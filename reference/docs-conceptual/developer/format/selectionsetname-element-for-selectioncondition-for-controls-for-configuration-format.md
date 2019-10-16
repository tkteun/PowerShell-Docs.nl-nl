---
title: SelectionSetName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358844"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="c8450-102">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c8450-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c8450-103">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c8450-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c8450-104">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="c8450-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="c8450-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="c8450-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c8450-106">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries-element voor besturings elementen voor Configuratie (indeling) CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de configuratie (indeling) SelectionCondition element voor EntrySelectedBy voor besturings elementen voor Configuratie (Format) SelectionSetName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="c8450-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c8450-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c8450-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c8450-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c8450-108">Attributes and Elements</span></span>

<span data-ttu-id="c8450-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="c8450-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c8450-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c8450-110">Attributes</span></span>

<span data-ttu-id="c8450-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="c8450-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c8450-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c8450-112">Child Elements</span></span>

<span data-ttu-id="c8450-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="c8450-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c8450-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c8450-114">Parent Elements</span></span>

|<span data-ttu-id="c8450-115">Element</span><span class="sxs-lookup"><span data-stu-id="c8450-115">Element</span></span>|<span data-ttu-id="c8450-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c8450-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8450-117">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="c8450-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="c8450-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="c8450-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c8450-119">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="c8450-119">Text Value</span></span>

<span data-ttu-id="c8450-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="c8450-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c8450-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c8450-121">Remarks</span></span>

<span data-ttu-id="c8450-122">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="c8450-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c8450-123">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="c8450-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c8450-124">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c8450-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c8450-125">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="c8450-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c8450-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c8450-126">See Also</span></span>

[<span data-ttu-id="c8450-127">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="c8450-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="c8450-128">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="c8450-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c8450-129">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="c8450-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c8450-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c8450-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
