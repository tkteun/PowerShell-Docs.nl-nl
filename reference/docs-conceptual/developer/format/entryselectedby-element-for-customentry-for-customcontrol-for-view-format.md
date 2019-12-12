---
title: EntrySelectedBy-element voor CustomEntry voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358998"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="750a8-102">Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="750a8-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="750a8-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="750a8-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="750a8-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (indeling) EntrySelectedBy Element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="750a8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="750a8-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="750a8-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="750a8-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="750a8-106">Attributes and Elements</span></span>

<span data-ttu-id="750a8-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `EntrySelectedBy` beschreven.</span><span class="sxs-lookup"><span data-stu-id="750a8-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="750a8-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="750a8-108">Attributes</span></span>

<span data-ttu-id="750a8-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="750a8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="750a8-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="750a8-110">Child Elements</span></span>

|<span data-ttu-id="750a8-111">Element</span><span class="sxs-lookup"><span data-stu-id="750a8-111">Element</span></span>|<span data-ttu-id="750a8-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="750a8-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="750a8-113">SelectionCondition-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="750a8-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="750a8-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="750a8-114">Optional element.</span></span><br /><br /> <span data-ttu-id="750a8-115">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="750a8-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="750a8-116">SelectionSetName-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="750a8-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="750a8-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="750a8-117">Optional element.</span></span><br /><br /> <span data-ttu-id="750a8-118">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van de beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="750a8-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="750a8-119">TypeName-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="750a8-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="750a8-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="750a8-120">Optional element.</span></span><br /><br /> <span data-ttu-id="750a8-121">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van de controle weergave.</span><span class="sxs-lookup"><span data-stu-id="750a8-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="750a8-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="750a8-122">Parent Elements</span></span>

|<span data-ttu-id="750a8-123">Element</span><span class="sxs-lookup"><span data-stu-id="750a8-123">Element</span></span>|<span data-ttu-id="750a8-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="750a8-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="750a8-125">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="750a8-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="750a8-126">Hiermee worden de besturings elementen gedefinieerd die worden gebruikt door specifieke .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="750a8-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="750a8-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="750a8-127">Remarks</span></span>

<span data-ttu-id="750a8-128">U moet ten minste één type, selectieset of selectie voorwaarde voor een vermelding opgeven.</span><span class="sxs-lookup"><span data-stu-id="750a8-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="750a8-129">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="750a8-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="750a8-130">De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die moet bestaan voor het gebruik van de vermelding, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script `true`.</span><span class="sxs-lookup"><span data-stu-id="750a8-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="750a8-131">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="750a8-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="750a8-132">Zie [aangepaste besturings elementen weer geven](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="750a8-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="750a8-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="750a8-133">See Also</span></span>

[<span data-ttu-id="750a8-134">SelectionCondition-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="750a8-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="750a8-135">SelectionSetName-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="750a8-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="750a8-136">TypeName-element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="750a8-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="750a8-137">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="750a8-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="750a8-138">Aangepaste besturings elementen weer geven</span><span class="sxs-lookup"><span data-stu-id="750a8-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="750a8-139">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="750a8-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
