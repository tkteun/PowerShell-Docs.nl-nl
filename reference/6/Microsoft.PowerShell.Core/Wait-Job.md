---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: 93673fe82ebb87f160fc0a20acdc5c766a446445
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387172"
---
# <span data-ttu-id="3558e-103">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="3558e-103">Wait-Job</span></span>

## <span data-ttu-id="3558e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3558e-104">SYNOPSIS</span></span>
<span data-ttu-id="3558e-105">Onderdrukt de opdracht prompt totdat een of alle Power shell-achtergrond taken die in de sessie worden uitgevoerd, zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-105">Suppresses the command prompt until one or all of the PowerShell background jobs running in the session are completed.</span></span>

## <span data-ttu-id="3558e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3558e-106">SYNTAX</span></span>

### <span data-ttu-id="3558e-107">SessionIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="3558e-107">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="3558e-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="3558e-108">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="3558e-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="3558e-109">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="3558e-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3558e-110">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="3558e-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="3558e-111">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="3558e-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="3558e-112">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="3558e-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3558e-113">DESCRIPTION</span></span>

<span data-ttu-id="3558e-114">De `Wait-Job` cmdlet wacht tot de Power shell-achtergrond taken zijn voltooid voordat de opdracht prompt wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3558e-114">The `Wait-Job` cmdlet waits for PowerShell background jobs to finish before it displays the command prompt.</span></span> <span data-ttu-id="3558e-115">U kunt wachten tot een wille keurige achtergrond taak is voltooid of totdat alle achtergrond taken zijn voltooid en u een maximale wacht tijd voor de taak kunt instellen.</span><span class="sxs-lookup"><span data-stu-id="3558e-115">You can wait until any background job is complete, or until all background jobs are complete, and you can set a maximum wait time for the job.</span></span>

<span data-ttu-id="3558e-116">Wanneer de opdrachten in de taak zijn voltooid, `Wait-Job` wordt de opdracht prompt weer gegeven en wordt een taak object geretourneerd, zodat u het kunt door sluizen naar een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="3558e-116">When the commands in the job are complete, `Wait-Job` displays the command prompt and returns a job object so that you can pipe it to another command.</span></span>

<span data-ttu-id="3558e-117">U kunt `Wait-Job` de cmdlet gebruiken om te wachten op achtergrond taken, zoals die zijn gestart met behulp `Start-Job` van de cmdlet of de para meter **AsJob** van de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3558e-117">You can use `Wait-Job` cmdlet to wait for background jobs, such as those that were started by using the `Start-Job` cmdlet or the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="3558e-118">Zie [about_Jobs](./about/about_Jobs.md)voor meer informatie over Windows Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="3558e-118">For more information about Windows PowerShell background jobs, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="3558e-119">Vanaf Windows Power Shell 3,0 wacht de `Wait-Job` cmdlet ook op aangepaste taak typen, zoals werk stroom taken en exemplaren van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="3558e-119">Starting in Windows PowerShell 3.0, the `Wait-Job` cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="3558e-120">Als u `Wait-Job` wilt wachten op taken van een bepaald type, importeert u de module die het aangepaste taak type ondersteunt in de sessie voordat u de `Get-Job` cmdlet uitvoert, hetzij met behulp van de `Import-Module` cmdlet of door een cmdlet in de module te gebruiken of op te halen.</span><span class="sxs-lookup"><span data-stu-id="3558e-120">To enable `Wait-Job` to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the `Get-Job` cmdlet, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="3558e-121">Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.</span><span class="sxs-lookup"><span data-stu-id="3558e-121">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="3558e-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3558e-122">EXAMPLES</span></span>

### <span data-ttu-id="3558e-123">Voor beeld 1: wachten op alle taken</span><span class="sxs-lookup"><span data-stu-id="3558e-123">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="3558e-124">Met deze opdracht wordt gewacht tot alle achtergrond taken die in de sessie worden uitgevoerd, worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-124">This command waits for all of the background jobs running in the session to finish.</span></span>

### <span data-ttu-id="3558e-125">Voor beeld 2: wachten op taken die zijn gestart op externe computers met behulp van Start-Job</span><span class="sxs-lookup"><span data-stu-id="3558e-125">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="3558e-126">In dit voor beeld ziet u hoe u de `Wait-Job` cmdlet gebruikt met taken die zijn gestart op externe computers met behulp van de- `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3558e-126">This example shows how to use the `Wait-Job` cmdlet with jobs started on remote computers by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="3558e-127">Zowel `Start-Job` als- `Wait-Job` opdrachten worden naar de externe computer verzonden met behulp van de- `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3558e-127">Both `Start-Job` and `Wait-Job` commands are submitted to the remote computer by using the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="3558e-128">In dit voor beeld wordt gebruikt `Wait-Job` om te bepalen of een `Get-Date` opdracht die wordt uitgevoerd als achtergrond taak op drie verschillende computers is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-128">This example uses `Wait-Job` to determine whether a `Get-Date` command running as a background job on three different computers is finished.</span></span>

<span data-ttu-id="3558e-129">Met de eerste opdracht maakt u een Windows Power shell-sessie ( **PSSession** ) op elk van de drie externe computers en slaat u deze op in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="3558e-129">The first command creates a Windows PowerShell session ( **PSSession** ) on each of the three remote computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="3558e-130">De tweede opdracht wordt gebruikt `Invoke-Command` om `Start-Job` in elk van de drie sessies in te worden uitgevoerd `$s` .</span><span class="sxs-lookup"><span data-stu-id="3558e-130">The second command uses `Invoke-Command` to run `Start-Job` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="3558e-131">Alle taken hebben de naam Datum1.</span><span class="sxs-lookup"><span data-stu-id="3558e-131">All of the jobs are named Date1.</span></span>

<span data-ttu-id="3558e-132">De derde opdracht wordt gebruikt `Invoke-Command` om uit te voeren `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="3558e-132">The third command uses `Invoke-Command` to run `Wait-Job`.</span></span> <span data-ttu-id="3558e-133">Met deze opdracht wordt gewacht op de Datum1-taken op elke computer om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="3558e-133">This command waits for the Date1 jobs on each computer to finish.</span></span> <span data-ttu-id="3558e-134">De resulterende verzameling (matrix) van taak objecten wordt opgeslagen in de `$done` variabele.</span><span class="sxs-lookup"><span data-stu-id="3558e-134">It stores the resulting collection (array) of job objects in the `$done` variable.</span></span>

<span data-ttu-id="3558e-135">De vierde opdracht gebruikt de eigenschap **Count** van de matrix met taak objecten in de `$done` variabele om te bepalen hoeveel taken zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-135">The fourth command uses the **Count** property of the array of job objects in the `$done` variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="3558e-136">Voor beeld 3: bepalen wanneer de eerste achtergrond taak is voltooid</span><span class="sxs-lookup"><span data-stu-id="3558e-136">Example 3: Determine when the first background job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="3558e-137">In dit voor beeld wordt **de para meter** van gebruikt `Wait-Job` om te bepalen wanneer de eerste van de vele achtergrond taken die in de huidige sessie worden uitgevoerd, zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-137">This example uses the **Any** parameter of `Wait-Job` to determine when the first of many background jobs running in the current session are completed.</span></span> <span data-ttu-id="3558e-138">U ziet ook hoe u de cmdlet kunt gebruiken `Wait-Job` om te wachten tot externe taken zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-138">It also shows how to use the `Wait-Job` cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="3558e-139">Met de eerste opdracht maakt u een **PSSession** op elke computer die wordt vermeld in het Machines.txt-bestand en worden de **PSSession** -objecten opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="3558e-139">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the `$s` variable.</span></span> <span data-ttu-id="3558e-140">De opdracht gebruikt de `Get-Content` cmdlet om de inhoud van het bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="3558e-140">The command uses the `Get-Content` cmdlet to get the contents of the file.</span></span> <span data-ttu-id="3558e-141">De `Get-Content` opdracht bevindt zich tussen haakjes om er zeker van te zijn dat deze vóór de opdracht wordt uitgevoerd `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="3558e-141">The `Get-Content` command is enclosed in parentheses to make sure that it runs before the `New-PSSession` command.</span></span>

<span data-ttu-id="3558e-142">Met de tweede opdracht `Get-EventLog` wordt een opdracht reeks opgeslagen tussen aanhalings tekens in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="3558e-142">The second command stores a `Get-EventLog` command string, in quotation marks, in the `$c` variable.</span></span>

<span data-ttu-id="3558e-143">De derde opdracht gebruikt `Invoke-Command` cmdlet om uit te voeren `Start-Job` in elk van de sessies in `$s` .</span><span class="sxs-lookup"><span data-stu-id="3558e-143">The third command uses `Invoke-Command` cmdlet to run `Start-Job` in each of the sessions in `$s`.</span></span>
<span data-ttu-id="3558e-144">`Start-Job`Met de opdracht wordt een achtergrond taak gestart waarmee de opdracht wordt uitgevoerd `Get-EventLog` in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="3558e-144">The `Start-Job` command starts a background job that runs the `Get-EventLog` command in the `$c` variable.</span></span>

<span data-ttu-id="3558e-145">De opdracht gebruikt de aanpassings functie voor het **gebruik** van het bereik om aan te geven dat de `$c` variabele op de lokale computer is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="3558e-145">The command uses the **Using** scope modifier to indicate that the `$c` variable was defined on the local computer.</span></span> <span data-ttu-id="3558e-146">De aanpassings functie voor het **gebruik** van scopes is geïntroduceerd in Windows power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3558e-146">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="3558e-147">Zie [about_Remote_Variables](./about/about_Remote_Variables.md)voor meer informatie **over de aanpassing van het** bereik.</span><span class="sxs-lookup"><span data-stu-id="3558e-147">For more information about the **Using** scope modifier, see [about_Remote_Variables](./about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="3558e-148">De vierde opdracht wordt gebruikt `Invoke-Command` om een opdracht uit te voeren `Wait-Job` in de sessies.</span><span class="sxs-lookup"><span data-stu-id="3558e-148">The fourth command uses `Invoke-Command` to run a `Wait-Job` command in the sessions.</span></span> <span data-ttu-id="3558e-149">De **para meter** wordt gebruikt om te wachten tot de eerste taak op de externe computers is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-149">It uses the **Any** parameter to wait until the first job on the remote computers is completed.</span></span>

### <span data-ttu-id="3558e-150">Voor beeld 4: een wacht tijd instellen voor taken op externe computers</span><span class="sxs-lookup"><span data-stu-id="3558e-150">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

<span data-ttu-id="3558e-151">In dit voor beeld ziet u hoe u de para meter **time-out** van gebruikt `Wait-Job` om een maximale wacht tijd in te stellen voor de taken die worden uitgevoerd op externe computers.</span><span class="sxs-lookup"><span data-stu-id="3558e-151">This example shows how to use the **Timeout** parameter of `Wait-Job` to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="3558e-152">Met de eerste opdracht maakt u een **PSSession** op elk van de drie externe computers (Server01, Server02 en Server03), waarna de **PSSession** -objecten worden opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="3558e-152">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="3558e-153">De tweede opdracht wordt gebruikt `Invoke-Command` om `Start-Job` in elk van de **PSSession** -objecten in te worden uitgevoerd `$s` .</span><span class="sxs-lookup"><span data-stu-id="3558e-153">The second command uses `Invoke-Command` to run `Start-Job` in each of the **PSSession** objects in `$s`.</span></span> <span data-ttu-id="3558e-154">De resulterende taak objecten worden opgeslagen in de `$jobs` variabele.</span><span class="sxs-lookup"><span data-stu-id="3558e-154">It stores the resulting job objects in the `$jobs` variable.</span></span>

<span data-ttu-id="3558e-155">De derde opdracht wordt gebruikt `Invoke-Command` om `Wait-Job` in elk van de sessies in te worden uitgevoerd `$s` .</span><span class="sxs-lookup"><span data-stu-id="3558e-155">The third command uses `Invoke-Command` to run `Wait-Job` in each of the sessions in `$s`.</span></span> <span data-ttu-id="3558e-156">De `Wait-Job` opdracht bepaalt of alle opdrachten binnen 30 seconden zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-156">The `Wait-Job` command determines whether all of the commands have completed within 30 seconds.</span></span> <span data-ttu-id="3558e-157">De para meter **time-out** met de waarde 30 wordt gebruikt om de maximale wacht tijd te bepalen en vervolgens de resultaten van de opdracht in de variabele op te slaan `$done` .</span><span class="sxs-lookup"><span data-stu-id="3558e-157">It uses the **Timeout** parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the `$done` variable.</span></span>

<span data-ttu-id="3558e-158">In dit geval, na 30 seconden, is alleen de opdracht op de Server02 computer voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-158">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span> <span data-ttu-id="3558e-159">`Wait-Job` de wacht tijd wordt beëindigd, de opdracht prompt wordt weer gegeven en het object wordt geretourneerd dat de voltooide taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="3558e-159">`Wait-Job` ends the wait, displays the command prompt, and returns the object that represents the job that was completed.</span></span>

<span data-ttu-id="3558e-160">De `$done` variabele bevat een taak object dat de taak vertegenwoordigt die is uitgevoerd op Server02.</span><span class="sxs-lookup"><span data-stu-id="3558e-160">The `$done` variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="3558e-161">Voor beeld 5: wachten tot een van de taken is voltooid</span><span class="sxs-lookup"><span data-stu-id="3558e-161">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="3558e-162">Met deze opdracht worden drie taken geïdentificeerd op basis van hun Id's en wordt gewacht totdat een van deze opdrachten is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-162">This command identifies three jobs by their IDs and waits until any one of them are completed.</span></span>
<span data-ttu-id="3558e-163">De opdracht prompt wordt weer gegeven wanneer de eerste taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-163">The command prompt returns when the first job finishes.</span></span>

### <span data-ttu-id="3558e-164">Voor beeld 6: wachten op een periode, waarna de taak op de achtergrond kan worden voortgezet</span><span class="sxs-lookup"><span data-stu-id="3558e-164">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="3558e-165">Met deze opdracht wordt 120 seconden (twee minuten) gewacht totdat de DailyLog-taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-165">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span> <span data-ttu-id="3558e-166">Als de taak niet in de volgende twee minuten wordt voltooid, wordt de opdracht prompt toch geretourneerd en wordt de taak op de achtergrond uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3558e-166">If the job does not finish in the next two minutes, the command prompt returns anyway, and the job continues to run in the background.</span></span>

### <span data-ttu-id="3558e-167">Voor beeld 7: wachten op een taak op naam</span><span class="sxs-lookup"><span data-stu-id="3558e-167">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="3558e-168">Met deze opdracht wordt de taak naam gebruikt om de taak te identificeren waarvoor moet worden gewacht.</span><span class="sxs-lookup"><span data-stu-id="3558e-168">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="3558e-169">Voor beeld 8: wachten op taken op de lokale computer die is gestart met Start-Job</span><span class="sxs-lookup"><span data-stu-id="3558e-169">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="3558e-170">In dit voor beeld ziet u hoe u de `Wait-Job` cmdlet gebruikt met taken die zijn gestart op de lokale computer met behulp van `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="3558e-170">This example shows how to use the `Wait-Job` cmdlet with jobs started on the local computer by using `Start-Job`.</span></span>

<span data-ttu-id="3558e-171">Met deze opdrachten wordt een taak gestart waarmee de Windows Power shell-script bestanden worden opgehaald die in de afgelopen week zijn toegevoegd of bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="3558e-171">These commands start a job that gets the Windows PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="3558e-172">De eerste opdracht wordt gebruikt `Start-Job` om een achtergrond taak op de lokale computer te starten.</span><span class="sxs-lookup"><span data-stu-id="3558e-172">The first command uses `Start-Job` to start a background job on the local computer.</span></span> <span data-ttu-id="3558e-173">Met de taak wordt een `Get-ChildItem` opdracht uitgevoerd waarmee alle bestanden met de bestandsnaam extensie. ps1 worden opgehaald die in de afgelopen week zijn toegevoegd of bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="3558e-173">The job runs a `Get-ChildItem` command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="3558e-174">De derde opdracht wordt gebruikt `Wait-Job` om te wachten tot de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-174">The third command uses `Wait-Job` to wait until the job is completed.</span></span> <span data-ttu-id="3558e-175">Wanneer de taak is voltooid, wordt met de opdracht het taak object weer gegeven, dat informatie over de taak bevat.</span><span class="sxs-lookup"><span data-stu-id="3558e-175">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="3558e-176">Voor beeld 9: wachten op taken die zijn gestart op externe computers met behulp van Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="3558e-176">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="3558e-177">In dit voor beeld ziet u hoe u kunt gebruiken `Wait-Job` met taken die zijn gestart op externe computers met behulp van de para meter **AsJob** van `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="3558e-177">This example shows how to use `Wait-Job` with jobs started on remote computers by using the **AsJob** parameter of `Invoke-Command`.</span></span> <span data-ttu-id="3558e-178">Wanneer u **AsJob** gebruikt, wordt de taak op de lokale computer gemaakt en worden de resultaten automatisch naar de lokale computer geretourneerd, zelfs als de taak wordt uitgevoerd op de externe computers.</span><span class="sxs-lookup"><span data-stu-id="3558e-178">When using **AsJob** , the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="3558e-179">In dit voor beeld wordt gebruikt `Wait-Job` om te bepalen of een `Get-Process` opdracht die wordt uitgevoerd in de sessies op drie externe computers, is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-179">This example uses `Wait-Job` to determine whether a `Get-Process` command running in the sessions on three remote computers is completed.</span></span>

<span data-ttu-id="3558e-180">Met de eerste opdracht worden **PSSession** -objecten op drie computers gemaakt en opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="3558e-180">The first command creates **PSSession** objects on three computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="3558e-181">De tweede opdracht wordt gebruikt `Invoke-Command` om `Get-Process` in elk van de drie sessies in te worden uitgevoerd `$s` .</span><span class="sxs-lookup"><span data-stu-id="3558e-181">The second command uses `Invoke-Command` to run `Get-Process` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="3558e-182">De opdracht gebruikt de para meter **AsJob** om de opdracht asynchroon uit te voeren als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="3558e-182">The command uses the **AsJob** parameter to run the command asynchronously as a background job.</span></span> <span data-ttu-id="3558e-183">De opdracht retourneert een taak object, net zoals de taken die met `Start-Job` worden gestart, en het taak object wordt opgeslagen in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="3558e-183">The command returns a job object, just like the jobs started by using `Start-Job`, and the job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="3558e-184">De derde opdracht maakt gebruik van een pijplijn operator ( `|` ) voor het verzenden van het taak object in `$j` naar de `Wait-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3558e-184">The third command uses a pipeline operator (`|`) to send the job object in `$j` to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="3558e-185">`Invoke-Command`In dit geval is een opdracht niet vereist, omdat de taak zich op de lokale computer bevindt.</span><span class="sxs-lookup"><span data-stu-id="3558e-185">An `Invoke-Command` command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="3558e-186">Voor beeld 10: wachten op een taak met een ID</span><span class="sxs-lookup"><span data-stu-id="3558e-186">Example 10: Wait for a job that has an ID</span></span>

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

<span data-ttu-id="3558e-187">Met deze opdracht wordt gewacht op de taak met de ID-waarde 1.</span><span class="sxs-lookup"><span data-stu-id="3558e-187">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="3558e-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3558e-188">PARAMETERS</span></span>

### <span data-ttu-id="3558e-189">-Alle</span><span class="sxs-lookup"><span data-stu-id="3558e-189">-Any</span></span>

<span data-ttu-id="3558e-190">Geeft aan dat met deze cmdlet de opdracht prompt wordt weer gegeven en het taak object als resultaat wordt gegeven wanneer een taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-190">Indicates that this cmdlet displays the command prompt, and returns the job object, when any job finishes.</span></span> <span data-ttu-id="3558e-191">Standaard wordt `Wait-Job` gewacht totdat alle opgegeven taken zijn voltooid voordat de prompt wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3558e-191">By default, `Wait-Job` waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="3558e-192">-Filter</span><span class="sxs-lookup"><span data-stu-id="3558e-192">-Filter</span></span>

<span data-ttu-id="3558e-193">Hiermee geeft u een hash-tabel met voor waarden op.</span><span class="sxs-lookup"><span data-stu-id="3558e-193">Specifies a hash table of conditions.</span></span> <span data-ttu-id="3558e-194">Met deze cmdlet wordt gewacht op taken die voldoen aan alle voor waarden in de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="3558e-194">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="3558e-195">Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="3558e-195">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="3558e-196">Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken.</span><span class="sxs-lookup"><span data-stu-id="3558e-196">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="3558e-197">Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3558e-197">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="3558e-198">Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="3558e-198">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="3558e-199">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3558e-199">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3558e-200">-Force</span><span class="sxs-lookup"><span data-stu-id="3558e-200">-Force</span></span>

<span data-ttu-id="3558e-201">Hiermee wordt aangegeven dat deze cmdlet blijft wachten op taken met de status onderbroken of niet verbonden.</span><span class="sxs-lookup"><span data-stu-id="3558e-201">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span> <span data-ttu-id="3558e-202">`Wait-Job`Retourneert standaard of beëindigt de wacht tijd wanneer taken een van de volgende statussen hebben:</span><span class="sxs-lookup"><span data-stu-id="3558e-202">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="3558e-203">Voltooid</span><span class="sxs-lookup"><span data-stu-id="3558e-203">Completed</span></span>
- <span data-ttu-id="3558e-204">Mislukt</span><span class="sxs-lookup"><span data-stu-id="3558e-204">Failed</span></span>
- <span data-ttu-id="3558e-205">Gestopt</span><span class="sxs-lookup"><span data-stu-id="3558e-205">Stopped</span></span>
- <span data-ttu-id="3558e-206">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="3558e-206">Suspended</span></span>
- <span data-ttu-id="3558e-207">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="3558e-207">Disconnected</span></span>

<span data-ttu-id="3558e-208">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3558e-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3558e-209">-Id</span><span class="sxs-lookup"><span data-stu-id="3558e-209">-Id</span></span>

<span data-ttu-id="3558e-210">Hiermee geeft u een matrix met Id's van taken op waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="3558e-210">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="3558e-211">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="3558e-211">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="3558e-212">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="3558e-212">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="3558e-213">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="3558e-213">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="3558e-214">Als u de ID van een taak wilt zoeken, typt u `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="3558e-214">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="3558e-215">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="3558e-215">-InstanceId</span></span>

<span data-ttu-id="3558e-216">Hiermee geeft u een matrix met exemplaar-Id's op van taken waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="3558e-216">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span> <span data-ttu-id="3558e-217">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="3558e-217">The default is all jobs.</span></span>

<span data-ttu-id="3558e-218">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="3558e-218">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="3558e-219">Gebruik om de exemplaar-ID van een taak te vinden `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="3558e-219">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="3558e-220">-Taak</span><span class="sxs-lookup"><span data-stu-id="3558e-220">-Job</span></span>

<span data-ttu-id="3558e-221">Hiermee geeft u de taken op waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="3558e-221">Specifies the jobs for which this cmdlet waits.</span></span> <span data-ttu-id="3558e-222">Voer een variabele in die de taak objecten bevat of een opdracht waarmee de taak objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="3558e-222">Enter a variable that contains the job objects or a command that gets the job objects.</span></span> <span data-ttu-id="3558e-223">U kunt ook een pijplijn operator gebruiken om taak objecten te verzenden naar de `Wait-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3558e-223">You can also use a pipeline operator to send job objects to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="3558e-224">Standaard wordt `Wait-Job` gewacht op alle taken die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="3558e-224">By default, `Wait-Job` waits for all jobs created in the current session.</span></span>

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

### <span data-ttu-id="3558e-225">-Name</span><span class="sxs-lookup"><span data-stu-id="3558e-225">-Name</span></span>

<span data-ttu-id="3558e-226">Hiermee geeft u beschrijvende namen van taken op waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="3558e-226">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

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

### <span data-ttu-id="3558e-227">-Status</span><span class="sxs-lookup"><span data-stu-id="3558e-227">-State</span></span>

<span data-ttu-id="3558e-228">Hiermee geeft u een taak status op.</span><span class="sxs-lookup"><span data-stu-id="3558e-228">Specifies a job state.</span></span> <span data-ttu-id="3558e-229">Met deze cmdlet wordt alleen gewacht op taken in de opgegeven status.</span><span class="sxs-lookup"><span data-stu-id="3558e-229">This cmdlet waits only for jobs in the specified state.</span></span> <span data-ttu-id="3558e-230">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="3558e-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3558e-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="3558e-231">NotStarted</span></span>
- <span data-ttu-id="3558e-232">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="3558e-232">Running</span></span>
- <span data-ttu-id="3558e-233">Voltooid</span><span class="sxs-lookup"><span data-stu-id="3558e-233">Completed</span></span>
- <span data-ttu-id="3558e-234">Mislukt</span><span class="sxs-lookup"><span data-stu-id="3558e-234">Failed</span></span>
- <span data-ttu-id="3558e-235">Gestopt</span><span class="sxs-lookup"><span data-stu-id="3558e-235">Stopped</span></span>
- <span data-ttu-id="3558e-236">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="3558e-236">Blocked</span></span>
- <span data-ttu-id="3558e-237">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="3558e-237">Suspended</span></span>
- <span data-ttu-id="3558e-238">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="3558e-238">Disconnected</span></span>
- <span data-ttu-id="3558e-239">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="3558e-239">Suspending</span></span>
- <span data-ttu-id="3558e-240">Stoppen</span><span class="sxs-lookup"><span data-stu-id="3558e-240">Stopping</span></span>

<span data-ttu-id="3558e-241">Zie [JobState Enumeration](/dotnet/api/system.management.automation.jobstate)(Engelstalig) voor meer informatie over de status van een taak.</span><span class="sxs-lookup"><span data-stu-id="3558e-241">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="3558e-242">-Time-out</span><span class="sxs-lookup"><span data-stu-id="3558e-242">-Timeout</span></span>

<span data-ttu-id="3558e-243">Hiermee geeft u de maximale wacht tijd op voor elke achtergrond taak, in seconden.</span><span class="sxs-lookup"><span data-stu-id="3558e-243">Specifies the maximum wait time for each background job, in seconds.</span></span> <span data-ttu-id="3558e-244">De standaard waarde-1 geeft aan dat de cmdlet wacht totdat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3558e-244">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span> <span data-ttu-id="3558e-245">De tijds duur begint wanneer u de `Wait-Job` opdracht verzendt, niet de `Start-Job` opdracht.</span><span class="sxs-lookup"><span data-stu-id="3558e-245">The timing starts when you submit the `Wait-Job` command, not the `Start-Job` command.</span></span>

<span data-ttu-id="3558e-246">Als deze tijd wordt overschreden, worden de wacht tijden beëindigd en wordt de opdracht prompt weer gegeven, zelfs als de taak nog steeds wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3558e-246">If this time is exceeded, the wait ends and the command prompt returns, even if the job is still running.</span></span> <span data-ttu-id="3558e-247">Met de opdracht wordt geen fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3558e-247">The command does not display any error message.</span></span>

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

### <span data-ttu-id="3558e-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3558e-248">CommonParameters</span></span>

<span data-ttu-id="3558e-249">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3558e-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3558e-250">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3558e-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3558e-251">INVOER</span><span class="sxs-lookup"><span data-stu-id="3558e-251">INPUTS</span></span>

### <span data-ttu-id="3558e-252">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="3558e-252">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="3558e-253">U kunt een taak object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3558e-253">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="3558e-254">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3558e-254">OUTPUTS</span></span>

### <span data-ttu-id="3558e-255">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="3558e-255">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="3558e-256">Met deze cmdlet worden taak objecten geretourneerd die de voltooide taken vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="3558e-256">This cmdlet returns job objects that represent the completed jobs.</span></span> <span data-ttu-id="3558e-257">Als de wacht tijd eindigt omdat de waarde van de para meter **time-out** is overschreden, `Wait-Job` worden er geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3558e-257">If the wait ends because the value of the **Timeout** parameter is exceeded, `Wait-Job` does not return any objects.</span></span>

## <span data-ttu-id="3558e-258">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3558e-258">NOTES</span></span>

<span data-ttu-id="3558e-259">`Wait-Job`Retourneert standaard of beëindigt de wacht tijd wanneer taken een van de volgende statussen hebben:</span><span class="sxs-lookup"><span data-stu-id="3558e-259">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="3558e-260">Voltooid</span><span class="sxs-lookup"><span data-stu-id="3558e-260">Completed</span></span>
- <span data-ttu-id="3558e-261">Mislukt</span><span class="sxs-lookup"><span data-stu-id="3558e-261">Failed</span></span>
- <span data-ttu-id="3558e-262">Gestopt</span><span class="sxs-lookup"><span data-stu-id="3558e-262">Stopped</span></span>
- <span data-ttu-id="3558e-263">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="3558e-263">Suspended</span></span>
- <span data-ttu-id="3558e-264">De verbinding is verbroken zodat u `Wait-Job` verder kunt wachten op onderbroken en verbroken taken, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="3558e-264">Disconnected To direct `Wait-Job` to continue to wait for Suspended and Disconnected jobs, use the **Force** parameter.</span></span>

## <span data-ttu-id="3558e-265">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3558e-265">RELATED LINKS</span></span>

[<span data-ttu-id="3558e-266">Get-job</span><span class="sxs-lookup"><span data-stu-id="3558e-266">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="3558e-267">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="3558e-267">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="3558e-268">Receive-job</span><span class="sxs-lookup"><span data-stu-id="3558e-268">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="3558e-269">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="3558e-269">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="3558e-270">Begin taak</span><span class="sxs-lookup"><span data-stu-id="3558e-270">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="3558e-271">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="3558e-271">Stop-Job</span></span>](Stop-Job.md)
