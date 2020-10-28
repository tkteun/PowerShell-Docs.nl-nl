---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)
description: Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 1dd325a58b29a0f13b1341559c2a7dfe251c6b36
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665852"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="148a2-103">Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="148a2-103">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="148a2-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="148a2-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="148a2-105">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="148a2-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="148a2-106">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="148a2-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="148a2-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element voor weer gave (indeling) CustomEntries-element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor CustomControl voor weer gave (Format) EntrySelectedBy-element voor CustomEntry voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy voor het object CustomControl voor de weer gave (Format) voor SelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="148a2-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="148a2-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="148a2-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="148a2-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="148a2-109">Attributes and Elements</span></span>

<span data-ttu-id="148a2-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="148a2-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="148a2-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="148a2-111">Attributes</span></span>

<span data-ttu-id="148a2-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="148a2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="148a2-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="148a2-113">Child Elements</span></span>

<span data-ttu-id="148a2-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="148a2-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="148a2-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="148a2-115">Parent Elements</span></span>

|<span data-ttu-id="148a2-116">Element</span><span class="sxs-lookup"><span data-stu-id="148a2-116">Element</span></span>|<span data-ttu-id="148a2-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="148a2-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="148a2-118">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="148a2-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="148a2-119">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="148a2-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="148a2-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="148a2-120">Text Value</span></span>

<span data-ttu-id="148a2-121">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="148a2-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="148a2-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="148a2-122">Remarks</span></span>

<span data-ttu-id="148a2-123">De selectie voorwaarde moet ten minste één eigenschaps naam of een script opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="148a2-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="148a2-124">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="148a2-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="148a2-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="148a2-125">See Also</span></span>

[<span data-ttu-id="148a2-126">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="148a2-126">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="148a2-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="148a2-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
