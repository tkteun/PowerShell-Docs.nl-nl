---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 77a89a9189d3ae8f7c3450bdddbe9456b4e941c7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250106"
---
# Uninstall-Module

## SAMENVATTING
Hiermee verwijdert u een module.

## SYNTAXIS

### NameParameterSet (standaard)

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Input object

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Uninstall-Module`Met de cmdlet wordt een opgegeven module verwijderd van de lokale computer. U kunt een module niet verwijderen als deze andere modules als afhankelijkheden heeft.

## VOORBEELDEN

### Voor beeld 1: een module verwijderen

In dit voor beeld wordt een module verwijderd.

```powershell
Uninstall-Module -Name SpeculationControl
```

`Uninstall-Module` maakt gebruik van de para meter **name** om de module op te geven die u wilt verwijderen van de lokale computer.

### Voor beeld 2: de pijp lijn gebruiken om een module te verwijderen

In dit voor beeld wordt de pijp lijn gebruikt om een module te verwijderen.

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

`Get-InstalledModule` maakt gebruik van de para meter **name** om de module op te geven. Het object wordt naar de pijp lijn verzonden `Uninstall-Module` en wordt verwijderd.

## PARAMETERS

### -AllowPrerelease

Hiermee kunt u een module verwijderen die is gemarkeerd als een voorlopige versie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

Hiermee geeft u aan dat u alle beschik bare versies van een module wilt toevoegen. U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion** , **MaximumVersion** of **RequiredVersion** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vraagt u om bevestiging voordat de wordt uitgevoerd `Uninstall-Module` .

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

### -Force

Er wordt geforceerd `Uninstall-Module` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

### -Input object

Hiermee wordt een **PSRepositoryItemInfo** -object geaccepteerd. Bijvoorbeeld: uitvoer `Get-InstalledModule` naar een variabele en de variabele gebruiken als het argument **input object** .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

Hiermee geeft u het maximum of nieuwste versie van de module moet worden verwijderd. De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

Hiermee geeft u de minimum versie op van de module die u wilt verwijderen. De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een matrix van module namen op die moet worden verwijderd.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

Hiermee geeft u het exacte versie nummer van de module die u wilt verwijderen.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Hier wordt weer gegeven wat er gebeurt als er `Uninstall-Module` wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

### System.String[]

### System. Management. Automation. PSObject []

### System. String

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Find-Module](Find-Module.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Publish-Module](Publish-Module.md)

[Save-Module](Save-Module.md)

[Update-Module](Update-Module.md)

