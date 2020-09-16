---
title: Een lijst weergave maken | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 24eb673e0db011a1439fa5ba1f2966fcc3bdc338
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783769"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="2383b-102">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="2383b-102">Creating a List View</span></span>

<span data-ttu-id="2383b-103">In een lijst weergave worden gegevens in één kolom weer gegeven (in sequentiële volg orde).</span><span class="sxs-lookup"><span data-stu-id="2383b-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="2383b-104">De gegevens die in de lijst worden weer gegeven, kunnen de waarde van een .NET-eigenschap of de waarde van een script zijn.</span><span class="sxs-lookup"><span data-stu-id="2383b-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="2383b-105">Een lijst weergave weer geven</span><span class="sxs-lookup"><span data-stu-id="2383b-105">A List View Display</span></span>

<span data-ttu-id="2383b-106">In de volgende uitvoer ziet u hoe de eigenschappen van [System. ServiceProcess. servicecontroller worden weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten die worden geretourneerd door de cmdlet [Get-service](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="2383b-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="2383b-107">In dit voor beeld zijn er drie objecten geretourneerd, waarbij elk object is gescheiden van het voor gaande object door een lege regel.</span><span class="sxs-lookup"><span data-stu-id="2383b-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

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

## <a name="defining-the-list-view"></a><span data-ttu-id="2383b-108">De lijst weergave definiëren</span><span class="sxs-lookup"><span data-stu-id="2383b-108">Defining the List View</span></span>

<span data-ttu-id="2383b-109">In het volgende XML-bestand wordt het lijst weergave schema weer gegeven voor het weer geven van verschillende eigenschappen van [System. ServiceProcess. servicecontroller? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -object.</span><span class="sxs-lookup"><span data-stu-id="2383b-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="2383b-110">U moet elke eigenschap opgeven die u wilt weer geven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="2383b-110">You must specify each property that you want displayed in the list view.</span></span>

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

<span data-ttu-id="2383b-111">De volgende XML-elementen worden gebruikt voor het definiëren van een lijst weergave:</span><span class="sxs-lookup"><span data-stu-id="2383b-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="2383b-112">Het element [View](./view-element-format.md) is het bovenliggende element van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="2383b-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="2383b-113">(Dit is hetzelfde bovenliggende element voor de tabel-, brede en aangepaste besturings elementen.)</span><span class="sxs-lookup"><span data-stu-id="2383b-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="2383b-114">Het element [name](./name-element-for-view-format.md) specificeert de naam van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="2383b-115">Dit element is vereist voor alle weer gaven.</span><span class="sxs-lookup"><span data-stu-id="2383b-115">This element is required for all views.</span></span>

- <span data-ttu-id="2383b-116">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="2383b-117">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="2383b-117">This element is required.</span></span>

- <span data-ttu-id="2383b-118">Het element [GroupBy](./groupby-element-for-view-format.md) definieert wanneer een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="2383b-119">Er wordt een nieuwe groep gestart wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="2383b-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="2383b-120">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="2383b-120">This element is optional.</span></span>

- <span data-ttu-id="2383b-121">Het element [Controls](./controls-element-for-view-format.md) definieert de aangepaste besturings elementen die door de lijst weergave worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2383b-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="2383b-122">Met besturings elementen kunt u nader aangeven hoe de gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="2383b-123">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="2383b-123">This element is optional.</span></span> <span data-ttu-id="2383b-124">Een weer gave kan zijn eigen aangepaste besturings elementen definiëren, maar u kunt ook algemene besturings elementen gebruiken die kunnen worden gebruikt door elke weer gave in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="2383b-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="2383b-125">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over aangepaste besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="2383b-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="2383b-126">Het element [ListControl](./listcontrol-element-format.md) definieert wat wordt weer gegeven in de weer gave en hoe het is opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="2383b-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="2383b-127">Net als bij alle andere weer gaven kunnen in een lijst weergave de waarden van object eigenschappen of waarden worden weer gegeven die door het script worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="2383b-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="2383b-128">Zie [lijst weergave (Basic)](./list-view-basic.md)voor een voor beeld van een volledig opmaak bestand dat een eenvoudige lijst weergave definieert.</span><span class="sxs-lookup"><span data-stu-id="2383b-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="2383b-129">Definities opgeven voor de lijst weergave</span><span class="sxs-lookup"><span data-stu-id="2383b-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="2383b-130">Lijst Weergaven kunnen een of meer definities bieden met behulp van de onderliggende elementen van het element [ListControl](./listcontrol-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="2383b-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="2383b-131">Normaal gesp roken bevat een weer gave slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="2383b-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="2383b-132">In het volgende voor beeld bevat de weer gave één definitie waarin verschillende eigenschappen van het [systeem. Diagnostics. process worden weer gegeven? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -object.</span><span class="sxs-lookup"><span data-stu-id="2383b-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="2383b-133">Een lijst weergave kan de waarde van een eigenschap of de waarde van een script weer geven (niet weer gegeven in het voor beeld).</span><span class="sxs-lookup"><span data-stu-id="2383b-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="2383b-134">De volgende XML-elementen kunnen worden gebruikt om definities op te geven voor een lijst weergave:</span><span class="sxs-lookup"><span data-stu-id="2383b-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="2383b-135">Het element [ListControl](./listcontrol-element-format.md) en de onderliggende elementen bepalen wat wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="2383b-136">Het element [List entries](./listentries-element-for-listcontrol-format.md) bevat de definities van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="2383b-137">In de meeste gevallen heeft een weer gave slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="2383b-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="2383b-138">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="2383b-138">This element is required.</span></span>

- <span data-ttu-id="2383b-139">Het element [List entry](./listentry-element-for-listcontrol-format.md) bevat een definitie van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="2383b-140">Er is ten minste één [List entry](./listentry-element-for-listcontrol-format.md) vereist; Er is echter geen maximum limiet voor het aantal elementen dat u kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="2383b-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="2383b-141">In de meeste gevallen heeft een weer gave slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="2383b-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="2383b-142">Het [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -element geeft de objecten aan die door een specifieke definitie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="2383b-143">Dit element is optioneel en is alleen nodig wanneer u meerdere [List entry](./listentry-element-for-listcontrol-format.md) -elementen definieert waarin verschillende objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="2383b-144">Het [list items](./listitems-element-for-listentry-for-listcontrol-format.md) -element geeft de eigenschappen en scripts op waarvan de waarden worden weer gegeven in de rijen van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="2383b-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="2383b-145">Het element [lijst item](./listitems-element-for-listentry-for-listcontrol-format.md) geeft een eigenschap of script op waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="2383b-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="2383b-146">In een lijst weergave moet ten minste één eigenschap of script worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="2383b-147">Er is geen maximum limiet voor het aantal rijen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="2383b-148">Met het element [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="2383b-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="2383b-149">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="2383b-150">Het [script Block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -element geeft het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="2383b-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="2383b-151">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="2383b-152">Het [Label](./label-element-for-listitem-for-listcontrol-format.md) element geeft het label aan dat links van de eigenschap of script waarde in de rij wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="2383b-153">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="2383b-153">This element is optional.</span></span> <span data-ttu-id="2383b-154">Als er geen label is opgegeven, wordt de naam van de eigenschap of het script weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="2383b-155">Zie [lijst weergave (labels)](./list-view-labels.md)voor een volledig voor beeld.</span><span class="sxs-lookup"><span data-stu-id="2383b-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="2383b-156">Het [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) -element geeft een voor waarde aan die moet bestaan om de rij weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2383b-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="2383b-157">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het toevoegen van voor waarden aan de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="2383b-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="2383b-158">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="2383b-158">This element is optional.</span></span>

- <span data-ttu-id="2383b-159">Het element [formats Tring](./formatstring-element-for-listitem-for-listcontrol-format.md) geeft een patroon op dat wordt gebruikt om de waarde van de eigenschap of het script weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2383b-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="2383b-160">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="2383b-160">This element is optional.</span></span>

<span data-ttu-id="2383b-161">Zie [lijst weergave (Basic)](./list-view-basic.md)voor een voor beeld van een volledig opmaak bestand dat een eenvoudige lijst weergave definieert.</span><span class="sxs-lookup"><span data-stu-id="2383b-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="2383b-162">De objecten definiëren die gebruikmaken van de lijst weergave</span><span class="sxs-lookup"><span data-stu-id="2383b-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="2383b-163">Er zijn twee manieren om te definiëren welke .NET-objecten gebruikmaken van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="2383b-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="2383b-164">U kunt het element [ViewSelectedBy](./viewselectedby-element-format.md) gebruiken om de objecten te definiëren die door alle definities van de weer gave kunnen worden weer gegeven, of u kunt het element [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) gebruiken om te definiëren welke objecten worden weer gegeven met een specifieke definitie van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="2383b-165">In de meeste gevallen heeft een weer gave slechts één definitie, waardoor objecten doorgaans worden gedefinieerd door het element [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="2383b-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="2383b-166">In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven in de lijst weergave met behulp van de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="2383b-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="2383b-167">Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) -elementen dat u kunt opgeven en de volg orde hiervan is niet belang rijk.</span><span class="sxs-lookup"><span data-stu-id="2383b-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="2383b-168">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de lijst weergave:</span><span class="sxs-lookup"><span data-stu-id="2383b-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="2383b-169">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="2383b-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="2383b-170">Het element [TypeName](./typename-element-for-viewselectedby-format.md) specificeert het .net-object dat wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="2383b-171">De volledig gekwalificeerde .NET-type naam is vereist.</span><span class="sxs-lookup"><span data-stu-id="2383b-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="2383b-172">U moet ten minste één type of selectieset voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="2383b-173">Zie [lijst weergave (Basic)](./list-view-basic.md)voor een voor beeld van een volledig indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="2383b-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="2383b-174">In het volgende voor beeld worden de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2383b-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="2383b-175">Gebruik selectie sets waar u een gerelateerde set objecten hebt die worden weer gegeven met behulp van meerdere weer gaven, zoals wanneer u een lijst weergave definieert en een tabel weergave voor dezelfde objecten.</span><span class="sxs-lookup"><span data-stu-id="2383b-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="2383b-176">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken van een selectie reeks.</span><span class="sxs-lookup"><span data-stu-id="2383b-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="2383b-177">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de lijst weergave:</span><span class="sxs-lookup"><span data-stu-id="2383b-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="2383b-178">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="2383b-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="2383b-179">Het [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -element geeft een set objecten op die door de weer gave kan worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="2383b-180">U moet ten minste één selectieset of type voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="2383b-181">In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven met een specifieke definitie van de lijst weergave met behulp van het element [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="2383b-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="2383b-182">Met dit element kunt u de .NET-type naam van het object, een selectieset van objecten of een selectie voorwaarde opgeven die opgeeft wanneer de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2383b-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="2383b-183">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het maken van een selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="2383b-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="2383b-184">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door een specifieke definitie van de lijst weergave:</span><span class="sxs-lookup"><span data-stu-id="2383b-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="2383b-185">Het [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -element definieert welke objecten worden weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="2383b-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="2383b-186">Het element [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) specificeert het .net-object dat wordt weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="2383b-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="2383b-187">Wanneer u dit element gebruikt, is de volledig gekwalificeerde .NET-type naam vereist.</span><span class="sxs-lookup"><span data-stu-id="2383b-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="2383b-188">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="2383b-189">Het [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -element (niet weer gegeven) bevat een set objecten die kunnen worden weer gegeven door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="2383b-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="2383b-190">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="2383b-191">Het element [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (niet weer gegeven) bevat een voor waarde die voor deze definitie moet bestaan.</span><span class="sxs-lookup"><span data-stu-id="2383b-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="2383b-192">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="2383b-193">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="2383b-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="2383b-194">Groepen van objecten in een lijst weergave weer geven</span><span class="sxs-lookup"><span data-stu-id="2383b-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="2383b-195">U kunt de objecten die door de lijst weergave worden weer gegeven, scheiden in groepen.</span><span class="sxs-lookup"><span data-stu-id="2383b-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="2383b-196">Dit betekent niet dat u een groep definieert, alleen dat Windows Power shell een nieuwe groep start wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="2383b-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="2383b-197">In het volgende voor beeld wordt een nieuwe groep gestart wanneer de waarde van de eigenschap [System. ServiceProcess. servicecontroller. service](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) type wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="2383b-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="2383b-198">De volgende XML-elementen worden gebruikt om te definiëren wanneer een groep wordt gestart:</span><span class="sxs-lookup"><span data-stu-id="2383b-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="2383b-199">Het element [GroupBy](./groupby-element-for-view-format.md) definieert de eigenschap of het script waarmee de nieuwe groep wordt gestart en definieert hoe de groep wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="2383b-200">Met het element [PropertyName](./propertyname-element-for-groupby-format.md) wordt de eigenschap opgegeven waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="2383b-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="2383b-201">U moet een eigenschap of script opgeven om de groep te starten, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="2383b-202">Het [script Block](./scriptblock-element-for-groupby-format.md) -element geeft het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="2383b-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="2383b-203">U moet een script of eigenschap opgeven om de groep te starten, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="2383b-204">Het element [Label](./label-element-for-groupby-format.md) definieert een label dat aan het begin van elke groep wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="2383b-205">Naast de tekst die door dit element is opgegeven, wordt in Windows Power shell de waarde weer gegeven die de nieuwe groep heeft geactiveerd en wordt een lege regel toegevoegd vóór en na het label.</span><span class="sxs-lookup"><span data-stu-id="2383b-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="2383b-206">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="2383b-206">This element is optional.</span></span>

- <span data-ttu-id="2383b-207">Het [CustomControl](./customcontrol-element-for-groupby-format.md) -element definieert een besturings element dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2383b-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="2383b-208">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="2383b-208">This element is optional.</span></span>

- <span data-ttu-id="2383b-209">Het [CustomControlName](./customcontrolname-element-for-groupby-format.md) -element geeft een algemeen of weergave besturings element op dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2383b-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="2383b-210">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="2383b-210">This element is optional.</span></span>

<span data-ttu-id="2383b-211">Zie [lijst weergave (GroupBy)](./list-view-groupby.md)voor een voor beeld van een volledig indelings bestand waarmee groepen worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2383b-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="2383b-212">Opmaak teken reeksen gebruiken</span><span class="sxs-lookup"><span data-stu-id="2383b-212">Using Format Strings</span></span>

<span data-ttu-id="2383b-213">Opmaak teken reeksen kunnen worden toegevoegd aan een weer gave om te bepalen hoe de gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="2383b-214">In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="2383b-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="2383b-215">De volgende XML-elementen kunnen worden gebruikt om een notatie patroon op te geven:</span><span class="sxs-lookup"><span data-stu-id="2383b-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="2383b-216">Het element [lijst item](./listitem-element-for-listitems-for-listcontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="2383b-217">Met het element [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="2383b-218">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="2383b-219">Het element [formats Tring](./formatstring-element-for-listitem-for-listcontrol-format.md) geeft een opmaak patroon op dat bepaalt hoe de eigenschap of script waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="2383b-220">Het element [script Block](./scriptblock-element-for-listitem-for-listcontrol-format.md) (niet weer gegeven) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="2383b-221">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="2383b-222">In het volgende voor beeld wordt de- `ToString` methode aangeroepen om de waarde van het script op te maken.</span><span class="sxs-lookup"><span data-stu-id="2383b-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="2383b-223">Scripts kunnen een wille keurige methode van een object aanroepen.</span><span class="sxs-lookup"><span data-stu-id="2383b-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="2383b-224">Als een object een methode heeft, zoals `ToString` die opmaak parameters heeft, kan het script deze methode ook aanroepen om de uitvoer waarde van het script op te maken.</span><span class="sxs-lookup"><span data-stu-id="2383b-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="2383b-225">Het volgende XML-element kan worden gebruikt om de methode aan te roepen `ToString` :</span><span class="sxs-lookup"><span data-stu-id="2383b-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="2383b-226">Het element [lijst item](./listitem-element-for-listitems-for-listcontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="2383b-227">Het element [script Block](./scriptblock-element-for-listitem-for-listcontrol-format.md) (niet weer gegeven) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2383b-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="2383b-228">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="2383b-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="2383b-229">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2383b-229">See Also</span></span>

[<span data-ttu-id="2383b-230">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="2383b-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
