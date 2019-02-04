---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: DSC-verbeteringen in WMF 5.1
ms.openlocfilehash: 92f82d62550e105a187fd7c0c58b49367c646a7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683798"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="94bdb-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="94bdb-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="94bdb-104">DSC-klasse resource verbeteringen</span><span class="sxs-lookup"><span data-stu-id="94bdb-104">DSC class resource improvements</span></span>

<span data-ttu-id="94bdb-105">In WMF 5.1, hebben we de volgende bekende problemen opgelost:</span><span class="sxs-lookup"><span data-stu-id="94bdb-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="94bdb-106">Get-DscConfiguration mogelijk lege waarden (null) of fouten als resultaat als een type complex/hash-tabel wordt geretourneerd door de functie Get() van een klasse op basis van DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="94bdb-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="94bdb-107">Get-DscConfiguration retourneert fout als de RunAs-referentie in DSC-configuratie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="94bdb-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="94bdb-108">Op basis van een klasse resource kan niet worden gebruikt in een samengestelde configuratie.</span><span class="sxs-lookup"><span data-stu-id="94bdb-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="94bdb-109">Start-DscConfiguration loopt vast als bron op basis van een klasse een eigenschap van een eigen type heeft.</span><span class="sxs-lookup"><span data-stu-id="94bdb-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="94bdb-110">Op basis van een klasse resource kan niet worden gebruikt als een exclusieve resource.</span><span class="sxs-lookup"><span data-stu-id="94bdb-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="94bdb-111">Verbeteringen in Foutopsporing voor DSC-resource</span><span class="sxs-lookup"><span data-stu-id="94bdb-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="94bdb-112">In WMF 5.0, is de PowerShell-foutopsporing niet gestopt op de resource op basis van een klasse, methode (Get/Set/Test) rechtstreeks.</span><span class="sxs-lookup"><span data-stu-id="94bdb-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="94bdb-113">In WMF 5.1 stopt het foutopsporingsprogramma op dezelfde manier als voor de resources op basis van MOF-methoden op de resource op basis van een klasse-methode.</span><span class="sxs-lookup"><span data-stu-id="94bdb-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="94bdb-114">DSC-pull-client biedt ondersteuning voor TLS 1.1 en TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="94bdb-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="94bdb-115">Voorheen was ondersteund de DSC-pull-client alleen SSL3.0 en TLS1.0 via HTTPS-verbindingen.</span><span class="sxs-lookup"><span data-stu-id="94bdb-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="94bdb-116">Wanneer geforceerde veiliger protocollen gebruiken, dan werkt de pull-client niet.</span><span class="sxs-lookup"><span data-stu-id="94bdb-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="94bdb-117">In WMF 5.1, de DSC pull-client niet langer ondersteuning biedt voor SSL 3.0 en voegt ondersteuning toe voor de beter beveiligde TLS 1.1 en TLS 1.2-protocollen.</span><span class="sxs-lookup"><span data-stu-id="94bdb-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="94bdb-118">Verbeterde pull-server registreren</span><span class="sxs-lookup"><span data-stu-id="94bdb-118">Improved pull server registration</span></span>

<span data-ttu-id="94bdb-119">In eerdere versies van WMF zou gelijktijdige registraties/reporting aanvragen voor een DSC-pull-server tijdens het gebruik van de database ESENT leiden tot LCM niet te registreren en/of rapport.</span><span class="sxs-lookup"><span data-stu-id="94bdb-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="94bdb-120">In dergelijke gevallen de gebeurtenislogboeken op de pull-server heeft de fout 'Exemplaarnaam al in gebruik'.</span><span class="sxs-lookup"><span data-stu-id="94bdb-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="94bdb-121">Dit is vanwege een onjuiste patroon wordt gebruikt voor toegang tot de ESENT-database in een scenario met meerdere threads.</span><span class="sxs-lookup"><span data-stu-id="94bdb-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="94bdb-122">In WMF 5.1, heeft dit probleem is opgelost.</span><span class="sxs-lookup"><span data-stu-id="94bdb-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="94bdb-123">Gelijktijdige registraties of reporting (met inschakeling van ESENT-database) werkt prima in WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="94bdb-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="94bdb-124">Dit probleem geldt alleen voor de database ESENT en geldt niet voor de OLE DB-database.</span><span class="sxs-lookup"><span data-stu-id="94bdb-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="94bdb-125">Permanente logboekbestand op ESENT-database-exemplaar inschakelen</span><span class="sxs-lookup"><span data-stu-id="94bdb-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="94bdb-126">Eariler versie van DSC-PullServer, zijn de logboekbestanden van de ESENT-database de schijfruimte van de pullserver becouse die de database-instantie werd gemaakt zonder circulair vastleggen terechtkomen.</span><span class="sxs-lookup"><span data-stu-id="94bdb-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="94bdb-127">In deze release hebt u de optie voor het beheren van het gedrag circulair vastleggen van het exemplaar met behulp van het bestand web.config van de pullserver.</span><span class="sxs-lookup"><span data-stu-id="94bdb-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="94bdb-128">CircularLogging is standaard ingesteld op TRUE.</span><span class="sxs-lookup"><span data-stu-id="94bdb-128">By default CircularLogging is set to TRUE.</span></span>

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="94bdb-129">De naamconventie gedeeltelijke configuratie ophalen</span><span class="sxs-lookup"><span data-stu-id="94bdb-129">Pull partial configuration naming convention</span></span>

<span data-ttu-id="94bdb-130">In de vorige versie, de naamconventie voor een gedeeltelijke configuratie is dat de naam van de MOF-bestand in de pull-server/service moet overeenkomen met de naam van de gedeeltelijke configuratie opgegeven in de lokale configuration manager-instellingen die op zijn beurt moeten overeenkomen met de naam van de configuratie is ingesloten in het MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="94bdb-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="94bdb-131">Zie de onderstaande momentopnamen:</span><span class="sxs-lookup"><span data-stu-id="94bdb-131">See the snapshots below:</span></span>

- <span data-ttu-id="94bdb-132">Lokale configuratie-instellingen die u definieert een gedeeltelijke configuratie dat is toegestaan voor het ontvangen van een knooppunt.</span><span class="sxs-lookup"><span data-stu-id="94bdb-132">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Voorbeeld metaconfiguration](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="94bdb-134">De definitie van de voorbeeld-gedeeltelijke configuratie</span><span class="sxs-lookup"><span data-stu-id="94bdb-134">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="94bdb-135">'ConfigurationName' ingesloten in het gegenereerde MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="94bdb-135">'ConfigurationName' embedded in the generated MOF file.</span></span>

![Voorbeeld van gegenereerde mof-bestand](../images/PartialGeneratedMof.png)

- <span data-ttu-id="94bdb-137">Bestandsnaam in de opslagplaats van de pull-configuratie</span><span class="sxs-lookup"><span data-stu-id="94bdb-137">FileName in the pull configuration repository</span></span>

![Bestandsnaam in de opslagplaats van configuratie](../images/PartialInConfigRepository.png)

<span data-ttu-id="94bdb-139">Azure Automation-servicenaam gegenereerd MOF-bestanden als `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="94bdb-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="94bdb-140">Dus de onderstaande configuratie worden gecompileerd naar PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="94bdb-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="94bdb-141">Dit werd het onmogelijk voor pull een van uw gedeeltelijke configuratie in Azure Automation-service.</span><span class="sxs-lookup"><span data-stu-id="94bdb-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

<span data-ttu-id="94bdb-142">In WMF 5.1, een gedeeltelijke configuratie in de pull-server/service kan worden met de naam als `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="94bdb-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="94bdb-143">Als een virtuele machine is een eenmalige configuratie van een pull binnenhalen kunt serverservice vervolgens het configuratiebestand op de opslagplaats van de pull-server-configuratie bovendien een bestandsnaam hebben.</span><span class="sxs-lookup"><span data-stu-id="94bdb-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="94bdb-144">Deze naamgevingsconventie flexibiliteit kunt u uw knooppunten gedeeltelijk beheren met Azure Automation-service, waar een configuratie voor het knooppunt is binnenkort in Azure Automation DSC en waarbij een gedeeltelijke configuratie die u lokaal beheren.</span><span class="sxs-lookup"><span data-stu-id="94bdb-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="94bdb-145">De metaconfiguration hieronder ingesteld op een knooppunt om te worden beheerd zowel lokaal als door Azure Automation-service.</span><span class="sxs-lookup"><span data-stu-id="94bdb-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="94bdb-146">Met behulp van PsDscRunAsCredential met samengestelde DSC-resources</span><span class="sxs-lookup"><span data-stu-id="94bdb-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="94bdb-147">Ondersteuning voor het gebruik van toegevoegd [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) met DSC [samengestelde](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span><span class="sxs-lookup"><span data-stu-id="94bdb-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="94bdb-148">U kunt nu een waarde opgeven voor PsDscRunAsCredential bij het gebruik van samengestelde resources binnen configuraties.</span><span class="sxs-lookup"><span data-stu-id="94bdb-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="94bdb-149">Wanneer is opgegeven, wordt alle resources binnen een samengestelde resource uitgevoerd als een RunAs-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="94bdb-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="94bdb-150">Als een samengestelde resource aanroept die een andere samengestelde resource, worden alle bijbehorende resources ook uitgevoerd als RunAs-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="94bdb-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="94bdb-151">Run as-referenties worden doorgegeven aan een willekeurig niveau in de hiërarchie samengestelde resource.</span><span class="sxs-lookup"><span data-stu-id="94bdb-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="94bdb-152">Als een resource binnen een samengestelde resource een eigen waarde voor PsDscRunAsCredential bevat, resulteert een merge-fout tijdens de compilatie van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="94bdb-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="94bdb-153">Dit voorbeeld laat zien voor gebruik met [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) samengestelde resource opgenomen in de module PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="94bdb-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="94bdb-154">DSC-module en configuratie van validaties ondertekenen</span><span class="sxs-lookup"><span data-stu-id="94bdb-154">DSC module and configuration signing validations</span></span>

<span data-ttu-id="94bdb-155">DSC, worden configuraties en -modules gedistribueerd naar beheerde computers van de pull-server.</span><span class="sxs-lookup"><span data-stu-id="94bdb-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="94bdb-156">Als de pull-server is geknoeid, kan mogelijk een aanvaller wijzigen van de configuraties en -modules op de pull-server en dat er mee worden gedistribueerd naar alle beheerde knooppunten, verlies van al deze.</span><span class="sxs-lookup"><span data-stu-id="94bdb-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

<span data-ttu-id="94bdb-157">In WMF 5.1, DSC biedt ondersteuning voor de digitale handtekeningen van catalogus en de configuratie valideren (. MOF)-bestanden.</span><span class="sxs-lookup"><span data-stu-id="94bdb-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="94bdb-158">Deze functie wordt voorkomen dat knooppunten configuraties of module bestanden die niet zijn ondertekend door een vertrouwde ondertekenaar of waarmee is geknoeid nadat ze zijn ondertekend door vertrouwde ondertekenaar wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="94bdb-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="94bdb-159">Het ondertekenen van de configuratie en -module</span><span class="sxs-lookup"><span data-stu-id="94bdb-159">How to sign configuration and module</span></span>

***
* <span data-ttu-id="94bdb-160">Configuratiebestanden (. MOF-bestanden): De bestaande PowerShell-cmdlet [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) wordt uitgebreid met ondersteuning voor ondertekening van de MOF-bestanden.</span><span class="sxs-lookup"><span data-stu-id="94bdb-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="94bdb-161">Modules: Ondertekening van modules wordt uitgevoerd door het ondertekenen van de bijbehorende module-catalogus met behulp van de volgende stappen uit:</span><span class="sxs-lookup"><span data-stu-id="94bdb-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="94bdb-162">Maak een catalogusbestand: Een catalogusbestand bevat een verzameling van cryptografische hashes of de vingerafdrukken.</span><span class="sxs-lookup"><span data-stu-id="94bdb-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="94bdb-163">Elke vingerafdruk komt overeen met een bestand dat is opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="94bdb-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="94bdb-164">De nieuwe cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), zodat gebruikers kunnen maken van een catalogusbestand voor de module is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="94bdb-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="94bdb-165">Meld u aan het catalogusbestand: Gebruik [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) om de catalogusbestand te ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="94bdb-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="94bdb-166">Plaats het catalogusbestand in de modulemap.</span><span class="sxs-lookup"><span data-stu-id="94bdb-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="94bdb-167">Volgens de conventies wordt moet module catalogusbestand worden geplaatst in de modulemap met dezelfde naam als de module.</span><span class="sxs-lookup"><span data-stu-id="94bdb-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="94bdb-168">Instellingen voor LocalConfigurationManager ondertekenen validaties inschakelen</span><span class="sxs-lookup"><span data-stu-id="94bdb-168">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="94bdb-169">Pull</span><span class="sxs-lookup"><span data-stu-id="94bdb-169">Pull</span></span>

<span data-ttu-id="94bdb-170">De LocalConfigurationManager van een knooppunt voert ondertekenen validatie van modules en configuraties op basis van de huidige instellingen.</span><span class="sxs-lookup"><span data-stu-id="94bdb-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="94bdb-171">Handtekeningvalidatie is standaard uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="94bdb-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="94bdb-172">Handtekeningvalidatie kan worden ingeschakeld door het blok 'SignatureValidation' toe te voegen aan de definitie meta-configuratie van het knooppunt zoals hieronder:</span><span class="sxs-lookup"><span data-stu-id="94bdb-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="94bdb-173">De bovenstaande metaconfiguration instellen op een knooppunt, kunt handtekeningvalidatie op gedownloade configuraties en -modules.</span><span class="sxs-lookup"><span data-stu-id="94bdb-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="94bdb-174">De Local Configuration Manager voert de volgende stappen uit om te controleren of de digitale handtekeningen.</span><span class="sxs-lookup"><span data-stu-id="94bdb-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="94bdb-175">Controleer of de handtekening van een configuratiebestand (. MOF) is geldig.</span><span class="sxs-lookup"><span data-stu-id="94bdb-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="94bdb-176">Het maakt gebruik van de PowerShell-cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), die in 5.1 ter ondersteuning van MOF handtekeningvalidatie is uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="94bdb-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="94bdb-177">Controleer of de certificeringsinstantie die de ondertekenaar gemachtigd wordt vertrouwd.</span><span class="sxs-lookup"><span data-stu-id="94bdb-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="94bdb-178">Afhankelijkheden van de configuratie van de module/resource naar een tijdelijke locatie downloaden.</span><span class="sxs-lookup"><span data-stu-id="94bdb-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="94bdb-179">Controleer of de handtekening van de catalogus die is opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="94bdb-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="94bdb-180">Zoek een `<moduleName>.cat` bestands- en controleer of de handtekening met behulp van de cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="94bdb-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="94bdb-181">Controleer of de certificeringsinstantie (CA) die de ondertekenaar geverifieerd wordt vertrouwd.</span><span class="sxs-lookup"><span data-stu-id="94bdb-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="94bdb-182">Controleer of de inhoud van de modules niet is geknoeid met de nieuwe cmdlet [Test FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="94bdb-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="94bdb-183">Install-Module voor $env: ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="94bdb-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="94bdb-184">Procesconfiguratie van</span><span class="sxs-lookup"><span data-stu-id="94bdb-184">Process configuration</span></span>

> <span data-ttu-id="94bdb-185">Opmerking: Handtekeningvalidatie van module-catalogus en de configuratie wordt alleen uitgevoerd wanneer de configuratie wordt toegepast op het systeem voor de eerste keer of wanneer de module wordt gedownload en geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="94bdb-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="94bdb-186">Consistentiecontrole wordt uitgevoerd, wordt de handtekening van Current.mof of de module-afhankelijkheden niet gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="94bdb-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="94bdb-187">Als verificatie is mislukt tijdens elke fase, bijvoorbeeld, als de configuratie die is opgehaald uit de pull-server is niet ondertekend, klikt u vervolgens verwerking van de configuratie wordt beëindigd met de fout die hieronder wordt weergegeven en alle tijdelijke bestanden worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="94bdb-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Uitvoer van de voorbeeldconfiguratie-fout](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="94bdb-189">Binnenhalen van een module met-catalogus niet is ondertekend op dezelfde manier, resulteert dit in de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="94bdb-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Uitvoer van de voorbeeldmodule-fout](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="94bdb-191">Push</span><span class="sxs-lookup"><span data-stu-id="94bdb-191">Push</span></span>

<span data-ttu-id="94bdb-192">Een configuratie die is geleverd met behulp van push kan worden geknoeid bij de bron voordat deze naar het knooppunt geleverd.</span><span class="sxs-lookup"><span data-stu-id="94bdb-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="94bdb-193">De Local Configuration Manager voert gelijksoortige stappen van de handtekening validatie voor gepushte of gepubliceerd configuratie (s).</span><span class="sxs-lookup"><span data-stu-id="94bdb-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="94bdb-194">Hieronder volgt een compleet voorbeeld van validatie van de handtekening voor pushmeldingen.</span><span class="sxs-lookup"><span data-stu-id="94bdb-194">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="94bdb-195">Handtekeningvalidatie op het knooppunt inschakelen.</span><span class="sxs-lookup"><span data-stu-id="94bdb-195">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="94bdb-196">Een voorbeeld-configuratiebestand maken.</span><span class="sxs-lookup"><span data-stu-id="94bdb-196">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="94bdb-197">Probeer de niet-ondertekende configuratiebestand pushen naar het knooppunt.</span><span class="sxs-lookup"><span data-stu-id="94bdb-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="94bdb-199">Meld u aan het configuratiebestand met behulp van certificaat voor ondertekening van programmacode.</span><span class="sxs-lookup"><span data-stu-id="94bdb-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="94bdb-201">Probeer het pushen van de ondertekende MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="94bdb-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)
