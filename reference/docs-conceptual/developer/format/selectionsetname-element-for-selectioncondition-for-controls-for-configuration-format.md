---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
description: Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 4177aace5a6a9374900e7339167c69b531c1e2e7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651656"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="42423-103">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="42423-103">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="42423-104">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="42423-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="42423-105">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="42423-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="42423-106">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="42423-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="42423-107">Configuratie-element (Format) Controls element van configuratie (Format) Control-element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het beheer van de configuratie (Format) CustomEntry-element voor het EntrySelectedBy-element van de configuratie (indeling) voor CustomEntry voor besturings elementen voor de configuratie (indeling) SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor de configuratie (indeling) SelectionSetName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="42423-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42423-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="42423-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42423-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="42423-109">Attributes and Elements</span></span>

<span data-ttu-id="42423-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="42423-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42423-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="42423-111">Attributes</span></span>

<span data-ttu-id="42423-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="42423-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42423-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="42423-113">Child Elements</span></span>

<span data-ttu-id="42423-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="42423-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="42423-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="42423-115">Parent Elements</span></span>

|<span data-ttu-id="42423-116">Element</span><span class="sxs-lookup"><span data-stu-id="42423-116">Element</span></span>|<span data-ttu-id="42423-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="42423-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42423-118">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="42423-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="42423-119">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="42423-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="42423-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="42423-120">Text Value</span></span>

<span data-ttu-id="42423-121">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="42423-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="42423-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="42423-122">Remarks</span></span>

<span data-ttu-id="42423-123">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="42423-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="42423-124">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="42423-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="42423-125">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="42423-125">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="42423-126">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="42423-126">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42423-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="42423-127">See Also</span></span>

[<span data-ttu-id="42423-128">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="42423-128">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="42423-129">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="42423-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="42423-130">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="42423-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="42423-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="42423-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
