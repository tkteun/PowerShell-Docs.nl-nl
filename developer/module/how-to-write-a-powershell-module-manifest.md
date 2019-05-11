---
title: Over het schrijven van een PowerShell-Module-Manifest | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 93a8c11099a9883127bca87422e1acaebfd2c093
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670283"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Een manifest voor een PowerShell-module schrijven

Nadat u hebt geschreven uw Windows PowerShell-module, kunt u een module-manifest (optioneel) toevoegen. Een module-manifest is een PowerShell-scriptbestand dat u gebruiken kunt om gegevens over de module te nemen. U kunt bijvoorbeeld beschrijven de auteur, opgeven van bestanden in de module (zoals geneste modules), uitvoeren van scripts voor het aanpassen van de gebruikersomgeving, type en de opmaak bestanden laden, systeemvereisten te definiëren en beperken van de leden die door de module worden geëxporteerd.

## <a name="creating-a-module-manifest"></a>Het maken van een Module-Manifest

Een *module-manifest* is een Windows PowerShell-gegevensbestand (.psd1) die de inhoud van een module wordt beschreven en wordt bepaald hoe een module worden verwerkt. Het manifestbestand zelf is een tekstbestand met een hash-tabel van sleutels en waarden. U koppelen een manifestbestand aan een module door hetzelfde als de module naamgeving en in de hoofdmap van de modulemap plaatst.

Voor eenvoudige modules die alleen een enkel .psm1 of binaire assembly bevatten, is een module-manifest optioneel. Het wordt echter aanbevolen dat u een module-manifest indien mogelijk, zoals ze zijn nuttig om te helpen u uw code kunt indelen en om versiebeheer informatie te onderhouden. Een module-manifest is bovendien vereist voor het exporteren van een assembly die is geïnstalleerd in de global assemblycache. Een module-manifest is ook vereist voor modules die ondersteuning bieden voor de bij te werken Help-functie. Dat wil zeggen, bij te werken Help maakt gebruik van de **HelpInfoUri** sleutel in de module-manifest te vinden van het Help-informatie (HelpInfo XML)-bestand met de locatie van de bijgewerkte help-bestanden voor de module. Zie voor meer informatie over het bij te werken Help [ondersteunende bij te werken Help](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Het maken en gebruiken van een module-manifest

1. U hebt verschillende mogelijkheden voor het maken van een module-manifest:

   1. De hash-tabel maken met de minimale vereiste informatie rechtstreeks en sla deze op een .psd1-bestand met dezelfde naam als de module. Zodra u dit hebt gedaan, kunt u open het bestand en de gewenste waarden handmatig toevoegen.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. Of bel de [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet, met een of meer van de standaardwaarden als parameters doorgegeven. (Houd er rekening mee dat het alleen de naam van het bestand vereist voor het genereren van een manifest echter is.) Hiermee wordt een module-manifest gemaakt met alle manifest waarden opgegeven expliciet is opgegeven, en met de rest met de juiste standaardwaarde.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Ten slotte, u kunt ook maakt u een lege .psd1-bestand en kopieer de sjabloon aan de onderkant van dit onderwerp in het bestand, en vul de relevante waarden. De enige echte vereiste zou in dit geval zijn om ervoor te zorgen dat het bestand is met de naam van de module.

2. In eventuele extra elementen toevoegen aan het manifest dat u wilt hebben in het bestand.

   In het algemeen wordt deze waarschijnlijk worden uitgevoerd in de teksteditor u liever, zoals Kladblok. Maar dit technisch gezien is een scriptbestand bevat de code, zodat u kunt desgewenst bewerken in een werkelijke uitvoeren van scripts of ontwikkeling omgeving, zoals de PowerShell ISE. Nogmaals, houd er rekening mee dat alle elementen van een manifestbestand optioneel, met uitzondering van het aantal ModuleVersion zijn.

   Zie voor beschrijvingen van de sleutels en waarden die u in een module-manifest hebben kunt, het **Module-Manifest van de elementen** hieronder. Voor meer informatie, Zie de beschrijvingen van de parameters in de [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet.

3. U kunt desgewenst aanvullende code toevoegen aan uw module-manifest voor alle scenario's die niet wordt gedekt door de basismodule manifest elementen.

   Vanwege beveiligingsproblemen, PowerShell slechts een kleine subset van de beschikbare bewerkingen uitgevoerd in een module-manifest-bestand. Over het algemeen kunt u de **als** -instructie, berekeningen en vergelijking van de operators en de eenvoudige PowerShell-gegevenstypen.

4. Nadat u uw module-manifest hebt gemaakt, kunt u deze (om te bevestigen dat de paden die worden beschreven in het manifest weet juist) testen met een aanroep naar [Test ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Zorg ervoor dat uw module-manifest zich bevinden in het hoogste niveau van de map waarin de module.

   Wanneer u de module op een systeem kopiëren en importeren, PowerShell module-manifest gebruikt om de module te importeren.

6. Desgewenst kunt u rechtstreeks met een aanroep naar de module-manifest testen [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) door dotsourcing het manifest zelf.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Module-Manifest elementen

De volgende tabel beschrijft de elementen die u in een module-manifest hebben kunt

|Element|Standaard|Description|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Type: tekenreeks|' '|Module of binaire module scriptbestand dat is gekoppeld aan dit manifest. Eerdere versies van PowerShell wordt deze element van de ModuleToProcess genoemd.<br /><br /> Mogelijk typen voor het root-module kunnen niet leeg zijn (waardoor dit een **Manifest** module), de naam van een scriptmodule (.psm1, waardoor dit een **Script** module), of de naam van een binaire-module (.exe of .dll, Dit is een **binaire** module). Als u de naam van een module-manifest (.psd1) of een scriptbestand (.ps1) in dit element plaatst, wordt een fout optreden.|
|ModuleVersion<br /><br /> Type: tekenreeks|1.0|Versienummer van deze module. De tekenreeks moet kunt converteren naar [System.Version]. Dat wil zeggen, ' #. #. #. #. #'. `Import-Module` wordt de eerste module laden gevonden op de **$psModulePath** die overeenkomt met de naam, en ten minste zo hoog een ModuleVersion heeft als de `-MinimumVersion` parameter. Als u wilt importeren in een specifieke versie, gebruik de`-RequiredVersion` parameter, in plaats daarvan.<br /><br /> Voorbeeld: `ModuleVersion = '1.0'`|
|GUID<br /><br /> Type: tekenreeks|Automatisch gegenereerde GUID|De ID die wordt gebruikt voor het aanduiden van deze module. Houd er rekening mee dat u momenteel een module door de GUID kan niet importeren.<br /><br /> Voorbeeld: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Auteur<br /><br /> Type: tekenreeks|Geen|De auteur van deze module.<br /><br /> Voorbeeld: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Type: tekenreeks|Onbekend|Bedrijf of de leverancier van deze module.<br /><br /> Voorbeeld: `CompanyName = 'Fabrikam'`|
|Copyright<br /><br /> Type: tekenreeks|(c) [currentYear] [auteur]. Alle rechten voorbehouden.|Copyrightinformatie voor deze module.<br /><br /> Voorbeeld: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Description<br /><br /> Type: tekenreeks|' '|Beschrijving van de functionaliteit van deze module.<br /><br /> Voorbeeld: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Type: tekenreeks|' '|Minimale versie van de Windows PowerShell-engine die is vereist voor deze module. Huidige geldige waarden zijn 1.0, 2.0, 3.0, 4.0 en 5.0.<br /><br /> Voorbeeld: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Type: tekenreeks|' '|Hiermee geeft u de naam van de Windows PowerShell-host die is vereist door de module. Deze naam wordt geleverd door Windows PowerShell. Typ de naam van een hostprogramma, in het programma vindt: `$host.name` .<br /><br /> Voorbeeld: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Type: tekenreeks|' '|Minimale versie van de host Windows PowerShell is vereist voor deze module.<br /><br /> Voorbeeld: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Type: tekenreeks|' '|Minimale versie van Microsoft .NET Framework is vereist voor deze module.<br /><br /> Voorbeeld: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Type: tekenreeks|' '|Minimale versie van de common language runtime (CLR) vereist voor deze module.<br /><br /> Voorbeeld: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Type: tekenreeks|' '|Processorarchitectuur (geen, X86, Amd64) vereist voor deze module. Geldige waarden zijn x86, AMD64 IA64, en niets in (onbekend of niet-opgegeven).<br /><br /> Voorbeeld: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Type: [string[]]|@()|Modules die moeten worden geïmporteerd in de globale omgeving vóór het importeren van deze module. Alle modules die worden vermeld, tenzij ze al geladen zijn, dit wordt geladen. (Bijvoorbeeld: sommige modules mogelijk al geladen door een andere module.). Het is ook mogelijk om op te geven van een specifieke versie te laden met behulp van `RequiredVersion` in plaats van `ModuleVersion`. Bij het gebruik van `ModuleVersion` deze de nieuwste versie beschikbaar met een minimum van de opgegeven versie wordt geladen.<br /><br /> Voorbeeld: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Voorbeeld: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Type: [string[]]|@()|Assembly's die moeten worden geladen vóór het importeren van deze module.<br /><br /> Houd er rekening mee dat in tegenstelling tot RequiredModules, PowerShell laadt de RequiredAssemblies als ze niet al geladen.|
|ScriptsToProcess<br /><br /> Type: [string[]]|@()|Script (.ps1)-bestanden die worden uitgevoerd in de sessiestatus van de oproepende functie wanneer de module wordt geïmporteerd. Dit wordt mogelijk de globale sessie staat of, voor geneste modules, de status van de sessie van een andere module. U kunt deze scripts gebruiken om voor te bereiden van een omgeving, net zoals u een aanmeldingsscript kunt.<br /><br /> Deze scripts worden uitgevoerd voordat een van de modules die worden vermeld in het manifest worden geladen.|
|TypesToProcess<br /><br /> Type: [Object []]|@()|Typ bestanden (.ps1xml) moeten worden geladen bij het importeren van deze module.|
|FormatsToProcess<br /><br /> Type: [Object []]|@()|Bestanden (.ps1xml) moeten worden geladen bij het importeren van deze module-indeling.|
|NestedModules<br /><br /> Type: [Object []]|@()|Modules te importeren als een geneste modules van de module die is opgegeven in de velden RootModule/ModuleToProcess.<br /><br /> Naam van een module toe te voegen aan dit element is vergelijkbaar met aanroepen `Import-Module` uit vanuit uw code script of een assembly. Het belangrijkste verschil is dat het eenvoudiger om te zien wat u laadt hier in het manifestbestand is. Ook als een module niet laden hier, wordt u nog niet hebt geladen uw werkelijke module.<br /><br /> Naast andere modules, kunt u ook hier script (.ps1)-bestanden laden. Deze bestanden wordt uitgevoerd in de context van het root-module. (Dit is gelijk aan het script in uw hoofdmap module sourcing punt).|
|FunctionsToExport<br /><br /> Type: Tekenreeks|'*'|Hiermee geeft u de functies die door de module worden geëxporteerd (jokerteken tekens zijn toegestaan) status van de sessie van de oproepende functie. Standaard worden alle functies die worden geëxporteerd. U kunt deze sleutel gebruiken om te beperken van de functies die zijn geëxporteerd door de module.<br /><br /> Status van de sessie van de oproepende functie kan de globale sessie staat of, voor geneste modules, de status van de sessie van een andere module zijn. Bij het koppelen van geneste modules, worden alle functies die zijn geëxporteerd door een geneste module worden geëxporteerd naar de globale sessiestatus, tenzij een module in de keten Hiermee beperkt u de functie met behulp van de sleutel FunctionsToExport.<br /><br /> Als het manifest ook aliassen voor de functies exporteert, wordt deze sleutel functies waarvan aliassen worden vermeld in de sleutel AliasesToExport kunt verwijderen, maar deze sleutel kan functie aliassen niet toevoegen aan de lijst.|
|CmdletsToExport<br /><br /> Type: Tekenreeks|'*'|Hiermee geeft u de cmdlets die de module wordt geëxporteerd (jokerteken tekens zijn toegestaan). Standaard worden alle cmdlets geëxporteerd. U kunt deze sleutel gebruiken om te beperken van de cmdlets die zijn geëxporteerd door de module.<br /><br /> Status van de sessie van de oproepende functie kan de globale sessie staat of, voor geneste modules, de status van de sessie van een andere module zijn. Wanneer u een keten geneste modules maakt, worden alle cmdlets die zijn geëxporteerd door een geneste module uiteindelijk geëxporteerd naar de globale sessiestatus, tenzij een module in de keten Hiermee beperkt u de cmdlet met behulp van de sleutel CmdletsToExport.<br /><br /> Als het manifest ook aliassen voor de cmdlets exporteert, wordt deze sleutel cmdlets waarvan aliassen worden vermeld in de sleutel AliasesToExport kunt verwijderen, maar deze sleutel kan cmdlet aliassen niet toevoegen aan de lijst.|
|VariablesToExport<br /><br /> Type: Tekenreeks|'*'|Hiermee geeft u de variabelen die door de module worden geëxporteerd (jokerteken tekens zijn toegestaan) status van de sessie van de oproepende functie. Standaard worden alle variabelen worden geëxporteerd. U kunt deze sleutel gebruiken om te beperken van de variabelen die zijn geëxporteerd door de module.<br /><br /> Status van de sessie van de oproepende functie kan de globale sessie staat of, voor geneste modules, de status van de sessie van een andere module zijn. Wanneer u een keten geneste modules maakt, wordt alle variabelen die zijn geëxporteerd door een geneste module worden geëxporteerd naar de globale sessiestatus, tenzij een module in de keten Hiermee beperkt u de variabele met behulp van de sleutel VariablesToExport.<br /><br /> Als het manifest ook aliassen voor de variabelen exporteert, wordt deze sleutel variabelen waarvan aliassen worden vermeld in de sleutel AliasesToExport kunt verwijderen, maar deze sleutel niet variabele aliassen toevoegen aan de lijst.|
|AliasesToExport<br /><br /> Type: Tekenreeks|'*'|Hiermee geeft u de aliassen waarmee de module geëxporteerd (jokerteken tekens zijn toegestaan) status van de sessie van de oproepende functie. Standaard worden alle aliassen zijn geëxporteerd. U kunt deze sleutel gebruiken om te beperken de aliassen die zijn geëxporteerd door de module.<br /><br /> Status van de sessie van de oproepende functie kan de globale sessie staat of, voor geneste modules, de status van de sessie van een andere module zijn. Wanneer u een keten geneste modules maakt, worden alle aliassen die zijn geëxporteerd door een geneste module uiteindelijk geëxporteerd naar de globale sessiestatus, tenzij een module in de keten de alias beperkt met behulp van de sleutel AliasesToExport.|
|ModuleList<br /><br /> Type: [string[]]|@()|Hiermee geeft u de modules die zijn verpakt met deze module. Deze modules kunnen worden ingevoerd met de naam (een door komma's gescheiden tekenreeks) of als een hash-tabel met de modulenaam en -GUID-sleutels. De hash-tabel kan ook een optionele ModuleVersion sleutel hebben. De sleutel ModuleList is ontworpen om te fungeren als een module-inventarisatie. Deze modules worden niet automatisch verwerkt.|
|FileList<br /><br /> Type: [string[]]|@()|Lijst van alle bestanden die zijn ingepakt met deze module. Als met ModuleList, FileList is om u te helpen als een inventarislijst met en anders niet is verwerkt.|
|PrivateData<br /><br /> Type: [object]|' '|Hiermee geeft u alle persoonlijke gegevens die moeten worden doorgegeven aan de basismodule die is opgegeven door de velden RootModule/ModuleToProcess-sleutel.|
|HelpInfoURI<br /><br /> Type: tekenreeks|' '|HelpInfo URI van deze module.|
|DefaultCommandPrefix<br /><br /> Type: tekenreeks|' '|Standaardvoorvoegsel voor opdrachten van deze module worden geëxporteerd. Overschrijven de standaard voorvoegsel via `Import-Module` -voorvoegsel.|

## <a name="sample-module-manifest"></a>Voorbeeld van Module-Manifest

Het volgende voorbeeld module-manifest ziet u de sleutels en waarden in een module-manifest. In dit voorbeeld is gemaakt met behulp van de `New-ModuleManifest` cmdlet in Windows PowerShell 3.0. Bij het maken van meerdere modules, kunt u deze cmdlet gebruiken om een manifest sjabloon die vervolgens kan worden gewijzigd voor andere modules te maken.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-Module schrijven](./writing-a-windows-powershell-module.md)
