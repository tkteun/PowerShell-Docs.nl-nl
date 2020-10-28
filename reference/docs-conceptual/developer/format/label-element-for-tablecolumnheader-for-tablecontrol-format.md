---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Label voor TableColumnHeader voor TableControl (opmaak)
description: Het element Label voor TableColumnHeader voor TableControl (opmaak)
ms.openlocfilehash: fe4c209903c04e683b44e2bdcbf381adb6874ace
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667790"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="d0fb1-103">Het element Label voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d0fb1-103">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="d0fb1-104">Hiermee wordt het label gedefinieerd dat boven aan een kolom wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-104">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="d0fb1-105">Dit element wordt gebruikt bij het definiëren van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-105">This element is used when defining a table view.</span></span>

<span data-ttu-id="d0fb1-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weergave (indeling) TableControl element (Format) TableHeaders element voor TableControl (Format) TableColumnHeader-element voor TableHeaders voor TableControl (Format) voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="d0fb1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0fb1-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0fb1-107">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0fb1-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d0fb1-108">Attributes and Elements</span></span>

<span data-ttu-id="d0fb1-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Label` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-109">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="d0fb1-110">Voor elke kolom is slechts één label toegestaan.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-110">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0fb1-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d0fb1-111">Attributes</span></span>

<span data-ttu-id="d0fb1-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0fb1-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d0fb1-113">Child Elements</span></span>

<span data-ttu-id="d0fb1-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d0fb1-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d0fb1-115">Parent Elements</span></span>

|<span data-ttu-id="d0fb1-116">Element</span><span class="sxs-lookup"><span data-stu-id="d0fb1-116">Element</span></span>|<span data-ttu-id="d0fb1-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d0fb1-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0fb1-118">TableColumnHeader-element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="d0fb1-118">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="d0fb1-119">Hiermee definieert u een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-119">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d0fb1-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="d0fb1-120">Text Value</span></span>

<span data-ttu-id="d0fb1-121">Geef de tekst op die boven aan de kolom van de tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-121">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="d0fb1-122">Er zijn geen beperkte tekens voor het kolom Label.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-122">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0fb1-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d0fb1-123">Remarks</span></span>

<span data-ttu-id="d0fb1-124">Als er geen label is opgegeven, wordt de naam van de eigenschap waarvan de waarde wordt weer gegeven in de rijen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-124">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="d0fb1-125">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d0fb1-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d0fb1-126">Example</span></span>

<span data-ttu-id="d0fb1-127">In dit voor beeld ziet u een `TableColumnHeader` element waarvan het label ' kolom 1 ' is.</span><span class="sxs-lookup"><span data-stu-id="d0fb1-127">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="d0fb1-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d0fb1-128">See Also</span></span>

[<span data-ttu-id="d0fb1-129">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="d0fb1-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d0fb1-130">Het element TableColumnHeader (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d0fb1-130">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="d0fb1-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d0fb1-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
