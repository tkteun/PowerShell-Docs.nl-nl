---
title: PropertyName-Element voor TableColumnItem voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064605"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="5d549-102">Het element PropertyName voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5d549-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="5d549-103">Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="5d549-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="5d549-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) TableColumnItems-Element (indeling) TableColumnItem-Element (indeling) PropertyName-Element voor TableColumnItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="5d549-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5d549-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5d549-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5d549-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5d549-106">Attributes and Elements</span></span>

<span data-ttu-id="5d549-107">De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="5d549-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5d549-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5d549-108">Attributes</span></span>

<span data-ttu-id="5d549-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="5d549-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5d549-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5d549-110">Child Elements</span></span>

<span data-ttu-id="5d549-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="5d549-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5d549-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5d549-112">Parent Elements</span></span>

|<span data-ttu-id="5d549-113">Element</span><span class="sxs-lookup"><span data-stu-id="5d549-113">Element</span></span>|<span data-ttu-id="5d549-114">Description</span><span class="sxs-lookup"><span data-stu-id="5d549-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5d549-115">TableColumnItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5d549-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="5d549-116">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="5d549-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5d549-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="5d549-117">Text Value</span></span>

<span data-ttu-id="5d549-118">Geef de naam van de eigenschap waarvan de waarde wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="5d549-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d549-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5d549-119">Remarks</span></span>

<span data-ttu-id="5d549-120">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="5d549-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5d549-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5d549-121">Example</span></span>

<span data-ttu-id="5d549-122">In dit voorbeeld ziet u een `TableColumnItem` element dat Hiermee geeft u de `Status` eigenschap van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span><span class="sxs-lookup"><span data-stu-id="5d549-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="5d549-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5d549-123">See Also</span></span>

[<span data-ttu-id="5d549-124">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="5d549-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5d549-125">TableColumnItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5d549-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="5d549-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d549-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
