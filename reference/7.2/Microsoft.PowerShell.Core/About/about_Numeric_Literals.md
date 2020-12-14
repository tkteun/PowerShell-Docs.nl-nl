---
description: Zowel integere als reële numerieke letterlijke waarden kunnen type-en vermenigvuldiger-achtervoegsels hebben.
Locale: en-US
ms.date: 04/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Numerieke letterlijke waarden
ms.openlocfilehash: 0e4081c7601928ce9b74010ea3c86762902ca97a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705522"
---
# <a name="about-numeric-literals"></a>Numerieke letterlijke waarden

Er zijn twee soorten numerieke letterlijke waarden: geheel getal en werkelijk. Beide kunnen type-en multiplier-achtervoegsels hebben.

## <a name="integer-literals"></a>Letterlijke tekens voor geheel getal

Letterlijke tekens kunnen worden geschreven in decimale, hexadecimale of binaire notaties.
Hexadecimale letterlijke waarden worden voorafgegaan door `0x` en binaire letterlijke waarden worden voorafgegaan door `0b` om ze te onderscheiden van decimale getallen.

Letterlijke tekens van een geheel getal kunnen een type achtervoegsel en een vermenigvuldigings achtervoegsel hebben.

| Achtervoegsel |            Betekenis             |          Notitie           |
| ------ | ------------------------------ | ----------------------- |
| y      | gegevens type van ondertekend byte          | Toegevoegd in Power shell 6,2 |
| uy     | gegevens type niet-ondertekend byte        | Toegevoegd in Power shell 6,2 |
| s      | kort gegevens type                | Toegevoegd in Power shell 6,2 |
| VS     | niet-ondertekend kort gegevens type       | Toegevoegd in Power shell 6,2 |
| l      | Long-gegevens type                 |                         |
| h      | niet-ondertekend int of Long-gegevens type | Toegevoegd in Power shell 6,2 |
| UL     | niet-ondertekend Long-gegevens type        | Toegevoegd in Power shell 6,2 |
| n      | BigInteger-gegevens type           | Toegevoegd in Power shell 7,0 |
| KB823980     | kilo byte vermenigvuldiger            |                         |
| Bespaar     | Mega byte multiplier            |                         |
| GB     | Gigabyte multiplier            |                         |
| TB     | terabyte-vermenigvuldiger            |                         |
| jager     | PETA byte vermenigvuldiger            |                         |

Het type van een letterlijke integerwaarde wordt bepaald door de waarde, het type achtervoegsel en het achtervoegsel van de numerieke vermenigvuldiger.

Voor een letterlijke integer zonder type achtervoegsel:

- Als de waarde kan worden weer gegeven op type `[int]` , is dat van het type.
- Als dat niet het geval is, kunt u ook de waarde van het `[long]` type opgeven.
- Als dat niet het geval is, kunt u ook de waarde van het `[decimal]` type opgeven.
- Anders wordt deze weer gegeven op type `[double]` .

Voor een letterlijke integer met een type achtervoegsel:

- Als het type achtervoegsel is `u` en de waarde kan worden weer gegeven op type, `[uint]` dan is het type ervan `[uint]` .
- Als het type achtervoegsel is `u` en de waarde kan worden weer gegeven op type, `[ulong]` dan is het type ervan `[ulong]` .
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

De vermenigvuldiger achtervoegsels kunnen worden gebruikt in combi natie met eventuele type achtervoegsels, maar moeten aanwezig zijn na het type achtervoegsel. De letterlijke waarde `100gbL` is bijvoorbeeld ongeldig, maar de letterlijke waarde `100Lgb` is geldig.

Als een vermenigvuldiger een waarde maakt die de mogelijke waarden voor het numerieke type dat het achtervoegsel opgeeft, overschrijdt, is de letterlijke teken reeks ongeldig. De letterlijke `1usgb` waarde is bijvoorbeeld onjuist, omdat deze `1gb` groter is dan is toegestaan voor het `[ushort]` type dat is opgegeven door het `us` achtervoegsel.

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

| Accelerator |         Notitie         |           Description            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | Byte (niet ondertekend)                  |
| `[sbyte]`   |                      | Byte (ondertekend)                    |
| `[Int16]`   |                      | 16-bits geheel getal                   |
| `[short]`   | alias voor `[int16]`  | 16-bits geheel getal                   |
| `[UInt16]`  |                      | 16-bits geheel getal (niet-ondertekend)        |
| `[ushort]`  | alias voor `[uint16]` | 16-bits geheel getal (niet-ondertekend)        |
| `[Int32]`   |                      | 32-bits geheel getal                   |
| `[int]`     | alias voor `[int32]`  | 32-bits geheel getal                   |
| `[UInt32]`  |                      | 32-bits geheel getal (niet-ondertekend)        |
| `[uint]`    | alias voor `[uint32]` | 32-bits geheel getal (niet-ondertekend)        |
| `[Int64]`   |                      | 64-bits geheel getal                   |
| `[long]`    | alias voor `[int64]`  | 64-bits geheel getal                   |
| `[UInt64]`  |                      | 64-bits geheel getal (niet-ondertekend)        |
| `[ulong]`   | alias voor `[uint64]` | 64-bits geheel getal (niet-ondertekend)        |
| `[bigint]`  |                      | Zie [BigInteger struct][bigint]  |
| `[single]`  |                      | Drijvende komma met enkele precisie  |
| `[float]`   | alias voor `[single]` | Drijvende komma met enkele precisie  |
| `[double]`  |                      | Drijvende komma met dubbele precisie  |
| `[decimal]` |                      | 128-bits drijvende komma           |

> [!NOTE]
> De volgende typen Accelerators zijn toegevoegd aan Power shell 6,2: `[short]` , `[ushort]` , `[uint]` , `[ulong]` .

## <a name="examples"></a>Voorbeelden

De volgende tabel bevat verschillende voor beelden van numerieke letterlijke waarden en een lijst met het type en de waarde:

|   Getal    |    Type    |    Waarde     |
| ----------: | ---------- | -----------: |
|         100 | Int32      |          100 |
|        100u | UInt32     |          100 |
|        100D | Decimaal    |          100 |
|        100l | Int64      |          100 |
|       100uL | UInt64     |          100 |
|       100us | UInt16     |          100 |
|       100uy | Byte       |          100 |
|        100y | SByte      |          100 |
|         1e2 | Dubbel     |          100 |
|        1. E2 | Dubbel     |          100 |
|       0x1e2 | Int32      |          482 |
|      0x1e2L | Int64      |          482 |
|      0x1e2D | Int32      |         7725 |
|        482D | Decimaal    |          482 |
|       482gb | Int64      | 517543559168 |
|      482ngb | BigInteger | 517543559168 |
|    0x1e2lgb | Int64      | 517543559168 |
|   0b1011011 | Int32      |           91 |
|     0xFFFFs | Int16      |           -1 |
|  0xFFFFFFFF | Int32      |           -1 |
| -0xFFFFFFFF | Int32      |            1 |
| 0xFFFFFFFFu | UInt32     |   4294967295 |

### <a name="working-with-binary-or-hexadecimal-numbers"></a>Werken met binaire of hexadecimale getallen

Over grote binaire of hexadecimale letterlijke tekens kan worden geretourneerd `[bigint]` in plaats van het mislukken van de parser, als en alleen als het `n` achtervoegsel is opgegeven. Onderteken-bits worden nog steeds boven even `[decimal]` bereiken geëerbiedigd, echter:

- Als een binaire teken reeks een meervoud van 8 bits lang is, wordt de hoogste bit beschouwd als de teken-bit.
- Als een hexadecimale teken reeks met een lengte die een meervoud van 8 is, het eerste cijfer met 8 of hoger heeft, wordt het cijfer als negatief beschouwd.

Als u een niet-ondertekend achtervoegsel opgeeft voor binaire en hexadecimale letterlijke tekens, worden teken-bits genegeerd. `0xFFFFFFFF`Retourneert bijvoorbeeld `-1` , maar `0xFFFFFFFFu` retourneert de waarde `[uint]::MaxValue` van 4294967295.

In Power shell 7,1 retourneert het gebruik van een type achtervoegsel voor een hex literal nu een ondertekende waarde van dat type. In Power shell 7,0 retourneert de expressie bijvoorbeeld `0xFFFFs` een fout omdat de positieve waarde te groot is voor een `[int16]` type.
Power shell 7,1 interpreteert dit als `-1` een `[int16]` type.

Voor het voor voegsel van de letterlijke waarde met a `0` wordt deze omzeild en beschouwd als niet-ondertekend.
Bijvoorbeeld: `0b011111111`. Dit kan nodig zijn bij het werken met letterlijke waarden in het `[bigint]` bereik, omdat de `u` `n` achtervoegsels niet kunnen worden gecombineerd.

U kunt ook binaire en hexadecimale letterlijke waarden negeren met het `-` voor voegsel. Dit kan resulteren in een positief getal sinds de aanmeldings-bits zijn toegestaan.

Onderteken bits worden geaccepteerd voor BigInteger cijfers:

- Met BigInteger-achtervoegseld hex wordt de grote bit van elke letterlijke waarde met een lengte van meer dan acht tekens beschouwd als de teken-bit. De lengte bevat niet het `0x` voor voegsel of achtervoegsels.
- BigInteger-achtervoegsels accepteren binaire aanmeldingen op 96 en 128 tekens, en om de 8 tekens na.

### <a name="commands-that-look-like-numeric-literals"></a>Opdrachten die eruitzien als numerieke letterlijke waarden

Elke opdracht die eruitziet als een geldige numerieke literal moet worden uitgevoerd met de aanroep operator ( `&` ), anders wordt deze geïnterpreteerd als een getal. Onjuist gevormde letterlijke waarden met een geldige syntaxis als `1usgb` resultaat hebben de volgende fout:

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

Onjuist ingedeelde letterlijke tekens met een ongeldige syntaxis zoals `1gbus` wordt geïnterpreteerd als een standaard bare teken reeks en kan worden geïnterpreteerd als een geldige opdracht naam in contexten waar opdrachten kunnen worden aangeroepen.

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
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

De eerste twee voor beelden werken zonder tussen haakjes, omdat de Power shell-parser kan bepalen waar de numerieke letterlijke waarde eindigt en de **gettype** -methode wordt gestart.

## <a name="how-powershell-parses-numeric-literals"></a>Hoe in Power shell numerieke letterlijke waarden worden geparseerd

Power shell v 7.0 heeft de manier gewijzigd waarop numerieke letterlijke waarden worden geparseerd om de nieuwe functies in te scha kelen.

### <a name="parsing-real-numeric-literals"></a>Werkelijke numerieke letterlijke waarden parseren

Als de letterlijke waarde een decimaal teken of de e-notatie bevat, wordt de letterlijke teken reeks geparseerd als een reëel getal.

- Als het decimale achtervoegsel direct in wordt weer gegeven `[decimal]` .
- Else, parse as `[Double]` en apply vermenigvuldigen met de waarde. Controleer vervolgens het type achtervoegsels en probeer het naar het juiste type te casten.
- Als de teken reeks geen type achtervoegsel heeft, vervolgens parseren als `[Double]` .

### <a name="paring-integer-numeric-literals"></a>Numerieke letterlijke waarden voor paring geheel getal

Letterlijke waarden van het type integer worden geparseerd met behulp van de volgende stappen:

1. De indeling van het grondtal bepalen
   - Voor binaire indelingen parseren naar `[BigInteger]` .
   - Voor hexadecimale notaties Parset u in `[BigInteger]` met behulp van speciale casies om oorspronkelijke gedragingen te behouden wanneer de waarde in de `[int]` of het bereik ligt `[long]` .
   - Als binair noch hex, worden geparseerd als een `[BigInteger]` .
2. Pas de vermenigvuldiger waarde toe voordat u een casts probeert te maken om ervoor te zorgen dat type bindingen op de juiste wijze kunnen worden gecontroleerd zonder overloop.
3. Controleer type achtervoegsels.
   - Controleer type grenzen en probeer te parseren naar dat type.
   - Als er geen achtervoegsel wordt gebruikt, wordt de waarde ingesteld op grenzen-ingeschakeld in de volgende volg orde, wat resulteert in de eerste geslaagde test die het type van het getal bepaalt.
     - `[int]`
     - `[long]`
     - `[decimal]` (alleen base-10 letterlijke waarden)
     - `[double]` (alleen base-10 letterlijke waarden)
   - Als de waarde buiten het `[long]` bereik van hexadecimale en binaire getallen ligt, mislukt de parsering.
   - Als de waarde buiten het `[double]` bereik van het grondtal 10 nummer valt, mislukt de parsering.
   - Hogere waarden moeten expliciet worden geschreven met behulp van het `n` achtervoegsel voor het parseren van de letterlijke waarde als een `BigInteger` .

### <a name="parsing-large-value-literals"></a>Letterlijke waarden voor grote waarden parseren

Voorheen werden hogere integerwaarden geparseerd als dubbele waarden voordat ze naar een ander type worden geconverteerd. Dit resulteert in een verlies van nauw keurigheid in de hogere bereiken. Bijvoorbeeld:

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

U kunt dit probleem voor komen door waarden te schrijven als teken reeksen en ze vervolgens te converteren:

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

In Power shell 7,0 moet u het `N` achtervoegsel gebruiken.

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

Ook waarden tussen `[ulong]::MaxValue` en `[decimal]::MaxValue` moeten worden aangegeven met het decimale achtervoegsel `D` om nauw keurigheid te behouden. Zonder achtervoegsel worden deze waarden geparseerd als `[Double]` het gebruik van de modus voor real-parseren.

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
