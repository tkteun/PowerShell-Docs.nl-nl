---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: ce0ecdfc216680f255718b1a03f78276364b1c50
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250439"
---
# <span data-ttu-id="b5e89-103">Get-FileHash</span><span class="sxs-lookup"><span data-stu-id="b5e89-103">Get-FileHash</span></span>

## <span data-ttu-id="b5e89-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b5e89-104">SYNOPSIS</span></span>
<span data-ttu-id="b5e89-105">Hiermee wordt de hash-waarde voor een bestand berekend met behulp van een opgegeven hash-algoritme.</span><span class="sxs-lookup"><span data-stu-id="b5e89-105">Computes the hash value for a file by using a specified hash algorithm.</span></span>

## <span data-ttu-id="b5e89-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b5e89-106">SYNTAX</span></span>

### <span data-ttu-id="b5e89-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="b5e89-107">Path (Default)</span></span>

```
Get-FileHash [-Path] <String[]> [-Algorithm <String>] [<CommonParameters>]
```

### <span data-ttu-id="b5e89-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b5e89-108">LiteralPath</span></span>

```
Get-FileHash -LiteralPath <String[]> [-Algorithm <String>] [<CommonParameters>]
```

### <span data-ttu-id="b5e89-109">Streamen</span><span class="sxs-lookup"><span data-stu-id="b5e89-109">Stream</span></span>

```
Get-FileHash -InputStream <Stream> [-Algorithm <String>] [<CommonParameters>]
```

## <span data-ttu-id="b5e89-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b5e89-110">DESCRIPTION</span></span>

<span data-ttu-id="b5e89-111">De `Get-FileHash` cmdlet berekent de hash-waarde voor een bestand met behulp van een opgegeven hash-algoritme.</span><span class="sxs-lookup"><span data-stu-id="b5e89-111">The `Get-FileHash` cmdlet computes the hash value for a file by using a specified hash algorithm.</span></span>
<span data-ttu-id="b5e89-112">Een hash-waarde is een unieke waarde die overeenkomt met de inhoud van het bestand.</span><span class="sxs-lookup"><span data-stu-id="b5e89-112">A hash value is a unique value that corresponds to the content of the file.</span></span> <span data-ttu-id="b5e89-113">In plaats van de inhoud van een bestand te identificeren met behulp van de bestands naam, extensie of andere aanduiding, wijst een hash een unieke waarde toe aan de inhoud van een bestand.</span><span class="sxs-lookup"><span data-stu-id="b5e89-113">Rather than identifying the contents of a file by its file name, extension, or other designation, a hash assigns a unique value to the contents of a file.</span></span> <span data-ttu-id="b5e89-114">Bestands namen en extensies kunnen worden gewijzigd zonder de inhoud van het bestand te wijzigen en zonder de hash-waarde te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b5e89-114">File names and extensions can be changed without altering the content of the file, and without changing the hash value.</span></span> <span data-ttu-id="b5e89-115">De inhoud van het bestand kan ook worden gewijzigd zonder de naam of extensie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b5e89-115">Similarly, the file's content can be changed without changing the name or extension.</span></span> <span data-ttu-id="b5e89-116">Als er echter maar één teken in de inhoud van een bestand wordt gewijzigd, wordt de hash-waarde van het bestand gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b5e89-116">However, changing even a single character in the contents of a file changes the hash value of the file.</span></span>

<span data-ttu-id="b5e89-117">Hash-waarden zijn bedoeld om een cryptografische veilige manier te bieden om te controleren of de inhoud van een bestand niet is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b5e89-117">The purpose of hash values is to provide a cryptographically-secure way to verify that the contents of a file have not been changed.</span></span> <span data-ttu-id="b5e89-118">Hoewel sommige hash-algoritmen, met inbegrip van MD5 en SHA1, niet meer worden beschouwd als beveiligd tegen aanvallen, is het doel van een beveiligd hash-algoritme het onmogelijk om de inhoud van een bestand te wijzigen, hetzij per ongeluk, hetzij door kwaad aardige of niet-geautoriseerde pogingen, en dezelfde hash-waarde te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="b5e89-118">While some hash algorithms, including MD5 and SHA1, are no longer considered secure against attack, the goal of a secure hash algorithm is to render it impossible to change the contents of a file -- either by accident, or by malicious or unauthorized attempt -- and maintain the same hash value.</span></span> <span data-ttu-id="b5e89-119">U kunt ook hash-waarden gebruiken om te bepalen of twee verschillende bestanden precies dezelfde inhoud hebben.</span><span class="sxs-lookup"><span data-stu-id="b5e89-119">You can also use hash values to determine if two different files have exactly the same content.</span></span> <span data-ttu-id="b5e89-120">Als de hash-waarden van twee bestanden identiek zijn, is de inhoud van de bestanden ook identiek.</span><span class="sxs-lookup"><span data-stu-id="b5e89-120">If the hash values of two files are identical, the contents of the files are also identical.</span></span>

<span data-ttu-id="b5e89-121">De `Get-FileHash` cmdlet maakt standaard gebruik van het sha256-algoritme, hoewel elk hash-algoritme dat wordt ondersteund door het besturings systeem van de doel groep kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b5e89-121">By default, the `Get-FileHash` cmdlet uses the SHA256 algorithm, although any hash algorithm that is supported by the target operating system can be used.</span></span>

## <span data-ttu-id="b5e89-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b5e89-122">EXAMPLES</span></span>

### <span data-ttu-id="b5e89-123">Voor beeld 1: de hash-waarde voor een bestand berekenen</span><span class="sxs-lookup"><span data-stu-id="b5e89-123">Example 1: Compute the hash value for a file</span></span>

<span data-ttu-id="b5e89-124">In dit voor beeld wordt de `Get-FileHash` cmdlet gebruikt om de hash-waarde voor het bestand te berekenen `Powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="b5e89-124">This example uses the `Get-FileHash` cmdlet to compute the hash value for the `Powershell.exe` file.</span></span>
<span data-ttu-id="b5e89-125">Het hash-algoritme dat wordt gebruikt, is de standaard SHA256.</span><span class="sxs-lookup"><span data-stu-id="b5e89-125">The hash algorithm used is the default, SHA256.</span></span> <span data-ttu-id="b5e89-126">De uitvoer wordt naar de cmdlet gepiped `Format-List` om de uitvoer als een lijst op te maken.</span><span class="sxs-lookup"><span data-stu-id="b5e89-126">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash $PSHOME\powershell.exe | Format-List
```

```Output
Algorithm : SHA256
Hash      : 908B64B1971A979C7E3E8CE4621945CBA84854CB98D76367B791A6E22B5F6D53
Path      : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
```

### <span data-ttu-id="b5e89-127">Voor beeld 2: de hash-waarde voor een ISO-bestand berekenen</span><span class="sxs-lookup"><span data-stu-id="b5e89-127">Example 2: Compute the hash value for an ISO file</span></span>

<span data-ttu-id="b5e89-128">In dit voor beeld worden de `Get-FileHash` cmdlet en de **SHA384** -algoritme gebruikt voor het berekenen van de hash-waarde voor een ISO-bestand dat een beheerder heeft gedownload van Internet.</span><span class="sxs-lookup"><span data-stu-id="b5e89-128">This example uses the `Get-FileHash` cmdlet and the **SHA384** algorithm to compute the hash value for an ISO file that an administrator has downloaded from the internet.</span></span> <span data-ttu-id="b5e89-129">De uitvoer wordt naar de cmdlet gepiped `Format-List` om de uitvoer als een lijst op te maken.</span><span class="sxs-lookup"><span data-stu-id="b5e89-129">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### <span data-ttu-id="b5e89-130">Voor beeld 3: de hash-waarde van een stroom berekenen</span><span class="sxs-lookup"><span data-stu-id="b5e89-130">Example 3: Compute the hash value of a stream</span></span>

<span data-ttu-id="b5e89-131">In dit voor beeld gebruiken we **System .net. webclient** om een pakket te downloaden van de [pagina Power shell-release](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span><span class="sxs-lookup"><span data-stu-id="b5e89-131">For this example, we get are using **System.Net.WebClient** to download a package from the [Powershell release page](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span></span> <span data-ttu-id="b5e89-132">Op de release pagina wordt ook de SHA256-hash van elk pakket bestand gedocumenteerd.</span><span class="sxs-lookup"><span data-stu-id="b5e89-132">The release page also documents the SHA256 hash of each package file.</span></span> <span data-ttu-id="b5e89-133">We kunnen de gepubliceerde hashwaarde vergelijken met de waarde die wordt berekend met `Get-FileHash` .</span><span class="sxs-lookup"><span data-stu-id="b5e89-133">We can compare the published hash value with the one we calculate with `Get-FileHash`.</span></span>

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

### <span data-ttu-id="b5e89-134">Voor beeld 4: de hash van een teken reeks berekenen</span><span class="sxs-lookup"><span data-stu-id="b5e89-134">Example 4: Compute the hash of a string</span></span>

<span data-ttu-id="b5e89-135">Power shell biedt geen cmdlet voor het berekenen van de hash van een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="b5e89-135">PowerShell does not provide a cmdlet to compute the hash of a string.</span></span> <span data-ttu-id="b5e89-136">U kunt echter een teken reeks naar een stroom schrijven en de para meter **InputStream** van gebruiken `Get-FileHash` om de hash-waarde op te halen.</span><span class="sxs-lookup"><span data-stu-id="b5e89-136">However, you can write a string to a stream and use the **InputStream** parameter of `Get-FileHash` to get the hash value.</span></span>

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

## <span data-ttu-id="b5e89-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b5e89-137">PARAMETERS</span></span>

### <span data-ttu-id="b5e89-138">-Algoritme</span><span class="sxs-lookup"><span data-stu-id="b5e89-138">-Algorithm</span></span>

<span data-ttu-id="b5e89-139">Hiermee geeft u de cryptografische hash-functie op die moet worden gebruikt voor het berekenen van de hashwaarde van de inhoud van het opgegeven bestand of de gespecificeerde stroom.</span><span class="sxs-lookup"><span data-stu-id="b5e89-139">Specifies the cryptographic hash function to use for computing the hash value of the contents of the specified file or stream.</span></span> <span data-ttu-id="b5e89-140">Een cryptografische hash-functie heeft de eigenschap die niet haalbaar is om twee verschillende bestanden met dezelfde hashwaarde te vinden.</span><span class="sxs-lookup"><span data-stu-id="b5e89-140">A cryptographic hash function has the property that it is infeasible to find two different files with the same hash value.</span></span> <span data-ttu-id="b5e89-141">Hash-functies worden vaak gebruikt in combi natie met digitale hand tekeningen en gegevens integriteit.</span><span class="sxs-lookup"><span data-stu-id="b5e89-141">Hash functions are commonly used with digital signatures and for data integrity.</span></span> <span data-ttu-id="b5e89-142">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="b5e89-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b5e89-143">SHA1</span><span class="sxs-lookup"><span data-stu-id="b5e89-143">SHA1</span></span>
- <span data-ttu-id="b5e89-144">SHA256</span><span class="sxs-lookup"><span data-stu-id="b5e89-144">SHA256</span></span>
- <span data-ttu-id="b5e89-145">SHA384</span><span class="sxs-lookup"><span data-stu-id="b5e89-145">SHA384</span></span>
- <span data-ttu-id="b5e89-146">SHA512</span><span class="sxs-lookup"><span data-stu-id="b5e89-146">SHA512</span></span>
- <span data-ttu-id="b5e89-147">MACTripleDES</span><span class="sxs-lookup"><span data-stu-id="b5e89-147">MACTripleDES</span></span>
- <span data-ttu-id="b5e89-148">MD5</span><span class="sxs-lookup"><span data-stu-id="b5e89-148">MD5</span></span>
- <span data-ttu-id="b5e89-149">RIPEMD160</span><span class="sxs-lookup"><span data-stu-id="b5e89-149">RIPEMD160</span></span>

<span data-ttu-id="b5e89-150">Als er geen waarde is opgegeven, of als de para meter wordt wegge laten, is de standaard waarde SHA256.</span><span class="sxs-lookup"><span data-stu-id="b5e89-150">If no value is specified, or if the parameter is omitted, the default value is SHA256.</span></span>

<span data-ttu-id="b5e89-151">Om veiligheids redenen moet MD5 en SHA1, die niet meer worden beschouwd als veilig, alleen worden gebruikt voor eenvoudige wijzigings validatie, en mag niet worden gebruikt voor het genereren van hash-waarden voor bestanden die bescherming tegen aanvallen of knoeien vereisen.</span><span class="sxs-lookup"><span data-stu-id="b5e89-151">For security reasons, MD5 and SHA1, which are no longer considered secure, should only be used for simple change validation, and should not be used to generate hash values for files that require protection from attack or tampering.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MACTripleDES, MD5, RIPEMD160

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5e89-152">-InputStream</span><span class="sxs-lookup"><span data-stu-id="b5e89-152">-InputStream</span></span>

<span data-ttu-id="b5e89-153">Hiermee geeft u de invoer stroom op.</span><span class="sxs-lookup"><span data-stu-id="b5e89-153">Specifies the input stream.</span></span>

```yaml
Type: System.IO.Stream
Parameter Sets: Stream
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5e89-154">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b5e89-154">-LiteralPath</span></span>

<span data-ttu-id="b5e89-155">Hiermee geeft u het pad naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="b5e89-155">Specifies the path to a file.</span></span> <span data-ttu-id="b5e89-156">In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt terwijl deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="b5e89-156">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="b5e89-157">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="b5e89-157">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="b5e89-158">Als het pad escape tekens bevat, plaatst u het pad tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="b5e89-158">If the path includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="b5e89-159">Enkele aanhalings tekens geven Power shell opdracht instructies niet te interpreteren als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="b5e89-159">Single quotation marks instruct PowerShell not to interpret characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5e89-160">-Path</span><span class="sxs-lookup"><span data-stu-id="b5e89-160">-Path</span></span>

<span data-ttu-id="b5e89-161">Hiermee geeft u het pad naar een of meer bestanden als een matrix.</span><span class="sxs-lookup"><span data-stu-id="b5e89-161">Specifies the path to one or more files as an array.</span></span> <span data-ttu-id="b5e89-162">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b5e89-162">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b5e89-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5e89-163">CommonParameters</span></span>

<span data-ttu-id="b5e89-164">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b5e89-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b5e89-165">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b5e89-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5e89-166">INVOER</span><span class="sxs-lookup"><span data-stu-id="b5e89-166">INPUTS</span></span>

### <span data-ttu-id="b5e89-167">System. String</span><span class="sxs-lookup"><span data-stu-id="b5e89-167">System.String</span></span>

<span data-ttu-id="b5e89-168">U kunt een teken reeks door sluizen naar de `Get-FileHash` cmdlet die een pad naar een of meer bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="b5e89-168">You can pipe a string to the `Get-FileHash` cmdlet that contains a path to one or more files.</span></span>

## <span data-ttu-id="b5e89-169">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b5e89-169">OUTPUTS</span></span>

### <span data-ttu-id="b5e89-170">Micro soft. Power shell. Utility. FileHash</span><span class="sxs-lookup"><span data-stu-id="b5e89-170">Microsoft.Powershell.Utility.FileHash</span></span>

<span data-ttu-id="b5e89-171">`Get-FileHash` retourneert een-object dat het pad naar het opgegeven bestand vertegenwoordigt, de waarde van de berekende hash en de algoritme die wordt gebruikt om de hash te berekenen.</span><span class="sxs-lookup"><span data-stu-id="b5e89-171">`Get-FileHash` returns an object that represents the path to the specified file, the value of the computed hash, and the algorithm used to compute the hash.</span></span>

## <span data-ttu-id="b5e89-172">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b5e89-172">NOTES</span></span>

## <span data-ttu-id="b5e89-173">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b5e89-173">RELATED LINKS</span></span>

[<span data-ttu-id="b5e89-174">Format-List</span><span class="sxs-lookup"><span data-stu-id="b5e89-174">Format-List</span></span>](Format-List.md)
