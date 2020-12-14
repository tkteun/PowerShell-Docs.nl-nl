---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor SelectionCondition voor GroupBy (opmaak)
description: Het element PropertyName voor SelectionCondition voor GroupBy (opmaak)
ms.openlocfilehash: b89fead6185c88ca03956dc265135833696b91d7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665665"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="9189d-103">Het element PropertyName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9189d-103">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="9189d-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9189d-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="9189d-105">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9189d-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="9189d-106">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9189d-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9189d-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) voor SelectionCondition voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9189d-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9189d-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="9189d-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9189d-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9189d-109">Attributes and Elements</span></span>

<span data-ttu-id="9189d-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="9189d-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9189d-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9189d-111">Attributes</span></span>

<span data-ttu-id="9189d-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="9189d-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9189d-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9189d-113">Child Elements</span></span>

<span data-ttu-id="9189d-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="9189d-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9189d-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9189d-115">Parent Elements</span></span>

|<span data-ttu-id="9189d-116">Element</span><span class="sxs-lookup"><span data-stu-id="9189d-116">Element</span></span>|<span data-ttu-id="9189d-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9189d-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9189d-118">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9189d-118">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="9189d-119">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="9189d-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9189d-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="9189d-120">Text Value</span></span>

<span data-ttu-id="9189d-121">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="9189d-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="9189d-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9189d-122">Remarks</span></span>

<span data-ttu-id="9189d-123">De selectie voorwaarde moet ten minste één eigenschaps naam of een script opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="9189d-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="9189d-124">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9189d-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9189d-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9189d-125">See Also</span></span>

[<span data-ttu-id="9189d-126">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9189d-126">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="9189d-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="9189d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
