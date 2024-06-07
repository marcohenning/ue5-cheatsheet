# AActor

## Event BeginPlay

![event_beginplay](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/448e4095-4385-4fa6-b095-3890eb46a7b4)

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

![event_tick](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/ed6844ae-92c0-47c8-af89-f18625c6d287)

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

![set_actor_location](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/2148dae7-d628-44c5-bf2b-73f41dab5281)

```cpp
AActor* ExampleActor;

FVector NewLocation;

ExampleActor->SetActorLocation(NewLocation);
```

## Set Actor Rotation

![set_actor_rotation](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/335ced1e-4edd-4a52-9ec4-f06d9d971189)

```cpp
AActor* ExampleActor;

FRotator NewRotation;

// Convert FRotator to FQuat and set actor rotation
ExampleActor->SetActorRotation(FQuat::MakeFromRotator(NewRotation));
```

## Set Actor Scale 3D

![set_actor_scale_3d](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/39b2bc03-5b67-4fe2-9e37-4c2dfef77de4)

```cpp
AActor* ExampleActor;

FVector NewScale3D;

ExampleActor->SetActorScale3D(NewScale3D);
```

## Set Actor Transform

![set_actor_transform](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/81a18215-7487-4db9-bcfe-1cb7bca55dfc)

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

![set_actor_hidden_in_game](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/f1c25431-9226-4749-8c34-8db4bf811431)

```cpp
AActor* ExampleActor;

bool bHideActor;

ExampleActor->SetActorHiddenInGame(bHideActor);
```

## Destroy Actor

![destroy_actor](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/361abba1-842e-42a0-a7f3-1857b1395c7f)

```cpp
AActor* ExampleActor;

ExampleActor->Destroy();
```
