---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: d364b04bef4a46a086af2b90a71c15f2ab3ddba5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249411"
---
# <span data-ttu-id="fb104-103">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="fb104-103">Wait-Job</span></span>

## <span data-ttu-id="fb104-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fb104-104">SYNOPSIS</span></span>
<span data-ttu-id="fb104-105">Onderdrukt de opdracht prompt totdat een of alle Power shell-achtergrond taken die in de sessie worden uitgevoerd, zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-105">Suppresses the command prompt until one or all of the PowerShell background jobs running in the session are completed.</span></span>

## <span data-ttu-id="fb104-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fb104-106">SYNTAX</span></span>

### <span data-ttu-id="fb104-107">SessionIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="fb104-107">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="fb104-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="fb104-108">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="fb104-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="fb104-109">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="fb104-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="fb104-110">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="fb104-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="fb104-111">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="fb104-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="fb104-112">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="fb104-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fb104-113">DESCRIPTION</span></span>

<span data-ttu-id="fb104-114">De **wacht opdracht-** cmdlet wacht totdat de Power shell-achtergrond taken zijn voltooid, voordat de-prompt wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fb104-114">The **Wait-Job** cmdlet waits for PowerShell background jobs to finish before it displays the command prompt.</span></span>
<span data-ttu-id="fb104-115">U kunt wachten tot een wille keurige achtergrond taak is voltooid of totdat alle achtergrond taken zijn voltooid en u een maximale wacht tijd voor de taak kunt instellen.</span><span class="sxs-lookup"><span data-stu-id="fb104-115">You can wait until any background job is complete, or until all background jobs are complete, and you can set a maximum wait time for the job.</span></span>

<span data-ttu-id="fb104-116">Wanneer de opdrachten in de taak zijn voltooid, wordt de opdracht prompt weer gegeven **en wordt een** taak object geretourneerd, zodat u het kunt door sluizen naar een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="fb104-116">When the commands in the job are complete, **Wait-Job** displays the command prompt and returns a job object so that you can pipe it to another command.</span></span>

<span data-ttu-id="fb104-117">U kunt de cmdlet **wacht opdracht** gebruiken om te wachten op achtergrond taken, zoals die zijn gestart met behulp van de cmdlet Start-Job of de para meter *AsJob* van de cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="fb104-117">You can use **Wait-Job** cmdlet to wait for background jobs, such as those that were started by using the Start-Job cmdlet or the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>
<span data-ttu-id="fb104-118">Zie about_Jobs voor meer informatie over Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="fb104-118">For more information about PowerShell background jobs, see about_Jobs.</span></span>

<span data-ttu-id="fb104-119">Vanaf Windows Power Shell 3,0 wacht de cmdlet **wait-job** ook op aangepaste taak typen, zoals werk stroom taken en exemplaren van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="fb104-119">Starting in Windows PowerShell 3.0, the **Wait-Job** cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="fb104-120">Als u **wacht** op taken van een bepaald type wilt wachten, importeert u de module die het aangepaste taak type ondersteunt in de sessie voordat u de cmdlet Get-Job uitvoert, met behulp van de Import-Module cmdlet of door een cmdlet in de module te gebruiken of op te halen.</span><span class="sxs-lookup"><span data-stu-id="fb104-120">To enable **Wait-Job** to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the Get-Job cmdlet, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="fb104-121">Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.</span><span class="sxs-lookup"><span data-stu-id="fb104-121">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="fb104-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fb104-122">EXAMPLES</span></span>

### <span data-ttu-id="fb104-123">Voor beeld 1: wachten op alle taken</span><span class="sxs-lookup"><span data-stu-id="fb104-123">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="fb104-124">Met deze opdracht wordt gewacht tot alle achtergrond taken die in de sessie worden uitgevoerd, worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-124">This command waits for all of the background jobs running in the session to finish.</span></span>

### <span data-ttu-id="fb104-125">Voor beeld 2: wachten op taken die zijn gestart op externe computers met behulp van Start-Job</span><span class="sxs-lookup"><span data-stu-id="fb104-125">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="fb104-126">In dit voor beeld ziet u hoe u de cmdlet **wait-job** gebruikt met taken die zijn gestart op externe computers met behulp van de cmdlet **Start-job** .</span><span class="sxs-lookup"><span data-stu-id="fb104-126">This example shows how to use the **Wait-Job** cmdlet with jobs started on remote computers by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="fb104-127">De opdrachten **Start-job** en **wait-job** worden verzonden naar de externe computer met behulp van de cmdlet **invoke-opdracht** .</span><span class="sxs-lookup"><span data-stu-id="fb104-127">Both **Start-Job** and **Wait-Job** commands are submitted to the remote computer by using the **Invoke-Command** cmdlet.</span></span>

<span data-ttu-id="fb104-128">In dit voor beeld wordt **wacht taak** gebruikt om te bepalen of een Get-Date-opdracht die als achtergrond taak wordt uitgevoerd op drie verschillende computers is voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-128">This example uses **Wait-Job** to determine whether a Get-Date command running as a background job on three different computers is finished.</span></span>

<span data-ttu-id="fb104-129">Met de eerste opdracht maakt u een Power shell-sessie ( **PSSession** ) op elk van de drie externe computers en slaat u deze op in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="fb104-129">The first command creates a PowerShell session ( **PSSession** ) on each of the three remote computers and stores them in the $s variable.</span></span>

<span data-ttu-id="fb104-130">Met de tweede opdracht wordt **invoke-opdracht** gebruikt voor het uitvoeren van **Start-taak** in elk van de drie sessies in $s.</span><span class="sxs-lookup"><span data-stu-id="fb104-130">The second command uses **Invoke-Command** to run **Start-Job** in each of the three sessions in $s.</span></span>
<span data-ttu-id="fb104-131">Alle taken hebben de naam Datum1.</span><span class="sxs-lookup"><span data-stu-id="fb104-131">All of the jobs are named Date1.</span></span>

<span data-ttu-id="fb104-132">De derde opdracht maakt gebruik van de **opdracht invoke** om een **wachtende taak** uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="fb104-132">The third command uses **Invoke-Command** to run **Wait-Job**.</span></span>
<span data-ttu-id="fb104-133">Met deze opdracht wordt gewacht op de Datum1-taken op elke computer om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="fb104-133">This command waits for the Date1 jobs on each computer to finish.</span></span>
<span data-ttu-id="fb104-134">De resulterende verzameling (matrix) van taak objecten wordt opgeslagen in de variabele $done.</span><span class="sxs-lookup"><span data-stu-id="fb104-134">It stores the resulting collection (array) of job objects in the $done variable.</span></span>

<span data-ttu-id="fb104-135">De vierde opdracht gebruikt de eigenschap **Count** van de matrix met taak objecten in de variabele $Done om te bepalen hoeveel taken zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-135">The fourth command uses the **Count** property of the array of job objects in the $done variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="fb104-136">Voor beeld 3: bepalen wanneer de eerste achtergrond taak is voltooid</span><span class="sxs-lookup"><span data-stu-id="fb104-136">Example 3: Determine when the first background job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="fb104-137">In dit voor beeld wordt de para meter van *een* **wachtende taak** gebruikt om te bepalen wanneer de eerste van de vele achtergrond taken die in de huidige sessie worden uitgevoerd, zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-137">This example uses the *Any* parameter of **Wait-Job** to determine when the first of many background jobs running in the current session are completed.</span></span>
<span data-ttu-id="fb104-138">U ziet ook hoe u de cmdlet **wait-job** gebruikt om te wachten tot externe taken zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-138">It also shows how to use the **Wait-Job** cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="fb104-139">Met de eerste opdracht maakt u een **PSSession** op elke computer die wordt vermeld in het Machines.txt-bestand en worden de **PSSession** -objecten opgeslagen in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="fb104-139">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the $s variable.</span></span>
<span data-ttu-id="fb104-140">De opdracht gebruikt de cmdlet Get-Content om de inhoud van het bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="fb104-140">The command uses the Get-Content cmdlet to get the contents of the file.</span></span>
<span data-ttu-id="fb104-141">De opdracht **Get-content** bevindt zich tussen haakjes om ervoor te zorgen dat deze wordt uitgevoerd vóór de opdracht New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="fb104-141">The **Get-Content** command is enclosed in parentheses to make sure that it runs before the New-PSSession command.</span></span>

<span data-ttu-id="fb104-142">Met de tweede opdracht wordt een teken reeks voor de opdracht **get-eventlog** opgeslagen, tussen aanhalings tekens in de variabele $c.</span><span class="sxs-lookup"><span data-stu-id="fb104-142">The second command stores a **Get-EventLog** command string, in quotation marks, in the $c variable.</span></span>

<span data-ttu-id="fb104-143">De derde opdracht maakt gebruik van Invoke-Command cmdlet om **Start-taak** uit te voeren in elk van de sessies in $s.</span><span class="sxs-lookup"><span data-stu-id="fb104-143">The third command uses Invoke-Command cmdlet to run **Start-Job** in each of the sessions in $s.</span></span>
<span data-ttu-id="fb104-144">Met de opdracht **Start-job** wordt een achtergrond taak gestart waarmee de opdracht **get-eventlog** wordt uitgevoerd in de variabele $c.</span><span class="sxs-lookup"><span data-stu-id="fb104-144">The **Start-Job** command starts a background job that runs the **Get-EventLog** command in the $c variable.</span></span>

<span data-ttu-id="fb104-145">De opdracht gebruikt de aanpassings functie voor het **gebruik** van het bereik om aan te geven dat de variabele $c op de lokale computer is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="fb104-145">The command uses the **Using** scope modifier to indicate that the $c variable was defined on the local computer.</span></span>
<span data-ttu-id="fb104-146">De aanpassings functie voor het **gebruik** van scopes is geïntroduceerd in Windows power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fb104-146">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span>
<span data-ttu-id="fb104-147">Zie [about_Remote_Variables](about/about_Remote_Variables.md)voor meer informatie **over de aanpassing van het** bereik.</span><span class="sxs-lookup"><span data-stu-id="fb104-147">For more information about the **Using** scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="fb104-148">De vierde opdracht gebruikt **invoke-opdracht** om een **wacht** opdracht uit te voeren in de sessies.</span><span class="sxs-lookup"><span data-stu-id="fb104-148">The fourth command uses **Invoke-Command** to run a **Wait-Job** command in the sessions.</span></span>
<span data-ttu-id="fb104-149">De *para meter* wordt gebruikt om te wachten tot de eerste taak op de externe computers is voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-149">It uses the *Any* parameter to wait until the first job on the remote computers is completed.</span></span>

### <span data-ttu-id="fb104-150">Voor beeld 4: een wacht tijd instellen voor taken op externe computers</span><span class="sxs-lookup"><span data-stu-id="fb104-150">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

<span data-ttu-id="fb104-151">In dit voor beeld ziet u hoe u de para meter *time-out* van **wacht taak** gebruikt om een maximale wacht tijd in te stellen voor de taken die worden uitgevoerd op externe computers.</span><span class="sxs-lookup"><span data-stu-id="fb104-151">This example shows how to use the *Timeout* parameter of **Wait-Job** to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="fb104-152">Met de eerste opdracht maakt u een **PSSession** op elk van de drie externe computers (Server01, Server02 en Server03), waarna de **PSSession** -objecten worden opgeslagen in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="fb104-152">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the $s variable.</span></span>

<span data-ttu-id="fb104-153">De tweede opdracht maakt gebruik van **invoke-opdracht** voor het uitvoeren van **Start-taak** in elk van de **PSSession** -objecten in $s.</span><span class="sxs-lookup"><span data-stu-id="fb104-153">The second command uses **Invoke-Command** to run **Start-Job** in each of the **PSSession** objects in $s.</span></span>
<span data-ttu-id="fb104-154">De resulterende taak objecten worden opgeslagen in de variabele $jobs.</span><span class="sxs-lookup"><span data-stu-id="fb104-154">It stores the resulting job objects in the $jobs variable.</span></span>

<span data-ttu-id="fb104-155">De derde opdracht gebruikt **invoke-opdracht** voor het uitvoeren van een **wachtende taak** in elk van de sessies in $s.</span><span class="sxs-lookup"><span data-stu-id="fb104-155">The third command uses **Invoke-Command** to run **Wait-Job** in each of the sessions in $s.</span></span>
<span data-ttu-id="fb104-156">De opdracht **wachten** bepaalt of alle opdrachten binnen 30 seconden zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-156">The **Wait-Job** command determines whether all of the commands have completed within 30 seconds.</span></span>
<span data-ttu-id="fb104-157">Hierbij wordt de para meter *time-out* met de waarde 30 gebruikt voor het instellen van de maximale wacht tijd en worden de resultaten van de opdracht opgeslagen in de variabele $done.</span><span class="sxs-lookup"><span data-stu-id="fb104-157">It uses the *Timeout* parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the $done variable.</span></span>

<span data-ttu-id="fb104-158">In dit geval, na 30 seconden, is alleen de opdracht op de Server02 computer voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-158">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span>
<span data-ttu-id="fb104-159">**Wacht taak** eindigt de wacht tijd, geeft de opdracht prompt en retourneert het object dat de voltooide taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="fb104-159">**Wait-Job** ends the wait, displays the command prompt, and returns the object that represents the job that was completed.</span></span>

<span data-ttu-id="fb104-160">De variabele $done bevat een taak object dat de taak vertegenwoordigt die is uitgevoerd op Server02.</span><span class="sxs-lookup"><span data-stu-id="fb104-160">The $done variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="fb104-161">Voor beeld 5: wachten tot een van de taken is voltooid</span><span class="sxs-lookup"><span data-stu-id="fb104-161">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="fb104-162">Met deze opdracht worden drie taken geïdentificeerd op basis van hun Id's en wordt gewacht totdat een van deze opdrachten is voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-162">This command identifies three jobs by their IDs and waits until any one of them are completed.</span></span>
<span data-ttu-id="fb104-163">De opdracht prompt wordt weer gegeven wanneer de eerste taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-163">The command prompt returns when the first job finishes.</span></span>

### <span data-ttu-id="fb104-164">Voor beeld 6: wachten op een periode, waarna de taak op de achtergrond kan worden voortgezet</span><span class="sxs-lookup"><span data-stu-id="fb104-164">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="fb104-165">Met deze opdracht wordt 120 seconden (twee minuten) gewacht totdat de DailyLog-taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-165">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span>
<span data-ttu-id="fb104-166">Als de taak niet in de volgende twee minuten wordt voltooid, wordt de opdracht prompt toch geretourneerd en wordt de taak op de achtergrond uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fb104-166">If the job does not finish in the next two minutes, the command prompt returns anyway, and the job continues to run in the background.</span></span>

### <span data-ttu-id="fb104-167">Voor beeld 7: wachten op een taak op naam</span><span class="sxs-lookup"><span data-stu-id="fb104-167">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="fb104-168">Met deze opdracht wordt de taak naam gebruikt om de taak te identificeren waarvoor moet worden gewacht.</span><span class="sxs-lookup"><span data-stu-id="fb104-168">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="fb104-169">Voor beeld 8: wachten op taken op de lokale computer die is gestart met Start-Job</span><span class="sxs-lookup"><span data-stu-id="fb104-169">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="fb104-170">In dit voor beeld ziet u hoe u de cmdlet **wait-job** gebruikt met taken die zijn gestart op de lokale computer met behulp van **Start-job**.</span><span class="sxs-lookup"><span data-stu-id="fb104-170">This example shows how to use the **Wait-Job** cmdlet with jobs started on the local computer by using **Start-Job**.</span></span>

<span data-ttu-id="fb104-171">Met deze opdrachten wordt een taak gestart waarmee de Power shell-script bestanden worden opgehaald die in de afgelopen week zijn toegevoegd of bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="fb104-171">These commands start a job that gets the PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="fb104-172">De eerste opdracht maakt gebruik van **Start-taak** om een achtergrond taak op de lokale computer te starten.</span><span class="sxs-lookup"><span data-stu-id="fb104-172">The first command uses **Start-Job** to start a background job on the local computer.</span></span>
<span data-ttu-id="fb104-173">De taak voert een Get-ChildItem-opdracht uit waarmee alle bestanden met de bestandsnaam extensie. ps1 die in de afgelopen week zijn toegevoegd of bijgewerkt, worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fb104-173">The job runs a Get-ChildItem command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="fb104-174">De derde opdracht gebruikt **wacht tijden** om te wachten tot de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-174">The third command uses **Wait-Job** to wait until the job is completed.</span></span>
<span data-ttu-id="fb104-175">Wanneer de taak is voltooid, wordt met de opdracht het taak object weer gegeven, dat informatie over de taak bevat.</span><span class="sxs-lookup"><span data-stu-id="fb104-175">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="fb104-176">Voor beeld 9: wachten op taken die zijn gestart op externe computers met behulp van Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="fb104-176">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="fb104-177">In dit voor beeld ziet u hoe u **wacht** opdrachten gebruikt met taken die zijn gestart op externe computers met behulp van de para meter *AsJob* van **invoke-Command**.</span><span class="sxs-lookup"><span data-stu-id="fb104-177">This example shows how to use **Wait-Job** with jobs started on remote computers by using the *AsJob* parameter of **Invoke-Command**.</span></span>
<span data-ttu-id="fb104-178">Wanneer u *AsJob* gebruikt, wordt de taak op de lokale computer gemaakt en worden de resultaten automatisch naar de lokale computer geretourneerd, zelfs als de taak wordt uitgevoerd op de externe computers.</span><span class="sxs-lookup"><span data-stu-id="fb104-178">When using *AsJob* , the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="fb104-179">In dit voor beeld wordt **wacht taak** gebruikt om te bepalen of een **Get-process-** opdracht die wordt uitgevoerd in de sessies op drie externe computers, is voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-179">This example uses **Wait-Job** to determine whether a **Get-Process** command running in the sessions on three remote computers is completed.</span></span>

<span data-ttu-id="fb104-180">Met de eerste opdracht worden **PSSession** -objecten op drie computers gemaakt en opgeslagen in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="fb104-180">The first command creates **PSSession** objects on three computers and stores them in the $s variable.</span></span>

<span data-ttu-id="fb104-181">De tweede opdracht gebruikt u **invoke-opdracht** voor het uitvoeren van **Get-process** in elk van de drie sessies in $s.</span><span class="sxs-lookup"><span data-stu-id="fb104-181">The second command uses **Invoke-Command** to run **Get-Process** in each of the three sessions in $s.</span></span>
<span data-ttu-id="fb104-182">De opdracht gebruikt de para meter *AsJob* om de opdracht asynchroon uit te voeren als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="fb104-182">The command uses the *AsJob* parameter to run the command asynchronously as a background job.</span></span>
<span data-ttu-id="fb104-183">De opdracht retourneert een taak object, net zoals de taken die zijn gestart met behulp van **Start taak** en het taak object wordt opgeslagen in de variabele $j.</span><span class="sxs-lookup"><span data-stu-id="fb104-183">The command returns a job object, just like the jobs started by using **Start-Job** , and the job object is stored in the $j variable.</span></span>

<span data-ttu-id="fb104-184">De derde opdracht maakt gebruik van een pijplijn operator (|) om het taak object in $j te verzenden naar de cmdlet **wait-job** .</span><span class="sxs-lookup"><span data-stu-id="fb104-184">The third command uses a pipeline operator (|) to send the job object in $j to the **Wait-Job** cmdlet.</span></span>
<span data-ttu-id="fb104-185">Een opdracht **invoke-opdracht** is in dit geval niet vereist omdat de taak zich op de lokale computer bevindt.</span><span class="sxs-lookup"><span data-stu-id="fb104-185">An **Invoke-Command** command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="fb104-186">Voor beeld 10: wachten op een taak met een ID</span><span class="sxs-lookup"><span data-stu-id="fb104-186">Example 10: Wait for a job that has an ID</span></span>

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

<span data-ttu-id="fb104-187">Met deze opdracht wordt gewacht op de taak met de ID-waarde 1.</span><span class="sxs-lookup"><span data-stu-id="fb104-187">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="fb104-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fb104-188">PARAMETERS</span></span>

### <span data-ttu-id="fb104-189">-Alle</span><span class="sxs-lookup"><span data-stu-id="fb104-189">-Any</span></span>

<span data-ttu-id="fb104-190">Geeft aan dat met deze cmdlet de opdracht prompt wordt weer gegeven en het taak object als resultaat wordt gegeven wanneer een taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-190">Indicates that this cmdlet displays the command prompt, and returns the job object, when any job finishes.</span></span>
<span data-ttu-id="fb104-191">**Wacht** totdat alle opgegeven taken zijn voltooid, wordt standaard gewacht voordat de prompt wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fb104-191">By default, **Wait-Job** waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="fb104-192">-Filter</span><span class="sxs-lookup"><span data-stu-id="fb104-192">-Filter</span></span>

<span data-ttu-id="fb104-193">Hiermee geeft u een hash-tabel met voor waarden op.</span><span class="sxs-lookup"><span data-stu-id="fb104-193">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="fb104-194">Met deze cmdlet wordt gewacht op taken die voldoen aan alle voor waarden in de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="fb104-194">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span>
<span data-ttu-id="fb104-195">Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="fb104-195">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="fb104-196">Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken.</span><span class="sxs-lookup"><span data-stu-id="fb104-196">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="fb104-197">Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .</span><span class="sxs-lookup"><span data-stu-id="fb104-197">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="fb104-198">Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="fb104-198">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="fb104-199">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fb104-199">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="fb104-200">-Force</span><span class="sxs-lookup"><span data-stu-id="fb104-200">-Force</span></span>

<span data-ttu-id="fb104-201">Hiermee wordt aangegeven dat deze cmdlet blijft wachten op taken met de status onderbroken of niet verbonden.</span><span class="sxs-lookup"><span data-stu-id="fb104-201">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span>
<span data-ttu-id="fb104-202">Standaard retourneert een **wacht opdracht** of de wacht tijd wanneer taken een van de volgende statussen hebben:</span><span class="sxs-lookup"><span data-stu-id="fb104-202">By default, **Wait-Job** returns, or ends  the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="fb104-203">Voltooid</span><span class="sxs-lookup"><span data-stu-id="fb104-203">Completed</span></span>
- <span data-ttu-id="fb104-204">Mislukt</span><span class="sxs-lookup"><span data-stu-id="fb104-204">Failed</span></span>
- <span data-ttu-id="fb104-205">Gestopt</span><span class="sxs-lookup"><span data-stu-id="fb104-205">Stopped</span></span>
- <span data-ttu-id="fb104-206">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="fb104-206">Suspended</span></span>
- <span data-ttu-id="fb104-207">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="fb104-207">Disconnected</span></span>

<span data-ttu-id="fb104-208">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fb104-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="fb104-209">-Id</span><span class="sxs-lookup"><span data-stu-id="fb104-209">-Id</span></span>

<span data-ttu-id="fb104-210">Hiermee geeft u een matrix met Id's van taken op waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="fb104-210">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="fb104-211">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="fb104-211">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="fb104-212">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="fb104-212">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="fb104-213">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="fb104-213">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="fb104-214">Als u de ID van een taak wilt zoeken, typt u `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="fb104-214">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="fb104-215">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="fb104-215">-InstanceId</span></span>

<span data-ttu-id="fb104-216">Hiermee geeft u een matrix met exemplaar-Id's op van taken waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="fb104-216">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span>
<span data-ttu-id="fb104-217">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="fb104-217">The default is all jobs.</span></span>

<span data-ttu-id="fb104-218">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="fb104-218">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="fb104-219">Gebruik **Get-job** om de exemplaar-id van een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="fb104-219">To find the instance ID of a job, use **Get-Job**.</span></span>

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

### <span data-ttu-id="fb104-220">-Taak</span><span class="sxs-lookup"><span data-stu-id="fb104-220">-Job</span></span>

<span data-ttu-id="fb104-221">Hiermee geeft u de taken op waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="fb104-221">Specifies the jobs for which this cmdlet waits.</span></span>
<span data-ttu-id="fb104-222">Voer een variabele in die de taak objecten bevat of een opdracht waarmee de taak objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fb104-222">Enter a variable that contains the job objects or a command that gets the job objects.</span></span>
<span data-ttu-id="fb104-223">U kunt ook een pijplijn operator gebruiken om taak objecten te verzenden naar de cmdlet **wait-job** .</span><span class="sxs-lookup"><span data-stu-id="fb104-223">You can also use a pipeline operator to send job objects to the **Wait-Job** cmdlet.</span></span>
<span data-ttu-id="fb104-224">Standaard **wacht een wachten op** alle taken die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fb104-224">By default, **Wait-Job** waits for all jobs created in the current session.</span></span>

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

### <span data-ttu-id="fb104-225">-Name</span><span class="sxs-lookup"><span data-stu-id="fb104-225">-Name</span></span>

<span data-ttu-id="fb104-226">Hiermee geeft u beschrijvende namen van taken op waarvoor deze cmdlet wacht.</span><span class="sxs-lookup"><span data-stu-id="fb104-226">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

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

### <span data-ttu-id="fb104-227">-Status</span><span class="sxs-lookup"><span data-stu-id="fb104-227">-State</span></span>

<span data-ttu-id="fb104-228">Hiermee geeft u een taak status op.</span><span class="sxs-lookup"><span data-stu-id="fb104-228">Specifies a job state.</span></span>
<span data-ttu-id="fb104-229">Met deze cmdlet wordt alleen gewacht op taken in de opgegeven status.</span><span class="sxs-lookup"><span data-stu-id="fb104-229">This cmdlet waits only for jobs in the specified state.</span></span>
<span data-ttu-id="fb104-230">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="fb104-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fb104-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="fb104-231">NotStarted</span></span>
- <span data-ttu-id="fb104-232">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="fb104-232">Running</span></span>
- <span data-ttu-id="fb104-233">Voltooid</span><span class="sxs-lookup"><span data-stu-id="fb104-233">Completed</span></span>
- <span data-ttu-id="fb104-234">Mislukt</span><span class="sxs-lookup"><span data-stu-id="fb104-234">Failed</span></span>
- <span data-ttu-id="fb104-235">Gestopt</span><span class="sxs-lookup"><span data-stu-id="fb104-235">Stopped</span></span>
- <span data-ttu-id="fb104-236">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="fb104-236">Blocked</span></span>
- <span data-ttu-id="fb104-237">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="fb104-237">Suspended</span></span>
- <span data-ttu-id="fb104-238">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="fb104-238">Disconnected</span></span>
- <span data-ttu-id="fb104-239">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="fb104-239">Suspending</span></span>
- <span data-ttu-id="fb104-240">Stoppen</span><span class="sxs-lookup"><span data-stu-id="fb104-240">Stopping</span></span>

<span data-ttu-id="fb104-241">Zie [JobState Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.jobstate) in de MSDN-bibliotheek voor meer informatie over de status van de taak.</span><span class="sxs-lookup"><span data-stu-id="fb104-241">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="fb104-242">-Time-out</span><span class="sxs-lookup"><span data-stu-id="fb104-242">-Timeout</span></span>

<span data-ttu-id="fb104-243">Hiermee geeft u de maximale wacht tijd op voor elke achtergrond taak, in seconden.</span><span class="sxs-lookup"><span data-stu-id="fb104-243">Specifies the maximum wait time for each background job, in seconds.</span></span>
<span data-ttu-id="fb104-244">De standaard waarde-1 geeft aan dat de cmdlet wacht totdat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="fb104-244">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span>
<span data-ttu-id="fb104-245">De tijds duur begint wanneer u de opdracht **wacht** op te sturen, niet de opdracht **Start-job** .</span><span class="sxs-lookup"><span data-stu-id="fb104-245">The timing starts when you submit the **Wait-Job** command, not the **Start-Job** command.</span></span>

<span data-ttu-id="fb104-246">Als deze tijd wordt overschreden, worden de wacht tijden beëindigd en wordt de opdracht prompt weer gegeven, zelfs als de taak nog steeds wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fb104-246">If this time is exceeded, the wait ends and the command prompt returns, even if the job is still running.</span></span>
<span data-ttu-id="fb104-247">Met de opdracht wordt geen fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fb104-247">The command does not display any error message.</span></span>

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

### <span data-ttu-id="fb104-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb104-248">CommonParameters</span></span>

<span data-ttu-id="fb104-249">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fb104-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fb104-250">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fb104-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fb104-251">INVOER</span><span class="sxs-lookup"><span data-stu-id="fb104-251">INPUTS</span></span>

### <span data-ttu-id="fb104-252">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="fb104-252">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="fb104-253">U kunt een taak object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb104-253">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="fb104-254">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fb104-254">OUTPUTS</span></span>

### <span data-ttu-id="fb104-255">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="fb104-255">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="fb104-256">Met deze cmdlet worden taak objecten geretourneerd die de voltooide taken vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="fb104-256">This cmdlet returns job objects that represent the completed jobs.</span></span>
<span data-ttu-id="fb104-257">Als de wacht tijd eindigt omdat de waarde van de para meter *time-out* is overschreden, worden er geen objecten geretourneerd met een **wacht opdracht** .</span><span class="sxs-lookup"><span data-stu-id="fb104-257">If the wait ends because the value of the *Timeout* parameter is exceeded, **Wait-Job** does not return any objects.</span></span>

## <span data-ttu-id="fb104-258">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fb104-258">NOTES</span></span>

* <span data-ttu-id="fb104-259">Standaard retourneert een **wacht opdracht** of de wacht tijd wanneer taken een van de volgende statussen hebben:</span><span class="sxs-lookup"><span data-stu-id="fb104-259">By default, **Wait-Job** returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="fb104-260">Voltooid</span><span class="sxs-lookup"><span data-stu-id="fb104-260">Completed</span></span>
- <span data-ttu-id="fb104-261">Mislukt</span><span class="sxs-lookup"><span data-stu-id="fb104-261">Failed</span></span>
- <span data-ttu-id="fb104-262">Gestopt</span><span class="sxs-lookup"><span data-stu-id="fb104-262">Stopped</span></span>
- <span data-ttu-id="fb104-263">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="fb104-263">Suspended</span></span>
- <span data-ttu-id="fb104-264">De verbinding met de directe **wacht taak** is verbroken. Als u wilt blijven wachten op onderbroken en verbroken taken, gebruikt u de para meter *Force* .</span><span class="sxs-lookup"><span data-stu-id="fb104-264">Disconnected To direct **Wait-Job** to continue to wait for Suspended and Disconnected jobs, use the *Force* parameter.</span></span>

## <span data-ttu-id="fb104-265">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fb104-265">RELATED LINKS</span></span>

[<span data-ttu-id="fb104-266">Get-job</span><span class="sxs-lookup"><span data-stu-id="fb104-266">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="fb104-267">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="fb104-267">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="fb104-268">Receive-job</span><span class="sxs-lookup"><span data-stu-id="fb104-268">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="fb104-269">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="fb104-269">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="fb104-270">Begin taak</span><span class="sxs-lookup"><span data-stu-id="fb104-270">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="fb104-271">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="fb104-271">Stop-Job</span></span>](Stop-Job.md)
