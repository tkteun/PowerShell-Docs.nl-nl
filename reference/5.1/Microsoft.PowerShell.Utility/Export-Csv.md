---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: 17c3ef3046ba8f0cca9a85cf41aaf683212a58e9
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913338"
---
# <span data-ttu-id="df814-102">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="df814-102">Export-Csv</span></span>

## <span data-ttu-id="df814-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="df814-103">SYNOPSIS</span></span>
<span data-ttu-id="df814-104">Hiermee worden objecten geconverteerd naar een reeks teken reeksen met door komma's gescheiden waarden (CSV) en worden de teken reeksen opgeslagen in een bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-104">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="df814-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="df814-105">SYNTAX</span></span>

### <span data-ttu-id="df814-106">Scheidings teken (standaard)</span><span class="sxs-lookup"><span data-stu-id="df814-106">Delimiter (Default)</span></span>

```
Export-Csv [[-Path] <string>] [[-Delimiter] <char>] -InputObject <psobject> [-LiteralPath <string>]
 [-Force] [-NoClobber] [-Encoding <string>] [-Append] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="df814-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="df814-107">UseCulture</span></span>

```
Export-Csv [[-Path] <string>] -InputObject <psobject> [-LiteralPath <string>] [-Force] [-NoClobber]
 [-Encoding <string>] [-Append] [-UseCulture] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="df814-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="df814-108">DESCRIPTION</span></span>

<span data-ttu-id="df814-109">De `Export-CSV` cmdlet maakt een CSV-bestand van de objecten die u verzendt.</span><span class="sxs-lookup"><span data-stu-id="df814-109">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="df814-110">Elk object is een rij met een door komma's gescheiden lijst van de eigenschaps waarden van het object.</span><span class="sxs-lookup"><span data-stu-id="df814-110">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="df814-111">U kunt de `Export-CSV` cmdlet gebruiken om werk bladen te maken en gegevens te delen met Program ma's die CSV-bestanden accepteren als invoer.</span><span class="sxs-lookup"><span data-stu-id="df814-111">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="df814-112">Maak objecten niet op voordat u ze naar de `Export-CSV` cmdlet verzendt.</span><span class="sxs-lookup"><span data-stu-id="df814-112">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="df814-113">Als u `Export-CSV` opgemaakte objecten ontvangt, bevat het CSV-bestand de indelings eigenschappen in plaats van de object eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="df814-113">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="df814-114">Als u alleen geselecteerde eigenschappen van een object wilt exporteren, gebruikt u de `Select-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df814-114">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="df814-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="df814-115">EXAMPLES</span></span>

### <span data-ttu-id="df814-116">Voor beeld 1: proces eigenschappen exporteren naar een CSV-bestand</span><span class="sxs-lookup"><span data-stu-id="df814-116">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="df814-117">In dit voor beeld worden **proces** objecten met specifieke eigenschappen geselecteerd, worden de objecten geëxporteerd naar een CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-117">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

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

<span data-ttu-id="df814-118">`Get-Process`Met de cmdlet worden de **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="df814-118">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="df814-119">De para meter **name** filtert de uitvoer zo dat alleen de WmiPrvSE-proces objecten worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="df814-119">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="df814-120">De proces objecten worden in de pijp lijn naar de `Select-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-120">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="df814-121">`Select-Object` gebruikt de para meter **Property** om een subset van eigenschappen van proces objecten te selecteren.</span><span class="sxs-lookup"><span data-stu-id="df814-121">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="df814-122">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-122">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="df814-123">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="df814-123">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="df814-124">De para meter **Path** geeft aan dat het WmiData.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="df814-124">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="df814-125">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="df814-125">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="df814-126">De `Import-Csv` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="df814-126">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="df814-127">Voor beeld 2: processen exporteren naar een bestand met door komma's gescheiden waarden</span><span class="sxs-lookup"><span data-stu-id="df814-127">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="df814-128">In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-128">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="df814-129">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="df814-129">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="df814-130">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-130">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="df814-131">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="df814-131">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="df814-132">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="df814-132">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="df814-133">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="df814-133">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="df814-134">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="df814-134">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="df814-135">Voor beeld 3: processen exporteren naar een door punt komma's gescheiden bestand</span><span class="sxs-lookup"><span data-stu-id="df814-135">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="df814-136">In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een bestand met een punt komma als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="df814-136">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="df814-137">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="df814-137">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="df814-138">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-138">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="df814-139">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="df814-139">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="df814-140">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="df814-140">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="df814-141">De **scheidings** parameter geeft een punt komma om de teken reeks waarden te scheiden.</span><span class="sxs-lookup"><span data-stu-id="df814-141">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="df814-142">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="df814-142">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="df814-143">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="df814-143">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="df814-144">Voor beeld 4: processen exporteren met behulp van het lijst scheidings teken van de huidige cultuur</span><span class="sxs-lookup"><span data-stu-id="df814-144">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="df814-145">In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-145">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="df814-146">Het scheidings teken is het lijst scheidings teken van de huidige cultuur.</span><span class="sxs-lookup"><span data-stu-id="df814-146">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="df814-147">De `Get-Culture` cmdlet maakt gebruik van de geneste eigenschappen **Eigenschappen** en **ListSeparator** en geeft het standaard lijst scheidings teken van de huidige cultuur weer.</span><span class="sxs-lookup"><span data-stu-id="df814-147">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="df814-148">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="df814-148">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="df814-149">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-149">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="df814-150">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="df814-150">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="df814-151">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="df814-151">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="df814-152">De para meter **UseCulture** gebruikt het standaard lijst scheidings teken van de huidige cultuur als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="df814-152">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="df814-153">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="df814-153">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="df814-154">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="df814-154">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="df814-155">Voor beeld 5: processen exporteren met type-informatie</span><span class="sxs-lookup"><span data-stu-id="df814-155">Example 5: Export processes with type information</span></span>

<span data-ttu-id="df814-156">In dit voor beeld wordt uitgelegd hoe u de **#TYPE** header gegevens opneemt in een CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-156">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="df814-157">De **#TYPE** header is de standaard waarde in versies voorafgaand aan power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="df814-157">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="df814-158">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="df814-158">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="df814-159">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-159">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="df814-160">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="df814-160">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="df814-161">De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="df814-161">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="df814-162">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="df814-162">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="df814-163">Voor beeld 6: objecten exporteren en toevoegen aan een CSV-bestand</span><span class="sxs-lookup"><span data-stu-id="df814-163">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="df814-164">In dit voor beeld wordt beschreven hoe u objecten exporteert naar een CSV-bestand en hoe u de para meter **Append** gebruikt om objecten toe te voegen aan een bestaand bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-164">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

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

<span data-ttu-id="df814-165">`Get-Service`Met de cmdlet worden service objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="df814-165">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="df814-166">De para meter **DisplayName** retourneert services die de Word-toepassing bevatten.</span><span class="sxs-lookup"><span data-stu-id="df814-166">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="df814-167">De service objecten worden naar de-cmdlet verzonden via de pijp lijn `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="df814-167">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="df814-168">`Select-Object` maakt gebruik van de para meter **Property** om de eigenschappen **DisplayName** en **status** op te geven.</span><span class="sxs-lookup"><span data-stu-id="df814-168">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="df814-169">De `$AppService` variabele slaat de objecten op.</span><span class="sxs-lookup"><span data-stu-id="df814-169">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="df814-170">De `$AppService` objecten worden naar de-cmdlet verzonden via de pijp lijn `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="df814-170">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="df814-171">`Export-Csv` Hiermee worden de service objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="df814-171">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="df814-172">De para meter **Path** geeft aan dat het Services.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="df814-172">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="df814-173">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="df814-173">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="df814-174">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="df814-174">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="df814-175">De `Get-Service` `Select-Object` cmdlets en worden herhaald voor services die het woord Windows bevatten.</span><span class="sxs-lookup"><span data-stu-id="df814-175">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="df814-176">De `$WinService` variabele slaat de service objecten op.</span><span class="sxs-lookup"><span data-stu-id="df814-176">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="df814-177">De `Export-Csv` cmdlet gebruikt de para meter **Append** om op te geven dat de `$WinService` objecten worden toegevoegd aan het bestaande Services.csv-bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-177">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="df814-178">De `Get-Content` cmdlet wordt herhaald om het bijgewerkte bestand weer te geven dat de toegevoegde gegevens bevat.</span><span class="sxs-lookup"><span data-stu-id="df814-178">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="df814-179">Voor beeld 7: met de cmdlet Format in een pijp lijn worden onverwachte resultaten gemaakt</span><span class="sxs-lookup"><span data-stu-id="df814-179">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="df814-180">In dit voor beeld ziet u waarom het belang rijk is dat u geen indelings-cmdlet kunt gebruiken in een pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="df814-180">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="df814-181">Als onverwachte uitvoer wordt ontvangen, moet u de pijplijn syntaxis oplossen.</span><span class="sxs-lookup"><span data-stu-id="df814-181">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

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

<span data-ttu-id="df814-182">De `Get-Date` cmdlet haalt het **DateTime** -object op.</span><span class="sxs-lookup"><span data-stu-id="df814-182">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="df814-183">Het object wordt vanuit de pijp lijn naar de `Select-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-183">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="df814-184">`Select-Object` gebruikt de para meter **Property** om een subset van object eigenschappen te selecteren.</span><span class="sxs-lookup"><span data-stu-id="df814-184">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="df814-185">Het object wordt vanuit de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-185">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="df814-186">`Export-Csv` converteert het object naar een CSV-indeling.</span><span class="sxs-lookup"><span data-stu-id="df814-186">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="df814-187">De para meter **Path** geeft aan dat het DateTime.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="df814-187">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="df814-188">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="df814-188">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="df814-189">De `Get-Content` cmdlet gebruikt de para meter **Path** om het CSV-bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="df814-189">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="df814-190">Wanneer de `Format-Table` cmdlet wordt gebruikt in de pijp lijn om eigenschappen te selecteren, worden er onverwachte resultaten ontvangen.</span><span class="sxs-lookup"><span data-stu-id="df814-190">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="df814-191">`Format-Table` Hiermee worden de objecten van de tabel indeling naar de-cmdlet van de pijp lijn in `Export-Csv` plaats van het **DateTime** -object verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-191">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="df814-192">`Export-Csv` de tabel indelings objecten worden geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="df814-192">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="df814-193">`Get-Content`Met de cmdlet wordt het CSV-bestand weer gegeven dat de tabel indelings objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="df814-193">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="df814-194">Voor beeld 8: de para meter Force gebruiken om alleen-lezen bestanden te overschrijven</span><span class="sxs-lookup"><span data-stu-id="df814-194">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="df814-195">In dit voor beeld maakt u een leeg bestand met het kenmerk alleen-lezen en gebruikt u de para meter **Force** om het bestand bij te werken.</span><span class="sxs-lookup"><span data-stu-id="df814-195">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

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

<span data-ttu-id="df814-196">De `New-Item` cmdlet maakt gebruik van de para meters **Path** en **item** type voor het maken van het ReadOnly.csv-bestand in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="df814-196">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="df814-197">De `Set-ItemProperty` cmdlet gebruikt de para meters **name** en **Value** om de eigenschap **IsReadOnly** van het bestand te wijzigen in True.</span><span class="sxs-lookup"><span data-stu-id="df814-197">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="df814-198">`Get-Process`Met de cmdlet worden **proces** objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="df814-198">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="df814-199">De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-199">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="df814-200">`Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="df814-200">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="df814-201">De para meter **Path** geeft aan dat het ReadOnly.csv bestand wordt opgeslagen in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="df814-201">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="df814-202">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="df814-202">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="df814-203">In de uitvoer ziet u dat het bestand niet is geschreven, omdat de toegang wordt geweigerd.</span><span class="sxs-lookup"><span data-stu-id="df814-203">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="df814-204">De para meter **Force** wordt toegevoegd aan de `Export-Csv` cmdlet om de export af te dwingen om naar het bestand te schrijven.</span><span class="sxs-lookup"><span data-stu-id="df814-204">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="df814-205">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="df814-205">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="df814-206">Voor beeld 9: de para meter Force gebruiken met Append</span><span class="sxs-lookup"><span data-stu-id="df814-206">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="df814-207">In dit voor beeld ziet u hoe u de para meters **Force** en **Append** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="df814-207">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="df814-208">Als deze para meters worden gecombineerd, kunnen niet-overeenkomende object eigenschappen naar een CSV-bestand worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="df814-208">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

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

<span data-ttu-id="df814-209">Een expressie maakt de **PSCustomObject** met de **naam** en **versie** -eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="df814-209">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="df814-210">De waarden worden opgeslagen in de `$Content` variabele.</span><span class="sxs-lookup"><span data-stu-id="df814-210">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="df814-211">De `$Content` variabele wordt via de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-211">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="df814-212">`Export-Csv` maakt gebruik van de para meter **Path** en slaat het ParmFile.csv-bestand op in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="df814-212">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="df814-213">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="df814-213">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="df814-214">Met een andere expressie maakt u een **PSCustomObject** met de **naam** en **editie** -eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="df814-214">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="df814-215">De waarden worden opgeslagen in de `$AdditionalContent` variabele.</span><span class="sxs-lookup"><span data-stu-id="df814-215">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="df814-216">De `$AdditionalContent` variabele wordt via de pijp lijn naar de `Export-Csv` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="df814-216">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="df814-217">De **toevoeg** parameter wordt gebruikt om de gegevens aan het bestand toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="df814-217">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="df814-218">De toevoeg bewerking mislukt omdat de naam van een eigenschap niet overeenkomt met de **versie** en **editie**.</span><span class="sxs-lookup"><span data-stu-id="df814-218">The append fails because there is a property name mismatch between **Version** and **Edition**.</span></span>

<span data-ttu-id="df814-219">De `Export-Csv` cmdlet **Force** -para meter wordt gebruikt om het exporteren af te dwingen om naar het bestand te schrijven.</span><span class="sxs-lookup"><span data-stu-id="df814-219">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="df814-220">De **editie** -eigenschap wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="df814-220">The **Edition** property is discarded.</span></span> <span data-ttu-id="df814-221">De `Import-Csv` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="df814-221">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

## <span data-ttu-id="df814-222">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="df814-222">PARAMETERS</span></span>

### <span data-ttu-id="df814-223">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="df814-223">-Append</span></span>

<span data-ttu-id="df814-224">Gebruik deze para meter zodat `Export-CSV` CSV-uitvoer aan het einde van het opgegeven bestand wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="df814-224">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="df814-225">Zonder deze para meter `Export-CSV` vervangt de bestands inhoud zonder waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="df814-225">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="df814-226">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="df814-226">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="df814-227">-Scheidings teken</span><span class="sxs-lookup"><span data-stu-id="df814-227">-Delimiter</span></span>

<span data-ttu-id="df814-228">Hiermee wordt een scheidings teken opgegeven om de eigenschaps waarden van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="df814-228">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="df814-229">De standaard waarde is een komma ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="df814-229">The default is a comma (`,`).</span></span> <span data-ttu-id="df814-230">Voer een teken in, bijvoorbeeld een dubbele punt ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="df814-230">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="df814-231">Als u een punt komma () wilt opgeven `;` , plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="df814-231">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="df814-232">-Encoding</span><span class="sxs-lookup"><span data-stu-id="df814-232">-Encoding</span></span>

<span data-ttu-id="df814-233">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="df814-233">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="df814-234">De standaardwaarde is `ASCII`.</span><span class="sxs-lookup"><span data-stu-id="df814-234">The default value is `ASCII`.</span></span>

<span data-ttu-id="df814-235">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="df814-235">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="df814-236">`ASCII` Maakt gebruik van ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="df814-236">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="df814-237">`BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="df814-237">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="df814-238">`Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).</span><span class="sxs-lookup"><span data-stu-id="df814-238">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="df814-239">`OEM` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.</span><span class="sxs-lookup"><span data-stu-id="df814-239">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="df814-240">`Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="df814-240">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="df814-241">`UTF7` Maakt gebruik van UTF-7.</span><span class="sxs-lookup"><span data-stu-id="df814-241">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="df814-242">`UTF8` Maakt gebruik van UTF-8.</span><span class="sxs-lookup"><span data-stu-id="df814-242">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="df814-243">`UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="df814-243">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

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

### <span data-ttu-id="df814-244">-Force</span><span class="sxs-lookup"><span data-stu-id="df814-244">-Force</span></span>

<span data-ttu-id="df814-245">Met deze para meter kunt `Export-Csv` u bestanden overschrijven met het kenmerk **alleen-lezen** .</span><span class="sxs-lookup"><span data-stu-id="df814-245">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="df814-246">Wanneer **Force** -en **Append** -para meters worden gecombineerd, kunnen objecten die niet-overeenkomende eigenschappen bevatten, naar een CSV-bestand worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="df814-246">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="df814-247">Alleen de eigenschappen die overeenkomen, worden naar het bestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="df814-247">Only the properties that match are written to the file.</span></span> <span data-ttu-id="df814-248">De eigenschappen die niet overeenkomen, worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="df814-248">The mismatched properties are discarded.</span></span>

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

### <span data-ttu-id="df814-249">-Input object</span><span class="sxs-lookup"><span data-stu-id="df814-249">-InputObject</span></span>

<span data-ttu-id="df814-250">Geeft aan welke objecten als CSV-teken reeksen moeten worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="df814-250">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="df814-251">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="df814-251">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="df814-252">U kunt ook objecten pipeen naar `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="df814-252">You can also pipe objects to `Export-CSV`.</span></span>

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

### <span data-ttu-id="df814-253">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="df814-253">-LiteralPath</span></span>

<span data-ttu-id="df814-254">Hiermee geeft u het pad naar het CSV-uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-254">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="df814-255">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="df814-255">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="df814-256">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="df814-256">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="df814-257">Als het pad escape-tekens bevat, gebruikt u enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="df814-257">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="df814-258">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="df814-258">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="df814-259">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="df814-259">-NoClobber</span></span>

<span data-ttu-id="df814-260">Gebruik deze para meter om `Export-CSV` een bestaand bestand niet te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="df814-260">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="df814-261">Als het bestand zich in het opgegeven pad bevindt, wordt `Export-CSV` het bestand standaard zonder waarschuwing overschreven.</span><span class="sxs-lookup"><span data-stu-id="df814-261">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="df814-262">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="df814-262">-NoTypeInformation</span></span>

<span data-ttu-id="df814-263">Hiermee verwijdert u de **#TYPE** informatie uit de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="df814-263">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="df814-264">Deze para meter werd de standaard waarde in Power shell 6,0 en is opgenomen voor achterwaartse compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="df814-264">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="df814-265">-Path</span><span class="sxs-lookup"><span data-stu-id="df814-265">-Path</span></span>

<span data-ttu-id="df814-266">Een vereiste para meter waarmee de locatie wordt opgegeven waarop het CSV-uitvoer bestand moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="df814-266">A required parameter that specifies the location to save the CSV output file.</span></span>

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

### <span data-ttu-id="df814-267">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="df814-267">-UseCulture</span></span>

<span data-ttu-id="df814-268">Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="df814-268">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="df814-269">Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="df814-269">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="df814-270">-Confirm</span><span class="sxs-lookup"><span data-stu-id="df814-270">-Confirm</span></span>

<span data-ttu-id="df814-271">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="df814-271">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="df814-272">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="df814-272">-WhatIf</span></span>

<span data-ttu-id="df814-273">Hiermee voor komt u dat de cmdlet wordt verwerkt of dat er wijzigingen worden aangebracht.</span><span class="sxs-lookup"><span data-stu-id="df814-273">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="df814-274">De uitvoer laat zien wat er zou gebeuren als de cmdlet werd uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="df814-274">The output shows what would happen if the cmdlet were run.</span></span>

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

### <span data-ttu-id="df814-275">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="df814-275">CommonParameters</span></span>

<span data-ttu-id="df814-276">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="df814-276">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="df814-277">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="df814-277">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="df814-278">INVOER</span><span class="sxs-lookup"><span data-stu-id="df814-278">INPUTS</span></span>

### <span data-ttu-id="df814-279">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="df814-279">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="df814-280">U kunt elk object met een adapter voor een Extended-type systeem (ETS) aan `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="df814-280">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="df814-281">UITVOER</span><span class="sxs-lookup"><span data-stu-id="df814-281">OUTPUTS</span></span>

### <span data-ttu-id="df814-282">System. String</span><span class="sxs-lookup"><span data-stu-id="df814-282">System.String</span></span>

<span data-ttu-id="df814-283">De CSV-lijst wordt verzonden naar het bestand dat is opgegeven in de para meter Path.</span><span class="sxs-lookup"><span data-stu-id="df814-283">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="df814-284">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="df814-284">NOTES</span></span>

<span data-ttu-id="df814-285">De `Export-CSV` cmdlet converteert de objecten die u verzendt naar een reeks CSV-teken reeksen en slaat deze op in het opgegeven tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-285">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="df814-286">U kunt gebruiken `Export-CSV` om objecten op te slaan in een CSV-bestand en vervolgens de `Import-Csv` cmdlet te gebruiken om objecten te maken vanuit het CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-286">You can use `Export-CSV` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the CSV file.</span></span>

<span data-ttu-id="df814-287">In het CSV-bestand wordt elk object vertegenwoordigd door een door komma's gescheiden lijst van de eigenschaps waarden van het object.</span><span class="sxs-lookup"><span data-stu-id="df814-287">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="df814-288">De eigenschaps waarden worden geconverteerd naar teken reeksen met de methode **toString ()** .</span><span class="sxs-lookup"><span data-stu-id="df814-288">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="df814-289">De teken reeksen worden vertegenwoordigd door de naam van de eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="df814-289">The strings are represented by the property value name.</span></span> <span data-ttu-id="df814-290">Export-CSV exporteert de methoden van het object niet.</span><span class="sxs-lookup"><span data-stu-id="df814-290">\`Export-CSV does not export the methods of the object.</span></span>

<span data-ttu-id="df814-291">De CSV-teken reeksen worden als volgt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="df814-291">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="df814-292">De eerste teken reeks bevat standaard de **#TYPE** informatie header, gevolgd door de volledig gekwalificeerde naam van het object type.</span><span class="sxs-lookup"><span data-stu-id="df814-292">By default the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span> <span data-ttu-id="df814-293">Bijvoorbeeld **#TYPE System. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="df814-293">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="df814-294">Als **NoTypeInformation** wordt gebruikt, bevat de eerste teken reeks de kolom koppen.</span><span class="sxs-lookup"><span data-stu-id="df814-294">If **NoTypeInformation** is used the first string includes the column headers.</span></span> <span data-ttu-id="df814-295">De headers bevatten de eigenschaps namen van het eerste object als een door komma's gescheiden lijst.</span><span class="sxs-lookup"><span data-stu-id="df814-295">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="df814-296">De resterende teken reeksen bevatten door komma's gescheiden lijsten van de eigenschaps waarden van elk object.</span><span class="sxs-lookup"><span data-stu-id="df814-296">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="df814-297">Wanneer u meerdere objecten indient `Export-CSV` , `Export-CSV` organiseert het bestand op basis van de eigenschappen van het eerste object dat u verzendt.</span><span class="sxs-lookup"><span data-stu-id="df814-297">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="df814-298">Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de eigenschaps waarde van dat object null, zoals wordt weer gegeven in twee opeenvolgende komma's.</span><span class="sxs-lookup"><span data-stu-id="df814-298">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="df814-299">Als de resterende objecten extra eigenschappen hebben, worden deze eigenschaps waarden niet opgenomen in het bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-299">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="df814-300">U kunt de `Import-Csv` cmdlet gebruiken om objecten opnieuw te maken op basis van de CSV-teken reeksen in de bestanden.</span><span class="sxs-lookup"><span data-stu-id="df814-300">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="df814-301">De resulterende objecten zijn CSV-versies van de oorspronkelijke objecten die bestaan uit teken reeks representaties van de eigenschaps waarden en geen methoden.</span><span class="sxs-lookup"><span data-stu-id="df814-301">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="df814-302">Met `ConvertTo-Csv` de `ConvertFrom-Csv` cmdlets en worden objecten GECONVERTEERD naar CSV-teken reeksen en CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="df814-302">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="df814-303">`Export-CSV` is hetzelfde als `ConvertTo-CSV` , behalve dat de CSV-teken reeksen worden opgeslagen in een bestand.</span><span class="sxs-lookup"><span data-stu-id="df814-303">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="df814-304">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="df814-304">RELATED LINKS</span></span>

[<span data-ttu-id="df814-305">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="df814-305">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="df814-306">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="df814-306">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="df814-307">Format-Table</span><span class="sxs-lookup"><span data-stu-id="df814-307">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="df814-308">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="df814-308">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="df814-309">Select-Object</span><span class="sxs-lookup"><span data-stu-id="df814-309">Select-Object</span></span>](Select-Object.md)
