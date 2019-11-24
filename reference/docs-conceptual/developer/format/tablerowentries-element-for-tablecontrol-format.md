---
title: TableRowEntries-element voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358788"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="2c7f0-102">Het element TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2c7f0-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="2c7f0-103">Hiermee worden de rijen van de tabel gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2c7f0-103">Defines the rows of the table.</span></span>

<span data-ttu-id="2c7f0-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="2c7f0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2c7f0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2c7f0-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c7f0-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2c7f0-106">Attributes and Elements</span></span>

<span data-ttu-id="2c7f0-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `TableRowEntries` beschreven.</span><span class="sxs-lookup"><span data-stu-id="2c7f0-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2c7f0-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2c7f0-108">Attributes</span></span>

<span data-ttu-id="2c7f0-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="2c7f0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2c7f0-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2c7f0-110">Child Elements</span></span>

|<span data-ttu-id="2c7f0-111">Element</span><span class="sxs-lookup"><span data-stu-id="2c7f0-111">Element</span></span>|<span data-ttu-id="2c7f0-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2c7f0-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c7f0-113">TableRowEntry-element voor TableRowEntries voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="2c7f0-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="2c7f0-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="2c7f0-114">Required element.</span></span><br /><br /> <span data-ttu-id="2c7f0-115">Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.</span><span class="sxs-lookup"><span data-stu-id="2c7f0-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2c7f0-116">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2c7f0-116">Parent Elements</span></span>

|<span data-ttu-id="2c7f0-117">Element</span><span class="sxs-lookup"><span data-stu-id="2c7f0-117">Element</span></span>|<span data-ttu-id="2c7f0-118">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2c7f0-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c7f0-119">TableControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2c7f0-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="2c7f0-120">Definieert een tabel indeling voor een weer gave.</span><span class="sxs-lookup"><span data-stu-id="2c7f0-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2c7f0-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2c7f0-121">Remarks</span></span>

<span data-ttu-id="2c7f0-122">U moet een of meer `TableRowEntry` elementen voor de tabel weergave opgeven.</span><span class="sxs-lookup"><span data-stu-id="2c7f0-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="2c7f0-123">Er is geen maximum limiet voor het aantal `TableRowEntry` elementen dat kan worden toegevoegd, en de volg orde hiervan is aanzienlijk.</span><span class="sxs-lookup"><span data-stu-id="2c7f0-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="2c7f0-124">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="2c7f0-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2c7f0-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2c7f0-125">Example</span></span>

<span data-ttu-id="2c7f0-126">In het volgende voor beeld ziet u een `TableRowEntries`-element dat een rij definieert waarin de waarden van twee eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2c7f0-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2c7f0-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2c7f0-127">See Also</span></span>

[<span data-ttu-id="2c7f0-128">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="2c7f0-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2c7f0-129">TableControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2c7f0-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="2c7f0-130">TableRowEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2c7f0-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="2c7f0-131">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2c7f0-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
