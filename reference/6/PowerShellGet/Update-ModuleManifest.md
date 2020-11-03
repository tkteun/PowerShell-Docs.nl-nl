---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: f4eb5989f98517e70cc684457f0d0e3f0d12c1d4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251064"
---
# Update-ModuleManifest

## SAMENVATTING
Hiermee wordt een manifest bestand van de module bijgewerkt.

## SYNTAXIS

### Alles

```
Update-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-CompatiblePSEditions <String[]>] [-PowerShellVersion <Version>] [-ClrVersion <Version>]
 [-DotNetFrameworkVersion <Version>] [-PowerShellHostName <String>]
 [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>] [-RequiredAssemblies <String[]>]
 [-FileList <String[]>] [-ModuleList <Object[]>] [-FunctionsToExport <String[]>]
 [-AliasesToExport <String[]>] [-VariablesToExport <String[]>] [-CmdletsToExport <String[]>]
 [-DscResourcesToExport <String[]>] [-PrivateData <Hashtable>] [-Tags <String[]>]
 [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ReleaseNotes <String[]>]
 [-Prerelease <String>] [-HelpInfoUri <Uri>] [-PassThru] [-DefaultCommandPrefix <String>]
 [-ExternalModuleDependencies <String[]>] [-PackageManagementProviders <String[]>]
 [-RequireLicenseAcceptance] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Update-ModuleManifest` cmdlet wordt een module manifest `.psd1` bestand () bijgewerkt.

## VOORBEELDEN

### Voor beeld 1: een module manifest bijwerken

In dit voor beeld wordt een bestaand module manifest bestand bijgewerkt. Splatting wordt gebruikt om parameter waarden door te geven aan `Update-ModuleManifest` . Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

`$Parms` is een splat die de parameter waarden voor **pad** , **Auteur** , **Bedrijfs naam** en **copyright** opslaat. `Update-ModuleManifest` Hiermee worden de parameter waarden opgehaald uit `@Parms` en wordt het module manifest bijgewerkt **TestManifest.psd1**.

## PARAMETERS

### -AliasesToExport

Hiermee geeft u de aliassen op die de module exporteert. Joker tekens zijn toegestaan.

Gebruik deze para meter om de aliassen te beperken die door de module worden geëxporteerd. **AliasesToExport** kan aliassen uit de lijst met geëxporteerde aliassen verwijderen, maar kan geen aliassen toevoegen aan de lijst.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Author

Hiermee geeft u de auteur van de module.

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

### -ClrVersion

Hiermee geeft u de minimale versie van common language runtime (CLR) op van het Microsoft .NET Framework dat vereist is voor de module.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CmdletsToExport

Hiermee geeft u de cmdlets op die de module exporteert. Joker tekens zijn toegestaan.

Gebruik deze para meter om de cmdlets te beperken die door de module worden geëxporteerd. **CmdletsToExport** kan cmdlets uit de lijst geëxporteerde cmdlets verwijderen, maar kan geen cmdlets toevoegen aan de lijst.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -CompanyName

Hiermee geeft u het bedrijf of de leverancier op die de module heeft gemaakt.

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

### -CompatiblePSEditions

Hiermee geeft u de compatibele **PSEditions** van de module op. Zie [modules met compatibele Power shell-edities](/powershell/scripting/gallery/concepts/module-psedition-support)voor meer informatie over **PSEdition**.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vraagt u om bevestiging voordat deze wordt uitgevoerd `Update-ModuleManifest` .

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

Hiermee geeft u een copyright verklaring voor de module op.

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

### -DefaultCommandPrefix

Hiermee geeft u het standaard voorvoegsel voor de opdracht op.

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

Hiermee geeft u een beschrijving van de module.

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

### -DotNetFrameworkVersion

Hiermee geeft u de minimale versie van het Microsoft .NET Framework op dat voor de module nodig is.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DscResourcesToExport

Hiermee geeft u de resources voor desired state Configuration (DSC) op die de module exporteert. Joker tekens zijn toegestaan.

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

### -File List

Hiermee geeft u alle items die zijn opgenomen in de module.

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

### -FormatsToProcess

Hiermee geeft u de indelings bestanden ( `.ps1xml` ) op die worden uitgevoerd wanneer de module wordt geïmporteerd.

Wanneer u een module importeert, voert Power shell de `Update-FormatData` cmdlet uit met de opgegeven bestanden.
Omdat de indelings bestanden geen bereik hebben, hebben ze invloed op alle sessie statussen in de sessie.

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

### -FunctionsToExport

Hiermee geeft u de functies op die de module exporteert. Joker tekens zijn toegestaan.

Gebruik deze para meter om de functies te beperken die door de module worden geëxporteerd. **FunctionsToExport** kan functies uit de lijst met geëxporteerde aliassen verwijderen, maar kan geen functies toevoegen aan de lijst.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -GUID

Hiermee geeft u een unieke id op voor de module. De GUID kan worden gebruikt om onderscheid te maken tussen modules met dezelfde naam.

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

### -HelpInfoUri

Hiermee geeft u het Internet adres op van het **HelpInfo XML-** bestand van de module. Voer een URI (Uniform Resource Identifier) in die begint met **http** of **https**.

Het **XML-bestand HelpInfo** ondersteunt de bijwerk bare Help-functie die is geïntroduceerd in Power shell versie 3,0. Het bevat informatie over de locatie van de Download bare Help bestanden van de module en de versie nummers van de nieuwste Help-bestanden voor elke ondersteunde land instelling.

Zie [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md)voor meer informatie over de Help die kan worden bijgewerkt.
Zie voor meer informatie over het **HelpInfo XML-** bestand [ondersteunende Help](/powershell/scripting/developer/module/supporting-updatable-help).

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

Hiermee geeft u de URL op van de licentie voorwaarden voor de module.

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

### -ModuleList

Hiermee geeft u een matrix met modules op die zijn opgenomen in de module.

Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels. De hash-tabel kan ook een optionele **GUID** -sleutel hebben. U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.

Deze sleutel is ontworpen om te fungeren als een module-inventarisatie. De modules die in de waarde van deze sleutel worden vermeld, worden niet automatisch verwerkt.

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

### -ModuleVersion

Hiermee geeft u de versie van de module.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NestedModules

Hiermee geeft u script modules ( `.psm1` ) en binaire modules ( `.dll` ) op die worden geïmporteerd in de sessie status van de module. De bestanden in de **NestedModules** -sleutel worden uitgevoerd in de volg orde waarin ze worden weer gegeven in de waarde.

Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels. De hash-tabel kan ook een optionele **GUID** -sleutel hebben. U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.

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

### -PackageManagementProviders

Hiermee wordt een matrix met pakket beheer providers opgegeven.

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

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt. Standaard genereert geen `Update-ModuleManifest` uitvoer.

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

Hiermee geeft u het pad en de bestands naam van het module manifest. Voer een pad en een bestands naam in met een `.psd1` bestands extensie, zoals `$PSHOME\Modules\MyModule\MyModule.psd1` .

Als u het pad naar een bestaand bestand opgeeft, wordt `Update-ModuleManifest` het bestand vervangen zonder waarschuwing tenzij het bestand het kenmerk alleen-lezen heeft.

Het manifest moet zich in de map van de module bevinden en de naam van het manifest bestand moet hetzelfde zijn als de mapnaam, maar met een `.psd1` extensie.

U kunt geen variabelen, zoals `$PSHOME` of, gebruiken als `$HOME` antwoord op een prompt voor een **pad** parameter waarde. Als u een variabele wilt gebruiken, neemt u de para meter **Path** op in de opdracht.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PowerShellHostName

Hiermee geeft u de naam op van het Power shell-hostprogramma dat is vereist voor de module. Voer de naam van het hostprogramma in, zoals Power shell ISE host of ConsoleHost. Joker tekens zijn niet toegestaan.

Als u de naam van een hostprogramma wilt zoeken, typt u in het programma `$Host.Name` .

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

### -PowerShellHostVersion

Hiermee geeft u de minimale versie van het Power shell-hostprogramma op dat met de module werkt. Voer een versie nummer in, bijvoorbeeld 1,1.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellVersion

Hiermee geeft u de minimale versie van Power shell op die met deze module kan worden gebruikt. U kunt bijvoorbeeld 3,0, 4,0 of 5,0 opgeven als de waarde van deze para meter.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Prerelease

Hiermee wordt aangegeven dat de module Prerelease is.

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

### -PrivateData

Hiermee geeft u de gegevens op die worden door gegeven aan de module wanneer deze wordt geïmporteerd.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProcessorArchitecture

Hiermee geeft u de processor architectuur op die de module vereist.

De aanvaardbare waarden voor deze parameter zijn:

- Amd64
- Scherp
- 64
- MSIL
- Geen (onbekend of niet opgegeven)
- X86

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

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

### -RequiredAssemblies

Hiermee geeft u de assembly ( `.dll` )-bestanden op die de module vereist. Voer de namen van de assembly bestanden in.
Power shell laadt de opgegeven assembly's vóór het bijwerken van typen of indelingen, het importeren van geneste modules of het importeren van het module bestand dat is opgegeven in de waarde van de sleutel **RootModule** .

Gebruik deze para meter om alle assembly's op te geven die de module vereist, inclusief de assembly's die moeten worden geladen voor het bijwerken van de opmaak of het type van bestanden die worden vermeld in de sleutels **FormatsToProcess** of **TypesToProcess** , zelfs als deze assembly's ook worden vermeld als binaire modules in de **NestedModules** -sleutel.

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

Hiermee worden modules opgegeven die de algemene sessie status moeten hebben. Als de vereiste modules zich niet in de globale sessie status bevinden, worden ze door Power shell geïmporteerd. Als de vereiste modules niet beschikbaar zijn, `Import-Module` mislukt de opdracht.

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

### -RequireLicenseAcceptance

Hiermee geeft u op dat een acceptatie van de licentie is vereist voor de module.

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

### -RootModule

Hiermee geeft u het primaire of hoofd bestand van de module op. Voer de bestands naam van een script ( `.ps1` ), een script module ( `.psm1` ), een module manifest ( `.psd1` ), een assembly ( `.dll` ), een XML-bestand voor de cmdlet-definitie ( `.cdxml` ) of een werk stroom ( `.xaml` ) in. Wanneer de module wordt geïmporteerd, worden de leden die worden geëxporteerd uit het hoofd module bestand geïmporteerd in de sessie status van de aanroeper.

Als een module een manifest bestand heeft en er geen hoofd bestand is opgegeven in de **RootModule** -sleutel, wordt het manifest het primaire bestand voor de module. En wordt de module een manifest module (module type = manifest).

Als u leden wilt exporteren uit `.psm1` of `.dll` bestanden in een module met een manifest, moeten de namen van die bestanden worden opgegeven in de waarden van de sleutels **RootModule** of **NestedModules** in het manifest. Anders worden de leden niet geëxporteerd.

In Power Shell 2,0 is deze sleutel **ModuleToProcess** genoemd.

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

### -ScriptsToProcess

Hiermee geeft u script ( `.ps1` )-bestanden op die worden uitgevoerd in de sessie status van de aanroeper wanneer de module wordt geïmporteerd.
U kunt deze scripts gebruiken om een omgeving voor te bereiden, net zoals u een aanmeldings script zou kunnen gebruiken.

Als u scripts wilt opgeven die worden uitgevoerd in de sessie status van de module, gebruikt u de sleutel **NestedModules** .

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

### -TypesToProcess

Hiermee geeft u het type bestanden ( `.ps1xml` ) op dat wordt uitgevoerd wanneer de module wordt geïmporteerd.

Wanneer u de module importeert, voert Power shell de `Update-TypeData` cmdlet uit met de opgegeven bestanden.
Omdat type bestanden geen bereik hebben, hebben ze invloed op alle sessie statussen in de sessie.

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

### -VariablesToExport

Hiermee geeft u de variabelen op die de module exporteert. Joker tekens zijn toegestaan.

Gebruik deze para meter om de variabelen te beperken die door de module worden geëxporteerd. **VariablesToExport** kan variabelen uit de lijst geëxporteerde variabelen verwijderen, maar kan geen variabelen toevoegen aan de lijst.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -WhatIf

Hier wordt weer gegeven wat er gebeurt als er `Update-ModuleManifest` wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

## GERELATEERDE KOPPELINGEN
