---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Best practices voor pull-servers
ms.openlocfilehash: 7b717e9e3bd753ef287701f3e2406e3fde1e2542
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236251"
---
# <a name="pull-server-best-practices"></a>Best practices voor pull-servers

Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

> [!IMPORTANT]
> De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden. Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.

Samen vatting: dit document is bedoeld om proces en uitbreid baarheid te omvatten om de technici te helpen bij het voorbereiden van de oplossing. Details moeten aanbevolen procedures bieden die door klanten worden geïdentificeerd en vervolgens door het product team worden gevalideerd om ervoor te zorgen dat aanbevelingen op de toekomst worden gericht en stabiel worden beschouwd.

|           |                      Doc-info                      |
| :-------- | :------------------------------------------------- |
| Auteur    | Michael Greene                                     |
| Reviewers | Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic |
| Gepubliceerd | April, 2015                                        |

## <a name="abstract"></a>Abstract

Dit document is ontworpen om officiële richt lijnen te bieden voor iedereen die een Windows Power shell desired state Configuration pull-Server implementatie moet uitvoeren. Een pull-server is een eenvoudige service die slechts enkele minuten mag duren om te implementeren. Hoewel dit document technische instructies biedt die kunnen worden gebruikt in een implementatie, is de waarde van dit document als referentie voor de aanbevolen procedures en wat u moet nadenken voordat u implementeert. Lezers moeten basis kennis hebben van DSC en de voor waarden die worden gebruikt voor het beschrijven van de onderdelen die zijn opgenomen in een DSC-implementatie. Zie het onderwerp [Windows Power shell desired state Configuration (overzicht](/powershell/scripting/dsc/overview/overview) ) voor meer informatie. Aangezien DSC wordt verwacht te ontwikkelen in de Cloud uitgebracht, wordt de onderliggende technologie, inclusief Pull-server, ook verwacht om nieuwe mogelijkheden te ontwikkelen en te introduceren. Dit document bevat een versie tabel in de bijlage die verwijzingen bevat naar eerdere releases en verwijzingen naar toekomstige oplossingen om voorwaartse ontwerpen te stimuleren.

De twee belangrijkste secties van dit document:

- Configuratie planning
- Installatiehandleiding

### <a name="versions-of-the-windows-management-framework"></a>Versies van het Windows Management Framework

De informatie in dit document is bedoeld voor toepassing op Windows Management Framework 5,0. Hoewel WMF 5,0 niet is vereist voor het implementeren en gebruiken van een pull-server, is versie 5,0 de focus van dit document.

### <a name="windows-powershell-desired-state-configuration"></a>Windows Power shell desired state Configuration

Desired state Configuration (DSC) is een beheer platform waarmee configuratie gegevens kunnen worden geïmplementeerd en beheerd met behulp van een industrie syntaxis met de naam de Managed Object Format (MOF) om de Common Information Model (CIM) te beschrijven. Een open-source project, open Management Infrastructure (OMI), bestaat uit het verder ontwikkelen van deze standaarden op verschillende platforms, waaronder Linux en netwerkhardware. Zie voor meer informatie de [DMTF-pagina koppelen aan MOF-specificaties](https://www.dmtf.org/standards/cim)en [Omi-documenten en-bron](https://collaboration.opengroup.org/omi/documents.php).

Windows Power shell biedt een set taal extensies voor desired state Configuration, die u kunt gebruiken om declaratieve configuraties te maken en te beheren.

### <a name="pull-server-role"></a>Server functie pull

Een pull-server biedt een gecentraliseerde service voor het opslaan van configuraties die toegankelijk zijn voor doel knooppunten.

De rol van de pull-server kan worden geïmplementeerd als een webserver instantie of een SMB-bestands share. De webserver-functionaliteit bevat een OData-interface en kan eventueel mogelijkheden voor doel knooppunten bevatten om de bevestiging van het slagen of mislukken van de toepassing te rapporteren. Deze functionaliteit is handig in omgevingen waar zich een groot aantal doel knooppunten bevindt. Na het configureren van een doel knooppunt (ook wel een client genoemd) om naar de pull-server te verwijzen, worden de nieuwste configuratie gegevens en eventuele vereiste scripts gedownload en toegepast. Dit kan gebeuren als een eenmalige implementatie of als een nieuwe taak, waardoor de pull-server ook een belang rijk activum vormt voor het beheer van wijzigingen op schaal. Zie voor meer informatie [Windows Power shell desired state Configuration pull servers](pullserver.md) en [push and pull Configuration mode](pullserver.md)(Engelstalig).

## <a name="configuration-planning"></a>Configuratie planning

Voor elke implementatie van een bedrijfs software is er informatie die van tevoren kan worden verzameld om te helpen bij het plannen van de juiste architectuur en om voor te bereiden op de stappen die nodig zijn om de implementatie te volt ooien. De volgende secties bevatten informatie over de voor bereiding en de organisatie verbindingen die waarschijnlijk van tevoren moeten plaatsvinden.

### <a name="software-requirements"></a>Softwarevereisten

De implementatie van een pull-server vereist de DSC-service functie van Windows Server. Deze functie is geïntroduceerd in Windows Server 2012 en is bijgewerkt via de doorlopende versies van Windows Management Framework (WMF).

### <a name="software-downloads"></a>Software downloads

Naast het installeren van de meest recente inhoud van Windows Update, worden er twee down loads beschouwd als best practice voor het implementeren van een DSC-pull-server: de nieuwste versie van Windows Management Framework en een DSC-module voor het automatiseren van het inrichten van pull-servers.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 bevat een functie met de naam DSC-service. De functie DSC-service biedt de functionaliteit van de pull-server, met inbegrip van de binaire bestanden die ondersteuning bieden voor het OData-eind punt. WMF is opgenomen in Windows Server en wordt bijgewerkt op een flexibele uitgebracht tussen Windows Server-releases.
[Nieuwe versies van WMF 5,0](https://www.microsoft.com/download/details.aspx?id=54616) kunnen updates bevatten voor de functie DSC-service. Daarom is het een best practice om de meest recente versie van WMF te downloaden en de release opmerkingen te bekijken om te bepalen of de release een update voor de DSC-service functie bevat. U moet ook de sectie van de release-opmerkingen door nemen die aangeven of de ontwerp status voor een update of scenario wordt weer gegeven als stabiel of experimenteel. Om een flexibele release cyclus mogelijk te maken, kunnen afzonderlijke functies worden gedeclareerd als stabiel, wat aangeeft dat de functie gereed is om te worden gebruikt in een productie omgeving, zelfs wanneer WMF in Preview wordt uitgebracht. Andere functies die historisch zijn bijgewerkt door WMF-releases (zie opmerkingen bij de WMF-release voor meer informatie):

- Windows Power shell Windows Power shell Integrated Scripting
- Environment (ISE) Windows Power shell-webservices (Management OData
- IIS-uitbrei ding) Windows Power shell desired state Configuration (DSC)
- Windows Management Instrumentation van Windows Remote Management (WinRM) (WMI)

### <a name="dsc-resource"></a>DSC-resource

Een pull-Server implementatie kan worden vereenvoudigd door de service in te richten met behulp van een DSC-configuratie script. Dit document bevat configuratie scripts die kunnen worden gebruikt voor het implementeren van een server knooppunt dat gereed is voor productie. Als u de configuratie scripts wilt gebruiken, is een DSC-module vereist die niet is opgenomen in Windows Server. De vereiste module naam is **xPSDesiredStateConfiguration**, die de DSC-resource **xDscWebService**bevat. De xPSDesiredStateConfiguration-module kan [hier](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d)worden gedownload.

Gebruik de `Install-Module` cmdlet uit de **PowerShellGet** -module.

```powershell
Install-Module xPSDesiredStateConfiguration
```

De module **PowerShellGet** wordt door de module gedownload naar:

`C:\Program Files\Windows PowerShell\Modules`

Taak plannen

- Hebt u toegang tot de installatie bestanden voor Windows Server 2012 R2?
- Heeft de implementatie omgeving via internet toegang tot het downloaden van WMF en de module vanuit de online galerie?
- Hoe installeert u de nieuwste beveiligings updates na de installatie van het besturings systeem?
- Heeft de omgeving Internet toegang om updates te verkrijgen of heeft deze een lokale Windows Server Update Services server (WSUS)?
- Hebt u toegang tot installatie bestanden van Windows Server die al updates bevatten via offline injectie?

### <a name="hardware-requirements"></a>Hardwarevereisten

Pull-server implementaties worden ondersteund op zowel fysieke als virtuele servers. De grootte vereisten voor pull-server worden uitgelijnd met de vereisten voor Windows Server 2012 R2.

- CPU: 1,4 GHz 64-bits processor
- Geheugen: 512 MB
- Schijf ruimte: 32 GB
- Netwerk: Gigabit Ethernet-adapter

Taak plannen

- Gaat u implementeren op fysieke hardware of op een virtualisatieplatform?
- Wat is het proces voor het aanvragen van een nieuwe server voor uw doel omgeving?
- Wat is de gemiddelde verlever tijd voor een server die beschikbaar moet zijn?
- Welke grootte wilt u aanvragen voor de server?

### <a name="accounts"></a>Accounts

Er zijn geen service account vereisten voor het implementeren van een pull-Server exemplaar. Er zijn echter scenario's waarin de website kan worden uitgevoerd in de context van een lokale gebruikers account. Als er bijvoorbeeld een opslag share nodig is voor de inhoud van de website en de Windows-Server of het apparaat dat als host fungeert voor de opslag share, geen lid is van een domein.

### <a name="dns-records"></a>DNS-records

U hebt een server naam nodig om te gebruiken bij het configureren van clients om met een pull-server omgeving te werken.
In test omgevingen wordt doorgaans de hostnaam van de server gebruikt, of het IP-adres voor de server kan worden gebruikt als de DNS-naam omzetting niet beschikbaar is. In productie omgevingen of in een test omgeving die bedoeld is voor een productie-implementatie, bestaat de best practice uit het maken van een DNS CNAME-record.

Met een DNS-CNAME kunt u een alias maken om te verwijzen naar uw host (A)-record. Het doel van de aanvullende naam record is om de flexibiliteit te verg Roten, omdat een wijziging in de toekomst nood zakelijk is. Een CNAME kan u helpen de client configuratie te isoleren zodat wijzigingen in de server omgeving, zoals het vervangen van een pull-server of het toevoegen van extra pull-servers, geen overeenkomstige wijziging in de client configuratie nodig heeft.

Houd bij het kiezen van een naam voor de DNS-record de oplossings architectuur in acht.
Als taak verdeling wordt gebruikt, moet het certificaat dat wordt gebruikt voor het beveiligen van verkeer via HTTPS dezelfde naam hebben als de DNS-record.

|       Scenario        |                                                                                         Best Practice
|:--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
|Testomgeving       | Reproduceer, indien mogelijk, de geplande productie omgeving. Een hostnaam van een server is geschikt voor eenvoudige configuraties. Als DNS niet beschikbaar is, kan een IP-adres worden gebruikt in plaats van een hostnaam.
|Implementatie met één knoop punt | Maak een DNS CNAME-record die verwijst naar de hostnaam van de server.

Zie [Configuring DNS round robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10))(Engelstalig) voor meer informatie.

Taak plannen

- Weet u met wie u contact moet opnemen om DNS-records te maken en te wijzigen?
- Wat is de gemiddelde oplever van een aanvraag voor een DNS-record?
- Moet u statische hostname-records (A) aanvragen voor servers?
- Wat gaat u aanvragen als een CNAME?
- Als dat niet het geval is, welk type taakverdelings oplossing gebruikt u? (Zie de sectie taak verdeling voor meer informatie)

### <a name="public-key-infrastructure"></a>Open bare-sleutel infrastructuur

Voor de meeste organisaties moet het netwerk verkeer, met name verkeer dat gevoelige gegevens bevat, worden gevalideerd en/of versleuteld tijdens de overdracht.
Hoewel het mogelijk is om een pull-server te implementeren met behulp van HTTP, waardoor aanvragen van clients worden vereenvoudigd als ongecodeerde tekst, is het een best practice om verkeer te beveiligen met behulp van HTTPS. De service kan worden geconfigureerd voor het gebruik van HTTPS met behulp van een set para meters in de DSC-resource **xPSDesiredStateConfiguration**.

De certificaat vereisten voor het beveiligen van HTTPS-verkeer voor de pull-server zijn niet anders dan het beveiligen van elke andere HTTPS-website. De **webserver** sjabloon in een Windows Server Certificate Services voldoet aan de vereiste mogelijkheden.

Taak plannen

- Als certificaat aanvragen niet worden geautomatiseerd, wie moet u contact opnemen om een certificaat aan te vragen?
- Wat is de gemiddelde oplever actie voor de aanvraag?
- Hoe wordt het certificaat bestand overgezet?
- Hoe wordt de persoonlijke sleutel van het certificaat overgezet?
- Hoe lang is de standaard verloop tijd?
- Hebt u de DNS-naam voor de pull-server omgeving verrekend, die u voor de certificaat naam kunt gebruiken?

### <a name="choosing-an-architecture"></a>Een architectuur kiezen

Een pull-server kan worden geïmplementeerd met behulp van een webservice die wordt gehost op IIS of een SMB-bestands share. In de meeste gevallen biedt de webservice-optie meer flexibiliteit. Het is niet ongebruikelijk voor HTTPS-verkeer om netwerk grenzen te passeren, terwijl SMB-verkeer vaak wordt gefilterd of geblokkeerd tussen netwerken. De webservice biedt ook de mogelijkheid om een conformiteit server of webrapport Manager op te geven (beide onderwerpen moeten worden behandeld in een toekomstige versie van dit document) die een mechanisme bieden voor clients om de status terug te rapporteren aan een server voor gecentraliseerde zicht baarheid. SMB biedt een optie voor omgevingen waarbij beleids regels bepalen dat een webserver niet moet worden gebruikt en voor andere omgevings vereisten die een webserver functie onwenselijk maken. In beide gevallen moet u de vereisten voor het ondertekenen en versleutelen van verkeer evalueren. HTTPS, SMB-ondertekening en IPSEC-beleid zijn alle opties die u moet overwegen.

#### <a name="load-balancing"></a>Taakverdeling

Clients die communiceren met de webservice maken een aanvraag voor informatie die in één antwoord wordt geretourneerd. Er zijn geen opeenvolgende aanvragen vereist, dus het is niet nodig om ervoor te zorgen dat sessies op één server op elk moment worden onderhouden.

Taak plannen

- Welke oplossing wordt gebruikt voor taak verdeling verkeer tussen servers?
- Als er een hardware-load balancer wordt gebruikt, kan deze een nieuwe configuratie toevoegen aan het apparaat?
- Wat is de gemiddelde verwerkings tijd voor een aanvraag om een nieuwe webservice met gelijke taak verdeling te configureren?
- Welke informatie is vereist voor de aanvraag?
- Moet u een extra IP-adres aanvragen of wordt het team dat verantwoordelijk is voor de taak verdeling?
- Hebt u de DNS-records nodig en is dit vereist voor het team dat verantwoordelijk is voor het configureren van de oplossing voor taak verdeling?
- Moet de oplossing voor taak verdeling vereisen dat de PKI door het apparaat wordt verwerkt of kan het de taak verdeling van HTTPS-verkeer hebben zolang er geen sessie vereisten zijn?

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Faserings configuraties en-modules op de pull-server

Als onderdeel van de configuratie planning moet u nadenken over welke DSC-modules en configuraties worden gehost door de pull-server. Voor het plannen van de configuratie is het belang rijk dat u een basis memorandum hebt van het voorbereiden en implementeren van inhoud op een pull-server.

In de toekomst wordt deze sectie uitgebreid en opgenomen in een Operations Guide voor de DSC-pull-server. In de hand leiding wordt het dagelijkse proces voor het beheren van modules en configuraties in de loop van de tijd met automatisering besproken.

#### <a name="dsc-modules"></a>DSC-modules

Clients die een configuratie aanvragen, hebben de vereiste DSC-modules nodig. Een functionaliteit van de pull-server is het automatiseren van de distributie op aanvraag van DSC-modules naar clients. Als u een pull-server voor de eerste keer implementeert, bijvoorbeeld een Lab of concept, is het waarschijnlijk afhankelijk van de DSC-modules die beschikbaar zijn vanuit open bare opslag plaatsen, zoals de PowerShell Gallery of de PowerShell.org GitHub-opslag plaatsen voor DSC-modules.

Het is belang rijk om te onthouden dat zelfs voor vertrouwde online bronnen, zoals de PowerShell Gallery, elke module die wordt gedownload uit een open bare opslag plaats moet worden gecontroleerd door iemand met een Power shell-ervaring en kennis van de omgeving waarin de modules worden gebruikt voordat deze in productie worden gebruikt. Bij het volt ooien van deze taak is het een goed idee om te controleren of er extra Payload in de module is die kan worden verwijderd, zoals documentatie en voorbeeld scripts. Hiermee wordt de netwerk bandbreedte per client in de eerste aanvraag verminderd, wanneer modules via het netwerk van de server naar de client worden gedownload.

Elke module moet worden verpakt in een specifieke indeling, een ZIP-bestand met de naam ModuleName_Version.zip dat de module Payload bevat. Nadat het bestand is gekopieerd naar de server, moet er een controlesom bestand worden gemaakt.
Wanneer clients verbinding maken met de server, wordt de controlesom gebruikt om te controleren of de inhoud van de DSC-module niet is gewijzigd sinds deze is gepubliceerd.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

Taak plannen

- Als u van plan bent een test-of lab-omgeving te plannen, welke scenario's zijn de sleutel die moet worden gevalideerd?
- Zijn er openbaar beschik bare modules die resources bevatten voor alles wat u nodig hebt, of moet u uw eigen resources maken?
- Heeft uw omgeving Internet toegang om open bare modules op te halen?
- Wie is verantwoordelijk voor het beoordelen van DSC-modules?
- Als u een productie omgeving plant, kunt u deze gebruiken als lokale opslag plaats voor het opslaan van DSC-modules?
- Wordt een centraal team DSC-modules geaccepteerd van toepassings teams? Wat is het proces?
- Automatiseert u de verpakking, het kopiëren en het maken van een controlesom voor DSC-modules die gereed zijn voor productie naar de-server, vanuit uw bron-opslag plaats?
- Is uw team ook verantwoordelijk voor het beheer van het automatiserings platform?

#### <a name="dsc-configurations"></a>DSC-configuraties

Het doel van een pull-server is het bieden van een gecentraliseerd mechanisme voor het distribueren van DSC-configuraties naar client knooppunten. De configuraties worden op de server als MOF-documenten opgeslagen. Elk document krijgt een unieke **GUID**. Wanneer clients zijn geconfigureerd om verbinding te maken met een pull-server, krijgen ze ook de **GUID** voor de configuratie die ze moeten aanvragen. Dit systeem voor het verwijzen naar configuraties door de **GUID** garandeert globale uniekheid en is flexibel, zodat een configuratie kan worden toegepast met granulatie per knoop punt, of als een functie configuratie die veel servers bevat die identieke configuraties moeten hebben.

#### <a name="guids"></a>Guid's

Het plannen van configuratie- **guid's** is extra aandacht wanneer u een pull-Server implementatie overweegt. Er is geen specifieke vereiste voor het afhandelen van **guid's** en het proces is waarschijnlijk uniek voor elke omgeving. Het proces kan variëren van eenvoudig tot complex: een centraal opgeslagen CSV-bestand, een eenvoudige SQL-tabel, een CMDB of een complexe oplossing die integratie met een ander hulp programma of software oplossing vereist. Er zijn twee algemene benaderingen:

- Het **toewijzen van guid's per server** — biedt een mate van zekerheid dat elke server configuratie afzonderlijk wordt beheerd. Dit biedt een nauwkeurigheids niveau voor updates en kan goed worden gebruikt in omgevingen met weinig servers.
- Het **toewijzen van guid's per serverrol** : alle servers die dezelfde functie uitvoeren, zoals webservers, gebruiken dezelfde GUID om te verwijzen naar de vereiste configuratie gegevens. Houd er rekening mee dat als veel servers dezelfde GUID delen, deze allemaal tegelijkertijd worden bijgewerkt wanneer de configuratie wordt gewijzigd.

  De GUID is iets wat moet worden beschouwd als gevoelige gegevens omdat deze kan worden gebruikt door iemand met kwaad aardigheid om informatie te verkrijgen over hoe servers worden geïmplementeerd en geconfigureerd in uw omgeving. Zie voor meer informatie [veilig toewijzing van guid's in Power shell pull-modus voor desired state Configuration](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).

Taak plannen

- Wie is verantwoordelijk voor het kopiëren van configuraties in de map van de pull-server wanneer deze klaar zijn?
- Als er configuraties worden gemaakt door een toepassings team, wat moet het proces dan hand matig worden afgebroken?
- Maakt u gebruik van een opslag plaats voor het opslaan van configuraties zoals ze worden geschreven in teams?
- Automatiseert u het proces van het kopiëren van configuraties naar de server en het maken van een controlesom wanneer deze klaar zijn?
- Hoe wijst u Guid's toe aan servers of rollen en waar wordt deze opgeslagen?
- Wat gaat u gebruiken als een proces voor het configureren van client computers en hoe wordt het geïntegreerd met uw proces voor het maken en opslaan van configuratie-Guid's?

## <a name="installation-guide"></a>Installatiehandleiding

*De in dit document gegeven scripts zijn stabiele voor beelden. Controleer altijd de scripts zorgvuldig voordat u ze in een productie omgeving uitvoert.*

### <a name="prerequisites"></a>Vereisten

Gebruik de volgende opdracht om de versie van Power shell op uw server te controleren.

```powershell
$PSVersionTable.PSVersion
```

Voer, indien mogelijk, een upgrade uit naar de nieuwste versie van Windows Management Framework. Down load vervolgens de `xPsDesiredStateConfiguration` module met de volgende opdracht.

```powershell
Install-Module xPSDesiredStateConfiguration
```

De opdracht wordt gevraagd naar uw goed keuring voordat u de module downloadt.

### <a name="installation-and-configuration-scripts"></a>Installatie-en configuratie scripts

De beste methode voor het implementeren van een DSC-pull-server is het gebruik van een DSC-configuratie script. In dit document worden de scripts weer gegeven, inclusief de basis instellingen waarmee alleen de DSC-webservice en geavanceerde instellingen worden geconfigureerd waarmee een end-to-end-service van Windows Server wordt geconfigureerd, inclusief de DSC-webservice.

Opmerking: de `xPSDesiredStateConfiguration` DSC-module vereist momenteel dat de server is ingesteld op de land instelling en-us.

### <a name="basic-configuration-for-windows-server-2012"></a>Basis configuratie voor Windows Server 2012

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
# This is an advanced Configuration example for Pull Server production deployments
# on Windows Server 2012 R2. Many of the features demonstrated are optional and
# provided to demonstrate how to adapt the Configuration for multiple scenarios
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

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority,
        # complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider
        # modifying the default port, possibly leveraging port 443 in environments where that is
        # enforced as a standard.
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

### <a name="verify-pull-server-functionality"></a>De functionaliteit van de pull-server controleren

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the
# default service URL, you will need to adjust accordingly.
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

## <a name="additional-references-snippets-and-examples"></a>Aanvullende verwijzingen, fragmenten en voor beelden

In dit voor beeld ziet u hoe u hand matig een client verbinding start (vereist WMF5) voor het testen.

```powershell
Update-DscConfiguration –Wait -Verbose
```

De cmdlet [add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) wordt gebruikt om een type CNAME-record toe te voegen aan een DNS-zone.

De Power shell-functie voor het [maken van een controlesom en het publiceren van DSC MOF naar SMB pull-server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) genereert automatisch de vereiste controlesom en kopieert vervolgens zowel de MOF-configuratie als de controlesom bestanden naar de SMB-pull-server.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Bijlage: informatie over ODATA-service gegevens bestands typen

Er wordt een gegevens bestand opgeslagen om informatie te maken tijdens de implementatie van een pull-server die de OData-webservice bevat. Het type bestand is afhankelijk van het besturings systeem, zoals hieronder wordt beschreven.

- **Windows Server 2012** Het bestands type is altijd. mdb
- **Windows Server 2012 R2** Het bestands type wordt standaard ingesteld op. edb tenzij er een. mdb is opgegeven in de configuratie

In het [geavanceerde voorbeeld script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) voor het installeren van een pull-Server vindt u ook een voor beeld van het automatisch beheren van de bestands instellingen van web.config om te voor komen dat er een fout wordt veroorzaakt door het bestands type.
