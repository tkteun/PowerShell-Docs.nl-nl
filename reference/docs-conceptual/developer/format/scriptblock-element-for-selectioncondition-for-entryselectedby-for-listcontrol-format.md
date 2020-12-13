---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)
description: Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)
ms.openlocfilehash: ec7691358d0ff3758411317a349221e1704a1895
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659902"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="efdfd-103">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="efdfd-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="efdfd-104">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="efdfd-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="efdfd-105">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de vermelding in de lijst gebruikt.</span><span class="sxs-lookup"><span data-stu-id="efdfd-105">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="efdfd-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ListControl element (indeling) item type-element (indeling) EntrySelectedBy element (Format) element list item (Format) voor List entry (Format) SelectionCondition-element voor EntrySelectedBy voor List entry (Format) script block-element voor SelectionCondition voor List entry (Format)</span><span class="sxs-lookup"><span data-stu-id="efdfd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="efdfd-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="efdfd-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="efdfd-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="efdfd-108">Attributes and Elements</span></span>

<span data-ttu-id="efdfd-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="efdfd-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="efdfd-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="efdfd-110">Attributes</span></span>

<span data-ttu-id="efdfd-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="efdfd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="efdfd-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="efdfd-112">Child Elements</span></span>

<span data-ttu-id="efdfd-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="efdfd-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="efdfd-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="efdfd-114">Parent Elements</span></span>

|<span data-ttu-id="efdfd-115">Element</span><span class="sxs-lookup"><span data-stu-id="efdfd-115">Element</span></span>|<span data-ttu-id="efdfd-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="efdfd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="efdfd-117">SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="efdfd-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="efdfd-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst vermelding.</span><span class="sxs-lookup"><span data-stu-id="efdfd-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="efdfd-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="efdfd-119">Text Value</span></span>

<span data-ttu-id="efdfd-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="efdfd-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="efdfd-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="efdfd-121">Remarks</span></span>

<span data-ttu-id="efdfd-122">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="efdfd-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="efdfd-123">(Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie voorwaarden kunnen worden gebruikt.)</span><span class="sxs-lookup"><span data-stu-id="efdfd-123">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="efdfd-124">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over de andere onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="efdfd-124">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="efdfd-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="efdfd-125">See Also</span></span>

[<span data-ttu-id="efdfd-126">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="efdfd-126">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="efdfd-127">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="efdfd-127">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="efdfd-128">SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="efdfd-128">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="efdfd-129">Lijst weergave</span><span class="sxs-lookup"><span data-stu-id="efdfd-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="efdfd-130">Voor waarden definiëren voor het gebruik van een weergave vermelding of een item</span><span class="sxs-lookup"><span data-stu-id="efdfd-130">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="efdfd-131">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="efdfd-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
