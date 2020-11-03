---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 5d4a27f1a1949056ca63b9b6a2340bf1226592e0
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251737"
---
# <span data-ttu-id="c7bef-103">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="c7bef-103">Measure-Object</span></span>

## <span data-ttu-id="c7bef-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c7bef-104">SYNOPSIS</span></span>
<span data-ttu-id="c7bef-105">Hiermee worden de numerieke eigenschappen van objecten en de tekens, woorden en regels in teken reeks objecten, zoals tekst bestanden, berekend.</span><span class="sxs-lookup"><span data-stu-id="c7bef-105">Calculates the numeric properties of objects, and the characters, words, and lines in string objects, such as files of text.</span></span>

## <span data-ttu-id="c7bef-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c7bef-106">SYNTAX</span></span>

### <span data-ttu-id="c7bef-107">GenericMeasure (standaard)</span><span class="sxs-lookup"><span data-stu-id="c7bef-107">GenericMeasure (Default)</span></span>

```
Measure-Object [-InputObject <PSObject>] [[-Property] <String[]>] [-Sum] [-Average] [-Maximum] [-Minimum]
 [<CommonParameters>]
```

### <span data-ttu-id="c7bef-108">TextMeasure</span><span class="sxs-lookup"><span data-stu-id="c7bef-108">TextMeasure</span></span>

```
Measure-Object [-InputObject <PSObject>] [[-Property] <String[]>] [-Line] [-Word] [-Character]
 [-IgnoreWhiteSpace] [<CommonParameters>]
```

## <span data-ttu-id="c7bef-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c7bef-109">DESCRIPTION</span></span>

<span data-ttu-id="c7bef-110">`Measure-Object`Met de cmdlet worden de eigenschapwaarden van bepaalde typen objecten berekend.</span><span class="sxs-lookup"><span data-stu-id="c7bef-110">The `Measure-Object` cmdlet calculates the property values of certain types of object.</span></span>
<span data-ttu-id="c7bef-111">`Measure-Object` voert drie soorten metingen uit, afhankelijk van de para meters in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="c7bef-111">`Measure-Object` performs three types of measurements, depending on the parameters in the command.</span></span>

<span data-ttu-id="c7bef-112">De `Measure-Object` cmdlet voert berekeningen uit op de eigenschaps waarden van objecten.</span><span class="sxs-lookup"><span data-stu-id="c7bef-112">The `Measure-Object` cmdlet performs calculations on the property values of objects.</span></span> <span data-ttu-id="c7bef-113">U kunt gebruiken `Measure-Object` om objecten te tellen of objecten te tellen met een opgegeven **eigenschap**.</span><span class="sxs-lookup"><span data-stu-id="c7bef-113">You can use `Measure-Object` to count objects or count objects with a specified **Property**.</span></span> <span data-ttu-id="c7bef-114">U kunt ook gebruiken `Measure-Object` om het **minimum** , **maximum** , **Sum** , **StandardDeviation** en het **gemiddelde** van numerieke waarden te berekenen.</span><span class="sxs-lookup"><span data-stu-id="c7bef-114">You can also use `Measure-Object` to calculate the **Minimum** , **Maximum** , **Sum** , **StandardDeviation** and **Average** of numeric values.</span></span> <span data-ttu-id="c7bef-115">Voor **teken reeks** objecten kunt u ook gebruiken `Measure-Object` om het aantal regels, woorden en tekens te tellen.</span><span class="sxs-lookup"><span data-stu-id="c7bef-115">For **String** objects, you can also use `Measure-Object` to count the number of lines, words, and characters.</span></span>

## <span data-ttu-id="c7bef-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c7bef-116">EXAMPLES</span></span>

### <span data-ttu-id="c7bef-117">Voor beeld 1: het aantal bestanden en mappen in een map tellen</span><span class="sxs-lookup"><span data-stu-id="c7bef-117">Example 1: Count the files and folders in a directory</span></span>

<span data-ttu-id="c7bef-118">Met deze opdracht worden de bestanden en mappen in de huidige map geteld.</span><span class="sxs-lookup"><span data-stu-id="c7bef-118">This command counts the files and folders in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object
```

### <span data-ttu-id="c7bef-119">Voor beeld 2: de bestanden in een map meten</span><span class="sxs-lookup"><span data-stu-id="c7bef-119">Example 2: Measure the files in a directory</span></span>

<span data-ttu-id="c7bef-120">Met deze opdracht worden het **minimum** , **maximum** en de **som** van de grootte van alle bestanden in de huidige map en de gemiddelde grootte van een bestand in de map weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7bef-120">This command displays the **Minimum** , **Maximum** , and **Sum** of the sizes of all files in the current directory, and the average size of a file in the directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### <span data-ttu-id="c7bef-121">Voor beeld 3: tekst in een tekst bestand meten</span><span class="sxs-lookup"><span data-stu-id="c7bef-121">Example 3: Measure text in a text file</span></span>

<span data-ttu-id="c7bef-122">Met deze opdracht wordt het aantal tekens, woorden en regels in het Text.txt bestand weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7bef-122">This command displays the number of characters, words, and lines in the Text.txt file.</span></span>
<span data-ttu-id="c7bef-123">Zonder de **onbewerkte** para meter `Get-Content` voert het bestand uit als een matrix met regels.</span><span class="sxs-lookup"><span data-stu-id="c7bef-123">Without the **Raw** parameter, `Get-Content` outputs the file as an array of lines.</span></span>

<span data-ttu-id="c7bef-124">De eerste opdracht wordt gebruikt `Set-Content` om een standaard tekst toe te voegen aan een bestand.</span><span class="sxs-lookup"><span data-stu-id="c7bef-124">The first command uses `Set-Content` to add some default text to a file.</span></span>

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### <span data-ttu-id="c7bef-125">Voor beeld 4: objecten met een opgegeven eigenschap meten</span><span class="sxs-lookup"><span data-stu-id="c7bef-125">Example 4: Measure objects containing a specified Property</span></span>

<span data-ttu-id="c7bef-126">In dit voor beeld wordt het aantal objecten met een eigenschap **DisplayName** geteld.</span><span class="sxs-lookup"><span data-stu-id="c7bef-126">This example counts the number of objects that have a **DisplayName** property.</span></span> <span data-ttu-id="c7bef-127">Met de eerste twee opdrachten worden alle services en processen op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c7bef-127">The first two commands retrieve all the services and processes on the local machine.</span></span> <span data-ttu-id="c7bef-128">Met de derde opdracht wordt het gecombineerde aantal services en processen geteld.</span><span class="sxs-lookup"><span data-stu-id="c7bef-128">The third command counts the combined number of services and processes.</span></span> <span data-ttu-id="c7bef-129">Met de laatste opdracht worden de twee verzamelingen gecombineerd en wordt het resultaat door sluizen naar `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="c7bef-129">The last command combines the two collections and pipes the result to `Measure-Object`.</span></span>

<span data-ttu-id="c7bef-130">Het object **System. Diagnostics. process** heeft geen eigenschap **DisplayName** en wordt wegge laten uit het laatste aantal.</span><span class="sxs-lookup"><span data-stu-id="c7bef-130">The **System.Diagnostics.Process** object does not have a **DisplayName** property, and is left out of the final count.</span></span>

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

### <span data-ttu-id="c7bef-131">Voor beeld 5: de inhoud van een CSV-bestand meten</span><span class="sxs-lookup"><span data-stu-id="c7bef-131">Example 5: Measure the contents of a CSV file</span></span>

<span data-ttu-id="c7bef-132">Met deze opdracht wordt het gemiddelde aantal jaren van de service van de werk nemers van een bedrijf berekend.</span><span class="sxs-lookup"><span data-stu-id="c7bef-132">This command calculates the average years of service of the employees of a company.</span></span>

<span data-ttu-id="c7bef-133">Het `ServiceYrs.csv` bestand is een CSV-bestand dat het werknemers nummer en de dienst jaren van elke werk nemer bevat.</span><span class="sxs-lookup"><span data-stu-id="c7bef-133">The `ServiceYrs.csv` file is a CSV file that contains the employee number and years of service of each employee.</span></span> <span data-ttu-id="c7bef-134">De eerste rij in de tabel is een veldnamenrij van **EmpNo** , **jaar**.</span><span class="sxs-lookup"><span data-stu-id="c7bef-134">The first row in the table is a header row of **EmpNo** , **Years**.</span></span>

<span data-ttu-id="c7bef-135">Wanneer u gebruikt `Import-Csv` om het bestand te importeren, is het resultaat een **PSCustomObject** met notitie-eigenschappen van **EmpNo** en **jaren**.</span><span class="sxs-lookup"><span data-stu-id="c7bef-135">When you use `Import-Csv` to import the file, the result is a **PSCustomObject** with note properties of **EmpNo** and **Years**.</span></span>
<span data-ttu-id="c7bef-136">U kunt gebruiken `Measure-Object` voor het berekenen van de waarden van deze eigenschappen, net als elke andere eigenschap van een object.</span><span class="sxs-lookup"><span data-stu-id="c7bef-136">You can use `Measure-Object` to calculate the values of these properties, just like any other property of an object.</span></span>

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### <span data-ttu-id="c7bef-137">Voor beeld 6: Boole-waarden meten</span><span class="sxs-lookup"><span data-stu-id="c7bef-137">Example 6: Measure Boolean values</span></span>

<span data-ttu-id="c7bef-138">In dit voor beeld wordt gedemonstreerd hoe `Measure-Object` Booleaanse waarden kunnen worden gemeten.</span><span class="sxs-lookup"><span data-stu-id="c7bef-138">This example demonstrates how the `Measure-Object` can measure Boolean values.</span></span>
<span data-ttu-id="c7bef-139">In dit geval wordt de **PSIsContainer** **Boolean** -eigenschap gebruikt om het incidenten van mappen (versus bestanden) in de huidige map te meten.</span><span class="sxs-lookup"><span data-stu-id="c7bef-139">In this case, it uses the **PSIsContainer** **Boolean** property to measure the incidence of folders (vs. files) in the current directory.</span></span>

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

### <span data-ttu-id="c7bef-140">Voor beeld 7: teken reeksen meten</span><span class="sxs-lookup"><span data-stu-id="c7bef-140">Example 7: Measure strings</span></span>

<span data-ttu-id="c7bef-141">In het volgende voor beeld wordt het aantal regels, eerste één teken reeks, in meerdere teken reeksen gemeten.</span><span class="sxs-lookup"><span data-stu-id="c7bef-141">The following example measures the number of lines, first a single string, then across several strings.</span></span> <span data-ttu-id="c7bef-142">Het teken voor een nieuwe regel <code>\`n</code> scheidt reeksen in meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="c7bef-142">The newline character <code>\`n</code> separates strings into multiple lines.</span></span>

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

## <span data-ttu-id="c7bef-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c7bef-143">PARAMETERS</span></span>

### <span data-ttu-id="c7bef-144">-Gemiddeld</span><span class="sxs-lookup"><span data-stu-id="c7bef-144">-Average</span></span>

<span data-ttu-id="c7bef-145">Geeft aan dat de cmdlet de gemiddelde waarde van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="c7bef-145">Indicates that the cmdlet displays the average value of the specified properties.</span></span>

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

### <span data-ttu-id="c7bef-146">-Teken</span><span class="sxs-lookup"><span data-stu-id="c7bef-146">-Character</span></span>

<span data-ttu-id="c7bef-147">Geeft aan dat de cmdlet het aantal tekens in de invoer objecten telt.</span><span class="sxs-lookup"><span data-stu-id="c7bef-147">Indicates that the cmdlet counts the number of characters in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="c7bef-148">Het **woord** , **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="c7bef-148">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="c7bef-149">Zie voor beeld 7.</span><span class="sxs-lookup"><span data-stu-id="c7bef-149">See Example 7.</span></span>

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

### <span data-ttu-id="c7bef-150">-IgnoreWhiteSpace</span><span class="sxs-lookup"><span data-stu-id="c7bef-150">-IgnoreWhiteSpace</span></span>

<span data-ttu-id="c7bef-151">Geeft aan dat de cmdlet witruimte in het aantal tekens negeert.</span><span class="sxs-lookup"><span data-stu-id="c7bef-151">Indicates that the cmdlet ignores white space in character counts.</span></span>
<span data-ttu-id="c7bef-152">Standaard wordt witruimte niet genegeerd.</span><span class="sxs-lookup"><span data-stu-id="c7bef-152">By default, white space is not ignored.</span></span>

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

### <span data-ttu-id="c7bef-153">-Input object</span><span class="sxs-lookup"><span data-stu-id="c7bef-153">-InputObject</span></span>

<span data-ttu-id="c7bef-154">Geeft aan welke objecten moeten worden gemeten.</span><span class="sxs-lookup"><span data-stu-id="c7bef-154">Specifies the objects to be measured.</span></span>
<span data-ttu-id="c7bef-155">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c7bef-155">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="c7bef-156">Wanneer u de para meter **input object** gebruikt in `Measure-Object` plaats van de resultaten van de pijpleiding opdracht, `Measure-Object` wordt de waarde van **input object** behandeld als een enkel object.</span><span class="sxs-lookup"><span data-stu-id="c7bef-156">When you use the **InputObject** parameter with `Measure-Object`, instead of piping command results to `Measure-Object`, the **InputObject** value is treated as a single object.</span></span>

<span data-ttu-id="c7bef-157">Het is raadzaam `Measure-Object` om in de pijp lijn te gebruiken als u een verzameling objecten wilt meten op basis van het feit of de objecten specifieke waarden in gedefinieerde eigenschappen hebben.</span><span class="sxs-lookup"><span data-stu-id="c7bef-157">It is recommended that you use `Measure-Object` in the pipeline if you want to measure a collection of objects based on whether the objects have specific values in defined properties.</span></span>

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

### <span data-ttu-id="c7bef-158">-Regel</span><span class="sxs-lookup"><span data-stu-id="c7bef-158">-Line</span></span>

<span data-ttu-id="c7bef-159">Geeft aan dat de cmdlet het aantal regels in de invoer objecten telt.</span><span class="sxs-lookup"><span data-stu-id="c7bef-159">Indicates that the cmdlet counts the number of lines in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="c7bef-160">Het **woord** , **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="c7bef-160">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="c7bef-161">Zie voor beeld 7.</span><span class="sxs-lookup"><span data-stu-id="c7bef-161">See Example 7.</span></span>

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

### <span data-ttu-id="c7bef-162">-Maximum</span><span class="sxs-lookup"><span data-stu-id="c7bef-162">-Maximum</span></span>

<span data-ttu-id="c7bef-163">Geeft aan dat de cmdlet de maximum waarde van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="c7bef-163">Indicates that the cmdlet displays the maximum value of the specified properties.</span></span>

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

### <span data-ttu-id="c7bef-164">-Minimum</span><span class="sxs-lookup"><span data-stu-id="c7bef-164">-Minimum</span></span>

<span data-ttu-id="c7bef-165">Geeft aan dat de cmdlet de minimale waarde van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="c7bef-165">Indicates that the cmdlet displays the minimum value of the specified properties.</span></span>

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

### <span data-ttu-id="c7bef-166">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="c7bef-166">-Property</span></span>

<span data-ttu-id="c7bef-167">Hiermee geeft u een of meer eigenschappen op die moeten worden gemeten.</span><span class="sxs-lookup"><span data-stu-id="c7bef-167">Specifies one or more properties to measure.</span></span> <span data-ttu-id="c7bef-168">Als u geen andere maat regelen opgeeft, `Measure-Object` telt het aantal objecten dat de door u opgegeven eigenschappen bevat.</span><span class="sxs-lookup"><span data-stu-id="c7bef-168">If you do not specify any other measures, `Measure-Object` counts the objects that have the properties you specify.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c7bef-169">-Sum</span><span class="sxs-lookup"><span data-stu-id="c7bef-169">-Sum</span></span>

<span data-ttu-id="c7bef-170">Geeft aan dat de cmdlet de som van de waarden van de opgegeven eigenschappen weergeeft.</span><span class="sxs-lookup"><span data-stu-id="c7bef-170">Indicates that the cmdlet displays the sum of the values of the specified properties.</span></span>

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

### <span data-ttu-id="c7bef-171">-Word</span><span class="sxs-lookup"><span data-stu-id="c7bef-171">-Word</span></span>

<span data-ttu-id="c7bef-172">Geeft aan dat de cmdlet het aantal woorden in de invoer objecten telt.</span><span class="sxs-lookup"><span data-stu-id="c7bef-172">Indicates that the cmdlet counts the number of words in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="c7bef-173">Het **woord** , **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="c7bef-173">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="c7bef-174">Zie voor beeld 7.</span><span class="sxs-lookup"><span data-stu-id="c7bef-174">See Example 7.</span></span>

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

### <span data-ttu-id="c7bef-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c7bef-175">CommonParameters</span></span>

<span data-ttu-id="c7bef-176">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c7bef-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c7bef-177">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c7bef-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c7bef-178">INVOER</span><span class="sxs-lookup"><span data-stu-id="c7bef-178">INPUTS</span></span>

### <span data-ttu-id="c7bef-179">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="c7bef-179">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c7bef-180">U kunt objecten door sluizen naar `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="c7bef-180">You can pipe objects to `Measure-Object`.</span></span>

## <span data-ttu-id="c7bef-181">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c7bef-181">OUTPUTS</span></span>

### <span data-ttu-id="c7bef-182">Micro soft. Power shell. commands. GenericMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="c7bef-182">Microsoft.PowerShell.Commands.GenericMeasureInfo</span></span>

### <span data-ttu-id="c7bef-183">Micro soft. Power shell. commands. TextMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="c7bef-183">Microsoft.PowerShell.Commands.TextMeasureInfo</span></span>

<span data-ttu-id="c7bef-184">Als u de para meter **Word** gebruikt, `Measure-Object` wordt een **TextMeasureInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c7bef-184">If you use the **Word** parameter, `Measure-Object` returns a **TextMeasureInfo** object.</span></span>
<span data-ttu-id="c7bef-185">Anders wordt een **GenericMeasureInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c7bef-185">Otherwise, it returns a **GenericMeasureInfo** object.</span></span>

## <span data-ttu-id="c7bef-186">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c7bef-186">NOTES</span></span>

## <span data-ttu-id="c7bef-187">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c7bef-187">RELATED LINKS</span></span>

[<span data-ttu-id="c7bef-188">Compare-object</span><span class="sxs-lookup"><span data-stu-id="c7bef-188">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="c7bef-189">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="c7bef-189">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="c7bef-190">Groep-object</span><span class="sxs-lookup"><span data-stu-id="c7bef-190">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="c7bef-191">New-Object</span><span class="sxs-lookup"><span data-stu-id="c7bef-191">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="c7bef-192">Select-Object</span><span class="sxs-lookup"><span data-stu-id="c7bef-192">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="c7bef-193">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="c7bef-193">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="c7bef-194">T-object</span><span class="sxs-lookup"><span data-stu-id="c7bef-194">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="c7bef-195">Where-object</span><span class="sxs-lookup"><span data-stu-id="c7bef-195">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
