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
# <a name="using-a-dsc-report-server"></a>Een DSC-rapportserver gebruiken

Van toepassing op: Windows Power shell 5,0

> [!IMPORTANT]
> De pull-server (Windows *-functie DSC-service* ) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden. Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.
>
> [!NOTE]
> De rapport server die in dit onderwerp wordt beschreven, is niet beschikbaar in Power Shell 4,0.

De lokale Configuration Manager (LCM) van een knoop punt kan worden geconfigureerd voor het verzenden van rapporten over de configuratie status naar een pull-server waarvoor vervolgens een query kan worden uitgevoerd om die gegevens op te halen. Telkens wanneer het knoop punt een configuratie controleert en toepast, wordt een rapport verzonden naar de rapport server. Deze rapporten worden opgeslagen in een Data Base op de server en kunnen worden opgehaald door de webservice voor rapporten aan te roepen.
Elk rapport bevat informatie zoals de configuraties die zijn toegepast en of ze zijn geslaagd, de gebruikte resources, fouten die zijn opgetreden, en begin-en eind tijden.

## <a name="configuring-a-node-to-send-reports"></a>Een knoop punt configureren voor het verzenden van rapporten

U geeft een knoop punt de opdracht om rapporten naar een server te verzenden met behulp van een **ReportServerWeb** -blok in de LCM-configuratie van het knoop punt (Zie [Configuring the local Configuration Manager](../managing-nodes/metaConfig.md)) voor meer informatie over het configureren van de LCM. De server waarnaar het knoop punt rapporten verzendt, moet worden ingesteld als een webpull-server (u kunt geen rapporten verzenden naar een SMB-share). Zie [een DSC Web-pull-server instellen](pullServer.md)voor meer informatie over het instellen van een pull-server. De rapport server kan dezelfde service zijn als waaruit het knoop punt configuraties ophaalt en resources ophaalt, of het kan een andere service zijn.

In het **ReportServerWeb** -blok geeft u de URL van de pull-service en een registratie sleutel op die bekend is bij de-server.

Met de volgende configuratie configureert u een knoop punt voor het ophalen van configuraties van één service, en verzendt u rapporten naar een service op een andere server.

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

Met de volgende configuratie configureert u een knoop punt voor het gebruik van één server voor configuraties, resources en rapportage.

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
> U kunt de webservice een naam, wat u wilt wanneer u een pull-server instelt, maar de **ServerURL** -eigenschap moet overeenkomen met de service naam.

## <a name="getting-report-data"></a>Rapport gegevens ophalen

Rapporten die worden verzonden naar de pull-server, worden ingevoerd in een Data Base op de server. De rapporten zijn beschikbaar via aanroepen van de webservice. Als u rapporten wilt ophalen voor een specifiek knoop punt, verzendt u een HTTP-aanvraag naar de webservice voor rapporten in de volgende vorm:

`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`

Waarbij `MyNodeAgentId` de AgentId is van het knoop punt waarvoor u rapporten wilt ophalen. U kunt de AgentID voor een knoop punt ophalen door [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) op dat knoop punt aan te roepen.

De rapporten worden geretourneerd als een matrix van JSON-objecten.

Het volgende script retourneert de rapporten voor het knoop punt waarop het wordt uitgevoerd:

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

## <a name="viewing-report-data"></a>Rapport gegevens weer geven

Als u een variabele instelt op het resultaat van de functie **GetReport** , kunt u de afzonderlijke velden weer geven in een element van de geretourneerde matrix:

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

Standaard worden de rapporten gesorteerd op **JobID** . Als u het meest recente rapport wilt ophalen, kunt u de rapporten sorteren op aflopende eigenschap **StartTime** en vervolgens het eerste element van de matrix ophalen:

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

U ziet dat de eigenschap **StatusData** een object met een aantal eigenschappen bevat. Dit is het gedeelte van de rapport gegevens. Laten we eens kijken naar de afzonderlijke velden van de eigenschap **StatusData** voor het meest recente rapport:

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

Dit laat onder andere zien dat de meest recente configuratie twee resources heet en dat een van de onderdelen de gewenste status heeft, en dat een van beide is. U kunt een lees bare uitvoer van alleen de eigenschap **ResourcesNotInDesiredState** verkrijgen:

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

Deze voor beelden zijn bedoeld om u een idee te geven van wat u met rapport gegevens kunt doen. Zie voor een inleiding over het werken met JSON in Power shell [afspelen met JSON en Power shell](https://devblogs.microsoft.com/scripting/playing-with-json-and-powershell/).

## <a name="see-also"></a>Zie ook

[De lokale Configuration Manager configureren](../managing-nodes/metaConfig.md)

[Een DSC Web-pull-server instellen](pullServer.md)

[Een pull-client instellen met behulp van configuratienamen](pullClientConfigNames.md)
