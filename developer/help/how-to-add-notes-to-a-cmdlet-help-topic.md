---
title: Notities toevoegen aan een Cmdlet Help-onderwerp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851196"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Notities toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een sectie met opmerkingen toevoegen aan een Windows PowerShell® cmdlet Help-onderwerp. De sectie met opmerkingen wordt gebruikt om uit te leggen van de gegevens die niet zijn voor eenvoudig in de andere gestructureerde secties, zoals een meer gedetailleerde uitleg van een parameter geschikt. Deze inhoud kan opmerkingen over de werking van de cmdlet met een specifieke provider, sommige unieke nog belangrijker, maakt gebruik van de cmdlet of manieren om te voorkomen dat mogelijk fouten bevatten.

Er zijn geen beperkingen voor het aantal opmerkingen in die u aan een sectie met opmerkingen toevoegen kunt. Voor elke opmerking toevoegen een tweetal \<maml:alert > tags aan het \<maml:alertset > knooppunt. De inhoud van elke opmerking wordt toegevoegd in een set \<maml:para > tags. Gebruik leeg \<maml:para > tags voor afstand.

De volgende XML bevat een \<maml:alertset > knooppunt met opmerkingen bij de twee. U ziet dat elke opmerking een optionele is \<maml:title > tag (titels kunnen worden gebruikt voor het groeperen van een set \<maml:alert > tags), en dat elke opmerking heeft een lege regel na de inhoud voor afstand.

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



