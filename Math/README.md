# Math

## Min (Int)

```cpp
#include "Kismet/KismetMathLibrary.h"

int32 A;
int32 B;

int32 Min = UKismetMathLibrary::Min(A, B);
```

## Max (Int)

```cpp
#include "Kismet/KismetMathLibrary.h"

int32 A;
int32 B;

int32 Max = UKismetMathLibrary::Max(A, B);
```

## Min (Float)

```cpp
#include "Kismet/KismetMathLibrary.h"

float A;
float B;

float Min = UKismetMathLibrary::FMin(A, B);
```

## Max (Float)

```cpp
#include "Kismet/KismetMathLibrary.h"

float A;
float B;

float Max = UKismetMathLibrary::FMax(A, B);
```

## Ceil

```cpp
#include "Kismet/KismetMathLibrary.h"

float A;

int32 Result = UKismetMathLibrary::FCeil(A);
```

## Floor

```cpp
#include "Kismet/KismetMathLibrary.h"

float A;

int32 Result = UKismetMathLibrary::FFloor(A);
```

## Absolute (Int)

```cpp
#include "Kismet/KismetMathLibrary.h"

int32 A;

int32 Result = UKismetMathLibrary::Abs_Int(A);
```

## Absolute (Float)

```cpp
#include "Kismet/KismetMathLibrary.h"

float A;

float Result = UKismetMathLibrary::Abs(A);
```

## Clamp

```cpp
float A;
float Min;
float Max;

float Result = FMath::Clamp(A, Min, Max);
```

## Lerp

```cpp
float A;
float B;
float Alpha;

float Result = FMath::Lerp(A, B, Alpha);
```

## Nearly Equal

```cpp
float A;
float B;
float ErrorTolerance;

bool Result = FMath::IsNearlyEqual(A, B, ErrorTolerance);
```

## Make Vector

```cpp
float X;
float Y;
float Z;

FVector ExampleVector(X, Y, Z);
```

## Make Rotator

```cpp
float Pitch;
float Yaw;
float Roll;

FRotator ExampleRotator(Pitch, Yaw, Roll);
```

## Break Vector

You can simply access each variable of a FVector by using `.X`, `.Y` and `.Z`.

```cpp
FVector ExampleVector;

ExampleVector.X;     // X
ExampleVector.Y;     // Y
ExampleVector.Z;     // Z
```

## Break Rotator

You can simply access each variable of a FRotator by using `.Pitch`, `.Yaw` and `.Roll`.

```cpp
FRotator ExampleRotator;

ExampleRotator.Pitch;    // Pitch
ExampleRotator.Yaw;      // Yaw
ExampleRotator.Roll;     // Roll
```

## Vector Length

```cpp
FVector ExampleVector;

ExampleVector.Size();
```

## Distance (Vector)

```cpp
FVector A;
FVector B;

FVector::Distance(A, B);
```

## Normalize (Vector)

```cpp
FVector ExampleVector;

float Tolerance;

// Normalizes the vector in-place
ExampleVector.Normalize(Tolerance);
```

## FInterp To

```cpp
float Current;
float Target;
float DeltaTime;
float InterpSpeed;

float Result = FMath::FInterpTo(Current, Target, DeltaTime, InterpSpeed);
```

## VInterp To

```cpp
FVector Current;
FVector Target;
float DeltaTime;
float InterpSpeed;

FVector Result = FMath::VInterpTo(Current, Target, DeltaTime, InterpSpeed);
```

## RInterp To

```cpp
FRotator Current;
FRotator Target;
float DeltaTime;
float InterpSpeed;

FRotator Result = FMath::RInterpTo(Current, Target, DeltaTime, InterpSpeed);
```

## Find Look at Rotation

```cpp
#include "Kismet/KismetMathLibrary.h"

FVector Start;
FVector Target;

FRotator Result = UKismetMathLibrary::FindLookAtRotation(Start, Target);
```

## Random Integer

```cpp
#include "Kismet/KismetMathLibrary.h"

int32 Max;

int32 Result = UKismetMathLibrary::RandomInteger(Max);
```

## Random Float

```cpp
#include "Kismet/KismetMathLibrary.h"

float Result = UKismetMathLibrary::RandomFloat();
```

## Random Integer in Range

```cpp
#include "Kismet/KismetMathLibrary.h"

int32 Min;
int32 Max;

int32 Result = UKismetMathLibrary::RandomIntegerInRange(Min, Max);
```

## Random Float in Range

```cpp
#include "Kismet/KismetMathLibrary.h"

float Min;
float Max;

float Result = UKismetMathLibrary::RandomFloatInRange(Min, Max);
```
