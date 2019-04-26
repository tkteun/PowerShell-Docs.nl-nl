---
title: Het maken van een lijst weergeven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066852"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="6b738-102">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="6b738-102">Creating a List View</span></span>

<span data-ttu-id="6b738-103">Een lijstweergave geeft gegevens weer in één kolom (in opeenvolgende volgorde).</span><span class="sxs-lookup"><span data-stu-id="6b738-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="6b738-104">De gegevens die worden weergegeven in de lijst is de waarde van een eigenschap .NET of de waarde van een script.</span><span class="sxs-lookup"><span data-stu-id="6b738-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="6b738-105">Een lijst met weergave worden weergegeven</span><span class="sxs-lookup"><span data-stu-id="6b738-105">A List View Display</span></span>

<span data-ttu-id="6b738-106">De volgende uitvoer ziet u hoe Windows PowerShell worden weergegeven in de eigenschappen van [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten die worden geretourneerd door de [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b738-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="6b738-107">In dit voorbeeld drie objecten zijn opgehaald, met elk object van het voorgaande object gescheiden door een lege regel.</span><span class="sxs-lookup"><span data-stu-id="6b738-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a><span data-ttu-id="6b738-108">De lijstweergave definiëren</span><span class="sxs-lookup"><span data-stu-id="6b738-108">Defining the List View</span></span>

<span data-ttu-id="6b738-109">Het volgende XML-bestand bevat de lijst met weergave-schema voor het weergeven van verschillende eigenschappen van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span><span class="sxs-lookup"><span data-stu-id="6b738-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="6b738-110">U moet elke eigenschap die u weergeven in de lijstweergave wilt.</span><span class="sxs-lookup"><span data-stu-id="6b738-110">You must specify each property that you want displayed in the list view.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

<span data-ttu-id="6b738-111">De volgende XML-elementen worden gebruikt voor het definiëren van een lijst weergeven:</span><span class="sxs-lookup"><span data-stu-id="6b738-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="6b738-112">De [weergave](./view-element-format.md) -element is het bovenliggende element van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="6b738-113">(Dit is hetzelfde bovenliggende element voor de tabel, breed en aangepaste weergaven.)</span><span class="sxs-lookup"><span data-stu-id="6b738-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="6b738-114">De [naam](./name-element-for-view-format.md) element Hiermee geeft u de naam van de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="6b738-115">Dit element is vereist voor alle weergaven.</span><span class="sxs-lookup"><span data-stu-id="6b738-115">This element is required for all views.</span></span>

- <span data-ttu-id="6b738-116">De [ViewSelectedBy](./viewselectedby-element-format.md) element definieert de objecten die gebruikmaken van de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="6b738-117">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="6b738-117">This element is required.</span></span>

- <span data-ttu-id="6b738-118">De [GroupBy](./groupby-element-for-view-format.md) element wordt gedefinieerd wanneer een nieuwe groep objecten wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="6b738-119">Een nieuwe groep wordt gestart wanneer de waarde van een bepaalde eigenschap of script wijzigt.</span><span class="sxs-lookup"><span data-stu-id="6b738-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="6b738-120">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6b738-120">This element is optional.</span></span>

- <span data-ttu-id="6b738-121">De [besturingselementen](./controls-element-for-view-format.md) element wordt gedefinieerd voor de aangepaste besturingselementen die zijn gedefinieerd door de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="6b738-122">Besturingselementen kunnen u nader aangeven hoe de gegevens worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="6b738-123">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6b738-123">This element is optional.</span></span> <span data-ttu-id="6b738-124">Een weergave een eigen aangepaste besturingselementen kunt definiëren of deze algemene besturingselementen die kunnen worden gebruikt door elke weergave in de opmaak-bestand kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6b738-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="6b738-125">Zie voor meer informatie over aangepaste besturingselementen [het maken van aangepaste besturingselementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6b738-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="6b738-126">De [ListControl](./listcontrol-element-format.md) element wordt gedefinieerd wat wordt weergegeven in de weergave en hoe dit wordt geformatteerd.</span><span class="sxs-lookup"><span data-stu-id="6b738-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="6b738-127">Net als bij alle andere weergaven, een lijst met weergave kan de waarden van eigenschappen van het object of de waarden die worden gegenereerd door het script.</span><span class="sxs-lookup"><span data-stu-id="6b738-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="6b738-128">Zie voor een voorbeeld van een volledige opmaak bestand dat een eenvoudige lijstweergave definieert [lijstweergave (basis)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="6b738-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="6b738-129">Definities voor de weergave te bieden</span><span class="sxs-lookup"><span data-stu-id="6b738-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="6b738-130">Lijstweergaven kunnen een of meer netwerkdefinities opgeven met behulp van de onderliggende elementen van de [ListControl](./listcontrol-element-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="6b738-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="6b738-131">Een weergave wordt meestal slechts één definitie hebben.</span><span class="sxs-lookup"><span data-stu-id="6b738-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="6b738-132">In het volgende voorbeeld wordt de weergave bevat één definitie die verschillende van eigenschappen de [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) object.</span><span class="sxs-lookup"><span data-stu-id="6b738-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="6b738-133">Een lijst met weergave kan de waarde van een eigenschap of de waarde van een script (niet weergegeven in het voorbeeld).</span><span class="sxs-lookup"><span data-stu-id="6b738-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

<span data-ttu-id="6b738-134">De volgende XML-elementen kunnen worden gebruikt voor definities voor een lijst weergeven:</span><span class="sxs-lookup"><span data-stu-id="6b738-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="6b738-135">De [ListControl](./listcontrol-element-format.md) -element en de onderliggende elementen definiëren wat wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="6b738-136">De [ListEntries](./listentries-element-for-listcontrol-format.md) element bevat de definities van de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="6b738-137">In de meeste gevallen wordt een weergave slechts één definitie hebben.</span><span class="sxs-lookup"><span data-stu-id="6b738-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="6b738-138">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="6b738-138">This element is required.</span></span>

- <span data-ttu-id="6b738-139">De [ListEntry](./listentry-element-for-listcontrol-format.md) -element bevat een definitie van de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="6b738-140">Ten minste één [ListEntry](./listentry-element-for-listcontrol-format.md) is vereist; er is echter geen maximale limiet voor het aantal elementen die u kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="6b738-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="6b738-141">In de meeste gevallen wordt een weergave slechts één definitie hebben.</span><span class="sxs-lookup"><span data-stu-id="6b738-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="6b738-142">De [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element Hiermee geeft u de objecten die worden weergegeven door de definitie van een specifieke.</span><span class="sxs-lookup"><span data-stu-id="6b738-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="6b738-143">Dit element is optioneel en is alleen nodig wanneer u meerdere definiëren [ListEntry](./listentry-element-for-listcontrol-format.md) elementen die verschillende objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="6b738-144">De [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element Hiermee geeft u de eigenschappen en -scripts waarvan de waarden worden weergegeven in de rijen van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="6b738-145">De [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element Hiermee geeft u een eigenschap of een script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="6b738-146">Een lijst weergeven moet ten minste één eigenschap of script opgeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="6b738-147">Er is geen maximale limiet voor het aantal rijen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="6b738-148">De [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="6b738-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="6b738-149">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="6b738-150">De [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u het script waarvan de waarde wordt weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="6b738-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="6b738-151">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="6b738-152">De [Label](./label-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u het label dat wordt weergegeven aan de linkerkant van de waarde voor eigenschap of het script in de rij.</span><span class="sxs-lookup"><span data-stu-id="6b738-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="6b738-153">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6b738-153">This element is optional.</span></span> <span data-ttu-id="6b738-154">Als een label niet opgegeven is, wordt de naam van de eigenschap of het script wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="6b738-155">Zie voor een compleet voorbeeld [lijstweergave (Labels)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="6b738-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="6b738-156">De [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u een voorwaarde die moet aanwezig zijn voor de rij moet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="6b738-157">Zie voor meer informatie over het toevoegen van voorwaarden aan de lijstweergave [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6b738-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="6b738-158">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6b738-158">This element is optional.</span></span>

- <span data-ttu-id="6b738-159">De [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u een patroon dat wordt gebruikt om de waarde van de eigenschap of het script weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6b738-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="6b738-160">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6b738-160">This element is optional.</span></span>

<span data-ttu-id="6b738-161">Zie voor een voorbeeld van een volledige opmaak bestand dat een eenvoudige lijstweergave definieert [lijstweergave (basis)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="6b738-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="6b738-162">Definieert de objecten die gebruikmaken van de lijstweergave</span><span class="sxs-lookup"><span data-stu-id="6b738-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="6b738-163">Er zijn twee manieren om te definiëren welke .NET-objecten worden gebruikt in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="6b738-164">U kunt de [ViewSelectedBy](./viewselectedby-element-format.md) element voor het definiëren van de objecten die kunnen worden weergegeven door de definities van de weergave, of u kunt de [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element te definiëren welke objecten worden weergegeven door een de definitie van de weergave van specifieke.</span><span class="sxs-lookup"><span data-stu-id="6b738-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="6b738-165">In de meeste gevallen een weergave heeft slechts één definitie zodat objecten worden gewoonlijk gedefinieerd door de [ViewSelectedBy](./viewselectedby-element-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="6b738-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="6b738-166">Het volgende voorbeeld ziet u hoe u de objecten die worden weergegeven door de lijst weergeven met behulp van de [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) elementen.</span><span class="sxs-lookup"><span data-stu-id="6b738-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="6b738-167">Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) elementen dat u opgeven kunt en de volgorde niet belangrijk is.</span><span class="sxs-lookup"><span data-stu-id="6b738-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="6b738-168">De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de lijstweergave:</span><span class="sxs-lookup"><span data-stu-id="6b738-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="6b738-169">De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="6b738-170">De [TypeName](./typename-element-for-viewselectedby-format.md) element Hiermee geeft u de .NET-object dat door de weergave wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="6b738-171">De volledig gekwalificeerde naam van de .NET-type is vereist.</span><span class="sxs-lookup"><span data-stu-id="6b738-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="6b738-172">U moet ten minste één type of de selectie instellen voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="6b738-173">Zie voor een voorbeeld van een volledige opmaak bestand [lijstweergave (basis)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="6b738-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="6b738-174">Het volgende voorbeeld wordt de [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementen.</span><span class="sxs-lookup"><span data-stu-id="6b738-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="6b738-175">Gebruik selectie wordt ingesteld wanneer er een gerelateerde set van objecten die worden weergegeven met behulp van meerdere weergaven, zoals wanneer u een lijst weergeven en een tabelweergave voor dezelfde objecten definiëren.</span><span class="sxs-lookup"><span data-stu-id="6b738-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="6b738-176">Zie voor meer informatie over het maken van een selectieset [selectiesets definiëren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6b738-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="6b738-177">De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de lijstweergave:</span><span class="sxs-lookup"><span data-stu-id="6b738-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="6b738-178">De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="6b738-179">De [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element Hiermee geeft u een set van objecten die kunnen worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="6b738-180">U moet ten minste één selectie instellen of type voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="6b738-181">Het volgende voorbeeld ziet u hoe u de objecten weergegeven door een specifieke definitie van de lijst weergeven met behulp van de [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="6b738-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="6b738-182">Met behulp van dit element, kunt u de .NET-typenaam van het object, een selectieset objecten of een selectievoorwaarde waarmee wordt aangegeven wanneer de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6b738-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="6b738-183">Zie voor meer informatie over het maken van een selectie voorwaarden [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6b738-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="6b738-184">De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door een specifieke definitie van de lijstweergave:</span><span class="sxs-lookup"><span data-stu-id="6b738-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="6b738-185">De [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="6b738-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="6b738-186">De [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element Hiermee geeft u de .NET-object dat door de definitie wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="6b738-187">Wanneer u dit element gebruikt, is de volledig gekwalificeerde naam van de .NET-type is vereist.</span><span class="sxs-lookup"><span data-stu-id="6b738-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="6b738-188">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="6b738-189">De [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u een set van objecten die kunnen worden weergegeven door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="6b738-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="6b738-190">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="6b738-191">De [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u een voorwaarde moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6b738-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="6b738-192">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="6b738-193">Zie voor meer informatie over het definiëren van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6b738-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="6b738-194">Groepen of objecten weergeven in een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="6b738-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="6b738-195">U kunt de objecten die worden weergegeven door de lijstweergave in groepen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="6b738-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="6b738-196">Dit betekent niet dat u een groep definieert, alleen of Windows PowerShell wordt een nieuwe groep gestart wanneer de waarde van een bepaalde eigenschap of script wijzigt.</span><span class="sxs-lookup"><span data-stu-id="6b738-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="6b738-197">In het volgende voorbeeld wordt een nieuwe groep wordt gestart wanneer de waarde van de [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) wijzigingen in de eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="6b738-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="6b738-198">De volgende XML-elementen worden gebruikt om te definiëren wanneer een groep wordt gestart:</span><span class="sxs-lookup"><span data-stu-id="6b738-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="6b738-199">De [GroupBy](./groupby-element-for-view-format.md) element wordt gedefinieerd voor de eigenschap of het script dat de nieuwe groep wordt gestart en wordt gedefinieerd hoe de groep wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="6b738-200">De [PropertyName](./propertyname-element-for-groupby-format.md) element Hiermee geeft u de eigenschap waarmee een nieuwe groep wordt gestart wanneer de waarde ervan verandert.</span><span class="sxs-lookup"><span data-stu-id="6b738-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="6b738-201">U moet een eigenschap of het script voor het starten van de groep opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="6b738-202">De [ScriptBlock](./scriptblock-element-for-groupby-format.md) element Hiermee geeft u het script dat een nieuwe groep wordt gestart wanneer de waarde ervan verandert.</span><span class="sxs-lookup"><span data-stu-id="6b738-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="6b738-203">U moet een script of een eigenschap te starten van de groep opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="6b738-204">De [Label](./label-element-for-groupby-format.md) element een label dat wordt weergegeven aan het begin van elke groep wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="6b738-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="6b738-205">Naast de tekst die is opgegeven door dit element, wordt de waarde die de nieuwe groep geactiveerd en wordt een lege regel toegevoegd voor en na het label weergegeven in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6b738-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="6b738-206">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6b738-206">This element is optional.</span></span>

- <span data-ttu-id="6b738-207">De [CustomControl](./customcontrol-element-for-groupby-format.md) element wordt gedefinieerd voor een besturingselement dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6b738-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="6b738-208">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6b738-208">This element is optional.</span></span>

- <span data-ttu-id="6b738-209">De [CustomControlName](./customcontrolname-element-for-groupby-format.md) element Hiermee geeft u een algemene of besturingselement dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6b738-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="6b738-210">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6b738-210">This element is optional.</span></span>

<span data-ttu-id="6b738-211">Zie voor een voorbeeld van een volledige opmaak bestand dat groepen worden gedefinieerd, [lijstweergave (GroupBy)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="6b738-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="6b738-212">Met behulp van opmaaktekenreeksen</span><span class="sxs-lookup"><span data-stu-id="6b738-212">Using Format Strings</span></span>

<span data-ttu-id="6b738-213">Opmaak tekenreeksen kunnen worden toegevoegd aan een weergave om verder te definiëren hoe de gegevens worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="6b738-214">Het volgende voorbeeld ziet u hoe u een opmaaktekenreeks voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="6b738-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="6b738-215">De volgende XML-elementen kunnen worden gebruikt om op te geven van een patroon indeling:</span><span class="sxs-lookup"><span data-stu-id="6b738-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="6b738-216">De [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element Hiermee geeft u de gegevens die worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="6b738-217">De [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="6b738-218">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="6b738-219">De [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="6b738-220">De [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u het script waarvan de waarde wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="6b738-221">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="6b738-222">In het volgende voorbeeld wordt de `ToString` methode aangeroepen om de indeling van de waarde van het script.</span><span class="sxs-lookup"><span data-stu-id="6b738-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="6b738-223">Scripts kunnen elke methode van een object aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="6b738-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="6b738-224">Dus als een object een methode, zoals heeft `ToString`, met parameters voor formatteren, het script dat methode voor de indeling van de uitvoerwaarde van het script kunt aanroepen.</span><span class="sxs-lookup"><span data-stu-id="6b738-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="6b738-225">De volgende XML-element kan worden gebruikt voor aanroepen de `ToString` methode:</span><span class="sxs-lookup"><span data-stu-id="6b738-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="6b738-226">De [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element Hiermee geeft u de gegevens die worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="6b738-227">De [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u het script waarvan de waarde wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="6b738-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="6b738-228">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6b738-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b738-229">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6b738-229">See Also</span></span>

[<span data-ttu-id="6b738-230">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6b738-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
