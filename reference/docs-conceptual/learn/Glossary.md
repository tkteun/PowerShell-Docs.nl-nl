---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows Power shell-woorden lijst
ms.openlocfilehash: 1e2285bb49ed6a30fb5624ab3cf136cbf06401b5
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810566"
---
# <a name="windows-powershell-glossary"></a>Windows Power shell-woorden lijst

|Term|Definitie|
|--------|--------------|
|binaire module|Een Windows Power shell-module met een binaire module bestand (. dll). Een binaire module kan een module manifest bevatten.|
|algemene para meter|Een para meter die wordt toegevoegd aan alle cmdlets, geavanceerde functies en werk stromen door de Windows Power shell-engine.|
|punt bron|In Windows Power shell kunt u een opdracht starten door een punt en een spatie voor de opdracht te typen. Opdrachten die met een punt zijn genoteerd, worden uitgevoerd in de huidige scope in plaats van in een nieuwe scope. Alle variabelen, aliassen, functies of stations die door de opdracht worden gemaakt, worden gemaakt in het huidige bereik en zijn beschikbaar voor gebruikers wanneer de opdracht is voltooid.|
|dynamische module|Een module die alleen bestaat in het geheugen. Met de cmdlets New-module en import-PSSession worden dynamische modules gemaakt.|
|dynamische para meter|Een para meter die wordt toegevoegd aan een Windows Power shell-cmdlet,-functie of-script onder bepaalde voor waarden. Cmdlets, functies, providers en scripts kunnen dynamische para meters toevoegen.|
|Opmaak bestand|Een Windows Power shell XML-bestand met de extensie. Format. ps1xml dat bepaalt hoe Windows Power shell een object weergeeft op basis van het .NET Framework type.|
|algemene sessie status|De sessie status die de gegevens bevat die toegankelijk is voor de gebruiker van een Windows Power shell-sessie.|
|host|De interface die door de Windows Power shell-engine wordt gebruikt om met de gebruiker te communiceren. De host geeft bijvoorbeeld op hoe prompts worden afgehandeld tussen Windows Power shell en de gebruiker.|
|hosttoepassing|Een programma dat de Windows Power shell-engine in het proces laadt en gebruikt om bewerkingen uit te voeren.|
|invoer verwerkings methode|Een methode die een cmdlet kan gebruiken voor het verwerken van de records die worden ontvangen als invoer. De invoer methoden omvatten de methode BeginProcessing, de methode ProcessRecord, de methode EndProcessing en de methode StopProcessing.|
|Manifest module|Een Windows Power shell-module met een manifest en waarvan de RootModule-sleutel leeg is.|
|module manifest|Een Windows Power shell-gegevens bestand (. psd1) waarmee de inhoud van een module wordt beschreven en waarmee wordt bepaald hoe een module wordt verwerkt.|
|sessie status van de module|De sessie status die de open bare en persoonlijke gegevens van een Windows Power shell-module bevat. De persoonlijke gegevens in deze sessie status zijn niet beschikbaar voor de gebruiker van een Windows Power shell-sessie.|
|niet-afsluit fout|Er is een fout opgetreden die Windows Power shell niet stopt met het verwerken van de opdracht.|
|zelfstandig|Het woord dat volgt op het afbreek streepje in de naam van een Windows Power shell-cmdlet. In het zelfstandig naam woord worden de resources beschreven waarop de cmdlet optreedt.|
|parameterset|Een groep para meters die in dezelfde opdracht kunnen worden gebruikt om een specifieke actie uit te voeren.|
|teer|In Windows Power shell om de resultaten van de voor gaande opdracht als invoer naar de volgende opdracht in de pijp lijn te verzenden.|
|pijp lijn|Een reeks opdrachten die zijn verbonden door pijplijn operators (&#124;) (ASCII 124). Elke pijplijn operator verzendt de resultaten van de voor gaande opdracht als invoer voor de volgende opdracht.|
|PSSession|Een type Windows Power shell-sessie dat door de gebruiker wordt gemaakt, beheerd en gesloten.|
|hoofd module|De module die is opgegeven in de sleutel RootModule in een module manifest.|
|runs|In Windows Power shell wordt de besturings omgeving waarin elke opdracht in een pijp lijn wordt uitgevoerd.|
|script blok|In de programmeer taal Windows Power shell, een verzameling instructies of expressies die kunnen worden gebruikt als één eenheid. Een script blok kan argumenten en retour waarden accepteren.|
|script module|Een Windows Power shell-module waarvan de hoofd module een script module bestand is (. psm1). Een script module kan een module manifest bevatten.|
|script module bestand|Een bestand dat een Windows Power shell-script bevat. Het script definieert de leden die de script module exporteert. Script module bestanden hebben de bestandsnaam extensie. psm1.|
|shell|De opdrachtinterpreter die wordt gebruikt voor het door geven van opdrachten aan het besturings systeem.|
|switch parameter|Een para meter die geen argument gebruikt.|
|fout bij beëindigen|Er is een fout opgetreden bij het verwerken van de opdracht door Windows Power shell.|
|trans actie|Een Atomic-werk eenheid. Het werk in een trans actie moet als geheel worden voltooid. Als een deel van de trans actie mislukt, mislukt de hele trans actie.|
|bestands typen|Een Windows Power shell XML-bestand met de extensie. ps1xml, dat de eigenschappen van Microsoft .NET Framework-typen in Windows Power shell uitbreidt.|
|term|Het woord dat voorafgaat aan het afbreek streepje in de naam van een Windows Power shell-cmdlet. De bewerking beschrijft de actie die de cmdlet uitvoert.|
|Windows PowerShell|Een opdracht regel-shell en script technologie op basis van taken waarmee IT-beheerders uitgebreide controle en automatisering van systeembeheer taken bieden.|
|Windows Power shell-opdracht|De elementen in een pijp lijn die ervoor zorgen dat een actie wordt uitgevoerd. Windows Power shell-opdrachten kunnen worden getypt op het toetsen bord of worden aangeroepen door een programma.|
|Windows Power shell-gegevens bestand|Een tekst bestand met de bestandsnaam extensie. psd1. Windows Power shell gebruikt gegevens bestanden voor verschillende doel einden, zoals het opslaan van module manifest gegevens en het opslaan van vertaalde teken reeksen voor script-intertalen.|
|Windows Power Shell-station|Een virtuele schijf die rechtstreekse toegang biedt tot een gegevens archief. Het kan worden gedefinieerd door een Windows Power shell-provider of worden gemaakt op de opdracht regel. Stations die zijn gemaakt op de opdracht regel, zijn sessie-specifieke stations en gaan verloren wanneer de sessie wordt gesloten.|
|Windows PowerShell ISE (Integrated Scripting Environment)|Een Windows Power shell-hosttoepassing waarmee u opdrachten kunt uitvoeren en scripts kunt schrijven, testen en opsporen in een beschrijvende, Unicode-compatibele omgeving.|
|Windows PowerShell-module|Een onafhankelijke herbruikbare eenheid waarmee u uw Windows Power shell-code kunt partitioneren, organiseren en samen voegen. Een module kan cmdlets, providers, functies, variabelen en andere typen resources bevatten die als één eenheid kunnen worden geïmporteerd.|
|Windows Power shell-provider|Een op Microsoft .NET Framework gebaseerd programma dat de gegevens in een gespecialiseerd gegevens archief beschikbaar maakt in Windows Power shell, zodat u het kunt weer geven en beheren.|
|Windows Power shell-script|Een script dat is geschreven in de Windows Power shell-taal.|
|Windows Power shell-script bestand|Een bestand met de extensie. ps1 en dat een script bevat dat is geschreven in de Windows Power shell-taal.|
|Windows Power shell-module|Een resource die een set cmdlets, providers en Microsoft .NET Framework-typen definieert die kunnen worden toegevoegd aan de Windows Power shell-omgeving.|
|Windows Power shell-werk stroom|Een werkstroom is een opeenvolging van geprogrammeerde, met elkaar verbonden stappen waarmee langlopende taken worden uitgevoerd of die de coördinatie vereisen van meerdere stappen op meerdere apparaten of beheerde knooppunten. De Windows Power shell-werk stroom stelt IT-professionals en ontwikkel aars in staat om reeksen van beheer activiteiten voor meerdere apparaten of afzonderlijke taken binnen een werk stroom te schrijven als werk stromen. Met Windows Power shell-werk stroom kunt u zowel Windows Power shell-scripts als XAML-bestanden aanpassen en uitvoeren als werk stromen.|
