---
title: SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358885"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="68ee8-102">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="68ee8-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="68ee8-103">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een definitie van een besturings element.</span><span class="sxs-lookup"><span data-stu-id="68ee8-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="68ee8-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="68ee8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="68ee8-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (indeling) EntrySelectedBy voor CustomEntry voor GroupBy (Format) SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="68ee8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68ee8-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="68ee8-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68ee8-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="68ee8-107">Attributes and Elements</span></span>

<span data-ttu-id="68ee8-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionCondition` beschreven.</span><span class="sxs-lookup"><span data-stu-id="68ee8-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="68ee8-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="68ee8-109">Attributes</span></span>

<span data-ttu-id="68ee8-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="68ee8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68ee8-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="68ee8-111">Child Elements</span></span>

|<span data-ttu-id="68ee8-112">Element</span><span class="sxs-lookup"><span data-stu-id="68ee8-112">Element</span></span>|<span data-ttu-id="68ee8-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="68ee8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68ee8-114">Het element PropertyName voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="68ee8-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="68ee8-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="68ee8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="68ee8-116">Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="68ee8-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="68ee8-117">Script block-element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="68ee8-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="68ee8-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="68ee8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="68ee8-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="68ee8-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="68ee8-120">SelectionSetName-element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="68ee8-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="68ee8-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="68ee8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="68ee8-122">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="68ee8-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="68ee8-123">TypeName-element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="68ee8-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="68ee8-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="68ee8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="68ee8-125">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="68ee8-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="68ee8-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="68ee8-126">Parent Elements</span></span>

|<span data-ttu-id="68ee8-127">Element</span><span class="sxs-lookup"><span data-stu-id="68ee8-127">Element</span></span>|<span data-ttu-id="68ee8-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="68ee8-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68ee8-129">EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="68ee8-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="68ee8-130">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="68ee8-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="68ee8-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="68ee8-131">Remarks</span></span>

<span data-ttu-id="68ee8-132">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="68ee8-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="68ee8-133">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="68ee8-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="68ee8-134">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="68ee8-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="68ee8-135">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="68ee8-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="68ee8-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="68ee8-136">See Also</span></span>

[<span data-ttu-id="68ee8-137">Het element PropertyName voor SelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="68ee8-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="68ee8-138">Script block-element voor SelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="68ee8-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="68ee8-139">SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="68ee8-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="68ee8-140">TypeName-element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="68ee8-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="68ee8-141">EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="68ee8-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="68ee8-142">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="68ee8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
