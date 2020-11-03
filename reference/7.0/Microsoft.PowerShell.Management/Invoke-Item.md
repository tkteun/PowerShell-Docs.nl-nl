---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: bbd3ca9a3a4df8930a75ecc395765e70fc7ccf7b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249462"
---
# <span data-ttu-id="b06e2-103">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="b06e2-103">Invoke-Item</span></span>

## <span data-ttu-id="b06e2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b06e2-104">SYNOPSIS</span></span>
<span data-ttu-id="b06e2-105">Voert de standaard actie uit op het opgegeven item.</span><span class="sxs-lookup"><span data-stu-id="b06e2-105">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="b06e2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b06e2-106">SYNTAX</span></span>

### <span data-ttu-id="b06e2-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="b06e2-107">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b06e2-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b06e2-108">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b06e2-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b06e2-109">DESCRIPTION</span></span>

<span data-ttu-id="b06e2-110">De `Invoke-Item` cmdlet voert de standaard actie uit op het opgegeven item.</span><span class="sxs-lookup"><span data-stu-id="b06e2-110">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="b06e2-111">Er wordt bijvoorbeeld een uitvoerbaar bestand uitgevoerd of een document bestand geopend in de toepassing die is gekoppeld aan het document bestands type.</span><span class="sxs-lookup"><span data-stu-id="b06e2-111">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="b06e2-112">De standaard actie is afhankelijk van het type item en wordt bepaald door de Power shell-provider die toegang biedt tot de gegevens.</span><span class="sxs-lookup"><span data-stu-id="b06e2-112">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="b06e2-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b06e2-113">EXAMPLES</span></span>

### <span data-ttu-id="b06e2-114">Voor beeld 1: een bestand openen</span><span class="sxs-lookup"><span data-stu-id="b06e2-114">Example 1: Open a file</span></span>

<span data-ttu-id="b06e2-115">Met deze opdracht wordt het bestand ' aliasApr04.doc ' geopend in Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="b06e2-115">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="b06e2-116">In dit geval is het openen in Word de standaard actie voor '. doc ' bestanden.</span><span class="sxs-lookup"><span data-stu-id="b06e2-116">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="b06e2-117">Voor beeld 2: alle bestanden van een specifiek type openen</span><span class="sxs-lookup"><span data-stu-id="b06e2-117">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="b06e2-118">Met deze opdracht worden alle Microsoft Office Excel-spread sheets in de `C:\Documents and
Settings\Lister\My Documents` map geopend.</span><span class="sxs-lookup"><span data-stu-id="b06e2-118">This command opens all of the Microsoft Office Excel spreadsheets in the `C:\Documents and
Settings\Lister\My Documents` folder.</span></span> <span data-ttu-id="b06e2-119">Elk werk blad wordt geopend in een nieuw exemplaar van Excel.</span><span class="sxs-lookup"><span data-stu-id="b06e2-119">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="b06e2-120">In dit geval is het openen in Excel de standaard actie voor `.xls` bestanden.</span><span class="sxs-lookup"><span data-stu-id="b06e2-120">In this case, opening in Excel is the default action for `.xls` files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="b06e2-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b06e2-121">PARAMETERS</span></span>

### <span data-ttu-id="b06e2-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="b06e2-122">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="b06e2-123">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="b06e2-123">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="b06e2-124">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b06e2-124">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="b06e2-125">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="b06e2-125">-Exclude</span></span>

<span data-ttu-id="b06e2-126">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="b06e2-126">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="b06e2-127">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="b06e2-127">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b06e2-128">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="b06e2-128">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="b06e2-129">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b06e2-129">Wildcard characters are permitted.</span></span> <span data-ttu-id="b06e2-130">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="b06e2-130">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b06e2-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="b06e2-131">-Filter</span></span>

<span data-ttu-id="b06e2-132">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="b06e2-132">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="b06e2-133">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="b06e2-133">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="b06e2-134">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="b06e2-134">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="b06e2-135">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b06e2-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="b06e2-136">-Include</span><span class="sxs-lookup"><span data-stu-id="b06e2-136">-Include</span></span>

<span data-ttu-id="b06e2-137">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="b06e2-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="b06e2-138">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="b06e2-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b06e2-139">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="b06e2-139">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="b06e2-140">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b06e2-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="b06e2-141">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="b06e2-141">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b06e2-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b06e2-142">-LiteralPath</span></span>

<span data-ttu-id="b06e2-143">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="b06e2-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="b06e2-144">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="b06e2-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="b06e2-145">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="b06e2-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b06e2-146">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="b06e2-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b06e2-147">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="b06e2-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="b06e2-148">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b06e2-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="b06e2-149">-Path</span><span class="sxs-lookup"><span data-stu-id="b06e2-149">-Path</span></span>

<span data-ttu-id="b06e2-150">Hiermee geeft u het pad op naar het geselecteerde item.</span><span class="sxs-lookup"><span data-stu-id="b06e2-150">Specifies the path to the selected item.</span></span>
<span data-ttu-id="b06e2-151">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b06e2-151">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="b06e2-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b06e2-152">-Confirm</span></span>

<span data-ttu-id="b06e2-153">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b06e2-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b06e2-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b06e2-154">-WhatIf</span></span>

<span data-ttu-id="b06e2-155">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b06e2-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b06e2-156">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b06e2-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b06e2-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b06e2-157">CommonParameters</span></span>

<span data-ttu-id="b06e2-158">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="b06e2-158">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b06e2-159">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b06e2-159">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b06e2-160">INVOER</span><span class="sxs-lookup"><span data-stu-id="b06e2-160">INPUTS</span></span>

### <span data-ttu-id="b06e2-161">System. String</span><span class="sxs-lookup"><span data-stu-id="b06e2-161">System.String</span></span>

<span data-ttu-id="b06e2-162">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="b06e2-162">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="b06e2-163">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b06e2-163">OUTPUTS</span></span>

### <span data-ttu-id="b06e2-164">Geen</span><span class="sxs-lookup"><span data-stu-id="b06e2-164">None</span></span>

<span data-ttu-id="b06e2-165">Met de opdracht wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b06e2-165">The command does not generate any output.</span></span>
<span data-ttu-id="b06e2-166">Uitvoer kan echter worden gegenereerd door het item dat wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b06e2-166">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="b06e2-167">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b06e2-167">NOTES</span></span>

<span data-ttu-id="b06e2-168">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b06e2-168">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="b06e2-169">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="b06e2-169">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="b06e2-170">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b06e2-170">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="b06e2-171">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b06e2-171">RELATED LINKS</span></span>

[<span data-ttu-id="b06e2-172">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="b06e2-172">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="b06e2-173">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="b06e2-173">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="b06e2-174">Get-item</span><span class="sxs-lookup"><span data-stu-id="b06e2-174">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="b06e2-175">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="b06e2-175">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="b06e2-176">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="b06e2-176">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="b06e2-177">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="b06e2-177">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="b06e2-178">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="b06e2-178">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="b06e2-179">Set-item</span><span class="sxs-lookup"><span data-stu-id="b06e2-179">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="b06e2-180">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b06e2-180">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
