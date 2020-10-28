---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)
description: Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)
ms.openlocfilehash: a984bda6b8fba3a5cb9485576ffd847f0d366d3e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659887"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="a6b12-103">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a6b12-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="a6b12-104">Hiermee geeft u het script blok op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a6b12-104">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="a6b12-105">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het tabel item gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a6b12-105">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="a6b12-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element voor TableRowEntry (Format) SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (Format) script block-element voor SelectionCondition voor EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="a6b12-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6b12-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a6b12-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6b12-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a6b12-108">Attributes and Elements</span></span>

<span data-ttu-id="a6b12-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="a6b12-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6b12-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a6b12-110">Attributes</span></span>

<span data-ttu-id="a6b12-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="a6b12-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6b12-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a6b12-112">Child Elements</span></span>

<span data-ttu-id="a6b12-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="a6b12-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6b12-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a6b12-114">Parent Elements</span></span>

|<span data-ttu-id="a6b12-115">Element</span><span class="sxs-lookup"><span data-stu-id="a6b12-115">Element</span></span>|<span data-ttu-id="a6b12-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a6b12-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6b12-117">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a6b12-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a6b12-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit tabel item.</span><span class="sxs-lookup"><span data-stu-id="a6b12-118">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a6b12-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="a6b12-119">Text Value</span></span>

<span data-ttu-id="a6b12-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="a6b12-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6b12-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a6b12-121">Remarks</span></span>

<span data-ttu-id="a6b12-122">Voor de selectie voorwaarde moet ten minste één script blok of een eigenschaps naam worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a6b12-122">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="a6b12-123">Zie voor [waarden definiëren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="a6b12-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a6b12-124">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="a6b12-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6b12-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a6b12-125">See Also</span></span>

[<span data-ttu-id="a6b12-126">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="a6b12-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a6b12-127">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="a6b12-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a6b12-128">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a6b12-128">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="a6b12-129">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a6b12-129">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a6b12-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a6b12-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
