---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ViewSelectedBy (opmaak)
description: Het element ViewSelectedBy (opmaak)
ms.openlocfilehash: ac3c7de299b3009a067a476a024c6a6fcb5dce02
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667705"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="01cb7-103">Het element ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="01cb7-103">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="01cb7-104">Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="01cb7-104">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="01cb7-105">Elke weer gave moet ten minste één .NET-object opgeven.</span><span class="sxs-lookup"><span data-stu-id="01cb7-105">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="01cb7-106">ViewDefinitions element (indeling) element weer geven (indeling) ViewSelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="01cb7-106">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="01cb7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="01cb7-107">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="01cb7-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="01cb7-108">Attributes and Elements</span></span>

<span data-ttu-id="01cb7-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ViewSelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="01cb7-109">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="01cb7-110">Dit element moet ten minste één `TypeName` of een `SelectionSetName` onderliggend element bevatten.</span><span class="sxs-lookup"><span data-stu-id="01cb7-110">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="01cb7-111">Er is geen limiet voor het aantal onderliggende elementen dat kan worden opgegeven, en de volg orde hiervan is aanzienlijk.</span><span class="sxs-lookup"><span data-stu-id="01cb7-111">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="01cb7-112">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="01cb7-112">Attributes</span></span>

<span data-ttu-id="01cb7-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="01cb7-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="01cb7-114">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="01cb7-114">Child Elements</span></span>

|<span data-ttu-id="01cb7-115">Element</span><span class="sxs-lookup"><span data-stu-id="01cb7-115">Element</span></span>|<span data-ttu-id="01cb7-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="01cb7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="01cb7-117">Het element TypeName voor ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="01cb7-117">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="01cb7-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="01cb7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="01cb7-119">Hiermee geeft u een .NET-object op dat wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="01cb7-119">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="01cb7-120">Het element SelectionSetName voor ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="01cb7-120">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="01cb7-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="01cb7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="01cb7-122">Hiermee geeft u een set .NET-objecten op die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="01cb7-122">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="01cb7-123">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="01cb7-123">Parent Elements</span></span>

|<span data-ttu-id="01cb7-124">Element</span><span class="sxs-lookup"><span data-stu-id="01cb7-124">Element</span></span>|<span data-ttu-id="01cb7-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="01cb7-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="01cb7-126">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="01cb7-126">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="01cb7-127">Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="01cb7-127">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="01cb7-128">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="01cb7-128">Remarks</span></span>

<span data-ttu-id="01cb7-129">Zie voor meer informatie over hoe dit element wordt gebruikt in verschillende weer gaven de [tabel weergave onderdelen](./creating-a-table-view.md), [lijst weergave onderdelen](./creating-a-list-view.md), [brede weer gave](./creating-a-wide-view.md)-onderdelen en [aangepaste besturings elementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="01cb7-129">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="01cb7-130">Het `SelectionSetName` element wordt gebruikt wanneer het opmaak bestand een set objecten definieert die door meerdere weer gaven worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="01cb7-130">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="01cb7-131">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over de manier waarop selectie sets worden gedefinieerd en waarnaar wordt verwezen.</span><span class="sxs-lookup"><span data-stu-id="01cb7-131">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="01cb7-132">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="01cb7-132">Example</span></span>

<span data-ttu-id="01cb7-133">In het volgende voor beeld ziet u hoe u het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) opgeeft voor een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="01cb7-133">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="01cb7-134">Hetzelfde schema wordt gebruikt voor tabel-, brede en aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="01cb7-134">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="01cb7-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="01cb7-135">See Also</span></span>

[<span data-ttu-id="01cb7-136">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="01cb7-136">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="01cb7-137">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="01cb7-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="01cb7-138">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="01cb7-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="01cb7-139">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="01cb7-139">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="01cb7-140">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="01cb7-140">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="01cb7-141">Het element SelectionSetName voor ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="01cb7-141">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="01cb7-142">TypeName-element (Format)</span><span class="sxs-lookup"><span data-stu-id="01cb7-142">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="01cb7-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="01cb7-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
