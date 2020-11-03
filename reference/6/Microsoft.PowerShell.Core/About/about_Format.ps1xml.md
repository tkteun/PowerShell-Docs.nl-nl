---
description: Vanaf Power shell 6 worden de standaard weergaven voor objecten gedefinieerd in Power shell-bron code.  U kunt uw eigen `Format.ps1xml` bestanden maken om de weer gave van objecten te wijzigen of om standaard weer gaven te definiëren voor nieuwe object typen die u in Power Shell maakt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1XML
ms.openlocfilehash: bbe7c9d2d36673ff6240be89f9ceb439ab0d0dfa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252337"
---
# <a name="about-formatps1xml"></a><span data-ttu-id="bf555-105">Over Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="bf555-105">About Format.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="bf555-106">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="bf555-106">Short description</span></span>

<span data-ttu-id="bf555-107">Vanaf Power shell 6 worden de standaard weergaven voor objecten gedefinieerd in Power shell-bron code.</span><span class="sxs-lookup"><span data-stu-id="bf555-107">Beginning in PowerShell 6, the default views for objects are defined in PowerShell source code.</span></span>

<span data-ttu-id="bf555-108">U kunt uw eigen `Format.ps1xml` bestanden maken om de weer gave van objecten te wijzigen of om standaard weer gaven te definiëren voor nieuwe object typen die u in Power Shell maakt.</span><span class="sxs-lookup"><span data-stu-id="bf555-108">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="bf555-109">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="bf555-109">Long description</span></span>

<span data-ttu-id="bf555-110">Vanaf Power shell 6 worden de standaard weergaven gedefinieerd in Power shell-bron code.</span><span class="sxs-lookup"><span data-stu-id="bf555-110">Beginning in PowerShell 6, the default views are defined in PowerShell source code.</span></span> <span data-ttu-id="bf555-111">De `Format.ps1xml` bestanden van de Power shell 5,1 en eerdere versies bestaan niet in Power shell 6 en hoger.</span><span class="sxs-lookup"><span data-stu-id="bf555-111">The `Format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="bf555-112">De Power shell-bron code definieert de standaard weergave van objecten in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="bf555-112">The PowerShell source code defines the default display of objects in the PowerShell console.</span></span> <span data-ttu-id="bf555-113">U kunt uw eigen `Format.ps1xml` bestanden maken om de weer gave van objecten te wijzigen of om standaard weer gaven te definiëren voor nieuwe object typen die u in Power Shell maakt.</span><span class="sxs-lookup"><span data-stu-id="bf555-113">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

<span data-ttu-id="bf555-114">Wanneer Power shell een object weergeeft, worden de gegevens in gestructureerde indelings bestanden gebruikt om de standaard weergave van het object te bepalen.</span><span class="sxs-lookup"><span data-stu-id="bf555-114">When PowerShell displays an object, it uses the data in structured formatting files to determine the default display of the object.</span></span> <span data-ttu-id="bf555-115">De gegevens in de indelings bestanden bepalen of het object wordt weer gegeven in een tabel of in een lijst en bepaalt welke eigenschappen standaard worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bf555-115">The data in the formatting files determines whether the object is rendered in a table or in a list, and it determines which properties are displayed by default.</span></span>

<span data-ttu-id="bf555-116">De opmaak is alleen van invloed op de weer gave.</span><span class="sxs-lookup"><span data-stu-id="bf555-116">The formatting affects the display only.</span></span> <span data-ttu-id="bf555-117">Dit heeft geen invloed op welke object eigenschappen worden door gegeven aan de pijp lijn of hoe ze worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="bf555-117">It doesn't affect which object properties are passed down the pipeline or how they're passed.</span></span> <span data-ttu-id="bf555-118">`Format.ps1xml` bestanden kunnen niet worden gebruikt om de uitvoer indeling voor hash-tabellen aan te passen.</span><span class="sxs-lookup"><span data-stu-id="bf555-118">`Format.ps1xml` files can't be used to customize the output format for hash tables.</span></span>

<span data-ttu-id="bf555-119">Een `.ps1xml` Opmaak bestand kan vier verschillende weer gaven van elk object definiëren:</span><span class="sxs-lookup"><span data-stu-id="bf555-119">A `.ps1xml` formatting file can define four different views of each object:</span></span>

- <span data-ttu-id="bf555-120">Tabel</span><span class="sxs-lookup"><span data-stu-id="bf555-120">Table</span></span>
- <span data-ttu-id="bf555-121">Lijst</span><span class="sxs-lookup"><span data-stu-id="bf555-121">List</span></span>
- <span data-ttu-id="bf555-122">Organisatiebreed</span><span class="sxs-lookup"><span data-stu-id="bf555-122">Wide</span></span>
- <span data-ttu-id="bf555-123">Aangepast</span><span class="sxs-lookup"><span data-stu-id="bf555-123">Custom</span></span>

<span data-ttu-id="bf555-124">Als bijvoorbeeld de uitvoer van een `Get-ChildItem` opdracht wordt gepiped naar een `Format-List` opdracht, `Format-List` gebruikt de lijst weergave die is gedefinieerd in de bron code om te bepalen hoe het bestand en de objecten van de map als een lijst worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bf555-124">For example, when the output of a `Get-ChildItem` command is piped to a `Format-List` command, `Format-List` uses the list view defined in the source code to determine how to display the file and folder objects as a list.</span></span>

<span data-ttu-id="bf555-125">Wanneer een opmaak bestand meer dan één weer gave van een object bevat, past Power shell de eerste weer gave toe die wordt gevonden.</span><span class="sxs-lookup"><span data-stu-id="bf555-125">When a formatting file includes more than one view of an object, PowerShell applies the first view that it finds.</span></span>

<span data-ttu-id="bf555-126">In een aangepast `Format.ps1xml` bestand wordt een weer gave gedefinieerd met behulp van een set XML-tags die de naam van de weer gave beschrijven, het type object waarop deze kan worden toegepast, de kolom koppen en de eigenschappen die worden weer gegeven in de hoofd tekst van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="bf555-126">In a custom `Format.ps1xml` file, a view is defined by a set of XML tags that describe the name of the view, the type of object to which it can be applied, the column headers, and the properties that are displayed in the body of the view.</span></span> <span data-ttu-id="bf555-127">De indeling in `Format.ps1xml` bestanden wordt alleen toegepast voordat de gegevens aan de gebruiker worden gepresenteerd.</span><span class="sxs-lookup"><span data-stu-id="bf555-127">The format in `Format.ps1xml` files is applied just before the data is presented to the user.</span></span>

## <a name="creating-new-formatps1xml-files"></a><span data-ttu-id="bf555-128">Nieuwe Format.ps1XML-bestanden maken</span><span class="sxs-lookup"><span data-stu-id="bf555-128">Creating new Format.ps1xml files</span></span>

<span data-ttu-id="bf555-129">Als u de weergave opmaak van een bestaande object weergave wilt wijzigen of als u weer gaven wilt toevoegen voor nieuwe objecten, maakt u uw eigen `Format.ps1xml` bestanden en voegt u deze toe aan uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="bf555-129">To change the display format of an existing object view, or to add views for new objects, create your own `Format.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="bf555-130">Als u een `Format.ps1xml` bestand wilt maken voor het definiëren van een aangepaste weer gave, gebruikt u de cmdlets [Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) en [export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) .</span><span class="sxs-lookup"><span data-stu-id="bf555-130">To create a `Format.ps1xml` file to define a custom view, use the [Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) and [Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) cmdlets.</span></span> <span data-ttu-id="bf555-131">Gebruik een tekst editor om het bestand te bewerken.</span><span class="sxs-lookup"><span data-stu-id="bf555-131">Use a text editor to edit the file.</span></span> <span data-ttu-id="bf555-132">Het bestand kan worden opgeslagen in een map die Power shell kan openen, zoals een submap van `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="bf555-132">The file can be saved to any directory that PowerShell can access, such as a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="bf555-133">Als u de opmaak van een huidige weer gave wilt wijzigen, gaat u naar de weer gave in het opmaak bestand en gebruikt u vervolgens de labels om de weer gave te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bf555-133">To change the formatting of a current view, locate the view in the formatting file, and then use the tags to change the view.</span></span> <span data-ttu-id="bf555-134">Als u een weer gave voor een nieuw object type wilt maken, maakt u een nieuwe weer gave of gebruikt u een bestaande weer gave als een model.</span><span class="sxs-lookup"><span data-stu-id="bf555-134">To create a view for a new object type, create a new view, or use an existing view as a model.</span></span> <span data-ttu-id="bf555-135">De tags worden in de volgende sectie beschreven.</span><span class="sxs-lookup"><span data-stu-id="bf555-135">The tags are described in the next section.</span></span> <span data-ttu-id="bf555-136">U kunt vervolgens alle andere weer gaven in het bestand verwijderen, zodat de wijzigingen duidelijk zijn voor iedereen die het bestand bekijkt.</span><span class="sxs-lookup"><span data-stu-id="bf555-136">You can then delete all the other views in the file so that the changes are obvious to anyone examining the file.</span></span>

<span data-ttu-id="bf555-137">Nadat u de wijzigingen hebt opgeslagen, gebruikt u de [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) om het nieuwe bestand aan uw Power shell-sessie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="bf555-137">After you save the changes, use the [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) to add the new file to your PowerShell session.</span></span> <span data-ttu-id="bf555-138">Als u wilt dat de weer gave voor rang krijgt boven een weer gave die is gedefinieerd in de ingebouwde bestanden, gebruikt u de para meter **PrependPath** .</span><span class="sxs-lookup"><span data-stu-id="bf555-138">If you want your view to take precedence over a view defined in the built-in files, use the **PrependPath** parameter.</span></span> <span data-ttu-id="bf555-139">`Update-FormatData` alleen van invloed op de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bf555-139">`Update-FormatData` affects only the current session.</span></span> <span data-ttu-id="bf555-140">Als u de wijziging wilt aanbrengen in alle toekomstige sessies, voegt u de `Update-FormatData` opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="bf555-140">To make the change to all future sessions, add the `Update-FormatData` command to your PowerShell profile.</span></span>

### <a name="example-add-calendar-data-to-culture-objects"></a><span data-ttu-id="bf555-141">Voor beeld: agenda gegevens toevoegen aan cultuur objecten</span><span class="sxs-lookup"><span data-stu-id="bf555-141">Example: Add calendar data to culture objects</span></span>

<span data-ttu-id="bf555-142">In dit voor beeld ziet u hoe u de indeling wijzigt van de cultuur-objecten **System. Globalization. Culture info** die zijn gegenereerd door de `Get-Culture` cmdlet in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="bf555-142">This example shows how to change the formatting of the culture objects **System.Globalization.CultureInfo** generated by the `Get-Culture` cmdlet in the current PowerShell session.</span></span> <span data-ttu-id="bf555-143">Met de opdrachten in het voor beeld wordt de eigenschap **Calendar** toegevoegd aan de standaard tabel weergave weer gave van cultuur-objecten.</span><span class="sxs-lookup"><span data-stu-id="bf555-143">The commands in the example add the **Calendar** property to the default table view display of culture objects.</span></span>

<span data-ttu-id="bf555-144">Als u wilt beginnen, haalt u de indelings gegevens op uit het bron code bestand en maakt u een `Format.ps1xml` bestand dat de huidige weer gave van de cultuur-objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="bf555-144">To begin, get the format data from the source code file and create a `Format.ps1xml` file that contains the current view of the culture objects.</span></span>

```powershell
Get-FormatData -TypeName System.Globalization.CultureInfo |
  Export-FormatData -Path $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="bf555-145">Open het `CultureInfo.Format.ps1xml` bestand in een XML-of tekst editor, zoals Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="bf555-145">Open the `CultureInfo.Format.ps1xml` file in any XML or text editor, such as Visual Studio Code.</span></span> <span data-ttu-id="bf555-146">De volgende XML definieert de weer gaven van het **Culture info** -object.</span><span class="sxs-lookup"><span data-stu-id="bf555-146">The following XML defines the views of the **CultureInfo** object.</span></span>

<span data-ttu-id="bf555-147">Het `CultureInfo.Format.ps1xml` bestand moet er ongeveer uitzien als in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="bf555-147">The `CultureInfo.Format.ps1xml` file should look like the following sample:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.Globalization.CultureInfo</Name>
      <ViewSelectedBy>
        <TypeName>System.Globalization.CultureInfo</TypeName>
      </ViewSelectedBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Width>16</Width>
          </TableColumnHeader>
          <TableColumnHeader>
            <Width>16</Width>
          </TableColumnHeader>
          <TableColumnHeader />
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>LCID</PropertyName>
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
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="bf555-148">Maak een nieuwe kolom voor de eigenschap **Calendar** door een nieuwe set tags toe te voegen `<TableColumnHeader>` .</span><span class="sxs-lookup"><span data-stu-id="bf555-148">Create a new column for the **Calendar** property by adding a new set of `<TableColumnHeader>` tags.</span></span> <span data-ttu-id="bf555-149">De waarde van de eigenschap **Calendar** kan lang zijn. Geef dus een waarde van 45 tekens op als de `<Width>` .</span><span class="sxs-lookup"><span data-stu-id="bf555-149">The value of the **Calendar** property can be long, so specify a value of 45 characters as the `<Width>`.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>45</Width>
  </TableColumnHeader>
  <TableColumnHeader/>
</TableHeaders>
```

<span data-ttu-id="bf555-150">Voeg een nieuw kolom item toe voor **kalenders** in de tabel rijen met behulp van de `<TableColumnItem>` `<PropertyName` Tags en:</span><span class="sxs-lookup"><span data-stu-id="bf555-150">Add a new column item for **Calendar** in the table rows using the `<TableColumnItem>` and `<PropertyName` tags:</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName>LCID</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Name</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Calendar</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>DisplayName</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>
```

<span data-ttu-id="bf555-151">Sla het bestand op en sluit het.</span><span class="sxs-lookup"><span data-stu-id="bf555-151">Save and close the file.</span></span> <span data-ttu-id="bf555-152">Gebruik `Update-FormatData` om het nieuwe indelings bestand aan de huidige Power shell-sessie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="bf555-152">Use `Update-FormatData` to add the new format file to the current PowerShell session.</span></span>

<span data-ttu-id="bf555-153">In dit voor beeld wordt de para meter **PrependPath** gebruikt om het nieuwe bestand in een hogere volg orde dan het oorspronkelijke bestand te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="bf555-153">This example uses the **PrependPath** parameter to place the new file in a higher precedence order than the original file.</span></span> <span data-ttu-id="bf555-154">Zie [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bf555-154">For more information, see [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span></span>

```powershell
Update-FormatData -PrependPath $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="bf555-155">Als u de wijziging wilt testen, typt `Get-Culture` en controleert u de uitvoer die de eigenschap **Calendar** bevat.</span><span class="sxs-lookup"><span data-stu-id="bf555-155">To test the change, type `Get-Culture` and review the output that includes the **Calendar** property.</span></span>

```powershell
Get-Culture
```

```Output
LCID  Name   Calendar                                DisplayName
----  ----   --------                                -----------
1033  en-US  System.Globalization.GregorianCalendar  English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a><span data-ttu-id="bf555-156">De XML in Format.ps1XML-bestanden</span><span class="sxs-lookup"><span data-stu-id="bf555-156">The XML in Format.ps1xml files</span></span>

<span data-ttu-id="bf555-157">De volledige schema definitie vindt u in [Format. XSD](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in de Power shell-bron code opslagplaats op github.</span><span class="sxs-lookup"><span data-stu-id="bf555-157">The full schema definition can be found in [Format.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="bf555-158">De sectie **ViewDefinitions** van elk `Format.ps1xml` bestand bevat de `<View>` Tags waarmee elke weer gave wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="bf555-158">The **ViewDefinitions** section of each `Format.ps1xml` file contains the `<View>` tags that define each view.</span></span> <span data-ttu-id="bf555-159">Een typische `<View>` tag bevat de volgende Tags:</span><span class="sxs-lookup"><span data-stu-id="bf555-159">A typical `<View>` tag includes the following tags:</span></span>

- <span data-ttu-id="bf555-160">`<Name>` Hiermee wordt de naam van de weer gave aangeduid.</span><span class="sxs-lookup"><span data-stu-id="bf555-160">`<Name>` identifies the name of the view.</span></span>
- <span data-ttu-id="bf555-161">`<ViewSelectedBy>` Hiermee geeft u het object type of de typen waarop de weer gave van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="bf555-161">`<ViewSelectedBy>` specifies the object type or types to which the view applies.</span></span>
- <span data-ttu-id="bf555-162">`<GroupBy>` Hiermee wordt aangegeven hoe items in de weer gave in groepen worden gecombineerd.</span><span class="sxs-lookup"><span data-stu-id="bf555-162">`<GroupBy>` specifies how items in the view will be combined in groups.</span></span>
- <span data-ttu-id="bf555-163">`<TableControl>`, `<ListControl>` , `<WideControl>` en `<CustomControl>` bevatten de tags die aangeven hoe elk item wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bf555-163">`<TableControl>`, `<ListControl>`, `<WideControl>`, and `<CustomControl>` contain the tags that specify how each item will be displayed.</span></span>

### <a name="viewselectedby-tag"></a><span data-ttu-id="bf555-164">ViewSelectedBy-tag</span><span class="sxs-lookup"><span data-stu-id="bf555-164">ViewSelectedBy tag</span></span>

<span data-ttu-id="bf555-165">De `<ViewSelectedBy>` tag kan een `<TypeName>` tag bevatten voor elk object type waarop de weer gave van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="bf555-165">The `<ViewSelectedBy>` tag can contain a `<TypeName>` tag for each object type to which the view applies.</span></span> <span data-ttu-id="bf555-166">Het kan ook een tag bevatten `<SelectionSetName>` die verwijst naar een selectieset die elders is gedefinieerd met behulp van een `<SelectionSet>` tag.</span><span class="sxs-lookup"><span data-stu-id="bf555-166">Or, it can contain a `<SelectionSetName>` tag that references a selection set that is defined elsewhere by using a `<SelectionSet>` tag.</span></span>

### <a name="groupby-tag"></a><span data-ttu-id="bf555-167">GroupBy-tag</span><span class="sxs-lookup"><span data-stu-id="bf555-167">GroupBy tag</span></span>

<span data-ttu-id="bf555-168">Het `<GroupBy>` label bevat een `<PropertyName>` tag die de object eigenschap specificeert op basis waarvan items moeten worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="bf555-168">The `<GroupBy>` tag contains a `<PropertyName>` tag that specifies the object property by which items are to be grouped.</span></span> <span data-ttu-id="bf555-169">Het bevat ook een `<Label>` label dat een teken reeks opgeeft die moet worden gebruikt als label voor elke groep of een `<CustomControlName>` label dat verwijst naar een aangepast besturings element dat elders is gedefinieerd met behulp van een `<Control>` tag.</span><span class="sxs-lookup"><span data-stu-id="bf555-169">It also contains either a `<Label>` tag that specifies a string to be used as a label for each group or a `<CustomControlName>` tag that references a custom control defined elsewhere using a `<Control>` tag.</span></span> <span data-ttu-id="bf555-170">Het `<Control>` label bevat een `<Name>` tag en een `<CustomControl>` tag.</span><span class="sxs-lookup"><span data-stu-id="bf555-170">The `<Control>` tag contains a `<Name>` tag and a `<CustomControl>` tag.</span></span>

### <a name="tablecontroltag"></a><span data-ttu-id="bf555-171">TableControlTag</span><span class="sxs-lookup"><span data-stu-id="bf555-171">TableControlTag</span></span>

<span data-ttu-id="bf555-172">De `<TableControl>` tag bevat normaal gesp roken `<TableHeaders>` `<TableRowEntries>` labels en tags waarmee de opmaak van de koppen en rijen van de tabel worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="bf555-172">The `<TableControl>` tag typically contains `<TableHeaders>` and `<TableRowEntries>` tags that define the formatting for the table's heads and rows.</span></span> <span data-ttu-id="bf555-173">Het `<TableHeaders>` label bevat doorgaans `<TableColumnHeader>` Tags die de `<Label>` `<Width>` Tags, en bevatten `<Alignment>` .</span><span class="sxs-lookup"><span data-stu-id="bf555-173">The `<TableHeaders>` tag typically contains `<TableColumnHeader>` tags that contain `<Label>`, `<Width>`, and `<Alignment>` tags.</span></span> <span data-ttu-id="bf555-174">Het `<TableRowEntries>` label bevat `<TableRowEntry>` labels voor elke rij in de tabel.</span><span class="sxs-lookup"><span data-stu-id="bf555-174">The `<TableRowEntries>` tag contains `<TableRowEntry>` tags for each row in the table.</span></span> <span data-ttu-id="bf555-175">Het `<TableRowEntry>` label bevat een `<TableColumnItems>` label dat een `<TableColumnItem>` tag bevat voor elke kolom in de rij.</span><span class="sxs-lookup"><span data-stu-id="bf555-175">The `<TableRowEntry>` tag contains a `<TableColumnItems>` tag that contains a `<TableColumnItem>` tag for each column in the row.</span></span> <span data-ttu-id="bf555-176">Normaal gesp roken `<TableColumnItem>` bevat de tag een `<PropertyName>` tag die de object eigenschap identificeert die moet worden weer gegeven op de gedefinieerde locatie of een label met een `<ScriptBlock>` script code die een resultaat berekent dat op de locatie moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bf555-176">Typically, the `<TableColumnItem>` tag contains either a `<PropertyName>` tag that identifies the object property to be displayed in the defined location, or a `<ScriptBlock>` tag that contains script code that calculates a result that is to be displayed in the location.</span></span>

> [!NOTE]
> <span data-ttu-id="bf555-177">Script blokken kunnen ook elders worden gebruikt in locaties waar berekende resultaten nuttig kunnen zijn.</span><span class="sxs-lookup"><span data-stu-id="bf555-177">Script blocks can also be used elsewhere in locations where calculated results can be useful.</span></span>

<span data-ttu-id="bf555-178">De `<TableColumnItem>` tag kan ook een `<FormatString>` tag bevatten die aangeeft hoe de eigenschap of de berekende resultaten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bf555-178">The `<TableColumnItem>` tag can also contain a `<FormatString>` tag that specifies how the property or the calculated results will be displayed.</span></span>

### <a name="listcontrol-tag"></a><span data-ttu-id="bf555-179">ListControl-tag</span><span class="sxs-lookup"><span data-stu-id="bf555-179">ListControl tag</span></span>

<span data-ttu-id="bf555-180">De `<ListControl>` tag bevat meestal een `<ListEntries>` tag.</span><span class="sxs-lookup"><span data-stu-id="bf555-180">The `<ListControl>` tag typically contains a `<ListEntries>` tag.</span></span> <span data-ttu-id="bf555-181">Het `<ListEntries>` label bevat een `<ListEntry>` tag.</span><span class="sxs-lookup"><span data-stu-id="bf555-181">The `<ListEntries>` tag contains a `<ListEntry>` tag.</span></span> <span data-ttu-id="bf555-182">Het `<ListEntry>` label bevat een `<ListItems>` tag.</span><span class="sxs-lookup"><span data-stu-id="bf555-182">The `<ListEntry>` tag contains a `<ListItems>` tag.</span></span> <span data-ttu-id="bf555-183">Het `<ListItems>` label bevat `<ListItem>` Tags die labels bevatten `<PropertyName>` .</span><span class="sxs-lookup"><span data-stu-id="bf555-183">The `<ListItems>` tag contains `<ListItem>` tags, which contain `<PropertyName>` tags.</span></span> <span data-ttu-id="bf555-184">De `<PropertyName>` labels geven de object eigenschap op die moet worden weer gegeven op de opgegeven locatie in de lijst.</span><span class="sxs-lookup"><span data-stu-id="bf555-184">The `<PropertyName>` tags specify the object property to be displayed at the specified location in the list.</span></span> <span data-ttu-id="bf555-185">Als de weergave selectie is gedefinieerd met behulp van een selectieset, `<ListControl>` `<ListEntry>` kunnen de tags en ook een tag bevatten `<EntrySelectedBy>` die een of meer `<TypeName>` labels bevat.</span><span class="sxs-lookup"><span data-stu-id="bf555-185">If the view selection is defined using a selection set, the `<ListControl>` and `<ListEntry>` tags can also contain an `<EntrySelectedBy>` tag that contains one or more `<TypeName>` tags.</span></span> <span data-ttu-id="bf555-186">Deze `<TypeName>` Tags geven het object type op waarvan de `<ListControl>` tag is bedoeld om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bf555-186">These `<TypeName>` tags specify the object type that the `<ListControl>` tag is intended to display.</span></span>

### <a name="widecontrol-tag"></a><span data-ttu-id="bf555-187">WideControl-tag</span><span class="sxs-lookup"><span data-stu-id="bf555-187">WideControl tag</span></span>

<span data-ttu-id="bf555-188">De `<WideControl>` tag bevat meestal een `<WideEntries>` tag.</span><span class="sxs-lookup"><span data-stu-id="bf555-188">The `<WideControl>` tag typically contains a `<WideEntries>` tag.</span></span> <span data-ttu-id="bf555-189">Het `<WideEntries>` label bevat een of meer `<WideEntry>` Tags.</span><span class="sxs-lookup"><span data-stu-id="bf555-189">The `<WideEntries>` tag contains one or more `<WideEntry>` tags.</span></span> <span data-ttu-id="bf555-190">Een `<WideEntry>` tag bevat meestal een `<PropertyName>` tag waarmee de eigenschap wordt opgegeven die op de opgegeven locatie in de weer gave moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bf555-190">A `<WideEntry>` tag typically contains a `<PropertyName>` tag that specifies the property to be displayed at the specified location in the view.</span></span> <span data-ttu-id="bf555-191">De `<PropertyName>` tag kan een `<FormatString>` tag bevatten die aangeeft hoe de eigenschap moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bf555-191">The `<PropertyName>` tag can contain a `<FormatString>` tag that specifies how the property is to be displayed.</span></span>

### <a name="customcontrol-tag"></a><span data-ttu-id="bf555-192">CustomControl-tag</span><span class="sxs-lookup"><span data-stu-id="bf555-192">CustomControl tag</span></span>

<span data-ttu-id="bf555-193">`<CustomControl>`Met de tag kunt u een script blok gebruiken om een indeling te definiëren.</span><span class="sxs-lookup"><span data-stu-id="bf555-193">The `<CustomControl>` tag lets you use a script block to define a format.</span></span> <span data-ttu-id="bf555-194">Een `<CustomControl>` tag bevat doorgaans een `<CustomEntries>` tag die meerdere `<CustomEntry>` labels bevat.</span><span class="sxs-lookup"><span data-stu-id="bf555-194">A `<CustomControl>` tag typically contains a `<CustomEntries>` tag that contains multiple `<CustomEntry>` tags.</span></span> <span data-ttu-id="bf555-195">Elke `<CustomEntry>` tag bevat een `<CustomItem>` tag die diverse Tags kan bevatten waarin de inhoud en opmaak van de opgegeven locatie in de weer gave, inclusief `<Text>` ,, `<Indentation>` `<ExpressionBinding>` , en de `<NewLine>` Tags, worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf555-195">Each `<CustomEntry>` tag contains a `<CustomItem>` tag that can contain a variety of tags that specify contents and formatting of the specified location in the view, including `<Text>`, `<Indentation>`, `<ExpressionBinding>`, and `<NewLine>` tags.</span></span>

## <a name="tracing-formatps1xml-file-use"></a><span data-ttu-id="bf555-196">Het gebruik van Format.ps1XML-bestand traceren</span><span class="sxs-lookup"><span data-stu-id="bf555-196">Tracing Format.ps1xml file use</span></span>

<span data-ttu-id="bf555-197">Als u fouten wilt detecteren tijdens het laden of Toep assen van `Format.ps1xml` bestanden, gebruikt u de `Trace-Command` cmdlet met een van de volgende indelings onderdelen als de waarde van de para meter **name** :</span><span class="sxs-lookup"><span data-stu-id="bf555-197">To detect errors in the loading or application of `Format.ps1xml` files, use the `Trace-Command` cmdlet with any of the following format components as the value of the **Name** parameter:</span></span>

- <span data-ttu-id="bf555-198">FormatFileLoading</span><span class="sxs-lookup"><span data-stu-id="bf555-198">FormatFileLoading</span></span>
- <span data-ttu-id="bf555-199">FormatViewBinding</span><span class="sxs-lookup"><span data-stu-id="bf555-199">FormatViewBinding</span></span>

<span data-ttu-id="bf555-200">Zie [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) en [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bf555-200">For more information, see [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) and [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span></span>

## <a name="signing-a-formatps1xml-file"></a><span data-ttu-id="bf555-201">Een Format.ps1XML-bestand ondertekenen</span><span class="sxs-lookup"><span data-stu-id="bf555-201">Signing a Format.ps1xml file</span></span>

<span data-ttu-id="bf555-202">Als u de gebruikers van uw bestand wilt beveiligen, moet u `Format.ps1xml` het bestand ondertekenen met een digitale hand tekening.</span><span class="sxs-lookup"><span data-stu-id="bf555-202">To protect the users of your `Format.ps1xml` file, sign the file using a digital signature.</span></span> <span data-ttu-id="bf555-203">Zie [about_Signing](about_Signing.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bf555-203">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="sample-xml-for-a-format-table-custom-view"></a><span data-ttu-id="bf555-204">Voor beeld-XML voor een aangepaste weer gave Format-Table</span><span class="sxs-lookup"><span data-stu-id="bf555-204">Sample XML for a Format-Table custom view</span></span>

<span data-ttu-id="bf555-205">Met het volgende XML-voor beeld maakt u een `Format-Table` aangepaste weer gave voor de objecten **System. io. DirectoryInfo** en **System. io. file info** die zijn gemaakt door `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="bf555-205">The following XML sample creates a `Format-Table` custom view for the **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span> <span data-ttu-id="bf555-206">De aangepaste weer gave heet **mygciview** en voegt de kolom **CreationTime** toe aan de tabel.</span><span class="sxs-lookup"><span data-stu-id="bf555-206">The custom view is named **mygciview** and adds the **CreationTime** column to the table.</span></span>

<span data-ttu-id="bf555-207">Als u de aangepaste weer gave wilt maken, gebruikt u de `Get-FormatData` `Export-FormatData` cmdlets en om een bestand te genereren `.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="bf555-207">To create the custom view, use the `Get-FormatData` and `Export-FormatData` cmdlets to generate a `.ps1xml` file.</span></span> <span data-ttu-id="bf555-208">Bewerk vervolgens het `.ps1xml` bestand om de code te maken voor uw aangepaste weer gave.</span><span class="sxs-lookup"><span data-stu-id="bf555-208">Then, edit your `.ps1xml` file to create the code for your custom view.</span></span> <span data-ttu-id="bf555-209">Het `.ps1xml` bestand kan worden opgeslagen in een map waartoe Power shell toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="bf555-209">The `.ps1xml` file can be stored in any directory that PowerShell can access.</span></span> <span data-ttu-id="bf555-210">Bijvoorbeeld een submap van `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="bf555-210">For example, a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="bf555-211">Nadat het `.ps1xml` bestand is gemaakt, gebruikt `Update-FormatData` u de cmdlet om de weer gave in de huidige Power shell-sessie op te geven.</span><span class="sxs-lookup"><span data-stu-id="bf555-211">After the `.ps1xml` file is created, use the `Update-FormatData` cmdlet to include the view in the current PowerShell session.</span></span> <span data-ttu-id="bf555-212">U kunt ook de opdracht bijwerken toevoegen aan uw Power shell-profiel als u de weer gave beschikbaar wilt hebben in alle Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="bf555-212">Or, add the update command to your PowerShell profile if you need the view available in all PowerShell sessions.</span></span>

<span data-ttu-id="bf555-213">In dit voor beeld moet de aangepaste weer gave de tabel indeling gebruiken, anders `Format-Table` mislukt.</span><span class="sxs-lookup"><span data-stu-id="bf555-213">For this example, the custom view must use the table format, otherwise, `Format-Table` fails.</span></span>

<span data-ttu-id="bf555-214">Gebruik `Format-Table` met de **weer gave** -para meter om de naam van de aangepaste weer gave op te geven, **mygciview** , en de uitvoer van de tabel op te maken met de kolom **CreationTime** .</span><span class="sxs-lookup"><span data-stu-id="bf555-214">Use `Format-Table` with the **View** parameter to specify the custom view's name, **mygciview** , and format the table's output with the **CreationTime** column.</span></span> <span data-ttu-id="bf555-215">Zie [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)voor een voor beeld van hoe de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bf555-215">For an example of how the command is run, see [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

> [!NOTE]
> <span data-ttu-id="bf555-216">Hoewel u de XML-opmaak van de bron code kunt ophalen om een aangepaste weer gave te maken, is er mogelijk meer ontwikkel aars nodig om het gewenste resultaat te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="bf555-216">Although you can get the formatting XML from the source code to create a custom view, more development might be needed to get the desired result.</span></span>

<span data-ttu-id="bf555-217">In de volgende `Get-FormatData` opdracht is er een alternatief voor de para meter **PowerShellVersion** om ervoor te zorgen dat alle lokale opmaak gegevens worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bf555-217">In the following `Get-FormatData` command, there's an alternative for the **PowerShellVersion** parameter to ensure that all local formatting information is returned.</span></span> <span data-ttu-id="bf555-218">Gebruiken `-PowerShellVersion $PSVersionTable.PSVersion` in plaats van een specifieke Power shell-versie.</span><span class="sxs-lookup"><span data-stu-id="bf555-218">Use `-PowerShellVersion $PSVersionTable.PSVersion` rather than a specific PowerShell version.</span></span>

```powershell
Get-FormatData -PowerShellVersion 5.1 -TypeName System.IO.DirectoryInfo |
   Export-FormatData -Path ./Mygciview.Format.ps1xml
Update-FormatData -AppendPath ./Mygciview.Format.ps1xml
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>mygciview</Name>
      <ViewSelectedBy>
        <TypeName>System.IO.DirectoryInfo</TypeName>
        <TypeName>System.IO.FileInfo</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>PSParentPath</PropertyName>
      </GroupBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Label>Mode</Label>
            <Width>7</Width>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>LastWriteTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>CreationTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Length</Label>
            <Width>14</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Name</Label>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <Wrap />
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>ModeWithoutHardLink</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>LastWriteTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>CreationTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Length</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Name</PropertyName>
              </TableColumnItem>
            </TableColumnItems>
          </TableRowEntry>
        </TableRowEntries>
      </TableControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="bf555-219">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bf555-219">See also</span></span>

[<span data-ttu-id="bf555-220">Exporteren-FormatData</span><span class="sxs-lookup"><span data-stu-id="bf555-220">Export-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[<span data-ttu-id="bf555-221">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="bf555-221">Get-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[<span data-ttu-id="bf555-222">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="bf555-222">Get-TraceSource</span></span>](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[<span data-ttu-id="bf555-223">Naslaginformatie over XML voor opmaakschema</span><span class="sxs-lookup"><span data-stu-id="bf555-223">Format Schema XML Reference</span></span>](/powershell/scripting/developer/format/format-schema-xml-reference)

[<span data-ttu-id="bf555-224">Tracering-opdracht</span><span class="sxs-lookup"><span data-stu-id="bf555-224">Trace-Command</span></span>](xref:Microsoft.PowerShell.Utility.Trace-Command)

[<span data-ttu-id="bf555-225">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="bf555-225">Update-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[<span data-ttu-id="bf555-226">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="bf555-226">Writing a PowerShell Formatting File</span></span>](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
