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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355872"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="bd713-102">Het element ScriptBlock voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="bd713-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="bd713-103">Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bd713-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="bd713-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (Format) script block-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="bd713-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd713-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="bd713-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bd713-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="bd713-106">Attributes and Elements</span></span>

<span data-ttu-id="bd713-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="bd713-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd713-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="bd713-108">Attributes</span></span>

<span data-ttu-id="bd713-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="bd713-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bd713-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bd713-110">Child Elements</span></span>

<span data-ttu-id="bd713-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="bd713-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bd713-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bd713-112">Parent Elements</span></span>

|<span data-ttu-id="bd713-113">Element</span><span class="sxs-lookup"><span data-stu-id="bd713-113">Element</span></span>|<span data-ttu-id="bd713-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bd713-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bd713-115">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="bd713-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="bd713-116">Hiermee definieert u hoe een groep .NET-objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bd713-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bd713-117">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="bd713-117">Text Value</span></span>

<span data-ttu-id="bd713-118">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="bd713-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd713-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bd713-119">Remarks</span></span>

<span data-ttu-id="bd713-120">Power shell start een nieuwe groep wanneer de waarde van dit script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bd713-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="bd713-121">Als dit element is opgegeven, kunt u het element [PropertyName](propertyname-element-for-groupby-format.md) niet opgeven om een nieuwe groep te starten.</span><span class="sxs-lookup"><span data-stu-id="bd713-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd713-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bd713-122">See Also</span></span>

[<span data-ttu-id="bd713-123">PropertyName-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="bd713-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="bd713-124">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="bd713-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="bd713-125">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="bd713-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
