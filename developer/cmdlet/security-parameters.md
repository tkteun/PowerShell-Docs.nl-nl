---
title: Beveiligingsparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: bdf88de0258af75c01739f30a71fb4914cac3a9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849026"
---
# <a name="security-parameters"></a><span data-ttu-id="57f10-102">Beveiligingsparameters</span><span class="sxs-lookup"><span data-stu-id="57f10-102">Security Parameters</span></span>

<span data-ttu-id="57f10-103">De volgende tabel bevat de aanbevolen namen en de functionaliteit voor parameters die worden gebruikt om te voorzien van informatie over de beveiliging voor een bewerking, zoals parameters die sleutel en bevoegdheden certificaatgegevens opgeeft.</span><span class="sxs-lookup"><span data-stu-id="57f10-103">The following table lists the recommended names and functionality for parameters used to provide security information for an operation, such as parameters that specify certificate key and privilege information.</span></span>

<span data-ttu-id="57f10-104">ACL-gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-104">ACL Data type: String</span></span>

<span data-ttu-id="57f10-105">Deze parameter om op te geven van het toegangsniveau van de controle van de beveiliging voor een catalogus of voor een Uniform Resource Identifier (URI) implementeren.</span><span class="sxs-lookup"><span data-stu-id="57f10-105">Implement this parameter to specify the access control level of protection for a catalog or for a Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="57f10-106">CertBestand gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-106">CertFile Data type: String</span></span>

<span data-ttu-id="57f10-107">Deze parameter implementeren zodat de gebruiker kan de naam van een bestand met een van de volgende opgeven:</span><span class="sxs-lookup"><span data-stu-id="57f10-107">Implement this parameter so that the user can specify the name of a file that contains one of the following:</span></span>

- <span data-ttu-id="57f10-108">Een met Base64 of regels DER (Distinguished Encoding) gecodeerd x.509-certificaat</span><span class="sxs-lookup"><span data-stu-id="57f10-108">A Base64 or Distinguished Encoding Rules (DER) encoded x.509 certificate</span></span>

- <span data-ttu-id="57f10-109">Een Public Key Cryptography Standards (PKCS) #12-bestand met ten minste één certificaat en de sleutel</span><span class="sxs-lookup"><span data-stu-id="57f10-109">A Public Key Cryptography Standards (PKCS) #12 file that contains at least one certificate and key</span></span>

<span data-ttu-id="57f10-110">CertIssuerName gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-110">CertIssuerName Data type: String</span></span>

<span data-ttu-id="57f10-111">Deze parameter implementeren zodat de gebruiker kan de naam van de verlener van een certificaat opgeven of zodat de gebruiker kan een subtekenreeks opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-111">Implement this parameter so that the user can specify the name of the issuer of a certificate or so that the user can specify a substring.</span></span>

<span data-ttu-id="57f10-112">CertRequestFile Data type: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-112">CertRequestFile Data type: String</span></span>

<span data-ttu-id="57f10-113">Deze parameter om op te geven van de naam van een bestand met een met Base64- of DER-gecodeerd PKCS #10 certificaataanvraag implementeren.</span><span class="sxs-lookup"><span data-stu-id="57f10-113">Implement this parameter to specify the name of a file that contains a Base64 or DER-encoded PKCS #10 certificate request.</span></span>

<span data-ttu-id="57f10-114">CertSerialNumber gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-114">CertSerialNumber Data type: String</span></span>

<span data-ttu-id="57f10-115">Deze parameter om op te geven van het serienummer dat is uitgegeven door de certificeringsinstantie (CA) implementeren.</span><span class="sxs-lookup"><span data-stu-id="57f10-115">Implement this parameter to specify the serial number that was issued by the certification authority.</span></span>

<span data-ttu-id="57f10-116">CertStoreLocation gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-116">CertStoreLocation Data type: String</span></span>

<span data-ttu-id="57f10-117">Implementeer deze parameter zodat de gebruiker kan de locatie van het certificaatarchief opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-117">Implement this parameter so that the user can specify the location of the certificate store.</span></span> <span data-ttu-id="57f10-118">De locatie is doorgaans een bestandspad.</span><span class="sxs-lookup"><span data-stu-id="57f10-118">The location is typically a file path.</span></span>

<span data-ttu-id="57f10-119">CertSubjectName gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-119">CertSubjectName Data type: String</span></span>

<span data-ttu-id="57f10-120">Deze parameter implementeren zodat de gebruiker kan de verlener van een certificaat opgeven of zodat de gebruiker kan een subtekenreeks opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-120">Implement this parameter so that the user can specify the issuer of a certificate or so that the user can specify a substring.</span></span>

<span data-ttu-id="57f10-121">CertUsage gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-121">CertUsage Data type: String</span></span>

<span data-ttu-id="57f10-122">Deze parameter om op te geven van het gebruik van de sleutel of het uitgebreide sleutelgebruik implementeren.</span><span class="sxs-lookup"><span data-stu-id="57f10-122">Implement this parameter to specify the key usage or the enhanced key usage.</span></span> <span data-ttu-id="57f10-123">De sleutel kan worden weergegeven als een en ander maskeren, wat een object-id (OID), of een tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="57f10-123">The key can be represented as a bit mask, a bit, an object identifier (OID), or a string.</span></span>

<span data-ttu-id="57f10-124">Referentie-gegevenstype: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="57f10-124">Credential Data type: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span></span>

<span data-ttu-id="57f10-125">Implementeer deze parameter zodat de cmdlet wordt automatisch de gebruiker gevraagd om een gebruikersnaam of wachtwoord.</span><span class="sxs-lookup"><span data-stu-id="57f10-125">Implement this parameter so that the cmdlet will automatically prompt the user for a user name or password.</span></span> <span data-ttu-id="57f10-126">Een prompt voor zowel wordt weergegeven als een volledige referentie niet rechtstreeks worden verstrekt.</span><span class="sxs-lookup"><span data-stu-id="57f10-126">A prompt for both is displayed if a full credential is not supplied directly.</span></span>

<span data-ttu-id="57f10-127">CSP-naam-gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-127">CSPName Data type: String</span></span>

<span data-ttu-id="57f10-128">Implementeer deze parameter zodat de gebruiker kan de naam van de certificaat-provider (CSP) opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-128">Implement this parameter so that the user can specify the name of the certificate service provider (CSP).</span></span>

<span data-ttu-id="57f10-129">CSPType gegevenstype: Geheel getal</span><span class="sxs-lookup"><span data-stu-id="57f10-129">CSPType Data type: Integer</span></span>

<span data-ttu-id="57f10-130">Implementeer deze parameter zodat de gebruiker kan het type van de CSP opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-130">Implement this parameter so that the user can specify the type of CSP.</span></span>

<span data-ttu-id="57f10-131">Gegevens van het type groep: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-131">Group Data type: String</span></span>

<span data-ttu-id="57f10-132">Deze parameter implementeren zodat de gebruiker kan een verzameling van beveiligings-principals voor toegang tot opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-132">Implement this parameter so that the user can specify a collection of principals for access.</span></span> <span data-ttu-id="57f10-133">Zie voor meer informatie, de beschrijving van de `Principal` parameter.</span><span class="sxs-lookup"><span data-stu-id="57f10-133">For more information, see the description of the `Principal` parameter.</span></span>

<span data-ttu-id="57f10-134">KeyAlgorithm gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-134">KeyAlgorithm Data type: String</span></span>

<span data-ttu-id="57f10-135">Implementeer deze parameter zodat de gebruiker kan het genereren van sleutels-algoritme moet worden gebruikt voor beveiliging opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-135">Implement this parameter so that the user can specify the key generation algorithm to use for security.</span></span>

<span data-ttu-id="57f10-136">Naam van sleutelcontainer gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-136">KeyContainerName Data type: String</span></span>

<span data-ttu-id="57f10-137">Implementeer deze parameter zodat de gebruiker kan de naam van de sleutelcontainer opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-137">Implement this parameter so that the user can specify the name of the key container.</span></span>

<span data-ttu-id="57f10-138">Sleutellengte gegevenstype: Geheel getal</span><span class="sxs-lookup"><span data-stu-id="57f10-138">KeyLength Data type: Integer</span></span>

<span data-ttu-id="57f10-139">Implementeer deze parameter zodat de gebruiker de lengte van de sleutel in bits kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-139">Implement this parameter so that the user can specify the length of the key in bits.</span></span>

<span data-ttu-id="57f10-140">Bewerking gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-140">Operation Data type: String</span></span>

<span data-ttu-id="57f10-141">Implementeer deze parameter zodat de gebruiker kan een actie die kan worden uitgevoerd op een beveiligde object opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-141">Implement this parameter so that the user can specify an action that can be performed on a protected object.</span></span>

<span data-ttu-id="57f10-142">Principal-gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-142">Principal Data type: String</span></span>

<span data-ttu-id="57f10-143">Deze parameter implementeren zodat de gebruiker kan een unieke identificeerbare entiteit voor toegang tot opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-143">Implement this parameter so that the user can specify a unique identifiable entity for access.</span></span>

<span data-ttu-id="57f10-144">Bevoegdheden voor gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-144">Privilege Data type: String</span></span>

<span data-ttu-id="57f10-145">Implementeer deze parameter zodat de gebruiker kan het recht voor dat een cmdlet uit te voeren een bewerking voor een bepaalde entiteit moet opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-145">Implement this parameter so that the user can specify the right a cmdlet needs to perform an operation for a particular entity.</span></span>

<span data-ttu-id="57f10-146">Bevoegdheden gegevenstype: Matrix van bevoegdheden</span><span class="sxs-lookup"><span data-stu-id="57f10-146">Privileges Data type: Array of privileges</span></span>

<span data-ttu-id="57f10-147">Implementeer deze parameter zodat de gebruiker kan de rechten die een cmdlet uit te voeren van de bewerking voor een bepaalde vermelding moet opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-147">Implement this parameter so that the user can specify the rights that a cmdlet needs to perform its operation for a particular entry.</span></span>

<span data-ttu-id="57f10-148">Gegevenstype van de rol: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-148">Role Data type: String</span></span>

<span data-ttu-id="57f10-149">Implementeer deze parameter zodat de gebruiker kan een reeks bewerkingen die kunnen worden uitgevoerd door een entiteit opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-149">Implement this parameter so that the user can specify a set of operations that can be performed by an entity.</span></span>

<span data-ttu-id="57f10-150">SaveCred gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="57f10-150">SaveCred Data type: SwitchParameter</span></span>

<span data-ttu-id="57f10-151">Implementeer deze parameter zodat de referenties die zijn opgeslagen door de gebruiker worden gebruikt wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-151">Implement this parameter so that credentials that were previously saved by the user will be used when the parameter is specified.</span></span>

<span data-ttu-id="57f10-152">Het bereik van gegevens van het type: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-152">Scope Data type: String</span></span>

<span data-ttu-id="57f10-153">Implementeer deze parameter zodat de gebruiker kan de groep met beveiligde objecten voor de cmdlet opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-153">Implement this parameter so that the user can specify the group of protected objects for the cmdlet.</span></span>

<span data-ttu-id="57f10-154">SID Data type: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="57f10-154">SID Data type: String</span></span>

<span data-ttu-id="57f10-155">Implementeer deze parameter zodat de gebruiker een unieke id die staat voor een principal kan opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-155">Implement this parameter so that the user can specify a unique identifier that represents a principal.</span></span>

<span data-ttu-id="57f10-156">Vertrouwde gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="57f10-156">Trusted Data type: SwitchParameter</span></span>

<span data-ttu-id="57f10-157">Implementeer deze parameter zodat vertrouwensniveaus worden ondersteund wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-157">Implement this parameter so that trust levels are supported when the parameter is specified.</span></span>

<span data-ttu-id="57f10-158">TrustLevel gegevenstype: Trefwoord</span><span class="sxs-lookup"><span data-stu-id="57f10-158">TrustLevel Data type: Keyword</span></span>

<span data-ttu-id="57f10-159">Implementeer deze parameter zodat het vertrouwensniveau dat wordt ondersteund door de gebruiker kan opgeven.</span><span class="sxs-lookup"><span data-stu-id="57f10-159">Implement this parameter so that the user can specify the trust level that is supported.</span></span> <span data-ttu-id="57f10-160">Mogelijke waarden zijn bijvoorbeeld internet en intranet fulltrust.</span><span class="sxs-lookup"><span data-stu-id="57f10-160">For example, possible values include internet, intranet, and fulltrust.</span></span>

## <a name="see-also"></a><span data-ttu-id="57f10-161">Zie ook</span><span class="sxs-lookup"><span data-stu-id="57f10-161">See Also</span></span>

[<span data-ttu-id="57f10-162">Cmdlet-Parameters</span><span class="sxs-lookup"><span data-stu-id="57f10-162">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="57f10-163">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="57f10-163">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="57f10-164">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="57f10-164">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
