---
title: "Watcher"
type: docs
weight: 2
---

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

> **Source image:** image201.png *(media file pending upload: `image201.png`)*

> **Source image:** image94.png *(media file pending upload: `image94.png`)*

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
