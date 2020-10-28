---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor GroupBy (opmaak)
description: Het element ScriptBlock voor GroupBy (opmaak)
ms.openlocfilehash: 117cbef93889046626741449886a1caaa39815cb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665236"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="ef721-103">Het element ScriptBlock voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef721-103">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="ef721-104">Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="ef721-104">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="ef721-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (Format) script block-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="ef721-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef721-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef721-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef721-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ef721-107">Attributes and Elements</span></span>

<span data-ttu-id="ef721-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="ef721-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef721-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ef721-109">Attributes</span></span>

<span data-ttu-id="ef721-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="ef721-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef721-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ef721-111">Child Elements</span></span>

<span data-ttu-id="ef721-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="ef721-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ef721-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ef721-113">Parent Elements</span></span>

|<span data-ttu-id="ef721-114">Element</span><span class="sxs-lookup"><span data-stu-id="ef721-114">Element</span></span>|<span data-ttu-id="ef721-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ef721-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef721-116">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef721-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="ef721-117">Hiermee definieert u hoe een groep .NET-objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef721-117">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ef721-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="ef721-118">Text Value</span></span>

<span data-ttu-id="ef721-119">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="ef721-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef721-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ef721-120">Remarks</span></span>

<span data-ttu-id="ef721-121">Power shell start een nieuwe groep wanneer de waarde van dit script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="ef721-121">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="ef721-122">Als dit element is opgegeven, kunt u het element [PropertyName](propertyname-element-for-groupby-format.md) niet opgeven om een nieuwe groep te starten.</span><span class="sxs-lookup"><span data-stu-id="ef721-122">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef721-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ef721-123">See Also</span></span>

[<span data-ttu-id="ef721-124">Het element PropertyName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef721-124">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="ef721-125">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef721-125">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="ef721-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="ef721-126">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
