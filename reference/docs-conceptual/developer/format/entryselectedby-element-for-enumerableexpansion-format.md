---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor EnumerableExpansion (opmaak)
description: Het element EntrySelectedBy voor EnumerableExpansion (opmaak)
ms.openlocfilehash: 8b2fff2d0b14d0622d0be2c5af3a95194c733a73
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652327"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="6d005-103">Het element EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d005-103">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="6d005-104">Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6d005-104">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="6d005-105">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="6d005-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6d005-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d005-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d005-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6d005-107">Attributes and Elements</span></span>

<span data-ttu-id="6d005-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="6d005-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d005-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6d005-109">Attributes</span></span>

<span data-ttu-id="6d005-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="6d005-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d005-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6d005-111">Child Elements</span></span>

|<span data-ttu-id="6d005-112">Element</span><span class="sxs-lookup"><span data-stu-id="6d005-112">Element</span></span>|<span data-ttu-id="6d005-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6d005-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d005-114">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d005-114">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="6d005-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6d005-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6d005-116">Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="6d005-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="6d005-117">Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d005-117">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="6d005-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6d005-118">Optional element.</span></span><br /><br /> <span data-ttu-id="6d005-119">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van hoe verzamelings objecten worden uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="6d005-119">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="6d005-120">Het element TypeName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d005-120">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="6d005-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6d005-121">Optional element.</span></span><br /><br /> <span data-ttu-id="6d005-122">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van hoe verzamelings objecten worden uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="6d005-122">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6d005-123">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6d005-123">Parent Elements</span></span>

|<span data-ttu-id="6d005-124">Element</span><span class="sxs-lookup"><span data-stu-id="6d005-124">Element</span></span>|<span data-ttu-id="6d005-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6d005-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d005-126">Het element EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d005-126">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="6d005-127">Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6d005-127">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6d005-128">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6d005-128">Remarks</span></span>

<span data-ttu-id="6d005-129">U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie vermelding opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d005-129">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="6d005-130">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6d005-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="6d005-131">De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een specifiek script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="6d005-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="6d005-132">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="6d005-132">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6d005-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6d005-133">See Also</span></span>

[<span data-ttu-id="6d005-134">Voorwaarden voor het weergeven van gegevens definiëren</span><span class="sxs-lookup"><span data-stu-id="6d005-134">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6d005-135">Het element EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d005-135">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="6d005-136">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d005-136">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6d005-137">Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d005-137">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6d005-138">Het element TypeName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d005-138">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6d005-139">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="6d005-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
