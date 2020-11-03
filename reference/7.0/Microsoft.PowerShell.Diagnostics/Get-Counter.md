---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-counter?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Counter
ms.openlocfilehash: b7eafd52393a1e7e80a12e5bc982965b0af12fd5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249751"
---
# <span data-ttu-id="36a72-103">Get-Counter</span><span class="sxs-lookup"><span data-stu-id="36a72-103">Get-Counter</span></span>

## <span data-ttu-id="36a72-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="36a72-104">SYNOPSIS</span></span>
<span data-ttu-id="36a72-105">Hiermee worden gegevens van het prestatie meter item opgehaald van lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="36a72-105">Gets performance counter data from local and remote computers.</span></span>

## <span data-ttu-id="36a72-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="36a72-106">SYNTAX</span></span>

### <span data-ttu-id="36a72-107">GetCounterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="36a72-107">GetCounterSet (Default)</span></span>

```
Get-Counter [[-Counter] <String[]>] [-SampleInterval <Int32>] [-MaxSamples <Int64>] [-Continuous]
 [-ComputerName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="36a72-108">ListSetSet</span><span class="sxs-lookup"><span data-stu-id="36a72-108">ListSetSet</span></span>

```
Get-Counter [-ListSet] <String[]> [-ComputerName <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="36a72-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="36a72-109">DESCRIPTION</span></span>

<span data-ttu-id="36a72-110">Met de `Get-Counter` cmdlet worden gegevens van prestatie meter items rechtstreeks opgehaald uit de instrumentatie voor prestatie bewaking in de Windows-besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="36a72-110">The `Get-Counter` cmdlet gets performance counter data directly from the performance monitoring instrumentation in the Windows family of operating systems.</span></span> <span data-ttu-id="36a72-111">`Get-Counter` Hiermee worden prestatie gegevens opgehaald van een lokale computer of externe computers.</span><span class="sxs-lookup"><span data-stu-id="36a72-111">`Get-Counter` gets performance data from a local computer or remote computers.</span></span>

<span data-ttu-id="36a72-112">U kunt de `Get-Counter` para meters gebruiken voor het opgeven van een of meer computers, het weer geven van de prestatie meter sets en de instanties die ze bevatten, de controle-intervallen instellen en het maximum aantal steek proeven opgeven.</span><span class="sxs-lookup"><span data-stu-id="36a72-112">You can use the `Get-Counter` parameters to specify one or more computers, list the performance counter sets and the instances they contain, set the sample intervals, and specify the maximum number of samples.</span></span> <span data-ttu-id="36a72-113">Zonder para meters worden `Get-Counter` prestatie meter gegevens voor een set systeem tellers opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a72-113">Without parameters, `Get-Counter` gets performance counter data for a set of system counters.</span></span>

<span data-ttu-id="36a72-114">Veel item sets worden beveiligd door Access Control Lists (ACL).</span><span class="sxs-lookup"><span data-stu-id="36a72-114">Many counter sets are protected by access control lists (ACL).</span></span> <span data-ttu-id="36a72-115">Als u alle item sets wilt zien, opent u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="36a72-115">To see all counter sets, open PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="36a72-116">Deze cmdlet is opnieuw geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="36a72-116">This cmdlet was reintroduced in PowerShell 7.</span></span>

## <span data-ttu-id="36a72-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="36a72-117">EXAMPLES</span></span>

### <span data-ttu-id="36a72-118">Voor beeld 1: de lijst met item sets ophalen</span><span class="sxs-lookup"><span data-stu-id="36a72-118">Example 1: Get the counter set list</span></span>

<span data-ttu-id="36a72-119">In dit voor beeld wordt de lijst met item sets van de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a72-119">This example gets the local computer's list of counter sets.</span></span>

```powershell
Get-Counter -ListSet *
```

```Output
CounterSetName     : Processor
MachineName        : .
CounterSetType     : MultiInstance
Description        : The Processor performance object consists of counters that measure aspects ...
                     computer that performs arithmetic and logical computations, initiates ...
                     computer can have multiple processors.  The processor object represents ...
Paths              : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
PathsWithInstances : {\Processor(0)\% Processor Time, \Processor(1)\% Processor Time, ...
Counter            : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
```

<span data-ttu-id="36a72-120">`Get-Counter` maakt gebruik van de **listset** -para meter met een asterisk ( `*` ) om de lijst met item sets op te halen.</span><span class="sxs-lookup"><span data-stu-id="36a72-120">`Get-Counter` uses the **ListSet** parameter with an asterisk (`*`) to get the list of counter sets.</span></span>
<span data-ttu-id="36a72-121">De punt ( `.` ) in de kolom **MachineName** vertegenwoordigt de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="36a72-121">The dot (`.`) in the **MachineName** column represents the local computer.</span></span>

### <span data-ttu-id="36a72-122">Voor beeld 2: Geef de SampleInterval en MaxSamples op</span><span class="sxs-lookup"><span data-stu-id="36a72-122">Example 2: Specify the SampleInterval and MaxSamples</span></span>

<span data-ttu-id="36a72-123">In deze voor beelden worden de item gegevens voor alle processors op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a72-123">This examples gets the counter data for all processors on the local computer.</span></span> <span data-ttu-id="36a72-124">Gegevens worden op twee seconden verzameld, totdat er drie voor beelden zijn.</span><span class="sxs-lookup"><span data-stu-id="36a72-124">Data is collected at two-second intervals until there are three samples.</span></span>

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -SampleInterval 2 -MaxSamples 3
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/18/2019 14:39:56        \\Computer01\processor(_total)\% processor time :
                          20.7144271584086

6/18/2019 14:39:58        \\Computer01\processor(_total)\% processor time :
                          10.4391790575511

6/18/2019 14:40:01        \\Computer01\processor(_total)\% processor time :
                          37.5968799396998
```

<span data-ttu-id="36a72-125">`Get-Counter` maakt gebruik van de para meter **Counter** om het itempad op te geven `\Processor(_Total)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="36a72-125">`Get-Counter` uses the **Counter** parameter to specify the counter path `\Processor(_Total)\% Processor Time`.</span></span> <span data-ttu-id="36a72-126">De para meter **SampleInterval** stelt een interval van twee seconden in om de teller te controleren.</span><span class="sxs-lookup"><span data-stu-id="36a72-126">The **SampleInterval** parameter sets a two-second interval to check the counter.</span></span> <span data-ttu-id="36a72-127">**MaxSamples** bepaalt dat drie het maximum aantal keer dat de teller moet worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="36a72-127">**MaxSamples** determines that three is the maximum number of times to check the counter.</span></span>

### <span data-ttu-id="36a72-128">Voor beeld 3: doorlopende voor beelden van een item ophalen</span><span class="sxs-lookup"><span data-stu-id="36a72-128">Example 3: Get continuous samples of a counter</span></span>

<span data-ttu-id="36a72-129">In deze voor beelden worden voor elke seconde doorlopende voor beelden voor een item opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a72-129">This examples gets continuous samples for a counter every second.</span></span> <span data-ttu-id="36a72-130">Als u de opdracht wilt stoppen, drukt u op <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="36a72-130">To stop the command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="36a72-131">Als u een langere interval tussen steek proeven wilt opgeven, gebruikt u de para meter **SampleInterval** .</span><span class="sxs-lookup"><span data-stu-id="36a72-131">To specify a longer interval between samples, use the **SampleInterval** parameter.</span></span>

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -Continuous
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 15:35:03        \\Computer01\processor(_total)\% processor time :
                          43.8522842937022

6/19/2019 15:35:04        \\Computer01\processor(_total)\% processor time :
                          29.7896844697383

6/19/2019 15:35:05        \\Computer01\processor(_total)\% processor time :
                          29.4962645638135

6/19/2019 15:35:06        \\Computer01\processor(_total)\% processor time :
                          25.5901500127408
```

<span data-ttu-id="36a72-132">`Get-Counter` Hiermee wordt **de teller-para meter** gebruikt om de teller op te geven `\Processor\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="36a72-132">`Get-Counter` uses the **Counter** parameter to specify the `\Processor\% Processor Time` counter.</span></span>
<span data-ttu-id="36a72-133">De **doorlopende** para meter geeft aan dat voor beelden elke seconde worden ontvangen totdat de opdracht wordt gestopt met <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="36a72-133">The **Continuous** parameter specifies to get samples every second until the command is stopped with <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

### <span data-ttu-id="36a72-134">Voor beeld 4: alfabetische lijst met item sets</span><span class="sxs-lookup"><span data-stu-id="36a72-134">Example 4: Alphabetical list of counter sets</span></span>

<span data-ttu-id="36a72-135">In dit voor beeld wordt de pijp lijn gebruikt om de lijst met tellers in te stellen en de lijst vervolgens in alfabetische volg orde te sorteren.</span><span class="sxs-lookup"><span data-stu-id="36a72-135">This example uses the pipeline to get the counter list set and then sort the list in alphabetical order.</span></span>

```powershell
Get-Counter -ListSet * |
  Sort-Object -Property CounterSetName |
    Format-Table CounterSetName, CounterSetType -AutoSize
```

```Output
CounterSetName                        CounterSetType
--------------                        --------------
.NET CLR Data                         SingleInstance
.NET Data Provider for SqlServer      SingleInstance
AppV Client Streamed Data Percentage  SingleInstance
Authorization Manager Applications    SingleInstance
BitLocker                             MultiInstance
Bluetooth Device                      SingleInstance
Cache                                 SingleInstance
Client Side Caching                   SingleInstance
```

<span data-ttu-id="36a72-136">`Get-Counter` maakt gebruik van de **listset** -para meter met een asterisk ( `*` ) om een volledige lijst met item sets op te halen.</span><span class="sxs-lookup"><span data-stu-id="36a72-136">`Get-Counter` uses the **ListSet** parameter with an asterisk (`*`) to get a complete list of counter sets.</span></span> <span data-ttu-id="36a72-137">De **counterset** -objecten worden omlaag verzonden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="36a72-137">The **CounterSet** objects are sent down the pipeline.</span></span> <span data-ttu-id="36a72-138">`Sort-Object` Hiermee wordt de para meter **Property** gebruikt om op te geven dat de objecten zijn gesorteerd op **CounterSetName**.</span><span class="sxs-lookup"><span data-stu-id="36a72-138">`Sort-Object` uses the **Property** parameter to specify that the objects are sorted by **CounterSetName**.</span></span> <span data-ttu-id="36a72-139">De objecten worden naar beneden verzonden in de pijp lijn `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="36a72-139">The objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="36a72-140">Met de para meter **AutoSize** worden de kolom breedten aangepast om de afkap ping te minimaliseren.</span><span class="sxs-lookup"><span data-stu-id="36a72-140">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

<span data-ttu-id="36a72-141">De punt ( `.` ) in de kolom **MachineName** vertegenwoordigt de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="36a72-141">The dot (`.`) in the **MachineName** column represents the local computer.</span></span>

### <span data-ttu-id="36a72-142">Voor beeld 5: een achtergrond taak uitvoeren om item gegevens op te halen</span><span class="sxs-lookup"><span data-stu-id="36a72-142">Example 5: Run a background job to get counter data</span></span>

<span data-ttu-id="36a72-143">In dit voor beeld `Start-Job` wordt een `Get-Counter` opdracht uitgevoerd als achtergrond taak op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="36a72-143">In this example, `Start-Job` runs a `Get-Counter` command as a background job on the local computer.</span></span>
<span data-ttu-id="36a72-144">Als u de uitvoer van het prestatie meter item van de taak wilt weer geven, gebruikt u de `Receive-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36a72-144">To view the performance counter output from the job, use the `Receive-Job` cmdlet.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Counter -Counter "\LogicalDisk(_Total)\% Free Space" -MaxSamples 1000}
```

```Output
Id     Name  PSJobTypeName   State    HasMoreData  Location   Command
--     ----  -------------   -----    -----------  --------   -------
1      Job1  BackgroundJob   Running  True         localhost  Get-Counter -Counter
```

<span data-ttu-id="36a72-145">`Start-Job` maakt gebruik van de para meter **script Block** om een opdracht uit te voeren `Get-Counter` .</span><span class="sxs-lookup"><span data-stu-id="36a72-145">`Start-Job` uses the **ScriptBlock** parameter to run a `Get-Counter` command.</span></span> <span data-ttu-id="36a72-146">`Get-Counter` maakt gebruik van de para meter **Counter** om het itempad op te geven `\LogicalDisk(_Total)\% Free Space` .</span><span class="sxs-lookup"><span data-stu-id="36a72-146">`Get-Counter` uses the **Counter** parameter to specify the counter path `\LogicalDisk(_Total)\% Free Space`.</span></span> <span data-ttu-id="36a72-147">De para meter **MaxSamples** geeft aan dat er 1000 voor beelden van de teller worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="36a72-147">The **MaxSamples** parameter specifies to get 1000 samples of the counter.</span></span>

### <span data-ttu-id="36a72-148">Voor beeld 6: item gegevens van meerdere computers ophalen</span><span class="sxs-lookup"><span data-stu-id="36a72-148">Example 6: Get counter data from multiple computers</span></span>

<span data-ttu-id="36a72-149">In dit voor beeld wordt een variabele gebruikt om prestatie meter items van twee computers op te halen.</span><span class="sxs-lookup"><span data-stu-id="36a72-149">This example uses a variable to get performance counter data from two computers.</span></span>

```powershell
$DiskReads = "\LogicalDisk(C:)\Disk Reads/sec"
$DiskReads | Get-Counter -ComputerName Server01, Server02 -MaxSamples 10
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/21/2019 10:51:04        \\Server01\logicaldisk(c:)\disk reads/sec :
                          0

                          \\Server02\logicaldisk(c:)\disk reads/sec :
                          0.983050344269146
```

<span data-ttu-id="36a72-150">De `$DiskReads` variabele slaat het `\LogicalDisk(C:)\Disk Reads/sec` itempad op.</span><span class="sxs-lookup"><span data-stu-id="36a72-150">The `$DiskReads` variable stores the `\LogicalDisk(C:)\Disk Reads/sec` counter path.</span></span> <span data-ttu-id="36a72-151">De `$DiskReads` variabele wordt naar beneden verzonden in de pijp lijn `Get-Counter` .</span><span class="sxs-lookup"><span data-stu-id="36a72-151">The `$DiskReads` variable is sent down the pipeline to `Get-Counter`.</span></span> <span data-ttu-id="36a72-152">**Teller** is de eerste positie parameter en accepteert het pad dat is opgeslagen in `$DiskReads` .</span><span class="sxs-lookup"><span data-stu-id="36a72-152">**Counter** is the first position parameter and accepts the path stored in `$DiskReads`.</span></span> <span data-ttu-id="36a72-153">**ComputerName** specificeert de twee computers en **MaxSamples** geeft aan dat er tien steek proeven van elke computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a72-153">**ComputerName** specifies the two computers and **MaxSamples** specifies to get 10 samples from each computer.</span></span>

### <span data-ttu-id="36a72-154">Voor beeld 7: de exemplaar waarden van een teller ophalen van meerdere wille keurige computers</span><span class="sxs-lookup"><span data-stu-id="36a72-154">Example 7: Get a counter's instance values from multiple random computers</span></span>

<span data-ttu-id="36a72-155">In dit voor beeld wordt de waarde van een prestatie meter item op 50 wille keurige externe computers in de onderneming opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a72-155">This example gets the value of a performance counter on 50 random, remote computers in the enterprise.</span></span> <span data-ttu-id="36a72-156">De para meter **ComputerName** gebruikt wille keurige computer namen die zijn opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="36a72-156">The **ComputerName** parameter uses random computer names stored in a variable.</span></span> <span data-ttu-id="36a72-157">Als u de computer namen in de variabele wilt bijwerken, maakt u de variabele opnieuw.</span><span class="sxs-lookup"><span data-stu-id="36a72-157">To update the computer names in the variable, recreate the variable.</span></span>

<span data-ttu-id="36a72-158">Een alternatief voor de server namen in de para meter **ComputerName** is het gebruik van een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="36a72-158">An alternative for the server names in the **ComputerName** parameter is to use a text file.</span></span> <span data-ttu-id="36a72-159">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="36a72-159">For example:</span></span>

`-ComputerName (Get-Random (Get-Content -Path C:\Servers.txt) -Count 50)`

<span data-ttu-id="36a72-160">Het itempad bevat een asterisk ( `*` ) in de naam van het exemplaar om de gegevens op te halen voor elk van de processors van de externe computer.</span><span class="sxs-lookup"><span data-stu-id="36a72-160">The counter path includes an asterisk (`*`) in the instance name to get the data for each of the remote computer's processors.</span></span>

```powershell
$Servers = Get-Random (Get-Content -Path C:\Servers.txt) -Count 50
$Counter = "\Processor(*)\% Processor Time"
Get-Counter -Counter $Counter -ComputerName $Servers
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/20/2019 12:20:35        \\Server01\processor(0)\% processor time :
                          6.52610319637854

                          \\Server01\processor(1)\% processor time :
                          3.41030663625782

                          \\Server01\processor(2)\% processor time :
                          9.64189975649925

                          \\Server01\processor(3)\% processor time :
                          1.85240835619747

                          \\Server01\processor(_total)\% processor time :
                          5.35768447160776
```

<span data-ttu-id="36a72-161">De `Get-Random` cmdlet gebruikt `Get-Content` om 50 wille keurige computer namen uit het bestand te selecteren `Servers.txt` .</span><span class="sxs-lookup"><span data-stu-id="36a72-161">The `Get-Random` cmdlet uses `Get-Content` to select 50 random computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="36a72-162">De namen van de externe computers worden opgeslagen in de `$Servers` variabele.</span><span class="sxs-lookup"><span data-stu-id="36a72-162">The remote computer names are stored in the `$Servers` variable.</span></span> <span data-ttu-id="36a72-163">Het `\Processor(*)\% Processor Time` pad van het item wordt opgeslagen in de `$Counter` variabele.</span><span class="sxs-lookup"><span data-stu-id="36a72-163">The `\Processor(*)\% Processor Time` counter's path is stored in the `$Counter` variable.</span></span> <span data-ttu-id="36a72-164">`Get-Counter` gebruikt de **teller** -para meter om de items in de variabele op te geven `$Counter` .</span><span class="sxs-lookup"><span data-stu-id="36a72-164">`Get-Counter` uses the **Counter** parameter to specify the counters in the `$Counter` variable.</span></span> <span data-ttu-id="36a72-165">Met de para meter **ComputerName** worden de computer namen in de `$Servers` variabele opgegeven.</span><span class="sxs-lookup"><span data-stu-id="36a72-165">The **ComputerName** parameter specifies the computer names in the `$Servers` variable.</span></span>

### <span data-ttu-id="36a72-166">Voor beeld 8: gebruik de eigenschap Path om opgemaakte padnamen op te halen</span><span class="sxs-lookup"><span data-stu-id="36a72-166">Example 8: Use the Path property to get formatted path names</span></span>

<span data-ttu-id="36a72-167">In dit voor beeld wordt de eigenschap **Path** van een counterset gebruikt om de opgemaakte padnamen voor de prestatie meter items te vinden.</span><span class="sxs-lookup"><span data-stu-id="36a72-167">This example uses the **Path** property of a counter set to find the formatted path names for the performance counters.</span></span>

<span data-ttu-id="36a72-168">De pijp lijn wordt met de `Where-Object` cmdlet gebruikt om een subset van de namen van de paden te vinden.</span><span class="sxs-lookup"><span data-stu-id="36a72-168">The pipeline is used with the `Where-Object` cmdlet to find a subset of the path names.</span></span> <span data-ttu-id="36a72-169">Als u wilt zoeken naar een item sets met een volledige lijst met item paden, verwijdert u de pijp lijn ( `|` ) en de `Where-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="36a72-169">To find a counter sets complete list of counter paths, remove the pipeline (`|`) and `Where-Object` command.</span></span>

<span data-ttu-id="36a72-170">De `$_` is een automatische variabele voor het huidige object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="36a72-170">The `$_` is an automatic variable for the current object in the pipeline.</span></span>
<span data-ttu-id="36a72-171">Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36a72-171">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
(Get-Counter -ListSet Memory).Paths | Where-Object { $_ -like "*Cache*" }
```

```Output
\Memory\Cache Faults/sec
\Memory\Cache Bytes
\Memory\Cache Bytes Peak
\Memory\System Cache Resident Bytes
\Memory\Standby Cache Reserve Bytes
\Memory\Standby Cache Normal Priority Bytes
\Memory\Standby Cache Core Bytes
\Memory\Long-Term Average Standby Cache Lifetime (s)
```

<span data-ttu-id="36a72-172">`Get-Counter` maakt gebruik van de **listset** -para meter om de set **geheugen** teller op te geven.</span><span class="sxs-lookup"><span data-stu-id="36a72-172">`Get-Counter` uses the **ListSet** parameter to specify the **Memory** counter set.</span></span> <span data-ttu-id="36a72-173">De opdracht bevindt zich tussen haakjes zodat de eigenschap **paden** elk pad retourneert als een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="36a72-173">The command is enclosed in parentheses so that the **Paths** property returns each path as a string.</span></span> <span data-ttu-id="36a72-174">De objecten worden naar beneden verzonden in de pijp lijn `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="36a72-174">The objects are sent down the pipeline to `Where-Object`.</span></span> <span data-ttu-id="36a72-175">`Where-Object` gebruikt de variabele `$_` voor het verwerken van elk object en gebruikt de `-like` operator om overeenkomsten te vinden voor de teken reeks `*Cache*` .</span><span class="sxs-lookup"><span data-stu-id="36a72-175">`Where-Object` uses the variable `$_` to process each object and uses the `-like` operator to find matches for the string `*Cache*`.</span></span> <span data-ttu-id="36a72-176">De sterretjes ( `*` ) zijn joker tekens voor wille keurige tekens.</span><span class="sxs-lookup"><span data-stu-id="36a72-176">The asterisks (`*`) are wildcards for any characters.</span></span>

### <span data-ttu-id="36a72-177">Voor beeld 9: gebruik de eigenschap PathsWithInstances om opgemaakte padnamen op te halen</span><span class="sxs-lookup"><span data-stu-id="36a72-177">Example 9: Use the PathsWithInstances property to get formatted path names</span></span>

<span data-ttu-id="36a72-178">In dit voor beeld worden de opgemaakte padnamen opgehaald die de instanties voor de **fysieke schijf** prestatie meter items bevatten.</span><span class="sxs-lookup"><span data-stu-id="36a72-178">This example gets the formatted path names that include the instances for the **PhysicalDisk** performance counters.</span></span>

```powershell
(Get-Counter -ListSet PhysicalDisk).PathsWithInstances
```

```Output
\PhysicalDisk(0 C:)\Current Disk Queue Length
\PhysicalDisk(_Total)\Current Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Time
\PhysicalDisk(_Total)\% Disk Time
\PhysicalDisk(0 C:)\Avg. Disk Queue Length
\PhysicalDisk(_Total)\Avg. Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Read Time
\PhysicalDisk(_Total)\% Disk Read Time
```

<span data-ttu-id="36a72-179">`Get-Counter` maakt gebruik van de **listset** -para meter om de tellerset van het **fysieke** volume op te geven.</span><span class="sxs-lookup"><span data-stu-id="36a72-179">`Get-Counter` uses the **ListSet** parameter to specify the **PhysicalDisk** counter set.</span></span> <span data-ttu-id="36a72-180">De opdracht bevindt zich tussen haakjes zodat de eigenschap **PathsWithInstances** elke apparaatinstantie als een teken reeks retourneert.</span><span class="sxs-lookup"><span data-stu-id="36a72-180">The command is enclosed in parentheses so that the **PathsWithInstances** property returns each path instance as a string.</span></span>

### <span data-ttu-id="36a72-181">Voor beeld 10: een enkele waarde ophalen voor elk item in een tellerset</span><span class="sxs-lookup"><span data-stu-id="36a72-181">Example 10: Get a single value for each counter in a counter set</span></span>

<span data-ttu-id="36a72-182">In dit voor beeld wordt één waarde geretourneerd voor elk prestatie meter item in de set **geheugen** tellers van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="36a72-182">In this example, a single value is returned for each performance counter in the local computer's **Memory** counter set.</span></span>

```powershell
$MemCounters = (Get-Counter -ListSet Memory).Paths
Get-Counter -Counter $MemCounters
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 12:05:00        \\Computer01\memory\page faults/sec :
                          868.772077545597

                          \\Computer01\memory\available bytes :
                          9031176192

                          \\Computer01\memory\committed bytes :
                          8242982912

                          \\Computer01\memory\commit limit :
                          19603333120
```

<span data-ttu-id="36a72-183">`Get-Counter` maakt gebruik van de **listset** -para meter om de set **geheugen** teller op te geven.</span><span class="sxs-lookup"><span data-stu-id="36a72-183">`Get-Counter` uses the **ListSet** parameter to specify the **Memory** counter set.</span></span> <span data-ttu-id="36a72-184">De opdracht bevindt zich tussen haakjes zodat de eigenschap **paden** elk pad retourneert als een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="36a72-184">The command is enclosed in parentheses so that the **Paths** property returns each path as a string.</span></span> <span data-ttu-id="36a72-185">De paden worden opgeslagen in de `$MemCounters` variabele.</span><span class="sxs-lookup"><span data-stu-id="36a72-185">The paths are stored in the `$MemCounters` variable.</span></span> <span data-ttu-id="36a72-186">`Get-Counter` gebruikt de **teller** -para meter om de item paden in de variabele op te geven `$MemCounters` .</span><span class="sxs-lookup"><span data-stu-id="36a72-186">`Get-Counter` uses the **Counter** parameter to specify the counter paths in the `$MemCounters` variable.</span></span>

### <span data-ttu-id="36a72-187">Voor beeld 11: de eigenschaps waarden van een object weer geven</span><span class="sxs-lookup"><span data-stu-id="36a72-187">Example 11: Display an object's property values</span></span>

<span data-ttu-id="36a72-188">De eigenschaps waarden in het object **PerformanceCounterSample** vertegenwoordigen elk gegevens voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="36a72-188">The property values in the **PerformanceCounterSample** object represent each data sample.</span></span> <span data-ttu-id="36a72-189">In dit voor beeld gebruiken we de eigenschappen van het object **CounterSamples** om de gegevens te bekijken, te selecteren, te sorteren en te groeperen.</span><span class="sxs-lookup"><span data-stu-id="36a72-189">In this example we use the properties of the **CounterSamples** object to examine, select, sort, and group the data.</span></span>

```powershell
$Counter = "\\Server01\Process(Idle)\% Processor Time"
$Data = Get-Counter $Counter
$Data.CounterSamples | Format-List -Property *
```

```Output
Path             : \\Server01\process(idle)\% processor time
InstanceName     : idle
CookedValue      : 198.467899571389
RawValue         : 14329160321003
SecondValue      : 128606459528326201
MultipleCount    : 1
CounterType      : Timer100Ns
Timestamp        : 6/19/2019 12:20:49
Timestamp100NSec : 128606207528320000
Status           : 0
DefaultScale     : 0
TimeBase         : 10000000
```

<span data-ttu-id="36a72-190">Het itempad wordt opgeslagen in de `$Counter` variabele.</span><span class="sxs-lookup"><span data-stu-id="36a72-190">The counter path is stored in the `$Counter` variable.</span></span> <span data-ttu-id="36a72-191">`Get-Counter` Hiermee wordt een voor beeld van de item waarden opgehaald en worden de resultaten opgeslagen in de `$Data` variabele.</span><span class="sxs-lookup"><span data-stu-id="36a72-191">`Get-Counter` gets one sample of the counter values and stores the results in the `$Data` variable.</span></span> <span data-ttu-id="36a72-192">De `$Data` variabele gebruikt de eigenschap **CounterSamples** om de eigenschappen van het object op te halen.</span><span class="sxs-lookup"><span data-stu-id="36a72-192">The `$Data` variable uses the **CounterSamples** property to get the object's properties.</span></span> <span data-ttu-id="36a72-193">Het object wordt naar de pijp lijn verzonden `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="36a72-193">The object is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="36a72-194">De **eigenschaps** parameter maakt gebruik van een asterisk ( `*` ) als Joker teken om alle eigenschappen te selecteren.</span><span class="sxs-lookup"><span data-stu-id="36a72-194">The **Property** parameter uses an asterisk (`*`) wildcard to select all the properties.</span></span>

### <span data-ttu-id="36a72-195">Voor beeld 12: matrix waarden voor prestatie meter items</span><span class="sxs-lookup"><span data-stu-id="36a72-195">Example 12: Performance counter array values</span></span>

<span data-ttu-id="36a72-196">In dit voor beeld wordt elk prestatie meter item opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="36a72-196">In this example, a variable stores each performance counter.</span></span> <span data-ttu-id="36a72-197">De eigenschap **CounterSamples** is een matrix waarin specifieke item waarden kunnen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36a72-197">The **CounterSamples** property is an array that can display specific counter values.</span></span>

<span data-ttu-id="36a72-198">Als u elk item voorbeeld wilt weer geven, gebruikt u `$Counter.CounterSamples` .</span><span class="sxs-lookup"><span data-stu-id="36a72-198">To display each counter sample, use `$Counter.CounterSamples`.</span></span>

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples[0]
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              1.33997091699662
```

<span data-ttu-id="36a72-199">`Get-Counter` Hiermee wordt **de teller-para meter** gebruikt om de teller op te geven `\Processor(*)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="36a72-199">`Get-Counter` uses the **Counter** parameter to specify the counter `\Processor(*)\% Processor Time`.</span></span> <span data-ttu-id="36a72-200">De waarden worden opgeslagen in de `$Counter` variabele.</span><span class="sxs-lookup"><span data-stu-id="36a72-200">The values are stored in the `$Counter` variable.</span></span>
<span data-ttu-id="36a72-201">`$Counter.CounterSamples[0]` Hiermee wordt de matrix waarde voor de waarde van het eerste item weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36a72-201">`$Counter.CounterSamples[0]` displays the array value for the first counter value.</span></span>

### <span data-ttu-id="36a72-202">Voor beeld 13: waarden van prestatie meter items vergelijken</span><span class="sxs-lookup"><span data-stu-id="36a72-202">Example 13: Compare performance counter values</span></span>

<span data-ttu-id="36a72-203">In dit voor beeld wordt gezocht naar de hoeveelheid processor tijd die door elke processor op de lokale computer wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="36a72-203">This example finds the amount of processor time used by each processor on the local computer.</span></span> <span data-ttu-id="36a72-204">De eigenschap **CounterSamples** wordt gebruikt om de item gegevens te vergelijken met een opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="36a72-204">The **CounterSamples** property is used to compare the counter data against a specified value.</span></span>

<span data-ttu-id="36a72-205">Als u elk item voorbeeld wilt weer geven, gebruikt u `$Counter.CounterSamples` .</span><span class="sxs-lookup"><span data-stu-id="36a72-205">To display each counter sample, use `$Counter.CounterSamples`.</span></span>

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples | Where-Object { $_.CookedValue -lt "20" }
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              12.6398025240208
\\Computer01\processor(1)\% processor time   1              15.7598095767344
```

<span data-ttu-id="36a72-206">`Get-Counter` Hiermee wordt **de teller-para meter** gebruikt om de teller op te geven `\Processor(*)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="36a72-206">`Get-Counter` uses the **Counter** parameter to specify the counter `\Processor(*)\% Processor Time`.</span></span> <span data-ttu-id="36a72-207">De waarden worden opgeslagen in de `$Counter` variabele.</span><span class="sxs-lookup"><span data-stu-id="36a72-207">The values are stored in the `$Counter` variable.</span></span> <span data-ttu-id="36a72-208">De objecten `$Counter.CounterSamples` die zijn opgeslagen in, worden naar de pijp lijn verzonden.</span><span class="sxs-lookup"><span data-stu-id="36a72-208">The objects stored in `$Counter.CounterSamples` are sent down the pipeline.</span></span> <span data-ttu-id="36a72-209">`Where-Object` maakt gebruik van een script blok om de waarde van elk object te vergelijken met een opgegeven waarde van 20.</span><span class="sxs-lookup"><span data-stu-id="36a72-209">`Where-Object` uses a script block to compare each objects value against a specified value of 20.</span></span> <span data-ttu-id="36a72-210">De `$_.CookedValue` is een variabele voor het huidige object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="36a72-210">The `$_.CookedValue` is a variable for the current object in the pipeline.</span></span> <span data-ttu-id="36a72-211">Tellers met een **CookedValue** die kleiner is dan 20 worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36a72-211">Counters with a **CookedValue** that is less than 20 are displayed.</span></span>

### <span data-ttu-id="36a72-212">Voor beeld 14: gegevens van prestatie meter items sorteren</span><span class="sxs-lookup"><span data-stu-id="36a72-212">Example 14: Sort performance counter data</span></span>

<span data-ttu-id="36a72-213">In dit voor beeld ziet u hoe gegevens van prestatie meter items worden gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="36a72-213">This example shows how to sort performance counter data.</span></span> <span data-ttu-id="36a72-214">In het voor beeld worden de processen gevonden op de computer die de meeste processor tijd gebruiken tijdens het voor beeld.</span><span class="sxs-lookup"><span data-stu-id="36a72-214">The example finds the processes on the computer that are using the most processor time during the sample.</span></span>

```powershell
$Procs = Get-Counter -Counter "\Process(*)\% Processor Time"
$Procs.CounterSamples | Sort-Object -Property CookedValue -Descending |
   Format-Table -Property Path, InstanceName, CookedValue -AutoSize
```

```Output
Path                                                         InstanceName             CookedValue
----                                                         ------------             -----------
\\Computer01\process(_total)\% processor time                _total              395.464129650573
\\Computer01\process(idle)\% processor time                  idle                389.356575524695
\\Computer01\process(mssense)\% processor time               mssense             3.05377706293879
\\Computer01\process(csrss#1)\% processor time               csrss               1.52688853146939
\\Computer01\process(microsoftedgecp#10)\% processor time    microsoftedgecp     1.52688853146939
\\Computer01\process(runtimebroker#5)\% processor time       runtimebroker                      0
\\Computer01\process(settingsynchost)\% processor time       settingsynchost                    0
\\Computer01\process(microsoftedgecp#16)\% processor time    microsoftedgecp                    0
```

<span data-ttu-id="36a72-215">`Get-Counter` gebruikt de **teller** -para meter om de `\Process(*)\% Processor Time` teller op te geven voor alle processen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="36a72-215">`Get-Counter` uses the **Counter** parameter to specify the `\Process(*)\% Processor Time` counter for all the processes on the local computer.</span></span> <span data-ttu-id="36a72-216">Het resultaat wordt opgeslagen in de `$Procs` variabele.</span><span class="sxs-lookup"><span data-stu-id="36a72-216">The result is stored in the `$Procs` variable.</span></span> <span data-ttu-id="36a72-217">De `$Procs` variabele met de eigenschap **CounterSamples** verzendt de **PerformanceCounterSample** -objecten omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="36a72-217">The `$Procs` variable with the **CounterSamples** property sends the **PerformanceCounterSample** objects down the pipeline.</span></span> <span data-ttu-id="36a72-218">`Sort-Object` gebruikt de para meter **Property** om de objecten te sorteren op **CookedValue** in **aflopende** volg orde.</span><span class="sxs-lookup"><span data-stu-id="36a72-218">`Sort-Object` uses the **Property** parameter to sort the objects by **CookedValue** in **Descending** order.</span></span> <span data-ttu-id="36a72-219">`Format-Table` gebruikt de para meter **Property** om de kolommen voor de uitvoer te selecteren.</span><span class="sxs-lookup"><span data-stu-id="36a72-219">`Format-Table` uses the **Property** parameter to select the columns for the output.</span></span> <span data-ttu-id="36a72-220">Met de para meter **AutoSize** worden de kolom breedten aangepast om de afkap ping te minimaliseren.</span><span class="sxs-lookup"><span data-stu-id="36a72-220">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

## <span data-ttu-id="36a72-221">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36a72-221">PARAMETERS</span></span>

### <span data-ttu-id="36a72-222">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="36a72-222">-ComputerName</span></span>

<span data-ttu-id="36a72-223">Hiermee geeft u een computer naam of een door komma's gescheiden matrix met **externe** computer namen op.</span><span class="sxs-lookup"><span data-stu-id="36a72-223">Specifies one computer name or a comma-separated array of **remote** computer names.</span></span> <span data-ttu-id="36a72-224">Gebruik de NetBIOS-naam, een IP-adres of de Fully Qualified Domain Name van de computer.</span><span class="sxs-lookup"><span data-stu-id="36a72-224">Use the NetBIOS name, an IP address, or the computer's fully qualified domain name.</span></span>

<span data-ttu-id="36a72-225">Als u prestatie meter gegevens wilt ophalen van de **lokale** computer, sluit u de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="36a72-225">To get performance counter data from the **local** computer, exclude the **ComputerName** parameter.</span></span>
<span data-ttu-id="36a72-226">Voor uitvoer, zoals een **lijstset** die de kolom **MachineName** bevat, geeft een punt ( `.` ) de lokale computer aan.</span><span class="sxs-lookup"><span data-stu-id="36a72-226">For output such as a **ListSet** that contains the **MachineName** column, a dot (`.`) indicates the local computer.</span></span>

<span data-ttu-id="36a72-227">`Get-Counter` vertrouwt niet op externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="36a72-227">`Get-Counter` doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="36a72-228">U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="36a72-228">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a72-229">-Doorlopend</span><span class="sxs-lookup"><span data-stu-id="36a72-229">-Continuous</span></span>

<span data-ttu-id="36a72-230">Wanneer de **doorlopende** is opgegeven, worden `Get-Counter` er voor beelden opgehaald totdat u op <kbd>CTRL</kbd> + <kbd>C</kbd>drukt.</span><span class="sxs-lookup"><span data-stu-id="36a72-230">When the **Continuous** is specified, `Get-Counter` gets samples until you press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="36a72-231">Voor elk opgegeven prestatie meter item worden voor beelden elke seconde opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a72-231">Samples are obtained every second for each specified performance counter.</span></span> <span data-ttu-id="36a72-232">Gebruik de para meter **SampleInterval** om het interval tussen opeenvolgende steek proeven te verhogen.</span><span class="sxs-lookup"><span data-stu-id="36a72-232">Use the **SampleInterval** parameter to increase the interval between continuous samples.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a72-233">-Teller</span><span class="sxs-lookup"><span data-stu-id="36a72-233">-Counter</span></span>

<span data-ttu-id="36a72-234">Hiermee geeft u het pad naar een of meer teller paden.</span><span class="sxs-lookup"><span data-stu-id="36a72-234">Specifies the path to one or more counter paths.</span></span> <span data-ttu-id="36a72-235">Paden worden ingevoerd als een door komma's gescheiden matrix, een variabele of waarden uit een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="36a72-235">Paths are input as a comma-separated array, a variable, or values from a text file.</span></span> <span data-ttu-id="36a72-236">U kunt tellers voor itempad naar beneden verplaatsen in de pijp lijn `Get-Counter` .</span><span class="sxs-lookup"><span data-stu-id="36a72-236">You can send counter path strings down the pipeline to `Get-Counter`.</span></span>

<span data-ttu-id="36a72-237">Teller paden gebruiken de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="36a72-237">Counter paths use the following syntax:</span></span>

`\\ComputerName\CounterSet(Instance)\CounterName`

`\CounterSet(Instance)\CounterName`

<span data-ttu-id="36a72-238">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="36a72-238">For example:</span></span>

`\\Server01\Processor(*)\% User Time`

`\Processor(*)\% User Time`

<span data-ttu-id="36a72-239">De `\\ComputerName` is optioneel in een pad voor prestatie meter items.</span><span class="sxs-lookup"><span data-stu-id="36a72-239">The `\\ComputerName` is optional in a performance counter path.</span></span> <span data-ttu-id="36a72-240">Als het itempad geen computer naam bevat, `Get-Counter` wordt de lokale computer gebruikt.</span><span class="sxs-lookup"><span data-stu-id="36a72-240">If the counter path doesn't include the computer name, `Get-Counter` uses the local computer.</span></span>

<span data-ttu-id="36a72-241">Een asterisk ( `*` ) in het exemplaar is een Joker teken om alle exemplaren van de teller op te halen.</span><span class="sxs-lookup"><span data-stu-id="36a72-241">An asterisk (`*`) in the instance is a wildcard character to get all instances of the counter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="36a72-242">-Lijstset</span><span class="sxs-lookup"><span data-stu-id="36a72-242">-ListSet</span></span>

<span data-ttu-id="36a72-243">Geeft een lijst van de prestatie meter sets op de computers.</span><span class="sxs-lookup"><span data-stu-id="36a72-243">Lists the performance counter sets on the computers.</span></span> <span data-ttu-id="36a72-244">Gebruik een asterisk ( `*` ) om alle item sets op te geven.</span><span class="sxs-lookup"><span data-stu-id="36a72-244">Use an asterisk (`*`) to specify all counter sets.</span></span> <span data-ttu-id="36a72-245">Voer één naam of een door komma's gescheiden teken reeks in voor de namen van de Counter sets.</span><span class="sxs-lookup"><span data-stu-id="36a72-245">Enter one name or a comma-separated string of counter set names.</span></span> <span data-ttu-id="36a72-246">U kunt namen van tellers sets omlaag verzenden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="36a72-246">You can send counter set names down the pipeline.</span></span>

<span data-ttu-id="36a72-247">Voor het ophalen van teller-paden die zijn opgemaakt met Counter sets, gebruikt u de **listset** -para meter.</span><span class="sxs-lookup"><span data-stu-id="36a72-247">To get a counter sets formatted counter paths, use the **ListSet** parameter.</span></span> <span data-ttu-id="36a72-248">De **paden** en **PathsWithInstances** -eigenschappen van elke verzameling tellers bevatten de afzonderlijke item paden die zijn opgemaakt als een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="36a72-248">The **Paths** and **PathsWithInstances** properties of each counter set contain the individual counter paths formatted as a string.</span></span>

<span data-ttu-id="36a72-249">U kunt de itempad teken reeksen in een variabele opslaan of de pijp lijn gebruiken om de teken reeks naar een andere opdracht te verzenden `Get-Counter` .</span><span class="sxs-lookup"><span data-stu-id="36a72-249">You can save the counter path strings in a variable or use the pipeline to send the string to another `Get-Counter` command.</span></span>

<span data-ttu-id="36a72-250">U kunt bijvoorbeeld elk pad naar de **processor** teller verzenden naar `Get-Counter` :</span><span class="sxs-lookup"><span data-stu-id="36a72-250">For example to send each **Processor** counter path to `Get-Counter`:</span></span>

`Get-Counter -ListSet Processor | Get-Counter`

> [!NOTE]
> <span data-ttu-id="36a72-251">In Power shell 7 `Get-Counter` kan de eigenschap **Description** van de verzameling tellers niet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a72-251">In PowerShell 7, `Get-Counter` can't retrieve the **Description** property of the counter set.</span></span> <span data-ttu-id="36a72-252">De **Beschrijving** is ingesteld op `$null` .</span><span class="sxs-lookup"><span data-stu-id="36a72-252">The **Description** is set to `$null`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="36a72-253">-MaxSamples</span><span class="sxs-lookup"><span data-stu-id="36a72-253">-MaxSamples</span></span>

<span data-ttu-id="36a72-254">Hiermee geeft u het aantal steek proeven op dat moet worden opgehaald van elk opgegeven prestatie meter item.</span><span class="sxs-lookup"><span data-stu-id="36a72-254">Specifies the number of samples to get from each specified performance counter.</span></span> <span data-ttu-id="36a72-255">Gebruik de **doorlopende** para meter om een constante stroom van voor beelden te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="36a72-255">To get a constant stream of samples, use the **Continuous** parameter.</span></span>

<span data-ttu-id="36a72-256">Als de para meter **MaxSamples** niet is opgegeven, `Get-Counter` wordt er slechts één voor beeld voor elke opgegeven teller opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a72-256">If the **MaxSamples** parameter isn't specified, `Get-Counter` only gets one sample for each specified counter.</span></span>

<span data-ttu-id="36a72-257">Als u een grote gegevensset wilt verzamelen, voert u uit `Get-Counter` als een Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="36a72-257">To collect a large data set, run `Get-Counter` as a PowerShell background job.</span></span> <span data-ttu-id="36a72-258">Zie [About Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) (Taken) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36a72-258">For more information, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a72-259">-SampleInterval</span><span class="sxs-lookup"><span data-stu-id="36a72-259">-SampleInterval</span></span>

<span data-ttu-id="36a72-260">Hiermee geeft u het aantal seconden tussen steek proeven op voor elk opgegeven prestatie meter item.</span><span class="sxs-lookup"><span data-stu-id="36a72-260">Specifies the number of seconds between samples for each specified performance counter.</span></span> <span data-ttu-id="36a72-261">Als de para meter **SampleInterval** niet wordt opgegeven, `Get-Counter` gebruikt een interval van één seconde.</span><span class="sxs-lookup"><span data-stu-id="36a72-261">If the **SampleInterval** parameter isn't specified, `Get-Counter` uses a one-second interval.</span></span>

```yaml
Type: System.Int32
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a72-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36a72-262">CommonParameters</span></span>

<span data-ttu-id="36a72-263">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36a72-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36a72-264">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36a72-264">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36a72-265">INVOER</span><span class="sxs-lookup"><span data-stu-id="36a72-265">INPUTS</span></span>

### <span data-ttu-id="36a72-266">System.String[]</span><span class="sxs-lookup"><span data-stu-id="36a72-266">System.String[]</span></span>

<span data-ttu-id="36a72-267">`Get-Counter` accepteert invoer van de pijp lijn voor item paden en namen van tellers.</span><span class="sxs-lookup"><span data-stu-id="36a72-267">`Get-Counter` accepts pipeline input for counter paths and counter set names.</span></span>

## <span data-ttu-id="36a72-268">UITVOER</span><span class="sxs-lookup"><span data-stu-id="36a72-268">OUTPUTS</span></span>

### <span data-ttu-id="36a72-269">Micro soft. Power shell. commands. GetCounter. Counterset, micro soft. Power shell. commands. GetCounter. PerformanceCounterSampleSet, micro soft. Power shell. commands. GetCounter. PerformanceCounterSample</span><span class="sxs-lookup"><span data-stu-id="36a72-269">Microsoft.PowerShell.Commands.GetCounter.CounterSet, Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet, Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSample</span></span>

<span data-ttu-id="36a72-270">Als u de eigenschappen van een object wilt weer geven, verzendt u de uitvoer naar de pijp lijn naar `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="36a72-270">To view an object's properties, send the output down the pipeline to `Get-Member`.</span></span> <span data-ttu-id="36a72-271">De object typen die worden uitgevoerd, zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="36a72-271">The object types that are output are as follows:</span></span>

<span data-ttu-id="36a72-272">**Listset** -para meter: **micro soft. Power shell. commands. GetCounter. counterset**</span><span class="sxs-lookup"><span data-stu-id="36a72-272">**ListSet** parameter: **Microsoft.PowerShell.Commands.GetCounter.CounterSet**</span></span>

<span data-ttu-id="36a72-273">**Teller** -para meter: **micro soft. Power shell. commands. GetCounter. PerformanceCounterSampleSet**</span><span class="sxs-lookup"><span data-stu-id="36a72-273">**Counter** parameter: **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet**</span></span>

<span data-ttu-id="36a72-274">Eigenschap **CounterSamples** : **micro soft. Power shell. commands. GetCounter. PerformanceCounterSample**</span><span class="sxs-lookup"><span data-stu-id="36a72-274">**CounterSamples** property: **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSample**</span></span>

## <span data-ttu-id="36a72-275">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="36a72-275">NOTES</span></span>

<span data-ttu-id="36a72-276">Als er geen para meters zijn opgegeven, `Get-Counter` wordt een voor beeld opgehaald voor elk opgegeven prestatie meter item.</span><span class="sxs-lookup"><span data-stu-id="36a72-276">If no parameters are specified, `Get-Counter` gets one sample for each specified performance counter.</span></span> <span data-ttu-id="36a72-277">Gebruik de **MaxSamples** -en **doorlopende** para meters om meer voor beelden te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="36a72-277">Use the **MaxSamples** and **Continuous** parameters to get more samples.</span></span>

<span data-ttu-id="36a72-278">`Get-Counter` maakt gebruik van een interval van één seconde tussen steek proeven.</span><span class="sxs-lookup"><span data-stu-id="36a72-278">`Get-Counter` uses a one-second interval between samples.</span></span> <span data-ttu-id="36a72-279">Gebruik de para meter **SampleInterval** om het interval te verhogen.</span><span class="sxs-lookup"><span data-stu-id="36a72-279">Use the **SampleInterval** parameter to increase the interval.</span></span>

<span data-ttu-id="36a72-280">De waarden **MaxSamples** en **SampleInterval** zijn van toepassing op alle items op elke computer in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="36a72-280">The **MaxSamples** and **SampleInterval** values apply to all the counters on each computer in the command.</span></span> <span data-ttu-id="36a72-281">Als u verschillende waarden voor verschillende items wilt instellen, voert u afzonderlijke `Get-Counter` opdrachten in.</span><span class="sxs-lookup"><span data-stu-id="36a72-281">To set different values for different counters, enter separate `Get-Counter` commands.</span></span>

<span data-ttu-id="36a72-282">Bij gebruik van de **listset** para meter kan in Power shell 7 `Get-Counter` de eigenschap **Description** van de verzameling tellers niet ophalen.</span><span class="sxs-lookup"><span data-stu-id="36a72-282">In PowerShell 7, when using the **ListSet** parameter, `Get-Counter` can't retrieve the **Description** property of the counter set.</span></span> <span data-ttu-id="36a72-283">De **Beschrijving** is ingesteld op `$null` .</span><span class="sxs-lookup"><span data-stu-id="36a72-283">The **Description** is set to `$null`.</span></span>

## <span data-ttu-id="36a72-284">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="36a72-284">RELATED LINKS</span></span>

[<span data-ttu-id="36a72-285">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="36a72-285">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="36a72-286">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="36a72-286">about_Jobs</span></span>](../Microsoft.PowerShell.Core/About/about_Jobs.md)

[<span data-ttu-id="36a72-287">Format-List</span><span class="sxs-lookup"><span data-stu-id="36a72-287">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="36a72-288">Format-Table</span><span class="sxs-lookup"><span data-stu-id="36a72-288">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="36a72-289">Get-member</span><span class="sxs-lookup"><span data-stu-id="36a72-289">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="36a72-290">Receive-job</span><span class="sxs-lookup"><span data-stu-id="36a72-290">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)

[<span data-ttu-id="36a72-291">Begin taak</span><span class="sxs-lookup"><span data-stu-id="36a72-291">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="36a72-292">Where-object</span><span class="sxs-lookup"><span data-stu-id="36a72-292">Where-Object</span></span>](..//Microsoft.PowerShell.Core/Where-Object.md)
