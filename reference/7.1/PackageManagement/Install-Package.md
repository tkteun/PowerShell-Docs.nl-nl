---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 7a99c4c00f809c2ec418618b2c1322d2552d1120
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250888"
---
# Install-Package

## SAMENVATTING
Hiermee worden een of meer software pakketten geïnstalleerd.

## SYNTAXIS

### PackageBySearch (standaard)

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### PackageByInputObject

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### NuGet: PackageBySearch

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### NuGet: PackageByInputObject

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### PowerShellGet: PackageBySearch

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### PowerShellGet: PackageByInputObject

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## BESCHRIJVING

`Install-Package`Met de cmdlet worden een of meer software pakketten op de lokale computer geïnstalleerd. Als u meerdere software bronnen hebt, gebruikt `Get-PackageProvider` en `Get-PackageSource` om details over uw providers weer te geven.

## VOORBEELDEN

### Voor beeld 1: een pakket installeren op pakket naam

`Install-Package`Met de cmdlet worden een software pakket en de bijbehorende afhankelijkheden geïnstalleerd.

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

`Install-Package` maakt gebruik van para meters om de **naam** en **bron** van het pakket op te geven. De para meter **Credential** maakt gebruik van een domein gebruikers account met machtigingen voor het installeren van pakketten. De opdracht vraagt u om het wacht woord voor het gebruikers account.

### Voor beeld 2: Find-Package gebruiken om een pakket te installeren

In dit voor beeld wordt het object dat `Find-Package` wordt geretourneerd door, verzonden door de pijp lijn en geïnstalleerd door `Install-Package` .

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

`Find-Package` maakt gebruik van de **name** -en **Source** -para meters voor het zoeken van een pakket. Het object wordt via de pijp lijn verzonden en `Install-Package` het pakket wordt op de lokale computer geïnstalleerd.

### Voor beeld 3: pakketten installeren door een reeks versies op te geven

`Install-Package` maakt gebruik van de para meters **MinimumVersion** en **MaximumVersion** om een reeks software versies op te geven.

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

`Install-Package` maakt gebruik van de **naam** en de **bron** parameters om een pakket te vinden. De para meters **MinimumVersion** en **MaximumVersion** geven een reeks software versies op. De hoogste versie in het bereik is geïnstalleerd.

## PARAMETERS

### -AcceptLicense

 **AcceptLicense** accepteert de licentie overeenkomst automatisch tijdens de installatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowClobber

Onderdrukt waarschuwings berichten over conflicten met bestaande opdrachten. Overschrijft bestaande opdrachten die dezelfde naam hebben als de opdrachten die worden geïnstalleerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

Hiermee kan de installatie van pakketten die zijn gemarkeerd als Prerelease.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

`Install-Package` Hiermee worden alle beschik bare versies van het pakket geïnstalleerd. Standaard wordt alleen de nieuwste versie geïnstalleerd.

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

### -Opdracht

Hiermee geeft u een of meer opdrachten op die worden `Install-Package` doorzocht.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigFile

Hiermee geeft u een pad op dat een configuratie bestand bevat.

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bevat

`Install-Package` haalt objecten op als de para meter **contains** een waarde bevat die overeenkomt met de eigenschaps waarden van het object.

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om toegang te krijgen tot de computer en om opdrachten uit te voeren. Typ een gebruikers naam, zoals **gebruiker01** , **Domain01\User01** , of voer een **PSCredential** -object in dat door de `Get-Credential` cmdlet wordt gegenereerd. Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

Wanneer de para meter **Credential** niet is opgegeven, `Install-Package` gebruikt de huidige gebruiker.

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

### -Bestemming

Hiermee geeft u een pad naar een invoer object op.

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Dscresource bieden

Hiermee geeft u een of meer desired state Configuration (DSC)-resources op waarnaar wordt gezocht `Install-Package` . Gebruik de `Find-DscResource` cmdlet om DSC-resources te zoeken.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
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
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Hiermee geeft u de voor waarden voor het zoeken in de eigenschappen **name** en **Description** .

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterOnTag

Hiermee geeft u een label op waarmee resultaten worden gefilterd en worden geen resultaten opgenomen die het opgegeven label niet bevatten.

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd. Onderdrukkingen van beperkingen die voor komen dat `Install-Package` de slagen worden voltooid, met uitzonde ring van beveiliging.

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

Forceert **Package Management** de pakket provider automatisch te installeren voor het opgegeven pakket.

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

### -Headers

Hiermee geeft u de pakket headers op.

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bevat

Hiermee wordt aangegeven of `Install-Package` alle pakket typen moeten worden gevonden. De acceptabele waarden voor deze para meter zijn als volgt:

- Cmdlet
- Dscresource bieden
- Functie
- RoleCapability
- Werkstroom

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Accepteert invoer van de pijp lijn. Hiermee geeft u een pakket op met behulp van het **SoftwareIdentity** -type van het pakket.
`Find-Package` Hiermee wordt een **SoftwareIdentity** -object uitgevoerd.

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -InstallUpdate

Hiermee wordt aangegeven dat `Install-Package` updates worden geïnstalleerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

Hiermee geeft u de Maxi maal toegestane pakket versie op die u wilt installeren. Als u deze para meter niet opgeeft, `Install-Package` installeert de nieuwste versie van het pakket.

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

Hiermee geeft u de mini maal toegestane pakket versie op die u wilt installeren. Als u deze para meter niet toevoegt, `Install-Package` installeert de nieuwste versie van het pakket die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een of meer pakket namen op. Meerdere pakket namen moeten worden gescheiden door komma's.

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoPathUpdate

**NoPathUpdate** is alleen van toepassing op de `Install-Script` cmdlet. **NoPathUpdate** is een dynamische para meter die door de provider wordt toegevoegd en niet wordt ondersteund door `Install-Package` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

Hiermee geeft u de naam van de **Package Management** -provider.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

Hiermee geeft u een of meer pakket provider namen op voor het bereik van uw pakket zoekopdracht. U kunt pakket provider namen ophalen door de cmdlet uit te voeren `Get-PackageProvider` .

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Proxy

Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met een Internet bron.

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

Hiermee geeft u een gebruikers account op dat gemachtigd is om de proxy server te gebruiken die is opgegeven met de **proxy** para meter.

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

### -PublishLocation

Hiermee geeft u het pad op naar de gepubliceerde locatie van een pakket.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Hiermee geeft u de exacte toegestane versie van het pakket op dat u wilt installeren. Als u deze para meter niet toevoegt, `Install-Package` installeert de nieuwste versie van het pakket die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RoleCapability

Hiermee wordt een matrix met functie mogelijkheden opgegeven.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bereik

Hiermee geeft u het bereik op waarvoor het pakket moet worden geïnstalleerd. De acceptabele waarden voor deze para meter zijn als volgt:

- CurrentUser
- AllUsers

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptPublishLocation

Hiermee geeft u het pad op naar de gepubliceerde locatie van een script.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptSourceLocation

Hiermee geeft u de bron locatie van het script op.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipDependencies

Slaat de installatie van software-afhankelijkheden over.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
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
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipValidate

Switch waarmee de validatie van de referenties van een pakket wordt overgeslagen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Hiermee geeft u een of meer pakket bronnen op. Meerdere pakket bron namen moeten worden gescheiden door komma's.
U kunt pakket bron namen ophalen door de cmdlet uit te voeren `Get-PackageSource` .

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Tag

Hiermee geeft u een of meer teken reeksen op waarnaar moet worden gezocht in de meta gegevens van het pakket.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of beide. De acceptabele waarden voor deze para meter zijn als volgt:

- Module
- Script
- Alles

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Module, Script, All

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

### -WhatIf

Laat zien wat er zou gebeuren als de `Install-Package` cmdlet wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

### `Install-Package` accepteert invoer van de pijp lijn.

## UITVOER

### SoftwareIdentity []

## OPMERKINGEN

Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet. Dynamische para meters zijn specifiek voor een pakket provider. De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider. `Install-Package`Heeft bijvoorbeeld de para meter **PowerShellGet** met de waarde `-NoPathUpdate` , `AllowClobber` en `SkipPublisherCheck` .

## GERELATEERDE KOPPELINGEN

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Zoeken-Dscresource bieden](../PowershellGet/Find-DscResource.md)

[Get-Help](../Microsoft.PowerShell.Core/Get-Help.md)

[Get-Package](Get-Package.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Get-PackageSource](Get-PackageSource.md)

[Zoeken-pakket](Find-Package.md)

[Opslaan-pakket](Save-Package.md)

[Uninstall-pakket](Uninstall-Package.md)
