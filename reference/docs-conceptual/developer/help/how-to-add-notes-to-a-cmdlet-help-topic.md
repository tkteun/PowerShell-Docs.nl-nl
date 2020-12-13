---
ms.date: 10/20/2020
ms.topic: reference
title: Notities toevoegen aan een Help-onderwerp voor cmdlets
description: Notities toevoegen aan een Help-onderwerp voor cmdlets
ms.openlocfilehash: 61363c26ab0172277d1332ed1e9de080d8da200c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659560"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Notities toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een sectie **notities** kunt toevoegen aan het Help-onderwerp van een Power shell-cmdlet. De sectie **notities** wordt gebruikt om de details te verklaren die niet eenvoudig in de andere gestructureerde secties passen, zoals een gedetailleerdere uitleg van een para meter. Deze inhoud kan ook opmerkingen bevatten over de werking van de cmdlet met een specifieke provider, een unieke, nog belang rijke, gebruiks vorm van de cmdlet of manieren om mogelijke fout situaties te voor komen.

De sectie **notities** is gedefinieerd met behulp van één `<maml:alertset>` knoop punt. Er zijn geen beperkingen voor het aantal notities dat u kunt toevoegen aan een sectie Notities. Voeg voor elke notitie een paar tags toe `<maml:alert>` aan het `<maml:alertset>` knoop punt. De inhoud van elke notitie wordt toegevoegd binnen een set met `<maml:para>` Tags. Lege `<maml:para>` labels gebruiken voor afstand.

```xml
<maml:alertSet>
  <maml:title>Optional title for Note</maml:title>
  <maml:alert>
    <maml:para>Note 1</maml:para>
    <maml:para>Note a</maml:para>
  </maml:alert>
  <maml:alert>
    <maml:para>Note 2</maml:para>
  </maml:alert>
</maml:alertSet>
```
