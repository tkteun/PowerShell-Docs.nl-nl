---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een DSC-rapportserver gebruiken
description: De lokale Configuration Manager (LCM) van een knoop punt kan worden geconfigureerd voor het verzenden van rapporten over de configuratie status naar een pull-server waarvoor vervolgens een query kan worden uitgevoerd om die gegevens op te halen.
ms.openlocfilehash: 58ff1684bbe1d23fa68296aa56dd94ba6bc5b148
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653716"
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="d7080-104">Een DSC-rapportserver gebruiken</span><span class="sxs-lookup"><span data-stu-id="d7080-104">Using a DSC report server</span></span>

<span data-ttu-id="d7080-105">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="d7080-105">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7080-106">De pull-server (Windows *-functie DSC-service* ) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden.</span><span class="sxs-lookup"><span data-stu-id="d7080-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="d7080-107">Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.</span><span class="sxs-lookup"><span data-stu-id="d7080-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>
>
> [!NOTE]
> <span data-ttu-id="d7080-108">De rapport server die in dit onderwerp wordt beschreven, is niet beschikbaar in Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="d7080-108">The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="d7080-109">De lokale Configuration Manager (LCM) van een knoop punt kan worden geconfigureerd voor het verzenden van rapporten over de configuratie status naar een pull-server waarvoor vervolgens een query kan worden uitgevoerd om die gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="d7080-109">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server that can then be queried to retrieve that data.</span></span> <span data-ttu-id="d7080-110">Telkens wanneer het knoop punt een configuratie controleert en toepast, wordt een rapport verzonden naar de rapport server.</span><span class="sxs-lookup"><span data-stu-id="d7080-110">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="d7080-111">Deze rapporten worden opgeslagen in een Data Base op de server en kunnen worden opgehaald door de webservice voor rapporten aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="d7080-111">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span>
<span data-ttu-id="d7080-112">Elk rapport bevat informatie zoals de configuraties die zijn toegepast en of ze zijn geslaagd, de gebruikte resources, fouten die zijn opgetreden, en begin-en eind tijden.</span><span class="sxs-lookup"><span data-stu-id="d7080-112">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="d7080-113">Een knoop punt configureren voor het verzenden van rapporten</span><span class="sxs-lookup"><span data-stu-id="d7080-113">Configuring a node to send reports</span></span>

<span data-ttu-id="d7080-114">U geeft een knoop punt de opdracht om rapporten naar een server te verzenden met behulp van een **ReportServerWeb** -blok in de LCM-configuratie van het knoop punt (Zie [Configuring the local Configuration Manager](../managing-nodes/metaConfig.md)) voor meer informatie over het configureren van de LCM.</span><span class="sxs-lookup"><span data-stu-id="d7080-114">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)).</span></span> <span data-ttu-id="d7080-115">De server waarnaar het knoop punt rapporten verzendt, moet worden ingesteld als een webpull-server (u kunt geen rapporten verzenden naar een SMB-share).</span><span class="sxs-lookup"><span data-stu-id="d7080-115">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="d7080-116">Zie [een DSC Web-pull-server instellen](pullServer.md)voor meer informatie over het instellen van een pull-server.</span><span class="sxs-lookup"><span data-stu-id="d7080-116">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="d7080-117">De rapport server kan dezelfde service zijn als waaruit het knoop punt configuraties ophaalt en resources ophaalt, of het kan een andere service zijn.</span><span class="sxs-lookup"><span data-stu-id="d7080-117">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>

<span data-ttu-id="d7080-118">In het **ReportServerWeb** -blok geeft u de URL van de pull-service en een registratie sleutel op die bekend is bij de-server.</span><span class="sxs-lookup"><span data-stu-id="d7080-118">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>

<span data-ttu-id="d7080-119">Met de volgende configuratie configureert u een knoop punt voor het ophalen van configuraties van één service, en verzendt u rapporten naar een service op een andere server.</span><span class="sxs-lookup"><span data-stu-id="d7080-119">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCPullServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}

ReportClientConfig
```

<span data-ttu-id="d7080-120">Met de volgende configuratie configureert u een knoop punt voor het gebruik van één server voor configuraties, resources en rapportage.</span><span class="sxs-lookup"><span data-stu-id="d7080-120">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }



        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfig
```

> [!NOTE]
> <span data-ttu-id="d7080-121">U kunt de webservice een naam, wat u wilt wanneer u een pull-server instelt, maar de **ServerURL** -eigenschap moet overeenkomen met de service naam.</span><span class="sxs-lookup"><span data-stu-id="d7080-121">You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="d7080-122">Rapport gegevens ophalen</span><span class="sxs-lookup"><span data-stu-id="d7080-122">Getting report data</span></span>

<span data-ttu-id="d7080-123">Rapporten die worden verzonden naar de pull-server, worden ingevoerd in een Data Base op de server.</span><span class="sxs-lookup"><span data-stu-id="d7080-123">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="d7080-124">De rapporten zijn beschikbaar via aanroepen van de webservice.</span><span class="sxs-lookup"><span data-stu-id="d7080-124">The reports are available through calls to the web service.</span></span> <span data-ttu-id="d7080-125">Als u rapporten wilt ophalen voor een specifiek knoop punt, verzendt u een HTTP-aanvraag naar de webservice voor rapporten in de volgende vorm:</span><span class="sxs-lookup"><span data-stu-id="d7080-125">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form:</span></span>

`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`

<span data-ttu-id="d7080-126">Waarbij `MyNodeAgentId` de AgentId is van het knoop punt waarvoor u rapporten wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="d7080-126">Where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="d7080-127">U kunt de AgentID voor een knoop punt ophalen door [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) op dat knoop punt aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="d7080-127">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) on that node.</span></span>

<span data-ttu-id="d7080-128">De rapporten worden geretourneerd als een matrix van JSON-objecten.</span><span class="sxs-lookup"><span data-stu-id="d7080-128">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="d7080-129">Het volgende script retourneert de rapporten voor het knoop punt waarop het wordt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="d7080-129">The following script returns the reports for the node on which it is run:</span></span>

```powershell
function GetReport
{
    param
    (
        $AgentId = "$((glcm).AgentId)",
        $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc"
    )

    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```

## <a name="viewing-report-data"></a><span data-ttu-id="d7080-130">Rapport gegevens weer geven</span><span class="sxs-lookup"><span data-stu-id="d7080-130">Viewing report data</span></span>

<span data-ttu-id="d7080-131">Als u een variabele instelt op het resultaat van de functie **GetReport** , kunt u de afzonderlijke velden weer geven in een element van de geretourneerde matrix:</span><span class="sxs-lookup"><span data-stu-id="d7080-131">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

```powershell
$reports = GetReport
$reports[1]
```

```output
JobId                : 019dfbe5-f99f-11e5-80c6-001dd8b8065c
OperationType        : Consistency
RefreshMode          : Pull
Status               : Success
ReportFormatVersion  : 2.0
ConfigurationVersion : 2.0.0
StartTime            : 04/03/2016 06:21:43
EndTime              : 04/03/2016 06:22:04
RebootRequested      : False
Errors               : {}
StatusData           : {{"StartDate":"2016-04-03T06:21:43.7220000-07:00","IPV6Addresses":["2001:4898:d8:f2f2:852b:b255:b071:283b","fe80::852b:b255:b071
                       :283b%12","::2000:0:0:0","::1","::2000:0:0:0"],"DurationInSeconds":"21","JobID":"{019DFBE5-F99F-11E5-80C6-001DD8B8065C}","Curren
                       tChecksum":"A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F","MetaData":"Author: configAuthor; Name:
                       Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost: CONTOSO-PullSrv;","RebootRequested":"False
                       ","Status":"Success","IPV4Addresses":["10.240.179.151","127.0.0.1"],"LCMVersion":"2.0","ResourcesNotInDesiredState":[{"SourceInf
                       o":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall","ModuleName":"xNetworking","DurationInSeconds":"8.785",
                       "InstanceName":"Firewall","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"xFirewall","ModuleVersion":"2.7.0.0","
                       RebootRequested":"False","ResourceId":"[xFirewall]Firewall","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"False
                       "}],"NumberOfResources":"2","Type":"Consistency","HostName":"CONTOSO-PULLCLI","ResourcesInDesiredState":[{"SourceInfo":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive","ModuleName":"PSDesiredStateConfiguration","DurationInSeconds":"1.848",
                       "InstanceName":"ArchiveExample","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"Archive","ModuleVersion":"1.1","
                       RebootRequested":"False","ResourceId":"[Archive]ArchiveExample","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"T
                       rue"}],"MACAddresses":["00-1D-D8-B8-06-5C","00-00-00-00-00-00-00-E0"],"MetaConfiguration":{"AgentId":"52DA826D-00DE-4166-8ACB-73F2B46A7E00",
                       "ConfigurationDownloadManagers":[{"SourceInfo":"C:\\ReportTest\\LCMConfig.ps1::14::9::ConfigurationRepositoryWeb","A
                       llowUnsecureConnection":"True","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","RegistrationKey":"","ResourceId":"[Config
                       urationRepositoryWeb]CONTOSO-PullSrv","ConfigurationNames":["ClientConfig"]}],"ActionAfterReboot":"ContinueConfiguration","LCMCo
                       mpatibleVersions":["1.0","2.0"],"LCMState":"Idle","ResourceModuleManagers":[],"ReportManagers":[{"AllowUnsecureConnection":"True
                       ","RegistrationKey":"","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","ResourceId":"[ReportServerWeb]CONTOSO-PullSrv","S
                       ourceInfo":"C:\\ReportTest\\LCMConfig.ps1::24::9::ReportServerWeb"}],"StatusRetentionTimeInDays":"10","LCMVersion":"2.0","Config
                       urationMode":"ApplyAndMonitor","RefreshFrequencyMins":"30","RebootNodeIfNeeded":"True","RefreshMode":"Pull","DebugMode":["NONE"]
                       ,"LCMStateDetail":"","AllowModuleOverwrite":"False","ConfigurationModeFrequencyMins":"15"},"Locale":"en-US","Mode":"Pull"}}
AdditionalData       : {}
```

<span data-ttu-id="d7080-132">Standaard worden de rapporten gesorteerd op **JobID** .</span><span class="sxs-lookup"><span data-stu-id="d7080-132">By default, the reports are sorted by **JobID** .</span></span> <span data-ttu-id="d7080-133">Als u het meest recente rapport wilt ophalen, kunt u de rapporten sorteren op aflopende eigenschap **StartTime** en vervolgens het eerste element van de matrix ophalen:</span><span class="sxs-lookup"><span data-stu-id="d7080-133">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="d7080-134">U ziet dat de eigenschap **StatusData** een object met een aantal eigenschappen bevat.</span><span class="sxs-lookup"><span data-stu-id="d7080-134">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="d7080-135">Dit is het gedeelte van de rapport gegevens.</span><span class="sxs-lookup"><span data-stu-id="d7080-135">This is where much of the reporting data is.</span></span> <span data-ttu-id="d7080-136">Laten we eens kijken naar de afzonderlijke velden van de eigenschap **StatusData** voor het meest recente rapport:</span><span class="sxs-lookup"><span data-stu-id="d7080-136">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData
```

```output
StartDate                  : 2016-04-04T11:21:41.2990000-07:00
IPV6Addresses              : {2001:4898:d8:f2f2:852b:b255:b071:283b, fe80::852b:b255:b071:283b%12, ::2000:0:0:0, ::1...}
DurationInSeconds          : 25
JobID                      : {135D230E-FA92-11E5-80C6-001DD8B8065C}
CurrentChecksum            : A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F
MetaData                   : Author: configAuthor; Name: Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost:
                             CONTOSO-PullSrv;
RebootRequested            : False
Status                     : Success
IPV4Addresses              : {10.240.179.151, 127.0.0.1}
LCMVersion                 : 2.0
ResourcesNotInDesiredState : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall; ModuleName=xNetworking;
                             DurationInSeconds=10.725; InstanceName=Firewall; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=xFirewall;
                             ModuleVersion=2.7.0.0; RebootRequested=False; ResourceId=[xFirewall]Firewall; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=False}}
NumberOfResources          : 2
Type                       : Consistency
HostName                   : CONTOSO-PULLCLI
ResourcesInDesiredState    : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive; ModuleName=PSDesiredStateConfiguration;
                             DurationInSeconds=2.672; InstanceName=ArchiveExample; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=Archive;
                             ModuleVersion=1.1; RebootRequested=False; ResourceId=[Archive]ArchiveExample; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=True}}
MACAddresses               : {00-1D-D8-B8-06-5C, 00-00-00-00-00-00-00-E0}
MetaConfiguration          : @{AgentId=52DA826D-00DE-4166-8ACB-73F2B46A7E00; ConfigurationDownloadManagers=System.Object[];
                             ActionAfterReboot=ContinueConfiguration; LCMCompatibleVersions=System.Object[]; LCMState=Idle;
                             ResourceModuleManagers=System.Object[]; ReportManagers=System.Object[]; StatusRetentionTimeInDays=10; LCMVersion=2.0;
                             ConfigurationMode=ApplyAndMonitor; RefreshFrequencyMins=30; RebootNodeIfNeeded=True; RefreshMode=Pull;
                             DebugMode=System.Object[]; LCMStateDetail=; AllowModuleOverwrite=False; ConfigurationModeFrequencyMins=15}
Locale                     : en-US
Mode                       : Pull
```

<span data-ttu-id="d7080-137">Dit laat onder andere zien dat de meest recente configuratie twee resources heet en dat een van de onderdelen de gewenste status heeft, en dat een van beide is.</span><span class="sxs-lookup"><span data-stu-id="d7080-137">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="d7080-138">U kunt een lees bare uitvoer van alleen de eigenschap **ResourcesNotInDesiredState** verkrijgen:</span><span class="sxs-lookup"><span data-stu-id="d7080-138">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

```powershell
$statusData.ResourcesInDesiredState
```

```output
SourceInfo        : C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive
ModuleName        : PSDesiredStateConfiguration
DurationInSeconds : 2.672
InstanceName      : ArchiveExample
StartDate         : 2016-04-04T11:21:55.7200000-07:00
ResourceName      : Archive
ModuleVersion     : 1.1
RebootRequested   : False
ResourceId        : [Archive]ArchiveExample
ConfigurationName : Sample_ArchiveFirewall
InDesiredState    : True
```

<span data-ttu-id="d7080-139">Deze voor beelden zijn bedoeld om u een idee te geven van wat u met rapport gegevens kunt doen.</span><span class="sxs-lookup"><span data-stu-id="d7080-139">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="d7080-140">Zie voor een inleiding over het werken met JSON in Power shell [afspelen met JSON en Power shell](https://devblogs.microsoft.com/scripting/playing-with-json-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="d7080-140">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://devblogs.microsoft.com/scripting/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7080-141">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d7080-141">See Also</span></span>

[<span data-ttu-id="d7080-142">De lokale Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="d7080-142">Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="d7080-143">Een DSC Web-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="d7080-143">Setting up a DSC web pull server</span></span>](pullServer.md)

[<span data-ttu-id="d7080-144">Een pull-client instellen met behulp van configuratienamen</span><span class="sxs-lookup"><span data-stu-id="d7080-144">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
