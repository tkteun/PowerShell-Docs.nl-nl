---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: b8940ded189d822a5a2cd40773ef5146353611cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058995"
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a>Cmdlets voor Cryptographic Message-syntaxis (CMS)

De cmdlets voor Cryptographic Message-syntaxis ondersteunt versleuteling en ontsleuteling van inhoud met behulp van de IETF-standaard indeling voor het beveiligen van berichten cryptografisch zoals beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652).

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

De standaard CMS-versleuteling implementeert openbare-sleutelcryptografie, waarbij de sleutels worden gebruikt voor het versleutelen van inhoud (de *openbare sleutel*) en de sleutels die worden gebruikt om inhoud te ontsleutelen (de *privésleutel*) zijn gescheiden.

Uw openbare-sleutelcertificaat grote schaal kan worden gedeeld, en is geen gevoelige gegevens. Als de inhoud is versleuteld met deze openbare sleutel, kan alleen de persoonlijke sleutel worden gedecodeerd. Zie voor meer informatie, [openbare-sleutelcryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).

Certificaten voor bestandsversleuteling vereist om te worden herkend in PowerShell, een id unieke sleutelgebruik (EKU) om te bepalen of deze gegevens versleutelingscertificaten (zoals de id's voor 'Handtekening bij programmacode', 'Mail versleuteld').

Hier volgt een voorbeeld van het maken van een certificaat dat geschikt is voor Document-versleuteling:

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

Voer vervolgens het volgende uit:
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

En u kunt nu versleutelen en ontsleutelen van inhoud:

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

Een parameter van het type **CMSMessageRecipient** biedt ondersteuning voor id's in de volgende indelingen:
- Een werkelijke-certificaat (als opgehaald uit de certificaatprovider)
- Pad naar het een bestand met het certificaat
- Pad naar een map met het certificaat
- Vingerafdruk van het certificaat (gebruikt om te zoeken in het certificaatarchief)
- Naam van het onderwerp van het certificaat (gebruikt om te zoeken in het certificaatarchief)

Als u wilt weergeven versleutelingscertificaten document in de certificaatprovider, kunt u de **- DocumentEncryptionCert** dynamische parameter:

```powershell
dir -DocumentEncryptionCert
```
