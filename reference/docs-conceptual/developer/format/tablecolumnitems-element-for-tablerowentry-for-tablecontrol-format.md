---
title: TableColumnItems-element voor TableRowEntry voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 661b938e8db0e68e10dc05f552e4f3a14608bc55
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785146"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="8eb58-102">Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8eb58-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="8eb58-103">Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden in een rij worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8eb58-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="8eb58-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weergave (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (Format) TableColumnItems-element voor TableControlEntry voor TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8eb58-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8eb58-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8eb58-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8eb58-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="8eb58-106">Attributes and Elements</span></span>

<span data-ttu-id="8eb58-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableColumnItems` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="8eb58-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8eb58-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8eb58-108">Attributes</span></span>

<span data-ttu-id="8eb58-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="8eb58-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8eb58-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8eb58-110">Child Elements</span></span>

|<span data-ttu-id="8eb58-111">Element</span><span class="sxs-lookup"><span data-stu-id="8eb58-111">Element</span></span>|<span data-ttu-id="8eb58-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8eb58-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8eb58-113">Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8eb58-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="8eb58-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="8eb58-114">Required element.</span></span><br /><br /> <span data-ttu-id="8eb58-115">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="8eb58-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8eb58-116">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8eb58-116">Parent Elements</span></span>

|<span data-ttu-id="8eb58-117">Element</span><span class="sxs-lookup"><span data-stu-id="8eb58-117">Element</span></span>|<span data-ttu-id="8eb58-118">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8eb58-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8eb58-119">Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8eb58-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="8eb58-120">Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.</span><span class="sxs-lookup"><span data-stu-id="8eb58-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8eb58-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8eb58-121">Remarks</span></span>

<span data-ttu-id="8eb58-122">Een `TableColumnItem` element is vereist voor elke kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="8eb58-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="8eb58-123">De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="8eb58-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="8eb58-124">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="8eb58-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8eb58-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="8eb58-125">Example</span></span>

<span data-ttu-id="8eb58-126">In het volgende voor beeld ziet u een- `TableColumnItems` element dat drie eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) definieert.</span><span class="sxs-lookup"><span data-stu-id="8eb58-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8eb58-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8eb58-127">See Also</span></span>

[<span data-ttu-id="8eb58-128">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="8eb58-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8eb58-129">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="8eb58-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="8eb58-130">TableRowEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="8eb58-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="8eb58-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="8eb58-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
