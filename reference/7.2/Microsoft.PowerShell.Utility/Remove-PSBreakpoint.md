---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: a56b9041c0ae70def7df619f2a4d265cb631fe7b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704752"
---
# Remove-PSBreakpoint

## SAMENVATTING
Hiermee worden onderbrekings punten uit de huidige console verwijderd.

## SYNTAXIS

### Onderbrekings punt (standaard)

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Remove-PSBreakpoint** wordt een onderbrekings punt verwijderd.
Voer een onderbrekings punt object of een onderbrekings punt-ID in.

Wanneer u een onderbrekings punt verwijdert, is het object onderbrekings punt niet meer beschikbaar of werkt het niet meer.
Als u een onderbrekings punt object in een variabele hebt opgeslagen, bestaat de verwijzing nog steeds, maar werkt het onderbrekings punt niet.

**Remove-PSBreakpoint** is een van de verschillende cmdlets die zijn ontworpen voor het opsporen van fouten in Power shell-scripts.
Zie about_Debuggers voor meer informatie over de Power Shell-fout opsporing.

## VOORBEELDEN

### Voor beeld 1: alle onderbrekings punten verwijderen

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

Met deze opdracht worden alle onderbrekings punten in de huidige console verwijderd.

### Voor beeld 2: een opgegeven onderbrekings punt verwijderen

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

Met deze opdracht wordt een onderbrekings punt verwijderd.

De eerste opdracht gebruikt de cmdlet Set-PSBreakpoint om een onderbrekings punt te maken op de naam variabele in het Sample.ps1 script.
Vervolgens wordt het object onderbrekings punt opgeslagen in de variabele $B.

De tweede opdracht maakt gebruik van de cmdlet **Remove-PSBreakpoint** om het nieuwe onderbrekings punt te verwijderen.
Er wordt een pijplijn operator (|) gebruikt om het Break Point-object in de $B variabele te verzenden naar de cmdlet **Remove-PSBreakpoint** .

Als gevolg van deze opdracht, als u het script uitvoert, wordt het uitgevoerd om te worden voltooid zonder te stoppen.
De cmdlet **Get-PSBreakpoint** retourneert dit onderbrekings punt ook niet.

### Voor beeld 3: een onderbrekings punt verwijderen op basis van ID

```
PS C:\> Remove-PSBreakpoint -Id 2
```

Met deze opdracht wordt het onderbrekings punt met onderbrekings punt-ID 2 verwijderd.

### Voor beeld 4: een functie gebruiken om alle onderbrekings punten te verwijderen

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

Met deze eenvoudige functie worden alle onderbrekings punten in de huidige console verwijderd.
De Get-PSBreakpoint cmdlet wordt gebruikt om de onderbrekings punten op te halen.
Vervolgens wordt een pijplijn operator (|) gebruikt om de onderbrekings punten te verzenden naar de cmdlet **Remove-PSBreakpoint** , waarmee deze worden verwijderd.

Als gevolg hiervan kunt u `del-psb` in plaats van de langere opdracht typen.

Als u de functie wilt opslaan, voegt u deze toe aan uw Power shell-profiel.

## PARAMETERS

### -Onderbrekings punt
Hiermee geeft u de onderbrekings punten die moeten worden verwijderd.
Voer een variabele in die Break Point-objecten bevat of een opdracht die Break Point-objecten, zoals een **Get-PSBreakpoint-** opdracht, ontvangt.
U kunt ook pipet-objecten voor onderbrekingen voor **het verwijderen van-PSBreakpoint**.

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
Hiermee geeft u onderbrekings punt-Id's op waarvoor deze cmdlet onderbrekings punten verwijdert.

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
U kunt **PSBreakpoint-** onderbrekings punten verwijderen.

## UITVOER

### Geen
De cmdlet genereert geen uitvoer.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

