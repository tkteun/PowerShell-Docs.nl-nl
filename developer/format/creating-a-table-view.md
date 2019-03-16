---
title: Het maken van een tabelweergave | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057362"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="bf680-102">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="bf680-102">Creating a Table View</span></span>

<span data-ttu-id="bf680-103">Gegevens weergegeven weergeven als een tabel in een of meer kolommen.</span><span class="sxs-lookup"><span data-stu-id="bf680-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="bf680-104">Elke rij in de tabel vertegenwoordigt een .NET-object en elke kolom in de tabel een eigenschap van het object of de Scriptwaarde van een.</span><span class="sxs-lookup"><span data-stu-id="bf680-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="bf680-105">Weergeven als een tabel die de eigenschappen van een object of een subset van de eigenschappen van een object wordt weergegeven, kunt u definiëren.</span><span class="sxs-lookup"><span data-stu-id="bf680-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="bf680-106">De weergave van een tabel</span><span class="sxs-lookup"><span data-stu-id="bf680-106">A Table View Display</span></span>

<span data-ttu-id="bf680-107">Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object dat wordt geretourneerd door de [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf680-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="bf680-108">Voor dit object is Windows PowerShell weergeven als een tabel die wordt gedefinieerd. de `Status` eigenschap, de `Name` eigenschap (deze eigenschap is een alias-eigenschap voor de `ServiceName` eigenschap), en de `DisplayName` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="bf680-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="bf680-109">Elke rij in de tabel vertegenwoordigt een object dat wordt geretourneerd door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf680-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="bf680-110">De tabelweergave definiëren</span><span class="sxs-lookup"><span data-stu-id="bf680-110">Defining the Table View</span></span>

<span data-ttu-id="bf680-111">Het volgende XML-bestand ziet u het tabelschema van de weergave voor het weergeven van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span><span class="sxs-lookup"><span data-stu-id="bf680-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="bf680-112">U moet elke eigenschap die u weergeven in de tabelweergave wilt.</span><span class="sxs-lookup"><span data-stu-id="bf680-112">You must specify each property that you want displayed in the table view.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="bf680-113">De volgende XML-elementen worden gebruikt voor het definiëren van een lijst weergeven:</span><span class="sxs-lookup"><span data-stu-id="bf680-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="bf680-114">De [weergave](./view-element-format.md) -element is het bovenliggende element van de tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="bf680-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="bf680-115">(Dit is hetzelfde bovenliggende element voor de lijst, breed en aangepaste weergaven.)</span><span class="sxs-lookup"><span data-stu-id="bf680-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="bf680-116">De [naam](./name-element-for-view-format.md) element Hiermee geeft u de naam van de weergave.</span><span class="sxs-lookup"><span data-stu-id="bf680-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="bf680-117">Dit element is vereist voor alle weergaven.</span><span class="sxs-lookup"><span data-stu-id="bf680-117">This element is required for all views.</span></span>

- <span data-ttu-id="bf680-118">De [ViewSelectedBy](./viewselectedby-element-format.md) element definieert de objecten die gebruikmaken van de weergave.</span><span class="sxs-lookup"><span data-stu-id="bf680-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="bf680-119">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="bf680-119">This element is required.</span></span>

- <span data-ttu-id="bf680-120">De [GroupBy](./groupby-element-for-view-format.md) element (niet weergegeven in dit voorbeeld) wordt gedefinieerd wanneer een nieuwe groep objecten wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="bf680-121">Een nieuwe groep wordt gestart wanneer de waarde van een bepaalde eigenschap of script wijzigt.</span><span class="sxs-lookup"><span data-stu-id="bf680-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="bf680-122">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="bf680-122">This element is optional.</span></span>

- <span data-ttu-id="bf680-123">De [besturingselementen](./controls-element-for-view-format.md) element (niet weergegeven in dit voorbeeld) definieert de aangepaste besturingselementen die zijn gedefinieerd door de tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="bf680-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="bf680-124">Besturingselementen kunnen u nader aangeven hoe de gegevens worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="bf680-125">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="bf680-125">This element is optional.</span></span> <span data-ttu-id="bf680-126">Een weergave een eigen aangepaste besturingselementen kunt definiëren of deze algemene besturingselementen die kunnen worden gebruikt door elke weergave in de opmaak-bestand kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bf680-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="bf680-127">Zie voor meer informatie over aangepaste besturingselementen [het maken van aangepaste besturingselementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="bf680-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="bf680-128">De [HideTableHeaders](./hidetableheaders-element-format.md) element (niet weergeven in dit voorbeeld) geeft aan dat de tabel niet in de labels die aan de bovenkant van de tabel weergegeven wordt.</span><span class="sxs-lookup"><span data-stu-id="bf680-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="bf680-129">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="bf680-129">This element is optional.</span></span>

- <span data-ttu-id="bf680-130">De [TableControl](./tablecontrol-element-format.md) element dat de kop- en gegevens van de tabel definieert.</span><span class="sxs-lookup"><span data-stu-id="bf680-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="bf680-131">Net als bij alle andere weergaven, een tabel weergave kan de waarden van eigenschappen van het object of de waarden die worden gegenereerd door scripts.</span><span class="sxs-lookup"><span data-stu-id="bf680-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="bf680-132">Kolomkoppen definiëren</span><span class="sxs-lookup"><span data-stu-id="bf680-132">Defining Column Headers</span></span>

1. <span data-ttu-id="bf680-133">De [TableHeaders](./tableheaders-element-format.md) -element en de onderliggende elementen definiëren wat wordt weergegeven aan de bovenkant van de tabel.</span><span class="sxs-lookup"><span data-stu-id="bf680-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="bf680-134">De [TableColumnHeader](./tablecolumnheader-element-format.md) element wordt gedefinieerd wat er aan de bovenkant van een kolom van de tabel wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="bf680-135">Geef deze elementen in de volgorde waarin u de headers weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="bf680-136">Er is geen limiet voor het aantal van deze element dat u kunt gebruiken, maar het aantal [TableColumnHeader](./tablecolumnheader-element-format.md) elementen in uw tabelweergave moeten gelijk zijn aan het aantal [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elementen die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bf680-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="bf680-137">De [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element Hiermee geeft u de tekst die wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="bf680-138">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="bf680-138">This element is optional.</span></span>

4. <span data-ttu-id="bf680-139">De [breedte](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element geeft de breedte (in tekens) van de kolom.</span><span class="sxs-lookup"><span data-stu-id="bf680-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="bf680-140">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="bf680-140">This element is optional.</span></span>

5. <span data-ttu-id="bf680-141">De [uitlijning](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element geeft aan hoe het label wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="bf680-142">Het label kan worden afgestemd op de links aan de rechterkant, of gecentreerd.</span><span class="sxs-lookup"><span data-stu-id="bf680-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="bf680-143">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="bf680-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="bf680-144">De tabelrijen definiëren</span><span class="sxs-lookup"><span data-stu-id="bf680-144">Defining the Table Rows</span></span>

<span data-ttu-id="bf680-145">Tabelweergaven krijgt u een of meer definities die welke gegevens worden weergegeven in de rijen van de tabel opgeeft met behulp van de onderliggende elementen van de [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf680-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="bf680-146">U ziet dat u kunt meerdere definities voor de rijen van de tabel opgeven, maar de headers voor de rijen blijft hetzelfde, ongeacht welke rijdefinitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bf680-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="bf680-147">Een tabel wordt meestal slechts één definitie bevatten.</span><span class="sxs-lookup"><span data-stu-id="bf680-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="bf680-148">In het volgende voorbeeld wordt de weergave bevat één definitie waarin de waarden van verschillende eigenschappen van de [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) object.</span><span class="sxs-lookup"><span data-stu-id="bf680-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="bf680-149">Weergeven als een tabel weergeven, de waarde van een eigenschap of de waarde van een script (niet weergegeven in het voorbeeld) in de rijen.</span><span class="sxs-lookup"><span data-stu-id="bf680-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

<span data-ttu-id="bf680-150">De volgende XML-elementen kunnen worden gebruikt voor definities voor een rij:</span><span class="sxs-lookup"><span data-stu-id="bf680-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="bf680-151">De [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) -element en de onderliggende elementen definiëren wat wordt weergegeven in de rijen van de tabel.</span><span class="sxs-lookup"><span data-stu-id="bf680-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="bf680-152">De [TableRowEntry](./listentry-element-for-listcontrol-format.md) -element bevat een definitie van de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="bf680-153">Ten minste één [TableRowEntry](./listentry-element-for-listcontrol-format.md) is vereist; er is echter geen maximale limiet voor het aantal elementen die u kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="bf680-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="bf680-154">In de meeste gevallen wordt een weergave slechts één definitie hebben.</span><span class="sxs-lookup"><span data-stu-id="bf680-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="bf680-155">De [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element Hiermee geeft u de objecten die worden weergegeven door de definitie van een specifieke.</span><span class="sxs-lookup"><span data-stu-id="bf680-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="bf680-156">Dit element is optioneel en is alleen nodig wanneer u meerdere definiëren [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementen die verschillende objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="bf680-157">De [verpakken](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element geeft aan dat de tekst die langer is dan de breedte van de kolom wordt weergegeven op de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="bf680-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="bf680-158">Standaard de tekst die langer is dan de breedte van legendakolom wordt afgekapt.</span><span class="sxs-lookup"><span data-stu-id="bf680-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="bf680-159">De [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element definieert de eigenschappen of scripts waarvan de waarden worden weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="bf680-160">De [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element wordt gedefinieerd voor de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="bf680-161">Een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is vereist voor elke kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="bf680-162">De eerste vermelding wordt weergegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="bf680-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="bf680-163">De [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="bf680-164">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="bf680-165">De [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element Hiermee geeft u het script waarvan de waarde wordt weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="bf680-166">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="bf680-167">De [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="bf680-168">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="bf680-168">This element is optional.</span></span>

- <span data-ttu-id="bf680-169">De [uitlijning](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element geeft aan hoe de waarde van de eigenschap of het script wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="bf680-170">De waarde kan worden afgestemd op de links aan de rechterkant, of gecentreerd.</span><span class="sxs-lookup"><span data-stu-id="bf680-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="bf680-171">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="bf680-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="bf680-172">De objecten die gebruikmaken van de tabelweergave definiëren</span><span class="sxs-lookup"><span data-stu-id="bf680-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="bf680-173">Er zijn twee manieren om te definiëren welke objecten .NET gebruiken de tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="bf680-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="bf680-174">U kunt de [ViewSelectedBy](./viewselectedby-element-format.md) element voor het definiëren van de objecten die kunnen worden weergegeven door de definities van de weergave, of u kunt de [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element te definiëren welke objecten worden weergegeven door een de definitie van de weergave van specifieke.</span><span class="sxs-lookup"><span data-stu-id="bf680-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="bf680-175">In de meeste gevallen een weergave heeft slechts één definitie zodat objecten worden gewoonlijk gedefinieerd door de [ViewSelectedBy](./viewselectedby-element-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf680-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="bf680-176">Het volgende voorbeeld ziet u hoe u de objecten die worden weergegeven door de tabel weergeven met behulp van de [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) elementen.</span><span class="sxs-lookup"><span data-stu-id="bf680-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="bf680-177">Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) elementen dat u opgeven kunt en de volgorde niet belangrijk is.</span><span class="sxs-lookup"><span data-stu-id="bf680-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="bf680-178">De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de tabelweergave:</span><span class="sxs-lookup"><span data-stu-id="bf680-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="bf680-179">De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="bf680-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="bf680-180">De [TypeName](./typename-element-for-viewselectedby-format.md) element Hiermee geeft u de .NET-object dat door de weergave wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="bf680-181">De volledig gekwalificeerde naam van de .NET-type is vereist.</span><span class="sxs-lookup"><span data-stu-id="bf680-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="bf680-182">U moet ten minste één type of de selectie instellen voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="bf680-183">Het volgende voorbeeld wordt de [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementen.</span><span class="sxs-lookup"><span data-stu-id="bf680-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="bf680-184">Gebruik selectie wordt ingesteld wanneer er een gerelateerde set van objecten die worden weergegeven met behulp van meerdere weergaven, zoals wanneer u een lijst weergeven en een tabelweergave voor dezelfde objecten definiëren.</span><span class="sxs-lookup"><span data-stu-id="bf680-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="bf680-185">Zie voor meer informatie over het maken van een selectieset [selectiesets definiëren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="bf680-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="bf680-186">De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de lijstweergave:</span><span class="sxs-lookup"><span data-stu-id="bf680-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="bf680-187">De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="bf680-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="bf680-188">De [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element Hiermee geeft u een set van objecten die kunnen worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="bf680-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="bf680-189">U moet ten minste één selectie instellen of type voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="bf680-190">Het volgende voorbeeld ziet u hoe u de objecten weergegeven door een specifieke definitie van de tabel weergeven met behulp van de [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf680-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="bf680-191">Met behulp van dit element, kunt u de .NET-typenaam van het object, een selectieset objecten of een selectievoorwaarde waarmee wordt aangegeven wanneer de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bf680-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="bf680-192">Zie voor meer informatie over het maken van een selectie voorwaarden [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bf680-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="bf680-193">Bij het maken van meerdere definities van de tabelweergave kunt u verschillende kolomkoppen niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="bf680-194">U kunt opgeven wat wordt alleen weergegeven in de rijen van de tabel, zoals welke objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="bf680-195">De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door een specifieke definitie van de lijstweergave:</span><span class="sxs-lookup"><span data-stu-id="bf680-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="bf680-196">De [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="bf680-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="bf680-197">De [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element Hiermee geeft u de .NET-object dat door de definitie wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="bf680-198">Wanneer u dit element gebruikt, is de volledig gekwalificeerde naam van de .NET-type is vereist.</span><span class="sxs-lookup"><span data-stu-id="bf680-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="bf680-199">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="bf680-200">De [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u een set van objecten die kunnen worden weergegeven door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="bf680-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="bf680-201">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="bf680-202">De [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u een voorwaarde moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bf680-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="bf680-203">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="bf680-204">Zie voor meer informatie over het definiëren van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bf680-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="bf680-205">Met behulp van opmaaktekenreeksen</span><span class="sxs-lookup"><span data-stu-id="bf680-205">Using Format Strings</span></span>

<span data-ttu-id="bf680-206">Opmaak tekenreeksen kunnen worden toegevoegd aan een weergave om verder te definiëren hoe de gegevens worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="bf680-207">Het volgende voorbeeld ziet u hoe u een opmaaktekenreeks voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="bf680-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="bf680-208">De volgende XML-elementen kunnen worden gebruikt om op te geven van een patroon indeling:</span><span class="sxs-lookup"><span data-stu-id="bf680-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="bf680-209">De [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element wordt gedefinieerd voor de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="bf680-210">Een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is vereist voor elke kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="bf680-211">De eerste vermelding wordt weergegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="bf680-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="bf680-212">De [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="bf680-213">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="bf680-214">De [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="bf680-215">In het volgende voorbeeld wordt de `ToString` methode aangeroepen om de indeling van de waarde van het script.</span><span class="sxs-lookup"><span data-stu-id="bf680-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="bf680-216">Scripts kunnen elke methode van een object aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="bf680-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="bf680-217">Dus als een object een methode, zoals heeft `ToString`, met parameters voor formatteren, het script dat methode voor de indeling van de uitvoerwaarde van het script kunt aanroepen.</span><span class="sxs-lookup"><span data-stu-id="bf680-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="bf680-218">De volgende XML-element kan worden gebruikt voor aanroepen de `ToString` methode:</span><span class="sxs-lookup"><span data-stu-id="bf680-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="bf680-219">De [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element wordt gedefinieerd voor de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="bf680-220">Een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is vereist voor elke kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="bf680-221">De eerste vermelding wordt weergegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="bf680-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="bf680-222">De [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element Hiermee geeft u het script waarvan de waarde wordt weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="bf680-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="bf680-223">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="bf680-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf680-224">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bf680-224">See Also</span></span>

[<span data-ttu-id="bf680-225">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf680-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
