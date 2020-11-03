---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 1d5379b22cbc9f501d8fdf50da76d82f1122897b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249712"
---
# <span data-ttu-id="654a5-103">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="654a5-103">Compress-Archive</span></span>

## <span data-ttu-id="654a5-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="654a5-104">SYNOPSIS</span></span>
<span data-ttu-id="654a5-105">Hiermee maakt u een gecomprimeerd archief of zip-bestand van opgegeven bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="654a5-105">Creates a compressed archive, or zipped file, from specified files and directories.</span></span>

## <span data-ttu-id="654a5-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="654a5-106">SYNTAX</span></span>

### <span data-ttu-id="654a5-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="654a5-107">Path (Default)</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="654a5-108">PathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="654a5-108">PathWithUpdate</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="654a5-109">PathWithForce</span><span class="sxs-lookup"><span data-stu-id="654a5-109">PathWithForce</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="654a5-110">LiteralPathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="654a5-110">LiteralPathWithUpdate</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="654a5-111">LiteralPathWithForce</span><span class="sxs-lookup"><span data-stu-id="654a5-111">LiteralPathWithForce</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="654a5-112">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="654a5-112">LiteralPath</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="654a5-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="654a5-113">DESCRIPTION</span></span>

<span data-ttu-id="654a5-114">`Compress-Archive`Met de cmdlet maakt u een gecomprimeerd of zip-archief bestand van een of meer opgegeven bestanden of mappen.</span><span class="sxs-lookup"><span data-stu-id="654a5-114">The `Compress-Archive` cmdlet creates a compressed, or zipped, archive file from one or more specified files or directories.</span></span> <span data-ttu-id="654a5-115">Een archief verpakt meerdere bestanden, met optionele compressie, in één ZIP-bestand voor eenvoudigere distributie en opslag.</span><span class="sxs-lookup"><span data-stu-id="654a5-115">An archive packages multiple files, with optional compression, into a single zipped file for easier distribution and storage.</span></span> <span data-ttu-id="654a5-116">Een archief bestand kan worden gecomprimeerd met behulp van het compressie algoritme dat is opgegeven door de para meter **CompressionLevel** .</span><span class="sxs-lookup"><span data-stu-id="654a5-116">An archive file can be compressed by using the compression algorithm specified by the **CompressionLevel** parameter.</span></span>

<span data-ttu-id="654a5-117">De `Compress-Archive` cmdlet gebruikt de Microsoft .net-API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) om bestanden te comprimeren.</span><span class="sxs-lookup"><span data-stu-id="654a5-117">The `Compress-Archive` cmdlet uses the Microsoft .NET API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) to compress files.</span></span>
<span data-ttu-id="654a5-118">De maximale bestands grootte is 2 GB omdat de onderliggende API wordt beperkt.</span><span class="sxs-lookup"><span data-stu-id="654a5-118">The maximum file size is 2 GB because there's a limitation of the underlying API.</span></span>

<span data-ttu-id="654a5-119">Enkele voor beelden gebruiken splatting om de regel lengte van de code voorbeelden te reduceren.</span><span class="sxs-lookup"><span data-stu-id="654a5-119">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="654a5-120">Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="654a5-120">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="654a5-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="654a5-121">EXAMPLES</span></span>

### <span data-ttu-id="654a5-122">Voor beeld 1: bestanden comprimeren om een archief bestand te maken</span><span class="sxs-lookup"><span data-stu-id="654a5-122">Example 1: Compress files to create an archive file</span></span>

<span data-ttu-id="654a5-123">In dit voor beeld worden bestanden uit verschillende mappen gecomprimeerd en wordt een archief bestand gemaakt.</span><span class="sxs-lookup"><span data-stu-id="654a5-123">This example compresses files from different directories and creates an archive file.</span></span> <span data-ttu-id="654a5-124">Er wordt een Joker teken gebruikt om alle bestanden met een bepaalde bestands extensie op te halen.</span><span class="sxs-lookup"><span data-stu-id="654a5-124">A wildcard is used to get all files with a particular file extension.</span></span> <span data-ttu-id="654a5-125">Er is geen mapstructuur in het archief bestand, omdat alleen bestands namen worden opgegeven in het **pad** .</span><span class="sxs-lookup"><span data-stu-id="654a5-125">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="654a5-126">De para meter **Path** accepteert specifieke bestands namen en bestands namen met Joker tekens, `*.vsd` .</span><span class="sxs-lookup"><span data-stu-id="654a5-126">The **Path** parameter accepts specific file names and file names with wildcards, `*.vsd`.</span></span> <span data-ttu-id="654a5-127">Het **pad** gebruikt een door komma's gescheiden lijst om bestanden uit verschillende mappen op te halen.</span><span class="sxs-lookup"><span data-stu-id="654a5-127">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="654a5-128">Het compressie niveau is het **snelst** om de verwerkings tijd te verminderen.</span><span class="sxs-lookup"><span data-stu-id="654a5-128">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="654a5-129">De **doelpad** para meter geeft u de locatie voor het `Draft.zip` bestand op.</span><span class="sxs-lookup"><span data-stu-id="654a5-129">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="654a5-130">Het `Draft.zip` bestand bevat `Draftdoc.docx` en alle bestanden met een `.vsd` extensie.</span><span class="sxs-lookup"><span data-stu-id="654a5-130">The `Draft.zip` file contains `Draftdoc.docx` and all the files with a `.vsd` extension.</span></span>

### <span data-ttu-id="654a5-131">Voor beeld 2: bestanden comprimeren met een LiteralPath</span><span class="sxs-lookup"><span data-stu-id="654a5-131">Example 2: Compress files using a LiteralPath</span></span>

<span data-ttu-id="654a5-132">In dit voor beeld worden specifieke benoemde bestanden gecomprimeerd en een nieuw archief bestand gemaakt.</span><span class="sxs-lookup"><span data-stu-id="654a5-132">This example compresses specific named files and creates a new archive file.</span></span> <span data-ttu-id="654a5-133">Er is geen mapstructuur in het archief bestand, omdat alleen bestands namen worden opgegeven in het **pad** .</span><span class="sxs-lookup"><span data-stu-id="654a5-133">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="654a5-134">Absolute paden en bestands namen worden gebruikt omdat de para meter **LiteralPath** geen joker tekens accepteert.</span><span class="sxs-lookup"><span data-stu-id="654a5-134">Absolute path and file names are used because the **LiteralPath** parameter doesn't accept wildcards.</span></span> <span data-ttu-id="654a5-135">Het **pad** gebruikt een door komma's gescheiden lijst om bestanden uit verschillende mappen op te halen.</span><span class="sxs-lookup"><span data-stu-id="654a5-135">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="654a5-136">Het compressie niveau is het **snelst** om de verwerkings tijd te verminderen.</span><span class="sxs-lookup"><span data-stu-id="654a5-136">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="654a5-137">De **doelpad** para meter geeft u de locatie voor het `Draft.zip` bestand op.</span><span class="sxs-lookup"><span data-stu-id="654a5-137">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="654a5-138">Het `Draft.zip` bestand bevat alleen `Draftdoc.docx` en `diagram2.vsd` .</span><span class="sxs-lookup"><span data-stu-id="654a5-138">The `Draft.zip` file only contains `Draftdoc.docx` and `diagram2.vsd`.</span></span>

### <span data-ttu-id="654a5-139">Voor beeld 3: een map comprimeren die de hoofdmap bevat</span><span class="sxs-lookup"><span data-stu-id="654a5-139">Example 3: Compress a directory that includes the root directory</span></span>

<span data-ttu-id="654a5-140">In dit voor beeld wordt een map gecomprimeerd en wordt een archief bestand gemaakt dat de hoofdmap **bevat** en alle bijbehorende bestanden en submappen.</span><span class="sxs-lookup"><span data-stu-id="654a5-140">This example compresses a directory and creates an archive file that **includes** the root directory, and all its files and subdirectories.</span></span> <span data-ttu-id="654a5-141">Het archief bestand heeft een mapstructuur, omdat het **pad** een hoofdmap specificeert.</span><span class="sxs-lookup"><span data-stu-id="654a5-141">The archive file has a directory structure because the **Path** specifies a root directory.</span></span>

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="654a5-142">`Compress-Archive` gebruikt de para meter **Path** om de hoofdmap op te geven `C:\Reference` .</span><span class="sxs-lookup"><span data-stu-id="654a5-142">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference`.</span></span> <span data-ttu-id="654a5-143">De **doelpad** para meter geeft u de locatie voor het archief bestand op.</span><span class="sxs-lookup"><span data-stu-id="654a5-143">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="654a5-144">Het `Draft.zip` archief bevat de `Reference` hoofdmap en alle bijbehorende bestanden en submappen.</span><span class="sxs-lookup"><span data-stu-id="654a5-144">The `Draft.zip` archive includes the `Reference` root directory, and all its files and subdirectories.</span></span>

### <span data-ttu-id="654a5-145">Voor beeld 4: een map comprimeren die de hoofdmap uitsluit</span><span class="sxs-lookup"><span data-stu-id="654a5-145">Example 4: Compress a directory that excludes the root directory</span></span>

<span data-ttu-id="654a5-146">In dit voor beeld wordt een map gecomprimeerd en wordt een archief bestand gemaakt dat de hoofdmap **uitsluit** , omdat het **pad** een asterisk () gebruikt als `*` Joker teken.</span><span class="sxs-lookup"><span data-stu-id="654a5-146">This example compresses a directory and creates an archive file that **excludes** the root directory because the **Path** uses an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="654a5-147">Het archief bevat een mapstructuur die de bestanden en submappen van de hoofdmap bevat.</span><span class="sxs-lookup"><span data-stu-id="654a5-147">The archive contains a directory structure that contains the root directory's files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="654a5-148">`Compress-Archive` gebruikt de para meter **Path** om de hoofdmap op te geven `C:\Reference` met een asterisk ( `*` ) als Joker teken.</span><span class="sxs-lookup"><span data-stu-id="654a5-148">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="654a5-149">De **doelpad** para meter geeft u de locatie voor het archief bestand op.</span><span class="sxs-lookup"><span data-stu-id="654a5-149">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="654a5-150">Het `Draft.zip` archief bevat de bestanden en submappen van de hoofdmap.</span><span class="sxs-lookup"><span data-stu-id="654a5-150">The `Draft.zip` archive contains the root directory's files and subdirectories.</span></span> <span data-ttu-id="654a5-151">De `Reference` hoofdmap wordt uitgesloten van het archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-151">The `Reference` root directory is excluded from the archive.</span></span>

### <span data-ttu-id="654a5-152">Voor beeld 5: alleen de bestanden in een hoofdmap comprimeren</span><span class="sxs-lookup"><span data-stu-id="654a5-152">Example 5: Compress only the files in a root directory</span></span>

<span data-ttu-id="654a5-153">In dit voor beeld worden alleen de bestanden in een hoofdmap gecomprimeerd en wordt een archief bestand gemaakt.</span><span class="sxs-lookup"><span data-stu-id="654a5-153">This example compresses only the files in a root directory and creates an archive file.</span></span> <span data-ttu-id="654a5-154">Er is geen mapstructuur in het archief, omdat alleen bestanden zijn gecomprimeerd.</span><span class="sxs-lookup"><span data-stu-id="654a5-154">There's no directory structure in the archive because only files are compressed.</span></span>

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="654a5-155">`Compress-Archive` maakt gebruik van de para meter **Path** om de hoofdmap op te geven, `C:\Reference` met een **sterretje** ( `*.*` ) als Joker teken ().</span><span class="sxs-lookup"><span data-stu-id="654a5-155">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with a **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="654a5-156">De **doelpad** para meter geeft u de locatie voor het archief bestand op.</span><span class="sxs-lookup"><span data-stu-id="654a5-156">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="654a5-157">Het `Draft.zip` archief bevat alleen de `Reference` bestanden van de hoofdmap en de hoofdmap wordt uitgesloten.</span><span class="sxs-lookup"><span data-stu-id="654a5-157">The `Draft.zip` archive only contains the `Reference` root directory's files and the root directory is excluded.</span></span>

### <span data-ttu-id="654a5-158">Voor beeld 6: de pijp lijn gebruiken om bestanden te archiveren</span><span class="sxs-lookup"><span data-stu-id="654a5-158">Example 6: Use the pipeline to archive files</span></span>

<span data-ttu-id="654a5-159">In dit voor beeld worden bestanden via de pijp lijn verzonden om een archief te maken.</span><span class="sxs-lookup"><span data-stu-id="654a5-159">This example sends files down the pipeline to create an archive.</span></span> <span data-ttu-id="654a5-160">Er is geen mapstructuur in het archief bestand, omdat alleen bestands namen worden opgegeven in het **pad** .</span><span class="sxs-lookup"><span data-stu-id="654a5-160">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

<span data-ttu-id="654a5-161">`Get-ChildItem` gebruikt de para meter **Path** om twee bestanden uit verschillende directory's op te geven.</span><span class="sxs-lookup"><span data-stu-id="654a5-161">`Get-ChildItem` uses the **Path** parameter to specify two files from different directories.</span></span> <span data-ttu-id="654a5-162">Elk bestand wordt vertegenwoordigd door een **file info** -object en de pijp lijn wordt naar beneden verzonden `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="654a5-162">Each file is represented by a **FileInfo** object and is sent down the pipeline to `Compress-Archive`.</span></span>
<span data-ttu-id="654a5-163">De twee opgegeven bestanden worden gearchiveerd in `PipelineFiles.zip` .</span><span class="sxs-lookup"><span data-stu-id="654a5-163">The two specified files are archived in `PipelineFiles.zip`.</span></span>

### <span data-ttu-id="654a5-164">Voor beeld 7: de pijp lijn gebruiken om een map te archiveren</span><span class="sxs-lookup"><span data-stu-id="654a5-164">Example 7: Use the pipeline to archive a directory</span></span>

<span data-ttu-id="654a5-165">In dit voor beeld wordt een directory door de pijp lijn verzonden om een archief te maken.</span><span class="sxs-lookup"><span data-stu-id="654a5-165">This example sends a directory down the pipeline to create an archive.</span></span> <span data-ttu-id="654a5-166">Bestanden worden als **DirectoryInfo** -objecten verzonden als **file info** -objecten en-mappen.</span><span class="sxs-lookup"><span data-stu-id="654a5-166">Files are sent as **FileInfo** objects and directories as **DirectoryInfo** objects.</span></span> <span data-ttu-id="654a5-167">De directory structuur van het archief bevat niet de hoofdmap, maar de bijbehorende bestanden en submappen zijn opgenomen in het archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-167">The archive's directory structure doesn't include the root directory, but its files and subdirectories are included in the archive.</span></span>

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

<span data-ttu-id="654a5-168">`Get-ChildItem` maakt gebruik van de para meter **Path** om de hoofdmap op te geven `C:\LogFiles` .</span><span class="sxs-lookup"><span data-stu-id="654a5-168">`Get-ChildItem` uses the **Path** parameter to specify the `C:\LogFiles` root directory.</span></span> <span data-ttu-id="654a5-169">Elk **file info** -en **DirectoryInfo** -object wordt via de pijp lijn verzonden.</span><span class="sxs-lookup"><span data-stu-id="654a5-169">Each **FileInfo** and **DirectoryInfo** object is sent down the pipeline.</span></span>

<span data-ttu-id="654a5-170">`Compress-Archive` elk object wordt toegevoegd aan het `PipelineDir.zip` Archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-170">`Compress-Archive` adds each object to the `PipelineDir.zip` archive.</span></span> <span data-ttu-id="654a5-171">De para meter **Path** is niet opgegeven omdat de pijplijn objecten worden ontvangen in de parameter positie 0.</span><span class="sxs-lookup"><span data-stu-id="654a5-171">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

### <span data-ttu-id="654a5-172">Voor beeld 8: hoe recursie kan invloed hebben op Archief</span><span class="sxs-lookup"><span data-stu-id="654a5-172">Example 8: How recursion can affect archives</span></span>

<span data-ttu-id="654a5-173">In dit voor beeld ziet u hoe herhalingen bestanden in uw archief kunnen dupliceren.</span><span class="sxs-lookup"><span data-stu-id="654a5-173">This example shows how recursion can duplicate files in your archive.</span></span> <span data-ttu-id="654a5-174">Als u bijvoorbeeld gebruikt `Get-ChildItem` met de **recursieve** para meter.</span><span class="sxs-lookup"><span data-stu-id="654a5-174">For example, if you use `Get-ChildItem` with the **Recurse** parameter.</span></span> <span data-ttu-id="654a5-175">Als recursieproces worden elk **file info** -en **DirectoryInfo** -object verzonden naar de pijp lijn en toegevoegd aan het archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-175">As recursion processes, each **FileInfo** and **DirectoryInfo** object is sent down the pipeline and added to the archive.</span></span>

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

<span data-ttu-id="654a5-176">De `C:\TestLog` map bevat geen bestanden.</span><span class="sxs-lookup"><span data-stu-id="654a5-176">The `C:\TestLog` directory doesn't contain any files.</span></span> <span data-ttu-id="654a5-177">Het bevat een submap met de naam `testsub` die het `testlog.txt` bestand bevat.</span><span class="sxs-lookup"><span data-stu-id="654a5-177">It does contain a subdirectory named `testsub` that contains the `testlog.txt` file.</span></span>

<span data-ttu-id="654a5-178">`Get-ChildItem` gebruikt de para meter **Path** om de hoofdmap op te geven `C:\TestLog` .</span><span class="sxs-lookup"><span data-stu-id="654a5-178">`Get-ChildItem` uses the **Path** parameter to specify the root directory, `C:\TestLog`.</span></span> <span data-ttu-id="654a5-179">Met de **recursieve** para meter worden de bestanden en mappen verwerkt.</span><span class="sxs-lookup"><span data-stu-id="654a5-179">The **Recurse** parameter processes the files and directories.</span></span> <span data-ttu-id="654a5-180">Er wordt een **DirectoryInfo** -object gemaakt voor `testsub` en een **file info** -object `testlog.txt` .</span><span class="sxs-lookup"><span data-stu-id="654a5-180">A **DirectoryInfo** object is created for `testsub` and a **FileInfo** object `testlog.txt`.</span></span>

<span data-ttu-id="654a5-181">Elk object wordt naar beneden verzonden in de pijp lijn `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="654a5-181">Each object is sent down the pipeline to `Compress-Archive`.</span></span> <span data-ttu-id="654a5-182">De **doelpad** geeft de locatie voor het archief bestand.</span><span class="sxs-lookup"><span data-stu-id="654a5-182">The **DestinationPath** specifies the location for the archive file.</span></span> <span data-ttu-id="654a5-183">De para meter **Path** is niet opgegeven omdat de pijplijn objecten worden ontvangen in de parameter positie 0.</span><span class="sxs-lookup"><span data-stu-id="654a5-183">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

<span data-ttu-id="654a5-184">In het volgende overzicht wordt de `PipelineRecurse.zip` inhoud van het archief beschreven die een dubbel bestand bevat:</span><span class="sxs-lookup"><span data-stu-id="654a5-184">The following summary describes the `PipelineRecurse.zip` archive's contents that contains a duplicate file:</span></span>

- <span data-ttu-id="654a5-185">Het **DirectoryInfo** -object maakt de `testsub` map en bevat het `testlog.txt` bestand dat de oorspronkelijke mapstructuur weerspiegelt.</span><span class="sxs-lookup"><span data-stu-id="654a5-185">The **DirectoryInfo** object creates the `testsub` directory and contains the `testlog.txt` file, which reflects the original directory structure.</span></span>
- <span data-ttu-id="654a5-186">Het **file info** -object maakt een duplicaat `testlog.txt` in de hoofdmap van het archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-186">The **FileInfo** object creates a duplicate `testlog.txt` in the archive's root.</span></span> <span data-ttu-id="654a5-187">Het duplicaat bestand is gemaakt, omdat de recursie een bestands object naar heeft verzonden `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="654a5-187">The duplicate file is created because recursion sent a file object to `Compress-Archive`.</span></span> <span data-ttu-id="654a5-188">Dit gedrag wordt verwacht omdat elk object dat via de pijp lijn wordt verzonden, wordt toegevoegd aan het archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-188">This behavior is expected because each object sent down the pipeline is added to the archive.</span></span>

### <span data-ttu-id="654a5-189">Voor beeld 9: een bestaand archief bestand bijwerken</span><span class="sxs-lookup"><span data-stu-id="654a5-189">Example 9: Update an existing archive file</span></span>

<span data-ttu-id="654a5-190">In dit voor beeld wordt een bestaand archief bestand `Draft.Zip` in de `C:\Archives` map bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="654a5-190">This example updates an existing archive file, `Draft.Zip`, in the `C:\Archives` directory.</span></span> <span data-ttu-id="654a5-191">In dit voor beeld bevat het bestaande archief bestand de hoofdmap en de bijbehorende bestanden en submappen.</span><span class="sxs-lookup"><span data-stu-id="654a5-191">In this example, the existing archive file contains the root directory, and its files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

<span data-ttu-id="654a5-192">De opdracht wordt bijgewerkt `Draft.Zip` met nieuwere versies van bestaande bestanden in de `C:\Reference` map en de bijbehorende submappen.</span><span class="sxs-lookup"><span data-stu-id="654a5-192">The command updates `Draft.Zip` with newer versions of existing files in the `C:\Reference` directory and its subdirectories.</span></span> <span data-ttu-id="654a5-193">Nieuwe bestanden die zijn toegevoegd aan `C:\Reference` of de submappen daarvan, worden opgenomen in het bijgewerkte `Draft.Zip` Archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-193">And, new files that were added to `C:\Reference` or its subdirectories are included in the updated `Draft.Zip` archive.</span></span>

## <span data-ttu-id="654a5-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="654a5-194">PARAMETERS</span></span>

### <span data-ttu-id="654a5-195">-CompressionLevel</span><span class="sxs-lookup"><span data-stu-id="654a5-195">-CompressionLevel</span></span>

<span data-ttu-id="654a5-196">Hiermee geeft u op hoeveel compressie moet worden toegepast bij het maken van het archief bestand.</span><span class="sxs-lookup"><span data-stu-id="654a5-196">Specifies how much compression to apply when you're creating the archive file.</span></span> <span data-ttu-id="654a5-197">Snellere compressie vereist minder tijd om het bestand te maken, maar kan leiden tot grotere bestands grootten.</span><span class="sxs-lookup"><span data-stu-id="654a5-197">Faster compression requires less time to create the file, but can result in larger file sizes.</span></span>

<span data-ttu-id="654a5-198">Als deze para meter niet is opgegeven, gebruikt de opdracht de standaard waarde, **optimaal**.</span><span class="sxs-lookup"><span data-stu-id="654a5-198">If this parameter isn't specified, the command uses the default value, **Optimal**.</span></span>

<span data-ttu-id="654a5-199">Hier volgen de geldige waarden voor deze para meter:</span><span class="sxs-lookup"><span data-stu-id="654a5-199">The following are the acceptable values for this parameter:</span></span>

- <span data-ttu-id="654a5-200">**Snelst**.</span><span class="sxs-lookup"><span data-stu-id="654a5-200">**Fastest**.</span></span> <span data-ttu-id="654a5-201">Gebruik de snelste compressie methode die beschikbaar is om de verwerkings tijd te verminderen.</span><span class="sxs-lookup"><span data-stu-id="654a5-201">Use the fastest compression method available to reduce processing time.</span></span> <span data-ttu-id="654a5-202">Snellere compressie kan leiden tot grotere bestands grootten.</span><span class="sxs-lookup"><span data-stu-id="654a5-202">Faster compression can result in larger file sizes.</span></span>
- <span data-ttu-id="654a5-203">Geen **compressie**.</span><span class="sxs-lookup"><span data-stu-id="654a5-203">**NoCompression**.</span></span> <span data-ttu-id="654a5-204">De bron bestanden worden niet gecomprimeerd.</span><span class="sxs-lookup"><span data-stu-id="654a5-204">Doesn't compress the source files.</span></span>
- <span data-ttu-id="654a5-205">**Optimaal**.</span><span class="sxs-lookup"><span data-stu-id="654a5-205">**Optimal**.</span></span> <span data-ttu-id="654a5-206">De verwerkings tijd is afhankelijk van de bestands grootte.</span><span class="sxs-lookup"><span data-stu-id="654a5-206">Processing time is dependent on file size.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="654a5-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="654a5-207">-Confirm</span></span>

<span data-ttu-id="654a5-208">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="654a5-208">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="654a5-209">-Doelpad</span><span class="sxs-lookup"><span data-stu-id="654a5-209">-DestinationPath</span></span>

<span data-ttu-id="654a5-210">Deze para meter is vereist en geeft het pad op naar het uitvoer bestand voor het archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-210">This parameter is required and specifies the path to the archive output file.</span></span> <span data-ttu-id="654a5-211">De **doelpad** moet de naam van het zip-bestand bevatten en ofwel het absolute of relatieve pad naar het zip-bestand.</span><span class="sxs-lookup"><span data-stu-id="654a5-211">The **DestinationPath** should include the name of the zipped file, and either the absolute or relative path to the zipped file.</span></span>

<span data-ttu-id="654a5-212">Als de bestands naam in **doelpad** geen `.zip` bestandsnaam extensie heeft, voegt de cmdlet de `.zip` bestandsnaam extensie toe.</span><span class="sxs-lookup"><span data-stu-id="654a5-212">If the file name in **DestinationPath** doesn't have a `.zip` file name extension, the cmdlet adds the `.zip` file name extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="654a5-213">-Force</span><span class="sxs-lookup"><span data-stu-id="654a5-213">-Force</span></span>

<span data-ttu-id="654a5-214">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="654a5-214">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="654a5-215">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="654a5-215">-LiteralPath</span></span>

<span data-ttu-id="654a5-216">Hiermee geeft u het pad of de paden naar de bestanden die u wilt toevoegen aan het gecomprimeerde bestand van het archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-216">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="654a5-217">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="654a5-217">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="654a5-218">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="654a5-218">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="654a5-219">Als het pad escape tekens bevat, moet u elk escape teken tussen enkele aanhalings tekens plaatsen om Power shell te instrueren dat tekens niet worden geïnterpreteerd als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="654a5-219">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>
<span data-ttu-id="654a5-220">Als u meerdere paden wilt opgeven en bestanden wilt toevoegen op meerdere locaties in uw uitvoer zip-bestand, gebruikt u komma's om de paden van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="654a5-220">To specify multiple paths, and include files in multiple locations in your output zipped file, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="654a5-221">-PassThru</span><span class="sxs-lookup"><span data-stu-id="654a5-221">-PassThru</span></span>

<span data-ttu-id="654a5-222">Zorgt ervoor dat de cmdlet een File-object uitvoert dat het gemaakte archief bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="654a5-222">Causes the cmdlet to output a file object representing the archive file created.</span></span>

<span data-ttu-id="654a5-223">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="654a5-223">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="654a5-224">-Path</span><span class="sxs-lookup"><span data-stu-id="654a5-224">-Path</span></span>

<span data-ttu-id="654a5-225">Hiermee geeft u het pad of de paden naar de bestanden die u wilt toevoegen aan het gecomprimeerde bestand van het archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-225">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="654a5-226">Als u meerdere paden wilt opgeven en bestanden op meerdere locaties wilt toevoegen, gebruikt u komma's om de paden van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="654a5-226">To specify multiple paths, and include files in multiple locations, use commas to separate the paths.</span></span>

<span data-ttu-id="654a5-227">Deze para meter accepteert joker tekens.</span><span class="sxs-lookup"><span data-stu-id="654a5-227">This parameter accepts wildcard characters.</span></span> <span data-ttu-id="654a5-228">Met Joker tekens kunt u alle bestanden in een map toevoegen aan het archief bestand.</span><span class="sxs-lookup"><span data-stu-id="654a5-228">Wildcard characters allow you to add all files in a directory to your archive file.</span></span>

<span data-ttu-id="654a5-229">Het gebruik van joker tekens met een root directory is van invloed op de inhoud van het archief:</span><span class="sxs-lookup"><span data-stu-id="654a5-229">Using wildcards with a root directory affects the archive's contents:</span></span>

- <span data-ttu-id="654a5-230">Als u een archief wilt maken dat de hoofdmap **bevat** en alle bijbehorende bestanden en submappen, geeft u de hoofdmap op in het **pad** zonder joker tekens.</span><span class="sxs-lookup"><span data-stu-id="654a5-230">To create an archive that **includes** the root directory, and all its files and subdirectories, specify the root directory in the **Path** without wildcards.</span></span> <span data-ttu-id="654a5-231">Bijvoorbeeld: `-Path C:\Reference`</span><span class="sxs-lookup"><span data-stu-id="654a5-231">For example: `-Path C:\Reference`</span></span>
- <span data-ttu-id="654a5-232">Gebruik het Joker teken asterisk () om een archief te maken dat de hoofdmap **uitsluit** , maar zips alle bestanden en submappen `*` .</span><span class="sxs-lookup"><span data-stu-id="654a5-232">To create an archive that **excludes** the root directory, but zips all its files and subdirectories, use the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="654a5-233">Bijvoorbeeld: `-Path C:\Reference\*`</span><span class="sxs-lookup"><span data-stu-id="654a5-233">For example: `-Path C:\Reference\*`</span></span>
- <span data-ttu-id="654a5-234">Als u een archief wilt maken dat alleen de bestanden in de hoofdmap zips, gebruikt u het Joker teken **Star-punt** ( `*.*` ).</span><span class="sxs-lookup"><span data-stu-id="654a5-234">To create an archive that only zips the files in the root directory, use the **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="654a5-235">Submappen van de hoofdmap worden niet opgenomen in het archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-235">Subdirectories of the root aren't included in the archive.</span></span> <span data-ttu-id="654a5-236">Bijvoorbeeld: `-Path C:\Reference\*.*`</span><span class="sxs-lookup"><span data-stu-id="654a5-236">For example: `-Path C:\Reference\*.*`</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="654a5-237">-Update</span><span class="sxs-lookup"><span data-stu-id="654a5-237">-Update</span></span>

<span data-ttu-id="654a5-238">Hiermee wordt het opgegeven archief bijgewerkt door oudere versies van bestanden in het archief te vervangen door nieuwere bestands versies die dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="654a5-238">Updates the specified archive by replacing older file versions in the archive with newer file versions that have the same names.</span></span> <span data-ttu-id="654a5-239">U kunt deze para meter ook toevoegen om bestanden toe te voegen aan een bestaand archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-239">You can also add this parameter to add files to an existing archive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="654a5-240">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="654a5-240">-WhatIf</span></span>

<span data-ttu-id="654a5-241">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="654a5-241">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="654a5-242">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="654a5-242">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="654a5-243">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="654a5-243">CommonParameters</span></span>

<span data-ttu-id="654a5-244">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="654a5-244">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="654a5-245">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="654a5-245">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="654a5-246">INVOER</span><span class="sxs-lookup"><span data-stu-id="654a5-246">INPUTS</span></span>

### <span data-ttu-id="654a5-247">System. String</span><span class="sxs-lookup"><span data-stu-id="654a5-247">System.String</span></span>

<span data-ttu-id="654a5-248">U kunt een teken reeks met een pad naar een of meer bestanden door sluizen.</span><span class="sxs-lookup"><span data-stu-id="654a5-248">You can pipe a string that contains a path to one or more files.</span></span>

## <span data-ttu-id="654a5-249">UITVOER</span><span class="sxs-lookup"><span data-stu-id="654a5-249">OUTPUTS</span></span>

### <span data-ttu-id="654a5-250">System. IO. file info</span><span class="sxs-lookup"><span data-stu-id="654a5-250">System.IO.FileInfo</span></span>

<span data-ttu-id="654a5-251">De cmdlet retourneert alleen een **file info** -object wanneer u de para meter **PassThru** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="654a5-251">The cmdlet only returns a **FileInfo** object when you use the **PassThru** parameter.</span></span>

## <span data-ttu-id="654a5-252">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="654a5-252">NOTES</span></span>

<span data-ttu-id="654a5-253">Door recursie te gebruiken en objecten naar beneden te verzenden, kunnen de bestanden in uw archief worden gedupliceerd.</span><span class="sxs-lookup"><span data-stu-id="654a5-253">Using recursion and sending objects down the pipeline can duplicate files in your archive.</span></span> <span data-ttu-id="654a5-254">Als u bijvoorbeeld gebruikt `Get-ChildItem` met de **recursieve** para meter, worden elk **file info** -en **DirectoryInfo** -object dat wordt verzonden naar de pijp lijn toegevoegd aan het archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-254">For example, if you use `Get-ChildItem` with the **Recurse** parameter, each **FileInfo** and **DirectoryInfo** object that's sent down the pipeline is added to the archive.</span></span>

<span data-ttu-id="654a5-255">De [specificatie zip-bestand](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) geeft geen standaard wijze op voor het coderen van bestands namen die niet-ASCII-tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="654a5-255">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="654a5-256">De `Compress-Archive` cmdlet maakt gebruik van UTF-8-code ring.</span><span class="sxs-lookup"><span data-stu-id="654a5-256">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="654a5-257">Andere ZIP-archief hulpprogramma's kunnen gebruikmaken van een ander coderings schema.</span><span class="sxs-lookup"><span data-stu-id="654a5-257">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="654a5-258">Bij het uitpakken van bestanden met bestands namen die niet met UTF-8-code ring zijn opgeslagen, `Expand-Archive` wordt de onbewerkte waarde gebruikt die in het archief is gevonden.</span><span class="sxs-lookup"><span data-stu-id="654a5-258">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="654a5-259">Dit kan resulteren in een bestands naam die verschilt van de bron bestandsnaam die is opgeslagen in het archief.</span><span class="sxs-lookup"><span data-stu-id="654a5-259">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="654a5-260">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="654a5-260">RELATED LINKS</span></span>

[<span data-ttu-id="654a5-261">Uitvouwen-archief</span><span class="sxs-lookup"><span data-stu-id="654a5-261">Expand-Archive</span></span>](Expand-Archive.md)

[<span data-ttu-id="654a5-262">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="654a5-262">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)
