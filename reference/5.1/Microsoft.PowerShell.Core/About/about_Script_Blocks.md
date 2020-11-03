---
description: Definieert wat een script blok is en legt uit hoe script blokken moeten worden gebruikt in de programmeer taal Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: f842701d83c525e4695debf99c4725580661b1de
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252565"
---
# <a name="about-script-blocks"></a>Over script blokken

## <a name="short-description"></a>Korte beschrijving

Definieert wat een script blok is en legt uit hoe script blokken moeten worden gebruikt in de programmeer taal Power shell.

## <a name="long-description"></a>Lange beschrijving

In de programmeer taal van Power shell is een script blok een verzameling instructies of expressies die kunnen worden gebruikt als één eenheid.
Een script blok kan argumenten en retour waarden accepteren.

Een script blok is syntactisch een instructie lijst in accolades, zoals wordt weer gegeven in de volgende syntaxis:

```
{<statement list>}
```

Een script blok retourneert de uitvoer van alle opdrachten in het script blok, hetzij als een enkel object of als een matrix.

U kunt ook een retour waarde opgeven met behulp van het `return` sleutel woord. Het `return` tref woord heeft geen invloed op of onderdrukt andere uitvoer die wordt geretourneerd door het script blok. Het `return` sleutel woord sluit echter het script blok af op die regel. Zie [about_Return](about_Return.md)voor meer informatie.

Net als bij functies kan een script blok para meters bevatten. Gebruik het sleutel woord param om benoemde para meters toe te wijzen, zoals wordt weer gegeven in de volgende syntaxis:

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> In een-script blok, in tegens telling tot een functie, kunt u geen para meters opgeven buiten de accolades.

Net als bij functies kunnen script blokken de `DynamicParam` `Begin` `Process` sleutel woorden,, en bevatten `End` . Zie [about_Functions](about_Functions.md) en [about_Functions_Advanced](about_Functions_Advanced.md)voor meer informatie.

## <a name="using-script-blocks"></a>Script blokken gebruiken

Een script blok is een exemplaar van een Microsoft .NET Framework-type `System.Management.Automation.ScriptBlock` . Opdrachten kunnen script Block-parameter waarden bevatten. De `Invoke-Command` cmdlet heeft bijvoorbeeld een `ScriptBlock` para meter die een script blok waarde nodig heeft, zoals wordt weer gegeven in dit voor beeld:

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

`Invoke-Command` kan ook script blokken met parameter blokken uitvoeren.
Para meters worden toegewezen op basis van de positie met behulp van de para meter **argument List** .

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

In het script blok in het voor gaande voor beeld wordt het `param` sleutel woord gebruikt voor het maken van para meters `$p1` en `$p2` . De teken reeks ' First ' is gebonden aan de eerste para meter ( `$p1` ) en ' Second ' is gebonden aan ( `$p2` ).

Zie [about_Splatting](about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.

U kunt variabelen gebruiken om script blokken op te slaan en uit te voeren. In het onderstaande voor beeld wordt een script blok in een variabele opgeslagen en door gegeven aan `Invoke-Command` .

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

De aanroep operator is een andere manier om script blokken uit te voeren die zijn opgeslagen in een variabele.
Net als `Invoke-Command` de aanroep operator voert het script blok uit in een onderliggend bereik. De operator oproep kan het gemakkelijker maken om para meters met uw script blokken te gebruiken.

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

U kunt de uitvoer van uw script blokken in een variabele opslaan met behulp van de toewijzing.

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

Zie [about_Operators](about_Operators.md)voor meer informatie over de aanroep operator.

## <a name="using-delay-bind-script-blocks-with-parameters"></a>Gebruiken van vertraging-BIND script blokken met para meters

Een getypeerde para meter die pijplijn invoer ( `by Value` ) of () accepteert, `by PropertyName` maakt het gebruik van script blokken met **vertragings bindingen** mogelijk voor de para meter.
Binnen het script blok voor de **vertragings binding** kunt u verwijzen naar het pipet in object met behulp van de pijplijn variabele `$_` .

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

In complexere cmdlets kunt u met vertraging-BIND script blokken één piped in object opnieuw gebruiken om andere para meters in te vullen.

Opmerkingen bij **vertraging-** script blokken als para meters binden:

- U moet expliciet parameter namen opgeven die u gebruikt met **vertragings-BIND** script blokken.
- De para meter mag niet van het type ungetypeerde zijn en het parameter type mag niet zijn `[scriptblock]` of `[object]` .
- U ontvangt een fout melding als u een **vertragings-BIND** script blok gebruikt zonder de invoer van de pijp lijn te leveren.

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a>Zie ook

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Operators](about_Operators.md)
