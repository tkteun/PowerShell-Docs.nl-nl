---
ms.date: 10/30/2018
keywords: DSC, Power shell, configuratie, installatie
title: Problemen met DSC oplossen
ms.openlocfilehash: 5cbe6496a6e0b9940f4b69e13d1e19e43b3915f0
ms.sourcegitcommit: 5f199cd2a1b31dbcebaab44f2fe496f289831a30
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77478782"
---
# <a name="troubleshooting-dsc"></a>Problemen met DSC oplossen

_Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0_

In dit onderwerp worden manieren beschreven om problemen met DSC op te lossen wanneer er problemen optreden.

## <a name="winrm-dependency"></a>WinRM-afhankelijkheid

Windows Power shell desired state Configuration (DSC) is afhankelijk van WinRM. WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 en Windows 7. Voer `Set-WSManQuickConfig`uit in een Windows Power shell-sessie met verhoogde bevoegdheden om WinRM in te scha kelen.

## <a name="using-get-dscconfigurationstatus"></a>Get-DscConfigurationStatus gebruiken

De cmdlet [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) krijgt informatie over de configuratie status van een doel knooppunt. Er wordt een uitgebreid object geretourneerd dat informatie op hoog niveau bevat over de vraag of de configuratie is geslaagd of niet. U kunt het object bekijken om details over de configuratie-uitvoering te detecteren, zoals:

- Alle resources die zijn mislukt
- Alle bronnen waarvoor opnieuw opstarten is aangevraagd
- Meta configuratie-instellingen op het moment van de configuratie-uitvoering
- Enz.

De volgende parameterset retourneert de status informatie voor de laatste configuratie-uitvoering:

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
De volgende parameterset retourneert de status informatie voor alle vorige configuratie-uitvoeringen:

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a>Voorbeeld

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

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>Mijn script wordt niet uitgevoerd: DSC-Logboeken gebruiken om script fouten te onderzoeken

Net als alle Windows-software registreert DSC fouten en gebeurtenissen in [Logboeken](/windows/desktop/EventLog/about-event-logging) die kunnen worden weer gegeven vanuit het [Logboeken](https://support.microsoft.com/hub/4338813/windows-help).
Door deze logboeken te controleren, kunt u beter begrijpen waarom een bepaalde bewerking niet kan worden uitgevoerd en hoe u fouten in de toekomst wilt voor komen. Het schrijven van configuratie scripts kan lastig zijn, zodat het bijhouden van fouten eenvoudiger is terwijl u zich aanmeldt, met behulp van de DSC-logboek bron om de voortgang van uw configuratie in het DSC-logboek voor analyse gebeurtenissen te volgen.

## <a name="where-are-dsc-event-logs"></a>Waar worden DSC-gebeurtenis logboeken?

In Logboeken bevinden DSC-gebeurtenissen zich in: **Logboeken van toepassingen en services/micro soft/Windows/desired state Configuration**

De bijbehorende Power shell-cmdlet [Get-Wine vent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)kan ook worden uitgevoerd om de gebeurtenis logboeken weer te geven:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

Zoals hierboven wordt weer gegeven, is de primaire logboek naam van DSC **micro soft > Windows-> DSC** (andere logboek namen onder Windows worden hier niet weer gegeven voor de boog). De primaire naam wordt toegevoegd aan de kanaal naam om de volledige logboek naam te maken. De DSC-engine schrijft voornamelijk in drie typen logboeken: [operationele, analyse en logboeken voor fout opsporing](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)). Aangezien de logboeken voor analyse en fout opsporing standaard zijn uitgeschakeld, moet u ze inschakelen in Logboeken. Als u dit wilt doen, opent u Logboeken door in Windows Power shell show-EventLog te typen. of klik op de knop **Start** , klik op **configuratie scherm**, klik op **systeem beheer**en klik vervolgens op **Logboeken**.
Klik in het menu **beeld** in Logboeken op **analyse logboeken en fout opsporing weer geven**. De logboek naam voor het analytische kanaal is **micro soft-Windows-DSC/analytic**en het fout opsporingsprogramma is **micro soft-Windows-DSC/debug**. U kunt ook het hulp programma [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) gebruiken om de logboeken in te scha kelen, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>Wat bevatten DSC-logboeken?

DSC-logboeken worden verdeeld over de drie logboek kanalen op basis van het belang van het bericht. Het operationele logboek in DSC bevat alle fout berichten en kan worden gebruikt om een probleem te identificeren. Het analytische logboek heeft een groter volume aan gebeurtenissen en kan identificeren waar fout (en) zijn opgetreden. Dit kanaal bevat ook uitgebreide berichten (indien van toepassing). Het logboek voor fout opsporing bevat logboeken die u kunnen helpen begrijpen hoe de fouten zijn opgetreden. DSC-gebeurtenis berichten zijn zodanig gestructureerd dat elk gebeurtenis bericht begint met een taak-ID die een DSC-bewerking uniek vertegenwoordigt. In het volgende voor beeld wordt geprobeerd het bericht te verkrijgen van de eerste gebeurtenis die is geregistreerd in het operationeel DSC-logboek.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

DSC-gebeurtenissen worden vastgelegd in een bepaalde structuur waarmee de gebruiker gebeurtenissen van één DSC-taak kan samen voegen. De structuur is als volgt:

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a>Gebeurtenissen van één DSC-bewerking verzamelen

DSC-gebeurtenis logboeken bevatten gebeurtenissen die door verschillende DSC-bewerkingen worden gegenereerd. Het is echter doorgaans een belang rijkere manier om een bepaalde bewerking uit te leggen. Alle DSC-logboeken kunnen worden gegroepeerd op de eigenschap voor de taak-ID die uniek is voor elke DSC-bewerking. De taak-ID wordt weer gegeven als de eerste eigenschaps waarde in alle DSC-gebeurtenissen. In de volgende stappen wordt uitgelegd hoe u alle gebeurtenissen in een gegroepeerde matrix structuur kunt samen voegen.

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

Hier bevat de variabele `$SeparateDscOperations` logboeken, gegroepeerd op de taak-Id's. Elk matrix element van deze variabele vertegenwoordigt een groep gebeurtenissen die zijn geregistreerd door een andere DSC-bewerking, waardoor er meer informatie over de logboeken kan worden geopend.

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

U kunt de gegevens in de variabele `$SeparateDscOperations` extra heren met behulp van [where-object](/powershell/module/microsoft.powershell.core/where-object). Hieronder volgen vijf scenario's waarin u mogelijk gegevens wilt ophalen voor het oplossen van problemen met DSC:

### <a name="1-operations-failures"></a>1: mislukte bewerkingen

Alle gebeurtenissen hebben [niveau Ernst](/windows/desktop/WES/defining-severity-levels). Deze informatie kan worden gebruikt om de fout gebeurtenissen te identificeren:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: Details van bewerkingen die in de afgelopen helft uur worden uitgevoerd

`TimeCreated`, een eigenschap van elke Windows-gebeurtenis, geeft de tijd aan waarop de gebeurtenis is gemaakt. Het vergelijken van deze eigenschap met een bepaald datum/tijd-object kan worden gebruikt om alle gebeurtenissen te filteren:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a>3: berichten van de laatste bewerking

De laatste bewerking wordt opgeslagen in de eerste index van de matrix groep `$SeparateDscOperations`.
Opvragen van de berichten van de groep voor index 0 retourneert alle berichten voor de meest recente bewerking:

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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: fout berichten geregistreerd voor recente mislukte bewerkingen

`$SeparateDscOperations[0].Group` bevat een set gebeurtenissen voor de laatste bewerking. Voer de `Where-Object` cmdlet uit om de gebeurtenissen te filteren op basis van de weergave naam van het niveau. De resultaten worden opgeslagen in de variabele `$myFailedEvent`, die verder kan worden ontladen om het gebeurtenis bericht op te halen:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: alle gebeurtenissen die zijn gegenereerd voor een bepaalde taak-ID.

`$SeparateDscOperations` is een matrix van groepen, die elk een naam hebben als de unieke taak-ID. Door de cmdlet `Where-Object` uit te voeren, kunt u deze groepen gebeurtenissen met een bepaalde taak-ID extra heren:

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>DSC-logboeken analyseren met behulp van xDscDiagnostics

**xDscDiagnostics** is een Power shell-module die bestaat uit verschillende functies waarmee DSC-fouten op uw machine kunnen worden geanalyseerd. Deze functies kunnen u helpen bij het identificeren van alle lokale gebeurtenissen van eerdere DSC-bewerkingen of DSC-gebeurtenissen op externe computers (met geldige referenties). Hier wordt de term DSC-bewerking gebruikt voor het definiëren van een enkele unieke DSC-uitvoering van het begin tot het einde. `Test-DscConfiguration` zou bijvoorbeeld een afzonderlijke DSC-bewerking zijn. Op dezelfde manier kunnen alle andere cmdlets in DSC (zoals `Get-DscConfiguration`, `Start-DscConfiguration`enz.) worden aangeduid als afzonderlijke DSC-bewerkingen. De functies worden beschreven op [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics). Help is beschikbaar door `Get-Help <cmdlet name>`uit te voeren.

### <a name="getting-details-of-dsc-operations"></a>Details van DSC-bewerkingen ophalen

Met de functie `Get-xDscOperation` kunt u de resultaten vinden van de DSC-bewerkingen die worden uitgevoerd op een of meer computers en wordt een object geretourneerd dat de verzameling gebeurtenissen bevat die door elke DSC-bewerking worden geproduceerd. In de volgende uitvoer zijn bijvoorbeeld drie opdrachten uitgevoerd. Het eerste dat is door gegeven en de andere twee is mislukt. Deze resultaten worden in de uitvoer van `Get-xDscOperation`samenvatten.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

U kunt ook opgeven dat u alleen de resultaten voor de meest recente bewerkingen wilt gebruiken met behulp van de para meter `Newest`:

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

### <a name="getting-details-of-dsc-events"></a>Details van DSC-gebeurtenissen ophalen

De cmdlet `Trace-xDscOperation` retourneert een object met een verzameling gebeurtenissen, hun gebeurtenis typen en de bericht uitvoer die is gegenereerd op basis van een bepaalde DSC-bewerking. Wanneer u bijvoorbeeld een fout in een van de bewerkingen met `Get-xDscOperation`ontdekt, zou u die bewerking traceren om erachter te komen welke van de gebeurtenissen een fout heeft veroorzaakt.

Gebruik de para meter `SequenceID` om de gebeurtenissen voor een specifieke bewerking voor een specifieke computer op te halen.
Als u bijvoorbeeld een `SequenceID` van 9 opgeeft, `Trace-xDscOperaion` de tracering ophalen voor de DSC-bewerking die als negende van de laatste bewerking is uitgevoerd:

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

Geef de **GUID** die is toegewezen aan een specifieke DSC-bewerking (zoals geretourneerd door de `Get-xDscOperation` cmdlet) door om de gebeurtenis Details voor die DSC-bewerking op te halen:

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

Houd er rekening mee dat, omdat `Trace-xDscOperation` gebeurtenissen samenvoegt vanuit de logboeken analyse, fouten opsporen en operationeel, wordt u gevraagd deze logboeken in te scha kelen, zoals hierboven beschreven.

U kunt ook informatie over de gebeurtenissen verzamelen door de uitvoer van `Trace-xDscOperation` in een variabele op te slaan. U kunt de volgende opdrachten gebruiken om alle gebeurtenissen voor een bepaalde DSC-bewerking weer te geven.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

Hiermee worden de resultaten weer gegeven als de cmdlet `Get-WinEvent`, zoals in de volgende uitvoer:

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

In het ideale geval gebruikt u `Get-xDscOperation` om de laatste DSC-configuratie uitgevoerd op uw computers uit te geven. Daarna kunt u een enkele bewerking (met behulp van de SequenceID of JobID) met `Trace-xDscOperation` bekijken om te ontdekken wat het achter de schermen heeft gedaan.

### <a name="getting-events-for-a-remote-computer"></a>Gebeurtenissen ophalen voor een externe computer

Gebruik de para meter `ComputerName` van de cmdlet `Trace-xDscOperation` om de gebeurtenis details op een externe computer op te halen. Voordat u dit kunt doen, moet u een firewall regel maken om extern beheer toe te staan op de externe computer:

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

Nu kunt u die computer opgeven in de aanroep van `Trace-xDscOperation`:

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Mijn resources worden niet bijgewerkt: de cache opnieuw instellen

De DSC-Engine slaat resources op die zijn geïmplementeerd als een Power shell-module voor efficiëntie doeleinden.
Dit kan er echter toe leiden dat er problemen zijn bij het ontwerpen van een resource en deze tegelijkertijd te testen, omdat DSC de versie in de cache laadt totdat het proces opnieuw wordt gestart. De enige manier om DSC-belasting te maken, is de nieuwere versie door het proces dat als host fungeert voor de DSC-engine expliciet te beëindigen.

En wanneer u `Start-DscConfiguration`uitvoert en u een aangepaste resource toevoegt en wijzigt, kan de wijziging niet worden uitgevoerd, tenzij of tot de computer opnieuw wordt opgestart. Dit komt doordat DSC wordt uitgevoerd in het hostproces van de WMI-provider (WmiPrvSE), en normaal gesp roken worden er veel exemplaren van WmiPrvSE tegelijk worden uitgevoerd. Wanneer u de computer opnieuw opstart, wordt het hostproces opnieuw gestart en wordt de cache gewist.

Als u de configuratie wilt herhalen en de cache wilt wissen zonder opnieuw op te starten, moet u het hostproces stoppen en opnieuw opstarten. Dit kan per instantie geschieden, waarbij u het proces identificeert en stopt, en het opnieuw start. U kunt ook `DebugMode`, zoals hieronder wordt geïllustreerd, gebruiken om de Power shell DSC-resource opnieuw te laden.

Als u wilt weten welk proces als host fungeert voor de DSC-engine en deze op per exemplaar wilt stoppen, kunt u de proces-ID van het WmiPrvSE weer geven dat als host fungeert voor de DSC-engine. Als u de provider wilt bijwerken, stopt u het WmiPrvSE-proces met de onderstaande opdrachten en voert u **Start-DscConfiguration** opnieuw uit.

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

## <a name="using-debugmode"></a>DebugMode gebruiken

U kunt de DSC Local Configuration Manager (LCM) configureren voor het gebruik van `DebugMode` om de cache altijd te wissen wanneer het hostproces opnieuw wordt gestart. Als deze eigenschap is ingesteld op **True**, wordt de Power shell DSC-resource altijd opnieuw geladen door de engine. Zodra u klaar bent met het schrijven van uw resource, kunt u deze weer instellen op **False** en wordt de engine teruggezet naar het gedrag van het opslaan van de modules in de cache.

Hier volgt een demonstratie om te laten zien hoe `DebugMode` de cache automatisch kunt vernieuwen. Laten we eerst de standaard configuratie bekijken:

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

U kunt zien dat `DebugMode` is ingesteld op **' geen '** .

Als u de `DebugMode` demonstratie wilt instellen, gebruikt u de volgende Power shell-resource:

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

Maak nu een configuratie met behulp van de bovenstaande resource met de naam `TestProviderDebugMode`:

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

U ziet dat de inhoud van het bestand: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` **1**is.

Werk nu de provider code bij met het volgende script:

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

Met dit script wordt een wille keurig getal gegenereerd en wordt de provider code dienovereenkomstig bijgewerkt. Als `DebugMode` is ingesteld op False, wordt de inhoud van het bestand ' **$env: SystemDrive\OutputFromTestProviderDebugMode.txt**' nooit gewijzigd.

Stel nu `DebugMode` in op **' ForceModuleImport '** in uw configuratie script:

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

Wanneer u het bovenstaande script opnieuw uitvoert, ziet u dat de inhoud van het bestand elke keer verschillend is. (U kunt `Get-DscConfiguration` uitvoeren om het te controleren). Hieronder ziet u het resultaat van twee extra uitvoeringen (uw resultaten kunnen verschillen als u het script uitvoert):

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

## <a name="dsc-returns-unexpected-response-code-internalservererror-when-registering-with-windows-pull-server"></a>DSC retourneert ' onverwachte respons code InternalServerError ' bij het registreren met een Windows pull-server

Wanneer u een-configuratie toepast op een server om deze te registreren met een exemplaar van Windows pull server, kan de volgende fout optreden.

```PowerShell
Registration of the Dsc Agent with the server https://<serverfqdn>:8080/PSDSCPullServer.svc failed. The underlying error is: The attempt to register Dsc Agent with AgentId <ID> with the server 
https://<serverfqdn>:8080/PSDSCPullServer.svc/Nodes(AgentId='<ID>') returned unexpected response code InternalServerError. .
    + CategoryInfo          : InvalidResult: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : RegisterDscAgentUnsuccessful,Microsoft.PowerShell.DesiredStateConfiguration.Commands.RegisterDscAgentCommand
    + PSComputerName        : <computername>
```

Dit kan gebeuren wanneer het certificaat dat op de server wordt gebruikt voor het versleutelen van verkeer, een algemene naam (CN) heeft die afwijkt van de DNS-naam die door het knoop punt wordt gebruikt om de URL op te lossen.
Werk het Windows pull Server-exemplaar bij om een certificaat met een herstelde naam te gebruiken.

## <a name="error-when-running-sysprep-after-applying-a-dsc-configuration"></a>Fout bij het uitvoeren van Sysprep na het Toep assen van een DSC-configuratie

Wanneer u probeert Sysprep uit te voeren om een Windows Server te generaliseren na het Toep assen van een DSC-configuratie, kan de volgende fout optreden.

```
SYSPRP LaunchDll:Failure occurred while executing 'DscCore.dll,SysPrep_Cleanup', returned error code 0x2
```

Het generaliseren van een server nadat deze is geconfigureerd met behulp van de desired state Configuration van Windows Power shell is geen ondersteund scenario.  Pas in plaats daarvan configuraties toe op Windows nadat de fase specialize van Windows Setup is voltooid.

## <a name="see-also"></a>Zie ook

### <a name="concepts"></a>Concepten

- [Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen](../resources/authoringResource.md)

### <a name="other-resources"></a>Meer informatie

- [Windows Power shell desired state Configuration-cmdlets](/powershell/module/psdesiredstateconfiguration/)
