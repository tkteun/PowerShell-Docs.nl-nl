---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: 831f40e9bd24cee20eeae54a41e0b022dc6300da
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705854"
---
# <span data-ttu-id="0af41-102">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="0af41-102">Set-AuthenticodeSignature</span></span>

## <span data-ttu-id="0af41-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0af41-103">SYNOPSIS</span></span>
<span data-ttu-id="0af41-104">Hiermee voegt u een [Authenticode](/windows-hardware/drivers/install/authenticode) -hand tekening toe aan een Power shell-script of een ander bestand.</span><span class="sxs-lookup"><span data-stu-id="0af41-104">Adds an [Authenticode](/windows-hardware/drivers/install/authenticode) signature to a PowerShell script or other file.</span></span>

## <span data-ttu-id="0af41-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0af41-105">SYNTAX</span></span>

### <span data-ttu-id="0af41-106">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="0af41-106">ByPath (Default)</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0af41-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="0af41-107">ByLiteralPath</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0af41-108">ByContent</span><span class="sxs-lookup"><span data-stu-id="0af41-108">ByContent</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0af41-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0af41-109">DESCRIPTION</span></span>

<span data-ttu-id="0af41-110">De `Set-AuthenticodeSignature` cmdlet voegt een Authenticode-hand tekening toe aan elk bestand dat ondersteuning biedt voor het object interface pakket (SIP).</span><span class="sxs-lookup"><span data-stu-id="0af41-110">The `Set-AuthenticodeSignature` cmdlet adds an Authenticode signature to any file that supports Subject Interface Package (SIP).</span></span>

<span data-ttu-id="0af41-111">In een Power shell-script bestand krijgt de hand tekening de vorm van een tekst blok dat het einde aangeeft van de instructies die worden uitgevoerd in het script.</span><span class="sxs-lookup"><span data-stu-id="0af41-111">In a PowerShell script file, the signature takes the form of a block of text that indicates the end of the instructions that are executed in the script.</span></span> <span data-ttu-id="0af41-112">Als er een hand tekening in het bestand is wanneer deze cmdlet wordt uitgevoerd, wordt die hand tekening verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0af41-112">If there is a signature in the file when this cmdlet runs, that signature is removed.</span></span>

## <span data-ttu-id="0af41-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0af41-113">EXAMPLES</span></span>

### <span data-ttu-id="0af41-114">Voor beeld 1: een script ondertekenen met een certificaat uit het lokale certificaat archief</span><span class="sxs-lookup"><span data-stu-id="0af41-114">Example 1 - Sign a script using a certificate from the local certificate store</span></span>

<span data-ttu-id="0af41-115">Met deze opdrachten wordt een certificaat voor ondertekening van programma code opgehaald van de Power shell-certificaat provider en gebruikt om een Power shell-script te ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="0af41-115">These commands retrieve a code-signing certificate from the PowerShell certificate provider and use it to sign a PowerShell script.</span></span>

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

<span data-ttu-id="0af41-116">De eerste opdracht gebruikt de `Get-ChildItem` cmdlet en de Power shell-certificaat provider om de certificaten op te halen in de `Cert:\CurrentUser\My` submap van het certificaat archief.</span><span class="sxs-lookup"><span data-stu-id="0af41-116">The first command uses the `Get-ChildItem` cmdlet and the PowerShell certificate provider to get the certificates in the `Cert:\CurrentUser\My` subdirectory of the certificate store.</span></span> <span data-ttu-id="0af41-117">Het `Cert:` station is het station dat door de certificaat provider wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0af41-117">The `Cert:` drive is the drive exposed by the certificate provider.</span></span> <span data-ttu-id="0af41-118">De **CodeSigningCert** -para meter, die alleen wordt ondersteund door de certificaat provider, beperkt de certificaten die worden opgehaald tot die met de instantie voor het ondertekenen van programma code.</span><span class="sxs-lookup"><span data-stu-id="0af41-118">The **CodeSigningCert** parameter, which is supported only by the certificate provider, limits the certificates retrieved to those with code-signing authority.</span></span> <span data-ttu-id="0af41-119">De opdracht slaat het resultaat op in de `$cert` variabele.</span><span class="sxs-lookup"><span data-stu-id="0af41-119">The command stores the result in the `$cert` variable.</span></span>

<span data-ttu-id="0af41-120">Met de tweede opdracht wordt de `Set-AuthenticodeSignature` cmdlet gebruikt om het script te ondertekenen `PSTestInternet2.ps1` .</span><span class="sxs-lookup"><span data-stu-id="0af41-120">The second command uses the `Set-AuthenticodeSignature` cmdlet to sign the `PSTestInternet2.ps1` script.</span></span> <span data-ttu-id="0af41-121">De para meter **filepath** wordt gebruikt om de naam van het script en de para meter **certificaat** op te geven om op te geven dat het certificaat is opgeslagen in de `$cert` variabele.</span><span class="sxs-lookup"><span data-stu-id="0af41-121">It uses the **FilePath** parameter to specify the name of the script and the **Certificate** parameter to specify that the certificate is stored in the `$cert` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="0af41-122">Het gebruik van de para meter **CodeSigningCert** met `Get-ChildItem` alleen certificaten met de instantie voor ondertekening van programma code en een persoonlijke sleutel bevatten.</span><span class="sxs-lookup"><span data-stu-id="0af41-122">Using the **CodeSigningCert** parameter with `Get-ChildItem` only returns certificates that have code-signing authority and contain a private key.</span></span> <span data-ttu-id="0af41-123">Als er geen persoonlijke sleutel is, kunnen de certificaten niet worden gebruikt voor het ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="0af41-123">If there is no private key, the certificates cannot be used for signing.</span></span>

### <span data-ttu-id="0af41-124">Voor beeld 2: een script ondertekenen met een certificaat uit een PFX-bestand</span><span class="sxs-lookup"><span data-stu-id="0af41-124">Example 2 - Sign a script using a certificate from a PFX file</span></span>

<span data-ttu-id="0af41-125">Deze opdrachten gebruiken de `Get-PfxCertificate` cmdlet om een certificaat voor ondertekening van programma code te laden.</span><span class="sxs-lookup"><span data-stu-id="0af41-125">These commands use the `Get-PfxCertificate` cmdlet to load a code signing certificate.</span></span> <span data-ttu-id="0af41-126">Vervolgens gebruikt u het om een Power shell-script te ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="0af41-126">Then, use it to sign a PowerShell script.</span></span>

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

<span data-ttu-id="0af41-127">De eerste opdracht gebruikt de `Get-PfxCertificate` cmdlet om het C:\Test\MySign.pfx-certificaat in de `$cert` variabele te laden.</span><span class="sxs-lookup"><span data-stu-id="0af41-127">The first command uses the `Get-PfxCertificate` cmdlet to load the C:\Test\MySign.pfx certificate into the `$cert` variable.</span></span>

<span data-ttu-id="0af41-128">De tweede opdracht wordt gebruikt `Set-AuthenticodeSignature` om het script te ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="0af41-128">The second command uses `Set-AuthenticodeSignature` to sign the script.</span></span> <span data-ttu-id="0af41-129">De **filepath** para meter van het `Set-AuthenticodeSignature` pad naar het script bestand dat wordt ondertekend en de para meter **CERT** geeft de `$cert` variabele met het certificaat door `Set-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="0af41-129">The **FilePath** parameter of `Set-AuthenticodeSignature` specifies the path to the script file being signed and the **Cert** parameter passes the `$cert` variable containing the certificate to `Set-AuthenticodeSignature`.</span></span>

<span data-ttu-id="0af41-130">Als het certificaat bestand is beveiligd met een wacht woord, vraagt Power shell u om het wacht woord.</span><span class="sxs-lookup"><span data-stu-id="0af41-130">If the certificate file is password protected, PowerShell prompts you for the password.</span></span>

### <span data-ttu-id="0af41-131">Voor beeld 3: een hand tekening toevoegen die de basis instantie bevat</span><span class="sxs-lookup"><span data-stu-id="0af41-131">Example 3 - Add a signature that includes the root authority</span></span>

<span data-ttu-id="0af41-132">Met deze opdracht wordt een digitale hand tekening toegevoegd die de basis instantie in de vertrouwens keten bevat en is ondertekend door een tijds tempel server van derden.</span><span class="sxs-lookup"><span data-stu-id="0af41-132">This command adds a digital signature that includes the root authority in the trust chain, and it is signed by a third-party timestamp server.</span></span>

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

<span data-ttu-id="0af41-133">De opdracht gebruikt de **filepath** -para meter om het script op te geven dat wordt ondertekend en de para meter **certificaat** om het certificaat op te geven dat is opgeslagen in de `$cert` variabele.</span><span class="sxs-lookup"><span data-stu-id="0af41-133">The command uses the **FilePath** parameter to specify the script being signed and the **Certificate** parameter to specify the certificate that is saved in the `$cert` variable.</span></span> <span data-ttu-id="0af41-134">De para meter **IncludeChain** wordt gebruikt voor het opnemen van alle hand tekeningen in de vertrouwens keten, met inbegrip van de basis certificerings instantie.</span><span class="sxs-lookup"><span data-stu-id="0af41-134">It uses the **IncludeChain** parameter to include all of the signatures in the trust chain, including the root authority.</span></span> <span data-ttu-id="0af41-135">De para meter **TimeStampServer** wordt ook gebruikt om een tijds tempel toe te voegen aan de hand tekening.</span><span class="sxs-lookup"><span data-stu-id="0af41-135">It also uses the **TimeStampServer** parameter to add a timestamp to the signature.</span></span>
<span data-ttu-id="0af41-136">Zo voor komt u dat het script mislukt wanneer het certificaat verloopt.</span><span class="sxs-lookup"><span data-stu-id="0af41-136">This prevents the script from failing when the certificate expires.</span></span>

## <span data-ttu-id="0af41-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0af41-137">PARAMETERS</span></span>

### <span data-ttu-id="0af41-138">-Certificaat</span><span class="sxs-lookup"><span data-stu-id="0af41-138">-Certificate</span></span>

<span data-ttu-id="0af41-139">Hiermee geeft u het certificaat op dat wordt gebruikt voor het ondertekenen van het script of bestand.</span><span class="sxs-lookup"><span data-stu-id="0af41-139">Specifies the certificate that will be used to sign the script or file.</span></span> <span data-ttu-id="0af41-140">Voer een variabele in die een object opslaat dat het certificaat vertegenwoordigt, of een expressie die het certificaat ophaalt.</span><span class="sxs-lookup"><span data-stu-id="0af41-140">Enter a variable that stores an object representing the certificate or an expression that gets the certificate.</span></span>

<span data-ttu-id="0af41-141">Als u een certificaat wilt zoeken, gebruikt `Get-PfxCertificate` of gebruikt u de `Get-ChildItem` cmdlet in het certificaat `Cert:` station.</span><span class="sxs-lookup"><span data-stu-id="0af41-141">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate `Cert:` drive.</span></span> <span data-ttu-id="0af41-142">Als het certificaat ongeldig is of geen `code-signing` instantie heeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="0af41-142">If the certificate is not valid or does not have `code-signing` authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0af41-143">-FilePath</span><span class="sxs-lookup"><span data-stu-id="0af41-143">-FilePath</span></span>

<span data-ttu-id="0af41-144">Hiermee geeft u het pad naar een bestand dat wordt ondertekend.</span><span class="sxs-lookup"><span data-stu-id="0af41-144">Specifies the path to a file that is being signed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0af41-145">-Force</span><span class="sxs-lookup"><span data-stu-id="0af41-145">-Force</span></span>

<span data-ttu-id="0af41-146">Hiermee kan de cmdlet een hand tekening toevoegen aan een alleen-lezen bestand.</span><span class="sxs-lookup"><span data-stu-id="0af41-146">Allows the cmdlet to append a signature to a read-only file.</span></span> <span data-ttu-id="0af41-147">Zelfs met behulp van de para meter **forceren** , kan de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="0af41-147">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0af41-148">-HashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="0af41-148">-HashAlgorithm</span></span>

<span data-ttu-id="0af41-149">Hiermee geeft u het hash-algoritme op dat door Windows wordt gebruikt voor het berekenen van de digitale hand tekening voor het bestand.</span><span class="sxs-lookup"><span data-stu-id="0af41-149">Specifies the hashing algorithm that Windows uses to compute the digital signature for the file.</span></span>

<span data-ttu-id="0af41-150">Voor Power Shell 3,0 is de standaard waarde SHA256, het standaard hash-algoritme voor Windows.</span><span class="sxs-lookup"><span data-stu-id="0af41-150">For PowerShell 3.0, the default is SHA256, which is the Windows default hashing algorithm.</span></span> <span data-ttu-id="0af41-151">Voor Power Shell 2,0 is de standaard SHA1.</span><span class="sxs-lookup"><span data-stu-id="0af41-151">For PowerShell 2.0, the default is SHA1.</span></span> <span data-ttu-id="0af41-152">Bestanden die zijn ondertekend met een ander hash-algoritme, worden mogelijk niet herkend op andere systemen.</span><span class="sxs-lookup"><span data-stu-id="0af41-152">Files that are signed with a different hashing algorithm might not be recognized on other systems.</span></span> <span data-ttu-id="0af41-153">Welke algoritmen worden ondersteund, is afhankelijk van de versie van het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="0af41-153">Which algorithms are supported depends on the version of the operating system.</span></span>

<span data-ttu-id="0af41-154">Zie [HashAlgorithmName struct](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties)voor een lijst met mogelijke waarden.</span><span class="sxs-lookup"><span data-stu-id="0af41-154">For a list of possible values, see [HashAlgorithmName Struct](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0af41-155">-IncludeChain</span><span class="sxs-lookup"><span data-stu-id="0af41-155">-IncludeChain</span></span>

<span data-ttu-id="0af41-156">Hiermee wordt bepaald welke certificaten in de certificaat vertrouwens keten zijn opgenomen in de digitale hand tekening.</span><span class="sxs-lookup"><span data-stu-id="0af41-156">Determines which certificates in the certificate trust chain are included in the digital signature.</span></span>
<span data-ttu-id="0af41-157">**NotRoot** is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="0af41-157">**NotRoot** is the default.</span></span>

<span data-ttu-id="0af41-158">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="0af41-158">Valid values are:</span></span>

- <span data-ttu-id="0af41-159">Ondertekenaar: bevat alleen het certificaat van de ondertekenaar.</span><span class="sxs-lookup"><span data-stu-id="0af41-159">Signer: Includes only the signer's certificate.</span></span>
- <span data-ttu-id="0af41-160">NotRoot: bevat alle certificaten in de certificaat keten, met uitzonde ring van de basis certificerings instantie.</span><span class="sxs-lookup"><span data-stu-id="0af41-160">NotRoot: Includes all of the certificates in the certificate chain, except for the root authority.</span></span>
- <span data-ttu-id="0af41-161">Alle: bevat alle certificaten in de certificaat keten.</span><span class="sxs-lookup"><span data-stu-id="0af41-161">All: Includes all the certificates in the certificate chain.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0af41-162">-TimestampServer</span><span class="sxs-lookup"><span data-stu-id="0af41-162">-TimestampServer</span></span>

<span data-ttu-id="0af41-163">Gebruikt de opgegeven tijds tempel server om een tijds tempel toe te voegen aan de hand tekening.</span><span class="sxs-lookup"><span data-stu-id="0af41-163">Uses the specified time stamp server to add a time stamp to the signature.</span></span> <span data-ttu-id="0af41-164">Typ de URL van de tijds tempel server als een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="0af41-164">Type the URL of the time stamp server as a string.</span></span>

<span data-ttu-id="0af41-165">Het tijds tempel vertegenwoordigt de exacte tijd dat het certificaat is toegevoegd aan het bestand.</span><span class="sxs-lookup"><span data-stu-id="0af41-165">The time stamp represents the exact time that the certificate was added to the file.</span></span> <span data-ttu-id="0af41-166">Een tijds tempel voor komt dat het script mislukt als het certificaat verloopt omdat gebruikers en Program ma's kunnen controleren of het certificaat geldig is op het moment van ondertekening.</span><span class="sxs-lookup"><span data-stu-id="0af41-166">A time stamp prevents the script from failing if the certificate expires because users and programs can verify that the certificate was valid at the time of signing.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0af41-167">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0af41-167">-LiteralPath</span></span>

<span data-ttu-id="0af41-168">Hiermee geeft u het pad naar een bestand dat wordt ondertekend.</span><span class="sxs-lookup"><span data-stu-id="0af41-168">Specifies the path to a file that is being signed.</span></span> <span data-ttu-id="0af41-169">In tegens telling tot het **bestandspad** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="0af41-169">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="0af41-170">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="0af41-170">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0af41-171">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="0af41-171">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0af41-172">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="0af41-172">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="0af41-173">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="0af41-173">-SourcePathOrExtension</span></span>

<span data-ttu-id="0af41-174">Het pad naar het bestand of het bestands type van de inhoud waarvoor de digitale hand tekening is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="0af41-174">Path to the file or file type of the content for which the digital signature is added.</span></span> <span data-ttu-id="0af41-175">Deze para meter wordt gebruikt met **inhoud** waar bestands inhoud als een byte matrix wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="0af41-175">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0af41-176">-Inhoud</span><span class="sxs-lookup"><span data-stu-id="0af41-176">-Content</span></span>

<span data-ttu-id="0af41-177">Inhoud van een bestand als een byte matrix waarvoor de digitale hand tekening is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="0af41-177">Contents of a file as a byte array for which the digital signature is added.</span></span> <span data-ttu-id="0af41-178">Deze para meter moet worden gebruikt met de para meter **SourcePathOrExtension** .</span><span class="sxs-lookup"><span data-stu-id="0af41-178">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="0af41-179">De inhoud van het bestand moet de Unicode-indeling (UTF-16LE) hebben.</span><span class="sxs-lookup"><span data-stu-id="0af41-179">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0af41-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0af41-180">-Confirm</span></span>

<span data-ttu-id="0af41-181">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="0af41-181">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0af41-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0af41-182">-WhatIf</span></span>

<span data-ttu-id="0af41-183">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="0af41-183">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0af41-184">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0af41-184">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0af41-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0af41-185">CommonParameters</span></span>

<span data-ttu-id="0af41-186">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0af41-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0af41-187">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0af41-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0af41-188">INVOER</span><span class="sxs-lookup"><span data-stu-id="0af41-188">INPUTS</span></span>

### <span data-ttu-id="0af41-189">System. String</span><span class="sxs-lookup"><span data-stu-id="0af41-189">System.String</span></span>

<span data-ttu-id="0af41-190">U kunt een teken reeks die het bestandspad bevat door sluizen naar `Set-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="0af41-190">You can pipe a string that contains the file path to `Set-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="0af41-191">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0af41-191">OUTPUTS</span></span>

### <span data-ttu-id="0af41-192">System. Management. Automation. Signature</span><span class="sxs-lookup"><span data-stu-id="0af41-192">System.Management.Automation.Signature</span></span>

## <span data-ttu-id="0af41-193">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0af41-193">NOTES</span></span>

<span data-ttu-id="0af41-194">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="0af41-194">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="0af41-195">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0af41-195">RELATED LINKS</span></span>

[<span data-ttu-id="0af41-196">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="0af41-196">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="0af41-197">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="0af41-197">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="0af41-198">Get-pfx</span><span class="sxs-lookup"><span data-stu-id="0af41-198">Get-PfxCertificate</span></span>](Get-PfxCertificate.md)

[<span data-ttu-id="0af41-199">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="0af41-199">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="0af41-200">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="0af41-200">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="0af41-201">about_Signing</span><span class="sxs-lookup"><span data-stu-id="0af41-201">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)
