---
title: TableRowEntry-element voor TableRowEntries voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 83076ae5b2c48992ce5e621c65fc9937efb68b87
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787407"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="73b51-102">Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73b51-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="73b51-103">Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.</span><span class="sxs-lookup"><span data-stu-id="73b51-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="73b51-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="73b51-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73b51-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="73b51-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73b51-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="73b51-106">Attributes and Elements</span></span>

<span data-ttu-id="73b51-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableRowEntry` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="73b51-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="73b51-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="73b51-108">Attributes</span></span>

<span data-ttu-id="73b51-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="73b51-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73b51-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="73b51-110">Child Elements</span></span>

|<span data-ttu-id="73b51-111">Element</span><span class="sxs-lookup"><span data-stu-id="73b51-111">Element</span></span>|<span data-ttu-id="73b51-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="73b51-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73b51-113">EntrySelectedBy-element voor TableRowEntry voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="73b51-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="73b51-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="73b51-114">Required element.</span></span><br /><br /> <span data-ttu-id="73b51-115">Hiermee worden de objecten gedefinieerd waarvan de eigenschaps waarden worden weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="73b51-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="73b51-116">Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73b51-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="73b51-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="73b51-117">Required element.</span></span><br /><br /> <span data-ttu-id="73b51-118">Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="73b51-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="73b51-119">Omloop-element voor TableRowEntry voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="73b51-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="73b51-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73b51-120">Optional element.</span></span><br /><br /> <span data-ttu-id="73b51-121">Geeft aan dat de tekst die de kolom breedte overschrijdt wordt weer gegeven op de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="73b51-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="73b51-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="73b51-122">Parent Elements</span></span>

|<span data-ttu-id="73b51-123">Element</span><span class="sxs-lookup"><span data-stu-id="73b51-123">Element</span></span>|<span data-ttu-id="73b51-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="73b51-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73b51-125">Het element TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73b51-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="73b51-126">Hiermee worden de rijen van de tabel gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="73b51-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="73b51-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="73b51-127">Remarks</span></span>

<span data-ttu-id="73b51-128">Er `TableColumnItems` moet één element en één `EntrySelectedBy` element worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="73b51-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="73b51-129">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="73b51-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="73b51-130">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="73b51-130">Example</span></span>

<span data-ttu-id="73b51-131">In het volgende voor beeld ziet u een- `TableRowEntry` element dat een rij definieert waarin de waarden van twee eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="73b51-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
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
```

## <a name="see-also"></a><span data-ttu-id="73b51-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="73b51-132">See Also</span></span>

[<span data-ttu-id="73b51-133">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="73b51-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="73b51-134">EntrySelectedBy-element voor TableRowEntry voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="73b51-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="73b51-135">Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73b51-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="73b51-136">Het element TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73b51-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="73b51-137">Omloop-element voor TableRowEntry voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="73b51-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="73b51-138">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="73b51-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
