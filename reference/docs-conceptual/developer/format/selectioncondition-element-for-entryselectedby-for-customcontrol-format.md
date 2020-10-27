---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor CustomControl (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor CustomControl (opmaak)
ms.openlocfilehash: 6d4cc5a2d5fef0445d586e320b3729d3a7044063
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649770"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="47bc4-103">Het element SelectionCondition voor EntrySelectedBy voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="47bc4-103">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="47bc4-104">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een definitie van een besturings element.</span><span class="sxs-lookup"><span data-stu-id="47bc4-104">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="47bc4-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="47bc4-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="47bc4-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (Format) CustomControl element voor weer gave (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor het object CustomControl voor weer gave (Format) EntrySelectedBy voor CustomEntry</span><span class="sxs-lookup"><span data-stu-id="47bc4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="47bc4-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="47bc4-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47bc4-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="47bc4-108">Attributes and Elements</span></span>

<span data-ttu-id="47bc4-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="47bc4-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="47bc4-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="47bc4-110">Attributes</span></span>

<span data-ttu-id="47bc4-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="47bc4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47bc4-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="47bc4-112">Child Elements</span></span>

|<span data-ttu-id="47bc4-113">Element</span><span class="sxs-lookup"><span data-stu-id="47bc4-113">Element</span></span>|<span data-ttu-id="47bc4-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="47bc4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47bc4-115">Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="47bc4-115">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="47bc4-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="47bc4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="47bc4-117">Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="47bc4-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="47bc4-118">Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="47bc4-118">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="47bc4-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="47bc4-119">Optional element.</span></span><br /><br /> <span data-ttu-id="47bc4-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="47bc4-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="47bc4-121">SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="47bc4-121">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="47bc4-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="47bc4-122">Optional element.</span></span><br /><br /> <span data-ttu-id="47bc4-123">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="47bc4-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="47bc4-124">Het element TypeName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="47bc4-124">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="47bc4-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="47bc4-125">Optional element.</span></span><br /><br /> <span data-ttu-id="47bc4-126">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="47bc4-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="47bc4-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="47bc4-127">Parent Elements</span></span>

|<span data-ttu-id="47bc4-128">Element</span><span class="sxs-lookup"><span data-stu-id="47bc4-128">Element</span></span>|<span data-ttu-id="47bc4-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="47bc4-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47bc4-130">Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="47bc4-130">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="47bc4-131">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="47bc4-131">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="47bc4-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="47bc4-132">Remarks</span></span>

<span data-ttu-id="47bc4-133">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="47bc4-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="47bc4-134">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="47bc4-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="47bc4-135">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="47bc4-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="47bc4-136">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="47bc4-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="47bc4-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="47bc4-137">See Also</span></span>

[<span data-ttu-id="47bc4-138">Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="47bc4-138">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="47bc4-139">Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="47bc4-139">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="47bc4-140">SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="47bc4-140">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="47bc4-141">Het element TypeName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="47bc4-141">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="47bc4-142">Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="47bc4-142">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="47bc4-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="47bc4-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
