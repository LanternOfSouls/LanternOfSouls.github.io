---
title: "Game Systems"
type: docs
weight: 7
---

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

LockBrazier(): Called when the player finishes opening a brazier. Hides the rotate mouse prompt and displays the “Exit” prompt.

> **Source image:** image101.png *(media file pending upload: `image101.png`)*

BrokenBrazierInteract(): Not currently in use but does get called when the player interacts with a broken brazier.

> **Source image:** image261.png *(media file pending upload: `image261.png`)*

**Player Events**

RechargeLight(float percent): Sets the player’s light amount to the input percent.

> **Source image:** image341.png *(media file pending upload: `image341.png`)*

PlayerBeginPlay(): Called when the player spawns/respawns. Sets the distraction ammo and abilities to be visible.

> **Source image:** image271.png *(media file pending upload: `image271.png`)*

BeginInteractOverlap(): Called when the player enters the range of an interactable. Displays an action prompt based on the subclass of that interactable.

> **Source image:** image245.png *(media file pending upload: `image245.png`)*

EndInteractOverlap(): Called when a player exits the range of an interactable. Hides the action prompt.

> **Source image:** image17.png *(media file pending upload: `image17.png`)*

**Game Events**

PauseGame(): Called when the player presses Esc or Tab. Freezes the game and displays the pause menu.

> **Source image:** image361.png *(media file pending upload: `image361.png`)*

UnpauseGame(): Unfreezes the game and hides the pause menu.

> **Source image:** image85.png *(media file pending upload: `image85.png`)*

TogglePause(): Pauses game if unpaused. Unpauses game if paused.

> **Source image:** image29.png *(media file pending upload: `image29.png`)*

ReturnToMainMenu(): Opens the main menu level and resets the game.

> **Source image:** image30.png *(media file pending upload: `image30.png`)*

BeginPlay(): Called from the built-in BeginPlay function in GM_Lantern since a game instance doesn’t have its own. Sets up the level.

> **Source image:** image5.png *(media file pending upload: `image5.png`)*

ResetGame(): Called each time the player dies. Sets their spawn location/rotation and handles the braziers according to the last save point.

> **Source image:** image45.png *(media file pending upload: `image45.png`)*

InitializePlayerStart(): Moves the player start actor according to SpawnPointLocation and SpawnPointRotation.

> **Source image:** image108.png *(media file pending upload: `image108.png`)*

SetBrazierUI(): Sets the Braziers Lit Widget based on TotalBraziers and the length of BraziersLit.

> **Source image:** image354.png *(media file pending upload: `image354.png`)*

SetGuards(): Finds all guards in the level and adds them to the Guards set.

> **Source image:** image142.png *(media file pending upload: `image142.png`)*

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

FirstBrazierLit(): Called after the player lights a brazier for the first time.

> **Source image:** image241.png *(media file pending upload: `image241.png`)*

FirstCrackUsed(): Called the first time a player enters a crack.

> **Source image:** image191.png *(media file pending upload: `image191.png`)*

FirstCrackSuccessful(): Called after a guard investigates a crevice containing the player for the first time.

> **Source image:** image95.png *(media file pending upload: `image95.png`)*

SeeWatcher(): Called the first time the player sees the Watcher.

> **Source image:** image311.png *(media file pending upload: `image311.png`)*

FirstCrackSuccessful(): Called after a guard investigates a crevice containing the player for the first time.

> **Source image:** image95.png *(media file pending upload: `image95.png`)*

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

RequestQTEInput(): Called from the HUD when the first part of the QTE is completed. Passes the input based on QTEDodge2.

> **Source image:** image323.png *(media file pending upload: `image323.png`)*

SendQTEResult(): Called from the HUD when the second part of the QTE is completed. If the player fails, the level is reloaded. Otherwise, the cutscene plays and the widget is hidden.

> **Source image:** image253.png *(media file pending upload: `image253.png`)*

**GI_Lantern Functions**

NoCutscenesModeToggle(): Toggles the NoCutscenesMode bool. Dev tool triggered by pressing 0.

> **Source image:** image272.png *(media file pending upload: `image272.png`)*

InfiniteLightModeToggle(): Toggles the InfiniteLightMode bool. Dev tool triggered by pressing 9.

> **Source image:** image183.png *(media file pending upload: `image183.png`)*

CheckShouldTeachInvisibility(): Returns true if the invisibility tutorial should trigger. The player must have more than 0 light, NoCutscenesMode must be disabled, the camera must not be in fixed mode, and the tutorial must have not yet been triggered.

> **Source image:** image82.png *(media file pending upload: `image82.png`)*

CheckShouldTeachDistraction(): Returns true if the distraction tutorial should trigger. The player must have more than 0 light and the tutorial must have not yet been triggered.

> **Source image:** image157.png *(media file pending upload: `image157.png`)*

Save(): Saves the game. Moves all contents of ActivatedInteractables to SavedInteractables. Clears ActivatedInteractables. Called when the player interacts with a Soul Statue.

> **Source image:** image343.png *(media file pending upload: `image343.png`)*

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
