---
title: "Soul"
type: docs
weight: 2
url: "/docs/player/soul/"
---

## Soul Abilities

## **Distraction**

> **Source image:** image242.gif *(media file pending upload: `image242.gif`)*

**Last Updated:** (10/6/2026)

### **Design**

**Design Statement:**

**Abstraction:** A tool used to lure enemies to a specific location.

The distraction is designed to lure enemies away from the player using a projectile that emits a ping when it hits the floor. As the name suggests, it functions as a distraction that enemies can follow instead of the player when the player is not sufficiently visible to them i.e outside the kill sequence.

Notes: Tie back into one of the pillars (Player-Soul-Teamwork, Helping hand abilities)

### **Interactions with Other Elements** 

- **Player:** The player can spawn distractions from the distraction holder if they have sufficient light levels and throw them toward a desired location. The player can use two distractions with a full light level.

- **Environment:** The distraction bounces off walls and falls to the ground, allowing the player to throw the distraction at a location roughly without having to be pixel perfect with their throwing arc

- **Ground:** When the distraction lands, it begins emitting its ping and becomes an active distraction.

- **Guards:** The ping alerts nearby guards within its detection range, causing them to investigate the distraction's location instead of continuing to focus on the player.

- **Stealth System:** The distraction gives the player an opportunity to redirect enemy attention when the player is hidden or has broken the enemy's direct visibility.

### **Code Overview**

**<u>Player Side</u>**

**BP_Player_Controller (Enhanced Input Action: IA_ThrowLight):**

> **Source image:** image327.png *(media file pending upload: `image327.png`)*

While the player holds down the input, the distraction enters its aiming state, if the player can use the Distraction (Checked with the Can Use Distraction Bool) then BP_Player_Controller calls Aim Distraction. When the player releases the input, the distraction is thrown, and the Player Controller calls Throw Distraction in BP_Player

<span class="mark">If the player cancels aiming using a separate input, they can still use the distraction again upon releasing the hold</span>, provided the Light Percent is above 0. This prevents players from needing pixel-perfect timing when canceling the distraction. Instead, they can hold the aiming input, press the cancel input, and then release the hold when ready. This makes canceling the distraction more forgiving and intuitive.

**BP_Player_Controller (Aim Distraction):**

> **Source image:** image154.png *(media file pending upload: `image154.png`)*

When Aim Distraction is called, as long as the player is not in a crack (checked by In Crack) if BP_Light_Projectile (the Distraction Actor) is null, the player spawns a new BP_Light_Projectile using Spawn Light in Hand in BP_Player. A new distraction will also spawn if the previous one has already been thrown and Ping Activated has been activated ie. the distraction has landed.

**<u>NOTE FOR CHANGE:</u>** The player can spawn as many distractions sequentially as they want, we probably don’t care if the ping has been activated on the current one and instead should just de register the BP_Light_Projectile once it’s been thrown, which I think we already do. TLDR: Delete the Ping Activated check

If the distraction already exists and has not been thrown, the event will call the Update Light Projectile Path in BP_Player allowing the player to preview where the distraction will travel when thrown.

**BP_Player (Spawn Light In Hand):**

> **Source image:** image316.png *(media file pending upload: `image316.png`)*

When Spawn Light in Hand is called it calls Spawn Light From BP_Player and sets Distraction in Hand to be true meaning it's ready to be used.

**BP_Player (Spawn Light):**

> **Source image:** image151.png *(media file pending upload: `image151.png`)*

When Spawn Light is called, if there is enough Light Percent for the ability it will Spawn the BP_Light_Projectile and set it as the BP_Light_Projectile variable in the player it then also populates the BP_Player variable in the BP_Light_Projectile.

**BP_Player (Update Light Projectile Path):**

> **Source image:** image75.png *(media file pending upload: `image75.png`)*

Update Light Projectile Path is called while the player is holding down the aim distraction button. Due to a race condition it makes sure the BP_Light_Projectile has been populated then clears the projection spline using Clear Projection Spline, calculates where the player is pointing using Calculate Projectile Launch Vector then creates a new projection spline based on that using Create Projection Spline

**BP_Player (Clear Projection Spline):**

> **Source image:** image34.png *(media file pending upload: `image34.png`)*

When Clear Projection Spline is called it clears everything including clearing the Spline Mesh and clearing all the spline points from the Light Projectile Projection Spline

Note: Why do we have to destroy the component and clear it? That seems needless.

**BP_Player (Calculate Projectile Launch Vector):**

> **Source image:** image214.png *(media file pending upload: `image214.png`)*

When Calculate Projectile Launch Vector is called it grabs the Player Controller casts to BP_PlayerController and then takes the Player Camera Manager variable from there, gets its forward vector add an upward tilt for the launch vector “0.3” and then multiplies the vector by the launch vector range which is “1200” then sets it as BP_Player’s Light Projectile Launch Vector variable

**<u>Note:</u>** casting to the player controller and then the camera manager seems like we are just putting more classes in memory than necessary. We should only cast to the player camera manager and if there is a way to avoid casting even to the player camera manager we should avoid it. Also these magic numbers need to have variable names especially because this is a function so there can be local variables .3 should be called “Launch Vector Upward Tilt” and 1200 should be called “Launch Vector Range”

**BP_Player (Create Projection Spline):**

> **Source image:** image168.png *(media file pending upload: `image168.png`)*

When Create Projection Spline is called it first makes sure BP_Light_Projectile is valid due to a race condition. It then grabs the Light Projectile Holder which is a point in space relative to the player, it then takes that world position and puts the BP_Light_Projectile there. After which the game predicts the Projectile Path using Light Projectile Holder as the start point and Light Projectile Launch Vector as the launch velocity. It then grabs the path that has been calculated and for each of the path points it adds the location of that point to the Light Projectile Projection Spline. After all the spline points are added on it takes all of them (except for the first point because that’s where the BP_Light_Projectile is) and adds them to Spline Mesh lerping to each one so that each spline mesh component points to the next.

**BP_Player (Throw Distraction):**

> **Source image:** image358.png *(media file pending upload: `image358.png`)*

When the player releases the aim distraction button, clear the projection spline using Clear Projection Spline. And if there is a distraction in the player's hand, indicated by Distraction In Hand then the function calls Throw Light Projectile and sets Distraction In Hand to false. After which it casts to GI_Lantern and calls the Distraction Set function to reduce the Light Percent from the UI and affects the actual Light Percent from the player. Then checks if there is enough light percent for the next throw. If there is not you can no longer use the distraction.

**<u>NOTE:</u>** There should be less magic numbers, the light cost should be a variable (I think there is a cost for the distraction cost) also it shouldn't be if light percent is more than 0.0 it should be if the light cost is higher than the light percent or it shouldn't exist at all.

**BP_Player_Controller (Throw Light Projectile):**

> **Source image:** image47.png *(media file pending upload: `image47.png`)*

When Throw Light Projectile is called it checks if Current Light Amount is greater than Light Projectile Cost. If it is then we take BP Light Projectile’s Projectile Movement Component and set Simulation Enabled to true and use the Set Velocity in Local Space function to set the velocity of the Projectile Movement Component to Light Projectile Launch Vector multiplied by 2 we then clear BP Light Projectile

**<u>NOTE:</u>** There shouldn’t be so many checks for if there is enough light that should be a one and done at the beginning of the chain. Also that 2 times should be a variable called “Local Space Velocity Multiplier” which it should be looked into why that needs to be multiplied in the first place

**Game Instance (Distraction Set):**

> **Source image:** image267.png *(media file pending upload: `image267.png`)*

When Distraction Set is called, it takes the percent of the light meter and calls the Hud to set the state of the icon using Set Distraction Action and set the light amount in the hud using Set Light Amount

Note: We no longer need Set Distraction Action

**HUD_Main (Event SetLightAmount):**

> **Source image:** image60.png *(media file pending upload: `image60.png`)*

Set Distraction Action is received by the HUD_Main, which first checks if Distraction Ammo Widget is valid, if it’s not then it pairs it to the Player Controller and sets the Distraction Ammo Widget variable to the created Widget Blueprint. If Distraction Ammo Widget is valid or is not valid it will call Set Light Amount on the Distraction Ammo Widget

**For Information on the Set Light Amount Widget please look at the <u>Widget Blueprints</u> Section of the Documentation**

**<u>Distraction Side</u>**

**BP_Light_Projectile (Event Begin Play):**

> **Source image:** image229.png *(media file pending upload: `image229.png`)*

When Begin Play is initialized it grabs the BP_Waypoint_Manager (God AI) and adds it to it’s God AIRef variable for alerting the guards later

**<u>NOTE</u>** I think the distraction now calls guards directly, which means that this is deprecated

**BP_Light_Projectile (Event Hit):**

> **Source image:** image227.png *(media file pending upload: `image227.png`)*

As the distraction is thrown as soon as it hits a point that is pointing upwards by “.85” then it stops simulating physics on the sphere and deploys a ping and calls guards over by calling Deploy Super Ping.

**<u>NOTE</u>** I'm pretty sure we don't need to set the simulated physics to false. now that we are using the projectile movement component. We should also make sure that .85 is called something like “floor slope threshold”

**BP_Light_Projectile (Deploy Super Ping):**

> **Source image:** image20.png *(media file pending upload: `image20.png`)*

When Deploy Super Ping is called it makes sure to set Ping Activated to true, then it grabs the Child actor which is a Light Ping and calls the Spawn Ping function, after which it sets the visible sphere of the projectile to false and gets all the actors of Guard Base

> **Source image:** image258.png *(media file pending upload: `image258.png`)*

After it gets all the actors of Guard Base it runs a for each loop. For each guard it finds a path with the distraction being the start point. It then checks the path length of that path between the guard and the distraction, checking if the Path Length is less than the range variable. If it is, it gets BP_GuardController01_AIC and calls the Go To New Stimulus Function passing in the distractions world location. After it does that with all the Guards waits 1 second using a delay and then destroys itself.

## **Invisibility:**

> **Source image:** image93.gif *(media file pending upload: `image93.gif`)*

### **Design**

**Design Statement:**

**Abstraction:** A tool used as a panic button when the player is caught and there is nothing else they can do to escape. It gives the player immunity for enough time to get away, at the cost of using up all of your light.

**Players Agency:** Because this ability is high cost, it is meant as a last resort for escaping the guard. But if you want to waste all of your light when you are totally safe, be my guest I guess.

### **Interactions with Other Elements** 

- **Player:** The player becomes invisible for a few seconds, visually becomes transparent.

- **Environment:** You still interact with the environment like normal.

- **Guards:** Guards are unable to see you. If you get spotted by the watcher and then become invisible, the guard will go to the last place that you were spotted.

- **Stealth System:** Invisibility gives the player an opportunity at the very last moment. It should be used as a last resort. These few seconds should be used to hide behind something or go into a crack, or else the guard will see you again and you will die.

### **Code Overview**

Starting inside of the Bp Player Controller, when you press the space bar, it activates the logic for invisibility. In GI_Lantern it gets the variable “Infinite Light Mode” which is a dev tool that can be activated by the 9 key. If infinite light is on, it will simply get the player and toggle invisibility. 

> **Source image:** image330.png *(media file pending upload: `image330.png`)*

However if not, it will activate Turn invisible timed

> **Source image:** image304.png *(media file pending upload: `image304.png`)*

Which will then activate Start Invisibility

> **Source image:** image162.png *(media file pending upload: `image162.png`)*

> **Source image:** image96.png *(media file pending upload: `image96.png`)*

As of now, it starts invisibility. If the light level is greater than 0 it will make the player invisible by setting the texture. If infinite light mode is on it will just go ahead and set the invisibility.

> **Source image:** image291.png *(media file pending upload: `image291.png`)*

After the delay in TurnInvisibleTimed, it will activate <u>end invisibility</u>, which will turn the texture back to the original texture. <span class="mark">(want to go back and revise, inefficient)</span>




## **Sprinting:**

### **Design**

**Design Statement:**

**Abstraction:** A tool used to quickly move around the map when there is less of a perceived threat. Used to help frustration associated with gameplay feeling too slow, or having to sneak everywhere when not necessary.

**Players Agency:** Players will be able to exercise agency by deciding how fast they want to move through the level. It also allows the player to exercise more risk if they would like to (even though we learned in general conference that we’re not supposed to gamble)

### **Interactions with Other Elements** 

- **Player:** The player walks at a higher speed. It will also change the visual light radius the surrounds the player. Light strength (how detectable you are to the guards) is higher.

- **Environment:** Causes an echo, as your foot steps are louder

- **Guards:** Guards may not see you if they are far away, but if you are closer and sprint, they will detect you.

- **Stealth System:** Will make you more detectable, use wisely

### **Code Overview**

> **Source image:** image233.png *(media file pending upload: `image233.png`)*

Sprint is activated by the Shift key, and logic is held inside of BP Player.

<u>On Sprint Triggered</u>

> **Source image:** image251.png *(media file pending upload: `image251.png`)*

What on Sprint triggered does, is it first makes sure you're not crouching, or else it will not activate.

If you are moving, it will then set the movement state to sprinting. In the apply movement settings, it will set the speed of the player depending on the movement state. It will also change how strong the light is for the enemy.

The set attention radius changes the appearance of the light. This is kept separate from strength as we want the strength and appearance to not be dependent on each other.

> **Source image:** image187.png *(media file pending upload: `image187.png`)*

This starts the noise loop. It’s on Started so that it only activates once. For the other things <span class="mark">(go back to revise, might be redundant)</span>

> **Source image:** image359.png *(media file pending upload: `image359.png`)*

OnSprintStop stops the sprint sound, it also sets the movement state to walking and sets the light strength and visual light radius back to normal.
