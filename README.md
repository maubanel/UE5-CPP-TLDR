## Common Specifiers

* UCLASS Specifiers - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/GameplayArchitecture/Classes/Specifiers/)

    `UCLASS(Blueprintable)` 

* UENUM Specifiers - [Docs](https://benui.ca/unreal/uenum-umeta/)
```
    UENUM(BlueprintType) enum class Foo : Uint8
    {
        None = 0 UMETA(DisplayName = "None")...
    }
```

* USTRUCT Specifiers - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/GameplayArchitecture/Structs/Specifiers/)
  
    `USTRUCT(BlueprintType)`
* UPROPERTY Specifiers - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/GameplayArchitecture/Properties/Specifiers/)
  
    `UPROPERTY(VisibleAnywhere, Category = "Foo")`
  
    `UPROPERTY(BlueprintReadOnly, Category = "Foo")`
  
    `UPROPERTY(BlueprintReadWrite, Category = "Foo")` 

## Unreal Specific Coding Hints

* Use `TObjectPtr<ClassName>` intead of raw `*` pointers
* Initialize FStrings with `FString Name = TEXT("This is a a string")` to ensure platform specific encoding

## CPP Coding Hints
* Forward declare in the `.h` and include in the `.cpp` to speed up compile times and limit cross references
