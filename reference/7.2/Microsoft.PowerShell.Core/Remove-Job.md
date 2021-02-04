---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: 52613dae3ba73227818c6c0dec40183ba20ce2a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706048"
---
# <span data-ttu-id="efa92-102">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="efa92-102">Remove-Job</span></span>

## <span data-ttu-id="efa92-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="efa92-103">SYNOPSIS</span></span>
<span data-ttu-id="efa92-104">Hiermee verwijdert u een Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="efa92-104">Deletes a PowerShell background job.</span></span>

## <span data-ttu-id="efa92-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="efa92-105">SYNTAX</span></span>

### <span data-ttu-id="efa92-106">SessionIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="efa92-106">SessionIdParameterSet (Default)</span></span>

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="efa92-107">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="efa92-107">JobParameterSet</span></span>

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="efa92-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="efa92-108">NameParameterSet</span></span>

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="efa92-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="efa92-109">InstanceIdParameterSet</span></span>

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="efa92-110">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="efa92-110">FilterParameterSet</span></span>

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="efa92-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="efa92-111">StateParameterSet</span></span>

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="efa92-112">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="efa92-112">CommandParameterSet</span></span>

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="efa92-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="efa92-113">DESCRIPTION</span></span>

<span data-ttu-id="efa92-114">De `Remove-Job` cmdlet verwijdert Power shell-achtergrond taken die zijn gestart door de `Start-Job` cmdlet of door cmdlets zoals `Invoke-Command` die ondersteuning bieden voor de para meter **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="efa92-114">The `Remove-Job` cmdlet deletes PowerShell background jobs that were started by the `Start-Job` cmdlet or by cmdlets such as `Invoke-Command` that support the **AsJob** parameter.</span></span>

<span data-ttu-id="efa92-115">U kunt gebruiken `Remove-Job` om alle taken te verwijderen of geselecteerde taken te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="efa92-115">You can use `Remove-Job` to delete all jobs or delete selected jobs.</span></span> <span data-ttu-id="efa92-116">De taken worden geïdentificeerd aan de hand van hun **naam**, **ID**, **exemplaar-id**, **opdracht** of **status**.</span><span class="sxs-lookup"><span data-stu-id="efa92-116">The jobs are identified by their **Name**, **ID**, **Instance ID**, **Command**, or **State**.</span></span> <span data-ttu-id="efa92-117">U kunt ook een taak object omlaag naar de pijp lijn verzenden `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="efa92-117">Or, a job object can be sent down the pipeline to `Remove-Job`.</span></span> <span data-ttu-id="efa92-118">Zonder para meters of parameter waarden `Remove-Job` heeft geen effect.</span><span class="sxs-lookup"><span data-stu-id="efa92-118">Without parameters or parameter values, `Remove-Job` has no effect.</span></span>

<span data-ttu-id="efa92-119">Sinds Power Shell 3,0 `Remove-Job` kunnen aangepaste taak typen, zoals geplande taken en werk stroom taken, verwijderen.</span><span class="sxs-lookup"><span data-stu-id="efa92-119">Since PowerShell 3.0, `Remove-Job` can delete custom job types, such as scheduled jobs and workflow jobs.</span></span> <span data-ttu-id="efa92-120">`Remove-Job`Hiermee verwijdert u bijvoorbeeld de geplande taak, alle exemplaren van de geplande taak op schijf en de resultaten van alle geactiveerde taak exemplaren.</span><span class="sxs-lookup"><span data-stu-id="efa92-120">For example, `Remove-Job` deletes the scheduled job, all instances of the scheduled job on disk, and the results of all triggered job instances.</span></span>

<span data-ttu-id="efa92-121">Als u probeert een actieve taak te verwijderen, `Remove-Job` mislukt de bewerking.</span><span class="sxs-lookup"><span data-stu-id="efa92-121">If you try to delete a running job, `Remove-Job` fails.</span></span> <span data-ttu-id="efa92-122">Gebruik de `Stop-Job` cmdlet om een actieve taak te stoppen.</span><span class="sxs-lookup"><span data-stu-id="efa92-122">Use the `Stop-Job` cmdlet to stop a running job.</span></span> <span data-ttu-id="efa92-123">Of gebruik `Remove-Job` met de para meter **Force** om een actieve taak te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="efa92-123">Or, use `Remove-Job` with the **Force** parameter to delete a running job.</span></span>

<span data-ttu-id="efa92-124">Taken blijven aanwezig in de cache van de globale taak totdat u de achtergrond taak verwijdert of de Power shell-sessie sluit.</span><span class="sxs-lookup"><span data-stu-id="efa92-124">Jobs remain in the global job cache until you delete the background job or close the PowerShell session.</span></span>

## <span data-ttu-id="efa92-125">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="efa92-125">EXAMPLES</span></span>

### <span data-ttu-id="efa92-126">Voor beeld 1: een taak verwijderen door gebruik te maken van de naam</span><span class="sxs-lookup"><span data-stu-id="efa92-126">Example 1: Delete a job by using its name</span></span>

<span data-ttu-id="efa92-127">In dit voor beeld worden een variabele en de pijp lijn gebruikt om een taak op naam te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="efa92-127">This example uses a variable and the pipeline to delete a job by name.</span></span>

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

<span data-ttu-id="efa92-128">`Get-Job` gebruikt de para meter **name** om de taak, **BatchJob**, op te geven.</span><span class="sxs-lookup"><span data-stu-id="efa92-128">`Get-Job` uses the **Name** parameter to specify the job, **BatchJob**.</span></span> <span data-ttu-id="efa92-129">Het taak object wordt opgeslagen in de `$batch` variabele.</span><span class="sxs-lookup"><span data-stu-id="efa92-129">The job object is stored in the `$batch` variable.</span></span> <span data-ttu-id="efa92-130">Het object in `$batch` wordt naar beneden verzonden in de pijp lijn `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="efa92-130">The object in `$batch` is sent down the pipeline to `Remove-Job`.</span></span>

<span data-ttu-id="efa92-131">U kunt ook de **taak** parameter gebruiken, zoals `Remove-Job -Job $batch` .</span><span class="sxs-lookup"><span data-stu-id="efa92-131">An alternative is to use the **Job** parameter, such as `Remove-Job -Job $batch`.</span></span>

### <span data-ttu-id="efa92-132">Voor beeld 2: alle taken in een sessie verwijderen</span><span class="sxs-lookup"><span data-stu-id="efa92-132">Example 2: Delete all jobs in a session</span></span>

<span data-ttu-id="efa92-133">In dit voor beeld worden alle taken in de huidige Power shell-sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="efa92-133">In this example, all the jobs in the current PowerShell session are deleted.</span></span>

```powershell
Get-job | Remove-Job
```

<span data-ttu-id="efa92-134">`Get-Job` Hiermee worden alle taken in de huidige Power shell-sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="efa92-134">`Get-Job` gets all the jobs in the current PowerShell session.</span></span> <span data-ttu-id="efa92-135">De taak objecten worden naar beneden verzonden in de pijp lijn `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="efa92-135">The job objects are sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="efa92-136">Voor beeld 3: NotStarted-taken verwijderen</span><span class="sxs-lookup"><span data-stu-id="efa92-136">Example 3: Delete NotStarted jobs</span></span>

<span data-ttu-id="efa92-137">In dit voor beeld worden alle taken verwijderd uit de huidige Power shell-sessie die nog niet is gestart.</span><span class="sxs-lookup"><span data-stu-id="efa92-137">This example deletes all jobs from the current PowerShell session that haven't started.</span></span>

```powershell
Remove-Job -State NotStarted
```

<span data-ttu-id="efa92-138">`Remove-Job` gebruikt de para meter **State** om de taak status op te geven.</span><span class="sxs-lookup"><span data-stu-id="efa92-138">`Remove-Job` uses the **State** parameter to specify the job status.</span></span>

### <span data-ttu-id="efa92-139">Voor beeld 4: taken verwijderen met een beschrijvende naam</span><span class="sxs-lookup"><span data-stu-id="efa92-139">Example 4: Delete jobs by using a friendly name</span></span>

<span data-ttu-id="efa92-140">In dit voor beeld worden alle taken van de huidige sessie verwijderd met beschrijvende namen die eindigen op \* batch \* \*, inclusief taken die worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="efa92-140">This example deletes all jobs from the current session with friendly names that end with \*batch\*\*, including jobs that are running.</span></span>

```powershell
Remove-Job -Name *batch -Force
```

<span data-ttu-id="efa92-141">`Remove-Job` maakt gebruik van de para meter **name** om een taak naam patroon op te geven.</span><span class="sxs-lookup"><span data-stu-id="efa92-141">`Remove-Job` uses the **Name** parameter to specify a job name pattern.</span></span> <span data-ttu-id="efa92-142">Het patroon bevat het sterretje ( `*` ) als Joker teken om alle taak namen te vinden die eindigen op **batch**.</span><span class="sxs-lookup"><span data-stu-id="efa92-142">The pattern includes the asterisk (`*`) wildcard to find all job names that end with **batch**.</span></span> <span data-ttu-id="efa92-143">Met de para meter **Force** worden taken verwijderd die worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="efa92-143">The **Force** parameter deletes jobs that running.</span></span>

### <span data-ttu-id="efa92-144">Voor beeld 5: een taak verwijderen die is gemaakt door Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="efa92-144">Example 5: Delete a job that was created by Invoke-Command</span></span>

<span data-ttu-id="efa92-145">In dit voor beeld wordt een taak die op een externe computer is gestart, verwijderd met behulp `Invoke-Command` van de para meter **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="efa92-145">This example removes a job that was started on a remote computer using `Invoke-Command` with the **AsJob** parameter.</span></span>

<span data-ttu-id="efa92-146">Omdat in het voor beeld de para meter **AsJob** wordt gebruikt, wordt het taak object op de lokale computer gemaakt.</span><span class="sxs-lookup"><span data-stu-id="efa92-146">Because the example uses the **AsJob** parameter, the job object is created on the local computer.</span></span>
<span data-ttu-id="efa92-147">Maar de taak wordt uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="efa92-147">But, the job runs on a remote computer.</span></span> <span data-ttu-id="efa92-148">Als gevolg hiervan kunt u lokale opdrachten gebruiken om de taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="efa92-148">As a result, you use local commands to manage the job.</span></span>

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

<span data-ttu-id="efa92-149">`Invoke-Command` Hiermee wordt een taak uitgevoerd op de **Server01** -computer.</span><span class="sxs-lookup"><span data-stu-id="efa92-149">`Invoke-Command` runs a job on the **Server01** computer.</span></span> <span data-ttu-id="efa92-150">De para meter **AsJob** voert de **script Block** als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="efa92-150">The **AsJob** parameter runs the **ScriptBlock** as a background job.</span></span> <span data-ttu-id="efa92-151">Het taak object wordt opgeslagen in de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="efa92-151">The job object is stored in the `$job` variable.</span></span> <span data-ttu-id="efa92-152">Het `$job` variabele-object wordt naar beneden verzonden in de pijp lijn `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="efa92-152">The `$job` variable object is sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="efa92-153">Voor beeld 6: een taak verwijderen die is gemaakt door Invoke-Command en Start-Job</span><span class="sxs-lookup"><span data-stu-id="efa92-153">Example 6: Delete a job that was created by Invoke-Command and Start-Job</span></span>

<span data-ttu-id="efa92-154">In dit voor beeld ziet u hoe u een taak verwijdert op een externe computer die is gestart met `Invoke-Command` om uit te voeren `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="efa92-154">This example shows how to remove a job on a remote computer that was started by using `Invoke-Command` to run `Start-Job`.</span></span> <span data-ttu-id="efa92-155">Het taak object wordt gemaakt op de externe computer en de externe opdrachten worden gebruikt om de taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="efa92-155">The job object is created on the remote computer and remote commands are used to manage the job.</span></span> <span data-ttu-id="efa92-156">Een permanente verbinding is vereist voor het uitvoeren van een externe `Start-Job` opdracht.</span><span class="sxs-lookup"><span data-stu-id="efa92-156">A persistent connection is required when running a remote `Start-Job` command.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

<span data-ttu-id="efa92-157">`New-PSSession` Hiermee maakt u een **PSSession**, een permanente verbinding, naar de **Server01** -computer.</span><span class="sxs-lookup"><span data-stu-id="efa92-157">`New-PSSession` creates a **PSSession**, a persistent connection, to the **Server01** computer.</span></span> <span data-ttu-id="efa92-158">De verbinding wordt opgeslagen in de `$S` variabele.</span><span class="sxs-lookup"><span data-stu-id="efa92-158">The connection is saved in the `$S` variable.</span></span>

<span data-ttu-id="efa92-159">`Invoke-Command` maakt verbinding met de sessie die is opgeslagen in `$S` .</span><span class="sxs-lookup"><span data-stu-id="efa92-159">`Invoke-Command` connects to the session saved in `$S`.</span></span> <span data-ttu-id="efa92-160">De **script Block** gebruikt `Start-Job` om een externe taak te starten.</span><span class="sxs-lookup"><span data-stu-id="efa92-160">The **ScriptBlock** uses `Start-Job` to start a remote job.</span></span> <span data-ttu-id="efa92-161">De taak voert een `Get-Process` opdracht uit en gebruikt de para meter **name** om een beschrijvende taak naam op te geven, **MyJob**.</span><span class="sxs-lookup"><span data-stu-id="efa92-161">The job runs a `Get-Process` command and uses the **Name** parameter to specify a friendly job name, **MyJob**.</span></span>

<span data-ttu-id="efa92-162">`Invoke-Command` maakt gebruik van de `$S` sessie en wordt uitgevoerd `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="efa92-162">`Invoke-Command` uses the `$S` session and runs `Remove-Job`.</span></span> <span data-ttu-id="efa92-163">De para meter **name** geeft aan dat de taak met de naam **MyJob** wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="efa92-163">The **Name** parameter specifies that the job named **MyJob** is deleted.</span></span>

### <span data-ttu-id="efa92-164">Voor beeld 7: een taak verwijderen door gebruik te maken van de InstanceId</span><span class="sxs-lookup"><span data-stu-id="efa92-164">Example 7: Delete a job by using its InstanceId</span></span>

<span data-ttu-id="efa92-165">In dit voor beeld wordt een taak op basis van de **InstanceId** verwijderd.</span><span class="sxs-lookup"><span data-stu-id="efa92-165">This example removes a job based on its **InstanceId**.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="efa92-166">`Start-Job` Hiermee wordt een achtergrond taak gestart en het taak object wordt opgeslagen in de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="efa92-166">`Start-Job` starts a background job and the job object is saved in the `$job` variable.</span></span>

<span data-ttu-id="efa92-167">Het object in `$job` wordt naar beneden verzonden in de pijp lijn `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="efa92-167">The object in `$job` is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="efa92-168">De **eigenschaps** parameter maakt gebruik van een asterisk ( `*` ) om op te geven dat alle eigenschappen van het object in een lijst worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="efa92-168">The **Property** parameter uses an asterisk (`*`) to specify that all the object's properties are displayed in a list.</span></span>

<span data-ttu-id="efa92-169">`Remove-Job` gebruikt de **InstanceId** para meter om de taak op te geven die moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="efa92-169">`Remove-Job` uses the **InstanceId** parameter to specify the job to delete.</span></span>

## <span data-ttu-id="efa92-170">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="efa92-170">PARAMETERS</span></span>

### <span data-ttu-id="efa92-171">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="efa92-171">-Command</span></span>

<span data-ttu-id="efa92-172">Hiermee verwijdert u taken die de opgegeven woorden bevatten in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="efa92-172">Deletes jobs that include the specified words in the command.</span></span> <span data-ttu-id="efa92-173">U kunt een door komma's gescheiden matrix invoeren.</span><span class="sxs-lookup"><span data-stu-id="efa92-173">You can enter a comma-separated array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="efa92-174">-Confirm</span><span class="sxs-lookup"><span data-stu-id="efa92-174">-Confirm</span></span>

<span data-ttu-id="efa92-175">Vraagt u om bevestiging voordat deze `Remove-Job` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="efa92-175">Prompts you for confirmation before `Remove-Job` is run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efa92-176">-Filter</span><span class="sxs-lookup"><span data-stu-id="efa92-176">-Filter</span></span>

<span data-ttu-id="efa92-177">Hiermee verwijdert u taken die voldoen aan de voor waarden die zijn vastgelegd in de bijbehorende hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="efa92-177">Deletes jobs that satisfy all the conditions established in the associated hash table.</span></span> <span data-ttu-id="efa92-178">Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="efa92-178">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="efa92-179">Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken.</span><span class="sxs-lookup"><span data-stu-id="efa92-179">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="efa92-180">Het werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="efa92-180">It doesn't work on standard background jobs, such as those created by using the `Start-Job`.</span></span>

<span data-ttu-id="efa92-181">Deze para meter wordt geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="efa92-181">This parameter is introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="efa92-182">-Force</span><span class="sxs-lookup"><span data-stu-id="efa92-182">-Force</span></span>

<span data-ttu-id="efa92-183">Hiermee verwijdert u een taak, zelfs als de status van de taak wordt **uitgevoerd**.</span><span class="sxs-lookup"><span data-stu-id="efa92-183">Deletes a job even if the job's state is **Running**.</span></span> <span data-ttu-id="efa92-184">Als de para meter **Forces** niet wordt opgegeven, worden `Remove-Job` actieve taken niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="efa92-184">If the **Force** parameter isn't specified, `Remove-Job` doesn't delete running jobs.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, InstanceIdParameterSet, NameParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efa92-185">-Id</span><span class="sxs-lookup"><span data-stu-id="efa92-185">-Id</span></span>

<span data-ttu-id="efa92-186">Hiermee verwijdert u achtergrond taken met de opgegeven **id**. U kunt een door komma's gescheiden matrix invoeren.</span><span class="sxs-lookup"><span data-stu-id="efa92-186">Deletes background jobs with the specified **Id**. You can enter a comma-separated array.</span></span> <span data-ttu-id="efa92-187">De **id** van de taak is een uniek geheel getal dat een taak binnen de huidige sessie identificeert.</span><span class="sxs-lookup"><span data-stu-id="efa92-187">The job's **Id** is a unique integer that identifies a job within the current session.</span></span>

<span data-ttu-id="efa92-188">Als u de **id** van een taak wilt zoeken, gebruikt u `Get-Job` zonder para meters.</span><span class="sxs-lookup"><span data-stu-id="efa92-188">To find a job's **Id**, use `Get-Job` without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="efa92-189">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="efa92-189">-InstanceId</span></span>

<span data-ttu-id="efa92-190">Hiermee verwijdert u taken met de opgegeven **InstanceId**.</span><span class="sxs-lookup"><span data-stu-id="efa92-190">Deletes jobs with the specified **InstanceId**.</span></span> <span data-ttu-id="efa92-191">U kunt een door komma's gescheiden matrix invoeren.</span><span class="sxs-lookup"><span data-stu-id="efa92-191">You can enter a comma-separated array.</span></span> <span data-ttu-id="efa92-192">Een **InstanceId** is een unieke GUID waarmee een taak wordt aangeduid.</span><span class="sxs-lookup"><span data-stu-id="efa92-192">An **InstanceId** is a unique GUID that identifies a job.</span></span>

<span data-ttu-id="efa92-193">Als u wilt zoeken naar de **InstanceId** van een taak, gebruikt u `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="efa92-193">To find a job's **InstanceId**, use `Get-Job`.</span></span>

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

### <span data-ttu-id="efa92-194">-Taak</span><span class="sxs-lookup"><span data-stu-id="efa92-194">-Job</span></span>

<span data-ttu-id="efa92-195">Hiermee geeft u de taken die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="efa92-195">Specifies the jobs to be deleted.</span></span> <span data-ttu-id="efa92-196">Voer een variabele in die de taken bevat of een opdracht waarmee de taken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="efa92-196">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="efa92-197">U kunt een door komma's gescheiden matrix invoeren.</span><span class="sxs-lookup"><span data-stu-id="efa92-197">You can enter a comma-separated array.</span></span>

<span data-ttu-id="efa92-198">U kunt taak objecten naar beneden verplaatsen in de pijp lijn `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="efa92-198">You can send job objects down the pipeline to `Remove-Job`.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="efa92-199">-Name</span><span class="sxs-lookup"><span data-stu-id="efa92-199">-Name</span></span>

<span data-ttu-id="efa92-200">Hiermee verwijdert u alleen taken met de opgegeven beschrijvende naam.</span><span class="sxs-lookup"><span data-stu-id="efa92-200">Only deletes jobs with the specified friendly name.</span></span> <span data-ttu-id="efa92-201">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="efa92-201">Wildcards are permitted.</span></span> <span data-ttu-id="efa92-202">U kunt een door komma's gescheiden matrix invoeren.</span><span class="sxs-lookup"><span data-stu-id="efa92-202">You can enter a comma-separated array.</span></span>

<span data-ttu-id="efa92-203">Beschrijvende namen voor taken zijn niet gegarandeerd uniek, zelfs binnen een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="efa92-203">Friendly names for jobs aren't guaranteed to be unique, even within a PowerShell session.</span></span> <span data-ttu-id="efa92-204">Gebruik de para meters **WhatIf** en **confirm** wanneer u bestanden op naam verwijdert.</span><span class="sxs-lookup"><span data-stu-id="efa92-204">Use the **WhatIf** and **Confirm** parameters when you delete files by name.</span></span>

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

### <span data-ttu-id="efa92-205">-Status</span><span class="sxs-lookup"><span data-stu-id="efa92-205">-State</span></span>

<span data-ttu-id="efa92-206">Hiermee verwijdert u alleen taken met de opgegeven status.</span><span class="sxs-lookup"><span data-stu-id="efa92-206">Only deletes jobs with the specified state.</span></span> <span data-ttu-id="efa92-207">Als u taken wilt verwijderen met de status **wordt uitgevoerd**, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="efa92-207">To delete jobs with a state of **Running**, use the **Force** parameter.</span></span>

<span data-ttu-id="efa92-208">Geaccepteerde waarden:</span><span class="sxs-lookup"><span data-stu-id="efa92-208">Accepted values:</span></span>

- <span data-ttu-id="efa92-209">AtBreakpoint</span><span class="sxs-lookup"><span data-stu-id="efa92-209">AtBreakpoint</span></span>
- <span data-ttu-id="efa92-210">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="efa92-210">Blocked</span></span>
- <span data-ttu-id="efa92-211">Voltooid</span><span class="sxs-lookup"><span data-stu-id="efa92-211">Completed</span></span>
- <span data-ttu-id="efa92-212">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="efa92-212">Disconnected</span></span>
- <span data-ttu-id="efa92-213">Mislukt</span><span class="sxs-lookup"><span data-stu-id="efa92-213">Failed</span></span>
- <span data-ttu-id="efa92-214">NotStarted</span><span class="sxs-lookup"><span data-stu-id="efa92-214">NotStarted</span></span>
- <span data-ttu-id="efa92-215">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="efa92-215">Running</span></span>
- <span data-ttu-id="efa92-216">Gestopt</span><span class="sxs-lookup"><span data-stu-id="efa92-216">Stopped</span></span>
- <span data-ttu-id="efa92-217">Stoppen</span><span class="sxs-lookup"><span data-stu-id="efa92-217">Stopping</span></span>
- <span data-ttu-id="efa92-218">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="efa92-218">Suspended</span></span>
- <span data-ttu-id="efa92-219">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="efa92-219">Suspending</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="efa92-220">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="efa92-220">-WhatIf</span></span>

<span data-ttu-id="efa92-221">Hier wordt weer gegeven wat er gebeurt als er `Remove-Job` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="efa92-221">Shows what would happen if `Remove-Job` runs.</span></span> <span data-ttu-id="efa92-222">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="efa92-222">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efa92-223">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="efa92-223">CommonParameters</span></span>

<span data-ttu-id="efa92-224">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="efa92-224">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="efa92-225">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="efa92-225">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="efa92-226">INVOER</span><span class="sxs-lookup"><span data-stu-id="efa92-226">INPUTS</span></span>

### <span data-ttu-id="efa92-227">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="efa92-227">System.Management.Automation.Job</span></span>

<span data-ttu-id="efa92-228">U kunt een taak object omlaag verzenden via de pijp lijn `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="efa92-228">You can send a job object down the pipeline to `Remove-Job`.</span></span>

## <span data-ttu-id="efa92-229">UITVOER</span><span class="sxs-lookup"><span data-stu-id="efa92-229">OUTPUTS</span></span>

### <span data-ttu-id="efa92-230">Geen</span><span class="sxs-lookup"><span data-stu-id="efa92-230">None</span></span>

<span data-ttu-id="efa92-231">`Remove-Job` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="efa92-231">`Remove-Job` doesn't generate any output.</span></span>

## <span data-ttu-id="efa92-232">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="efa92-232">NOTES</span></span>

<span data-ttu-id="efa92-233">Een Power shell-taak maakt een nieuw proces.</span><span class="sxs-lookup"><span data-stu-id="efa92-233">A PowerShell job creates a new process.</span></span> <span data-ttu-id="efa92-234">Wanneer de taak is voltooid, wordt het proces afgesloten.</span><span class="sxs-lookup"><span data-stu-id="efa92-234">When the job completes, the process exits.</span></span> <span data-ttu-id="efa92-235">Wanneer `Remove-Job` wordt uitgevoerd, wordt de status van de taak verwijderd.</span><span class="sxs-lookup"><span data-stu-id="efa92-235">When `Remove-Job` is run, the job's state is removed.</span></span>

<span data-ttu-id="efa92-236">Als een taak stopt voordat deze is voltooid en het proces ervan niet is afgesloten, wordt het proces geforceerd beëindigd.</span><span class="sxs-lookup"><span data-stu-id="efa92-236">If a job stops before completion and its process hasn't exited, the process is forcibly terminated.</span></span>

## <span data-ttu-id="efa92-237">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="efa92-237">RELATED LINKS</span></span>

[<span data-ttu-id="efa92-238">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="efa92-238">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="efa92-239">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="efa92-239">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="efa92-240">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="efa92-240">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="efa92-241">Get-job</span><span class="sxs-lookup"><span data-stu-id="efa92-241">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="efa92-242">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="efa92-242">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="efa92-243">Receive-job</span><span class="sxs-lookup"><span data-stu-id="efa92-243">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="efa92-244">Begin taak</span><span class="sxs-lookup"><span data-stu-id="efa92-244">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="efa92-245">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="efa92-245">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="efa92-246">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="efa92-246">Wait-Job</span></span>](Wait-Job.md)
