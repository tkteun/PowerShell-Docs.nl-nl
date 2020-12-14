---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: ebb79f16447aef2dd194505d805a34353f710e69
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705726"
---
# <span data-ttu-id="e99fd-102">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="e99fd-102">Invoke-Item</span></span>

## <span data-ttu-id="e99fd-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e99fd-103">SYNOPSIS</span></span>
<span data-ttu-id="e99fd-104">Voert de standaard actie uit op het opgegeven item.</span><span class="sxs-lookup"><span data-stu-id="e99fd-104">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="e99fd-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e99fd-105">SYNTAX</span></span>

### <span data-ttu-id="e99fd-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="e99fd-106">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e99fd-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e99fd-107">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e99fd-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e99fd-108">DESCRIPTION</span></span>

<span data-ttu-id="e99fd-109">De `Invoke-Item` cmdlet voert de standaard actie uit op het opgegeven item.</span><span class="sxs-lookup"><span data-stu-id="e99fd-109">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="e99fd-110">Er wordt bijvoorbeeld een uitvoerbaar bestand uitgevoerd of een document bestand geopend in de toepassing die is gekoppeld aan het document bestands type.</span><span class="sxs-lookup"><span data-stu-id="e99fd-110">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="e99fd-111">De standaard actie is afhankelijk van het type item en wordt bepaald door de Power shell-provider die toegang biedt tot de gegevens.</span><span class="sxs-lookup"><span data-stu-id="e99fd-111">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="e99fd-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e99fd-112">EXAMPLES</span></span>

### <span data-ttu-id="e99fd-113">Voor beeld 1: een bestand openen</span><span class="sxs-lookup"><span data-stu-id="e99fd-113">Example 1: Open a file</span></span>

<span data-ttu-id="e99fd-114">Met deze opdracht wordt het bestand ' aliasApr04.doc ' geopend in Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="e99fd-114">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="e99fd-115">In dit geval is het openen in Word de standaard actie voor '. doc ' bestanden.</span><span class="sxs-lookup"><span data-stu-id="e99fd-115">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="e99fd-116">Voor beeld 2: alle bestanden van een specifiek type openen</span><span class="sxs-lookup"><span data-stu-id="e99fd-116">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="e99fd-117">Met deze opdracht worden alle Microsoft Office Excel-spread sheets in de `C:\Documents and
Settings\Lister\My Documents` map geopend.</span><span class="sxs-lookup"><span data-stu-id="e99fd-117">This command opens all of the Microsoft Office Excel spreadsheets in the `C:\Documents and
Settings\Lister\My Documents` folder.</span></span> <span data-ttu-id="e99fd-118">Elk werk blad wordt geopend in een nieuw exemplaar van Excel.</span><span class="sxs-lookup"><span data-stu-id="e99fd-118">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="e99fd-119">In dit geval is het openen in Excel de standaard actie voor `.xls` bestanden.</span><span class="sxs-lookup"><span data-stu-id="e99fd-119">In this case, opening in Excel is the default action for `.xls` files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="e99fd-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e99fd-120">PARAMETERS</span></span>

### <span data-ttu-id="e99fd-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="e99fd-121">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="e99fd-122">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="e99fd-122">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="e99fd-123">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e99fd-123">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="e99fd-124">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="e99fd-124">-Exclude</span></span>

<span data-ttu-id="e99fd-125">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="e99fd-125">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="e99fd-126">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="e99fd-126">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e99fd-127">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="e99fd-127">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="e99fd-128">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e99fd-128">Wildcard characters are permitted.</span></span> <span data-ttu-id="e99fd-129">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="e99fd-129">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="e99fd-130">-Filter</span><span class="sxs-lookup"><span data-stu-id="e99fd-130">-Filter</span></span>

<span data-ttu-id="e99fd-131">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="e99fd-131">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="e99fd-132">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="e99fd-132">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="e99fd-133">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="e99fd-133">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="e99fd-134">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e99fd-134">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="e99fd-135">-Include</span><span class="sxs-lookup"><span data-stu-id="e99fd-135">-Include</span></span>

<span data-ttu-id="e99fd-136">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="e99fd-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="e99fd-137">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="e99fd-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e99fd-138">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="e99fd-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="e99fd-139">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e99fd-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="e99fd-140">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="e99fd-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="e99fd-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e99fd-141">-LiteralPath</span></span>

<span data-ttu-id="e99fd-142">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="e99fd-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="e99fd-143">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="e99fd-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="e99fd-144">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="e99fd-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e99fd-145">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="e99fd-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e99fd-146">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="e99fd-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="e99fd-147">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e99fd-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="e99fd-148">-Path</span><span class="sxs-lookup"><span data-stu-id="e99fd-148">-Path</span></span>

<span data-ttu-id="e99fd-149">Hiermee geeft u het pad op naar het geselecteerde item.</span><span class="sxs-lookup"><span data-stu-id="e99fd-149">Specifies the path to the selected item.</span></span>
<span data-ttu-id="e99fd-150">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e99fd-150">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e99fd-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e99fd-151">-Confirm</span></span>

<span data-ttu-id="e99fd-152">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e99fd-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e99fd-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e99fd-153">-WhatIf</span></span>

<span data-ttu-id="e99fd-154">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e99fd-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e99fd-155">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e99fd-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e99fd-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e99fd-156">CommonParameters</span></span>

<span data-ttu-id="e99fd-157">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="e99fd-157">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="e99fd-158">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e99fd-158">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e99fd-159">INVOER</span><span class="sxs-lookup"><span data-stu-id="e99fd-159">INPUTS</span></span>

### <span data-ttu-id="e99fd-160">System. String</span><span class="sxs-lookup"><span data-stu-id="e99fd-160">System.String</span></span>

<span data-ttu-id="e99fd-161">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="e99fd-161">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="e99fd-162">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e99fd-162">OUTPUTS</span></span>

### <span data-ttu-id="e99fd-163">Geen</span><span class="sxs-lookup"><span data-stu-id="e99fd-163">None</span></span>

<span data-ttu-id="e99fd-164">Met de opdracht wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="e99fd-164">The command does not generate any output.</span></span>
<span data-ttu-id="e99fd-165">Uitvoer kan echter worden gegenereerd door het item dat wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="e99fd-165">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="e99fd-166">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e99fd-166">NOTES</span></span>

<span data-ttu-id="e99fd-167">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e99fd-167">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="e99fd-168">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="e99fd-168">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="e99fd-169">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e99fd-169">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="e99fd-170">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e99fd-170">RELATED LINKS</span></span>

[<span data-ttu-id="e99fd-171">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="e99fd-171">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="e99fd-172">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="e99fd-172">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="e99fd-173">Get-item</span><span class="sxs-lookup"><span data-stu-id="e99fd-173">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="e99fd-174">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="e99fd-174">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="e99fd-175">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="e99fd-175">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="e99fd-176">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="e99fd-176">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="e99fd-177">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="e99fd-177">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="e99fd-178">Set-item</span><span class="sxs-lookup"><span data-stu-id="e99fd-178">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="e99fd-179">about_Providers</span><span class="sxs-lookup"><span data-stu-id="e99fd-179">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

