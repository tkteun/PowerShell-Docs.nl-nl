---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: bb2d077b3584d4501db00a927b83034d37dceaec
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913356"
---
# <span data-ttu-id="f2152-102">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="f2152-102">Export-Csv</span></span>

## <span data-ttu-id="f2152-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f2152-103">SYNOPSIS</span></span>
<span data-ttu-id="f2152-104">Hiermee worden objecten geconverteerd naar een reeks teken reeksen met door komma's gescheiden waarden (CSV) en worden de teken reeksen opgeslagen in een bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-104">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="f2152-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f2152-105">SYNTAX</span></span>

### <span data-ttu-id="f2152-106">Scheidings teken (standaard)</span><span class="sxs-lookup"><span data-stu-id="f2152-106">Delimiter (Default)</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f2152-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="f2152-107">UseCulture</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f2152-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f2152-108">DESCRIPTION</span></span>

<span data-ttu-id="f2152-109">De `Export-CSV` cmdlet maakt een CSV-bestand van de objecten die u verzendt.</span><span class="sxs-lookup"><span data-stu-id="f2152-109">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="f2152-110">Elk object is een rij met een door komma's gescheiden lijst van de eigenschaps waarden van het object.</span><span class="sxs-lookup"><span data-stu-id="f2152-110">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="f2152-111">U kunt de `Export-CSV` cmdlet gebruiken om werk bladen te maken en gegevens te delen met Program ma's die CSV-bestanden accepteren als invoer.</span><span class="sxs-lookup"><span data-stu-id="f2152-111">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="f2152-112">Maak objecten niet op voordat u ze naar de `Export-CSV` cmdlet verzendt.</span><span class="sxs-lookup"><span data-stu-id="f2152-112">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="f2152-113">Als u `Export-CSV` opgemaakte objecten ontvangt, bevat het CSV-bestand de indelings eigenschappen in plaats van de object eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="f2152-113">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="f2152-114">Als u alleen geselecteerde eigenschappen van een object wilt exporteren, gebruikt u de `Select-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2152-114">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="f2152-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f2152-115">EXAMPLES</span></span>

### <span data-ttu-id="f2152-116">Voor beeld 1: proces eigenschappen exporteren naar een CSV-bestand</span><span class="sxs-lookup"><span data-stu-id="f2152-116">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="f2152-117">In dit voor beeld worden **proces** objecten met specifieke eigenschappen geselecteerd, worden de objecten geëxporteerd naar een CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-117">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

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

<span data-ttu-id="f2152-118">`Get-Process`Met de cmdlet worden de **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2152-118">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="f2152-119">De para meter **name** filtert de uitvoer zo dat alleen de WmiPrvSE-proces objecten worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="f2152-119">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="f2152-120">De proces objecten worden in de pijp lijn naar de `Select-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-120">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="f2152-121">`Select-Object` gebruikt de para meter **Property** om een subset van eigenschappen van proces objecten te selecteren.</span><span class="sxs-lookup"><span data-stu-id="f2152-121">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="f2152-122">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-122">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2152-123">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2152-123">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="f2152-124">De para meter **Path** geeft aan dat het WmiData.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="f2152-124">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2152-125">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="f2152-125">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2152-126">De `Import-Csv` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="f2152-126">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2152-127">Voor beeld 2: processen exporteren naar een bestand met door komma's gescheiden waarden</span><span class="sxs-lookup"><span data-stu-id="f2152-127">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="f2152-128">In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-128">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="f2152-129">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2152-129">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="f2152-130">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-130">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2152-131">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2152-131">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="f2152-132">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="f2152-132">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2152-133">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="f2152-133">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2152-134">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="f2152-134">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2152-135">Voor beeld 3: processen exporteren naar een door punt komma's gescheiden bestand</span><span class="sxs-lookup"><span data-stu-id="f2152-135">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="f2152-136">In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een bestand met een punt komma als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="f2152-136">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="f2152-137">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2152-137">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="f2152-138">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-138">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2152-139">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2152-139">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="f2152-140">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="f2152-140">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2152-141">De **scheidings** parameter geeft een punt komma om de teken reeks waarden te scheiden.</span><span class="sxs-lookup"><span data-stu-id="f2152-141">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="f2152-142">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="f2152-142">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2152-143">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="f2152-143">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2152-144">Voor beeld 4: processen exporteren met behulp van het lijst scheidings teken van de huidige cultuur</span><span class="sxs-lookup"><span data-stu-id="f2152-144">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="f2152-145">In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-145">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="f2152-146">Het scheidings teken is het lijst scheidings teken van de huidige cultuur.</span><span class="sxs-lookup"><span data-stu-id="f2152-146">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="f2152-147">De `Get-Culture` cmdlet maakt gebruik van de geneste eigenschappen **Eigenschappen** en **ListSeparator** en geeft het standaard lijst scheidings teken van de huidige cultuur weer.</span><span class="sxs-lookup"><span data-stu-id="f2152-147">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="f2152-148">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2152-148">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="f2152-149">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-149">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2152-150">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2152-150">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="f2152-151">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="f2152-151">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2152-152">De para meter **UseCulture** gebruikt het standaard lijst scheidings teken van de huidige cultuur als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="f2152-152">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="f2152-153">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="f2152-153">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2152-154">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="f2152-154">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2152-155">Voor beeld 5: processen exporteren met type-informatie</span><span class="sxs-lookup"><span data-stu-id="f2152-155">Example 5: Export processes with type information</span></span>

<span data-ttu-id="f2152-156">In dit voor beeld wordt uitgelegd hoe u de **#TYPE** header gegevens opneemt in een CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-156">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="f2152-157">De **#TYPE** header is de standaard waarde in versies voorafgaand aan power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f2152-157">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -IncludeTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="f2152-158">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2152-158">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="f2152-159">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-159">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2152-160">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2152-160">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="f2152-161">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="f2152-161">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2152-162">De **IncludeTypeInformation** bevat de **#TYPE** informatie-header in de CSV-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f2152-162">The **IncludeTypeInformation** includes the **#TYPE** information header in the CSV output.</span></span> <span data-ttu-id="f2152-163">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="f2152-163">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2152-164">Voor beeld 6: objecten exporteren en toevoegen aan een CSV-bestand</span><span class="sxs-lookup"><span data-stu-id="f2152-164">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="f2152-165">In dit voor beeld wordt beschreven hoe u objecten exporteert naar een CSV-bestand en hoe u de para meter **Append** gebruikt om objecten toe te voegen aan een bestaand bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-165">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

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

<span data-ttu-id="f2152-166">`Get-Service`Met de cmdlet worden service objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2152-166">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="f2152-167">De para meter **DisplayName** retourneert services die de Word-toepassing bevatten.</span><span class="sxs-lookup"><span data-stu-id="f2152-167">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="f2152-168">De service objecten worden naar de-cmdlet verzonden via de pijp lijn `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="f2152-168">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="f2152-169">`Select-Object` maakt gebruik van de para meter **Property** om de eigenschappen **DisplayName** en **status** op te geven.</span><span class="sxs-lookup"><span data-stu-id="f2152-169">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="f2152-170">De `$AppService` variabele slaat de objecten op.</span><span class="sxs-lookup"><span data-stu-id="f2152-170">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="f2152-171">De `$AppService` objecten worden naar de-cmdlet verzonden via de pijp lijn `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="f2152-171">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2152-172">`Export-Csv` Hiermee worden de service objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2152-172">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="f2152-173">De para meter **Path** geeft aan dat het Services.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="f2152-173">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2152-174">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="f2152-174">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2152-175">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="f2152-175">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="f2152-176">De `Get-Service` `Select-Object` cmdlets en worden herhaald voor services die het woord Windows bevatten.</span><span class="sxs-lookup"><span data-stu-id="f2152-176">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="f2152-177">De `$WinService` variabele slaat de service objecten op.</span><span class="sxs-lookup"><span data-stu-id="f2152-177">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="f2152-178">De `Export-Csv` cmdlet gebruikt de para meter **Append** om op te geven dat de `$WinService` objecten worden toegevoegd aan het bestaande Services.csv-bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-178">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="f2152-179">De `Get-Content` cmdlet wordt herhaald om het bijgewerkte bestand weer te geven dat de toegevoegde gegevens bevat.</span><span class="sxs-lookup"><span data-stu-id="f2152-179">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="f2152-180">Voor beeld 7: met de cmdlet Format in een pijp lijn worden onverwachte resultaten gemaakt</span><span class="sxs-lookup"><span data-stu-id="f2152-180">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="f2152-181">In dit voor beeld ziet u waarom het belang rijk is dat u geen indelings-cmdlet kunt gebruiken in een pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="f2152-181">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="f2152-182">Als onverwachte uitvoer wordt ontvangen, moet u de pijplijn syntaxis oplossen.</span><span class="sxs-lookup"><span data-stu-id="f2152-182">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

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

<span data-ttu-id="f2152-183">De `Get-Date` cmdlet haalt het **DateTime** -object op.</span><span class="sxs-lookup"><span data-stu-id="f2152-183">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="f2152-184">Het object wordt vanuit de pijp lijn naar de `Select-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-184">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="f2152-185">`Select-Object` gebruikt de para meter **Property** om een subset van object eigenschappen te selecteren.</span><span class="sxs-lookup"><span data-stu-id="f2152-185">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="f2152-186">Het object wordt vanuit de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-186">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2152-187">`Export-Csv` converteert het object naar een CSV-indeling.</span><span class="sxs-lookup"><span data-stu-id="f2152-187">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="f2152-188">De para meter **Path** geeft aan dat het DateTime.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="f2152-188">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2152-189">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="f2152-189">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2152-190">De `Get-Content` cmdlet gebruikt de para meter **Path** om het CSV-bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="f2152-190">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="f2152-191">Wanneer de `Format-Table` cmdlet wordt gebruikt in de pijp lijn om eigenschappen te selecteren, worden er onverwachte resultaten ontvangen.</span><span class="sxs-lookup"><span data-stu-id="f2152-191">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="f2152-192">`Format-Table` Hiermee worden de objecten van de tabel indeling naar de-cmdlet van de pijp lijn in `Export-Csv` plaats van het **DateTime** -object verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-192">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="f2152-193">`Export-Csv` de tabel indelings objecten worden geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2152-193">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="f2152-194">`Get-Content`Met de cmdlet wordt het CSV-bestand weer gegeven dat de tabel indelings objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="f2152-194">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="f2152-195">Voor beeld 8: de para meter Force gebruiken om alleen-lezen bestanden te overschrijven</span><span class="sxs-lookup"><span data-stu-id="f2152-195">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="f2152-196">In dit voor beeld maakt u een leeg bestand met het kenmerk alleen-lezen en gebruikt u de para meter **Force** om het bestand bij te werken.</span><span class="sxs-lookup"><span data-stu-id="f2152-196">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

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

<span data-ttu-id="f2152-197">De `New-Item` cmdlet maakt gebruik van de para meters **Path** en **item** type voor het maken van het ReadOnly.csv-bestand in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="f2152-197">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="f2152-198">De `Set-ItemProperty` cmdlet gebruikt de para meters **name** en **Value** om de eigenschap **IsReadOnly** van het bestand te wijzigen in True.</span><span class="sxs-lookup"><span data-stu-id="f2152-198">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="f2152-199">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2152-199">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="f2152-200">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-200">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2152-201">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2152-201">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="f2152-202">De para meter **Path** geeft aan dat het ReadOnly.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="f2152-202">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2152-203">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="f2152-203">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2152-204">In de uitvoer ziet u dat het bestand niet is geschreven, omdat de toegang wordt geweigerd.</span><span class="sxs-lookup"><span data-stu-id="f2152-204">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="f2152-205">De para meter **Force** wordt toegevoegd aan de `Export-Csv` cmdlet om de export af te dwingen om naar het bestand te schrijven.</span><span class="sxs-lookup"><span data-stu-id="f2152-205">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="f2152-206">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="f2152-206">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2152-207">Voor beeld 9: de para meter Force gebruiken met Append</span><span class="sxs-lookup"><span data-stu-id="f2152-207">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="f2152-208">In dit voor beeld ziet u hoe u de para meters **Force** en **Append** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f2152-208">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="f2152-209">Als deze para meters worden gecombineerd, kunnen niet-overeenkomende object eigenschappen naar een CSV-bestand worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="f2152-209">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

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

<span data-ttu-id="f2152-210">Een expressie maakt de **PSCustomObject** met de **naam** en **versie** -eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="f2152-210">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="f2152-211">De waarden worden opgeslagen in de `$Content` variabele.</span><span class="sxs-lookup"><span data-stu-id="f2152-211">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="f2152-212">De `$Content` variabele wordt via de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-212">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2152-213">`Export-Csv` maakt gebruik van de para meter **Path** en slaat het ParmFile.csv-bestand op in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="f2152-213">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="f2152-214">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="f2152-214">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="f2152-215">Met een andere expressie maakt u een **PSCustomObject** met de **naam** en **editie** -eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="f2152-215">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="f2152-216">De waarden worden opgeslagen in de `$AdditionalContent` variabele.</span><span class="sxs-lookup"><span data-stu-id="f2152-216">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="f2152-217">De `$AdditionalContent` variabele wordt via de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2152-217">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2152-218">De **toevoeg** parameter wordt gebruikt om de gegevens aan het bestand toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="f2152-218">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="f2152-219">De toevoeg bewerking mislukt omdat de naam van een eigenschap niet overeenkomt met de **versie** en **editie**.</span><span class="sxs-lookup"><span data-stu-id="f2152-219">The append fails because there is a property name mismatch between **Version** and **Edition**.</span></span>

<span data-ttu-id="f2152-220">De `Export-Csv` cmdlet **Force** -para meter wordt gebruikt om het exporteren af te dwingen om naar het bestand te schrijven.</span><span class="sxs-lookup"><span data-stu-id="f2152-220">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="f2152-221">De **editie** -eigenschap wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f2152-221">The **Edition** property is discarded.</span></span> <span data-ttu-id="f2152-222">De `Import-Csv` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="f2152-222">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2152-223">Voor beeld 10: exporteren naar CSV met aanhalings tekens rond twee kolommen</span><span class="sxs-lookup"><span data-stu-id="f2152-223">Example 10: Export to CSV with quotes around two columns</span></span>

<span data-ttu-id="f2152-224">In dit voor beeld wordt een **DateTime** -object geconverteerd naar een CSV-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="f2152-224">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | Export-Csv  -QuoteFields "DateTime","Date" -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="f2152-225">Voor beeld 11: exporteren naar CSV met alleen aanhalings tekens als dat nodig is</span><span class="sxs-lookup"><span data-stu-id="f2152-225">Example 11: Export to CSV with quotes only when needed</span></span>

<span data-ttu-id="f2152-226">In dit voor beeld wordt een **DateTime** -object geconverteerd naar een CSV-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="f2152-226">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | Export-Csv  -UseQuotes AsNeeded -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="f2152-227">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f2152-227">PARAMETERS</span></span>

### <span data-ttu-id="f2152-228">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="f2152-228">-Append</span></span>

<span data-ttu-id="f2152-229">Gebruik deze para meter zodat `Export-CSV` CSV-uitvoer aan het einde van het opgegeven bestand wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f2152-229">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="f2152-230">Zonder deze para meter `Export-CSV` vervangt de bestands inhoud zonder waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="f2152-230">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="f2152-231">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f2152-231">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f2152-232">-Scheidings teken</span><span class="sxs-lookup"><span data-stu-id="f2152-232">-Delimiter</span></span>

<span data-ttu-id="f2152-233">Hiermee wordt een scheidings teken opgegeven om de eigenschaps waarden van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="f2152-233">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="f2152-234">De standaard waarde is een komma ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="f2152-234">The default is a comma (`,`).</span></span> <span data-ttu-id="f2152-235">Voer een teken in, bijvoorbeeld een dubbele punt ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="f2152-235">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="f2152-236">Als u een punt komma () wilt opgeven `;` , plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="f2152-236">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="f2152-237">-Encoding</span><span class="sxs-lookup"><span data-stu-id="f2152-237">-Encoding</span></span>

<span data-ttu-id="f2152-238">Hiermee geeft u de code ring voor het geëxporteerde CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-238">Specifies the encoding for the exported CSV file.</span></span> <span data-ttu-id="f2152-239">De standaardwaarde is `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="f2152-239">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="f2152-240">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="f2152-240">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f2152-241">`ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="f2152-241">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="f2152-242">`bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="f2152-242">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="f2152-243">`oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.</span><span class="sxs-lookup"><span data-stu-id="f2152-243">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="f2152-244">`unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="f2152-244">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="f2152-245">`utf7`: Wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="f2152-245">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="f2152-246">`utf8`: Wordt gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="f2152-246">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="f2152-247">`utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="f2152-247">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="f2152-248">`utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="f2152-248">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="f2152-249">`utf32`: Gecodeerd in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="f2152-249">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="f2152-250">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="f2152-250">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="f2152-251">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f2152-251">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2152-252">-Force</span><span class="sxs-lookup"><span data-stu-id="f2152-252">-Force</span></span>

<span data-ttu-id="f2152-253">Met deze para meter kunt `Export-Csv` u bestanden overschrijven met het kenmerk **alleen-lezen** .</span><span class="sxs-lookup"><span data-stu-id="f2152-253">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="f2152-254">Wanneer **Force** -en **Append** -para meters worden gecombineerd, kunnen objecten die niet-overeenkomende eigenschappen bevatten, naar een CSV-bestand worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="f2152-254">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="f2152-255">Alleen de eigenschappen die overeenkomen, worden naar het bestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="f2152-255">Only the properties that match are written to the file.</span></span> <span data-ttu-id="f2152-256">De eigenschappen die niet overeenkomen, worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f2152-256">The mismatched properties are discarded.</span></span>

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

### <span data-ttu-id="f2152-257">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="f2152-257">-IncludeTypeInformation</span></span>

<span data-ttu-id="f2152-258">Als deze para meter wordt gebruikt, bevat de eerste regel van de CSV-uitvoer **#TYPE** gevolgd door de volledig gekwalificeerde naam van het object type.</span><span class="sxs-lookup"><span data-stu-id="f2152-258">When this parameter is used the first line of the CSV output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="f2152-259">Bijvoorbeeld **#TYPE System. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="f2152-259">For example, **#TYPE System.Diagnostics.Process**.</span></span>

<span data-ttu-id="f2152-260">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f2152-260">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2152-261">-Input object</span><span class="sxs-lookup"><span data-stu-id="f2152-261">-InputObject</span></span>

<span data-ttu-id="f2152-262">Geeft aan welke objecten als CSV-teken reeksen moeten worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="f2152-262">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="f2152-263">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2152-263">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="f2152-264">U kunt ook objecten pipeen naar `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="f2152-264">You can also pipe objects to `Export-CSV`.</span></span>

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

### <span data-ttu-id="f2152-265">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f2152-265">-LiteralPath</span></span>

<span data-ttu-id="f2152-266">Hiermee geeft u het pad naar het CSV-uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-266">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="f2152-267">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="f2152-267">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="f2152-268">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="f2152-268">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f2152-269">Als het pad escape-tekens bevat, gebruikt u enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="f2152-269">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="f2152-270">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2152-270">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2152-271">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="f2152-271">-NoClobber</span></span>

<span data-ttu-id="f2152-272">Gebruik deze para meter om `Export-CSV` een bestaand bestand niet te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="f2152-272">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="f2152-273">Als het bestand zich in het opgegeven pad bevindt, wordt `Export-CSV` het bestand standaard zonder waarschuwing overschreven.</span><span class="sxs-lookup"><span data-stu-id="f2152-273">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="f2152-274">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="f2152-274">-NoTypeInformation</span></span>

<span data-ttu-id="f2152-275">Hiermee verwijdert u de **#TYPE** informatie uit de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f2152-275">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="f2152-276">Deze para meter werd de standaard waarde in Power shell 6,0 en is opgenomen voor achterwaartse compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="f2152-276">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="f2152-277">-Path</span><span class="sxs-lookup"><span data-stu-id="f2152-277">-Path</span></span>

<span data-ttu-id="f2152-278">Een vereiste para meter waarmee de locatie wordt opgegeven waarop het CSV-uitvoer bestand moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f2152-278">A required parameter that specifies the location to save the CSV output file.</span></span>

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

### <span data-ttu-id="f2152-279">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="f2152-279">-UseCulture</span></span>

<span data-ttu-id="f2152-280">Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="f2152-280">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="f2152-281">Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="f2152-281">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="f2152-282">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f2152-282">-Confirm</span></span>

<span data-ttu-id="f2152-283">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f2152-283">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f2152-284">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f2152-284">-WhatIf</span></span>

<span data-ttu-id="f2152-285">Hiermee voor komt u dat de cmdlet wordt verwerkt of dat er wijzigingen worden aangebracht.</span><span class="sxs-lookup"><span data-stu-id="f2152-285">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="f2152-286">De uitvoer laat zien wat er zou gebeuren als de cmdlet werd uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f2152-286">The output shows what would happen if the cmdlet were run.</span></span>

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

### <span data-ttu-id="f2152-287">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="f2152-287">-QuoteFields</span></span>

<span data-ttu-id="f2152-288">Hiermee geeft u de namen van de kolommen die moeten worden genoteerd.</span><span class="sxs-lookup"><span data-stu-id="f2152-288">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="f2152-289">Als deze para meter wordt gebruikt, worden alleen de opgegeven kolommen genoteerd.</span><span class="sxs-lookup"><span data-stu-id="f2152-289">When this parameter is used, only the specified columns are quoted.</span></span> <span data-ttu-id="f2152-290">Deze para meter is toegevoegd in Power shell 7,0.</span><span class="sxs-lookup"><span data-stu-id="f2152-290">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2152-291">-UseQuotes</span><span class="sxs-lookup"><span data-stu-id="f2152-291">-UseQuotes</span></span>

<span data-ttu-id="f2152-292">Hiermee geeft u op wanneer aanhalings tekens worden gebruikt in de CSV-bestanden.</span><span class="sxs-lookup"><span data-stu-id="f2152-292">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="f2152-293">Mogelijke waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="f2152-293">Possible values are:</span></span>

- <span data-ttu-id="f2152-294">Nooit: niets citeren</span><span class="sxs-lookup"><span data-stu-id="f2152-294">Never - don't quote anything</span></span>
- <span data-ttu-id="f2152-295">Altijd: alle citaten (standaard gedrag)</span><span class="sxs-lookup"><span data-stu-id="f2152-295">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="f2152-296">Alleen-AsNeeded die een scheidings teken bevatten</span><span class="sxs-lookup"><span data-stu-id="f2152-296">AsNeeded - only quote fields that contain a delimiter character</span></span>

<span data-ttu-id="f2152-297">Deze para meter is toegevoegd in Power shell 7,0.</span><span class="sxs-lookup"><span data-stu-id="f2152-297">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2152-298">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2152-298">CommonParameters</span></span>

<span data-ttu-id="f2152-299">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f2152-299">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2152-300">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f2152-300">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2152-301">INVOER</span><span class="sxs-lookup"><span data-stu-id="f2152-301">INPUTS</span></span>

### <span data-ttu-id="f2152-302">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="f2152-302">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f2152-303">U kunt elk object met een adapter voor een Extended-type systeem (ETS) aan `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="f2152-303">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="f2152-304">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f2152-304">OUTPUTS</span></span>

### <span data-ttu-id="f2152-305">System. String</span><span class="sxs-lookup"><span data-stu-id="f2152-305">System.String</span></span>

<span data-ttu-id="f2152-306">De CSV-lijst wordt verzonden naar het bestand dat is opgegeven in de para meter Path.</span><span class="sxs-lookup"><span data-stu-id="f2152-306">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="f2152-307">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f2152-307">NOTES</span></span>

<span data-ttu-id="f2152-308">De `Export-CSV` cmdlet converteert de objecten die u verzendt naar een reeks CSV-teken reeksen en slaat deze op in het opgegeven tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-308">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="f2152-309">U kunt gebruiken `Export-CSV -IncludeTypeInformation` om objecten op te slaan in een CSV-bestand en vervolgens de `Import-Csv` cmdlet te gebruiken om objecten te maken op basis van de tekst in het CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-309">You can use `Export-CSV -IncludeTypeInformation` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the text in the CSV file.</span></span>

<span data-ttu-id="f2152-310">In het CSV-bestand wordt elk object vertegenwoordigd door een door komma's gescheiden lijst van de eigenschaps waarden van het object.</span><span class="sxs-lookup"><span data-stu-id="f2152-310">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="f2152-311">De eigenschaps waarden worden geconverteerd naar teken reeksen met de methode **toString ()** .</span><span class="sxs-lookup"><span data-stu-id="f2152-311">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="f2152-312">De teken reeksen worden vertegenwoordigd door de naam van de eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="f2152-312">The strings are represented by the property value name.</span></span> <span data-ttu-id="f2152-313">`Export-CSV -IncludeTypeInformation` exporteert de methoden van het object niet.</span><span class="sxs-lookup"><span data-stu-id="f2152-313">`Export-CSV -IncludeTypeInformation` does not export the methods of the object.</span></span>

<span data-ttu-id="f2152-314">De CSV-teken reeksen worden als volgt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="f2152-314">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="f2152-315">Als **IncludeTypeInformation** wordt gebruikt, bevat de eerste teken reeks de **#TYPE** informatie header, gevolgd door de volledig gekwalificeerde naam van het object type.</span><span class="sxs-lookup"><span data-stu-id="f2152-315">If **IncludeTypeInformation** is used, the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span>
  <span data-ttu-id="f2152-316">Bijvoorbeeld **#TYPE System. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="f2152-316">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="f2152-317">Als **IncludeTypeInformation** niet wordt gebruikt, bevat de eerste teken reeks de kolom koppen.</span><span class="sxs-lookup"><span data-stu-id="f2152-317">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="f2152-318">De headers bevatten de eigenschaps namen van het eerste object als een door komma's gescheiden lijst.</span><span class="sxs-lookup"><span data-stu-id="f2152-318">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="f2152-319">De resterende teken reeksen bevatten door komma's gescheiden lijsten van de eigenschaps waarden van elk object.</span><span class="sxs-lookup"><span data-stu-id="f2152-319">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="f2152-320">Vanaf Power shell 6,0 is het standaard gedrag van de `Export-CSV` **#TYPE** informatie in het CSV-bestand en **NoTypeInformation** wordt geïmpliceerd.</span><span class="sxs-lookup"><span data-stu-id="f2152-320">Beginning with PowerShell 6.0 the default behavior of `Export-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="f2152-321">**IncludeTypeInformation** kan worden gebruikt om de **#TYPE** informatie op te neemt en het standaard gedrag van `Export-CSV` vóór Power shell 6,0 te emuleren.</span><span class="sxs-lookup"><span data-stu-id="f2152-321">**IncludeTypeInformation** can be used to include the **#TYPE** Information and emulate the default behavior of `Export-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="f2152-322">Wanneer u meerdere objecten indient `Export-CSV` , `Export-CSV` organiseert het bestand op basis van de eigenschappen van het eerste object dat u verzendt.</span><span class="sxs-lookup"><span data-stu-id="f2152-322">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="f2152-323">Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de eigenschaps waarde van dat object null, zoals wordt weer gegeven in twee opeenvolgende komma's.</span><span class="sxs-lookup"><span data-stu-id="f2152-323">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="f2152-324">Als de resterende objecten extra eigenschappen hebben, worden deze eigenschaps waarden niet opgenomen in het bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-324">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="f2152-325">U kunt de `Import-Csv` cmdlet gebruiken om objecten opnieuw te maken op basis van de CSV-teken reeksen in de bestanden.</span><span class="sxs-lookup"><span data-stu-id="f2152-325">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="f2152-326">De resulterende objecten zijn CSV-versies van de oorspronkelijke objecten die bestaan uit teken reeks representaties van de eigenschaps waarden en geen methoden.</span><span class="sxs-lookup"><span data-stu-id="f2152-326">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="f2152-327">Met `ConvertTo-Csv` de `ConvertFrom-Csv` cmdlets en worden objecten GECONVERTEERD naar CSV-teken reeksen en CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2152-327">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="f2152-328">`Export-CSV` is hetzelfde als `ConvertTo-CSV` , behalve dat de CSV-teken reeksen worden opgeslagen in een bestand.</span><span class="sxs-lookup"><span data-stu-id="f2152-328">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="f2152-329">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f2152-329">RELATED LINKS</span></span>

[<span data-ttu-id="f2152-330">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="f2152-330">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="f2152-331">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="f2152-331">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="f2152-332">Format-Table</span><span class="sxs-lookup"><span data-stu-id="f2152-332">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="f2152-333">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="f2152-333">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="f2152-334">Select-Object</span><span class="sxs-lookup"><span data-stu-id="f2152-334">Select-Object</span></span>](Select-Object.md)
