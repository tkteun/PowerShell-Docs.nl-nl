---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: 93db9ab1c8d70306fbf7243ac045ff0aa455dac6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705729"
---
# <span data-ttu-id="012ca-102">Get-Process</span><span class="sxs-lookup"><span data-stu-id="012ca-102">Get-Process</span></span>

## <span data-ttu-id="012ca-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="012ca-103">SYNOPSIS</span></span>
<span data-ttu-id="012ca-104">Hiermee worden de processen opgehaald die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="012ca-104">Gets the processes that are running on the local computer.</span></span>

## <span data-ttu-id="012ca-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="012ca-105">SYNTAX</span></span>

### <span data-ttu-id="012ca-106">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="012ca-106">Name (Default)</span></span>

```
Get-Process [[-Name] <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="012ca-107">NameWithUserName</span><span class="sxs-lookup"><span data-stu-id="012ca-107">NameWithUserName</span></span>

```
Get-Process [[-Name] <String[]>] -IncludeUserName [<CommonParameters>]
```

### <span data-ttu-id="012ca-108">Id</span><span class="sxs-lookup"><span data-stu-id="012ca-108">Id</span></span>

```
Get-Process -Id <Int32[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="012ca-109">IdWithUserName</span><span class="sxs-lookup"><span data-stu-id="012ca-109">IdWithUserName</span></span>

```
Get-Process -Id <Int32[]> -IncludeUserName [<CommonParameters>]
```

### <span data-ttu-id="012ca-110">Input object</span><span class="sxs-lookup"><span data-stu-id="012ca-110">InputObject</span></span>

```
Get-Process -InputObject <Process[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="012ca-111">InputObjectWithUserName</span><span class="sxs-lookup"><span data-stu-id="012ca-111">InputObjectWithUserName</span></span>

```
Get-Process -InputObject <Process[]> -IncludeUserName [<CommonParameters>]
```

## <span data-ttu-id="012ca-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="012ca-112">DESCRIPTION</span></span>

<span data-ttu-id="012ca-113">De `Get-Process` cmdlet haalt de processen op een lokale of externe computer op.</span><span class="sxs-lookup"><span data-stu-id="012ca-113">The `Get-Process` cmdlet gets the processes on a local or remote computer.</span></span>

<span data-ttu-id="012ca-114">Zonder para meters haalt deze cmdlet alle processen op de lokale computer op.</span><span class="sxs-lookup"><span data-stu-id="012ca-114">Without parameters, this cmdlet gets all of the processes on the local computer.</span></span> <span data-ttu-id="012ca-115">U kunt ook een bepaald proces opgeven op basis van de proces naam of proces-ID (PID) of een proces object door de pijp lijn door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="012ca-115">You can also specify a particular process by process name or process ID (PID) or pass a process object through the pipeline to this cmdlet.</span></span>

<span data-ttu-id="012ca-116">Met deze cmdlet wordt standaard een proces object geretourneerd dat gedetailleerde informatie over het proces bevat en methoden ondersteunt waarmee u het proces kunt starten en stoppen.</span><span class="sxs-lookup"><span data-stu-id="012ca-116">By default, this cmdlet returns a process object that has detailed information about the process and supports methods that let you start and stop the process.</span></span> <span data-ttu-id="012ca-117">U kunt ook de para meters van de `Get-Process` cmdlet gebruiken om informatie over de bestands versie op te halen voor het programma dat wordt uitgevoerd in het proces en om de modules op te halen die het proces heeft geladen.</span><span class="sxs-lookup"><span data-stu-id="012ca-117">You can also use the parameters of the `Get-Process` cmdlet to get file version information for the program that runs in the process and to get the modules that the process loaded.</span></span>

## <span data-ttu-id="012ca-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="012ca-118">EXAMPLES</span></span>

### <span data-ttu-id="012ca-119">Voor beeld 1: een lijst met alle actieve processen op de lokale computer ophalen</span><span class="sxs-lookup"><span data-stu-id="012ca-119">Example 1: Get a list of all active processes on the local computer</span></span>

```powershell
Get-Process
```

<span data-ttu-id="012ca-120">Met deze opdracht wordt een lijst met alle actieve processen opgehaald die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="012ca-120">This command gets a list of all active processes running on the local computer.</span></span> <span data-ttu-id="012ca-121">Zie de sectie [opmerkingen](#notes) voor een definitie van elke kolom.</span><span class="sxs-lookup"><span data-stu-id="012ca-121">For a definition of each column, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="012ca-122">Voor beeld 2: alle beschik bare gegevens over een of meer processen ophalen</span><span class="sxs-lookup"><span data-stu-id="012ca-122">Example 2: Get all available data about one or more processes</span></span>

```powershell
Get-Process winword, explorer | Format-List *
```

<span data-ttu-id="012ca-123">Met deze opdracht worden alle beschik bare gegevens over de processen Winword en Explorer op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="012ca-123">This command gets all available data about the Winword and Explorer processes on the computer.</span></span> <span data-ttu-id="012ca-124">Hierbij wordt de para meter **name** gebruikt voor het opgeven van de processen, maar de naam van de optionele para meter wordt wegge laten.</span><span class="sxs-lookup"><span data-stu-id="012ca-124">It uses the **Name** parameter to specify the processes, but it omits the optional parameter name.</span></span> <span data-ttu-id="012ca-125">De pijplijn operator `|` geeft de gegevens door aan de `Format-List` cmdlet, die alle beschik bare eigenschappen `*` van de objecten Winword en Explorer-proces weergeeft.</span><span class="sxs-lookup"><span data-stu-id="012ca-125">The pipeline operator `|` passes the data to the `Format-List` cmdlet, which displays all available properties `*` of the Winword and Explorer process objects.</span></span>

<span data-ttu-id="012ca-126">U kunt de processen ook identificeren aan de hand van hun proces-Id's.</span><span class="sxs-lookup"><span data-stu-id="012ca-126">You can also identify the processes by their process IDs.</span></span> <span data-ttu-id="012ca-127">Bijvoorbeeld `Get-Process -Id 664, 2060`.</span><span class="sxs-lookup"><span data-stu-id="012ca-127">For instance, `Get-Process -Id 664, 2060`.</span></span>

### <span data-ttu-id="012ca-128">Voor beeld 3: alle processen ophalen met een werkset die groter is dan een opgegeven grootte</span><span class="sxs-lookup"><span data-stu-id="012ca-128">Example 3: Get all processes with a working set greater than a specified size</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

<span data-ttu-id="012ca-129">Met deze opdracht worden alle processen opgehaald die een werkset hebben die groter is dan 20 MB.</span><span class="sxs-lookup"><span data-stu-id="012ca-129">This command gets all processes that have a working set greater than 20 MB.</span></span> <span data-ttu-id="012ca-130">De cmdlet wordt gebruikt `Get-Process` voor het ophalen van alle actieve processen.</span><span class="sxs-lookup"><span data-stu-id="012ca-130">It uses the `Get-Process` cmdlet to get all running processes.</span></span> <span data-ttu-id="012ca-131">De pijplijn operator `|` geeft de proces objecten door aan de `Where-Object` cmdlet, waarmee alleen het object wordt geselecteerd met een waarde die groter is dan 20.000.000 bytes voor de eigenschap **workingset** .</span><span class="sxs-lookup"><span data-stu-id="012ca-131">The pipeline operator `|` passes the process objects to the `Where-Object` cmdlet, which selects only the object with a value greater than 20,000,000 bytes for the **WorkingSet** property.</span></span>

<span data-ttu-id="012ca-132">**Workingset** is een van de vele eigenschappen van proces objecten.</span><span class="sxs-lookup"><span data-stu-id="012ca-132">**WorkingSet** is one of many properties of process objects.</span></span> <span data-ttu-id="012ca-133">Als u alle eigenschappen wilt weer geven, typt u `Get-Process | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="012ca-133">To see all of the properties, type `Get-Process | Get-Member`.</span></span> <span data-ttu-id="012ca-134">Standaard worden de waarden van alle eigenschappen van het bedrag in bytes weer gegeven, zelfs als de standaard weergave deze in kilo bytes en mega bytes vermeldt.</span><span class="sxs-lookup"><span data-stu-id="012ca-134">By default, the values of all amount properties are in bytes, even though the default display lists them in kilobytes and megabytes.</span></span>

### <span data-ttu-id="012ca-135">Voor beeld 4: processen op de computer in groepen weer geven op basis van prioriteit</span><span class="sxs-lookup"><span data-stu-id="012ca-135">Example 4: List processes on the computer in groups based on priority</span></span>

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

<span data-ttu-id="012ca-136">Met deze opdrachten worden de processen op de computer in groepen weer geven op basis van hun prioriteits klasse.</span><span class="sxs-lookup"><span data-stu-id="012ca-136">These commands list the processes on the computer in groups based on their priority class.</span></span> <span data-ttu-id="012ca-137">De eerste opdracht haalt alle processen op de computer op en slaat deze vervolgens op in de `$A` variabele.</span><span class="sxs-lookup"><span data-stu-id="012ca-137">The first command gets all the processes on the computer and then stores them in the `$A` variable.</span></span>

<span data-ttu-id="012ca-138">Met de tweede opdracht pipet u het **proces** object dat in de `$A` variabele is opgeslagen, naar de `Get-Process` cmdlet en vervolgens naar de `Format-Table` cmdlet, waarmee de processen worden opgemaakt met behulp van de weer gave **prioriteit** .</span><span class="sxs-lookup"><span data-stu-id="012ca-138">The second command pipes the **Process** object stored in the `$A` variable to the `Get-Process` cmdlet, then to the `Format-Table` cmdlet, which formats the processes by using the **Priority** view.</span></span>

<span data-ttu-id="012ca-139">De weer gave **prioriteit** en andere weer gaven worden gedefinieerd in de PS1XML-indelings bestanden in de Power shell-basis directory ( `$pshome` ).</span><span class="sxs-lookup"><span data-stu-id="012ca-139">The **Priority** view, and other views, are defined in the PS1XML format files in the PowerShell home directory (`$pshome`).</span></span>

### <span data-ttu-id="012ca-140">Voor beeld 5: een eigenschap toevoegen aan de standaard Get-Process uitvoer weergave</span><span class="sxs-lookup"><span data-stu-id="012ca-140">Example 5: Add a property to the standard Get-Process output display</span></span>

```powershell
Get-Process pwsh | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 .           pwsh
     6 23500 31348   142 2.75   4016 .           pwsh
    27 54572 54520   576 5.52   4428 .           pwsh
```

<span data-ttu-id="012ca-141">In dit voor beeld worden processen opgehaald van de lokale computer en een externe computer (S1).</span><span class="sxs-lookup"><span data-stu-id="012ca-141">This example retrieves processes from the local computer and a remote computer (S1).</span></span> <span data-ttu-id="012ca-142">De opgehaalde processen worden door gegeven aan de `Format-Table` opdracht waarmee de eigenschap **MachineName** wordt toegevoegd aan de standaard `Get-Process` uitvoer weergave.</span><span class="sxs-lookup"><span data-stu-id="012ca-142">The retrieved processes are piped to the `Format-Table` command that adds the **MachineName** property to the standard `Get-Process` output display.</span></span>

### <span data-ttu-id="012ca-143">Voor beeld 6: versie-informatie voor een proces ophalen</span><span class="sxs-lookup"><span data-stu-id="012ca-143">Example 6: Get version information for a process</span></span>

```powershell
Get-Process pwsh -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.2            6.1.2            C:\Program Files\PowerShell\6\pwsh.exe
```

<span data-ttu-id="012ca-144">Met deze opdracht wordt de **FileVersionInfo** -para meter gebruikt om de versie gegevens op te halen voor het pwsh.exe-bestand dat de belangrijkste module voor het Power Shell-proces is.</span><span class="sxs-lookup"><span data-stu-id="012ca-144">This command uses the **FileVersionInfo** parameter to get the version information for the pwsh.exe file that is the main module for the PowerShell process.</span></span>

<span data-ttu-id="012ca-145">Als u deze opdracht wilt uitvoeren met processen waarvan u geen eigenaar bent in Windows Vista en latere versies van Windows, moet u Power shell openen met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="012ca-145">To run this command with processes that you do not own on Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="012ca-146">Voor beeld 7: modules ophalen die met het opgegeven proces zijn geladen</span><span class="sxs-lookup"><span data-stu-id="012ca-146">Example 7: Get modules loaded with the specified process</span></span>

```powershell
Get-Process SQL* -Module
```

<span data-ttu-id="012ca-147">Met deze opdracht wordt de **module** parameter gebruikt om de modules op te halen die door het proces zijn geladen.</span><span class="sxs-lookup"><span data-stu-id="012ca-147">This command uses the **Module** parameter to get the modules that have been loaded by the process.</span></span>
<span data-ttu-id="012ca-148">Met deze opdracht worden de modules opgehaald voor de processen die namen hebben die met SQL beginnen.</span><span class="sxs-lookup"><span data-stu-id="012ca-148">This command gets the modules for the processes that have names that begin with SQL.</span></span>

<span data-ttu-id="012ca-149">Als u deze opdracht wilt uitvoeren in Windows Vista en latere versies van Windows met processen waarvan u geen eigenaar bent, moet u Power shell starten met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="012ca-149">To run this command on Windows Vista and later versions of Windows with processes that you do not own, you must start PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="012ca-150">Voor beeld 8: de eigenaar van een proces zoeken</span><span class="sxs-lookup"><span data-stu-id="012ca-150">Example 8: Find the owner of a process</span></span>

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     pwsh
```

<span data-ttu-id="012ca-151">Met deze opdracht wordt aangegeven hoe u de eigenaar van een proces kunt vinden.</span><span class="sxs-lookup"><span data-stu-id="012ca-151">This command shows how to find the owner of a process.</span></span>
<span data-ttu-id="012ca-152">In Windows vereist de para meter **IncludeUserName** verhoogde gebruikers rechten (als administrator uitvoeren).</span><span class="sxs-lookup"><span data-stu-id="012ca-152">On Windows, the **IncludeUserName** parameter requires elevated user rights (Run as Administrator).</span></span>
<span data-ttu-id="012ca-153">De uitvoer laat zien dat de eigenaar Domain01\user01. is</span><span class="sxs-lookup"><span data-stu-id="012ca-153">The output reveals that the owner is Domain01\user01.</span></span>

### <span data-ttu-id="012ca-154">Voor beeld 9: een automatische variabele gebruiken om het proces te identificeren dat als host fungeert voor de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="012ca-154">Example 9: Use an automatic variable to identify the process hosting the current session</span></span>

```powershell
Get-Process pwsh
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21     105.95       4.33    1192  10 pwsh
    79    83.81     117.61       2.16   10580  10 pwsh
```

```powershell
Get-Process -Id $PID
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21      77.53       4.39    1192  10 pwsh
```

<span data-ttu-id="012ca-155">Deze opdrachten laten zien hoe u de `$PID` Automatische variabele gebruikt om het proces te identificeren dat als host fungeert voor de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="012ca-155">These commands show how to use the `$PID` automatic variable to identify the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="012ca-156">U kunt deze methode gebruiken om het hostproces te onderscheiden van andere Power shell-processen die u mogelijk wilt stoppen of sluiten.</span><span class="sxs-lookup"><span data-stu-id="012ca-156">You can use this method to distinguish the host process from other PowerShell processes that you might want to stop or close.</span></span>

<span data-ttu-id="012ca-157">Met de eerste opdracht worden alle Power shell-processen in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="012ca-157">The first command gets all of the PowerShell processes in the current session.</span></span>

<span data-ttu-id="012ca-158">Met de tweede opdracht wordt het Power Shell-proces opgehaald dat als host fungeert voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="012ca-158">The second command gets the PowerShell process that is hosting the current session.</span></span>

### <span data-ttu-id="012ca-159">Voor beeld 10: alle processen met een hoofd venster titel ophalen en weer geven in een tabel</span><span class="sxs-lookup"><span data-stu-id="012ca-159">Example 10: Get all processes that have a main window title and display them in a table</span></span>

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

<span data-ttu-id="012ca-160">Met deze opdracht worden alle processen opgehaald die een hoofd venster titel hebben en worden deze weer gegeven in een tabel met de proces-ID en de proces naam.</span><span class="sxs-lookup"><span data-stu-id="012ca-160">This command gets all the processes that have a main window title, and it displays them in a table with the process ID and the process name.</span></span>

<span data-ttu-id="012ca-161">De eigenschap **mainWindowTitle** is slechts een van de vele handige eigenschappen van het **proces** object dat `Get-Process` retourneert.</span><span class="sxs-lookup"><span data-stu-id="012ca-161">The **mainWindowTitle** property is just one of many useful properties of the **Process** object that `Get-Process` returns.</span></span> <span data-ttu-id="012ca-162">Als u alle eigenschappen wilt weer geven, pipet u de resultaten van een `Get-Process` opdracht naar de `Get-Member` cmdlet `Get-Process | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="012ca-162">To view all of the properties, pipe the results of a `Get-Process` command to the `Get-Member` cmdlet `Get-Process | Get-Member`.</span></span>

## <span data-ttu-id="012ca-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="012ca-163">PARAMETERS</span></span>

### <span data-ttu-id="012ca-164">-FileVersionInfo</span><span class="sxs-lookup"><span data-stu-id="012ca-164">-FileVersionInfo</span></span>

<span data-ttu-id="012ca-165">Geeft aan dat met deze cmdlet de informatie over de bestands versie wordt opgehaald voor het programma dat in het proces wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="012ca-165">Indicates that this cmdlet gets the file version information for the program that runs in the process.</span></span>

<span data-ttu-id="012ca-166">In Windows Vista en latere versies van Windows moet u Power shell openen met de optie als administrator uitvoeren om deze para meter te gebruiken voor processen waarvan u geen eigenaar bent.</span><span class="sxs-lookup"><span data-stu-id="012ca-166">On Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="012ca-167">Als u informatie over de bestands versie wilt ophalen voor een proces op een externe computer, gebruikt u de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="012ca-167">To get file version information for a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="012ca-168">Het gebruik van deze para meter komt overeen met het ophalen van de eigenschap **MainModule. FileVersionInfo** van elk proces object.</span><span class="sxs-lookup"><span data-stu-id="012ca-168">Using this parameter is equivalent to getting the **MainModule.FileVersionInfo** property of each process object.</span></span> <span data-ttu-id="012ca-169">Wanneer u deze para meter gebruikt, `Get-Process` retourneert een **FileVersionInfo** -object **System. Diagnostics. FileVersionInfo**, geen process-object.</span><span class="sxs-lookup"><span data-stu-id="012ca-169">When you use this parameter, `Get-Process` returns a **FileVersionInfo** object **System.Diagnostics.FileVersionInfo**, not a process object.</span></span> <span data-ttu-id="012ca-170">U kunt de uitvoer van de opdracht dus niet door sluizen naar een cmdlet die een proces object verwacht, zoals `Stop-Process` .</span><span class="sxs-lookup"><span data-stu-id="012ca-170">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="012ca-171">-Id</span><span class="sxs-lookup"><span data-stu-id="012ca-171">-Id</span></span>

<span data-ttu-id="012ca-172">Hiermee geeft u een of meer processen op proces-ID (PID).</span><span class="sxs-lookup"><span data-stu-id="012ca-172">Specifies one or more processes by process ID (PID).</span></span> <span data-ttu-id="012ca-173">Als u meerdere Id's wilt opgeven, gebruikt u komma's om de Id's van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="012ca-173">To specify multiple IDs, use commas to separate the IDs.</span></span> <span data-ttu-id="012ca-174">Als u de PID van een proces wilt vinden, typt u `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="012ca-174">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id, IdWithUserName
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="012ca-175">-IncludeUserName</span><span class="sxs-lookup"><span data-stu-id="012ca-175">-IncludeUserName</span></span>

<span data-ttu-id="012ca-176">Geeft aan dat de waarde van de gebruikers naam van het **proces** object wordt geretourneerd met de resultaten van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="012ca-176">Indicates that the UserName value of the **Process** object is returned with results of the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="012ca-177">-Input object</span><span class="sxs-lookup"><span data-stu-id="012ca-177">-InputObject</span></span>

<span data-ttu-id="012ca-178">Hiermee geeft u een of meer proces objecten op.</span><span class="sxs-lookup"><span data-stu-id="012ca-178">Specifies one or more process objects.</span></span> <span data-ttu-id="012ca-179">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="012ca-179">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="012ca-180">-Module</span><span class="sxs-lookup"><span data-stu-id="012ca-180">-Module</span></span>

<span data-ttu-id="012ca-181">Geeft aan dat met deze cmdlet de modules worden opgehaald die zijn geladen door de processen.</span><span class="sxs-lookup"><span data-stu-id="012ca-181">Indicates that this cmdlet gets the modules that have been loaded by the processes.</span></span>

<span data-ttu-id="012ca-182">In Windows Vista en latere versies van Windows moet u Power shell openen met de optie **als administrator uitvoeren** om deze para meter te gebruiken voor processen waarvan u geen eigenaar bent.</span><span class="sxs-lookup"><span data-stu-id="012ca-182">On Windows Vista and later versions of Windows, you must open PowerShell with the **Run as administrator** option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="012ca-183">Gebruik de cmdlet om de modules op te halen die zijn geladen door een proces op een externe computer `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="012ca-183">To get the modules that have been loaded by a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="012ca-184">Deze para meter is gelijk aan het ophalen van de eigenschap **modules** van elk proces object.</span><span class="sxs-lookup"><span data-stu-id="012ca-184">This parameter is equivalent to getting the **Modules** property of each process object.</span></span> <span data-ttu-id="012ca-185">Wanneer u deze para meter gebruikt, retourneert deze cmdlet een **ProcessModule** -object **System. Diagnostics. ProcessModule**, geen process-object.</span><span class="sxs-lookup"><span data-stu-id="012ca-185">When you use this parameter, this cmdlet returns a **ProcessModule** object **System.Diagnostics.ProcessModule**, not a process object.</span></span> <span data-ttu-id="012ca-186">U kunt de uitvoer van de opdracht dus niet door sluizen naar een cmdlet die een proces object verwacht, zoals `Stop-Process` .</span><span class="sxs-lookup"><span data-stu-id="012ca-186">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

<span data-ttu-id="012ca-187">Wanneer u zowel de *module* -als de **FileVersionInfo** -para meters in dezelfde opdracht gebruikt, retourneert deze cmdlet een **FileVersionInfo** -object met informatie over de bestands versie van alle modules.</span><span class="sxs-lookup"><span data-stu-id="012ca-187">When you use both the *Module* and **FileVersionInfo** parameters in the same command, this cmdlet returns a **FileVersionInfo** object with information about the file version of all modules.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="012ca-188">-Name</span><span class="sxs-lookup"><span data-stu-id="012ca-188">-Name</span></span>

<span data-ttu-id="012ca-189">Hiermee geeft u een of meer processen op proces naam.</span><span class="sxs-lookup"><span data-stu-id="012ca-189">Specifies one or more processes by process name.</span></span> <span data-ttu-id="012ca-190">U kunt meerdere proces namen typen (gescheiden door komma's) en Joker tekens gebruiken.</span><span class="sxs-lookup"><span data-stu-id="012ca-190">You can type multiple process names (separated by commas) and use wildcard characters.</span></span> <span data-ttu-id="012ca-191">De parameter naam ("naam") is optioneel.</span><span class="sxs-lookup"><span data-stu-id="012ca-191">The parameter name ("Name") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="012ca-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="012ca-192">CommonParameters</span></span>

<span data-ttu-id="012ca-193">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="012ca-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="012ca-194">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="012ca-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="012ca-195">INVOER</span><span class="sxs-lookup"><span data-stu-id="012ca-195">INPUTS</span></span>

### <span data-ttu-id="012ca-196">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="012ca-196">System.Diagnostics.Process</span></span>

<span data-ttu-id="012ca-197">U kunt een proces object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="012ca-197">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="012ca-198">UITVOER</span><span class="sxs-lookup"><span data-stu-id="012ca-198">OUTPUTS</span></span>

### <span data-ttu-id="012ca-199">System. Diagnostics. proces, System. Diagnostics. FileVersionInfo, System. Diagnostics. ProcessModule</span><span class="sxs-lookup"><span data-stu-id="012ca-199">System.Diagnostics.Process, System.Diagnostics.FileVersionInfo, System.Diagnostics.ProcessModule</span></span>

<span data-ttu-id="012ca-200">Met deze cmdlet wordt standaard een **System. Diagnostics. process** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="012ca-200">By default, this cmdlet returns a **System.Diagnostics.Process** object.</span></span> <span data-ttu-id="012ca-201">Als u de para meter **FileVersionInfo** gebruikt, wordt een **System. Diagnostics. FileVersionInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="012ca-201">If you use the **FileVersionInfo** parameter, it returns a **System.Diagnostics.FileVersionInfo** object.</span></span> <span data-ttu-id="012ca-202">Als u de **module** parameter gebruikt zonder de para meter **FileVersionInfo** , wordt er een **System. Diagnostics. ProcessModule** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="012ca-202">If you use the **Module** parameter, without the **FileVersionInfo** parameter, it returns a **System.Diagnostics.ProcessModule** object.</span></span>

## <span data-ttu-id="012ca-203">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="012ca-203">NOTES</span></span>

- <span data-ttu-id="012ca-204">U kunt ook naar deze cmdlet verwijzen door de ingebouwde aliassen ps en GPS te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="012ca-204">You can also refer to this cmdlet by its built-in aliases, ps and gps.</span></span> <span data-ttu-id="012ca-205">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="012ca-205">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="012ca-206">Op computers waarop een 64-bits versie van Windows wordt uitgevoerd, worden door de 64-bits versie van Power shell alleen de 64-bits proces modules en de 32-bits versie van Power shell alleen 32-bits proces modules opgehaald.</span><span class="sxs-lookup"><span data-stu-id="012ca-206">On computers that are running a 64-bit version of Windows, the 64-bit version of PowerShell gets only 64-bit process modules and the 32-bit version of PowerShell gets only 32-bit process modules.</span></span>
- <span data-ttu-id="012ca-207">U kunt de eigenschappen en methoden van het Windows Management Instrumentation (WMI) Win32_Process-object in Power shell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="012ca-207">You can use the properties and methods of the Windows Management Instrumentation (WMI) Win32_Process object in PowerShell.</span></span> <span data-ttu-id="012ca-208">Zie `Get-WmiObject` en de WMI-SDK voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="012ca-208">For information, see `Get-WmiObject` and the WMI SDK.</span></span>
- <span data-ttu-id="012ca-209">De standaard weergave van een proces is een tabel die de volgende kolommen bevat.</span><span class="sxs-lookup"><span data-stu-id="012ca-209">The default display of a process is a table that includes the following columns.</span></span> <span data-ttu-id="012ca-210">Zie [Eigenschappen](/dotnet/api/system.diagnostics.process)van het proces voor een beschrijving van alle eigenschappen van proces objecten.</span><span class="sxs-lookup"><span data-stu-id="012ca-210">For a description of all of the properties of process objects, see [Process Properties](/dotnet/api/system.diagnostics.process).</span></span>
  - <span data-ttu-id="012ca-211">Handgrepen: het aantal ingangen dat het proces heeft geopend.</span><span class="sxs-lookup"><span data-stu-id="012ca-211">Handles: The number of handles that the process has opened.</span></span>
  - <span data-ttu-id="012ca-212">NPM (K): de hoeveelheid niet-wisselbaar geheugen die door het proces wordt gebruikt, in kilo bytes.</span><span class="sxs-lookup"><span data-stu-id="012ca-212">NPM(K): The amount of non-paged memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="012ca-213">PM (K): de hoeveelheid wisselbaar geheugen die door het proces wordt gebruikt, in kilo bytes.</span><span class="sxs-lookup"><span data-stu-id="012ca-213">PM(K): The amount of pageable memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="012ca-214">WS (K): de grootte van de werkset van het proces, in kilo bytes.</span><span class="sxs-lookup"><span data-stu-id="012ca-214">WS(K): The size of the working set of the process, in kilobytes.</span></span>
    <span data-ttu-id="012ca-215">De werkset bestaat uit de geheugen pagina's waarnaar recent werd verwezen door het proces.</span><span class="sxs-lookup"><span data-stu-id="012ca-215">The working set consists of the pages of memory that were recently referenced by the process.</span></span>
  - <span data-ttu-id="012ca-216">VM (M): de hoeveelheid virtueel geheugen die door het proces wordt gebruikt, in mega bytes.</span><span class="sxs-lookup"><span data-stu-id="012ca-216">VM(M): The amount of virtual memory that the process is using, in megabytes.</span></span>
    <span data-ttu-id="012ca-217">Virtueel geheugen bevat opslag in de Wissel bestanden op schijf.</span><span class="sxs-lookup"><span data-stu-id="012ca-217">Virtual memory includes storage in the paging files on disk.</span></span>
  - <span data-ttu-id="012ca-218">CPU ('s): de hoeveelheid processor tijd die het proces heeft gebruikt op alle processors, in seconden.</span><span class="sxs-lookup"><span data-stu-id="012ca-218">CPU(s): The amount of processor time that the process has used on all processors, in seconds.</span></span>
  - <span data-ttu-id="012ca-219">ID: de proces-ID (PID) van het proces.</span><span class="sxs-lookup"><span data-stu-id="012ca-219">ID: The process ID (PID) of the process.</span></span>
  - <span data-ttu-id="012ca-220">Verwerker: de naam van het proces.</span><span class="sxs-lookup"><span data-stu-id="012ca-220">ProcessName: The name of the process.</span></span> <span data-ttu-id="012ca-221">Zie de woorden lijst in Help en ondersteuning en de Help voor taak beheer voor uitleg van de concepten die betrekking hebben op processen.</span><span class="sxs-lookup"><span data-stu-id="012ca-221">For explanations of the concepts related to processes, see the Glossary in Help and Support Center and the Help for Task Manager.</span></span>
- <span data-ttu-id="012ca-222">U kunt ook de ingebouwde alternatieve weer gaven van de beschik bare processen gebruiken `Format-Table` , zoals **StartTime** en **prioriteit**, en u kunt uw eigen weer gaven ontwerpen.</span><span class="sxs-lookup"><span data-stu-id="012ca-222">You can also use the built-in alternate views of the processes available with `Format-Table`, such as **StartTime** and **Priority**, and you can design your own views.</span></span>

## <span data-ttu-id="012ca-223">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="012ca-223">RELATED LINKS</span></span>

[<span data-ttu-id="012ca-224">Debug-proces</span><span class="sxs-lookup"><span data-stu-id="012ca-224">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="012ca-225">Get-Process</span><span class="sxs-lookup"><span data-stu-id="012ca-225">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="012ca-226">Start-process</span><span class="sxs-lookup"><span data-stu-id="012ca-226">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="012ca-227">Stoppen-proces</span><span class="sxs-lookup"><span data-stu-id="012ca-227">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="012ca-228">Wacht proces</span><span class="sxs-lookup"><span data-stu-id="012ca-228">Wait-Process</span></span>](Wait-Process.md)
