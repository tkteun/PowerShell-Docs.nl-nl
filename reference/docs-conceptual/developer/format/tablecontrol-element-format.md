---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TableControl (opmaak)
description: Het element TableControl (opmaak)
ms.openlocfilehash: 93e05e22d61504d7781b6f3c07f9a3fd0b3c9e8a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651457"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="c1e21-103">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1e21-103">TableControl Element (Format)</span></span>

<span data-ttu-id="c1e21-104">Definieert een tabel indeling voor een weer gave.</span><span class="sxs-lookup"><span data-stu-id="c1e21-104">Defines a table format for a view.</span></span>

<span data-ttu-id="c1e21-105">ViewDefinitions element (indeling) element weer geven (indeling) TableControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c1e21-105">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1e21-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c1e21-106">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1e21-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c1e21-107">Attributes and Elements</span></span>

<span data-ttu-id="c1e21-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableControl` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c1e21-108">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="c1e21-109">U moet de rijen van de tabel opgeven.</span><span class="sxs-lookup"><span data-stu-id="c1e21-109">You must specify the rows of the table.</span></span> <span data-ttu-id="c1e21-110">Alle onderliggende elementen zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="c1e21-110">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1e21-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c1e21-111">Attributes</span></span>

<span data-ttu-id="c1e21-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="c1e21-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1e21-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c1e21-113">Child Elements</span></span>

|<span data-ttu-id="c1e21-114">Element</span><span class="sxs-lookup"><span data-stu-id="c1e21-114">Element</span></span>|<span data-ttu-id="c1e21-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c1e21-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1e21-116">Het element AutoSize voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1e21-116">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="c1e21-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c1e21-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c1e21-118">Hiermee wordt aangegeven of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="c1e21-118">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="c1e21-119">HideTableHeaders-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="c1e21-119">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="c1e21-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c1e21-120">Optional element.</span></span><br /><br /> <span data-ttu-id="c1e21-121">Hiermee wordt aangegeven of de koptekst van de tabel niet wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c1e21-121">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="c1e21-122">TableHeaders-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="c1e21-122">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="c1e21-123">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="c1e21-123">Required element.</span></span><br /><br /> <span data-ttu-id="c1e21-124">Hiermee worden de labels, de breedten en de uitlijning van de gegevens voor de kolommen van de tabel weergave gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="c1e21-124">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="c1e21-125">Het element TableRowEntries voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1e21-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="c1e21-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c1e21-126">Optional element.</span></span><br /><br /> <span data-ttu-id="c1e21-127">Biedt de definities van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="c1e21-127">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c1e21-128">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c1e21-128">Parent Elements</span></span>

|<span data-ttu-id="c1e21-129">Element</span><span class="sxs-lookup"><span data-stu-id="c1e21-129">Element</span></span>|<span data-ttu-id="c1e21-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c1e21-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1e21-131">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1e21-131">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c1e21-132">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c1e21-132">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c1e21-133">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c1e21-133">Remarks</span></span>

<span data-ttu-id="c1e21-134">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="c1e21-134">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c1e21-135">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c1e21-135">Example</span></span>

<span data-ttu-id="c1e21-136">In dit voor beeld ziet u een- `TableControl` element dat wordt gebruikt om de eigenschappen van het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c1e21-136">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="c1e21-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c1e21-137">See Also</span></span>

[<span data-ttu-id="c1e21-138">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="c1e21-138">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c1e21-139">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1e21-139">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c1e21-140">Het element AutoSize voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1e21-140">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="c1e21-141">Het element HideTableHeaders (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1e21-141">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="c1e21-142">Het element TableHeaders (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1e21-142">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="c1e21-143">TableRowEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c1e21-143">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="c1e21-144">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c1e21-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
