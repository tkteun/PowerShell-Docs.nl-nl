---
ms.date: 10/30/2018
keywords: DSC, Power shell, configuratie, installatie
title: Problemen met DSC oplossen
ms.openlocfilehash: 2a0d2138f30573b9ae6cf52d8b106a05f1193407
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942410"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="ab90b-103">Problemen met DSC oplossen</span><span class="sxs-lookup"><span data-stu-id="ab90b-103">Troubleshooting DSC</span></span>

<span data-ttu-id="ab90b-104">_Applies: Windows Power Shell 4,0, Windows Power shell 5.0 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="ab90b-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="ab90b-105">In dit onderwerp worden manieren beschreven om problemen met DSC op te lossen wanneer er problemen optreden.</span><span class="sxs-lookup"><span data-stu-id="ab90b-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="ab90b-106">WinRM-afhankelijkheid</span><span class="sxs-lookup"><span data-stu-id="ab90b-106">WinRM Dependency</span></span>

<span data-ttu-id="ab90b-107">Windows Power shell desired state Configuration (DSC) is afhankelijk van WinRM.</span><span class="sxs-lookup"><span data-stu-id="ab90b-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="ab90b-108">WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 en Windows 7.</span><span class="sxs-lookup"><span data-stu-id="ab90b-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="ab90b-109">Voer `Set-WSManQuickConfig`uit in een Windows Power shell-sessie met verhoogde bevoegdheden om WinRM in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="ab90b-110">Get-DscConfigurationStatus gebruiken</span><span class="sxs-lookup"><span data-stu-id="ab90b-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="ab90b-111">De cmdlet [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) krijgt informatie over de configuratie status van een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="ab90b-111">The [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="ab90b-112">Er wordt een uitgebreid object geretourneerd dat informatie op hoog niveau bevat over de vraag of de configuratie is geslaagd of niet.</span><span class="sxs-lookup"><span data-stu-id="ab90b-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="ab90b-113">U kunt het object bekijken om details over de configuratie-uitvoering te detecteren, zoals:</span><span class="sxs-lookup"><span data-stu-id="ab90b-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="ab90b-114">Alle resources die zijn mislukt</span><span class="sxs-lookup"><span data-stu-id="ab90b-114">All of the resources that failed</span></span>
- <span data-ttu-id="ab90b-115">Alle bronnen waarvoor opnieuw opstarten is aangevraagd</span><span class="sxs-lookup"><span data-stu-id="ab90b-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="ab90b-116">Meta configuratie-instellingen op het moment van de configuratie-uitvoering</span><span class="sxs-lookup"><span data-stu-id="ab90b-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="ab90b-117">Heap.</span><span class="sxs-lookup"><span data-stu-id="ab90b-117">Etc.</span></span>

<span data-ttu-id="ab90b-118">De volgende parameterset retourneert de status informatie voor de laatste configuratie-uitvoering:</span><span class="sxs-lookup"><span data-stu-id="ab90b-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
<span data-ttu-id="ab90b-119">De volgende parameterset retourneert de status informatie voor alle vorige configuratie-uitvoeringen:</span><span class="sxs-lookup"><span data-stu-id="ab90b-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="ab90b-120">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ab90b-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ResourceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="ab90b-121">Mijn script wordt niet uitgevoerd: DSC-Logboeken gebruiken om script fouten te diagnosticeren</span><span class="sxs-lookup"><span data-stu-id="ab90b-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="ab90b-122">Net als alle Windows-software registreert DSC fouten en gebeurtenissen in [Logboeken](/windows/desktop/EventLog/about-event-logging) die kunnen worden weer gegeven vanuit het [Logboeken](https://support.microsoft.com/hub/4338813/windows-help).</span><span class="sxs-lookup"><span data-stu-id="ab90b-122">Like all Windows software, DSC records errors and events in [logs](/windows/desktop/EventLog/about-event-logging) that can be viewed from the [Event Viewer](https://support.microsoft.com/hub/4338813/windows-help).</span></span>
<span data-ttu-id="ab90b-123">Door deze logboeken te controleren, kunt u beter begrijpen waarom een bepaalde bewerking niet kan worden uitgevoerd en hoe u fouten in de toekomst wilt voor komen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="ab90b-124">Het schrijven van configuratie scripts kan lastig zijn, zodat het bijhouden van fouten eenvoudiger is terwijl u zich aanmeldt, met behulp van de DSC-logboek bron om de voortgang van uw configuratie in het DSC-logboek voor analyse gebeurtenissen te volgen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="ab90b-125">Waar worden DSC-gebeurtenis logboeken?</span><span class="sxs-lookup"><span data-stu-id="ab90b-125">Where are DSC event logs?</span></span>

<span data-ttu-id="ab90b-126">In Logboeken bevinden DSC-gebeurtenissen zich in: **Logboeken toepassingen en services/micro soft/Windows/desired state Configuration**</span><span class="sxs-lookup"><span data-stu-id="ab90b-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="ab90b-127">De bijbehorende Power shell-cmdlet [Get-Wine vent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)kan ook worden uitgevoerd om de gebeurtenis logboeken weer te geven:</span><span class="sxs-lookup"><span data-stu-id="ab90b-127">The corresponding PowerShell cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="ab90b-128">Zoals hierboven wordt weer gegeven, is de primaire logboek naam van DSC **micro soft > Windows-> DSC** (andere logboek namen onder Windows worden hier niet weer gegeven voor de boog).</span><span class="sxs-lookup"><span data-stu-id="ab90b-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="ab90b-129">De primaire naam wordt toegevoegd aan de kanaal naam om de volledige logboek naam te maken.</span><span class="sxs-lookup"><span data-stu-id="ab90b-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="ab90b-130">De DSC-engine schrijft voornamelijk in drie typen logboeken: [Operationele, analyse en logboeken voor fout opsporing](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="ab90b-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span></span> <span data-ttu-id="ab90b-131">Aangezien de logboeken voor analyse en fout opsporing standaard zijn uitgeschakeld, moet u ze inschakelen in Logboeken.</span><span class="sxs-lookup"><span data-stu-id="ab90b-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="ab90b-132">Als u dit wilt doen, opent u Logboeken door in Windows Power shell show-EventLog te typen. of klik op de knop **Start** , klik op **configuratie scherm**, klik op **systeem beheer**en klik vervolgens op **Logboeken**.</span><span class="sxs-lookup"><span data-stu-id="ab90b-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="ab90b-133">Klik in het menu **beeld** in Logboeken op **analyse logboeken en fout opsporing weer geven**.</span><span class="sxs-lookup"><span data-stu-id="ab90b-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="ab90b-134">De logboek naam voor het analytische kanaal is **micro soft-Windows-DSC/analytic**en het fout opsporingsprogramma is **micro soft-Windows-DSC/debug**.</span><span class="sxs-lookup"><span data-stu-id="ab90b-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="ab90b-135">U kunt ook het hulp programma [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) gebruiken om de logboeken in te scha kelen, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="ab90b-135">You could also use the [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="ab90b-136">Wat bevatten DSC-logboeken?</span><span class="sxs-lookup"><span data-stu-id="ab90b-136">What do DSC logs contain?</span></span>

<span data-ttu-id="ab90b-137">DSC-logboeken worden verdeeld over de drie logboek kanalen op basis van het belang van het bericht.</span><span class="sxs-lookup"><span data-stu-id="ab90b-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="ab90b-138">Het operationele logboek in DSC bevat alle fout berichten en kan worden gebruikt om een probleem te identificeren.</span><span class="sxs-lookup"><span data-stu-id="ab90b-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="ab90b-139">Het analytische logboek heeft een groter volume aan gebeurtenissen en kan identificeren waar fout (en) zijn opgetreden.</span><span class="sxs-lookup"><span data-stu-id="ab90b-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="ab90b-140">Dit kanaal bevat ook uitgebreide berichten (indien van toepassing).</span><span class="sxs-lookup"><span data-stu-id="ab90b-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="ab90b-141">Het logboek voor fout opsporing bevat logboeken die u kunnen helpen begrijpen hoe de fouten zijn opgetreden.</span><span class="sxs-lookup"><span data-stu-id="ab90b-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="ab90b-142">DSC-gebeurtenis berichten zijn zodanig gestructureerd dat elk gebeurtenis bericht begint met een taak-ID die een DSC-bewerking uniek vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="ab90b-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="ab90b-143">In het volgende voor beeld wordt geprobeerd het bericht te verkrijgen van de eerste gebeurtenis die is geregistreerd in het operationeel DSC-logboek.</span><span class="sxs-lookup"><span data-stu-id="ab90b-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="ab90b-144">DSC-gebeurtenissen worden vastgelegd in een bepaalde structuur waarmee de gebruiker gebeurtenissen van één DSC-taak kan samen voegen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="ab90b-145">De structuur is als volgt:</span><span class="sxs-lookup"><span data-stu-id="ab90b-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="ab90b-146">Gebeurtenissen van één DSC-bewerking verzamelen</span><span class="sxs-lookup"><span data-stu-id="ab90b-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="ab90b-147">DSC-gebeurtenis logboeken bevatten gebeurtenissen die door verschillende DSC-bewerkingen worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ab90b-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="ab90b-148">Het is echter doorgaans een belang rijkere manier om een bepaalde bewerking uit te leggen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="ab90b-149">Alle DSC-logboeken kunnen worden gegroepeerd op de eigenschap voor de taak-ID die uniek is voor elke DSC-bewerking.</span><span class="sxs-lookup"><span data-stu-id="ab90b-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="ab90b-150">De taak-ID wordt weer gegeven als de eerste eigenschaps waarde in alle DSC-gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="ab90b-151">In de volgende stappen wordt uitgelegd hoe u alle gebeurtenissen in een gegroepeerde matrix structuur kunt samen voegen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

<span data-ttu-id="ab90b-152">Hier bevat de variabele `$SeparateDscOperations` logboeken gegroepeerd op de taak-Id's.</span><span class="sxs-lookup"><span data-stu-id="ab90b-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="ab90b-153">Elk matrix element van deze variabele vertegenwoordigt een groep gebeurtenissen die zijn geregistreerd door een andere DSC-bewerking, waardoor er meer informatie over de logboeken kan worden geopend.</span><span class="sxs-lookup"><span data-stu-id="ab90b-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....

PS C:\> $SeparateDscOperations[0].Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

<span data-ttu-id="ab90b-154">U kunt de gegevens in de variabele `$SeparateDscOperations` extra heren met behulp van [where-object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="ab90b-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span> <span data-ttu-id="ab90b-155">Hieronder volgen vijf scenario's waarin u mogelijk gegevens wilt ophalen voor het oplossen van problemen met DSC:</span><span class="sxs-lookup"><span data-stu-id="ab90b-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="ab90b-156">1: Mislukte bewerkingen</span><span class="sxs-lookup"><span data-stu-id="ab90b-156">1: Operations failures</span></span>

<span data-ttu-id="ab90b-157">Alle gebeurtenissen hebben [niveau Ernst](/windows/desktop/WES/defining-severity-levels).</span><span class="sxs-lookup"><span data-stu-id="ab90b-157">All events have [severity levels](/windows/desktop/WES/defining-severity-levels).</span></span> <span data-ttu-id="ab90b-158">Deze informatie kan worden gebruikt om de fout gebeurtenissen te identificeren:</span><span class="sxs-lookup"><span data-stu-id="ab90b-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="ab90b-159">2: Details van bewerkingen die in de afgelopen helft uur worden uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="ab90b-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="ab90b-160">`TimeCreated`, een eigenschap van elke Windows-gebeurtenis, geeft de tijd aan waarop de gebeurtenis is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="ab90b-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="ab90b-161">Het vergelijken van deze eigenschap met een bepaald datum/tijd-object kan worden gebruikt om alle gebeurtenissen te filteren:</span><span class="sxs-lookup"><span data-stu-id="ab90b-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="ab90b-162">3: Berichten van de laatste bewerking</span><span class="sxs-lookup"><span data-stu-id="ab90b-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="ab90b-163">De laatste bewerking wordt opgeslagen in de eerste index van de matrix groep `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="ab90b-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="ab90b-164">Opvragen van de berichten van de groep voor index 0 retourneert alle berichten voor de meest recente bewerking:</span><span class="sxs-lookup"><span data-stu-id="ab90b-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

```powershell
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="ab90b-165">3 Fout berichten die zijn geregistreerd voor recente mislukte bewerkingen</span><span class="sxs-lookup"><span data-stu-id="ab90b-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="ab90b-166">`$SeparateDscOperations[0].Group` bevat een set gebeurtenissen voor de laatste bewerking.</span><span class="sxs-lookup"><span data-stu-id="ab90b-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="ab90b-167">Voer de `Where-Object`-cmdlet uit om de gebeurtenissen te filteren op basis van de weergave naam van het niveau.</span><span class="sxs-lookup"><span data-stu-id="ab90b-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="ab90b-168">De resultaten worden opgeslagen in de variabele `$myFailedEvent`, die verder kan worden ontdubbeld om het gebeurtenis bericht op te halen:</span><span class="sxs-lookup"><span data-stu-id="ab90b-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="ab90b-169">5,0 Alle gebeurtenissen die worden gegenereerd voor een bepaalde taak-ID.</span><span class="sxs-lookup"><span data-stu-id="ab90b-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="ab90b-170">`$SeparateDscOperations` is een matrix van groepen, die elk de naam hebben als de unieke taak-ID.</span><span class="sxs-lookup"><span data-stu-id="ab90b-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="ab90b-171">Door de `Where-Object`-cmdlet uit te voeren, kunt u deze groepen gebeurtenissen met een bepaalde taak-ID extra heren:</span><span class="sxs-lookup"><span data-stu-id="ab90b-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="ab90b-172">DSC-logboeken analyseren met behulp van xDscDiagnostics</span><span class="sxs-lookup"><span data-stu-id="ab90b-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="ab90b-173">**xDscDiagnostics** is een Power shell-module die bestaat uit verschillende functies waarmee DSC-fouten op uw machine kunnen worden geanalyseerd.</span><span class="sxs-lookup"><span data-stu-id="ab90b-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="ab90b-174">Deze functies kunnen u helpen bij het identificeren van alle lokale gebeurtenissen van eerdere DSC-bewerkingen of DSC-gebeurtenissen op externe computers (met geldige referenties).</span><span class="sxs-lookup"><span data-stu-id="ab90b-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="ab90b-175">Hier wordt de term DSC-bewerking gebruikt voor het definiëren van een enkele unieke DSC-uitvoering van het begin tot het einde.</span><span class="sxs-lookup"><span data-stu-id="ab90b-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="ab90b-176">@No__t-0 zou bijvoorbeeld een afzonderlijke DSC-bewerking zijn.</span><span class="sxs-lookup"><span data-stu-id="ab90b-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="ab90b-177">Op dezelfde manier kunnen alle andere cmdlets in DSC (zoals `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) worden aangeduid als afzonderlijke DSC-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="ab90b-178">De functies worden beschreven op [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="ab90b-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="ab90b-179">Help is beschikbaar door `Get-Help <cmdlet name>` uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ab90b-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="ab90b-180">Details van DSC-bewerkingen ophalen</span><span class="sxs-lookup"><span data-stu-id="ab90b-180">Getting details of DSC operations</span></span>

<span data-ttu-id="ab90b-181">Met de functie `Get-xDscOperation` kunt u de resultaten vinden van de DSC-bewerkingen die worden uitgevoerd op een of meer computers en wordt een object geretourneerd dat de verzameling gebeurtenissen bevat die door elke DSC-bewerking worden geproduceerd.</span><span class="sxs-lookup"><span data-stu-id="ab90b-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="ab90b-182">In de volgende uitvoer zijn bijvoorbeeld drie opdrachten uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ab90b-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="ab90b-183">Het eerste dat is door gegeven en de andere twee is mislukt.</span><span class="sxs-lookup"><span data-stu-id="ab90b-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="ab90b-184">Deze resultaten worden samen vatting van de uitvoer van `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="ab90b-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="ab90b-185">U kunt ook opgeven dat u alleen de resultaten voor de meest recente bewerkingen wilt gebruiken met behulp van de para meter `Newest`:</span><span class="sxs-lookup"><span data-stu-id="ab90b-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="ab90b-186">Details van DSC-gebeurtenissen ophalen</span><span class="sxs-lookup"><span data-stu-id="ab90b-186">Getting details of DSC events</span></span>

<span data-ttu-id="ab90b-187">De cmdlet `Trace-xDscOperation` retourneert een object met een verzameling gebeurtenissen, hun gebeurtenis typen en de bericht uitvoer die is gegenereerd op basis van een bepaalde DSC-bewerking.</span><span class="sxs-lookup"><span data-stu-id="ab90b-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="ab90b-188">Als u een fout ontdekt in een van de bewerkingen met `Get-xDscOperation`, zou u die bewerking traceren om te bepalen welke gebeurtenissen een fout veroorzaken.</span><span class="sxs-lookup"><span data-stu-id="ab90b-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="ab90b-189">Gebruik de para meter `SequenceID` om de gebeurtenissen voor een specifieke bewerking voor een specifieke computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="ab90b-190">Als u bijvoorbeeld een `SequenceID` opgeeft, `Trace-xDscOperaion` de tracering ophalen voor de DSC-bewerking die is genegende van de laatste bewerking:</span><span class="sxs-lookup"><span data-stu-id="ab90b-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

<span data-ttu-id="ab90b-191">Geef de **GUID** door die is toegewezen aan een specifieke DSC-bewerking (zoals geretourneerd door de cmdlet `Get-xDscOperation`) om de gebeurtenis Details voor die DSC-bewerking op te halen:</span><span class="sxs-lookup"><span data-stu-id="ab90b-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmdlet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="ab90b-192">Houd er rekening mee dat, omdat `Trace-xDscOperation` gebeurtenissen uit de logboeken analyse, fout opsporing en operationeel worden verzameld, u wordt gevraagd deze logboeken in te scha kelen, zoals hierboven beschreven.</span><span class="sxs-lookup"><span data-stu-id="ab90b-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="ab90b-193">U kunt ook informatie over de gebeurtenissen verzamelen door de uitvoer van `Trace-xDscOperation` op te slaan in een variabele.</span><span class="sxs-lookup"><span data-stu-id="ab90b-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="ab90b-194">U kunt de volgende opdrachten gebruiken om alle gebeurtenissen voor een bepaalde DSC-bewerking weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ab90b-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="ab90b-195">Hiermee worden dezelfde resultaten weer gegeven als de `Get-WinEvent`-cmdlet, zoals in de volgende uitvoer:</span><span class="sxs-lookup"><span data-stu-id="ab90b-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="ab90b-196">In het ideale geval moet u `Get-xDscOperation` eerst gebruiken om de laatste DSC-configuratie op uw machines uit te geven.</span><span class="sxs-lookup"><span data-stu-id="ab90b-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="ab90b-197">Daarna kunt u een enkele bewerking (met behulp van de SequenceID of JobID) met `Trace-xDscOperation` bekijken om te ontdekken wat het achter de schermen heeft gedaan.</span><span class="sxs-lookup"><span data-stu-id="ab90b-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="ab90b-198">Gebeurtenissen ophalen voor een externe computer</span><span class="sxs-lookup"><span data-stu-id="ab90b-198">Getting events for a remote computer</span></span>

<span data-ttu-id="ab90b-199">Gebruik de para meter `ComputerName` van de cmdlet `Trace-xDscOperation` om de gebeurtenis details op een externe computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="ab90b-200">Voordat u dit kunt doen, moet u een firewall regel maken om extern beheer toe te staan op de externe computer:</span><span class="sxs-lookup"><span data-stu-id="ab90b-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="ab90b-201">Nu kunt u die computer opgeven in de aanroep van `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="ab90b-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="ab90b-202">Mijn resources worden niet bijgewerkt: De cache opnieuw instellen</span><span class="sxs-lookup"><span data-stu-id="ab90b-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="ab90b-203">De DSC-Engine slaat resources op die zijn geïmplementeerd als een Power shell-module voor efficiëntie doeleinden.</span><span class="sxs-lookup"><span data-stu-id="ab90b-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="ab90b-204">Dit kan er echter toe leiden dat er problemen zijn bij het ontwerpen van een resource en deze tegelijkertijd te testen, omdat DSC de versie in de cache laadt totdat het proces opnieuw wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="ab90b-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="ab90b-205">De enige manier om DSC-belasting te maken, is de nieuwere versie door het proces dat als host fungeert voor de DSC-engine expliciet te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="ab90b-206">En wanneer u `Start-DscConfiguration` uitvoert nadat u een aangepaste resource hebt toegevoegd en gewijzigd, kan de wijziging niet worden uitgevoerd, tenzij of tot de computer opnieuw wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="ab90b-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="ab90b-207">Dit komt doordat DSC wordt uitgevoerd in het hostproces van de WMI-provider (WmiPrvSE), en normaal gesp roken worden er veel exemplaren van WmiPrvSE tegelijk worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ab90b-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="ab90b-208">Wanneer u de computer opnieuw opstart, wordt het hostproces opnieuw gestart en wordt de cache gewist.</span><span class="sxs-lookup"><span data-stu-id="ab90b-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="ab90b-209">Als u de configuratie wilt herhalen en de cache wilt wissen zonder opnieuw op te starten, moet u het hostproces stoppen en opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="ab90b-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="ab90b-210">Dit kan per instantie geschieden, waarbij u het proces identificeert en stopt, en het opnieuw start.</span><span class="sxs-lookup"><span data-stu-id="ab90b-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="ab90b-211">U kunt ook `DebugMode`, zoals hieronder wordt geïllustreerd, gebruiken om de Power shell DSC-resource opnieuw te laden.</span><span class="sxs-lookup"><span data-stu-id="ab90b-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="ab90b-212">Als u wilt weten welk proces als host fungeert voor de DSC-engine en deze op per exemplaar wilt stoppen, kunt u de proces-ID van het WmiPrvSE weer geven dat als host fungeert voor de DSC-engine.</span><span class="sxs-lookup"><span data-stu-id="ab90b-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="ab90b-213">Als u de provider wilt bijwerken, stopt u het WmiPrvSE-proces met de onderstaande opdrachten en voert u **Start-DscConfiguration** opnieuw uit.</span><span class="sxs-lookup"><span data-stu-id="ab90b-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a><span data-ttu-id="ab90b-214">DebugMode gebruiken</span><span class="sxs-lookup"><span data-stu-id="ab90b-214">Using DebugMode</span></span>

<span data-ttu-id="ab90b-215">U kunt de DSC Local Configuration Manager (LCM) configureren voor het gebruik van `DebugMode` om altijd de cache te wissen wanneer het hostproces opnieuw wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="ab90b-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="ab90b-216">Als deze eigenschap is ingesteld op **True**, wordt de Power shell DSC-resource altijd opnieuw geladen door de engine.</span><span class="sxs-lookup"><span data-stu-id="ab90b-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="ab90b-217">Zodra u klaar bent met het schrijven van uw resource, kunt u deze weer instellen op **False** en wordt de engine teruggezet naar het gedrag van het opslaan van de modules in de cache.</span><span class="sxs-lookup"><span data-stu-id="ab90b-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="ab90b-218">Hieronder ziet u een demonstratie waarin wordt weer gegeven hoe `DebugMode` automatisch de cache kan vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="ab90b-219">Laten we eerst de standaard configuratie bekijken:</span><span class="sxs-lookup"><span data-stu-id="ab90b-219">First, let's look at the default configuration:</span></span>

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="ab90b-220">U kunt zien dat `DebugMode` is ingesteld op **' geen '** .</span><span class="sxs-lookup"><span data-stu-id="ab90b-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="ab90b-221">Als u de `DebugMode` demonstratie wilt instellen, gebruikt u de volgende Power shell-resource:</span><span class="sxs-lookup"><span data-stu-id="ab90b-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

<span data-ttu-id="ab90b-222">Maak nu een configuratie met behulp van de bovenstaande resource met de naam `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="ab90b-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

<span data-ttu-id="ab90b-223">U ziet dat de inhoud van het bestand: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` **1**is.</span><span class="sxs-lookup"><span data-stu-id="ab90b-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="ab90b-224">Werk nu de provider code bij met het volgende script:</span><span class="sxs-lookup"><span data-stu-id="ab90b-224">Now, update the provider code using the following script:</span></span>

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

<span data-ttu-id="ab90b-225">Met dit script wordt een wille keurig getal gegenereerd en wordt de provider code dienovereenkomstig bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="ab90b-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="ab90b-226">Als `DebugMode` is ingesteld op False, wordt de inhoud van het bestand ' **$env: SystemDrive\OutputFromTestProviderDebugMode.txt**' nooit gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="ab90b-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="ab90b-227">Stel nu `DebugMode` in op **' ForceModuleImport '** in uw configuratie script:</span><span class="sxs-lookup"><span data-stu-id="ab90b-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="ab90b-228">Wanneer u het bovenstaande script opnieuw uitvoert, ziet u dat de inhoud van het bestand elke keer verschillend is.</span><span class="sxs-lookup"><span data-stu-id="ab90b-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="ab90b-229">(U kunt `Get-DscConfiguration` uitvoeren om het te controleren).</span><span class="sxs-lookup"><span data-stu-id="ab90b-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="ab90b-230">Hieronder ziet u het resultaat van twee extra uitvoeringen (uw resultaten kunnen verschillen als u het script uitvoert):</span><span class="sxs-lookup"><span data-stu-id="ab90b-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="dsc-returns-unexpected-response-code-internalservererror-when-registering-with-windows-pull-server"></a><span data-ttu-id="ab90b-231">DSC retourneert ' onverwachte respons code InternalServerError ' bij het registreren met een Windows pull-server</span><span class="sxs-lookup"><span data-stu-id="ab90b-231">DSC returns "unexpected response code InternalServerError" when registering with Windows Pull Server</span></span>

<span data-ttu-id="ab90b-232">Wanneer u een-configuratie toepast op een server om deze te registreren met een exemplaar van Windows pull server, kan de volgende fout optreden.</span><span class="sxs-lookup"><span data-stu-id="ab90b-232">When applying a metaconfiguration to a server to register it with an instance of Windows Pull Server, you might encounter the following error.</span></span>

```PowerShell
Registration of the Dsc Agent with the server https://<serverfqdn>:8080/PSDSCPullServer.svc failed. The underlying error is: The attempt to register Dsc Agent with AgentId <ID> with the server 
https://<serverfqdn>:8080/PSDSCPullServer.svc/Nodes(AgentId='<ID>') returned unexpected response code InternalServerError. .
    + CategoryInfo          : InvalidResult: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : RegisterDscAgentUnsuccessful,Microsoft.PowerShell.DesiredStateConfiguration.Commands.RegisterDscAgentCommand
    + PSComputerName        : <computername>
```

<span data-ttu-id="ab90b-233">Dit kan gebeuren wanneer het certificaat dat op de server wordt gebruikt voor het versleutelen van verkeer, een algemene naam (CN) heeft die afwijkt van de DNS-naam die door het knoop punt wordt gebruikt om de URL op te lossen.</span><span class="sxs-lookup"><span data-stu-id="ab90b-233">This can occur when the certificate used on the server to encrypt traffic has a common name (CN) that is different than the DNS name used by the node to resolve the URL.</span></span>
<span data-ttu-id="ab90b-234">Werk het Windows pull Server-exemplaar bij om een certificaat met een herstelde naam te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ab90b-234">Update the Windows Pull Server instance to use a certificate with a corrected name.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab90b-235">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ab90b-235">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="ab90b-236">Concepten</span><span class="sxs-lookup"><span data-stu-id="ab90b-236">Concepts</span></span>

- [<span data-ttu-id="ab90b-237">Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen</span><span class="sxs-lookup"><span data-stu-id="ab90b-237">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](../resources/authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="ab90b-238">Andere bronnen</span><span class="sxs-lookup"><span data-stu-id="ab90b-238">Other Resources</span></span>

- [<span data-ttu-id="ab90b-239">Windows Power shell desired state Configuration-cmdlets</span><span class="sxs-lookup"><span data-stu-id="ab90b-239">Windows PowerShell Desired State Configuration Cmdlets</span></span>](/powershell/module/psdesiredstateconfiguration/)
