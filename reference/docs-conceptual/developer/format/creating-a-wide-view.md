---
title: Een brede weer gave maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359075"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="fffa7-102">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="fffa7-102">Creating a Wide View</span></span>

<span data-ttu-id="fffa7-103">In een brede weer gave wordt één waarde weer gegeven voor elk object dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="fffa7-104">De weer gegeven waarde kan de waarde van een .NET-object eigenschap of de waarde van een script zijn.</span><span class="sxs-lookup"><span data-stu-id="fffa7-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="fffa7-105">Standaard is er geen label of kop voor deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="fffa7-106">Een brede weer gave</span><span class="sxs-lookup"><span data-stu-id="fffa7-106">A Wide View Display</span></span>

<span data-ttu-id="fffa7-107">In het volgende voor beeld ziet u hoe in Windows Power shell het [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -object wordt weer gegeven dat wordt geretourneerd door de cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) wanneer de uitvoer wordt gepiped naar de [indeling-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fffa7-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="fffa7-108">(De cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourneert standaard een tabel weergave.) In dit voor beeld worden de twee kolommen gebruikt om de naam van het proces voor elk geretourneerd object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="fffa7-109">De naam van de eigenschap van het object wordt niet weer gegeven, alleen de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="fffa7-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="fffa7-110">De brede weer gave definiëren</span><span class="sxs-lookup"><span data-stu-id="fffa7-110">Defining the Wide View</span></span>

<span data-ttu-id="fffa7-111">De volgende XML-code toont het breedste weergave schema voor het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="fffa7-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="fffa7-112">De volgende XML-elementen worden gebruikt voor het definiëren van een brede weer gave:</span><span class="sxs-lookup"><span data-stu-id="fffa7-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="fffa7-113">Het element [View](./view-element-format.md) is het bovenliggende element van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="fffa7-114">(Dit is hetzelfde bovenliggende element voor de tabel-, lijst-en aangepaste besturings elementen.)</span><span class="sxs-lookup"><span data-stu-id="fffa7-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="fffa7-115">Het element [name](./name-element-for-view-format.md) specificeert de naam van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="fffa7-116">Dit element is vereist voor alle weer gaven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-116">This element is required for all views.</span></span>

- <span data-ttu-id="fffa7-117">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="fffa7-118">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="fffa7-118">This element is required.</span></span>

- <span data-ttu-id="fffa7-119">Het element [GroupBy](./groupby-element-for-view-format.md) definieert wanneer een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="fffa7-120">Er wordt een nieuwe groep gestart wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="fffa7-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="fffa7-121">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fffa7-121">This element is optional.</span></span>

- <span data-ttu-id="fffa7-122">De elementen [Controls](./controls-element-for-view-format.md) definieert de aangepaste besturings elementen die worden gedefinieerd door de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="fffa7-123">Met besturings elementen kunt u nader aangeven hoe de gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="fffa7-124">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fffa7-124">This element is optional.</span></span> <span data-ttu-id="fffa7-125">Een weer gave kan zijn eigen aangepaste besturings elementen definiëren, maar u kunt ook algemene besturings elementen gebruiken die kunnen worden gebruikt door elke weer gave in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="fffa7-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="fffa7-126">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over aangepaste besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="fffa7-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="fffa7-127">Het [WideControl](./widecontrol-element-format.md) -element en de onderliggende elementen bepalen wat er in de weer gave wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="fffa7-128">In het voor gaande voor beeld is de weer gave ontworpen om de eigenschap [System. Diagnostics. process. Autoprocesnaam](/dotnet/api/System.Diagnostics.Process.ProcessName) weer te geven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="fffa7-129">Zie [Wide View (Basic)](./wide-view-basic.md)voor een voor beeld van een compleet opmaak bestand dat een eenvoudige, brede weer gave definieert.</span><span class="sxs-lookup"><span data-stu-id="fffa7-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="fffa7-130">Definities opgeven voor de brede weer gave</span><span class="sxs-lookup"><span data-stu-id="fffa7-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="fffa7-131">Breedbeeld weergaven kunnen een of meer definities bieden met behulp van de onderliggende elementen van het element [WideControl](./widecontrol-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="fffa7-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="fffa7-132">Normaal gesp roken bevat een weer gave slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="fffa7-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="fffa7-133">In het volgende voor beeld bevat de weer gave één definitie waarmee de waarde van de eigenschap [System. Diagnostics. process. Autoprocesnaam](/dotnet/api/System.Diagnostics.Process.ProcessName) wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="fffa7-134">Een brede weer gave kan de waarde van een eigenschap of de waarde van een script weer geven (niet weer gegeven in het voor beeld).</span><span class="sxs-lookup"><span data-stu-id="fffa7-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="fffa7-135">De volgende XML-elementen kunnen worden gebruikt om definities te bieden voor een brede weer gave:</span><span class="sxs-lookup"><span data-stu-id="fffa7-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="fffa7-136">Het [WideControl](./widecontrol-element-format.md) -element en de onderliggende elementen bepalen wat er in de weer gave wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="fffa7-137">Het element [AutoSize](./autosize-element-for-widecontrol-format.md) geeft aan of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="fffa7-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="fffa7-138">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fffa7-138">This element is optional.</span></span>

- <span data-ttu-id="fffa7-139">Het [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) -element geeft het aantal kolommen op dat wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="fffa7-140">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fffa7-140">This element is optional.</span></span>

- <span data-ttu-id="fffa7-141">Het [WideEntries](./wideentries-element-for-widecontrol-format.md) -element bevat de definities van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="fffa7-142">In de meeste gevallen heeft een weer gave slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="fffa7-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="fffa7-143">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="fffa7-143">This element is required.</span></span>

- <span data-ttu-id="fffa7-144">Het [WideEntry](./wideentry-element-for-widecontrol-format.md) -element bevat een definitie van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="fffa7-145">Er is ten minste één [WideEntry](./wideentry-element-for-widecontrol-format.md) vereist. Er is echter geen maximum limiet voor het aantal elementen dat u kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="fffa7-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="fffa7-146">In de meeste gevallen heeft een weer gave slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="fffa7-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="fffa7-147">Het [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -element geeft de objecten aan die door een specifieke definitie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="fffa7-148">Dit element is optioneel en is alleen nodig wanneer u meerdere [WideEntry](./wideentry-element-for-widecontrol-format.md) -elementen definieert waarin verschillende objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="fffa7-149">Het element [WideItem](./wideitem-element-for-widecontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="fffa7-150">In tegens telling tot andere soorten weer gaven, kan een breed besturings element slechts één item weer geven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="fffa7-151">Met het element [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="fffa7-152">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="fffa7-153">Het [script Block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -element geeft het script op waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="fffa7-154">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="fffa7-155">Het element [formats Tring](./formatstring-element-for-wideitem-for-widecontrol-format.md) geeft een patroon op dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="fffa7-156">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fffa7-156">This element is optional.</span></span>

<span data-ttu-id="fffa7-157">Zie [Wide View (Basic)](./wide-view-basic.md)voor een voor beeld van een volledige indelings bestand waarin een brede weergave definitie is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="fffa7-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="fffa7-158">De objecten definiëren die gebruikmaken van de brede weer gave</span><span class="sxs-lookup"><span data-stu-id="fffa7-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="fffa7-159">Er zijn twee manieren om te definiëren welke .NET-objecten gebruikmaken van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="fffa7-160">U kunt het element [ViewSelectedBy](./viewselectedby-element-format.md) gebruiken om de objecten te definiëren die door alle definities van de weer gave kunnen worden weer gegeven, of u kunt het element [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) gebruiken om te definiëren welke objecten worden weer gegeven met een specifieke definitie van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="fffa7-161">In de meeste gevallen heeft een weer gave slechts één definitie, waardoor objecten doorgaans worden gedefinieerd door het element [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="fffa7-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="fffa7-162">In het volgende voor beeld ziet u hoe u de objecten definieert die door de brede weer gave worden weer gegeven met behulp van de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="fffa7-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="fffa7-163">Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) -elementen dat u kunt opgeven en de volg orde hiervan is niet belang rijk.</span><span class="sxs-lookup"><span data-stu-id="fffa7-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="fffa7-164">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de brede weer gave:</span><span class="sxs-lookup"><span data-stu-id="fffa7-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="fffa7-165">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven door de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="fffa7-166">Het element [TypeName](./typename-element-for-viewselectedby-format.md) specificeert de .net die wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="fffa7-167">De volledig gekwalificeerde .NET-type naam is vereist.</span><span class="sxs-lookup"><span data-stu-id="fffa7-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="fffa7-168">U moet ten minste één type of selectieset voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="fffa7-169">Zie [Wide View (Basic)](./wide-view-basic.md)voor een voor beeld van een volledig indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="fffa7-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="fffa7-170">In het volgende voor beeld worden de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fffa7-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="fffa7-171">Gebruik selectie sets waar u een gerelateerde set objecten hebt die met meerdere weer gaven worden weer gegeven, zoals wanneer u een brede weer gave en een tabel weergave voor dezelfde objecten definieert.</span><span class="sxs-lookup"><span data-stu-id="fffa7-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="fffa7-172">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken van een selectie reeks.</span><span class="sxs-lookup"><span data-stu-id="fffa7-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="fffa7-173">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de brede weer gave:</span><span class="sxs-lookup"><span data-stu-id="fffa7-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="fffa7-174">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven door de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="fffa7-175">Het [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -element geeft een set objecten op die door de weer gave kan worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="fffa7-176">U moet ten minste één selectieset of type voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="fffa7-177">In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven met een specifieke definitie van de brede weer gave met behulp van het element [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) .</span><span class="sxs-lookup"><span data-stu-id="fffa7-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="fffa7-178">Met dit element kunt u de .NET-type naam van het object, een selectieset van objecten of een selectie voorwaarde opgeven die opgeeft wanneer de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fffa7-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="fffa7-179">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het maken van een selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="fffa7-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="fffa7-180">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door een specifieke definitie van de brede weer gave:</span><span class="sxs-lookup"><span data-stu-id="fffa7-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="fffa7-181">Het [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -element definieert welke objecten worden weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="fffa7-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="fffa7-182">Het element [TypeName](./typename-element-for-viewselectedby-format.md) specificeert de .net die wordt weer gegeven in de definitie.</span><span class="sxs-lookup"><span data-stu-id="fffa7-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="fffa7-183">Wanneer u dit element gebruikt, is de volledig gekwalificeerde .NET-type naam vereist.</span><span class="sxs-lookup"><span data-stu-id="fffa7-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="fffa7-184">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="fffa7-185">Het [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -element (niet weer gegeven) bevat een set objecten die kunnen worden weer gegeven door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="fffa7-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="fffa7-186">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="fffa7-187">Het element [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (niet weer gegeven) bevat een voor waarde die voor deze definitie moet bestaan.</span><span class="sxs-lookup"><span data-stu-id="fffa7-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="fffa7-188">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="fffa7-189">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="fffa7-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="fffa7-190">Groepen objecten weer geven in een brede weer gave</span><span class="sxs-lookup"><span data-stu-id="fffa7-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="fffa7-191">U kunt de objecten die worden weer gegeven door de brede weer gave, scheiden in groepen.</span><span class="sxs-lookup"><span data-stu-id="fffa7-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="fffa7-192">Dit betekent niet dat u een groep definieert, alleen dat Windows Power shell een nieuwe groep start wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="fffa7-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="fffa7-193">In het volgende voor beeld wordt een nieuwe groep gestart wanneer de waarde van de eigenschap [System. ServiceProcess. servicecontroller. service](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) type wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="fffa7-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="fffa7-194">De volgende XML-elementen worden gebruikt om te definiëren wanneer een groep wordt gestart:</span><span class="sxs-lookup"><span data-stu-id="fffa7-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="fffa7-195">Het element [GroupBy](./groupby-element-for-view-format.md) definieert de eigenschap of het script waarmee de nieuwe groep wordt gestart en definieert hoe de groep wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="fffa7-196">Met het element [PropertyName](./propertyname-element-for-groupby-format.md) wordt de eigenschap opgegeven waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="fffa7-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="fffa7-197">U moet een eigenschap of script opgeven om de groep te starten, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="fffa7-198">Het [script Block](./scriptblock-element-for-groupby-format.md) -element geeft het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="fffa7-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="fffa7-199">U moet een script of eigenschap opgeven om de groep te starten, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="fffa7-200">Het element [Label](./label-element-for-groupby-format.md) definieert een label dat aan het begin van elke groep wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="fffa7-201">Naast de tekst die door dit element is opgegeven, wordt in Windows Power shell de waarde weer gegeven die de nieuwe groep heeft geactiveerd en wordt een lege regel toegevoegd vóór en na het label.</span><span class="sxs-lookup"><span data-stu-id="fffa7-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="fffa7-202">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fffa7-202">This element is optional.</span></span>

- <span data-ttu-id="fffa7-203">Het [CustomControl](./customcontrol-element-for-groupby-format.md) -element definieert een besturings element dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="fffa7-204">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fffa7-204">This element is optional.</span></span>

- <span data-ttu-id="fffa7-205">Het [CustomControlName](./customcontrolname-element-for-groupby-format.md) -element geeft een algemeen of weergave besturings element op dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="fffa7-206">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fffa7-206">This element is optional.</span></span>

<span data-ttu-id="fffa7-207">Zie [Wide View (GroupBy)](./wide-view-groupby.md)voor een voor beeld van een volledig indelings bestand waarmee groepen worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="fffa7-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="fffa7-208">Opmaak teken reeksen gebruiken</span><span class="sxs-lookup"><span data-stu-id="fffa7-208">Using Format Strings</span></span>

<span data-ttu-id="fffa7-209">Opmaak teken reeksen kunnen worden toegevoegd aan een brede weer gave om te bepalen hoe de gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="fffa7-210">In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de eigenschap `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="fffa7-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="fffa7-211">De volgende XML-elementen kunnen worden gebruikt om een notatie patroon op te geven:</span><span class="sxs-lookup"><span data-stu-id="fffa7-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="fffa7-212">Het element [WideItem](./wideitem-element-for-widecontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="fffa7-213">Met het element [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="fffa7-214">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="fffa7-215">Het element [formats Tring](./formatstring-element-for-wideitem-for-widecontrol-format.md) geeft een opmaak patroon op dat bepaalt hoe de eigenschap of script waarde wordt weer gegeven in de weer gave</span><span class="sxs-lookup"><span data-stu-id="fffa7-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="fffa7-216">Het element [script Block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (niet weer gegeven) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="fffa7-217">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="fffa7-218">In het volgende voor beeld wordt de methode `ToString` aangeroepen om de waarde van het script op te maken.</span><span class="sxs-lookup"><span data-stu-id="fffa7-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="fffa7-219">Scripts kunnen een wille keurige methode van een object aanroepen.</span><span class="sxs-lookup"><span data-stu-id="fffa7-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="fffa7-220">Als een object een methode heeft, zoals `ToString`, die opmaak parameters heeft, kan het script deze methode ook aanroepen om de uitvoer waarde van het script op te maken.</span><span class="sxs-lookup"><span data-stu-id="fffa7-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="fffa7-221">Het volgende XML-element kan worden gebruikt om de `ToString` methode aan te roepen:</span><span class="sxs-lookup"><span data-stu-id="fffa7-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="fffa7-222">Het element [WideItem](./wideitem-element-for-widecontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="fffa7-223">Het element [script Block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (niet weer gegeven) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fffa7-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="fffa7-224">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="fffa7-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="fffa7-225">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fffa7-225">See Also</span></span>

[<span data-ttu-id="fffa7-226">Brede weer gave (basis)</span><span class="sxs-lookup"><span data-stu-id="fffa7-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="fffa7-227">Brede weer gave (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="fffa7-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="fffa7-228">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="fffa7-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
