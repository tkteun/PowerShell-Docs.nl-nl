---
description: Hiermee wordt het huidige bereik afgesloten, wat een functie, script of script blok kan zijn.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: 032f3c694096e11e2800be941eb76b1f442b5088
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706223"
---
# <a name="about-return"></a>Over retour neren

## <a name="short-description"></a>Korte beschrijving

Hiermee wordt het huidige bereik afgesloten, wat een functie, script of script blok kan zijn.

## <a name="long-description"></a>Lange beschrijving

Met het `return` sleutel woord wordt een functie, script of script blok afgesloten. Het kan worden gebruikt om een scope af te sluiten op een specifiek punt, om een waarde te retour neren of om aan te geven dat het einde van de scope is bereikt.

Gebruikers die bekend zijn met talen als C of C, \# willen mogelijk het `return` tref woord gebruiken om de logica te maken van het expliciet hebben van een bereik.

In Power shell worden de resultaten van elke instructie geretourneerd als uitvoer, zelfs zonder een instructie die het sleutel woord Return bevat. Talen zoals C of C \# retour neren alleen de waarde of waarden die zijn opgegeven met het `return` sleutel woord.

> [!NOTE]
> Vanaf Power shell 5,0, Power shell toegevoegde taal voor het definiëren van klassen, met behulp van formele syntaxis.  In de context van een Power shell-klasse is er geen uitvoer van een methode, behalve wat u opgeeft met behulp van een- `return` instructie. Meer informatie over Power shell-klassen vindt u in [about_Classes](about_Classes.md).

### <a name="syntax"></a>Syntax

De syntaxis voor het `return` sleutel woord is als volgt:

```
return [<expression>]
```

Het `return` tref woord kan alleen worden weer gegeven of kan als volgt worden gevolgd door een waarde of expressie:

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a>Voorbeelden

In het volgende voor beeld wordt het `return` sleutel woord gebruikt om een functie op een specifiek punt af te sluiten als aan een voorwaardelijke waarde is voldaan. Oneven getallen worden niet vermenigvuldigd omdat de instructie return wordt afgesloten voordat die instructie kan worden uitgevoerd.

```powershell
function MultiplyEven
{
    param($number)

    if ($number % 2) { return "$number is not even" }
    $number * 2
}

1..10 | ForEach-Object {MultiplyEven -Number $_}
```

```output
1 is not even
4
3 is not even
8
5 is not even
12
7 is not even
16
9 is not even
20
```

In Power shell kunnen waarden worden geretourneerd, zelfs als het `return` sleutel woord niet wordt gebruikt.
De resultaten van elke instructie worden geretourneerd. Met de volgende instructies wordt bijvoorbeeld de waarde van de `$a` variabele geretourneerd:

```powershell
$a
return
```

De volgende instructie retourneert ook de waarde `$a` :

```powershell
return $a
```

Het volgende voor beeld bevat een instructie die is bedoeld om de gebruiker te laten weten dat de functie een berekening uitvoert:

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

Het wacht even. Bezig met berekenen... ' de teken reeks wordt niet weer gegeven. In plaats daarvan wordt deze toegewezen aan de `$a` variabele, zoals in het volgende voor beeld:

```
PS> $a
Please wait. Working on calculation...
87
```

Zowel de informatielijke teken reeks als het resultaat van de berekening worden geretourneerd door de functie en toegewezen aan de `$a` variabele.

Als u een bericht binnen uw functie wilt weer geven, vanaf Power shell 5,0, kunt u de stream gebruiken `Information` . De onderstaande code corrigeert het bovenstaande voor beeld met behulp `Write-Information` van de cmdlet met een `InformationAction` van de **door** gaande.

```powershell
function calculation {
    param ($value)

    Write-Information "Please wait. Working on calculation..." -InformationAction Continue
    $value += 73
    return $value
}

$a = calculation 14
```

```output
Please wait. Working on calculation...
C:\PS> $a
87
```

### <a name="return-values-and-the-pipeline"></a>Retour waarden en de pijp lijn

Wanneer u een verzameling uit het script blok of de-functie retourneert, worden de leden automatisch door Power shell opgeheven en door de pijp lijn per keer door gegeven. Dit wordt veroorzaakt door de eenmalige verwerking van Power shell. Zie [about_pipelines](about_pipelines.md)voor meer informatie.

Dit concept wordt geïllustreerd door de volgende voorbeeld functie waarmee een matrix met getallen wordt geretourneerd. De uitvoer van de functie wordt door gegeven aan de `Measure-Object` cmdlet waarmee het aantal objecten in de pijp lijn wordt geteld.

```powershell
function Test-Return
{
    $array = 1,2,3
    return $array
}
Test-Return | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

Gebruik een van de volgende twee methoden om een script blok of functie te dwingen om de verzameling te retour neren als één object naar de pijp lijn:

- Expressie voor unaire matrix

  Als u een unaire expressie gebruikt, kunt u de retour waarde naar de pijp lijn verzenden als een enkel object, zoals wordt geïllustreerd door het volgende voor beeld.

  ```powershell
  function Test-Return
  {
      $array = 1,2,3
      return (, $array)
  }
  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

- `Write-Output` met de para meter ' niet **opsommen** '.

  U kunt de cmdlet ook gebruiken `Write-Output` met de para meter voor de **opsomming** . In het volgende voor beeld wordt de `Measure-Object` cmdlet gebruikt om de objecten te tellen die vanuit de voorbeeld functie naar de pijp lijn worden verzonden met het `return` sleutel woord.

  ```powershell
  function Test-Return
  {
      $array = 1, 2, 3
      return Write-Output -NoEnumerate $array
  }

  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

## <a name="see-also"></a>Zie ook

[about_Language_Keywords](about_Language_Keywords.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[about_Classes](about_Classes.md)

[Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)

[about_Script_Blocks](about_Script_Blocks.md)

