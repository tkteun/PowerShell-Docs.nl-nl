---
title: SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358830"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="b4a64-102">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b4a64-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="b4a64-103">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b4a64-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b4a64-104">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van deze definitie van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="b4a64-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="b4a64-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type-element (indeling) EntrySelectedBy element (Format) voor List entry (Format) SelectionCondition element voor EntrySelectedBy voor List entry (Format) SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor List entry (Format)</span><span class="sxs-lookup"><span data-stu-id="b4a64-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4a64-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b4a64-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4a64-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b4a64-107">Attributes and Elements</span></span>

<span data-ttu-id="b4a64-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="b4a64-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4a64-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b4a64-109">Attributes</span></span>

<span data-ttu-id="b4a64-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="b4a64-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4a64-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b4a64-111">Child Elements</span></span>

<span data-ttu-id="b4a64-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="b4a64-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b4a64-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b4a64-113">Parent Elements</span></span>

|<span data-ttu-id="b4a64-114">Element</span><span class="sxs-lookup"><span data-stu-id="b4a64-114">Element</span></span>|<span data-ttu-id="b4a64-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b4a64-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4a64-116">SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="b4a64-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b4a64-117">Hiermee definieert u de voor waarde die moet bestaan om deze definitie van de lijst weergave te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b4a64-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b4a64-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="b4a64-118">Text Value</span></span>

<span data-ttu-id="b4a64-119">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="b4a64-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4a64-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b4a64-120">Remarks</span></span>

<span data-ttu-id="b4a64-121">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b4a64-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="b4a64-122">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="b4a64-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b4a64-123">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b4a64-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b4a64-124">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="b4a64-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b4a64-125">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over andere onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="b4a64-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4a64-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b4a64-126">See Also</span></span>

[<span data-ttu-id="b4a64-127">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="b4a64-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b4a64-128">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="b4a64-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b4a64-129">SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="b4a64-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="b4a64-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b4a64-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
