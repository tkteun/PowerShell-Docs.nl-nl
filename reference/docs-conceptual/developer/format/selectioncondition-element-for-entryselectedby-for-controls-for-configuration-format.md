---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: ce00cdf868a3075875043aeb59f2cb8a17d049a9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645784"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="7228b-103">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7228b-103">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7228b-104">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een algemene definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="7228b-104">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="7228b-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="7228b-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7228b-106">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor besturings elementen voor configuratie (Format) CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (Format) SelectionCondition-element voor EntrySelectedBy voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="7228b-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7228b-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="7228b-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7228b-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7228b-108">Attributes and Elements</span></span>

<span data-ttu-id="7228b-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="7228b-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7228b-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7228b-110">Attributes</span></span>

<span data-ttu-id="7228b-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="7228b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7228b-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7228b-112">Child Elements</span></span>

|<span data-ttu-id="7228b-113">Element</span><span class="sxs-lookup"><span data-stu-id="7228b-113">Element</span></span>|<span data-ttu-id="7228b-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7228b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7228b-115">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7228b-115">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7228b-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7228b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="7228b-117">Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7228b-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="7228b-118">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7228b-118">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7228b-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7228b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="7228b-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7228b-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="7228b-121">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7228b-121">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7228b-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7228b-122">Optional element.</span></span><br /><br /> <span data-ttu-id="7228b-123">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7228b-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="7228b-124">Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7228b-124">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7228b-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7228b-125">Optional element.</span></span><br /><br /> <span data-ttu-id="7228b-126">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7228b-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7228b-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7228b-127">Parent Elements</span></span>

|<span data-ttu-id="7228b-128">Element</span><span class="sxs-lookup"><span data-stu-id="7228b-128">Element</span></span>|<span data-ttu-id="7228b-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7228b-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7228b-130">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7228b-130">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="7228b-131">Hiermee worden de .NET-typen gedefinieerd die dit item van de algemene besturings definitie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7228b-131">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7228b-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7228b-132">Remarks</span></span>

<span data-ttu-id="7228b-133">De volgende richt lijnen moeten worden gevolgd bij het definiëren van een selectie voorwaarde:</span><span class="sxs-lookup"><span data-stu-id="7228b-133">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="7228b-134">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="7228b-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="7228b-135">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7228b-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="7228b-136">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7228b-136">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7228b-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7228b-137">See Also</span></span>

[<span data-ttu-id="7228b-138">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7228b-138">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7228b-139">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7228b-139">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7228b-140">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7228b-140">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7228b-141">Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7228b-141">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7228b-142">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7228b-142">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="7228b-143">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7228b-143">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
