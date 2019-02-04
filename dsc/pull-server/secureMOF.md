---
ms.date: 10/31/2017
keywords: DSC, powershell, configuratie en installatie
title: Het MOF-bestand te beveiligen
ms.openlocfilehash: 6c2aadb75ac617d9b845ef387f292b8156bb8889
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688327"
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="1451b-103">Het MOF-bestand te beveiligen</span><span class="sxs-lookup"><span data-stu-id="1451b-103">Securing the MOF File</span></span>

> <span data-ttu-id="1451b-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1451b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1451b-105">DSC wordt de configuratie van server-knooppunten beheerd door toe te passen die zijn opgeslagen in een MOF-bestand, waarbij de lokale Configuration Manager (LCM) de status van de gewenste end implementeert.</span><span class="sxs-lookup"><span data-stu-id="1451b-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span>
<span data-ttu-id="1451b-106">Omdat dit bestand de details van de configuratie bevat, is het belangrijk om veilig te houden.</span><span class="sxs-lookup"><span data-stu-id="1451b-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span>
<span data-ttu-id="1451b-107">In dit onderwerp wordt beschreven hoe om te controleren of het doelknooppunt het bestand is versleuteld.</span><span class="sxs-lookup"><span data-stu-id="1451b-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="1451b-108">Beginnen met de PowerShell-versie 5.0, het gehele MOF-bestand is standaard versleuteld wanneer deze wordt toegepast op het knooppunt met behulp van de `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1451b-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the `Start-DSCConfiguration` cmdlet.</span></span>
<span data-ttu-id="1451b-109">De procedure beschreven in dit artikel is vereist alleen bij het implementeren van een oplossing met behulp van de pull-service-protocol als certificaten niet worden beheerd, om te controleren of de configuraties die zijn gedownload door het doelknooppunt kunnen worden ontsleuteld en worden gelezen door het systeem voordat ze worden toegepast (bijvoorbeeld de pull-service beschikbaar is in Windows Server).</span><span class="sxs-lookup"><span data-stu-id="1451b-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span>
<span data-ttu-id="1451b-110">Knooppunten die zijn geregistreerd bij [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) automatisch certificaten geïnstalleerd en beheerd door de service met geen administratieve overhead vereist.</span><span class="sxs-lookup"><span data-stu-id="1451b-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

> [!NOTE]
> <span data-ttu-id="1451b-111">In dit onderwerp worden de certificaten die worden gebruikt voor versleuteling.</span><span class="sxs-lookup"><span data-stu-id="1451b-111">This topic discusses certificates used for encryption.</span></span>
> <span data-ttu-id="1451b-112">Voor versleuteling, wordt een zelfondertekend certificaat voldoende is, omdat de persoonlijke sleutel wordt altijd bewaard geheim en versleuteling impliceert geen vertrouwen in het document.</span><span class="sxs-lookup"><span data-stu-id="1451b-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span>
> <span data-ttu-id="1451b-113">Zelfondertekende certificaten moeten *niet* worden gebruikt voor verificatiedoeleinden wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1451b-113">Self-signed certificates should *not* be used for authentication purposes.</span></span>
> <span data-ttu-id="1451b-114">U moet een certificaat van een vertrouwde certificeringsinstantie (CA) gebruiken voor verificatiedoeleinden.</span><span class="sxs-lookup"><span data-stu-id="1451b-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1451b-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1451b-115">Prerequisites</span></span>

<span data-ttu-id="1451b-116">Voor het versleutelen is van de referenties die worden gebruikt voor het beveiligen van een DSC-configuratie, zorg ervoor dat u het volgende:</span><span class="sxs-lookup"><span data-stu-id="1451b-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

- <span data-ttu-id="1451b-117">**Een manier van uitgeven en distribueren van certificaten**.</span><span class="sxs-lookup"><span data-stu-id="1451b-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="1451b-118">In dit onderwerp en de voorbeelden wordt ervan uitgegaan dat u gebruikmaakt van Active Directory-certificeringsinstantie.</span><span class="sxs-lookup"><span data-stu-id="1451b-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="1451b-119">Zie voor meer achtergrondinformatie over Active Directory Certificate Services, [overzicht van Active Directory Certificate Services](https://technet.microsoft.com/library/hh831740.aspx) en [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="1451b-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
- <span data-ttu-id="1451b-120">**Beheerderstoegang tot het doelknooppunt of knooppunten**.</span><span class="sxs-lookup"><span data-stu-id="1451b-120">**Administrative access to the target node or nodes**.</span></span>
- <span data-ttu-id="1451b-121">**Elk doelknooppunt heeft een versleuteling geschikt certificaat opgeslagen van de persoonlijke Store**.</span><span class="sxs-lookup"><span data-stu-id="1451b-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="1451b-122">In Windows PowerShell is het pad naar de store Cert: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="1451b-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="1451b-123">De voorbeelden in dit onderwerp gebruikt u de sjabloon "verificatie van werkstation" die u (samen met andere certificaatsjablonen vinden kunt) op [standaardcertificaatsjablonen](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="1451b-123">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
- <span data-ttu-id="1451b-124">Als u deze configuratie op een andere computer dan het doelknooppunt uitvoert **Exporteer de openbare sleutel van het certificaat**, en vervolgens importeren naar de computer die u de configuratie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1451b-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="1451b-125">Zorg ervoor dat u alleen exporteert de **openbare** sleutel; de persoonlijke sleutel te beveiligen.</span><span class="sxs-lookup"><span data-stu-id="1451b-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="1451b-126">Algehele proces</span><span class="sxs-lookup"><span data-stu-id="1451b-126">Overall process</span></span>

 1. <span data-ttu-id="1451b-127">Instellen van de certificaten, sleutels en vingerafdrukken, ervoor te zorgen dat elk doelknooppunt kopieën van het certificaat heeft en de configuratie-computer de openbare sleutel en de vingerafdruk heeft.</span><span class="sxs-lookup"><span data-stu-id="1451b-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="1451b-128">Maak een configuratie-gegevensblokken die het pad en de vingerafdruk van de openbare sleutel bevat.</span><span class="sxs-lookup"><span data-stu-id="1451b-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="1451b-129">Maakt een configuratiescript die definieert de gewenste configuratie op voor het doelknooppunt en decodering van de doelknooppunten ingesteld door de lokale configuratie appautonomie manager om de van configuratiegegevens met behulp van het certificaat en de vingerafdruk te ontsleutelen.</span><span class="sxs-lookup"><span data-stu-id="1451b-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="1451b-130">Voer de configuratie, waardoor de Local Configuration Manager-instellingen en start de DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="1451b-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](../images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="1451b-132">Vereisten voor certificaten</span><span class="sxs-lookup"><span data-stu-id="1451b-132">Certificate Requirements</span></span>

<span data-ttu-id="1451b-133">Als u wilt gerapporteerd versleuteling van referenties, een openbare-sleutelcertificaat moet beschikbaar zijn op de _doelknooppunt_ dat wil zeggen **vertrouwde** door de computer die wordt gebruikt voor het maken van de DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="1451b-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="1451b-134">Deze openbare-sleutelcertificaat dat heeft specifieke vereisten voor de oplossing worden gebruikt voor versleuteling van de DSC-referenties:</span><span class="sxs-lookup"><span data-stu-id="1451b-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>

1. <span data-ttu-id="1451b-135">**Sleutelgebruik**:</span><span class="sxs-lookup"><span data-stu-id="1451b-135">**Key Usage**:</span></span>
   - <span data-ttu-id="1451b-136">Moet bevatten: 'Keyencipherment-bit' en 'DataEncipherment'.</span><span class="sxs-lookup"><span data-stu-id="1451b-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="1451b-137">Moet _niet_ bevatten: 'De digitale handtekening'.</span><span class="sxs-lookup"><span data-stu-id="1451b-137">Should _not_ contain: 'Digital Signature'.</span></span>
2. <span data-ttu-id="1451b-138">**Enhanced Key Usage**:</span><span class="sxs-lookup"><span data-stu-id="1451b-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="1451b-139">Moet bevatten: Document-versleuteling (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="1451b-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="1451b-140">Moet _niet_ bevatten: Clientverificatie (1.3.6.1.5.5.7.3.2) en serververificatie (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="1451b-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
3. <span data-ttu-id="1451b-141">De persoonlijke sleutel voor het certificaat is beschikbaar op de \* Node_ doel.</span><span class="sxs-lookup"><span data-stu-id="1451b-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
4. <span data-ttu-id="1451b-142">De **Provider** voor het certificaat moet 'Microsoft RSA SChannel Cryptographic Provider'.</span><span class="sxs-lookup"><span data-stu-id="1451b-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1451b-143">Maar u een certificaat gebruiken kunt met die van een Sleutelgebruik 'Digitale handtekening' of een van de clientverificatie-EKU, schakelt Hiermee u de versleutelingssleutel moet eenvoudiger misbruik en kwetsbaar voor aanvallen.</span><span class="sxs-lookup"><span data-stu-id="1451b-143">Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="1451b-144">Het is dus aanbevolen procedure om een certificaat gemaakt voor de beveiliging van de DSC-referenties die worden weggelaten deze sleutelgebruik en EKU's te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1451b-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="1451b-145">Alle bestaande certificaten op de _doelknooppunt_ dat voldoet aan deze criteria kunnen worden gebruikt voor beveiligde DSC-referenties.</span><span class="sxs-lookup"><span data-stu-id="1451b-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="1451b-146">Het maken van certificaten</span><span class="sxs-lookup"><span data-stu-id="1451b-146">Certificate creation</span></span>

<span data-ttu-id="1451b-147">Er zijn twee manieren om te maken en gebruiken van het vereiste certificaat voor versleuteling (openbaar / persoonlijk sleutelpaar).</span><span class="sxs-lookup"><span data-stu-id="1451b-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="1451b-148">Maken door op de **doelknooppunt** en exporteren van de openbare sleutel voor de **knooppunt ontwerpen**</span><span class="sxs-lookup"><span data-stu-id="1451b-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="1451b-149">Maken door op de **ontwerpen knooppunt** en exporteren van het gehele sleutelpaar aan de **doelknooppunt**</span><span class="sxs-lookup"><span data-stu-id="1451b-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="1451b-150">Methode 1 wordt aanbevolen omdat de persoonlijke sleutel voor het ontsleutelen van de referenties in het MOF op het doelknooppunt te allen tijde blijft.</span><span class="sxs-lookup"><span data-stu-id="1451b-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>

### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="1451b-151">Het maken van het certificaat op het doelknooppunt</span><span class="sxs-lookup"><span data-stu-id="1451b-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="1451b-152">De privésleutel geheim moet blijven, omdat wordt gebruikt voor het ontsleutelen van de MOF op de **doelknooppunt** de eenvoudigste manier om dat te doen is om te maken van het certificaat met persoonlijke sleutel op de **doelknooppunt**, en kopieer de  **openbare-sleutelcertificaat** op de computer die wordt gebruikt voor het maken van de DSC-configuratie naar een MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="1451b-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="1451b-153">Het volgende voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1451b-153">The following example:</span></span>

1. <span data-ttu-id="1451b-154">Hiermee maakt u een certificaat op de **doelknooppunt**</span><span class="sxs-lookup"><span data-stu-id="1451b-154">creates a certificate on the **Target node**</span></span>
2. <span data-ttu-id="1451b-155">Hiermee exporteert u de openbare-sleutelcertificaat dat op de **doelknooppunt**.</span><span class="sxs-lookup"><span data-stu-id="1451b-155">exports the public key certificate on the **Target node**.</span></span>
3. <span data-ttu-id="1451b-156">de invoer van de openbare-sleutelcertificaat dat in de **mijn** certificaatarchief op de **ontwerpen knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="1451b-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="1451b-157">Op het doelknooppunt: maken en exporteren van het certificaat</span><span class="sxs-lookup"><span data-stu-id="1451b-157">On the Target Node: create and export the certificate</span></span>

> <span data-ttu-id="1451b-158">Doelknooppunt: WindowsServer 2016 en Windows 10</span><span class="sxs-lookup"><span data-stu-id="1451b-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="1451b-159">Eenmaal hebt geëxporteerd, de `DscPublicKey.cer` moet worden gekopieerd naar de **ontwerpen knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="1451b-159">Once exported, the `DscPublicKey.cer` would need to be copied to the **Authoring Node**.</span></span>

> <span data-ttu-id="1451b-160">Doelknooppunt: Windows Server 2012 R2/Windows 8.1 en oudere versies</span><span class="sxs-lookup"><span data-stu-id="1451b-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="1451b-161">Omdat de `New-SelfSignedCertificate` cmdlet op Windows-besturingssystemen vóór Windows 10 en Windows Server 2016 bieden geen ondersteuning voor de **Type** parameter, een alternatieve methode voor het maken van dit certificaat is vereist op deze besturingssystemen.</span><span class="sxs-lookup"><span data-stu-id="1451b-161">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
>
> <span data-ttu-id="1451b-162">In dit geval kunt u `makecert.exe` of `certutil.exe` om het certificaat te maken.</span><span class="sxs-lookup"><span data-stu-id="1451b-162">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span>
>
><span data-ttu-id="1451b-163">Is een alternatieve methode [het script New-SelfSignedCertificateEx.ps1 downloaden vanaf Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) en voor het maken van het certificaat in plaats daarvan het:</span><span class="sxs-lookup"><span data-stu-id="1451b-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="1451b-164">Eenmaal hebt geëxporteerd, de ```DscPublicKey.cer``` moet worden gekopieerd naar de **ontwerpen knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="1451b-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="1451b-165">Op het knooppunt ontwerpen: de openbare sleutel van het certificaat importeren</span><span class="sxs-lookup"><span data-stu-id="1451b-165">On the Authoring Node: import the cert’s public key</span></span>

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="1451b-166">Het maken van het certificaat op het knooppunt ontwerpen</span><span class="sxs-lookup"><span data-stu-id="1451b-166">Creating the Certificate on the Authoring Node</span></span>

<span data-ttu-id="1451b-167">U kunt ook het versleutelingscertificaat dat kan worden gemaakt op de **ontwerpen knooppunt**, geëxporteerd met de **privésleutel** als een PFX-bestand en vervolgens worden geïmporteerd op de **doelknooppunt**.</span><span class="sxs-lookup"><span data-stu-id="1451b-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="1451b-168">Dit is de huidige methode voor het implementeren van DSC-referentieversleuteling op _Nano Server_.</span><span class="sxs-lookup"><span data-stu-id="1451b-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="1451b-169">Hoewel de PFX is beveiligd met een wachtwoord moet het worden gehouden beveiligd tijdens de overdracht.</span><span class="sxs-lookup"><span data-stu-id="1451b-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="1451b-170">Het volgende voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1451b-170">The following example:</span></span>

1. <span data-ttu-id="1451b-171">Hiermee maakt u een certificaat op de **ontwerpen knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="1451b-171">creates a certificate on the **Authoring node**.</span></span>
2. <span data-ttu-id="1451b-172">Hiermee exporteert u het certificaat met inbegrip van de persoonlijke sleutel op de **ontwerpen knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="1451b-172">exports the certificate including the private key on the **Authoring node**.</span></span>
3. <span data-ttu-id="1451b-173">Hiermee verwijdert u de persoonlijke sleutel van de **ontwerpen knooppunt**, maar houdt u de openbare-sleutelcertificaat dat de **mijn** opslaan.</span><span class="sxs-lookup"><span data-stu-id="1451b-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
4. <span data-ttu-id="1451b-174">het certificaat met persoonlijke sleutel wordt geïmporteerd in het certificaatarchief My(Personal) op de **doelknooppunt**.</span><span class="sxs-lookup"><span data-stu-id="1451b-174">imports the private key certificate into the My(Personal) certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="1451b-175">Deze moet worden toegevoegd aan het basisarchief zodat deze worden vertrouwd door de **doelknooppunt**.</span><span class="sxs-lookup"><span data-stu-id="1451b-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="1451b-176">Op het knooppunt ontwerpen: maken en exporteren van het certificaat</span><span class="sxs-lookup"><span data-stu-id="1451b-176">On the Authoring Node: create and export the certificate</span></span>

> <span data-ttu-id="1451b-177">Doelknooppunt: WindowsServer 2016 en Windows 10</span><span class="sxs-lookup"><span data-stu-id="1451b-177">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

<span data-ttu-id="1451b-178">Eenmaal hebt geëxporteerd, de `DscPrivateKey.pfx` moet worden gekopieerd naar de **doelknooppunt**.</span><span class="sxs-lookup"><span data-stu-id="1451b-178">Once exported, the `DscPrivateKey.pfx` would need to be copied to the **Target Node**.</span></span>

> <span data-ttu-id="1451b-179">Doelknooppunt: Windows Server 2012 R2/Windows 8.1 en oudere versies</span><span class="sxs-lookup"><span data-stu-id="1451b-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="1451b-180">Omdat de `New-SelfSignedCertificate` cmdlet op Windows-besturingssystemen vóór Windows 10 en Windows Server 2016 bieden geen ondersteuning voor de **Type** parameter, een alternatieve methode voor het maken van dit certificaat is vereist op deze besturingssystemen.</span><span class="sxs-lookup"><span data-stu-id="1451b-180">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
>
> <span data-ttu-id="1451b-181">In dit geval kunt u `makecert.exe` of `certutil.exe` om het certificaat te maken.</span><span class="sxs-lookup"><span data-stu-id="1451b-181">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span>
>
> <span data-ttu-id="1451b-182">Is een alternatieve methode [het script New-SelfSignedCertificateEx.ps1 downloaden vanaf Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) en voor het maken van het certificaat in plaats daarvan het:</span><span class="sxs-lookup"><span data-stu-id="1451b-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="1451b-183">Op het doelknooppunt: de persoonlijke sleutel van het certificaat als een vertrouwd basiscertificaat importeren</span><span class="sxs-lookup"><span data-stu-id="1451b-183">On the Target Node: import the cert’s private key as a trusted root</span></span>

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="1451b-184">Configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="1451b-184">Configuration data</span></span>

<span data-ttu-id="1451b-185">Het gegevensblok configuratie definieert welke doelknooppunten bewerkingen uitvoeren, of of niet voor het versleutelen van de referenties, de wijze van versleuteling en andere informatie.</span><span class="sxs-lookup"><span data-stu-id="1451b-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="1451b-186">Zie voor meer informatie over het gegevensblok configuratie [scheiden van configuratie- en omgevingsgegevens](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="1451b-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](../configurations/configData.md).</span></span>

<span data-ttu-id="1451b-187">De elementen die kunnen worden geconfigureerd voor elk knooppunt die gerelateerd zijn aan de versleuteling van referenties zijn:</span><span class="sxs-lookup"><span data-stu-id="1451b-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>

- <span data-ttu-id="1451b-188">**Knooppuntnaam** -de naam van het doelknooppunt die voor de versleuteling van referenties wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="1451b-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
- <span data-ttu-id="1451b-189">**PsDscAllowPlainTextPassword** - of niet-versleutelde referenties worden doorgegeven aan dit knooppunt kunnen worden.</span><span class="sxs-lookup"><span data-stu-id="1451b-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="1451b-190">Dit is **niet aanbevolen**.</span><span class="sxs-lookup"><span data-stu-id="1451b-190">This is **not recommended**.</span></span>
- <span data-ttu-id="1451b-191">**Vingerafdruk** -de vingerafdruk van het certificaat dat wordt gebruikt voor het ontsleutelen van de referenties in de DSC-configuratie op de _doelknooppunt_.</span><span class="sxs-lookup"><span data-stu-id="1451b-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="1451b-192">**Dit certificaat moet zich in het certificaatarchief van lokale computer op het doelknooppunt.**</span><span class="sxs-lookup"><span data-stu-id="1451b-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
- <span data-ttu-id="1451b-193">**CertificateFile** - het certificaatbestand (met alleen de openbare sleutel) die moet worden gebruikt voor het versleutelen van de referenties voor de _doelknooppunt_.</span><span class="sxs-lookup"><span data-stu-id="1451b-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="1451b-194">Dit moet ofwel een DER encoded binary X.509 of Base-64 gecodeerde x.509-certificaat indelingsbestand.</span><span class="sxs-lookup"><span data-stu-id="1451b-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="1451b-195">Dit voorbeeld toont een configuratie-gegevensblokken die Hiermee geeft u een doelknooppunt om te reageren op met de naam targetNode, het pad naar het openbare-sleutelcertificaat dat bestand (met de naam targetNode.cer) en de vingerafdruk voor de openbare sleutel.</span><span class="sxs-lookup"><span data-stu-id="1451b-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            };
        );
    }
```

## <a name="configuration-script"></a><span data-ttu-id="1451b-196">Het script voor configuratie</span><span class="sxs-lookup"><span data-stu-id="1451b-196">Configuration script</span></span>

<span data-ttu-id="1451b-197">In het configuratiescript zelf, gebruikt u de `PsCredential` parameter om ervoor te zorgen dat de referenties voor de kortst mogelijke tijd worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1451b-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="1451b-198">Wanneer u het opgegeven voorbeeld uitvoert, wordt DSC u gevraagd om referenties en deze vervolgens versleutelen het MOF-bestand met behulp van de CertificateFile die is gekoppeld aan het doelknooppunt in het gegevensblok configuratie.</span><span class="sxs-lookup"><span data-stu-id="1451b-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="1451b-199">Dit codevoorbeeld wordt een bestand gekopieerd van een share die wordt beveiligd voor een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="1451b-199">This code example copies a file from a share that is secured to a user.</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a><span data-ttu-id="1451b-200">Instellen van ontsleuteling</span><span class="sxs-lookup"><span data-stu-id="1451b-200">Setting up decryption</span></span>

<span data-ttu-id="1451b-201">Voordat u [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) kunt werken, hebt u vertelt de Local Configuration Manager op elk doelknooppunt welk certificaat moet worden gebruikt voor het decoderen van de referenties met behulp van de resource CertificateID om te controleren of de vingerafdruk van het certificaat.</span><span class="sxs-lookup"><span data-stu-id="1451b-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="1451b-202">Deze voorbeeldfunctie vindt u de juiste lokale certificaatarchief (mogelijk moet u deze aanpassen, dus het exacte certificaat dat u wilt gebruiken):</span><span class="sxs-lookup"><span data-stu-id="1451b-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

<span data-ttu-id="1451b-203">Met het certificaat dat wordt geïdentificeerd door de vingerafdruk, kan het configuratiescript worden bijgewerkt om de waarde te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="1451b-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a><span data-ttu-id="1451b-204">De configuratie wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="1451b-204">Running the configuration</span></span>

<span data-ttu-id="1451b-205">Op dit moment kunt u de configuratie, die wordt uitgevoerd twee bestanden uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="1451b-205">At this point, you can run the configuration, which will output two files:</span></span>

- <span data-ttu-id="1451b-206">Een \*. meta.mof-bestand dat Hiermee configureert u de Local Configuration Manager voor het ontsleutelen van de referenties met behulp van het certificaat dat is opgeslagen in het archief van de lokale computer en die worden vermeld op basis van de miniatuur.</span><span class="sxs-lookup"><span data-stu-id="1451b-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="1451b-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) van toepassing is de \*. meta.mof-bestand.</span><span class="sxs-lookup"><span data-stu-id="1451b-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
- <span data-ttu-id="1451b-208">Een MOF-bestand dat de configuratie geldt.</span><span class="sxs-lookup"><span data-stu-id="1451b-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="1451b-209">Start-DscConfiguration geldt de configuratie.</span><span class="sxs-lookup"><span data-stu-id="1451b-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="1451b-210">Deze opdrachten wordt deze stappen uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="1451b-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="1451b-211">In dit voorbeeld zou de DSC-configuratie om het doelknooppunt te pushen.</span><span class="sxs-lookup"><span data-stu-id="1451b-211">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="1451b-212">De DSC-configuratie kan ook worden toegepast met behulp van een DSC-Pull-Server als deze beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="1451b-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="1451b-213">Zie [instellen van een DSC-pull-client](pullClient.md) voor meer informatie over het toepassen van DSC-configuraties met behulp van een DSC-Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="1451b-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="1451b-214">Voorbeeld van de Module referentie-codering</span><span class="sxs-lookup"><span data-stu-id="1451b-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="1451b-215">Hier volgt een compleet voorbeeld waarin al deze stappen, plus een helper-cmdlet die worden geëxporteerd en de openbare sleutels worden gekopieerd:</span><span class="sxs-lookup"><span data-stu-id="1451b-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```
