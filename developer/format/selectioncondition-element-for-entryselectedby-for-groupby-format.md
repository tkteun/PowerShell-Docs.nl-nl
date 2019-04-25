---
title: SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075712"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="254fc-102">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="254fc-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="254fc-103">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van een moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="254fc-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="254fc-104">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="254fc-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="254fc-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) EntrySelectedBy Element voor CustomEntry voor GroupBy (indeling) SelectionCondition Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="254fc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="254fc-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="254fc-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="254fc-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="254fc-107">Attributes and Elements</span></span>

<span data-ttu-id="254fc-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="254fc-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="254fc-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="254fc-109">Attributes</span></span>

<span data-ttu-id="254fc-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="254fc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="254fc-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="254fc-111">Child Elements</span></span>

|<span data-ttu-id="254fc-112">Element</span><span class="sxs-lookup"><span data-stu-id="254fc-112">Element</span></span>|<span data-ttu-id="254fc-113">Description</span><span class="sxs-lookup"><span data-stu-id="254fc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="254fc-114">PropertyName-Element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="254fc-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="254fc-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="254fc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="254fc-116">Hiermee geeft u een .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="254fc-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="254fc-117">ScriptBlock-Element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="254fc-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="254fc-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="254fc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="254fc-119">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="254fc-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="254fc-120">SelectionSetName-Element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="254fc-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="254fc-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="254fc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="254fc-122">Hiermee geeft u de set van .NET-typen die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="254fc-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="254fc-123">TypeName-Element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="254fc-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="254fc-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="254fc-124">Optional element.</span></span><br /><br /> <span data-ttu-id="254fc-125">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="254fc-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="254fc-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="254fc-126">Parent Elements</span></span>

|<span data-ttu-id="254fc-127">Element</span><span class="sxs-lookup"><span data-stu-id="254fc-127">Element</span></span>|<span data-ttu-id="254fc-128">Description</span><span class="sxs-lookup"><span data-stu-id="254fc-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="254fc-129">EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="254fc-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="254fc-130">Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="254fc-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="254fc-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="254fc-131">Remarks</span></span>

<span data-ttu-id="254fc-132">Wanneer u een selectievoorwaarde definieert, wordt de volgende vereisten gelden:</span><span class="sxs-lookup"><span data-stu-id="254fc-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="254fc-133">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een scriptblok opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="254fc-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="254fc-134">De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="254fc-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="254fc-135">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="254fc-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="254fc-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="254fc-136">See Also</span></span>

[<span data-ttu-id="254fc-137">PropertyName-Element voor SelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="254fc-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="254fc-138">ScriptBlock-Element voor SelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="254fc-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="254fc-139">SelectionSetName-Element voor SelectionCondition voor aangepaste besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="254fc-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="254fc-140">TypeName-Element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="254fc-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="254fc-141">EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="254fc-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="254fc-142">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="254fc-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
