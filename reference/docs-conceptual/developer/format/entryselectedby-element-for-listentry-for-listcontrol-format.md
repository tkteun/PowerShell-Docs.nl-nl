---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor ListEntry voor ListControl (opmaak)
description: Het element EntrySelectedBy voor ListEntry voor ListControl (opmaak)
ms.openlocfilehash: 1981c8fae65f494504d6cdd9f59337d555350b07
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652297"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="81749-103">Het element EntrySelectedBy voor ListEntry voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="81749-103">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="81749-104">Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst weergave definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="81749-104">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="81749-105">In de meeste gevallen is slechts één definitie nodig voor een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="81749-105">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="81749-106">U kunt echter meerdere definities voor de lijst weergave opgeven als u dezelfde lijst weergave wilt gebruiken om verschillende gegevens voor verschillende objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="81749-106">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="81749-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) element (Format) List item voor ListControl (indeling) voor List entry voor ListControl (Format) element list item voor ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="81749-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="81749-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="81749-108">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="81749-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="81749-109">Attributes and Elements</span></span>

<span data-ttu-id="81749-110">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="81749-110">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="81749-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="81749-111">Attributes</span></span>

<span data-ttu-id="81749-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="81749-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="81749-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="81749-113">Child Elements</span></span>

|<span data-ttu-id="81749-114">Element</span><span class="sxs-lookup"><span data-stu-id="81749-114">Element</span></span>|<span data-ttu-id="81749-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="81749-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81749-116">SelectionCondition-element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="81749-116">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="81749-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="81749-117">Optional element.</span></span><br /><br /> <span data-ttu-id="81749-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="81749-118">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="81749-119">Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="81749-119">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="81749-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="81749-120">Optional element.</span></span><br /><br /> <span data-ttu-id="81749-121">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze lijst weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="81749-121">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="81749-122">Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="81749-122">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="81749-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="81749-123">Optional element.</span></span><br /><br /> <span data-ttu-id="81749-124">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze lijst weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="81749-124">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="81749-125">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="81749-125">Parent Elements</span></span>

|<span data-ttu-id="81749-126">Element</span><span class="sxs-lookup"><span data-stu-id="81749-126">Element</span></span>|<span data-ttu-id="81749-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="81749-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81749-128">Het element ListEntry voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="81749-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="81749-129">Hiermee wordt gedefinieerd hoe de rijen van de lijst worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="81749-129">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="81749-130">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="81749-130">Remarks</span></span>

<span data-ttu-id="81749-131">U moet ten minste één type, selectieset of selectie voorwaarde opgeven voor een lijst weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="81749-131">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="81749-132">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="81749-132">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="81749-133">De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een specifiek script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="81749-133">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="81749-134">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="81749-134">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="81749-135">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="81749-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="81749-136">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="81749-136">Example</span></span>

<span data-ttu-id="81749-137">In het volgende voor beeld ziet u hoe u de objecten voor een lijst weergave definieert met behulp van de .NET-type naam.</span><span class="sxs-lookup"><span data-stu-id="81749-137">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="81749-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="81749-138">See Also</span></span>

[<span data-ttu-id="81749-139">Het element ListEntry voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="81749-139">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="81749-140">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="81749-140">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="81749-141">Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="81749-141">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="81749-142">Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="81749-142">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="81749-143">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="81749-143">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="81749-144">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="81749-144">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="81749-145">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="81749-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
