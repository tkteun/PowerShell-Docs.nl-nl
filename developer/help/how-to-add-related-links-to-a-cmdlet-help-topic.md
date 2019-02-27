---
title: Verwante koppelingen toevoegen aan een Cmdlet Help-onderwerp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846387"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u verwijzingen naar andere inhoud die is gerelateerd aan een Windows PowerShell® cmdlet Help-onderwerp toevoegen. Omdat deze verwijzingen worden weergegeven in een opdrachtvenster, worden ze niet koppelen rechtstreeks naar de inhoud waarnaar wordt verwezen.

In de cmdlet Help-onderwerpen die zijn opgenomen in Windows PowerShell®, verwijst deze koppelingen naar andere cmdlets, conceptuele inhoud ("about_"), en andere documenten en Help-bestanden die niet gerelateerd zijn aan Windows PowerShell®.

De volgende XML-code laat zien hoe een RelatedLinks-knooppunt met twee verwijzingen naar verwante onderwerpen wilt toevoegen.

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



