---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)
description: Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)
ms.openlocfilehash: f3193799e67706eb07f0fe1c2cd42cce83f7af57
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651550"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="d4ba0-103">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d4ba0-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="d4ba0-104">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="d4ba0-105">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van deze definitie van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="d4ba0-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ListControl element (indeling) item type-element (indeling) EntrySelectedBy element (Format) element list item (Format) voor List entry (Format) SelectionCondition-element voor EntrySelectedBy voor List entry (Format) SelectionSetName-element voor SelectionCondition voor List entry (Format)</span><span class="sxs-lookup"><span data-stu-id="d4ba0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d4ba0-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d4ba0-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4ba0-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d4ba0-108">Attributes and Elements</span></span>

<span data-ttu-id="d4ba0-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d4ba0-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d4ba0-110">Attributes</span></span>

<span data-ttu-id="d4ba0-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d4ba0-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d4ba0-112">Child Elements</span></span>

<span data-ttu-id="d4ba0-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d4ba0-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d4ba0-114">Parent Elements</span></span>

|<span data-ttu-id="d4ba0-115">Element</span><span class="sxs-lookup"><span data-stu-id="d4ba0-115">Element</span></span>|<span data-ttu-id="d4ba0-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d4ba0-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4ba0-117">SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="d4ba0-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d4ba0-118">Hiermee definieert u de voor waarde die moet bestaan om deze definitie van de lijst weergave te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-118">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d4ba0-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="d4ba0-119">Text Value</span></span>

<span data-ttu-id="d4ba0-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d4ba0-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d4ba0-121">Remarks</span></span>

<span data-ttu-id="d4ba0-122">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="d4ba0-123">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d4ba0-124">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="d4ba0-125">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-125">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d4ba0-126">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over andere onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="d4ba0-126">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4ba0-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d4ba0-127">See Also</span></span>

[<span data-ttu-id="d4ba0-128">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="d4ba0-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d4ba0-129">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="d4ba0-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d4ba0-130">SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="d4ba0-130">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="d4ba0-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d4ba0-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
