# User Interface

## Create Widget

![create_widget](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/cd6df316-fb57-489c-82c8-ea4031aac8f4)

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

![add_to_viewport](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/5ce9b6d4-4a85-4209-8108-0fd73cf3cefd)

Make sure `"UMG"` is included as a dependency in the Build.cs file.

```cpp
#include "Blueprint/UserWidget.h"

UUserWidget* ExampleWidget;

ExampleWidget->AddToViewport();
```

## Set Input Mode Game Only

![set_input_mode_game_only](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/b722ab7c-7cc5-440b-a9c9-277318c73fc5)

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

![set_input_mode_ui_only](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/8d3540e0-21b0-4bb0-97e1-6b1ff912a6c2)

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

![set_input_mode_game_and_ui](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/33c6c6a3-7a66-4ef9-bf21-a4685b79c621)

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
