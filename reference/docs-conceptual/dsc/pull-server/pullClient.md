---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een DSC-pull-client instellen
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942795"
---
# <a name="setting-up-a-dsc-pull-client"></a>Een DSC-pull-client instellen

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

> [!IMPORTANT]
> De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden. Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.

Elk doel knooppunt moet worden weer gegeven om de pull-modus te gebruiken en de URL of de bestands locatie op te geven waar het een verbinding kan maken met de pull-server voor het ophalen van configuraties en resources, en waar de rapport gegevens moeten worden verzonden.

In de volgende onderwerpen wordt uitgelegd hoe u pull-clients instelt:

* [Een pull-client instellen met behulp van configuratienamen](pullClientConfigNames.md)
* [Een pull-client instellen met behulp van het configuratie-id](pullClientConfigID.md)

> [!NOTE]
> Deze onderwerpen zijn van toepassing op Power shell 5,0. Zie [een pull-client instellen met behulp van de configuratie-ID in Power shell 4,0](pullClientConfigID4.md)voor het instellen van een pull-client in power Shell 4,0.