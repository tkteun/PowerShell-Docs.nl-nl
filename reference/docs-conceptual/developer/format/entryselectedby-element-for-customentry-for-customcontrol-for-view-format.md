---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)
description: Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 4821f22560f35034f90d018e5a109004f331441f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655351"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="73272-103">Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73272-103">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="73272-104">Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="73272-104">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="73272-105">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) EntrySelectedBy element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="73272-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73272-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="73272-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73272-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="73272-107">Attributes and Elements</span></span>

<span data-ttu-id="73272-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="73272-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="73272-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="73272-109">Attributes</span></span>

<span data-ttu-id="73272-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="73272-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73272-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="73272-111">Child Elements</span></span>

|<span data-ttu-id="73272-112">Element</span><span class="sxs-lookup"><span data-stu-id="73272-112">Element</span></span>|<span data-ttu-id="73272-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="73272-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73272-114">SelectionCondition-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="73272-114">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="73272-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73272-115">Optional element.</span></span><br /><br /> <span data-ttu-id="73272-116">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="73272-116">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="73272-117">SelectionSetName-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="73272-117">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="73272-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73272-118">Optional element.</span></span><br /><br /> <span data-ttu-id="73272-119">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van de beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="73272-119">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="73272-120">TypeName-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="73272-120">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="73272-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73272-121">Optional element.</span></span><br /><br /> <span data-ttu-id="73272-122">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van de controle weergave.</span><span class="sxs-lookup"><span data-stu-id="73272-122">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="73272-123">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="73272-123">Parent Elements</span></span>

|<span data-ttu-id="73272-124">Element</span><span class="sxs-lookup"><span data-stu-id="73272-124">Element</span></span>|<span data-ttu-id="73272-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="73272-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73272-126">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="73272-126">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="73272-127">Hiermee worden de besturings elementen gedefinieerd die worden gebruikt door specifieke .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="73272-127">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="73272-128">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="73272-128">Remarks</span></span>

<span data-ttu-id="73272-129">U moet ten minste één type, selectieset of selectie voorwaarde voor een vermelding opgeven.</span><span class="sxs-lookup"><span data-stu-id="73272-129">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="73272-130">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="73272-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="73272-131">Selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die moet bestaan voor het gebruik van de vermelding, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="73272-131">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="73272-132">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="73272-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="73272-133">Zie [aangepaste besturings elementen weer geven](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="73272-133">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73272-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="73272-134">See Also</span></span>

[<span data-ttu-id="73272-135">SelectionCondition-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="73272-135">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="73272-136">SelectionSetName-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="73272-136">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="73272-137">TypeName-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="73272-137">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="73272-138">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="73272-138">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="73272-139">Aangepaste besturings elementen weer geven</span><span class="sxs-lookup"><span data-stu-id="73272-139">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="73272-140">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="73272-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
