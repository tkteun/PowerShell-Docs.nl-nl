---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: 2c4f3526e1277c887a350cacda6641a889cae712
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249465"
---
# Uninstall-Package

## SAMENVATTING
Hiermee verwijdert u een of meer software pakketten.

## SYNTAXIS

### PackageByInputObject

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PackageBySearch

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### NuGet: PackageByInputObject

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### NuGet: PackageBySearch

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### PowerShellGet: PackageByInputObject

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### PowerShellGet: PackageBySearch

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## BESCHRIJVING

De `Uninstall-Package` cmdlet verwijdert een of meer software pakketten van de lokale computer. Gebruik de cmdlet om geïnstalleerde pakketten te vinden `Get-Package` .

## VOORBEELDEN

### Voor beeld 1: een pakket verwijderen

De `Uninstall-Package` cmdlet verwijdert het verwijderen van pakketten. De para meter **name** geeft het pakket op dat moet worden verwijderd. Als er meerdere versies van een pakket zijn geïnstalleerd, wordt de nieuwste versie verwijderd.

```
PS> Uninstall-Package -Name NuGet.Core
```

### Voor beeld 2: de pijp lijn gebruiken om een pakket te verwijderen

`Get-Package` zoekt een specifiek pakket en verzendt het **SoftwareIdentity** -object omlaag in de pijp lijn naar de `Uninsall-Package` cmdlet.

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

De `Get-Package` cmdlet maakt gebruik van de para meters **name** en **RequiredVersion** om een pakket op te geven.
Er wordt een **SoftwareIdentity** -object verzonden naar de pijp lijn. De `Uninstall-Package` cmdlet ontvangt het object als een **input object** en verwijdert het pakket.

Als alternatief `Uninstall-Package` kan de cmdlet een waarde opgeven voor de para meter **input object** :

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## PARAMETERS

### -AllowClobber

Onderdrukt waarschuwings berichten over conflicten met bestaande opdrachten. Overschrijft bestaande opdrachten die dezelfde naam hebben als de opdrachten die worden geïnstalleerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

Toestaan dat pakketten die zijn gemarkeerd als Prerelease, worden verwijderd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

Geeft aan dat met deze cmdlet alle versies van het pakket worden verwijderd.

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

Hiermee geeft u een teken reeks van het pad naar het invoer object.

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
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
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
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

### -Input object

Hiermee wordt een pijplijn invoer geaccepteerd waarmee het **SoftwareIdentity** -object van het pakket wordt opgegeven vanuit de `Get-Package` cmdlet. **Input object** accepteert het **SoftwareIdentity** -object als een `Get-Package` waarde of een variabele die het object bevat.

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

Hiermee wordt aangegeven dat `Uninstall-Package` updates worden verwijderd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

Hiermee geeft u de Maxi maal toegestane pakket versie op die u wilt verwijderen. Als u deze para meter niet opgeeft, wordt `Uninstall-Package` de nieuwste versie van het pakket verwijderd.

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

Hiermee geeft u de mini maal toegestane pakket versie op die u wilt verwijderen. Als u deze para meter niet toevoegt, wordt `Uninstall-Package` de nieuwste versie van het pakket verwijderd die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .

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

**NoPathUpdate** is alleen van toepassing op de `Install-Script` cmdlet. **NoPathUpdate** is een dynamische para meter die door de provider wordt toegevoegd en niet wordt ondersteund door `Uninstall-Package` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

Hiermee geeft u de **Package Management** -provider.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

Hiermee geeft u een of meer pakket provider namen op om te zoeken naar pakketten. U kunt pakket provider namen ophalen door de cmdlet uit te voeren `Get-PackageProvider` .

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

### -RequiredVersion

Hiermee geeft u de exacte toegestane versie van het pakket dat u wilt verwijderen. Als u deze para meter niet toevoegt, wordt `Uninstall-Package` de nieuwste versie van het pakket verwijderd die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .

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

### -Bereik

Hiermee geeft u het bereik op waarvoor het pakket moet worden verwijderd. De acceptabele waarden voor deze para meter zijn als volgt:

- CurrentUser
- AllUsers

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch, PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipDependencies

Hiermee wordt de verwijdering van software-afhankelijkheden overgeslagen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
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
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
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
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
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

Laat zien wat er zou gebeuren als de `Uninstall-Package` cmdlet wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

### `Uninstall-Package` Hiermee worden **SoftwareIdentity** -objecten van de pijp lijn geaccepteerd als invoer.

## UITVOER

### `Uninstall-Package` Er wordt geen uitvoer gegenereerd.

## OPMERKINGEN

Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet. Dynamische para meters zijn specifiek voor een pakket provider. De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider. `Uninstall-Package`Heeft bijvoorbeeld de para meter **PowerShellGet** met de waarde `-NoPathUpdate` , `AllowClobber` en `SkipPublisherCheck` .

## GERELATEERDE KOPPELINGEN

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Zoeken-pakket](Find-Package.md)

[Get-Package](Get-Package.md)

[Install-Package](Install-Package.md)

[Opslaan-pakket](Save-Package.md)
