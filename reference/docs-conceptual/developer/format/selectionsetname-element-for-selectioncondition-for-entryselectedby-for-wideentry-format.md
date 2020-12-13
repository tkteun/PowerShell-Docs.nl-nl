---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)
description: Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)
ms.openlocfilehash: c6466e3ac6e1f194df9172468d26448f9630da6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655009"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="60531-103">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="60531-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="60531-104">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="60531-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="60531-105">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van deze definitie van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="60531-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="60531-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition-element voor EntrySelectedBy voor WideEntry (Format) SelectionSetName-element voor SelectionCondition voor EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="60531-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="60531-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="60531-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60531-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="60531-108">Attributes and Elements</span></span>

<span data-ttu-id="60531-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="60531-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="60531-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="60531-110">Attributes</span></span>

<span data-ttu-id="60531-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="60531-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60531-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="60531-112">Child Elements</span></span>

<span data-ttu-id="60531-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="60531-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="60531-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="60531-114">Parent Elements</span></span>

|<span data-ttu-id="60531-115">Element</span><span class="sxs-lookup"><span data-stu-id="60531-115">Element</span></span>|<span data-ttu-id="60531-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="60531-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60531-117">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="60531-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="60531-118">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="60531-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="60531-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="60531-119">Text Value</span></span>

<span data-ttu-id="60531-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="60531-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="60531-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="60531-121">Remarks</span></span>

<span data-ttu-id="60531-122">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="60531-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="60531-123">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="60531-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="60531-124">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="60531-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="60531-125">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="60531-125">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="60531-126">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="60531-126">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="60531-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="60531-127">See Also</span></span>

[<span data-ttu-id="60531-128">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="60531-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="60531-129">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="60531-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="60531-130">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="60531-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="60531-131">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="60531-131">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="60531-132">TypeName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="60531-132">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="60531-133">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="60531-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
