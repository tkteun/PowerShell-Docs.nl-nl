---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/unregister-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-ScheduledJob
ms.openlocfilehash: 0c0b55513bcfdcebdcd5d8a6f17968a4a45e2839
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250290"
---
# <span data-ttu-id="09ea2-103">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="09ea2-103">Unregister-ScheduledJob</span></span>

## <span data-ttu-id="09ea2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="09ea2-104">SYNOPSIS</span></span>
<span data-ttu-id="09ea2-105">Hiermee verwijdert u de geplande taken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="09ea2-105">Deletes scheduled jobs on the local computer.</span></span>

## <span data-ttu-id="09ea2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="09ea2-106">SYNTAX</span></span>

### <span data-ttu-id="09ea2-107">Definitie (standaard)</span><span class="sxs-lookup"><span data-stu-id="09ea2-107">Definition (Default)</span></span>

```
Unregister-ScheduledJob [-InputObject] <ScheduledJobDefinition[]> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="09ea2-108">DefinitionId</span><span class="sxs-lookup"><span data-stu-id="09ea2-108">DefinitionId</span></span>

```
Unregister-ScheduledJob [-Id] <Int32[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="09ea2-109">Definitie</span><span class="sxs-lookup"><span data-stu-id="09ea2-109">DefinitionName</span></span>

```
Unregister-ScheduledJob [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="09ea2-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="09ea2-110">DESCRIPTION</span></span>
<span data-ttu-id="09ea2-111">De cmdlet **unregister-ScheduledJob** verwijdert geplande taken van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="09ea2-111">The **Unregister-ScheduledJob** cmdlet deletes scheduled jobs from the local computer.</span></span>

<span data-ttu-id="09ea2-112">Wanneer u een geplande taak verwijdert of de registratie ervan ongedaan maakt, wordt de **registratie-ScheduledJob** verwijderd uit de map voor de geplande taak (in de map $Home \appdata\local\microsoft\windows\powershell\scheduledjobs), die het XML-bestand bevat dat de geplande taak, de taak uitvoerings geschiedenis en alle taak resultaten definieert.</span><span class="sxs-lookup"><span data-stu-id="09ea2-112">When it deletes or unregisters a scheduled job, **Unregister-ScheduledJob** deletes the directory for the scheduled job (in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory), which contains the XML file that defines the scheduled job, the job execution history, and all job results.</span></span>
<span data-ttu-id="09ea2-113">Met deze actie wordt ook de taak uit taak planner verwijderd.</span><span class="sxs-lookup"><span data-stu-id="09ea2-113">This action also deletes the job from Task Scheduler.</span></span>

<span data-ttu-id="09ea2-114">**Registratie ongedaan maken: ScheduledJob** verwijdert alleen de geplande taken die zijn gemaakt met behulp van de cmdlet Register-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="09ea2-114">**Unregister-ScheduledJob** deletes only the scheduled jobs that are created by using the Register-ScheduledJob cmdlet.</span></span>
<span data-ttu-id="09ea2-115">Geplande taken die zijn gemaakt in taak planner, worden niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="09ea2-115">It does not delete scheduled jobs that are created in Task Scheduler.</span></span>

<span data-ttu-id="09ea2-116">U kunt de para meters van **unregister-ScheduledJob** gebruiken om de geplande taken te verwijderen op basis van de id of naam, of door de ScheduledJob geplande taken van Get-ScheduledJob uit te **schrijven naar unregistere-** refrom.</span><span class="sxs-lookup"><span data-stu-id="09ea2-116">You can use the parameters of **Unregister-ScheduledJob** to delete scheduled jobs by ID or name, or pipe scheduled jobs from Get-ScheduledJob to **Unregister-ScheduledJob**.</span></span>

<span data-ttu-id="09ea2-117">**Unregister-ScheduledJob** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="09ea2-117">**Unregister-ScheduledJob** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="09ea2-118">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="09ea2-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="09ea2-119">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="09ea2-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="09ea2-120">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="09ea2-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="09ea2-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="09ea2-121">EXAMPLES</span></span>

### <span data-ttu-id="09ea2-122">Voor beeld 1: een geplande taak verwijderen</span><span class="sxs-lookup"><span data-stu-id="09ea2-122">Example 1: Delete a scheduled job</span></span>

```
PS C:\> Unregister-ScheduledJob TestJob
```

<span data-ttu-id="09ea2-123">Met deze opdracht wordt de geplande taak TestJob op de lokale computer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="09ea2-123">This command deletes the TestJob scheduled job on the local computer.</span></span>

### <span data-ttu-id="09ea2-124">Voor beeld 2: alle geplande taken verwijderen</span><span class="sxs-lookup"><span data-stu-id="09ea2-124">Example 2: Delete all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Unregister-ScheduledJob -Force
PS C:\> Unregister-ScheduledJob -Name "*" -Force
```

<span data-ttu-id="09ea2-125">In dit voor beeld ziet u twee verschillende opdrachten waarmee alle geplande taken op de lokale computer worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="09ea2-125">This example shows two different commands that delete all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="09ea2-126">De eerste opdracht gebruikt de cmdlet Get-ScheduledJob om alle geplande taken op de lokale computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="09ea2-126">The first command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="09ea2-127">Een pijplijn operator (|) verzendt de geplande taken voor het **ongedaan maken van de registratie-ScheduleJob** , waarmee ze worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="09ea2-127">A pipeline operator (|) sends the scheduled jobs to **Unregister-ScheduleJob** , which deletes them.</span></span>

<span data-ttu-id="09ea2-128">De tweede opdracht maakt gebruik van de para meter *name* van **unregister-ScheduledJob** met een waarde van alle (\*) om alle geplande taken te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="09ea2-128">The second command uses the *Name* parameter of **Unregister-ScheduledJob** with a value of all (\*) to delete all scheduled jobs.</span></span>

<span data-ttu-id="09ea2-129">Beide opdrachten gebruiken de para meter *Force* , waarmee een geplande taak wordt verwijderd, zelfs als er een exemplaar van de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="09ea2-129">Both commands use the *Force* parameter, which deletes a scheduled job even if an instance of the job is running.</span></span>

### <span data-ttu-id="09ea2-130">Voor beeld 3: een geplande taak op een externe computer verwijderen</span><span class="sxs-lookup"><span data-stu-id="09ea2-130">Example 3: Delete a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" { Unregister-ScheduledJob -Name "Test*"}
```

<span data-ttu-id="09ea2-131">Met deze opdracht worden geplande taken verwijderd met namen die beginnen met testen op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="09ea2-131">This command deletes scheduled jobs with names that begin with Test on the Server01 remote computer.</span></span>
<span data-ttu-id="09ea2-132">De opdracht gebruikt de cmdlet Invoke-Command om de opdracht **unregister-ScheduledJob** uit te voeren op de Server02-computer.</span><span class="sxs-lookup"><span data-stu-id="09ea2-132">The command uses the Invoke-Command cmdlet to run the **Unregister-ScheduledJob** command on the Server02 computer.</span></span>

## <span data-ttu-id="09ea2-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="09ea2-133">PARAMETERS</span></span>

### <span data-ttu-id="09ea2-134">-Force</span><span class="sxs-lookup"><span data-stu-id="09ea2-134">-Force</span></span>
<span data-ttu-id="09ea2-135">Hiermee wordt de geplande taak verwijderd, zelfs als er een exemplaar van de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="09ea2-135">Deletes the scheduled job even if an instance of the job is running.</span></span>
<span data-ttu-id="09ea2-136">Bij **het ongedaan maken van de registratie-ScheduledJob** wordt de uitvoering van taken standaard niet onderbroken.</span><span class="sxs-lookup"><span data-stu-id="09ea2-136">By default, **Unregister-ScheduledJob** does not interrupt running jobs.</span></span>

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

### <span data-ttu-id="09ea2-137">-Id</span><span class="sxs-lookup"><span data-stu-id="09ea2-137">-Id</span></span>
<span data-ttu-id="09ea2-138">Hiermee worden de geplande taken met de opgegeven identificatie nummers (ID) verwijderd.</span><span class="sxs-lookup"><span data-stu-id="09ea2-138">Deletes the scheduled jobs with the specified identification numbers (ID).</span></span>
<span data-ttu-id="09ea2-139">Voer de Id's van de geplande taken op de computer in.</span><span class="sxs-lookup"><span data-stu-id="09ea2-139">Enter the IDs of scheduled jobs on the computer.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09ea2-140">-Input object</span><span class="sxs-lookup"><span data-stu-id="09ea2-140">-InputObject</span></span>
<span data-ttu-id="09ea2-141">Hiermee geeft u een geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="09ea2-141">Specifies a scheduled job.</span></span>
<span data-ttu-id="09ea2-142">Voer een variabele in die **ScheduledJob** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJob** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.</span><span class="sxs-lookup"><span data-stu-id="09ea2-142">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="09ea2-143">U kunt ook **ScheduledJob** -objecten pipeen voor het **ongedaan maken van de registratie-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="09ea2-143">You can also pipe **ScheduledJob** objects to **Unregister-JobTrigger**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="09ea2-144">-Name</span><span class="sxs-lookup"><span data-stu-id="09ea2-144">-Name</span></span>
<span data-ttu-id="09ea2-145">Hiermee worden de geplande taken met de opgegeven namen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="09ea2-145">Deletes the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="09ea2-146">Voer de namen in van een of meer geplande taken op de computer.</span><span class="sxs-lookup"><span data-stu-id="09ea2-146">Enter the names of one or more scheduled jobs on the computer.</span></span>
<span data-ttu-id="09ea2-147">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="09ea2-147">Wildcards are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09ea2-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="09ea2-148">-Confirm</span></span>
<span data-ttu-id="09ea2-149">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="09ea2-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="09ea2-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="09ea2-150">-WhatIf</span></span>
<span data-ttu-id="09ea2-151">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="09ea2-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="09ea2-152">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="09ea2-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="09ea2-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="09ea2-153">CommonParameters</span></span>
<span data-ttu-id="09ea2-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="09ea2-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="09ea2-155">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="09ea2-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="09ea2-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="09ea2-156">INPUTS</span></span>

### <span data-ttu-id="09ea2-157">Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="09ea2-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="09ea2-158">U kunt geplande taken door sluizen naar Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="09ea2-158">You can pipe scheduled jobs to Unregister-ScheduledJob</span></span>

## <span data-ttu-id="09ea2-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="09ea2-159">OUTPUTS</span></span>

### <span data-ttu-id="09ea2-160">Geen</span><span class="sxs-lookup"><span data-stu-id="09ea2-160">None</span></span>
<span data-ttu-id="09ea2-161">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="09ea2-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="09ea2-162">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="09ea2-162">NOTES</span></span>

## <span data-ttu-id="09ea2-163">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="09ea2-163">RELATED LINKS</span></span>

[<span data-ttu-id="09ea2-164">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="09ea2-164">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="09ea2-165">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="09ea2-165">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="09ea2-166">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="09ea2-166">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="09ea2-167">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="09ea2-167">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="09ea2-168">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="09ea2-168">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="09ea2-169">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="09ea2-169">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="09ea2-170">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="09ea2-170">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="09ea2-171">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="09ea2-171">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="09ea2-172">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="09ea2-172">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="09ea2-173">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="09ea2-173">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="09ea2-174">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="09ea2-174">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="09ea2-175">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="09ea2-175">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="09ea2-176">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="09ea2-176">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="09ea2-177">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="09ea2-177">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="09ea2-178">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="09ea2-178">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="09ea2-179">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="09ea2-179">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
