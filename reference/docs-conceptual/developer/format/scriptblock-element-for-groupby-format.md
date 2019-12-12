---
title: Script block-element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355872"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="fcdce-102">Het element ScriptBlock voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fcdce-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="fcdce-103">Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="fcdce-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="fcdce-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (Format) script block-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="fcdce-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fcdce-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fcdce-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fcdce-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fcdce-106">Attributes and Elements</span></span>

<span data-ttu-id="fcdce-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="fcdce-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fcdce-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fcdce-108">Attributes</span></span>

<span data-ttu-id="fcdce-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="fcdce-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fcdce-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fcdce-110">Child Elements</span></span>

<span data-ttu-id="fcdce-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="fcdce-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fcdce-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fcdce-112">Parent Elements</span></span>

|<span data-ttu-id="fcdce-113">Element</span><span class="sxs-lookup"><span data-stu-id="fcdce-113">Element</span></span>|<span data-ttu-id="fcdce-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fcdce-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fcdce-115">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fcdce-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="fcdce-116">Hiermee definieert u hoe een groep .NET-objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcdce-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fcdce-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="fcdce-117">Text Value</span></span>

<span data-ttu-id="fcdce-118">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="fcdce-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcdce-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fcdce-119">Remarks</span></span>

<span data-ttu-id="fcdce-120">Power shell start een nieuwe groep wanneer de waarde van dit script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="fcdce-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="fcdce-121">Als dit element is opgegeven, kunt u het element [PropertyName](propertyname-element-for-groupby-format.md) niet opgeven om een nieuwe groep te starten.</span><span class="sxs-lookup"><span data-stu-id="fcdce-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcdce-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fcdce-122">See Also</span></span>

[<span data-ttu-id="fcdce-123">PropertyName-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="fcdce-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="fcdce-124">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fcdce-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="fcdce-125">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="fcdce-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
