---
title: SelectionSetName-element voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355739"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="b6de7-102">Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b6de7-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="b6de7-103">Hiermee geeft u een set .NET-objecten voor de lijst vermelding op.</span><span class="sxs-lookup"><span data-stu-id="b6de7-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="b6de7-104">Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b6de7-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="b6de7-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b6de7-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b6de7-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (indeling) EntrySelectedBy voor CustomEntry voor GroupBy (Format) SelectionSetName-element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="b6de7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b6de7-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b6de7-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b6de7-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b6de7-108">Attributes and Elements</span></span>

<span data-ttu-id="b6de7-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="b6de7-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6de7-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b6de7-110">Attributes</span></span>

<span data-ttu-id="b6de7-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="b6de7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b6de7-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b6de7-112">Child Elements</span></span>

<span data-ttu-id="b6de7-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="b6de7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b6de7-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b6de7-114">Parent Elements</span></span>

|<span data-ttu-id="b6de7-115">Element</span><span class="sxs-lookup"><span data-stu-id="b6de7-115">Element</span></span>|<span data-ttu-id="b6de7-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b6de7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b6de7-117">EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="b6de7-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="b6de7-118">Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="b6de7-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b6de7-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="b6de7-119">Text Value</span></span>

<span data-ttu-id="b6de7-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="b6de7-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6de7-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b6de7-121">Remarks</span></span>

<span data-ttu-id="b6de7-122">Voor elke aangepaste besturings definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b6de7-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b6de7-123">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="b6de7-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="b6de7-124">U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten.</span><span class="sxs-lookup"><span data-stu-id="b6de7-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="b6de7-125">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="b6de7-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b6de7-126">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="b6de7-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6de7-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b6de7-127">See Also</span></span>

[<span data-ttu-id="b6de7-128">EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="b6de7-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="b6de7-129">Aangepaste besturings elementen maken</span><span class="sxs-lookup"><span data-stu-id="b6de7-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="b6de7-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b6de7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
