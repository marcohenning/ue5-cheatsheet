# Utilities

## Delay

![delay](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/2ed38a93-99ec-4c4b-b0be-3b9dd52a1926)

There is no equivalent to the delay node in C++, so timers are used instead.
If you want to execute code after a specific delay, put that code into a function and then start a timer with the desired delay.
See: `Set Timer by Function Name`

## Print String

![print_string](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/23c01a82-1284-4c52-8cc1-ae4b919e4890)

Commonly used, but has a few minor differences to the blueprint node:

```cpp
if (GEngine)
{
	GEngine->AddOnScreenDebugMessage(
		-1,                        // Key
		2.0f,                      // Duration
		FColor::Cyan,              // Color
		"Hello"                    // Message
	);
}
```

The exact blueprint node:

```cpp
#include "Kismet/KismetSystemLibrary.h"

UKismetSystemLibrary::PrintString(
	this,                                    // World context object
	"Hello",                                 // Message
	true,                                    // Print to screen?
	true,                                    // Print to console?
	FLinearColor(0.0f, 0.66f, 1.0f, 1.0f),   // Color
	2.0f                                     // Duration
);
```

## Get Player Controller

![get_player_controller](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/18f58b8b-86f1-482e-addb-15fb304b6c01)

```cpp
#include "Kismet/GameplayStatics.h"

APlayerController* PlayerController = UGameplayStatics::GetPlayerController(this, 0);
```

## Get Player Camera Manager

![get_player_camera_manager](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/8e1d3d1a-1e1b-411e-9295-0c6cf55d34fd)

```cpp
#include "Kismet/GameplayStatics.h"

APlayerCameraManager* PlayerCameraManager = UGameplayStatics::GetPlayerCameraManager(this, 0);
```

## Spawn Emitter at Location

![spawn_emitter_at_location](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/6ecbed9d-961b-4953-993c-d48df3bb99ef)

.h File
```cpp
private:
	// The emitter needs to be set in blueprint
	UPROPERTY(EditAnywhere, meta = (AllowPrivateAccess = "true"))
	UParticleSystem* ExampleEmitter;
```

.cpp File
```cpp
#include "Kismet/GameplayStatics.h"

UParticleSystemComponent* SpawnedEmitter;
FTransform SpawnTransform;

if (ExampleEmitter)
{
	SpawnedEmitter = UGameplayStatics::SpawnEmitterAtLocation(
		GetWorld(),        // World object
		ExampleEmitter,    // Emitter
		SpawnTransform     // Spawn transform
	);
}
```

## Line Trace By Channel

![line_trace_by_channel](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/e7eb2f56-034d-4108-b261-f5f25e08a9fc)

```cpp
FVector Start;
FVector End;

// Results will be stored here
FHitResult HitResult;

bool bHit = GetWorld()->LineTraceSingleByChannel(
	HitResult,                                   // Hit result
	Start,                                       // Start of the trace
	End,                                         // End of the trace
	ECollisionChannel::ECC_Visibility            // Trace channel
);
```

## Multi Line Trace By Channel

![multi_line_trace_by_channel](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/55d5275e-21c2-4833-b7bd-beec07fab781)

```cpp
FVector Start;
FVector End;

// Results will be stored here
TArray<FHitResult> HitResults;

bool bHit = GetWorld()->LineTraceMultiByChannel(
	HitResults,                                  // Hit results
	Start,                                       // Start of the trace
	End,                                         // End of the trace
	ECollisionChannel::ECC_Visibility            // Trace channel
);
```

## Get Actor Of Class

![get_actor_of_class](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/0d699f2c-8f28-41c5-beca-375b20d6d84e)

.h File
```cpp
private:
	// The class needs to be set in blueprint
	UPROPERTY(EditAnywhere, meta = (AllowPrivateAccess = "true"))
	TSubclassOf<AActor> ActorClass;
```

.cpp File
```cpp
#include "Kismet/GameplayStatics.h"

// First found actor
AActor* Actor;

if (ActorClass)
{
	Actor = UGameplayStatics::GetActorOfClass(
		this,                               // World context object
		ActorClass                          // Actor class
	);
}
```

## Get All Actors Of Class

![get_all_actors_of_class](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/7541737c-afa4-457b-ab9c-870d8c2a19f0)

.h File
```cpp
private:
	// The class needs to be set in blueprint
	UPROPERTY(EditAnywhere, meta = (AllowPrivateAccess = "true"))
	TSubclassOf<AActor> ActorClass;
```

.cpp File
```cpp
#include "Kismet/GameplayStatics.h"

// Result will be stored here
TArray<AActor*> Actors;

if (ActorClass)
{
	UGameplayStatics::GetAllActorsOfClass(
		this,                           // World context object
		ActorClass,                     // Actor class
		Actors                          // (Output) Result
	);
}
```

## Get All Actors with Tag

![get_all_actors_with_tag](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/d1cc4737-9fff-4539-819a-d9c31f118631)

```cpp
#include "Kismet/GameplayStatics.h"

// Result will be stored in this array
TArray<AActor*> Actors;

UGameplayStatics::GetAllActorsWithTag(
	this,                           // World context object
	"ExampleTag",                   // Tag name
	Actors                          // (Output) Result
);
```

## Spawn Actor from Class

![spawn_actor_from_class](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/6683dcff-7954-41ea-b6ae-c712fc7086ac)

.h File
```cpp
private:
	// The actor class needs to be set in blueprint
	UPROPERTY(EditAnywhere, meta = (AllowPrivateAccess = "true"))
	TSubclassOf<AActor> ActorClass;
```

.cpp File
```cpp
AActor* SpawnedActor;
FVector Location;
FRotator Rotation;
FActorSpawnParameters SpawnParameters;

if (ActorClass)
{
	SpawnedActor = GetWorld()->SpawnActor<AActor>(
		ActorClass,               // Actor class
		Location,                 // Spawn location
		Rotation,                 // Spawn rotation
		SpawnParameters           // Spawn parameters
	);
}
```

## Play Sound 2D

![play_sound_2d](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/71ad88a6-e375-4a67-bf55-9788352f282a)

.h File
```cpp
private:
	// The sound needs to be set in blueprint
	UPROPERTY(EditAnywhere, meta = (AllowPrivateAccess = "true"))
	USoundBase* ExampleSound;
```

.cpp File
```cpp
#include "Kismet/GameplayStatics.h"

if (ExampleSound)
{
	UGameplayStatics::PlaySound2D(
		this,                   // World context object
		ExampleSound,           // Sound
		1.0f,                   // Volume multiplier
		1.0f                    // Pitch multiplier
	);
}
```

## Play Sound at Location

![play_sound_at_location](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/6c02a8fa-e6aa-4095-9ed7-bf190787334d)

.h File
```cpp
private:
	// The sound needs to be set in blueprint
	UPROPERTY(EditAnywhere, meta = (AllowPrivateAccess = "true"))
	USoundBase* ExampleSound;
```

.cpp File
```cpp
#include "Kismet/GameplayStatics.h"

FVector Location;

if (ExampleSound)
{
	UGameplayStatics::PlaySoundAtLocation(
		this,                           // World context object
		ExampleSound,                   // Sound
		Location,                       // Location
		1.0f,                           // Volume multiplier
		1.0f                            // Pitch multiplier
	);
}
```

## Apply Damage

![apply_damage](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/145bd299-a6b3-4f3f-a6b0-1595f3bfef5c)

```cpp
#include "Kismet/GameplayStatics.h"

AController* EventInstigator;
AActor* DamagedActor;
AActor* DamageCauser;

UGameplayStatics::ApplyDamage(
	DamagedActor,                  // Damaged actor
	100.0f,                        // Damage amount
	EventInstigator,               // Instigator
	DamageCauser,                  // Damage causer
	UDamageType::StaticClass()     // Damage type
);
```

## Apply Radial Damage

![apply_radial_damage](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/301f1027-7c78-48ed-9184-99f1f98912f5)

```cpp
#include "Kismet/GameplayStatics.h"

FVector Origin;
AActor* DamageCauser;
AController* EventInstigator;

UGameplayStatics::ApplyRadialDamage(
	this,                          // World context object
	100.0f,                        // Damage amount
	Origin,                        // Damage location
	200.0f,                        // Damage radius
	UDamageType::StaticClass(),    // Damage type
	TArray<AActor*>(),             // Ignored actors
	DamageCauser,                  // Damage causer
	EventInstigator,               // Instigator
	false                          // Do full damage?
);
```

## Get Game Mode

![get_game_mode](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/551eb2ec-e355-40f1-9806-cd8c4f5c125c)

```cpp
#include "Kismet/GameplayStatics.h"

AGameModeBase* GameMode = UGameplayStatics::GetGameMode(this);
```

## Get Game State

![get_game_state](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/f5ca4328-10be-4dc7-8020-40bbe4d66b7d)

```cpp
#include "Kismet/GameplayStatics.h"

AGameStateBase* GameState = UGameplayStatics::GetGameState(this);
```

## Project World to Screen

![project_world_to_screen](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/505ba30c-f055-43af-af9b-cd3baa6753b8)

```cpp
#include "Kismet/GameplayStatics.h"

// Get player controller
APlayerController* PlayerController = UGameplayStatics::GetPlayerController(this, 0);

FVector WorldPosition;

// Result is stored in this vector
FVector2D ScreenPosition;

UGameplayStatics::ProjectWorldToScreen(
	PlayerController,                  // Target player
	WorldPosition,                     // World position
	ScreenPosition,                    // (Output) Screen position
	false                              // Player viewport relative?
);
```

## Deproject Screen to World

![deproject_screen_to_world](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/81d761bd-ca33-4885-aa1a-bb74ed88d65d)

```cpp
#include "Kismet/GameplayStatics.h"

// Get player controller
APlayerController* PlayerController = UGameplayStatics::GetPlayerController(this, 0);

FVector2D ScreenPosition;

// Result is stored in these vectors
FVector WorldPosition;
FVector WorldDirection;

UGameplayStatics::DeprojectScreenToWorld(
	PlayerController,                  // Target player
	ScreenPosition,                    // Screen position
	WorldPosition,                     // (Output) World position
	WorldDirection                     // (Output) World direction
);
```

## Open Level (by Name)

![open_level_by_name](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/e8ff0289-3754-4a6b-b861-77dc69f343d7)

```cpp
#include "Kismet/GameplayStatics.h"

UGameplayStatics::OpenLevel(
	this,                    // World context object
	"ExampleMap"             // Level name
);
```

## Set Game Paused

![set_game_paused](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/abb42c34-1413-46bc-891f-f3da7e545b37)

```cpp
#include "Kismet/GameplayStatics.h"

bool bPaused;

UGameplayStatics::SetGamePaused(this, bPaused);
```

## Spawn Decal at Location

![spawn_decal_at_location](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/da67d5a2-4401-42fd-a5f4-0bf8ffe6ae76)

.h File
```cpp
private:
	// The material needs to be set in blueprint
	UPROPERTY(EditAnywhere, meta = (AllowPrivateAccess = "true"))
	UMaterialInterface* ExampleMaterial;
```

.cpp File
```cpp
#include "Kismet/GameplayStatics.h"

UDecalComponent* SpawnedDecal;
FVector Size;
FVector Location;
FRotator Rotation;

if (ExampleMaterial)
{
	SpawnedDecal = UGameplayStatics::SpawnDecalAtLocation(
		this,                 // World context object
		ExampleMaterial,      // Decal material
		Size,                 // Decal size
		Location,             // Decal location
		Rotation,             // Decal rotation
		0.0f                  // Life span (0 = infinite)
	);
}
```

## Draw Debug Line

![draw_debug_line](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/ab590515-2e8d-41db-9d80-d91a60cbe587)

```cpp
FVector Start;
FVector End;

DrawDebugLine(
	GetWorld(),        // World object
	Start,             // Start of the line
	End,               // End of the line
	FColor::Red,       // Line color
	false,             // Persistent?
	5.0f,              // Duration
	0,                 // Depth priority
	1.0f               // Line thickness
);
```

## Draw Debug Box

![draw_debug_box](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/811d4bb0-9757-45a3-82f5-4ef4103e1d5b)

```cpp
FVector Center;
FVector Extent;

DrawDebugBox(
	GetWorld(),        // World object
	Center,            // Box center
	Extent,            // Box extent
	FColor::Red,       // Box color
	false,             // Persistent?
	5.0f,              // Duration
	0,                 // Depth priority
	1.0f               // Line thickness
);
```

## Is Valid

![is_valid](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/d057e400-dbcd-4120-b909-0915e16d0215)

Not identical to the blueprint node but used in most cases:
```cpp
AActor* ExampleActor;

// Check validity
if (ExampleActor)
{
	// Is Valid...
}
else
{
	// Is Not Valid...
}
```

Identical to the blueprint node:
```cpp
#include "Kismet/KismetSystemLibrary.h"

AActor* ExampleActor;

// Check validity
if (UKismetSystemLibrary::IsValid(ExampleActor))
{
	// Is Valid...
}
else
{
	// Is Not Valid...
}
```

## Quit Game

![quit_game](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/f980f272-75eb-46d6-958b-f2b0014a4afb)

```cpp
#include "Kismet/GameplayStatics.h"
#include "Kismet/KismetSystemLibrary.h"

// Get player controller
APlayerController* PlayerController = UGameplayStatics::GetPlayerController(this, 0);

// Quit game
UKismetSystemLibrary::QuitGame(
	this,                        // World context object
	PlayerController,            // Quitting player controller
	EQuitPreference::Quit,       // Quit preference
	false                        // Ignore platform restrictions?
);
```
