---
title: TableColumnItems-element voor TableRowEntry voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353688"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="ba6f4-102">Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ba6f4-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="ba6f4-103">Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden in een rij worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ba6f4-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="ba6f4-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (indeling) TableColumnItems-element voor TableControlEntry voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ba6f4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ba6f4-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ba6f4-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ba6f4-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ba6f4-106">Attributes and Elements</span></span>

<span data-ttu-id="ba6f4-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `TableColumnItems` beschreven.</span><span class="sxs-lookup"><span data-stu-id="ba6f4-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ba6f4-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ba6f4-108">Attributes</span></span>

<span data-ttu-id="ba6f4-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="ba6f4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ba6f4-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ba6f4-110">Child Elements</span></span>

|<span data-ttu-id="ba6f4-111">Element</span><span class="sxs-lookup"><span data-stu-id="ba6f4-111">Element</span></span>|<span data-ttu-id="ba6f4-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ba6f4-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ba6f4-113">TableColumnItem-element voor TableColumnItems voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ba6f4-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="ba6f4-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="ba6f4-114">Required element.</span></span><br /><br /> <span data-ttu-id="ba6f4-115">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="ba6f4-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ba6f4-116">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ba6f4-116">Parent Elements</span></span>

|<span data-ttu-id="ba6f4-117">Element</span><span class="sxs-lookup"><span data-stu-id="ba6f4-117">Element</span></span>|<span data-ttu-id="ba6f4-118">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ba6f4-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ba6f4-119">TableRowEntry-element voor TableRowEntries voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ba6f4-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="ba6f4-120">Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.</span><span class="sxs-lookup"><span data-stu-id="ba6f4-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ba6f4-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ba6f4-121">Remarks</span></span>

<span data-ttu-id="ba6f4-122">Voor elke kolom van de rij is een `TableColumnItem`-element vereist.</span><span class="sxs-lookup"><span data-stu-id="ba6f4-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="ba6f4-123">De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="ba6f4-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="ba6f4-124">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="ba6f4-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ba6f4-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ba6f4-125">Example</span></span>

<span data-ttu-id="ba6f4-126">In het volgende voor beeld ziet u een `TableColumnItems`-element dat drie eigenschappen van het [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -object definieert.</span><span class="sxs-lookup"><span data-stu-id="ba6f4-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ba6f4-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ba6f4-127">See Also</span></span>

[<span data-ttu-id="ba6f4-128">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="ba6f4-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ba6f4-129">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ba6f4-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="ba6f4-130">TableRowEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ba6f4-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="ba6f4-131">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="ba6f4-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
