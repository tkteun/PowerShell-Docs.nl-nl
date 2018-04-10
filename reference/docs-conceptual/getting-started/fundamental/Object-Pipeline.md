---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Objectpijplijn
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 6102ec6e8fbf38fdc2bc5fa9c583244ef639dec8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="object-pipeline"></a>Objectpijplijn
Pijplijnen fungeren als een reeks verbonden segmenten van de pipe. Items verplaatst langs de pijplijn is doorlaten van elk segment. Voor het maken van een pijplijn in Windows PowerShell, u verbinding maakt opdrachten samen met de pipe-operator ' | '. De uitvoer van elke opdracht wordt gebruikt als invoer voor de volgende opdracht.

Pijplijnen zijn weliswaar het meest waardevolle concept gebruikt in opdrachtregelinterfaces. Juist gebruik, pijplijnen niet alleen minder moeite hoeven die zijn betrokken bij het invoeren van complexe opdrachten, maar ook gemakkelijker om te zien van de werkstroom in de opdrachten. Een gerelateerde nuttig kenmerk van pijplijnen is of omdat deze afzonderlijk op elk item werken, er geen wijzigen op basis van of u nul, een of veel items in de pijplijn moet. Bovendien elke opdracht in een pijplijn (een pipeline-element genoemd) wordt de uitvoer meestal doorgegeven aan de volgende opdracht in de pipeline-per-item. Dit meestal vermindert de behoefte aan bronnen van complexe opdrachten en kunt u beginnen onmiddellijk ophalen van de uitvoer.

In dit hoofdstuk we beschrijven hoe de Windows PowerShell-pijplijn verschilt van de pijplijnen van de meest populaire houders en vervolgens demonstreren sommige hulpmiddelen die u gebruiken kunt bij het besturingselement pijplijn uitvoer en om te zien hoe de pijplijn werkt.