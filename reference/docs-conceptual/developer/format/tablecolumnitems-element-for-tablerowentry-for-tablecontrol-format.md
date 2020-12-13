---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)
description: Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)
ms.openlocfilehash: 4d600a366d2be1c453f05b301bdf575351dd51c1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667756"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="e5cb4-103">Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e5cb4-103">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="e5cb4-104">Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden in een rij worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e5cb4-104">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="e5cb4-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weergave (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (Format) TableColumnItems-element voor TableControlEntry voor TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5cb4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5cb4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5cb4-106">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5cb4-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e5cb4-107">Attributes and Elements</span></span>

<span data-ttu-id="e5cb4-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableColumnItems` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="e5cb4-108">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5cb4-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e5cb4-109">Attributes</span></span>

<span data-ttu-id="e5cb4-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="e5cb4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5cb4-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5cb4-111">Child Elements</span></span>

|<span data-ttu-id="e5cb4-112">Element</span><span class="sxs-lookup"><span data-stu-id="e5cb4-112">Element</span></span>|<span data-ttu-id="e5cb4-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5cb4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5cb4-114">Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e5cb4-114">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="e5cb4-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="e5cb4-115">Required element.</span></span><br /><br /> <span data-ttu-id="e5cb4-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="e5cb4-116">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5cb4-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5cb4-117">Parent Elements</span></span>

|<span data-ttu-id="e5cb4-118">Element</span><span class="sxs-lookup"><span data-stu-id="e5cb4-118">Element</span></span>|<span data-ttu-id="e5cb4-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5cb4-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5cb4-120">Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e5cb4-120">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="e5cb4-121">Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.</span><span class="sxs-lookup"><span data-stu-id="e5cb4-121">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5cb4-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e5cb4-122">Remarks</span></span>

<span data-ttu-id="e5cb4-123">Een `TableColumnItem` element is vereist voor elke kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="e5cb4-123">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="e5cb4-124">De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="e5cb4-124">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="e5cb4-125">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="e5cb4-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e5cb4-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e5cb4-126">Example</span></span>

<span data-ttu-id="e5cb4-127">In het volgende voor beeld ziet u een- `TableColumnItems` element dat drie eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) definieert.</span><span class="sxs-lookup"><span data-stu-id="e5cb4-127">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="e5cb4-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e5cb4-128">See Also</span></span>

[<span data-ttu-id="e5cb4-129">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="e5cb4-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e5cb4-130">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5cb4-130">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="e5cb4-131">TableRowEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5cb4-131">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="e5cb4-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e5cb4-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
