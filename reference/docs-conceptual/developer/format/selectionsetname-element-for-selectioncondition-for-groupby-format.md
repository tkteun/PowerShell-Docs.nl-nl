---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)
description: Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)
ms.openlocfilehash: a4f28c1caba3790718b99f63659cb0cbed8def16
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654992"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="88c70-103">Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="88c70-103">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="88c70-104">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="88c70-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="88c70-105">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="88c70-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="88c70-106">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="88c70-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="88c70-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) SelectionCondition voor EntrySelectedBy voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="88c70-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88c70-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="88c70-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88c70-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="88c70-109">Attributes and Elements</span></span>

<span data-ttu-id="88c70-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="88c70-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="88c70-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="88c70-111">Attributes</span></span>

<span data-ttu-id="88c70-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="88c70-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88c70-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="88c70-113">Child Elements</span></span>

<span data-ttu-id="88c70-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="88c70-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="88c70-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="88c70-115">Parent Elements</span></span>

|<span data-ttu-id="88c70-116">Element</span><span class="sxs-lookup"><span data-stu-id="88c70-116">Element</span></span>|<span data-ttu-id="88c70-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="88c70-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88c70-118">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="88c70-118">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="88c70-119">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="88c70-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="88c70-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="88c70-120">Text Value</span></span>

<span data-ttu-id="88c70-121">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="88c70-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="88c70-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="88c70-122">Remarks</span></span>

<span data-ttu-id="88c70-123">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="88c70-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="88c70-124">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="88c70-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="88c70-125">Als dit element is opgegeven, kunt u het element [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="88c70-125">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="88c70-126">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="88c70-126">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88c70-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="88c70-127">See Also</span></span>

[<span data-ttu-id="88c70-128">Het element TypeName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="88c70-128">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="88c70-129">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="88c70-129">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="88c70-130">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="88c70-130">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="88c70-131">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="88c70-131">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="88c70-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="88c70-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
