---
title: "Activatables"
type: docs
weight: 4
---

## **<u>Activatables</u>**

**Last Updated:** 10/26/26

### **Design**

**Design Statement:** Activatables are actors within the game which perform a specific action when triggered by their OnActivate event. Activations are typically triggered by player actions, often involving Interactables.

## 

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

OnActivate

> **Source image:** image285.png *(media file pending upload: `image285.png`)*

activates the torches.

AddTorch

> **Source image:** image11.png *(media file pending upload: `image11.png`)*

spawns a new torch and adds it to its array of Torches

DestroyTorches

> **Source image:** image225.png *(media file pending upload: `image225.png`)*

deletes all torches in its array, then itself.

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

> **Source image:** image26.png *(media file pending upload: `image26.png`)*

sets the color of FlameMaterial to the preset golden light.

BeginPlay

> **Source image:** image266.png *(media file pending upload: `image266.png`)*

Creates a new material instance and assigns it to FlameMaterial, then assigns it to the sphere at the top.

## **BP_DoorLights**

> **Source image:** image143.png *(media file pending upload: `image143.png`)*

**Design Statement:** a light source placed to illuminate and draw attention to important items in the level, and change color to indicate completion of the area.

**Interactions with Other Elements**

**Interactable:** Requires an interactable to call OnActivate

### **Code Overview**

OnActivate: 

> **Source image:** image150.png *(media file pending upload: `image150.png`)*

sets the color of the spot light to the preset golden light.

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

BeginOverlap

> **Source image:** image69.png *(media file pending upload: `image69.png`)*

when overlapping a player, it checks its own activation status, then if not activated, calls OnActivate on itself. If it is activated and can be deactivated, it deactivates itself.

OnActivate

> **Source image:** image83.png *(media file pending upload: `image83.png`)*

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

OnComponentBeginOverlap

> **Source image:** image226.png *(media file pending upload: `image226.png`)*

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

**BP_Watcher_Trigger (OnActivate):**

> **Source image:** image40.png *(media file pending upload: `image40.png`)*

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
