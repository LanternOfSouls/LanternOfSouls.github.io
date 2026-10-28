---
title: "Guard"
type: docs
weight: 1
---

## GuardBase.h

The GuardBase’s purpose is to exist as a physical object in the world and hold variables. See the comments for more details.

Variables

```cpp
// unused, intended to be for a guard that holds still

bool bStationary = false;

// deprecated from when we had the guards following a spline. Still in use in BP_Guard, which is not being used anywhere. There is a Watcher variable with the same name.

TArray<FGuardWaypoint> PatrolWaypoints;

// deprecated, only in unused BP_Guard

int NextPatrolWaypointIndex = 0;

// deprecated, only in unused BP_Guard

void OnOverlapWaypoint(const AWaypointBase* Waypoint);

// these are the colors the point lights are set to depending on the guard’s state. They are still used in BP_Guard_01, but their values are overridden.

FLinearColor NeutralColor = FLinearColor(0.371f, 0.0f, 1.0f, 1.0f);

FLinearColor InvestigationColor = FLinearColor(1.0f, 1.0f, 0.0f, 1.0f);

FLinearColor AttackColor = FLinearColor(1.0f, 0.0f, 0.0f, 1.0f);

// Movement speeds

float PatrolSpeed = 150.0f;

float InvestigateSpeed = 250.0f;

float ChaseSpeed = 500.0f;

// Getters, not used

float GetPatrolSpeed() const;

float GetInvestigateSpeed() const;

float GetChaseSpeed() const;

// Setters, not used

void SetPatrolSpeed(float NewSpeed);

void SetInvestigateSpeed(float NewSpeed);

void SetChaseSpeed(float NewSpeed);

// sets light colors

void SetLightColors(FLinearColor LightColor);
```

## GuardBase.cpp

```cpp
void AGuardBase::BeginPlay()

{

Super::BeginPlay();

if (PatrolWaypoints.Num() > NextPatrolWaypointIndex)

{

this->SetActorLocation(PatrolWaypoints[NextPatrolWaypointIndex].Waypoint->GetActorLocation());

}

}
```

This set actor location call is a leftover from following splines and can be removed.

There are also the getters and setters for Speed variables from above, but they are basic setters and getters, so I won’t copy/paste them here. They aren’t used at all, and honestly programmers have probably just been setting the variable directly. Getters and setters are more flexible so I’d like to make them standard practice.

This concludes GuardBase.

## GuardControllerBase.h

Most of the code in this class deals with the perception component. This class’s job is to keep track of the current “most important” object it’s receiving from the perception component. I will explain how this works using a few diagrams rather than copy/paste all 291 lines of code; if you need more details, there are comments in the code to explain the small parts.

First, let’s go over the header file. There are a few delegates, properties, and methods to be aware of:

```cpp
// delegates declared before class declaration; these can be used to trigger in other classes when the GuardController calls them.

DECLARE_DYNAMIC_MULTICAST_DELEGATE_OneParam(FOnGuardYellow, FGuardYellowInfo, GuardYellowInfo);

DECLARE_DYNAMIC_MULTICAST_DELEGATE_OneParam(FOnGuardRed, FGuardYellowInfo, GuardRedInfo);

DECLARE_DYNAMIC_MULTICAST_DELEGATE_OneParam(FOnGuardGreen, FGuardYellowInfo, GuardGreenInfo);

// State Tree asset to run. This will be run on BeginPlay, overriding the existing StateTree.

TObjectPtr<UStateTree> StateTree;

// Deprecated. Only used in old BP_Guard

FGameplayTag ArrivedAtWaypointTag;

// Array of DetectableLights. Keeps track of all DetectableLight objects inside of the vision cone, even those in the green zone.

TArray<TScriptInterface<IDetectableLight>> LightsInRange;

// Deprecated. Not used anywhere.

TEnumAsByte<EDetectionState> DeprecatedCurrentDetectionState;

// Detection Strengths from the previous frame for each DetectableLight. FDetectionStrengthPair is a pair of floats: one for Yellow and one for Red, since Yellow and Red use different equations to determine strength. Both floats are normalized to values between 0 and 1.

TMap<UObject*, FDetectionStrengthPair> OldDetectionStrengths;

// Detection States from the previous frame for each DetectableLight. Used to determine when the detection state changes; if this is different from the current frame’s Detection State, the object has just crossed into a new zone.

TMap<UObject*, TEnumAsByte<EDetectionState>> OldDetectionStates;

// Sight Config used for AIPerceptionComponent. This makes it so the sight sense is enabled and configured by default in Blueprints. It’s assigned default values in the constructor.

TObjectPtr<UAISenseConfig_Sight> SightConfig;

// Same as Sight Config

TObjectPtr<UAISenseConfig_Hearing> HearingConfig;

// If enabled, displays debug information about the detection strengths and states.

bool bDebugDetection = false;

// Reference to the object the guard is prioritizing. Determined by detection strength.

TScriptInterface<IDetectableLight> PriorityLight;

//functions

// Deprecated. Only used in old BP_Guard_AIC and BP_Guard.

void OnReachedWaypoint(FGuardWaypoint NextWaypoint);

// Event bound to PerceptionComponent delegate. Called every time the PerceptionComponent sees or loses any stimulus.

void OnTargetPerceptionUpdated(AActor* Actor, FAIStimulus Stimulus);

// Called when the Guard first sees a DetectableLight. Starts a timer that calls GetLightInfo() every 0.2 seconds, avoiding a Tick() call.

void StartTrackingDetectionState(IDetectableLight* Light);

// This handles all of the state changes; for example, it sends a delegate that the player has crossed into the yellow zone.

void HandleDetectionStateChanges(const TScriptInterface<IDetectableLight>& Light, EDetectionState NewState, EDetectionState OldState, FVector Location);

// Prints a debug statement containing the strength and the detected object

void DebugDetectionState(TScriptInterface<IDetectableLight> Light, float NewDetectionStrength, EDetectionState NewDetectionState);

// Called on Yellow->Green. Blueprint Implementable.

void OnPlayerLost(FVector StimulusLocation);

// Called on Green->Yellow. Blueprint Implementable.

void OnLightDetected(const TScriptInterface<IDetectableLight>& DetectedObject);

// Called on Yellow->Red. Blueprint Implementable.

void OnLightAggro(const TScriptInterface<IDetectableLight>& DetectedObject);

// Not currently in use. Blueprint Implementable.

void OnHeardStimulus(AActor* Actor);

// Given all DetectableLights, calculates the strengths and states of each, then determines which one to follow and calls HandleDetectionStateChanges to send events based on where the objects have moved. Called every 0.2 seconds.

void GetLightInfo();

// begin delegates. These are declarations of the delegates at the beginning.

FOnGuardYellow OnGuardYellow;

FOnGuardYellow OnGuardRed;

FOnGuardYellow OnGuardGreen;

// end delegates
```

## GuardControllerBase.cpp

I’ve added comments in the code explaining the details. Here is a conceptual overview of the class, including the most important snippets of code:

### CONSTRUCTOR (AGuardControllerBase())

The constructor has a few things to set up.

1.  First, it creates the Perception component. This makes the component show up in the Blueprint class:

```cpp
Perception = CreateDefaultSubobject<UGuardPerceptionComponent>(

TEXT("EnemyPerception")

);
```

> **Source image:** image35.png *(media file pending upload: `image35.png`)*

2.  Next, it configures the Sight and Hearing Senses, making them show up in the Blueprint class. Any class that derives from GuardControllerBase will have these defaults.

```cpp
// set up Sight sense

Perception->SetSenseEnabled(UAISense_Sight::StaticClass(), true);

SightConfig = CreateDefaultSubobject<UAISenseConfig_Sight>(TEXT("SightConfig"));

SightConfig->SightRadius = 3000;

SightConfig->LoseSightRadius = 3500;

SightConfig->PeripheralVisionAngleDegrees = 90.0;

SightConfig->DetectionByAffiliation = FAISenseAffiliationFilter(true, true, true);

Perception->ConfigureSense(*SightConfig);

// set up Hearing sense

Perception->SetSenseEnabled(UAISense_Hearing::StaticClass(), true);

HearingConfig = CreateDefaultSubobject<UAISenseConfig_Hearing>(TEXT("HearingConfig"));

HearingConfig->HearingRange = 4000;

HearingConfig->DetectionByAffiliation = FAISenseAffiliationFilter(true, true, true);

Perception->ConfigureSense(*HearingConfig);
```

> **Source image:** image204.png *(media file pending upload: `image204.png`)*

3.  It binds a function to the Perception Component’s OnTargetPerceptionUpdated delegate (more on that in the Perception section.

4.  It disables the StateTree automatically starting, since we want to change the StateTree at runtime.

```cpp
// disable state tree starting automatically; we will do this ourselves at BeginPlay

StateTreeAI->SetStartLogicAutomatically(false);
```

### Perception Component Integration

The GuardControllerBase has an AIPerceptionComponent (this is the vision cone). I won’t go into detail on the PerceptionComponent’s inner workings, just the Controller’s job in relation to it. In the constructor, it registers its own function to the PerceptionComponent’s delegate so it can react when the perception detects a stimulus.

```cpp
// add delegate for perception updates

Perception->OnTargetPerceptionUpdated.AddDynamic(this, &AGuardControllerBase::OnTargetPerceptionUpdated);
```

Now we’ll set up a situation: The player crosses into the guard’s vision cone, stays for a couple seconds, then breaks line of sight.

1.  The player enters the vision cone, triggering OnTargetPerceptionUpdated:

    1.  check to see if the player is a DetectableLight

    2.  add the player to LightsInRange

    3.  start tracking the player’s Red/Yellow/Green detection state every 0.2 seconds.

<!-- -->

1.  StartTrackingDetectionState starts a loop to call GetLightInfo every 0.2 seconds

2.  GetLightInfo uses a standard “find the biggest item in this array” style loop. It initializes all of the variables, then does the following for each iteration of the loop:

    1.  Asks the Player through the DetectableLight interface, which uses the GetDetectability function, for their location, light strength, and whether they’re in a crevice.

```cpp
auto [Location, LightStrength, bHiding] = IDetectableLight::Execute_GetDetectability(Light.GetObject());
```

2.  Asks the Perception component to calculate the detection score (DetectionStrength, a number between 0 and 1). It checks to see if the player is hiding in a crevice, setting the strength to 0 if they are.

```cpp
// Player should not be detected if they're hiding in a crevice.

if (!bHiding) {

NewDetectionStrength = GuardPerception->GetDetectionStrength(GetPawn()->GetActorLocation(), Location, SightConfig->LoseSightRadius, LightStrength);

} else {

NewDetectionStrength = {0, 0};

}
```

3.  Uses the DetectionStrength to calculate the DetectionState (Red, Yellow, Green)

```cpp
// calculate the new green/yellow/red state based on the strength

EDetectionState NewDetectionState = GuardPerception->GetDetectionState(NewDetectionStrength.YellowStrength, NewDetectionStrength.RedStrength);
```

4.  Let’s review. At this point, we’ve confirmed that the Player is not hiding in a crevice and we’ve labeled them Red, Yellow, or Green based on their position and light level.

5.  The next step is to get the detection strength and state from the previous “frame” (but remember, these aren’t actual frames since it’s running every 0.2 seconds). These are stored in OldDetectionStrengths and OldDetectionStates. (In this case, they are EMPTY, because the player is just barely getting registered with the perception system. Most of the time, it will be actual numbers from the last frame.) We do some fun C++ pointer shenanigans to get the Strength:

```cpp
FDetectionStrengthPair* OldDetectionStrengthPtr = OldDetectionStrengths.Find(Light.GetObject());

FDetectionStrengthPair OldDetectionStrength;

if (OldDetectionStrengthPtr == nullptr) { // the light is entering vision radius and doesn't have an entry in OldDetectionStrengths yet

OldDetectionStrength = {FLT_EPSILON, FLT_EPSILON};

} else {

OldDetectionStrength = *OldDetectionStrengthPtr;

}
```

6.  Then we do the exact same process to get the State (Red, Yellow, Green):

```cpp
TEnumAsByte<EDetectionState>* OldDetectionStatePtr = OldDetectionStates.Find(Light.GetObject());

EDetectionState OldDetectionState;

if (OldDetectionStatePtr == nullptr) { // the light is entering vision radius and doesn't have an entry in OldDetectionStates yet

OldDetectionState = Green;

} else {

OldDetectionState = *OldDetectionStatePtr;

}
```

7.  Before doing anything else, we must update the OldDetectionStrengths and States so that we have our *current* values in the next “frame”.

```cpp
OldDetectionStrengths.Add(Light.GetObject()) = NewDetectionStrength;

OldDetectionStates.Add(Light.GetObject()) = NewDetectionState;
```

8.  Now we check the strength against our running maximum - remember, this is looping through *all* of the objects in the vision cone to find the “brightest” one.

```cpp
if (OldDetectionStrength.YellowStrength > HighestDetectionStrength)

{

HighestNewDetectionState = NewDetectionState;

HighestOldDetectionState = OldDetectionState;

HighestLocation = Location;

HighestLight = Light;

PriorityLight = Light;

}
```

9.  We let the for loop run to completion. This is what we’ve been building to: **now we have a reference to the “brightest” object in the Guard’s vision cone**, along with its previous and current detection strengths and states.

10. With this information, we call HandleDetectionStateChanges, which is the piece of the C++ class that connects to the Blueprint event graph.

```cpp
HandleDetectionStateChanges(HighestLight, HighestNewDetectionState, HighestOldDetectionState, HighestLocation);
```

11. HandleDetectionStateChanges is pretty simple, but it’s better explained by a diagram. It uses the Old and New detection states to decide which Blueprint function it will call: OnLightDetected, OnPlayerLost, or OnLightAggro.

> **Source image:** image297.png *(media file pending upload: `image297.png`)*

3.  We do have one last Perception case to look at: what happens when the player leaves the vision cone? This happens in OnTargetPerceptionUpdated, the function that’s subscribed to the Perception component.

    1.  We remove the stimulus from LightsInRange; this stops us from tracking it.

```cpp
LightsInRange.Remove(Light);
```

2.  We remove the stimulus’s values from OldDetectionStates and OldDetectionStrengths

```cpp
OldDetectionStates.Remove(Actor);

OldDetectionStrengths.Remove(Actor);
```

3.  We call OnPlayerLost, which happens in Blueprints. This handles the case where the player walks straight from the yellow zone out of the vision cone, without passing through the green zone first (like behind a wall while in the yellow zone). FIX: this should also check to ensure the player is not in the green zone.

```cpp
OnPlayerLost(Stimulus.StimulusLocation);
```

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

```cpp
ABP_GuardTestAnims:
```

> **Source image:** image321.png *(media file pending upload: `image321.png`)*

STT_ChooseNextPointOfInterest

> **Source image:** image61.png *(media file pending upload: `image61.png`)*

fix: pull ActorToLookAt into C++ parent

BP_Guard01:

> **Source image:** image66.png *(media file pending upload: `image66.png`)*

> **Source image:** image73.png *(media file pending upload: `image73.png`)*

fix: declare these two functions in C++ parent (definition can stay in BP if needed)

GI_Lantern:

> **Source image:** image270.png *(media file pending upload: `image270.png`)*

x3

fix: remove cast; Get Controlled Pawn exists in base Controller class

BP_LightProjectile:

> **Source image:** image163.png *(media file pending upload: `image163.png`)*

BP_WaypointManager:

> **Source image:** image305.png *(media file pending upload: `image305.png`)*

x2

fix: declare GoToNewStimulus in C++ parent

## BP Reference audit - Pawn

```cpp
AIC_GuardController02, BP_GuardController01_AIC:
```

> **Source image:** image80.png *(media file pending upload: `image80.png`)*

> **Source image:** image39.png *(media file pending upload: `image39.png`)*

> **Source image:** image76.png *(media file pending upload: `image76.png`)*

fix: move PointToGoTo and RandomlyCheckingPlayerCrevice to C++

BP_GuardController01_AIC:

> **Source image:** image287.png *(media file pending upload: `image287.png`)*

fix: define a function to get the skeletal mesh in C++, then implement it in Blueprints

STT_CheckIfPointIsCrevice:

> **Source image:** image318.png *(media file pending upload: `image318.png`)*

fix: move PointToGoTo to C++

STT_ChooseClosestPointsInRange:

> **Source image:** image208.png *(media file pending upload: `image208.png`)*

> **Source image:** image65.png *(media file pending upload: `image65.png`)*

fix: move PointsToInvestigate and PointOfInterestRange to C++

STT_ChooseClosestPointOfInterest:

> **Source image:** image243.png *(media file pending upload: `image243.png`)*

> **Source image:** image62.png *(media file pending upload: `image62.png`)*

> **Source image:** image92.png *(media file pending upload: `image92.png`)*

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

> **Source image:** image128.png *(media file pending upload: `image128.png`)*

> **Source image:** image329.png *(media file pending upload: `image329.png`)*

> **Source image:** image346.png *(media file pending upload: `image346.png`)*

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

> **Source image:** image216.png *(media file pending upload: `image216.png`)*

> **Source image:** image118.png *(media file pending upload: `image118.png`)*

> **Source image:** image86.png *(media file pending upload: `image86.png`)*

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

```cpp
TArray<FGuardWaypoint> Waypoints;
```

This FGuardWaypoint struct, however, is used frequently throughout the Guard and Controller. The weight is not referenced anywhere, but we may want to use it eventually.

```cpp
USTRUCT(BlueprintType)
struct FGuardWaypoint
{
    GENERATED_BODY()

public:
    TObjectPtr<AWaypointBase> Waypoint;
    float Weight = 1.0f;
};
```

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

```cpp
// How sensitive the enemy is to the player's distance

float YellowDistanceWeight = 1;

// How sensitive the enemy is to the player's angle (peripheral vision or straight on)

float YellowAngleWeight = 1;

// How sensitive the enemy is to light levels

float YellowLightWeight = 1;

// How sensitive the enemy is to the player's distance

float RedDistanceWeight = 1;

// How sensitive the enemy is to the player's angle (peripheral vision or straight on)

float RedAngleWeight = 1;

// How sensitive the enemy is to light levels

float RedLightWeight = 1;

// The threshold at which the enemy becomes curious (0-1)

float CuriousThreshold = 0.33;

// The threshold at which the enemy becomes aggro (0-1)

float AggroThreshold = 0.66;

// Minimum distance to ensure the enemy aggros. Unused.

float MinimumAggroDistance = 100;

// height of the floating debug bar chart

float DebugVerticalOffset = 300;
```

Then the following public functions, which we saw in the GuardController (plus a function for debugging):

```cpp
UFUNCTION(BlueprintCallable, Category="Enemy|Perception")

FDetectionStrengthPair GetDetectionStrength(FVector SelfLocation, FVector StimulusLocation, float LoseSightRadius, float LightAmount);

UFUNCTION(BlueprintCallable, Category="Enemy|Perception")

EDetectionState GetDetectionState(float YellowDecision, float RedDecision);

void DebugDetectionStrength(FVector MyLocation, float Angle, float Distance, float LightAmount, const FString* Identifier) const;
```

And finally a private function, used only by this class:

```cpp
void NormalizeDetectionWeights();
```

Let’s see how they’re built in the CPP file. We’ll start with NormalizeDetectionWeights(). Its purpose is to turn all of the Weight values into a number between 0 and 1. For example, values 1, 2, 1 become 0.25, 0.5, 0.25, which all add

up to 1.

```cpp
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
```

We normalize our weights at BeginPlay.

When the Controller asks us for a Strength, we calculate the detection strength. Parameters for this function are our own location, the stimulus location, our sight range, and the brightness of the object, which we use to determine how strongly we’re sensing the object.

```cpp
FDetectionStrengthPair UGuardPerceptionComponent::GetDetectionStrength(FVector SelfLocation, FVector StimulusLocation, float LoseSightRadius, float LightAmount) {}
```

This involves 3 different calculations, since we’re dealing with distance, angle, and light amount.

Light Amount is the easiest, since we get the value through a parameter. Remember, the Controller asked the Player for this value back in GetLightInfo(). We “normalize” this value by multiplying it by the weight.

```cpp
float YellowLightAmountNormalized = LightAmount*YellowLightWeight;
```

Distance is the next easiest. This will be a value between 0 and 1, with 0 at the edge of the vision radius, and 1 right on top of the guard.

```cpp
float DistanceNormalized = 1-UKismetMathLibrary::Vector_Distance2D(StimulusLocation, SelfLocation)/(LoseSightRadius);
```

We normalize the distance value in the same way, by multiplying it by its weight.

```cpp
float YellowDistanceNormalized = DistanceNormalized * YellowDistanceWeight;
```

Last, we have Angle. This one is a little more complicated and involves some linear algebra. We end up with a value between 0 and 1, where 0 = to the side and 1 = right in front of the enemy.

```cpp
FVector Direction = (StimulusLocation - SelfLocation).GetSafeNormal2D();

float AngleNormalized = Direction.Dot(this->GetOwner()->GetActorForwardVector());
```

We normalize this just like the other two.

```cpp
float YellowAngleNormalized = AngleNormalized*YellowAngleWeight;
```

Now we have three variables indicating how “strongly” the guard sees the player. They’ve been adjusted with weights depending on which one the designer wants to prioritize. We add all three together to get YellowDecision, a value between 0 and 1. **This is what we compare to the CuriousThreshold (yellow) to decide if it’s “in” or “out” of the yellow zone.**

```cpp
float YellowDecision = YellowAngleNormalized + YellowDistanceNormalized + YellowLightAmountNormalized;
```

The RedDecision is calculated exactly the same way, using the Red variables instead of the Yellow ones.

At some point, the Controller will ask us (the PerceptionComponent) to convert this RedDecision and YellowDecision into Red, Yellow, or Green. We calculate this by comparing the Decision variables with the Aggro (red) and Curious (yellow) thresholds:

```cpp
EDetectionState UGuardPerceptionComponent::GetDetectionState(float YellowDecision, float RedDecision)

{

if (RedDecision > AggroThreshold)

{

return Red;

}

if (YellowDecision > CuriousThreshold)

{

return Yellow;

}

return Green;

}
```

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
