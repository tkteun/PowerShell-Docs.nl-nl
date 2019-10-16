---
title: EntrySelectedBy-element voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358992"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="fb476-102">Het element EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fb476-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="fb476-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fb476-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="fb476-104">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb476-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fb476-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fb476-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fb476-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fb476-106">Attributes and Elements</span></span>

<span data-ttu-id="fb476-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `EntrySelectedBy` beschreven.</span><span class="sxs-lookup"><span data-stu-id="fb476-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb476-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fb476-108">Attributes</span></span>

<span data-ttu-id="fb476-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="fb476-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fb476-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fb476-110">Child Elements</span></span>

|<span data-ttu-id="fb476-111">Element</span><span class="sxs-lookup"><span data-stu-id="fb476-111">Element</span></span>|<span data-ttu-id="fb476-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fb476-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb476-113">SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb476-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="fb476-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="fb476-114">Optional element.</span></span><br /><br /> <span data-ttu-id="fb476-115">Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="fb476-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="fb476-116">SelectionSetName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb476-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="fb476-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="fb476-117">Optional element.</span></span><br /><br /> <span data-ttu-id="fb476-118">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van hoe verzamelings objecten worden uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="fb476-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="fb476-119">TypeName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb476-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="fb476-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="fb476-120">Optional element.</span></span><br /><br /> <span data-ttu-id="fb476-121">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van hoe verzamelings objecten worden uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="fb476-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fb476-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fb476-122">Parent Elements</span></span>

|<span data-ttu-id="fb476-123">Element</span><span class="sxs-lookup"><span data-stu-id="fb476-123">Element</span></span>|<span data-ttu-id="fb476-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fb476-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb476-125">EnumerableExpansion-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb476-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="fb476-126">Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fb476-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fb476-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fb476-127">Remarks</span></span>

<span data-ttu-id="fb476-128">U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie vermelding opgeven.</span><span class="sxs-lookup"><span data-stu-id="fb476-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="fb476-129">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fb476-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="fb476-130">De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een script het `true` evalueert.</span><span class="sxs-lookup"><span data-stu-id="fb476-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="fb476-131">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="fb476-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb476-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fb476-132">See Also</span></span>

[<span data-ttu-id="fb476-133">Voor waarden definiëren voor het weer geven van gegevens</span><span class="sxs-lookup"><span data-stu-id="fb476-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fb476-134">EnumerableExpansion-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb476-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="fb476-135">SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb476-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="fb476-136">SelectionSetName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb476-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="fb476-137">TypeName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb476-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="fb476-138">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="fb476-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
