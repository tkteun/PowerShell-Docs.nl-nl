---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-JobTrigger
ms.openlocfilehash: d08b55f4ba78af69608ac74c097fc6851164093b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250308"
---
# <span data-ttu-id="7eb66-103">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="7eb66-103">Enable-JobTrigger</span></span>

## <span data-ttu-id="7eb66-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7eb66-104">SYNOPSIS</span></span>
<span data-ttu-id="7eb66-105">Hiermee schakelt u de taak triggers van geplande taken in.</span><span class="sxs-lookup"><span data-stu-id="7eb66-105">Enables the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="7eb66-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7eb66-106">SYNTAX</span></span>

```
Enable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7eb66-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7eb66-107">DESCRIPTION</span></span>
<span data-ttu-id="7eb66-108">Met de cmdlet **Enable-JobTrigger** worden taak triggers van geplande taken opnieuw ingeschakeld, zoals die zijn uitgeschakeld met behulp van de cmdlet Disable-JobTrigger.</span><span class="sxs-lookup"><span data-stu-id="7eb66-108">The **Enable-JobTrigger** cmdlet re-enables job triggers of scheduled jobs, such as those that were disabled by using the Disable-JobTrigger cmdlet.</span></span>
<span data-ttu-id="7eb66-109">Met ingeschakelde en opnieuw ingeschakelde taak triggers kunnen geplande taken onmiddellijk starten. u hoeft Windows of Windows Power shell niet opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="7eb66-109">Enabled and re-enabled job triggers can start scheduled jobs immediately; there is no need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="7eb66-110">Als u deze cmdlet wilt gebruiken, gebruikt u de cmdlet Get-JobTrigger om de taak triggers te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="7eb66-110">To use this cmdlet, use the  Get-JobTrigger cmdlet to get the job triggers.</span></span>
<span data-ttu-id="7eb66-111">Pipet vervolgens de taak triggers in om **-JobTrigger in te scha kelen** of de *input object* -para meter te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7eb66-111">Then pipe the job triggers to **Enable-JobTrigger** or use its *InputObject* parameter.</span></span>

<span data-ttu-id="7eb66-112">Als u een taak trigger wilt inschakelen, stelt de cmdlet **Enable-JobTrigger** de eigenschap Enabled van de taak trigger in op $True.</span><span class="sxs-lookup"><span data-stu-id="7eb66-112">To enable a job trigger, the **Enable-JobTrigger** cmdlet sets the Enabled property of the job trigger to $True.</span></span>

<span data-ttu-id="7eb66-113">**Enable-ScheduledJob** is een van een verzameling taak planning-cmdlets in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="7eb66-113">**Enable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="7eb66-114">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="7eb66-114">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="7eb66-115">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="7eb66-115">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="7eb66-116">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7eb66-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="7eb66-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7eb66-117">EXAMPLES</span></span>

### <span data-ttu-id="7eb66-118">Voor beeld 1: een taak trigger inschakelen</span><span class="sxs-lookup"><span data-stu-id="7eb66-118">Example 1: Enable a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name Backup-Archives -TriggerID 1 | Enable-JobTrigger
```

<span data-ttu-id="7eb66-119">Met deze opdracht wordt de eerste trigger (ID = 1) van de Backup-Archives geplande taak op de lokale computer ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="7eb66-119">This command enables the first trigger (ID=1) of the Backup-Archives scheduled job on the local computer.</span></span>

<span data-ttu-id="7eb66-120">De opdracht gebruikt de cmdlet Get-JobTrigger om de taak trigger op te halen.</span><span class="sxs-lookup"><span data-stu-id="7eb66-120">The command uses the Get-JobTrigger cmdlet to get the job trigger.</span></span>
<span data-ttu-id="7eb66-121">Een pijplijn operator verzendt de taak trigger naar de cmdlet **Enable-JobTrigger** , waarmee deze wordt ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="7eb66-121">A pipeline operator sends the job trigger to the **Enable-JobTrigger** cmdlet, which enables it.</span></span>

### <span data-ttu-id="7eb66-122">Voor beeld 2: alle taak triggers inschakelen</span><span class="sxs-lookup"><span data-stu-id="7eb66-122">Example 2: Enable all job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Enable-JobTrigger
```

<span data-ttu-id="7eb66-123">De opdracht gebruikt de cmdlet Get-ScheduledJob om de geplande taken op de lokale computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="7eb66-123">The command uses the Get-ScheduledJob cmdlet to get  the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="7eb66-124">Een pijplijn operator (|) verzendt de geplande taken naar de cmdlet Get-JobTrigger, waarmee alle taak triggers van de geplande taken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7eb66-124">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="7eb66-125">Een andere pijplijn operator verzendt de taak triggers naar de cmdlet **Enable-JobTrigger** , waarmee ze worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="7eb66-125">Another pipeline operator sends the job triggers to the **Enable-JobTrigger** cmdlet, which enables them.</span></span>

### <span data-ttu-id="7eb66-126">Voor beeld 3: de taak trigger van een geplande taak op een externe computer inschakelen</span><span class="sxs-lookup"><span data-stu-id="7eb66-126">Example 3: Enable the job trigger of a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "AtLogon"} | Enable-JobTrigger}
```

<span data-ttu-id="7eb66-127">Met deze opdracht wordt de AtLogon-taak triggers ingeschakeld op de geplande DeployPackage-taak op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="7eb66-127">This command re-enables the AtLogon job triggers on the DeployPackage scheduled job on the Server01 remote computer.</span></span>

<span data-ttu-id="7eb66-128">De opdracht gebruikt de cmdlet Invoke-Command om de opdrachten uit te voeren op de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="7eb66-128">The command uses the Invoke-Command cmdlet to run the commands on the Server01 computer.</span></span>
<span data-ttu-id="7eb66-129">De opdracht extern maakt gebruik van de cmdlet Get-JobTrigger om de taak triggers van de geplande DeployPackage-taak te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="7eb66-129">The remote command uses the Get-JobTrigger cmdlet to get the job triggers of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="7eb66-130">Een pijplijn operator verzendt de taak triggers naar de Where-Object cmdlet waarmee alleen AtLogon-taak triggers worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7eb66-130">A pipeline operator sends the job triggers to the Where-Object cmdlet which returns only AtLogon job triggers.</span></span>
<span data-ttu-id="7eb66-131">Een pijplijn operator verzendt de AtLogon-taak triggers naar de cmdlet **Enable-JobTrigger** , waarmee ze worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="7eb66-131">A pipeline operator sends the AtLogon job triggers to the **Enable-JobTrigger** cmdlet, which enables them.</span></span>

### <span data-ttu-id="7eb66-132">Voor beeld 4: Uitgeschakelde taak triggers weer geven</span><span class="sxs-lookup"><span data-stu-id="7eb66-132">Example 4: Display disabled job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | where {!$_.Enabled} | Format-Table Id, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}}
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
 1    Weekly 9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
 2    Daily  9/29/2011 1:00:00 AM              False   Backup-Archive
 1    Weekly 10/20/2011 11:00:00 PM {Friday}   False   Inventory
 1    Weekly 11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

<span data-ttu-id="7eb66-133">Met deze opdracht worden alle uitgeschakelde taak triggers van alle geplande taken in een tabel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7eb66-133">This command displays all disabled job triggers of all scheduled jobs in a table.</span></span>
<span data-ttu-id="7eb66-134">U kunt een opdracht als deze gebruiken om taak triggers te detecteren die mogelijk moeten worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="7eb66-134">You can use a command like this one to discover job triggers that might need to be enabled.</span></span>

<span data-ttu-id="7eb66-135">De opdracht gebruikt de cmdlet Get-ScheduledJob om de geplande taken op de lokale computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="7eb66-135">The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="7eb66-136">Een pijplijn operator (|) verzendt de geplande taken naar de cmdlet Get-JobTrigger, waarmee alle taak triggers van de geplande taken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7eb66-136">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="7eb66-137">Een andere pijplijn operator verzendt de taak triggers naar de cmdlet Where-Object, waarmee alleen taak triggers worden geretourneerd die zijn uitgeschakeld, dat wil zeggen, waarbij de waarde van de eigenschap Enabled van de taak trigger niet (!) True is.</span><span class="sxs-lookup"><span data-stu-id="7eb66-137">Another pipeline operator sends the job triggers to the Where-Object cmdlet, which returns only job triggers that are disabled, that is, where the value of the Enabled property of the job trigger is not (!) true.</span></span>

<span data-ttu-id="7eb66-138">Een andere pijplijn operator verzendt de uitgeschakelde taak triggers naar de cmdlet Format-Table, waarin de geselecteerde eigenschappen van de taak triggers in een tabel worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7eb66-138">Another pipeline operator sends the disabled job triggers to the Format-Table cmdlet, which displays the selected properties of the job triggers in a table.</span></span>
<span data-ttu-id="7eb66-139">De eigenschappen bevatten een nieuwe JobName-eigenschap waarmee de naam van de geplande taak wordt weer gegeven in de eigenschap taak definitie van de taak trigger.</span><span class="sxs-lookup"><span data-stu-id="7eb66-139">The properties include a new JobName property that displays the name of the scheduled job in the JobDefinition property of the job trigger.</span></span>

## <span data-ttu-id="7eb66-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7eb66-140">PARAMETERS</span></span>

### <span data-ttu-id="7eb66-141">-Input object</span><span class="sxs-lookup"><span data-stu-id="7eb66-141">-InputObject</span></span>
<span data-ttu-id="7eb66-142">Hiermee geeft u de taak trigger op die moet worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="7eb66-142">Specifies the job trigger to enable.</span></span>
<span data-ttu-id="7eb66-143">Voer een variabele in die **ScheduledJobTrigger** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobTrigger** -objecten worden opgehaald, zoals een Get-JobTrigger opdracht.</span><span class="sxs-lookup"><span data-stu-id="7eb66-143">Enter a variable that contains **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="7eb66-144">U kunt ook een **ScheduledJobTrigger** -object pipeen om **-JobTrigger in te scha kelen**.</span><span class="sxs-lookup"><span data-stu-id="7eb66-144">You can also pipe a **ScheduledJobTrigger** object to **Enable-JobTrigger**.</span></span>

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

### <span data-ttu-id="7eb66-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7eb66-145">-PassThru</span></span>
<span data-ttu-id="7eb66-146">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="7eb66-146">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="7eb66-147">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="7eb66-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="7eb66-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7eb66-148">-Confirm</span></span>
<span data-ttu-id="7eb66-149">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7eb66-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7eb66-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7eb66-150">-WhatIf</span></span>
<span data-ttu-id="7eb66-151">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7eb66-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7eb66-152">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7eb66-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7eb66-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7eb66-153">CommonParameters</span></span>
<span data-ttu-id="7eb66-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7eb66-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7eb66-155">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7eb66-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7eb66-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="7eb66-156">INPUTS</span></span>

### <span data-ttu-id="7eb66-157">Micro soft. Power shell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="7eb66-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="7eb66-158">U kunt taak triggers pipet om **-JobTrigger in te scha kelen**.</span><span class="sxs-lookup"><span data-stu-id="7eb66-158">You can pipe job triggers to **Enable-JobTrigger**.</span></span>

## <span data-ttu-id="7eb66-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7eb66-159">OUTPUTS</span></span>

### <span data-ttu-id="7eb66-160">Geen</span><span class="sxs-lookup"><span data-stu-id="7eb66-160">None</span></span>
<span data-ttu-id="7eb66-161">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="7eb66-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7eb66-162">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7eb66-162">NOTES</span></span>

* <span data-ttu-id="7eb66-163">**Enable-JobTrigger** genereert geen fouten of waarschuwingen als u een taak trigger inschakelt die al is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="7eb66-163">**Enable-JobTrigger** does not generate errors or warnings if you enable a job trigger that is already enabled.</span></span>

## <span data-ttu-id="7eb66-164">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7eb66-164">RELATED LINKS</span></span>

[<span data-ttu-id="7eb66-165">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="7eb66-165">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="7eb66-166">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="7eb66-166">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="7eb66-167">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="7eb66-167">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="7eb66-168">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="7eb66-168">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="7eb66-169">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="7eb66-169">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="7eb66-170">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="7eb66-170">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="7eb66-171">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="7eb66-171">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="7eb66-172">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="7eb66-172">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="7eb66-173">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="7eb66-173">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="7eb66-174">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="7eb66-174">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="7eb66-175">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="7eb66-175">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="7eb66-176">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="7eb66-176">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="7eb66-177">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="7eb66-177">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="7eb66-178">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="7eb66-178">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="7eb66-179">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="7eb66-179">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="7eb66-180">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="7eb66-180">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
