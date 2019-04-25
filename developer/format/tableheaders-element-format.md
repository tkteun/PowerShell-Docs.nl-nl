---
title: TableHeaders-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075406"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="efba6-102">Het element TableHeaders (opmaak)</span><span class="sxs-lookup"><span data-stu-id="efba6-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="efba6-103">Hiermee definieert u de koptekst van de kolommen van een tabel.</span><span class="sxs-lookup"><span data-stu-id="efba6-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="efba6-104">ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableHeaders-Element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="efba6-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="efba6-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="efba6-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="efba6-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="efba6-106">Attributes and Elements</span></span>

<span data-ttu-id="efba6-107">De volgende secties worden de kenmerken, de onderliggende elementen en de bovenliggende elementen van de `TableHeaders` element.</span><span class="sxs-lookup"><span data-stu-id="efba6-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="efba6-108">Er moet een onderliggend element voor elke eigenschap van het object dat moet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="efba6-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="efba6-109">De kolom header-informatie wordt weergegeven in de volgorde die de onderliggende elementen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="efba6-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="efba6-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="efba6-110">Attributes</span></span>

<span data-ttu-id="efba6-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="efba6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="efba6-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="efba6-112">Child Elements</span></span>

|<span data-ttu-id="efba6-113">Element</span><span class="sxs-lookup"><span data-stu-id="efba6-113">Element</span></span>|<span data-ttu-id="efba6-114">Description</span><span class="sxs-lookup"><span data-stu-id="efba6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="efba6-115">TableColumnHeader-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="efba6-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="efba6-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="efba6-116">Optional element.</span></span><br /><br /> <span data-ttu-id="efba6-117">Definieert het label, de breedte en de uitlijning van de gegevens voor een kolom van een tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="efba6-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="efba6-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="efba6-118">Parent Elements</span></span>

|<span data-ttu-id="efba6-119">Element</span><span class="sxs-lookup"><span data-stu-id="efba6-119">Element</span></span>|<span data-ttu-id="efba6-120">Description</span><span class="sxs-lookup"><span data-stu-id="efba6-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="efba6-121">TableControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="efba6-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="efba6-122">Hiermee definieert u een tabelindeling voor een weergave.</span><span class="sxs-lookup"><span data-stu-id="efba6-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="efba6-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="efba6-123">Remarks</span></span>

<span data-ttu-id="efba6-124">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="efba6-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="efba6-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="efba6-125">Example</span></span>

<span data-ttu-id="efba6-126">In dit voorbeeld ziet u een `TableHeaders` element dat twee kolomkoppen definieert.</span><span class="sxs-lookup"><span data-stu-id="efba6-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="efba6-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="efba6-127">See Also</span></span>

[<span data-ttu-id="efba6-128">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="efba6-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="efba6-129">TableColumnHeader-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="efba6-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="efba6-130">TableControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="efba6-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="efba6-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="efba6-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
