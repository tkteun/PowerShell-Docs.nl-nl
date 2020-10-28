---
ms.date: 09/13/2016
ms.topic: reference
title: Het element FirstLineHanging voor Frame voor GroupBy (opmaak)
description: Het element FirstLineHanging voor Frame voor GroupBy (opmaak)
ms.openlocfilehash: 6a4ded9cced484440636aee694cd8381b2889ba8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652281"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a><span data-ttu-id="d19c2-103">Het element FirstLineHanging voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d19c2-103">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="d19c2-104">Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.</span><span class="sxs-lookup"><span data-stu-id="d19c2-104">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="d19c2-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d19c2-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d19c2-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) voor het object voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="d19c2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d19c2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d19c2-107">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d19c2-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d19c2-108">Attributes and Elements</span></span>

<span data-ttu-id="d19c2-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `FirstLineHanging` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d19c2-109">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d19c2-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d19c2-110">Attributes</span></span>

<span data-ttu-id="d19c2-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="d19c2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d19c2-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d19c2-112">Child Elements</span></span>

<span data-ttu-id="d19c2-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="d19c2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d19c2-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d19c2-114">Parent Elements</span></span>

|<span data-ttu-id="d19c2-115">Element</span><span class="sxs-lookup"><span data-stu-id="d19c2-115">Element</span></span>|<span data-ttu-id="d19c2-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d19c2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d19c2-117">Het element Frame voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d19c2-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="d19c2-118">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="d19c2-118">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d19c2-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="d19c2-119">Text Value</span></span>

<span data-ttu-id="d19c2-120">Geef het aantal tekens op waarmee u de eerste regel van de gegevens wilt verschuiven.</span><span class="sxs-lookup"><span data-stu-id="d19c2-120">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="d19c2-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d19c2-121">Remarks</span></span>

<span data-ttu-id="d19c2-122">Als dit element is opgegeven, kunt u het [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -element niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="d19c2-122">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="d19c2-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d19c2-123">See Also</span></span>

[<span data-ttu-id="d19c2-124">Het element FirstLineIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d19c2-124">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="d19c2-125">Het element Frame voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d19c2-125">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="d19c2-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d19c2-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
