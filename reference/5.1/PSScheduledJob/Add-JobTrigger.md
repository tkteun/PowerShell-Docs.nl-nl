---
external help file: Microsoft.PowerShell.ScheduledJob.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/add-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-JobTrigger
ms.openlocfilehash: 6066b8f91c99830fefb09a8bea13fac6ddf958e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250321"
---
# <span data-ttu-id="bb521-103">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bb521-103">Add-JobTrigger</span></span>

## <span data-ttu-id="bb521-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="bb521-104">SYNOPSIS</span></span>
<span data-ttu-id="bb521-105">Taak triggers worden toegevoegd aan geplande taken.</span><span class="sxs-lookup"><span data-stu-id="bb521-105">Adds job triggers to scheduled jobs.</span></span>

## <span data-ttu-id="bb521-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="bb521-106">SYNTAX</span></span>

### <span data-ttu-id="bb521-107">Taak definitie (standaard)</span><span class="sxs-lookup"><span data-stu-id="bb521-107">JobDefinition (Default)</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-InputObject] <ScheduledJobDefinition[]>
 [<CommonParameters>]
```

### <span data-ttu-id="bb521-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="bb521-108">JobDefinitionId</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="bb521-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="bb521-109">JobDefinitionName</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="bb521-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bb521-110">DESCRIPTION</span></span>
<span data-ttu-id="bb521-111">De cmdlet **add-JobTrigger** voegt taak triggers toe aan geplande taken.</span><span class="sxs-lookup"><span data-stu-id="bb521-111">The **Add-JobTrigger** cmdlet adds job triggers to scheduled jobs.</span></span>
<span data-ttu-id="bb521-112">U kunt deze gebruiken om meerdere triggers aan meerdere geplande taken toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="bb521-112">You can use it to add multiple triggers to multiple scheduled jobs.</span></span>

<span data-ttu-id="bb521-113">Een taak trigger start een geplande taak op een eenmalige of terugkerende planning of wanneer er een gebeurtenis optreedt.</span><span class="sxs-lookup"><span data-stu-id="bb521-113">A job trigger starts a scheduled job on a one-time or recurring schedule or when an event occurs.</span></span>

<span data-ttu-id="bb521-114">Gebruik de *trigger* parameter van **add-JobTrigger** om de taak triggers te identificeren die moeten worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="bb521-114">Use the *Trigger* parameter of **Add-JobTrigger** to identify the job triggers to add.</span></span>
<span data-ttu-id="bb521-115">Gebruik de para meters *name* , *id* of *input object* van **add-JobTrigger** om de geplande taak te identificeren waaraan de triggers worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="bb521-115">Use the *Name* , *ID* , or *InputObject* parameters of **Add-JobTrigger** to identify the scheduled job to which the triggers are added.</span></span>

<span data-ttu-id="bb521-116">Als u taak triggers wilt maken voor de waarde van de *trigger* parameter, gebruikt u de cmdlet New-JobTrigger of gebruikt u een hash-tabel om de taak trigger op te geven.</span><span class="sxs-lookup"><span data-stu-id="bb521-116">To create job triggers for the value of the *Trigger* parameter, use the New-JobTrigger cmdlet or use a hash table to specify the job trigger.</span></span>

<span data-ttu-id="bb521-117">**Add-JobTrigger** is een van een verzameling taak planning-cmdlets in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="bb521-117">**Add-JobTrigger** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="bb521-118">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="bb521-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="bb521-119">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="bb521-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="bb521-120">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bb521-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="bb521-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="bb521-121">EXAMPLES</span></span>

### <span data-ttu-id="bb521-122">Voor beeld 1: een taak trigger toevoegen aan een geplande taak</span><span class="sxs-lookup"><span data-stu-id="bb521-122">Example 1: Add a job trigger to a scheduled job</span></span>

```
PS C:\> $Daily = New-JobTrigger -Daily -At 3AMPS
PS C:\> Add-JobTrigger -Trigger $Daily -Name "TestJob"
```

<span data-ttu-id="bb521-123">Met deze opdrachten wordt de dagelijkse taak trigger toegevoegd aan de geplande taak TestJob.</span><span class="sxs-lookup"><span data-stu-id="bb521-123">These commands add the Daily job trigger to the TestJob scheduled job.</span></span>

<span data-ttu-id="bb521-124">De eerste opdracht gebruikt de cmdlet New-JobTrigger om een taak trigger te maken waarmee elke dag om 3:00 uur een geplande taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="bb521-124">The first command uses the New-JobTrigger cmdlet to create a job trigger that starts a scheduled job every day at 3:00 a.m.</span></span>
<span data-ttu-id="bb521-125">Met de opdracht wordt de taak trigger opgeslagen in de variabele $Daily.</span><span class="sxs-lookup"><span data-stu-id="bb521-125">The command saves the job trigger in the $Daily variable.</span></span>

<span data-ttu-id="bb521-126">De tweede opdracht maakt gebruik van de cmdlet **add-JobTrigger** om de taak trigger toe te voegen in de variabele $Startup aan de geplande TestJob-taak.</span><span class="sxs-lookup"><span data-stu-id="bb521-126">The second command uses the **Add-JobTrigger** cmdlet to add the job trigger in the $Startup variable to the TestJob scheduled job.</span></span>

### <span data-ttu-id="bb521-127">Voor beeld 2: een taak trigger toevoegen aan verschillende geplande taken</span><span class="sxs-lookup"><span data-stu-id="bb521-127">Example 2: Add a job trigger to several scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Add-JobTrigger -Trigger (New-JobTrigger -AtStartup)
```

<span data-ttu-id="bb521-128">Met deze opdracht wordt een AtStartup-taak trigger toegevoegd aan alle geplande taken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bb521-128">This command adds an AtStartup job trigger to all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="bb521-129">De Get-ScheduledJob gebruikt om alle geplande taken op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="bb521-129">It uses the Get-ScheduledJob to get all of the scheduled jobs on the computer.</span></span>
<span data-ttu-id="bb521-130">Er wordt een pijplijn operator (|) gebruikt om de taken te verzenden naar de cmdlet **add-JobTrigger** , waarmee de taak trigger wordt toegevoegd aan elk van de geplande taken.</span><span class="sxs-lookup"><span data-stu-id="bb521-130">It uses a pipeline operator (|) to send the jobs to the **Add-JobTrigger** cmdlet, which adds the job trigger to each of the scheduled jobs.</span></span>
<span data-ttu-id="bb521-131">De waarde van de *trigger* parameter is een New-JobTrigger opdracht waarmee de taak trigger AtStartup wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bb521-131">The value of the *Trigger* parameter is a New-JobTrigger command that creates the AtStartup job trigger.</span></span>

### <span data-ttu-id="bb521-132">Voor beeld 3: een taak trigger kopiëren</span><span class="sxs-lookup"><span data-stu-id="bb521-132">Example 3: Copy a job trigger</span></span>

```
PS C:\> $T = Get-JobTrigger -Name "BackupArchives"
PS C:\> Add-JobTrigger -Name "TestBackup,BackupLogs" -Trigger $T
```

<span data-ttu-id="bb521-133">Met deze opdrachten wordt de taak trigger gekopieerd van de geplande BackupArchives-taak en wordt deze toegevoegd aan de TestBackup-en BackupLogs-geplande taken.</span><span class="sxs-lookup"><span data-stu-id="bb521-133">These commands copy the job trigger from the BackupArchives scheduled job and add it to the TestBackup and BackupLogs scheduled jobs.</span></span>

<span data-ttu-id="bb521-134">De eerste opdracht gebruikt de cmdlet Get-JobTrigger om de taak trigger van de geplande taak BackupArchives te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="bb521-134">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the BackupArchives scheduled job.</span></span>
<span data-ttu-id="bb521-135">De-opdracht slaat de trigger op in de variabele $t.</span><span class="sxs-lookup"><span data-stu-id="bb521-135">The command saves the trigger in the $t variable.</span></span>

<span data-ttu-id="bb521-136">De tweede opdracht maakt gebruik van de cmdlet **add-JobTrigger** om de taak trigger in $t toe te voegen aan de TestBackup-en BackupLogs-geplande taken.</span><span class="sxs-lookup"><span data-stu-id="bb521-136">The second command uses the **Add-JobTrigger** cmdlet to add the job trigger in $t to the TestBackup and BackupLogs scheduled jobs.</span></span>

## <span data-ttu-id="bb521-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb521-137">PARAMETERS</span></span>

### <span data-ttu-id="bb521-138">-Id</span><span class="sxs-lookup"><span data-stu-id="bb521-138">-Id</span></span>
<span data-ttu-id="bb521-139">Hiermee geeft u de id-nummers van de geplande taken op.</span><span class="sxs-lookup"><span data-stu-id="bb521-139">Specifies the identification numbers of the scheduled jobs.</span></span>
<span data-ttu-id="bb521-140">**Add-JobTrigger** voegt de taak trigger toe aan de opgegeven geplande taken.</span><span class="sxs-lookup"><span data-stu-id="bb521-140">**Add-JobTrigger** adds the job trigger to the specified scheduled jobs.</span></span>

<span data-ttu-id="bb521-141">Als u het id-nummer van geplande taken op de lokale computer of een externe computer wilt ophalen, gebruikt u de Get-ScheduledJob-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb521-141">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb521-142">-Input object</span><span class="sxs-lookup"><span data-stu-id="bb521-142">-InputObject</span></span>
<span data-ttu-id="bb521-143">Hiermee geeft u de geplande taken op.</span><span class="sxs-lookup"><span data-stu-id="bb521-143">Specifies the scheduled jobs.</span></span>
<span data-ttu-id="bb521-144">Voer een variabele in die **ScheduledJob** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJob** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.</span><span class="sxs-lookup"><span data-stu-id="bb521-144">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="bb521-145">U kunt ook **ScheduledJob** -objecten pipeen naar **add-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="bb521-145">You can also pipe **ScheduledJob** objects to **Add-JobTrigger**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bb521-146">-Name</span><span class="sxs-lookup"><span data-stu-id="bb521-146">-Name</span></span>
<span data-ttu-id="bb521-147">Hiermee geeft u de namen van de geplande taken.</span><span class="sxs-lookup"><span data-stu-id="bb521-147">Specifies the names of the scheduled jobs.</span></span>
<span data-ttu-id="bb521-148">**Add-JobTrigger** voegt de taak triggers toe aan de opgegeven geplande taken.</span><span class="sxs-lookup"><span data-stu-id="bb521-148">**Add-JobTrigger** adds the job triggers to the specified scheduled jobs.</span></span>
<span data-ttu-id="bb521-149">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bb521-149">Wildcards are supported.</span></span>

<span data-ttu-id="bb521-150">Gebruik de cmdlet Get-ScheduledJob om de namen van geplande taken op de lokale computer of een externe computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="bb521-150">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb521-151">-Trigger</span><span class="sxs-lookup"><span data-stu-id="bb521-151">-Trigger</span></span>
<span data-ttu-id="bb521-152">Hiermee geeft u de taak triggers op die moeten worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="bb521-152">Specifies the job triggers to add.</span></span>
<span data-ttu-id="bb521-153">Voer een hash-tabel in waarmee taak triggers worden opgegeven of een variabele die **ScheduledJobTrigger** -objecten bevat, of typ een opdracht of expressie waarmee **ScheduledJobTrigger** -objecten worden opgehaald, zoals een Get-JobTrigger opdracht.</span><span class="sxs-lookup"><span data-stu-id="bb521-153">Enter a hash table that specifies job triggers or a variable that contains **ScheduledJobTrigger** objects, or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="bb521-154">U kunt ook **ScheduledJobTrigger** -objecten pipeen naar **add-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="bb521-154">You can also pipe **ScheduledJobTrigger** objects to **Add-JobTrigger**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bb521-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb521-155">CommonParameters</span></span>
<span data-ttu-id="bb521-156">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bb521-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb521-157">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bb521-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb521-158">INVOER</span><span class="sxs-lookup"><span data-stu-id="bb521-158">INPUTS</span></span>

### <span data-ttu-id="bb521-159">Micro soft. Power shell. ScheduledJob. ScheduledJobTrigger, micro soft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="bb521-159">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger, Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="bb521-160">U kunt taak triggers of geplande taken door sluizen naar **add-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="bb521-160">You can pipe job triggers or scheduled jobs to **Add-JobTrigger**.</span></span>

## <span data-ttu-id="bb521-161">UITVOER</span><span class="sxs-lookup"><span data-stu-id="bb521-161">OUTPUTS</span></span>

### <span data-ttu-id="bb521-162">Geen</span><span class="sxs-lookup"><span data-stu-id="bb521-162">None</span></span>
<span data-ttu-id="bb521-163">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bb521-163">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="bb521-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="bb521-164">NOTES</span></span>

## <span data-ttu-id="bb521-165">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="bb521-165">RELATED LINKS</span></span>

[<span data-ttu-id="bb521-166">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bb521-166">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="bb521-167">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bb521-167">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="bb521-168">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bb521-168">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="bb521-169">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bb521-169">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="bb521-170">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bb521-170">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="bb521-171">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bb521-171">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="bb521-172">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bb521-172">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="bb521-173">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="bb521-173">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="bb521-174">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bb521-174">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="bb521-175">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="bb521-175">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="bb521-176">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bb521-176">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="bb521-177">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bb521-177">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="bb521-178">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bb521-178">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="bb521-179">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bb521-179">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="bb521-180">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="bb521-180">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="bb521-181">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bb521-181">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
