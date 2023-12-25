## Common Specifiers
* `UCLASS(Blueprintable)` - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/GameplayArchitecture/Classes/Specifiers/)
* `UPROPERTY(

## Unreal Specific Coding Hints

* Use `TObjectPtr<ClassName>` intead of raw `*` pointers
* Initialize FStrings with `FString Name = TEXT("This is a a string")

## CPP Coding Hints
* Forward declare in the `.h` and include in the `.cpp` to speed up compile times and limit cross references
