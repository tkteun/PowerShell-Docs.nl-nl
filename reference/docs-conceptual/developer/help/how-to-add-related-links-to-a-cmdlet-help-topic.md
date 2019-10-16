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
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353275"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="ec55a-102">Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="ec55a-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="ec55a-103">In deze sectie wordt beschreven hoe u verwijzingen kunt toevoegen aan andere inhoud die betrekking heeft op een Help-onderwerp voor Windows Power shell®-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ec55a-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="ec55a-104">Omdat deze verwijzingen worden weer gegeven in een opdracht venster, worden ze niet rechtstreeks gekoppeld aan de inhoud waarnaar wordt verwezen.</span><span class="sxs-lookup"><span data-stu-id="ec55a-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="ec55a-105">In de Help-onderwerpen over cmdlets die zijn opgenomen in Windows Power shell® verwijzen deze koppelingen naar andere cmdlets, conceptuele inhoud (' about_ ') en andere documenten en Help-bestanden die geen betrekking hebben op Windows Power shell®.</span><span class="sxs-lookup"><span data-stu-id="ec55a-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="ec55a-106">In het volgende XML-bestand ziet u hoe u een RelatedLinks-knoop punt kunt toevoegen dat twee verwijzingen naar verwante onderwerpen bevat.</span><span class="sxs-lookup"><span data-stu-id="ec55a-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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



