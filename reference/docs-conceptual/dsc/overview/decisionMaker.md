---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Overzicht Desired State Configuration voor besluitvormers
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941759"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Overzicht Desired State Configuration voor besluitvormers

Dit document beschrijft de zakelijke voor delen van het gebruik van Windows Power shell desired state Configuration (DSC). Het is geen technische hand leiding.

## <a name="what-is-desired-state-configuration"></a>Wat is desired state Configuration?

De gewenste status configuratie van Power shell is een configuratie beheersysteem dat is ingebouwd in Windows dat is gebaseerd op open standaarden. DSC is flexibel genoeg om betrouwbaar en consistent te functioneren in elke fase van de levens cyclus van de implementatie (ontwikkeling, test, pre-productie, productie), evenals tijdens het uitschalen.

DSC Centers rondom [configuraties](../configurations/configurations.md).
Een configuratie is een gemakkelijk te lezen document met een beschrijving van een omgeving die bestaat uit computers (knoop punten) met specifieke kenmerken.
Deze kenmerken kunnen zo eenvoudig zijn dat een specifieke Windows-functie wordt ingeschakeld of zo complex is als bij het implementeren van share point.

DSC heeft ook ingebouwde bewaking en rapportage.
Als een systeem niet meer voldoet aan het beleid, kan DSC een waarschuwing genereren en het systeem verwerken.

## <a name="benefits-of-using-desired-state-configuration"></a>Voor delen van het gebruik van desired state Configuration

Configuraties zijn zodanig ontworpen dat ze gemakkelijk kunnen worden gelezen, opgeslagen en bijgewerkt.
Configuraties geven aan dat de doel apparaten van de status moeten zijn in in plaats van instructies te schrijven voor het plaatsen van deze in die staat.
Dit maakt het veel minder kost om de configuratie via DSC te leren, aan te passen, te implementeren en te onderhouden.

Het maken van configuraties houdt in dat complexe implementaties tappen worden vastgelegd als een ' enkele bron van waarheid ' op één locatie.
Dit maakt het herhaalde implementaties van een specifieke set machines veel minder fout gevoelig.
Zo maakt u implementaties sneller en betrouwbaarder, waardoor u snel complexe implementaties kunt uitvoeren.

Configuraties kunnen ook worden gedeeld via de [PowerShell Gallery](https://powershellgallery.com) betekenis van veelvoorkomende scenario's en aanbevolen procedures zijn mogelijk al aanwezig voor het werk dat moet worden uitgevoerd.


## <a name="desired-state-configuration-and-devops"></a>Desired state Configuration en DevOps

DSC is ontworpen met het oog op [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) , een combi natie van personen, processen en hulpprogram ma's waarmee snelle implementatie en iteratie kan worden gericht op het leveren van waarde aan eind gebruikers, ongeacht of deze intern of extern zijn.
Met één configuratie definieert u een omgeving dat ontwikkel aars hun vereisten kunnen coderen in een configuratie, de configuratie controleren in broncode beheer, en operationele teams kunnen eenvoudig code implementeren zonder dat ze de fout gevoelig hoeven te door lopen hand matige processen.

Configuraties worden ook [gegevensgestuurd](../configurations/configData.md), waardoor het voor OPS gemakkelijker is om omgevingen te identificeren en te wijzigen zonder tussen komst van een ontwikkelaar.

## <a name="desired-state-configuration-on-premises-and-off-premises"></a>Configuratie van de gewenste status on-premises en off-premises
DSC kan worden gebruikt voor het beheren van zowel on-premises als lokale implementaties.
Voor on-premises oplossingen heeft DSC een [Pull-server](../pull-server/pullServer.md) die kan worden gebruikt om het beheer van machines te centraliseren en te rapporteren over hun status.
Voor cloud oplossingen is DSC bruikbaar wanneer Windows kan worden gebruikt.
Er zijn ook specifieke aanbiedingen van Azure op basis van de gewenste status configuratie, zoals [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), die de rapportage van DSC centraliseren.

## <a name="dsc-and-compatibility"></a>DSC en compatibiliteit

Hoewel DSC is geïntroduceerd in Windows Server 2012 R2, is het beschikbaar voor besturings systemen van lagere niveaus via het Windows Management Framework (WMF)-pakket.
Meer informatie over de WMF vindt u op de [Power shell-start pagina](/powershell/).

DSC kan ook worden gebruikt voor het beheren van Linux. Zie [aan de slag met DSC voor Linux](../getting-started/lnxGettingStarted.md)voor meer informatie.
