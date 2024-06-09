# Math

## Min (Int)

![min_int](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/77000cec-1fab-4c82-abee-a187d6b36253)

```cpp
#include "Kismet/KismetMathLibrary.h"

int32 A;
int32 B;

int32 Min = UKismetMathLibrary::Min(A, B);
```

## Max (Int)

![max_int](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/c4200223-e54c-4938-ad44-7e624696b8a2)

```cpp
#include "Kismet/KismetMathLibrary.h"

int32 A;
int32 B;

int32 Max = UKismetMathLibrary::Max(A, B);
```

## Min (Float)

![min_float](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/ce9c8d03-f353-4ed9-a0b2-47ec9bce0e22)

```cpp
#include "Kismet/KismetMathLibrary.h"

float A;
float B;

float Min = UKismetMathLibrary::FMin(A, B);
```

## Max (Float)

![max_float](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/dffbd570-d90b-4687-8737-f55a5a853f90)

```cpp
#include "Kismet/KismetMathLibrary.h"

float A;
float B;

float Max = UKismetMathLibrary::FMax(A, B);
```

## Ceil

![ceil](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/ff0ab4a3-442c-4524-bd8e-bebc54519e9f)

```cpp
float A;

int32 Result = FMath::CeilToInt(A);
```

## Floor

![floor](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/8ac11bbf-e7cd-410f-bb50-7944a4dfbfaf)

```cpp
float A;

int32 Result = FMath::FloorToInt(A);
```

## Absolute

![absolute](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/ffc253c0-d05b-42a1-9317-b182a4194395)

```cpp
int32 A;
int32 Result1 = FMath::Abs(A);

float B;
float Result2 = FMath::Abs(B);
```

## Clamp

![clamp](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/5d84b870-7289-4b4f-917c-c29d323eee59)

```cpp
float A;
float Min;
float Max;

float Result = FMath::Clamp(A, Min, Max);
```

## Lerp

![lerp](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/b7587e23-8e60-40db-85d3-87897c0af860)

```cpp
float A;
float B;
float Alpha;

float Result = FMath::Lerp(A, B, Alpha);
```

## Nearly Equal

![nearly_equal](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/a23b17ae-e2b3-41e9-8c97-f960a36f65b6)

```cpp
float A;
float B;
float ErrorTolerance;

bool Result = FMath::IsNearlyEqual(A, B, ErrorTolerance);
```

## Make Vector

![make_vector](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/3345d020-a2a3-498d-a675-edd13a57fb55)

```cpp
float X;
float Y;
float Z;

FVector ExampleVector(X, Y, Z);
```

## Make Rotator

![make_rotator](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/0e941912-f82f-4dd0-befb-7e19140ae6b2)

```cpp
float Pitch;
float Yaw;
float Roll;

FRotator ExampleRotator(Pitch, Yaw, Roll);
```

## Break Vector

![break_vector](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/b505cc33-9bd6-4970-89b8-5fcf1d7825f7)

You can simply access each variable of a FVector by using `.X`, `.Y` and `.Z`.

```cpp
FVector ExampleVector;

ExampleVector.X;     // X
ExampleVector.Y;     // Y
ExampleVector.Z;     // Z
```

## Break Rotator

![break_rotator](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/ea188d19-643c-41de-9744-b949bb1492f9)

You can simply access each variable of a FRotator by using `.Pitch`, `.Yaw` and `.Roll`.

```cpp
FRotator ExampleRotator;

ExampleRotator.Pitch;    // Pitch
ExampleRotator.Yaw;      // Yaw
ExampleRotator.Roll;     // Roll
```

## Vector Length

![vector_length](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/6f2423f1-01ae-4691-ab5d-8d76d3895e09)

```cpp
FVector ExampleVector;

ExampleVector.Size();
```

## Distance (Vector)

![distance_vector](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/3fe385ac-6a67-4ca8-970e-2fd532d58eb9)

```cpp
FVector A;
FVector B;

FVector::Distance(A, B);
```

## Normalize (Vector)

![normalize_vector](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/cd181aa9-ec20-48de-946f-10ed5baaae44)

```cpp
FVector ExampleVector;

float Tolerance;

// Normalizes the vector in-place
ExampleVector.Normalize(Tolerance);
```

## FInterp To

![finterp_to](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/8a0d579d-a306-4ee1-a7f7-2f64f39188d7)

```cpp
float Current;
float Target;
float DeltaTime;
float InterpSpeed;

float Result = FMath::FInterpTo(Current, Target, DeltaTime, InterpSpeed);
```

## VInterp To

![vinterp_to](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/d68d7223-cc12-4815-a6f6-d20b4f92349b)

```cpp
FVector Current;
FVector Target;
float DeltaTime;
float InterpSpeed;

FVector Result = FMath::VInterpTo(Current, Target, DeltaTime, InterpSpeed);
```

## RInterp To

![rinterp_to](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/f0cf22a5-5e89-44e9-89fe-701c28519973)

```cpp
FRotator Current;
FRotator Target;
float DeltaTime;
float InterpSpeed;

FRotator Result = FMath::RInterpTo(Current, Target, DeltaTime, InterpSpeed);
```

## Find Look at Rotation

![find_look_at_rotation](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/ac23361d-6a4e-4101-af11-49e52e5351e2)

```cpp
#include "Kismet/KismetMathLibrary.h"

FVector Start;
FVector Target;

FRotator Result = UKismetMathLibrary::FindLookAtRotation(Start, Target);
```

## Random Integer

![random_integer](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/9b971e6e-df44-4530-9465-bb9e5c4f5052)

```cpp
#include "Kismet/KismetMathLibrary.h"

int32 Max;

int32 Result = UKismetMathLibrary::RandomInteger(Max);
```

## Random Float

![random_float](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/35a19fd8-9848-4768-9c41-9f4cfd7c11f5)

```cpp
#include "Kismet/KismetMathLibrary.h"

float Result = UKismetMathLibrary::RandomFloat();
```

## Random Integer in Range

![random_integer_in_range](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/967e7c9e-20ad-44de-974b-2af45843826e)

```cpp
#include "Kismet/KismetMathLibrary.h"

int32 Min;
int32 Max;

int32 Result = UKismetMathLibrary::RandomIntegerInRange(Min, Max);
```

## Random Float in Range

![random_float_in_range](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/804bb5c9-d723-4de7-8f02-60bb31fb3614)

```cpp
#include "Kismet/KismetMathLibrary.h"

float Min;
float Max;

float Result = UKismetMathLibrary::RandomFloatInRange(Min, Max);
```
