---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: 3bdda43a3996e8ecfe5c26c146190e63796ad130
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251121"
---
# <span data-ttu-id="297a0-103">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="297a0-103">Export-FormatData</span></span>

## <span data-ttu-id="297a0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="297a0-104">SYNOPSIS</span></span>
<span data-ttu-id="297a0-105">Hiermee slaat u de opmaak gegevens van de huidige sessie op in een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="297a0-105">Saves formatting data from the current session in a formatting file.</span></span>

## <span data-ttu-id="297a0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="297a0-106">SYNTAX</span></span>

### <span data-ttu-id="297a0-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="297a0-107">ByPath (Default)</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### <span data-ttu-id="297a0-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="297a0-108">ByLiteralPath</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## <span data-ttu-id="297a0-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="297a0-109">DESCRIPTION</span></span>

<span data-ttu-id="297a0-110">`Export-FormatData`Met de cmdlet worden Power shell-indelings bestanden (format.ps1XML) gemaakt op basis van de opmaak objecten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="297a0-110">The `Export-FormatData` cmdlet creates PowerShell formatting files (format.ps1xml) from the formatting objects in the current session.</span></span> <span data-ttu-id="297a0-111">Hiermee worden de **ExtendedTypeDefinition** -objecten `Get-FormatData` opgehaald die worden geretourneerd en opgeslagen in een bestand met de XML-indeling.</span><span class="sxs-lookup"><span data-stu-id="297a0-111">It takes the **ExtendedTypeDefinition** objects that `Get-FormatData` returns and saves them in a file in XML format.</span></span>

<span data-ttu-id="297a0-112">Power shell gebruikt de gegevens in indelings bestanden (format.ps1XML) om de standaard weergave van Microsoft .NET Framework-objecten in de sessie te genereren.</span><span class="sxs-lookup"><span data-stu-id="297a0-112">PowerShell uses the data in formatting files (format.ps1xml) to generate the default display of Microsoft .NET Framework objects in the session.</span></span> <span data-ttu-id="297a0-113">U kunt de indelings bestanden weer geven en bewerken en de Update-FormatData cmdlet gebruiken om de opmaak gegevens aan een sessie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="297a0-113">You can view and edit the formatting files and use the Update-FormatData cmdlet to add the formatting data to a session.</span></span>

<span data-ttu-id="297a0-114">Zie [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)voor meer informatie over het format teren van bestanden in Power shell.</span><span class="sxs-lookup"><span data-stu-id="297a0-114">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="297a0-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="297a0-115">EXAMPLES</span></span>

### <span data-ttu-id="297a0-116">Voor beeld 1: gegevens van sessie formaat exporteren</span><span class="sxs-lookup"><span data-stu-id="297a0-116">Example 1: Export session format data</span></span>

```powershell
Get-FormatData -TypeName "*" -PowerShellVersion 5.1 | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="297a0-117">Met deze opdracht worden alle indelings gegevens in de sessie geëxporteerd naar het XML-bestand van de AllFormat.ps1.</span><span class="sxs-lookup"><span data-stu-id="297a0-117">This command exports all of the format data in the session to the AllFormat.ps1xml file.</span></span>

<span data-ttu-id="297a0-118">De opdracht gebruikt de `Get-FormatData` cmdlet om de indelings gegevens in de sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="297a0-118">The command uses the `Get-FormatData` cmdlet to get the format data in the session.</span></span> <span data-ttu-id="297a0-119">De waarde van `*` (alle) voor de para meter **TypeName** zorgt ervoor dat de cmdlet alle gegevens in de sessie ophaalt.</span><span class="sxs-lookup"><span data-stu-id="297a0-119">A value of `*` (all) for the **TypeName** parameter directs the cmdlet to get all of the data in the session.</span></span>

<span data-ttu-id="297a0-120">De opdracht maakt gebruik van een pijplijn operator ( `|` ) om de indelings gegevens van de `Get-FormatData` opdracht te verzenden naar de `Export-FormatData` cmdlet, waarmee de indelings gegevens worden geëxporteerd naar het AllFormat.ps1-bestand.</span><span class="sxs-lookup"><span data-stu-id="297a0-120">The command uses a pipeline operator (`|`) to send the format data from the `Get-FormatData` command to the `Export-FormatData` cmdlet, which exports the format data to the AllFormat.ps1 file.</span></span>

<span data-ttu-id="297a0-121">De `Export-FormatData` opdracht gebruikt de para meter **IncludeScriptBlock** voor het insluiten van script blokken in de indelings gegevens in het bestand.</span><span class="sxs-lookup"><span data-stu-id="297a0-121">The `Export-FormatData` command uses the **IncludeScriptBlock** parameter to include script blocks in the format data in the file.</span></span>

### <span data-ttu-id="297a0-122">Voor beeld 2: indelings gegevens exporteren voor een type</span><span class="sxs-lookup"><span data-stu-id="297a0-122">Example 2: Export format data for a type</span></span>

```powershell
$F = Get-FormatData -TypeName "helpinfoshort" -PowerShellVersion 5.1
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="297a0-123">Met deze opdrachten exporteert u de indelings gegevens voor het **HelpInfoShort** -type naar het XML-bestand van de Help.format.ps1.</span><span class="sxs-lookup"><span data-stu-id="297a0-123">These commands export the format data for the **HelpInfoShort** type to the Help.format.ps1xml file.</span></span>

<span data-ttu-id="297a0-124">Met de eerste opdracht wordt de `Get-FormatData` cmdlet gebruikt om de indelings gegevens voor het **HelpInfoShort** -type op te halen. deze worden opgeslagen in de `$F` variabele.</span><span class="sxs-lookup"><span data-stu-id="297a0-124">The first command uses the `Get-FormatData` cmdlet to get the format data for the **HelpInfoShort** type, and it saves it in the `$F` variable.</span></span>

<span data-ttu-id="297a0-125">Met de tweede opdracht wordt de para meter **input object** van de `Export-FormatData` cmdlet gebruikt om de indelings gegevens in te voeren die in de variabele zijn opgeslagen `$F` .</span><span class="sxs-lookup"><span data-stu-id="297a0-125">The second command uses the **InputObject** parameter of the `Export-FormatData` cmdlet to enter the format data saved in the `$F` variable.</span></span> <span data-ttu-id="297a0-126">De para meter **IncludeScriptBlock** wordt ook gebruikt om script blokken in de uitvoer op te neemt.</span><span class="sxs-lookup"><span data-stu-id="297a0-126">It also uses the **IncludeScriptBlock** parameter to include script blocks in the output.</span></span>

### <span data-ttu-id="297a0-127">Voor beeld 3: indelings gegevens exporteren zonder een script blok</span><span class="sxs-lookup"><span data-stu-id="297a0-127">Example 3: Export format data without a script block</span></span>

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" -PowerShellVersion 5.1 | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

<span data-ttu-id="297a0-128">In dit voor beeld ziet u het effect van het weglaten van de para meter **IncludeScriptBlock** van een `Export-FormatData` opdracht.</span><span class="sxs-lookup"><span data-stu-id="297a0-128">This example shows the effect of omitting the **IncludeScriptBlock** parameter from an `Export-FormatData` command.</span></span>

<span data-ttu-id="297a0-129">Met de eerste opdracht wordt de `Get-FormatData` cmdlet gebruikt om de indelings gegevens op te halen voor het object **System. Diagnostics. process** dat door de cmdlet Get-Process wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="297a0-129">The first command uses the `Get-FormatData` cmdlet to get the format data for the **System.Diagnostics.Process** object that the Get-Process cmdlet returns.</span></span> <span data-ttu-id="297a0-130">De opdracht maakt gebruik van een pijplijn operator ( `|` ) voor het verzenden van de opmaak gegevens naar de `Export-FormatData` cmdlet, die deze exporteert naar het Process.format.ps1XML-bestand in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="297a0-130">The command uses a pipeline operator (`|`) to send the formatting data to the `Export-FormatData` cmdlet, which exports it to the Process.format.ps1xml file in the current directory.</span></span>

<span data-ttu-id="297a0-131">In dit geval gebruikt de `Export-FormatData` opdracht de para meter **IncludeScriptBlock** niet.</span><span class="sxs-lookup"><span data-stu-id="297a0-131">In this case, the `Export-FormatData` command does not use the **IncludeScriptBlock** parameter.</span></span>

<span data-ttu-id="297a0-132">De tweede opdracht gebruikt de `Update-FormatData` cmdlet om het Process.format.ps1XML-bestand toe te voegen aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="297a0-132">The second command uses the `Update-FormatData` cmdlet to add the Process.format.ps1xml file to the current session.</span></span> <span data-ttu-id="297a0-133">De opdracht gebruikt de para meter **PrependPath** om ervoor te zorgen dat de opmaak gegevens voor proces objecten in het XML-bestand van de Process.format.ps1worden gevonden vóór de standaard indelings gegevens voor proces objecten.</span><span class="sxs-lookup"><span data-stu-id="297a0-133">The command uses the **PrependPath** parameter to ensure that the formatting data for process objects in the Process.format.ps1xml file is found before the standard formatting data for process objects.</span></span>

<span data-ttu-id="297a0-134">Met de derde opdracht worden de effecten van deze wijziging weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="297a0-134">The third command shows the effects of this change.</span></span> <span data-ttu-id="297a0-135">De opdracht gebruikt de `Get-Process` cmdlet om processen te verkrijgen die namen hebben die met P beginnen. De uitvoer laat zien dat eigenschaps waarden die worden berekend met behulp van script blokken, ontbreken in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="297a0-135">The command uses the `Get-Process` cmdlet to get processes that have names that begin with P. The output shows that property values that are calculated by using script blocks are missing from the display.</span></span>

## <span data-ttu-id="297a0-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="297a0-136">PARAMETERS</span></span>

### <span data-ttu-id="297a0-137">-Force</span><span class="sxs-lookup"><span data-stu-id="297a0-137">-Force</span></span>

<span data-ttu-id="297a0-138">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="297a0-138">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="297a0-139">-IncludeScriptBlock</span><span class="sxs-lookup"><span data-stu-id="297a0-139">-IncludeScriptBlock</span></span>

<span data-ttu-id="297a0-140">Hiermee wordt aangegeven of script blokken in de indelings gegevens worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="297a0-140">Indicates whether script blocks in the format data are exported.</span></span>

<span data-ttu-id="297a0-141">Omdat script blokken code bevatten en kunnen worden gebruikt om schadelijke software te gebruiken, worden deze niet standaard geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="297a0-141">Because script blocks contain code and can be used maliciously, they are not exported by default.</span></span>

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

### <span data-ttu-id="297a0-142">-Input object</span><span class="sxs-lookup"><span data-stu-id="297a0-142">-InputObject</span></span>

<span data-ttu-id="297a0-143">Hiermee geeft u de gegevens objecten opmaken die moeten worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="297a0-143">Specifies the format data objects to be exported.</span></span> <span data-ttu-id="297a0-144">Voer een variabele in die de objecten bevat of een opdracht waarmee de objecten worden opgehaald, zoals een `Get-FormatData` opdracht.</span><span class="sxs-lookup"><span data-stu-id="297a0-144">Enter a variable that contains the objects or a command that gets the objects, such as a `Get-FormatData` command.</span></span> <span data-ttu-id="297a0-145">U kunt de objecten ook door sluizen van `Get-FormatData` naar `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="297a0-145">You can also pipe the objects from `Get-FormatData` to `Export-FormatData`.</span></span>

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="297a0-146">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="297a0-146">-LiteralPath</span></span>

<span data-ttu-id="297a0-147">Hiermee geeft u een locatie op voor het uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="297a0-147">Specifies a location for the output file.</span></span> <span data-ttu-id="297a0-148">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="297a0-148">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="297a0-149">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="297a0-149">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="297a0-150">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="297a0-150">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="297a0-151">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="297a0-151">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="297a0-152">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="297a0-152">-NoClobber</span></span>

<span data-ttu-id="297a0-153">Geeft aan dat de cmdlet bestaande bestanden niet overschrijft.</span><span class="sxs-lookup"><span data-stu-id="297a0-153">Indicates that the cmdlet does not overwrite existing files.</span></span> <span data-ttu-id="297a0-154">Standaard worden `Export-FormatData` bestanden overschreven zonder waarschuwing tenzij het bestand het kenmerk alleen-lezen heeft.</span><span class="sxs-lookup"><span data-stu-id="297a0-154">By default, `Export-FormatData` overwrites files without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="297a0-155">Als u `Export-FormatData` alleen-lezen bestanden wilt overschrijven, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="297a0-155">To direct `Export-FormatData` to overwrite read-only files, use the **Force** parameter.</span></span>

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

### <span data-ttu-id="297a0-156">-Path</span><span class="sxs-lookup"><span data-stu-id="297a0-156">-Path</span></span>

<span data-ttu-id="297a0-157">Hiermee geeft u een locatie op voor het uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="297a0-157">Specifies a location for the output file.</span></span>
<span data-ttu-id="297a0-158">Voer een pad (optioneel) en een bestands naam in met een format.ps1XML-bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="297a0-158">Enter a path (optional) and file name with a format.ps1xml file name extension.</span></span>
<span data-ttu-id="297a0-159">Als u het pad weglaat, `Export-FormatData` maakt het bestand in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="297a0-159">If you omit the path, `Export-FormatData` creates the file in the current directory.</span></span>

<span data-ttu-id="297a0-160">Als u een andere bestands extensie dan. ps1xml gebruikt, `Update-FormatData` wordt het bestand niet door de cmdlet herkend.</span><span class="sxs-lookup"><span data-stu-id="297a0-160">If you use a file name extension other than .ps1xml, the `Update-FormatData` cmdlet will not recognize the file.</span></span>

<span data-ttu-id="297a0-161">Als u een bestaand bestand opgeeft, wordt `Export-FormatData` het bestand overschreven zonder waarschuwing, tenzij het bestand het kenmerk alleen-lezen heeft.</span><span class="sxs-lookup"><span data-stu-id="297a0-161">If you specify an existing file, `Export-FormatData` overwrites the file without warning, unless the file has the read-only attribute.</span></span> <span data-ttu-id="297a0-162">Als u een alleen-lezen bestand wilt overschrijven, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="297a0-162">To overwrite a read-only file, use the **Force** parameter.</span></span> <span data-ttu-id="297a0-163">Gebruik de para meter **NoClobber** om te voor komen dat bestanden worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="297a0-163">To prevent files from being overwritten, use the **NoClobber** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="297a0-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="297a0-164">CommonParameters</span></span>

<span data-ttu-id="297a0-165">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="297a0-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="297a0-166">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="297a0-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="297a0-167">INVOER</span><span class="sxs-lookup"><span data-stu-id="297a0-167">INPUTS</span></span>

### <span data-ttu-id="297a0-168">System. Management. Automation. ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="297a0-168">System.Management.Automation.ExtendedTypeDefinition</span></span>

<span data-ttu-id="297a0-169">U kunt **ExtendedTypeDefinition** -objecten door sluizen van `Get-FormatData` naar `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="297a0-169">You can pipe **ExtendedTypeDefinition** objects from `Get-FormatData` to `Export-FormatData`.</span></span>

## <span data-ttu-id="297a0-170">UITVOER</span><span class="sxs-lookup"><span data-stu-id="297a0-170">OUTPUTS</span></span>

### <span data-ttu-id="297a0-171">Geen</span><span class="sxs-lookup"><span data-stu-id="297a0-171">None</span></span>

<span data-ttu-id="297a0-172">`Export-FormatData` retourneert geen objecten.</span><span class="sxs-lookup"><span data-stu-id="297a0-172">`Export-FormatData` does not return any objects.</span></span>
<span data-ttu-id="297a0-173">Er wordt een bestand gegenereerd en opgeslagen in het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="297a0-173">It generates a file and saves it in the specified path.</span></span>

## <span data-ttu-id="297a0-174">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="297a0-174">NOTES</span></span>

- <span data-ttu-id="297a0-175">Als u een opmaak bestand wilt gebruiken, met inbegrip van een geëxporteerd opmaak bestand, moet het uitvoerings beleid voor de sessie toestaan dat scripts en configuratie bestanden worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="297a0-175">To use any formatting file, including an exported formatting file, the execution policy for the session must allow scripts and configuration files to run.</span></span> <span data-ttu-id="297a0-176">Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="297a0-176">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="297a0-177">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="297a0-177">RELATED LINKS</span></span>

[<span data-ttu-id="297a0-178">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="297a0-178">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="297a0-179">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="297a0-179">Update-FormatData</span></span>](Update-FormatData.md)
