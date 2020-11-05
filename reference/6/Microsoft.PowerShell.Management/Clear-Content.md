---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: 2d7575718391052fedea978b6957e5caec0eafdc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250092"
---
# <span data-ttu-id="57dae-103">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="57dae-103">Clear-Content</span></span>

## <span data-ttu-id="57dae-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="57dae-104">SYNOPSIS</span></span>
<span data-ttu-id="57dae-105">Hiermee verwijdert u de inhoud van een item, maar verwijdert u het item niet.</span><span class="sxs-lookup"><span data-stu-id="57dae-105">Deletes the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="57dae-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="57dae-106">SYNTAX</span></span>

### <span data-ttu-id="57dae-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="57dae-107">Path (Default)</span></span>

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

### <span data-ttu-id="57dae-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="57dae-108">LiteralPath</span></span>

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

## <span data-ttu-id="57dae-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="57dae-109">DESCRIPTION</span></span>

<span data-ttu-id="57dae-110">De `Clear-Content` cmdlet verwijdert de inhoud van een item, zoals het verwijderen van de tekst uit een bestand, maar het item wordt niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="57dae-110">The `Clear-Content` cmdlet deletes the contents of an item, such as deleting the text from a file, but it does not delete the item.</span></span>
<span data-ttu-id="57dae-111">Als gevolg hiervan bestaat het item wel, maar is het leeg.</span><span class="sxs-lookup"><span data-stu-id="57dae-111">As a result, the item exists, but it is empty.</span></span>
<span data-ttu-id="57dae-112">Het `Clear-Content` is vergelijkbaar met `Clear-Item` , maar het werkt op items met inhoud in plaats van items met waarden.</span><span class="sxs-lookup"><span data-stu-id="57dae-112">The `Clear-Content` is similar to `Clear-Item`, but it works on items with contents, instead of items with values.</span></span>

## <span data-ttu-id="57dae-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="57dae-113">EXAMPLES</span></span>

### <span data-ttu-id="57dae-114">Voor beeld 1: alle inhoud uit een map verwijderen</span><span class="sxs-lookup"><span data-stu-id="57dae-114">Example 1: Delete all content from a directory</span></span>

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

<span data-ttu-id="57dae-115">Met deze opdracht wordt alle inhoud verwijderd uit de "init.txt"-bestanden in alle submappen van de SmpUsers-map.</span><span class="sxs-lookup"><span data-stu-id="57dae-115">This command deletes all of the content from the "init.txt" files in all subdirectories of the SmpUsers directory.</span></span>
<span data-ttu-id="57dae-116">De bestanden worden niet verwijderd, maar ze zijn leeg.</span><span class="sxs-lookup"><span data-stu-id="57dae-116">The files are not deleted, but they are empty.</span></span>

### <span data-ttu-id="57dae-117">Voor beeld 2: inhoud van alle bestanden met een Joker teken verwijderen</span><span class="sxs-lookup"><span data-stu-id="57dae-117">Example 2: Delete content of all files with a wildcard</span></span>

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

<span data-ttu-id="57dae-118">Met deze opdracht wordt de inhoud van alle bestanden in de huidige map verwijderd met de bestandsnaam extensie. log, inclusief bestanden met het kenmerk alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="57dae-118">This command deletes the contents of all files in the current directory with the ".log" file name extension, including files with the read-only attribute.</span></span>
<span data-ttu-id="57dae-119">Het sterretje ( \* ) in het pad staat voor alle items in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="57dae-119">The asterisk (\*) in the path represents all items in the current directory.</span></span>
<span data-ttu-id="57dae-120">Met de para meter **Force** is de opdracht geldig voor alleen-lezen bestanden.</span><span class="sxs-lookup"><span data-stu-id="57dae-120">The **Force** parameter makes the command effective on read-only files.</span></span>
<span data-ttu-id="57dae-121">Het gebruik van een filter om de opdracht te beperken tot bestanden met de bestandsnaam extensie. log in plaats van op te geven \* . in het pad wordt de bewerking sneller uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="57dae-121">Using a filter to restrict the command to files with the .log file name extension instead of specifying \*.log in the path makes the operation faster.</span></span>

### <span data-ttu-id="57dae-122">Voor beeld 3: alle gegevens uit een stroom wissen</span><span class="sxs-lookup"><span data-stu-id="57dae-122">Example 3: Clear all data from a stream</span></span>

<span data-ttu-id="57dae-123">In dit voor beeld ziet u hoe de `Clear-Content` cmdlet de inhoud uit een alternatieve gegevens stroom wist terwijl de stroom intact blijft.</span><span class="sxs-lookup"><span data-stu-id="57dae-123">This example shows how the `Clear-Content` cmdlet clears the content from an alternate data stream while leaving the stream intact.</span></span>

<span data-ttu-id="57dae-124">De eerste opdracht gebruikt de `Get-Content` cmdlet om de inhoud van de zone. id-stroom op te halen in het Copy-Script.ps1 bestand, dat is gedownload van het internet.</span><span class="sxs-lookup"><span data-stu-id="57dae-124">The first command uses the `Get-Content` cmdlet to get the content of the Zone.Identifier stream in the Copy-Script.ps1 file, which was downloaded from the Internet.</span></span>

<span data-ttu-id="57dae-125">Met de tweede opdracht wordt de- `Clear-Content` cmdlet gebruikt om de inhoud te wissen.</span><span class="sxs-lookup"><span data-stu-id="57dae-125">The second command uses the `Clear-Content` cmdlet to clear the content.</span></span>

<span data-ttu-id="57dae-126">Met de derde opdracht wordt de eerste opdracht herhaald.</span><span class="sxs-lookup"><span data-stu-id="57dae-126">The third command repeats the first command.</span></span> <span data-ttu-id="57dae-127">Er wordt gecontroleerd of de inhoud is gewist, maar de stroom blijft.</span><span class="sxs-lookup"><span data-stu-id="57dae-127">It verifies that the content is cleared, but the stream remains.</span></span> <span data-ttu-id="57dae-128">Als de stroom is verwijderd, wordt door de opdracht een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="57dae-128">If the stream were deleted, the command would generate an error.</span></span>

<span data-ttu-id="57dae-129">U kunt een methode als deze gebruiken om de inhoud van een alternatieve gegevens stroom te wissen.</span><span class="sxs-lookup"><span data-stu-id="57dae-129">You can use a method like this one to clear the content of an alternate data stream.</span></span> <span data-ttu-id="57dae-130">Het is echter niet de aanbevolen manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="57dae-130">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="57dae-131">Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57dae-131">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

```
PS C:\> Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

[ZoneTransfer]
ZoneId=3

PS C:\>Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

PS C:\>Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
PS C:\>
```

## <span data-ttu-id="57dae-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="57dae-132">PARAMETERS</span></span>

### <span data-ttu-id="57dae-133">-Stream</span><span class="sxs-lookup"><span data-stu-id="57dae-133">-Stream</span></span>

<span data-ttu-id="57dae-134">Hiermee geeft u een alternatieve gegevens stroom voor inhoud.</span><span class="sxs-lookup"><span data-stu-id="57dae-134">Specifies an alternative data stream for content.</span></span>
<span data-ttu-id="57dae-135">Als de stroom niet bestaat, wordt deze gemaakt met deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57dae-135">If the stream does not exist, this cmdlet creates it.</span></span>
<span data-ttu-id="57dae-136">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="57dae-136">Wildcard characters are not supported.</span></span>

<span data-ttu-id="57dae-137">Stream is een dynamische para meter waaraan de File System Provider toevoegt `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="57dae-137">Stream is a dynamic parameter that the FileSystem provider adds to `Clear-Content`.</span></span>
<span data-ttu-id="57dae-138">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="57dae-138">This parameter works only in file system drives.</span></span>

<span data-ttu-id="57dae-139">U kunt de- `Clear-Content` cmdlet gebruiken om de inhoud van de zone te wijzigen. id alternatieve gegevens stroom.</span><span class="sxs-lookup"><span data-stu-id="57dae-139">You can use the `Clear-Content` cmdlet to change the content of the Zone.Identifier alternate data stream.</span></span>
<span data-ttu-id="57dae-140">Dit wordt echter niet aangeraden als een manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="57dae-140">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span>
<span data-ttu-id="57dae-141">Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57dae-141">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

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

### <span data-ttu-id="57dae-142">-Credential</span><span class="sxs-lookup"><span data-stu-id="57dae-142">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="57dae-143">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="57dae-143">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="57dae-144">Gebruik invoke-Command om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="57dae-144">To impersonate another user, or elevate your credentials when running this cmdlet, use Invoke-Command.</span></span>

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

### <span data-ttu-id="57dae-145">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="57dae-145">-Exclude</span></span>

<span data-ttu-id="57dae-146">Hiermee geeft u als teken reeks matrix teken reeksen op die met deze cmdlet worden wegge laten van het pad naar de inhoud.</span><span class="sxs-lookup"><span data-stu-id="57dae-146">Specifies, as a string array, strings that this cmdlet omits from the path to the content.</span></span>
<span data-ttu-id="57dae-147">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="57dae-147">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="57dae-148">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="57dae-148">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="57dae-149">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="57dae-149">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="57dae-150">-Filter</span><span class="sxs-lookup"><span data-stu-id="57dae-150">-Filter</span></span>

<span data-ttu-id="57dae-151">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="57dae-151">Specifies a filter in the provider's format or language.</span></span>
<span data-ttu-id="57dae-152">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="57dae-152">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="57dae-153">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="57dae-153">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span>
<span data-ttu-id="57dae-154">Filters zijn efficiënter dan andere para meters, omdat de provider deze toepast tijdens het ophalen van de objecten, in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="57dae-154">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="57dae-155">-Force</span><span class="sxs-lookup"><span data-stu-id="57dae-155">-Force</span></span>

<span data-ttu-id="57dae-156">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="57dae-156">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="57dae-157">-Include</span><span class="sxs-lookup"><span data-stu-id="57dae-157">-Include</span></span>

<span data-ttu-id="57dae-158">Hiermee geeft u als een teken reeks matrix inhoud op die door deze cmdlet wordt gewist.</span><span class="sxs-lookup"><span data-stu-id="57dae-158">Specifies, as a string array, content that this cmdlet clears.</span></span>
<span data-ttu-id="57dae-159">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="57dae-159">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="57dae-160">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="57dae-160">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="57dae-161">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="57dae-161">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="57dae-162">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="57dae-162">-LiteralPath</span></span>

<span data-ttu-id="57dae-163">Hiermee geeft u de paden op naar de items waarvan de inhoud wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="57dae-163">Specifies the paths to the items from which content is deleted.</span></span>
<span data-ttu-id="57dae-164">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="57dae-164">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="57dae-165">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="57dae-165">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="57dae-166">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="57dae-166">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="57dae-167">Enkele aanhalings tekens geven aan dat Power shell geen karakters kan interpreteren als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="57dae-167">Single quotation marks tell having PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="57dae-168">-Path</span><span class="sxs-lookup"><span data-stu-id="57dae-168">-Path</span></span>

<span data-ttu-id="57dae-169">Hiermee geeft u de paden op naar de items waarvan de inhoud wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="57dae-169">Specifies the paths to the items from which content is deleted.</span></span>
<span data-ttu-id="57dae-170">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="57dae-170">Wildcards are permitted.</span></span>
<span data-ttu-id="57dae-171">De paden moeten paden naar items zijn en niet naar containers.</span><span class="sxs-lookup"><span data-stu-id="57dae-171">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="57dae-172">U moet bijvoorbeeld een pad naar een of meer bestanden opgeven, niet een pad naar een map.</span><span class="sxs-lookup"><span data-stu-id="57dae-172">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="57dae-173">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="57dae-173">Wildcards are permitted.</span></span>
<span data-ttu-id="57dae-174">Deze para meter is vereist, maar de parameter naam ("pad") is optioneel.</span><span class="sxs-lookup"><span data-stu-id="57dae-174">This parameter is required, but the parameter name ("Path") is optional.</span></span>

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

### <span data-ttu-id="57dae-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="57dae-175">-Confirm</span></span>

<span data-ttu-id="57dae-176">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="57dae-176">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="57dae-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="57dae-177">-WhatIf</span></span>

<span data-ttu-id="57dae-178">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="57dae-178">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="57dae-179">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="57dae-179">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="57dae-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="57dae-180">CommonParameters</span></span>

<span data-ttu-id="57dae-181">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="57dae-181">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="57dae-182">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="57dae-182">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="57dae-183">INVOER</span><span class="sxs-lookup"><span data-stu-id="57dae-183">INPUTS</span></span>

### <span data-ttu-id="57dae-184">Geen</span><span class="sxs-lookup"><span data-stu-id="57dae-184">None</span></span>

<span data-ttu-id="57dae-185">U kunt geen objecten pipeen naar `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="57dae-185">You cannot pipe objects to `Clear-Content`.</span></span>

## <span data-ttu-id="57dae-186">UITVOER</span><span class="sxs-lookup"><span data-stu-id="57dae-186">OUTPUTS</span></span>

### <span data-ttu-id="57dae-187">Geen</span><span class="sxs-lookup"><span data-stu-id="57dae-187">None</span></span>

<span data-ttu-id="57dae-188">Met deze cmdlet worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="57dae-188">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="57dae-189">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="57dae-189">NOTES</span></span>

<span data-ttu-id="57dae-190">U kunt gebruiken `Clear-Content` met de Power shell-bestandssysteem provider en met andere providers die inhoud bewerken.</span><span class="sxs-lookup"><span data-stu-id="57dae-190">You can use `Clear-Content` with the PowerShell FileSystem provider and with other providers that manipulate content.</span></span>
<span data-ttu-id="57dae-191">Als u items wilt wissen die niet worden beschouwd als inhoud, zoals items die worden beheerd door het Power shell-certificaat of register providers, gebruikt u `Clear-Item` .</span><span class="sxs-lookup"><span data-stu-id="57dae-191">To clear items that are not considered to be content, such as items managed by the PowerShell Certificate or Registry providers, use `Clear-Item`.</span></span>

<span data-ttu-id="57dae-192">De `Clear-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="57dae-192">The `Clear-Content` cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="57dae-193">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="57dae-193">To list the providers available in your session, type `Get-PsProvider`.</span></span>
<span data-ttu-id="57dae-194">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="57dae-194">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="57dae-195">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="57dae-195">RELATED LINKS</span></span>

[<span data-ttu-id="57dae-196">Add-content</span><span class="sxs-lookup"><span data-stu-id="57dae-196">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="57dae-197">Get-Content</span><span class="sxs-lookup"><span data-stu-id="57dae-197">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="57dae-198">Get-item</span><span class="sxs-lookup"><span data-stu-id="57dae-198">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="57dae-199">Set-Content</span><span class="sxs-lookup"><span data-stu-id="57dae-199">Set-Content</span></span>](Set-Content.md)

[<span data-ttu-id="57dae-200">about_Providers</span><span class="sxs-lookup"><span data-stu-id="57dae-200">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)