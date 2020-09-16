---
title: Een tabel weergave maken | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: cbe81962a0f68d64506062898a8f21a1596cc29a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786149"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="3b6e3-102">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="3b6e3-102">Creating a Table View</span></span>

<span data-ttu-id="3b6e3-103">In een tabel weergave worden gegevens in een of meer kolommen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="3b6e3-104">Elke rij in de tabel vertegenwoordigt een .NET-object en elke kolom van de tabel vertegenwoordigt een eigenschap van het object of een script waarde.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="3b6e3-105">U kunt een tabel weergave definiëren waarin alle eigenschappen van een object of een subset van de eigenschappen van een object worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="3b6e3-106">Een tabel weergave weer geven</span><span class="sxs-lookup"><span data-stu-id="3b6e3-106">A Table View Display</span></span>

<span data-ttu-id="3b6e3-107">In het volgende voor beeld ziet u hoe in Windows Power shell het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) wordt weer gegeven dat wordt geretourneerd door de cmdlet [Get-service](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="3b6e3-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="3b6e3-108">Voor dit object heeft Windows Power shell een tabel weergave gedefinieerd waarin de eigenschap wordt weer gegeven `Status` , de `Name` eigenschap (deze eigenschap is een alias eigenschap voor de `ServiceName` eigenschap) en de `DisplayName` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="3b6e3-109">Elke rij in de tabel vertegenwoordigt een object dat door de cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="3b6e3-110">De tabel weergave definiëren</span><span class="sxs-lookup"><span data-stu-id="3b6e3-110">Defining the Table View</span></span>

<span data-ttu-id="3b6e3-111">In het volgende XML-bestand wordt het tabel weergave schema weer gegeven voor het weer geven van [System. ServiceProcess. servicecontroller? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -object.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="3b6e3-112">U moet elke eigenschap opgeven die u wilt weer geven in de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="3b6e3-113">De volgende XML-elementen worden gebruikt voor het definiëren van een lijst weergave:</span><span class="sxs-lookup"><span data-stu-id="3b6e3-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="3b6e3-114">Het element [View](./view-element-format.md) is het bovenliggende element van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="3b6e3-115">(Dit is hetzelfde bovenliggende element voor de lijst weergave, brede en aangepaste besturings elementen.)</span><span class="sxs-lookup"><span data-stu-id="3b6e3-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="3b6e3-116">Het element [name](./name-element-for-view-format.md) specificeert de naam van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="3b6e3-117">Dit element is vereist voor alle weer gaven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-117">This element is required for all views.</span></span>

- <span data-ttu-id="3b6e3-118">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="3b6e3-119">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-119">This element is required.</span></span>

- <span data-ttu-id="3b6e3-120">Het element [GroupBy](./groupby-element-for-view-format.md) (niet weer gegeven in dit voor beeld) definieert wanneer een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="3b6e3-121">Er wordt een nieuwe groep gestart wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="3b6e3-122">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-122">This element is optional.</span></span>

- <span data-ttu-id="3b6e3-123">Het element [Controls](./controls-element-for-view-format.md) (in dit voor beeld wordt niet weer gegeven) definieert de aangepaste besturings elementen die door de tabel weergave worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="3b6e3-124">Met besturings elementen kunt u nader aangeven hoe de gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="3b6e3-125">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-125">This element is optional.</span></span> <span data-ttu-id="3b6e3-126">Een weer gave kan zijn eigen aangepaste besturings elementen definiëren, maar u kunt ook algemene besturings elementen gebruiken die kunnen worden gebruikt door elke weer gave in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="3b6e3-127">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over aangepaste besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="3b6e3-128">Het [HideTableHeaders](./hidetableheaders-element-format.md) -element (niet weer gegeven in dit voor beeld) geeft aan dat er geen labels worden weer gegeven boven aan de tabel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="3b6e3-129">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-129">This element is optional.</span></span>

- <span data-ttu-id="3b6e3-130">Het [TableControl](./tablecontrol-element-format.md) -element waarmee de koptekst en de rij-informatie van de tabel worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="3b6e3-131">Net als bij alle andere weer gaven kunnen in een tabel weergave de waarden van object eigenschappen of waarden worden weer gegeven die door scripts worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="3b6e3-132">Kolom koppen definiëren</span><span class="sxs-lookup"><span data-stu-id="3b6e3-132">Defining Column Headers</span></span>

1. <span data-ttu-id="3b6e3-133">Het [TableHeaders](./tableheaders-element-format.md) -element en de onderliggende elementen bepalen wat er boven aan de tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="3b6e3-134">Het element [TableColumnHeader](./tablecolumnheader-element-format.md) definieert wat wordt weer gegeven aan de bovenkant van een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="3b6e3-135">Geef deze elementen op in de volg orde waarin de kopteksten moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="3b6e3-136">Er is geen limiet voor het aantal van dit element dat u kunt gebruiken, maar het aantal [TableColumnHeader](./tablecolumnheader-element-format.md) -elementen in de tabel weergave moet gelijk zijn aan het aantal [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) -elementen dat u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="3b6e3-137">Het element [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) geeft de tekst aan die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="3b6e3-138">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-138">This element is optional.</span></span>

4. <span data-ttu-id="3b6e3-139">Met het element [width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) wordt de breedte (in tekens) van de kolom opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="3b6e3-140">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-140">This element is optional.</span></span>

5. <span data-ttu-id="3b6e3-141">Het element [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) geeft aan hoe het label wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="3b6e3-142">Het label kan aan de linkerkant, rechts of gecentreerd worden uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="3b6e3-143">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="3b6e3-144">De tabel rijen definiëren</span><span class="sxs-lookup"><span data-stu-id="3b6e3-144">Defining the Table Rows</span></span>

<span data-ttu-id="3b6e3-145">Tabel weergaven kunnen een of meer definities bieden die aangeven welke gegevens in de rijen van de tabel worden weer gegeven door de onderliggende elementen van het element [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="3b6e3-146">U kunt meerdere definities opgeven voor de rijen van de tabel, maar de kopteksten van de rijen blijven hetzelfde, ongeacht de rijdefinitie die wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="3b6e3-147">Normaal gesp roken bevat een tabel slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="3b6e3-148">In het volgende voor beeld bevat de weer gave één definitie waarmee de waarden van verschillende eigenschappen van het [System. Diagnostics. process worden weer gegeven? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -object.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="3b6e3-149">Een tabel weergave kan de waarde van een eigenschap of de waarde van een script (niet weer gegeven in het voor beeld) weer geven in de rijen.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="3b6e3-150">De volgende XML-elementen kunnen worden gebruikt om definities voor een rij op te geven:</span><span class="sxs-lookup"><span data-stu-id="3b6e3-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="3b6e3-151">Het element [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) en de onderliggende elementen bepalen wat wordt weer gegeven in de rijen van de tabel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="3b6e3-152">Het [TableRowEntry](./listentry-element-for-listcontrol-format.md) -element bevat een definitie van de rij.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="3b6e3-153">Er is ten minste één [TableRowEntry](./listentry-element-for-listcontrol-format.md) vereist. Er is echter geen maximum limiet voor het aantal elementen dat u kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="3b6e3-154">In de meeste gevallen heeft een weer gave slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="3b6e3-155">Het [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -element geeft de objecten aan die door een specifieke definitie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="3b6e3-156">Dit element is optioneel en is alleen nodig wanneer u meerdere [TableRowEntry](./listentry-element-for-listcontrol-format.md) -elementen definieert waarin verschillende objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="3b6e3-157">Met het [Terugloop](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element wordt aangegeven dat de tekst die de kolom breedte overschrijdt wordt weer gegeven op de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="3b6e3-158">Standaard wordt tekst die de kolom breedte overschrijdt, afgekapt.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="3b6e3-159">Het [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) -element definieert de eigenschappen of scripts waarvan de waarden in de rij worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="3b6e3-160">Het [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="3b6e3-161">Voor elke kolom van de rij is een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element vereist.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="3b6e3-162">De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="3b6e3-163">Met het element [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="3b6e3-164">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="3b6e3-165">Het [script Block](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -element geeft het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="3b6e3-166">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="3b6e3-167">Het element [formats Tring](./label-element-for-listitem-for-listcontrol-format.md) geeft een opmaak patroon op dat bepaalt hoe de eigenschap of script waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="3b6e3-168">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-168">This element is optional.</span></span>

- <span data-ttu-id="3b6e3-169">Het element [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) geeft aan hoe de waarde van de eigenschap of het script wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="3b6e3-170">De waarde kan aan de linkerkant, rechts of gecentreerd worden uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="3b6e3-171">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="3b6e3-172">De objecten definiëren die gebruikmaken van de tabel weergave</span><span class="sxs-lookup"><span data-stu-id="3b6e3-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="3b6e3-173">Er zijn twee manieren om te definiëren welke .NET-objecten gebruikmaken van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="3b6e3-174">U kunt het element [ViewSelectedBy](./viewselectedby-element-format.md) gebruiken om de objecten te definiëren die door alle definities van de weer gave kunnen worden weer gegeven, of u kunt het element [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) gebruiken om te definiëren welke objecten worden weer gegeven met een specifieke definitie van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="3b6e3-175">In de meeste gevallen heeft een weer gave slechts één definitie, waardoor objecten doorgaans worden gedefinieerd door het element [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="3b6e3-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="3b6e3-176">In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven in de tabel weergave met behulp van de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="3b6e3-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="3b6e3-177">Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) -elementen dat u kunt opgeven en de volg orde hiervan is niet belang rijk.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="3b6e3-178">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de tabel weergave:</span><span class="sxs-lookup"><span data-stu-id="3b6e3-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="3b6e3-179">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="3b6e3-180">Het element [TypeName](./typename-element-for-viewselectedby-format.md) specificeert het .net-object dat wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="3b6e3-181">De volledig gekwalificeerde .NET-type naam is vereist.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="3b6e3-182">U moet ten minste één type of selectieset voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="3b6e3-183">In het volgende voor beeld worden de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="3b6e3-184">Gebruik selectie sets waar u een gerelateerde set objecten hebt die worden weer gegeven met behulp van meerdere weer gaven, zoals wanneer u een lijst weergave definieert en een tabel weergave voor dezelfde objecten.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="3b6e3-185">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken van een selectie reeks.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="3b6e3-186">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de lijst weergave:</span><span class="sxs-lookup"><span data-stu-id="3b6e3-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="3b6e3-187">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="3b6e3-188">Het [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -element geeft een set objecten op die door de weer gave kan worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="3b6e3-189">U moet ten minste één selectieset of type voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="3b6e3-190">In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven met een specifieke definitie van de tabel weergave met behulp van het element [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="3b6e3-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="3b6e3-191">Met dit element kunt u de .NET-type naam van het object, een selectieset van objecten of een selectie voorwaarde opgeven die opgeeft wanneer de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="3b6e3-192">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het maken van een selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3b6e3-193">Bij het maken van meerdere definities van de tabel weergave kunt u geen andere kolom koppen opgeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="3b6e3-194">U kunt alleen opgeven wat er wordt weer gegeven in de rijen van de tabel, zoals welke objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="3b6e3-195">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door een specifieke definitie van de lijst weergave:</span><span class="sxs-lookup"><span data-stu-id="3b6e3-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="3b6e3-196">Het [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -element definieert welke objecten worden weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="3b6e3-197">Het element [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) specificeert het .net-object dat wordt weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="3b6e3-198">Wanneer u dit element gebruikt, is de volledig gekwalificeerde .NET-type naam vereist.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="3b6e3-199">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="3b6e3-200">Het [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -element (niet weer gegeven) bevat een set objecten die kunnen worden weer gegeven door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="3b6e3-201">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="3b6e3-202">Het element [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (niet weer gegeven) bevat een voor waarde die voor deze definitie moet bestaan.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="3b6e3-203">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="3b6e3-204">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="3b6e3-205">Opmaak teken reeksen gebruiken</span><span class="sxs-lookup"><span data-stu-id="3b6e3-205">Using Format Strings</span></span>

<span data-ttu-id="3b6e3-206">Opmaak teken reeksen kunnen worden toegevoegd aan een weer gave om te bepalen hoe de gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="3b6e3-207">In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="3b6e3-208">De volgende XML-elementen kunnen worden gebruikt om een notatie patroon op te geven:</span><span class="sxs-lookup"><span data-stu-id="3b6e3-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="3b6e3-209">Het [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="3b6e3-210">Voor elke kolom van de rij is een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element vereist.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="3b6e3-211">De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="3b6e3-212">Met het element [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="3b6e3-213">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="3b6e3-214">Het element [formats Tring](./label-element-for-listitem-for-listcontrol-format.md) geeft een opmaak patroon op dat bepaalt hoe de eigenschap of script waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="3b6e3-215">In het volgende voor beeld wordt de- `ToString` methode aangeroepen om de waarde van het script op te maken.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="3b6e3-216">Scripts kunnen een wille keurige methode van een object aanroepen.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="3b6e3-217">Als een object een methode heeft, zoals `ToString` die opmaak parameters heeft, kan het script deze methode ook aanroepen om de uitvoer waarde van het script op te maken.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="3b6e3-218">Het volgende XML-element kan worden gebruikt om de methode aan te roepen `ToString` :</span><span class="sxs-lookup"><span data-stu-id="3b6e3-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="3b6e3-219">Het [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="3b6e3-220">Voor elke kolom van de rij is een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element vereist.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="3b6e3-221">De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="3b6e3-222">Het [script Block](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -element geeft het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="3b6e3-223">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3b6e3-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b6e3-224">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3b6e3-224">See Also</span></span>

[<span data-ttu-id="3b6e3-225">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="3b6e3-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
