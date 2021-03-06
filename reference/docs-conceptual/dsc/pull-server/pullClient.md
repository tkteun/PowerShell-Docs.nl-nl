---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een DSC-pull-client instellen
description: Dit artikel bevat een overzicht van de informatie die beschikbaar is voor het instellen van de DSC pull-client.
ms.openlocfilehash: 584af3aee46d801e363422ae7a197348231a1442
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646814"
---
# <a name="setting-up-a-dsc-pull-client"></a>Een DSC-pull-client instellen

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

> [!IMPORTANT]
> De pull-server (Windows *-functie DSC-service* ) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden. Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.

Elk doel knooppunt moet worden weer gegeven om de pull-modus te gebruiken en de URL of de bestands locatie op te geven waar het een verbinding kan maken met de pull-server voor het ophalen van configuraties en resources, en waar de rapport gegevens moeten worden verzonden.

In de volgende onderwerpen wordt uitgelegd hoe u pull-clients instelt:

- [Een pull-client instellen met behulp van configuratie namen](pullClientConfigNames.md) 
*- [Een pull-client instellen met behulp van de configuratie-ID](pullClientConfigID.md)

> [!NOTE]
> Deze onderwerpen zijn van toepassing op Power shell 5,0. Zie [een pull-client instellen met behulp van de configuratie-ID in Power shell 4,0](pullClientConfigID4.md)voor het instellen van een pull-client in power Shell 4,0.
