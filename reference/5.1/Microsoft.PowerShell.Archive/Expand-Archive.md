---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: 41d571747a9b81cafff8c0ca20d5121163ece452
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "93251452"
---
# <span data-ttu-id="1f751-103">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="1f751-103">Expand-Archive</span></span>

## <span data-ttu-id="1f751-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1f751-104">SYNOPSIS</span></span>
<span data-ttu-id="1f751-105">Hiermee worden bestanden uitgepakt uit een opgegeven archief bestand (zip).</span><span class="sxs-lookup"><span data-stu-id="1f751-105">Extracts files from a specified archive (zipped) file.</span></span>

## <span data-ttu-id="1f751-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1f751-106">SYNTAX</span></span>

### <span data-ttu-id="1f751-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="1f751-107">Path (Default)</span></span>

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="1f751-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1f751-108">LiteralPath</span></span>

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="1f751-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1f751-109">DESCRIPTION</span></span>

<span data-ttu-id="1f751-110">`Expand-Archive`Met de cmdlet worden bestanden uit een opgegeven gezipt archief bestand uitgepakt naar een opgegeven doelmap.</span><span class="sxs-lookup"><span data-stu-id="1f751-110">The `Expand-Archive` cmdlet extracts files from a specified zipped archive file to a specified destination folder.</span></span> <span data-ttu-id="1f751-111">Met een archief bestand kunnen meerdere bestanden worden verpakt en optioneel gecomprimeerd in één ZIP-bestand, voor een eenvoudigere distributie en opslag.</span><span class="sxs-lookup"><span data-stu-id="1f751-111">An archive file allows multiple files to be packaged, and optionally compressed, into a single zipped file for easier distribution and storage.</span></span>

## <span data-ttu-id="1f751-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1f751-112">EXAMPLES</span></span>

### <span data-ttu-id="1f751-113">Voor beeld 1: de inhoud van een archief extra heren</span><span class="sxs-lookup"><span data-stu-id="1f751-113">Example 1: Extract the contents of an archive</span></span>

<span data-ttu-id="1f751-114">In dit voor beeld wordt de inhoud van een bestaand archief bestand geëxtraheerd naar de map die is opgegeven door de para meter **doelpad** .</span><span class="sxs-lookup"><span data-stu-id="1f751-114">This example extracts the contents of an existing archive file into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

<span data-ttu-id="1f751-115">In dit voor beeld wordt de para meter **LiteralPath** gebruikt omdat de bestands naam tekens bevat die als Joker teken kunnen worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="1f751-115">In this example, the **LiteralPath** parameter is used because the filename contains characters that could be interpreted as wildcards.</span></span>

### <span data-ttu-id="1f751-116">Voor beeld 2: de inhoud van een archief in de huidige map extra heren</span><span class="sxs-lookup"><span data-stu-id="1f751-116">Example 2: Extract the contents of an archive in the current folder</span></span>

<span data-ttu-id="1f751-117">In dit voor beeld wordt de inhoud van een bestaand archief bestand in de huidige map geëxtraheerd naar de map die is opgegeven door de para meter **doelpad** .</span><span class="sxs-lookup"><span data-stu-id="1f751-117">This example extracts the contents of an existing archive file in the current folder into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## <span data-ttu-id="1f751-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1f751-118">PARAMETERS</span></span>

### <span data-ttu-id="1f751-119">-Doelpad</span><span class="sxs-lookup"><span data-stu-id="1f751-119">-DestinationPath</span></span>

<span data-ttu-id="1f751-120">`Expand-Archive`Maakt standaard een map op de huidige locatie die dezelfde naam als het zip-bestand heeft.</span><span class="sxs-lookup"><span data-stu-id="1f751-120">By default, `Expand-Archive` creates a folder in the current location that is the same name as the ZIP file.</span></span> <span data-ttu-id="1f751-121">Met de para meter kunt u het pad naar een andere map opgeven.</span><span class="sxs-lookup"><span data-stu-id="1f751-121">The parameter allows you to specify the path to a different folder.</span></span> <span data-ttu-id="1f751-122">De doelmap wordt gemaakt als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="1f751-122">The target folder is created if it does not exist.</span></span>

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

### <span data-ttu-id="1f751-123">-Force</span><span class="sxs-lookup"><span data-stu-id="1f751-123">-Force</span></span>

<span data-ttu-id="1f751-124">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="1f751-124">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="1f751-125">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1f751-125">-LiteralPath</span></span>

<span data-ttu-id="1f751-126">Hiermee geeft u het pad naar een archief bestand.</span><span class="sxs-lookup"><span data-stu-id="1f751-126">Specifies the path to an archive file.</span></span> <span data-ttu-id="1f751-127">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="1f751-127">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="1f751-128">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="1f751-128">Wildcard characters are not supported.</span></span> <span data-ttu-id="1f751-129">Als het pad escape tekens bevat, moet u elk escape teken tussen enkele aanhalings tekens plaatsen om Power shell te instrueren dat tekens niet worden geïnterpreteerd als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="1f751-129">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="1f751-130">-Path</span><span class="sxs-lookup"><span data-stu-id="1f751-130">-Path</span></span>

<span data-ttu-id="1f751-131">Hiermee geeft u het pad naar het archief bestand.</span><span class="sxs-lookup"><span data-stu-id="1f751-131">Specifies the path to the archive file.</span></span>

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

### <span data-ttu-id="1f751-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1f751-132">-Confirm</span></span>

<span data-ttu-id="1f751-133">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1f751-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1f751-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1f751-134">-WhatIf</span></span>

<span data-ttu-id="1f751-135">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1f751-135">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1f751-136">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1f751-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1f751-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1f751-137">CommonParameters</span></span>
<span data-ttu-id="1f751-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1f751-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1f751-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1f751-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1f751-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="1f751-140">INPUTS</span></span>

### <span data-ttu-id="1f751-141">System. String</span><span class="sxs-lookup"><span data-stu-id="1f751-141">System.String</span></span>

<span data-ttu-id="1f751-142">U kunt een teken reeks met een pad naar een bestaand archief bestand door sluizen.</span><span class="sxs-lookup"><span data-stu-id="1f751-142">You can pipe a string that contains a path to an existing archive file.</span></span>

## <span data-ttu-id="1f751-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1f751-143">OUTPUTS</span></span>

### <span data-ttu-id="1f751-144">Geen</span><span class="sxs-lookup"><span data-stu-id="1f751-144">None</span></span>

## <span data-ttu-id="1f751-145">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1f751-145">NOTES</span></span>

<span data-ttu-id="1f751-146">De [specificatie zip-bestand](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) geeft geen standaard wijze op voor het coderen van bestands namen die niet-ASCII-tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="1f751-146">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="1f751-147">De `Compress-Archive` cmdlet maakt gebruik van UTF-8-code ring.</span><span class="sxs-lookup"><span data-stu-id="1f751-147">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="1f751-148">Andere ZIP-archief hulpprogramma's kunnen gebruikmaken van een ander coderings schema.</span><span class="sxs-lookup"><span data-stu-id="1f751-148">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="1f751-149">Bij het uitpakken van bestanden met bestands namen die niet met UTF-8-code ring zijn opgeslagen, `Expand-Archive` wordt de onbewerkte waarde gebruikt die in het archief is gevonden.</span><span class="sxs-lookup"><span data-stu-id="1f751-149">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="1f751-150">Dit kan resulteren in een bestands naam die verschilt van de bron bestandsnaam die is opgeslagen in het archief.</span><span class="sxs-lookup"><span data-stu-id="1f751-150">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="1f751-151">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1f751-151">RELATED LINKS</span></span>

[<span data-ttu-id="1f751-152">Comprimeren-archief</span><span class="sxs-lookup"><span data-stu-id="1f751-152">Compress-Archive</span></span>](compress-archive.md)
