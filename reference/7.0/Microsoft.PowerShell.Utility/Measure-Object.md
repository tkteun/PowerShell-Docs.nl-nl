---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 37fa83b804516cacf0c1cc1b0a2f4d6b5949178b
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251792"
---
# <span data-ttu-id="7e538-103">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="7e538-103">Measure-Object</span></span>

## <span data-ttu-id="7e538-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7e538-104">SYNOPSIS</span></span>
<span data-ttu-id="7e538-105">Hiermee worden de numerieke eigenschappen van objecten en de tekens, woorden en regels in teken reeks objecten, zoals tekst bestanden, berekend.</span><span class="sxs-lookup"><span data-stu-id="7e538-105">Calculates the numeric properties of objects, and the characters, words, and lines in string objects, such as files of text.</span></span>

## <span data-ttu-id="7e538-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7e538-106">SYNTAX</span></span>

### <span data-ttu-id="7e538-107">GenericMeasure (standaard)</span><span class="sxs-lookup"><span data-stu-id="7e538-107">GenericMeasure (Default)</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-StandardDeviation]
 [-Sum] [-AllStats] [-Average] [-Maximum] [-Minimum] [<CommonParameters>]
```

### <span data-ttu-id="7e538-108">TextMeasure</span><span class="sxs-lookup"><span data-stu-id="7e538-108">TextMeasure</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-Line] [-Word]
 [-Character] [-IgnoreWhiteSpace] [<CommonParameters>]
```

## <span data-ttu-id="7e538-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7e538-109">DESCRIPTION</span></span>

<span data-ttu-id="7e538-110">`Measure-Object`Met de cmdlet worden de eigenschapwaarden van bepaalde typen objecten berekend.</span><span class="sxs-lookup"><span data-stu-id="7e538-110">The `Measure-Object` cmdlet calculates the property values of certain types of object.</span></span>
<span data-ttu-id="7e538-111">`Measure-Object` voert drie soorten metingen uit, afhankelijk van de para meters in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7e538-111">`Measure-Object` performs three types of measurements, depending on the parameters in the command.</span></span>

<span data-ttu-id="7e538-112">De `Measure-Object` cmdlet voert berekeningen uit op de eigenschaps waarden van objecten.</span><span class="sxs-lookup"><span data-stu-id="7e538-112">The `Measure-Object` cmdlet performs calculations on the property values of objects.</span></span> <span data-ttu-id="7e538-113">U kunt gebruiken `Measure-Object` om objecten te tellen of objecten te tellen met een opgegeven **eigenschap**.</span><span class="sxs-lookup"><span data-stu-id="7e538-113">You can use `Measure-Object` to count objects or count objects with a specified **Property**.</span></span> <span data-ttu-id="7e538-114">U kunt ook gebruiken `Measure-Object` om het **minimum** , **maximum** , **Sum** , **StandardDeviation** en het **gemiddelde** van numerieke waarden te berekenen.</span><span class="sxs-lookup"><span data-stu-id="7e538-114">You can also use `Measure-Object` to calculate the **Minimum** , **Maximum** , **Sum** , **StandardDeviation** and **Average** of numeric values.</span></span> <span data-ttu-id="7e538-115">Voor **teken reeks** objecten kunt u ook gebruiken `Measure-Object` om het aantal regels, woorden en tekens te tellen.</span><span class="sxs-lookup"><span data-stu-id="7e538-115">For **String** objects, you can also use `Measure-Object` to count the number of lines, words, and characters.</span></span>

## <span data-ttu-id="7e538-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7e538-116">EXAMPLES</span></span>

### <span data-ttu-id="7e538-117">Voor beeld 1: het aantal bestanden en mappen in een map tellen</span><span class="sxs-lookup"><span data-stu-id="7e538-117">Example 1: Count the files and folders in a directory</span></span>

<span data-ttu-id="7e538-118">Met deze opdracht worden de bestanden en mappen in de huidige map geteld.</span><span class="sxs-lookup"><span data-stu-id="7e538-118">This command counts the files and folders in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object
```

### <span data-ttu-id="7e538-119">Voor beeld 2: de bestanden in een map meten</span><span class="sxs-lookup"><span data-stu-id="7e538-119">Example 2: Measure the files in a directory</span></span>

<span data-ttu-id="7e538-120">Met deze opdracht worden het **minimum** , **maximum** en de **som** van de grootte van alle bestanden in de huidige map en de gemiddelde grootte van een bestand in de map weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7e538-120">This command displays the **Minimum** , **Maximum** , and **Sum** of the sizes of all files in the current directory, and the average size of a file in the directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### <span data-ttu-id="7e538-121">Voor beeld 3: tekst in een tekst bestand meten</span><span class="sxs-lookup"><span data-stu-id="7e538-121">Example 3: Measure text in a text file</span></span>

<span data-ttu-id="7e538-122">Met deze opdracht wordt het aantal tekens, woorden en regels in het Text.txt bestand weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7e538-122">This command displays the number of characters, words, and lines in the Text.txt file.</span></span>
<span data-ttu-id="7e538-123">Zonder de **onbewerkte** para meter `Get-Content` voert het bestand uit als een matrix met regels.</span><span class="sxs-lookup"><span data-stu-id="7e538-123">Without the **Raw** parameter, `Get-Content` outputs the file as an array of lines.</span></span>

<span data-ttu-id="7e538-124">De eerste opdracht wordt gebruikt `Set-Content` om een standaard tekst toe te voegen aan een bestand.</span><span class="sxs-lookup"><span data-stu-id="7e538-124">The first command uses `Set-Content` to add some default text to a file.</span></span>

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### <span data-ttu-id="7e538-125">Voor beeld 4: objecten met een opgegeven eigenschap meten</span><span class="sxs-lookup"><span data-stu-id="7e538-125">Example 4: Measure objects containing a specified Property</span></span>

<span data-ttu-id="7e538-126">In dit voor beeld wordt het aantal objecten met een eigenschap **DisplayName** geteld.</span><span class="sxs-lookup"><span data-stu-id="7e538-126">This example counts the number of objects that have a **DisplayName** property.</span></span> <span data-ttu-id="7e538-127">Met de eerste twee opdrachten worden alle services en processen op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e538-127">The first two commands retrieve all the services and processes on the local machine.</span></span> <span data-ttu-id="7e538-128">Met de derde opdracht wordt het gecombineerde aantal services en processen geteld.</span><span class="sxs-lookup"><span data-stu-id="7e538-128">The third command counts the combined number of services and processes.</span></span> <span data-ttu-id="7e538-129">Met de laatste opdracht worden de twee verzamelingen gecombineerd en wordt het resultaat door sluizen naar `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="7e538-129">The last command combines the two collections and pipes the result to `Measure-Object`.</span></span>

<span data-ttu-id="7e538-130">Het object **System. Diagnostics. process** heeft geen eigenschap **DisplayName** en wordt wegge laten uit het laatste aantal.</span><span class="sxs-lookup"><span data-stu-id="7e538-130">The **System.Diagnostics.Process** object does not have a **DisplayName** property, and is left out of the final count.</span></span>

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

### <span data-ttu-id="7e538-131">Voor beeld 5: de inhoud van een CSV-bestand meten</span><span class="sxs-lookup"><span data-stu-id="7e538-131">Example 5: Measure the contents of a CSV file</span></span>

<span data-ttu-id="7e538-132">Met deze opdracht wordt het gemiddelde aantal jaren van de service van de werk nemers van een bedrijf berekend.</span><span class="sxs-lookup"><span data-stu-id="7e538-132">This command calculates the average years of service of the employees of a company.</span></span>

<span data-ttu-id="7e538-133">Het `ServiceYrs.csv` bestand is een CSV-bestand dat het werknemers nummer en de dienst jaren van elke werk nemer bevat.</span><span class="sxs-lookup"><span data-stu-id="7e538-133">The `ServiceYrs.csv` file is a CSV file that contains the employee number and years of service of each employee.</span></span> <span data-ttu-id="7e538-134">De eerste rij in de tabel is een veldnamenrij van **EmpNo** , **jaar**.</span><span class="sxs-lookup"><span data-stu-id="7e538-134">The first row in the table is a header row of **EmpNo** , **Years**.</span></span>

<span data-ttu-id="7e538-135">Wanneer u gebruikt `Import-Csv` om het bestand te importeren, is het resultaat een **PSCustomObject** met notitie-eigenschappen van **EmpNo** en **jaren**.</span><span class="sxs-lookup"><span data-stu-id="7e538-135">When you use `Import-Csv` to import the file, the result is a **PSCustomObject** with note properties of **EmpNo** and **Years**.</span></span>
<span data-ttu-id="7e538-136">U kunt gebruiken `Measure-Object` voor het berekenen van de waarden van deze eigenschappen, net als elke andere eigenschap van een object.</span><span class="sxs-lookup"><span data-stu-id="7e538-136">You can use `Measure-Object` to calculate the values of these properties, just like any other property of an object.</span></span>

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### <span data-ttu-id="7e538-137">Voor beeld 6: Boole-waarden meten</span><span class="sxs-lookup"><span data-stu-id="7e538-137">Example 6: Measure Boolean values</span></span>

<span data-ttu-id="7e538-138">In dit voor beeld wordt gedemonstreerd hoe `Measure-Object` Booleaanse waarden kunnen worden gemeten.</span><span class="sxs-lookup"><span data-stu-id="7e538-138">This example demonstrates how the `Measure-Object` can measure Boolean values.</span></span>
<span data-ttu-id="7e538-139">In dit geval wordt de **PSIsContainer** **Boolean** -eigenschap gebruikt om het incidenten van mappen (versus bestanden) in de huidige map te meten.</span><span class="sxs-lookup"><span data-stu-id="7e538-139">In this case, it uses the **PSIsContainer** **Boolean** property to measure the incidence of folders (vs. files) in the current directory.</span></span>

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

### <span data-ttu-id="7e538-140">Voor beeld 7: teken reeksen meten</span><span class="sxs-lookup"><span data-stu-id="7e538-140">Example 7: Measure strings</span></span>

<span data-ttu-id="7e538-141">In het volgende voor beeld wordt het aantal regels, eerste één teken reeks, in meerdere teken reeksen gemeten.</span><span class="sxs-lookup"><span data-stu-id="7e538-141">The following example measures the number of lines, first a single string, then across several strings.</span></span> <span data-ttu-id="7e538-142">Het teken voor een nieuwe regel <code>\`n</code> scheidt reeksen in meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="7e538-142">The newline character <code>\`n</code> separates strings into multiple lines.</span></span>

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

### <span data-ttu-id="7e538-143">Voor beeld 8: alle waarden meten</span><span class="sxs-lookup"><span data-stu-id="7e538-143">Example 8: Measure all the values</span></span>

<span data-ttu-id="7e538-144">Vanaf Power shell 6 kunt u met de para meter **AllStats** van `Measure-Object` alle statistieken tegelijk meten.</span><span class="sxs-lookup"><span data-stu-id="7e538-144">Beginning in PowerShell 6, the **AllStats** parameter of `Measure-Object` allows you to measure all the statistics together.</span></span>

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

### <span data-ttu-id="7e538-145">Voor beeld 9: meten met behulp van script Block-eigenschappen</span><span class="sxs-lookup"><span data-stu-id="7e538-145">Example 9: Measure using scriptblock properties</span></span>

<span data-ttu-id="7e538-146">Vanaf Power shell 6 `Measure-Object` ondersteunt **script Block** -eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="7e538-146">Beginning in PowerShell 6, `Measure-Object` supports **ScriptBlock** properties.</span></span> <span data-ttu-id="7e538-147">In het volgende voor beeld ziet u hoe u een eigenschap **script Block** kunt gebruiken om de grootte, in mega bytes, van alle bestanden in een map te bepalen.</span><span class="sxs-lookup"><span data-stu-id="7e538-147">The following example demonstrates how to use a **ScriptBlock** property to determine the size, in MegaBytes, of all the files in a directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Sum {$_.Length/1MB}
```

### <span data-ttu-id="7e538-148">Voor beeld 10: hashtabellen meten</span><span class="sxs-lookup"><span data-stu-id="7e538-148">Example 10: Measure hashtables</span></span>

<span data-ttu-id="7e538-149">Vanaf Power shell 6 `Measure-Object` ondersteunt meting van de **hash** -invoer.</span><span class="sxs-lookup"><span data-stu-id="7e538-149">Beginning in PowerShell 6, `Measure-Object` supports measurement of **hashtable** input.</span></span> <span data-ttu-id="7e538-150">In het volgende voor beeld wordt de grootste waarde bepaald voor de `num` sleutel van 3 **Hashtable** -objecten.</span><span class="sxs-lookup"><span data-stu-id="7e538-150">The following example determines the largest value for the `num` key of 3 **hashtable** objects.</span></span>

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

### <span data-ttu-id="7e538-151">Voor beeld 11: de standaard afwijking meten</span><span class="sxs-lookup"><span data-stu-id="7e538-151">Example 11: Measure the Standard Deviation</span></span>

<span data-ttu-id="7e538-152">Vanaf Power shell 6 `Measure-Object` ondersteunt de `-StandardDeviation` para meter.</span><span class="sxs-lookup"><span data-stu-id="7e538-152">Beginning in PowerShell 6, `Measure-Object` supports the `-StandardDeviation` parameter.</span></span> <span data-ttu-id="7e538-153">In het volgende voor beeld wordt de *standaard afwijking* bepaald voor de CPU die wordt gebruikt door alle processen.</span><span class="sxs-lookup"><span data-stu-id="7e538-153">The following example determines the *standard deviation* for the CPU used by all processes.</span></span> <span data-ttu-id="7e538-154">Een grote afwijkingen duiden op een klein aantal processen die de meeste CPU gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7e538-154">A large deviation would indicate a small number of processes consuming the most CPU.</span></span>

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

### <span data-ttu-id="7e538-155">Voor beeld 12: meten met behulp van joker tekens</span><span class="sxs-lookup"><span data-stu-id="7e538-155">Example 12: Measure using wildcards</span></span>

<span data-ttu-id="7e538-156">Vanaf Power shell 6 `Measure-Object` ondersteunt het meten van objecten met behulp van joker tekens in eigenschapnamen.</span><span class="sxs-lookup"><span data-stu-id="7e538-156">Beginning in PowerShell 6, `Measure-Object` supports measurement of objects by using wildcards in property names.</span></span> <span data-ttu-id="7e538-157">In het volgende voor beeld wordt het maximum van elk type wisselbaar geheugen gebruikt voor een reeks processen.</span><span class="sxs-lookup"><span data-stu-id="7e538-157">The following example determines the maximum of any type of paged memory usage among a set of processes.</span></span>

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

## <span data-ttu-id="7e538-158">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7e538-158">PARAMETERS</span></span>

### <span data-ttu-id="7e538-159">-Gemiddeld</span><span class="sxs-lookup"><span data-stu-id="7e538-159">-Average</span></span>

<span data-ttu-id="7e538-160">Geeft aan dat de cmdlet de gemiddelde waarde van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="7e538-160">Indicates that the cmdlet displays the average value of the specified properties.</span></span>

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

### <span data-ttu-id="7e538-161">-Teken</span><span class="sxs-lookup"><span data-stu-id="7e538-161">-Character</span></span>

<span data-ttu-id="7e538-162">Geeft aan dat de cmdlet het aantal tekens in de invoer objecten telt.</span><span class="sxs-lookup"><span data-stu-id="7e538-162">Indicates that the cmdlet counts the number of characters in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="7e538-163">Het **woord** , **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="7e538-163">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="7e538-164">Zie voor beeld 7.</span><span class="sxs-lookup"><span data-stu-id="7e538-164">See Example 7.</span></span>

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

### <span data-ttu-id="7e538-165">-IgnoreWhiteSpace</span><span class="sxs-lookup"><span data-stu-id="7e538-165">-IgnoreWhiteSpace</span></span>

<span data-ttu-id="7e538-166">Geeft aan dat de cmdlet witruimte in het aantal tekens negeert.</span><span class="sxs-lookup"><span data-stu-id="7e538-166">Indicates that the cmdlet ignores white space in character counts.</span></span>
<span data-ttu-id="7e538-167">Standaard wordt witruimte niet genegeerd.</span><span class="sxs-lookup"><span data-stu-id="7e538-167">By default, white space is not ignored.</span></span>

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

### <span data-ttu-id="7e538-168">-Input object</span><span class="sxs-lookup"><span data-stu-id="7e538-168">-InputObject</span></span>

<span data-ttu-id="7e538-169">Geeft aan welke objecten moeten worden gemeten.</span><span class="sxs-lookup"><span data-stu-id="7e538-169">Specifies the objects to be measured.</span></span>
<span data-ttu-id="7e538-170">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e538-170">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="7e538-171">Wanneer u de para meter **input object** gebruikt in `Measure-Object` plaats van de resultaten van de pijpleiding opdracht, `Measure-Object` wordt de waarde van **input object** behandeld als een enkel object.</span><span class="sxs-lookup"><span data-stu-id="7e538-171">When you use the **InputObject** parameter with `Measure-Object`, instead of piping command results to `Measure-Object`, the **InputObject** value is treated as a single object.</span></span>

<span data-ttu-id="7e538-172">Het is raadzaam `Measure-Object` om in de pijp lijn te gebruiken als u een verzameling objecten wilt meten op basis van het feit of de objecten specifieke waarden in gedefinieerde eigenschappen hebben.</span><span class="sxs-lookup"><span data-stu-id="7e538-172">It is recommended that you use `Measure-Object` in the pipeline if you want to measure a collection of objects based on whether the objects have specific values in defined properties.</span></span>

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

### <span data-ttu-id="7e538-173">-Regel</span><span class="sxs-lookup"><span data-stu-id="7e538-173">-Line</span></span>

<span data-ttu-id="7e538-174">Geeft aan dat de cmdlet het aantal regels in de invoer objecten telt.</span><span class="sxs-lookup"><span data-stu-id="7e538-174">Indicates that the cmdlet counts the number of lines in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="7e538-175">Het **woord** , **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="7e538-175">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="7e538-176">Zie voor beeld 7.</span><span class="sxs-lookup"><span data-stu-id="7e538-176">See Example 7.</span></span>

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

### <span data-ttu-id="7e538-177">-Maximum</span><span class="sxs-lookup"><span data-stu-id="7e538-177">-Maximum</span></span>

<span data-ttu-id="7e538-178">Geeft aan dat de cmdlet de maximum waarde van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="7e538-178">Indicates that the cmdlet displays the maximum value of the specified properties.</span></span>

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

### <span data-ttu-id="7e538-179">-Minimum</span><span class="sxs-lookup"><span data-stu-id="7e538-179">-Minimum</span></span>

<span data-ttu-id="7e538-180">Geeft aan dat de cmdlet de minimale waarde van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="7e538-180">Indicates that the cmdlet displays the minimum value of the specified properties.</span></span>

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

### <span data-ttu-id="7e538-181">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="7e538-181">-Property</span></span>

<span data-ttu-id="7e538-182">Hiermee geeft u een of meer eigenschappen op die moeten worden gemeten.</span><span class="sxs-lookup"><span data-stu-id="7e538-182">Specifies one or more properties to measure.</span></span> <span data-ttu-id="7e538-183">Als u geen andere maat regelen opgeeft, `Measure-Object` telt het aantal objecten dat de door u opgegeven eigenschappen bevat.</span><span class="sxs-lookup"><span data-stu-id="7e538-183">If you do not specify any other measures, `Measure-Object` counts the objects that have the properties you specify.</span></span>

<span data-ttu-id="7e538-184">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="7e538-184">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="7e538-185">De berekende eigenschap moet een script blok zijn.</span><span class="sxs-lookup"><span data-stu-id="7e538-185">The calculated property must be a script block.</span></span> <span data-ttu-id="7e538-186">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7e538-186">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="7e538-187">-StandardDeviation</span><span class="sxs-lookup"><span data-stu-id="7e538-187">-StandardDeviation</span></span>

<span data-ttu-id="7e538-188">Geeft aan dat de cmdlet de standaard afwijking van de waarden van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="7e538-188">Indicates that the cmdlet displays the standard deviation of the values of the specified properties.</span></span>

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

### <span data-ttu-id="7e538-189">-Sum</span><span class="sxs-lookup"><span data-stu-id="7e538-189">-Sum</span></span>

<span data-ttu-id="7e538-190">Geeft aan dat de cmdlet de som van de waarden van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="7e538-190">Indicates that the cmdlet displays the sum of the values of the specified properties.</span></span>

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

### <span data-ttu-id="7e538-191">-AllStats</span><span class="sxs-lookup"><span data-stu-id="7e538-191">-AllStats</span></span>

<span data-ttu-id="7e538-192">Geeft aan dat de cmdlet alle statistieken van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="7e538-192">Indicates that the cmdlet displays all the statistics of the specified properties.</span></span>

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

### <span data-ttu-id="7e538-193">-Word</span><span class="sxs-lookup"><span data-stu-id="7e538-193">-Word</span></span>

<span data-ttu-id="7e538-194">Geeft aan dat de cmdlet het aantal woorden in de invoer objecten telt.</span><span class="sxs-lookup"><span data-stu-id="7e538-194">Indicates that the cmdlet counts the number of words in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="7e538-195">Het **woord** , **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="7e538-195">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="7e538-196">Zie voor beeld 7.</span><span class="sxs-lookup"><span data-stu-id="7e538-196">See Example 7.</span></span>

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

### <span data-ttu-id="7e538-197">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e538-197">CommonParameters</span></span>

<span data-ttu-id="7e538-198">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7e538-198">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e538-199">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7e538-199">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7e538-200">INVOER</span><span class="sxs-lookup"><span data-stu-id="7e538-200">INPUTS</span></span>

### <span data-ttu-id="7e538-201">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="7e538-201">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7e538-202">U kunt objecten door sluizen naar `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="7e538-202">You can pipe objects to `Measure-Object`.</span></span>

## <span data-ttu-id="7e538-203">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7e538-203">OUTPUTS</span></span>

### <span data-ttu-id="7e538-204">Micro soft. Power shell. commands. GenericMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="7e538-204">Microsoft.PowerShell.Commands.GenericMeasureInfo</span></span>

### <span data-ttu-id="7e538-205">Micro soft. Power shell. commands. TextMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="7e538-205">Microsoft.PowerShell.Commands.TextMeasureInfo</span></span>

<span data-ttu-id="7e538-206">Als u de para meter **Word** gebruikt, `Measure-Object` wordt een **TextMeasureInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7e538-206">If you use the **Word** parameter, `Measure-Object` returns a **TextMeasureInfo** object.</span></span>
<span data-ttu-id="7e538-207">Anders wordt een **GenericMeasureInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7e538-207">Otherwise, it returns a **GenericMeasureInfo** object.</span></span>

## <span data-ttu-id="7e538-208">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7e538-208">NOTES</span></span>

## <span data-ttu-id="7e538-209">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7e538-209">RELATED LINKS</span></span>

[<span data-ttu-id="7e538-210">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="7e538-210">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="7e538-211">Compare-object</span><span class="sxs-lookup"><span data-stu-id="7e538-211">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="7e538-212">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="7e538-212">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="7e538-213">Groep-object</span><span class="sxs-lookup"><span data-stu-id="7e538-213">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="7e538-214">New-Object</span><span class="sxs-lookup"><span data-stu-id="7e538-214">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="7e538-215">Select-Object</span><span class="sxs-lookup"><span data-stu-id="7e538-215">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="7e538-216">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="7e538-216">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="7e538-217">T-object</span><span class="sxs-lookup"><span data-stu-id="7e538-217">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="7e538-218">Where-object</span><span class="sxs-lookup"><span data-stu-id="7e538-218">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
