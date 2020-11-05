---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: 4f5600ebcff89e71fe310df203e5b794076f8323
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250497"
---
# <span data-ttu-id="3d527-103">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="3d527-103">Protect-CmsMessage</span></span>

## <span data-ttu-id="3d527-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3d527-104">SYNOPSIS</span></span>
<span data-ttu-id="3d527-105">Versleutelt inhoud met behulp van de syntaxis voor cryptografische berichten.</span><span class="sxs-lookup"><span data-stu-id="3d527-105">Encrypts content by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="3d527-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3d527-106">SYNTAX</span></span>

### <span data-ttu-id="3d527-107">ByContent (standaard)</span><span class="sxs-lookup"><span data-stu-id="3d527-107">ByContent (Default)</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="3d527-108">ByPath</span><span class="sxs-lookup"><span data-stu-id="3d527-108">ByPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### <span data-ttu-id="3d527-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="3d527-109">ByLiteralPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="3d527-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3d527-110">DESCRIPTION</span></span>

<span data-ttu-id="3d527-111">De `Protect-CmsMessage` cmdlet versleutelt inhoud door gebruik te maken van de indeling voor de syntaxis van cryptografische berichten (CMS).</span><span class="sxs-lookup"><span data-stu-id="3d527-111">The `Protect-CmsMessage` cmdlet encrypts content by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="3d527-112">De CMS-cmdlets ondersteunen de versleuteling en ontsleuteling van inhoud met behulp van de IETF-indeling zoals beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span><span class="sxs-lookup"><span data-stu-id="3d527-112">The CMS cmdlets support encryption and decryption of content using the IETF format as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="3d527-113">De CMS-versleutelings standaard maakt gebruik van open bare-sleutel cryptografie, waarbij de sleutels worden gebruikt voor het versleutelen van inhoud (de open bare sleutel) en de sleutels die worden gebruikt voor het ontsleutelen van inhoud (de persoonlijke sleutel).</span><span class="sxs-lookup"><span data-stu-id="3d527-113">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="3d527-114">Uw open bare sleutel kan algemeen worden gedeeld en bevat geen gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="3d527-114">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="3d527-115">Als er inhoud is versleuteld met deze open bare sleutel, kan alleen uw persoonlijke sleutel worden ontsleuteld.</span><span class="sxs-lookup"><span data-stu-id="3d527-115">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="3d527-116">Zie voor meer informatie [open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="3d527-116">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="3d527-117">Voordat u de cmdlet kunt uitvoeren `Protect-CmsMessage` , moet u een versleutelings certificaat instellen.</span><span class="sxs-lookup"><span data-stu-id="3d527-117">Before you can run the `Protect-CmsMessage` cmdlet, you must have an encryption certificate set up.</span></span>
<span data-ttu-id="3d527-118">Om te worden herkend in Power shell, is voor versleutelings certificaten een unieke[EKU](/windows/desktop/SecCrypto/eku)-id (Extended Key Usage) vereist om ze te identificeren als certificaten voor gegevens versleuteling (zoals de Id's voor ondertekening van programma code en versleutelde e-mail).</span><span class="sxs-lookup"><span data-stu-id="3d527-118">To be recognized in PowerShell, encryption certificates require a unique extended key usage ([EKU](/windows/desktop/SecCrypto/eku)) ID to identify them as data encryption certificates (such as the IDs for Code Signing and Encrypted Mail).</span></span> <span data-ttu-id="3d527-119">Zie voor beeld 1 in dit onderwerp voor een voor beeld van een certificaat dat kan worden gebruikt voor het versleutelen van documenten.</span><span class="sxs-lookup"><span data-stu-id="3d527-119">For an example of a certificate that would work for document encryption, see Example 1 in this topic.</span></span>

## <span data-ttu-id="3d527-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3d527-120">EXAMPLES</span></span>

### <span data-ttu-id="3d527-121">Voor beeld 1: een certificaat maken voor het versleutelen van inhoud</span><span class="sxs-lookup"><span data-stu-id="3d527-121">Example 1: Create a certificate for encrypting content</span></span>

<span data-ttu-id="3d527-122">Voordat u de cmdlet kunt uitvoeren `Protect-CmsMessage` , moet u een versleutelings certificaat maken.</span><span class="sxs-lookup"><span data-stu-id="3d527-122">Before you can run the `Protect-CmsMessage` cmdlet, you must create an encryption certificate.</span></span> <span data-ttu-id="3d527-123">Gebruik de volgende tekst om de naam op de regel onderwerp te wijzigen in uw naam, e-mail adres of andere id en sla het certificaat op in een bestand (zoals `DocumentEncryption.inf` in dit voor beeld).</span><span class="sxs-lookup"><span data-stu-id="3d527-123">Using the following text, change the name in the Subject line to your name, email, or other identifier, and save the certificate in a file (such as `DocumentEncryption.inf`, as shown in this example).</span></span>

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

### <span data-ttu-id="3d527-124">Voor beeld 2: een bericht versleutelen dat via e-mail is verzonden</span><span class="sxs-lookup"><span data-stu-id="3d527-124">Example 2: Encrypt a message sent by email</span></span>

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

<span data-ttu-id="3d527-125">In het volgende voor beeld versleutelt u een bericht, ' Hallo wereld ', door het te sluizen naar de `Protect-CmsMessage` cmdlet en vervolgens het versleutelde bericht in een variabele op te slaan.</span><span class="sxs-lookup"><span data-stu-id="3d527-125">In the following example, you encrypt a message, "Hello World", by piping it to the `Protect-CmsMessage` cmdlet, and then save the encrypted message in a variable.</span></span> <span data-ttu-id="3d527-126">De para meter **to** gebruikt de waarde van de regel onderwerp in het certificaat.</span><span class="sxs-lookup"><span data-stu-id="3d527-126">The **To** parameter uses the value of the Subject line in the certificate.</span></span>

### <span data-ttu-id="3d527-127">Voor beeld 3: document versleutelings certificaten weer geven</span><span class="sxs-lookup"><span data-stu-id="3d527-127">Example 3: View document encryption certificates</span></span>

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

<span data-ttu-id="3d527-128">Als u certificaten voor document versleuteling in de certificaat provider wilt weer geven, kunt u de dynamische para meter **DocumentEncryptionCert** van [Get-Child item](../Microsoft.PowerShell.Management/Get-ChildItem.md)toevoegen, die alleen beschikbaar is wanneer de certificaat provider wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="3d527-128">To view document encryption certificates in the certificate provider, you can add the **DocumentEncryptionCert** dynamic parameter of [Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md), available only when the certificate provider is loaded.</span></span>

## <span data-ttu-id="3d527-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3d527-129">PARAMETERS</span></span>

### <span data-ttu-id="3d527-130">-Inhoud</span><span class="sxs-lookup"><span data-stu-id="3d527-130">-Content</span></span>

<span data-ttu-id="3d527-131">Hiermee geeft u een **PSObject** die inhoud bevat die u wilt versleutelen.</span><span class="sxs-lookup"><span data-stu-id="3d527-131">Specifies a **PSObject** that contains content that you want to encrypt.</span></span> <span data-ttu-id="3d527-132">U kunt bijvoorbeeld de inhoud van een gebeurtenis bericht versleutelen en vervolgens de variabele met het bericht ( `$Event` in dit voor beeld) gebruiken als de waarde van de para meter **Content** : `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` .</span><span class="sxs-lookup"><span data-stu-id="3d527-132">For example, you can encrypt the content of an event message, and then use the variable containing the message (`$Event`, in this example) as the value of the **Content** parameter: `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1`.</span></span> <span data-ttu-id="3d527-133">U kunt de cmdlet ook gebruiken `Get-Content` om de inhoud van een bestand, zoals een micro soft Word-document, op te halen en de inhoud in een variabele op te slaan die u als de waarde van de para meter **Content** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3d527-133">You can also use the `Get-Content` cmdlet to get the contents of a file, such as a Microsoft Word document, and save the content in a variable that you use as the value of the **Content** parameter.</span></span>

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

### <span data-ttu-id="3d527-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3d527-134">-LiteralPath</span></span>

<span data-ttu-id="3d527-135">Hiermee geeft u het pad naar de inhoud die u wilt versleutelen.</span><span class="sxs-lookup"><span data-stu-id="3d527-135">Specifies the path to content that you want to encrypt.</span></span> <span data-ttu-id="3d527-136">In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="3d527-136">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="3d527-137">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="3d527-137">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="3d527-138">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="3d527-138">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="3d527-139">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="3d527-139">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="3d527-140">-Outfile</span><span class="sxs-lookup"><span data-stu-id="3d527-140">-OutFile</span></span>

<span data-ttu-id="3d527-141">Hiermee geeft u het pad en de bestands naam van een bestand waarnaar u de versleutelde inhoud wilt verzenden.</span><span class="sxs-lookup"><span data-stu-id="3d527-141">Specifies the path and file name of a file to which you want to send the encrypted content.</span></span>

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

### <span data-ttu-id="3d527-142">-Path</span><span class="sxs-lookup"><span data-stu-id="3d527-142">-Path</span></span>

<span data-ttu-id="3d527-143">Hiermee geeft u het pad naar de inhoud die u wilt versleutelen.</span><span class="sxs-lookup"><span data-stu-id="3d527-143">Specifies the path to content that you want to encrypt.</span></span>

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

### <span data-ttu-id="3d527-144">-Naar</span><span class="sxs-lookup"><span data-stu-id="3d527-144">-To</span></span>

<span data-ttu-id="3d527-145">Hiermee geeft u een of meer CMS-bericht ontvangers, aangeduid met een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="3d527-145">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="3d527-146">Een echt certificaat (zoals opgehaald van de certificaat provider).</span><span class="sxs-lookup"><span data-stu-id="3d527-146">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="3d527-147">Het pad naar het bestand met het certificaat.</span><span class="sxs-lookup"><span data-stu-id="3d527-147">Path to the file containing the certificate.</span></span>
- <span data-ttu-id="3d527-148">Pad naar een map met het certificaat.</span><span class="sxs-lookup"><span data-stu-id="3d527-148">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="3d527-149">Vinger afdruk van het certificaat (dat wordt gebruikt om te zoeken in het certificaat archief).</span><span class="sxs-lookup"><span data-stu-id="3d527-149">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="3d527-150">De onderwerpnaam van het certificaat (dat wordt gebruikt om te zoeken in het certificaat archief).</span><span class="sxs-lookup"><span data-stu-id="3d527-150">Subject name of the certificate (used to look in the certificate store).</span></span>

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

### <span data-ttu-id="3d527-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d527-151">CommonParameters</span></span>

<span data-ttu-id="3d527-152">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="3d527-152">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="3d527-153">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3d527-153">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3d527-154">INVOER</span><span class="sxs-lookup"><span data-stu-id="3d527-154">INPUTS</span></span>

## <span data-ttu-id="3d527-155">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3d527-155">OUTPUTS</span></span>

## <span data-ttu-id="3d527-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3d527-156">NOTES</span></span>

## <span data-ttu-id="3d527-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3d527-157">RELATED LINKS</span></span>

[<span data-ttu-id="3d527-158">about_Providers</span><span class="sxs-lookup"><span data-stu-id="3d527-158">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="3d527-159">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="3d527-159">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="3d527-160">Beveiliging opheffen-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="3d527-160">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)