---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: 2e4380163c7dc34c84460a1cfef3ef2f4b33507b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250246"
---
# <span data-ttu-id="21411-103">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="21411-103">Start-Transcript</span></span>

## <span data-ttu-id="21411-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="21411-104">SYNOPSIS</span></span>
<span data-ttu-id="21411-105">Hiermee maakt u een record van een Power shell-sessie of een deel ervan aan een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="21411-105">Creates a record of all or part of a PowerShell session to a text file.</span></span>

## <span data-ttu-id="21411-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="21411-106">SYNTAX</span></span>

### <span data-ttu-id="21411-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="21411-107">ByPath (Default)</span></span>

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="21411-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="21411-108">ByLiteralPath</span></span>

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="21411-109">ByOutputDirectory</span><span class="sxs-lookup"><span data-stu-id="21411-109">ByOutputDirectory</span></span>

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="21411-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="21411-110">DESCRIPTION</span></span>

<span data-ttu-id="21411-111">`Start-Transcript`Met de cmdlet maakt u een record van een Power shell-sessie of een deel ervan aan een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="21411-111">The `Start-Transcript` cmdlet creates a record of all or part of a PowerShell session to a text file.</span></span> <span data-ttu-id="21411-112">De transcript bevat alle opdrachten die de gebruiker typt en alle uitvoer die wordt weer gegeven op de-console.</span><span class="sxs-lookup"><span data-stu-id="21411-112">The transcript includes all command that the user types and all output that appears on the console.</span></span>

<span data-ttu-id="21411-113">Vanaf Windows Power shell 5,0 `Start-Transcript` bevat de hostnaam in de gegenereerde bestands naam van alle transcripten.</span><span class="sxs-lookup"><span data-stu-id="21411-113">Starting in Windows PowerShell 5.0, `Start-Transcript` includes the hostname in the generated file name of all transcripts.</span></span> <span data-ttu-id="21411-114">Dit is vooral handig wanneer de logboek registratie van uw onderneming is gecentraliseerd.</span><span class="sxs-lookup"><span data-stu-id="21411-114">This is especially useful when your enterprise's logging is centralized.</span></span>
<span data-ttu-id="21411-115">Bestanden die door de cmdlet worden gemaakt, `Start-Transcript` bevatten wille keurige tekens in namen om te voor komen dat er sprake is van mogelijke overschrijvingen of duplicatie wanneer twee of meer transcripten tegelijk worden gestart.</span><span class="sxs-lookup"><span data-stu-id="21411-115">Files that are created by the `Start-Transcript` cmdlet include random characters in names to prevent potential overwrites or duplication when two or more transcripts are started simultaneously.</span></span>
<span data-ttu-id="21411-116">Dit voor komt ook niet-geautoriseerde detectie van transcripten die zijn opgeslagen in een gecentraliseerde bestands share.</span><span class="sxs-lookup"><span data-stu-id="21411-116">This also prevents unauthorized discovery of transcripts that are stored in a centralized file share.</span></span>

## <span data-ttu-id="21411-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="21411-117">EXAMPLES</span></span>

### <span data-ttu-id="21411-118">Voor beeld 1: een transcript bestand met de standaard instellingen starten</span><span class="sxs-lookup"><span data-stu-id="21411-118">Example 1: Start a transcript file with default settings</span></span>

```powershell
Start-Transcript
```

<span data-ttu-id="21411-119">Met deze opdracht start u een transcriptie op de standaard locatie van het bestand.</span><span class="sxs-lookup"><span data-stu-id="21411-119">This command starts a transcript in the default file location.</span></span>

### <span data-ttu-id="21411-120">Voor beeld 2: een transcript bestand op een specifieke locatie starten</span><span class="sxs-lookup"><span data-stu-id="21411-120">Example 2: Start a transcript file at a specific location</span></span>

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

<span data-ttu-id="21411-121">Met deze opdracht wordt een transcript in het `Transcript0.txt` bestand in geopend `C:\transcripts` .</span><span class="sxs-lookup"><span data-stu-id="21411-121">This command starts a transcript in the `Transcript0.txt` file in `C:\transcripts`.</span></span> <span data-ttu-id="21411-122">Omdat de para meter **NoClobber** wordt gebruikt, wordt voor komen dat bestaande bestanden worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="21411-122">Since the **NoClobber** parameter is used, the command prevents any existing files from being overwritten.</span></span> <span data-ttu-id="21411-123">Als het `Transcript0.txt` bestand al bestaat, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="21411-123">If the `Transcript0.txt` file already exists, the command fails.</span></span>

## <span data-ttu-id="21411-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21411-124">PARAMETERS</span></span>

### <span data-ttu-id="21411-125">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="21411-125">-Append</span></span>

<span data-ttu-id="21411-126">Geeft aan dat met deze cmdlet het nieuwe transcript wordt toegevoegd aan het einde van een bestaand bestand.</span><span class="sxs-lookup"><span data-stu-id="21411-126">Indicates that this cmdlet adds the new transcript to the end of an existing file.</span></span> <span data-ttu-id="21411-127">Gebruik de para meter **Path** om het bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="21411-127">Use the **Path** parameter to specify the file.</span></span>

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

### <span data-ttu-id="21411-128">-Force</span><span class="sxs-lookup"><span data-stu-id="21411-128">-Force</span></span>

<span data-ttu-id="21411-129">Hiermee kan de-cmdlet de transcriptie toevoegen aan een bestaand alleen-lezen bestand.</span><span class="sxs-lookup"><span data-stu-id="21411-129">Allows the cmdlet to append the transcript to an existing read-only file.</span></span> <span data-ttu-id="21411-130">Bij gebruik in een bestand met het kenmerk alleen-lezen, wijzigt de cmdlet de bestands machtiging voor lezen/schrijven.</span><span class="sxs-lookup"><span data-stu-id="21411-130">When used on a read-only file, the cmdlet changes the file permission to read-write.</span></span> <span data-ttu-id="21411-131">De cmdlet kan geen beveiligings beperkingen overschrijven als deze para meter wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="21411-131">The cmdlet cannot override security restrictions when this parameter is used.</span></span>

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

### <span data-ttu-id="21411-132">-IncludeInvocationHeader</span><span class="sxs-lookup"><span data-stu-id="21411-132">-IncludeInvocationHeader</span></span>

<span data-ttu-id="21411-133">Geeft aan dat met deze cmdlet het tijds tempel wordt geregistreerd wanneer opdrachten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="21411-133">Indicates that this cmdlet logs the time stamp when commands are run.</span></span>

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

### <span data-ttu-id="21411-134">-UseMinimalHeader</span><span class="sxs-lookup"><span data-stu-id="21411-134">-UseMinimalHeader</span></span>

<span data-ttu-id="21411-135">Laten voorafgaan door een korte kop voor de transcriptie, in plaats van de gedetailleerde header die standaard is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="21411-135">Prepend a short header to the transcript, instead of the detailed header included by default.</span></span> <span data-ttu-id="21411-136">Deze para meter is toegevoegd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="21411-136">This parameter was added in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="21411-137">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="21411-137">-LiteralPath</span></span>

<span data-ttu-id="21411-138">Hiermee geeft u een locatie naar het transcript bestand op.</span><span class="sxs-lookup"><span data-stu-id="21411-138">Specifies a location to the transcript file.</span></span> <span data-ttu-id="21411-139">In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt terwijl deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="21411-139">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="21411-140">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="21411-140">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="21411-141">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="21411-141">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="21411-142">Enkele aanhalings tekens melden Power shell geen tekens te interpreteren als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="21411-142">Single quotation marks inform PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21411-143">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="21411-143">-NoClobber</span></span>

<span data-ttu-id="21411-144">Hiermee wordt aangegeven dat deze cmdlet geen bestaand bestand overschrijft.</span><span class="sxs-lookup"><span data-stu-id="21411-144">Indicates that this cmdlet will not overwrite of an existing file.</span></span> <span data-ttu-id="21411-145">Als er een transcript bestand bestaat in het opgegeven pad, wordt `Start-Transcript` het bestand standaard zonder waarschuwing overschreven.</span><span class="sxs-lookup"><span data-stu-id="21411-145">By default, if a transcript file exists in the specified path, `Start-Transcript` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21411-146">-Output directory</span><span class="sxs-lookup"><span data-stu-id="21411-146">-OutputDirectory</span></span>

<span data-ttu-id="21411-147">Hiermee geeft u een specifiek pad en een map op waarin een transcript moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="21411-147">Specifies a specific path and folder in which to save a transcript.</span></span> <span data-ttu-id="21411-148">Power shell wijst automatisch de transcript naam toe.</span><span class="sxs-lookup"><span data-stu-id="21411-148">PowerShell automatically assigns the transcript name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21411-149">-Path</span><span class="sxs-lookup"><span data-stu-id="21411-149">-Path</span></span>

<span data-ttu-id="21411-150">Hiermee geeft u een locatie naar het transcript bestand op.</span><span class="sxs-lookup"><span data-stu-id="21411-150">Specifies a location to the transcript file.</span></span> <span data-ttu-id="21411-151">Voer een pad naar een `.txt` bestand in.</span><span class="sxs-lookup"><span data-stu-id="21411-151">Enter a path to a `.txt` file.</span></span> <span data-ttu-id="21411-152">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="21411-152">Wildcards are not permitted.</span></span>

<span data-ttu-id="21411-153">Als u geen pad opgeeft, `Start-Transcript` wordt het pad gebruikt in de waarde van de `$Transcript` globale variabele.</span><span class="sxs-lookup"><span data-stu-id="21411-153">If you do not specify a path, `Start-Transcript` uses the path in the value of the `$Transcript` global variable.</span></span> <span data-ttu-id="21411-154">Als u deze variabele niet hebt gemaakt, `Start-Transcript` slaat de transcripten op in de `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` bestanden.</span><span class="sxs-lookup"><span data-stu-id="21411-154">If you have not created this variable, `Start-Transcript` stores the transcripts in the `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` files.</span></span>

<span data-ttu-id="21411-155">Als een van de mappen in het pad niet bestaat, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="21411-155">If any of the directories in the path do not exist, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21411-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="21411-156">-Confirm</span></span>

<span data-ttu-id="21411-157">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="21411-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="21411-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="21411-158">-WhatIf</span></span>

<span data-ttu-id="21411-159">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="21411-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="21411-160">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="21411-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="21411-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21411-161">CommonParameters</span></span>

<span data-ttu-id="21411-162">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="21411-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="21411-163">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="21411-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="21411-164">INVOER</span><span class="sxs-lookup"><span data-stu-id="21411-164">INPUTS</span></span>

### <span data-ttu-id="21411-165">Geen</span><span class="sxs-lookup"><span data-stu-id="21411-165">None</span></span>

<span data-ttu-id="21411-166">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="21411-166">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="21411-167">UITVOER</span><span class="sxs-lookup"><span data-stu-id="21411-167">OUTPUTS</span></span>

### <span data-ttu-id="21411-168">System. String</span><span class="sxs-lookup"><span data-stu-id="21411-168">System.String</span></span>

<span data-ttu-id="21411-169">Deze cmdlet retourneert een teken reeks die een bevestigings bericht en het pad naar het uitvoer bestand bevat.</span><span class="sxs-lookup"><span data-stu-id="21411-169">This cmdlet returns a string that contains a confirmation message and the path to the output file.</span></span>

## <span data-ttu-id="21411-170">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="21411-170">NOTES</span></span>

<span data-ttu-id="21411-171">Als u een transcript wilt stoppen, gebruikt u de `Stop-Transcript` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="21411-171">To stop a transcript, use the `Stop-Transcript` cmdlet.</span></span>

<span data-ttu-id="21411-172">Als u een volledige sessie wilt vastleggen, voegt `Start-Transcript` u de opdracht toe aan uw profiel.</span><span class="sxs-lookup"><span data-stu-id="21411-172">To record an entire session, add the `Start-Transcript` command to your profile.</span></span> <span data-ttu-id="21411-173">Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="21411-173">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

## <span data-ttu-id="21411-174">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="21411-174">RELATED LINKS</span></span>

[<span data-ttu-id="21411-175">Stoppen-transcriptie</span><span class="sxs-lookup"><span data-stu-id="21411-175">Stop-Transcript</span></span>](Stop-Transcript.md)
