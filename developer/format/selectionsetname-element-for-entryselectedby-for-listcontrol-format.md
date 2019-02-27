---
title: SelectionSetName-Element voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849719"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="6a646-102">Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6a646-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="6a646-103">Hiermee geeft u een set van .NET-objecten voor de vermelding in de lijst.</span><span class="sxs-lookup"><span data-stu-id="6a646-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="6a646-104">Er is geen limiet voor het aantal selectiesets die kan worden opgegeven voor een vermelding.</span><span class="sxs-lookup"><span data-stu-id="6a646-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="6a646-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling) EntrySelectedBy Element voor ListEntry (indeling) SelectionSetName-Element voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6a646-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a646-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6a646-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a646-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6a646-107">Attributes and Elements</span></span>

<span data-ttu-id="6a646-108">De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="6a646-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a646-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6a646-109">Attributes</span></span>

<span data-ttu-id="6a646-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="6a646-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a646-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6a646-111">Child Elements</span></span>

<span data-ttu-id="6a646-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="6a646-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6a646-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6a646-113">Parent Elements</span></span>

|<span data-ttu-id="6a646-114">Element</span><span class="sxs-lookup"><span data-stu-id="6a646-114">Element</span></span>|<span data-ttu-id="6a646-115">Description</span><span class="sxs-lookup"><span data-stu-id="6a646-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a646-116">EntrySelectedBy-Element voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6a646-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="6a646-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze vermelding lijst of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6a646-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6a646-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="6a646-118">Text Value</span></span>

<span data-ttu-id="6a646-119">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="6a646-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a646-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6a646-120">Remarks</span></span>

<span data-ttu-id="6a646-121">Elk lijstitem moet hebben ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="6a646-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="6a646-122">Selectiesets worden meestal gebruikt wanneer u wilt definiëren van een groep objecten die worden gebruikt in meerdere weergaven.</span><span class="sxs-lookup"><span data-stu-id="6a646-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="6a646-123">Bijvoorbeeld, als u wilt weergeven als een tabel en een lijst weergeven voor dezelfde set objecten maken.</span><span class="sxs-lookup"><span data-stu-id="6a646-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="6a646-124">Zie voor meer informatie over het definiëren van selectiesets [van objecten voor een weergave definiëren ingesteld](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6a646-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="6a646-125">Zie voor meer informatie over de onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="6a646-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6a646-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6a646-126">Example</span></span>

<span data-ttu-id="6a646-127">Het volgende voorbeeld ziet hoe u een selectie instellen voor een vermelding van een lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="6a646-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="6a646-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6a646-128">See Also</span></span>

[<span data-ttu-id="6a646-129">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="6a646-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6a646-130">EntrySelectedBy-Element voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6a646-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="6a646-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a646-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
