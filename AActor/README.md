# AActor

## Event BeginPlay

.h File
```cpp
protected:
	virtual void BeginPlay() override;
```

.cpp File
```cpp
void AExampleActor::BeginPlay()
{
	Super::BeginPlay();

	// Your code here...
}
```

## Event Tick

Make sure that `PrimaryActorTick.bCanEverTick` is set to `true` in the constructor, so the tick function will be called.

.h File
```cpp
public:
	virtual void Tick(float DeltaTime) override;
```

.cpp File
```cpp
void AExampleActor::Tick(float DeltaTime)
{
	Super::Tick(DeltaTime);

	// Your code here...
}
```

## Set Actor Location

```cpp
AActor* ExampleActor;

FVector NewLocation;

ExampleActor->SetActorLocation(NewLocation);
```

## Set Actor Rotation

```cpp
AActor* ExampleActor;

FRotator NewRotation;

// Convert FRotator to FQuat and set actor rotation
ExampleActor->SetActorRotation(FQuat::MakeFromRotator(NewRotation));
```

## Set Actor Scale 3D

```cpp
AActor* ExampleActor;

FVector NewScale3D;

ExampleActor->SetActorScale3D(NewScale3D);
```

## Set Actor Transform

```cpp
AActor* ExampleActor;

FVector NewLocation;
FRotator NewRotation;
FVector NewScale3D;

// Create FTransform (rotation, location and scale)
FTransform NewTransform(NewRotation, NewLocation, NewScale3D);

ExampleActor->SetActorTransform(NewTransform);
```

## Set Actor Hidden In Game

```cpp
AActor* ExampleActor;

bool bHideActor;

ExampleActor->SetActorHiddenInGame(bHideActor);
```

## Destroy Actor

```cpp
AActor* ExampleActor;

ExampleActor->Destroy();
```
