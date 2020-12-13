---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)
ms.openlocfilehash: 14c293b6bc6d6accc201de35be9219349079801d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664754"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="d25d6-103">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d25d6-103">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="d25d6-104">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een definitie van een besturings element.</span><span class="sxs-lookup"><span data-stu-id="d25d6-104">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="d25d6-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d25d6-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d25d6-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="d25d6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d25d6-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d25d6-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d25d6-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d25d6-108">Attributes and Elements</span></span>

<span data-ttu-id="d25d6-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d25d6-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d25d6-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d25d6-110">Attributes</span></span>

<span data-ttu-id="d25d6-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="d25d6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d25d6-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d25d6-112">Child Elements</span></span>

|<span data-ttu-id="d25d6-113">Element</span><span class="sxs-lookup"><span data-stu-id="d25d6-113">Element</span></span>|<span data-ttu-id="d25d6-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d25d6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d25d6-115">Het element PropertyName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d25d6-115">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="d25d6-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d25d6-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d25d6-117">Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="d25d6-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d25d6-118">Script block-element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="d25d6-118">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="d25d6-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d25d6-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d25d6-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="d25d6-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="d25d6-121">Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d25d6-121">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="d25d6-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d25d6-122">Optional element.</span></span><br /><br /> <span data-ttu-id="d25d6-123">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="d25d6-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="d25d6-124">TypeName-element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="d25d6-124">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="d25d6-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d25d6-125">Optional element.</span></span><br /><br /> <span data-ttu-id="d25d6-126">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="d25d6-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d25d6-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d25d6-127">Parent Elements</span></span>

|<span data-ttu-id="d25d6-128">Element</span><span class="sxs-lookup"><span data-stu-id="d25d6-128">Element</span></span>|<span data-ttu-id="d25d6-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d25d6-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d25d6-130">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d25d6-130">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="d25d6-131">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d25d6-131">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d25d6-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d25d6-132">Remarks</span></span>

<span data-ttu-id="d25d6-133">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="d25d6-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="d25d6-134">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="d25d6-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="d25d6-135">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d25d6-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="d25d6-136">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="d25d6-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d25d6-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d25d6-137">See Also</span></span>

[<span data-ttu-id="d25d6-138">Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d25d6-138">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d25d6-139">Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d25d6-139">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d25d6-140">SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d25d6-140">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d25d6-141">TypeName-element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="d25d6-141">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="d25d6-142">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d25d6-142">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="d25d6-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d25d6-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
