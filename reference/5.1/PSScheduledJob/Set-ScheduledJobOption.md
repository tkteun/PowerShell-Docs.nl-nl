---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJobOption
ms.openlocfilehash: 6647e9ba4e2ee49afa90dd382573d437d2deaee6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250291"
---
# <span data-ttu-id="9cfc9-103">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9cfc9-103">Set-ScheduledJobOption</span></span>

## <span data-ttu-id="9cfc9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9cfc9-104">SYNOPSIS</span></span>
<span data-ttu-id="9cfc9-105">Hiermee wijzigt u de taak opties van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-105">Changes the job options of a scheduled job.</span></span>

## <span data-ttu-id="9cfc9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9cfc9-106">SYNTAX</span></span>

```
Set-ScheduledJobOption [-InputObject] <ScheduledJobOptions> [-PassThru] [-RunElevated] [-HideInTaskScheduler]
 [-RestartOnIdleResume] [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart]
 [-RequireNetwork] [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery]
 [-IdleTimeout <TimeSpan>] [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## <span data-ttu-id="9cfc9-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9cfc9-107">DESCRIPTION</span></span>
<span data-ttu-id="9cfc9-108">De cmdlet **set-ScheduledJobOptions** wijzigt de taak opties van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-108">The **Set-ScheduledJobOptions** cmdlet changes the job options of scheduled jobs.</span></span>

<span data-ttu-id="9cfc9-109">Als u de opties van een geplande taak wilt wijzigen, begint u met de cmdlet Get-ScheduledJobOption om de taak opties van een geplande taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-109">To change the options of a scheduled job, begin by using the Get-ScheduledJobOption cmdlet to get the job options of a scheduled job.</span></span>
<span data-ttu-id="9cfc9-110">Vervolgens kunt u de opties voor de **ScheduledJobOption instellen** of de opties in een variabele opslaan en de para meter *input object* van de cmdlet **set-ScheduledJobOption** gebruiken om de opties te identificeren.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-110">Then, pipe the options to **Set-ScheduledJobOption** or save the options in a variable and use the *InputObject* parameter of **Set-ScheduledJobOption** cmdlet to identify the options.</span></span>
<span data-ttu-id="9cfc9-111">Gebruik de resterende para meters van **set-ScheduledJobOption** om de taak opties te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-111">Use the remaining parameters of **Set-ScheduledJobOption** to change the job options.</span></span>

<span data-ttu-id="9cfc9-112">Als u een taak optie wilt inschakelen, gebruikt u de para meter waarmee die optie wordt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-112">To turn on a job option, use the parameter that sets that option.</span></span>
<span data-ttu-id="9cfc9-113">Als u een optie wilt uitschakelen, typt u de parameter naam, een dubbele punt (:) en $False.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-113">To turn off an option, type the parameter name, a colon (:), and $False.</span></span>
<span data-ttu-id="9cfc9-114">Als u bijvoorbeeld de optie *RunElevated* wilt uitschakelen, typt u `-RunElevated:$False` .</span><span class="sxs-lookup"><span data-stu-id="9cfc9-114">For example, to turn off the *RunElevated* option, type `-RunElevated:$False`.</span></span>

<span data-ttu-id="9cfc9-115">Elk object taak opties bevat een taak definitie-eigenschap die de geplande taak bevat, waardoor de koppeling met de geplande taak behouden blijft wanneer de taak opties worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-115">Each job options object includes a JobDefinition property that contains the scheduled job, so the association with the scheduled job is retained when the job options are changed.</span></span>

<span data-ttu-id="9cfc9-116">De geplande taak opties bepalen hoe de taak wordt uitgevoerd wanneer deze wordt gestart door de taak planner.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-116">The scheduled job options determine how the job runs when it is started by Task Scheduler.</span></span>
<span data-ttu-id="9cfc9-117">Deze opties worden niet toegepast wanneer u de cmdlet Start-Job gebruikt om een geplande taak te starten.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-117">These options to not apply when you use the Start-Job cmdlet to start a scheduled job.</span></span>

<span data-ttu-id="9cfc9-118">**Set-ScheduledJobOption** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-118">**Set-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="9cfc9-119">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="9cfc9-120">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="9cfc9-121">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="9cfc9-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9cfc9-122">EXAMPLES</span></span>

### <span data-ttu-id="9cfc9-123">Voor beeld 1: taak opties wijzigen</span><span class="sxs-lookup"><span data-stu-id="9cfc9-123">Example 1: Change job options</span></span>

```
PS C:\> Get-ScheduledJobOption -Name "DeployPackage"
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          :

The second command uses the **Set-ScheduledJobOpton** cmdlet to change the job options so the values of the WakeToRun and RunWithoutNetwork properties are $True. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-ScheduledJobOption -Name "DeployPackage" | Set-ScheduledJobOption -WakeToRun -RequireNetwork:$False -Passthru
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNewJobDefinition          :
```

<span data-ttu-id="9cfc9-124">In dit voor beeld ziet u hoe u de opties van een geplande taak op de lokale computer wijzigt.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-124">This example shows how to change the options of a scheduled job on the local computer.</span></span>

<span data-ttu-id="9cfc9-125">De eerste opdracht gebruikt de cmdlet Get-ScheduledJobOption om de taak opties van de geplande DeployPackage-taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-125">The first command uses the Get-ScheduledJobOption cmdlet to get the job options of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="9cfc9-126">In de uitvoer ziet u dat de eigenschappen WakeToRun en RunElevated zijn ingesteld op $False.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-126">The output shows that the WakeToRun and RunElevated properties are set to $False.</span></span>

<span data-ttu-id="9cfc9-127">Deze opdracht is niet vereist. het is alleen opgenomen om het effect van de optie wijziging weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-127">This command is not required; it is included only to show the effect of the option change.</span></span>

### <span data-ttu-id="9cfc9-128">Voor beeld 2: een optie wijzigen voor alle externe geplande taken</span><span class="sxs-lookup"><span data-stu-id="9cfc9-128">Example 2: Change an option on all remote scheduled jobs</span></span>

```
PS C:\> Invoke-Command -Computer "Server01" -ScriptBlock {Get-ScheduledJob | Get-ScheduledJobOption | Set-ScheduledJobOption -IdleTimeout 2:00:00}
```

<span data-ttu-id="9cfc9-129">Met deze opdracht wordt de waarde van de *IdleTimeout* van één uur (de standaard waarde) gewijzigd in twee uur op alle geplande taken op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-129">This command changes the value of the *IdleTimeout* from one hour (the default value) to two hours on all scheduled jobs on the Server01 computer.</span></span>

<span data-ttu-id="9cfc9-130">De opdracht gebruikt de cmdlet Invoke-Command om een opdracht uit te voeren op de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-130">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>

<span data-ttu-id="9cfc9-131">De externe opdracht begint met een Get-ScheduledJob opdracht waarmee alle geplande taken op de computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-131">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="9cfc9-132">De geplande taken worden door gegeven aan de cmdlet Get-ScheduledJobOption, waarmee de taak opties van de geplande taken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-132">The scheduled jobs are piped to the Get-ScheduledJobOption cmdlet, which gets the job options of the scheduled jobs.</span></span>
<span data-ttu-id="9cfc9-133">Elk-taak opties object bevat een taak definitie-eigenschap die de geplande taak bevat, zodat het opties-object is gekoppeld aan de geplande taak, zelfs wanneer dit wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-133">Each job options object contains a JobDefinition property that contains the scheduled job, so the options object remains associated with the scheduled job even when it is changed.</span></span>

<span data-ttu-id="9cfc9-134">De taak triggers worden gepiped naar de cmdlet **set-ScheduledJobOption** , waarmee de waarde van de optie *IdleTimeout* wordt gewijzigd in twee uur (2:00:00).</span><span class="sxs-lookup"><span data-stu-id="9cfc9-134">The job triggers are piped to the **Set-ScheduledJobOption** cmdlet, which changes the value of the *IdleTimeout* option to two hours (2:00:00).</span></span>

## <span data-ttu-id="9cfc9-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9cfc9-135">PARAMETERS</span></span>

### <span data-ttu-id="9cfc9-136">-ContinueIfGoingOnBattery</span><span class="sxs-lookup"><span data-stu-id="9cfc9-136">-ContinueIfGoingOnBattery</span></span>
<span data-ttu-id="9cfc9-137">Stop de geplande taak niet als de computer overschakelt naar de accu stroom (de verbinding met netstroom verbreekt) terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-137">Do not stop the scheduled job if the computer switches to battery power (disconnects from AC power) while the job is running.</span></span>
<span data-ttu-id="9cfc9-138">Geplande taken worden standaard gestopt wanneer de computer de verbinding met netstroom verbreekt.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-138">By default, scheduled jobs stop when the computer disconnects from AC power.</span></span>

<span data-ttu-id="9cfc9-139">Met de para meter *ContinueIfGoingOnBattery* wordt de waarde van de eigenschap StopIfGoingOnBatteries van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-139">The *ContinueIfGoingOnBattery* parameter sets the value of the StopIfGoingOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="9cfc9-140">-DoNotAllowDemandStart</span><span class="sxs-lookup"><span data-stu-id="9cfc9-140">-DoNotAllowDemandStart</span></span>
<span data-ttu-id="9cfc9-141">Start de taak alleen wanneer deze wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-141">Start the job only when it is triggered.</span></span>
<span data-ttu-id="9cfc9-142">Gebruikers kunnen de taak niet hand matig starten, bijvoorbeeld met behulp van de functie uitvoeren in taak planner.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-142">Users cannot start the job manually, such as by using the Run feature in Task Scheduler.</span></span>

<span data-ttu-id="9cfc9-143">Deze para meter is alleen van invloed op de taak planner.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-143">This parameter only affects Task Scheduler.</span></span>
<span data-ttu-id="9cfc9-144">Hiermee wordt niet voor komen dat gebruikers de cmdlet Start-Job gebruiken om de taak te starten.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-144">It does not prevents users from using the Start-Job cmdlet to start the job.</span></span>

<span data-ttu-id="9cfc9-145">Met de para meter *DoNotAllowDemandStart* wordt de waarde van de eigenschap DoNotAllowDemandStart van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-145">The *DoNotAllowDemandStart* parameter sets the value of the DoNotAllowDemandStart property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="9cfc9-146">-HideInTaskScheduler</span><span class="sxs-lookup"><span data-stu-id="9cfc9-146">-HideInTaskScheduler</span></span>
<span data-ttu-id="9cfc9-147">De taak niet weer geven in taak planner.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-147">Do not display the job in Task Scheduler.</span></span>
<span data-ttu-id="9cfc9-148">Deze waarde is alleen van invloed op de computer waarop de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-148">This value affects only the computer on which the job runs.</span></span>
<span data-ttu-id="9cfc9-149">Geplande taken worden standaard weer gegeven in taak planner.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-149">By default, scheduled tasks appear in Task Scheduler.</span></span>

<span data-ttu-id="9cfc9-150">Zelfs als een taak verborgen is, kunnen gebruikers de taak weer geven door de optie **verborgen taken** weer geven in taak planner te selecteren.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-150">Even if a task is hidden, users can display the task by selecting the **Show hidden tasks** view option in Task Scheduler.</span></span>

<span data-ttu-id="9cfc9-151">Met de para meter *HideInTaskScheduler* wordt de waarde van de eigenschap ShowInTaskScheduler van geplande taken ingesteld op $false.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-151">The *HideInTaskScheduler* parameter sets the value of the ShowInTaskScheduler property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="9cfc9-152">-IdleDuration</span><span class="sxs-lookup"><span data-stu-id="9cfc9-152">-IdleDuration</span></span>
<span data-ttu-id="9cfc9-153">Hiermee geeft u op hoe lang de computer inactief moet zijn voordat de taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-153">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="9cfc9-154">De standaardwaarde is 10 minuten.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-154">The default value is 10 minutes.</span></span>
<span data-ttu-id="9cfc9-155">Als de computer niet inactief is voor de opgegeven duur voordat de waarde van *IdleTimeout* verloopt, wordt de geplande taak niet uitgevoerd tot de volgende geplande tijd, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-155">If the computer is not idle for the specified duration before the value of *IdleTimeout* expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="9cfc9-156">Voer een time span-object in, zoals het nummer dat is gegenereerd door de New-TimeSpan cmdlet of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format die automatisch wordt geconverteerd naar een **time span** -object.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-156">Enter a timespan object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="9cfc9-157">Als u deze waarde wilt inschakelen, gebruikt u de para meter *StartIfIdle* .</span><span class="sxs-lookup"><span data-stu-id="9cfc9-157">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="9cfc9-158">De eigenschap StartIfNotIdle van geplande taken is standaard ingesteld op $True en Windows Power shell negeert de waarden voor *IdleDuration* en *IdleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="9cfc9-158">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9cfc9-159">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="9cfc9-159">-IdleTimeout</span></span>
<span data-ttu-id="9cfc9-160">Hiermee geeft u op hoe lang de computer inactief moet zijn voordat de taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-160">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="9cfc9-161">De standaardwaarde is 10 minuten.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-161">The default value is 10 minutes.</span></span>
<span data-ttu-id="9cfc9-162">Als de computer niet inactief is voor de opgegeven duur voordat de waarde van **IdleTimeout** verloopt, wordt de geplande taak niet uitgevoerd tot de volgende geplande tijd, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-162">If the computer is not idle for the specified duration before the value of **IdleTimeout** expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="9cfc9-163">Voer een time span-object in, zoals het nummer dat is gegenereerd door de New-TimeSpan cmdlet of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format die automatisch wordt geconverteerd naar een **time span** -object.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-163">Enter a timespan object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="9cfc9-164">Als u deze waarde wilt inschakelen, gebruikt u de para meter *StartIfIdle* .</span><span class="sxs-lookup"><span data-stu-id="9cfc9-164">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="9cfc9-165">De eigenschap StartIfNotIdle van geplande taken is standaard ingesteld op $True en Windows Power shell negeert de waarden voor *IdleDuration* en *IdleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="9cfc9-165">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9cfc9-166">-Input object</span><span class="sxs-lookup"><span data-stu-id="9cfc9-166">-InputObject</span></span>
<span data-ttu-id="9cfc9-167">Hiermee geeft u de taak opties.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-167">Specifies the job options.</span></span>
<span data-ttu-id="9cfc9-168">Voer een variabele in die **ScheduledJobOptions** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobOptions** -objecten worden opgehaald, zoals een Get-ScheduledJobOption opdracht.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-168">Enter a variable that contains **ScheduledJobOptions** objects or type a command or expression that gets **ScheduledJobOptions** objects, such as a Get-ScheduledJobOption command.</span></span>
<span data-ttu-id="9cfc9-169">U kunt ook een **ScheduledJobOptions** -object pipeen naar **set-ScheduledJobOption**.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-169">You can also pipe a **ScheduledJobOptions** object to **Set-ScheduledJobOption**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9cfc9-170">-MultipleInstancePolicy</span><span class="sxs-lookup"><span data-stu-id="9cfc9-170">-MultipleInstancePolicy</span></span>
<span data-ttu-id="9cfc9-171">Hiermee wordt bepaald hoe het systeem reageert op een aanvraag om een exemplaar van een geplande taak te starten terwijl een ander exemplaar van de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-171">Determines how the system responds to a request to start an instance of a scheduled job while another instance of the job is running.</span></span>
<span data-ttu-id="9cfc9-172">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="9cfc9-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9cfc9-173">IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-173">IgnoreNew.</span></span>
<span data-ttu-id="9cfc9-174">Het nieuwe taak exemplaar wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-174">The new job instance is ignored.</span></span>
<span data-ttu-id="9cfc9-175">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-175">This is the default value.</span></span>
- <span data-ttu-id="9cfc9-176">Daarmee.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-176">Parallel.</span></span>
<span data-ttu-id="9cfc9-177">Het nieuwe taak exemplaar wordt onmiddellijk gestart.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-177">The new job instance starts immediately.</span></span>
- <span data-ttu-id="9cfc9-178">Wachtrij.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-178">Queue.</span></span>
<span data-ttu-id="9cfc9-179">Het nieuwe taak exemplaar wordt gestart zodra het huidige exemplaar is voltooid.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-179">The new job instance starts as soon as the current instance completes.</span></span>
- <span data-ttu-id="9cfc9-180">StopExisting.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-180">StopExisting.</span></span>
<span data-ttu-id="9cfc9-181">Het huidige exemplaar van de taak stop en het nieuwe exemplaar wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-181">The current instance of the job stop and the new instance starts.</span></span>

<span data-ttu-id="9cfc9-182">Als u de taak wilt uitvoeren, moeten aan alle voor waarden voor de taak planning worden voldaan.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-182">To run the job, all conditions for the job schedule must be met.</span></span>
<span data-ttu-id="9cfc9-183">Als de voor waarden die zijn ingesteld door de para meters *RequireNetwork* , *IdleDuration* en *IdleTimeout* niet worden vervuld, wordt het taak exemplaar niet gestart, ongeacht de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-183">For example, if the conditions that are set by the *RequireNetwork* , *IdleDuration* , and *IdleTimeout* parameters are not satisfied, the job instance is not started, regardless of the value of this parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.TaskMultipleInstancePolicy
Parameter Sets: (All)
Aliases:
Accepted values: None, IgnoreNew, Parallel, Queue, StopExisting

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9cfc9-184">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9cfc9-184">-PassThru</span></span>
<span data-ttu-id="9cfc9-185">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-185">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="9cfc9-186">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-186">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9cfc9-187">-RequireNetwork</span><span class="sxs-lookup"><span data-stu-id="9cfc9-187">-RequireNetwork</span></span>
<span data-ttu-id="9cfc9-188">De geplande taak wordt alleen uitgevoerd als er netwerk verbindingen beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-188">Runs the scheduled job only when network connections are available.</span></span>

<span data-ttu-id="9cfc9-189">Als u deze para meter opgeeft en het netwerk is niet beschikbaar op de geplande begin tijd, wordt de taak niet uitgevoerd tot de volgende geplande begin tijd, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-189">If you specify this parameter and the network is not available at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="9cfc9-190">Met de para meter *RequireNetwork* wordt de waarde van de eigenschap RunWithoutNetwork van geplande taken ingesteld op $false.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-190">The *RequireNetwork* parameter sets the value of the RunWithoutNetwork property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="9cfc9-191">-RestartOnIdleResume</span><span class="sxs-lookup"><span data-stu-id="9cfc9-191">-RestartOnIdleResume</span></span>
<span data-ttu-id="9cfc9-192">Hiermee wordt een geplande taak opnieuw gestart wanneer de computer inactief wordt.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-192">Restarts a scheduled job when the computer becomes idle.</span></span>
<span data-ttu-id="9cfc9-193">Deze para meter werkt met de para meter *StopIfGoingOffIdle* , die een actieve geplande taak onderbreekt als de computer actief wordt (de niet-actieve status blijft).</span><span class="sxs-lookup"><span data-stu-id="9cfc9-193">This parameter works with the *StopIfGoingOffIdle* parameter, which suspends a running scheduled job if the computer becomes active (leaves the idle state).</span></span>

<span data-ttu-id="9cfc9-194">Met de para meter *RestartOnIdleResume* wordt de waarde van de eigenschap RestartOnIdleResume van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-194">The *RestartOnIdleResume* parameter sets the value of the RestartOnIdleResume property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="9cfc9-195">-RunElevated</span><span class="sxs-lookup"><span data-stu-id="9cfc9-195">-RunElevated</span></span>
<span data-ttu-id="9cfc9-196">De geplande taak wordt uitgevoerd met de machtigingen van een lid van de groep Administrators op de computer waarop de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-196">Runs the scheduled job with the permissions of a member of the Administrators group on the computer on which the job runs.</span></span>

<span data-ttu-id="9cfc9-197">Als u wilt dat een geplande taak wordt uitgevoerd met beheerders machtigingen, gebruikt u de para meter *Credential* van Register-ScheduledJob om expliciete referenties voor de taak op te geven.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-197">To enable a scheduled job to run with Administrator permissions, use the *Credential* parameter of Register-ScheduledJob to provide explicit credential for the job.</span></span>

<span data-ttu-id="9cfc9-198">Met de para meter **RunElevated** wordt de waarde van de eigenschap **RunElevated** van geplande taken ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-198">The **RunElevated** parameter sets the value of the **RunElevated** property of scheduled jobs to True.</span></span>

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

### <span data-ttu-id="9cfc9-199">-StartIfIdle</span><span class="sxs-lookup"><span data-stu-id="9cfc9-199">-StartIfIdle</span></span>
<span data-ttu-id="9cfc9-200">Start de geplande taak als de computer niet actief is geweest gedurende de tijd die is opgegeven door de para meter **IdleDuration** voordat de tijd die is opgegeven door de para meter *IdleTimeout* is verlopen.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-200">Starts the scheduled job if the computer has been idle for the time specified by the **IdleDuration** parameter before the time specified by the *IdleTimeout* parameter expires.</span></span>

<span data-ttu-id="9cfc9-201">Standaard worden de para meters *IdleDuration* en *IdleTimeout* genegeerd en wordt de taak gestart op de geplande begin tijd, zelfs als de computer bezet is.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-201">By default, the *IdleDuration* and *IdleTimeout* parameters are ignored and the job starts at the scheduled start time even if the computer is busy.</span></span>

<span data-ttu-id="9cfc9-202">Als u deze para meter opgeeft en de computer bezet is (niet inactief) op de geplande begin tijd, wordt de taak niet uitgevoerd tot de volgende geplande begin tijd, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-202">If you specify this parameter and the computer is busy (not idle) at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="9cfc9-203">De para meter *StartIfIdle* stelt de waarde van de eigenschap **StartIfNotIdle** van geplande taken in op false.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-203">The *StartIfIdle* parameter sets the value of the **StartIfNotIdle** property of scheduled jobs to False.</span></span>

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

### <span data-ttu-id="9cfc9-204">-StartIfOnBattery</span><span class="sxs-lookup"><span data-stu-id="9cfc9-204">-StartIfOnBattery</span></span>
<span data-ttu-id="9cfc9-205">Hiermee wordt de geplande taak gestart, zelfs als de computer op de geplande begin tijd op de accu werkt.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-205">Starts the scheduled job even if the computer is running on batteries at the scheduled start time.</span></span>
<span data-ttu-id="9cfc9-206">De standaard waarde is False.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-206">The default value is False.</span></span>

<span data-ttu-id="9cfc9-207">Met de para meter *StartIfOnBattery* wordt de waarde van de eigenschap **StartIfOnBatteries** van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-207">The *StartIfOnBattery* parameter sets the value of the **StartIfOnBatteries** property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="9cfc9-208">-StopIfGoingOffIdle</span><span class="sxs-lookup"><span data-stu-id="9cfc9-208">-StopIfGoingOffIdle</span></span>
<span data-ttu-id="9cfc9-209">Hiermee wordt een actieve geplande taak onderbroken als de computer actief wordt (niet-inactief) terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-209">Suspends a running scheduled job if the computer becomes active (not idle) while the job is running.</span></span>

<span data-ttu-id="9cfc9-210">Standaard wordt een geplande taak die wordt onderbroken wanneer de computer actief wordt hervat wanneer de computer weer actief wordt.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-210">By default, a scheduled job that is suspended when the computer becomes active resumes when the computer becomes idle again.</span></span>
<span data-ttu-id="9cfc9-211">Als u dit standaard gedrag wilt wijzigen, gebruikt u de para meter *RestartOnIdleResume* .</span><span class="sxs-lookup"><span data-stu-id="9cfc9-211">To change this default behavior, use the *RestartOnIdleResume* parameter.</span></span>

<span data-ttu-id="9cfc9-212">Met de para meter *StopIfGoingOffIdle* wordt de waarde van de eigenschap StopIfGoingOffIdle van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-212">The *StopIfGoingOffIdle* parameter sets the value of the StopIfGoingOffIdle property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="9cfc9-213">-WakeToRun</span><span class="sxs-lookup"><span data-stu-id="9cfc9-213">-WakeToRun</span></span>
<span data-ttu-id="9cfc9-214">De computer uit de slaap stand of sluimer stand halen op de geplande begin tijd zodat de taak kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-214">Wakes the computer from a Hibernate or Sleep state at the scheduled start time so it can run the job.</span></span>
<span data-ttu-id="9cfc9-215">Als de computer zich standaard in de sluimer stand of slaap stand bevindt op de geplande begin tijd, wordt de taak niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-215">By default, if the computer is in a Hibernate or Sleep state at the scheduled start time, the job does not run.</span></span>

<span data-ttu-id="9cfc9-216">Met de para meter *WakeToRun* wordt de waarde van de eigenschap WakeToRun van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-216">The *WakeToRun* parameter sets the value of the WakeToRun property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="9cfc9-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9cfc9-217">CommonParameters</span></span>
<span data-ttu-id="9cfc9-218">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9cfc9-219">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9cfc9-220">INVOER</span><span class="sxs-lookup"><span data-stu-id="9cfc9-220">INPUTS</span></span>

### <span data-ttu-id="9cfc9-221">Micro soft. Power shell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="9cfc9-221">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>
<span data-ttu-id="9cfc9-222">U kunt een geplande taak opties-object door geven aan **set-ScheduledJobOption**.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-222">You can pipe a scheduled job options object to **Set-ScheduledJobOption**.</span></span>

## <span data-ttu-id="9cfc9-223">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9cfc9-223">OUTPUTS</span></span>

### <span data-ttu-id="9cfc9-224">Geen of Microsoft. Power shell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="9cfc9-224">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>
<span data-ttu-id="9cfc9-225">Wanneer u de para meter *PassThru* gebruikt, retourneert **set-ScheduledJobOption** de taak opties die zijn gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-225">When you use the *Passthru* parameter, **Set-ScheduledJobOption** returns the job options that were changed.</span></span>
<span data-ttu-id="9cfc9-226">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9cfc9-226">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9cfc9-227">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9cfc9-227">NOTES</span></span>

## <span data-ttu-id="9cfc9-228">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9cfc9-228">RELATED LINKS</span></span>

[<span data-ttu-id="9cfc9-229">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9cfc9-229">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="9cfc9-230">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9cfc9-230">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="9cfc9-231">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9cfc9-231">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="9cfc9-232">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9cfc9-232">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="9cfc9-233">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9cfc9-233">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="9cfc9-234">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9cfc9-234">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="9cfc9-235">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9cfc9-235">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="9cfc9-236">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9cfc9-236">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="9cfc9-237">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9cfc9-237">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="9cfc9-238">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9cfc9-238">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="9cfc9-239">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9cfc9-239">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="9cfc9-240">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9cfc9-240">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="9cfc9-241">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9cfc9-241">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="9cfc9-242">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9cfc9-242">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="9cfc9-243">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9cfc9-243">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="9cfc9-244">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9cfc9-244">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
