---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: DSC-verbeteringen in WMF 5.1
ms.openlocfilehash: e7f20bfa865777aeac8f083959782317cfdf6cde
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856229"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="46da8-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="46da8-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="46da8-104">DSC-klasse resource verbeteringen</span><span class="sxs-lookup"><span data-stu-id="46da8-104">DSC class resource improvements</span></span>

<span data-ttu-id="46da8-105">In WMF 5.1, hebben we de volgende bekende problemen opgelost:</span><span class="sxs-lookup"><span data-stu-id="46da8-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="46da8-106">Get-DscConfiguration mogelijk lege waarden (null) of fouten als resultaat als een type complex/hash-tabel wordt geretourneerd door de functie Get() van een klasse op basis van DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="46da8-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="46da8-107">Get-DscConfiguration retourneert fout als de RunAs-referentie in DSC-configuratie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="46da8-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="46da8-108">Op basis van een klasse resource kan niet worden gebruikt in een samengestelde configuratie.</span><span class="sxs-lookup"><span data-stu-id="46da8-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="46da8-109">Start-DscConfiguration loopt vast als bron op basis van een klasse een eigenschap van een eigen type heeft.</span><span class="sxs-lookup"><span data-stu-id="46da8-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="46da8-110">Op basis van een klasse resource kan niet worden gebruikt als een exclusieve resource.</span><span class="sxs-lookup"><span data-stu-id="46da8-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="46da8-111">Verbeteringen in Foutopsporing voor DSC-resource</span><span class="sxs-lookup"><span data-stu-id="46da8-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="46da8-112">In WMF 5.0, is de PowerShell-foutopsporing niet gestopt op de resource op basis van een klasse, methode (Get/Set/Test) rechtstreeks.</span><span class="sxs-lookup"><span data-stu-id="46da8-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="46da8-113">In WMF 5.1 stopt het foutopsporingsprogramma op dezelfde manier als voor de resources op basis van MOF-methoden op de resource op basis van een klasse-methode.</span><span class="sxs-lookup"><span data-stu-id="46da8-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="46da8-114">DSC-pull-client biedt ondersteuning voor TLS 1.1 en TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="46da8-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="46da8-115">Voorheen was ondersteund de DSC-pull-client alleen SSL3.0 en TLS1.0 via HTTPS-verbindingen.</span><span class="sxs-lookup"><span data-stu-id="46da8-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="46da8-116">Wanneer geforceerde veiliger protocollen gebruiken, dan werkt de pull-client niet.</span><span class="sxs-lookup"><span data-stu-id="46da8-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="46da8-117">In WMF 5.1, de DSC pull-client niet langer ondersteuning biedt voor SSL 3.0 en voegt ondersteuning toe voor de beter beveiligde TLS 1.1 en TLS 1.2-protocollen.</span><span class="sxs-lookup"><span data-stu-id="46da8-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="46da8-118">Verbeterde pull-server registreren</span><span class="sxs-lookup"><span data-stu-id="46da8-118">Improved pull server registration</span></span>

<span data-ttu-id="46da8-119">In eerdere versies van WMF zou gelijktijdige registraties/reporting aanvragen voor een DSC-pull-server tijdens het gebruik van de database ESENT leiden tot LCM niet te registreren en/of rapport.</span><span class="sxs-lookup"><span data-stu-id="46da8-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="46da8-120">In dergelijke gevallen de gebeurtenislogboeken op de pull-server heeft de fout 'Exemplaarnaam al in gebruik'.</span><span class="sxs-lookup"><span data-stu-id="46da8-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="46da8-121">Dit is veroorzaakt door een onjuiste patroon wordt gebruikt voor toegang tot de ESENT-database in een scenario met meerdere threads.</span><span class="sxs-lookup"><span data-stu-id="46da8-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="46da8-122">In WMF 5.1, heeft dit probleem is opgelost.</span><span class="sxs-lookup"><span data-stu-id="46da8-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="46da8-123">Gelijktijdige registraties of reporting (met inschakeling van ESENT-database) werkt prima in WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="46da8-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="46da8-124">Dit probleem geldt alleen voor de database ESENT en geldt niet voor de OLE DB-database.</span><span class="sxs-lookup"><span data-stu-id="46da8-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="46da8-125">Permanente logboekbestand op ESENT-database-exemplaar inschakelen</span><span class="sxs-lookup"><span data-stu-id="46da8-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="46da8-126">Eariler versie van DSC-PullServer, zijn de logboekbestanden van de ESENT-database de schijfruimte van de pullserver becouse die de database-instantie werd gemaakt zonder circulair vastleggen terechtkomen.</span><span class="sxs-lookup"><span data-stu-id="46da8-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="46da8-127">In deze release hebt u de optie voor het beheren van het gedrag circulair vastleggen van het exemplaar met behulp van het bestand web.config van de pullserver.</span><span class="sxs-lookup"><span data-stu-id="46da8-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="46da8-128">CircularLogging is standaard ingesteld op TRUE.</span><span class="sxs-lookup"><span data-stu-id="46da8-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="46da8-129">WOW64-ondersteuning voor Configuratiesleutelwoord</span><span class="sxs-lookup"><span data-stu-id="46da8-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="46da8-130">De `Configuration` trefwoord wordt nu ondersteund in WOW64 op een 64-bits computer.</span><span class="sxs-lookup"><span data-stu-id="46da8-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="46da8-131">Dit betekent dat een DSC-configuratie kan worden gedefinieerd en gecompileerd in een 32-bits proces, zoals Windows PowerShell ISE (x 86) wordt uitgevoerd op een 64-bits computer.</span><span class="sxs-lookup"><span data-stu-id="46da8-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="46da8-132">De naamconventie gedeeltelijke configuratie ophalen</span><span class="sxs-lookup"><span data-stu-id="46da8-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="46da8-133">In de vorige versie, de naamconventie voor een gedeeltelijke configuratie is dat de naam van de MOF-bestand in de pull-server/service moet overeenkomen met de naam van de gedeeltelijke configuratie opgegeven in de lokale configuration manager-instellingen die op zijn beurt moeten overeenkomen met de naam van de configuratie is ingesloten in het MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="46da8-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="46da8-134">Zie de onderstaande momentopnamen:</span><span class="sxs-lookup"><span data-stu-id="46da8-134">See the snapshots below:</span></span>

- <span data-ttu-id="46da8-135">Lokale configuratie-instellingen die u definieert een gedeeltelijke configuratie dat is toegestaan voor het ontvangen van een knooppunt.</span><span class="sxs-lookup"><span data-stu-id="46da8-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![Voorbeeld metaconfiguration](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="46da8-137">De definitie van de voorbeeld-gedeeltelijke configuratie</span><span class="sxs-lookup"><span data-stu-id="46da8-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="46da8-138">'ConfigurationName' ingesloten in het gegenereerde MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="46da8-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![Voorbeeld van gegenereerde mof-bestand](../images/PartialGeneratedMof.png)

- <span data-ttu-id="46da8-140">Bestandsnaam in de opslagplaats van de pull-configuratie</span><span class="sxs-lookup"><span data-stu-id="46da8-140">FileName in the pull configuration repository</span></span>

  ![Bestandsnaam in de opslagplaats van configuratie](../images/PartialInConfigRepository.png)

  <span data-ttu-id="46da8-142">Azure Automation-servicenaam gegenereerd MOF-bestanden als `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="46da8-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="46da8-143">Dus de onderstaande configuratie worden gecompileerd naar PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="46da8-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="46da8-144">Dit werd het onmogelijk voor pull een van uw gedeeltelijke configuratie in Azure Automation-service.</span><span class="sxs-lookup"><span data-stu-id="46da8-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="46da8-145">In WMF 5.1, een gedeeltelijke configuratie in de pull-server/service kan worden met de naam als `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="46da8-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="46da8-146">Als een virtuele machine is een eenmalige configuratie van een pull binnenhalen kunt serverservice vervolgens het configuratiebestand op de opslagplaats van de pull-server-configuratie bovendien een bestandsnaam hebben.</span><span class="sxs-lookup"><span data-stu-id="46da8-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="46da8-147">Deze naamgevingsconventie flexibiliteit kunt u uw knooppunten gedeeltelijk beheren met Azure Automation-service, waar een configuratie voor het knooppunt is binnenkort in Azure Automation DSC en waarbij een gedeeltelijke configuratie die u lokaal beheren.</span><span class="sxs-lookup"><span data-stu-id="46da8-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="46da8-148">De metaconfiguration hieronder ingesteld op een knooppunt om te worden beheerd zowel lokaal als door Azure Automation-service.</span><span class="sxs-lookup"><span data-stu-id="46da8-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="46da8-149">Met behulp van PsDscRunAsCredential met samengestelde DSC-resources</span><span class="sxs-lookup"><span data-stu-id="46da8-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="46da8-150">Ondersteuning voor het gebruik van toegevoegd [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) met DSC [samengestelde](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span><span class="sxs-lookup"><span data-stu-id="46da8-150">We have added support for using [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="46da8-151">U kunt nu een waarde opgeven voor **PsDscRunAsCredential** bij het gebruik van samengestelde resources binnen configuraties.</span><span class="sxs-lookup"><span data-stu-id="46da8-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="46da8-152">Wanneer is opgegeven, wordt alle resources binnen een samengestelde resource uitgevoerd als een RunAs-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="46da8-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="46da8-153">Als een samengestelde resource aanroept die een andere samengestelde resource, worden alle resources die ook uitgevoerd als RunAs-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="46da8-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="46da8-154">Run as-referenties worden doorgegeven aan een willekeurig niveau in de hiërarchie samengestelde resource.</span><span class="sxs-lookup"><span data-stu-id="46da8-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="46da8-155">Als een resource binnen een samengestelde resource Hiermee geeft u een eigen waarde voor **PsDscRunAsCredential**, een merge-fout tijdens de compilatie van de configuratie van resultaten.</span><span class="sxs-lookup"><span data-stu-id="46da8-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="46da8-156">Dit voorbeeld laat zien voor gebruik met de [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) samengestelde resource opgenomen in de module PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="46da8-156">This example shows usage with the [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="46da8-157">Toestaan van identieke dubbele Resources in een configuratie</span><span class="sxs-lookup"><span data-stu-id="46da8-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="46da8-158">DSC niet toestaan of conflicterende resourcedefinities binnen een configuratie worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="46da8-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="46da8-159">In plaats van het conflict op te lossen, gewoon is mislukt.</span><span class="sxs-lookup"><span data-stu-id="46da8-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="46da8-160">Als het hergebruik van de configuratie wordt meer samengestelde resources gebruikt, wordt vaker enzovoort conflicten optreden.</span><span class="sxs-lookup"><span data-stu-id="46da8-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="46da8-161">Wanneer er conflicterende resourcedefinities identiek zijn, moet de DSC Wees slim en dit toestaan.</span><span class="sxs-lookup"><span data-stu-id="46da8-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="46da8-162">Met deze versie wordt ondersteund met meerdere exemplaren van resources met identieke definities:</span><span class="sxs-lookup"><span data-stu-id="46da8-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

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

<span data-ttu-id="46da8-163">In eerdere versies is het resultaat een compilatie is mislukt vanwege een conflict tussen de WindowsFeature FE_IIS en WindowsFeature Worker_IIS exemplaren probeert om te controleren of de rol 'Webserver' is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="46da8-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="46da8-164">U ziet dat *alle* zijn identiek in deze twee configuraties van de eigenschappen die worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="46da8-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="46da8-165">Aangezien *alle* van de eigenschappen in deze twee resources identiek zijn, resulteert dit in een geslaagde compilatie nu.</span><span class="sxs-lookup"><span data-stu-id="46da8-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="46da8-166">Als een van de eigenschappen van de verschillen tussen de twee resources, ze komen niet in aanmerking identiek zijn en mislukt de compilatie.</span><span class="sxs-lookup"><span data-stu-id="46da8-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="46da8-167">DSC-module en configuratie van validaties ondertekenen</span><span class="sxs-lookup"><span data-stu-id="46da8-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="46da8-168">DSC, worden configuraties en -modules gedistribueerd naar beheerde computers van de pull-server.</span><span class="sxs-lookup"><span data-stu-id="46da8-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="46da8-169">Als de pull-server is geknoeid, kunt mogelijk een aanvaller de configuraties en -modules op de pull-server wijzigen en deze gedistribueerd naar alle beheerde knooppunten.</span><span class="sxs-lookup"><span data-stu-id="46da8-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="46da8-170">In WMF 5.1, DSC biedt ondersteuning voor de digitale handtekeningen van catalogus en de configuratie valideren (. MOF)-bestanden.</span><span class="sxs-lookup"><span data-stu-id="46da8-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="46da8-171">Deze functie wordt voorkomen dat knooppunten configuraties of module bestanden die niet zijn ondertekend door een vertrouwde ondertekenaar of waarmee is geknoeid nadat ze zijn ondertekend door vertrouwde ondertekenaar wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="46da8-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="46da8-172">Het ondertekenen van de configuratie en -module</span><span class="sxs-lookup"><span data-stu-id="46da8-172">How to sign configuration and module</span></span>

- <span data-ttu-id="46da8-173">Configuratiebestanden (. MOF-bestanden): De bestaande PowerShell-cmdlet [Set AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) wordt uitgebreid met ondersteuning voor ondertekening van de MOF-bestanden.</span><span class="sxs-lookup"><span data-stu-id="46da8-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="46da8-174">Modules: Ondertekening van modules wordt uitgevoerd door het ondertekenen van de bijbehorende module-catalogus met behulp van de volgende stappen uit:</span><span class="sxs-lookup"><span data-stu-id="46da8-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="46da8-175">Maak een catalogusbestand: Een catalogusbestand bevat een verzameling van cryptografische hashes of de vingerafdrukken.</span><span class="sxs-lookup"><span data-stu-id="46da8-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="46da8-176">Elke vingerafdruk komt overeen met een bestand dat is opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="46da8-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="46da8-177">De nieuwe cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), zodat gebruikers kunnen maken van een catalogusbestand voor de module is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="46da8-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="46da8-178">Meld u aan het catalogusbestand: Gebruik [Set AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) om de catalogusbestand te ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="46da8-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="46da8-179">Plaats het catalogusbestand in de modulemap.</span><span class="sxs-lookup"><span data-stu-id="46da8-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="46da8-180">Volgens de conventies wordt moet module catalogusbestand worden geplaatst in de modulemap met dezelfde naam als de module.</span><span class="sxs-lookup"><span data-stu-id="46da8-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="46da8-181">Instellingen voor LocalConfigurationManager ondertekenen validaties inschakelen</span><span class="sxs-lookup"><span data-stu-id="46da8-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="46da8-182">Pull</span><span class="sxs-lookup"><span data-stu-id="46da8-182">Pull</span></span>

<span data-ttu-id="46da8-183">De LocalConfigurationManager van een knooppunt voert ondertekenen validatie van modules en configuraties op basis van de huidige instellingen.</span><span class="sxs-lookup"><span data-stu-id="46da8-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="46da8-184">Handtekeningvalidatie is standaard uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="46da8-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="46da8-185">Handtekeningvalidatie kan worden ingeschakeld door het blok 'SignatureValidation' toe te voegen aan de definitie meta-configuratie van het knooppunt zoals hieronder:</span><span class="sxs-lookup"><span data-stu-id="46da8-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="46da8-186">De bovenstaande metaconfiguration instellen op een knooppunt, kunt handtekeningvalidatie op gedownloade configuraties en -modules.</span><span class="sxs-lookup"><span data-stu-id="46da8-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="46da8-187">De Local Configuration Manager voert de volgende stappen uit om te controleren of de digitale handtekeningen.</span><span class="sxs-lookup"><span data-stu-id="46da8-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="46da8-188">Controleer of de handtekening van een configuratiebestand (. MOF) is geldig met behulp van de `Get-AuthenticodeSignature` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46da8-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="46da8-189">Controleer of de certificeringsinstantie die de ondertekenaar gemachtigd wordt vertrouwd.</span><span class="sxs-lookup"><span data-stu-id="46da8-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="46da8-190">Afhankelijkheden van de configuratie van de module/resource naar een tijdelijke locatie downloaden.</span><span class="sxs-lookup"><span data-stu-id="46da8-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="46da8-191">Controleer of de handtekening van de catalogus die is opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="46da8-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="46da8-192">Zoek een `<moduleName>.cat` bestands- en controleer of de handtekening met behulp van `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="46da8-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="46da8-193">Controleer of de certificeringsinstantie (CA) die de ondertekenaar geverifieerd wordt vertrouwd.</span><span class="sxs-lookup"><span data-stu-id="46da8-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="46da8-194">Controleer of de inhoud van de modules niet is geknoeid met de nieuwe cmdlet `Test-FileCatalog`.</span><span class="sxs-lookup"><span data-stu-id="46da8-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="46da8-195">`Install-Module` Aan `$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="46da8-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="46da8-196">Procesconfiguratie van</span><span class="sxs-lookup"><span data-stu-id="46da8-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="46da8-197">Handtekeningvalidatie van module-catalogus en de configuratie wordt alleen uitgevoerd wanneer de configuratie wordt toegepast op het systeem voor de eerste keer of wanneer de module wordt gedownload en geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="46da8-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="46da8-198">Consistentiecontrole wordt uitgevoerd, wordt de handtekening van Current.mof of de module-afhankelijkheden niet gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="46da8-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="46da8-199">Als verificatie is mislukt tijdens elke fase, bijvoorbeeld, als de configuratie die is opgehaald uit de pull-server is niet ondertekend, klikt u vervolgens verwerking van de configuratie wordt beëindigd met de fout die hieronder wordt weergegeven en alle tijdelijke bestanden worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="46da8-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Uitvoer van de voorbeeldconfiguratie-fout](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="46da8-201">Binnenhalen van een module met-catalogus niet is ondertekend op dezelfde manier, resulteert dit in de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="46da8-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Uitvoer van de voorbeeldmodule-fout](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="46da8-203">Push</span><span class="sxs-lookup"><span data-stu-id="46da8-203">Push</span></span>

<span data-ttu-id="46da8-204">Een configuratie die is geleverd met behulp van push kan worden geknoeid bij de bron voordat deze naar het knooppunt geleverd.</span><span class="sxs-lookup"><span data-stu-id="46da8-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="46da8-205">De Local Configuration Manager voert gelijksoortige stappen van de handtekening validatie voor gepushte of gepubliceerd configuratie (s).</span><span class="sxs-lookup"><span data-stu-id="46da8-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="46da8-206">Hieronder volgt een compleet voorbeeld van validatie van de handtekening voor pushmeldingen.</span><span class="sxs-lookup"><span data-stu-id="46da8-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="46da8-207">Handtekeningvalidatie op het knooppunt inschakelen.</span><span class="sxs-lookup"><span data-stu-id="46da8-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="46da8-208">Een voorbeeld-configuratiebestand maken.</span><span class="sxs-lookup"><span data-stu-id="46da8-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="46da8-209">Probeer de niet-ondertekende configuratiebestand pushen naar het knooppunt.</span><span class="sxs-lookup"><span data-stu-id="46da8-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="46da8-211">Meld u aan het configuratiebestand met behulp van certificaat voor ondertekening van programmacode.</span><span class="sxs-lookup"><span data-stu-id="46da8-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="46da8-213">Probeer het pushen van de ondertekende MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="46da8-213">Try pushing the signed MOF file.</span></span>

  ![SignMofFile](../images/PushSignedMof.png)
