---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: f2159a2de3432aec14fb395b93ed476f349616a8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250479"
---
# <span data-ttu-id="a1ee0-103">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="a1ee0-103">ConvertFrom-Json</span></span>

## <span data-ttu-id="a1ee0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a1ee0-104">SYNOPSIS</span></span>
<span data-ttu-id="a1ee0-105">Converteert een teken reeks in JSON-indeling naar een aangepast object.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-105">Converts a JSON-formatted string to a custom object.</span></span>

## <span data-ttu-id="a1ee0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a1ee0-106">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [<CommonParameters>]
```

## <span data-ttu-id="a1ee0-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a1ee0-107">DESCRIPTION</span></span>

<span data-ttu-id="a1ee0-108">Met de `ConvertFrom-Json` cmdlet wordt een met JavaScript object Notation (JSON) opgemaakte teken reeks geconverteerd naar een aangepast **PSCustomObject** -object met een eigenschap voor elk veld in de JSON-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-108">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="a1ee0-109">JSON wordt doorgaans door websites gebruikt om een tekstuele representatie van objecten te bieden.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-109">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="a1ee0-110">De JSON-standaard verhindert niet het gebruik dat is verboden met een **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-110">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject**.</span></span> <span data-ttu-id="a1ee0-111">Als de JSON-teken reeks bijvoorbeeld dubbele sleutels bevat, wordt alleen de laatste sleutel gebruikt door deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-111">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="a1ee0-112">Zie andere voor beelden hieronder.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-112">See other examples below.</span></span>

<span data-ttu-id="a1ee0-113">Als u een JSON-teken reeks wilt genereren vanuit een wille keurig object, gebruikt u de `ConvertTo-Json` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-113">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="a1ee0-114">Deze cmdlet is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="a1ee0-115">Deze cmdlet biedt geen ondersteuning voor JSON met opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-115">This cmdlet doesn't support JSON with comments.</span></span>

## <span data-ttu-id="a1ee0-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a1ee0-116">EXAMPLES</span></span>

### <span data-ttu-id="a1ee0-117">Voor beeld 1: een DateTime-object converteren naar een JSON-object</span><span class="sxs-lookup"><span data-stu-id="a1ee0-117">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="a1ee0-118">Met deze opdracht worden de- `ConvertTo-Json` en- `ConvertFrom-Json` cmdlets gebruikt om een **DateTime** -object van de cmdlet om te zetten naar een JSON- `Get-Date` object en vervolgens naar een **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-118">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject**.</span></span>

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

<span data-ttu-id="a1ee0-119">In het voor beeld wordt de `Select-Object` cmdlet gebruikt om alle eigenschappen van het **DateTime** -object op te halen.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-119">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="a1ee0-120">De cmdlet wordt gebruikt `ConvertTo-Json` om het **DateTime** -object te converteren naar een teken reeks die is OPGEMAAKT als een JSON-object en de `ConvertFrom-Json` cmdlet om de teken reeks in JSON-indeling te converteren naar een **PSCustomObject** -object.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-120">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="a1ee0-121">Voor beeld 2: JSON-teken reeksen ophalen van een webservice en deze converteren naar Power shell-objecten</span><span class="sxs-lookup"><span data-stu-id="a1ee0-121">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="a1ee0-122">Met deze opdracht wordt de `Invoke-WebRequest` cmdlet gebruikt om JSON-teken reeksen op te halen uit een webservice en wordt vervolgens de `ConvertFrom-Json` cmdlet gebruikt om JSON-inhoud te converteren naar objecten die kunnen worden beheerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-122">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="a1ee0-123">U kunt ook de `Invoke-RestMethod` cmdlet gebruiken, waarmee JSON-inhoud automatisch naar objecten wordt geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-123">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="a1ee0-124">Voor beeld 3: een JSON-teken reeks converteren naar een aangepast object</span><span class="sxs-lookup"><span data-stu-id="a1ee0-124">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="a1ee0-125">In dit voor beeld ziet u hoe u de `ConvertFrom-Json` cmdlet gebruikt om een JSON-bestand te converteren naar een aangepast Power shell-object.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-125">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="a1ee0-126">De opdracht gebruikt Get-Content cmdlet om de teken reeksen in een JSON-bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-126">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="a1ee0-127">Vervolgens wordt de pijplijn operator gebruikt voor het verzenden van de gescheiden teken reeks naar de `ConvertFrom-Json` cmdlet, die deze converteert naar een aangepast object.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-127">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

## <span data-ttu-id="a1ee0-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a1ee0-128">PARAMETERS</span></span>

### <span data-ttu-id="a1ee0-129">-Input object</span><span class="sxs-lookup"><span data-stu-id="a1ee0-129">-InputObject</span></span>

<span data-ttu-id="a1ee0-130">Hiermee geeft u de JSON-teken reeksen op die moeten worden geconverteerd naar JSON-objecten.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-130">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="a1ee0-131">Voer een variabele in die de teken reeks bevat, of typ een opdracht of expressie die de teken reeks ophaalt.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-131">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="a1ee0-132">U kunt ook een teken reeks aan een pipe door geven `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="a1ee0-132">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="a1ee0-133">De para meter **input object** is vereist, maar de waarde kan een lege teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-133">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="a1ee0-134">Wanneer het invoer object een lege teken reeks is, wordt `ConvertFrom-Json` er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-134">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="a1ee0-135">De **input object** -waarde kan niet zijn `$null` .</span><span class="sxs-lookup"><span data-stu-id="a1ee0-135">The **InputObject** value cannot be `$null`.</span></span>

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

### <span data-ttu-id="a1ee0-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a1ee0-136">CommonParameters</span></span>

<span data-ttu-id="a1ee0-137">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a1ee0-138">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a1ee0-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a1ee0-139">INVOER</span><span class="sxs-lookup"><span data-stu-id="a1ee0-139">INPUTS</span></span>

### <span data-ttu-id="a1ee0-140">System. String</span><span class="sxs-lookup"><span data-stu-id="a1ee0-140">System.String</span></span>

<span data-ttu-id="a1ee0-141">U kunt een JSON-teken reeks door sluizen naar `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="a1ee0-141">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="a1ee0-142">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a1ee0-142">OUTPUTS</span></span>

### <span data-ttu-id="a1ee0-143">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="a1ee0-143">PSCustomObject</span></span>

## <span data-ttu-id="a1ee0-144">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a1ee0-144">NOTES</span></span>

<span data-ttu-id="a1ee0-145">De `ConvertFrom-Json` cmdlet wordt geïmplementeerd met behulp van de [JavaScriptSerializer-klasse](/dotnet/api/system.web.script.serialization.javascriptserializer).</span><span class="sxs-lookup"><span data-stu-id="a1ee0-145">The `ConvertFrom-Json` cmdlet is implemented using the [JavaScriptSerializer class](/dotnet/api/system.web.script.serialization.javascriptserializer).</span></span>

## <span data-ttu-id="a1ee0-146">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a1ee0-146">RELATED LINKS</span></span>

<span data-ttu-id="a1ee0-147">[Een inleiding tot JavaScript Object Notation (JSON) in Java script en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="a1ee0-147">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="a1ee0-148">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="a1ee0-148">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="a1ee0-149">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="a1ee0-149">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="a1ee0-150">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="a1ee0-150">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
