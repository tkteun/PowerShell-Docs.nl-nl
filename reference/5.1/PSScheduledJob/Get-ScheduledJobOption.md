---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJobOption
ms.openlocfilehash: 5c317be9add0898137aceed6c39032f3e271bac1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250304"
---
# <span data-ttu-id="9b1df-103">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9b1df-103">Get-ScheduledJobOption</span></span>

## <span data-ttu-id="9b1df-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9b1df-104">SYNOPSIS</span></span>
<span data-ttu-id="9b1df-105">Hiermee worden de taak opties van geplande taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9b1df-105">Gets the job options of scheduled jobs.</span></span>

## <span data-ttu-id="9b1df-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9b1df-106">SYNTAX</span></span>

### <span data-ttu-id="9b1df-107">Taak definitie (standaard)</span><span class="sxs-lookup"><span data-stu-id="9b1df-107">JobDefinition (Default)</span></span>

```
Get-ScheduledJobOption [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### <span data-ttu-id="9b1df-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="9b1df-108">JobDefinitionId</span></span>

```
Get-ScheduledJobOption [-Id] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="9b1df-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="9b1df-109">JobDefinitionName</span></span>

```
Get-ScheduledJobOption [-Name] <String> [<CommonParameters>]
```

## <span data-ttu-id="9b1df-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9b1df-110">DESCRIPTION</span></span>
<span data-ttu-id="9b1df-111">De cmdlet **Get-ScheduledJobOption** haalt de taak opties van geplande taken op.</span><span class="sxs-lookup"><span data-stu-id="9b1df-111">The **Get-ScheduledJobOption** cmdlet gets the job options of scheduled jobs.</span></span>
<span data-ttu-id="9b1df-112">U kunt deze opdracht gebruiken om de taak opties te controleren of om de taak opties naar andere cmdlets te pipeen.</span><span class="sxs-lookup"><span data-stu-id="9b1df-112">You can use this command to examine the job options or to pipe the job options to other cmdlets.</span></span>

<span data-ttu-id="9b1df-113">Taak opties worden niet onafhankelijk van de schijf opgeslagen. ze maken deel uit van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="9b1df-113">Job options are not saved to disk independently; they are part of a scheduled job.</span></span>
<span data-ttu-id="9b1df-114">Als u de taak opties van een geplande taak wilt weer geven, geeft u de geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="9b1df-114">To get the job options of a scheduled job, specify the scheduled job.</span></span>

<span data-ttu-id="9b1df-115">Gebruik de para meters van de cmdlet **Get-ScheduledJobOption** om de geplande taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="9b1df-115">Use the parameters of the **Get-ScheduledJobOption** cmdlet to identify the scheduled job.</span></span>
<span data-ttu-id="9b1df-116">U kunt geplande taken identificeren met hun namen of identificatie nummers of door **ScheduledJob** -objecten op te geven of te maken, zoals die die worden geretourneerd door de Get-ScheduledJob cmdlet, naar **Get-ScheduledJobOption**.</span><span class="sxs-lookup"><span data-stu-id="9b1df-116">You can identify scheduled jobs by their names or identification numbers, or by entering or piping **ScheduledJob** objects, such as those that are returned by the Get-ScheduledJob cmdlet, to **Get-ScheduledJobOption**.</span></span>

<span data-ttu-id="9b1df-117">**Get-ScheduledJobOption** is een van een verzameling cmdlets voor taak planning in de PSScheduledJob-module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9b1df-117">**Get-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="9b1df-118">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="9b1df-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="9b1df-119">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="9b1df-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="9b1df-120">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9b1df-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="9b1df-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9b1df-121">EXAMPLES</span></span>

### <span data-ttu-id="9b1df-122">Voor beeld 1: taak opties ophalen</span><span class="sxs-lookup"><span data-stu-id="9b1df-122">Example 1: Get job options</span></span>

```
PS C:\> Get-ScheduledJobOption -Name "*Backup*"
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : False

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="9b1df-123">Met deze opdracht worden de taak opties opgehaald van geplande taken met een back-up in hun namen.</span><span class="sxs-lookup"><span data-stu-id="9b1df-123">This command gets the job options of scheduled jobs that have BackUp in their names.</span></span>
<span data-ttu-id="9b1df-124">De resultaten geven het taak opties-object weer dat **Get-ScheduledJobOption** retourneert.</span><span class="sxs-lookup"><span data-stu-id="9b1df-124">The results show the job options object that **Get-ScheduledJobOption** returned.</span></span>

### <span data-ttu-id="9b1df-125">Voor beeld 2: alle taak opties ophalen</span><span class="sxs-lookup"><span data-stu-id="9b1df-125">Example 2: Get all job options</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption
```

<span data-ttu-id="9b1df-126">Met deze opdracht worden de taak opties van alle geplande taken op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9b1df-126">This command gets the job options of all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="9b1df-127">De Get-ScheduledJob cmdlet wordt gebruikt om de geplande taken op de lokale computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="9b1df-127">It uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="9b1df-128">Een pijplijn operator (|) verzendt de geplande taken naar de cmdlet **Get-ScheduledJobOption** , waarmee de taak opties van elke geplande taak worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9b1df-128">A pipeline operator (|) sends the scheduled jobs to the **Get-ScheduledJobOption** cmdlet, which gets the job options of each scheduled job.</span></span>

### <span data-ttu-id="9b1df-129">Voor beeld 3: de geselecteerde taak opties ophalen</span><span class="sxs-lookup"><span data-stu-id="9b1df-129">Example 3: Get selected job options</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun}
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : True

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The second command shows how to find to which scheduled job the job options belong. This command uses a pipeline operator (|) to send the selected job options to the ForEach-Object cmdlet, which gets the JobDefinition property of each options object. The JobDefinition property contains the originating job object. The results show that the selected options came from the DeployPkg scheduled job.
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun} | ForEach-Object {$_.JobDefinition}
Id         Name            Triggers        Command                                  Enabled

--         ----            --------        -------                                  -------

2          DeployPkg         {1, 2}        DeployPackage.ps1                        True
```

<span data-ttu-id="9b1df-130">In dit voor beeld ziet u hoe u met bepaalde waarden het object taak opties kunt vinden.</span><span class="sxs-lookup"><span data-stu-id="9b1df-130">This example shows how to find job options object with particular values.</span></span>

<span data-ttu-id="9b1df-131">Met de eerste opdracht worden taak opties opgehaald waarin de eigenschap RunElevated de waarde $True heeft en de eigenschap RunWithoutNetwork de waarde $False heeft.</span><span class="sxs-lookup"><span data-stu-id="9b1df-131">The first command gets job options in which the RunElevated property has a value of $True and the RunWithoutNetwork property has a value of $False.</span></span>
<span data-ttu-id="9b1df-132">De uitvoer toont het object **JobOptions** dat is geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="9b1df-132">The output shows the **JobOptions** object that was selected.</span></span>

### <span data-ttu-id="9b1df-133">Voor beeld 4: taak opties gebruiken om een nieuwe taak te maken</span><span class="sxs-lookup"><span data-stu-id="9b1df-133">Example 4: Use job options to create a new job</span></span>

```
PS C:\> $Opts = Get-ScheduledJobOption -Name "BackupTestLogs"
PS C:\> Register-ScheduledJob -Name "Archive-Scripts" -FilePath "\\Srv01\Scripts\ArchiveScripts.ps1" -ScheduledJobOption $Opts
```

<span data-ttu-id="9b1df-134">In dit voor beeld ziet u hoe u de taak opties kunt gebruiken die Get-ScheduledJobOption in een nieuwe geplande taak ontvangt.</span><span class="sxs-lookup"><span data-stu-id="9b1df-134">This example shows how to use the job options that Get-ScheduledJobOption gets in a new scheduled job.</span></span>

<span data-ttu-id="9b1df-135">De eerste opdracht gebruikt **Get-ScheduledJobOption** om de opties voor de taken van de geplande BackupTestLogs-taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="9b1df-135">The first command uses **Get-ScheduledJobOption** to get the jobs options of the BackupTestLogs scheduled job.</span></span>
<span data-ttu-id="9b1df-136">Met de opdracht worden de opties opgeslagen in de variabele $Opts.</span><span class="sxs-lookup"><span data-stu-id="9b1df-136">The command saves the options in the $Opts variable.</span></span>

<span data-ttu-id="9b1df-137">De tweede opdracht maakt gebruik van Register-ScheduledJob cmdlet om een nieuwe geplande taak te maken.</span><span class="sxs-lookup"><span data-stu-id="9b1df-137">The second command uses Register-ScheduledJob cmdlet to create a new scheduled job.</span></span>
<span data-ttu-id="9b1df-138">De waarde van de para meter *ScheduledJobOption* is het object Options in de variabele $opts.</span><span class="sxs-lookup"><span data-stu-id="9b1df-138">The value of the *ScheduledJobOption* parameter is the options object in the $Opts variable.</span></span>

### <span data-ttu-id="9b1df-139">Voor beeld 5: taak opties ophalen van een externe computer</span><span class="sxs-lookup"><span data-stu-id="9b1df-139">Example 5: Get job options from a remote computer</span></span>

```
PS C:\> $O = Invoke-Command -ComputerName "Srv01" -ScriptBlock {Get-ScheduledJob -Name "DataDemon" }
```

<span data-ttu-id="9b1df-140">Met deze opdracht wordt de cmdlet Invoke-Command gebruikt om de geplande taak opties van de DataDemon-taak op de Srv01-computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="9b1df-140">This command uses the Invoke-Command cmdlet to get the scheduled job options of the DataDemon job on the Srv01 computer.</span></span>
<span data-ttu-id="9b1df-141">Met de opdracht worden de opties opgeslagen in de variabele $O.</span><span class="sxs-lookup"><span data-stu-id="9b1df-141">The command saves the options in the $O variable.</span></span>

## <span data-ttu-id="9b1df-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9b1df-142">PARAMETERS</span></span>

### <span data-ttu-id="9b1df-143">-Id</span><span class="sxs-lookup"><span data-stu-id="9b1df-143">-Id</span></span>
<span data-ttu-id="9b1df-144">Hiermee geeft u het id-nummer van een geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="9b1df-144">Specifies the identification number of a scheduled job.</span></span>
<span data-ttu-id="9b1df-145">**Get-ScheduledJobOption** haalt de taak opties van de opgegeven geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="9b1df-145">**Get-ScheduledJobOption** gets the job options of the specified scheduled job.</span></span>

<span data-ttu-id="9b1df-146">Als u de identificatie nummers van geplande taken op de lokale computer of een externe computer wilt ophalen, gebruikt u de Get-ScheduledJob-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9b1df-146">To get the identification numbers of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="9b1df-147">-Input object</span><span class="sxs-lookup"><span data-stu-id="9b1df-147">-InputObject</span></span>
<span data-ttu-id="9b1df-148">Hiermee geeft u een geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="9b1df-148">Specifies a scheduled job.</span></span>
<span data-ttu-id="9b1df-149">Voer een variabele in die een **ScheduledJob** -object bevat of typ een opdracht of expressie waarmee een **ScheduledJob** -object wordt opgehaald, zoals een Get-ScheduledJob opdracht.</span><span class="sxs-lookup"><span data-stu-id="9b1df-149">Enter a variable that contains a **ScheduledJob** object or type a command or expression that gets a **ScheduledJob** object, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="9b1df-150">U kunt ook een **ScheduledJob** -object door sluizen naar **Get-ScheduledJobOption**.</span><span class="sxs-lookup"><span data-stu-id="9b1df-150">You can also pipe a **ScheduledJob** object to **Get-ScheduledJobOption**.</span></span>

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

### <span data-ttu-id="9b1df-151">-Name</span><span class="sxs-lookup"><span data-stu-id="9b1df-151">-Name</span></span>
<span data-ttu-id="9b1df-152">Hiermee geeft u de namen van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="9b1df-152">Specifies the names of scheduled jobs.</span></span>
<span data-ttu-id="9b1df-153">**Get-ScheduledJobOption** haalt de taak opties van de opgegeven geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="9b1df-153">**Get-ScheduledJobOption** gets the job options of the specified scheduled job.</span></span>
<span data-ttu-id="9b1df-154">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9b1df-154">Wildcards are supported.</span></span>

<span data-ttu-id="9b1df-155">Gebruik de cmdlet Get-ScheduledJob om de namen van geplande taken op de lokale computer of een externe computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="9b1df-155">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9b1df-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9b1df-156">CommonParameters</span></span>
<span data-ttu-id="9b1df-157">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9b1df-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9b1df-158">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9b1df-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9b1df-159">INVOER</span><span class="sxs-lookup"><span data-stu-id="9b1df-159">INPUTS</span></span>

### <span data-ttu-id="9b1df-160">Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="9b1df-160">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="9b1df-161">U kunt een geplande taak door sluizen van Get-ScheduledJob naar **Get-ScheduledJobOption**.</span><span class="sxs-lookup"><span data-stu-id="9b1df-161">You can pipe a scheduled job from Get-ScheduledJob to **Get-ScheduledJobOption**.</span></span>

## <span data-ttu-id="9b1df-162">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9b1df-162">OUTPUTS</span></span>

### <span data-ttu-id="9b1df-163">Micro soft. Power shell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="9b1df-163">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>

## <span data-ttu-id="9b1df-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9b1df-164">NOTES</span></span>

## <span data-ttu-id="9b1df-165">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9b1df-165">RELATED LINKS</span></span>

[<span data-ttu-id="9b1df-166">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9b1df-166">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="9b1df-167">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9b1df-167">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="9b1df-168">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9b1df-168">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="9b1df-169">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9b1df-169">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="9b1df-170">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9b1df-170">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="9b1df-171">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9b1df-171">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="9b1df-172">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9b1df-172">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="9b1df-173">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9b1df-173">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="9b1df-174">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9b1df-174">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="9b1df-175">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9b1df-175">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="9b1df-176">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9b1df-176">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="9b1df-177">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9b1df-177">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="9b1df-178">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9b1df-178">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="9b1df-179">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9b1df-179">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="9b1df-180">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9b1df-180">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="9b1df-181">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9b1df-181">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
