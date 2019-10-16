---
title: ViewSelectedBy-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358733"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="06d26-102">Het element ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06d26-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="06d26-103">Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="06d26-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="06d26-104">Elke weer gave moet ten minste één .NET-object opgeven.</span><span class="sxs-lookup"><span data-stu-id="06d26-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="06d26-105">ViewDefinitions element (indeling) element weer geven (indeling) ViewSelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="06d26-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06d26-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="06d26-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06d26-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="06d26-107">Attributes and Elements</span></span>

<span data-ttu-id="06d26-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ViewSelectedBy` beschreven.</span><span class="sxs-lookup"><span data-stu-id="06d26-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="06d26-109">Dit element moet ten minste één `TypeName`-of `SelectionSetName`-onderliggend element bevatten.</span><span class="sxs-lookup"><span data-stu-id="06d26-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="06d26-110">Er is geen limiet voor het aantal onderliggende elementen dat kan worden opgegeven, en de volg orde hiervan is aanzienlijk.</span><span class="sxs-lookup"><span data-stu-id="06d26-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="06d26-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="06d26-111">Attributes</span></span>

<span data-ttu-id="06d26-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="06d26-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06d26-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06d26-113">Child Elements</span></span>

|<span data-ttu-id="06d26-114">Element</span><span class="sxs-lookup"><span data-stu-id="06d26-114">Element</span></span>|<span data-ttu-id="06d26-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="06d26-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06d26-116">TypeName-element voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="06d26-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="06d26-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="06d26-117">Optional element.</span></span><br /><br /> <span data-ttu-id="06d26-118">Hiermee geeft u een .NET-object op dat wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="06d26-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="06d26-119">SelectionSetName-element voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="06d26-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="06d26-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="06d26-120">Optional element.</span></span><br /><br /> <span data-ttu-id="06d26-121">Hiermee geeft u een set .NET-objecten op die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="06d26-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06d26-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06d26-122">Parent Elements</span></span>

|<span data-ttu-id="06d26-123">Element</span><span class="sxs-lookup"><span data-stu-id="06d26-123">Element</span></span>|<span data-ttu-id="06d26-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="06d26-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06d26-125">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="06d26-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="06d26-126">Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="06d26-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06d26-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="06d26-127">Remarks</span></span>

<span data-ttu-id="06d26-128">Zie voor meer informatie over hoe dit element wordt gebruikt in verschillende weer gaven de [tabel weergave onderdelen](./creating-a-table-view.md), [lijst weergave onderdelen](./creating-a-list-view.md), [brede weer gave](./creating-a-wide-view.md)-onderdelen en [aangepaste besturings elementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="06d26-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="06d26-129">Het element `SelectionSetName` wordt gebruikt wanneer het opmaak bestand een set objecten definieert die door meerdere weer gaven worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="06d26-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="06d26-130">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over de manier waarop selectie sets worden gedefinieerd en waarnaar wordt verwezen.</span><span class="sxs-lookup"><span data-stu-id="06d26-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="06d26-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="06d26-131">Example</span></span>

<span data-ttu-id="06d26-132">In het volgende voor beeld ziet u hoe u het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) opgeeft voor een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="06d26-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="06d26-133">Hetzelfde schema wordt gebruikt voor tabel-, brede en aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="06d26-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="06d26-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="06d26-134">See Also</span></span>

[<span data-ttu-id="06d26-135">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="06d26-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="06d26-136">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="06d26-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="06d26-137">Een brede weer gave maken</span><span class="sxs-lookup"><span data-stu-id="06d26-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="06d26-138">Aangepaste besturings elementen maken</span><span class="sxs-lookup"><span data-stu-id="06d26-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="06d26-139">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="06d26-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="06d26-140">SelectionSetName-element voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="06d26-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="06d26-141">TypeName-element (Format)</span><span class="sxs-lookup"><span data-stu-id="06d26-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="06d26-142">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="06d26-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
