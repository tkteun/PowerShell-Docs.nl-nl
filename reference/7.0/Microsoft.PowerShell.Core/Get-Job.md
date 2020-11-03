---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 76644dbf15d2bdabd7a365f4bd5910a50502e17d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249785"
---
# <span data-ttu-id="cb090-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="cb090-103">Get-Job</span></span>

## <span data-ttu-id="cb090-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cb090-104">SYNOPSIS</span></span>
<span data-ttu-id="cb090-105">Hiermee worden Power shell-achtergrond taken opgehaald die in de huidige sessie worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cb090-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="cb090-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cb090-106">SYNTAX</span></span>

### <span data-ttu-id="cb090-107">SessionIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="cb090-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="cb090-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="cb090-108">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="cb090-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="cb090-109">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="cb090-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="cb090-110">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="cb090-111">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="cb090-111">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="cb090-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="cb090-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="cb090-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cb090-113">DESCRIPTION</span></span>

<span data-ttu-id="cb090-114">De cmdlet **Get-job** haalt objecten op die de achtergrond taken vertegenwoordigen die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="cb090-114">The **Get-Job** cmdlet gets objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="cb090-115">U kunt **Get-job** gebruiken om taken op te halen die zijn gestart met behulp van de cmdlet Start-Job, of door gebruik te maken van de para meter *AsJob* van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cb090-115">You can use **Get-Job** to get jobs that were started by using the Start-Job cmdlet, or by using the *AsJob* parameter of any cmdlet.</span></span>

<span data-ttu-id="cb090-116">Zonder para meters haalt een **Get-job-** opdracht alle taken in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="cb090-116">Without parameters, a **Get-Job** command gets all jobs in the current session.</span></span>
<span data-ttu-id="cb090-117">U kunt de para meters van **Get-job** gebruiken om bepaalde taken op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb090-117">You can use the parameters of **Get-Job** to get particular jobs.</span></span>

<span data-ttu-id="cb090-118">Het taak object dat **Get-job** retourneert, bevat nuttige informatie over de taak, maar bevat geen taak resultaten.</span><span class="sxs-lookup"><span data-stu-id="cb090-118">The job object that **Get-Job** returns contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="cb090-119">Gebruik de cmdlet Receive-Job om de resultaten op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb090-119">To get the results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="cb090-120">Een Power shell-achtergrond taak is een opdracht die op de achtergrond wordt uitgevoerd zonder interactie met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="cb090-120">A PowerShell background job is a command that runs in the background without interacting with the current session.</span></span> <span data-ttu-id="cb090-121">Normaal gesp roken gebruikt u een achtergrond taak om een complexe opdracht uit te voeren die veel tijd in beslag neemt.</span><span class="sxs-lookup"><span data-stu-id="cb090-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span> <span data-ttu-id="cb090-122">Zie about_Jobs voor meer informatie over achtergrond taken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="cb090-122">For more information about background jobs in PowerShell, see about_Jobs.</span></span>

<span data-ttu-id="cb090-123">Vanaf Windows Power Shell 3,0 worden met de cmdlet **Get-job** ook aangepaste taak typen opgehaald, zoals werk stroom taken en exemplaren van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="cb090-123">Beginning in Windows PowerShell 3.0, the **Get-Job** cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="cb090-124">Gebruik de eigenschap **PSJobTypeName** van de taak om het taak type van een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="cb090-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="cb090-125">Als u **Get-job** wilt inschakelen om een aangepast taak type op te halen, importeert u de module die het aangepaste taak type ondersteunt in de sessie voordat u een opdracht **Get-job** uitvoert, met behulp van de Import-Module cmdlet of door een cmdlet in de module te gebruiken of op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb090-125">To enable **Get-Job** to get a custom job type, import the module that supports the custom job type into the session before you run a **Get-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="cb090-126">Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.</span><span class="sxs-lookup"><span data-stu-id="cb090-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="cb090-127">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cb090-127">EXAMPLES</span></span>

### <span data-ttu-id="cb090-128">Voor beeld 1: alle achtergrond taken ophalen gestart in de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="cb090-128">Example 1: Get all background jobs started in the current session</span></span>

```powershell
Get-Job
```

<span data-ttu-id="cb090-129">Met deze opdracht worden alle achtergrond taken opgehaald die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="cb090-129">This command gets all background jobs started in the current session.</span></span>
<span data-ttu-id="cb090-130">Het bevat geen taken die zijn gemaakt in andere sessies, zelfs als de taken worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="cb090-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

### <span data-ttu-id="cb090-131">Voor beeld 2: een taak stoppen met een exemplaar-ID</span><span class="sxs-lookup"><span data-stu-id="cb090-131">Example 2: Stop a job by using an instance ID</span></span>

<span data-ttu-id="cb090-132">Deze opdrachten laten zien hoe u de exemplaar-ID van een taak ophaalt en vervolgens kunt gebruiken om een taak te stoppen.</span><span class="sxs-lookup"><span data-stu-id="cb090-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span>
<span data-ttu-id="cb090-133">In tegens telling tot de naam van een taak, die niet uniek is, is de exemplaar-ID uniek.</span><span class="sxs-lookup"><span data-stu-id="cb090-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

```powershell
$j = Get-Job -Name Job1
$ID = $j.InstanceID
$ID
```

```Output
Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55
```

```powershell
Stop-Job -InstanceId $ID
```

<span data-ttu-id="cb090-134">De eerste opdracht maakt gebruik van de cmdlet **Get-job** om een taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb090-134">The first command uses the **Get-Job** cmdlet to get a job.</span></span> <span data-ttu-id="cb090-135">De para meter *name* wordt gebruikt om de taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="cb090-135">It uses the *Name* parameter to identify the job.</span></span> <span data-ttu-id="cb090-136">De opdracht slaat het taak object op dat **Get-job** retourneert in de variabele $j.</span><span class="sxs-lookup"><span data-stu-id="cb090-136">The command stores the job object that **Get-Job** returns in the $j variable.</span></span> <span data-ttu-id="cb090-137">In dit voor beeld is er slechts één taak met de opgegeven naam.</span><span class="sxs-lookup"><span data-stu-id="cb090-137">In this example, there is only one job with the specified name.</span></span>

<span data-ttu-id="cb090-138">Met de tweede opdracht wordt de eigenschap **InstanceId** van het object in de variabele $j opgehaald en opgeslagen in de $id variabele.</span><span class="sxs-lookup"><span data-stu-id="cb090-138">The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.</span></span>

<span data-ttu-id="cb090-139">Met de derde opdracht wordt de waarde van de variabele $ID weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cb090-139">The third command displays the value of the $ID variable.</span></span>

<span data-ttu-id="cb090-140">De vierde opdracht maakt gebruik van Stop-Job cmdlet om de taak te stoppen.</span><span class="sxs-lookup"><span data-stu-id="cb090-140">The fourth command uses Stop-Job cmdlet to stop the job.</span></span> <span data-ttu-id="cb090-141">De para meter *InstanceId* wordt gebruikt om de taak en $id variabele te identificeren die de exemplaar-id van de taak vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="cb090-141">It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.</span></span>

### <span data-ttu-id="cb090-142">Voor beeld 3: taken ophalen die een specifieke opdracht bevatten</span><span class="sxs-lookup"><span data-stu-id="cb090-142">Example 3: Get jobs that include a specific command</span></span>

```powershell
Get-Job -Command "*get-process*"
```

<span data-ttu-id="cb090-143">Met deze opdracht worden de taken op het systeem opgehaald die een Get-Process opdracht bevatten.</span><span class="sxs-lookup"><span data-stu-id="cb090-143">This command gets the jobs on the system that include a Get-Process command.</span></span> <span data-ttu-id="cb090-144">De opdracht gebruikt de *opdracht* parameter van **Get-job** om de opgehaalde taken te beperken.</span><span class="sxs-lookup"><span data-stu-id="cb090-144">The command uses the *Command* parameter of **Get-Job** to limit the jobs retrieved.</span></span> <span data-ttu-id="cb090-145">De opdracht gebruikt joker tekens (\*) om taken op te halen die een opdracht **Get-process bevatten,** overal in de opdracht reeks.</span><span class="sxs-lookup"><span data-stu-id="cb090-145">The command uses wildcard characters (\*) to get jobs that include a **Get-Process** command anywhere in the command string.</span></span>

### <span data-ttu-id="cb090-146">Voor beeld 4: taken met een bepaalde opdracht ophalen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="cb090-146">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

```powershell
"*get-process*" | Get-Job
```

<span data-ttu-id="cb090-147">Net als de opdracht in het vorige voor beeld, haalt deze opdracht de taken op het systeem op die een opdracht **Get-process** bevatten.</span><span class="sxs-lookup"><span data-stu-id="cb090-147">Like the command in the previous example, this command gets the jobs on the system that include a **Get-Process** command.</span></span> <span data-ttu-id="cb090-148">De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van een teken reeks tussen aanhalings tekens en de cmdlet **Get-job** .</span><span class="sxs-lookup"><span data-stu-id="cb090-148">The command uses a pipeline operator (|) to send a string, in quotation marks, to the **Get-Job** cmdlet.</span></span> <span data-ttu-id="cb090-149">Dit is het equivalent van de vorige opdracht.</span><span class="sxs-lookup"><span data-stu-id="cb090-149">It is the equivalent of the previous command.</span></span>

### <span data-ttu-id="cb090-150">Voor beeld 5: taken ophalen die niet zijn gestart</span><span class="sxs-lookup"><span data-stu-id="cb090-150">Example 5: Get jobs that have not been started</span></span>

```powershell
Get-Job -State NotStarted
```

<span data-ttu-id="cb090-151">Met deze opdracht worden alleen de taken opgehaald die zijn gemaakt, maar die nog niet zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="cb090-151">This command gets only those jobs that have been created but have not yet been started.</span></span>
<span data-ttu-id="cb090-152">Dit omvat taken die in de toekomst zijn gepland en die nog niet zijn gepland.</span><span class="sxs-lookup"><span data-stu-id="cb090-152">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

### <span data-ttu-id="cb090-153">Voor beeld 6: taken ophalen waaraan geen naam is toegewezen</span><span class="sxs-lookup"><span data-stu-id="cb090-153">Example 6: Get jobs that have not been assigned a name</span></span>

```powershell
Get-Job -Name Job*
```

<span data-ttu-id="cb090-154">Met deze opdracht worden alle taken opgehaald die met taak namen beginnen.</span><span class="sxs-lookup"><span data-stu-id="cb090-154">This command gets all jobs that have job names that begin with job.</span></span>
<span data-ttu-id="cb090-155">Omdat taak \<number\> de standaard naam voor een taak is, worden met deze opdracht alle taken opgehaald die geen expliciet toegewezen naam hebben.</span><span class="sxs-lookup"><span data-stu-id="cb090-155">Because job\<number\> is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

### <span data-ttu-id="cb090-156">Voor beeld 7: een taak object gebruiken om de taak in een opdracht weer te geven</span><span class="sxs-lookup"><span data-stu-id="cb090-156">Example 7: Use a job object to represent the job in a command</span></span>

<span data-ttu-id="cb090-157">In dit voor beeld ziet u hoe u **Get-job** kunt gebruiken om een taak object op te halen. vervolgens ziet u hoe u het taak object kunt gebruiken om de taak in een opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cb090-157">This example shows how to use **Get-Job** to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process} -Name MyJob
$j = Get-Job -Name MyJob
$j
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process
```

```powershell
Receive-Job -Job $j
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

<span data-ttu-id="cb090-158">De eerste opdracht maakt gebruik van de cmdlet **Start-job** om een achtergrond taak te starten die een **Get-process-** opdracht uitvoert op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="cb090-158">The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer.</span></span> <span data-ttu-id="cb090-159">De opdracht gebruikt de para meter *name* van **Start-job** om een beschrijvende naam toe te wijzen aan de taak.</span><span class="sxs-lookup"><span data-stu-id="cb090-159">The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.</span></span>

<span data-ttu-id="cb090-160">De tweede opdracht maakt gebruik van Get-Job om de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb090-160">The second command uses Get-Job to get the job.</span></span> <span data-ttu-id="cb090-161">De para meter *name* van **Get-job** wordt gebruikt om de taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="cb090-161">It uses the *Name* parameter of **Get-Job** to identify the job.</span></span> <span data-ttu-id="cb090-162">De opdracht slaat het resulterende taak object op in de variabele $j.</span><span class="sxs-lookup"><span data-stu-id="cb090-162">The command saves the resulting job object in the $j variable.</span></span>

<span data-ttu-id="cb090-163">Met de derde opdracht wordt de waarde van het taak object weer gegeven in de variabele $j.</span><span class="sxs-lookup"><span data-stu-id="cb090-163">The third command displays the value of the job object in the $j variable.</span></span> <span data-ttu-id="cb090-164">De waarde van de **status** eigenschap geeft aan dat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="cb090-164">The value of the **State** property shows that the job is completed.</span></span> <span data-ttu-id="cb090-165">De waarde van de eigenschap **HasMoreData** geeft aan dat er resultaten beschikbaar zijn van de taak die nog niet zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cb090-165">The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.</span></span>

<span data-ttu-id="cb090-166">De vierde opdracht maakt gebruik van de cmdlet **Receive-job** om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb090-166">The fourth command uses the **Receive-Job** cmdlet to get the results of the job.</span></span> <span data-ttu-id="cb090-167">Het taak object in de variabele $j wordt gebruikt om de taak te vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="cb090-167">It uses the job object in the $j variable to represent the job.</span></span> <span data-ttu-id="cb090-168">U kunt ook een pijplijn operator gebruiken om een taak object te verzenden naar **Receive-job**.</span><span class="sxs-lookup"><span data-stu-id="cb090-168">You can also use a pipeline operator to send a job object to **Receive-Job**.</span></span>

### <span data-ttu-id="cb090-169">Voor beeld 8: alle taken ophalen, inclusief taken die met een andere methode zijn gestart</span><span class="sxs-lookup"><span data-stu-id="cb090-169">Example 8: Get all jobs including jobs started by a different method</span></span>

<span data-ttu-id="cb090-170">In dit voor beeld wordt gedemonstreerd dat de cmdlet **Get-job** alle taken kan ophalen die in de huidige sessie zijn gestart, zelfs als deze zijn gestart door verschillende methoden te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cb090-170">This example demonstrates that the **Get-Job** cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

```powershell
Start-Job -ScriptBlock {Get-EventLog System}
Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Get-Job
```

```Output
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System
```

```powershell
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
```

```Output
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

<span data-ttu-id="cb090-171">De eerste opdracht maakt gebruik van de cmdlet **Start-job** om een taak op de lokale computer te starten.</span><span class="sxs-lookup"><span data-stu-id="cb090-171">The first command uses the **Start-Job** cmdlet to start a job on the local computer.</span></span>

<span data-ttu-id="cb090-172">De tweede opdracht maakt gebruik van de para meter *AsJob* van de cmdlet **invoke-opdracht** om een taak op de computer S1 te starten.</span><span class="sxs-lookup"><span data-stu-id="cb090-172">The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer.</span></span> <span data-ttu-id="cb090-173">Hoewel de opdrachten in de taak worden uitgevoerd op de externe computer, wordt het taak object gemaakt op de lokale computer, dus u kunt lokale opdrachten gebruiken om de taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="cb090-173">Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.</span></span>

<span data-ttu-id="cb090-174">De derde opdracht maakt gebruik van de cmdlet **invoke-opdracht** om een **Start-taak** opdracht uit te voeren op de S2-computer.</span><span class="sxs-lookup"><span data-stu-id="cb090-174">The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer.</span></span> <span data-ttu-id="cb090-175">Met deze methode wordt het taak object op de externe computer gemaakt, zodat u externe opdrachten gebruikt om de taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="cb090-175">By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.</span></span>

<span data-ttu-id="cb090-176">De vierde opdracht gebruikt **Get-job** om de taken op de lokale computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb090-176">The fourth command uses **Get-Job** to get the jobs stored on the local computer.</span></span> <span data-ttu-id="cb090-177">De eigenschap **PSJobTypeName** van taken, geïntroduceerd in Windows power Shell 3,0, laat zien dat de lokale taak is gestart met de cmdlet **Start-job** een achtergrond taak is en de taak is gestart in een externe sessie met behulp van de cmdlet **invoke-opdracht** is een externe taak.</span><span class="sxs-lookup"><span data-stu-id="cb090-177">The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.</span></span>

<span data-ttu-id="cb090-178">De vijfde opdracht gebruikt u **invoke-opdracht** om een opdracht **Get-job** uit te voeren op de S2-computer. De voorbeeld uitvoer toont de resultaten van de Get-Job opdracht.</span><span class="sxs-lookup"><span data-stu-id="cb090-178">The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command.</span></span> <span data-ttu-id="cb090-179">Op de computer S2 lijkt de taak een lokale taak te zijn.</span><span class="sxs-lookup"><span data-stu-id="cb090-179">On the S2 computer, the job appears to be a local job.</span></span> <span data-ttu-id="cb090-180">De computer naam is localhost en het taak type is een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="cb090-180">The computer name is localhost and the job type is a background job.</span></span>

<span data-ttu-id="cb090-181">Zie about_Remote_Jobs voor meer informatie over het uitvoeren van achtergrond taken op externe computers.</span><span class="sxs-lookup"><span data-stu-id="cb090-181">For more information about how to run background jobs on remote computers, see about_Remote_Jobs.</span></span>

### <span data-ttu-id="cb090-182">Voor beeld 9: een mislukte taak onderzoeken</span><span class="sxs-lookup"><span data-stu-id="cb090-182">Example 9: Investigate a failed job</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

```Output
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process
```

```powershell
(Get-Job).JobStateInfo | Format-List -Property *
```

```Output
State  : Failed
Reason :
```

```powershell
Get-Job | Format-List -Property *
```

```Output
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
```

```powershell
(Get-Job -Name job2).JobStateInfo.Reason
```

```Output
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.

For information about requirements for remoting in PowerShell, see about_Remote_Requirements. For
troubleshooting tips, see about_Remote_Troubleshooting.
```

<span data-ttu-id="cb090-183">Met deze opdracht wordt uitgelegd hoe u het taak object gebruikt dat **Get-job** retourneert om te onderzoeken waarom een taak is mislukt.</span><span class="sxs-lookup"><span data-stu-id="cb090-183">This command shows how to use the job object that **Get-Job** returns to investigate why a job failed.</span></span>
<span data-ttu-id="cb090-184">Ook wordt uitgelegd hoe u de onderliggende taken van elke taak kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="cb090-184">It also shows how to get the child jobs of each job.</span></span>

<span data-ttu-id="cb090-185">De eerste opdracht maakt gebruik van de cmdlet **Start-job** om een taak op de lokale computer te starten.</span><span class="sxs-lookup"><span data-stu-id="cb090-185">The first command uses the **Start-Job** cmdlet to start a job on the local computer.</span></span> <span data-ttu-id="cb090-186">Het taak object dat **Start taak retourneert,** geeft aan dat de taak is mislukt.</span><span class="sxs-lookup"><span data-stu-id="cb090-186">The job object that **Start-Job** returns shows that the job failed.</span></span> <span data-ttu-id="cb090-187">De waarde van de **status** eigenschap is mislukt.</span><span class="sxs-lookup"><span data-stu-id="cb090-187">The value of the **State** property is Failed.</span></span>

<span data-ttu-id="cb090-188">De tweede opdracht maakt gebruik van de cmdlet **Get-job** om de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb090-188">The second command uses the **Get-Job** cmdlet to get the job.</span></span> <span data-ttu-id="cb090-189">De opdracht gebruikt de punt methode om de waarde van de eigenschap **JobStateInfo** van het object op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb090-189">The command uses the dot method to get the value of the **JobStateInfo** property of the object.</span></span> <span data-ttu-id="cb090-190">Er wordt een pijplijn operator gebruikt voor het verzenden van het object in de eigenschap **JobStateInfo** naar de cmdlet Format-List, waarmee alle eigenschappen van het object (\*) in een lijst worden opgemaakt. Het resultaat van de **indeling-lijst** opdracht laat zien dat de waarde van de eigenschap **reason** van de taak leeg is.</span><span class="sxs-lookup"><span data-stu-id="cb090-190">It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (\*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.</span></span>

<span data-ttu-id="cb090-191">De derde opdracht onderzoekt meer.</span><span class="sxs-lookup"><span data-stu-id="cb090-191">The third command investigates more.</span></span> <span data-ttu-id="cb090-192">Er wordt een opdracht **Get-job** gebruikt om de taak op te halen en vervolgens een pijplijn operator gebruikt om het hele taak object te verzenden naar de **indelings lijst-** cmdlet, waarin alle eigenschappen van de taak in een lijst worden weer gegeven. De weer gave van alle eigenschappen in het taak object toont aan dat de taak een onderliggende taak bevat met de naam Job2.</span><span class="sxs-lookup"><span data-stu-id="cb090-192">It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.</span></span>

<span data-ttu-id="cb090-193">De vierde opdracht gebruikt **Get-job** om het taak object op te halen dat de onderliggende taak Job2 vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="cb090-193">The fourth command uses **Get-Job** to get the job object that represents the Job2 child job.</span></span> <span data-ttu-id="cb090-194">Dit is de taak waarin de opdracht daad werkelijk wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cb090-194">This is the job in which the command actually ran.</span></span> <span data-ttu-id="cb090-195">De punt methode wordt gebruikt om de eigenschap **reason** van de eigenschap **JobStateInfo** op te halen. Het resultaat toont aan dat de taak is mislukt vanwege een fout bij de toegang geweigerd.</span><span class="sxs-lookup"><span data-stu-id="cb090-195">It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error.</span></span> <span data-ttu-id="cb090-196">In dit geval is de gebruiker verg eten de optie als administrator uitvoeren te gebruiken bij het starten van Power shell. omdat achtergrond taken gebruikmaken van de externe functies van Power shell, moet de computer zijn geconfigureerd voor externe toegang om een taak uit te voeren, zelfs wanneer de taak wordt uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="cb090-196">In this case, the user forgot to use the Run as administrator option when starting PowerShell.Because background jobs use the remoting features of PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.</span></span>

### <span data-ttu-id="cb090-197">Voor beeld 10: gefilterde resultaten ophalen</span><span class="sxs-lookup"><span data-stu-id="cb090-197">Example 10: Get filtered results</span></span>

<span data-ttu-id="cb090-198">In dit voor beeld ziet u hoe u de *filter* parameter gebruikt om een werk stroom taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb090-198">This example shows how to use the *Filter* parameter to get a workflow job.</span></span>
<span data-ttu-id="cb090-199">De *filter* parameter, die is geïntroduceerd in Windows power Shell 3,0, is alleen geldig voor aangepaste taak typen, zoals werk stroom taken en geplande taken.</span><span class="sxs-lookup"><span data-stu-id="cb090-199">The *Filter* parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

```powershell
Workflow WFProcess {Get-Process}
WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
Get-Job -Filter @{MyCustomId = 92107}
```

```Output
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

<span data-ttu-id="cb090-200">Met de eerste opdracht wordt het sleutel woord **workflow** gebruikt om de WFProcess-werk stroom te maken.</span><span class="sxs-lookup"><span data-stu-id="cb090-200">The first command uses the **Workflow** keyword to create the WFProcess workflow.</span></span>

<span data-ttu-id="cb090-201">De tweede opdracht maakt gebruik van de para meter *AsJob* van de WFProcess-werk stroom om de werk stroom als een achtergrond taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="cb090-201">The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job.</span></span> <span data-ttu-id="cb090-202">De para meter *JobName* van de werk stroom wordt gebruikt om een naam voor de taak op te geven en de para meter *PSPrivateMetadata* van de werk stroom om een aangepaste ID op te geven.</span><span class="sxs-lookup"><span data-stu-id="cb090-202">It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.</span></span>

<span data-ttu-id="cb090-203">De derde opdracht gebruikt de *filter* parameter van **Get-job** om de taak op te halen op basis van een aangepaste id die is opgegeven in de para meter *PSPrivateMetadata* .</span><span class="sxs-lookup"><span data-stu-id="cb090-203">The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.</span></span>

### <span data-ttu-id="cb090-204">Voor beeld 11: informatie over onderliggende taken ophalen</span><span class="sxs-lookup"><span data-stu-id="cb090-204">Example 11: Get information about child jobs</span></span>

<span data-ttu-id="cb090-205">In dit voor beeld ziet u het effect van het gebruik van de para meters *IncludeChildJob* en *ChildJobState* van de cmdlet **Get-job** .</span><span class="sxs-lookup"><span data-stu-id="cb090-205">This example shows the effect of using the *IncludeChildJob* and *ChildJobState* parameters of the **Get-Job** cmdlet.</span></span>

```powershell
Get-Job
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
Get-Job -IncludeChildJob
```

```Output
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
```

```powershell
Get-Job -Name Job4 -ChildJobState Failed
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
(Get-Job -Name Job5).JobStateInfo.Reason
```

```Output
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

<span data-ttu-id="cb090-206">Met de eerste opdracht worden de taken in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cb090-206">The first command gets the jobs in the current session.</span></span> <span data-ttu-id="cb090-207">De uitvoer bevat een achtergrond taak, een externe taak en verschillende exemplaren van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="cb090-207">The output includes a background job, a remote job and several instances of a scheduled job.</span></span> <span data-ttu-id="cb090-208">De externe taak Job4 lijkt te zijn mislukt.</span><span class="sxs-lookup"><span data-stu-id="cb090-208">The remote job, Job4, appears to have failed.</span></span>

<span data-ttu-id="cb090-209">De tweede opdracht maakt gebruik van de para meter *IncludeChildJob* van **Get-job**.</span><span class="sxs-lookup"><span data-stu-id="cb090-209">The second command uses the *IncludeChildJob* parameter of **Get-Job**.</span></span> <span data-ttu-id="cb090-210">Met de uitvoer worden de onderliggende taken van alle taken met onderliggende taken toegevoegd. In dit geval toont de gereviseerde uitvoer alleen dat de onderliggende Job5-taak van Job4 is mislukt.</span><span class="sxs-lookup"><span data-stu-id="cb090-210">The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.</span></span>

<span data-ttu-id="cb090-211">De derde opdracht gebruikt de para meter *ChildJobState* met de waarde mislukt. de uitvoer bevat alle bovenliggende taken en alleen de onderliggende taken die zijn mislukt.</span><span class="sxs-lookup"><span data-stu-id="cb090-211">The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.</span></span>

<span data-ttu-id="cb090-212">De vierde opdracht maakt gebruik van de eigenschap **JobStateInfo** van Jobs en de eigenschap **reason** om te ontdekken waarom Job5 is mislukt.</span><span class="sxs-lookup"><span data-stu-id="cb090-212">The fourth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.</span></span>

## <span data-ttu-id="cb090-213">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cb090-213">PARAMETERS</span></span>

### <span data-ttu-id="cb090-214">-Na</span><span class="sxs-lookup"><span data-stu-id="cb090-214">-After</span></span>

<span data-ttu-id="cb090-215">Hiermee worden voltooide taken opgehaald die zijn beëindigd na de opgegeven datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="cb090-215">Gets completed jobs that ended after the specified date and time.</span></span> <span data-ttu-id="cb090-216">Voer een **DateTime** -object in, bijvoorbeeld een waarde die wordt geretourneerd door de Get-Date cmdlet of een teken reeks die kan worden geconverteerd naar een **DateTime** -object, zoals `Dec 1, 2012 2:00 AM` of `11/06` .</span><span class="sxs-lookup"><span data-stu-id="cb090-216">Enter a **DateTime** object, such as one returned by the Get-Date cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="cb090-217">Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken, die een eigenschap **EndTime** hebben.</span><span class="sxs-lookup"><span data-stu-id="cb090-217">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="cb090-218">Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .</span><span class="sxs-lookup"><span data-stu-id="cb090-218">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span> <span data-ttu-id="cb090-219">Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="cb090-219">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="cb090-220">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cb090-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb090-221">-Vóór</span><span class="sxs-lookup"><span data-stu-id="cb090-221">-Before</span></span>

<span data-ttu-id="cb090-222">Hiermee worden voltooide taken opgehaald die voor de opgegeven datum en tijd zijn beëindigd.</span><span class="sxs-lookup"><span data-stu-id="cb090-222">Gets completed jobs that ended before the specified date and time.</span></span>
<span data-ttu-id="cb090-223">Voer een **DateTime** -object in.</span><span class="sxs-lookup"><span data-stu-id="cb090-223">Enter a **DateTime** object.</span></span>

<span data-ttu-id="cb090-224">Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken, die een eigenschap **EndTime** hebben.</span><span class="sxs-lookup"><span data-stu-id="cb090-224">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="cb090-225">Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .</span><span class="sxs-lookup"><span data-stu-id="cb090-225">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span> <span data-ttu-id="cb090-226">Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="cb090-226">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="cb090-227">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cb090-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb090-228">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="cb090-228">-ChildJobState</span></span>

<span data-ttu-id="cb090-229">Hiermee worden alleen de onderliggende taken met de opgegeven status opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cb090-229">Gets only the child jobs that have the specified state.</span></span>
<span data-ttu-id="cb090-230">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="cb090-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cb090-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="cb090-231">NotStarted</span></span>
- <span data-ttu-id="cb090-232">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="cb090-232">Running</span></span>
- <span data-ttu-id="cb090-233">Voltooid</span><span class="sxs-lookup"><span data-stu-id="cb090-233">Completed</span></span>
- <span data-ttu-id="cb090-234">Mislukt</span><span class="sxs-lookup"><span data-stu-id="cb090-234">Failed</span></span>
- <span data-ttu-id="cb090-235">Gestopt</span><span class="sxs-lookup"><span data-stu-id="cb090-235">Stopped</span></span>
- <span data-ttu-id="cb090-236">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="cb090-236">Blocked</span></span>
- <span data-ttu-id="cb090-237">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="cb090-237">Suspended</span></span>
- <span data-ttu-id="cb090-238">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="cb090-238">Disconnected</span></span>
- <span data-ttu-id="cb090-239">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="cb090-239">Suspending</span></span>
- <span data-ttu-id="cb090-240">Stoppen</span><span class="sxs-lookup"><span data-stu-id="cb090-240">Stopping</span></span>

<span data-ttu-id="cb090-241">**Get-job** krijgt standaard geen onderliggende taken.</span><span class="sxs-lookup"><span data-stu-id="cb090-241">By default, **Get-Job** does not get child jobs.</span></span>
<span data-ttu-id="cb090-242">Met behulp van de *IncludeChildJob* para meter **Get-job** worden alle onderliggende taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cb090-242">By using the *IncludeChildJob* parameter, **Get-Job** gets all child jobs.</span></span>
<span data-ttu-id="cb090-243">Als u de para meter *ChildJobState* gebruikt, heeft de para meter *IncludeChildJob* geen effect.</span><span class="sxs-lookup"><span data-stu-id="cb090-243">If you use the *ChildJobState* parameter, the *IncludeChildJob* parameter has no effect.</span></span>

<span data-ttu-id="cb090-244">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cb090-244">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb090-245">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="cb090-245">-Command</span></span>

<span data-ttu-id="cb090-246">Geeft een matrix van opdrachten aan als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="cb090-246">Specifies an array of commands as strings.</span></span>
<span data-ttu-id="cb090-247">Met deze cmdlet worden de taken opgehaald die de opgegeven opdrachten bevatten.</span><span class="sxs-lookup"><span data-stu-id="cb090-247">This cmdlet gets the jobs that include the specified commands.</span></span>
<span data-ttu-id="cb090-248">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="cb090-248">The default is all jobs.</span></span>
<span data-ttu-id="cb090-249">U kunt joker tekens gebruiken om een opdracht patroon op te geven.</span><span class="sxs-lookup"><span data-stu-id="cb090-249">You can use wildcard characters to specify a command pattern.</span></span>

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

### <span data-ttu-id="cb090-250">-Filter</span><span class="sxs-lookup"><span data-stu-id="cb090-250">-Filter</span></span>

<span data-ttu-id="cb090-251">Hiermee geeft u een hash-tabel met voor waarden op.</span><span class="sxs-lookup"><span data-stu-id="cb090-251">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="cb090-252">Met deze cmdlet worden taken opgehaald die voldoen aan alle voor waarden.</span><span class="sxs-lookup"><span data-stu-id="cb090-252">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="cb090-253">Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="cb090-253">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="cb090-254">Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken.</span><span class="sxs-lookup"><span data-stu-id="cb090-254">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="cb090-255">Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .</span><span class="sxs-lookup"><span data-stu-id="cb090-255">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="cb090-256">Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="cb090-256">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="cb090-257">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cb090-257">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="cb090-258">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="cb090-258">-HasMoreData</span></span>

<span data-ttu-id="cb090-259">Hiermee wordt aangegeven of met deze cmdlet alleen taken worden opgehaald die de opgegeven waarde voor de eigenschap **HasMoreData** hebben.</span><span class="sxs-lookup"><span data-stu-id="cb090-259">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="cb090-260">De eigenschap **HasMoreData** geeft aan of alle taak resultaten zijn ontvangen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="cb090-260">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span>
<span data-ttu-id="cb090-261">Als u taken met meer resultaten wilt ophalen, geeft u de waarde $True op.</span><span class="sxs-lookup"><span data-stu-id="cb090-261">To get jobs that have more results, specify a value of $True.</span></span>
<span data-ttu-id="cb090-262">Als u taken wilt ophalen die niet meer resultaten hebben, geeft u de waarde $False op.</span><span class="sxs-lookup"><span data-stu-id="cb090-262">To get jobs that do not have more results, specify a value of $False.</span></span>

<span data-ttu-id="cb090-263">Gebruik de cmdlet Receive-Job om de resultaten van een taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb090-263">To get the results of a job, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="cb090-264">Wanneer u de cmdlet **Receive-job** gebruikt, wordt deze verwijderd uit de in-Memory, sessie-specifieke opslag de geretourneerde resultaten.</span><span class="sxs-lookup"><span data-stu-id="cb090-264">When you use the **Receive-Job** cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span> <span data-ttu-id="cb090-265">Wanneer het alle resultaten van de taak in de huidige sessie heeft geretourneerd, wordt de waarde van de eigenschap **HasMoreData** van de taak ingesteld op $false) om aan te geven dat deze geen resultaten meer heeft voor de taak in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="cb090-265">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to $False) to indicate that it has no more results for the job in the current session.</span></span> <span data-ttu-id="cb090-266">Gebruik de *para* meter van **Receive-job** om te voor komen dat de **functie receive** results verwijdert en de waarde van de eigenschap **HasMoreData** wijzigt.</span><span class="sxs-lookup"><span data-stu-id="cb090-266">Use the *Keep* parameter of **Receive-Job** to prevent **Receive-Job** from deleting results and changing the value of the **HasMoreData** property.</span></span> <span data-ttu-id="cb090-267">Typ `Get-Help Receive-Job` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cb090-267">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="cb090-268">De eigenschap **HasMoreData** is specifiek voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="cb090-268">The **HasMoreData** property is specific to the current session.</span></span> <span data-ttu-id="cb090-269">Als de resultaten voor een aangepast taak type buiten de sessie worden opgeslagen, zoals het type geplande taak, waarmee taak resultaten op schijf worden opgeslagen, kunt u de cmdlet **Receive-job** in een andere sessie gebruiken om de taak resultaten opnieuw op te halen, zelfs als de waarde van **HasMoreData** is $False.</span><span class="sxs-lookup"><span data-stu-id="cb090-269">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the **Receive-Job** cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is $False.</span></span> <span data-ttu-id="cb090-270">Zie de Help-onderwerpen voor het aangepaste taak type voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cb090-270">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="cb090-271">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cb090-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb090-272">-Id</span><span class="sxs-lookup"><span data-stu-id="cb090-272">-Id</span></span>

<span data-ttu-id="cb090-273">Hiermee wordt een matrix met Id's opgegeven van taken die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cb090-273">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="cb090-274">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="cb090-274">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="cb090-275">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="cb090-275">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="cb090-276">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="cb090-276">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="cb090-277">Als u de ID van een taak wilt zoeken, typt u `Get-Job` zonder para meters.</span><span class="sxs-lookup"><span data-stu-id="cb090-277">To find the ID of a job, type `Get-Job` without parameters.</span></span>

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

### <span data-ttu-id="cb090-278">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="cb090-278">-IncludeChildJob</span></span>

<span data-ttu-id="cb090-279">Geeft aan dat deze cmdlet onderliggende taken retourneert, naast de bovenliggende taken.</span><span class="sxs-lookup"><span data-stu-id="cb090-279">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="cb090-280">Deze para meter is vooral nuttig voor het onderzoeken van werk stroom taken, waarvoor **Get-job** een bovenliggende container taak en taak fouten retourneert, omdat de reden voor de fout wordt opgeslagen in een eigenschap van de onderliggende taak.</span><span class="sxs-lookup"><span data-stu-id="cb090-280">This parameter is especially useful for investigating workflow jobs, for which **Get-Job** returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="cb090-281">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cb090-281">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb090-282">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="cb090-282">-InstanceId</span></span>

<span data-ttu-id="cb090-283">Hiermee geeft u een matrix met exemplaar-Id's van taken op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cb090-283">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="cb090-284">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="cb090-284">The default is all jobs.</span></span>

<span data-ttu-id="cb090-285">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="cb090-285">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="cb090-286">Gebruik **Get-job** om de exemplaar-id van een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="cb090-286">To find the instance ID of a job, use **Get-Job**.</span></span>

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

### <span data-ttu-id="cb090-287">-Name</span><span class="sxs-lookup"><span data-stu-id="cb090-287">-Name</span></span>

<span data-ttu-id="cb090-288">Hiermee geeft u een matrix met beschrijvende namen van taken op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cb090-288">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="cb090-289">Voer een taak naam in of gebruik joker tekens om een job name-patroon in te voeren.</span><span class="sxs-lookup"><span data-stu-id="cb090-289">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span>
<span data-ttu-id="cb090-290">**Get-job** haalt standaard alle taken in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="cb090-290">By default, **Get-Job** gets all jobs in the current session.</span></span>

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

### <span data-ttu-id="cb090-291">-Nieuwste</span><span class="sxs-lookup"><span data-stu-id="cb090-291">-Newest</span></span>

<span data-ttu-id="cb090-292">Hiermee geeft u een aantal taken op dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cb090-292">Specifies a number of jobs to get.</span></span>
<span data-ttu-id="cb090-293">Met deze cmdlet worden de taken opgehaald die het meest recent zijn beëindigd.</span><span class="sxs-lookup"><span data-stu-id="cb090-293">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="cb090-294">De *nieuwste* para meter sorteert of retourneert de nieuwste taken niet in de volg orde van de eind tijd.</span><span class="sxs-lookup"><span data-stu-id="cb090-294">The *Newest* parameter does not sort or return the newest jobs in end-time order.</span></span>
<span data-ttu-id="cb090-295">Als u de uitvoer wilt sorteren, gebruikt u de cmdlet Sort-Object.</span><span class="sxs-lookup"><span data-stu-id="cb090-295">To sort the output, use the Sort-Object cmdlet.</span></span>

<span data-ttu-id="cb090-296">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cb090-296">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb090-297">-Status</span><span class="sxs-lookup"><span data-stu-id="cb090-297">-State</span></span>

<span data-ttu-id="cb090-298">Hiermee geeft u een taak status op.</span><span class="sxs-lookup"><span data-stu-id="cb090-298">Specifies a job state.</span></span>
<span data-ttu-id="cb090-299">Met deze cmdlet worden alleen taken in de opgegeven status opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cb090-299">This cmdlet gets only jobs in the specified state.</span></span>
<span data-ttu-id="cb090-300">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="cb090-300">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cb090-301">NotStarted</span><span class="sxs-lookup"><span data-stu-id="cb090-301">NotStarted</span></span>
- <span data-ttu-id="cb090-302">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="cb090-302">Running</span></span>
- <span data-ttu-id="cb090-303">Voltooid</span><span class="sxs-lookup"><span data-stu-id="cb090-303">Completed</span></span>
- <span data-ttu-id="cb090-304">Mislukt</span><span class="sxs-lookup"><span data-stu-id="cb090-304">Failed</span></span>
- <span data-ttu-id="cb090-305">Gestopt</span><span class="sxs-lookup"><span data-stu-id="cb090-305">Stopped</span></span>
- <span data-ttu-id="cb090-306">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="cb090-306">Blocked</span></span>
- <span data-ttu-id="cb090-307">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="cb090-307">Suspended</span></span>
- <span data-ttu-id="cb090-308">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="cb090-308">Disconnected</span></span>
- <span data-ttu-id="cb090-309">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="cb090-309">Suspending</span></span>
- <span data-ttu-id="cb090-310">Stoppen</span><span class="sxs-lookup"><span data-stu-id="cb090-310">Stopping</span></span>

<span data-ttu-id="cb090-311">**Get-job** haalt standaard alle taken in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="cb090-311">By default, **Get-Job** gets all the jobs in the current session.</span></span>

<span data-ttu-id="cb090-312">Zie [JobState Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.jobstate) in de MSDN-bibliotheek voor meer informatie over de status van de taak.</span><span class="sxs-lookup"><span data-stu-id="cb090-312">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="cb090-313">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cb090-313">CommonParameters</span></span>

<span data-ttu-id="cb090-314">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cb090-314">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cb090-315">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cb090-315">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cb090-316">INVOER</span><span class="sxs-lookup"><span data-stu-id="cb090-316">INPUTS</span></span>

### <span data-ttu-id="cb090-317">Geen</span><span class="sxs-lookup"><span data-stu-id="cb090-317">None</span></span>

<span data-ttu-id="cb090-318">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cb090-318">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="cb090-319">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cb090-319">OUTPUTS</span></span>

### <span data-ttu-id="cb090-320">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="cb090-320">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="cb090-321">Deze cmdlet retourneert objecten die de taken in de sessie vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="cb090-321">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="cb090-322">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cb090-322">NOTES</span></span>

* <span data-ttu-id="cb090-323">De eigenschap **PSJobTypeName** van taken geeft het taak type van de taak aan.</span><span class="sxs-lookup"><span data-stu-id="cb090-323">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="cb090-324">De waarde van de eigenschap wordt bepaald door de auteur van het taak type.</span><span class="sxs-lookup"><span data-stu-id="cb090-324">The property value is determined by the job type author.</span></span> <span data-ttu-id="cb090-325">De volgende lijst bevat algemene taak typen.</span><span class="sxs-lookup"><span data-stu-id="cb090-325">The following list shows common job types.</span></span>

  - <span data-ttu-id="cb090-326">**BackgroundJob**.</span><span class="sxs-lookup"><span data-stu-id="cb090-326">**BackgroundJob**.</span></span>
<span data-ttu-id="cb090-327">De lokale taak is gestart met **het starten** van de taak.</span><span class="sxs-lookup"><span data-stu-id="cb090-327">Local job started by using **Start-Job**.</span></span>

  - <span data-ttu-id="cb090-328">**RemoteJob**.</span><span class="sxs-lookup"><span data-stu-id="cb090-328">**RemoteJob**.</span></span>
<span data-ttu-id="cb090-329">De taak is gestart in een **PSSession** met de para meter *AsJob* van de cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="cb090-329">Job started in a **PSSession** by using the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>

  - <span data-ttu-id="cb090-330">**PSWorkflowJob**.</span><span class="sxs-lookup"><span data-stu-id="cb090-330">**PSWorkflowJob**.</span></span>
<span data-ttu-id="cb090-331">De taak is gestart met de gemeen schappelijke para meter *AsJob* van werk stromen.</span><span class="sxs-lookup"><span data-stu-id="cb090-331">Job started by using the *AsJob* common parameter of workflows.</span></span>

## <span data-ttu-id="cb090-332">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cb090-332">RELATED LINKS</span></span>

[<span data-ttu-id="cb090-333">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="cb090-333">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="cb090-334">Receive-job</span><span class="sxs-lookup"><span data-stu-id="cb090-334">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="cb090-335">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="cb090-335">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="cb090-336">Begin taak</span><span class="sxs-lookup"><span data-stu-id="cb090-336">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="cb090-337">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="cb090-337">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="cb090-338">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="cb090-338">Wait-Job</span></span>](Wait-Job.md)
