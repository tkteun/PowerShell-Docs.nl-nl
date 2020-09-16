---
title: Label element voor TableColumnHeader voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b7b1d6825d3bca0e36b230415d19c2ac48377a46
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785741"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="0826d-102">Het element Label voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0826d-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="0826d-103">Hiermee wordt het label gedefinieerd dat boven aan een kolom wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0826d-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="0826d-104">Dit element wordt gebruikt bij het definiëren van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="0826d-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="0826d-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weergave (indeling) TableControl element (Format) TableHeaders element voor TableControl (Format) TableColumnHeader-element voor TableHeaders voor TableControl (Format) voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0826d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0826d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0826d-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0826d-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0826d-107">Attributes and Elements</span></span>

<span data-ttu-id="0826d-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Label` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="0826d-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="0826d-109">Voor elke kolom is slechts één label toegestaan.</span><span class="sxs-lookup"><span data-stu-id="0826d-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="0826d-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0826d-110">Attributes</span></span>

<span data-ttu-id="0826d-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="0826d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0826d-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0826d-112">Child Elements</span></span>

<span data-ttu-id="0826d-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="0826d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0826d-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0826d-114">Parent Elements</span></span>

|<span data-ttu-id="0826d-115">Element</span><span class="sxs-lookup"><span data-stu-id="0826d-115">Element</span></span>|<span data-ttu-id="0826d-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0826d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0826d-117">TableColumnHeader-element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0826d-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="0826d-118">Hiermee definieert u een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="0826d-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0826d-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="0826d-119">Text Value</span></span>

<span data-ttu-id="0826d-120">Geef de tekst op die boven aan de kolom van de tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0826d-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="0826d-121">Er zijn geen beperkte tekens voor het kolom Label.</span><span class="sxs-lookup"><span data-stu-id="0826d-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="0826d-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0826d-122">Remarks</span></span>

<span data-ttu-id="0826d-123">Als er geen label is opgegeven, wordt de naam van de eigenschap waarvan de waarde wordt weer gegeven in de rijen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0826d-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="0826d-124">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="0826d-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0826d-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0826d-125">Example</span></span>

<span data-ttu-id="0826d-126">In dit voor beeld ziet u een `TableColumnHeader` element waarvan het label ' kolom 1 ' is.</span><span class="sxs-lookup"><span data-stu-id="0826d-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="0826d-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0826d-127">See Also</span></span>

[<span data-ttu-id="0826d-128">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="0826d-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0826d-129">Het element TableColumnHeader (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0826d-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="0826d-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="0826d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
