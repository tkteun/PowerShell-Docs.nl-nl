---
title: SelectionCondition-element voor EntrySelectedBy voor WideControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4115ad1ee8729ea4fc16bc19698018d2f4ed9be1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772702"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="8ce84-102">Het element SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8ce84-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="8ce84-103">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8ce84-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="8ce84-104">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een definitie van een brede vermelding.</span><span class="sxs-lookup"><span data-stu-id="8ce84-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="8ce84-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="8ce84-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8ce84-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8ce84-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8ce84-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="8ce84-107">Attributes and Elements</span></span>

<span data-ttu-id="8ce84-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="8ce84-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="8ce84-109">U moet één `PropertyName` element of opgeven `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="8ce84-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="8ce84-110">De `SelectionSetName` `TypeName` elementen en zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="8ce84-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="8ce84-111">U kunt een van beide elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="8ce84-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ce84-112">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8ce84-112">Attributes</span></span>

<span data-ttu-id="8ce84-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="8ce84-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8ce84-114">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8ce84-114">Child Elements</span></span>

|<span data-ttu-id="8ce84-115">Element</span><span class="sxs-lookup"><span data-stu-id="8ce84-115">Element</span></span>|<span data-ttu-id="8ce84-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8ce84-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ce84-117">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8ce84-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="8ce84-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8ce84-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8ce84-119">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8ce84-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8ce84-120">Script block-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="8ce84-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="8ce84-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8ce84-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8ce84-122">Hiermee geeft u het script blok op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8ce84-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="8ce84-123">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8ce84-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="8ce84-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8ce84-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8ce84-125">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8ce84-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="8ce84-126">TypeName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="8ce84-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="8ce84-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8ce84-127">Optional element.</span></span><br /><br /> <span data-ttu-id="8ce84-128">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8ce84-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8ce84-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8ce84-129">Parent Elements</span></span>

|<span data-ttu-id="8ce84-130">Element</span><span class="sxs-lookup"><span data-stu-id="8ce84-130">Element</span></span>|<span data-ttu-id="8ce84-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8ce84-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ce84-132">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8ce84-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="8ce84-133">Hiermee definieert u de .NET-typen die gebruikmaken van deze brede vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="8ce84-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8ce84-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8ce84-134">Remarks</span></span>

<span data-ttu-id="8ce84-135">Voor elke uitgebreide vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="8ce84-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8ce84-136">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="8ce84-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="8ce84-137">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="8ce84-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="8ce84-138">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="8ce84-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="8ce84-139">Zie voor [waarden definiëren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="8ce84-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8ce84-140">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="8ce84-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ce84-141">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8ce84-141">See Also</span></span>

[<span data-ttu-id="8ce84-142">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="8ce84-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8ce84-143">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="8ce84-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8ce84-144">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8ce84-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="8ce84-145">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8ce84-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="8ce84-146">Script block-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="8ce84-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="8ce84-147">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8ce84-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="8ce84-148">TypeName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="8ce84-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="8ce84-149">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="8ce84-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
