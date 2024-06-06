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

```cpp
```

## Spawn Emitter Attached

```cpp
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

```cpp
```

## Get All Actors Of Class

```cpp
```

## Get All Actors Of Class with Tag

```cpp
```

## Get All Actors with Interface

```cpp
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

## Spawn Sound 2D

```cpp
```

## Spawn Sound at Location

```cpp
```

## Spawn Sound Attached

```cpp
```

## Play Sound 2D

```cpp
```

## Play Sound at Location

```cpp
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

## Apply Point Damage

```cpp
```

## Apply Radial Damage

```cpp
```

## Apply Radial Damage with Falloff

```cpp
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

```cpp
```

## Spawn Decal Attached

```cpp
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
