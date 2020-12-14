---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: baf06c34511217f23d876843007525b9ce17f35b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705721"
---
# <span data-ttu-id="44d4f-102">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="44d4f-102">Get-PfxCertificate</span></span>

## <span data-ttu-id="44d4f-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="44d4f-103">SYNOPSIS</span></span>
<span data-ttu-id="44d4f-104">Haalt informatie op over PFX-certificaat bestanden op de computer.</span><span class="sxs-lookup"><span data-stu-id="44d4f-104">Gets information about PFX certificate files on the computer.</span></span>

## <span data-ttu-id="44d4f-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="44d4f-105">SYNTAX</span></span>

### <span data-ttu-id="44d4f-106">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="44d4f-106">ByPath (Default)</span></span>

```
Get-PfxCertificate [-FilePath] <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

### <span data-ttu-id="44d4f-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="44d4f-107">ByLiteralPath</span></span>

```
Get-PfxCertificate -LiteralPath <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

## <span data-ttu-id="44d4f-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="44d4f-108">DESCRIPTION</span></span>

<span data-ttu-id="44d4f-109">De `Get-PfxCertificate` cmdlet haalt een object op dat staat voor elk opgegeven pfx-certificaat bestand.</span><span class="sxs-lookup"><span data-stu-id="44d4f-109">The `Get-PfxCertificate` cmdlet gets an object representing each specified PFX certificate file.</span></span>
<span data-ttu-id="44d4f-110">Een PFX-bestand bevat zowel het certificaat als een persoonlijke sleutel.</span><span class="sxs-lookup"><span data-stu-id="44d4f-110">A PFX file includes both the certificate and a private key.</span></span>

## <span data-ttu-id="44d4f-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="44d4f-111">EXAMPLES</span></span>

### <span data-ttu-id="44d4f-112">Voor beeld 1: een PFX-certificaat ophalen</span><span class="sxs-lookup"><span data-stu-id="44d4f-112">Example 1: Get a PFX certificate</span></span>

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

<span data-ttu-id="44d4f-113">Met deze opdracht wordt informatie opgehaald over het bestand test. pfx op het systeem.</span><span class="sxs-lookup"><span data-stu-id="44d4f-113">This command gets information about the Test.pfx certificate file on the system.</span></span>

### <span data-ttu-id="44d4f-114">Voor beeld 2: een PFX-certificaat ophalen van een externe computer</span><span class="sxs-lookup"><span data-stu-id="44d4f-114">Example 2: Get a PFX certificate from a remote computer</span></span>

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

<span data-ttu-id="44d4f-115">Met deze opdracht wordt een PFX-certificaat bestand opgehaald van de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="44d4f-115">This command gets a PFX certificate file from the Server01 remote computer.</span></span> <span data-ttu-id="44d4f-116">Het gebruikt `Invoke-Command` om een `Get-PfxCertificate` opdracht op afstand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="44d4f-116">It uses `Invoke-Command` to run a `Get-PfxCertificate` command remotely.</span></span>

<span data-ttu-id="44d4f-117">Wanneer het PFX-certificaat bestand niet met een wacht woord is beveiligd, moet de waarde van de **authenticatie** parameter van `Invoke-Command` CredSSP zijn.</span><span class="sxs-lookup"><span data-stu-id="44d4f-117">When the PFX certificate file is not password-protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="44d4f-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="44d4f-118">PARAMETERS</span></span>

### <span data-ttu-id="44d4f-119">-FilePath</span><span class="sxs-lookup"><span data-stu-id="44d4f-119">-FilePath</span></span>

<span data-ttu-id="44d4f-120">Hiermee geeft u het volledige pad naar het PFX-bestand van het beveiligde bestand.</span><span class="sxs-lookup"><span data-stu-id="44d4f-120">Specifies the full path to the PFX file of the secured file.</span></span> <span data-ttu-id="44d4f-121">Als u een waarde voor deze para meter opgeeft, hoeft u niet `-FilePath` op de opdracht regel te typen.</span><span class="sxs-lookup"><span data-stu-id="44d4f-121">If you specify a value for this parameter, it is not necessary to type `-FilePath` at the command line.</span></span>

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

### <span data-ttu-id="44d4f-122">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="44d4f-122">-LiteralPath</span></span>

<span data-ttu-id="44d4f-123">Het volledige pad naar het PFX-bestand van het beveiligde bestand.</span><span class="sxs-lookup"><span data-stu-id="44d4f-123">The full path to the PFX file of the secured file.</span></span> <span data-ttu-id="44d4f-124">In tegens telling tot het **bestandspad** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="44d4f-124">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="44d4f-125">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="44d4f-125">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="44d4f-126">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="44d4f-126">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="44d4f-127">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="44d4f-127">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="44d4f-128">-NoPromptForPassword</span><span class="sxs-lookup"><span data-stu-id="44d4f-128">-NoPromptForPassword</span></span>

<span data-ttu-id="44d4f-129">Onderdrukt de vraag naar een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="44d4f-129">Suppresses prompting for a password.</span></span>

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

### <span data-ttu-id="44d4f-130">-Password</span><span class="sxs-lookup"><span data-stu-id="44d4f-130">-Password</span></span>

<span data-ttu-id="44d4f-131">Hiermee geeft u een wacht woord op dat vereist is voor toegang tot een `.pfx` certificaat bestand.</span><span class="sxs-lookup"><span data-stu-id="44d4f-131">Specifies a password required to access a `.pfx` certificate file.</span></span>

<span data-ttu-id="44d4f-132">Deze para meter is geïntroduceerd in Power shell 6,1.</span><span class="sxs-lookup"><span data-stu-id="44d4f-132">This parameter was introduced in PowerShell 6.1.</span></span>

> [!NOTE]
> <span data-ttu-id="44d4f-133">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="44d4f-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="44d4f-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="44d4f-134">CommonParameters</span></span>

<span data-ttu-id="44d4f-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="44d4f-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="44d4f-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="44d4f-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="44d4f-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="44d4f-137">INPUTS</span></span>

### <span data-ttu-id="44d4f-138">System. String</span><span class="sxs-lookup"><span data-stu-id="44d4f-138">System.String</span></span>

<span data-ttu-id="44d4f-139">U kunt een teken reeks die een bestandspad bevat, door sluizen naar `Get-PfxCertificate` .</span><span class="sxs-lookup"><span data-stu-id="44d4f-139">You can pipe a string that contains a file path to `Get-PfxCertificate`.</span></span>

## <span data-ttu-id="44d4f-140">UITVOER</span><span class="sxs-lookup"><span data-stu-id="44d4f-140">OUTPUTS</span></span>

### <span data-ttu-id="44d4f-141">System. Security. Cryptography. X509Certificates. X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="44d4f-141">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>

<span data-ttu-id="44d4f-142">`Get-PfxCertificate` retourneert een object voor elk certificaat dat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="44d4f-142">`Get-PfxCertificate` returns an object for each certificate that it gets.</span></span>

## <span data-ttu-id="44d4f-143">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="44d4f-143">NOTES</span></span>

<span data-ttu-id="44d4f-144">Wanneer u de `Invoke-Command` cmdlet gebruikt om een `Get-PfxCertificate` opdracht extern uit te voeren en het pfx-certificaat bestand niet met een wacht woord is beveiligd, moet de waarde van de **authenticatie** parameter van `Invoke-Command` CredSSP zijn.</span><span class="sxs-lookup"><span data-stu-id="44d4f-144">When using the `Invoke-Command` cmdlet to run a `Get-PfxCertificate` command remotely, and the PFX certificate file is not password protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="44d4f-145">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="44d4f-145">RELATED LINKS</span></span>

[<span data-ttu-id="44d4f-146">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="44d4f-146">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="44d4f-147">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="44d4f-147">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

