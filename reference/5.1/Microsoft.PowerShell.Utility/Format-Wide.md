---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: f2dccb4d0fb2d39114e5b24af8085424938ea9c7
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251757"
---
# <span data-ttu-id="060fc-103">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="060fc-103">Format-Wide</span></span>

## <span data-ttu-id="060fc-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="060fc-104">SYNOPSIS</span></span>
<span data-ttu-id="060fc-105">Maakt objecten op als een brede tabel waarin slechts één eigenschap van elk object wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-105">Formats objects as a wide table that displays only one property of each object.</span></span>

## <span data-ttu-id="060fc-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="060fc-106">SYNTAX</span></span>

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## <span data-ttu-id="060fc-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="060fc-107">DESCRIPTION</span></span>

<span data-ttu-id="060fc-108">`Format-Wide`Met de cmdlet worden objecten opgemaakt als een brede tabel waarin slechts één eigenschap van elk object wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-108">The `Format-Wide` cmdlet formats objects as a wide table that displays only one property of each object.</span></span> <span data-ttu-id="060fc-109">U kunt de **eigenschap** para meter gebruiken om te bepalen welke eigenschap wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-109">You can use the **Property** parameter to determine which property is displayed.</span></span>

## <span data-ttu-id="060fc-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="060fc-110">EXAMPLES</span></span>

### <span data-ttu-id="060fc-111">Voor beeld 1: de namen van bestanden in de huidige map Format teren</span><span class="sxs-lookup"><span data-stu-id="060fc-111">Example 1: Format names of files in the current directory</span></span>

<span data-ttu-id="060fc-112">Met deze opdracht worden de namen van de bestanden in de huidige map in drie kolommen op het scherm weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-112">This command displays the names of files in the current directory in three columns across the screen.</span></span>

```powershell
Get-ChildItem | Format-Wide -Column 3
```

<span data-ttu-id="060fc-113">Met de cmdlet Get-ChildItem worden objecten opgehaald die elk bestand in de map vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="060fc-113">The Get-ChildItem cmdlet gets objects representing each file in the directory.</span></span> <span data-ttu-id="060fc-114">De pijplijn operator (|) geeft de bestands objecten door aan de pijp lijn naar `Format-Wide` , waardoor ze worden opgemaakt voor uitvoer.</span><span class="sxs-lookup"><span data-stu-id="060fc-114">The pipeline operator (|) passes the file objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="060fc-115">De para meter **Column** geeft het aantal kolommen aan.</span><span class="sxs-lookup"><span data-stu-id="060fc-115">The **Column** parameter specifies the number of columns.</span></span>

### <span data-ttu-id="060fc-116">Voor beeld 2: de namen van register sleutels opmaken</span><span class="sxs-lookup"><span data-stu-id="060fc-116">Example 2: Format names of registry keys</span></span>

<span data-ttu-id="060fc-117">Met deze opdracht worden de namen van register sleutels in de sleutel HKEY_CURRENT_USER\Software\Microsoft weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-117">This command displays the names of registry keys in the HKEY_CURRENT_USER\Software\Microsoft key.</span></span>

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

<span data-ttu-id="060fc-118">De Get-ChildItem cmdlet haalt objecten op die de sleutels vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="060fc-118">The Get-ChildItem cmdlet gets objects representing the keys.</span></span> <span data-ttu-id="060fc-119">Het pad wordt opgegeven als HKCU:, een van de stations die worden weer gegeven door de Power shell-register provider, gevolgd door het sleutelpad.</span><span class="sxs-lookup"><span data-stu-id="060fc-119">The path is specified as HKCU:, one of the drives exposed by the PowerShell Registry provider, followed by the key path.</span></span> <span data-ttu-id="060fc-120">Met de pijplijn operator (|) worden de register sleutel objecten door gegeven via de pijp lijn naar `Format-Wide` , waarmee ze worden geformatteerd voor uitvoer.</span><span class="sxs-lookup"><span data-stu-id="060fc-120">The pipeline operator (|) passes the registry key objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="060fc-121">De **eigenschap** para meter geeft de naam van de eigenschap op en de **AutoSize** -para meter past de kolommen voor de Lees baarheid aan.</span><span class="sxs-lookup"><span data-stu-id="060fc-121">The **Property** parameter specifies the name of the property, and the **AutoSize** parameter adjusts the columns for readability.</span></span>

### <span data-ttu-id="060fc-122">Voor beeld 3: problemen met indelings fouten oplossen</span><span class="sxs-lookup"><span data-stu-id="060fc-122">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="060fc-123">In de volgende voor beelden ziet u de resultaten van het toevoegen van de para meters **Display error** of **show error** met een expressie.</span><span class="sxs-lookup"><span data-stu-id="060fc-123">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="060fc-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="060fc-124">PARAMETERS</span></span>

### <span data-ttu-id="060fc-125">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="060fc-125">-AutoSize</span></span>

<span data-ttu-id="060fc-126">Past de kolom grootte en het aantal kolommen aan op basis van de breedte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="060fc-126">Adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="060fc-127">De grootte en het aantal van de kolom worden standaard bepaald door de weer gave.</span><span class="sxs-lookup"><span data-stu-id="060fc-127">By default, the column size and number are determined by the view.</span></span> <span data-ttu-id="060fc-128">U kunt de para meters **AutoSize** en **Column** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="060fc-128">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

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

### <span data-ttu-id="060fc-129">-Kolom</span><span class="sxs-lookup"><span data-stu-id="060fc-129">-Column</span></span>

<span data-ttu-id="060fc-130">Hiermee wordt het aantal kolommen in de weer gave opgegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-130">Specifies the number of columns in the display.</span></span> <span data-ttu-id="060fc-131">U kunt de para meters **AutoSize** en **Column** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="060fc-131">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="060fc-132">-Display error</span><span class="sxs-lookup"><span data-stu-id="060fc-132">-DisplayError</span></span>

<span data-ttu-id="060fc-133">Hiermee worden fouten weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="060fc-133">Displays errors at the command line.</span></span> <span data-ttu-id="060fc-134">Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-Wide` opdracht en de expressies worden niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-134">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="060fc-135">-Uitbreiden</span><span class="sxs-lookup"><span data-stu-id="060fc-135">-Expand</span></span>

<span data-ttu-id="060fc-136">Hiermee wordt het verzamelings object opgemaakt, evenals de objecten in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="060fc-136">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="060fc-137">Deze para meter is ontworpen om objecten op te maken die ondersteuning bieden voor de ICollection-interface (System. Collections).</span><span class="sxs-lookup"><span data-stu-id="060fc-137">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="060fc-138">De standaard waarde is **EnumOnly**.</span><span class="sxs-lookup"><span data-stu-id="060fc-138">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="060fc-139">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="060fc-139">Valid values are:</span></span>

- <span data-ttu-id="060fc-140">EnumOnly: Hiermee worden de eigenschappen van de objecten in de verzameling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-140">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="060fc-141">CoreOnly: Hiermee worden de eigenschappen van het verzamelings object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-141">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="060fc-142">Beide: Hiermee worden de eigenschappen van het verzamelings object en de eigenschappen van objecten in de verzameling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-142">Both: Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="060fc-143">-Force</span><span class="sxs-lookup"><span data-stu-id="060fc-143">-Force</span></span>

<span data-ttu-id="060fc-144">Hiermee wordt aangegeven dat met deze cmdlet de beperkingen worden overschreven waarmee wordt voor komen dat de opdracht kan worden uitgevoerd, zodat de wijzigingen geen inbreuk maken op de beveiliging.</span><span class="sxs-lookup"><span data-stu-id="060fc-144">Indicates that this cmdlet overrides restrictions that prevent the command from succeeding, just so the changes do not compromise security.</span></span> <span data-ttu-id="060fc-145">**Forceert** bijvoorbeeld het kenmerk alleen-lezen of maakt mappen om een bestandspad te volt ooien, maar er wordt geen poging gedaan om bestands machtigingen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="060fc-145">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="060fc-146">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="060fc-146">-GroupBy</span></span>

<span data-ttu-id="060fc-147">Hiermee wordt de uitvoer in groepen opgemaakt op basis van een gedeelde eigenschap of waarde.</span><span class="sxs-lookup"><span data-stu-id="060fc-147">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="060fc-148">Voer een expressie of een eigenschap van de uitvoer in.</span><span class="sxs-lookup"><span data-stu-id="060fc-148">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="060fc-149">De waarde van de para meter **GroupBy** kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="060fc-149">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="060fc-150">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="060fc-150">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="060fc-151">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="060fc-151">Valid key-value pairs are:</span></span>

- <span data-ttu-id="060fc-152">Naam (of label)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="060fc-152">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="060fc-153">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="060fc-153">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="060fc-154">Tring `<string>`</span><span class="sxs-lookup"><span data-stu-id="060fc-154">FormatString - `<string>`</span></span>

<span data-ttu-id="060fc-155">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="060fc-155">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="060fc-156">-Input object</span><span class="sxs-lookup"><span data-stu-id="060fc-156">-InputObject</span></span>

<span data-ttu-id="060fc-157">Hiermee geeft u de objecten op die moeten worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="060fc-157">Specifies the objects to format.</span></span> <span data-ttu-id="060fc-158">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="060fc-158">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="060fc-159">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="060fc-159">-Property</span></span>

<span data-ttu-id="060fc-160">Hiermee geeft u de object eigenschappen op die in de weer gave worden weer gegeven en de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-160">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="060fc-161">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="060fc-161">Wildcards are permitted.</span></span>

<span data-ttu-id="060fc-162">Als u deze para meter weglaat, zijn de eigenschappen die worden weer gegeven in de weer gave afhankelijk van het object dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-162">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="060fc-163">De parameter naam ' Property ' is optioneel.</span><span class="sxs-lookup"><span data-stu-id="060fc-163">The parameter name "Property" is optional.</span></span> <span data-ttu-id="060fc-164">U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="060fc-164">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="060fc-165">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="060fc-165">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="060fc-166">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="060fc-166">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="060fc-167">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="060fc-167">Valid key-value pairs are:</span></span>

- <span data-ttu-id="060fc-168">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="060fc-168">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="060fc-169">Tring `<string>`</span><span class="sxs-lookup"><span data-stu-id="060fc-169">FormatString - `<string>`</span></span>

<span data-ttu-id="060fc-170">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="060fc-170">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="060fc-171">-Show error</span><span class="sxs-lookup"><span data-stu-id="060fc-171">-ShowError</span></span>

<span data-ttu-id="060fc-172">Hiermee worden fouten verzonden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="060fc-172">Sends errors through the pipeline.</span></span> <span data-ttu-id="060fc-173">Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-Wide` opdracht en de expressies worden niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-173">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="060fc-174">-Weer geven</span><span class="sxs-lookup"><span data-stu-id="060fc-174">-View</span></span>

<span data-ttu-id="060fc-175">Geeft de naam van een alternatieve tabel indeling of weer gave aan.</span><span class="sxs-lookup"><span data-stu-id="060fc-175">Specifies the name of an alternate table format or view.</span></span> <span data-ttu-id="060fc-176">U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="060fc-176">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="060fc-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="060fc-177">CommonParameters</span></span>

<span data-ttu-id="060fc-178">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="060fc-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="060fc-179">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="060fc-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="060fc-180">INVOER</span><span class="sxs-lookup"><span data-stu-id="060fc-180">INPUTS</span></span>

### <span data-ttu-id="060fc-181">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="060fc-181">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="060fc-182">U kunt elk object door sluizen naar `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="060fc-182">You can pipe any object to `Format-Wide`.</span></span>

## <span data-ttu-id="060fc-183">UITVOER</span><span class="sxs-lookup"><span data-stu-id="060fc-183">OUTPUTS</span></span>

### <span data-ttu-id="060fc-184">Micro soft. Power shell. commands. internal. Format</span><span class="sxs-lookup"><span data-stu-id="060fc-184">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="060fc-185">`Format-Wide` retourneert de indelings objecten die de tabel vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="060fc-185">`Format-Wide` returns format objects that represent the table.</span></span>

## <span data-ttu-id="060fc-186">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="060fc-186">NOTES</span></span>

<span data-ttu-id="060fc-187">U kunt ook verwijzen naar `Format-Wide` de ingebouwde alias `fw` .</span><span class="sxs-lookup"><span data-stu-id="060fc-187">You can also refer to `Format-Wide` by its built-in alias, `fw`.</span></span> <span data-ttu-id="060fc-188">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="060fc-188">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="060fc-189">De para meter **GroupBy** gaat ervan uit dat de objecten zijn gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="060fc-189">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="060fc-190">Gebruik `Sort-Object` voordat `Format-Custom` u de objecten groepeert.</span><span class="sxs-lookup"><span data-stu-id="060fc-190">Use `Sort-Object` before using `Format-Custom` to group the objects.</span></span>

<span data-ttu-id="060fc-191">Met de para meter **weer geven** kunt u een alternatieve notatie voor de tabel opgeven.</span><span class="sxs-lookup"><span data-stu-id="060fc-191">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="060fc-192">U kunt de weer gaven gebruiken die zijn gedefinieerd in de `*.format.PS1XML` bestanden in de Power shell-map, maar u kunt ook uw eigen weer gaven maken in nieuwe PS1XML-bestanden en de `Update-FormatData` cmdlet gebruiken om deze op te geven in Power shell.</span><span class="sxs-lookup"><span data-stu-id="060fc-192">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory or you can create your own views in new PS1XML files and use the `Update-FormatData` cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="060fc-193">De alternatieve weer gave voor de **weergave** parameter moet tabel indeling gebruiken. Als dat niet het geval is, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="060fc-193">The alternate view for the **View** parameter must use table format; if it does not, the command fails.</span></span> <span data-ttu-id="060fc-194">Als de weer gave alternatieve een lijst is, gebruikt u `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="060fc-194">If the alternate view is a list, use `Format-List`.</span></span> <span data-ttu-id="060fc-195">Als de alternatieve weer gave geen lijst of tabel is, gebruikt u indeling-aangepast.</span><span class="sxs-lookup"><span data-stu-id="060fc-195">If the alternate view is neither a list nor a table, use Format-Custom.</span></span>

## <span data-ttu-id="060fc-196">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="060fc-196">RELATED LINKS</span></span>

[<span data-ttu-id="060fc-197">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="060fc-197">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="060fc-198">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="060fc-198">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="060fc-199">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="060fc-199">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="060fc-200">Format-List</span><span class="sxs-lookup"><span data-stu-id="060fc-200">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="060fc-201">Format-Table</span><span class="sxs-lookup"><span data-stu-id="060fc-201">Format-Table</span></span>](Format-Table.md)
