---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Weergave (opmaak)
description: Het element Weergave (opmaak)
ms.openlocfilehash: 6fed1304d94339cc90b6ae53e06483c08d937c12
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649747"
---
# <a name="view-element-format"></a><span data-ttu-id="3fec8-103">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-103">View Element (Format)</span></span>

<span data-ttu-id="3fec8-104">Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3fec8-104">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="3fec8-105">Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="3fec8-105">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="3fec8-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="3fec8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3fec8-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="3fec8-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="3fec8-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="3fec8-108">Attributes and Elements</span></span>

<span data-ttu-id="3fec8-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `View` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="3fec8-109">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="3fec8-110">U moet één en slechts één van de onderliggende elementen van het besturings element opgeven, en u moet de naam van de weer gave opgeven en de objecten die gebruikmaken van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3fec8-110">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="3fec8-111">Aangepaste besturings elementen definiëren, objecten groeperen en opgeven of de weer gave out-of-band optioneel is.</span><span class="sxs-lookup"><span data-stu-id="3fec8-111">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="3fec8-112">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3fec8-112">Attributes</span></span>

<span data-ttu-id="3fec8-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="3fec8-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3fec8-114">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3fec8-114">Child Elements</span></span>

|<span data-ttu-id="3fec8-115">Element</span><span class="sxs-lookup"><span data-stu-id="3fec8-115">Element</span></span>|<span data-ttu-id="3fec8-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3fec8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3fec8-117">Het element Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-117">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="3fec8-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="3fec8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3fec8-119">Hiermee wordt een set besturings elementen gedefinieerd waarnaar kan worden verwezen met hun naam in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3fec8-119">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="3fec8-120">CustomControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="3fec8-120">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="3fec8-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="3fec8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3fec8-122">Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3fec8-122">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="3fec8-123">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-123">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="3fec8-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="3fec8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3fec8-125">Hiermee wordt gedefinieerd hoe de leden van de .NET-objecten worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="3fec8-125">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="3fec8-126">Het element ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-126">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="3fec8-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="3fec8-127">Optional element.</span></span><br /><br /> <span data-ttu-id="3fec8-128">Hiermee definieert u een lijst indeling voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3fec8-128">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="3fec8-129">Het element Naam voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-129">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="3fec8-130">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="3fec8-130">Required element.</span></span><br /><br /> <span data-ttu-id="3fec8-131">Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3fec8-131">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="3fec8-132">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-132">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="3fec8-133">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="3fec8-133">Optional element.</span></span><br /><br /> <span data-ttu-id="3fec8-134">Hiermee definieert u een tabel indeling voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3fec8-134">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="3fec8-135">Element ViewSelectedBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3fec8-135">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="3fec8-136">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="3fec8-136">Required element.</span></span><br /><br /> <span data-ttu-id="3fec8-137">Hiermee worden de .NET-objecten gedefinieerd die in deze weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3fec8-137">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="3fec8-138">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-138">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="3fec8-139">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="3fec8-139">Optional element.</span></span><br /><br /> <span data-ttu-id="3fec8-140">Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3fec8-140">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3fec8-141">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3fec8-141">Parent Elements</span></span>

|<span data-ttu-id="3fec8-142">Element</span><span class="sxs-lookup"><span data-stu-id="3fec8-142">Element</span></span>|<span data-ttu-id="3fec8-143">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3fec8-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3fec8-144">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-144">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="3fec8-145">Hiermee worden de weer gaven gedefinieerd waarmee objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3fec8-145">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3fec8-146">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3fec8-146">Remarks</span></span>

<span data-ttu-id="3fec8-147">Zie de volgende onderwerpen voor meer informatie over de onderdelen van verschillende weer gaven en aangepaste besturings elementen:</span><span class="sxs-lookup"><span data-stu-id="3fec8-147">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="3fec8-148">Onderdelen van de tabel weergave</span><span class="sxs-lookup"><span data-stu-id="3fec8-148">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="3fec8-149">Lijst weergave onderdelen</span><span class="sxs-lookup"><span data-stu-id="3fec8-149">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="3fec8-150">Brede weergave onderdelen</span><span class="sxs-lookup"><span data-stu-id="3fec8-150">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="3fec8-151">Aangepaste besturings elementen</span><span class="sxs-lookup"><span data-stu-id="3fec8-151">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="3fec8-152">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3fec8-152">Example</span></span>

<span data-ttu-id="3fec8-153">In dit voor beeld ziet u een- `View` element dat een tabel weergave definieert voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="3fec8-153">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3fec8-154">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3fec8-154">See Also</span></span>

[<span data-ttu-id="3fec8-155">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-155">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="3fec8-156">Het element Naam voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-156">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="3fec8-157">Het element ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-157">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="3fec8-158">Het element Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-158">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="3fec8-159">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-159">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="3fec8-160">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-160">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="3fec8-161">Het element ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-161">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="3fec8-162">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3fec8-162">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="3fec8-163">CustomControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="3fec8-163">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="3fec8-164">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="3fec8-164">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
