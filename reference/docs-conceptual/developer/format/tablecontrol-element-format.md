---
title: TableControl-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358793"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="a04f8-102">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a04f8-102">TableControl Element (Format)</span></span>

<span data-ttu-id="a04f8-103">Definieert een tabel indeling voor een weer gave.</span><span class="sxs-lookup"><span data-stu-id="a04f8-103">Defines a table format for a view.</span></span>

<span data-ttu-id="a04f8-104">ViewDefinitions element (indeling) element weer geven (indeling) TableControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a04f8-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a04f8-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a04f8-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a04f8-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a04f8-106">Attributes and Elements</span></span>

<span data-ttu-id="a04f8-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `TableControl` beschreven.</span><span class="sxs-lookup"><span data-stu-id="a04f8-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="a04f8-108">U moet de rijen van de tabel opgeven.</span><span class="sxs-lookup"><span data-stu-id="a04f8-108">You must specify the rows of the table.</span></span> <span data-ttu-id="a04f8-109">Alle onderliggende elementen zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="a04f8-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="a04f8-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a04f8-110">Attributes</span></span>

<span data-ttu-id="a04f8-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="a04f8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a04f8-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a04f8-112">Child Elements</span></span>

|<span data-ttu-id="a04f8-113">Element</span><span class="sxs-lookup"><span data-stu-id="a04f8-113">Element</span></span>|<span data-ttu-id="a04f8-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a04f8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a04f8-115">Het element AutoSize voor TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a04f8-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="a04f8-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a04f8-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a04f8-117">Hiermee wordt aangegeven of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="a04f8-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="a04f8-118">HideTableHeaders-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="a04f8-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="a04f8-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a04f8-119">Optional element.</span></span><br /><br /> <span data-ttu-id="a04f8-120">Hiermee wordt aangegeven of de koptekst van de tabel niet wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a04f8-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="a04f8-121">TableHeaders-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="a04f8-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="a04f8-122">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="a04f8-122">Required element.</span></span><br /><br /> <span data-ttu-id="a04f8-123">Hiermee worden de labels, de breedten en de uitlijning van de gegevens voor de kolommen van de tabel weergave gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a04f8-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="a04f8-124">TableRowEntries-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="a04f8-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="a04f8-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a04f8-125">Optional element.</span></span><br /><br /> <span data-ttu-id="a04f8-126">Biedt de definities van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="a04f8-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a04f8-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a04f8-127">Parent Elements</span></span>

|<span data-ttu-id="a04f8-128">Element</span><span class="sxs-lookup"><span data-stu-id="a04f8-128">Element</span></span>|<span data-ttu-id="a04f8-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a04f8-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a04f8-130">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="a04f8-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="a04f8-131">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a04f8-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a04f8-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a04f8-132">Remarks</span></span>

<span data-ttu-id="a04f8-133">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="a04f8-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a04f8-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a04f8-134">Example</span></span>

<span data-ttu-id="a04f8-135">In dit voor beeld ziet u een `TableControl`-element dat wordt gebruikt om de eigenschappen van het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a04f8-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a04f8-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a04f8-136">See Also</span></span>

[<span data-ttu-id="a04f8-137">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="a04f8-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a04f8-138">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="a04f8-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="a04f8-139">Het element AutoSize voor TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a04f8-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="a04f8-140">HideTableHeaders-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a04f8-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="a04f8-141">TableHeaders-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a04f8-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="a04f8-142">TableRowEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a04f8-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="a04f8-143">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a04f8-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
