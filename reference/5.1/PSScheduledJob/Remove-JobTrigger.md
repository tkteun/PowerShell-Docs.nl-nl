---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/remove-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-JobTrigger
ms.openlocfilehash: adcd74361b1a045a57c7db2f15996f4ea53d6d5b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250300"
---
# <span data-ttu-id="64e3b-103">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="64e3b-103">Remove-JobTrigger</span></span>

## <span data-ttu-id="64e3b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="64e3b-104">SYNOPSIS</span></span>
<span data-ttu-id="64e3b-105">Taak triggers uit geplande taken verwijderen.</span><span class="sxs-lookup"><span data-stu-id="64e3b-105">Delete job triggers from scheduled jobs.</span></span>

## <span data-ttu-id="64e3b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="64e3b-106">SYNTAX</span></span>

### <span data-ttu-id="64e3b-107">Taak definitie (standaard)</span><span class="sxs-lookup"><span data-stu-id="64e3b-107">JobDefinition (Default)</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-InputObject] <ScheduledJobDefinition[]> [<CommonParameters>]
```

### <span data-ttu-id="64e3b-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="64e3b-108">JobDefinitionId</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="64e3b-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="64e3b-109">JobDefinitionName</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="64e3b-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="64e3b-110">DESCRIPTION</span></span>
<span data-ttu-id="64e3b-111">De cmdlet **Remove-JobTrigger** verwijdert taak triggers van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="64e3b-111">The **Remove-JobTrigger** cmdlet deletes job triggers from scheduled jobs.</span></span>

<span data-ttu-id="64e3b-112">Een taak trigger definieert een terugkerende planning of voor waarden voor het starten van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="64e3b-112">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="64e3b-113">Als u taak triggers wilt beheren, gebruikt u de cmdlets New-JobTrigger en add-JobTrigger, set-JobTrigger en Set-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="64e3b-113">To manage job triggers, use the New-JobTrigger, Add-JobTrigger, Set-JobTrigger, and Set-ScheduledJob cmdlets.</span></span>

<span data-ttu-id="64e3b-114">Gebruik de para meters *name* , *id* of *input object* van **Remove-JobTrigger** om de geplande taken te identificeren van waaruit de triggers worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="64e3b-114">Use the *Name* , *ID* , or *InputObject* parameters of **Remove-JobTrigger** to identify the scheduled jobs from which the triggers are removed.</span></span>
<span data-ttu-id="64e3b-115">Gebruik de para meter *TriggerID* om de taak triggers te identificeren die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="64e3b-115">Use the *TriggerID* parameter to identify the job triggers to delete.</span></span>
<span data-ttu-id="64e3b-116">Standaard verwijdert **Remove-JobTrigger** alle taak triggers van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="64e3b-116">By default, **Remove-JobTrigger** deletes all job triggers of a scheduled job.</span></span>

<span data-ttu-id="64e3b-117">**Remove-JobTrigger** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="64e3b-117">**Remove-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="64e3b-118">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="64e3b-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="64e3b-119">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="64e3b-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="64e3b-120">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="64e3b-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="64e3b-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="64e3b-121">EXAMPLES</span></span>

### <span data-ttu-id="64e3b-122">Voor beeld 1: alle taak triggers verwijderen</span><span class="sxs-lookup"><span data-stu-id="64e3b-122">Example 1: Delete all job triggers</span></span>

```
PS C:\> Remove-JobTrigger -Name "Test*"
```

<span data-ttu-id="64e3b-123">Met deze opdracht worden alle taak triggers verwijderd uit een geplande taak met namen die beginnen met de test.</span><span class="sxs-lookup"><span data-stu-id="64e3b-123">This command deletes all job triggers from scheduled job that have names that begin with Test.</span></span>

### <span data-ttu-id="64e3b-124">Voor beeld 2: geselecteerde taak triggers verwijderen</span><span class="sxs-lookup"><span data-stu-id="64e3b-124">Example 2: Delete selected job triggers</span></span>

```
PS C:\> Remove-JobTrigger -Name "BackupArchive" -TriggerID 3
```

<span data-ttu-id="64e3b-125">Met deze opdracht wordt alleen de derde trigger (ID = 3) verwijderd uit de geplande taak BackupArchive.</span><span class="sxs-lookup"><span data-stu-id="64e3b-125">This command deletes only the third trigger (ID = 3) from the BackupArchive scheduled job.</span></span>

### <span data-ttu-id="64e3b-126">Voor beeld 3: AtStartup-taak triggers uit alle geplande taken verwijderen</span><span class="sxs-lookup"><span data-stu-id="64e3b-126">Example 3: Delete AtStartup job triggers from all scheduled jobs</span></span>

```
PS C:\> function Delete-AtStartup
{
    Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.Frequency -eq "AtStartup"} | ForEach-Object { Remove-JobTrigger -InputObject $_.JobDefinition -TriggerID $_.ID}
}
```

<span data-ttu-id="64e3b-127">Deze functie verwijdert alle AtStartup-taak triggers van alle taken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="64e3b-127">This function deletes all AtStartup job triggers from all jobs on the local computer.</span></span>
<span data-ttu-id="64e3b-128">Als u de functie wilt gebruiken, voert u de functie in uw sessie uit en typt u `Delete-AtStartup` .</span><span class="sxs-lookup"><span data-stu-id="64e3b-128">To use the function, run the function in your session and then type `Delete-AtStartup`.</span></span>

<span data-ttu-id="64e3b-129">De functie Delete-AtStartup bevat één opdracht.</span><span class="sxs-lookup"><span data-stu-id="64e3b-129">The Delete-AtStartup function contains a single command.</span></span>
<span data-ttu-id="64e3b-130">De opdracht gebruikt de cmdlet Get-ScheduledJob om de geplande taken op de lokale computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="64e3b-130">The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="64e3b-131">Een pijplijn operator (|) verzendt de geplande taken naar de cmdlet Get-JobTrigger, waarmee alle taak triggers van elk van de geplande taken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="64e3b-131">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all of the job triggers from each of the scheduled jobs.</span></span>
<span data-ttu-id="64e3b-132">Een pijplijn operator verzendt de taak triggers naar de cmdlet Where-Object, waarmee taak triggers worden geselecteerd waarbij de waarde van de eigenschap Frequency van de taak trigger gelijk is aan AtStartup.</span><span class="sxs-lookup"><span data-stu-id="64e3b-132">A pipeline operator sends the job triggers to the Where-Object cmdlet, which selects job triggers where the value of the Frequency property of the job trigger equals AtStartup.</span></span>

<span data-ttu-id="64e3b-133">**JobTrigger** -objecten hebben een eigenschap **taak definitie** die de geplande taak bevat die ze activeren.</span><span class="sxs-lookup"><span data-stu-id="64e3b-133">**JobTrigger** objects have a **JobDefinition** property that contains the scheduled job that they trigger.</span></span>
<span data-ttu-id="64e3b-134">De rest van de opdracht gebruikt die waardevolle functie.</span><span class="sxs-lookup"><span data-stu-id="64e3b-134">The remainder of the command uses that valuable feature.</span></span>

<span data-ttu-id="64e3b-135">Een pijplijn operator verzendt de AtStartup-taak triggers naar de cmdlet ForEach-Object, waarmee de opdracht **Remove-JobTrigger** wordt uitgevoerd op elke AtStartup-trigger.</span><span class="sxs-lookup"><span data-stu-id="64e3b-135">A pipeline operator sends the AtStartup job triggers to the ForEach-Object cmdlet, which runs a **Remove-JobTrigger** command on each AtStartup trigger.</span></span>
<span data-ttu-id="64e3b-136">De waarde van de para meter *input object* van **Remove-JobTrigger** is de geplande taak in de eigenschap taak definitie van de taak trigger.</span><span class="sxs-lookup"><span data-stu-id="64e3b-136">The value of the *InputObject* parameter of **Remove-JobTrigger** is the scheduled job in the JobDefinition property of the job trigger.</span></span>
<span data-ttu-id="64e3b-137">De waarde van de para meter *TriggerID* is de id in de eigenschap ID van de taak trigger.</span><span class="sxs-lookup"><span data-stu-id="64e3b-137">The value of the *TriggerID* parameter is the identifier in the ID property of the job trigger.</span></span>

### <span data-ttu-id="64e3b-138">Voor beeld 4: een taak trigger verwijderen uit een externe geplande taak</span><span class="sxs-lookup"><span data-stu-id="64e3b-138">Example 4: Delete a job trigger from a remote scheduled job</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" { Remove-JobTrigger -ID 38 -TriggerID 1 }
```

<span data-ttu-id="64e3b-139">Met deze opdracht wordt de eerste taak trigger uit de inventaris taak op de Server01-computer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="64e3b-139">This command deletes the first job trigger from the Inventory job on the Server01 computer.</span></span>

<span data-ttu-id="64e3b-140">De opdracht gebruikt de cmdlet **invoke-opdracht** om de cmdlet **Remove-JobTrigger** uit te voeren op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="64e3b-140">The command uses the **Invoke-Command** cmdlet to run the **Remove-JobTrigger** cmdlet on the Server01 computer.</span></span>
<span data-ttu-id="64e3b-141">De **Remove-JobTrigger** -cmdlet gebruikt de *id-* para meter voor het identificeren van de geplande inventarisatie taak en de para meter *TriggerID* om de eerste trigger op te geven.</span><span class="sxs-lookup"><span data-stu-id="64e3b-141">The **Remove-JobTrigger** cmdlet uses the *ID* parameter to identify the Inventory scheduled job and the *TriggerID* parameter to specify the first trigger.</span></span>
<span data-ttu-id="64e3b-142">De *id-* para meter is met name handig wanneer meerdere geplande taken dezelfde of vergelijk bare naam hebben.</span><span class="sxs-lookup"><span data-stu-id="64e3b-142">The *ID* parameter is especially useful when multiple scheduled jobs have the same or similar names.</span></span>

## <span data-ttu-id="64e3b-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="64e3b-143">PARAMETERS</span></span>

### <span data-ttu-id="64e3b-144">-Id</span><span class="sxs-lookup"><span data-stu-id="64e3b-144">-Id</span></span>
<span data-ttu-id="64e3b-145">Hiermee geeft u de id-nummers van de geplande taken op.</span><span class="sxs-lookup"><span data-stu-id="64e3b-145">Specifies the identification numbers of the scheduled jobs.</span></span>
<span data-ttu-id="64e3b-146">**Remove-JobTrigger** verwijdert taak triggers uit de opgegeven geplande taken.</span><span class="sxs-lookup"><span data-stu-id="64e3b-146">**Remove-JobTrigger** deletes job triggers from the specified scheduled jobs.</span></span>

<span data-ttu-id="64e3b-147">Als u het id-nummer van geplande taken op de lokale computer of een externe computer wilt ophalen, gebruikt u de Get-ScheduledJob-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="64e3b-147">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="64e3b-148">-Input object</span><span class="sxs-lookup"><span data-stu-id="64e3b-148">-InputObject</span></span>
<span data-ttu-id="64e3b-149">Hiermee geeft u de geplande taken op.</span><span class="sxs-lookup"><span data-stu-id="64e3b-149">Specifies the scheduled jobs.</span></span>
<span data-ttu-id="64e3b-150">Voer een variabele in die **ScheduledJob** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJob** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.</span><span class="sxs-lookup"><span data-stu-id="64e3b-150">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="64e3b-151">U kunt ook **ScheduledJob** -objecten pipeen om **-JobTrigger te verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="64e3b-151">You can also pipe **ScheduledJob** objects to **Remove-JobTrigger**.</span></span>

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

### <span data-ttu-id="64e3b-152">-Name</span><span class="sxs-lookup"><span data-stu-id="64e3b-152">-Name</span></span>
<span data-ttu-id="64e3b-153">Hiermee geeft u de namen van de geplande taken.</span><span class="sxs-lookup"><span data-stu-id="64e3b-153">Specifies the names of the scheduled jobs.</span></span>
<span data-ttu-id="64e3b-154">**Remove-JobTrigger** verwijdert de taak triggers uit de opgegeven geplande taken.</span><span class="sxs-lookup"><span data-stu-id="64e3b-154">**Remove-JobTrigger** deletes the job triggers from the specified scheduled jobs.</span></span>
<span data-ttu-id="64e3b-155">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="64e3b-155">Wildcards are supported.</span></span>

<span data-ttu-id="64e3b-156">Gebruik de cmdlet Get-ScheduledJob om de namen van geplande taken op de lokale computer of een externe computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="64e3b-156">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="64e3b-157">-TriggerId</span><span class="sxs-lookup"><span data-stu-id="64e3b-157">-TriggerId</span></span>
<span data-ttu-id="64e3b-158">Hiermee verwijdert u alleen de opgegeven taak triggers.</span><span class="sxs-lookup"><span data-stu-id="64e3b-158">Deletes only the specified job triggers.</span></span>
<span data-ttu-id="64e3b-159">Standaard verwijdert **Remove-JobTrigger** alle triggers uit de geplande taken.</span><span class="sxs-lookup"><span data-stu-id="64e3b-159">By default, **Remove-JobTrigger** deletes all triggers from the scheduled jobs.</span></span>
<span data-ttu-id="64e3b-160">Gebruik deze para meter wanneer de geplande taken meerdere taak triggers hebben.</span><span class="sxs-lookup"><span data-stu-id="64e3b-160">Use this parameter when the scheduled jobs have multiple job triggers.</span></span>

<span data-ttu-id="64e3b-161">Voer de trigger-Id's in van een of meer taak triggers van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="64e3b-161">Enter the trigger IDs of one or more job triggers of a scheduled job.</span></span>
<span data-ttu-id="64e3b-162">Als u meerdere geplande taken opgeeft, verwijdert **Remove-JobTrigger** de taak trigger met de opgegeven id uit alle geplande taken.</span><span class="sxs-lookup"><span data-stu-id="64e3b-162">If you specify multiple scheduled jobs, **Remove-JobTrigger** deletes the job trigger with the specified ID from all scheduled jobs.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="64e3b-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64e3b-163">CommonParameters</span></span>
<span data-ttu-id="64e3b-164">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="64e3b-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="64e3b-165">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="64e3b-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="64e3b-166">INVOER</span><span class="sxs-lookup"><span data-stu-id="64e3b-166">INPUTS</span></span>

### <span data-ttu-id="64e3b-167">Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="64e3b-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="64e3b-168">U kunt geplande taken door sluizen naar de cmdlet **Remove-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="64e3b-168">You can pipe scheduled jobs to the **Remove-JobTrigger** cmdlet.</span></span>

## <span data-ttu-id="64e3b-169">UITVOER</span><span class="sxs-lookup"><span data-stu-id="64e3b-169">OUTPUTS</span></span>

### <span data-ttu-id="64e3b-170">Geen</span><span class="sxs-lookup"><span data-stu-id="64e3b-170">None</span></span>
<span data-ttu-id="64e3b-171">De cmdlet genereert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="64e3b-171">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="64e3b-172">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="64e3b-172">NOTES</span></span>

## <span data-ttu-id="64e3b-173">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="64e3b-173">RELATED LINKS</span></span>

[<span data-ttu-id="64e3b-174">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="64e3b-174">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="64e3b-175">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="64e3b-175">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="64e3b-176">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="64e3b-176">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="64e3b-177">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="64e3b-177">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="64e3b-178">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="64e3b-178">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="64e3b-179">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="64e3b-179">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="64e3b-180">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="64e3b-180">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="64e3b-181">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="64e3b-181">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="64e3b-182">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="64e3b-182">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="64e3b-183">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="64e3b-183">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="64e3b-184">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="64e3b-184">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="64e3b-185">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="64e3b-185">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="64e3b-186">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="64e3b-186">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="64e3b-187">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="64e3b-187">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="64e3b-188">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="64e3b-188">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="64e3b-189">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="64e3b-189">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
