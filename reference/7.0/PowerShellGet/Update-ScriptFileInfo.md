---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-scriptfileinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ScriptFileInfo
ms.openlocfilehash: 1fa19b82d0467bdd363af70919efe9a51febbdcb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249791"
---
# Update-ScriptFileInfo

## SAMENVATTING
Hiermee wordt informatie over een script bijgewerkt.

## SYNTAXIS

### PathParameterSet (standaard)

```
Update-ScriptFileInfo [-Path] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### LiteralPathParameterSet

```
Update-ScriptFileInfo [-LiteralPath] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet worden de `Update-ScriptFileInfo` eigenschaps waarden van een script bijgewerkt. Bijvoorbeeld: de waarden voor versie, auteur of beschrijving.

## VOORBEELDEN

### Voor beeld 1: de versie van een script bestand bijwerken

In dit voor beeld wordt een bestaand script bestand bijgewerkt met nieuwe eigenschaps waarden.

Splatting wordt gebruikt om para meters door te geven aan de `Update-ScriptFileInfo` cmdlet. Zie [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)voor meer informatie.

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "2.0"
  Author = "bob@contoso.com"
  CompanyName = "Contoso"
  Description = "This is the updated description"
  }
Update-ScriptFileInfo @Parms -PassThru
```

```Output
<#PSScriptInfo

.VERSION 2.0

.GUID 4609f00c-e850-4d3f-9c69-3741e56e4133

.AUTHOR bob@contoso.com

.COMPANYNAME Contoso

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

.PRIVATEDATA

#>

<#

.DESCRIPTION
This is the updated description

#>
Param()
```

`$Parms` Hiermee slaat u de parameter waarden voor **pad** , **versie** , **Auteur** , **Bedrijfs naam** en **Beschrijving** op. `Update-ScriptFileInfo` Hiermee worden de parameter waarden opgehaald uit `@Parms` en wordt het script bijgewerkt. Met de para meter **PassThru** wordt de inhoud van het script weer gegeven in de Power shell-console.

## PARAMETERS

### -Author

Hiermee geeft u de auteur van het script.

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

### -CompanyName

Hiermee geeft u het bedrijf of de leverancier op die het script heeft gemaakt.

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

### -Confirm

Vraagt u om bevestiging voordat deze wordt uitgevoerd `Update-ScriptFileInfo` .

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

### -Copyright

Hiermee geeft u een copyright verklaring voor het script op.

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

### -Beschrijving

Hiermee geeft u een beschrijving op voor het script.

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

### -ExternalModuleDependencies

Hiermee geeft u een matrix met externe module-afhankelijkheden op.

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

### -ExternalScriptDependencies

Hiermee geeft u een matrix met externe script afhankelijkheden.

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

### -Force

Er wordt geforceerd `Update-ScriptFileInfo` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

### -GUID

Hiermee geeft u een unieke ID voor een script op.

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IconUri

Hiermee geeft u de URL van een pictogram voor het script. Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor het script.

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

Hiermee geeft u de URL van de licentie voorwaarden.

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

### -LiteralPath

Hiermee geeft u een pad naar een of meer locaties. De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt ingevoerd. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt. Standaard genereert geen `Update-ScriptFileInfo` uitvoer.

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

### -Path

Hiermee geeft u de locatie van het script bestand. Joker tekens zijn toegestaan.

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PrivateData

Hiermee geeft u de persoonlijke gegevens voor het script.

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

Hiermee geeft u een teken reeks matrix met release opmerkingen of opmerkingen die u beschikbaar wilt stellen voor deze versie van het script.

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

### -RequiredModules

Hiermee worden modules opgegeven die de algemene sessie status moeten hebben. Als de vereiste modules zich niet in de globale sessie status bevinden, worden ze door Power shell geïmporteerd.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredScripts

Hiermee geeft u een matrix met vereiste scripts op.

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

### -Tags

Hiermee geeft u een matrix met tags op.

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

### -Versie

Hiermee geeft u de versie van het script op.

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

### -WhatIf

Hier wordt weer gegeven wat er gebeurt als er `Update-ScriptFileInfo` wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

## UITVOER

### System. object

## OPMERKINGEN

Gebruik de `Test-ScriptFileInfo` cmdlet om de meta gegevens van een script te valideren. Scripts moeten waarden bevatten voor versie, GUID, beschrijving en auteur.

## GERELATEERDE KOPPELINGEN

[New-ScriptFileInfo](New-ScriptFileInfo.md)

[Test-ScriptFileInfo](Test-ScriptFileInfo.md)
