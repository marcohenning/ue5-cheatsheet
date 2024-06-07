# Basics

## Branch

![branch](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/e687fde3-e7b6-4136-97d8-eb79f2dcf740)

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

![for_loop](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/8b084c5c-9114-4666-a0bd-3cad1ce2e35e)

```cpp
for (int32 i = 0; i <= 10; i++)
{
	// Loop Body...
}
```

## For Loop with Break

![for_loop_break](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/734dbab8-19ea-41a6-822d-02465742d47b)

```cpp
bool ExampleBreakCondition;

for (int32 i = 0; i <= 10; i++)
{
	if (ExampleBreakCondition) { break; }
	// Loop Body...
}
```

## For Each Loop

![for_each_loop](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/4c7d8868-2ca5-4858-a745-47e3286359ad)

```cpp
TArray<int32> ExampleArray;

for (int32 Element : ExampleArray)
{
	// Loop Body...
}
```

## For Each Loop with Break

![for_each_loop_break](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/bd61fbb2-9c02-45a1-9d59-cf9190d42f52)

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

![while_loop](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/8d72bfc5-9f90-4e65-a257-870fb5b2ddb7)

```cpp
bool ExampleCondition;

while (ExampleCondition)
{
	// Loop Body...
}
```

## Flip Flop

![flip_flop](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/75e2e317-f4b0-4cd5-a333-5dc444c859c6)

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

![cast_to](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/5ea906b6-8c8a-4cf6-a84d-a32877da5bca)

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
