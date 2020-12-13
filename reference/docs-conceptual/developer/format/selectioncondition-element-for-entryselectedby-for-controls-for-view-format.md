---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 16b048e73195b3d6168724714ff223851dc1b20b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664849"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="26894-103">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26894-103">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="26894-104">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="26894-104">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="26894-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="26894-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="26894-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy voor besturings elementen</span><span class="sxs-lookup"><span data-stu-id="26894-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26894-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="26894-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26894-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="26894-108">Attributes and Elements</span></span>

<span data-ttu-id="26894-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="26894-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="26894-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="26894-110">Attributes</span></span>

<span data-ttu-id="26894-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="26894-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26894-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="26894-112">Child Elements</span></span>

|<span data-ttu-id="26894-113">Element</span><span class="sxs-lookup"><span data-stu-id="26894-113">Element</span></span>|<span data-ttu-id="26894-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="26894-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26894-115">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26894-115">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="26894-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="26894-116">Optional element.</span></span><br /><br /> <span data-ttu-id="26894-117">Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="26894-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="26894-118">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26894-118">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="26894-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="26894-119">Optional element.</span></span><br /><br /> <span data-ttu-id="26894-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="26894-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="26894-121">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26894-121">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="26894-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="26894-122">Optional element.</span></span><br /><br /> <span data-ttu-id="26894-123">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="26894-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="26894-124">Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26894-124">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="26894-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="26894-125">Optional element.</span></span><br /><br /> <span data-ttu-id="26894-126">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="26894-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="26894-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="26894-127">Parent Elements</span></span>

|<span data-ttu-id="26894-128">Element</span><span class="sxs-lookup"><span data-stu-id="26894-128">Element</span></span>|<span data-ttu-id="26894-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="26894-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26894-130">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26894-130">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="26894-131">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="26894-131">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="26894-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="26894-132">Remarks</span></span>

<span data-ttu-id="26894-133">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="26894-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="26894-134">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="26894-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="26894-135">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="26894-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="26894-136">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="26894-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26894-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="26894-137">See Also</span></span>

[<span data-ttu-id="26894-138">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26894-138">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="26894-139">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26894-139">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="26894-140">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26894-140">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="26894-141">Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26894-141">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="26894-142">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26894-142">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="26894-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="26894-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
