---
title: Naam van Element voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849264"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="61728-102">Het element Naam voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="61728-102">Name Element for View (Format)</span></span>

<span data-ttu-id="61728-103">Hiermee geeft u de naam die wordt gebruikt voor het identificeren van de weergave.</span><span class="sxs-lookup"><span data-stu-id="61728-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="61728-104">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) naamelement (indeling)</span><span class="sxs-lookup"><span data-stu-id="61728-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="61728-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="61728-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="61728-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="61728-106">Attributes and Elements</span></span>

<span data-ttu-id="61728-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Name` element.</span><span class="sxs-lookup"><span data-stu-id="61728-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="61728-108">Slechts één `Name` element is toegestaan voor elke weergave.</span><span class="sxs-lookup"><span data-stu-id="61728-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="61728-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="61728-109">Attributes</span></span>

<span data-ttu-id="61728-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="61728-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="61728-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="61728-111">Child Elements</span></span>

<span data-ttu-id="61728-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="61728-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="61728-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="61728-113">Parent Elements</span></span>

|<span data-ttu-id="61728-114">Element</span><span class="sxs-lookup"><span data-stu-id="61728-114">Element</span></span>|<span data-ttu-id="61728-115">Description</span><span class="sxs-lookup"><span data-stu-id="61728-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61728-116">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="61728-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="61728-117">Hiermee definieert u een weergave die wordt gebruikt om de leden van een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="61728-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="61728-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="61728-118">Text Value</span></span>

<span data-ttu-id="61728-119">Geef een unieke beschrijvende naam voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="61728-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="61728-120">Deze naam kan een verwijzing naar het type van de weergave (zoals een tabel of lijstweergave), welke object of een set van objecten gebruikt u de weergave, welke opdracht retourneert de objecten of een combinatie hiervan bevatten.</span><span class="sxs-lookup"><span data-stu-id="61728-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="61728-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="61728-121">Remarks</span></span>

<span data-ttu-id="61728-122">Zie de volgende onderwerpen voor meer informatie over de verschillende typen weergaven: [Weergave tabel](./creating-a-table-view.md), [lijstweergave](./creating-a-list-view.md), [brede weergave](./creating-a-wide-view.md), en [aangepaste weergave](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="61728-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="61728-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="61728-123">Example</span></span>

<span data-ttu-id="61728-124">Het volgende voorbeeld wordt een `View` element dat een tabelweergave voor definieert de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span><span class="sxs-lookup"><span data-stu-id="61728-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="61728-125">De naam van de weergave is 'service'.</span><span class="sxs-lookup"><span data-stu-id="61728-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="61728-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="61728-126">See Also</span></span>

[<span data-ttu-id="61728-127">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="61728-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="61728-128">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="61728-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="61728-129">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="61728-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="61728-130">Het maken van aangepaste besturingselementen</span><span class="sxs-lookup"><span data-stu-id="61728-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="61728-131">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="61728-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="61728-132">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="61728-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
