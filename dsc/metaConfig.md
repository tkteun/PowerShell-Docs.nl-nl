---
ms.date: 2017-10-11
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De lokale Configuration Manager configureren
ms.openlocfilehash: 947bc17347204f6f15a24f83b449582afe65a4ee
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="configuring-the-local-configuration-manager"></a>De lokale Configuration Manager configureren

> Van toepassing op: Windows PowerShell 5.0

De lokale Configuration Manager (LCM) is de engine van Desired State Configuration (DSC).
De LCM wordt uitgevoerd op elk doelknooppunt en is verantwoordelijk voor het parseren en configuraties die worden verzonden naar het knooppunt vast te stellen.
Het is ook verantwoordelijk is voor een aantal andere aspecten van DSC, waaronder de volgende.

- Bepalen van vernieuwingsmodus (push of pull).
- Opgeven hoe vaak een knooppunt ophaalt en enacts configuraties.
- Koppelen van het knooppunt met pull-service.
- Gedeeltelijke configuraties op te geven.

Een speciaal soort configuratie kunt u de LCM om op te geven van elk van deze handelingen configureren.
De volgende secties wordt beschreven hoe de LCM configureren.

> **Opmerking**: dit onderwerp geldt voor de LCM geïntroduceerd in Windows PowerShell 5.0.
Zie voor meer informatie over het configureren van de LCM in Windows PowerShell 4.0 [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Schrijven en de configuratie van een LCM vast te stellen

Voor het configureren van de LCM u maken en uitvoeren van een speciaal soort configuratie die LCM instellingen toegepast.
Als u een configuratie LCM, moet u het kenmerk DscLocalConfigurationManager gebruiken.
Hieronder ziet u een eenvoudige configuratie stelt de LCM push-modus.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

Het proces van het toepassen van instellingen op LCM is vergelijkbaar met het toepassen van een DSC-configuratie.
U een configuratie LCM maken, naar een MOF-bestand te compileren en toepassen op het knooppunt.
In tegenstelling tot DSC-configuraties, doet u een configuratie LCM niet vast door het aanroepen van de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.
In plaats daarvan u aanroepen [Set DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx), levert het pad naar de configuratie van de LCM MOF als parameter.
Nadat u de configuratie van de LCM vast, ziet u de eigenschappen van de LCM door het aanroepen van de [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.

Een configuratie LCM kan blokken alleen voor een beperkt aantal resources bevatten.
In het vorige voorbeeld de enige resource aangeroepen is **instellingen**.
De beschikbare bronnen zijn:

* **ConfigurationRepositoryWeb**: Hiermee geeft u een HTTP-pull-service voor configuraties.
* **ConfigurationRepositoryShare**: Hiermee geeft u op een SMB-share voor configuraties.
* **ResourceRepositoryWeb**: Hiermee geeft u een HTTP-pull-service voor modules.
* **ResourceRepositoryShare**: Hiermee geeft u op een SMB-share voor modules.
* **ReportServerWeb**: Hiermee geeft u een HTTP-pull-service waarop rapporten worden verzonden.
* **PartialConfiguration**: biedt gegevens om in te schakelen gedeeltelijke configuraties.

## <a name="basic-settings"></a>Basisinstellingen

Dan geven pull-service-eindpunten/paden en gedeeltelijke configuraties, alle eigenschappen van de LCM zijn geconfigureerd in een **instellingen** blok.
De volgende eigenschappen beschikbaar zijn in een **instellingen** blok.

|  Eigenschap  |  Type  |  Beschrijving   |
|----------- |------- |--------------- |
| ActionAfterReboot| string| Hiermee geeft u op wat er gebeurt na opnieuw opstarten tijdens de toepassing van een configuratie. De mogelijke waarden zijn __'ContinueConfiguration'__ en __'StopConfiguration'__. <ul><li> __ContinueConfiguration__: blijven toepassen van de huidige configuratie nadat de computer opnieuw is opgestart. Dit is de standaardwaarde</li><li>__StopConfiguration__: stoppen van de huidige configuratie nadat de computer opnieuw is opgestart.</li></ul>|
| AllowModuleOverwrite| BOOL| __$TRUE__ nieuwe configuraties die zijn gedownload van de pull-service zijn niet toegestaan als de oude versie in het doelknooppunt te overschrijven. Anders wordt $FALSE.|
| CertificateID| string| De vingerafdruk van een certificaat gebruikt voor het beveiligen van referenties die zijn doorgegeven in een configuratie. Zie voor meer informatie [wilt beveiligen van referenties in Windows PowerShell Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)?. <br> __Opmerking:__ dit wordt automatisch beheerd als Azure Automation DSC-pull-service.|
| ConfigurationDownloadManagers| CimInstance[]| Verouderd. Gebruik __ConfigurationRepositoryWeb__ en __ConfigurationRepositoryShare__ blokken definiëren configuratie pull service-eindpunten.|
| ConfigurationID| string| Voor achterwaartse compatibiliteit met oudere pull versies service. Een GUID die identificeert het configuratiebestand van een pull-service ophalen. Het knooppunt wordt configuraties ophalen van de pull-service als de naam van de configuratie van de MOF ConfigurationID.mof heet.<br> __Opmerking:__ als u deze eigenschap instelt, registreren van het knooppunt met een pull-service met behulp van __RegistrationKey__ werkt niet. Zie voor meer informatie [instellen van een pull-client met configuratienamen](pullClientConfigNames.md).|
| ConfigurationMode| string | Hiermee geeft u op hoe de LCM daadwerkelijk geldt de configuratie voor de doelknooppunten. Mogelijke waarden zijn __'ApplyOnly'__,__'ApplyandMonitior'__, en __'ApplyandAutoCorrect'__. <ul><li>__ApplyOnly__: DSC geldt de configuratie en doet niets meer tenzij u een nieuwe configuratie wordt doorgeschoven, is naar het doelknooppunt of wanneer een nieuwe configuratie is opgehaald van een service. Na de eerste toepassing van een nieuwe configuratie controleert het DSC niet voor afwijking van een eerder geconfigureerde status. Houd er rekening mee dat DSC probeert toe te passen van de configuratie, totdat hij erin slaagt voordat __ApplyOnly__ wordt van kracht. </li><li> __ApplyAndMonitor__: dit is de standaardwaarde. De LCM geldt voor alle nieuwe configuraties. Als het doelknooppunt drifts van de gewenste status rapporteert DSC na de eerste toepassing van een nieuwe configuratie, de discrepantie in Logboeken. Houd er rekening mee dat DSC probeert toe te passen van de configuratie, totdat hij erin slaagt voordat __ApplyAndMonitor__ wordt van kracht.</li><li>__ApplyAndAutoCorrect__: DSC eventuele nieuwe configuraties van toepassing. Na de eerste toepassing van een nieuwe configuratie als het doelknooppunt drifts van de gewenste status DSC rapporteert het verschil in Logboeken en vervolgens wordt de huidige configuratie opnieuw toegepast.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Hoe vaak, in minuten, de huidige configuratie wordt gecontroleerd en toegepast. Deze eigenschap wordt genegeerd als de eigenschap ConfigurationMode is ingesteld op ApplyOnly. De standaardwaarde is 15.|
| DebugMode| string| Mogelijke waarden zijn __geen__, __ForceModuleImport__, en __alle__. <ul><li>Ingesteld op __geen__ bronnen in de cache te gebruiken. Dit is de standaardinstelling en moet worden gebruikt in scenario's voor productie.</li><li>Als u op __ForceModuleImport__, zorgt ervoor dat de LCM om opnieuw te laden geen DSC-resource-modules, zelfs als ze eerder zijn geladen en in de cache opgeslagen. Dit geldt voor de prestaties van DSC-bewerkingen, zoals elke module is geladen voor gebruik. Doorgaans gebruikt u deze waarde tijdens het opsporen van een resource</li><li>In deze release __alle__ is hetzelfde als __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| BOOL| Stel dit in op __$true__ automatisch het knooppunt opnieuw wordt opgestart na een configuratie waarbij opnieuw opstarten wordt toegepast. Anders moet u het knooppunt voor een configuratie die dit vereist is voor handmatig opnieuw opstarten. De standaardwaarde is __$false__. Voor het gebruik van deze instelling als u een voorwaarde opnieuw opstarten wordt gepubliceerd door iets anders dan DSC (zoals Windows Installer), combineert u deze instelling met de [xPendingReboot](https://github.com/powershell/xpendingreboot) module.|
| RefreshMode| string| Hiermee geeft u op hoe de LCM configuraties opgehaald. De mogelijke waarden zijn __"Uitgeschakeld"__, __'Push'__, en __'Pull'__. <ul><li>__Uitgeschakeld__: DSC-configuraties zijn uitgeschakeld voor dit knooppunt.</li><li> __Push__: configuraties worden geïnitieerd door het aanroepen van de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet. De configuratie wordt onmiddellijk toegepast op het knooppunt. Dit is de standaardwaarde.</li><li>__Pull:__ het knooppunt is geconfigureerd voor het regelmatig te controleren op configuraties van een pull-service of SMB-pad. Als deze eigenschap is ingesteld op __Pull__, moet u een HTTP (service) of SMB (share)-pad in een __ConfigurationRepositoryWeb__ of __ConfigurationRepositoryShare__ blok.</li></ul>|
| RefreshFrequencyMins| UInt32| Het tijdsinterval in minuten, waarmee de LCM een pull-service controleert om bijgewerkte configuraties. Deze waarde wordt genegeerd als de LCM niet is geconfigureerd in de pull-modus. De standaardwaarde is 30.|
| ReportManagers| CimInstance[]| Verouderd. Gebruik __ReportServerWeb__ blokken voor het definiëren van een eindpunt te verzenden gegevens naar een pull-service reporting.|
| ResourceModuleManagers| CimInstance[]| Verouderd. Gebruik __ResourceRepositoryWeb__ en __ResourceRepositoryShare__ blokken definiëren pull respectievelijk de service HTTP-eindpunten of SMB-paden.|
| PartialConfigurations| CimInstance| Niet geïmplementeerd. Niet gebruiken.|
| StatusRetentionTimeInDays | UInt32| Het aantal dagen dat de LCM de status van de huidige configuratie houdt.|

## <a name="pull-service"></a>Pull-service

DSC-instellingen kunnen een knooppunt kan worden beheerd door binnenhalen van configuraties en -modules en rapportagegegevens publiceren naar een externe locatie.
De huidige opties voor het pull-service zijn onder andere:

- Azure Automation gewenst State Configuration-service
- Een pull-service-exemplaar met Windows Server
- Een SMB-share (biedt geen ondersteuning voor het publiceren van rapportagegegevens)

LCM configuratie ondersteunt de volgende soorten pull-service-eindpunten definiëren:

- **Configuratieserver**: een opslagplaats voor DSC-configuraties. Configuratieservers definiëren met behulp van **ConfigurationRepositoryWeb** (voor het web gebaseerde servers) en **ConfigurationRepositoryShare** (voor SMB-servers) geblokkeerd.
- **Bronserver**: een opslagplaats voor DSC-resources, geleverd als PowerShell-modules. Bronservers definiëren met behulp van **ResourceRepositoryWeb** (voor het web gebaseerde servers) en **ResourceRepositoryShare** (voor SMB-servers) geblokkeerd.
- **Rapportserver**: een service die DSC rapportgegevens worden verzonden. Rapportservers definiëren met behulp van **ReportServerWeb** blokken. Een rapportserver moet een webservice.

**De aanbevolen oplossing**, en de optie met de meeste functies die beschikbaar is, is [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).

De Azure-service kunt knooppunten lokale in datacenters persoonlijke of openbare clouds, zoals Azure en AWS beheren.
Persoonlijke omgevingen waarin servers kunnen niet rechtstreeks verbinding met Internet maken, Beperk uitgaand verkeer naar de gepubliceerde Azure IP-bereik (Zie [Azure Datacenter IP-adresbereiken](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Functies van de online service die momenteel niet beschikbaar in de pull-service op Windows Server zijn:
- Alle gegevens worden versleuteld in rust en onderweg
- Clientcertificaten worden gemaakt en automatisch beheerd
- Geheimen opslaan voor het centraal beheren van [wachtwoorden/referenties](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), of [variabelen](https://docs.microsoft.com/en-us/azure/automation/automation-variables) zoals servernamen of verbindingsreeksen
- Centraal beheren knooppunt [LCM configuratie](metaConfig.md#basic-settings)
- Centraal toewijzen configuraties aan client-knooppunten
- Release-configuratie voor het testen alvorens productie gewijzigd in 'kokospalm groepen'
- Grafische rapportage
  - Details van de status op het niveau van de resource DSC van granulatie
  - Uitgebreide foutberichten van clientcomputers voor probleemoplossing
- [Integratie met Azure-logboekanalyse](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) voor waarschuwingen, geautomatiseerde taken Android/iOS-app voor rapportage en waarschuwingen

U kunt ook, voor informatie over het instellen en gebruiken van pull-HTTP-service op Windows Server, Zie [een DSC-pull-server instellen](pullServer.md).
Neem in kennis gesteld dat het een beperkte implementatie met alleen eenvoudige mogelijkheden van configuraties/modules opslaan en vastleggen van gegevens in een lokale database is.

## <a name="configuration-server-blocks"></a>Configuratie server blokkeert

Als u een web gebaseerde configuratieserver definieert, maakt u een **ConfigurationRepositoryWeb** blok.
Een **ConfigurationRepositoryWeb** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|AllowUnsecureConnection|BOOL|Ingesteld op **$TRUE** om verbindingen vanuit het knooppunt zonder verificatie naar de server te staan. Ingesteld op **$FALSE** om verificatie te vereisen.|
|CertificateID|string|De vingerafdruk van een certificaat dat wordt gebruikt om de server te verifiëren.|
|ConfigurationNames|String]|Een matrix met namen van configuraties om te worden opgehaald door het doelknooppunt. Deze worden alleen gebruikt als het knooppunt is geregistreerd bij de pull-service met behulp van een **RegistrationKey**. Zie voor meer informatie [instellen van een pull-client met configuratienamen](pullClientConfigNames.md).|
|RegistrationKey|string|Een GUID die het knooppunt bij de pull-service registreert. Zie voor meer informatie [instellen van een pull-client met configuratienamen](pullClientConfigNames.md).|
|ServerURL|string|De URL van de configuration-service.|

Zie voor een voorbeeldscript voor het vereenvoudigen van de waarde ConfigurationRepositoryWeb configureren voor de lokale knooppunten - [metaconfigurations DSC genereren](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Als u wilt definiëren een configuratie op basis van een SMB-server, die u maakt een **ConfigurationRepositoryShare** blok.
Een **ConfigurationRepositoryShare** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|referentie|MSFT_Credential|De referentie die wordt gebruikt om de SMB-share te verifiëren.|
|SourcePath|string|Het pad van de SMB-share.|

## <a name="resource-server-blocks"></a>Resource-server blokkeert

Als u een web gebaseerde bronserver definieert, maakt u een **ResourceRepositoryWeb** blok.
Een **ResourceRepositoryWeb** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|AllowUnsecureConnection|BOOL|Ingesteld op **$TRUE** om verbindingen vanuit het knooppunt zonder verificatie naar de server te staan. Ingesteld op **$FALSE** om verificatie te vereisen.|
|CertificateID|string|De vingerafdruk van een certificaat dat wordt gebruikt om de server te verifiëren.|
|RegistrationKey|string|Een GUID die het knooppunt met de pull-service identificeert.|
|ServerURL|string|De URL van de configuratieserver.|

Zie voor een voorbeeldscript voor het vereenvoudigen van de waarde ResourceRepositoryWeb configureren voor de lokale knooppunten - [metaconfigurations DSC genereren](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Als u wilt definiëren een resource op basis van een SMB-server, die u maakt een **ResourceRepositoryShare** blok.
**ResourceRepositoryShare** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|referentie|MSFT_Credential|De referentie die wordt gebruikt om de SMB-share te verifiëren. Zie voor een voorbeeld van de doorgegeven referenties [een SMB DSC-pull-server instellen](pullServerSMB.md)|
|SourcePath|string|Het pad van de SMB-share.|

## <a name="report-server-blocks"></a>Rapport server blokkeert

Als u wilt definiëren een rapportserver, maakt u een **ReportServerWeb** blok.
De report server-rol is niet compatibel met SMB op basis van pull-service.
**ReportServerWeb** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|AllowUnsecureConnection|BOOL|Ingesteld op **$TRUE** om verbindingen vanuit het knooppunt zonder verificatie naar de server te staan. Ingesteld op **$FALSE** om verificatie te vereisen.|
|CertificateID|string|De vingerafdruk van een certificaat dat wordt gebruikt om de server te verifiëren.|
|RegistrationKey|string|Een GUID die het knooppunt met de pull-service identificeert.|
|ServerURL|string|De URL van de configuratieserver.|

Zie voor een voorbeeldscript voor het vereenvoudigen van de waarde ReportServerWeb configureren voor de lokale knooppunten - [metaconfigurations DSC genereren](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Gedeeltelijke configuraties

Als u een gedeeltelijke configuratie definieert, maakt u een **PartialConfiguration** blok.
Zie voor meer informatie over gedeeltelijke configuraties [gedeeltelijk DSC-configuraties](partialConfigs.md).
**PartialConfiguration** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|ConfigurationSource|String]|Een matrix met namen van de van configuratieservers, eerder is gedefinieerd in **ConfigurationRepositoryWeb** en **ConfigurationRepositoryShare** blokken, waarbij de gedeeltelijke configuratie opgehaald uit.|
|dependsOn|tekenreeks {}|Een lijst met namen van andere configuraties die moeten worden voltooid voordat deze gedeeltelijke configuratie wordt toegepast.|
|Beschrijving|string|De tekst die wordt gebruikt om de configuratie van de gedeeltelijke te beschrijven.|
|ExclusiveResources|String]|Een matrix van resources is uitsluitend van toepassing op deze gedeeltelijke configuratie.|
|RefreshMode|string|Hiermee geeft u op hoe de LCM deze gedeeltelijke configuratie opgehaald. De mogelijke waarden zijn __"Uitgeschakeld"__, __'Push'__, en __'Pull'__. <ul><li>__Uitgeschakeld__: deze gedeeltelijke configuratie is uitgeschakeld.</li><li> __Push__: de configuratie van de gedeeltelijk wordt doorgeschoven, is naar het knooppunt door het aanroepen van de [publiceren DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx) cmdlet. Nadat alle gedeeltelijke configuraties voor het knooppunt worden gepusht of opgehaald uit een service, de configuratie kan worden gestart door het aanroepen van `Start-DscConfiguration –UseExisting`. Dit is de standaardwaarde.</li><li>__Pull:__ het knooppunt regelmatig om te controleren of gedeeltelijke configuratie van een pull-service is geconfigureerd. Als deze eigenschap is ingesteld op __Pull__, moet u een pull-service in een __ConfigurationSource__ eigenschap. Zie voor meer informatie over Azure Automation pull-service, [overzicht van Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|String]|Een matrix met de namen van servers resource waarvan voor het downloaden van de vereiste resources voor deze gedeeltelijke configuratie. Deze namen moeten verwijzen naar service-eindpunten die eerder is gedefinieerd in **ResourceRepositoryWeb** en **ResourceRepositoryShare** blokken.|

__Opmerking:__ gedeeltelijke configuraties worden ondersteund met Azure Automation DSC, maar slechts één configuratie bij elk automation-account per knooppunt kan worden opgevraagd.

## <a name="see-also"></a>Zie ook

### <a name="concepts"></a>Concepten
[Desired State Configuration-overzicht](overview.md)

[Aan de slag met Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Andere bronnen

[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)

[Een pull-client met de configuratienamen instellen](pullClientConfigNames.md)
