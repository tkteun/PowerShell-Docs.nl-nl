---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: be590368539f396f0aac694e9565674393543f2c
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913199"
---
# <span data-ttu-id="09b19-102">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="09b19-102">ConvertTo-Csv</span></span>

## <span data-ttu-id="09b19-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="09b19-103">SYNOPSIS</span></span>
<span data-ttu-id="09b19-104">Converteert .NET-objecten naar een reeks teken reeksen met door komma's gescheiden waarden (CSV).</span><span class="sxs-lookup"><span data-stu-id="09b19-104">Converts .NET objects into a series of comma-separated value (CSV) strings.</span></span>

## <span data-ttu-id="09b19-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="09b19-105">SYNTAX</span></span>

### <span data-ttu-id="09b19-106">Scheidings teken (standaard)</span><span class="sxs-lookup"><span data-stu-id="09b19-106">Delimiter (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <psobject> [[-Delimiter] <char>] [-NoTypeInformation]
 [<CommonParameters>]
```

### <span data-ttu-id="09b19-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="09b19-107">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <psobject> [-UseCulture] [-NoTypeInformation] [<CommonParameters>]
```

## <span data-ttu-id="09b19-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="09b19-108">DESCRIPTION</span></span>

<span data-ttu-id="09b19-109">De `ConvertTo-CSV` cmdlet retourneert een reeks teken reeksen met door komma's gescheiden waarden (CSV) die de objecten vertegenwoordigen die u verzendt.</span><span class="sxs-lookup"><span data-stu-id="09b19-109">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="09b19-110">U kunt de cmdlet vervolgens gebruiken `ConvertFrom-Csv` om objecten opnieuw te maken op basis van de CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="09b19-110">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="09b19-111">De objecten die zijn geconverteerd van CSV zijn teken reeks waarden van de oorspronkelijke objecten die eigenschaps waarden en geen methoden bevatten.</span><span class="sxs-lookup"><span data-stu-id="09b19-111">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="09b19-112">U kunt de `Export-Csv` cmdlet gebruiken om objecten te converteren naar CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="09b19-112">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="09b19-113">`Export-CSV` is vergelijkbaar met `ConvertTo-CSV` , behalve dat de CSV-teken reeksen worden opgeslagen in een bestand.</span><span class="sxs-lookup"><span data-stu-id="09b19-113">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="09b19-114">De `ConvertTo-CSV` cmdlet bevat para meters om een ander scheidings teken dan een komma op te geven of gebruik de huidige cultuur als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="09b19-114">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="09b19-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="09b19-115">EXAMPLES</span></span>

### <span data-ttu-id="09b19-116">Voor beeld 1: een object converteren naar CSV</span><span class="sxs-lookup"><span data-stu-id="09b19-116">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="09b19-117">In dit voor beeld wordt een **proces** object geconverteerd naar een CSV-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="09b19-117">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name 'PowerShell' | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"powershell","11","691","2204036739072","175943680","132665344","33312", ...
```

<span data-ttu-id="09b19-118">De `Get-Process` cmdlet haalt het **proces** object op en gebruikt de para meter **name** om het Power Shell-proces op te geven.</span><span class="sxs-lookup"><span data-stu-id="09b19-118">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="09b19-119">Het proces object wordt via de pijp lijn naar de `ConvertTo-CSV` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="09b19-119">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="09b19-120">De `ConvertTo-CSV` cmdlet converteert het object naar CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="09b19-120">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="09b19-121">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="09b19-121">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

### <span data-ttu-id="09b19-122">Voor beeld 2: een DateTime-object converteren naar CSV</span><span class="sxs-lookup"><span data-stu-id="09b19-122">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="09b19-123">In dit voor beeld wordt een **DateTime** -object geconverteerd naar een CSV-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="09b19-123">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="09b19-124">De `Get-Date` cmdlet haalt het **DateTime** -object op en slaat het op in de `$Date` variabele.</span><span class="sxs-lookup"><span data-stu-id="09b19-124">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="09b19-125">`ConvertTo-Csv`Met de cmdlet wordt het **DateTime** -object geconverteerd naar teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="09b19-125">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="09b19-126">De para meter **input object** maakt gebruik van het **DateTime** -object dat is opgeslagen in de `$Date` variabele.</span><span class="sxs-lookup"><span data-stu-id="09b19-126">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="09b19-127">De **scheidings** parameter geeft een punt komma om de teken reeks waarden te scheiden.</span><span class="sxs-lookup"><span data-stu-id="09b19-127">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="09b19-128">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="09b19-128">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

### <span data-ttu-id="09b19-129">Voor beeld 3: het Power shell-gebeurtenis logboek converteren naar CSV</span><span class="sxs-lookup"><span data-stu-id="09b19-129">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="09b19-130">In dit voor beeld wordt het Windows-gebeurtenis logboek voor Power shell geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="09b19-130">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'Windows PowerShell' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error","403",,"0","4","4",,"36028797018963968","46891","PowerShell", ...
```

<span data-ttu-id="09b19-131">De `Get-Culture` cmdlet maakt gebruik van de geneste eigenschappen **Eigenschappen** en **ListSeparator** en geeft het standaard lijst scheidings teken van de huidige cultuur weer.</span><span class="sxs-lookup"><span data-stu-id="09b19-131">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="09b19-132">De `Get-WinEvent` cmdlet haalt de gebeurtenis logboek objecten op en gebruikt de para meter **LogName** om de naam van het logboek bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="09b19-132">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="09b19-133">De gebeurtenis logboek objecten worden naar de-cmdlet verzonden via de pijp lijn `ConvertTo-Csv` .</span><span class="sxs-lookup"><span data-stu-id="09b19-133">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="09b19-134">`ConvertTo-Csv`Met de cmdlet worden gebeurtenis logboek objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="09b19-134">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="09b19-135">De para meter **UseCulture** gebruikt het standaard lijst scheidings teken van de huidige cultuur als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="09b19-135">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="09b19-136">De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="09b19-136">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

## <span data-ttu-id="09b19-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="09b19-137">PARAMETERS</span></span>

### <span data-ttu-id="09b19-138">-Scheidings teken</span><span class="sxs-lookup"><span data-stu-id="09b19-138">-Delimiter</span></span>

<span data-ttu-id="09b19-139">Hiermee geeft u het scheidings teken voor het scheiden van de eigenschaps waarden in CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="09b19-139">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="09b19-140">De standaard waarde is een komma ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="09b19-140">The default is a comma (`,`).</span></span> <span data-ttu-id="09b19-141">Voer een teken in, bijvoorbeeld een dubbele punt ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="09b19-141">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="09b19-142">Als u een punt komma () wilt opgeven, `;` plaatst u deze tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="09b19-142">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

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

### <span data-ttu-id="09b19-143">-Input object</span><span class="sxs-lookup"><span data-stu-id="09b19-143">-InputObject</span></span>

<span data-ttu-id="09b19-144">Hiermee geeft u de objecten die worden geconverteerd naar CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="09b19-144">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="09b19-145">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="09b19-145">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="09b19-146">U kunt ook objecten pipeen naar `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="09b19-146">You can also pipe objects to `ConvertTo-CSV`.</span></span>

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

### <span data-ttu-id="09b19-147">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="09b19-147">-NoTypeInformation</span></span>

<span data-ttu-id="09b19-148">Hiermee verwijdert u de **#TYPE** informatie uit de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="09b19-148">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="09b19-149">Deze para meter werd de standaard waarde in Power shell 6,0 en is opgenomen voor achterwaartse compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="09b19-149">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="09b19-150">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="09b19-150">-UseCulture</span></span>

<span data-ttu-id="09b19-151">Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="09b19-151">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="09b19-152">Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="09b19-152">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="09b19-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="09b19-153">CommonParameters</span></span>

<span data-ttu-id="09b19-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="09b19-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="09b19-155">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="09b19-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="09b19-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="09b19-156">INPUTS</span></span>

### <span data-ttu-id="09b19-157">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="09b19-157">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="09b19-158">U kunt elk object dat een adapter met een Extended type systeem (ETS) bevat, aan `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="09b19-158">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="09b19-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="09b19-159">OUTPUTS</span></span>

### <span data-ttu-id="09b19-160">System. String</span><span class="sxs-lookup"><span data-stu-id="09b19-160">System.String</span></span>

<span data-ttu-id="09b19-161">De CSV-uitvoer wordt geretourneerd als een verzameling teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="09b19-161">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="09b19-162">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="09b19-162">NOTES</span></span>

<span data-ttu-id="09b19-163">In CSV-indeling wordt elk object vertegenwoordigd door een door komma's gescheiden lijst van de eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="09b19-163">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="09b19-164">De eigenschaps waarden worden geconverteerd naar teken reeksen met de methode **toString ()** van het object.</span><span class="sxs-lookup"><span data-stu-id="09b19-164">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="09b19-165">De teken reeksen worden vertegenwoordigd door de naam van de eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="09b19-165">The strings are represented by the property value name.</span></span> <span data-ttu-id="09b19-166">`ConvertTo-CSV` exporteert de methoden van het object niet.</span><span class="sxs-lookup"><span data-stu-id="09b19-166">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="09b19-167">De CSV-teken reeksen worden als volgt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="09b19-167">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="09b19-168">De eerste teken reeks bevat standaard de **#TYPE** informatie header, gevolgd door de volledig gekwalificeerde naam van het object type.</span><span class="sxs-lookup"><span data-stu-id="09b19-168">By default the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span> <span data-ttu-id="09b19-169">Bijvoorbeeld **#TYPE System. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="09b19-169">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="09b19-170">Als **NoTypeInformation** wordt gebruikt, bevat de eerste teken reeks de kolom koppen.</span><span class="sxs-lookup"><span data-stu-id="09b19-170">If **NoTypeInformation** is used the first string includes the column headers.</span></span> <span data-ttu-id="09b19-171">De headers bevatten de eigenschaps namen van het eerste object als een door komma's gescheiden lijst.</span><span class="sxs-lookup"><span data-stu-id="09b19-171">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="09b19-172">De resterende teken reeksen bevatten door komma's gescheiden lijsten van de eigenschaps waarden van elk object.</span><span class="sxs-lookup"><span data-stu-id="09b19-172">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="09b19-173">Wanneer u meerdere objecten verzendt naar `ConvertTo-CSV` , worden `ConvertTo-CSV` de teken reeksen door gesorteerd op basis van de eigenschappen van het eerste object dat u verzendt.</span><span class="sxs-lookup"><span data-stu-id="09b19-173">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="09b19-174">Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de eigenschaps waarde van dat object null, zoals wordt weer gegeven in twee opeenvolgende komma's.</span><span class="sxs-lookup"><span data-stu-id="09b19-174">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="09b19-175">Als de resterende objecten extra eigenschappen hebben, worden die eigenschaps waarden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="09b19-175">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="09b19-176">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="09b19-176">RELATED LINKS</span></span>

[<span data-ttu-id="09b19-177">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="09b19-177">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="09b19-178">Exporteren-CSV</span><span class="sxs-lookup"><span data-stu-id="09b19-178">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="09b19-179">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="09b19-179">Import-Csv</span></span>](Import-Csv.md)
