---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 970c72d5661796c25d6beb30eb08b6cd7032ceb1
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249755"
---
# Measure-Command

## SAMENVATTING
Meet de tijd die nodig is voor het uitvoeren van script blokken en-cmdlets.

## SYNTAXIS

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## BESCHRIJVING

De `Measure-Command` cmdlet voert een script blok of cmdlet intern uit, keer de uitvoering van de bewerking en retourneert de uitvoerings tijd.

> [!NOTE]
> Script blokken worden uitgevoerd door uit te `Measure-Command` voeren in het huidige bereik, niet op een onderliggend bereik.

## VOORBEELDEN

### Voor beeld 1: een opdracht meten

In dit voor beeld wordt de tijd gemeten die nodig is om een opdracht uit te voeren `Get-EventLog` waarmee de gebeurtenissen in het gebeurtenis logboek van Windows Power shell worden opgehaald.

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### Voor beeld 2: twee uitvoer van Measure-Command vergelijken

De eerste opdracht meet de tijd die nodig is voor het verwerken van een recursieve `Get-ChildItem` opdracht die gebruikmaakt van de para meter **Path** om alleen `.txt` bestanden in de `C:\Windows` map en de bijbehorende submappen op te halen.

De tweede opdracht meet de tijd die nodig is voor het verwerken van een recursieve `Get-ChildItem` opdracht die gebruikmaakt van de para meter voor de provider.

Met deze opdrachten wordt de waarde weer gegeven van het gebruik van een provider-specifiek filter in Power shell-opdrachten.

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### Voor beeld 3: pijpleiding invoer naar Measure-Command

Objecten waarnaar wordt gepiped `Measure-Command` , zijn beschikbaar voor het script blok dat wordt door gegeven aan de para meter **Expression** . Het script blok wordt één keer uitgevoerd voor elk object in de pijp lijn.

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_; $i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### Voor beeld 4: uitvoer van gemeten opdracht weer geven

Als u de uitvoer van de expressie in wilt weer geven, `Measure-Command` kunt u een pipe gebruiken `Out-Default` .

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### Voor beeld 5: uitvoering meten in een onderliggend bereik

`Measure-Command` Hiermee wordt het script blok in het huidige bereik uitgevoerd, zodat het script blok waarden in het huidige bereik kan wijzigen. Als u wilt voor komen dat de huidige scope wordt gewijzigd, moet u het script blok in accolades ( `{}` ) plaatsen en de aanroep operator ( `&` ) gebruiken om het blok in een onderliggend bereik uit te voeren.

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

Zie [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-)voor meer informatie over de aanroep operator.

## PARAMETERS

### -Expressie

Hiermee geeft u de expressie op waarvoor een time-out is ingesteld. Plaats de expressie tussen accolades ( `{}` ).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Objecten die zijn gekoppeld aan de para meter **input object** zijn optionele invoer voor het script blok dat is door gegeven aan de para meter **Expression** . In het-script blok `$_` kan worden gebruikt om te verwijzen naar het huidige object in de pijp lijn.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt een object door sluizen naar `Measure-Command` .

## UITVOER

### System. time span

`Measure-Command` retourneert een time span-object dat het resultaat voor stelt.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Invoke-opdracht](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Tracering-opdracht](Trace-Command.md)
