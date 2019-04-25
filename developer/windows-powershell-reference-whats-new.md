---
title: Windows PowerShell-referentie - wat is er nieuw
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080523"
---
# <a name="whats-new"></a>Wat is nieuw

Windows PowerShell 2.0 biedt de volgende nieuwe functies voor gebruik bij het schrijven van cmdlets en providers hosting van toepassingen.

## <a name="modules"></a>Modules

U kunt nu Inpakken en distribueren van Windows PowerShell-oplossingen met behulp van modules. Modules kunnen u de partitie, organiseren en uw Windows PowerShell-code in zelfstandige, herbruikbare eenheden abstract. Zie voor meer informatie over modules, een Windows PowerShell-Module schrijven.

## <a name="the-powershell-class"></a>De PowerShell-klasse

De PowerShell-klasse biedt een eenvoudigere oplossing voor het maken van toepassingen, aangeduid als hosttoepassingen, die opdrachten via een programma uitvoeren. Deze klasse kunt u een pijplijn van opdrachten, geven de runspace die wordt gebruikt voor het uitvoeren van de opdrachten en geef de opdrachten aanroepen synchroon of asynchroon.

## <a name="the-runspacepool-class"></a>De klasse RunspacePool

Runspace pools kunnen u meerdere runspaces maken met behulp van één aanroep. De methode CreateRunspacePool biedt verschillende overloads die kunnen worden gebruikt voor het maken van runspaces waarvoor de dezelfde functies, zoals de dezelfde host, de status van de eerste sessie en de verbindingsgegevens.

## <a name="the-initialsessionstate-class"></a>De klasse InitialSessionState

De klasse InitialSessionState kunt u maken van een sessieconfiguratie van de status die wordt gebruikt wanneer een runspace wordt geopend. U kunt een aangepaste configuratie, een standaard-configuratie met de opdrachten van mshshort en een configuratie waarvan u de opdrachten beperkt op basis van de mogelijkheden van de sessie zijn maken.

## <a name="remote-runspaces"></a>Externe runspaces

U kunt runspaces die kunnen worden geopend nu maken op externe computers, zodat u opdrachten uitvoeren op de externe computer en de resultaten lokaal verzamelen. Voor het maken van een externe runspace, moet u informatie over de externe verbinding opgeven bij het maken van de runspace. Zie de methoden CreateRunspace en CreateRunspacePool voor voorbeelden. Gegevens voor de verbinding wordt gedefinieerd door de klasse RunspaceConnectionInfo.

## <a name="private-runspace-elements"></a>Persoonlijke runspace elementen

U kunt nu runspaces waarvan de elementen openbaar of privé zijn maken. Hiermee kunt u runspaces waarvan de elementen beschikbaar zijn voor de runspace, maar zijn niet beschikbaar voor de gebruiker te maken. Raadpleeg de klasse ConstrainedSessionStateEntry om erachter te komen welke elementen van de runspace persoonlijk kunnen worden gemaakt.

## <a name="runspace-threading-modes-and-apartment-state"></a>Runspace threading modi en apartmentstatus

U kunt nu hoe threads worden gemaakt en die wordt gebruikt bij het uitvoeren van opdrachten in een runspace opgeven. Zie de System.Management.Automation.Runspaces.Runspace.ThreadOptions en System.Management.Automation.Runspaces.RunspacePool.ThreadOptions-eigenschappen.

U kunt nu de apartmentstatus van het aantal threads die worden gebruikt voor het uitvoeren van opdrachten in een runspace krijgen. Zie de System.Management.Automation.Runspaces.Runspace.ApartmentState en System.Management.Automation.Runspaces.RunspacePool.ApartmentState-eigenschappen.

## <a name="transaction-cmdlets"></a>Transactie-cmdlets

U kunt nu cmdlets die kunnen worden gebruikt binnen een transactie maken. Wanneer een cmdlet wordt gebruikt in een transactie, de acties zijn tijdelijk en ze kunnen worden geaccepteerd of geweigerd door de beschikbare Windows PowerShell cmdlets voor de transactie.

Zie voor meer informatie over transacties, hoe u ondersteuning voor transacties.

## <a name="transaction-provider"></a>Transactie-provider

U kunt nu providers die kunnen worden gebruikt binnen een transactie maken. Net als bij cmdlets, wanneer een provider wordt gebruikt in een transactie, de acties zijn tijdelijk en ze kunnen worden geaccepteerd of geweigerd door de beschikbare Windows PowerShell cmdlets voor de transactie.

Zie voor meer informatie over het opgeven van ondersteuning voor de transactie in de providerklasse van een van de eigenschap System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities.

## <a name="job-cmdlets"></a>Taak-cmdlets

U kunt nu schrijven-cmdlets die de actie als wanneer u een taak kunt uitvoeren. Deze taken worden uitgevoerd op de achtergrond zonder interactie met de huidige sessie. Zie voor meer informatie over hoe taken ondersteuning biedt voor Windows PowerShell, achtergrondtaken.

## <a name="cmdlet-output-types"></a>Uitvoertypen voor cmdlet

Nu kunt u de .NET Framework-typen die zijn geretourneerd door uw cmdlets door op te geven van het kenmerk OutputType bij het schrijven van uw cmdlets. Hierdoor kunnen andere gebruikers om te bepalen welk type objecten worden geretourneerd door een cmdlet, door te kijken naar de eigenschap OutputType van de cmdlet.

## <a name="event-support"></a>Gebeurtenisondersteuning

U kunt nu cmdlets die toevoegen en gebruiken van gebeurtenissen schrijven. Raadpleeg de PSEvent-klasse.

## <a name="proxy-commands"></a>Proxy-opdrachten

U kunt nu proxy-opdrachten die kunnen worden gebruikt om uit te voeren van een andere opdracht schrijven. Een proxy-opdracht kunt u bepalen welke functionaliteit van de bron-cmdlet is beschikbaar voor de gebruiker. Bijvoorbeeld, kunt u een proxy-opdracht die een parameter die wordt geleverd door de opdracht bron verwijdert. Raadpleeg de ProxyCommand-klasse.

## <a name="multiple-choice-prompts"></a>Meerdere keuze prompts

U kunt nu toepassingen schrijven waarmee krijgt u aanwijzingen waarmee de gebruiker meerdere opties selecteren. Zie de IHostUISupportsMultipleChoiceSelection-interface

## <a name="interactive-sessions"></a>Interactieve sessies

U kunt nu toepassingen schrijven waarmee kunnen starten en stoppen van een interactieve sessie op een externe computer.
Zie de IHostSupportsInteractiveSession-interface.

## <a name="custom-cmdlet-help-for-providers"></a>Aangepaste Cmdlet Help voor Providers

Nu kunt u aangepaste Help-onderwerpen voor de provider-cmdlets. Aangepaste cmdlet help-onderwerpen kunt uitleggen hoe de cmdlet werkt in de provider pad en de document speciale functies, met inbegrip van de dynamische parameters die door de provider worden toegevoegd aan de cmdlet.
