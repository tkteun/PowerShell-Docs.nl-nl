---
title: SelectionSetName-element voor SelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6d0263aa335287f20be5b94a8eb65696d06d82a8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772617"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="740fc-102">Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="740fc-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="740fc-103">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="740fc-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="740fc-104">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="740fc-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="740fc-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="740fc-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="740fc-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) SelectionCondition voor EntrySelectedBy voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="740fc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="740fc-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="740fc-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="740fc-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="740fc-108">Attributes and Elements</span></span>

<span data-ttu-id="740fc-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="740fc-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="740fc-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="740fc-110">Attributes</span></span>

<span data-ttu-id="740fc-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="740fc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="740fc-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="740fc-112">Child Elements</span></span>

<span data-ttu-id="740fc-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="740fc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="740fc-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="740fc-114">Parent Elements</span></span>

|<span data-ttu-id="740fc-115">Element</span><span class="sxs-lookup"><span data-stu-id="740fc-115">Element</span></span>|<span data-ttu-id="740fc-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="740fc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="740fc-117">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="740fc-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="740fc-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="740fc-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="740fc-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="740fc-119">Text Value</span></span>

<span data-ttu-id="740fc-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="740fc-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="740fc-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="740fc-121">Remarks</span></span>

<span data-ttu-id="740fc-122">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="740fc-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="740fc-123">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="740fc-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="740fc-124">Als dit element is opgegeven, kunt u het element [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="740fc-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="740fc-125">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="740fc-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="740fc-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="740fc-126">See Also</span></span>

[<span data-ttu-id="740fc-127">Het element TypeName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="740fc-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="740fc-128">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="740fc-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="740fc-129">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="740fc-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="740fc-130">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="740fc-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="740fc-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="740fc-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
