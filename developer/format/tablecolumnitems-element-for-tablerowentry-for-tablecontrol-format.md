---
title: TableColumnItems-Element voor TableRowEntry voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056903"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="bc399-102">Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="bc399-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="bc399-103">Definieert de eigenschappen of scripts waarvan de waarden in een rij worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bc399-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="bc399-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries Element voor TableControl (indeling) TableRowEntry-Element voor TableRowEntries voor TableControl (indeling) TableColumnItems-Element voor TableControlEntry voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="bc399-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc399-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="bc399-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc399-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="bc399-106">Attributes and Elements</span></span>

<span data-ttu-id="bc399-107">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `TableColumnItems` element.</span><span class="sxs-lookup"><span data-stu-id="bc399-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc399-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="bc399-108">Attributes</span></span>

<span data-ttu-id="bc399-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="bc399-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc399-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bc399-110">Child Elements</span></span>

|<span data-ttu-id="bc399-111">Element</span><span class="sxs-lookup"><span data-stu-id="bc399-111">Element</span></span>|<span data-ttu-id="bc399-112">Description</span><span class="sxs-lookup"><span data-stu-id="bc399-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc399-113">TableColumnItem-Element voor TableColumnItems voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="bc399-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="bc399-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="bc399-114">Required element.</span></span><br /><br /> <span data-ttu-id="bc399-115">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="bc399-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bc399-116">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bc399-116">Parent Elements</span></span>

|<span data-ttu-id="bc399-117">Element</span><span class="sxs-lookup"><span data-stu-id="bc399-117">Element</span></span>|<span data-ttu-id="bc399-118">Description</span><span class="sxs-lookup"><span data-stu-id="bc399-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc399-119">TableRowEntry-Element voor TableRowEntries voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="bc399-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="bc399-120">De gegevens die worden weergegeven in een rij van de tabel definieert.</span><span class="sxs-lookup"><span data-stu-id="bc399-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bc399-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bc399-121">Remarks</span></span>

<span data-ttu-id="bc399-122">Een `TableColumnItem` element is vereist voor elke kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="bc399-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="bc399-123">De eerste vermelding wordt weergegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="bc399-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="bc399-124">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="bc399-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bc399-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="bc399-125">Example</span></span>

<span data-ttu-id="bc399-126">Het volgende voorbeeld wordt een `TableColumnItems` element dat drie eigenschappen van bepaalt de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span><span class="sxs-lookup"><span data-stu-id="bc399-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bc399-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bc399-127">See Also</span></span>

[<span data-ttu-id="bc399-128">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="bc399-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bc399-129">TableColumnItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="bc399-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="bc399-130">TableRowEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="bc399-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="bc399-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc399-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
