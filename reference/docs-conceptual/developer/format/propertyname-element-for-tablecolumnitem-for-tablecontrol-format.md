---
title: Het element PropertyName voor TableColumnItem voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bf267eeb83aef59abea2d945af12e849252309c8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772974"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="e6471-102">Het element PropertyName voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e6471-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="e6471-103">Hiermee geeft u de eigenschap op waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="e6471-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="e6471-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) TableColumnItems element (indeling) TableColumnItem element (indeling) element eigenschap van TableColumnItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="e6471-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e6471-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6471-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6471-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e6471-106">Attributes and Elements</span></span>

<span data-ttu-id="e6471-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="e6471-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6471-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e6471-108">Attributes</span></span>

<span data-ttu-id="e6471-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="e6471-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6471-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e6471-110">Child Elements</span></span>

<span data-ttu-id="e6471-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="e6471-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e6471-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e6471-112">Parent Elements</span></span>

|<span data-ttu-id="e6471-113">Element</span><span class="sxs-lookup"><span data-stu-id="e6471-113">Element</span></span>|<span data-ttu-id="e6471-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e6471-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6471-115">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e6471-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="e6471-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="e6471-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e6471-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="e6471-117">Text Value</span></span>

<span data-ttu-id="e6471-118">Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e6471-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6471-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e6471-119">Remarks</span></span>

<span data-ttu-id="e6471-120">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="e6471-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e6471-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e6471-121">Example</span></span>

<span data-ttu-id="e6471-122">In dit voor beeld ziet u een- `TableColumnItem` element dat de `Status` eigenschap van het [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -object aangeeft.</span><span class="sxs-lookup"><span data-stu-id="e6471-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="e6471-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e6471-123">See Also</span></span>

[<span data-ttu-id="e6471-124">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="e6471-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e6471-125">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e6471-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="e6471-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e6471-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
