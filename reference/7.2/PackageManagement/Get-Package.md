---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: c26365eb5b4833c4982fa54e742521cf72307e99
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889494"
---
# Get-Package

## SAMENVATTING
Retourneert een lijst met alle software pakketten die zijn geïnstalleerd met **Package Management**.

## SYNTAXIS

### NuGet

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### PowerShellGet

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Package` cmdlet retourneert een lijst met alle software pakketten op de lokale computer die is geïnstalleerd met **Package Management**. U kunt uitvoeren `Get-Package` op externe computers door deze uit te voeren als onderdeel van een `Invoke-Command` `Enter-PSSession` opdracht of script.

## VOORBEELDEN

### Voor beeld 1: alle geïnstalleerde pakketten ophalen

De `Get-Package` cmdlet haalt alle pakketten op die zijn geïnstalleerd op de lokale computer.

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### Voor beeld 2: pakketten ophalen die zijn geïnstalleerd op een externe computer

Met deze opdracht wordt een lijst opgehaald met pakketten die zijn geïnstalleerd door **Package Management** op een externe computer. Met deze opdracht wordt u gevraagd het wacht woord van de opgegeven gebruiker op te geven.

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

`Invoke-Command` maakt gebruik van de para meter **ComputerName** om een externe computer op te geven, **Server01**. De **referentie** parameter bevat een domein-en gebruikers naam met machtigingen voor het uitvoeren van opdrachten op de computer. De para meter **script Block** voert de `Get-Package` cmdlet uit op de externe computer.

### Voor beeld 3: pakketten voor een opgegeven provider ophalen

Met deze opdracht worden software pakketten die zijn geïnstalleerd op de lokale computer van een specifieke provider opgehaald.

```powershell
Get-Package -ProviderName PowerShellGet -AllVersions
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.2.2        https://www.powershellgallery.com/api/v2   PowerShellGet
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
posh-git              0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
PowerShellGet         2.0.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

`Get-Package` maakt gebruik van de para meter **ProviderName** om een specifieke provider op te geven, **PowerShellGet**.
In de para meter **all-versions** wordt elke geïnstalleerde versie weer gegeven.

### Voor beeld 4: een exacte versie van een specifiek pakket ophalen

Met deze opdracht wordt een specifieke versie van een geïnstalleerd pakket opgehaald. Er kan meer dan één versie van een pakket worden geïnstalleerd.

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

`Get-Package` maakt gebruik van de para meter **name** om de naam van het pakket op te geven, **Package Management**. De para meter **ProviderName** specificeert de provider, **PowerShellGet**. De **vereiste-versie** parameter geeft een geïnstalleerde versie op.

### Voor beeld 5: een pakket verwijderen

In dit voor beeld worden pakket gegevens opgehaald en wordt het pakket vervolgens verwijderd.

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

`Get-Package` maakt gebruik van de para meter **name** om de naam van het pakket op te geven, **posh-Git**. De **RequiredVersion** -para meter is een specifieke versie van het pakket. Het object wordt vanuit de pijp lijn naar de `Uninstall-Package` cmdlet verzonden. `Uninstall-Package` Hiermee verwijdert u het pakket.

## PARAMETERS

### -AllowClobber

Onderdrukt waarschuwings berichten over conflicten met bestaande opdrachten. Overschrijft bestaande opdrachten die dezelfde naam hebben als opdrachten die door een module worden geïnstalleerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

Bevat pakketten die zijn gemarkeerd als een prerelease in de resultaten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

Hiermee wordt aangegeven dat `Get-Package` alle beschik bare versies van het pakket worden geretourneerd. `Get-Package`Retourneert standaard alleen de nieuwste beschik bare versie.

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

### -Bestemming

Hiermee geeft u het pad op naar een map die uitgepakte pakket bestanden bevat.

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExcludeVersion

Schakel over om het versie nummer in het mappad uit te sluiten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### -ForceBootstrap

Geeft aan `Get-Package` dat **Package Management** automatisch de pakket provider installeert.

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

### -InstallUpdate

Geeft aan dat met deze cmdlet updates worden geïnstalleerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

Hiermee geeft u de maximale pakket versie op die u wilt zoeken.

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

Hiermee geeft u de minimale pakket versie op die u wilt zoeken. Als er een hogere versie beschikbaar is, wordt die versie geretourneerd.

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

Hiermee geeft u een of meer pakket namen of pakket namen met Joker tekens op. Scheid meerdere pakket namen met komma's.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -NoPathUpdate

**NoPathUpdate** is alleen van toepassing op de `Install-Script` cmdlet. **NoPathUpdate** is een dynamische para meter die door de provider wordt toegevoegd en niet wordt ondersteund door `Get-Package` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

Hiermee geeft u de naam van een pakket beheer provider.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

Hiermee geeft u een of meer pakket provider namen op. Scheid meerdere pakket provider namen met komma's.
Gebruiken `Get-PackageProvider` om een lijst met beschik bare pakket providers op te halen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

Hiermee geeft u de exacte versie van het pakket op dat moet worden gevonden.

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

### -Bereik

Hiermee geeft u het zoek bereik voor het pakket op.

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

### -SkipDependencies

Switch waarmee wordt aangegeven dat er geen pakket afhankelijkheden moeten worden gevonden.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipPublisherCheck

Hiermee kunt u een pakket versie ophalen die nieuwer is dan de geïnstalleerde versie. Bijvoorbeeld een geïnstalleerd pakket dat digitaal is ondertekend door een vertrouwde uitgever, maar een nieuwe versie niet digitaal is ondertekend.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of een van beide.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

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

### SoftwareIdentity []

## OPMERKINGEN

Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet. Dynamische para meters zijn specifiek voor een pakket provider. De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider. `Get-Package`Heeft bijvoorbeeld de para meter **PowerShellGet** met de waarde `-NoPathUpdate` , `AllowClobber` en `SkipPublisherCheck` .

> [!IMPORTANT]
> Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1. Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery. Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Enter-PSSession](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[Zoeken-pakket](Find-Package.md)

[Get-Help](../Microsoft.PowerShell.Core/Get-Help.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Get-PackageSource](Get-PackageSource.md)

[Install-Package](Install-Package.md)

[Invoke-opdracht](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Opslaan-pakket](Save-Package.md)

[Uninstall-pakket](Uninstall-Package.md)
