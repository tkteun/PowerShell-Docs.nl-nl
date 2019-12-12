---
title: Element weer geven (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353443"
---
# <a name="view-element-format"></a><span data-ttu-id="4f48f-102">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4f48f-102">View Element (Format)</span></span>

<span data-ttu-id="4f48f-103">Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4f48f-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="4f48f-104">Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="4f48f-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="4f48f-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4f48f-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="4f48f-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f48f-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="4f48f-107">Attributes and Elements</span></span>

<span data-ttu-id="4f48f-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `View` beschreven.</span><span class="sxs-lookup"><span data-stu-id="4f48f-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="4f48f-109">U moet één en slechts één van de onderliggende elementen van het besturings element opgeven, en u moet de naam van de weer gave opgeven en de objecten die gebruikmaken van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="4f48f-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="4f48f-110">Aangepaste besturings elementen definiëren, objecten groeperen en opgeven of de weer gave out-of-band optioneel is.</span><span class="sxs-lookup"><span data-stu-id="4f48f-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f48f-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4f48f-111">Attributes</span></span>

<span data-ttu-id="4f48f-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="4f48f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4f48f-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4f48f-113">Child Elements</span></span>

|<span data-ttu-id="4f48f-114">Element</span><span class="sxs-lookup"><span data-stu-id="4f48f-114">Element</span></span>|<span data-ttu-id="4f48f-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4f48f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f48f-116">Element Controls voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="4f48f-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4f48f-117">Optional element.</span></span><br /><br /> <span data-ttu-id="4f48f-118">Hiermee wordt een set besturings elementen gedefinieerd waarnaar kan worden verwezen met hun naam in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="4f48f-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="4f48f-119">CustomControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="4f48f-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4f48f-120">Optional element.</span></span><br /><br /> <span data-ttu-id="4f48f-121">Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="4f48f-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="4f48f-122">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="4f48f-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4f48f-123">Optional element.</span></span><br /><br /> <span data-ttu-id="4f48f-124">Hiermee wordt gedefinieerd hoe de leden van de .NET-objecten worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="4f48f-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="4f48f-125">ListControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="4f48f-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4f48f-126">Optional element.</span></span><br /><br /> <span data-ttu-id="4f48f-127">Hiermee definieert u een lijst indeling voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="4f48f-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="4f48f-128">Naam element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="4f48f-129">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="4f48f-129">Required element.</span></span><br /><br /> <span data-ttu-id="4f48f-130">Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de weer gave.</span><span class="sxs-lookup"><span data-stu-id="4f48f-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="4f48f-131">TableControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="4f48f-132">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4f48f-132">Optional element.</span></span><br /><br /> <span data-ttu-id="4f48f-133">Hiermee definieert u een tabel indeling voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="4f48f-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="4f48f-134">Element ViewSelectedBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="4f48f-135">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="4f48f-135">Required element.</span></span><br /><br /> <span data-ttu-id="4f48f-136">Hiermee worden de .NET-objecten gedefinieerd die in deze weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4f48f-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="4f48f-137">WideControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="4f48f-138">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4f48f-138">Optional element.</span></span><br /><br /> <span data-ttu-id="4f48f-139">Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="4f48f-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4f48f-140">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4f48f-140">Parent Elements</span></span>

|<span data-ttu-id="4f48f-141">Element</span><span class="sxs-lookup"><span data-stu-id="4f48f-141">Element</span></span>|<span data-ttu-id="4f48f-142">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4f48f-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f48f-143">ViewDefinitions-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="4f48f-144">Hiermee worden de weer gaven gedefinieerd waarmee objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4f48f-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4f48f-145">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4f48f-145">Remarks</span></span>

<span data-ttu-id="4f48f-146">Zie de volgende onderwerpen voor meer informatie over de onderdelen van verschillende weer gaven en aangepaste besturings elementen:</span><span class="sxs-lookup"><span data-stu-id="4f48f-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="4f48f-147">Onderdelen van de tabel weergave</span><span class="sxs-lookup"><span data-stu-id="4f48f-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="4f48f-148">Lijst weergave onderdelen</span><span class="sxs-lookup"><span data-stu-id="4f48f-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="4f48f-149">Brede weergave onderdelen</span><span class="sxs-lookup"><span data-stu-id="4f48f-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="4f48f-150">Aangepaste besturings elementen</span><span class="sxs-lookup"><span data-stu-id="4f48f-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="4f48f-151">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="4f48f-151">Example</span></span>

<span data-ttu-id="4f48f-152">In dit voor beeld ziet u een `View`-element dat een tabel weergave definieert voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="4f48f-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="4f48f-153">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4f48f-153">See Also</span></span>

[<span data-ttu-id="4f48f-154">ViewDefinitions-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="4f48f-155">Naam element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="4f48f-156">ViewSelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="4f48f-157">Element Controls voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="4f48f-158">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="4f48f-159">TableControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="4f48f-160">ListControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="4f48f-161">WideControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="4f48f-162">CustomControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4f48f-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="4f48f-163">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="4f48f-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
