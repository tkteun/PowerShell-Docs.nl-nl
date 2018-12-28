---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Overzicht Desired State Configuration voor besluitvormers
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403952"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Overzicht Desired State Configuration voor besluitvormers

Dit document beschrijft de zakelijke voordelen van het gebruik van Windows PowerShell Desired State Configuration (DSC). Het is niet een technische handleiding.

## <a name="what-is-desired-state-configuration"></a>Wat Is er Desired State Configuration?

PowerShell Desired State Configuration is een beheerplatform voor de configuratie die is ingebouwd in Windows die is gebaseerd op open standaarden. DSC is flexibel genoeg om betrouwbare en consistente manier werken in elke fase van de levenscyclus van de implementatie (ontwikkeling, testen, Pre-productie, productie), en tijdens de scale-out.

DSC draait om [configuraties](../configurations/configurations.md).
Een configuratie is een gemakkelijk leesbare-document met een beschrijving van een omgeving die bestaan uit computers ("knooppunten") met specifieke kenmerken.
Deze kenmerken kunnen worden net zo eenvoudig als u ervoor te zorgen dat een specifieke Windows-functie is ingeschakeld of een stuk complexer is zoals het implementeren van SharePoint.

DSC heeft ook bewaking en rapportage ingebouwd.
Als een systeem niet meer compatibel zijn is, kan DSC waarschuwen en Neem maatregelen om te corrigeren van het systeem.

## <a name="benefits-of-using-desired-state-configuration"></a>Voordelen van het gebruik van Desired State Configuration

Configuraties zijn ontworpen om gemakkelijk lezen, die zijn opgeslagen en bijgewerkt.
Configuraties declareren dat de doelapparaten status moeten zich in, in plaats van het schrijven van instructies voor het plaatsen die status hebben.
Hierdoor kunt u veel minder kostbaar zijn om te leren, vast, implementeren en onderhouden van de configuratie met behulp van DSC.

Het maken van configuraties betekent dat complexe implementatiestappen worden vastgelegd als een 'één betrouwbare bron' op één locatie.
Hierdoor kunt u herhaalde implementaties van een specifieke set computers veel minder gevoelig voor fouten.
Op zijn beurt, waardoor implementaties sneller en betrouwbaarder waardoor een snelle doorlooptijd op complexe implementaties.

Er zijn ook configuraties deelbaar via de [PowerShell Gallery](https://powershellgallery.com) wat betekent dat algemene scenario's en aanbevolen procedures bestaat mogelijk al voor het werk dat moet worden uitgevoerd.


## <a name="desired-state-configuration-and-devops"></a>Desired State Configuration en DevOps

DSC is ontworpen met [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) Denk eraan dat u een combinatie van mensen, processen en hulpprogramma's die voor snelle implementatie en herhalen zeer zorgen gericht op het leveren van een waarde voor eindgebruikers, intern of extern.
Met een configuratie voor één definiëren van een omgeving betekent dat ontwikkelaars kunnen hun vereisten in een configuratie met coderen, controleert u dat de configuratie in broncodebeheer en bewerking teams kan de implementatie eenvoudig code zonder te hoeven doorlopen gevoelig voor fouten handmatige processen.

Firewallconfiguraties zijn ook [gegevensgestuurde](../configurations/configData.md), waardoor het gemakkelijker voor ops om te bepalen en omgevingen zonder tussenkomst van ontwikkelaars te wijzigen.

## <a name="desired-state-configuration-on-premises-and-off-premises"></a>On-Premises en buiten het bedrijf Desired State Configuration
DSC kan worden gebruikt voor het beheren van zowel on-premises en off-premises implementaties.
Voor on-premises oplossingen, DSC heeft een [pull-server](../pull-server/pullServer.md) die kunnen worden gebruikt voor centraliseer het beheer van computers en rapporteren van hun status.
Voor cloudoplossingen kan DSC worden gebruikt waar Windows kan worden gebruikt.
Er zijn ook speciale aanbiedingen van Azure is gebouwd op Desired State Configuration, zoals [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), die centraliseert rapportage van DSC.

## <a name="dsc-and-compatibility"></a>DSC en compatibiliteit

DSC werd geïntroduceerd in Windows Server 2012 R2, is het beschikbaar voor eerdere besturingssystemen via het pakket voor Windows Management Framework (WMF).
Meer informatie over de WMF vindt u op de [PowerShell startpagina](/powershell/).

DSC kan ook worden gebruikt voor het beheren van Linux. Zie voor meer informatie, [aan de slag met DSC voor Linux](../getting-started/lnxGettingStarted.md).
