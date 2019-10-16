---
title: SelectionSetName-element voor SelectionCondition voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353800"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="411be-102">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="411be-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="411be-103">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="411be-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="411be-104">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object met dit besturings element weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="411be-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="411be-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="411be-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="411be-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy for Controls ( Format) SelectionSetName-element voor SelectionCondition voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="411be-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="411be-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="411be-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="411be-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="411be-108">Attributes and Elements</span></span>

<span data-ttu-id="411be-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="411be-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="411be-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="411be-110">Attributes</span></span>

<span data-ttu-id="411be-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="411be-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="411be-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="411be-112">Child Elements</span></span>

<span data-ttu-id="411be-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="411be-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="411be-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="411be-114">Parent Elements</span></span>

|<span data-ttu-id="411be-115">Element</span><span class="sxs-lookup"><span data-stu-id="411be-115">Element</span></span>|<span data-ttu-id="411be-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="411be-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="411be-117">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="411be-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="411be-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="411be-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="411be-119">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="411be-119">Text Value</span></span>

<span data-ttu-id="411be-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="411be-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="411be-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="411be-121">Remarks</span></span>

<span data-ttu-id="411be-122">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="411be-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="411be-123">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="411be-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="411be-124">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="411be-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="411be-125">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="411be-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="411be-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="411be-126">See Also</span></span>

[<span data-ttu-id="411be-127">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="411be-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="411be-128">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="411be-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="411be-129">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="411be-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="411be-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="411be-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
