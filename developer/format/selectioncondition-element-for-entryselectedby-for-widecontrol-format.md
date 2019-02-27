---
title: SelectionCondition-Element voor EntrySelectedBy voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845491"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="00d82-102">Het element SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="00d82-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="00d82-103">Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="00d82-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="00d82-104">Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor de definitie van een breed vermelding.</span><span class="sxs-lookup"><span data-stu-id="00d82-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="00d82-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="00d82-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00d82-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="00d82-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="00d82-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="00d82-107">Attributes and Elements</span></span>

<span data-ttu-id="00d82-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="00d82-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="00d82-109">U moet een enkel `PropertyName` of `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="00d82-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="00d82-110">De `SelectionSetName` en `TypeName` elementen zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="00d82-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="00d82-111">U kunt een van beide element opgeven.</span><span class="sxs-lookup"><span data-stu-id="00d82-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00d82-112">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="00d82-112">Attributes</span></span>

<span data-ttu-id="00d82-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="00d82-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00d82-114">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="00d82-114">Child Elements</span></span>

|<span data-ttu-id="00d82-115">Element</span><span class="sxs-lookup"><span data-stu-id="00d82-115">Element</span></span>|<span data-ttu-id="00d82-116">Description</span><span class="sxs-lookup"><span data-stu-id="00d82-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00d82-117">PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="00d82-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="00d82-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="00d82-118">Optional element.</span></span><br /><br /> <span data-ttu-id="00d82-119">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="00d82-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="00d82-120">ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="00d82-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="00d82-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="00d82-121">Optional element.</span></span><br /><br /> <span data-ttu-id="00d82-122">Hiermee geeft u het scriptblok waarmee de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="00d82-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="00d82-123">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="00d82-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="00d82-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="00d82-124">Optional element.</span></span><br /><br /> <span data-ttu-id="00d82-125">Hiermee geeft u de set van .NET-typen die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="00d82-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="00d82-126">TypeName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="00d82-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="00d82-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="00d82-127">Optional element.</span></span><br /><br /> <span data-ttu-id="00d82-128">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="00d82-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="00d82-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="00d82-129">Parent Elements</span></span>

|<span data-ttu-id="00d82-130">Element</span><span class="sxs-lookup"><span data-stu-id="00d82-130">Element</span></span>|<span data-ttu-id="00d82-131">Description</span><span class="sxs-lookup"><span data-stu-id="00d82-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00d82-132">EntrySelectedBy-Element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="00d82-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="00d82-133">Hiermee definieert u de .NET-typen die gebruikmaken van deze vermelding breed of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="00d82-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="00d82-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="00d82-134">Remarks</span></span>

<span data-ttu-id="00d82-135">Elk item wide moet ten minste één typenaam, selectie instellen of selectievoorwaarde gedefinieerd hebben.</span><span class="sxs-lookup"><span data-stu-id="00d82-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="00d82-136">Wanneer u een selectievoorwaarde definieert, wordt de volgende vereisten gelden:</span><span class="sxs-lookup"><span data-stu-id="00d82-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="00d82-137">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een scriptblok opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="00d82-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="00d82-138">De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="00d82-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="00d82-139">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="00d82-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="00d82-140">Zie voor meer informatie over andere onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="00d82-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00d82-141">Zie ook</span><span class="sxs-lookup"><span data-stu-id="00d82-141">See Also</span></span>

[<span data-ttu-id="00d82-142">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="00d82-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="00d82-143">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="00d82-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="00d82-144">EntrySelectedBy-Element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="00d82-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="00d82-145">PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="00d82-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="00d82-146">ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="00d82-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="00d82-147">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="00d82-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="00d82-148">TypeName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="00d82-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="00d82-149">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="00d82-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
