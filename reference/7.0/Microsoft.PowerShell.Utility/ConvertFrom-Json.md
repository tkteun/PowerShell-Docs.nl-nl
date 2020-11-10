---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: e3a40fcda5d3fa0acad0b8b435a7b369e1e1ae50
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389654"
---
# <span data-ttu-id="6ffc7-103">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="6ffc7-103">ConvertFrom-Json</span></span>

## <span data-ttu-id="6ffc7-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6ffc7-104">SYNOPSIS</span></span>
<span data-ttu-id="6ffc7-105">Converteert een teken reeks in JSON-indeling naar een aangepast object of een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-105">Converts a JSON-formatted string to a custom object or a hash table.</span></span>

## <span data-ttu-id="6ffc7-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6ffc7-106">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="6ffc7-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6ffc7-107">DESCRIPTION</span></span>

<span data-ttu-id="6ffc7-108">Met de `ConvertFrom-Json` cmdlet wordt een met JavaScript object Notation (JSON) opgemaakte teken reeks geconverteerd naar een aangepast **PSCustomObject** -object met een eigenschap voor elk veld in de JSON-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-108">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="6ffc7-109">JSON wordt doorgaans door websites gebruikt om een tekstuele representatie van objecten te bieden.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-109">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="6ffc7-110">De JSON-standaard verhindert niet het gebruik dat is verboden met een **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-110">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject**.</span></span> <span data-ttu-id="6ffc7-111">Als de JSON-teken reeks bijvoorbeeld dubbele sleutels bevat, wordt alleen de laatste sleutel gebruikt door deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-111">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="6ffc7-112">Zie andere voor beelden hieronder.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-112">See other examples below.</span></span>

<span data-ttu-id="6ffc7-113">Als u een JSON-teken reeks wilt genereren vanuit een wille keurig object, gebruikt u de `ConvertTo-Json` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-113">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="6ffc7-114">Deze cmdlet is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="6ffc7-115">Vanaf Power shell 6 ondersteunt deze cmdlet JSON met opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-115">Beginning with PowerShell 6, this cmdlet supports JSON with comments.</span></span> <span data-ttu-id="6ffc7-116">Geaccepteerde opmerkingen worden gestart met twee slashes ( `//` ).</span><span class="sxs-lookup"><span data-stu-id="6ffc7-116">Accepted comments are started with two forward slashes (`//`).</span></span> <span data-ttu-id="6ffc7-117">De opmerking wordt niet weer gegeven in de gegevens en kan in het bestand worden geschreven zonder de gegevens te beschadigen of er wordt een fout opgetreden in de Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-117">The comment will not be represented in the data and can be written in the file without corrupting the data or throwing an error as it did in PowerShell 5.1.</span></span>

## <span data-ttu-id="6ffc7-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6ffc7-118">EXAMPLES</span></span>

### <span data-ttu-id="6ffc7-119">Voor beeld 1: een DateTime-object converteren naar een JSON-object</span><span class="sxs-lookup"><span data-stu-id="6ffc7-119">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="6ffc7-120">Met deze opdracht worden de- `ConvertTo-Json` en- `ConvertFrom-Json` cmdlets gebruikt om een **DateTime** -object van de cmdlet om te zetten naar een JSON- `Get-Date` object en vervolgens naar een **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-120">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject**.</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

<span data-ttu-id="6ffc7-121">In het voor beeld wordt de `Select-Object` cmdlet gebruikt om alle eigenschappen van het **DateTime** -object op te halen.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-121">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="6ffc7-122">De cmdlet wordt gebruikt `ConvertTo-Json` om het **DateTime** -object te converteren naar een teken reeks die is OPGEMAAKT als een JSON-object en de `ConvertFrom-Json` cmdlet om de teken reeks in JSON-indeling te converteren naar een **PSCustomObject** -object.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-122">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="6ffc7-123">Voor beeld 2: JSON-teken reeksen ophalen van een webservice en deze converteren naar Power shell-objecten</span><span class="sxs-lookup"><span data-stu-id="6ffc7-123">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="6ffc7-124">Met deze opdracht wordt de `Invoke-WebRequest` cmdlet gebruikt om JSON-teken reeksen op te halen uit een webservice en wordt vervolgens de `ConvertFrom-Json` cmdlet gebruikt om JSON-inhoud te converteren naar objecten die kunnen worden beheerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-124">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="6ffc7-125">U kunt ook de `Invoke-RestMethod` cmdlet gebruiken, waarmee JSON-inhoud automatisch naar objecten wordt geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-125">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="6ffc7-126">Voor beeld 3: een JSON-teken reeks converteren naar een aangepast object</span><span class="sxs-lookup"><span data-stu-id="6ffc7-126">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="6ffc7-127">In dit voor beeld ziet u hoe u de `ConvertFrom-Json` cmdlet gebruikt om een JSON-bestand te converteren naar een aangepast Power shell-object.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-127">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="6ffc7-128">De opdracht gebruikt Get-Content cmdlet om de teken reeksen in een JSON-bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-128">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="6ffc7-129">Vervolgens wordt de pijplijn operator gebruikt voor het verzenden van de gescheiden teken reeks naar de `ConvertFrom-Json` cmdlet, die deze converteert naar een aangepast object.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-129">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

### <span data-ttu-id="6ffc7-130">Voor beeld 4: een JSON-teken reeks converteren naar een hash-tabel</span><span class="sxs-lookup"><span data-stu-id="6ffc7-130">Example 4: Convert a JSON string to a hash table</span></span>

<span data-ttu-id="6ffc7-131">Met deze opdracht wordt een voor beeld weer gegeven waarin de `-AsHashtable` Switch beperkingen van de opdracht kan overwinnen.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-131">This command shows an example where the `-AsHashtable` switch can overcome limitations of the command.</span></span>

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

<span data-ttu-id="6ffc7-132">De JSON-teken reeks bevat twee sleutel waardeparen met sleutels die alleen in hoofdletter gebruik verschillen.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-132">The JSON string contains two key value pairs with keys that differ only in casing.</span></span> <span data-ttu-id="6ffc7-133">Zonder de schakel optie zou de opdracht een fout hebben gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-133">Without the switch, the command would have thrown an error.</span></span>

### <span data-ttu-id="6ffc7-134">Voor beeld 5: een matrix met één element retour ronding</span><span class="sxs-lookup"><span data-stu-id="6ffc7-134">Example 5: Round-trip a single element array</span></span>

<span data-ttu-id="6ffc7-135">Met deze opdracht wordt een voor beeld weer gegeven waarin de `-NoEnumerate` Schakel optie wordt gebruikt voor het afronden van een JSON-matrix met één element.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-135">This command shows an example where the `-NoEnumerate` switch is used to round-trip a single element JSON array.</span></span>

```powershell
Write-Output "With -NoEnumerate: $('[1]' | ConvertFrom-Json -NoEnumerate | ConvertTo-Json -Compress)"
Write-Output "Without -NoEnumerate: $('[1]' | ConvertFrom-Json | ConvertTo-Json -Compress)"
```

```Output
With -NoEnumerate: [1]
Without -NoEnumerate: 1
```

<span data-ttu-id="6ffc7-136">De JSON-teken reeks bevat een matrix met één element.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-136">The JSON string contains an array with a single element.</span></span> <span data-ttu-id="6ffc7-137">Zonder de switch, het converteren van de JSON naar een PSObject en het opnieuw converteren met de `ConvertTo-Json` opdracht resulteert in één geheel getal.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-137">Without the switch, converting the JSON to a PSObject and then converting it back with the `ConvertTo-Json` command results in a single integer.</span></span>

## <span data-ttu-id="6ffc7-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6ffc7-138">PARAMETERS</span></span>

### <span data-ttu-id="6ffc7-139">-AsHashtable</span><span class="sxs-lookup"><span data-stu-id="6ffc7-139">-AsHashtable</span></span>

<span data-ttu-id="6ffc7-140">Converteert de JSON naar een object hash table.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-140">Converts the JSON to a hash table object.</span></span> <span data-ttu-id="6ffc7-141">Deze switch is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-141">This switch was introduced in PowerShell 6.0.</span></span> <span data-ttu-id="6ffc7-142">Er zijn verschillende scenario's waarbij een aantal beperkingen van de cmdlet kan worden Weggen Omen `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="6ffc7-142">There are several scenarios where it can overcome some limitations of the `ConvertFrom-Json` cmdlet.</span></span>

- <span data-ttu-id="6ffc7-143">Als de JSON een lijst bevat met sleutels die alleen in hoofdletter verschillen.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-143">If the JSON contains a list with keys that only differ in casing.</span></span> <span data-ttu-id="6ffc7-144">Zonder de switch worden deze sleutels gezien als identieke sleutels, waardoor alleen de laatste wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-144">Without the switch, those keys would be seen as identical keys and therefore only the last one would get used.</span></span>
- <span data-ttu-id="6ffc7-145">Als de JSON een sleutel bevat die een lege teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-145">If the JSON contains a key that is an empty string.</span></span> <span data-ttu-id="6ffc7-146">Zonder de switch treedt er een fout op omdat de cmdlet `PSCustomObject` geen toestaat, maar een hash-tabel wel.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-146">Without the switch, the cmdlet would throw an error since a `PSCustomObject` does not allow for that but a hash table does.</span></span> <span data-ttu-id="6ffc7-147">Een voor beeld van een voorbeeld toepassing waarbij dit kan gebeuren, zijn `project.lock.json` bestanden.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-147">An example use case where this can occurs are `project.lock.json` files.</span></span>
- <span data-ttu-id="6ffc7-148">Hash-tabellen kunnen sneller worden verwerkt voor bepaalde gegevens structuren.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-148">Hash tables can be processed faster for certain data structures.</span></span>

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

### <span data-ttu-id="6ffc7-149">-Diepte</span><span class="sxs-lookup"><span data-stu-id="6ffc7-149">-Depth</span></span>

<span data-ttu-id="6ffc7-150">Hiermee wordt de maximale diepte opgehaald of ingesteld die de JSON-invoer mag hebben.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-150">Gets or sets the maximum depth the JSON input is allowed to have.</span></span> <span data-ttu-id="6ffc7-151">Standaard is dit 1024.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-151">By default, it is 1024.</span></span>

<span data-ttu-id="6ffc7-152">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-152">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="6ffc7-153">-Input object</span><span class="sxs-lookup"><span data-stu-id="6ffc7-153">-InputObject</span></span>

<span data-ttu-id="6ffc7-154">Hiermee geeft u de JSON-teken reeksen op die moeten worden geconverteerd naar JSON-objecten.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-154">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="6ffc7-155">Voer een variabele in die de teken reeks bevat, of typ een opdracht of expressie die de teken reeks ophaalt.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-155">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="6ffc7-156">U kunt ook een teken reeks aan een pipe door geven `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="6ffc7-156">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="6ffc7-157">De para meter **input object** is vereist, maar de waarde kan een lege teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-157">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="6ffc7-158">Wanneer het invoer object een lege teken reeks is, wordt `ConvertFrom-Json` er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-158">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="6ffc7-159">De **input object** -waarde kan niet zijn `$null` .</span><span class="sxs-lookup"><span data-stu-id="6ffc7-159">The **InputObject** value cannot be `$null`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6ffc7-160">-Opsomming</span><span class="sxs-lookup"><span data-stu-id="6ffc7-160">-NoEnumerate</span></span>

<span data-ttu-id="6ffc7-161">Hiermee geeft u op dat de uitvoer niet wordt opgesomd.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-161">Specifies that output is not enumerated.</span></span>

<span data-ttu-id="6ffc7-162">Als deze para meter wordt ingesteld, worden matrices als één object verzonden, in plaats van dat elk element afzonderlijk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-162">Setting this parameter causes arrays to be sent as a single object instead of sending every element separately.</span></span> <span data-ttu-id="6ffc7-163">Dit garandeert dat JSON kan worden afgerond via `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="6ffc7-163">This guarantees that JSON can be round-tripped via `ConvertTo-Json`.</span></span>

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

### <span data-ttu-id="6ffc7-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6ffc7-164">CommonParameters</span></span>

<span data-ttu-id="6ffc7-165">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6ffc7-166">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6ffc7-167">INVOER</span><span class="sxs-lookup"><span data-stu-id="6ffc7-167">INPUTS</span></span>

### <span data-ttu-id="6ffc7-168">System. String</span><span class="sxs-lookup"><span data-stu-id="6ffc7-168">System.String</span></span>

<span data-ttu-id="6ffc7-169">U kunt een JSON-teken reeks door sluizen naar `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="6ffc7-169">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="6ffc7-170">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6ffc7-170">OUTPUTS</span></span>

### <span data-ttu-id="6ffc7-171">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="6ffc7-171">PSCustomObject</span></span>

### <span data-ttu-id="6ffc7-172">System. Collections. hashtabel</span><span class="sxs-lookup"><span data-stu-id="6ffc7-172">System.Collections.Hashtable</span></span>

## <span data-ttu-id="6ffc7-173">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6ffc7-173">NOTES</span></span>

<span data-ttu-id="6ffc7-174">Deze cmdlet wordt geïmplementeerd met behulp van [newton soft JSON.net](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="6ffc7-174">This cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

<span data-ttu-id="6ffc7-175">Vanaf Power shell 6 `ConvertTo-Json` probeert teken reeksen die zijn opgemaakt als tijds tempels te converteren naar **DateTime** -waarden.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-175">Beginning in PowerShell 6, `ConvertTo-Json` attempts to convert strings formatted as timestamps to **DateTime** values.</span></span> <span data-ttu-id="6ffc7-176">De geconverteerde waarde is `[datetime]` als volgt een exemplaar waarvan een `Kind` eigenschap is ingesteld:</span><span class="sxs-lookup"><span data-stu-id="6ffc7-176">The converted value is a `[datetime]` instance with a `Kind` property set as follows:</span></span>

- <span data-ttu-id="6ffc7-177">`Unspecified`Als de invoer teken reeks geen tijd zone-informatie bevat.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-177">`Unspecified`, if there is no time zone information in the input string.</span></span>
- <span data-ttu-id="6ffc7-178">`Utc`Als de tijdzone gegevens een navolgende zijn `Z` .</span><span class="sxs-lookup"><span data-stu-id="6ffc7-178">`Utc`, if the time zone information is a trailing `Z`.</span></span>
- <span data-ttu-id="6ffc7-179">`Local`Als de informatie over de tijd zone wordt gegeven als een afsluitende UTC- _Offset_ , zoals `+02:00` .</span><span class="sxs-lookup"><span data-stu-id="6ffc7-179">`Local`, if the time zone information is given as a trailing UTC _offset_ like `+02:00`.</span></span> <span data-ttu-id="6ffc7-180">De offset wordt correct geconverteerd naar de geconfigureerde tijd zone van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-180">The offset is properly converted to the caller's configured time zone.</span></span> <span data-ttu-id="6ffc7-181">De standaard uitvoer opmaak geeft niet de oorspronkelijke tijd zone-offset aan.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-181">The default output formatting does not indicate the original time zone offset.</span></span>

## <span data-ttu-id="6ffc7-182">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6ffc7-182">RELATED LINKS</span></span>

<span data-ttu-id="6ffc7-183">[Een inleiding tot JavaScript Object Notation (JSON) in Java script en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="6ffc7-183">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="6ffc7-184">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="6ffc7-184">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="6ffc7-185">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="6ffc7-185">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="6ffc7-186">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="6ffc7-186">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
