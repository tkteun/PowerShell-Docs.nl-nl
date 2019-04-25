---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Windows PowerShell Glossary
ms.assetid: b0f88cbe-cb83-4912-a301-184534cb35c7
ms.openlocfilehash: fd15667939fd9b3ea705806686b626645519588a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057334"
---
# <a name="windows-powershell-glossary"></a>Windows PowerShell Glossary


|Term|Definitie|
|--------|--------------|
|binaire-module|Een Windows PowerShell-module waarvan root-module een binaire modulebestand (.dll is). Een binaire module kan mogelijk niet bevatten of een module-manifest.|
|algemene parameter|Een parameter die wordt toegevoegd aan alle cmdlets, geavanceerde functies en werkstromen door de Windows PowerShell-engine.|
|punt-bron|In Windows PowerShell, om te beginnen een opdracht door een punt en een spatie vóór de opdracht te typen. Opdrachten die stip afkomstig zijn uitgevoerd in de huidige scope in plaats van in een nieuwe scope. Eventuele variabelen, aliassen, functies of stations die opdracht maakt u in het huidige bereik zijn gemaakt en zijn beschikbaar voor gebruikers wanneer de opdracht is voltooid.|
|dynamische module|Een module die alleen in het geheugen bestaat. De cmdlets New-Module en Import-PSSession maken dynamische modules.|
|dynamische parameter|Een parameter die wordt toegevoegd aan een Windows PowerShell-cmdlet, de functie of het script onder bepaalde omstandigheden. Dynamische parameters kunnen toevoegen door cmdlets, functies, -providers en -scripts.|
|opmaak van bestand|Een Windows PowerShell-XML-bestand met de. format.ps1xml-extensie en die wordt gedefinieerd hoe een object op basis van het .NET Framework-type worden weergegeven in Windows PowerShell.|
|globale sessiestatus|De sessiestatus met de gegevens die toegankelijk is voor de gebruiker van een Windows PowerShell-sessie.|
|host|De interface die de Windows PowerShell-engine gebruikt om te communiceren met de gebruiker. De host bevat bijvoorbeeld hoe prompts tussen Windows PowerShell en de gebruiker worden verwerkt.|
|Host-toepassing|Een programma dat de Windows PowerShell-engine in het proces geladen en gebruikt deze bewerkingen uit te voeren.|
|verwerken van methode invoer|Een methode die een cmdlet gebruiken kunt voor het verwerken van de records die deze ontvangt als invoer. De van invoer-verwerkingsmethoden zijn onder meer de methode BeginProcessing, de methode ProcessRecord de EndProcessing-methode en de methode StopProcessing.|
|manifest van de module|Een Windows PowerShell-module die een manifest heeft en waarvan de velden RootModule sleutel is leeg.|
|module-manifest|Een Windows PowerShell gegevensbestand (.psd1) met de beschrijving van de inhoud van een module en die bepaalt hoe een module worden verwerkt.|
|module-sessiestatus|De sessiestatus met de openbare en persoonlijke gegevens van een Windows PowerShell-module. De persoonlijke gegevens in de sessiestatus van deze is niet beschikbaar voor de gebruiker van een Windows PowerShell-sessie.|
|niet-afsluitfout|Een fout die niet dat de Windows PowerShell u verdergaat voorkomen wordt met het verwerken van de opdracht.|
|zelfstandig naamwoord|Het woord die volgt op het koppelteken in de naam van een Windows PowerShell-cmdlet. Het zelfstandig naamwoord beschrijving van de resources waarop de cmdlet fungeert.|
|Parameterset|Een groep van de parameters die kunnen worden gebruikt in dezelfde opdracht een bepaalde actie uit te voeren.|
|pipe|In Windows PowerShell voor het verzenden van de resultaten van de voorgaande opdracht als invoer voor de volgende opdracht in de pijplijn.|
|Pijplijn|Een reeks opdrachten die zijn verbonden via de pipeline-operators (&#124;) (124 ASCII). Elke pijplijn-operator verzendt de resultaten van de voorgaande opdracht als invoer voor de volgende opdracht.|
|PSSession|Een type van de Windows PowerShell-sessie die is gemaakt, beheerd en gesloten door de gebruiker.|
|basismodule|De module die is opgegeven in de velden RootModule-sleutel in een module-manifest.|
|Runspace|In Windows PowerShell, de operationele omgeving waarin elke opdracht in een pijplijn wordt uitgevoerd.|
|scriptblok|Programmeren taal, een verzameling instructies of expressies die kunnen worden gebruikt als één eenheid in de Windows PowerShell. Een scriptblok kan accepteren argumenten en waarden retourneren.|
|scriptmodule|Een Windows PowerShell-module waarvan root-module een scriptbestand voor module (.psm1 is). Een scriptmodule kan of kan een module-manifest niet opgenomen.|
|module-scriptbestand|Een bestand met een Windows PowerShell-script. Het script definieert de leden die de scriptmodule exporteert. Module-scriptbestanden hebben de .psm1-bestandsextensie.|
|Shell|De opdrachtinterpreter die wordt gebruikt voor opdrachten doorgeven aan het besturingssysteem.|
|switch-parameter|Een parameter die niet een argument neemt.|
|afsluitfout|Een fout die voorkomt dat Windows PowerShell voor het verwerken van de opdracht.|
|Transactie|Een atomische eenheid van het werk. Het werk in een transactie moet worden uitgevoerd als een geheel; Als een deel van de transactie is mislukt, wordt de hele transactie mislukt.|
|typen bestand|Een Windows PowerShell-XML-bestand dat de extensie .ps1xml heeft en dat de eigenschappen van Microsoft .NET Framework-typen in Windows PowerShell wordt uitgebreid.|
|term|Het woord die voorafgaat aan het koppelteken in de naam van een Windows PowerShell-cmdlet. Het werkwoord beschrijft de actie die de cmdlet uitvoert.|
|Windows PowerShell|Een opdrachtregel-shell en taak-scripttechnologie op basis van die voorziet in uitgebreide controle voor IT-beheerders en automatisering van systeem beheertaken.|
|Windows PowerShell-opdracht|De elementen in een pijplijn die ertoe leiden een actie die dat moet worden uitgevoerd. Windows PowerShell-opdrachten zijn getypt op het toetsenbord of via een programma wordt aangeroepen.|
|Windows PowerShell-gegevensbestand|Een tekstbestand dat de extensie .psd1 heeft. Windows PowerShell maakt gebruik van gegevensbestanden voor verschillende doeleinden, zoals de module-manifest gegevens opslaan en het opslaan van vertaalde tekenreeksen voor voorkeuren voor internationalisatie script.|
|Windows PowerShell-station|Een virtuele schijf die rechtstreekse toegang tot een gegevensarchief biedt. Het kan worden gedefinieerd door een Windows PowerShell-provider of gemaakt op de opdrachtregel. Stations die zijn gemaakt op de opdrachtregel zijn sessie-specifieke stations en gaan verloren wanneer de sessie is gesloten.|
|Windows PowerShell ISE (Integrated Scripting Environment)|Een Windows PowerShell-hosttoepassing waarmee u opdrachten uit te voeren en te schrijven, testen en fouten opsporen in scripts in een gebruiksvriendelijke, syntaxis kleur, compatibel is met Unicode-omgeving.|
|Windows PowerShell-module|Een op zichzelf staand herbruikbare eenheid waarmee u partitioneren, organiseren en uw Windows PowerShell-code als abstract. Een module kan bevatten cmdlets, providers, functies, variabelen en andere typen resources die kunnen worden geïmporteerd als één eenheid.|
|Windows PowerShell-provider|Een Microsoft .NET Framework-programma waarin de gegevens in een gespecialiseerde gegevensarchief beschikbaar zijn in Windows PowerShell zodat u kunt weergeven en beheren.|
|Windows PowerShell-script|Een script dat is geschreven in de Windows PowerShell-taal.|
|Windows PowerShell-scriptbestand|Een bestand dat de .ps1 extensie heeft en die een script dat is geschreven in de Windows PowerShell-taal bevat.|
|Windows PowerShell-module|Een resource die u definieert een reeks cmdlets en providers Microsoft .NET Framework-typen die kunnen worden toegevoegd aan de Windows PowerShell-omgeving.|
|Windows PowerShell-werkstroom|Een werkstroom is een opeenvolging van geprogrammeerde, met elkaar verbonden stappen waarmee langlopende taken worden uitgevoerd of die de coördinatie vereisen van meerdere stappen op meerdere apparaten of beheerde knooppunten. Windows PowerShell Workflow kunnen IT-professionals en ontwikkelaars ontwerpen met reeksen van activiteiten voor beheer van meerdere apparaten, of één taken binnen een werkstroom als werkstromen. Windows PowerShell-werkstroom kunt u aan te passen en Windows PowerShell-scripts en XAML-bestanden als werkstromen uitvoeren.|