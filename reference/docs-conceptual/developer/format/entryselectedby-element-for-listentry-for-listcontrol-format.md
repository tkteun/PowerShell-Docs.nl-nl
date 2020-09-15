---
title: EntrySelectedBy-element voor List entry voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d6ab1c08dd353da74d1a7d27c569d2fa86e083c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774113"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="4da05-102">Het element EntrySelectedBy voor ListEntry voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4da05-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="4da05-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst weergave definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4da05-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="4da05-104">In de meeste gevallen is slechts één definitie nodig voor een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="4da05-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="4da05-105">U kunt echter meerdere definities voor de lijst weergave opgeven als u dezelfde lijst weergave wilt gebruiken om verschillende gegevens voor verschillende objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4da05-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="4da05-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) element (Format) List item voor ListControl (indeling) voor List entry voor ListControl (Format) element list item voor ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4da05-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4da05-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="4da05-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4da05-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="4da05-108">Attributes and Elements</span></span>

<span data-ttu-id="4da05-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="4da05-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4da05-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4da05-110">Attributes</span></span>

<span data-ttu-id="4da05-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="4da05-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4da05-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4da05-112">Child Elements</span></span>

|<span data-ttu-id="4da05-113">Element</span><span class="sxs-lookup"><span data-stu-id="4da05-113">Element</span></span>|<span data-ttu-id="4da05-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4da05-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4da05-115">SelectionCondition-element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="4da05-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="4da05-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4da05-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4da05-117">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="4da05-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="4da05-118">Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4da05-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="4da05-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4da05-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4da05-120">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze lijst weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="4da05-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="4da05-121">Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4da05-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="4da05-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4da05-122">Optional element.</span></span><br /><br /> <span data-ttu-id="4da05-123">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze lijst weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="4da05-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4da05-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4da05-124">Parent Elements</span></span>

|<span data-ttu-id="4da05-125">Element</span><span class="sxs-lookup"><span data-stu-id="4da05-125">Element</span></span>|<span data-ttu-id="4da05-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4da05-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4da05-127">Het element ListEntry voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4da05-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="4da05-128">Hiermee wordt gedefinieerd hoe de rijen van de lijst worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4da05-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4da05-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4da05-129">Remarks</span></span>

<span data-ttu-id="4da05-130">U moet ten minste één type, selectieset of selectie voorwaarde opgeven voor een lijst weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="4da05-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="4da05-131">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4da05-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="4da05-132">De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een specifiek script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="4da05-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="4da05-133">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="4da05-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="4da05-134">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="4da05-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4da05-135">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="4da05-135">Example</span></span>

<span data-ttu-id="4da05-136">In het volgende voor beeld ziet u hoe u de objecten voor een lijst weergave definieert met behulp van de .NET-type naam.</span><span class="sxs-lookup"><span data-stu-id="4da05-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="4da05-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4da05-137">See Also</span></span>

[<span data-ttu-id="4da05-138">Het element ListEntry voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4da05-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="4da05-139">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4da05-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="4da05-140">Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4da05-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="4da05-141">Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4da05-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="4da05-142">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="4da05-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4da05-143">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="4da05-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="4da05-144">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="4da05-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
