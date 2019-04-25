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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083334"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="3775f-102">Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="3775f-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="3775f-103">In deze sectie wordt beschreven hoe u verwijzingen naar andere inhoud die is gerelateerd aan een Windows PowerShell® cmdlet Help-onderwerp toevoegen.</span><span class="sxs-lookup"><span data-stu-id="3775f-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="3775f-104">Omdat deze verwijzingen worden weergegeven in een opdrachtvenster, worden ze niet koppelen rechtstreeks naar de inhoud waarnaar wordt verwezen.</span><span class="sxs-lookup"><span data-stu-id="3775f-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="3775f-105">In de cmdlet Help-onderwerpen die zijn opgenomen in Windows PowerShell®, verwijst deze koppelingen naar andere cmdlets, conceptuele inhoud ("about_"), en andere documenten en Help-bestanden die niet gerelateerd zijn aan Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="3775f-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="3775f-106">De volgende XML-code laat zien hoe een RelatedLinks-knooppunt met twee verwijzingen naar verwante onderwerpen wilt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="3775f-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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



