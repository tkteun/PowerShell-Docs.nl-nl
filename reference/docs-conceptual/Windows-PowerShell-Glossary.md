---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Woordenlijst voor de Windows PowerShell
ms.assetid: b0f88cbe-cb83-4912-a301-184534cb35c7
ms.openlocfilehash: fd15667939fd9b3ea705806686b626645519588a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-glossary"></a>Woordenlijst voor de Windows PowerShell


|Term|Definitie|
|--------|--------------|
|binaire module|Een Windows PowerShell-module waarvan root-module een binaire modulebestand (.dll is). Een binaire-module kan mogelijk niet bevatten of een module-manifest.|
|algemene parameter|Een parameter die wordt toegevoegd aan alle cmdlets, geavanceerde functies en werkstromen door de engine voor Windows PowerShell.|
|punt-bron|In Windows PowerShell starten van een opdracht door een punt en een spatie voor de opdracht te typen. Opdrachten die punt afkomstig zijn uitgevoerd in de huidige scope in plaats van in een nieuwe scope. Alle variabelen, aliassen, functies of stations die opdracht maakt u in het huidige bereik zijn gemaakt en zijn beschikbaar voor gebruikers als de opdracht is voltooid.|
|dynamische module|Een module die alleen in het geheugen bestaat. De cmdlets New-Module en importeren-PSSession maken dynamische modules.|
|dynamische parameter|Een parameter die wordt toegevoegd aan een Windows PowerShell-cmdlet, de functie of het script onder bepaalde omstandigheden. Dynamische parameters kunnen toevoegen door cmdlets, functies, -providers en -scripts.|
|bestand opmaak|Een Windows PowerShell-XML-bestand met de. format.ps1xml-extensie en die definieert hoe een object op basis van de .NET Framework-type worden weergegeven in Windows PowerShell.|
|globale sessiestatus|De sessiestatus die de gegevens bevat die toegankelijk is voor de gebruiker van een Windows PowerShell-sessie.|
|host|De interface die door de engine voor Windows PowerShell gebruikt om te communiceren met de gebruiker. De host bevat bijvoorbeeld hoe prompts tussen Windows PowerShell en de gebruiker worden verwerkt.|
|Host-toepassing|Een programma dat de Windows PowerShell-engine in het proces wordt geladen en gebruikt deze bewerkingen uit te voeren.|
|invoer verwerken van methode|Een methode die een cmdlet gebruiken kunt voor het verwerken van de records die het ontvangt als invoer. De van invoer-verwerkingsmethoden zijn: de methode BeginProcessing, de methode ProcessRecord, de methode EndProcessing en de methode StopProcessing.|
|manifestmodule|Een Windows PowerShell-module die een manifest heeft en waarvan RootModule-sleutel is leeg.|
|module-manifest|Een Windows PowerShell gegevensbestand (.psd1) die de inhoud van een module wordt beschreven en die bepaalt hoe een module wordt verwerkt.|
|module-sessiestatus|De sessiestatus met de openbare en persoonlijke gegevens van een Windows PowerShell-module. De persoonlijke gegevens in de status van deze sessie is niet beschikbaar voor de gebruiker van een Windows PowerShell-sessie.|
|fout niet wordt beëindigd|Een fout die niet de Windows PowerShell stopt niet door kan gaan om de opdracht te verwerken.|
|zelfstandig naamwoord|Het woord dat volgt op het koppelteken in de naam van een Windows PowerShell-cmdlet. Het zelfstandig naamwoord beschrijving van de bronnen waarop de cmdlet fungeert.|
|Parameterset|Een groep met parameters die kan worden gebruikt in dezelfde opdracht voor een specifieke actie uitgevoerd.|
|pipe|In Windows PowerShell voor het verzenden van de resultaten van de voorgaande opdracht als invoer voor de volgende opdracht in de pijplijn.|
|pipeline|Een reeks opdrachten die verbonden zijn door pipeline-operators (&#124;) (ASCII 124). Elke pipeline-operator verzendt de resultaten van de voorgaande opdracht als invoer voor de volgende opdracht.|
|PSSession|Een type van Windows PowerShell-sessie die is gemaakt, beheerd en door de gebruiker zijn gesloten.|
|basis-module|De module die is opgegeven in de sleutel RootModule in een module-manifest.|
|Runspace|In Windows PowerShell, de besturingsomgeving waarin elke opdracht in een pijplijn is uitgevoerd.|
|scriptblok|Programmeren taal, een verzameling instructies of expressies die kunnen worden gebruikt als een eenheid in de Windows PowerShell. Een scriptblok kan accepteren de argumenten en retourwaarden.|
|scriptmodule|Een Windows PowerShell-module waarvan root-module een script module-bestand (.psm1 is). Een scriptmodule kan mogelijk niet bevatten of een module-manifest.|
|module-scriptbestand|Een bestand met een Windows PowerShell-script. Het script definieert de leden die door de scriptmodule worden geëxporteerd. Module scriptbestanden hebben de psm1-bestandsnaamextensie.|
|Shell|De opdrachtinterpreter die wordt gebruikt voor het doorgeven van opdrachten op het besturingssysteem.|
|switch-parameter|Een parameter die geen argument.|
|afsluitfout|Een fout die voorkomt dat Windows PowerShell verwerken van de opdracht.|
|Transactie|Een atomic-eenheid van het werk. Het werk in een transactie moet worden uitgevoerd in zijn geheel; Als een deel van de transactie mislukt, wordt de hele transactie mislukt.|
|typen bestand|Een Windows PowerShell-XML-bestand dat de extensie .ps1xml en die de eigenschappen van Microsoft .NET Framework-typen in Windows PowerShell wordt uitgebreid.|
|Term|Het woord dat voorafgaat aan het koppelteken in de naam van een Windows PowerShell-cmdlet. De term beschrijft de actie die de cmdlet uitvoert.|
|Windows PowerShell|Een opdrachtregel-shell en taakgebaseerde scripttechnologie waarmee IT-beheerders uitgebreide controle en automatisering van systeem beheertaken.|
|Windows PowerShell-opdracht|De elementen in een pijplijn die ertoe leiden een actie dat uit te voeren. Windows PowerShell-opdrachten zijn getypt op het toetsenbord of programmatisch aangeroepen.|
|Windows PowerShell-gegevensbestand|Een tekstbestand met de extensie .psd1. Windows PowerShell maakt gebruik van gegevensbestanden worden opgeslagen voor verschillende doeleinden, zoals de module-manifest gegevens op te slaan en het opslaan van de vertaalde tekenreeksen voor verschillende talen script.|
|Windows PowerShell-station|Een virtuele schijf die rechtstreekse toegang tot een gegevensarchief biedt. Het kan worden gedefinieerd door een Windows PowerShell-provider of gemaakt op de opdrachtregel. Stations die zijn gemaakt op de opdrachtregel zijn sessie-specifieke stations en gaan verloren wanneer de sessie wordt afgesloten.|
|Windows PowerShell ISE (Integrated Scripting Environment)|Een Windows PowerShell-hosttoepassing u opdrachten kunt uitvoeren kunt en schrijven, testen en fouten opsporen in scripts in een omgeving met gebruiksvriendelijke, syntaxis kleur compatibel is met Unicode.|
|Windows PowerShell-module|Een zelfstandige herbruikbare eenheid waarmee u partitioneren, organiseert en uw Windows PowerShell-code als abstract. Een module kan bevatten cmdlets, providers, functies, variabelen en andere typen resources die kunnen worden geïmporteerd als één eenheid.|
|Windows PowerShell-provider|Een Microsoft .NET Framework-programma waarmee de gegevens in een speciale gegevensarchief beschikbaar in Windows PowerShell, zodat u kunt bekijken en beheren.|
|Windows PowerShell-script|Een script dat is geschreven in de taal van Windows PowerShell.|
|Windows PowerShell-scriptbestand|Een bestand dat de .ps1-extensie heeft en dat een script dat is geschreven in de taal van Windows PowerShell bevat.|
|Windows PowerShell-module|Een bron die u definieert een reeks cmdlets, providers en Microsoft .NET Framework-typen die kunnen worden toegevoegd aan de Windows PowerShell-omgeving.|
|Windows PowerShell-werkstroom|Een werkstroom is een opeenvolging van geprogrammeerde, met elkaar verbonden stappen waarmee langlopende taken worden uitgevoerd of die de coördinatie vereisen van meerdere stappen op meerdere apparaten of beheerde knooppunten. Windows PowerShell Workflow kunnen IT-professionals en ontwikkelaars ontwerpen met reeksen van activiteiten voor beheer van meerdere apparaten of één taken binnen een werkstroom als werkstromen. Windows PowerShell-werkstroom kunt u aanpassen en Windows PowerShell-scripts en XAML-bestanden als werkstromen uitvoeren.|