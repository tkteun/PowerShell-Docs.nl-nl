---
ms.date: 10/31/2017
keywords: DSC, Power shell, configuratie, installatie
title: Het MOF-bestand beveiligen
ms.openlocfilehash: ab03db8bf4ed7d412691ae87fd12da5131607886
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278461"
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="d9976-103">Het MOF-bestand beveiligen</span><span class="sxs-lookup"><span data-stu-id="d9976-103">Securing the MOF File</span></span>

> <span data-ttu-id="d9976-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="d9976-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d9976-105">DSC beheert de configuratie van server knooppunten door gegevens die zijn opgeslagen in een MOF-bestand toe te passen, waarbij de lokale Configuration Manager (LCM) de gewenste eind status implementeert.</span><span class="sxs-lookup"><span data-stu-id="d9976-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span> <span data-ttu-id="d9976-106">Omdat dit bestand de details van de configuratie bevat, is het belang rijk om het beveiligd te blijven.</span><span class="sxs-lookup"><span data-stu-id="d9976-106">Because this file contains the details of the configuration, it's important to keep it secure.</span></span> <span data-ttu-id="d9976-107">In dit onderwerp wordt beschreven hoe u ervoor zorgt dat het bestand is versleuteld met het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="d9976-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="d9976-108">Vanaf Power shell versie 5,0 wordt het volledige MOF-bestand standaard versleuteld wanneer het wordt toegepast op het knoop punt `Start-DSCConfiguration` met behulp van de-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9976-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="d9976-109">Het proces dat in dit artikel wordt beschreven, is alleen vereist bij het implementeren van een oplossing met het pull-service protocol als certificaten niet worden beheerd, om ervoor te zorgen dat de configuraties die door het doel knooppunt worden gedownload, kunnen worden ontsleuteld en gelezen voordat ze worden toegepast (bijvoorbeeld de pull-service die beschikbaar is in Windows Server).</span><span class="sxs-lookup"><span data-stu-id="d9976-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span> <span data-ttu-id="d9976-110">Knoop punten die zijn geregistreerd bij [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) , hebben automatisch certificaten geïnstalleerd en beheerd door de service zonder dat er administratieve overhead nodig is.</span><span class="sxs-lookup"><span data-stu-id="d9976-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

> [!NOTE]
> <span data-ttu-id="d9976-111">In dit onderwerp worden de certificaten beschreven die worden gebruikt voor versleuteling.</span><span class="sxs-lookup"><span data-stu-id="d9976-111">This topic discusses certificates used for encryption.</span></span> <span data-ttu-id="d9976-112">Voor versleuteling is een zelfondertekend certificaat voldoende, omdat de persoonlijke sleutel altijd geheim is en versleuteling niet het vertrouwen van het document impliceert.</span><span class="sxs-lookup"><span data-stu-id="d9976-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span> <span data-ttu-id="d9976-113">Zelfondertekende certificaten mogen *niet* worden gebruikt voor verificatie doeleinden.</span><span class="sxs-lookup"><span data-stu-id="d9976-113">Self-signed certificates should *not* be used for authentication purposes.</span></span> <span data-ttu-id="d9976-114">U moet een certificaat van een vertrouwde certificerings instantie (CA) gebruiken voor verificatie doeleinden.</span><span class="sxs-lookup"><span data-stu-id="d9976-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d9976-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d9976-115">Prerequisites</span></span>

<span data-ttu-id="d9976-116">Zorg ervoor dat u over het volgende beschikt om de referenties te versleutelen die worden gebruikt voor het beveiligen van een DSC-configuratie:</span><span class="sxs-lookup"><span data-stu-id="d9976-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

- <span data-ttu-id="d9976-117">**Een aantal manieren om certificaten te verlenen en te distribueren**.</span><span class="sxs-lookup"><span data-stu-id="d9976-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="d9976-118">In dit onderwerp en de voor beelden wordt ervan uitgegaan dat u Active Directory certificerings instantie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d9976-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="d9976-119">Zie [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx)(Engelstalig) voor meer achtergrond informatie over Active Directory Certificate Services.</span><span class="sxs-lookup"><span data-stu-id="d9976-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
- <span data-ttu-id="d9976-120">**Beheerders toegang tot het doel knooppunt of de knoop punten**.</span><span class="sxs-lookup"><span data-stu-id="d9976-120">**Administrative access to the target node or nodes**.</span></span>
- <span data-ttu-id="d9976-121">**Elk doel knooppunt heeft een persoonlijk archief dat geschikt is voor versleuteling**.</span><span class="sxs-lookup"><span data-stu-id="d9976-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="d9976-122">Het pad naar de Store van Windows Power shell is certificaat: \ LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="d9976-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="d9976-123">In de voor beelden in dit onderwerp wordt gebruikgemaakt van de sjabloon voor verificatie van werk station, die u kunt vinden (samen met andere certificaat sjablonen) op [standaard certificaat sjablonen](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="d9976-123">The examples in this topic use the "workstation authentication" template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
- <span data-ttu-id="d9976-124">Als u deze configuratie op een andere computer dan het doel knooppunt wilt uitvoeren, **exporteert u de open bare sleutel van het certificaat**en importeert u het vervolgens naar de computer waarop u de configuratie wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="d9976-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="d9976-125">Zorg ervoor dat u alleen de **open bare** sleutel exporteert. Zorg ervoor dat de persoonlijke sleutel is beveiligd.</span><span class="sxs-lookup"><span data-stu-id="d9976-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="d9976-126">Algemeen proces</span><span class="sxs-lookup"><span data-stu-id="d9976-126">Overall process</span></span>

 1. <span data-ttu-id="d9976-127">Stel de certificaten, sleutels en vinger afdrukken in om ervoor te zorgen dat elk doel knooppunt kopieën van het certificaat heeft en de configuratie computer de open bare sleutel en vinger afdruk heeft.</span><span class="sxs-lookup"><span data-stu-id="d9976-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="d9976-128">Maak een blok met configuratie gegevens dat het pad en de vinger afdruk van de open bare sleutel bevat.</span><span class="sxs-lookup"><span data-stu-id="d9976-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="d9976-129">Maak een configuratie script dat uw gewenste configuratie definieert voor het doel knooppunt en stelt ontsleuteling in voor de doel knooppunten door de lokale Configuration Manager te gebruiken om de configuratie gegevens te ontsleutelen met behulp van het certificaat en de vinger afdruk.</span><span class="sxs-lookup"><span data-stu-id="d9976-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="d9976-130">Voer de configuratie uit, waarmee de lokale Configuration Manager instellingen worden ingesteld en de DSC-configuratie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="d9976-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](media/secureMOF/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="d9976-132">Certificaatvereisten</span><span class="sxs-lookup"><span data-stu-id="d9976-132">Certificate Requirements</span></span>

<span data-ttu-id="d9976-133">Als u referentie versleuteling wilt instellen, moet er een certificaat met een open bare sleutel beschikbaar zijn op het _doel knooppunt_ dat wordt **vertrouwd** door de computer die wordt gebruikt voor het ontwerpen van de DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="d9976-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span> <span data-ttu-id="d9976-134">Aan deze open bare-sleutel certificaat kunnen specifieke vereisten worden gebruikt voor het versleutelen van DSC-referenties:</span><span class="sxs-lookup"><span data-stu-id="d9976-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>

1. <span data-ttu-id="d9976-135">**Sleutel gebruik**:</span><span class="sxs-lookup"><span data-stu-id="d9976-135">**Key Usage**:</span></span>
   - <span data-ttu-id="d9976-136">Moet het volgende bevatten: ' KeyEncipherment ' en ' DataEncipherment '.</span><span class="sxs-lookup"><span data-stu-id="d9976-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="d9976-137">Mag _niet_ bevatten: ' digitale hand tekening '.</span><span class="sxs-lookup"><span data-stu-id="d9976-137">Should _not_ contain: 'Digital Signature'.</span></span>
2. <span data-ttu-id="d9976-138">**Uitgebreid sleutel gebruik**:</span><span class="sxs-lookup"><span data-stu-id="d9976-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="d9976-139">Moet het volgende bevatten: document Encryption (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="d9976-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="d9976-140">Mag _niet_ bevatten: Client verificatie (1.3.6.1.5.5.7.3.2) en Server verificatie (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="d9976-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
3. <span data-ttu-id="d9976-141">De persoonlijke sleutel voor het certificaat is beschikbaar op de \* doel-Node_.</span><span class="sxs-lookup"><span data-stu-id="d9976-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
4. <span data-ttu-id="d9976-142">De **provider** van het certificaat moet micro soft RSA SChannel Cryptographic Provider zijn.</span><span class="sxs-lookup"><span data-stu-id="d9976-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9976-143">Hoewel u een certificaat met een sleutel gebruik van digitale hand tekening of een van de EKU voor authenticatie kunt gebruiken, is het mogelijk dat de versleutelings sleutel eenvoudiger te gebruiken is en kwetsbaar is voor aanvallen.</span><span class="sxs-lookup"><span data-stu-id="d9976-143">Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="d9976-144">Het is dus best practice een certificaat te gebruiken dat specifiek is gemaakt voor het beveiligen van DSC-referenties die deze sleutel gebruik en Eku's weglaten.</span><span class="sxs-lookup"><span data-stu-id="d9976-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="d9976-145">Elk bestaand certificaat op het _doel knooppunt_ dat voldoet aan deze criteria kan worden gebruikt voor het beveiligen van DSC-referenties.</span><span class="sxs-lookup"><span data-stu-id="d9976-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="d9976-146">Certificaat maken</span><span class="sxs-lookup"><span data-stu-id="d9976-146">Certificate creation</span></span>

<span data-ttu-id="d9976-147">Er zijn twee benaderingen die u kunt nemen om het vereiste versleutelings certificaat (openbaar-persoonlijk sleutel paar) te maken en te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d9976-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="d9976-148">Maken op het **doel knooppunt** en alleen de open bare sleutel exporteren naar het **ontwerp knooppunt**</span><span class="sxs-lookup"><span data-stu-id="d9976-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="d9976-149">Maken op het **ontwerp knooppunt** en het volledige sleutel paar exporteren naar het **doel knooppunt**</span><span class="sxs-lookup"><span data-stu-id="d9976-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="d9976-150">Methode 1 wordt aanbevolen omdat de persoonlijke sleutel die wordt gebruikt voor het ontsleutelen van referenties in de MOF te allen tijde op het doel knooppunt blijft.</span><span class="sxs-lookup"><span data-stu-id="d9976-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>

### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="d9976-151">Het certificaat maken op het doel knooppunt</span><span class="sxs-lookup"><span data-stu-id="d9976-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="d9976-152">De persoonlijke sleutel moet geheim blijven, omdat deze wordt gebruikt voor het ontsleutelen van de MOF op het **doel knooppunt** de eenvoudigste manier om dat te doen, is door het certificaat voor de persoonlijke sleutel te maken op het **doel knooppunt**en het certificaat van de **open bare sleutel** te kopiëren naar de computer die wordt gebruikt om de DSC-configuratie te schrijven naar een MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="d9976-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span> <span data-ttu-id="d9976-153">Het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="d9976-153">The following example:</span></span>

1. <span data-ttu-id="d9976-154">Hiermee maakt u een certificaat op het **doel knooppunt**</span><span class="sxs-lookup"><span data-stu-id="d9976-154">creates a certificate on the **Target node**</span></span>
2. <span data-ttu-id="d9976-155">exporteert het certificaat van de open bare sleutel op het **doel knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="d9976-155">exports the public key certificate on the **Target node**.</span></span>
3. <span data-ttu-id="d9976-156">Hiermee wordt het certificaat van de open bare sleutel in **het certificaat archief van het** **ontwerp knooppunt**geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="d9976-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="d9976-157">Op het doel knooppunt: het certificaat maken en exporteren</span><span class="sxs-lookup"><span data-stu-id="d9976-157">On the Target Node: create and export the certificate</span></span>

> <span data-ttu-id="d9976-158">Doel knooppunt: Windows Server 2016 en Windows 10</span><span class="sxs-lookup"><span data-stu-id="d9976-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="d9976-159">Na het exporteren moet `DscPublicKey.cer` de worden gekopieerd naar het **ontwerp knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="d9976-159">Once exported, the `DscPublicKey.cer` would need to be copied to the **Authoring Node**.</span></span>

> <span data-ttu-id="d9976-160">Doel knooppunt: Windows Server 2012 R2/Windows 8,1 en eerder</span><span class="sxs-lookup"><span data-stu-id="d9976-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="d9976-161">Omdat de `New-SelfSignedCertificate` cmdlet op Windows-besturings systemen vóór Windows 10 en windows server 2016 niet de **type** parameter ondersteunt, is een alternatieve methode voor het maken van dit certificaat vereist op deze besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="d9976-161">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="d9976-162">In dit geval kunt u of `makecert.exe` `certutil.exe` gebruiken om het certificaat te maken.</span><span class="sxs-lookup"><span data-stu-id="d9976-162">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="d9976-163">Een alternatieve methode is [het script New-SelfSignedCertificateEx. ps1 te downloaden uit het micro soft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) en dit te gebruiken om in plaats daarvan het certificaat te maken:</span><span class="sxs-lookup"><span data-stu-id="d9976-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

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

<span data-ttu-id="d9976-164">Na het exporteren moet ```DscPublicKey.cer``` de worden gekopieerd naar het **ontwerp knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="d9976-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="d9976-165">Op het ontwerp knooppunt: de open bare sleutel van het certificaat importeren</span><span class="sxs-lookup"><span data-stu-id="d9976-165">On the Authoring Node: import the cert's public key</span></span>

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="d9976-166">Het certificaat maken op het ontwerp knooppunt</span><span class="sxs-lookup"><span data-stu-id="d9976-166">Creating the Certificate on the Authoring Node</span></span>

<span data-ttu-id="d9976-167">Het versleutelings certificaat kan ook worden gemaakt op het **ontwerp knooppunt**, met de **persoonlijke sleutel** geëxporteerd als een pfx-bestand en vervolgens worden geïmporteerd op het **doel knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="d9976-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span> <span data-ttu-id="d9976-168">Dit is de huidige methode voor het implementeren van DSC-referentie versleuteling op _nano server_.</span><span class="sxs-lookup"><span data-stu-id="d9976-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span> <span data-ttu-id="d9976-169">Hoewel de PFX met een wacht woord is beveiligd, moet deze tijdens de overdracht veilig worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="d9976-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span> <span data-ttu-id="d9976-170">Het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="d9976-170">The following example:</span></span>

1. <span data-ttu-id="d9976-171">Hiermee maakt u een certificaat op het **ontwerp knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="d9976-171">creates a certificate on the **Authoring node**.</span></span>
2. <span data-ttu-id="d9976-172">exporteert het certificaat inclusief de persoonlijke sleutel op het **ontwerp knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="d9976-172">exports the certificate including the private key on the **Authoring node**.</span></span>
3. <span data-ttu-id="d9976-173">Hiermee verwijdert u de persoonlijke sleutel van het **ontwerp knooppunt**, maar behoudt u het certificaat voor de open bare sleutel in de **mijn** Store.</span><span class="sxs-lookup"><span data-stu-id="d9976-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
4. <span data-ttu-id="d9976-174">importeert het certificaat van de persoonlijke sleutel in het certificaat archief mijn (persoonlijk) op het **doel knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="d9976-174">imports the private key certificate into the My(Personal) certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="d9976-175">het moet worden toegevoegd aan het hoofd archief zodat het wordt vertrouwd door het **doel knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="d9976-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="d9976-176">Op het ontwerp knooppunt: het certificaat maken en exporteren</span><span class="sxs-lookup"><span data-stu-id="d9976-176">On the Authoring Node: create and export the certificate</span></span>

> <span data-ttu-id="d9976-177">Doel knooppunt: Windows Server 2016 en Windows 10</span><span class="sxs-lookup"><span data-stu-id="d9976-177">Target Node: Windows Server 2016 and Windows 10</span></span>

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

<span data-ttu-id="d9976-178">Na het exporteren moet `DscPrivateKey.pfx` de worden gekopieerd naar het **doel knooppunt**.</span><span class="sxs-lookup"><span data-stu-id="d9976-178">Once exported, the `DscPrivateKey.pfx` would need to be copied to the **Target Node**.</span></span>

> <span data-ttu-id="d9976-179">Doel knooppunt: Windows Server 2012 R2/Windows 8,1 en eerder</span><span class="sxs-lookup"><span data-stu-id="d9976-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="d9976-180">Omdat de `New-SelfSignedCertificate` cmdlet op Windows-besturings systemen vóór Windows 10 en windows server 2016 niet de **type** parameter ondersteunt, is een alternatieve methode voor het maken van dit certificaat vereist op deze besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="d9976-180">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="d9976-181">In dit geval kunt u of `makecert.exe` `certutil.exe` gebruiken om het certificaat te maken.</span><span class="sxs-lookup"><span data-stu-id="d9976-181">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="d9976-182">Een alternatieve methode is [het script New-SelfSignedCertificateEx. ps1 te downloaden uit het micro soft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) en dit te gebruiken om in plaats daarvan het certificaat te maken:</span><span class="sxs-lookup"><span data-stu-id="d9976-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

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

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="d9976-183">Op het doel knooppunt: de persoonlijke sleutel van het certificaat importeren als een vertrouwde basis</span><span class="sxs-lookup"><span data-stu-id="d9976-183">On the Target Node: import the cert's private key as a trusted root</span></span>

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="d9976-184">Configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="d9976-184">Configuration data</span></span>

<span data-ttu-id="d9976-185">In het configuratie gegevens blok worden de doel knooppunten gedefinieerd waarop moet worden toegepast, ongeacht of de referenties, de wijze van versleuteling en andere gegevens moeten worden versleuteld.</span><span class="sxs-lookup"><span data-stu-id="d9976-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="d9976-186">Zie de [configuratie-en omgevings gegevens scheiden](../configurations/configData.md)voor meer informatie over het gegevens blok van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="d9976-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](../configurations/configData.md).</span></span>

<span data-ttu-id="d9976-187">De volgende elementen kunnen worden geconfigureerd voor elk knoop punt dat is gerelateerd aan referentie versleuteling:</span><span class="sxs-lookup"><span data-stu-id="d9976-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>

- <span data-ttu-id="d9976-188">**Nodenaam** : de naam van het doel knooppunt waarvoor de referentie versleuteling wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="d9976-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
- <span data-ttu-id="d9976-189">**PsDscAllowPlainTextPassword** : Hiermee wordt aangegeven of niet-versleutelde referenties mogen worden door gegeven aan dit knoop punt.</span><span class="sxs-lookup"><span data-stu-id="d9976-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="d9976-190">Dit wordt **niet aanbevolen**.</span><span class="sxs-lookup"><span data-stu-id="d9976-190">This is **not recommended**.</span></span>
- <span data-ttu-id="d9976-191">**Vinger afdruk** : de vinger afdruk van het certificaat dat wordt gebruikt voor het ontsleutelen van de referenties in de DSC-configuratie op het _doel knooppunt_.</span><span class="sxs-lookup"><span data-stu-id="d9976-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="d9976-192">**Dit certificaat moet aanwezig zijn in het certificaat archief van de lokale computer op het doel knooppunt.**</span><span class="sxs-lookup"><span data-stu-id="d9976-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
- <span data-ttu-id="d9976-193">**CertificateFile** : het certificaat bestand (alleen de open bare sleutel) dat moet worden gebruikt om de referenties voor het _doel knooppunt_te versleutelen.</span><span class="sxs-lookup"><span data-stu-id="d9976-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="d9976-194">Dit moet een DER Encoded Binary X. 509 of base-64 Encoded X. 509-indeling certificaat bestand.</span><span class="sxs-lookup"><span data-stu-id="d9976-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="d9976-195">In dit voor beeld wordt een blok van een configuratie gegevens weer gegeven waarin een doel knooppunt wordt opgegeven voor het uitvoeren van de naam targetNode, het pad naar het certificaat bestand met de open bare sleutel (met de naam targetNode. CER) en de vinger afdruk voor de open bare sleutel.</span><span class="sxs-lookup"><span data-stu-id="d9976-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

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

## <a name="configuration-script"></a><span data-ttu-id="d9976-196">Configuratie script</span><span class="sxs-lookup"><span data-stu-id="d9976-196">Configuration script</span></span>

<span data-ttu-id="d9976-197">In het configuratie script zelf gebruikt u de `PsCredential` para meter om ervoor te zorgen dat referenties voor de kortst mogelijke tijd worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="d9976-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="d9976-198">Wanneer u het opgegeven voor beeld uitvoert, wordt u gevraagd referenties op te vragen en vervolgens het MOF-bestand te versleutelen met behulp van de CertificateFile die is gekoppeld aan het doel knooppunt in het configuratie gegevens blok.</span><span class="sxs-lookup"><span data-stu-id="d9976-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="d9976-199">In dit code voorbeeld wordt een bestand gekopieerd van een share die is beveiligd met een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d9976-199">This code example copies a file from a share that is secured to a user.</span></span>

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

## <a name="setting-up-decryption"></a><span data-ttu-id="d9976-200">Ontsleuteling instellen</span><span class="sxs-lookup"><span data-stu-id="d9976-200">Setting up decryption</span></span>

<span data-ttu-id="d9976-201">Voordat [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) u kunt werken, moet u de lokale Configuration Manager op elk doel knooppunt vertellen welk certificaat moet worden gebruikt om de referenties te ontsleutelen, met behulp van de CertificateID-resource om de vinger afdruk van het certificaat te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="d9976-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate's thumbprint.</span></span> <span data-ttu-id="d9976-202">In dit voor beeld wordt het juiste lokale certificaat gevonden (mogelijk moet u het aanpassen zodat het exacte certificaat wordt gevonden dat u wilt gebruiken):</span><span class="sxs-lookup"><span data-stu-id="d9976-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

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

<span data-ttu-id="d9976-203">Met het certificaat dat is geïdentificeerd door de vinger afdruk, kan het configuratie script worden bijgewerkt om de waarde te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="d9976-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

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

## <a name="running-the-configuration"></a><span data-ttu-id="d9976-204">De configuratie wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="d9976-204">Running the configuration</span></span>

<span data-ttu-id="d9976-205">Op dit moment kunt u de configuratie uitvoeren, waardoor twee bestanden worden uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="d9976-205">At this point, you can run the configuration, which will output two files:</span></span>

- <span data-ttu-id="d9976-206">Een meta. MOF-bestand waarmee de lokale Configuration Manager worden geconfigureerd om de referenties te ontsleutelen met behulp van het certificaat dat is opgeslagen in het archief van de lokale computer en wordt geïdentificeerd door de vinger afdruk.</span><span class="sxs-lookup"><span data-stu-id="d9976-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span>
  <span data-ttu-id="d9976-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx)Hiermee past u het bestand \*. meta. MOF toe.</span><span class="sxs-lookup"><span data-stu-id="d9976-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
- <span data-ttu-id="d9976-208">Een MOF-bestand dat de configuratie werkelijk toepast.</span><span class="sxs-lookup"><span data-stu-id="d9976-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="d9976-209">Start-DscConfiguration past de configuratie toe.</span><span class="sxs-lookup"><span data-stu-id="d9976-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="d9976-210">Met deze opdrachten voert u de volgende stappen uit:</span><span class="sxs-lookup"><span data-stu-id="d9976-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="d9976-211">In dit voor beeld wordt de DSC-configuratie naar het doel knooppunt gepusht.</span><span class="sxs-lookup"><span data-stu-id="d9976-211">This example would push the DSC configuration to the target node.</span></span> <span data-ttu-id="d9976-212">De DSC-configuratie kan ook worden toegepast met behulp van een DSC-pull-server, als er een beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="d9976-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="d9976-213">Zie [een DSC-pull-client instellen](pullClient.md) voor meer informatie over het Toep assen van DSC-configuraties met behulp van een DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="d9976-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="d9976-214">Voor beeld van referentie versleutelings module</span><span class="sxs-lookup"><span data-stu-id="d9976-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="d9976-215">Hier volgt een volledig voor beeld waarin al deze stappen zijn opgenomen, plus een helper-cmdlet waarmee de open bare sleutels worden geëxporteerd en gekopieerd:</span><span class="sxs-lookup"><span data-stu-id="d9976-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

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
