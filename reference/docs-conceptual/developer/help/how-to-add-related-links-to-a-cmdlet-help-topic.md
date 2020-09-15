---
title: Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets
ms.date: 09/12/2016
ms.openlocfilehash: 7557b3856d8470434070dd286cd7e30c9ba015c5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893370"
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
