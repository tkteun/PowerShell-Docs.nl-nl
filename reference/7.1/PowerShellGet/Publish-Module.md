---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: d7b75b9aec6cba352d72176de59af82155d1fa17
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250166"
---
# Publish-Module

## SAMENVATTING
Hiermee publiceert u een opgegeven module van de lokale computer naar een online galerie.

## SYNTAXIS

### ModuleNameParameterSet (standaard)

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModulePathParameterSet

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Publish-Module` cmdlet publiceert een module naar een online NuGet-galerie met behulp van een API-sleutel, opgeslagen als onderdeel van een gebruikers profiel in de galerie. U kunt opgeven welke module moet worden gepubliceerd door de naam van de module of door het pad naar de map met de module.

Wanneer u een module op naam opgeeft, wordt `Publish-Module` de eerste module gepubliceerd die zou worden gevonden door uit te voeren `Get-Module -ListAvailable <Name>` . Als u een minimum versie van een module opgeeft om te publiceren, `Publish-Module` publiceert de eerste module met een versie die groter is dan of gelijk is aan de minimum versie die u hebt opgegeven.

Voor het publiceren van een module zijn meta gegevens vereist die worden weer gegeven op de galerie pagina voor de module. De vereiste meta gegevens bevatten de module naam, versie, beschrijving en auteur. Hoewel de meeste meta gegevens worden opgehaald uit het module manifest, moeten sommige meta gegevens worden opgegeven in `Publish-Module` para meters, zoals **tag** , **ReleaseNote** , **IconUri** , **ProjectUri** en **LicenseUri** , omdat deze para meters overeenkomen met velden in een op NuGet gebaseerde galerie.

## VOORBEELDEN

### Voor beeld 1: een module publiceren

In dit voor beeld wordt MyDscModule in de online galerie gepubliceerd met behulp van de API-sleutel om het online galerie account van de module eigenaar aan te geven. Als MyDscModule geen geldige manifest module is die een naam, versie, beschrijving en auteur opgeeft, treedt er een fout op.

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### Voor beeld 2: een module met de meta gegevens van de galerie publiceren

In dit voor beeld wordt MyDscModule in de online galerie gepubliceerd met behulp van de API-sleutel om het Galerie account van de module eigenaar aan te geven. De aanvullende meta gegevens worden weer gegeven op de webpagina van de module in de galerie. De eigenaar voegt twee zoek tags voor de module toe, met betrekking tot Active Directory. Er wordt een korte release opmerking toegevoegd. Als MyDscModule geen geldige manifest module is die een naam, versie, beschrijving en auteur opgeeft, treedt er een fout op.

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## PARAMETERS

### -AllowPrerelease

Hiermee kunnen modules die zijn gemarkeerd als Prerelease, worden gepubliceerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vraagt u om bevestiging voordat de wordt uitgevoerd `Publish-Module` .

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

Hiermee geeft u een gebruikers account op dat beschikt over rechten voor het publiceren van een module voor een opgegeven pakket provider of bron.

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

### -Uitsluiten

Hiermee worden bestanden gedefinieerd die moeten worden uitgesloten van de gepubliceerde module.

```yaml
Type: System.String[]
Parameter Sets: ModuleNameParameterSet
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
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatVersion

Accepteert alleen geldige waarden die zijn opgegeven met het kenmerk **Validate** .

Zie [Validate-kenmerk declaratie](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) en [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute)voor meer informatie.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:
Accepted values: 2.0

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IconUri

Hiermee geeft u de URL op van een pictogram voor de module. Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor de module.

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

### -LicenseUri

Hiermee geeft u de URL op van de licentie voorwaarden voor de module die u wilt publiceren.

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

### -Name

Hiermee geeft u de naam van de module die u wilt publiceren. `Publish-Module` zoekt naar de opgegeven module naam in `$Env:PSModulePath` .

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NuGetApiKey

Hiermee geeft u de API-sleutel op die u wilt gebruiken voor het publiceren van een module naar de online galerie. De API-sleutel maakt deel uit van uw profiel in de online galerie en is te vinden op de pagina met uw gebruikers account in de galerie. De API-sleutel is NuGet-specifieke functionaliteit.

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

### -Path

Hiermee geeft u het pad op naar de module die u wilt publiceren. Deze para meter accepteert het pad naar de map waarin de module zich bevindt.

```yaml
Type: System.String
Parameter Sets: ModulePathParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProjectUri

Hiermee geeft u de URL van een webpagina over dit project op.

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

### -ReleaseNotes

Hiermee geeft u een teken reeks met release opmerkingen of opmerkingen die u beschikbaar wilt maken voor gebruikers van deze versie van de module.

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

### -Opslag plaats

Hiermee geeft u de beschrijvende naam op van een opslag plaats die is geregistreerd door te worden uitgevoerd `Register-PSRepository` . De opslag plaats moet een **PublishLocation** hebben. Dit is een geldige NUGET-URI.
De **PublishLocation** kan worden ingesteld door te worden uitgevoerd `Set-PSRepository` .

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

### -RequiredVersion

Hiermee geeft u de exacte versie van één module op die moet worden gepubliceerd.

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipAutomaticTags

Hiermee verwijdert u opdrachten en resources uit de tags die u wilt opnemen. Hiermee slaat u automatisch tags toe aan een module.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tags

Hiermee voegt u een of meer tags toe aan de module die u publiceert. Voor beelden van tags zijn DesiredStateConfiguration, DSC, DSCResourceKit of PSModule. Scheid meerdere labels met komma's.

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

### -WhatIf

Laat zien wat er zou gebeuren als de `Publish-Module` uitvoeringen wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

### System. String

### System. Management. Automation. PSCredential

## UITVOER

### System. object

## OPMERKINGEN

`Publish-Module` wordt uitgevoerd op Power Shell 3,0 of latere versies van Power shell, op Windows 7 of Windows 2008 R2 en latere versies van Windows.

Voor het publiceren van een module zijn meta gegevens vereist die worden weer gegeven op de galerie pagina voor de module. De vereiste meta gegevens bevatten de module naam, versie, beschrijving en auteur. De meeste meta gegevens worden opgehaald uit het module manifest, maar sommige meta gegevens kunnen worden opgegeven in `Publish-Module` para meters, zoals **tag** , **ReleaseNote** , **IconUri** , **ProjectUri** en **LicenseUri**. Zie [pakket manifest waarden die van invloed zijn op de PowerShell Gallery-gebruikers interface](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Find-Module](Find-Module.md)

[Installatie-module](Install-Module.md)

[REGI ster-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Uninstall-module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

