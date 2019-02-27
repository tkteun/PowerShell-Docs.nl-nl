---
title: TableRowEntries-Element voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: d93750f919c1075f173dc9ac70324cc003e36879
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851140"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="fb22a-102">Het element TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fb22a-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="fb22a-103">Hiermee definieert u de rijen van de tabel.</span><span class="sxs-lookup"><span data-stu-id="fb22a-103">Defines the rows of the table.</span></span>

<span data-ttu-id="fb22a-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries Element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb22a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fb22a-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fb22a-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fb22a-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fb22a-106">Attributes and Elements</span></span>

<span data-ttu-id="fb22a-107">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `TableRowEntries` element.</span><span class="sxs-lookup"><span data-stu-id="fb22a-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb22a-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fb22a-108">Attributes</span></span>

<span data-ttu-id="fb22a-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="fb22a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fb22a-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fb22a-110">Child Elements</span></span>

|<span data-ttu-id="fb22a-111">Element</span><span class="sxs-lookup"><span data-stu-id="fb22a-111">Element</span></span>|<span data-ttu-id="fb22a-112">Description</span><span class="sxs-lookup"><span data-stu-id="fb22a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb22a-113">TableRowEntry-Element voor TableRowEntries voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb22a-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="fb22a-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="fb22a-114">Required element.</span></span><br /><br /> <span data-ttu-id="fb22a-115">De gegevens die worden weergegeven in een rij van de tabel definieert.</span><span class="sxs-lookup"><span data-stu-id="fb22a-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fb22a-116">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fb22a-116">Parent Elements</span></span>

|<span data-ttu-id="fb22a-117">Element</span><span class="sxs-lookup"><span data-stu-id="fb22a-117">Element</span></span>|<span data-ttu-id="fb22a-118">Description</span><span class="sxs-lookup"><span data-stu-id="fb22a-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb22a-119">TableControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb22a-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="fb22a-120">Hiermee definieert u een tabelindeling voor een weergave.</span><span class="sxs-lookup"><span data-stu-id="fb22a-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fb22a-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fb22a-121">Remarks</span></span>

<span data-ttu-id="fb22a-122">Moet u een of meer `TableRowEntry` -elementen voor de tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="fb22a-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="fb22a-123">Er is geen maximale limiet voor het aantal `TableRowEntry` elementen die kunnen worden toegevoegd en is de volgorde belangrijk.</span><span class="sxs-lookup"><span data-stu-id="fb22a-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="fb22a-124">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="fb22a-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fb22a-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="fb22a-125">Example</span></span>

<span data-ttu-id="fb22a-126">Het volgende voorbeeld wordt een `TableRowEntries` element dat definieert een rij waarin de waarden van twee eigenschappen van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span><span class="sxs-lookup"><span data-stu-id="fb22a-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fb22a-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fb22a-127">See Also</span></span>

[<span data-ttu-id="fb22a-128">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="fb22a-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fb22a-129">TableControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb22a-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="fb22a-130">TableRowEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fb22a-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="fb22a-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb22a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
