---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: fef31cbf015642d6ae499ebb57b30328a53f266e
ms.sourcegitcommit: c91f79576bc54e162bcc7adf78026417b2776687
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2021
ms.locfileid: "106274390"
---
# <span data-ttu-id="a51f6-102">New-Alias</span><span class="sxs-lookup"><span data-stu-id="a51f6-102">New-Alias</span></span>

## <span data-ttu-id="a51f6-103">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="a51f6-103">Synopsis</span></span>
<span data-ttu-id="a51f6-104">Hiermee maakt u een nieuwe alias.</span><span class="sxs-lookup"><span data-stu-id="a51f6-104">Creates a new alias.</span></span>

## <span data-ttu-id="a51f6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a51f6-105">Syntax</span></span>

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a51f6-106">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a51f6-106">Description</span></span>

<span data-ttu-id="a51f6-107">De `New-Alias` cmdlet maakt een nieuwe alias in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="a51f6-107">The `New-Alias` cmdlet creates a new alias in the current PowerShell session.</span></span> <span data-ttu-id="a51f6-108">Aliassen die zijn gemaakt met behulp van `New-Alias` worden niet opgeslagen nadat u de sessie afsluit of Power shell sluiten.</span><span class="sxs-lookup"><span data-stu-id="a51f6-108">Aliases created by using `New-Alias` are not saved after you exit the session or close PowerShell.</span></span>
<span data-ttu-id="a51f6-109">U kunt de- `Export-Alias` cmdlet gebruiken om uw alias gegevens op te slaan in een bestand.</span><span class="sxs-lookup"><span data-stu-id="a51f6-109">You can use the `Export-Alias` cmdlet to save your alias information to a file.</span></span> <span data-ttu-id="a51f6-110">U kunt later gebruiken `Import-Alias` om die opgeslagen alias gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="a51f6-110">You can later use `Import-Alias` to retrieve that saved alias information.</span></span>

## <span data-ttu-id="a51f6-111">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="a51f6-111">Examples</span></span>

### <span data-ttu-id="a51f6-112">Voor beeld 1: een alias maken voor een cmdlet</span><span class="sxs-lookup"><span data-stu-id="a51f6-112">Example 1: Create an alias for a cmdlet</span></span>

```
New-Alias -Name "List" Get-ChildItem
```

<span data-ttu-id="a51f6-113">Met deze opdracht maakt u een alias met de naam lijst die de Get-ChildItem-cmdlet vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a51f6-113">This command creates an alias named List to represent the Get-ChildItem cmdlet.</span></span>

### <span data-ttu-id="a51f6-114">Voor beeld 2: een alleen-lezen-alias maken voor een cmdlet</span><span class="sxs-lookup"><span data-stu-id="a51f6-114">Example 2: Create a read-only alias for a cmdlet</span></span>

```
New-Alias -Name "C" -Value Get-ChildItem -Description "quick gci alias" -Option ReadOnly
Get-Alias -Name "C" | Format-List *
```

<span data-ttu-id="a51f6-115">Met deze opdracht maakt u een alias `C` met de naam die de `Get-ChildItem` cmdlet vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a51f6-115">This command creates an alias named `C` to represent the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="a51f6-116">Er wordt een beschrijving, een snelle WMI-alias voor de alias gemaakt en deze wordt alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="a51f6-116">It creates a description, quick wmi alias, for the alias and makes it read-only.</span></span> <span data-ttu-id="a51f6-117">De laatste regel van de opdracht wordt gebruikt `Get-Alias` om de nieuwe alias op te halen en deze te Format-List om alle informatie hierover weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a51f6-117">The last line of the command uses `Get-Alias` to get the new alias and pipes it to Format-List to display all of the information about it.</span></span>

## <span data-ttu-id="a51f6-118">Parameters</span><span class="sxs-lookup"><span data-stu-id="a51f6-118">Parameters</span></span>

### <span data-ttu-id="a51f6-119">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a51f6-119">-Description</span></span>

<span data-ttu-id="a51f6-120">Hiermee geeft u een beschrijving van de alias.</span><span class="sxs-lookup"><span data-stu-id="a51f6-120">Specifies a description of the alias.</span></span> <span data-ttu-id="a51f6-121">U kunt een wille keurige teken reeks typen.</span><span class="sxs-lookup"><span data-stu-id="a51f6-121">You can type any string.</span></span> <span data-ttu-id="a51f6-122">Als de beschrijving spaties bevat, plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="a51f6-122">If the description includes spaces, enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="a51f6-123">-Force</span><span class="sxs-lookup"><span data-stu-id="a51f6-123">-Force</span></span>

<span data-ttu-id="a51f6-124">Geeft aan dat de cmdlet fungeert `Set-Alias` als de alias die al bestaat.</span><span class="sxs-lookup"><span data-stu-id="a51f6-124">Indicates that the cmdlet acts like `Set-Alias` if the alias named already exists.</span></span>

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

### <span data-ttu-id="a51f6-125">-Name</span><span class="sxs-lookup"><span data-stu-id="a51f6-125">-Name</span></span>

<span data-ttu-id="a51f6-126">Hiermee geeft u de nieuwe alias.</span><span class="sxs-lookup"><span data-stu-id="a51f6-126">Specifies the new alias.</span></span> <span data-ttu-id="a51f6-127">U kunt alle alfanumerieke tekens in een alias gebruiken, maar het eerste teken mag geen getal zijn.</span><span class="sxs-lookup"><span data-stu-id="a51f6-127">You can use any alphanumeric characters in an alias, but the first character cannot be a number.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a51f6-128">-Optie</span><span class="sxs-lookup"><span data-stu-id="a51f6-128">-Option</span></span>

<span data-ttu-id="a51f6-129">Hiermee geeft u de waarde van de eigenschap **Options** van de alias.</span><span class="sxs-lookup"><span data-stu-id="a51f6-129">Specifies the value of the **Options** property of the alias.</span></span>
<span data-ttu-id="a51f6-130">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="a51f6-130">Valid values are:</span></span>

- <span data-ttu-id="a51f6-131">`None`: De alias heeft geen beperkingen (standaard waarde)</span><span class="sxs-lookup"><span data-stu-id="a51f6-131">`None`: The alias has no constraints (default value)</span></span>
- <span data-ttu-id="a51f6-132">`ReadOnly`: De alias kan worden verwijderd, maar kan niet worden gewijzigd met behulp van de para meter **Force**</span><span class="sxs-lookup"><span data-stu-id="a51f6-132">`ReadOnly`: The alias can be deleted but cannot be changed except by using the **Force** parameter</span></span>
- <span data-ttu-id="a51f6-133">`Constant`: De alias kan niet worden verwijderd of gewijzigd</span><span class="sxs-lookup"><span data-stu-id="a51f6-133">`Constant`: The alias cannot be deleted or changed</span></span>
- <span data-ttu-id="a51f6-134">`Private`: De alias is alleen beschikbaar in het huidige bereik</span><span class="sxs-lookup"><span data-stu-id="a51f6-134">`Private`: The alias is available only in the current scope</span></span>
- <span data-ttu-id="a51f6-135">`AllScope`: De alias wordt gekopieerd naar een nieuwe scope die wordt gemaakt</span><span class="sxs-lookup"><span data-stu-id="a51f6-135">`AllScope`: The alias is copied to any new scopes that are created</span></span>
- <span data-ttu-id="a51f6-136">`Unspecified`: De optie is niet opgegeven</span><span class="sxs-lookup"><span data-stu-id="a51f6-136">`Unspecified`: The option is not specified</span></span>

<span data-ttu-id="a51f6-137">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="a51f6-137">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="a51f6-138">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="a51f6-138">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="a51f6-139">De waarden kunnen worden door gegeven aan de para meter **Option** als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="a51f6-139">The values can be passed to the **Option** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="a51f6-140">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="a51f6-140">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="a51f6-141">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="a51f6-141">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

<span data-ttu-id="a51f6-142">Als u de eigenschap **Options** van alle aliassen in de sessie wilt weer geven, typt u `Get-Alias | Format-Table -Property Name, Options -AutoSize` .</span><span class="sxs-lookup"><span data-stu-id="a51f6-142">To see the **Options** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -AutoSize`.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a51f6-143">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a51f6-143">-PassThru</span></span>

<span data-ttu-id="a51f6-144">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="a51f6-144">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="a51f6-145">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a51f6-145">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a51f6-146">-Bereik</span><span class="sxs-lookup"><span data-stu-id="a51f6-146">-Scope</span></span>

<span data-ttu-id="a51f6-147">Hiermee wordt het bereik van de nieuwe alias opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a51f6-147">Specifies the scope of the new alias.</span></span> <span data-ttu-id="a51f6-148">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="a51f6-148">The acceptable values for this parameter are:</span></span>

- `Global`
- `Local`
- `Script`
- <span data-ttu-id="a51f6-149">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij `0` het huidige bereik is en de `1` bovenliggende scope).</span><span class="sxs-lookup"><span data-stu-id="a51f6-149">A number relative to the current scope (0 through the number of scopes, where `0` is the current scope and `1` is its parent).</span></span>

<span data-ttu-id="a51f6-150">`Local` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="a51f6-150">`Local` is the default.</span></span> <span data-ttu-id="a51f6-151">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a51f6-151">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="a51f6-152">-Waarde</span><span class="sxs-lookup"><span data-stu-id="a51f6-152">-Value</span></span>

<span data-ttu-id="a51f6-153">Hiermee geeft u de naam op van de cmdlet of het opdracht element waarvoor een alias wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="a51f6-153">Specifies the name of the cmdlet or command element that is being aliased.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a51f6-154">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a51f6-154">-Confirm</span></span>

<span data-ttu-id="a51f6-155">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a51f6-155">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a51f6-156">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a51f6-156">-WhatIf</span></span>

<span data-ttu-id="a51f6-157">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a51f6-157">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a51f6-158">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a51f6-158">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a51f6-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a51f6-159">CommonParameters</span></span>

<span data-ttu-id="a51f6-160">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a51f6-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a51f6-161">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a51f6-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a51f6-162">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="a51f6-162">Inputs</span></span>

### <span data-ttu-id="a51f6-163">Geen</span><span class="sxs-lookup"><span data-stu-id="a51f6-163">None</span></span>

<span data-ttu-id="a51f6-164">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a51f6-164">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a51f6-165">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="a51f6-165">Outputs</span></span>

### <span data-ttu-id="a51f6-166">Geen of System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="a51f6-166">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="a51f6-167">Wanneer u de para meter **PassThru** gebruikt, `New-Alias` genereert een **System. Management. Automation. AliasInfo** -object dat de nieuwe alias vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a51f6-167">When you use the **Passthru** parameter, `New-Alias` generates a **System.Management.Automation.AliasInfo** object representing the new alias.</span></span> <span data-ttu-id="a51f6-168">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a51f6-168">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a51f6-169">Notities</span><span class="sxs-lookup"><span data-stu-id="a51f6-169">Notes</span></span>

- <span data-ttu-id="a51f6-170">Als u een nieuwe alias wilt maken, gebruikt u `Set-Alias` of `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="a51f6-170">To create a new alias, use `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="a51f6-171">Als u een alias wilt wijzigen, gebruikt u `Set-Alias` .</span><span class="sxs-lookup"><span data-stu-id="a51f6-171">To change an alias, use `Set-Alias`.</span></span> <span data-ttu-id="a51f6-172">Als u een alias wilt verwijderen, gebruikt u `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="a51f6-172">To delete an alias, use `Remove-Item`.</span></span>

## <span data-ttu-id="a51f6-173">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="a51f6-173">Related Links</span></span>

[<span data-ttu-id="a51f6-174">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="a51f6-174">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="a51f6-175">Get-alias</span><span class="sxs-lookup"><span data-stu-id="a51f6-175">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="a51f6-176">Import-alias</span><span class="sxs-lookup"><span data-stu-id="a51f6-176">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="a51f6-177">Set-alias</span><span class="sxs-lookup"><span data-stu-id="a51f6-177">Set-Alias</span></span>](Set-Alias.md)

