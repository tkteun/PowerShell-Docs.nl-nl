---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)
description: Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)
ms.openlocfilehash: 5af4abe081ca268699d281a1b586a584107b9a83
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652359"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="50534-103">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="50534-103">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="50534-104">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="50534-104">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="50534-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="50534-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="50534-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor het object CustomControl voor GroupBy (Format) EntrySelectedBy voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="50534-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="50534-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="50534-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50534-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="50534-108">Attributes and Elements</span></span>

<span data-ttu-id="50534-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="50534-109">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="50534-110">U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="50534-110">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="50534-111">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="50534-111">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="50534-112">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="50534-112">Attributes</span></span>

<span data-ttu-id="50534-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="50534-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50534-114">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="50534-114">Child Elements</span></span>

|<span data-ttu-id="50534-115">Element</span><span class="sxs-lookup"><span data-stu-id="50534-115">Element</span></span>|<span data-ttu-id="50534-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="50534-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50534-117">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="50534-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="50534-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="50534-118">Optional element.</span></span><br /><br /> <span data-ttu-id="50534-119">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="50534-119">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="50534-120">Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="50534-120">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="50534-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="50534-121">Optional element.</span></span><br /><br /> <span data-ttu-id="50534-122">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="50534-122">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="50534-123">Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="50534-123">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="50534-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="50534-124">Optional element.</span></span><br /><br /> <span data-ttu-id="50534-125">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="50534-125">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="50534-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="50534-126">Parent Elements</span></span>

|<span data-ttu-id="50534-127">Element</span><span class="sxs-lookup"><span data-stu-id="50534-127">Element</span></span>|<span data-ttu-id="50534-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="50534-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50534-129">Het element CustomEntry voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="50534-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="50534-130">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="50534-130">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="50534-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="50534-131">Remarks</span></span>

<span data-ttu-id="50534-132">Selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="50534-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="50534-133">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="50534-133">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="50534-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="50534-134">See Also</span></span>

[<span data-ttu-id="50534-135">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="50534-135">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="50534-136">Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="50534-136">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="50534-137">Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="50534-137">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="50534-138">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="50534-138">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="50534-139">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="50534-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
