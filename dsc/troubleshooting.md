---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Problemen met DSC oplossen
ms.openlocfilehash: 6bb639febc3f413e909c3e61559059adb5c96389
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="f0b40-103">Problemen met DSC oplossen</span><span class="sxs-lookup"><span data-stu-id="f0b40-103">Troubleshooting DSC</span></span>

><span data-ttu-id="f0b40-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f0b40-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f0b40-105">In dit onderwerp wordt beschreven hoe DSC oplossen wanneer er zich problemen voordoen.</span><span class="sxs-lookup"><span data-stu-id="f0b40-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="f0b40-106">WinRM-afhankelijkheid</span><span class="sxs-lookup"><span data-stu-id="f0b40-106">WinRM Dependency</span></span>

<span data-ttu-id="f0b40-107">Windows PowerShell Desired State Configuration (DSC), is afhankelijk van WinRM.</span><span class="sxs-lookup"><span data-stu-id="f0b40-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="f0b40-108">WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 en Windows 7.</span><span class="sxs-lookup"><span data-stu-id="f0b40-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="f0b40-109">Voer ```Set-WSManQuickConfig```, in een Windows PowerShell met verhoogde bevoegdheden voor het inschakelen van de WinRM-sessie.</span><span class="sxs-lookup"><span data-stu-id="f0b40-109">Run ```Set-WSManQuickConfig```, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="f0b40-110">Gebruik Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="f0b40-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="f0b40-111">De [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet Hiermee haalt u informatie over de configuratiestatus van de van een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="f0b40-111">The [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet gets information about configuration status from a target node.</span></span>
<span data-ttu-id="f0b40-112">Een uitgebreide object wordt geretourneerd die bevat belangrijke informatie over het uitvoeren van de configuratie al dan niet geslaagd of mislukt is.</span><span class="sxs-lookup"><span data-stu-id="f0b40-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="f0b40-113">U kunt verdiepen in het object voor het detecteren van gegevens over de configuratie uitvoeren zoals:</span><span class="sxs-lookup"><span data-stu-id="f0b40-113">You can dig into the object to discover details about the configuration run such as:</span></span>

* <span data-ttu-id="f0b40-114">Alle resources die niet zijn geslaagd</span><span class="sxs-lookup"><span data-stu-id="f0b40-114">All of the resources that failed</span></span>
* <span data-ttu-id="f0b40-115">Een resource die opnieuw worden opgestart aangevraagd</span><span class="sxs-lookup"><span data-stu-id="f0b40-115">Any resource that requested a reboot</span></span>
* <span data-ttu-id="f0b40-116">META-configuratie-instellingen op het moment van de configuratie uitvoeren</span><span class="sxs-lookup"><span data-stu-id="f0b40-116">Meta-Configuration settings at time of configuration run</span></span>
* <span data-ttu-id="f0b40-117">enz.</span><span class="sxs-lookup"><span data-stu-id="f0b40-117">Etc.</span></span>

<span data-ttu-id="f0b40-118">De volgende parameter ingesteld retourneert de statusinformatie voor de laatste configuratie uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="f0b40-118">The following parameter set returns the status information for the last configuration run:</span></span>

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```
<span data-ttu-id="f0b40-119">De volgende parameter ingesteld retourneert de statusinformatie voor alle voorgaande configuratie wordt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="f0b40-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```powershell
Get-DscConfigurationStatus  -All
                            [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="f0b40-120">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f0b40-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :
InDesiredState          :   False
InitialState            :
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="f0b40-121">Mijn script niet uitgevoerd: DSC met behulp van de logboeken voor analyseren scriptfouten</span><span class="sxs-lookup"><span data-stu-id="f0b40-121">My script won’t run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="f0b40-122">Net als alle Windows-software, DSC registreert fouten en gebeurtenissen in [logboeken](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) die kan worden bekeken in de [logboeken](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span><span class="sxs-lookup"><span data-stu-id="f0b40-122">Like all Windows software, DSC records errors and events in [logs](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) that can be viewed from the [Event Viewer](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span></span> <span data-ttu-id="f0b40-123">Deze logboeken onderzoeken kan u helpen begrijpen waarom een bepaalde bewerking is mislukt en fout in de toekomst te voorkomen.</span><span class="sxs-lookup"><span data-stu-id="f0b40-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="f0b40-124">Configuratiescripts schrijven is lastig, dus als u wilt bijhouden fouten gemakkelijker als u de auteur van, de DSC-logboek bron gebruiken voor het bijhouden van de voortgang van uw configuratie in het gebeurtenislogboek van DSC-analyse.</span><span class="sxs-lookup"><span data-stu-id="f0b40-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="f0b40-125">Waar zijn de gebeurtenislogboeken DSC?</span><span class="sxs-lookup"><span data-stu-id="f0b40-125">Where are DSC event logs?</span></span>

<span data-ttu-id="f0b40-126">In Logboeken DSC gebeurtenissen zich in: **toepassingen en Services Logboeken/Microsoft/Windows/gewenst State Configuration**</span><span class="sxs-lookup"><span data-stu-id="f0b40-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="f0b40-127">De bijbehorende PowerShell-cmdlet [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), kunnen ook worden uitgevoerd om de gebeurtenislogboeken weer te geven:</span><span class="sxs-lookup"><span data-stu-id="f0b40-127">The corresponding PowerShell cmdlet, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="f0b40-128">Zoals hierboven beschreven, de naam van de primaire logboek van DSC is **Microsoft Windows -> DSC ->** (andere logboeknamen onder Windows worden hier niet weergegeven als beknopt alternatief bevat).</span><span class="sxs-lookup"><span data-stu-id="f0b40-128">As shown above, DSC’s primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="f0b40-129">De naam van de primaire wordt toegevoegd aan de naam van het kanaal te maken van de naam van het volledige logboek.</span><span class="sxs-lookup"><span data-stu-id="f0b40-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="f0b40-130">De DSC-engine schrijft voornamelijk in drie verschillende typen logboeken: [operationeel, analyse en foutopsporing logboeken](https://technet.microsoft.com/library/cc722404.aspx).</span><span class="sxs-lookup"><span data-stu-id="f0b40-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](https://technet.microsoft.com/library/cc722404.aspx).</span></span> <span data-ttu-id="f0b40-131">Sinds de analytische en logboeken voor foutopsporing zijn standaard uitgeschakeld, moet u ze inschakelen in Logboeken.</span><span class="sxs-lookup"><span data-stu-id="f0b40-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="f0b40-132">U doet dit door Logboeken te openen door te typen weergeven gebeurtenislogboek in Windows PowerShell; of klik op de **Start** klikken, klik op **Configuratiescherm**, klikt u op **Systeembeheer**, en klik vervolgens op **logboeken**.</span><span class="sxs-lookup"><span data-stu-id="f0b40-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span> <span data-ttu-id="f0b40-133">Op de **weergave** menu in Logboeken, klikt u op **analytische weergeven logboeken en foutopsporing**.</span><span class="sxs-lookup"><span data-stu-id="f0b40-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="f0b40-134">De naam van het logboek voor de analytic channel is **Microsoft-Windows-Dsc/analysen**, en het kanaal foutopsporing **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="f0b40-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="f0b40-135">U kunt ook de [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) hulpprogramma voor het inschakelen van de logboeken, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="f0b40-135">You could also use the [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="f0b40-136">Wat bevatten de logboeken van de DSC?</span><span class="sxs-lookup"><span data-stu-id="f0b40-136">What do DSC logs contain?</span></span>

<span data-ttu-id="f0b40-137">DSC-logboeken worden gesplitst via de drie logboekkanalen op basis van het belang van het bericht.</span><span class="sxs-lookup"><span data-stu-id="f0b40-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="f0b40-138">Het operationele logboek in DSC bevat alle foutberichten en kan worden gebruikt om een probleem te identificeren.</span><span class="sxs-lookup"><span data-stu-id="f0b40-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="f0b40-139">Het analytische logboek heeft een groter volume van gebeurtenissen en kunt identificeren waar is een fout opgetreden.</span><span class="sxs-lookup"><span data-stu-id="f0b40-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="f0b40-140">Dit kanaal bevat ook uitgebreide berichten (indien aanwezig).</span><span class="sxs-lookup"><span data-stu-id="f0b40-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="f0b40-141">Het logboek voor foutopsporing bevat de logboeken die kunnen u helpen begrijpen hoe de fouten zijn opgetreden.</span><span class="sxs-lookup"><span data-stu-id="f0b40-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="f0b40-142">DSC-gebeurtenisberichten structuur zo dat elke gebeurtenisbericht begint met een taak-ID die een unieke een DSC-bewerking vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f0b40-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="f0b40-143">Het onderstaande voorbeeld probeert te verkrijgen van het bericht uit de eerste gebeurtenis vastgelegd in het operationele logboek van DSC.</span><span class="sxs-lookup"><span data-stu-id="f0b40-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="f0b40-144">DSC-gebeurtenissen worden vastgelegd in een bepaalde structuur waarmee de gebruiker te verzamelen van gegevens uit een DSC-taak.</span><span class="sxs-lookup"><span data-stu-id="f0b40-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="f0b40-145">De structuur is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f0b40-145">The structure is as follows:</span></span>

<span data-ttu-id="f0b40-146">**Taak-ID: <Guid>**
**<Event Message>**</span><span class="sxs-lookup"><span data-stu-id="f0b40-146">**Job ID : <Guid>**
**<Event Message>**</span></span>

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="f0b40-147">Verzamelen van gebeurtenissen van een enkele DSC-bewerking</span><span class="sxs-lookup"><span data-stu-id="f0b40-147">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="f0b40-148">DSC-gebeurtenislogboeken bevatten gebeurtenissen die worden gegenereerd door verschillende DSC-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="f0b40-148">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="f0b40-149">Echter, u meestal zult betrokken zijn bij de details over een bepaalde bewerking.</span><span class="sxs-lookup"><span data-stu-id="f0b40-149">However, you’ll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="f0b40-150">Alle DSC-logboeken kunnen worden gegroepeerd door de taak-ID-eigenschap die uniek is voor elke DSC-bewerking.</span><span class="sxs-lookup"><span data-stu-id="f0b40-150">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="f0b40-151">De taak-ID wordt weergegeven als de eerste eigenschapswaarde in alle DSC-gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="f0b40-151">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="f0b40-152">De volgende stappen wordt uitgelegd hoe verzamelt alle gebeurtenissen in een structuur matrix gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="f0b40-152">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true

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

<span data-ttu-id="f0b40-153">Hier wordt de variabele `$SeparateDscOperations` logboeken gegroepeerd op de taak-id's bevat.</span><span class="sxs-lookup"><span data-stu-id="f0b40-153">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="f0b40-154">Elk matrixelement van deze variabele vertegenwoordigt een groep gebeurtenissen vastgelegd door een andere bewerking van het DSC toestaan van toegang tot meer informatie over de logboeken.</span><span class="sxs-lookup"><span data-stu-id="f0b40-154">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

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

<span data-ttu-id="f0b40-155">U kunt de gegevens in de variabele uitpakken `$SeparateDscOperations` met [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span><span class="sxs-lookup"><span data-stu-id="f0b40-155">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span></span> <span data-ttu-id="f0b40-156">Hieronder vindt u vijf scenario's waarin u wilt mogelijk om gegevens voor het oplossen van DSC te extraheren:</span><span class="sxs-lookup"><span data-stu-id="f0b40-156">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="f0b40-157">1: operations fouten</span><span class="sxs-lookup"><span data-stu-id="f0b40-157">1: Operations failures</span></span>

<span data-ttu-id="f0b40-158">Alle gebeurtenissen hebben [ernstniveaus](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f0b40-158">All events have [severity levels](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span></span> <span data-ttu-id="f0b40-159">Deze informatie kan worden gebruikt voor het identificeren van de foutgebeurtenissen:</span><span class="sxs-lookup"><span data-stu-id="f0b40-159">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="f0b40-160">2: details van bewerkingen uitvoeren in het laatste half uur</span><span class="sxs-lookup"><span data-stu-id="f0b40-160">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="f0b40-161">`TimeCreated`, een eigenschap van elke Windows-gebeurtenis bepaalt het moment dat de gebeurtenis is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f0b40-161">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="f0b40-162">Het vergelijken van deze eigenschap met een bepaalde datum/tijd-object kan worden gebruikt om alle gebeurtenissen te filteren:</span><span class="sxs-lookup"><span data-stu-id="f0b40-162">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="f0b40-163">3: berichten van de meest recente bewerking</span><span class="sxs-lookup"><span data-stu-id="f0b40-163">3: Messages from the latest operation</span></span>

<span data-ttu-id="f0b40-164">De meest recente bewerking wordt opgeslagen in de eerste index van de matrixgroep `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="f0b40-164">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span> <span data-ttu-id="f0b40-165">Opvragen van berichten voor index 0 van de groep retourneert alle berichten voor de meest recente bewerking:</span><span class="sxs-lookup"><span data-stu-id="f0b40-165">Querying the group’s messages for index 0 returns all messages for the latest operation:</span></span>

```powershelll
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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="f0b40-166">4: foutberichten voor mislukte bewerkingen die recent zijn geregistreerd</span><span class="sxs-lookup"><span data-stu-id="f0b40-166">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="f0b40-167">`$SeparateDscOperations[0].Group` bevat een reeks gebeurtenissen voor de meest recente bewerking.</span><span class="sxs-lookup"><span data-stu-id="f0b40-167">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="f0b40-168">Voer de `Where-Object` cmdlet om de gebeurtenissen te filteren op basis van hun niveau weergavenaam.</span><span class="sxs-lookup"><span data-stu-id="f0b40-168">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="f0b40-169">Resultaten worden opgeslagen in de `$myFailedEvent` variabele, die verder kan worden opgesplitst om het gebeurtenisbericht weergegeven:</span><span class="sxs-lookup"><span data-stu-id="f0b40-169">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="f0b40-170">5: alle gebeurtenissen die worden gegenereerd voor een bepaalde taak-ID.</span><span class="sxs-lookup"><span data-stu-id="f0b40-170">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="f0b40-171">`$SeparateDscOperations` is een matrix van groepen, elk met de naam als de unieke taak-ID heeft.</span><span class="sxs-lookup"><span data-stu-id="f0b40-171">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="f0b40-172">Door het uitvoeren van de `Where-Object` cmdlet, kunt u deze groepen van gebeurtenissen die gedurende een bepaalde taak-ID hebben uitpakken:</span><span class="sxs-lookup"><span data-stu-id="f0b40-172">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="f0b40-173">Logboeken met behulp van xDscDiagnostics DSC analyseren</span><span class="sxs-lookup"><span data-stu-id="f0b40-173">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="f0b40-174">**xDscDiagnostics** is een PowerShell-module die bestaat uit verschillende functies die kunnen helpen bij het analyseren van DSC-fouten op uw computer.</span><span class="sxs-lookup"><span data-stu-id="f0b40-174">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="f0b40-175">Deze functies kunt u alle lokale gebeurtenissen van afgelopen DSC-bewerkingen of DSC-gebeurtenissen op externe computers identificeren (met geldige referenties).</span><span class="sxs-lookup"><span data-stu-id="f0b40-175">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="f0b40-176">Hier wordt de term DSC-bewerking gebruikt voor het definiëren van één unieke DSC uitvoering vanaf het begin tot het einde.</span><span class="sxs-lookup"><span data-stu-id="f0b40-176">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="f0b40-177">Bijvoorbeeld: `Test-DscConfiguration` is een afzonderlijke DSC-bewerking.</span><span class="sxs-lookup"><span data-stu-id="f0b40-177">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="f0b40-178">Op deze manier elke andere cmdlet in DSC (zoals `Get-DscConfiguration`, `Start-DscConfiguration`, enzovoort) elk worden geïdentificeerd als afzonderlijke DSC-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="f0b40-178">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="f0b40-179">De functies worden beschreven op [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="f0b40-179">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span>
<span data-ttu-id="f0b40-180">Hulp is beschikbaar door het uitvoeren van `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="f0b40-180">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="f0b40-181">Details van DSC-bewerkingen ophalen</span><span class="sxs-lookup"><span data-stu-id="f0b40-181">Getting details of DSC operations</span></span>

<span data-ttu-id="f0b40-182">De `Get-xDscOperation` functie kunt u de resultaten van de DSC-bewerkingen die worden uitgevoerd op een of meerdere computers vinden en retourneert een object dat het verzamelen van gebeurtenissen bevat die wordt geproduceerd door elke DSC-bewerking.</span><span class="sxs-lookup"><span data-stu-id="f0b40-182">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span>
<span data-ttu-id="f0b40-183">In de volgende uitvoer kan drie opdrachten zijn uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f0b40-183">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="f0b40-184">Het eerste werd doorgegeven en de andere twee is mislukt.</span><span class="sxs-lookup"><span data-stu-id="f0b40-184">The first one passed, and the other two failed.</span></span> <span data-ttu-id="f0b40-185">Deze resultaten worden samengevat in de uitvoer van `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="f0b40-185">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...

```

<span data-ttu-id="f0b40-186">U kunt ook opgeven dat u alleen resultaten voor de meest recente bewerkingen met behulp van wilt de `Newest` parameter:</span><span class="sxs-lookup"><span data-stu-id="f0b40-186">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

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

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="f0b40-187">Details van gebeurtenissen voor DSC ophalen</span><span class="sxs-lookup"><span data-stu-id="f0b40-187">Getting details of DSC events</span></span>

<span data-ttu-id="f0b40-188">De `Trace-xDscOperation` cmdlet retourneert een object met een verzameling van gebeurtenissen, hun typen gebeurtenissen en het bericht uitvoer gegenereerd op basis van een bepaalde DSC-bewerking.</span><span class="sxs-lookup"><span data-stu-id="f0b40-188">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="f0b40-189">Normaal gesproken als u merkt dat een storing in een van de bewerkingen met behulp van `Get-xDscOperation`, u wilt traceren die voor deze bewerking om erachter te komen welke van de gebeurtenissen heeft een fout veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="f0b40-189">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="f0b40-190">Gebruik de `SequenceID` -parameter voor het ophalen van de gebeurtenissen voor een specifieke bewerking voor een specifieke computer.</span><span class="sxs-lookup"><span data-stu-id="f0b40-190">Use the  `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span> <span data-ttu-id="f0b40-191">Als u bijvoorbeeld een `SequenceID` van 9, `Trace-xDscOperaion` ophalen van de tracering voor de DSC-bewerking die werd 9de van de laatste bewerking:</span><span class="sxs-lookup"><span data-stu-id="f0b40-191">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

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

<span data-ttu-id="f0b40-192">Geeft de **GUID** toegewezen aan een specifieke DSC-bewerking (geretourneerd door de `Get-xDscOperation` cmldet) details van de gebeurtenis voor die bewerking DSC ophalen:</span><span class="sxs-lookup"><span data-stu-id="f0b40-192">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmldet) to get the event details for that DSC operation:</span></span>

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

<span data-ttu-id="f0b40-193">Merk op dat, aangezien `Trace-xDscOperation` cumuleert de gebeurtenissen van de analyse, foutopsporing, en operationele Logboeken, wordt gevraagd u deze logboeken inschakelen, zoals hierboven is beschreven.</span><span class="sxs-lookup"><span data-stu-id="f0b40-193">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="f0b40-194">Ook kunt u informatie over de gebeurtenissen verzamelen door het opslaan van de uitvoer van `Trace-xDscOperation` in een variabele.</span><span class="sxs-lookup"><span data-stu-id="f0b40-194">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="f0b40-195">U kunt de volgende opdrachten gebruiken om alle gebeurtenissen voor een bepaalde DSC-bewerking weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f0b40-195">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="f0b40-196">Hiermee wordt weergegeven dat hetzelfde resultaat als de `Get-WinEvent` cmdlet, zoals in de onderstaande uitvoer:</span><span class="sxs-lookup"><span data-stu-id="f0b40-196">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```powershell
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

<span data-ttu-id="f0b40-197">Eerst gebruikt u in het ideale geval `Get-xDscOperation` om weer te geven van de laatste paar DSC configuratie wordt uitgevoerd op uw computers.</span><span class="sxs-lookup"><span data-stu-id="f0b40-197">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="f0b40-198">Na dit, kunt u een enkele bewerking (met de SequenceID of JobID) bestuderen met `Trace-xDscOperation` te detecteren die gold achter de schermen.</span><span class="sxs-lookup"><span data-stu-id="f0b40-198">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="f0b40-199">Ophalen van gebeurtenissen voor een externe computer</span><span class="sxs-lookup"><span data-stu-id="f0b40-199">Getting events for a remote computer</span></span>

<span data-ttu-id="f0b40-200">Gebruik de `ComputerName` parameter van de `Trace-xDscOperation` cmdlet details van de gebeurtenis ophalen op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="f0b40-200">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="f0b40-201">Voordat u dit doen kunt, hebt u een firewallregel extern beheer toestaan op de externe computer maken:</span><span class="sxs-lookup"><span data-stu-id="f0b40-201">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
<span data-ttu-id="f0b40-202">Nu kunt u die computer in de aanroep van `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="f0b40-202">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="f0b40-203">Mijn resources niet bijgewerkt: het opnieuw instellen van de cache</span><span class="sxs-lookup"><span data-stu-id="f0b40-203">My resources won’t update: How to reset the cache</span></span>

<span data-ttu-id="f0b40-204">De DSC-engine in de cache opslaat voor resources die zijn geïmplementeerd als een PowerShell-module voor efficiëntie doeleinden.</span><span class="sxs-lookup"><span data-stu-id="f0b40-204">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span> <span data-ttu-id="f0b40-205">Dit kan echter problemen veroorzaken bij het ontwerpen van een resource en tegelijkertijd testen omdat DSC versie in de cache wordt geladen totdat het proces opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="f0b40-205">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="f0b40-206">De enige manier om DSC laden van de nieuwere versie is het proces voor het hosten van de DSC-engine expliciet afsluiten.</span><span class="sxs-lookup"><span data-stu-id="f0b40-206">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="f0b40-207">Op deze manier bij het uitvoeren van `Start-DscConfiguration`, na het toevoegen en wijzigen van een aangepaste bron, de wijziging mogelijk niet uitgevoerd tenzij of tot, de computer opnieuw wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="f0b40-207">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="f0b40-208">Dit komt doordat DSC in het hostproces van de WMI-Provider (WmiPrvSE) wordt uitgevoerd en er zijn meestal veel exemplaren van WmiPrvSE tegelijk worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f0b40-208">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="f0b40-209">Wanneer u het opnieuw opstarten, het hostproces opnieuw is opgestart en de cache is leeggemaakt.</span><span class="sxs-lookup"><span data-stu-id="f0b40-209">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="f0b40-210">Om te recyclen van de configuratie en de cache wissen zonder opnieuw opstarten, moet u stoppen en vervolgens het hostproces opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="f0b40-210">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="f0b40-211">Dit kan worden gedaan op een basis per exemplaar, waarbij u het proces te identificeren, stoppen en opnieuw starten.</span><span class="sxs-lookup"><span data-stu-id="f0b40-211">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="f0b40-212">Of u kunt `DebugMode`, zoals hieronder wordt gedemonstreerd opnieuw laden van de PowerShell DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="f0b40-212">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="f0b40-213">Om te bepalen welk proces als host fungeert voor de DSC-engine en stop de toepassing op basis van per exemplaar, kunt u de proces-ID van de WmiPrvSE die als host voor de DSC-engine fungeert aanbieden.</span><span class="sxs-lookup"><span data-stu-id="f0b40-213">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="f0b40-214">Stop vervolgens, voor het bijwerken van de provider de WmiPrvSE proces met behulp van de onderstaande opdrachten en voer **Start DscConfiguration** opnieuw.</span><span class="sxs-lookup"><span data-stu-id="f0b40-214">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

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

## <a name="using-debugmode"></a><span data-ttu-id="f0b40-215">Met behulp van fouten opsporen-modus</span><span class="sxs-lookup"><span data-stu-id="f0b40-215">Using DebugMode</span></span>

<span data-ttu-id="f0b40-216">U kunt de DSC lokale Configuration Manager (LCM) te gebruiken `DebugMode` altijd de cache wissen wanneer het hostproces opnieuw is gestart.</span><span class="sxs-lookup"><span data-stu-id="f0b40-216">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="f0b40-217">Als de waarde **TRUE**, het ervoor zorgt dat de engine altijd opnieuw laden van de PowerShell DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="f0b40-217">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="f0b40-218">Wanneer u klaar bent u schrijft de bron, kunt u dit instellen terug naar **FALSE** en de engine voor het gedrag van de modules in het cachegeheugen worden hersteld.</span><span class="sxs-lookup"><span data-stu-id="f0b40-218">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="f0b40-219">Hieronder vindt u een demonstratie om weer te geven hoe `DebugMode` kunnen automatisch worden vernieuwd met de cache.</span><span class="sxs-lookup"><span data-stu-id="f0b40-219">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="f0b40-220">Eerst bekijken we de standaardconfiguratie:</span><span class="sxs-lookup"><span data-stu-id="f0b40-220">First, let’s look at the default configuration:</span></span>

```
PS C:\> Get-DscLocalConfigurationManager


AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : False
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="f0b40-221">Kunt u zien dat `DebugMode` is ingesteld op **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="f0b40-221">You can see that `DebugMode` is set to **FALSE**.</span></span>

<span data-ttu-id="f0b40-222">Voor het instellen van de `DebugMode` demonstreren, gebruikt u de volgende PowerShell-resource:</span><span class="sxs-lookup"><span data-stu-id="f0b40-222">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

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

<span data-ttu-id="f0b40-223">Schrijf nu een configuratie met behulp van de bovenstaande resource aangeroepen `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="f0b40-223">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

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

<span data-ttu-id="f0b40-224">U ziet dat de inhoud van bestand: '**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**' is **1**.</span><span class="sxs-lookup"><span data-stu-id="f0b40-224">You will see that the contents of file: “**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” is **1**.</span></span>

<span data-ttu-id="f0b40-225">Werk nu de code van de provider door het volgende script:</span><span class="sxs-lookup"><span data-stu-id="f0b40-225">Now, update the provider code using the following script:</span></span>

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

<span data-ttu-id="f0b40-226">Dit script genereert een willekeurig getal en de code van de provider dienovereenkomstig bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="f0b40-226">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="f0b40-227">Met `DebugMode` ingesteld op false, de inhoud van het bestand '**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**' nooit worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f0b40-227">With `DebugMode` set to false, the contents of the file “**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” are never changed.</span></span>

<span data-ttu-id="f0b40-228">Nu ingesteld `DebugMode` naar **TRUE** in uw configuratiescript:</span><span class="sxs-lookup"><span data-stu-id="f0b40-228">Now, set `DebugMode` to **TRUE** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = $true
}
```

<span data-ttu-id="f0b40-229">Als u de bovenstaande script opnieuw uitvoert, ziet u dat de inhoud van het bestand anders elke keer is.</span><span class="sxs-lookup"><span data-stu-id="f0b40-229">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="f0b40-230">(U kunt uitvoeren `Get-DscConfiguration` wilt controleren op het).</span><span class="sxs-lookup"><span data-stu-id="f0b40-230">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="f0b40-231">Hieronder volgt het resultaat van de twee extra wordt uitgevoerd (de resultaten mogelijk andere wanneer u het script uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="f0b40-231">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f0b40-232">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f0b40-232">See Also</span></span>

### <a name="reference"></a><span data-ttu-id="f0b40-233">Verwijzing</span><span class="sxs-lookup"><span data-stu-id="f0b40-233">Reference</span></span>
* [<span data-ttu-id="f0b40-234">Logboek van de DSC-Resource</span><span class="sxs-lookup"><span data-stu-id="f0b40-234">DSC Log Resource</span></span>](logResource.md)

### <a name="concepts"></a><span data-ttu-id="f0b40-235">Concepten</span><span class="sxs-lookup"><span data-stu-id="f0b40-235">Concepts</span></span>
* [<span data-ttu-id="f0b40-236">Aangepaste Windows PowerShell Desired State Configuration Resources bouwen</span><span class="sxs-lookup"><span data-stu-id="f0b40-236">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="f0b40-237">Andere bronnen</span><span class="sxs-lookup"><span data-stu-id="f0b40-237">Other Resources</span></span>
* <span data-ttu-id="f0b40-238">[Windows PowerShell Desired State Configuration-Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="f0b40-238">[Windows PowerShell Desired State Configuration Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span></span>