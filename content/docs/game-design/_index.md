---
title: "Game Design Document"
type: docs
weight: 2
bookToC: true
---

> **Media note:** This page was migrated from the Google Docs source. Its 373 embedded images and GIFs are identified below, but the binary files still need to be added under `static/game-design-media/` before those visuals can be restored.

## The Purpose of This Game Design Doc

The purpose of this Game Design Document is to provide the team with a clear understanding of how the game is intended to feel and play. It explains how different game elements function from a design perspective, how they interact with one another, and how each element is implemented programmatically. This ensures that every team member can understand the purpose, behavior, and operation of each part of the game. This design doc is meant to be updated every week as people finish features

## How to Write Each Game Design Document Entry

<u>Example: Distraction</u>

Each entry in the Game Design Document should follow the structure below. The goal is to clearly explain what the element is, how it is intended to work, how it interacts with other game elements, and how it is implemented.

## Title of Element (Heading 2)

The name of the game element being documented.

**Last Updated:** Date of the most recent update to this entry. (Normal Text)

###  (Heading 3) Design

**Design Statement:** Write approximately one paragraph explaining the purpose of the element, how it is intended to feel and play, and what experience it is meant to provide to the player. (Normal Text)

### (Heading 3) Interactions with Other Elements 

(Normal Text) Describe which other game elements this element interacts with from a design perspective. Explain how these interactions affect gameplay and how the elements work together to create the intended experience.

### Code Overview (Heading 3)

(Normal Text) Document the technical implementation of the element. Include:

- Functions

- Variables

- Events

- Interfaces

- A step-by-step explanation of how the element works and how its different parts interact.

The purpose of this section is to ensure that any team member can understand how the element operates and how its implementation supports the design.

Please be sure to add lots of pictures/gifs of things working as intended. The expected work time on each element should be sub 20 minutes, use AI and then review it.

## Game-Wide Design Statement

The game is designed to evoke fear and dread through its enemies and environment. Despite this, players should have the tools, encouragement and environmental readability to rely on stealth, particularly positional stealth, to navigate levels and avoid enemies. The game should be difficult and scary, but players should come away thinking, “I wish I had done X,” rather than, “The game should have given me X.” Players should feel intrigued and motivated to keep trying, not discouraged by an unnecessarily steep initial difficulty curve.

## Fantasy Statement

You play as a Soul Master navigating a dark underworld to guide a soul to ascension. Your power comes from your experience in this world. Using your environment and the soul's light you will outwit massive, terrifying lost souls.

## Core Emotions

High-stakes fear, a strong protective drive toward the soul, the player should feel aware of their environment and abilities and be able to use them to overcome enemies, and intense relief when you reach safety.

## Core Pillars

- Horror: *“Light in the dark” player should be cautious while they play*

- Stealth: *special emphasis on player agency, Interconnected level design, we want the player to feel scared, but capable as they outsmart the enemies and navigate the level.*

- Single Player Companion Game: *story is focused on the relationship with the two characters, side character is helpful, the player should feel attached and protective of the side character.  
  > *

## Player Design Statement

The player and the soul exist in a symbiotic relationship. The player cannot beat the game without relying on the soul, at least to some degree. The player should feel attached to and protective of the soul, as the soul provides the player with the power and guidance needed to survive through its abilities. The player and the soul are a team, and their success depends on working together. Players should have a clear understanding of the abilities the soul provides, including their intended uses and limitations. When used correctly, these abilities should feel reliable and effective, encouraging players to learn how best to work with the soul.

Player immersion should also feel seamless through responsive movement and an unobtrusive camera. The player's sound and light radius should feel meaningful, encouraging caution and deliberate movement when navigating around enemies. Players should understand how their actions and visibility affect their risk of detection. The camera should consistently provide the information players need to navigate the environment, assess threats, and make informed decisions without compromising the intended atmosphere of fear and uncertainty.

## Player Design Pillars

1.  Immersion: Players should feel like they are seamlessly connected to the avatar. Movement should feel responsive, camera should be unobtrusive. If the player wants to act in a certain way using the tools that are given to them, it should be as seamless and as realistic as possible. On the flip side if the player fricks up, they should be punished.

2.  Positional Stealth: The player should rely heavily on positional stealth as their stealth bread and butter, being mindful of their light radius and sound to stay out of the perception of the enemies.

3.  Player-Soul Teamwork: The player and the soul should be a team, they should have a symbiotic relationship. The soul should feel like a companion and a helpmate, using its abilities to help the player accomplish their goals. The player should feel protective and attached to the soul.

**Player**

## Design Statement

The player and the soul exist in a symbiotic relationship. The player cannot beat the game without relying on the soul, at least to some degree. The player should feel attached to and protective of the soul, as the soul provides the player with the power and guidance needed to survive through its abilities. The player and the soul are a team, and their success depends on working together. Players should have a clear understanding of the abilities the soul provides, including their intended uses and limitations. When used correctly, these abilities should feel reliable and effective, encouraging players to learn how best to work with the soul.

Player immersion should also feel seamless through responsive movement and an unobtrusive camera. The player's sound and light radius should feel meaningful, encouraging caution and deliberate movement when navigating around enemies. Players should understand how their actions and visibility affect their risk of detection. The camera should consistently provide the information players need to navigate the environment, assess threats, and make informed decisions without compromising the intended atmosphere of fear and uncertainty.

## Design Pillars 

1.  **Immersion:** Players should feel like they are seamlessly connected to the avatar. Movement should feel responsive, camera should be unobtrusive. If the player wants to act in a certain way using the tools that are given to them, it should be as seamless and as realistic as possible. On the flip side if the player fricks up, they should be punished.

2.  **Positional Stealth:** The player should rely heavily on positional stealth as their stealth bread and butter, being mindful of their light radius and sound to stay out of the perception of the enemies.

3.  **Player-Soul Teamwork:** The player and the soul should be a team, they should have a symbiotic relationship. The soul should feel like a companion and a helpmate, using its abilities to help the player accomplish their goals. The player should feel protective and attached to the soul.

## **Player Verbs**

The core of the game is stealth, all other abilities serve the stealth.

**The Foundation (Pure Positional Stealth):** The core mechanic for stealth is how the player positions themselves to both initially stay out of line of sight of the enemy and to break line of sight when seen. A player can beat the game using pure intelligent positioning

- Moving around obstacles

- Crouching

- Crevices

**The Helping Hand (The Soul’s Power):***"You don't want to use the soul's power, but sometimes there is no other choice."* - Mailen. These abilities aren’t designed to replace stealth, bypass level design, or instantly undo a loss condition. Instead, they act as high-friction assists—temporary nudges that ease overwhelming pressure, redirect enemy attention, or bridge dangerous spatial gaps just long enough to let the player set up their next positional move.

- Distraction

- Invisibility

- Sprinting

What the ability is, what player want is it answering, how does it answer that want, what ways does it not answer that want, how we are communicating it to the player

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Ability Name</th>
<th>Player Want</th>
<th>Answer to Want</th>
<th>Downsides</th>
</tr>
<tr class="odd">
<th colspan="4">Positional Stealth (Foundational)</th>
</tr>
<tr class="header">
<th>Using obstacles</th>
<th>Wants to be out of sight of the enemy</th>
<th>The player can stay out of sight of an enemy with an obstacle as long as they are on the other side of the obstacle. Can see around obstacles</th>
<th>The player is stuck behind one obstacle while an enemy is looking at them, they can be seen from the side they're hiding on.</th>
</tr>
<tr class="odd">
<th>Crouching</th>
<th>To be less visible</th>
<th>Decreases discoverability from the enemy, so players can have closer encounters with enemies without being spotted. Player can look around</th>
<th>Slower, does not work if you have been seen.</th>
</tr>
<tr class="header">
<th>Crevices</th>
<th>Players want to feel extra safe</th>
<th>The crack protects players on all sides besides the front, and the front is safe as long as you hit the QTE, and the player can see in front of them.</th>
<th>Enemies can peak in forcing a player skill check that they can fail. They are stuck in that location until they decide to move out.</th>
</tr>
<tr class="odd">
<th colspan="4">Helping Hand Mechanics</th>
</tr>
<tr class="header">
<th>Sprinting</th>
<th><p>Players want to be able to get to their objectives quickly,</p>
<p>People like moving quickly,</p>
<p>Players want to escape an enemy if they see them</p>
<p>Long Range</p></th>
<th>Moves you quicker, ideally not detectable at long ranges</th>
<th>Not viable in close and mid range as it makes the player more detectable.</th>
</tr>
<tr class="odd">
<th>Distraction</th>
<th><p>Players want to take the enemy off of them when they have been seen, or create an opening to move</p>
<p>Mid Range</p></th>
<th>The distraction calls enemies within its call range to them. You have two uses.</th>
<th><p>The player has to escape line of sight first to use it and has to stay out of line of sight.</p>
<p>Not available if enemy is red states</p></th>
</tr>
<tr class="header">
<th>Invisibility</th>
<th><p>Players want a panic button when they have been found, or something allows them to make a quick movement decision.</p>
<p>Close Range</p></th>
<th>Gives them 2.4 seconds of invisibility allowing them to find a location to hide behind or for them to escape the room</th>
<th>Is short and is very costly draining all of your light meter</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## **Abilities**

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

> **Source image:** image358.png *(media file pending upload: `image358.png`)*When the player releases the aim distraction button, clear the projection spline using Clear Projection Spline. And if there is a distraction in the player's hand, indicated by Distraction In Hand then the function calls Throw Light Projectile and sets Distraction In Hand to false. After which it casts to GI_Lantern and calls the Distraction Set function to reduce the Light Percent from the UI and affects the actual Light Percent from the player. Then checks if there is enough light percent for the next throw. If there is not you can no longer use the distraction.

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

Starting inside of the Bp Player Controller, when you press the space bar, it activates the logic for invisibility. In GI_Lantern it gets the variable “Infinite Light Mode” which is a dev tool that can be activated by the 9 key. If infinite light is on, it will simply get the player and toggle invisibility. > **Source image:** image330.png *(media file pending upload: `image330.png`)*

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

<u>On Sprint Triggered</u>> **Source image:** image251.png *(media file pending upload: `image251.png`)*

What on Sprint triggered does, is it first makes sure you're not crouching, or else it will not activate.

If you are moving, it will then set the movement state to sprinting. In the apply movement settings, it will set the speed of the player depending on the movement state. It will also change how strong the light is for the enemy.

The set attention radius changes the appearance of the light. This is kept separate from strength as we want the strength and appearance to not be dependent on each other.

> **Source image:** image187.png *(media file pending upload: `image187.png`)*

This starts the noise loop. It’s on Started so that it only activates once. For the other things <span class="mark">(go back to revise, might be redundant)</span>

> **Source image:** image359.png *(media file pending upload: `image359.png`)*

OnSprintStop stops the sprint sound, it also sets the movement state to walking and sets the light strength and visual light radius back to normal.

## **Movement** 

Design Statement: Movement is on the simpler side. The player is able to walk around and go upstairs. Jumping is not included as it doesn’t affect the exploration of the map.

> **Source image:** image141.png *(media file pending upload: `image141.png`)*

> **Source image:** image113.png *(media file pending upload: `image113.png`)*

Move keyboard…I’m sure it works. It gets the action input, casts to GI lantern, and checks whether there’s a quick time event active. If there is a QTE active and the input is A, S, or D (the possible QTE inputs), the input is passed to the game instance to determine the result of the event.

When there's not an active QTE it gets the BP player, it sets the BP Player Moving, and then if the player is not sprinting or crouching, it sets it to walking, then starts the walk sound.

When you’re done it sets it bp player to not moving, and stops the walk sound.

**Look Keyboard**

Times that looking around would be disabled would be anytime there is a fixed camera, and looking around is limited within the crack. Player has a 360 view around itself and follows the rotation of the mouse.

> **Source image:** image56.png *(media file pending upload: `image56.png`)*

If rotation is not frozen, it will get the BP player and it <span class="mark">calls a variable that we don’t even use anymore (drawing).</span> It then tracks to see if the player is in the crack, it casts to GI lantern to see if there is a quicktime event. If there is, the mouse switches to be one that is visible on the screen instead of controlling where the camera is looking. (think click and point game.) (See [<u>QTE Widget</u>](#qte-widget-wbp_qte) for more info.)

If the player is in the crack, the sensitivity is set to .3, but if the player is not in the crack the sensitivity is a 1 which is the baseline. The Look function is then called which is handled in the c++.

**Soul**

## Design Statement

The soul is the companion to the player. Along with giving the players light to do abilities, he also gives the player information that helps the player move through the map and be aware of the enemies.

BP Soul Rotate Soul

Abstract:

Rotates the soul to face the guard, but also changes color to indicate the danger level of the player. Acts as a radar to let the player know if they should proceed or hide.

Big picture of code

> **Source image:** image158.png *(media file pending upload: `image158.png`)*

> **Source image:** image15.png *(media file pending upload: `image15.png`)*

At the start of the function, we set the closest distance to 10,000, which is a base distance that we can compare distances for the guard. For each guard in the array, we find a path to the guard.It finds the path to the guard,

and if the player is not in the crack…

> **Source image:** image53.png *(media file pending upload: `image53.png`)*

It gets the distance of the path and sees it is smaller than the current closest distance of 100,000, it will reset the closest distance and set the closest guard.

> **Source image:** image314.png *(media file pending upload: `image314.png`)*

If you are in the crack, the logic isn’t too different, but what it does is gets the location of the player and the guard. It takes the x y of the locations and checks if that’s less than the closest distance.

It then takes the difference of the z values and makes sure that’s less than 200 (this checks if the guard is on the same floor)

If the guard is on the same floor and the x,y 2D vector is smaller than the closest distance, it will reset the closest distance and closest guard.

<u>Logic for when for each loop is completed</u>

> **Source image:** image129.png *(media file pending upload: `image129.png`)*

> **Source image:** image374.png *(media file pending upload: `image374.png`)*

We get the closest distance, and detect range. If the closest Distance is not within the Detect Range (if this statement is false)

> **Source image:** image9.png *(media file pending upload: `image9.png`)*

Then it will set the rotation to the default, set the material to green, and turn the invisibility off on the arrow.

> **Source image:** image246.png *(media file pending upload: `image246.png`)*However if the Closest distance IS within the detect range,

The set visibility is put on the arrow, which points towards the closest guard. The Set Actor Rotation rotates the soul depending on the look at rotation from the soul to the closest guard.

The soul is then lit to yellow to indicate that the guard is nearby.

> **Source image:** image337.png *(media file pending upload: `image337.png`)*

However, if the Closest Distance is shorter than the Panic Range, it will set the soul’s color to red, indicating imminent danger.

This statment loops back to the first GET dead in the blueprint, creating a while loop that keeps activating the function until the Soul is dead.

> **Source image:** image199.png *(media file pending upload: `image199.png`)*

When death is called, it sets the dead boolean, which breaks the large while loop above. It also turns off the invisibility for the arrow.

**Camager**

**Core of Camager: Camera Orient**

**Camera Orient is a crucial component of the camera, and the first thing I coded to make the camager work. It constantly gets the camera location and rotation. You won’t interact with this function, but this function will show up continually in the code.**> **Source image:** image132.png *(media file pending upload: `image132.png`)*

Basic flow of camera orient is getting the camera location, doing a raytrace to check for collisions, and setting the offset depending on if there’s a collision or not.

<span class="mark">Get world camera location</span>

> **Source image:** image51.png *(media file pending upload: `image51.png`)*

First function within the camera orient <span class="mark">(Get world camera location)</span> will get the camera location according to the offset that is put in. It rotates the offset by the control rotation, and then subtracts that from the location of the camera target. The QTE active branchoff is for when there is a quick time event

<span class="mark">Raytrace collision</span>

> **Source image:** image161.png *(media file pending upload: `image161.png`)*

> **Source image:** image90.png *(media file pending upload: `image90.png`)*

The raytrace collision for the springarm is divided into 2 halves.

The first raytrace is to see the location of the wall hit. The trace starts above the players head. this is done by getting the actor location and adding (15, 0, 150) to move it above the players head

The trace ends 300 centimeters behind the player by subtracting (300, -90, -35) to the actor location and plugging that into the end.

The outhit location is then used to make a new camera offset. I get the actor location, subtracted that by the outhit location to get the length, I then subtract it by 12,12,12 to make the location land before the wall. (if you get the exact location the camera clips through). I unrotate the vector and that is our new desired camera offset.

The second line trace shoots down from where the camera normally would be without collision, and that sees if there is a floor. If there isn’t a floor, it spring arms. This method is planned to change in the future when we implement tags.

**Camera States**

## **Looking** 

> **Source image:** image351.gif *(media file pending upload: `image351.gif`)*

###  **Design**

**Design Statement:** A default camera that follows the player as it is walking around. It faces where the mouse points, and it will spring to collisions on walls. Freedom of movement allows the player control of where they’re looking to make stealth easier.

### **Interactions with Other Elements** 

**Walls**: Currently, it sends a line trace behind itself, if it hits a wall that does not have ground under it, it will springarm to that wall, but we do want to do a tag system in the future.

**Boxes and Columns:** It will not springarm to smaller items, this messes up the flow

**Floor:** technically spring arms to floor when looking directly up, but it’s not obvious.

**Code**

> **Source image:** image210.png *(media file pending upload: `image210.png`)*

**Normal Walking** is how the walking camera typically works. The desired camera offset changes continuously depending on collisions with walls. If the desired camera offset is different from the actual camera offset, the actual offset will lerp to the desired camera offset.This accounts for changes with wall collisions

**Lerp into normal walking** is how the walking camera works if we need to interpolate into the walking camera. This happens if we need to transition from another camera mode like Fixed Camera.

## **Fixed Camera**

> **Source image:** image190.gif *(media file pending upload: `image190.gif`)*

###  **Design**

**Design Statement:** A camera that stays in a set position. You can choose to lerp to it or not. Typically used for interactables or cutscenes.

### **Interactions with Other Elements** 

**Interactables:** Takes in an arrow within interactables and sets that to the desired camera location and rotation.

> **Source image:** image237.png *(media file pending upload: `image237.png`)*> **Source image:** image255.png *(media file pending upload: `image255.png`)*> **Source image:** image211.png *(media file pending upload: `image211.png`)*

Within an intractable, the programmer can place the arrow where the camera would be, and you can plug that into the Enter Fixed Camera function. Lerp can be turned on and off depending if you want to interpolate to the arrow location.

**Code**

> **Source image:** image145.png *(media file pending upload: `image145.png`)*

The enter fixed camera function simply sets the desired camera location and rotation.

> **Source image:** image260.png *(media file pending upload: `image260.png`)*

Within the update blueprint camera itself, it will lerp the camera if that is on, or it will set the actual camera location and rotation if lerp is off.

## **Peek Left/ Peek Right**

> **Source image:** image42.gif *(media file pending upload: `image42.gif`)*

###  **Design**

**Design Statement:** Peek left and peek right shift the camera to either side and allows the player to look around corners. This adds to the stealth a player can utilize. Q allows the player to peek to the left, and E allows the player to peek to the right. Those inputs are handled in the game controller.

### **Interactions with Other Elements** 

Similar interactions to the looking camera, as it still has a springarm that collides with walls. It

### **Code**

> **Source image:** image179.png *(media file pending upload: `image179.png`)*

Peek left and peek right simply lerp the actual camera offset to a position that is off to the side. In peek left it is (140, 30, -60). If there is a wall collision that is detected in the Camera orient however, it will interpolate off to the side of the collision location.

## **Death Cutscene**

> **Source image:** image112.gif *(media file pending upload: `image112.gif`)*

###  **Design**

**Design Statement:** Death cut scene is similar logic to the fixed camera, but instead of an arrow it grabs the location of a socket inside of the guard state machine

### **Code**

> **Source image:** image220.png *(media file pending upload: `image220.png`)*

## **Crack Look**

###  **Design**

> **Source image:** image355.gif *(media file pending upload: `image355.gif`)*> **Source image:** image308.gif *(media file pending upload: `image308.gif`)*

**Design Statement:** Where do I even begin? Crack look started off as a fixed camera that would just switch to peek left and right, which were more fixed cameras. However we wanted the experience in the crack to be more interactive. This is first done by letting the player look around the crack with their mouse. Then with the quick time event, we did something super dynamic, which the camera movements had to match.

### **Interactions with Other Elements** 

**Interactables:** The player is able to look around the corners with the mouse, when the enemy is around the area, and decides to look inside the crack, a quick time event starts.

**Code**

This is the flow of logic within blueprint update camera. The structure here is similar to the other walking cameras, however instead of camera orient, we have <span class="mark">Enter Crack Look</span>, which handles the core logic way differently. > **Source image:** image319.png *(media file pending upload: `image319.png`)*

> **Source image:** image22.png *(media file pending upload: `image22.png`)*

> **Source image:** image206.png *(media file pending upload: `image206.png`)*

Enter Crack look can actually be called within the crack logic. The original rotation is the base rotation for the rest of the logic, and the crack forward vector is plugged into it. We set it to the crack Rotation so that this separate rotation can be plugged into the function in Blueprint update camera.

**Normal Crack Look Around**

> **Source image:** image331.png *(media file pending upload: `image331.png`)*

When the QTE is not active, we have the view where you can look around with your mouse. I grab the crack rotation and use delta rotator to get the difference between the original crack rotation and the control rotation. If the distance is greater than 10, it sets the desired camera offset to face the left, and if its less than -10 it goes to the right. If it’s between those values, it pulls back in the center.

The input mouse is there, because if the mouse is fast enough, it won’t pull back to the center.

> **Source image:** image198.png *(media file pending upload: `image198.png`)*

Afterwards, I set the view max and mins for the pitch and yaw. This locks how far left/right, and up/down you can go with your mouse.

**When QTE active**

When there's a QTE, there’s one more boolean for QTE dodging, which happens when the player dodges after successfully doing the QT task. > **Source image:** image44.png *(media file pending upload: `image44.png`)*

When QTE dodging is active, the QTE direction is chosen by random in the GI_latern, which determines what side of the crack the camera will shift to.

**Easy to use functions**

**Enter fixed camera**

> **Source image:** image228.png *(media file pending upload: `image228.png`)*

If there is a fixed camera needed, such as for interactables:

-Make a camera arrow in the intractable viewport, and then plug this arrow into the function.

-Lerp can be turned on to lerp into the camera.

**Exit fixed camera**

> **Source image:** image120.png *(media file pending upload: `image120.png`)*

To Exit, the exit fixed camera function can be used, again with the lerp on and off.

**Set QTE and QTE dodge**

> **Source image:** image185.png *(media file pending upload: `image185.png`)*> **Source image:** image135.png *(media file pending upload: `image135.png`)*

Starts the quick time event within the crack, used in GI_lantern.

**Enter Crack Look**

> **Source image:** image72.png *(media file pending upload: `image72.png`)*

Used in Blueprint Update camera, but also used to initialize the crack look. What gets plugged into Original Rotation is the World Rotation of the Arrow Front Camera. Only used within BP_crack

**More functions under the hood**

> **Source image:** image159.png *(media file pending upload: `image159.png`)*

Function used to lerp the camera location and Rotation. This logic showed up enough that it was easier to turn it into a function.

**Testing Debug Tool**

Design Statement: This tool allows us to record and display locations for when different types of events occur, such as death, hide, etc., that helps testing to have more useful information on player behavior. It also has functionality to filter displayed locations using a min/max time.

> **Source image:** image173.png *(media file pending upload: `image173.png`)*

\*Tool usage guide

[<u>https://docs.google.com/document/d/1eW5Eo0d_uDM_zu-P4qN2CZz1nc8aLJPDMJJnw1CZtp4/edit?usp=sharing</u>](https://docs.google.com/document/d/1eW5Eo0d_uDM_zu-P4qN2CZz1nc8aLJPDMJJnw1CZtp4/edit?usp=sharing)

Test Events (location + type of test event) are triggered to be recorded in various places using the function below. This tool uses GI because it is easily accessed everywhere, and is currently called in:

- STT_KillPlayer (Death)

- BP_Player (ThrowDistraction → Distraction)

- BP_Crack_I (EventOnInteract → Hid)

- Escaped is WIP

> **Source image:** image286.png *(media file pending upload: `image286.png`)*

Inside of the GI, IsRecordDebug tells you whether or not the game can record (that being said, the proper file in TestLogs must also be checked out)

> **Source image:** image4.png *(media file pending upload: `image4.png`)*

This function in GI is wired to a function inside of BP_MapDebug. The map being tested on MUST have an instance of MapDebug to work.

BP_MapDebug holds 3 functions.

- AddEvent that is always triggered by GI_Lantern, which records to a file based on the name that is set by CurrentFile. > **Source image:** image125.png *(media file pending upload: `image125.png`)*

- DrawLocations and ClearDraws draws/clears debug boxes. See usage guide for how to use them in the level editor.

  - TestDrawStart/EndTime variables determine the window of tests we want to display. Disconnected by default.

  - Debug Size determines the size of the box displayed.

- \*Note that CurrentFile is used for *both* the file that is being read from when drawing and written to when recording.

ENEMIES

Guard Design Pillars and Design Statement:

The guard is the primary obstacle for the player and a source of fear and tension. It wanders the halls of the level, investigating the player’s location when it sees them and attacking once it gets close. The player must avoid and outsmart the guards as they progress through the level.

Pillars:

- hunter, intelligent enemy

- methodical and intentional behavior

- facilitates buildup -\> release of tension

- otherworldly, creepy, tormented, lost, predatory

Watcher Design Pillars and Design Statement:

The watcher is an additional obstacle that complicates the player’s decision making process by giving them something else to think about and avoid. The watcher is a towering, stationary creature with a spotlight emitting from its eye, and as it searches the level, if the spotlight lands on the player it alerts the closest guard to the player location.

Pillars:

- unpredictable but slow/telegraphed movement that ties up the player’s attention

- Doesn’t harm the player directly but calls a guard over to them

- Creates immediate panic when the player is caught

THE GUARD

## GuardBase.h

The GuardBase’s purpose is to exist as a physical object in the world and hold variables. See the comments for more details.

Variables

*// unused, intended to be for a guard that holds still*

bool bStationary = false;

*// deprecated from when we had the guards following a spline. Still in use in BP_Guard, which is not being used anywhere. There is a Watcher variable with the same name.*

TArray\<FGuardWaypoint\> PatrolWaypoints;

*// deprecated, only in unused BP_Guard*

int NextPatrolWaypointIndex = 0;

*// deprecated, only in unused BP_Guard*

void OnOverlapWaypoint(const AWaypointBase\* Waypoint);

*// these are the colors the point lights are set to depending on the guard’s state. They are still used in BP_Guard_01, but their values are overridden.*

FLinearColor NeutralColor = FLinearColor(0.371f, 0.0f, 1.0f, 1.0f);

FLinearColor InvestigationColor = FLinearColor(1.0f, 1.0f, 0.0f, 1.0f);

FLinearColor AttackColor = FLinearColor(1.0f, 0.0f, 0.0f, 1.0f);

*// Movement speeds*

float PatrolSpeed = 150.0f;

float InvestigateSpeed = 250.0f;

float ChaseSpeed = 500.0f;

*// Getters, not used*

float GetPatrolSpeed() const;

float GetInvestigateSpeed() const;

float GetChaseSpeed() const;

*// Setters, not used*

void SetPatrolSpeed(float NewSpeed);

void SetInvestigateSpeed(float NewSpeed);

void SetChaseSpeed(float NewSpeed);

*// sets light colors*

void SetLightColors(FLinearColor LightColor);

## GuardBase.cpp

void AGuardBase::BeginPlay()

{

Super::BeginPlay();

if (PatrolWaypoints.Num() \> NextPatrolWaypointIndex)

{

this-\>SetActorLocation(PatrolWaypoints\[NextPatrolWaypointIndex\].Waypoint-\>GetActorLocation());

}

}

This set actor location call is a leftover from following splines and can be removed.

There are also the getters and setters for Speed variables from above, but they are basic setters and getters, so I won’t copy/paste them here. They aren’t used at all, and honestly programmers have probably just been setting the variable directly. Getters and setters are more flexible so I’d like to make them standard practice.

This concludes GuardBase.

## GuardControllerBase.h

Most of the code in this class deals with the perception component. This class’s job is to keep track of the current “most important” object it’s receiving from the perception component. I will explain how this works using a few diagrams rather than copy/paste all 291 lines of code; if you need more details, there are comments in the code to explain the small parts.

First, let’s go over the header file. There are a few delegates, properties, and methods to be aware of:

*// delegates declared before class declaration; these can be used to trigger in other classes when the GuardController calls them.*

DECLARE_DYNAMIC_MULTICAST_DELEGATE_OneParam(FOnGuardYellow, FGuardYellowInfo, GuardYellowInfo);

DECLARE_DYNAMIC_MULTICAST_DELEGATE_OneParam(FOnGuardRed, FGuardYellowInfo, GuardRedInfo);

DECLARE_DYNAMIC_MULTICAST_DELEGATE_OneParam(FOnGuardGreen, FGuardYellowInfo, GuardGreenInfo);

*// State Tree asset to run. This will be run on BeginPlay, overriding the existing StateTree.*

TObjectPtr\<UStateTree\> StateTree;

*// Deprecated. Only used in old BP_Guard*

FGameplayTag ArrivedAtWaypointTag;

*// Array of DetectableLights. Keeps track of all DetectableLight objects inside of the vision cone, even those in the green zone.*

TArray\<TScriptInterface\<IDetectableLight\>\> LightsInRange;

*// Deprecated. Not used anywhere.*

TEnumAsByte\<EDetectionState\> DeprecatedCurrentDetectionState;

*// Detection Strengths from the previous frame for each DetectableLight. FDetectionStrengthPair is a pair of floats: one for Yellow and one for Red, since Yellow and Red use different equations to determine strength. Both floats are normalized to values between 0 and 1.*

TMap\<UObject\*, FDetectionStrengthPair\> OldDetectionStrengths;

*// Detection States from the previous frame for each DetectableLight. Used to determine when the detection state changes; if this is different from the current frame’s Detection State, the object has just crossed into a new zone.*

TMap\<UObject\*, TEnumAsByte\<EDetectionState\>\> OldDetectionStates;

*// Sight Config used for AIPerceptionComponent. This makes it so the sight sense is enabled and configured by default in Blueprints. It’s assigned default values in the constructor.*

TObjectPtr\<UAISenseConfig_Sight\> SightConfig;

*// Same as Sight Config*

TObjectPtr\<UAISenseConfig_Hearing\> HearingConfig;

*// If enabled, displays debug information about the detection strengths and states.*

bool bDebugDetection = false;

*// Reference to the object the guard is prioritizing. Determined by detection strength.*

TScriptInterface\<IDetectableLight\> PriorityLight;

*//functions*

*// Deprecated. Only used in old BP_Guard_AIC and BP_Guard.*

void OnReachedWaypoint(FGuardWaypoint NextWaypoint);

*// Event bound to PerceptionComponent delegate. Called every time the PerceptionComponent sees or loses any stimulus.*

void OnTargetPerceptionUpdated(AActor\* Actor, FAIStimulus Stimulus);

*// Called when the Guard first sees a DetectableLight. Starts a timer that calls GetLightInfo() every 0.2 seconds, avoiding a Tick() call.*

void StartTrackingDetectionState(IDetectableLight\* Light);

*// This handles all of the state changes; for example, it sends a delegate that the player has crossed into the yellow zone.*

void HandleDetectionStateChanges(const TScriptInterface\<IDetectableLight\>& Light, EDetectionState NewState, EDetectionState OldState, FVector Location);

*// Prints a debug statement containing the strength and the detected object*

void DebugDetectionState(TScriptInterface\<IDetectableLight\> Light, float NewDetectionStrength, EDetectionState NewDetectionState);

*// Called on Yellow-\>Green. Blueprint Implementable.*

void OnPlayerLost(FVector StimulusLocation);

*// Called on Green-\>Yellow. Blueprint Implementable.*

void OnLightDetected(const TScriptInterface\<IDetectableLight\>& DetectedObject);

*// Called on Yellow-\>Red. Blueprint Implementable.*

void OnLightAggro(const TScriptInterface\<IDetectableLight\>& DetectedObject);

*// Not currently in use. Blueprint Implementable.*

void OnHeardStimulus(AActor\* Actor);

*// Given all DetectableLights, calculates the strengths and states of each, then determines which one to follow and calls HandleDetectionStateChanges to send events based on where the objects have moved. Called every 0.2 seconds.*

void GetLightInfo();

*// begin delegates. These are declarations of the delegates at the beginning.*

FOnGuardYellow OnGuardYellow;

FOnGuardYellow OnGuardRed;

FOnGuardYellow OnGuardGreen;

*// end delegates*

## GuardControllerBase.cpp

I’ve added comments in the code explaining the details. Here is a conceptual overview of the class, including the most important snippets of code:

### CONSTRUCTOR (AGuardControllerBase())

The constructor has a few things to set up.

1.  First, it creates the Perception component. This makes the component show up in the Blueprint class:

Perception = CreateDefaultSubobject\<UGuardPerceptionComponent\>(

TEXT("EnemyPerception")

);

> **Source image:** image35.png *(media file pending upload: `image35.png`)*

2.  Next, it configures the Sight and Hearing Senses, making them show up in the Blueprint class. Any class that derives from GuardControllerBase will have these defaults.

*// set up Sight sense*

Perception-\>SetSenseEnabled(UAISense_Sight::StaticClass(), true);

SightConfig = CreateDefaultSubobject\<UAISenseConfig_Sight\>(TEXT("SightConfig"));

SightConfig-\>SightRadius = 3000;

SightConfig-\>LoseSightRadius = 3500;

SightConfig-\>PeripheralVisionAngleDegrees = 90.0;

SightConfig-\>DetectionByAffiliation = FAISenseAffiliationFilter(true, true, true);

Perception-\>ConfigureSense(\*SightConfig);

*// set up Hearing sense*

Perception-\>SetSenseEnabled(UAISense_Hearing::StaticClass(), true);

HearingConfig = CreateDefaultSubobject\<UAISenseConfig_Hearing\>(TEXT("HearingConfig"));

HearingConfig-\>HearingRange = 4000;

HearingConfig-\>DetectionByAffiliation = FAISenseAffiliationFilter(true, true, true);

Perception-\>ConfigureSense(\*HearingConfig);

> **Source image:** image204.png *(media file pending upload: `image204.png`)*

3.  It binds a function to the Perception Component’s OnTargetPerceptionUpdated delegate (more on that in the Perception section.

4.  It disables the StateTree automatically starting, since we want to change the StateTree at runtime.

*// disable state tree starting automatically; we will do this ourselves at BeginPlay*

StateTreeAI-\>SetStartLogicAutomatically(false);

### Perception Component Integration

The GuardControllerBase has an AIPerceptionComponent (this is the vision cone). I won’t go into detail on the PerceptionComponent’s inner workings, just the Controller’s job in relation to it. In the constructor, it registers its own function to the PerceptionComponent’s delegate so it can react when the perception detects a stimulus.

*// add delegate for perception updates*

Perception-\>OnTargetPerceptionUpdated.AddDynamic(this, &AGuardControllerBase::OnTargetPerceptionUpdated);

Now we’ll set up a situation: The player crosses into the guard’s vision cone, stays for a couple seconds, then breaks line of sight.

1.  The player enters the vision cone, triggering OnTargetPerceptionUpdated:

    1.  check to see if the player is a DetectableLight

    2.  add the player to LightsInRange

    3.  start tracking the player’s Red/Yellow/Green detection state every 0.2 seconds.

<!-- -->

1.  StartTrackingDetectionState starts a loop to call GetLightInfo every 0.2 seconds

2.  GetLightInfo uses a standard “find the biggest item in this array” style loop. It initializes all of the variables, then does the following for each iteration of the loop:

    1.  Asks the Player through the DetectableLight interface, which uses the GetDetectability function, for their location, light strength, and whether they’re in a crevice.

auto \[Location, LightStrength, bHiding\] = IDetectableLight::Execute_GetDetectability(Light.GetObject());

2.  Asks the Perception component to calculate the detection score (DetectionStrength, a number between 0 and 1). It checks to see if the player is hiding in a crevice, setting the strength to 0 if they are.

*// Player should not be detected if they're hiding in a crevice.*

if (!bHiding) {

NewDetectionStrength = GuardPerception-\>GetDetectionStrength(GetPawn()-\>GetActorLocation(), Location, SightConfig-\>LoseSightRadius, LightStrength);

} else {

NewDetectionStrength = {0, 0};

}

3.  Uses the DetectionStrength to calculate the DetectionState (Red, Yellow, Green)

*// calculate the new green/yellow/red state based on the strength*

EDetectionState NewDetectionState = GuardPerception-\>GetDetectionState(NewDetectionStrength.YellowStrength, NewDetectionStrength.RedStrength);

4.  Let’s review. At this point, we’ve confirmed that the Player is not hiding in a crevice and we’ve labeled them Red, Yellow, or Green based on their position and light level.

5.  The next step is to get the detection strength and state from the previous “frame” (but remember, these aren’t actual frames since it’s running every 0.2 seconds). These are stored in OldDetectionStrengths and OldDetectionStates. (In this case, they are EMPTY, because the player is just barely getting registered with the perception system. Most of the time, it will be actual numbers from the last frame.) We do some fun C++ pointer shenanigans to get the Strength:

FDetectionStrengthPair\* OldDetectionStrengthPtr = OldDetectionStrengths.Find(Light.GetObject());

FDetectionStrengthPair OldDetectionStrength;

if (OldDetectionStrengthPtr == nullptr) { *// the light is entering vision radius and doesn't have an entry in OldDetectionStrengths yet*

OldDetectionStrength = {FLT_EPSILON, FLT_EPSILON};

} else {

OldDetectionStrength = \*OldDetectionStrengthPtr;

}

6.  Then we do the exact same process to get the State (Red, Yellow, Green):

TEnumAsByte\<EDetectionState\>\* OldDetectionStatePtr = OldDetectionStates.Find(Light.GetObject());

EDetectionState OldDetectionState;

if (OldDetectionStatePtr == nullptr) { *// the light is entering vision radius and doesn't have an entry in OldDetectionStates yet*

OldDetectionState = Green;

} else {

OldDetectionState = \*OldDetectionStatePtr;

}

7.  Before doing anything else, we must update the OldDetectionStrengths and States so that we have our *current* values in the next “frame”.

OldDetectionStrengths.Add(Light.GetObject()) = NewDetectionStrength;

OldDetectionStates.Add(Light.GetObject()) = NewDetectionState;

8.  Now we check the strength against our running maximum - remember, this is looping through *all* of the objects in the vision cone to find the “brightest” one.

if (OldDetectionStrength.YellowStrength \> HighestDetectionStrength)

{

HighestNewDetectionState = NewDetectionState;

HighestOldDetectionState = OldDetectionState;

HighestLocation = Location;

HighestLight = Light;

PriorityLight = Light;

}

9.  We let the for loop run to completion. This is what we’ve been building to: **now we have a reference to the “brightest” object in the Guard’s vision cone**, along with its previous and current detection strengths and states.

10. With this information, we call HandleDetectionStateChanges, which is the piece of the C++ class that connects to the Blueprint event graph.

HandleDetectionStateChanges(HighestLight, HighestNewDetectionState, HighestOldDetectionState, HighestLocation);

11. HandleDetectionStateChanges is pretty simple, but it’s better explained by a diagram. It uses the Old and New detection states to decide which Blueprint function it will call: OnLightDetected, OnPlayerLost, or OnLightAggro.

> **Source image:** image297.png *(media file pending upload: `image297.png`)*

3.  We do have one last Perception case to look at: what happens when the player leaves the vision cone? This happens in OnTargetPerceptionUpdated, the function that’s subscribed to the Perception component.

    1.  We remove the stimulus from LightsInRange; this stops us from tracking it.

LightsInRange.Remove(Light);

2.  We remove the stimulus’s values from OldDetectionStates and OldDetectionStrengths

OldDetectionStates.Remove(Actor);

OldDetectionStrengths.Remove(Actor);

3.  We call OnPlayerLost, which happens in Blueprints. This handles the case where the player walks straight from the yellow zone out of the vision cone, without passing through the green zone first (like behind a wall while in the yellow zone). FIX: this should also check to ensure the player is not in the green zone.

OnPlayerLost(Stimulus.StimulusLocation);

This wraps up the Controller’s interaction with the Perception component. To summarize: **The Controller’s purpose is to keep track of the objects in the vision cone, firing off events in Blueprints when the “brightest” object crosses between red, yellow, and green zones.**

## Pawn and Controller (Blueprints)

## BP_Guard01

Variables

- PointsToInvestigate

- PointToGoTo

- CurrentDetectionState

- Randomly Checking Player Crevice

- Default Walk Speed

- GodAI

- WaypointList

- Fix: Move as much as possible to GuardBase

Components

- Capsule Component

  - AlertFwoop

  - Arrow Component (Arrow)

  - Backlight

  - Mesh (CharacterMesh0)

    - DeathLight1

    - DeathLight2

    - EyeLight

    - InternalLight

  - DeathCutsceneCameraLocation

  - DistantAlertScreech

  - EnvironmentLight

  - PatrollingSound

  - PlayerFarAwayCheck

  - Point Of Interest Range

- Character Movement (CharMoveComp)

- EnemyAudioComponent

- Fix: organize lights and sounds in the hierarchy

Event BeginPlay

- First set the light colors to <u>Neutral Color</u>

> **Source image:** image78.png *(media file pending upload: `image78.png`)*

- Depending on the guard’s state (determined by the Perception Component), set the guard’s light colors to match its state. If entering the investigate (Yellow) state, play a sound.

> **Source image:** image310.png *(media file pending upload: `image310.png`)*

- Set <u>Distant Alert Audio</u> as <u>Distant Alert Screech</u> and stop playing <u>Distant Alert Screech</u>. Set <u>Patrolling Sound</u> as <u>Patrol Audio</u>, and set <u>Alert Fwoop</u> as <u>Alert Audio.</u> Run <u>Play Patrol sound</u> and <u>Start Audio Occlusion</u>. This sets up the basic enemy sound system.

> **Source image:** image350.png *(media file pending upload: `image350.png`)*

- The death lights are supposed to come on during the death cutscene to create a more visible silhouette, so we start them with an attenuation radius of 0 so they aren’t visible before then. Death lights don’t currently work as intended.

> **Source image:** image156.png *(media file pending upload: `image156.png`)*

- Fix: death lights

On Component End Overlap (PlayerFarAwayCheck)

- This sends a signal to the guard controller if the player leaves the guard’s <u>PlayerFarAwayCheck</u> collider range. Its main use is to make sure that the guard isn’t going to get tied up investigating a spot for a long time while the player is on the other side of the map. Runs the function <u>On Player Far</u> in the guard controller.

- Fix: does the distraction break this? Like if you distract the guard when you’re already outside of the PlayerFarAwayCheck range, getting farther away will never run this function, meaning it would be easy to tie up a guard in an investigate sequence that way?

> **Source image:** image160.png *(media file pending upload: `image160.png`)*

Event Boost Guard Speed

- Speed up the guard when the watcher calls it

> **Source image:** image224.png *(media file pending upload: `image224.png`)*

- Fix: This doesn’t seem to do anything? It just prints a string.

Event glow

- Works with the post process volume to create the glow effect after the enemy “eats” a distraction.

> **Source image:** image84.png *(media file pending upload: `image84.png`)*

- Fix: Deprecated? The enemy no longer eats the distraction.

On Component Begin Overlap (Point Of Interest Range)

- This runs the random crevice check. If the enemy’s <u>Point of Interest Range</u> collider collides with a crevice, so long as the enemy is in its Green (Patrol) state, it runs <u>Randomly Check Player Crevice</u> in the guard controller.

> **Source image:** image365.png *(media file pending upload: `image365.png`)*

Event SetLightColors

- Sets the Eye Light, Environment Light, Internal Light, and Backlight all to be the input light color. Called mostly in Begin Play to indicate changes in the guard state.

> **Source image:** image317.png *(media file pending upload: `image317.png`)*

## BP_GuardController01_AIC

Variables

- ActorToLookAt

- InvestigatedInterestInTheLastLittleBit

  - Don’t like this name

- InvestigatingLostStimulus

- Aggroing

Event OnHeardStimulus

- Sends tag Enemy.Guard.StimulusHeard to the state tree.

> **Source image:** image16.png *(media file pending upload: `image16.png`)*

Event On Light Detected

- Gets detected actor and checks whether it is a <u>Player Base</u>.

  - This branch doesn’t do anything because we no longer are trying to detect a distraction lying on the ground.

> **Source image:** image175.png *(media file pending upload: `image175.png`)*

- Send a state tree event with the tag Enemy.Guard.StimulusSeen

> **Source image:** image328.png *(media file pending upload: `image328.png`)*

- Call <u>On Guard Yellow</u> and set the detected actor as <u>Actor to Look At</u>

> **Source image:** image298.png *(media file pending upload: `image298.png`)*

Event on Light Aggro

- Gets the detected actor and checks whether it is a Player Base.

> **Source image:** image200.png *(media file pending upload: `image200.png`)*

- If it is a Player Base, play a sound and then send a state tree event with the tag Enemy.Player.Seen.. Set <u>Aggroing</u> to True, call <u>On Guard Red,</u> the set the detected actor as <u>Actor to Look At</u>

- If the detected actor is not a Player Base (meaning it is a distraction), send a state tree event with Enemy.Guard.DistractionSeen as the tag. Call <u>On Guard Red</u> and set the detected actor as <u>Actor to Look At</u>

  - Is this ever true? Now that the distractions aren’t things the enemy detects lying on the ground? This might be deprecated

> **Source image:** image166.png *(media file pending upload: `image166.png`)*

Event On Player Lost

- Called when the player leaves the yellow zone. If the player either enters the green zone from the yellow zone or exits the yellow zone suddenly by hiding behind an obstacle, the player is “lost” from the enemy perception and this runs.

- First, check to see whether the player is <u>In Crack</u>. Then check if the enemy is <u>Aggroing</u>. If either of these are true, stop running the event.

> **Source image:** image203.png *(media file pending upload: `image203.png`)*

- Play the look around animation and send an event to the state tree with the tag Enemy.PlayerLost. Call On Guard Green (to set the color of the guard’s lights) and set <u>Actor to Look At</u> as nothing, so it no longer looks at a fixed point. Set <u>Investigating Lost Stimulus</u> as true, and after a delay (so the look around animation can complete) play the idle animation.

> **Source image:** image27.png *(media file pending upload: `image27.png`)*

- Fix: Casts to BP_Player, BP_Guard01

Event Go to Point Of Interest

- First check if <u>InvestigatedInterestInTheLastLittleBit</u> is true. If it is, the event finishes. If not, set <u>Investigated Interest in the Last Little Bit</u> to be true, then send a state tree event with the tag Enemy.Guard.PointOfInterestDetected. Delay for 7 seconds, then set <u>Investigated Interest in the Last Little Bit</u> to be false.

> **Source image:** image189.png *(media file pending upload: `image189.png`)*

- Fix: The branch that checks <u>Is Crevice</u> doesn’t do anything

Event Go To New Stimulus (God AI Stimulus)

- Called by the God AI (In BP_WaypointManager) to send the guard to the player when the player is caught by the watcher. Also called when the player uses a distraction.

- Sends a state tree event with tag Enemy.Guard.GodAIStimulus.

> **Source image:** image58.png *(media file pending upload: `image58.png`)*

Event On Player Far

- Called in BP_Guard01 when the player leaves the enemy’s <u>Player Far Away Check</u> range.

> **Source image:** image177.png *(media file pending upload: `image177.png`)*

Event Randomly Check Player Crevice

- This runs when the enemy comes near a crevice the player is hiding in and the enemy is in its green patrolling state. It may choose to randomly check inside the crevice.

- First, check to see if there are any component tags active in the State Tree. If it’s empty, that means the enemy is in its patrol state and is not currently completing any action. Then check if <u>In Crack</u> is true, and if it is (meaning the player is in the crack), get a Random Bool with Weight and check if it’s true. This is the chance of the player crevice getting checked.

> **Source image:** image152.png *(media file pending upload: `image152.png`)*

- If the Random Bool with Weight returns true and we proceed with the check, get the crevice and set that as <u>Point to Go To</u>. Then send a state tree event with the tag Enemy.Guard.PlayerCreviceDetected and set <u>Randomly Checking Player Crevice</u> to be true.

> **Source image:** image207.png *(media file pending upload: `image207.png`)*

- Fix: Casts to BP_Crack_1, BP_Guard01, BP_PointOfInterest_Crevice

## BP Reference audit - Controller

ABP_GuardTestAnims:

> **Source image:** image321.png *(media file pending upload: `image321.png`)*

STT_ChooseNextPointOfInterest

> **Source image:** image61.png *(media file pending upload: `image61.png`)*

fix: pull ActorToLookAt into C++ parent

BP_Guard01:

> **Source image:** image66.png *(media file pending upload: `image66.png`)*

> **Source image:** image73.png *(media file pending upload: `image73.png`)*

fix: declare these two functions in C++ parent (definition can stay in BP if needed)

GI_Lantern:

> **Source image:** image270.png *(media file pending upload: `image270.png`)*x3

fix: remove cast; Get Controlled Pawn exists in base Controller class

BP_LightProjectile:

> **Source image:** image163.png *(media file pending upload: `image163.png`)*

BP_WaypointManager:

> **Source image:** image305.png *(media file pending upload: `image305.png`)*x2

fix: declare GoToNewStimulus in C++ parent

## BP Reference audit - Pawn

AIC_GuardController02, BP_GuardController01_AIC:

> **Source image:** image80.png *(media file pending upload: `image80.png`)*> **Source image:** image39.png *(media file pending upload: `image39.png`)*> **Source image:** image76.png *(media file pending upload: `image76.png`)*

fix: move PointToGoTo and RandomlyCheckingPlayerCrevice to C++

BP_GuardController01_AIC:

> **Source image:** image287.png *(media file pending upload: `image287.png`)*

fix: define a function to get the skeletal mesh in C++, then implement it in Blueprints

STT_CheckIfPointIsCrevice:

> **Source image:** image318.png *(media file pending upload: `image318.png`)*

fix: move PointToGoTo to C++

STT_ChooseClosestPointsInRange:

> **Source image:** image208.png *(media file pending upload: `image208.png`)*> **Source image:** image65.png *(media file pending upload: `image65.png`)*

fix: move PointsToInvestigate and PointOfInterestRange to C++

STT_ChooseClosestPointOfInterest:

> **Source image:** image243.png *(media file pending upload: `image243.png`)*> **Source image:** image62.png *(media file pending upload: `image62.png`)*> **Source image:** image92.png *(media file pending upload: `image92.png`)*

there are three 3 cast nodes to be replaced, each referencing a combination of these 3 variables

fix: move all 3 variables to C++

STT_ChooseRandomWaypoint:

> **Source image:** image352.png *(media file pending upload: `image352.png`)*

fix: move WaypointList to C++

STT_ChooseWaypointGodAI:

> **Source image:** image254.png *(media file pending upload: `image254.png`)*

fix: move GodAI to C++; this will require WaypointManager to move to C++ first

STT_DeathCutscene:

> **Source image:** image147.png *(media file pending upload: `image147.png`)*

fix: move DeathCutsceneCameraLocation to C++ (or if it can’t exist in C++, make a C++ getter that is implemented in Blueprints)

> **Source image:** image36.png *(media file pending upload: `image36.png`)*

fix: make a function in Guard (OnDeathCutscene or some such) that handles all of the light logic during the death cutscene instead of doing this logic in the STT

STT_InvestigateCrevice:

> **Source image:** image293.png *(media file pending upload: `image293.png`)*

fix: move PointToGoTo, covered by several others in this list

BP_WaypointManager:

> **Source image:** image128.png *(media file pending upload: `image128.png`)*> **Source image:** image329.png *(media file pending upload: `image329.png`)*> **Source image:** image346.png *(media file pending upload: `image346.png`)*

> **Source image:** image290.png *(media file pending upload: `image290.png`)*

fix: these are just a few examples of BP Guard 01 references. Enumerating all of them would be more work than it’s worth. I suggest we change all of the types to GuardBase one by one, confirming that the WaypointManager still works after each change. We’ll also need to move some functions/variables to C++.

Design For States:

<table style="width:100%;">
<colgroup>
<col style="width: 21%" />
<col style="width: 22%" />
<col style="width: 27%" />
<col style="width: 29%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>State</strong></th>
<th><strong>How it feeds core pillars</strong></th>
<th><strong>Emotions/thoughts evoked by state</strong></th>
<th><strong>How the player can beat it</strong></th>
</tr>
<tr class="odd">
<th>Patrol</th>
<th>wandering randomly enhances “lost” vibes</th>
<th><p>aversion, dread; “Dang hope that thing doesn’t come over here, it looks scary”</p>
<p>relief; “oh thank goodness it’s going somewhere else”</p></th>
<th>Be aware of where it is and stay out of sight, keep it away from you with distractions, use crevices, boxes, and your surroundings to hide</th>
</tr>
<tr class="header">
<th>Investigate</th>
<th>Methodical, intelligent searching of an area</th>
<th><p>panic level 1; “Ah frick it saw me, I gotta break line of sight or get far away”</p>
<p>relief + tension; “oh thank goodness it lost my scent, I still gotta be careful until it leaves”</p></th>
<th>intelligent use of distraction, crevice, put distance or obstacles between you and the enemy</th>
</tr>
<tr class="odd">
<th>Hunt</th>
<th>Intelligent, predatory searching for the player</th>
<th><p>panic level 2; “It knows where I am and I have to escape or hide asap”</p>
<p>highest level of tension where you can actually do something</p></th>
<th><p>Invisibility, intelligent use of distraction, crevice (definitely triggers QTE), escaping enemy perception range</p>
<p>just hiding behind obstacles is less effective</p></th>
</tr>
<tr class="header">
<th>Attack</th>
<th>releases tension with scary</th>
<th>panic level 3, Fight or Flight, denial anger bargaining depression acceptance</th>
<th>Can’t</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## StateTree

State Tree v3 is still a work in progress, and it <u>has not been fully proven</u>. My philosophy for the change is twofold: 1) If each state is meaningfully separated from the others, programmers will be able to compartmentalize their thinking and focus on a single state at at time; and 2) By using two layers of motivation variables (“perception” and “motivation”), programmers will be able to more reliably debug transitions between states.

With those ideas in mind, let’s look at the draft for v3, which is actually called ST_Guard02 in the project.

ST_Guard02 represents the highest level of the state tree. It doesn’t care about all the individual actions the Guard is taking, but instead focuses on the general states that the Guard can be in. Right now these are separated into Patrol, Noticed, Identified, and Attack. Note that while I have colored these green, yellow, orange, and red respectively, they’re *not* 1-to-1 parallels with the Perception component.

This is the main tree. It’s a state machine, which means only one state is active at a time, and states can transition to other states based on set rules.

> **Source image:** image195.png *(media file pending upload: `image195.png`)*

This is the Schema. I’ve overridden the ContextActor class, since this state tree will always be used by a GuardBase. The Context is passed into StateTree Tasks by default. Modifying this value allows State Tree Tasks to use GuardBase functions without casting to GuardBase first.

> **Source image:** image54.png *(media file pending upload: `image54.png`)*

This is the Parameters menu. It stores values that are accessible throughout the StateTree. I’ll talk more about the individual parameters later in this doc. They can be set by State Tree Tasks and State Tree Evaluators, which we’ll discuss next.

> **Source image:** image312.png *(media file pending upload: `image312.png`)*

This is the Evaluators menu, which contains only one Evaluator right now. I expect this Evaluator to change significantly as I work out problems, but we can see that right now it takes in the Guard and Controller from the context menu, setting the Perception and returning three other variables. **This is a significant change from the old state tree**, and will be the main mechanism for getting information into our state tree (the old state tree uses Transition On Event, which is technically cheaper performance-wise but more difficult to work with. Anything could send any event to the state tree at any time, while this newer model will function as a more independent component with a clearly defined interface).

> **Source image:** image116.png *(media file pending upload: `image116.png`)*

To understand the purpose of the Evaluator, we need to know how Transitions work, since they rely on the Evaluator to function. This is what a Transition looks like:

> **Source image:** image294.png *(media file pending upload: `image294.png`)*

On Tick (which can be modified to run less often than actual Tick), it checks to see if the specified Conditions are true. If it is, it executes the transition and switches to the next State. This particular Condition checks the Parameters.Motivation variable, which will be changed by the Evaluator.

So what’s the Evaluator’s job? It will do the following:

1.  subscribe to all of the External Factors that influence the Guard’s behavior (perception component, god ai, distraction, etc)

2.  combine all of those factors in a magical algorithm soup

3.  magical algorithm soup produces a “motivation” variable that tells the state tree what it should be doing (patrol, investigate, hunt, attack).

My next job on this will be to define what exactly the magical algorithm soup does. This is how it behaves right now:

> **Source image:** image70.png *(media file pending upload: `image70.png`)*

This is the STE subscribing to all of the perception-related events in GuardControllerBase. When one of those functions is called (which is something you can read about in the GuardControllerBase earlier in this doc), the STE will catch it and call one of its own functions, which I will show here:

> **Source image:** image216.png *(media file pending upload: `image216.png`)*> **Source image:** image118.png *(media file pending upload: `image118.png`)*> **Source image:** image86.png *(media file pending upload: `image86.png`)*

Right now, it gathers an Object/Vector to give the StateTree an Actor and/or location for the thing it senses. This is temporary code and should be replaced with something better (I propose changing Guard Yellow Info to match what’s needed here).

ApplyRed, ApplyYellow, and ApplyGreen are unfinished. Here is ApplyRed as an example of finishing the STE pipeline:

> **Source image:** image222.png *(media file pending upload: `image222.png`)*

When it’s called, it assigns AcquiredTarget and TargetLocation, which are both variables in the “Output” category. Then, it assigns the PerceptionParam by reference: this will change the actual Perception parameter in the State Tree so that the Transitions can react accordingly.

Let’s also take a brief look at one of the subtrees. This is ST_Patrol:

> **Source image:** image46.png *(media file pending upload: `image46.png`)*

My current idea is that the state tree will go through the green states as it patrols, then interrupt, set Motivation, and return to a different state using the gray nodes at the end once it receives a Perception tag. I don’t think this is the best way to do this, and I’d rather find a better solution.

This concludes my rough outline of the State Tree. There are still several open questions that need to be solved:

- How can we ensure that all of the State Tree Tasks have the right information at the right time? (Player Actor, Player Location)

- Are there situations where the State Tree needs to jump directly into a low-level state without first going through the high-level state? How should we handle those?

- How can we process input from multiple sources? We’re using the perception component, state tree transitions, the God AI, and the brazier/distractions to influence the Guard’s behavior, and we need to prioritize each one under various situations.

- How should we handle transitions between high-level states? I have a potential design but I’m not sure how well it’ll work.

## State Tree Tasks

STE_BreakPatrolWaypointData

- Empty

- FIX: WHAT IS THIS FOR??? DELETE???

STT_CheckifPointIsCrevice

> **Source image:** image7.png *(media file pending upload: `image7.png`)*

- Gets the guard from the context, casts to BP_Guard01 and gets the “Point to go to”, then checks if that’s a BP_PointOfInterest_Crevice. If it is, it succeeds the task, if not the task fails.

- FIX: CAST TO BP_GUARD01

STT_ChooseClosestPointsInRange

> **Source image:** image110.png *(media file pending upload: `image110.png`)*

- Gets the guard from the context, then clears the Points to Investigate array and Closest Points array stored within the guard to make sure they are empty. It then finds the overlapping actors within the guard’s Point of Interest Range of class BP_PointOfInterest, (so all points of interest and crevices) and in a for each loop adds them to the local array FoundPoints.

> **Source image:** image349.png *(media file pending upload: `image349.png`)*

- Now we make sure we aren’t trying to investigate more points than are within our range. Number of Points to Investigate is a local variable for how many POIs we want to look at during an investigation, but if there were only two within range and Number of Points to Investigate is three, that’s a problem. This checks the length of Found Points and sets Number of Points to Investigate to len(Found Points) if there are fewer found points than the set number to investigate.

> **Source image:** image279.png *(media file pending upload: `image279.png`)*

- This loop finds the closest few points of interest and stores them in the local array Closest Points.

- The outer for loop will run as many times as the set Number of Points to Investigate. It sets local variable Min Distance to a very high number (100,000), and then runs another For Each Loop. This loop goes through Found Points and for each point, it gets the distance to the guard. If that distance is less than the Min Distance, it sets that distance as the new Min Distance and sets that as the Current Closest Point. It loops through every point in Found Points that way, ultimately storing the very closest point. At the end of the loop, it stores the closest point in Closest Points and removes it from Found Points. This whole thing runs as many times as Number of Points to Investigate, leaving you with that many points in Closest Points.

> **Source image:** image138.png *(media file pending upload: `image138.png`)*

- Sets the guard’s <u>Points to Investigate</u> to <u>Closest Points</u>. Succeeds the task.

- FIX: 2 CASTS TO BP_GUARD, SOME PRINT STATEMENTS

STT_ChooseNextPointOfInterest

- Get guard from context. First checks to see if <u>Randomly Checking Player Crevice</u> is true, and if it is, takes the guard’s stored <u>Point to Go To</u> and sets the output <u>Point to Go To</u> as that. It also sets that point as the <u>Actor to Look at</u>, then finishes the task.

  - For a random player crevice check, <u>Point to Go To</u> is set in BP_GuardController_AIC in the event <u>Randomly Check Player Crevice</u>, which runs when BP_Player runs <u>On Component Begin Overlap (Point Of Interest Range)</u> with a crevice

> **Source image:** image14.png *(media file pending upload: `image14.png`)*

- If not randomly checking player crevice, check if Points to Investigate (stored in the Guard) is empty. If empty, that means we’ve investigated everything already, and the task finishes with a failure (which returns to root), returning the guard to patrolling behavior

> **Source image:** image170.png *(media file pending upload: `image170.png`)*

- If it’s not empty, we check local var Chance of Checking Player Crevice First. If that is true (meaning that if the player is hiding in a crevice nearby, that point will be checked first), the For Loop checks each point in Points to Investigate for if they are a crevice, and if they have a player inside. If there is one, that crevice is set as the Point to Go To. When the loop completes, if Point to Go To is valid (meaning there is a player crevice that will be checked), we finish the task with a success.

> **Source image:** image239.png *(media file pending upload: `image239.png`)*

> **Source image:** image167.png *(media file pending upload: `image167.png`)*

- If either there is no crevice with a player inside, or if the random bool with weight on Chance Of Checking Player Crevice First is false (meaning we don’t weight it to check the player crevice first), then we select a random point from Points to Investigate and set that as the point to go to, then remove it from the list. It also is set as the Actor to Look At.

> **Source image:** image105.png *(media file pending upload: `image105.png`)*

- This entire task will run once for every point in Points to Investigate, unless interrupted by something.

- FIX: CASTS TO BP_GUARD01, BP_GUARDCONTROLLER01_AIC, BP_POINTOFINTEREST, BP_POINTOFINTERESTCREVICE, BP_CRACK,

STT_ChooseRandomWaypoint DEPRICATED???

- Sets local array Waypoint List as Waypoint List (from BP_Guard01) and selects a random waypoint to move to. If that point is valid, the task succeeds.

> **Source image:** image38.png *(media file pending upload: `image38.png`)*

- FIX: I DON’T THINK WE’RE USING THIS, CAST TO BP_GUARD01

STT_ChooseWaypointGodAI

> **Source image:** image137.png *(media file pending upload: `image137.png`)*

- Gets the GodIA from BP_Guard01 and calls Assign New Target Waypoint (located in BP_WaypointManager), then gets Target Waypoint from the God AI and sets that as Waypoint to Move To.

- FIX: CAST TO BP_GUARD01

STT_DeathCutscene

- First we cast to the camera manager and set Attacking Guard (inside the camera manager) to Guard (from context). Now the camera manager knows what guard is attacking. Then we get Death Cutscene Camera Location from the Guard, and that becomes our Death Cutscene Arrow (both locally and in the camera manager). This is where the fixed camera is going to move to during the cut scene.

> **Source image:** image332.png *(media file pending upload: `image332.png`)*

- Then we call Recall Light inside of BP_Player. This destroys any distraction currently in the player’s hand. We Remove Mapping Context and Disable Input, removing the player's ability to move or do anything. We also turn off the visibility of the player cylinder.

> **Source image:** image153.png *(media file pending upload: `image153.png`)*

- We then run Death in BP_Soul, which changes the material and visibility. Then we play the death cutscene animation.

  - In the death cutscene animation, we first run a short delay, so the animation starts to play before changing the fixed camera. This is intended to let the enemy complete the “wind up” part of the animation before throwing the player to the floor (fixed camera location).

> **Source image:** image324.png *(media file pending upload: `image324.png`)*

- We then set up some lights to make the enemy silhouette read better.

  - These aren’t fully working

> **Source image:** image107.png *(media file pending upload: `image107.png`)*

- Check to see if the cut scene is going to be blocked by walls or obstacles with the function Death Camera Obstructed, which sends a line trace from the enemy to the player, and if it is blocked we run Rotate Enemy Away from Wall

> **Source image:** image100.png *(media file pending upload: `image100.png`)*

> **Source image:** image235.png *(media file pending upload: `image235.png`)*

- Rotate Enemy Away From Wall runs a while loop where so long as Death Camera Blocked is true, we take the guard and rotate it a few degrees, then check to see if the camera is still obstructed.

- Only rotates in one direction currently

> **Source image:** image102.png *(media file pending upload: `image102.png`)*

- Set camera state to DeathCutscene in the camera manager. This switches the camera to a fixed camera location at Death Cutscene Arrow.

- After another delay, it takes the mesh of the soul and attaches it to EatSoulSocketL on the guard skeleton. This makes it so that the guard appears to eat the soul. Another delay lets the animation finish.

> **Source image:** image248.png *(media file pending upload: `image248.png`)*

- The task succeeds

- FIX: CASTS TO BP_GUARD01, BP_SOUL, BP_PLAYERCONTROLLER, BP_PLAYER, BP_PLAYERCAMERAMANAGER

STT_EatDistraction

- As the enemy no longer “eats” the distraction, this just creates a 2 second delay used after the enemy reaches the distraction.

- FIX: DELETE OR RENAME TO BE A PAUSE. WE DON’T NEED TO EAT THE DISTRACTION.

STT_GuardBase

- Empty

- FIX: WHAT IS THIS FOR??? DELETE???

STT_IncreaseGuardSpeed

- Increases guard speed 3x when it aggros and begins to chase the player.

> **Source image:** image221.png *(media file pending upload: `image221.png`)*

STT_InvestigateCrevice

- Gets player pawn and sets the player as local variable <u>Player.</u> Then we get the <u>Point to Go To</u> from the guard, since that point is the crack the guard is investigating. We check if <u>In Crack</u> (from BP_Crack_1) is true, and if it is not, we set that point as local variable <u>Crack</u> and finish the task with a success.

> **Source image:** image33.png *(media file pending upload: `image33.png`)*

- If <u>In Crack</u> is true, set the point of interest to local variable <u>Crack</u> and start the crack check.

  - First, a short delay to create a feeling of anticipation as the guard pauses outside the crack.

  - Then we set the Guard transform to match the crack arrow, which ensures the guard is in the right position for the check.

> **Source image:** image49.png *(media file pending upload: `image49.png`)*

- If <u>QTEEnabled</u> is true, start the quick time event.

  - If not true, run <u>First Crack Successful</u> in GI Lantern, then succeed the task. This means we aren’t running the quick time event and the player automatically succeeds.

- Run <u>Start QTE</u> in GI Lantern, then play the crack check animation. After a 2 second delay for the animation to play, a loop runs checking if the QTE is still active. As long as it is, we keep running a 0.1 second delay. Once <u>QTEActive</u> is false, play the Idle animation again and finish the task with a success.

> **Source image:** image367.png *(media file pending upload: `image367.png`)*

- FIX: CASTS TO BP_PLAYER, BP_GUARD01, BP_CRACK_1, PRINT STATEMENTS

STT_KillPlayer

- <u>Add Test Event</u> to GI_Lantern, then re-opens the level

> **Source image:** image301.png *(media file pending upload: `image301.png`)*

- Should request GI/GM instead of doing this directly

STT_LookAround

- Plays look around animation once

> **Source image:** image21.png *(media file pending upload: `image21.png`)*

STT_LookAtInterest

- Makes the enemy look down at a point of interest when investigating.

> **Source image:** image67.png *(media file pending upload: `image67.png`)*

- <u>Event EnterState</u> gets the actor rotation from the guard and sets that as <u>Original Rotation</u>. It then creates a rotator from the location of the point being investigated and sets that as the target location.

> **Source image:** image8.png *(media file pending upload: `image8.png`)*

- On <u>Event Tick</u>, we lerp from the original rotation to the <u>Target Rotation</u>. If the enemy is starting to look at the point of interest, then it lerps like normal to look at it. Once it’s done looking, if <u>Original Rotation</u> and <u>Target Rotation</u> are not equal, <u>Target Rotation</u> is set to <u>Original Rotation,</u> that way it is set to look back the way it was originally looking. The guard lerps back to its original rotation and the task succeeds.

- FIX: looks dumb

STT_PlayIdleAnim

> **Source image:** image25.png *(media file pending upload: `image25.png`)*

- Gets the guard from the context and plays the idle animation on loop

- Runs when the guard is in its “patrol” green state.

STT_PlayInvestigatingAnim

> **Source image:** image10.png *(media file pending upload: `image10.png`)*

- Gets the guard from context and plays the investigating animation on loop

- Runs when the guard is in its “investigate” yellow state.

STT_PlayHuntingAnim

> **Source image:** image164.png *(media file pending upload: `image164.png`)*

- Gets the guard from context and plays the hunting animation on loop

- Runs when the guard is in its “hunting” orange state

STT_PlayAggroAnim

> **Source image:** image111.png *(media file pending upload: `image111.png`)*

- Gets the guard from context and plays aggro animation on loop

- Runs when the guard is in it’s “Aggro” red state, as it charges the player before the death cutscene plays

STT_PlaySound

- Gets the enemy from context, gets the enemy location, and plays sound at location, then succeeds the task.

> **Source image:** image303.png *(media file pending upload: `image303.png`)*

STT_ResetEnemySpeed

- Called when the Guard enters the Patrol state.

- Resets the Guard walk speed back to 400 then succeeds the task.

> **Source image:** image180.png *(media file pending upload: `image180.png`)*

STT_SetGameplayTag

- Gets a reference to a property in the state tree and modifies it directly.

> **Source image:** image231.png *(media file pending upload: `image231.png`)*

STT_TeachInvisibility

- This runs the Teach Invisibility event when the player first encounters an enemy aggroing on them. First, it runs <u>Check Should Teach Invisibility</u> in GI_Lantern, then uses the outputs to set <u>Should Aggro</u> and <u>First Aggro</u>. The invisibility teaching runs within GI_Lantern in <u>Suggest Invisibility</u> if activated.

> **Source image:** image188.png *(media file pending upload: `image188.png`)*

## Waypoint Manager (God AI)

The purpose of the Waypoint Manager is to keep track of a set of waypoints. The Guards ask the Waypoint Manager for a new target waypoint, and it evaluates its set of waypoints, returning an appropriate one based on the state of the other guards and the player’s location. The Waypoint Manager also tells a Guard to go to a particular location when notified by a Brazier or Distraction.

The C++ parent is mostly empty. Let’s take a look at the variables we do have.

The Waypoints array is mostly unused. It is assigned values in L_Hallway01, which we are not using anymore. In the current level (L_Courtyard_V3), it is left empty. Its intention was to store a list of waypoints so the Guards wouldn’t have to, but in the code, it gets the Guard’s waypoints directly.

TArray\<FGuardWaypoint\> Waypoints;

This FGuardWaypoint struct, however, is used frequently throughout the Guard and Controller. The weight is not referenced anywhere, but we may want to use it eventually.

USTRUCT(BlueprintType)

struct FGuardWaypoint

{

GENERATED_BODY()

public:

TObjectPtr\<AWaypointBase\> Waypoint;

float Weight = 1.0f;

};

Here are the variables we’re working with:

> **Source image:** image265.png *(media file pending upload: `image265.png`)*

On BeginPlay, we store the Player actor so we can use it later.

> **Source image:** image256.png *(media file pending upload: `image256.png`)*

The most important function in this class is AssignNewTargetWaypoint. This is what the Guard calls when it needs a new waypoint to go to.

> **Source image:** image249.png *(media file pending upload: `image249.png`)*

First it confirms that no other Guard is currently using this function, buffering the request if there is one. If it confirms that it’s allowed to move forward, it sets Processing, blocking any other Guards from using the function. (This should definitely be changed. I’m pretty sure the only race condition involved in this function is the variable TargetWaypoint, which should really be a return value from the function and not stored at all.)

> **Source image:** image184.png *(media file pending upload: `image184.png`)*

Next, it chooses waypoints based on the ScriptedState: in the “Enemies Stay Upstairs” state, it restricts the available waypoints, but otherwise they can choose any waypoint.

GetNewTargetWaypointUpstairs is tightly coupled to the level design and works differently than the ordinary GetNewTargetWaypoint. The upstairs waypoint list is a member variable in WaypointManager, while the normal waypoint list is a member variable in the guards. We need to make these consistent, probably by storing both waypoint lists in the WaypointManager.

GetNewTargetWaypoint or GetNewTargetWaypointUpstairs looks at the waypoints the guard can go to, then decides which one it should be sent to. Next we set the Target Waypoint accordingly, update the guard’s target location in the GuardToWaypointLocation map, then unmark Processing, allowing other Guards to access the function.

Right now, the class depends on the Guard to ask it for the recently-set TargetWaypoint. This should definitely be changed into a return value.

> **Source image:** image169.png *(media file pending upload: `image169.png`)*

So how does the WaypointManager decide which waypoint the Guard should go to?

Right now, it needs to consider 3 factors:

1.  How many waypoints does the Guard have to choose between?

2.  Is this the furthest Guard from the player? If so, it should be sent close to the player.

3.  Is there another Guard going to the same Waypoint? If so, it should choose a different one.

Let’s look at how GetNewTargetWaypoint incorporates those 3 decision points. First, it calls IsFurthestGuardFromPlayer. I won’t put screenshots of the actual function here since its purpose is really straightforward. It gets the Player’s location, then calculates each Guard’s **navigation** **path** **distance** to that location. If our Guard has the largest distance, it returns true.

> **Source image:** image276.png *(media file pending upload: `image276.png`)*

Now we know if we have the furthest Guard, and we store that information in a variable.

Next up, we store the Guard’s list of waypoints in our own local variable. We’re gonna be manipulating its values later, so we need to make a copy instead of accessing the Guard’s member variable directly.

> **Source image:** image134.png *(media file pending upload: `image134.png`)*

Now we have the information we need to make our first major decision: **How many waypoints are available in the first place?** We get the number of waypoints, then use a Switch statement to decide what to do.

0: there are no waypoints. We raise an error because we can’t return one.

1: there is exactly one waypoint. We return it because there are no other options

default: there are 2+ waypoints. We move forward into our other selection criteria.

> **Source image:** image277.png *(media file pending upload: `image277.png`)*

Let’s make our second major decision: **Is this the furthest Guard from the player?**

We already calculated this, so we use a simple if statement with the boolean we stored.

If this is the furthest Guard, we call GetNearestWaypointToPlayer and send it to that waypoint. This is another small function that simply takes in a list of waypoints and returns the one with the **closest path distance** to the Player.

We store that waypoint, then check our third major decision: **Is there another Guard heading there already?** We call IsAlreadyTargeted, which loops through the map of Guards and confirms that there are no others going to the same Waypoint. If it’s not already targeted, we’ve found our waypoint, and we return it.

If there *is* another Guard heading there, we remove this waypoint from our temporary list, then move to the last step.

> **Source image:** image149.png *(media file pending upload: `image149.png`)*

By this point, a Furthest Guard has exhausted all of their options. Their preferred waypoint (the one closest to the player) is already taken, so what should they pick now?

A non-Furthest Guard is in the same situation. They don’t have a preferred waypoint, so where should they be sent?

Both scenarios lead to the same thing: just use a random waypoint, preferably one that isn’t targeted by any other Guards. GetRandomOpenWaypoint does exactly that, with the caveat that if there are *no* open waypoints, it will choose one at random from the list anyway.

> **Source image:** image320.png *(media file pending upload: `image320.png`)*

This covers all of GetNewTargetWaypoint, so let’s review our event graph to see it with a new perspective.

We can see that after we’ve gotten a Target Waypoint with the criteria we discussed earlier, we set the Target Waypoint variable for the Guard to get (remember, this should probably change to be a return value instead of a member variable), then add it to the target waypoints map.

> **Source image:** image77.png *(media file pending upload: `image77.png`)*

There are a few other things in the WaypointManager to be aware of. Let’s take a look at them:

Send Closest Guard to Location does exactly what it says on the box.

> **Source image:** image148.png *(media file pending upload: `image148.png`)*

It loops through all of the Guards to find the closest one, then uses the following process to send it to a particular location. Note that this uses a BP cast. I’d recommend we make a Guard function to do this whole thing instead of telling the Guard explicitly to set its walk speed and play a sound.

> **Source image:** image24.png *(media file pending upload: `image24.png`)*

The WaypointManager also subscribes to the NotifySuperPing, and it sends the closest guard to a location when it receives it.

> **Source image:** image334.png *(media file pending upload: `image334.png`)*

We also have CloisterEvent, which grabs a guard, teleports it to the Cloister level, then directs it towards the player. This should probably not go here, and I’d suggest putting it in the GameInstance or GameMode. The WaypointManager shouldn’t care about scripted in-game events, and its role in this process should just be the “send closest guard” node at the end.

> **Source image:** image295.png *(media file pending upload: `image295.png`)*

## GuardPerceptionComponent (C++)

The Perception Component is called upon by the GuardController to calculate the Red, Yellow, or Green values for any objects inside of its vision cone. It does this with magical linear algebra wizardry.

Before we get too deep into the code, it’s important to have a conceptual understanding of how the perception works. We can do this using the Python script found at this Git repository: [<u>https://github.com/bsharplydian/los_guard_vision_tool</u>](https://github.com/bsharplydian/los_guard_vision_tool).

We’ll start by looking just at the Yellow zone. The size and shape of the yellow zone are determined by four numbers: \*more detail, exposed to designers

1.  the distance weight

2.  the angle weight

3.  the light weight

4.  the curious (yellow) threshold

Let’s walk through each of them and see how they affect the shape. We’ll start with distance weight.

> **Source image:** image194.png *(media file pending upload: `image194.png`)*

distance 10, angle 0, light 0

This is what the yellow zone looks like when only considering distance. It doesn’t care about the angle the player’s being seen at or the light the player’s giving off.

And now the angle weight:

> **Source image:** image213.png *(media file pending upload: `image213.png`)*

distance 0 (technically 0.09 but close enough), angle 10, light 0

This is what the yellow zone looks like when only considering angle (matplotlib struggles to graph this, but in-engine it’s a perfect cone radiating from the center point) It doesn’t care how far the player is.

Let’s combine distance and angle to create some more interesting shapes.

> **Source image:** image209.png *(media file pending upload: `image209.png`)*

distance 4.87, angle 6.7, light 0

> **Source image:** image348.png *(media file pending upload: `image348.png`)*

distance 2.45, angle 0.64, light 0

We can see that it’s taken on some characteristics of the “angle” shape, and some characteristics of the “distance” shape. It’s biased towards seeing things in front of it, but it doesn’t see *too* far in front. By playing with these values, we can create a shape we like. In addition, its shape is influenced **proportionally** by the relationship between distance and angle. Higher distance weight = closer to a perfect circle; higher angle weight = closer to a cone. Also note that the actual values don’t matter - distance 1 angle 2 will produce the exact same effect as distance 10 angle 20. It only matters *how much bigger* one is than the other.

Now, let’s look at Curious (Yellow) Threshold while holding Distance and Angle constant. This is what determines the “size” of the zone. Here’s a low Curious (Yellow) Threshold (0.156):

> **Source image:** image127.png *(media file pending upload: `image127.png`)*

distance 1.76, angle 3.8, light 0

And here’s a high Curious (Yellow) Threshold (0.842):

> **Source image:** image369.png *(media file pending upload: `image369.png`)*

distance 1.76, angle 3.8, light 0

The lower threshold allows further/peripheral points through, resulting in a bigger shape, and the higher threshold blocks those further/peripheral points, resulting in a smaller shape.

Now let’s look at the Light Weight. This is what makes the player more visible when they’re sprinting and less visible when they’re crouched. In the following screenshot, you can see the effect of varying Light Weight values on the vision cone.

> **Source image:** image205.png *(media file pending upload: `image205.png`)*

The Red Zone functions exactly the same way. It has Distance, Angle, and Light weights, and it can be controlled independently of the Yellow Zone.

These are the current default values of all of the weights and thresholds.

> **Source image:** image172.png *(media file pending upload: `image172.png`)*

Now that we have a conceptual understanding of the vision zones, let’s look at the code and see how we calculate everything.

Here’s the header file. We’ve already gone over most of the variables:

*// How sensitive the enemy is to the player's distance*

float YellowDistanceWeight = 1;

*// How sensitive the enemy is to the player's angle (peripheral vision or straight on)*

float YellowAngleWeight = 1;

*// How sensitive the enemy is to light levels*

float YellowLightWeight = 1;

*// How sensitive the enemy is to the player's distance*

float RedDistanceWeight = 1;

*// How sensitive the enemy is to the player's angle (peripheral vision or straight on)*

float RedAngleWeight = 1;

*// How sensitive the enemy is to light levels*

float RedLightWeight = 1;

*// The threshold at which the enemy becomes curious (0-1)*

float CuriousThreshold = 0.33;

*// The threshold at which the enemy becomes aggro (0-1)*

float AggroThreshold = 0.66;

*// Minimum distance to ensure the enemy aggros. Unused.*

float MinimumAggroDistance = 100;

*// height of the floating debug bar chart*

float DebugVerticalOffset = 300;

Then the following public functions, which we saw in the GuardController (plus a function for debugging):

UFUNCTION(BlueprintCallable, Category="Enemy\|Perception")

FDetectionStrengthPair GetDetectionStrength(FVector SelfLocation, FVector StimulusLocation, float LoseSightRadius, float LightAmount);

UFUNCTION(BlueprintCallable, Category="Enemy\|Perception")

EDetectionState GetDetectionState(float YellowDecision, float RedDecision);

void DebugDetectionStrength(FVector MyLocation, float Angle, float Distance, float LightAmount, const FString\* Identifier) const;

And finally a private function, used only by this class:

void NormalizeDetectionWeights();

Let’s see how they’re built in the CPP file. We’ll start with NormalizeDetectionWeights(). Its purpose is to turn all of the Weight values into a number between 0 and 1. For example, values 1, 2, 1 become 0.25, 0.5, 0.25, which all add

up to 1.

void UGuardPerceptionComponent::NormalizeDetectionWeights()

{

const float YellowTotal = YellowDistanceWeight+YellowAngleWeight+YellowLightWeight;

YellowDistanceWeight /= YellowTotal;

YellowAngleWeight /= YellowTotal;

YellowLightWeight /= YellowTotal;

const float RedTotal = RedDistanceWeight+RedAngleWeight+RedLightWeight;

RedDistanceWeight /= RedTotal;

RedAngleWeight /= RedTotal;

RedLightWeight /= RedTotal;

}

We normalize our weights at BeginPlay.

When the Controller asks us for a Strength, we calculate the detection strength. Parameters for this function are our own location, the stimulus location, our sight range, and the brightness of the object, which we use to determine how strongly we’re sensing the object.

FDetectionStrengthPair UGuardPerceptionComponent::GetDetectionStrength(FVector SelfLocation, FVector StimulusLocation, float LoseSightRadius, float LightAmount) {}

This involves 3 different calculations, since we’re dealing with distance, angle, and light amount.

Light Amount is the easiest, since we get the value through a parameter. Remember, the Controller asked the Player for this value back in GetLightInfo(). We “normalize” this value by multiplying it by the weight.

float YellowLightAmountNormalized = LightAmount\*YellowLightWeight;

Distance is the next easiest. This will be a value between 0 and 1, with 0 at the edge of the vision radius, and 1 right on top of the guard.

float DistanceNormalized = 1-UKismetMathLibrary::Vector_Distance2D(StimulusLocation, SelfLocation)/(LoseSightRadius);

We normalize the distance value in the same way, by multiplying it by its weight.

float YellowDistanceNormalized = DistanceNormalized \* YellowDistanceWeight;

Last, we have Angle. This one is a little more complicated and involves some linear algebra. We end up with a value between 0 and 1, where 0 = to the side and 1 = right in front of the enemy.

FVector Direction = (StimulusLocation - SelfLocation).GetSafeNormal2D();

float AngleNormalized = Direction.Dot(this-\>GetOwner()-\>GetActorForwardVector());

We normalize this just like the other two.

float YellowAngleNormalized = AngleNormalized\*YellowAngleWeight;

Now we have three variables indicating how “strongly” the guard sees the player. They’ve been adjusted with weights depending on which one the designer wants to prioritize. We add all three together to get YellowDecision, a value between 0 and 1. **This is what we compare to the CuriousThreshold (yellow) to decide if it’s “in” or “out” of the yellow zone.**

float YellowDecision = YellowAngleNormalized + YellowDistanceNormalized + YellowLightAmountNormalized;

The RedDecision is calculated exactly the same way, using the Red variables instead of the Yellow ones.

At some point, the Controller will ask us (the PerceptionComponent) to convert this RedDecision and YellowDecision into Red, Yellow, or Green. We calculate this by comparing the Decision variables with the Aggro (red) and Curious (yellow) thresholds:

EDetectionState UGuardPerceptionComponent::GetDetectionState(float YellowDecision, float RedDecision)

{

if (RedDecision \> AggroThreshold)

{

return Red;

}

if (YellowDecision \> CuriousThreshold)

{

return Yellow;

}

return Green;

}

I’d recommend going back to review the Controller now, with more understanding of how the PerceptionComponent works.

## Animation Blueprint

Currently handles functionality for the guard looking directly at the player or point of interest it’s searching for.

Variables

- Actor to Look At

- Look At Target

- IsTracking

- GuardController

- Player Camera Manager

- Locked

- CurrentAnimationState

- Fix: Some variables are Blueprints

Event Blueprint Begin Play

- Get the Guard controller and camera manager and set them as the variables <u>Guard Controller</u> and <u>Player Camera Manager</u>

> **Source image:** image280.png *(media file pending upload: `image280.png`)*

- Fix: Casts to BP_GuardController_01_AIC and BP_PlayerCameraManager

Event Blueprint Update Animation

- First check to see if <u>Player Camera Manager</u> is valid. If it is, check to see if the current camera state is DeathCutscene. If it is, set <u>Locked</u> to be true.

> **Source image:** image322.png *(media file pending upload: `image322.png`)*

- If not, get the <u>Guard Controller</u> and from it get its variable <u>Actor to Look At</u>. Set <u>Is Tracking</u> to True and set <u>Look at Target</u> as the location of <u>Actor to Look At.</u> If <u>Actor to Look At</u> is not valid, that means we don’t have a fixed point to look at. Set <u>Is Tracking</u> to false.

> **Source image:** image81.png *(media file pending upload: `image81.png`)*

## Sound System

Design Statement:

The enemy sound system should contribute to player immersion by making the enemies feel more integrated into the game world. The player should be able to identify features about a given enemy based on how they sound. This includes location and state, meaning whether they are actively seeking the player or not.

This system should also be the framework which future sounds should be patterned after

Implementation Details:

The basics of the enemy sound system consist of AudioComponents (AC), which are an UE feature, and the EnemyAudioComponent (EAC), which we created to manage all the AudioComponents that live on the enemy.

> **Source image:** image2.png *(media file pending upload: `image2.png`)*

> **Source image:** image238.png *(media file pending upload: `image238.png`)*

As we can see here, the BP_Guard01 has both a patrolling sound (AC) and the EAC. In the enemy BeginPlay, it needs to connect that sound to the EAC. Here is an example of how that looks.

When other game objects want to interact with the enemy sound, they should do so through the EAC, it should control playing and stopping sounds as well as performing calculations which control details about the sound profile. Here is an example of how the patrol sound is started.

> **Source image:** image74.png *(media file pending upload: `image74.png`)*

One more important feature is the Attenuation Settings which is set on the AC for a given sound. You should create one Attenuation Setting Asset for similar sounds i.e. sounds that should have the same properties.

> **Source image:** image88.png *(media file pending upload: `image88.png`)*

> **Source image:** image364.png *(media file pending upload: `image364.png`)*

> **Source image:** image117.png *(media file pending upload: `image117.png`)*

THE WATCHER

## WatcherBase and WatcherControllerBase (C++):

### WatcherBase.h

*// Defines Watcher behavior. Unused*

bool SpinPatrol = false;

*// Time it takes in seconds to look at the next waypoint. Unused*

float DefaultInterpolationTime = 2.0f;

*// hidden variable set based on the waypoint multiplier and default interpolation time. Used in Animation Blueprint when turning to face something*

float InterpolationTime = 2.0f;

*//Used by State Tree to tell Animation blueprint when to turn the eye (True) and when it pauses (False). This has been commented out and can be removed*

*//UPROPERTY(BlueprintReadWrite, Category = "Patrol")*

*//bool TurningTowardsWaypoint = true;*

*// Sets Patrol Path through Waypoint actors with additional information*

TArray\<FWatcherWaypoint\> PatrolWaypoints;

*// I believe this is used to put a Waypoint at the player’s last known location. It starts at the Watcher’s own location.*

TSubclassOf\<AWaypointBase\> WaypointClassToSpawn;

*// Player’s last known location struct*

FWatcherWaypoint LastKnownLocationWaypointData;

*// Player’s last known location actor*

TObjectPtr\<AWaypointBase\> LastKnownLocationWaypoint;

protected:

*// Called when the game starts or when spawned*

virtual void BeginPlay() override;

*// Used by Animation Blueprint to determine animation state*

UWatcherStateComponent\* StateComponent;

### WatcherBase.cpp

Only thing it does is spawn the LastKnownLocationWaypoint at its own location at BeginPlay. This will be used later to mark the player’s location when they’re spotted.

*// Ensure the user assigned the Blueprint class in the Editor*

if (WaypointClassToSpawn)

{

FActorSpawnParameters SpawnParams;

SpawnParams.Owner = this;

SpawnParams.Instigator = GetInstigator();

*// Spawn the Blueprint instance, but store it as the C++ base type*

LastKnownLocationWaypoint = World-\>SpawnActor\<AWaypointBase\>(

WaypointClassToSpawn,

GetActorLocation(),

GetActorRotation(),

SpawnParams

);

}

### WatcherControllerBase.h 

(has nothing besides default functions)

### WatcherControllerBase.cpp

has only one thing besides defaults, it configures the perception component to be a Watcher perception component:

Perception = CreateDefaultSubobject\<UWatcherPerceptionComponent\>(

TEXT("EnemyPerception"));

### WatcherPerceptionComponent.h/.cpp: 

just a normal perception component class with no additions.

## Pawn and Controller (Blueprints):

### BP_Watcher

BP_Watcher only contains the high-level logic - the minutia of lerping its rotation happens in the Animation Blueprint.

## BP Reference Audit

### BP_Watcher_Controller Audit

In BP_Watcher:

> **Source image:** image309.png *(media file pending upload: `image309.png`)*

> **Source image:** image201.png *(media file pending upload: `image201.png`)*> **Source image:** image94.png *(media file pending upload: `image94.png`)*

> **Source image:** image144.png *(media file pending upload: `image144.png`)*

Fix: declare these event dispatchers in C++, then cast to WatcherControllerBase instead

### BP_Watcher Audit

In BP_Watcher_Trigger:

> **Source image:** image48.png *(media file pending upload: `image48.png`)*

Fix: move WatcherActivated function and Activated variable to C++, then change the Get to WatcherBase instead of BP_Watcher.

StateTree and Tasks:

STT_ChooseNextWaypoint

STT_Spin

STT_SetFocusOnWaypoint

STT_SetFocusOnPlayer

STT_ChangeWatcherStateMachine

Animation Blueprint:

**Level**

## **Level Design Statement**

The level layout should encourage fear while minimizing frustration. Everywhere the player goes, they should feel like an enemy always has the opportunity to sneak up behind them and scare them. The player should feel like they have agency in how they approach the game through the level. The flow of the level should be non-linear, but the player should rarely feel lost. Spaces in the level should always have multiple ways to evade an enemy to avoid the “screwed, but not dead” feeling, where players feel trapped but are not yet spotted. Ideally, the player will not even notice the level design because of how seamless it feels.

The player should always have options. The environment should be designed in such a way that the player can use either their position (crouching behind boxes, sneaking behind columns, etc.) or crevices (similar to the lockers from Alien: Isolation) to hide from enemies, and at certain points one or the other may be the only option available. Each room should make sense in the context of this being a sacred building, but good level design and player experience should come before logical layouts. The player should feel like they have gotten the idea of the full experience the game has to offer within the first two rooms they visit.

## **Level Design Pillars**

1.  **Support player agency through non-linear level progression:** The player should always feel like they have control of where they go next. There should not be a set path the player must take to complete the level. Most rooms should have more than one entrance/exit to facilitate player agency as well as give players more ways to evade enemies.

2.  **Enemy Omnipresence:** The player should always feel like an enemy could be around the next corner or right behind them. There should be a constant feeling of dread as the player makes their way through the level.

3.  **Balance crevice and positional stealth:** The environment should be laid out in such a way that the player has to use both positional stealth (crouching behind boxes, sneaking behind columns, etc.) as well as crevices in order to evade enemies. The level should skew more towards positional stealth than hiding in crevices, but both should be valid options.

4.  **Communicate direction clearly:** While supporting player agency is important, the player should rarely feel confused or lost while playing. They should be able to know where they are in relation to the level, and areas where they have not explored yet.

## **Table of Contents**

- [<u>Design Philosophy</u>](#design-philosophy)

- [<u>Activatables</u>](#activatables)

- [<u>Interactables</u>](#interactables)

- [<u>Waypoints</u>](#waypoints)

- [<u>Cutscenes</u>](#cutscenes)

## **<u>Design Philosophy</u>**

## **Overall Level Design Philosophy**

**Last Updated:** 10/26/2026

The level consists of one main, two story room with the other rooms and hallways branching off of that main hub. Everywhere the player goes they should feel like there could be enemies approaching from behind if they are not being watchful. The player should feel rewarded for going out of their way to explore. The environment should be designed in such a way throughout the whole map so that the player can use either their position (crouching behind boxes, sneaking behind columns, etc.) or crevices (similar to the lockers from Alien: Isolation) to hide from enemies, and at certain points one or the other may be the only option available.

The main room should be a hub the player has to pass through in order to get to the other, smaller rooms/hallways. It should be clear to the player where they are in the hub room in relation to the rooms they have already visited.

Each smaller room should be its own small, self contained sub-level. The player spawns in a room on the bottom floor. The rooms downstairs should be easier to complete than the rooms upstairs to help ease the players into the level. Currently each room should also contain a brazier, but that may change at a future date. The player should feel like they have gotten the idea of the full experience the game has to offer within the first two rooms they visit.

> **Source image:** image366.png *(media file pending upload: `image366.png`)*

> **Source image:** image140.png *(media file pending upload: `image140.png`)*

## **Intro/Spawn Sub-level**

**Last Updated:** 10/26/2026

**Design Philosophy:** The intro sub-level is currently where the player is first spawned into the game. It is located on the bottom floor. This room should introduce the player to the guards as well as teach them that they need to light the braziers to complete the level, lighting the braziers alerts the guards, and that you can hide from guards in a crack.

| **Intro Sub-level Breakdown**                              |                       |                                                                                                                                                      |                                                                                                                                                                                                                                                      |
|------------------------------------------------------------|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Level Element**                                          | **Help or Challenge** | **Explanation**                                                                                                                                      | **How it Supports the Philosophy**                                                                                                                                                                                                                   |
| Brazier right in front of the player when they first spawn | Help                  | It’s really easy to find and furthers the player’s progress.                                                                                         | By placing the brazier in a really obvious place right in front of the player when they spawn, they will be much more likely to interact with it and learn what it does.                                                                             |
| Top-right and Top-left Cracks                              | Help                  | It’s a place to hide from the guards near the brazier.                                                                                               | By placing these cracks really close to the brazier, we’re able to teach and encourage the player to hide once they light the brazier and alert a guard.                                                                                             |
| Bottom-left Crack                                          | Help                  | It’s a place to hide from the guards further into the room.                                                                                          | This supports the overall design philosophy of avoiding the player feeling trapped. This is another place the player can choose to hide if they try to walk back into the room to get away from the incoming guard summoned by lighting the brazier. |
| Two Exits                                                  | Help                  | If the enemy is approaching one exit, the player can use the other exit to escape. It also prevents the watcher from looking straight into the room. | Supports the overall design philosophy of avoiding the player feeling trapped. They always have another option they can use to get where they want to go.                                                                                            |

> **Source image:** image98.png *(media file pending upload: `image98.png`)*

> **Source image:** image192.png *(media file pending upload: `image192.png`)*

## **Cloister Sub-level**

**Last Updated:** 10/27/2026

**Design Philosophy:** This should be the next sub-level the player will enter after the intro sub-level. It is also located on the bottom floor. It should be a little harder, but not to the same extent as the upstairs rooms. The player should learn how to hide using positional stealth (behind boxes, pillars, etc.), how to use the distraction, and that the guards are roaming around the map.

| **Cloister Sub-level Breakdown**                         |                       |                                                                                                                              |                                                                                                                                                                                                                                                                         |
|----------------------------------------------------------|-----------------------|------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Level Element**                                        | **Help or Challenge** | **Explanation**                                                                                                              | **How it Supports the Philosophy**                                                                                                                                                                                                                                      |
| Brazier in the middle of the room                        | Both                  | It’s easy to see when you walk in the room, but it’s unclear about how you can get there until you start exploring the room. | It makes the sub-level harder than the intro sub-level while not being quite as difficult as the upstairs rooms.                                                                                                                                                        |
| Positional Stealth Objects Scattered Throughout the Room | Help                  | It’s a place to hide from the guards when traversing the room.                                                               | By placing these positional stealth objects throughout the room with only one crack, the player is forced to use them to hide from enemies and learn that is an option available to them.                                                                               |
| Far-right Crack                                          | Help                  | It’s a place to hide from the guards with a direct shot from the brazier.                                                    | By placing this at the back of the room, the player naturally goes there to hide once the brazier is lit. The player then has to make their way all the way back through the room to get to the exit, being forced to use the positional cover if an enemy comes close. |
| Pillars/Arches                                           | Both                  | A way to break line of sight with the guards, but also can obstruct the way forward.                                         | It is a way to make the room harder without making it impossible to see the brazier in the center of the room.                                                                                                                                                          |
| Railings                                                 | Challenge             | It prevents the player from walking straight to the brazier when they spot it, forcing them to find the stairs down.         | It makes the room harder than the intro sub-level by forcing the player to explore for the way down while still allowing them to see their end goal.                                                                                                                    |
| Two Exits                                                | Help                  | If the enemy is approaching one exit, the player can use the other exit to escape.                                           | Supports the overall design philosophy of avoiding the player feeling trapped. They always have another option they can use to get where they want to go.                                                                                                               |

> **Source image:** image119.png *(media file pending upload: `image119.png`)*

> **Source image:** image192.png *(media file pending upload: `image192.png`)*

## **Horseshoe Sub-level**

**Last Updated:** 10/27/2026

**Design Philosophy:** The horseshoe sub-level is located on the upper level, meaning it should be more difficult to complete than the bottom floor sub-levels. The player should be given different options to traverse the sub-level, but also be forced to explore the space and go to areas they might not have typically explored.

| **Horseshoe Sub-level Breakdown**                        |                       |                                                                                                                                                             |                                                                                                                                                                                                                                                                                                                            |
|----------------------------------------------------------|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Level Element**                                        | **Help or Challenge** | **Explanation**                                                                                                                                             | **How it Supports the Philosophy**                                                                                                                                                                                                                                                                                         |
| Brazier in the Central “Spoke” Area                      | Challenge             | It’s hard to find, as it’s tucked into the corner of the room. It’s also located in the central room that is exposed to the watcher through a window.       | This location makes this sub-level harder than the bottom floor, while presenting an interesting challenge the player hasn’t seen before.                                                                                                                                                                                  |
| Window in the Central “Spoke” Area                       | Challenge             | Allows the watcher to see into the room, providing another challenge the player has to deal with.                                                           | This detail adds another level of complexity to the sub-level, and makes the watcher, and by extension the guards, feel more omnipresent.                                                                                                                                                                                  |
| Closing Doors                                            | Challenge             | When the player first enters the central “spoke” area, the first corridor they walk through unexpectedly closes behind them so they can’t go back that way. | It forces the player to have to use the other two corridors branching off the central area, meaning they have to explore areas they might not have otherwise. It also makes a loud noise when it falls, spooking the player and reminding them that unexpected things can happen and that they need to stay on their toes. |
| Save Statue                                              | Help                  | Allows the player to save their progress.                                                                                                                   | Giving the player a place to save allows them                                                                                                                                                                                                                                                                              |
| Top-right Crack                                          | Help                  | It’s a place to hide from the guards if the player is in the hallway.                                                                                       | This supports the overall design philosophy of avoiding the player feeling trapped. This is another place the player can choose to hide if they decide to leave using the back corridor.                                                                                                                                   |
| Positional Stealth Objects Scattered Throughout the Room | Help                  | It’s a place to hide from the guards when traversing the room.                                                                                              | By placing these positional stealth objects throughout the room with only one crack, the player is more likely to need to use them and not rely solely on the cracks to hide.                                                                                                                                              |
| Two Exits                                                | Help                  | If the enemy is approaching one exit, the player can use the other exit to escape. It also prevents the watcher from looking straight into the room.        | Supports the overall design philosophy of avoiding the player feeling trapped. They always have another option they can use to get where they want to go.                                                                                                                                                                  |

> **Source image:** image174.png *(media file pending upload: `image174.png`)*

> **Source image:** image333.png *(media file pending upload: `image333.png`)*

## **Switch Sub-level**

**Last Updated:** 10/27/2026

**Design Philosophy:** The switch sub-level is located on the upper level, meaning it should be more difficult to complete than the bottom floor sub-levels. The player should have to spend some time in this sub-level looking around for the brazier, giving them more opportunities to have tense interactions with the guards.

| **Switch Sub-level Breakdown**      |                       |                                                                                                                                                      |                                                                                                                                                                                                                                                      |
|-------------------------------------|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Level Element**                   | **Help or Challenge** | **Explanation**                                                                                                                                      | **How it Supports the Philosophy**                                                                                                                                                                                                                   |
| Brazier Hidden in the Top-left Room | Challenge             | It’s hard to find and requires the player to explore the space.                                                                                      | The player has to look around the space to find the brazier, requiring them to explore and rewarding them when they do find it.                                                                                                                      |
| Four Separate Rooms                 | Challenge             | Nothing is                                                                                                                                           |                                                                                                                                                                                                                                                      |
| Top-right and Top-left Cracks       | Help                  | It’s a place to hide from the guards near the brazier.                                                                                               | By placing these cracks really close to the brazier, we’re able to teach and encourage the player to hide once they light the brazier and alert a guard.                                                                                             |
| Bottom-left Crack                   | Help                  | It’s a place to hide from the guards further into the room.                                                                                          | This supports the overall design philosophy of avoiding the player feeling trapped. This is another place the player can choose to hide if they try to walk back into the room to get away from the incoming guard summoned by lighting the brazier. |
| Two Exits                           | Help                  | If the enemy is approaching one exit, the player can use the other exit to escape. It also prevents the watcher from looking straight into the room. | Supports the overall design philosophy of avoiding the player feeling trapped. They always have another option they can use to get where they want to go.                                                                                            |

## **<u>Interactables</u>**

**Last Updated:** 10/26/26

### **Design**

**Design Statement:** Interactables are actors which the player interacts with to cause an effect. Interactables invite the player to interact with them when nearby, and have a direct and immediate effect upon the game.

**Interactions with Other Elements**

**Player:** Checks for overlaps with the player and prompts them to “interact with F”

**Game Instance:** Some Interactables communicate interactions with the Game Instance

using a Persistent Interactable Component.

### **Code Overview** 

**Variables**

**public**

- Activatables: TArray\<ActivatableBase\> — array of activatables that activate during interaction

- AHighlightableMeshes: TArray\<UStaticMeshComponent\*\> — array of materials to use when highlighted

- Toggleable: boolean — whether the interactable can be turned off.

**Functions**

- void SetHighlightMaterial — used to make the interact prompt appear and disappear as needed.

- OnInteract — function declaration for subclasses to implement. By default, it turns it on if off, and if on checks if it can be turned off, and if so turns it off. It then sets all activatables associated with it to its current activation.

> **Source image:** image123.png *(media file pending upload: `image123.png`)*

## **BP_Brazier**

> **Source image:** image219.png *(media file pending upload: `image219.png`)*


### **Design**

**Design Statement:** The Brazier is an intractable part of the level that the player must activate to progress toward the final objective. Interaction with it brings the player into a minigame where they must turn the wheel to open the brazier, during which the player cannot move and can see very little. Activating the brazier calls the enemies, and progresses you toward the goal.

### **Interactions with Other Elements** 

**Player:** Upon overlap with the player, it invites players to interact with it. Upon interaction, it can do one of four things:

- If destroyed, it restores some of the player’s light

- if completed, it restores all the players light

- if not completed and not active, it takes away player control, moves the camera, and hides the player.

- if not completed but active, it gives back player control, restores the camera, and reveals the player.

**Game Instance:** Upon interaction, it can call several possible GI_Lantern events

- If destroyed, it calls Broken Brazier Interact

- if completed, it calls SetLight

- if not completed and active, it calls ExitBrazier

With the event OnActivate, it calls AddBrazier, passing in its own ID as an argument, and adds itself to ActivatedInteractables.

**Code Overview**

> **Source image:** image356.png *(media file pending upload: `image356.png`)*

resets the brazier without pinging the guards.

**OnInteract  
**<u>if destroyed</u>> **Source image:** image299.png *(media file pending upload: `image299.png`)*restore some light.

<u>if completed</u>> **Source image:** image345.png *(media file pending upload: `image345.png`)*restore light. Do this only once.

<u>if not completed, and is active</u> > **Source image:** image109.png *(media file pending upload: `image109.png`)*free the camera and update materials. Set active so this will not happen again.> **Source image:** image371.png *(media file pending upload: `image371.png`)*remove the controls for the brazier opening mini game. Make the player visible again.

> **Source image:** image106.png *(media file pending upload: `image106.png`)*update the Game Instance so it doesn’t display the minigame UI anymore. Trigger cutscene.

<u>If not completed or active:</u>

> **Source image:** image91.png *(media file pending upload: `image91.png`)*enter fixed camera. Remove usual player controls and activate minigame controls.> **Source image:** image193.png *(media file pending upload: `image193.png`)*hide the player. Assign new materials and alert the GI to begin displaying the minigame UI.

**Event Tick**: Relevant only during the minigame. Updates the position of the top of the brazier and play the sounds of opening the brazier. If the minigame is complete, it tells the GI to lock this brazier.

**RotateWheel:** Performs the math to detect mouse rotations, and update the position of the visible ship’s wheel.

**Activate**> **Source image:** image217.png *(media file pending upload: `image217.png`)*Pings enemies, activates activatables associated with it, tells the GI to update its status.

## **BP_Crack_I**

> **Source image:** image87.png *(media file pending upload: `image87.png`)*


### **Design**

**Design Statement:** The crack blueprint is an interactable piece of the level that allows the player to hide from enemies. It is also the only place a quick time event can trigger, which happens when a guard decides to investigate the crack that the player is currently hiding in. It involves high stakes, since it either protects the player perfectly or kills them instantly (if they fail the QTE).

### **Interactions with Other Elements** 

**Player:** Checks for overlaps with the player and sets their location when they enter or exit the crack.

**Game Instance:** Notifies the game instance when the player enters the range and when they enter/exit the crack

### **Code Overview** 

**Variables**

- InCrack: bool — whether or not the player is in the crack

- Player: BP_Player — a reference to the player blueprint

- PlayerLocation: Vector — a variable that gets set when the player enters the crack but is not called anywhere else; probably deprecated

- ArmStart: Vector — (ARM) start location of arm lerp

- Midpoint: Vector — (ARM) midpoint of arm lerp for bezier curve

- ArmEnd: Vector — (ARM) endpoint of arm lerp

- TargetRot: Rotator — (ARM) target rotation of arm lerp

- StartRot: Rotator — (ARM) starting rotation of arm lerp

- ArmLerpCounter: int — (ARM) tracks which stage of animation arm is on

- Dodge1Direction: E_QTEDodgeDirections — (ARM) first dodge direction of QTE

- Dodge2Direction: E_QTEDodgeDirections — (ARM) second dodge direction of QTE

- CurveLerp: bool — (ARM) whether or not an arm lerp should use a bezier curve

## **BP_SaveStatue**

> **Source image:** image89.png *(media file pending upload: `image89.png`)*

### **Design**

**Design Statement:** The SaveStatue is an intractable part of the level that allows the player to save their progress. It moves the player spawn point to itself, and saves the status of persistent interactables and activatables. After interacting with a save statue, all saved states are restored by the Game Instance upon game reset.

### **Interactions with Other Elements** 

**Player:** Upon overlap with player, it invites players to interact with it.

**Game Instance:** Upon interaction it calls the save() function.

### **Code Overview**

> **Source image:** image368.png *(media file pending upload: `image368.png`)*

call save.

## **BP_Switch_I**

> **Source image:** image115.png *(media file pending upload: `image115.png`)*

**Design Statement:** this is an easily readable actor to be placed in world to allow the player to activate other actors.

**Interactions with Other Elements**

**Player:** Upon overlap with player, it invites players to interact with it. Upon interaction, it activates all activatable items associated with it.

**Game Instance:** Upon activation, it adds itself to the set of ActivatedInteractables.

## **<u>Activatables</u>**

**Last Updated:** 10/26/26

### **Design**

**Design Statement:** Activatables are actors within the game which perform a specific action when triggered by their OnActivate event. Activations are typically triggered by player actions, often involving Interactables.


## **BP_Door_Braziers**

**Design Statement:** The final door which is opened when the player has completed all their objectives. When the player goes through this door, they win

**Interactions with Other Elements**

**Player:** saves a reference to the player on BeginPlay. Takes the camera to show the door when OnActivate is called the first and last time, and disables the controls at those times as well.

**Game Instance:** accesses the GI to play sounds and begin cutscenes.

### **Code Overview**

<u>OnActivate</u>

- First: increment number of activated braziers. Open the door if they are all activated.

- Second: save a reference to the player (used for coming cutscenes)

- Third: play the “Legend of Zelda found a Secret Thing” sound.

- Fourth: if it’s the first brazier you opened, show them the door, and that a lock has opened.

- Fifth: if it’s the last brazier that needs to be opened, show them the door and that it’s opened.

## **BP_Torch_Manager**

**Design Statement:** the Torch Manager is an actor placed to reduce clutter in the BP_Brazier’s list of activatables. When activated, it activates the BP_IndicatorTorches in its array Torches.

**Interactions with Other Elements**

**BP_Indicator_Torches:** can generate and activate torches.

### **Code Overview**

**Variables**

Torches: Array\<BP_Indicator_Torches\> -- Array of torches.

**Functions**

OnActivate> **Source image:** image285.png *(media file pending upload: `image285.png`)*activates the torches.

AddTorch> **Source image:** image11.png *(media file pending upload: `image11.png`)*spawns a new torch and adds it to its array of Torches

DestroyTorches

> **Source image:** image225.png *(media file pending upload: `image225.png`)*deletes all torches in its array, then itself.

## **BP_Indicator_Torches**

> **Source image:** image131.png *(media file pending upload: `image131.png`)*

**Design Statement:** An interactable which indicates to the player when there is something to complete in an area. Emits colored light to attract attention to important areas and indicate completion of tasks.

**Interactions with Other Elements**

**Interactable:** Will never be activated unless told to do so by an interactable

### **Code Overview**

**Variables**

FlameMaterial: a Material instance reference, intended to hold an instance of M_EmissiveIndicatorTorch

**Functions**

OnActivate

> **Source image:** image26.png *(media file pending upload: `image26.png`)*sets the color of FlameMaterial to the preset golden light.

BeginPlay> **Source image:** image266.png *(media file pending upload: `image266.png`)*Creates a new material instance and assigns it to FlameMaterial, then assigns it to the sphere at the top.

## **BP_DoorLights**

> **Source image:** image143.png *(media file pending upload: `image143.png`)*

**Design Statement:** a light source placed to illuminate and draw attention to important items in the level, and change color to indicate completion of the area.

**Interactions with Other Elements**

**Interactable:** Requires an interactable to call OnActivate

### **Code Overview**

OnActivate: > **Source image:** image150.png *(media file pending upload: `image150.png`)*sets the color of the spot light to the preset golden light.

## **BP_Trigger**

> **Source image:** image275.png *(media file pending upload: `image275.png`)*

**Design Statement:** An invisible object which activates other Activatables upon overlap with the player.

**Interactions with Other Elements**

**Player:** Overlap with the player triggers OnActivate.

**Game Instance:** Some triggers communicate their activation state to the GI through the Persistent Interactable Component.

### **Code Overview**

**Variables**

TriggeredItems: Array\<Actor\> -- array of Interactables and Activatables to be triggered.

Deactivatable: boolean -- whether it should be able to be turned off

ReactivateOnReset: boolean -- whether the triggered events need to be reactivated every game reset

**Functions**

BeginOverlap> **Source image:** image69.png *(media file pending upload: `image69.png`)*when overlapping a player, it checks its own activation status, then if not activated, calls OnActivate on itself. If it is activated and can be deactivated, it deactivates itself.

OnActivate> **Source image:** image83.png *(media file pending upload: `image83.png`)*

Tell the PersistentInteractable component to inform GI of activation, then for every item in TriggeredItems either activate or Interact with it.

## **BP_Door_Trigger**

> **Source image:** image269.png *(media file pending upload: `image269.png`)*

**Design Statement:** An actor which slams a door behind the player the first time they interact with it. The fallen door is a persistent actor which is saved with the SaveStatue.

**Interactions with Other Elements**

**Player:** When overlapping the player, it drops the door behind them.

**Game Instance:** When triggered, it adds itself and the proper door to ActivatedInteractables.

### **Code Overview**

Important note, this is neither an interactable or activatable actor. Its use case was a bit jank, and thus implements similar but distinctly different logic and cannot inherit.

**Variables**

AlreadyTriggered: Boolean -- set to true when first interacted with.

BoxTriggered: -- sets to whichever of the three possible doors is the closed one.

**Functions**

OnComponentBeginOverlap> **Source image:** image226.png *(media file pending upload: `image226.png`)*

There are three versions of this which all do the same thing, targeting different boxes and triggering a different door.

If the overlapping actor is the player, then check if we are already triggered. If not, set AlreadyTriggered to true and play the door falling noise, and set the location of the blocking door to the fallen position. Add yourself and the proper door to the ActivatedInteractables set in GI.

BeginPlay: For each possible door, check if its name is inside the GI’s set of SavedInteractables. If it’s found, set the door to the correct place, set AlreadyTriggered to true, and stop looking.

## **BP_Lock_A**

> **Source image:** image313.png *(media file pending upload: `image313.png`)*

### **Design**

**Design Statement:** The lock’s main design is to give the player a visual sense of progression as they progress the level and unlock the main door brazier by brazier

### **Interactions with Other Elements** 

**BP_Door_Braziers:** During the first lock, the lock is unlocked by the door instead of the brazier for cinematic effect. For more information look at the Brazier to Door cutscene

**BP_Brazier:** After the first lock the brazier activates the lock

### **Code Overview**

> **Source image:** image292.png *(media file pending upload: `image292.png`)*

When the lock is activated we are going to move the upper part of the lock up and turn it green.

## **BP_Door_Camera_Track**

### **Design**

**Design Statement:** A track the camera follows during the Brazier Door Cutscene, mostly made as a separate object because it would move too much if we modified the door at all and it was easier to have a separate object to plug in

NOTE: Just put the spline in world space ya goob

### **Interactions with Other Elements/Code Overview**

Please see Brazier Door Cutscene

## **BP_Watcher_Trigger**

### **Design**

**Design Statement:** BP_Watcher_Trigger serves two design goals:

1.  Introducing the Watcher. The first time the player triggers it, a short cutscene shows them the Watcher, so they know it exists and is dangerous.

2.  Activating the Watcher in a limited state. At first the Watcher can only look at the second floor, so it isn’t a real threat yet. It becomes one once the player enters the cloister room, after which it starts looking down at the first floor.

### **Interactions with Other Elements** 

| **ActivatableBase**                 | Provides the OnActivate event this Blueprint overrides.                                                                                     |
|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **BP_Trigger**                      | Parent class. OnActivate calls the parent implementation first.                                                                             |
| **BP_Watcher**                      | Every Watcher in the level is found with Get All Actors Of Class. Each gets Watcher Activated called on it and has its Activated bool read. |
| **WaypointBase**                    | This trigger’s ActivatedWaypoints array is passed to each Watcher.                                                                          |
| **GI_Lantern (Game Instance)**      | Provides NoCutscenesMode (dev skip), HasSeenWatcher (play-once flag), and SeeWatcher() (sets that flag).                                    |
| **BP_PlayerCameraManager**          | Provides enter fixed camera(arrow, lerp on) and exit fixed camera(lerp on).                                                                 |
| **Arrow (component on this actor)** | The camera’s target transform for the cutscene. Place and rotate it in the level to frame the shot.                                         |

### **Code Overview**

**BP_Watcher_Trigger (OnActivate):**> **Source image:** image40.png *(media file pending upload: `image40.png`)*

1.  Call the parent OnActivate (BP_Trigger, which calls it when a player overlaps with the Box Collision).

2.  Get All Actors Of Class (BP_Watcher, there should be only one), then run a **ForEachLoop** over the results.

3.  For each Watcher, call Watcher Activated(ActivatedWaypoints), then branch on that Watcher’s Activated bool:

    1.  **True:** do nothing.

    2.  **False:** continue to the cutscene checks below.

> **Source image:** image122.png *(media file pending upload: `image122.png`)*

4.  Cast the Game Instance to GI_Lantern.

5.  If NoCutscenesMode is true, print a dev-only message (“Dev Tools: Skipped Watcher Startup”) and stop.

6.  If HasSeenWatcher is true, stop.

7.  Otherwise, play the cutscene:

    1.  Cast the Player Camera Manager to BP_PlayerCameraManager.

    2.  enter fixed camera using this actor’s Arrow, with lerp on.

    3.  Delay 0.4s.

> **Source image:** image262.png *(media file pending upload: `image262.png`)*

4.  GI_Lantern.SeeWatcher(), which sets HasSeenWatcher.

5.  Delay 3.0s.

6.  exit fixed camera, with lerp on.

## **BP_Trigger_Cloister**

### **Design**

**Design Statement:** The cloister trigger is an invisible field in the cloister that triggers a scripted event with a guard and the distraction tutorial. The level is designed such that the majority of players will trigger it towards the beginning of their experience.

### **Interactions with Other Elements** 

**Player:** The player is frozen in place upon triggering the event. They have to watch a brief cutscene of the guard approaching, and then are given a prompt to throw a distraction. Once they have done that, they are given full control back.

**Game Instance:** When the player passes through the object, it checks with the game instance to see whether or not the cutscene/tutorial has already played. If it hasn’t, the game instance ensures all other requirements are met and then triggers the cutscene.

**Waypoint Manager:** The blueprint calls the CloisterEvent function in the waypoint manager to tell it to warp a guard into position.

### **Code Overview**

**Variables**

- GuardTeleportLocation: WaypointBase — the waypoint to warp a guard to

**OnActivate:** The only event or function in the blueprint. Called when the player enters the field. Checks with the game instance to see whether or not the event should be played.

> **Source image:** image114.png *(media file pending upload: `image114.png`)*

**BeginPlay:** Sets the Player variable and hides the guardarm component.

> **Source image:** image114.png *(media file pending upload: `image114.png`)*

**ActorBeginOverlap:** Checks whether the player is in range and notifies Game Instance if so.

> **Source image:** image37.png *(media file pending upload: `image37.png`)*

**OnInteract:** Called when the player interacts with the crack. Moves the player and camera accordingly then notifies the Game Instance.

> **Source image:** image3.png *(media file pending upload: `image3.png`)*

**Arm Lerp:** A bunch of nonsense that simulates an animation using the guardarm component, used for the QTE. Do not touch this unless you are replacing it with an actual animation in which case please touch this.

> **Source image:** image13.png *(media file pending upload: `image13.png`)*

**StartQTE:** Sets the two dodge directions and begins the first arm lerp. Will be deprecated once the arm lerp is replaced by an animation.

> **Source image:** image247.png *(media file pending upload: `image247.png`)*

**GetGrabPoints:** Returns the necessary locations and rotations for the arm lerps depending on the dodge direction. Will be deprecated once the arm lerp is replaced by an animation.

> **Source image:** image372.png *(media file pending upload: `image372.png`)*

**Arm Lerp Timelines/Events:** A bunch of nonsense that simulates an animation using the guardarm component, used for the QTE. Do not touch this unless you are replacing it with an actual animation in which case please touch this.

> **Source image:** image13.png *(media file pending upload: `image13.png`)*

## **<u>Waypoints</u>**

## **<u>Cutscenes</u>**

### **Design**

**Design Statement:**

**Abstraction:** A tool used to help introduce the player to key objectives, enemies and abilities

The cutscenes are meant to help introduce the player to important components and rules of the game. Overall the cutscenes are supposed to be obtrusive enough to inform the player without causing large amounts of frustration

## **Brazier to Door**

> **Source image:** image136.gif *(media file pending upload: `image136.gif`)*


### **Design**

**Design Statement:**

**Abstraction:** A tool to introduce the player to the connection between the sub-objectives and the main objective.

The brazier to door cutscene is meant to show the player the direct connection from the brazier to the door, giving them an understanding of how the brazier sub-objective links to the main objective which is the door.

### **Interactions with Other Elements** 

**Door:** The cutscene originates from the door (BP_Door_Braziers_A) and uses a spline component for the camera track.

**Camera Manager:** It uses the enter fixed camera function to continually move along the spline.

**BP_Lock:** It takes the first lock away from the brazier and puts it on the door as an activatable. It waits until the camera gets to the end of the spline track to unlock the lock.

### **Code Overview** 

> **Source image:** image234.png *(media file pending upload: `image234.png`)*

When the first brazier is lit, we call **Lerp To Door** and pass in **BP_Player_Manager** as a variable to drive the custom cutscene. We then set the play rate of the **DoorLerpTimeline** component to 0.5 to get the speed we want, and run the timeline.

On each update, we take the **Door Camera Track** variable (a simple spline) and multiply the timeline’s progress by the spline’s length to get a distance along it. We use that distance to get a location on the spline, then move the camera arrow component to that point. Each update also calls **Enter Fixed Camera** with **Lerp On** enabled for a smooth transition.

When the timeline finishes, we delay for half a second, open the first lock, and play the lock-open sound.

**TODO:**

- Replace the 0.5 play rate with an exposed variable (e.g., DoorLerpPlayRate) instead of a magic number.

- Find a better approach than calling Enter Fixed Camera on every update. Ideally, we’d call it once before the timeline starts and have the timeline only move the camera arrow component.

## **Watcher Introduction**

> **Source image:** image273.gif *(media file pending upload: `image273.gif`)*


### **Design**

**Design Statement:**

**Abstraction:** A tool to introduce the player to one of the main enemies

The watcher cutscene is meant to introduce the player to the watcher, it teaches the player it’s not just an environmental thing but an enemy and something to be feared

### **Interactions with Other Elements** 

**BP_Trigger_Watcher:** The watcher trigger checks if the player overlaps it, takes the players camera and powers up the watcher

**Watcher:** BP_Trigger_Watcher turns on the watcher and then gives it valid waypoints it can look at

**Camera Manager:** It uses the enter fixed camera function to pull the players attention to the watcher

### **Code Overview**

For Code Overviews Look at BP_Trigger_Watcher and Watcher Documentation

## **Distraction Tutorial**

> **Source image:** image289.gif *(media file pending upload: `image289.gif`)*


### **Design**

**Design Statement:**

**Abstraction:** A tool to introduce the player on how to use one of the main abilities

The distraction tutorial is to help the player become acquainted with how the distraction works so they can use it later in the level.

### **Interactions with Other Elements/Code Overview** 

For code overview and interactions with other elements look at BP_Trigger_Cloister

## **<u>LightPing</u>**

### **Design**

**Design Statement:**

**Abstraction:** Light Ping is used to indicate to the player that the guards in the vicinity will be going to that location. It is a light that spreads out to visually show a big effect. Light Ping is used in both distraction and the braziers to signify that the guards are notified.

**Interaction with other elements:**

- **Environment:** The light from the ping starts from the center, and expands into a large dome that fills in the whole room.

- **Distract:** When a distraction lands on the ground, the light sphere expands from the distraction’s point of impact

- **Braizer:** Light Ping activates after turning the wheel and the soul lighting it.

### **Code Overview** 

Event BeginPlay

> **Source image:** image79.png *(media file pending upload: `image79.png`)*

In event beginplay, it creates a dynamic material instance, which lets us change the material in real time.

> **Source image:** image325.png *(media file pending upload: `image325.png`)*

When SpawnPing is called within the BP_LightProjectile, it sets the visibility of the sphere, plays the gong sound, and then sets the activate boolean to True. This allows the logic for the ontick to start.

> **Source image:** image99.png *(media file pending upload: `image99.png`)*

If activated is True, in event tic, it will continuously decrease the Aurora opacity for the material. It will also continuously increase the world scale of the object.

It will stop activated once the actor is destroyed in spawn ping after the 10 second delay.


## **<u>Elements</u>**

**Game**

## **Game Instance (GI_Lantern)**

**Last Updated:** 10/20/26

###  **Design**

**Design Statement:** The game instance is the only piece of the game that persists across level changes and deaths. It loads when the application is launched and its status will update continuously until the application is closed. Therefore, it contains all variables that should not be reset when the player dies.

### **Interactions with Other Elements** 

The game instance acts as the presenter in the Model-View-Presenter pattern with the HUD (view) and the game objects (model). It therefore communicates with both sides, generally by receiving event triggers from the objects and calling the appropriate logic in HUD_Main through BPI_HUD.

### **Code Overview**

**Variables**

- SpawnPointLocation: Vector — the location at which the player spawns either on start or after dying

- SpawnPointRotation: Rotator — the rotation at which the player spawns either on start or after dying

- BraziersLit: array\[int\] — a list of the IDs of the braziers that have been lit

- ResetBool: bool — HELP

- HUD: HUD_Main — a reference to the HUD

- Guards: Set\[Actor\] — a set of all guards in the level

- TotalBraziers: int — the number of total braziers in the level

- QTEActive: bool — whether or not the quick time event is currently active

- ToolTips: Map\[E_ToolTipKeys, String\] — a dictionary that maps each tooltip key to its corresponding tip text

- RecordingTestInfo: bool — HELP

- TestSlotName: String — HELP

- TestSave: Object — HELP

- QTEDodge1: E_QTEDodgeDirections — the first dodge direction, set each time a quick time event is triggered

- QTEDodge2: E_QTEDodgeDirections — the second dodge direction, set each time a quick time event is triggered

- QTEDirectionKeyMap: Map\[E_QTEDodgeDirections, String\] — constant, {down: “S”, right: “D”, left: “A”}

- TestEvents: bool — HELP

- FirstCrack: bool — true until the player exits a crack for the first time

- QTEEnabled: bool — boolean that prevents the QTE from triggering on the first encounter in the crack

- WaitingForInvisiblity: bool — whether or not the invisibility tutorial is active and the game is waiting for the player to press SPACE

- HasSuggestedInvisibility: bool — whether or not the invisibility tutorial has already been given

- MapDebug: BP_MapDebug — Reference to a MapDebug object that allows the game instance to have access to functions for recording debug information.

- IsRecordDebug: bool — Whether or not the debug recording tool is active. Set to true by default. That being said, the recording tool doesn't actually record unless the proper save file is checked out.

- UsedDialogue: Set\[String\] — set of the dialogue lines that have already been displayed

- HasSeenWatcher: bool — whether or not the watcher cutscene has been triggered

- HasSuggestedDistraction: bool — whether or not the distraction tutorial has already been given

- WaitingForAim: bool — whether or not the distraction tutorial is active and the game is waiting for the player to hold left click

- WaitingForRelease: bool — whether or not the distraction tutorial is active and the game is waiting for the player to release left click

- NoCutscenesMode: bool — dev tool to prevent cutscenes from triggering

- InfiniteLightMode: bool — dev tool to grant infinite light

- ActivatedInteractables: Set\[String\] — set of all interactables that have been activated since the last save

- SavedInteractables: Set\[String\] — set of all interactables that have been activated and saved

- SaveStatueInteractedWith: bool — whether or not a save statue has

**Brazier Events**

AddBrazier(int brazierID): Called each time a brazier is lit. Adds the ID to BraziersLit and calls FirstBrazierLit if necessary.

> **Source image:** image124.png *(media file pending upload: `image124.png`)*

ExitBrazier(bool locked): Called when the player exits a brazier. The locked parameter is true if they finished opening that brazier.

> **Source image:** image18.png *(media file pending upload: `image18.png`)*

EnterBrazier(): Called when the player interacts with an unopened brazier. Displays the rotate mouse prompt.

> **Source image:** image360.png *(media file pending upload: `image360.png`)*

LockBrazier(): Called when the player finishes opening a brazier. Hides the rotate mouse prompt and displays the “Exit” prompt.> **Source image:** image101.png *(media file pending upload: `image101.png`)*

BrokenBrazierInteract(): Not currently in use but does get called when the player interacts with a broken brazier.

> **Source image:** image261.png *(media file pending upload: `image261.png`)*

**Player Events**

RechargeLight(float percent): Sets the player’s light amount to the input percent.

> **Source image:** image341.png *(media file pending upload: `image341.png`)*

PlayerBeginPlay(): Called when the player spawns/respawns. Sets the distraction ammo and abilities to be visible.

> **Source image:** image271.png *(media file pending upload: `image271.png`)*

BeginInteractOverlap(): Called when the player enters the range of an interactable. Displays an action prompt based on the subclass of that interactable.

> **Source image:** image245.png *(media file pending upload: `image245.png`)*

EndInteractOverlap(): Called when a player exits the range of an interactable. Hides the action prompt.> **Source image:** image17.png *(media file pending upload: `image17.png`)*

**Game Events**

PauseGame(): Called when the player presses Esc or Tab. Freezes the game and displays the pause menu.

> **Source image:** image361.png *(media file pending upload: `image361.png`)*

UnpauseGame(): Unfreezes the game and hides the pause menu.

> **Source image:** image85.png *(media file pending upload: `image85.png`)*

TogglePause(): Pauses game if unpaused. Unpauses game if paused.

> **Source image:** image29.png *(media file pending upload: `image29.png`)*

ReturnToMainMenu(): Opens the main menu level and resets the game.> **Source image:** image30.png *(media file pending upload: `image30.png`)*

BeginPlay(): Called from the built-in BeginPlay function in GM_Lantern since a game instance doesn’t have its own. Sets up the level.> **Source image:** image5.png *(media file pending upload: `image5.png`)*

ResetGame(): Called each time the player dies. Sets their spawn location/rotation and handles the braziers according to the last save point.> **Source image:** image45.png *(media file pending upload: `image45.png`)*

InitializePlayerStart(): Moves the player start actor according to SpawnPointLocation and SpawnPointRotation.> **Source image:** image108.png *(media file pending upload: `image108.png`)*

SetBrazierUI(): Sets the Braziers Lit Widget based on TotalBraziers and the length of BraziersLit.> **Source image:** image354.png *(media file pending upload: `image354.png`)*

SetGuards(): Finds all guards in the level and adds them to the Guards set.> **Source image:** image142.png *(media file pending upload: `image142.png`)*

AddTestEvent(E_TestType newEventTestType): HELP

> **Source image:** image32.png *(media file pending upload: `image32.png`)*

**Crack Events**

EnterCrack(): Called whenever the player enters a crack.

> **Source image:** image284.png *(media file pending upload: `image284.png`)*

ExitCrack(): Called whenever the player exits a crack.

> **Source image:** image302.png *(media file pending upload: `image302.png`)*

**Story Events**

DisplayDialogueLine(String text, float time, E_Characters speaker, bool forceDisplay): Displays a line of dialogue and adds it to the UsedDialogue set. If forceDisplay is true, it will display even if already in UsedDialogue.

> **Source image:** image274.png *(media file pending upload: `image274.png`)*

DisplayTip(E_ToolTipKeys tipKeyword, float displayTime, String alignment, bool removeTip): Displays the input tool tip and removes it from the ToolTips map if removeTip is true.

> **Source image:** image340.png *(media file pending upload: `image340.png`)*

Spawn(): Called when the player first spawns.

> **Source image:** image250.png *(media file pending upload: `image250.png`)*

FirstBrazierLit(): Called after the player lights a brazier for the first time.> **Source image:** image241.png *(media file pending upload: `image241.png`)*

FirstCrackUsed(): Called the first time a player enters a crack.> **Source image:** image191.png *(media file pending upload: `image191.png`)*

FirstCrackSuccessful(): Called after a guard investigates a crevice containing the player for the first time.> **Source image:** image95.png *(media file pending upload: `image95.png`)*

SeeWatcher(): Called the first time the player sees the Watcher.> **Source image:** image311.png *(media file pending upload: `image311.png`)*

FirstCrackSuccessful(): Called after a guard investigates a crevice containing the player for the first time.> **Source image:** image95.png *(media file pending upload: `image95.png`)*

SuggestInvisibility(): Called the first time a guard tries to aggro on the player. Triggers the invisibility tutorial.

> **Source image:** image63.png *(media file pending upload: `image63.png`)*

TriggerFirstInvisibility(): Called when the player uses their invisibility while the tutorial is active. Deactivates bullet time.

> **Source image:** image268.png *(media file pending upload: `image268.png`)*

SuggestDistraction(): Called when the player moves through the trigger in the cloister. Triggers the distraction tutorial.

> **Source image:** image64.png *(media file pending upload: `image64.png`)*

SuggestReleaseDistraction(): Called when the player aims a distraction while the tutorial is active. Switches the widget to tell them to release.

> **Source image:** image43.png *(media file pending upload: `image43.png`)*

TriggerFirstDistraction(): Called when the player releases their distraction while the tutorial is active. Deactivates bullet time.

> **Source image:** image306.png *(media file pending upload: `image306.png`)*

**QTE Events**

StartQTE(): Picks two random, different dodge directions and sets up the QTE in the HUD, camera manager, and player controller.

> **Source image:** image59.png *(media file pending upload: `image59.png`)*

MoveMouseQTE(Vector2D movement): Called when the player moves their mouse while the first part of the QTE is active. Passes the input value to the HUD to move the widget accordingly.

> **Source image:** image344.png *(media file pending upload: `image344.png`)*

ReceiveQTEInput(): Called when the player passes an input during the second part of the QTE. Passes the input to the HUD to handle.

> **Source image:** image264.png *(media file pending upload: `image264.png`)*

RequestQTEInput(): Called from the HUD when the first part of the QTE is completed. Passes the input based on QTEDodge2.> **Source image:** image323.png *(media file pending upload: `image323.png`)*

SendQTEResult(): Called from the HUD when the second part of the QTE is completed. If the player fails, the level is reloaded. Otherwise, the cutscene plays and the widget is hidden.> **Source image:** image253.png *(media file pending upload: `image253.png`)*

**GI_Lantern Functions**

NoCutscenesModeToggle(): Toggles the NoCutscenesMode bool. Dev tool triggered by pressing 0.

> **Source image:** image272.png *(media file pending upload: `image272.png`)*

InfiniteLightModeToggle(): Toggles the InfiniteLightMode bool. Dev tool triggered by pressing 9.

> **Source image:** image183.png *(media file pending upload: `image183.png`)*

CheckShouldTeachInvisibility(): Returns true if the invisibility tutorial should trigger. The player must have more than 0 light, NoCutscenesMode must be disabled, the camera must not be in fixed mode, and the tutorial must have not yet been triggered.

> **Source image:** image82.png *(media file pending upload: `image82.png`)*

CheckShouldTeachDistraction(): Returns true if the distraction tutorial should trigger. The player must have more than 0 light and the tutorial must have not yet been triggered.> **Source image:** image157.png *(media file pending upload: `image157.png`)*

Save(): Saves the game. Moves all contents of ActivatedInteractables to SavedInteractables. Clears ActivatedInteractables. Called when the player interacts with a Soul Statue.> **Source image:** image343.png *(media file pending upload: `image343.png`)*

## **Game Mode (GM_Lantern)**

**Last Updated:** 10/21/26

###  **Design**

**Design Statement:** While the game instance loads only once (when the application is first launched), the game mode is loaded with each level.

### **Interactions with Other Elements** 

The game mode currently only sets the input mode for the player controller and calls BeginPlay in GI_Lantern.

### **Code Overview**

**GM_Lantern Events**

BeginPlay(): Sets the input mode in the player controller, calls BeginPlay in GI_Lantern (since a game instance does not have BeginPlay built in), and plays the spawn sound.

> **Source image:** image363.png *(media file pending upload: `image363.png`)*

**UI/UX**

## Design Statement

The UI elements in Lantern of Souls are designed so as not to distract from the gameplay. They are small and kept to the sides of the screen whenever possible. A horror game depends on immersion, and flashy text or icons covering the screen very quickly breaks that immersion.

Exceptions to that include instances such as the quick time event and ability tutorials, where the gameplay becomes centered around the UI more than the events in the world itself. That said, they should still not break the immersion for the player. Their designs should match the tone of the game to make the transitions feel sudden but still natural.

## Design Pillars 

1.  Minimalist Design: UI elements should avoid bright, over-saturated colors and intricate designs. The goal of the game is for the player to be aware of their surroundings, which becomes far more difficult if they do not have a full view of them. Icon designs should maintain a consistent style that is both simple and appealing.

2.  Tone: Designs should match the environment such that they feel natural in the world being created. Colors should be mapped to concepts in the same way as the rest of the game.

3.  Sudden but Smooth Transitions: In instances where the UI takes over the gameplay (QTE and ability tutorials), the transitions to them should be sudden, like a jumpscare, but should not feel jerky or unnatural. Lerp anything and everything, even if only for a fraction of a second.

**HUD**

###  **Design**

**Design Statement:** The HUD is the controller of all 2D UI elements that are displayed on the player’s screen throughout the game. It is based in HUD_Main.

### **Interactions with Other Elements** 

The HUD follows a Model-View-Presenter pattern in which the model is the objects in the game (player, braziers, enemies, etc.), the presenter is the game instance (GI_Lantern), and the view is the HUD. This means that the game objects and HUD can only communicate through the game instance. The game instance calls the HUD’s functions EXCLUSIVELY through BPI_HUD so as to depend on abstractions.

For example, when a brazier is opened, BP_Brazier calls the LockBrazier event in GI_Lantern. GI_Lantern then calls BPI_HUD functions that tell HUD_Main to hide the mouse icon and display the “Exit” prompt.

### **Code Overview**

**Variables**

- [<u>ActionWidget</u>](#action-widget-wbp_key): WBP_Key

- [<u>DistractionWidget</u>](#distraction-widget-wbp_distractionactions): WBP_DistractionActions

- [<u>RotateMouseWidget</u>](#rotate-mouse-widget-wbp_rotatemouse): WBP_RotateMouse

- [<u>DistractionAmmoWidget</u>](#distraction-ammo-widget-wbp_distractionammo): WBP_DistractionAmmo

- [<u>PauseMenu</u>](#pause-menu-wbp_pausemenu): WBP_PauseMenu

- [<u>DialogueWidget</u>](#dialogue-widget-wbp_dialogue): WBP_Dialogue

- [<u>BrazierWidget</u>](#brazier-widget-wbp_brazierslit): WBP_BraziersLit

- [<u>QTEWidget</u>](#qte-widget-wbp_qte): WBP_QTE

- [<u>ObjectiveWidget</u>](#objective-widget-wbp_objective): WBP_Objective

- [<u>ToolTipWidget</u>](#tooltip-widget-wbp_tooltip): WBP_ToolTip

- [<u>InvisibleWidget</u>](#invisible-widget-wbp_invisible): WBP_Invisible

- QTEing: bool — whether or not the QTE is currently active

All other variables are deprecated.

The functions and events within BPI_HUD and HUD_Main are below, categorized by their corresponding widgets. All BPI_HUD functions are implemented as events in HUD_Main.

## **Action Widget ([<u>WBP_Key</u>](#action-widget-wbp_key))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

ToggleActionVisibility(): If the action widget is visible, it is hidden. Otherwise, it is displayed. Does not affect text. Not currently in use.

> **Source image:** image126.png *(media file pending upload: `image126.png`)*

DisplayActionPrompt(String key, String action): Calls DisplayActionWidget and passes on the inputs.

> **Source image:** image50.png *(media file pending upload: `image50.png`)*

HideActionPrompt(): Calls HideActionWidget.

> **Source image:** image1.png *(media file pending upload: `image1.png`)*

**HUD_Main Functions**

DisplayActionWidget(String key, String action): If ActionWidget exists, it is added to the viewport with the corresponding text. If not, it is created and then added to the viewport.

> **Source image:** image370.png *(media file pending upload: `image370.png`)*

HideActionWidget(): Removes the widget from the viewport.

> **Source image:** image6.png *(media file pending upload: `image6.png`)*

## **Distraction Widget ([<u>WBP_DistractionActions</u>](#ability-widget-wbp_distractionactions))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

SetDistractionAction(bool chargeSet?): Sets the widget to be visible. The chargeSet? parameter is deprecated.

> **Source image:** image252.png *(media file pending upload: `image252.png`)*

**HUD_Main Functions**

SetDistractionActionsVisibility(bool visible): If visible is true, DistractionActions is created and/or added to the viewport. If not, it is removed.

> **Source image:** image357.png *(media file pending upload: `image357.png`)*

## **Rotate Mouse Widget (WBP_RotateMouse)**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

SetRotateMousePromptVisibility(bool visible): Passes the visible parameter to SetRotateMouseVisibility.

> **Source image:** image103.png *(media file pending upload: `image103.png`)*

**HUD_Main Functions**

SetRotateMouseVisibility(bool visible, bool rune): If visible is true, the widget is created and/or added to the viewport. If not, it is removed. The rune parameter is deprecated.

> **Source image:** image71.png *(media file pending upload: `image71.png`)*

## **Distraction Ammo Widget ([<u>WBP_DistractionAmmo</u>](#light-meter-wbp_distractionammo))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

SetLightAmountVisibility(bool visible): Passes the visible parameter to SetAmmoVisibility.

> **Source image:** image315.png *(media file pending upload: `image315.png`)*

SetLightAmount(float remainingCharge): Ensures that the widget exists, then calls its SetLightAmount function.

> **Source image:** image181.png *(media file pending upload: `image181.png`)*

**HUD_Main Functions**

SetAmmoVisibility(bool visible): If visible is true, the widget is created and/or added to the viewport. If not, it is removed.> **Source image:** image186.png *(media file pending upload: `image186.png`)*

## **Pause Menu ([<u>WBP_PauseMenu</u>](#pause-menu-wbp_pausemenu-1))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

SetPauseMenuVisibility(bool visible): Passes the visible parameter to SetPauseVisibility.

> **Source image:** image259.png *(media file pending upload: `image259.png`)*

**HUD_Main Functions**

SetPauseVisibility(bool visible): If visible is true, the widget is created and/or added to the viewport. If not, it is removed.> **Source image:** image300.png *(media file pending upload: `image300.png`)*

**HUD_Main Events**

ResumeClicked(): Binds to the resume button in the pause menu and tells the game instance to unpause the game

> **Source image:** image335.png *(media file pending upload: `image335.png`)*

QuitToMenuClicked(): Binds to the quit to menu button in the pause menu and tells the game instance to switch the level to the main menu

> **Source image:** image133.png *(media file pending upload: `image133.png`)*

## **Dialogue Widget (WBP_Dialogue)**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

DisplayDialogue(String text, float time, E_Characters speaker): Fades out current dialogue (if applicable), then fades in the new dialogue with the corresponding text and speaker and starts a countdown with the input time.

> **Source image:** image178.png *(media file pending upload: `image178.png`)*

SetLightAmount(float remainingCharge): Ensures that the widget exists, then calls its SetLightAmount function.

> **Source image:** image181.png *(media file pending upload: `image181.png`)*

**HUD_Main Functions**

SetDialogue(String text, E_Characters speaker): Creates the widget if necessary, then displays it with the corresponding text and speaker.> **Source image:** image326.png *(media file pending upload: `image326.png`)*

**HUD_Main Events**

HideDialogue(): Reverses the fade-in timeline to instead make the widget fade out.

> **Source image:** image97.png *(media file pending upload: `image97.png`)*

## **Brazier Widget ([<u>WBP_BraziersLit</u>](#pause-menu-wbp_pausemenu))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

SetNumBraziersLit(int numLit, int numTotal, float displayTime): Calls SetBraziersLit with the corresponding parameters. Visible is always true because the widget simply slides off-screen when not in use.

> **Source image:** image171.png *(media file pending upload: `image171.png`)*

**HUD_Main Functions**

SetBraziersLit(bool visible, int numLit, int numTotal, float displayTime): If visible is true, the widget is created and/or added to the viewport and the Display() function in WBP_BraziersLit is called. If not, it is removed.> **Source image:** image202.png *(media file pending upload: `image202.png`)*

## **QTE Widget ([<u>WBP_QTE</u>](#quick-time-event-wbp_qte))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

BeginQTE(E_QTEDodgeDirections direction1, E_QTEDodgeDirections direction2): Adds the widget to the viewport and calls the StartQTE2 function in WBP_QTE. The direction2 parameter is not in use.

> **Source image:** image176.png *(media file pending upload: `image176.png`)*

MouseQTE(Vector2D movement): Passes the mouse movement to the widget during the first part of the QTE, then notifies the game instance and requests the second dodge direction if the target has been reached.

> **Source image:** image339.png *(media file pending upload: `image339.png`)*

SetQTEKey(String input): Passes the required input for the second dodge and tells the widget to display it.

> **Source image:** image338.png *(media file pending upload: `image338.png`)*

SendQTEInput(Vector2D input): Tells the HUD which input key the player has pressed and converts it to a string (A is represented by (-1, 0), S by (0, -1), and D by (1, 0)). Tells the game instance whether or not the player was successful, then hides the QTE widget.

> **Source image:** image121.png *(media file pending upload: `image121.png`)*

**HUD_Main Functions**

SetQTEVisible(bool visible): If visible is true, the widget is created and/or added to the viewport. If not, it is removed.> **Source image:** image52.png *(media file pending upload: `image52.png`)*

## **Objective Widget ([<u>WBP_Objective</u>](#objective-wbp_objective))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

FadeObjective(float playRate, float visibleTime, float delayTime, Text objective): Sets the objective text, waits delayTime seconds, then fades in the objective widget with the input play rate. After visibleTime seconds, the timeline is reversed and the objective fades out.

> **Source image:** image182.png *(media file pending upload: `image182.png`)*

**HUD_Main Functions**

SetObjectiveVisibility(bool visible, float opacity): If visible is true, the widget is created and/or added to the viewport with the input opacity. If not, it is removed.> **Source image:** image347.png *(media file pending upload: `image347.png`)*

## **Tooltip Widget ([<u>WBP_ToolTip</u>](#tooltip-wbp_tooltip))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

DisplayToolTip(String tipText, float displayTime, String alignment): If another tip with the same alignment (“right” or “left”) is already being displayed, SwapToolTip is called and this function stops. If a tip with opposing alignment is being displayed, that one is collapsed and the function continues. The function then starts lerping the bar, waits 0.3 seconds, then lerps the tip. It starts the ToolTipTimeline function with a play rate based on displayTime, which automatically calls CollapseToolTime when finished.

> **Source image:** image55.png *(media file pending upload: `image55.png`)*

**HUD_Main Functions**

SetToolTipVisibility(bool visible): If visible is true, the widget is created and/or added to the viewport. If not, it is removed.> **Source image:** image373.png *(media file pending upload: `image373.png`)*

**HUD_Main Events**

CollapseToolTip(bool collapseBar): Collapses the tip and, if collapseBar is true, then it collapses that next. If no tip is being swapped in, collapseBar will be false.

> **Source image:** image307.png *(media file pending upload: `image307.png`)*

SwapToolTip(String newText, float time): Collapses the current displayed tip (but not the bar), then lerps in the new one and sets the length of ToolTipTimeline according to the input time.

> **Source image:** image12.png *(media file pending upload: `image12.png`)*

## **Invisible Widget ([<u>WBP_Invisible</u>](#ability-tutorial-wbp_invisible))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

StartAbilityPrompt(String ability): Fades out the objective widget if necessary to avoid overlapping, then sets the panel in WBP_Invisible according to the input ability (“Invisibility”, “Aim”, or “Release”) and fades the widget into view.

> **Source image:** image215.png *(media file pending upload: `image215.png`)*

HideAbilityPrompt(): Hides the widget with SetInvisiblityVisibility.

> **Source image:** image244.png *(media file pending upload: `image244.png`)*

SetAbilityPrompt(String ability): Swaps the visible panel according to the input ability (“Invisibility”, “Aim”, or “Release”) without fading in or out. Used to swap from “Aim” to “Release” in the distraction tutorial.

> **Source image:** image281.png *(media file pending upload: `image281.png`)*

**HUD_Main Functions**

SetInvisibilityVisibility(bool visible): If visible is true, the widget is created and/or added to the viewport. If not, it is removed.> **Source image:** image218.png *(media file pending upload: `image218.png`)*

**Widget Blueprints**

## **Interact (WBP_Key)**

> **Source image:** image165.png *(media file pending upload: `image165.png`)*

**Last Updated:** 10/16/26

###  **Design**

**Design Statement:** The Interact widget is a universal and easily understandable prompt to suggest or indicate the availability of an action to the player. The key and text are both customizable.

### **Interactions with Other Elements** 

This widget appears in the following scenarios.

| **Object**  | **Key** | **Prompts**   | **Scenario**              |
|-------------|---------|---------------|---------------------------|
| Brazier     | F       | Light Brazier | Unlit brazier in range    |
|             |         | Exit          | Player is in brazier mode |
|             |         | Restore Light | Lit brazier in range      |
| Crack       | F       | Hide          | Crack in range            |
|             |         | Exit          | Inside crack              |
| Soul Statue | F       | Interact      | Statue in range           |

The brazier’s “Exit” prompt will not appear until the player has lit the brazier, but they may still exit at any time. The crack’s “Exit” prompt disappears during the Quick Time Event and the player is unable to exit during that time.

### **Code Overview**

**Variables**

- Prompt: Text widget — the textbox containing the prompt displayed below the key

- Key: Text widget — the textbox containing the action key

- Image: Image widget — not yet in use; will replace Key when controller prompts are implemented

**Functions**

SetActionText(String text): Sets the text of Prompt to the input string

> **Source image:** image28.png *(media file pending upload: `image28.png`)*

SetKey(String key): Sets the text of Key to the input string.

> **Source image:** image342.png *(media file pending upload: `image342.png`)*

## **Tooltip (WBP_ToolTip)**

> **Source image:** image146.png *(media file pending upload: `image146.png`)*

**Last Updated:** 10/16/26

###  **Design**

**Design Statement:** The Tooltip widget is used to give the player non-urgent hints about the game. It is a gentle recommendation and does not work for life-or-death scenarios. Each tooltip will display only once.

### **Interactions with Other Elements** 

GI_Lantern has a dictionary called ToolTips that maps E_TooltipKeys to Strings. Any active tooltip must appear in that dictionary, with its text being the String. These are the tooltips that are currently active in the game.

| **E_TooltipKeys** | **Text**                                                                    | **Scenario**                                    |
|-------------------|-----------------------------------------------------------------------------|-------------------------------------------------|
| Crouch            | Hold CTRL to crouch. Stay out of sight by hiding behind objects around you. | Player successfully passes distraction tutorial |
| Crevice Check     | Be careful. Enemies may try to check inside of crevices.                    | Player enters a crack for the first time        |
| Watcher           | Don't let the Watcher see you.                                              | Watcher activates                               |
| Save              | Use Soul Statues to save your progress.                                     | Player enters trigger around first Soul Statue  |
| Hide in Crack     | You can hide in cracks along the wall using F.                              | Player activates first brazier                  |

BP_ToolTipTrigger is an invisible bubble object that can be placed anywhere in a level. It has variables that allow devs to specify a tooltip, display time, and alignment (right or left). When the player enters the bubble for the first time, the corresponding tooltip will display.

### **Code Overview**

**Variables**

- TipRight: Text widget — the textbox containing the right-aligned tip

- TipLeft: Text widget — the textbox containing the left-aligned tip

- BarLeft: Border widget — the left-aligned bar

- BarRight: Border widget — the right-aligned bar

- CurrentText: Text widget — the active text widget (right/left)

- CurrentBar: Border widget — the active bar widget (right/left)

- TipAlpha: float

- BarAlpha: float

- TipSpeed: float

- BarSpeed: float

- LerpingTip: bool — tip is currently sliding into view

- LerpingBar: bool — bar is currently expanding

- ReverseTip: bool — tip is currently sliding out of view

- ReverseBar: bool — bar is currently collapsing

- BarTargetSize: Vector2D

- BarInitialSize: Vector 2D

- TipInitialX: float

- TipTargetX: float

- Alignment: String — “Right” or “Left”

- Active: bool — tooltip is currently visible

**Events**

SetAlignment(String alignment): Sets the alignment to the input string (“Right” or “Left”)

> **Source image:** image282.png *(media file pending upload: `image282.png`)*

StartTipLerp(String tipText): Starts displaying input tooltip at current alignment

StartBarLerp(): Starts displaying bar (called slightly before StartTipLerp)> **Source image:** image223.png *(media file pending upload: `image223.png`)*

ReverseTipLerp() and ReverseBarLerp(): Start collapsing tip and bar, respectively> **Source image:** image336.png *(media file pending upload: `image336.png`)*> **Source image:** image68.png *(media file pending upload: `image68.png`)*

## **Objective (WBP_Objective)**

> **Source image:** image283.png *(media file pending upload: `image283.png`)*

**Last Updated:** 10/16/26

###  **Design**

**Design Statement:** The Objective widget is a simple way of telling the player what to do as soon as they spawn into the game.

### **Interactions with Other Elements** 

The widget interacts only with the HUD.

### **Code Overview**

**Variables**

- TextBlock_138: Text widget — Text box that appears under “Objective”

## **Braziers (WBP_BraziersLit)**

> **Source image:** image155.png *(media file pending upload: `image155.png`)*

**Last Updated:** 10/16/26

###  **Design**

**Design Statement:** This widget helps the player keep track of their progress in the game and feel motivated to continue.

### **Interactions with Other Elements** 

The widget slides in, updates, and slides out each time a brazier is lit.

### **Code Overview**

**Variables**

- TextBlock_21: Text widget — the textbox containing the number of braziers lit and number of total braziers

- Panel: CanvasPanel widget — the panel containing the entire widget

- TargetPos: Vector2D

- HiddenPos: Vector2D

- Speed: float

- SlidingIn: bool

- SlidingOut: bool

- Alpha: float

**Events**

Display(float displayTime, int numLit, int numTotal): Sets the text based on the input and displays the widget

> **Source image:** image197.png *(media file pending upload: `image197.png`)*

**Functions**

SetNumLit(int numLit, int numTotal): Builds the textbox string based on the input

> **Source image:** image288.png *(media file pending upload: `image288.png`)*

## **Ability Widget (WBP_DistractionActions)**

> **Source image:** image257.png *(media file pending upload: `image257.png`)*


**Last Updated:** 10/16/26

###  **Design**

**Design Statement:** This is a static widget that simply serves as a reminder of important abilities (distraction and invisibility) and their inputs to the player.

### **Interactions with Other Elements** 

None fr

### **Code Overview**

No code for the widget is currently in use. It is fully static and displays the same thing throughout the game.

## **Light Meter (WBP_DistractionAmmo)**

> **Source image:** image257.png *(media file pending upload: `image257.png`)*

**Last Updated:** 10/16/26

###  **Design**

**Design Statement:**

### **Interactions with Other Elements** 

Decreases when distraction or invisibility used and increases when restoring light at a lit brazier.

### **Code Overview**

**Variables**

- LightAmount1: ProgressBar widget — the main progress bar that displays the remaining light

All other variables are deprecated.

**Events**

SetLightAmount(float lightAmount): Sets the fill percentage based on the input float; lerps color to red where applicable but widget is not currently being lerped

> **Source image:** image240.png *(media file pending upload: `image240.png`)*

## **Ability Tutorial (WBP_Invisible)**

> **Source image:** image130.png *(media file pending upload: `image130.png`)*

**Last Updated:** 10/16/26

###  **Design**

**Design Statement:** The ability tutorials are designed to force the player to learn how to use main abilities in a way that still makes them feel skilled and capable.

### **Interactions with Other Elements** 

The widget displays the invisibility tutorial the first time the player would be killed IF they have more than 0 light and the camera is not in fixed position. It displays the distraction tutorial when the player passes through the trigger in the cloister.

### **Code Overview**

**Variables**

- Invisible: CanvasPanel widget — the panel containing the invisibility tutorial

- Aim: CanvasPanel widget — the panel containing the aim distraction tutorial

- Release: CanvasPanel widget — the panel containing the release distraction tutorial

**Functions**

SetPanel(String panel): Sets the tutorial based on the input string (“Invisibility”, “Aim”, or “Release”)

> **Source image:** image362.png *(media file pending upload: `image362.png`)*

## **Main Menu (WBP_MainMenu)**

> **Source image:** image263.png *(media file pending upload: `image263.png`)*

**Last Updated:** 10/16/26

###  **Design**

**Design Statement:** The main menu should convey a fragment of the overall fantasy and aesthetic of the game. It is ultimately a very simple interface that currently only accepts a Start input.

### **Interactions with Other Elements** 

The Start button opens the main level.

### **Code Overview**

**Variables**

- Modulate: Widget Animation — fades the start text between yellow and white

- FadeOut: Widget Animation — fades the widget to black

- White: LinearColor — white color of start text

- Yellow: LinearColor — yellow color of start text

**Events**

FadeOut(): Triggers the FadeOut animation; called when Space is pressed and game is started

> **Source image:** image57.png *(media file pending upload: `image57.png`)*

## **Pause Menu (WBP_PauseMenu)**

> **Source image:** image353.png *(media file pending upload: `image353.png`)*

**Last Updated:** 10/16/26

###  **Design**

**Design Statement:** The pause menu allows the player to stop the game and adjust settings as needed.

### **Interactions with Other Elements** 

The entire game is frozen when the pause menu is opened using Tab or Esc.

### **Code Overview**

**Variables**

- Unpause: Button widget — the button that closes the menu and resumes the game

- Settings: Button widget — the button that opens the settings window

- QuitGame: Button widget — the button that exits the game

- Menu: Button widget — the button that brings the player to the main menu

- Close: Button widget — the button that closes the settings menu

- SettingsWindow: CanvasPanel widget — the panel containing the settings menu

**Events**

OnClicked() x3: Open settings, close settings, and quit game

> **Source image:** image31.png *(media file pending upload: `image31.png`)*

**Functions**

OpenMenu(): opens the menu and hides the settings window

> **Source image:** image139.png *(media file pending upload: `image139.png`)*

## **Quick Time Event (WBP_QTE)**

> **Source image:** image236.png *(media file pending upload: `image236.png`)*

**Last Updated:** 10/16/26

###  **Design**

**Design Statement:** The quick time event should make the player feel afraid but skilled enough to overcome that fear, and the widget should support that. It needs to clearly convey exactly what the player should do such that they can understand and react to it in a matter of seconds.

### **Interactions with Other Elements** 

The widget is connected to the QTE itself and is therefore triggered by both player and enemy locations. BP_Crack_I is shaped around the camera’s movement during the QTE.

### **Code Overview**

**Variables**

- DistanceMargin: float — the distance the mouse icon can be from the target to be accepted

- MouseSensitivity: float — the multiplier that alters the mouse movement input to increase mouse speed

- QTEInput: string — the key (A, S, or D) that must be pressed for the player to succeed

- WaitingForInput: bool — whether or not the game is waiting for the player to press the correct key

- WaitingForMouse: bool — whether or not the game is waiting for the player to move the mouse to the target

- DodgeMap: map\[E_QTEDodgeDirections, Vector2D\] — maps each direction to the corresponding target position

- Grab1Direction: EQTEDodgeDirections — the direction of the first dodge

All other non-widget variables are for the old QTE and are deprecated.

**Events**

MoveMouse(Vector2D amount): Moves mouse icon according to input player mouse movement

> **Source image:** image23.png *(media file pending upload: `image23.png`)*

SetInputKey(String key): Sets textbox to required key and listens for player input

> **Source image:** image296.png *(media file pending upload: `image296.png`)*

StartQTE2(E_QTEDodgeDirections direction): Accepts a direction and starts the quick time event

> **Source image:** image19.png *(media file pending upload: `image19.png`)*

**Functions**

IsTargetReached(): bool: Checks whether the mouse icon has been moved close enough to the target

> **Source image:** image41.png *(media file pending upload: `image41.png`)*

StartQTE() corresponds to the old QTE and is deprecated.

## **Rotate Mouse (WBP_RotateMouse)**

> **Source image:** image212.png *(media file pending upload: `image212.png`)*

**Last Updated:** 10/16/26

###  **Design**

**Design Statement:** The widget conveys to the player how they are supposed to rotate the wheel on the brazier to open and light it.

### **Interactions with Other Elements** 

The widget appears when the player has interacted with an unlit brazier. It disappears once they either light it or exit.

### **Code Overview**

**Variables**

- Start: Vector — start position for current lerp

- Target: Vector — target position for current lerp

- Speed: float

- Alpha: float

- CurrentPoint: int

- CanvasPanel_24: CanvasPanel widget — the panel containing the mouse icon

- CircleCenter: Vector — position of the center of the circle

- Radius: float

- NumPoints: int — number of points to find and store (more points makes a more realistic circle)

- CirclePoints: array\[Vector\] — stored points based on center, radius, and numPoints

- Rotate: bool — whether or not the widget should move in a circle

- Iterations: int — the number of times the widget has moved around the circle

All rune-related variables are deprecated.

**Events**

StartRotate(): Sets up lerp for circular movement

> **Source image:** image232.png *(media file pending upload: `image232.png`)*

Construct(): Finds and stores points along a circle according to variables

> **Source image:** image230.png *(media file pending upload: `image230.png`)*

IncrementLine(): Starts the next lerp

> **Source image:** image196.png *(media file pending upload: `image196.png`)*

All rune-related events are deprecated.

**Functions**

GetNextLine(): int: Gets the next line for the widget to follow

> **Source image:** image278.png *(media file pending upload: `image278.png`)*

## **WBP_Dialogue (Not in use)**

## **WBP_Rune (Deprecated)**

## **WBP_DrawnSymbol (Deprecated)**

## **WBP_QuickTimeCrouch (Deprecated)**

## **WBP_QTEVignette (Deprecated)**

## **WBP_DoCrack (Deprecated)**

## **WBP_InCrack (Deprecated)**

## **WBP_GuardRadar (Deprecated)**

## **WBP_GuardProximity (Deprecated)**

## **WBP_LeftClick (Deprecated)**
