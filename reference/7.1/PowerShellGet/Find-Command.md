---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: 1cd86a1c9abe6c8a4af9f68ed17ea1876ff1bd20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250881"
---
# Find-Command

## SAMENVATTING
Hiermee vindt u Power shell-opdrachten in modules.

## SYNTAXIS

### Alles

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

`Find-Command`Met de cmdlet vindt u Power shell-opdrachten zoals cmdlets, aliassen, functies en werk stromen. `Find-Command` Hiermee worden modules in geregistreerde opslag plaatsen gezocht.

Voor elke opdracht die door wordt gevonden `Find-Command` , wordt een **PSGetCommandInfo** -object geretourneerd. Het **PSGetCommandInfo** -object kan via de pijp lijn naar de cmdlet worden verzonden `Install-Module` .
`Install-Module` installeert de module die de opdracht bevat.

## VOORBEELDEN

### Voor beeld 1: alle opdrachten in een opgegeven opslag plaats zoeken

De `Find-Command` cmdlet zoekt een geregistreerde opslag plaats voor modules.

```powershell
Find-Command -Repository PSGallery | Select-Object -First 10
```

```output
Name                                Version    ModuleName          Repository
----                                -------    ----------          ----------
Disable-AzureRmDataCollection       5.8.3      AzureRM.profile     PSGallery
Disable-AzureRmContextAutosave      5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmDataCollection        5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmContextAutosave       5.8.3      AzureRM.profile     PSGallery
Remove-AzureRmEnvironment           5.8.3      AzureRM.profile     PSGallery
Get-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Set-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Add-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Get-AzureRmSubscription             5.8.3      AzureRM.profile     PSGallery
Connect-AzureRmAccount              5.8.3      AzureRM.profile     PSGallery
```

`Find-Command` gebruikt de para meter **opslagplaats** om de naam van de geregistreerde opslag plaats op te geven. De objecten worden naar beneden verzonden via de pijp lijn. `Select-Object` de objecten worden ontvangen en de **eerste** para meter wordt gebruikt om de eerste tien resultaten weer te geven.

### Voor beeld 2: een opdracht op naam zoeken

`Find-Command` kan de naam van een opdracht gebruiken om de module in een opslag plaats te vinden. Het is mogelijk dat een opdracht naam bestaat in meerdere **ModuleNames**.

```powershell
Find-Command -Repository PSGallery -Name Get-TargetResource
```

```Output
Name                  Version    ModuleName                      Repository
----                  -------    ----------                      ----------
Get-TargetResource    3.1.0.0    xPowerShellExecutionPolicy      PSGallery
Get-TargetResource    1.0.0      xInternetExplorerHomePage       PSGallery
Get-TargetResource    1.2.0.0    SystemLocaleDsc                 PSGallery
```

`Find-Command` gebruikt de para meter **opslagplaats** om te zoeken in de **PSGallery**. De para meter **name** specificeert de opdracht **Get-TargetResource**.

### Voor beeld 3: opdrachten zoeken op naam en de module installeren

`Find-Command` kan de opdracht en module vinden en vervolgens het object naar verzenden `Install-Module` . Als een opdracht is opgenomen in meerdere modules, gebruikt u de `Find-Command` module cmdlets **-name** para meter.
Anders kunnen modules geïnstalleerd zijn die u niet wilt installeren.

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

`Find-Command` maakt gebruik van de para meter **name** om de opdracht **Get-TargetResource** op te geven. De **opslagplaats** parameter zoekt in de **PSGallery**. De para meter **module** naam geeft de module op die u wilt installeren, **SystemLocaleDsc**. Het object wordt naar de pijp lijn verzonden `Install-Module` en de module is geïnstalleerd. Nadat de installatie is voltooid, kunt u gebruiken `Get-InstalledModule` om de resultaten weer te geven.

### Voor beeld 4: een opdracht zoeken en de module opslaan

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

`Find-Command` maakt gebruik van de para meters **name** en **repository** om te zoeken naar de opdracht **invoke-ScriptAnalyzer** in de **PSGallery** -opslag plaats. Het object wordt naar de pijp lijn verzonden `Save-Module` . De para meter **Path** bepaalt de locatie waar de module moet worden opgeslagen. **Uitgebreid** is een optionele para meter, maar de status uitvoer wordt weer gegeven in de Power shell-console. De uitgebreide uitvoer is handig voor het oplossen van problemen.

## PARAMETERS

### -AllowPrerelease

Bevat modules die zijn gemarkeerd als een prerelease in de resultaten.

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

Geeft aan dat met deze cmdlet alle versies van een module worden opgehaald.

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

Hiermee zoekt u naar modules op basis van de zoek syntaxis van de **Package Management** -provider. Geef bijvoorbeeld woorden op waarnaar u wilt zoeken in de **ModuleName** eigenschappen van module **naam en beschrijving** .

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

Hiermee geeft u de naam van een module op die moet worden gezocht naar opdrachten. De standaard instelling is alle modules.

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

Hiermee geeft u de naam van de opdracht waarnaar moet worden gezocht in een opslag plaats. Gebruik komma's om een matrix van opdracht namen te scheiden.

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

Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .

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

Hiermee geeft u de opslag plaats om naar opdrachten te zoeken. Gebruik komma's om een matrix van de namen van opslag plaatsen te scheiden. De standaard instelling is alle opslag plaatsen.

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

Hiermee geeft u de versie van de module op die in de resultaten moet worden meegenomen.

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

### PSGetCommandInfo

`Find-Command` Hiermee wordt een **PSGetCommandInfo** -object uitgevoerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-InstalledModule](Get-InstalledModule.md)

[Installatie-module](Install-Module.md)

[Save-Module](Save-Module.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Uninstall-module](Uninstall-Module.md)

