---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: df41ccf696e39d0bd6c90c118bd715ab83934cf2
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913329"
---
# <span data-ttu-id="9f59b-102">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="9f59b-102">ConvertTo-Csv</span></span>

## <span data-ttu-id="9f59b-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9f59b-103">SYNOPSIS</span></span>
<span data-ttu-id="9f59b-104">Hiermee converteert u .NET-objecten naar een reeks teken reeksen met tekens gescheiden waarden (CSV).</span><span class="sxs-lookup"><span data-stu-id="9f59b-104">Converts .NET objects into a series of character-separated value (CSV) strings.</span></span>

## <span data-ttu-id="9f59b-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9f59b-105">SYNTAX</span></span>

### <span data-ttu-id="9f59b-106">Scheidings teken (standaard)</span><span class="sxs-lookup"><span data-stu-id="9f59b-106">Delimiter (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

### <span data-ttu-id="9f59b-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="9f59b-107">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

## <span data-ttu-id="9f59b-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9f59b-108">DESCRIPTION</span></span>

<span data-ttu-id="9f59b-109">De `ConvertTo-CSV` cmdlet retourneert een reeks teken reeksen met door komma's gescheiden waarden (CSV) die de objecten vertegenwoordigen die u verzendt.</span><span class="sxs-lookup"><span data-stu-id="9f59b-109">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="9f59b-110">U kunt de cmdlet vervolgens gebruiken `ConvertFrom-Csv` om objecten opnieuw te maken op basis van de CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="9f59b-110">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="9f59b-111">De objecten die zijn geconverteerd van CSV zijn teken reeks waarden van de oorspronkelijke objecten die eigenschaps waarden en geen methoden bevatten.</span><span class="sxs-lookup"><span data-stu-id="9f59b-111">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="9f59b-112">U kunt de `Export-Csv` cmdlet gebruiken om objecten te converteren naar CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="9f59b-112">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="9f59b-113">`Export-CSV` is vergelijkbaar met `ConvertTo-CSV` , behalve dat de CSV-teken reeksen worden opgeslagen in een bestand.</span><span class="sxs-lookup"><span data-stu-id="9f59b-113">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="9f59b-114">De `ConvertTo-CSV` cmdlet bevat para meters om een ander scheidings teken dan een komma op te geven of gebruik de huidige cultuur als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="9f59b-114">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="9f59b-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9f59b-115">EXAMPLES</span></span>

### <span data-ttu-id="9f59b-116">Voor beeld 1: een object converteren naar CSV</span><span class="sxs-lookup"><span data-stu-id="9f59b-116">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="9f59b-117">In dit voor beeld wordt een **proces** object geconverteerd naar een CSV-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="9f59b-117">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

<span data-ttu-id="9f59b-118">De `Get-Process` cmdlet haalt het **proces** object op en gebruikt de para meter **name** om het Power Shell-proces op te geven.</span><span class="sxs-lookup"><span data-stu-id="9f59b-118">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="9f59b-119">Het proces object wordt via de pijp lijn naar de `ConvertTo-CSV` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="9f59b-119">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="9f59b-120">De `ConvertTo-CSV` cmdlet converteert het object naar CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="9f59b-120">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="9f59b-121">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="9f59b-121">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="9f59b-122">Voor beeld 2: een DateTime-object converteren naar CSV</span><span class="sxs-lookup"><span data-stu-id="9f59b-122">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="9f59b-123">In dit voor beeld wordt een **DateTime** -object geconverteerd naar een CSV-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="9f59b-123">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="9f59b-124">De `Get-Date` cmdlet haalt het **DateTime** -object op en slaat het op in de `$Date` variabele.</span><span class="sxs-lookup"><span data-stu-id="9f59b-124">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="9f59b-125">`ConvertTo-Csv`Met de cmdlet wordt het **DateTime** -object geconverteerd naar teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="9f59b-125">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="9f59b-126">De para meter **input object** maakt gebruik van het **DateTime** -object dat is opgeslagen in de `$Date` variabele.</span><span class="sxs-lookup"><span data-stu-id="9f59b-126">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="9f59b-127">De **scheidings** parameter geeft een punt komma om de teken reeks waarden te scheiden.</span><span class="sxs-lookup"><span data-stu-id="9f59b-127">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="9f59b-128">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="9f59b-128">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="9f59b-129">Voor beeld 3: het Power shell-gebeurtenis logboek converteren naar CSV</span><span class="sxs-lookup"><span data-stu-id="9f59b-129">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="9f59b-130">In dit voor beeld wordt het Windows-gebeurtenis logboek voor Power shell geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="9f59b-130">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

<span data-ttu-id="9f59b-131">De `Get-Culture` cmdlet maakt gebruik van de geneste eigenschappen **Eigenschappen** en **ListSeparator** en geeft het standaard lijst scheidings teken van de huidige cultuur weer.</span><span class="sxs-lookup"><span data-stu-id="9f59b-131">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="9f59b-132">De `Get-WinEvent` cmdlet haalt de gebeurtenis logboek objecten op en gebruikt de para meter **LogName** om de naam van het logboek bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="9f59b-132">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="9f59b-133">De gebeurtenis logboek objecten worden naar de-cmdlet verzonden via de pijp lijn `ConvertTo-Csv` .</span><span class="sxs-lookup"><span data-stu-id="9f59b-133">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="9f59b-134">`ConvertTo-Csv`Met de cmdlet worden gebeurtenis logboek objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="9f59b-134">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="9f59b-135">De para meter **UseCulture** gebruikt het standaard lijst scheidings teken van de huidige cultuur als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="9f59b-135">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="9f59b-136">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="9f59b-136">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="9f59b-137">Voor beeld 4: converteren naar CSV met aanhalings tekens rond twee kolommen</span><span class="sxs-lookup"><span data-stu-id="9f59b-137">Example 4: Convert to CSV with quotes around two columns</span></span>

<span data-ttu-id="9f59b-138">In dit voor beeld wordt een **DateTime** -object geconverteerd naar een CSV-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="9f59b-138">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -QuoteFields "DateTime","Date"
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="9f59b-139">Voor beeld 4: Converteer naar CSV met alleen aanhalings tekens als dat nodig is</span><span class="sxs-lookup"><span data-stu-id="9f59b-139">Example 4: Convert to CSV with quotes only when needed</span></span>

<span data-ttu-id="9f59b-140">In dit voor beeld wordt een **DateTime** -object geconverteerd naar een CSV-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="9f59b-140">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -UseQuotes AsNeeded
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="9f59b-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9f59b-141">PARAMETERS</span></span>

### <span data-ttu-id="9f59b-142">-Scheidings teken</span><span class="sxs-lookup"><span data-stu-id="9f59b-142">-Delimiter</span></span>

<span data-ttu-id="9f59b-143">Hiermee geeft u het scheidings teken voor het scheiden van de eigenschaps waarden in CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="9f59b-143">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="9f59b-144">De standaard waarde is een komma ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="9f59b-144">The default is a comma (`,`).</span></span> <span data-ttu-id="9f59b-145">Voer een teken in, bijvoorbeeld een dubbele punt ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="9f59b-145">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="9f59b-146">Als u een punt komma () wilt opgeven, `;` plaatst u deze tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="9f59b-146">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f59b-147">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="9f59b-147">-IncludeTypeInformation</span></span>

<span data-ttu-id="9f59b-148">Als deze para meter wordt gebruikt, bevat de eerste regel van de uitvoer **#TYPE** gevolgd door de volledig gekwalificeerde naam van het object type.</span><span class="sxs-lookup"><span data-stu-id="9f59b-148">When this parameter is used the first line of the output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="9f59b-149">Bijvoorbeeld **#TYPE System. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="9f59b-149">For example, **#TYPE System.Diagnostics.Process**.</span></span>

<span data-ttu-id="9f59b-150">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="9f59b-150">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f59b-151">-Input object</span><span class="sxs-lookup"><span data-stu-id="9f59b-151">-InputObject</span></span>

<span data-ttu-id="9f59b-152">Hiermee geeft u de objecten die worden geconverteerd naar CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="9f59b-152">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="9f59b-153">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9f59b-153">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="9f59b-154">U kunt ook objecten pipeen naar `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="9f59b-154">You can also pipe objects to `ConvertTo-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9f59b-155">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="9f59b-155">-NoTypeInformation</span></span>

<span data-ttu-id="9f59b-156">Hiermee verwijdert u de **#TYPE** informatie uit de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="9f59b-156">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="9f59b-157">Deze para meter werd de standaard waarde in Power shell 6,0 en is opgenomen voor achterwaartse compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="9f59b-157">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f59b-158">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="9f59b-158">-UseCulture</span></span>

<span data-ttu-id="9f59b-159">Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="9f59b-159">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="9f59b-160">Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="9f59b-160">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f59b-161">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="9f59b-161">-QuoteFields</span></span>

<span data-ttu-id="9f59b-162">Hiermee geeft u de namen van de kolommen die moeten worden genoteerd.</span><span class="sxs-lookup"><span data-stu-id="9f59b-162">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="9f59b-163">Als deze para meter wordt gebruikt, worden alleen de opgegeven kolommen genoteerd.</span><span class="sxs-lookup"><span data-stu-id="9f59b-163">When this parameter is used only the specified columns are quoted.</span></span> <span data-ttu-id="9f59b-164">Deze para meter is toegevoegd in Power shell 7,0.</span><span class="sxs-lookup"><span data-stu-id="9f59b-164">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f59b-165">-UseQuotes</span><span class="sxs-lookup"><span data-stu-id="9f59b-165">-UseQuotes</span></span>

<span data-ttu-id="9f59b-166">Hiermee geeft u op wanneer aanhalings tekens worden gebruikt in de CSV-bestanden.</span><span class="sxs-lookup"><span data-stu-id="9f59b-166">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="9f59b-167">Mogelijke waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="9f59b-167">Possible values are:</span></span>

- <span data-ttu-id="9f59b-168">Nooit: niets citeren</span><span class="sxs-lookup"><span data-stu-id="9f59b-168">Never - don't quote anything</span></span>
- <span data-ttu-id="9f59b-169">Altijd: alle citaten (standaard gedrag)</span><span class="sxs-lookup"><span data-stu-id="9f59b-169">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="9f59b-170">Alleen-AsNeeded die een scheidings teken bevatten</span><span class="sxs-lookup"><span data-stu-id="9f59b-170">AsNeeded - only quote fields that contain a delimiter character</span></span>

<span data-ttu-id="9f59b-171">Deze para meter is toegevoegd in Power shell 7,0.</span><span class="sxs-lookup"><span data-stu-id="9f59b-171">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f59b-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9f59b-172">CommonParameters</span></span>

<span data-ttu-id="9f59b-173">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9f59b-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9f59b-174">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9f59b-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9f59b-175">INVOER</span><span class="sxs-lookup"><span data-stu-id="9f59b-175">INPUTS</span></span>

### <span data-ttu-id="9f59b-176">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="9f59b-176">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9f59b-177">U kunt elk object dat een adapter met een Extended type systeem (ETS) bevat, aan `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="9f59b-177">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="9f59b-178">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9f59b-178">OUTPUTS</span></span>

### <span data-ttu-id="9f59b-179">System. String</span><span class="sxs-lookup"><span data-stu-id="9f59b-179">System.String</span></span>

<span data-ttu-id="9f59b-180">De CSV-uitvoer wordt geretourneerd als een verzameling teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="9f59b-180">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="9f59b-181">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9f59b-181">NOTES</span></span>

<span data-ttu-id="9f59b-182">In CSV-indeling wordt elk object vertegenwoordigd door een door komma's gescheiden lijst van de eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="9f59b-182">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="9f59b-183">De eigenschaps waarden worden geconverteerd naar teken reeksen met de methode **toString ()** van het object.</span><span class="sxs-lookup"><span data-stu-id="9f59b-183">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="9f59b-184">De teken reeksen worden vertegenwoordigd door de naam van de eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="9f59b-184">The strings are represented by the property value name.</span></span> <span data-ttu-id="9f59b-185">`ConvertTo-CSV` exporteert de methoden van het object niet.</span><span class="sxs-lookup"><span data-stu-id="9f59b-185">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="9f59b-186">De CSV-teken reeksen worden als volgt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="9f59b-186">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="9f59b-187">Als **IncludeTypeInformation** wordt gebruikt, bestaat de eerste teken reeks uit **#TYPE** gevolgd door de volledig gekwalificeerde naam van het object type.</span><span class="sxs-lookup"><span data-stu-id="9f59b-187">If **IncludeTypeInformation** is used, the first string consists of **#TYPE** followed by the object type's fully qualified name.</span></span> <span data-ttu-id="9f59b-188">Bijvoorbeeld **#TYPE System. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="9f59b-188">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="9f59b-189">Als **IncludeTypeInformation** niet wordt gebruikt, bevat de eerste teken reeks de kolom koppen.</span><span class="sxs-lookup"><span data-stu-id="9f59b-189">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="9f59b-190">De headers bevatten de eigenschaps namen van het eerste object als een door komma's gescheiden lijst.</span><span class="sxs-lookup"><span data-stu-id="9f59b-190">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="9f59b-191">De resterende teken reeksen bevatten door komma's gescheiden lijsten van de eigenschaps waarden van elk object.</span><span class="sxs-lookup"><span data-stu-id="9f59b-191">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="9f59b-192">Vanaf Power shell 6,0 is het standaard gedrag van de `ConvertTo-CSV` **#TYPE** informatie in het CSV-bestand en **NoTypeInformation** wordt geïmpliceerd.</span><span class="sxs-lookup"><span data-stu-id="9f59b-192">Beginning with PowerShell 6.0 the default behavior of `ConvertTo-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="9f59b-193">**IncludeTypeInformation** kan worden gebruikt om de **#TYPE** informatie op te neemt en het standaard gedrag van `ConvertTo-CSV` vóór Power shell 6,0 te emuleren.</span><span class="sxs-lookup"><span data-stu-id="9f59b-193">**IncludeTypeInformation** can be used to include the **#TYPE** information and emulate the default behavior of `ConvertTo-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="9f59b-194">Wanneer u meerdere objecten verzendt naar `ConvertTo-CSV` , worden `ConvertTo-CSV` de teken reeksen door gesorteerd op basis van de eigenschappen van het eerste object dat u verzendt.</span><span class="sxs-lookup"><span data-stu-id="9f59b-194">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="9f59b-195">Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de eigenschaps waarde van dat object null, zoals wordt weer gegeven in twee opeenvolgende komma's.</span><span class="sxs-lookup"><span data-stu-id="9f59b-195">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="9f59b-196">Als de resterende objecten extra eigenschappen hebben, worden die eigenschaps waarden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="9f59b-196">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="9f59b-197">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9f59b-197">RELATED LINKS</span></span>

[<span data-ttu-id="9f59b-198">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="9f59b-198">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="9f59b-199">Exporteren-CSV</span><span class="sxs-lookup"><span data-stu-id="9f59b-199">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="9f59b-200">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="9f59b-200">Import-Csv</span></span>](Import-Csv.md)
