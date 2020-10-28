---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor EntrySelectedBy voor CustomControl voor Weergave (opmaak)
description: Het element SelectionSetName voor EntrySelectedBy voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: a158c5476fb3a168a146ce67565c0ed6f7859519
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651914"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="05b89-103">Het element SelectionSetName voor EntrySelectedBy voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="05b89-103">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="05b89-104">Hiermee geeft u een set .NET-objecten voor de lijst vermelding op.</span><span class="sxs-lookup"><span data-stu-id="05b89-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="05b89-105">Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="05b89-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="05b89-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) EntrySelectedBy element voor CustomEntry voor weer gave (Format) SelectionSetName-element voor EntrySelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="05b89-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="05b89-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="05b89-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="05b89-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="05b89-108">Attributes and Elements</span></span>

<span data-ttu-id="05b89-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="05b89-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="05b89-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="05b89-110">Attributes</span></span>

<span data-ttu-id="05b89-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="05b89-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="05b89-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="05b89-112">Child Elements</span></span>

<span data-ttu-id="05b89-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="05b89-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="05b89-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="05b89-114">Parent Elements</span></span>

|<span data-ttu-id="05b89-115">Element</span><span class="sxs-lookup"><span data-stu-id="05b89-115">Element</span></span>|<span data-ttu-id="05b89-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="05b89-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05b89-117">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="05b89-117">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="05b89-118">Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="05b89-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="05b89-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="05b89-119">Text Value</span></span>

<span data-ttu-id="05b89-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="05b89-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="05b89-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="05b89-121">Remarks</span></span>

<span data-ttu-id="05b89-122">Voor elke aangepaste controle vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="05b89-122">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="05b89-123">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="05b89-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="05b89-124">U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten.</span><span class="sxs-lookup"><span data-stu-id="05b89-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="05b89-125">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="05b89-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="05b89-126">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="05b89-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05b89-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="05b89-127">See Also</span></span>

[<span data-ttu-id="05b89-128">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="05b89-128">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="05b89-129">Aangepaste besturings elementen weer geven</span><span class="sxs-lookup"><span data-stu-id="05b89-129">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="05b89-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="05b89-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
