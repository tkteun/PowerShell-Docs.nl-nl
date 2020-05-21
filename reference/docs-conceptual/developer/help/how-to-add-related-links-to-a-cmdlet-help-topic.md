---
title: Verwante koppelingen toevoegen aan een Help-onderwerp over cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: 0a6403e2dea16d73e2fdcb8cf5df39b2aa5b5dae
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560267"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u verwijzingen kunt toevoegen aan andere inhoud die betrekking heeft op een Help-onderwerp voor Windows Power shell®-cmdlet. Omdat deze verwijzingen worden weer gegeven in een opdracht venster, worden ze niet rechtstreeks gekoppeld aan de inhoud waarnaar wordt verwezen.

In de Help-onderwerpen over cmdlets die zijn opgenomen in Windows Power shell® verwijzen deze koppelingen naar andere cmdlets, conceptuele inhoud (' about_ ') en andere documenten en Help-bestanden die geen betrekking hebben op Windows Power shell®.

In het volgende XML-bestand ziet u hoe u een RelatedLinks-knoop punt kunt toevoegen dat twee verwijzingen naar verwante onderwerpen bevat.

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```
