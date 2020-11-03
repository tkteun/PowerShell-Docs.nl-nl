---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 7875419bed68251628b072a35d6c220e75b78c24
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250069"
---
# <span data-ttu-id="b1008-103">Start-Job</span><span class="sxs-lookup"><span data-stu-id="b1008-103">Start-Job</span></span>

## <span data-ttu-id="b1008-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b1008-104">SYNOPSIS</span></span>
<span data-ttu-id="b1008-105">Start een Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="b1008-105">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="b1008-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b1008-106">SYNTAX</span></span>

### <span data-ttu-id="b1008-107">Computer naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="b1008-107">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="b1008-108">Definitie</span><span class="sxs-lookup"><span data-stu-id="b1008-108">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [-WorkingDirectory <String>] [<CommonParameters>]
```

### <span data-ttu-id="b1008-109">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="b1008-109">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="b1008-110">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="b1008-110">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="b1008-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b1008-111">DESCRIPTION</span></span>

<span data-ttu-id="b1008-112">`Start-Job`Met de cmdlet wordt een Power shell-achtergrond taak gestart op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b1008-112">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="b1008-113">Met een Power shell-achtergrond taak wordt een opdracht uitgevoerd zonder interactie met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b1008-113">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="b1008-114">Wanneer u een achtergrond taak start, retourneert een taak object onmiddellijk, zelfs als de taak een lange tijd kost om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="b1008-114">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="b1008-115">U kunt zonder onderbreking in de sessie blijven werken terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-115">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="b1008-116">Het taak object bevat nuttige informatie over de taak, maar bevat geen taak resultaten.</span><span class="sxs-lookup"><span data-stu-id="b1008-116">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="b1008-117">Wanneer de taak is voltooid, gebruikt `Receive-Job` u de cmdlet om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="b1008-117">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="b1008-118">Zie [about_Jobs](./About/about_Jobs.md)voor meer informatie over achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="b1008-118">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="b1008-119">Als u een achtergrond taak wilt uitvoeren op een externe computer, gebruikt u de para meter **AsJob** die beschikbaar is in veel cmdlets of gebruikt `Invoke-Command` u de cmdlet om een opdracht uit te voeren `Start-Job` op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b1008-119">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="b1008-120">Zie [about_Remote_Jobs](./About/about_Remote_Jobs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b1008-120">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="b1008-121">Vanaf Power Shell 3,0 `Start-Job` kunnen exemplaren van aangepaste taak typen worden gestart, zoals geplande taken.</span><span class="sxs-lookup"><span data-stu-id="b1008-121">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="b1008-122">`Start-Job`Zie de Help-documenten voor de functie type taak voor meer informatie over het gebruik van om taken met aangepaste typen te starten.</span><span class="sxs-lookup"><span data-stu-id="b1008-122">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="b1008-123">Vanaf Power shell 6,0 kunt u taken starten met de-ampersand ( `&` )-achtergrond operator.</span><span class="sxs-lookup"><span data-stu-id="b1008-123">Beginning in PowerShell 6.0, you can start jobs using the ampersand (`&`) background operator.</span></span> <span data-ttu-id="b1008-124">De functionaliteit van de operator achtergrond is vergelijkbaar met `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="b1008-124">The functionality of the background operator is similar to `Start-Job`.</span></span> <span data-ttu-id="b1008-125">Met beide methoden voor het starten van een taak maakt u een **PSRemotingJob** -taak object.</span><span class="sxs-lookup"><span data-stu-id="b1008-125">Both methods to start a job create a **PSRemotingJob** job object.</span></span> <span data-ttu-id="b1008-126">Zie about_Operators voor meer informatie over het gebruik van het `&` en [about_Operators](./about/about_operators.md#background-operator-)-teken ().</span><span class="sxs-lookup"><span data-stu-id="b1008-126">For more information about using the ampersand (`&`), see [about_Operators](./about/about_operators.md#background-operator-).</span></span>

<span data-ttu-id="b1008-127">Power shell 7 heeft de **variabele workingdirectory** -para meter geïntroduceerd waarmee de oorspronkelijke werkmap van een achtergrond taak wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b1008-127">PowerShell 7 introduced the **WorkingDirectory** parameter that specifies a background job's initial working directory.</span></span> <span data-ttu-id="b1008-128">Als de para meter niet is opgegeven, wordt `Start-Job` standaard de actieve werkmap gebruikt van de aanroeper waarmee de taak is gestart.</span><span class="sxs-lookup"><span data-stu-id="b1008-128">If the parameter isn't specified, `Start-Job` defaults to the current working directory of the caller that started the job.</span></span>

> [!NOTE]
> <span data-ttu-id="b1008-129">Het maken van een out-of-process-achtergrond taak met `Start-Job` wordt niet ondersteund in het scenario waarin Power shell wordt gehost in andere toepassingen, zoals de Power shell-Azure functions.</span><span class="sxs-lookup"><span data-stu-id="b1008-129">Creating an out-of-process background job with `Start-Job` is not supported in the scenario where PowerShell is being hosted in other applications, such as the PowerShell Azure Functions.</span></span>
>
> <span data-ttu-id="b1008-130">Dit is standaard, omdat `Start-Job` het `pwsh` uitvoer bare bestand dat beschikbaar is voor het `$PSHOME` starten van een out-of-process-achtergrond taak, maar wanneer een toepassing Power shell host, rechtstreeks gebruikmaakt van de Power shell NuGet SDK-pakketten en deze niet heeft `pwsh` verzonden.</span><span class="sxs-lookup"><span data-stu-id="b1008-130">This is by design because `Start-Job` depends on the `pwsh` executable to be available under `$PSHOME` to start an out-of-process background job, but when an application is hosting PowerShell, it's directly using the PowerShell NuGet SDK packages and won't have `pwsh` shipped along.</span></span>
>
> <span data-ttu-id="b1008-131">De vervanging in dat scenario is `Start-ThreadJob` afkomstig uit de module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**.</span><span class="sxs-lookup"><span data-stu-id="b1008-131">The substitute in that scenario is `Start-ThreadJob` from the module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**.</span></span>

## <span data-ttu-id="b1008-132">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b1008-132">EXAMPLES</span></span>

### <span data-ttu-id="b1008-133">Voor beeld 1: een achtergrond taak starten</span><span class="sxs-lookup"><span data-stu-id="b1008-133">Example 1: Start a background job</span></span>

<span data-ttu-id="b1008-134">In dit voor beeld wordt een achtergrond taak gestart die wordt uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b1008-134">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

<span data-ttu-id="b1008-135">`Start-Job` maakt gebruik van de para meter **script Block** om te worden uitgevoerd `Get-Process` als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="b1008-135">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="b1008-136">De para meter **name** geeft aan dat Power shell-processen moeten worden gevonden `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="b1008-136">The **Name** parameter specifies to find PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="b1008-137">De taak informatie wordt weer gegeven en Power shell keert terug naar een prompt wanneer de taak op de achtergrond wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-137">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="b1008-138">Gebruik de cmdlet om de uitvoer van de taak weer te geven `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="b1008-138">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="b1008-139">Bijvoorbeeld `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="b1008-139">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="b1008-140">Voor beeld 2: de operator achtergrond gebruiken om een achtergrond taak te starten</span><span class="sxs-lookup"><span data-stu-id="b1008-140">Example 2: Use the background operator to start a background job</span></span>

<span data-ttu-id="b1008-141">In dit voor beeld wordt de ampersand ( `&` )-achtergrond operator gebruikt om een achtergrond taak op de lokale computer te starten.</span><span class="sxs-lookup"><span data-stu-id="b1008-141">This example uses the ampersand (`&`) background operator to start a background job on the local computer.</span></span> <span data-ttu-id="b1008-142">De taak krijgt hetzelfde resultaat als `Start-Job` in voor beeld 1.</span><span class="sxs-lookup"><span data-stu-id="b1008-142">The job gets the same result as `Start-Job` in Example 1.</span></span>

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

<span data-ttu-id="b1008-143">`Get-Process` maakt gebruik van de para meter **name** voor het opgeven van Power shell-processen `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="b1008-143">`Get-Process` uses the **Name** parameter to specify PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="b1008-144">Met het ampersand ( `&` ) wordt de opdracht als achtergrond taak uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-144">The ampersand (`&`) runs the command as a background job.</span></span> <span data-ttu-id="b1008-145">De taak informatie wordt weer gegeven en Power shell keert terug naar een prompt wanneer de taak op de achtergrond wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-145">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="b1008-146">Gebruik de cmdlet om de uitvoer van de taak weer te geven `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="b1008-146">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="b1008-147">Bijvoorbeeld `Receive-Job -Id 5`.</span><span class="sxs-lookup"><span data-stu-id="b1008-147">For example, `Receive-Job -Id 5`.</span></span>

### <span data-ttu-id="b1008-148">Voor beeld 3: een taak starten met Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="b1008-148">Example 3: Start a job using Invoke-Command</span></span>

<span data-ttu-id="b1008-149">In dit voor beeld wordt een taak op meerdere computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-149">This example runs a job on multiple computers.</span></span> <span data-ttu-id="b1008-150">De taak wordt opgeslagen in een variabele en wordt uitgevoerd met behulp van de naam van de variabele op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="b1008-150">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="b1008-151">Een taak die gebruikmaakt `Invoke-Command` van wordt gemaakt en opgeslagen in de `$jobWRM` variabele.</span><span class="sxs-lookup"><span data-stu-id="b1008-151">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="b1008-152">`Invoke-Command` maakt gebruik van de para meter **ComputerName** om de computers op te geven waarop de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-152">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="b1008-153">`Get-Content` Hiermee worden de server namen opgehaald uit het `C:\Servers.txt` bestand.</span><span class="sxs-lookup"><span data-stu-id="b1008-153">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="b1008-154">De **script Block** para meter geeft u een opdracht op waarmee `Get-Service` de **WinRM** -service wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b1008-154">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="b1008-155">De **JobName** para meter geeft een beschrijvende naam voor de taak, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="b1008-155">The **JobName** parameter specifies a friendly name for the job, **WinRM**.</span></span> <span data-ttu-id="b1008-156">De para meter **ThrottleLimit** beperkt het aantal gelijktijdige opdrachten tot 16.</span><span class="sxs-lookup"><span data-stu-id="b1008-156">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="b1008-157">Met de para meter **AsJob** wordt een achtergrond taak gestart die de opdracht uitvoert op de-servers.</span><span class="sxs-lookup"><span data-stu-id="b1008-157">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="b1008-158">Voor beeld 4: taak gegevens ophalen</span><span class="sxs-lookup"><span data-stu-id="b1008-158">Example 4: Get job information</span></span>

<span data-ttu-id="b1008-159">In dit voor beeld wordt informatie over een taak opgehaald en worden de resultaten weer gegeven van een voltooide taak die is uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b1008-159">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

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

<span data-ttu-id="b1008-160">`Start-Job` maakt gebruik van de para meter **script Block** om een opdracht uit te voeren die opgeeft `Get-WinEvent` om het **systeem** logboek op te halen.</span><span class="sxs-lookup"><span data-stu-id="b1008-160">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="b1008-161">De **referentie** parameter geeft een domein gebruikers account op dat is gemachtigd om de taak uit te voeren op de computer.</span><span class="sxs-lookup"><span data-stu-id="b1008-161">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="b1008-162">Het taak object wordt opgeslagen in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="b1008-162">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="b1008-163">Het object in de `$j` variabele wordt naar beneden verzonden in de pijp lijn `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="b1008-163">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="b1008-164">De **eigenschap** para meter geeft een asterisk ( `*` ) op om alle eigenschappen van het taak object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b1008-164">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="b1008-165">Voor beeld 5: een script uitvoeren als een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="b1008-165">Example 5: Run a script as a background job</span></span>

<span data-ttu-id="b1008-166">In dit voor beeld wordt een script op de lokale computer uitgevoerd als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="b1008-166">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="b1008-167">`Start-Job` gebruikt de **filepath** -para meter om een script bestand op te geven dat is opgeslagen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b1008-167">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="b1008-168">Voor beeld 6: een proces met een achtergrond taak verkrijgen</span><span class="sxs-lookup"><span data-stu-id="b1008-168">Example 6: Get a process using a background job</span></span>

<span data-ttu-id="b1008-169">In dit voor beeld wordt een achtergrond taak gebruikt om een opgegeven proces op naam op te halen.</span><span class="sxs-lookup"><span data-stu-id="b1008-169">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="b1008-170">`Start-Job` maakt gebruik van de para meter **name** om een beschrijvende taak naam op te geven, **PShellJob**.</span><span class="sxs-lookup"><span data-stu-id="b1008-170">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob**.</span></span> <span data-ttu-id="b1008-171">De para meter **script Block** geeft `Get-Process` aan dat er processen worden opgehaald met de naam **Power shell**.</span><span class="sxs-lookup"><span data-stu-id="b1008-171">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell**.</span></span>

### <span data-ttu-id="b1008-172">Voor beeld 7: gegevens verzamelen en opslaan met behulp van een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="b1008-172">Example 7: Collect and save data by using a background job</span></span>

<span data-ttu-id="b1008-173">In dit voor beeld wordt een taak gestart die een grote hoeveelheid kaart gegevens verzamelt en vervolgens opslaat in een `.tif` bestand.</span><span class="sxs-lookup"><span data-stu-id="b1008-173">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif }
```

<span data-ttu-id="b1008-174">`Start-Job` maakt gebruik van de para meter **name** om een beschrijvende taak naam op te geven, **GetMappingFiles**.</span><span class="sxs-lookup"><span data-stu-id="b1008-174">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles**.</span></span> <span data-ttu-id="b1008-175">De para meter **InitializationScript** voert een script blok uit waarmee de **MapFunctions** -module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-175">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="b1008-176">De para meter **script Block** wordt uitgevoerd `Get-Map` en `Set-Content` de gegevens worden opgeslagen op de locatie die is opgegeven door de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="b1008-176">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span>

### <span data-ttu-id="b1008-177">Voor beeld 8: invoer door geven aan een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="b1008-177">Example 8: Pass input to a background job</span></span>

<span data-ttu-id="b1008-178">In dit voor beeld wordt de `$input` Automatische variabele gebruikt voor het verwerken van een invoer object.</span><span class="sxs-lookup"><span data-stu-id="b1008-178">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="b1008-179">Gebruiken `Receive-Job` om de uitvoer van de taak weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b1008-179">Use `Receive-Job` to view the job's output.</span></span>

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

<span data-ttu-id="b1008-180">`Start-Job` maakt gebruik van de para meter **script Block** om te worden uitgevoerd `Get-Content` met de `$input` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="b1008-180">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="b1008-181">De `$input` variabele haalt objecten op uit de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="b1008-181">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="b1008-182">`Receive-Job` maakt gebruik van de para meter **name** om de taak op te geven en de resultaten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b1008-182">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="b1008-183">De **Keep** -para meter slaat de taak uitvoer op zodat deze weer kan worden weer gegeven tijdens de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="b1008-183">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="b1008-184">Voor beeld 9: de werkmap instellen voor een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="b1008-184">Example 9: Set the working directory for a background job</span></span>

<span data-ttu-id="b1008-185">Met de **variabele workingdirectory** kunt u een alternatieve map opgeven voor een taak van waaruit u scripts of geopende bestanden kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b1008-185">The **WorkingDirectory** allows you to specify an alternate directory for a job from which you can run scripts or open files.</span></span> <span data-ttu-id="b1008-186">In dit voor beeld wordt met de achtergrond taak een werkmap opgegeven die afwijkt van de huidige maplocatie.</span><span class="sxs-lookup"><span data-stu-id="b1008-186">In this example, the background job specifies a working directory that's different than the current directory location.</span></span>

```
PS C:\Test> Start-Job -WorkingDirectory C:\Test\Scripts { $PWD } | Receive-Job -AutoRemoveJob -Wait

Path
----
C:\Test\Scripts
```

<span data-ttu-id="b1008-187">In dit voor beeld is de huidige werkmap `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="b1008-187">This example's current working directory is `C:\Test`.</span></span> <span data-ttu-id="b1008-188">`Start-Job` maakt gebruik van de para meter **variabele workingdirectory** om de werkmap van de taak op te geven.</span><span class="sxs-lookup"><span data-stu-id="b1008-188">`Start-Job` uses the **WorkingDirectory** parameter to specify the job's working directory.</span></span> <span data-ttu-id="b1008-189">De para meter **script Block** maakt gebruik `$PWD` van om de werkmap van de taak weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b1008-189">The **ScriptBlock** parameter uses `$PWD` to display the job's working directory.</span></span> <span data-ttu-id="b1008-190">`Receive-Job` Hiermee wordt de uitvoer van de achtergrond taak weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b1008-190">`Receive-Job` displays the background job's output.</span></span>
<span data-ttu-id="b1008-191">**AutoRemoveJob** verwijdert de taak en **wacht** op de opdracht prompt totdat alle resultaten zijn ontvangen.</span><span class="sxs-lookup"><span data-stu-id="b1008-191">**AutoRemoveJob** deletes the job and **Wait** suppresses the command prompt until all results are received.</span></span>

### <span data-ttu-id="b1008-192">Voor beeld 10: de para meter argument list gebruiken om een matrix op te geven</span><span class="sxs-lookup"><span data-stu-id="b1008-192">Example 10: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="b1008-193">In dit voor beeld wordt de para meter **argument List** gebruikt om een matrix met argumenten op te geven.</span><span class="sxs-lookup"><span data-stu-id="b1008-193">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="b1008-194">De matrix is een door komma's gescheiden lijst met proces namen.</span><span class="sxs-lookup"><span data-stu-id="b1008-194">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="b1008-195">De `Start-Job` cmdlet gebruikt de para meter **script Block** om een opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b1008-195">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="b1008-196">`Get-Process` maakt gebruik van de para meter **name** om de automatische variabele op te geven `$args` .</span><span class="sxs-lookup"><span data-stu-id="b1008-196">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="b1008-197">De **argument List** para meter geeft de matrix van proces namen door aan `$args` .</span><span class="sxs-lookup"><span data-stu-id="b1008-197">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="b1008-198">De proces namen Power shell, pwsh en Notepad zijn processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b1008-198">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="b1008-199">Gebruik de cmdlet om de uitvoer van de taak weer te geven `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="b1008-199">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="b1008-200">Bijvoorbeeld `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="b1008-200">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="b1008-201">Voor beeld 11: taak uitvoeren in een Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="b1008-201">Example 11: Run job in a Windows PowerShell 5.1</span></span>

<span data-ttu-id="b1008-202">In dit voor beeld wordt de **PSVersion** -para meter met de waarde **5,1** gebruikt voor het uitvoeren van een taak in een Windows Power shell 5,1-sessie.</span><span class="sxs-lookup"><span data-stu-id="b1008-202">This example uses the **PSVersion** parameter with value **5.1** to run job in a Windows PowerShell 5.1 session.</span></span>

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

## <span data-ttu-id="b1008-203">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b1008-203">PARAMETERS</span></span>

### <span data-ttu-id="b1008-204">-Argument List</span><span class="sxs-lookup"><span data-stu-id="b1008-204">-ArgumentList</span></span>

<span data-ttu-id="b1008-205">Hiermee geeft u een matrix met argumenten, of parameter waarden, op voor het script dat is opgegeven met de para meter **filepath** of een opdracht die is opgegeven met de para meter **script Block** .</span><span class="sxs-lookup"><span data-stu-id="b1008-205">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="b1008-206">Argumenten moeten worden door gegeven aan **argument List** als een matrix argument met één dimensie.</span><span class="sxs-lookup"><span data-stu-id="b1008-206">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="b1008-207">Bijvoorbeeld een lijst met door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="b1008-207">For example, a comma-separated list.</span></span> <span data-ttu-id="b1008-208">Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="b1008-208">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="b1008-209">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="b1008-209">-Authentication</span></span>

<span data-ttu-id="b1008-210">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="b1008-210">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="b1008-211">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="b1008-211">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b1008-212">Standaard</span><span class="sxs-lookup"><span data-stu-id="b1008-212">Default</span></span>
- <span data-ttu-id="b1008-213">Basic</span><span class="sxs-lookup"><span data-stu-id="b1008-213">Basic</span></span>
- <span data-ttu-id="b1008-214">CredSSP</span><span class="sxs-lookup"><span data-stu-id="b1008-214">Credssp</span></span>
- <span data-ttu-id="b1008-215">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="b1008-215">Digest</span></span>
- <span data-ttu-id="b1008-216">Kerberos</span><span class="sxs-lookup"><span data-stu-id="b1008-216">Kerberos</span></span>
- <span data-ttu-id="b1008-217">Negotiate</span><span class="sxs-lookup"><span data-stu-id="b1008-217">Negotiate</span></span>
- <span data-ttu-id="b1008-218">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="b1008-218">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="b1008-219">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="b1008-219">The default value is Default.</span></span>

<span data-ttu-id="b1008-220">CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="b1008-220">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="b1008-221">Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="b1008-221">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="b1008-222">De verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="b1008-222">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="b1008-223">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="b1008-223">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="b1008-224">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="b1008-224">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="b1008-225">-Credential</span><span class="sxs-lookup"><span data-stu-id="b1008-225">-Credential</span></span>

<span data-ttu-id="b1008-226">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b1008-226">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="b1008-227">Als de para meter **Credential** niet is opgegeven, gebruikt de opdracht de referenties van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b1008-227">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="b1008-228">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="b1008-228">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="b1008-229">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="b1008-229">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="b1008-230">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="b1008-230">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="b1008-231">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="b1008-231">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="b1008-232">-Definitie</span><span class="sxs-lookup"><span data-stu-id="b1008-232">-DefinitionName</span></span>

<span data-ttu-id="b1008-233">Hiermee geeft u de definitie naam op van de taak die met deze cmdlet wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="b1008-233">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="b1008-234">Gebruik deze para meter om aangepaste taak typen te starten die een definitie naam hebben, zoals geplande taken.</span><span class="sxs-lookup"><span data-stu-id="b1008-234">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="b1008-235">Wanneer u gebruikt `Start-Job` om een exemplaar van een geplande taak te starten, wordt de taak onmiddellijk gestart, ongeacht taak triggers of taak opties.</span><span class="sxs-lookup"><span data-stu-id="b1008-235">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="b1008-236">Het resulterende taak exemplaar is een geplande taak, maar wordt niet opgeslagen op schijf zoals geactiveerde geplande taken.</span><span class="sxs-lookup"><span data-stu-id="b1008-236">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="b1008-237">U kunt de para meter **argument List** niet gebruiken `Start-Job` om waarden op te geven voor para meters van scripts die worden uitgevoerd in een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="b1008-237">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span>

<span data-ttu-id="b1008-238">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b1008-238">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="b1008-239">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="b1008-239">-DefinitionPath</span></span>

<span data-ttu-id="b1008-240">Hiermee geeft u het pad op van de definitie voor de taak die met deze cmdlet wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="b1008-240">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="b1008-241">Voer het definitie-pad in.</span><span class="sxs-lookup"><span data-stu-id="b1008-241">Enter the definition path.</span></span> <span data-ttu-id="b1008-242">De samen voeging van de waarden van de para meters **DefinitionPath** en **rijdefinitie** is het volledig gekwalificeerde pad van de taak definitie.</span><span class="sxs-lookup"><span data-stu-id="b1008-242">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="b1008-243">Gebruik deze para meter om aangepaste taak typen met een definitie-pad te starten, zoals geplande taken.</span><span class="sxs-lookup"><span data-stu-id="b1008-243">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="b1008-244">Voor geplande taken is de waarde van de **DefinitionPath** para meter DefinitionPath `$home\AppData\Local\Windows\PowerShell\ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="b1008-244">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="b1008-245">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b1008-245">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="b1008-246">-FilePath</span><span class="sxs-lookup"><span data-stu-id="b1008-246">-FilePath</span></span>

<span data-ttu-id="b1008-247">Hiermee geeft u een lokaal script op dat `Start-Job` als achtergrond taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-247">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="b1008-248">Voer het pad en de bestands naam van het script in of gebruik de pijp lijn om een scriptpad naar te verzenden `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="b1008-248">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="b1008-249">Het script moet zich op de lokale computer of in een map bevindt waartoe de lokale computer toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="b1008-249">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="b1008-250">Wanneer u deze para meter gebruikt, wordt de inhoud van het opgegeven script bestand door Power shell naar een script blok geconverteerd en wordt het script blok als achtergrond taak uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-250">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

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

### <span data-ttu-id="b1008-251">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="b1008-251">-InitializationScript</span></span>

<span data-ttu-id="b1008-252">Geeft opdrachten die worden uitgevoerd voordat de taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="b1008-252">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="b1008-253">Als u een script blok wilt maken, plaatst u de opdrachten in accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="b1008-253">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="b1008-254">Gebruik deze para meter om de sessie voor te bereiden waarin de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-254">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="b1008-255">U kunt dit bijvoorbeeld gebruiken om functies, modules en modules toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="b1008-255">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

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

### <span data-ttu-id="b1008-256">-Input object</span><span class="sxs-lookup"><span data-stu-id="b1008-256">-InputObject</span></span>

<span data-ttu-id="b1008-257">Hiermee geeft u de invoer aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="b1008-257">Specifies input to the command.</span></span> <span data-ttu-id="b1008-258">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-258">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="b1008-259">Gebruik in de waarde van de para meter **script Block** de `$input` Automatische variabele om de invoer objecten te vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="b1008-259">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

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

### <span data-ttu-id="b1008-260">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b1008-260">-LiteralPath</span></span>

<span data-ttu-id="b1008-261">Hiermee geeft u een lokaal script op dat met deze cmdlet als achtergrond taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-261">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="b1008-262">Geef het pad van een script op de lokale computer op.</span><span class="sxs-lookup"><span data-stu-id="b1008-262">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="b1008-263">`Start-Job` gebruikt de waarde van de para meter **LiteralPath** precies zoals deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="b1008-263">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="b1008-264">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="b1008-264">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="b1008-265">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="b1008-265">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b1008-266">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="b1008-266">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="b1008-267">-Name</span><span class="sxs-lookup"><span data-stu-id="b1008-267">-Name</span></span>

<span data-ttu-id="b1008-268">Hiermee geeft u een beschrijvende naam op voor de nieuwe taak.</span><span class="sxs-lookup"><span data-stu-id="b1008-268">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="b1008-269">U kunt de naam gebruiken om de taak te identificeren in andere taak-cmdlets, zoals de- `Stop-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b1008-269">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="b1008-270">De standaard beschrijvende naam is `Job#` , waarbij `#` een rang nummer is dat voor elke taak wordt verhoogd.</span><span class="sxs-lookup"><span data-stu-id="b1008-270">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

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

### <span data-ttu-id="b1008-271">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="b1008-271">-PSVersion</span></span>

<span data-ttu-id="b1008-272">Hiermee geeft u een versie van Power shell op die moet worden gebruikt voor het uitvoeren van de taak.</span><span class="sxs-lookup"><span data-stu-id="b1008-272">Specifies a version of PowerShell to use for running the job.</span></span>
<span data-ttu-id="b1008-273">Wanneer de waarde van **PSVersion** is **5,1** , wordt de taak uitgevoerd in een Windows Power shell 5,1-sessie.</span><span class="sxs-lookup"><span data-stu-id="b1008-273">When the value of **PSVersion** is **5.1** The job is run in a Windows PowerShell 5.1 session.</span></span>
<span data-ttu-id="b1008-274">Voor elke andere waarde wordt de taak uitgevoerd met de huidige versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="b1008-274">For any other value, the job is run using the current version of PowerShell.</span></span>

<span data-ttu-id="b1008-275">Deze para meter is toegevoegd in Power shell 7 en werkt alleen in Windows.</span><span class="sxs-lookup"><span data-stu-id="b1008-275">This parameter was added in PowerShell 7 and only works on Windows.</span></span>

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

### <span data-ttu-id="b1008-276">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="b1008-276">-RunAs32</span></span>

<span data-ttu-id="b1008-277">Vanaf Power shell 7 werkt de para meter **RunAs32** niet op 64-bits Power shell ( `pwsh` ).</span><span class="sxs-lookup"><span data-stu-id="b1008-277">Beginning with PowerShell 7, the **RunAs32** parameter doesn't work on 64-bit PowerShell (`pwsh`).</span></span>
<span data-ttu-id="b1008-278">Als **RunAs32** is opgegeven in 64-bits Power shell, wordt `Start-Job` een uitzonderings fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-278">If **RunAs32** is specified in 64-bit PowerShell, `Start-Job` throws a terminating exception error.</span></span>
<span data-ttu-id="b1008-279">Als u een 32-bits Power shell ()-proces wilt starten `pwsh` met **RunAs32** , moet de 32-bits Power shell zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-279">To start a 32-bit PowerShell (`pwsh`) process with **RunAs32** , you need to have the 32-bit PowerShell installed.</span></span>

<span data-ttu-id="b1008-280">In 32-bits Power shell zorgt **RunAs32** ervoor dat de taak wordt uitgevoerd in een 32-bits proces, zelfs op een 64-bits besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="b1008-280">In 32-bit PowerShell, **RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="b1008-281">In 64-bits versies van Windows 7 en Windows Server 2008 R2, wanneer de `Start-Job` opdracht de para meter **RunAs32** bevat, kunt u de para meter **Credential** niet gebruiken om de referenties van een andere gebruiker op te geven.</span><span class="sxs-lookup"><span data-stu-id="b1008-281">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

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

### <span data-ttu-id="b1008-282">-Script Block</span><span class="sxs-lookup"><span data-stu-id="b1008-282">-ScriptBlock</span></span>

<span data-ttu-id="b1008-283">Hiermee geeft u de opdrachten op die in de achtergrond taak moeten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1008-283">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="b1008-284">Als u een script blok wilt maken, plaatst u de opdrachten in accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="b1008-284">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="b1008-285">Gebruik de `$input` Automatische variabele om toegang te krijgen tot de waarde van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="b1008-285">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="b1008-286">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="b1008-286">This parameter is required.</span></span>

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

### <span data-ttu-id="b1008-287">-Type</span><span class="sxs-lookup"><span data-stu-id="b1008-287">-Type</span></span>

<span data-ttu-id="b1008-288">Hiermee geeft u het aangepaste type op voor taken die worden gestart door `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="b1008-288">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="b1008-289">Voer een aangepaste taak type naam in, zoals PSScheduledJob voor geplande taken of PSWorkflowJob voor werk stroom taken.</span><span class="sxs-lookup"><span data-stu-id="b1008-289">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="b1008-290">Deze para meter is niet geldig voor standaard achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="b1008-290">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="b1008-291">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b1008-291">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="b1008-292">-Variabele workingdirectory</span><span class="sxs-lookup"><span data-stu-id="b1008-292">-WorkingDirectory</span></span>

<span data-ttu-id="b1008-293">Hiermee geeft u de oorspronkelijke werkmap van de achtergrond taak op.</span><span class="sxs-lookup"><span data-stu-id="b1008-293">Specifies the initial working directory of the background job.</span></span> <span data-ttu-id="b1008-294">Als de para meter niet is opgegeven, wordt de taak uitgevoerd vanaf de standaard locatie.</span><span class="sxs-lookup"><span data-stu-id="b1008-294">If the parameter isn't specified, the job runs from the default location.</span></span> <span data-ttu-id="b1008-295">De standaard locatie is de huidige werkmap van de aanroeper die de taak heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="b1008-295">The default location is the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="b1008-296">Deze para meter is geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="b1008-296">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.String
Parameter Sets: All
Aliases:

Required: False
Position: Named
Default value: $HOME on Unix (macOS, Linux) and $HOME\Documents on Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1008-297">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b1008-297">CommonParameters</span></span>

<span data-ttu-id="b1008-298">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b1008-298">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b1008-299">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b1008-299">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b1008-300">INVOER</span><span class="sxs-lookup"><span data-stu-id="b1008-300">INPUTS</span></span>

### <span data-ttu-id="b1008-301">System. String</span><span class="sxs-lookup"><span data-stu-id="b1008-301">System.String</span></span>

<span data-ttu-id="b1008-302">U kunt de pijp lijn gebruiken om een object met de **naam** -eigenschap naar de para meter **name** te verzenden.</span><span class="sxs-lookup"><span data-stu-id="b1008-302">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="b1008-303">U kunt bijvoorbeeld een **file info** -object uitlijnen van `Get-ChildItem` tot `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="b1008-303">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="b1008-304">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b1008-304">OUTPUTS</span></span>

### <span data-ttu-id="b1008-305">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="b1008-305">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="b1008-306">`Start-Job` retourneert een **PSRemotingJob** -object dat de taak vertegenwoordigt die het heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="b1008-306">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="b1008-307">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b1008-307">NOTES</span></span>

<span data-ttu-id="b1008-308">Om op de achtergrond uit te voeren, `Start-Job` wordt uitgevoerd in een eigen sessie in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b1008-308">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="b1008-309">Wanneer u de `Invoke-Command` cmdlet gebruikt om een opdracht uit te voeren `Start-Job` in een sessie op een externe computer, `Start-Job` wordt uitgevoerd in een sessie in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="b1008-309">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="b1008-310">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b1008-310">RELATED LINKS</span></span>

[<span data-ttu-id="b1008-311">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="b1008-311">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="b1008-312">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="b1008-312">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="b1008-313">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="b1008-313">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="b1008-314">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="b1008-314">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="b1008-315">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="b1008-315">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="b1008-316">Get-job</span><span class="sxs-lookup"><span data-stu-id="b1008-316">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="b1008-317">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="b1008-317">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="b1008-318">Receive-job</span><span class="sxs-lookup"><span data-stu-id="b1008-318">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="b1008-319">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="b1008-319">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="b1008-320">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="b1008-320">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="b1008-321">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="b1008-321">Wait-Job</span></span>](Wait-Job.md)
