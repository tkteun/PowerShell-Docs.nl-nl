---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: De Local Configuration Manager configureren
ms.openlocfilehash: c3ced2376c7d99477c40ae078dcecd775538b350
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404005"
---
# <a name="configuring-the-local-configuration-manager"></a>De Local Configuration Manager configureren

> Van toepassing op: Windows PowerShell 5.0

De lokale Configuration Manager (LCM) is de engine van Desired State Configuration (DSC).
De LCM wordt uitgevoerd op elk doelknooppunt, en is verantwoordelijk voor het parseren en configuraties die worden verzonden naar het knooppunt doorvoeren.
Het is ook verantwoordelijk voor een aantal andere aspecten van DSC, met inbegrip van de volgende.

- Bepalen van vernieuwingsmodus (push of pull).
- Hoe vaak een knooppunt wordt opgehaald en enacts configuraties op te geven.
- Het knooppunt koppelen met pull-service.
- Gedeeltelijke configuraties opgeven.

Een speciaal soort configuratie kunt u de LCM om op te geven van elk van deze problemen te configureren.
De volgende secties wordt beschreven hoe u de LCM configureren.

Nieuwe instellingen van Windows PowerShell 5.0 geïntroduceerd voor het beheren van de lokale Configuration Manager.
Zie voor meer informatie over de LCM configureren in Windows PowerShell 4.0 [de Local Configuration Manager configureren in eerdere versies van Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Schrijven en het doorvoeren van de configuratie van een LCM

Als u wilt de LCM configureren, moet u maken en uitvoeren van een speciaal soort configuratie die LCM instellingen toegepast.
Als u een LCM-configuratie, moet u het kenmerk DscLocalConfigurationManager gebruiken.
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
U wordt een LCM-configuratie maken, deze worden gecompileerd naar een MOF-bestand en pas deze toe op het knooppunt.
In tegenstelling tot DSC-configuraties, doet u een configuratie LCM niet gerapporteerd door het aanroepen van de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.
In plaats daarvan u aanroepen [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager), waarbij u het pad naar de configuratie van de LCM MOF als een parameter opgeeft.
Nadat u de configuratie van de LCM gerapporteerd, kunt u de eigenschappen van de LCM zien door het aanroepen van de [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.

De configuratie van een LCM kan blokken alleen voor een beperkt aantal resources bevatten.
In het vorige voorbeeld is het de enige bron met de naam **instellingen**.
De beschikbare resources zijn:

* **ConfigurationRepositoryWeb**: Hiermee geeft u een HTTP-pull-service voor configuraties.
* **ConfigurationRepositoryShare**: Hiermee geeft u een SMB-share voor de configuraties.
* **ResourceRepositoryWeb**: Hiermee geeft u een HTTP-pull-service voor modules.
* **ResourceRepositoryShare**: Hiermee geeft u een SMB-share voor modules.
* **ReportServerWeb**: Hiermee geeft u een HTTP-pull-service waarop rapporten worden verzonden.
* **PartialConfiguration**: levert gegevens om in te schakelen gedeeltelijke configuraties.

## <a name="basic-settings"></a>Basisinstellingen

Dan het pull-service-eindpunten/paden en gedeeltelijke configuraties op te geven, alle van de eigenschappen van de LCM zijn geconfigureerd in een **instellingen** blokkeren.
De volgende eigenschappen zijn beschikbaar in een **instellingen** blokkeren.

|  Eigenschap  |  Type  |  Beschrijving   |
|----------- |------- |--------------- |
| ActionAfterReboot| string| Hiermee geeft u op wat gebeurt er na een opnieuw opstarten tijdens de toepassing van een configuratie. De mogelijke waarden zijn __"ContinueConfiguration"__ en __"De StopConfiguration"__. <ul><li> __ContinueConfiguration__: Doorgaan met het toepassen van de huidige configuratie na de computer opnieuw is opgestart. Dit is de standaardwaarde</li><li>__De StopConfiguration__: De huidige configuratie na opnieuw opstarten van machine stoppen.</li></ul>|
| AllowModuleOverwrite| BOOL| __$TRUE__ als nieuwe configuraties die zijn gedownload van de pull-service zijn toegestaan voor de oude overschrijven op het doelknooppunt. Anders wordt $FALSE.|
| CertificateID| string| De vingerafdruk van een certificaat dat wordt gebruikt voor het beveiligen van referenties die zijn doorgegeven in een configuratie. Zie voor meer informatie [wilt voor het beveiligen van referenties in Windows PowerShell Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)?. <br> __Opmerking:__ dit automatisch als met behulp van Azure Automation DSC pull-service wordt beheerd.|
| ConfigurationDownloadManagers| CimInstance]| Verouderd. Gebruik __ConfigurationRepositoryWeb__ en __ConfigurationRepositoryShare__ blokken voor het definiëren van configuratie pull service-eindpunten.|
| ConfigurationID| string| Voor achterwaartse compatibiliteit met oudere pull versies service. Een GUID die het configuratiebestand ophalen uit een pull-service identificeert. Het knooppunt wordt configuraties opgehaald van de pull-service als de naam van de configuratie van de MOF ConfigurationID.mof heet.<br> __Opmerking:__ Als u deze eigenschap is ingesteld, registreert u het knooppunt met een pull-service met behulp van __RegistrationKey__ werkt niet. Zie voor meer informatie, [instellen van een pull-client met configuratienamen](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| string | Hiermee geeft u op hoe de LCM daadwerkelijk geldt de configuratie voor de doelknooppunten. Mogelijke waarden zijn __"ApplyOnly"__,__"ApplyAndMonitor"__, en __"ApplyAndAutoCorrect"__. <ul><li>__ApplyOnly__: DSC geldt de configuratie en doet niets meer, tenzij er een nieuwe configuratie wordt doorgestuurd naar het doelknooppunt of wanneer een nieuwe configuratie wordt opgehaald uit een service. Na de eerste toepassing van een nieuwe configuratie DSC controleert niet op afwijking van een eerder geconfigureerde status. Houd er rekening mee dat de DSC proberen zal om toe te passen van de configuratie totdat hij erin slaagt voordat __ApplyOnly__ wordt van kracht. </li><li> __ApplyAndMonitor__: Dit is de standaardwaarde. De LCM geldt voor alle nieuwe configuraties. Als het doelknooppunt drifts van de gewenste status, rapporteert DSC na de eerste toepassing van een nieuwe configuratie, het verschil in Logboeken. Houd er rekening mee dat de DSC proberen zal om toe te passen van de configuratie totdat hij erin slaagt voordat __ApplyAndMonitor__ wordt van kracht.</li><li>__ApplyAndAutoCorrect__: DSC geldt voor alle nieuwe configuraties. Na de eerste toepassing van een nieuwe configuratie als het doelknooppunt drifts van de gewenste status, DSC rapporteert het verschil in Logboeken en de huidige configuratie vervolgens opnieuw toegepast.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Hoe vaak in minuten, de huidige configuratie is dit selectievakje is ingeschakeld en toegepast. Deze eigenschap wordt genegeerd als de eigenschap ConfigurationMode is ingesteld op ApplyOnly. De standaardwaarde is 15.|
| Fouten opsporen-modus| string| Mogelijke waarden zijn __geen__, __ForceModuleImport__, en __alle__. <ul><li>Ingesteld op __geen__ gebruik van resources in de cache. Dit is de standaardinstelling en moet worden gebruikt in productiescenario's.</li><li>Als u op __ForceModuleImport__, zorgt ervoor dat de LCM om opnieuw te laden van alle modules DSC-resource, zelfs als ze eerder zijn geladen en opgeslagen in de cache. Dit van invloed op de prestaties van DSC-bewerkingen zoals elke module opnieuw is geladen voor gebruik. Doorgaans gebruikt u deze waarde tijdens het opsporen van fouten in een resource</li><li>In deze release __alle__ is hetzelfde als __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| BOOL| Stel dit in op __$true__ automatisch het knooppunt opnieuw wordt opgestart na een configuratie waarvoor opnieuw opstarten wordt toegepast. Anders moet u handmatig het knooppunt voor de configuratie die vereist dat het opnieuw opstarten. De standaardwaarde is __$false__. Voor het gebruik van deze instelling als de voorwaarde van een opnieuw opstarten wordt gepubliceerd door iets anders dan DSC (zoals Windows-installatieprogramma), combineert u deze instelling met de [xPendingReboot](https://github.com/powershell/xpendingreboot) module.|
| RefreshMode| string| Hiermee geeft u op hoe de LCM configuraties opgehaald. De mogelijke waarden zijn __"Uitgeschakeld"__, __'Push'__, en __'Pull'__. <ul><li>__Uitgeschakelde__: DSC-configuraties zijn uitgeschakeld voor dit knooppunt.</li><li> __Push-__: Configuraties zijn gestart door het aanroepen van de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. De configuratie wordt direct toegepast op het knooppunt. Dit is de standaardwaarde.</li><li>__Haal:__ Het knooppunt is geconfigureerd om te controleren op regelmatig configuraties van een pull-service of een SMB-pad. Als deze eigenschap is ingesteld op __Pull__, moet u een HTTP-(service) of SMB (delen)-pad in een __ConfigurationRepositoryWeb__ of __ConfigurationRepositoryShare__ blokkeren.</li></ul>|
| RefreshFrequencyMins| Uint32| Het tijdsinterval in minuten, waarmee de LCM controleert of een pull-service om op te halen van bijgewerkte configuraties. Deze waarde wordt genegeerd als de LCM niet is geconfigureerd in de pull-modus. De standaardwaarde is 30.|
| ReportManagers| CimInstance]| Verouderd. Gebruik __ReportServerWeb__ blokken voor het definiëren van een eindpunt voor het verzenden van gegevens naar een pull-service reporting.|
| ResourceModuleManagers| CimInstance]| Verouderd. Gebruik __ResourceRepositoryWeb__ en __ResourceRepositoryShare__ blokken voor het definiëren van pull-service HTTP-eindpunten of SMB-paden, respectievelijk.|
| PartialConfigurations| CimInstance| Niet geïmplementeerd. Niet gebruiken.|
| StatusRetentionTimeInDays | UInt32| Het aantal dagen dat de LCM de status van de huidige configuratie houdt.|

## <a name="pull-service"></a>Pull-service

LCM configuratie biedt ondersteuning voor het definiëren van de volgende typen pull-service-eindpunten:

- **Configuratieserver**: Een opslagplaats voor DSC-configuraties. Configuratieservers definiëren met behulp van **ConfigurationRepositoryWeb** (voor het web gebaseerde servers) en **ConfigurationRepositoryShare** (voor SMB-servers) geblokkeerd.
- **Resource-server**: Een opslagplaats voor DSC-resources worden geleverd als PowerShell-modules. Resource-servers definiëren met behulp van **ResourceRepositoryWeb** (voor het web gebaseerde servers) en **ResourceRepositoryShare** (voor SMB-servers) geblokkeerd.
- **Rapportserver**: Een service die DSC rapportgegevens worden verzonden. Rapportservers definiëren met behulp van **ReportServerWeb** blokken. Een rapportserver moet een webservice.

Voor meer informatie over pull-service ziet, [Pull-Service Desired State Configuration](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Configuratie van server-blokken

Voor het definiëren van een web gebaseerde configuratieserver die u maakt een **ConfigurationRepositoryWeb** blokkeren.
Een **ConfigurationRepositoryWeb** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|AllowUnsecureConnection|BOOL|Ingesteld op **$TRUE** om verbindingen vanuit het knooppunt zonder verificatie naar de server te staan. Ingesteld op **$FALSE** om verificatie te vereisen.|
|CertificateID|string|De vingerafdruk van een certificaat dat wordt gebruikt om de server te verifiëren.|
|ConfigurationNames|String]|Een matrix met namen van configuraties om te worden opgehaald door het doelknooppunt. Deze worden alleen gebruikt als het knooppunt is geregistreerd bij de pull-service met behulp van een **RegistrationKey**. Zie voor meer informatie, [instellen van een pull-client met configuratienamen](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|string|Een GUID waarmee het knooppunt met de pull-service wordt geregistreerd. Zie voor meer informatie, [instellen van een pull-client met configuratienamen](../pull-server/pullClientConfigNames.md).|
|ServerURL|string|De URL van de configuration-service.|

Zie voor een voorbeeldscript voor het vereenvoudigen van de waarde ConfigurationRepositoryWeb configureren voor on-premises knooppunten zijn beschikbaar: [metaconfigurations DSC genereren](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Voor het definiëren van een configuratie op basis van SMB-server die u maakt een **ConfigurationRepositoryShare** blokkeren.
Een **ConfigurationRepositoryShare** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|Referentie|MSFT_Credential|De referentie die wordt gebruikt om de SMB-share te verifiëren.|
|Bronpad|string|Het pad van de SMB-share.|

## <a name="resource-server-blocks"></a>Resource-server blokkeert

Voor het definiëren van een resource op het web server, die u maakt een **ResourceRepositoryWeb** blokkeren.
Een **ResourceRepositoryWeb** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|AllowUnsecureConnection|BOOL|Ingesteld op **$TRUE** om verbindingen vanuit het knooppunt zonder verificatie naar de server te staan. Ingesteld op **$FALSE** om verificatie te vereisen.|
|CertificateID|string|De vingerafdruk van een certificaat dat wordt gebruikt om de server te verifiëren.|
|RegistrationKey|string|Een GUID waarmee het knooppunt naar de pull-service.|
|ServerURL|string|De URL van de configuratieserver.|

Zie voor een voorbeeldscript voor het vereenvoudigen van de waarde ResourceRepositoryWeb configureren voor on-premises knooppunten zijn beschikbaar: [metaconfigurations DSC genereren](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Voor het definiëren van een resource op basis van SMB-server die u maakt een **ResourceRepositoryShare** blokkeren.
**ResourceRepositoryShare** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|Referentie|MSFT_Credential|De referentie die wordt gebruikt om de SMB-share te verifiëren. Zie voor een voorbeeld van het doorgeven van referenties, [instellen van een DSC SMB-pull-server](../pull-server/pullServerSMB.md)|
|Bronpad|string|Het pad van de SMB-share.|

## <a name="report-server-blocks"></a>Rapport server blokken

Voor het definiëren van een rapportserver die u maakt een **ReportServerWeb** blokkeren.
De report server-rol is niet compatibel met SMB op basis van pull-service.
**ReportServerWeb** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|AllowUnsecureConnection|BOOL|Ingesteld op **$TRUE** om verbindingen vanuit het knooppunt zonder verificatie naar de server te staan. Ingesteld op **$FALSE** om verificatie te vereisen.|
|CertificateID|string|De vingerafdruk van een certificaat dat wordt gebruikt om de server te verifiëren.|
|RegistrationKey|string|Een GUID waarmee het knooppunt naar de pull-service.|
|ServerURL|string|De URL van de configuratieserver.|

Zie voor een voorbeeldscript voor het vereenvoudigen van de waarde ReportServerWeb configureren voor on-premises knooppunten zijn beschikbaar: [metaconfigurations DSC genereren](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Gedeeltelijke configuraties

Voor het definiëren van een gedeeltelijke configuratie die u maakt een **PartialConfiguration** blokkeren.
Zie voor meer informatie over gedeeltelijke configuraties [gedeeltelijk DSC-configuraties](../pull-server/partialConfigs.md).
**PartialConfiguration** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|ConfigurationSource|String]|Een matrix van namen van de van configuratieservers, dat is gedefinieerd in **ConfigurationRepositoryWeb** en **ConfigurationRepositoryShare** blokken, waarbij de gedeeltelijke configuratie wordt opgehaald uit.|
|DependsOn|Tekenreeks{}|Een lijst met namen van andere configuraties die moeten worden uitgevoerd voordat deze gedeeltelijke configuratie is toegepast.|
|Beschrijving|string|Tekst die wordt gebruikt om te beschrijven de gedeeltelijke configuratie.|
|ExclusiveResources|String]|Een matrix van resources die exclusief zijn voor deze gedeeltelijke configuratie.|
|RefreshMode|string|Hiermee geeft u op hoe deze gedeeltelijke configuratie in de LCM worden opgehaald. De mogelijke waarden zijn __"Uitgeschakeld"__, __'Push'__, en __'Pull'__. <ul><li>__Uitgeschakelde__: Deze gedeeltelijke configuratie is uitgeschakeld.</li><li> __Push-__: De configuratie van de gedeeltelijke wordt doorgestuurd naar het knooppunt door het aanroepen van de [publiceren-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet. Nadat alle gedeeltelijke configuraties voor het knooppunt worden gepusht of opgehaald uit een service, de configuratie kan worden gestart door het aanroepen van `Start-DscConfiguration –UseExisting`. Dit is de standaardwaarde.</li><li>__Haal:__ Het knooppunt is geconfigureerd om te controleren regelmatig of er een gedeeltelijke configuratie van een pull-service. Als deze eigenschap is ingesteld op __Pull__, moet u een pull-service in een __ConfigurationSource__ eigenschap. Zie voor meer informatie over pull-service voor Azure Automation, [overzicht van Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|String]|Een matrix met de namen van resource-servers van waaruit vereiste resources voor deze gedeeltelijke configuratie gedownload. Deze namen moeten verwijzen naar de service-eindpunten die eerder is gedefinieerd in **ResourceRepositoryWeb** en **ResourceRepositoryShare** blokken.|

__Opmerking:__ gedeeltelijke configuraties worden ondersteund door Azure Automation DSC, maar slechts één configuratie kan worden opgehaald uit elk automation-account per knooppunt.

## <a name="see-also"></a>Zie ook

### <a name="concepts"></a>Concepten
[Overzicht Desired State Configuration](../overview/overview.md)

[Aan de slag met Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Andere bronnen

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Instellen van een pull-client met configuratienamen](../pull-server/pullClientConfigNames.md)
