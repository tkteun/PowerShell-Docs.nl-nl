---
title: SelectionSetName-element voor SelectionCondition voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358837"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="e033b-102">Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e033b-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="e033b-103">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e033b-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="e033b-104">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object met dit besturings element weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e033b-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="e033b-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="e033b-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e033b-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (indeling) EntrySelectedBy Element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e033b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e033b-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e033b-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e033b-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e033b-108">Attributes and Elements</span></span>

<span data-ttu-id="e033b-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="e033b-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e033b-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e033b-110">Attributes</span></span>

<span data-ttu-id="e033b-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="e033b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e033b-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e033b-112">Child Elements</span></span>

<span data-ttu-id="e033b-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="e033b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e033b-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e033b-114">Parent Elements</span></span>

|<span data-ttu-id="e033b-115">Element</span><span class="sxs-lookup"><span data-stu-id="e033b-115">Element</span></span>|<span data-ttu-id="e033b-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e033b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e033b-117">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e033b-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="e033b-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="e033b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e033b-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="e033b-119">Text Value</span></span>

<span data-ttu-id="e033b-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="e033b-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e033b-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e033b-121">Remarks</span></span>

<span data-ttu-id="e033b-122">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e033b-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="e033b-123">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="e033b-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e033b-124">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e033b-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="e033b-125">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="e033b-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e033b-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e033b-126">See Also</span></span>

[<span data-ttu-id="e033b-127">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e033b-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="e033b-128">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="e033b-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e033b-129">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="e033b-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e033b-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e033b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
