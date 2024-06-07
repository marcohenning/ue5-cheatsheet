# AGameModeBase

## Event OnPostLogin

![event_login](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/4462ae77-4c8a-46ef-bf2d-10e42bd0d960)

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

![event_logout](https://github.com/marcohenning/ue5-cheatsheet/assets/91918460/9d22ba61-ce4b-425a-8ccd-d07075c84b76)

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
