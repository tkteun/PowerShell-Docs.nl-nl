---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-JobTrigger
ms.openlocfilehash: de49ab937c6f3a8187f5aecd6aafc81425b8cd00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250303"
---
# <span data-ttu-id="15ccc-103">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15ccc-103">New-JobTrigger</span></span>

## <span data-ttu-id="15ccc-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="15ccc-104">SYNOPSIS</span></span>
<span data-ttu-id="15ccc-105">Hiermee maakt u een taak trigger voor een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="15ccc-105">Creates a job trigger for a scheduled job.</span></span>

## <span data-ttu-id="15ccc-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="15ccc-106">SYNTAX</span></span>

### <span data-ttu-id="15ccc-107">Eenmaal (standaard)</span><span class="sxs-lookup"><span data-stu-id="15ccc-107">Once (Default)</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] -At <DateTime> [-Once] [-RepetitionInterval <TimeSpan>]
 [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely] [<CommonParameters>]
```

### <span data-ttu-id="15ccc-108">Dagelijks</span><span class="sxs-lookup"><span data-stu-id="15ccc-108">Daily</span></span>

```
New-JobTrigger [-DaysInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> [-Daily] [<CommonParameters>]
```

### <span data-ttu-id="15ccc-109">Wekelijks</span><span class="sxs-lookup"><span data-stu-id="15ccc-109">Weekly</span></span>

```
New-JobTrigger [-WeeksInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> -DaysOfWeek <DayOfWeek[]>
 [-Weekly] [<CommonParameters>]
```

### <span data-ttu-id="15ccc-110">AtStartup</span><span class="sxs-lookup"><span data-stu-id="15ccc-110">AtStartup</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-AtStartup] [<CommonParameters>]
```

### <span data-ttu-id="15ccc-111">AtLogon</span><span class="sxs-lookup"><span data-stu-id="15ccc-111">AtLogon</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-User <String>] [-AtLogOn] [<CommonParameters>]
```

## <span data-ttu-id="15ccc-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="15ccc-112">DESCRIPTION</span></span>
<span data-ttu-id="15ccc-113">Met de cmdlet **New-JobTrigger** wordt een taak trigger gemaakt waarmee een geplande taak wordt gestart in een eenmalige of terugkerende planning, of wanneer er een gebeurtenis optreedt.</span><span class="sxs-lookup"><span data-stu-id="15ccc-113">The **New-JobTrigger** cmdlet creates a job trigger that starts a scheduled job on a one-time or recurring schedule, or when an event occurs.</span></span>

<span data-ttu-id="15ccc-114">U kunt het **ScheduledJobTrigger** -object gebruiken dat **New-JobTrigger** retourneert om een taak trigger in te stellen voor een nieuwe of bestaande geplande taak.</span><span class="sxs-lookup"><span data-stu-id="15ccc-114">You can use the **ScheduledJobTrigger** object that **New-JobTrigger** returns to set a job trigger for a new or existing scheduled job.</span></span>
<span data-ttu-id="15ccc-115">U kunt ook een taak trigger maken met behulp van de cmdlet Get-JobTrigger om de taak trigger van een bestaande geplande taak te verkrijgen of door een hash-tabel waarde te gebruiken om een taak trigger weer te geven.</span><span class="sxs-lookup"><span data-stu-id="15ccc-115">You can also create a job trigger by using the Get-JobTrigger cmdlet to get the job trigger of an existing scheduled job, or by using a hash table value to represent a job trigger.</span></span>

<span data-ttu-id="15ccc-116">Wanneer u een taak trigger maakt, controleert u de standaard waarden van de opties die zijn opgegeven door de New-ScheduledJobOption-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15ccc-116">When creating a job trigger, review the default values of the options specified by the New-ScheduledJobOption cmdlet.</span></span>
<span data-ttu-id="15ccc-117">Deze opties, die dezelfde geldige en standaard waarden hebben als de overeenkomstige opties in **taak planner** , beïnvloeden de planning en timing van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="15ccc-117">These options, which have the same valid and default values as the corresponding options in **Task Scheduler** , affect the scheduling and timing of scheduled jobs.</span></span>

<span data-ttu-id="15ccc-118">**New-JobTrigger** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="15ccc-118">**New-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="15ccc-119">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="15ccc-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="15ccc-120">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="15ccc-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="15ccc-121">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="15ccc-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="15ccc-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="15ccc-122">EXAMPLES</span></span>

### <span data-ttu-id="15ccc-123">Voor beeld 1: eenmaal plannen</span><span class="sxs-lookup"><span data-stu-id="15ccc-123">Example 1: Once Schedule</span></span>

```
PS C:\> New-JobTrigger -Once -At "1/20/2012 3:00 AM"
```

<span data-ttu-id="15ccc-124">Met deze opdracht wordt de cmdlet **New-JobTrigger** gebruikt om een taak trigger te maken waarmee slechts één keer een geplande taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="15ccc-124">This command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a scheduled job only one time.</span></span>
<span data-ttu-id="15ccc-125">De waarde van de *at* -para meter is een teken reeks die door Windows Power shell wordt geconverteerd naar een **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="15ccc-125">The value of the *At* parameter is a string that Windows PowerShell converts into a **DateTime** object.</span></span>
<span data-ttu-id="15ccc-126">De waarde *van de at* -para meter bevat een expliciete datum, niet alleen een tijd.</span><span class="sxs-lookup"><span data-stu-id="15ccc-126">The *At* parameter value includes an explicit date, not just a time.</span></span>
<span data-ttu-id="15ccc-127">Als de datum is wegge laten, wordt de trigger gemaakt met de huidige datum en 3:00 AM-tijd, die waarschijnlijk een tijd in het verleden aangeeft.</span><span class="sxs-lookup"><span data-stu-id="15ccc-127">If the date were omitted, the trigger would be created with the current date and 3:00 AM time, which is likely to represent a time in the past.</span></span>

### <span data-ttu-id="15ccc-128">Voor beeld 2: dagelijks plannen</span><span class="sxs-lookup"><span data-stu-id="15ccc-128">Example 2: Daily Schedule</span></span>

```
PS C:\> New-JobTrigger -Daily -At "4:15 AM" -DaysInterval 3
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/21/2012 4:15:00 AM                           True
```

<span data-ttu-id="15ccc-129">Met deze opdracht wordt een taak trigger gemaakt waarmee elke 3 dagen om 4:15 uur een geplande taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="15ccc-129">This command creates a job trigger that starts a scheduled job every 3 days at 4:15 a.m.</span></span>

<span data-ttu-id="15ccc-130">Omdat de waarde van de para meter *at* geen datum bevat, wordt de huidige datum gebruikt als datum waarde in het **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="15ccc-130">Because the value of the *At* parameter does not include a date, the current date is used as the date value in the **DateTime** object.</span></span>
<span data-ttu-id="15ccc-131">Als de datum en tijd zich in het verleden bevindt, wordt de geplande taak gestart bij de volgende instantie, die 3 dagen later van de waarde *bij* para meter is.</span><span class="sxs-lookup"><span data-stu-id="15ccc-131">If the date and time is in the past, the scheduled job is started at the next occurrence, which is 3 days later from the *At* parameter value.</span></span>

### <span data-ttu-id="15ccc-132">Voor beeld 3: wekelijks schema</span><span class="sxs-lookup"><span data-stu-id="15ccc-132">Example 3: Weekly Schedule</span></span>

```
PS C:\> New-JobTrigger -Weekly -DaysOfWeek Monday, Wednesday, Friday -At "23:00" -WeeksInterval 4
Id Frequency Time                  DaysOfWeek                  Enabled
-- --------- ----                  ----------                  -------
0  Weekly    9/21/2012 11:00:00 PM {Monday, Wednesday, Friday} True
```

<span data-ttu-id="15ccc-133">Met deze opdracht wordt een taak trigger gemaakt waarmee elke 4 weken op maandag, woensdag en vrijdag om 2300 uur (11:00 PM) een geplande taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="15ccc-133">This command creates a job trigger that starts a scheduled job every 4 weeks on Monday, Wednesday, and Friday at 2300 hours (11:00 PM).</span></span>

<span data-ttu-id="15ccc-134">U kunt ook de waarde van de para meter *DaysOfWeek* invoeren in gehele getallen, zoals `-DaysOfWeek 1, 5` .</span><span class="sxs-lookup"><span data-stu-id="15ccc-134">You can also enter the *DaysOfWeek* parameter value in integers, such as `-DaysOfWeek 1, 5`.</span></span>

### <span data-ttu-id="15ccc-135">Voor beeld 4: aanmeldings schema</span><span class="sxs-lookup"><span data-stu-id="15ccc-135">Example 4: Logon Schedule</span></span>

```
PS C:\> New-JobTrigger -AtLogOn -User Domain01\Admin01
```

<span data-ttu-id="15ccc-136">Met deze opdracht wordt een taak trigger gemaakt waarmee een geplande taak wordt gestart wanneer de domein beheerder zich bij de computer aanmeldt.</span><span class="sxs-lookup"><span data-stu-id="15ccc-136">This command creates a job trigger that starts a scheduled job whenever the domain administrator logs onto the computer.</span></span>

### <span data-ttu-id="15ccc-137">Voor beeld 5: een wille keurige vertraging gebruiken</span><span class="sxs-lookup"><span data-stu-id="15ccc-137">Example 5: Using a Random Delay</span></span>

```
PS C:\> New-JobTrigger -Daily -At 1:00 -RandomDelay 00:20:00
```

<span data-ttu-id="15ccc-138">Met deze opdracht wordt een taak trigger gemaakt waarmee elke dag om 1:00 's morgen een geplande taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="15ccc-138">This command creates a job trigger that starts a scheduled job every day at 1:00 in the morning.</span></span>
<span data-ttu-id="15ccc-139">De opdracht gebruikt de para meter *RandomDelay* om de maximale vertraging in te stellen op 20 minuten.</span><span class="sxs-lookup"><span data-stu-id="15ccc-139">The command uses the *RandomDelay* parameter to set the maximum delay to 20 minutes.</span></span>
<span data-ttu-id="15ccc-140">Als gevolg hiervan wordt de taak elke dag uitgevoerd tussen 1:00 uur en 1:20 uur, met het interval waarbij pseudo-wille keurig wordt gevarieerd.</span><span class="sxs-lookup"><span data-stu-id="15ccc-140">As a result, the job runs every day between 1:00 AM and 1:20 AM, with the interval varying pseudo-randomly.</span></span>

<span data-ttu-id="15ccc-141">U kunt een wille keurige vertraging gebruiken voor steek proeven, taak verdeling en andere beheer taken.</span><span class="sxs-lookup"><span data-stu-id="15ccc-141">You can use a random delay for sampling, load balancing, and other administrative tasks.</span></span>
<span data-ttu-id="15ccc-142">Wanneer u de vertragings waarde instelt, controleert u de ingangs-en standaard waarden van de cmdlet New-ScheduledJobOption en coördineert u de vertraging met de optie-instellingen.</span><span class="sxs-lookup"><span data-stu-id="15ccc-142">When setting the delay value, review the effective and default values of the New-ScheduledJobOption cmdlet and coordinate the delay with the option settings.</span></span>

### <span data-ttu-id="15ccc-143">Voor beeld 6: een taak trigger maken voor een nieuwe geplande taak</span><span class="sxs-lookup"><span data-stu-id="15ccc-143">Example 6: Create a Job Trigger for a New Scheduled Job</span></span>

```
The first command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The command saves the job trigger in the $T variable.
PS C:\> $T = New-JobTrigger -Weekly -DaysOfWeek 1,3,5 -At 12:01AM


The second command uses the Register-ScheduledJob cmdlet to create a scheduled job that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The value of the *Trigger* parameter is the trigger that is stored in the $T variable.
PS C:\> Register-ScheduledJob -Name Test-HelpFiles -FilePath C:\Scripts\Test-HelpFiles.ps1 -Trigger $T
```

<span data-ttu-id="15ccc-144">Deze opdrachten gebruiken een taak trigger om een nieuwe geplande taak te maken.</span><span class="sxs-lookup"><span data-stu-id="15ccc-144">These commands use a job trigger to create a new scheduled job.</span></span>

### <span data-ttu-id="15ccc-145">Voor beeld 7: een taak trigger toevoegen aan een geplande taak</span><span class="sxs-lookup"><span data-stu-id="15ccc-145">Example 7: Add a Job Trigger to a Scheduled Job</span></span>

```
PS C:\> Add-JobTrigger -Name SynchronizeApps -Trigger (New-JobTrigger -Daily -At 3:10AM)
```

<span data-ttu-id="15ccc-146">In dit voor beeld ziet u hoe u een taak trigger toevoegt aan een bestaande geplande taak.</span><span class="sxs-lookup"><span data-stu-id="15ccc-146">This example shows how to add a job trigger to an existing scheduled job.</span></span>
<span data-ttu-id="15ccc-147">U kunt meerdere taak triggers toevoegen aan een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="15ccc-147">You can add multiple job triggers to any scheduled job.</span></span>

<span data-ttu-id="15ccc-148">De opdracht gebruikt de cmdlet Add-JobTrigger om de taak trigger toe te voegen aan de geplande taak SynchronizeApps.</span><span class="sxs-lookup"><span data-stu-id="15ccc-148">The command uses the Add-JobTrigger cmdlet to add the job trigger to the SynchronizeApps scheduled job.</span></span>
<span data-ttu-id="15ccc-149">De waarde van de *trigger* parameter is een **nieuwe JobTrigger** opdracht waarmee de taak elke dag om 3:10 uur wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="15ccc-149">The value of the *Trigger* parameter is a **New-JobTrigger** command that runs the job every day at 3:10 AM.</span></span>

<span data-ttu-id="15ccc-150">Wanneer de opdracht is voltooid, is SynchronizeApps een geplande taak die wordt uitgevoerd op het tijdstip dat is opgegeven door de taak trigger.</span><span class="sxs-lookup"><span data-stu-id="15ccc-150">When the command completes, SynchronizeApps is a scheduled job that runs at the times specified by the job trigger.</span></span>

### <span data-ttu-id="15ccc-151">Voor beeld 8: een herhalende taak trigger maken</span><span class="sxs-lookup"><span data-stu-id="15ccc-151">Example 8: Create a repeating job trigger</span></span>

```
PS C:\> New-JobTrigger -Once -At "09/12/2013 1:00:00" -RepetitionInterval (New-TimeSpan -Hours 1) -RepetitionDuration (New-Timespan -Hours 48)
```

<span data-ttu-id="15ccc-152">Met deze opdracht wordt een taak trigger gemaakt waarmee elke 60 minuten voor 48 uur vanaf 12 september 2013 op 1:00 AM een taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="15ccc-152">This command creates a job trigger that runs a job every 60 minutes for 48 hours beginning on September 12, 2013 at 1:00 AM.</span></span>

### <span data-ttu-id="15ccc-153">Voor beeld 9: een herhaalde taak trigger stoppen</span><span class="sxs-lookup"><span data-stu-id="15ccc-153">Example 9: Stop a repeating job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name SecurityCheck | Set-JobTrigger -RepetitionInterval 0:00 -RepetitionDuration 0:00
```

<span data-ttu-id="15ccc-154">Met deze opdracht wordt de SecurityCheck-taak geforceerd gestopt, die wordt geactiveerd om elke 60 minuten uit te voeren totdat de taak trigger verloopt.</span><span class="sxs-lookup"><span data-stu-id="15ccc-154">This command forcibly stops the SecurityCheck job, which is triggered to run every 60 minutes until its job trigger expires.</span></span>

<span data-ttu-id="15ccc-155">Om te voor komen dat de taak wordt herhaald, gebruikt de opdracht de Get-JobTrigger om de taak trigger van de SecurityCheck-taak te verkrijgen en de Set-JobTrigger-cmdlet om het herhalings interval en de duur van de herhaling van de taak trigger te wijzigen in nul (0).</span><span class="sxs-lookup"><span data-stu-id="15ccc-155">To prevent the job from repeating, the command uses the Get-JobTrigger to get the job trigger of the SecurityCheck job and the Set-JobTrigger cmdlet to change the repetition interval and repetition duration of the job trigger to zero (0).</span></span>

### <span data-ttu-id="15ccc-156">Voor beeld 10: een taak trigger per uur maken</span><span class="sxs-lookup"><span data-stu-id="15ccc-156">Example 10: Create an hourly job trigger</span></span>

```
PS C:\> New-JobTrigger -Once -At "9/21/2012 0am" -RepetitionInterval (New-TimeSpan -Hour 12) -RepetitionDuration ([TimeSpan]::MaxValue)
```

<span data-ttu-id="15ccc-157">Met de volgende opdracht maakt u een taak trigger die elke 12 uur een geplande taak uitvoert voor een onbepaalde periode.</span><span class="sxs-lookup"><span data-stu-id="15ccc-157">The following command creates a job trigger that runs a scheduled job once every 12 hours for an indefinite period of time.</span></span>
<span data-ttu-id="15ccc-158">De planning begint morgen (9/21/2012) om middernacht (0:00 uur).</span><span class="sxs-lookup"><span data-stu-id="15ccc-158">The schedule begins tomorrow (9/21/2012) at midnight (0:00 AM).</span></span>

## <span data-ttu-id="15ccc-159">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="15ccc-159">PARAMETERS</span></span>

### <span data-ttu-id="15ccc-160">-At</span><span class="sxs-lookup"><span data-stu-id="15ccc-160">-At</span></span>
<span data-ttu-id="15ccc-161">De taak wordt gestart op de opgegeven datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="15ccc-161">Starts the job at the specified date and time.</span></span>
<span data-ttu-id="15ccc-162">Voer een **DateTime** -object in, zoals een teken reeks die wordt geretourneerd door de cmdlet Get-Date, of een String die kan worden geconverteerd naar een datum en tijd, zoals ' 19 April 2012 15:00 ', ' 12/31 ' of ' 3am '.</span><span class="sxs-lookup"><span data-stu-id="15ccc-162">Enter a **DateTime** object, such as one that the Get-Date cmdlet returns, or a string that can be converted to a date and time, such as "April 19, 2012 15:00", "12/31", or "3am".</span></span>
<span data-ttu-id="15ccc-163">Als u geen element van de datum opgeeft, zoals het jaar, heeft de datum in de trigger het bijbehorende element van de huidige datum.</span><span class="sxs-lookup"><span data-stu-id="15ccc-163">If you don't specify an element of the date, such as the year, the date in the trigger has the corresponding element from the current date.</span></span>

<span data-ttu-id="15ccc-164">Wanneer u de para meter *Once* gebruikt, stelt u de waarde van de para meter *in* op een datum en tijd in de toekomst.</span><span class="sxs-lookup"><span data-stu-id="15ccc-164">When using the *Once* parameter, set the value of the *At* parameter to a future date and time.</span></span>
<span data-ttu-id="15ccc-165">Omdat de standaard datum in een **DateTime** -object de huidige datum is, als u een tijd opgeeft vóór de huidige tijd zonder een expliciete datum, wordt de taak trigger voor een tijd in het verleden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="15ccc-165">Because the default date in a **DateTime** object is the current date, if you specify a time before the current time without an explicit date, the job trigger is created for a time in the past.</span></span>

<span data-ttu-id="15ccc-166">**DateTime** -objecten en teken reeksen die worden geconverteerd naar **DateTime** -objecten, worden automatisch aangepast zodat ze compatibel zijn met de datum-en tijd notaties die zijn geselecteerd voor de lokale computer in de regio en taal in het configuratie scherm.</span><span class="sxs-lookup"><span data-stu-id="15ccc-166">**DateTime** objects, and strings that are converted to **DateTime** objects, are automatically adjusted to be compatible with the date and time formats selected for the local computer in Region and Language in Control Panel.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Once, Daily, Weekly
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-167">-AtLogOn</span><span class="sxs-lookup"><span data-stu-id="15ccc-167">-AtLogOn</span></span>
<span data-ttu-id="15ccc-168">Hiermee wordt de geplande taak gestart wanneer de opgegeven gebruikers zich aanmelden bij de computer.</span><span class="sxs-lookup"><span data-stu-id="15ccc-168">Starts the scheduled job when the specified users log on to the computer.</span></span>
<span data-ttu-id="15ccc-169">Als u een gebruiker wilt opgeven, gebruikt u de para meter *User* .</span><span class="sxs-lookup"><span data-stu-id="15ccc-169">To specify a user, use the *User* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtLogon
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-170">-AtStartup</span><span class="sxs-lookup"><span data-stu-id="15ccc-170">-AtStartup</span></span>
<span data-ttu-id="15ccc-171">De geplande taak wordt gestart wanneer Windows wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="15ccc-171">Starts the scheduled job when Windows starts.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtStartup
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-172">-Dagelijks</span><span class="sxs-lookup"><span data-stu-id="15ccc-172">-Daily</span></span>
<span data-ttu-id="15ccc-173">Geeft een terugkerende dagelijkse taak planning op.</span><span class="sxs-lookup"><span data-stu-id="15ccc-173">Specifies a recurring daily job schedule.</span></span>
<span data-ttu-id="15ccc-174">Gebruik de andere para meters in de para meter *dagelijks* instellen om de details van de planning op te geven.</span><span class="sxs-lookup"><span data-stu-id="15ccc-174">Use the other parameters in the *Daily* parameter set to specify the schedule details.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Daily
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-175">-DaysInterval</span><span class="sxs-lookup"><span data-stu-id="15ccc-175">-DaysInterval</span></span>
<span data-ttu-id="15ccc-176">Hiermee geeft u het aantal dagen op dat in een dagelijks schema voor komt.</span><span class="sxs-lookup"><span data-stu-id="15ccc-176">Specifies the number of days between occurrences on a daily schedule.</span></span>
<span data-ttu-id="15ccc-177">Een waarde van 3 begint bijvoorbeeld met de geplande taak op dagen 1, 4, 7, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="15ccc-177">For example, a value of 3 starts the scheduled job on days 1, 4, 7 and so on.</span></span>
<span data-ttu-id="15ccc-178">De standaardwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="15ccc-178">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Daily
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-179">-DaysOfWeek</span><span class="sxs-lookup"><span data-stu-id="15ccc-179">-DaysOfWeek</span></span>
<span data-ttu-id="15ccc-180">Hiermee geeft u de dagen van de week op waarop een wekelijkse geplande taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="15ccc-180">Specifies the days of the week on which a weekly scheduled job runs.</span></span>
<span data-ttu-id="15ccc-181">Voer namen van dagen in, zoals "maandag" of gehele getallen van 0-6, waarbij 0 staat voor zondag.</span><span class="sxs-lookup"><span data-stu-id="15ccc-181">Enter day names, such as "Monday" or integers 0-6, where 0 represents Sunday.</span></span>
<span data-ttu-id="15ccc-182">Deze para meter is vereist in de set met wekelijkse para meters.</span><span class="sxs-lookup"><span data-stu-id="15ccc-182">This parameter is required in the Weekly parameter set.</span></span>

<span data-ttu-id="15ccc-183">De namen van dagen worden geconverteerd naar hun gehele waarden in de taak trigger.</span><span class="sxs-lookup"><span data-stu-id="15ccc-183">Day names are converted to their integer values in the job trigger.</span></span>
<span data-ttu-id="15ccc-184">Wanneer u namen van dagen tussen aanhalings tekens in een opdracht plaatst, plaatst u de naam van elke dag in afzonderlijke aanhalings tekens, zoals "maandag", "dinsdag".</span><span class="sxs-lookup"><span data-stu-id="15ccc-184">When you enclose day names in quotation marks in a command, enclose each day name in separate quotation marks, such as "Monday", "Tuesday".</span></span>
<span data-ttu-id="15ccc-185">Als u meerdere namen van dagen in een enkel aanhalings teken plaatst, worden de bijbehorende waarden voor gehele getallen opgeteld.</span><span class="sxs-lookup"><span data-stu-id="15ccc-185">If you enclose multiple day names in a single quotation mark pair, the corresponding integer values are summed.</span></span>
<span data-ttu-id="15ccc-186">Bijvoorbeeld: ' maandag, dinsdag ' (1, 2) resulteert in een waarde van ' woensdag ' (3).</span><span class="sxs-lookup"><span data-stu-id="15ccc-186">For example, "Monday, Tuesday" (1, 2) results in a value of "Wednesday" (3).</span></span>

```yaml
Type: System.DayOfWeek[]
Parameter Sets: Weekly
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-187">-Eenmaal</span><span class="sxs-lookup"><span data-stu-id="15ccc-187">-Once</span></span>
<span data-ttu-id="15ccc-188">Hiermee geeft u een niet-terugkerende (eenmalige) of aangepaste herhalende planning op.</span><span class="sxs-lookup"><span data-stu-id="15ccc-188">Specifies a non-recurring (one time) or custom repeating schedule.</span></span>
<span data-ttu-id="15ccc-189">Als u een herhalings schema wilt maken, gebruikt u de para meter *Once* met de para meters *RepetitionDuration* en *RepetitionInterval* .</span><span class="sxs-lookup"><span data-stu-id="15ccc-189">To create a repeating schedule, use the *Once* parameter with the *RepetitionDuration* and *RepetitionInterval* parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-190">-RandomDelay</span><span class="sxs-lookup"><span data-stu-id="15ccc-190">-RandomDelay</span></span>
<span data-ttu-id="15ccc-191">Hiermee schakelt u een wille keurige vertraging in die begint op de geplande begin tijd en stelt de maximale vertragings waarde in.</span><span class="sxs-lookup"><span data-stu-id="15ccc-191">Enables a random delay that begins at the scheduled start time, and sets the maximum delay value.</span></span>
<span data-ttu-id="15ccc-192">De lengte van de vertraging is ingesteld op wille keurige pseudo voor elk begin en varieert van geen vertraging tot de tijd die is opgegeven door de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="15ccc-192">The length of the delay is set pseudo-randomly for each start and varies from no delay to the time specified by the value of this parameter.</span></span>
<span data-ttu-id="15ccc-193">De standaard waarde, nul (00:00:00), schakelt de wille keurige vertraging uit.</span><span class="sxs-lookup"><span data-stu-id="15ccc-193">The default value, zero (00:00:00), disables the random delay.</span></span>

<span data-ttu-id="15ccc-194">Voer een time span-object in, zoals het resultaat van de cmdlet New-TimeSpan, of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format, die automatisch wordt geconverteerd naar een **time span** -object.</span><span class="sxs-lookup"><span data-stu-id="15ccc-194">Enter a timespan object, such as one returned by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format, which is automatically converted to a **TimeSpan** object.</span></span>

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

### <span data-ttu-id="15ccc-195">-RepeatIndefinitely</span><span class="sxs-lookup"><span data-stu-id="15ccc-195">-RepeatIndefinitely</span></span>
<span data-ttu-id="15ccc-196">Deze para meter, die beschikbaar is in Windows Power Shell 4,0, elimineert de nood zaak om een **time span. MaxValue** -waarde voor de para meter *RepetitionDuration* op te geven om een geplande taak herhaaldelijk uit te voeren voor een onbepaalde periode.</span><span class="sxs-lookup"><span data-stu-id="15ccc-196">This parameter, available starting in Windows PowerShell 4.0, eliminates the necessity of specifying a **TimeSpan.MaxValue** value for the *RepetitionDuration* parameter to run a scheduled job repeatedly, for an indefinite period.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-197">-RepetitionDuration</span><span class="sxs-lookup"><span data-stu-id="15ccc-197">-RepetitionDuration</span></span>
<span data-ttu-id="15ccc-198">Herhaalt de taak totdat de opgegeven tijd verloopt.</span><span class="sxs-lookup"><span data-stu-id="15ccc-198">Repeats the job until the specified time expires.</span></span>
<span data-ttu-id="15ccc-199">De frequentie van de herhaling wordt bepaald door de waarde van de para meter *RepetitionInterval* .</span><span class="sxs-lookup"><span data-stu-id="15ccc-199">The repetition frequency is determined by the value of the *RepetitionInterval* parameter.</span></span>
<span data-ttu-id="15ccc-200">Als de waarde van **RepetitionInterval** bijvoorbeeld 5 minuten is en de waarde van **RepetitionDuration** 2 uur is, wordt de taak gedurende twee uur elke vijf minuten geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="15ccc-200">For example, if the value of **RepetitionInterval** is 5 minutes and the value of **RepetitionDuration** is 2 hours, the job is triggered every five minutes for two hours.</span></span>

<span data-ttu-id="15ccc-201">Voer een time span-object in, zoals een voor het retour neren van de cmdlet New-TimeSpan, of een teken reeks die kan worden geconverteerd naar een time span-object, zoals ' 1:05:30 '.</span><span class="sxs-lookup"><span data-stu-id="15ccc-201">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="15ccc-202">Als u een taak voor onbepaalde tijd wilt uitvoeren, voegt u in plaats daarvan de para meter *RepeatIndefinitely* toe.</span><span class="sxs-lookup"><span data-stu-id="15ccc-202">To run a job indefinitely, add the *RepeatIndefinitely* parameter instead.</span></span>

<span data-ttu-id="15ccc-203">Als u een taak wilt stoppen voordat de herhalings duur van de taak trigger verloopt, gebruikt u de Set-JobTrigger cmdlet om de waarde *RepetitionDuration* in te stellen op nul (0).</span><span class="sxs-lookup"><span data-stu-id="15ccc-203">To stop a job before the job trigger repetition duration expires, use the Set-JobTrigger cmdlet to set the *RepetitionDuration* value to zero (0).</span></span>

<span data-ttu-id="15ccc-204">Deze para meter is alleen geldig wanneer de para meters *eenmaal* , *at* en *RepetitionInterval* worden gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="15ccc-204">This parameter is valid only when the *Once* , *At* and *RepetitionInterval* parameters are used in the command.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-205">-RepetitionInterval</span><span class="sxs-lookup"><span data-stu-id="15ccc-205">-RepetitionInterval</span></span>
<span data-ttu-id="15ccc-206">Hiermee wordt de taak herhaald op het opgegeven tijds interval.</span><span class="sxs-lookup"><span data-stu-id="15ccc-206">Repeats the job at the specified time interval.</span></span>
<span data-ttu-id="15ccc-207">Als de waarde van deze para meter bijvoorbeeld 2 uur is, wordt de taak elke twee uur geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="15ccc-207">For example, if the value of this parameter is 2 hours, the job is triggered every two hours.</span></span>
<span data-ttu-id="15ccc-208">De standaard waarde, 0, herhaalt de taak niet.</span><span class="sxs-lookup"><span data-stu-id="15ccc-208">The default value, 0, does not repeat the job.</span></span>

<span data-ttu-id="15ccc-209">Voer een time span-object in, zoals een voor het retour neren van de cmdlet New-TimeSpan, of een teken reeks die kan worden geconverteerd naar een time span-object, zoals ' 1:05:30 '.</span><span class="sxs-lookup"><span data-stu-id="15ccc-209">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="15ccc-210">Deze para meter is alleen geldig wanneer de *eenmalige* , *at* -en *RepetitionDuration* -para meters worden gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="15ccc-210">This parameter is valid only when the *Once* , *At* , and *RepetitionDuration* parameters are used in the command.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-211">-User</span><span class="sxs-lookup"><span data-stu-id="15ccc-211">-User</span></span>
<span data-ttu-id="15ccc-212">Hiermee geeft u de gebruikers die een geplande taak *AtLogon* starten.</span><span class="sxs-lookup"><span data-stu-id="15ccc-212">Specifies the users who trigger an *AtLogon* start of a scheduled job.</span></span>
<span data-ttu-id="15ccc-213">Voer de naam van een gebruiker in \<UserName\> of in of \<Domain\Username\> Voer een asterisk ( \* ) in om alle gebruikers weer te geven.</span><span class="sxs-lookup"><span data-stu-id="15ccc-213">Enter the name of a user in \<UserName\> or \<Domain\Username\> format or enter an asterisk (\*) to represent all users.</span></span>
<span data-ttu-id="15ccc-214">De standaard waarde is alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="15ccc-214">The default value is all users.</span></span>

```yaml
Type: System.String
Parameter Sets: AtLogon
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-215">-Wekelijks</span><span class="sxs-lookup"><span data-stu-id="15ccc-215">-Weekly</span></span>
<span data-ttu-id="15ccc-216">Hiermee geeft u een terugkerende wekelijkse taak planning op.</span><span class="sxs-lookup"><span data-stu-id="15ccc-216">Specifies a recurring weekly job schedule.</span></span>
<span data-ttu-id="15ccc-217">Gebruik de andere para meters in de set met wekelijkse para meters om de details van de planning op te geven.</span><span class="sxs-lookup"><span data-stu-id="15ccc-217">Use the other parameters in the Weekly parameter set to specify the schedule details.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Weekly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-218">-WeeksInterval</span><span class="sxs-lookup"><span data-stu-id="15ccc-218">-WeeksInterval</span></span>
<span data-ttu-id="15ccc-219">Hiermee geeft u het aantal weken tussen exemplaren op voor een wekelijks taak schema.</span><span class="sxs-lookup"><span data-stu-id="15ccc-219">Specifies the number of weeks between occurrences on a weekly job schedule.</span></span>
<span data-ttu-id="15ccc-220">Een waarde van 3 begint bijvoorbeeld met de geplande taak op weken 1, 4, 7 enzovoort.</span><span class="sxs-lookup"><span data-stu-id="15ccc-220">For example, a value of 3 starts the scheduled job on weeks 1, 4, 7 and so on.</span></span>
<span data-ttu-id="15ccc-221">De standaardwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="15ccc-221">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Weekly
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15ccc-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="15ccc-222">CommonParameters</span></span>
<span data-ttu-id="15ccc-223">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="15ccc-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="15ccc-224">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="15ccc-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="15ccc-225">INVOER</span><span class="sxs-lookup"><span data-stu-id="15ccc-225">INPUTS</span></span>

### <span data-ttu-id="15ccc-226">Geen</span><span class="sxs-lookup"><span data-stu-id="15ccc-226">None</span></span>
<span data-ttu-id="15ccc-227">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15ccc-227">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="15ccc-228">UITVOER</span><span class="sxs-lookup"><span data-stu-id="15ccc-228">OUTPUTS</span></span>

### <span data-ttu-id="15ccc-229">Micro soft. Power shell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="15ccc-229">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>

## <span data-ttu-id="15ccc-230">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="15ccc-230">NOTES</span></span>

* <span data-ttu-id="15ccc-231">Taak triggers worden niet op schijf opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="15ccc-231">Job triggers are not saved to disk.</span></span> <span data-ttu-id="15ccc-232">Geplande taken worden echter op schijf opgeslagen en u kunt de Get-JobTrigger gebruiken om de taak trigger van een geplande taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="15ccc-232">However, scheduled jobs are saved to disk, and you can use the Get-JobTrigger to get the job trigger of any scheduled job.</span></span>
* <span data-ttu-id="15ccc-233">**New-JobTrigger** voor komt niet dat u een taak trigger maakt waarmee geen geplande taak wordt uitgevoerd, zoals eenmalige trigger voor een datum in het verleden.</span><span class="sxs-lookup"><span data-stu-id="15ccc-233">**New-JobTrigger** does not prevent you from creating a job trigger that will not run a scheduled job, such as one-time trigger for a date in the past.</span></span>
* <span data-ttu-id="15ccc-234">De Register-ScheduledJob-cmdlet accepteert een ScheduledJobTrigger-object, zoals het dat wordt geretourneerd door de cmdlets **New-JobTrigger** of Get-JobTrigger, of een hash-tabel met trigger waarden.</span><span class="sxs-lookup"><span data-stu-id="15ccc-234">The Register-ScheduledJob cmdlet accepts a ScheduledJobTrigger object, such as one returned by the **New-JobTrigger** or Get-JobTrigger cmdlets, or a hash table with trigger values.</span></span>

  <span data-ttu-id="15ccc-235">Als u een hash-tabel wilt verzenden, gebruikt u de volgende sleutels.</span><span class="sxs-lookup"><span data-stu-id="15ccc-235">To submit a hash table, use the following keys.</span></span>

  <span data-ttu-id="15ccc-236">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (of een wille keurige geldige tijd reeks); `DaysOfWeek="Monday", "Wednesday"` (of een combi natie van namen van dagen); `Interval=2` (of een geldig frequentie-interval); `RandomDelay="30minutes"` (of een wille keurige geldige time span-teken reeks); `User="Domain1\User01` (of een geldige gebruiker; wordt alleen gebruikt met de *AtLogon* -frequentie waarde)}</span><span class="sxs-lookup"><span data-stu-id="15ccc-236">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (or any valid time string); `DaysOfWeek="Monday", "Wednesday"` (or any combination of day names); `Interval=2` (or any valid frequency interval); `RandomDelay="30minutes"` (or any valid timespan string); `User="Domain1\User01` (or any valid user; used only with the *AtLogon* frequency value) }</span></span>

## <span data-ttu-id="15ccc-237">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="15ccc-237">RELATED LINKS</span></span>

[<span data-ttu-id="15ccc-238">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15ccc-238">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="15ccc-239">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15ccc-239">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="15ccc-240">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15ccc-240">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="15ccc-241">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15ccc-241">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="15ccc-242">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15ccc-242">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="15ccc-243">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15ccc-243">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="15ccc-244">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15ccc-244">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="15ccc-245">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="15ccc-245">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="15ccc-246">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15ccc-246">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="15ccc-247">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="15ccc-247">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="15ccc-248">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15ccc-248">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="15ccc-249">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15ccc-249">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="15ccc-250">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15ccc-250">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="15ccc-251">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15ccc-251">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="15ccc-252">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="15ccc-252">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="15ccc-253">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15ccc-253">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
