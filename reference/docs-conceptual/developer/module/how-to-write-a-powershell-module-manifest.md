---
title: Een Power shell-module manifest schrijven | Microsoft Docs
ms.custom: ''
ms.date: 10/16/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 992148c9e39b6edbfa26907de03a5ae57691d831
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84148393"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Een Power shell-module manifest schrijven

Nadat u de Power shell-module hebt geschreven, kunt u een optioneel module manifest toevoegen dat informatie over de module bevat. U kunt bijvoorbeeld de auteur beschrijven, bestanden opgeven in de module (zoals geneste modules), scripts uitvoeren voor het aanpassen van de omgeving van de gebruiker, het laden van het type en het format teren van de systeem vereisten en het beperken van de leden die de module exporteert.

## <a name="creating-a-module-manifest"></a>Een module manifest maken

Een **module manifest** is een Power shell-gegevens bestand ( `.psd1` ) dat de inhoud van een module beschrijft en bepaalt hoe een module wordt verwerkt. Het manifest bestand is een tekst bestand dat een hash-tabel met sleutels en waarden bevat. U koppelt een manifest bestand aan een module door de naam van het manifest te wijzigen in de module en het manifest op te slaan in de hoofdmap van de module.

Voor eenvoudige modules die slechts één `.psm1` of binaire assembly bevatten, is een module manifest optioneel. Het is echter raadzaam een module manifest te gebruiken wanneer dat mogelijk is, omdat deze handig zijn om u te helpen bij het organiseren van uw code en het onderhouden van versie gegevens. En een module manifest is vereist voor het exporteren van een assembly die is geïnstalleerd in de [globale assembly-cache](/dotnet/framework/app-domains/gac). Er is ook een module manifest vereist voor modules die ondersteuning bieden voor de Help-functie die kan worden bijgewerkt. Bij te werken Help wordt de **HelpInfoUri** -sleutel in het module manifest gebruikt om het bestand met Help-informatie (HelpInfo XML) te vinden dat de locatie van de bijgewerkte Help-bestanden voor de module bevat. Zie [ondersteunende Help](./supporting-updatable-help.md)voor meer informatie over de Help die kan worden bijgewerkt.

### <a name="to-create-and-use-a-module-manifest"></a>Een module manifest maken en gebruiken

1. De best practice een module manifest te maken, is met behulp van de cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) . U kunt para meters gebruiken om een of meer van de standaard sleutels en-waarden van het manifest op te geven. De enige vereiste is de naam van het bestand. `New-ModuleManifest`Hiermee maakt u een module manifest met de opgegeven waarden, inclusief de overige sleutels en hun standaard waarden. Als u meerdere modules wilt maken, gebruikt u voor `New-ModuleManifest` het maken van een module manifest sjabloon die voor uw verschillende modules kan worden gewijzigd. Zie het manifest voor beeld [modules](#sample-module-manifest)voor een voor beeld van een standaard module manifest.

   `New-ModuleManifest -Path C:\myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   U kunt ook de hash-tabel van het module manifest hand matig maken met behulp van de minimale vereiste gegevens, het **ModuleVersion**. U slaat het bestand op met dezelfde naam als uw module en gebruikt de `.psd1` bestands extensie. U kunt het bestand vervolgens bewerken en de juiste sleutels en waarden toevoegen.

1. Voeg eventuele extra elementen in het manifest bestand toe.

   Als u het manifest bestand wilt bewerken, gebruikt u een wille keurige tekst editor. Het manifest bestand is echter een script bestand dat code bevat. u kunt dit dus bewerken in een script-of ontwikkel omgeving, zoals Visual Studio code. Alle elementen van een manifest bestand zijn optioneel, met uitzonde ring van het **ModuleVersion** -nummer.

   Zie de tabel [manifest elementen van module](#module-manifest-elements) voor beschrijvingen van de sleutels en waarden die u kunt toevoegen in een module manifest. Zie de parameter beschrijvingen in de cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) voor meer informatie.

1. U hebt de mogelijkheid extra code toe te voegen aan het module manifest om eventuele scenario's op te lossen die mogelijk niet worden gedekt door de basis module manifest elementen.

   Uit veiligheids overwegingen voert Power shell alleen een kleine subset van de beschik bare bewerkingen in een module manifest bestand uit. Over het algemeen kunt u de `if` Opera tors instructie, reken kundige en vergelijkings operatoren en de basis-Power shell-gegevens typen gebruiken.

1. Nadat u het module manifest hebt gemaakt, kunt u dit testen om te bevestigen dat alle in het manifest beschreven paden correct zijn. Gebruik [test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)om het module manifest te testen.

   `Test-ModuleManifest myModuleName.psd1`

1. Zorg ervoor dat het module manifest zich bevindt in het hoogste niveau van de map die uw module bevat.

   Wanneer u uw module op een systeem kopieert en importeert, gebruikt Power shell het module manifest om uw module te importeren.

1. Desgewenst kunt u uw module manifest rechtstreeks testen met een aanroep van [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) by dot, het manifest zelf.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Manifest elementen van module

In de volgende tabel worden de elementen beschreven die u kunt toevoegen in een module manifest.

|Element|Standaard|Beschrijving|
|-------------|-------------|-----------------|
|**RootModule**<br /> Voert`String`|`<empty string>`|Script module of binair module bestand dat is gekoppeld aan dit manifest. In eerdere versies van Power shell heet dit element de **ModuleToProcess**.<br /> Mogelijke typen voor de hoofd module kunnen leeg zijn, waardoor er een **manifest** module, de naam van een script module ( `.psm1` ) of de naam van een binaire module ( `.exe` of) wordt gemaakt `.dll` . Als u de naam van een module manifest ( `.psd1` ) of een script bestand ( `.ps1` ) in dit element plaatst, treedt er een fout op. <br /> Voorbeeld: `RootModule = 'ScriptModule.psm1'`|
|**ModuleVersion**<br /> Voert`Version`|`'0.0.1'`|Het versie nummer van deze module. Als er geen waarde is opgegeven, `New-ModuleManifest` gebruikt de standaard. De teken reeks moet zo kunnen worden geconverteerd naar het type `Version` `#.#.#.#.#` . `Import-Module`laadt de eerste module die wordt gevonden op de **$PSModulePath** die overeenkomt met de naam en heeft ten minste als hoge a **ModuleVersion**, als de para meter **MinimumVersion** . Als u een specifieke versie wilt importeren, gebruikt u de `Import-Module` para meter **RequiredVersion** van de cmdlet.<br /> Voorbeeld: `ModuleVersion = '1.0'`|
|**GPT**<br /> Voert`GUID`|`'<GUID>'`|ID die wordt gebruikt om deze module uniek te identificeren. Als er geen waarde is opgegeven, `New-ModuleManifest` genereert automatisch de waarde. U kunt op dit moment geen module importeren op **GUID**. <br /> Voorbeeld: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|**Auteur**<br /> Voert`String`|`'<Current user>'`|Auteur van deze module. Als er geen waarde is opgegeven, `New-ModuleManifest` wordt de huidige gebruiker gebruikt. <br /> Voorbeeld: `Author = 'AuthorNameHere'`|
|**CompanyName**<br /> Voert`String`|`'Unknown'`|Bedrijf of leverancier van deze module. Als er geen waarde is opgegeven, `New-ModuleManifest` gebruikt de standaard.<br /> Voorbeeld: `CompanyName = 'Fabrikam'`|
|**Gegevens**<br /> Voert`String`|`'(c) <Author>. All rights reserved.'`| Copyright verklaring voor deze module. Als er geen waarde is opgegeven, `New-ModuleManifest` wordt de standaard instelling gebruikt voor de huidige gebruiker als `<Author>` . Als u een auteur wilt opgeven, gebruikt u de para meter **Auteur** . <br /> Voorbeeld: `Copyright = '2019 AuthorName. All rights reserved.'`|
|**Beschrijving**<br /> Voert`String`|`<empty string>`|Beschrijving van de functionaliteit van deze module.<br /> Voorbeeld: `Description = 'This is the module's description.'`|
|**PowerShellVersion**<br /> Voert`Version`|`<empty string>`|Minimale versie van de Power shell-engine die vereist is voor deze module. Geldige waarden zijn 1,0, 2,0, 3,0, 4,0, 5,0, 5,1, 6 en 7.<br /> Voorbeeld: `PowerShellVersion = '5.0'`|
|**PowerShellHostName**<br /> Voert`String`|`<empty string>`|De naam van de Power shell-host die is vereist voor deze module. Deze naam wordt verschaft door Power shell. Als u de naam van een hostprogramma wilt zoeken, typt u het volgende in het programma: `$host.name` .<br /> Voorbeeld: `PowerShellHostName = 'ConsoleHost'`|
|**PowerShellHostVersion**<br /> Voert`Version`|`<empty string>`|De minimale versie van de Power shell-host die is vereist voor deze module.<br /> Voorbeeld: `PowerShellHostVersion = '2.0'`|
|**DotNetFrameworkVersion**<br /> Voert`Version`|`<empty string>`|Mini maal vereiste versie van Microsoft .NET Framework dat is vereist voor deze module. Deze vereiste is alleen geldig voor de Power shell Desktop Edition, zoals Power shell 5,1.<br /> Voorbeeld: `DotNetFrameworkVersion = '3.5'`|
|**CLRVersion**<br /> Voert`Version`|`<empty string>`|De minimale versie van de Common Language Runtime (CLR) die vereist is voor deze module. Deze vereiste is alleen geldig voor de Power shell Desktop Edition, zoals Power shell 5,1.<br /> Voorbeeld: `CLRVersion = '3.5'`|
|**ProcessorArchitecture**<br /> Voert`ProcessorArchitecture`|`<empty string>`|De processor architectuur (geen, x86, amd64) die is vereist voor deze module. Geldige waarden zijn x86, AMD64, arm, IA64, MSIL en geen (onbekend of niet opgegeven).<br /> Voorbeeld: `ProcessorArchitecture = 'x86'`|
|**RequiredModules**<br /> Voert`Object[]`|`@()`|Modules die moeten worden geïmporteerd in de globale omgeving voordat deze module wordt geïmporteerd. Hiermee worden alle modules geladen, tenzij deze al zijn geladen. Sommige modules kunnen bijvoorbeeld al zijn geladen door een andere module. Het is mogelijk om een specifieke versie op te geven die u wilt laden `RequiredVersion` in plaats van `ModuleVersion` . Wanneer `ModuleVersion` wordt gebruikt, wordt de nieuwste versie geladen die beschikbaar is met een minimum van de opgegeven versie. U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.<br /> Voorbeeld: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; ModuleVersion="2.0"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /> Voorbeeld: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; RequiredVersion="1.5"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|**RequiredAssemblies**<br /> Voert`String[]`|`@()`|Assembly's die moeten worden geladen voordat deze module wordt geïmporteerd. Hiermee geeft u de assembly ( `.dll` ) bestands namen op die de module vereist.<br /> Power shell laadt de opgegeven assembly's vóór het bijwerken van typen of indelingen, het importeren van geneste modules of het importeren van het module bestand dat is opgegeven in de waarde van de sleutel RootModule. Gebruik deze para meter om een lijst weer te geven van alle assembly's die de module vereist.<br /> Voorbeeld: `RequiredAssemblies = @("assembly1.dll", "assembly2.dll", "assembly3.dll")`|
|**ScriptsToProcess**<br /> Voert`String[]`|`@()`|Script ( `.ps1` )-bestanden die worden uitgevoerd in de sessie status van de aanroeper wanneer de module wordt geïmporteerd. Dit kan de algemene sessie status zijn of, voor geneste modules, de sessie status van een andere module. U kunt deze scripts gebruiken om een omgeving voor te bereiden net zoals u een aanmeldings script gebruikt.<br /> Deze scripts worden uitgevoerd voordat een van de modules die worden vermeld in het manifest, worden geladen. <br /> Voorbeeld: `ScriptsToProcess = @("script1.ps1", "script2.ps1", "script3.ps1")`|
|**TypesToProcess**<br /> Voert`String[]`|`@()`|Type bestanden ( `.ps1xml` ) die moeten worden geladen bij het importeren van deze module. <br /> Voorbeeld: `TypesToProcess = @("type1.ps1xml", "type2.ps1xml", "type3.ps1xml")`|
|**FormatsToProcess**<br /> Voert`String[]`|`@()`|Format-bestanden ( `.ps1xml` ) die moeten worden geladen bij het importeren van deze module. <br /> Voorbeeld: `FormatsToProcess = @("format1.ps1xml", "format2.ps1xml", "format3.ps1xml")`|
|**NestedModules**<br /> Voert`Object[]`|`@()`|Modules die moeten worden geïmporteerd als geneste modules van de module die is opgegeven in **RootModule** (alias:**ModuleToProcess**).<br /> Het toevoegen van een module naam aan dit element is vergelijkbaar met het aanroepen `Import-Module` vanuit vanuit uw script of assembly-code. Het belangrijkste verschil met behulp van een manifest bestand is dat het eenvoudiger is om te zien wat u wilt laden. En als een module niet kan worden geladen, hebt u de daad werkelijke module nog niet geladen.<br /> Naast andere modules kunt u ook script ( `.ps1` )-bestanden hier laden. Deze bestanden worden uitgevoerd in de context van de hoofd module. Dit komt overeen met puntjes het script in uw hoofd module. <br /> Voorbeeld: `NestedModules = @("script.ps1", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FunctionsToExport**<br /> Voert`String[]`|`@()`|Hiermee geeft u de functies voor het exporteren van deze module, voor de beste prestaties, het gebruik van geen joker tekens en het verwijderen van de vermelding niet. gebruik een lege matrix als er geen functies zijn om te exporteren. Standaard worden er geen functies geëxporteerd. U kunt deze sleutel gebruiken om de functies weer te geven die door de module worden geëxporteerd.<br /> De module exporteert de functies naar de sessie status van de oproepende functie. De sessie status van de oproepende functie kan de algemene sessie status zijn of, voor geneste modules, de sessie status van een andere module. Bij het koppelen van geneste modules worden alle functies die worden geëxporteerd door een geneste module, geëxporteerd naar de algemene sessie status, tenzij een module in de keten de functie beperkt met behulp van de **FunctionsToExport** -sleutel.<br /> Als het manifest aliassen voor de functies exporteert, kan met deze sleutel functies worden verwijderd waarvan de aliassen worden weer gegeven in de **AliasesToExport** -sleutel, maar deze sleutel kan geen functie aliassen toevoegen aan de lijst. <br /> Voorbeeld: `FunctionsToExport = @("function1", "function2", "function3")`|
|**CmdletsToExport**<br /> Voert`String[]`|`@()`|Hiermee geeft u de cmdlets op die vanuit deze module moeten worden geëxporteerd. voor de beste prestaties moet u geen joker tekens gebruiken en de vermelding niet verwijderen. gebruik een lege matrix als er geen cmdlets zijn om te exporteren. Standaard worden er geen cmdlets geëxporteerd. U kunt deze sleutel gebruiken om de cmdlets weer te geven die door de module worden geëxporteerd.<br /> De sessie status van de oproepende functie kan de algemene sessie status zijn of, voor geneste modules, de sessie status van een andere module. Wanneer u geneste modules koppelt, worden alle cmdlets die worden geëxporteerd door een geneste module geëxporteerd naar de algemene sessie status, tenzij een module in de keten de cmdlet beperkt met behulp van de **CmdletsToExport** -sleutel.<br /> Als het manifest aliassen voor de cmdlets exporteert, kan met deze sleutel cmdlets worden verwijderd waarvan de aliassen worden vermeld in de **AliasesToExport** -sleutel, maar deze sleutel kan geen cmdlet-aliassen toevoegen aan de lijst. <br /> Voorbeeld: `CmdletsToExport = @("Get-MyCmdlet", "Set-MyCmdlet", "Test-MyCmdlet")`|
|**VariablesToExport**<br /> Voert`String[]`|`'*'`|Hiermee geeft u de variabelen op die de module exporteert naar de sessie status van de aanroeper. Joker tekens zijn toegestaan. Standaard worden alle variabelen ( `'*'` ) geëxporteerd. U kunt deze sleutel gebruiken om de variabelen te beperken die door de module worden geëxporteerd.<br /> De sessie status van de oproepende functie kan de algemene sessie status zijn of, voor geneste modules, de sessie status van een andere module. Wanneer u geneste modules koppelt, worden alle variabelen die worden geëxporteerd door een geneste module, geëxporteerd naar de globale sessie status, tenzij een module in de keten de variabele beperkt door gebruik te maken van de **VariablesToExport** -sleutel.<br /> Als het manifest ook aliassen voor de variabelen exporteert, kan deze sleutel variabelen verwijderen waarvan de aliassen worden weer gegeven in de **AliasesToExport** -sleutel, maar met deze sleutel kunnen geen variabele aliassen aan de lijst worden toegevoegd. <br /> Voorbeeld: `VariablesToExport = @('$MyVariable1', '$MyVariable2', '$MyVariable3')`|
|**AliasesToExport**<br /> Voert`String[]`|`@()`|Hiermee geeft u de aliassen op die vanuit deze module moeten worden geëxporteerd. voor de beste prestaties moet u geen joker tekens gebruiken en de vermelding niet verwijderen. gebruik een lege matrix als er geen aliassen zijn om te exporteren. Standaard worden er geen aliassen geëxporteerd. U kunt deze sleutel gebruiken om de aliassen weer te geven die door de module worden geëxporteerd.<br /> De module exporteert de aliassen naar de sessie status van de aanroeper. De sessie status van de oproepende functie kan de algemene sessie status zijn of, voor geneste modules, de sessie status van een andere module. Wanneer u geneste modules koppelt, worden alle aliassen die worden geëxporteerd door een geneste module uiteindelijk geëxporteerd naar de status van de globale sessie, tenzij een module in de keten de alias beperkt met behulp van de **AliasesToExport** -sleutel. <br /> Voorbeeld: `AliasesToExport = @("MyAlias1", "MyAlias2", "MyAlias3")`|
|**DscResourcesToExport**<br /> Voert`String[]`|`@()`|Hiermee geeft u DSC-resources op die vanuit deze module moeten worden geëxporteerd. Joker tekens zijn toegestaan. <br /> Voorbeeld: `DscResourcesToExport = @("DscResource1", "DscResource2", "DscResource3")`|
|**ModuleList**<br /> Voert`Object[]`|`@()`|Hiermee geeft u alle modules op die zijn verpakt met deze module. Deze modules kunnen worden ingevoerd op naam, met behulp van een door komma's gescheiden teken reeks of als een hash-tabel met de sleutels **module** en **GUID** . De hash-tabel kan ook een optionele **ModuleVersion** -sleutel hebben. De **ModuleList** -sleutel is ontworpen om te fungeren als een module-inventarisatie. Deze modules worden niet automatisch verwerkt. <br /> Voorbeeld: `ModuleList = @("SampleModule", "MyModule", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**File List**<br /> Voert`String[]`|`@()`|Een lijst met alle bestanden die bij deze module zijn verpakt. Net als bij **ModuleList**is **File List** een inventarisatie lijst en wordt niet anderszins verwerkt. <br /> Voorbeeld: `FileList = @("File1", "File2", "File3")`|
|**PrivateData**<br /> Voert`Object`|`@{...}`|Hiermee geeft u alle persoonlijke gegevens op die moeten worden door gegeven aan de hoofd module die is opgegeven door de **RootModule** -sleutel (alias: **ModuleToProcess**). **PrivateData** is een hash-tabel die verschillende elementen omvat **: Tags**, **LicenseUri**, **ProjectURI**, **IconUri**, **ReleaseNotes**, **Prerelease**, **RequireLicenseAcceptance**en **ExternalModuleDependencies**. |
|**Tags** <br /> Voert`String[]` |`@()`| Tags helpen bij het detecteren van modules in online galerieën. <br /> Voorbeeld: `Tags = "PackageManagement", "PowerShell", "Manifest"`|
|**LicenseUri**<br /> Voert`Uri` |`<empty string>`| Een URL naar de licentie voor deze module. <br /> Voorbeeld: `LicenseUri = 'https://www.contoso.com/license'`|
|**ProjectUri**<br /> Voert`Uri` |`<empty string>`| Een URL naar de hoofd website voor dit project. <br /> Voorbeeld: `ProjectUri = 'https://www.contoso.com/project'`|
|**IconUri**<br /> Voert`Uri` |`<empty string>`| Een URL naar een pictogram dat deze module vertegenwoordigt. <br /> Voorbeeld: `IconUri = 'https://www.contoso.com/icons/icon.png'`|
|**ReleaseNotes**<br /> Voert`String` |`<empty string>`| Specificeert de release opmerkingen van de module. <br /> Voorbeeld: `ReleaseNotes = 'The release notes provide information about the module.`|
|**PreRelease**<br /> Voert`String` |`<empty string>`| Deze para meter is toegevoegd in PowerShellGet 1.6.6. Een **Prerelease** -teken reeks waarmee de module wordt geïdentificeerd als een voorlopige versie in online galerieën. <br /> Voorbeeld: `PreRelease = 'This module is a prerelease version.`|
|**RequireLicenseAcceptance**<br /> Voert`Boolean`|`$true`| Deze para meter is toegevoegd in PowerShellGet 1,5. Markering om aan te geven of voor de module expliciete gebruikers acceptatie is vereist voor installeren, bijwerken of opslaan. <br /> Voorbeeld: `RequireLicenseAcceptance = $false`|
|**ExternalModuleDependencies**<br /> Voert`String[]` |`@()`| Deze para meter is toegevoegd in PowerShellGet v2. Een lijst met externe modules waarvan deze module afhankelijk is. <br /> Voorbeeld: `ExternalModuleDependencies =  @("ExtModule1", "ExtModule2", "ExtModule3")`|
|**HelpInfoURI**<br /> Voert`String`|`<empty string>`|HelpInfo-URI van deze module. <br /> Voorbeeld: `HelpInfoURI = 'https://www.contoso.com/help'`|
|**DefaultCommandPrefix**<br /> Voert`String`|`<empty string>`|Standaard voorvoegsel voor opdrachten die vanuit deze module worden geëxporteerd. Vervang het standaard voorvoegsel door `Import-Module -Prefix` . <br /> Voorbeeld: `DefaultCommandPrefix = 'My'`|

## <a name="sample-module-manifest"></a>Voor beeld-module manifest

Het volgende voor beeld-module manifest is gemaakt met `New-ModuleManifest` in Power shell 7 en bevat de standaard sleutels en-waarden.

```powershell
#
# Module manifest for module 'SampleModuleManifest'
#
# Generated by: User01
#
# Generated on: 10/15/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b632e90c-df3d-4340-9f6c-3b832646bf87'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        RequireLicenseAcceptance = $true

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

## <a name="see-also"></a>Zie ook

[about_Comparison_Operators](/powershell/module/microsoft.powershell.core/about/about_comparison_operators)

[about_If](/powershell/module/microsoft.powershell.core/about/about_if)

[Global assembly-cache](/dotnet/framework/app-domains/gac)

[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest)

[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest)

[Update-ModuleManifest](/powershell/module/powershellget/update-modulemanifest)

[Een Windows PowerShell-module schrijven](./writing-a-windows-powershell-module.md)
