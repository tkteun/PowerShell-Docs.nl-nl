---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 0b9c76ca1e26adaa244473366c2eabdaaa28452c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249959"
---
# <span data-ttu-id="86a69-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="86a69-103">Get-Job</span></span>

## <span data-ttu-id="86a69-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="86a69-104">SYNOPSIS</span></span>
<span data-ttu-id="86a69-105">Hiermee worden Power shell-achtergrond taken opgehaald die in de huidige sessie worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="86a69-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="86a69-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="86a69-106">SYNTAX</span></span>

### <span data-ttu-id="86a69-107">SessionIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="86a69-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="86a69-108">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="86a69-108">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="86a69-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="86a69-109">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="86a69-110">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="86a69-110">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="86a69-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="86a69-111">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="86a69-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="86a69-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="86a69-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="86a69-113">DESCRIPTION</span></span>

<span data-ttu-id="86a69-114">De cmdlet **Get-job** haalt objecten op die de achtergrond taken vertegenwoordigen die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="86a69-114">The **Get-Job** cmdlet gets objects that represent the background jobs that were started in the current session.</span></span>
<span data-ttu-id="86a69-115">U kunt **Get-job** gebruiken om taken op te halen die zijn gestart met behulp van de cmdlet Start-Job, of door gebruik te maken van de para meter *AsJob* van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="86a69-115">You can use **Get-Job** to get jobs that were started by using the Start-Job cmdlet, or by using the *AsJob* parameter of any cmdlet.</span></span>

<span data-ttu-id="86a69-116">Zonder para meters haalt een **Get-job-** opdracht alle taken in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="86a69-116">Without parameters, a **Get-Job** command gets all jobs in the current session.</span></span>
<span data-ttu-id="86a69-117">U kunt de para meters van **Get-job** gebruiken om bepaalde taken op te halen.</span><span class="sxs-lookup"><span data-stu-id="86a69-117">You can use the parameters of **Get-Job** to get particular jobs.</span></span>

<span data-ttu-id="86a69-118">Het taak object dat **Get-job** retourneert, bevat nuttige informatie over de taak, maar bevat geen taak resultaten.</span><span class="sxs-lookup"><span data-stu-id="86a69-118">The job object that **Get-Job** returns contains useful information about the job, but it does not contain the job results.</span></span>
<span data-ttu-id="86a69-119">Gebruik de cmdlet Receive-Job om de resultaten op te halen.</span><span class="sxs-lookup"><span data-stu-id="86a69-119">To get the results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="86a69-120">Een Windows Power shell-achtergrond taak is een opdracht die op de achtergrond wordt uitgevoerd zonder interactie met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="86a69-120">A Windows PowerShell background job is a command that runs in the background without interacting with the current session.</span></span>
<span data-ttu-id="86a69-121">Normaal gesp roken gebruikt u een achtergrond taak om een complexe opdracht uit te voeren die veel tijd in beslag neemt.</span><span class="sxs-lookup"><span data-stu-id="86a69-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span>
<span data-ttu-id="86a69-122">Zie about_Jobs voor meer informatie over achtergrond taken in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="86a69-122">For more information about background jobs in Windows PowerShell, see about_Jobs.</span></span>

<span data-ttu-id="86a69-123">Vanaf Windows Power Shell 3,0 worden met de cmdlet **Get-job** ook aangepaste taak typen opgehaald, zoals werk stroom taken en exemplaren van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="86a69-123">Beginning in Windows PowerShell 3.0, the **Get-Job** cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="86a69-124">Gebruik de eigenschap **PSJobTypeName** van de taak om het taak type van een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="86a69-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="86a69-125">Als u **Get-job** wilt inschakelen om een aangepast taak type op te halen, importeert u de module die het aangepaste taak type ondersteunt in de sessie voordat u een opdracht **Get-job** uitvoert, met behulp van de Import-Module cmdlet of door een cmdlet in de module te gebruiken of op te halen.</span><span class="sxs-lookup"><span data-stu-id="86a69-125">To enable **Get-Job** to get a custom job type, import the module that supports the custom job type into the session before you run a **Get-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="86a69-126">Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.</span><span class="sxs-lookup"><span data-stu-id="86a69-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="86a69-127">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="86a69-127">EXAMPLES</span></span>

### <span data-ttu-id="86a69-128">Voor beeld 1: alle achtergrond taken ophalen gestart in de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="86a69-128">Example 1: Get all background jobs started in the current session</span></span>

```
PS C:\> Get-Job
```

<span data-ttu-id="86a69-129">Met deze opdracht worden alle achtergrond taken opgehaald die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="86a69-129">This command gets all background jobs started in the current session.</span></span>
<span data-ttu-id="86a69-130">Het bevat geen taken die zijn gemaakt in andere sessies, zelfs als de taken worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="86a69-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

### <span data-ttu-id="86a69-131">Voor beeld 2: een taak stoppen met een exemplaar-ID</span><span class="sxs-lookup"><span data-stu-id="86a69-131">Example 2: Stop a job by using an instance ID</span></span>

```
The first command uses the **Get-Job** cmdlet to get a job. It uses the *Name* parameter to identify the job. The command stores the job object that **Get-Job** returns in the $j variable. In this example, there is only one job with the specified name.
PS C:\> $j = Get-Job -Name Job1

The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.
PS C:\> $ID = $j.InstanceID

The third command displays the value of the $ID variable.
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

The fourth command uses Stop-Job cmdlet to stop the job. It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.
PS C:\> Stop-Job -InstanceId $ID
```

<span data-ttu-id="86a69-132">Deze opdrachten laten zien hoe u de exemplaar-ID van een taak ophaalt en vervolgens kunt gebruiken om een taak te stoppen.</span><span class="sxs-lookup"><span data-stu-id="86a69-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span>
<span data-ttu-id="86a69-133">In tegens telling tot de naam van een taak, die niet uniek is, is de exemplaar-ID uniek.</span><span class="sxs-lookup"><span data-stu-id="86a69-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

### <span data-ttu-id="86a69-134">Voor beeld 3: taken ophalen die een specifieke opdracht bevatten</span><span class="sxs-lookup"><span data-stu-id="86a69-134">Example 3: Get jobs that include a specific command</span></span>

```
PS C:\> Get-Job -Command "*get-process*"
```

<span data-ttu-id="86a69-135">Met deze opdracht worden de taken op het systeem opgehaald die een Get-Process opdracht bevatten.</span><span class="sxs-lookup"><span data-stu-id="86a69-135">This command gets the jobs on the system that include a Get-Process command.</span></span>
<span data-ttu-id="86a69-136">De opdracht gebruikt de *opdracht* parameter van **Get-job** om de opgehaalde taken te beperken.</span><span class="sxs-lookup"><span data-stu-id="86a69-136">The command uses the *Command* parameter of **Get-Job** to limit the jobs retrieved.</span></span>
<span data-ttu-id="86a69-137">De opdracht gebruikt joker tekens (\*) om taken op te halen die een opdracht **Get-process bevatten,** overal in de opdracht reeks.</span><span class="sxs-lookup"><span data-stu-id="86a69-137">The command uses wildcard characters (\*) to get jobs that include a **Get-Process** command anywhere in the command string.</span></span>

### <span data-ttu-id="86a69-138">Voor beeld 4: taken met een bepaalde opdracht ophalen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="86a69-138">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

```
PS C:\> "*get-process*" | Get-Job
```

<span data-ttu-id="86a69-139">Net als de opdracht in het vorige voor beeld, haalt deze opdracht de taken op het systeem op die een opdracht **Get-process** bevatten.</span><span class="sxs-lookup"><span data-stu-id="86a69-139">Like the command in the previous example, this command gets the jobs on the system that include a **Get-Process** command.</span></span>
<span data-ttu-id="86a69-140">De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van een teken reeks tussen aanhalings tekens en de cmdlet **Get-job** .</span><span class="sxs-lookup"><span data-stu-id="86a69-140">The command uses a pipeline operator (|) to send a string, in quotation marks, to the **Get-Job** cmdlet.</span></span>
<span data-ttu-id="86a69-141">Dit is het equivalent van de vorige opdracht.</span><span class="sxs-lookup"><span data-stu-id="86a69-141">It is the equivalent of the previous command.</span></span>

### <span data-ttu-id="86a69-142">Voor beeld 5: taken ophalen die niet zijn gestart</span><span class="sxs-lookup"><span data-stu-id="86a69-142">Example 5: Get jobs that have not been started</span></span>

```
PS C:\> Get-Job -State NotStarted
```

<span data-ttu-id="86a69-143">Met deze opdracht worden alleen de taken opgehaald die zijn gemaakt, maar die nog niet zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="86a69-143">This command gets only those jobs that have been created but have not yet been started.</span></span>
<span data-ttu-id="86a69-144">Dit omvat taken die in de toekomst zijn gepland en die nog niet zijn gepland.</span><span class="sxs-lookup"><span data-stu-id="86a69-144">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

### <span data-ttu-id="86a69-145">Voor beeld 6: taken ophalen waaraan geen naam is toegewezen</span><span class="sxs-lookup"><span data-stu-id="86a69-145">Example 6: Get jobs that have not been assigned a name</span></span>

```
PS C:\> Get-Job -Name Job*
```

<span data-ttu-id="86a69-146">Met deze opdracht worden alle taken opgehaald die met taak namen beginnen.</span><span class="sxs-lookup"><span data-stu-id="86a69-146">This command gets all jobs that have job names that begin with job.</span></span>
<span data-ttu-id="86a69-147">Omdat taak \<number\> de standaard naam voor een taak is, worden met deze opdracht alle taken opgehaald die geen expliciet toegewezen naam hebben.</span><span class="sxs-lookup"><span data-stu-id="86a69-147">Because job\<number\> is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

### <span data-ttu-id="86a69-148">Voor beeld 7: een taak object gebruiken om de taak in een opdracht weer te geven</span><span class="sxs-lookup"><span data-stu-id="86a69-148">Example 7: Use a job object to represent the job in a command</span></span>

```
The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer. The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob

The second command uses Get-Job to get the job. It uses the *Name* parameter of **Get-Job** to identify the job. The command saves the resulting job object in the $j variable.
PS C:\> $j = Get-Job -Name MyJob

The third command displays the value of the job object in the $j variable. The value of the **State** property shows that the job is completed. The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

The fourth command uses the **Receive-Job** cmdlet to get the results of the job. It uses the job object in the $j variable to represent the job. You can also use a pipeline operator to send a job object to **Receive-Job**.
PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

<span data-ttu-id="86a69-149">In dit voor beeld ziet u hoe u **Get-job** kunt gebruiken om een taak object op te halen. vervolgens ziet u hoe u het taak object kunt gebruiken om de taak in een opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="86a69-149">This example shows how to use **Get-Job** to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

### <span data-ttu-id="86a69-150">Voor beeld 8: alle taken ophalen, inclusief taken die met een andere methode zijn gestart</span><span class="sxs-lookup"><span data-stu-id="86a69-150">Example 8: Get all jobs including jobs started by a different method</span></span>

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer.
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}

The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer. Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob

The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer. By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}

The fourth command uses **Get-Job** to get the jobs stored on the local computer. The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command. On the S2 computer, the job appears to be a local job. The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see about_Remote_Jobs.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

<span data-ttu-id="86a69-151">In dit voor beeld wordt gedemonstreerd dat de cmdlet **Get-job** alle taken kan ophalen die in de huidige sessie zijn gestart, zelfs als deze zijn gestart door verschillende methoden te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="86a69-151">This example demonstrates that the **Get-Job** cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

### <span data-ttu-id="86a69-152">Voor beeld 9: een mislukte taak onderzoeken</span><span class="sxs-lookup"><span data-stu-id="86a69-152">Example 9: Investigate a failed job</span></span>

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer. The job object that **Start-Job** returns shows that the job failed. The value of the **State** property is Failed.
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

The second command uses the **Get-Job** cmdlet to get the job. The command uses the dot method to get the value of the **JobStateInfo** property of the object. It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.
PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

The third command investigates more. It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.
PS C:\> Get-Job | Format-List -Property *
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :

The fourth command uses **Get-Job** to get the job object that represents the Job2 child job. This is the job in which the command actually ran. It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error. In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see about_Remote_Requirements. For troubleshooting tips, see about_Remote_Troubleshooting.
PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.
```

<span data-ttu-id="86a69-153">Met deze opdracht wordt uitgelegd hoe u het taak object gebruikt dat **Get-job** retourneert om te onderzoeken waarom een taak is mislukt.</span><span class="sxs-lookup"><span data-stu-id="86a69-153">This command shows how to use the job object that **Get-Job** returns to investigate why a job failed.</span></span>
<span data-ttu-id="86a69-154">Ook wordt uitgelegd hoe u de onderliggende taken van elke taak kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="86a69-154">It also shows how to get the child jobs of each job.</span></span>

### <span data-ttu-id="86a69-155">Voor beeld 10: gefilterde resultaten ophalen</span><span class="sxs-lookup"><span data-stu-id="86a69-155">Example 10: Get filtered results</span></span>

```
The first command uses the **Workflow** keyword to create the WFProcess workflow.
PS C:\> Workflow WFProcess {Get-Process}

The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job. It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}

The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

<span data-ttu-id="86a69-156">In dit voor beeld ziet u hoe u de *filter* parameter gebruikt om een werk stroom taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="86a69-156">This example shows how to use the *Filter* parameter to get a workflow job.</span></span>
<span data-ttu-id="86a69-157">De *filter* parameter, die is geïntroduceerd in Windows power Shell 3,0, is alleen geldig voor aangepaste taak typen, zoals werk stroom taken en geplande taken.</span><span class="sxs-lookup"><span data-stu-id="86a69-157">The *Filter* parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

### <span data-ttu-id="86a69-158">Voor beeld 11: informatie over onderliggende taken ophalen</span><span class="sxs-lookup"><span data-stu-id="86a69-158">Example 11: Get information about child jobs</span></span>

```
The first command gets the jobs in the current session. The output includes a background job, a remote job and several instances of a scheduled job. The remote job, Job4, appears to have failed.
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The second command uses the *IncludeChildJob* parameter of **Get-Job**. The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.
PS C:\> Get-Job -IncludeChildJob
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.
PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.
PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

<span data-ttu-id="86a69-159">In dit voor beeld ziet u het effect van het gebruik van de para meters *IncludeChildJob* en *ChildJobState* van de cmdlet **Get-job** .</span><span class="sxs-lookup"><span data-stu-id="86a69-159">This example shows the effect of using the *IncludeChildJob* and *ChildJobState* parameters of the **Get-Job** cmdlet.</span></span>

## <span data-ttu-id="86a69-160">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="86a69-160">PARAMETERS</span></span>

### <span data-ttu-id="86a69-161">-Na</span><span class="sxs-lookup"><span data-stu-id="86a69-161">-After</span></span>

<span data-ttu-id="86a69-162">Hiermee worden voltooide taken opgehaald die zijn beëindigd na de opgegeven datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="86a69-162">Gets completed jobs that ended after the specified date and time.</span></span>
<span data-ttu-id="86a69-163">Voer een **DateTime** -object in, bijvoorbeeld een waarde die wordt geretourneerd door de Get-Date cmdlet of een teken reeks die kan worden geconverteerd naar een **DateTime** -object, zoals `Dec 1, 2012 2:00 AM` of `11/06` .</span><span class="sxs-lookup"><span data-stu-id="86a69-163">Enter a **DateTime** object, such as one returned by the Get-Date cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="86a69-164">Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken, die een eigenschap **EndTime** hebben.</span><span class="sxs-lookup"><span data-stu-id="86a69-164">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span>
<span data-ttu-id="86a69-165">Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .</span><span class="sxs-lookup"><span data-stu-id="86a69-165">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="86a69-166">Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="86a69-166">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="86a69-167">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="86a69-167">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="86a69-168">-Vóór</span><span class="sxs-lookup"><span data-stu-id="86a69-168">-Before</span></span>

<span data-ttu-id="86a69-169">Hiermee worden voltooide taken opgehaald die voor de opgegeven datum en tijd zijn beëindigd.</span><span class="sxs-lookup"><span data-stu-id="86a69-169">Gets completed jobs that ended before the specified date and time.</span></span>
<span data-ttu-id="86a69-170">Voer een **DateTime** -object in.</span><span class="sxs-lookup"><span data-stu-id="86a69-170">Enter a **DateTime** object.</span></span>

<span data-ttu-id="86a69-171">Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken, die een eigenschap **EndTime** hebben.</span><span class="sxs-lookup"><span data-stu-id="86a69-171">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span>
<span data-ttu-id="86a69-172">Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .</span><span class="sxs-lookup"><span data-stu-id="86a69-172">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="86a69-173">Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="86a69-173">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="86a69-174">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="86a69-174">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="86a69-175">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="86a69-175">-ChildJobState</span></span>

<span data-ttu-id="86a69-176">Hiermee worden alleen de onderliggende taken met de opgegeven status opgehaald.</span><span class="sxs-lookup"><span data-stu-id="86a69-176">Gets only the child jobs that have the specified state.</span></span>
<span data-ttu-id="86a69-177">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="86a69-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="86a69-178">NotStarted</span><span class="sxs-lookup"><span data-stu-id="86a69-178">NotStarted</span></span>
- <span data-ttu-id="86a69-179">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="86a69-179">Running</span></span>
- <span data-ttu-id="86a69-180">Voltooid</span><span class="sxs-lookup"><span data-stu-id="86a69-180">Completed</span></span>
- <span data-ttu-id="86a69-181">Mislukt</span><span class="sxs-lookup"><span data-stu-id="86a69-181">Failed</span></span>
- <span data-ttu-id="86a69-182">Gestopt</span><span class="sxs-lookup"><span data-stu-id="86a69-182">Stopped</span></span>
- <span data-ttu-id="86a69-183">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="86a69-183">Blocked</span></span>
- <span data-ttu-id="86a69-184">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="86a69-184">Suspended</span></span>
- <span data-ttu-id="86a69-185">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="86a69-185">Disconnected</span></span>
- <span data-ttu-id="86a69-186">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="86a69-186">Suspending</span></span>
- <span data-ttu-id="86a69-187">Stoppen</span><span class="sxs-lookup"><span data-stu-id="86a69-187">Stopping</span></span>

<span data-ttu-id="86a69-188">**Get-job** krijgt standaard geen onderliggende taken.</span><span class="sxs-lookup"><span data-stu-id="86a69-188">By default, **Get-Job** does not get child jobs.</span></span>
<span data-ttu-id="86a69-189">Met behulp van de *IncludeChildJob* para meter **Get-job** worden alle onderliggende taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="86a69-189">By using the *IncludeChildJob* parameter, **Get-Job** gets all child jobs.</span></span>
<span data-ttu-id="86a69-190">Als u de para meter *ChildJobState* gebruikt, heeft de para meter *IncludeChildJob* geen effect.</span><span class="sxs-lookup"><span data-stu-id="86a69-190">If you use the *ChildJobState* parameter, the *IncludeChildJob* parameter has no effect.</span></span>

<span data-ttu-id="86a69-191">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="86a69-191">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="86a69-192">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="86a69-192">-Command</span></span>

<span data-ttu-id="86a69-193">Geeft een matrix van opdrachten aan als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="86a69-193">Specifies an array of commands as strings.</span></span>
<span data-ttu-id="86a69-194">Met deze cmdlet worden de taken opgehaald die de opgegeven opdrachten bevatten.</span><span class="sxs-lookup"><span data-stu-id="86a69-194">This cmdlet gets the jobs that include the specified commands.</span></span>
<span data-ttu-id="86a69-195">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="86a69-195">The default is all jobs.</span></span>
<span data-ttu-id="86a69-196">U kunt joker tekens gebruiken om een opdracht patroon op te geven.</span><span class="sxs-lookup"><span data-stu-id="86a69-196">You can use wildcard characters to specify a command pattern.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="86a69-197">-Filter</span><span class="sxs-lookup"><span data-stu-id="86a69-197">-Filter</span></span>

<span data-ttu-id="86a69-198">Hiermee geeft u een hash-tabel met voor waarden op.</span><span class="sxs-lookup"><span data-stu-id="86a69-198">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="86a69-199">Met deze cmdlet worden taken opgehaald die voldoen aan alle voor waarden.</span><span class="sxs-lookup"><span data-stu-id="86a69-199">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="86a69-200">Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="86a69-200">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="86a69-201">Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken.</span><span class="sxs-lookup"><span data-stu-id="86a69-201">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="86a69-202">Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .</span><span class="sxs-lookup"><span data-stu-id="86a69-202">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="86a69-203">Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="86a69-203">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="86a69-204">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="86a69-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="86a69-205">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="86a69-205">-HasMoreData</span></span>

<span data-ttu-id="86a69-206">Hiermee wordt aangegeven of met deze cmdlet alleen taken worden opgehaald die de opgegeven waarde voor de eigenschap **HasMoreData** hebben.</span><span class="sxs-lookup"><span data-stu-id="86a69-206">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="86a69-207">De eigenschap **HasMoreData** geeft aan of alle taak resultaten zijn ontvangen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="86a69-207">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span>
<span data-ttu-id="86a69-208">Als u taken met meer resultaten wilt ophalen, geeft u de waarde $True op.</span><span class="sxs-lookup"><span data-stu-id="86a69-208">To get jobs that have more results, specify a value of $True.</span></span>
<span data-ttu-id="86a69-209">Als u taken wilt ophalen die niet meer resultaten hebben, geeft u de waarde $False op.</span><span class="sxs-lookup"><span data-stu-id="86a69-209">To get jobs that do not have more results, specify a value of $False.</span></span>

<span data-ttu-id="86a69-210">Gebruik de cmdlet Receive-Job om de resultaten van een taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="86a69-210">To get the results of a job, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="86a69-211">Wanneer u de cmdlet **Receive-job** gebruikt, wordt deze verwijderd uit de in-Memory, sessie-specifieke opslag de geretourneerde resultaten.</span><span class="sxs-lookup"><span data-stu-id="86a69-211">When you use the **Receive-Job** cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span>
<span data-ttu-id="86a69-212">Wanneer het alle resultaten van de taak in de huidige sessie heeft geretourneerd, wordt de waarde van de eigenschap **HasMoreData** van de taak ingesteld op $false) om aan te geven dat deze geen resultaten meer heeft voor de taak in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="86a69-212">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to $False) to indicate that it has no more results for the job in the current session.</span></span>
<span data-ttu-id="86a69-213">Gebruik de *para* meter van **Receive-job** om te voor komen dat de **functie receive** results verwijdert en de waarde van de eigenschap **HasMoreData** wijzigt.</span><span class="sxs-lookup"><span data-stu-id="86a69-213">Use the *Keep* parameter of **Receive-Job** to prevent **Receive-Job** from deleting results and changing the value of the **HasMoreData** property.</span></span>
<span data-ttu-id="86a69-214">Typ `Get-Help Receive-Job` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="86a69-214">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="86a69-215">De eigenschap **HasMoreData** is specifiek voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="86a69-215">The **HasMoreData** property is specific to the current session.</span></span>
<span data-ttu-id="86a69-216">Als de resultaten voor een aangepast taak type buiten de sessie worden opgeslagen, zoals het type geplande taak, waarmee taak resultaten op schijf worden opgeslagen, kunt u de cmdlet **Receive-job** in een andere sessie gebruiken om de taak resultaten opnieuw op te halen, zelfs als de waarde van **HasMoreData** is $False.</span><span class="sxs-lookup"><span data-stu-id="86a69-216">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the **Receive-Job** cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is $False.</span></span>
<span data-ttu-id="86a69-217">Zie de Help-onderwerpen voor het aangepaste taak type voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="86a69-217">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="86a69-218">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="86a69-218">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="86a69-219">-Id</span><span class="sxs-lookup"><span data-stu-id="86a69-219">-Id</span></span>

<span data-ttu-id="86a69-220">Hiermee wordt een matrix met Id's opgegeven van taken die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="86a69-220">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="86a69-221">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="86a69-221">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="86a69-222">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="86a69-222">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="86a69-223">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="86a69-223">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="86a69-224">Als u de ID van een taak wilt zoeken, typt u `Get-Job` zonder para meters.</span><span class="sxs-lookup"><span data-stu-id="86a69-224">To find the ID of a job, type `Get-Job` without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="86a69-225">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="86a69-225">-IncludeChildJob</span></span>

<span data-ttu-id="86a69-226">Geeft aan dat deze cmdlet onderliggende taken retourneert, naast de bovenliggende taken.</span><span class="sxs-lookup"><span data-stu-id="86a69-226">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="86a69-227">Deze para meter is vooral nuttig voor het onderzoeken van werk stroom taken, waarvoor **Get-job** een bovenliggende container taak en taak fouten retourneert, omdat de reden voor de fout wordt opgeslagen in een eigenschap van de onderliggende taak.</span><span class="sxs-lookup"><span data-stu-id="86a69-227">This parameter is especially useful for investigating workflow jobs, for which **Get-Job** returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="86a69-228">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="86a69-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="86a69-229">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="86a69-229">-InstanceId</span></span>

<span data-ttu-id="86a69-230">Hiermee geeft u een matrix met exemplaar-Id's van taken op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="86a69-230">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="86a69-231">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="86a69-231">The default is all jobs.</span></span>

<span data-ttu-id="86a69-232">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="86a69-232">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="86a69-233">Gebruik **Get-job** om de exemplaar-id van een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="86a69-233">To find the instance ID of a job, use **Get-Job**.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="86a69-234">-Name</span><span class="sxs-lookup"><span data-stu-id="86a69-234">-Name</span></span>

<span data-ttu-id="86a69-235">Hiermee geeft u een matrix met beschrijvende namen van taken op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="86a69-235">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="86a69-236">Voer een taak naam in of gebruik joker tekens om een job name-patroon in te voeren.</span><span class="sxs-lookup"><span data-stu-id="86a69-236">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span>
<span data-ttu-id="86a69-237">**Get-job** haalt standaard alle taken in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="86a69-237">By default, **Get-Job** gets all jobs in the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="86a69-238">-Nieuwste</span><span class="sxs-lookup"><span data-stu-id="86a69-238">-Newest</span></span>

<span data-ttu-id="86a69-239">Hiermee geeft u een aantal taken op dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="86a69-239">Specifies a number of jobs to get.</span></span>
<span data-ttu-id="86a69-240">Met deze cmdlet worden de taken opgehaald die het meest recent zijn beëindigd.</span><span class="sxs-lookup"><span data-stu-id="86a69-240">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="86a69-241">De *nieuwste* para meter sorteert of retourneert de nieuwste taken niet in de volg orde van de eind tijd.</span><span class="sxs-lookup"><span data-stu-id="86a69-241">The *Newest* parameter does not sort or return the newest jobs in end-time order.</span></span>
<span data-ttu-id="86a69-242">Als u de uitvoer wilt sorteren, gebruikt u de cmdlet Sort-Object.</span><span class="sxs-lookup"><span data-stu-id="86a69-242">To sort the output, use the Sort-Object cmdlet.</span></span>

<span data-ttu-id="86a69-243">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="86a69-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="86a69-244">-Status</span><span class="sxs-lookup"><span data-stu-id="86a69-244">-State</span></span>

<span data-ttu-id="86a69-245">Hiermee geeft u een taak status op.</span><span class="sxs-lookup"><span data-stu-id="86a69-245">Specifies a job state.</span></span>
<span data-ttu-id="86a69-246">Met deze cmdlet worden alleen taken in de opgegeven status opgehaald.</span><span class="sxs-lookup"><span data-stu-id="86a69-246">This cmdlet gets only jobs in the specified state.</span></span>
<span data-ttu-id="86a69-247">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="86a69-247">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="86a69-248">NotStarted</span><span class="sxs-lookup"><span data-stu-id="86a69-248">NotStarted</span></span>
- <span data-ttu-id="86a69-249">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="86a69-249">Running</span></span>
- <span data-ttu-id="86a69-250">Voltooid</span><span class="sxs-lookup"><span data-stu-id="86a69-250">Completed</span></span>
- <span data-ttu-id="86a69-251">Mislukt</span><span class="sxs-lookup"><span data-stu-id="86a69-251">Failed</span></span>
- <span data-ttu-id="86a69-252">Gestopt</span><span class="sxs-lookup"><span data-stu-id="86a69-252">Stopped</span></span>
- <span data-ttu-id="86a69-253">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="86a69-253">Blocked</span></span>
- <span data-ttu-id="86a69-254">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="86a69-254">Suspended</span></span>
- <span data-ttu-id="86a69-255">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="86a69-255">Disconnected</span></span>
- <span data-ttu-id="86a69-256">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="86a69-256">Suspending</span></span>
- <span data-ttu-id="86a69-257">Stoppen</span><span class="sxs-lookup"><span data-stu-id="86a69-257">Stopping</span></span>

<span data-ttu-id="86a69-258">**Get-job** haalt standaard alle taken in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="86a69-258">By default, **Get-Job** gets all the jobs in the current session.</span></span>

<span data-ttu-id="86a69-259">Zie [JobState Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.jobstate) in de MSDN-bibliotheek voor meer informatie over de status van de taak.</span><span class="sxs-lookup"><span data-stu-id="86a69-259">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="86a69-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="86a69-260">CommonParameters</span></span>

<span data-ttu-id="86a69-261">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="86a69-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="86a69-262">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="86a69-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="86a69-263">INVOER</span><span class="sxs-lookup"><span data-stu-id="86a69-263">INPUTS</span></span>

### <span data-ttu-id="86a69-264">Geen</span><span class="sxs-lookup"><span data-stu-id="86a69-264">None</span></span>

<span data-ttu-id="86a69-265">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="86a69-265">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="86a69-266">UITVOER</span><span class="sxs-lookup"><span data-stu-id="86a69-266">OUTPUTS</span></span>

### <span data-ttu-id="86a69-267">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="86a69-267">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="86a69-268">Deze cmdlet retourneert objecten die de taken in de sessie vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="86a69-268">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="86a69-269">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="86a69-269">NOTES</span></span>

* <span data-ttu-id="86a69-270">De eigenschap **PSJobTypeName** van taken geeft het taak type van de taak aan.</span><span class="sxs-lookup"><span data-stu-id="86a69-270">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="86a69-271">De waarde van de eigenschap wordt bepaald door de auteur van het taak type.</span><span class="sxs-lookup"><span data-stu-id="86a69-271">The property value is determined by the job type author.</span></span> <span data-ttu-id="86a69-272">De volgende lijst bevat algemene taak typen.</span><span class="sxs-lookup"><span data-stu-id="86a69-272">The following list shows common job types.</span></span>

  - <span data-ttu-id="86a69-273">**BackgroundJob**.</span><span class="sxs-lookup"><span data-stu-id="86a69-273">**BackgroundJob**.</span></span>
<span data-ttu-id="86a69-274">De lokale taak is gestart met **het starten** van de taak.</span><span class="sxs-lookup"><span data-stu-id="86a69-274">Local job started by using **Start-Job**.</span></span>

  - <span data-ttu-id="86a69-275">**RemoteJob**.</span><span class="sxs-lookup"><span data-stu-id="86a69-275">**RemoteJob**.</span></span>
<span data-ttu-id="86a69-276">De taak is gestart in een **PSSession** met de para meter *AsJob* van de cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="86a69-276">Job started in a **PSSession** by using the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>

  - <span data-ttu-id="86a69-277">**PSWorkflowJob**.</span><span class="sxs-lookup"><span data-stu-id="86a69-277">**PSWorkflowJob**.</span></span>
<span data-ttu-id="86a69-278">De taak is gestart met de gemeen schappelijke para meter *AsJob* van werk stromen.</span><span class="sxs-lookup"><span data-stu-id="86a69-278">Job started by using the *AsJob* common parameter of workflows.</span></span>

## <span data-ttu-id="86a69-279">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="86a69-279">RELATED LINKS</span></span>

[<span data-ttu-id="86a69-280">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="86a69-280">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="86a69-281">Receive-job</span><span class="sxs-lookup"><span data-stu-id="86a69-281">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="86a69-282">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="86a69-282">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="86a69-283">Resume-job</span><span class="sxs-lookup"><span data-stu-id="86a69-283">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="86a69-284">Begin taak</span><span class="sxs-lookup"><span data-stu-id="86a69-284">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="86a69-285">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="86a69-285">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="86a69-286">Onderbreken-taak</span><span class="sxs-lookup"><span data-stu-id="86a69-286">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="86a69-287">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="86a69-287">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="86a69-288">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="86a69-288">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="86a69-289">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="86a69-289">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="86a69-290">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="86a69-290">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="86a69-291">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="86a69-291">about_Scheduled_Jobs</span></span>](../PSScheduledJob/About/about_Scheduled_Jobs.md)
