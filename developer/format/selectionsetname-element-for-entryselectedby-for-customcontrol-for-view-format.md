---
title: SelectionSetName-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063965"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="ec105-102">Het element SelectionSetName voor EntrySelectedBy voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ec105-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="ec105-103">Hiermee geeft u een set van .NET-objecten voor de vermelding in de lijst.</span><span class="sxs-lookup"><span data-stu-id="ec105-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="ec105-104">Er is geen limiet voor het aantal selectiesets die kan worden opgegeven voor een vermelding.</span><span class="sxs-lookup"><span data-stu-id="ec105-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="ec105-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor EntrySelectedBy weergeven (indeling) Element voor CustomEntry voor weergave (indeling) SelectionSetName Element voor EntrySelectedBy voor CustomEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="ec105-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ec105-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ec105-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec105-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ec105-107">Attributes and Elements</span></span>

<span data-ttu-id="ec105-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="ec105-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec105-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ec105-109">Attributes</span></span>

<span data-ttu-id="ec105-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="ec105-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec105-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ec105-111">Child Elements</span></span>

<span data-ttu-id="ec105-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="ec105-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ec105-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ec105-113">Parent Elements</span></span>

|<span data-ttu-id="ec105-114">Element</span><span class="sxs-lookup"><span data-stu-id="ec105-114">Element</span></span>|<span data-ttu-id="ec105-115">Description</span><span class="sxs-lookup"><span data-stu-id="ec105-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec105-116">EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ec105-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="ec105-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ec105-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ec105-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="ec105-118">Text Value</span></span>

<span data-ttu-id="ec105-119">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="ec105-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec105-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ec105-120">Remarks</span></span>

<span data-ttu-id="ec105-121">Elk item van het aangepaste besturingselement moet hebben ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="ec105-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ec105-122">Selectiesets worden meestal gebruikt wanneer u wilt definiëren van een groep objecten die worden gebruikt in meerdere weergaven.</span><span class="sxs-lookup"><span data-stu-id="ec105-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="ec105-123">Bijvoorbeeld, als u wilt weergeven als een tabel en een lijst weergeven voor dezelfde set objecten maken.</span><span class="sxs-lookup"><span data-stu-id="ec105-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="ec105-124">Zie voor meer informatie over het definiëren van selectiesets [definiëren voor de selectie wordt ingesteld](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ec105-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ec105-125">Zie voor meer informatie over de onderdelen van de weergave van een aangepast besturingselement [het maken van aangepaste besturingselementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ec105-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec105-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ec105-126">See Also</span></span>

[<span data-ttu-id="ec105-127">EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ec105-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ec105-128">Aangepast besturingselement weergeven</span><span class="sxs-lookup"><span data-stu-id="ec105-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ec105-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec105-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
