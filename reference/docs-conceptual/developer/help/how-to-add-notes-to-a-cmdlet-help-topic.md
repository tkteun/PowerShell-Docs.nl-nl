---
title: Notities toevoegen aan een Help-onderwerp voor cmdlets
ms.date: 10/20/2020
ms.openlocfilehash: 7f8be34a82de2c12cfd2a05deed139ddb30da95f
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "92298315"
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
