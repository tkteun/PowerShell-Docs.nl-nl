---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Verbeteringen van DSC in WMF 5.1
ms.openlocfilehash: 47c1de362108096f26c0420d6135a9d9028a0302
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145080"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="e22bb-103">Verbeteringen in desired state Configuration (DSC) in WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="e22bb-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="e22bb-104">Verbeteringen DSC-klasse resource</span><span class="sxs-lookup"><span data-stu-id="e22bb-104">DSC class resource improvements</span></span>

<span data-ttu-id="e22bb-105">In WMF 5,1 hebben we de volgende bekende problemen opgelost:</span><span class="sxs-lookup"><span data-stu-id="e22bb-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="e22bb-106">Get-DscConfiguration kan lege waarden (null) of fouten retour neren als een complex/hash-tabel type wordt geretourneerd door de functie Get () van een DSC-resource op basis van een klasse.</span><span class="sxs-lookup"><span data-stu-id="e22bb-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="e22bb-107">Get-DscConfiguration retourneert een fout als de RunAs-referentie wordt gebruikt in de DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="e22bb-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="e22bb-108">Op klassen gebaseerde resource kan niet worden gebruikt in een samengestelde configuratie.</span><span class="sxs-lookup"><span data-stu-id="e22bb-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="e22bb-109">Start-DscConfiguration loopt vast als op de klasse gebaseerde resource een eigenschap van een eigen type heeft.</span><span class="sxs-lookup"><span data-stu-id="e22bb-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="e22bb-110">Bron op basis van een klasse kan niet worden gebruikt als exclusieve resource.</span><span class="sxs-lookup"><span data-stu-id="e22bb-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="e22bb-111">Verbeteringen in DSC-bron fout opsporing</span><span class="sxs-lookup"><span data-stu-id="e22bb-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="e22bb-112">In WMF 5,0 is het Power Shell-fout opsporingsprogramma niet gestopt bij de op klassen gebaseerde resource methode (Get/set/test) direct.</span><span class="sxs-lookup"><span data-stu-id="e22bb-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="e22bb-113">In WMF 5,1 stopt het fout opsporingsprogramma bij de op klassen gebaseerde resource methode op dezelfde manier als voor op MOF gebaseerde bronnen methoden.</span><span class="sxs-lookup"><span data-stu-id="e22bb-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="e22bb-114">De DSC pull-client ondersteunt TLS 1,1 en TLS 1,2</span><span class="sxs-lookup"><span data-stu-id="e22bb-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="e22bb-115">Voorheen werd de DSC pull-client alleen ondersteund SSL 3.0 en TLS 1.0 via HTTPS-verbindingen.</span><span class="sxs-lookup"><span data-stu-id="e22bb-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="e22bb-116">Wanneer er meer beveiligde protocollen worden gebruikt, werkt de pull-client niet meer.</span><span class="sxs-lookup"><span data-stu-id="e22bb-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="e22bb-117">De DSC pull-client in WMF 5,1 biedt geen ondersteuning meer voor SSL 3,0 en voegt ondersteuning toe voor de meer beveiligde TLS 1,1-en TLS 1,2-protocollen.</span><span class="sxs-lookup"><span data-stu-id="e22bb-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="e22bb-118">Verbeterde registratie van de pull-server</span><span class="sxs-lookup"><span data-stu-id="e22bb-118">Improved pull server registration</span></span>

<span data-ttu-id="e22bb-119">In eerdere versies van WMF zouden gelijktijdige registraties/rapporten naar een DSC-pull-server tijdens het gebruik van de ESENT-data base ertoe leiden dat de LCM niet kan worden geregistreerd en/of gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="e22bb-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="e22bb-120">In dergelijke gevallen heeft de gebeurtenis logboeken op de pull-server de fout ' exemplaar naam al in gebruik '.</span><span class="sxs-lookup"><span data-stu-id="e22bb-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="e22bb-121">Dit wordt veroorzaakt door een onjuist patroon dat wordt gebruikt voor toegang tot de ESENT-data base in een scenario met meerdere threads.</span><span class="sxs-lookup"><span data-stu-id="e22bb-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="e22bb-122">Dit probleem is opgelost in WMF 5,1.</span><span class="sxs-lookup"><span data-stu-id="e22bb-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="e22bb-123">Gelijktijdige registraties of rapporten (met behulp van ESENT-data base) werken prima in WMF 5,1.</span><span class="sxs-lookup"><span data-stu-id="e22bb-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="e22bb-124">Dit probleem is alleen van toepassing op de ESENT-data base en is niet van toepassing op de OLEDB-data base.</span><span class="sxs-lookup"><span data-stu-id="e22bb-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="e22bb-125">Circulair data base-exemplaar van het logboek inschakelen.</span><span class="sxs-lookup"><span data-stu-id="e22bb-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="e22bb-126">In de eariler-versie van DSC-PullServer werden de logboek bestanden van de ESENT-data base gevuld met de schijf ruimte van de PullServer becouse het data base-exemplaar werd gemaakt zonder circulaire logboek registratie.</span><span class="sxs-lookup"><span data-stu-id="e22bb-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="e22bb-127">In deze release hebt u de mogelijkheid om de circulaire logboek registratie van het exemplaar te beheren met de web. config van de pullserver.</span><span class="sxs-lookup"><span data-stu-id="e22bb-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="e22bb-128">CircularLogging is standaard ingesteld op TRUE.</span><span class="sxs-lookup"><span data-stu-id="e22bb-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="e22bb-129">WOW64-ondersteuning voor configuratie sleutelwoord</span><span class="sxs-lookup"><span data-stu-id="e22bb-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="e22bb-130">Het `Configuration` sleutel woord wordt nu ondersteund in WOW64 op een 64-bits computer.</span><span class="sxs-lookup"><span data-stu-id="e22bb-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="e22bb-131">Dit betekent dat een DSC-configuratie kan worden gedefinieerd en gecompileerd binnen een 32-bits proces, zoals Windows PowerShell ISE (x86) dat wordt uitgevoerd op een 64-bits computer.</span><span class="sxs-lookup"><span data-stu-id="e22bb-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="e22bb-132">Naamgevings Conventie voor gedeeltelijke configuratie pullen</span><span class="sxs-lookup"><span data-stu-id="e22bb-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="e22bb-133">In de vorige versie is de naam Conventie voor een gedeeltelijke configuratie het MOF-bestand in de pull-Server/service moet overeenkomen met de gedeeltelijke configuratie naam opgegeven in de lokale Configuration Manager-instellingen die op zijn beurt moeten overeenkomen met de de configuratie naam in het MOF-bestand is inge sloten.</span><span class="sxs-lookup"><span data-stu-id="e22bb-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="e22bb-134">Bekijk de onderstaande moment opnamen:</span><span class="sxs-lookup"><span data-stu-id="e22bb-134">See the snapshots below:</span></span>

- <span data-ttu-id="e22bb-135">Lokale configuratie-instellingen waarmee een gedeeltelijke configuratie wordt gedefinieerd die een knoop punt mag ontvangen.</span><span class="sxs-lookup"><span data-stu-id="e22bb-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![Voor beeld van een automatische configuratie](../images/DSC-improvements/MetaConfigPartialOne.png)

- <span data-ttu-id="e22bb-137">Voor beeld van gedeeltelijke configuratie definitie</span><span class="sxs-lookup"><span data-stu-id="e22bb-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="e22bb-138">Configuratiepad is inge sloten in het gegenereerde MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="e22bb-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![Voor beeld van gegenereerd MOF-bestand](../images/DSC-improvements/PartialGeneratedMof.png)

- <span data-ttu-id="e22bb-140">Bestands naam in de opslag plaats voor pull-configuratie</span><span class="sxs-lookup"><span data-stu-id="e22bb-140">FileName in the pull configuration repository</span></span>

  ![Bestands naam in configuratie opslagplaats](../images/DSC-improvements/PartialInConfigRepository.png)

  <span data-ttu-id="e22bb-142">Azure Automation Service naam heeft MOF-bestanden `<ConfigurationName>.<NodeName>.mof`gegenereerd als.</span><span class="sxs-lookup"><span data-stu-id="e22bb-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="e22bb-143">De onderstaande configuratie compileert daarom met PartialOne. localhost. mof.</span><span class="sxs-lookup"><span data-stu-id="e22bb-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="e22bb-144">Hierdoor is het onmogelijk om een van uw gedeeltelijke configuratie van Azure Automation-Service te verzamelen.</span><span class="sxs-lookup"><span data-stu-id="e22bb-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="e22bb-145">In WMF 5,1 kan een gedeeltelijke configuratie in de pull-Server/-service worden genoemd `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="e22bb-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="e22bb-146">Bovendien, als een machine een configuratie van een pull-Server/-service haalt, kan het configuratie bestand in de opslag plaats van de pull-server een wille keurige bestands naam hebben.</span><span class="sxs-lookup"><span data-stu-id="e22bb-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="e22bb-147">Deze naam flexibiliteit biedt u de mogelijkheid om uw knoop punten gedeeltelijk te beheren door Azure Automation Service, waarbij bepaalde configuraties voor uw knoop punt afkomstig zijn van Azure Automation DSC en met een gedeeltelijke configuratie die u lokaal beheert.</span><span class="sxs-lookup"><span data-stu-id="e22bb-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="e22bb-148">De onderstaande configuratie stelt een knoop punt in dat zowel lokaal als door Azure Automation Service moet worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="e22bb-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="e22bb-149">PsDscRunAsCredential gebruiken met DSC-samengestelde resources</span><span class="sxs-lookup"><span data-stu-id="e22bb-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="e22bb-150">Er is ondersteuning toegevoegd voor het gebruik van [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) met DSC- [samengestelde](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span><span class="sxs-lookup"><span data-stu-id="e22bb-150">We have added support for using [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="e22bb-151">U kunt nu een waarde opgeven voor **PsDscRunAsCredential** bij het gebruik van samengestelde resources binnen configuraties.</span><span class="sxs-lookup"><span data-stu-id="e22bb-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="e22bb-152">Als u deze opgeeft, worden alle resources in een samengestelde resource uitgevoerd als een runas-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e22bb-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="e22bb-153">Als een samengestelde resource een andere samengestelde resource aanroept, worden alle resources ook uitgevoerd als runas-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e22bb-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="e22bb-154">Runas-referenties worden door gegeven aan elk niveau van de samengestelde resource hiërarchie.</span><span class="sxs-lookup"><span data-stu-id="e22bb-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="e22bb-155">Als een resource in een samengestelde resource een eigen waarde voor **PsDscRunAsCredential**opgeeft, wordt er tijdens het compileren van de configuratie een samenvoeg fout veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="e22bb-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="e22bb-156">In dit voor beeld ziet u het gebruik van de [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) -samengestelde resource die is opgenomen in de PSDesiredStateConfiguration-module.</span><span class="sxs-lookup"><span data-stu-id="e22bb-156">This example shows usage with the [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="e22bb-157">Identieke dubbele resources in een configuratie toestaan</span><span class="sxs-lookup"><span data-stu-id="e22bb-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="e22bb-158">DSC staat geen conflicterende resource definities binnen een configuratie toe of verwerkt deze.</span><span class="sxs-lookup"><span data-stu-id="e22bb-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="e22bb-159">In plaats van het conflict op te lossen, mislukt dit gewoon.</span><span class="sxs-lookup"><span data-stu-id="e22bb-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="e22bb-160">Naarmate het opnieuw gebruiken van de configuratie wordt gebruikt door samengestelde resources, enzovoort, worden er vaker conflicten optreden.</span><span class="sxs-lookup"><span data-stu-id="e22bb-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="e22bb-161">Wanneer conflicterende resource definities identiek zijn, moet DSC slim zijn en dit toestaan.</span><span class="sxs-lookup"><span data-stu-id="e22bb-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="e22bb-162">In deze release ondersteunen we meerdere bron instanties met identieke definities:</span><span class="sxs-lookup"><span data-stu-id="e22bb-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

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

<span data-ttu-id="e22bb-163">In eerdere releases zou het resultaat een mislukte compilatie zijn vanwege een conflict tussen de FE_IIS-WindowsFeature-en WindowsFeature Worker_IIS-instanties om te controleren of de functie web-server is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e22bb-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="e22bb-164">U ziet dat *alle* eigenschappen die worden geconfigureerd, identiek zijn in deze twee configuraties.</span><span class="sxs-lookup"><span data-stu-id="e22bb-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="e22bb-165">Omdat *alle* eigenschappen in deze twee resources identiek zijn, resulteert dit in een succes volle compilatie.</span><span class="sxs-lookup"><span data-stu-id="e22bb-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="e22bb-166">Als een van de eigenschappen verschilt tussen de twee resources, worden ze niet beschouwd als identiek en mislukt het compileren.</span><span class="sxs-lookup"><span data-stu-id="e22bb-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="e22bb-167">Validatie van de DSC-module en configuratie-ondertekening</span><span class="sxs-lookup"><span data-stu-id="e22bb-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="e22bb-168">In DSC worden configuraties en modules gedistribueerd naar beheerde computers vanaf de pull-server.</span><span class="sxs-lookup"><span data-stu-id="e22bb-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="e22bb-169">Als de pull-server is aangetast, kan een aanvaller de configuraties en modules op de pull-server mogelijk wijzigen en deze naar alle beheerde knoop punten distribueren.</span><span class="sxs-lookup"><span data-stu-id="e22bb-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="e22bb-170">In WMF 5,1 ondersteunt DSC het valideren van digitale hand tekeningen in Catalog en configuratie (. MOF-bestanden).</span><span class="sxs-lookup"><span data-stu-id="e22bb-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="e22bb-171">Deze functie voor komt dat knoop punten configuraties of module bestanden uitvoeren die niet zijn ondertekend door een vertrouwde ondertekenaar of waarvan is geknoeid nadat deze zijn ondertekend door een vertrouwde ondertekenaar.</span><span class="sxs-lookup"><span data-stu-id="e22bb-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="e22bb-172">Configuratie en module ondertekenen</span><span class="sxs-lookup"><span data-stu-id="e22bb-172">How to sign configuration and module</span></span>

- <span data-ttu-id="e22bb-173">Configuratie bestanden (. Mof's): De bestaande Power shell [-cmdlet Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) wordt uitgebreid ter ondersteuning van het ondertekenen van MOF-bestanden.</span><span class="sxs-lookup"><span data-stu-id="e22bb-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="e22bb-174">Modules Het ondertekenen van modules wordt uitgevoerd door de bijbehorende module catalogus te ondertekenen met behulp van de volgende stappen:</span><span class="sxs-lookup"><span data-stu-id="e22bb-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="e22bb-175">Een catalogus bestand maken: Een catalogus bestand bevat een verzameling cryptografische hashes of vinger afdrukken.</span><span class="sxs-lookup"><span data-stu-id="e22bb-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="e22bb-176">Elke vinger afdruk komt overeen met een bestand dat is opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="e22bb-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="e22bb-177">De nieuwe cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog)is toegevoegd om gebruikers in staat te stellen een catalogus bestand voor hun module te maken.</span><span class="sxs-lookup"><span data-stu-id="e22bb-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="e22bb-178">Het catalogus bestand ondertekenen: Gebruik [set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) om het catalogus bestand te ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="e22bb-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="e22bb-179">Plaats het catalogus bestand in de map module.</span><span class="sxs-lookup"><span data-stu-id="e22bb-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="e22bb-180">Per Conventie moet het module catalogus bestand onder de module map met dezelfde naam als de module worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="e22bb-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="e22bb-181">LocalConfigurationManager-instellingen voor het inschakelen van validaties van ondertekening</span><span class="sxs-lookup"><span data-stu-id="e22bb-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="e22bb-182">Pull</span><span class="sxs-lookup"><span data-stu-id="e22bb-182">Pull</span></span>

<span data-ttu-id="e22bb-183">De LocalConfigurationManager van een knoop punt voert de validatie van modules en configuraties op basis van de huidige instellingen uit.</span><span class="sxs-lookup"><span data-stu-id="e22bb-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="e22bb-184">Validatie van hand tekeningen is standaard uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="e22bb-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="e22bb-185">Handtekening validatie kan worden ingeschakeld door het blok ' SignatureValidation ' toe te voegen aan de meta-configuratie definitie van het knoop punt, zoals hieronder wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="e22bb-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="e22bb-186">Bij het instellen van de hierboven genoemde configuratie op een knoop punt wordt handtekening validatie op gedownloade configuraties en modules ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="e22bb-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="e22bb-187">De lokale Configuration Manager voert de volgende stappen uit om de digitale hand tekeningen te controleren.</span><span class="sxs-lookup"><span data-stu-id="e22bb-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="e22bb-188">Controleer de hand tekening op een configuratie bestand (. MOF) is geldig met de `Get-AuthenticodeSignature` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e22bb-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="e22bb-189">Controleer of de certificerings instantie die de ondertekenaar heeft geautoriseerd, vertrouwd is.</span><span class="sxs-lookup"><span data-stu-id="e22bb-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="e22bb-190">Down load module/Resource-afhankelijkheden van de configuratie naar een tijdelijke locatie.</span><span class="sxs-lookup"><span data-stu-id="e22bb-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="e22bb-191">Controleer de hand tekening van de catalogus die is opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="e22bb-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="e22bb-192">Zoek een `<moduleName>.cat` bestand en controleer de hand tekening `Get-AuthenticodeSignature`met behulp van.</span><span class="sxs-lookup"><span data-stu-id="e22bb-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="e22bb-193">Controleer of de certificerings instantie die de ondertekenaar heeft geverifieerd, vertrouwd is.</span><span class="sxs-lookup"><span data-stu-id="e22bb-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="e22bb-194">Controleer of de inhoud van de modules niet is geknoeid met de nieuwe `Test-FileCatalog`cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e22bb-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="e22bb-195">`Install-Module`Aan`$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="e22bb-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="e22bb-196">Proces configuratie</span><span class="sxs-lookup"><span data-stu-id="e22bb-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="e22bb-197">Handtekening validatie voor module-Catalog en configuratie wordt alleen uitgevoerd wanneer de configuratie voor de eerste keer wordt toegepast op het systeem of wanneer de module wordt gedownload en geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e22bb-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="e22bb-198">Met consistentie runs wordt de hand tekening van huidige. MOF of de bijbehorende module-afhankelijkheden niet gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="e22bb-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="e22bb-199">Als de verificatie is mislukt in elk stadium, bijvoorbeeld als de configuratie die is opgehaald van de pull-server niet is ondertekend, wordt de verwerking van de configuratie beëindigd met de fout die hieronder wordt weer gegeven en worden alle tijdelijke bestanden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e22bb-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Configuratie van voorbeeld fout uitvoer](../images/DSC-improvements/PullUnsignedConfigFail.png)

<span data-ttu-id="e22bb-201">Op dezelfde manier wordt het ophalen van een module waarvan de catalogus niet is ondertekend met de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="e22bb-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Uitvoer module voor voorbeeld fout](../images/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="e22bb-203">Push</span><span class="sxs-lookup"><span data-stu-id="e22bb-203">Push</span></span>

<span data-ttu-id="e22bb-204">Een configuratie die wordt geleverd met behulp van push kan worden geknoeid met de bron voordat deze wordt afgeleverd bij het knoop punt.</span><span class="sxs-lookup"><span data-stu-id="e22bb-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="e22bb-205">De lokale Configuration Manager voert vergelijk bare handtekening validatie stappen uit voor gepushte of gepubliceerde configuratie (s).</span><span class="sxs-lookup"><span data-stu-id="e22bb-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="e22bb-206">Hieronder vindt u een volledig voor beeld van handtekening validatie voor push.</span><span class="sxs-lookup"><span data-stu-id="e22bb-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="e22bb-207">Schakel handtekening validatie in op het knoop punt.</span><span class="sxs-lookup"><span data-stu-id="e22bb-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="e22bb-208">Maak een voor beeld van een configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="e22bb-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="e22bb-209">Probeer het niet-ondertekende configuratie bestand naar het knoop punt te pushen.</span><span class="sxs-lookup"><span data-stu-id="e22bb-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/DSC-improvements/PushUnsignedMof.png)

- <span data-ttu-id="e22bb-211">Onderteken het configuratie bestand met het certificaat voor ondertekening van programma code.</span><span class="sxs-lookup"><span data-stu-id="e22bb-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/DSC-improvements/SignMofFile.png)

- <span data-ttu-id="e22bb-213">Probeer het ondertekende MOF-bestand te pushen.</span><span class="sxs-lookup"><span data-stu-id="e22bb-213">Try pushing the signed MOF file.</span></span>

  ![SignMofFile](../images/DSC-improvements/PushSignedMof.png)
