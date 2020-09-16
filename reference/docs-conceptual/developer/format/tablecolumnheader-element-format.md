---
title: TableColumnHeader-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6296aea5c567663b1c3c0a2cf0a57b21aa5394de
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785180"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="89192-102">Het element TableColumnHeader (opmaak)</span><span class="sxs-lookup"><span data-stu-id="89192-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="89192-103">Hiermee definieert u het label, de breedte van de kolom en de uitlijning van het label voor een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="89192-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="89192-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableHeaders element voor TableControl (Format) TableColumnHeader-element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="89192-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="89192-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="89192-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89192-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="89192-106">Attributes and Elements</span></span>

<span data-ttu-id="89192-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TableColumnHeader` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="89192-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="89192-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="89192-108">Attributes</span></span>

<span data-ttu-id="89192-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="89192-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="89192-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="89192-110">Child Elements</span></span>

|<span data-ttu-id="89192-111">Element</span><span class="sxs-lookup"><span data-stu-id="89192-111">Element</span></span>|<span data-ttu-id="89192-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="89192-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89192-113">Label element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="89192-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="89192-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="89192-114">Optional element.</span></span><br /><br /> <span data-ttu-id="89192-115">Hiermee wordt het label gedefinieerd dat boven aan de kolom wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="89192-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="89192-116">Als er geen label is opgegeven, wordt de naam van de eigenschap waarvan de waarde wordt weer gegeven in de rijen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="89192-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="89192-117">Het element Breedte voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="89192-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="89192-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="89192-118">Required element.</span></span><br /><br /> <span data-ttu-id="89192-119">Geeft de breedte van de kolom aan (in tekens).</span><span class="sxs-lookup"><span data-stu-id="89192-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="89192-120">Het element Uitlijning voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="89192-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="89192-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="89192-121">Optional element.</span></span><br /><br /> <span data-ttu-id="89192-122">Hiermee wordt aangegeven hoe het label van de kolom wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="89192-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="89192-123">Als er geen uitlijning is opgegeven, wordt het label links uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="89192-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="89192-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="89192-124">Parent Elements</span></span>

|<span data-ttu-id="89192-125">Element</span><span class="sxs-lookup"><span data-stu-id="89192-125">Element</span></span>|<span data-ttu-id="89192-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="89192-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89192-127">Het element TableHeaders (opmaak)</span><span class="sxs-lookup"><span data-stu-id="89192-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="89192-128">Hiermee worden de kolommen van een tabel weergave gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="89192-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89192-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="89192-129">Remarks</span></span>

<span data-ttu-id="89192-130">Geef een koptekst op voor elke kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="89192-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="89192-131">De kolommen worden weer gegeven in de volg orde waarin de `TableColumnHeader` elementen zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="89192-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="89192-132">Een tabel moet hetzelfde aantal `TableColumnHeader` elementen als `TableRowEntry` elementen hebben.</span><span class="sxs-lookup"><span data-stu-id="89192-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="89192-133">De kolomkop geeft aan hoe de tekst boven aan de tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="89192-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="89192-134">De rij-items bepalen welke gegevens in de rijen van de tabel worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="89192-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="89192-135">Zie [tabel weergave](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="89192-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="89192-136">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="89192-136">Example</span></span>

<span data-ttu-id="89192-137">In het volgende voor beeld ziet u twee `TableColumnHeader` elementen.</span><span class="sxs-lookup"><span data-stu-id="89192-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="89192-138">Het eerste element definieert een kolom waarvan het label kolom 1, een breedte van 16 tekens en waarvan het label aan de linkerkant wordt uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="89192-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="89192-139">Het tweede element definieert een kolom waarvan het label kolom 2 is, heeft een breedte van 10 tekens en waarvan het label in de kolom is gecentreerd.</span><span class="sxs-lookup"><span data-stu-id="89192-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="89192-140">Zie ook</span><span class="sxs-lookup"><span data-stu-id="89192-140">See Also</span></span>

[<span data-ttu-id="89192-141">Het element Uitlijning voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="89192-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="89192-142">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="89192-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="89192-143">Het element Label voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="89192-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="89192-144">TableHeaders-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="89192-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="89192-145">Breedte voor TableColumnHeader voor het TableControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="89192-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="89192-146">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="89192-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
