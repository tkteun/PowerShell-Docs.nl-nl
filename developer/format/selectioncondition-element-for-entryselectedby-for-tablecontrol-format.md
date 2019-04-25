---
title: SelectionCondition-Element voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075661"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="a3fa2-102">Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="a3fa2-103">Hiermee definieert u de voorwaarde die moet aanwezig zijn als u wilt gebruiken voor deze definitie van de tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="a3fa2-104">Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor de tabeldefinitie van een.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="a3fa2-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy Element voor TableRowEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a3fa2-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a3fa2-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a3fa2-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a3fa2-107">Attributes and Elements</span></span>

<span data-ttu-id="a3fa2-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van het element SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a3fa2-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a3fa2-109">Attributes</span></span>

<span data-ttu-id="a3fa2-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a3fa2-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a3fa2-111">Child Elements</span></span>

|<span data-ttu-id="a3fa2-112">Element</span><span class="sxs-lookup"><span data-stu-id="a3fa2-112">Element</span></span>|<span data-ttu-id="a3fa2-113">Description</span><span class="sxs-lookup"><span data-stu-id="a3fa2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3fa2-114">PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="a3fa2-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a3fa2-116">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a3fa2-117">ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a3fa2-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a3fa2-119">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a3fa2-120">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a3fa2-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a3fa2-122">Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="a3fa2-123">TypeName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a3fa2-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a3fa2-125">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a3fa2-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a3fa2-126">Parent Elements</span></span>

|<span data-ttu-id="a3fa2-127">Element</span><span class="sxs-lookup"><span data-stu-id="a3fa2-127">Element</span></span>|<span data-ttu-id="a3fa2-128">Description</span><span class="sxs-lookup"><span data-stu-id="a3fa2-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3fa2-129">EntrySelectedBy-Element voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="a3fa2-130">Hiermee definieert u de .NET-typen die gebruikmaken van de vermelding in deze tabel of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a3fa2-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a3fa2-131">Remarks</span></span>

<span data-ttu-id="a3fa2-132">Elk lijstitem moet hebben ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="a3fa2-133">Wanneer u een selectievoorwaarde definieert, wordt de volgende vereisten gelden:</span><span class="sxs-lookup"><span data-stu-id="a3fa2-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a3fa2-134">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een scriptblok opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a3fa2-135">De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="a3fa2-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a3fa2-136">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a3fa2-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a3fa2-137">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a3fa2-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a3fa2-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a3fa2-138">See Also</span></span>

[<span data-ttu-id="a3fa2-139">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="a3fa2-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a3fa2-140">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="a3fa2-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a3fa2-141">EntrySelectedBy-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="a3fa2-142">PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="a3fa2-143">ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a3fa2-144">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a3fa2-145">TypeName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3fa2-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a3fa2-146">Schrijven van een Windows PowerShell opmaak en het bestand van het type</span><span class="sxs-lookup"><span data-stu-id="a3fa2-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
