---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: f78f562aba1b6cbbc2abe404c8db508de1525f5f
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251769"
---
# <span data-ttu-id="b9619-103">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="b9619-103">Format-Custom</span></span>

## <span data-ttu-id="b9619-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b9619-104">SYNOPSIS</span></span>
<span data-ttu-id="b9619-105">Maakt gebruik van een aangepaste weer gave om de uitvoer op te maken.</span><span class="sxs-lookup"><span data-stu-id="b9619-105">Uses a customized view to format the output.</span></span>

## <span data-ttu-id="b9619-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b9619-106">SYNTAX</span></span>

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## <span data-ttu-id="b9619-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b9619-107">DESCRIPTION</span></span>

<span data-ttu-id="b9619-108">De `Format-Custom` cmdlet formatteert de uitvoer van een opdracht zoals gedefinieerd in een alternatieve weer gave.</span><span class="sxs-lookup"><span data-stu-id="b9619-108">The `Format-Custom` cmdlet formats the output of a command as defined in an alternate view.</span></span>
<span data-ttu-id="b9619-109">`Format-Custom` is ontworpen om weer gaven weer te geven die niet alleen uit tabellen bestaan of alleen lijsten.</span><span class="sxs-lookup"><span data-stu-id="b9619-109">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="b9619-110">U kunt de weer gaven gebruiken die zijn gedefinieerd in Power shell, of u kunt uw eigen weer gaven maken in een nieuw `format.ps1xml` bestand en de `Update-FormatData` cmdlet gebruiken om ze toe te voegen aan Power shell.</span><span class="sxs-lookup"><span data-stu-id="b9619-110">You can use the views defined in PowerShell, or you can create your own views in a new `format.ps1xml` file and use the `Update-FormatData` cmdlet to add them to PowerShell.</span></span>

## <span data-ttu-id="b9619-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b9619-111">EXAMPLES</span></span>

### <span data-ttu-id="b9619-112">Voor beeld 1: uitvoer opmaken met een aangepaste weer gave</span><span class="sxs-lookup"><span data-stu-id="b9619-112">Example 1: Format output with a custom view</span></span>

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

<span data-ttu-id="b9619-113">Met deze opdracht wordt informatie over de `Start-Transcript` cmdlet opgemaakt in de indeling die is gedefinieerd door de weer gave MyView, een aangepaste weer gave die door de gebruiker is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b9619-113">This command formats information about the `Start-Transcript` cmdlet in the format defined by the MyView view, a custom view created by the user.</span></span> <span data-ttu-id="b9619-114">Als u deze opdracht wilt uitvoeren, moet u eerst een nieuw PS1XML-bestand maken, de weer gave **MyView** definiëren en vervolgens de `Update-FormatData` opdracht gebruiken om het PS1XML-bestand toe te voegen aan Power shell.</span><span class="sxs-lookup"><span data-stu-id="b9619-114">To run this command successfully, you must first create a new PS1XML file, define the **MyView** view, and then use the `Update-FormatData` command to add the PS1XML file to PowerShell.</span></span>

### <span data-ttu-id="b9619-115">Voor beeld 2: uitvoer opmaken met de standaard weergave</span><span class="sxs-lookup"><span data-stu-id="b9619-115">Example 2: Format output with the default view</span></span>

```powershell
Get-Process Winlogon | Format-Custom
```

<span data-ttu-id="b9619-116">Met deze opdracht wordt informatie over het **Winlogon** -proces in een alternatieve aangepaste weer gave opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="b9619-116">This command formats information about the **Winlogon** process in an alternate customized view.</span></span>
<span data-ttu-id="b9619-117">Omdat de opdracht de **weer gave** -para meter niet gebruikt, `Format-Custom` gebruikt een standaard aangepaste weer gave om de gegevens op te maken.</span><span class="sxs-lookup"><span data-stu-id="b9619-117">Because the command does not use the **View** parameter, `Format-Custom` uses a default custom view to format the data.</span></span>

### <span data-ttu-id="b9619-118">Voor beeld 3: problemen met indelings fouten oplossen</span><span class="sxs-lookup"><span data-stu-id="b9619-118">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="b9619-119">In de volgende voor beelden ziet u de resultaten van het toevoegen van de para meters **Display error** of **show error** met een expressie.</span><span class="sxs-lookup"><span data-stu-id="b9619-119">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="b9619-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b9619-120">PARAMETERS</span></span>

### <span data-ttu-id="b9619-121">-Diepte</span><span class="sxs-lookup"><span data-stu-id="b9619-121">-Depth</span></span>

<span data-ttu-id="b9619-122">Hiermee wordt het aantal kolommen in de weer gave opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b9619-122">Specifies the number of columns in the display.</span></span>

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

### <span data-ttu-id="b9619-123">-Display error</span><span class="sxs-lookup"><span data-stu-id="b9619-123">-DisplayError</span></span>

<span data-ttu-id="b9619-124">Hiermee worden fouten weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="b9619-124">Displays errors at the command line.</span></span> <span data-ttu-id="b9619-125">Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-Custom` opdracht en de expressies worden niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9619-125">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="b9619-126">-Uitbreiden</span><span class="sxs-lookup"><span data-stu-id="b9619-126">-Expand</span></span>

<span data-ttu-id="b9619-127">Hiermee wordt het verzamelings object opgemaakt, evenals de objecten in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="b9619-127">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="b9619-128">Deze para meter is ontworpen om objecten op te maken die ondersteuning bieden voor de interface **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="b9619-128">This parameter is designed to format objects that support the **System.Collections.ICollection** interface.</span></span> <span data-ttu-id="b9619-129">De standaard waarde is **EnumOnly**.</span><span class="sxs-lookup"><span data-stu-id="b9619-129">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="b9619-130">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="b9619-130">Valid values are:</span></span>

- <span data-ttu-id="b9619-131">EnumOnly: Hiermee worden de eigenschappen van de objecten in de verzameling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9619-131">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="b9619-132">CoreOnly: Hiermee worden de eigenschappen van het verzamelings object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9619-132">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="b9619-133">Beide: Hiermee worden de eigenschappen van het verzamelings object en de objecten in de verzameling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9619-133">Both: Displays the properties of the collection object and the objects in the collection.</span></span>

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

### <span data-ttu-id="b9619-134">-Force</span><span class="sxs-lookup"><span data-stu-id="b9619-134">-Force</span></span>

<span data-ttu-id="b9619-135">Hiermee wordt de cmdlet doorgestuurd om alle fout gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b9619-135">Directs the cmdlet to display all of the error information.</span></span> <span data-ttu-id="b9619-136">Gebruik met de para meters **Display error** of **show error** .</span><span class="sxs-lookup"><span data-stu-id="b9619-136">Use with the **DisplayError** or **ShowError** parameters.</span></span> <span data-ttu-id="b9619-137">Wanneer een fout object naar de fout wordt geschreven of stromen weer geven, wordt standaard slechts een deel van de fout informatie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9619-137">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="b9619-138">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="b9619-138">-GroupBy</span></span>

<span data-ttu-id="b9619-139">Hiermee wordt de uitvoer in groepen opgemaakt op basis van een gedeelde eigenschap of waarde.</span><span class="sxs-lookup"><span data-stu-id="b9619-139">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="b9619-140">Voer een expressie of een eigenschap van de uitvoer in.</span><span class="sxs-lookup"><span data-stu-id="b9619-140">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="b9619-141">De waarde van de para meter **GroupBy** kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="b9619-141">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="b9619-142">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="b9619-142">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="b9619-143">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="b9619-143">Valid key-value pairs are:</span></span>

- <span data-ttu-id="b9619-144">Naam (of label)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="b9619-144">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="b9619-145">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="b9619-145">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="b9619-146">Tring `<string>`</span><span class="sxs-lookup"><span data-stu-id="b9619-146">FormatString - `<string>`</span></span>

<span data-ttu-id="b9619-147">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9619-147">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="b9619-148">-Input object</span><span class="sxs-lookup"><span data-stu-id="b9619-148">-InputObject</span></span>

<span data-ttu-id="b9619-149">Geeft aan welke objecten moeten worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="b9619-149">Specifies the objects to be formatted.</span></span> <span data-ttu-id="b9619-150">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9619-150">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="b9619-151">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="b9619-151">-Property</span></span>

<span data-ttu-id="b9619-152">Hiermee geeft u de object eigenschappen op die in de weer gave worden weer gegeven en de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9619-152">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="b9619-153">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b9619-153">Wildcards are permitted.</span></span>

<span data-ttu-id="b9619-154">Als u deze para meter weglaat, zijn de eigenschappen die worden weer gegeven in de weer gave afhankelijk van het object dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9619-154">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="b9619-155">De parameter naam **eigenschap** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="b9619-155">The parameter name **Property** is optional.</span></span> <span data-ttu-id="b9619-156">U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="b9619-156">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="b9619-157">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="b9619-157">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="b9619-158">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="b9619-158">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="b9619-159">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="b9619-159">Valid key-value pairs are:</span></span>

- <span data-ttu-id="b9619-160">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="b9619-160">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="b9619-161">Diepga `<int32>`</span><span class="sxs-lookup"><span data-stu-id="b9619-161">Depth - `<int32>`</span></span>

<span data-ttu-id="b9619-162">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9619-162">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b9619-163">-Show error</span><span class="sxs-lookup"><span data-stu-id="b9619-163">-ShowError</span></span>

<span data-ttu-id="b9619-164">Hiermee worden fouten verzonden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b9619-164">Sends errors through the pipeline.</span></span> <span data-ttu-id="b9619-165">Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-Custom` opdracht en de expressies worden niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9619-165">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="b9619-166">-Weer geven</span><span class="sxs-lookup"><span data-stu-id="b9619-166">-View</span></span>

<span data-ttu-id="b9619-167">Hiermee geeft u de naam van een alternatieve notatie of weer gave.</span><span class="sxs-lookup"><span data-stu-id="b9619-167">Specifies the name of an alternate format or view.</span></span> <span data-ttu-id="b9619-168">Als u deze para meter weglaat, `Format-Custom` wordt een standaard aangepaste weer gave gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b9619-168">If you omit this parameter, `Format-Custom` uses a default custom view.</span></span> <span data-ttu-id="b9619-169">U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="b9619-169">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="b9619-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b9619-170">CommonParameters</span></span>

<span data-ttu-id="b9619-171">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b9619-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b9619-172">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9619-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b9619-173">INVOER</span><span class="sxs-lookup"><span data-stu-id="b9619-173">INPUTS</span></span>

### <span data-ttu-id="b9619-174">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b9619-174">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b9619-175">U kunt elk object door sluizen naar `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="b9619-175">You can pipe any object to `Format-Custom`.</span></span>

## <span data-ttu-id="b9619-176">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b9619-176">OUTPUTS</span></span>

### <span data-ttu-id="b9619-177">Micro soft. Power shell. commands. internal. Format</span><span class="sxs-lookup"><span data-stu-id="b9619-177">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="b9619-178">`Format-Custom` retourneert de indelings objecten die de weer gave vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="b9619-178">`Format-Custom` returns the format objects that represent the display.</span></span>

## <span data-ttu-id="b9619-179">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b9619-179">NOTES</span></span>

<span data-ttu-id="b9619-180">`Format-Custom` is ontworpen om weer gaven weer te geven die niet alleen uit tabellen bestaan of alleen lijsten.</span><span class="sxs-lookup"><span data-stu-id="b9619-180">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="b9619-181">Als u een alternatieve tabel weergave wilt weer geven, gebruikt u `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="b9619-181">To display an alternate table view, use `Format-Table`.</span></span> <span data-ttu-id="b9619-182">Als u een alternatieve lijst weergave wilt weer geven, gebruikt u `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="b9619-182">To display an alternate list view, use `Format-List`.</span></span>

<span data-ttu-id="b9619-183">U kunt ook verwijzen naar `Format-Custom` de ingebouwde alias `fc` .</span><span class="sxs-lookup"><span data-stu-id="b9619-183">You can also refer to `Format-Custom` by its built-in alias, `fc`.</span></span> <span data-ttu-id="b9619-184">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9619-184">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="b9619-185">De para meter **GroupBy** gaat ervan uit dat de objecten zijn gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="b9619-185">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="b9619-186">Voordat u `Format-Custom` de objecten groepeert, kunt u `Sort-Object` deze gebruiken om ze te sorteren.</span><span class="sxs-lookup"><span data-stu-id="b9619-186">Before using `Format-Custom` to group the objects, use `Sort-Object` to sort them.</span></span>

## <span data-ttu-id="b9619-187">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b9619-187">RELATED LINKS</span></span>

[<span data-ttu-id="b9619-188">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="b9619-188">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="b9619-189">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="b9619-189">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="b9619-190">Format-List</span><span class="sxs-lookup"><span data-stu-id="b9619-190">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="b9619-191">Format-Table</span><span class="sxs-lookup"><span data-stu-id="b9619-191">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="b9619-192">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="b9619-192">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="b9619-193">Get-Process</span><span class="sxs-lookup"><span data-stu-id="b9619-193">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
