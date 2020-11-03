---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: 6b99eb73fb126b67b97fc360b2f0474710b4cc52
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250866"
---
# Get-InstalledScript

## SAMENVATTING
Hiermee wordt een geïnstalleerd script opgehaald.

## SYNTAXIS

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **Get-InstalledScript** haalt geïnstalleerde scripts op voor het bereik van CurrentUser en ALLUSERS.

## VOORBEELDEN

### Voor beeld 1: alle geïnstalleerde scripts ophalen

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

Met deze opdracht worden alle geïnstalleerde scripts opgehaald.

### Voor beeld 2: geïnstalleerde scripts op naam ophalen

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

Met deze opdracht wordt een script opgehaald waarbij de naam begint met vereist-SCRI.

## PARAMETERS

### -AllowPrerelease

Bevat de resultaten scripts die als Prerelease zijn gemarkeerd.

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

Hiermee geeft u het maximum, of de meest recente versie van een script op dat moet worden opgehaald.
De para meters *MaximumVersion* en *RequiredVersion* sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.

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

Hiermee geeft u de minimum versie op van een script dat moet worden opgehaald.
De para meters *MinimumVersion* en *RequiredVersion* sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.

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

Hiermee geeft u een matrix met namen van te verkrijgen scripts op.
Joker tekens worden geaccepteerd.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -RequiredVersion

Hiermee geeft u de exacte versie van een script op dat moet worden opgehaald.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System.String[]

### System. String

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Install-script](Install-Script.md)

[Uninstall-script](Uninstall-Script.md)

