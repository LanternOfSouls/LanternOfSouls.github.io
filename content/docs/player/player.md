---
title: "Player"
type: docs
weight: 1
---

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

If rotation is not frozen, it will get the BP player and it <span class="mark">calls a variable that we don’t even use anymore (drawing).</span> It then tracks to see if the player is in the crack, it casts to GI lantern to see if there is a quicktime event. If there is, the mouse switches to be one that is visible on the screen instead of controlling where the camera is looking. (think click and point game.) (See [<u>QTE Widget</u>](../../ui-hud/reference/#qte-widget-wbp_qte) for more info.)

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

> **Source image:** image246.png *(media file pending upload: `image246.png`)*

However if the Closest distance IS within the detect range,

The set visibility is put on the arrow, which points towards the closest guard. The Set Actor Rotation rotates the soul depending on the look at rotation from the soul to the closest guard.

The soul is then lit to yellow to indicate that the guard is nearby.

> **Source image:** image337.png *(media file pending upload: `image337.png`)*

However, if the Closest Distance is shorter than the Panic Range, it will set the soul’s color to red, indicating imminent danger.

This statment loops back to the first GET dead in the blueprint, creating a while loop that keeps activating the function until the Soul is dead.

> **Source image:** image199.png *(media file pending upload: `image199.png`)*

When death is called, it sets the dead boolean, which breaks the large while loop above. It also turns off the invisibility for the arrow.

**Camager**

**Core of Camager: Camera Orient**

**Camera Orient is a crucial component of the camera, and the first thing I coded to make the camager work. It constantly gets the camera location and rotation. You won’t interact with this function, but this function will show up continually in the code.**

> **Source image:** image132.png *(media file pending upload: `image132.png`)*

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

> **Source image:** image237.png *(media file pending upload: `image237.png`)*

> **Source image:** image255.png *(media file pending upload: `image255.png`)*

> **Source image:** image211.png *(media file pending upload: `image211.png`)*

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

> **Source image:** image355.gif *(media file pending upload: `image355.gif`)*

> **Source image:** image308.gif *(media file pending upload: `image308.gif`)*

**Design Statement:** Where do I even begin? Crack look started off as a fixed camera that would just switch to peek left and right, which were more fixed cameras. However we wanted the experience in the crack to be more interactive. This is first done by letting the player look around the crack with their mouse. Then with the quick time event, we did something super dynamic, which the camera movements had to match.

### **Interactions with Other Elements** 

**Interactables:** The player is able to look around the corners with the mouse, when the enemy is around the area, and decides to look inside the crack, a quick time event starts.

**Code**

This is the flow of logic within blueprint update camera. The structure here is similar to the other walking cameras, however instead of camera orient, we have <span class="mark">Enter Crack Look</span>, which handles the core logic way differently. 

> **Source image:** image319.png *(media file pending upload: `image319.png`)*

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

When there's a QTE, there’s one more boolean for QTE dodging, which happens when the player dodges after successfully doing the QT task. 

> **Source image:** image44.png *(media file pending upload: `image44.png`)*

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

> **Source image:** image185.png *(media file pending upload: `image185.png`)*

> **Source image:** image135.png *(media file pending upload: `image135.png`)*

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

- AddEvent that is always triggered by GI_Lantern, which records to a file based on the name that is set by CurrentFile. 

> **Source image:** image125.png *(media file pending upload: `image125.png`)*

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
