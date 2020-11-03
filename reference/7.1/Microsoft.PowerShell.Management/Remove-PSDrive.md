---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: 9c1edd90757017c679516553d376d4cd4e552875
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249840"
---
# Remove-PSDrive

## SAMENVATTING
Verwijdert tijdelijke Power Shell-stations en verbreekt de verbinding van toegewezen netwerk stations.

## SYNTAXIS

### Naam (standaard)

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Letterlijke waarde

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Remove-PSDrive` cmdlet verwijdert tijdelijke Power Shell-stations die zijn gemaakt met behulp van de- `New-PSDrive` cmdlet.

Met ingang van Windows Power Shell 3,0 `Remove-PSDrive` verbreekt ook de verbinding met toegewezen netwerk stations, inclusief, maar niet beperkt tot, stations die zijn gemaakt met behulp `Persist` van de para meter van `New-PSDrive` .

`Remove-PSDrive` kan fysieke of logische stations van Windows niet verwijderen.

Vanaf Windows Power Shell 3,0, wanneer een extern station is verbonden met de computer, wordt door Power shell automatisch een PSDrive toegevoegd aan het bestands systeem dat het nieuwe station vertegenwoordigt.
U hoeft Power shell niet opnieuw op te starten.
Op dezelfde manier verwijdert Power shell automatisch de PSDrive die de verwijderde schijf vertegenwoordigt wanneer een extern station wordt losgekoppeld van de computer.

## VOORBEELDEN

### Voor beeld 1: een bestandssysteem station verwijderen

Met deze opdracht wordt een tijdelijk bestandssysteem station met de naam "smp" verwijderd.

```powershell
Remove-PSDrive -Name smp
```

### Voor beeld 2: toegewezen netwerk stations verwijderen

Met deze opdracht wordt gebruikt `Remove-PSDrive` om de verbinding met de X: en S: toegewezen netwerk stations te verbreken.

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## PARAMETERS

### -Force

Hiermee verwijdert u het huidige Power Shell-station.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Literal-waarde

Hiermee geeft u de naam van het station.

De waarde van **literal** wordt exact als getypt gebruikt.
Geen tekens worden geïnterpreteerd als joker tekens.
Als de naam escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens (').
Enkele aanhalings tekens geven Power shell opdracht instructies niet te interpreteren als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de namen van de stations die u wilt verwijderen.
Typ geen dubbele punt (:) na de naam van het station.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PSProvider

Hiermee wordt een matrix met **PSProvider** -objecten opgegeven.
Met deze cmdlet worden alle stations die zijn gekoppeld aan de opgegeven Power shell-provider, verwijderd en verbroken.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Bereik

Hiermee geeft u een bereik voor het station.
De acceptabele waarden voor deze para meter zijn: Global, local en script, of een getal dat relatief is ten opzichte van het huidige bereik. Bereiken nummer 0 tot het aantal bereiken. Het huidige bereik nummer is 0 en de bovenliggende waarde is 1.
Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System.Management.Automation.PSDriveInfo

U kunt een schijf object, zoals een, van de `Get-PSDrive` cmdlet, naar de cmdlet pipeen `Remove-PSDrive` .

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

- De `Remove-PSDrive` cmdlet is ontworpen om te werken met de gegevens die door elke Power shell-provider worden weer gegeven. Gebruik de cmdlet om de providers in uw sessie weer te geven `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Get-PSDrive](Get-PSDrive.md)

[New-PSDrive](New-PSDrive.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

