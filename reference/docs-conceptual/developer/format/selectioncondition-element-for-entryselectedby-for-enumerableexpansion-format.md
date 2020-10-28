---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)
ms.openlocfilehash: 3ecf7fde99b9ee66a153eea416792f351ff62af3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647925"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="f18b5-103">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f18b5-103">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="f18b5-104">Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="f18b5-104">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="f18b5-105">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="f18b5-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f18b5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f18b5-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f18b5-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f18b5-107">Attributes and Elements</span></span>

<span data-ttu-id="f18b5-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f18b5-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="f18b5-109">U moet één `PropertyName` element of opgeven `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="f18b5-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="f18b5-110">De `SelectionSetName` `TypeName` elementen en zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="f18b5-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="f18b5-111">U kunt een van beide elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="f18b5-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f18b5-112">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f18b5-112">Attributes</span></span>

<span data-ttu-id="f18b5-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="f18b5-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f18b5-114">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f18b5-114">Child Elements</span></span>

|<span data-ttu-id="f18b5-115">Element</span><span class="sxs-lookup"><span data-stu-id="f18b5-115">Element</span></span>|<span data-ttu-id="f18b5-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f18b5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f18b5-117">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f18b5-117">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f18b5-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f18b5-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f18b5-119">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f18b5-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f18b5-120">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f18b5-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f18b5-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f18b5-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f18b5-122">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f18b5-122">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f18b5-123">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f18b5-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f18b5-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f18b5-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f18b5-125">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f18b5-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f18b5-126">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f18b5-126">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f18b5-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f18b5-127">Optional element.</span></span><br /><br /> <span data-ttu-id="f18b5-128">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f18b5-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f18b5-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f18b5-129">Parent Elements</span></span>

|<span data-ttu-id="f18b5-130">Element</span><span class="sxs-lookup"><span data-stu-id="f18b5-130">Element</span></span>|<span data-ttu-id="f18b5-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f18b5-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f18b5-132">Het element EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f18b5-132">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="f18b5-133">Hiermee definieert u welke .NET-verzamelings objecten worden uitgevouwen door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="f18b5-133">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f18b5-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f18b5-134">Remarks</span></span>

<span data-ttu-id="f18b5-135">Voor elke definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="f18b5-135">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="f18b5-136">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="f18b5-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f18b5-137">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="f18b5-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f18b5-138">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f18b5-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f18b5-139">Zie voor [waarden definiëren voor Diplaying-gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="f18b5-139">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f18b5-140">Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="f18b5-140">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f18b5-141">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f18b5-141">See Also</span></span>

[<span data-ttu-id="f18b5-142">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="f18b5-142">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f18b5-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f18b5-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
