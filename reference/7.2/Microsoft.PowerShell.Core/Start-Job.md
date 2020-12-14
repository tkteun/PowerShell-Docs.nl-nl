---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 491292253578f287940490bad198698fc4b87e37
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705892"
---
# <span data-ttu-id="3adbd-102">Start-Job</span><span class="sxs-lookup"><span data-stu-id="3adbd-102">Start-Job</span></span>

## <span data-ttu-id="3adbd-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3adbd-103">SYNOPSIS</span></span>
<span data-ttu-id="3adbd-104">Start een Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="3adbd-104">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="3adbd-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3adbd-105">SYNTAX</span></span>

### <span data-ttu-id="3adbd-106">Computer naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="3adbd-106">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="3adbd-107">Definitie</span><span class="sxs-lookup"><span data-stu-id="3adbd-107">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [-WorkingDirectory <String>] [<CommonParameters>]
```

### <span data-ttu-id="3adbd-108">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="3adbd-108">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="3adbd-109">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="3adbd-109">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="3adbd-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3adbd-110">DESCRIPTION</span></span>

<span data-ttu-id="3adbd-111">`Start-Job`Met de cmdlet wordt een Power shell-achtergrond taak gestart op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3adbd-111">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="3adbd-112">Met een Power shell-achtergrond taak wordt een opdracht uitgevoerd zonder interactie met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-112">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="3adbd-113">Wanneer u een achtergrond taak start, retourneert een taak object onmiddellijk, zelfs als de taak een lange tijd kost om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="3adbd-113">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="3adbd-114">U kunt zonder onderbreking in de sessie blijven werken terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-114">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="3adbd-115">Het taak object bevat nuttige informatie over de taak, maar bevat geen taak resultaten.</span><span class="sxs-lookup"><span data-stu-id="3adbd-115">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="3adbd-116">Wanneer de taak is voltooid, gebruikt `Receive-Job` u de cmdlet om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="3adbd-116">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="3adbd-117">Zie [about_Jobs](./About/about_Jobs.md)voor meer informatie over achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="3adbd-117">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="3adbd-118">Als u een achtergrond taak wilt uitvoeren op een externe computer, gebruikt u de para meter **AsJob** die beschikbaar is in veel cmdlets of gebruikt `Invoke-Command` u de cmdlet om een opdracht uit te voeren `Start-Job` op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="3adbd-118">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="3adbd-119">Zie [about_Remote_Jobs](./About/about_Remote_Jobs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-119">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="3adbd-120">Vanaf Power Shell 3,0 `Start-Job` kunnen exemplaren van aangepaste taak typen worden gestart, zoals geplande taken.</span><span class="sxs-lookup"><span data-stu-id="3adbd-120">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="3adbd-121">`Start-Job`Zie de Help-documenten voor de functie type taak voor meer informatie over het gebruik van om taken met aangepaste typen te starten.</span><span class="sxs-lookup"><span data-stu-id="3adbd-121">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="3adbd-122">Vanaf Power shell 6,0 kunt u taken starten met de-ampersand ( `&` )-achtergrond operator.</span><span class="sxs-lookup"><span data-stu-id="3adbd-122">Beginning in PowerShell 6.0, you can start jobs using the ampersand (`&`) background operator.</span></span> <span data-ttu-id="3adbd-123">De functionaliteit van de operator achtergrond is vergelijkbaar met `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-123">The functionality of the background operator is similar to `Start-Job`.</span></span> <span data-ttu-id="3adbd-124">Met beide methoden voor het starten van een taak maakt u een **PSRemotingJob** -taak object.</span><span class="sxs-lookup"><span data-stu-id="3adbd-124">Both methods to start a job create a **PSRemotingJob** job object.</span></span> <span data-ttu-id="3adbd-125">Zie about_Operators voor meer informatie over het gebruik van het `&` en [](./about/about_operators.md#background-operator-)-teken ().</span><span class="sxs-lookup"><span data-stu-id="3adbd-125">For more information about using the ampersand (`&`), see [about_Operators](./about/about_operators.md#background-operator-).</span></span>

<span data-ttu-id="3adbd-126">Power shell 7 heeft de **variabele workingdirectory** -para meter geïntroduceerd waarmee de oorspronkelijke werkmap van een achtergrond taak wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3adbd-126">PowerShell 7 introduced the **WorkingDirectory** parameter that specifies a background job's initial working directory.</span></span> <span data-ttu-id="3adbd-127">Als de para meter niet is opgegeven, wordt `Start-Job` standaard de actieve werkmap gebruikt van de aanroeper waarmee de taak is gestart.</span><span class="sxs-lookup"><span data-stu-id="3adbd-127">If the parameter isn't specified, `Start-Job` defaults to the current working directory of the caller that started the job.</span></span>

> [!NOTE]
> <span data-ttu-id="3adbd-128">Het maken van een out-of-process-achtergrond taak met `Start-Job` wordt niet ondersteund in het scenario waarin Power shell wordt gehost in andere toepassingen, zoals de Power shell-Azure functions.</span><span class="sxs-lookup"><span data-stu-id="3adbd-128">Creating an out-of-process background job with `Start-Job` is not supported in the scenario where PowerShell is being hosted in other applications, such as the PowerShell Azure Functions.</span></span>
>
> <span data-ttu-id="3adbd-129">Dit is standaard, omdat `Start-Job` het `pwsh` uitvoer bare bestand dat beschikbaar is voor het `$PSHOME` starten van een out-of-process-achtergrond taak, maar wanneer een toepassing Power shell host, rechtstreeks gebruikmaakt van de Power shell NuGet SDK-pakketten en deze niet heeft `pwsh` verzonden.</span><span class="sxs-lookup"><span data-stu-id="3adbd-129">This is by design because `Start-Job` depends on the `pwsh` executable to be available under `$PSHOME` to start an out-of-process background job, but when an application is hosting PowerShell, it's directly using the PowerShell NuGet SDK packages and won't have `pwsh` shipped along.</span></span>
>
> <span data-ttu-id="3adbd-130">De vervanging in dat scenario is `Start-ThreadJob` afkomstig uit de module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**.</span><span class="sxs-lookup"><span data-stu-id="3adbd-130">The substitute in that scenario is `Start-ThreadJob` from the module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**.</span></span>

## <span data-ttu-id="3adbd-131">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3adbd-131">EXAMPLES</span></span>

### <span data-ttu-id="3adbd-132">Voor beeld 1: een achtergrond taak starten</span><span class="sxs-lookup"><span data-stu-id="3adbd-132">Example 1: Start a background job</span></span>

<span data-ttu-id="3adbd-133">In dit voor beeld wordt een achtergrond taak gestart die wordt uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3adbd-133">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

<span data-ttu-id="3adbd-134">`Start-Job` maakt gebruik van de para meter **script Block** om te worden uitgevoerd `Get-Process` als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="3adbd-134">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="3adbd-135">De para meter **name** geeft aan dat Power shell-processen moeten worden gevonden `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-135">The **Name** parameter specifies to find PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="3adbd-136">De taak informatie wordt weer gegeven en Power shell keert terug naar een prompt wanneer de taak op de achtergrond wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-136">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="3adbd-137">Gebruik de cmdlet om de uitvoer van de taak weer te geven `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-137">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="3adbd-138">Bijvoorbeeld `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="3adbd-138">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="3adbd-139">Voor beeld 2: de operator achtergrond gebruiken om een achtergrond taak te starten</span><span class="sxs-lookup"><span data-stu-id="3adbd-139">Example 2: Use the background operator to start a background job</span></span>

<span data-ttu-id="3adbd-140">In dit voor beeld wordt de ampersand ( `&` )-achtergrond operator gebruikt om een achtergrond taak op de lokale computer te starten.</span><span class="sxs-lookup"><span data-stu-id="3adbd-140">This example uses the ampersand (`&`) background operator to start a background job on the local computer.</span></span> <span data-ttu-id="3adbd-141">De taak krijgt hetzelfde resultaat als `Start-Job` in voor beeld 1.</span><span class="sxs-lookup"><span data-stu-id="3adbd-141">The job gets the same result as `Start-Job` in Example 1.</span></span>

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

<span data-ttu-id="3adbd-142">`Get-Process` maakt gebruik van de para meter **name** voor het opgeven van Power shell-processen `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-142">`Get-Process` uses the **Name** parameter to specify PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="3adbd-143">Met het ampersand ( `&` ) wordt de opdracht als achtergrond taak uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-143">The ampersand (`&`) runs the command as a background job.</span></span> <span data-ttu-id="3adbd-144">De taak informatie wordt weer gegeven en Power shell keert terug naar een prompt wanneer de taak op de achtergrond wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-144">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="3adbd-145">Gebruik de cmdlet om de uitvoer van de taak weer te geven `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-145">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="3adbd-146">Bijvoorbeeld `Receive-Job -Id 5`.</span><span class="sxs-lookup"><span data-stu-id="3adbd-146">For example, `Receive-Job -Id 5`.</span></span>

### <span data-ttu-id="3adbd-147">Voor beeld 3: een taak starten met Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="3adbd-147">Example 3: Start a job using Invoke-Command</span></span>

<span data-ttu-id="3adbd-148">In dit voor beeld wordt een taak op meerdere computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-148">This example runs a job on multiple computers.</span></span> <span data-ttu-id="3adbd-149">De taak wordt opgeslagen in een variabele en wordt uitgevoerd met behulp van de naam van de variabele op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="3adbd-149">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="3adbd-150">Een taak die gebruikmaakt `Invoke-Command` van wordt gemaakt en opgeslagen in de `$jobWRM` variabele.</span><span class="sxs-lookup"><span data-stu-id="3adbd-150">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="3adbd-151">`Invoke-Command` maakt gebruik van de para meter **ComputerName** om de computers op te geven waarop de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-151">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="3adbd-152">`Get-Content` Hiermee worden de server namen opgehaald uit het `C:\Servers.txt` bestand.</span><span class="sxs-lookup"><span data-stu-id="3adbd-152">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="3adbd-153">De **script Block** para meter geeft u een opdracht op waarmee `Get-Service` de **WinRM** -service wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="3adbd-153">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="3adbd-154">De **JobName** para meter geeft een beschrijvende naam voor de taak, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="3adbd-154">The **JobName** parameter specifies a friendly name for the job, **WinRM**.</span></span> <span data-ttu-id="3adbd-155">De para meter **ThrottleLimit** beperkt het aantal gelijktijdige opdrachten tot 16.</span><span class="sxs-lookup"><span data-stu-id="3adbd-155">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="3adbd-156">Met de para meter **AsJob** wordt een achtergrond taak gestart die de opdracht uitvoert op de-servers.</span><span class="sxs-lookup"><span data-stu-id="3adbd-156">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="3adbd-157">Voor beeld 4: taak gegevens ophalen</span><span class="sxs-lookup"><span data-stu-id="3adbd-157">Example 4: Get job information</span></span>

<span data-ttu-id="3adbd-158">In dit voor beeld wordt informatie over een taak opgehaald en worden de resultaten weer gegeven van een voltooide taak die is uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3adbd-158">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

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

<span data-ttu-id="3adbd-159">`Start-Job` maakt gebruik van de para meter **script Block** om een opdracht uit te voeren die opgeeft `Get-WinEvent` om het **systeem** logboek op te halen.</span><span class="sxs-lookup"><span data-stu-id="3adbd-159">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="3adbd-160">De **referentie** parameter geeft een domein gebruikers account op dat is gemachtigd om de taak uit te voeren op de computer.</span><span class="sxs-lookup"><span data-stu-id="3adbd-160">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="3adbd-161">Het taak object wordt opgeslagen in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="3adbd-161">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="3adbd-162">Het object in de `$j` variabele wordt naar beneden verzonden in de pijp lijn `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-162">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="3adbd-163">De **eigenschap** para meter geeft een asterisk ( `*` ) op om alle eigenschappen van het taak object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3adbd-163">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="3adbd-164">Voor beeld 5: een script uitvoeren als een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="3adbd-164">Example 5: Run a script as a background job</span></span>

<span data-ttu-id="3adbd-165">In dit voor beeld wordt een script op de lokale computer uitgevoerd als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="3adbd-165">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="3adbd-166">`Start-Job` gebruikt de **filepath** -para meter om een script bestand op te geven dat is opgeslagen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3adbd-166">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="3adbd-167">Voor beeld 6: een proces met een achtergrond taak verkrijgen</span><span class="sxs-lookup"><span data-stu-id="3adbd-167">Example 6: Get a process using a background job</span></span>

<span data-ttu-id="3adbd-168">In dit voor beeld wordt een achtergrond taak gebruikt om een opgegeven proces op naam op te halen.</span><span class="sxs-lookup"><span data-stu-id="3adbd-168">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="3adbd-169">`Start-Job` maakt gebruik van de para meter **name** om een beschrijvende taak naam op te geven, **PShellJob**.</span><span class="sxs-lookup"><span data-stu-id="3adbd-169">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob**.</span></span> <span data-ttu-id="3adbd-170">De para meter **script Block** geeft `Get-Process` aan dat er processen worden opgehaald met de naam **Power shell**.</span><span class="sxs-lookup"><span data-stu-id="3adbd-170">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell**.</span></span>

### <span data-ttu-id="3adbd-171">Voor beeld 7: gegevens verzamelen en opslaan met behulp van een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="3adbd-171">Example 7: Collect and save data by using a background job</span></span>

<span data-ttu-id="3adbd-172">In dit voor beeld wordt een taak gestart die een grote hoeveelheid kaart gegevens verzamelt en vervolgens opslaat in een `.tif` bestand.</span><span class="sxs-lookup"><span data-stu-id="3adbd-172">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif }
```

<span data-ttu-id="3adbd-173">`Start-Job` maakt gebruik van de para meter **name** om een beschrijvende taak naam op te geven, **GetMappingFiles**.</span><span class="sxs-lookup"><span data-stu-id="3adbd-173">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles**.</span></span> <span data-ttu-id="3adbd-174">De para meter **InitializationScript** voert een script blok uit waarmee de **MapFunctions** -module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-174">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="3adbd-175">De para meter **script Block** wordt uitgevoerd `Get-Map` en `Set-Content` de gegevens worden opgeslagen op de locatie die is opgegeven door de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="3adbd-175">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span>

### <span data-ttu-id="3adbd-176">Voor beeld 8: invoer door geven aan een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="3adbd-176">Example 8: Pass input to a background job</span></span>

<span data-ttu-id="3adbd-177">In dit voor beeld wordt de `$input` Automatische variabele gebruikt voor het verwerken van een invoer object.</span><span class="sxs-lookup"><span data-stu-id="3adbd-177">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="3adbd-178">Gebruiken `Receive-Job` om de uitvoer van de taak weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3adbd-178">Use `Receive-Job` to view the job's output.</span></span>

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

<span data-ttu-id="3adbd-179">`Start-Job` maakt gebruik van de para meter **script Block** om te worden uitgevoerd `Get-Content` met de `$input` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="3adbd-179">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="3adbd-180">De `$input` variabele haalt objecten op uit de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="3adbd-180">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="3adbd-181">`Receive-Job` maakt gebruik van de para meter **name** om de taak op te geven en de resultaten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3adbd-181">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="3adbd-182">De **Keep** -para meter slaat de taak uitvoer op zodat deze weer kan worden weer gegeven tijdens de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-182">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="3adbd-183">Voor beeld 9: de werkmap instellen voor een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="3adbd-183">Example 9: Set the working directory for a background job</span></span>

<span data-ttu-id="3adbd-184">Met de **variabele workingdirectory** kunt u een alternatieve map opgeven voor een taak van waaruit u scripts of geopende bestanden kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="3adbd-184">The **WorkingDirectory** allows you to specify an alternate directory for a job from which you can run scripts or open files.</span></span> <span data-ttu-id="3adbd-185">In dit voor beeld wordt met de achtergrond taak een werkmap opgegeven die afwijkt van de huidige maplocatie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-185">In this example, the background job specifies a working directory that's different than the current directory location.</span></span>

```
PS C:\Test> Start-Job -WorkingDirectory C:\Test\Scripts { $PWD } | Receive-Job -AutoRemoveJob -Wait

Path
----
C:\Test\Scripts
```

<span data-ttu-id="3adbd-186">In dit voor beeld is de huidige werkmap `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-186">This example's current working directory is `C:\Test`.</span></span> <span data-ttu-id="3adbd-187">`Start-Job` maakt gebruik van de para meter **variabele workingdirectory** om de werkmap van de taak op te geven.</span><span class="sxs-lookup"><span data-stu-id="3adbd-187">`Start-Job` uses the **WorkingDirectory** parameter to specify the job's working directory.</span></span> <span data-ttu-id="3adbd-188">De para meter **script Block** maakt gebruik `$PWD` van om de werkmap van de taak weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3adbd-188">The **ScriptBlock** parameter uses `$PWD` to display the job's working directory.</span></span> <span data-ttu-id="3adbd-189">`Receive-Job` Hiermee wordt de uitvoer van de achtergrond taak weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3adbd-189">`Receive-Job` displays the background job's output.</span></span>
<span data-ttu-id="3adbd-190">**AutoRemoveJob** verwijdert de taak en **wacht** op de opdracht prompt totdat alle resultaten zijn ontvangen.</span><span class="sxs-lookup"><span data-stu-id="3adbd-190">**AutoRemoveJob** deletes the job and **Wait** suppresses the command prompt until all results are received.</span></span>

### <span data-ttu-id="3adbd-191">Voor beeld 10: de para meter argument list gebruiken om een matrix op te geven</span><span class="sxs-lookup"><span data-stu-id="3adbd-191">Example 10: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="3adbd-192">In dit voor beeld wordt de para meter **argument List** gebruikt om een matrix met argumenten op te geven.</span><span class="sxs-lookup"><span data-stu-id="3adbd-192">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="3adbd-193">De matrix is een door komma's gescheiden lijst met proces namen.</span><span class="sxs-lookup"><span data-stu-id="3adbd-193">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="3adbd-194">De `Start-Job` cmdlet gebruikt de para meter **script Block** om een opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3adbd-194">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="3adbd-195">`Get-Process` maakt gebruik van de para meter **name** om de automatische variabele op te geven `$args` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-195">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="3adbd-196">De **argument List** para meter geeft de matrix van proces namen door aan `$args` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-196">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="3adbd-197">De proces namen Power shell, pwsh en Notepad zijn processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3adbd-197">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="3adbd-198">Gebruik de cmdlet om de uitvoer van de taak weer te geven `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-198">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="3adbd-199">Bijvoorbeeld `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="3adbd-199">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="3adbd-200">Voor beeld 11: taak uitvoeren in een Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="3adbd-200">Example 11: Run job in a Windows PowerShell 5.1</span></span>

<span data-ttu-id="3adbd-201">In dit voor beeld wordt de **PSVersion** -para meter met de waarde **5,1** gebruikt voor het uitvoeren van een taak in een Windows Power shell 5,1-sessie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-201">This example uses the **PSVersion** parameter with value **5.1** to run job in a Windows PowerShell 5.1 session.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Patch  PreReleaseLabel BuildLabel
-----  -----  -----  --------------- ----------
7      0      0      rc.1
```

```powershell
$job = Start-Job { $PSVersionTable.PSVersion } -PSVersion 5.1
Receive-Job $job
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  3383
```

## <span data-ttu-id="3adbd-202">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3adbd-202">PARAMETERS</span></span>

### <span data-ttu-id="3adbd-203">-Argument List</span><span class="sxs-lookup"><span data-stu-id="3adbd-203">-ArgumentList</span></span>

<span data-ttu-id="3adbd-204">Hiermee geeft u een matrix met argumenten, of parameter waarden, op voor het script dat is opgegeven met de para meter **filepath** of een opdracht die is opgegeven met de para meter **script Block** .</span><span class="sxs-lookup"><span data-stu-id="3adbd-204">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="3adbd-205">Argumenten moeten worden door gegeven aan **argument List** als een matrix argument met één dimensie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-205">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="3adbd-206">Bijvoorbeeld een lijst met door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="3adbd-206">For example, a comma-separated list.</span></span> <span data-ttu-id="3adbd-207">Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="3adbd-207">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3adbd-208">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="3adbd-208">-Authentication</span></span>

<span data-ttu-id="3adbd-209">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="3adbd-209">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="3adbd-210">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="3adbd-210">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="3adbd-211">Standaard</span><span class="sxs-lookup"><span data-stu-id="3adbd-211">Default</span></span>
- <span data-ttu-id="3adbd-212">Basic</span><span class="sxs-lookup"><span data-stu-id="3adbd-212">Basic</span></span>
- <span data-ttu-id="3adbd-213">CredSSP</span><span class="sxs-lookup"><span data-stu-id="3adbd-213">Credssp</span></span>
- <span data-ttu-id="3adbd-214">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="3adbd-214">Digest</span></span>
- <span data-ttu-id="3adbd-215">Kerberos</span><span class="sxs-lookup"><span data-stu-id="3adbd-215">Kerberos</span></span>
- <span data-ttu-id="3adbd-216">Negotiate</span><span class="sxs-lookup"><span data-stu-id="3adbd-216">Negotiate</span></span>
- <span data-ttu-id="3adbd-217">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="3adbd-217">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="3adbd-218">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="3adbd-218">The default value is Default.</span></span>

<span data-ttu-id="3adbd-219">CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="3adbd-219">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="3adbd-220">Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="3adbd-220">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="3adbd-221">De verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="3adbd-221">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="3adbd-222">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="3adbd-222">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="3adbd-223">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="3adbd-223">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3adbd-224">-Credential</span><span class="sxs-lookup"><span data-stu-id="3adbd-224">-Credential</span></span>

<span data-ttu-id="3adbd-225">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3adbd-225">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="3adbd-226">Als de para meter **Credential** niet is opgegeven, gebruikt de opdracht de referenties van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="3adbd-226">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="3adbd-227">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-227">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="3adbd-228">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="3adbd-228">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="3adbd-229">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="3adbd-229">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="3adbd-230">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="3adbd-230">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3adbd-231">-Definitie</span><span class="sxs-lookup"><span data-stu-id="3adbd-231">-DefinitionName</span></span>

<span data-ttu-id="3adbd-232">Hiermee geeft u de definitie naam op van de taak die met deze cmdlet wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="3adbd-232">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="3adbd-233">Gebruik deze para meter om aangepaste taak typen te starten die een definitie naam hebben, zoals geplande taken.</span><span class="sxs-lookup"><span data-stu-id="3adbd-233">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="3adbd-234">Wanneer u gebruikt `Start-Job` om een exemplaar van een geplande taak te starten, wordt de taak onmiddellijk gestart, ongeacht taak triggers of taak opties.</span><span class="sxs-lookup"><span data-stu-id="3adbd-234">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="3adbd-235">Het resulterende taak exemplaar is een geplande taak, maar wordt niet opgeslagen op schijf zoals geactiveerde geplande taken.</span><span class="sxs-lookup"><span data-stu-id="3adbd-235">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="3adbd-236">U kunt de para meter **argument List** niet gebruiken `Start-Job` om waarden op te geven voor para meters van scripts die worden uitgevoerd in een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="3adbd-236">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span>

<span data-ttu-id="3adbd-237">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3adbd-237">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3adbd-238">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="3adbd-238">-DefinitionPath</span></span>

<span data-ttu-id="3adbd-239">Hiermee geeft u het pad op van de definitie voor de taak die met deze cmdlet wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="3adbd-239">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="3adbd-240">Voer het definitie-pad in.</span><span class="sxs-lookup"><span data-stu-id="3adbd-240">Enter the definition path.</span></span> <span data-ttu-id="3adbd-241">De samen voeging van de waarden van de para meters **DefinitionPath** en **rijdefinitie** is het volledig gekwalificeerde pad van de taak definitie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-241">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="3adbd-242">Gebruik deze para meter om aangepaste taak typen met een definitie-pad te starten, zoals geplande taken.</span><span class="sxs-lookup"><span data-stu-id="3adbd-242">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="3adbd-243">Voor geplande taken is de waarde van de  para meter DefinitionPath `$home\AppData\Local\Windows\PowerShell\ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-243">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="3adbd-244">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3adbd-244">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3adbd-245">-FilePath</span><span class="sxs-lookup"><span data-stu-id="3adbd-245">-FilePath</span></span>

<span data-ttu-id="3adbd-246">Hiermee geeft u een lokaal script op dat `Start-Job` als achtergrond taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-246">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="3adbd-247">Voer het pad en de bestands naam van het script in of gebruik de pijp lijn om een scriptpad naar te verzenden `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-247">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="3adbd-248">Het script moet zich op de lokale computer of in een map bevindt waartoe de lokale computer toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="3adbd-248">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="3adbd-249">Wanneer u deze para meter gebruikt, wordt de inhoud van het opgegeven script bestand door Power shell naar een script blok geconverteerd en wordt het script blok als achtergrond taak uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-249">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

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

### <span data-ttu-id="3adbd-250">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="3adbd-250">-InitializationScript</span></span>

<span data-ttu-id="3adbd-251">Geeft opdrachten die worden uitgevoerd voordat de taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="3adbd-251">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="3adbd-252">Als u een script blok wilt maken, plaatst u de opdrachten in accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="3adbd-252">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="3adbd-253">Gebruik deze para meter om de sessie voor te bereiden waarin de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-253">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="3adbd-254">U kunt dit bijvoorbeeld gebruiken om functies, modules en modules toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-254">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3adbd-255">-Input object</span><span class="sxs-lookup"><span data-stu-id="3adbd-255">-InputObject</span></span>

<span data-ttu-id="3adbd-256">Hiermee geeft u de invoer aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3adbd-256">Specifies input to the command.</span></span> <span data-ttu-id="3adbd-257">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-257">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="3adbd-258">Gebruik in de waarde van de para meter **script Block** de `$input` Automatische variabele om de invoer objecten te vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="3adbd-258">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3adbd-259">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3adbd-259">-LiteralPath</span></span>

<span data-ttu-id="3adbd-260">Hiermee geeft u een lokaal script op dat met deze cmdlet als achtergrond taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-260">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="3adbd-261">Geef het pad van een script op de lokale computer op.</span><span class="sxs-lookup"><span data-stu-id="3adbd-261">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="3adbd-262">`Start-Job` gebruikt de waarde van de para meter **LiteralPath** precies zoals deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="3adbd-262">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="3adbd-263">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="3adbd-263">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="3adbd-264">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="3adbd-264">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="3adbd-265">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="3adbd-265">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3adbd-266">-Name</span><span class="sxs-lookup"><span data-stu-id="3adbd-266">-Name</span></span>

<span data-ttu-id="3adbd-267">Hiermee geeft u een beschrijvende naam op voor de nieuwe taak.</span><span class="sxs-lookup"><span data-stu-id="3adbd-267">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="3adbd-268">U kunt de naam gebruiken om de taak te identificeren in andere taak-cmdlets, zoals de- `Stop-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3adbd-268">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="3adbd-269">De standaard beschrijvende naam is `Job#` , waarbij `#` een rang nummer is dat voor elke taak wordt verhoogd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-269">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3adbd-270">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="3adbd-270">-PSVersion</span></span>

<span data-ttu-id="3adbd-271">Hiermee geeft u een versie van Power shell op die moet worden gebruikt voor het uitvoeren van de taak.</span><span class="sxs-lookup"><span data-stu-id="3adbd-271">Specifies a version of PowerShell to use for running the job.</span></span>
<span data-ttu-id="3adbd-272">Wanneer de waarde van **PSVersion** is **5,1** , wordt de taak uitgevoerd in een Windows Power shell 5,1-sessie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-272">When the value of **PSVersion** is **5.1** The job is run in a Windows PowerShell 5.1 session.</span></span>
<span data-ttu-id="3adbd-273">Voor elke andere waarde wordt de taak uitgevoerd met de huidige versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="3adbd-273">For any other value, the job is run using the current version of PowerShell.</span></span>

<span data-ttu-id="3adbd-274">Deze para meter is toegevoegd in Power shell 7 en werkt alleen in Windows.</span><span class="sxs-lookup"><span data-stu-id="3adbd-274">This parameter was added in PowerShell 7 and only works on Windows.</span></span>

```yaml
Type: System.Version
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3adbd-275">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="3adbd-275">-RunAs32</span></span>

<span data-ttu-id="3adbd-276">Vanaf Power shell 7 werkt de para meter **RunAs32** niet op 64-bits Power shell ( `pwsh` ).</span><span class="sxs-lookup"><span data-stu-id="3adbd-276">Beginning with PowerShell 7, the **RunAs32** parameter doesn't work on 64-bit PowerShell (`pwsh`).</span></span>
<span data-ttu-id="3adbd-277">Als **RunAs32** is opgegeven in 64-bits Power shell, wordt `Start-Job` een uitzonderings fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-277">If **RunAs32** is specified in 64-bit PowerShell, `Start-Job` throws a terminating exception error.</span></span>
<span data-ttu-id="3adbd-278">Als u een 32-bits Power shell ()-proces wilt starten `pwsh` met **RunAs32**, moet de 32-bits Power shell zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-278">To start a 32-bit PowerShell (`pwsh`) process with **RunAs32**, you need to have the 32-bit PowerShell installed.</span></span>

<span data-ttu-id="3adbd-279">In 32-bits Power shell zorgt **RunAs32** ervoor dat de taak wordt uitgevoerd in een 32-bits proces, zelfs op een 64-bits besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="3adbd-279">In 32-bit PowerShell, **RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="3adbd-280">In 64-bits versies van Windows 7 en Windows Server 2008 R2, wanneer de `Start-Job` opdracht de para meter **RunAs32** bevat, kunt u de para meter **Credential** niet gebruiken om de referenties van een andere gebruiker op te geven.</span><span class="sxs-lookup"><span data-stu-id="3adbd-280">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3adbd-281">-Script Block</span><span class="sxs-lookup"><span data-stu-id="3adbd-281">-ScriptBlock</span></span>

<span data-ttu-id="3adbd-282">Hiermee geeft u de opdrachten op die in de achtergrond taak moeten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3adbd-282">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="3adbd-283">Als u een script blok wilt maken, plaatst u de opdrachten in accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="3adbd-283">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="3adbd-284">Gebruik de `$input` Automatische variabele om toegang te krijgen tot de waarde van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="3adbd-284">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="3adbd-285">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="3adbd-285">This parameter is required.</span></span>

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

### <span data-ttu-id="3adbd-286">-Type</span><span class="sxs-lookup"><span data-stu-id="3adbd-286">-Type</span></span>

<span data-ttu-id="3adbd-287">Hiermee geeft u het aangepaste type op voor taken die worden gestart door `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-287">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="3adbd-288">Voer een aangepaste taak type naam in, zoals PSScheduledJob voor geplande taken of PSWorkflowJob voor werk stroom taken.</span><span class="sxs-lookup"><span data-stu-id="3adbd-288">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="3adbd-289">Deze para meter is niet geldig voor standaard achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="3adbd-289">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="3adbd-290">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3adbd-290">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3adbd-291">-Variabele workingdirectory</span><span class="sxs-lookup"><span data-stu-id="3adbd-291">-WorkingDirectory</span></span>

<span data-ttu-id="3adbd-292">Hiermee geeft u de oorspronkelijke werkmap van de achtergrond taak op.</span><span class="sxs-lookup"><span data-stu-id="3adbd-292">Specifies the initial working directory of the background job.</span></span> <span data-ttu-id="3adbd-293">Als de para meter niet is opgegeven, wordt de taak uitgevoerd vanaf de standaard locatie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-293">If the parameter isn't specified, the job runs from the default location.</span></span> <span data-ttu-id="3adbd-294">De standaard locatie is de huidige werkmap van de aanroeper die de taak heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="3adbd-294">The default location is the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="3adbd-295">Deze para meter is geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="3adbd-295">This parameter was introduced in PowerShell 7.</span></span>

 ```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $HOME on Unix (macOS, Linux) and $HOME\Documents on Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3adbd-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3adbd-296">CommonParameters</span></span>

<span data-ttu-id="3adbd-297">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3adbd-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3adbd-298">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3adbd-299">INVOER</span><span class="sxs-lookup"><span data-stu-id="3adbd-299">INPUTS</span></span>

### <span data-ttu-id="3adbd-300">System. String</span><span class="sxs-lookup"><span data-stu-id="3adbd-300">System.String</span></span>

<span data-ttu-id="3adbd-301">U kunt de pijp lijn gebruiken om een object met de **naam** -eigenschap naar de para meter **name** te verzenden.</span><span class="sxs-lookup"><span data-stu-id="3adbd-301">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="3adbd-302">U kunt bijvoorbeeld een **file info** -object uitlijnen van `Get-ChildItem` tot `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="3adbd-302">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="3adbd-303">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3adbd-303">OUTPUTS</span></span>

### <span data-ttu-id="3adbd-304">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="3adbd-304">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="3adbd-305">`Start-Job` retourneert een **PSRemotingJob** -object dat de taak vertegenwoordigt die het heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="3adbd-305">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="3adbd-306">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3adbd-306">NOTES</span></span>

<span data-ttu-id="3adbd-307">Om op de achtergrond uit te voeren, `Start-Job` wordt uitgevoerd in een eigen sessie in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-307">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="3adbd-308">Wanneer u de `Invoke-Command` cmdlet gebruikt om een opdracht uit te voeren `Start-Job` in een sessie op een externe computer, `Start-Job` wordt uitgevoerd in een sessie in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="3adbd-308">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="3adbd-309">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3adbd-309">RELATED LINKS</span></span>

[<span data-ttu-id="3adbd-310">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="3adbd-310">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="3adbd-311">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="3adbd-311">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="3adbd-312">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="3adbd-312">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="3adbd-313">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="3adbd-313">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="3adbd-314">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="3adbd-314">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="3adbd-315">Get-job</span><span class="sxs-lookup"><span data-stu-id="3adbd-315">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="3adbd-316">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="3adbd-316">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="3adbd-317">Receive-job</span><span class="sxs-lookup"><span data-stu-id="3adbd-317">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="3adbd-318">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="3adbd-318">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="3adbd-319">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="3adbd-319">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="3adbd-320">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="3adbd-320">Wait-Job</span></span>](Wait-Job.md)
