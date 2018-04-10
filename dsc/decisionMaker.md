---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Overzicht Desired State Configuration voor besluitvormers
ms.openlocfilehash: 8b410420ef30b066a32864a0d08a12a8485eaa4b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Overzicht Desired State Configuration voor besluitvormers

Dit document beschrijft de zakelijke voordelen van het gebruik van PowerShell Desired State Configuration (DSC). Het is niet een technische handleiding.

## <a name="what-is-desired-state-configuration"></a>Wat Is er Desired State Configuration?

Windows PowerShell Desired State Configuration (DSC) is een platform voor het beheer van configuratie ingebouwd in Windows die is gebaseerd op open standaarden. DSC is flexibel genoeg betrouwbare en consistente manier werken in elke fase van de levenscyclus van de implementatie (ontwikkeling, test, vóór productie-, productie), evenals tijdens scale-out.

DSC draait om '[configuraties](https://msdn.microsoft.com/powershell/dsc/configurations)'.
Een configuratie is een eenvoudig te lezen-document met een beschrijving van een omgeving die bestaan uit computers ("knooppunten") met specifieke kenmerken.
Deze kenmerken kunnen worden net zo eenvoudig als het een specifieke Windows-functie is ingeschakeld of zoals het implementeren van SharePoint gezorgd.

DSC heeft ook bewaking en rapportage ingebouwd.
Als een systeem niet meer compatibel is, kan de DSC waarschuwing activeren en fungeren als u wilt corrigeren, het systeem.

## <a name="benefits-of-using-desired-state-configuration"></a>Voordelen van het gebruik van Desired State Configuration

Configuraties zijn ontworpen om gemakkelijk lezen, opgeslagen en bijgewerkt.
Configuraties declareren dat doelapparaten status moet, in plaats van de instructies voor het plaatsen die status schrijven.
Hierdoor kunt u veel minder dure meer, vaststellen, implementeren en onderhouden van de configuratie met behulp van DSC.

Configuraties maakt, complexe implementatiestappen worden vastgelegd als een 'één bron van waarheid' op één locatie.
Hierdoor kunt u herhaalde implementaties van een specifieke set machines veel minder gevoelig voor fouten.
Op zijn beurt dankzij implementaties sneller en betrouwbaarder waardoor een snelle reactietijd ook op complexe implementaties.

Configuraties zijn ook deelbaar via de [PowerShell Gallery](https://powershellgallery.com) wat betekent dat algemene scenario's en best practices bestaat wellicht al voor de taken die u moet doen.


## <a name="desired-state-configuration-and-devops"></a>Desired State Configuration en DevOps

[DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) is een combinatie van mensen, verwerken en hulpprogramma's waarmee voor snelle implementatie en herhaling gericht op de waarde voor eindgebruikers intern of extern.
DSC is ontworpen met DevOps in gedachten.
Een omgeving met een configuratie voor één definiëren betekent dat ontwikkelaars kunt coderen van de vereisten in een configuratie, controleert u dat de configuratie in broncodebeheer en bewerkingen teams code eenvoudig implementeren kunnen zonder te hoeven te doorlopen gevoelig voor fouten handmatige processen.

Configuraties zijn ook [gegevensgestuurde](https://msdn.microsoft.com/powershell/dsc/configdata), waardoor het gemakkelijker voor ops-teams te identificeren en te wijzigen omgevingen zonder tussenkomst van de ontwikkelaar.

## <a name="desired-state-configuration-on--and-off-premises"></a>Desired State Configuration op - en niet op locatie

DSC kan worden gebruikt voor het beheren van zowel on-premises en niet-lokale implementaties.
Voor oplossingen voor on-premises DSC heeft een [pull-server](https://msdn.microsoft.com/powershell/dsc/pullserver) kunnen worden gebruikt voor het beheer van machines centraliseren en rapporteren over hun status.
Voor cloudoplossingen, DSC kan worden gebruikt waar Windows kan worden gebruikt.
Er zijn ook speciale aanbiedingen van Azure die zijn gebouwd op Desired State Configuration, zoals [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), die centraliseert het melden van DSC.

## <a name="dsc-and-compatibility"></a>Compatibiliteit en DSC

Hoewel DSC is geïntroduceerd in Windows Server 2012 R2, is beschikbaar voor downlevel-besturingssystemen via het pakket voor Windows Management Framework (WMF).
Meer informatie over de WMF vindt u op de [PowerShell startpagina](https://msdn.microsoft.com/en-us/powershell/).

DSC kan ook worden gebruikt voor het beheren van Linux. Zie voor meer informatie [aan de slag met DSC voor Linux](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted).