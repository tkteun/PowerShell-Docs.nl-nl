---
title: SelectionCondition Element for EntrySelectedBy for ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 7150b29ad84dfb587215ee3e64c356adbd5a6305
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417533"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="1f6c6-102">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1f6c6-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="1f6c6-103">Defines the condition that must exist to use this definition of the list view.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="1f6c6-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="1f6c6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f6c6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f6c6-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1f6c6-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f6c6-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1f6c6-107">Attributes and Elements</span></span>

<span data-ttu-id="1f6c6-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f6c6-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1f6c6-109">Attributes</span></span>

<span data-ttu-id="1f6c6-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f6c6-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1f6c6-111">Child Elements</span></span>

|<span data-ttu-id="1f6c6-112">Element</span><span class="sxs-lookup"><span data-stu-id="1f6c6-112">Element</span></span>|<span data-ttu-id="1f6c6-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1f6c6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f6c6-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f6c6-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1f6c6-115">Optional element.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1f6c6-116">Specifies the .NET property that triggers the condition.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="1f6c6-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f6c6-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1f6c6-118">Optional element.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-118">Optional element.</span></span><br /><br /> <span data-ttu-id="1f6c6-119">Specifies the script that triggers the condition.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="1f6c6-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f6c6-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="1f6c6-121">Optional element.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-121">Optional element.</span></span><br /><br /> <span data-ttu-id="1f6c6-122">Specifies the set of .NET types that trigger the condition.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="1f6c6-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f6c6-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1f6c6-124">Optional element.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-124">Optional element.</span></span><br /><br /> <span data-ttu-id="1f6c6-125">Specifies a .NET type that triggers the condition.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1f6c6-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1f6c6-126">Parent Elements</span></span>

|<span data-ttu-id="1f6c6-127">Element</span><span class="sxs-lookup"><span data-stu-id="1f6c6-127">Element</span></span>|<span data-ttu-id="1f6c6-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1f6c6-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f6c6-129">EntrySelectedBy Element for TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f6c6-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="1f6c6-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f6c6-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1f6c6-131">Remarks</span></span>

<span data-ttu-id="1f6c6-132">lWhen you are defining a selection condition, the following requirements apply:</span><span class="sxs-lookup"><span data-stu-id="1f6c6-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="1f6c6-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="1f6c6-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span><span class="sxs-lookup"><span data-stu-id="1f6c6-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="1f6c6-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1f6c6-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1f6c6-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1f6c6-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f6c6-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1f6c6-137">See Also</span></span>

[<span data-ttu-id="1f6c6-138">Creating a List View</span><span class="sxs-lookup"><span data-stu-id="1f6c6-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1f6c6-139">Defining Conditions for When Data Is Displayed</span><span class="sxs-lookup"><span data-stu-id="1f6c6-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1f6c6-140">ListEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="1f6c6-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="1f6c6-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f6c6-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1f6c6-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f6c6-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="1f6c6-143">Writing a PowerShell Formatting File</span><span class="sxs-lookup"><span data-stu-id="1f6c6-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
