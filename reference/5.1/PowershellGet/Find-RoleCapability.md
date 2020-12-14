---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: d3300e0f378139cc873ffef1e798326100644d94
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889807"
---
# Find-RoleCapability

## SAMENVATTING
Hiermee vindt u functie mogelijkheden in modules.

## SYNTAXIS

### Alles

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
[-Repository <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Find-RoleCapability` cmdlet zoekt geregistreerde opslag plaatsen om de Power shell-functies en-modules te vinden.

Voor elke functie die door wordt gevonden `Find-RoleCapability` , wordt een **PSGetRoleCapabilityInfo** -object geretourneerd. **PSGetRoleCapabilityInfo** -objecten kunnen naar de `Install-Module` of cmdlets in de pijp lijn worden verzonden `Save-Module` .

Met Power shell-functie functies definieert u welke opdrachten en toepassingen beschikbaar zijn voor een gebruiker op een JEA-eind punt (genoeg aan het beheer). Functie mogelijkheden worden gedefinieerd door bestanden met een `.psrc` extensie.

## VOORBEELDEN

### Voor beeld 1: functie mogelijkheden zoeken

`Find-RoleCapability` Hiermee vindt u functie mogelijkheden in elke geregistreerde opslag plaats. Als u een specifieke opslag plaats wilt doorzoeken, gebruikt u de para meter **opslagplaats** .

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### Voor beeld 2: functie mogelijkheden op naam zoeken

`Find-RoleCapability` Hiermee zoekt u functie mogelijkheden op naam. Gebruik komma's om een matrix met namen van elkaar te scheiden.

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### Voor beeld 3: de module van een functie mogelijkheid zoeken en opslaan

De `Find-RoleCapability` cmdlet vindt een functie en verzendt het object omlaag in de pijp lijn.
`Save-Module` Hiermee wordt de module van de functie capaciteit opgeslagen in een bestands systeem. `Get-ChildItem` Hiermee wordt de inhoud van de map van de module weer gegeven.

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

`Find-RoleCapability` maakt gebruik van de para meter **name** om de functie van **algemene Lev1** te specificeren.
Het object wordt via de pijp lijn verzonden. `Save-Module` gebruikt de para meter **Path** voor de locatie van het bestands systeem om de module op te slaan. Nadat de module is opgeslagen, `Get-ChildItem` geeft u het **pad** van de module op en geeft u de inhoud van de map van de **JeaExamples** -module weer.

### Voor beeld 4: de module van een functie mogelijkheid zoeken en installeren

`Find-RoleCapability` zoekt de module en verzendt het object omlaag in de pijp lijn. `Install-Module` installeert de module. Na de installatie, gebruikt `Get-InstalledModule` u om de resultaten te bekijken.

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

`Find-RoleCapability` maakt gebruik van de para meter **name** om de functie van **algemene Lev1** te specificeren.
Het object wordt via de pijp lijn verzonden. `Install-Module` maakt gebruik van de para meter **uitgebreid** om status berichten tijdens de installatie weer te geven. Nadat de installatie is voltooid, wordt `Get-InstalledModule` met de uitvoer bevestigd dat de **JeaExamples** -module is geïnstalleerd.

## PARAMETERS

### -AllowPrerelease

Bevat resources die zijn gemarkeerd als een prerelease in de resultaten.

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

Geeft aan dat met deze cmdlet alle versies van een module worden opgehaald. Met de para meter **AllVersions** worden alle beschik bare versies van een module weer gegeven.

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

### -Filter

Zoekt bronnen op basis van de zoek syntaxis van de **Package Management** -provider. Geef bijvoorbeeld woorden op waarnaar u wilt zoeken in de  eigenschappen van module **naam en beschrijving** .

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

### -MaximumVersion

Hiermee geeft u de maximum versie van de module op die in resultaten moet worden meegenomen. De **MaximumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.

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

Hiermee geeft u de minimale versie van de module op die in de resultaten moet worden meegenomen. De **MinimumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.

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

### -Module naam

Hiermee geeft u de naam op van de module waarin u wilt zoeken naar functie mogelijkheden. De standaard instelling is alle modules.

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

Hiermee geeft u de naam van een functie mogelijkheid. De standaard waarde is alle functie mogelijkheden. Gebruik komma's om een matrix met resource namen te scheiden.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Proxy

Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven in de **proxy** para meter.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Opslag plaats

Hiermee geeft u een opslag plaats voor het zoeken naar functie mogelijkheden. Gebruik komma's om een matrix van de namen van opslag plaatsen te scheiden.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Hiermee geeft u het exacte versie nummer van de module op die in de resultaten moet worden meegenomen. De **RequiredVersion** -en **MinimumVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.

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

### -Tag

Hiermee geeft u labels op waarmee modules in een opslag plaats worden gecategoriseerd. Gebruik komma's om een matrix met tags te scheiden.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

### PSGetRoleCapabilityInfo

De `Find-RoleCapability` cmdlet retourneert een **PSGetRoleCapabilityInfo** -object.

## OPMERKINGEN

> [!IMPORTANT]
> Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1. Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery. Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Get-Child item](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Installatie-module](Install-Module.md)

[New-PSRoleCapabilityFile](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[Save-Module](Save-Module.md)
