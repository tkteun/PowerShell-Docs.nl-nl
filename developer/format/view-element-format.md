---
title: Weergeven van Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846912"
---
# <a name="view-element-format"></a><span data-ttu-id="38d01-102">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="38d01-102">View Element (Format)</span></span>

<span data-ttu-id="38d01-103">Hiermee definieert u een weergave met een of meer .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="38d01-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="38d01-104">Er is geen limiet voor het aantal weergaven die kunnen worden gedefinieerd in een bestand met opmaak.</span><span class="sxs-lookup"><span data-stu-id="38d01-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="38d01-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38d01-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="38d01-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="38d01-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="38d01-107">Attributes and Elements</span></span>

<span data-ttu-id="38d01-108">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `View` element.</span><span class="sxs-lookup"><span data-stu-id="38d01-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="38d01-109">Moet u slechts één van de onderliggende elementen van controle en moet u de naam van de weergave en de objecten die gebruikmaken van de weergave opgeven.</span><span class="sxs-lookup"><span data-stu-id="38d01-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="38d01-110">Aangepaste besturingselementen te definiëren, hoe u aan de groep objecten en op te geven als de weergave is het out-of-band zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="38d01-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="38d01-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="38d01-111">Attributes</span></span>

<span data-ttu-id="38d01-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="38d01-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38d01-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="38d01-113">Child Elements</span></span>

|<span data-ttu-id="38d01-114">Element</span><span class="sxs-lookup"><span data-stu-id="38d01-114">Element</span></span>|<span data-ttu-id="38d01-115">Description</span><span class="sxs-lookup"><span data-stu-id="38d01-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38d01-116">Element van de besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="38d01-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="38d01-117">Optional element.</span></span><br /><br /> <span data-ttu-id="38d01-118">Hiermee definieert een set besturingselementen die kan worden verwezen door de naam in de weergave.</span><span class="sxs-lookup"><span data-stu-id="38d01-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="38d01-119">CustomControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="38d01-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="38d01-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="38d01-120">Optional element.</span></span><br /><br /> <span data-ttu-id="38d01-121">Hiermee definieert u een aangepast besturingselement-indeling voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="38d01-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="38d01-122">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="38d01-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="38d01-123">Optional element.</span></span><br /><br /> <span data-ttu-id="38d01-124">Hiermee definieert u hoe de leden van de .NET-objecten worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="38d01-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="38d01-125">ListControl Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="38d01-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="38d01-126">Optional element.</span></span><br /><br /> <span data-ttu-id="38d01-127">Hiermee definieert u een indeling voor de weergave heeft.</span><span class="sxs-lookup"><span data-stu-id="38d01-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="38d01-128">Naamelement voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="38d01-129">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="38d01-129">Required element.</span></span><br /><br /> <span data-ttu-id="38d01-130">Hiermee geeft u de naam die wordt gebruikt om te verwijzen naar de weergave.</span><span class="sxs-lookup"><span data-stu-id="38d01-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="38d01-131">TableControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="38d01-132">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="38d01-132">Optional element.</span></span><br /><br /> <span data-ttu-id="38d01-133">Hiermee definieert u een tabelindeling voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="38d01-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="38d01-134">ViewSelectedBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="38d01-135">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="38d01-135">Required element.</span></span><br /><br /> <span data-ttu-id="38d01-136">Hiermee definieert u de .NET-objecten die deze weergave worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="38d01-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="38d01-137">WideControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="38d01-138">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="38d01-138">Optional element.</span></span><br /><br /> <span data-ttu-id="38d01-139">Definieert een breed (één waarde) lijstweergave voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="38d01-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="38d01-140">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="38d01-140">Parent Elements</span></span>

|<span data-ttu-id="38d01-141">Element</span><span class="sxs-lookup"><span data-stu-id="38d01-141">Element</span></span>|<span data-ttu-id="38d01-142">Description</span><span class="sxs-lookup"><span data-stu-id="38d01-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38d01-143">ViewDefinitions-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="38d01-144">Definieert de weergaven die wordt gebruikt om objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="38d01-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38d01-145">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="38d01-145">Remarks</span></span>

<span data-ttu-id="38d01-146">Zie voor meer informatie over de onderdelen van de verschillende weergaven en aangepaste besturingselementen in de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="38d01-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="38d01-147">Onderdelen van de tabel weergeven</span><span class="sxs-lookup"><span data-stu-id="38d01-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="38d01-148">Lijst met weergave-onderdelen</span><span class="sxs-lookup"><span data-stu-id="38d01-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="38d01-149">Onderdelen van de brede weergave</span><span class="sxs-lookup"><span data-stu-id="38d01-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="38d01-150">Aangepaste besturingselementen</span><span class="sxs-lookup"><span data-stu-id="38d01-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="38d01-151">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="38d01-151">Example</span></span>

<span data-ttu-id="38d01-152">In dit voorbeeld ziet u een `View` element dat een tabelweergave voor definieert de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span><span class="sxs-lookup"><span data-stu-id="38d01-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="38d01-153">Zie ook</span><span class="sxs-lookup"><span data-stu-id="38d01-153">See Also</span></span>

[<span data-ttu-id="38d01-154">ViewDefinitions-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="38d01-155">Naamelement voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="38d01-156">ViewSelectedBy-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="38d01-157">Element van de besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="38d01-158">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="38d01-159">TableControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="38d01-160">ListControl Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="38d01-161">WideControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="38d01-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="38d01-162">CustomControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="38d01-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="38d01-163">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="38d01-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
