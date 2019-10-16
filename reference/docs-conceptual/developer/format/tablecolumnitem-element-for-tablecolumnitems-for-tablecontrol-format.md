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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358803"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="98b45-102">Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="98b45-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="98b45-103">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="98b45-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="98b45-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (indeling) TableColumnItems-element voor TableControlEntry voor TableControl (Format) TableColumnItem element voor TableColumnItems voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="98b45-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98b45-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="98b45-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98b45-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="98b45-106">Attributes and Elements</span></span>

<span data-ttu-id="98b45-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `TableColumnItem` beschreven.</span><span class="sxs-lookup"><span data-stu-id="98b45-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="98b45-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="98b45-108">Attributes</span></span>

<span data-ttu-id="98b45-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="98b45-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98b45-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="98b45-110">Child Elements</span></span>

|<span data-ttu-id="98b45-111">Element</span><span class="sxs-lookup"><span data-stu-id="98b45-111">Element</span></span>|<span data-ttu-id="98b45-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="98b45-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98b45-113">Alignment-element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="98b45-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="98b45-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="98b45-114">Optional element.</span></span><br /><br /> <span data-ttu-id="98b45-115">Bepaalt hoe de gegevens in een kolom van de rij worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="98b45-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="98b45-116">Element formats Tring voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="98b45-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="98b45-117">Geeft een indelings patroon aan dat wordt gebruikt om de gegevens in de kolom van de rij op te maken.</span><span class="sxs-lookup"><span data-stu-id="98b45-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="98b45-118">Het element PropertyName voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="98b45-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="98b45-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="98b45-119">Optional element.</span></span><br /><br /> <span data-ttu-id="98b45-120">Hiermee geeft u de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="98b45-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="98b45-121">Script block-element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="98b45-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="98b45-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="98b45-122">Optional element.</span></span><br /><br /> <span data-ttu-id="98b45-123">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de kolom van een rij.</span><span class="sxs-lookup"><span data-stu-id="98b45-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="98b45-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="98b45-124">Parent Elements</span></span>

|<span data-ttu-id="98b45-125">Element</span><span class="sxs-lookup"><span data-stu-id="98b45-125">Element</span></span>|<span data-ttu-id="98b45-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="98b45-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98b45-127">TableColumnItems-element voor TableControlEntry voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="98b45-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="98b45-128">Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden worden weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="98b45-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="98b45-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="98b45-129">Remarks</span></span>

<span data-ttu-id="98b45-130">U kunt een eigenschap van een object of een script in elke kolom van de rij opgeven.</span><span class="sxs-lookup"><span data-stu-id="98b45-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="98b45-131">Als er geen onderliggende elementen zijn opgegeven, is het item een tijdelijke aanduiding en worden er geen gegevens weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="98b45-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="98b45-132">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="98b45-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="98b45-133">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="98b45-133">Example</span></span>

<span data-ttu-id="98b45-134">In dit voor beeld wordt een element `TableColumnItem` weer gegeven met de waarde van de eigenschap `Status` van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="98b45-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="98b45-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="98b45-135">See Also</span></span>

[<span data-ttu-id="98b45-136">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="98b45-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="98b45-137">Alignment-element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="98b45-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="98b45-138">TableColumnItems-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="98b45-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="98b45-139">Element formats Tring voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="98b45-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="98b45-140">Het element PropertyName voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="98b45-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="98b45-141">Script block-element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="98b45-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="98b45-142">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="98b45-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
