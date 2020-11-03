---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: 7817384f077c58b46aed1dba552f89ac431891f0
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251759"
---
# <span data-ttu-id="abf68-103">Format-List</span><span class="sxs-lookup"><span data-stu-id="abf68-103">Format-List</span></span>

## <span data-ttu-id="abf68-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="abf68-104">SYNOPSIS</span></span>
<span data-ttu-id="abf68-105">Hiermee wordt de uitvoer opgemaakt als een lijst met eigenschappen waarin elke eigenschap op een nieuwe regel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-105">Formats the output as a list of properties in which each property appears on a new line.</span></span>

## <span data-ttu-id="abf68-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="abf68-106">SYNTAX</span></span>

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## <span data-ttu-id="abf68-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="abf68-107">DESCRIPTION</span></span>

<span data-ttu-id="abf68-108">De `Format-List` cmdlet formatteert de uitvoer van een opdracht als een lijst met eigenschappen waarin elke eigenschap op een afzonderlijke regel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-108">The `Format-List` cmdlet formats the output of a command as a list of properties in which each property is displayed on a separate line.</span></span> <span data-ttu-id="abf68-109">U kunt gebruiken `Format-List` om alle of geselecteerde eigenschappen van een object op te maken en weer te geven als een lijst (opmaak lijst \*).</span><span class="sxs-lookup"><span data-stu-id="abf68-109">You can use `Format-List` to format and display all or selected properties of an object as a list (format-list \*).</span></span>

<span data-ttu-id="abf68-110">Omdat er meer ruimte beschikbaar is voor elk item in een lijst dan in een tabel, worden in Power Shell meer eigenschappen van het object in de lijst weer gegeven en worden de eigenschapwaarden minder waarschijnlijk afgekapt.</span><span class="sxs-lookup"><span data-stu-id="abf68-110">Because more space is available for each item in a list than in a table, PowerShell displays more properties of the object in the list, and the property values are less likely to be truncated.</span></span>

## <span data-ttu-id="abf68-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="abf68-111">EXAMPLES</span></span>

### <span data-ttu-id="abf68-112">Voor beeld 1: computer services Format teren</span><span class="sxs-lookup"><span data-stu-id="abf68-112">Example 1: Format computer services</span></span>

```powershell
Get-Service | Format-List
```

<span data-ttu-id="abf68-113">Met deze opdracht wordt informatie over services op de computer als een lijst opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="abf68-113">This command formats information about services on the computer as a list.</span></span> <span data-ttu-id="abf68-114">Standaard worden de services opgemaakt als een tabel.</span><span class="sxs-lookup"><span data-stu-id="abf68-114">By default, the services are formatted as a table.</span></span> <span data-ttu-id="abf68-115">De `Get-Service` cmdlet haalt objecten op die de services op de computer vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="abf68-115">The `Get-Service` cmdlet gets objects representing the services on the computer.</span></span> <span data-ttu-id="abf68-116">De pijplijn operator (|) geeft de resultaten door de pijp lijn door aan `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="abf68-116">The pipeline operator (|) passes the results through the pipeline to `Format-List`.</span></span>
<span data-ttu-id="abf68-117">De `Format-List` opdracht formatteert vervolgens de service gegevens in een lijst en verzendt deze naar de standaard uitvoer-cmdlet om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="abf68-117">Then, the `Format-List` command formats the service information in a list and sends it to the default output cmdlet for display.</span></span>

### <span data-ttu-id="abf68-118">Voor beeld 2: PS1XML-bestanden Format teren</span><span class="sxs-lookup"><span data-stu-id="abf68-118">Example 2: Format PS1XML files</span></span>

<span data-ttu-id="abf68-119">Met deze opdrachten wordt informatie weer gegeven over de PS1XML-bestanden in de Power shell-map als een lijst.</span><span class="sxs-lookup"><span data-stu-id="abf68-119">These commands display information about the PS1XML files in the PowerShell directory as a list.</span></span>

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

<span data-ttu-id="abf68-120">Met de eerste opdracht worden de objecten opgehaald die de bestanden vertegenwoordigen en opgeslagen in de `$A` variabele.</span><span class="sxs-lookup"><span data-stu-id="abf68-120">The first command gets the objects representing the files and stores them in the `$A` variable.</span></span>

<span data-ttu-id="abf68-121">De tweede opdracht wordt gebruikt `Format-List` voor het opmaken van informatie over objecten die zijn opgeslagen in `$A` .</span><span class="sxs-lookup"><span data-stu-id="abf68-121">The second command uses `Format-List` to format information about objects stored in `$A`.</span></span> <span data-ttu-id="abf68-122">Met deze opdracht wordt de para meter **input object** gebruikt om de variabele door te geven aan `Format-List` , waarna de opgemaakte uitvoer wordt verzonden naar de standaard uitvoer-cmdlet voor weer gave.</span><span class="sxs-lookup"><span data-stu-id="abf68-122">This command uses the **InputObject** parameter to pass the variable to `Format-List`, which then sends the formatted output to the default output cmdlet for display.</span></span>

### <span data-ttu-id="abf68-123">Voor beeld 3: proces eigenschappen opmaken op naam</span><span class="sxs-lookup"><span data-stu-id="abf68-123">Example 3: Format process properties by name</span></span>

<span data-ttu-id="abf68-124">Met deze opdracht worden de naam, de basis prioriteit en de prioriteits klasse van elk proces op de computer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-124">This command displays the name, base priority, and priority class of each process on the computer.</span></span>

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

<span data-ttu-id="abf68-125">De cmdlet wordt gebruikt `Get-Process` om een object op te halen dat elk proces vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="abf68-125">It uses the `Get-Process` cmdlet to get an object representing each process.</span></span> <span data-ttu-id="abf68-126">De pijplijn operator (|) geeft de proces objecten door aan de pijp lijn `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="abf68-126">The pipeline operator (|) passes the process objects through the pipeline to `Format-List`.</span></span> <span data-ttu-id="abf68-127">`Format-List` Hiermee worden de processen opgemaakt als een lijst met de opgegeven eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="abf68-127">`Format-List` formats the processes as a list of the specified properties.</span></span> <span data-ttu-id="abf68-128">De naam van de *eigenschaps* parameter is optioneel. u kunt deze weglaten.</span><span class="sxs-lookup"><span data-stu-id="abf68-128">The *Property* parameter name is optional, so you can omit it.</span></span>

### <span data-ttu-id="abf68-129">Voor beeld 4: alle eigenschappen voor een proces opmaken</span><span class="sxs-lookup"><span data-stu-id="abf68-129">Example 4: Format all properties for a process</span></span>

<span data-ttu-id="abf68-130">Met deze opdracht worden alle eigenschappen van het Winlogon-proces weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-130">This command displays all of the properties of the Winlogon process.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="abf68-131">De Get-Process cmdlet wordt gebruikt om een object op te halen dat het Winlogon-proces vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="abf68-131">It uses the Get-Process cmdlet to get an object representing the Winlogon process.</span></span> <span data-ttu-id="abf68-132">De pijplijn operator (|) geeft het Winlogon-proces object door de pijp lijn door `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="abf68-132">The pipeline operator (|) passes the Winlogon process object through the pipeline to `Format-List`.</span></span> <span data-ttu-id="abf68-133">De opdracht gebruikt de para meter *Property* om de eigenschappen op te geven en de \* om alle eigenschappen aan te geven.</span><span class="sxs-lookup"><span data-stu-id="abf68-133">The command uses the *Property* parameter to specify the properties and the \* to indicate all properties.</span></span>
<span data-ttu-id="abf68-134">Omdat de naam van de *eigenschaps* parameter optioneel is, kunt u deze weglaten en de opdracht typen als `Format-List *` .</span><span class="sxs-lookup"><span data-stu-id="abf68-134">Because the name of the *Property* parameter is optional, you can omit it and type the command as `Format-List *`.</span></span> <span data-ttu-id="abf68-135">`Format-List` de resultaten worden automatisch naar de standaard uitvoer-cmdlet verzonden voor weer gave.</span><span class="sxs-lookup"><span data-stu-id="abf68-135">`Format-List` automatically sends the results to the default output cmdlet for display.</span></span>

### <span data-ttu-id="abf68-136">Voor beeld 5: problemen met indelings fouten oplossen</span><span class="sxs-lookup"><span data-stu-id="abf68-136">Example 5: Troubleshooting format errors</span></span>

<span data-ttu-id="abf68-137">In de volgende voor beelden ziet u de resultaten van het toevoegen van de para meters **Display error** of **show error** met een expressie.</span><span class="sxs-lookup"><span data-stu-id="abf68-137">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="abf68-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="abf68-138">PARAMETERS</span></span>

### <span data-ttu-id="abf68-139">-Display error</span><span class="sxs-lookup"><span data-stu-id="abf68-139">-DisplayError</span></span>

<span data-ttu-id="abf68-140">Geeft aan dat met deze cmdlet fouten worden weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="abf68-140">Indicates that this cmdlet displays errors at the command line.</span></span> <span data-ttu-id="abf68-141">Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-List` opdracht en de expressies worden niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-141">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="abf68-142">-Uitbreiden</span><span class="sxs-lookup"><span data-stu-id="abf68-142">-Expand</span></span>

<span data-ttu-id="abf68-143">Hiermee geeft u het opgemaakte verzamelings object op, evenals de objecten in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="abf68-143">Specifies the formatted collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="abf68-144">Deze para meter is ontworpen om objecten op te maken die ondersteuning bieden voor de ICollection-interface (System. Collections).</span><span class="sxs-lookup"><span data-stu-id="abf68-144">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="abf68-145">De standaard waarde is EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="abf68-145">The default value is EnumOnly.</span></span> <span data-ttu-id="abf68-146">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="abf68-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="abf68-147">EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="abf68-147">EnumOnly.</span></span> <span data-ttu-id="abf68-148">Hiermee worden de eigenschappen van de objecten in de verzameling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-148">Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="abf68-149">CoreOnly.</span><span class="sxs-lookup"><span data-stu-id="abf68-149">CoreOnly.</span></span> <span data-ttu-id="abf68-150">Hiermee worden de eigenschappen van het verzamelings object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-150">Displays the properties of the collection object.</span></span>
- <span data-ttu-id="abf68-151">Zowel.</span><span class="sxs-lookup"><span data-stu-id="abf68-151">Both.</span></span> <span data-ttu-id="abf68-152">Hiermee worden de eigenschappen van het verzamelings object en de eigenschappen van objecten in de verzameling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-152">Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abf68-153">-Force</span><span class="sxs-lookup"><span data-stu-id="abf68-153">-Force</span></span>

<span data-ttu-id="abf68-154">Geeft aan dat met deze cmdlet alle fout gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-154">Indicates that this cmdlet displays all of the error information.</span></span> <span data-ttu-id="abf68-155">Gebruik met de para meter **Display error** of **show error** .</span><span class="sxs-lookup"><span data-stu-id="abf68-155">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="abf68-156">Wanneer een fout object naar de fout wordt geschreven of stromen weer geven, wordt standaard slechts een deel van de fout informatie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-156">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="abf68-157">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="abf68-157">-GroupBy</span></span>

<span data-ttu-id="abf68-158">Hiermee geeft u de uitvoer op in groepen op basis van een gedeelde eigenschap of waarde.</span><span class="sxs-lookup"><span data-stu-id="abf68-158">Specifies the output in groups based on a shared property or value.</span></span> <span data-ttu-id="abf68-159">Voer een expressie of een eigenschap van de uitvoer in.</span><span class="sxs-lookup"><span data-stu-id="abf68-159">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="abf68-160">De waarde van de para meter **GroupBy** kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="abf68-160">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="abf68-161">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="abf68-161">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="abf68-162">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="abf68-162">Valid key-value pairs are:</span></span>

- <span data-ttu-id="abf68-163">Naam (of label)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="abf68-163">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="abf68-164">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="abf68-164">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="abf68-165">Tring `<string>`</span><span class="sxs-lookup"><span data-stu-id="abf68-165">FormatString - `<string>`</span></span>

<span data-ttu-id="abf68-166">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="abf68-166">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="abf68-167">-Input object</span><span class="sxs-lookup"><span data-stu-id="abf68-167">-InputObject</span></span>

<span data-ttu-id="abf68-168">Geeft aan welke objecten moeten worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="abf68-168">Specifies the objects to be formatted.</span></span> <span data-ttu-id="abf68-169">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="abf68-169">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="abf68-170">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="abf68-170">-Property</span></span>

<span data-ttu-id="abf68-171">Hiermee geeft u de object eigenschappen op die in de weer gave worden weer gegeven en de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-171">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="abf68-172">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="abf68-172">Wildcards are permitted.</span></span>

<span data-ttu-id="abf68-173">Als u deze para meter weglaat, zijn de eigenschappen die worden weer gegeven in de weer gave afhankelijk van het object dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-173">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="abf68-174">De parameter naam ' Property ' is optioneel.</span><span class="sxs-lookup"><span data-stu-id="abf68-174">The parameter name "Property" is optional.</span></span> <span data-ttu-id="abf68-175">U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="abf68-175">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="abf68-176">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="abf68-176">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="abf68-177">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="abf68-177">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="abf68-178">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="abf68-178">Valid key-value pairs are:</span></span>

- <span data-ttu-id="abf68-179">Naam (of label)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="abf68-179">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="abf68-180">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="abf68-180">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="abf68-181">Tring `<string>`</span><span class="sxs-lookup"><span data-stu-id="abf68-181">FormatString - `<string>`</span></span>

<span data-ttu-id="abf68-182">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="abf68-182">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="abf68-183">-Show error</span><span class="sxs-lookup"><span data-stu-id="abf68-183">-ShowError</span></span>

<span data-ttu-id="abf68-184">Geeft aan dat de cmdlet fouten verzendt via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="abf68-184">Indicates that the cmdlet sends errors through the pipeline.</span></span> <span data-ttu-id="abf68-185">Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-List` opdracht en de expressies worden niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-185">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="abf68-186">-Weer geven</span><span class="sxs-lookup"><span data-stu-id="abf68-186">-View</span></span>

<span data-ttu-id="abf68-187">Geeft de naam van een alternatieve lijst indeling of weer gave aan.</span><span class="sxs-lookup"><span data-stu-id="abf68-187">Specifies the name of an alternate list format or view.</span></span> <span data-ttu-id="abf68-188">U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="abf68-188">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="abf68-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="abf68-189">CommonParameters</span></span>

<span data-ttu-id="abf68-190">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="abf68-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="abf68-191">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="abf68-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="abf68-192">INVOER</span><span class="sxs-lookup"><span data-stu-id="abf68-192">INPUTS</span></span>

### <span data-ttu-id="abf68-193">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="abf68-193">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="abf68-194">U kunt elk object door sluizen naar `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="abf68-194">You can pipe any object to `Format-List`.</span></span>

## <span data-ttu-id="abf68-195">UITVOER</span><span class="sxs-lookup"><span data-stu-id="abf68-195">OUTPUTS</span></span>

### <span data-ttu-id="abf68-196">Micro soft. Power shell. commands. internal. Format</span><span class="sxs-lookup"><span data-stu-id="abf68-196">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="abf68-197">`Format-List` retourneert de indelings objecten die de lijst vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="abf68-197">`Format-List` returns the format objects that represent the list.</span></span>

## <span data-ttu-id="abf68-198">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="abf68-198">NOTES</span></span>

<span data-ttu-id="abf68-199">U kunt ook verwijzen naar Format-List door de ingebouwde alias, FL.</span><span class="sxs-lookup"><span data-stu-id="abf68-199">You can also refer to Format-List by its built-in alias, FL.</span></span> <span data-ttu-id="abf68-200">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="abf68-200">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="abf68-201">De indelings-cmdlets, zoals `Format-List` , ordenen van de gegevens die worden weer gegeven, maar niet weer geven.</span><span class="sxs-lookup"><span data-stu-id="abf68-201">The format cmdlets, such as `Format-List`, arrange the data to be displayed but do not display it.</span></span>
<span data-ttu-id="abf68-202">De gegevens worden weer gegeven in de uitvoer functies van Power shell en door de cmdlets die de out-verb (de out-cmdlets) bevatten, zoals `Out-Host` of `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="abf68-202">The data is displayed by the output features of PowerShell and by the cmdlets that contain the Out verb (the Out cmdlets), such as `Out-Host` or `Out-File`.</span></span>

<span data-ttu-id="abf68-203">Als u geen indelings-cmdlet gebruikt, past Power shell deze standaard indeling toe voor elk object dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-203">If you do not use a format cmdlet, PowerShell applies that default format for each object that it displays.</span></span>

<span data-ttu-id="abf68-204">De para meter **GroupBy** gaat ervan uit dat de objecten zijn gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="abf68-204">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="abf68-205">Gebruik Sort-Object voordat `Format-List` u de objecten groepeert.</span><span class="sxs-lookup"><span data-stu-id="abf68-205">Use Sort-Object before using `Format-List` to group the objects.</span></span>

<span data-ttu-id="abf68-206">Met de para meter **weer geven** kunt u een alternatieve notatie voor de tabel opgeven.</span><span class="sxs-lookup"><span data-stu-id="abf68-206">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="abf68-207">U kunt de weer gaven gebruiken die zijn gedefinieerd in de `*.format.PS1XML` bestanden in de Power shell-map, maar u kunt ook uw eigen weer gaven maken in nieuwe PS1XML-bestanden en de cmdlet Update-FormatData gebruiken om deze op te geven in Power shell.</span><span class="sxs-lookup"><span data-stu-id="abf68-207">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory, or you can create your own views in new PS1XML files and use the Update-FormatData cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="abf68-208">De alternatieve weer gave voor de **weer gave** -para meter moet de lijst indeling gebruiken, anders mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="abf68-208">The alternate view for the **View** parameter must use the list format, otherwise, the command fails.</span></span> <span data-ttu-id="abf68-209">Als de weer gave alternatieve een tabel is, gebruikt u `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="abf68-209">If the alternate view is a table, use `Format-Table`.</span></span> <span data-ttu-id="abf68-210">Als de alternatieve weer gave geen lijst of tabel is, gebruikt u `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="abf68-210">If the alternate view is not a list or a table, use `Format-Custom`.</span></span>

## <span data-ttu-id="abf68-211">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="abf68-211">RELATED LINKS</span></span>

[<span data-ttu-id="abf68-212">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="abf68-212">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="abf68-213">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="abf68-213">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="abf68-214">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="abf68-214">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="abf68-215">Format-Table</span><span class="sxs-lookup"><span data-stu-id="abf68-215">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="abf68-216">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="abf68-216">Format-Wide</span></span>](Format-Wide.md)
