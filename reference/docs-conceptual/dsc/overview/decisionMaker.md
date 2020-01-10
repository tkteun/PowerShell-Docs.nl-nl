---
ms.date: 10/11/2019
keywords: DSC, Power shell, configuratie, installatie
title: Overzicht Desired State Configuration voor besluitvormers
ms.openlocfilehash: b6d483d105c2d3b9be7215be36397d452338c7f1
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737250"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Overzicht van desired state Configuration voor besluit vormers

Dit document beschrijft de zakelijke voor delen van het gebruik van Power shell desired state Configuration (DSC) en is geen technische hand leiding.

## <a name="what-is-dsc"></a>Wat is DSC?

Power shell DSC is een configuratie beheersysteem dat is ingebouwd in Windows en dat is gebaseerd op open standaarden. DSC is flexibel genoeg om betrouwbaar en consistent te functioneren in elke fase van de levens cyclus van de implementatie (ontwikkeling, test, pre-productie, productie) en tijdens het uitschalen.

DSC Centers rondom [configuraties](../configurations/configurations.md). Een configuratie is een Power shell-script dat een omgeving beschrijft die bestaat uit computers, of knoop punten, met specifieke kenmerken. Deze kenmerken kunnen zo eenvoudig zijn dat een specifieke Windows-functie wordt ingeschakeld of zo complex is als bij het implementeren van share point.

DSC heeft ingebouwde bewaking en rapportage. Als een systeem niet meer voldoet aan het beleid, kan DSC een waarschuwing genereren en het systeem verwerken.

## <a name="benefits-of-using-dsc"></a>Voor delen van het gebruik van DSC

Het ontwerp van de configuratie vereenvoudigt de manier waarop ze worden gelezen, opgeslagen en bijgewerkt. Configuraties declareren de status van doel apparaten in plaats van instructies te schrijven voor het plaatsen van apparaten in die staat. Deze factoren verlagen de kosten voor het leren, aannemen, implementeren en onderhouden van configuratie via DSC.

Het maken van configuraties houdt in dat complexe implementaties tappen als **één bron van waarheid** op één locatie worden vastgelegd. Configuraties maken herhaalde implementaties van een specifieke set computers minder fout gevoelig. En de implementaties zijn sneller en betrouwbaarder, waardoor u snel complexe implementaties kunt uitvoeren.

Configuraties kunnen worden gedeeld via de [PowerShell Gallery](https://powershellgallery.com). Het is mogelijk dat veelvoorkomende scenario's en aanbevolen procedures al bestaan voor het werk dat u moet doen.

## <a name="dsc-and-devops"></a>DSC en DevOps

DSC is ontworpen met het oog op [DevOps](/archive/blogs/ashleymcglone/devops-for-n00bs-ie-windows-people-like-me) . Een combi natie van personen, processen en hulpprogram ma's waarmee een snelle implementatie en iteratie kan worden gericht op het leveren van waarde aan eind gebruikers, ongeacht of deze intern of extern zijn. Een configuratie die een omgeving definieert, houdt in dat ontwikkel aars hun vereisten kunnen coderen in een configuratie en controleren of de configuratie broncode beheer is. Operations-teams kunnen vervolgens code implementeren zonder de fout gevoelige hand matige processen te door lopen.

Configuraties worden [gegevensgestuurd](../configurations/configData.md). De gedefinieerde gegevens maken het gemakkelijker voor bewerkingen om omgevingen te identificeren en te wijzigen zonder tussen komst van de ontwikkelaar.

## <a name="dsc-on-premises-and-off-premises"></a>DSC on-premises en off-premises

DSC kan on-premises en off-premises implementaties beheren. Voor on-premises oplossingen heeft DSC een [Pull-server](../pull-server/pullServer.md) die wordt gebruikt om het beheer van machines te centraliseren en te rapporteren over hun status. Voor on-premises cloud oplossingen kan DSC op elke plek waar Windows wordt gebruikt, worden gebruikt.
Er zijn specifieke aanbiedingen van Azure gebaseerd op DSC, zoals [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), die DSC-rapportage centraliseren.

## <a name="dsc-and-compatibility"></a>DSC en compatibiliteit

DSC is geïntroduceerd in Windows Server 2012 R2, maar is ook beschikbaar voor besturings systemen van lagere niveaus via het Windows Management Framework (WMF). Zie [Windows Management Framework](/powershell/scripting/wmf/overview)voor meer informatie over WMF.

DSC kan worden gebruikt om Linux te beheren. Zie [aan de slag met DSC voor Linux](../getting-started/lnxGettingStarted.md)voor meer informatie.
