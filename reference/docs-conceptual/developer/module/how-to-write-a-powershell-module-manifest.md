---
title: Een Power shell-module manifest schrijven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 1265855b82b0bfaa7b2717c8eb348b822c19f561
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357391"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Een manifest voor een PowerShell-module schrijven

Wanneer u uw Windows Power shell-module hebt geschreven, kunt u eventueel een module manifest toevoegen. Een module manifest is een Power shell-script bestand dat u kunt gebruiken voor het toevoegen van informatie over de module. U kunt bijvoorbeeld de auteur beschrijven, bestanden opgeven in de module (zoals geneste modules), scripts uitvoeren voor het aanpassen van de omgeving van de gebruiker, het laden van het type en het format teren van de systeem vereisten en het beperken van de leden die de module exporteert.

## <a name="creating-a-module-manifest"></a>Een module manifest maken

Een *module manifest* is een Windows Power shell-gegevens bestand (. psd1) dat de inhoud van een module beschrijft en bepaalt hoe een module wordt verwerkt. Het manifest bestand zelf is een tekst bestand dat een hash-tabel met sleutels en waarden bevat. U koppelt een manifest bestand aan een module door deze dezelfde naam te geven als de module en deze te plaatsen in de hoofdmap van de module directory.

Voor eenvoudige modules die slechts één. psm1-of binaire assembly bevatten, is een module manifest optioneel. Het is echter raadzaam een module manifest te gebruiken wanneer dat mogelijk is, omdat deze handig zijn om u te helpen bij het organiseren van uw code en het onderhouden van versie-informatie. Daarnaast is een module manifest vereist voor het exporteren van een assembly die is geïnstalleerd in de Global Assembly Cache. Er is ook een module manifest vereist voor modules die ondersteuning bieden voor de Help-functie die kan worden bijgewerkt. Dat wil zeggen dat bij bij te werken Help de sleutel **HelpInfoUri** in het module manifest wordt gebruikt om het bestand met Help-informatie (HelpInfo XML) te vinden dat de locatie van de bijgewerkte Help-bestanden voor de module bevat. Zie [ondersteunende Help](./supporting-updatable-help.md)voor meer informatie over de Help die kan worden bijgewerkt.

### <a name="to-create-and-use-a-module-manifest"></a>Een module manifest maken en gebruiken

1. U hebt verschillende opties om een module manifest te maken:

   1. Maak de hash-tabel rechtstreeks met de minimale vereiste gegevens en sla deze op in een. psd1-bestand met dezelfde naam als uw module. Zodra u dit hebt gedaan, kunt u het bestand openen en de juiste waarden hand matig toevoegen.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. U kunt ook de cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) aanroepen met een of meer van de standaard waarden die zijn door gegeven als para meters. (Houd er rekening mee dat alleen de naam van het bestand vereist is voor het genereren van een manifest.) Hiermee wordt een module manifest gemaakt met alle manifest waarden die u expliciet hebt opgegeven, en met de rest die de juiste standaard waarde bevat.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Ten slotte kunt u ook een leeg. psd1-bestand maken en de sjabloon onder aan dit onderwerp kopiëren naar het bestand en de relevante waarden invullen. De enige echte vereiste in dit geval is om ervoor te zorgen dat het bestand dezelfde naam heeft als de module.

2. Voeg in alle extra elementen toe aan het manifest dat u in het bestand wilt hebben.

   Normaal gesp roken wordt dit in de gewenste tekst editor, zoals Klad blok, gedaan. Dit is echter technisch een script bestand dat code bevat. u kunt het dus bewerken in een echte scripting-of ontwikkel omgeving, zoals Visual Studio code. Houd er rekening mee dat alle elementen van een manifest bestand optioneel zijn, met uitzonde ring van het ModuleVersion-nummer.

   Zie de **module manifest elementen** hieronder voor beschrijvingen van de sleutels en waarden die u kunt hebben in een module manifest. Zie de parameter beschrijvingen in de cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) voor meer informatie.

3. U kunt desgewenst extra code toevoegen aan het module manifest, om eventuele scenario's op te lossen die niet worden gedekt door de elementen van de basis module manifest.

   Vanwege beveiligings problemen voert Power shell slechts een kleine subset van de beschik bare bewerkingen uit in een manifest bestand van de module. Over het algemeen kunt u de **if** -instructie, reken kundige en vergelijkings operators en de basis-Power shell-gegevens typen gebruiken.

4. Nadat u het module manifest hebt gemaakt, kunt u dit testen (om te bevestigen dat alle in het manifest beschreven paden correct zijn) met een aanroep van [test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Zorg ervoor dat het module manifest zich bevindt in het hoogste niveau van de map die uw module bevat.

   Wanneer u uw module op een systeem kopieert en importeert, gebruikt Power shell het module manifest om uw module te importeren.

6. Desgewenst kunt u uw module manifest rechtstreeks testen met een aanroep van [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) by dot, het manifest zelf.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Manifest elementen van module

In de volgende tabel worden de elementen beschreven die u in een module manifest kunt hebben

|Element|Standaardinstelling|Beschrijving|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Type: teken reeks|' '|Script module of binair module bestand dat is gekoppeld aan dit manifest. In eerdere versies van Power shell heet dit element de ModuleToProcess.<br /><br /> Mogelijke typen voor de hoofd module kunnen leeg zijn (waardoor deze **manifest** module wordt gemaakt), de naam van een script module (. psm1, waarmee deze **script** module wordt gemaakt) of de naam van een binaire module (. exe of. dll, waarmee deze **binaire** module wordt gemaakt). Als u de naam van een module manifest (. psd1) of een script bestand (. ps1) in dit element plaatst, treedt er een fout op.|
|ModuleVersion<br /><br /> Type: teken reeks|1.0|Het versie nummer van deze module. De teken reeks moet kunnen worden geconverteerd naar [System. version]. Dat wil zeggen ' #. #. #. #. # '. `Import-Module` laadt de eerste module die wordt gevonden op de **$psModulePath** die overeenkomt met de naam en heeft ten minste als hoge a ModuleVersion, als de para meter `-MinimumVersion`. Als u een specifieke versie wilt importeren, gebruikt u in plaats daarvan de para meter @ no__t-0.<br /><br /> Voorbeeld: `ModuleVersion = '1.0'`|
|GPT<br /><br /> Type: teken reeks|Automatisch gegenereerde GUID|ID die wordt gebruikt om deze module uniek te identificeren. Houd er rekening mee dat u een module momenteel niet op GUID kunt importeren.<br /><br /> Voorbeeld: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Lijsten<br /><br /> Type: teken reeks|Geen|Auteur van deze module.<br /><br /> Voorbeeld: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Type: teken reeks|Herkend|Bedrijf of leverancier van deze module.<br /><br /> Voorbeeld: `CompanyName = 'Fabrikam'`|
|Copyright<br /><br /> Type: teken reeks|(c) [currentYear] [Auteur]. Alle rechten voorbehouden.|Copyright verklaring voor deze module.<br /><br /> Voorbeeld: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Beschrijving<br /><br /> Type: teken reeks|' '|Beschrijving van de functionaliteit van deze module.<br /><br /> Voorbeeld: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Type: teken reeks|' '|Minimale versie van de Windows Power shell-engine die vereist is voor deze module. De huidige geldige waarden zijn 1,0, 2,0, 3,0, 4,0 en 5,0.<br /><br /> Voorbeeld: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Type: teken reeks|' '|Hiermee geeft u de naam op van de Windows Power shell-host die wordt vereist door de module. Deze naam wordt verschaft door Windows Power shell. Als u de naam van een hostprogramma wilt zoeken, typt u het volgende in het programma: `$host.name`.<br /><br /> Voorbeeld: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Type: teken reeks|' '|Mini maal vereiste versie van de Windows Power shell-host die is vereist voor deze module.<br /><br /> Voorbeeld: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Type: teken reeks|' '|Mini maal vereiste versie van Microsoft .NET Framework dat is vereist voor deze module.<br /><br /> Voorbeeld: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Type: teken reeks|' '|De minimale versie van de Common Language Runtime (CLR) die vereist is voor deze module.<br /><br /> Voorbeeld: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Type: teken reeks|' '|De processor architectuur (geen, x86, amd64) die is vereist voor deze module. Geldige waarden zijn x86, AMD64, IA64 en geen (onbekend of niet opgegeven).<br /><br /> Voorbeeld: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Type: [string []]|@()|Modules die moeten worden geïmporteerd in de globale omgeving voordat deze module wordt geïmporteerd. Hiermee worden alle modules die worden vermeld, geladen, tenzij ze al zijn geladen. (Sommige modules kunnen bijvoorbeeld al zijn geladen door een andere module.). Het is ook mogelijk om een specifieke versie op te geven die moet worden geladen met `RequiredVersion` in plaats van `ModuleVersion`. Als `ModuleVersion` wordt gebruikt, wordt de nieuwste versie geladen die beschikbaar is, met een minimum van de opgegeven versie.<br /><br /> Voorbeeld: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Voorbeeld: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Type: [string []]|@()|Assembly's die moeten worden geladen voordat deze module wordt geïmporteerd.<br /><br /> In tegens telling tot RequiredModules, laadt Power shell de RequiredAssemblies als deze nog niet zijn geladen.|
|ScriptsToProcess<br /><br /> Type: [string []]|@()|Script bestanden (. ps1) die worden uitgevoerd in de sessie status van de aanroeper wanneer de module wordt geïmporteerd. Dit kan de algemene sessie status zijn of, voor geneste modules, de sessie status van een andere module. U kunt deze scripts gebruiken om een omgeving voor te bereiden net zoals u een aanmeldings script zou kunnen gebruiken.<br /><br /> Deze scripts worden uitgevoerd voordat een van de modules die worden vermeld in het manifest, worden geladen.|
|TypesToProcess<br /><br /> Type: [string []]|@()|Type bestanden (. ps1xml) die moeten worden geladen bij het importeren van deze module.|
|FormatsToProcess<br /><br /> Type: [string []]|@()|Bestands indeling (. ps1xml) die moet worden geladen bij het importeren van deze module.|
|NestedModules<br /><br /> Type: [string []]|@()|Modules die moeten worden geïmporteerd als geneste modules van de module die is opgegeven in RootModule/ModuleToProcess.<br /><br /> Het toevoegen van een module naam aan dit element is vergelijkbaar met het aanroepen van `Import-Module` vanuit uw script of assembly-code. Het belangrijkste verschil is dat het eenvoudiger is om te zien wat u hier in het manifest bestand kunt laden. Als een module hier niet kan worden geladen, hebt u de daad werkelijke module nog niet geladen.<br /><br /> Naast andere modules kunt u ook script bestanden (. ps1) laden. Deze bestanden worden uitgevoerd in de context van de hoofd module. (Dit komt overeen met het script in de hoofd module.)|
|FunctionsToExport<br /><br /> Type: [string []]|@()|Hiermee geeft u de functies op die de module exporteert (joker tekens zijn toegestaan, maar worden afgeraden) naar de sessie status van de beller. Standaard worden er geen functies geëxporteerd. U kunt deze sleutel gebruiken om de functies weer te geven die door de module worden geëxporteerd.<br /><br /> De sessie status van de oproepende functie kan de algemene sessie status zijn of, voor geneste modules, de sessie status van een andere module. Bij het koppelen van geneste modules worden alle functies die worden geëxporteerd door een geneste module, geëxporteerd naar de algemene sessie status, tenzij een module in de keten de functie beperkt met behulp van de FunctionsToExport-sleutel.<br /><br /> Als het manifest ook aliassen voor de functies exporteert, kan deze sleutel functies verwijderen waarvan de aliassen worden weer gegeven in de AliasesToExport-sleutel, maar deze sleutel kan geen functie aliassen toevoegen aan de lijst.|
|CmdletsToExport<br /><br /> Type: [string []]|@()|Hiermee geeft u de cmdlets op die de module exporteert (joker tekens zijn toegestaan, maar worden afgeraden). Standaard worden er geen cmdlets geëxporteerd. U kunt deze sleutel gebruiken om de cmdlets weer te geven die door de module worden geëxporteerd.<br /><br /> De sessie status van de oproepende functie kan de algemene sessie status zijn of, voor geneste modules, de sessie status van een andere module. Wanneer u geneste modules koppelt, worden alle cmdlets die worden geëxporteerd door een geneste module uiteindelijk geëxporteerd naar de status van de globale sessie, tenzij een module in de keten de cmdlet beperkt met behulp van de CmdletsToExport-sleutel.<br /><br /> Als het manifest ook aliassen voor de cmdlets exporteert, kan met deze sleutel cmdlets worden verwijderd waarvan de aliassen worden weer gegeven in de AliasesToExport-sleutel, maar deze sleutel kan geen cmdlet-aliassen toevoegen aan de lijst.|
|VariablesToExport<br /><br /> Type: teken reeks|'*'|Hiermee geeft u de variabelen op die de module exporteert (joker tekens zijn toegestaan) naar de sessie status van de beller. Standaard worden alle variabelen geëxporteerd. U kunt deze sleutel gebruiken om de variabelen te beperken die door de module worden geëxporteerd.<br /><br /> De sessie status van de oproepende functie kan de algemene sessie status zijn of, voor geneste modules, de sessie status van een andere module. Wanneer u geneste modules koppelt, worden alle variabelen die worden geëxporteerd door een geneste module, geëxporteerd naar de globale sessie status, tenzij een module in de keten de variabele beperkt door gebruik te maken van de VariablesToExport-sleutel.<br /><br /> Als het manifest ook aliassen voor de variabelen exporteert, kan deze sleutel variabelen verwijderen waarvan de aliassen worden weer gegeven in de AliasesToExport-sleutel, maar met deze sleutel kunnen geen variabele aliassen aan de lijst worden toegevoegd.|
|AliasesToExport<br /><br /> Type: [string []]|@()|Hiermee geeft u de aliassen op die de module exporteert (joker tekens zijn toegestaan, maar worden afgeraden) naar de sessie status van de beller. Standaard worden er geen aliassen geëxporteerd. U kunt deze sleutel gebruiken om de aliassen weer te geven die door de module worden geëxporteerd.<br /><br /> De sessie status van de oproepende functie kan de algemene sessie status zijn of, voor geneste modules, de sessie status van een andere module. Wanneer u geneste modules koppelt, worden alle aliassen die worden geëxporteerd door een geneste module uiteindelijk geëxporteerd naar de status van de globale sessie, tenzij een module in de keten de alias beperkt met behulp van de AliasesToExport-sleutel.|
|ModuleList<br /><br /> Type: [string []]|@()|Hiermee geeft u alle modules op die zijn verpakt met deze module. Deze modules kunnen worden ingevoerd op naam (een door komma's gescheiden teken reeks) of als een hash-tabel met de sleutels module en GUID. De hash-tabel kan ook een optionele ModuleVersion-sleutel hebben. De ModuleList-sleutel is ontworpen om te fungeren als een module-inventarisatie. Deze modules worden niet automatisch verwerkt.|
|File List<br /><br /> Type: [string []]|@()|Een lijst met alle bestanden die bij deze module zijn verpakt. Net als bij ModuleList is File List de hulp om u te helpen als inventarisatie lijst en niet anderszins te worden verwerkt.|
|PrivateData<br /><br /> Type: [object]|@{...}|Hiermee geeft u alle persoonlijke gegevens op die moeten worden door gegeven aan de hoofd module die is opgegeven door de RootModule/ModuleToProcess-sleutel.|
|HelpInfoURI<br /><br /> Type: teken reeks|' '|HelpInfo-URI van deze module.|
|DefaultCommandPrefix<br /><br /> Type: teken reeks|' '|Standaard voorvoegsel voor opdrachten die vanuit deze module worden geëxporteerd. Het standaard voorvoegsel overschrijven met `Import-Module`-voor voegsel.|

## <a name="sample-module-manifest"></a>Voor beeld-module manifest

In het volgende voor beeld van een module manifest ziet u de sleutels en de standaard waarden in een module manifest. Dit voor beeld is gemaakt met behulp van de cmdlet `New-ModuleManifest` in Windows Power Shell 3,0. Bij het maken van meerdere modules kunt u met deze cmdlet een manifest sjabloon maken die vervolgens voor verschillende modules kan worden gewijzigd.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 2019-10-09
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b888e5a2-8578-4c0b-938d-0cd9b5b836ba'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2019 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
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

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-module schrijven](./writing-a-windows-powershell-module.md)
