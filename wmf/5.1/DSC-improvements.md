---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: DSC-verbeteringen in WMF 5.1
ms.openlocfilehash: 76cfb1a1e8908fbb751562c1d5081c116368a8f6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Verbeteringen in Desired State Configuration (DSC) in WMF 5.1

## <a name="dsc-class-resource-improvements"></a>DSC klasse resource verbeteringen

We hebben de volgende bekende problemen opgelost in WMF 5.1:
* Get-DscConfiguration mogelijk lege waarden (null) of fouten als resultaat als een type complex/hash-tabel wordt geretourneerd door de functie Get() van een klasse gebaseerde DSC-resource.
* Get-DscConfiguration retourneert fout als RunAs-referentie wordt gebruikt in DSC-configuratie.
* Op basis van een klasse resource kan niet worden gebruikt in een samengestelde configuratie.
* Start DscConfiguration loopt vast als bron op basis van klasse een eigenschap van een eigen type heeft.
* Op basis van een klasse resource kan niet worden gebruikt als een exclusieve resource.


## <a name="dsc-resource-debugging-improvements"></a>DSC-resource verbeteringen foutopsporing
In WMF 5.0 is de PowerShell-foutopsporing niet gestopt op de resource op basis van klasse-methode (Set-Get/Test) rechtstreeks.
In WMF 5.1 stopt het foutopsporingsprogramma bij de methode op basis van een klasse resource op dezelfde manier als voor bronnen op basis van het MOF-methoden.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>DSC-pull-client ondersteunt TLS 1.1 en TLS 1.2
Voorheen ondersteund de DSC-pull-client alleen SSL3.0 en TLS1.0 via HTTPS-verbindingen.
Wanneer geforceerde veiliger protocollen gebruiken, zou de pull-client niet meer werkt.
In WMF 5.1, de DSC pull-client niet langer biedt ondersteuning voor SSL 3.0 en voegt ondersteuning toe voor de veiliger TLS 1.1 en TLS 1.2-protocollen.

## <a name="improved-pull-server-registration"></a>Verbeterde pull-server registreren ##

In eerdere versies van WMF zou gelijktijdige registraties/reporting aanvragen voor een DSC-pull-server tijdens het gebruik van de database ESENT leiden tot LCM niet te registreren en/of te rapporteren.
In dergelijke gevallen de gebeurtenislogboeken op de pull-server heeft de fout "Exemplaarnaam al in gebruik."
Dit is vanwege een onjuist patroon wordt gebruikt voor toegang tot de ESENT-database in een scenario met meerdere threads.
In WMF 5.1, is dit probleem opgelost.
Werkt probleemloos in WMF 5.1 gelijktijdige registraties of reporting (met betrekking tot ESENT database).
Dit probleem is alleen van toepassing op de ESENT-database en niet van toepassing op de OLEDB-database.

## <a name="enable-circular-log-on-esent-database-instance"></a>Permanente logboekbestand voor database-exemplaar ESENT inschakelen
Eariler versie van DSC-PullServer, zijn de schijfruimte van de pullserver becouse die is de database-instantie wordt gemaakt zonder circulair vastleggen invullen van de logboekbestanden van de ESENT-database. U hebt de optie om te bepalen het gedrag circulair vastleggen van het exemplaar met behulp van web.config van de pullserver in deze release. CircularLogging is standaard ingesteld op TRUE.
```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```
## <a name="pull-partial-configuration-naming-convention"></a>Pull-naamconventie gedeeltelijke configuratie
In de vorige release de naamconventie voor een gedeeltelijke configuratie is dat het MOF-bestandsnaam in de pull-server/service moet overeenkomen met de configuratienaam van de van gedeeltelijke opgegeven in de lokale configuration manager-instellingen die op zijn beurt moeten overeenkomen met de naam van de configuratie is ingesloten in het MOF-bestand.

Zie de onderstaande momentopnamen:

• Lokale configuratie-instellingen waarmee een gedeeltelijke configuratie dat is toegestaan voor het ontvangen van een knooppunt zijn gedefinieerd.

![Voorbeeld metaconfiguratie](../images/MetaConfigPartialOne.png)

• Voorbeeld gedeeltelijke configuratiedefinitie

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

• 'ConfigurationName' ingesloten in het gegenereerde MOF-bestand.

![Voorbeeld gegenereerde mof-bestand](../images/PartialGeneratedMof.png)

• Bestandsnaam in de opslagplaats pull-configuratie

![Bestandsnaam in de opslagplaats voor configuratie](../images/PartialInConfigRepository.png)

Naam van de service Azure Automation gegenereerd MOF-bestanden als `<ConfigurationName>.<NodeName>.mof`.
De onderstaande configuratie compileert dus naar PartialOne.localhost.mof.

Hierdoor was het niet mogelijk in pull een van de configuratie van uw gedeeltelijke van Azure Automation-service.

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

In WMF 5.1, een gedeeltelijke configuratie in de pull-server/service kan de naam `<ConfigurationName>.<NodeName>.mof`.
Bovendien, als een machine is binnenhalen van een configuratie voor één uit een pull serverservice vervolgens in het configuratiebestand op de pull-server configuration opslagplaats hebben een willekeurige bestandsnaam.
Deze flexibiliteit naming kunt u voor het beheren van uw knooppunten gedeeltelijk door Azure Automation-service, waarbij een bepaalde configuratie voor uw knooppunt afkomstig is uit Azure Automation DSC en met een gedeeltelijke configuratie die u lokaal beheren.

De metaconfiguratie hieronder ingesteld op een knooppunt als niet-beheerd zowel lokaal als door Azure Automation-service.

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

# <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Met behulp van PsDscRunAsCredential met samengestelde DSC-resources

Ondersteuning voor het gebruik van toegevoegd [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) met DSC [samengestelde](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) resources.

U kunt nu een waarde opgeven voor PsDscRunAsCredential bij gebruik van samengestelde bronnen binnen configuraties.
Als u opgeeft, wordt alle resources binnen een samengestelde bron uitgevoerd als een RunAs-gebruiker.
Als een samengestelde bron een andere samengestelde bron aanroept, zijn alle bijbehorende resources ook uitgevoerd als RunAs-gebruiker.
Run as-referenties worden doorgegeven aan een niveau van de samengestelde bron-hiërarchie.
Als een bron binnen een samengestelde bron wordt een eigen waarde voor PsDscRunAsCredential opgegeven, resulteert een merge-fout tijdens het compileren van de configuratie.

Dit voorbeeld ziet u informatie over het gebruik met [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) samengestelde bron opgenomen in de module PSDesiredStateConfiguration.



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

##<a name="dsc-module-and-configuration-signing-validations"></a>DSC-module en configuratie validaties ondertekening
In DSC worden-configuraties en modules gedistribueerd naar beheerde computers van de pull-server.
Als de pull-server is aangetast, kan mogelijk een aanvaller de modules die zich in de pull-server en de configuraties aanpassen en laat het gedistribueerd naar alle beheerde knooppunten, inbreuk op deze.

 In WMF 5.1 DSC ondersteunt de digitale handtekeningen van catalogus en de configuratie valideren (. MOF)-bestanden.
Deze functie wordt voorkomen dat knooppunten configuraties of module-bestanden die niet zijn ondertekend door een vertrouwde ondertekenaar of waarmee is geknoeid nadat ze zijn ondertekend door vertrouwde ondertekenaar wordt uitgevoerd.



###<a name="how-to-sign-configuration-and-module"></a>Het ondertekenen van de configuratie en -module
***
* Configuratiebestanden (. MOF-bestanden): de bestaande PowerShell-cmdlet [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) wordt uitgebreid met ondersteuning voor ondertekening van het MOF-bestanden.
* Modules: Ondertekening van modules wordt uitgevoerd door de ondertekening van de corresponderende module catalogus met behulp van de volgende stappen uit:
    1. Een catalogusbestand maken: een catalogusbestand bevat een verzameling van cryptografische hashes of vingerafdrukken.
       Elke vingerafdruk overeenkomt met een bestand dat is opgenomen in de module.
       De nieuwe cmdlet [nieuw FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), zodat gebruikers kunnen maken van een catalogusbestand voor de module is toegevoegd.
    2. Meld u aan het catalogusbestand: Gebruik [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) om de catalogusbestand te ondertekenen.
    3. Plaats het catalogusbestand in de modulemap.
Volgens de conventies worden catalogusbestand module onder de modulemap met dezelfde naam als de module geplaatst.

###<a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>Instellingen voor LocalConfigurationManager ondertekenen validaties inschakelen

####<a name="pull"></a>Pull-
De LocalConfigurationManager van een knooppunt voert ondertekenen validatie van modules en configuraties op basis van de huidige instellingen.
Validatie van handtekening is standaard uitgeschakeld.
Validatie van handtekening kan worden ingeschakeld door het blok 'SignatureValidation' toe te voegen aan de definitie van de meta-configuratie van het knooppunt zoals hieronder:

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
        # By default, LCM uses the default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM uses this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
 ```

Het instellen van de bovenstaande metaconfiguratie toe op een knooppunt kunt handtekeningvalidatie op gedownloade configuraties en modules.
De lokale Configuration Manager voert de volgende stappen uit om te controleren of de digitale handtekeningen.

1. Controleer of de handtekening van een configuratiebestand (. MOF) is ongeldig.
   Dit maakt gebruik van de PowerShell-cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), die wordt uitgebreid in 5.1 ter ondersteuning van de handtekeningvalidatie MOF.
2. Controleer of de certificeringsinstantie die de ondertekenaar gemachtigd wordt vertrouwd.
3. Module of systeembronnen afhankelijkheden van de configuratie naar een tijdelijke locatie downloaden.
4. Controleer of de handtekening van de catalogus die is opgenomen in de module.
    * Zoeken naar een `<moduleName>.cat` bestands- en controleer of de handtekening met de cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Controleer of de certificeringsinstantie (CA) die de ondertekenaar geverifieerd wordt vertrouwd.
    * Controleer of de inhoud van de modules niet is geknoeid met de nieuwe cmdlet [Test FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).
5. Installatie-Module voor $env: ProgramFiles\WindowsPowerShell\Modules\
6. Procesconfiguratie

> Opmerking: De handtekeningvalidatie van module-catalogus en -configuratie wordt alleen uitgevoerd wanneer de configuratie wordt toegepast op het systeem voor het eerst of wanneer de module wordt gedownload en geïnstalleerd.
De handtekening van Current.mof of de afhankelijkheden van de module wordt niet gevalideerd door consistentiecontrole wordt uitgevoerd.
Verificatie is mislukt in elk stadium, bijvoorbeeld als de configuratie die is opgehaald uit de pull-server is niet ondertekend, vervolgens verwerking van de configuratie wordt beëindigd met de fout hieronder wordt weergegeven als alle tijdelijke bestanden worden verwijderd.

![Uitvoer van de voorbeeldconfiguratie-fout](../images/PullUnsignedConfigFail.png)

Binnenhalen van een module waarvan catalogus niet is ondertekend op dezelfde manier resulteert in de volgende fout:

![Voorbeeld uitvoer Foutenmodule](../images/PullUnisgnedCatalog.png)

####<a name="push"></a>Push
Een configuratie met behulp van push geleverd kan op de bron geknoeid voordat deze naar het knooppunt afgeleverd.
De lokale Configuration Manager voert vergelijkbare handtekening Validatiestappen voor configuratie (pushed of gepubliceerd s).
Hieronder vindt u een compleet voorbeeld van validatie van handtekening voor de push.

* Handtekeningvalidatie op het knooppunt inschakelen.

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
* Maak een voorbeeldconfiguratiebestand.

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

* Probeer de niet-ondertekende configuratiebestand pushen naar het knooppunt.

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```
![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

* Meld u aan het configuratiebestand met code signing-certificaat.

![SignMofFile](../images/SignMofFile.png)

* Probeer het ondertekende MOF-bestand worden gepusht.

![SignMofFile](../images/PushSignedMof.png)
