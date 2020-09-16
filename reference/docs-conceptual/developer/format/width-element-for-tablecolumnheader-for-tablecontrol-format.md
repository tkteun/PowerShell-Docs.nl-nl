---
title: Width-element voor TableColumnHeader voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9540d3d351041ad7cb98a21bb360ebea7eca117
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779910"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="38dfb-102">Het element Breedte voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="38dfb-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="38dfb-103">Hiermee wordt de breedte (in tekens) van een kolom gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="38dfb-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="38dfb-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableHeaders element voor TableControl (indeling) TableColumnHeader element TableHeaders voor TableControl (indeling) breedte-element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="38dfb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38dfb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="38dfb-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38dfb-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="38dfb-106">Attributes and Elements</span></span>

<span data-ttu-id="38dfb-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Width` element beschreven die worden gebruikt bij het definiëren van kolom koppen.</span><span class="sxs-lookup"><span data-stu-id="38dfb-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="38dfb-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="38dfb-108">Attributes</span></span>

<span data-ttu-id="38dfb-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="38dfb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38dfb-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="38dfb-110">Child Elements</span></span>

<span data-ttu-id="38dfb-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="38dfb-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="38dfb-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="38dfb-112">Parent Elements</span></span>

|<span data-ttu-id="38dfb-113">Element</span><span class="sxs-lookup"><span data-stu-id="38dfb-113">Element</span></span>|<span data-ttu-id="38dfb-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="38dfb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38dfb-115">TableColumnHeader-element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="38dfb-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="38dfb-116">Hiermee definieert u een label, breedte en uitlijning van de gegevens voor een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="38dfb-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="38dfb-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="38dfb-117">Text Value</span></span>

<span data-ttu-id="38dfb-118">Als dat mogelijk is, geeft u een breedte (in tekens) op die groter is dan de lengte van de weer gegeven eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="38dfb-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="38dfb-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="38dfb-119">Remarks</span></span>

<span data-ttu-id="38dfb-120">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="38dfb-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="38dfb-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="38dfb-121">Example</span></span>

<span data-ttu-id="38dfb-122">In het volgende voor beeld ziet u een `TableColumnHeader` element waarvan de breedte 16 tekens is.</span><span class="sxs-lookup"><span data-stu-id="38dfb-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="38dfb-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="38dfb-123">See Also</span></span>

[<span data-ttu-id="38dfb-124">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="38dfb-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="38dfb-125">TableColumnHeader-element voor TableHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="38dfb-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="38dfb-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="38dfb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
