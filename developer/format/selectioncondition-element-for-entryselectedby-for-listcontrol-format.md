---
title: SelectionCondition-Element voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: f04a07c241268566eaedfe2b299c33d5be4dc19d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735083"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="11d5b-102">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="11d5b-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="11d5b-103">Hiermee definieert u de voorwaarde die moet bestaan voor het gebruik van deze definitie van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="11d5b-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="11d5b-104">Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor de Lijstdefinitie van een.</span><span class="sxs-lookup"><span data-stu-id="11d5b-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="11d5b-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling) EntrySelectedBy Element voor ListEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="11d5b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11d5b-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="11d5b-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11d5b-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="11d5b-107">Attributes and Elements</span></span>

<span data-ttu-id="11d5b-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="11d5b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11d5b-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="11d5b-109">Attributes</span></span>

<span data-ttu-id="11d5b-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="11d5b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11d5b-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="11d5b-111">Child Elements</span></span>

|<span data-ttu-id="11d5b-112">Element</span><span class="sxs-lookup"><span data-stu-id="11d5b-112">Element</span></span>|<span data-ttu-id="11d5b-113">Description</span><span class="sxs-lookup"><span data-stu-id="11d5b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11d5b-114">PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="11d5b-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="11d5b-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="11d5b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="11d5b-116">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="11d5b-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="11d5b-117">ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="11d5b-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="11d5b-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="11d5b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="11d5b-119">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="11d5b-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="11d5b-120">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="11d5b-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="11d5b-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="11d5b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="11d5b-122">Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="11d5b-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="11d5b-123">TypeName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="11d5b-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="11d5b-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="11d5b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="11d5b-125">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="11d5b-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="11d5b-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="11d5b-126">Parent Elements</span></span>

|<span data-ttu-id="11d5b-127">Element</span><span class="sxs-lookup"><span data-stu-id="11d5b-127">Element</span></span>|<span data-ttu-id="11d5b-128">Description</span><span class="sxs-lookup"><span data-stu-id="11d5b-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11d5b-129">EntrySelectedBy-Element voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="11d5b-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="11d5b-130">Hiermee definieert u de .NET-typen die gebruikmaken van de vermelding in deze tabel of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="11d5b-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="11d5b-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="11d5b-131">Remarks</span></span>

<span data-ttu-id="11d5b-132">lWhen definieert u een selectievoorwaarde, gelden voor de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="11d5b-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="11d5b-133">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een scriptblok opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="11d5b-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="11d5b-134">De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="11d5b-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="11d5b-135">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="11d5b-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="11d5b-136">Zie voor meer informatie over andere onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="11d5b-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11d5b-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="11d5b-137">See Also</span></span>

[<span data-ttu-id="11d5b-138">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="11d5b-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="11d5b-139">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="11d5b-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="11d5b-140">ListEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="11d5b-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="11d5b-141">SelectionSetName-Element voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="11d5b-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="11d5b-142">TypeName-Element voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="11d5b-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="11d5b-143">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="11d5b-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
