---
title: "UI & HUD Reference"
type: docs
weight: 1
url: "/docs/ui-hud/reference/"
---

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

SetAmmoVisibility(bool visible): If visible is true, the widget is created and/or added to the viewport. If not, it is removed.

> **Source image:** image186.png *(media file pending upload: `image186.png`)*

## **Pause Menu ([<u>WBP_PauseMenu</u>](#pause-menu-wbp_pausemenu-1))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

SetPauseMenuVisibility(bool visible): Passes the visible parameter to SetPauseVisibility.

> **Source image:** image259.png *(media file pending upload: `image259.png`)*

**HUD_Main Functions**

SetPauseVisibility(bool visible): If visible is true, the widget is created and/or added to the viewport. If not, it is removed.

> **Source image:** image300.png *(media file pending upload: `image300.png`)*

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

SetDialogue(String text, E_Characters speaker): Creates the widget if necessary, then displays it with the corresponding text and speaker.

> **Source image:** image326.png *(media file pending upload: `image326.png`)*

**HUD_Main Events**

HideDialogue(): Reverses the fade-in timeline to instead make the widget fade out.

> **Source image:** image97.png *(media file pending upload: `image97.png`)*

## **Brazier Widget ([<u>WBP_BraziersLit</u>](#pause-menu-wbp_pausemenu))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

SetNumBraziersLit(int numLit, int numTotal, float displayTime): Calls SetBraziersLit with the corresponding parameters. Visible is always true because the widget simply slides off-screen when not in use.

> **Source image:** image171.png *(media file pending upload: `image171.png`)*

**HUD_Main Functions**

SetBraziersLit(bool visible, int numLit, int numTotal, float displayTime): If visible is true, the widget is created and/or added to the viewport and the Display() function in WBP_BraziersLit is called. If not, it is removed.

> **Source image:** image202.png *(media file pending upload: `image202.png`)*

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

SetQTEVisible(bool visible): If visible is true, the widget is created and/or added to the viewport. If not, it is removed.

> **Source image:** image52.png *(media file pending upload: `image52.png`)*

## **Objective Widget ([<u>WBP_Objective</u>](#objective-wbp_objective))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

FadeObjective(float playRate, float visibleTime, float delayTime, Text objective): Sets the objective text, waits delayTime seconds, then fades in the objective widget with the input play rate. After visibleTime seconds, the timeline is reversed and the objective fades out.

> **Source image:** image182.png *(media file pending upload: `image182.png`)*

**HUD_Main Functions**

SetObjectiveVisibility(bool visible, float opacity): If visible is true, the widget is created and/or added to the viewport with the input opacity. If not, it is removed.

> **Source image:** image347.png *(media file pending upload: `image347.png`)*

## **Tooltip Widget ([<u>WBP_ToolTip</u>](#tooltip-wbp_tooltip))**

**Last Updated:** 10/19/26

**BPI_HUD Functions**

DisplayToolTip(String tipText, float displayTime, String alignment): If another tip with the same alignment (“right” or “left”) is already being displayed, SwapToolTip is called and this function stops. If a tip with opposing alignment is being displayed, that one is collapsed and the function continues. The function then starts lerping the bar, waits 0.3 seconds, then lerps the tip. It starts the ToolTipTimeline function with a play rate based on displayTime, which automatically calls CollapseToolTime when finished.

> **Source image:** image55.png *(media file pending upload: `image55.png`)*

**HUD_Main Functions**

SetToolTipVisibility(bool visible): If visible is true, the widget is created and/or added to the viewport. If not, it is removed.

> **Source image:** image373.png *(media file pending upload: `image373.png`)*

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

SetInvisibilityVisibility(bool visible): If visible is true, the widget is created and/or added to the viewport. If not, it is removed.

> **Source image:** image218.png *(media file pending upload: `image218.png`)*

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

StartBarLerp(): Starts displaying bar (called slightly before StartTipLerp)

> **Source image:** image223.png *(media file pending upload: `image223.png`)*

ReverseTipLerp() and ReverseBarLerp(): Start collapsing tip and bar, respectively

> **Source image:** image336.png *(media file pending upload: `image336.png`)*

> **Source image:** image68.png *(media file pending upload: `image68.png`)*

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
