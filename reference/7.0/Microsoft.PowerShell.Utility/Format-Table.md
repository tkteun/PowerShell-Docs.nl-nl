---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: dc406be942cce50fea7d39cae705834353ff6941
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251775"
---
# <span data-ttu-id="5f87d-103">Format-Table</span><span class="sxs-lookup"><span data-stu-id="5f87d-103">Format-Table</span></span>

## <span data-ttu-id="5f87d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5f87d-104">SYNOPSIS</span></span>
<span data-ttu-id="5f87d-105">Hiermee wordt de uitvoer als een tabel opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="5f87d-105">Formats the output as a table.</span></span>

## <span data-ttu-id="5f87d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5f87d-106">SYNTAX</span></span>

### <span data-ttu-id="5f87d-107">Alles</span><span class="sxs-lookup"><span data-stu-id="5f87d-107">All</span></span>

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="5f87d-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5f87d-108">DESCRIPTION</span></span>

<span data-ttu-id="5f87d-109">`Format-Table`Met de cmdlet wordt de uitvoer van een opdracht opgemaakt als een tabel met de geselecteerde eigenschappen van het object in elke kolom.</span><span class="sxs-lookup"><span data-stu-id="5f87d-109">The `Format-Table` cmdlet formats the output of a command as a table with the selected properties of the object in each column.</span></span> <span data-ttu-id="5f87d-110">Het object type bepaalt de standaard indeling en eigenschappen die in elke kolom worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-110">The object type determines the default layout and properties that are displayed in each column.</span></span> <span data-ttu-id="5f87d-111">U kunt de **eigenschap** para meter gebruiken om de eigenschappen te selecteren die u wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-111">You can use the **Property** parameter to select the properties that you want to display.</span></span>

<span data-ttu-id="5f87d-112">Power shell gebruikt standaard formatteringen om te definiëren hoe object typen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-112">PowerShell uses default formatters to define how object types are displayed.</span></span> <span data-ttu-id="5f87d-113">U kunt `.ps1xml` bestanden gebruiken om aangepaste weer gaven te maken waarin een uitvoer tabel met opgegeven eigenschappen wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-113">You can use `.ps1xml` files to create custom views that display an output table with specified properties.</span></span> <span data-ttu-id="5f87d-114">Nadat een aangepaste weer gave is gemaakt, gebruikt u de para meter **weer geven** om de tabel weer te geven met uw aangepaste weer gave.</span><span class="sxs-lookup"><span data-stu-id="5f87d-114">After a custom view is created, use the **View** parameter to display the table with your custom view.</span></span> <span data-ttu-id="5f87d-115">Zie voor meer informatie over weer gaven [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="5f87d-115">For more information about views, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="5f87d-116">U kunt een hash-tabel gebruiken om berekende eigenschappen toe te voegen aan een object voordat dit wordt weer gegeven en om de kolom koppen in de tabel op te geven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-116">You can use a hash table to add calculated properties to an object before displaying it and to specify the column headings in the table.</span></span> <span data-ttu-id="5f87d-117">Als u een berekende eigenschap wilt toevoegen, gebruikt u de **eigenschap** of **GroupBy** -para meter.</span><span class="sxs-lookup"><span data-stu-id="5f87d-117">To add a calculated property, use the **Property** or **GroupBy** parameter.</span></span> <span data-ttu-id="5f87d-118">Zie [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)voor meer informatie over hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="5f87d-118">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

## <span data-ttu-id="5f87d-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5f87d-119">EXAMPLES</span></span>

### <span data-ttu-id="5f87d-120">Voor beeld 1: Power shell-host Format teren</span><span class="sxs-lookup"><span data-stu-id="5f87d-120">Example 1: Format PowerShell host</span></span>

<span data-ttu-id="5f87d-121">In dit voor beeld wordt informatie weer gegeven over het hostprogramma voor Power shell in een tabel.</span><span class="sxs-lookup"><span data-stu-id="5f87d-121">This example displays information about the host program for PowerShell in a table.</span></span>

```powershell
Get-Host | Format-Table -AutoSize
```

<span data-ttu-id="5f87d-122">De `Get-Host` cmdlet krijgt **System. Management. Automation. internal. host. InternalHost** -objecten die de host vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="5f87d-122">The `Get-Host` cmdlet gets **System.Management.Automation.Internal.Host.InternalHost** objects that represent the host.</span></span> <span data-ttu-id="5f87d-123">De objecten worden naar de pijp lijn verzonden naar `Format-Table` en weer gegeven in een tabel.</span><span class="sxs-lookup"><span data-stu-id="5f87d-123">The objects are sent down the pipeline to `Format-Table` and displayed in a table.</span></span> <span data-ttu-id="5f87d-124">Met de para meter **AutoSize** worden de kolom breedten aangepast om de afkap ping te minimaliseren.</span><span class="sxs-lookup"><span data-stu-id="5f87d-124">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

### <span data-ttu-id="5f87d-125">Voor beeld 2: processen opmaken op BasePriority</span><span class="sxs-lookup"><span data-stu-id="5f87d-125">Example 2: Format processes by BasePriority</span></span>

<span data-ttu-id="5f87d-126">In dit voor beeld worden processen weer gegeven in groepen met dezelfde **BasePriority** -eigenschap.</span><span class="sxs-lookup"><span data-stu-id="5f87d-126">In this example, processes are displayed in groups that have the same **BasePriority** property.</span></span>

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

<span data-ttu-id="5f87d-127">De `Get-Process` cmdlet haalt objecten op die elk proces op de computer vertegenwoordigen en verzendt deze naar de pijp lijn naar beneden `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="5f87d-127">The `Get-Process` cmdlet gets objects that represent each process on the computer and sends them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="5f87d-128">De objecten worden gesorteerd in de volg orde van hun **BasePriority** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="5f87d-128">The objects are sorted in the order of their **BasePriority** property.</span></span>

<span data-ttu-id="5f87d-129">De gesorteerde objecten worden naar de pijp lijn verzonden `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="5f87d-129">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="5f87d-130">De para meter **GroupBy** rangschikt de proces gegevens in groepen op basis van de waarde van de eigenschap **BasePriority** .</span><span class="sxs-lookup"><span data-stu-id="5f87d-130">The **GroupBy** parameter arranges the process data into groups based on their **BasePriority** property's value.</span></span> <span data-ttu-id="5f87d-131">De **Terugloop** parameter zorgt ervoor dat de gegevens niet worden afgekapt.</span><span class="sxs-lookup"><span data-stu-id="5f87d-131">The **Wrap** parameter ensures that data isn't truncated.</span></span>

### <span data-ttu-id="5f87d-132">Voor beeld 3: processen opmaken op begin datum</span><span class="sxs-lookup"><span data-stu-id="5f87d-132">Example 3: Format processes by start date</span></span>

<span data-ttu-id="5f87d-133">In dit voor beeld wordt informatie weer gegeven over de processen die op de computer worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f87d-133">This example displays information about the processes running on the computer.</span></span> <span data-ttu-id="5f87d-134">De objecten worden gesorteerd en `Format-Table` Er wordt een weer gave gebruikt om de objecten te groeperen op basis van de begin datum.</span><span class="sxs-lookup"><span data-stu-id="5f87d-134">The objects are sorted and `Format-Table` uses a view to group the objects by their start date.</span></span>

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

<span data-ttu-id="5f87d-135">`Get-Process` Hiermee worden de **System. Diagnostics. process** -objecten opgehaald die de processen vertegenwoordigen die worden uitgevoerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="5f87d-135">`Get-Process` gets the **System.Diagnostics.Process** objects that represent the processes running on the computer.</span></span> <span data-ttu-id="5f87d-136">De objecten worden naar de pijp lijn verzonden naar `Sort-Object` en worden gesorteerd op basis van de eigenschap **StartTime** .</span><span class="sxs-lookup"><span data-stu-id="5f87d-136">The objects are sent down the pipeline to `Sort-Object`, and are sorted based on the **StartTime** property.</span></span>

<span data-ttu-id="5f87d-137">De gesorteerde objecten worden naar de pijp lijn verzonden `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="5f87d-137">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="5f87d-138">De **weer gave** -para meter geeft u de weer gave van de **StartTime** op die is gedefinieerd in het Power shell- `DotNetTypes.format.ps1xml` bestand voor **System. Diagnostics. process** -objecten.</span><span class="sxs-lookup"><span data-stu-id="5f87d-138">The **View** parameter specifies the **StartTime** view that's defined in the PowerShell `DotNetTypes.format.ps1xml` file for **System.Diagnostics.Process** objects.</span></span> <span data-ttu-id="5f87d-139">In de weer gave **StartTime** worden de begin tijd van elke processen geconverteerd naar een korte datum en worden vervolgens de processen gegroepeerd op basis van de begin datum.</span><span class="sxs-lookup"><span data-stu-id="5f87d-139">The **StartTime** view converts each processes start time to a short date and then groups the processes by the start date.</span></span>

<span data-ttu-id="5f87d-140">Het `DotNetTypes.format.ps1xml` bestand bevat een **prioriteits** weergave voor processen.</span><span class="sxs-lookup"><span data-stu-id="5f87d-140">The `DotNetTypes.format.ps1xml` file contains a **Priority** view for processes.</span></span> <span data-ttu-id="5f87d-141">U kunt uw eigen `format.ps1xml` bestanden maken met aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-141">You can create your own `format.ps1xml` files with customized views.</span></span>

### <span data-ttu-id="5f87d-142">Voor beeld 4: een aangepaste weer gave voor tabel uitvoer gebruiken</span><span class="sxs-lookup"><span data-stu-id="5f87d-142">Example 4: Use a custom view for table output</span></span>

<span data-ttu-id="5f87d-143">In dit voor beeld wordt de inhoud van een map weer gegeven in een aangepaste weer gave.</span><span class="sxs-lookup"><span data-stu-id="5f87d-143">In this example, a custom view displays a directory's contents.</span></span> <span data-ttu-id="5f87d-144">De aangepaste weer gave voegt de kolom **CreationTime** toe aan de tabel uitvoer voor **System. io. DirectoryInfo** -en **System. io. file info** -objecten die zijn gemaakt door `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="5f87d-144">The custom view adds the **CreationTime** column to the table output for **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span>

<span data-ttu-id="5f87d-145">De aangepaste weer gave in dit voor beeld is gemaakt op basis van de weer gave die in Power shell-bron code is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="5f87d-145">The custom view in this example was created from the view defined in PowerShell source code.</span></span> <span data-ttu-id="5f87d-146">Zie [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view)voor meer informatie over weer gaven en de code die wordt gebruikt om de weer gave van dit voor beeld te maken.</span><span class="sxs-lookup"><span data-stu-id="5f87d-146">For more information about views and the code used to create this example's view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).</span></span>

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

<span data-ttu-id="5f87d-147">`Get-ChildItem` Hiermee wordt de inhoud van de huidige map opgehaald `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="5f87d-147">`Get-ChildItem` gets the contents of the current directory, `C:\Test`.</span></span> <span data-ttu-id="5f87d-148">De objecten **System. io. DirectoryInfo** en **System. io. file info** worden via de pijp lijn verzonden.</span><span class="sxs-lookup"><span data-stu-id="5f87d-148">The **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects are sent down the pipeline.</span></span>
<span data-ttu-id="5f87d-149">`Format-Table` gebruikt de **weer gave** -para meter om de aangepaste weergave **mygciview** op te geven die de kolom **CreationTime** bevat.</span><span class="sxs-lookup"><span data-stu-id="5f87d-149">`Format-Table` uses the **View** parameter to specify the custom view **mygciview** that includes the **CreationTime** column.</span></span>

<span data-ttu-id="5f87d-150">De standaard `Format-Table` uitvoer voor bevat `Get-ChildItem` niet de kolom **CreationTime** .</span><span class="sxs-lookup"><span data-stu-id="5f87d-150">The default `Format-Table` output for `Get-ChildItem` doesn't include the **CreationTime** column.</span></span>

### <span data-ttu-id="5f87d-151">Voor beeld 5: eigenschappen voor tabel uitvoer gebruiken</span><span class="sxs-lookup"><span data-stu-id="5f87d-151">Example 5: Use properties for table output</span></span>

<span data-ttu-id="5f87d-152">In dit voor beeld wordt de para meter **Property** gebruikt om alle services van de computer weer te geven in een tabel met twee kolommen waarin de eigenschappen **name** en **DependentServices** worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-152">This example uses the **Property** parameter to display all the computer's services in a two-column table that shows the properties **Name** and **DependentServices**.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="5f87d-153">`Get-Service` haalt alle services op de computer op en verzendt de objecten **System. ServiceProcess. ServiceController** omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="5f87d-153">`Get-Service` gets all the services on the computer and sends the **System.ServiceProcess.ServiceController** objects down the pipeline.</span></span> <span data-ttu-id="5f87d-154">`Format-Table` Hiermee wordt de **eigenschap** para meter gebruikt om op te geven dat de eigenschappen **name** en **DependentServices** in de tabel worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-154">`Format-Table` uses the **Property** parameter to specify that the **Name** and **DependentServices** properties are displayed in the table.</span></span>

<span data-ttu-id="5f87d-155">**Name** en **DependentServices** zijn twee eigenschappen van het object type.</span><span class="sxs-lookup"><span data-stu-id="5f87d-155">**Name** and **DependentServices** are two of the object type's properties.</span></span> <span data-ttu-id="5f87d-156">Alle eigenschappen weer geven: `Get-Service | Get-Member -MemberType Properties` .</span><span class="sxs-lookup"><span data-stu-id="5f87d-156">To view all the properties: `Get-Service | Get-Member -MemberType Properties`.</span></span>

### <span data-ttu-id="5f87d-157">Voor beeld 6: een proces opmaken en de uitvoerings tijd berekenen</span><span class="sxs-lookup"><span data-stu-id="5f87d-157">Example 6: Format a process and calculate its running time</span></span>

<span data-ttu-id="5f87d-158">In dit voor beeld wordt een tabel weer gegeven met de proces naam en de totale uitvoerings tijd voor de **Klad blok** -processen van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5f87d-158">This example displays a table with the process name and total running time for the local computer's **notepad** processes.</span></span> <span data-ttu-id="5f87d-159">De totale uitvoerings tijd wordt berekend door de begin tijd van elk proces van de huidige tijd af te trekken.</span><span class="sxs-lookup"><span data-stu-id="5f87d-159">The total running time is calculated by subtracting the start time of each process from the current time.</span></span>

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

<span data-ttu-id="5f87d-160">`Get-Process` Hiermee worden alle **Notepad** -processen van de lokale computer opgehaald en worden de objecten van de pijp lijn omlaag verzonden.</span><span class="sxs-lookup"><span data-stu-id="5f87d-160">`Get-Process` gets all the local computer's **notepad** processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="5f87d-161">`Format-Table` geeft een tabel weer met twee kolommen: **Verwerknaam** , een `Get-Process` eigenschap en **TotalRunningTime** , een berekende eigenschap.</span><span class="sxs-lookup"><span data-stu-id="5f87d-161">`Format-Table` displays a table with two columns: **ProcessName** , a `Get-Process` property, and **TotalRunningTime** , a calculated property.</span></span>

<span data-ttu-id="5f87d-162">De eigenschap **TotalRunningTime** wordt opgegeven met een hash-tabel met twee sleutels, **Label** en **expressie**.</span><span class="sxs-lookup"><span data-stu-id="5f87d-162">The **TotalRunningTime** property is specified by a hash table with two keys, **Label** and **Expression**.</span></span> <span data-ttu-id="5f87d-163">De **Label** sleutel geeft u de naam van de eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="5f87d-163">The **Label** key specifies the property name.</span></span> <span data-ttu-id="5f87d-164">De **expressie** sleutel geeft de berekening aan.</span><span class="sxs-lookup"><span data-stu-id="5f87d-164">The **Expression** key specifies the calculation.</span></span> <span data-ttu-id="5f87d-165">Met de expressie wordt de eigenschap **StartTime** van elk proces object opgehaald en afgetrokken van het resultaat van een `Get-Date` opdracht, waardoor de huidige datum en tijd worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5f87d-165">The expression gets the **StartTime** property of each process object and subtracts it from the result of a `Get-Date` command, which gets the current date and time.</span></span>

### <span data-ttu-id="5f87d-166">Voor beeld 7: Klad blok-processen opmaken</span><span class="sxs-lookup"><span data-stu-id="5f87d-166">Example 7: Format Notepad processes</span></span>

<span data-ttu-id="5f87d-167">In dit voor beeld wordt gebruikt `Get-CimInstance` om de uitvoerings tijd voor alle **Notepad** -processen op de lokale computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="5f87d-167">This example uses `Get-CimInstance` to get the running time for all **notepad** processes on the local computer.</span></span> <span data-ttu-id="5f87d-168">U kunt `Get-CimInstance` met de para meter **ComputerName** gebruiken om informatie op te halen van externe computers.</span><span class="sxs-lookup"><span data-stu-id="5f87d-168">You can use `Get-CimInstance` with the **ComputerName** parameter to get information from remote computers.</span></span>

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

<span data-ttu-id="5f87d-169">`Get-CimInstance` Hiermee haalt u exemplaren van de WMI- **Win32_Process** klasse op waarmee alle processen van de lokale computer met de naam **notepad.exe** worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-169">`Get-CimInstance` gets instances of the WMI **Win32_Process** class that describes all the local computer's processes named **notepad.exe**.</span></span> <span data-ttu-id="5f87d-170">De proces objecten worden opgeslagen in de `$Processes` variabele.</span><span class="sxs-lookup"><span data-stu-id="5f87d-170">The process objects are stored in the `$Processes` variable.</span></span>

<span data-ttu-id="5f87d-171">De proces objecten in de `$Processes` variabele worden naar beneden verzonden in de pijp lijn naar `Format-Table` , waarin de eigenschap **proces** naam en een nieuwe berekende eigenschap worden weer gegeven, waarbij de **totale uitvoerings tijd** wordt berekend.</span><span class="sxs-lookup"><span data-stu-id="5f87d-171">The process objects in the `$Processes` variable are sent down the pipeline to `Format-Table`, which displays the **ProcessName** property and a new calculated property, **Total Running Time**.</span></span>

<span data-ttu-id="5f87d-172">De opdracht wijst de naam van de nieuwe berekende eigenschap, de **totale uitvoerings tijd** , toe aan de **Label** sleutel.</span><span class="sxs-lookup"><span data-stu-id="5f87d-172">The command assigns the name of the new calculated property, **Total Running Time** , to the **Label** key.</span></span> <span data-ttu-id="5f87d-173">Het script blok van de **expressie** sleutel berekent hoe lang het proces actief is door de aanmaak datum van de processen af te trekken van de huidige datum.</span><span class="sxs-lookup"><span data-stu-id="5f87d-173">The **Expression** key's script block calculates how long the process has been running by subtracting the processes creation date from the current date.</span></span> <span data-ttu-id="5f87d-174">De `Get-Date` cmdlet krijgt de huidige datum.</span><span class="sxs-lookup"><span data-stu-id="5f87d-174">The `Get-Date` cmdlet gets the current date.</span></span> <span data-ttu-id="5f87d-175">De aanmaak datum wordt afgetrokken van de huidige datum.</span><span class="sxs-lookup"><span data-stu-id="5f87d-175">The creation date is subtracted from the current date.</span></span> <span data-ttu-id="5f87d-176">Het resultaat is de waarde van de **totale uitvoerings tijd**.</span><span class="sxs-lookup"><span data-stu-id="5f87d-176">The result is the value of **Total Running Time**.</span></span>

### <span data-ttu-id="5f87d-177">Voor beeld 8: problemen met indelings fouten oplossen</span><span class="sxs-lookup"><span data-stu-id="5f87d-177">Example 8: Troubleshooting format errors</span></span>

<span data-ttu-id="5f87d-178">In de volgende voor beelden ziet u de resultaten van het toevoegen van de para meters **Display error** of **show error** met een expressie.</span><span class="sxs-lookup"><span data-stu-id="5f87d-178">The following examples show the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday

InvalidArgument: Failed to evaluate expression " $_ / $null ".
```

## <span data-ttu-id="5f87d-179">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5f87d-179">PARAMETERS</span></span>

### <span data-ttu-id="5f87d-180">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="5f87d-180">-AutoSize</span></span>

<span data-ttu-id="5f87d-181">Geeft aan dat de cmdlet de kolom grootte en het aantal kolommen aanpast op basis van de breedte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="5f87d-181">Indicates that the cmdlet adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="5f87d-182">De grootte en het aantal van de kolom worden standaard bepaald door de weer gave.</span><span class="sxs-lookup"><span data-stu-id="5f87d-182">By default, the column size and number are determined by the view.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f87d-183">-Display error</span><span class="sxs-lookup"><span data-stu-id="5f87d-183">-DisplayError</span></span>

<span data-ttu-id="5f87d-184">Geeft aan dat de cmdlet fouten weergeeft op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="5f87d-184">Indicates that the cmdlet displays errors on the command line.</span></span> <span data-ttu-id="5f87d-185">Deze para meter kan worden gebruikt als hulp bij het opsporen van fout opsporing wanneer u expressies opmaakt in een `Format-Table` opdracht en de expressies moet oplossen.</span><span class="sxs-lookup"><span data-stu-id="5f87d-185">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f87d-186">-Uitbreiden</span><span class="sxs-lookup"><span data-stu-id="5f87d-186">-Expand</span></span>

<span data-ttu-id="5f87d-187">Hiermee geeft u de indeling van het verzamelings object en de objecten in de verzameling op.</span><span class="sxs-lookup"><span data-stu-id="5f87d-187">Specifies the format of the collection object and the objects in the collection.</span></span> <span data-ttu-id="5f87d-188">Deze para meter is ontworpen om objecten op te maken die ondersteuning bieden voor de [ICollection](/dotnet/api/system.collections.icollection) -interface ([System. Collections](/dotnet/api/system.collections)).</span><span class="sxs-lookup"><span data-stu-id="5f87d-188">This parameter is designed to format objects that support the [ICollection](/dotnet/api/system.collections.icollection) ([System.Collections](/dotnet/api/system.collections)) interface.</span></span> <span data-ttu-id="5f87d-189">De standaard waarde is **EnumOnly**.</span><span class="sxs-lookup"><span data-stu-id="5f87d-189">The default value is **EnumOnly**.</span></span>
<span data-ttu-id="5f87d-190">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="5f87d-190">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="5f87d-191">**EnumOnly** : Hiermee worden de eigenschappen van de objecten in de verzameling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-191">**EnumOnly** : Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="5f87d-192">**CoreOnly** : Hiermee worden de eigenschappen van het verzamelings object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-192">**CoreOnly** : Displays the properties of the collection object.</span></span>
- <span data-ttu-id="5f87d-193">**Beide** : Hiermee worden de eigenschappen van het verzamelings object en de eigenschappen van objecten in de verzameling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-193">**Both** : Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f87d-194">-Force</span><span class="sxs-lookup"><span data-stu-id="5f87d-194">-Force</span></span>

<span data-ttu-id="5f87d-195">Geeft aan dat de cmdlet de cmdlet omleidt om alle fout gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-195">Indicates that the cmdlet directs the cmdlet to display all the error information.</span></span> <span data-ttu-id="5f87d-196">Gebruik met de para meter **Display error** of **show error** .</span><span class="sxs-lookup"><span data-stu-id="5f87d-196">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="5f87d-197">Wanneer een fout object naar de fout wordt geschreven of stromen weer geven, wordt standaard slechts een deel van de fout informatie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-197">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f87d-198">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="5f87d-198">-GroupBy</span></span>

<span data-ttu-id="5f87d-199">Hiermee geeft u de gesorteerde uitvoer in afzonderlijke tabellen op op basis van een eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="5f87d-199">Specifies sorted output in separate tables based on a property value.</span></span> <span data-ttu-id="5f87d-200">U kunt bijvoorbeeld **GroupBy** gebruiken om services in afzonderlijke tabellen weer te geven op basis van hun status.</span><span class="sxs-lookup"><span data-stu-id="5f87d-200">For example, you can use **GroupBy** to list services in separate tables based on their status.</span></span>

<span data-ttu-id="5f87d-201">Voer een expressie of een eigenschap in.</span><span class="sxs-lookup"><span data-stu-id="5f87d-201">Enter an expression or a property.</span></span> <span data-ttu-id="5f87d-202">De para meter **GroupBy** verwacht dat de objecten zijn gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="5f87d-202">The **GroupBy** parameter expects that the objects are sorted.</span></span>
<span data-ttu-id="5f87d-203">Gebruik de `Sort-Object` cmdlet voor `Format-Table` het groeperen van de objecten.</span><span class="sxs-lookup"><span data-stu-id="5f87d-203">Use the `Sort-Object` cmdlet before using `Format-Table` to group the objects.</span></span>

<span data-ttu-id="5f87d-204">De waarde van de para meter **GroupBy** kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="5f87d-204">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="5f87d-205">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="5f87d-205">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="5f87d-206">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="5f87d-206">Valid key-value pairs are:</span></span>

- <span data-ttu-id="5f87d-207">Naam (of label)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="5f87d-207">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="5f87d-208">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="5f87d-208">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="5f87d-209">Tring `<string>`</span><span class="sxs-lookup"><span data-stu-id="5f87d-209">FormatString - `<string>`</span></span>

<span data-ttu-id="5f87d-210">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5f87d-210">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f87d-211">-HideTableHeaders</span><span class="sxs-lookup"><span data-stu-id="5f87d-211">-HideTableHeaders</span></span>

<span data-ttu-id="5f87d-212">De kolom koppen in de tabel worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="5f87d-212">Omits the column headings from the table.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f87d-213">-Input object</span><span class="sxs-lookup"><span data-stu-id="5f87d-213">-InputObject</span></span>

<span data-ttu-id="5f87d-214">Hiermee geeft u de objecten op die moeten worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="5f87d-214">Specifies the objects to format.</span></span> <span data-ttu-id="5f87d-215">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5f87d-215">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5f87d-216">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="5f87d-216">-Property</span></span>

<span data-ttu-id="5f87d-217">Hiermee geeft u de object eigenschappen op die in de weer gave worden weer gegeven en de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-217">Specifies the object properties that appear in the display and the order in which they appear.</span></span> <span data-ttu-id="5f87d-218">Typ een of meer eigenschapnamen, gescheiden door komma's, of gebruik een hash-tabel om een berekende eigenschap weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-218">Type one or more property names, separated by commas, or use a hash table to display a calculated property.</span></span> <span data-ttu-id="5f87d-219">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="5f87d-219">Wildcards are permitted.</span></span>

<span data-ttu-id="5f87d-220">Als u deze para meter weglaat, zijn de eigenschappen die worden weer gegeven in de weer gave afhankelijk van de eigenschappen van het eerste object.</span><span class="sxs-lookup"><span data-stu-id="5f87d-220">If you omit this parameter, the properties that appear in the display depend on the first object's properties.</span></span> <span data-ttu-id="5f87d-221">Als het eerste object bijvoorbeeld **eigenschapa** en **PropertyB** heeft, maar volgende objecten **eigenschapa** , **PropertyB** en **PropertyC** hebben, worden alleen de **eigenschapa** en **PropertyB** teksten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-221">For example, if the first object has **PropertyA** and **PropertyB** but subsequent objects have **PropertyA** , **PropertyB** , and **PropertyC** , then only the **PropertyA** and **PropertyB** headers will display.</span></span>

<span data-ttu-id="5f87d-222">De **eigenschaps** parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="5f87d-222">The **Property** parameter is optional.</span></span> <span data-ttu-id="5f87d-223">U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="5f87d-223">You can't use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="5f87d-224">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="5f87d-224">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="5f87d-225">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="5f87d-225">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="5f87d-226">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="5f87d-226">Valid key-value pairs are:</span></span>

- <span data-ttu-id="5f87d-227">Naam (of label) `<string>`</span><span class="sxs-lookup"><span data-stu-id="5f87d-227">Name (or Label) `<string>`</span></span>
- <span data-ttu-id="5f87d-228">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="5f87d-228">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="5f87d-229">Tring `<string>`</span><span class="sxs-lookup"><span data-stu-id="5f87d-229">FormatString - `<string>`</span></span>
- <span data-ttu-id="5f87d-230">Breedte: `<int32>` moet groter zijn dan `0`</span><span class="sxs-lookup"><span data-stu-id="5f87d-230">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="5f87d-231">Uitlijning-waarde kan `Left` , `Center` of `Right`</span><span class="sxs-lookup"><span data-stu-id="5f87d-231">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="5f87d-232">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5f87d-232">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5f87d-233">-RepeatHeader</span><span class="sxs-lookup"><span data-stu-id="5f87d-233">-RepeatHeader</span></span>

<span data-ttu-id="5f87d-234">Herhaalt de weer gave van de koptekst van een tabel na elk scherm vol.</span><span class="sxs-lookup"><span data-stu-id="5f87d-234">Repeats displaying the header of a table after every screen full.</span></span> <span data-ttu-id="5f87d-235">De herhaalde koptekst is nuttig wanneer de uitvoer wordt gepiped naar een paginerings functie zoals `less` of `more` of paging met een scherm lezer.</span><span class="sxs-lookup"><span data-stu-id="5f87d-235">The repeated header is useful when the output is piped to a pager such as `less` or `more` or paging with a screen reader.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f87d-236">-Show error</span><span class="sxs-lookup"><span data-stu-id="5f87d-236">-ShowError</span></span>

<span data-ttu-id="5f87d-237">Met deze para meter worden fouten verzonden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="5f87d-237">This parameter sends errors through the pipeline.</span></span> <span data-ttu-id="5f87d-238">Deze para meter kan worden gebruikt als hulp bij het opsporen van fout opsporing wanneer u expressies opmaakt in een `Format-Table` opdracht en de expressies moet oplossen.</span><span class="sxs-lookup"><span data-stu-id="5f87d-238">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f87d-239">-Weer geven</span><span class="sxs-lookup"><span data-stu-id="5f87d-239">-View</span></span>

<span data-ttu-id="5f87d-240">Vanaf Power shell 6 worden de standaard weergaven gedefinieerd in Power shell- `C#` bron code.</span><span class="sxs-lookup"><span data-stu-id="5f87d-240">Beginning in PowerShell 6, the default views are defined in PowerShell `C#` source code.</span></span> <span data-ttu-id="5f87d-241">De `*.format.ps1xml` bestanden van de Power shell 5,1 en eerdere versies bestaan niet in Power shell 6 en hoger.</span><span class="sxs-lookup"><span data-stu-id="5f87d-241">The `*.format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="5f87d-242">Met de para meter **weer geven** kunt u een alternatieve notatie of aangepaste weer gave voor de tabel opgeven.</span><span class="sxs-lookup"><span data-stu-id="5f87d-242">The **View** parameter lets you specify an alternate format or custom view for the table.</span></span> <span data-ttu-id="5f87d-243">U kunt de standaard Power shell-weer gaven gebruiken of aangepaste weer gaven maken.</span><span class="sxs-lookup"><span data-stu-id="5f87d-243">You can use the default PowerShell views or create custom views.</span></span> <span data-ttu-id="5f87d-244">Zie [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)voor meer informatie over het maken van een aangepaste weer gave.</span><span class="sxs-lookup"><span data-stu-id="5f87d-244">For more information about how to create a custom view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="5f87d-245">De alternatieve en aangepaste weer gaven voor de **weergave** parameter moeten de tabel indeling gebruiken, anders `Format-Table` mislukt.</span><span class="sxs-lookup"><span data-stu-id="5f87d-245">The alternate and custom views for the **View** parameter must use the table format, otherwise, `Format-Table` fails.</span></span> <span data-ttu-id="5f87d-246">Als de weer gave alternatieve een lijst is, gebruikt u de `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f87d-246">If the alternate view is a list, use the `Format-List` cmdlet.</span></span> <span data-ttu-id="5f87d-247">Als de alternatieve weer gave geen lijst of tabel is, gebruikt u de `Format-Custom` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f87d-247">If the alternate view isn't a list or a table, use the `Format-Custom` cmdlet.</span></span>

<span data-ttu-id="5f87d-248">U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="5f87d-248">You can't use the **Property** and **View** parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f87d-249">-Terugloop</span><span class="sxs-lookup"><span data-stu-id="5f87d-249">-Wrap</span></span>

<span data-ttu-id="5f87d-250">Hiermee wordt tekst weer gegeven die de kolom breedte op de volgende regel overschrijdt.</span><span class="sxs-lookup"><span data-stu-id="5f87d-250">Displays text that exceeds the column width on the next line.</span></span> <span data-ttu-id="5f87d-251">Standaard wordt tekst die de kolom breedte overschrijdt, afgekapt.</span><span class="sxs-lookup"><span data-stu-id="5f87d-251">By default, text that exceeds the column width is truncated.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f87d-252">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f87d-252">CommonParameters</span></span>

<span data-ttu-id="5f87d-253">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5f87d-253">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f87d-254">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5f87d-254">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f87d-255">INVOER</span><span class="sxs-lookup"><span data-stu-id="5f87d-255">INPUTS</span></span>

### <span data-ttu-id="5f87d-256">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="5f87d-256">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="5f87d-257">U kunt elk object omlaag naar de pijp lijn verzenden `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="5f87d-257">You can send any object down the pipeline to `Format-Table`.</span></span>

## <span data-ttu-id="5f87d-258">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5f87d-258">OUTPUTS</span></span>

### <span data-ttu-id="5f87d-259">Micro soft. Power shell. commands. internal. Format</span><span class="sxs-lookup"><span data-stu-id="5f87d-259">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="5f87d-260">`Format-Table` retourneert de indelings objecten die de tabel vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="5f87d-260">`Format-Table` returns format objects that represent the table.</span></span>

## <span data-ttu-id="5f87d-261">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5f87d-261">NOTES</span></span>

## <span data-ttu-id="5f87d-262">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5f87d-262">RELATED LINKS</span></span>

[<span data-ttu-id="5f87d-263">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="5f87d-263">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="5f87d-264">about_Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="5f87d-264">about_Format.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="5f87d-265">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="5f87d-265">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="5f87d-266">Exporteren-FormatData</span><span class="sxs-lookup"><span data-stu-id="5f87d-266">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="5f87d-267">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="5f87d-267">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="5f87d-268">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="5f87d-268">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="5f87d-269">Format-List</span><span class="sxs-lookup"><span data-stu-id="5f87d-269">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="5f87d-270">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="5f87d-270">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="5f87d-271">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="5f87d-271">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="5f87d-272">Get-member</span><span class="sxs-lookup"><span data-stu-id="5f87d-272">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="5f87d-273">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="5f87d-273">Get-CimInstance</span></span>](../CimCmdlets/Get-CimInstance.md)

[<span data-ttu-id="5f87d-274">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="5f87d-274">Update-FormatData</span></span>](Update-FormatData.md)
