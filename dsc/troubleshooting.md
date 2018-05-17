---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Problemen met DSC oplossen
ms.openlocfilehash: c08f91b514aae438578fa278228fe5ec879a4012
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="troubleshooting-dsc"></a>Problemen met DSC oplossen

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

In dit onderwerp wordt beschreven hoe DSC oplossen wanneer er zich problemen voordoen.

## <a name="winrm-dependency"></a>WinRM-afhankelijkheid

Windows PowerShell Desired State Configuration (DSC), is afhankelijk van WinRM. WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 en Windows 7. Voer ```Set-WSManQuickConfig```, in een Windows PowerShell met verhoogde bevoegdheden voor het inschakelen van de WinRM-sessie.

## <a name="using-get-dscconfigurationstatus"></a>Gebruik Get-DscConfigurationStatus

De [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet Hiermee haalt u informatie over de configuratiestatus van de van een doelknooppunt.
Een uitgebreide object wordt geretourneerd die bevat belangrijke informatie over het uitvoeren van de configuratie al dan niet geslaagd of mislukt is. U kunt verdiepen in het object voor het detecteren van gegevens over de configuratie uitvoeren zoals:

* Alle resources die niet zijn geslaagd
* Een resource die opnieuw worden opgestart aangevraagd
* META-configuratie-instellingen op het moment van de configuratie uitvoeren
* enz.

De volgende parameter ingesteld retourneert de statusinformatie voor de laatste configuratie uitvoeren:

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```
De volgende parameter ingesteld retourneert de statusinformatie voor alle voorgaande configuratie wordt uitgevoerd:

```powershell
Get-DscConfigurationStatus  -All
                            [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```

## <a name="example"></a>Voorbeeld

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

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>Mijn script niet uitgevoerd: DSC met behulp van de logboeken voor analyseren scriptfouten

Net als alle Windows-software, DSC registreert fouten en gebeurtenissen in [logboeken](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) die kan worden bekeken in de [logboeken](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer). Deze logboeken onderzoeken kan u helpen begrijpen waarom een bepaalde bewerking is mislukt en fout in de toekomst te voorkomen. Configuratiescripts schrijven is lastig, dus als u wilt bijhouden fouten gemakkelijker als u de auteur van, de DSC-logboek bron gebruiken voor het bijhouden van de voortgang van uw configuratie in het gebeurtenislogboek van DSC-analyse.

## <a name="where-are-dsc-event-logs"></a>Waar zijn de gebeurtenislogboeken DSC?

In Logboeken DSC gebeurtenissen zich in: **toepassingen en Services Logboeken/Microsoft/Windows/gewenst State Configuration**

De bijbehorende PowerShell-cmdlet [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), kunnen ook worden uitgevoerd om de gebeurtenislogboeken weer te geven:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

Zoals hierboven beschreven, de naam van de primaire logboek van DSC is **Microsoft Windows -> DSC ->** (andere logboeknamen onder Windows worden hier niet weergegeven als beknopt alternatief bevat). De naam van de primaire wordt toegevoegd aan de naam van het kanaal te maken van de naam van het volledige logboek. De DSC-engine schrijft voornamelijk in drie verschillende typen logboeken: [operationeel, analyse en foutopsporing logboeken](https://technet.microsoft.com/library/cc722404.aspx). Sinds de analytische en logboeken voor foutopsporing zijn standaard uitgeschakeld, moet u ze inschakelen in Logboeken. U doet dit door Logboeken te openen door te typen weergeven gebeurtenislogboek in Windows PowerShell; of klik op de **Start** klikken, klik op **Configuratiescherm**, klikt u op **Systeembeheer**, en klik vervolgens op **logboeken**. Op de **weergave** menu in Logboeken, klikt u op **analytische weergeven logboeken en foutopsporing**. De naam van het logboek voor de analytic channel is **Microsoft-Windows-Dsc/analysen**, en het kanaal foutopsporing **Microsoft-Windows-Dsc/Debug**. U kunt ook de [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) hulpprogramma voor het inschakelen van de logboeken, zoals wordt weergegeven in het volgende voorbeeld.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>Wat bevatten de logboeken van de DSC?

DSC-logboeken worden gesplitst via de drie logboekkanalen op basis van het belang van het bericht. Het operationele logboek in DSC bevat alle foutberichten en kan worden gebruikt om een probleem te identificeren. Het analytische logboek heeft een groter volume van gebeurtenissen en kunt identificeren waar is een fout opgetreden. Dit kanaal bevat ook uitgebreide berichten (indien aanwezig). Het logboek voor foutopsporing bevat de logboeken die kunnen u helpen begrijpen hoe de fouten zijn opgetreden. DSC-gebeurtenisberichten structuur zo dat elke gebeurtenisbericht begint met een taak-ID die een unieke een DSC-bewerking vertegenwoordigt. Het onderstaande voorbeeld probeert te verkrijgen van het bericht uit de eerste gebeurtenis vastgelegd in het operationele logboek van DSC.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

DSC-gebeurtenissen worden vastgelegd in een bepaalde structuur waarmee de gebruiker te verzamelen van gegevens uit een DSC-taak. De structuur is als volgt:

**Taak-ID: <Guid>**
**<Event Message>**

## <a name="gathering-events-from-a-single-dsc-operation"></a>Verzamelen van gebeurtenissen van een enkele DSC-bewerking

DSC-gebeurtenislogboeken bevatten gebeurtenissen die worden gegenereerd door verschillende DSC-bewerkingen. Echter, u meestal zult betrokken zijn bij de details over een bepaalde bewerking. Alle DSC-logboeken kunnen worden gegroepeerd door de taak-ID-eigenschap die uniek is voor elke DSC-bewerking. De taak-ID wordt weergegeven als de eerste eigenschapswaarde in alle DSC-gebeurtenissen. De volgende stappen wordt uitgelegd hoe verzamelt alle gebeurtenissen in een structuur matrix gegroepeerd.

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

Hier wordt de variabele `$SeparateDscOperations` logboeken gegroepeerd op de taak-id's bevat. Elk matrixelement van deze variabele vertegenwoordigt een groep gebeurtenissen vastgelegd door een andere bewerking van het DSC toestaan van toegang tot meer informatie over de logboeken.

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

U kunt de gegevens in de variabele uitpakken `$SeparateDscOperations` met [Where-Object](https://technet.microsoft.com/library/ee177028.aspx). Hieronder vindt u vijf scenario's waarin u wilt mogelijk om gegevens voor het oplossen van DSC te extraheren:

### <a name="1-operations-failures"></a>1: operations fouten

Alle gebeurtenissen hebben [ernstniveaus](https://msdn.microsoft.com/library/dd996917(v=vs.85)). Deze informatie kan worden gebruikt voor het identificeren van de foutgebeurtenissen:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: details van bewerkingen uitvoeren in het laatste half uur

`TimeCreated`, een eigenschap van elke Windows-gebeurtenis bepaalt het moment dat de gebeurtenis is gemaakt. Het vergelijken van deze eigenschap met een bepaalde datum/tijd-object kan worden gebruikt om alle gebeurtenissen te filteren:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a>3: berichten van de meest recente bewerking

De meest recente bewerking wordt opgeslagen in de eerste index van de matrixgroep `$SeparateDscOperations`. Opvragen van berichten voor index 0 van de groep retourneert alle berichten voor de meest recente bewerking:

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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: foutberichten voor mislukte bewerkingen die recent zijn geregistreerd

`$SeparateDscOperations[0].Group` bevat een reeks gebeurtenissen voor de meest recente bewerking. Voer de `Where-Object` cmdlet om de gebeurtenissen te filteren op basis van hun niveau weergavenaam. Resultaten worden opgeslagen in de `$myFailedEvent` variabele, die verder kan worden opgesplitst om het gebeurtenisbericht weergegeven:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: alle gebeurtenissen die worden gegenereerd voor een bepaalde taak-ID.

`$SeparateDscOperations` is een matrix van groepen, elk met de naam als de unieke taak-ID heeft. Door het uitvoeren van de `Where-Object` cmdlet, kunt u deze groepen van gebeurtenissen die gedurende een bepaalde taak-ID hebben uitpakken:

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>Logboeken met behulp van xDscDiagnostics DSC analyseren

**xDscDiagnostics** is een PowerShell-module die bestaat uit verschillende functies die kunnen helpen bij het analyseren van DSC-fouten op uw computer. Deze functies kunt u alle lokale gebeurtenissen van afgelopen DSC-bewerkingen of DSC-gebeurtenissen op externe computers identificeren (met geldige referenties). Hier wordt de term DSC-bewerking gebruikt voor het definiëren van één unieke DSC uitvoering vanaf het begin tot het einde. Bijvoorbeeld: `Test-DscConfiguration` is een afzonderlijke DSC-bewerking. Op deze manier elke andere cmdlet in DSC (zoals `Get-DscConfiguration`, `Start-DscConfiguration`, enzovoort) elk worden geïdentificeerd als afzonderlijke DSC-bewerkingen. De functies worden beschreven op [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).
Hulp is beschikbaar door het uitvoeren van `Get-Help <cmdlet name>`.

### <a name="getting-details-of-dsc-operations"></a>Details van DSC-bewerkingen ophalen

De `Get-xDscOperation` functie kunt u de resultaten van de DSC-bewerkingen die worden uitgevoerd op een of meerdere computers vinden en retourneert een object dat het verzamelen van gebeurtenissen bevat die wordt geproduceerd door elke DSC-bewerking.
In de volgende uitvoer kan drie opdrachten zijn uitgevoerd. Het eerste werd doorgegeven en de andere twee is mislukt. Deze resultaten worden samengevat in de uitvoer van `Get-xDscOperation`.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...

```

U kunt ook opgeven dat u alleen resultaten voor de meest recente bewerkingen met behulp van wilt de `Newest` parameter:

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

### <a name="getting-details-of-dsc-events"></a>Details van gebeurtenissen voor DSC ophalen

De `Trace-xDscOperation` cmdlet retourneert een object met een verzameling van gebeurtenissen, hun typen gebeurtenissen en het bericht uitvoer gegenereerd op basis van een bepaalde DSC-bewerking. Normaal gesproken als u merkt dat een storing in een van de bewerkingen met behulp van `Get-xDscOperation`, u wilt traceren die voor deze bewerking om erachter te komen welke van de gebeurtenissen heeft een fout veroorzaakt.

Gebruik de `SequenceID` -parameter voor het ophalen van de gebeurtenissen voor een specifieke bewerking voor een specifieke computer. Als u bijvoorbeeld een `SequenceID` van 9, `Trace-xDscOperaion` ophalen van de tracering voor de DSC-bewerking die werd 9de van de laatste bewerking:

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

Geeft de **GUID** toegewezen aan een specifieke DSC-bewerking (geretourneerd door de `Get-xDscOperation` cmldet) details van de gebeurtenis voor die bewerking DSC ophalen:

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

Merk op dat, aangezien `Trace-xDscOperation` cumuleert de gebeurtenissen van de analyse, foutopsporing, en operationele Logboeken, wordt gevraagd u deze logboeken inschakelen, zoals hierboven is beschreven.

Ook kunt u informatie over de gebeurtenissen verzamelen door het opslaan van de uitvoer van `Trace-xDscOperation` in een variabele. U kunt de volgende opdrachten gebruiken om alle gebeurtenissen voor een bepaalde DSC-bewerking weer te geven.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

Hiermee wordt weergegeven dat hetzelfde resultaat als de `Get-WinEvent` cmdlet, zoals in de onderstaande uitvoer:

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

Eerst gebruikt u in het ideale geval `Get-xDscOperation` om weer te geven van de laatste paar DSC configuratie wordt uitgevoerd op uw computers. Na dit, kunt u een enkele bewerking (met de SequenceID of JobID) bestuderen met `Trace-xDscOperation` te detecteren die gold achter de schermen.

### <a name="getting-events-for-a-remote-computer"></a>Ophalen van gebeurtenissen voor een externe computer

Gebruik de `ComputerName` parameter van de `Trace-xDscOperation` cmdlet details van de gebeurtenis ophalen op een externe computer. Voordat u dit doen kunt, hebt u een firewallregel extern beheer toestaan op de externe computer maken:

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
Nu kunt u die computer in de aanroep van `Trace-xDscOperation`:

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Mijn resources niet bijgewerkt: het opnieuw instellen van de cache

De DSC-engine in de cache opslaat voor resources die zijn geïmplementeerd als een PowerShell-module voor efficiëntie doeleinden. Dit kan echter problemen veroorzaken bij het ontwerpen van een resource en tegelijkertijd testen omdat DSC versie in de cache wordt geladen totdat het proces opnieuw is opgestart. De enige manier om DSC laden van de nieuwere versie is het proces voor het hosten van de DSC-engine expliciet afsluiten.

Op deze manier bij het uitvoeren van `Start-DscConfiguration`, na het toevoegen en wijzigen van een aangepaste bron, de wijziging mogelijk niet uitgevoerd tenzij of tot, de computer opnieuw wordt opgestart. Dit komt doordat DSC in het hostproces van de WMI-Provider (WmiPrvSE) wordt uitgevoerd en er zijn meestal veel exemplaren van WmiPrvSE tegelijk worden uitgevoerd. Wanneer u het opnieuw opstarten, het hostproces opnieuw is opgestart en de cache is leeggemaakt.

Om te recyclen van de configuratie en de cache wissen zonder opnieuw opstarten, moet u stoppen en vervolgens het hostproces opnieuw te starten. Dit kan worden gedaan op een basis per exemplaar, waarbij u het proces te identificeren, stoppen en opnieuw starten. Of u kunt `DebugMode`, zoals hieronder wordt gedemonstreerd opnieuw laden van de PowerShell DSC-resource.

Om te bepalen welk proces als host fungeert voor de DSC-engine en stop de toepassing op basis van per exemplaar, kunt u de proces-ID van de WmiPrvSE die als host voor de DSC-engine fungeert aanbieden. Stop vervolgens, voor het bijwerken van de provider de WmiPrvSE proces met behulp van de onderstaande opdrachten en voer **Start DscConfiguration** opnieuw.

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

## <a name="using-debugmode"></a>Met behulp van fouten opsporen-modus

U kunt de DSC lokale Configuration Manager (LCM) te gebruiken `DebugMode` altijd de cache wissen wanneer het hostproces opnieuw is gestart. Als de waarde **TRUE**, het ervoor zorgt dat de engine altijd opnieuw laden van de PowerShell DSC-resource. Wanneer u klaar bent u schrijft de bron, kunt u dit instellen terug naar **FALSE** en de engine voor het gedrag van de modules in het cachegeheugen worden hersteld.

Hieronder vindt u een demonstratie om weer te geven hoe `DebugMode` kunnen automatisch worden vernieuwd met de cache. Eerst bekijken we de standaardconfiguratie:

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

Kunt u zien dat `DebugMode` is ingesteld op **FALSE**.

Voor het instellen van de `DebugMode` demonstreren, gebruikt u de volgende PowerShell-resource:

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

Schrijf nu een configuratie met behulp van de bovenstaande resource aangeroepen `TestProviderDebugMode`:

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

U ziet dat de inhoud van bestand: '**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**' is **1**.

Werk nu de code van de provider door het volgende script:

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

Dit script genereert een willekeurig getal en de code van de provider dienovereenkomstig bijgewerkt. Met `DebugMode` ingesteld op false, de inhoud van het bestand '**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**' nooit worden gewijzigd.

Nu ingesteld `DebugMode` naar **TRUE** in uw configuratiescript:

```powershell
LocalConfigurationManager
{
    DebugMode = $true
}
```

Als u de bovenstaande script opnieuw uitvoert, ziet u dat de inhoud van het bestand anders elke keer is. (U kunt uitvoeren `Get-DscConfiguration` wilt controleren op het). Hieronder volgt het resultaat van de twee extra wordt uitgevoerd (de resultaten mogelijk andere wanneer u het script uitvoeren):

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

## <a name="see-also"></a>Zie ook

### <a name="reference"></a>Verwijzing
* [Logboek van de DSC-Resource](logResource.md)

### <a name="concepts"></a>Concepten
* [Aangepaste Windows PowerShell Desired State Configuration Resources bouwen](authoringResource.md)

### <a name="other-resources"></a>Andere bronnen
* [Windows PowerShell Desired State Configuration-Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)