---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: e285391bdfd68211883827babbc7075e4727f06d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250734"
---
# Uninstall-Script

## SAMENVATTING
Hiermee verwijdert u een script.

## SYNTAXIS

### NameParameterSet (standaard)

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Input object

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Uninstall-Script`Met de cmdlet wordt een opgegeven script verwijderd van de lokale computer.

## VOORBEELDEN

### Voor beeld 1: een script verwijderen

In dit voor beeld wordt een script verwijderd.

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

`Uninstall-Script` maakt gebruik van de para meter **name** om het script op te geven dat van de lokale computer moet worden verwijderd.

### Voor beeld 2: de pijp lijn gebruiken om een script te verwijderen

In dit voor beeld wordt de pijp lijn gebruikt voor het verwijderen van een script.

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

`Get-InstalledScript` maakt gebruik van de para meter **name** om het script op te geven. Het object wordt naar de pijp lijn verzonden `Uninstall-Script` en het script wordt verwijderd.

## PARAMETERS

### -AllowPrerelease

Hiermee kunt u een script dat is gemarkeerd als Prerelease, verwijderen.

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

Vraagt u om bevestiging voordat deze wordt uitgevoerd `Uninstall-Script` .

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

Er wordt geforceerd `Uninstall-Script` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

Hiermee wordt een **PSRepositoryItemInfo** -object geaccepteerd. Bijvoorbeeld: uitvoer `Get-InstalledScript` naar een variabele en de variabele gebruiken als het argument **input object** .

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

Hiermee geeft u het maximum of nieuwste versie van het script op dat moet worden verwijderd. De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.

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

Hiermee geeft u de minimum versie van het script dat moet worden verwijderd. De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.

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

Hiermee geeft u een matrix met script namen op die moet worden verwijderd.

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

Hiermee geeft u het exacte versie nummer van het script dat moet worden verwijderd.

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

Hier wordt weer gegeven wat er gebeurt als er `Uninstall-Script` wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

`Uninstall-Script` Hiermee worden **PSRepositoryItemInfo** -objecten geaccepteerd vanuit de pijp lijn.

### System. String

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Zoeken-script](Find-Script.md)

[Install-script](Install-Script.md)

[Publish-Script](Publish-Script.md)

[Save-Script](Save-Script.md)

[Update-script](Update-Script.md)
