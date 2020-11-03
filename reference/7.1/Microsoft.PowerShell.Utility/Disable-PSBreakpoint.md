---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: 2f89be6b2ae9973b060a8562b5815b4e44b56ad8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250904"
---
# Disable-PSBreakpoint

## SAMENVATTING
Hiermee schakelt u de onderbrekings punten in de huidige console uit.

## SYNTAXIS

### Onderbrekings punt (standaard)

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **Disable-PSBreakpoint** worden onderbrekings punten uitgeschakeld. Dit zorgt ervoor dat ze niet worden weer bereikt wanneer het script wordt uitgevoerd.
U kunt deze gebruiken om alle onderbrekings punten uit te scha kelen of u kunt onderbrekings punten opgeven door Break Point-objecten of onderbrekings punt-Id's in te dienen.

Technisch gesp roken wijzigt deze cmdlet de waarde van de eigenschap Enabled van een onderbrekings punt-object in ONWAAR.
Als u een onderbrekings punt opnieuw wilt inschakelen, gebruikt u de cmdlet Enable-PSBreakpoint.
Onderbrekings punten worden standaard ingeschakeld wanneer u deze maakt met behulp van de cmdlet Set-PSBreakpoint.

Een onderbrekings punt is een Point in een script waar de uitvoering tijdelijk wordt gestopt zodat u de instructies in het script kunt onderzoeken.
**Disable-PSBreakpoint** is een van de verschillende cmdlets die zijn ontworpen voor het opsporen van fouten in Power shell-scripts.
Zie about_Debuggers voor meer informatie over de Power Shell-fout opsporing.

## VOORBEELDEN

### Voor beeld 1: een onderbrekings punt instellen en deze uitschakelen

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

Met deze opdrachten wordt een nieuw gemaakt onderbrekings punt uitgeschakeld.

De eerste opdracht gebruikt de cmdlet Set-PSBreakpoint om een onderbrekings punt te maken op de *naam* variabele in het Sample.ps1 script.
Vervolgens wordt het object onderbrekings punt opgeslagen in de variabele $B.

De tweede opdracht maakt gebruik van de cmdlet **Disable-PSBreakpoint** om het nieuwe onderbrekings punt uit te scha kelen.
Er wordt een pijplijn operator (|) gebruikt om het Break Point-object in $B te verzenden naar de cmdlet **Disable-PSBreakpoint** .

Als gevolg van deze opdracht is de waarde van de eigenschap ingeschakeld van het object onderbrekings punt in $B onwaar.

### Voor beeld 2: een onderbrekings punt uitschakelen

```
PS C:\> Disable-PSBreakpoint -Id 0
```

Met deze opdracht wordt het onderbrekings punt met onderbrekings punt-ID 0 uitgeschakeld.

### Voor beeld 3: een uitgeschakeld onderbrekings punt maken

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

Met deze opdracht maakt u een nieuw onderbrekings punt dat is uitgeschakeld totdat u het inschakelt.

De cmdlet **Disable-PSBreakpoint** wordt gebruikt om het onderbrekings punt uit te scha kelen.
De waarde van de para meter *Break Point* is een Set-PSBreakpoint opdracht waarmee een nieuw onderbrekings punt wordt ingesteld, een onderbrekings punt object wordt gegenereerd en het object wordt opgeslagen in de variabele $B.

Cmdlet-para meters die objecten als waarden aannemen, kunnen een variabele accepteren die het object bevat of een opdracht waarmee het object wordt opgehaald of gegenereerd.
In dit geval, omdat **set-PSBreakpoint** een Break Point-object genereert, kan worden gebruikt als de waarde van de para meter *Break Point* .

Met de tweede opdracht wordt het Break Point-object weer gegeven in de waarde van de variabele $B.

### Voor beeld 4: alle onderbrekings punten in de huidige console uitschakelen

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

Met deze opdracht worden alle onderbrekings punten in de huidige console uitgeschakeld.
U kunt deze opdracht afkorten als: "GBP | dbp".

## PARAMETERS

### -Onderbrekings punt

Hiermee geeft u de onderbrekings punten die moeten worden uitgeschakeld.
Voer een variabele in die Break Point-objecten bevat of een opdracht die Break Point-objecten, zoals een Get-PSBreakpoint opdracht.
U kunt ook pipet-objecten naar de cmdlet **Disable-PSBreakpoint** .

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

Hiermee worden de onderbrekings punten met de opgegeven onderbrekings punt-Id's uitgeschakeld.
Voer de Id's of een variabele in die de Id's bevat.
U kunt geen pipe-Id's naar **Disable-PSBreakpoint**.

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

Retourneert een object dat de ingeschakelde onderbrekings punten vertegenwoordigt.
Deze cmdlet genereert standaard geen uitvoer.

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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

U kunt een Break Point-object door sluizen naar **Disable-PSBreakpoint**.

## UITVOER

### Geen of System. Management. Automation. Break Point

Wanneer u de para meter *PassThru* gebruikt, retourneert **Disable-PSBreakpoint** een object dat het uitgeschakelde onderbrekings punt vertegenwoordigt.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

