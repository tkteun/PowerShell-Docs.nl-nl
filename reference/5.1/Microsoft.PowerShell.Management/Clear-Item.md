---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Item
ms.openlocfilehash: a0854fbff06ea51c322bdaf46c81f47f76af978b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250828"
---
# <span data-ttu-id="b2f21-103">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="b2f21-103">Clear-Item</span></span>

## <span data-ttu-id="b2f21-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b2f21-104">SYNOPSIS</span></span>
<span data-ttu-id="b2f21-105">Hiermee wist u de inhoud van een item, maar verwijdert u het item niet.</span><span class="sxs-lookup"><span data-stu-id="b2f21-105">Clears the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="b2f21-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b2f21-106">SYNTAX</span></span>

### <span data-ttu-id="b2f21-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="b2f21-107">Path (Default)</span></span>

```
Clear-Item [-Path] <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="b2f21-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b2f21-108">LiteralPath</span></span>

```
Clear-Item -LiteralPath <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="b2f21-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b2f21-109">DESCRIPTION</span></span>

<span data-ttu-id="b2f21-110">Met de cmdlet wordt de `Clear-Item` inhoud van een item gewist, maar wordt het item niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b2f21-110">The `Clear-Item` cmdlet clears the content of an item, but it does not delete the item.</span></span>
<span data-ttu-id="b2f21-111">`Clear-Item`Met de cmdlet kan bijvoorbeeld de waarde van een variabele worden verwijderd, maar wordt de variabele niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b2f21-111">For example, the `Clear-Item` cmdlet can delete the value of a variable, but it does not delete the variable.</span></span> <span data-ttu-id="b2f21-112">De waarde die wordt gebruikt om een verrekend item weer te geven, wordt gedefinieerd door elke Power shell-provider.</span><span class="sxs-lookup"><span data-stu-id="b2f21-112">The value that used to represent a cleared item is defined by each PowerShell provider.</span></span>
<span data-ttu-id="b2f21-113">Deze cmdlet is vergelijkbaar met `Clear-Content` , maar werkt op aliassen en variabelen, in plaats van bestanden.</span><span class="sxs-lookup"><span data-stu-id="b2f21-113">This cmdlet is similar to `Clear-Content`, but it works on aliases and variables, instead of files.</span></span>

## <span data-ttu-id="b2f21-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b2f21-114">EXAMPLES</span></span>

### <span data-ttu-id="b2f21-115">Voor beeld 1: de waarde van een variabele wissen</span><span class="sxs-lookup"><span data-stu-id="b2f21-115">Example 1: Clear the value of a variable</span></span>

<span data-ttu-id="b2f21-116">Met deze opdracht wordt de waarde van de variabele met de naam gewist `TestVar1` .</span><span class="sxs-lookup"><span data-stu-id="b2f21-116">This command clears the value of the variable named `TestVar1`.</span></span>
<span data-ttu-id="b2f21-117">De variabele blijft en is geldig, maar de waarde is ingesteld op `$null` .</span><span class="sxs-lookup"><span data-stu-id="b2f21-117">The variable remains and is valid, but its value is set to `$null`.</span></span>
<span data-ttu-id="b2f21-118">De naam van de variabele wordt voorafgegaan door `Variable:` om de Power shell-variabele provider aan te geven.</span><span class="sxs-lookup"><span data-stu-id="b2f21-118">The variable name is prefixed with `Variable:` to indicate the PowerShell Variable provider.</span></span>

<span data-ttu-id="b2f21-119">De alternatieve opdrachten laten zien dat, om hetzelfde resultaat te krijgen, u kunt overschakelen naar het Power shell- `Variable:` station en vervolgens de `Clear-Item` opdracht uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b2f21-119">The alternate commands show that, to get the same result, you can switch to the PowerShell `Variable:` drive and then run the `Clear-Item` command.</span></span>

```powershell
Clear-Item Variable:TestVar1
```

```
Set-Location Variable:
PS Variable:\> Clear-Item TestVar1
```

### <span data-ttu-id="b2f21-120">Voor beeld 2: alle Register vermeldingen wissen</span><span class="sxs-lookup"><span data-stu-id="b2f21-120">Example 2: Clear all registry entries</span></span>

<span data-ttu-id="b2f21-121">Met deze opdracht worden alle Register vermeldingen in de subsleutel "MyKey" gewist, maar pas u gevraagd om uw intentie te bevestigen.</span><span class="sxs-lookup"><span data-stu-id="b2f21-121">This command clears all registry entries in the "MyKey" subkey, but only after prompting you to confirm your intent.</span></span>
<span data-ttu-id="b2f21-122">De subsleutel "MyKey" wordt niet verwijderd of heeft geen invloed op andere register sleutels of-vermeldingen.</span><span class="sxs-lookup"><span data-stu-id="b2f21-122">It does not delete the "MyKey" subkey or affect any other registry keys or entries.</span></span>
<span data-ttu-id="b2f21-123">U kunt de para meters **include** en **exclude** gebruiken om bepaalde register sleutels te identificeren, maar u kunt ze niet gebruiken om Register vermeldingen te identificeren.</span><span class="sxs-lookup"><span data-stu-id="b2f21-123">You can use the **Include** and **Exclude** parameters to identify particular registry keys, but you cannot use them to identify registry entries.</span></span>

- <span data-ttu-id="b2f21-124">Als u bepaalde register vermeldingen wilt verwijderen, gebruikt u de `Remove-ItemProperty` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2f21-124">To delete particular registry entries, use the `Remove-ItemProperty` cmdlet.</span></span>
- <span data-ttu-id="b2f21-125">Als u de waarde van een register vermelding wilt verwijderen, gebruikt u de `Clear-ItemProperty` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2f21-125">To delete the value of a registry entry, use the `Clear-ItemProperty` cmdlet.</span></span>

```powershell
Clear-Item HKLM:\Software\MyCompany\MyKey -Confirm
```

## <span data-ttu-id="b2f21-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b2f21-126">PARAMETERS</span></span>

### <span data-ttu-id="b2f21-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="b2f21-127">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="b2f21-128">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="b2f21-128">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="b2f21-129">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b2f21-129">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="b2f21-130">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="b2f21-130">-Exclude</span></span>

<span data-ttu-id="b2f21-131">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="b2f21-131">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="b2f21-132">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="b2f21-132">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b2f21-133">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="b2f21-133">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="b2f21-134">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b2f21-134">Wildcard characters are permitted.</span></span> <span data-ttu-id="b2f21-135">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="b2f21-135">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b2f21-136">-Filter</span><span class="sxs-lookup"><span data-stu-id="b2f21-136">-Filter</span></span>

<span data-ttu-id="b2f21-137">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="b2f21-137">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="b2f21-138">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="b2f21-138">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="b2f21-139">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="b2f21-139">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="b2f21-140">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b2f21-140">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="b2f21-141">-Force</span><span class="sxs-lookup"><span data-stu-id="b2f21-141">-Force</span></span>

<span data-ttu-id="b2f21-142">Geeft aan dat de cmdlet items wist die anders niet kunnen worden gewijzigd, zoals alleen-lezen aliassen.</span><span class="sxs-lookup"><span data-stu-id="b2f21-142">Indicates that the cmdlet clears items that cannot otherwise be changed, such as read- only aliases.</span></span>
<span data-ttu-id="b2f21-143">De cmdlet kan constanten niet wissen.</span><span class="sxs-lookup"><span data-stu-id="b2f21-143">The cmdlet cannot clear constants.</span></span>
<span data-ttu-id="b2f21-144">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="b2f21-144">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="b2f21-145">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b2f21-145">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="b2f21-146">De cmdlet kan geen beveiligings beperkingen overschrijven, zelfs niet wanneer de para meter **Forces** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b2f21-146">The cmdlet cannot override security restrictions, even when the **Force** parameter is used.</span></span>

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

### <span data-ttu-id="b2f21-147">-Include</span><span class="sxs-lookup"><span data-stu-id="b2f21-147">-Include</span></span>

<span data-ttu-id="b2f21-148">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="b2f21-148">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="b2f21-149">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="b2f21-149">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b2f21-150">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="b2f21-150">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="b2f21-151">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b2f21-151">Wildcard characters are permitted.</span></span> <span data-ttu-id="b2f21-152">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="b2f21-152">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b2f21-153">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b2f21-153">-LiteralPath</span></span>

<span data-ttu-id="b2f21-154">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="b2f21-154">Specifies a path to one or more locations.</span></span> <span data-ttu-id="b2f21-155">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="b2f21-155">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="b2f21-156">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="b2f21-156">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b2f21-157">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="b2f21-157">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b2f21-158">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="b2f21-158">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="b2f21-159">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b2f21-159">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b2f21-160">-Path</span><span class="sxs-lookup"><span data-stu-id="b2f21-160">-Path</span></span>

<span data-ttu-id="b2f21-161">Hiermee geeft u het pad op naar de items die worden gewist.</span><span class="sxs-lookup"><span data-stu-id="b2f21-161">Specifies the path to the items being cleared.</span></span>
<span data-ttu-id="b2f21-162">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b2f21-162">Wildcard characters are permitted.</span></span>
<span data-ttu-id="b2f21-163">Deze para meter is vereist, maar het **pad naar** de parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="b2f21-163">This parameter is required, but the parameter name **Path** is optional.</span></span>

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

### <span data-ttu-id="b2f21-164">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="b2f21-164">-UseTransaction</span></span>

<span data-ttu-id="b2f21-165">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="b2f21-165">Includes the command in the active transaction.</span></span>
<span data-ttu-id="b2f21-166">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b2f21-166">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="b2f21-167">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b2f21-167">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2f21-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b2f21-168">-Confirm</span></span>

<span data-ttu-id="b2f21-169">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b2f21-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b2f21-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b2f21-170">-WhatIf</span></span>

<span data-ttu-id="b2f21-171">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b2f21-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b2f21-172">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b2f21-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b2f21-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2f21-173">CommonParameters</span></span>

<span data-ttu-id="b2f21-174">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="b2f21-174">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b2f21-175">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b2f21-175">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b2f21-176">INVOER</span><span class="sxs-lookup"><span data-stu-id="b2f21-176">INPUTS</span></span>

### <span data-ttu-id="b2f21-177">System. String</span><span class="sxs-lookup"><span data-stu-id="b2f21-177">System.String</span></span>

<span data-ttu-id="b2f21-178">U kunt een padtekenreeks door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2f21-178">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="b2f21-179">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b2f21-179">OUTPUTS</span></span>

### <span data-ttu-id="b2f21-180">Geen</span><span class="sxs-lookup"><span data-stu-id="b2f21-180">None</span></span>

<span data-ttu-id="b2f21-181">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b2f21-181">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b2f21-182">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b2f21-182">NOTES</span></span>

- <span data-ttu-id="b2f21-183">De `Clear-Item` cmdlet wordt alleen ondersteund door verschillende Power shell-providers, met inbegrip van de **alias** -, **omgevings** -, **functie** -, **register** -en **variabelen** providers.</span><span class="sxs-lookup"><span data-stu-id="b2f21-183">The `Clear-Item` cmdlet is supported only by several PowerShell providers, including the **Alias** , **Environment** , **Function** , **Registry** , and **Variable** providers.</span></span> <span data-ttu-id="b2f21-184">Zo kunt u gebruiken `Clear-Item` om de inhoud van items in de naam ruimten van de provider te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="b2f21-184">As such, you can use `Clear-Item` to delete the content of items in the provider namespaces.</span></span> <span data-ttu-id="b2f21-185">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="b2f21-185">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="b2f21-186">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b2f21-186">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
- <span data-ttu-id="b2f21-187">U kunt niet gebruiken `Clear-Item` om de inhoud van een bestand te verwijderen, omdat de Power shell-bestands provider deze cmdlet niet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="b2f21-187">You cannot use `Clear-Item` to delete the contents of a file, because the PowerShell FileSystem provider does not support this cmdlet.</span></span> <span data-ttu-id="b2f21-188">Gebruik de om bestanden te wissen `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="b2f21-188">To clear files, use the `Clear-Content`.</span></span>

## <span data-ttu-id="b2f21-189">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b2f21-189">RELATED LINKS</span></span>

[<span data-ttu-id="b2f21-190">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="b2f21-190">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="b2f21-191">Get-item</span><span class="sxs-lookup"><span data-stu-id="b2f21-191">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="b2f21-192">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="b2f21-192">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="b2f21-193">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="b2f21-193">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="b2f21-194">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="b2f21-194">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="b2f21-195">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="b2f21-195">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="b2f21-196">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="b2f21-196">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="b2f21-197">Set-item</span><span class="sxs-lookup"><span data-stu-id="b2f21-197">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="b2f21-198">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b2f21-198">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
