---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: 57213b72bee5733f6e8089ff7dcbb9be82104d8a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705946"
---
# <span data-ttu-id="345dc-102">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="345dc-102">Protect-CmsMessage</span></span>

## <span data-ttu-id="345dc-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="345dc-103">SYNOPSIS</span></span>
<span data-ttu-id="345dc-104">Versleutelt inhoud met behulp van de syntaxis voor cryptografische berichten.</span><span class="sxs-lookup"><span data-stu-id="345dc-104">Encrypts content by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="345dc-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="345dc-105">SYNTAX</span></span>

### <span data-ttu-id="345dc-106">ByContent (standaard)</span><span class="sxs-lookup"><span data-stu-id="345dc-106">ByContent (Default)</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="345dc-107">ByPath</span><span class="sxs-lookup"><span data-stu-id="345dc-107">ByPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### <span data-ttu-id="345dc-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="345dc-108">ByLiteralPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="345dc-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="345dc-109">DESCRIPTION</span></span>

<span data-ttu-id="345dc-110">De `Protect-CmsMessage` cmdlet versleutelt inhoud door gebruik te maken van de indeling voor de syntaxis van cryptografische berichten (CMS).</span><span class="sxs-lookup"><span data-stu-id="345dc-110">The `Protect-CmsMessage` cmdlet encrypts content by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="345dc-111">De CMS-cmdlets ondersteunen de versleuteling en ontsleuteling van inhoud met behulp van de IETF-indeling zoals beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span><span class="sxs-lookup"><span data-stu-id="345dc-111">The CMS cmdlets support encryption and decryption of content using the IETF format as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="345dc-112">De CMS-versleutelings standaard maakt gebruik van open bare-sleutel cryptografie, waarbij de sleutels worden gebruikt voor het versleutelen van inhoud (de open bare sleutel) en de sleutels die worden gebruikt voor het ontsleutelen van inhoud (de persoonlijke sleutel).</span><span class="sxs-lookup"><span data-stu-id="345dc-112">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="345dc-113">Uw open bare sleutel kan algemeen worden gedeeld en bevat geen gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="345dc-113">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="345dc-114">Als er inhoud is versleuteld met deze open bare sleutel, kan alleen uw persoonlijke sleutel worden ontsleuteld.</span><span class="sxs-lookup"><span data-stu-id="345dc-114">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="345dc-115">Zie voor meer informatie [open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="345dc-115">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="345dc-116">Voordat u de cmdlet kunt uitvoeren `Protect-CmsMessage` , moet u een versleutelings certificaat instellen.</span><span class="sxs-lookup"><span data-stu-id="345dc-116">Before you can run the `Protect-CmsMessage` cmdlet, you must have an encryption certificate set up.</span></span>
<span data-ttu-id="345dc-117">Om te worden herkend in Power shell, is voor versleutelings certificaten een unieke[EKU](/windows/desktop/SecCrypto/eku)-id (Extended Key Usage) vereist om ze te identificeren als certificaten voor gegevens versleuteling (zoals de Id's voor ondertekening van programma code en versleutelde e-mail).</span><span class="sxs-lookup"><span data-stu-id="345dc-117">To be recognized in PowerShell, encryption certificates require a unique extended key usage ([EKU](/windows/desktop/SecCrypto/eku)) ID to identify them as data encryption certificates (such as the IDs for Code Signing and Encrypted Mail).</span></span> <span data-ttu-id="345dc-118">Zie voor beeld 1 in dit onderwerp voor een voor beeld van een certificaat dat kan worden gebruikt voor het versleutelen van documenten.</span><span class="sxs-lookup"><span data-stu-id="345dc-118">For an example of a certificate that would work for document encryption, see Example 1 in this topic.</span></span>

<span data-ttu-id="345dc-119">Ondersteuning voor Linux en macOS is toegevoegd in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="345dc-119">Support for Linux and macOS was added in PowerShell 7.1.</span></span>

## <span data-ttu-id="345dc-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="345dc-120">EXAMPLES</span></span>

### <span data-ttu-id="345dc-121">Voor beeld 1: een certificaat maken voor het versleutelen van inhoud</span><span class="sxs-lookup"><span data-stu-id="345dc-121">Example 1: Create a certificate for encrypting content</span></span>

<span data-ttu-id="345dc-122">Voordat u de cmdlet kunt uitvoeren `Protect-CmsMessage` , moet u een versleutelings certificaat maken.</span><span class="sxs-lookup"><span data-stu-id="345dc-122">Before you can run the `Protect-CmsMessage` cmdlet, you must create an encryption certificate.</span></span> <span data-ttu-id="345dc-123">Gebruik de volgende tekst om de naam op de regel onderwerp te wijzigen in uw naam, e-mail adres of andere id en sla het certificaat op in een bestand (zoals `DocumentEncryption.inf` in dit voor beeld).</span><span class="sxs-lookup"><span data-stu-id="345dc-123">Using the following text, change the name in the Subject line to your name, email, or other identifier, and save the certificate in a file (such as `DocumentEncryption.inf`, as shown in this example).</span></span>

```powershell
# Create .INF file for certreq
{[Version]
Signature = "$Windows NT$"

[Strings]
szOID_ENHANCED_KEY_USAGE = "2.5.29.37"
szOID_DOCUMENT_ENCRYPTION = "1.3.6.1.4.1.311.80.1"

[NewRequest]
Subject = "cn=youralias@emailaddress.com"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT_KEY_ENCIPHERMENT_KEY_USAGE | CERT_DATA_ENCIPHERMENT_KEY_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"

[Extensions]
%szOID_ENHANCED_KEY_USAGE% = "{text}%szOID_DOCUMENT_ENCRYPTION%"
} | Out-File -FilePath DocumentEncryption.inf

# After you have created your certificate file, run the following command to add
# the certificate file to the certificate store. Now you are ready to encrypt and
# decrypt content with the next two examples.
certreq.exe -new DocumentEncryption.inf DocumentEncryption.cer
```

### <span data-ttu-id="345dc-124">Voor beeld 2: een bericht versleutelen dat via e-mail is verzonden</span><span class="sxs-lookup"><span data-stu-id="345dc-124">Example 2: Encrypt a message sent by email</span></span>

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

<span data-ttu-id="345dc-125">In het volgende voor beeld versleutelt u een bericht, ' Hallo wereld ', door het te sluizen naar de `Protect-CmsMessage` cmdlet en vervolgens het versleutelde bericht in een variabele op te slaan.</span><span class="sxs-lookup"><span data-stu-id="345dc-125">In the following example, you encrypt a message, "Hello World", by piping it to the `Protect-CmsMessage` cmdlet, and then save the encrypted message in a variable.</span></span> <span data-ttu-id="345dc-126">De para meter **to** gebruikt de waarde van de regel onderwerp in het certificaat.</span><span class="sxs-lookup"><span data-stu-id="345dc-126">The **To** parameter uses the value of the Subject line in the certificate.</span></span>

### <span data-ttu-id="345dc-127">Voor beeld 3: document versleutelings certificaten weer geven</span><span class="sxs-lookup"><span data-stu-id="345dc-127">Example 3: View document encryption certificates</span></span>

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

<span data-ttu-id="345dc-128">Als u certificaten voor document versleuteling in de certificaat provider wilt weer geven, kunt u de dynamische para meter **DocumentEncryptionCert** van [Get-Child item](../Microsoft.PowerShell.Management/Get-ChildItem.md)toevoegen, die alleen beschikbaar is wanneer de certificaat provider wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="345dc-128">To view document encryption certificates in the certificate provider, you can add the **DocumentEncryptionCert** dynamic parameter of [Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md), available only when the certificate provider is loaded.</span></span>

## <span data-ttu-id="345dc-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="345dc-129">PARAMETERS</span></span>

### <span data-ttu-id="345dc-130">-Inhoud</span><span class="sxs-lookup"><span data-stu-id="345dc-130">-Content</span></span>

<span data-ttu-id="345dc-131">Hiermee geeft u een **PSObject** die inhoud bevat die u wilt versleutelen.</span><span class="sxs-lookup"><span data-stu-id="345dc-131">Specifies a **PSObject** that contains content that you want to encrypt.</span></span> <span data-ttu-id="345dc-132">U kunt bijvoorbeeld de inhoud van een gebeurtenis bericht versleutelen en vervolgens de variabele met het bericht ( `$Event` in dit voor beeld) gebruiken als de waarde van de para meter **Content** : `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` .</span><span class="sxs-lookup"><span data-stu-id="345dc-132">For example, you can encrypt the content of an event message, and then use the variable containing the message (`$Event`, in this example) as the value of the **Content** parameter: `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1`.</span></span> <span data-ttu-id="345dc-133">U kunt de cmdlet ook gebruiken `Get-Content` om de inhoud van een bestand, zoals een micro soft Word-document, op te halen en de inhoud in een variabele op te slaan die u als de waarde van de para meter **Content** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="345dc-133">You can also use the `Get-Content` cmdlet to get the contents of a file, such as a Microsoft Word document, and save the content in a variable that you use as the value of the **Content** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByContent
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="345dc-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="345dc-134">-LiteralPath</span></span>

<span data-ttu-id="345dc-135">Hiermee geeft u het pad naar de inhoud die u wilt versleutelen.</span><span class="sxs-lookup"><span data-stu-id="345dc-135">Specifies the path to content that you want to encrypt.</span></span> <span data-ttu-id="345dc-136">In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="345dc-136">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="345dc-137">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="345dc-137">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="345dc-138">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="345dc-138">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="345dc-139">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="345dc-139">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="345dc-140">-Outfile</span><span class="sxs-lookup"><span data-stu-id="345dc-140">-OutFile</span></span>

<span data-ttu-id="345dc-141">Hiermee geeft u het pad en de bestands naam van een bestand waarnaar u de versleutelde inhoud wilt verzenden.</span><span class="sxs-lookup"><span data-stu-id="345dc-141">Specifies the path and file name of a file to which you want to send the encrypted content.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="345dc-142">-Path</span><span class="sxs-lookup"><span data-stu-id="345dc-142">-Path</span></span>

<span data-ttu-id="345dc-143">Hiermee geeft u het pad naar de inhoud die u wilt versleutelen.</span><span class="sxs-lookup"><span data-stu-id="345dc-143">Specifies the path to content that you want to encrypt.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="345dc-144">-Naar</span><span class="sxs-lookup"><span data-stu-id="345dc-144">-To</span></span>

<span data-ttu-id="345dc-145">Hiermee geeft u een of meer CMS-bericht ontvangers, aangeduid met een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="345dc-145">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="345dc-146">Een echt certificaat (zoals opgehaald van de certificaat provider).</span><span class="sxs-lookup"><span data-stu-id="345dc-146">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="345dc-147">Het pad naar het bestand met het certificaat.</span><span class="sxs-lookup"><span data-stu-id="345dc-147">Path to the file containing the certificate.</span></span>
- <span data-ttu-id="345dc-148">Pad naar een map met het certificaat.</span><span class="sxs-lookup"><span data-stu-id="345dc-148">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="345dc-149">Vinger afdruk van het certificaat (dat wordt gebruikt om te zoeken in het certificaat archief).</span><span class="sxs-lookup"><span data-stu-id="345dc-149">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="345dc-150">De onderwerpnaam van het certificaat (dat wordt gebruikt om te zoeken in het certificaat archief).</span><span class="sxs-lookup"><span data-stu-id="345dc-150">Subject name of the certificate (used to look in the certificate store).</span></span>

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="345dc-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="345dc-151">CommonParameters</span></span>

<span data-ttu-id="345dc-152">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="345dc-152">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="345dc-153">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="345dc-153">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="345dc-154">INVOER</span><span class="sxs-lookup"><span data-stu-id="345dc-154">INPUTS</span></span>

## <span data-ttu-id="345dc-155">UITVOER</span><span class="sxs-lookup"><span data-stu-id="345dc-155">OUTPUTS</span></span>

## <span data-ttu-id="345dc-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="345dc-156">NOTES</span></span>

## <span data-ttu-id="345dc-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="345dc-157">RELATED LINKS</span></span>

[<span data-ttu-id="345dc-158">about_Providers</span><span class="sxs-lookup"><span data-stu-id="345dc-158">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="345dc-159">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="345dc-159">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="345dc-160">Beveiliging opheffen-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="345dc-160">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)
