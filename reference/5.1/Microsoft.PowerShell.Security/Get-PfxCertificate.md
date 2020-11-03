---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: 1be3034b1fb44b1dce1a592ea5a2c1622b54d28f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250499"
---
# <span data-ttu-id="02e26-103">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="02e26-103">Get-PfxCertificate</span></span>

## <span data-ttu-id="02e26-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="02e26-104">SYNOPSIS</span></span>
<span data-ttu-id="02e26-105">Haalt informatie op over PFX-certificaat bestanden op de computer.</span><span class="sxs-lookup"><span data-stu-id="02e26-105">Gets information about PFX certificate files on the computer.</span></span>

## <span data-ttu-id="02e26-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="02e26-106">SYNTAX</span></span>

### <span data-ttu-id="02e26-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="02e26-107">ByPath (Default)</span></span>

```
Get-PfxCertificate [-FilePath] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="02e26-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="02e26-108">ByLiteralPath</span></span>

```
Get-PfxCertificate -LiteralPath <String[]> [<CommonParameters>]
```

## <span data-ttu-id="02e26-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="02e26-109">DESCRIPTION</span></span>

<span data-ttu-id="02e26-110">De `Get-PfxCertificate` cmdlet haalt een object op dat staat voor elk opgegeven pfx-certificaat bestand.</span><span class="sxs-lookup"><span data-stu-id="02e26-110">The `Get-PfxCertificate` cmdlet gets an object representing each specified PFX certificate file.</span></span>
<span data-ttu-id="02e26-111">Een PFX-bestand bevat zowel het certificaat als een persoonlijke sleutel.</span><span class="sxs-lookup"><span data-stu-id="02e26-111">A PFX file includes both the certificate and a private key.</span></span>

## <span data-ttu-id="02e26-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="02e26-112">EXAMPLES</span></span>

### <span data-ttu-id="02e26-113">Voor beeld 1: een PFX-certificaat ophalen</span><span class="sxs-lookup"><span data-stu-id="02e26-113">Example 1: Get a PFX certificate</span></span>

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

<span data-ttu-id="02e26-114">Met deze opdracht wordt informatie opgehaald over het bestand test. pfx op het systeem.</span><span class="sxs-lookup"><span data-stu-id="02e26-114">This command gets information about the Test.pfx certificate file on the system.</span></span>

### <span data-ttu-id="02e26-115">Voor beeld 2: een PFX-certificaat ophalen van een externe computer</span><span class="sxs-lookup"><span data-stu-id="02e26-115">Example 2: Get a PFX certificate from a remote computer</span></span>

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

<span data-ttu-id="02e26-116">Met deze opdracht wordt een PFX-certificaat bestand opgehaald van de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="02e26-116">This command gets a PFX certificate file from the Server01 remote computer.</span></span> <span data-ttu-id="02e26-117">Het gebruikt `Invoke-Command` om een `Get-PfxCertificate` opdracht op afstand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="02e26-117">It uses `Invoke-Command` to run a `Get-PfxCertificate` command remotely.</span></span>

<span data-ttu-id="02e26-118">Wanneer het PFX-certificaat bestand niet met een wacht woord is beveiligd, moet de waarde van de **authenticatie** parameter van `Invoke-Command` CredSSP zijn.</span><span class="sxs-lookup"><span data-stu-id="02e26-118">When the PFX certificate file is not password-protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="02e26-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="02e26-119">PARAMETERS</span></span>

### <span data-ttu-id="02e26-120">-FilePath</span><span class="sxs-lookup"><span data-stu-id="02e26-120">-FilePath</span></span>

<span data-ttu-id="02e26-121">Hiermee geeft u het volledige pad naar het PFX-bestand van het beveiligde bestand.</span><span class="sxs-lookup"><span data-stu-id="02e26-121">Specifies the full path to the PFX file of the secured file.</span></span> <span data-ttu-id="02e26-122">Als u een waarde voor deze para meter opgeeft, hoeft u niet `-FilePath` op de opdracht regel te typen.</span><span class="sxs-lookup"><span data-stu-id="02e26-122">If you specify a value for this parameter, it is not necessary to type `-FilePath` at the command line.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="02e26-123">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="02e26-123">-LiteralPath</span></span>

<span data-ttu-id="02e26-124">Het volledige pad naar het PFX-bestand van het beveiligde bestand.</span><span class="sxs-lookup"><span data-stu-id="02e26-124">The full path to the PFX file of the secured file.</span></span> <span data-ttu-id="02e26-125">In tegens telling tot het **bestandspad** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="02e26-125">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="02e26-126">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="02e26-126">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="02e26-127">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="02e26-127">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="02e26-128">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="02e26-128">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="02e26-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="02e26-129">CommonParameters</span></span>

<span data-ttu-id="02e26-130">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="02e26-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="02e26-131">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02e26-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="02e26-132">INVOER</span><span class="sxs-lookup"><span data-stu-id="02e26-132">INPUTS</span></span>

### <span data-ttu-id="02e26-133">System. String</span><span class="sxs-lookup"><span data-stu-id="02e26-133">System.String</span></span>

<span data-ttu-id="02e26-134">U kunt een teken reeks die een bestandspad bevat, door sluizen naar `Get-PfxCertificate` .</span><span class="sxs-lookup"><span data-stu-id="02e26-134">You can pipe a string that contains a file path to `Get-PfxCertificate`.</span></span>

## <span data-ttu-id="02e26-135">UITVOER</span><span class="sxs-lookup"><span data-stu-id="02e26-135">OUTPUTS</span></span>

### <span data-ttu-id="02e26-136">System. Security. Cryptography. X509Certificates. X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="02e26-136">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>

<span data-ttu-id="02e26-137">`Get-PfxCertificate` retourneert een object voor elk certificaat dat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="02e26-137">`Get-PfxCertificate` returns an object for each certificate that it gets.</span></span>

## <span data-ttu-id="02e26-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="02e26-138">NOTES</span></span>

<span data-ttu-id="02e26-139">Wanneer u de `Invoke-Command` cmdlet gebruikt om een `Get-PfxCertificate` opdracht extern uit te voeren en het pfx-certificaat bestand niet met een wacht woord is beveiligd, moet de waarde van de **authenticatie** parameter van `Invoke-Command` CredSSP zijn.</span><span class="sxs-lookup"><span data-stu-id="02e26-139">When using the `Invoke-Command` cmdlet to run a `Get-PfxCertificate` command remotely, and the PFX certificate file is not password protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="02e26-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="02e26-140">RELATED LINKS</span></span>

[<span data-ttu-id="02e26-141">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="02e26-141">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="02e26-142">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="02e26-142">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)
