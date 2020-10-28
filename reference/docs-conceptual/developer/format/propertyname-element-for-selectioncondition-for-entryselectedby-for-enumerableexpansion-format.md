---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)
description: Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)
ms.openlocfilehash: 8e28118894661b50e90a5ccc86a36fbbe77e4b03
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665835"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="cefa7-103">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cefa7-103">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="cefa7-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="cefa7-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="cefa7-105">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cefa7-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="cefa7-106">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (Format) eigenschap Naam element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="cefa7-106">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cefa7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="cefa7-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cefa7-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="cefa7-108">Attributes and Elements</span></span>

<span data-ttu-id="cefa7-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="cefa7-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cefa7-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="cefa7-110">Attributes</span></span>

<span data-ttu-id="cefa7-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="cefa7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cefa7-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cefa7-112">Child Elements</span></span>

<span data-ttu-id="cefa7-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="cefa7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cefa7-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cefa7-114">Parent Elements</span></span>

|<span data-ttu-id="cefa7-115">Element</span><span class="sxs-lookup"><span data-stu-id="cefa7-115">Element</span></span>|<span data-ttu-id="cefa7-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cefa7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cefa7-117">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cefa7-117">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="cefa7-118">Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="cefa7-118">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cefa7-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="cefa7-119">Text Value</span></span>

<span data-ttu-id="cefa7-120">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="cefa7-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="cefa7-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cefa7-121">Remarks</span></span>

<span data-ttu-id="cefa7-122">Voor de selectie voorwaarde moet ten minste één eigenschaps naam of een script worden opgegeven om te evalueren, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="cefa7-122">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="cefa7-123">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="cefa7-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cefa7-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cefa7-124">See Also</span></span>

[<span data-ttu-id="cefa7-125">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="cefa7-125">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cefa7-126">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cefa7-126">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="cefa7-127">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cefa7-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="cefa7-128">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="cefa7-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
