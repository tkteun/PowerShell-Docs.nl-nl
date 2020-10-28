---
ms.date: 09/13/2016
ms.topic: reference
title: Een tabelweergave maken
description: Een tabelweergave maken
ms.openlocfilehash: 035d42f7968a9e8babec692a7a5873e24b36cd97
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660298"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="d150b-103">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="d150b-103">Creating a Table View</span></span>

<span data-ttu-id="d150b-104">In een tabel weergave worden gegevens in een of meer kolommen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-104">A table view displays data in one or more columns.</span></span> <span data-ttu-id="d150b-105">Elke rij in de tabel vertegenwoordigt een .NET-object en elke kolom van de tabel vertegenwoordigt een eigenschap van het object of een script waarde.</span><span class="sxs-lookup"><span data-stu-id="d150b-105">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="d150b-106">U kunt een tabel weergave definiëren waarin alle eigenschappen van een object of een subset van de eigenschappen van een object worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-106">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="d150b-107">Een tabel weergave weer geven</span><span class="sxs-lookup"><span data-stu-id="d150b-107">A Table View Display</span></span>

<span data-ttu-id="d150b-108">In het volgende voor beeld ziet u hoe in Windows Power shell het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) wordt weer gegeven dat wordt geretourneerd door de cmdlet [Get-service](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="d150b-108">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="d150b-109">Voor dit object heeft Windows Power shell een tabel weergave gedefinieerd waarin de eigenschap wordt weer gegeven `Status` , de `Name` eigenschap (deze eigenschap is een alias eigenschap voor de `ServiceName` eigenschap) en de `DisplayName` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="d150b-109">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="d150b-110">Elke rij in de tabel vertegenwoordigt een object dat door de cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d150b-110">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="d150b-111">De tabel weergave definiëren</span><span class="sxs-lookup"><span data-stu-id="d150b-111">Defining the Table View</span></span>

<span data-ttu-id="d150b-112">In het volgende XML-bestand wordt het tabel weergave schema weer gegeven voor het weer geven van [System. ServiceProcess. servicecontroller? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -object.</span><span class="sxs-lookup"><span data-stu-id="d150b-112">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="d150b-113">U moet elke eigenschap opgeven die u wilt weer geven in de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="d150b-113">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="d150b-114">De volgende XML-elementen worden gebruikt voor het definiëren van een lijst weergave:</span><span class="sxs-lookup"><span data-stu-id="d150b-114">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="d150b-115">Het element [View](./view-element-format.md) is het bovenliggende element van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="d150b-115">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="d150b-116">(Dit is hetzelfde bovenliggende element voor de lijst weergave, brede en aangepaste besturings elementen.)</span><span class="sxs-lookup"><span data-stu-id="d150b-116">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="d150b-117">Het element [name](./name-element-for-view-format.md) specificeert de naam van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="d150b-117">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="d150b-118">Dit element is vereist voor alle weer gaven.</span><span class="sxs-lookup"><span data-stu-id="d150b-118">This element is required for all views.</span></span>

- <span data-ttu-id="d150b-119">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="d150b-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="d150b-120">Dit element is vereist.</span><span class="sxs-lookup"><span data-stu-id="d150b-120">This element is required.</span></span>

- <span data-ttu-id="d150b-121">Het element [GroupBy](./groupby-element-for-view-format.md) (niet weer gegeven in dit voor beeld) definieert wanneer een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-121">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="d150b-122">Er wordt een nieuwe groep gestart wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="d150b-122">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="d150b-123">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="d150b-123">This element is optional.</span></span>

- <span data-ttu-id="d150b-124">Het element [Controls](./controls-element-for-view-format.md) (in dit voor beeld wordt niet weer gegeven) definieert de aangepaste besturings elementen die door de tabel weergave worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="d150b-124">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="d150b-125">Met besturings elementen kunt u nader aangeven hoe de gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-125">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="d150b-126">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="d150b-126">This element is optional.</span></span> <span data-ttu-id="d150b-127">Een weer gave kan zijn eigen aangepaste besturings elementen definiëren, maar u kunt ook algemene besturings elementen gebruiken die kunnen worden gebruikt door elke weer gave in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="d150b-127">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="d150b-128">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over aangepaste besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="d150b-128">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="d150b-129">Het [HideTableHeaders](./hidetableheaders-element-format.md) -element (niet weer gegeven in dit voor beeld) geeft aan dat er geen labels worden weer gegeven boven aan de tabel.</span><span class="sxs-lookup"><span data-stu-id="d150b-129">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="d150b-130">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="d150b-130">This element is optional.</span></span>

- <span data-ttu-id="d150b-131">Het [TableControl](./tablecontrol-element-format.md) -element waarmee de koptekst en de rij-informatie van de tabel worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="d150b-131">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="d150b-132">Net als bij alle andere weer gaven kunnen in een tabel weergave de waarden van object eigenschappen of waarden worden weer gegeven die door scripts worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="d150b-132">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="d150b-133">Kolom koppen definiëren</span><span class="sxs-lookup"><span data-stu-id="d150b-133">Defining Column Headers</span></span>

1. <span data-ttu-id="d150b-134">Het [TableHeaders](./tableheaders-element-format.md) -element en de onderliggende elementen bepalen wat er boven aan de tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-134">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="d150b-135">Het element [TableColumnHeader](./tablecolumnheader-element-format.md) definieert wat wordt weer gegeven aan de bovenkant van een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="d150b-135">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="d150b-136">Geef deze elementen op in de volg orde waarin de kopteksten moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-136">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="d150b-137">Er is geen limiet voor het aantal van dit element dat u kunt gebruiken, maar het aantal [TableColumnHeader](./tablecolumnheader-element-format.md) -elementen in de tabel weergave moet gelijk zijn aan het aantal [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) -elementen dat u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d150b-137">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="d150b-138">Het element [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) geeft de tekst aan die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-138">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="d150b-139">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="d150b-139">This element is optional.</span></span>

4. <span data-ttu-id="d150b-140">Met het element [width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) wordt de breedte (in tekens) van de kolom opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-140">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="d150b-141">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="d150b-141">This element is optional.</span></span>

5. <span data-ttu-id="d150b-142">Het element [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) geeft aan hoe het label wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-142">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="d150b-143">Het label kan aan de linkerkant, rechts of gecentreerd worden uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="d150b-143">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="d150b-144">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="d150b-144">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="d150b-145">De tabel rijen definiëren</span><span class="sxs-lookup"><span data-stu-id="d150b-145">Defining the Table Rows</span></span>

<span data-ttu-id="d150b-146">Tabel weergaven kunnen een of meer definities bieden die aangeven welke gegevens in de rijen van de tabel worden weer gegeven door de onderliggende elementen van het element [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d150b-146">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="d150b-147">U kunt meerdere definities opgeven voor de rijen van de tabel, maar de kopteksten van de rijen blijven hetzelfde, ongeacht de rijdefinitie die wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d150b-147">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="d150b-148">Normaal gesp roken bevat een tabel slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="d150b-148">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="d150b-149">In het volgende voor beeld bevat de weer gave één definitie waarmee de waarden van verschillende eigenschappen van het [System. Diagnostics. process worden weer gegeven? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -object.</span><span class="sxs-lookup"><span data-stu-id="d150b-149">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="d150b-150">Een tabel weergave kan de waarde van een eigenschap of de waarde van een script (niet weer gegeven in het voor beeld) weer geven in de rijen.</span><span class="sxs-lookup"><span data-stu-id="d150b-150">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="d150b-151">De volgende XML-elementen kunnen worden gebruikt om definities voor een rij op te geven:</span><span class="sxs-lookup"><span data-stu-id="d150b-151">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="d150b-152">Het element [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) en de onderliggende elementen bepalen wat wordt weer gegeven in de rijen van de tabel.</span><span class="sxs-lookup"><span data-stu-id="d150b-152">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="d150b-153">Het [TableRowEntry](./listentry-element-for-listcontrol-format.md) -element bevat een definitie van de rij.</span><span class="sxs-lookup"><span data-stu-id="d150b-153">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="d150b-154">Er is ten minste één [TableRowEntry](./listentry-element-for-listcontrol-format.md) vereist. Er is echter geen maximum limiet voor het aantal elementen dat u kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="d150b-154">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="d150b-155">In de meeste gevallen heeft een weer gave slechts één definitie.</span><span class="sxs-lookup"><span data-stu-id="d150b-155">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="d150b-156">Het [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -element geeft de objecten aan die door een specifieke definitie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-156">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="d150b-157">Dit element is optioneel en is alleen nodig wanneer u meerdere [TableRowEntry](./listentry-element-for-listcontrol-format.md) -elementen definieert waarin verschillende objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-157">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="d150b-158">Met het [Terugloop](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element wordt aangegeven dat de tekst die de kolom breedte overschrijdt wordt weer gegeven op de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="d150b-158">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="d150b-159">Standaard wordt tekst die de kolom breedte overschrijdt, afgekapt.</span><span class="sxs-lookup"><span data-stu-id="d150b-159">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="d150b-160">Het [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) -element definieert de eigenschappen of scripts waarvan de waarden in de rij worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-160">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="d150b-161">Het [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="d150b-161">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="d150b-162">Voor elke kolom van de rij is een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element vereist.</span><span class="sxs-lookup"><span data-stu-id="d150b-162">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="d150b-163">De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="d150b-163">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="d150b-164">Met het element [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="d150b-164">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="d150b-165">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-165">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d150b-166">Het [script Block](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -element geeft het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="d150b-166">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="d150b-167">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-167">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="d150b-168">Het element [formats Tring](./label-element-for-listitem-for-listcontrol-format.md) geeft een opmaak patroon op dat bepaalt hoe de eigenschap of script waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-168">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="d150b-169">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="d150b-169">This element is optional.</span></span>

- <span data-ttu-id="d150b-170">Het element [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) geeft aan hoe de waarde van de eigenschap of het script wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-170">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="d150b-171">De waarde kan aan de linkerkant, rechts of gecentreerd worden uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="d150b-171">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="d150b-172">Dit element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="d150b-172">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="d150b-173">De objecten definiëren die gebruikmaken van de tabel weergave</span><span class="sxs-lookup"><span data-stu-id="d150b-173">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="d150b-174">Er zijn twee manieren om te definiëren welke .NET-objecten gebruikmaken van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="d150b-174">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="d150b-175">U kunt het element [ViewSelectedBy](./viewselectedby-element-format.md) gebruiken om de objecten te definiëren die door alle definities van de weer gave kunnen worden weer gegeven, of u kunt het element [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) gebruiken om te definiëren welke objecten worden weer gegeven met een specifieke definitie van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="d150b-175">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="d150b-176">In de meeste gevallen heeft een weer gave slechts één definitie, waardoor objecten doorgaans worden gedefinieerd door het element [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="d150b-176">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="d150b-177">In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven in de tabel weergave met behulp van de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="d150b-177">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d150b-178">Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) -elementen dat u kunt opgeven en de volg orde hiervan is niet belang rijk.</span><span class="sxs-lookup"><span data-stu-id="d150b-178">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="d150b-179">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de tabel weergave:</span><span class="sxs-lookup"><span data-stu-id="d150b-179">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="d150b-180">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="d150b-180">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="d150b-181">Het element [TypeName](./typename-element-for-viewselectedby-format.md) specificeert het .net-object dat wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="d150b-181">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="d150b-182">De volledig gekwalificeerde .NET-type naam is vereist.</span><span class="sxs-lookup"><span data-stu-id="d150b-182">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="d150b-183">U moet ten minste één type of selectieset voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-183">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d150b-184">In het volgende voor beeld worden de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d150b-184">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d150b-185">Gebruik selectie sets waar u een gerelateerde set objecten hebt die worden weer gegeven met behulp van meerdere weer gaven, zoals wanneer u een lijst weergave definieert en een tabel weergave voor dezelfde objecten.</span><span class="sxs-lookup"><span data-stu-id="d150b-185">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="d150b-186">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken van een selectie reeks.</span><span class="sxs-lookup"><span data-stu-id="d150b-186">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="d150b-187">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de lijst weergave:</span><span class="sxs-lookup"><span data-stu-id="d150b-187">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="d150b-188">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="d150b-188">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="d150b-189">Het [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -element geeft een set objecten op die door de weer gave kan worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-189">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="d150b-190">U moet ten minste één selectieset of type voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-190">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d150b-191">In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven met een specifieke definitie van de tabel weergave met behulp van het element [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="d150b-191">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="d150b-192">Met dit element kunt u de .NET-type naam van het object, een selectieset van objecten of een selectie voorwaarde opgeven die opgeeft wanneer de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d150b-192">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="d150b-193">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het maken van een selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="d150b-193">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d150b-194">Bij het maken van meerdere definities van de tabel weergave kunt u geen andere kolom koppen opgeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-194">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="d150b-195">U kunt alleen opgeven wat er wordt weer gegeven in de rijen van de tabel, zoals welke objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-195">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="d150b-196">De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door een specifieke definitie van de lijst weergave:</span><span class="sxs-lookup"><span data-stu-id="d150b-196">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="d150b-197">Het [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -element definieert welke objecten worden weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="d150b-197">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="d150b-198">Het element [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) specificeert het .net-object dat wordt weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="d150b-198">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="d150b-199">Wanneer u dit element gebruikt, is de volledig gekwalificeerde .NET-type naam vereist.</span><span class="sxs-lookup"><span data-stu-id="d150b-199">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="d150b-200">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-200">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d150b-201">Het [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -element (niet weer gegeven) bevat een set objecten die kunnen worden weer gegeven door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="d150b-201">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="d150b-202">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-202">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d150b-203">Het element [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (niet weer gegeven) bevat een voor waarde die voor deze definitie moet bestaan.</span><span class="sxs-lookup"><span data-stu-id="d150b-203">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="d150b-204">U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-204">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="d150b-205">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="d150b-205">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="d150b-206">Opmaak teken reeksen gebruiken</span><span class="sxs-lookup"><span data-stu-id="d150b-206">Using Format Strings</span></span>

<span data-ttu-id="d150b-207">Opmaak teken reeksen kunnen worden toegevoegd aan een weer gave om te bepalen hoe de gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-207">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="d150b-208">In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="d150b-208">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="d150b-209">De volgende XML-elementen kunnen worden gebruikt om een notatie patroon op te geven:</span><span class="sxs-lookup"><span data-stu-id="d150b-209">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="d150b-210">Het [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="d150b-210">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="d150b-211">Voor elke kolom van de rij is een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element vereist.</span><span class="sxs-lookup"><span data-stu-id="d150b-211">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="d150b-212">De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="d150b-212">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="d150b-213">Met het element [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="d150b-213">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="d150b-214">U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d150b-215">Het element [formats Tring](./label-element-for-listitem-for-listcontrol-format.md) geeft een opmaak patroon op dat bepaalt hoe de eigenschap of script waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-215">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="d150b-216">In het volgende voor beeld wordt de- `ToString` methode aangeroepen om de waarde van het script op te maken.</span><span class="sxs-lookup"><span data-stu-id="d150b-216">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="d150b-217">Scripts kunnen een wille keurige methode van een object aanroepen.</span><span class="sxs-lookup"><span data-stu-id="d150b-217">Scripts can call any method of an object.</span></span> <span data-ttu-id="d150b-218">Als een object een methode heeft, zoals `ToString` die opmaak parameters heeft, kan het script deze methode ook aanroepen om de uitvoer waarde van het script op te maken.</span><span class="sxs-lookup"><span data-stu-id="d150b-218">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="d150b-219">Het volgende XML-element kan worden gebruikt om de methode aan te roepen `ToString` :</span><span class="sxs-lookup"><span data-stu-id="d150b-219">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="d150b-220">Het [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="d150b-220">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="d150b-221">Voor elke kolom van de rij is een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element vereist.</span><span class="sxs-lookup"><span data-stu-id="d150b-221">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="d150b-222">De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="d150b-222">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="d150b-223">Het [script Block](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -element geeft het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="d150b-223">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="d150b-224">U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="d150b-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="d150b-225">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d150b-225">See Also</span></span>

[<span data-ttu-id="d150b-226">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d150b-226">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
