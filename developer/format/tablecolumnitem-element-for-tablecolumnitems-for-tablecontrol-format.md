---
title: TableColumnItem-element voor TableColumnItems voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143585"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="36194-102">Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="36194-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="36194-103">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="36194-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="36194-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (indeling) TableColumnItems-element voor TableControlEntry voor TableControl (Format) TableColumnItem element voor TableColumnItems voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="36194-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="36194-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="36194-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="36194-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="36194-106">Attributes and Elements</span></span>

<span data-ttu-id="36194-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van `TableColumnItem` het element beschreven.</span><span class="sxs-lookup"><span data-stu-id="36194-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="36194-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="36194-108">Attributes</span></span>

<span data-ttu-id="36194-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="36194-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="36194-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="36194-110">Child Elements</span></span>

|<span data-ttu-id="36194-111">Element</span><span class="sxs-lookup"><span data-stu-id="36194-111">Element</span></span>|<span data-ttu-id="36194-112">Description</span><span class="sxs-lookup"><span data-stu-id="36194-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36194-113">Alignment-element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="36194-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="36194-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="36194-114">Optional element.</span></span><br /><br /> <span data-ttu-id="36194-115">Bepaalt hoe de gegevens in een kolom van de rij worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36194-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="36194-116">Element formats Tring voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="36194-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="36194-117">Geeft een indelings patroon aan dat wordt gebruikt om de gegevens in de kolom van de rij op te maken.</span><span class="sxs-lookup"><span data-stu-id="36194-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="36194-118">Het element PropertyName voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="36194-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="36194-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="36194-119">Optional element.</span></span><br /><br /> <span data-ttu-id="36194-120">Hiermee geeft u de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36194-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="36194-121">Script block-element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="36194-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="36194-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="36194-122">Optional element.</span></span><br /><br /> <span data-ttu-id="36194-123">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de kolom van een rij.</span><span class="sxs-lookup"><span data-stu-id="36194-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="36194-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="36194-124">Parent Elements</span></span>

|<span data-ttu-id="36194-125">Element</span><span class="sxs-lookup"><span data-stu-id="36194-125">Element</span></span>|<span data-ttu-id="36194-126">Description</span><span class="sxs-lookup"><span data-stu-id="36194-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36194-127">TableColumnItems-element voor TableControlEntry voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="36194-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="36194-128">Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden worden weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="36194-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="36194-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="36194-129">Remarks</span></span>

<span data-ttu-id="36194-130">U kunt een eigenschap van een object of een script in elke kolom van de rij opgeven.</span><span class="sxs-lookup"><span data-stu-id="36194-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="36194-131">Als er geen onderliggende elementen zijn opgegeven, is het item een tijdelijke aanduiding en worden er geen gegevens weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36194-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="36194-132">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="36194-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="36194-133">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="36194-133">Example</span></span>

<span data-ttu-id="36194-134">In dit voor beeld `TableColumnItem` ziet u een-element dat de `Status` waarde van de eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weergeeft.</span><span class="sxs-lookup"><span data-stu-id="36194-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="36194-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="36194-135">See Also</span></span>

[<span data-ttu-id="36194-136">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="36194-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="36194-137">Alignment-element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="36194-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="36194-138">TableColumnItems-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="36194-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="36194-139">Element formats Tring voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="36194-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="36194-140">Het element PropertyName voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="36194-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="36194-141">Script block-element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="36194-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="36194-142">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="36194-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
