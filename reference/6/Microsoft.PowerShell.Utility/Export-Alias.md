---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 5a732573a24da5de2a00bfd29abb3711218c64e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251124"
---
# <span data-ttu-id="7b538-103">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="7b538-103">Export-Alias</span></span>

## <span data-ttu-id="7b538-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7b538-104">SYNOPSIS</span></span>
<span data-ttu-id="7b538-105">Exporteert informatie over momenteel gedefinieerde aliassen naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-105">Exports information about currently defined aliases to a file.</span></span>

## <span data-ttu-id="7b538-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7b538-106">SYNTAX</span></span>

### <span data-ttu-id="7b538-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="7b538-107">ByPath (Default)</span></span>

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7b538-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="7b538-108">ByLiteralPath</span></span>

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7b538-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7b538-109">DESCRIPTION</span></span>

<span data-ttu-id="7b538-110">`Export-Alias`Met de cmdlet worden de aliassen in de huidige sessie geëxporteerd naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-110">The `Export-Alias` cmdlet exports the aliases in the current session to a file.</span></span>
<span data-ttu-id="7b538-111">Als het uitvoer bestand niet bestaat, wordt het door de cmdlet gemaakt.</span><span class="sxs-lookup"><span data-stu-id="7b538-111">If the output file does not exist, the cmdlet will create it.</span></span>

<span data-ttu-id="7b538-112">`Export-Alias` kan de aliassen in een bepaald bereik of alle bereiken exporteren, het kan de gegevens in CSV-indeling genereren of als een reeks Set-Alias opdrachten die u aan een sessie of een Power shell-profiel kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="7b538-112">`Export-Alias` can export the aliases in a particular scope or all scopes, it can generate the data in CSV format or as a series of Set-Alias commands that you can add to a session or to a PowerShell profile.</span></span>

## <span data-ttu-id="7b538-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7b538-113">EXAMPLES</span></span>

### <span data-ttu-id="7b538-114">Voor beeld 1: een alias exporteren</span><span class="sxs-lookup"><span data-stu-id="7b538-114">Example 1: Export an alias</span></span>

```powershell
Export-Alias -Path "alias.csv"
```

<span data-ttu-id="7b538-115">Met deze opdracht worden de huidige alias gegevens geëxporteerd naar een bestand met de naam Alias.csv in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="7b538-115">This command exports current alias information to a file named Alias.csv in the current directory.</span></span>

### <span data-ttu-id="7b538-116">Voor beeld 2: een alias exporteren tenzij het export bestand al bestaat</span><span class="sxs-lookup"><span data-stu-id="7b538-116">Example 2: Export an alias unless the export file already exists</span></span>

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

<span data-ttu-id="7b538-117">Met deze opdracht worden de aliassen in de huidige sessie geëxporteerd naar een Alias.csv-bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-117">This command exports the aliases in the current session to an Alias.csv file.</span></span>

<span data-ttu-id="7b538-118">Omdat de para meter **NoClobber** is opgegeven, mislukt de opdracht als er al een Alias.csv-bestand in de huidige map bestaat.</span><span class="sxs-lookup"><span data-stu-id="7b538-118">Because the **NoClobber** parameter is specified, the command will fail if an Alias.csv file already exists in the current directory.</span></span>

### <span data-ttu-id="7b538-119">Voor beeld 3: aliassen toevoegen aan een bestand</span><span class="sxs-lookup"><span data-stu-id="7b538-119">Example 3: Append aliases to a file</span></span>

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

<span data-ttu-id="7b538-120">Met deze opdracht worden de aliassen in de huidige sessie toegevoegd aan het Alias.csv-bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-120">This command appends the aliases in the current session to the Alias.csv file.</span></span>

<span data-ttu-id="7b538-121">De opdracht gebruikt de para meter **Description** om een beschrijving toe te voegen aan de opmerkingen boven aan het bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-121">The command uses the **Description** parameter to add a description to the comments at the top of the file.</span></span>

<span data-ttu-id="7b538-122">De opdracht gebruikt ook de **Force** -para meter om bestaande Alias.csv-bestanden te overschrijven, zelfs als ze het kenmerk alleen-lezen hebben.</span><span class="sxs-lookup"><span data-stu-id="7b538-122">The command also uses the **Force** parameter to overwrite any existing Alias.csv files, even if they have the read-only attribute.</span></span>

### <span data-ttu-id="7b538-123">Voor beeld 4: aliassen als een script exporteren</span><span class="sxs-lookup"><span data-stu-id="7b538-123">Example 4: Export aliases as a script</span></span>

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

<span data-ttu-id="7b538-124">In dit voor beeld ziet u hoe u de bestands indeling van het script gebruikt die wordt `Export-Alias` gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="7b538-124">This example shows how to use the script file format that `Export-Alias` generates.</span></span>

<span data-ttu-id="7b538-125">Met de eerste opdracht worden de aliassen in de sessie geëxporteerd naar het Alias.ps1-bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-125">The first command exports the aliases in the session to the Alias.ps1 file.</span></span>
<span data-ttu-id="7b538-126">Het gebruikt de **as** -para meter met de waarde script om een bestand te genereren dat een Set-Alias-opdracht voor elke alias bevat.</span><span class="sxs-lookup"><span data-stu-id="7b538-126">It uses the **As** parameter with a value of Script to generate a file that contains a Set-Alias command for each alias.</span></span>

<span data-ttu-id="7b538-127">Met de tweede opdracht worden de aliassen in het Alias.ps1-bestand toegevoegd aan het CurrentUser-CurrentHost-profiel.</span><span class="sxs-lookup"><span data-stu-id="7b538-127">The second command adds the aliases in the Alias.ps1 file to the CurrentUser-CurrentHost profile.</span></span>
<span data-ttu-id="7b538-128">Het pad naar het profiel wordt opgeslagen in de `$Profile` variabele.</span><span class="sxs-lookup"><span data-stu-id="7b538-128">The path to the profile is saved in the `$Profile` variable.</span></span>
<span data-ttu-id="7b538-129">De opdracht gebruikt de- `Get-Content` cmdlet om de aliassen uit het Alias.ps1 bestand en de `Add-Content` cmdlet te verkrijgen om ze aan het profiel toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="7b538-129">The command uses the `Get-Content` cmdlet to get the aliases from the Alias.ps1 file and the `Add-Content` cmdlet to add them to the profile.</span></span>
<span data-ttu-id="7b538-130">Zie about_Profiles voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7b538-130">For more information, see about_Profiles.</span></span>

<span data-ttu-id="7b538-131">De derde en vierde opdracht voegen de aliassen in het Alias.ps1 bestand toe aan een externe sessie op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="7b538-131">The third and fourth commands add the aliases in the Alias.ps1 file to a remote session on the Server01 computer.</span></span>
<span data-ttu-id="7b538-132">De derde opdracht gebruikt de `New-PSSession` cmdlet om de sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="7b538-132">The third command uses the `New-PSSession` cmdlet to create the session.</span></span>
<span data-ttu-id="7b538-133">De vierde opdracht gebruikt de **filepath** -para meter van de `Invoke-Command` cmdlet om het Alias.ps1-bestand in de nieuwe sessie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="7b538-133">The fourth command uses the **FilePath** parameter of the `Invoke-Command` cmdlet to run the Alias.ps1 file in the new session.</span></span>

## <span data-ttu-id="7b538-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7b538-134">PARAMETERS</span></span>

### <span data-ttu-id="7b538-135">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="7b538-135">-Append</span></span>

<span data-ttu-id="7b538-136">Geeft aan dat met deze cmdlet de uitvoer wordt toegevoegd aan het opgegeven bestand, in plaats van de bestaande inhoud van dat bestand te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="7b538-136">Indicates that this cmdlet appends the output to the specified file, rather than overwriting the existing contents of that file.</span></span>

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

### <span data-ttu-id="7b538-137">-As</span><span class="sxs-lookup"><span data-stu-id="7b538-137">-As</span></span>

<span data-ttu-id="7b538-138">Hiermee geeft u de indeling van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="7b538-138">Specifies the output format.</span></span>
<span data-ttu-id="7b538-139">CSV is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="7b538-139">CSV is the default.</span></span>
<span data-ttu-id="7b538-140">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="7b538-140">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7b538-141">Bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-141">CSV.</span></span>
<span data-ttu-id="7b538-142">Indeling met door komma's gescheiden waarden (CSV).</span><span class="sxs-lookup"><span data-stu-id="7b538-142">Comma-separated value (CSV) format.</span></span>
- <span data-ttu-id="7b538-143">Schriften.</span><span class="sxs-lookup"><span data-stu-id="7b538-143">Script.</span></span>
<span data-ttu-id="7b538-144">Hiermee maakt u een `Set-Alias` opdracht voor elke geëxporteerde alias.</span><span class="sxs-lookup"><span data-stu-id="7b538-144">Creates a `Set-Alias` command for each exported alias.</span></span>
<span data-ttu-id="7b538-145">Als u het uitvoer bestand een naam met de extensie. ps1 hebt, kunt u het uitvoeren als een script om de aliassen toe te voegen aan een sessie.</span><span class="sxs-lookup"><span data-stu-id="7b538-145">If you name the output file with a .ps1 file name extension, you can run it as a script to add the aliases to any session.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7b538-146">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7b538-146">-Description</span></span>

<span data-ttu-id="7b538-147">Hiermee geeft u de beschrijving van het geëxporteerde bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-147">Specifies the description of the exported file.</span></span>
<span data-ttu-id="7b538-148">De beschrijving wordt weer gegeven als een opmerking boven aan het bestand, volgens de koptekst informatie.</span><span class="sxs-lookup"><span data-stu-id="7b538-148">The description appears as a comment at the top of the file, following the header information.</span></span>

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

### <span data-ttu-id="7b538-149">-Force</span><span class="sxs-lookup"><span data-stu-id="7b538-149">-Force</span></span>

<span data-ttu-id="7b538-150">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="7b538-150">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="7b538-151">Hiermee wordt het uitvoer bestand overschreven, zelfs als het kenmerk alleen-lezen is ingesteld voor het bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-151">Overwrites the output file, even if the read-only attribute is set on the file.</span></span>

<span data-ttu-id="7b538-152">Standaard worden `Export-Alias` bestanden zonder waarschuwing overschreven, tenzij het kenmerk alleen-lezen of verborgen is ingesteld, of als de para meter **NoClobber** in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7b538-152">By default, `Export-Alias` overwrites files without warning, unless the read-only or hidden attribute is set or the **NoClobber** parameter is used in the command.</span></span>
<span data-ttu-id="7b538-153">De para meter **NoClobber** krijgt voor rang op de para meter **Force** wanneer beide worden gebruikt in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="7b538-153">The **NoClobber** parameter takes precedence over the **Force** parameter when both are used in a command.</span></span>

<span data-ttu-id="7b538-154">De **Force** -para meter kan niet forceren `Export-Alias` om bestanden te overschrijven met het kenmerk Hidden.</span><span class="sxs-lookup"><span data-stu-id="7b538-154">The **Force** parameter cannot force `Export-Alias` to overwrite files with the hidden attribute.</span></span>

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

### <span data-ttu-id="7b538-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7b538-155">-LiteralPath</span></span>

<span data-ttu-id="7b538-156">Hiermee geeft u het pad naar het uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-156">Specifies the path to the output file.</span></span>
<span data-ttu-id="7b538-157">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="7b538-157">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="7b538-158">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="7b538-158">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="7b538-159">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="7b538-159">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="7b538-160">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="7b538-160">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7b538-161">-Name</span><span class="sxs-lookup"><span data-stu-id="7b538-161">-Name</span></span>

<span data-ttu-id="7b538-162">Hiermee geeft u de namen als een matrix van de aliassen die u wilt exporteren.</span><span class="sxs-lookup"><span data-stu-id="7b538-162">Specifies the names as an array of the aliases to export.</span></span>
<span data-ttu-id="7b538-163">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7b538-163">Wildcards are permitted.</span></span>

<span data-ttu-id="7b538-164">`Export-Alias`Exporteert standaard alle aliassen in de sessie of het bereik.</span><span class="sxs-lookup"><span data-stu-id="7b538-164">By default, `Export-Alias` exports all aliases in the session or scope.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="7b538-165">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="7b538-165">-NoClobber</span></span>

<span data-ttu-id="7b538-166">Geeft aan dat deze cmdlet voor komt dat `Export-Alias` bestanden worden overschreven, zelfs niet als de para meter **Force** in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7b538-166">Indicates that this cmdlet prevents `Export-Alias` from overwriting any files, even if the **Force** parameter is used in the command.</span></span>

<span data-ttu-id="7b538-167">Als de para meter **NoClobber** wordt wegge laten, `Export-Alias` wordt een bestaand bestand zonder waarschuwing overschreven, tenzij het kenmerk alleen-lezen is ingesteld voor het bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-167">If the **NoClobber** parameter is omitted, `Export-Alias` will overwrite an existing file without warning, unless the read-only attribute is set on the file.</span></span>
<span data-ttu-id="7b538-168">*NoClobber* heeft voor rang op de para meter **Force** , waarmee `Export-Alias` een bestand kan worden overschreven door het kenmerk alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="7b538-168">*NoClobber* takes precedence over the **Force** parameter, which permits `Export-Alias` to overwrite a file with the read-only attribute.</span></span>

<span data-ttu-id="7b538-169">*NoClobber* verhindert niet dat de **toevoeg** parameter inhoud toevoegt aan een bestaand bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-169">*NoClobber* does not prevent the **Append** parameter from adding content to an existing file.</span></span>

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

### <span data-ttu-id="7b538-170">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7b538-170">-PassThru</span></span>

<span data-ttu-id="7b538-171">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="7b538-171">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="7b538-172">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="7b538-172">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="7b538-173">-Path</span><span class="sxs-lookup"><span data-stu-id="7b538-173">-Path</span></span>

<span data-ttu-id="7b538-174">Hiermee geeft u het pad naar het uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-174">Specifies the path to the output file.</span></span>
<span data-ttu-id="7b538-175">Joker tekens zijn toegestaan, maar de resulterende padwaarde moet worden omgezet in een enkele bestands naam.</span><span class="sxs-lookup"><span data-stu-id="7b538-175">Wildcards are permitted, but the resulting path value must resolve to a single file name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7b538-176">-Bereik</span><span class="sxs-lookup"><span data-stu-id="7b538-176">-Scope</span></span>

<span data-ttu-id="7b538-177">Hiermee geeft u het bereik op waaruit de aliassen moeten worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="7b538-177">Specifies the scope from which the aliases should be exported.</span></span>
<span data-ttu-id="7b538-178">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="7b538-178">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7b538-179">Globaal</span><span class="sxs-lookup"><span data-stu-id="7b538-179">Global</span></span>
- <span data-ttu-id="7b538-180">Lokaal</span><span class="sxs-lookup"><span data-stu-id="7b538-180">Local</span></span>
- <span data-ttu-id="7b538-181">Script</span><span class="sxs-lookup"><span data-stu-id="7b538-181">Script</span></span>
- <span data-ttu-id="7b538-182">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot het aantal bereiken waarbij 0 het huidige bereik is en 1 de bovenliggende scope)</span><span class="sxs-lookup"><span data-stu-id="7b538-182">A number relative to the current scope (0 through the number of scopes where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="7b538-183">De standaard waarde is lokaal.</span><span class="sxs-lookup"><span data-stu-id="7b538-183">The default value is Local.</span></span>
<span data-ttu-id="7b538-184">Zie about_Scopes voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7b538-184">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="7b538-185">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7b538-185">-Confirm</span></span>

<span data-ttu-id="7b538-186">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7b538-186">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7b538-187">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7b538-187">-WhatIf</span></span>

<span data-ttu-id="7b538-188">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7b538-188">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7b538-189">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7b538-189">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7b538-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7b538-190">CommonParameters</span></span>

<span data-ttu-id="7b538-191">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7b538-191">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7b538-192">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7b538-192">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7b538-193">INVOER</span><span class="sxs-lookup"><span data-stu-id="7b538-193">INPUTS</span></span>

### <span data-ttu-id="7b538-194">Geen.</span><span class="sxs-lookup"><span data-stu-id="7b538-194">None.</span></span>

<span data-ttu-id="7b538-195">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="7b538-195">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="7b538-196">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7b538-196">OUTPUTS</span></span>

### <span data-ttu-id="7b538-197">Geen of System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="7b538-197">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="7b538-198">Wanneer u de para meter **PassThru** gebruikt, `Export-Alias` retourneert een **System. Management. Automation. AliasInfo** -object dat de alias vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="7b538-198">When you use the **Passthru** parameter, `Export-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="7b538-199">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="7b538-199">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7b538-200">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7b538-200">NOTES</span></span>

* <span data-ttu-id="7b538-201">U kunt alleen Export-Aliases naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="7b538-201">You can only Export-Aliases to a file.</span></span>

## <span data-ttu-id="7b538-202">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7b538-202">RELATED LINKS</span></span>

[<span data-ttu-id="7b538-203">Get-alias</span><span class="sxs-lookup"><span data-stu-id="7b538-203">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="7b538-204">Import-alias</span><span class="sxs-lookup"><span data-stu-id="7b538-204">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="7b538-205">Nieuwe alias</span><span class="sxs-lookup"><span data-stu-id="7b538-205">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="7b538-206">Set-alias</span><span class="sxs-lookup"><span data-stu-id="7b538-206">Set-Alias</span></span>](Set-Alias.md)
