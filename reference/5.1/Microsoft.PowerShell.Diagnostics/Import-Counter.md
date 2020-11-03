---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/import-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Counter
ms.openlocfilehash: 837f6b4b3b2869c6f74b3b02904dd43b73f6bcd5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250119"
---
# <span data-ttu-id="1aeff-103">Import-Counter</span><span class="sxs-lookup"><span data-stu-id="1aeff-103">Import-Counter</span></span>

## <span data-ttu-id="1aeff-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1aeff-104">SYNOPSIS</span></span>
<span data-ttu-id="1aeff-105">Importeert logboek bestanden voor prestatie meter items en maakt de objecten die elk item voorbeeld vertegenwoordigen in het logboek.</span><span class="sxs-lookup"><span data-stu-id="1aeff-105">Imports performance counter log files and creates the objects that represent each counter sample in the log.</span></span>

## <span data-ttu-id="1aeff-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1aeff-106">SYNTAX</span></span>

### <span data-ttu-id="1aeff-107">GetCounterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="1aeff-107">GetCounterSet (Default)</span></span>

```
Import-Counter [-Path] <String[]> [-StartTime <DateTime>] [-EndTime <DateTime>] [-Counter <String[]>]
 [-MaxSamples <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="1aeff-108">ListSetSet</span><span class="sxs-lookup"><span data-stu-id="1aeff-108">ListSetSet</span></span>

```
Import-Counter [-Path] <String[]> -ListSet <String[]> [<CommonParameters>]
```

### <span data-ttu-id="1aeff-109">Samenvattings</span><span class="sxs-lookup"><span data-stu-id="1aeff-109">SummarySet</span></span>

```
Import-Counter [-Path] <String[]> [-Summary] [<CommonParameters>]
```

## <span data-ttu-id="1aeff-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1aeff-110">DESCRIPTION</span></span>

<span data-ttu-id="1aeff-111">Met de cmdlet **import-Counter** worden prestatie meter gegevens uit logboek bestanden voor prestatie meter items geïmporteerd en worden objecten gemaakt voor elk item voorbeeld in het bestand.</span><span class="sxs-lookup"><span data-stu-id="1aeff-111">The **Import-Counter** cmdlet imports performance counter data from performance counter log files and creates objects for each counter sample in the file.</span></span>
<span data-ttu-id="1aeff-112">De **PerformanceCounterSampleSet** -objecten die worden gemaakt, zijn identiek aan de objecten die **Get-Counter** retourneert wanneer er prestatie meter gegevens worden verzameld.</span><span class="sxs-lookup"><span data-stu-id="1aeff-112">The **PerformanceCounterSampleSet** objects that it creates are identical to the objects that **Get-Counter** returns when it collects performance counter data.</span></span>

<span data-ttu-id="1aeff-113">U kunt gegevens importeren uit een bestand met door komma's gescheiden waarden (. CSV), een door tabs gescheiden waarde (. tsv) en logboek bestanden met de prestatie meter binary (. blg).</span><span class="sxs-lookup"><span data-stu-id="1aeff-113">You can import data from comma-separated value (.csv), tab-separated value ( .tsv), and binary performance log (.blg) performance log files.</span></span>
<span data-ttu-id="1aeff-114">Als u. blg-bestanden gebruikt, kunt u Maxi maal 32 bestanden importeren in elke opdracht.</span><span class="sxs-lookup"><span data-stu-id="1aeff-114">If you are using .blg files, you can import up to 32 files in each command.</span></span>
<span data-ttu-id="1aeff-115">U kunt de para meters van **import teller** gebruiken om de geïmporteerde gegevens te filteren.</span><span class="sxs-lookup"><span data-stu-id="1aeff-115">You can use the parameters of **Import-Counter** to filter the data that you import.</span></span>

<span data-ttu-id="1aeff-116">Met de Get-Counter-en Export-Counter-cmdlets kunt u met deze functie gegevens over prestatie meter items verzamelen, exporteren, importeren, combi neren, filteren, bewerken en opnieuw exporteren in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="1aeff-116">Along with the Get-Counter and Export-Counter cmdlets, this feature lets you collect, export, import, combine, filter, manipulate, and re-export performance counter data within Windows PowerShell.</span></span>

## <span data-ttu-id="1aeff-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1aeff-117">EXAMPLES</span></span>

### <span data-ttu-id="1aeff-118">Voor beeld 1: alle item gegevens uit een bestand importeren</span><span class="sxs-lookup"><span data-stu-id="1aeff-118">Example 1: Import all counter data from a file</span></span>

```powershell
$Data = Import-Counter -Path ProcessorData.csv
```

<span data-ttu-id="1aeff-119">Met deze opdracht worden alle item gegevens uit het ProcessorData.csv-bestand in de $Data-variabele geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="1aeff-119">This command imports all counter data from the ProcessorData.csv file into the $Data variable.</span></span>

### <span data-ttu-id="1aeff-120">Voor beeld 2: specifieke item gegevens uit een bestand importeren</span><span class="sxs-lookup"><span data-stu-id="1aeff-120">Example 2: Import specific counter data from a file</span></span>

```
PS C:\> $I = Import-Counter -Path "ProcessorData.blg" -Counter "\\SERVER01\Processor(_Total)\Interrupts/sec"
```

<span data-ttu-id="1aeff-121">Met deze opdracht worden alleen de item gegevens **' processor (_Total) \ interrupts/sec '** uit het bestand ProcessorData. blg geïmporteerd in de $I-variabele.</span><span class="sxs-lookup"><span data-stu-id="1aeff-121">This command imports only the **"Processor(_total)\Interrupts/sec"** counter data from the ProcessorData.blg file into the $I variable.</span></span>

### <span data-ttu-id="1aeff-122">Voor beeld 3: gegevens selecteren uit een prestatie meter item en deze vervolgens exporteren naar een bestand</span><span class="sxs-lookup"><span data-stu-id="1aeff-122">Example 3: Select data from a performance counter then export it to a file</span></span>

```
The first command uses **Import-Counter** to import all of the performance counter data from the ProcessorData.blg files. The command saves the data in the $Data variable.
PS C:\> $Data = Import-Counter .\ProcessorData.blg

The second command displays the counter paths in the $Data variable. To get the display shown in the command output, the example uses the Format-Table cmdlet to format as a table the counter paths of the first counter in the $Data variable.
PS C:\> $Data[0].CounterSamples | Format-Table -Property Path

Path
----
\\SERVER01\Processor(_Total)\DPC Rate
\\SERVER01\Processor(1)\DPC Rate
\\SERVER01\Processor(0)\DPC Rate
\\SERVER01\Processor(_Total)\% Idle Time
\\SERVER01\Processor(1)\% Idle Time
\\SERVER01\Processor(0)\% Idle Time
\\SERVER01\Processor(_Total)\% C3 Time
\\SERVER01\Processor(1)\% C3 Time

The third command gets the counter paths that end in "Interrupts/sec" and saves the paths in the $IntCtrs variable. It uses the Where-Object cmdlet to filter the counter paths and the ForEach-Object cmdlet to get only the value of the **Path** property of each selected path object.
PS C:\> $IntCtrs = $Data[0].Countersamples | Where-Object {$_.Path -like "*Interrupts/sec"} | ForEach-Object {$_.Path}

The fourth command displays the selected counter paths in the $IntCtrs variable.
PS C:\> $IntCtrs

\\SERVER01\Processor(_Total)\Interrupts/sec
\\SERVER01\Processor(1)\Interrupts/sec
\\SERVER01\Processor(0)\Interrupts/sec

The fifth command uses the **Import-Counter** cmdlet to import the data. It uses the $IntCtrs variable as the value of the *Counter* parameter to import only data for the counter paths in $IntCtrs.
PS C:\> $I = Import-Counter -Path .\ProcessorData.blg -Counter $intCtrs

The sixth command uses the Export-Counter cmdlet to export the data to the Interrupts.csv file.
PS C:\> $I | Export-Counter -Path .\Interrupts.csv -Format CSV
```

<span data-ttu-id="1aeff-123">In dit voor beeld ziet u hoe u gegevens selecteert uit een logboek bestand voor prestatie meter items (. blg) en hoe u de geselecteerde gegevens vervolgens exporteert naar een CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="1aeff-123">This example shows how to select data from a performance counter log file (.blg) and then export the selected data to a .csv file.</span></span>
<span data-ttu-id="1aeff-124">Met de eerste vier opdrachten worden de item paden opgehaald uit het bestand en opgeslagen in de variabele met de naam $Data.</span><span class="sxs-lookup"><span data-stu-id="1aeff-124">The first four commands get the counter paths from the file and save them in the variable named $Data.</span></span>
<span data-ttu-id="1aeff-125">De laatste twee opdrachten importeren geselecteerde gegevens en exporteren alleen de geselecteerde gegevens.</span><span class="sxs-lookup"><span data-stu-id="1aeff-125">The last two commands import selected data and then export only the selected data.</span></span>

### <span data-ttu-id="1aeff-126">Voor beeld 4: alle item paden weer geven in een groep met geïmporteerde item sets</span><span class="sxs-lookup"><span data-stu-id="1aeff-126">Example 4: Display all counter paths in a group of imported counter sets</span></span>

```
The first command uses the *ListSet* parameter of the **Import-Counter** cmdlet to get all of the counter sets that are represented in a counter data file.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet *

CounterSetName     : Processor
MachineName        : \\SERVER01
CounterSetType     : MultiInstance
Description        :
Paths              : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}
PathsWithInstances : {\\SERVER01\Processor(_Total)\DPC Rate, \\SERVER01\Processor(1)\DPC Rate, \\SERVER01
\Processor(0)\DPC Rate, \\SERVER01\Processor(_Total)\% Idle Time...}
Counter            : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}

The second command gets all of the counter paths from the list set.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet * | ForEach-Object {$_.Paths}

\\SERVER01\Processor(*)\DPC Rate
\\SERVER01\Processor(*)\% Idle Time
\\SERVER01\Processor(*)\% C3 Time
\\SERVER01\Processor(*)\% Interrupt Time
\\SERVER01\Processor(*)\% C2 Time
\\SERVER01\Processor(*)\% User Time
\\SERVER01\Processor(*)\% C1 Time
\\SERVER01\Processor(*)\% Processor Time
\\SERVER01\Processor(*)\C1 Transitions/sec
\\SERVER01\Processor(*)\% DPC Time
\\SERVER01\Processor(*)\C2 Transitions/sec
\\SERVER01\Processor(*)\% Privileged Time
\\SERVER01\Processor(*)\C3 Transitions/sec
\\SERVER01\Processor(*)\DPCs Queued/sec
\\SERVER01\Processor(*)\Interrupts/sec
```

<span data-ttu-id="1aeff-127">In dit voor beeld ziet u hoe alle item paden worden weer gegeven in een groep met geïmporteerde item sets.</span><span class="sxs-lookup"><span data-stu-id="1aeff-127">This example shows how to display all the counter paths in a group of imported counter sets.</span></span>

### <span data-ttu-id="1aeff-128">Voor beeld 5: item gegevens importeren uit een bereik van tijds tempels</span><span class="sxs-lookup"><span data-stu-id="1aeff-128">Example 5: Import counter data from a range of time stamps</span></span>

```
The first command lists in a table the time stamps of all of the data in the ProcessorData.blg file.
PS C:\> Import-Counter -Path ".\disk.blg" | Format-Table -Property Timestamp

The second command saves particular time stamps in the $Start and $End variables. The strings are cast to **DateTime** objects.
PS C:\> $Start = [datetime]"7/9/2008 3:47:00 PM"; $End = [datetime]"7/9/2008 3:47:59 PM"

The third command uses the **Import-Counter** cmdlet to get only counter data that has a time stamp between the start and end times (inclusive). The command uses the *StartTime* and *EndTime* parameters of **Import-Counter** to specify the range.
PS C:\> Import-Counter -Path Disk.blg -StartTime $start -EndTime $end
```

<span data-ttu-id="1aeff-129">In dit voor beeld worden alleen de prestatie meter items geïmporteerd die een tijds tempel hebben tussen het begin van een eindigend bereik dat is opgegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1aeff-129">This example imports only the counter data that has a time stamp between the starting an ending ranges specified in the command.</span></span>

### <span data-ttu-id="1aeff-130">Voor beeld 6: een opgegeven aantal oudste voor beelden importeren uit een logboek bestand voor prestatie meter items</span><span class="sxs-lookup"><span data-stu-id="1aeff-130">Example 6: Import a specified number of the oldest samples from a performance counter log file</span></span>

```
The first command uses the **Import-Counter** cmdlet to import the first (oldest) five samples from the Disk.blg file. The command uses the *MaxSamples* parameter to limit the import to five counter samples.
PS C:\> Import-Counter -Path "Disk.blg" -MaxSamples 5

The second command uses array notation and the Windows PowerShell range operator (..) to get the last five counter samples from the file. These are the five newest samples.
PS C:\> (Import-Counter -Path Disk.blg)[-1 .. -5]
```

<span data-ttu-id="1aeff-131">In dit voor beeld ziet u hoe u de vijf oudste en vijf meest recente steek proeven importeert uit een logboek bestand voor prestatie meter items.</span><span class="sxs-lookup"><span data-stu-id="1aeff-131">This example shows how to import the five oldest and five newest samples from a performance counter log file.</span></span>

### <span data-ttu-id="1aeff-132">Voor beeld 7: een samen vatting van item gegevens uit een bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="1aeff-132">Example 7: Get a summary of counter data from a file</span></span>

```
PS C:\> Import-Counter "D:\Samples\Memory.blg" -Summary

OldestRecord            NewestRecord            SampleCount
------------            ------------            -----------
7/10/2008 2:59:18 PM    7/10/2008 3:00:27 PM    1000
```

<span data-ttu-id="1aeff-133">Met deze opdracht wordt de *samenvattings* parameter van de cmdlet **import-Counter** gebruikt om een samen vatting van de item gegevens in het bestand Memory. blg weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1aeff-133">This command uses the *Summary* parameter of the **Import-Counter** cmdlet to get a summary of the counter data in the Memory.blg file.</span></span>

### <span data-ttu-id="1aeff-134">Voor beeld 8: een logboek bestand voor prestatie meter items bijwerken</span><span class="sxs-lookup"><span data-stu-id="1aeff-134">Example 8: Update a performance counter log file</span></span>

```
The first command uses the *ListSet* parameter of **Import-Counter** to get the counters in OldData.blg, an existing counter log file. The command uses a pipeline operator (|) to send the data to a ForEach-Object command that gets only the values of the **PathsWithInstances** property of each object
PS C:\> $Counters = Import-Counter OldData.blg -ListSet * | ForEach-Object {$_.PathsWithInstances}

The second command gets updated data for the counters in the $Counters variable. It uses the Get-Counter cmdlet to get a current sample, and then export the results to the NewData.blg file.
PS C:\> Get-Counter -Counter $Counters -MaxSamples 20 | Export-Counter C:\Logs\NewData.blg
```

<span data-ttu-id="1aeff-135">In dit voor beeld wordt een logboek bestand voor prestatie meter items bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="1aeff-135">This example updates a performance counter log file.</span></span>

### <span data-ttu-id="1aeff-136">Voor beeld 9: prestatie logboek gegevens importeren uit meerdere bestanden en deze vervolgens opslaan</span><span class="sxs-lookup"><span data-stu-id="1aeff-136">Example 9: Import performance log data from multiple files and then save it</span></span>

```
PS C:\> $Counters = "D:\test\pdata.blg", "D:\samples\netlog.blg" | Import-Counter
```

<span data-ttu-id="1aeff-137">Met deze opdracht worden prestatie logboek gegevens uit twee logboeken geïmporteerd en worden de gegevens opgeslagen in de variabele $Counters.</span><span class="sxs-lookup"><span data-stu-id="1aeff-137">This command imports performance log data from two logs and saves the data in the $Counters variable.</span></span>
<span data-ttu-id="1aeff-138">De opdracht maakt gebruik van een pijplijn operator voor het verzenden van de prestatie logboek paden naar import teller, waarmee de gegevens uit de opgegeven paden worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="1aeff-138">The command uses a pipeline operator to send the performance log paths to Import-Counter, which imports the data from the specified paths.</span></span>

<span data-ttu-id="1aeff-139">U ziet dat elk pad tussen aanhalings tekens staat en dat de paden van elkaar worden gescheiden door een komma.</span><span class="sxs-lookup"><span data-stu-id="1aeff-139">Notice that each path is enclosed in quotation marks and that the paths are separated from each other by a comma.</span></span>

## <span data-ttu-id="1aeff-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1aeff-140">PARAMETERS</span></span>

### <span data-ttu-id="1aeff-141">-Teller</span><span class="sxs-lookup"><span data-stu-id="1aeff-141">-Counter</span></span>

<span data-ttu-id="1aeff-142">Hiermee geeft u als een teken reeks matrix de prestatie meter items op.</span><span class="sxs-lookup"><span data-stu-id="1aeff-142">Specifies, as a string array, the performance counters.</span></span>
<span data-ttu-id="1aeff-143">**Import-Counter** importeert standaard alle gegevens uit alle items in de invoer bestanden.</span><span class="sxs-lookup"><span data-stu-id="1aeff-143">By default, **Import-Counter** imports all data from all counters in the input files.</span></span>
<span data-ttu-id="1aeff-144">Voer een of meer teller paden in.</span><span class="sxs-lookup"><span data-stu-id="1aeff-144">Enter one or more counter paths.</span></span>
<span data-ttu-id="1aeff-145">Joker tekens zijn toegestaan in het gedeelte exemplaar van het pad.</span><span class="sxs-lookup"><span data-stu-id="1aeff-145">Wildcards are permitted in the Instance part of the path.</span></span>

<span data-ttu-id="1aeff-146">Elk itempad heeft de volgende indeling.</span><span class="sxs-lookup"><span data-stu-id="1aeff-146">Each counter path has the following format.</span></span>
<span data-ttu-id="1aeff-147">De waarde ComputerName is vereist in het pad.</span><span class="sxs-lookup"><span data-stu-id="1aeff-147">The ComputerName value is required in the path.</span></span>
<span data-ttu-id="1aeff-148">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1aeff-148">For instance:</span></span>

- `\\<ComputerName>\<CounterSet>(<Instance>)\<CounterName>`

<span data-ttu-id="1aeff-149">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1aeff-149">For example:</span></span>

- `\\Server01\Processor(2)\% User Time`
- `\\Server01\Processor(*)\% Processor Time`

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: All counter
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1aeff-150">-EndTime</span><span class="sxs-lookup"><span data-stu-id="1aeff-150">-EndTime</span></span>

<span data-ttu-id="1aeff-151">Hiermee geeft u een eind datum en-tijd op die met deze cmdlet item gegevens worden geïmporteerd tussen de *StartTime* en de tijds tempel van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="1aeff-151">Specifies an end date and time that this cmdlet imports counter data between the *StartTime* and this parameter timestamps.</span></span>
<span data-ttu-id="1aeff-152">Voer een **DateTime** -object in, zoals een dat is gemaakt door de cmdlet Get-Date.</span><span class="sxs-lookup"><span data-stu-id="1aeff-152">Enter a **DateTime** object, such as one created by the Get-Date cmdlet.</span></span>
<span data-ttu-id="1aeff-153">**Import-Counter** importeert standaard alle item gegevens in de bestanden die zijn opgegeven met de para meter *Path* .</span><span class="sxs-lookup"><span data-stu-id="1aeff-153">By default, **Import-Counter** imports all counter data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No end time
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aeff-154">-Lijstset</span><span class="sxs-lookup"><span data-stu-id="1aeff-154">-ListSet</span></span>

<span data-ttu-id="1aeff-155">Hiermee geeft u de prestatie meter sets op die in de geëxporteerde bestanden worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1aeff-155">Specifies the performance counter sets that are represented in the exported files.</span></span>
<span data-ttu-id="1aeff-156">Met de opdrachten met deze para meter worden geen gegevens geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="1aeff-156">Commands with this parameter do not import any data.</span></span>

<span data-ttu-id="1aeff-157">Voer een of meer namen van tellers sets in.</span><span class="sxs-lookup"><span data-stu-id="1aeff-157">Enter one or more counter set names.</span></span>
<span data-ttu-id="1aeff-158">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1aeff-158">Wildcards are permitted.</span></span>
<span data-ttu-id="1aeff-159">Als u alle item sets in het bestand wilt ophalen, typt u `Import-Counter -ListSet *` .</span><span class="sxs-lookup"><span data-stu-id="1aeff-159">To get all counter sets in the file, type `Import-Counter -ListSet *`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1aeff-160">-MaxSamples</span><span class="sxs-lookup"><span data-stu-id="1aeff-160">-MaxSamples</span></span>

<span data-ttu-id="1aeff-161">Hiermee geeft u het maximum aantal steek proeven op voor elk item dat u wilt importeren.</span><span class="sxs-lookup"><span data-stu-id="1aeff-161">Specifies the maximum number of samples of each counter to import.</span></span>
<span data-ttu-id="1aeff-162">Standaard worden met **Get-Counter** alle gegevens geïmporteerd uit de bestanden die zijn opgegeven met de para meter *Path* .</span><span class="sxs-lookup"><span data-stu-id="1aeff-162">By default, **Get-Counter** imports all of the data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No maximum
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aeff-163">-Path</span><span class="sxs-lookup"><span data-stu-id="1aeff-163">-Path</span></span>

<span data-ttu-id="1aeff-164">Hiermee geeft u de bestands paden op van de bestanden die moeten worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="1aeff-164">Specifies the file paths of the files to be imported.</span></span>
<span data-ttu-id="1aeff-165">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="1aeff-165">This parameter is required.</span></span>

<span data-ttu-id="1aeff-166">Voer het pad en de bestands naam in van een, CSV,,. TSV-of. blg-bestand dat u hebt geëxporteerd met de cmdlet **export-Counter** .</span><span class="sxs-lookup"><span data-stu-id="1aeff-166">Enter the path and file name of a, .csv,, .tsv, or .blg file that you exported by using the **Export-Counter** cmdlet.</span></span>
<span data-ttu-id="1aeff-167">U kunt slechts één CSV-of TSV-bestand opgeven, maar u kunt meerdere. blg-bestanden (Maxi maal 32) in elke opdracht opgeven.</span><span class="sxs-lookup"><span data-stu-id="1aeff-167">You can specify only one .csv or .tsv file, but you can specify multiple .blg files (up to 32) in each command.</span></span>
<span data-ttu-id="1aeff-168">U kunt ook teken reeksen van het bestandspad (tussen aanhalings tekens) naar **import teller**.</span><span class="sxs-lookup"><span data-stu-id="1aeff-168">You can also pipe file path strings (in quotation marks) to **Import-Counter**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="1aeff-169">-StartTime</span><span class="sxs-lookup"><span data-stu-id="1aeff-169">-StartTime</span></span>

<span data-ttu-id="1aeff-170">Hiermee geeft u de begin datum en-tijd op waarop deze cmdlet item gegevens ophaalt.</span><span class="sxs-lookup"><span data-stu-id="1aeff-170">Specifies the start date and time in which this cmdlet gets counter data.</span></span>
<span data-ttu-id="1aeff-171">Voer een **DateTime** -object in, zoals een, gemaakt door de cmdlet **Get-date** .</span><span class="sxs-lookup"><span data-stu-id="1aeff-171">Enter a **DateTime** object, such as one created by the **Get-Date** cmdlet.</span></span>
<span data-ttu-id="1aeff-172">**Import-Counter** importeert standaard alle item gegevens in de bestanden die zijn opgegeven met de para meter *Path* .</span><span class="sxs-lookup"><span data-stu-id="1aeff-172">By default, **Import-Counter** imports all counter data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No start time
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aeff-173">-Samen vatting</span><span class="sxs-lookup"><span data-stu-id="1aeff-173">-Summary</span></span>

<span data-ttu-id="1aeff-174">Hiermee wordt aangegeven dat met deze cmdlet een samen vatting van de geïmporteerde gegevens wordt opgehaald, in plaats van afzonderlijke meter gegevens voor beelden te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="1aeff-174">Indicates that this cmdlet gets a summary of the imported data, instead of getting individual counter data samples.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SummarySet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aeff-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1aeff-175">CommonParameters</span></span>

<span data-ttu-id="1aeff-176">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1aeff-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1aeff-177">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1aeff-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1aeff-178">INVOER</span><span class="sxs-lookup"><span data-stu-id="1aeff-178">INPUTS</span></span>

### <span data-ttu-id="1aeff-179">System. String</span><span class="sxs-lookup"><span data-stu-id="1aeff-179">System.String</span></span>

<span data-ttu-id="1aeff-180">U kunt de logboek paden voor prestatie meter items door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1aeff-180">You can pipe performance counter log paths to this cmdlet.</span></span>

## <span data-ttu-id="1aeff-181">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1aeff-181">OUTPUTS</span></span>

### <span data-ttu-id="1aeff-182">Micro soft. Power shell. commands. GetCounter. PerformanceCounterSampleSet, micro soft. Power shell. commands. GetCounter. Counterset, micro soft. Power shell. commands. GetCounter. CounterFileInfo</span><span class="sxs-lookup"><span data-stu-id="1aeff-182">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet, Microsoft.PowerShell.Commands.GetCounter.CounterSet, Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo</span></span>

<span data-ttu-id="1aeff-183">Met deze cmdlet wordt een **Microsoft. Power shell. commands. GetCounter. PerformanceCounterSampleSet** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1aeff-183">This cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet**.</span></span>
<span data-ttu-id="1aeff-184">Als u de *listset* -para meter gebruikt, retourneert deze cmdlet een **micro soft. Power shell. commands. GetCounter. counterset** -object.</span><span class="sxs-lookup"><span data-stu-id="1aeff-184">If you use the *ListSet* parameter, this cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.CounterSet** object.</span></span>
<span data-ttu-id="1aeff-185">Als u de para meter *Summary* gebruikt, retourneert deze cmdlet een object **micro soft. Power shell. commands. GetCounter. CounterFileInfo** .</span><span class="sxs-lookup"><span data-stu-id="1aeff-185">If you use the *Summary* parameter, this cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo** object.</span></span>

## <span data-ttu-id="1aeff-186">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1aeff-186">NOTES</span></span>

* <span data-ttu-id="1aeff-187">Deze cmdlet heeft geen *ComputerName* -para meter.</span><span class="sxs-lookup"><span data-stu-id="1aeff-187">This cmdlet does not have a *ComputerName* parameter.</span></span> <span data-ttu-id="1aeff-188">Als de computer echter is geconfigureerd voor externe communicatie met Windows Power shell, kunt u de cmdlet Invoke-Command gebruiken om een opdracht voor het **importeren van items** uit te voeren op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="1aeff-188">However, if the computer is configured for Windows PowerShell remoting, you can use the Invoke-Command cmdlet to run an **Import-Counter** command on a remote computer.</span></span>

## <span data-ttu-id="1aeff-189">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1aeff-189">RELATED LINKS</span></span>

[<span data-ttu-id="1aeff-190">Exporteren-teller</span><span class="sxs-lookup"><span data-stu-id="1aeff-190">Export-Counter</span></span>](Export-Counter.md)

[<span data-ttu-id="1aeff-191">Get-teller</span><span class="sxs-lookup"><span data-stu-id="1aeff-191">Get-Counter</span></span>](Get-Counter.md)
