---
title: EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355123"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="0bc83-102">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0bc83-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="0bc83-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0bc83-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="0bc83-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0bc83-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0bc83-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (indeling) EntrySelectedBy voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="0bc83-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0bc83-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0bc83-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0bc83-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0bc83-107">Attributes and Elements</span></span>

<span data-ttu-id="0bc83-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `EntrySelectedBy` beschreven.</span><span class="sxs-lookup"><span data-stu-id="0bc83-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="0bc83-109">U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="0bc83-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="0bc83-110">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0bc83-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="0bc83-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0bc83-111">Attributes</span></span>

<span data-ttu-id="0bc83-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="0bc83-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0bc83-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0bc83-113">Child Elements</span></span>

|<span data-ttu-id="0bc83-114">Element</span><span class="sxs-lookup"><span data-stu-id="0bc83-114">Element</span></span>|<span data-ttu-id="0bc83-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0bc83-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0bc83-116">SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="0bc83-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0bc83-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0bc83-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0bc83-118">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0bc83-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="0bc83-119">SelectionSetName-element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="0bc83-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0bc83-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0bc83-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0bc83-121">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="0bc83-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="0bc83-122">TypeName-element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="0bc83-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0bc83-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0bc83-123">Optional element.</span></span><br /><br /> <span data-ttu-id="0bc83-124">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="0bc83-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0bc83-125">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0bc83-125">Parent Elements</span></span>

|<span data-ttu-id="0bc83-126">Element</span><span class="sxs-lookup"><span data-stu-id="0bc83-126">Element</span></span>|<span data-ttu-id="0bc83-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0bc83-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0bc83-128">CustomEntry-element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="0bc83-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="0bc83-129">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="0bc83-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0bc83-130">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0bc83-130">Remarks</span></span>

<span data-ttu-id="0bc83-131">De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script wordt geëvalueerd als `true`.</span><span class="sxs-lookup"><span data-stu-id="0bc83-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="0bc83-132">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="0bc83-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0bc83-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0bc83-133">See Also</span></span>

[<span data-ttu-id="0bc83-134">SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="0bc83-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0bc83-135">SelectionSetName-element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="0bc83-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0bc83-136">TypeName-element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="0bc83-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0bc83-137">CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="0bc83-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="0bc83-138">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="0bc83-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
