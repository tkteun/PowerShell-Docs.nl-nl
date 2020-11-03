---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-JobTrigger
ms.openlocfilehash: 8d1b12b67ccf695e1c4b948e6eeecf292c588af4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250297"
---
# <span data-ttu-id="e0a91-103">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e0a91-103">Set-JobTrigger</span></span>

## <span data-ttu-id="e0a91-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e0a91-104">SYNOPSIS</span></span>
<span data-ttu-id="e0a91-105">Hiermee wijzigt u de taak trigger van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="e0a91-105">Changes the job trigger of a scheduled job.</span></span>

## <span data-ttu-id="e0a91-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e0a91-106">SYNTAX</span></span>

```
Set-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-DaysInterval <Int32>] [-WeeksInterval <Int32>]
 [-RandomDelay <TimeSpan>] [-At <DateTime>] [-User <String>] [-DaysOfWeek <DayOfWeek[]>] [-AtStartup]
 [-AtLogOn] [-Once] [-RepetitionInterval <TimeSpan>] [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely]
 [-Daily] [-Weekly] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="e0a91-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e0a91-107">DESCRIPTION</span></span>
<span data-ttu-id="e0a91-108">Met de cmdlet **set-JobTrigger** worden de eigenschappen van de taak triggers van geplande taken gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-108">The **Set-JobTrigger** cmdlet changes the properties of the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="e0a91-109">U kunt deze gebruiken om de tijd of frequentie te wijzigen waarmee de taken worden gestart of om te wijzigen van een op tijd gebaseerde planningen in schema's die worden geactiveerd door een aanmelding of het opstarten.</span><span class="sxs-lookup"><span data-stu-id="e0a91-109">You can use it to change the time or frequency at which the jobs start or to change from a time-based schedules to schedules that are triggered by a logon or startup.</span></span>

<span data-ttu-id="e0a91-110">Een taak trigger definieert een terugkerende planning of voor waarden voor het starten van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="e0a91-110">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="e0a91-111">Hoewel taak triggers niet op schijf worden opgeslagen, kunt u de taak triggers van geplande taken wijzigen, die op schijf worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e0a91-111">Although job triggers are not saved to disk, you can change the job triggers of scheduled jobs, which are saved to disk.</span></span>

<span data-ttu-id="e0a91-112">Als u een taak trigger van een geplande taak wilt wijzigen, moet u beginnen met behulp van de cmdlet Get-JobTrigger om de taak trigger van een geplande taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="e0a91-112">To change a job trigger of a scheduled job, begin by using the Get-JobTrigger cmdlet to get the job trigger of a scheduled job.</span></span>
<span data-ttu-id="e0a91-113">Vervolgens pipet u de trigger in op **set JobTrigger** of slaat u de trigger op in een variabele en gebruikt u de para meter *input object* van de cmdlet **set-JobTrigger** om de trigger te identificeren.</span><span class="sxs-lookup"><span data-stu-id="e0a91-113">Then, pipe the trigger to **Set-JobTrigger** or save the trigger in a variable and use the *InputObject* parameter of **Set-JobTrigger** cmdlet to identify the trigger.</span></span>
<span data-ttu-id="e0a91-114">Gebruik de resterende para meters van **set-JobTrigger** om de taak trigger te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e0a91-114">Use the remaining parameters of **Set-JobTrigger** to change the job trigger.</span></span>

<span data-ttu-id="e0a91-115">Wanneer u het type van een taak trigger wijzigt, zoals het wijzigen van een taak trigger van een dagelijkse of wekelijkse trigger naar een *AtLogon* trigger, worden de oorspronkelijke trigger eigenschappen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-115">When you change the type of a job trigger, such as changing a job trigger from a daily or weekly trigger to an *AtLogon* trigger, the original trigger properties are deleted.</span></span>
<span data-ttu-id="e0a91-116">Als u echter de waarden van de trigger wijzigt, maar niet het type ervan, zoals het wijzigen van de dagen in een wekelijkse trigger, worden alleen de eigenschappen die u opgeeft, gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-116">However, if you change the values of the trigger, but not its type, such as changing the days in a weekly trigger, only the properties that you specify are changed.</span></span>
<span data-ttu-id="e0a91-117">Alle andere eigenschappen van de oorspronkelijke taak trigger blijven behouden.</span><span class="sxs-lookup"><span data-stu-id="e0a91-117">All other properties of the original job trigger are retained.</span></span>

<span data-ttu-id="e0a91-118">**Set-JobTrigger** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e0a91-118">**Set-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="e0a91-119">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="e0a91-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="e0a91-120">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*`  of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="e0a91-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*`  or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="e0a91-121">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e0a91-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="e0a91-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e0a91-122">EXAMPLES</span></span>

### <span data-ttu-id="e0a91-123">Voor beeld 1: de dagen in een taak trigger wijzigen</span><span class="sxs-lookup"><span data-stu-id="e0a91-123">Example 1: Change the days in a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name "DeployPackage"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Saturday}   True

The second command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job. A pipeline operator (|) sends the trigger to the **Set-JobTrigger** cmdlet, which changes the job trigger so that it starts the DeployPackage job on Wednesdays and Sundays. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "DeployPackage" | Set-JobTrigger -DaysOfWeek "Wednesday", "Sunday" -Passthru
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Sunday}     True
```

<span data-ttu-id="e0a91-124">In dit voor beeld ziet u hoe u de dagen in een wekelijkse taak trigger wijzigt.</span><span class="sxs-lookup"><span data-stu-id="e0a91-124">This example shows how to change the days in a weekly job trigger.</span></span>

<span data-ttu-id="e0a91-125">De eerste opdracht gebruikt de cmdlet Get-JobTrigger om de taak trigger van de geplande taak DeployPackage te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="e0a91-125">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="e0a91-126">De uitvoer laat zien dat de trigger de taak wordt gestart om middernacht op Wednesdays en zaterdag.</span><span class="sxs-lookup"><span data-stu-id="e0a91-126">The output shows that the trigger starts the job at midnight on Wednesdays and Saturdays.</span></span>

<span data-ttu-id="e0a91-127">Deze opdracht is niet vereist. het is alleen opgenomen om het effect van de wijziging van de trigger weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e0a91-127">This command is not required; it is included only to show the effect of the trigger change.</span></span>

### <span data-ttu-id="e0a91-128">Voor beeld 2: het taak trigger type wijzigen</span><span class="sxs-lookup"><span data-stu-id="e0a91-128">Example 2: Change the job trigger type</span></span>

```
PS C:\> Get-JobTrigger -Name "Inventory"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          AtStartup                                                      True

The second command uses the **Get-JobTrigger** cmdlet to get the *AtStartup* job trigger of the Inventory job. The command uses the *TriggerID* parameter to identify the job trigger. A pipeline operator (|) sends the job trigger to the **Set-JobTrigger** cmdlet, which changes it to a weekly job trigger that runs every four weeks on Monday at midnight. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "Inventory" -TriggerID 2 | Set-JobTrigger -Weekly -WeeksInterval 4 -DaysOfWeek Monday -At "12:00 AM"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          Weekly          10/31/2011 12:00:00 AM {Monday}                True
```

<span data-ttu-id="e0a91-129">In dit voor beeld ziet u hoe u het type taak trigger kunt wijzigen waarmee een taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="e0a91-129">This example shows how to change the type of job trigger that starts a job.</span></span>
<span data-ttu-id="e0a91-130">Met de opdrachten in dit voor beeld wordt een trigger voor een AtStartup-taak vervangen door een wekelijkse trigger.</span><span class="sxs-lookup"><span data-stu-id="e0a91-130">The commands in this example replace an AtStartup job trigger with a weekly trigger.</span></span>

<span data-ttu-id="e0a91-131">De eerste opdracht maakt gebruik van de cmdlet Get-JobTrigger om de taak trigger van de geplande voorraad taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="e0a91-131">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the Inventory scheduled job.</span></span>
<span data-ttu-id="e0a91-132">In de uitvoer ziet u dat de taak twee keer een dagelijkse trigger en een *AtStartup* -trigger heeft geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-132">The output shows that the job has two triggers a daily trigger and an *AtStartup* trigger.</span></span>

<span data-ttu-id="e0a91-133">Deze opdracht is niet vereist. het is alleen opgenomen om het effect van de wijziging van de trigger weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e0a91-133">This command is not required; it is included only to show the effect of the trigger change.</span></span>

### <span data-ttu-id="e0a91-134">Voor beeld 3: de gebruiker wijzigen op een externe taak trigger</span><span class="sxs-lookup"><span data-stu-id="e0a91-134">Example 3: Change the user on a remote job trigger</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.User} | Set-JobTrigger -User "Domain01/Admin02"}
```

<span data-ttu-id="e0a91-135">Met deze opdracht wordt de gebruiker gewijzigd in alle *AtLogon* -taak triggers van geplande taken op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="e0a91-135">This command changes the user in all *AtLogon* job triggers of scheduled jobs on the Server01 computer.</span></span>

<span data-ttu-id="e0a91-136">De opdracht gebruikt de cmdlet Invoke-Command om een opdracht uit te voeren op de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="e0a91-136">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>

<span data-ttu-id="e0a91-137">De externe opdracht begint met een Get-ScheduledJob opdracht waarmee alle geplande taken op de computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e0a91-137">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="e0a91-138">De geplande taken worden door gegeven aan de cmdlet Get-JobTrigger, waarmee de taak triggers van de geplande taken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e0a91-138">The scheduled jobs are piped to the Get-JobTrigger cmdlet, which gets the job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="e0a91-139">Elke taak trigger bevat een taak definitie-eigenschap die de geplande taak bevat. de trigger blijft dus gekoppeld aan de geplande taak, zelfs wanneer deze wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-139">Each job trigger contains a JobDefinition property that contains the scheduled job, so the trigger remains associated with the scheduled job even when it is changed.</span></span>

<span data-ttu-id="e0a91-140">De taak triggers worden door gegeven aan de cmdlet Where-Object, waarmee taak triggers worden opgehaald die de eigenschap gebruiker hebben.</span><span class="sxs-lookup"><span data-stu-id="e0a91-140">The job triggers are piped to the Where-Object cmdlet, which gets job triggers that have the User property.</span></span>
<span data-ttu-id="e0a91-141">De geselecteerde taak triggers worden gepiped naar de cmdlet **set-JobTrigger** , waarmee de gebruiker wordt gewijzigd in Domain01\Admin02.</span><span class="sxs-lookup"><span data-stu-id="e0a91-141">The selected job triggers are piped to the **Set-JobTrigger** cmdlet, which changes the user to Domain01\Admin02.</span></span>

### <span data-ttu-id="e0a91-142">Voor beeld 4: een van de vele taak triggers wijzigen</span><span class="sxs-lookup"><span data-stu-id="e0a91-142">Example 4: Change one of many job triggers</span></span>

```
PS C:\> Get-JobTrigger -Name "SecurityCheck"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           4/24/2013 3:00:00 AM                           True
2          Weekly          4/24/2013 4:00:00 PM   {Sunday}                True
3          Once            4/24/2013 4:00:00 PM                           True

The second command uses the **TriggerID** parameter of the **Get-JobTrigger** cmdlet to get the *Once* trigger of the SecurityCheck scheduled job. The command pipes the trigger to the Format-List cmdlet, which displays all of the properties of the *Once* job trigger.The output shows that the trigger starts the job once every hour (RepetitionInterval = 1 hour) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:00:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The third command changes the repetition interval of the job trigger from one hour to 90 minutes. The command does not return any output.
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerId 3 | Set-JobTrigger -RepetitionInterval (New-TimeSpan -Minutes 90)

The fourth command displays the effect of the change.The output shows that the trigger starts the job once every 90 minutes (RepetitionInterval = 1 hour, 30 minutes) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:30:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="e0a91-143">Met de opdrachten in dit voor beeld wordt het herhalings interval van de taak trigger *Once* van de geplande taak SecurityCheck van elke 60 minuten tot elke 90 minuten gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-143">The commands in this example changes the repetition interval of the *Once* job trigger of SecurityCheck scheduled job from every 60 minutes to every 90 minutes.</span></span>
<span data-ttu-id="e0a91-144">De geplande SecurityCheck-taak heeft drie taak triggers, waardoor de opdrachten de para meter *TriggerId* van de cmdlet Get-JobTrigger gebruiken om de taak trigger te identificeren die wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-144">The SecurityCheck scheduled job has three job triggers, so the commands use the *TriggerId* parameter of the Get-JobTrigger cmdlet to identify the job trigger that is being changed.</span></span>

<span data-ttu-id="e0a91-145">Met de eerste opdracht wordt de cmdlet **Get-JobTrigger** gebruikt om alle taak triggers van de geplande SecurityCheck-taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="e0a91-145">The first command uses the **Get-JobTrigger** cmdlet to get all job triggers of the SecurityCheck scheduled job.</span></span>
<span data-ttu-id="e0a91-146">De uitvoer, waarin de Id's van de taak triggers worden weer gegeven, laat zien dat de trigger voor de taak *eenmaal* de id 3 heeft.</span><span class="sxs-lookup"><span data-stu-id="e0a91-146">The output, which displays the IDs of the job triggers, reveals that the *Once* job trigger has an ID of 3.</span></span>

## <span data-ttu-id="e0a91-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e0a91-147">PARAMETERS</span></span>

### <span data-ttu-id="e0a91-148">-At</span><span class="sxs-lookup"><span data-stu-id="e0a91-148">-At</span></span>
<span data-ttu-id="e0a91-149">De taak wordt gestart op de opgegeven datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-149">Starts the job at the specified date and time.</span></span>
<span data-ttu-id="e0a91-150">Voer een **DateTime** -object in, zoals een teken reeks die wordt geretourneerd door de cmdlet Get-Date, of een String die kan worden geconverteerd naar een tijd, zoals ' 19 April 2012 15:00 ', ' 12/31/2013 9:00 pm ' of ' 3am '.</span><span class="sxs-lookup"><span data-stu-id="e0a91-150">Enter a **DateTime** object, such as one that the Get-Date cmdlet returns, or a string that can be converted to a time, such as "April 19, 2012 15:00", "12/31/2013 9:00 PM", or "3am".</span></span>

<span data-ttu-id="e0a91-151">Als u geen element van het **DateTime** -object opgeeft, zoals seconden, wordt dat element van de taak trigger niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-151">If you don't specify an element of the **DateTime** object, such as seconds, that element of the job trigger is not changed.</span></span>
<span data-ttu-id="e0a91-152">Als de oorspronkelijke taak trigger geen **DateTime** -object bevat en u een element weglaat, wordt de taak trigger gemaakt met het bijbehorende element van de huidige datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-152">If the original job trigger didn't include a **DateTime** object and you omit an element, the job trigger is created with the corresponding element from the current date and time.</span></span>

<span data-ttu-id="e0a91-153">Wanneer u de para meter *Once* gebruikt, stelt u de waarde van de para meter *in* op een bepaalde datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-153">When using the *Once* parameter, set the value of the *At* parameter to a particular date and time.</span></span>
<span data-ttu-id="e0a91-154">Omdat de standaard datum in een **DateTime** -object de huidige datum is, is het instellen van een tijd vóór de huidige tijd zonder een expliciete datum resulteert in een taak trigger voor een tijd in het verleden.</span><span class="sxs-lookup"><span data-stu-id="e0a91-154">Because the default date in a **DateTime** object is the current date, setting a time before the current time without an explicit date results in a job trigger for a time in the past.</span></span>

<span data-ttu-id="e0a91-155">**DateTime** -objecten en teken reeksen die worden geconverteerd naar **DateTime** -objecten, worden automatisch aangepast zodat ze compatibel zijn met de datum-en tijd notaties die zijn geselecteerd voor de lokale computer in de regio en taal in het configuratie scherm.</span><span class="sxs-lookup"><span data-stu-id="e0a91-155">**DateTime** objects, and strings that are converted to **DateTime** objects, are automatically adjusted to be compatible with the date and time formats selected for the local computer in Region and Language in Control Panel.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0a91-156">-AtLogOn</span><span class="sxs-lookup"><span data-stu-id="e0a91-156">-AtLogOn</span></span>
<span data-ttu-id="e0a91-157">Hiermee wordt de geplande taak gestart wanneer de opgegeven gebruikers zich aanmelden bij de computer.</span><span class="sxs-lookup"><span data-stu-id="e0a91-157">Starts the scheduled job when the specified users log on to the computer.</span></span>
<span data-ttu-id="e0a91-158">Als u een gebruiker wilt opgeven, gebruikt u de para meter *User* .</span><span class="sxs-lookup"><span data-stu-id="e0a91-158">To specify a user, use the *User* parameter.</span></span>

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

### <span data-ttu-id="e0a91-159">-AtStartup</span><span class="sxs-lookup"><span data-stu-id="e0a91-159">-AtStartup</span></span>
<span data-ttu-id="e0a91-160">De geplande taak wordt gestart wanneer Windows wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="e0a91-160">Starts the scheduled job when Windows starts.</span></span>

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

### <span data-ttu-id="e0a91-161">-Dagelijks</span><span class="sxs-lookup"><span data-stu-id="e0a91-161">-Daily</span></span>
<span data-ttu-id="e0a91-162">Geeft een terugkerende dagelijkse taak planning op.</span><span class="sxs-lookup"><span data-stu-id="e0a91-162">Specifies a recurring daily job schedule.</span></span>
<span data-ttu-id="e0a91-163">Gebruik de andere para meters in de para meter *dagelijks* instellen om de details van de planning op te geven.</span><span class="sxs-lookup"><span data-stu-id="e0a91-163">Use the other parameters in the *Daily* parameter set to specify the schedule details.</span></span>

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

### <span data-ttu-id="e0a91-164">-DaysInterval</span><span class="sxs-lookup"><span data-stu-id="e0a91-164">-DaysInterval</span></span>
<span data-ttu-id="e0a91-165">Hiermee geeft u het aantal dagen op dat in een dagelijks schema voor komt.</span><span class="sxs-lookup"><span data-stu-id="e0a91-165">Specifies the number of days between occurrences on a daily schedule.</span></span>
<span data-ttu-id="e0a91-166">Een waarde van 3 begint bijvoorbeeld met de geplande taak op dagen 1, 4, 7, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="e0a91-166">For example, a value of 3 starts the scheduled job on days 1, 4, 7 and so on.</span></span>
<span data-ttu-id="e0a91-167">De standaardwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="e0a91-167">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0a91-168">-DaysOfWeek</span><span class="sxs-lookup"><span data-stu-id="e0a91-168">-DaysOfWeek</span></span>
<span data-ttu-id="e0a91-169">Hiermee geeft u de dagen van de week op waarop een wekelijkse geplande taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-169">Specifies the days of the week on which a weekly scheduled job runs.</span></span>
<span data-ttu-id="e0a91-170">Voer de namen van dagen in, zoals maandag, donderdag, gehele getallen van 0-6, waarbij 0 staat voor zondag, of een asterisk ( \* ) die elke dag voor stelt.</span><span class="sxs-lookup"><span data-stu-id="e0a91-170">Enter day names, such as Monday, Thursday, integers 0-6, where 0 represents Sunday, or an asterisk (\*) to represent every day.</span></span>
<span data-ttu-id="e0a91-171">Deze para meter is vereist in de set met wekelijkse para meters.</span><span class="sxs-lookup"><span data-stu-id="e0a91-171">This parameter is required in the Weekly parameter set.</span></span>

<span data-ttu-id="e0a91-172">De namen van dagen worden geconverteerd naar hun gehele waarden in de taak trigger.</span><span class="sxs-lookup"><span data-stu-id="e0a91-172">Day names are converted to their integer values in the job trigger.</span></span>
<span data-ttu-id="e0a91-173">Wanneer u namen van dagen tussen aanhalings tekens in een opdracht plaatst, plaatst u de naam van elke dag in afzonderlijke aanhalings tekens, zoals "maandag", "dinsdag".</span><span class="sxs-lookup"><span data-stu-id="e0a91-173">When you enclose day names in quotation marks in a command, enclose each day name in separate quotation marks, such as "Monday", "Tuesday".</span></span>
<span data-ttu-id="e0a91-174">Als u meerdere namen van dagen in een enkel aanhalings teken plaatst, worden de bijbehorende waarden voor gehele getallen opgeteld.</span><span class="sxs-lookup"><span data-stu-id="e0a91-174">If you enclose multiple day names in a single quotation mark pair, the corresponding integer values are summed.</span></span>
<span data-ttu-id="e0a91-175">Bijvoorbeeld: ' maandag, dinsdag ' (1, 2) resulteert in een waarde van ' woensdag ' (3).</span><span class="sxs-lookup"><span data-stu-id="e0a91-175">For example, "Monday, Tuesday" (1, 2) results in a value of "Wednesday" (3).</span></span>

```yaml
Type: System.DayOfWeek[]
Parameter Sets: (All)
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0a91-176">-Input object</span><span class="sxs-lookup"><span data-stu-id="e0a91-176">-InputObject</span></span>
<span data-ttu-id="e0a91-177">Hiermee geeft u de taak triggers.</span><span class="sxs-lookup"><span data-stu-id="e0a91-177">Specifies the job triggers.</span></span>
<span data-ttu-id="e0a91-178">Voer een variabele in die **ScheduledJobTrigger** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobTrigger** -objecten worden opgehaald, zoals een Get-JobTrigger opdracht.</span><span class="sxs-lookup"><span data-stu-id="e0a91-178">Enter a variable that contains **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="e0a91-179">U kunt ook een **ScheduledJobTrigger** -object pipeen naar **set-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="e0a91-179">You can also pipe a **ScheduledJobTrigger** object to **Set-JobTrigger**.</span></span>

<span data-ttu-id="e0a91-180">Als u meerdere taak triggers opgeeft, worden met **set-JobTrigger** dezelfde wijzigingen aangebracht aan alle taak triggers.</span><span class="sxs-lookup"><span data-stu-id="e0a91-180">If you specify multiple job triggers, **Set-JobTrigger** makes the same changes to all job triggers.</span></span>

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

### <span data-ttu-id="e0a91-181">-Eenmaal</span><span class="sxs-lookup"><span data-stu-id="e0a91-181">-Once</span></span>
<span data-ttu-id="e0a91-182">Hiermee geeft u een schema voor niet-terugkerende (eenmalige).</span><span class="sxs-lookup"><span data-stu-id="e0a91-182">Specifies a non-recurring (one time) schedule.</span></span>

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

### <span data-ttu-id="e0a91-183">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e0a91-183">-PassThru</span></span>
<span data-ttu-id="e0a91-184">Retourneert de taak triggers die zijn gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-184">Returns the job triggers that changed.</span></span>
<span data-ttu-id="e0a91-185">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e0a91-185">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e0a91-186">-RandomDelay</span><span class="sxs-lookup"><span data-stu-id="e0a91-186">-RandomDelay</span></span>
<span data-ttu-id="e0a91-187">Hiermee schakelt u een wille keurige vertraging in die begint op de geplande begin tijd en stelt de maximale vertragings waarde in.</span><span class="sxs-lookup"><span data-stu-id="e0a91-187">Enables a random delay that begins at the scheduled start time, and sets the maximum delay value.</span></span>
<span data-ttu-id="e0a91-188">De lengte van de vertraging is ingesteld op wille keurige pseudo voor elk begin en varieert van geen vertraging tot de tijd die is opgegeven door de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="e0a91-188">The length of the delay is set pseudo-randomly for each start and varies from no delay to the time specified by the value of this parameter.</span></span>
<span data-ttu-id="e0a91-189">De standaard waarde, nul (00:00:00), schakelt de wille keurige vertraging uit.</span><span class="sxs-lookup"><span data-stu-id="e0a91-189">The default value, zero (00:00:00), disables the random delay.</span></span>

<span data-ttu-id="e0a91-190">Voer een time span-object in, zoals het resultaat van de cmdlet New-TimeSpan, of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format, die automatisch wordt geconverteerd naar een time span-object.</span><span class="sxs-lookup"><span data-stu-id="e0a91-190">Enter a timespan object, such as one returned by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format, which is automatically converted to a timespan object.</span></span>

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

### <span data-ttu-id="e0a91-191">-RepeatIndefinitely</span><span class="sxs-lookup"><span data-stu-id="e0a91-191">-RepeatIndefinitely</span></span>
<span data-ttu-id="e0a91-192">Deze para meter, die beschikbaar is in Windows Power Shell 4,0, elimineert de nood zaak om een **time span. MaxValue** -waarde voor de para meter *RepetitionDuration* op te geven om een geplande taak herhaaldelijk uit te voeren voor een onbepaalde periode.</span><span class="sxs-lookup"><span data-stu-id="e0a91-192">This parameter, available starting in Windows PowerShell 4.0, eliminates the necessity of specifying a **TimeSpan.MaxValue** value for the *RepetitionDuration* parameter to run a scheduled job repeatedly, for an indefinite period.</span></span>

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

### <span data-ttu-id="e0a91-193">-RepetitionDuration</span><span class="sxs-lookup"><span data-stu-id="e0a91-193">-RepetitionDuration</span></span>
<span data-ttu-id="e0a91-194">Herhaalt de taak totdat de opgegeven tijd verloopt.</span><span class="sxs-lookup"><span data-stu-id="e0a91-194">Repeats the job until the specified time expires.</span></span>
<span data-ttu-id="e0a91-195">De frequentie van de herhaling wordt bepaald door de waarde van de para meter *RepetitionInterval* .</span><span class="sxs-lookup"><span data-stu-id="e0a91-195">The repetition frequency is determined by the value of the *RepetitionInterval* parameter.</span></span>
<span data-ttu-id="e0a91-196">Als de waarde van **RepetitionInterval** bijvoorbeeld 5 minuten is en de waarde van *RepetitionDuration* 2 uur is, wordt de taak gedurende twee uur elke vijf minuten geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-196">For example, if the value of **RepetitionInterval** is 5 minutes and the value of *RepetitionDuration* is 2 hours, the job is triggered every five minutes for two hours.</span></span>

<span data-ttu-id="e0a91-197">Voer een time span-object in, zoals een voor het retour neren van de cmdlet New-TimeSpan, of een teken reeks die kan worden geconverteerd naar een time span-object, zoals ' 1:05:30 '.</span><span class="sxs-lookup"><span data-stu-id="e0a91-197">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="e0a91-198">Als u een taak voor onbepaalde tijd wilt uitvoeren, voegt u in plaats daarvan de para meter *RepeatIndefinitely* toe.</span><span class="sxs-lookup"><span data-stu-id="e0a91-198">To run a job indefinitely, add the *RepeatIndefinitely* parameter instead.</span></span>

<span data-ttu-id="e0a91-199">Als u een taak wilt stoppen voordat de herhalings duur van de taak trigger verloopt, stelt u de waarde voor **RepetitionDuration** in op nul (0).</span><span class="sxs-lookup"><span data-stu-id="e0a91-199">To stop a job before the job trigger repetition duration expires, set the **RepetitionDuration** value to zero (0).</span></span>

<span data-ttu-id="e0a91-200">Als u de herhalings duur of het herhalings interval van een *eenmalige* taak trigger wilt wijzigen, moet de opdracht zowel de para meters **RepetitionInterval** als **RepetitionDuration** bevatten.</span><span class="sxs-lookup"><span data-stu-id="e0a91-200">To change the repetition duration or repetition interval of a *Once* job trigger, the command must include both the **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>
<span data-ttu-id="e0a91-201">Als u de herhalings duur of herhalings intervallen van andere typen taak triggers wilt wijzigen, moet de opdracht de para meters *Once* , *at* , *RepetitionInterval* en *RepetitionDuration* bevatten.</span><span class="sxs-lookup"><span data-stu-id="e0a91-201">To change the repetition duration or repetition intervals of other types of job triggers, the command must include the *Once* , *At* , *RepetitionInterval* and *RepetitionDuration* parameters.</span></span>

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

### <span data-ttu-id="e0a91-202">-RepetitionInterval</span><span class="sxs-lookup"><span data-stu-id="e0a91-202">-RepetitionInterval</span></span>
<span data-ttu-id="e0a91-203">Hiermee wordt de taak herhaald op het opgegeven tijds interval.</span><span class="sxs-lookup"><span data-stu-id="e0a91-203">Repeats the job at the specified time interval.</span></span>
<span data-ttu-id="e0a91-204">Als de waarde van deze para meter bijvoorbeeld 2 uur is, wordt de taak elke twee uur geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-204">For example, if the value of this parameter is 2 hours, the job is triggered every two hours.</span></span>
<span data-ttu-id="e0a91-205">De standaard waarde, 0, herhaalt de taak niet.</span><span class="sxs-lookup"><span data-stu-id="e0a91-205">The default value, 0, does not repeat the job.</span></span>

<span data-ttu-id="e0a91-206">Voer een time span-object in, zoals een voor het retour neren van de cmdlet New-TimeSpan, of een teken reeks die kan worden geconverteerd naar een time span-object, zoals ' 1:05:30 '.</span><span class="sxs-lookup"><span data-stu-id="e0a91-206">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="e0a91-207">Als u de herhalings duur of het herhalings interval van een **eenmalige** taak trigger wilt wijzigen, moet de opdracht zowel de para meters **RepetitionInterval** als **RepetitionDuration** bevatten.</span><span class="sxs-lookup"><span data-stu-id="e0a91-207">To change the repetition duration or repetition interval of a **Once** job trigger, the command must include both the **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>
<span data-ttu-id="e0a91-208">Als u de herhalings duur of herhalings intervallen van andere typen taak triggers wilt wijzigen, moet de opdracht de para meters **Once** , **at** , **RepetitionInterval** en **RepetitionDuration** bevatten.</span><span class="sxs-lookup"><span data-stu-id="e0a91-208">To change the repetition duration or repetition intervals of other types of job triggers, the command must include the **Once** , **At** , **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>

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

### <span data-ttu-id="e0a91-209">-User</span><span class="sxs-lookup"><span data-stu-id="e0a91-209">-User</span></span>
<span data-ttu-id="e0a91-210">Hiermee geeft u de gebruikers die een geplande taak *AtLogon* starten.</span><span class="sxs-lookup"><span data-stu-id="e0a91-210">Specifies the users who trigger an *AtLogon* start of a scheduled job.</span></span>
<span data-ttu-id="e0a91-211">Voer de naam van een gebruiker in \<UserName\> of in of \<Domain\Username\> Voer een asterisk ( \* ) in om alle gebruikers weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e0a91-211">Enter the name of a user in \<UserName\> or \<Domain\Username\> format or enter an asterisk (\*) to represent all users.</span></span>
<span data-ttu-id="e0a91-212">De standaard waarde is alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="e0a91-212">The default value is all users.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0a91-213">-Wekelijks</span><span class="sxs-lookup"><span data-stu-id="e0a91-213">-Weekly</span></span>
<span data-ttu-id="e0a91-214">Hiermee geeft u een terugkerende wekelijkse taak planning op.</span><span class="sxs-lookup"><span data-stu-id="e0a91-214">Specifies a recurring weekly job schedule.</span></span>
<span data-ttu-id="e0a91-215">Gebruik de andere para meters in de set met *wekelijkse* para meters om de details van de planning op te geven.</span><span class="sxs-lookup"><span data-stu-id="e0a91-215">Use the other parameters in the *Weekly* parameter set to specify the schedule details.</span></span>

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

### <span data-ttu-id="e0a91-216">-WeeksInterval</span><span class="sxs-lookup"><span data-stu-id="e0a91-216">-WeeksInterval</span></span>
<span data-ttu-id="e0a91-217">Hiermee geeft u het aantal weken tussen exemplaren op voor een wekelijks taak schema.</span><span class="sxs-lookup"><span data-stu-id="e0a91-217">Specifies the number of weeks between occurrences on a weekly job schedule.</span></span>
<span data-ttu-id="e0a91-218">Een waarde van 3 begint bijvoorbeeld met de geplande taak op weken 1, 4, 7 enzovoort.</span><span class="sxs-lookup"><span data-stu-id="e0a91-218">For example, a value of 3 starts the scheduled job on weeks 1, 4, 7 and so on.</span></span>
<span data-ttu-id="e0a91-219">De standaardwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="e0a91-219">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0a91-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e0a91-220">CommonParameters</span></span>
<span data-ttu-id="e0a91-221">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e0a91-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e0a91-222">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e0a91-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e0a91-223">INVOER</span><span class="sxs-lookup"><span data-stu-id="e0a91-223">INPUTS</span></span>

### <span data-ttu-id="e0a91-224">Micro soft. Power shell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="e0a91-224">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="e0a91-225">U kunt meerdere taak triggers door sluizen naar **set-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="e0a91-225">You can pipe multiple job triggers to **Set-JobTrigger**.</span></span>

## <span data-ttu-id="e0a91-226">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e0a91-226">OUTPUTS</span></span>

### <span data-ttu-id="e0a91-227">Geen of Microsoft. Power shell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="e0a91-227">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="e0a91-228">Wanneer u de para meter *PassThru* gebruikt, retourneert **set-JobTrigger** de taak triggers die zijn gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-228">When you use the *Passthru* parameter, **Set-JobTrigger** returns the job triggers that were changed.</span></span>
<span data-ttu-id="e0a91-229">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-229">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e0a91-230">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e0a91-230">NOTES</span></span>

* <span data-ttu-id="e0a91-231">Taak triggers hebben een JobDefintion-eigenschap die deze koppelt aan de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="e0a91-231">Job triggers have a JobDefintion property that associates them with the scheduled job.</span></span> <span data-ttu-id="e0a91-232">Wanneer u de taak trigger van een geplande taak wijzigt, wordt de taak gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="e0a91-232">When you change the job trigger of a scheduled job, the job is changed.</span></span> <span data-ttu-id="e0a91-233">U hoeft geen Set-ScheduledJob opdracht te gebruiken om de gewijzigde trigger toe te passen op de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="e0a91-233">You do not need to use a Set-ScheduledJob command to apply the changed trigger to the scheduled job.</span></span>

## <span data-ttu-id="e0a91-234">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e0a91-234">RELATED LINKS</span></span>

[<span data-ttu-id="e0a91-235">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e0a91-235">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="e0a91-236">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e0a91-236">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="e0a91-237">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e0a91-237">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="e0a91-238">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e0a91-238">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="e0a91-239">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e0a91-239">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="e0a91-240">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e0a91-240">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="e0a91-241">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e0a91-241">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="e0a91-242">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="e0a91-242">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="e0a91-243">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e0a91-243">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="e0a91-244">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="e0a91-244">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="e0a91-245">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e0a91-245">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="e0a91-246">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e0a91-246">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="e0a91-247">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e0a91-247">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="e0a91-248">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e0a91-248">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="e0a91-249">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="e0a91-249">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="e0a91-250">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e0a91-250">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
