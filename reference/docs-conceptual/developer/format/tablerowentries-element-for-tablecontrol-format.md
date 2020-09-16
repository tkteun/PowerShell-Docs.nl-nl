---
title: TableRowEntries-element voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4cc5d354df3e552e181a95148caa020f0041db92
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785112"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="9e849-102">Het element TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9e849-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="9e849-103">Hiermee worden de rijen van de tabel gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9e849-103">Defines the rows of the table.</span></span>

<span data-ttu-id="9e849-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="9e849-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9e849-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9e849-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9e849-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9e849-106">Attributes and Elements</span></span>

<span data-ttu-id="9e849-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableRowEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="9e849-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9e849-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9e849-108">Attributes</span></span>

<span data-ttu-id="9e849-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="9e849-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9e849-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9e849-110">Child Elements</span></span>

|<span data-ttu-id="9e849-111">Element</span><span class="sxs-lookup"><span data-stu-id="9e849-111">Element</span></span>|<span data-ttu-id="9e849-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9e849-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e849-113">Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9e849-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="9e849-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="9e849-114">Required element.</span></span><br /><br /> <span data-ttu-id="9e849-115">Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.</span><span class="sxs-lookup"><span data-stu-id="9e849-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9e849-116">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9e849-116">Parent Elements</span></span>

|<span data-ttu-id="9e849-117">Element</span><span class="sxs-lookup"><span data-stu-id="9e849-117">Element</span></span>|<span data-ttu-id="9e849-118">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9e849-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e849-119">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9e849-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="9e849-120">Definieert een tabel indeling voor een weer gave.</span><span class="sxs-lookup"><span data-stu-id="9e849-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9e849-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9e849-121">Remarks</span></span>

<span data-ttu-id="9e849-122">U moet een of meer `TableRowEntry` elementen opgeven voor de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="9e849-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="9e849-123">Er is geen maximum limiet voor het aantal `TableRowEntry` elementen dat kan worden toegevoegd en de volg orde hiervan is aanzienlijk.</span><span class="sxs-lookup"><span data-stu-id="9e849-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="9e849-124">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="9e849-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9e849-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="9e849-125">Example</span></span>

<span data-ttu-id="9e849-126">In het volgende voor beeld ziet u een- `TableRowEntries` element dat een rij definieert waarin de waarden van twee eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9e849-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9e849-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9e849-127">See Also</span></span>

[<span data-ttu-id="9e849-128">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="9e849-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9e849-129">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9e849-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="9e849-130">TableRowEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9e849-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="9e849-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="9e849-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
