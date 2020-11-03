---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: c4d2e01305e198e9c38ffe09e9ac06cff4d358cf
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "93251448"
---
# <span data-ttu-id="b708a-103">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="b708a-103">Expand-Archive</span></span>

## <span data-ttu-id="b708a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b708a-104">SYNOPSIS</span></span>
<span data-ttu-id="b708a-105">Hiermee worden bestanden uitgepakt uit een opgegeven archief bestand (zip).</span><span class="sxs-lookup"><span data-stu-id="b708a-105">Extracts files from a specified archive (zipped) file.</span></span>

## <span data-ttu-id="b708a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b708a-106">SYNTAX</span></span>

### <span data-ttu-id="b708a-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="b708a-107">Path (Default)</span></span>

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b708a-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b708a-108">LiteralPath</span></span>

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b708a-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b708a-109">DESCRIPTION</span></span>

<span data-ttu-id="b708a-110">`Expand-Archive`Met de cmdlet worden bestanden uit een opgegeven gezipt archief bestand uitgepakt naar een opgegeven doelmap.</span><span class="sxs-lookup"><span data-stu-id="b708a-110">The `Expand-Archive` cmdlet extracts files from a specified zipped archive file to a specified destination folder.</span></span> <span data-ttu-id="b708a-111">Met een archief bestand kunnen meerdere bestanden worden verpakt en optioneel gecomprimeerd in één ZIP-bestand, voor een eenvoudigere distributie en opslag.</span><span class="sxs-lookup"><span data-stu-id="b708a-111">An archive file allows multiple files to be packaged, and optionally compressed, into a single zipped file for easier distribution and storage.</span></span>

## <span data-ttu-id="b708a-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b708a-112">EXAMPLES</span></span>

### <span data-ttu-id="b708a-113">Voor beeld 1: de inhoud van een archief extra heren</span><span class="sxs-lookup"><span data-stu-id="b708a-113">Example 1: Extract the contents of an archive</span></span>

<span data-ttu-id="b708a-114">In dit voor beeld wordt de inhoud van een bestaand archief bestand geëxtraheerd naar de map die is opgegeven door de para meter **doelpad** .</span><span class="sxs-lookup"><span data-stu-id="b708a-114">This example extracts the contents of an existing archive file into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

<span data-ttu-id="b708a-115">In dit voor beeld wordt de para meter **LiteralPath** gebruikt omdat de bestands naam tekens bevat die als Joker teken kunnen worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="b708a-115">In this example, the **LiteralPath** parameter is used because the filename contains characters that could be interpreted as wildcards.</span></span>

### <span data-ttu-id="b708a-116">Voor beeld 2: de inhoud van een archief in de huidige map extra heren</span><span class="sxs-lookup"><span data-stu-id="b708a-116">Example 2: Extract the contents of an archive in the current folder</span></span>

<span data-ttu-id="b708a-117">In dit voor beeld wordt de inhoud van een bestaand archief bestand in de huidige map geëxtraheerd naar de map die is opgegeven door de para meter **doelpad** .</span><span class="sxs-lookup"><span data-stu-id="b708a-117">This example extracts the contents of an existing archive file in the current folder into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## <span data-ttu-id="b708a-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b708a-118">PARAMETERS</span></span>

### <span data-ttu-id="b708a-119">-Doelpad</span><span class="sxs-lookup"><span data-stu-id="b708a-119">-DestinationPath</span></span>

<span data-ttu-id="b708a-120">`Expand-Archive`Maakt standaard een map op de huidige locatie die dezelfde naam als het zip-bestand heeft.</span><span class="sxs-lookup"><span data-stu-id="b708a-120">By default, `Expand-Archive` creates a folder in the current location that is the same name as the ZIP file.</span></span> <span data-ttu-id="b708a-121">Met de para meter kunt u het pad naar een andere map opgeven.</span><span class="sxs-lookup"><span data-stu-id="b708a-121">The parameter allows you to specify the path to a different folder.</span></span> <span data-ttu-id="b708a-122">De doelmap wordt gemaakt als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="b708a-122">The target folder is created if it does not exist.</span></span>

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

### <span data-ttu-id="b708a-123">-Force</span><span class="sxs-lookup"><span data-stu-id="b708a-123">-Force</span></span>

<span data-ttu-id="b708a-124">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="b708a-124">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="b708a-125">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b708a-125">-LiteralPath</span></span>

<span data-ttu-id="b708a-126">Hiermee geeft u het pad naar een archief bestand.</span><span class="sxs-lookup"><span data-stu-id="b708a-126">Specifies the path to an archive file.</span></span> <span data-ttu-id="b708a-127">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="b708a-127">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="b708a-128">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b708a-128">Wildcard characters are not supported.</span></span> <span data-ttu-id="b708a-129">Als het pad escape tekens bevat, moet u elk escape teken tussen enkele aanhalings tekens plaatsen om Power shell te instrueren dat tekens niet worden geïnterpreteerd als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="b708a-129">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="b708a-130">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b708a-130">-PassThru</span></span>

<span data-ttu-id="b708a-131">Zorgt ervoor dat de cmdlet een lijst uitvoer van de bestanden die uit het archief zijn uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="b708a-131">Causes the cmdlet to output a list of the files expanded from the archive.</span></span>

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

### <span data-ttu-id="b708a-132">-Path</span><span class="sxs-lookup"><span data-stu-id="b708a-132">-Path</span></span>

<span data-ttu-id="b708a-133">Hiermee geeft u het pad naar het archief bestand.</span><span class="sxs-lookup"><span data-stu-id="b708a-133">Specifies the path to the archive file.</span></span>

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

### <span data-ttu-id="b708a-134">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b708a-134">-Confirm</span></span>

<span data-ttu-id="b708a-135">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b708a-135">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b708a-136">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b708a-136">-WhatIf</span></span>

<span data-ttu-id="b708a-137">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b708a-137">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b708a-138">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b708a-138">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b708a-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b708a-139">CommonParameters</span></span>
<span data-ttu-id="b708a-140">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b708a-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b708a-141">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b708a-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b708a-142">INVOER</span><span class="sxs-lookup"><span data-stu-id="b708a-142">INPUTS</span></span>

### <span data-ttu-id="b708a-143">System. String</span><span class="sxs-lookup"><span data-stu-id="b708a-143">System.String</span></span>

<span data-ttu-id="b708a-144">U kunt een teken reeks met een pad naar een bestaand archief bestand door sluizen.</span><span class="sxs-lookup"><span data-stu-id="b708a-144">You can pipe a string that contains a path to an existing archive file.</span></span>

## <span data-ttu-id="b708a-145">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b708a-145">OUTPUTS</span></span>

### <span data-ttu-id="b708a-146">System. IO. FileSystemInfo</span><span class="sxs-lookup"><span data-stu-id="b708a-146">System.IO.FileSystemInfo</span></span>

<span data-ttu-id="b708a-147">Wanneer de `-PassThru` para meter wordt gebruikt, voert de cmdlet een lijst met bestanden uit die zijn uitgevouwen uit het archief.</span><span class="sxs-lookup"><span data-stu-id="b708a-147">When the `-PassThru` parameter is used, the cmdlet outputs a list of files that were expanded from the archive.</span></span>

## <span data-ttu-id="b708a-148">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b708a-148">NOTES</span></span>

<span data-ttu-id="b708a-149">De [specificatie zip-bestand](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) geeft geen standaard wijze op voor het coderen van bestands namen die niet-ASCII-tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="b708a-149">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="b708a-150">De `Compress-Archive` cmdlet maakt gebruik van UTF-8-code ring.</span><span class="sxs-lookup"><span data-stu-id="b708a-150">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="b708a-151">Andere ZIP-archief hulpprogramma's kunnen gebruikmaken van een ander coderings schema.</span><span class="sxs-lookup"><span data-stu-id="b708a-151">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="b708a-152">Bij het uitpakken van bestanden met bestands namen die niet met UTF-8-code ring zijn opgeslagen, `Expand-Archive` wordt de onbewerkte waarde gebruikt die in het archief is gevonden.</span><span class="sxs-lookup"><span data-stu-id="b708a-152">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="b708a-153">Dit kan resulteren in een bestands naam die verschilt van de bron bestandsnaam die is opgeslagen in het archief.</span><span class="sxs-lookup"><span data-stu-id="b708a-153">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="b708a-154">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b708a-154">RELATED LINKS</span></span>

[<span data-ttu-id="b708a-155">Comprimeren-archief</span><span class="sxs-lookup"><span data-stu-id="b708a-155">Compress-Archive</span></span>](compress-archive.md)
