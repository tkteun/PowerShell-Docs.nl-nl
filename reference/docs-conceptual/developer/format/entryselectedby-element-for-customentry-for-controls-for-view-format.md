---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)
description: Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 29b0574a95d81962fb3f72a526f89273baeea647
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660270"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="24afd-103">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="24afd-103">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="24afd-104">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="24afd-104">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="24afd-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="24afd-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="24afd-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element (indeling) Controls-element (opmaak) Control element (Format) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor de weer gave (Format) CustomEntries-element voor object voor weer gave (Format) voor de weer gave (Format) voor het EntrySelectedBy-element voor Controls (indeling)</span><span class="sxs-lookup"><span data-stu-id="24afd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="24afd-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="24afd-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="24afd-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="24afd-108">Attributes and Elements</span></span>

<span data-ttu-id="24afd-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="24afd-109">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="24afd-110">U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="24afd-110">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="24afd-111">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="24afd-111">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="24afd-112">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="24afd-112">Attributes</span></span>

<span data-ttu-id="24afd-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="24afd-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="24afd-114">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="24afd-114">Child Elements</span></span>

|<span data-ttu-id="24afd-115">Element</span><span class="sxs-lookup"><span data-stu-id="24afd-115">Element</span></span>|<span data-ttu-id="24afd-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="24afd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="24afd-117">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="24afd-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="24afd-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="24afd-118">Optional element.</span></span><br /><br /> <span data-ttu-id="24afd-119">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="24afd-119">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="24afd-120">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="24afd-120">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="24afd-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="24afd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="24afd-122">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="24afd-122">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="24afd-123">Het element TypeName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="24afd-123">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="24afd-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="24afd-124">Optional element.</span></span><br /><br /> <span data-ttu-id="24afd-125">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="24afd-125">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="24afd-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="24afd-126">Parent Elements</span></span>

|<span data-ttu-id="24afd-127">Element</span><span class="sxs-lookup"><span data-stu-id="24afd-127">Element</span></span>|<span data-ttu-id="24afd-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="24afd-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="24afd-129">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="24afd-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="24afd-130">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="24afd-130">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="24afd-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="24afd-131">Remarks</span></span>

<span data-ttu-id="24afd-132">Selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="24afd-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="24afd-133">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="24afd-133">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="24afd-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="24afd-134">See Also</span></span>

[<span data-ttu-id="24afd-135">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="24afd-135">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="24afd-136">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="24afd-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
