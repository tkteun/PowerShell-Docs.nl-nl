---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: e1cb814d349d6b77885ebaaf176a7c3153d93eb5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889367"
---
# Find-DscResource

## SAMENVATTING
Zoekt naar desired state Configuration (DSC)-resources.

## SYNTAXIS

### Alles

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Find-DscResource` cmdlet zoekt geregistreerde opslag plaatsen om DSC-resources in modules te vinden. Standaard `Find-DscResource` doorzoekt alle geregistreerde opslag plaatsen.

Voor elke module die door wordt gevonden `Find-DscResource` , wordt een **PSGetDscResourceInfo** -object geretourneerd.
**PSGetDscResourceInfo** -objecten kunnen naar de-cmdlet worden verzonden door de pijp lijn `Install-Module` .
`Install-Module` installeert de module.

## VOORBEELDEN

### Voor beeld 1: alle DSC-resources zoeken

`Find-DscResource` Hiermee worden DSC-resources uit de geregistreerde opslag plaatsen geretourneerd. Als u een specifieke opslag plaats wilt doorzoeken, gebruikt u de para meter **opslagplaats** .

```powershell
Find-DscResource
```

```Output
Name                           Version    ModuleName                     Repository
----                           -------    ----------                     ----------
Carbon_Privilege               2.8.1      Carbon                         PSGallery
Carbon_ScheduledTask           2.8.1      Carbon                         PSGallery
Carbon_Service                 2.8.1      Carbon                         PSGallery
PackageManagement              1.4        PackageManagement              PSGallery
PackageManagementSource        1.4        PackageManagement              PSGallery
PSModule                       2.1.4      PowerShellGet                  PSGallery
PSRepository                   2.1.4      PowerShellGet                  PSGallery
xArchive                       8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xDSCWebService                 8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xEnvironment                   8.7.0.0    xPSDesiredStateConfiguration   PSGallery
```

### Voor beeld 2: een DSC-resource op naam zoeken

`Find-DscResource` DSC-resources zoeken op naam. Gebruik komma's om een matrix met resource namen te scheiden.

```powershell
Find-DscResource -Name xWebsite, xWebApplication, xWebSiteDefaults
```

```Output
Name               Version    ModuleName            Repository
----               -------    ----------            ----------
xWebApplication    2.6.0.0    xWebAdministration    PSGallery
xWebsite           2.6.0.0    xWebAdministration    PSGallery
xWebSiteDefaults   2.6.0.0    xWebAdministration    PSGallery
```

`Find-DscResource` maakt gebruik van de para meter **name** om de opgegeven matrix van DSC-resources te zoeken.

### Voor beeld 3: een DSC-resource zoeken en installeren

`Find-DscResource` zoekt een DSC-resource en stuurt het object omlaag in de pijp lijn die moet worden geïnstalleerd.
Na de installatie gebruikt `Get-InstalledModule` u om de resultaten weer te geven.

Er kunnen meerdere resources van dezelfde module naar de pijp lijn worden verzonden `Install-Module` .
`Install-Module` probeert de module alleen eenmaal te installeren.

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

`Find-DscResource` maakt gebruik van de para meter **name** om de resource met de naam **xWebsite** te zoeken. Het object wordt vanuit de pijp lijn naar de `Install-Module` cmdlet verzonden. `Install-Module` Hiermee installeert u de **xWebAdministration** -module voor de resource.

### Voor beeld 4: alle DSC-resources in een module zoeken

`Find-DscResource` Hiermee worden alle DSC-resources in een opgegeven module gevonden. Standaard wordt de huidige versie weer gegeven. Als u andere versies wilt weer geven, gebruikt u de para meters **AllVersions** of **RequiredVersions** .

```powershell
Find-DscResource -ModuleName xWebAdministration
```

```Output
Name                                Version    ModuleName              Repository
----                                -------    ----------              ----------
WebApplicationHandler               2.6.0.0    xWebAdministration      PSGallery
xIisFeatureDelegation               2.6.0.0    xWebAdministration      PSGallery
xIisHandler                         2.6.0.0    xWebAdministration      PSGallery
xIisLogging                         2.6.0.0    xWebAdministration      PSGallery
```

`Find-DscResource` maakt gebruik van de para meter **module** om de **xWebAdministration** op te geven en de DSC-resources in de module te vinden. De huidige versie van elke resource wordt weer gegeven.

### Voor beeld 5: een DSC-resource zoeken op label en vereiste versie

DSC-resources kunnen worden gevonden met behulp van de para meters **tag** en **RequiredVersion**. **Tag** geeft de huidige versie weer van elke resource die het opgegeven label bevat in de opslag plaats.
**RequiredVersion** moet de  para meter voor de module **naam** hebben en de para meter name is optioneel. De para meters **name en naam** **module** beperken de uitvoer. Gebruik de para meter **AllVersions** om de beschik bare versies van een DSC-resource weer te geven.

```powershell
Find-DscResource -ModuleName xWebAdministration -Tag DSC -RequiredVersion 1.20
```

```output
Name                    Version    ModuleName             Repository
----                    -------    ----------             ----------
xIisFeatureDelegation   1.20.0.0   xWebAdministration     PSGallery
xIisHandler             1.20.0.0   xWebAdministration     PSGallery
xIisLogging             1.20.0.0   xWebAdministration     PSGallery
xIisMimeTypeMapping     1.20.0.0   xWebAdministration     PSGallery
```

### Voor beeld 6: een resource zoeken met behulp van een filter

`Find-DscResource` Hiermee worden alle resources gevonden en de **filter** parameter gebruikt om de resultaten op basis van het **domein** op te geven. De **filter** parameter zoekt de filter waarde in de beschrijving of module naam van het object. Gebruik de `Select-Object` cmdlet om de eigenschappen van een object weer te geven.

```powershell
Find-DscResource -Filter Domain
```

```output
Name                    Version    ModuleName                 Repository
----                    -------    ----------                 ---------
xComputer               4.1.0.0    xComputerManagement        PSGallery
Computer                6.4.0.0    ComputerManagementDsc      PSGallery
xDSCDomainjoin          1.1        xDSCDomainjoin             PSGallery
xDisk                   1.0        xDisk                      PSGallery
xDSCFirewall            1.6.21     xDSCFirewall               PSGallery
dmAwsTagInstance        1.0.1      domainAwsDSCResources      PSGallery
```

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

Met de para meter **AllVersions** worden alle beschik bare versies van een DSC-resource weer gegeven. U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion**, **MaximumVersion** of **RequiredVersion** .

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

Hiermee geeft u de maximum versie van de resource op die in de resultaten moet worden meegenomen. De **MaximumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.

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

Hiermee geeft u de minimale versie van de resource op die moet worden meegenomen in de resultaten. De **MinimumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.

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

Hiermee geeft u een module die de DSC-resource bevat.

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

Hiermee geeft u de naam van een resource. De standaard waarde is alle resources. Gebruik komma's om een matrix met resource namen te scheiden.

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

Hiermee geeft u een opslag plaats voor het zoeken naar resources op. Gebruik komma's om een matrix van de namen van opslag plaatsen te scheiden.

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

### PSGetDscResourceInfo

`Find-DscResource` retourneert een **PSGetDscResourceInfo** -object.

## OPMERKINGEN

> [!IMPORTANT]
> Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1. Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery. Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Get-InstalledModule](Get-InstalledModule.md)

[Installatie-module](Install-Module.md)

[REGI ster-PSRepository](Register-PSRepository.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Uninstall-module](Uninstall-Module.md)
