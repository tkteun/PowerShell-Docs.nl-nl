---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)
description: Het element TypeName voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)
ms.openlocfilehash: 2e8246e3ef2cba38824d8f8004acfffc3236df13
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645556"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="a4b72-103">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4b72-103">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="a4b72-104">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a4b72-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="a4b72-105">Wanneer dit type aanwezig is, wordt de vermelding in de lijst gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a4b72-105">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="a4b72-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het object (indeling) ListControl element (indeling) (Format) element list item voor ListControl (indeling) element List entry voor List Entries (Format) EntrySelectedBy element voor List entry voor ListControl (Format) SelectionCondition-element voor het object voor de ListControl (Format) voor de SelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="a4b72-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a4b72-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4b72-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a4b72-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a4b72-108">Attributes and Elements</span></span>

<span data-ttu-id="a4b72-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="a4b72-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a4b72-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a4b72-110">Attributes</span></span>

<span data-ttu-id="a4b72-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="a4b72-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a4b72-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a4b72-112">Child Elements</span></span>

<span data-ttu-id="a4b72-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="a4b72-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a4b72-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a4b72-114">Parent Elements</span></span>

|<span data-ttu-id="a4b72-115">Element</span><span class="sxs-lookup"><span data-stu-id="a4b72-115">Element</span></span>|<span data-ttu-id="a4b72-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a4b72-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4b72-117">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4b72-117">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="a4b72-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst vermelding.</span><span class="sxs-lookup"><span data-stu-id="a4b72-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a4b72-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="a4b72-119">Text Value</span></span>

<span data-ttu-id="a4b72-120">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="a4b72-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4b72-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a4b72-121">Remarks</span></span>

<span data-ttu-id="a4b72-122">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a4b72-122">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="a4b72-123">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="a4b72-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a4b72-124">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over andere onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="a4b72-124">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a4b72-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a4b72-125">See Also</span></span>

[<span data-ttu-id="a4b72-126">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="a4b72-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a4b72-127">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="a4b72-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a4b72-128">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4b72-128">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="a4b72-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a4b72-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
