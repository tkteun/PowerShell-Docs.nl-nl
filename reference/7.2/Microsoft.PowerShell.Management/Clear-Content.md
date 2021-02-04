---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: 8024dc8a4a041fad783f1234477ee4b5920e7b00
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693062"
---
# <span data-ttu-id="cbff1-102">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="cbff1-102">Clear-Content</span></span>

## <span data-ttu-id="cbff1-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cbff1-103">SYNOPSIS</span></span>
<span data-ttu-id="cbff1-104">Hiermee verwijdert u de inhoud van een item, maar verwijdert u het item niet.</span><span class="sxs-lookup"><span data-stu-id="cbff1-104">Deletes the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="cbff1-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cbff1-105">SYNTAX</span></span>

### <span data-ttu-id="cbff1-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="cbff1-106">Path (Default)</span></span>

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

### <span data-ttu-id="cbff1-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cbff1-107">LiteralPath</span></span>

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

## <span data-ttu-id="cbff1-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cbff1-108">DESCRIPTION</span></span>

<span data-ttu-id="cbff1-109">De `Clear-Content` cmdlet verwijdert de inhoud van een item, zoals het verwijderen van de tekst uit een bestand, maar het item wordt niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="cbff1-109">The `Clear-Content` cmdlet deletes the contents of an item, such as deleting the text from a file, but it does not delete the item.</span></span>
<span data-ttu-id="cbff1-110">Als gevolg hiervan bestaat het item wel, maar is het leeg.</span><span class="sxs-lookup"><span data-stu-id="cbff1-110">As a result, the item exists, but it is empty.</span></span>
<span data-ttu-id="cbff1-111">Het `Clear-Content` is vergelijkbaar met `Clear-Item` , maar het werkt op items met inhoud in plaats van items met waarden.</span><span class="sxs-lookup"><span data-stu-id="cbff1-111">The `Clear-Content` is similar to `Clear-Item`, but it works on items with contents, instead of items with values.</span></span>

## <span data-ttu-id="cbff1-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cbff1-112">EXAMPLES</span></span>

### <span data-ttu-id="cbff1-113">Voor beeld 1: alle inhoud uit een map verwijderen</span><span class="sxs-lookup"><span data-stu-id="cbff1-113">Example 1: Delete all content from a directory</span></span>

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

<span data-ttu-id="cbff1-114">Met deze opdracht wordt alle inhoud verwijderd uit de "init.txt"-bestanden in alle submappen van de SmpUsers-map.</span><span class="sxs-lookup"><span data-stu-id="cbff1-114">This command deletes all of the content from the "init.txt" files in all subdirectories of the SmpUsers directory.</span></span>
<span data-ttu-id="cbff1-115">De bestanden worden niet verwijderd, maar ze zijn leeg.</span><span class="sxs-lookup"><span data-stu-id="cbff1-115">The files are not deleted, but they are empty.</span></span>

### <span data-ttu-id="cbff1-116">Voor beeld 2: inhoud van alle bestanden met een Joker teken verwijderen</span><span class="sxs-lookup"><span data-stu-id="cbff1-116">Example 2: Delete content of all files with a wildcard</span></span>

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

<span data-ttu-id="cbff1-117">Met deze opdracht wordt de inhoud van alle bestanden in de huidige map verwijderd met de bestandsnaam extensie. log, inclusief bestanden met het kenmerk alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="cbff1-117">This command deletes the contents of all files in the current directory with the ".log" file name extension, including files with the read-only attribute.</span></span> <span data-ttu-id="cbff1-118">Het sterretje ( \* ) in het pad staat voor alle items in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="cbff1-118">The asterisk (\*) in the path represents all items in the current directory.</span></span> <span data-ttu-id="cbff1-119">Met de para meter **Force** is de opdracht geldig voor alleen-lezen bestanden.</span><span class="sxs-lookup"><span data-stu-id="cbff1-119">The **Force** parameter makes the command effective on read-only files.</span></span> <span data-ttu-id="cbff1-120">Het gebruik van een filter om de opdracht te beperken tot bestanden met de bestandsnaam extensie. log in plaats van op te geven \* . in het pad wordt de bewerking sneller uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cbff1-120">Using a filter to restrict the command to files with the .log file name extension instead of specifying \*.log in the path makes the operation faster.</span></span>

### <span data-ttu-id="cbff1-121">Voor beeld 3: alle gegevens uit een stroom wissen</span><span class="sxs-lookup"><span data-stu-id="cbff1-121">Example 3: Clear all data from a stream</span></span>

<span data-ttu-id="cbff1-122">In dit voor beeld ziet u hoe de `Clear-Content` cmdlet de inhoud uit een alternatieve gegevens stroom wist terwijl de stroom intact blijft.</span><span class="sxs-lookup"><span data-stu-id="cbff1-122">This example shows how the `Clear-Content` cmdlet clears the content from an alternate data stream while leaving the stream intact.</span></span>

<span data-ttu-id="cbff1-123">Met de eerste opdracht wordt de- `Get-Content` cmdlet gebruikt om de inhoud van de `Zone.Identifier` stroom op te halen in het Copy-Script.ps1-bestand, dat is gedownload van het internet.</span><span class="sxs-lookup"><span data-stu-id="cbff1-123">The first command uses the `Get-Content` cmdlet to get the content of the `Zone.Identifier` stream in the Copy-Script.ps1 file, which was downloaded from the Internet.</span></span>

<span data-ttu-id="cbff1-124">Met de tweede opdracht wordt de- `Clear-Content` cmdlet gebruikt om de inhoud te wissen.</span><span class="sxs-lookup"><span data-stu-id="cbff1-124">The second command uses the `Clear-Content` cmdlet to clear the content.</span></span>

<span data-ttu-id="cbff1-125">Met de derde opdracht wordt de eerste opdracht herhaald.</span><span class="sxs-lookup"><span data-stu-id="cbff1-125">The third command repeats the first command.</span></span> <span data-ttu-id="cbff1-126">Er wordt gecontroleerd of de inhoud is gewist, maar de stroom blijft.</span><span class="sxs-lookup"><span data-stu-id="cbff1-126">It verifies that the content is cleared, but the stream remains.</span></span> <span data-ttu-id="cbff1-127">Als de stroom is verwijderd, wordt door de opdracht een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="cbff1-127">If the stream were deleted, the command would generate an error.</span></span>

<span data-ttu-id="cbff1-128">U kunt een methode als deze gebruiken om de inhoud van een alternatieve gegevens stroom te wissen.</span><span class="sxs-lookup"><span data-stu-id="cbff1-128">You can use a method like this one to clear the content of an alternate data stream.</span></span> <span data-ttu-id="cbff1-129">Het is echter niet de aanbevolen manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="cbff1-129">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="cbff1-130">Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cbff1-130">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

```
PS C:\> Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

[ZoneTransfer]
ZoneId=3

PS C:\>Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

PS C:\>Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
PS C:\>
```

## <span data-ttu-id="cbff1-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cbff1-131">PARAMETERS</span></span>

### <span data-ttu-id="cbff1-132">-Stream</span><span class="sxs-lookup"><span data-stu-id="cbff1-132">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="cbff1-133">Deze para meter is alleen beschikbaar in Windows.</span><span class="sxs-lookup"><span data-stu-id="cbff1-133">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="cbff1-134">Hiermee geeft u een alternatieve gegevens stroom voor inhoud.</span><span class="sxs-lookup"><span data-stu-id="cbff1-134">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="cbff1-135">Als de stroom niet bestaat, wordt deze gemaakt met deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cbff1-135">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="cbff1-136">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="cbff1-136">Wildcard characters are not supported.</span></span>

<span data-ttu-id="cbff1-137">**Stream** is een dynamische para meter waaraan de File System Provider toevoegt `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="cbff1-137">**Stream** is a dynamic parameter that the FileSystem provider adds to `Clear-Content`.</span></span> <span data-ttu-id="cbff1-138">Deze para meter werkt alleen in bestandssysteem stations en verwijdert de inhoud van alternatieve gegevens stromen voor bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="cbff1-138">This parameter works only in file system drives, and will clear the content of alternative data streams on both files and directories.</span></span>

<span data-ttu-id="cbff1-139">U kunt de `Clear-Content` cmdlet gebruiken om de inhoud van een alternatieve gegevens stroom van Amy te wijzigen, zoals `Zone.Identifier` .</span><span class="sxs-lookup"><span data-stu-id="cbff1-139">You can use the `Clear-Content` cmdlet to change the content of amy alternate data stream, such as `Zone.Identifier`.</span></span> <span data-ttu-id="cbff1-140">Dit wordt echter niet aangeraden als een manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="cbff1-140">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="cbff1-141">Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cbff1-141">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="cbff1-142">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cbff1-142">This parameter was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="cbff1-143">Vanaf Power shell 7,2 `Clear-Content` kan de inhoud van alternatieve gegevens stromen van mappen en bestanden worden gewist.</span><span class="sxs-lookup"><span data-stu-id="cbff1-143">As of PowerShell 7.2, `Clear-Content` can clear the content of alternative data streams from directories as well as files.</span></span>

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

### <span data-ttu-id="cbff1-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="cbff1-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="cbff1-145">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="cbff1-145">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="cbff1-146">Gebruik invoke-Command om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cbff1-146">To impersonate another user, or elevate your credentials when running this cmdlet, use Invoke-Command.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cbff1-147">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="cbff1-147">-Exclude</span></span>

<span data-ttu-id="cbff1-148">Hiermee geeft u als teken reeks matrix teken reeksen op die met deze cmdlet worden wegge laten van het pad naar de inhoud.</span><span class="sxs-lookup"><span data-stu-id="cbff1-148">Specifies, as a string array, strings that this cmdlet omits from the path to the content.</span></span> <span data-ttu-id="cbff1-149">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="cbff1-149">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="cbff1-150">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="cbff1-150">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="cbff1-151">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="cbff1-151">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="cbff1-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="cbff1-152">-Filter</span></span>

<span data-ttu-id="cbff1-153">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="cbff1-153">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="cbff1-154">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="cbff1-154">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="cbff1-155">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="cbff1-155">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="cbff1-156">Filters zijn efficiënter dan andere para meters, omdat de provider deze toepast tijdens het ophalen van de objecten, in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cbff1-156">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="cbff1-157">-Force</span><span class="sxs-lookup"><span data-stu-id="cbff1-157">-Force</span></span>

<span data-ttu-id="cbff1-158">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="cbff1-158">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="cbff1-159">-Include</span><span class="sxs-lookup"><span data-stu-id="cbff1-159">-Include</span></span>

<span data-ttu-id="cbff1-160">Hiermee geeft u als een teken reeks matrix inhoud op die door deze cmdlet wordt gewist.</span><span class="sxs-lookup"><span data-stu-id="cbff1-160">Specifies, as a string array, content that this cmdlet clears.</span></span> <span data-ttu-id="cbff1-161">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="cbff1-161">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="cbff1-162">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="cbff1-162">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="cbff1-163">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="cbff1-163">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="cbff1-164">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cbff1-164">-LiteralPath</span></span>

<span data-ttu-id="cbff1-165">Hiermee geeft u de paden op naar de items waarvan de inhoud wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="cbff1-165">Specifies the paths to the items from which content is deleted.</span></span> <span data-ttu-id="cbff1-166">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="cbff1-166">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="cbff1-167">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="cbff1-167">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="cbff1-168">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="cbff1-168">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="cbff1-169">Enkele aanhalings tekens geven aan dat Power shell geen karakters kan interpreteren als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="cbff1-169">Single quotation marks tell having PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cbff1-170">-Path</span><span class="sxs-lookup"><span data-stu-id="cbff1-170">-Path</span></span>

<span data-ttu-id="cbff1-171">Hiermee geeft u de paden op naar de items waarvan de inhoud wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="cbff1-171">Specifies the paths to the items from which content is deleted.</span></span> <span data-ttu-id="cbff1-172">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="cbff1-172">Wildcards are permitted.</span></span> <span data-ttu-id="cbff1-173">De paden moeten paden naar items zijn en niet naar containers.</span><span class="sxs-lookup"><span data-stu-id="cbff1-173">The paths must be paths to items, not to containers.</span></span> <span data-ttu-id="cbff1-174">U moet bijvoorbeeld een pad naar een of meer bestanden opgeven, niet een pad naar een map.</span><span class="sxs-lookup"><span data-stu-id="cbff1-174">For example, you must specify a path to one or more files, not a path to a directory.</span></span> <span data-ttu-id="cbff1-175">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="cbff1-175">Wildcards are permitted.</span></span> <span data-ttu-id="cbff1-176">Deze para meter is vereist, maar de parameter naam ("pad") is optioneel.</span><span class="sxs-lookup"><span data-stu-id="cbff1-176">This parameter is required, but the parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="cbff1-177">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cbff1-177">-Confirm</span></span>

<span data-ttu-id="cbff1-178">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cbff1-178">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cbff1-179">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cbff1-179">-WhatIf</span></span>

<span data-ttu-id="cbff1-180">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cbff1-180">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cbff1-181">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cbff1-181">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cbff1-182">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cbff1-182">CommonParameters</span></span>

<span data-ttu-id="cbff1-183">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cbff1-183">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cbff1-184">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cbff1-184">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cbff1-185">INVOER</span><span class="sxs-lookup"><span data-stu-id="cbff1-185">INPUTS</span></span>

### <span data-ttu-id="cbff1-186">Geen</span><span class="sxs-lookup"><span data-stu-id="cbff1-186">None</span></span>

<span data-ttu-id="cbff1-187">U kunt geen objecten pipeen naar `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="cbff1-187">You cannot pipe objects to `Clear-Content`.</span></span>

## <span data-ttu-id="cbff1-188">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cbff1-188">OUTPUTS</span></span>

### <span data-ttu-id="cbff1-189">Geen</span><span class="sxs-lookup"><span data-stu-id="cbff1-189">None</span></span>

<span data-ttu-id="cbff1-190">Met deze cmdlet worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cbff1-190">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="cbff1-191">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cbff1-191">NOTES</span></span>

<span data-ttu-id="cbff1-192">U kunt gebruiken `Clear-Content` met de Power shell-bestandssysteem provider en met andere providers die inhoud bewerken.</span><span class="sxs-lookup"><span data-stu-id="cbff1-192">You can use `Clear-Content` with the PowerShell FileSystem provider and with other providers that manipulate content.</span></span> <span data-ttu-id="cbff1-193">Als u items wilt wissen die niet worden beschouwd als inhoud, zoals items die worden beheerd door het Power shell-certificaat of register providers, gebruikt u `Clear-Item` .</span><span class="sxs-lookup"><span data-stu-id="cbff1-193">To clear items that are not considered to be content, such as items managed by the PowerShell Certificate or Registry providers, use `Clear-Item`.</span></span>

<span data-ttu-id="cbff1-194">De `Clear-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cbff1-194">The `Clear-Content` cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="cbff1-195">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="cbff1-195">To list the providers available in your session, type `Get-PsProvider`.</span></span>
<span data-ttu-id="cbff1-196">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cbff1-196">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="cbff1-197">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cbff1-197">RELATED LINKS</span></span>

[<span data-ttu-id="cbff1-198">Add-content</span><span class="sxs-lookup"><span data-stu-id="cbff1-198">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="cbff1-199">Get-Content</span><span class="sxs-lookup"><span data-stu-id="cbff1-199">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="cbff1-200">Get-item</span><span class="sxs-lookup"><span data-stu-id="cbff1-200">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="cbff1-201">Set-Content</span><span class="sxs-lookup"><span data-stu-id="cbff1-201">Set-Content</span></span>](Set-Content.md)

[<span data-ttu-id="cbff1-202">about_Providers</span><span class="sxs-lookup"><span data-stu-id="cbff1-202">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)