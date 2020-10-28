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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="e9110-103">Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="e9110-103">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="e9110-104">In deze sectie wordt beschreven hoe u verwijzingen kunt toevoegen aan andere inhoud die betrekking heeft op een Help-onderwerp voor Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e9110-104">This section describes how to add references to other content that is related to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="e9110-105">Omdat deze verwijzingen worden weer gegeven in een opdracht venster, worden ze niet rechtstreeks gekoppeld aan de inhoud waarnaar wordt verwezen.</span><span class="sxs-lookup"><span data-stu-id="e9110-105">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="e9110-106">In de Help-onderwerpen over cmdlets die zijn opgenomen in Power shell verwijzen deze koppelingen naar andere cmdlets, conceptuele inhoud ( `about_` ) en andere documenten en Help-bestanden die geen betrekking hebben op Power shell.</span><span class="sxs-lookup"><span data-stu-id="e9110-106">In the cmdlet Help topics that are included in PowerShell, these links reference other cmdlets, conceptual content (`about_`), and other documents and Help files that are not related to PowerShell.</span></span>

<span data-ttu-id="e9110-107">In het volgende XML-bestand ziet u hoe u een **RelatedLinks** -knoop punt kunt toevoegen dat twee verwijzingen naar verwante onderwerpen bevat.</span><span class="sxs-lookup"><span data-stu-id="e9110-107">The following XML shows how to add a **RelatedLinks** node that contains two references to related topics.</span></span>

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
