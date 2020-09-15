---
title: Notities toevoegen aan een Help-onderwerp voor cmdlets
ms.date: 09/12/2016
ms.openlocfilehash: d3679126ea34d7e86bcda700d0d050d8312a7aa2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893404"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Notities toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een sectie **notities** kunt toevoegen aan het Help-onderwerp van een Power shell-cmdlet. De sectie **notities** wordt gebruikt om de details te verklaren die niet eenvoudig in de andere gestructureerde secties passen, zoals een gedetailleerdere uitleg van een para meter. Deze inhoud kan ook opmerkingen bevatten over de werking van de cmdlet met een specifieke provider, een unieke, nog belang rijke, gebruiks vorm van de cmdlet of manieren om mogelijke fout situaties te voor komen.

Er zijn geen beperkingen voor het aantal notities dat u kunt toevoegen aan een sectie Notities. Voeg voor elke notitie een paar tags toe `<maml:alert>` aan het `<maml:alertset>` knoop punt. De inhoud van elke notitie wordt toegevoegd binnen een set met `<maml:para>` Tags. Lege `<maml:para>` labels gebruiken voor afstand.

De volgende XML-code bevat een `<maml:alertset>` knoop punt met twee notities. U ziet dat elke notitie een optionele `<maml:title>` tag heeft (titels kunnen worden gebruikt voor het groeperen van een wille keurige set `<maml:alert>` Tags) en dat elke notitie een lege regel heeft na de inhoud voor afstand.

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
