---
ms.date: 09/13/2016
ms.topic: reference
title: Overzicht voor opmaakbestanden
description: Overzicht voor opmaakbestanden
ms.openlocfilehash: 769a86d274ef3b35a322d76e2f03cb551d9204a1
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879133"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="4374a-103">Overzicht voor opmaakbestanden</span><span class="sxs-lookup"><span data-stu-id="4374a-103">Formatting File Overview</span></span>

<span data-ttu-id="4374a-104">De weer gave-indeling voor de objecten die worden geretourneerd door de opdrachten (cmdlets, functies en scripts) worden gedefinieerd met behulp van indelings bestanden (format.ps1XML-bestanden).</span><span class="sxs-lookup"><span data-stu-id="4374a-104">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="4374a-105">Verschillende van deze bestanden worden geleverd door Power shell om de weergave notatie te definiëren voor objecten die worden geretourneerd door Power shell-opdrachten, zoals het [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -object dat door de cmdlet wordt geretourneerd `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="4374a-105">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="4374a-106">U kunt echter ook uw eigen aangepaste opmaak bestanden maken om de standaard notaties te overschrijven of u kunt een aangepast opmaak bestand schrijven om de weer gave van objecten te definiëren die door uw eigen opdrachten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4374a-106">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4374a-107">Indelings bestanden bepalen niet welke elementen van een object worden geretourneerd naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="4374a-107">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="4374a-108">Wanneer een object wordt geretourneerd naar de pijp lijn, zijn alle leden van dat object beschikbaar, zelfs als sommige niet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4374a-108">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="4374a-109">Power shell gebruikt de gegevens in deze indelings bestanden om te bepalen wat wordt weer gegeven en hoe de weer gegeven gegevens worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="4374a-109">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="4374a-110">De weer gegeven gegevens kunnen de eigenschappen van een object of de waarde van een script bevatten.</span><span class="sxs-lookup"><span data-stu-id="4374a-110">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="4374a-111">Scripts worden gebruikt als u een bepaalde waarde wilt weer geven die niet rechtstreeks beschikbaar is vanuit de eigenschappen van een object, zoals het toevoegen van de waarde van twee eigenschappen van een object en de som als een stukje gegevens wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4374a-111">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="4374a-112">De indeling van de weer gegeven gegevens wordt uitgevoerd door weer gaven te definiëren voor de objecten die u wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="4374a-112">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="4374a-113">U kunt één weer gave definiëren voor elk object, u kunt één weer gave voor meerdere objecten definiëren, maar u kunt ook meerdere weer gaven definiëren voor hetzelfde object.</span><span class="sxs-lookup"><span data-stu-id="4374a-113">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="4374a-114">Er is geen limiet voor het aantal weer gaven dat u kunt definiëren.</span><span class="sxs-lookup"><span data-stu-id="4374a-114">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="4374a-115">Algemene functies van het format teren van bestanden</span><span class="sxs-lookup"><span data-stu-id="4374a-115">Common Features of Formatting Files</span></span>

<span data-ttu-id="4374a-116">Elk opmaak bestand kan de volgende onderdelen definiëren die kunnen worden gedeeld in alle weer gaven die door het bestand worden gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="4374a-116">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="4374a-117">De standaard configuratie-instelling, zoals of de gegevens in de rijen met tabellen worden weer gegeven op de volgende regel als de gegevens langer zijn dan de breedte van de kolom.</span><span class="sxs-lookup"><span data-stu-id="4374a-117">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="4374a-118">Zie [algemene configuratie-instellingen definiëren](./defining-common-configuration-features.md)voor meer informatie over deze instellingen.</span><span class="sxs-lookup"><span data-stu-id="4374a-118">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="4374a-119">Sets van objecten die kunnen worden weer gegeven in een van de weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="4374a-119">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="4374a-120">Zie [sets met objecten definiëren](./defining-selection-sets.md)voor meer informatie over deze sets (ook wel *selectie sets* genoemd).</span><span class="sxs-lookup"><span data-stu-id="4374a-120">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="4374a-121">Algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="4374a-121">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="4374a-122">Met besturings elementen krijgt u meer controle over de manier waarop gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4374a-122">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="4374a-123">Zie [aangepaste besturings elementen definiëren](./creating-custom-controls.md)voor meer informatie over besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="4374a-123">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="4374a-124">Opmaak weergaven</span><span class="sxs-lookup"><span data-stu-id="4374a-124">Formatting Views</span></span>

<span data-ttu-id="4374a-125">In opmaak weergaven kunnen objecten worden weer gegeven in een tabel indeling, lijst opmaak, brede notatie en aangepaste notatie.</span><span class="sxs-lookup"><span data-stu-id="4374a-125">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="4374a-126">Voor de meeste delen wordt elke opmaak definitie beschreven met een set XML-tags die de weer gave beschrijven.</span><span class="sxs-lookup"><span data-stu-id="4374a-126">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="4374a-127">Elke weer gave bevat de naam van de weer gave, de objecten die gebruikmaken van de weer gave en de elementen van de weer gave, zoals de kolom-en rij-informatie voor een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="4374a-127">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="4374a-128">In de tabel weergave worden de eigenschappen van een object of een script blok waarde in een of meer kolommen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4374a-128">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="4374a-129">Elke kolom vertegenwoordigt één eigenschap van het object of een script waarde.</span><span class="sxs-lookup"><span data-stu-id="4374a-129">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="4374a-130">U kunt een tabel weergave definiëren waarin alle eigenschappen van een object, een subset van de eigenschappen van een object of een combi natie van eigenschappen en script waarden worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4374a-130">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="4374a-131">Elke rij van de tabel vertegenwoordigt een geretourneerd object.</span><span class="sxs-lookup"><span data-stu-id="4374a-131">Each row of the table represents a returned object.</span></span> <span data-ttu-id="4374a-132">Het maken van een tabel weergave lijkt sterk op wanneer u een object naar de `Format-Table` cmdlet pipet.</span><span class="sxs-lookup"><span data-stu-id="4374a-132">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="4374a-133">Zie [tabel weergave](./creating-a-table-view.md)voor meer informatie over deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="4374a-133">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="4374a-134">In de lijst weergave worden de eigenschappen van een object of een script waarde in één kolom weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4374a-134">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="4374a-135">Elke rij van de lijst bevat een optioneel label of de naam van de eigenschap gevolgd door de waarde van de eigenschap of het script.</span><span class="sxs-lookup"><span data-stu-id="4374a-135">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="4374a-136">Het maken van een lijst weergave lijkt sterk op het sluizen van een object naar de `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4374a-136">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="4374a-137">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="4374a-137">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="4374a-138">Breedbeeld weergave bevat een enkele eigenschap van een object of een script waarde in een of meer kolommen.</span><span class="sxs-lookup"><span data-stu-id="4374a-138">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="4374a-139">Er is geen label of koptekst voor deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="4374a-139">There is no label or header for this view.</span></span> <span data-ttu-id="4374a-140">Het maken van een brede weer gave lijkt sterk op het sluizen van een object naar de `Format-Wide` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4374a-140">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="4374a-141">Zie [brede weer](./creating-a-wide-view.md)gave voor meer informatie over deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="4374a-141">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="4374a-142">In de aangepaste weer gave wordt een aanpas bare weer gave weer gegeven van object eigenschappen of script waarden die niet voldoen aan de stijve structuur van tabel weergaven, lijst weergaven of brede weer gaven.</span><span class="sxs-lookup"><span data-stu-id="4374a-142">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="4374a-143">U kunt een zelfstandige aangepaste weer gave definiëren, maar u kunt ook een aangepaste weer gave definiëren die wordt gebruikt door een andere weer gave, zoals een tabel weergave of lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="4374a-143">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="4374a-144">Het maken van een aangepaste weer gave lijkt sterk op het sluizen van een object naar de `Format-Custom` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4374a-144">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="4374a-145">Zie [aangepaste weer gave](./creating-custom-controls.md)voor meer informatie over deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="4374a-145">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="4374a-146">Onderdelen van een weer gave</span><span class="sxs-lookup"><span data-stu-id="4374a-146">Components of a View</span></span>

<span data-ttu-id="4374a-147">In de volgende XML-voor beelden ziet u de algemene XML-onderdelen van een weer gave.</span><span class="sxs-lookup"><span data-stu-id="4374a-147">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="4374a-148">De afzonderlijke XML-elementen variëren, afhankelijk van de weer gave die u wilt maken, maar de basis onderdelen van de weer gaven zijn allemaal hetzelfde.</span><span class="sxs-lookup"><span data-stu-id="4374a-148">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="4374a-149">Elke weer gave heeft een `Name` element dat een gebruiks vriendelijke naam specificeert die wordt gebruikt om te verwijzen naar de weer gave om te beginnen met.</span><span class="sxs-lookup"><span data-stu-id="4374a-149">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="4374a-150">een `ViewSelectedBy` element dat definieert welke .net-objecten worden weer gegeven in de weer gave en een *Control* -element waarmee de weer gave wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="4374a-150">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

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

<span data-ttu-id="4374a-151">Binnen het element Control kunt u een of meer *invoer* elementen definiëren.</span><span class="sxs-lookup"><span data-stu-id="4374a-151">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="4374a-152">Als u meerdere definities gebruikt, moet u opgeven welke .NET-objecten elke definitie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4374a-152">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="4374a-153">Normaal gesp roken is slechts één vermelding, met slechts één definitie, nodig voor elk besturings element.</span><span class="sxs-lookup"><span data-stu-id="4374a-153">Typically only one entry, with only one definition, is needed for each control.</span></span>

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

<span data-ttu-id="4374a-154">Binnen elk item element van een weer gave geeft u de *element* elementen op waarmee de .net-eigenschappen of-scripts worden gedefinieerd die door die weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4374a-154">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="4374a-155">Zoals in de voor gaande voor beelden wordt weer gegeven, kan het opmaak bestand meerdere weer gaven bevatten, een weer gave meerdere definities kan bevatten en elke definitie meerdere items kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="4374a-155">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="4374a-156">Voor beeld van een tabel weergave</span><span class="sxs-lookup"><span data-stu-id="4374a-156">Example of a Table View</span></span>

<span data-ttu-id="4374a-157">In het volgende voor beeld ziet u de XML-labels die worden gebruikt voor het definiëren van een tabel weergave die twee kolommen bevat.</span><span class="sxs-lookup"><span data-stu-id="4374a-157">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="4374a-158">Het element [ViewDefinitions](./viewdefinitions-element-format.md) is het container element voor alle weer gaven die in het opmaak bestand zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="4374a-158">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="4374a-159">Het element [weer gave](./view-element-format.md) definieert de specifieke tabel, lijst, brede of aangepaste weer gave.</span><span class="sxs-lookup"><span data-stu-id="4374a-159">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="4374a-160">In elk [weer gave](./view-element-format.md) -element geeft het element [name](./name-element-for-view-format.md) de naam van de weer gave, het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave en de verschillende elementen van het besturings element (zoals het `TableControl` element dat in het volgende voor beeld wordt weer gegeven) definiëren het type weer gave.</span><span class="sxs-lookup"><span data-stu-id="4374a-160">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

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
    </TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="4374a-161">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4374a-161">See Also</span></span>

[<span data-ttu-id="4374a-162">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="4374a-162">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4374a-163">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="4374a-163">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4374a-164">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="4374a-164">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4374a-165">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="4374a-165">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="4374a-166">Een Power shell-indeling en-typen bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="4374a-166">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
