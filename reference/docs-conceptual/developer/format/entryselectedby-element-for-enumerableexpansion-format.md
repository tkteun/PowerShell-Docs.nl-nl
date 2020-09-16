---
title: EntrySelectedBy-element voor EnumerableExpansion (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 031bf10cfb1aed2c737fdd53fa4f20f025351d40
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783667"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="e1a0d-102">Het element EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e1a0d-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="e1a0d-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="e1a0d-104">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="e1a0d-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1a0d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e1a0d-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1a0d-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e1a0d-106">Attributes and Elements</span></span>

<span data-ttu-id="e1a0d-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1a0d-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e1a0d-108">Attributes</span></span>

<span data-ttu-id="e1a0d-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1a0d-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e1a0d-110">Child Elements</span></span>

|<span data-ttu-id="e1a0d-111">Element</span><span class="sxs-lookup"><span data-stu-id="e1a0d-111">Element</span></span>|<span data-ttu-id="e1a0d-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e1a0d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1a0d-113">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e1a0d-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e1a0d-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e1a0d-115">Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="e1a0d-116">Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e1a0d-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e1a0d-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e1a0d-118">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van hoe verzamelings objecten worden uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="e1a0d-119">Het element TypeName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e1a0d-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e1a0d-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e1a0d-121">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van hoe verzamelings objecten worden uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e1a0d-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e1a0d-122">Parent Elements</span></span>

|<span data-ttu-id="e1a0d-123">Element</span><span class="sxs-lookup"><span data-stu-id="e1a0d-123">Element</span></span>|<span data-ttu-id="e1a0d-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e1a0d-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1a0d-125">Het element EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e1a0d-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="e1a0d-126">Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e1a0d-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e1a0d-127">Remarks</span></span>

<span data-ttu-id="e1a0d-128">U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie vermelding opgeven.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="e1a0d-129">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="e1a0d-130">De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een specifiek script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="e1a0d-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="e1a0d-131">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="e1a0d-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1a0d-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e1a0d-132">See Also</span></span>

[<span data-ttu-id="e1a0d-133">Voorwaarden voor het weergeven van gegevens definiëren</span><span class="sxs-lookup"><span data-stu-id="e1a0d-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e1a0d-134">Het element EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e1a0d-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="e1a0d-135">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e1a0d-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e1a0d-136">Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e1a0d-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e1a0d-137">Het element TypeName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e1a0d-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e1a0d-138">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e1a0d-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
