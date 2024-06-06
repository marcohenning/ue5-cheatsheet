# Basics

## Branch

```cpp
bool ExampleCondition;

if (ExampleCondition)
{
	// True...
}
else
{
	// False...
}
```

## For Loop

```cpp
for (int32 i = 0; i <= 10; i++)
{
	// Loop Body...
}
```

## For Loop with Break

```cpp
bool ExampleBreakCondition;

for (int32 i = 0; i <= 10; i++)
{
	if (ExampleBreakCondition) { break; }
	// Loop Body...
}
```

## For Each Loop

```cpp
TArray<int32> ExampleArray;

for (int32 Element : ExampleArray)
{
	// Loop Body...
}
```

## For Each Loop with Break

```cpp
TArray<int32> ExampleArray;

bool ExampleBreakCondition;

for (int32 Element : ExampleArray)
{
	if (ExampleBreakCondition) { break; }
	// Loop Body...
}
```

## While Loop

```cpp
bool ExampleCondition;

while (ExampleCondition)
{
	// Loop Body...
}
```

## Flip Flop

.h File
```cpp
private:
	bool IsA = true;
```

.cpp File
```cpp
if (IsA)
{
	// A...
}
else
{
	// B...
}
IsA = !IsA;
```

## Cast To

```cpp
AActor* ExampleActor;

// Casting: <> = Type to cast to, () = Object to cast
ACharacter* ExampleCharacter = Cast<ACharacter>(ExampleActor);

if (ExampleCharacter)
{
	// Cast Succeeded...
}
else
{
	// Cast Failed...
}
```
