---
description: Bevat informatie over achtergrond taken op lokale en externe computers.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: cd6c633e9f409054b0ee89021de961c36d84ac3b
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/17/2020
ms.locfileid: "93253073"
---
# <a name="about-job-details"></a><span data-ttu-id="9f943-104">Over taak Details</span><span class="sxs-lookup"><span data-stu-id="9f943-104">About Job Details</span></span>

## <a name="short-description"></a><span data-ttu-id="9f943-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="9f943-105">Short description</span></span>
<span data-ttu-id="9f943-106">Bevat informatie over achtergrond taken op lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="9f943-106">Provides details about background jobs on local and remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="9f943-107">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="9f943-107">Detailed description</span></span>

<span data-ttu-id="9f943-108">In dit onderwerp wordt het concept van een achtergrond taak uitgelegd en vindt u technische informatie over de werking van achtergrond taken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="9f943-108">This topic explains the concept of a background job and provides technical information about how background jobs work in PowerShell.</span></span>

<span data-ttu-id="9f943-109">Dit onderwerp is een aanvulling op de onderwerpen [about_Jobs](about_Jobs.md), [about_Thread_Jobs](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs)en [about_Remote_Jobs](about_Remote_Jobs.md) .</span><span class="sxs-lookup"><span data-stu-id="9f943-109">This topic is a supplement to the [about_Jobs](about_Jobs.md), [about_Thread_Jobs](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs), and [about_Remote_Jobs](about_Remote_Jobs.md) topics.</span></span>

### <a name="about-background-jobs"></a><span data-ttu-id="9f943-110">Over achtergrond taken</span><span class="sxs-lookup"><span data-stu-id="9f943-110">About background jobs</span></span>

<span data-ttu-id="9f943-111">Met een achtergrond taak wordt een opdracht of expressie asynchroon uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9f943-111">A background job runs a command or expression asynchronously.</span></span> <span data-ttu-id="9f943-112">Er kan een cmdlet, een functie, een script of een andere op opdrachten gebaseerde taak worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9f943-112">It might run a cmdlet, a function, a script, or any other command-based task.</span></span> <span data-ttu-id="9f943-113">Het is ontworpen om opdrachten uit te voeren die lange tijd duren, maar u kunt deze gebruiken om elke opdracht op de achtergrond uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9f943-113">It is designed to run commands that take an extended period of time, but you can use it to run any command in the background.</span></span>

<span data-ttu-id="9f943-114">Wanneer een synchrone opdracht wordt uitgevoerd, wordt de Power shell-opdracht prompt onderdrukt totdat de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="9f943-114">When a synchronous command runs, the PowerShell command prompt is suppressed until the command is complete.</span></span> <span data-ttu-id="9f943-115">De Power shell-prompt wordt niet onderdrukt door een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="9f943-115">But a background job does not suppress the PowerShell prompt.</span></span> <span data-ttu-id="9f943-116">Een opdracht voor het starten van een achtergrond taak retourneert een taak object.</span><span class="sxs-lookup"><span data-stu-id="9f943-116">A command to start a background job returns a job object.</span></span>
<span data-ttu-id="9f943-117">De prompt wordt onmiddellijk geretourneerd, zodat u met andere taken kunt werken terwijl de achtergrond taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9f943-117">The prompt returns immediately so you can work on other tasks while the background job runs.</span></span>

<span data-ttu-id="9f943-118">Wanneer u echter een achtergrond taak start, worden de resultaten niet meteen opgehaald, zelfs niet als de taak zeer snel wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9f943-118">However, when you start a background job, you do not get the results immediately even if the job runs very quickly.</span></span> <span data-ttu-id="9f943-119">Het taak object dat wordt geretourneerd, bevat nuttige informatie over de taak, maar bevat geen taak resultaten.</span><span class="sxs-lookup"><span data-stu-id="9f943-119">The job object that is returned contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="9f943-120">U moet een afzonderlijke opdracht uitvoeren om de taak resultaten te krijgen.</span><span class="sxs-lookup"><span data-stu-id="9f943-120">You must run a separate command to get the job results.</span></span> <span data-ttu-id="9f943-121">U kunt ook opdrachten uitvoeren om de taak te stoppen, te wachten tot de taak is voltooid en de taak te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="9f943-121">You can also run commands to stop the job, to wait for the job to be completed, and to delete the job.</span></span>

<span data-ttu-id="9f943-122">Om de timing van een achtergrond taak onafhankelijk van andere opdrachten te maken, wordt elke achtergrond taak uitgevoerd in een eigen Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="9f943-122">To make the timing of a background job independent of other commands, each background job runs in its own PowerShell session.</span></span> <span data-ttu-id="9f943-123">Dit kan echter een tijdelijke verbinding zijn die alleen wordt gemaakt om de taak uit te voeren en vervolgens wordt vernietigd, of het kan een permanente **PSSession** zijn die u kunt gebruiken om verschillende gerelateerde taken of opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9f943-123">However, this can be a temporary connection that is created only to run the job and is then destroyed, or it can be a persistent **PSSession** that you can use to run several related jobs or commands.</span></span>

### <a name="using-the-job-cmdlets"></a><span data-ttu-id="9f943-124">De taak-cmdlets gebruiken</span><span class="sxs-lookup"><span data-stu-id="9f943-124">Using the job cmdlets</span></span>

<span data-ttu-id="9f943-125">Gebruik een `Start-Job` opdracht voor het starten van een achtergrond taak op een lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9f943-125">Use a `Start-Job` command to start a background job on a local computer.</span></span>
<span data-ttu-id="9f943-126">`Start-Job` retourneert een taak object.</span><span class="sxs-lookup"><span data-stu-id="9f943-126">`Start-Job` returns a job object.</span></span> <span data-ttu-id="9f943-127">U kunt ook objecten ophalen die de taken vertegenwoordigen die zijn gestart op de lokale computer met behulp van de- `Get-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f943-127">You can also get objects representing the jobs that were started on the local computer using the `Get-Job` cmdlet.</span></span>

<span data-ttu-id="9f943-128">Gebruik een opdracht om de taak resultaten te verkrijgen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="9f943-128">To get the job results, use a `Receive-Job` command.</span></span> <span data-ttu-id="9f943-129">Als de taak niet is voltooid, `Receive-Job` retourneert gedeeltelijke resultaten.</span><span class="sxs-lookup"><span data-stu-id="9f943-129">If the job is not complete, `Receive-Job` returns partial results.</span></span> <span data-ttu-id="9f943-130">U kunt de cmdlet ook gebruiken `Wait-Job` om de opdracht prompt te onderdrukken totdat een of alle taken die in de sessie zijn gestart, zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="9f943-130">You can also use the `Wait-Job` cmdlet to suppress the command prompt until one or all of the jobs that were started in the session are complete.</span></span>

<span data-ttu-id="9f943-131">Als u een achtergrond taak wilt stoppen, gebruikt u de `Stop-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f943-131">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="9f943-132">Als u een taak wilt verwijderen, gebruikt u de `Remove-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f943-132">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="9f943-133">Zie voor meer informatie over de werking van de cmdlets het Help-onderwerp voor elke cmdlet en Zie [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="9f943-133">For more information about how the cmdlets work, see the Help topic for each cmdlet, and see [about_Jobs](about_Jobs.md).</span></span>

### <a name="starting-background-jobs-on-remote-computers"></a><span data-ttu-id="9f943-134">Achtergrond taken op externe computers starten</span><span class="sxs-lookup"><span data-stu-id="9f943-134">Starting background jobs on remote computers</span></span>

<span data-ttu-id="9f943-135">U kunt achtergrond taken maken en beheren op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="9f943-135">You can create and manage background jobs on a local or remote computer.</span></span> <span data-ttu-id="9f943-136">Als u een achtergrond taak extern wilt uitvoeren, gebruikt u de para meter **AsJob** van een cmdlet zoals `Invoke-Command` of gebruikt `Invoke-Command` u de cmdlet om een `Start-Job` opdracht op afstand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9f943-136">To run a background job remotely, use the **AsJob** parameter of a cmdlet such as `Invoke-Command`, or use the `Invoke-Command` cmdlet to run a `Start-Job` command remotely.</span></span> <span data-ttu-id="9f943-137">U kunt ook een achtergrond taak in een interactieve sessie starten.</span><span class="sxs-lookup"><span data-stu-id="9f943-137">You can also start a background job in an interactive session.</span></span>

<span data-ttu-id="9f943-138">Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie over externe achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="9f943-138">For more information about remote background jobs, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>

### <a name="child-jobs"></a><span data-ttu-id="9f943-139">Onderliggende taken</span><span class="sxs-lookup"><span data-stu-id="9f943-139">Child jobs</span></span>

<span data-ttu-id="9f943-140">Elke achtergrond taak bestaat uit een bovenliggende taak en een of meer onderliggende taken.</span><span class="sxs-lookup"><span data-stu-id="9f943-140">Each background job consists of a parent job and one or more child jobs.</span></span> <span data-ttu-id="9f943-141">In taken die zijn gestart met `Start-Job` of de **AsJob** -para meter van `Invoke-Command` is de bovenliggende taak een Executive.</span><span class="sxs-lookup"><span data-stu-id="9f943-141">In jobs started using `Start-Job` or the **AsJob** parameter of `Invoke-Command`, the parent job is an executive.</span></span> <span data-ttu-id="9f943-142">Er worden geen opdrachten uitgevoerd en er worden geen resultaten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9f943-142">It does not run any commands or return any results.</span></span> <span data-ttu-id="9f943-143">De opdrachten worden feitelijk uitgevoerd door de onderliggende taken.</span><span class="sxs-lookup"><span data-stu-id="9f943-143">The commands are actually run by the child jobs.</span></span> <span data-ttu-id="9f943-144">Taken die zijn gestart met andere cmdlets werken mogelijk anders.</span><span class="sxs-lookup"><span data-stu-id="9f943-144">Jobs started using other cmdlets might work differently.</span></span>

<span data-ttu-id="9f943-145">De onderliggende taken worden opgeslagen in de eigenschap **ChildJobs** van het bovenliggende taak object.</span><span class="sxs-lookup"><span data-stu-id="9f943-145">The child jobs are stored in the **ChildJobs** property of the parent job object.</span></span> <span data-ttu-id="9f943-146">De eigenschap **ChildJobs** kan een of meer onderliggende taak objecten bevatten.</span><span class="sxs-lookup"><span data-stu-id="9f943-146">The **ChildJobs** property can contain one or many child job objects.</span></span>
<span data-ttu-id="9f943-147">De onderliggende taak objecten hebben een **naam** , **id** en **InstanceId** die verschillen van de bovenliggende taak, zodat u de bovenliggende en onderliggende taken afzonderlijk of als een eenheid kunt beheren.</span><span class="sxs-lookup"><span data-stu-id="9f943-147">The child job objects have a **Name** , **ID** , and **InstanceId** that differ from the parent job so that you can manage the parent and child jobs individually or as a unit.</span></span>

<span data-ttu-id="9f943-148">Als u de bovenliggende en onderliggende taken van een taak wilt ophalen, gebruikt u de para meter **IncludeChildJobs** van de `Get-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f943-148">To get the parent and child jobs of a job, use the **IncludeChildJobs** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="9f943-149">De para meter **IncludeChildJob** is geïntroduceerd in Windows power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9f943-149">The **IncludeChildJob** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="9f943-150">Als u de bovenliggende taak en alleen de onderliggende taken met een bepaalde **status** waarde wilt ophalen, gebruikt u de para meter **ChildJobState** van de `Get-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f943-150">To get the parent job and only the child jobs with a particular **State** value, use the **ChildJobState** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="9f943-151">De para meter **ChildJobState** is geïntroduceerd in Windows power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9f943-151">The **ChildJobState** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="9f943-152">Als u de onderliggende taken van een taak op alle versies van Power shell wilt ophalen, gebruikt u de eigenschap **ChildJob** van de bovenliggende taak.</span><span class="sxs-lookup"><span data-stu-id="9f943-152">To get the child jobs of a job on all versions of PowerShell, use the **ChildJob** property of the parent job.</span></span>

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="9f943-153">U kunt ook een `Get-Job` opdracht gebruiken in de onderliggende taak, zoals wordt weer gegeven in de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="9f943-153">You can also use a `Get-Job` command on the child job, as shown in the following command:</span></span>

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="9f943-154">De configuratie van de onderliggende taak is afhankelijk van de opdracht die u gebruikt om de taak te starten.</span><span class="sxs-lookup"><span data-stu-id="9f943-154">The configuration of the child job depends on the command that you use to start the job.</span></span>

- <span data-ttu-id="9f943-155">Wanneer u gebruikt `Start-Job` om een taak te starten op een lokale computer, bestaat de taak uit een Executive bovenliggende taak en een onderliggende taak die de opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9f943-155">When you use `Start-Job` to start a job on a local computer, the job consists of an executive parent job and a child job that runs the command.</span></span>

- <span data-ttu-id="9f943-156">Wanneer u de para meter **AsJob** van gebruikt `Invoke-Command` om een taak op een of meer computers te starten, bestaat de taak uit een Executive bovenliggende taak en een onderliggende taak voor elke taak die op elke computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9f943-156">When you use the **AsJob** parameter of `Invoke-Command` to start a job on one or more computers, the job consists of an executive parent job and a child job for each job run on each computer.</span></span>

- <span data-ttu-id="9f943-157">Wanneer u gebruikt `Invoke-Command` om een opdracht uit te voeren `Start-Job` op een of meer externe computers, is het resultaat hetzelfde als een lokale opdracht die op elke externe computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9f943-157">When you use `Invoke-Command` to run a `Start-Job` command on one or more remote computers, the result is the same as a local command run on each remote computer.</span></span> <span data-ttu-id="9f943-158">De opdracht retourneert een taak object voor elke computer.</span><span class="sxs-lookup"><span data-stu-id="9f943-158">The command returns a job object for each computer.</span></span> <span data-ttu-id="9f943-159">Het taak object bestaat uit een Executive bovenliggende taak en één onderliggende taak die de opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9f943-159">The job object consists of an executive parent job and one child job that runs the command.</span></span>

<span data-ttu-id="9f943-160">De bovenliggende taak vertegenwoordigt alle onderliggende taken.</span><span class="sxs-lookup"><span data-stu-id="9f943-160">The parent job represents all of the child jobs.</span></span> <span data-ttu-id="9f943-161">Wanneer u een bovenliggende taak beheert, beheert u ook de bijbehorende onderliggende taken.</span><span class="sxs-lookup"><span data-stu-id="9f943-161">When you manage a parent job, you also manage the associated child jobs.</span></span> <span data-ttu-id="9f943-162">Als u bijvoorbeeld een bovenliggende taak stopt, worden alle onderliggende taken gestopt.</span><span class="sxs-lookup"><span data-stu-id="9f943-162">For example, if you stop a parent job, all child jobs are stopped.</span></span> <span data-ttu-id="9f943-163">Als u de resultaten van een bovenliggende taak ontvangt, krijgt u de resultaten van alle onderliggende taken.</span><span class="sxs-lookup"><span data-stu-id="9f943-163">If you get the results of a parent job, you get the results of all child jobs.</span></span>

<span data-ttu-id="9f943-164">U kunt echter ook onderliggende taken afzonderlijk beheren.</span><span class="sxs-lookup"><span data-stu-id="9f943-164">However, you can also manage child jobs individually.</span></span> <span data-ttu-id="9f943-165">Dit is vooral handig wanneer u een probleem met een taak wilt onderzoeken of als u de resultaten wilt ophalen van slechts één van een aantal onderliggende taken dat is gestart met de para meter **AsJob** van `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="9f943-165">This is most useful when you want to investigate a problem with a job or get the results of only one of a number of child jobs started using the **AsJob** parameter of `Invoke-Command`.</span></span>

<span data-ttu-id="9f943-166">De volgende opdracht maakt gebruik van de para meter **AsJob** van `Invoke-Command` om achtergrond taken op de lokale computer en twee externe computers te starten.</span><span class="sxs-lookup"><span data-stu-id="9f943-166">The following command uses the **AsJob** parameter of `Invoke-Command` to start background jobs on the local computer and two remote computers.</span></span> <span data-ttu-id="9f943-167">Met de opdracht wordt de taak opgeslagen in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="9f943-167">The command saves the job in the `$j` variable.</span></span>

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

<span data-ttu-id="9f943-168">Wanneer u de eigenschappen name en **ChildJob** van de taak in weergeeft `$j` , ziet u dat de opdracht een taak object heeft geretourneerd met drie onderliggende taken, één voor elke computer.</span><span class="sxs-lookup"><span data-stu-id="9f943-168">When you display the Name and **ChildJob** properties of the job in `$j`, it shows that the command returned a job object with three child jobs, one for each computer.</span></span>

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

<span data-ttu-id="9f943-169">Wanneer u de bovenliggende taak weergeeft, ziet u dat de taak is mislukt.</span><span class="sxs-lookup"><span data-stu-id="9f943-169">When you display the parent job, it shows that the job failed.</span></span>

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

<span data-ttu-id="9f943-170">Maar wanneer u een `Get-Job` opdracht uitvoert waarmee de onderliggende taken worden opgehaald, laat de uitvoer zien dat er slechts één onderliggende taak is mislukt.</span><span class="sxs-lookup"><span data-stu-id="9f943-170">But when you run a `Get-Job` command that gets the child jobs, the output shows that only one child job failed.</span></span>

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

<span data-ttu-id="9f943-171">Als u de resultaten van alle onderliggende taken wilt ophalen, gebruikt u de `Receive-Job` cmdlet om de resultaten van de bovenliggende taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="9f943-171">To get the results of all child jobs, use the `Receive-Job` cmdlet to get the results of the parent job.</span></span> <span data-ttu-id="9f943-172">U kunt echter ook de resultaten van een bepaalde onderliggende taak ophalen, zoals wordt weer gegeven in de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="9f943-172">But you can also get the results of a particular child job, as shown in the following command.</span></span>

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

<span data-ttu-id="9f943-173">Met de functie voor onderliggende taken van Power shell-achtergrond taken hebt u meer controle over de taken die u uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9f943-173">The child jobs feature of PowerShell background jobs gives you more control over the jobs that you run.</span></span>

### <a name="job-types"></a><span data-ttu-id="9f943-174">Jobtypen</span><span class="sxs-lookup"><span data-stu-id="9f943-174">Job types</span></span>

<span data-ttu-id="9f943-175">Power shell ondersteunt verschillende typen taken voor verschillende taken.</span><span class="sxs-lookup"><span data-stu-id="9f943-175">PowerShell supports different types of jobs for different tasks.</span></span> <span data-ttu-id="9f943-176">Met ingang van Windows Power Shell 3,0 kunnen ontwikkel aars ' taak bron adapters ' schrijven waarmee nieuwe taak typen worden toegevoegd aan Power shell en de taak bron adapters in modules worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="9f943-176">Beginning in Windows PowerShell 3.0, developers can write "job source adapters" that add new job types to PowerShell and include the job source adapters in modules.</span></span>
<span data-ttu-id="9f943-177">Wanneer u de module importeert, kunt u het nieuwe taak type gebruiken in uw sessie.</span><span class="sxs-lookup"><span data-stu-id="9f943-177">When you import the module, you can use the new job type in your session.</span></span>

<span data-ttu-id="9f943-178">De PSScheduledJob-module voegt bijvoorbeeld geplande taken toe en de PSWorkflow-module voegt werk stroom taken toe.</span><span class="sxs-lookup"><span data-stu-id="9f943-178">For example, the PSScheduledJob module adds scheduled jobs and the PSWorkflow module adds workflow jobs.</span></span>

<span data-ttu-id="9f943-179">Aangepaste taken typen kunnen aanzienlijk verschillen van standaard-Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="9f943-179">Custom jobs types might differ significantly from standard PowerShell background jobs.</span></span> <span data-ttu-id="9f943-180">Geplande taken worden bijvoorbeeld op schijf opgeslagen. ze bestaan niet alleen in een bepaalde sessie.</span><span class="sxs-lookup"><span data-stu-id="9f943-180">For example, scheduled jobs are saved on disk; they do not exist only in a particular session.</span></span> <span data-ttu-id="9f943-181">Werk stroom taken kunnen worden onderbroken en hervat.</span><span class="sxs-lookup"><span data-stu-id="9f943-181">Workflow jobs can be suspended and resumed.</span></span>

<span data-ttu-id="9f943-182">De cmdlets die u gebruikt om aangepaste taken te beheren, zijn afhankelijk van het taak type.</span><span class="sxs-lookup"><span data-stu-id="9f943-182">The cmdlets that you use to manage custom jobs depend on the job type.</span></span> <span data-ttu-id="9f943-183">Voor sommige gebruikt u de standaard taak cmdlets, zoals `Get-Job` en `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="9f943-183">For some, you use the standard job cmdlets, such as `Get-Job` and `Start-Job`.</span></span> <span data-ttu-id="9f943-184">Andere worden geleverd met gespecialiseerde cmdlets die alleen een bepaald type taak beheren.</span><span class="sxs-lookup"><span data-stu-id="9f943-184">Others come with specialized cmdlets that manage only a particular type of job.</span></span> <span data-ttu-id="9f943-185">Zie de Help-onderwerpen over het taak type voor gedetailleerde informatie over aangepaste taak typen.</span><span class="sxs-lookup"><span data-stu-id="9f943-185">For detailed information about custom job types, see the help topics about the job type.</span></span>

<span data-ttu-id="9f943-186">Gebruik de cmdlet om het taak type van een taak te vinden `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="9f943-186">To find the job type of a job, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="9f943-187">`Get-Job` retourneert verschillende taak objecten voor verschillende typen taken.</span><span class="sxs-lookup"><span data-stu-id="9f943-187">`Get-Job` returns different job objects for different types of jobs.</span></span> <span data-ttu-id="9f943-188">De waarde van de eigenschap **PSJobTypeName** van de `Get-Job` geretourneerde taak objecten geeft het taak type aan.</span><span class="sxs-lookup"><span data-stu-id="9f943-188">The value of the **PSJobTypeName** property of the job objects that `Get-Job` returns indicates the job type.</span></span>

<span data-ttu-id="9f943-189">De volgende tabel bevat de taak typen die bij Power shell worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="9f943-189">The following table lists the job types that come with PowerShell.</span></span>

|    <span data-ttu-id="9f943-190">Taak type</span><span class="sxs-lookup"><span data-stu-id="9f943-190">Job Type</span></span>    |                       <span data-ttu-id="9f943-191">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9f943-191">Description</span></span>                        |
| -------------- | -------------------------------------------------------- |
| <span data-ttu-id="9f943-192">BackgroundJob</span><span class="sxs-lookup"><span data-stu-id="9f943-192">BackgroundJob</span></span>  | <span data-ttu-id="9f943-193">Het gebruik van de cmdlet is gestart `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="9f943-193">Started using the `Start-Job` cmdlet.</span></span>                    |
| <span data-ttu-id="9f943-194">RemoteJob</span><span class="sxs-lookup"><span data-stu-id="9f943-194">RemoteJob</span></span>      | <span data-ttu-id="9f943-195">Gestart met het gebruik van de para meter **AsJob** van de</span><span class="sxs-lookup"><span data-stu-id="9f943-195">Started using the **AsJob** parameter of the</span></span>             |
|                | <span data-ttu-id="9f943-196">`Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f943-196">`Invoke-Command` cmdlet.</span></span>                                 |
| <span data-ttu-id="9f943-197">PSWorkflowJob</span><span class="sxs-lookup"><span data-stu-id="9f943-197">PSWorkflowJob</span></span>  | <span data-ttu-id="9f943-198">Gestart met het gebruik van de para meter **AsJob** van een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="9f943-198">Started using the **AsJob** parameter of a workflow.</span></span>     |
| <span data-ttu-id="9f943-199">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9f943-199">PSScheduledJob</span></span> | <span data-ttu-id="9f943-200">Een exemplaar van een geplande taak die is gestart door een taak trigger.</span><span class="sxs-lookup"><span data-stu-id="9f943-200">An instance of a scheduled job started by a job trigger.</span></span> |
| <span data-ttu-id="9f943-201">CIMJob</span><span class="sxs-lookup"><span data-stu-id="9f943-201">CIMJob</span></span>         | <span data-ttu-id="9f943-202">Gestart met het gebruik van de para meter **AsJob** van een cmdlet van een</span><span class="sxs-lookup"><span data-stu-id="9f943-202">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="9f943-203">CDXML-module.</span><span class="sxs-lookup"><span data-stu-id="9f943-203">CDXML module.</span></span>                                            |
| <span data-ttu-id="9f943-204">WMIJob</span><span class="sxs-lookup"><span data-stu-id="9f943-204">WMIJob</span></span>         | <span data-ttu-id="9f943-205">Gestart met het gebruik van de para meter **AsJob** van een cmdlet van een</span><span class="sxs-lookup"><span data-stu-id="9f943-205">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="9f943-206">WMI-module.</span><span class="sxs-lookup"><span data-stu-id="9f943-206">WMI module.</span></span>                                              |
| <span data-ttu-id="9f943-207">PSEventJob</span><span class="sxs-lookup"><span data-stu-id="9f943-207">PSEventJob</span></span>     | <span data-ttu-id="9f943-208">Gemaakt met `Register-ObjectEvent` en opgeven van een</span><span class="sxs-lookup"><span data-stu-id="9f943-208">Created using`Register-ObjectEvent` and specifying an</span></span>    |
|                | <span data-ttu-id="9f943-209">actie met de **actie** parameter.</span><span class="sxs-lookup"><span data-stu-id="9f943-209">action with the **Action** parameter.</span></span>                    |

<span data-ttu-id="9f943-210">Opmerking: voordat u de `Get-Job` cmdlet gebruikt om taken van een bepaald type op te halen, moet u controleren of de module waarmee het taak type wordt toegevoegd, is geïmporteerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="9f943-210">NOTE: Before using the `Get-Job` cmdlet to get jobs of a particular type, verify that the module that adds the job type is imported into the current session.</span></span>
<span data-ttu-id="9f943-211">Als dat niet het geval is, `Get-Job` worden er geen taken van dat type opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9f943-211">Otherwise, `Get-Job` does not get jobs of that type.</span></span>

## <a name="examples"></a><span data-ttu-id="9f943-212">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="9f943-212">Examples</span></span>

<span data-ttu-id="9f943-213">Met de volgende opdrachten maakt u een lokale achtergrond taak, een externe achtergrond taak, een werk stroom taak en een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="9f943-213">The following commands create a local background job, a remote background job, a workflow job, and a scheduled job.</span></span> <span data-ttu-id="9f943-214">Vervolgens wordt de cmdlet gebruikt `Get-Job` om de taken op te halen.</span><span class="sxs-lookup"><span data-stu-id="9f943-214">Then, it uses the `Get-Job` cmdlet to get the jobs.</span></span> <span data-ttu-id="9f943-215">`Get-Job` Hiermee wordt de geplande taak niet opgehaald, maar worden alle gestarte exemplaren van de geplande taak opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9f943-215">`Get-Job` does not get the scheduled job, but it gets any started instances of the scheduled job.</span></span>

<span data-ttu-id="9f943-216">Start een achtergrond taak op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9f943-216">Start a background job on the local computer.</span></span>

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

<span data-ttu-id="9f943-217">Een achtergrond taak starten die wordt uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="9f943-217">Start a background job that runs on a remote computer.</span></span>

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

<span data-ttu-id="9f943-218">Een geplande taak maken</span><span class="sxs-lookup"><span data-stu-id="9f943-218">Create a scheduled job</span></span>

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

<span data-ttu-id="9f943-219">Een werk stroom maken.</span><span class="sxs-lookup"><span data-stu-id="9f943-219">Create a workflow.</span></span>

```powershell
PS> workflow Test-Workflow {Get-Process}
```

<span data-ttu-id="9f943-220">Voer de werk stroom uit als een taak.</span><span class="sxs-lookup"><span data-stu-id="9f943-220">Run the workflow as a job.</span></span>

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

<span data-ttu-id="9f943-221">De taken ophalen.</span><span class="sxs-lookup"><span data-stu-id="9f943-221">Get the jobs.</span></span> <span data-ttu-id="9f943-222">De `Get-Job` opdracht ontvangt geen geplande taken, maar er worden exemplaren van de geplande taak opgehaald die worden gestart.</span><span class="sxs-lookup"><span data-stu-id="9f943-222">The `Get-Job` command does not get scheduled jobs, but it gets instances of the scheduled job that are started.</span></span>

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

<span data-ttu-id="9f943-223">Als u geplande taken wilt ophalen, gebruikt u de `Get-ScheduledJob` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f943-223">To get scheduled jobs, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a><span data-ttu-id="9f943-224">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9f943-224">See also</span></span>

- [<span data-ttu-id="9f943-225">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="9f943-225">about_Jobs</span></span>](about_Jobs.md)
- [<span data-ttu-id="9f943-226">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="9f943-226">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="9f943-227">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="9f943-227">about_Thread_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs)
- [<span data-ttu-id="9f943-228">about_Remote</span><span class="sxs-lookup"><span data-stu-id="9f943-228">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="9f943-229">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="9f943-229">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="9f943-230">Begin taak</span><span class="sxs-lookup"><span data-stu-id="9f943-230">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="9f943-231">Get-job</span><span class="sxs-lookup"><span data-stu-id="9f943-231">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="9f943-232">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="9f943-232">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="9f943-233">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="9f943-233">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="9f943-234">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="9f943-234">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="9f943-235">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="9f943-235">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="9f943-236">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="9f943-236">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [<span data-ttu-id="9f943-237">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="9f943-237">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
