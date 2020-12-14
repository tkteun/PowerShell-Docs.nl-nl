---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/unprotect-cmsmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unprotect-CmsMessage
ms.openlocfilehash: ed1c80a70e8fc51c242be6f9369f0a0bd44cb9c8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706169"
---
# <span data-ttu-id="853f4-102">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="853f4-102">Unprotect-CmsMessage</span></span>

## <span data-ttu-id="853f4-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="853f4-103">SYNOPSIS</span></span>
<span data-ttu-id="853f4-104">Ontsleutelt inhoud die is versleuteld met de syntaxis voor cryptografische berichten.</span><span class="sxs-lookup"><span data-stu-id="853f4-104">Decrypts content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="853f4-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="853f4-105">SYNTAX</span></span>

### <span data-ttu-id="853f4-106">ByWinEvent (standaard)</span><span class="sxs-lookup"><span data-stu-id="853f4-106">ByWinEvent (Default)</span></span>

```
Unprotect-CmsMessage [-EventLogRecord] <PSObject> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="853f4-107">ByContent</span><span class="sxs-lookup"><span data-stu-id="853f4-107">ByContent</span></span>

```
Unprotect-CmsMessage [-Content] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="853f4-108">ByPath</span><span class="sxs-lookup"><span data-stu-id="853f4-108">ByPath</span></span>

```
Unprotect-CmsMessage [-Path] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="853f4-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="853f4-109">ByLiteralPath</span></span>

```
Unprotect-CmsMessage [-LiteralPath] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="853f4-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="853f4-110">DESCRIPTION</span></span>

<span data-ttu-id="853f4-111">De `Unprotect-CmsMessage` cmdlet ontsleutelt inhoud die is versleuteld met de CMS-indeling (Cryptographic Message Syntax).</span><span class="sxs-lookup"><span data-stu-id="853f4-111">The `Unprotect-CmsMessage` cmdlet decrypts content that has been encrypted by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="853f4-112">De CMS-cmdlets ondersteunen de versleuteling en ontsleuteling van inhoud met behulp van de IETF-standaard indeling voor cryptografische berichten, zoals wordt beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="853f4-112">The CMS cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="853f4-113">De CMS-versleutelings standaard maakt gebruik van open bare-sleutel cryptografie, waarbij de sleutels worden gebruikt voor het versleutelen van inhoud (de open bare sleutel) en de sleutels die worden gebruikt voor het ontsleutelen van inhoud (de persoonlijke sleutel).</span><span class="sxs-lookup"><span data-stu-id="853f4-113">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="853f4-114">Uw open bare sleutel kan algemeen worden gedeeld en bevat geen gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="853f4-114">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="853f4-115">Als er inhoud is versleuteld met deze open bare sleutel, kan alleen uw persoonlijke sleutel worden ontsleuteld.</span><span class="sxs-lookup"><span data-stu-id="853f4-115">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="853f4-116">Zie voor meer informatie [open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="853f4-116">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="853f4-117">`Unprotect-CmsMessage` ontsleutelt inhoud die is versleuteld in de CMS-indeling.</span><span class="sxs-lookup"><span data-stu-id="853f4-117">`Unprotect-CmsMessage` decrypts content that has been encrypted in CMS format.</span></span> <span data-ttu-id="853f4-118">U kunt deze cmdlet uitvoeren om inhoud te ontsleutelen die u hebt versleuteld door de cmdlet uit te voeren `Protect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="853f4-118">You can run this cmdlet to decrypt content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="853f4-119">U kunt inhoud opgeven die u wilt ontsleutelen als een teken reeks, op basis van het versleutelings gebeurtenis logboek record-ID-nummer of op pad naar de versleutelde inhoud.</span><span class="sxs-lookup"><span data-stu-id="853f4-119">You can specify content that you want to decrypt as a string, by the encryption event log record ID number, or by path to the encrypted content.</span></span> <span data-ttu-id="853f4-120">De `Unprotect-CmsMessage` cmdlet retourneert de ontsleutelde inhoud.</span><span class="sxs-lookup"><span data-stu-id="853f4-120">The `Unprotect-CmsMessage` cmdlet returns the decrypted content.</span></span>

<span data-ttu-id="853f4-121">Ondersteuning voor Linux en macOS is toegevoegd in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="853f4-121">Support for Linux and macOS was added in PowerShell 7.1.</span></span>

## <span data-ttu-id="853f4-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="853f4-122">EXAMPLES</span></span>

### <span data-ttu-id="853f4-123">Voor beeld 1: een bericht ontsleutelen</span><span class="sxs-lookup"><span data-stu-id="853f4-123">Example 1: Decrypt a message</span></span>

<span data-ttu-id="853f4-124">In het volgende voor beeld ontsleutelt u inhoud die zich op het letterlijke pad bevindt `C:\Users\Test\Documents\PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="853f4-124">In the following example, you decrypt content that is located at the literal path `C:\Users\Test\Documents\PowerShell`.</span></span> <span data-ttu-id="853f4-125">Voor de waarde van **de para meter** required gebruikt dit voor beeld de vinger afdruk van het certificaat dat is gebruikt om de versleuteling uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="853f4-125">For the value of the required **To** parameter, this example uses the thumbprint of the certificate that was used to perform the encryption.</span></span> <span data-ttu-id="853f4-126">Het gedecodeerde bericht ' Probeer de nieuwe opdracht alles afkraken ', is het resultaat.</span><span class="sxs-lookup"><span data-stu-id="853f4-126">The decrypted message, "Try the new Break All command," is the result.</span></span>

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

## <span data-ttu-id="853f4-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="853f4-127">PARAMETERS</span></span>

### <span data-ttu-id="853f4-128">-Inhoud</span><span class="sxs-lookup"><span data-stu-id="853f4-128">-Content</span></span>

<span data-ttu-id="853f4-129">Hiermee geeft u een versleutelde teken reeks of een variabele met een versleutelde teken reeks op.</span><span class="sxs-lookup"><span data-stu-id="853f4-129">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

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

### <span data-ttu-id="853f4-130">-EventLogRecord</span><span class="sxs-lookup"><span data-stu-id="853f4-130">-EventLogRecord</span></span>

<span data-ttu-id="853f4-131">Hiermee geeft u een record-ID van het gebeurtenis logboek op die een CMS-versleutelings bewerking vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="853f4-131">Specifies an event log record ID that represents a CMS encryption operation.</span></span>

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

### <span data-ttu-id="853f4-132">-IncludeContext</span><span class="sxs-lookup"><span data-stu-id="853f4-132">-IncludeContext</span></span>

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

### <span data-ttu-id="853f4-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="853f4-133">-LiteralPath</span></span>

<span data-ttu-id="853f4-134">Hiermee geeft u het pad naar de versleutelde inhoud die u wilt ontsleutelen.</span><span class="sxs-lookup"><span data-stu-id="853f4-134">Specifies the path to encrypted content that you want to decrypt.</span></span> <span data-ttu-id="853f4-135">In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="853f4-135">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="853f4-136">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="853f4-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="853f4-137">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="853f4-137">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="853f4-138">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="853f4-138">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="853f4-139">-Path</span><span class="sxs-lookup"><span data-stu-id="853f4-139">-Path</span></span>

<span data-ttu-id="853f4-140">Hiermee geeft u het pad naar de versleutelde inhoud die u wilt ontsleutelen.</span><span class="sxs-lookup"><span data-stu-id="853f4-140">Specifies the path to encrypted content that you want to decrypt.</span></span>

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

### <span data-ttu-id="853f4-141">-Naar</span><span class="sxs-lookup"><span data-stu-id="853f4-141">-To</span></span>

<span data-ttu-id="853f4-142">Hiermee geeft u een of meer CMS-bericht ontvangers, aangeduid met een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="853f4-142">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="853f4-143">Een echt certificaat (zoals opgehaald van de certificaat provider).</span><span class="sxs-lookup"><span data-stu-id="853f4-143">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="853f4-144">Het pad naar het bestand met het certificaat.</span><span class="sxs-lookup"><span data-stu-id="853f4-144">Path to the a file containing the certificate.</span></span>
- <span data-ttu-id="853f4-145">Pad naar een map met het certificaat.</span><span class="sxs-lookup"><span data-stu-id="853f4-145">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="853f4-146">Vinger afdruk van het certificaat (dat wordt gebruikt om te zoeken in het certificaat archief).</span><span class="sxs-lookup"><span data-stu-id="853f4-146">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="853f4-147">De onderwerpnaam van het certificaat (dat wordt gebruikt om te zoeken in het certificaat archief).</span><span class="sxs-lookup"><span data-stu-id="853f4-147">Subject name of the certificate (used to look in the certificate store).</span></span>

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

### <span data-ttu-id="853f4-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="853f4-148">CommonParameters</span></span>

<span data-ttu-id="853f4-149">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="853f4-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="853f4-150">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="853f4-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="853f4-151">INVOER</span><span class="sxs-lookup"><span data-stu-id="853f4-151">INPUTS</span></span>

### <span data-ttu-id="853f4-152">System. Diagnostics. Event. Reader. EventLogRecord of System. String</span><span class="sxs-lookup"><span data-stu-id="853f4-152">System.Diagnostics.Eventing.Reader.EventLogRecord or System.String</span></span>

<span data-ttu-id="853f4-153">U kunt een object dat versleutelde inhoud bevat door sluizen naar `Unprotect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="853f4-153">You can pipe an object containing encrypted content to `Unprotect-CmsMessage`.</span></span>

## <span data-ttu-id="853f4-154">UITVOER</span><span class="sxs-lookup"><span data-stu-id="853f4-154">OUTPUTS</span></span>

### <span data-ttu-id="853f4-155">System. String</span><span class="sxs-lookup"><span data-stu-id="853f4-155">System.String</span></span>

<span data-ttu-id="853f4-156">Het niet-versleutelde bericht.</span><span class="sxs-lookup"><span data-stu-id="853f4-156">The unencrypted message.</span></span>

## <span data-ttu-id="853f4-157">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="853f4-157">NOTES</span></span>

## <span data-ttu-id="853f4-158">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="853f4-158">RELATED LINKS</span></span>

[<span data-ttu-id="853f4-159">about_Providers</span><span class="sxs-lookup"><span data-stu-id="853f4-159">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="853f4-160">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="853f4-160">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="853f4-161">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="853f4-161">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)
