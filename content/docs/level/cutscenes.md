---
title: "Cutscenes"
type: docs
weight: 5
---

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
