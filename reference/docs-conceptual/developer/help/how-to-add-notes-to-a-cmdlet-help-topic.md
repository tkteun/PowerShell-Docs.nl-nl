---
title: Opmerkingen toevoegen aan een Help-onderwerp over cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353310"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Notities toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een sectie notities kunt toevoegen aan het Help-onderwerp van een Windows Power shell®-cmdlet. De sectie Notities wordt gebruikt om de details te verklaren die niet eenvoudig in de andere gestructureerde secties passen, zoals een gedetailleerdere uitleg van een para meter. Deze inhoud kan ook opmerkingen bevatten over de werking van de cmdlet met een specifieke provider, een unieke, nog belang rijke, gebruiks vorm van de cmdlet of manieren om mogelijke fout situaties te voor komen.

Er zijn geen beperkingen voor het aantal notities dat u kunt toevoegen aan een sectie Notities. Voeg voor elke notitie een paar \<maml: alarm > Tags toe aan het knoop punt \<maml: > alertset. De inhoud van elke notitie wordt toegevoegd in een set \<maml: para codes >. Gebruik blank \<maml: para > Tags voor afstand.

Het volgende XML-bestand bevat een \<maml: waarschuwingsset > knoop punt met twee notities. U ziet dat elke notitie een optionele \<maml: title > tag (titels kan worden gebruikt om een wille keurige set van \<maml: alert > Tags te groeperen) en dat elke notitie een lege regel heeft na de inhoud voor afstand.

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```


