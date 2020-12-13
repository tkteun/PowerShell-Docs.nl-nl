---
ms.date: 09/13/2016
ms.topic: reference
title: Een brede weergave maken
description: Een brede weergave maken
ms.openlocfilehash: 4230ef91a3612e962b2773b12e8016df6f760eae
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655611"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="3c3b5-103">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="3c3b5-103">Creating a Wide View</span></span>

<span data-ttu-id="3c3b5-104">In een brede weer gave wordt één waarde weer gegeven voor elk object dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-104">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="3c3b5-105">De weer gegeven waarde kan de waarde van een .NET-object eigenschap of de waarde van een script zijn.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-105">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="3c3b5-106">Standaard is er geen label of kop voor deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-106">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="3c3b5-107">Een brede weer gave</span><span class="sxs-lookup"><span data-stu-id="3c3b5-107">A Wide View Display</span></span>

<span data-ttu-id="3c3b5-108">In het volgende voor beeld ziet u hoe in Windows Power shell het [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -object wordt weer gegeven dat wordt geretourneerd door de cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) wanneer de uitvoer wordt gepiped naar de [indeling-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-108">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="3c3b5-109">(De cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourneert standaard een tabel weergave.) In dit voor beeld worden de twee kolommen gebruikt om de naam van het proces voor elk geretourneerd object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-109">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="3c3b5-110">De naam van de eigenschap van het object wordt niet weer gegeven, alleen de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-110">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="3c3b5-111">De brede weer gave definiëren</span><span class="sxs-lookup"><span data-stu-id="3c3b5-111">Defining the Wide View</span></span>

<span data-ttu-id="3c3b5-112">De volgende XML-code toont het breedste weergave schema voor het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="3c3b5-112">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="3c3b5-113">De volgende XML-elementen worden gebruikt voor het definiëren van een brede weer gave:</span><span class="sxs-lookup"><span data-stu-id="3c3b5-113">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="3c3b5-114">Het element [View](./view-element-format.md) is het bovenliggende element van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-114">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="3c3b5-115">(Dit is hetzelfde bovenliggende element voor de tabel-, lijst-en aangepaste besturings elementen.)</span><span class="sxs-lookup"><span data-stu-id="3c3b5-115">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="3c3b5-116">Het element [name](./name-element-for-view-format.md) specificeert de naam van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="3c3b5-117">Dit element is vereist voor alle weer gaven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-117">This element is required for all views.</span></span>

- <span data-ttu-id="3c3b5-118">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="3c3b5-119">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-119">This element is required.</span></span>

- <span data-ttu-id="3c3b5-120">Het element [GroupBy](./groupby-element-for-view-format.md) definieert wanneer een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-120">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="3c3b5-121">Er wordt een nieuwe groep gestart wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="3c3b5-122">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-122">This element is optional.</span></span>

- <span data-ttu-id="3c3b5-123">De elementen [Controls](./controls-element-for-view-format.md) definieert de aangepaste besturings elementen die worden gedefinieerd door de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-123">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="3c3b5-124">Met besturings elementen kunt u nader aangeven hoe de gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="3c3b5-125">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-125">This element is optional.</span></span> <span data-ttu-id="3c3b5-126">Een weer gave kan zijn eigen aangepaste besturings elementen definiëren, maar u kunt ook algemene besturings elementen gebruiken die kunnen worden gebruikt door elke weer gave in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="3c3b5-127">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over aangepaste besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="3c3b5-128">Het [WideControl](./widecontrol-element-format.md) -element en de onderliggende elementen bepalen wat er in de weer gave wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-128">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="3c3b5-129">In het voor gaande voor beeld is de weer gave ontworpen om de eigenschap [System. Diagnostics. process. Autoprocesnaam](/dotnet/api/System.Diagnostics.Process.ProcessName) weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-129">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="3c3b5-130">Zie [Wide View (Basic)](./wide-view-basic.md)voor een voor beeld van een compleet opmaak bestand dat een eenvoudige, brede weer gave definieert.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-130">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="3c3b5-131">Definities opgeven voor de brede weer gave</span><span class="sxs-lookup"><span data-stu-id="3c3b5-131">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="3c3b5-132">Breedbeeld weergaven kunnen een of meer definities bieden met behulp van de onderliggende elementen van het element [WideControl](./widecontrol-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="3c3b5-132">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="3c3b5-133">Normaal gesp roken bevat een weer gave slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-133">Typically, a view will have only one definition.</span></span> <span data-ttu-id="3c3b5-134">In het volgende voor beeld bevat de weer gave één definitie waarmee de waarde van de eigenschap [System. Diagnostics. process. Autoprocesnaam](/dotnet/api/System.Diagnostics.Process.ProcessName) wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-134">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="3c3b5-135">Een brede weer gave kan de waarde van een eigenschap of de waarde van een script weer geven (niet weer gegeven in het voor beeld).</span><span class="sxs-lookup"><span data-stu-id="3c3b5-135">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="3c3b5-136">De volgende XML-elementen kunnen worden gebruikt om definities te bieden voor een brede weer gave:</span><span class="sxs-lookup"><span data-stu-id="3c3b5-136">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="3c3b5-137">Het [WideControl](./widecontrol-element-format.md) -element en de onderliggende elementen bepalen wat er in de weer gave wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-137">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="3c3b5-138">Het element [AutoSize](./autosize-element-for-widecontrol-format.md) geeft aan of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-138">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="3c3b5-139">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-139">This element is optional.</span></span>

- <span data-ttu-id="3c3b5-140">Het [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) -element geeft het aantal kolommen op dat wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-140">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="3c3b5-141">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-141">This element is optional.</span></span>

- <span data-ttu-id="3c3b5-142">Het [WideEntries](./wideentries-element-for-widecontrol-format.md) -element bevat de definities van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-142">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="3c3b5-143">In de meeste gevallen heeft een weer gave slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-143">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="3c3b5-144">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-144">This element is required.</span></span>

- <span data-ttu-id="3c3b5-145">Het [WideEntry](./wideentry-element-for-widecontrol-format.md) -element bevat een definitie van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-145">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="3c3b5-146">Er is ten minste één [WideEntry](./wideentry-element-for-widecontrol-format.md) vereist. Er is echter geen maximum limiet voor het aantal elementen dat u kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-146">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="3c3b5-147">In de meeste gevallen heeft een weer gave slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-147">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="3c3b5-148">Het [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -element geeft de objecten aan die door een specifieke definitie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-148">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="3c3b5-149">Dit element is optioneel en is alleen nodig wanneer u meerdere [WideEntry](./wideentry-element-for-widecontrol-format.md) -elementen definieert waarin verschillende objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-149">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="3c3b5-150">Het element [WideItem](./wideitem-element-for-widecontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-150">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="3c3b5-151">In tegens telling tot andere soorten weer gaven, kan een breed besturings element slechts één item weer geven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-151">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="3c3b5-152">Met het element [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-152">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="3c3b5-153">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-153">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="3c3b5-154">Het [script Block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -element geeft het script op waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-154">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="3c3b5-155">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-155">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="3c3b5-156">Het element [formats Tring](./formatstring-element-for-wideitem-for-widecontrol-format.md) geeft een patroon op dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-156">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="3c3b5-157">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-157">This element is optional.</span></span>

<span data-ttu-id="3c3b5-158">Zie [Wide View (Basic)](./wide-view-basic.md)voor een voor beeld van een volledige indelings bestand waarin een brede weergave definitie is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-158">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="3c3b5-159">De objecten definiëren die gebruikmaken van de brede weer gave</span><span class="sxs-lookup"><span data-stu-id="3c3b5-159">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="3c3b5-160">Er zijn twee manieren om te definiëren welke .NET-objecten gebruikmaken van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-160">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="3c3b5-161">U kunt het element [ViewSelectedBy](./viewselectedby-element-format.md) gebruiken om de objecten te definiëren die door alle definities van de weer gave kunnen worden weer gegeven, of u kunt het element [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) gebruiken om te definiëren welke objecten worden weer gegeven met een specifieke definitie van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-161">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="3c3b5-162">In de meeste gevallen heeft een weer gave slechts één definitie, waardoor objecten doorgaans worden gedefinieerd door het element [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="3c3b5-162">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="3c3b5-163">In het volgende voor beeld ziet u hoe u de objecten definieert die door de brede weer gave worden weer gegeven met behulp van de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="3c3b5-163">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="3c3b5-164">Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) -elementen dat u kunt opgeven en de volg orde hiervan is niet belang rijk.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-164">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="3c3b5-165">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de brede weer gave:</span><span class="sxs-lookup"><span data-stu-id="3c3b5-165">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="3c3b5-166">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven door de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-166">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="3c3b5-167">Het element [TypeName](./typename-element-for-viewselectedby-format.md) specificeert de .net die wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-167">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="3c3b5-168">De volledig gekwalificeerde .NET-type naam is vereist.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-168">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="3c3b5-169">U moet ten minste één type of selectieset voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-169">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="3c3b5-170">Zie [Wide View (Basic)](./wide-view-basic.md)voor een voor beeld van een volledig indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-170">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="3c3b5-171">In het volgende voor beeld worden de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-171">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="3c3b5-172">Gebruik selectie sets waar u een gerelateerde set objecten hebt die met meerdere weer gaven worden weer gegeven, zoals wanneer u een brede weer gave en een tabel weergave voor dezelfde objecten definieert.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-172">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="3c3b5-173">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken van een selectie reeks.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-173">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="3c3b5-174">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de brede weer gave:</span><span class="sxs-lookup"><span data-stu-id="3c3b5-174">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="3c3b5-175">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven door de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-175">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="3c3b5-176">Het [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -element geeft een set objecten op die door de weer gave kan worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-176">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="3c3b5-177">U moet ten minste één selectieset of type voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-177">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="3c3b5-178">In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven met een specifieke definitie van de brede weer gave met behulp van het element [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) .</span><span class="sxs-lookup"><span data-stu-id="3c3b5-178">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="3c3b5-179">Met dit element kunt u de .NET-type naam van het object, een selectieset van objecten of een selectie voorwaarde opgeven die opgeeft wanneer de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-179">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="3c3b5-180">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het maken van een selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-180">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="3c3b5-181">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door een specifieke definitie van de brede weer gave:</span><span class="sxs-lookup"><span data-stu-id="3c3b5-181">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="3c3b5-182">Het [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -element definieert welke objecten worden weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-182">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="3c3b5-183">Het element [TypeName](./typename-element-for-viewselectedby-format.md) specificeert de .net die wordt weer gegeven in de definitie.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-183">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="3c3b5-184">Wanneer u dit element gebruikt, is de volledig gekwalificeerde .NET-type naam vereist.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-184">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="3c3b5-185">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-185">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="3c3b5-186">Het [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -element (niet weer gegeven) bevat een set objecten die kunnen worden weer gegeven door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-186">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="3c3b5-187">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-187">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="3c3b5-188">Het element [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (niet weer gegeven) bevat een voor waarde die voor deze definitie moet bestaan.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-188">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="3c3b5-189">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-189">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="3c3b5-190">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-190">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="3c3b5-191">Groepen objecten weer geven in een brede weer gave</span><span class="sxs-lookup"><span data-stu-id="3c3b5-191">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="3c3b5-192">U kunt de objecten die worden weer gegeven door de brede weer gave, scheiden in groepen.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-192">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="3c3b5-193">Dit betekent niet dat u een groep definieert, alleen dat Windows Power shell een nieuwe groep start wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-193">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="3c3b5-194">In het volgende voor beeld wordt een nieuwe groep gestart wanneer de waarde van de eigenschap [System. ServiceProcess. servicecontroller. service](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) type wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-194">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="3c3b5-195">De volgende XML-elementen worden gebruikt om te definiëren wanneer een groep wordt gestart:</span><span class="sxs-lookup"><span data-stu-id="3c3b5-195">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="3c3b5-196">Het element [GroupBy](./groupby-element-for-view-format.md) definieert de eigenschap of het script waarmee de nieuwe groep wordt gestart en definieert hoe de groep wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-196">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="3c3b5-197">Met het element [PropertyName](./propertyname-element-for-groupby-format.md) wordt de eigenschap opgegeven waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-197">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="3c3b5-198">U moet een eigenschap of script opgeven om de groep te starten, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-198">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="3c3b5-199">Het [script Block](./scriptblock-element-for-groupby-format.md) -element geeft het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-199">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="3c3b5-200">U moet een script of eigenschap opgeven om de groep te starten, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-200">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="3c3b5-201">Het element [Label](./label-element-for-groupby-format.md) definieert een label dat aan het begin van elke groep wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-201">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="3c3b5-202">Naast de tekst die door dit element is opgegeven, wordt in Windows Power shell de waarde weer gegeven die de nieuwe groep heeft geactiveerd en wordt een lege regel toegevoegd vóór en na het label.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-202">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="3c3b5-203">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-203">This element is optional.</span></span>

- <span data-ttu-id="3c3b5-204">Het [CustomControl](./customcontrol-element-for-groupby-format.md) -element definieert een besturings element dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-204">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="3c3b5-205">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-205">This element is optional.</span></span>

- <span data-ttu-id="3c3b5-206">Het [CustomControlName](./customcontrolname-element-for-groupby-format.md) -element geeft een algemeen of weergave besturings element op dat wordt gebruikt om de gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-206">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="3c3b5-207">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-207">This element is optional.</span></span>

<span data-ttu-id="3c3b5-208">Zie [Wide View (GroupBy)](./wide-view-groupby.md)voor een voor beeld van een volledig indelings bestand waarmee groepen worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-208">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="3c3b5-209">Opmaak teken reeksen gebruiken</span><span class="sxs-lookup"><span data-stu-id="3c3b5-209">Using Format Strings</span></span>

<span data-ttu-id="3c3b5-210">Opmaak teken reeksen kunnen worden toegevoegd aan een brede weer gave om te bepalen hoe de gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-210">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="3c3b5-211">In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-211">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="3c3b5-212">De volgende XML-elementen kunnen worden gebruikt om een notatie patroon op te geven:</span><span class="sxs-lookup"><span data-stu-id="3c3b5-212">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="3c3b5-213">Het element [WideItem](./wideitem-element-for-widecontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-213">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="3c3b5-214">Met het element [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-214">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="3c3b5-215">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-215">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="3c3b5-216">Het element [formats Tring](./formatstring-element-for-wideitem-for-widecontrol-format.md) geeft een opmaak patroon op dat bepaalt hoe de eigenschap of script waarde wordt weer gegeven in de weer gave</span><span class="sxs-lookup"><span data-stu-id="3c3b5-216">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="3c3b5-217">Het element [script Block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (niet weer gegeven) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-217">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="3c3b5-218">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-218">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="3c3b5-219">In het volgende voor beeld wordt de- `ToString` methode aangeroepen om de waarde van het script op te maken.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-219">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="3c3b5-220">Scripts kunnen een wille keurige methode van een object aanroepen.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-220">Scripts can call any method of an object.</span></span> <span data-ttu-id="3c3b5-221">Als een object een methode heeft, zoals `ToString` die opmaak parameters heeft, kan het script deze methode ook aanroepen om de uitvoer waarde van het script op te maken.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-221">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="3c3b5-222">Het volgende XML-element kan worden gebruikt om de methode aan te roepen `ToString` :</span><span class="sxs-lookup"><span data-stu-id="3c3b5-222">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="3c3b5-223">Het element [WideItem](./wideitem-element-for-widecontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-223">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="3c3b5-224">Het element [script Block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (niet weer gegeven) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-224">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="3c3b5-225">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3c3b5-225">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c3b5-226">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3c3b5-226">See Also</span></span>

[<span data-ttu-id="3c3b5-227">Brede weergave (Basis)</span><span class="sxs-lookup"><span data-stu-id="3c3b5-227">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="3c3b5-228">Brede weergave (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="3c3b5-228">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="3c3b5-229">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="3c3b5-229">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
