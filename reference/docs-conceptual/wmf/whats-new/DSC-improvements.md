---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Verbeteringen van DSC in WMF 5.1
ms.openlocfilehash: 78c15f453977384ba437b0bd69cd620eb1a29fbd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "80978284"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Verbeteringen in desired state Configuration (DSC) in WMF 5,1

## <a name="dsc-class-resource-improvements"></a>Verbeteringen DSC-klasse resource

In WMF 5,1 hebben we de volgende bekende problemen opgelost:

- Get-DscConfiguration kan lege waarden (null) of fouten retour neren als een complex/hash-tabel type wordt geretourneerd door de functie Get () van een DSC-resource op basis van een klasse.
- Get-DscConfiguration retourneert een fout als de RunAs-referentie wordt gebruikt in de DSC-configuratie.
- Op klassen gebaseerde resource kan niet worden gebruikt in een samengestelde configuratie.
- Start-DscConfiguration loopt vast als op de klasse gebaseerde resource een eigenschap van een eigen type heeft.
- Bron op basis van een klasse kan niet worden gebruikt als exclusieve resource.

## <a name="dsc-resource-debugging-improvements"></a>Verbeteringen in DSC-bron fout opsporing

In WMF 5,0 is het Power Shell-fout opsporingsprogramma niet gestopt bij de op klassen gebaseerde resource methode (Get/set/test) direct. In WMF 5,1 stopt het fout opsporingsprogramma bij de op klassen gebaseerde resource methode op dezelfde manier als voor op MOF gebaseerde bronnen methoden.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>De DSC pull-client ondersteunt TLS 1,1 en TLS 1,2

Voorheen werd de DSC pull-client alleen ondersteund SSL 3.0 en TLS 1.0 via HTTPS-verbindingen. Wanneer er meer beveiligde protocollen worden gebruikt, werkt de pull-client niet meer. De DSC pull-client in WMF 5,1 biedt geen ondersteuning meer voor SSL 3,0 en voegt ondersteuning toe voor de meer beveiligde TLS 1,1-en TLS 1,2-protocollen.

## <a name="improved-pull-server-registration"></a>Verbeterde registratie van de pull-server

In eerdere versies van WMF zouden gelijktijdige registraties/rapporten naar een DSC-pull-server tijdens het gebruik van de ESENT-data base ertoe leiden dat de LCM niet kan worden geregistreerd en/of gerapporteerd. In dergelijke gevallen heeft de gebeurtenis logboeken op de pull-server de fout ' exemplaar naam al in gebruik '. Dit wordt veroorzaakt door een onjuist patroon dat wordt gebruikt voor toegang tot de ESENT-data base in een scenario met meerdere threads. Dit probleem is opgelost in WMF 5,1. Gelijktijdige registraties of rapporten (met behulp van ESENT-data base) werken prima in WMF 5,1. Dit probleem is alleen van toepassing op de ESENT-data base en is niet van toepassing op de OLEDB-data base.

## <a name="enable-circular-log-on-esent-database-instance"></a>Circulair data base-exemplaar van het logboek inschakelen.

In de eariler-versie van DSC-PullServer werden de ESENT-database logboek bestanden de schijf ruimte van de PullServer opgevuld omdat het data base-exemplaar werd gemaakt zonder circulaire logboek registratie. In deze release hebt u de mogelijkheid om de circulaire logboek registratie van het exemplaar te beheren met de web. config van de pullserver. CircularLogging is standaard ingesteld op TRUE.

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a>WOW64-ondersteuning voor configuratie sleutelwoord

Het `Configuration` sleutel woord wordt nu ondersteund in WOW64 op een 64-bits computer. Dit betekent dat een DSC-configuratie kan worden gedefinieerd en gecompileerd binnen een 32-bits proces, zoals Windows PowerShell ISE (x86) dat wordt uitgevoerd op een 64-bits computer.

## <a name="pull-partial-configuration-naming-convention"></a>Naamgevings Conventie voor gedeeltelijke configuratie pullen

In de vorige versie is de naam Conventie voor een gedeeltelijke configuratie het MOF-bestand in de pull-Server/service moet overeenkomen met de gedeeltelijke configuratie naam opgegeven in de lokale Configuration Manager-instellingen die op zijn beurt moeten overeenkomen met de configuratie naam die in het MOF-bestand is inge sloten.

Bekijk de onderstaande moment opnamen:

- Lokale configuratie-instellingen waarmee een gedeeltelijke configuratie wordt gedefinieerd die een knoop punt mag ontvangen.

  ![Voor beeld van een automatische configuratie](media/DSC-improvements/MetaConfigPartialOne.png)

- Voor beeld van gedeeltelijke configuratie definitie

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

- Configuratiepad is inge sloten in het gegenereerde MOF-bestand.

  ![Voor beeld van gegenereerd MOF-bestand](media/DSC-improvements/PartialGeneratedMof.png)

- Bestands naam in de opslag plaats voor pull-configuratie

  ![Bestands naam in configuratie opslagplaats](media/DSC-improvements/PartialInConfigRepository.png)

  Azure Automation Service naam heeft MOF-bestanden `<ConfigurationName>.<NodeName>.mof`gegenereerd als. De onderstaande configuratie compileert daarom met PartialOne. localhost. mof.

  Hierdoor is het onmogelijk om een van uw gedeeltelijke configuratie van Azure Automation-Service te verzamelen.

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

  In WMF 5,1 kan een gedeeltelijke configuratie in de pull-Server/-service worden genoemd `<ConfigurationName>.<NodeName>.mof`. Bovendien, als een machine een configuratie van een pull-Server/-service haalt, kan het configuratie bestand in de opslag plaats van de pull-server een wille keurige bestands naam hebben. Deze naam flexibiliteit biedt u de mogelijkheid om uw knoop punten gedeeltelijk te beheren door Azure Automation Service, waarbij bepaalde configuraties voor uw knoop punt afkomstig zijn van Azure Automation DSC en met een gedeeltelijke configuratie die u lokaal beheert.

  De onderstaande configuratie stelt een knoop punt in dat zowel lokaal als door Azure Automation Service moet worden beheerd.

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>PsDscRunAsCredential gebruiken met DSC-samengestelde resources

Er is ondersteuning toegevoegd voor het gebruik van [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) met DSC- [samengestelde](/powershell/scripting/dsc/resources/authoringresourcecomposite) resources.

U kunt nu een waarde opgeven voor **PsDscRunAsCredential** bij het gebruik van samengestelde resources binnen configuraties. Als u deze opgeeft, worden alle resources in een samengestelde resource uitgevoerd als een runas-gebruiker. Als een samengestelde resource een andere samengestelde resource aanroept, worden alle resources ook uitgevoerd als runas-gebruiker. Runas-referenties worden door gegeven aan elk niveau van de samengestelde resource hiërarchie. Als een resource in een samengestelde resource een eigen waarde voor **PsDscRunAsCredential**opgeeft, wordt er tijdens het compileren van de configuratie een samenvoeg fout veroorzaakt.

In dit voor beeld ziet u het gebruik van de [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) -samengestelde resource die is opgenomen in de PSDesiredStateConfiguration-module.

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Identieke dubbele resources in een configuratie toestaan

DSC staat geen conflicterende resource definities binnen een configuratie toe of verwerkt deze. In plaats van het conflict op te lossen, mislukt dit gewoon. Naarmate het opnieuw gebruiken van de configuratie wordt gebruikt door samengestelde resources, enzovoort, worden er vaker conflicten optreden. Wanneer conflicterende resource definities identiek zijn, moet DSC slim zijn en dit toestaan. In deze release ondersteunen we meerdere bron instanties met identieke definities:

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

In eerdere releases zou het resultaat een mislukte compilatie zijn vanwege een conflict tussen de WindowsFeature-FE_IIS en de WindowsFeature-Worker_IIS exemplaren die proberen te controleren of de functie web-server is geïnstalleerd. U ziet dat *alle* eigenschappen die worden geconfigureerd, identiek zijn in deze twee configuraties. Omdat *alle* eigenschappen in deze twee resources identiek zijn, resulteert dit in een succes volle compilatie.

Als een van de eigenschappen verschilt tussen de twee resources, worden ze niet beschouwd als identiek en mislukt het compileren.

## <a name="dsc-module-and-configuration-signing-validations"></a>Validatie van de DSC-module en configuratie-ondertekening

In DSC worden configuraties en modules gedistribueerd naar beheerde computers vanaf de pull-server. Als de pull-server is aangetast, kan een aanvaller de configuraties en modules op de pull-server mogelijk wijzigen en deze naar alle beheerde knoop punten distribueren.

In WMF 5,1 ondersteunt DSC het valideren van digitale hand tekeningen in Catalog en configuratie (. MOF-bestanden). Deze functie voor komt dat knoop punten configuraties of module bestanden uitvoeren die niet zijn ondertekend door een vertrouwde ondertekenaar of waarvan is geknoeid nadat deze zijn ondertekend door een vertrouwde ondertekenaar.

### <a name="how-to-sign-configuration-and-module"></a>Configuratie en module ondertekenen

- Configuratie bestanden (. Mof's): de bestaande Power shell [-cmdlet Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) wordt uitgebreid ter ondersteuning van het ondertekenen van MOF-bestanden.
- Modules: ondertekening van modules wordt uitgevoerd door de bijbehorende module catalogus te ondertekenen met behulp van de volgende stappen:
  1. Een catalogus bestand maken: een catalogus bestand bevat een verzameling cryptografische hashes of vinger afdrukken. Elke vinger afdruk komt overeen met een bestand dat is opgenomen in de module. De nieuwe cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog)is toegevoegd om gebruikers in staat te stellen een catalogus bestand voor hun module te maken.
  2. Het catalogus bestand ondertekenen: gebruik [set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) om het catalogus bestand te ondertekenen.
  3. Plaats het catalogus bestand in de map module. Per Conventie moet het module catalogus bestand onder de module map met dezelfde naam als de module worden geplaatst.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>LocalConfigurationManager-instellingen voor het inschakelen van validaties van ondertekening

#### <a name="pull"></a>Pull

De LocalConfigurationManager van een knoop punt voert de validatie van modules en configuraties op basis van de huidige instellingen uit. Validatie van hand tekeningen is standaard uitgeschakeld. Handtekening validatie kan worden ingeschakeld door het blok ' SignatureValidation ' toe te voegen aan de meta-configuratie definitie van het knoop punt, zoals hieronder wordt weer gegeven:

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

Bij het instellen van de hierboven genoemde configuratie op een knoop punt wordt handtekening validatie op gedownloade configuraties en modules ingeschakeld. De lokale Configuration Manager voert de volgende stappen uit om de digitale hand tekeningen te controleren.

1. Controleer de hand tekening op een configuratie bestand (. MOF) is geldig met de `Get-AuthenticodeSignature` cmdlet.
2. Controleer of de certificerings instantie die de ondertekenaar heeft geautoriseerd, vertrouwd is.
3. Down load module/Resource-afhankelijkheden van de configuratie naar een tijdelijke locatie.
4. Controleer de hand tekening van de catalogus die is opgenomen in de module.
   - Zoek een `<moduleName>.cat` bestand en controleer de hand tekening `Get-AuthenticodeSignature`met behulp van.
   - Controleer of de certificerings instantie die de ondertekenaar heeft geverifieerd, vertrouwd is.
   - Controleer of de inhoud van de modules niet is geknoeid met de nieuwe `Test-FileCatalog`cmdlet.
5. `Install-Module`Aan`$env:ProgramFiles\WindowsPowerShell\Modules\`
6. Proces configuratie

> [!NOTE]
> Handtekening validatie voor module-Catalog en configuratie wordt alleen uitgevoerd wanneer de configuratie voor de eerste keer wordt toegepast op het systeem of wanneer de module wordt gedownload en geïnstalleerd.
> Met consistentie runs wordt de hand tekening van huidige. MOF of de bijbehorende module-afhankelijkheden niet gevalideerd. Als de verificatie is mislukt in elk stadium, bijvoorbeeld als de configuratie die is opgehaald van de pull-server niet is ondertekend, wordt de verwerking van de configuratie beëindigd met de fout die hieronder wordt weer gegeven en worden alle tijdelijke bestanden verwijderd.

![Configuratie van voorbeeld fout uitvoer](media/DSC-improvements/PullUnsignedConfigFail.png)

Op dezelfde manier wordt het ophalen van een module waarvan de catalogus niet is ondertekend met de volgende fout:

![Uitvoer module voor voorbeeld fout](media/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a>Push

Een configuratie die wordt geleverd met behulp van push kan worden geknoeid met de bron voordat deze wordt afgeleverd bij het knoop punt. De lokale Configuration Manager voert vergelijk bare handtekening validatie stappen uit voor gepushte of gepubliceerde configuratie (s). Hieronder vindt u een volledig voor beeld van handtekening validatie voor push.

- Schakel handtekening validatie in op het knoop punt.

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

- Maak een voor beeld van een configuratie bestand.

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

- Probeer het niet-ondertekende configuratie bestand naar het knoop punt te pushen.

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](media/DSC-improvements/PushUnsignedMof.png)

- Onderteken het configuratie bestand met het certificaat voor ondertekening van programma code.

  ![SignMofFile](media/DSC-improvements/SignMofFile.png)

- Probeer het ondertekende MOF-bestand te pushen.

  ![PushSignedMofFile](media/DSC-improvements/PushSignedMof.png)
