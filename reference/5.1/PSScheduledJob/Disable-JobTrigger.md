---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-JobTrigger
ms.openlocfilehash: 236e6b7e6e450bd1f3f868f889a19cf796890127
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250320"
---
# <span data-ttu-id="3a1d6-103">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a1d6-103">Disable-JobTrigger</span></span>

## <span data-ttu-id="3a1d6-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3a1d6-104">SYNOPSIS</span></span>
<span data-ttu-id="3a1d6-105">Hiermee schakelt u de taak triggers van geplande taken uit.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-105">Disables the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="3a1d6-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3a1d6-106">SYNTAX</span></span>

```
Disable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3a1d6-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3a1d6-107">DESCRIPTION</span></span>
<span data-ttu-id="3a1d6-108">De cmdlet **Disable-JobTrigger** schakelt tijdelijk de taak triggers van geplande taken uit.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-108">The **Disable-JobTrigger** cmdlet temporarily disables the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="3a1d6-109">Als u deze optie uitschakelt, worden alle taak trigger eigenschappen behouden, maar wordt voor komen dat de taak trigger de geplande taak start.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-109">Disabling preserves all job trigger properties, but it prevents the job trigger from starting the scheduled job.</span></span>

<span data-ttu-id="3a1d6-110">Als u deze cmdlet wilt gebruiken, gebruikt u de cmdlet Get-JobTrigger om de taak triggers te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-110">To use this cmdlet, use the Get-JobTrigger cmdlet to get the job triggers.</span></span>
<span data-ttu-id="3a1d6-111">Pipet vervolgens de taak triggers om **JobTrigger uit te scha kelen** of de para meter *input object* te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-111">Then pipe the job triggers to **Disable-JobTrigger** or use its *InputObject* parameter.</span></span>

<span data-ttu-id="3a1d6-112">Als u een taak trigger wilt uitschakelen, stelt de cmdlet **Disable-JobTrigger** de eigenschap Enabled van de taak trigger in op $false.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-112">To disable a job trigger, the **Disable-JobTrigger** cmdlet sets the Enabled property of the job trigger to $False.</span></span>
<span data-ttu-id="3a1d6-113">Als u de taak trigger opnieuw wilt inschakelen, gebruikt u de cmdlet Enable-JobTrigger, waarmee de eigenschap **enabled** van de taak trigger wordt ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-113">To re-enable the job trigger, use the Enable-JobTrigger cmdlet, which sets the **Enabled** property of the job trigger to $True.</span></span>
<span data-ttu-id="3a1d6-114">Als u een taak trigger uitschakelt, wordt de geplande taak niet uitgeschakeld, bijvoorbeeld door de cmdlet Disable-ScheduledJob, maar als u alle taak triggers uitschakelt, is het effect hetzelfde als het uitschakelen van de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-114">Disabling a job trigger does not disable the scheduled job, such as is done by the Disable-ScheduledJob cmdlet, but if you disable all job triggers, the effect is the same as disabling the scheduled job.</span></span>

<span data-ttu-id="3a1d6-115">Als u een geplande taak uitschakelt of alle taak triggers van een geplande taak uitschakelt, kunt u de taak nog steeds starten met behulp van de cmdlet Start-Job of de uitgeschakelde geplande taak als sjabloon gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-115">If you disable a scheduled job or disable all job triggers of a scheduled job, you can still start the job by using the Start-Job cmdlet or use the disabled scheduled job as a template.</span></span>

<span data-ttu-id="3a1d6-116">**Disable-ScheduledJob** is een van een verzameling taak planning-cmdlets in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-116">**Disable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="3a1d6-117">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="3a1d6-118">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="3a1d6-119">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="3a1d6-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3a1d6-120">EXAMPLES</span></span>

### <span data-ttu-id="3a1d6-121">Voor beeld 1: een taak trigger uitschakelen</span><span class="sxs-lookup"><span data-stu-id="3a1d6-121">Example 1: Disable a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name "Backup-Archives" -TriggerID 1 | Disable-JobTrigger
```

<span data-ttu-id="3a1d6-122">Met deze opdracht wordt de eerste trigger (ID = 1) van de Backup-Archives geplande taak op de lokale computer uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-122">This command disables the first trigger (ID=1) of the Backup-Archives scheduled job on the local computer.</span></span>

<span data-ttu-id="3a1d6-123">De opdracht gebruikt de cmdlet Get-JobTrigger om de taak trigger op te halen.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-123">The command uses the Get-JobTrigger cmdlet to get the job trigger.</span></span>
<span data-ttu-id="3a1d6-124">Een pijplijn operator verzendt de taak trigger naar de cmdlet **Disable-JobTrigger** , waardoor deze wordt uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-124">A pipeline operator sends the job trigger to the **Disable-JobTrigger** cmdlet, which disables it.</span></span>

### <span data-ttu-id="3a1d6-125">Voor beeld 2: alle taak triggers uitschakelen</span><span class="sxs-lookup"><span data-stu-id="3a1d6-125">Example 2: Disable all job triggers</span></span>

```
The first command uses the Get-ScheduledJob cmdlet to get the Backup-Archives and Inventory scheduled jobs. A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs. Another pipeline operator sends the job triggers to the **Disable-JobTrigger** cmdlet, which disables them.The first command uses the **Get-ScheduledJob** cmdlet to get the jobs, because its *Name* parameter takes multiple names.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Disable-JobTrigger

The second command displays the results. The command repeats the **Get-ScheduledJob** and **Get-JobTrigger** command. A pipeline operator sends the job triggers to the Format-Table cmdlet, which displays the job triggers in a table. The **Format-Table** command adds a JobName property that displays the value of the Name property of the scheduled job in the JobDefinition property of the job trigger object.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
1  Weekly    9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
2  Daily     9/29/2011 1:00:00 AM              False   Backup-Archive
1  Weekly    10/20/2011 11:00:00 PM {Friday}   False   Inventory
1  Weekly    11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

<span data-ttu-id="3a1d6-126">Met deze opdrachten worden alle taak triggers op twee geplande taken uitgeschakeld en worden de resultaten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-126">These commands disable all job triggers on two scheduled jobs and display the results.</span></span>

### <span data-ttu-id="3a1d6-127">Voor beeld 3: taak trigger van een geplande taak op een externe computer uitschakelen</span><span class="sxs-lookup"><span data-stu-id="3a1d6-127">Example 3: Disable job trigger of a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "Daily"} | Disable-JobTrigger}
```

<span data-ttu-id="3a1d6-128">Met deze opdracht worden de dagelijkse taak triggers uitgeschakeld op de geplande DeployPackage-taak op de externe computer met Server01.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-128">This command disables the daily job triggers on the DeployPackage scheduled job on the Server01 remote computer.</span></span>

<span data-ttu-id="3a1d6-129">De opdracht gebruikt de cmdlet Invoke-Command om de opdrachten uit te voeren op de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-129">The command uses the Invoke-Command cmdlet to run the commands on the Server01 computer.</span></span>
<span data-ttu-id="3a1d6-130">De opdracht extern maakt gebruik van de cmdlet Get-JobTrigger om de taak triggers van de geplande DeployPackage-taak te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-130">The remote command uses the Get-JobTrigger cmdlet to get the job triggers of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="3a1d6-131">Een pijplijn operator verzendt de taak triggers naar de cmdlet Where-Object, waarmee alleen dagelijkse taak triggers worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-131">A pipeline operator sends the job triggers to the Where-Object cmdlet, which returns only daily job triggers.</span></span>
<span data-ttu-id="3a1d6-132">Een pijplijn operator verzendt de dagelijkse taak triggers naar de cmdlet **Disable-JobTrigger** , waarmee deze worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-132">A pipeline operator sends the daily job triggers to the **Disable-JobTrigger** cmdlet, which disables them.</span></span>

## <span data-ttu-id="3a1d6-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3a1d6-133">PARAMETERS</span></span>

### <span data-ttu-id="3a1d6-134">-Input object</span><span class="sxs-lookup"><span data-stu-id="3a1d6-134">-InputObject</span></span>
<span data-ttu-id="3a1d6-135">Hiermee geeft u de taak trigger op die moet worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-135">Specifies the job trigger to be disabled.</span></span>
<span data-ttu-id="3a1d6-136">Voer een variabele in die  **ScheduledJobTrigger** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobTrigger** -objecten worden opgehaald, zoals een Get-JobTrigger opdracht.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-136">Enter a variable that contains  **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="3a1d6-137">U kunt ook een **ScheduledJobTrigger** -object pipeen om **-JobTrigger uit te scha kelen**.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-137">You can also pipe a **ScheduledJobTrigger** object to **Disable-JobTrigger**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3a1d6-138">-PassThru</span><span class="sxs-lookup"><span data-stu-id="3a1d6-138">-PassThru</span></span>
<span data-ttu-id="3a1d6-139">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-139">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="3a1d6-140">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-140">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="3a1d6-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3a1d6-141">-Confirm</span></span>
<span data-ttu-id="3a1d6-142">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3a1d6-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3a1d6-143">-WhatIf</span></span>
<span data-ttu-id="3a1d6-144">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="3a1d6-145">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3a1d6-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3a1d6-146">CommonParameters</span></span>
<span data-ttu-id="3a1d6-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3a1d6-148">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3a1d6-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="3a1d6-149">INPUTS</span></span>

### <span data-ttu-id="3a1d6-150">Micro soft. Power shell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a1d6-150">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="3a1d6-151">U kunt taak triggers pipet om **-JobTrigger uit te scha kelen**.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-151">You can pipe job triggers to **Disable-JobTrigger**.</span></span>

## <span data-ttu-id="3a1d6-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3a1d6-152">OUTPUTS</span></span>

### <span data-ttu-id="3a1d6-153">Geen</span><span class="sxs-lookup"><span data-stu-id="3a1d6-153">None</span></span>
<span data-ttu-id="3a1d6-154">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-154">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3a1d6-155">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3a1d6-155">NOTES</span></span>

* <span data-ttu-id="3a1d6-156">**Disable-JobTrigger** genereert geen fouten of waarschuwingen als u een taak trigger uitschakelt die al is uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a1d6-156">**Disable-JobTrigger** does not generate errors or warnings if you disable a job trigger that is already disabled.</span></span>

## <span data-ttu-id="3a1d6-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3a1d6-157">RELATED LINKS</span></span>

[<span data-ttu-id="3a1d6-158">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a1d6-158">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="3a1d6-159">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a1d6-159">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="3a1d6-160">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a1d6-160">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="3a1d6-161">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a1d6-161">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="3a1d6-162">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a1d6-162">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="3a1d6-163">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a1d6-163">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="3a1d6-164">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a1d6-164">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="3a1d6-165">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3a1d6-165">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="3a1d6-166">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a1d6-166">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="3a1d6-167">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3a1d6-167">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="3a1d6-168">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a1d6-168">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="3a1d6-169">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a1d6-169">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="3a1d6-170">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a1d6-170">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="3a1d6-171">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a1d6-171">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="3a1d6-172">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3a1d6-172">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="3a1d6-173">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a1d6-173">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
