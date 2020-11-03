---
description: Beschrijft een tref woord dat een afsluit fout verwerkt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_trap?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Trap
ms.openlocfilehash: 88c16066b96912faf38fd48a3bd2f84572707e4c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252204"
---
# <a name="about-trap"></a>Over trap

## <a name="short-description"></a>Korte beschrijving

Beschrijft een tref woord dat een afsluit fout verwerkt.

## <a name="long-description"></a>Lange beschrijving

Een afsluit fout zorgt ervoor dat een instructie niet kan worden uitgevoerd. Als Power shell geen afsluit fout op een of andere manier verwerkt, stopt Power shell ook met het uitvoeren van de functie of het script in de huidige pijp lijn. In andere talen, zoals C#, worden afsluit fouten ook wel uitzonde ringen genoemd.

Met het `trap` sleutel woord wordt een lijst met instructies opgegeven die moeten worden uitgevoerd wanneer er een afsluit fout optreedt. `trap` instructies verwerken de afsluit fouten op de volgende manieren:

- De fout weer geven na het verwerken `trap` van het instructie blok en de uitvoering van het script of de functie die de bevat, voortzetten `trap` . Dit is de standaardinstelling.

- De fout weer geven en de uitvoering van het script of de functie die de `trap` gebruiken `break` in de-instructie bevat afbreken `trap` .

- Stilte de fout, maar ga door met het uitvoeren van het script of de functie die de `trap` door gebruikt `continue` in de- `trap` instructie.

De instructie lijst van `trap` kan meerdere voor waarden of functie aanroepen bevatten. Een `trap` kan Logboeken schrijven, test omstandigheden of zelfs een ander programma uitvoeren.

### <a name="syntax"></a>Syntax

De `trap` instructie heeft de volgende syntaxis:

```powershell
trap [[<error type>]] {<statement list>}
```

De `trap` instructie bevat een lijst met instructies die moeten worden uitgevoerd wanneer er een afsluit fout optreedt. Een `trap` instructie bestaat uit het `trap` tref woord, eventueel gevolgd door een type-expressie, en het instructie blok met de lijst met instructies die moeten worden uitgevoerd wanneer een fout wordt onderschept. De type-expressie verfijnt de typen fouten die de `trap` vangsten opleveren.

Een script of opdracht kan meerdere `trap` instructies hebben. `trap` instructies kunnen ergens in het script of de opdracht worden weer gegeven.

### <a name="trapping-all-terminating-errors"></a>Alle afsluit fouten worden overgevuld

Wanneer er een afsluit fout optreedt die niet op een andere manier wordt verwerkt in een script of opdracht, controleert Power shell op een `trap` instructie die de fout verwerkt. Als er een `trap` instructie aanwezig is, gaat Power shell door met het uitvoeren van het script of de opdracht in de `trap` instructie.

Het volgende voor beeld is een zeer eenvoudige `trap` instructie:

```powershell
trap {"Error found."}
```

Deze `trap` instructie overlapt elke afsluit fout.

In het volgende voor beeld bevat de functie een niet-zin teken reeks die een runtime-fout veroorzaakt.

```powershell
function TrapTest {
    trap {"Error found."}
    nonsenseString
}

TrapTest
```

Als u deze functie uitvoert, wordt het volgende geretourneerd:

```Output
Error found.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

Het volgende voor beeld bevat een `trap` instructie waarmee de fout wordt weer gegeven met behulp van de `$_` Automatische variabele:

```powershell
function TrapTest {
    trap {"Error found: $_"}
    nonsenseString
}

TrapTest
```

Als deze versie van de functie wordt uitgevoerd, wordt het volgende geretourneerd:

```Output
Error found: The term 'nonsenseString' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the
name, or if a path was included, verify that the path is correct and try again.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

> [!IMPORTANT]
> `trap` instructies kunnen ergens binnen een bepaald bereik worden gedefinieerd, maar altijd gelden voor alle instructies in dat bereik. Tijdens runtime `trap` worden instructies in een blok gedefinieerd voordat andere instructies worden uitgevoerd. In Java script wordt dit ' [hijsing](https://wikipedia.org/wiki/JavaScript_syntax#hoisting)' genoemd. Dit betekent dat de `trap` instructies van toepassing zijn op alle-instructies in dat blok, zelfs als de uitvoering niet is gevorderd voorbij het punt waarop ze zijn gedefinieerd. Als u bijvoorbeeld een `trap` aan het einde van een script definieert en er een fout optreedt in de eerste instructie, wordt er nog steeds geactiveerd `trap` .

### <a name="trapping-specific-errors"></a>Specifieke fouten overvullen

Een script of opdracht kan meerdere `trap` instructies hebben. A `trap` kan worden gedefinieerd om specifieke fouten te verwerken.

Het volgende voor beeld is een `trap` instructie waarmee de specifieke fout **CommandNotFoundException** wordt onderschept:

```powershell
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
```

Wanneer een functie of script een teken reeks aantreft die niet overeenkomt met een bekende opdracht, wordt in deze `trap` instructie de teken reeks "opdracht fout onderschept" weer gegeven.
Na het uitvoeren van de `trap` instructie lijst, schrijft Power shell het fout object naar de fout stroom en wordt het script voortgezet.

Power shell gebruikt .NET-uitzonderings typen. In het volgende voor beeld wordt het **systeem. uitzonderings** fout type opgegeven:

```powershell
trap [System.Exception] {"An error trapped"}
```

Het **CommandNotFoundException** -fout type neemt over van het type **System. Exception** . Met deze instructie wordt een fout onderschept die wordt gemaakt door een onbekende opdracht. Ook worden andere fout typen onderschept.

U kunt meer dan één `trap` instructie in een script hebben. Elk fout type kan slechts door één instructie worden getrapt `trap` . Wanneer er een afsluit fout optreedt, zoekt Power shell naar de `trap` met de meest specifieke overeenkomst, te beginnen met het huidige bereik van de uitvoering.

Het volgende script voorbeeld bevat een fout. Het script bevat een algemene `trap` instructie waarmee elke afsluit fout wordt onderschept en een specifieke `trap` instructie die het type **CommandNotFoundException** opgeeft.

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException] {
  "Command error trapped"
}
nonsenseString
```

Als u dit script uitvoert, wordt het volgende resultaat gegenereerd:

```Output
Command error trapped
nonsenseString:
Line |
   5 |  nonsenseString
     |  ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

Omdat Power shell geen nonsenseString herkent als een cmdlet of een ander item, wordt een **CommandNotFoundException** -fout geretourneerd. Deze afsluit fout wordt getrapt door de specifieke `trap` instructie.

Het volgende script voorbeeld bevat dezelfde `trap` instructies met een andere fout:

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
1/$null
```

Als u dit script uitvoert, wordt het volgende resultaat gegenereerd:

```Output
Other terminating error trapped
RuntimeException:
Line |
   4 |  1/$null
     |  ~~~~~~~
     | Attempted to divide by zero.
```

Bij de poging om door nul te delen, wordt er geen **CommandNotFoundException** -fout gemaakt. In plaats daarvan wordt deze fout overlapt door de andere `trap` instructie, wat een afsluit fout overlapt.

### <a name="trapping-errors-and-scope"></a>Trap fouten en bereik

Als een afsluit fout optreedt in hetzelfde bereik als de `trap` instructie, voert Power shell de lijst met instructies uit die zijn gedefinieerd door `trap` . De uitvoering gaat na de fout verder met de instructie. Als de `trap` instructie een andere scope heeft dan de fout, wordt de uitvoering voortgezet bij de volgende instructie die zich in hetzelfde bereik bevindt als de- `trap` instructie.

Als er bijvoorbeeld een fout optreedt in een functie en de `trap` instructie zich in de functie bevindt, wordt het script voortgezet bij de volgende instructie. Het volgende script bevat een fout en een `trap` instructie:

```powershell
function function1 {
    trap { "An error: " }
    NonsenseString
    "function1 was completed"
}

function1
```

Als u dit script uitvoert, wordt het volgende resultaat gegenereerd:

```Output
An error:
NonsenseString:
Line |
   3 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
function1 was completed
```

De `trap` instructie in de functie overtrapt de fout. Na het weer geven van het bericht, wordt de uitvoering van de functie hervat met Power shell. Opmerking `Function1` is voltooid.

Vergelijk dit met het volgende voor beeld, dat dezelfde fout en `trap` instructie heeft. In dit voor beeld `trap` vindt de instructie plaats buiten de functie:

```powershell
function function2 {
    NonsenseString
    "function2 was completed"
}

trap { "An error: " }

function2
```

Het uitvoeren van de `Function2` functie levert het volgende resultaat:

```Output
An error:
NonsenseString:
Line |
   2 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

In dit voor beeld is de opdracht ' function2 is voltooid ' niet uitgevoerd. In beide voor beelden treedt de afsluit fout op in de functie. In dit voor beeld `trap` is de instructie echter buiten de functie. Power shell gaat niet terug naar de functie nadat de `trap` instructie is uitgevoerd.

> [!CAUTION]
> Wanneer meerdere traps voor dezelfde fout voorwaarde worden gedefinieerd, wordt de eerste `trap` gedefinieerde lexicale (hoogste in het bereik) gebruikt.

In het volgende voor beeld wordt alleen de `trap` met ' Whoops 1 ' uitgevoerd.

```powershell
Remove-Item -ErrorAction Stop ThisFileDoesNotExist
trap { "whoops 1"; continue }
trap { "whoops 2"; continue }
```

> [!IMPORTANT]
> Een trap-instructie ligt binnen het bereik waar deze zich bevindt. Als u een `trap` -instructie in een Function-of dot-script hebt, worden alle-instructies verwijderd wanneer het script van de functie of het punt wordt afgesloten `trap` .

### <a name="using-the-break-and-continue-keywords"></a>De tref woorden voor onderbreken en door lopen gebruiken

U kunt de `break` en `continue` tref woorden in een `trap` instructie gebruiken om te bepalen of een script of opdracht wordt uitgevoerd na een afsluit fout.

Als u een instructie opneemt `break` in een `trap` instructie lijst, stopt Power shell de functie of het script. De volgende voorbeeld functie maakt gebruik `break` van het sleutel woord in een `trap` instructie:

```powershell
function break_example {
    trap {
        "Error trapped"
        break
    }
    1/$null
    "Function completed."
}

break_example
```

```Output
Error trapped
ParentContainsErrorRecordException:
Line |
   6 |      1/$null
     |      ~~~~~~~
     | Attempted to divide by zero.
```

Omdat de `trap` instructie het `break` tref woord bevat, wordt de functie niet verder uitgevoerd en wordt de regel ' functie voltooid ' niet uitgevoerd.

Als u een `continue` sleutel woord in een instructie opneemt `trap` , wordt Power shell hervat na de instructie die de fout heeft veroorzaakt, net zoals zonder `break` of `continue` . Met het `continue` tref woord schrijft Power shell echter geen fout naar de fout stroom.

De volgende voorbeeld functie maakt gebruik `continue` van het sleutel woord in een `trap` instructie:

```powershell
function continue_example {
    trap {
        "Error trapped"
        continue
    }
    1/$null
    "Function completed."
}

continue_example
```

```Output
Error trapped
Function completed.
```

De functie wordt hervat nadat de fout is getrapt en de instructie ' functie voltooid ' wordt uitgevoerd. Er wordt geen fout naar de fout stroom geschreven.

## <a name="notes"></a>Opmerkingen

`trap` instructies bieden een eenvoudige manier om ervoor te zorgen dat alle afsluit fouten binnen een bereik worden afgehandeld. Gebruik `try` / `catch` blokken waarin traps worden gedefinieerd met behulp van-instructies voor meer nauw keurige fout afhandeling `catch` . De `catch` instructies zijn alleen van toepassing op de code in de bijbehorende `try` instructie. Zie [about_Try_Catch_Finally](about_Try_Catch_Finally.md)voor meer informatie.

## <a name="see-also"></a>Zie ook

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
