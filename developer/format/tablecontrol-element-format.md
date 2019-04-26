---
title: TableControl-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063823"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="c17c7-102">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c17c7-102">TableControl Element (Format)</span></span>

<span data-ttu-id="c17c7-103">Hiermee definieert u een tabelindeling voor een weergave.</span><span class="sxs-lookup"><span data-stu-id="c17c7-103">Defines a table format for a view.</span></span>

<span data-ttu-id="c17c7-104">ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c17c7-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c17c7-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c17c7-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c17c7-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c17c7-106">Attributes and Elements</span></span>

<span data-ttu-id="c17c7-107">De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `TableControl` element.</span><span class="sxs-lookup"><span data-stu-id="c17c7-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="c17c7-108">U moet de rijen van de tabel opgeven.</span><span class="sxs-lookup"><span data-stu-id="c17c7-108">You must specify the rows of the table.</span></span> <span data-ttu-id="c17c7-109">Alle onderliggende elementen zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="c17c7-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="c17c7-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c17c7-110">Attributes</span></span>

<span data-ttu-id="c17c7-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="c17c7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c17c7-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c17c7-112">Child Elements</span></span>

|<span data-ttu-id="c17c7-113">Element</span><span class="sxs-lookup"><span data-stu-id="c17c7-113">Element</span></span>|<span data-ttu-id="c17c7-114">Description</span><span class="sxs-lookup"><span data-stu-id="c17c7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c17c7-115">AutoSize-Element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="c17c7-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="c17c7-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c17c7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c17c7-117">Hiermee geeft u op of de kolomgrootte en het aantal kolommen zijn aangepast op basis van de grootte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="c17c7-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="c17c7-118">HideTableHeaders-Element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="c17c7-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="c17c7-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c17c7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c17c7-120">Geeft aan of de header van de tabel niet wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="c17c7-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="c17c7-121">TableHeaders-Element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="c17c7-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="c17c7-122">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="c17c7-122">Required element.</span></span><br /><br /> <span data-ttu-id="c17c7-123">Definieert de labels, de breedte en de uitlijning van de gegevens voor de kolommen van de tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="c17c7-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="c17c7-124">TableRowEntries-Element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="c17c7-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="c17c7-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c17c7-125">Optional element.</span></span><br /><br /> <span data-ttu-id="c17c7-126">Bevat de definities van de tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="c17c7-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c17c7-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c17c7-127">Parent Elements</span></span>

|<span data-ttu-id="c17c7-128">Element</span><span class="sxs-lookup"><span data-stu-id="c17c7-128">Element</span></span>|<span data-ttu-id="c17c7-129">Description</span><span class="sxs-lookup"><span data-stu-id="c17c7-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c17c7-130">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c17c7-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c17c7-131">Hiermee definieert u een weergave die wordt gebruikt om de leden van een of meer objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c17c7-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c17c7-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c17c7-132">Remarks</span></span>

<span data-ttu-id="c17c7-133">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c17c7-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c17c7-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c17c7-134">Example</span></span>

<span data-ttu-id="c17c7-135">In dit voorbeeld ziet u een `TableControl` element dat wordt gebruikt om weer te geven van de eigenschappen van de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span><span class="sxs-lookup"><span data-stu-id="c17c7-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c17c7-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c17c7-136">See Also</span></span>

[<span data-ttu-id="c17c7-137">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="c17c7-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c17c7-138">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c17c7-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c17c7-139">AutoSize-Element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="c17c7-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="c17c7-140">HideTableHeaders-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c17c7-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="c17c7-141">TableHeaders-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c17c7-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="c17c7-142">TableRowEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c17c7-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="c17c7-143">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="c17c7-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
