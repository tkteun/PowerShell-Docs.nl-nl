---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)
ms.openlocfilehash: e93499691dd0046265e43abd26497b2974546083
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655102"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="6989e-103">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6989e-103">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="6989e-104">Hiermee definieert u de voor waarde die moet bestaan om deze definitie van de lijst weergave te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6989e-104">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="6989e-105">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een lijst definitie.</span><span class="sxs-lookup"><span data-stu-id="6989e-105">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="6989e-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type element (indeling) EntrySelectedBy element (Format) element list item (Format) voor List entry (Format) SelectionCondition element voor de List entry (Format)</span><span class="sxs-lookup"><span data-stu-id="6989e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6989e-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="6989e-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6989e-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6989e-108">Attributes and Elements</span></span>

<span data-ttu-id="6989e-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="6989e-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6989e-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6989e-110">Attributes</span></span>

<span data-ttu-id="6989e-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="6989e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6989e-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6989e-112">Child Elements</span></span>

|<span data-ttu-id="6989e-113">Element</span><span class="sxs-lookup"><span data-stu-id="6989e-113">Element</span></span>|<span data-ttu-id="6989e-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6989e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6989e-115">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6989e-115">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="6989e-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6989e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6989e-117">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6989e-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="6989e-118">Script block-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6989e-118">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="6989e-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6989e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="6989e-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6989e-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="6989e-121">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6989e-121">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="6989e-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6989e-122">Optional element.</span></span><br /><br /> <span data-ttu-id="6989e-123">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6989e-123">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="6989e-124">TypeName-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6989e-124">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="6989e-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6989e-125">Optional element.</span></span><br /><br /> <span data-ttu-id="6989e-126">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6989e-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6989e-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6989e-127">Parent Elements</span></span>

|<span data-ttu-id="6989e-128">Element</span><span class="sxs-lookup"><span data-stu-id="6989e-128">Element</span></span>|<span data-ttu-id="6989e-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6989e-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6989e-130">EntrySelectedBy-element voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6989e-130">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="6989e-131">Hiermee definieert u de .NET-typen die gebruikmaken van deze tabel vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="6989e-131">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6989e-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6989e-132">Remarks</span></span>

<span data-ttu-id="6989e-133">lWhen u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="6989e-133">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="6989e-134">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6989e-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="6989e-135">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6989e-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="6989e-136">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="6989e-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6989e-137">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over andere onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="6989e-137">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6989e-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6989e-138">See Also</span></span>

[<span data-ttu-id="6989e-139">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="6989e-139">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6989e-140">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="6989e-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6989e-141">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6989e-141">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="6989e-142">SelectionSetName-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6989e-142">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="6989e-143">TypeName-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6989e-143">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="6989e-144">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="6989e-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
