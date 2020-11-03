---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Item
ms.openlocfilehash: b03e6a68da933dc0da6bfce92201825f70b77b19
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251335"
---
# <span data-ttu-id="fccd0-103">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="fccd0-103">Clear-Item</span></span>

## <span data-ttu-id="fccd0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fccd0-104">SYNOPSIS</span></span>
<span data-ttu-id="fccd0-105">Hiermee wist u de inhoud van een item, maar verwijdert u het item niet.</span><span class="sxs-lookup"><span data-stu-id="fccd0-105">Clears the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="fccd0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fccd0-106">SYNTAX</span></span>

### <span data-ttu-id="fccd0-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="fccd0-107">Path (Default)</span></span>

```
Clear-Item [-Path] <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fccd0-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fccd0-108">LiteralPath</span></span>

```
Clear-Item -LiteralPath <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fccd0-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fccd0-109">DESCRIPTION</span></span>

<span data-ttu-id="fccd0-110">Met de cmdlet wordt de `Clear-Item` inhoud van een item gewist, maar wordt het item niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="fccd0-110">The `Clear-Item` cmdlet clears the content of an item, but it does not delete the item.</span></span>
<span data-ttu-id="fccd0-111">`Clear-Item`Met de cmdlet kan bijvoorbeeld de waarde van een variabele worden verwijderd, maar wordt de variabele niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="fccd0-111">For example, the `Clear-Item` cmdlet can delete the value of a variable, but it does not delete the variable.</span></span> <span data-ttu-id="fccd0-112">De waarde die wordt gebruikt om een verrekend item weer te geven, wordt gedefinieerd door elke Power shell-provider.</span><span class="sxs-lookup"><span data-stu-id="fccd0-112">The value that used to represent a cleared item is defined by each PowerShell provider.</span></span>
<span data-ttu-id="fccd0-113">Deze cmdlet is vergelijkbaar met `Clear-Content` , maar werkt op aliassen en variabelen, in plaats van bestanden.</span><span class="sxs-lookup"><span data-stu-id="fccd0-113">This cmdlet is similar to `Clear-Content`, but it works on aliases and variables, instead of files.</span></span>

## <span data-ttu-id="fccd0-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fccd0-114">EXAMPLES</span></span>

### <span data-ttu-id="fccd0-115">Voor beeld 1: de waarde van een variabele wissen</span><span class="sxs-lookup"><span data-stu-id="fccd0-115">Example 1: Clear the value of a variable</span></span>

<span data-ttu-id="fccd0-116">Met deze opdracht wordt de waarde van de variabele met de naam gewist `TestVar1` .</span><span class="sxs-lookup"><span data-stu-id="fccd0-116">This command clears the value of the variable named `TestVar1`.</span></span>
<span data-ttu-id="fccd0-117">De variabele blijft en is geldig, maar de waarde is ingesteld op `$null` .</span><span class="sxs-lookup"><span data-stu-id="fccd0-117">The variable remains and is valid, but its value is set to `$null`.</span></span>
<span data-ttu-id="fccd0-118">De naam van de variabele wordt voorafgegaan door `Variable:` om de Power shell-variabele provider aan te geven.</span><span class="sxs-lookup"><span data-stu-id="fccd0-118">The variable name is prefixed with `Variable:` to indicate the PowerShell Variable provider.</span></span>

<span data-ttu-id="fccd0-119">De alternatieve opdrachten laten zien dat, om hetzelfde resultaat te krijgen, u kunt overschakelen naar het Power shell- `Variable:` station en vervolgens de `Clear-Item` opdracht uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="fccd0-119">The alternate commands show that, to get the same result, you can switch to the PowerShell `Variable:` drive and then run the `Clear-Item` command.</span></span>

```powershell
Clear-Item Variable:TestVar1
```

```
Set-Location Variable:
PS Variable:\> Clear-Item TestVar1
```

### <span data-ttu-id="fccd0-120">Voor beeld 2: alle Register vermeldingen wissen</span><span class="sxs-lookup"><span data-stu-id="fccd0-120">Example 2: Clear all registry entries</span></span>

<span data-ttu-id="fccd0-121">Met deze opdracht worden alle Register vermeldingen in de subsleutel "MyKey" gewist, maar pas u gevraagd om uw intentie te bevestigen.</span><span class="sxs-lookup"><span data-stu-id="fccd0-121">This command clears all registry entries in the "MyKey" subkey, but only after prompting you to confirm your intent.</span></span>
<span data-ttu-id="fccd0-122">De subsleutel "MyKey" wordt niet verwijderd of heeft geen invloed op andere register sleutels of-vermeldingen.</span><span class="sxs-lookup"><span data-stu-id="fccd0-122">It does not delete the "MyKey" subkey or affect any other registry keys or entries.</span></span>
<span data-ttu-id="fccd0-123">U kunt de para meters **include** en **exclude** gebruiken om bepaalde register sleutels te identificeren, maar u kunt ze niet gebruiken om Register vermeldingen te identificeren.</span><span class="sxs-lookup"><span data-stu-id="fccd0-123">You can use the **Include** and **Exclude** parameters to identify particular registry keys, but you cannot use them to identify registry entries.</span></span>

- <span data-ttu-id="fccd0-124">Als u bepaalde register vermeldingen wilt verwijderen, gebruikt u de `Remove-ItemProperty` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fccd0-124">To delete particular registry entries, use the `Remove-ItemProperty` cmdlet.</span></span>
- <span data-ttu-id="fccd0-125">Als u de waarde van een register vermelding wilt verwijderen, gebruikt u de `Clear-ItemProperty cmdlet` .</span><span class="sxs-lookup"><span data-stu-id="fccd0-125">To delete the value of a registry entry, use the `Clear-ItemProperty cmdlet`.</span></span>

```powershell
Clear-Item HKLM:\Software\MyCompany\MyKey -Confirm
```

## <span data-ttu-id="fccd0-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fccd0-126">PARAMETERS</span></span>

### <span data-ttu-id="fccd0-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="fccd0-127">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="fccd0-128">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="fccd0-128">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="fccd0-129">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fccd0-129">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="fccd0-130">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="fccd0-130">-Exclude</span></span>

<span data-ttu-id="fccd0-131">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="fccd0-131">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="fccd0-132">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="fccd0-132">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fccd0-133">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="fccd0-133">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="fccd0-134">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="fccd0-134">Wildcard characters are permitted.</span></span> <span data-ttu-id="fccd0-135">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="fccd0-135">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="fccd0-136">-Filter</span><span class="sxs-lookup"><span data-stu-id="fccd0-136">-Filter</span></span>

<span data-ttu-id="fccd0-137">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="fccd0-137">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="fccd0-138">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="fccd0-138">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="fccd0-139">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="fccd0-139">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="fccd0-140">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fccd0-140">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="fccd0-141">-Force</span><span class="sxs-lookup"><span data-stu-id="fccd0-141">-Force</span></span>

<span data-ttu-id="fccd0-142">Geeft aan dat de cmdlet items wist die anders niet kunnen worden gewijzigd, zoals alleen-lezen aliassen.</span><span class="sxs-lookup"><span data-stu-id="fccd0-142">Indicates that the cmdlet clears items that cannot otherwise be changed, such as read- only aliases.</span></span>
<span data-ttu-id="fccd0-143">De cmdlet kan constanten niet wissen.</span><span class="sxs-lookup"><span data-stu-id="fccd0-143">The cmdlet cannot clear constants.</span></span>
<span data-ttu-id="fccd0-144">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="fccd0-144">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="fccd0-145">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fccd0-145">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="fccd0-146">De cmdlet kan geen beveiligings beperkingen overschrijven, zelfs niet wanneer de para meter **Forces** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fccd0-146">The cmdlet cannot override security restrictions, even when the **Force** parameter is used.</span></span>

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

### <span data-ttu-id="fccd0-147">-Include</span><span class="sxs-lookup"><span data-stu-id="fccd0-147">-Include</span></span>

<span data-ttu-id="fccd0-148">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="fccd0-148">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="fccd0-149">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="fccd0-149">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fccd0-150">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="fccd0-150">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="fccd0-151">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="fccd0-151">Wildcard characters are permitted.</span></span> <span data-ttu-id="fccd0-152">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="fccd0-152">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="fccd0-153">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fccd0-153">-LiteralPath</span></span>

<span data-ttu-id="fccd0-154">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="fccd0-154">Specifies a path to one or more locations.</span></span> <span data-ttu-id="fccd0-155">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="fccd0-155">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="fccd0-156">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="fccd0-156">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="fccd0-157">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="fccd0-157">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="fccd0-158">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="fccd0-158">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="fccd0-159">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fccd0-159">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="fccd0-160">-Path</span><span class="sxs-lookup"><span data-stu-id="fccd0-160">-Path</span></span>

<span data-ttu-id="fccd0-161">Hiermee geeft u het pad op naar de items die worden gewist.</span><span class="sxs-lookup"><span data-stu-id="fccd0-161">Specifies the path to the items being cleared.</span></span>
<span data-ttu-id="fccd0-162">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="fccd0-162">Wildcard characters are permitted.</span></span>
<span data-ttu-id="fccd0-163">Deze para meter is vereist, maar het **pad naar** de parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fccd0-163">This parameter is required, but the parameter name **Path** is optional.</span></span>

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

### <span data-ttu-id="fccd0-164">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fccd0-164">-Confirm</span></span>

<span data-ttu-id="fccd0-165">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fccd0-165">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fccd0-166">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fccd0-166">-WhatIf</span></span>

<span data-ttu-id="fccd0-167">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fccd0-167">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="fccd0-168">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fccd0-168">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fccd0-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fccd0-169">CommonParameters</span></span>

<span data-ttu-id="fccd0-170">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="fccd0-170">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="fccd0-171">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fccd0-171">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="fccd0-172">INVOER</span><span class="sxs-lookup"><span data-stu-id="fccd0-172">INPUTS</span></span>

### <span data-ttu-id="fccd0-173">System. String</span><span class="sxs-lookup"><span data-stu-id="fccd0-173">System.String</span></span>

<span data-ttu-id="fccd0-174">U kunt een padtekenreeks door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fccd0-174">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="fccd0-175">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fccd0-175">OUTPUTS</span></span>

### <span data-ttu-id="fccd0-176">Geen</span><span class="sxs-lookup"><span data-stu-id="fccd0-176">None</span></span>

<span data-ttu-id="fccd0-177">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="fccd0-177">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fccd0-178">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fccd0-178">NOTES</span></span>

- <span data-ttu-id="fccd0-179">De `Clear-Item` cmdlet wordt alleen ondersteund door verschillende Power shell-providers, met inbegrip van de **alias** -, **omgevings** -, **functie** -, **register** -en **variabelen** providers.</span><span class="sxs-lookup"><span data-stu-id="fccd0-179">The `Clear-Item` cmdlet is supported only by several PowerShell providers, including the **Alias** , **Environment** , **Function** , **Registry** , and **Variable** providers.</span></span> <span data-ttu-id="fccd0-180">Zo kunt u gebruiken `Clear-Item` om de inhoud van items in de naam ruimten van de provider te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="fccd0-180">As such, you can use `Clear-Item` to delete the content of items in the provider namespaces.</span></span> <span data-ttu-id="fccd0-181">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="fccd0-181">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="fccd0-182">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fccd0-182">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
- <span data-ttu-id="fccd0-183">U kunt niet gebruiken `Clear-Item` om de inhoud van een bestand te verwijderen, omdat de Power shell-bestands provider deze cmdlet niet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="fccd0-183">You cannot use `Clear-Item` to delete the contents of a file, because the PowerShell FileSystem provider does not support this cmdlet.</span></span> <span data-ttu-id="fccd0-184">Gebruik de om bestanden te wissen `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="fccd0-184">To clear files, use the `Clear-Content`.</span></span>

## <span data-ttu-id="fccd0-185">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fccd0-185">RELATED LINKS</span></span>

[<span data-ttu-id="fccd0-186">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="fccd0-186">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="fccd0-187">Get-item</span><span class="sxs-lookup"><span data-stu-id="fccd0-187">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="fccd0-188">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="fccd0-188">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="fccd0-189">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="fccd0-189">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="fccd0-190">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="fccd0-190">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="fccd0-191">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="fccd0-191">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="fccd0-192">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="fccd0-192">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="fccd0-193">Set-item</span><span class="sxs-lookup"><span data-stu-id="fccd0-193">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="fccd0-194">about_Providers</span><span class="sxs-lookup"><span data-stu-id="fccd0-194">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

