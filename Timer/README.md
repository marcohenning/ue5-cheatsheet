# Timer

## Set Timer by Function Name

```cpp
#include "TimerManager.h"

FTimerHandle TimerHandle;

GetWorldTimerManager().SetTimer(
	TimerHandle,                          // Timer handle
	this,                                 // Object to call the timer function on
	&AExampleCharacter::ExampleMethod,    // Method to call the timer function on
	3.0f,                                 // Delay (in seconds)
	false                                 // Loop timer?
);
```

## Set Timer by Event

There is no equivalent to events in C++, so you set timers by function name instead.
See: `Set Timer by Function Name`

## Clear and Invalidate Timer by Handle

```cpp
#include "TimerManager.h"

FTimerHandle ExampleTimerHandle;

// Clear and invalidate timer handle
GetWorldTimerManager().ClearTimer(ExampleTimerHandle);
```

## Clear Timer by Function Name

There is no equivalent to this node in C++, so you clear timers by handle instead.
See: `Clear and Invalidate Timer by Handle`

## Invalidate Timer Handle

```cpp
FTimerHandle ExampleTimerHandle;

ExampleTimerHandle.Invalidate();
```
