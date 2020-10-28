---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TableRowEntries voor TableControl (opmaak)
description: Het element TableRowEntries voor TableControl (opmaak)
ms.openlocfilehash: 1df63e645234da8276c7ccc5af34e81a56475e43
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651470"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="0458b-103">Het element TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0458b-103">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="0458b-104">Hiermee worden de rijen van de tabel gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="0458b-104">Defines the rows of the table.</span></span>

<span data-ttu-id="0458b-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0458b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0458b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0458b-106">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0458b-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0458b-107">Attributes and Elements</span></span>

<span data-ttu-id="0458b-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableRowEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="0458b-108">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0458b-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0458b-109">Attributes</span></span>

<span data-ttu-id="0458b-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="0458b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0458b-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0458b-111">Child Elements</span></span>

|<span data-ttu-id="0458b-112">Element</span><span class="sxs-lookup"><span data-stu-id="0458b-112">Element</span></span>|<span data-ttu-id="0458b-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0458b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0458b-114">Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0458b-114">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="0458b-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="0458b-115">Required element.</span></span><br /><br /> <span data-ttu-id="0458b-116">Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.</span><span class="sxs-lookup"><span data-stu-id="0458b-116">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0458b-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0458b-117">Parent Elements</span></span>

|<span data-ttu-id="0458b-118">Element</span><span class="sxs-lookup"><span data-stu-id="0458b-118">Element</span></span>|<span data-ttu-id="0458b-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0458b-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0458b-120">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0458b-120">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="0458b-121">Definieert een tabel indeling voor een weer gave.</span><span class="sxs-lookup"><span data-stu-id="0458b-121">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0458b-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0458b-122">Remarks</span></span>

<span data-ttu-id="0458b-123">U moet een of meer `TableRowEntry` elementen opgeven voor de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="0458b-123">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="0458b-124">Er is geen maximum limiet voor het aantal `TableRowEntry` elementen dat kan worden toegevoegd en de volg orde hiervan is aanzienlijk.</span><span class="sxs-lookup"><span data-stu-id="0458b-124">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="0458b-125">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="0458b-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0458b-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0458b-126">Example</span></span>

<span data-ttu-id="0458b-127">In het volgende voor beeld ziet u een- `TableRowEntries` element dat een rij definieert waarin de waarden van twee eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0458b-127">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="0458b-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0458b-128">See Also</span></span>

[<span data-ttu-id="0458b-129">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="0458b-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0458b-130">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0458b-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="0458b-131">TableRowEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="0458b-131">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="0458b-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="0458b-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
