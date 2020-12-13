---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)
ms.openlocfilehash: 22f304615c6433ffb67f3b4046b645d0c37be8a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645769"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="e0b94-103">Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e0b94-103">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="e0b94-104">Hiermee definieert u de voor waarde die moet bestaan om te gebruiken voor deze definitie van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="e0b94-104">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="e0b94-105">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een tabel definitie.</span><span class="sxs-lookup"><span data-stu-id="e0b94-105">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="e0b94-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element voor TableRowEntry (Format) SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0b94-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0b94-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0b94-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0b94-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e0b94-108">Attributes and Elements</span></span>

<span data-ttu-id="e0b94-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element SelectionCondition beschreven.</span><span class="sxs-lookup"><span data-stu-id="e0b94-109">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0b94-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e0b94-110">Attributes</span></span>

<span data-ttu-id="e0b94-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="e0b94-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0b94-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e0b94-112">Child Elements</span></span>

|<span data-ttu-id="e0b94-113">Element</span><span class="sxs-lookup"><span data-stu-id="e0b94-113">Element</span></span>|<span data-ttu-id="e0b94-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e0b94-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0b94-115">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e0b94-115">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="e0b94-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e0b94-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e0b94-117">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e0b94-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e0b94-118">Script block-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0b94-118">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e0b94-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e0b94-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e0b94-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e0b94-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="e0b94-121">SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0b94-121">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e0b94-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e0b94-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e0b94-123">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e0b94-123">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="e0b94-124">TypeName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0b94-124">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e0b94-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e0b94-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e0b94-126">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e0b94-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e0b94-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e0b94-127">Parent Elements</span></span>

|<span data-ttu-id="e0b94-128">Element</span><span class="sxs-lookup"><span data-stu-id="e0b94-128">Element</span></span>|<span data-ttu-id="e0b94-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e0b94-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0b94-130">EntrySelectedBy-element voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0b94-130">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="e0b94-131">Hiermee definieert u de .NET-typen die gebruikmaken van deze tabel vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="e0b94-131">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0b94-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e0b94-132">Remarks</span></span>

<span data-ttu-id="e0b94-133">Voor elke lijst vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e0b94-133">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e0b94-134">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="e0b94-134">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="e0b94-135">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="e0b94-135">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="e0b94-136">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e0b94-136">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="e0b94-137">Zie voor [waarden definiëren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="e0b94-137">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e0b94-138">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="e0b94-138">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0b94-139">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e0b94-139">See Also</span></span>

[<span data-ttu-id="e0b94-140">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="e0b94-140">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e0b94-141">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="e0b94-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e0b94-142">EntrySelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0b94-142">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="e0b94-143">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e0b94-143">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="e0b94-144">Script block-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0b94-144">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e0b94-145">SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0b94-145">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e0b94-146">TypeName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0b94-146">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e0b94-147">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e0b94-147">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
