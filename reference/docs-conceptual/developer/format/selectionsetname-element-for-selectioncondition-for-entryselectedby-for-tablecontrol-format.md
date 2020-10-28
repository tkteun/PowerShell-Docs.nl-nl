---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)
description: Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)
ms.openlocfilehash: 2fb09e27eef1ce5d6e864c72edb595817d91f729
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655046"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="b17d5-103">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b17d5-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="b17d5-104">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b17d5-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b17d5-105">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van deze definitie van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="b17d5-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="b17d5-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element voor TableRowEntry (Format) SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (Format) SelectionSetName-element voor SelectionCondition voor EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="b17d5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b17d5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b17d5-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b17d5-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b17d5-108">Attributes and Elements</span></span>

<span data-ttu-id="b17d5-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="b17d5-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b17d5-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b17d5-110">Attributes</span></span>

<span data-ttu-id="b17d5-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="b17d5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b17d5-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b17d5-112">Child Elements</span></span>

<span data-ttu-id="b17d5-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="b17d5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b17d5-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b17d5-114">Parent Elements</span></span>

|<span data-ttu-id="b17d5-115">Element</span><span class="sxs-lookup"><span data-stu-id="b17d5-115">Element</span></span>|<span data-ttu-id="b17d5-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b17d5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b17d5-117">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="b17d5-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b17d5-118">Hiermee definieert u de voor waarde die moet bestaan om te gebruiken voor deze definitie van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="b17d5-118">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b17d5-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="b17d5-119">Text Value</span></span>

<span data-ttu-id="b17d5-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="b17d5-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b17d5-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b17d5-121">Remarks</span></span>

<span data-ttu-id="b17d5-122">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b17d5-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="b17d5-123">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="b17d5-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b17d5-124">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b17d5-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b17d5-125">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="b17d5-125">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b17d5-126">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="b17d5-126">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b17d5-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b17d5-127">See Also</span></span>

[<span data-ttu-id="b17d5-128">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="b17d5-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b17d5-129">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="b17d5-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b17d5-130">TypeName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="b17d5-130">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b17d5-131">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="b17d5-131">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b17d5-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b17d5-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
