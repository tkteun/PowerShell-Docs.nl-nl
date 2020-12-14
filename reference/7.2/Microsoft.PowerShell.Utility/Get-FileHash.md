---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 0b31409d1da56979887e606b76ddf20532b188c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705708"
---
# <span data-ttu-id="96dd4-102">Get-FileHash</span><span class="sxs-lookup"><span data-stu-id="96dd4-102">Get-FileHash</span></span>

## <span data-ttu-id="96dd4-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="96dd4-103">SYNOPSIS</span></span>
<span data-ttu-id="96dd4-104">Hiermee wordt de hash-waarde voor een bestand berekend met behulp van een opgegeven hash-algoritme.</span><span class="sxs-lookup"><span data-stu-id="96dd4-104">Computes the hash value for a file by using a specified hash algorithm.</span></span>

## <span data-ttu-id="96dd4-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="96dd4-105">SYNTAX</span></span>

### <span data-ttu-id="96dd4-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="96dd4-106">Path (Default)</span></span>

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="96dd4-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="96dd4-107">LiteralPath</span></span>

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="96dd4-108">StreamParameterSet</span><span class="sxs-lookup"><span data-stu-id="96dd4-108">StreamParameterSet</span></span>

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## <span data-ttu-id="96dd4-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="96dd4-109">DESCRIPTION</span></span>

<span data-ttu-id="96dd4-110">De `Get-FileHash` cmdlet berekent de hash-waarde voor een bestand met behulp van een opgegeven hash-algoritme.</span><span class="sxs-lookup"><span data-stu-id="96dd4-110">The `Get-FileHash` cmdlet computes the hash value for a file by using a specified hash algorithm.</span></span>
<span data-ttu-id="96dd4-111">Een hash-waarde is een unieke waarde die overeenkomt met de inhoud van het bestand.</span><span class="sxs-lookup"><span data-stu-id="96dd4-111">A hash value is a unique value that corresponds to the content of the file.</span></span> <span data-ttu-id="96dd4-112">In plaats van de inhoud van een bestand te identificeren met behulp van de bestands naam, extensie of andere aanduiding, wijst een hash een unieke waarde toe aan de inhoud van een bestand.</span><span class="sxs-lookup"><span data-stu-id="96dd4-112">Rather than identifying the contents of a file by its file name, extension, or other designation, a hash assigns a unique value to the contents of a file.</span></span> <span data-ttu-id="96dd4-113">Bestands namen en extensies kunnen worden gewijzigd zonder de inhoud van het bestand te wijzigen en zonder de hash-waarde te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="96dd4-113">File names and extensions can be changed without altering the content of the file, and without changing the hash value.</span></span> <span data-ttu-id="96dd4-114">De inhoud van het bestand kan ook worden gewijzigd zonder de naam of extensie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="96dd4-114">Similarly, the file's content can be changed without changing the name or extension.</span></span> <span data-ttu-id="96dd4-115">Als er echter maar één teken in de inhoud van een bestand wordt gewijzigd, wordt de hash-waarde van het bestand gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="96dd4-115">However, changing even a single character in the contents of a file changes the hash value of the file.</span></span>

<span data-ttu-id="96dd4-116">Hash-waarden zijn bedoeld om een cryptografische veilige manier te bieden om te controleren of de inhoud van een bestand niet is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="96dd4-116">The purpose of hash values is to provide a cryptographically-secure way to verify that the contents of a file have not been changed.</span></span> <span data-ttu-id="96dd4-117">Hoewel sommige hash-algoritmen, met inbegrip van MD5 en SHA1, niet meer worden beschouwd als beveiligd tegen aanvallen, is het doel van een beveiligd hash-algoritme het onmogelijk om de inhoud van een bestand te wijzigen, hetzij per ongeluk, hetzij door kwaad aardige of niet-geautoriseerde pogingen, en dezelfde hash-waarde te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="96dd4-117">While some hash algorithms, including MD5 and SHA1, are no longer considered secure against attack, the goal of a secure hash algorithm is to render it impossible to change the contents of a file -- either by accident, or by malicious or unauthorized attempt -- and maintain the same hash value.</span></span> <span data-ttu-id="96dd4-118">U kunt ook hash-waarden gebruiken om te bepalen of twee verschillende bestanden precies dezelfde inhoud hebben.</span><span class="sxs-lookup"><span data-stu-id="96dd4-118">You can also use hash values to determine if two different files have exactly the same content.</span></span> <span data-ttu-id="96dd4-119">Als de hash-waarden van twee bestanden identiek zijn, is de inhoud van de bestanden ook identiek.</span><span class="sxs-lookup"><span data-stu-id="96dd4-119">If the hash values of two files are identical, the contents of the files are also identical.</span></span>

<span data-ttu-id="96dd4-120">De `Get-FileHash` cmdlet maakt standaard gebruik van het sha256-algoritme, hoewel elk hash-algoritme dat wordt ondersteund door het besturings systeem van de doel groep kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="96dd4-120">By default, the `Get-FileHash` cmdlet uses the SHA256 algorithm, although any hash algorithm that is supported by the target operating system can be used.</span></span>

## <span data-ttu-id="96dd4-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="96dd4-121">EXAMPLES</span></span>

### <span data-ttu-id="96dd4-122">Voor beeld 1: de hash-waarde voor een bestand berekenen</span><span class="sxs-lookup"><span data-stu-id="96dd4-122">Example 1: Compute the hash value for a file</span></span>

<span data-ttu-id="96dd4-123">In dit voor beeld wordt de `Get-FileHash` cmdlet gebruikt om de hash-waarde voor het bestand te berekenen `/etc/apt/sources.list` .</span><span class="sxs-lookup"><span data-stu-id="96dd4-123">This example uses the `Get-FileHash` cmdlet to compute the hash value for the `/etc/apt/sources.list` file.</span></span> <span data-ttu-id="96dd4-124">Het hash-algoritme dat wordt gebruikt, is de standaard **sha256**.</span><span class="sxs-lookup"><span data-stu-id="96dd4-124">The hash algorithm used is the default, **SHA256**.</span></span> <span data-ttu-id="96dd4-125">De uitvoer wordt naar de cmdlet gepiped `Format-List` om de uitvoer als een lijst op te maken.</span><span class="sxs-lookup"><span data-stu-id="96dd4-125">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### <span data-ttu-id="96dd4-126">Voor beeld 2: de hash-waarde voor een ISO-bestand berekenen</span><span class="sxs-lookup"><span data-stu-id="96dd4-126">Example 2: Compute the hash value for an ISO file</span></span>

<span data-ttu-id="96dd4-127">In dit voor beeld worden de `Get-FileHash` cmdlet en de **SHA384** -algoritme gebruikt voor het berekenen van de hash-waarde voor een ISO-bestand dat een beheerder heeft gedownload van Internet.</span><span class="sxs-lookup"><span data-stu-id="96dd4-127">This example uses the `Get-FileHash` cmdlet and the **SHA384** algorithm to compute the hash value for an ISO file that an administrator has downloaded from the internet.</span></span> <span data-ttu-id="96dd4-128">De uitvoer wordt naar de cmdlet gepiped `Format-List` om de uitvoer als een lijst op te maken.</span><span class="sxs-lookup"><span data-stu-id="96dd4-128">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### <span data-ttu-id="96dd4-129">Voor beeld 3: de hash-waarde van een stroom berekenen</span><span class="sxs-lookup"><span data-stu-id="96dd4-129">Example 3: Compute the hash value of a stream</span></span>

<span data-ttu-id="96dd4-130">In dit voor beeld gebruiken we **System .net. webclient** om een pakket te downloaden van de [pagina Power shell-release](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span><span class="sxs-lookup"><span data-stu-id="96dd4-130">For this example, we get are using **System.Net.WebClient** to download a package from the [Powershell release page](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span></span> <span data-ttu-id="96dd4-131">Op de release pagina wordt ook de SHA256-hash van elk pakket bestand gedocumenteerd.</span><span class="sxs-lookup"><span data-stu-id="96dd4-131">The release page also documents the SHA256 hash of each package file.</span></span> <span data-ttu-id="96dd4-132">We kunnen de gepubliceerde hashwaarde vergelijken met de waarde die wordt berekend met `Get-FileHash` .</span><span class="sxs-lookup"><span data-stu-id="96dd4-132">We can compare the published hash value with the one we calculate with `Get-FileHash`.</span></span>

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### <span data-ttu-id="96dd4-133">Voor beeld 4: de hash van een teken reeks berekenen</span><span class="sxs-lookup"><span data-stu-id="96dd4-133">Example 4: Compute the hash of a string</span></span>

<span data-ttu-id="96dd4-134">Power shell biedt geen cmdlet voor het berekenen van de hash van een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="96dd4-134">PowerShell does not provide a cmdlet to compute the hash of a string.</span></span> <span data-ttu-id="96dd4-135">U kunt echter een teken reeks naar een stroom schrijven en de para meter **InputStream** van gebruiken `Get-FileHash` om de hash-waarde op te halen.</span><span class="sxs-lookup"><span data-stu-id="96dd4-135">However, you can write a string to a stream and use the **InputStream** parameter of `Get-FileHash` to get the hash value.</span></span>

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## <span data-ttu-id="96dd4-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="96dd4-136">PARAMETERS</span></span>

### <span data-ttu-id="96dd4-137">-Algoritme</span><span class="sxs-lookup"><span data-stu-id="96dd4-137">-Algorithm</span></span>

<span data-ttu-id="96dd4-138">Hiermee geeft u de cryptografische hash-functie op die moet worden gebruikt voor het berekenen van de hashwaarde van de inhoud van het opgegeven bestand of de gespecificeerde stroom.</span><span class="sxs-lookup"><span data-stu-id="96dd4-138">Specifies the cryptographic hash function to use for computing the hash value of the contents of the specified file or stream.</span></span> <span data-ttu-id="96dd4-139">Een cryptografische hash-functie heeft de eigenschap die niet haalbaar is om twee verschillende bestanden met dezelfde hashwaarde te vinden.</span><span class="sxs-lookup"><span data-stu-id="96dd4-139">A cryptographic hash function has the property that it is infeasible to find two different files with the same hash value.</span></span> <span data-ttu-id="96dd4-140">Hash-functies worden vaak gebruikt in combi natie met digitale hand tekeningen en gegevens integriteit.</span><span class="sxs-lookup"><span data-stu-id="96dd4-140">Hash functions are commonly used with digital signatures and for data integrity.</span></span> <span data-ttu-id="96dd4-141">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="96dd4-141">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="96dd4-142">SHA1</span><span class="sxs-lookup"><span data-stu-id="96dd4-142">SHA1</span></span>
- <span data-ttu-id="96dd4-143">SHA256</span><span class="sxs-lookup"><span data-stu-id="96dd4-143">SHA256</span></span>
- <span data-ttu-id="96dd4-144">SHA384</span><span class="sxs-lookup"><span data-stu-id="96dd4-144">SHA384</span></span>
- <span data-ttu-id="96dd4-145">SHA512</span><span class="sxs-lookup"><span data-stu-id="96dd4-145">SHA512</span></span>
- <span data-ttu-id="96dd4-146">MD5</span><span class="sxs-lookup"><span data-stu-id="96dd4-146">MD5</span></span>

<span data-ttu-id="96dd4-147">Als er geen waarde is opgegeven, of als de para meter wordt wegge laten, is de standaard waarde SHA256.</span><span class="sxs-lookup"><span data-stu-id="96dd4-147">If no value is specified, or if the parameter is omitted, the default value is SHA256.</span></span>

<span data-ttu-id="96dd4-148">Om veiligheids redenen moet MD5 en SHA1, die niet meer worden beschouwd als veilig, alleen worden gebruikt voor eenvoudige wijzigings validatie, en mag niet worden gebruikt voor het genereren van hash-waarden voor bestanden die bescherming tegen aanvallen of knoeien vereisen.</span><span class="sxs-lookup"><span data-stu-id="96dd4-148">For security reasons, MD5 and SHA1, which are no longer considered secure, should only be used for simple change validation, and should not be used to generate hash values for files that require protection from attack or tampering.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MD5

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96dd4-149">-InputStream</span><span class="sxs-lookup"><span data-stu-id="96dd4-149">-InputStream</span></span>

<span data-ttu-id="96dd4-150">Hiermee geeft u de invoer stroom op.</span><span class="sxs-lookup"><span data-stu-id="96dd4-150">Specifies the input stream.</span></span>

```yaml
Type: System.IO.Stream
Parameter Sets: StreamParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96dd4-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="96dd4-151">-LiteralPath</span></span>

<span data-ttu-id="96dd4-152">Hiermee geeft u het pad naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="96dd4-152">Specifies the path to a file.</span></span> <span data-ttu-id="96dd4-153">In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt terwijl deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="96dd4-153">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="96dd4-154">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="96dd4-154">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="96dd4-155">Als het pad escape tekens bevat, plaatst u het pad tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="96dd4-155">If the path includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="96dd4-156">Enkele aanhalings tekens geven Power shell opdracht instructies niet te interpreteren als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="96dd4-156">Single quotation marks instruct PowerShell not to interpret characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="96dd4-157">-Path</span><span class="sxs-lookup"><span data-stu-id="96dd4-157">-Path</span></span>

<span data-ttu-id="96dd4-158">Hiermee geeft u het pad naar een of meer bestanden als een matrix.</span><span class="sxs-lookup"><span data-stu-id="96dd4-158">Specifies the path to one or more files as an array.</span></span> <span data-ttu-id="96dd4-159">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="96dd4-159">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="96dd4-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="96dd4-160">CommonParameters</span></span>

<span data-ttu-id="96dd4-161">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="96dd4-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="96dd4-162">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="96dd4-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="96dd4-163">INVOER</span><span class="sxs-lookup"><span data-stu-id="96dd4-163">INPUTS</span></span>

### <span data-ttu-id="96dd4-164">System. String</span><span class="sxs-lookup"><span data-stu-id="96dd4-164">System.String</span></span>

<span data-ttu-id="96dd4-165">U kunt een teken reeks door sluizen naar de `Get-FileHash` cmdlet die een pad naar een of meer bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="96dd4-165">You can pipe a string to the `Get-FileHash` cmdlet that contains a path to one or more files.</span></span>

## <span data-ttu-id="96dd4-166">UITVOER</span><span class="sxs-lookup"><span data-stu-id="96dd4-166">OUTPUTS</span></span>

### <span data-ttu-id="96dd4-167">Micro soft. Power shell. Utility. FileHash</span><span class="sxs-lookup"><span data-stu-id="96dd4-167">Microsoft.Powershell.Utility.FileHash</span></span>

<span data-ttu-id="96dd4-168">`Get-FileHash` retourneert een-object dat het pad naar het opgegeven bestand vertegenwoordigt, de waarde van de berekende hash en de algoritme die wordt gebruikt om de hash te berekenen.</span><span class="sxs-lookup"><span data-stu-id="96dd4-168">`Get-FileHash` returns an object that represents the path to the specified file, the value of the computed hash, and the algorithm used to compute the hash.</span></span>

## <span data-ttu-id="96dd4-169">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="96dd4-169">NOTES</span></span>

## <span data-ttu-id="96dd4-170">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="96dd4-170">RELATED LINKS</span></span>

[<span data-ttu-id="96dd4-171">Format-List</span><span class="sxs-lookup"><span data-stu-id="96dd4-171">Format-List</span></span>](Format-List.md)

