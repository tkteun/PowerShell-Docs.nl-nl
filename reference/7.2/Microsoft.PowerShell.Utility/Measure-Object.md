---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 594837b2f85f4d5d5d4125d3f7c63ad2c8a16153
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706022"
---
# <span data-ttu-id="bc801-102">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="bc801-102">Measure-Object</span></span>

## <span data-ttu-id="bc801-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="bc801-103">SYNOPSIS</span></span>
<span data-ttu-id="bc801-104">Hiermee worden de numerieke eigenschappen van objecten en de tekens, woorden en regels in teken reeks objecten, zoals tekst bestanden, berekend.</span><span class="sxs-lookup"><span data-stu-id="bc801-104">Calculates the numeric properties of objects, and the characters, words, and lines in string objects, such as files of text.</span></span>

## <span data-ttu-id="bc801-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="bc801-105">SYNTAX</span></span>

### <span data-ttu-id="bc801-106">GenericMeasure (standaard)</span><span class="sxs-lookup"><span data-stu-id="bc801-106">GenericMeasure (Default)</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-StandardDeviation]
 [-Sum] [-AllStats] [-Average] [-Maximum] [-Minimum] [<CommonParameters>]
```

### <span data-ttu-id="bc801-107">TextMeasure</span><span class="sxs-lookup"><span data-stu-id="bc801-107">TextMeasure</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-Line] [-Word]
 [-Character] [-IgnoreWhiteSpace] [<CommonParameters>]
```

## <span data-ttu-id="bc801-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bc801-108">DESCRIPTION</span></span>

<span data-ttu-id="bc801-109">`Measure-Object`Met de cmdlet worden de eigenschapwaarden van bepaalde typen objecten berekend.</span><span class="sxs-lookup"><span data-stu-id="bc801-109">The `Measure-Object` cmdlet calculates the property values of certain types of object.</span></span>
<span data-ttu-id="bc801-110">`Measure-Object` voert drie soorten metingen uit, afhankelijk van de para meters in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="bc801-110">`Measure-Object` performs three types of measurements, depending on the parameters in the command.</span></span>

<span data-ttu-id="bc801-111">De `Measure-Object` cmdlet voert berekeningen uit op de eigenschaps waarden van objecten.</span><span class="sxs-lookup"><span data-stu-id="bc801-111">The `Measure-Object` cmdlet performs calculations on the property values of objects.</span></span> <span data-ttu-id="bc801-112">U kunt gebruiken `Measure-Object` om objecten te tellen of objecten te tellen met een opgegeven **eigenschap**.</span><span class="sxs-lookup"><span data-stu-id="bc801-112">You can use `Measure-Object` to count objects or count objects with a specified **Property**.</span></span> <span data-ttu-id="bc801-113">U kunt ook gebruiken `Measure-Object` om het **minimum**, **maximum**, **Sum**, **StandardDeviation** en het **gemiddelde** van numerieke waarden te berekenen.</span><span class="sxs-lookup"><span data-stu-id="bc801-113">You can also use `Measure-Object` to calculate the **Minimum**, **Maximum**, **Sum**, **StandardDeviation** and **Average** of numeric values.</span></span> <span data-ttu-id="bc801-114">Voor **teken reeks** objecten kunt u ook gebruiken `Measure-Object` om het aantal regels, woorden en tekens te tellen.</span><span class="sxs-lookup"><span data-stu-id="bc801-114">For **String** objects, you can also use `Measure-Object` to count the number of lines, words, and characters.</span></span>

## <span data-ttu-id="bc801-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="bc801-115">EXAMPLES</span></span>

### <span data-ttu-id="bc801-116">Voor beeld 1: het aantal bestanden en mappen in een map tellen</span><span class="sxs-lookup"><span data-stu-id="bc801-116">Example 1: Count the files and folders in a directory</span></span>

<span data-ttu-id="bc801-117">Met deze opdracht worden de bestanden en mappen in de huidige map geteld.</span><span class="sxs-lookup"><span data-stu-id="bc801-117">This command counts the files and folders in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object
```

### <span data-ttu-id="bc801-118">Voor beeld 2: de bestanden in een map meten</span><span class="sxs-lookup"><span data-stu-id="bc801-118">Example 2: Measure the files in a directory</span></span>

<span data-ttu-id="bc801-119">Met deze opdracht worden het **minimum**, **maximum** en de **som** van de grootte van alle bestanden in de huidige map en de gemiddelde grootte van een bestand in de map weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bc801-119">This command displays the **Minimum**, **Maximum**, and **Sum** of the sizes of all files in the current directory, and the average size of a file in the directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### <span data-ttu-id="bc801-120">Voor beeld 3: tekst in een tekst bestand meten</span><span class="sxs-lookup"><span data-stu-id="bc801-120">Example 3: Measure text in a text file</span></span>

<span data-ttu-id="bc801-121">Met deze opdracht wordt het aantal tekens, woorden en regels in het Text.txt bestand weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bc801-121">This command displays the number of characters, words, and lines in the Text.txt file.</span></span>
<span data-ttu-id="bc801-122">Zonder de **onbewerkte** para meter `Get-Content` voert het bestand uit als een matrix met regels.</span><span class="sxs-lookup"><span data-stu-id="bc801-122">Without the **Raw** parameter, `Get-Content` outputs the file as an array of lines.</span></span>

<span data-ttu-id="bc801-123">De eerste opdracht wordt gebruikt `Set-Content` om een standaard tekst toe te voegen aan een bestand.</span><span class="sxs-lookup"><span data-stu-id="bc801-123">The first command uses `Set-Content` to add some default text to a file.</span></span>

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### <span data-ttu-id="bc801-124">Voor beeld 4: objecten met een opgegeven eigenschap meten</span><span class="sxs-lookup"><span data-stu-id="bc801-124">Example 4: Measure objects containing a specified Property</span></span>

<span data-ttu-id="bc801-125">In dit voor beeld wordt het aantal objecten met een eigenschap **DisplayName** geteld.</span><span class="sxs-lookup"><span data-stu-id="bc801-125">This example counts the number of objects that have a **DisplayName** property.</span></span> <span data-ttu-id="bc801-126">Met de eerste twee opdrachten worden alle services en processen op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="bc801-126">The first two commands retrieve all the services and processes on the local machine.</span></span> <span data-ttu-id="bc801-127">Met de derde opdracht wordt het gecombineerde aantal services en processen geteld.</span><span class="sxs-lookup"><span data-stu-id="bc801-127">The third command counts the combined number of services and processes.</span></span> <span data-ttu-id="bc801-128">Met de laatste opdracht worden de twee verzamelingen gecombineerd en wordt het resultaat door sluizen naar `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="bc801-128">The last command combines the two collections and pipes the result to `Measure-Object`.</span></span>

<span data-ttu-id="bc801-129">Het object **System. Diagnostics. process** heeft geen eigenschap **DisplayName** en wordt wegge laten uit het laatste aantal.</span><span class="sxs-lookup"><span data-stu-id="bc801-129">The **System.Diagnostics.Process** object does not have a **DisplayName** property, and is left out of the final count.</span></span>

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### <span data-ttu-id="bc801-130">Voor beeld 5: de inhoud van een CSV-bestand meten</span><span class="sxs-lookup"><span data-stu-id="bc801-130">Example 5: Measure the contents of a CSV file</span></span>

<span data-ttu-id="bc801-131">Met deze opdracht wordt het gemiddelde aantal jaren van de service van de werk nemers van een bedrijf berekend.</span><span class="sxs-lookup"><span data-stu-id="bc801-131">This command calculates the average years of service of the employees of a company.</span></span>

<span data-ttu-id="bc801-132">Het `ServiceYrs.csv` bestand is een CSV-bestand dat het werknemers nummer en de dienst jaren van elke werk nemer bevat.</span><span class="sxs-lookup"><span data-stu-id="bc801-132">The `ServiceYrs.csv` file is a CSV file that contains the employee number and years of service of each employee.</span></span> <span data-ttu-id="bc801-133">De eerste rij in de tabel is een veldnamenrij van **EmpNo**, **jaar**.</span><span class="sxs-lookup"><span data-stu-id="bc801-133">The first row in the table is a header row of **EmpNo**, **Years**.</span></span>

<span data-ttu-id="bc801-134">Wanneer u gebruikt `Import-Csv` om het bestand te importeren, is het resultaat een **PSCustomObject** met notitie-eigenschappen van **EmpNo** en **jaren**.</span><span class="sxs-lookup"><span data-stu-id="bc801-134">When you use `Import-Csv` to import the file, the result is a **PSCustomObject** with note properties of **EmpNo** and **Years**.</span></span>
<span data-ttu-id="bc801-135">U kunt gebruiken `Measure-Object` voor het berekenen van de waarden van deze eigenschappen, net als elke andere eigenschap van een object.</span><span class="sxs-lookup"><span data-stu-id="bc801-135">You can use `Measure-Object` to calculate the values of these properties, just like any other property of an object.</span></span>

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### <span data-ttu-id="bc801-136">Voor beeld 6: Boole-waarden meten</span><span class="sxs-lookup"><span data-stu-id="bc801-136">Example 6: Measure Boolean values</span></span>

<span data-ttu-id="bc801-137">In dit voor beeld wordt gedemonstreerd hoe `Measure-Object` Booleaanse waarden kunnen worden gemeten.</span><span class="sxs-lookup"><span data-stu-id="bc801-137">This example demonstrates how the `Measure-Object` can measure Boolean values.</span></span>
<span data-ttu-id="bc801-138">In dit geval wordt de **PSIsContainer** **Boolean** -eigenschap gebruikt om het incidenten van mappen (versus bestanden) in de huidige map te meten.</span><span class="sxs-lookup"><span data-stu-id="bc801-138">In this case, it uses the **PSIsContainer** **Boolean** property to measure the incidence of folders (vs. files) in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### <span data-ttu-id="bc801-139">Voor beeld 7: teken reeksen meten</span><span class="sxs-lookup"><span data-stu-id="bc801-139">Example 7: Measure strings</span></span>

<span data-ttu-id="bc801-140">In het volgende voor beeld wordt het aantal regels, eerste één teken reeks, in meerdere teken reeksen gemeten.</span><span class="sxs-lookup"><span data-stu-id="bc801-140">The following example measures the number of lines, first a single string, then across several strings.</span></span> <span data-ttu-id="bc801-141">Het teken voor een nieuwe regel <code>\`n</code> scheidt reeksen in meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="bc801-141">The newline character <code>\`n</code> separates strings into multiple lines.</span></span>

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

### <span data-ttu-id="bc801-142">Voor beeld 8: alle waarden meten</span><span class="sxs-lookup"><span data-stu-id="bc801-142">Example 8: Measure all the values</span></span>

<span data-ttu-id="bc801-143">Vanaf Power shell 6 kunt u met de para meter **AllStats** van `Measure-Object` alle statistieken tegelijk meten.</span><span class="sxs-lookup"><span data-stu-id="bc801-143">Beginning in PowerShell 6, the **AllStats** parameter of `Measure-Object` allows you to measure all the statistics together.</span></span>

```powershell
1..5 | Measure-Object -AllStats
```

```output
Count             : 5
Average           : 3
Sum               : 15
Maximum           : 5
Minimum           : 1
StandardDeviation : 1.58113883008419
Property          :
```

### <span data-ttu-id="bc801-144">Voor beeld 9: meten met behulp van script Block-eigenschappen</span><span class="sxs-lookup"><span data-stu-id="bc801-144">Example 9: Measure using scriptblock properties</span></span>

<span data-ttu-id="bc801-145">Vanaf Power shell 6 `Measure-Object` ondersteunt **script Block** -eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="bc801-145">Beginning in PowerShell 6, `Measure-Object` supports **ScriptBlock** properties.</span></span> <span data-ttu-id="bc801-146">In het volgende voor beeld ziet u hoe u een eigenschap **script Block** kunt gebruiken om de grootte, in mega bytes, van alle bestanden in een map te bepalen.</span><span class="sxs-lookup"><span data-stu-id="bc801-146">The following example demonstrates how to use a **ScriptBlock** property to determine the size, in MegaBytes, of all the files in a directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Sum {$_.Length/1MB}
```

### <span data-ttu-id="bc801-147">Voor beeld 10: hashtabellen meten</span><span class="sxs-lookup"><span data-stu-id="bc801-147">Example 10: Measure hashtables</span></span>

<span data-ttu-id="bc801-148">Vanaf Power shell 6 `Measure-Object` ondersteunt meting van de **hash** -invoer.</span><span class="sxs-lookup"><span data-stu-id="bc801-148">Beginning in PowerShell 6, `Measure-Object` supports measurement of **hashtable** input.</span></span> <span data-ttu-id="bc801-149">In het volgende voor beeld wordt de grootste waarde bepaald voor de `num` sleutel van 3 **Hashtable** -objecten.</span><span class="sxs-lookup"><span data-stu-id="bc801-149">The following example determines the largest value for the `num` key of 3 **hashtable** objects.</span></span>

```powershell
@{num=3}, @{num=4}, @{num=5} | Measure-Object -Maximum Num
```

```output
Count             : 3
Average           :
Sum               :
Maximum           : 5
Minimum           :
StandardDeviation :
Property          : num
```

### <span data-ttu-id="bc801-150">Voor beeld 11: de standaard afwijking meten</span><span class="sxs-lookup"><span data-stu-id="bc801-150">Example 11: Measure the Standard Deviation</span></span>

<span data-ttu-id="bc801-151">Vanaf Power shell 6 `Measure-Object` ondersteunt de `-StandardDeviation` para meter.</span><span class="sxs-lookup"><span data-stu-id="bc801-151">Beginning in PowerShell 6, `Measure-Object` supports the `-StandardDeviation` parameter.</span></span> <span data-ttu-id="bc801-152">In het volgende voor beeld wordt de *standaard afwijking* bepaald voor de CPU die wordt gebruikt door alle processen.</span><span class="sxs-lookup"><span data-stu-id="bc801-152">The following example determines the *standard deviation* for the CPU used by all processes.</span></span> <span data-ttu-id="bc801-153">Een grote afwijkingen duiden op een klein aantal processen die de meeste CPU gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bc801-153">A large deviation would indicate a small number of processes consuming the most CPU.</span></span>

```powershell
Get-Process | Measure-Object -Average -StandardDeviation CPU
```

```output
Count             : 303
Average           : 163.032384488449
Sum               :
Maximum           :
Minimum           :
StandardDeviation : 859.444048419069
Property          : CPU
```

### <span data-ttu-id="bc801-154">Voor beeld 12: meten met behulp van joker tekens</span><span class="sxs-lookup"><span data-stu-id="bc801-154">Example 12: Measure using wildcards</span></span>

<span data-ttu-id="bc801-155">Vanaf Power shell 6 `Measure-Object` ondersteunt het meten van objecten met behulp van joker tekens in eigenschapnamen.</span><span class="sxs-lookup"><span data-stu-id="bc801-155">Beginning in PowerShell 6, `Measure-Object` supports measurement of objects by using wildcards in property names.</span></span> <span data-ttu-id="bc801-156">In het volgende voor beeld wordt het maximum van elk type wisselbaar geheugen gebruikt voor een reeks processen.</span><span class="sxs-lookup"><span data-stu-id="bc801-156">The following example determines the maximum of any type of paged memory usage among a set of processes.</span></span>

```powershell
Get-Process | Measure-Object -Maximum *paged*memory*size
```

```output
Count             : 303
Average           :
Sum               :
Maximum           : 735784
Minimum           :
StandardDeviation :
Property          : NonpagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 352104448
Minimum           :
StandardDeviation :
Property          : PagedMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 2201968
Minimum           :
StandardDeviation :
Property          : PagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 719032320
Minimum           :
StandardDeviation :
Property          : PeakPagedMemorySize
```

## <span data-ttu-id="bc801-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bc801-157">PARAMETERS</span></span>

### <span data-ttu-id="bc801-158">-Gemiddeld</span><span class="sxs-lookup"><span data-stu-id="bc801-158">-Average</span></span>

<span data-ttu-id="bc801-159">Geeft aan dat de cmdlet de gemiddelde waarde van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="bc801-159">Indicates that the cmdlet displays the average value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc801-160">-Teken</span><span class="sxs-lookup"><span data-stu-id="bc801-160">-Character</span></span>

<span data-ttu-id="bc801-161">Geeft aan dat de cmdlet het aantal tekens in de invoer objecten telt.</span><span class="sxs-lookup"><span data-stu-id="bc801-161">Indicates that the cmdlet counts the number of characters in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="bc801-162">Het **woord**, **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="bc801-162">The **Word**, **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="bc801-163">Zie voor beeld 7.</span><span class="sxs-lookup"><span data-stu-id="bc801-163">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc801-164">-IgnoreWhiteSpace</span><span class="sxs-lookup"><span data-stu-id="bc801-164">-IgnoreWhiteSpace</span></span>

<span data-ttu-id="bc801-165">Geeft aan dat de cmdlet witruimte in het aantal tekens negeert.</span><span class="sxs-lookup"><span data-stu-id="bc801-165">Indicates that the cmdlet ignores white space in character counts.</span></span>
<span data-ttu-id="bc801-166">Standaard wordt witruimte niet genegeerd.</span><span class="sxs-lookup"><span data-stu-id="bc801-166">By default, white space is not ignored.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc801-167">-Input object</span><span class="sxs-lookup"><span data-stu-id="bc801-167">-InputObject</span></span>

<span data-ttu-id="bc801-168">Geeft aan welke objecten moeten worden gemeten.</span><span class="sxs-lookup"><span data-stu-id="bc801-168">Specifies the objects to be measured.</span></span>
<span data-ttu-id="bc801-169">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="bc801-169">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="bc801-170">Wanneer u de para meter **input object** gebruikt in `Measure-Object` plaats van de resultaten van de pijpleiding opdracht, `Measure-Object` wordt de waarde van **input object** behandeld als een enkel object.</span><span class="sxs-lookup"><span data-stu-id="bc801-170">When you use the **InputObject** parameter with `Measure-Object`, instead of piping command results to `Measure-Object`, the **InputObject** value is treated as a single object.</span></span>

<span data-ttu-id="bc801-171">Het is raadzaam `Measure-Object` om in de pijp lijn te gebruiken als u een verzameling objecten wilt meten op basis van het feit of de objecten specifieke waarden in gedefinieerde eigenschappen hebben.</span><span class="sxs-lookup"><span data-stu-id="bc801-171">It is recommended that you use `Measure-Object` in the pipeline if you want to measure a collection of objects based on whether the objects have specific values in defined properties.</span></span>

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

### <span data-ttu-id="bc801-172">-Regel</span><span class="sxs-lookup"><span data-stu-id="bc801-172">-Line</span></span>

<span data-ttu-id="bc801-173">Geeft aan dat de cmdlet het aantal regels in de invoer objecten telt.</span><span class="sxs-lookup"><span data-stu-id="bc801-173">Indicates that the cmdlet counts the number of lines in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="bc801-174">Het **woord**, **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="bc801-174">The **Word**, **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="bc801-175">Zie voor beeld 7.</span><span class="sxs-lookup"><span data-stu-id="bc801-175">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc801-176">-Maximum</span><span class="sxs-lookup"><span data-stu-id="bc801-176">-Maximum</span></span>

<span data-ttu-id="bc801-177">Geeft aan dat de cmdlet de maximum waarde van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="bc801-177">Indicates that the cmdlet displays the maximum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc801-178">-Minimum</span><span class="sxs-lookup"><span data-stu-id="bc801-178">-Minimum</span></span>

<span data-ttu-id="bc801-179">Geeft aan dat de cmdlet de minimale waarde van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="bc801-179">Indicates that the cmdlet displays the minimum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc801-180">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="bc801-180">-Property</span></span>

<span data-ttu-id="bc801-181">Hiermee geeft u een of meer eigenschappen op die moeten worden gemeten.</span><span class="sxs-lookup"><span data-stu-id="bc801-181">Specifies one or more properties to measure.</span></span> <span data-ttu-id="bc801-182">Als u geen andere maat regelen opgeeft, `Measure-Object` telt het aantal objecten dat de door u opgegeven eigenschappen bevat.</span><span class="sxs-lookup"><span data-stu-id="bc801-182">If you do not specify any other measures, `Measure-Object` counts the objects that have the properties you specify.</span></span>

<span data-ttu-id="bc801-183">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="bc801-183">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="bc801-184">De berekende eigenschap moet een script blok zijn.</span><span class="sxs-lookup"><span data-stu-id="bc801-184">The calculated property must be a script block.</span></span> <span data-ttu-id="bc801-185">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bc801-185">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bc801-186">-StandardDeviation</span><span class="sxs-lookup"><span data-stu-id="bc801-186">-StandardDeviation</span></span>

<span data-ttu-id="bc801-187">Geeft aan dat de cmdlet de standaard afwijking van de waarden van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="bc801-187">Indicates that the cmdlet displays the standard deviation of the values of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc801-188">-Sum</span><span class="sxs-lookup"><span data-stu-id="bc801-188">-Sum</span></span>

<span data-ttu-id="bc801-189">Geeft aan dat de cmdlet de som van de waarden van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="bc801-189">Indicates that the cmdlet displays the sum of the values of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc801-190">-AllStats</span><span class="sxs-lookup"><span data-stu-id="bc801-190">-AllStats</span></span>

<span data-ttu-id="bc801-191">Geeft aan dat de cmdlet alle statistieken van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="bc801-191">Indicates that the cmdlet displays all the statistics of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc801-192">-Word</span><span class="sxs-lookup"><span data-stu-id="bc801-192">-Word</span></span>

<span data-ttu-id="bc801-193">Geeft aan dat de cmdlet het aantal woorden in de invoer objecten telt.</span><span class="sxs-lookup"><span data-stu-id="bc801-193">Indicates that the cmdlet counts the number of words in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="bc801-194">Het **woord**, **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="bc801-194">The **Word**, **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="bc801-195">Zie voor beeld 7.</span><span class="sxs-lookup"><span data-stu-id="bc801-195">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc801-196">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bc801-196">CommonParameters</span></span>

<span data-ttu-id="bc801-197">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bc801-197">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bc801-198">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bc801-198">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bc801-199">INVOER</span><span class="sxs-lookup"><span data-stu-id="bc801-199">INPUTS</span></span>

### <span data-ttu-id="bc801-200">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="bc801-200">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="bc801-201">U kunt objecten door sluizen naar `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="bc801-201">You can pipe objects to `Measure-Object`.</span></span>

## <span data-ttu-id="bc801-202">UITVOER</span><span class="sxs-lookup"><span data-stu-id="bc801-202">OUTPUTS</span></span>

### <span data-ttu-id="bc801-203">Micro soft. Power shell. commands. GenericMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="bc801-203">Microsoft.PowerShell.Commands.GenericMeasureInfo</span></span>

### <span data-ttu-id="bc801-204">Micro soft. Power shell. commands. TextMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="bc801-204">Microsoft.PowerShell.Commands.TextMeasureInfo</span></span>

<span data-ttu-id="bc801-205">Als u de para meter **Word** gebruikt, `Measure-Object` wordt een **TextMeasureInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bc801-205">If you use the **Word** parameter, `Measure-Object` returns a **TextMeasureInfo** object.</span></span>
<span data-ttu-id="bc801-206">Anders wordt een **GenericMeasureInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bc801-206">Otherwise, it returns a **GenericMeasureInfo** object.</span></span>

## <span data-ttu-id="bc801-207">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="bc801-207">NOTES</span></span>

## <span data-ttu-id="bc801-208">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="bc801-208">RELATED LINKS</span></span>

[<span data-ttu-id="bc801-209">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="bc801-209">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="bc801-210">Compare-object</span><span class="sxs-lookup"><span data-stu-id="bc801-210">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="bc801-211">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="bc801-211">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="bc801-212">Groep-object</span><span class="sxs-lookup"><span data-stu-id="bc801-212">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="bc801-213">New-Object</span><span class="sxs-lookup"><span data-stu-id="bc801-213">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="bc801-214">Select-Object</span><span class="sxs-lookup"><span data-stu-id="bc801-214">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="bc801-215">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="bc801-215">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="bc801-216">T-object</span><span class="sxs-lookup"><span data-stu-id="bc801-216">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="bc801-217">Where-object</span><span class="sxs-lookup"><span data-stu-id="bc801-217">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
