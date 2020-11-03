---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-JobTrigger
ms.openlocfilehash: 7a75a5a7e6875ed88fd31ea0f385c19f1991f8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250307"
---
# <span data-ttu-id="b615c-103">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b615c-103">Get-JobTrigger</span></span>

## <span data-ttu-id="b615c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b615c-104">SYNOPSIS</span></span>
<span data-ttu-id="b615c-105">Hiermee worden de taak triggers van geplande taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b615c-105">Gets the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="b615c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b615c-106">SYNTAX</span></span>

### <span data-ttu-id="b615c-107">Taak definitie (standaard)</span><span class="sxs-lookup"><span data-stu-id="b615c-107">JobDefinition (Default)</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### <span data-ttu-id="b615c-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="b615c-108">JobDefinitionId</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Id] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="b615c-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="b615c-109">JobDefinitionName</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Name] <String> [<CommonParameters>]
```

## <span data-ttu-id="b615c-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b615c-110">DESCRIPTION</span></span>
<span data-ttu-id="b615c-111">Met de cmdlet **Get-JobTrigger** worden de taak triggers van geplande taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b615c-111">The **Get-JobTrigger** cmdlet gets the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="b615c-112">U kunt deze opdracht gebruiken om de taak triggers te controleren of om de taak triggers te pipeen naar andere cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b615c-112">You can use this command to examine the job triggers or to pipe the job triggers to other cmdlets.</span></span>

<span data-ttu-id="b615c-113">Een taak trigger definieert een terugkerende planning of voor waarden voor het starten van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="b615c-113">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="b615c-114">Taak triggers worden niet onafhankelijk van de schijf opgeslagen. ze maken deel uit van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="b615c-114">Job triggers are not saved to disk independently; they are part of a scheduled job.</span></span>
<span data-ttu-id="b615c-115">Als u een taak trigger wilt ophalen, geeft u de geplande taak op waarmee de trigger wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="b615c-115">To get a job trigger, specify the scheduled job that the trigger starts.</span></span>

<span data-ttu-id="b615c-116">Gebruik de para meters van de cmdlet **Get-JobTrigger** om de geplande taken te identificeren.</span><span class="sxs-lookup"><span data-stu-id="b615c-116">Use the parameters of the **Get-JobTrigger** cmdlet to identify the scheduled jobs.</span></span>
<span data-ttu-id="b615c-117">U kunt de geplande taken identificeren met hun namen of identificatie nummers, of door **ScheduledJob** -objecten in of uit te voeren, zoals die worden geretourneerd door de Get-ScheduledJob cmdlet, naar **Get-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="b615c-117">You can identify the scheduled jobs by their names or identification numbers, or by entering or piping **ScheduledJob** objects, such as those that are returned by the Get-ScheduledJob cmdlet, to **Get-JobTrigger**.</span></span>

<span data-ttu-id="b615c-118">**Get-JobTrigger** is een van een verzameling cmdlets voor taak planning in de PSScheduledJob-module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="b615c-118">**Get-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="b615c-119">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="b615c-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="b615c-120">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="b615c-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="b615c-121">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b615c-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b615c-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b615c-122">EXAMPLES</span></span>

### <span data-ttu-id="b615c-123">Voor beeld 1: een taak trigger ophalen op basis van de naam van de geplande taak</span><span class="sxs-lookup"><span data-stu-id="b615c-123">Example 1: Get a job trigger by scheduled job name</span></span>

```
PS C:\> Get-JobTrigger -Name "BackupJob"
```

<span data-ttu-id="b615c-124">De opdracht gebruikt de para meter *name* van **Get-JobTrigger** om de taak triggers van de geplande BackupJob-taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="b615c-124">The command uses the *Name* parameter of **Get-JobTrigger** to get the job triggers of the BackupJob scheduled job.</span></span>

### <span data-ttu-id="b615c-125">Voor beeld 2: een taak trigger op basis van ID ophalen</span><span class="sxs-lookup"><span data-stu-id="b615c-125">Example 2: Get a job trigger by ID</span></span>

```
The first command uses the Get-ScheduledJob cmdlet to display the scheduled jobs on the local computer. The display includes the IDs of the scheduled jobs.
PS C:\> Get-ScheduledJob
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProjects {1}             \\Server\Share\Archive-Projects.ps1      True
2          Backup          {1,2}           \\Server\Share\Run-Backup.ps1            True
3          Test-HelpFiles  {1}             \\Server\Share\Test-HelpFiles.ps1        True
4          TestJob         {}              \\Server\Share\Run-AllTests.ps1          True

The second command uses the **Get-JobTrigger** cmdlet to get the job trigger for the Test-HelpFiles job (ID = 3)
PS C:\> Get-JobTrigger -ID 3
```

<span data-ttu-id="b615c-126">In het voor beeld wordt de para meter *id* van **Get-JobTrigger** gebruikt om de taak triggers van een geplande taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="b615c-126">The example uses the *ID* parameter of **Get-JobTrigger** to get the job triggers of a scheduled job.</span></span>

### <span data-ttu-id="b615c-127">Voor beeld 3: taak triggers ophalen door pijpleidingen aan een taak</span><span class="sxs-lookup"><span data-stu-id="b615c-127">Example 3: Get job triggers by piping a job</span></span>

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive* | Get-JobTrigger
```

<span data-ttu-id="b615c-128">Met deze opdracht worden de taak triggers opgehaald van alle taken met een back-up of archief in hun namen.</span><span class="sxs-lookup"><span data-stu-id="b615c-128">This command gets the job triggers of all jobs that have Backup or Archive in their names.</span></span>

### <span data-ttu-id="b615c-129">Voor beeld 4: de taak trigger van een taak op een externe computer ophalen</span><span class="sxs-lookup"><span data-stu-id="b615c-129">Example 4: Get the job trigger of a job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 { Get-ScheduledJob Backup | Get-JobTrigger -TriggerID 2 }
```

<span data-ttu-id="b615c-130">Met deze opdracht wordt een van de twee taak triggers van een geplande taak op een externe computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b615c-130">This command gets one of the two job triggers of a scheduled job on a remote computer.</span></span>

<span data-ttu-id="b615c-131">De opdracht gebruikt de cmdlet Invoke-Command om een opdracht uit te voeren op de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="b615c-131">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>
<span data-ttu-id="b615c-132">De Get-ScheduledJob cmdlet wordt gebruikt voor het ophalen van de geplande back-uptaak, die het pipet naar de **Get-JobTrigger-** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b615c-132">It uses the Get-ScheduledJob cmdlet to get the Backup scheduled job, which it pipes to the **Get-JobTrigger** cmdlet.</span></span>
<span data-ttu-id="b615c-133">De para meter *TriggerID* wordt gebruikt om alleen de tweede trigger op te halen.</span><span class="sxs-lookup"><span data-stu-id="b615c-133">It uses the *TriggerID* parameter to get only the second trigger.</span></span>

### <span data-ttu-id="b615c-134">Voor beeld 5: alle taak triggers ophalen</span><span class="sxs-lookup"><span data-stu-id="b615c-134">Example 5: Get all job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="ScheduledJob";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                    DaysOfWeek Enabled ScheduledJob
-- --------- --                    ---------- ------- ------------
1    Weekly  9/28/2011 3:00:00 AM  {Monday}   True    Backup
1    Daily   9/27/2011 11:00:00 PM            True    Test-HelpFiles
```

<span data-ttu-id="b615c-135">Met deze opdracht worden alle taak triggers van alle geplande taken op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b615c-135">This command gets all job triggers of all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="b615c-136">De opdracht gebruikt de Get-ScheduledJob om de geplande taken op de lokale computer op te halen en deze op te **halen-JobTrigger** , waarmee de taak trigger van elke geplande taak wordt opgehaald (indien van toepassing).</span><span class="sxs-lookup"><span data-stu-id="b615c-136">The command uses the Get-ScheduledJob to get the scheduled jobs on the local computer and pipes them to **Get-JobTrigger** , which gets the job trigger of each scheduled job (if any).</span></span>

<span data-ttu-id="b615c-137">Als u de naam van de geplande taak wilt toevoegen aan de taak trigger weergave, gebruikt de opdracht de berekende eigenschap van de cmdlet Format-Table.</span><span class="sxs-lookup"><span data-stu-id="b615c-137">To add the name of the scheduled job to the job trigger display, the command uses the calculated property feature of the Format-Table cmdlet.</span></span>
<span data-ttu-id="b615c-138">Naast de taak trigger eigenschappen die standaard worden weer gegeven, maakt de opdracht een nieuwe ScheduledJob-eigenschap die de naam van de geplande taak weergeeft.</span><span class="sxs-lookup"><span data-stu-id="b615c-138">In addition to the job trigger properties that are displayed by default, the command creates a new ScheduledJob property that displays the name of the scheduled job.</span></span>

### <span data-ttu-id="b615c-139">Voor beeld 6: de eigenschap taak trigger van een geplande taak ophalen</span><span class="sxs-lookup"><span data-stu-id="b615c-139">Example 6: Get the job trigger property of a scheduled job</span></span>

```
The command uses the Get-ScheduledJob cmdlet to get the Test-HelpFiles scheduled job. Then it uses the dot method (.) to get the JobTriggers property of the Test-HelpFiles scheduled job.
PS C:\> (Get-ScheduledJob Test-HelpFiles).JobTriggers

The second command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer. It uses the ForEach-Object cmdlet to get the value of the JobTrigger property of each scheduled job.
PS C:\> Get-ScheduledJob | foreach {$_.JobTriggers}
```

<span data-ttu-id="b615c-140">De taak triggers van een geplande taak worden opgeslagen in de eigenschap JobTriggers van de taak.</span><span class="sxs-lookup"><span data-stu-id="b615c-140">The job triggers of a scheduled job are stored in the JobTriggers property of the job.</span></span>
<span data-ttu-id="b615c-141">Dit voor beeld toont alternatieven voor het gebruik van de cmdlet **Get-JobTrigger** om taak triggers op te halen.</span><span class="sxs-lookup"><span data-stu-id="b615c-141">This example shows alternatives to using the **Get-JobTrigger** cmdlet to get job triggers.</span></span>
<span data-ttu-id="b615c-142">De resultaten zijn identiek aan het gebruik van de cmdlet **Get-JobTrigger** en de technieken kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b615c-142">The results are identical to using the **Get-JobTrigger** cmdlet and the techniques can be used interchangeably.</span></span>

### <span data-ttu-id="b615c-143">Voor beeld 7: taak triggers vergelijken</span><span class="sxs-lookup"><span data-stu-id="b615c-143">Example 7: Compare job triggers</span></span>

```
The first command gets the job trigger of the ArchiveProjects scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T1 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name ArchiveProjects | Get-JobTrigger | Tee-Object -Variable T1
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The second command gets the job trigger of the Test-HelpFiles scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T2 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name "Test-HelpFiles" | Get-JobTrigger | Tee-Object -Variable T2
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The third command compares the job triggers in the $t1 and $t2 variables. It uses the Get-Member cmdlet to get the properties of the job trigger in the $t1 variable. It pipes the properties to the ForEach-Object cmdlet, which compares each property to the properties of the job trigger in the $t2 variable by name. The command then pipes the differing properties to the Format-List cmdlet, which displays them in a list.The output indicates that, although the job triggers appear to be the same, the HelpFiles job trigger includes a random delay of three (3) minutes.
PS C:\> $T1 | Get-Member -Type Property | ForEach-Object { Compare-Object $T1 $T2 -Property $_.Name}
RandomDelay                                                 SideIndicator
-----------                                                 -------------
00:00:00                                                    =>
00:03:00                                                    <=
```

<span data-ttu-id="b615c-144">In dit voor beeld ziet u hoe de taak triggers van twee geplande taken worden vergeleken.</span><span class="sxs-lookup"><span data-stu-id="b615c-144">This example shows how to compare the job triggers of two scheduled jobs.</span></span>

## <span data-ttu-id="b615c-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b615c-145">PARAMETERS</span></span>

### <span data-ttu-id="b615c-146">-Id</span><span class="sxs-lookup"><span data-stu-id="b615c-146">-Id</span></span>
<span data-ttu-id="b615c-147">Hiermee geeft u het id-nummer van een geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="b615c-147">Specifies the identification number of a scheduled job.</span></span>
<span data-ttu-id="b615c-148">**Get-JobTrigger** haalt de taak trigger van de opgegeven geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="b615c-148">**Get-JobTrigger** gets the job trigger of the specified scheduled job.</span></span>

<span data-ttu-id="b615c-149">Als u het id-nummer van geplande taken op de lokale computer of een externe computer wilt ophalen, gebruikt u de Get-ScheduledJob-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b615c-149">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b615c-150">-Input object</span><span class="sxs-lookup"><span data-stu-id="b615c-150">-InputObject</span></span>
<span data-ttu-id="b615c-151">Hiermee geeft u een geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="b615c-151">Specifies a scheduled job.</span></span>
<span data-ttu-id="b615c-152">Voer een variabele in die  **ScheduledJob** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJob** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.</span><span class="sxs-lookup"><span data-stu-id="b615c-152">Enter a variable that contains  **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="b615c-153">U kunt ook **ScheduledJob** -objecten pipeen naar **Get-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="b615c-153">You can also pipe **ScheduledJob** objects to **Get-JobTrigger**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b615c-154">-Name</span><span class="sxs-lookup"><span data-stu-id="b615c-154">-Name</span></span>
<span data-ttu-id="b615c-155">Hiermee geeft u de naam van een geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="b615c-155">Specifies the name of a scheduled job.</span></span>
<span data-ttu-id="b615c-156">**Get-JobTrigger** haalt de taak trigger van de opgegeven geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="b615c-156">**Get-JobTrigger** gets the job trigger of the specified scheduled job.</span></span>
<span data-ttu-id="b615c-157">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b615c-157">Wildcards are supported.</span></span>

<span data-ttu-id="b615c-158">Gebruik de cmdlet Get-ScheduledJob om de namen van geplande taken op de lokale computer of een externe computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="b615c-158">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b615c-159">-TriggerId</span><span class="sxs-lookup"><span data-stu-id="b615c-159">-TriggerId</span></span>
<span data-ttu-id="b615c-160">Hiermee worden de opgegeven taak triggers opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b615c-160">Gets the specified job triggers.</span></span>
<span data-ttu-id="b615c-161">Voer de trigger-Id's in van een of meer taak triggers van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="b615c-161">Enter the trigger IDs of one or more job triggers of a scheduled job.</span></span>
<span data-ttu-id="b615c-162">Gebruik deze para meter wanneer de geplande taak die wordt opgegeven door de para meters *name* , *id* of *input object* , meerdere taak triggers heeft.</span><span class="sxs-lookup"><span data-stu-id="b615c-162">Use this parameter when the scheduled job that is specified by the *Name* , *ID* , or *InputObject* parameters has multiple job triggers.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b615c-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b615c-163">CommonParameters</span></span>
<span data-ttu-id="b615c-164">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b615c-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b615c-165">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b615c-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b615c-166">INVOER</span><span class="sxs-lookup"><span data-stu-id="b615c-166">INPUTS</span></span>

### <span data-ttu-id="b615c-167">Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="b615c-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="b615c-168">U kunt een geplande taak door sluizen van Get-ScheduledJob naar **Get-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="b615c-168">You can pipe a scheduled job from Get-ScheduledJob to **Get-JobTrigger**.</span></span>

## <span data-ttu-id="b615c-169">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b615c-169">OUTPUTS</span></span>

### <span data-ttu-id="b615c-170">Micro soft. Power shell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="b615c-170">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>

## <span data-ttu-id="b615c-171">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b615c-171">NOTES</span></span>

## <span data-ttu-id="b615c-172">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b615c-172">RELATED LINKS</span></span>

[<span data-ttu-id="b615c-173">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b615c-173">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="b615c-174">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b615c-174">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="b615c-175">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b615c-175">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="b615c-176">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b615c-176">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="b615c-177">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b615c-177">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="b615c-178">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b615c-178">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="b615c-179">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b615c-179">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="b615c-180">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="b615c-180">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="b615c-181">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b615c-181">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="b615c-182">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="b615c-182">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="b615c-183">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b615c-183">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="b615c-184">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b615c-184">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="b615c-185">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b615c-185">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="b615c-186">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b615c-186">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="b615c-187">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="b615c-187">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="b615c-188">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b615c-188">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
