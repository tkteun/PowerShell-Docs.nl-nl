---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ScheduledJob
ms.openlocfilehash: a7ea520d7d0365fd0de8c9d0bb767981b68467c6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250316"
---
# <span data-ttu-id="3dde8-103">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3dde8-103">Disable-ScheduledJob</span></span>

## <span data-ttu-id="3dde8-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3dde8-104">SYNOPSIS</span></span>
<span data-ttu-id="3dde8-105">Hiermee wordt een geplande taak uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3dde8-105">Disables a scheduled job.</span></span>

## <span data-ttu-id="3dde8-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3dde8-106">SYNTAX</span></span>

### <span data-ttu-id="3dde8-107">Definitie (standaard)</span><span class="sxs-lookup"><span data-stu-id="3dde8-107">Definition (Default)</span></span>

```
Disable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3dde8-108">DefinitionId</span><span class="sxs-lookup"><span data-stu-id="3dde8-108">DefinitionId</span></span>

```
Disable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3dde8-109">Definitie</span><span class="sxs-lookup"><span data-stu-id="3dde8-109">DefinitionName</span></span>

```
Disable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3dde8-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3dde8-110">DESCRIPTION</span></span>
<span data-ttu-id="3dde8-111">Met de cmdlet **Disable-ScheduledJob** worden geplande taken tijdelijk uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3dde8-111">The **Disable-ScheduledJob** cmdlet temporarily disables scheduled jobs.</span></span>
<span data-ttu-id="3dde8-112">Als u uitschakelen kiest, worden alle taak eigenschappen behouden en worden de taak triggers niet uitgeschakeld, maar wordt voor komen dat de geplande taken automatisch worden gestart wanneer deze worden geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="3dde8-112">Disabling preserves all job properties and does not disable the job triggers, but it prevents the scheduled jobs from starting automatically when triggered.</span></span>
<span data-ttu-id="3dde8-113">U kunt een uitgeschakelde geplande taak starten met behulp van de cmdlet Start-Job of een uitgeschakelde geplande taak als sjabloon gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3dde8-113">You can start a disabled scheduled job by using the Start-Job cmdlet or use a disabled scheduled job as a template.</span></span>

<span data-ttu-id="3dde8-114">Als u een geplande taak wilt uitschakelen, stelt de cmdlet **Disable-ScheduledJob** de eigenschap **enabled** van de geplande taak in op False ($false).</span><span class="sxs-lookup"><span data-stu-id="3dde8-114">To disable a scheduled job, the **Disable-ScheduledJob** cmdlet sets the **Enabled** property of the scheduled job to False ($false).</span></span>
<span data-ttu-id="3dde8-115">Gebruik de cmdlet Enable-ScheduledJob om de geplande taak opnieuw in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="3dde8-115">To re-enable the scheduled job, use the Enable-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="3dde8-116">**Disable-ScheduledJob** is een van een verzameling taak planning-cmdlets in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="3dde8-116">**Disable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="3dde8-117">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="3dde8-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="3dde8-118">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="3dde8-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="3dde8-119">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3dde8-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="3dde8-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3dde8-120">EXAMPLES</span></span>

### <span data-ttu-id="3dde8-121">Voor beeld 1: een geplande taak uitschakelen</span><span class="sxs-lookup"><span data-stu-id="3dde8-121">Example 1: Disable a scheduled job</span></span>

```
PS C:\> Disable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
```

<span data-ttu-id="3dde8-122">Met deze opdracht wordt de geplande taak met ID 2 op de lokale computer uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3dde8-122">This command disables the scheduled job with ID 2 on the local computer.</span></span>
<span data-ttu-id="3dde8-123">In de uitvoer ziet u het effect van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3dde8-123">The output shows the effect of the command.</span></span>

### <span data-ttu-id="3dde8-124">Voor beeld 2: alle geplande taken uitschakelen</span><span class="sxs-lookup"><span data-stu-id="3dde8-124">Example 2: Disable all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Disable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        False
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     False
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       False
```

<span data-ttu-id="3dde8-125">Met deze opdracht worden alle geplande taken op de lokale computer uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3dde8-125">This command disables all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="3dde8-126">De cmdlet Get-ScheduledJob wordt gebruikt om alle geplande taken en de cmdlet **Disable-ScheduledJob** uit te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="3dde8-126">It uses the Get-ScheduledJob cmdlet to get all scheduled job and the **Disable-ScheduledJob** cmdlet to disable them.</span></span>

<span data-ttu-id="3dde8-127">U kunt de geplande taak opnieuw inschakelen met behulp van de cmdlet Enable-ScheduledJob en een uitgeschakelde geplande taak uitvoeren met behulp van de Start-Job-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3dde8-127">You can re-enable scheduled job by using the Enable-ScheduledJob cmdlet and run a disabled scheduled job by using the Start-Job cmdlet.</span></span>

<span data-ttu-id="3dde8-128">**Met Disable-ScheduledJob** worden geen waarschuwingen of fouten gegenereerd als u een geplande taak uitschakelt die al is uitgeschakeld, zodat u alle geplande taken zonder voor waarden kunt uitschakelen.</span><span class="sxs-lookup"><span data-stu-id="3dde8-128">**Disable-ScheduledJob** does not generate warnings or errors if you disable a scheduled job that is already disabled, so you can disable all scheduled jobs without conditions.</span></span>

### <span data-ttu-id="3dde8-129">Voor beeld 3: geselecteerde geplande taken uitschakelen</span><span class="sxs-lookup"><span data-stu-id="3dde8-129">Example 3: Disable selected scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Where-Object {!$_.Credential} | Disable-ScheduledJob
```

<span data-ttu-id="3dde8-130">Met deze opdracht wordt de geplande taak uitgeschakeld, wordt er geen referentie opgenomen.</span><span class="sxs-lookup"><span data-stu-id="3dde8-130">This command disables scheduled job do not include a credential.</span></span>
<span data-ttu-id="3dde8-131">Taken zonder referenties worden uitgevoerd met de machtiging van de gebruiker die ze heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="3dde8-131">Jobs without credentials run with the permission of the user who created them.</span></span>

<span data-ttu-id="3dde8-132">De opdracht gebruikt de cmdlet Get-ScheduledJob om alle geplande taken op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="3dde8-132">The command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the computer.</span></span>
<span data-ttu-id="3dde8-133">Een pijplijn operator verzendt de geplande taken naar de cmdlet Where-Object, waarmee geplande taken worden geselecteerd die geen referenties hebben.</span><span class="sxs-lookup"><span data-stu-id="3dde8-133">A pipeline operator sends the scheduled jobs to the Where-Object cmdlet, which selects scheduled jobs that do not have credentials.</span></span>
<span data-ttu-id="3dde8-134">De opdracht maakt gebruik van de operator Not (!) en verwijst naar de eigenschap Credential van de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="3dde8-134">The command uses the not (!) operator and references the Credential property of the scheduled job.</span></span>
<span data-ttu-id="3dde8-135">Een andere pijplijn operator verzendt de geselecteerde geplande taken naar de cmdlet **Disable-ScheduledJob** , waarmee deze worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3dde8-135">Another pipeline operator sends the selected scheduled jobs to the **Disable-ScheduledJob** cmdlet, which disables them.</span></span>

### <span data-ttu-id="3dde8-136">Voor beeld 4: geplande taken uitschakelen op een externe computer</span><span class="sxs-lookup"><span data-stu-id="3dde8-136">Example 4: Disable scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01, Srv10 -ScriptBlock {Disable-ScheduledJob -Name TestJob}
```

<span data-ttu-id="3dde8-137">Met deze opdracht wordt de geplande taak TestJob op twee externe computers, Srv01 en Srv10, uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3dde8-137">This command disables the TestJob scheduled job on two remote computers, Srv01 and Srv10.</span></span>

<span data-ttu-id="3dde8-138">De opdracht gebruikt de cmdlet Invoke-Command om een opdracht **Disable-ScheduledJob** uit te voeren op de computers Srv01 en Srv10.</span><span class="sxs-lookup"><span data-stu-id="3dde8-138">The command uses the Invoke-Command cmdlet to run a **Disable-ScheduledJob** command on the Srv01 and Srv10 computers.</span></span>
<span data-ttu-id="3dde8-139">De opdracht gebruikt de para meter *name* van **Disable-ScheduledJob** om de geplande TestJob-taak op elke computer te selecteren.</span><span class="sxs-lookup"><span data-stu-id="3dde8-139">The command uses the *Name* parameter of **Disable-ScheduledJob** to select the TestJob scheduled job on each computer.</span></span>

### <span data-ttu-id="3dde8-140">Voor beeld 5: een geplande taak uitschakelen op basis van de algemene ID</span><span class="sxs-lookup"><span data-stu-id="3dde8-140">Example 5: Disable a scheduled job by its global ID</span></span>

```
The first command demonstrates one way of finding the GlobalID of a scheduled job. The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Format-Table cmdlet, which displays the Name, GlobalID, and Command properties of each job in a table.
PS C:\> Get-ScheduledJob | Format-Table -Property Name, GlobalID, Command -Autosize
Name             GlobalId                             Command
----             --------                             -------
ArchiveProjects1 a26a0b3d-b4e6-44d3-8b95-8706ef621f7c C:\Scripts\Archive-DxProjects.ps1
Inventory        3ac37e5d-84c0-4a8f-9661-7e88ebb8f914 \\Srv01\Scripts\Get-FullInventory.ps1
Backup-Scripts   4d0cc6be-c082-48d1-baec-1bd8278f3c81  Copy-Item C:\CurrentScripts\*.ps1 -Destination C:\BackupScripts
Test-HelpFiles   d77020ca-f20d-42be-86c8-fc64df97db90 .\Test-HelpFiles.ps1
Test-HelpFiles   2f1606d2-c6cf-4bef-8b1c-ae36a9cc9934 .\Test-DomainHelpFiles.ps1

The second command uses the  Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Where-Object cmdlet, which selects the scheduled job with the specified global ID. Another pipeline operator sends the job to the **Disable-ScheduledJob** cmdlet, which disables it.
PS C:\> Get-ScheduledJob | Where-Object {$_.GlobalID = d77020ca-f20d-42be-86c8-fc64df97db90} | Disable-ScheduledJob
```

<span data-ttu-id="3dde8-141">In deze voor beelden ziet u hoe u een geplande taak kunt uitschakelen met behulp van de algemene id.</span><span class="sxs-lookup"><span data-stu-id="3dde8-141">This examples shows how to disable a scheduled job by using its global identifier.</span></span>
<span data-ttu-id="3dde8-142">De waarde van de eigenschap GlobalID van een geplande taak is een unieke id (GUID).</span><span class="sxs-lookup"><span data-stu-id="3dde8-142">The value of the GlobalID property of a scheduled job is a unique identifier (GUID).</span></span>
<span data-ttu-id="3dde8-143">Gebruik de GlobalID-waarde wanneer Precision vereist is, bijvoorbeeld wanneer u geplande taken op meerdere computers uitschakelt.</span><span class="sxs-lookup"><span data-stu-id="3dde8-143">Use the GlobalID value when precision is required, such as when you are disabling scheduled jobs on multiple computers.</span></span>

## <span data-ttu-id="3dde8-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3dde8-144">PARAMETERS</span></span>

### <span data-ttu-id="3dde8-145">-Id</span><span class="sxs-lookup"><span data-stu-id="3dde8-145">-Id</span></span>
<span data-ttu-id="3dde8-146">Hiermee wordt de geplande taak met het opgegeven id-nummer (ID) uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3dde8-146">Disables the scheduled job with the specified identification number (ID).</span></span>
<span data-ttu-id="3dde8-147">Voer de ID van een geplande taak in.</span><span class="sxs-lookup"><span data-stu-id="3dde8-147">Enter the ID of a scheduled job.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3dde8-148">-Input object</span><span class="sxs-lookup"><span data-stu-id="3dde8-148">-InputObject</span></span>
<span data-ttu-id="3dde8-149">Hiermee geeft u de geplande taak moet worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3dde8-149">Specifies the scheduled job to be disabled.</span></span>
<span data-ttu-id="3dde8-150">Voer een variabele in die  **ScheduledJobDefinition** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobDefinition** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.</span><span class="sxs-lookup"><span data-stu-id="3dde8-150">Enter a variable that contains  **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="3dde8-151">U kunt ook een **ScheduledJobDefinition** -object pipeen om **-ScheduledJob uit te scha kelen**.</span><span class="sxs-lookup"><span data-stu-id="3dde8-151">You can also pipe a **ScheduledJobDefinition** object to **Disable-ScheduledJob**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3dde8-152">-Name</span><span class="sxs-lookup"><span data-stu-id="3dde8-152">-Name</span></span>
<span data-ttu-id="3dde8-153">Hiermee worden de geplande taken met de opgegeven namen uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3dde8-153">Disables the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="3dde8-154">Voer de naam van een geplande taak in.</span><span class="sxs-lookup"><span data-stu-id="3dde8-154">Enter the name of a scheduled job.</span></span>
<span data-ttu-id="3dde8-155">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3dde8-155">Wildcards are supported.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3dde8-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="3dde8-156">-PassThru</span></span>
<span data-ttu-id="3dde8-157">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="3dde8-157">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="3dde8-158">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="3dde8-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="3dde8-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3dde8-159">-Confirm</span></span>
<span data-ttu-id="3dde8-160">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="3dde8-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3dde8-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3dde8-161">-WhatIf</span></span>
<span data-ttu-id="3dde8-162">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="3dde8-162">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="3dde8-163">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3dde8-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3dde8-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3dde8-164">CommonParameters</span></span>
<span data-ttu-id="3dde8-165">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3dde8-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3dde8-166">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3dde8-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3dde8-167">INVOER</span><span class="sxs-lookup"><span data-stu-id="3dde8-167">INPUTS</span></span>

### <span data-ttu-id="3dde8-168">Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="3dde8-168">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="3dde8-169">U kunt een geplande taak door sluizen naar **Disable-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="3dde8-169">You can pipe a scheduled job to **Disable-ScheduledJob**.</span></span>

## <span data-ttu-id="3dde8-170">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3dde8-170">OUTPUTS</span></span>

### <span data-ttu-id="3dde8-171">Geen of Microsoft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="3dde8-171">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="3dde8-172">Als u de para meter **PassThru** gebruikt, wordt de geplande taak die is uitgeschakeld, door **Disable-ScheduledJob** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3dde8-172">If you use the **Passthru** parameter, **Disable-ScheduledJob** returns the scheduled job that was disabled.</span></span>
<span data-ttu-id="3dde8-173">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3dde8-173">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3dde8-174">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3dde8-174">NOTES</span></span>

* <span data-ttu-id="3dde8-175">Als u **Disable-ScheduledJob** gebruikt, worden er geen waarschuwingen of fouten gegenereerd als u hiermee een geplande taak die al is uitgeschakeld, uitschakelt.</span><span class="sxs-lookup"><span data-stu-id="3dde8-175">**Disable-ScheduledJob** does not generate warnings or errors if you use it to disable a scheduled job that is already disabled.</span></span>

## <span data-ttu-id="3dde8-176">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3dde8-176">RELATED LINKS</span></span>

[<span data-ttu-id="3dde8-177">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3dde8-177">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="3dde8-178">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3dde8-178">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="3dde8-179">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3dde8-179">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="3dde8-180">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3dde8-180">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="3dde8-181">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3dde8-181">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="3dde8-182">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3dde8-182">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="3dde8-183">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3dde8-183">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="3dde8-184">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3dde8-184">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="3dde8-185">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3dde8-185">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="3dde8-186">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3dde8-186">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="3dde8-187">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3dde8-187">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="3dde8-188">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3dde8-188">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="3dde8-189">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3dde8-189">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="3dde8-190">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3dde8-190">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="3dde8-191">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3dde8-191">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="3dde8-192">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3dde8-192">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
