---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Best practices voor pull-servers
ms.openlocfilehash: da67f8fd793878b097ffb260afad0fcf5c69bb04
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686675"
---
# <a name="pull-server-best-practices"></a>Best practices voor pull-servers

Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden. Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).

Samenvatting: Dit document is bedoeld om op te nemen proces en uitbreidbaarheid voor de ondersteuning van technici die zijn voorbereid voor de oplossing. Details dient aanbevolen procedures aangeduid met de klanten en vervolgens worden gevalideerd door het productteam om te controleren of aanbevelingen toekomstige gericht zijn en als stabiel beschouwd.

| |Informatie over dit document|
|:---|:---|
De auteur | Michael Greene
Revisoren | Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic
Gepubliceerd | April 2015

## <a name="abstract"></a>Samenvatting

Dit document is ontworpen als officiële richtlijn voor iedereen plannen voor een implementatie van Windows PowerShell Desired State Configuration pull-server. Een pull-server is een eenvoudige service die duurt slechts enkele minuten om te implementeren. Hoewel dit document technische uitleg die kan worden gebruikt in een implementatie biedt, wordt de waarde van dit document is als referentie voor aanbevolen procedures en wat te denken voordat u implementeert.
Lezers mooi met DSC moeten zijn en de voorwaarden die worden gebruikt om te beschrijven van de onderdelen die zijn opgenomen in een DSC-implementatie. Zie voor meer informatie de [Windows PowerShell Desired State Configuration Overview](/powershell/dsc/overview) onderwerp.
Zoals DSC wordt verwacht op cloudcadans ontwikkelen, wordt de onderliggende technologie, met inbegrip van pull-server ook verwacht ontwikkelen en nieuwe mogelijkheden geïntroduceerd. Dit document bevat een versietabel met in de bijlage die verwijzingen naar de vorige releases en verwijzingen naar toekomstige uitziende oplossingen om aan te moedigen toekomstgerichte ontwerpen biedt.

De twee belangrijkste secties van dit document:

- Planning van de configuratie
- Installatiehandleiding

### <a name="versions-of-the-windows-management-framework"></a>Versies van Windows Management Framework

De informatie in dit document is bedoeld om te passen op Windows Management Framework 5.0. WMF 5.0 is niet vereist voor de implementatie en het gebruik van een pull-server, is versie 5.0 de focus van dit document.

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell Desired State Configuration

Desired State Configuration (DSC) is een beheerplatform waarmee configuratiegegevens implementeren en beheren met behulp van een industrie-syntaxis met de naam van het Managed Object Format (MOF) om te beschrijven van het Common Information Model (CIM). Er bestaat een open source-project, Open Management Infrastructure (OMI), om verdere ontwikkeling van deze standaarden voor platformen, waaronder Linux en de hardware, besturingssystemen. Zie voor meer informatie de [DMTF-pagina koppelen volgens de specificaties van MOF](https://www.dmtf.org/standards/cim), en [OMI documenten en bron](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell biedt een set met taaluitbreidingen voor Desired State Configuration die u gebruiken kunt voor het maken en beheren van declaratieve configuraties.

### <a name="pull-server-role"></a>Pull-server-rol

Een pull-server voorziet in een gecentraliseerde service voor het opslaan van configuraties die is toegankelijk voor de doelknooppunten.

De functie voor pull-server kan worden geïmplementeerd als een Web Server-exemplaar of een SMB-bestandsshare. De web server-functie bevat een OData-interface en kan de mogelijkheden voor doelknooppunten om te rapporteren terug bevestiging van het slagen of mislukken als configuraties zijn toegepast (optioneel) bevatten. Deze functionaliteit is nuttig in omgevingen waarin er een groot aantal doelknooppunten.
Na het configureren van een doelknooppunt (ook wel een client genoemd) om te verwijzen naar de pull-server de configuratie van de meest recente gegevens en alle vereiste scripts gedownload en toegepast. Dit kan gebeuren als een eenmalige installatie of als een opnieuw voorkomende taak waardoor ook de pull-server een belangrijk onderdeel voor het beheren van de wijziging op schaal. Zie voor meer informatie, [Windows PowerShell Desired State Configuration Pull-Servers](/powershell/dsc/pullServer) en

[Pushen en ophalen van configuratie-modi](/powershell/dsc/pullServer).

## <a name="configuration-planning"></a>Planning van de configuratie

Er is informatie die vooraf kan worden verzameld om u te helpen bij het plannen voor de juiste architectuur en om te worden voorbereid voor de stappen die nodig zijn om uit te voeren van de implementatie voor alle enterprise software-implementatie. De volgende secties bevatten informatie over het voorbereiden en de organisatie-verbindingen die waarschijnlijk moet gebeuren vooraf.

### <a name="software-requirements"></a>Softwarevereisten

Implementatie van een pull-server vereist de functie van de DSC-Service van Windows Server. Deze functie is geïntroduceerd in Windows Server 2012 en is bijgewerkt via voortdurende versies van Windows Management Framework (WMF).

### <a name="software-downloads"></a>Software downloaden

Naast het installeren van de meest recente inhoud van Windows Update, er zijn twee downloads beschouwd als aanbevolen procedure voor het implementeren van een DSC-pull-server: De meest recente versie van Windows Management Framework en een DSC-module voor het automatiseren van pull-server inrichten.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 bevat een functie met de naam van de DSC-Service. De functie DSC-Service biedt de functionaliteit pull-server, met inbegrip van de binaire bestanden die ondersteuning bieden voor het OData-eindpunt.
WMF is opgenomen in Windows Server en een flexibele uitgebracht tussen Windows Server-versies is bijgewerkt. [Nieuwe versies van WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) kunnen updates op de functie voor DSC-Service zijn. Daarom is het een aanbevolen procedure voor het downloaden van de nieuwste versie van WMF en om te controleren om na te gaan als u de release van een update voor de functie voor DSC-service bevat de opmerkingen bij de release. Ook moet u de sectie van de opmerkingen bij de release die aangeeft of de status van het ontwerp voor een update of scenario wordt vermeld als stabiel of experimentele controleren.
Als u wilt toestaan voor een flexibele releasecyclus afzonderlijke functies worden gedeclareerd stabiel, is wat aangeeft dat de functie gereed om te worden gebruikt in een productie-omgeving, terwijl de WMF in Preview-versie is uitgebracht.
Andere functies die in het verleden zijn bijgewerkt door versies van WMF (Zie de opmerkingen bij de Release van WMF voor verdere details):

- Windows PowerShell Windows PowerShell Integrated Scripting
- Environment (ISE) Windows PowerShell-webservices (Management OData
- IIS Extension)  Windows PowerShell Desired State Configuration (DSC)
- Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)

### <a name="dsc-resource"></a>DSC-resource

De implementatie van een pull-server kan worden vereenvoudigd door de service met behulp van een DSC-configuratiescript inricht. Dit document bevat configuratiescripts die kunnen worden gebruikt voor het implementeren van een productie gereed server-knooppunt. Voor het gebruik van de van configuratiescripts, een DSC-module is vereist dat niet is opgenomen in Windows Server. De modulenaam van de vereiste is **xPSDesiredStateConfiguration**, waaronder de DSC-resource **xDscWebService**. De module xPSDesiredStateConfiguration kan worden gedownload [hier](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Gebruik de `Install-Module` cmdlet uit de **PowerShellGet** module.

```powershell
Install-Module xPSDesiredStateConfiguration
```

De **PowerShellGet** module wordt de module te downloaden:

`C:\Program Files\Windows PowerShell\Modules`

Taak plannen|
---|
U hebt toegang tot de installatiebestanden voor Windows Server 2012 R2?|
De implementatieomgeving van een internettoegang hebben tot de module en WMF downloaden uit de galerie met online?|
Hoe installeert u de meest recente beveiligingsupdates na de installatie van het besturingssysteem?|
Wordt de omgeving hebt u toegang tot Internet om updates te downloaden of heeft deze een lokale Windows Server Update Services (WSUS)-server?|
Hebt u toegang tot bestanden die al updates via offline injectie zijn voor installatie van Windows Server?|

### <a name="hardware-requirements"></a>Hardwarevereisten

Pull-server-implementaties worden ondersteund op fysieke en virtuele servers. Vereisten voor pull-server de grootte uitgelijnd met de vereisten voor Windows Server 2012 R2.

CPU: 1,4 GHz, 64-bits processor, geheugen: 512 MB schijfruimte: Netwerk van 32 GB: Gigabit Ethernet-Adapter

Taak plannen|
---|
Wilt u implementeren op fysieke hardware of op een virtualisatieplatform?|
Wat is het proces voor het aanvragen van een nieuwe server voor uw doelomgeving?|
Wat is de gemiddelde verwerkingstijd voor een server beschikbaar?|
Welke grootte-server zal u vragen?|

### <a name="accounts"></a>Accounts

Er zijn geen vereisten voor serviceaccount om een pull-server-exemplaar te implementeren.
Er zijn echter scenario's waarin de website in de context van een lokale gebruikersaccount toegekend uitvoeren kan.
Bijvoorbeeld, als er behoefte aan toegang tot een storage-share voor website-inhoud en de Windows-Server of het apparaat die als host fungeert voor de storage-share zijn niet toegevoegd aan een domein.

### <a name="dns-records"></a>DNS-records

U moet een servernaam bij het configureren van clients gebruiken om te werken met een pull-server-omgeving.
Hostnaam van de server wordt meestal gebruikt in een testomgeving, of het IP-adres voor de server kan worden gebruikt als DNS-naamomzetting niet beschikbaar is.
In een productieomgeving of in een testomgeving die is bedoeld om weer te geven van een productie-implementatie, wordt de aanbevolen procedure is het maken van een DNS CNAME-record.

Een DNS CNAME kunt u een alias om te verwijzen naar de host-A-record maken.
Het doel van de extra UPN-record is de flexibiliteit te vergroten moet een wijziging vereist in de toekomst zijn.
Een CNAME te isoleren van configuratie van de client zodat wijzigingen in de server-omgeving, zoals het vervangen van een pull-server of het toevoegen van extra pull-servers, wordt een bijbehorende wijziging in de configuratie van de client vereist.

Bij het kiezen van een naam op voor de DNS-record, houd rekening met de oplossingsarchitectuur.
Als met behulp van de taakverdeling, moet het certificaat dat wordt gebruikt om verkeer te beveiligen via HTTPS voor het delen van dezelfde naam als de DNS-record.

Scenario |Best practices
:---|:---
Testomgeving |De geplande productie-omgeving, indien mogelijk reproduceren. De hostnaam van een server is geschikt voor eenvoudige configuraties. Als DNS niet beschikbaar is, kan een IP-adres kan worden gebruikt in plaats van een hostnaam.|
Implementatie met één knooppunt |Maak een DNS CNAME-record die naar de hostnaam van de server verwijst.|

Zie voor meer informatie, [DNS Round Robin configureren in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).

Taak plannen|
---|
Wist u dat met wie neem contact op met om DNS-records gemaakt en gewijzigd?|
Wat is de gemiddelde doorlooptijd voor een aanvraag voor een DNS-record?|
Moet u om aan te vragen van statische hostnaam-A-records voor servers?|
Welke vragen u als een CNAME?|
Indien nodig, welk type Load Balancing-oplossing wordt u gebruiken? (Zie sectie Load Balancing voor meer informatie)|

### <a name="public-key-infrastructure"></a>Openbare-sleutelinfrastructuur

De meeste organisaties vereisen dat het netwerkverkeer, met name verkeer dat dergelijke gevoelige gegevens bevat, hoe servers zijn geconfigureerd, moet worden gevalideerd en/of tijdens de overdracht versleuteld.
Het is mogelijk om te implementeren met behulp van HTTP, vereenvoudigt het uitvoeren van een pull-server aanvragen van clients in normale tekst, het is een best practice voor beveiligde via HTTPS-verkeer. De service kan worden geconfigureerd voor het gebruik van HTTPS met behulp van een set parameters in de DSC-resource **xPSDesiredStateConfiguration**.

De vereisten voor certificaten voor het beveiligen van HTTPS-verkeer voor pull-server zijn niet anders dan het beveiligen van een andere HTTPS-website. De **webserver** sjabloon in een Windows Server Certificate Services voldoet aan de vereiste mogelijkheden.

Taak plannen|
---|
Als certificaataanvragen niet zijn geautomatiseerd, die u moet contact opnemen met op aanvragen van een certificaat?|
Wat is de gemiddelde doorlooptijd voor de aanvraag?|
Hoe wordt het certificaatbestand worden overgebracht naar u?|
Hoe wordt de persoonlijke sleutel van het certificaat aan u worden overgedragen?|
Hoe lang is de verlooptijd van de standaard?|
Hebt u verrekend op een DNS-naam voor de pull-server-omgeving, die u voor de naam van het certificaat gebruiken kunt?|

### <a name="choosing-an-architecture"></a>Een architectuur kiezen

Een pull-server kan worden geïmplementeerd met behulp van een webservice die zijn gehost op IIS of een SMB-bestandsshare. In de meeste gevallen wordt de web service-optie bieden meer flexibiliteit. Het is niet ongebruikelijk dat HTTPS-verkeer naar de grenzen van het netwerk, door te gaan dat SMB-verkeer is vaak gefilterd of geblokkeerd tussen netwerken. De webservice biedt ook de mogelijkheid om op te nemen van een conformiteit van Server of Web Reporting Manager (beide onderwerpen in een toekomstige versie van dit document worden verholpen) die bieden een mechanisme voor clients voor statusrapportage terug naar een server voor gecentraliseerde zichtbaarheid.
SMB biedt een optie voor omgevingen waar beleid bepaalt dat een webserver niet moet worden gebruikt, en voor andere omgevingsvereisten die een web server-rol ongewenste maken.
Vergeet niet om te evalueren van de vereisten voor het ondertekenen en versleutelen van verkeer in beide gevallen. HTTPS en SMB-ondertekening IPSEC-beleid zijn alle opties waard.

#### <a name="load-balancing"></a>Taakverdeling

Clients communiceren met de webservice te vragen voor informatie die in een enkel antwoord wordt geretourneerd. Er zijn geen opeenvolgende aanvragen zijn vereist, dus het is niet nodig zijn voor de load balancer-platform, zodat er sessies op één server op elk gewenst moment worden bijgehouden in de tijd.

Taak plannen|
---|
Welke oplossing wordt gebruikt voor verkeer te verdelen over meerdere servers?|
Als u een load balancer, die een aanvraag voor het toevoegen van een nieuwe configuratie op het apparaat?|
Wat is de gemiddelde doorlooptijd voor een aanvraag voor het configureren van een nieuwe load balanced webservice?|
Welke gegevens zijn vereist voor de aanvraag?|
Hebt u nodig om aan te vragen van een extra IP-adres of het team dat verantwoordelijk is voor de taakverdeling wordt afgehandeld dat?|
Hebt u de DNS-records die nodig zijn, en deze zijn vereist om het team dat verantwoordelijk is voor het configureren van de load balancer-oplossing?|
De oplossing voor taakverdeling vereist dat de PKI worden verwerkt door het apparaat of saldo HTTPS-verkeer, zolang er geen sessievereisten zijn laden?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Staging-configuraties en -modules op de pull-server

Als onderdeel van de planning van de configuratie, moet u nadenken over welke DSC-modules en configuraties worden gehost door de pull-server. Voor de planning van de configuratie is het belangrijk dat u hebt een basiskennis hebt van het voorbereiden en implementeren van inhoud naar een pull-server.

Deze sectie wordt in de toekomst worden uitgebreid en opgenomen in de Operations Guide voor DSC-Pull-Server.  De handleiding wordt uitgelegd hoe het dagelijkse proces voor het beheren van modules en configuraties na verloop van tijd met automation.

#### <a name="dsc-modules"></a>DSC-modules

Clients die aanvragen van een configuratie moet de vereiste DSC-modules. Een functionaliteit van de pull-server is voor het automatiseren van distributie op aanvraag van DSC-modules voor clients. Als u een pull-server mogelijk als een testomgeving of testen van concept voor het eerst implementeert, gaat u waarschijnlijk afhangen van DSC-modules die beschikbaar via openbare opslagplaatsen, zoals de PowerShell Gallery of de PowerShell.org GitHub-opslagplaatsen voor DSC-modules zijn .

Het is essentieel om te onthouden dat zelfs voor betrouwbare online-bronnen, zoals de PowerShell Gallery, een module die is gedownload vanuit een openbare opslagplaats, moet worden gecontroleerd door iemand met PowerShell-ervaring en kennis van de omgeving waar de modules worden gebruikt voordat het wordt gebruikt in de productieomgeving. Tijdens het uitvoeren van deze taak is het een goed moment om te controleren voor elke extra nettolading in de module die kan worden verwijderd, zoals documentatie en scripts. Zo beperkt u de netwerkbandbreedte per client in de eerste aanvraag wanneer modules worden gedownload via het netwerk van server naar de client.

Elke module moet zijn ingepakt in een specifieke indeling, een ZIP-bestand met de naam ModuleName_Version.zip met de nettolading van de module. Nadat het bestand wordt gekopieerd naar de server die een controlesom-bestand moet worden gemaakt. Wanneer clients verbinding met de server maken, wordt de controlesom gebruikt om te controleren of dat de inhoud van de DSC-module is niet gewijzigd sinds het is gepubliceerd.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

Taak plannen|
---|
Als u van plan bent een omgeving met test- of testomgeving weet welke scenario's sleutel valideren?|
Zijn er openbaar beschikbare modules met resources voor alles wat die u nodig hebt of moet u uw eigen resources maken?|
Wordt uw omgeving hebt u toegang tot Internet om op te halen van openbare modules?|
Wie zijn verantwoordelijk voor het controleren van DSC-modules?|
Als u van plan bent een productie-omgeving wat u gebruikt als een lokale opslagplaats voor het opslaan van DSC-modules?|
Accepteert een centraal team DSC-modules van App-teams? Wat is het proces?|
Wordt u verpakking, kopiëren en het maken van een controlesom voor gereed is voor productie DSC modules met de server uit de opslagplaats van het automatiseren?|
Uw team zijn verantwoordelijk voor het beheren van het automatiseringsplatform?|

#### <a name="dsc-configurations"></a>DSC-configuraties

Het doel van een pull-server is een gecentraliseerde mechanisme voor het distribueren van DSC-configuraties voor de client-knooppunten bieden. De configuraties worden opgeslagen op de server als MOF-documenten.
Elk document worden benoemd met een unieke **Guid**. Wanneer clients verbinding maken met een pull-server worden geconfigureerd, krijgen ze ook de **Guid** voor de configuratie van deze moeten aanvragen. Dit systeem van configuraties door te verwijzen naar **Guid** gegarandeerd uniek globale en flexibele heeft dat kan een configuratie met granulatie per knooppunt, of als een configuratie van de functie die omvat veel servers zijn die moeten worden toegepast configuraties van identieke.

#### <a name="guids"></a>GUID 's

Planning voor de configuratie van **GUID's** de moeite waard is extra aandacht bij via een pull-server-implementatie. Er is geen specifieke vereiste voor het afhandelen van **GUID's** en het proces is waarschijnlijk moet uniek zijn voor elke omgeving. Het proces kan variëren van eenvoudige tot complexe: een centraal opgeslagen CSV-bestand, een eenvoudige SQL-tabel, een CMDB of een complexe oplossingen maken waarvoor integratie met een ander hulpprogramma of software-oplossing nodig. Er zijn twee algemene methoden:

- **Toewijzen van GUID's per server** : biedt een zekere mate van zekerheid dat de configuratie van elke server afzonderlijk wordt beheerd. Dit biedt een precisieniveau om updates en kan ze goed werken in omgevingen met een klein aantal servers.
- **Toewijzen van GUID's per serverfunctie** : alle servers die dezelfde functie, zoals webservers vervullen, gebruikt u dezelfde GUID om te verwijzen naar de vereiste configuratiegegevens.  Er rekening mee dat als veel servers dezelfde GUID delen, al deze zou worden bijgewerkt tegelijkertijd wanneer de configuratie wordt gewijzigd.

  De GUID is iets dat gevoelige gegevens moet worden overwogen omdat deze kan worden gebruikt door iemand met kwade bedoelingen te krijgen van inzicht in hoe servers zijn geïmplementeerd en geconfigureerd in uw omgeving. Zie voor meer informatie, [veilig bij het toewijzen van GUID's in PowerShell Desired State Configuration Pull-modus](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).

Taak plannen|
---|
Wie zijn verantwoordelijk voor het kopiëren van configuraties in naar de map van de pull-server wanneer ze klaar zijn?|
Als configuraties zijn gemaakt door een team van toepassing, wat het proces is om ze uit?|
Gebruik u van een opslagplaats voor het opslaan van configuraties als ze worden gemaakt, tussen teams?|
Automatiseert u het proces van configuraties kopiëren naar de server en het maken van een controlesom wanneer ze klaar zijn?|
Hoe wordt u GUID's toewijzen aan servers of rollen en waar deze worden opgeslagen?|
Wat u gebruikt als een proces voor het configureren van clientcomputers, en hoe wordt deze dan geïntegreerd met het proces voor het maken en opslaan van configuratie-GUID's?|

## <a name="installation-guide"></a>Installatiehandleiding

*Scripts die worden vermeld in dit document zijn stabiel voorbeelden. Altijd zorgvuldig te controleren scripts voordat deze wordt uitgevoerd in een productie-omgeving.*

### <a name="prerequisites"></a>Vereisten

De versie van PowerShell op uw server gebruik de volgende opdracht uit om te controleren.

```powershell
$PSVersionTable.PSVersion
```

Indien mogelijk een upgrade uitvoeren naar de nieuwste versie van Windows Management Framework.
Download vervolgens het `xPsDesiredStateConfiguration` module met behulp van de volgende opdracht uit.

```powershell
Install-Module xPSDesiredStateConfiguration
```

De opdracht vraagt om uw goedkeuring wordt vereist voor het downloaden van de module.

### <a name="installation-and-configuration-scripts"></a>Installatie en configuratie-scripts

De beste methode voor het implementeren van een DSC-pull-server is het gebruik van een script voor DSC-configuratie. Dit document worden gepresenteerd scripts, met inbegrip van beide basisinstellingen die alleen de DSC-webservice configureren en geavanceerde instellingen van een Windows Server-end-to-end met DSC webservice configureren.

Opmerking:  Op dit moment de `xPSDesiredStateConfiguation` DSC-module vereist dat de server om te worden van de landinstelling EN-US.

### <a name="basic-configuration-for-windows-server-2012"></a>Basisinformatie over de configuratie voor Windows Server 2012

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Geavanceerde configuratie voor Windows Server 2012 R2

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a>Controleer de functionaliteit van de pull-server

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>Clients configureren

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a>Aanvullende verwijzingen, codefragmenten en voorbeelden

Dit voorbeeld laat zien hoe u handmatig een clientverbinding tot stand (vereist WMF5) voor het testen.

```powershell
Update-DscConfiguration –Wait -Verbose
```

De [toevoegen DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet een type CNAME-record toevoegen aan een DNS-zone wordt gebruikt.

De PowerShell-functie aan [een controlesom en DSC MOF publiceren met SMB-Pull-Server maken](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) genereert automatisch de vereiste controlesom en vervolgens de configuratie van de MOF- en controlesom bestanden worden gekopieerd naar de SMB-pull-server.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Bijlage - Understanding ODATA-servicegegevens bestandstypen

Een bestand wordt opgeslagen voor het maken van informatie tijdens de implementatie van een pull-server met de OData-webservice. Het type bestand is afhankelijk van het besturingssysteem, zoals hieronder wordt beschreven.

- **Windows Server 2012** het bestandstype is altijd .mdb
- **Windows Server 2012 R2** het bestandstype wordt standaard edb, tenzij een .mdb is opgegeven in de configuratie

In de [voorbeeldscript geavanceerde](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) voor het installeren van een Pull-Server, vindt u ook een voorbeeld van hoe u kunt de instellingen van het bestand web.config om te voorkomen dat elke kans van de fout wordt veroorzaakt door het bestandstype automatisch te bepalen.
