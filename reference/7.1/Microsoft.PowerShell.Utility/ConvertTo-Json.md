---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: 6b90699266cf1a93cedb377fe4e4cb7f1e86a90d
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729988"
---
# <span data-ttu-id="38320-102">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="38320-102">ConvertTo-Json</span></span>

## <span data-ttu-id="38320-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="38320-103">SYNOPSIS</span></span>
<span data-ttu-id="38320-104">Converteert een object naar een tekenreeks in JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="38320-104">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="38320-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="38320-105">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## <span data-ttu-id="38320-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="38320-106">DESCRIPTION</span></span>

<span data-ttu-id="38320-107">De `ConvertTo-Json` cmdlet converteert elk .NET-object naar een tekenreeks in JavaScript Object Notation indeling (JSON).</span><span class="sxs-lookup"><span data-stu-id="38320-107">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="38320-108">De eigenschappen worden geconverteerd naar veldnamen, de veldwaarden worden geconverteerd naar eigenschapswaarden en de methoden worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="38320-108">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="38320-109">Vervolgens kunt u de cmdlet gebruiken om een tekenreeks in JSON-indeling te converteren naar een JSON-object, dat eenvoudig kan `ConvertFrom-Json` worden beheerd in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38320-109">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="38320-110">Veel websites gebruiken JSON in plaats van XML om gegevens te serialiseren voor communicatie tussen servers en web-apps.</span><span class="sxs-lookup"><span data-stu-id="38320-110">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="38320-111">Vanaf PowerShell 7.1 geeft een waarschuwing als de diepte van het invoerobject groter is dan de diepte die is `ConvertTo-Json` opgegeven voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="38320-111">As of PowerShell 7.1, `ConvertTo-Json` emits a warning if the depth of the input object exceeds the depth specified for the command.</span></span> <span data-ttu-id="38320-112">Hiermee voorkomt u ongewenst gegevensverlies bij het converteren van objecten.</span><span class="sxs-lookup"><span data-stu-id="38320-112">This prevents unwanted data loss when converting objects.</span></span>

<span data-ttu-id="38320-113">Deze cmdlet is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="38320-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="38320-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="38320-114">EXAMPLES</span></span>

### <span data-ttu-id="38320-115">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="38320-115">Example 1</span></span>

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

<span data-ttu-id="38320-116">Met deze opdracht wordt de `ConvertTo-Json` cmdlet gebruikt om een Object GregorianCalendar te converteren naar een tekenreeks in JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="38320-116">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="38320-117">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="38320-117">Example 2</span></span>

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

<span data-ttu-id="38320-118">In dit voorbeeld ziet u de uitvoer van `ConvertTo-Json` de cmdlet met en zonder de **asArray-switchparameter.**</span><span class="sxs-lookup"><span data-stu-id="38320-118">This example shows the output from `ConvertTo-Json` cmdlet with and without the **AsArray** switch parameter.</span></span> <span data-ttu-id="38320-119">U kunt zien dat het tweede deel van de uitvoer tussen matrixhaken is verpakt.</span><span class="sxs-lookup"><span data-stu-id="38320-119">You can see the second portion of the output is wrapped in array brackets.</span></span>

### <span data-ttu-id="38320-120">Voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="38320-120">Example 3</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="38320-121">Met deze opdracht ziet u het effect van het gebruik van de parameter **Compress** van `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="38320-121">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="38320-122">De compressie is alleen van invloed op het uiterlijk van de tekenreeks, niet op de geldigheid ervan.</span><span class="sxs-lookup"><span data-stu-id="38320-122">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="38320-123">Voorbeeld 4</span><span class="sxs-lookup"><span data-stu-id="38320-123">Example 4</span></span>

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

<span data-ttu-id="38320-124">In dit voorbeeld wordt de `ConvertTo-Json` cmdlet gebruikt om een **System.DateTime-object** van de cmdlet te converteren naar een `Get-Date` tekenreeks met JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="38320-124">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="38320-125">De opdracht gebruikt de `Select-Object` cmdlet om alle ( `*` ) eigenschappen van het **DateTime-object op te** halen.</span><span class="sxs-lookup"><span data-stu-id="38320-125">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="38320-126">In de uitvoer ziet u de JSON-tekenreeks die is `ConvertTo-Json` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="38320-126">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="38320-127">Voorbeeld 5</span><span class="sxs-lookup"><span data-stu-id="38320-127">Example 5</span></span>

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

<span data-ttu-id="38320-128">In dit voorbeeld ziet u hoe u de cmdlets en gebruikt om een object te converteren naar een `ConvertTo-Json` `ConvertFrom-Json` JSON-tekenreeks en een JSON-object.</span><span class="sxs-lookup"><span data-stu-id="38320-128">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="38320-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="38320-129">PARAMETERS</span></span>

### <span data-ttu-id="38320-130">-AsArray</span><span class="sxs-lookup"><span data-stu-id="38320-130">-AsArray</span></span>

<span data-ttu-id="38320-131">Het object wordt uitgevoerd tussen matrixhaken, zelfs als de invoer één object is.</span><span class="sxs-lookup"><span data-stu-id="38320-131">Outputs the object in array brackets, even if the input is a single object.</span></span>

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

### <span data-ttu-id="38320-132">-Comprimeren</span><span class="sxs-lookup"><span data-stu-id="38320-132">-Compress</span></span>

<span data-ttu-id="38320-133">Geen witruimte en ingesprongen opmaak in de uitvoertekenreeks.</span><span class="sxs-lookup"><span data-stu-id="38320-133">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="38320-134">-Diepte</span><span class="sxs-lookup"><span data-stu-id="38320-134">-Depth</span></span>

<span data-ttu-id="38320-135">Hiermee geeft u op hoeveel niveaus van ingesloten objecten zijn opgenomen in de JSON-weergave.</span><span class="sxs-lookup"><span data-stu-id="38320-135">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="38320-136">De waarde kan elk getal van tot `1` `[Int]::MaxValue` zijn.</span><span class="sxs-lookup"><span data-stu-id="38320-136">The value can be any number from `1` to `[Int]::MaxValue`.</span></span> <span data-ttu-id="38320-137">De standaardwaarde is `2`.</span><span class="sxs-lookup"><span data-stu-id="38320-137">The default value is `2`.</span></span> <span data-ttu-id="38320-138">`ConvertTo-Json` geeft een waarschuwing weer als het aantal niveaus in een invoerobject dit aantal overschrijdt.</span><span class="sxs-lookup"><span data-stu-id="38320-138">`ConvertTo-Json` emits a warning if the number of levels in an input object exceeds this number.</span></span>

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

### <span data-ttu-id="38320-139">-EnumsAsStrings</span><span class="sxs-lookup"><span data-stu-id="38320-139">-EnumsAsStrings</span></span>

<span data-ttu-id="38320-140">Biedt een alternatieve serialisatieoptie die alle enumeraties converteert naar de tekenreeksweergave.</span><span class="sxs-lookup"><span data-stu-id="38320-140">Provides an alternative serialization option that converts all enumerations to their string representation.</span></span>

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

### <span data-ttu-id="38320-141">-EscapeHandling</span><span class="sxs-lookup"><span data-stu-id="38320-141">-EscapeHandling</span></span>

<span data-ttu-id="38320-142">Hiermee bepaalt u hoe bepaalde tekens worden uitgesloten in de resulterende JSON-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="38320-142">Controls how certain characters are escaped in the resulting JSON output.</span></span> <span data-ttu-id="38320-143">Standaard worden alleen besturingselementtekens (zoals nieuwe regel) als escape-teken gebruikt.</span><span class="sxs-lookup"><span data-stu-id="38320-143">By default, only control characters (like newline) are escaped.</span></span>

<span data-ttu-id="38320-144">Acceptabele waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="38320-144">Acceptable values are:</span></span>

- <span data-ttu-id="38320-145">Standaard: alleen besturingselementtekens krijgen een escape-teken.</span><span class="sxs-lookup"><span data-stu-id="38320-145">Default - Only control characters are escaped.</span></span>
- <span data-ttu-id="38320-146">EscapeNonAscii: alle niet-ASCII- en besturingstekens krijgen een escape-teken.</span><span class="sxs-lookup"><span data-stu-id="38320-146">EscapeNonAscii - All non-ASCII and control characters are escaped.</span></span>
- <span data-ttu-id="38320-147">EscapeHtml- HTML ( `<` , , , , , ) en `>` `&` `'` `"` besturingselementtekens worden als escape-teken gebruikt.</span><span class="sxs-lookup"><span data-stu-id="38320-147">EscapeHtml - HTML (`<`, `>`, `&`, `'`, `"`) and control characters are escaped.</span></span>

<span data-ttu-id="38320-148">Deze parameter is geïntroduceerd in PowerShell 6.2.</span><span class="sxs-lookup"><span data-stu-id="38320-148">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="38320-149">-InputObject</span><span class="sxs-lookup"><span data-stu-id="38320-149">-InputObject</span></span>

<span data-ttu-id="38320-150">Hiermee geeft u de objecten om te converteren naar JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="38320-150">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="38320-151">Voer een variabele in die de objecten bevat of typ een opdracht of expressie die de objecten op haalt.</span><span class="sxs-lookup"><span data-stu-id="38320-151">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="38320-152">U kunt een object ook doorspijpen naar `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="38320-152">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="38320-153">De **parameter InputObject** is vereist, maar de waarde kan null ( `$null` ) of een lege tekenreeks zijn.</span><span class="sxs-lookup"><span data-stu-id="38320-153">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="38320-154">Wanneer het invoerobject `$null` is, `ConvertTo-Json` genereert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="38320-154">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="38320-155">Wanneer het invoerobject een lege tekenreeks is, `ConvertTo-Json` retourneert een lege tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="38320-155">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

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

### <span data-ttu-id="38320-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38320-156">CommonParameters</span></span>

<span data-ttu-id="38320-157">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="38320-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="38320-158">Zie voor meer informatie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="38320-158">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="38320-159">INVOER</span><span class="sxs-lookup"><span data-stu-id="38320-159">INPUTS</span></span>

### <span data-ttu-id="38320-160">System.Object</span><span class="sxs-lookup"><span data-stu-id="38320-160">System.Object</span></span>

<span data-ttu-id="38320-161">U kunt elk object doorspijpen naar `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="38320-161">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="38320-162">UITVOER</span><span class="sxs-lookup"><span data-stu-id="38320-162">OUTPUTS</span></span>

### <span data-ttu-id="38320-163">System.String</span><span class="sxs-lookup"><span data-stu-id="38320-163">System.String</span></span>

## <span data-ttu-id="38320-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="38320-164">NOTES</span></span>

<span data-ttu-id="38320-165">De `ConvertTo-Json` cmdlet wordt geïmplementeerd met [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="38320-165">The `ConvertTo-Json` cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

## <span data-ttu-id="38320-166">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="38320-166">RELATED LINKS</span></span>

<span data-ttu-id="38320-167">[Een inleiding tot JavaScript Object Notation (JSON) in JavaScript en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="38320-167">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="38320-168">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="38320-168">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="38320-169">Get-Content</span><span class="sxs-lookup"><span data-stu-id="38320-169">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="38320-170">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="38320-170">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="38320-171">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="38320-171">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="38320-172">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="38320-172">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="38320-173">NewtonSoft.Jsaan. StringEscapeHandling</span><span class="sxs-lookup"><span data-stu-id="38320-173">NewtonSoft.Json.StringEscapeHandling</span></span>](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
