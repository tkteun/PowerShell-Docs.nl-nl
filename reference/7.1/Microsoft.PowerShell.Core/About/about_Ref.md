---
description: Hierin wordt beschreven hoe u een verwijzings type variabele maakt en gebruikt. U kunt verwijzings type variabelen gebruiken om een functie toe te staan de waarde te wijzigen van een variabele die wordt door gegeven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: f011ec44e93d379e6d6a84eaeed37862c888baa1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252936"
---
# <a name="about-ref"></a>Over Ref

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u een verwijzings type variabele maakt en gebruikt. U kunt verwijzings type variabelen gebruiken om een functie toe te staan de waarde te wijzigen van een variabele die wordt door gegeven.

## <a name="long-description"></a>Lange beschrijving

U kunt variabelen door geven aan functies op *basis van verwijzing* of *op waarde*.

Wanneer u een variabele door geeft aan de hand van een *waarde* , wordt een kopie van de gegevens door gegeven.

In het volgende voor beeld wijzigt de functie de waarde van de variabele die hieraan wordt door gegeven. In Power shell zijn integers waardetypen zodat ze door een waarde worden door gegeven.
Daarom is de waarde van `$var` ongewijzigd buiten het bereik van de functie.

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

In het volgende voor beeld wordt een variabele met een `Hashtable` wordt door gegeven aan een functie. `Hashtable` is een object type dat standaard wordt door gegeven aan de functie *door verwijzing*.

Wanneer een variabele *door wordt door* gegeven, kan de functie de gegevens wijzigen en de wijziging blijft behouden nadat de functie is uitgevoerd.

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

De functie voegt een nieuw sleutel/waarde-paar toe dat zich buiten het bereik van de functie bevindt.

### <a name="writing-functions-to-accept-reference-parameters"></a>Functies schrijven om referentie parameters te accepteren

U kunt uw functies coderen om een para meter als referentie te maken, ongeacht het type gegevens dat is door gegeven. Hiervoor moet u het type para meters opgeven als `System.Management.Automation.PSReference` , of `[ref]` .

Wanneer u verwijzingen gebruikt, moet u de `Value` eigenschap van het `System.Management.Automation.PSReference` type gebruiken om toegang te krijgen tot uw gegevens.

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

Als u een variabele wilt door geven aan een para meter die een verwijzing verwacht, moet u uw variabele als referentie typen.

> [!NOTE]
> De haken en haakjes zijn beide verplicht.

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a>Verwijzingen naar .NET-methoden door geven

Voor sommige .NET-methoden moet u mogelijk een variabele door geven als referentie. Wanneer de definitie van de methode gebruikmaakt van de tref woorden `in` , `out` of `ref` op basis van een para meter, wordt een verwijzing verwacht.

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

De `TryParse` methode probeert een teken reeks te parseren als een geheel getal. Als de methode is geslaagd, wordt geretourneerd `$true` en wordt het resultaat opgeslagen in de variabele die u hebt door gegeven als **verwijzing**.

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a>Verwijzingen en bereiken

Met verwijzingen kan de waarde van een variabele in het bovenliggende bereik worden gewijzigd binnen een onderliggend bereik.

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

Alleen de variabele van het verwijzings type is gewijzigd.

## <a name="see-also"></a>Zie ook

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Scopes](about_scopes.md)

