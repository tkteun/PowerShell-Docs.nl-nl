---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 10/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/export-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Counter
ms.openlocfilehash: 54498eb504a1d13a5b96a2583b5e5d6e4c08735e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252123"
---
# <span data-ttu-id="0012c-103">Export-Counter</span><span class="sxs-lookup"><span data-stu-id="0012c-103">Export-Counter</span></span>

## <span data-ttu-id="0012c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0012c-104">SYNOPSIS</span></span>
<span data-ttu-id="0012c-105">Exporteert gegevens van prestatie meter items naar logboek bestanden.</span><span class="sxs-lookup"><span data-stu-id="0012c-105">Exports performance counter data to log files.</span></span>

## <span data-ttu-id="0012c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0012c-106">SYNTAX</span></span>

```
Export-Counter [-Path] <String> [-FileFormat <String>] [-MaxSize <UInt32>]
 -InputObject <PerformanceCounterSampleSet[]> [-Force] [-Circular] [<CommonParameters>]
```

## <span data-ttu-id="0012c-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0012c-107">DESCRIPTION</span></span>

<span data-ttu-id="0012c-108">De `Export-Counter` cmdlet exporteert gegevens over prestatie meter items (PerformanceCounterSampleSet-objecten) naar logboek bestanden in een binair prestatie logboek (. blg), door komma's gescheiden waarden (. CSV) of door tabs gescheiden waarden (. tsv).</span><span class="sxs-lookup"><span data-stu-id="0012c-108">The `Export-Counter` cmdlet exports performance counter data (PerformanceCounterSampleSet objects) to log files in binary performance log (.blg), comma-separated value (.csv), or tab-separated value (.tsv) format.</span></span> <span data-ttu-id="0012c-109">Met deze cmdlet kunt u gegevens van prestatie meter items registreren.</span><span class="sxs-lookup"><span data-stu-id="0012c-109">You use this cmdlet to log performance counter data.</span></span>

<span data-ttu-id="0012c-110">De `Export-Counter` cmdlet is ontworpen voor het exporteren van gegevens die worden geretourneerd door de- `Get-Counter` en- `Import-Counter` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0012c-110">The `Export-Counter` cmdlet is designed to export data that is returned by the `Get-Counter` and `Import-Counter` cmdlets.</span></span>

<span data-ttu-id="0012c-111">Deze cmdlet kan alleen worden uitgevoerd op Windows 7, Windows Server 2008 R2 en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="0012c-111">This cmdlet runs only on Windows 7, Windows Server 2008 R2, and later versions of Windows.</span></span>

## <span data-ttu-id="0012c-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0012c-112">EXAMPLES</span></span>

### <span data-ttu-id="0012c-113">VOOR beeld 1: item gegevens exporteren naar een bestand</span><span class="sxs-lookup"><span data-stu-id="0012c-113">EXAMPLE 1: Export counter data to a file</span></span>

<span data-ttu-id="0012c-114">In dit voor beeld worden item gegevens geëxporteerd naar een BLG-bestand.</span><span class="sxs-lookup"><span data-stu-id="0012c-114">This example exports counter data to a BLG file.</span></span>

```powershell
Get-Counter "\Processor(*)\% Processor Time" | Export-Counter -Path $home\Counters.blg
```

<span data-ttu-id="0012c-115">De opdracht gebruikt de `Get-Counter` cmdlet voor het verzamelen van processor tijd gegevens.</span><span class="sxs-lookup"><span data-stu-id="0012c-115">The command uses the `Get-Counter` cmdlet to collect processor time data.</span></span> <span data-ttu-id="0012c-116">Er wordt gebruikgemaakt van een pijplijn operator (|) voor het verzenden van de gegevens naar de `Export-Counter` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0012c-116">It uses a pipeline operator (|) to send the data to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="0012c-117">De `Export-Counter` opdracht gebruikt de **padvariabele** om het uitvoer bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="0012c-117">The `Export-Counter` command uses the **Path** variable to specify the output file.</span></span>

<span data-ttu-id="0012c-118">Omdat de gegevensset mogelijk erg groot is, verzendt dit voor beeld de gegevens naar `Export-Counter` via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="0012c-118">Because the data set might be very large, this example sends the data to `Export-Counter` through the pipeline.</span></span> <span data-ttu-id="0012c-119">Als de gegevens zijn opgeslagen in een variabele, kunt u een onevenredige hoeveelheid geheugen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0012c-119">If the data were saved in a variable, you might use a disproportionate amount of memory.</span></span>

### <span data-ttu-id="0012c-120">Voor beeld 2: een bestand naar een bestands indeling voor een teller exporteren</span><span class="sxs-lookup"><span data-stu-id="0012c-120">Example 2: Export a file to a counter file format</span></span>

<span data-ttu-id="0012c-121">In dit voor beeld wordt een CSV-bestand geconverteerd naar een teller data BLG-indeling.</span><span class="sxs-lookup"><span data-stu-id="0012c-121">This example converts a CSV file to a counter data BLG format.</span></span>

<span data-ttu-id="0012c-122">`Import-Counter`Met de cmdlet worden prestatie meter gegevens uit het `Threads.csv` bestand geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="0012c-122">The `Import-Counter` cmdlet imports performance counter data from the `Threads.csv` file.</span></span> <span data-ttu-id="0012c-123">In het voor beeld wordt ervan uitgegaan dat dit bestand eerder is geëxporteerd met behulp van de- `Export-Counter` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0012c-123">The example presumes that this file was previously exported by using the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="0012c-124">Een pijplijn operator ( `|` ) verzendt de geïmporteerde gegevens naar de `Export-Counter` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0012c-124">A pipeline operator (`|`) sends the imported data to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="0012c-125">De opdracht gebruikt de para meter **Path** om de locatie van het uitvoer bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="0012c-125">The command uses the **Path** parameter to specify the location of the output file.</span></span> <span data-ttu-id="0012c-126">De para meters **circulair** en **MaxSize** worden gebruikt om de `Export-Counter` cmdlet te sturen om een circulair logboek te maken dat op 1 GB loopt.</span><span class="sxs-lookup"><span data-stu-id="0012c-126">It uses the **Circular** and **MaxSize** parameters to direct the `Export-Counter` cmdlet to create a circular log that wraps at 1 GB.</span></span> <span data-ttu-id="0012c-127">De **MaxSize** para meter wordt uitgedrukt in mega bytes.</span><span class="sxs-lookup"><span data-stu-id="0012c-127">The **MaxSize** parameter is expressed in megabytes.</span></span>

```powershell
$1GBInMB = 1024 # 1GB = 1024MB
Import-Counter Threads.csv | Export-Counter -Path ThreadTest.blg -Circular -MaxSize $1GBInMB
```

### <span data-ttu-id="0012c-128">Voor beeld 3: item gegevens ophalen van een externe computer en de gegevens opslaan in een bestand</span><span class="sxs-lookup"><span data-stu-id="0012c-128">Example 3: Get counter data from a remote computer and save the data to a file</span></span>

<span data-ttu-id="0012c-129">In dit voor beeld ziet u hoe gegevens van een prestatie meter item worden opgehaald van een externe computer en dat de gegevens worden opgeslagen in een bestand op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="0012c-129">This example shows how to get performance counter data from a remote computer and save the data in a file on the remote computer.</span></span>

<span data-ttu-id="0012c-130">Met de eerste opdracht wordt de `Get-Counter` cmdlet gebruikt voor het verzamelen van gegevens over de werkset van Server01, een externe computer.</span><span class="sxs-lookup"><span data-stu-id="0012c-130">The first command uses the `Get-Counter` cmdlet to collect working set counter data from Server01, a remote computer.</span></span> <span data-ttu-id="0012c-131">Met de opdracht worden de gegevens in de `$C` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="0012c-131">The command saves the data in the `$C` variable.</span></span>

<span data-ttu-id="0012c-132">De tweede opdracht maakt gebruik van een pijplijn operator ( `|` ) om de gegevens `$C` te verzenden naar de `Export-Counter` cmdlet. deze wordt opgeslagen in het `Workingset.blg` bestand in het gedeelte prestaties van de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="0012c-132">The second command uses a pipeline operator (`|`) to send the data in `$C` to the `Export-Counter` cmdlet, which saves it in the `Workingset.blg` file in the Perf share of the Server01 computer.</span></span>

```powershell
$C = Get-Counter -ComputerName Server01 -Counter "\Process(*)\Working Set - Private" -MaxSamples $C | Export-Counter -Path \\Server01\Perf\WorkingSet.blg
```

```Output
20
```

### <span data-ttu-id="0012c-133">Voor beeld 4: bestaande gegevens opnieuw registreren</span><span class="sxs-lookup"><span data-stu-id="0012c-133">Example 4: Re-log existing data</span></span>

<span data-ttu-id="0012c-134">In dit voor beeld ziet u hoe u de- `Import-Counter` en `Export-Counter` -cmdlets kunt gebruiken om bestaande gegevens opnieuw te registreren.</span><span class="sxs-lookup"><span data-stu-id="0012c-134">This example shows how to use the `Import-Counter` and `Export-Counter` cmdlets to re-log existing data.</span></span>

<span data-ttu-id="0012c-135">Met de eerste opdracht wordt de `Import-Counter` cmdlet gebruikt voor het importeren van gegevens uit het prestatie meter item uit het logboek DiskSpace. blg.</span><span class="sxs-lookup"><span data-stu-id="0012c-135">The first command uses the `Import-Counter` cmdlet to import performance counter data from the DiskSpace.blg log.</span></span> <span data-ttu-id="0012c-136">De gegevens worden opgeslagen in de `$All` variabele.</span><span class="sxs-lookup"><span data-stu-id="0012c-136">It saves the data in the `$All` variable.</span></span> <span data-ttu-id="0012c-137">Dit bestand bevat voor beelden van het \% meter item ' beschik bare ruimte op de logische schijf ' op meer dan 200 externe computers in de onderneming.</span><span class="sxs-lookup"><span data-stu-id="0012c-137">This file contains samples of the "LogicalDisk\% Free Space" counter on more than 200 remote computers in the enterprise.</span></span>

<span data-ttu-id="0012c-138">De tweede opdracht gebruikt de `Where-Object` cmdlet om objecten te selecteren met **CookedValue** van minder dan 15 (procent).</span><span class="sxs-lookup"><span data-stu-id="0012c-138">The second command uses the `Where-Object` cmdlet to select objects with **CookedValue** of less than 15 (percent).</span></span> <span data-ttu-id="0012c-139">Met de opdracht worden de resultaten opgeslagen in de `$LowSpace` variabele.</span><span class="sxs-lookup"><span data-stu-id="0012c-139">The command saves the results in the `$LowSpace` variable.</span></span>

<span data-ttu-id="0012c-140">De derde opdracht maakt gebruik van een pijplijn operator ( `|` ) voor het verzenden van de gegevens in de `$LowSpace` variabele naar de `Export-Counter` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0012c-140">The third command uses a pipeline operator (`|`) to send the data in the `$LowSpace` variable to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="0012c-141">De opdracht gebruikt de para meter **Path** om aan te geven dat de geselecteerde gegevens moeten worden geregistreerd in het bestand LowDiskSpace. blg.</span><span class="sxs-lookup"><span data-stu-id="0012c-141">The command uses the **Path** parameter to indicate that the selected data should be logged in the LowDiskSpace.blg file.</span></span>

```powershell
$All = Import-Counter DiskSpace.blg
$LowSpace = $All | Where-Object {$_.CounterSamples.CookedValue -lt 15}
$LowSpace | Export-Counter -Path LowDiskSpace.blg
```

## <span data-ttu-id="0012c-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0012c-142">PARAMETERS</span></span>

### <span data-ttu-id="0012c-143">-Circulair</span><span class="sxs-lookup"><span data-stu-id="0012c-143">-Circular</span></span>

<span data-ttu-id="0012c-144">Geeft aan dat het uitvoer bestand een circulaire logboek met FIFO-indeling (First in, first out) is.</span><span class="sxs-lookup"><span data-stu-id="0012c-144">Indicates that the output file is a circular log with first in, first out (FIFO) format.</span></span>
<span data-ttu-id="0012c-145">Wanneer u deze para meter opneemt, is de para meter **MaxSize** vereist.</span><span class="sxs-lookup"><span data-stu-id="0012c-145">When you include this parameter, the **MaxSize** parameter is required.</span></span>

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

### <span data-ttu-id="0012c-146">-File Format</span><span class="sxs-lookup"><span data-stu-id="0012c-146">-FileFormat</span></span>

<span data-ttu-id="0012c-147">Hiermee geeft u de uitvoer indeling van het uitvoer logboek bestand.</span><span class="sxs-lookup"><span data-stu-id="0012c-147">Specifies the output format of the output log file.</span></span>

<span data-ttu-id="0012c-148">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="0012c-148">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0012c-149">CSV</span><span class="sxs-lookup"><span data-stu-id="0012c-149">CSV</span></span>
- <span data-ttu-id="0012c-150">TSV</span><span class="sxs-lookup"><span data-stu-id="0012c-150">TSV</span></span>
- <span data-ttu-id="0012c-151">BLG</span><span class="sxs-lookup"><span data-stu-id="0012c-151">BLG</span></span>

<span data-ttu-id="0012c-152">De standaard waarde is BLG.</span><span class="sxs-lookup"><span data-stu-id="0012c-152">The default value is BLG.</span></span>

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

### <span data-ttu-id="0012c-153">-Force</span><span class="sxs-lookup"><span data-stu-id="0012c-153">-Force</span></span>

<span data-ttu-id="0012c-154">Overschrijft en vervangt een bestaand bestand als er een bestaat op de locatie die is opgegeven door de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="0012c-154">Overwrites and replaces an existing file if one exists in the location specified by the **Path** parameter.</span></span>

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

### <span data-ttu-id="0012c-155">-Input object</span><span class="sxs-lookup"><span data-stu-id="0012c-155">-InputObject</span></span>

<span data-ttu-id="0012c-156">Geeft als een matrix de item gegevens aan die moeten worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="0012c-156">Specifies, as an array, the counter data to export.</span></span> <span data-ttu-id="0012c-157">Voer een variabele in die de gegevens bevat of een opdracht die de gegevens ophaalt, zoals de `Get-Counter` of- `Import-Counter` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0012c-157">Enter a variable that contains the data or a command that gets the data, such as the `Get-Counter` or `Import-Counter` cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0012c-158">-MaxSize</span><span class="sxs-lookup"><span data-stu-id="0012c-158">-MaxSize</span></span>

<span data-ttu-id="0012c-159">Hiermee geeft u de maximale grootte van het uitvoer bestand in mega bytes (MB).</span><span class="sxs-lookup"><span data-stu-id="0012c-159">Specifies the maximum size of the output file in megabytes (MB).</span></span>

<span data-ttu-id="0012c-160">Als de **circulaire** para meter is opgegeven, wordt de oudste vermeldingen verwijderd wanneer het logboek bestand de opgegeven maximum grootte heeft bereikt.</span><span class="sxs-lookup"><span data-stu-id="0012c-160">If the **Circular** parameter is specified, then when the log file reaches the specified maximum size, the oldest entries are deleted as newer ones are added.</span></span> <span data-ttu-id="0012c-161">Als de **kring** veld niet is opgegeven, wordt er geen nieuwe gegevens toegevoegd en wordt er een niet-afsluit fout gegenereerd wanneer het logboek bestand de opgegeven maximum grootte heeft bereikt.</span><span class="sxs-lookup"><span data-stu-id="0012c-161">If the **Circular** parameter is not specified, then when the log file reaches the specified maximum size, no new data is added and the cmdlet generates a non-terminating error.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0012c-162">-Path</span><span class="sxs-lookup"><span data-stu-id="0012c-162">-Path</span></span>

<span data-ttu-id="0012c-163">Hiermee geeft u het pad en de bestands naam van het uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="0012c-163">Specifies the path and file name of the output file.</span></span> <span data-ttu-id="0012c-164">Voer een relatief of absoluut pad op de lokale computer of een UNC-pad (Uniform Naming Convention) naar een externe computer, zoals `\\Computer\Share\file.blg` .</span><span class="sxs-lookup"><span data-stu-id="0012c-164">Enter a relative or absolute path on the local computer, or a Uniform Naming Convention (UNC) path to a remote computer, such as `\\Computer\Share\file.blg`.</span></span> <span data-ttu-id="0012c-165">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="0012c-165">This parameter is required.</span></span>

<span data-ttu-id="0012c-166">De bestands indeling wordt bepaald door de waarde van de para meter **File Format** , niet door de bestandsnaam extensie in het pad.</span><span class="sxs-lookup"><span data-stu-id="0012c-166">The file format is determined by the value of the **FileFormat** parameter, not by the file name extension in the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0012c-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0012c-167">CommonParameters</span></span>

<span data-ttu-id="0012c-168">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0012c-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0012c-169">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0012c-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0012c-170">INVOER</span><span class="sxs-lookup"><span data-stu-id="0012c-170">INPUTS</span></span>

### <span data-ttu-id="0012c-171">Micro soft. Power shell. commands. GetCounter. PerformanceCounterSampleSet</span><span class="sxs-lookup"><span data-stu-id="0012c-171">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet</span></span>

<span data-ttu-id="0012c-172">U kunt prestatie meter gegevens van `Get-Counter` of `Import-Counter` naar deze cmdlet sluizen.</span><span class="sxs-lookup"><span data-stu-id="0012c-172">You can pipe performance counter data from `Get-Counter` or `Import-Counter` to this cmdlet.</span></span>

## <span data-ttu-id="0012c-173">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0012c-173">OUTPUTS</span></span>

### <span data-ttu-id="0012c-174">Geen</span><span class="sxs-lookup"><span data-stu-id="0012c-174">None</span></span>

## <span data-ttu-id="0012c-175">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0012c-175">NOTES</span></span>

<span data-ttu-id="0012c-176">De generator van het logboek bestand verwacht dat alle invoer objecten hetzelfde itempad hebben en dat de objecten in oplopende volg orde zijn gerangschikt.</span><span class="sxs-lookup"><span data-stu-id="0012c-176">The log file generator expects that all input objects have the same counter path and that the objects are arranged in ascending time order.</span></span>

<span data-ttu-id="0012c-177">Het item type en pad van het eerste invoer object bepalen welke eigenschappen in het logboek bestand worden vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="0012c-177">The counter type and path of the first input object determines the properties recorded in the log file.</span></span> <span data-ttu-id="0012c-178">Als andere invoer objecten geen waarde voor een vastgelegde eigenschap hebben, is het veld van de eigenschap leeg.</span><span class="sxs-lookup"><span data-stu-id="0012c-178">If other input objects do not have a value for a recorded property, the property field is empty.</span></span> <span data-ttu-id="0012c-179">Als de objecten eigenschaps waarden hebben die niet zijn vastgelegd, worden de extra eigenschaps waarden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="0012c-179">If the objects have property values that were not recorded, the extra property values are ignored.</span></span>

<span data-ttu-id="0012c-180">De prestatie meter kan mogelijk niet alle logboeken lezen die worden `Export-Counter` gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="0012c-180">Performance Monitor might not be able to read all logs that `Export-Counter` generates.</span></span> <span data-ttu-id="0012c-181">Prestatie meter vereist bijvoorbeeld dat alle objecten hetzelfde pad hebben en dat alle objecten worden gescheiden door hetzelfde tijds interval.</span><span class="sxs-lookup"><span data-stu-id="0012c-181">For instance, Performance Monitor requires that all objects have the same path and that all objects are separated by the same time interval.</span></span>

<span data-ttu-id="0012c-182">De `Import-Counter` cmdlet heeft geen **ComputerName** -para meter.</span><span class="sxs-lookup"><span data-stu-id="0012c-182">The `Import-Counter` cmdlet does not have a **ComputerName** parameter.</span></span> <span data-ttu-id="0012c-183">Als de computer echter is geconfigureerd voor externe Windows Power shell Windows Power shell, kunt u de `Invoke-Command` cmdlet gebruiken om een opdracht uit te voeren `Import-Counter` op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="0012c-183">However, if the computer is configured for remote Windows PowerShell Windows PowerShell, you can use the `Invoke-Command` cmdlet to run an `Import-Counter` command on a remote computer.</span></span>

## <span data-ttu-id="0012c-184">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0012c-184">RELATED LINKS</span></span>

[<span data-ttu-id="0012c-185">Get-teller</span><span class="sxs-lookup"><span data-stu-id="0012c-185">Get-Counter</span></span>](Get-Counter.md)

[<span data-ttu-id="0012c-186">Import teller</span><span class="sxs-lookup"><span data-stu-id="0012c-186">Import-Counter</span></span>](Import-Counter.md)
