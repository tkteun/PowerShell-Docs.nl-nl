---
description: Zowel integere als reële numerieke letterlijke waarden kunnen type-en vermenigvuldiger-achtervoegsels hebben.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Numerieke letterlijke waarden
ms.openlocfilehash: 99fa8c1a751551d028fe6df0b0cec94e07f19c59
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253169"
---
# <a name="about-numeric-literals"></a>Numerieke letterlijke waarden

Er zijn twee soorten numerieke letterlijke waarden: geheel getal en werkelijk. Beide kunnen type-en multiplier-achtervoegsels hebben.

## <a name="integer-literals"></a>Letterlijke tekens voor geheel getal

Letterlijke tekens kunnen worden geschreven in decimale of hexadecimale notatie. Hexadecimale letterlijke waarden worden voorafgegaan door met `0x` om ze te onderscheiden van decimale getallen.

Letterlijke tekens van een geheel getal kunnen een type achtervoegsel en een vermenigvuldigings achtervoegsel hebben.

| Achtervoegsel |       Betekenis       |
| ------ | ------------------- |
| l      | Long-gegevens type      |
| KB823980     | kilo byte vermenigvuldiger |
| Bespaar     | Mega byte multiplier |
| GB     | Gigabyte multiplier |
| TB     | terabyte-vermenigvuldiger |
| jager     | PETA byte vermenigvuldiger |

Het type van een letterlijke integerwaarde wordt bepaald door de waarde, het type achtervoegsel en het achtervoegsel van de numerieke vermenigvuldiger.

Voor een letterlijke integer zonder type achtervoegsel:

- Als de waarde kan worden weer gegeven op type `[int]` , is dat van het type.
- Als dat niet het geval is, kunt u ook de waarde van het `[long]` type opgeven.
- Als dat niet het geval is, kunt u ook de waarde van het `[decimal]` type opgeven.
- Anders wordt deze weer gegeven op type `[double]` .

Voor een letterlijke integer met een type achtervoegsel:

- Als het type achtervoegsel is `u` en de waarde kan worden weer gegeven op type, `[int]` dan is het type ervan `[int]` .
- Als het type achtervoegsel is `u` en de waarde kan worden weer gegeven op type, `[long]` dan is het type ervan `[long]` .
- Als de waarde ervan kan worden weer gegeven op type dat is opgegeven, is het type ervan.
- Anders is de letterlijke waarde niet goed gevormd.

## <a name="real-literals"></a>Echte letterlijke waarden

Echte letterlijke waarden kunnen alleen worden geschreven in de decimale notatie. Deze notatie kan breuk waarden bevatten na een decimaal teken en een weten schappelijke notatie met een exponentieel onderdeel.

Het exponentiële deel bevat een ' e ', gevolgd door een optioneel teken (+/) en een getal dat de exponent voor stelt. De letterlijke waarde is bijvoorbeeld `1e2` gelijk aan de numerieke waarde 100.

Echte letterlijke waarden kunnen een type achtervoegsel en een vermenigvuldigings achtervoegsel hebben.

| Achtervoegsel |       Betekenis       |
| ------ | ------------------- |
| d      | Decimal-gegevens type   |
| KB823980     | kilo byte vermenigvuldiger |
| Bespaar     | Mega byte multiplier |
| GB     | Gigabyte multiplier |
| TB     | terabyte-vermenigvuldiger |
| jager     | PETA byte vermenigvuldiger |

Er zijn twee soorten echte letterlijke waarde: dubbel en decimaal. Deze worden aangegeven door de afwezigheid of aanwezigheid, respectievelijk van het decimale-type achtervoegsel. Power shell biedt geen ondersteuning voor een letterlijke representatie van een `[float]` waarde. Een dubbele echte letterlijke waarde is van het type `[double]` . Een decimale echte letterlijke waarde is van het type `[decimal]` .
Volg nullen in het gedeelte van een decimale letterlijke teken reeks zijn aanzienlijk.

Als de waarde van de cijfers van exponenten in een `[double]` echte letterlijke teken reeks kleiner is dan de minimale ondersteunde waarde, is de waarden van die `[double]` echte literal 0. Als de waarde van de cijfers van exponenten in een `[decimal]` echte letterlijke teken reeks kleiner is dan de minimale hoeveelheid die wordt ondersteund, is deze literal onjuist. Als de waarde van de cijfers van exponenten in een `[double]` of `[decimal]` echte letterlijke teken reeks groter is dan het maximum aantal dat wordt ondersteund, is de letterlijke teken reeks onjuist.

> [!NOTE]
> De syntaxis laat een dubbele echte letterlijke waarde een achtervoegsel van het type lang.
> Power shell behandelt deze case als een letterlijke integer waarvan de waarde wordt weer gegeven op type `[long]` . Deze functie is bewaard voor achterwaartse compatibiliteit met eerdere versies van Power shell. Programmeurs worden echter niet aangeraden om gehele letterlijke tekens van dit formulier te gebruiken, omdat de werkelijke waarde van de letterlijke teken reeks eenvoudig kan worden verborgen. Bijvoorbeeld: `1.2L` heeft waarde 1, `1.2345e1L` heeft waarde 12 en `1.2345e-5L` heeft waarde 0, geen van beide direct duidelijk.

## <a name="numeric-multipliers"></a>Numerieke vermenigvuldigers

Voor het gemak kunnen integers en reële letterlijke waarden een numerieke vermenigvuldiger bevatten, waarmee een van de meest gebruikte machten van 2 wordt aangegeven. De numerieke vermenigvuldiger kan worden geschreven in een combi natie van hoofd letters of kleine letter.

De vermenigvuldiger achtervoegsels kunnen worden gebruikt in combi natie met de `u` , `ul` en `l` typen achtervoegsels.

### <a name="multiplier-examples"></a>Voor beelden van vermenigvuldiger

```
PS> 1kb
1024

PS> 1.30Dmb
1363148.80

PS> 0x10Gb
17179869184

PS> 1.4e23tb
1.5393162788864E+35

PS> 0x12Lpb
20266198323167232
```

## <a name="numeric-type-accelerators"></a>Sneltoetsen voor numeriek type

Power shell ondersteunt de volgende typen Accelerators:

| Accelerator |         Opmerking         |           Beschrijving            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | Byte (niet ondertekend)                  |
| `[sbyte]`   |                      | Byte (ondertekend)                    |
| `[Int16]`   |                      | 16-bits geheel getal                   |
| `[UInt16]`  |                      | 16-bits geheel getal (niet-ondertekend)        |
| `[Int32]`   |                      | 32-bits geheel getal                   |
| `[int]`     | alias voor `[int32]`  | 32-bits geheel getal                   |
| `[UInt32]`  |                      | 32-bits geheel getal (niet-ondertekend)        |
| `[Int64]`   |                      | 64-bits geheel getal                   |
| `[long]`    | alias voor `[int64]`  | 64-bits geheel getal                   |
| `[UInt64]`  |                      | 64-bits geheel getal (niet-ondertekend)        |
| `[bigint]`  |                      | Zie [BigInteger struct][bigint]  |
| `[single]`  |                      | Drijvende komma met enkele precisie  |
| `[float]`   | alias voor `[single]` | Drijvende komma met enkele precisie  |
| `[double]`  |                      | Drijvende komma met dubbele precisie  |
| `[decimal]` |                      | 128-bits drijvende komma           |

### <a name="working-with-other-numeric-types"></a>Werken met andere numerieke typen

Als u wilt werken met andere numerieke typen, moet u type Accelerators gebruiken. Dit is niet mogelijk zonder dat er problemen zijn. Zo worden hoge integerwaarden altijd geparseerd als dubbele waarden voordat ze naar een ander type worden geconverteerd.

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

De waarde wordt als twee keer geparseerd, waarbij de precisie in de hogere bereiken verloren gaat.
U kunt dit probleem voor komen door waarden als teken reeksen in te voeren en deze vervolgens te converteren:

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a>Voorbeelden

De volgende tabel bevat verschillende voor beelden van numerieke letterlijke waarden en een lijst met het type en de waarde:

|  Getal  |  Type   |    Waarde     |
| -------: | ------- | -----------: |
|      100 | Int32   |          100 |
|     100D | Decimaal |          100 |
|     100l | Int64   |          100 |
|      1e2 | Dubbel  |          100 |
|     1. E2 | Dubbel  |          100 |
|    0x1e2 | Int32   |          482 |
|   0x1e2L | Int64   |          482 |
|   0x1e2D | Int32   |         7725 |
|     482D | Decimaal |          482 |
|    482gb | Int64   | 517543559168 |
| 0x1e2lgb | Int64   | 517543559168 |

### <a name="commands-that-look-like-numeric-literals"></a>Opdrachten die eruitzien als numerieke letterlijke waarden

Elke opdracht die eruitziet als een numerieke literal moet worden uitgevoerd met de aanroep operator ( `&` ), anders wordt deze geïnterpreteerd als een nummer van het bijbehorende type.

### <a name="access-properties-and-methods-of-numeric-objects"></a>Toegang tot eigenschappen en methoden van numerieke objecten

Om toegang te krijgen tot een lid van een numerieke letterlijke waarde, zijn er situaties waarin u de letterlijke teken reeks tussen haakjes moet plaatsen.

- De letterlijke waarde heeft geen decimaal teken
- De letterlijke waarde heeft geen cijfers na het decimaal teken
- De letterlijke waarde heeft geen achtervoegsel

Het volgende voor beeld mislukt bijvoorbeeld:

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

De volgende voor beelden werken:

```
PS> 2L.GetType().Name
Int64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

De eerste twee voor beelden werken zonder tussen haakjes, omdat de Power shell-parser kan bepalen waar de numerieke letterlijke waarde eindigt en de **gettype** -methode wordt gestart.

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
