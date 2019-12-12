---
title: SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353814"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="853f1-102">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="853f1-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="853f1-103">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="853f1-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="853f1-104">Wanneer een van de typen in deze set aanwezig is, wordt voldaan aan de voor waarde.</span><span class="sxs-lookup"><span data-stu-id="853f1-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="853f1-105">Configuratie-element DefaultSettings element (Format) EnumerableExpansions element (indeling) EnumerableExpansions element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (Format) SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="853f1-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="853f1-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="853f1-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="853f1-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="853f1-107">Attributes and Elements</span></span>

<span data-ttu-id="853f1-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="853f1-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="853f1-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="853f1-109">Attributes</span></span>

<span data-ttu-id="853f1-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="853f1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="853f1-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="853f1-111">Child Elements</span></span>

<span data-ttu-id="853f1-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="853f1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="853f1-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="853f1-113">Parent Elements</span></span>

|<span data-ttu-id="853f1-114">Element</span><span class="sxs-lookup"><span data-stu-id="853f1-114">Element</span></span>|<span data-ttu-id="853f1-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="853f1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="853f1-116">SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="853f1-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="853f1-117">Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="853f1-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="853f1-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="853f1-118">Text Value</span></span>

<span data-ttu-id="853f1-119">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="853f1-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="853f1-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="853f1-120">Remarks</span></span>

<span data-ttu-id="853f1-121">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="853f1-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="853f1-122">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="853f1-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="853f1-123">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="853f1-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="853f1-124">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="853f1-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="853f1-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="853f1-125">See Also</span></span>

[<span data-ttu-id="853f1-126">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="853f1-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="853f1-127">SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="853f1-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="853f1-128">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="853f1-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
