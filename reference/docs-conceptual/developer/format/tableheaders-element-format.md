---
title: TableHeaders-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b3176cbe1316d5b30cb61831d9915a80389709a5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787424"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="c973a-102">Het element TableHeaders (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c973a-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="c973a-103">Hiermee worden de kopteksten van de kolommen van een tabel gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="c973a-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="c973a-104">ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableHeaders element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="c973a-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c973a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c973a-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c973a-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c973a-106">Attributes and Elements</span></span>

<span data-ttu-id="c973a-107">In de volgende secties worden de kenmerken, onderliggende elementen en bovenliggende elementen van het `TableHeaders` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c973a-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="c973a-108">Er moet een onderliggend element zijn voor elke eigenschap van het object dat moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c973a-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="c973a-109">De informatie in de kolomkop wordt weer gegeven in de volg orde waarin de onderliggende elementen zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c973a-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c973a-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c973a-110">Attributes</span></span>

<span data-ttu-id="c973a-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="c973a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c973a-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c973a-112">Child Elements</span></span>

|<span data-ttu-id="c973a-113">Element</span><span class="sxs-lookup"><span data-stu-id="c973a-113">Element</span></span>|<span data-ttu-id="c973a-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c973a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c973a-115">Het element TableColumnHeader (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c973a-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="c973a-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c973a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c973a-117">Hiermee definieert u het label, de breedte en de uitlijning van de gegevens voor een kolom van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="c973a-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c973a-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c973a-118">Parent Elements</span></span>

|<span data-ttu-id="c973a-119">Element</span><span class="sxs-lookup"><span data-stu-id="c973a-119">Element</span></span>|<span data-ttu-id="c973a-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c973a-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c973a-121">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c973a-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="c973a-122">Definieert een tabel indeling voor een weer gave.</span><span class="sxs-lookup"><span data-stu-id="c973a-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c973a-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c973a-123">Remarks</span></span>

<span data-ttu-id="c973a-124">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="c973a-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c973a-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c973a-125">Example</span></span>

<span data-ttu-id="c973a-126">In dit voor beeld ziet u een- `TableHeaders` element dat twee kolom koppen definieert.</span><span class="sxs-lookup"><span data-stu-id="c973a-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c973a-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c973a-127">See Also</span></span>

[<span data-ttu-id="c973a-128">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="c973a-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c973a-129">Het element TableColumnHeader (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c973a-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="c973a-130">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c973a-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="c973a-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c973a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
