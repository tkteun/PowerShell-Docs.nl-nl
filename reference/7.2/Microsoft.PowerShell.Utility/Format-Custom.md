---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: ff4b2dda3f12fa34fc518c6a180f3213ba873d90
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705457"
---
# <span data-ttu-id="d7bb6-102">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="d7bb6-102">Format-Custom</span></span>

## <span data-ttu-id="d7bb6-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d7bb6-103">SYNOPSIS</span></span>
<span data-ttu-id="d7bb6-104">Maakt gebruik van een aangepaste weer gave om de uitvoer op te maken.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-104">Uses a customized view to format the output.</span></span>

## <span data-ttu-id="d7bb6-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d7bb6-105">SYNTAX</span></span>

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## <span data-ttu-id="d7bb6-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d7bb6-106">DESCRIPTION</span></span>

<span data-ttu-id="d7bb6-107">De `Format-Custom` cmdlet formatteert de uitvoer van een opdracht zoals gedefinieerd in een alternatieve weer gave.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-107">The `Format-Custom` cmdlet formats the output of a command as defined in an alternate view.</span></span>
<span data-ttu-id="d7bb6-108">`Format-Custom` is ontworpen om weer gaven weer te geven die niet alleen uit tabellen bestaan of alleen lijsten.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-108">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="d7bb6-109">U kunt de weer gaven gebruiken die zijn gedefinieerd in Power shell, of u kunt uw eigen weer gaven maken in een nieuw `format.ps1xml` bestand en de `Update-FormatData` cmdlet gebruiken om ze toe te voegen aan Power shell.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-109">You can use the views defined in PowerShell, or you can create your own views in a new `format.ps1xml` file and use the `Update-FormatData` cmdlet to add them to PowerShell.</span></span>

## <span data-ttu-id="d7bb6-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d7bb6-110">EXAMPLES</span></span>

### <span data-ttu-id="d7bb6-111">Voor beeld 1: uitvoer opmaken met een aangepaste weer gave</span><span class="sxs-lookup"><span data-stu-id="d7bb6-111">Example 1: Format output with a custom view</span></span>

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

<span data-ttu-id="d7bb6-112">Met deze opdracht wordt informatie over de `Start-Transcript` cmdlet opgemaakt in de indeling die is gedefinieerd door de weer gave MyView, een aangepaste weer gave die door de gebruiker is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-112">This command formats information about the `Start-Transcript` cmdlet in the format defined by the MyView view, a custom view created by the user.</span></span> <span data-ttu-id="d7bb6-113">Als u deze opdracht wilt uitvoeren, moet u eerst een nieuw PS1XML-bestand maken, de weer gave **MyView** definiëren en vervolgens de `Update-FormatData` opdracht gebruiken om het PS1XML-bestand toe te voegen aan Power shell.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-113">To run this command successfully, you must first create a new PS1XML file, define the **MyView** view, and then use the `Update-FormatData` command to add the PS1XML file to PowerShell.</span></span>

### <span data-ttu-id="d7bb6-114">Voor beeld 2: uitvoer opmaken met de standaard weergave</span><span class="sxs-lookup"><span data-stu-id="d7bb6-114">Example 2: Format output with the default view</span></span>

```powershell
Get-Process Winlogon | Format-Custom
```

<span data-ttu-id="d7bb6-115">Met deze opdracht wordt informatie over het **Winlogon** -proces in een alternatieve aangepaste weer gave opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-115">This command formats information about the **Winlogon** process in an alternate customized view.</span></span>
<span data-ttu-id="d7bb6-116">Omdat de opdracht de **weer gave** -para meter niet gebruikt, `Format-Custom` gebruikt een standaard aangepaste weer gave om de gegevens op te maken.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-116">Because the command does not use the **View** parameter, `Format-Custom` uses a default custom view to format the data.</span></span>

### <span data-ttu-id="d7bb6-117">Voor beeld 3: problemen met indelings fouten oplossen</span><span class="sxs-lookup"><span data-stu-id="d7bb6-117">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="d7bb6-118">In de volgende voor beelden ziet u de resultaten van het toevoegen van de para meters **Display error** of **show error** met een expressie.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-118">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

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

## <span data-ttu-id="d7bb6-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d7bb6-119">PARAMETERS</span></span>

### <span data-ttu-id="d7bb6-120">-Diepte</span><span class="sxs-lookup"><span data-stu-id="d7bb6-120">-Depth</span></span>

<span data-ttu-id="d7bb6-121">Hiermee wordt het aantal kolommen in de weer gave opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-121">Specifies the number of columns in the display.</span></span>

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

### <span data-ttu-id="d7bb6-122">-Display error</span><span class="sxs-lookup"><span data-stu-id="d7bb6-122">-DisplayError</span></span>

<span data-ttu-id="d7bb6-123">Hiermee worden fouten weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-123">Displays errors at the command line.</span></span> <span data-ttu-id="d7bb6-124">Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-Custom` opdracht en de expressies worden niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-124">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="d7bb6-125">-Uitbreiden</span><span class="sxs-lookup"><span data-stu-id="d7bb6-125">-Expand</span></span>

<span data-ttu-id="d7bb6-126">Hiermee wordt het verzamelings object opgemaakt, evenals de objecten in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-126">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="d7bb6-127">Deze para meter is ontworpen om objecten op te maken die ondersteuning bieden voor de interface **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="d7bb6-127">This parameter is designed to format objects that support the **System.Collections.ICollection** interface.</span></span> <span data-ttu-id="d7bb6-128">De standaard waarde is **EnumOnly**.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-128">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="d7bb6-129">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="d7bb6-129">Valid values are:</span></span>

- <span data-ttu-id="d7bb6-130">EnumOnly: Hiermee worden de eigenschappen van de objecten in de verzameling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-130">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="d7bb6-131">CoreOnly: Hiermee worden de eigenschappen van het verzamelings object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-131">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="d7bb6-132">Beide: Hiermee worden de eigenschappen van het verzamelings object en de objecten in de verzameling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-132">Both: Displays the properties of the collection object and the objects in the collection.</span></span>

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

### <span data-ttu-id="d7bb6-133">-Force</span><span class="sxs-lookup"><span data-stu-id="d7bb6-133">-Force</span></span>

<span data-ttu-id="d7bb6-134">Hiermee wordt de cmdlet doorgestuurd om alle fout gegevens weer te geven.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-134">Directs the cmdlet to display all of the error information.</span></span> <span data-ttu-id="d7bb6-135">Gebruik met de para meters **Display error** of **show error** .</span><span class="sxs-lookup"><span data-stu-id="d7bb6-135">Use with the **DisplayError** or **ShowError** parameters.</span></span> <span data-ttu-id="d7bb6-136">Wanneer een fout object naar de fout wordt geschreven of stromen weer geven, wordt standaard slechts een deel van de fout informatie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-136">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="d7bb6-137">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="d7bb6-137">-GroupBy</span></span>

<span data-ttu-id="d7bb6-138">Hiermee wordt de uitvoer in groepen opgemaakt op basis van een gedeelde eigenschap of waarde.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-138">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="d7bb6-139">Voer een expressie of een eigenschap van de uitvoer in.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-139">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="d7bb6-140">De waarde van de para meter **GroupBy** kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-140">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="d7bb6-141">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-141">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="d7bb6-142">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="d7bb6-142">Valid key-value pairs are:</span></span>

- <span data-ttu-id="d7bb6-143">Naam (of label)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="d7bb6-143">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="d7bb6-144">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="d7bb6-144">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="d7bb6-145">Tring `<string>`</span><span class="sxs-lookup"><span data-stu-id="d7bb6-145">FormatString - `<string>`</span></span>

<span data-ttu-id="d7bb6-146">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-146">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="d7bb6-147">-Input object</span><span class="sxs-lookup"><span data-stu-id="d7bb6-147">-InputObject</span></span>

<span data-ttu-id="d7bb6-148">Geeft aan welke objecten moeten worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-148">Specifies the objects to be formatted.</span></span> <span data-ttu-id="d7bb6-149">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-149">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="d7bb6-150">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="d7bb6-150">-Property</span></span>

<span data-ttu-id="d7bb6-151">Hiermee geeft u de object eigenschappen op die in de weer gave worden weer gegeven en de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-151">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="d7bb6-152">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-152">Wildcards are permitted.</span></span>

<span data-ttu-id="d7bb6-153">Als u deze para meter weglaat, zijn de eigenschappen die worden weer gegeven in de weer gave afhankelijk van het object dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-153">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="d7bb6-154">De parameter naam **eigenschap** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-154">The parameter name **Property** is optional.</span></span> <span data-ttu-id="d7bb6-155">U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-155">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="d7bb6-156">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-156">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="d7bb6-157">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-157">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="d7bb6-158">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="d7bb6-158">Valid key-value pairs are:</span></span>

- <span data-ttu-id="d7bb6-159">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="d7bb6-159">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="d7bb6-160">Diepga `<int32>`</span><span class="sxs-lookup"><span data-stu-id="d7bb6-160">Depth - `<int32>`</span></span>

<span data-ttu-id="d7bb6-161">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-161">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="d7bb6-162">-Show error</span><span class="sxs-lookup"><span data-stu-id="d7bb6-162">-ShowError</span></span>

<span data-ttu-id="d7bb6-163">Hiermee worden fouten verzonden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-163">Sends errors through the pipeline.</span></span> <span data-ttu-id="d7bb6-164">Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-Custom` opdracht en de expressies worden niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-164">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="d7bb6-165">-Weer geven</span><span class="sxs-lookup"><span data-stu-id="d7bb6-165">-View</span></span>

<span data-ttu-id="d7bb6-166">Hiermee geeft u de naam van een alternatieve notatie of weer gave.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-166">Specifies the name of an alternate format or view.</span></span> <span data-ttu-id="d7bb6-167">Als u deze para meter weglaat, `Format-Custom` wordt een standaard aangepaste weer gave gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-167">If you omit this parameter, `Format-Custom` uses a default custom view.</span></span> <span data-ttu-id="d7bb6-168">U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-168">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="d7bb6-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d7bb6-169">CommonParameters</span></span>

<span data-ttu-id="d7bb6-170">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-170">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d7bb6-171">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-171">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d7bb6-172">INVOER</span><span class="sxs-lookup"><span data-stu-id="d7bb6-172">INPUTS</span></span>

### <span data-ttu-id="d7bb6-173">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="d7bb6-173">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="d7bb6-174">U kunt elk object door sluizen naar `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="d7bb6-174">You can pipe any object to `Format-Custom`.</span></span>

## <span data-ttu-id="d7bb6-175">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d7bb6-175">OUTPUTS</span></span>

### <span data-ttu-id="d7bb6-176">Micro soft. Power shell. commands. internal. Format</span><span class="sxs-lookup"><span data-stu-id="d7bb6-176">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="d7bb6-177">`Format-Custom` retourneert de indelings objecten die de weer gave vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-177">`Format-Custom` returns the format objects that represent the display.</span></span>

## <span data-ttu-id="d7bb6-178">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d7bb6-178">NOTES</span></span>

<span data-ttu-id="d7bb6-179">`Format-Custom` is ontworpen om weer gaven weer te geven die niet alleen uit tabellen bestaan of alleen lijsten.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-179">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="d7bb6-180">Als u een alternatieve tabel weergave wilt weer geven, gebruikt u `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="d7bb6-180">To display an alternate table view, use `Format-Table`.</span></span> <span data-ttu-id="d7bb6-181">Als u een alternatieve lijst weergave wilt weer geven, gebruikt u `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="d7bb6-181">To display an alternate list view, use `Format-List`.</span></span>

<span data-ttu-id="d7bb6-182">U kunt ook verwijzen naar `Format-Custom` de ingebouwde alias `fc` .</span><span class="sxs-lookup"><span data-stu-id="d7bb6-182">You can also refer to `Format-Custom` by its built-in alias, `fc`.</span></span> <span data-ttu-id="d7bb6-183">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-183">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="d7bb6-184">De para meter **GroupBy** gaat ervan uit dat de objecten zijn gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-184">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="d7bb6-185">Voordat u `Format-Custom` de objecten groepeert, kunt u `Sort-Object` deze gebruiken om ze te sorteren.</span><span class="sxs-lookup"><span data-stu-id="d7bb6-185">Before using `Format-Custom` to group the objects, use `Sort-Object` to sort them.</span></span>

## <span data-ttu-id="d7bb6-186">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d7bb6-186">RELATED LINKS</span></span>

[<span data-ttu-id="d7bb6-187">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="d7bb6-187">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="d7bb6-188">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="d7bb6-188">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="d7bb6-189">Format-List</span><span class="sxs-lookup"><span data-stu-id="d7bb6-189">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="d7bb6-190">Format-Table</span><span class="sxs-lookup"><span data-stu-id="d7bb6-190">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="d7bb6-191">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="d7bb6-191">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="d7bb6-192">Get-Process</span><span class="sxs-lookup"><span data-stu-id="d7bb6-192">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
