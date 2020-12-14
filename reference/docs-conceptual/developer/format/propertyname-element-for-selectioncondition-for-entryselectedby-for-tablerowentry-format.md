---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)
description: Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)
ms.openlocfilehash: dcb59fc438ae217870566f09204fb16b8f031614
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665784"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="29e6d-103">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="29e6d-103">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="29e6d-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="29e6d-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="29e6d-105">Als deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het tabel item gebruikt.</span><span class="sxs-lookup"><span data-stu-id="29e6d-105">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="29e6d-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element voor TableRowEntry (Format) SelectionCondition element voor EntrySelectedBy voor TableRowEntry (Format) voor SelectionCondition voor EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="29e6d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="29e6d-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="29e6d-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29e6d-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="29e6d-108">Attributes and Elements</span></span>

<span data-ttu-id="29e6d-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="29e6d-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="29e6d-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="29e6d-110">Attributes</span></span>

<span data-ttu-id="29e6d-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="29e6d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="29e6d-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="29e6d-112">Child Elements</span></span>

<span data-ttu-id="29e6d-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="29e6d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="29e6d-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="29e6d-114">Parent Elements</span></span>

|<span data-ttu-id="29e6d-115">Element</span><span class="sxs-lookup"><span data-stu-id="29e6d-115">Element</span></span>|<span data-ttu-id="29e6d-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="29e6d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29e6d-117">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="29e6d-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="29e6d-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit tabel item.</span><span class="sxs-lookup"><span data-stu-id="29e6d-118">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="29e6d-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="29e6d-119">Text Value</span></span>

<span data-ttu-id="29e6d-120">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="29e6d-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="29e6d-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="29e6d-121">Remarks</span></span>

<span data-ttu-id="29e6d-122">Voor de selectie voorwaarde moet ten minste één eigenschaps naam of een script blok worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="29e6d-122">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="29e6d-123">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="29e6d-123">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="29e6d-124">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="29e6d-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29e6d-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="29e6d-125">See Also</span></span>

[<span data-ttu-id="29e6d-126">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="29e6d-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="29e6d-127">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="29e6d-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="29e6d-128">Script block-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="29e6d-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="29e6d-129">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="29e6d-129">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="29e6d-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="29e6d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
