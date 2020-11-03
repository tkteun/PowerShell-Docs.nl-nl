---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: 5a76f8ec454ad8144f193d8927f913b89a429fec
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250453"
---
# <span data-ttu-id="217ee-103">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="217ee-103">Export-Csv</span></span>

## <span data-ttu-id="217ee-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="217ee-104">SYNOPSIS</span></span>
<span data-ttu-id="217ee-105">Hiermee worden objecten geconverteerd naar een reeks teken reeksen met door komma's gescheiden waarden (CSV) en worden de teken reeksen opgeslagen in een bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-105">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="217ee-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="217ee-106">SYNTAX</span></span>

### <span data-ttu-id="217ee-107">Scheidings teken (standaard)</span><span class="sxs-lookup"><span data-stu-id="217ee-107">Delimiter (Default)</span></span>

```
Export-Csv [[-Path] <string>] [[-Delimiter] <char>] -InputObject <psobject> [-LiteralPath <string>]
 [-Force] [-NoClobber] [-Encoding <string>] [-Append] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="217ee-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="217ee-108">UseCulture</span></span>

```
Export-Csv [[-Path] <string>] -InputObject <psobject> [-LiteralPath <string>] [-Force] [-NoClobber]
 [-Encoding <string>] [-Append] [-UseCulture] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="217ee-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="217ee-109">DESCRIPTION</span></span>

<span data-ttu-id="217ee-110">De `Export-CSV` cmdlet maakt een CSV-bestand van de objecten die u verzendt.</span><span class="sxs-lookup"><span data-stu-id="217ee-110">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="217ee-111">Elk object is een rij met een door komma's gescheiden lijst van de eigenschaps waarden van het object.</span><span class="sxs-lookup"><span data-stu-id="217ee-111">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="217ee-112">U kunt de `Export-CSV` cmdlet gebruiken om werk bladen te maken en gegevens te delen met Program ma's die CSV-bestanden accepteren als invoer.</span><span class="sxs-lookup"><span data-stu-id="217ee-112">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="217ee-113">Maak objecten niet op voordat u ze naar de `Export-CSV` cmdlet verzendt.</span><span class="sxs-lookup"><span data-stu-id="217ee-113">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="217ee-114">Als u `Export-CSV` opgemaakte objecten ontvangt, bevat het CSV-bestand de indelings eigenschappen in plaats van de object eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="217ee-114">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="217ee-115">Als u alleen geselecteerde eigenschappen van een object wilt exporteren, gebruikt u de `Select-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="217ee-115">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="217ee-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="217ee-116">EXAMPLES</span></span>

### <span data-ttu-id="217ee-117">Voor beeld 1: proces eigenschappen exporteren naar een CSV-bestand</span><span class="sxs-lookup"><span data-stu-id="217ee-117">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="217ee-118">In dit voor beeld worden **proces** objecten met specifieke eigenschappen geselecteerd, worden de objecten geëxporteerd naar een CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-118">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

<span data-ttu-id="217ee-119">`Get-Process`Met de cmdlet worden de **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="217ee-119">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="217ee-120">De para meter **name** filtert de uitvoer zo dat alleen de WmiPrvSE-proces objecten worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="217ee-120">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="217ee-121">De proces objecten worden in de pijp lijn naar de `Select-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-121">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="217ee-122">`Select-Object` gebruikt de para meter **Property** om een subset van eigenschappen van proces objecten te selecteren.</span><span class="sxs-lookup"><span data-stu-id="217ee-122">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="217ee-123">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-123">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="217ee-124">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="217ee-124">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="217ee-125">De para meter **Path** geeft aan dat het WmiData.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="217ee-125">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="217ee-126">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="217ee-126">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="217ee-127">De `Import-Csv` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="217ee-127">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="217ee-128">Voor beeld 2: processen exporteren naar een bestand met door komma's gescheiden waarden</span><span class="sxs-lookup"><span data-stu-id="217ee-128">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="217ee-129">In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-129">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="217ee-130">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="217ee-130">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="217ee-131">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-131">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="217ee-132">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="217ee-132">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="217ee-133">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="217ee-133">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="217ee-134">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="217ee-134">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="217ee-135">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="217ee-135">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="217ee-136">Voor beeld 3: processen exporteren naar een door punt komma's gescheiden bestand</span><span class="sxs-lookup"><span data-stu-id="217ee-136">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="217ee-137">In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een bestand met een punt komma als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="217ee-137">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="217ee-138">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="217ee-138">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="217ee-139">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-139">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="217ee-140">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="217ee-140">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="217ee-141">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="217ee-141">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="217ee-142">De **scheidings** parameter geeft een punt komma om de teken reeks waarden te scheiden.</span><span class="sxs-lookup"><span data-stu-id="217ee-142">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="217ee-143">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="217ee-143">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="217ee-144">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="217ee-144">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="217ee-145">Voor beeld 4: processen exporteren met behulp van het lijst scheidings teken van de huidige cultuur</span><span class="sxs-lookup"><span data-stu-id="217ee-145">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="217ee-146">In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-146">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="217ee-147">Het scheidings teken is het lijst scheidings teken van de huidige cultuur.</span><span class="sxs-lookup"><span data-stu-id="217ee-147">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="217ee-148">De `Get-Culture` cmdlet maakt gebruik van de geneste eigenschappen **Eigenschappen** en **ListSeparator** en geeft het standaard lijst scheidings teken van de huidige cultuur weer.</span><span class="sxs-lookup"><span data-stu-id="217ee-148">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="217ee-149">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="217ee-149">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="217ee-150">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-150">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="217ee-151">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="217ee-151">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="217ee-152">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="217ee-152">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="217ee-153">De para meter **UseCulture** gebruikt het standaard lijst scheidings teken van de huidige cultuur als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="217ee-153">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="217ee-154">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="217ee-154">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="217ee-155">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="217ee-155">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="217ee-156">Voor beeld 5: processen exporteren met type-informatie</span><span class="sxs-lookup"><span data-stu-id="217ee-156">Example 5: Export processes with type information</span></span>

<span data-ttu-id="217ee-157">In dit voor beeld wordt uitgelegd hoe u de **#TYPE** header gegevens opneemt in een CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-157">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="217ee-158">De **#TYPE** header is de standaard waarde in versies voorafgaand aan power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="217ee-158">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="217ee-159">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="217ee-159">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="217ee-160">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-160">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="217ee-161">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="217ee-161">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="217ee-162">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="217ee-162">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="217ee-163">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="217ee-163">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="217ee-164">Voor beeld 6: objecten exporteren en toevoegen aan een CSV-bestand</span><span class="sxs-lookup"><span data-stu-id="217ee-164">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="217ee-165">In dit voor beeld wordt beschreven hoe u objecten exporteert naar een CSV-bestand en hoe u de para meter **Append** gebruikt om objecten toe te voegen aan een bestaand bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-165">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

<span data-ttu-id="217ee-166">`Get-Service`Met de cmdlet worden service objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="217ee-166">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="217ee-167">De para meter **DisplayName** retourneert services die de Word-toepassing bevatten.</span><span class="sxs-lookup"><span data-stu-id="217ee-167">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="217ee-168">De service objecten worden naar de-cmdlet verzonden via de pijp lijn `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="217ee-168">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="217ee-169">`Select-Object` maakt gebruik van de para meter **Property** om de eigenschappen **DisplayName** en **status** op te geven.</span><span class="sxs-lookup"><span data-stu-id="217ee-169">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="217ee-170">De `$AppService` variabele slaat de objecten op.</span><span class="sxs-lookup"><span data-stu-id="217ee-170">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="217ee-171">De `$AppService` objecten worden naar de-cmdlet verzonden via de pijp lijn `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="217ee-171">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="217ee-172">`Export-Csv` Hiermee worden de service objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="217ee-172">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="217ee-173">De para meter **Path** geeft aan dat het Services.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="217ee-173">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="217ee-174">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="217ee-174">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="217ee-175">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="217ee-175">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="217ee-176">De `Get-Service` `Select-Object` cmdlets en worden herhaald voor services die het woord Windows bevatten.</span><span class="sxs-lookup"><span data-stu-id="217ee-176">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="217ee-177">De `$WinService` variabele slaat de service objecten op.</span><span class="sxs-lookup"><span data-stu-id="217ee-177">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="217ee-178">De `Export-Csv` cmdlet gebruikt de para meter **Append** om op te geven dat de `$WinService` objecten worden toegevoegd aan het bestaande Services.csv-bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-178">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="217ee-179">De `Get-Content` cmdlet wordt herhaald om het bijgewerkte bestand weer te geven dat de toegevoegde gegevens bevat.</span><span class="sxs-lookup"><span data-stu-id="217ee-179">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="217ee-180">Voor beeld 7: met de cmdlet Format in een pijp lijn worden onverwachte resultaten gemaakt</span><span class="sxs-lookup"><span data-stu-id="217ee-180">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="217ee-181">In dit voor beeld ziet u waarom het belang rijk is dat u geen indelings-cmdlet kunt gebruiken in een pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="217ee-181">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="217ee-182">Als onverwachte uitvoer wordt ontvangen, moet u de pijplijn syntaxis oplossen.</span><span class="sxs-lookup"><span data-stu-id="217ee-182">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

<span data-ttu-id="217ee-183">De `Get-Date` cmdlet haalt het **DateTime** -object op.</span><span class="sxs-lookup"><span data-stu-id="217ee-183">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="217ee-184">Het object wordt vanuit de pijp lijn naar de `Select-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-184">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="217ee-185">`Select-Object` gebruikt de para meter **Property** om een subset van object eigenschappen te selecteren.</span><span class="sxs-lookup"><span data-stu-id="217ee-185">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="217ee-186">Het object wordt vanuit de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-186">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="217ee-187">`Export-Csv` converteert het object naar een CSV-indeling.</span><span class="sxs-lookup"><span data-stu-id="217ee-187">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="217ee-188">De para meter **Path** geeft aan dat het DateTime.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="217ee-188">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="217ee-189">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="217ee-189">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="217ee-190">De `Get-Content` cmdlet gebruikt de para meter **Path** om het CSV-bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="217ee-190">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="217ee-191">Wanneer de `Format-Table` cmdlet wordt gebruikt in de pijp lijn om eigenschappen te selecteren, worden er onverwachte resultaten ontvangen.</span><span class="sxs-lookup"><span data-stu-id="217ee-191">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="217ee-192">`Format-Table` Hiermee worden de objecten van de tabel indeling naar de-cmdlet van de pijp lijn in `Export-Csv` plaats van het **DateTime** -object verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-192">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="217ee-193">`Export-Csv` de tabel indelings objecten worden geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="217ee-193">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="217ee-194">`Get-Content`Met de cmdlet wordt het CSV-bestand weer gegeven dat de tabel indelings objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="217ee-194">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="217ee-195">Voor beeld 8: de para meter Force gebruiken om alleen-lezen bestanden te overschrijven</span><span class="sxs-lookup"><span data-stu-id="217ee-195">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="217ee-196">In dit voor beeld maakt u een leeg bestand met het kenmerk alleen-lezen en gebruikt u de para meter **Force** om het bestand bij te werken.</span><span class="sxs-lookup"><span data-stu-id="217ee-196">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="217ee-197">De `New-Item` cmdlet maakt gebruik van de para meters **Path** en **item** type voor het maken van het ReadOnly.csv-bestand in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="217ee-197">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="217ee-198">De `Set-ItemProperty` cmdlet gebruikt de para meters **name** en **Value** om de eigenschap **IsReadOnly** van het bestand te wijzigen in True.</span><span class="sxs-lookup"><span data-stu-id="217ee-198">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="217ee-199">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="217ee-199">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="217ee-200">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-200">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="217ee-201">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="217ee-201">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="217ee-202">De para meter **Path** geeft aan dat het ReadOnly.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="217ee-202">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="217ee-203">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="217ee-203">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="217ee-204">In de uitvoer ziet u dat het bestand niet is geschreven, omdat de toegang wordt geweigerd.</span><span class="sxs-lookup"><span data-stu-id="217ee-204">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="217ee-205">De para meter **Force** wordt toegevoegd aan de `Export-Csv` cmdlet om de export af te dwingen om naar het bestand te schrijven.</span><span class="sxs-lookup"><span data-stu-id="217ee-205">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="217ee-206">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="217ee-206">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="217ee-207">Voor beeld 9: de para meter Force gebruiken met Append</span><span class="sxs-lookup"><span data-stu-id="217ee-207">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="217ee-208">In dit voor beeld ziet u hoe u de para meters **Force** en **Append** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="217ee-208">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="217ee-209">Als deze para meters worden gecombineerd, kunnen niet-overeenkomende object eigenschappen naar een CSV-bestand worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="217ee-209">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

<span data-ttu-id="217ee-210">Een expressie maakt de **PSCustomObject** met de **naam** en **versie** -eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="217ee-210">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="217ee-211">De waarden worden opgeslagen in de `$Content` variabele.</span><span class="sxs-lookup"><span data-stu-id="217ee-211">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="217ee-212">De `$Content` variabele wordt via de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-212">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="217ee-213">`Export-Csv` maakt gebruik van de para meter **Path** en slaat het ParmFile.csv-bestand op in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="217ee-213">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="217ee-214">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="217ee-214">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="217ee-215">Met een andere expressie maakt u een **PSCustomObject** met de **naam** en **editie** -eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="217ee-215">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="217ee-216">De waarden worden opgeslagen in de `$AdditionalContent` variabele.</span><span class="sxs-lookup"><span data-stu-id="217ee-216">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="217ee-217">De `$AdditionalContent` variabele wordt via de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="217ee-217">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="217ee-218">De **toevoeg** parameter wordt gebruikt om de gegevens aan het bestand toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="217ee-218">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="217ee-219">De toevoeg bewerking mislukt omdat de naam van een eigenschap niet overeenkomt met de **versie** en **editie**.</span><span class="sxs-lookup"><span data-stu-id="217ee-219">The append fails because there is a property name mismatch between **Version** and **Edition**.</span></span>

<span data-ttu-id="217ee-220">De `Export-Csv` cmdlet **Force** -para meter wordt gebruikt om het exporteren af te dwingen om naar het bestand te schrijven.</span><span class="sxs-lookup"><span data-stu-id="217ee-220">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="217ee-221">De **editie** -eigenschap wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="217ee-221">The **Edition** property is discarded.</span></span> <span data-ttu-id="217ee-222">De `Import-Csv` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="217ee-222">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

## <span data-ttu-id="217ee-223">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="217ee-223">PARAMETERS</span></span>

### <span data-ttu-id="217ee-224">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="217ee-224">-Append</span></span>

<span data-ttu-id="217ee-225">Gebruik deze para meter zodat `Export-CSV` CSV-uitvoer aan het einde van het opgegeven bestand wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="217ee-225">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="217ee-226">Zonder deze para meter `Export-CSV` vervangt de bestands inhoud zonder waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="217ee-226">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="217ee-227">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="217ee-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-228">-Scheidings teken</span><span class="sxs-lookup"><span data-stu-id="217ee-228">-Delimiter</span></span>

<span data-ttu-id="217ee-229">Hiermee wordt een scheidings teken opgegeven om de eigenschaps waarden van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="217ee-229">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="217ee-230">De standaard waarde is een komma ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="217ee-230">The default is a comma (`,`).</span></span> <span data-ttu-id="217ee-231">Voer een teken in, bijvoorbeeld een dubbele punt ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="217ee-231">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="217ee-232">Als u een punt komma () wilt opgeven `;` , plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="217ee-232">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-233">-Encoding</span><span class="sxs-lookup"><span data-stu-id="217ee-233">-Encoding</span></span>

<span data-ttu-id="217ee-234">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="217ee-234">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="217ee-235">De standaardwaarde is `ASCII`.</span><span class="sxs-lookup"><span data-stu-id="217ee-235">The default value is `ASCII`.</span></span>

<span data-ttu-id="217ee-236">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="217ee-236">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="217ee-237">`ASCII` Maakt gebruik van ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="217ee-237">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="217ee-238">`BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="217ee-238">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="217ee-239">`Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).</span><span class="sxs-lookup"><span data-stu-id="217ee-239">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="217ee-240">`OEM` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.</span><span class="sxs-lookup"><span data-stu-id="217ee-240">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="217ee-241">`Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="217ee-241">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="217ee-242">`UTF7` Maakt gebruik van UTF-7.</span><span class="sxs-lookup"><span data-stu-id="217ee-242">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="217ee-243">`UTF8` Maakt gebruik van UTF-8.</span><span class="sxs-lookup"><span data-stu-id="217ee-243">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="217ee-244">`UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="217ee-244">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-245">-Force</span><span class="sxs-lookup"><span data-stu-id="217ee-245">-Force</span></span>

<span data-ttu-id="217ee-246">Met deze para meter kunt `Export-Csv` u bestanden overschrijven met het kenmerk **alleen-lezen** .</span><span class="sxs-lookup"><span data-stu-id="217ee-246">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="217ee-247">Wanneer **Force** -en **Append** -para meters worden gecombineerd, kunnen objecten die niet-overeenkomende eigenschappen bevatten, naar een CSV-bestand worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="217ee-247">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="217ee-248">Alleen de eigenschappen die overeenkomen, worden naar het bestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="217ee-248">Only the properties that match are written to the file.</span></span> <span data-ttu-id="217ee-249">De eigenschappen die niet overeenkomen, worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="217ee-249">The mismatched properties are discarded.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-250">-Input object</span><span class="sxs-lookup"><span data-stu-id="217ee-250">-InputObject</span></span>

<span data-ttu-id="217ee-251">Geeft aan welke objecten als CSV-teken reeksen moeten worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="217ee-251">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="217ee-252">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="217ee-252">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="217ee-253">U kunt ook objecten pipeen naar `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="217ee-253">You can also pipe objects to `Export-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-254">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="217ee-254">-LiteralPath</span></span>

<span data-ttu-id="217ee-255">Hiermee geeft u het pad naar het CSV-uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-255">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="217ee-256">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="217ee-256">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="217ee-257">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="217ee-257">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="217ee-258">Als het pad escape-tekens bevat, gebruikt u enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="217ee-258">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="217ee-259">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="217ee-259">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-260">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="217ee-260">-NoClobber</span></span>

<span data-ttu-id="217ee-261">Gebruik deze para meter om `Export-CSV` een bestaand bestand niet te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="217ee-261">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="217ee-262">Als het bestand zich in het opgegeven pad bevindt, wordt `Export-CSV` het bestand standaard zonder waarschuwing overschreven.</span><span class="sxs-lookup"><span data-stu-id="217ee-262">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-263">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="217ee-263">-NoTypeInformation</span></span>

<span data-ttu-id="217ee-264">Hiermee verwijdert u de **#TYPE** informatie uit de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="217ee-264">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="217ee-265">Deze para meter werd de standaard waarde in Power shell 6,0 en is opgenomen voor achterwaartse compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="217ee-265">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-266">-Path</span><span class="sxs-lookup"><span data-stu-id="217ee-266">-Path</span></span>

<span data-ttu-id="217ee-267">Een vereiste para meter waarmee de locatie wordt opgegeven waarop het CSV-uitvoer bestand moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="217ee-267">A required parameter that specifies the location to save the CSV output file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-268">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="217ee-268">-UseCulture</span></span>

<span data-ttu-id="217ee-269">Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="217ee-269">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="217ee-270">Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="217ee-270">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-271">-Confirm</span><span class="sxs-lookup"><span data-stu-id="217ee-271">-Confirm</span></span>

<span data-ttu-id="217ee-272">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="217ee-272">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-273">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="217ee-273">-WhatIf</span></span>

<span data-ttu-id="217ee-274">Hiermee voor komt u dat de cmdlet wordt verwerkt of dat er wijzigingen worden aangebracht.</span><span class="sxs-lookup"><span data-stu-id="217ee-274">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="217ee-275">De uitvoer laat zien wat er zou gebeuren als de cmdlet werd uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="217ee-275">The output shows what would happen if the cmdlet were run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="217ee-276">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="217ee-276">CommonParameters</span></span>

<span data-ttu-id="217ee-277">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="217ee-277">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="217ee-278">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="217ee-278">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="217ee-279">INVOER</span><span class="sxs-lookup"><span data-stu-id="217ee-279">INPUTS</span></span>

### <span data-ttu-id="217ee-280">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="217ee-280">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="217ee-281">U kunt elk object met een adapter voor een Extended-type systeem (ETS) aan `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="217ee-281">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="217ee-282">UITVOER</span><span class="sxs-lookup"><span data-stu-id="217ee-282">OUTPUTS</span></span>

### <span data-ttu-id="217ee-283">System. String</span><span class="sxs-lookup"><span data-stu-id="217ee-283">System.String</span></span>

<span data-ttu-id="217ee-284">De CSV-lijst wordt verzonden naar het bestand dat is opgegeven in de para meter Path.</span><span class="sxs-lookup"><span data-stu-id="217ee-284">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="217ee-285">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="217ee-285">NOTES</span></span>

<span data-ttu-id="217ee-286">De `Export-CSV` cmdlet converteert de objecten die u verzendt naar een reeks CSV-teken reeksen en slaat deze op in het opgegeven tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-286">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="217ee-287">U kunt gebruiken `Export-CSV` om objecten op te slaan in een CSV-bestand en vervolgens de `Import-Csv` cmdlet te gebruiken om objecten te maken vanuit het CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-287">You can use `Export-CSV` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the CSV file.</span></span>

<span data-ttu-id="217ee-288">In het CSV-bestand wordt elk object vertegenwoordigd door een door komma's gescheiden lijst van de eigenschaps waarden van het object.</span><span class="sxs-lookup"><span data-stu-id="217ee-288">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="217ee-289">De eigenschaps waarden worden geconverteerd naar teken reeksen met de methode **toString ()** .</span><span class="sxs-lookup"><span data-stu-id="217ee-289">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="217ee-290">De teken reeksen worden vertegenwoordigd door de naam van de eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="217ee-290">The strings are represented by the property value name.</span></span> <span data-ttu-id="217ee-291">Export-CSV exporteert de methoden van het object niet.</span><span class="sxs-lookup"><span data-stu-id="217ee-291">\`Export-CSV does not export the methods of the object.</span></span>

<span data-ttu-id="217ee-292">De CSV-teken reeksen worden als volgt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="217ee-292">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="217ee-293">De eerste teken reeks bevat standaard de **#TYPE** informatie header, gevolgd door de volledig gekwalificeerde naam van het object type.</span><span class="sxs-lookup"><span data-stu-id="217ee-293">By default the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span> <span data-ttu-id="217ee-294">Bijvoorbeeld **#TYPE System. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="217ee-294">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="217ee-295">Als **NoTypeInformation** wordt gebruikt, bevat de eerste teken reeks de kolom koppen.</span><span class="sxs-lookup"><span data-stu-id="217ee-295">If **NoTypeInformation** is used the first string includes the column headers.</span></span> <span data-ttu-id="217ee-296">De headers bevatten de eigenschaps namen van het eerste object als een door komma's gescheiden lijst.</span><span class="sxs-lookup"><span data-stu-id="217ee-296">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="217ee-297">De resterende teken reeksen bevatten door komma's gescheiden lijsten van de eigenschaps waarden van elk object.</span><span class="sxs-lookup"><span data-stu-id="217ee-297">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="217ee-298">Wanneer u meerdere objecten indient `Export-CSV` , `Export-CSV` organiseert het bestand op basis van de eigenschappen van het eerste object dat u verzendt.</span><span class="sxs-lookup"><span data-stu-id="217ee-298">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="217ee-299">Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de eigenschaps waarde van dat object null, zoals wordt weer gegeven in twee opeenvolgende komma's.</span><span class="sxs-lookup"><span data-stu-id="217ee-299">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="217ee-300">Als de resterende objecten extra eigenschappen hebben, worden deze eigenschaps waarden niet opgenomen in het bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-300">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="217ee-301">U kunt de `Import-Csv` cmdlet gebruiken om objecten opnieuw te maken op basis van de CSV-teken reeksen in de bestanden.</span><span class="sxs-lookup"><span data-stu-id="217ee-301">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="217ee-302">De resulterende objecten zijn CSV-versies van de oorspronkelijke objecten die bestaan uit teken reeks representaties van de eigenschaps waarden en geen methoden.</span><span class="sxs-lookup"><span data-stu-id="217ee-302">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="217ee-303">Met `ConvertTo-Csv` de `ConvertFrom-Csv` cmdlets en worden objecten GECONVERTEERD naar CSV-teken reeksen en CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="217ee-303">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="217ee-304">`Export-CSV` is hetzelfde als `ConvertTo-CSV` , behalve dat de CSV-teken reeksen worden opgeslagen in een bestand.</span><span class="sxs-lookup"><span data-stu-id="217ee-304">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="217ee-305">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="217ee-305">RELATED LINKS</span></span>

[<span data-ttu-id="217ee-306">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="217ee-306">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="217ee-307">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="217ee-307">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="217ee-308">Format-Table</span><span class="sxs-lookup"><span data-stu-id="217ee-308">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="217ee-309">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="217ee-309">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="217ee-310">Select-Object</span><span class="sxs-lookup"><span data-stu-id="217ee-310">Select-Object</span></span>](Select-Object.md)
