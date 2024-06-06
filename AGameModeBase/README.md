# AGameModeBase

## Event OnPostLogin

.h File
```cpp
public:
	// This method gets called every time a user logs in
	virtual void PostLogin(APlayerController* NewPlayer) override;
```

.cpp File
```cpp
void ExampleGameMode::PostLogin(APlayerController* NewPlayer)
{
	Super::PostLogin(NewPlayer);

	// Your code here...
}
```

## Event OnLogout

.h File
```cpp
public:
	// This method gets called every time a user logs out
	virtual void Logout(AController* Exiting) override;
```

.cpp File
```cpp
void ExampleGameMode::Logout(AController* Exiting)
{
	// Your code here...
}
```
