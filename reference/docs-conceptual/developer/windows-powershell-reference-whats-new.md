---
ms.date: 09/13/2016
ms.topic: reference
title: Naslag informatie voor Windows Power shell-What's New
description: Naslag informatie voor Windows Power shell-What's New
ms.openlocfilehash: b6fa97eacd476f055dd0c69eed2e547c450b85e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647117"
---
# <a name="whats-new"></a>Nieuwe functies

Windows Power Shell 2,0 biedt de volgende nieuwe functies die u kunt gebruiken bij het schrijven van cmdlets, providers en hosttoepassingen.

## <a name="modules"></a>Modules

U kunt nu Windows Power shell-oplossingen verpakken en distribueren met behulp van modules. Met beschik bare modules kunt u uw Windows Power shell-code partitioneren, ordenen en samen stellen in op zichzelf staande, herbruikbare eenheden. Zie een Windows Power shell-module schrijven voor meer informatie over modules.

## <a name="the-powershell-class"></a>De Power shell-klasse

De Power shell-klasse biedt een eenvoudiger oplossing voor het maken van toepassingen, aangeduid als hosttoepassingen, die programmatisch opdrachten uitvoeren. Met deze klasse kunt u een pijp lijn met opdrachten maken, de runs Pace opgeven die wordt gebruikt voor het uitvoeren van de opdrachten en opgeven dat de opdrachten synchroon of asynchroon worden aangeroepen.

## <a name="the-runspacepool-class"></a>De RunspacePool-klasse

Met runs Pace-groepen kunt u meerdere runspaces maken met behulp van één aanroep. De methode CreateRunspacePool biedt verschillende Overloads die kunnen worden gebruikt voor het maken van runspaces met dezelfde functies, zoals dezelfde host, de oorspronkelijke sessie status en verbindings gegevens.

## <a name="the-initialsessionstate-class"></a>De InitialSessionState-klasse

Met de InitialSessionState-klasse kunt u een sessie status configuratie maken die wordt gebruikt wanneer een runs Pace wordt geopend. U kunt een aangepaste configuratie maken, een standaard configuratie die de opdrachten bevat die worden geleverd door mshshort, en een configuratie waarvan de opdrachten worden beperkt op basis van de mogelijkheden van de sessie.

## <a name="remote-runspaces"></a>Externe runspaces

U kunt nu runspaces maken die kunnen worden geopend op externe computers, zodat u opdrachten kunt uitvoeren op de externe computer en de resultaten lokaal moet verzamelen. Als u een externe runs Pace wilt maken, moet u informatie over de externe verbinding opgeven tijdens het maken van de runs Pace. Zie de methoden CreateRunspace en CreateRunspacePool voor voor beelden. De verbindings gegevens worden gedefinieerd door de RunspaceConnectionInfo-klasse.

## <a name="private-runspace-elements"></a>Persoonlijke runs Pace-elementen

U kunt nu runspaces maken waarvan de elementen openbaar of privé zijn. Zo kunt u runspaces maken waarvan de elementen beschikbaar zijn voor de runs Pace, maar niet beschikbaar zijn voor de gebruiker. Zie de ConstrainedSessionStateEntry-klasse om erachter te komen welke elementen van de runs Pace persoonlijk kunnen worden gemaakt.

## <a name="runspace-threading-modes-and-apartment-state"></a>Runs Pace-threading modi en Apartment-status

U kunt nu opgeven hoe threads worden gemaakt en gebruikt voor het uitvoeren van opdrachten in een runs Pace. Zie de eigenschappen System. Management. Automation. Runspaces. runs. ThreadOptions en System. Management. Automation. Runspaces. RunspacePool. ThreadOptions.

U kunt nu de status van de Apartment ophalen van de threads die worden gebruikt voor het uitvoeren van opdrachten in een runs Pace. Zie de eigenschappen System. Management. Automation. Runspaces. runs. ApartmentState en System. Management. Automation. Runspaces. RunspacePool. ApartmentState.

## <a name="transaction-cmdlets"></a>Trans actie-cmdlets

U kunt nu cmdlets maken die kunnen worden gebruikt binnen een trans actie. Wanneer een cmdlet wordt gebruikt in een trans actie, zijn de acties tijdelijk en kunnen ze worden geaccepteerd of geweigerd door de trans actie-cmdlets van Windows Power shell.

Zie trans acties ondersteunen voor meer informatie over trans acties.

## <a name="transaction-provider"></a>Transactie provider

U kunt nu providers maken die kunnen worden gebruikt binnen een trans actie. Net als bij cmdlets, wanneer een provider wordt gebruikt in een trans actie, zijn de acties tijdelijk en kunnen ze worden geaccepteerd of geweigerd door de trans actie-cmdlets van Windows Power shell.

Voor meer informatie over het opgeven van ondersteuning voor trans acties binnen een provider klasse, zie de eigenschap System. Management. Automation. provider. CmdletProviderAttribute. ProviderCapabilities.

## <a name="job-cmdlets"></a>Taak-cmdlets

U kunt nu cmdlets schrijven waarmee de actie kan worden uitgevoerd als een taak. Deze taken worden op de achtergrond uitgevoerd zonder interactie met de huidige sessie. Zie achtergrond taken voor meer informatie over hoe Windows Power shell taken ondersteunt.

## <a name="cmdlet-output-types"></a>Uitvoer typen van de cmdlet

U kunt nu de .NET Framework typen opgeven die door de cmdlets worden geretourneerd door het kenmerk output type te declareren bij het schrijven van uw cmdlets. Op deze wijze kunnen anderen bepalen welk type objecten er door een cmdlet worden geretourneerd door te kijken naar de waarde voor het kenmerk output van de cmdlet.

## <a name="event-support"></a>Gebeurtenis ondersteuning

U kunt nu cmdlets schrijven waarmee gebeurtenissen worden toegevoegd en gebruikt. Zie de PSEvent-klasse.

## <a name="proxy-commands"></a>Proxy opdrachten

U kunt nu proxy opdrachten schrijven die kunnen worden gebruikt om een andere opdracht uit te voeren. Met een proxy opdracht kunt u bepalen welke functionaliteit van de bron-cmdlet beschikbaar is voor de gebruiker. U kunt bijvoorbeeld een proxy opdracht maken die een para meter verwijdert die wordt geleverd door de bron opdracht. Zie de ProxyCommand-klasse.

## <a name="multiple-choice-prompts"></a>Meerdere keuze prompts

U kunt nu toepassingen schrijven die de gebruiker in staat stelt om meerdere keuzes te selecteren. De IHostUISupportsMultipleChoiceSelection-interface weer geven

## <a name="interactive-sessions"></a>Interactieve sessies

U kunt nu toepassingen schrijven waarmee een interactieve sessie op een externe computer kan worden gestart en gestopt.
Zie de IHostSupportsInteractiveSession-interface.

## <a name="custom-cmdlet-help-for-providers"></a>Help voor aangepaste cmdlets voor providers

U kunt nu aangepaste Help-onderwerpen maken voor de provider-cmdlets. In de Help-onderwerpen voor aangepaste cmdlets kunt u uitleggen hoe de cmdlet werkt in het pad van de provider en de speciale functies van het document, inclusief de dynamische para meters die de provider toevoegt aan de cmdlet.
