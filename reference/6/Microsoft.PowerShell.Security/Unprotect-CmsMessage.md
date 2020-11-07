---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/unprotect-cmsmessage?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unprotect-CmsMessage
ms.openlocfilehash: 449feaad9c5e92ba7a4824911b558061da9218e3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343603"
---
# <span data-ttu-id="716ba-103">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="716ba-103">Unprotect-CmsMessage</span></span>

## <span data-ttu-id="716ba-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="716ba-104">SYNOPSIS</span></span>
<span data-ttu-id="716ba-105">Ontsleutelt inhoud die is versleuteld met de syntaxis voor cryptografische berichten.</span><span class="sxs-lookup"><span data-stu-id="716ba-105">Decrypts content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="716ba-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="716ba-106">SYNTAX</span></span>

### <span data-ttu-id="716ba-107">ByWinEvent (standaard)</span><span class="sxs-lookup"><span data-stu-id="716ba-107">ByWinEvent (Default)</span></span>

```
Unprotect-CmsMessage [-EventLogRecord] <PSObject> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="716ba-108">ByContent</span><span class="sxs-lookup"><span data-stu-id="716ba-108">ByContent</span></span>

```
Unprotect-CmsMessage [-Content] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="716ba-109">ByPath</span><span class="sxs-lookup"><span data-stu-id="716ba-109">ByPath</span></span>

```
Unprotect-CmsMessage [-Path] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="716ba-110">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="716ba-110">ByLiteralPath</span></span>

```
Unprotect-CmsMessage [-LiteralPath] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="716ba-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="716ba-111">DESCRIPTION</span></span>

<span data-ttu-id="716ba-112">De `Unprotect-CmsMessage` cmdlet ontsleutelt inhoud die is versleuteld met de CMS-indeling (Cryptographic Message Syntax).</span><span class="sxs-lookup"><span data-stu-id="716ba-112">The `Unprotect-CmsMessage` cmdlet decrypts content that has been encrypted by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="716ba-113">De CMS-cmdlets ondersteunen de versleuteling en ontsleuteling van inhoud met behulp van de IETF-standaard indeling voor cryptografische berichten, zoals wordt beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="716ba-113">The CMS cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="716ba-114">De CMS-versleutelings standaard maakt gebruik van open bare-sleutel cryptografie, waarbij de sleutels worden gebruikt voor het versleutelen van inhoud (de open bare sleutel) en de sleutels die worden gebruikt voor het ontsleutelen van inhoud (de persoonlijke sleutel).</span><span class="sxs-lookup"><span data-stu-id="716ba-114">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="716ba-115">Uw open bare sleutel kan algemeen worden gedeeld en bevat geen gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="716ba-115">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="716ba-116">Als er inhoud is versleuteld met deze open bare sleutel, kan alleen uw persoonlijke sleutel worden ontsleuteld.</span><span class="sxs-lookup"><span data-stu-id="716ba-116">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="716ba-117">Zie voor meer informatie [open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="716ba-117">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="716ba-118">`Unprotect-CmsMessage` ontsleutelt inhoud die is versleuteld in de CMS-indeling.</span><span class="sxs-lookup"><span data-stu-id="716ba-118">`Unprotect-CmsMessage` decrypts content that has been encrypted in CMS format.</span></span> <span data-ttu-id="716ba-119">U kunt deze cmdlet uitvoeren om inhoud te ontsleutelen die u hebt versleuteld door de cmdlet uit te voeren `Protect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="716ba-119">You can run this cmdlet to decrypt content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="716ba-120">U kunt inhoud opgeven die u wilt ontsleutelen als een teken reeks, op basis van het versleutelings gebeurtenis logboek record-ID-nummer of op pad naar de versleutelde inhoud.</span><span class="sxs-lookup"><span data-stu-id="716ba-120">You can specify content that you want to decrypt as a string, by the encryption event log record ID number, or by path to the encrypted content.</span></span> <span data-ttu-id="716ba-121">De `Unprotect-CmsMessage` cmdlet retourneert de ontsleutelde inhoud.</span><span class="sxs-lookup"><span data-stu-id="716ba-121">The `Unprotect-CmsMessage` cmdlet returns the decrypted content.</span></span>

> [!NOTE]
> <span data-ttu-id="716ba-122">Deze cmdlet is alleen beschikbaar in Windows.</span><span class="sxs-lookup"><span data-stu-id="716ba-122">This cmdlet is only available on Windows.</span></span>

## <span data-ttu-id="716ba-123">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="716ba-123">EXAMPLES</span></span>

### <span data-ttu-id="716ba-124">Voor beeld 1: een bericht ontsleutelen</span><span class="sxs-lookup"><span data-stu-id="716ba-124">Example 1: Decrypt a message</span></span>

<span data-ttu-id="716ba-125">In het volgende voor beeld ontsleutelt u inhoud die zich op het letterlijke pad bevindt `C:\Users\Test\Documents\PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="716ba-125">In the following example, you decrypt content that is located at the literal path `C:\Users\Test\Documents\PowerShell`.</span></span> <span data-ttu-id="716ba-126">Voor de waarde van **de para meter** required gebruikt dit voor beeld de vinger afdruk van het certificaat dat is gebruikt om de versleuteling uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="716ba-126">For the value of the required **To** parameter, this example uses the thumbprint of the certificate that was used to perform the encryption.</span></span> <span data-ttu-id="716ba-127">Het gedecodeerde bericht ' Probeer de nieuwe opdracht alles afkraken ', is het resultaat.</span><span class="sxs-lookup"><span data-stu-id="716ba-127">The decrypted message, "Try the new Break All command," is the result.</span></span>

```powershell
$parameters = @{
  LiteralPath = "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
  To = '0f 8j b1 ab e0 ce 35 1d 67 d2 f2 6f a2 d2 00 cl 22 z9 m9 85'
}
Unprotect-CmsMessage -LiteralPath @parameters
```

```Output
Try the new Break All command
```

## <span data-ttu-id="716ba-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="716ba-128">PARAMETERS</span></span>

### <span data-ttu-id="716ba-129">-Inhoud</span><span class="sxs-lookup"><span data-stu-id="716ba-129">-Content</span></span>

<span data-ttu-id="716ba-130">Hiermee geeft u een versleutelde teken reeks of een variabele met een versleutelde teken reeks op.</span><span class="sxs-lookup"><span data-stu-id="716ba-130">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="716ba-131">-EventLogRecord</span><span class="sxs-lookup"><span data-stu-id="716ba-131">-EventLogRecord</span></span>

<span data-ttu-id="716ba-132">Hiermee geeft u een record-ID van het gebeurtenis logboek op die een CMS-versleutelings bewerking vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="716ba-132">Specifies an event log record ID that represents a CMS encryption operation.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByWinEvent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="716ba-133">-IncludeContext</span><span class="sxs-lookup"><span data-stu-id="716ba-133">-IncludeContext</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="716ba-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="716ba-134">-LiteralPath</span></span>

<span data-ttu-id="716ba-135">Hiermee geeft u het pad naar de versleutelde inhoud die u wilt ontsleutelen.</span><span class="sxs-lookup"><span data-stu-id="716ba-135">Specifies the path to encrypted content that you want to decrypt.</span></span> <span data-ttu-id="716ba-136">In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="716ba-136">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="716ba-137">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="716ba-137">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="716ba-138">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="716ba-138">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="716ba-139">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="716ba-139">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="716ba-140">-Path</span><span class="sxs-lookup"><span data-stu-id="716ba-140">-Path</span></span>

<span data-ttu-id="716ba-141">Hiermee geeft u het pad naar de versleutelde inhoud die u wilt ontsleutelen.</span><span class="sxs-lookup"><span data-stu-id="716ba-141">Specifies the path to encrypted content that you want to decrypt.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="716ba-142">-Naar</span><span class="sxs-lookup"><span data-stu-id="716ba-142">-To</span></span>

<span data-ttu-id="716ba-143">Hiermee geeft u een of meer CMS-bericht ontvangers, aangeduid met een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="716ba-143">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="716ba-144">Een echt certificaat (zoals opgehaald van de certificaat provider).</span><span class="sxs-lookup"><span data-stu-id="716ba-144">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="716ba-145">Het pad naar het bestand met het certificaat.</span><span class="sxs-lookup"><span data-stu-id="716ba-145">Path to the a file containing the certificate.</span></span>
- <span data-ttu-id="716ba-146">Pad naar een map met het certificaat.</span><span class="sxs-lookup"><span data-stu-id="716ba-146">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="716ba-147">Vinger afdruk van het certificaat (dat wordt gebruikt om te zoeken in het certificaat archief).</span><span class="sxs-lookup"><span data-stu-id="716ba-147">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="716ba-148">De onderwerpnaam van het certificaat (dat wordt gebruikt om te zoeken in het certificaat archief).</span><span class="sxs-lookup"><span data-stu-id="716ba-148">Subject name of the certificate (used to look in the certificate store).</span></span>

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="716ba-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="716ba-149">CommonParameters</span></span>

<span data-ttu-id="716ba-150">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="716ba-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="716ba-151">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="716ba-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="716ba-152">INVOER</span><span class="sxs-lookup"><span data-stu-id="716ba-152">INPUTS</span></span>

### <span data-ttu-id="716ba-153">System. Diagnostics. Event. Reader. EventLogRecord of System. String</span><span class="sxs-lookup"><span data-stu-id="716ba-153">System.Diagnostics.Eventing.Reader.EventLogRecord or System.String</span></span>

<span data-ttu-id="716ba-154">U kunt een object dat versleutelde inhoud bevat door sluizen naar `Unprotect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="716ba-154">You can pipe an object containing encrypted content to `Unprotect-CmsMessage`.</span></span>

## <span data-ttu-id="716ba-155">UITVOER</span><span class="sxs-lookup"><span data-stu-id="716ba-155">OUTPUTS</span></span>

### <span data-ttu-id="716ba-156">System. String</span><span class="sxs-lookup"><span data-stu-id="716ba-156">System.String</span></span>

<span data-ttu-id="716ba-157">Het niet-versleutelde bericht.</span><span class="sxs-lookup"><span data-stu-id="716ba-157">The unencrypted message.</span></span>

## <span data-ttu-id="716ba-158">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="716ba-158">NOTES</span></span>

<span data-ttu-id="716ba-159">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="716ba-159">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="716ba-160">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="716ba-160">RELATED LINKS</span></span>

[<span data-ttu-id="716ba-161">about_Providers</span><span class="sxs-lookup"><span data-stu-id="716ba-161">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="716ba-162">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="716ba-162">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="716ba-163">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="716ba-163">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)
