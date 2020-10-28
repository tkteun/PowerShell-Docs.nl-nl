---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TableHeaders (opmaak)
description: Het element TableHeaders (opmaak)
ms.openlocfilehash: 5ac4dccae746c167ebf95add9f3d18030a2b3a99
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659828"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="2b6b7-103">Het element TableHeaders (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2b6b7-103">TableHeaders Element (Format)</span></span>

<span data-ttu-id="2b6b7-104">Hiermee worden de kopteksten van de kolommen van een tabel gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2b6b7-104">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="2b6b7-105">ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableHeaders element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="2b6b7-105">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b6b7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b6b7-106">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b6b7-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2b6b7-107">Attributes and Elements</span></span>

<span data-ttu-id="2b6b7-108">In de volgende secties worden de kenmerken, onderliggende elementen en bovenliggende elementen van het `TableHeaders` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="2b6b7-108">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="2b6b7-109">Er moet een onderliggend element zijn voor elke eigenschap van het object dat moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2b6b7-109">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="2b6b7-110">De informatie in de kolomkop wordt weer gegeven in de volg orde waarin de onderliggende elementen zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2b6b7-110">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b6b7-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2b6b7-111">Attributes</span></span>

<span data-ttu-id="2b6b7-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="2b6b7-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b6b7-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2b6b7-113">Child Elements</span></span>

|<span data-ttu-id="2b6b7-114">Element</span><span class="sxs-lookup"><span data-stu-id="2b6b7-114">Element</span></span>|<span data-ttu-id="2b6b7-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2b6b7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b6b7-116">Het element TableColumnHeader (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2b6b7-116">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="2b6b7-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2b6b7-117">Optional element.</span></span><br /><br /> <span data-ttu-id="2b6b7-118">Hiermee definieert u het label, de breedte en de uitlijning van de gegevens voor een kolom van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="2b6b7-118">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2b6b7-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2b6b7-119">Parent Elements</span></span>

|<span data-ttu-id="2b6b7-120">Element</span><span class="sxs-lookup"><span data-stu-id="2b6b7-120">Element</span></span>|<span data-ttu-id="2b6b7-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2b6b7-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b6b7-122">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2b6b7-122">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="2b6b7-123">Definieert een tabel indeling voor een weer gave.</span><span class="sxs-lookup"><span data-stu-id="2b6b7-123">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2b6b7-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2b6b7-124">Remarks</span></span>

<span data-ttu-id="2b6b7-125">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="2b6b7-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2b6b7-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2b6b7-126">Example</span></span>

<span data-ttu-id="2b6b7-127">In dit voor beeld ziet u een- `TableHeaders` element dat twee kolom koppen definieert.</span><span class="sxs-lookup"><span data-stu-id="2b6b7-127">This example shows a `TableHeaders` element that defines two column headers.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="2b6b7-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2b6b7-128">See Also</span></span>

[<span data-ttu-id="2b6b7-129">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="2b6b7-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2b6b7-130">Het element TableColumnHeader (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2b6b7-130">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="2b6b7-131">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2b6b7-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="2b6b7-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2b6b7-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
