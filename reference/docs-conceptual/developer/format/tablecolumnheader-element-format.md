---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TableColumnHeader (opmaak)
description: Het element TableColumnHeader (opmaak)
ms.openlocfilehash: 30368512875b7c5c4cf3c686f3d09540dea1bd26
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651532"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="b0b57-103">Het element TableColumnHeader (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b0b57-103">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="b0b57-104">Hiermee definieert u het label, de breedte van de kolom en de uitlijning van het label voor een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="b0b57-104">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="b0b57-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableHeaders element voor TableControl (Format) TableColumnHeader-element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="b0b57-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b0b57-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b0b57-106">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b0b57-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b0b57-107">Attributes and Elements</span></span>

<span data-ttu-id="b0b57-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TableColumnHeader` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="b0b57-108">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b0b57-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b0b57-109">Attributes</span></span>

<span data-ttu-id="b0b57-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="b0b57-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b0b57-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b0b57-111">Child Elements</span></span>

|<span data-ttu-id="b0b57-112">Element</span><span class="sxs-lookup"><span data-stu-id="b0b57-112">Element</span></span>|<span data-ttu-id="b0b57-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b0b57-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0b57-114">Label element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="b0b57-114">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="b0b57-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b0b57-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b0b57-116">Hiermee wordt het label gedefinieerd dat boven aan de kolom wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b0b57-116">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="b0b57-117">Als er geen label is opgegeven, wordt de naam van de eigenschap waarvan de waarde wordt weer gegeven in de rijen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b0b57-117">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="b0b57-118">Het element Breedte voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b0b57-118">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="b0b57-119">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="b0b57-119">Required element.</span></span><br /><br /> <span data-ttu-id="b0b57-120">Geeft de breedte van de kolom aan (in tekens).</span><span class="sxs-lookup"><span data-stu-id="b0b57-120">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="b0b57-121">Het element Uitlijning voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b0b57-121">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="b0b57-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b0b57-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b0b57-123">Hiermee wordt aangegeven hoe het label van de kolom wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b0b57-123">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="b0b57-124">Als er geen uitlijning is opgegeven, wordt het label links uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="b0b57-124">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b0b57-125">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b0b57-125">Parent Elements</span></span>

|<span data-ttu-id="b0b57-126">Element</span><span class="sxs-lookup"><span data-stu-id="b0b57-126">Element</span></span>|<span data-ttu-id="b0b57-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b0b57-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0b57-128">Het element TableHeaders (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b0b57-128">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="b0b57-129">Hiermee worden de kolommen van een tabel weergave gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b0b57-129">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b0b57-130">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b0b57-130">Remarks</span></span>

<span data-ttu-id="b0b57-131">Geef een koptekst op voor elke kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="b0b57-131">Specify a header for each column of the table.</span></span> <span data-ttu-id="b0b57-132">De kolommen worden weer gegeven in de volg orde waarin de `TableColumnHeader` elementen zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b0b57-132">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="b0b57-133">Een tabel moet hetzelfde aantal `TableColumnHeader` elementen als `TableRowEntry` elementen hebben.</span><span class="sxs-lookup"><span data-stu-id="b0b57-133">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="b0b57-134">De kolomkop geeft aan hoe de tekst boven aan de tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b0b57-134">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="b0b57-135">De rij-items bepalen welke gegevens in de rijen van de tabel worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b0b57-135">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="b0b57-136">Zie [tabel weergave](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="b0b57-136">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b0b57-137">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b0b57-137">Example</span></span>

<span data-ttu-id="b0b57-138">In het volgende voor beeld ziet u twee `TableColumnHeader` elementen.</span><span class="sxs-lookup"><span data-stu-id="b0b57-138">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="b0b57-139">Het eerste element definieert een kolom waarvan het label kolom 1, een breedte van 16 tekens en waarvan het label aan de linkerkant wordt uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="b0b57-139">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="b0b57-140">Het tweede element definieert een kolom waarvan het label kolom 2 is, heeft een breedte van 10 tekens en waarvan het label in de kolom is gecentreerd.</span><span class="sxs-lookup"><span data-stu-id="b0b57-140">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b0b57-141">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b0b57-141">See Also</span></span>

[<span data-ttu-id="b0b57-142">Het element Uitlijning voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b0b57-142">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="b0b57-143">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="b0b57-143">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b0b57-144">Het element Label voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b0b57-144">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="b0b57-145">TableHeaders-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="b0b57-145">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="b0b57-146">Breedte voor TableColumnHeader voor het TableControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="b0b57-146">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="b0b57-147">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b0b57-147">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
