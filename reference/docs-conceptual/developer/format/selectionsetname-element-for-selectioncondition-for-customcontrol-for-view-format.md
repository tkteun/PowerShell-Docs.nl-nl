---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)
description: Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 839032048739e529057d7066fb3bc6aa2fbc5037
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651602"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="48fe8-103">Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="48fe8-103">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="48fe8-104">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="48fe8-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="48fe8-105">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object met dit besturings element weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="48fe8-105">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="48fe8-106">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="48fe8-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="48fe8-107">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) EntrySelectedBy element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="48fe8-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="48fe8-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="48fe8-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48fe8-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="48fe8-109">Attributes and Elements</span></span>

<span data-ttu-id="48fe8-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="48fe8-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="48fe8-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="48fe8-111">Attributes</span></span>

<span data-ttu-id="48fe8-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="48fe8-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48fe8-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="48fe8-113">Child Elements</span></span>

<span data-ttu-id="48fe8-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="48fe8-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="48fe8-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="48fe8-115">Parent Elements</span></span>

|<span data-ttu-id="48fe8-116">Element</span><span class="sxs-lookup"><span data-stu-id="48fe8-116">Element</span></span>|<span data-ttu-id="48fe8-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="48fe8-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48fe8-118">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="48fe8-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="48fe8-119">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="48fe8-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="48fe8-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="48fe8-120">Text Value</span></span>

<span data-ttu-id="48fe8-121">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="48fe8-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="48fe8-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="48fe8-122">Remarks</span></span>

<span data-ttu-id="48fe8-123">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="48fe8-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="48fe8-124">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="48fe8-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="48fe8-125">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="48fe8-125">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="48fe8-126">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="48fe8-126">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="48fe8-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="48fe8-127">See Also</span></span>

[<span data-ttu-id="48fe8-128">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="48fe8-128">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="48fe8-129">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="48fe8-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="48fe8-130">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="48fe8-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="48fe8-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="48fe8-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
