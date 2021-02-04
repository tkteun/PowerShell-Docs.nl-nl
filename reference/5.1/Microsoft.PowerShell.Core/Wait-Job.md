---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/28/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: 1f6df33e995ad717e1451c047fec072a280b4a54
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098677"
---
# <span data-ttu-id="94ead-103">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="94ead-103">Wait-Job</span></span>

## <span data-ttu-id="94ead-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="94ead-104">SYNOPSIS</span></span>
<span data-ttu-id="94ead-105">Er wordt gewacht tot een of alle Power shell-taken die in de sessie worden uitgevoerd, zijn beëindigd.</span><span class="sxs-lookup"><span data-stu-id="94ead-105">Waits until one or all of the PowerShell jobs running in the session are in a terminating state.</span></span>

## <span data-ttu-id="94ead-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="94ead-106">SYNTAX</span></span>

### <span data-ttu-id="94ead-107">SessionIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="94ead-107">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="94ead-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="94ead-108">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="94ead-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="94ead-109">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="94ead-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="94ead-110">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="94ead-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="94ead-111">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="94ead-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="94ead-112">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="94ead-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="94ead-113">DESCRIPTION</span></span>

<span data-ttu-id="94ead-114">De `Wait-Job` cmdlet wacht totdat een taak een afsluitende status heeft voordat de uitvoering wordt voortgezet.</span><span class="sxs-lookup"><span data-stu-id="94ead-114">The `Wait-Job` cmdlet waits for a job to be in a terminating state before continuing execution.</span></span>
<span data-ttu-id="94ead-115">De afsluitende statussen zijn:</span><span class="sxs-lookup"><span data-stu-id="94ead-115">The terminating states are:</span></span>

- <span data-ttu-id="94ead-116">Voltooid</span><span class="sxs-lookup"><span data-stu-id="94ead-116">Completed</span></span>
- <span data-ttu-id="94ead-117">Mislukt</span><span class="sxs-lookup"><span data-stu-id="94ead-117">Failed</span></span>
- <span data-ttu-id="94ead-118">Gestopt</span><span class="sxs-lookup"><span data-stu-id="94ead-118">Stopped</span></span>
- <span data-ttu-id="94ead-119">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="94ead-119">Suspended</span></span>
- <span data-ttu-id="94ead-120">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="94ead-120">Disconnected</span></span>

<span data-ttu-id="94ead-121">U kunt wachten tot een opgegeven taak of alle taken een afsluitende status hebben.</span><span class="sxs-lookup"><span data-stu-id="94ead-121">You can wait until a specified job, or all jobs are in a terminating state.</span></span> <span data-ttu-id="94ead-122">U kunt ook een maximale wacht tijd instellen voor de taak met de **time-outwaarde** of de para meter **Force** gebruiken om te wachten op een taak in de `Suspended` of de `Disconnected` statussen.</span><span class="sxs-lookup"><span data-stu-id="94ead-122">You can also set a maximum wait time for the job using the **Timeout** parameter, or use the **Force** parameter to wait for a job in the `Suspended` or `Disconnected` states.</span></span>

<span data-ttu-id="94ead-123">Wanneer de opdrachten in de taak zijn voltooid, `Wait-Job` wordt een taak object geretourneerd en wordt de uitvoering voortgezet.</span><span class="sxs-lookup"><span data-stu-id="94ead-123">When the commands in the job are complete, `Wait-Job` returns a job object and continues execution.</span></span>

<span data-ttu-id="94ead-124">U kunt de `Wait-Job` cmdlet gebruiken om te wachten op taken die zijn gestart met behulp `Start-Job` van de cmdlet of de para meter **AsJob** van de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94ead-124">You can use the `Wait-Job` cmdlet to wait for jobs started by using the `Start-Job` cmdlet or the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="94ead-125">Zie [about_Jobs](./about/about_Jobs.md)voor meer informatie over taken.</span><span class="sxs-lookup"><span data-stu-id="94ead-125">For more information about jobs, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="94ead-126">Vanaf Windows Power Shell 3,0 wacht de `Wait-Job` cmdlet ook op aangepaste taak typen, zoals werk stroom taken en exemplaren van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="94ead-126">Starting in Windows PowerShell 3.0, the `Wait-Job` cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="94ead-127">Als u `Wait-Job` wilt wachten op taken van een bepaald type, importeert u de module die het aangepaste taak type ondersteunt in de sessie voordat u de `Get-Job` cmdlet uitvoert, hetzij met behulp van de `Import-Module` cmdlet of door een cmdlet in de module te gebruiken of op te halen.</span><span class="sxs-lookup"><span data-stu-id="94ead-127">To enable `Wait-Job` to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the `Get-Job` cmdlet, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="94ead-128">Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.</span><span class="sxs-lookup"><span data-stu-id="94ead-128">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="94ead-129">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="94ead-129">EXAMPLES</span></span>

### <span data-ttu-id="94ead-130">Voor beeld 1: wachten op alle taken</span><span class="sxs-lookup"><span data-stu-id="94ead-130">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="94ead-131">Met deze opdracht wordt gewacht tot alle taken die in de sessie worden uitgevoerd, zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="94ead-131">This command waits for all of the jobs running in the session to finish.</span></span>

### <span data-ttu-id="94ead-132">Voor beeld 2: wachten op taken die zijn gestart op externe computers met behulp van Start-Job</span><span class="sxs-lookup"><span data-stu-id="94ead-132">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="94ead-133">In dit voor beeld ziet u hoe u de `Wait-Job` cmdlet gebruikt met taken die zijn gestart op externe computers met behulp van de- `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94ead-133">This example shows how to use the `Wait-Job` cmdlet with jobs started on remote computers by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="94ead-134">Zowel `Start-Job` als- `Wait-Job` opdrachten worden naar de externe computer verzonden met behulp van de- `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94ead-134">Both `Start-Job` and `Wait-Job` commands are submitted to the remote computer by using the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="94ead-135">In dit voor beeld wordt gebruikt `Wait-Job` om te bepalen of een opdracht die wordt `Get-Date` uitgevoerd als een taak op drie verschillende computers, is voltooid.</span><span class="sxs-lookup"><span data-stu-id="94ead-135">This example uses `Wait-Job` to determine whether a `Get-Date` command running as a job on three different computers is finished.</span></span>

<span data-ttu-id="94ead-136">Met de eerste opdracht maakt u een Windows Power shell-sessie (**PSSession**) op elk van de drie externe computers en slaat u deze op in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="94ead-136">The first command creates a Windows PowerShell session (**PSSession**) on each of the three remote computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="94ead-137">De tweede opdracht wordt gebruikt `Invoke-Command` om `Start-Job` in elk van de drie sessies in te worden uitgevoerd `$s` .</span><span class="sxs-lookup"><span data-stu-id="94ead-137">The second command uses `Invoke-Command` to run `Start-Job` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="94ead-138">Alle taken hebben de naam Datum1.</span><span class="sxs-lookup"><span data-stu-id="94ead-138">All of the jobs are named Date1.</span></span>

<span data-ttu-id="94ead-139">De derde opdracht wordt gebruikt `Invoke-Command` om uit te voeren `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="94ead-139">The third command uses `Invoke-Command` to run `Wait-Job`.</span></span> <span data-ttu-id="94ead-140">Met deze opdracht wordt gewacht tot de `Date1` taken op elke computer zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="94ead-140">This command waits for the `Date1` jobs on each computer to finish.</span></span> <span data-ttu-id="94ead-141">De resulterende verzameling (**matrix**) van **taak** objecten wordt opgeslagen in de `$done` variabele.</span><span class="sxs-lookup"><span data-stu-id="94ead-141">It stores the resulting collection (**array**) of **job** objects in the `$done` variable.</span></span>

<span data-ttu-id="94ead-142">De vierde opdracht gebruikt de eigenschap **Count** van de matrix met taak objecten in de `$done` variabele om te bepalen hoeveel taken zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="94ead-142">The fourth command uses the **Count** property of the array of job objects in the `$done` variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="94ead-143">Voor beeld 3: bepalen wanneer de eerste taak is voltooid</span><span class="sxs-lookup"><span data-stu-id="94ead-143">Example 3: Determine when the first job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="94ead-144">In dit voor beeld **wordt de para** meter van gebruikt `Wait-Job` om te bepalen wanneer de eerste van veel taken die in de huidige sessie worden uitgevoerd, een afsluit status hebben.</span><span class="sxs-lookup"><span data-stu-id="94ead-144">This example uses the **Any** parameter of `Wait-Job` to determine when the first of many jobs running in the current session are in a terminating state.</span></span> <span data-ttu-id="94ead-145">U ziet ook hoe u de cmdlet kunt gebruiken `Wait-Job` om te wachten tot externe taken zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="94ead-145">It also shows how to use the `Wait-Job` cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="94ead-146">Met de eerste opdracht maakt u een **PSSession** op elke computer die wordt vermeld in het Machines.txt-bestand en worden de **PSSession** -objecten opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="94ead-146">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the `$s` variable.</span></span> <span data-ttu-id="94ead-147">De opdracht gebruikt de `Get-Content` cmdlet om de inhoud van het bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="94ead-147">The command uses the `Get-Content` cmdlet to get the contents of the file.</span></span> <span data-ttu-id="94ead-148">De `Get-Content` opdracht bevindt zich tussen haakjes om er zeker van te zijn dat deze vóór de opdracht wordt uitgevoerd `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="94ead-148">The `Get-Content` command is enclosed in parentheses to make sure that it runs before the `New-PSSession` command.</span></span>

<span data-ttu-id="94ead-149">Met de tweede opdracht `Get-EventLog` wordt een opdracht reeks opgeslagen tussen aanhalings tekens in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="94ead-149">The second command stores a `Get-EventLog` command string, in quotation marks, in the `$c` variable.</span></span>

<span data-ttu-id="94ead-150">De derde opdracht gebruikt `Invoke-Command` cmdlet om uit te voeren `Start-Job` in elk van de sessies in `$s` .</span><span class="sxs-lookup"><span data-stu-id="94ead-150">The third command uses `Invoke-Command` cmdlet to run `Start-Job` in each of the sessions in `$s`.</span></span>
<span data-ttu-id="94ead-151">`Start-Job`Met de opdracht wordt een taak gestart die de `Get-EventLog` opdracht in de `$c` variabele uitvoert.</span><span class="sxs-lookup"><span data-stu-id="94ead-151">The `Start-Job` command starts a job that runs the `Get-EventLog` command in the `$c` variable.</span></span>

<span data-ttu-id="94ead-152">De opdracht gebruikt de aanpassings functie voor het **gebruik** van het bereik om aan te geven dat de `$c` variabele op de lokale computer is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="94ead-152">The command uses the **Using** scope modifier to indicate that the `$c` variable was defined on the local computer.</span></span> <span data-ttu-id="94ead-153">De aanpassings functie voor het **gebruik** van scopes is geïntroduceerd in Windows power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="94ead-153">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="94ead-154">Zie [about_Remote_Variables](./about/about_Remote_Variables.md)voor meer informatie **over de aanpassing van het** bereik.</span><span class="sxs-lookup"><span data-stu-id="94ead-154">For more information about the **Using** scope modifier, see [about_Remote_Variables](./about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="94ead-155">De vierde opdracht wordt gebruikt `Invoke-Command` om een opdracht uit te voeren `Wait-Job` in de sessies.</span><span class="sxs-lookup"><span data-stu-id="94ead-155">The fourth command uses `Invoke-Command` to run a `Wait-Job` command in the sessions.</span></span> <span data-ttu-id="94ead-156">De **para meter** wordt gebruikt om te wachten tot de eerste taak op de externe computers wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="94ead-156">It uses the **Any** parameter to wait until the first job on the remote computers is terminating state.</span></span>

### <span data-ttu-id="94ead-157">Voor beeld 4: een wacht tijd instellen voor taken op externe computers</span><span class="sxs-lookup"><span data-stu-id="94ead-157">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
PS> $s = New-PSSession Server01, Server02, Server03
PS> $jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
PS> $done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
PS>
```

<span data-ttu-id="94ead-158">In dit voor beeld ziet u hoe u de para meter **time-out** van gebruikt `Wait-Job` om een maximale wacht tijd in te stellen voor de taken die worden uitgevoerd op externe computers.</span><span class="sxs-lookup"><span data-stu-id="94ead-158">This example shows how to use the **Timeout** parameter of `Wait-Job` to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="94ead-159">Met de eerste opdracht maakt u een **PSSession** op elk van de drie externe computers (Server01, Server02 en Server03), waarna de **PSSession** -objecten worden opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="94ead-159">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="94ead-160">De tweede opdracht wordt gebruikt `Invoke-Command` om `Start-Job` in elk van de **PSSession** -objecten in te worden uitgevoerd `$s` .</span><span class="sxs-lookup"><span data-stu-id="94ead-160">The second command uses `Invoke-Command` to run `Start-Job` in each of the **PSSession** objects in `$s`.</span></span> <span data-ttu-id="94ead-161">De resulterende taak objecten worden opgeslagen in de `$jobs` variabele.</span><span class="sxs-lookup"><span data-stu-id="94ead-161">It stores the resulting job objects in the `$jobs` variable.</span></span>

<span data-ttu-id="94ead-162">De derde opdracht wordt gebruikt `Invoke-Command` om `Wait-Job` in elk van de sessies in te worden uitgevoerd `$s` .</span><span class="sxs-lookup"><span data-stu-id="94ead-162">The third command uses `Invoke-Command` to run `Wait-Job` in each of the sessions in `$s`.</span></span> <span data-ttu-id="94ead-163">De `Wait-Job` opdracht bepaalt of alle opdrachten binnen 30 seconden zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="94ead-163">The `Wait-Job` command determines whether all of the commands have completed within 30 seconds.</span></span> <span data-ttu-id="94ead-164">De para meter **time-out** met de waarde 30 wordt gebruikt om de maximale wacht tijd te bepalen en vervolgens de resultaten van de opdracht in de variabele op te slaan `$done` .</span><span class="sxs-lookup"><span data-stu-id="94ead-164">It uses the **Timeout** parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the `$done` variable.</span></span>

<span data-ttu-id="94ead-165">In dit geval, na 30 seconden, is alleen de opdracht op de Server02 computer voltooid.</span><span class="sxs-lookup"><span data-stu-id="94ead-165">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span> <span data-ttu-id="94ead-166">`Wait-Job` de wacht tijd wordt beëindigd, het object wordt geretourneerd dat de voltooide taak vertegenwoordigt en de opdracht prompt wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="94ead-166">`Wait-Job` ends the wait, returns the object that represents the job that was completed, and displays the command prompt.</span></span>

<span data-ttu-id="94ead-167">De `$done` variabele bevat een taak object dat de taak vertegenwoordigt die is uitgevoerd op Server02.</span><span class="sxs-lookup"><span data-stu-id="94ead-167">The `$done` variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="94ead-168">Voor beeld 5: wachten tot een van de taken is voltooid</span><span class="sxs-lookup"><span data-stu-id="94ead-168">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="94ead-169">Met deze opdracht worden drie taken geïdentificeerd op basis van hun Id's en wordt gewacht totdat een van deze opdrachten in een afsluitende staat is.</span><span class="sxs-lookup"><span data-stu-id="94ead-169">This command identifies three jobs by their IDs and waits until any one of them are in a terminating state.</span></span> <span data-ttu-id="94ead-170">De uitvoering wordt voortgezet wanneer de eerste taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="94ead-170">Execution continues when the first job finishes.</span></span>

### <span data-ttu-id="94ead-171">Voor beeld 6: wachten op een periode, waarna de taak op de achtergrond kan worden voortgezet</span><span class="sxs-lookup"><span data-stu-id="94ead-171">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="94ead-172">Met deze opdracht wordt 120 seconden (twee minuten) gewacht totdat de DailyLog-taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="94ead-172">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span> <span data-ttu-id="94ead-173">Als de taak niet in de volgende twee minuten wordt voltooid, wordt de uitvoering voortgezet en wordt de taak nog steeds op de achtergrond uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="94ead-173">If the job does not finish in the next two minutes, execution continues, and the job continues to run in the background.</span></span>

### <span data-ttu-id="94ead-174">Voor beeld 7: wachten op een taak op naam</span><span class="sxs-lookup"><span data-stu-id="94ead-174">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="94ead-175">Met deze opdracht wordt de taak naam gebruikt om de taak te identificeren waarvoor moet worden gewacht.</span><span class="sxs-lookup"><span data-stu-id="94ead-175">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="94ead-176">Voor beeld 8: wachten op taken op de lokale computer die is gestart met Start-Job</span><span class="sxs-lookup"><span data-stu-id="94ead-176">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_.lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="94ead-177">In dit voor beeld ziet u hoe u de `Wait-Job` cmdlet gebruikt met taken die zijn gestart op de lokale computer met behulp van `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="94ead-177">This example shows how to use the `Wait-Job` cmdlet with jobs started on the local computer by using `Start-Job`.</span></span>

<span data-ttu-id="94ead-178">Met deze opdrachten wordt een taak gestart waarmee de Windows Power shell-script bestanden worden opgehaald die in de afgelopen week zijn toegevoegd of bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="94ead-178">These commands start a job that gets the Windows PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="94ead-179">De eerste opdracht wordt gebruikt `Start-Job` om een taak op de lokale computer te starten.</span><span class="sxs-lookup"><span data-stu-id="94ead-179">The first command uses `Start-Job` to start a job on the local computer.</span></span> <span data-ttu-id="94ead-180">Met de taak wordt een `Get-ChildItem` opdracht uitgevoerd waarmee alle bestanden met de bestandsnaam extensie. ps1 worden opgehaald die in de afgelopen week zijn toegevoegd of bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="94ead-180">The job runs a `Get-ChildItem` command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="94ead-181">De derde opdracht wordt gebruikt `Wait-Job` om te wachten tot de taak een afsluitende status heeft.</span><span class="sxs-lookup"><span data-stu-id="94ead-181">The third command uses `Wait-Job` to wait until the job is in a terminating state.</span></span> <span data-ttu-id="94ead-182">Wanneer de taak is voltooid, wordt met de opdracht het taak object weer gegeven, dat informatie over de taak bevat.</span><span class="sxs-lookup"><span data-stu-id="94ead-182">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="94ead-183">Voor beeld 9: wachten op taken die zijn gestart op externe computers met behulp van Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="94ead-183">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="94ead-184">In dit voor beeld ziet u hoe u kunt gebruiken `Wait-Job` met taken die zijn gestart op externe computers met behulp van de para meter **AsJob** van `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="94ead-184">This example shows how to use `Wait-Job` with jobs started on remote computers by using the **AsJob** parameter of `Invoke-Command`.</span></span> <span data-ttu-id="94ead-185">Wanneer u **AsJob** gebruikt, wordt de taak op de lokale computer gemaakt en worden de resultaten automatisch naar de lokale computer geretourneerd, zelfs als de taak wordt uitgevoerd op de externe computers.</span><span class="sxs-lookup"><span data-stu-id="94ead-185">When using **AsJob**, the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="94ead-186">In dit voor beeld wordt gebruikt `Wait-Job` om te bepalen of een `Get-Process` opdracht die wordt uitgevoerd in de sessies op drie externe computers een afsluitende status heeft.</span><span class="sxs-lookup"><span data-stu-id="94ead-186">This example uses `Wait-Job` to determine whether a `Get-Process` command running in the sessions on three remote computers is in a terminating state.</span></span>

<span data-ttu-id="94ead-187">Met de eerste opdracht worden **PSSession** -objecten op drie computers gemaakt en opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="94ead-187">The first command creates **PSSession** objects on three computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="94ead-188">De tweede opdracht wordt gebruikt `Invoke-Command` om `Get-Process` in elk van de drie sessies in te worden uitgevoerd `$s` .</span><span class="sxs-lookup"><span data-stu-id="94ead-188">The second command uses `Invoke-Command` to run `Get-Process` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="94ead-189">De opdracht gebruikt de para meter **AsJob** om de opdracht asynchroon uit te voeren als een taak.</span><span class="sxs-lookup"><span data-stu-id="94ead-189">The command uses the **AsJob** parameter to run the command asynchronously as a job.</span></span> <span data-ttu-id="94ead-190">De opdracht retourneert een taak object, net zoals de taken die met `Start-Job` worden gestart, en het taak object wordt opgeslagen in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="94ead-190">The command returns a job object, just like the jobs started by using `Start-Job`, and the job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="94ead-191">De derde opdracht maakt gebruik van een pijplijn operator ( `|` ) voor het verzenden van het taak object in `$j` naar de `Wait-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94ead-191">The third command uses a pipeline operator (`|`) to send the job object in `$j` to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="94ead-192">`Invoke-Command`In dit geval is een opdracht niet vereist, omdat de taak zich op de lokale computer bevindt.</span><span class="sxs-lookup"><span data-stu-id="94ead-192">An `Invoke-Command` command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="94ead-193">Voor beeld 10: wachten op een taak met een ID</span><span class="sxs-lookup"><span data-stu-id="94ead-193">Example 10: Wait for a job that has an ID</span></span>

```powershell
Get-Job
```

```Output
Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where
```

```powershell
Wait-Job -Id 1
```

<span data-ttu-id="94ead-194">Met deze opdracht wordt gewacht op de taak met de ID-waarde 1.</span><span class="sxs-lookup"><span data-stu-id="94ead-194">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="94ead-195">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="94ead-195">PARAMETERS</span></span>

### <span data-ttu-id="94ead-196">-Alle</span><span class="sxs-lookup"><span data-stu-id="94ead-196">-Any</span></span>

<span data-ttu-id="94ead-197">Geeft aan dat met deze cmdlet het taak object wordt geretourneerd en de uitvoering wordt voortgezet wanneer een taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="94ead-197">Indicates that this cmdlet returns the job object and continues execution when any job finishes.</span></span> <span data-ttu-id="94ead-198">Standaard wordt `Wait-Job` gewacht totdat alle opgegeven taken zijn voltooid voordat de prompt wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="94ead-198">By default, `Wait-Job` waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="94ead-199">-Filter</span><span class="sxs-lookup"><span data-stu-id="94ead-199">-Filter</span></span>

<span data-ttu-id="94ead-200">Hiermee geeft u een hash-tabel met voor waarden op.</span><span class="sxs-lookup"><span data-stu-id="94ead-200">Specifies a hash table of conditions.</span></span> <span data-ttu-id="94ead-201">Met deze cmdlet wordt gewacht op taken die voldoen aan alle voor waarden in de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="94ead-201">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="94ead-202">Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="94ead-202">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="94ead-203">Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken.</span><span class="sxs-lookup"><span data-stu-id="94ead-203">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="94ead-204">Deze functie werkt niet voor standaard taken, zoals die zijn gemaakt met behulp van de- `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94ead-204">It does not work on standard jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="94ead-205">Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="94ead-205">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="94ead-206">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="94ead-206">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="94ead-207">-Force</span><span class="sxs-lookup"><span data-stu-id="94ead-207">-Force</span></span>

<span data-ttu-id="94ead-208">Hiermee wordt aangegeven dat deze cmdlet blijft wachten op taken met de status onderbroken of niet verbonden.</span><span class="sxs-lookup"><span data-stu-id="94ead-208">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span> <span data-ttu-id="94ead-209">`Wait-Job`Retourneert standaard of beëindigt de wacht tijd wanneer taken een van de volgende statussen hebben:</span><span class="sxs-lookup"><span data-stu-id="94ead-209">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="94ead-210">Voltooid</span><span class="sxs-lookup"><span data-stu-id="94ead-210">Completed</span></span>
- <span data-ttu-id="94ead-211">Mislukt</span><span class="sxs-lookup"><span data-stu-id="94ead-211">Failed</span></span>
- <span data-ttu-id="94ead-212">Gestopt</span><span class="sxs-lookup"><span data-stu-id="94ead-212">Stopped</span></span>
- <span data-ttu-id="94ead-213">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="94ead-213">Suspended</span></span>
- <span data-ttu-id="94ead-214">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="94ead-214">Disconnected</span></span>

<span data-ttu-id="94ead-215">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="94ead-215">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="94ead-216">-Id</span><span class="sxs-lookup"><span data-stu-id="94ead-216">-Id</span></span>

<span data-ttu-id="94ead-217">Hiermee geeft u een matrix met Id's van taken op waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="94ead-217">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="94ead-218">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="94ead-218">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="94ead-219">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="94ead-219">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="94ead-220">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="94ead-220">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="94ead-221">Als u de ID van een taak wilt zoeken, typt u `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="94ead-221">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="94ead-222">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="94ead-222">-InstanceId</span></span>

<span data-ttu-id="94ead-223">Hiermee geeft u een matrix met exemplaar-Id's op van taken waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="94ead-223">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span> <span data-ttu-id="94ead-224">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="94ead-224">The default is all jobs.</span></span>

<span data-ttu-id="94ead-225">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="94ead-225">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="94ead-226">Gebruik om de exemplaar-ID van een taak te vinden `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="94ead-226">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="94ead-227">-Taak</span><span class="sxs-lookup"><span data-stu-id="94ead-227">-Job</span></span>

<span data-ttu-id="94ead-228">Hiermee geeft u de taken op waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="94ead-228">Specifies the jobs for which this cmdlet waits.</span></span> <span data-ttu-id="94ead-229">Voer een variabele in die de taak objecten bevat of een opdracht waarmee de taak objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="94ead-229">Enter a variable that contains the job objects or a command that gets the job objects.</span></span> <span data-ttu-id="94ead-230">U kunt ook een pijplijn operator gebruiken om taak objecten te verzenden naar de `Wait-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94ead-230">You can also use a pipeline operator to send job objects to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="94ead-231">Standaard wordt `Wait-Job` gewacht op alle taken die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="94ead-231">By default, `Wait-Job` waits for all jobs created in the current session.</span></span>

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

### <span data-ttu-id="94ead-232">-Name</span><span class="sxs-lookup"><span data-stu-id="94ead-232">-Name</span></span>

<span data-ttu-id="94ead-233">Hiermee geeft u beschrijvende namen van taken op waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="94ead-233">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="94ead-234">-Status</span><span class="sxs-lookup"><span data-stu-id="94ead-234">-State</span></span>

<span data-ttu-id="94ead-235">Hiermee geeft u een taak status op.</span><span class="sxs-lookup"><span data-stu-id="94ead-235">Specifies a job state.</span></span> <span data-ttu-id="94ead-236">Met deze cmdlet wordt alleen gewacht op taken in de opgegeven status.</span><span class="sxs-lookup"><span data-stu-id="94ead-236">This cmdlet waits only for jobs in the specified state.</span></span> <span data-ttu-id="94ead-237">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="94ead-237">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="94ead-238">NotStarted</span><span class="sxs-lookup"><span data-stu-id="94ead-238">NotStarted</span></span>
- <span data-ttu-id="94ead-239">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="94ead-239">Running</span></span>
- <span data-ttu-id="94ead-240">Voltooid</span><span class="sxs-lookup"><span data-stu-id="94ead-240">Completed</span></span>
- <span data-ttu-id="94ead-241">Mislukt</span><span class="sxs-lookup"><span data-stu-id="94ead-241">Failed</span></span>
- <span data-ttu-id="94ead-242">Gestopt</span><span class="sxs-lookup"><span data-stu-id="94ead-242">Stopped</span></span>
- <span data-ttu-id="94ead-243">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="94ead-243">Blocked</span></span>
- <span data-ttu-id="94ead-244">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="94ead-244">Suspended</span></span>
- <span data-ttu-id="94ead-245">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="94ead-245">Disconnected</span></span>
- <span data-ttu-id="94ead-246">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="94ead-246">Suspending</span></span>
- <span data-ttu-id="94ead-247">Stoppen</span><span class="sxs-lookup"><span data-stu-id="94ead-247">Stopping</span></span>

<span data-ttu-id="94ead-248">Zie [JobState Enumeration](/dotnet/api/system.management.automation.jobstate)(Engelstalig) voor meer informatie over de status van een taak.</span><span class="sxs-lookup"><span data-stu-id="94ead-248">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="94ead-249">-Time-out</span><span class="sxs-lookup"><span data-stu-id="94ead-249">-Timeout</span></span>

<span data-ttu-id="94ead-250">Hiermee geeft u de maximale wacht tijd op voor elke taak, in seconden.</span><span class="sxs-lookup"><span data-stu-id="94ead-250">Specifies the maximum wait time for each job, in seconds.</span></span> <span data-ttu-id="94ead-251">De standaard waarde-1 geeft aan dat de cmdlet wacht totdat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="94ead-251">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span> <span data-ttu-id="94ead-252">De tijds duur begint wanneer u de `Wait-Job` opdracht verzendt, niet de `Start-Job` opdracht.</span><span class="sxs-lookup"><span data-stu-id="94ead-252">The timing starts when you submit the `Wait-Job` command, not the `Start-Job` command.</span></span>

<span data-ttu-id="94ead-253">Als deze tijd wordt overschreden, worden de wacht tijden beëindigd en wordt de uitvoering voortgezet, zelfs als de taak nog steeds wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="94ead-253">If this time is exceeded, the wait ends and execution continues, even if the job is still running.</span></span>
<span data-ttu-id="94ead-254">Met de opdracht wordt geen fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="94ead-254">The command does not display any error message.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94ead-255">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="94ead-255">CommonParameters</span></span>

<span data-ttu-id="94ead-256">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="94ead-256">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="94ead-257">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="94ead-257">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="94ead-258">INVOER</span><span class="sxs-lookup"><span data-stu-id="94ead-258">INPUTS</span></span>

### <span data-ttu-id="94ead-259">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="94ead-259">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="94ead-260">U kunt een taak object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94ead-260">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="94ead-261">UITVOER</span><span class="sxs-lookup"><span data-stu-id="94ead-261">OUTPUTS</span></span>

### <span data-ttu-id="94ead-262">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="94ead-262">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="94ead-263">Met deze cmdlet worden taak objecten geretourneerd die de taken in een afsluitende status vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="94ead-263">This cmdlet returns job objects that represent the jobs in a terminating state.</span></span> <span data-ttu-id="94ead-264">Als de wacht tijd eindigt omdat de waarde van de para meter **time-out** is overschreden, `Wait-Job` worden er geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="94ead-264">If the wait ends because the value of the **Timeout** parameter is exceeded, `Wait-Job` does not return any objects.</span></span>

## <span data-ttu-id="94ead-265">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="94ead-265">NOTES</span></span>

<span data-ttu-id="94ead-266">`Wait-Job`Retourneert standaard of beëindigt de wacht tijd wanneer taken een van de volgende statussen hebben:</span><span class="sxs-lookup"><span data-stu-id="94ead-266">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="94ead-267">Voltooid</span><span class="sxs-lookup"><span data-stu-id="94ead-267">Completed</span></span>
- <span data-ttu-id="94ead-268">Mislukt</span><span class="sxs-lookup"><span data-stu-id="94ead-268">Failed</span></span>
- <span data-ttu-id="94ead-269">Gestopt</span><span class="sxs-lookup"><span data-stu-id="94ead-269">Stopped</span></span>
- <span data-ttu-id="94ead-270">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="94ead-270">Suspended</span></span>
- <span data-ttu-id="94ead-271">De verbinding is verbroken zodat u `Wait-Job` verder kunt wachten op onderbroken en verbroken taken, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="94ead-271">Disconnected To direct `Wait-Job` to continue to wait for Suspended and Disconnected jobs, use the **Force** parameter.</span></span>

## <span data-ttu-id="94ead-272">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="94ead-272">RELATED LINKS</span></span>

[<span data-ttu-id="94ead-273">Get-job</span><span class="sxs-lookup"><span data-stu-id="94ead-273">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="94ead-274">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="94ead-274">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="94ead-275">Receive-job</span><span class="sxs-lookup"><span data-stu-id="94ead-275">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="94ead-276">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="94ead-276">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="94ead-277">Resume-job</span><span class="sxs-lookup"><span data-stu-id="94ead-277">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="94ead-278">Begin taak</span><span class="sxs-lookup"><span data-stu-id="94ead-278">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="94ead-279">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="94ead-279">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="94ead-280">Onderbreken-taak</span><span class="sxs-lookup"><span data-stu-id="94ead-280">Suspend-Job</span></span>](Suspend-Job.md)
