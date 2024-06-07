# Timer

## Set Timer by Function Name

![set_timer_by_function_name](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/62ef21a4-13a2-4548-852c-2db016122496)

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

![set_timer_by_event](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/61cac459-b4fa-4d0b-a44d-ecff6b1c9cbc)

There is no equivalent to events in C++, so you set timers by function name instead.
See: `Set Timer by Function Name`

## Clear and Invalidate Timer by Handle

![clear_and_invalidate_timer_by_handle](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/46aa7911-c1a9-4a26-b35a-d86ffe9701a3)

```cpp
#include "TimerManager.h"

FTimerHandle ExampleTimerHandle;

// Clear and invalidate timer handle
GetWorldTimerManager().ClearTimer(ExampleTimerHandle);
```

## Clear Timer by Function Name

![clear_timer_by_function_name](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/59f234a8-f398-4d58-abf4-618311330eb9)

There is no equivalent to this node in C++, so you clear timers by handle instead.
See: `Clear and Invalidate Timer by Handle`

## Invalidate Timer Handle

![invalidate_timer_handle](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/0ee4ba44-3f51-4292-be29-1c4e50c03910)

```cpp
FTimerHandle ExampleTimerHandle;

ExampleTimerHandle.Invalidate();
```
