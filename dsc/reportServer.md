---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Een DSC-rapportserver gebruiken
ms.openlocfilehash: bcd414e9cc6d3b321676aaab6bbc3ca1b02e80aa
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893134"
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="09422-103">Een DSC-rapportserver gebruiken</span><span class="sxs-lookup"><span data-stu-id="09422-103">Using a DSC report server</span></span>

<span data-ttu-id="09422-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="09422-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09422-105">De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="09422-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="09422-106">Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="09422-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>
>
> <span data-ttu-id="09422-107">**Houd er rekening mee** de rapportserver die in dit onderwerp is niet beschikbaar in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="09422-107">**Note** The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="09422-108">De lokale Configuration Manager (LCM) van een knooppunt kan worden geconfigureerd voor het verzenden van rapporten over de status van de configuratie met een pull-server, die vervolgens kan worden opgevraagd die gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="09422-108">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="09422-109">Telkens wanneer het knooppunt wordt gecontroleerd en van toepassing is een configuratie, stuurt deze een rapport op de rapportserver.</span><span class="sxs-lookup"><span data-stu-id="09422-109">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="09422-110">Deze rapporten worden opgeslagen in een database op de server en kunnen worden opgehaald door het aanroepen van de reporting webservice.</span><span class="sxs-lookup"><span data-stu-id="09422-110">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="09422-111">Elk rapport bevat informatie zoals welke configuraties zijn toegepast en of deze is voltooid, de resources gebruikt, eventuele fouten die zijn gegenereerd, en begin- en eindtijden.</span><span class="sxs-lookup"><span data-stu-id="09422-111">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="09422-112">Configureren van een knooppunt voor het verzenden van rapporten</span><span class="sxs-lookup"><span data-stu-id="09422-112">Configuring a node to send reports</span></span>

<span data-ttu-id="09422-113">U zien dat een knooppunt om rapporten te verzenden naar een server met behulp van een **ReportServerWeb** blokkeren in de knooppuntconfiguratie LCM (Zie voor meer informatie over het configureren van de LCM [de Local Configuration Manager configureren](metaConfig.md) ).</span><span class="sxs-lookup"><span data-stu-id="09422-113">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md)).</span></span> <span data-ttu-id="09422-114">De server waarop het knooppunt worden rapporten verzonden moet worden ingesteld als een web-pull-server (u kunt geen rapporten verzenden naar een SMB-share).</span><span class="sxs-lookup"><span data-stu-id="09422-114">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="09422-115">Zie voor meer informatie over het instellen van een pull-server [instellen van een DSC-pull-endwebserver](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="09422-115">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="09422-116">De rapportserver kan dezelfde service waarvan het knooppunt haalt configuraties en -resources ophaalt, of een andere service kan zijn.</span><span class="sxs-lookup"><span data-stu-id="09422-116">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>

<span data-ttu-id="09422-117">In de **ReportServerWeb** blok, u de URL van de pull-service en een registratiesleutel die bekend is met de server opgeven.</span><span class="sxs-lookup"><span data-stu-id="09422-117">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>

<span data-ttu-id="09422-118">De volgende configuratie wordt een knooppunt geconfigureerd voor pull-configuraties van de ene service en rapporten verzenden naar een service op een andere server.</span><span class="sxs-lookup"><span data-stu-id="09422-118">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span>

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
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}

ReportClientConfig
```

<span data-ttu-id="09422-119">De volgende configuratie configureert u een knooppunt voor het gebruik van één server voor configuraties, resources en rapportage.</span><span class="sxs-lookup"><span data-stu-id="09422-119">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

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
> <span data-ttu-id="09422-120">U kunt de webservice naam wat u wilt dat bij het instellen van een pull-server, maar de **ServerURL** eigenschap moet overeenkomen met de naam van de service.</span><span class="sxs-lookup"><span data-stu-id="09422-120">You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="09422-121">Ophalen van rapportgegevens</span><span class="sxs-lookup"><span data-stu-id="09422-121">Getting report data</span></span>

<span data-ttu-id="09422-122">Rapporten die worden verzonden naar de pull-server worden ingevoerd in een database op de server.</span><span class="sxs-lookup"><span data-stu-id="09422-122">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="09422-123">De rapporten zijn beschikbaar via aanroepen naar de webservice.</span><span class="sxs-lookup"><span data-stu-id="09422-123">The reports are available through calls to the web service.</span></span> <span data-ttu-id="09422-124">Als u wilt ophalen van rapporten voor een bepaald knooppunt, door een HTTP-aanvraag te verzenden naar de rapport-webservice in de volgende notatie: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports` waar `MyNodeAgentId` is de AgentId van het knooppunt waarvan u wilt ophalen van rapporten.</span><span class="sxs-lookup"><span data-stu-id="09422-124">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports` where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="09422-125">U kunt de AgentID voor een knooppunt krijgen door het aanroepen van [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) op dat knooppunt.</span><span class="sxs-lookup"><span data-stu-id="09422-125">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) on that node.</span></span>

<span data-ttu-id="09422-126">De rapporten worden geretourneerd als een matrix met JSON-objecten.</span><span class="sxs-lookup"><span data-stu-id="09422-126">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="09422-127">Het volgende script retourneert de rapporten voor het knooppunt waarop deze wordt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="09422-127">The following script returns the reports for the node on which it is run:</span></span>

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

## <a name="viewing-report-data"></a><span data-ttu-id="09422-128">Rapportgegevens weergeven</span><span class="sxs-lookup"><span data-stu-id="09422-128">Viewing report data</span></span>

<span data-ttu-id="09422-129">Als u een variabele op het resultaat van instellen de **GetReport** functie, kunt u de afzonderlijke velden weergeven in een element van de matrix die is geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="09422-129">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

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

<span data-ttu-id="09422-130">De rapporten worden standaard gesorteerd op **JobID**.</span><span class="sxs-lookup"><span data-stu-id="09422-130">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="09422-131">Als u de meest recente rapport, kunt u de rapporten sorteren op Aflopend **StartTime** eigenschap en get het eerste element van de matrix:</span><span class="sxs-lookup"><span data-stu-id="09422-131">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="09422-132">U ziet dat de **StatusData** eigenschap is een object met een aantal eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="09422-132">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="09422-133">Dit is waar veel van de rapportagegegevens.</span><span class="sxs-lookup"><span data-stu-id="09422-133">This is where much of the reporting data is.</span></span> <span data-ttu-id="09422-134">Bekijk de afzonderlijke velden van de **StatusData** eigenschap voor de meest recente rapport:</span><span class="sxs-lookup"><span data-stu-id="09422-134">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

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

<span data-ttu-id="09422-135">Onder andere ziet dat de meest recente configuratie met de naam twee resources, en dat een van beide in de gewenste status is en een van deze niet is.</span><span class="sxs-lookup"><span data-stu-id="09422-135">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="09422-136">Krijgt u een beter leesbare uitvoer van alleen de **ResourcesNotInDesiredState** eigenschap:</span><span class="sxs-lookup"><span data-stu-id="09422-136">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

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

<span data-ttu-id="09422-137">Houd er rekening mee dat deze voorbeelden zijn bedoeld om aan te geven u een idee van wat u met de rapportgegevens doen kunt.</span><span class="sxs-lookup"><span data-stu-id="09422-137">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="09422-138">Zie voor een inleiding over het werken met JSON in PowerShell [spelen met JSON- en PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="09422-138">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="09422-139">Zie ook</span><span class="sxs-lookup"><span data-stu-id="09422-139">See Also</span></span>

[<span data-ttu-id="09422-140">De Local Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="09422-140">Configuring the Local Configuration Manager</span></span>](metaConfig.md)

[<span data-ttu-id="09422-141">Instellen van een DSC-pull-endwebserver</span><span class="sxs-lookup"><span data-stu-id="09422-141">Setting up a DSC web pull server</span></span>](pullServer.md)

[<span data-ttu-id="09422-142">Een pull-client instellen met behulp van configuratienamen</span><span class="sxs-lookup"><span data-stu-id="09422-142">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)