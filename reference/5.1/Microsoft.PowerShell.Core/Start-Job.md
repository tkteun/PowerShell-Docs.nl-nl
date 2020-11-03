---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 116e007cc28a91e3c97fd980cc27461932390b7c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250135"
---
# <span data-ttu-id="4673e-103">Start-Job</span><span class="sxs-lookup"><span data-stu-id="4673e-103">Start-Job</span></span>

## <span data-ttu-id="4673e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4673e-104">SYNOPSIS</span></span>
<span data-ttu-id="4673e-105">Start een Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="4673e-105">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="4673e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4673e-106">SYNTAX</span></span>

### <span data-ttu-id="4673e-107">Computer naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="4673e-107">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="4673e-108">Definitie</span><span class="sxs-lookup"><span data-stu-id="4673e-108">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="4673e-109">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="4673e-109">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="4673e-110">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="4673e-110">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="4673e-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4673e-111">DESCRIPTION</span></span>

<span data-ttu-id="4673e-112">`Start-Job`Met de cmdlet wordt een Power shell-achtergrond taak gestart op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4673e-112">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="4673e-113">Met een Power shell-achtergrond taak wordt een opdracht uitgevoerd zonder interactie met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="4673e-113">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="4673e-114">Wanneer u een achtergrond taak start, retourneert een taak object onmiddellijk, zelfs als de taak een lange tijd kost om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="4673e-114">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="4673e-115">U kunt zonder onderbreking in de sessie blijven werken terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4673e-115">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="4673e-116">Het taak object bevat nuttige informatie over de taak, maar bevat geen taak resultaten.</span><span class="sxs-lookup"><span data-stu-id="4673e-116">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="4673e-117">Wanneer de taak is voltooid, gebruikt `Receive-Job` u de cmdlet om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="4673e-117">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="4673e-118">Zie [about_Jobs](./About/about_Jobs.md)voor meer informatie over achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="4673e-118">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="4673e-119">Als u een achtergrond taak wilt uitvoeren op een externe computer, gebruikt u de para meter **AsJob** die beschikbaar is in veel cmdlets of gebruikt `Invoke-Command` u de cmdlet om een opdracht uit te voeren `Start-Job` op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="4673e-119">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="4673e-120">Zie [about_Remote_Jobs](./About/about_Remote_Jobs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4673e-120">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="4673e-121">Vanaf Power Shell 3,0 `Start-Job` kunnen exemplaren van aangepaste taak typen worden gestart, zoals geplande taken.</span><span class="sxs-lookup"><span data-stu-id="4673e-121">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="4673e-122">`Start-Job`Zie de Help-documenten voor de functie type taak voor meer informatie over het gebruik van om taken met aangepaste typen te starten.</span><span class="sxs-lookup"><span data-stu-id="4673e-122">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="4673e-123">De standaard werkmap voor taken is hardcoded.</span><span class="sxs-lookup"><span data-stu-id="4673e-123">The default working directory for jobs is hardcoded.</span></span> <span data-ttu-id="4673e-124">De Windows-standaard waarde is `$HOME\Documents` en op Linux of macOS de standaard waarde is `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="4673e-124">The Windows default is `$HOME\Documents` and on Linux or macOS the default is `$HOME`.</span></span> <span data-ttu-id="4673e-125">De script code die wordt uitgevoerd in de achtergrond taak moet de werkmap zo nodig beheren.</span><span class="sxs-lookup"><span data-stu-id="4673e-125">The script code running in the background job needs to manage the working directory as needed.</span></span>

## <span data-ttu-id="4673e-126">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4673e-126">EXAMPLES</span></span>

### <span data-ttu-id="4673e-127">Voor beeld 1: een achtergrond taak starten</span><span class="sxs-lookup"><span data-stu-id="4673e-127">Example 1: Start a background job</span></span>

<span data-ttu-id="4673e-128">In dit voor beeld wordt een achtergrond taak gestart die wordt uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4673e-128">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name powershell }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name powershell
```

<span data-ttu-id="4673e-129">`Start-Job` maakt gebruik van de para meter **script Block** om te worden uitgevoerd `Get-Process` als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="4673e-129">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="4673e-130">De para meter **name** geeft aan dat Power shell-processen moeten worden gevonden `powershell` .</span><span class="sxs-lookup"><span data-stu-id="4673e-130">The **Name** parameter specifies to find PowerShell processes, `powershell`.</span></span> <span data-ttu-id="4673e-131">De taak informatie wordt weer gegeven en Power shell keert terug naar een prompt wanneer de taak op de achtergrond wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4673e-131">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="4673e-132">Gebruik de cmdlet om de uitvoer van de taak weer te geven `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="4673e-132">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="4673e-133">Bijvoorbeeld `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="4673e-133">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="4673e-134">Voor beeld 2: een taak starten met Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="4673e-134">Example 2: Start a job using Invoke-Command</span></span>

<span data-ttu-id="4673e-135">In dit voor beeld wordt een taak op meerdere computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4673e-135">This example runs a job on multiple computers.</span></span> <span data-ttu-id="4673e-136">De taak wordt opgeslagen in een variabele en wordt uitgevoerd met behulp van de naam van de variabele op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="4673e-136">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="4673e-137">Een taak die gebruikmaakt `Invoke-Command` van wordt gemaakt en opgeslagen in de `$jobWRM` variabele.</span><span class="sxs-lookup"><span data-stu-id="4673e-137">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="4673e-138">`Invoke-Command` maakt gebruik van de para meter **ComputerName** om de computers op te geven waarop de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4673e-138">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="4673e-139">`Get-Content` Hiermee worden de server namen opgehaald uit het `C:\Servers.txt` bestand.</span><span class="sxs-lookup"><span data-stu-id="4673e-139">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="4673e-140">De **script Block** para meter geeft u een opdracht op waarmee `Get-Service` de **WinRM** -service wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="4673e-140">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="4673e-141">De **JobName** para meter geeft een beschrijvende naam voor de taak, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="4673e-141">The **JobName** parameter specifies a friendly name for the job, **WinRM**.</span></span> <span data-ttu-id="4673e-142">De para meter **ThrottleLimit** beperkt het aantal gelijktijdige opdrachten tot 16.</span><span class="sxs-lookup"><span data-stu-id="4673e-142">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="4673e-143">Met de para meter **AsJob** wordt een achtergrond taak gestart die de opdracht uitvoert op de-servers.</span><span class="sxs-lookup"><span data-stu-id="4673e-143">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="4673e-144">Voor beeld 3: taak gegevens ophalen</span><span class="sxs-lookup"><span data-stu-id="4673e-144">Example 3: Get job information</span></span>

<span data-ttu-id="4673e-145">In dit voor beeld wordt informatie over een taak opgehaald en worden de resultaten weer gegeven van een voltooide taak die is uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4673e-145">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="4673e-146">`Start-Job` maakt gebruik van de para meter **script Block** om een opdracht uit te voeren die opgeeft `Get-WinEvent` om het **systeem** logboek op te halen.</span><span class="sxs-lookup"><span data-stu-id="4673e-146">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="4673e-147">De **referentie** parameter geeft een domein gebruikers account op dat is gemachtigd om de taak uit te voeren op de computer.</span><span class="sxs-lookup"><span data-stu-id="4673e-147">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="4673e-148">Het taak object wordt opgeslagen in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="4673e-148">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="4673e-149">Het object in de `$j` variabele wordt naar beneden verzonden in de pijp lijn `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="4673e-149">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="4673e-150">De **eigenschap** para meter geeft een asterisk ( `*` ) op om alle eigenschappen van het taak object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4673e-150">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="4673e-151">Voor beeld 4: een script uitvoeren als een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="4673e-151">Example 4: Run a script as a background job</span></span>

<span data-ttu-id="4673e-152">In dit voor beeld wordt een script op de lokale computer uitgevoerd als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="4673e-152">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="4673e-153">`Start-Job` gebruikt de **filepath** -para meter om een script bestand op te geven dat is opgeslagen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4673e-153">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="4673e-154">Voor beeld 5: een proces met een achtergrond taak verkrijgen</span><span class="sxs-lookup"><span data-stu-id="4673e-154">Example 5: Get a process using a background job</span></span>

<span data-ttu-id="4673e-155">In dit voor beeld wordt een achtergrond taak gebruikt om een opgegeven proces op naam op te halen.</span><span class="sxs-lookup"><span data-stu-id="4673e-155">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="4673e-156">`Start-Job` maakt gebruik van de para meter **name** om een beschrijvende taak naam op te geven, **PShellJob**.</span><span class="sxs-lookup"><span data-stu-id="4673e-156">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob**.</span></span> <span data-ttu-id="4673e-157">De para meter **script Block** geeft `Get-Process` aan dat er processen worden opgehaald met de naam **Power shell**.</span><span class="sxs-lookup"><span data-stu-id="4673e-157">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell**.</span></span>

### <span data-ttu-id="4673e-158">Voor beeld 6: gegevens verzamelen en opslaan met behulp van een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="4673e-158">Example 6: Collect and save data by using a background job</span></span>

<span data-ttu-id="4673e-159">In dit voor beeld wordt een taak gestart die een grote hoeveelheid kaart gegevens verzamelt en vervolgens opslaat in een `.tif` bestand.</span><span class="sxs-lookup"><span data-stu-id="4673e-159">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif } -RunAs32
```

<span data-ttu-id="4673e-160">`Start-Job` maakt gebruik van de para meter **name** om een beschrijvende taak naam op te geven, **GetMappingFiles**.</span><span class="sxs-lookup"><span data-stu-id="4673e-160">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles**.</span></span> <span data-ttu-id="4673e-161">De para meter **InitializationScript** voert een script blok uit waarmee de **MapFunctions** -module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="4673e-161">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="4673e-162">De para meter **script Block** wordt uitgevoerd `Get-Map` en `Set-Content` de gegevens worden opgeslagen op de locatie die is opgegeven door de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="4673e-162">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="4673e-163">De para meter **RunAs32** voert het proces uit als 32-bits, zelfs op een 64-bits besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="4673e-163">The **RunAs32** parameter runs the process as 32-bit, even on a 64-bit operating system.</span></span>

### <span data-ttu-id="4673e-164">Voor beeld 7: invoer door geven aan een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="4673e-164">Example 7: Pass input to a background job</span></span>

<span data-ttu-id="4673e-165">In dit voor beeld wordt de `$input` Automatische variabele gebruikt voor het verwerken van een invoer object.</span><span class="sxs-lookup"><span data-stu-id="4673e-165">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="4673e-166">Gebruiken `Receive-Job` om de uitvoer van de taak weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4673e-166">Use `Receive-Job` to view the job's output.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

<span data-ttu-id="4673e-167">`Start-Job` maakt gebruik van de para meter **script Block** om te worden uitgevoerd `Get-Content` met de `$input` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="4673e-167">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="4673e-168">De `$input` variabele haalt objecten op uit de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="4673e-168">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="4673e-169">`Receive-Job` maakt gebruik van de para meter **name** om de taak op te geven en de resultaten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="4673e-169">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="4673e-170">De **Keep** -para meter slaat de taak uitvoer op zodat deze weer kan worden weer gegeven tijdens de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="4673e-170">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="4673e-171">Voor beeld 8: gebruik de para meter argument list om een matrix op te geven</span><span class="sxs-lookup"><span data-stu-id="4673e-171">Example 8: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="4673e-172">In dit voor beeld wordt de para meter **argument List** gebruikt om een matrix met argumenten op te geven.</span><span class="sxs-lookup"><span data-stu-id="4673e-172">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="4673e-173">De matrix is een door komma's gescheiden lijst met proces namen.</span><span class="sxs-lookup"><span data-stu-id="4673e-173">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="4673e-174">De `Start-Job` cmdlet gebruikt de para meter **script Block** om een opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="4673e-174">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="4673e-175">`Get-Process` maakt gebruik van de para meter **name** om de automatische variabele op te geven `$args` .</span><span class="sxs-lookup"><span data-stu-id="4673e-175">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="4673e-176">De **argument List** para meter geeft de matrix van proces namen door aan `$args` .</span><span class="sxs-lookup"><span data-stu-id="4673e-176">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="4673e-177">De proces namen Power shell, pwsh en Notepad zijn processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4673e-177">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="4673e-178">Gebruik de cmdlet om de uitvoer van de taak weer te geven `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="4673e-178">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="4673e-179">Bijvoorbeeld `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="4673e-179">For example, `Receive-Job -Id 1`.</span></span>

## <span data-ttu-id="4673e-180">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4673e-180">PARAMETERS</span></span>

### <span data-ttu-id="4673e-181">-Argument List</span><span class="sxs-lookup"><span data-stu-id="4673e-181">-ArgumentList</span></span>

<span data-ttu-id="4673e-182">Hiermee geeft u een matrix met argumenten, of parameter waarden, op voor het script dat is opgegeven met de para meter **filepath** of een opdracht die is opgegeven met de para meter **script Block** .</span><span class="sxs-lookup"><span data-stu-id="4673e-182">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="4673e-183">Argumenten moeten worden door gegeven aan **argument List** als een matrix argument met één dimensie.</span><span class="sxs-lookup"><span data-stu-id="4673e-183">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="4673e-184">Bijvoorbeeld een lijst met door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="4673e-184">For example, a comma-separated list.</span></span> <span data-ttu-id="4673e-185">Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="4673e-185">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-186">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="4673e-186">-Authentication</span></span>

<span data-ttu-id="4673e-187">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="4673e-187">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="4673e-188">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="4673e-188">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="4673e-189">Standaard</span><span class="sxs-lookup"><span data-stu-id="4673e-189">Default</span></span>
- <span data-ttu-id="4673e-190">Basic</span><span class="sxs-lookup"><span data-stu-id="4673e-190">Basic</span></span>
- <span data-ttu-id="4673e-191">CredSSP</span><span class="sxs-lookup"><span data-stu-id="4673e-191">Credssp</span></span>
- <span data-ttu-id="4673e-192">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="4673e-192">Digest</span></span>
- <span data-ttu-id="4673e-193">Kerberos</span><span class="sxs-lookup"><span data-stu-id="4673e-193">Kerberos</span></span>
- <span data-ttu-id="4673e-194">Negotiate</span><span class="sxs-lookup"><span data-stu-id="4673e-194">Negotiate</span></span>
- <span data-ttu-id="4673e-195">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="4673e-195">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="4673e-196">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="4673e-196">The default value is Default.</span></span>

<span data-ttu-id="4673e-197">CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="4673e-197">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="4673e-198">Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="4673e-198">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="4673e-199">De verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="4673e-199">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="4673e-200">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="4673e-200">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="4673e-201">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="4673e-201">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-202">-Credential</span><span class="sxs-lookup"><span data-stu-id="4673e-202">-Credential</span></span>

<span data-ttu-id="4673e-203">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="4673e-203">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="4673e-204">Als de para meter **Credential** niet is opgegeven, gebruikt de opdracht de referenties van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="4673e-204">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="4673e-205">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="4673e-205">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="4673e-206">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="4673e-206">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="4673e-207">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="4673e-207">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="4673e-208">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="4673e-208">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-209">-Definitie</span><span class="sxs-lookup"><span data-stu-id="4673e-209">-DefinitionName</span></span>

<span data-ttu-id="4673e-210">Hiermee geeft u de definitie naam op van de taak die met deze cmdlet wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="4673e-210">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="4673e-211">Gebruik deze para meter om aangepaste taak typen te starten die een definitie naam hebben, zoals geplande taken.</span><span class="sxs-lookup"><span data-stu-id="4673e-211">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="4673e-212">Wanneer u gebruikt `Start-Job` om een exemplaar van een geplande taak te starten, wordt de taak onmiddellijk gestart, ongeacht taak triggers of taak opties.</span><span class="sxs-lookup"><span data-stu-id="4673e-212">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="4673e-213">Het resulterende taak exemplaar is een geplande taak, maar wordt niet opgeslagen op schijf zoals geactiveerde geplande taken.</span><span class="sxs-lookup"><span data-stu-id="4673e-213">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="4673e-214">U kunt de para meter **argument List** niet gebruiken `Start-Job` om waarden op te geven voor para meters van scripts die worden uitgevoerd in een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="4673e-214">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span> <span data-ttu-id="4673e-215">Zie [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4673e-215">For more information, see [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md).</span></span>

<span data-ttu-id="4673e-216">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4673e-216">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-217">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="4673e-217">-DefinitionPath</span></span>

<span data-ttu-id="4673e-218">Hiermee geeft u het pad op van de definitie voor de taak die met deze cmdlet wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="4673e-218">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="4673e-219">Voer het definitie-pad in.</span><span class="sxs-lookup"><span data-stu-id="4673e-219">Enter the definition path.</span></span> <span data-ttu-id="4673e-220">De samen voeging van de waarden van de para meters **DefinitionPath** en **rijdefinitie** is het volledig gekwalificeerde pad van de taak definitie.</span><span class="sxs-lookup"><span data-stu-id="4673e-220">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="4673e-221">Gebruik deze para meter om aangepaste taak typen met een definitie-pad te starten, zoals geplande taken.</span><span class="sxs-lookup"><span data-stu-id="4673e-221">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="4673e-222">Voor geplande taken is de waarde van de **DefinitionPath** para meter DefinitionPath `$home\AppData\Local\Windows\PowerShell\ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="4673e-222">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="4673e-223">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4673e-223">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-224">-FilePath</span><span class="sxs-lookup"><span data-stu-id="4673e-224">-FilePath</span></span>

<span data-ttu-id="4673e-225">Hiermee geeft u een lokaal script op dat `Start-Job` als achtergrond taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4673e-225">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="4673e-226">Voer het pad en de bestands naam van het script in of gebruik de pijp lijn om een scriptpad naar te verzenden `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="4673e-226">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="4673e-227">Het script moet zich op de lokale computer of in een map bevindt waartoe de lokale computer toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="4673e-227">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="4673e-228">Wanneer u deze para meter gebruikt, wordt de inhoud van het opgegeven script bestand door Power shell naar een script blok geconverteerd en wordt het script blok als achtergrond taak uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4673e-228">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-229">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="4673e-229">-InitializationScript</span></span>

<span data-ttu-id="4673e-230">Geeft opdrachten die worden uitgevoerd voordat de taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="4673e-230">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="4673e-231">Als u een script blok wilt maken, plaatst u de opdrachten in accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="4673e-231">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="4673e-232">Gebruik deze para meter om de sessie voor te bereiden waarin de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4673e-232">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="4673e-233">U kunt dit bijvoorbeeld gebruiken om functies, modules en modules toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="4673e-233">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-234">-Input object</span><span class="sxs-lookup"><span data-stu-id="4673e-234">-InputObject</span></span>

<span data-ttu-id="4673e-235">Hiermee geeft u de invoer aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4673e-235">Specifies input to the command.</span></span> <span data-ttu-id="4673e-236">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4673e-236">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="4673e-237">Gebruik in de waarde van de para meter **script Block** de `$input` Automatische variabele om de invoer objecten te vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="4673e-237">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-238">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4673e-238">-LiteralPath</span></span>

<span data-ttu-id="4673e-239">Hiermee geeft u een lokaal script op dat met deze cmdlet als achtergrond taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4673e-239">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="4673e-240">Geef het pad van een script op de lokale computer op.</span><span class="sxs-lookup"><span data-stu-id="4673e-240">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="4673e-241">`Start-Job` gebruikt de waarde van de para meter **LiteralPath** precies zoals deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="4673e-241">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="4673e-242">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="4673e-242">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="4673e-243">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="4673e-243">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="4673e-244">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="4673e-244">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-245">-Name</span><span class="sxs-lookup"><span data-stu-id="4673e-245">-Name</span></span>

<span data-ttu-id="4673e-246">Hiermee geeft u een beschrijvende naam op voor de nieuwe taak.</span><span class="sxs-lookup"><span data-stu-id="4673e-246">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="4673e-247">U kunt de naam gebruiken om de taak te identificeren in andere taak-cmdlets, zoals de- `Stop-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4673e-247">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="4673e-248">De standaard beschrijvende naam is `Job#` , waarbij `#` een rang nummer is dat voor elke taak wordt verhoogd.</span><span class="sxs-lookup"><span data-stu-id="4673e-248">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-249">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="4673e-249">-PSVersion</span></span>

<span data-ttu-id="4673e-250">Hiermee geeft u een versie op.</span><span class="sxs-lookup"><span data-stu-id="4673e-250">Specifies a version.</span></span> <span data-ttu-id="4673e-251">`Start-Job` de taak wordt uitgevoerd met de versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="4673e-251">`Start-Job` runs the job with the version of PowerShell.</span></span> <span data-ttu-id="4673e-252">De acceptabele waarden voor deze para meter zijn: `2.0` en `3.0` .</span><span class="sxs-lookup"><span data-stu-id="4673e-252">The acceptable values for this parameter are: `2.0` and `3.0`.</span></span>

<span data-ttu-id="4673e-253">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4673e-253">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-254">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="4673e-254">-RunAs32</span></span>

<span data-ttu-id="4673e-255">Geeft aan dat `Start-Job` de taak wordt uitgevoerd in een 32-bits proces.</span><span class="sxs-lookup"><span data-stu-id="4673e-255">Indicates that `Start-Job` runs the job in a 32-bit process.</span></span> <span data-ttu-id="4673e-256">**RunAs32** zorgt ervoor dat de taak wordt uitgevoerd in een 32-bits proces, zelfs op een 64-bits besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="4673e-256">**RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="4673e-257">In 64-bits versies van Windows 7 en Windows Server 2008 R2, wanneer de `Start-Job` opdracht de para meter **RunAs32** bevat, kunt u de para meter **Credential** niet gebruiken om de referenties van een andere gebruiker op te geven.</span><span class="sxs-lookup"><span data-stu-id="4673e-257">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-258">-Script Block</span><span class="sxs-lookup"><span data-stu-id="4673e-258">-ScriptBlock</span></span>

<span data-ttu-id="4673e-259">Hiermee geeft u de opdrachten op die in de achtergrond taak moeten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4673e-259">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="4673e-260">Als u een script blok wilt maken, plaatst u de opdrachten in accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="4673e-260">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="4673e-261">Gebruik de `$input` Automatische variabele om toegang te krijgen tot de waarde van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="4673e-261">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="4673e-262">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="4673e-262">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-263">-Type</span><span class="sxs-lookup"><span data-stu-id="4673e-263">-Type</span></span>

<span data-ttu-id="4673e-264">Hiermee geeft u het aangepaste type op voor taken die worden gestart door `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="4673e-264">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="4673e-265">Voer een aangepaste taak type naam in, zoals PSScheduledJob voor geplande taken of PSWorkflowJob voor werk stroom taken.</span><span class="sxs-lookup"><span data-stu-id="4673e-265">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="4673e-266">Deze para meter is niet geldig voor standaard achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="4673e-266">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="4673e-267">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4673e-267">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4673e-268">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4673e-268">CommonParameters</span></span>

<span data-ttu-id="4673e-269">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4673e-269">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4673e-270">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4673e-270">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4673e-271">INVOER</span><span class="sxs-lookup"><span data-stu-id="4673e-271">INPUTS</span></span>

### <span data-ttu-id="4673e-272">System. String</span><span class="sxs-lookup"><span data-stu-id="4673e-272">System.String</span></span>

<span data-ttu-id="4673e-273">U kunt de pijp lijn gebruiken om een object met de **naam** -eigenschap naar de para meter **name** te verzenden.</span><span class="sxs-lookup"><span data-stu-id="4673e-273">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="4673e-274">U kunt bijvoorbeeld een **file info** -object uitlijnen van `Get-ChildItem` tot `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="4673e-274">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="4673e-275">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4673e-275">OUTPUTS</span></span>

### <span data-ttu-id="4673e-276">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="4673e-276">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="4673e-277">`Start-Job` retourneert een **PSRemotingJob** -object dat de taak vertegenwoordigt die het heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="4673e-277">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="4673e-278">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4673e-278">NOTES</span></span>

<span data-ttu-id="4673e-279">Om op de achtergrond uit te voeren, `Start-Job` wordt uitgevoerd in een eigen sessie in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="4673e-279">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="4673e-280">Wanneer u de `Invoke-Command` cmdlet gebruikt om een opdracht uit te voeren `Start-Job` in een sessie op een externe computer, `Start-Job` wordt uitgevoerd in een sessie in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="4673e-280">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="4673e-281">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4673e-281">RELATED LINKS</span></span>

[<span data-ttu-id="4673e-282">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="4673e-282">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="4673e-283">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="4673e-283">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="4673e-284">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="4673e-284">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="4673e-285">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="4673e-285">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="4673e-286">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="4673e-286">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="4673e-287">Get-job</span><span class="sxs-lookup"><span data-stu-id="4673e-287">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="4673e-288">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="4673e-288">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="4673e-289">Receive-job</span><span class="sxs-lookup"><span data-stu-id="4673e-289">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="4673e-290">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="4673e-290">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="4673e-291">Resume-job</span><span class="sxs-lookup"><span data-stu-id="4673e-291">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="4673e-292">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="4673e-292">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="4673e-293">Onderbreken-taak</span><span class="sxs-lookup"><span data-stu-id="4673e-293">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="4673e-294">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="4673e-294">Wait-Job</span></span>](Wait-Job.md)
