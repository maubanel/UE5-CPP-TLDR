## Common Specifiers

* UCLASS Specifiers - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/GameplayArchitecture/Classes/Specifiers/)

    `UCLASS(Blueprintable)` 

* USTRUCT Specifiers - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/GameplayArchitecture/Structs/Specifiers/)
  
```
    #include "Grid.generated.h"

    USTRUCT(BlueprintType)
    ustruct FGrid
{
    GENERATED BODY()

    FORCELINE FGrid;
    explicit FORCEINLINE FGrid(int32 Value);
    explicit FORCE INLINE FGrid (In32 X, Int32 Y);

    //... add properties here
    //... No UFUNCTIONS allowed but can use non-blueprintable functions
};
```

* UENUM Specifiers - [Docs](https://benui.ca/unreal/uenum-umeta/)
```
    UENUM(BlueprintType) enum class Foo : Uint8
    {
        None = 0 UMETA(DisplayName = "None")...
    }
```

* UPROPERTY Specifiers - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/GameplayArchitecture/Properties/Specifiers/)
  
    `UPROPERTY(VisibleAnywhere, Category = "Foo")`
  
    `UPROPERTY(BlueprintReadOnly, Category = "Foo")`
  
    `UPROPERTY(BlueprintReadWrite, Category = "Foo")` 

## Unreal Specific Coding Hints

* Use `TObjectPtr<ClassName>` intead of raw `*` pointers
* Initialize FStrings with `FString Name = TEXT("This is a a string");` to ensure platform specific encoding
* Use `check(pointer)` if you want the game to stop and assert on a null pointer (if that pointer is NOT supposed to be null).  Otherwise a non-breaking way is to use `if (IsValid(pointer)){//... do something}` - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/ProgrammingWithCPP/Assertions/)

## CPP Coding Hints
* Forward declare in the `.h` and include in the `.cpp` to speed up compile times and limit cross reference errors
* Initialize variables using the initilazation methode so use `int32 X{5};` instead of `int32 X = 5;`
