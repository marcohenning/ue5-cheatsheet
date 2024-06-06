# Components

## Play Animation

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

```cpp
USkeletalMeshComponent* ExampleComponent;

FVector NewLocation;

ExampleComponent->SetRelativeLocation(NewLocation);
```

## Set World Location

```cpp
USkeletalMeshComponent* ExampleComponent;

FVector NewLocation;

ExampleComponent->SetWorldLocation(NewLocation);
```

## Set Relative Rotation

```cpp
USkeletalMeshComponent* ExampleComponent;

FRotator NewRotation;

// Convert FRotator to FQuat and set relative rotation
ExampleComponent->SetRelativeRotation(FQuat::MakeFromRotator(NewRotation));
```

## Set World Rotation

```cpp
USkeletalMeshComponent* ExampleComponent;

FRotator NewRotation;

// Convert FRotator to FQuat and set world rotation
ExampleComponent->SetWorldRotation(FQuat::MakeFromRotator(NewRotation));
```
