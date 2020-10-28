---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor TableColumnItem voor TableControl (opmaak)
description: Het element PropertyName voor TableColumnItem voor TableControl (opmaak)
ms.openlocfilehash: e83bbdb96d2755013cb9fe065cb98731ba44917f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665580"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="72c04-103">Het element PropertyName voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="72c04-103">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="72c04-104">Hiermee geeft u de eigenschap op waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="72c04-104">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="72c04-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) TableColumnItems element (indeling) TableColumnItem element (indeling) element eigenschap van TableColumnItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="72c04-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="72c04-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="72c04-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="72c04-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="72c04-107">Attributes and Elements</span></span>

<span data-ttu-id="72c04-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="72c04-108">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="72c04-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="72c04-109">Attributes</span></span>

<span data-ttu-id="72c04-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="72c04-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="72c04-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="72c04-111">Child Elements</span></span>

<span data-ttu-id="72c04-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="72c04-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="72c04-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="72c04-113">Parent Elements</span></span>

|<span data-ttu-id="72c04-114">Element</span><span class="sxs-lookup"><span data-stu-id="72c04-114">Element</span></span>|<span data-ttu-id="72c04-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="72c04-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="72c04-116">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="72c04-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="72c04-117">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="72c04-117">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="72c04-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="72c04-118">Text Value</span></span>

<span data-ttu-id="72c04-119">Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="72c04-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="72c04-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="72c04-120">Remarks</span></span>

<span data-ttu-id="72c04-121">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="72c04-121">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="72c04-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="72c04-122">Example</span></span>

<span data-ttu-id="72c04-123">In dit voor beeld ziet u een- `TableColumnItem` element dat de `Status` eigenschap van het [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -object aangeeft.</span><span class="sxs-lookup"><span data-stu-id="72c04-123">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="72c04-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="72c04-124">See Also</span></span>

[<span data-ttu-id="72c04-125">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="72c04-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="72c04-126">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="72c04-126">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="72c04-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="72c04-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
