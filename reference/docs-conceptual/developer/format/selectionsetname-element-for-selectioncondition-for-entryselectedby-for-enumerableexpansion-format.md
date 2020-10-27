---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)
description: Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)
ms.openlocfilehash: 0c9372113a79f75cfbda67acf869164fde894ee3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651597"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="11eb1-103">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="11eb1-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="11eb1-104">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="11eb1-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="11eb1-105">Wanneer een van de typen in deze set aanwezig is, wordt voldaan aan de voor waarde.</span><span class="sxs-lookup"><span data-stu-id="11eb1-105">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="11eb1-106">Configuratie-element DefaultSettings element (Format) EnumerableExpansions element (indeling) EnumerableExpansions element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (Format) SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="11eb1-106">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11eb1-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="11eb1-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11eb1-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="11eb1-108">Attributes and Elements</span></span>

<span data-ttu-id="11eb1-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="11eb1-109">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11eb1-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="11eb1-110">Attributes</span></span>

<span data-ttu-id="11eb1-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="11eb1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11eb1-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="11eb1-112">Child Elements</span></span>

<span data-ttu-id="11eb1-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="11eb1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11eb1-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="11eb1-114">Parent Elements</span></span>

|<span data-ttu-id="11eb1-115">Element</span><span class="sxs-lookup"><span data-stu-id="11eb1-115">Element</span></span>|<span data-ttu-id="11eb1-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="11eb1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11eb1-117">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="11eb1-117">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="11eb1-118">Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="11eb1-118">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="11eb1-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="11eb1-119">Text Value</span></span>

<span data-ttu-id="11eb1-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="11eb1-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="11eb1-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="11eb1-121">Remarks</span></span>

<span data-ttu-id="11eb1-122">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="11eb1-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="11eb1-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="11eb1-123">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="11eb1-124">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="11eb1-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="11eb1-125">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="11eb1-125">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11eb1-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="11eb1-126">See Also</span></span>

[<span data-ttu-id="11eb1-127">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="11eb1-127">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="11eb1-128">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="11eb1-128">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="11eb1-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="11eb1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
