---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: e894e2f71e0a76badd05b86b42903d49aab4af0b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250248"
---
# Get-InstalledModule

## SAMENVATTING
Hiermee wordt een lijst met modules opgehaald op de computer die is geïnstalleerd door PowerShellGet.

## SYNTAXIS

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-InstalledModule` cmdlet haalt Power shell-modules op die zijn geïnstalleerd op een computer met behulp van PowerShellGet. Als u alle modules die op het systeem zijn geïnstalleerd wilt weer geven, gebruikt u de `Get-Module -ListAvailable` opdracht.

## VOORBEELDEN

### Voor beeld 1: alle geïnstalleerde modules ophalen

```powershell
Get-InstalledModule
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
2.0.0      PSGTEST-UploadMultipleVersionOfP... Module     GalleryINT     Module for DAC functionality
1.3.5      AzureAutomationDebug                Module     PSGallery      Module for debugging Azure Automation runbooks, emulating AA native cmdlets
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

Met deze opdracht worden alle geïnstalleerde modules opgehaald.

### Voor beeld 2: specifieke versies van een module ophalen

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

Met deze opdracht worden versies van de module AzureRM. Automation van versie 1,0 tot versie 2,0.

## PARAMETERS

### -AllowPrerelease

Bevat de resultaten modules die als een voorlopige versie zijn gemarkeerd.

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

### -AllVersions

Hiermee wordt aangegeven dat u alle beschik bare versies van een module wilt ophalen.
U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion** , **MaximumVersion** of **RequiredVersion** .

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

### -MaximumVersion

Hiermee geeft u de maximale of nieuwste versie van een module op die u wilt ophalen. De para meters **MaximumVersion** en **RequiredVersion** sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

Hiermee geeft u de minimum versie op van één module die moet worden opgehaald. De para meters **MinimumVersion** en **RequiredVersion** sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een matrix met namen van modules op die moet worden opgehaald.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

Hiermee geeft u de exacte versie op van een module die u wilt ophalen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

## UITVOER

### System. Management. Automation. PSCustomObject

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN
