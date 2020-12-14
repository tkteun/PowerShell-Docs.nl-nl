---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: cca73714cebf8f0d527c669358458f8509b80a90
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889518"
---
# Find-PackageProvider

## SAMENVATTING
Retourneert een lijst met pakket beheer pakket providers die beschikbaar zijn voor installatie.

## SYNTAXIS

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **find-package provider** vindt u overeenkomende Package Management-providers die beschikbaar zijn in pakket bronnen die zijn geregistreerd bij PowerShellGet.
Dit zijn pakket providers die beschikbaar zijn voor installatie met de cmdlet Install-PackageProvider.
Dit omvat standaard modules die beschikbaar zijn in de PowerShell Gallery met de labels **Package Management** en **provider** .

Met **find-package provider** vindt u ook overeenkomende pakket beheer providers die beschikbaar zijn in de Azure Blob Store van het pakket beheer.
Gebruik de Boots Trapper-provider om ze te zoeken en te installeren.

## VOORBEELDEN

### Voor beeld 1: alle beschik bare pakket providers zoeken

```
PS C:\> Find-PackageProvider
```

Met deze opdracht wordt een lijst van alle pakket providers opgehaald die beschikbaar zijn op de opslag plaatsen die worden ondersteund door Package Management.
Deze pakket providers zijn standaard beschikbaar op het PowerShell Gallery en met behulp van de toepassing voor het Boots trappen van het pakket beheer.

### Voor beeld 2: alle versies van een provider zoeken

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

Met deze opdracht vindt u alle versies van de pakket provider met de naam Nuget.

### Voor beeld 3: een provider uit een opgegeven bron zoeken

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

Met deze opdracht wordt een pakket provider gevonden die beschikbaar is via een opgegeven pakket bron.

## PARAMETERS

### -AllVersions

Geeft aan dat met deze cmdlet alle beschik bare versies van de pakket provider worden geretourneerd.
**Zoek-package provider** retourneert standaard alleen de nieuwste beschik bare versie.

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

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om te zoeken naar pakket providers.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.
Op dit moment is dit gelijk aan de para meter *ForceBootstrap* .

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

### -ForceBootstrap

Geeft aan dat deze cmdlet pakket beheer afdwingt om de pakket provider automatisch te installeren.

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

### -IncludeDependencies

Geeft aan dat deze cmdlet afhankelijkheden bevat.

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

Hiermee geeft u de Maxi maal toegestane versie van de pakket provider die u wilt zoeken.
Als u deze para meter niet toevoegt, zoekt **package provider** de hoogste beschik bare versie van de provider.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

Hiermee geeft u de mini maal toegestane versie van de pakket provider die u wilt zoeken.
Als u deze para meter niet toevoegt, zoekt **find-package provider** de hoogste beschik bare versie van het pakket dat ook voldoet aan de maximum opgegeven versie die is opgegeven door de para meter *MaximumVersion* .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een of meer module namen van pakket providers, of provider namen met Joker tekens.
Scheid meerdere pakket namen met komma's.

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

### -Proxy

Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Hiermee geeft u de exacte toegestane versie van de pakket provider die u wilt zoeken.
Als u deze para meter niet toevoegt, zoekt **find-package provider** de hoogste beschik bare versie van de provider die ook voldoet aan de maximum versie die is opgegeven door de para meter *MaximumVersion* .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Hiermee geeft u een of meer pakket bronnen op.
U kunt een lijst met beschik bare pakket bronnen ophalen met behulp van de cmdlet Get-PackageSource.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

### Micro soft. package management. verpakking. SoftwareIdentity

Met deze cmdlet wordt een **SoftwareIdentity** -object geretourneerd.
Een **SoftwareIdentity** -object kan worden gepiped in **install-package provider** om de resultaten van **zoeken-package provider** te installeren.

## OPMERKINGEN

> [!IMPORTANT]
> Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1. Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery. Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Registratie ongedaan maken-PackageSource](Unregister-PackageSource.md)

[Get-PackageSource](Get-PackageSource.md)

[REGI ster-PackageSource](Register-PackageSource.md)

[Install-package provider](Install-PackageProvider.md)
