---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: 9831249a9f1ffcc65fc275e44da04fde9348ae71
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388056"
---
# <span data-ttu-id="d00f3-103">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="d00f3-103">ConvertTo-Json</span></span>

## <span data-ttu-id="d00f3-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d00f3-104">SYNOPSIS</span></span>
<span data-ttu-id="d00f3-105">Converteert een object naar een teken reeks in JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="d00f3-105">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="d00f3-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d00f3-106">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
 [<CommonParameters>]
```

## <span data-ttu-id="d00f3-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d00f3-107">DESCRIPTION</span></span>

<span data-ttu-id="d00f3-108">`ConvertTo-Json`Met de cmdlet wordt een .net-object geconverteerd naar een teken reeks in de indeling van de JavaScript object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="d00f3-108">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="d00f3-109">De eigenschappen worden geconverteerd naar veld namen, de veld waarden worden geconverteerd naar eigenschaps waarden en de methoden worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d00f3-109">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="d00f3-110">U kunt de cmdlet vervolgens gebruiken `ConvertFrom-Json` om een JSON-indelings teken reeks te converteren naar een JSON-object, dat eenvoudig kan worden beheerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="d00f3-110">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="d00f3-111">Veel websites gebruiken JSON in plaats van XML om gegevens te serialiseren voor communicatie tussen servers en web-apps.</span><span class="sxs-lookup"><span data-stu-id="d00f3-111">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="d00f3-112">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d00f3-112">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="d00f3-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d00f3-113">EXAMPLES</span></span>

### <span data-ttu-id="d00f3-114">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="d00f3-114">Example 1</span></span>

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

<span data-ttu-id="d00f3-115">Met deze opdracht wordt de `ConvertTo-Json` cmdlet gebruikt om een GregorianCalendar-object te converteren naar een JSON-indelings teken reeks.</span><span class="sxs-lookup"><span data-stu-id="d00f3-115">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="d00f3-116">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="d00f3-116">Example 2</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="d00f3-117">Met deze opdracht wordt het effect van het gebruik van de para meter **compress** van gebruikt `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="d00f3-117">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="d00f3-118">De compressie is alleen van invloed op de weer gave van de teken reeks, niet op de geldigheids duur.</span><span class="sxs-lookup"><span data-stu-id="d00f3-118">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="d00f3-119">Voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="d00f3-119">Example 3</span></span>

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

<span data-ttu-id="d00f3-120">In dit voor beeld wordt de `ConvertTo-Json` cmdlet gebruikt voor het converteren van een **System. datetime** -object van de `Get-Date` cmdlet naar een teken reeks in JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="d00f3-120">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="d00f3-121">De opdracht gebruikt de `Select-Object` cmdlet om alle ( `*` ) van de eigenschappen van het **DateTime** -object op te halen.</span><span class="sxs-lookup"><span data-stu-id="d00f3-121">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="d00f3-122">In de uitvoer ziet u de JSON-teken reeks die is `ConvertTo-Json` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d00f3-122">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="d00f3-123">Voorbeeld 4</span><span class="sxs-lookup"><span data-stu-id="d00f3-123">Example 4</span></span>

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

<span data-ttu-id="d00f3-124">In dit voor beeld ziet u hoe u de `ConvertTo-Json` cmdlets en kunt gebruiken `ConvertFrom-Json` om een object te converteren naar een JSON-teken reeks en een JSON-object.</span><span class="sxs-lookup"><span data-stu-id="d00f3-124">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="d00f3-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d00f3-125">PARAMETERS</span></span>

### <span data-ttu-id="d00f3-126">-Comprimeren</span><span class="sxs-lookup"><span data-stu-id="d00f3-126">-Compress</span></span>

<span data-ttu-id="d00f3-127">Witruimte en Inge sprongen opmaak in de uitvoer teken reeks weglaten.</span><span class="sxs-lookup"><span data-stu-id="d00f3-127">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="d00f3-128">-Diepte</span><span class="sxs-lookup"><span data-stu-id="d00f3-128">-Depth</span></span>

<span data-ttu-id="d00f3-129">Hiermee geeft u op hoeveel niveaus van Inge sloten objecten worden opgenomen in de JSON-weer gave.</span><span class="sxs-lookup"><span data-stu-id="d00f3-129">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="d00f3-130">De standaardwaarde is 2.</span><span class="sxs-lookup"><span data-stu-id="d00f3-130">The default value is 2.</span></span>

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

### <span data-ttu-id="d00f3-131">-Input object</span><span class="sxs-lookup"><span data-stu-id="d00f3-131">-InputObject</span></span>

<span data-ttu-id="d00f3-132">Hiermee geeft u de objecten die moeten worden geconverteerd naar de JSON-indeling.</span><span class="sxs-lookup"><span data-stu-id="d00f3-132">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="d00f3-133">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d00f3-133">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="d00f3-134">U kunt ook een object pipet naar `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="d00f3-134">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="d00f3-135">De para meter **input object** is vereist, maar de waarde kan Null ( `$null` ) of een lege teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="d00f3-135">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="d00f3-136">Wanneer het invoer object is `$null` , wordt `ConvertTo-Json` er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="d00f3-136">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="d00f3-137">Wanneer het invoer object een lege teken reeks is, `ConvertTo-Json` retourneert een lege teken reeks.</span><span class="sxs-lookup"><span data-stu-id="d00f3-137">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

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

### <span data-ttu-id="d00f3-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d00f3-138">CommonParameters</span></span>

<span data-ttu-id="d00f3-139">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d00f3-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d00f3-140">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d00f3-140">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d00f3-141">INVOER</span><span class="sxs-lookup"><span data-stu-id="d00f3-141">INPUTS</span></span>

### <span data-ttu-id="d00f3-142">System. object</span><span class="sxs-lookup"><span data-stu-id="d00f3-142">System.Object</span></span>

<span data-ttu-id="d00f3-143">U kunt elk object door sluizen naar `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="d00f3-143">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="d00f3-144">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d00f3-144">OUTPUTS</span></span>

### <span data-ttu-id="d00f3-145">System. String</span><span class="sxs-lookup"><span data-stu-id="d00f3-145">System.String</span></span>

## <span data-ttu-id="d00f3-146">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d00f3-146">NOTES</span></span>

<span data-ttu-id="d00f3-147">De `ConvertTo-Json` cmdlet wordt geïmplementeerd met behulp van de [JavaScriptSerializer-klasse](/dotnet/api/system.web.script.serialization.javascriptserializer).</span><span class="sxs-lookup"><span data-stu-id="d00f3-147">The `ConvertTo-Json` cmdlet is implemented using the [JavaScriptSerializer class](/dotnet/api/system.web.script.serialization.javascriptserializer).</span></span>

## <span data-ttu-id="d00f3-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d00f3-148">RELATED LINKS</span></span>

<span data-ttu-id="d00f3-149">[Een inleiding tot JavaScript Object Notation (JSON) in Java script en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="d00f3-149">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="d00f3-150">ConvertFrom-JSON</span><span class="sxs-lookup"><span data-stu-id="d00f3-150">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="d00f3-151">Get-Content</span><span class="sxs-lookup"><span data-stu-id="d00f3-151">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="d00f3-152">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="d00f3-152">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="d00f3-153">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="d00f3-153">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="d00f3-154">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="d00f3-154">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
