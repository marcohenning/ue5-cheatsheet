# User Interface

## Create Widget

Make sure `"UMG"` is included as a dependency in the Build.cs file.

.h File
```cpp
private:
	// The specific user widget needs to be set in blueprint
	UPROPERTY(EditAnywhere, meta = (AllowPrivateAccess = "true"))
	TSubclassOf<UUserWidget> ExampleWidgetClass;
```

.cpp File
```cpp
#include "Blueprint/UserWidget.h"

if (ExampleWidgetClass)
{
	// Create widget
	UUserWidget* ExampleWidget = CreateWidget<UUserWidget>(GetWorld(), ExampleWidgetClass);
}
```

## Add to Viewport

Make sure `"UMG"` is included as a dependency in the Build.cs file.

```cpp
#include "Blueprint/UserWidget.h"

UUserWidget* ExampleWidget;

ExampleWidget->AddToViewport();
```

## Set Input Mode Game Only

```cpp
#include "Kismet/GameplayStatics.h"

// Get player controller
APlayerController* PlayerController = UGameplayStatics::GetPlayerController(this, 0);

if (PlayerController)
{
	// Set input mode
	FInputModeGameOnly InputMode;
	PlayerController->SetInputMode(InputMode);
}
```

## Set Input Mode UI Only

```cpp
#include "Kismet/GameplayStatics.h"

// Get player controller
APlayerController* PlayerController = UGameplayStatics::GetPlayerController(this, 0);

if (PlayerController)
{
	// Set input mode
	FInputModeUIOnly InputMode;
	PlayerController->SetInputMode(InputMode);
}
```

## Set Input Mode Game and UI

```cpp
#include "Kismet/GameplayStatics.h"

// Get player controller
APlayerController* PlayerController = UGameplayStatics::GetPlayerController(this, 0);

if (PlayerController)
{
	// Set input mode
	FInputModeGameAndUI InputMode;
	PlayerController->SetInputMode(InputMode);
}
```
