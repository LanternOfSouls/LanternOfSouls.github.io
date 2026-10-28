---
title: "Game Mode"
type: docs
weight: 1
---

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
