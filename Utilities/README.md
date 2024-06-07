# Utilities

## Delay

There is no equivalent to the delay node in C++, so timers are used instead.
If you want to execute code after a specific delay, put that code into a function and then start a timer with the desired delay.
See: `Set Timer by Function Name`

## Print String

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

```cpp
#include "Kismet/GameplayStatics.h"

APlayerController* PlayerController = UGameplayStatics::GetPlayerController(this, 0);
```

## Get Player Camera Manager

```cpp
#include "Kismet/GameplayStatics.h"

APlayerCameraManager* PlayerCameraManager = UGameplayStatics::GetPlayerCameraManager(this, 0);
```

## Spawn Emitter at Location

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

.h File
```cpp
private:
	// The actor class needs to be set in blueprint
	UPROPERTY(EditAnywhere, meta = (AllowPrivateAccess = "true"))
	TSubclassOf<AActor> ActorClass;
```

.cpp File
```cpp
FVector Location;
FRotator Rotation;
FActorSpawnParameters SpawnParameters;

if (ActorClass)
{
	GetWorld()->SpawnActor<AActor>(
		ActorClass,               // Actor class
		Location,                 // Spawn location
		Rotation,                 // Spawn rotation
		SpawnParameters           // Spawn parameters
	);
}
```

## Play Sound 2D

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

```cpp
#include "Kismet/GameplayStatics.h"

AGameModeBase* GameMode = UGameplayStatics::GetGameMode(this);
```

## Get Game State

```cpp
#include "Kismet/GameplayStatics.h"

AGameStateBase* GameState = UGameplayStatics::GetGameState(this);
```

## Project World to Screen

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

```cpp
#include "Kismet/GameplayStatics.h"

UGameplayStatics::OpenLevel(
	this,                    // World context object
	"ExampleMap"             // Level name
);
```

## Set Game Paused

```cpp
#include "Kismet/GameplayStatics.h"

bool bPaused;

UGameplayStatics::SetGamePaused(this, bPaused);
```

## Spawn Decal at Location

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
