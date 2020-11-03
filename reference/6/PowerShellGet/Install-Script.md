---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/install-script?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Script
ms.openlocfilehash: ecae1ba3a3aea6628817bab2f09fc23e23162f03
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250937"
---
# Install-Script

## SAMENVATTING
Hiermee wordt een script geïnstalleerd.

## SYNTAXIS

### NameParameterSet (standaard)

```
Install-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Scope <String>] [-NoPathUpdate]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Input object

```
Install-Script [-InputObject] <PSObject[]> [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Install-Script` cmdlet wordt een script lading opgehaald uit een opslag plaats, wordt gecontroleerd of de payload een geldig Power shell-script is en wordt het script bestand gekopieerd naar een opgegeven installatie locatie.

De standaard opslagplaatsen `Install-Script` kunnen worden geconfigureerd met behulp van `Register-PSRepository` de `Set-PSRepository` `Unregister-PSRepository` cmdlets,, en `Get-PSRepository` . Bij het werken met meerdere opslag plaatsen `Install-Script` installeert het eerste script dat overeenkomt met de opgegeven zoek criteria ( **name** , **MinimumVersion** of **MaximumVersion** ) van de eerste opslag plaats zonder enige fout.

## VOORBEELDEN

### Voor beeld 1: een script zoeken en installeren

```
PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2"
Version    Name                           Type       Repository           Description
-------    ----                           ----       ----------           -----------
2.5        Required-Script2               Script     local1               Description for the Required-Script2 script

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
PS C:\> Get-Command -Name "Required-Script2"
CommandType     Name                      Version    Source
-----------     ----                      -------    ------
ExternalScript  Required-Script2.ps1      2.0       C:\Users\pattif\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1

PS C:\> Get-InstalledScript -Name "Required-Script2"
Version    Name                  Type     Repository           Description
-------    ----                  ----     ----------           -----------
2.5        Required-Script2      Script   local1               Description for the Required-Script2 script

PS C:\> Get-InstalledScript -Name "Required-Script2" | Format-List *
Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\pattif\Documents\WindowsPowerShell\Scripts
```

Met de eerste opdracht vindt u het script met de naam `Required-Script2` uit de Local1-opslag plaats en worden de resultaten weer gegeven.

Met de tweede opdracht wordt het `Required-Script2` script gevonden en vervolgens de pijplijn operator gebruikt om het door te geven aan de `Install-Script` cmdlet om het te installeren.

De derde opdracht gebruikt de `Get-Command` cmdlet om op te halen `Required-Script2` . vervolgens worden de resultaten weer gegeven.

De vierde opdracht gebruikt de `Get-InstalledScript` cmdlet om de resultaten op te halen `Required-Script2` en weer te geven.

Met de vijfde opdracht wordt `Required-Script2` de pijplijn operator opgehaald en gebruikt om deze door te geven aan de `Format-List` cmdlet om de uitvoer op te maken.

### Voor beeld 2: een script met AllUsers-bereik installeren

```
PS C:\> Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
PS C:\> Get-InstalledScript -Name "Required-Script3"
Version    Name                  Type       Repository    Description
-------    ----                  ----       ----------    -----------
2.5        Required-Script3      Script     local1        Description for the Required-Script3 script

PS C:\> Get-InstalledScript -Name "Required-Script3" | Format-List *
Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts
```

Met de eerste opdracht wordt het script geïnstalleerd met de naam `Required-Script3` en wordt het ALLUSERS-bereik toegewezen.

Met de tweede opdracht wordt het geïnstalleerde script opgehaald `Required-Script3` en informatie hierover weer gegeven.

Met de derde opdracht wordt `Required-Script3` de pijplijn operator opgehaald en gebruikt om deze door te geven aan de `Format-List` cmdlet om de uitvoer op te maken.

### Voor beeld 3: een script en de bijbehorende afhankelijkheden installeren

```
PS C:\> Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script

PS C:\> Get-InstalledModule
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script*"
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Required-Script*"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
```

Met de eerste opdracht vindt u het script met de naam `Script-WithDependencies2` en de bijbehorende afhankelijkheden in de Local1-opslag plaats en worden de resultaten weer gegeven.

De tweede opdracht wordt geïnstalleerd `Script-WithDependencies2` .

De derde opdracht gebruikt de `Get-InstalledScript` script-cmdlet om geïnstalleerde scripts op te halen en de resultaten weer te geven.

De vierde opdracht gebruikt de `Get-InstalledModule` cmdlet om geïnstalleerde modules op te halen en de resultaten weer te geven.

De vijfde opdracht gebruikt de `Find-Script` cmdlet om scripts te zoeken waarvan de naam begint met `Required-Script` en de resultaten weer te geven.

De zesde opdracht installeert de scripts waarvan de naam begint met `Required-Script` in de Local1-opslag plaats.

Met de laatste opdracht worden de geïnstalleerde scripts opgehaald en worden de resultaten weer gegeven.

## PARAMETERS

### -AcceptLicense

Accepteer de gebruiksrecht overeenkomst automatisch tijdens de installatie als deze vereist is voor de module.

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

### -AllowPrerelease

Hiermee kunt u een script installeren dat is gemarkeerd als Prerelease.

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

### -Credential

Hiermee geeft u een gebruikers account op dat beschikt over rechten voor het installeren van een script voor een opgegeven pakket provider of bron.

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

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

Wordt gebruikt voor de invoer van de pijp lijn.

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

Hiermee geeft u de maximum versie van één script op dat moet worden geïnstalleerd. U kunt deze para meter niet toevoegen als u probeert meerdere scripts te installeren. De **MaximumVersion** en de **RequiredVersion** -para meters sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.

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

Hiermee geeft u de minimum versie van één script op dat moet worden geïnstalleerd. U kunt deze para meter niet toevoegen als u probeert meerdere scripts te installeren. De **MinimumVersion** en de **RequiredVersion** -para meters sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.

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

Hiermee geeft u een matrix met namen van te installeren scripts op.

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

### -NoPathUpdate

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

### -PassThru

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

### -Proxy

Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.

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

Hiermee geeft u de beschrijvende naam op van een opslag plaats die is geregistreerd bij de `Register-PSRepository` cmdlet. De standaard instelling is alle geregistreerde opslag plaatsen.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Hiermee geeft u het exacte versie nummer van het script op dat moet worden geïnstalleerd.

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

### -Bereik

Hiermee geeft u het installatie bereik van het script.
Geldige waarden zijn: AllUsers en CurrentUser.

Met het AllUsers-bereik kunnen modules worden geïnstalleerd op een locatie die toegankelijk is voor alle gebruikers van de computer, dat wil zeggen `$env:ProgramFiles\WindowsPowerShell\Scripts` .

Met het bereik CurrentUser kunnen modules alleen worden geïnstalleerd op `$home\Documents\WindowsPowerShell\Scripts` , zodat de module alleen beschikbaar is voor de huidige gebruiker.

Als er geen **bereik** is gedefinieerd, wordt de standaard waarde ingesteld op basis van de huidige sessie:

- Voor een Power shell-sessie met verhoogde bevoegdheid, wordt standaard de **Scope** ALLUSERS.
- Voor niet-verhoogde Power shell-sessies in [PowerShellGet-versies 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) en hoger, is de **Scope** CurrentUser;
- Voor niet-verhoogde Power shell-sessies in PowerShellGet-versies 1.6.7 en eerder, is het **bereik** niet gedefinieerd en `Install-Module` mislukt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

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

### System. URI

### System. Management. Automation. PSCredential

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Zoeken-script](Find-Script.md)

[Publish-Script](Publish-Script.md)

[Save-Script](Save-Script.md)

[Uninstall-script](Uninstall-Script.md)

[Update-script](Update-Script.md)
