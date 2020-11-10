---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: acfeae4025b3a32d2a04307609597cf30332d708
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389450"
---
# <span data-ttu-id="73704-103">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="73704-103">ConvertTo-Json</span></span>

## <span data-ttu-id="73704-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="73704-104">SYNOPSIS</span></span>
<span data-ttu-id="73704-105">Converteert een object naar een teken reeks in JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="73704-105">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="73704-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="73704-106">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## <span data-ttu-id="73704-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="73704-107">DESCRIPTION</span></span>

<span data-ttu-id="73704-108">`ConvertTo-Json`Met de cmdlet wordt een .net-object geconverteerd naar een teken reeks in de indeling van de JavaScript object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="73704-108">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="73704-109">De eigenschappen worden geconverteerd naar veld namen, de veld waarden worden geconverteerd naar eigenschaps waarden en de methoden worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="73704-109">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="73704-110">U kunt de cmdlet vervolgens gebruiken `ConvertFrom-Json` om een JSON-indelings teken reeks te converteren naar een JSON-object, dat eenvoudig kan worden beheerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="73704-110">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="73704-111">Veel websites gebruiken JSON in plaats van XML om gegevens te serialiseren voor communicatie tussen servers en web-apps.</span><span class="sxs-lookup"><span data-stu-id="73704-111">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="73704-112">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="73704-112">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="73704-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="73704-113">EXAMPLES</span></span>

### <span data-ttu-id="73704-114">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="73704-114">Example 1</span></span>

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
  "MinSupportedDateTime": "0001-01-01T00:00:00",
  "MaxSupportedDateTime": "9999-12-31T23:59:59.9999999",
  "AlgorithmType": 1,
  "CalendarType": 1,
  "Eras": [
    1
  ],
  "TwoDigitYearMax": 2029,
  "IsReadOnly": true
}
```

<span data-ttu-id="73704-115">Met deze opdracht wordt de `ConvertTo-Json` cmdlet gebruikt om een GregorianCalendar-object te converteren naar een JSON-indelings teken reeks.</span><span class="sxs-lookup"><span data-stu-id="73704-115">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="73704-116">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="73704-116">Example 2</span></span>

```powershell
Get-Date | ConvertTo-Json; Get-Date | ConvertTo-Json -AsArray
```

```Output
{
  "value": "2018-10-12T23:07:18.8450248-05:00",
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 11:07:18 PM"
}
[
  {
    "value": "2018-10-12T23:07:18.8480668-05:00",
    "DisplayHint": 2,
    "DateTime": "October 12, 2018 11:07:18 PM"
  }
]
```

<span data-ttu-id="73704-117">In dit voor beeld ziet u de uitvoer van de `ConvertTo-Json` cmdlet with en zonder de para meter **AsArray** .</span><span class="sxs-lookup"><span data-stu-id="73704-117">This example shows the output from `ConvertTo-Json` cmdlet with and without the **AsArray** switch parameter.</span></span> <span data-ttu-id="73704-118">U ziet dat het tweede gedeelte van de uitvoer wordt verpakt in een matrix van haakjes.</span><span class="sxs-lookup"><span data-stu-id="73704-118">You can see the second portion of the output is wrapped in array brackets.</span></span>

### <span data-ttu-id="73704-119">Voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="73704-119">Example 3</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="73704-120">Met deze opdracht wordt het effect van het gebruik van de para meter **compress** van gebruikt `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="73704-120">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="73704-121">De compressie is alleen van invloed op de weer gave van de teken reeks, niet op de geldigheids duur.</span><span class="sxs-lookup"><span data-stu-id="73704-121">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="73704-122">Voorbeeld 4</span><span class="sxs-lookup"><span data-stu-id="73704-122">Example 4</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 10:55:32 PM",
  "Date": "2018-10-12T00:00:00-05:00",
  "Day": 12,
  "DayOfWeek": 5,
  "DayOfYear": 285,
  "Hour": 22,
  "Kind": 2,
  "Millisecond": 639,
  "Minute": 55,
  "Month": 10,
  "Second": 32,
  "Ticks": 636749817326397744,
  "TimeOfDay": {
    "Ticks": 825326397744,
    "Days": 0,
    "Hours": 22,
    "Milliseconds": 639,
    "Minutes": 55,
    "Seconds": 32,
    "TotalDays": 0.95523888627777775,
    "TotalHours": 22.925733270666665,
    "TotalMilliseconds": 82532639.774400011,
    "TotalMinutes": 1375.54399624,
    "TotalSeconds": 82532.6397744
  },
  "Year": 2018
}
```

<span data-ttu-id="73704-123">In dit voor beeld wordt de `ConvertTo-Json` cmdlet gebruikt voor het converteren van een **System. datetime** -object van de `Get-Date` cmdlet naar een teken reeks in JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="73704-123">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="73704-124">De opdracht gebruikt de `Select-Object` cmdlet om alle ( `*` ) van de eigenschappen van het **DateTime** -object op te halen.</span><span class="sxs-lookup"><span data-stu-id="73704-124">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="73704-125">In de uitvoer ziet u de JSON-teken reeks die is `ConvertTo-Json` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="73704-125">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="73704-126">Voorbeeld 5</span><span class="sxs-lookup"><span data-stu-id="73704-126">Example 5</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : October 12, 2018 10:55:52 PM
Date        : 2018-10-12 12:00:00 AM
Day         : 12
DayOfWeek   : 5
DayOfYear   : 285
Hour        : 22
Kind        : 2
Millisecond : 768
Minute      : 55
Month       : 10
Second      : 52
Ticks       : 636749817527683372
TimeOfDay   : @{Ticks=825527683372; Days=0; Hours=22; Milliseconds=768; Minutes=55; Seconds=52;
              TotalDays=0.95547185575463; TotalHours=22.9313245381111; TotalMilliseconds=82552768.3372;
              TotalMinutes=1375.87947228667; TotalSeconds=82552.7683372}
Year        : 2018
```

<span data-ttu-id="73704-127">In dit voor beeld ziet u hoe u de `ConvertTo-Json` cmdlets en kunt gebruiken `ConvertFrom-Json` om een object te converteren naar een JSON-teken reeks en een JSON-object.</span><span class="sxs-lookup"><span data-stu-id="73704-127">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="73704-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73704-128">PARAMETERS</span></span>

### <span data-ttu-id="73704-129">-AsArray</span><span class="sxs-lookup"><span data-stu-id="73704-129">-AsArray</span></span>

<span data-ttu-id="73704-130">Hiermee wordt het object in een matrix tussen haakjes uitgevoerd, zelfs als de invoer een enkel object is.</span><span class="sxs-lookup"><span data-stu-id="73704-130">Outputs the object in array brackets, even if the input is a single object.</span></span>

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

### <span data-ttu-id="73704-131">-Comprimeren</span><span class="sxs-lookup"><span data-stu-id="73704-131">-Compress</span></span>

<span data-ttu-id="73704-132">Witruimte en Inge sprongen opmaak in de uitvoer teken reeks weglaten.</span><span class="sxs-lookup"><span data-stu-id="73704-132">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="73704-133">-Diepte</span><span class="sxs-lookup"><span data-stu-id="73704-133">-Depth</span></span>

<span data-ttu-id="73704-134">Hiermee geeft u op hoeveel niveaus van Inge sloten objecten worden opgenomen in de JSON-weer gave.</span><span class="sxs-lookup"><span data-stu-id="73704-134">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="73704-135">De standaardwaarde is 2.</span><span class="sxs-lookup"><span data-stu-id="73704-135">The default value is 2.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="73704-136">-EnumsAsStrings</span><span class="sxs-lookup"><span data-stu-id="73704-136">-EnumsAsStrings</span></span>

<span data-ttu-id="73704-137">Biedt een alternatieve serialisatie optie waarmee alle opsommingen worden geconverteerd naar de teken reeks weergave.</span><span class="sxs-lookup"><span data-stu-id="73704-137">Provides an alternative serialization option that converts all enumerations to their string representation.</span></span>

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

### <span data-ttu-id="73704-138">-EscapeHandling</span><span class="sxs-lookup"><span data-stu-id="73704-138">-EscapeHandling</span></span>

<span data-ttu-id="73704-139">Hiermee wordt bepaald hoe bepaalde tekens worden geescapet in de resulterende JSON-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="73704-139">Controls how certain characters are escaped in the resulting JSON output.</span></span> <span data-ttu-id="73704-140">Standaard worden alleen besturings tekens (zoals nieuwe regel) met escape-teken.</span><span class="sxs-lookup"><span data-stu-id="73704-140">By default, only control characters (like newline) are escaped.</span></span>

<span data-ttu-id="73704-141">Acceptabele waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="73704-141">Acceptable values are:</span></span>

- <span data-ttu-id="73704-142">Standaard-alleen besturings tekens worden met escape-teken.</span><span class="sxs-lookup"><span data-stu-id="73704-142">Default - Only control characters are escaped.</span></span>
- <span data-ttu-id="73704-143">EscapeNonAscii: alle niet-ASCII-en besturings tekens worden voorafgegaan.</span><span class="sxs-lookup"><span data-stu-id="73704-143">EscapeNonAscii - All non-ASCII and control characters are escaped.</span></span>
- <span data-ttu-id="73704-144">EscapeHtml-HTML ( `<` ,,, `>` `&` `'` `"` ) en de besturings tekens worden voorafgegaan.</span><span class="sxs-lookup"><span data-stu-id="73704-144">EscapeHtml - HTML (`<`, `>`, `&`, `'`, `"`) and control characters are escaped.</span></span>

<span data-ttu-id="73704-145">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="73704-145">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: Newtonsoft.Json.StringEscapeHandling
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="73704-146">-Input object</span><span class="sxs-lookup"><span data-stu-id="73704-146">-InputObject</span></span>

<span data-ttu-id="73704-147">Hiermee geeft u de objecten die moeten worden geconverteerd naar de JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="73704-147">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="73704-148">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73704-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="73704-149">U kunt ook een object pipet naar `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="73704-149">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="73704-150">De para meter **input object** is vereist, maar de waarde kan Null ( `$null` ) of een lege teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="73704-150">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="73704-151">Wanneer het invoer object is `$null` , wordt `ConvertTo-Json` er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="73704-151">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="73704-152">Wanneer het invoer object een lege teken reeks is, `ConvertTo-Json` retourneert een lege teken reeks.</span><span class="sxs-lookup"><span data-stu-id="73704-152">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="73704-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73704-153">CommonParameters</span></span>

<span data-ttu-id="73704-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="73704-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73704-155">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73704-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="73704-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="73704-156">INPUTS</span></span>

### <span data-ttu-id="73704-157">System. object</span><span class="sxs-lookup"><span data-stu-id="73704-157">System.Object</span></span>

<span data-ttu-id="73704-158">U kunt elk object door sluizen naar `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="73704-158">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="73704-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="73704-159">OUTPUTS</span></span>

### <span data-ttu-id="73704-160">System. String</span><span class="sxs-lookup"><span data-stu-id="73704-160">System.String</span></span>

## <span data-ttu-id="73704-161">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="73704-161">NOTES</span></span>

<span data-ttu-id="73704-162">De `ConvertTo-Json` cmdlet wordt geïmplementeerd met behulp van [Newton Soft JSON.net](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="73704-162">The `ConvertTo-Json` cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

## <span data-ttu-id="73704-163">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="73704-163">RELATED LINKS</span></span>

<span data-ttu-id="73704-164">[Een inleiding tot JavaScript Object Notation (JSON) in Java script en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="73704-164">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="73704-165">ConvertFrom-JSON</span><span class="sxs-lookup"><span data-stu-id="73704-165">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="73704-166">Get-Content</span><span class="sxs-lookup"><span data-stu-id="73704-166">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="73704-167">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="73704-167">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="73704-168">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="73704-168">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="73704-169">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="73704-169">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="73704-170">NewtonSoft.Jsop. StringEscapeHandling</span><span class="sxs-lookup"><span data-stu-id="73704-170">NewtonSoft.Json.StringEscapeHandling</span></span>](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
