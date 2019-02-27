---
title: EntrySelectedBy-Element voor CustomEntry voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849320"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="cfc39-102">Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cfc39-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="cfc39-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cfc39-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="cfc39-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor EntrySelectedBy weergeven (indeling) Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cfc39-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cfc39-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="cfc39-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cfc39-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="cfc39-106">Attributes and Elements</span></span>

<span data-ttu-id="cfc39-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="cfc39-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cfc39-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="cfc39-108">Attributes</span></span>

<span data-ttu-id="cfc39-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="cfc39-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cfc39-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cfc39-110">Child Elements</span></span>

|<span data-ttu-id="cfc39-111">Element</span><span class="sxs-lookup"><span data-stu-id="cfc39-111">Element</span></span>|<span data-ttu-id="cfc39-112">Description</span><span class="sxs-lookup"><span data-stu-id="cfc39-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cfc39-113">SelectionCondition-Element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="cfc39-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="cfc39-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cfc39-114">Optional element.</span></span><br /><br /> <span data-ttu-id="cfc39-115">Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cfc39-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="cfc39-116">SelectionSetName-Element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="cfc39-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="cfc39-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cfc39-117">Optional element.</span></span><br /><br /> <span data-ttu-id="cfc39-118">Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie van de weergave beheer.</span><span class="sxs-lookup"><span data-stu-id="cfc39-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="cfc39-119">TypeName-Element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="cfc39-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="cfc39-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cfc39-120">Optional element.</span></span><br /><br /> <span data-ttu-id="cfc39-121">Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van de weergave beheer.</span><span class="sxs-lookup"><span data-stu-id="cfc39-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cfc39-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cfc39-122">Parent Elements</span></span>

|<span data-ttu-id="cfc39-123">Element</span><span class="sxs-lookup"><span data-stu-id="cfc39-123">Element</span></span>|<span data-ttu-id="cfc39-124">Description</span><span class="sxs-lookup"><span data-stu-id="cfc39-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cfc39-125">CustomEntry-Element voor CustomEntries voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cfc39-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="cfc39-126">Hiermee definieert u de besturingselementen die worden gebruikt door specifieke .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="cfc39-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cfc39-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cfc39-127">Remarks</span></span>

<span data-ttu-id="cfc39-128">U moet ten minste één type, selectie instellen of selectievoorwaarde voor een vermelding opgeven.</span><span class="sxs-lookup"><span data-stu-id="cfc39-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="cfc39-129">Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cfc39-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="cfc39-130">Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde moet bestaan voor de vermelding moet worden gebruikt, bijvoorbeeld wanneer een object een bepaalde eigenschap heeft of wanneer de waarde van een bepaalde eigenschap of script wordt geëvalueerd als `true`.</span><span class="sxs-lookup"><span data-stu-id="cfc39-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="cfc39-131">Zie voor meer informatie over de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cfc39-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="cfc39-132">Zie voor meer informatie over de onderdelen van de weergave van een aangepast besturingselement [aangepaste weergave van het](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cfc39-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cfc39-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cfc39-133">See Also</span></span>

[<span data-ttu-id="cfc39-134">SelectionCondition-Element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="cfc39-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="cfc39-135">SelectionSetName-Element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="cfc39-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cfc39-136">TypeName-Element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="cfc39-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cfc39-137">CustomEntry-Element voor CustomEntries voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cfc39-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cfc39-138">Aangepast besturingselement weergeven</span><span class="sxs-lookup"><span data-stu-id="cfc39-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="cfc39-139">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfc39-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
