---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Breedte voor TableColumnHeader voor TableControl (opmaak)
description: Het element Breedte voor TableColumnHeader voor TableControl (opmaak)
ms.openlocfilehash: bde84f1d33b3d6b3b8c4462f870f978611cb434b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658259"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="49e37-103">Het element Breedte voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="49e37-103">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="49e37-104">Hiermee wordt de breedte (in tekens) van een kolom gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="49e37-104">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="49e37-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableHeaders element voor TableControl (indeling) TableColumnHeader element TableHeaders voor TableControl (indeling) breedte-element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="49e37-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="49e37-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="49e37-106">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49e37-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="49e37-107">Attributes and Elements</span></span>

<span data-ttu-id="49e37-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Width` element beschreven die worden gebruikt bij het definiëren van kolom koppen.</span><span class="sxs-lookup"><span data-stu-id="49e37-108">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="49e37-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="49e37-109">Attributes</span></span>

<span data-ttu-id="49e37-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="49e37-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="49e37-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="49e37-111">Child Elements</span></span>

<span data-ttu-id="49e37-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="49e37-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="49e37-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="49e37-113">Parent Elements</span></span>

|<span data-ttu-id="49e37-114">Element</span><span class="sxs-lookup"><span data-stu-id="49e37-114">Element</span></span>|<span data-ttu-id="49e37-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="49e37-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49e37-116">TableColumnHeader-element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="49e37-116">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="49e37-117">Hiermee definieert u een label, breedte en uitlijning van de gegevens voor een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="49e37-117">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="49e37-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="49e37-118">Text Value</span></span>

<span data-ttu-id="49e37-119">Als dat mogelijk is, geeft u een breedte (in tekens) op die groter is dan de lengte van de weer gegeven eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="49e37-119">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="49e37-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="49e37-120">Remarks</span></span>

<span data-ttu-id="49e37-121">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="49e37-121">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="49e37-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="49e37-122">Example</span></span>

<span data-ttu-id="49e37-123">In het volgende voor beeld ziet u een `TableColumnHeader` element waarvan de breedte 16 tekens is.</span><span class="sxs-lookup"><span data-stu-id="49e37-123">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="49e37-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="49e37-124">See Also</span></span>

[<span data-ttu-id="49e37-125">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="49e37-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="49e37-126">TableColumnHeader-element voor TableHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="49e37-126">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="49e37-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="49e37-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
