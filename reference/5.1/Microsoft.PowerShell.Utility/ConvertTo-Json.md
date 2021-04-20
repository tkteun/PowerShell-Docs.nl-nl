---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: e46ac1c58fa64b78411988d30f26f2ed771492f2
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729916"
---
# <span data-ttu-id="dd12e-102">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="dd12e-102">ConvertTo-Json</span></span>

## <span data-ttu-id="dd12e-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="dd12e-103">SYNOPSIS</span></span>
<span data-ttu-id="dd12e-104">Converteert een object naar een tekenreeks in JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="dd12e-104">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="dd12e-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="dd12e-105">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
 [<CommonParameters>]
```

## <span data-ttu-id="dd12e-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="dd12e-106">DESCRIPTION</span></span>

<span data-ttu-id="dd12e-107">De `ConvertTo-Json` cmdlet converteert elk .NET-object naar een tekenreeks in JavaScript Object Notation indeling (JSON).</span><span class="sxs-lookup"><span data-stu-id="dd12e-107">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="dd12e-108">De eigenschappen worden geconverteerd naar veldnamen, de veldwaarden worden geconverteerd naar eigenschapswaarden en de methoden worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="dd12e-108">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="dd12e-109">Vervolgens kunt u de cmdlet gebruiken om een tekenreeks in JSON-indeling te converteren naar een `ConvertFrom-Json` JSON-object, dat eenvoudig kan worden beheerd in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd12e-109">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="dd12e-110">Veel websites gebruiken JSON in plaats van XML om gegevens te serialiseren voor communicatie tussen servers en web-apps.</span><span class="sxs-lookup"><span data-stu-id="dd12e-110">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="dd12e-111">Deze cmdlet is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="dd12e-111">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="dd12e-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="dd12e-112">EXAMPLES</span></span>

### <span data-ttu-id="dd12e-113">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="dd12e-113">Example 1</span></span>

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
    "MinSupportedDateTime":  "\/Date(-62135596800000)\/",
    "MaxSupportedDateTime":  "\/Date(253402300799999)\/",
    "AlgorithmType":  1,
    "CalendarType":  1,
    "Eras":  [
                 1
             ],
    "TwoDigitYearMax":  2029,
    "IsReadOnly":  false
}
```

<span data-ttu-id="dd12e-114">Met deze opdracht wordt de `ConvertTo-Json` cmdlet gebruikt om een Object GregorianCalendar te converteren naar een tekenreeks in JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="dd12e-114">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="dd12e-115">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="dd12e-115">Example 2</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="dd12e-116">Met deze opdracht ziet u het effect van het gebruik van de parameter **Compress** van `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="dd12e-116">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="dd12e-117">De compressie is alleen van invloed op het uiterlijk van de tekenreeks, niet op de geldigheid ervan.</span><span class="sxs-lookup"><span data-stu-id="dd12e-117">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="dd12e-118">Voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="dd12e-118">Example 3</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
    "DisplayHint":  2,
    "DateTime":  "Friday, January 13, 2012 8:06:16 PM",
    "Date":  "\/Date(1326441600000)\/",
    "Day":  13,
    "DayOfWeek":  5,
    "DayOfYear":  13,
    "Hour":  20,
    "Kind":  2,
    "Millisecond":  221,
    "Minute":  6,
    "Month":  1,
    "Second":  16,
    "Ticks":  634620819762218083,
    "TimeOfDay":  {
                      "Ticks":  723762218083,
                      "Days":  0,
                      "Hours":  20,
                      "Milliseconds":  221,
                      "Minutes":  6,
                      "Seconds":  16,
                      "TotalDays":  0.83768775241087956,
                      "TotalHours":  20.104506057861109,
                      "TotalMilliseconds":  72376221.8083,
                      "TotalMinutes":  1206.2703634716668,
                      "TotalSeconds":  72376.22180829999
                  },
    "Year":  2012
}
```

<span data-ttu-id="dd12e-119">In dit voorbeeld wordt de cmdlet gebruikt om een System.DateTime-object van de cmdlet te converteren naar een `ConvertTo-Json`  `Get-Date` tekenreeks met JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="dd12e-119">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="dd12e-120">De opdracht gebruikt de `Select-Object` cmdlet om alle ( `*` ) eigenschappen van het **DateTime-object op te** halen.</span><span class="sxs-lookup"><span data-stu-id="dd12e-120">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="dd12e-121">De uitvoer toont de JSON-tekenreeks die is `ConvertTo-Json` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="dd12e-121">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="dd12e-122">Voorbeeld 4</span><span class="sxs-lookup"><span data-stu-id="dd12e-122">Example 4</span></span>

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

<span data-ttu-id="dd12e-123">In dit voorbeeld ziet u hoe u de cmdlets en gebruikt om een object te converteren naar een `ConvertTo-Json` `ConvertFrom-Json` JSON-tekenreeks en een JSON-object.</span><span class="sxs-lookup"><span data-stu-id="dd12e-123">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="dd12e-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dd12e-124">PARAMETERS</span></span>

### <span data-ttu-id="dd12e-125">-Comprimeren</span><span class="sxs-lookup"><span data-stu-id="dd12e-125">-Compress</span></span>

<span data-ttu-id="dd12e-126">Geen witruimte en ingesprongen opmaak in de uitvoertekenreeks.</span><span class="sxs-lookup"><span data-stu-id="dd12e-126">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="dd12e-127">-Diepte</span><span class="sxs-lookup"><span data-stu-id="dd12e-127">-Depth</span></span>

<span data-ttu-id="dd12e-128">Hiermee geeft u op hoeveel niveaus van ingesloten objecten zijn opgenomen in de JSON-weergave.</span><span class="sxs-lookup"><span data-stu-id="dd12e-128">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="dd12e-129">De waarde kan een getal van tot `1` `[Int]::MaxValue` zijn.</span><span class="sxs-lookup"><span data-stu-id="dd12e-129">The value can be any number from `1` to `[Int]::MaxValue`.</span></span> <span data-ttu-id="dd12e-130">De standaardwaarde is `2`.</span><span class="sxs-lookup"><span data-stu-id="dd12e-130">The default value is `2`.</span></span> <span data-ttu-id="dd12e-131">`ConvertTo-Json` geeft een waarschuwing weer als het aantal niveaus in een invoerobject dit aantal overschrijdt.</span><span class="sxs-lookup"><span data-stu-id="dd12e-131">`ConvertTo-Json` emits a warning if the number of levels in an input object exceeds this number.</span></span>

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

### <span data-ttu-id="dd12e-132">-InputObject</span><span class="sxs-lookup"><span data-stu-id="dd12e-132">-InputObject</span></span>

<span data-ttu-id="dd12e-133">Hiermee geeft u de objecten om te converteren naar JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="dd12e-133">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="dd12e-134">Voer een variabele in die de objecten bevat of typ een opdracht of expressie die de objecten op haalt.</span><span class="sxs-lookup"><span data-stu-id="dd12e-134">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="dd12e-135">U kunt een object ook doorspijpen naar `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="dd12e-135">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="dd12e-136">De **parameter InputObject** is vereist, maar de waarde kan null ( `$null` ) of een lege tekenreeks zijn.</span><span class="sxs-lookup"><span data-stu-id="dd12e-136">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="dd12e-137">Wanneer het invoerobject `$null` is, `ConvertTo-Json` genereert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="dd12e-137">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="dd12e-138">Wanneer het invoerobject een lege tekenreeks is, `ConvertTo-Json` retourneert een lege tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="dd12e-138">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

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

### <span data-ttu-id="dd12e-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dd12e-139">CommonParameters</span></span>

<span data-ttu-id="dd12e-140">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dd12e-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dd12e-141">Zie voor meer informatie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="dd12e-141">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="dd12e-142">INVOER</span><span class="sxs-lookup"><span data-stu-id="dd12e-142">INPUTS</span></span>

### <span data-ttu-id="dd12e-143">System.Object</span><span class="sxs-lookup"><span data-stu-id="dd12e-143">System.Object</span></span>

<span data-ttu-id="dd12e-144">U kunt elk object doorspijpen naar `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="dd12e-144">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="dd12e-145">UITVOER</span><span class="sxs-lookup"><span data-stu-id="dd12e-145">OUTPUTS</span></span>

### <span data-ttu-id="dd12e-146">System.String</span><span class="sxs-lookup"><span data-stu-id="dd12e-146">System.String</span></span>

## <span data-ttu-id="dd12e-147">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="dd12e-147">NOTES</span></span>

<span data-ttu-id="dd12e-148">De `ConvertTo-Json` cmdlet wordt geïmplementeerd met behulp van de [JavaScriptSerializer-klasse](/dotnet/api/system.web.script.serialization.javascriptserializer).</span><span class="sxs-lookup"><span data-stu-id="dd12e-148">The `ConvertTo-Json` cmdlet is implemented using the [JavaScriptSerializer class](/dotnet/api/system.web.script.serialization.javascriptserializer).</span></span>

## <span data-ttu-id="dd12e-149">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="dd12e-149">RELATED LINKS</span></span>

<span data-ttu-id="dd12e-150">[Een inleiding tot JavaScript Object Notation (JSON) in JavaScript en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="dd12e-150">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="dd12e-151">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="dd12e-151">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="dd12e-152">Get-Content</span><span class="sxs-lookup"><span data-stu-id="dd12e-152">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="dd12e-153">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="dd12e-153">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="dd12e-154">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="dd12e-154">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="dd12e-155">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="dd12e-155">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
