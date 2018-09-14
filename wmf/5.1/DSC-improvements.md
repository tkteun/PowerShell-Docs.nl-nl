---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: DSC-verbeteringen in WMF 5.1
ms.openlocfilehash: 92f82d62550e105a187fd7c0c58b49367c646a7e
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523019"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Verbeteringen in Desired State Configuration (DSC) in WMF 5.1

## <a name="dsc-class-resource-improvements"></a>DSC-klasse resource verbeteringen

In WMF 5.1, hebben we de volgende bekende problemen opgelost:

- Get-DscConfiguration mogelijk lege waarden (null) of fouten als resultaat als een type complex/hash-tabel wordt geretourneerd door de functie Get() van een klasse op basis van DSC-resource.
- Get-DscConfiguration retourneert fout als de RunAs-referentie in DSC-configuratie wordt gebruikt.
- Op basis van een klasse resource kan niet worden gebruikt in een samengestelde configuratie.
- Start-DscConfiguration loopt vast als bron op basis van een klasse een eigenschap van een eigen type heeft.
- Op basis van een klasse resource kan niet worden gebruikt als een exclusieve resource.

## <a name="dsc-resource-debugging-improvements"></a>Verbeteringen in Foutopsporing voor DSC-resource

In WMF 5.0, is de PowerShell-foutopsporing niet gestopt op de resource op basis van een klasse, methode (Get/Set/Test) rechtstreeks.
In WMF 5.1 stopt het foutopsporingsprogramma op dezelfde manier als voor de resources op basis van MOF-methoden op de resource op basis van een klasse-methode.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>DSC-pull-client biedt ondersteuning voor TLS 1.1 en TLS 1.2

Voorheen was ondersteund de DSC-pull-client alleen SSL3.0 en TLS1.0 via HTTPS-verbindingen.
Wanneer geforceerde veiliger protocollen gebruiken, dan werkt de pull-client niet.
In WMF 5.1, de DSC pull-client niet langer ondersteuning biedt voor SSL 3.0 en voegt ondersteuning toe voor de beter beveiligde TLS 1.1 en TLS 1.2-protocollen.

## <a name="improved-pull-server-registration"></a>Verbeterde pull-server registreren

In eerdere versies van WMF zou gelijktijdige registraties/reporting aanvragen voor een DSC-pull-server tijdens het gebruik van de database ESENT leiden tot LCM niet te registreren en/of rapport.
In dergelijke gevallen de gebeurtenislogboeken op de pull-server heeft de fout 'Exemplaarnaam al in gebruik'.
Dit is vanwege een onjuiste patroon wordt gebruikt voor toegang tot de ESENT-database in een scenario met meerdere threads.
In WMF 5.1, heeft dit probleem is opgelost.
Gelijktijdige registraties of reporting (met inschakeling van ESENT-database) werkt prima in WMF 5.1.
Dit probleem geldt alleen voor de database ESENT en geldt niet voor de OLE DB-database.

## <a name="enable-circular-log-on-esent-database-instance"></a>Permanente logboekbestand op ESENT-database-exemplaar inschakelen

Eariler versie van DSC-PullServer, zijn de logboekbestanden van de ESENT-database de schijfruimte van de pullserver becouse die de database-instantie werd gemaakt zonder circulair vastleggen terechtkomen. In deze release hebt u de optie voor het beheren van het gedrag circulair vastleggen van het exemplaar met behulp van het bestand web.config van de pullserver. CircularLogging is standaard ingesteld op TRUE.

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a>De naamconventie gedeeltelijke configuratie ophalen

In de vorige versie, de naamconventie voor een gedeeltelijke configuratie is dat de naam van de MOF-bestand in de pull-server/service moet overeenkomen met de naam van de gedeeltelijke configuratie opgegeven in de lokale configuration manager-instellingen die op zijn beurt moeten overeenkomen met de naam van de configuratie is ingesloten in het MOF-bestand.

Zie de onderstaande momentopnamen:

- Lokale configuratie-instellingen die u definieert een gedeeltelijke configuratie dat is toegestaan voor het ontvangen van een knooppunt.

![Voorbeeld metaconfiguration](../images/MetaConfigPartialOne.png)

- De definitie van de voorbeeld-gedeeltelijke configuratie

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

- 'ConfigurationName' ingesloten in het gegenereerde MOF-bestand.

![Voorbeeld van gegenereerde mof-bestand](../images/PartialGeneratedMof.png)

- Bestandsnaam in de opslagplaats van de pull-configuratie

![Bestandsnaam in de opslagplaats van configuratie](../images/PartialInConfigRepository.png)

Azure Automation-servicenaam gegenereerd MOF-bestanden als `<ConfigurationName>.<NodeName>.mof`.
Dus de onderstaande configuratie worden gecompileerd naar PartialOne.localhost.mof.

Dit werd het onmogelijk voor pull een van uw gedeeltelijke configuratie in Azure Automation-service.

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

In WMF 5.1, een gedeeltelijke configuratie in de pull-server/service kan worden met de naam als `<ConfigurationName>.<NodeName>.mof`.
Als een virtuele machine is een eenmalige configuratie van een pull binnenhalen kunt serverservice vervolgens het configuratiebestand op de opslagplaats van de pull-server-configuratie bovendien een bestandsnaam hebben.
Deze naamgevingsconventie flexibiliteit kunt u uw knooppunten gedeeltelijk beheren met Azure Automation-service, waar een configuratie voor het knooppunt is binnenkort in Azure Automation DSC en waarbij een gedeeltelijke configuratie die u lokaal beheren.

De metaconfiguration hieronder ingesteld op een knooppunt om te worden beheerd zowel lokaal als door Azure Automation-service.

```powershell
[DscLocalConfigurationManager()]
Configuration RegistrationMetaConfig
{
    Settings
    {
        RefreshFrequencyMins = 30
        RefreshMode = "PULL"
    }

    ConfigurationRepositoryWeb web
    {
        ServerURL =  $endPoint
        RegistrationKey = $registrationKey
        ConfigurationNames = $configurationName
    }

    # Partial configuration managed by Azure Automation service.
    PartialConfiguration PartialConfigurationManagedByAzureAutomation
    {
        ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
    }

    # This partial configuration is managed locally.
    PartialConfiguration OnPremisesConfig
    {
        RefreshMode = "PUSH"
        ExclusiveResources = @("Script")
    }

}

RegistrationMetaConfig
Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Met behulp van PsDscRunAsCredential met samengestelde DSC-resources

Ondersteuning voor het gebruik van toegevoegd [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) met DSC [samengestelde](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.

U kunt nu een waarde opgeven voor PsDscRunAsCredential bij het gebruik van samengestelde resources binnen configuraties.
Wanneer is opgegeven, wordt alle resources binnen een samengestelde resource uitgevoerd als een RunAs-gebruiker.
Als een samengestelde resource aanroept die een andere samengestelde resource, worden alle bijbehorende resources ook uitgevoerd als RunAs-gebruiker.
Run as-referenties worden doorgegeven aan een willekeurig niveau in de hiërarchie samengestelde resource.
Als een resource binnen een samengestelde resource een eigen waarde voor PsDscRunAsCredential bevat, resulteert een merge-fout tijdens de compilatie van de configuratie.

Dit voorbeeld laat zien voor gebruik met [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) samengestelde resource opgenomen in de module PSDesiredStateConfiguration.

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="dsc-module-and-configuration-signing-validations"></a>DSC-module en configuratie van validaties ondertekenen

DSC, worden configuraties en -modules gedistribueerd naar beheerde computers van de pull-server.
Als de pull-server is geknoeid, kan mogelijk een aanvaller wijzigen van de configuraties en -modules op de pull-server en dat er mee worden gedistribueerd naar alle beheerde knooppunten, verlies van al deze.

In WMF 5.1, DSC biedt ondersteuning voor de digitale handtekeningen van catalogus en de configuratie valideren (. MOF)-bestanden.
Deze functie wordt voorkomen dat knooppunten configuraties of module bestanden die niet zijn ondertekend door een vertrouwde ondertekenaar of waarmee is geknoeid nadat ze zijn ondertekend door vertrouwde ondertekenaar wordt uitgevoerd.

### <a name="how-to-sign-configuration-and-module"></a>Het ondertekenen van de configuratie en -module

***
* Configuratiebestanden (. MOF-bestanden): de bestaande PowerShell-cmdlet [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) wordt uitgebreid met ondersteuning voor ondertekening van de MOF-bestanden.
* Modules: Ondertekening van modules wordt uitgevoerd door het ondertekenen van de bijbehorende module-catalogus met behulp van de volgende stappen uit:
    1. Maken van een catalogusbestand: een catalogusbestand bevat een verzameling van cryptografische hashes of de vingerafdrukken.
       Elke vingerafdruk komt overeen met een bestand dat is opgenomen in de module.
       De nieuwe cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), zodat gebruikers kunnen maken van een catalogusbestand voor de module is toegevoegd.
    2. Meld u aan de catalogusbestand: Gebruik [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) om de catalogusbestand te ondertekenen.
    3. Plaats het catalogusbestand in de modulemap.
Volgens de conventies wordt moet module catalogusbestand worden geplaatst in de modulemap met dezelfde naam als de module.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>Instellingen voor LocalConfigurationManager ondertekenen validaties inschakelen

#### <a name="pull"></a>Pull

De LocalConfigurationManager van een knooppunt voert ondertekenen validatie van modules en configuraties op basis van de huidige instellingen.
Handtekeningvalidatie is standaard uitgeschakeld.
Handtekeningvalidatie kan worden ingeschakeld door het blok 'SignatureValidation' toe te voegen aan de definitie meta-configuratie van het knooppunt zoals hieronder:

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

De bovenstaande metaconfiguration instellen op een knooppunt, kunt handtekeningvalidatie op gedownloade configuraties en -modules.
De Local Configuration Manager voert de volgende stappen uit om te controleren of de digitale handtekeningen.

1. Controleer of de handtekening van een configuratiebestand (. MOF) is geldig.
   Het maakt gebruik van de PowerShell-cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), die in 5.1 ter ondersteuning van MOF handtekeningvalidatie is uitgebreid.
2. Controleer of de certificeringsinstantie die de ondertekenaar gemachtigd wordt vertrouwd.
3. Afhankelijkheden van de configuratie van de module/resource naar een tijdelijke locatie downloaden.
4. Controleer of de handtekening van de catalogus die is opgenomen in de module.
    * Zoek een `<moduleName>.cat` bestands- en controleer of de handtekening met behulp van de cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Controleer of de certificeringsinstantie (CA) die de ondertekenaar geverifieerd wordt vertrouwd.
    * Controleer of de inhoud van de modules niet is geknoeid met de nieuwe cmdlet [Test FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).
5. Install-Module voor $env: ProgramFiles\WindowsPowerShell\Modules\
6. Procesconfiguratie van

> Opmerking: Handtekeningvalidatie van module-catalogus en de configuratie wordt alleen uitgevoerd wanneer de configuratie wordt toegepast op het systeem voor de eerste keer of wanneer de module wordt gedownload en geïnstalleerd.
Consistentiecontrole wordt uitgevoerd, wordt de handtekening van Current.mof of de module-afhankelijkheden niet gevalideerd.
Als verificatie is mislukt tijdens elke fase, bijvoorbeeld, als de configuratie die is opgehaald uit de pull-server is niet ondertekend, klikt u vervolgens verwerking van de configuratie wordt beëindigd met de fout die hieronder wordt weergegeven en alle tijdelijke bestanden worden verwijderd.

![Uitvoer van de voorbeeldconfiguratie-fout](../images/PullUnsignedConfigFail.png)

Binnenhalen van een module met-catalogus niet is ondertekend op dezelfde manier, resulteert dit in de volgende fout:

![Uitvoer van de voorbeeldmodule-fout](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a>Push

Een configuratie die is geleverd met behulp van push kan worden geknoeid bij de bron voordat deze naar het knooppunt geleverd.
De Local Configuration Manager voert gelijksoortige stappen van de handtekening validatie voor gepushte of gepubliceerd configuratie (s).
Hieronder volgt een compleet voorbeeld van validatie van de handtekening voor pushmeldingen.

- Handtekeningvalidatie op het knooppunt inschakelen.

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'
    }
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType =  'Configuration','Module'
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

- Een voorbeeld-configuratiebestand maken.

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

- Probeer de niet-ondertekende configuratiebestand pushen naar het knooppunt.

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- Meld u aan het configuratiebestand met behulp van certificaat voor ondertekening van programmacode.

![SignMofFile](../images/SignMofFile.png)

- Probeer het pushen van de ondertekende MOF-bestand.

![SignMofFile](../images/PushSignedMof.png)
