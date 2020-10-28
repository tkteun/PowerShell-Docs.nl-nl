---
ms.date: 09/12/2016
ms.topic: reference
title: Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets
description: Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets
ms.openlocfilehash: 7f1baefea69310bdf835c52461f8d3f49c4d94e8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661993"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u verwijzingen kunt toevoegen aan andere inhoud die betrekking heeft op een Help-onderwerp voor Power shell-cmdlets. Omdat deze verwijzingen worden weer gegeven in een opdracht venster, worden ze niet rechtstreeks gekoppeld aan de inhoud waarnaar wordt verwezen.

In de Help-onderwerpen over cmdlets die zijn opgenomen in Power shell verwijzen deze koppelingen naar andere cmdlets, conceptuele inhoud ( `about_` ) en andere documenten en Help-bestanden die geen betrekking hebben op Power shell.

In het volgende XML-bestand ziet u hoe u een **RelatedLinks** -knoop punt kunt toevoegen dat twee verwijzingen naar verwante onderwerpen bevat.

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
