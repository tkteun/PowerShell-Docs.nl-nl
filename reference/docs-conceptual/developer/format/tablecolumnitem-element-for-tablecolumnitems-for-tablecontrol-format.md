---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)
description: Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)
ms.openlocfilehash: 8ef5158c9bb9f074d5c58190d4d3b20c10c83744
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659853"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="268b9-103">Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="268b9-103">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="268b9-104">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="268b9-104">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="268b9-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (Format) TableColumnItems-element voor TableControlEntry voor TableControl (Format) TableColumnItem-element voor TableColumnItems voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="268b9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="268b9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="268b9-106">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="268b9-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="268b9-107">Attributes and Elements</span></span>

<span data-ttu-id="268b9-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableColumnItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="268b9-108">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="268b9-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="268b9-109">Attributes</span></span>

<span data-ttu-id="268b9-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="268b9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="268b9-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="268b9-111">Child Elements</span></span>

|<span data-ttu-id="268b9-112">Element</span><span class="sxs-lookup"><span data-stu-id="268b9-112">Element</span></span>|<span data-ttu-id="268b9-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="268b9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="268b9-114">Het element Uitlijning voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="268b9-114">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="268b9-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="268b9-115">Optional element.</span></span><br /><br /> <span data-ttu-id="268b9-116">Bepaalt hoe de gegevens in een kolom van de rij worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="268b9-116">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="268b9-117">Het element FormatString voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="268b9-117">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="268b9-118">Geeft een indelings patroon aan dat wordt gebruikt om de gegevens in de kolom van de rij op te maken.</span><span class="sxs-lookup"><span data-stu-id="268b9-118">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="268b9-119">Het element PropertyName voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="268b9-119">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="268b9-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="268b9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="268b9-121">Hiermee geeft u de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="268b9-121">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="268b9-122">Het element ScriptBlock voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="268b9-122">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="268b9-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="268b9-123">Optional element.</span></span><br /><br /> <span data-ttu-id="268b9-124">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de kolom van een rij.</span><span class="sxs-lookup"><span data-stu-id="268b9-124">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="268b9-125">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="268b9-125">Parent Elements</span></span>

|<span data-ttu-id="268b9-126">Element</span><span class="sxs-lookup"><span data-stu-id="268b9-126">Element</span></span>|<span data-ttu-id="268b9-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="268b9-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="268b9-128">TableColumnItems-element voor TableControlEntry voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="268b9-128">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="268b9-129">Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden worden weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="268b9-129">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="268b9-130">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="268b9-130">Remarks</span></span>

<span data-ttu-id="268b9-131">U kunt een eigenschap van een object of een script in elke kolom van de rij opgeven.</span><span class="sxs-lookup"><span data-stu-id="268b9-131">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="268b9-132">Als er geen onderliggende elementen zijn opgegeven, is het item een tijdelijke aanduiding en worden er geen gegevens weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="268b9-132">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="268b9-133">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="268b9-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="268b9-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="268b9-134">Example</span></span>

<span data-ttu-id="268b9-135">In dit voor beeld ziet u een- `TableColumnItem` element dat de waarde van de `Status` eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weergeeft.</span><span class="sxs-lookup"><span data-stu-id="268b9-135">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="268b9-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="268b9-136">See Also</span></span>

[<span data-ttu-id="268b9-137">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="268b9-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="268b9-138">Het element Uitlijning voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="268b9-138">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="268b9-139">TableColumnItems-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="268b9-139">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="268b9-140">Het element FormatString voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="268b9-140">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="268b9-141">Het element PropertyName voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="268b9-141">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="268b9-142">Het element ScriptBlock voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="268b9-142">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="268b9-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="268b9-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
