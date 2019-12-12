---
title: SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358821"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="87f83-102">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="87f83-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="87f83-103">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="87f83-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="87f83-104">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van deze definitie van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="87f83-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="87f83-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition-element voor EntrySelectedBy voor WideEntry (Format) SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="87f83-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87f83-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="87f83-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87f83-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="87f83-107">Attributes and Elements</span></span>

<span data-ttu-id="87f83-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="87f83-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="87f83-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="87f83-109">Attributes</span></span>

<span data-ttu-id="87f83-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="87f83-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87f83-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="87f83-111">Child Elements</span></span>

<span data-ttu-id="87f83-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="87f83-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="87f83-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="87f83-113">Parent Elements</span></span>

|<span data-ttu-id="87f83-114">Element</span><span class="sxs-lookup"><span data-stu-id="87f83-114">Element</span></span>|<span data-ttu-id="87f83-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="87f83-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87f83-116">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="87f83-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="87f83-117">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="87f83-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="87f83-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="87f83-118">Text Value</span></span>

<span data-ttu-id="87f83-119">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="87f83-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="87f83-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="87f83-120">Remarks</span></span>

<span data-ttu-id="87f83-121">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="87f83-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="87f83-122">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="87f83-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="87f83-123">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="87f83-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="87f83-124">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="87f83-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="87f83-125">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="87f83-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87f83-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="87f83-126">See Also</span></span>

[<span data-ttu-id="87f83-127">Een brede weer gave maken</span><span class="sxs-lookup"><span data-stu-id="87f83-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="87f83-128">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="87f83-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="87f83-129">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="87f83-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="87f83-130">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="87f83-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="87f83-131">TypeName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="87f83-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="87f83-132">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="87f83-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
