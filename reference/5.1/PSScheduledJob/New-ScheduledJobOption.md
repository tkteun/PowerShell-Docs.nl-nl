---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScheduledJobOption
ms.openlocfilehash: 35ada8d5aaa6a6c1fdc74a089308aefe13598b10
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250302"
---
# <span data-ttu-id="a081c-103">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="a081c-103">New-ScheduledJobOption</span></span>

## <span data-ttu-id="a081c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a081c-104">SYNOPSIS</span></span>
<span data-ttu-id="a081c-105">Hiermee maakt u een object dat geavanceerde opties bevat voor een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="a081c-105">Creates an object that contains advanced options for a scheduled job.</span></span>

## <span data-ttu-id="a081c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a081c-106">SYNTAX</span></span>

```
New-ScheduledJobOption [-RunElevated] [-HideInTaskScheduler] [-RestartOnIdleResume]
 [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart] [-RequireNetwork]
 [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery] [-IdleTimeout <TimeSpan>]
 [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## <span data-ttu-id="a081c-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a081c-107">DESCRIPTION</span></span>
<span data-ttu-id="a081c-108">Met de cmdlet **New-ScheduledJobOption** maakt u een object dat geavanceerde opties bevat voor een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="a081c-108">The **New-ScheduledJobOption** cmdlet creates an object that contains advanced options for a scheduled job.</span></span>

<span data-ttu-id="a081c-109">U kunt het **ScheduledJobOptions** -object gebruiken dat door **New-ScheduledJobOption** wordt geretourneerd om de taak opties voor een nieuwe of bestaande geplande taak in te stellen.</span><span class="sxs-lookup"><span data-stu-id="a081c-109">You can use the **ScheduledJobOptions** object that **New-ScheduledJobOption** returns to set job options for a new or existing scheduled job.</span></span>
<span data-ttu-id="a081c-110">U kunt ook taak opties instellen met behulp van de cmdlet Get-ScheduledJobOption om de taak opties van een bestaande geplande taak te verkrijgen of door een waarde van een hash-tabel te gebruiken om de taak opties weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a081c-110">Alternatively, you can set job options by using the Get-ScheduledJobOption cmdlet to get the job options of an existing scheduled job or by using a hash table value to represent the job options.</span></span>

<span data-ttu-id="a081c-111">Zonder para meters, **New-ScheduledJobOption** genereert een object dat de standaard waarden voor alle opties bevat.</span><span class="sxs-lookup"><span data-stu-id="a081c-111">Without parameters, **New-ScheduledJobOption** generates an object that contains the default values for all of the options.</span></span>
<span data-ttu-id="a081c-112">Omdat alle eigenschappen, met uitzonde ring van de eigenschap taak definitie, kunnen worden bewerkt, kunt u het resulterende object als sjabloon gebruiken en standaard optie objecten maken voor uw onderneming.</span><span class="sxs-lookup"><span data-stu-id="a081c-112">Because all of the properties except for the JobDefinition property can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="a081c-113">Controleer de standaard waarden van alle geplande taak opties bij het maken van geplande taken en het instellen van geplande taak opties.</span><span class="sxs-lookup"><span data-stu-id="a081c-113">When creating scheduled jobs and setting scheduled job options, review the default values of all scheduled job options.</span></span>
<span data-ttu-id="a081c-114">Geplande taken worden alleen uitgevoerd als aan alle voor waarden is voldaan die voor de uitvoering ervan zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="a081c-114">Scheduled jobs run only when all conditions set for their execution are satisfied.</span></span>

<span data-ttu-id="a081c-115">**New-ScheduledJobOption** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="a081c-115">**New-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="a081c-116">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="a081c-116">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="a081c-117">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="a081c-117">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="a081c-118">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a081c-118">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="a081c-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a081c-119">EXAMPLES</span></span>

### <span data-ttu-id="a081c-120">Voor beeld 1: een optie object voor een geplande taak maken met standaard waarden</span><span class="sxs-lookup"><span data-stu-id="a081c-120">Example 1: Create a scheduled job option object with default values</span></span>

```
PS C:\> New-ScheduledJobOption
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
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

<span data-ttu-id="a081c-121">Met deze opdracht maakt u een optie object voor een geplande taak dat alle standaard waarden bevat.</span><span class="sxs-lookup"><span data-stu-id="a081c-121">This command creates a scheduled job option object that has all of the default values.</span></span>

### <span data-ttu-id="a081c-122">Voor beeld 2: een optie object voor een geplande taak maken met aangepaste waarden</span><span class="sxs-lookup"><span data-stu-id="a081c-122">Example 2: Create a scheduled job option object with custom values</span></span>

```
PS C:\> New-ScheduledJobOption -RequireNetwork -StartIfOnBattery
StartIfOnBatteries     : True
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
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

<span data-ttu-id="a081c-123">Met de volgende opdracht maakt u een gepland taak object waarvoor het netwerk is vereist en waarop de geplande taak wordt uitgevoerd, zelfs als de computer niet is verbonden met de netspanning.</span><span class="sxs-lookup"><span data-stu-id="a081c-123">The following command creates a scheduled job object that requires the network and runs the scheduled job even if the computer is not connected to AC power.</span></span>

<span data-ttu-id="a081c-124">In de uitvoer ziet u *dat de waarde* van de eigenschap RunWithoutNetwork in $False is gewijzigd en dat de para meter *StartIfOnBattery* de waarde van de eigenschap StartIfOnBatteries heeft gewijzigd in $True.</span><span class="sxs-lookup"><span data-stu-id="a081c-124">The output shows that the *RequireNetwork* parameter changed the value of the RunWithoutNetwork property to $False and the *StartIfOnBattery* parameter changed the value of the StartIfOnBatteries property to $True.</span></span>

### <span data-ttu-id="a081c-125">Voor beeld 3: opties instellen voor een nieuwe geplande taak</span><span class="sxs-lookup"><span data-stu-id="a081c-125">Example 3: Set options for a new scheduled job</span></span>

```
The first command creates a **ScheduledJobOptions** object with the *RunElevated* parameter. It saves the object in the $RunAsAdmin variable.
PS C:\> $RunAsAdmin = New-ScheduledJobOption -RunElevated

The second command uses the Register-ScheduledJob cmdlet to create a new scheduled job. The value of the *ScheduledJobOption* parameter is the option object in the value of the $RunAsAdmin variable.
PS C:\> Register-ScheduledJob -Name Backup -FilePath D:\Scripts\Backup.ps1 -Trigger $Mondays -ScheduledJobOption $RunAsAdmin

The third command uses the Get-ScheduledJobOption cmdlet to get the job options of the Backup scheduled job.The cmdlet output shows that the RunElevated property is set to $True and the JobDefinition property of the job option object is now populated with the scheduled job object for the Backup scheduled job.
PS C:\> Get-ScheduledJobOption -Name Backup
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
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="a081c-126">In dit voor beeld ziet u hoe u het **ScheduledJobOptions** -object gebruikt dat door **New-ScheduledJobOption** wordt geretourneerd om de opties voor een nieuwe geplande taak in te stellen.</span><span class="sxs-lookup"><span data-stu-id="a081c-126">This example shows how to use the **ScheduledJobOptions** object that **New-ScheduledJobOption** returns to set the options for a new scheduled job.</span></span>

### <span data-ttu-id="a081c-127">Voor beeld 4: de eigenschappen van een geplande taak selecteren optie object</span><span class="sxs-lookup"><span data-stu-id="a081c-127">Example 4: Sort the properties of a scheduled job option object</span></span>

```
PS C:\> $Options = New-ScheduledJobOption -WakeToRun
PS C:\> $Options.PSObject.Properties | Sort-Object -Property Name | Format-Table -Property Name, Value -Autosize
Name                       Value
----                       -----
DoNotAllowDemandStart      False
IdleDuration            00:10:00
IdleTimeout             01:00:00
JobDefinition
MultipleInstancePolicy IgnoreNew
RestartOnIdleResume        False
RunElevated                False
RunWithoutNetwork           True
ShowInTaskScheduler         True
StartIfNotIdle              True
StartIfOnBatteries         False
StopIfGoingOffIdle         False
StopIfGoingOnBatteries      True
WakeToRun                   True
```

<span data-ttu-id="a081c-128">In dit voor beeld ziet u hoe u de eigenschappen van een **ScheduledJobOptions** -object in alfabetische volg orde sorteert voor eenvoudig lezen.</span><span class="sxs-lookup"><span data-stu-id="a081c-128">This example shows how to sort the properties of a **ScheduledJobOptions** object in alphabetical order for easy reading.</span></span>

<span data-ttu-id="a081c-129">De eerste opdracht maakt gebruik van de cmdlet **New-ScheduledJobOption** om een **ScheduledJobOptions** -object te maken.</span><span class="sxs-lookup"><span data-stu-id="a081c-129">The first command uses the **New-ScheduledJobOption** cmdlet to create a **ScheduledJobOptions** object.</span></span>
<span data-ttu-id="a081c-130">De opdracht maakt gebruik van de para meter *WakeToRun* en slaat het resulterende object op in de variabele $Options.</span><span class="sxs-lookup"><span data-stu-id="a081c-130">The command uses the *WakeToRun* parameter and saves the resulting object in the $Options variable.</span></span>

<span data-ttu-id="a081c-131">De tweede opdracht gebruikt de eigenschap **PSObject** van alle Windows Power shell-objecten en de eigenschap eigenschappen om de eigenschappen van $Options als objecten op te halen.</span><span class="sxs-lookup"><span data-stu-id="a081c-131">To get the properties of $Options as objects, the second command uses the **PSObject** property of all Windows PowerShell objects and its Properties property.</span></span>
<span data-ttu-id="a081c-132">De opdracht bewaart de eigenschappen objecten vervolgens naar de cmdlet Sort-Object, waarmee de eigenschappen in alfabetische volg orde op naam worden gesorteerd en vervolgens naar de Format-Table-cmdlet, waarin de namen en waarden van de eigenschappen in een tabel worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a081c-132">The command then pipes the property objects to the Sort-Object cmdlet, which sorts the properties in alphabetical order by name, and then to the Format-Table cmdlet, which displays the names and values of the properties in a table.</span></span>

<span data-ttu-id="a081c-133">Met deze indeling is het veel eenvoudiger om de eigenschap WakeToRun van het object **ScheduledJobOptions** in $Options te vinden en te controleren of de waarde van $false is gewijzigd in $True.</span><span class="sxs-lookup"><span data-stu-id="a081c-133">This format makes it much easier to find the WakeToRun property of the **ScheduledJobOptions** object in $Options and to verify that its value was changed from $False to $True.</span></span>

## <span data-ttu-id="a081c-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a081c-134">PARAMETERS</span></span>

### <span data-ttu-id="a081c-135">-ContinueIfGoingOnBattery</span><span class="sxs-lookup"><span data-stu-id="a081c-135">-ContinueIfGoingOnBattery</span></span>
<span data-ttu-id="a081c-136">Stop de geplande taak niet als de computer overschakelt naar de accu stroom (de verbinding met netstroom verbreekt) terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a081c-136">Do not stop the scheduled job if the computer switches to battery power (disconnects from AC power) while the job is running.</span></span>
<span data-ttu-id="a081c-137">Geplande taken worden standaard gestopt wanneer de computer de verbinding met netstroom verbreekt.</span><span class="sxs-lookup"><span data-stu-id="a081c-137">By default, scheduled jobs stop when the computer disconnects from AC power.</span></span>

<span data-ttu-id="a081c-138">Met de para meter *ContinueIfGoingOnBattery* wordt de waarde van de eigenschap StopIfGoingOnBatteries van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="a081c-138">The *ContinueIfGoingOnBattery* parameter sets the value of the StopIfGoingOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="a081c-139">-DoNotAllowDemandStart</span><span class="sxs-lookup"><span data-stu-id="a081c-139">-DoNotAllowDemandStart</span></span>
<span data-ttu-id="a081c-140">Start de taak alleen wanneer deze wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a081c-140">Start the job only when it is triggered.</span></span>
<span data-ttu-id="a081c-141">Gebruikers kunnen de taak niet hand matig starten, bijvoorbeeld met behulp van de functie uitvoeren in taak planner.</span><span class="sxs-lookup"><span data-stu-id="a081c-141">Users cannot start the job manually, such as by using the Run feature in Task Scheduler.</span></span>

<span data-ttu-id="a081c-142">Deze para meter is alleen van invloed op de taak planner.</span><span class="sxs-lookup"><span data-stu-id="a081c-142">This parameter only affects Task Scheduler.</span></span>
<span data-ttu-id="a081c-143">Hiermee wordt niet voor komen dat gebruikers de cmdlet Start-Job gebruiken om de taak te starten.</span><span class="sxs-lookup"><span data-stu-id="a081c-143">It does not prevents users from using the Start-Job cmdlet to start the job.</span></span>

<span data-ttu-id="a081c-144">Met de para meter *DoNotAllowDemandStart* wordt de waarde van de eigenschap DoNotAllowDemandStart van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="a081c-144">The *DoNotAllowDemandStart* parameter sets the value of the DoNotAllowDemandStart property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="a081c-145">-HideInTaskScheduler</span><span class="sxs-lookup"><span data-stu-id="a081c-145">-HideInTaskScheduler</span></span>
<span data-ttu-id="a081c-146">De taak niet weer geven in taak planner.</span><span class="sxs-lookup"><span data-stu-id="a081c-146">Do not display the job in Task Scheduler.</span></span>
<span data-ttu-id="a081c-147">Deze waarde is alleen van invloed op de computer waarop de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a081c-147">This value affects only the computer on which the job runs.</span></span>
<span data-ttu-id="a081c-148">Geplande taken worden standaard weer gegeven in taak planner.</span><span class="sxs-lookup"><span data-stu-id="a081c-148">By default, scheduled tasks appear in Task Scheduler.</span></span>

<span data-ttu-id="a081c-149">Zelfs als een taak verborgen is, kunnen gebruikers de taak weer geven door de optie verborgen taken weer geven in taak planner te selecteren.</span><span class="sxs-lookup"><span data-stu-id="a081c-149">Even if a task is hidden, users can display the task by selecting the Show hidden tasks view option in Task Scheduler.</span></span>

<span data-ttu-id="a081c-150">Met de para meter *HideInTaskScheduler* wordt de waarde van de eigenschap ShowInTaskScheduler van geplande taken ingesteld op $false.</span><span class="sxs-lookup"><span data-stu-id="a081c-150">The *HideInTaskScheduler* parameter sets the value of the ShowInTaskScheduler property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="a081c-151">-IdleDuration</span><span class="sxs-lookup"><span data-stu-id="a081c-151">-IdleDuration</span></span>
<span data-ttu-id="a081c-152">Hiermee geeft u op hoe lang de computer inactief moet zijn voordat de taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="a081c-152">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="a081c-153">De standaardwaarde is 10 minuten.</span><span class="sxs-lookup"><span data-stu-id="a081c-153">The default value is 10 minutes.</span></span>
<span data-ttu-id="a081c-154">Als de computer niet inactief is voor de opgegeven duur voordat de waarde van *IdleTimeout* verloopt, wordt de geplande taak niet uitgevoerd tot de volgende geplande tijd, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="a081c-154">If the computer is not idle for the specified duration before the value of *IdleTimeout* expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="a081c-155">Voer een **time span** -object in, zoals het nummer dat is gegenereerd door de New-TimeSpan cmdlet of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format die automatisch wordt geconverteerd naar een **time span** -object.</span><span class="sxs-lookup"><span data-stu-id="a081c-155">Enter a **TimeSpan** object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format  that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="a081c-156">Als u deze waarde wilt inschakelen, gebruikt u de para meter *StartIfIdle* .</span><span class="sxs-lookup"><span data-stu-id="a081c-156">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="a081c-157">De eigenschap StartIfNotIdle van geplande taken is standaard ingesteld op $True en Windows Power shell negeert de waarden voor *IdleDuration* en *IdleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="a081c-157">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="a081c-158">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="a081c-158">-IdleTimeout</span></span>
<span data-ttu-id="a081c-159">Hiermee geeft u op hoe lang de geplande taak wacht om de computer inactief te maken.</span><span class="sxs-lookup"><span data-stu-id="a081c-159">Specifies how long the scheduled job waits for the computer to be idle.</span></span>
<span data-ttu-id="a081c-160">Als deze time-out verloopt voordat de computer inactief blijft gedurende de periode die is opgegeven door de para meter *IdleDuration* , wordt de taak niet uitgevoerd tot de volgende geplande tijd, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="a081c-160">If this timeout expires before the computer remains idle for the time period that is specified by the *IdleDuration* parameter, the job does not run until the next scheduled time, if any.</span></span>
<span data-ttu-id="a081c-161">De standaard waarde is een uur.</span><span class="sxs-lookup"><span data-stu-id="a081c-161">The default value is one hour.</span></span>

<span data-ttu-id="a081c-162">Voer een **time span** -object in, zoals het nummer dat is gegenereerd door de New-TimeSpan cmdlet of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format die automatisch wordt geconverteerd naar een **time span** -object.</span><span class="sxs-lookup"><span data-stu-id="a081c-162">Enter a **TimeSpan** object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="a081c-163">Als u deze waarde wilt inschakelen, gebruikt u de para meter *StartIfIdle* .</span><span class="sxs-lookup"><span data-stu-id="a081c-163">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="a081c-164">De eigenschap StartIfNotIdle van geplande taken is standaard ingesteld op $True en Windows Power shell negeert de waarden voor *IdleDuration* en *IdleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="a081c-164">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="a081c-165">-MultipleInstancePolicy</span><span class="sxs-lookup"><span data-stu-id="a081c-165">-MultipleInstancePolicy</span></span>
<span data-ttu-id="a081c-166">Hiermee wordt bepaald hoe het systeem reageert op een aanvraag om een exemplaar van een geplande taak te starten terwijl een ander exemplaar van de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a081c-166">Determines how the system responds to a request to start an instance of a scheduled job while another instance of the job is running.</span></span>
<span data-ttu-id="a081c-167">De standaard waarde is IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="a081c-167">The default value is IgnoreNew.</span></span>
<span data-ttu-id="a081c-168">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="a081c-168">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a081c-169">IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="a081c-169">IgnoreNew.</span></span>
<span data-ttu-id="a081c-170">Het nieuwe taak exemplaar wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="a081c-170">The new job instance is ignored.</span></span>
- <span data-ttu-id="a081c-171">Daarmee.</span><span class="sxs-lookup"><span data-stu-id="a081c-171">Parallel.</span></span>
<span data-ttu-id="a081c-172">Het nieuwe taak exemplaar wordt onmiddellijk gestart.</span><span class="sxs-lookup"><span data-stu-id="a081c-172">The new job instance starts immediately.</span></span>
- <span data-ttu-id="a081c-173">Wachtrij.</span><span class="sxs-lookup"><span data-stu-id="a081c-173">Queue.</span></span>
<span data-ttu-id="a081c-174">Het nieuwe taak exemplaar wordt gestart zodra het huidige exemplaar is voltooid.</span><span class="sxs-lookup"><span data-stu-id="a081c-174">The new job instance starts as soon as the current instance completes.</span></span>
- <span data-ttu-id="a081c-175">StopExisting.</span><span class="sxs-lookup"><span data-stu-id="a081c-175">StopExisting.</span></span>
<span data-ttu-id="a081c-176">Het huidige exemplaar van de taak wordt gestopt en het nieuwe exemplaar wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="a081c-176">The current instance of the job stops and the new instance starts.</span></span>

<span data-ttu-id="a081c-177">Als u de taak wilt uitvoeren, moeten aan alle voor waarden voor de taak planning worden voldaan.</span><span class="sxs-lookup"><span data-stu-id="a081c-177">To run the job, all conditions for the job schedule must be met.</span></span>
<span data-ttu-id="a081c-178">Als de voor waarden die zijn ingesteld door de para meters *RequireNetwork* , *IdleDuration* en *IdleTimeout* niet worden vervuld, wordt het taak exemplaar niet gestart, ongeacht de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="a081c-178">For example, if the conditions that are set by the *RequireNetwork* , *IdleDuration* , and *IdleTimeout* parameters are not satisfied, the job instance is not started, regardless of the value of this parameter.</span></span>

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

### <span data-ttu-id="a081c-179">-RequireNetwork</span><span class="sxs-lookup"><span data-stu-id="a081c-179">-RequireNetwork</span></span>
<span data-ttu-id="a081c-180">De geplande taak wordt alleen uitgevoerd als er netwerk verbindingen beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="a081c-180">Runs the scheduled job only when network connections are available.</span></span>

<span data-ttu-id="a081c-181">Als u deze para meter opgeeft en het netwerk is niet beschikbaar op de geplande begin tijd, wordt de taak niet uitgevoerd tot de volgende geplande begin tijd, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="a081c-181">If you specify this parameter and the network is not available at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="a081c-182">Met de para meter *RequireNetwork* wordt de waarde van de eigenschap RunWithoutNetwork van geplande taken ingesteld op $false.</span><span class="sxs-lookup"><span data-stu-id="a081c-182">The *RequireNetwork* parameter sets the value of the RunWithoutNetwork property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="a081c-183">-RestartOnIdleResume</span><span class="sxs-lookup"><span data-stu-id="a081c-183">-RestartOnIdleResume</span></span>
<span data-ttu-id="a081c-184">Hiermee wordt een geplande taak opnieuw gestart wanneer de computer inactief wordt.</span><span class="sxs-lookup"><span data-stu-id="a081c-184">Restarts a scheduled job when the computer becomes idle.</span></span>
<span data-ttu-id="a081c-185">Deze para meter werkt met de para meter *StopIfGoingOffIdle* , die een actieve geplande taak onderbreekt als de computer actief wordt (de niet-actieve status blijft).</span><span class="sxs-lookup"><span data-stu-id="a081c-185">This parameter works with the *StopIfGoingOffIdle* parameter, which suspends a running scheduled job if the computer becomes active (leaves the idle state).</span></span>

<span data-ttu-id="a081c-186">Met de para meter *RestartOnIdleResume* wordt de waarde van de eigenschap RestartOnIdleResume van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="a081c-186">The *RestartOnIdleResume* parameter sets the value of the RestartOnIdleResume property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="a081c-187">-RunElevated</span><span class="sxs-lookup"><span data-stu-id="a081c-187">-RunElevated</span></span>
<span data-ttu-id="a081c-188">De geplande taak wordt uitgevoerd met de machtigingen van een lid van de groep Administrators op de computer waarop de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a081c-188">Runs the scheduled job with the permissions of a member of the Administrators group on the computer on which the job runs.</span></span>

<span data-ttu-id="a081c-189">Als u wilt dat een geplande taak wordt uitgevoerd met beheerders machtigingen, gebruikt u de para meter *Credential* van Register-ScheduledJob om expliciete referenties voor de taak op te geven.</span><span class="sxs-lookup"><span data-stu-id="a081c-189">To enable a scheduled job to run with Administrator permissions, use the *Credential* parameter of Register-ScheduledJob to provide explicit credential for the job.</span></span>

<span data-ttu-id="a081c-190">Met de para meter *RunElevated* wordt de waarde van de eigenschap RunElevated van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="a081c-190">The *RunElevated* parameter sets the value of the RunElevated property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="a081c-191">-StartIfIdle</span><span class="sxs-lookup"><span data-stu-id="a081c-191">-StartIfIdle</span></span>
<span data-ttu-id="a081c-192">Start de geplande taak als de computer niet actief is geweest gedurende de tijd die is opgegeven door de para meter *IdleDuration* voordat de tijd die is opgegeven door de para meter *IdleTimeout* is verlopen.</span><span class="sxs-lookup"><span data-stu-id="a081c-192">Starts the scheduled job if the computer has been idle for the time specified by the *IdleDuration* parameter before the time specified by the *IdleTimeout* parameter expires.</span></span>

<span data-ttu-id="a081c-193">Standaard worden de para meters *IdleDuration* en *IdleTimeout* genegeerd en wordt de taak gestart op de geplande begin tijd, zelfs als de computer bezet is.</span><span class="sxs-lookup"><span data-stu-id="a081c-193">By default, the *IdleDuration* and *IdleTimeout* parameters are ignored and the job starts at the scheduled start time even if the computer is busy.</span></span>

<span data-ttu-id="a081c-194">Als u deze para meter opgeeft en de computer bezet is (niet inactief) op de geplande begin tijd, wordt de taak niet uitgevoerd tot de volgende geplande begin tijd, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="a081c-194">If you specify this parameter and the computer is busy (not idle) at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="a081c-195">Met de para meter *StartIfIdle* wordt de waarde van de eigenschap StartIfNotIdle van geplande taken ingesteld op $false.</span><span class="sxs-lookup"><span data-stu-id="a081c-195">The *StartIfIdle* parameter sets the value of the StartIfNotIdle property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="a081c-196">-StartIfOnBattery</span><span class="sxs-lookup"><span data-stu-id="a081c-196">-StartIfOnBattery</span></span>
<span data-ttu-id="a081c-197">Hiermee wordt de geplande taak gestart, zelfs als de computer op de geplande begin tijd op de accu werkt.</span><span class="sxs-lookup"><span data-stu-id="a081c-197">Starts the scheduled job even if the computer is running on batteries at the scheduled start time.</span></span>
<span data-ttu-id="a081c-198">De standaard waarde is $False.</span><span class="sxs-lookup"><span data-stu-id="a081c-198">The default value is $False.</span></span>

<span data-ttu-id="a081c-199">Met de para meter *StartIfOnBattery* wordt de waarde van de eigenschap StartIfOnBatteries van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="a081c-199">The *StartIfOnBattery* parameter sets the value of the StartIfOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="a081c-200">-StopIfGoingOffIdle</span><span class="sxs-lookup"><span data-stu-id="a081c-200">-StopIfGoingOffIdle</span></span>
<span data-ttu-id="a081c-201">Hiermee wordt een actieve geplande taak onderbroken als de computer actief wordt (niet-inactief) terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a081c-201">Suspends a running scheduled job if the computer becomes active (not idle) while the job is running.</span></span>

<span data-ttu-id="a081c-202">Standaard wordt een geplande taak die wordt onderbroken wanneer de computer actief wordt hervat wanneer de computer weer actief wordt.</span><span class="sxs-lookup"><span data-stu-id="a081c-202">By default, a scheduled job that is suspended when the computer becomes active resumes when the computer becomes idle again.</span></span>
<span data-ttu-id="a081c-203">Als u dit standaard gedrag wilt wijzigen, gebruikt u de para meter *RestartOnIdleResume* .</span><span class="sxs-lookup"><span data-stu-id="a081c-203">To change this default behavior, use the *RestartOnIdleResume* parameter.</span></span>

<span data-ttu-id="a081c-204">Met de para meter *StopIfGoingOffIdle* wordt de waarde van de eigenschap StopIfGoingOffIdle van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="a081c-204">The *StopIfGoingOffIdle* parameter sets the value of the StopIfGoingOffIdle property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="a081c-205">-WakeToRun</span><span class="sxs-lookup"><span data-stu-id="a081c-205">-WakeToRun</span></span>
<span data-ttu-id="a081c-206">De computer uit de slaap stand of sluimer stand halen op de geplande begin tijd zodat de taak kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a081c-206">Wakes the computer from a Hibernate or Sleep state at the scheduled start time so it can run the job.</span></span>
<span data-ttu-id="a081c-207">Als de computer zich standaard in de sluimer stand of slaap stand bevindt op de geplande begin tijd, wordt de taak niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a081c-207">By default, if the computer is in a Hibernate or Sleep state at the scheduled start time, the job does not run.</span></span>

<span data-ttu-id="a081c-208">Met de para meter *WakeToRun* wordt de waarde van de eigenschap WakeToRun van geplande taken ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="a081c-208">The *WakeToRun* parameter sets the value of the WakeToRun property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="a081c-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a081c-209">CommonParameters</span></span>
<span data-ttu-id="a081c-210">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a081c-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a081c-211">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a081c-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a081c-212">INVOER</span><span class="sxs-lookup"><span data-stu-id="a081c-212">INPUTS</span></span>

### <span data-ttu-id="a081c-213">Geen</span><span class="sxs-lookup"><span data-stu-id="a081c-213">None</span></span>
<span data-ttu-id="a081c-214">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a081c-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a081c-215">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a081c-215">OUTPUTS</span></span>

### <span data-ttu-id="a081c-216">Micro soft. Power shell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="a081c-216">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>

## <span data-ttu-id="a081c-217">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a081c-217">NOTES</span></span>

* <span data-ttu-id="a081c-218">U kunt het **ScheduledJobOptions** -object gebruiken dat **New-ScheduledJobOption** maakt als de waarde van de para meter *ScheduledJobOption* van de cmdlet Register-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="a081c-218">You can use the **ScheduledJobOptions** object that **New-ScheduledJobOption** creates as the value of the *ScheduledJobOption* parameter of the Register-ScheduledJob cmdlet.</span></span> <span data-ttu-id="a081c-219">De para meter *ScheduledJobOption* kan echter ook een hash-tabel waarde maken die de eigenschappen van het **ScheduledJobOptions** -object en hun waarden opgeeft, zoals:</span><span class="sxs-lookup"><span data-stu-id="a081c-219">However, the *ScheduledJobOption* parameter can also take a hash table value that specifies the properties of the **ScheduledJobOptions** object and their values, such as:</span></span>

  `@{ShowInTaskScheduler=$False; RunElevated=$True; IdleDuration="00:05"}`

## <span data-ttu-id="a081c-220">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a081c-220">RELATED LINKS</span></span>

[<span data-ttu-id="a081c-221">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a081c-221">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="a081c-222">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a081c-222">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="a081c-223">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a081c-223">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="a081c-224">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a081c-224">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="a081c-225">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a081c-225">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="a081c-226">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a081c-226">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="a081c-227">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a081c-227">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="a081c-228">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="a081c-228">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="a081c-229">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a081c-229">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="a081c-230">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="a081c-230">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="a081c-231">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a081c-231">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="a081c-232">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a081c-232">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="a081c-233">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a081c-233">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="a081c-234">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a081c-234">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="a081c-235">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="a081c-235">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="a081c-236">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a081c-236">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
