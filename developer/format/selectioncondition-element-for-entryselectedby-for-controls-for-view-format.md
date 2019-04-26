---
title: SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064226"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="44698-102">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="44698-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="44698-103">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="44698-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="44698-104">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="44698-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="44698-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor besturingselementen voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) EntrySelectedBy Element voor CustomEntry voor besturingselementen voor weergave (indeling) SelectionCondition Element voor EntrySelectedBy voor besturingselementen voor weergave ( -Indeling)</span><span class="sxs-lookup"><span data-stu-id="44698-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="44698-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="44698-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="44698-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="44698-107">Attributes and Elements</span></span>

<span data-ttu-id="44698-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="44698-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="44698-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="44698-109">Attributes</span></span>

<span data-ttu-id="44698-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="44698-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="44698-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="44698-111">Child Elements</span></span>

|<span data-ttu-id="44698-112">Element</span><span class="sxs-lookup"><span data-stu-id="44698-112">Element</span></span>|<span data-ttu-id="44698-113">Description</span><span class="sxs-lookup"><span data-stu-id="44698-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="44698-114">PropertyName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="44698-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="44698-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="44698-115">Optional element.</span></span><br /><br /> <span data-ttu-id="44698-116">Hiermee geeft u een .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="44698-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="44698-117">ScriptBlock-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="44698-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="44698-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="44698-118">Optional element.</span></span><br /><br /> <span data-ttu-id="44698-119">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="44698-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="44698-120">SelectionSetName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="44698-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="44698-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="44698-121">Optional element.</span></span><br /><br /> <span data-ttu-id="44698-122">Hiermee geeft u de set van .NET-typen die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="44698-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="44698-123">TypeName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="44698-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="44698-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="44698-124">Optional element.</span></span><br /><br /> <span data-ttu-id="44698-125">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="44698-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="44698-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="44698-126">Parent Elements</span></span>

|<span data-ttu-id="44698-127">Element</span><span class="sxs-lookup"><span data-stu-id="44698-127">Element</span></span>|<span data-ttu-id="44698-128">Description</span><span class="sxs-lookup"><span data-stu-id="44698-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="44698-129">EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="44698-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="44698-130">Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="44698-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="44698-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="44698-131">Remarks</span></span>

<span data-ttu-id="44698-132">Wanneer u een selectievoorwaarde definieert, wordt de volgende vereisten gelden:</span><span class="sxs-lookup"><span data-stu-id="44698-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="44698-133">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een scriptblok opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="44698-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="44698-134">De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="44698-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="44698-135">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="44698-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44698-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="44698-136">See Also</span></span>

[<span data-ttu-id="44698-137">PropertyName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="44698-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="44698-138">ScriptBlock-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="44698-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="44698-139">SelectionSetName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="44698-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="44698-140">TypeName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="44698-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="44698-141">EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="44698-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="44698-142">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="44698-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
