---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 547739d6482e86bc558245bc5c5f04eddcfe9614
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250903"
---
# Enable-PSBreakpoint

## SAMENVATTING
Hiermee schakelt u de onderbrekings punten in de huidige console in.

## SYNTAXIS

### Id (standaard)

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Stopt

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

`Enable-PSBreakpoint`Met de cmdlet worden uitgeschakelde onderbrekings punten opnieuw ingeschakeld. U kunt deze gebruiken om alle onderbrekings punten of specifieke onderbrekings punten in te scha kelen door Break Point-objecten of-Id's op te geven.

Een onderbrekings punt is een Point in een script waar de uitvoering tijdelijk wordt gestopt, zodat u de status van het script kunt controleren. Nieuw gemaakte onderbrekings punten worden automatisch ingeschakeld, maar kunnen worden uitgeschakeld met `Disable-PSBreakpoint` .

Technisch gesp roken wijzigt deze cmdlet de waarde van de eigenschap **enabled** van een Break Point-object in **True**.

`Enable-PSBreakpoint` is een van de verschillende cmdlets die zijn ontworpen voor fout opsporing in Power shell-scripts. Zie [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)voor meer informatie over de Power Shell-fout opsporing.

## VOORBEELDEN

### Voor beeld 1: alle onderbrekings punten inschakelen

In dit voor beeld worden alle onderbrekings punten in de huidige sessie ingeschakeld.

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

Met behulp van aliassen kan dit voor beeld worden afgekort tot `gbp | ebp` .

### Voor beeld 2: onderbrekings punten op ID inschakelen

In dit voor beeld worden meerdere onderbrekings punten met de onderbrekings punt-Id's ingeschakeld.

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### Voor beeld 3: een uitgeschakeld onderbrekings punt inschakelen

In dit voor beeld wordt een onderbrekings punt dat is uitgeschakeld opnieuw ingeschakeld.

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

`Set-PSBreakpoint` Hiermee maakt u een onderbrekings punt in de variabele **naam** in het `Sample.ps1` script om het onderbrekings punt object in de variabele op te slaan `$B` . De para meter **PassThru** geeft de waarde weer van de eigenschap **enabled** van het onderbrekings punt is **Onwaar**.

`Enable-PSBreakpoint` Hiermee schakelt u het onderbrekings punt opnieuw in. Ook als u de para meter **PassThru** gebruikt, ziet u dat de waarde van de eigenschap **ingeschakeld is ingesteld** op **True**.

### Voor beeld 4: onderbrekings punten inschakelen met behulp van een variabele

In dit voor beeld wordt een set onderbrekings punten ingeschakeld met behulp van de Break Point-objecten.

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

`Get-PSBreakpoint` Hiermee worden de onderbrekings punten opgehaald en opgeslagen in de `$B` variabele. Met de para meter **Break Point** worden `Enable-PSBreakpoint` de onderbrekings punten ingeschakeld.

Dit voor beeld is gelijk aan het uitvoeren van `Enable-PSBreakpoint -Id 3, 5` .

## PARAMETERS

### -Onderbrekings punt

Hiermee geeft u de onderbrekings punten die moeten worden ingeschakeld. Geef een variabele op die onderbrekings punten bevat of een opdracht die Break Point-objecten (bijvoorbeeld) ophaalt `Get-PSBreakpoint` . U kunt ook pipet-objecten naar `Enable-PSBreakpoint` .

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

Hiermee geeft u de **id-** nummers op van de onderbrekings punten die moeten worden ingeschakeld. De standaard waarde is alle onderbrekings punten.
Geef de **id** op per getal of in een variabele. U kunt geen **id-** nummers door sluizen naar `Enable-PSBreakpoint` . Als u de **id** van een onderbrekings punt wilt zoeken, gebruikt u de `Get-PSBreakpoint` cmdlet.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het onderbrekings punt vertegenwoordigt dat wordt ingeschakeld. Deze cmdlet genereert standaard geen uitvoer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. Break Point

U kunt een onderbrekings punt object door sluizen naar `Enable-PSBreakpoint` .

## UITVOER

### Geen of System. Management. Automation. Break Point

Wanneer u de para meter **PassThru** gebruikt, `Enable-PSBreakpoint` retourneert een Break Point-object dat de ingeschakelde onderbrekings punt vertegenwoordigt. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

- De `Enable-PSBreakpoint` cmdlet genereert geen fout als u probeert een onderbrekings punt in te scha kelen dat al is ingeschakeld. Zo kunt u alle onderbrekings punten zonder fouten inschakelen, zelfs wanneer er slechts enkele zijn uitgeschakeld.

- Onderbrekings punten worden ingeschakeld wanneer u deze maakt met behulp van de- `Set-PSBreakpoint` cmdlet. U hoeft geen nieuw gemaakte onderbrekings punten in te scha kelen.

## GERELATEERDE KOPPELINGEN

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

