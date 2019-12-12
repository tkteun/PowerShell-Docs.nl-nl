---
title: TableColumnHeader-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353716"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="9ae3e-102">Het element TableColumnHeader (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9ae3e-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="9ae3e-103">Hiermee definieert u het label, de breedte van de kolom en de uitlijning van het label voor een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="9ae3e-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableHeaders element voor TableControl (Format) TableColumnHeader-element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ae3e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9ae3e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9ae3e-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9ae3e-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9ae3e-106">Attributes and Elements</span></span>

<span data-ttu-id="9ae3e-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `TableColumnHeader` beschreven.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9ae3e-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9ae3e-108">Attributes</span></span>

<span data-ttu-id="9ae3e-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9ae3e-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9ae3e-110">Child Elements</span></span>

|<span data-ttu-id="9ae3e-111">Element</span><span class="sxs-lookup"><span data-stu-id="9ae3e-111">Element</span></span>|<span data-ttu-id="9ae3e-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9ae3e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ae3e-113">Label element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ae3e-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="9ae3e-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="9ae3e-115">Hiermee wordt het label gedefinieerd dat boven aan de kolom wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="9ae3e-116">Als er geen label is opgegeven, wordt de naam van de eigenschap waarvan de waarde wordt weer gegeven in de rijen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="9ae3e-117">Width-element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ae3e-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="9ae3e-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-118">Required element.</span></span><br /><br /> <span data-ttu-id="9ae3e-119">Geeft de breedte van de kolom aan (in tekens).</span><span class="sxs-lookup"><span data-stu-id="9ae3e-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="9ae3e-120">Alignment-element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ae3e-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="9ae3e-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="9ae3e-122">Hiermee wordt aangegeven hoe het label van de kolom wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="9ae3e-123">Als er geen uitlijning is opgegeven, wordt het label links uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9ae3e-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9ae3e-124">Parent Elements</span></span>

|<span data-ttu-id="9ae3e-125">Element</span><span class="sxs-lookup"><span data-stu-id="9ae3e-125">Element</span></span>|<span data-ttu-id="9ae3e-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9ae3e-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ae3e-127">TableHeaders-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ae3e-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="9ae3e-128">Hiermee worden de kolommen van een tabel weergave gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9ae3e-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9ae3e-129">Remarks</span></span>

<span data-ttu-id="9ae3e-130">Geef een koptekst op voor elke kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="9ae3e-131">De kolommen worden weer gegeven in de volg orde waarin de `TableColumnHeader` elementen zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="9ae3e-132">Een tabel moet hetzelfde aantal `TableColumnHeader` elementen als `TableRowEntry` elementen hebben.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="9ae3e-133">De kolomkop geeft aan hoe de tekst boven aan de tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="9ae3e-134">De rij-items bepalen welke gegevens in de rijen van de tabel worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="9ae3e-135">Zie [tabel weergave](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9ae3e-136">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="9ae3e-136">Example</span></span>

<span data-ttu-id="9ae3e-137">In het volgende voor beeld ziet u twee `TableColumnHeader` elementen.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="9ae3e-138">Het eerste element definieert een kolom waarvan het label kolom 1, een breedte van 16 tekens en waarvan het label aan de linkerkant wordt uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="9ae3e-139">Het tweede element definieert een kolom waarvan het label kolom 2 is, heeft een breedte van 10 tekens en waarvan het label in de kolom is gecentreerd.</span><span class="sxs-lookup"><span data-stu-id="9ae3e-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9ae3e-140">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9ae3e-140">See Also</span></span>

[<span data-ttu-id="9ae3e-141">Alignment-element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ae3e-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="9ae3e-142">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="9ae3e-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9ae3e-143">Label element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ae3e-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="9ae3e-144">TableHeaders-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ae3e-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="9ae3e-145">Breedte voor TableColumnHeader voor het TableControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ae3e-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="9ae3e-146">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="9ae3e-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
