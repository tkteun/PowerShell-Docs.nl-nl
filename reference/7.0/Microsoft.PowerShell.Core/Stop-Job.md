---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 1f00d08ec97d20c3d353c22e8f7abfee7c88621a
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249426"
---
# <span data-ttu-id="beec1-103">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="beec1-103">Stop-Job</span></span>

## <span data-ttu-id="beec1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="beec1-104">SYNOPSIS</span></span>
<span data-ttu-id="beec1-105">Hiermee stopt u een Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="beec1-105">Stops a PowerShell background job.</span></span>

## <span data-ttu-id="beec1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="beec1-106">SYNTAX</span></span>

### <span data-ttu-id="beec1-107">SessionIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="beec1-107">SessionIdParameterSet (Default)</span></span>

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="beec1-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="beec1-108">JobParameterSet</span></span>

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="beec1-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="beec1-109">NameParameterSet</span></span>

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="beec1-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="beec1-110">InstanceIdParameterSet</span></span>

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="beec1-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="beec1-111">StateParameterSet</span></span>

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="beec1-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="beec1-112">FilterParameterSet</span></span>

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="beec1-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="beec1-113">DESCRIPTION</span></span>

<span data-ttu-id="beec1-114">De cmdlet **Stop-job** stopt Power shell-achtergrond taken die worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="beec1-114">The **Stop-Job** cmdlet stops PowerShell background jobs that are in progress.</span></span>
<span data-ttu-id="beec1-115">U kunt deze cmdlet gebruiken om alle taken te stoppen of de geselecteerde taken te stoppen op basis van hun naam, ID, exemplaar-ID of status, of door een taak object door te geven om de **taak te stoppen**.</span><span class="sxs-lookup"><span data-stu-id="beec1-115">You can use this cmdlet to stop all jobs or stop selected jobs based on their name, ID, instance ID, or state, or by passing a job object to **Stop-Job**.</span></span>

<span data-ttu-id="beec1-116">U kunt **Stop-job** gebruiken om achtergrond taken te stoppen, zoals die zijn gestart met behulp van de cmdlet Start-Job of de para meter *AsJob* van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="beec1-116">You can use **Stop-Job** to stop background jobs, such as those that were started by using the Start-Job cmdlet or the *AsJob* parameter of any cmdlet.</span></span>
<span data-ttu-id="beec1-117">Wanneer u een achtergrond taak stopt, worden alle taken die in de taak wachtrij in behandeling zijn, door Power Shell voltooid en wordt de taak vervolgens beëindigd.</span><span class="sxs-lookup"><span data-stu-id="beec1-117">When you stop a background job, PowerShell completes all tasks that are pending in that job queue and then ends the job.</span></span>
<span data-ttu-id="beec1-118">Er worden geen nieuwe taken aan de wachtrij toegevoegd nadat deze opdracht is verzonden.</span><span class="sxs-lookup"><span data-stu-id="beec1-118">No new tasks are added to the queue after this command is submitted.</span></span>

<span data-ttu-id="beec1-119">Met deze cmdlet worden geen achtergrond taken verwijderd.</span><span class="sxs-lookup"><span data-stu-id="beec1-119">This cmdlet does not delete background jobs.</span></span>
<span data-ttu-id="beec1-120">Als u een taak wilt verwijderen, gebruikt u de cmdlet Remove-Job.</span><span class="sxs-lookup"><span data-stu-id="beec1-120">To delete a job, use the Remove-Job cmdlet.</span></span>

<span data-ttu-id="beec1-121">Vanuit Windows Power Shell 3,0 stopt **Stop-job** ook aangepaste taak typen, zoals werk stroom taken en exemplaren van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="beec1-121">Starting in Windows PowerShell 3.0, **Stop-Job** also stops custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="beec1-122">Als u **stoppen-taak** wilt inschakelen voor het stoppen van een taak met een aangepast taak type, importeert u de module die het aangepaste taak type in de sessie ondersteunt voordat u een **Stop** opdracht uitvoert, hetzij met behulp van de cmdlet Import-Module, hetzij door een cmdlet in de module te gebruiken of op te halen.</span><span class="sxs-lookup"><span data-stu-id="beec1-122">To enable **Stop-Job** to stop a job with custom job type, import the module that supports the custom job type into the session before you run a **Stop-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="beec1-123">Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.</span><span class="sxs-lookup"><span data-stu-id="beec1-123">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="beec1-124">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="beec1-124">EXAMPLES</span></span>

### <span data-ttu-id="beec1-125">Voor beeld 1: een taak stoppen op een externe computer met behulp van Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="beec1-125">Example 1: Stop a job on a remote computer by using Invoke-Command</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

<span data-ttu-id="beec1-126">In dit voor beeld ziet u hoe u de cmdlet **Stop-job** gebruikt voor het stoppen van een taak die wordt uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="beec1-126">This example shows how to use the **Stop-Job** cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="beec1-127">Omdat de taak is gestart met behulp van de cmdlet Invoke-Command voor het extern uitvoeren van een opdracht voor starten van de **taak** , wordt het taak object op de externe computer opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="beec1-127">Because the job was started by using the Invoke-Command cmdlet to run a **Start-Job** command remotely, the job object is stored on the remote computer.</span></span>
<span data-ttu-id="beec1-128">U moet een andere opdracht **invoke-opdracht** gebruiken om de opdracht **Stop-job** op afstand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="beec1-128">You must use another **Invoke-Command** command to run a **Stop-Job** command remotely.</span></span>
<span data-ttu-id="beec1-129">Zie about_Remote_Jobs voor meer informatie over externe achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="beec1-129">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

<span data-ttu-id="beec1-130">Met de eerste opdracht maakt u een Power shell-sessie ( **PSSession** ) op de Server01-computer. vervolgens slaat u het sessie object op in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="beec1-130">The first command creates a PowerShell session ( **PSSession** ) on the Server01 computer, and then stores the session object in the $s variable.</span></span>
<span data-ttu-id="beec1-131">De opdracht gebruikt de referenties van een domein beheerder.</span><span class="sxs-lookup"><span data-stu-id="beec1-131">The command uses the credentials of a domain administrator.</span></span>

<span data-ttu-id="beec1-132">Met de tweede opdracht wordt de cmdlet **invoke-opdracht** gebruikt voor het uitvoeren van een **Start-taak** opdracht in de sessie.</span><span class="sxs-lookup"><span data-stu-id="beec1-132">The second command uses the **Invoke-Command** cmdlet to run a **Start-Job** command in the session.</span></span>
<span data-ttu-id="beec1-133">Met de opdracht in de taak worden alle gebeurtenissen in het systeem gebeurtenis logboek opgehaald.</span><span class="sxs-lookup"><span data-stu-id="beec1-133">The command in the job gets all of the events in the System event log.</span></span>
<span data-ttu-id="beec1-134">Het resulterende taak object wordt opgeslagen in de variabele $j.</span><span class="sxs-lookup"><span data-stu-id="beec1-134">The resulting job object is stored in the $j variable.</span></span>

<span data-ttu-id="beec1-135">Met de derde opdracht wordt de taak gestopt.</span><span class="sxs-lookup"><span data-stu-id="beec1-135">The third command stops the job.</span></span>
<span data-ttu-id="beec1-136">De cmdlet **invoke-opdracht** wordt gebruikt om een opdracht **Stop-job** uit te voeren in de **PSSession** op Server01.</span><span class="sxs-lookup"><span data-stu-id="beec1-136">It uses the **Invoke-Command** cmdlet to run a **Stop-Job** command in the **PSSession** on Server01.</span></span>
<span data-ttu-id="beec1-137">Omdat de taak objecten worden opgeslagen in $j, wat een variabele is op de lokale computer, gebruikt de opdracht de aanpassings functie voor het gebruik van scope om $j als een lokale variabele te identificeren.</span><span class="sxs-lookup"><span data-stu-id="beec1-137">Because the job objects are stored in $j, which is a variable on the local computer, the command uses the Using scope modifier to identify $j as a local variable.</span></span>
<span data-ttu-id="beec1-138">Zie [about_Remote_Variables](about/about_Remote_Variables.md)voor meer informatie over de aanpassing van het bereik.</span><span class="sxs-lookup"><span data-stu-id="beec1-138">For more information about the Using scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="beec1-139">Wanneer de opdracht is voltooid, wordt de taak gestopt en is de **PSSession** in $s beschikbaar voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="beec1-139">When the command finishes, the job is stopped and the **PSSession** in $s is available for use.</span></span>

### <span data-ttu-id="beec1-140">Voor beeld 2: een achtergrond taak stoppen</span><span class="sxs-lookup"><span data-stu-id="beec1-140">Example 2: Stop a background job</span></span>

```powershell
Stop-Job -Name "Job1"
```

<span data-ttu-id="beec1-141">Met deze opdracht wordt de Taak1-achtergrond taak gestopt.</span><span class="sxs-lookup"><span data-stu-id="beec1-141">This command stops the Job1 background job.</span></span>

### <span data-ttu-id="beec1-142">Voor beeld 3: meerdere achtergrond taken stoppen</span><span class="sxs-lookup"><span data-stu-id="beec1-142">Example 3: Stop several background jobs</span></span>

```powershell
Stop-Job -Id 1, 3, 4
```

<span data-ttu-id="beec1-143">Met deze opdracht worden drie taken gestopt.</span><span class="sxs-lookup"><span data-stu-id="beec1-143">This command stops three jobs.</span></span>
<span data-ttu-id="beec1-144">Ze worden geïdentificeerd aan de hand van hun Id's.</span><span class="sxs-lookup"><span data-stu-id="beec1-144">It identifies them by their IDs.</span></span>

### <span data-ttu-id="beec1-145">Voor beeld 4: alle achtergrond taken stoppen</span><span class="sxs-lookup"><span data-stu-id="beec1-145">Example 4: Stop all background jobs</span></span>

```powershell
Get-Job | Stop-Job
```

<span data-ttu-id="beec1-146">Met deze opdracht worden alle achtergrond taken in de huidige sessie gestopt.</span><span class="sxs-lookup"><span data-stu-id="beec1-146">This command stops all of the background jobs in the current session.</span></span>

### <span data-ttu-id="beec1-147">Voor beeld 5: alle geblokkeerde achtergrond taken stoppen</span><span class="sxs-lookup"><span data-stu-id="beec1-147">Example 5: Stop all blocked background jobs</span></span>

```powershell
Stop-Job -State Blocked
```

<span data-ttu-id="beec1-148">Met deze opdracht worden alle geblokkeerde taken gestopt.</span><span class="sxs-lookup"><span data-stu-id="beec1-148">This command stops all the jobs that are blocked.</span></span>

### <span data-ttu-id="beec1-149">Voor beeld 6: een taak stoppen met een exemplaar-ID</span><span class="sxs-lookup"><span data-stu-id="beec1-149">Example 6: Stop a job by using an instance ID</span></span>

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

<span data-ttu-id="beec1-150">Deze opdrachten laten zien hoe u een taak kunt stoppen op basis van de exemplaar-ID.</span><span class="sxs-lookup"><span data-stu-id="beec1-150">These commands show how to stop a job based on its instance ID.</span></span>

<span data-ttu-id="beec1-151">De eerste opdracht gebruikt de cmdlet Get-Job om de taken in de huidige sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="beec1-151">The first command uses the Get-Job cmdlet to get the jobs in the current session.</span></span>
<span data-ttu-id="beec1-152">De opdracht maakt gebruik van een pijplijn operator (|) om de taken te verzenden naar een Format-Table opdracht, waarin een tabel van de opgegeven eigenschappen van elke taak wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="beec1-152">The command uses a pipeline operator (|) to send the jobs to a Format-Table command, which displays a table of the specified properties of each job.</span></span>
<span data-ttu-id="beec1-153">De tabel bevat de exemplaar-ID van elke taak.</span><span class="sxs-lookup"><span data-stu-id="beec1-153">The table includes the Instance ID of each job.</span></span>
<span data-ttu-id="beec1-154">Er wordt een berekende eigenschap gebruikt om de taak status weer te geven.</span><span class="sxs-lookup"><span data-stu-id="beec1-154">It uses a calculated property to display the job state.</span></span>

<span data-ttu-id="beec1-155">De tweede opdracht maakt gebruik van een **stop-taak** opdracht die de para meter *InstanceId* heeft om een geselecteerde taak te stoppen.</span><span class="sxs-lookup"><span data-stu-id="beec1-155">The second command uses a **Stop-Job** command that has the *InstanceID* parameter to stop a selected job.</span></span>

### <span data-ttu-id="beec1-156">Voor beeld 7: een taak stoppen op een externe computer</span><span class="sxs-lookup"><span data-stu-id="beec1-156">Example 7: Stop a job on a remote computer</span></span>

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

<span data-ttu-id="beec1-157">In dit voor beeld ziet u hoe u de cmdlet **Stop-job** gebruikt voor het stoppen van een taak die wordt uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="beec1-157">This example shows how to use the **Stop-Job** cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="beec1-158">Omdat de taak is gestart met behulp van de para meter *AsJob* van de cmdlet **invoke-opdracht** , bevindt het taak object zich op de lokale computer, zelfs als de taak wordt uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="beec1-158">Because the job was started by using the *AsJob* parameter of the **Invoke-Command** cmdlet, the job object is located on the local computer, even though the job runs on the remote computer.</span></span>
<span data-ttu-id="beec1-159">Daarom kunt u een lokale **stop-taak** opdracht gebruiken om de taak te stoppen.</span><span class="sxs-lookup"><span data-stu-id="beec1-159">Therefore, you can use a local **Stop-Job** command to stop the job.</span></span>

<span data-ttu-id="beec1-160">Met de eerste opdracht wordt de cmdlet **invoke-opdracht** gebruikt om een achtergrond taak op de Server01-computer te starten.</span><span class="sxs-lookup"><span data-stu-id="beec1-160">The first command uses the **Invoke-Command** cmdlet to start a background job on the Server01 computer.</span></span>
<span data-ttu-id="beec1-161">De opdracht gebruikt de para meter *AsJob* om de externe opdracht als achtergrond taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="beec1-161">The command uses the *AsJob* parameter to run the remote command as a background job.</span></span>

<span data-ttu-id="beec1-162">Met deze opdracht wordt een taak object geretourneerd. Dit is hetzelfde taak object dat door de cmdlet **Start-job** wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="beec1-162">This command returns a job object, which is the same job object that the **Start-Job** cmdlet returns.</span></span>
<span data-ttu-id="beec1-163">Met de opdracht slaat u het taak object op in de variabele $j.</span><span class="sxs-lookup"><span data-stu-id="beec1-163">The command saves the job object in the $j variable.</span></span>

<span data-ttu-id="beec1-164">De tweede opdracht maakt gebruik van een pijplijn operator om de taak te verzenden in de $j variabele om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="beec1-164">The second command uses a pipeline operator to send the job in the $j variable to Stop-Job.</span></span>
<span data-ttu-id="beec1-165">De opdracht gebruikt de para meter *PassThru* om **Stop-job** te sturen om een taak object te retour neren.</span><span class="sxs-lookup"><span data-stu-id="beec1-165">The command uses the *PassThru* parameter to direct **Stop-Job** to return a job object.</span></span>
<span data-ttu-id="beec1-166">In de weer gave taak object wordt bevestigd dat de status van de taak is gestopt.</span><span class="sxs-lookup"><span data-stu-id="beec1-166">The job object display confirms that the state of the job is Stopped.</span></span>

<span data-ttu-id="beec1-167">Zie about_Remote_Jobs voor meer informatie over externe achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="beec1-167">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

## <span data-ttu-id="beec1-168">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="beec1-168">PARAMETERS</span></span>

### <span data-ttu-id="beec1-169">-Filter</span><span class="sxs-lookup"><span data-stu-id="beec1-169">-Filter</span></span>

<span data-ttu-id="beec1-170">Hiermee geeft u een hash-tabel met voor waarden op.</span><span class="sxs-lookup"><span data-stu-id="beec1-170">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="beec1-171">Met deze cmdlet worden taken gestopt die voldoen aan alle voor waarden.</span><span class="sxs-lookup"><span data-stu-id="beec1-171">This cmdlet stops jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="beec1-172">Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="beec1-172">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="beec1-173">Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken.</span><span class="sxs-lookup"><span data-stu-id="beec1-173">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="beec1-174">Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .</span><span class="sxs-lookup"><span data-stu-id="beec1-174">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="beec1-175">Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="beec1-175">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="beec1-176">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="beec1-176">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="beec1-177">-Id</span><span class="sxs-lookup"><span data-stu-id="beec1-177">-Id</span></span>

<span data-ttu-id="beec1-178">Hiermee geeft u de Id's op van taken die met deze cmdlet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="beec1-178">Specifies the IDs of jobs that this cmdlet stops.</span></span>
<span data-ttu-id="beec1-179">De standaard instelling is alle taken in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="beec1-179">The default is all jobs in the current session.</span></span>

<span data-ttu-id="beec1-180">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="beec1-180">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="beec1-181">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="beec1-181">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="beec1-182">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="beec1-182">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="beec1-183">Als u de ID van een taak wilt zoeken, typt u `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="beec1-183">To find the ID of a job, type `Get-Job`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="beec1-184">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="beec1-184">-InstanceId</span></span>

<span data-ttu-id="beec1-185">Hiermee geeft u de exemplaar-Id's op van taken die met deze cmdlet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="beec1-185">Specifies the instance IDs of jobs that this cmdlet stops.</span></span>
<span data-ttu-id="beec1-186">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="beec1-186">The default is all jobs.</span></span>

<span data-ttu-id="beec1-187">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="beec1-187">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="beec1-188">Gebruik Get-job om de exemplaar-ID van een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="beec1-188">To find the instance ID of a job, use Get-Job.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="beec1-189">-Taak</span><span class="sxs-lookup"><span data-stu-id="beec1-189">-Job</span></span>

<span data-ttu-id="beec1-190">Hiermee geeft u de taken op die met deze cmdlet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="beec1-190">Specifies the jobs that this cmdlet stops.</span></span>
<span data-ttu-id="beec1-191">Voer een variabele in die de taken bevat of een opdracht waarmee de taken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="beec1-191">Enter a variable that contains the jobs or a command that gets the jobs.</span></span>
<span data-ttu-id="beec1-192">U kunt ook een pijplijn operator gebruiken om taken te verzenden naar de cmdlet **Stop-job** .</span><span class="sxs-lookup"><span data-stu-id="beec1-192">You can also use a pipeline operator to submit jobs to the **Stop-Job** cmdlet.</span></span>
<span data-ttu-id="beec1-193">Met **Stop-job** worden standaard alle taken verwijderd die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="beec1-193">By default, **Stop-Job** deletes all jobs that were started in the current session.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="beec1-194">-Name</span><span class="sxs-lookup"><span data-stu-id="beec1-194">-Name</span></span>

<span data-ttu-id="beec1-195">Hiermee geeft u beschrijvende namen op van taken die met deze cmdlet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="beec1-195">Specifies friendly names of jobs that this cmdlet stops.</span></span>
<span data-ttu-id="beec1-196">Voer de namen van de taken in een lijst met door komma's gescheiden waarden in of gebruik joker tekens (\*) om een taak naam patroon in te voeren.</span><span class="sxs-lookup"><span data-stu-id="beec1-196">Enter the job names in a comma-separated list or use wildcard characters (\*) to enter a job name pattern.</span></span>
<span data-ttu-id="beec1-197">Standaard stopt het **stoppen** van alle taken die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="beec1-197">By default, **Stop-Job** stops all jobs created in the current session.</span></span>

<span data-ttu-id="beec1-198">Omdat de beschrijvende naam niet gegarandeerd uniek is, gebruikt u de para meters *WhatIf* en *confirm* bij het stoppen van taken op naam.</span><span class="sxs-lookup"><span data-stu-id="beec1-198">Because the friendly name is not guaranteed to be unique, use the *WhatIf* and *Confirm* parameters when stopping jobs by name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="beec1-199">-PassThru</span><span class="sxs-lookup"><span data-stu-id="beec1-199">-PassThru</span></span>

<span data-ttu-id="beec1-200">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="beec1-200">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="beec1-201">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="beec1-201">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="beec1-202">-Status</span><span class="sxs-lookup"><span data-stu-id="beec1-202">-State</span></span>

<span data-ttu-id="beec1-203">Hiermee geeft u een taak status op.</span><span class="sxs-lookup"><span data-stu-id="beec1-203">Specifies a job state.</span></span>
<span data-ttu-id="beec1-204">Met deze cmdlet worden alleen taken in de opgegeven status gestopt.</span><span class="sxs-lookup"><span data-stu-id="beec1-204">This cmdlet stops only jobs in the specified state.</span></span>
<span data-ttu-id="beec1-205">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="beec1-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="beec1-206">NotStarted</span><span class="sxs-lookup"><span data-stu-id="beec1-206">NotStarted</span></span>
- <span data-ttu-id="beec1-207">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="beec1-207">Running</span></span>
- <span data-ttu-id="beec1-208">Voltooid</span><span class="sxs-lookup"><span data-stu-id="beec1-208">Completed</span></span>
- <span data-ttu-id="beec1-209">Mislukt</span><span class="sxs-lookup"><span data-stu-id="beec1-209">Failed</span></span>
- <span data-ttu-id="beec1-210">Gestopt</span><span class="sxs-lookup"><span data-stu-id="beec1-210">Stopped</span></span>
- <span data-ttu-id="beec1-211">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="beec1-211">Blocked</span></span>
- <span data-ttu-id="beec1-212">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="beec1-212">Suspended</span></span>
- <span data-ttu-id="beec1-213">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="beec1-213">Disconnected</span></span>
- <span data-ttu-id="beec1-214">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="beec1-214">Suspending</span></span>
- <span data-ttu-id="beec1-215">Stoppen</span><span class="sxs-lookup"><span data-stu-id="beec1-215">Stopping</span></span>

<span data-ttu-id="beec1-216">Zie [JobState Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.jobstate) in de MSDN-bibliotheek voor meer informatie over de status van de taak.</span><span class="sxs-lookup"><span data-stu-id="beec1-216">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="beec1-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="beec1-217">-Confirm</span></span>

<span data-ttu-id="beec1-218">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="beec1-218">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="beec1-219">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="beec1-219">-WhatIf</span></span>

<span data-ttu-id="beec1-220">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="beec1-220">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="beec1-221">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="beec1-221">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="beec1-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="beec1-222">CommonParameters</span></span>

<span data-ttu-id="beec1-223">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="beec1-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="beec1-224">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="beec1-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="beec1-225">INVOER</span><span class="sxs-lookup"><span data-stu-id="beec1-225">INPUTS</span></span>

### <span data-ttu-id="beec1-226">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="beec1-226">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="beec1-227">U kunt een taak object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="beec1-227">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="beec1-228">UITVOER</span><span class="sxs-lookup"><span data-stu-id="beec1-228">OUTPUTS</span></span>

### <span data-ttu-id="beec1-229">Geen, System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="beec1-229">None, System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="beec1-230">Met deze cmdlet wordt een taak object geretourneerd als u de para meter *PassThru* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="beec1-230">This cmdlet returns a job object, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="beec1-231">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="beec1-231">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="beec1-232">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="beec1-232">NOTES</span></span>

## <span data-ttu-id="beec1-233">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="beec1-233">RELATED LINKS</span></span>

[<span data-ttu-id="beec1-234">Get-job</span><span class="sxs-lookup"><span data-stu-id="beec1-234">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="beec1-235">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="beec1-235">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="beec1-236">Receive-job</span><span class="sxs-lookup"><span data-stu-id="beec1-236">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="beec1-237">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="beec1-237">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="beec1-238">Begin taak</span><span class="sxs-lookup"><span data-stu-id="beec1-238">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="beec1-239">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="beec1-239">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="beec1-240">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="beec1-240">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="beec1-241">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="beec1-241">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="beec1-242">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="beec1-242">about_Remote_Variables</span></span>](About/about_Remote_Variables.md)

[<span data-ttu-id="beec1-243">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="beec1-243">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="beec1-244">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="beec1-244">about_Scopes</span></span>](About/about_scopes.md)
