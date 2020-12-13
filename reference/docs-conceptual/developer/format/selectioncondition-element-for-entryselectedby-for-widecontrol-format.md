---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)
ms.openlocfilehash: 8c51ca72edc6ad174dc289c61a8987e8f9495d19
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655109"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="2f276-103">Het element SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2f276-103">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="2f276-104">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2f276-104">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="2f276-105">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een definitie van een brede vermelding.</span><span class="sxs-lookup"><span data-stu-id="2f276-105">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="2f276-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="2f276-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2f276-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="2f276-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f276-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2f276-108">Attributes and Elements</span></span>

<span data-ttu-id="2f276-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="2f276-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="2f276-110">U moet één `PropertyName` element of opgeven `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="2f276-110">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="2f276-111">De `SelectionSetName` `TypeName` elementen en zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="2f276-111">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="2f276-112">U kunt een van beide elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="2f276-112">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f276-113">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2f276-113">Attributes</span></span>

<span data-ttu-id="2f276-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="2f276-114">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f276-115">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2f276-115">Child Elements</span></span>

|<span data-ttu-id="2f276-116">Element</span><span class="sxs-lookup"><span data-stu-id="2f276-116">Element</span></span>|<span data-ttu-id="2f276-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2f276-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f276-118">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2f276-118">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="2f276-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2f276-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2f276-120">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="2f276-120">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2f276-121">Script block-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="2f276-121">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="2f276-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2f276-122">Optional element.</span></span><br /><br /> <span data-ttu-id="2f276-123">Hiermee geeft u het script blok op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="2f276-123">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="2f276-124">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2f276-124">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="2f276-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2f276-125">Optional element.</span></span><br /><br /> <span data-ttu-id="2f276-126">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="2f276-126">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="2f276-127">TypeName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="2f276-127">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="2f276-128">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2f276-128">Optional element.</span></span><br /><br /> <span data-ttu-id="2f276-129">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="2f276-129">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2f276-130">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2f276-130">Parent Elements</span></span>

|<span data-ttu-id="2f276-131">Element</span><span class="sxs-lookup"><span data-stu-id="2f276-131">Element</span></span>|<span data-ttu-id="2f276-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2f276-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f276-133">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2f276-133">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="2f276-134">Hiermee definieert u de .NET-typen die gebruikmaken van deze brede vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="2f276-134">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2f276-135">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2f276-135">Remarks</span></span>

<span data-ttu-id="2f276-136">Voor elke uitgebreide vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2f276-136">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2f276-137">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="2f276-137">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="2f276-138">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="2f276-138">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="2f276-139">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2f276-139">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="2f276-140">Zie voor [waarden definiëren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="2f276-140">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2f276-141">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="2f276-141">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f276-142">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2f276-142">See Also</span></span>

[<span data-ttu-id="2f276-143">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="2f276-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2f276-144">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="2f276-144">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2f276-145">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2f276-145">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="2f276-146">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2f276-146">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="2f276-147">Script block-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="2f276-147">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2f276-148">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2f276-148">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="2f276-149">TypeName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="2f276-149">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2f276-150">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2f276-150">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
