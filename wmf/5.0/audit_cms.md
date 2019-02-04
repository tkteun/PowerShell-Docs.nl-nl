---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: b8940ded189d822a5a2cd40773ef5146353611cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686206"
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="25c69-102">Cmdlets voor Cryptographic Message-syntaxis (CMS)</span><span class="sxs-lookup"><span data-stu-id="25c69-102">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="25c69-103">De cmdlets voor Cryptographic Message-syntaxis ondersteunt versleuteling en ontsleuteling van inhoud met behulp van de IETF-standaard indeling voor het beveiligen van berichten cryptografisch zoals beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="25c69-103">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

<span data-ttu-id="25c69-104">De standaard CMS-versleuteling implementeert openbare-sleutelcryptografie, waarbij de sleutels worden gebruikt voor het versleutelen van inhoud (de *openbare sleutel*) en de sleutels die worden gebruikt om inhoud te ontsleutelen (de *privésleutel*) zijn gescheiden.</span><span class="sxs-lookup"><span data-stu-id="25c69-104">The CMS encryption standard implements public key cryptography, where the keys used to encrypt content (the *public key*) and the keys used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="25c69-105">Uw openbare-sleutelcertificaat grote schaal kan worden gedeeld, en is geen gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="25c69-105">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="25c69-106">Als de inhoud is versleuteld met deze openbare sleutel, kan alleen de persoonlijke sleutel worden gedecodeerd.</span><span class="sxs-lookup"><span data-stu-id="25c69-106">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="25c69-107">Zie voor meer informatie, [openbare-sleutelcryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="25c69-107">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="25c69-108">Certificaten voor bestandsversleuteling vereist om te worden herkend in PowerShell, een id unieke sleutelgebruik (EKU) om te bepalen of deze gegevens versleutelingscertificaten (zoals de id's voor 'Handtekening bij programmacode', 'Mail versleuteld').</span><span class="sxs-lookup"><span data-stu-id="25c69-108">To be recognized in PowerShell, encryption certificates require a unique key usage identifier (EKU) to identify them as data encryption certificates (like the identifiers for 'Code Signing', 'Encrypted Mail').</span></span>

<span data-ttu-id="25c69-109">Hier volgt een voorbeeld van het maken van een certificaat dat geschikt is voor Document-versleuteling:</span><span class="sxs-lookup"><span data-stu-id="25c69-109">Here is an example of creating a certificate that is good for Document Encryption:</span></span>

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

<span data-ttu-id="25c69-110">Voer vervolgens het volgende uit:</span><span class="sxs-lookup"><span data-stu-id="25c69-110">Then run:</span></span>
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

<span data-ttu-id="25c69-111">En u kunt nu versleutelen en ontsleutelen van inhoud:</span><span class="sxs-lookup"><span data-stu-id="25c69-111">And you can now encrypt and decrypt content:</span></span>

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

<span data-ttu-id="25c69-112">Een parameter van het type **CMSMessageRecipient** biedt ondersteuning voor id's in de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="25c69-112">Any parameter of type **CMSMessageRecipient** supports identifiers in the following formats:</span></span>
- <span data-ttu-id="25c69-113">Een werkelijke-certificaat (als opgehaald uit de certificaatprovider)</span><span class="sxs-lookup"><span data-stu-id="25c69-113">An actual certificate (as retrieved from the certificate provider)</span></span>
- <span data-ttu-id="25c69-114">Pad naar het een bestand met het certificaat</span><span class="sxs-lookup"><span data-stu-id="25c69-114">Path to the a file containing the certificate</span></span>
- <span data-ttu-id="25c69-115">Pad naar een map met het certificaat</span><span class="sxs-lookup"><span data-stu-id="25c69-115">Path to a directory containing the certificate</span></span>
- <span data-ttu-id="25c69-116">Vingerafdruk van het certificaat (gebruikt om te zoeken in het certificaatarchief)</span><span class="sxs-lookup"><span data-stu-id="25c69-116">Thumbprint of the certificate (used to look in the certificate store)</span></span>
- <span data-ttu-id="25c69-117">Naam van het onderwerp van het certificaat (gebruikt om te zoeken in het certificaatarchief)</span><span class="sxs-lookup"><span data-stu-id="25c69-117">Subject name of the certificate (used to look in the certificate store)</span></span>

<span data-ttu-id="25c69-118">Als u wilt weergeven versleutelingscertificaten document in de certificaatprovider, kunt u de **- DocumentEncryptionCert** dynamische parameter:</span><span class="sxs-lookup"><span data-stu-id="25c69-118">To view document encryption certificates in the certificate provider, you can use the **-DocumentEncryptionCert** dynamic parameter:</span></span>

```powershell
dir -DocumentEncryptionCert
```
