## Common Specifiers

* UCLASS Specifiers - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/GameplayArchitecture/Classes/Specifiers/)

    `UCLASS(Blueprintable)` 

* USTRUCT Specifiers - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/GameplayArchitecture/Structs/Specifiers/)
  
```
    #include "Grid.generated.h"

    USTRUCT(BlueprintType)
    struct FGrid
{
    GENERATED BODY()

    FORCELINE FGrid();
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

* UFUNCTION Specifiers - [Docs](https://benui.ca/unreal/ufunction/)
```
    UFUNCTION(BLueprintCallable, Category = "Cat")
    // Change a reference in blueprint to an input pin and maintain writability
      UFUNCTION(BLueprintCallable, Category = "Cat")
      static void Foo(UPARAM(ref) AActor& Actor);
```
* UPROPERTY Specifiers - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/GameplayArchitecture/Properties/Specifiers/)
  
    `UPROPERTY(VisibleAnywhere, Category = "Foo")`
  
    `UPROPERTY(BlueprintReadOnly, Category = "Foo")`
  
    `UPROPERTY(BlueprintReadWrite, Category = "Foo")`

## Enumerators
* Access Display Name of UENUM in Unreal: `UEnum::GetValueAsString(BuildingName);`

## Unreal Specific Coding Hints

* Use `TObjectPtr<ClassName>` intead of raw `*` pointers for UPROPERTIES
* Initialize FStrings with `FString Name = TEXT("This is a a string");` to ensure platform specific encoding
* Use `check(pointer)` if you want the game to stop and assert on a null pointer (if that pointer is NOT supposed to be null).  Otherwise a non-breaking way is to use `if (IsValid(pointer)){//... do something}` - [Docs](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/ProgrammingWithCPP/Assertions/)

## CPP Coding Hints
* Forward declare in the `.h` and include in the `.cpp` to speed up compile times and limit cross reference errors
* Initialize variables using the initilazation methode so use `int32 X{5};` instead of `int32 X = 5;`
* Use bitfields for booleans `uint8 bIsFoo:1` if there are lots of booleans in a class/struct but then you cannot initialize without c++ 20 (not supported in Unreal)

## Debug Printing
`if (GEngine) GEngine->AddOnScreenDebugMessage(-1, 1.0f, FColor::Yellow, TEXT("Write simple message here"));`<br>
`if (GEngine) GEngine->AddOnScreenDebugMessage(-1, 1.0f, FColor::Yellow, FString::Printf(TEXT("Write message with vars: %d"), IntegerVar));`<br>
 `UE_LOG(LogTemp, Warning, TEXT("Text: %s"), *(ID.ToString()));`

## Error Messages
 * Customize error category in project.h file in Source
   ![twin h](https://github.com/maubanel/UE5-CPP-TLDR/assets/5504953/a03a91e5-eaa0-4c98-8705-ad7318d1a286)

## Links
* Parsing JSON: https://gist.github.com/hanzochang/07eba255ce0d1695582a92e98e973200

## TArrays
* `TArray <FSTring> Foo;`
*  Loop through entire array: `for (auto Foo : Foos);`

## Casts
*  `APawn* MyPawn = Cast<APawn>(MyActor);`

## Custom Log Category
* Project name.cpp or plugin name.cpp (in Source | Private) at the bottom after #undef: `DEFINE_LOG_CATEGORY(NameOfUELog);` (NameOfUELog is the log name you want to give and needs to be the same as in the name.h file.
* Project name.h or plugin name.h (in Source | Plublic)  at the top after #includes: `DECLARE_LOG_CATEGORY_EXTERN(NameOfUELog, Log, All)` (NameOfUELog is the log name you want to give)
