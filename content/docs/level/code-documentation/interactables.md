---
title: "Interactables"
type: docs
weight: 3
url: "/docs/level/interactables/"
---

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
**<u>if destroyed</u>

> **Source image:** image299.png *(media file pending upload: `image299.png`)*

restore some light.

<u>if completed</u>

> **Source image:** image345.png *(media file pending upload: `image345.png`)*

restore light. Do this only once.

<u>if not completed, and is active</u> 

> **Source image:** image109.png *(media file pending upload: `image109.png`)*

free the camera and update materials. Set active so this will not happen again.

> **Source image:** image371.png *(media file pending upload: `image371.png`)*

remove the controls for the brazier opening mini game. Make the player visible again.

> **Source image:** image106.png *(media file pending upload: `image106.png`)*

update the Game Instance so it doesn’t display the minigame UI anymore. Trigger cutscene.

<u>If not completed or active:</u>

> **Source image:** image91.png *(media file pending upload: `image91.png`)*

enter fixed camera. Remove usual player controls and activate minigame controls.

> **Source image:** image193.png *(media file pending upload: `image193.png`)*

hide the player. Assign new materials and alert the GI to begin displaying the minigame UI.

**Event Tick**: Relevant only during the minigame. Updates the position of the top of the brazier and play the sounds of opening the brazier. If the minigame is complete, it tells the GI to lock this brazier.

**RotateWheel:** Performs the math to detect mouse rotations, and update the position of the visible ship’s wheel.

**Activate**

> **Source image:** image217.png *(media file pending upload: `image217.png`)*

Pings enemies, activates activatables associated with it, tells the GI to update its status.

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
