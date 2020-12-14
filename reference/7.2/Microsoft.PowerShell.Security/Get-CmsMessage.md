---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: 421b49139f4750787b6c1c04d8a41a624755109a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705856"
---
# <span data-ttu-id="71eaa-102">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="71eaa-102">Get-CmsMessage</span></span>

## <span data-ttu-id="71eaa-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="71eaa-103">SYNOPSIS</span></span>
<span data-ttu-id="71eaa-104">Hiermee wordt inhoud opgehaald die is versleuteld met de syntaxis voor cryptografische berichten.</span><span class="sxs-lookup"><span data-stu-id="71eaa-104">Gets content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="71eaa-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="71eaa-105">SYNTAX</span></span>

### <span data-ttu-id="71eaa-106">ByContent</span><span class="sxs-lookup"><span data-stu-id="71eaa-106">ByContent</span></span>

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### <span data-ttu-id="71eaa-107">ByPath</span><span class="sxs-lookup"><span data-stu-id="71eaa-107">ByPath</span></span>

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="71eaa-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="71eaa-108">ByLiteralPath</span></span>

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## <span data-ttu-id="71eaa-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="71eaa-109">DESCRIPTION</span></span>

<span data-ttu-id="71eaa-110">De `Get-CmsMessage` cmdlet haalt inhoud op die is versleuteld met de CMS-indeling (Cryptographic Message Syntax).</span><span class="sxs-lookup"><span data-stu-id="71eaa-110">The `Get-CmsMessage` cmdlet gets content that has been encrypted using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="71eaa-111">De CMS-cmdlets ondersteunen de versleuteling en ontsleuteling van inhoud met behulp van de IETF-indeling voor cryptografische beveiliging van berichten, zoals wordt beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="71eaa-111">The CMS cmdlets support encryption and decryption of content using the IETF format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="71eaa-112">De CMS-versleutelings standaard maakt gebruik van open bare-sleutel cryptografie, waarbij de sleutels worden gebruikt voor het versleutelen van inhoud (de open bare sleutel) en de sleutels die worden gebruikt voor het ontsleutelen van inhoud (de persoonlijke sleutel).</span><span class="sxs-lookup"><span data-stu-id="71eaa-112">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="71eaa-113">Uw open bare sleutel kan algemeen worden gedeeld en bevat geen gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="71eaa-113">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="71eaa-114">Als er inhoud is versleuteld met deze open bare sleutel, kan alleen uw persoonlijke sleutel worden ontsleuteld.</span><span class="sxs-lookup"><span data-stu-id="71eaa-114">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="71eaa-115">Zie voor meer informatie [open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="71eaa-115">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="71eaa-116">`Get-CmsMessage` Hiermee wordt inhoud opgehaald die is versleuteld in de CMS-indeling.</span><span class="sxs-lookup"><span data-stu-id="71eaa-116">`Get-CmsMessage` gets content that has been encrypted in CMS format.</span></span> <span data-ttu-id="71eaa-117">De inhoud wordt niet ontsleuteld of beveiligd.</span><span class="sxs-lookup"><span data-stu-id="71eaa-117">It does not decrypt or unprotect content.</span></span> <span data-ttu-id="71eaa-118">U kunt deze cmdlet uitvoeren om inhoud op te halen die u hebt versleuteld door de cmdlet uit te voeren `Protect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="71eaa-118">You can run this cmdlet to get content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="71eaa-119">U kunt inhoud opgeven die u wilt ontsleutelen als een teken reeks of op basis van het pad naar de versleutelde inhoud.</span><span class="sxs-lookup"><span data-stu-id="71eaa-119">You can specify content that you want to decrypt as a string, or by path to the encrypted content.</span></span> <span data-ttu-id="71eaa-120">U kunt de resultaten van `Get-CmsMessage` voor het `Unprotect-CmsMessage` ontsleutelen van de inhoud door geven, mits u informatie hebt over het certificaat voor document versleuteling dat is gebruikt voor het versleutelen van de inhoud.</span><span class="sxs-lookup"><span data-stu-id="71eaa-120">You can pipe the results of `Get-CmsMessage` to `Unprotect-CmsMessage` to decrypt the content, provided that you have information about the document encryption certificate that was used to encrypt the content.</span></span>

<span data-ttu-id="71eaa-121">Ondersteuning voor Linux en macOS is toegevoegd in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="71eaa-121">Support for Linux and macOS was added in PowerShell 7.1.</span></span>

## <span data-ttu-id="71eaa-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="71eaa-122">EXAMPLES</span></span>

### <span data-ttu-id="71eaa-123">Voor beeld 1: versleutelde inhoud ophalen</span><span class="sxs-lookup"><span data-stu-id="71eaa-123">Example 1: Get encrypted content</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg.Content
```

```Output
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMBFWxlZWhv
bG1AbGljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYP5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNXmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPRwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84AHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1AtDj7nSJc=
-----END CMS-----
```

<span data-ttu-id="71eaa-124">Met deze opdracht wordt versleutelde inhoud op C:\Users\Test\Documents\PowerShell\Future_Plans.txt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="71eaa-124">This command gets encrypted content located at C:\Users\Test\Documents\PowerShell\Future_Plans.txt.</span></span>

### <span data-ttu-id="71eaa-125">Voor beeld 2: door pipe versleutelde inhoud naar Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="71eaa-125">Example 2: Pipe encrypted content to Unprotect-CmsMessage</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

<span data-ttu-id="71eaa-126">Met deze opdracht pipet u de resultaten van de `Get-CmsMessage` cmdlet van voor beeld 1 naar `Unprotect-CmsMessage` , om het bericht te ontsleutelen en te lezen in tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="71eaa-126">This command pipes the results of the `Get-CmsMessage` cmdlet from Example 1 to `Unprotect-CmsMessage`, to decrypt the message and read it in plain text.</span></span> <span data-ttu-id="71eaa-127">In dit geval is de waarde van de para meter **aan** de waarde van de onderwerpregel van het versleutelde certificaat.</span><span class="sxs-lookup"><span data-stu-id="71eaa-127">In this case, the value of the **To** parameter is the value of the encrypting certificate's Subject line.</span></span> <span data-ttu-id="71eaa-128">Het gedecodeerde bericht ' Probeer de nieuwe opdracht alles afkraken ', is het resultaat.</span><span class="sxs-lookup"><span data-stu-id="71eaa-128">The decrypted message, "Try the new Break All command," is the result.</span></span>

## <span data-ttu-id="71eaa-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="71eaa-129">PARAMETERS</span></span>

### <span data-ttu-id="71eaa-130">-Inhoud</span><span class="sxs-lookup"><span data-stu-id="71eaa-130">-Content</span></span>

<span data-ttu-id="71eaa-131">Hiermee geeft u een versleutelde teken reeks of een variabele met een versleutelde teken reeks op.</span><span class="sxs-lookup"><span data-stu-id="71eaa-131">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="71eaa-132">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="71eaa-132">-LiteralPath</span></span>

<span data-ttu-id="71eaa-133">Hiermee geeft u het pad op naar versleutelde inhoud die u wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="71eaa-133">Specifies the path to encrypted content that you want to get.</span></span> <span data-ttu-id="71eaa-134">In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="71eaa-134">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="71eaa-135">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="71eaa-135">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="71eaa-136">Als het pad escape tekens bevat, plaatst u dit tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="71eaa-136">If the path includes escape characters, enclose each one in single quotation marks.</span></span>
<span data-ttu-id="71eaa-137">Enkele aanhalings tekens geven aan dat Power shell niet-Inge sloten karakters mag interpreteren als escape-tekens.</span><span class="sxs-lookup"><span data-stu-id="71eaa-137">Single quotation marks tell PowerShell not to interpret enclosed characters as escape characters.</span></span>

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

### <span data-ttu-id="71eaa-138">-Path</span><span class="sxs-lookup"><span data-stu-id="71eaa-138">-Path</span></span>

<span data-ttu-id="71eaa-139">Hiermee geeft u het pad naar de versleutelde inhoud die u wilt ontsleutelen.</span><span class="sxs-lookup"><span data-stu-id="71eaa-139">Specifies the path to encrypted content that you want to decrypt.</span></span>

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

### <span data-ttu-id="71eaa-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="71eaa-140">CommonParameters</span></span>

<span data-ttu-id="71eaa-141">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="71eaa-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="71eaa-142">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71eaa-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="71eaa-143">INVOER</span><span class="sxs-lookup"><span data-stu-id="71eaa-143">INPUTS</span></span>

## <span data-ttu-id="71eaa-144">UITVOER</span><span class="sxs-lookup"><span data-stu-id="71eaa-144">OUTPUTS</span></span>

## <span data-ttu-id="71eaa-145">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="71eaa-145">NOTES</span></span>

## <span data-ttu-id="71eaa-146">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="71eaa-146">RELATED LINKS</span></span>

[<span data-ttu-id="71eaa-147">about_Providers</span><span class="sxs-lookup"><span data-stu-id="71eaa-147">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="71eaa-148">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="71eaa-148">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)

[<span data-ttu-id="71eaa-149">Beveiliging opheffen-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="71eaa-149">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)

