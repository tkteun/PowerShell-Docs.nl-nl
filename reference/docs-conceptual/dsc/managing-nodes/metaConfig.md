---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: De lokale Configuration Manager configureren
ms.openlocfilehash: c736f1c6a7cd6740f9d777dd68559f29909bc5b6
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691988"
---
# <a name="configuring-the-local-configuration-manager"></a>De lokale Configuration Manager configureren

> Van toepassing op: Windows Power shell 5,0

De lokale Configuration Manager (LCM) is de engine van desired state Configuration (DSC).
De LCM wordt uitgevoerd op elk doel knooppunt en is verantwoordelijk voor het parseren en door voeren van configuraties die naar het knoop punt worden verzonden.
Het is ook verantwoordelijk voor een aantal andere aspecten van DSC, waaronder de volgende.

- Vernieuwings modus bepalen (push of pull).
- Opgeven hoe vaak een knoop punt configuraties ophaalt en overgeeft.
- Het knoop punt koppelen aan de pull-service.
- Gedeeltelijke configuraties opgeven.

U gebruikt een speciaal type configuratie om de LCM te configureren om elk van deze gedragingen op te geven.
In de volgende secties wordt beschreven hoe u de LCM kunt configureren.

Windows Power shell 5,0 heeft nieuwe instellingen geïntroduceerd voor het beheren van lokale Configuration Manager.
Zie [Configuring the Local configuration manager in eerdere versies van Windows Power shell](metaconfig4.md)(Engelstalig) voor meer informatie over het configureren van de LCM in Windows power Shell 4,0.

## <a name="writing-and-enacting-an-lcm-configuration"></a>Een configuratie van een LCM schrijven en opstellen

Als u de LCM wilt configureren, maakt en voert u een speciaal type configuratie uit waarmee de instellingen van de LCM worden toegepast.
Als u een configuratie van een LCM wilt opgeven, gebruikt u het kenmerk DscLocalConfigurationManager.
Hieronder ziet u een eenvoudige configuratie waarmee de LCM wordt ingesteld op push-modus.

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

Het proces voor het Toep assen van instellingen op LCM is vergelijkbaar met het Toep assen van een DSC-configuratie.
U maakt een configuratie van de LCM, compileert deze in een MOF-bestand en past deze toe op het knoop punt.
In tegens telling tot DSC-configuraties is het niet mogelijk een configuratie van de LCM te maken door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen.
In plaats daarvan roept u [set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)aan, waarbij u het pad naar de ICM-configuratie-MOF opgeeft als een para meter.
Nadat u de configuratie van de LCM hebt aangenomen, kunt u de eigenschappen van de LCM zien door de cmdlet [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) aan te roepen.

Een configuratie van de LCM kan alleen blokken bevatten voor een beperkt aantal resources.
In het vorige voor beeld is de enige resource met de naam **instellingen**.
De andere beschik bare bronnen zijn:

* **ConfigurationRepositoryWeb**: Hiermee geeft u een HTTP pull-service voor configuraties.
* **ConfigurationRepositoryShare**: Hiermee geeft u een SMB-share op voor configuraties.
* **ResourceRepositoryWeb**: Hiermee geeft u een http-pull-service voor modules op.
* **ResourceRepositoryShare**: Hiermee geeft u een SMB-share voor modules op.
* **ReportServerWeb**: Hiermee geeft u een http-pull-service aan waarnaar rapporten worden verzonden.
* **PartialConfiguration**: biedt gegevens om gedeeltelijke configuraties mogelijk te maken.

## <a name="basic-settings"></a>Basisinstellingen

Behalve dat pull-service-eind punten/-paden en gedeeltelijke configuraties worden opgegeven, worden alle eigenschappen van de LCM geconfigureerd in een **instellingen** blok.
De volgende eigenschappen zijn beschikbaar in een **instellingen** blok.

|  Eigenschap  |  Type  |  Beschrijving   |
|----------- |------- |--------------- |
| ActionAfterReboot| tekenreeks| Hiermee geeft u op wat er gebeurt nadat de computer opnieuw is opgestart tijdens de toepassing van een configuratie. De mogelijke waarden zijn __' ContinueConfiguration '__ en __' de stopconfiguration '__. <ul><li> __ContinueConfiguration__: pas de huidige configuratie toe nadat de computer opnieuw is opgestart. Dit is de standaard waarde</li><li>__De stopconfiguration__: de huidige configuratie stoppen nadat de computer opnieuw is opgestart.</li></ul>|
| AllowModuleOverwrite| booleaans| __$True__ als nieuwe configuraties die worden gedownload van de pull-service, de oude kunnen overschrijven op het doel knooppunt. Anders $FALSE.|
| CertificateID| tekenreeks| De vinger afdruk van een certificaat dat wordt gebruikt voor het beveiligen van referenties die in een configuratie zijn door gegeven. Zie voor meer informatie [referenties beveiligen in Windows Power shell desired state Configuration](https://devblogs.microsoft.com/powershell/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/)(Engelstalig). <br> __Opmerking:__ dit wordt automatisch beheerd als Azure Automation DSC-pull-service wordt gebruikt.|
| ConfigurationDownloadManagers| CimInstance []| Verouderd. Gebruik __ConfigurationRepositoryWeb__ -en __ConfigurationRepositoryShare__ -blokken om configuratie-pull service-eind punten te definiëren.|
| ConfigurationID| tekenreeks| Voor achterwaartse compatibiliteit met oudere pull-service versies. Een GUID die het configuratie bestand identificeert dat van een pull-service moet worden opgehaald. Het knoop punt haalt configuraties op voor de pull-service als de naam van de configuratie-MOF ConfigurationID. MOF is.<br> __Opmerking:__ Als u deze eigenschap instelt, werkt u het knoop punt met een pull-service te registreren met behulp van __RegistrationKey__ . Zie [een pull-client met configuratie namen instellen](../pull-server/pullClientConfigNames.md)voor meer informatie.|
| ConfigurationMode| tekenreeks | Hiermee geeft u op hoe de LCM de configuratie daad werkelijk toepast op de doel knooppunten. Mogelijke waarden zijn __"ApplyOnly"__,__"ApplyAndMonitor"__ en __"ApplyAndAutoCorrect"__. <ul><li>__ApplyOnly__: DSC past de configuratie toe en doet niets verder tenzij een nieuwe configuratie wordt gepusht naar het doel knooppunt of wanneer een nieuwe configuratie wordt opgehaald uit een service. Na de eerste toepassing van een nieuwe configuratie controleert DSC niet op een eerder geconfigureerde status. U ziet dat DSC probeert de configuratie toe te passen totdat deze is voltooid voordat __ApplyOnly__ van kracht worden. </li><li> __ApplyAndMonitor__: dit is de standaard waarde. De LCM past nieuwe configuraties toe. Als er na de eerste toepassing van een nieuwe configuratie het doel knooppunt van de gewenste status is, wordt de discrepantie in de logboeken door DSC gerapporteerd. U ziet dat DSC probeert de configuratie toe te passen totdat deze is voltooid voordat __ApplyAndMonitor__ van kracht worden.</li><li>__ApplyAndAutoCorrect__: DSC past nieuwe configuraties toe. Als er na de eerste toepassing van een nieuwe configuratie het doel knooppunt van de gewenste status is, wordt de discrepantie in de logboeken door DSC gerapporteerd en wordt de huidige configuratie opnieuw toegepast.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Hoe vaak, in minuten, de huidige configuratie wordt gecontroleerd en toegepast. Deze eigenschap wordt genegeerd als de eigenschap ConfigurationMode is ingesteld op ApplyOnly. De standaard waarde is 15.|
| DebugMode| tekenreeks| Mogelijke waarden zijn __none__, __ForceModuleImport__en __all__. <ul><li>Stel deze waarde in op __geen__ om in cache opgeslagen resources te gebruiken. Dit is de standaard instelling en moet worden gebruikt in productie scenario's.</li><li>Als __ForceModuleImport__wordt ingesteld, laadt de LCM alle DSC-resource modules opnieuw, zelfs als ze eerder zijn geladen en in de cache zijn opgeslagen. Dit heeft gevolgen voor de prestaties van DSC-bewerkingen, omdat elke module opnieuw wordt geladen voor gebruik. Normaal gesp roken gebruikt u deze waarde bij het opsporen van fouten in een resource</li><li>In deze release is __alle__ hetzelfde als __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| booleaans| Stel dit in op `$true` om resources toe te staan om het knoop punt opnieuw op te starten met de `$global:DSCMachineStatus` vlag. Als dat niet het geval is, moet u het knoop punt hand matig opnieuw opstarten voor een configuratie waarvoor deze vereist is. De standaardwaarde is `$false`. Als u deze instelling wilt gebruiken wanneer een voor waarde voor opnieuw opstarten wordt ingesteld door iets anders dan DSC (zoals Windows Installer), moet u deze instelling combi neren met de __PendingReboot__ -resource in de [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) -module.|
| RefreshMode| tekenreeks| Hiermee geeft u op hoe de LCM configuraties krijgt. De mogelijke waarden zijn __' disabled '__, __' push '__ en __' pull '__. <ul><li>__Uitgeschakeld__: DSC-configuraties zijn uitgeschakeld voor dit knoop punt.</li><li> __Push__: configuraties worden geïnitieerd door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen. De configuratie wordt direct toegepast op het knoop punt. Dit is de standaardwaarde.</li><li>__Pull:__ Het knoop punt is geconfigureerd om regel matig te controleren op configuraties van een pull-service of SMB-pad. Als deze eigenschap is ingesteld op __pull__, moet u een http-(Service) of SMB (share)-pad opgeven in een __ConfigurationRepositoryWeb__ -of __ConfigurationRepositoryShare__ -blok.</li></ul>|
| RefreshFrequencyMins| Uint32| Het tijds interval, in minuten, waarna de LCM een pull-service controleert om bijgewerkte configuraties te verkrijgen. Deze waarde wordt genegeerd als de LCM niet is geconfigureerd in de pull-modus. De standaardwaarde is 30.|
| ReportManagers| CimInstance []| Verouderd. Gebruik __ReportServerWeb__ -blokken om een eind punt te definiëren voor het verzenden van rapportage gegevens naar een pull-service.|
| ResourceModuleManagers| CimInstance []| Verouderd. Gebruik __ResourceRepositoryWeb__ -en __ResourceRepositoryShare__ -blokken om respectievelijk pull service http-eind punten of SMB-paden te definiëren.|
| PartialConfigurations| CimInstance| Niet geïmplementeerd. Niet gebruiken.|
| StatusRetentionTimeInDays | UInt32| Het aantal dagen dat de LCM de status van de huidige configuratie behoudt.|

> [!NOTE]
> De LCM start de **ConfigurationModeFrequencyMins** -cyclus op basis van:
>
> - Er wordt een nieuwe-configuratie toegepast met behulp van`Set-DscLocalConfigurationManager`
> - Een computer opnieuw opstarten
>
> Voor elke voor waarde waarbij het timer proces vastloopt, wordt dit binnen 30 seconden gedetecteerd en wordt de cyclus opnieuw gestart.
> Een gelijktijdige bewerking kan ertoe leiden dat de cyclus wordt gestart. als de duur van deze bewerking de geconfigureerde cyclus frequentie overschrijdt, wordt de volgende timer niet gestart.
>
> Voor beeld: de configuratie van de instellingen van een pull-interval van vijf tien minuten en een pull vindt plaats in T1.  Het knoop punt is 16 minuten niet voltooid.  De eerste vijf tien minuten wordt genegeerd en de volgende pull-bewerking wordt uitgevoerd op T1 + 15 + 15.

## <a name="pull-service"></a>Pull-service

De configuratie van de LCM ondersteunt het definiëren van de volgende typen pull-service-eind punten:

- **Configuratie server**: een opslag plaats voor DSC-configuraties. Definieer configuratie servers met behulp van **ConfigurationRepositoryWeb** (voor webservers) en **ConfigurationRepositoryShare** (voor op SMB gebaseerde servers) blokken.
- **Resource server**: een opslag plaats voor DSC-resources, verpakt als Power shell-modules. Definieer resource servers met behulp van **ResourceRepositoryWeb** (voor webservers) en **ResourceRepositoryShare** (voor op SMB gebaseerde servers) blokken.
- **Rapport server**: een service waarnaar DSC rapport gegevens worden verzonden. Definieer rapport servers met behulp van **ReportServerWeb** -blokken. Een rapport server moet een webservice zijn.

Zie [desired state Configuration pull service](../pull-server/pullServer.md)(Engelstalig) voor meer informatie over pull-service.

## <a name="configuration-server-blocks"></a>Configuratie server blokken

Als u een configuratie server op het web wilt definiëren, maakt u een **ConfigurationRepositoryWeb** -blok.
Een **ConfigurationRepositoryWeb** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|AllowUnsecureConnection|booleaans|Ingesteld op **$True** om verbindingen van het knoop punt met de-server zonder verificatie toe te staan. Ingesteld op **$False** om verificatie te vereisen.|
|CertificateID|tekenreeks|De vinger afdruk van een certificaat dat wordt gebruikt voor verificatie bij de server.|
|ConfigurationNames|Teken reeks []|Een matrix met namen van configuraties die moeten worden opgehaald door het doel knooppunt. Deze worden alleen gebruikt als het knoop punt is geregistreerd bij de pull-service met behulp van een **RegistrationKey**. Zie [een pull-client met configuratie namen instellen](../pull-server/pullClientConfigNames.md)voor meer informatie.|
|RegistrationKey|tekenreeks|Een GUID waarmee het knoop punt wordt geregistreerd bij de pull-service. Zie [een pull-client met configuratie namen instellen](../pull-server/pullClientConfigNames.md)voor meer informatie.|
|ServerURL|tekenreeks|De URL van de configuratie service.|
|ProxyURL*|tekenreeks|De URL van de http-proxy die moet worden gebruikt voor de communicatie met de configuratie service.|
|ProxyCredential*|pscredential|Referentie die moet worden gebruikt voor de http-proxy.|

> [!NOTE]
>
> * Ondersteund in Windows versie 1809 en hoger.

Een voorbeeld script voor het vereenvoudigen van het configureren van de ConfigurationRepositoryWeb-waarde voor on-premises knoop punten is beschikbaar-Zie [DSC-configuratie genereren](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Als u een op SMB gebaseerde configuratie server wilt definiëren, maakt u een **ConfigurationRepositoryShare** -blok.
Een **ConfigurationRepositoryShare** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|Referentie|MSFT_Credential|De referentie die wordt gebruikt om te verifiëren bij de SMB-share.|
|Bronpad|tekenreeks|Het pad naar de SMB-share.|

## <a name="resource-server-blocks"></a>Resource server blokken

Voor het definiëren van een webbronserver maakt u een **ResourceRepositoryWeb** -blok.
Een **ResourceRepositoryWeb** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|AllowUnsecureConnection|booleaans|Ingesteld op **$True** om verbindingen van het knoop punt met de-server zonder verificatie toe te staan. Ingesteld op **$False** om verificatie te vereisen.|
|CertificateID|tekenreeks|De vinger afdruk van een certificaat dat wordt gebruikt voor verificatie bij de server.|
|RegistrationKey|tekenreeks|Een GUID waarmee het knoop punt wordt geïdentificeerd voor de pull-service.|
|ServerURL|tekenreeks|De URL van de configuratie server.|
|ProxyURL*|tekenreeks|De URL van de http-proxy die moet worden gebruikt voor de communicatie met de configuratie service.|
|ProxyCredential*|pscredential|Referentie die moet worden gebruikt voor de http-proxy.|

> [!NOTE]
>
> * Ondersteund in Windows versie 1809 en hoger.

Een voorbeeld script voor het vereenvoudigen van het configureren van de ResourceRepositoryWeb-waarde voor on-premises knoop punten is beschikbaar-Zie [DSC-configuratie genereren](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Als u een SMB-gebaseerde resource server wilt definiëren, maakt u een **ResourceRepositoryShare** -blok.
**ResourceRepositoryShare** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|Referentie|MSFT_Credential|De referentie die wordt gebruikt om te verifiëren bij de SMB-share. Zie [een DSC SMB-pull-server instellen](../pull-server/pullServerSMB.md) voor een voor beeld van het door geven van referenties|
|Bronpad|tekenreeks|Het pad naar de SMB-share.|

## <a name="report-server-blocks"></a>Blokken rapport server

Als u een rapport server wilt definiëren, maakt u een **ReportServerWeb** -blok.
De rapport server functie is niet compatibel met de SMB-gebaseerde pull-service.
**ReportServerWeb** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|AllowUnsecureConnection|booleaans|Ingesteld op **$True** om verbindingen van het knoop punt met de-server zonder verificatie toe te staan. Ingesteld op **$False** om verificatie te vereisen.|
|CertificateID|tekenreeks|De vinger afdruk van een certificaat dat wordt gebruikt voor verificatie bij de server.|
|RegistrationKey|tekenreeks|Een GUID waarmee het knoop punt wordt geïdentificeerd voor de pull-service.|
|ServerURL|tekenreeks|De URL van de configuratie server.|
|ProxyURL*|tekenreeks|De URL van de http-proxy die moet worden gebruikt voor de communicatie met de configuratie service.|
|ProxyCredential*|pscredential|Referentie die moet worden gebruikt voor de http-proxy.|

> [!NOTE]
>
> * Ondersteund in Windows versie 1809 en hoger.

Een voorbeeld script voor het vereenvoudigen van het configureren van de ReportServerWeb-waarde voor on-premises knoop punten is beschikbaar-Zie [DSC-configuratie genereren](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Gedeeltelijke configuraties

Als u een gedeeltelijke configuratie wilt definiëren, maakt u een **PartialConfiguration** -blok.
Zie voor meer informatie over gedeeltelijke configuraties [DSC-gedeeltelijke configuraties](../pull-server/partialConfigs.md).
**PartialConfiguration** definieert de volgende eigenschappen.

|Eigenschap|Type|Beschrijving|
|---|---|---|
|ConfigurationSource|teken reeks []|Een matrix met namen van configuratie servers, die eerder zijn gedefinieerd in **ConfigurationRepositoryWeb** -en **ConfigurationRepositoryShare** -blokken, waarbij de gedeeltelijke configuratie wordt opgehaald uit.|
|DependsOn|tekenreeks{}|Een lijst met namen van andere configuraties die moeten worden voltooid voordat deze gedeeltelijke configuratie wordt toegepast.|
|Description|tekenreeks|De tekst die wordt gebruikt om de gedeeltelijke configuratie te beschrijven.|
|ExclusiveResources|teken reeks []|Een matrix met bronnen die exclusief zijn voor deze gedeeltelijke configuratie.|
|RefreshMode|tekenreeks|Hiermee geeft u op hoe de LCM deze gedeeltelijke configuratie kan ophalen. De mogelijke waarden zijn __' disabled '__, __' push '__ en __' pull '__. <ul><li>__Uitgeschakeld__: deze gedeeltelijke configuratie is uitgeschakeld.</li><li> __Push__: de gedeeltelijke configuratie wordt naar het knoop punt gepusht door de cmdlet [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) aan te roepen. Nadat alle gedeeltelijke configuraties voor het knoop punt zijn gepusht of opgehaald van een service, kan de configuratie worden gestart door het aanroepen van `Start-DscConfiguration –UseExisting` . Dit is de standaardwaarde.</li><li>__Pull:__ Het knoop punt is geconfigureerd om regel matig te controleren op gedeeltelijke configuratie van een pull-service. Als deze eigenschap is ingesteld op __pull__, moet u een pull-service opgeven in een eigenschap __ConfigurationSource__ . Zie [Azure Automation DSC Overview](https://docs.microsoft.com/azure/automation/automation-dsc-overview)(Engelstalig) voor meer informatie over Azure Automation pull-service.</li></ul>|
|ResourceModuleSource|teken reeks []|Een matrix van de namen van resource servers waaruit de vereiste bronnen voor deze gedeeltelijke configuratie moeten worden gedownload. Deze namen moeten verwijzen naar service-eind punten die eerder zijn gedefinieerd in **ResourceRepositoryWeb** -en **ResourceRepositoryShare** -blokken.|

__Opmerking:__ gedeeltelijke configuraties worden ondersteund met Azure Automation DSC, maar er kan slechts één configuratie worden opgehaald uit elk Automation-account per knoop punt.

## <a name="see-also"></a>Zie ook

### <a name="concepts"></a>Concepten
[Overzicht van desired state Configuration](../overview/overview.md)

[Aan de slag met Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Meer informatie

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Een pull-client met configuratie namen instellen](../pull-server/pullClientConfigNames.md)
