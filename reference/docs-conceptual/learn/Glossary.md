---
ms.date: 06/11/2020
keywords: powershell,cmdlet
title: Verklarende woordenlijst voor PowerShell
ms.openlocfilehash: 8df76fa3a78e9701c28488db0bde25fa245b1160
ms.sourcegitcommit: 56463fb628a7d83dec4364e89417d83316c3e53b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2020
ms.locfileid: "84722861"
---
# <a name="powershell-glossary"></a>Verklarende woordenlijst voor PowerShell

|            Term             | Definitie |
| --------------------------- | ---------- |
| binaire module               | Een Power shell-module met een binaire module bestand (. dll). Een binaire module kan een module manifest bevatten. |
| algemene para meter            | Een para meter die wordt toegevoegd aan alle cmdlets, geavanceerde functies en werk stromen door de Power shell-engine. |
| punt bron                  | In Power shell kunt u een opdracht starten door een punt en een spatie voor de opdracht te typen. Opdrachten die met een punt zijn genoteerd, worden uitgevoerd in de huidige scope in plaats van in een nieuwe scope. Alle variabelen, aliassen, functies of stations die door de opdracht worden gemaakt, worden gemaakt in het huidige bereik en zijn beschikbaar voor gebruikers wanneer de opdracht is voltooid. |
| dynamische module              | Een module die alleen bestaat in het geheugen. Met de cmdlets New-module en import-PSSession worden dynamische modules gemaakt. |
| dynamische para meter           | Een para meter die wordt toegevoegd aan een Power shell-cmdlet, functie of script onder bepaalde voor waarden. Cmdlets, functies, providers en scripts kunnen dynamische para meters toevoegen. |
| Opmaak bestand             | Een Power shell-XML-bestand met de `.format.ps1xml` extensie en dat definieert hoe Power shell een object weergeeft op basis van het .NET Framework type. |
| algemene sessie status        | De sessie status die de gegevens bevat die toegankelijk zijn voor de gebruiker van een Power shell-sessie. |
| host                        | De interface die de Power shell-engine gebruikt om te communiceren met de gebruiker. De host geeft bijvoorbeeld op hoe prompts worden verwerkt tussen Power shell en de gebruiker. |
| hosttoepassing            | Een programma dat de Power shell-engine in het proces laadt en gebruikt om bewerkingen uit te voeren. |
| invoer verwerkings methode     | Een methode die een cmdlet kan gebruiken voor het verwerken van de records die worden ontvangen als invoer. De invoer methoden omvatten de methode BeginProcessing, de methode ProcessRecord, de methode EndProcessing en de methode StopProcessing. |
| Manifest module             | Een Power shell-module met een manifest en waarvan de RootModule-sleutel leeg is. |
| programma                      | Een onafhankelijke herbruikbare eenheid waarmee u uw Power shell-code kunt partitioneren, organiseren en samen voegen. Een module kan cmdlets, providers, functies, variabelen en andere typen resources bevatten die als één eenheid kunnen worden geïmporteerd. |
| module manifest             | Een Power shell-gegevens bestand ( `.psd1` ) dat de inhoud van een module beschrijft en die bepaalt hoe een module wordt verwerkt. |
| sessie status van de module        | De sessie status die de open bare en persoonlijke gegevens van een Power shell-module bevat. De persoonlijke gegevens in deze sessie status zijn niet beschikbaar voor de gebruiker van een Power shell-sessie. |
| niet-afsluit fout       | Er is een fout opgetreden die Power shell niet stopt met het verwerken van de opdracht. |
| zelfstandig                        | Het woord dat volgt op het koppel teken in de naam van een Power shell-cmdlet. In het zelfstandig naam woord worden de resources beschreven waarop de cmdlet optreedt. |
| parameterset               | Een groep para meters die in dezelfde opdracht kunnen worden gebruikt om een specifieke actie uit te voeren. |
| teer                        | In Power shell kunt u de resultaten van de voor gaande opdracht verzenden als invoer voor de volgende opdracht in de pijp lijn. |
| pijp lijn                    | Een reeks opdrachten die zijn verbonden door pijplijn operators (&#124;) (ASCII 124). Elke pijplijn operator verzendt de resultaten van de voor gaande opdracht als invoer voor de volgende opdracht. |
| Power shell-cmdlet           | Eén opdracht die deel uitmaakt van de pijplijn semantiek van Power shell. Dit omvat binaire (C#) cmdlets, geavanceerde script functies, CDXML en werk stromen. |
| PowerShell-opdracht          | De elementen in een pijp lijn die ervoor zorgen dat een actie wordt uitgevoerd. Power shell-opdrachten kunnen worden getypt op het toetsen bord of worden aangeroepen via een programma. |
| Power shell-gegevens bestand        | Een tekst bestand met de `.psd1` bestands extensie. Power shell gebruikt gegevens bestanden voor verschillende doel einden, zoals het opslaan van module manifest gegevens en het opslaan van vertaalde teken reeksen voor script-intertalen. |
| Power Shell-station            | Een virtuele schijf die rechtstreekse toegang biedt tot een gegevens archief. Het kan worden gedefinieerd door een Power shell-provider of worden gemaakt op de opdracht regel. Stations die zijn gemaakt op de opdracht regel, zijn sessie-specifieke stations en gaan verloren wanneer de sessie wordt gesloten. |
| providers                    | Een op Microsoft .NET Framework gebaseerd programma dat de gegevens in een gespecialiseerd gegevens archief beschikbaar maakt in Power shell, zodat u het kunt weer geven en beheren. |
| PSSession                   | Een type Power shell-sessie dat door de gebruiker wordt gemaakt, beheerd en gesloten. |
| hoofd module                 | De module die is opgegeven in de sleutel RootModule in een module manifest. |
| runs                    | In Power shell wordt de besturings omgeving waarin elke opdracht in een pijp lijn wordt uitgevoerd. |
| script blok                | In de programmeer taal Power shell, een verzameling instructies of expressies die kunnen worden gebruikt als één eenheid. Een script blok kan argumenten en retour waarden accepteren. |
| script bestand                 | Een bestand met de `.ps1` extensie en dat een script bevat dat is geschreven in de Power shell-taal. |
| script module               | Een Power shell-module waarvan de hoofd module een script module bestand ( `.psm1` ) is. Een script module kan een module manifest bevatten. |
| script module bestand          | Een bestand dat een Power shell-script bevat. Het script definieert de leden die de script module exporteert. Script module bestanden hebben de `.psm1` bestands extensie. |
| shell                       | De opdrachtinterpreter die wordt gebruikt voor het door geven van opdrachten aan het besturings systeem. |
| switch parameter            | Een para meter die geen argument gebruikt. |
| fout bij beëindigen           | Er is een fout opgetreden bij het verwerken van de opdracht door Power shell. |
| trans actie                 | Een Atomic-werk eenheid. Het werk in een trans actie moet als geheel worden voltooid. Als een deel van de trans actie mislukt, mislukt de hele trans actie. |
| bestands typen                  | Een Power shell-XML-bestand met de `.ps1xml` extensie en dat de eigenschappen van Microsoft .NET Framework-typen in Power shell uitbreidt. |
| term                        | Het woord dat voorafgaat aan het koppel teken in de naam van een Power shell-cmdlet. De bewerking beschrijft de actie die de cmdlet uitvoert. |
| Windows PowerShell ISE      | De geïntegreerde script omgeving: een Windows Power shell-hosttoepassing waarmee u opdrachten kunt uitvoeren en scripts kunt schrijven, testen en opsporen in een beschrijvende, Unicode-compatibele omgeving. |
| Windows Power shell-module  | Een resource die een set cmdlets, providers en Microsoft .NET Framework-typen definieert die kunnen worden toegevoegd aan de Windows Power shell-omgeving. |
| Windows Power shell-werk stroom | Een werkstroom is een opeenvolging van geprogrammeerde, met elkaar verbonden stappen waarmee langlopende taken worden uitgevoerd of die de coördinatie vereisen van meerdere stappen op meerdere apparaten of beheerde knooppunten. De Windows Power shell-werk stroom stelt IT-professionals en ontwikkel aars in staat om reeksen van beheer activiteiten voor meerdere apparaten of afzonderlijke taken binnen een werk stroom te schrijven als werk stromen. Met de Windows Power shell-werk stroom kunt u Power shell-scripts en XAML-bestanden aanpassen en uitvoeren als werk stromen. |
