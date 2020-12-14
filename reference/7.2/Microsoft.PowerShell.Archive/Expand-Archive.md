---
external help file: Microsoft.PowerShell.Archive-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: a4cf8970156f524578f7c9747aef1ffbf9f3eb58
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705984"
---
# <span data-ttu-id="596f2-102">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="596f2-102">Expand-Archive</span></span>

## <span data-ttu-id="596f2-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="596f2-103">SYNOPSIS</span></span>
<span data-ttu-id="596f2-104">Hiermee worden bestanden uitgepakt uit een opgegeven archief bestand (zip).</span><span class="sxs-lookup"><span data-stu-id="596f2-104">Extracts files from a specified archive (zipped) file.</span></span>

## <span data-ttu-id="596f2-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="596f2-105">SYNTAX</span></span>

### <span data-ttu-id="596f2-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="596f2-106">Path (Default)</span></span>

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="596f2-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="596f2-107">LiteralPath</span></span>

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="596f2-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="596f2-108">DESCRIPTION</span></span>

<span data-ttu-id="596f2-109">`Expand-Archive`Met de cmdlet worden bestanden uit een opgegeven gezipt archief bestand uitgepakt naar een opgegeven doelmap.</span><span class="sxs-lookup"><span data-stu-id="596f2-109">The `Expand-Archive` cmdlet extracts files from a specified zipped archive file to a specified destination folder.</span></span> <span data-ttu-id="596f2-110">Met een archief bestand kunnen meerdere bestanden worden verpakt en optioneel gecomprimeerd in één ZIP-bestand, voor een eenvoudigere distributie en opslag.</span><span class="sxs-lookup"><span data-stu-id="596f2-110">An archive file allows multiple files to be packaged, and optionally compressed, into a single zipped file for easier distribution and storage.</span></span>

## <span data-ttu-id="596f2-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="596f2-111">EXAMPLES</span></span>

### <span data-ttu-id="596f2-112">Voor beeld 1: de inhoud van een archief extra heren</span><span class="sxs-lookup"><span data-stu-id="596f2-112">Example 1: Extract the contents of an archive</span></span>

<span data-ttu-id="596f2-113">In dit voor beeld wordt de inhoud van een bestaand archief bestand geëxtraheerd naar de map die is opgegeven door de para meter **doelpad** .</span><span class="sxs-lookup"><span data-stu-id="596f2-113">This example extracts the contents of an existing archive file into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

<span data-ttu-id="596f2-114">In dit voor beeld wordt de para meter **LiteralPath** gebruikt omdat de bestands naam tekens bevat die als Joker teken kunnen worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="596f2-114">In this example, the **LiteralPath** parameter is used because the filename contains characters that could be interpreted as wildcards.</span></span>

### <span data-ttu-id="596f2-115">Voor beeld 2: de inhoud van een archief in de huidige map extra heren</span><span class="sxs-lookup"><span data-stu-id="596f2-115">Example 2: Extract the contents of an archive in the current folder</span></span>

<span data-ttu-id="596f2-116">In dit voor beeld wordt de inhoud van een bestaand archief bestand in de huidige map geëxtraheerd naar de map die is opgegeven door de para meter **doelpad** .</span><span class="sxs-lookup"><span data-stu-id="596f2-116">This example extracts the contents of an existing archive file in the current folder into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## <span data-ttu-id="596f2-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="596f2-117">PARAMETERS</span></span>

### <span data-ttu-id="596f2-118">-Doelpad</span><span class="sxs-lookup"><span data-stu-id="596f2-118">-DestinationPath</span></span>

<span data-ttu-id="596f2-119">`Expand-Archive`Maakt standaard een map op de huidige locatie die dezelfde naam als het zip-bestand heeft.</span><span class="sxs-lookup"><span data-stu-id="596f2-119">By default, `Expand-Archive` creates a folder in the current location that is the same name as the ZIP file.</span></span> <span data-ttu-id="596f2-120">Met de para meter kunt u het pad naar een andere map opgeven.</span><span class="sxs-lookup"><span data-stu-id="596f2-120">The parameter allows you to specify the path to a different folder.</span></span> <span data-ttu-id="596f2-121">De doelmap wordt gemaakt als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="596f2-121">The target folder is created if it does not exist.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: A folder in the current location
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="596f2-122">-Force</span><span class="sxs-lookup"><span data-stu-id="596f2-122">-Force</span></span>

<span data-ttu-id="596f2-123">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="596f2-123">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="596f2-124">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="596f2-124">-LiteralPath</span></span>

<span data-ttu-id="596f2-125">Hiermee geeft u het pad naar een archief bestand.</span><span class="sxs-lookup"><span data-stu-id="596f2-125">Specifies the path to an archive file.</span></span> <span data-ttu-id="596f2-126">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="596f2-126">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="596f2-127">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="596f2-127">Wildcard characters are not supported.</span></span> <span data-ttu-id="596f2-128">Als het pad escape tekens bevat, moet u elk escape teken tussen enkele aanhalings tekens plaatsen om Power shell te instrueren dat tekens niet worden geïnterpreteerd als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="596f2-128">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="596f2-129">-PassThru</span><span class="sxs-lookup"><span data-stu-id="596f2-129">-PassThru</span></span>

<span data-ttu-id="596f2-130">Zorgt ervoor dat de cmdlet een lijst uitvoer van de bestanden die uit het archief zijn uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="596f2-130">Causes the cmdlet to output a list of the files expanded from the archive.</span></span>

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

### <span data-ttu-id="596f2-131">-Path</span><span class="sxs-lookup"><span data-stu-id="596f2-131">-Path</span></span>

<span data-ttu-id="596f2-132">Hiermee geeft u het pad naar het archief bestand.</span><span class="sxs-lookup"><span data-stu-id="596f2-132">Specifies the path to the archive file.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="596f2-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="596f2-133">-Confirm</span></span>

<span data-ttu-id="596f2-134">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="596f2-134">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="596f2-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="596f2-135">-WhatIf</span></span>

<span data-ttu-id="596f2-136">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="596f2-136">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="596f2-137">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="596f2-137">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="596f2-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="596f2-138">CommonParameters</span></span>
<span data-ttu-id="596f2-139">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="596f2-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="596f2-140">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="596f2-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="596f2-141">INVOER</span><span class="sxs-lookup"><span data-stu-id="596f2-141">INPUTS</span></span>

### <span data-ttu-id="596f2-142">System. String</span><span class="sxs-lookup"><span data-stu-id="596f2-142">System.String</span></span>

<span data-ttu-id="596f2-143">U kunt een teken reeks met een pad naar een bestaand archief bestand door sluizen.</span><span class="sxs-lookup"><span data-stu-id="596f2-143">You can pipe a string that contains a path to an existing archive file.</span></span>

## <span data-ttu-id="596f2-144">UITVOER</span><span class="sxs-lookup"><span data-stu-id="596f2-144">OUTPUTS</span></span>

### <span data-ttu-id="596f2-145">System. IO. FileSystemInfo</span><span class="sxs-lookup"><span data-stu-id="596f2-145">System.IO.FileSystemInfo</span></span>

<span data-ttu-id="596f2-146">Wanneer de `-PassThru` para meter wordt gebruikt, voert de cmdlet een lijst met bestanden uit die zijn uitgevouwen uit het archief.</span><span class="sxs-lookup"><span data-stu-id="596f2-146">When the `-PassThru` parameter is used, the cmdlet outputs a list of files that were expanded from the archive.</span></span>

## <span data-ttu-id="596f2-147">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="596f2-147">NOTES</span></span>

<span data-ttu-id="596f2-148">De [specificatie zip-bestand](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) geeft geen standaard wijze op voor het coderen van bestands namen die niet-ASCII-tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="596f2-148">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="596f2-149">De `Compress-Archive` cmdlet maakt gebruik van UTF-8-code ring.</span><span class="sxs-lookup"><span data-stu-id="596f2-149">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="596f2-150">Andere ZIP-archief hulpprogramma's kunnen gebruikmaken van een ander coderings schema.</span><span class="sxs-lookup"><span data-stu-id="596f2-150">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="596f2-151">Bij het uitpakken van bestanden met bestands namen die niet met UTF-8-code ring zijn opgeslagen, `Expand-Archive` wordt de onbewerkte waarde gebruikt die in het archief is gevonden.</span><span class="sxs-lookup"><span data-stu-id="596f2-151">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="596f2-152">Dit kan resulteren in een bestands naam die verschilt van de bron bestandsnaam die is opgeslagen in het archief.</span><span class="sxs-lookup"><span data-stu-id="596f2-152">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="596f2-153">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="596f2-153">RELATED LINKS</span></span>

[<span data-ttu-id="596f2-154">Comprimeren-archief</span><span class="sxs-lookup"><span data-stu-id="596f2-154">Compress-Archive</span></span>](compress-archive.md)
