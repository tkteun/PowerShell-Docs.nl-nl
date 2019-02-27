---
title: ViewSelectedBy-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851840"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="e531e-102">Het element ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e531e-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="e531e-103">Hiermee definieert u de .NET-objecten die worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="e531e-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="e531e-104">Elke weergave moet ten minste één .NET-object opgeven.</span><span class="sxs-lookup"><span data-stu-id="e531e-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="e531e-105">ViewDefinitions-Element (indeling) weergave Element (indeling) ViewSelectedBy Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e531e-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e531e-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e531e-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e531e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e531e-107">Attributes and Elements</span></span>

<span data-ttu-id="e531e-108">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `ViewSelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="e531e-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="e531e-109">Dit element moet ten minste één bevatten `TypeName` of `SelectionSetName` onderliggend element.</span><span class="sxs-lookup"><span data-stu-id="e531e-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="e531e-110">Er is geen limiet voor het aantal onderliggende elementen die kunnen worden opgegeven of is de volgorde belangrijk.</span><span class="sxs-lookup"><span data-stu-id="e531e-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="e531e-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e531e-111">Attributes</span></span>

<span data-ttu-id="e531e-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="e531e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e531e-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e531e-113">Child Elements</span></span>

|<span data-ttu-id="e531e-114">Element</span><span class="sxs-lookup"><span data-stu-id="e531e-114">Element</span></span>|<span data-ttu-id="e531e-115">Description</span><span class="sxs-lookup"><span data-stu-id="e531e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e531e-116">TypeName-Element voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e531e-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="e531e-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e531e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e531e-118">Hiermee geeft u een .NET-object dat door de weergave wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="e531e-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="e531e-119">SelectionSetName-Element voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e531e-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="e531e-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e531e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e531e-121">Hiermee geeft u een set van .NET-objecten die worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="e531e-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e531e-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e531e-122">Parent Elements</span></span>

|<span data-ttu-id="e531e-123">Element</span><span class="sxs-lookup"><span data-stu-id="e531e-123">Element</span></span>|<span data-ttu-id="e531e-124">Description</span><span class="sxs-lookup"><span data-stu-id="e531e-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e531e-125">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e531e-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="e531e-126">Hiermee definieert u een weergave met een of meer .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="e531e-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e531e-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e531e-127">Remarks</span></span>

<span data-ttu-id="e531e-128">Zie voor meer informatie over hoe dit element wordt gebruikt in verschillende weergaven, [tabel weergave onderdelen](./creating-a-table-view.md), [lijst weergave onderdelen](./creating-a-list-view.md), [brede weergave onderdelen](./creating-a-wide-view.md), en [Aangepast besturingselement onderdelen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e531e-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="e531e-129">De `SelectionSetName` element wordt gebruikt wanneer de opmaak-bestand definieert een set van objecten die door meerdere weergaven worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="e531e-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="e531e-130">Zie voor meer informatie over hoe selectiesets zijn gedefinieerd en waarnaar wordt verwezen, [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e531e-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="e531e-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e531e-131">Example</span></span>

<span data-ttu-id="e531e-132">Het volgende voorbeeld ziet u hoe u de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) -object voor een lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="e531e-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="e531e-133">Hetzelfde schema wordt gebruikt voor de tabel, breed en aangepaste weergaven.</span><span class="sxs-lookup"><span data-stu-id="e531e-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="e531e-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e531e-134">See Also</span></span>

[<span data-ttu-id="e531e-135">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="e531e-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e531e-136">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="e531e-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e531e-137">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="e531e-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e531e-138">Het maken van aangepaste besturingselementen</span><span class="sxs-lookup"><span data-stu-id="e531e-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e531e-139">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="e531e-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e531e-140">SelectionSetName-Element voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e531e-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="e531e-141">TypeName Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e531e-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="e531e-142">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="e531e-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
