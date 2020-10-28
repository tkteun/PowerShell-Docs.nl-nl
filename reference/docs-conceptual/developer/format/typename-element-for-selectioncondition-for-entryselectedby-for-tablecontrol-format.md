---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)
description: Het element TypeName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)
ms.openlocfilehash: 66e90ab33775cf35d5e98e45266996d2d1a622d7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659636"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="8683e-103">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8683e-103">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="8683e-104">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8683e-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="8683e-105">Wanneer dit type aanwezig is, wordt voldaan aan de voor waarde en wordt de tabelrij gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8683e-105">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="8683e-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element voor TableRowEntry (Format) SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (Format) voor SelectionCondition voor EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="8683e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8683e-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8683e-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8683e-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="8683e-108">Attributes and Elements</span></span>

<span data-ttu-id="8683e-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="8683e-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8683e-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8683e-110">Attributes</span></span>

<span data-ttu-id="8683e-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="8683e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8683e-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8683e-112">Child Elements</span></span>

<span data-ttu-id="8683e-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="8683e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8683e-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8683e-114">Parent Elements</span></span>

|<span data-ttu-id="8683e-115">Element</span><span class="sxs-lookup"><span data-stu-id="8683e-115">Element</span></span>|<span data-ttu-id="8683e-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8683e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8683e-117">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="8683e-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="8683e-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze tabelrij.</span><span class="sxs-lookup"><span data-stu-id="8683e-118">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8683e-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="8683e-119">Text Value</span></span>

<span data-ttu-id="8683e-120">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="8683e-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="8683e-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8683e-121">Remarks</span></span>

<span data-ttu-id="8683e-122">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="8683e-122">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="8683e-123">Zie voor [waarden definiëren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="8683e-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8683e-124">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="8683e-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8683e-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8683e-125">See Also</span></span>

[<span data-ttu-id="8683e-126">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="8683e-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8683e-127">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="8683e-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8683e-128">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="8683e-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="8683e-129">SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="8683e-129">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="8683e-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="8683e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
