---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: 83a8cb444c20db8f7dd2181cac13e56d54d5d986
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705837"
---
# <span data-ttu-id="07173-102">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="07173-102">ConvertTo-Json</span></span>

## <span data-ttu-id="07173-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="07173-103">SYNOPSIS</span></span>
<span data-ttu-id="07173-104">Converteert een object naar een teken reeks in JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="07173-104">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="07173-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="07173-105">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## <span data-ttu-id="07173-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="07173-106">DESCRIPTION</span></span>

<span data-ttu-id="07173-107">`ConvertTo-Json`Met de cmdlet wordt een .net-object geconverteerd naar een teken reeks in de indeling van de JavaScript object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="07173-107">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="07173-108">De eigenschappen worden geconverteerd naar veld namen, de veld waarden worden geconverteerd naar eigenschaps waarden en de methoden worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="07173-108">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="07173-109">U kunt de cmdlet vervolgens gebruiken `ConvertFrom-Json` om een JSON-indelings teken reeks te converteren naar een JSON-object, dat eenvoudig kan worden beheerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="07173-109">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="07173-110">Veel websites gebruiken JSON in plaats van XML om gegevens te serialiseren voor communicatie tussen servers en web-apps.</span><span class="sxs-lookup"><span data-stu-id="07173-110">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="07173-111">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="07173-111">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="07173-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="07173-112">EXAMPLES</span></span>

### <span data-ttu-id="07173-113">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="07173-113">Example 1</span></span>

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

<span data-ttu-id="07173-114">Met deze opdracht wordt de `ConvertTo-Json` cmdlet gebruikt om een GregorianCalendar-object te converteren naar een JSON-indelings teken reeks.</span><span class="sxs-lookup"><span data-stu-id="07173-114">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="07173-115">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="07173-115">Example 2</span></span>

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

<span data-ttu-id="07173-116">In dit voor beeld ziet u de uitvoer van de `ConvertTo-Json` cmdlet with en zonder de para meter **AsArray** .</span><span class="sxs-lookup"><span data-stu-id="07173-116">This example shows the output from `ConvertTo-Json` cmdlet with and without the **AsArray** switch parameter.</span></span> <span data-ttu-id="07173-117">U ziet dat het tweede gedeelte van de uitvoer wordt verpakt in een matrix van haakjes.</span><span class="sxs-lookup"><span data-stu-id="07173-117">You can see the second portion of the output is wrapped in array brackets.</span></span>

### <span data-ttu-id="07173-118">Voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="07173-118">Example 3</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="07173-119">Met deze opdracht wordt het effect van het gebruik van de para meter **compress** van gebruikt `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="07173-119">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="07173-120">De compressie is alleen van invloed op de weer gave van de teken reeks, niet op de geldigheids duur.</span><span class="sxs-lookup"><span data-stu-id="07173-120">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="07173-121">Voorbeeld 4</span><span class="sxs-lookup"><span data-stu-id="07173-121">Example 4</span></span>

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

<span data-ttu-id="07173-122">In dit voor beeld wordt de `ConvertTo-Json` cmdlet gebruikt voor het converteren van een **System. datetime** -object van de `Get-Date` cmdlet naar een teken reeks in JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="07173-122">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="07173-123">De opdracht gebruikt de `Select-Object` cmdlet om alle ( `*` ) van de eigenschappen van het **DateTime** -object op te halen.</span><span class="sxs-lookup"><span data-stu-id="07173-123">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="07173-124">In de uitvoer ziet u de JSON-teken reeks die is `ConvertTo-Json` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="07173-124">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="07173-125">Voorbeeld 5</span><span class="sxs-lookup"><span data-stu-id="07173-125">Example 5</span></span>

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

<span data-ttu-id="07173-126">In dit voor beeld ziet u hoe u de `ConvertTo-Json` cmdlets en kunt gebruiken `ConvertFrom-Json` om een object te converteren naar een JSON-teken reeks en een JSON-object.</span><span class="sxs-lookup"><span data-stu-id="07173-126">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="07173-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="07173-127">PARAMETERS</span></span>

### <span data-ttu-id="07173-128">-AsArray</span><span class="sxs-lookup"><span data-stu-id="07173-128">-AsArray</span></span>

<span data-ttu-id="07173-129">Hiermee wordt het object in een matrix tussen haakjes uitgevoerd, zelfs als de invoer een enkel object is.</span><span class="sxs-lookup"><span data-stu-id="07173-129">Outputs the object in array brackets, even if the input is a single object.</span></span>

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

### <span data-ttu-id="07173-130">-Comprimeren</span><span class="sxs-lookup"><span data-stu-id="07173-130">-Compress</span></span>

<span data-ttu-id="07173-131">Witruimte en Inge sprongen opmaak in de uitvoer teken reeks weglaten.</span><span class="sxs-lookup"><span data-stu-id="07173-131">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="07173-132">-Diepte</span><span class="sxs-lookup"><span data-stu-id="07173-132">-Depth</span></span>

<span data-ttu-id="07173-133">Hiermee geeft u op hoeveel niveaus van Inge sloten objecten worden opgenomen in de JSON-weer gave.</span><span class="sxs-lookup"><span data-stu-id="07173-133">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="07173-134">De standaardwaarde is 2.</span><span class="sxs-lookup"><span data-stu-id="07173-134">The default value is 2.</span></span>

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

### <span data-ttu-id="07173-135">-EnumsAsStrings</span><span class="sxs-lookup"><span data-stu-id="07173-135">-EnumsAsStrings</span></span>

<span data-ttu-id="07173-136">Biedt een alternatieve serialisatie optie waarmee alle opsommingen worden geconverteerd naar de teken reeks weergave.</span><span class="sxs-lookup"><span data-stu-id="07173-136">Provides an alternative serialization option that converts all enumerations to their string representation.</span></span>

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

### <span data-ttu-id="07173-137">-EscapeHandling</span><span class="sxs-lookup"><span data-stu-id="07173-137">-EscapeHandling</span></span>

<span data-ttu-id="07173-138">Hiermee wordt bepaald hoe bepaalde tekens worden geescapet in de resulterende JSON-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="07173-138">Controls how certain characters are escaped in the resulting JSON output.</span></span> <span data-ttu-id="07173-139">Standaard worden alleen besturings tekens (zoals nieuwe regel) met escape-teken.</span><span class="sxs-lookup"><span data-stu-id="07173-139">By default, only control characters (like newline) are escaped.</span></span>

<span data-ttu-id="07173-140">Acceptabele waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="07173-140">Acceptable values are:</span></span>

- <span data-ttu-id="07173-141">Standaard-alleen besturings tekens worden met escape-teken.</span><span class="sxs-lookup"><span data-stu-id="07173-141">Default - Only control characters are escaped.</span></span>
- <span data-ttu-id="07173-142">EscapeNonAscii: alle niet-ASCII-en besturings tekens worden voorafgegaan.</span><span class="sxs-lookup"><span data-stu-id="07173-142">EscapeNonAscii - All non-ASCII and control characters are escaped.</span></span>
- <span data-ttu-id="07173-143">EscapeHtml-HTML ( `<` ,,, `>` `&` `'` `"` ) en de besturings tekens worden voorafgegaan.</span><span class="sxs-lookup"><span data-stu-id="07173-143">EscapeHtml - HTML (`<`, `>`, `&`, `'`, `"`) and control characters are escaped.</span></span>

<span data-ttu-id="07173-144">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="07173-144">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="07173-145">-Input object</span><span class="sxs-lookup"><span data-stu-id="07173-145">-InputObject</span></span>

<span data-ttu-id="07173-146">Hiermee geeft u de objecten die moeten worden geconverteerd naar de JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="07173-146">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="07173-147">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="07173-147">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="07173-148">U kunt ook een object pipet naar `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="07173-148">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="07173-149">De para meter **input object** is vereist, maar de waarde kan Null ( `$null` ) of een lege teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="07173-149">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="07173-150">Wanneer het invoer object is `$null` , wordt `ConvertTo-Json` er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="07173-150">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="07173-151">Wanneer het invoer object een lege teken reeks is, `ConvertTo-Json` retourneert een lege teken reeks.</span><span class="sxs-lookup"><span data-stu-id="07173-151">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

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

### <span data-ttu-id="07173-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="07173-152">CommonParameters</span></span>

<span data-ttu-id="07173-153">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="07173-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="07173-154">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="07173-154">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="07173-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="07173-155">INPUTS</span></span>

### <span data-ttu-id="07173-156">System. object</span><span class="sxs-lookup"><span data-stu-id="07173-156">System.Object</span></span>

<span data-ttu-id="07173-157">U kunt elk object door sluizen naar `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="07173-157">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="07173-158">UITVOER</span><span class="sxs-lookup"><span data-stu-id="07173-158">OUTPUTS</span></span>

### <span data-ttu-id="07173-159">System. String</span><span class="sxs-lookup"><span data-stu-id="07173-159">System.String</span></span>

## <span data-ttu-id="07173-160">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="07173-160">NOTES</span></span>

<span data-ttu-id="07173-161">De `ConvertTo-Json` cmdlet wordt geïmplementeerd met behulp van [Newton Soft JSON.net](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="07173-161">The `ConvertTo-Json` cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

## <span data-ttu-id="07173-162">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="07173-162">RELATED LINKS</span></span>

<span data-ttu-id="07173-163">[Een inleiding tot JavaScript Object Notation (JSON) in Java script en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="07173-163">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="07173-164">ConvertFrom-JSON</span><span class="sxs-lookup"><span data-stu-id="07173-164">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="07173-165">Get-Content</span><span class="sxs-lookup"><span data-stu-id="07173-165">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="07173-166">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="07173-166">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="07173-167">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="07173-167">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="07173-168">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="07173-168">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="07173-169">NewtonSoft.Jsop. StringEscapeHandling</span><span class="sxs-lookup"><span data-stu-id="07173-169">NewtonSoft.Json.StringEscapeHandling</span></span>](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
