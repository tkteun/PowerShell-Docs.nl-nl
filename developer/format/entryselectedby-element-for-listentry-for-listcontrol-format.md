---
title: EntrySelectedBy-Element voor ListEntry voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054931"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="f3791-102">Het element EntrySelectedBy voor ListEntry voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3791-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="f3791-103">Definieert de .NET-typen die gebruikmaken van de definitie van deze lijst weergeven of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f3791-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="f3791-104">In de meeste gevallen is slechts één definitie nodig voor een lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="f3791-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="f3791-105">U kunt echter meerdere definities voor de lijstweergave opgeven als u wilt de dezelfde lijstweergave gebruiken om verschillende gegevens voor verschillende objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f3791-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="f3791-106">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListEntry voor ListControl (indeling) EntrySelectedBy Element voor ListEntry voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3791-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f3791-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f3791-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f3791-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f3791-108">Attributes and Elements</span></span>

<span data-ttu-id="f3791-109">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="f3791-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f3791-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f3791-110">Attributes</span></span>

<span data-ttu-id="f3791-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="f3791-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f3791-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f3791-112">Child Elements</span></span>

|<span data-ttu-id="f3791-113">Element</span><span class="sxs-lookup"><span data-stu-id="f3791-113">Element</span></span>|<span data-ttu-id="f3791-114">Description</span><span class="sxs-lookup"><span data-stu-id="f3791-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3791-115">SelectionCondition-Element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3791-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f3791-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3791-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f3791-117">Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie voor het weergeven van lijst moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f3791-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="f3791-118">SelectionSetName-Element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3791-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f3791-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3791-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f3791-120">Hiermee geeft u een set van .NET-typen die gebruikmaken van de definitie van deze lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="f3791-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="f3791-121">TypeName-Element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3791-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f3791-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3791-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f3791-123">Hiermee geeft u een .NET-type dat gebruikmaakt van de definitie van deze lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="f3791-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f3791-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f3791-124">Parent Elements</span></span>

|<span data-ttu-id="f3791-125">Element</span><span class="sxs-lookup"><span data-stu-id="f3791-125">Element</span></span>|<span data-ttu-id="f3791-126">Description</span><span class="sxs-lookup"><span data-stu-id="f3791-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3791-127">ListEntry-Element voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3791-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="f3791-128">Hiermee definieert u hoe de rijen van de lijst worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="f3791-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f3791-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f3791-129">Remarks</span></span>

<span data-ttu-id="f3791-130">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van een lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="f3791-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="f3791-131">Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f3791-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="f3791-132">Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde die moet aanwezig zijn voor de definitie moet worden gebruikt, zoals wanneer een object een bepaalde eigenschap heeft of die een bepaalde eigenschapwaarde of een script wordt geëvalueerd als `true`.</span><span class="sxs-lookup"><span data-stu-id="f3791-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="f3791-133">Zie voor meer informatie over de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f3791-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f3791-134">Zie voor meer informatie over de onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f3791-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f3791-135">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f3791-135">Example</span></span>

<span data-ttu-id="f3791-136">Het volgende voorbeeld ziet hoe u definieert de objecten voor een lijst weergeven met behulp van de .NET-typenaam.</span><span class="sxs-lookup"><span data-stu-id="f3791-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="f3791-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f3791-137">See Also</span></span>

[<span data-ttu-id="f3791-138">ListEntry-Element voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3791-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f3791-139">SelectionCondition-Element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3791-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f3791-140">SelectionSetName-Element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3791-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f3791-141">TypeName-Element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3791-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f3791-142">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="f3791-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f3791-143">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="f3791-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f3791-144">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3791-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
