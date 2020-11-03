---
description: De `Format.ps1xml` bestanden in Power shell definiëren de standaard weergave van objecten in de Power shell-console. U kunt uw eigen `Format.ps1xml` bestanden maken om de weer gave van objecten te wijzigen of om standaard weer gaven te definiëren voor nieuwe object typen die u in Power Shell maakt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1XML
ms.openlocfilehash: be88007d23ab98b9c2f707b77f9c43578ba9887b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252619"
---
# <a name="about-formatps1xml"></a><span data-ttu-id="db677-105">Over Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="db677-105">About Format.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="db677-106">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="db677-106">Short description</span></span>

<span data-ttu-id="db677-107">De `Format.ps1xml` bestanden in Power shell definiëren de standaard weergave van objecten in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="db677-107">The `Format.ps1xml` files in PowerShell define the default display of objects in the PowerShell console.</span></span> <span data-ttu-id="db677-108">U kunt uw eigen `Format.ps1xml` bestanden maken om de weer gave van objecten te wijzigen of om standaard weer gaven te definiëren voor nieuwe object typen die u in Power Shell maakt.</span><span class="sxs-lookup"><span data-stu-id="db677-108">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="db677-109">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="db677-109">Long description</span></span>

<span data-ttu-id="db677-110">De `Format.ps1xml` bestanden in Power shell definiëren de standaard weergave van objecten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="db677-110">The `Format.ps1xml` files in PowerShell define the default display of objects in PowerShell.</span></span> <span data-ttu-id="db677-111">U kunt uw eigen `Format.ps1xml` bestanden maken om de weer gave van objecten te wijzigen of om standaard weer gaven te definiëren voor nieuwe object typen die u in Power Shell maakt.</span><span class="sxs-lookup"><span data-stu-id="db677-111">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

<span data-ttu-id="db677-112">Wanneer Power shell een object weergeeft, worden de gegevens in gestructureerde indelings bestanden gebruikt om de standaard weergave van het object te bepalen.</span><span class="sxs-lookup"><span data-stu-id="db677-112">When PowerShell displays an object, it uses the data in structured formatting files to determine the default display of the object.</span></span> <span data-ttu-id="db677-113">De gegevens in de indelings bestanden bepalen of het object wordt weer gegeven in een tabel of in een lijst en bepaalt welke eigenschappen standaard worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="db677-113">The data in the formatting files determines whether the object is rendered in a table or in a list, and it determines which properties are displayed by default.</span></span>

<span data-ttu-id="db677-114">De opmaak is alleen van invloed op de weer gave.</span><span class="sxs-lookup"><span data-stu-id="db677-114">The formatting affects the display only.</span></span> <span data-ttu-id="db677-115">Dit heeft geen invloed op welke object eigenschappen worden door gegeven aan de pijp lijn of hoe ze worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="db677-115">It doesn't affect which object properties are passed down the pipeline or how they're passed.</span></span> <span data-ttu-id="db677-116">`Format.ps1xml` bestanden kunnen niet worden gebruikt om de uitvoer indeling voor hash-tabellen aan te passen.</span><span class="sxs-lookup"><span data-stu-id="db677-116">`Format.ps1xml` files can't be used to customize the output format for hash tables.</span></span>

<span data-ttu-id="db677-117">Power shell bevat zeven indelings bestanden.</span><span class="sxs-lookup"><span data-stu-id="db677-117">PowerShell includes seven formatting files.</span></span> <span data-ttu-id="db677-118">Deze bestanden bevinden zich in de installatiemap ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="db677-118">These files are located in the installation directory (`$PSHOME`).</span></span> <span data-ttu-id="db677-119">Elk bestand definieert de weer gave van een groep Microsoft .NET Framework-objecten:</span><span class="sxs-lookup"><span data-stu-id="db677-119">Each file defines the display of a group of Microsoft .NET Framework objects:</span></span>

1. `Certificate.Format.ps1xml`

   <span data-ttu-id="db677-120">Objecten in het certificaat archief, zoals X. 509-certificaten en certificaat archieven.</span><span class="sxs-lookup"><span data-stu-id="db677-120">Objects in the Certificate store, such as X.509 certificates and certificate stores.</span></span>

1. `DotNetTypes.Format.ps1xml`

   <span data-ttu-id="db677-121">Andere .NET Framework typen, zoals Culture info-, FileVersionInfo-en EventLogEntry-objecten.</span><span class="sxs-lookup"><span data-stu-id="db677-121">Other .NET Framework types, such as CultureInfo, FileVersionInfo, and EventLogEntry objects.</span></span>

1. `FileSystem.Format.ps1xml`

   <span data-ttu-id="db677-122">Bestandssysteem objecten, zoals bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="db677-122">File system objects, such as files and directories.</span></span>

1. `Help.Format.ps1xml`

   <span data-ttu-id="db677-123">Help-weer gaven, zoals gedetailleerde en volledige weer gaven, para meters en voor beelden.</span><span class="sxs-lookup"><span data-stu-id="db677-123">Help views, such as detailed and full views, parameters, and examples.</span></span>

1. `PowerShellCore.Format.ps1xml`

   <span data-ttu-id="db677-124">Objecten die worden gegenereerd door Power shell core-cmdlets, zoals `Get-Member` en `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="db677-124">Objects generated by PowerShell core cmdlets, such as `Get-Member` and `Get-History`.</span></span>

1. `PowerShellTrace.Format.ps1xml`

   <span data-ttu-id="db677-125">Traceer objecten, zoals die worden gegenereerd door de `Trace-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="db677-125">Trace objects, such as those generated by the `Trace-Command` cmdlet.</span></span>

1. `Registry.Format.ps1xml`

   <span data-ttu-id="db677-126">Register objecten, zoals sleutels en vermeldingen.</span><span class="sxs-lookup"><span data-stu-id="db677-126">Registry objects, such as keys and entries.</span></span>

<span data-ttu-id="db677-127">Een opmaak bestand kan vier verschillende weer gaven van elk object definiëren:</span><span class="sxs-lookup"><span data-stu-id="db677-127">A formatting file can define four different views of each object:</span></span>

- <span data-ttu-id="db677-128">Tabel</span><span class="sxs-lookup"><span data-stu-id="db677-128">Table</span></span>
- <span data-ttu-id="db677-129">Lijst</span><span class="sxs-lookup"><span data-stu-id="db677-129">List</span></span>
- <span data-ttu-id="db677-130">Organisatiebreed</span><span class="sxs-lookup"><span data-stu-id="db677-130">Wide</span></span>
- <span data-ttu-id="db677-131">Aangepast</span><span class="sxs-lookup"><span data-stu-id="db677-131">Custom</span></span>

<span data-ttu-id="db677-132">Als bijvoorbeeld de uitvoer van een `Get-ChildItem` opdracht wordt gepiped naar een `Format-List` opdracht, `Format-List` wordt de weer gave in het `FileSystem.Format.ps1xml` bestand gebruikt om te bepalen hoe het bestand en de objecten van de map als een lijst moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="db677-132">For example, when the output of a `Get-ChildItem` command is piped to a `Format-List` command, `Format-List` uses the view in the `FileSystem.Format.ps1xml` file to determine how to display the file and folder objects as a list.</span></span>

<span data-ttu-id="db677-133">Wanneer een opmaak bestand meer dan één weer gave van een object bevat, past Power shell de eerste weer gave toe die wordt gevonden.</span><span class="sxs-lookup"><span data-stu-id="db677-133">When a formatting file includes more than one view of an object, PowerShell applies the first view that it finds.</span></span>

<span data-ttu-id="db677-134">In een `Format.ps1xml` bestand wordt een weer gave gedefinieerd met behulp van een set XML-tags die de naam van de weer gave beschrijven, het type object waarop deze kan worden toegepast, de kolom koppen en de eigenschappen die worden weer gegeven in de hoofd tekst van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="db677-134">In a `Format.ps1xml` file, a view is defined by a set of XML tags that describe the name of the view, the type of object to which it can be applied, the column headers, and the properties that are displayed in the body of the view.</span></span> <span data-ttu-id="db677-135">De indeling in `Format.ps1xml` bestanden wordt alleen toegepast voordat de gegevens aan de gebruiker worden gepresenteerd.</span><span class="sxs-lookup"><span data-stu-id="db677-135">The format in `Format.ps1xml` files is applied just before the data is presented to the user.</span></span>

## <a name="creating-new-formatps1xml-files"></a><span data-ttu-id="db677-136">Nieuwe Format.ps1XML-bestanden maken</span><span class="sxs-lookup"><span data-stu-id="db677-136">Creating new Format.ps1xml files</span></span>

<span data-ttu-id="db677-137">De `.ps1xml` bestanden die worden geïnstalleerd met Power shell, zijn digitaal ondertekend om knoeien te voor komen, omdat de opmaak script blokken kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="db677-137">The `.ps1xml` files that are installed with PowerShell are digitally signed to prevent tampering because the formatting can include script blocks.</span></span> <span data-ttu-id="db677-138">Als u de weergave opmaak van een bestaande object weergave wilt wijzigen of als u weer gaven wilt toevoegen voor nieuwe objecten, maakt u uw eigen `Format.ps1xml` bestanden en voegt u deze toe aan uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="db677-138">To change the display format of an existing object view, or to add views for new objects, create your own `Format.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="db677-139">Als u een nieuw bestand wilt maken, kopieert u een bestaand `Format.ps1xml` bestand.</span><span class="sxs-lookup"><span data-stu-id="db677-139">To create a new file, copy an existing `Format.ps1xml` file.</span></span> <span data-ttu-id="db677-140">Het nieuwe bestand kan een wille keurige naam hebben, maar moet een `.ps1xml` bestandsnaam extensie hebben.</span><span class="sxs-lookup"><span data-stu-id="db677-140">The new file can have any name, but it must have a `.ps1xml` file name extension.</span></span> <span data-ttu-id="db677-141">U kunt het nieuwe bestand in elke map plaatsen die toegankelijk is voor Power shell, maar het is handig om de bestanden in de Power shell-installatiemap ( `$PSHOME` ) of in een submap van de installatiemap te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="db677-141">You can place the new file in any directory that is accessible to PowerShell, but it's useful to place the files in the PowerShell installation directory (`$PSHOME`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="db677-142">Als u de opmaak van een huidige weer gave wilt wijzigen, gaat u naar de weer gave in het opmaak bestand en gebruikt u vervolgens de labels om de weer gave te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="db677-142">To change the formatting of a current view, locate the view in the formatting file, and then use the tags to change the view.</span></span> <span data-ttu-id="db677-143">Als u een weer gave voor een nieuw object type wilt maken, maakt u een nieuwe weer gave of gebruikt u een bestaande weer gave als een model.</span><span class="sxs-lookup"><span data-stu-id="db677-143">To create a view for a new object type, create a new view, or use an existing view as a model.</span></span> <span data-ttu-id="db677-144">De tags worden in de volgende sectie beschreven.</span><span class="sxs-lookup"><span data-stu-id="db677-144">The tags are described in the next section.</span></span> <span data-ttu-id="db677-145">U kunt vervolgens alle andere weer gaven in het bestand verwijderen, zodat de wijzigingen duidelijk zijn voor iedereen die het bestand bekijkt.</span><span class="sxs-lookup"><span data-stu-id="db677-145">You can then delete all the other views in the file so that the changes are obvious to anyone examining the file.</span></span>

<span data-ttu-id="db677-146">Nadat u de wijzigingen hebt opgeslagen, gebruikt u de `Update-FormatData` cmdlet om het nieuwe bestand aan uw Power shell-sessie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="db677-146">After you save the changes, use the `Update-FormatData` cmdlet to add the new file to your PowerShell session.</span></span> <span data-ttu-id="db677-147">Als u wilt dat de weer gave voor rang krijgt boven een weer gave die is gedefinieerd in de ingebouwde bestanden, gebruikt u de para meter **PrependPath** .</span><span class="sxs-lookup"><span data-stu-id="db677-147">If you want your view to take precedence over a view defined in the built-in files, use the **PrependPath** parameter.</span></span>
<span data-ttu-id="db677-148">`Update-FormatData` alleen van invloed op de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="db677-148">`Update-FormatData` affects only the current session.</span></span> <span data-ttu-id="db677-149">Als u de wijziging wilt aanbrengen in alle toekomstige sessies, voegt u de `Update-FormatData` opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="db677-149">To make the change to all future sessions, add the `Update-FormatData` command to your PowerShell profile.</span></span>

### <a name="example-adding-calendar-data-to-culture-objects"></a><span data-ttu-id="db677-150">Voor beeld: agenda gegevens toevoegen aan cultuur objecten</span><span class="sxs-lookup"><span data-stu-id="db677-150">Example: Adding calendar data to culture objects</span></span>

<span data-ttu-id="db677-151">In dit voor beeld ziet u hoe u de indeling wijzigt van de cultuur-objecten **System. Globalization. Culture info** die zijn gegenereerd door de `Get-Culture` cmdlet in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="db677-151">This example shows how to change the formatting of the culture objects **System.Globalization.CultureInfo** generated by the `Get-Culture` cmdlet in the current PowerShell session.</span></span> <span data-ttu-id="db677-152">Met de opdrachten in het voor beeld wordt de eigenschap **Calendar** toegevoegd aan de standaard tabel weergave weer gave van cultuur-objecten.</span><span class="sxs-lookup"><span data-stu-id="db677-152">The commands in the example add the **Calendar** property to the default table view display of culture objects.</span></span>

<span data-ttu-id="db677-153">De eerste stap is het zoeken naar het `Format.ps1xml` bestand dat de huidige weer gave van de cultuur-objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="db677-153">The first step is to find the `Format.ps1xml` file that contains the current view of the culture objects.</span></span> <span data-ttu-id="db677-154">Met de volgende `Select-String` opdracht wordt het bestand gevonden:</span><span class="sxs-lookup"><span data-stu-id="db677-154">The following `Select-String` command finds the file:</span></span>

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.Globalization.CultureInfo"
}

Select-String @Parms
```

```Output
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:113:
     <Name>System.Globalization.CultureInfo</Name>
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:115:
<TypeName>System.Globalization.CultureInfo</TypeName>
```

<span data-ttu-id="db677-155">Met deze opdracht wordt de definitie in het bestand verstaan `DotNetTypes.Format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="db677-155">This command reveals that the definition is in the `DotNetTypes.Format.ps1xml` file.</span></span>

<span data-ttu-id="db677-156">Met de volgende opdracht wordt de bestands inhoud naar een nieuw bestand gekopieerd `MyDotNetTypes.Format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="db677-156">The next command copies the file contents to a new file, `MyDotNetTypes.Format.ps1xml`.</span></span>

```powershell
Copy-Item $PSHome\DotNetTypes.format.ps1xml MyDotNetTypes.Format.ps1xml
```

<span data-ttu-id="db677-157">Open het `MyDotNetTypes.Format.ps1xml` bestand in een XML-of tekst editor, zoals Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="db677-157">Open the `MyDotNetTypes.Format.ps1xml` file in any XML or text editor, such as Visual Studio Code.</span></span> <span data-ttu-id="db677-158">Zoek de sectie **System. Globalization. Culture info** -object.</span><span class="sxs-lookup"><span data-stu-id="db677-158">Find the **System.Globalization.CultureInfo** object section.</span></span> <span data-ttu-id="db677-159">De volgende XML definieert de weer gaven van het **Culture info** -object.</span><span class="sxs-lookup"><span data-stu-id="db677-159">The following XML defines the views of the **CultureInfo** object.</span></span> <span data-ttu-id="db677-160">Het object heeft alleen een **TableControl** -weer gave.</span><span class="sxs-lookup"><span data-stu-id="db677-160">The object has only a **TableControl** view.</span></span>

```xml
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
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
```

<span data-ttu-id="db677-161">De rest van het bestand verwijderen, met uitzonde ring van de `<?xml>` Tags openen, `<Configuration>` ,, en `<ViewDefinitions>` Sluiten `<ViewDefinitions>` en `<Configuration>` Tags.</span><span class="sxs-lookup"><span data-stu-id="db677-161">Delete the remainder of the file, except for the opening `<?xml>`, `<Configuration>`, and `<ViewDefinitions>` tags and the closing `<ViewDefinitions>` and `<Configuration>` tags.</span></span> <span data-ttu-id="db677-162">Als er een digitale hand tekening is, verwijdert u deze uit uw aangepaste `Format.ps1xml` bestand.</span><span class="sxs-lookup"><span data-stu-id="db677-162">If there is a digital signature, delete it from your custom `Format.ps1xml`file.</span></span>

<span data-ttu-id="db677-163">Het `MyDotNetTypes.Format.ps1xml` bestand moet er nu uitzien als in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="db677-163">The `MyDotNetTypes.Format.ps1xml` file should now look like the following sample:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
<ViewDefinitions>
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
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
      <TableColumnHeader/>
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

<span data-ttu-id="db677-164">Maak een nieuwe kolom voor de eigenschap **Calendar** door een nieuwe set tags toe te voegen `<TableColumnHeader>` .</span><span class="sxs-lookup"><span data-stu-id="db677-164">Create a new column for the **Calendar** property by adding a new set of `<TableColumnHeader>` tags.</span></span> <span data-ttu-id="db677-165">De waarde van de eigenschap **Calendar** kan lang zijn. Geef dus een waarde van 45 tekens op als de `<Width>` .</span><span class="sxs-lookup"><span data-stu-id="db677-165">The value of the **Calendar** property can be long, so specify a value of 45 characters as the `<Width>`.</span></span>

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

<span data-ttu-id="db677-166">Voeg een nieuw kolom item toe voor **kalenders** in de tabel rijen met behulp van de `<TableColumnItem>` `<PropertyName` Tags en:</span><span class="sxs-lookup"><span data-stu-id="db677-166">Add a new column item for **Calendar** in the table rows using the `<TableColumnItem>` and `<PropertyName` tags:</span></span>

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

<span data-ttu-id="db677-167">Sla het bestand op en sluit het.</span><span class="sxs-lookup"><span data-stu-id="db677-167">Save and close the file.</span></span> <span data-ttu-id="db677-168">Gebruik `Update-FormatData` om het nieuwe indelings bestand aan de huidige Power shell-sessie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="db677-168">Use `Update-FormatData` to add the new format file to the current PowerShell session.</span></span>

<span data-ttu-id="db677-169">In dit voor beeld wordt de para meter **PrependPath** gebruikt om het nieuwe bestand in een hogere volg orde dan het oorspronkelijke bestand te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="db677-169">This example uses the **PrependPath** parameter to place the new file in a higher precedence order than the original file.</span></span> <span data-ttu-id="db677-170">Zie [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="db677-170">For more information, see [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span></span>

```powershell
Update-FormatData -PrependPath $PSHOME\MyDotNetTypes.Format.ps1xml
```

<span data-ttu-id="db677-171">Als u de wijziging wilt testen, typt `Get-Culture` en controleert u de uitvoer die de eigenschap **Calendar** bevat.</span><span class="sxs-lookup"><span data-stu-id="db677-171">To test the change, type `Get-Culture` and review the output that includes the **Calendar** property.</span></span>

```powershell
Get-Culture
```

```Output
LCID Name  Calendar                               DisplayName
---- ----  --------                               -----------
1033 en-US System.Globalization.GregorianCalendar English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a><span data-ttu-id="db677-172">De XML in Format.ps1XML-bestanden</span><span class="sxs-lookup"><span data-stu-id="db677-172">The XML in Format.ps1xml files</span></span>

<span data-ttu-id="db677-173">De volledige schema definitie vindt u in [Format. XSD](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in de Power shell-bron code opslagplaats op github.</span><span class="sxs-lookup"><span data-stu-id="db677-173">The full schema definition can be found in [Format.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="db677-174">De sectie **ViewDefinitions** van elk `Format.ps1xml` bestand bevat de `<View>` Tags waarmee elke weer gave wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="db677-174">The **ViewDefinitions** section of each `Format.ps1xml` file contains the `<View>` tags that define each view.</span></span> <span data-ttu-id="db677-175">Een typische `<View>` tag bevat de volgende Tags:</span><span class="sxs-lookup"><span data-stu-id="db677-175">A typical `<View>` tag includes the following tags:</span></span>

- <span data-ttu-id="db677-176">`<Name>` Hiermee wordt de naam van de weer gave aangeduid.</span><span class="sxs-lookup"><span data-stu-id="db677-176">`<Name>` identifies the name of the view.</span></span>
- <span data-ttu-id="db677-177">`<ViewSelectedBy>` Hiermee geeft u het object type of de typen waarop de weer gave van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="db677-177">`<ViewSelectedBy>` specifies the object type or types to which the view applies.</span></span>
- <span data-ttu-id="db677-178">`<GroupBy>` Hiermee wordt aangegeven hoe items in de weer gave in groepen worden gecombineerd.</span><span class="sxs-lookup"><span data-stu-id="db677-178">`<GroupBy>` specifies how items in the view will be combined in groups.</span></span>
- <span data-ttu-id="db677-179">`<TableControl>`, `<ListControl>` , `<WideControl>` en `<CustomControl>` bevatten de tags die aangeven hoe elk item wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="db677-179">`<TableControl>`, `<ListControl>`, `<WideControl>`, and `<CustomControl>` contain the tags that specify how each item will be displayed.</span></span>

### <a name="viewselectedby-tag"></a><span data-ttu-id="db677-180">ViewSelectedBy-tag</span><span class="sxs-lookup"><span data-stu-id="db677-180">ViewSelectedBy tag</span></span>

<span data-ttu-id="db677-181">De `<ViewSelectedBy>` tag kan een `<TypeName>` tag bevatten voor elk object type waarop de weer gave van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="db677-181">The `<ViewSelectedBy>` tag can contain a `<TypeName>` tag for each object type to which the view applies.</span></span> <span data-ttu-id="db677-182">Het kan ook een tag bevatten `<SelectionSetName>` die verwijst naar een selectieset die elders is gedefinieerd met behulp van een `<SelectionSet>` tag.</span><span class="sxs-lookup"><span data-stu-id="db677-182">Or, it can contain a `<SelectionSetName>` tag that references a selection set that is defined elsewhere by using a `<SelectionSet>` tag.</span></span>

### <a name="groupby-tag"></a><span data-ttu-id="db677-183">GroupBy-tag</span><span class="sxs-lookup"><span data-stu-id="db677-183">GroupBy tag</span></span>

<span data-ttu-id="db677-184">Het `<GroupBy>` label bevat een `<PropertyName>` tag die de object eigenschap specificeert op basis waarvan items moeten worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="db677-184">The `<GroupBy>` tag contains a `<PropertyName>` tag that specifies the object property by which items are to be grouped.</span></span> <span data-ttu-id="db677-185">Het bevat ook een `<Label>` label dat een teken reeks opgeeft die moet worden gebruikt als label voor elke groep of een `<CustomControlName>` label dat verwijst naar een aangepast besturings element dat elders is gedefinieerd met behulp van een `<Control>` tag.</span><span class="sxs-lookup"><span data-stu-id="db677-185">It also contains either a `<Label>` tag that specifies a string to be used as a label for each group or a `<CustomControlName>` tag that references a custom control defined elsewhere using a `<Control>` tag.</span></span> <span data-ttu-id="db677-186">Het `<Control>` label bevat een `<Name>` tag en een `<CustomControl>` tag.</span><span class="sxs-lookup"><span data-stu-id="db677-186">The `<Control>` tag contains a `<Name>` tag and a `<CustomControl>` tag.</span></span>

### <a name="tablecontroltag"></a><span data-ttu-id="db677-187">TableControlTag</span><span class="sxs-lookup"><span data-stu-id="db677-187">TableControlTag</span></span>

<span data-ttu-id="db677-188">De `<TableControl>` tag bevat normaal gesp roken `<TableHeaders>` `<TableRowEntries>` labels en tags waarmee de opmaak van de koppen en rijen van de tabel worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="db677-188">The `<TableControl>` tag typically contains `<TableHeaders>` and `<TableRowEntries>` tags that define the formatting for the table's heads and rows.</span></span> <span data-ttu-id="db677-189">Het `<TableHeaders>` label bevat doorgaans `<TableColumnHeader>` Tags die de `<Label>` `<Width>` Tags, en bevatten `<Alignment>` .</span><span class="sxs-lookup"><span data-stu-id="db677-189">The `<TableHeaders>` tag typically contains `<TableColumnHeader>` tags that contain `<Label>`, `<Width>`, and `<Alignment>` tags.</span></span> <span data-ttu-id="db677-190">Het `<TableRowEntries>` label bevat `<TableRowEntry>` labels voor elke rij in de tabel.</span><span class="sxs-lookup"><span data-stu-id="db677-190">The `<TableRowEntries>` tag contains `<TableRowEntry>` tags for each row in the table.</span></span> <span data-ttu-id="db677-191">Het `<TableRowEntry>` label bevat een `<TableColumnItems>` label dat een `<TableColumnItem>` tag bevat voor elke kolom in de rij.</span><span class="sxs-lookup"><span data-stu-id="db677-191">The `<TableRowEntry>` tag contains a `<TableColumnItems>` tag that contains a `<TableColumnItem>` tag for each column in the row.</span></span> <span data-ttu-id="db677-192">Normaal gesp roken `<TableColumnItem>` bevat de tag een `<PropertyName>` tag die de object eigenschap identificeert die moet worden weer gegeven op de gedefinieerde locatie of een label met een `<ScriptBlock>` script code die een resultaat berekent dat op de locatie moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="db677-192">Typically, the `<TableColumnItem>` tag contains either a `<PropertyName>` tag that identifies the object property to be displayed in the defined location, or a `<ScriptBlock>` tag that contains script code that calculates a result that is to be displayed in the location.</span></span>

> [!NOTE]
> <span data-ttu-id="db677-193">Script blokken kunnen ook elders worden gebruikt in locaties waar berekende resultaten nuttig kunnen zijn.</span><span class="sxs-lookup"><span data-stu-id="db677-193">Script blocks can also be used elsewhere in locations where calculated results can be useful.</span></span>

<span data-ttu-id="db677-194">De `<TableColumnItem>` tag kan ook een `<FormatString>` tag bevatten die aangeeft hoe de eigenschap of de berekende resultaten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="db677-194">The `<TableColumnItem>` tag can also contain a `<FormatString>` tag that specifies how the property or the calculated results will be displayed.</span></span>

### <a name="listcontrol-tag"></a><span data-ttu-id="db677-195">ListControl-tag</span><span class="sxs-lookup"><span data-stu-id="db677-195">ListControl tag</span></span>

<span data-ttu-id="db677-196">De `<ListControl>` tag bevat meestal een `<ListEntries>` tag.</span><span class="sxs-lookup"><span data-stu-id="db677-196">The `<ListControl>` tag typically contains a `<ListEntries>` tag.</span></span> <span data-ttu-id="db677-197">Het `<ListEntries>` label bevat een `<ListEntry>` tag.</span><span class="sxs-lookup"><span data-stu-id="db677-197">The `<ListEntries>` tag contains a `<ListEntry>` tag.</span></span> <span data-ttu-id="db677-198">Het `<ListEntry>` label bevat een `<ListItems>` tag.</span><span class="sxs-lookup"><span data-stu-id="db677-198">The `<ListEntry>` tag contains a `<ListItems>` tag.</span></span> <span data-ttu-id="db677-199">Het `<ListItems>` label bevat `<ListItem>` Tags die labels bevatten `<PropertyName>` .</span><span class="sxs-lookup"><span data-stu-id="db677-199">The `<ListItems>` tag contains `<ListItem>` tags, which contain `<PropertyName>` tags.</span></span> <span data-ttu-id="db677-200">De `<PropertyName>` labels geven de object eigenschap op die moet worden weer gegeven op de opgegeven locatie in de lijst.</span><span class="sxs-lookup"><span data-stu-id="db677-200">The `<PropertyName>` tags specify the object property to be displayed at the specified location in the list.</span></span> <span data-ttu-id="db677-201">Als de weergave selectie is gedefinieerd met behulp van een selectieset, `<ListControl>` `<ListEntry>` kunnen de tags en ook een tag bevatten `<EntrySelectedBy>` die een of meer `<TypeName>` labels bevat.</span><span class="sxs-lookup"><span data-stu-id="db677-201">If the view selection is defined using a selection set, the `<ListControl>` and `<ListEntry>` tags can also contain an `<EntrySelectedBy>` tag that contains one or more `<TypeName>` tags.</span></span> <span data-ttu-id="db677-202">Deze `<TypeName>` Tags geven het object type op waarvan de `<ListControl>` tag is bedoeld om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="db677-202">These `<TypeName>` tags specify the object type that the `<ListControl>` tag is intended to display.</span></span>

### <a name="widecontrol-tag"></a><span data-ttu-id="db677-203">WideControl-tag</span><span class="sxs-lookup"><span data-stu-id="db677-203">WideControl tag</span></span>

<span data-ttu-id="db677-204">De `<WideControl>` tag bevat meestal een `<WideEntries>` tag.</span><span class="sxs-lookup"><span data-stu-id="db677-204">The `<WideControl>` tag typically contains a `<WideEntries>` tag.</span></span> <span data-ttu-id="db677-205">Het `<WideEntries>` label bevat een of meer `<WideEntry>` Tags.</span><span class="sxs-lookup"><span data-stu-id="db677-205">The `<WideEntries>` tag contains one or more `<WideEntry>` tags.</span></span> <span data-ttu-id="db677-206">Een `<WideEntry>` tag bevat meestal een `<PropertyName>` tag waarmee de eigenschap wordt opgegeven die op de opgegeven locatie in de weer gave moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="db677-206">A `<WideEntry>` tag typically contains a `<PropertyName>` tag that specifies the property to be displayed at the specified location in the view.</span></span> <span data-ttu-id="db677-207">De `<PropertyName>` tag kan een `<FormatString>` tag bevatten die aangeeft hoe de eigenschap moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="db677-207">The `<PropertyName>` tag can contain a `<FormatString>` tag that specifies how the property is to be displayed.</span></span>

### <a name="customcontrol-tag"></a><span data-ttu-id="db677-208">CustomControl-tag</span><span class="sxs-lookup"><span data-stu-id="db677-208">CustomControl tag</span></span>

<span data-ttu-id="db677-209">`<CustomControl>`Met de tag kunt u een script blok gebruiken om een indeling te definiëren.</span><span class="sxs-lookup"><span data-stu-id="db677-209">The `<CustomControl>` tag lets you use a script block to define a format.</span></span> <span data-ttu-id="db677-210">Een `<CustomControl>` tag bevat doorgaans een `<CustomEntries>` tag die meerdere `<CustomEntry>` labels bevat.</span><span class="sxs-lookup"><span data-stu-id="db677-210">A `<CustomControl>` tag typically contains a `<CustomEntries>` tag that contains multiple `<CustomEntry>` tags.</span></span> <span data-ttu-id="db677-211">Elke `<CustomEntry>` tag bevat een `<CustomItem>` tag die diverse Tags kan bevatten waarin de inhoud en opmaak van de opgegeven locatie in de weer gave, inclusief `<Text>` ,, `<Indentation>` `<ExpressionBinding>` , en de `<NewLine>` Tags, worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="db677-211">Each `<CustomEntry>` tag contains a `<CustomItem>` tag that can contain a variety of tags that specify contents and formatting of the specified location in the view, including `<Text>`, `<Indentation>`, `<ExpressionBinding>`, and `<NewLine>` tags.</span></span>

## <a name="default-displays-in-typesps1xml"></a><span data-ttu-id="db677-212">Standaard wordt weer gegeven in Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="db677-212">Default displays in Types.ps1xml</span></span>

<span data-ttu-id="db677-213">De standaard weer gaven van sommige basis object typen worden gedefinieerd in het `Types.ps1xml` bestand in de `$PSHOME` map.</span><span class="sxs-lookup"><span data-stu-id="db677-213">The default displays of some basic object types are defined in the `Types.ps1xml` file in the `$PSHOME` directory.</span></span> <span data-ttu-id="db677-214">De knoop punten hebben de naam **PsStandardMembers** en de subknooppunten gebruiken een van de volgende Tags:</span><span class="sxs-lookup"><span data-stu-id="db677-214">The nodes are named **PsStandardMembers** , and the subnodes use one of the following tags:</span></span>

- `<DefaultDisplayProperty>`
- `<DefaultDisplayPropertySet>`
- `<DefaultKeyPropertySet>`

<span data-ttu-id="db677-215">Zie [about_Types.ps1XML](about_Types.ps1xml.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="db677-215">For more information, see [about_Types.ps1xml](about_Types.ps1xml.md).</span></span>

## <a name="tracing-formatps1xml-file-use"></a><span data-ttu-id="db677-216">Het gebruik van Format.ps1XML-bestand traceren</span><span class="sxs-lookup"><span data-stu-id="db677-216">Tracing Format.ps1xml file use</span></span>

<span data-ttu-id="db677-217">Als u fouten wilt detecteren tijdens het laden of Toep assen van `Format.ps1xml` bestanden, gebruikt u de `Trace-Command` cmdlet met een van de volgende indelings onderdelen als de waarde van de para meter **name** :</span><span class="sxs-lookup"><span data-stu-id="db677-217">To detect errors in the loading or application of `Format.ps1xml` files, use the `Trace-Command` cmdlet with any of the following format components as the value of the **Name** parameter:</span></span>

- <span data-ttu-id="db677-218">FormatFileLoading</span><span class="sxs-lookup"><span data-stu-id="db677-218">FormatFileLoading</span></span>
- <span data-ttu-id="db677-219">FormatViewBinding</span><span class="sxs-lookup"><span data-stu-id="db677-219">FormatViewBinding</span></span>

<span data-ttu-id="db677-220">Zie [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) en [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="db677-220">For more information, see [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) and [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span></span>

## <a name="signing-a-formatps1xml-file"></a><span data-ttu-id="db677-221">Een Format.ps1XML-bestand ondertekenen</span><span class="sxs-lookup"><span data-stu-id="db677-221">Signing a Format.ps1xml file</span></span>

<span data-ttu-id="db677-222">Als u de gebruikers van uw bestand wilt beveiligen, moet u `Format.ps1xml` het bestand ondertekenen met een digitale hand tekening.</span><span class="sxs-lookup"><span data-stu-id="db677-222">To protect the users of your `Format.ps1xml` file, sign the file using a digital signature.</span></span> <span data-ttu-id="db677-223">Zie [about_Signing](about_Signing.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="db677-223">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="sample-xml-for-a-format-table-custom-view"></a><span data-ttu-id="db677-224">Voor beeld-XML voor een aangepaste weer gave Format-Table</span><span class="sxs-lookup"><span data-stu-id="db677-224">Sample XML for a Format-Table custom view</span></span>

<span data-ttu-id="db677-225">In het volgende voor beeld wordt een `Format-Table` aangepaste weer gave gemaakt voor de objecten **System. io. DirectoryInfo** en **System. io. file info.** `Get-ChildItem`</span><span class="sxs-lookup"><span data-stu-id="db677-225">The following sample creates a `Format-Table` custom view for the **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span> <span data-ttu-id="db677-226">De aangepaste weer gave heet **mygciview** en voegt de kolom **CreationTime** toe aan de tabel.</span><span class="sxs-lookup"><span data-stu-id="db677-226">The custom view is named **mygciview** and adds the **CreationTime** column to the table.</span></span>

<span data-ttu-id="db677-227">De aangepaste weer gave wordt gemaakt op basis van een bewerkte versie van het `FileSystem.Format.ps1xml` bestand dat is opgeslagen in `$PSHOME` power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="db677-227">The custom view is created from an edited version of the `FileSystem.Format.ps1xml` file that's stored in `$PSHOME` on PowerShell 5.1.</span></span>

<span data-ttu-id="db677-228">Nadat het aangepaste `.ps1xml` bestand is opgeslagen, gebruikt `Update-FormatData` u om de weer gave in een Power shell-sessie op te slaan.</span><span class="sxs-lookup"><span data-stu-id="db677-228">After your custom `.ps1xml` file is saved, use `Update-FormatData` to include the view in a PowerShell session.</span></span> <span data-ttu-id="db677-229">In dit voor beeld moet de aangepaste weer gave de tabel indeling gebruiken, anders `Format-Table` mislukt.</span><span class="sxs-lookup"><span data-stu-id="db677-229">For this example, the custom view must use the table format, otherwise, `Format-Table` fails.</span></span>

<span data-ttu-id="db677-230">Gebruik `Format-Table` met de **weer gave** -para meter om de naam van de aangepaste weer gave op te geven en de uitvoer van de tabel op te maken.</span><span class="sxs-lookup"><span data-stu-id="db677-230">Use `Format-Table` with the **View** parameter to specify the custom view's name and format the table's output.</span></span> <span data-ttu-id="db677-231">Zie [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)voor een voor beeld van hoe de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="db677-231">For an example of how the command is run, see [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.IO.DirectoryInfo"
}
Select-String @Parms
Copy-Item $PSHome\FileSystem.format.ps1xml .\MyFileSystem.Format.ps1xml
Update-FormatData -PrependPath $PSHOME\Format\MyFileSystem.Format.ps1xml
```

> [!NOTE]
> <span data-ttu-id="db677-232">Als u het XML-voor beeld wilt aanpassen aan de beperkingen van de regel breedte, was het nood zakelijk om een bepaalde inspringing te comprimeren en regel einden in de code te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="db677-232">To fit the XML sample within line width limitations, it was necessary to compress some indentation and use line breaks within the code.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
    <SelectionSets>
        <SelectionSet>
            <Name>FileSystemTypes</Name>
            <Types>
                <TypeName>System.IO.DirectoryInfo</TypeName>
                <TypeName>System.IO.FileInfo</TypeName>
            </Types>
        </SelectionSet>
    </SelectionSets>
<Controls>
<Control>
<Name>FileSystemTypes-GroupingFormat</Name>
<CustomControl>
 <CustomEntries>
  <CustomEntry>
    <CustomItem>
    <Frame>
    <LeftIndent>4</LeftIndent>
    <CustomItem>
    <Text AssemblyName="System.Management.Automation"
    BaseName="FileSystemProviderStrings"
    ResourceId="DirectoryDisplayGrouping"/>
    <ExpressionBinding>
     <ScriptBlock>
      $_.PSParentPath.Replace("Microsoft.PowerShell.Core\FileSystem::", "")
     </ScriptBlock>
    </ExpressionBinding>
    <NewLine/>
    </CustomItem>
    </Frame>
    </CustomItem>
    </CustomEntry>
 </CustomEntries>
</CustomControl>
</Control>
</Controls>
<ViewDefinitions>
    <View>
    <Name>mygciview</Name>
    <ViewSelectedBy>
        <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <GroupBy>
      <PropertyName>PSParentPath</PropertyName>
      <CustomControlName>FileSystemTypes-GroupingFormat</CustomControlName>
    </GroupBy>
        <TableControl>
            <TableHeaders>
                <TableColumnHeader>
                    <Label>Mode</Label>
                    <Width>7</Width>
                    <Alignment>left</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>LastWriteTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>CreationTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>Length</Label>
                    <Width>14</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader/>
            </TableHeaders>
            <TableRowEntries>
                <TableRowEntry>
                    <Wrap/>
                    <TableColumnItems>
                        <TableColumnItem>
                            <PropertyName>Mode</PropertyName>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.LastWriteTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.CreationTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
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

## <a name="see-also"></a><span data-ttu-id="db677-233">Zie ook</span><span class="sxs-lookup"><span data-stu-id="db677-233">See also</span></span>

[<span data-ttu-id="db677-234">Exporteren-FormatData</span><span class="sxs-lookup"><span data-stu-id="db677-234">Export-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[<span data-ttu-id="db677-235">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="db677-235">Get-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[<span data-ttu-id="db677-236">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="db677-236">Get-TraceSource</span></span>](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[<span data-ttu-id="db677-237">Naslaginformatie over XML voor opmaakschema</span><span class="sxs-lookup"><span data-stu-id="db677-237">Format Schema XML Reference</span></span>](/powershell/scripting/developer/format/format-schema-xml-reference)

[<span data-ttu-id="db677-238">Tracering-opdracht</span><span class="sxs-lookup"><span data-stu-id="db677-238">Trace-Command</span></span>](xref:Microsoft.PowerShell.Utility.Trace-Command)

[<span data-ttu-id="db677-239">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="db677-239">Update-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[<span data-ttu-id="db677-240">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="db677-240">Writing a PowerShell Formatting File</span></span>](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
