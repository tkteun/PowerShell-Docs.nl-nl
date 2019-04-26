---
title: TypeName-Element voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084025"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="0eb3d-102">Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0eb3d-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="0eb3d-103">Hiermee geeft u een .NET-type dat deze vermelding van de lijstweergave gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0eb3d-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="0eb3d-104">Er is geen limiet voor het aantal typen die kunnen worden opgegeven voor een lijstitem.</span><span class="sxs-lookup"><span data-stu-id="0eb3d-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="0eb3d-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling) EntrySelectedBy Element voor ListEntry (indeling) TypeName-Element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0eb3d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0eb3d-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0eb3d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0eb3d-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0eb3d-107">Attributes and Elements</span></span>

<span data-ttu-id="0eb3d-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="0eb3d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0eb3d-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0eb3d-109">Attributes</span></span>

<span data-ttu-id="0eb3d-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="0eb3d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0eb3d-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0eb3d-111">Child Elements</span></span>

<span data-ttu-id="0eb3d-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="0eb3d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0eb3d-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0eb3d-113">Parent Elements</span></span>

|<span data-ttu-id="0eb3d-114">Element</span><span class="sxs-lookup"><span data-stu-id="0eb3d-114">Element</span></span>|<span data-ttu-id="0eb3d-115">Description</span><span class="sxs-lookup"><span data-stu-id="0eb3d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0eb3d-116">EntrySelectedBy-Element voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="0eb3d-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0eb3d-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze vermelding lijst of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0eb3d-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0eb3d-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="0eb3d-118">Text Value</span></span>

<span data-ttu-id="0eb3d-119">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="0eb3d-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0eb3d-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0eb3d-120">Remarks</span></span>

<span data-ttu-id="0eb3d-121">Elk lijstitem moet hebben ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="0eb3d-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0eb3d-122">Zie voor meer informatie over hoe dit element wordt gebruikt in een lijst weergeven, [lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="0eb3d-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0eb3d-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0eb3d-123">Example</span></span>

<span data-ttu-id="0eb3d-124">Het volgende voorbeeld ziet hoe u een selectie instellen voor een vermelding van een lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="0eb3d-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="0eb3d-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0eb3d-125">See Also</span></span>

[<span data-ttu-id="0eb3d-126">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="0eb3d-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0eb3d-127">EntrySelectedBy-Element voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="0eb3d-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0eb3d-128">SelectionSetName-Element voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="0eb3d-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="0eb3d-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="0eb3d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
