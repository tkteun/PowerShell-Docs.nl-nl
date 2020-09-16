---
title: Element weer geven (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c0c6fa373cfca3a55a62f201e1eabc6a1e308ef7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785027"
---
# <a name="view-element-format"></a><span data-ttu-id="7225d-102">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-102">View Element (Format)</span></span>

<span data-ttu-id="7225d-103">Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7225d-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="7225d-104">Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="7225d-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="7225d-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="7225d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7225d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7225d-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="7225d-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7225d-107">Attributes and Elements</span></span>

<span data-ttu-id="7225d-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `View` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="7225d-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="7225d-109">U moet één en slechts één van de onderliggende elementen van het besturings element opgeven, en u moet de naam van de weer gave opgeven en de objecten die gebruikmaken van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="7225d-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="7225d-110">Aangepaste besturings elementen definiëren, objecten groeperen en opgeven of de weer gave out-of-band optioneel is.</span><span class="sxs-lookup"><span data-stu-id="7225d-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="7225d-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7225d-111">Attributes</span></span>

<span data-ttu-id="7225d-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="7225d-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7225d-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7225d-113">Child Elements</span></span>

|<span data-ttu-id="7225d-114">Element</span><span class="sxs-lookup"><span data-stu-id="7225d-114">Element</span></span>|<span data-ttu-id="7225d-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7225d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7225d-116">Het element Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="7225d-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7225d-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7225d-118">Hiermee wordt een set besturings elementen gedefinieerd waarnaar kan worden verwezen met hun naam in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="7225d-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="7225d-119">CustomControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="7225d-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="7225d-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7225d-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7225d-121">Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="7225d-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="7225d-122">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="7225d-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7225d-123">Optional element.</span></span><br /><br /> <span data-ttu-id="7225d-124">Hiermee wordt gedefinieerd hoe de leden van de .NET-objecten worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="7225d-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="7225d-125">Het element ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="7225d-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7225d-126">Optional element.</span></span><br /><br /> <span data-ttu-id="7225d-127">Hiermee definieert u een lijst indeling voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="7225d-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="7225d-128">Het element Naam voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="7225d-129">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="7225d-129">Required element.</span></span><br /><br /> <span data-ttu-id="7225d-130">Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de weer gave.</span><span class="sxs-lookup"><span data-stu-id="7225d-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="7225d-131">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="7225d-132">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7225d-132">Optional element.</span></span><br /><br /> <span data-ttu-id="7225d-133">Hiermee definieert u een tabel indeling voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="7225d-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="7225d-134">Element ViewSelectedBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="7225d-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="7225d-135">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="7225d-135">Required element.</span></span><br /><br /> <span data-ttu-id="7225d-136">Hiermee worden de .NET-objecten gedefinieerd die in deze weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7225d-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="7225d-137">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="7225d-138">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7225d-138">Optional element.</span></span><br /><br /> <span data-ttu-id="7225d-139">Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="7225d-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7225d-140">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7225d-140">Parent Elements</span></span>

|<span data-ttu-id="7225d-141">Element</span><span class="sxs-lookup"><span data-stu-id="7225d-141">Element</span></span>|<span data-ttu-id="7225d-142">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7225d-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7225d-143">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="7225d-144">Hiermee worden de weer gaven gedefinieerd waarmee objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7225d-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7225d-145">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7225d-145">Remarks</span></span>

<span data-ttu-id="7225d-146">Zie de volgende onderwerpen voor meer informatie over de onderdelen van verschillende weer gaven en aangepaste besturings elementen:</span><span class="sxs-lookup"><span data-stu-id="7225d-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="7225d-147">Onderdelen van de tabel weergave</span><span class="sxs-lookup"><span data-stu-id="7225d-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="7225d-148">Lijst weergave onderdelen</span><span class="sxs-lookup"><span data-stu-id="7225d-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="7225d-149">Brede weergave onderdelen</span><span class="sxs-lookup"><span data-stu-id="7225d-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="7225d-150">Aangepaste besturings elementen</span><span class="sxs-lookup"><span data-stu-id="7225d-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="7225d-151">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="7225d-151">Example</span></span>

<span data-ttu-id="7225d-152">In dit voor beeld ziet u een- `View` element dat een tabel weergave definieert voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="7225d-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7225d-153">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7225d-153">See Also</span></span>

[<span data-ttu-id="7225d-154">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="7225d-155">Het element Naam voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="7225d-156">Het element ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="7225d-157">Het element Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="7225d-158">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="7225d-159">Het element TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="7225d-160">Het element ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="7225d-161">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7225d-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="7225d-162">CustomControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="7225d-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="7225d-163">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7225d-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
