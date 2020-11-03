---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 3c1f8d136cf98a703a1eb31d73e226df5d8ef56b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251099"
---
# <span data-ttu-id="87a76-103">Get-Random</span><span class="sxs-lookup"><span data-stu-id="87a76-103">Get-Random</span></span>

## <span data-ttu-id="87a76-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="87a76-104">SYNOPSIS</span></span>
<span data-ttu-id="87a76-105">Haalt een wille keurig getal op of selecteert objecten wille keurig van een verzameling.</span><span class="sxs-lookup"><span data-stu-id="87a76-105">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="87a76-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="87a76-106">SYNTAX</span></span>

### <span data-ttu-id="87a76-107">RandomNumberParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="87a76-107">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [<CommonParameters>]
```

### <span data-ttu-id="87a76-108">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="87a76-108">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="87a76-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="87a76-109">DESCRIPTION</span></span>

<span data-ttu-id="87a76-110">De `Get-Random` cmdlet haalt een wille keurig geselecteerd getal op.</span><span class="sxs-lookup"><span data-stu-id="87a76-110">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="87a76-111">Als u een verzameling objecten indient, worden er `Get-Random` een of meer wille keurig geselecteerde objecten uit de verzameling opgehaald.</span><span class="sxs-lookup"><span data-stu-id="87a76-111">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="87a76-112">Zonder para meters of invoer `Get-Random` retourneert een opdracht een wille keurig geselecteerd 32-bits geheel getal van 0 (nul) en **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).</span><span class="sxs-lookup"><span data-stu-id="87a76-112">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="87a76-113">U kunt de para meters van gebruiken `Get-Random` om een Seed-nummer, minimum-en maximum waarde op te geven en het aantal objecten dat door een ingediende verzameling wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="87a76-113">You can use the parameters of `Get-Random` to specify a seed number, minimum and maximum values, and the number of objects returned from a submitted collection.</span></span>

## <span data-ttu-id="87a76-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="87a76-114">EXAMPLES</span></span>

### <span data-ttu-id="87a76-115">Voor beeld 1: een wille keurig geheel getal ophalen</span><span class="sxs-lookup"><span data-stu-id="87a76-115">Example 1: Get a random integer</span></span>

<span data-ttu-id="87a76-116">Met deze opdracht wordt een wille keurig geheel getal opgehaald tussen 0 (nul) en **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="87a76-116">This command gets a random integer between 0 (zero) and **Int32.MaxValue**.</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="87a76-117">Voor beeld 2: een wille keurig geheel getal ophalen tussen 0 en 99</span><span class="sxs-lookup"><span data-stu-id="87a76-117">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="87a76-118">Voor beeld 3: een wille keurig geheel getal ophalen tussen-100 en 99</span><span class="sxs-lookup"><span data-stu-id="87a76-118">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="87a76-119">Voor beeld 4: een wille keurig getal met drijvende komma ophalen</span><span class="sxs-lookup"><span data-stu-id="87a76-119">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="87a76-120">Met deze opdracht wordt een wille keurig drijvende-komma nummer opgehaald dat groter is dan of gelijk is aan 10,7 en kleiner is dan 20,92.</span><span class="sxs-lookup"><span data-stu-id="87a76-120">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="87a76-121">Voor beeld 5: een wille keurig geheel getal uit een matrix ophalen</span><span class="sxs-lookup"><span data-stu-id="87a76-121">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="87a76-122">Met deze opdracht wordt een wille keurig geselecteerd getal uit de opgegeven matrix opgehaald.</span><span class="sxs-lookup"><span data-stu-id="87a76-122">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="87a76-123">Voor beeld 6: meerdere wille keurige gehele getallen ophalen uit een matrix</span><span class="sxs-lookup"><span data-stu-id="87a76-123">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="87a76-124">Met deze opdracht worden drie wille keurig geselecteerde getallen in wille keurige volg orde uit een matrix opgehaald.</span><span class="sxs-lookup"><span data-stu-id="87a76-124">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="87a76-125">Voor beeld 7: een hele verzameling wille keurig toekennen</span><span class="sxs-lookup"><span data-stu-id="87a76-125">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="87a76-126">Met deze opdracht wordt de gehele verzameling in wille keurige volg orde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="87a76-126">This command returns the entire collection in random order.</span></span>

<span data-ttu-id="87a76-127">De waarde van de para meter **aantal** is de eigenschap **MaxValue** static van integers.</span><span class="sxs-lookup"><span data-stu-id="87a76-127">The value of the **Count** parameter is the **MaxValue** static property of integers.</span></span>

<span data-ttu-id="87a76-128">Als u een volledige verzameling in een wille keurige volg orde wilt retour neren, voert u een getal in dat groter is dan of gelijk is aan het aantal objecten in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="87a76-128">To return an entire collection in random order, enter any number that is greater than or equal to the number of objects in the collection.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count ([int]::MaxValue)
```

```Output
2
3
5
1
8
13
```

### <span data-ttu-id="87a76-129">Voor beeld 8: een wille keurige, niet-numerieke waarde ophalen</span><span class="sxs-lookup"><span data-stu-id="87a76-129">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="87a76-130">Met deze opdracht wordt een wille keurige waarde uit een niet-numerieke collectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="87a76-130">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="87a76-131">Voor beeld 9: de para meter SetSeed gebruiken</span><span class="sxs-lookup"><span data-stu-id="87a76-131">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="87a76-132">In dit voor beeld ziet u het effect van het gebruik van de para meter **SetSeed** .</span><span class="sxs-lookup"><span data-stu-id="87a76-132">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="87a76-133">Omdat **SetSeed** niet-wille keurig gedrag produceert, wordt het doorgaans alleen gebruikt om de resultaten te reproduceren, bijvoorbeeld bij het opsporen van fouten in een script of het analyseren van een-bestand.</span><span class="sxs-lookup"><span data-stu-id="87a76-133">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

```powershell
# Commands with the default seed are pseudorandom
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

```powershell
# Commands with the same seed are not random
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
```

```Output
74
74
74
```

```powershell
# SetSeed results in a repeatable series
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

### <span data-ttu-id="87a76-134">Voor beeld 10: wille keurige bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="87a76-134">Example 10: Get random files</span></span>

<span data-ttu-id="87a76-135">Deze opdrachten krijgen een wille keurig geselecteerd voor beeld van 50 bestanden van het `C:` station van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="87a76-135">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="87a76-136">Voor beeld 11: roll-Fair-dobbel stenen</span><span class="sxs-lookup"><span data-stu-id="87a76-136">Example 11: Roll fair dice</span></span>

<span data-ttu-id="87a76-137">In dit voor beeld wordt een billijke dobbel steen van 1200 keer Gerolt en worden de resultaten geteld.</span><span class="sxs-lookup"><span data-stu-id="87a76-137">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="87a76-138">Met de eerste opdracht wordt `For-EachObject` de aanroep herhaald `Get-Random` van de sluis in getallen (1-6).</span><span class="sxs-lookup"><span data-stu-id="87a76-138">The first command, `For-EachObject` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="87a76-139">De resultaten worden gegroepeerd op basis van de waarde `Group-Object` en opgemaakt als een tabel met `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="87a76-139">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

```powershell
1..1200 | ForEach-Object {
    1..6 | Get-Random
} | Group-Object | Select-Object Name,Count
```

```Output
Name Count
---- -----
1      206
2      199
3      196
4      226
5      185
6      188
```

## <span data-ttu-id="87a76-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="87a76-140">PARAMETERS</span></span>

### <span data-ttu-id="87a76-141">-Aantal</span><span class="sxs-lookup"><span data-stu-id="87a76-141">-Count</span></span>

<span data-ttu-id="87a76-142">Hiermee geeft u het aantal wille keurige objecten of getallen op dat moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="87a76-142">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="87a76-143">De standaardwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="87a76-143">The default is 1.</span></span>

<span data-ttu-id="87a76-144">Als in combi natie met de `InputObject` waarde van **Count** het aantal objecten in de verzameling overschrijdt, `Get-Random` retourneert alle objecten in wille keurige volg orde.</span><span class="sxs-lookup"><span data-stu-id="87a76-144">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87a76-145">-Input object</span><span class="sxs-lookup"><span data-stu-id="87a76-145">-InputObject</span></span>

<span data-ttu-id="87a76-146">Hiermee wordt een verzameling objecten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="87a76-146">Specifies a collection of objects.</span></span> <span data-ttu-id="87a76-147">`Get-Random` Hiermee worden wille keurig geselecteerde objecten in wille keurige volg orde opgehaald uit de verzameling tot het aantal dat is opgegeven door **Count**.</span><span class="sxs-lookup"><span data-stu-id="87a76-147">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count**.</span></span> <span data-ttu-id="87a76-148">Voer de objecten, een variabele die de objecten bevat of een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="87a76-148">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="87a76-149">U kunt ook een verzameling van objecten door sluizen naar `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="87a76-149">You can also pipe a collection of objects to `Get-Random`.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="87a76-150">-Maximum</span><span class="sxs-lookup"><span data-stu-id="87a76-150">-Maximum</span></span>

<span data-ttu-id="87a76-151">Hiermee geeft u een maximum waarde op voor het wille keurig getal.</span><span class="sxs-lookup"><span data-stu-id="87a76-151">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="87a76-152">`Get-Random` retourneert een waarde die kleiner is dan het maximum (niet gelijk aan).</span><span class="sxs-lookup"><span data-stu-id="87a76-152">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="87a76-153">Voer een geheel getal, een zwevende-komma getal met dubbele precisie of een object in dat kan worden geconverteerd naar een geheel getal of dubbele waarde, zoals een numerieke teken reeks ("100").</span><span class="sxs-lookup"><span data-stu-id="87a76-153">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="87a76-154">De waarde van **maximum** moet groter dan (niet gelijk aan) de waarde van **minimum** zijn.</span><span class="sxs-lookup"><span data-stu-id="87a76-154">The value of **Maximum** must be greater than (not equal to) the value of **Minimum**.</span></span> <span data-ttu-id="87a76-155">Als de waarde van **maximum** of **minimum** een drijvende-komma getal is, `Get-Random` wordt een wille keurig geselecteerd drijvende-komma getal geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="87a76-155">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="87a76-156">Als de waarde van **minimum** een 32-bits integer is op een 64-bits computer, is de standaard waarde van **maximum** **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="87a76-156">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue**.</span></span>

<span data-ttu-id="87a76-157">Als de waarde van **minimum** een double is (een getal met een drijvende komma), is de standaard waarde van **maximum** **Double. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="87a76-157">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue**.</span></span> <span data-ttu-id="87a76-158">Anders is de standaard waarde **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="87a76-158">Otherwise, the default value is **Int32.MaxValue**.</span></span>

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87a76-159">-Minimum</span><span class="sxs-lookup"><span data-stu-id="87a76-159">-Minimum</span></span>

<span data-ttu-id="87a76-160">Hiermee geeft u een minimum waarde voor het wille keurig getal op.</span><span class="sxs-lookup"><span data-stu-id="87a76-160">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="87a76-161">Voer een geheel getal, een zwevende-komma getal met dubbele precisie of een object in dat kan worden geconverteerd naar een geheel getal of dubbele waarde, zoals een numerieke teken reeks ("100").</span><span class="sxs-lookup"><span data-stu-id="87a76-161">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="87a76-162">De standaardwaarde is 0 (nul).</span><span class="sxs-lookup"><span data-stu-id="87a76-162">The default value is 0 (zero).</span></span>

<span data-ttu-id="87a76-163">De waarde van **minimum** moet kleiner zijn dan (niet gelijk aan) de waarde van **maximum**.</span><span class="sxs-lookup"><span data-stu-id="87a76-163">The value of **Minimum** must be less than (not equal to) the value of **Maximum**.</span></span> <span data-ttu-id="87a76-164">Als de waarde van **maximum** of **minimum** een drijvende-komma getal is, `Get-Random` wordt een wille keurig geselecteerd drijvende-komma getal geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="87a76-164">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87a76-165">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="87a76-165">-SetSeed</span></span>

<span data-ttu-id="87a76-166">Hiermee geeft u een Seed-waarde op voor de generator voor wille keurige getallen.</span><span class="sxs-lookup"><span data-stu-id="87a76-166">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="87a76-167">Deze Seed-waarde wordt gebruikt voor de huidige opdracht en voor alle volgende `Get-Random` opdrachten in de huidige sessie totdat u **SetSeed** opnieuw gebruikt of de sessie sluit.</span><span class="sxs-lookup"><span data-stu-id="87a76-167">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="87a76-168">U kunt de Seed niet opnieuw instellen op de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="87a76-168">You can't reset the seed to its default value.</span></span>

<span data-ttu-id="87a76-169">De para meter **SetSeed** is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="87a76-169">The **SetSeed** parameter is not required.</span></span> <span data-ttu-id="87a76-170">`Get-Random`Maakt standaard gebruik van de methode [RandomNumberGenerator ()](/dotnet/api/system.security.cryptography.randomnumbergenerator) voor het genereren van een Seed-waarde.</span><span class="sxs-lookup"><span data-stu-id="87a76-170">By default, `Get-Random` uses the [RandomNumberGenerator()](/dotnet/api/system.security.cryptography.randomnumbergenerator) method to generate a seed value.</span></span> <span data-ttu-id="87a76-171">Omdat **SetSeed** resulteert in niet-wille keurig gedrag, wordt het normaal gesp roken alleen gebruikt bij het reproduceren van het gedrag, bijvoorbeeld bij het opsporen van fouten of het analyseren van een script dat `Get-Random` opdrachten bevat.</span><span class="sxs-lookup"><span data-stu-id="87a76-171">Because **SetSeed** results in non-random behavior, it's typically used only when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87a76-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="87a76-172">CommonParameters</span></span>

<span data-ttu-id="87a76-173">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="87a76-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="87a76-174">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="87a76-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="87a76-175">INVOER</span><span class="sxs-lookup"><span data-stu-id="87a76-175">INPUTS</span></span>

### <span data-ttu-id="87a76-176">System. object</span><span class="sxs-lookup"><span data-stu-id="87a76-176">System.Object</span></span>

<span data-ttu-id="87a76-177">U kunt een of meer objecten door sluizen.</span><span class="sxs-lookup"><span data-stu-id="87a76-177">You can pipe one or more objects.</span></span> <span data-ttu-id="87a76-178">`Get-Random` selecteert waarden wille keurig van de objecten met pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="87a76-178">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="87a76-179">UITVOER</span><span class="sxs-lookup"><span data-stu-id="87a76-179">OUTPUTS</span></span>

### <span data-ttu-id="87a76-180">System. Int32, System. Int64, systeem. Double</span><span class="sxs-lookup"><span data-stu-id="87a76-180">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="87a76-181">`Get-Random` retourneert een geheel getal of getal met een drijvende komma of een object dat wille keurig uit een ingediende verzameling is geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="87a76-181">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="87a76-182">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="87a76-182">NOTES</span></span>

<span data-ttu-id="87a76-183">`Get-Random` Hiermee stelt u een standaard zaad voor elke sessie in op basis van de systeem tijd klok wanneer de sessie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="87a76-183">`Get-Random` sets a default seed for each session based on the system time clock when the session starts.</span></span>

<span data-ttu-id="87a76-184">`Get-Random` retourneert niet altijd hetzelfde gegevens type als de invoer waarde.</span><span class="sxs-lookup"><span data-stu-id="87a76-184">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="87a76-185">In de volgende tabel ziet u het uitvoer type voor elk van de numerieke invoer typen.</span><span class="sxs-lookup"><span data-stu-id="87a76-185">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="87a76-186">Invoertype</span><span class="sxs-lookup"><span data-stu-id="87a76-186">Input Type</span></span> | <span data-ttu-id="87a76-187">Uitvoer type</span><span class="sxs-lookup"><span data-stu-id="87a76-187">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="87a76-188">SByte</span><span class="sxs-lookup"><span data-stu-id="87a76-188">SByte</span></span>    |   <span data-ttu-id="87a76-189">Dubbel</span><span class="sxs-lookup"><span data-stu-id="87a76-189">Double</span></span>    |
|    <span data-ttu-id="87a76-190">Byte</span><span class="sxs-lookup"><span data-stu-id="87a76-190">Byte</span></span>    |   <span data-ttu-id="87a76-191">Dubbel</span><span class="sxs-lookup"><span data-stu-id="87a76-191">Double</span></span>    |
|   <span data-ttu-id="87a76-192">Int16</span><span class="sxs-lookup"><span data-stu-id="87a76-192">Int16</span></span>    |   <span data-ttu-id="87a76-193">Dubbel</span><span class="sxs-lookup"><span data-stu-id="87a76-193">Double</span></span>    |
|   <span data-ttu-id="87a76-194">UInt16</span><span class="sxs-lookup"><span data-stu-id="87a76-194">UInt16</span></span>   |   <span data-ttu-id="87a76-195">Dubbel</span><span class="sxs-lookup"><span data-stu-id="87a76-195">Double</span></span>    |
|   <span data-ttu-id="87a76-196">Int32</span><span class="sxs-lookup"><span data-stu-id="87a76-196">Int32</span></span>    |    <span data-ttu-id="87a76-197">Int32</span><span class="sxs-lookup"><span data-stu-id="87a76-197">Int32</span></span>    |
|   <span data-ttu-id="87a76-198">UInt32</span><span class="sxs-lookup"><span data-stu-id="87a76-198">UInt32</span></span>   |   <span data-ttu-id="87a76-199">Dubbel</span><span class="sxs-lookup"><span data-stu-id="87a76-199">Double</span></span>    |
|   <span data-ttu-id="87a76-200">Int64</span><span class="sxs-lookup"><span data-stu-id="87a76-200">Int64</span></span>    |    <span data-ttu-id="87a76-201">Int64</span><span class="sxs-lookup"><span data-stu-id="87a76-201">Int64</span></span>    |
|   <span data-ttu-id="87a76-202">UInt64</span><span class="sxs-lookup"><span data-stu-id="87a76-202">UInt64</span></span>   |   <span data-ttu-id="87a76-203">Dubbel</span><span class="sxs-lookup"><span data-stu-id="87a76-203">Double</span></span>    |
|   <span data-ttu-id="87a76-204">Dubbel</span><span class="sxs-lookup"><span data-stu-id="87a76-204">Double</span></span>   |   <span data-ttu-id="87a76-205">Dubbel</span><span class="sxs-lookup"><span data-stu-id="87a76-205">Double</span></span>    |
|   <span data-ttu-id="87a76-206">Enkel</span><span class="sxs-lookup"><span data-stu-id="87a76-206">Single</span></span>   |   <span data-ttu-id="87a76-207">Dubbel</span><span class="sxs-lookup"><span data-stu-id="87a76-207">Double</span></span>    |

<span data-ttu-id="87a76-208">Vanaf Windows Power Shell 3,0 `Get-Random` ondersteunt 64-bits geheel getal.</span><span class="sxs-lookup"><span data-stu-id="87a76-208">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="87a76-209">In Windows Power Shell 2,0 worden alle waarden geconverteerd naar **System. Int32**.</span><span class="sxs-lookup"><span data-stu-id="87a76-209">In Windows PowerShell 2.0, all values are cast to **System.Int32**.</span></span>

## <span data-ttu-id="87a76-210">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="87a76-210">RELATED LINKS</span></span>
