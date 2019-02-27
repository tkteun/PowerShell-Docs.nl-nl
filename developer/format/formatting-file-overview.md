---
title: Opmaak-overzicht | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851917"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="91a7f-102">Overzicht voor opmaakbestanden</span><span class="sxs-lookup"><span data-stu-id="91a7f-102">Formatting File Overview</span></span>

<span data-ttu-id="91a7f-103">De notatie voor de objecten die worden geretourneerd door opdrachten (cmdlets, functies en scripts) worden gedefinieerd met behulp van opmaak-bestanden (format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="91a7f-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="91a7f-104">Aantal van deze bestanden worden geleverd door PowerShell voor het definiëren van de weergave-indeling voor die objecten geretourneerd door de opgegeven PowerShell opdrachten, zoals de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object dat wordt geretourneerd door de `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91a7f-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="91a7f-105">Echter, u kunt ook uw eigen aangepaste opmaak bestanden als u wilt overschrijven van de standaard weergave-indelingen maken of kunt u een aangepaste opmaak bestand voor het definiëren van de weergave van objecten die worden geretourneerd door uw eigen opdrachten.</span><span class="sxs-lookup"><span data-stu-id="91a7f-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="91a7f-106">Opmaak bestanden bepalen de elementen van een object die worden geretourneerd aan de pijplijn niet.</span><span class="sxs-lookup"><span data-stu-id="91a7f-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="91a7f-107">Wanneer een object wordt geretourneerd aan de pijplijn, zijn alle leden van dat object beschikbaar, zelfs als sommige worden niet weergegeven.</span><span class="sxs-lookup"><span data-stu-id="91a7f-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="91a7f-108">PowerShell maakt gebruik van de gegevens in deze opmaak bestanden om te bepalen wat wordt weergegeven en hoe de weergegeven gegevens zijn opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="91a7f-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="91a7f-109">De weergegeven gegevens kunnen de eigenschappen van een object of de waarde van een script bevatten.</span><span class="sxs-lookup"><span data-stu-id="91a7f-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="91a7f-110">Scripts worden gebruikt als u weergeven van een waarde die niet rechtstreeks vanuit de eigenschappen van een object wilt, zoals het toevoegen van de waarde van de twee eigenschappen van een object en klikt u vervolgens de som weer te geven als een onderdeel van de gegevens beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="91a7f-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="91a7f-111">Opmaak van de weergegeven gegevens wordt gedaan door het definiëren van weergaven voor de objecten die u wilt weergeven.</span><span class="sxs-lookup"><span data-stu-id="91a7f-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="91a7f-112">U kunt voor elk object één weergave definiëren, kunt u één weergave voor meerdere objecten of kunt u meerdere weergaven voor hetzelfde object.</span><span class="sxs-lookup"><span data-stu-id="91a7f-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="91a7f-113">Er is geen limiet voor het aantal weergaven die u kunt definiëren.</span><span class="sxs-lookup"><span data-stu-id="91a7f-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="91a7f-114">Algemene functies van opmaak bestanden</span><span class="sxs-lookup"><span data-stu-id="91a7f-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="91a7f-115">Elk bestand opmaak kunt de volgende onderdelen die kunnen worden gedeeld met alle weergaven die zijn gedefinieerd door het bestand definiëren:</span><span class="sxs-lookup"><span data-stu-id="91a7f-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="91a7f-116">Standaard configuratie-instelling, zoals of de gegevens die worden weergegeven in de rijen van tabellen worden weergegeven op de volgende regel als de gegevens langer dan de breedte van de kolom is.</span><span class="sxs-lookup"><span data-stu-id="91a7f-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="91a7f-117">Zie voor meer informatie over deze instellingen [algemene configuratie-instellingen definiëren](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="91a7f-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="91a7f-118">Sets van objecten die kunnen worden weergegeven door een van de weergaven van de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="91a7f-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="91a7f-119">Voor meer informatie over deze sets (aangeduid als *selectiesets*), Zie [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="91a7f-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="91a7f-120">Algemene besturingselementen die kunnen worden gebruikt door alle weergaven van de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="91a7f-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="91a7f-121">Besturingselementen kunnen u de mate van controle op hoe gegevens worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="91a7f-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="91a7f-122">Zie voor meer informatie over de besturingselementen [definiëren van aangepaste besturingselementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="91a7f-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="91a7f-123">Opmaak van weergaven</span><span class="sxs-lookup"><span data-stu-id="91a7f-123">Formatting Views</span></span>

<span data-ttu-id="91a7f-124">Opmaak weergaven kunnen objecten weergeven in een tabelindeling, lijstweergave, beeldschermen en aangepaste notatie.</span><span class="sxs-lookup"><span data-stu-id="91a7f-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="91a7f-125">Voor het overgrote deel wordt elke opmaak definitie beschreven door een set XML-labels die worden beschreven van de weergave.</span><span class="sxs-lookup"><span data-stu-id="91a7f-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="91a7f-126">Elke weergave bevat de naam van de weergave de objecten die gebruikmaken van de weergave en de elementen van de weergave, zoals de kolommen en rijen gegevens voor een tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="91a7f-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="91a7f-127">Tabel weergave bevat de eigenschappen van een object of een waarde voor het blokkeren van script in een of meer kolommen.</span><span class="sxs-lookup"><span data-stu-id="91a7f-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="91a7f-128">Elke kolom vertegenwoordigt een enkele eigenschap van het object of de Scriptwaarde van een.</span><span class="sxs-lookup"><span data-stu-id="91a7f-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="91a7f-129">U kunt weergeven als een tabel waarin de eigenschappen van een object, een subset van de eigenschappen van een object of een combinatie van eigenschappen en waarden van script definiëren.</span><span class="sxs-lookup"><span data-stu-id="91a7f-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="91a7f-130">Elke rij van de tabel vertegenwoordigt een geretourneerde object.</span><span class="sxs-lookup"><span data-stu-id="91a7f-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="91a7f-131">Het maken van de tabelweergave van een is heel vergelijkbaar met wanneer u een object doorgeven aan de `Format-Table` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91a7f-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="91a7f-132">Zie voor meer informatie over deze weergave [tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="91a7f-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="91a7f-133">Geef een lijst weergeven met de eigenschappen van een object of de Scriptwaarde van een in één kolom.</span><span class="sxs-lookup"><span data-stu-id="91a7f-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="91a7f-134">Elke rij van de lijst geeft een optionele label of de naam van de eigenschap gevolgd door de waarde van de eigenschap of het script.</span><span class="sxs-lookup"><span data-stu-id="91a7f-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="91a7f-135">Het maken van een lijst weergeven is heel vergelijkbaar met een object te sluizen de `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91a7f-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="91a7f-136">Zie voor meer informatie over deze weergave [lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="91a7f-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="91a7f-137">Brede weergave bevat één eigenschap van een object of de Scriptwaarde van een in een of meer kolommen.</span><span class="sxs-lookup"><span data-stu-id="91a7f-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="91a7f-138">Er is geen label of de header voor deze weergave.</span><span class="sxs-lookup"><span data-stu-id="91a7f-138">There is no label or header for this view.</span></span> <span data-ttu-id="91a7f-139">Het maken van een brede weergave is vergelijkbaar met een object te sluizen de `Format-Wide` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91a7f-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="91a7f-140">Zie voor meer informatie over deze weergave [brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="91a7f-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="91a7f-141">Aangepaste weergave bevat een aanpasbare weergave van eigenschappen van het object of script waarden die niet in overeenstemming is met de Star structuur van de tabelweergaven, lijstweergaven of breed weergaven.</span><span class="sxs-lookup"><span data-stu-id="91a7f-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="91a7f-142">U kunt een zelfstandige aangepaste weergave definiëren of kunt u een aangepaste weergave die wordt gebruikt door een andere weergave, zoals een tabel of lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="91a7f-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="91a7f-143">Het maken van een aangepaste weergave is vergelijkbaar met een object te sluizen de `Format-Custom` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91a7f-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="91a7f-144">Zie voor meer informatie over deze weergave [aangepaste weergave](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="91a7f-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="91a7f-145">Onderdelen van een weergave</span><span class="sxs-lookup"><span data-stu-id="91a7f-145">Components of a View</span></span>

<span data-ttu-id="91a7f-146">De volgende XML-voorbeelden ziet de basisonderdelen van de XML van een weergave.</span><span class="sxs-lookup"><span data-stu-id="91a7f-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="91a7f-147">De afzonderlijke XML-elementen variëren, afhankelijk van welke weergave die u wilt maken, maar de basisonderdelen van de weergaven zijn allemaal hetzelfde.</span><span class="sxs-lookup"><span data-stu-id="91a7f-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="91a7f-148">Te beginnen met elke weergave bevat een `Name` element dat Hiermee geeft u een beschrijvende naam die wordt gebruikt om te verwijzen naar de weergave.</span><span class="sxs-lookup"><span data-stu-id="91a7f-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="91a7f-149">een `ViewSelectedBy` element waarmee wordt gedefinieerd welke .NET-objecten worden weergegeven in de weergave en een *besturingselement* element dat de weergave wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="91a7f-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

<span data-ttu-id="91a7f-150">In het besturingselement-element, kunt u definiëren een of meer *vermelding* elementen.</span><span class="sxs-lookup"><span data-stu-id="91a7f-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="91a7f-151">Als u meerdere definities gebruikt, moet u opgeven welke .NET-objecten gebruiken elke definitie.</span><span class="sxs-lookup"><span data-stu-id="91a7f-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="91a7f-152">Meestal is slechts één vermelding, met slechts één definitie nodig voor elk besturingselement.</span><span class="sxs-lookup"><span data-stu-id="91a7f-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

<span data-ttu-id="91a7f-153">Binnen elk element van de vermelding van een weergave, geeft u de *item* elementen waarmee de .NET-eigenschappen of scripts die worden weergegeven in deze weergave wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="91a7f-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="91a7f-154">Zoals weergegeven in de voorgaande voorbeelden, de opmaak-bestand meerdere weergaven kan bevatten, een weergave kan meerdere definities bevatten en elke definitie van meerdere items kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="91a7f-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="91a7f-155">Voorbeeld van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="91a7f-155">Example of a Table View</span></span>

<span data-ttu-id="91a7f-156">Het volgende voorbeeld ziet de XML-labels die worden gebruikt voor het definiëren van weergeven als een tabel met twee kolommen.</span><span class="sxs-lookup"><span data-stu-id="91a7f-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="91a7f-157">De [ViewDefinitions](./viewdefinitions-element-format.md) element is de containerelement voor de weergaven die zijn gedefinieerd in het bestand met opmaak.</span><span class="sxs-lookup"><span data-stu-id="91a7f-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="91a7f-158">De [weergave](./view-element-format.md) element wordt gedefinieerd voor de specifieke tabel, lijst, breed of een aangepaste weergave.</span><span class="sxs-lookup"><span data-stu-id="91a7f-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="91a7f-159">Binnen elk [weergave](./view-element-format.md) -element de [naam](./name-element-for-view-format.md) element Hiermee geeft u de naam van de weergave de [ViewSelectedBy](./viewselectedby-element-format.md) element definieert de objecten die gebruikmaken van de weergave en de verschillende controle over de elementen (zoals de `TableControl` element in het volgende voorbeeld wordt weergegeven) het type van de weergave definiëren.</span><span class="sxs-lookup"><span data-stu-id="91a7f-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="91a7f-160">Zie ook</span><span class="sxs-lookup"><span data-stu-id="91a7f-160">See Also</span></span>

[<span data-ttu-id="91a7f-161">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="91a7f-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="91a7f-162">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="91a7f-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="91a7f-163">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="91a7f-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="91a7f-164">Het maken van aangepaste besturingselementen</span><span class="sxs-lookup"><span data-stu-id="91a7f-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="91a7f-165">Schrijven van een PowerShell-opmaak en typen bestand</span><span class="sxs-lookup"><span data-stu-id="91a7f-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
