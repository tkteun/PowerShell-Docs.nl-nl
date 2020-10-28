---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)
description: Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)
ms.openlocfilehash: 074f810f5a3cbad61ee8be69408967758f0591df
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651881"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="1b222-103">Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1b222-103">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="1b222-104">Hiermee geeft u de set .NET-typen op die door deze definitie worden uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="1b222-104">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="1b222-105">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionSetName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="1b222-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1b222-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b222-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b222-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1b222-107">Attributes and Elements</span></span>

<span data-ttu-id="1b222-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="1b222-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b222-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1b222-109">Attributes</span></span>

<span data-ttu-id="1b222-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="1b222-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1b222-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1b222-111">Child Elements</span></span>

<span data-ttu-id="1b222-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="1b222-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b222-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1b222-113">Parent Elements</span></span>

|<span data-ttu-id="1b222-114">Element</span><span class="sxs-lookup"><span data-stu-id="1b222-114">Element</span></span>|<span data-ttu-id="1b222-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1b222-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b222-116">Het element EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1b222-116">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="1b222-117">Hiermee definieert u de .NET-verzamelings objecten die door deze definitie worden uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="1b222-117">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1b222-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1b222-118">Text Value</span></span>

<span data-ttu-id="1b222-119">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="1b222-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b222-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1b222-120">Remarks</span></span>

<span data-ttu-id="1b222-121">Elke definitie moet een of meer type namen, een selectieset of een selectie voorwaarde opgeven.</span><span class="sxs-lookup"><span data-stu-id="1b222-121">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="1b222-122">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="1b222-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="1b222-123">U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten.</span><span class="sxs-lookup"><span data-stu-id="1b222-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="1b222-124">Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="1b222-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b222-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1b222-125">See Also</span></span>

[<span data-ttu-id="1b222-126">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="1b222-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1b222-127">Het element EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1b222-127">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="1b222-128">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="1b222-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
