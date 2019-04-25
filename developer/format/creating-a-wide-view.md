---
title: Het maken van een brede weergave | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066716"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="3a257-102">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="3a257-102">Creating a Wide View</span></span>

<span data-ttu-id="3a257-103">Een brede weergave toont één waarde voor elk object dat wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="3a257-104">De weergegeven waarde mag de waarde van de eigenschap van een .NET-object of de waarde van een script.</span><span class="sxs-lookup"><span data-stu-id="3a257-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="3a257-105">Standaard is er geen label of de header voor deze weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="3a257-106">Een brede weergave weer te geven</span><span class="sxs-lookup"><span data-stu-id="3a257-106">A Wide View Display</span></span>

<span data-ttu-id="3a257-107">Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object dat wordt geretourneerd door de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet wanneer de uitvoer is doorgesluisd naar de [ Indeling hele](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a257-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="3a257-108">(Standaard het [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet retourneert een tabelweergave.) In dit voorbeeld worden de twee kolommen worden gebruikt om de naam van het proces voor elke geretourneerde object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3a257-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="3a257-109">De naam van eigenschap van het object niet wordt weergegeven, alleen de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3a257-109">The name of the object's property is not displayed, only the value of the property.</span></span>

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a><span data-ttu-id="3a257-110">De brede weergave definiëren</span><span class="sxs-lookup"><span data-stu-id="3a257-110">Defining the Wide View</span></span>

<span data-ttu-id="3a257-111">Het volgende XML-bestand ziet u het schema van de brede weergave voor de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span><span class="sxs-lookup"><span data-stu-id="3a257-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

<span data-ttu-id="3a257-112">De volgende XML-elementen worden gebruikt voor het definiëren van een brede weergave:</span><span class="sxs-lookup"><span data-stu-id="3a257-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="3a257-113">De [weergave](./view-element-format.md) -element is het bovenliggende element van de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="3a257-114">(Dit is hetzelfde bovenliggende element voor de tabel, lijst en weergaven voor het aangepaste besturingselement).</span><span class="sxs-lookup"><span data-stu-id="3a257-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="3a257-115">De [naam](./name-element-for-view-format.md) element Hiermee geeft u de naam van de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="3a257-116">Dit element is vereist voor alle weergaven.</span><span class="sxs-lookup"><span data-stu-id="3a257-116">This element is required for all views.</span></span>

- <span data-ttu-id="3a257-117">De [ViewSelectedBy](./viewselectedby-element-format.md) element definieert de objecten die gebruikmaken van de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="3a257-118">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="3a257-118">This element is required.</span></span>

- <span data-ttu-id="3a257-119">De [GroupBy](./groupby-element-for-view-format.md) element wordt gedefinieerd wanneer een nieuwe groep objecten wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="3a257-120">Een nieuwe groep wordt gestart wanneer de waarde van een bepaalde eigenschap of script wijzigt.</span><span class="sxs-lookup"><span data-stu-id="3a257-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="3a257-121">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3a257-121">This element is optional.</span></span>

- <span data-ttu-id="3a257-122">De [besturingselementen](./controls-element-for-view-format.md) elementen definieert de aangepaste besturingselementen die zijn gedefinieerd door de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="3a257-123">Besturingselementen kunnen u nader aangeven hoe de gegevens worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="3a257-124">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3a257-124">This element is optional.</span></span> <span data-ttu-id="3a257-125">Een weergave een eigen aangepaste besturingselementen kunt definiëren of deze algemene besturingselementen die kunnen worden gebruikt door elke weergave in de opmaak-bestand kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3a257-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="3a257-126">Zie voor meer informatie over aangepaste besturingselementen [het maken van aangepaste besturingselementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3a257-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="3a257-127">De [WideControl](./widecontrol-element-format.md) -element en de onderliggende elementen definiëren wat wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="3a257-128">In het voorgaande voorbeeld wordt de weergave is ontworpen om weer te geven de [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3a257-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="3a257-129">Zie voor een voorbeeld van een volledige opmaak bestand dat een eenvoudige brede weergave definieert [brede weergave (basis)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="3a257-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="3a257-130">Definities voor uw brede weergave bieden</span><span class="sxs-lookup"><span data-stu-id="3a257-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="3a257-131">Breed weergaven kunnen een of meer definities bieden met behulp van de onderliggende elementen van de [WideControl](./widecontrol-element-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="3a257-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="3a257-132">Een weergave wordt meestal slechts één definitie hebben.</span><span class="sxs-lookup"><span data-stu-id="3a257-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="3a257-133">In het volgende voorbeeld wordt de weergave bevat één definitie die de waarde van wordt de [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3a257-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="3a257-134">Een brede weergave kan de waarde van een eigenschap of de waarde van een script (niet weergegeven in het voorbeeld).</span><span class="sxs-lookup"><span data-stu-id="3a257-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="3a257-135">De volgende XML-elementen kunnen worden gebruikt voor definities voor een brede weergave:</span><span class="sxs-lookup"><span data-stu-id="3a257-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="3a257-136">De [WideControl](./widecontrol-element-format.md) -element en de onderliggende elementen definiëren wat wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="3a257-137">De [AutoSize](./autosize-element-for-widecontrol-format.md) element geeft aan of de kolomgrootte en het aantal kolommen zijn aangepast op basis van de grootte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="3a257-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="3a257-138">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3a257-138">This element is optional.</span></span>

- <span data-ttu-id="3a257-139">De [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element Hiermee geeft u het aantal kolommen in de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="3a257-140">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3a257-140">This element is optional.</span></span>

- <span data-ttu-id="3a257-141">De [WideEntries](./wideentries-element-for-widecontrol-format.md) element bevat de definities van de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="3a257-142">In de meeste gevallen wordt een weergave slechts één definitie hebben.</span><span class="sxs-lookup"><span data-stu-id="3a257-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="3a257-143">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="3a257-143">This element is required.</span></span>

- <span data-ttu-id="3a257-144">De [WideEntry](./wideentry-element-for-widecontrol-format.md) -element bevat een definitie van de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="3a257-145">Ten minste één [WideEntry](./wideentry-element-for-widecontrol-format.md) is vereist; er is echter geen maximale limiet voor het aantal elementen die u kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="3a257-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="3a257-146">In de meeste gevallen wordt een weergave slechts één definitie hebben.</span><span class="sxs-lookup"><span data-stu-id="3a257-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="3a257-147">De [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element Hiermee geeft u de objecten die worden weergegeven door de definitie van een specifieke.</span><span class="sxs-lookup"><span data-stu-id="3a257-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="3a257-148">Dit element is optioneel en is alleen nodig wanneer u meerdere definiëren [WideEntry](./wideentry-element-for-widecontrol-format.md) elementen die verschillende objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="3a257-149">De [WideItem](./wideitem-element-for-widecontrol-format.md) element Hiermee geeft u de gegevens die worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="3a257-150">In tegenstelling tot andere typen weergaven, een breed besturingselement kan slechts één item worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="3a257-151">De [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="3a257-152">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="3a257-153">De [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element Hiermee geeft u het script waarvan de waarde wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="3a257-154">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="3a257-155">De [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element Hiermee geeft u een patroon dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3a257-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="3a257-156">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3a257-156">This element is optional.</span></span>

<span data-ttu-id="3a257-157">Zie voor een voorbeeld van een volledige opmaak-bestand dat de definitie van een brede weergave definieert [brede weergave (basis)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="3a257-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="3a257-158">De objecten die gebruikmaken van de brede weergave definiëren</span><span class="sxs-lookup"><span data-stu-id="3a257-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="3a257-159">Er zijn twee manieren om te definiëren welke objecten .NET gebruik maken van de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="3a257-160">U kunt de [ViewSelectedBy](./viewselectedby-element-format.md) element voor het definiëren van de objecten die kunnen worden weergegeven door de definities van de weergave, of u kunt de [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element te definiëren welke objecten worden weergegeven door een de definitie van de weergave van specifieke.</span><span class="sxs-lookup"><span data-stu-id="3a257-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="3a257-161">In de meeste gevallen een weergave heeft slechts één definitie zodat objecten worden gewoonlijk gedefinieerd door de [ViewSelectedBy](./viewselectedby-element-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="3a257-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="3a257-162">Het volgende voorbeeld ziet u hoe u de objecten die worden weergegeven met behulp van de brede weergave de [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) elementen.</span><span class="sxs-lookup"><span data-stu-id="3a257-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="3a257-163">Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) elementen dat u opgeven kunt en de volgorde niet belangrijk is.</span><span class="sxs-lookup"><span data-stu-id="3a257-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="3a257-164">De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de brede weergave:</span><span class="sxs-lookup"><span data-stu-id="3a257-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="3a257-165">De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="3a257-166">De [TypeName](./typename-element-for-viewselectedby-format.md) element Hiermee geeft u de .NET die wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="3a257-167">De volledig gekwalificeerde naam van de .NET-type is vereist.</span><span class="sxs-lookup"><span data-stu-id="3a257-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="3a257-168">U moet ten minste één type of de selectie instellen voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="3a257-169">Zie voor een voorbeeld van een volledige opmaak bestand [brede weergave (basis)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="3a257-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="3a257-170">Het volgende voorbeeld wordt de [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementen.</span><span class="sxs-lookup"><span data-stu-id="3a257-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="3a257-171">Gebruik selectiesets waarin u een gerelateerde set van objecten die worden weergegeven met behulp van meerdere weergaven, zoals wanneer u een brede weergave definiëren en een tabelweergave voor dezelfde objecten hebben.</span><span class="sxs-lookup"><span data-stu-id="3a257-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="3a257-172">Zie voor meer informatie over het maken van een selectieset [selectiesets definiëren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3a257-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="3a257-173">De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de brede weergave:</span><span class="sxs-lookup"><span data-stu-id="3a257-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="3a257-174">De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="3a257-175">De [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element Hiermee geeft u een set van objecten die kunnen worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="3a257-176">U moet ten minste één selectie instellen of type voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="3a257-177">Het volgende voorbeeld ziet u hoe u de objecten die met een specifieke definitie van het gebruik van de brede weergave wordt weergegeven de [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="3a257-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="3a257-178">Met behulp van dit element, kunt u de .NET-typenaam van het object, een selectieset objecten of een selectievoorwaarde waarmee wordt aangegeven wanneer de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3a257-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="3a257-179">Zie voor meer informatie over het maken van een selectie voorwaarden [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3a257-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="3a257-180">De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door een specifieke definitie van de brede weergave:</span><span class="sxs-lookup"><span data-stu-id="3a257-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="3a257-181">De [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="3a257-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="3a257-182">De [TypeName](./typename-element-for-viewselectedby-format.md) element Hiermee geeft u de .NET die wordt weergegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="3a257-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="3a257-183">Bij het gebruik van dit element is de volledig gekwalificeerde naam van de .NET-type is vereist.</span><span class="sxs-lookup"><span data-stu-id="3a257-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="3a257-184">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="3a257-185">De [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (niet weergegeven) Hiermee geeft u een set van objecten die kunnen worden weergegeven door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="3a257-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="3a257-186">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="3a257-187">De [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (niet weergegeven) Hiermee geeft u een voorwaarde moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3a257-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="3a257-188">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="3a257-189">Zie voor meer informatie over het definiëren van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3a257-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="3a257-190">Groepen van objecten weergeven in een brede weergave</span><span class="sxs-lookup"><span data-stu-id="3a257-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="3a257-191">U kunt de objecten die worden weergegeven door de brede weergave in groepen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="3a257-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="3a257-192">Dit betekent niet dat u een groep definieert, alleen of Windows PowerShell wordt een nieuwe groep gestart wanneer de waarde van een bepaalde eigenschap of script wijzigt.</span><span class="sxs-lookup"><span data-stu-id="3a257-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="3a257-193">In het volgende voorbeeld wordt een nieuwe groep wordt gestart wanneer de waarde van de [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) wijzigingen in de eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="3a257-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="3a257-194">De volgende XML-elementen worden gebruikt om te definiëren wanneer een groep wordt gestart:</span><span class="sxs-lookup"><span data-stu-id="3a257-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="3a257-195">De [GroupBy](./groupby-element-for-view-format.md) element wordt gedefinieerd voor de eigenschap of het script dat de nieuwe groep wordt gestart en wordt gedefinieerd hoe de groep wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="3a257-196">De [PropertyName](./propertyname-element-for-groupby-format.md) element Hiermee geeft u de eigenschap waarmee een nieuwe groep wordt gestart wanneer de waarde ervan verandert.</span><span class="sxs-lookup"><span data-stu-id="3a257-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="3a257-197">U moet een eigenschap of het script voor het starten van de groep opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="3a257-198">De [ScriptBlock](./scriptblock-element-for-groupby-format.md) element Hiermee geeft u het script dat een nieuwe groep wordt gestart wanneer de waarde ervan verandert.</span><span class="sxs-lookup"><span data-stu-id="3a257-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="3a257-199">U moet een script of een eigenschap te starten van de groep opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="3a257-200">De [Label](./label-element-for-groupby-format.md) element een label dat wordt weergegeven aan het begin van elke groep wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="3a257-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="3a257-201">Naast de tekst die is opgegeven door dit element, wordt de waarde die de nieuwe groep geactiveerd en wordt een lege regel toegevoegd voor en na het label weergegeven in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a257-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="3a257-202">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3a257-202">This element is optional.</span></span>

- <span data-ttu-id="3a257-203">De [CustomControl](./customcontrol-element-for-groupby-format.md) element wordt gedefinieerd voor een besturingselement dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3a257-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="3a257-204">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3a257-204">This element is optional.</span></span>

- <span data-ttu-id="3a257-205">De [CustomControlName](./customcontrolname-element-for-groupby-format.md) element Hiermee geeft u een algemene of besturingselement dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3a257-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="3a257-206">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3a257-206">This element is optional.</span></span>

<span data-ttu-id="3a257-207">Zie voor een voorbeeld van een volledige opmaak bestand dat groepen worden gedefinieerd, [brede weergave (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="3a257-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="3a257-208">Met behulp van opmaaktekenreeksen</span><span class="sxs-lookup"><span data-stu-id="3a257-208">Using Format Strings</span></span>

<span data-ttu-id="3a257-209">Opmaak tekenreeksen kunnen worden toegevoegd aan een brede weergave om verder te definiëren hoe de gegevens worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="3a257-210">Het volgende voorbeeld ziet u hoe u een opmaaktekenreeks voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3a257-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="3a257-211">De volgende XML-elementen kunnen worden gebruikt om op te geven van een patroon indeling:</span><span class="sxs-lookup"><span data-stu-id="3a257-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="3a257-212">De [WideItem](./wideitem-element-for-widecontrol-format.md) element Hiermee geeft u de gegevens die worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="3a257-213">De [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="3a257-214">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="3a257-215">De [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven in de weergave</span><span class="sxs-lookup"><span data-stu-id="3a257-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="3a257-216">De [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (niet weergegeven) Hiermee geeft u het script waarvan de waarde wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="3a257-217">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="3a257-218">In het volgende voorbeeld wordt de `ToString` methode aangeroepen om de indeling van de waarde van het script.</span><span class="sxs-lookup"><span data-stu-id="3a257-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="3a257-219">Scripts kunnen elke methode van een object aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="3a257-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="3a257-220">Dus als een object een methode, zoals heeft `ToString`, met parameters voor formatteren, het script dat methode voor de indeling van de uitvoerwaarde van het script kunt aanroepen.</span><span class="sxs-lookup"><span data-stu-id="3a257-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="3a257-221">De volgende XML-element kan worden gebruikt voor aanroepen de `ToString` methode:</span><span class="sxs-lookup"><span data-stu-id="3a257-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="3a257-222">De [WideItem](./wideitem-element-for-widecontrol-format.md) element Hiermee geeft u de gegevens die worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="3a257-223">De [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (niet weergegeven) Hiermee geeft u het script waarvan de waarde wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="3a257-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="3a257-224">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3a257-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a257-225">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3a257-225">See Also</span></span>

[<span data-ttu-id="3a257-226">Brede weergave (basis)</span><span class="sxs-lookup"><span data-stu-id="3a257-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="3a257-227">Brede weergave (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="3a257-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="3a257-228">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a257-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
