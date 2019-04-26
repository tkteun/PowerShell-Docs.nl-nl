---
title: EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066223"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="f5f5e-102">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f5f5e-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="f5f5e-103">Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="f5f5e-104">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f5f5e-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) EntrySelectedBy Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="f5f5e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5f5e-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f5f5e-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5f5e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f5f5e-107">Attributes and Elements</span></span>

<span data-ttu-id="f5f5e-108">De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="f5f5e-109">U moet ten minste één type, selectie instellen of selectievoorwaarde voor een definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="f5f5e-110">Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5f5e-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f5f5e-111">Attributes</span></span>

<span data-ttu-id="f5f5e-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5f5e-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f5f5e-113">Child Elements</span></span>

|<span data-ttu-id="f5f5e-114">Element</span><span class="sxs-lookup"><span data-stu-id="f5f5e-114">Element</span></span>|<span data-ttu-id="f5f5e-115">Description</span><span class="sxs-lookup"><span data-stu-id="f5f5e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5f5e-116">SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="f5f5e-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="f5f5e-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="f5f5e-118">Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="f5f5e-119">SelectionSetName-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="f5f5e-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="f5f5e-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="f5f5e-121">Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="f5f5e-122">TypeName-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="f5f5e-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="f5f5e-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-123">Optional element.</span></span><br /><br /> <span data-ttu-id="f5f5e-124">Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f5f5e-125">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f5f5e-125">Parent Elements</span></span>

|<span data-ttu-id="f5f5e-126">Element</span><span class="sxs-lookup"><span data-stu-id="f5f5e-126">Element</span></span>|<span data-ttu-id="f5f5e-127">Description</span><span class="sxs-lookup"><span data-stu-id="f5f5e-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5f5e-128">CustomEntry-Element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="f5f5e-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="f5f5e-129">Bevat een definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f5f5e-130">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f5f5e-130">Remarks</span></span>

<span data-ttu-id="f5f5e-131">Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde moet bestaan voor de definitie moet worden gebruikt, bijvoorbeeld wanneer een object een bepaalde eigenschap heeft of wanneer de waarde van een bepaalde eigenschap of script wordt geëvalueerd als `true`.</span><span class="sxs-lookup"><span data-stu-id="f5f5e-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="f5f5e-132">Zie voor meer informatie over de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f5f5e-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5f5e-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f5f5e-133">See Also</span></span>

[<span data-ttu-id="f5f5e-134">SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="f5f5e-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="f5f5e-135">SelectionSetName-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="f5f5e-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="f5f5e-136">TypeName-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="f5f5e-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="f5f5e-137">CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="f5f5e-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="f5f5e-138">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5f5e-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
