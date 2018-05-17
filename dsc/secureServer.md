---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Best practices voor pull-servers
ms.openlocfilehash: 1efc016df6882fa962f59dfd3e53eaa6d6b0c121
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="pull-server-best-practices"></a>Best practices voor pull-servers

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> De Pull-Server (Windows-onderdeel *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om de nieuwe functies en mogelijkheden bieden. Het verdient aanbeveling om te beginnen met een overgang clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen vermeld [hier](pullserver.md#community-solutions-for-pull-service).

Overzicht: Dit document is bedoeld om het proces en uitbreidingsmogelijkheden engineers die voor de oplossing voorbereiden zich helpen bevatten. Gegevens moeten best practices te geven aangeduid met klanten en vervolgens worden gevalideerd door het productteam om ervoor te zorgen aanbevelingen toekomstige verbonden zijn en als stabiel beschouwd.

| |Informatie over dit document|
|:---|:---|
auteur | Michael Greene
Revisoren | Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic
Gepubliceerd | April 2015

## <a name="abstract"></a>Abstracte

Dit document is ontworpen voor de officiële richtlijnen voor iedereen plannen voor een implementatie van Windows PowerShell Desired State Configuration pull-server. Een pull-server is een eenvoudige service die alleen minuten te implementeren. Hoewel dit document technische procedures richtlijnen die kan worden gebruikt in een implementatie biedt, is de waarde van dit document als een verwijzing voor aanbevolen procedures en wat u moet denken voordat u implementeert.
Lezers enigszins bekend bent met DSC moeten hebben en de voorwaarden voor het beschrijven van de onderdelen die zijn opgenomen in een DSC-implementatie. Zie voor meer informatie de [Windows PowerShell Desired Configuration overzicht](https://technet.microsoft.com/library/dn249912.aspx) onderwerp.
Zoals DSC wordt verwacht op cloud uitgebracht ontwikkelen, worden de onderliggende technologie inclusief pull-server wordt ook verwacht ontwikkelen en nieuwe mogelijkheden bieden. Dit document bevat een versietabel in de bijlage die voorziet in verwijzingen naar de vorige releases en verwijzingen naar toekomstige Zoek oplossingen te moedigen toekomstgerichte ontwerpen.

De twee hoofdonderdelen van dit document:

 - Planning van de configuratie
 - Installatiehandleiding

### <a name="versions-of-the-windows-management-framework"></a>Versies van het Windows Management Framework
De informatie in dit document is bedoeld om te passen op Windows Management Framework 5.0. WMF 5.0 is niet vereist voor de implementatie en het gebruik van een pull-server, is versie 5.0 de focus van dit document.

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell Desired State Configuration
Desired State Configuration (DSC) is een beheerplatform waarmee configuratiegegevens implementeren en beheren met behulp van een industrie-syntaxis Managed Object Format (MOF) met de naam voor het beschrijven van het Common Information Model (CIM). Er bestaat een open source-project, Open Management Infrastructure (OMI), om verdere ontwikkeling van deze standaarden in verschillende platforms, waaronder Linux en -netwerkbesturingssystemen hardware. Zie voor meer informatie de [DMTF pagina koppelen aan MOF specificaties](http://dmtf.org/standards/cim), en [OMI documenten en bron](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell biedt een set met taaluitbreidingen voor Desired State Configuration waarmee u kunt maken en beheren van declaratieve configuraties.

### <a name="pull-server-role"></a>Pull-serverfunctie
Een pull-server biedt een gecentraliseerde service voor het opslaan van de configuraties die toegankelijk is voor de doelknooppunten.

De functie van de pull-server kan worden geïmplementeerd als een Web Server-exemplaar of een SMB-bestandsshare. De mogelijkheid van web server bevat een OData-interface en kunt u eventueel opnemen mogelijkheden voor de doelknooppunten om te rapporteren terug bevestiging van het slagen of mislukken als configuraties zijn toegepast. Deze functionaliteit is handig in omgevingen wanneer er een groot aantal doelknooppunten.
Na het configureren van een doelknooppunt (ook wel een client genoemd) om te verwijzen naar de pull-server de configuratie van de meest recente zijn gegevens en alle vereiste scripts gedownload en toegepast. Dit kan gebeuren als een eenmalige implementatie of als een taak voor opnieuw voorkomende waardoor dit ook de pull-server een belangrijk onderdeel voor het beheren van de wijziging op grote schaal. Zie voor meer informatie [Windows PowerShell Desired status Pull-configuratieservers](https://technet.microsoft.com/library/dn249913.aspx) en [Push als Pull-Configuratiemodi](https://technet.microsoft.com/library/dn249913.aspx).

## <a name="configuration-planning"></a>Planning van de configuratie

Er is voor de implementatie van enterprise software informatie die vooraf kan worden verzameld om u te helpen bij het plannen voor de juiste architectuur en om te worden voorbereid voor de stappen die nodig zijn om de implementatie te vervolledigen. De volgende secties bevatten informatie over het voorbereiden en de organisatie-verbindingen die waarschijnlijk moet van tevoren gebeuren.

### <a name="software-requirements"></a>Softwarevereisten

Implementatie van een pull-server vereist de functie DSC-Service van Windows Server. Deze functie is geïntroduceerd in Windows Server 2012 en via lopende versies van Windows Management Framework (WMF) is bijgewerkt.

### <a name="software-downloads"></a>Softwaredownloads

Naast de meest recente inhoud vanaf Windows Update installeert, zijn er twee downloads beschouwd als aanbevolen procedure voor het implementeren van een DSC-pull-server: de meest recente versie van Windows Management Framework en een DSC-module voor het automatiseren van de inrichting van pull-server.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 bevat een functie met de naam de DSC-Service. De functie DSC-Service biedt de functionaliteit pull-server, met inbegrip van de binaire bestanden die ondersteuning bieden voor de OData-eindpunt.
WMF is opgenomen in Windows Server en een flexibele uitgebracht tussen versies van Windows Server wordt bijgewerkt. [Nieuwe versies van WMF 5.0](http://aka.ms/wmf5latest) kunt bevatten updates voor de functie DSC-Service. Daarom is een aanbevolen procedure voor het downloaden van de nieuwste versie van WMF en om te controleren van de release-opmerkingen om te bepalen of de versie een update op de functie voor DSC-service bevat. U moet ook de sectie van de release-opmerkingen die aangeeft of de status van het ontwerp voor een update of scenario wordt vermeld als stabiel of experimentele bekijken.
Als u wilt toestaan voor een flexibele releasecyclus afzonderlijke functies worden gedeclareerd stabiele, is wat aangeeft dat de functie gereed om te worden gebruikt in een productieomgeving, zelfs terwijl WMF Preview-versie wordt uitgebracht.
Andere functies die in het verleden zijn bijgewerkt door WMF-versies (Zie de opmerkingen bij de Release van WMF voor verdere details):

 - Windows PowerShell, Windows PowerShell Integrated Scripting
 - Environment (ISE) Windows PowerShell-webservices (Management OData
 - IIS-extensie) Windows PowerShell Desired State Configuration (DSC)
 - Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)

### <a name="dsc-resource"></a>DSC-resource

De implementatie van een pull-server kan worden vereenvoudigd door de service met een DSC-configuratiescript inricht. Dit document bevat configuratiescripts die kunnen worden gebruikt voor het implementeren van een knooppunt van de server gereed productie. Voor het gebruik van de configuratiescripts een DSC-module is vereist dat niet is opgenomen in Windows Server. De vereiste modulenaam **xPSDesiredStateConfiguration**, waaronder de DSC-resource **xDscWebService**. De module xPSDesiredStateConfiguration kan worden gedownload [hier](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Gebruik de **Install-Module** cmdlet uit de **PowerShellGet** module.

```powershell
Install-Module xPSDesiredStateConfiguration
```

De **PowerShellGet** module zal de module die u wilt downloaden:

`C:\Program Files\Windows PowerShell\Modules`

Taak plannen|
---|
Hebt u toegang tot de installatiebestanden voor Windows Server 2012 R2?|
De implementatieomgeving internettoegang hebben tot WMF en de module downloaden vanaf de on line galerie?|
Hoe wordt u de meest recente beveiligingsupdates na de installatie van het besturingssysteem installeren?|
Wordt de omgeving hebben toegang tot het Internet om updates te downloaden of wordt er een lokale server met Windows Server Update Services (WSUS)?|
Hebt u toegang tot Windows Server-installatiebestanden die al updates via offline injectie zijn?|

### <a name="hardware-requirements"></a>Hardwarevereisten

Implementaties van pull-server worden ondersteund op fysieke en virtuele servers. De sizing vereisten voor pull-server worden uitgelijnd met de vereisten voor Windows Server 2012 R2.

Processor: 1,4 GHz, 64-bits processor geheugen: 512 MB aan schijfruimte: 32 GB netwerk: Gigabit Ethernet-Adapter

Taak plannen|
---|
U implementeert op fysieke hardware of op een virtualisatieplatform?|
Wat is het proces voor het aanvragen van een nieuwe server voor de doelomgeving?|
Wat is de gemiddelde verwerkingstijd voor een server beschikbaar?|
Welke server grootte vraagt u de?|

### <a name="accounts"></a>Accounts

Er zijn geen vereisten voor serviceaccount voor het implementeren van een pull-server-exemplaar.
Er zijn echter scenario's waarin de website kan worden uitgevoerd in de context van een lokale gebruikersaccount.
Bijvoorbeeld, als er nodig is toegang tot een storage-share voor website-inhoud en de Windows-Server of het apparaat waarop de storage-share zijn niet verbonden met het domein.

### <a name="dns-records"></a>DNS-records

U moet een servernaam moet worden gebruikt wanneer clients configureren voor gebruik met een pull-server-omgeving.
De hostnaam van de server wordt meestal gebruikt in een testomgeving, of het IP-adres voor de server kan worden gebruikt als DNS-naamomzetting niet beschikbaar is.
In productieomgevingen of in een testomgeving die is bedoeld voor een productie-implementatie, is de aanbevolen procedure om een DNS CNAME-record te maken.

Een DNS CNAME kunt u een alias om te verwijzen naar de host-A-record maken.
De bedoeling van de naamrecord van de aanvullende is om de flexibiliteit te vergroten, moet een wijziging zijn vereist in de toekomst.
Kunt u een CNAME isoleren van configuratie van de client, zodat de wijzigingen in de server-omgeving, zoals een pull-server vervangen of toevoegen van extra pull-servers, is een overeenkomstige wijziging in de configuratie van de client niet vereist.

Houd rekening met de oplossingsarchitectuur bij het kiezen van een naam voor de DNS-record.
Als met behulp van taakverdeling, wordt het certificaat dat wordt gebruikt om verkeer te beveiligen via HTTPS moet dezelfde naam als de DNS-record.

Scenario |Best practices
:---|:---
Testomgeving |De geplande productie-omgeving, indien mogelijk reproduceren. Een hostnaam voor de server is geschikt voor eenvoudige configuraties. Als DNS niet beschikbaar is, kan een IP-adres in plaats van een hostnaam worden gebruikt.|
Implementatie van één knooppunt |Maak een DNS CNAME-record die naar de hostnaam van de server verwijst.|

Zie voor meer informatie [DNS Round Robin configureren in Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).

Taak plannen|
---|
Weet u contactpersoon om DNS-records gemaakt en gewijzigd?|
Wat is de gemiddelde reactietijd voor een aanvraag voor een DNS-record ook?|
Moet u de statische Hostname-A-records voor servers aanvragen?|
Wat u vraagt de als een CNAME?|
Indien nodig, wat voor soort Load Balancing-oplossing wordt u gebruiken? (Zie de sectie taakverdeling voor meer informatie)|

### <a name="public-key-infrastructure"></a>Openbare-sleutelinfrastructuur

De meeste organisaties vereisen vandaag dat netwerkverkeer, met name verkeer dat dergelijke gevoelige gegevens bevat, hoe servers zijn geconfigureerd, moet worden gevalideerd en/of tijdens de overdracht versleuteld.
Het is mogelijk voor het implementeren van een pull-server via HTTP wat vergemakkelijkt clientaanvragen in normale tekst, is het beste beveiligd verkeer via HTTPS. De service kan worden geconfigureerd voor het gebruik van HTTPS met behulp van een set parameters in de DSC-resource **xPSDesiredStateConfiguration**.

Certificaatvereisten voor het beveiligen van HTTPS-verkeer voor pull-server zijn niet anders dan een andere HTTPS-website te beveiligen. De **webserver** sjabloon in een Windows Server Certificate Services voldoet aan de vereiste mogelijkheden.

Taak plannen|
---|
Als certificaataanvragen niet worden geautomatiseerd, die u moet contact op aanvragen van een certificaat?|
Wat is de gemiddelde reactietijd ook voor de aanvraag?|
Hoe wordt het certificaatbestand overgedragen voor u?|
Hoe wordt de persoonlijke sleutel van het certificaat worden overgebracht naar u?|
Hoe lang is de verlooptijd van de standaard?|
Hebt u verrekend op een DNS-naam voor de pull-server-omgeving, die u voor de certificaatnaam gebruiken kunt?|

### <a name="choosing-an-architecture"></a>Een architectuur kiezen

Een pull-server kan worden geïmplementeerd via een webservice die zijn gehost op IIS of een SMB-bestandsshare. In de meeste gevallen wordt de optie web service bieden meer flexibiliteit. Het is niet ongewoon is voor HTTPS-verkeer naar de grenzen van netwerken, passeren dat SMB-verkeer is vaak gefilterd of geblokkeerd tussen netwerken. De web-service biedt ook de optie een overeenstemming Server of Web Reporting Manager (zowel onderwerpen worden opgelost in een toekomstige versie van dit document) die bieden een mechanisme voor clients voor statusrapportage terug naar een server voor gecentraliseerde zichtbaarheid op te nemen.
SMB biedt een optie voor omgevingen waar beleid bepaalt dat een webserver niet worden gebruikt en voor andere omgevingsvereisten waaruit een Webserverrol ongewenste.
In beide gevallen moet u evalueren van de vereisten voor het ondertekenen en versleutelen van verkeer. HTTPS, SMB-ondertekening en IPSEC-beleidsregels zijn alle opties waard.

#### <a name="load-balancing"></a>Taakverdeling
Clients communiceren met de webservice indienen voor informatie die in een enkel antwoord wordt geretourneerd. Er zijn geen opeenvolgende aanvragen zijn vereist, zodat het niet nodig zijn voor het platform om ervoor te zorgen sessies worden beheerd op één server op elk punt in tijd voor de taakverdeling.

Taak plannen|
---|
Welke oplossing voor taakverdeling verkeer tussen servers worden gebruikt?|
Als een load balancer, die een aanvraag voor het toevoegen van een nieuwe configuratie op het apparaat te laten gebruiken?|
Wat is de gemiddelde reactietijd ook voor een aanvraag voor het configureren van een nieuwe load balanced webservice?|
Welke informatie is alleen vereist voor de aanvraag?|
U moet aanvragen een extra IP-adres of het team dat verantwoordelijk is voor de taakverdeling wordt afgehandeld die?|
Hebt u de DNS-records die nodig zijn en wordt dit door het team dat verantwoordelijk is voor het configureren van de oplossing voor taakverdeling worden vereist?|
De load balancing oplossing vereist dat de PKI worden verwerkt door het apparaat of saldo HTTPS-verkeer, zolang er geen sessievereisten zijn laden?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Fasering configuraties en modules op de pull-server

Als onderdeel van de planning van de configuratie, moet u nadenken over welke DSC-modules en configuraties die wordt gehost door de pull-server. Omwille van de planning van de configuratie is het belangrijk dat u basiskennis van het voorbereiden en implementeren van inhoud naar een pull-server.

In de toekomst wordt in deze sectie uitgebreid en opgenomen in de Operations Guide voor DSC-Pull-Server.  De handleiding wordt uitgelegd hoe het dagelijkse proces voor het beheren van modules en configuraties gedurende een periode met automation.

#### <a name="dsc-modules"></a>DSC-modules
Clients die aanvragen van een configuratie moet de vereiste DSC-modules. Een functionaliteit van de pull-server is voor het automatiseren van distributie op verzoek van DSC-modules voor clients. Als u een pull-server mogelijk als een lab of het testen van het concept voor de eerste keer implementeert, gaat u waarschijnlijk afhangen van DSC-modules die beschikbaar via openbare opslagplaatsen zoals de galerie met PowerShell of de PowerShell.org GitHub-opslagplaatsen voor DSC-modules zijn .

Het is essentieel dat zelfs voor vertrouwde online-bronnen zoals de PowerShell-galerie, elke module die is gedownload van een openbare opslagplaats moet worden gecontroleerd door iemand met PowerShell-ervaring en kennis van de omgeving waar de modules worden onthouden gebruikt voordat het wordt gebruikt in productie. Tijdens het uitvoeren van deze taak is het een goed moment om te controleren voor elke extra nettolading in de module die zoals documentatie en voorbeeld-scripts kan worden verwijderd. Zo beperkt u de netwerkbandbreedte per client in de eerste aanvraag wanneer modules worden gedownload via het netwerk van de server met de client.

Elke module moet worden verpakt in een specifieke indeling, een ZIP-bestand met de naam ModuleName_Version.zip waarin de nettolading van de module. Nadat het bestand is gekopieerd naar de server die een controlesom-bestand moet worden gemaakt. Wanneer clients verbinding met de server maken, wordt de controlesom gebruikt om te controleren of dat de inhoud van de DSC-module niet is gewijzigd sinds het is gepubliceerd.

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

Taak plannen|
---|
Als u van plan bent een test- of testomgeving omgeving weet welke scenario's sleutel om te valideren?|
Zijn er openbaar beschikbare modules die bronnen ten aanzien van alles wat die u moet bevatten of u moet uw eigen resources ontwerpen?|
Uw omgeving internettoegang hebben tot openbare modules ophalen?|
Wie is verantwoordelijk voor het controleren van de DSC-modules?|
Als u van plan bent een productie-omgeving wat u gebruikt als een lokale opslagplaats voor het opslaan van DSC-modules?|
Een centrale team DSC-modules van App-teams accepteert? Wat is het proces|
Wordt u verpakking, kopiëren en een controlesom voor gereed is voor productie DSC modules maken met de server uit de opslagplaats van uw bron automatiseren?|
Kan uw team zijn verantwoordelijk voor het beheren van het automatiseringsplatform?|

#### <a name="dsc-configurations"></a>DSC-configuraties

Het doel van een pull-server is bieden een gecentraliseerde mechanisme voor het distribueren van DSC-configuraties voor client-knooppunten. De configuraties worden opgeslagen op de server als MOF-documenten.
Elk document worden benoemd met een unieke GUID. Wanneer clients verbinding maken met een pull-server worden geconfigureerd, krijgen ze ook de GUID voor de configuratie die moet aanvragen. Dit systeem voor het verwijzen naar configuraties door GUID wordt gegarandeerd dat globale uniekheid en flexibele zodanig is dat een configuratie met een granulatie per knooppunt, of als een configuratie van de functie die veel servers met identieke configuraties omvat kan worden toegepast.

#### <a name="guids"></a>GUID 's

Planning voor de configuratie van GUID's is waard extra aandacht bij gegevensclassificatie via de implementatie van een pull-server. Er is geen specifieke vereiste voor het verwerken van GUID's en het proces is waarschijnlijk uniek voor elke omgeving. Het proces kan variëren van eenvoudige tot complexe: een centraal opgeslagen CSV-bestand, een eenvoudige SQL-tabel, een CMDB of een complexe oplossing integratie met een andere oplossing voor hulpprogramma's of software vereisen. Er zijn twee algemene methoden:

 - **Toewijzen van GUID's per server** : biedt een zekere mate van zekerheid dat de configuratie van elke server afzonderlijk wordt beheerd. Dit biedt een niveau van precisie rond updates en kunt werken goed in omgevingen met enkele servers.
 - **Toewijzen van GUID's per serverfunctie** : alle servers die dezelfde functie, zoals webservers, uitvoeren met dezelfde GUID verwijzen naar de vereiste configuratiegegevens.  Let wel dat als veel servers dezelfde GUID delen, deze zou worden bijgewerkt tegelijkertijd wanneer de configuratie wordt gewijzigd.

De GUID is iets die gevoelige gegevens moeten worden overwogen omdat deze kan worden gebruikt door iemand met kwade bedoelingen intelligence over hoe de servers zijn geïmplementeerd en geconfigureerd in uw omgeving te krijgen. Zie voor meer informatie [veilig toewijzen van GUID's in PowerShell Desired status Pull-configuratiemodus](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).

Taak plannen|
---|
Wie is verantwoordelijk voor het kopiëren van configuraties in naar de map van de pull-server wanneer ze gereed zijn?|
Als configuraties zijn gemaakt door een toepassingsteam van, wat het proces is op deze aanlevert?|
Wordt u gebruikmaken van een opslagplaats voor het opslaan van configuraties als ze worden gemaakt, verschillende teams?|
Automatiseert het proces van het kopiëren van configuraties naar de server en het maken van een controlesom wanneer ze gereed zijn?|
Hoe wordt u GUID's toewijzen aan servers of -rollen en waar dit worden opgeslagen?|
Wat u gebruikt als een proces voor het configureren van clientcomputers en hoe wordt geïntegreerd met uw proces voor het maken en opslaan van de configuratie van GUID's?|

## <a name="installation-guide"></a>Installatiehandleiding

*Scripts die zijn opgegeven in dit document zijn stabiele voorbeelden. Altijd zorgvuldig te controleren scripts voordat deze wordt uitgevoerd in een productieomgeving.*

### <a name="prerequisites"></a>Vereisten

De versie van PowerShell op uw server gebruik de volgende opdracht om te controleren.

```powershell
$PSVersionTable.PSVersion
```

Indien mogelijk een upgrade uitvoeren naar de nieuwste versie van Windows Management Framework.
Download vervolgens het `xPsDesiredStateConfiguration` module met behulp van de volgende opdracht.


```powershell
Install-Module xPSDesiredStateConfiguration
```

De opdracht vraagt naar uw goedkeuring wordt vereist voor het downloaden van de module.

### <a name="installation-and-configuration-scripts"></a>Installatie en configuratie-scripts
-

De beste methode voor het implementeren van een DSC-pull-server is een DSC-configuratiescript gebruiken. Dit document biedt zowel basisinstellingen die alleen de DSC-webservice configureren en geavanceerde instellingen dat er een Windows Server end-to-end inclusief DSC webservice configureren waaronder scripts.

Opmerking: Op dit moment de `xPSDesiredStateConfiguation` DSC-module vereist dat de server moet de landinstelling EN-US.

### <a name="basic-configuration-for-windows-server-2012"></a>Basisconfiguratie voor Windows Server 2012
-------------------------------------------
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
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN'

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


## <a name="additional-references-snippets-and-examples"></a>Aanvullende verwijzingen, fragmenten en voorbeelden

Dit voorbeeld toont hoe u handmatig een clientverbinding tot stand (vereist WMF5) voor het testen.

```powershell
Update-DSCConfiguration –Wait -Verbose
```

De [toevoegen DnsServerResourceRecordName](http://bit.ly/1G1H31L) -cmdlet gebruikt voor een type CNAME-record toevoegen aan een DNS-zone.

De functie PowerShell [een controlesom en DSC-MOF publiceren met SMB Pull-Server maken](http://bit.ly/1E46BhI) genereert automatisch de vereiste controlesom en kopieert u de configuratie van de MOF- en controlesom bestanden naar de SMB-pull-server.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Bijlage - Understanding ODATA-servicegegevens bestandstypen

Een bestand wordt opgeslagen als u wilt maken van gegevens tijdens de implementatie van een pull-server met de OData-webservice. Het type bestand is afhankelijk van het besturingssysteem, zoals hieronder wordt beschreven.

 - **Windows Server 2012** het bestandstype worden altijd .mdb
 - **Windows Server 2012 R2** het bestandstype wordt standaard edb tenzij een .mdb is opgegeven in de configuratie

In de [voorbeeldscript geavanceerde](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) voor het installeren van een Pull-Server, vindt u ook een voorbeeld van hoe u kunt de instellingen van het bestand web.config om te voorkomen dat een kans van de fout is veroorzaakt door het bestandstype automatisch te bepalen.