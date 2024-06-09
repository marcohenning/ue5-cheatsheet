# Components

## Play Animation

![play_animation](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/597e01a3-dcd5-4a5a-ba41-a6fb13392a85)

.h File
```cpp
private:
	// The animation asset needs to be set in blueprint
	UPROPERTY(EditAnywhere, meta = (AllowPrivateAccess = "true"))
	class UAnimationAsset* ExampleAnimation;
```

.cpp File
```cpp
USkeletalMeshComponent* ExampleComponent;

if (ExampleAnimation)
{
	ExampleComponent->PlayAnimation(
		ExampleAnimation,         // Animation asset
		false                     // Loop animation?
	);
}
```

## Set Relative Location

![set_relative_location](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/8f4902d0-0681-49cc-989e-2ab1c6355652)

```cpp
USkeletalMeshComponent* ExampleComponent;

FVector NewLocation;

ExampleComponent->SetRelativeLocation(NewLocation);
```

## Set World Location

![set_world_location](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/5302daff-501e-41b6-89b3-e677e79a948e)

```cpp
USkeletalMeshComponent* ExampleComponent;

FVector NewLocation;

ExampleComponent->SetWorldLocation(NewLocation);
```

## Set Relative Rotation

![set_relative_rotation](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/43178a81-d20a-4ab4-b9fd-43319df693c8)

```cpp
USkeletalMeshComponent* ExampleComponent;

FRotator NewRotation;

// Convert FRotator to FQuat and set relative rotation
ExampleComponent->SetRelativeRotation(FQuat::MakeFromRotator(NewRotation));
```

## Set World Rotation

![set_world_rotation](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/c98603a9-e6ae-4027-a729-1f98a6e15b50)

```cpp
USkeletalMeshComponent* ExampleComponent;

FRotator NewRotation;

// Convert FRotator to FQuat and set world rotation
ExampleComponent->SetWorldRotation(FQuat::MakeFromRotator(NewRotation));
```
