---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 890088b91bd0d6e66e12cc5236272eeab842ed38
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705945"
---
# <span data-ttu-id="ed867-102">Get-Random</span><span class="sxs-lookup"><span data-stu-id="ed867-102">Get-Random</span></span>

## <span data-ttu-id="ed867-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ed867-103">SYNOPSIS</span></span>
<span data-ttu-id="ed867-104">Haalt een wille keurig getal op of selecteert objecten wille keurig van een verzameling.</span><span class="sxs-lookup"><span data-stu-id="ed867-104">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="ed867-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ed867-105">SYNTAX</span></span>

### <span data-ttu-id="ed867-106">RandomNumberParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="ed867-106">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="ed867-107">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="ed867-107">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="ed867-108">ShuffleParameterSet</span><span class="sxs-lookup"><span data-stu-id="ed867-108">ShuffleParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Shuffle] [<CommonParameters>]
```

## <span data-ttu-id="ed867-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ed867-109">DESCRIPTION</span></span>

<span data-ttu-id="ed867-110">De `Get-Random` cmdlet haalt een wille keurig geselecteerd getal op.</span><span class="sxs-lookup"><span data-stu-id="ed867-110">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="ed867-111">Als u een verzameling objecten indient, worden er `Get-Random` een of meer wille keurig geselecteerde objecten uit de verzameling opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ed867-111">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="ed867-112">Zonder para meters of invoer `Get-Random` retourneert een opdracht een wille keurig geselecteerd 32-bits geheel getal van 0 (nul) en **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).</span><span class="sxs-lookup"><span data-stu-id="ed867-112">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="ed867-113">U kunt de para meters van gebruiken `Get-Random` om een Seed-nummer, minimum-en maximum waarden op te geven, het aantal objecten dat door een ingediende verzameling wordt geretourneerd en de volledige verzameling in een wille keurige volg orde.</span><span class="sxs-lookup"><span data-stu-id="ed867-113">You can use the parameters of `Get-Random` to specify a seed number, minimum and maximum values, the number of objects returned from a submitted collection, and the entire collection in a random order.</span></span>

## <span data-ttu-id="ed867-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ed867-114">EXAMPLES</span></span>

### <span data-ttu-id="ed867-115">Voor beeld 1: een wille keurig geheel getal ophalen</span><span class="sxs-lookup"><span data-stu-id="ed867-115">Example 1: Get a random integer</span></span>

<span data-ttu-id="ed867-116">Met deze opdracht wordt een wille keurig geheel getal opgehaald tussen 0 (nul) en **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="ed867-116">This command gets a random integer between 0 (zero) and **Int32.MaxValue**.</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="ed867-117">Voor beeld 2: een wille keurig geheel getal ophalen tussen 0 en 99</span><span class="sxs-lookup"><span data-stu-id="ed867-117">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="ed867-118">Voor beeld 3: een wille keurig geheel getal ophalen tussen-100 en 99</span><span class="sxs-lookup"><span data-stu-id="ed867-118">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="ed867-119">Voor beeld 4: een wille keurig getal met drijvende komma ophalen</span><span class="sxs-lookup"><span data-stu-id="ed867-119">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="ed867-120">Met deze opdracht wordt een wille keurig drijvende-komma nummer opgehaald dat groter is dan of gelijk is aan 10,7 en kleiner is dan 20,92.</span><span class="sxs-lookup"><span data-stu-id="ed867-120">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="ed867-121">Voor beeld 5: een wille keurig geheel getal uit een matrix ophalen</span><span class="sxs-lookup"><span data-stu-id="ed867-121">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="ed867-122">Met deze opdracht wordt een wille keurig geselecteerd getal uit de opgegeven matrix opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ed867-122">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="ed867-123">Voor beeld 6: meerdere wille keurige gehele getallen ophalen uit een matrix</span><span class="sxs-lookup"><span data-stu-id="ed867-123">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="ed867-124">Met deze opdracht worden drie wille keurig geselecteerde getallen in wille keurige volg orde uit een matrix opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ed867-124">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="ed867-125">Voor beeld 7: een hele verzameling wille keurig toekennen</span><span class="sxs-lookup"><span data-stu-id="ed867-125">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="ed867-126">Vanaf Power shell 7,1 kunt u de para meter voor **wille keurige** volg orde gebruiken om de volledige verzameling te retour neren.</span><span class="sxs-lookup"><span data-stu-id="ed867-126">Starting in PowerShell 7.1, you can use the **Shuffle** parameter to return the entire collection in a random order.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Shuffle
```

```Output
2
3
5
1
8
13
```

### <span data-ttu-id="ed867-127">Voor beeld 8: een wille keurige, niet-numerieke waarde ophalen</span><span class="sxs-lookup"><span data-stu-id="ed867-127">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="ed867-128">Met deze opdracht wordt een wille keurige waarde uit een niet-numerieke collectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ed867-128">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="ed867-129">Voor beeld 9: de para meter SetSeed gebruiken</span><span class="sxs-lookup"><span data-stu-id="ed867-129">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="ed867-130">In dit voor beeld ziet u het effect van het gebruik van de para meter **SetSeed** .</span><span class="sxs-lookup"><span data-stu-id="ed867-130">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="ed867-131">Omdat **SetSeed** niet-wille keurig gedrag produceert, wordt het doorgaans alleen gebruikt om de resultaten te reproduceren, bijvoorbeeld bij het opsporen van fouten in een script of het analyseren van een-bestand.</span><span class="sxs-lookup"><span data-stu-id="ed867-131">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

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

### <span data-ttu-id="ed867-132">Voor beeld 10: wille keurige bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="ed867-132">Example 10: Get random files</span></span>

<span data-ttu-id="ed867-133">Deze opdrachten krijgen een wille keurig geselecteerd voor beeld van 50 bestanden van het `C:` station van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ed867-133">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="ed867-134">Voor beeld 11: roll-Fair-dobbel stenen</span><span class="sxs-lookup"><span data-stu-id="ed867-134">Example 11: Roll fair dice</span></span>

<span data-ttu-id="ed867-135">In dit voor beeld wordt een billijke dobbel steen van 1200 keer Gerolt en worden de resultaten geteld.</span><span class="sxs-lookup"><span data-stu-id="ed867-135">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="ed867-136">Met de eerste opdracht wordt `For-EachObject` de aanroep herhaald `Get-Random` van de sluis in getallen (1-6).</span><span class="sxs-lookup"><span data-stu-id="ed867-136">The first command, `For-EachObject` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="ed867-137">De resultaten worden gegroepeerd op basis van de waarde `Group-Object` en opgemaakt als een tabel met `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="ed867-137">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

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

### <span data-ttu-id="ed867-138">Voor beeld 12: de para meter aantal gebruiken</span><span class="sxs-lookup"><span data-stu-id="ed867-138">Example 12: Use the Count parameter</span></span>

<span data-ttu-id="ed867-139">U kunt nu de para meter **aantal** gebruiken zonder pijpleiding objecten aan `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="ed867-139">You can now use the **Count** parameter without piping objects to `Get-Random`.</span></span>
<span data-ttu-id="ed867-140">In het volgende voor beeld worden drie wille keurige getallen opgehaald die kleiner zijn dan 10.</span><span class="sxs-lookup"><span data-stu-id="ed867-140">The following example gets three random numbers less than 10.</span></span>

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### <span data-ttu-id="ed867-141">Voor beeld 13: gebruik de para meter input object met een lege teken reeks of $null</span><span class="sxs-lookup"><span data-stu-id="ed867-141">Example 13: Use the InputObject parameter with an empty string or $null</span></span>

<span data-ttu-id="ed867-142">In dit voor beeld wordt met de para meter **input object** een matrix opgegeven die een lege teken reeks ( `''` ) en bevat `$null` .</span><span class="sxs-lookup"><span data-stu-id="ed867-142">In this example, the **InputObject** parameter specifies an array that contains an empty string (`''`) and `$null`.</span></span>

```powershell
Get-Random -InputObject @('a','',$null)
```

<span data-ttu-id="ed867-143">`Get-Random` retourneert, een `a` lege teken reeks of `$null` .</span><span class="sxs-lookup"><span data-stu-id="ed867-143">`Get-Random` will return either `a`, empty string, or `$null`.</span></span> <span data-ttu-id="ed867-144">De lege Sting wordt weer gegeven als een lege regel en `$null` keert terug naar een Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="ed867-144">The empty sting displays as a blank line and `$null` returns to a PowerShell prompt.</span></span>

## <span data-ttu-id="ed867-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ed867-145">PARAMETERS</span></span>

### <span data-ttu-id="ed867-146">-Aantal</span><span class="sxs-lookup"><span data-stu-id="ed867-146">-Count</span></span>

<span data-ttu-id="ed867-147">Hiermee geeft u het aantal wille keurige objecten of getallen op dat moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ed867-147">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="ed867-148">De standaardwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="ed867-148">The default is 1.</span></span>

<span data-ttu-id="ed867-149">Als in combi natie met de `InputObject` waarde van **Count** het aantal objecten in de verzameling overschrijdt, `Get-Random` retourneert alle objecten in wille keurige volg orde.</span><span class="sxs-lookup"><span data-stu-id="ed867-149">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: RandomNumberParameterSet, RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ed867-150">-Input object</span><span class="sxs-lookup"><span data-stu-id="ed867-150">-InputObject</span></span>

<span data-ttu-id="ed867-151">Hiermee wordt een verzameling objecten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ed867-151">Specifies a collection of objects.</span></span> <span data-ttu-id="ed867-152">`Get-Random` Hiermee worden wille keurig geselecteerde objecten in wille keurige volg orde opgehaald uit de verzameling tot het aantal dat is opgegeven door **Count**.</span><span class="sxs-lookup"><span data-stu-id="ed867-152">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count**.</span></span> <span data-ttu-id="ed867-153">Voer de objecten, een variabele die de objecten bevat of een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ed867-153">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="ed867-154">U kunt ook een verzameling van objecten door sluizen naar `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="ed867-154">You can also pipe a collection of objects to `Get-Random`.</span></span>

<span data-ttu-id="ed867-155">Vanaf Power shell 7 accepteert de para meter **input object** matrices die een lege teken reeks of kunnen bevatten `$null` .</span><span class="sxs-lookup"><span data-stu-id="ed867-155">Beginning in PowerShell 7, the **InputObject** parameter accepts arrays that can contain an empty string or `$null`.</span></span> <span data-ttu-id="ed867-156">De matrix kan worden verzonden door de pijp lijn of als een **input object** parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="ed867-156">The array can be sent down the pipeline or as an **InputObject** parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet, ShuffleParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ed867-157">-Maximum</span><span class="sxs-lookup"><span data-stu-id="ed867-157">-Maximum</span></span>

<span data-ttu-id="ed867-158">Hiermee geeft u een maximum waarde op voor het wille keurig getal.</span><span class="sxs-lookup"><span data-stu-id="ed867-158">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="ed867-159">`Get-Random` retourneert een waarde die kleiner is dan het maximum (niet gelijk aan).</span><span class="sxs-lookup"><span data-stu-id="ed867-159">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="ed867-160">Voer een geheel getal, een zwevende-komma getal met dubbele precisie of een object in dat kan worden geconverteerd naar een geheel getal of dubbele waarde, zoals een numerieke teken reeks ("100").</span><span class="sxs-lookup"><span data-stu-id="ed867-160">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="ed867-161">De waarde van **maximum** moet groter dan (niet gelijk aan) de waarde van **minimum** zijn.</span><span class="sxs-lookup"><span data-stu-id="ed867-161">The value of **Maximum** must be greater than (not equal to) the value of **Minimum**.</span></span> <span data-ttu-id="ed867-162">Als de waarde van **maximum** of **minimum** een drijvende-komma getal is, `Get-Random` wordt een wille keurig geselecteerd drijvende-komma getal geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ed867-162">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="ed867-163">Als de waarde van **minimum** een 32-bits integer is op een 64-bits computer, is de standaard waarde van **maximum** **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="ed867-163">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue**.</span></span>

<span data-ttu-id="ed867-164">Als de waarde van **minimum** een double is (een getal met een drijvende komma), is de standaard waarde van **maximum** **Double. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="ed867-164">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue**.</span></span> <span data-ttu-id="ed867-165">Anders is de standaard waarde **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="ed867-165">Otherwise, the default value is **Int32.MaxValue**.</span></span>

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

### <span data-ttu-id="ed867-166">-Minimum</span><span class="sxs-lookup"><span data-stu-id="ed867-166">-Minimum</span></span>

<span data-ttu-id="ed867-167">Hiermee geeft u een minimum waarde voor het wille keurig getal op.</span><span class="sxs-lookup"><span data-stu-id="ed867-167">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="ed867-168">Voer een geheel getal, een zwevende-komma getal met dubbele precisie of een object in dat kan worden geconverteerd naar een geheel getal of dubbele waarde, zoals een numerieke teken reeks ("100").</span><span class="sxs-lookup"><span data-stu-id="ed867-168">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="ed867-169">De standaardwaarde is 0 (nul).</span><span class="sxs-lookup"><span data-stu-id="ed867-169">The default value is 0 (zero).</span></span>

<span data-ttu-id="ed867-170">De waarde van **minimum** moet kleiner zijn dan (niet gelijk aan) de waarde van **maximum**.</span><span class="sxs-lookup"><span data-stu-id="ed867-170">The value of **Minimum** must be less than (not equal to) the value of **Maximum**.</span></span> <span data-ttu-id="ed867-171">Als de waarde van **maximum** of **minimum** een drijvende-komma getal is, `Get-Random` wordt een wille keurig geselecteerd drijvende-komma getal geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ed867-171">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

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

### <span data-ttu-id="ed867-172">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="ed867-172">-SetSeed</span></span>

<span data-ttu-id="ed867-173">Hiermee geeft u een Seed-waarde op voor de generator voor wille keurige getallen.</span><span class="sxs-lookup"><span data-stu-id="ed867-173">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="ed867-174">Deze Seed-waarde wordt gebruikt voor de huidige opdracht en voor alle volgende `Get-Random` opdrachten in de huidige sessie totdat u **SetSeed** opnieuw gebruikt of de sessie sluit.</span><span class="sxs-lookup"><span data-stu-id="ed867-174">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="ed867-175">U kunt de Seed niet opnieuw instellen op de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="ed867-175">You can't reset the seed to its default value.</span></span>

<span data-ttu-id="ed867-176">De para meter **SetSeed** is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="ed867-176">The **SetSeed** parameter is not required.</span></span> <span data-ttu-id="ed867-177">`Get-Random`Maakt standaard gebruik van de methode [RandomNumberGenerator ()](/dotnet/api/system.security.cryptography.randomnumbergenerator) voor het genereren van een Seed-waarde.</span><span class="sxs-lookup"><span data-stu-id="ed867-177">By default, `Get-Random` uses the [RandomNumberGenerator()](/dotnet/api/system.security.cryptography.randomnumbergenerator) method to generate a seed value.</span></span> <span data-ttu-id="ed867-178">Omdat **SetSeed** resulteert in niet-wille keurig gedrag, wordt het normaal gesp roken alleen gebruikt bij het reproduceren van het gedrag, bijvoorbeeld bij het opsporen van fouten of het analyseren van een script dat `Get-Random` opdrachten bevat.</span><span class="sxs-lookup"><span data-stu-id="ed867-178">Because **SetSeed** results in non-random behavior, it's typically used only when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>

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

### <span data-ttu-id="ed867-179">-Wille keurige volg orde</span><span class="sxs-lookup"><span data-stu-id="ed867-179">-Shuffle</span></span>

<span data-ttu-id="ed867-180">Retourneert de volledige verzameling in een wille keurige volg orde.</span><span class="sxs-lookup"><span data-stu-id="ed867-180">Returns the entire collection in a randomized order.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShuffleParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ed867-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ed867-181">CommonParameters</span></span>

<span data-ttu-id="ed867-182">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ed867-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ed867-183">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ed867-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ed867-184">INVOER</span><span class="sxs-lookup"><span data-stu-id="ed867-184">INPUTS</span></span>

### <span data-ttu-id="ed867-185">System. object</span><span class="sxs-lookup"><span data-stu-id="ed867-185">System.Object</span></span>

<span data-ttu-id="ed867-186">U kunt een of meer objecten door sluizen.</span><span class="sxs-lookup"><span data-stu-id="ed867-186">You can pipe one or more objects.</span></span> <span data-ttu-id="ed867-187">`Get-Random` selecteert waarden wille keurig van de objecten met pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="ed867-187">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="ed867-188">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ed867-188">OUTPUTS</span></span>

### <span data-ttu-id="ed867-189">System. Int32, System. Int64, systeem. Double</span><span class="sxs-lookup"><span data-stu-id="ed867-189">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="ed867-190">`Get-Random` retourneert een geheel getal of getal met een drijvende komma of een object dat wille keurig uit een ingediende verzameling is geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="ed867-190">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="ed867-191">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ed867-191">NOTES</span></span>

<span data-ttu-id="ed867-192">`Get-Random` Hiermee stelt u een standaard zaad voor elke sessie in op basis van de systeem tijd klok wanneer de sessie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="ed867-192">`Get-Random` sets a default seed for each session based on the system time clock when the session starts.</span></span>

<span data-ttu-id="ed867-193">`Get-Random` retourneert niet altijd hetzelfde gegevens type als de invoer waarde.</span><span class="sxs-lookup"><span data-stu-id="ed867-193">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="ed867-194">In de volgende tabel ziet u het uitvoer type voor elk van de numerieke invoer typen.</span><span class="sxs-lookup"><span data-stu-id="ed867-194">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="ed867-195">Invoertype</span><span class="sxs-lookup"><span data-stu-id="ed867-195">Input Type</span></span> | <span data-ttu-id="ed867-196">Uitvoer type</span><span class="sxs-lookup"><span data-stu-id="ed867-196">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="ed867-197">SByte</span><span class="sxs-lookup"><span data-stu-id="ed867-197">SByte</span></span>    |   <span data-ttu-id="ed867-198">Dubbel</span><span class="sxs-lookup"><span data-stu-id="ed867-198">Double</span></span>    |
|    <span data-ttu-id="ed867-199">Byte</span><span class="sxs-lookup"><span data-stu-id="ed867-199">Byte</span></span>    |   <span data-ttu-id="ed867-200">Dubbel</span><span class="sxs-lookup"><span data-stu-id="ed867-200">Double</span></span>    |
|   <span data-ttu-id="ed867-201">Int16</span><span class="sxs-lookup"><span data-stu-id="ed867-201">Int16</span></span>    |   <span data-ttu-id="ed867-202">Dubbel</span><span class="sxs-lookup"><span data-stu-id="ed867-202">Double</span></span>    |
|   <span data-ttu-id="ed867-203">UInt16</span><span class="sxs-lookup"><span data-stu-id="ed867-203">UInt16</span></span>   |   <span data-ttu-id="ed867-204">Dubbel</span><span class="sxs-lookup"><span data-stu-id="ed867-204">Double</span></span>    |
|   <span data-ttu-id="ed867-205">Int32</span><span class="sxs-lookup"><span data-stu-id="ed867-205">Int32</span></span>    |    <span data-ttu-id="ed867-206">Int32</span><span class="sxs-lookup"><span data-stu-id="ed867-206">Int32</span></span>    |
|   <span data-ttu-id="ed867-207">UInt32</span><span class="sxs-lookup"><span data-stu-id="ed867-207">UInt32</span></span>   |   <span data-ttu-id="ed867-208">Dubbel</span><span class="sxs-lookup"><span data-stu-id="ed867-208">Double</span></span>    |
|   <span data-ttu-id="ed867-209">Int64</span><span class="sxs-lookup"><span data-stu-id="ed867-209">Int64</span></span>    |    <span data-ttu-id="ed867-210">Int64</span><span class="sxs-lookup"><span data-stu-id="ed867-210">Int64</span></span>    |
|   <span data-ttu-id="ed867-211">UInt64</span><span class="sxs-lookup"><span data-stu-id="ed867-211">UInt64</span></span>   |   <span data-ttu-id="ed867-212">Dubbel</span><span class="sxs-lookup"><span data-stu-id="ed867-212">Double</span></span>    |
|   <span data-ttu-id="ed867-213">Dubbel</span><span class="sxs-lookup"><span data-stu-id="ed867-213">Double</span></span>   |   <span data-ttu-id="ed867-214">Dubbel</span><span class="sxs-lookup"><span data-stu-id="ed867-214">Double</span></span>    |
|   <span data-ttu-id="ed867-215">Enkelvoudig</span><span class="sxs-lookup"><span data-stu-id="ed867-215">Single</span></span>   |   <span data-ttu-id="ed867-216">Dubbel</span><span class="sxs-lookup"><span data-stu-id="ed867-216">Double</span></span>    |

<span data-ttu-id="ed867-217">Vanaf Windows Power Shell 3,0 `Get-Random` ondersteunt 64-bits geheel getal.</span><span class="sxs-lookup"><span data-stu-id="ed867-217">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="ed867-218">In Windows Power Shell 2,0 worden alle waarden geconverteerd naar **System. Int32**.</span><span class="sxs-lookup"><span data-stu-id="ed867-218">In Windows PowerShell 2.0, all values are cast to **System.Int32**.</span></span>

<span data-ttu-id="ed867-219">Vanaf Power shell 7 accepteert de para meter **input object** in de para meter set **RandomListItemParameterSet** matrices die een lege teken reeks of bevatten `$null` .</span><span class="sxs-lookup"><span data-stu-id="ed867-219">Beginning in PowerShell 7, the **InputObject** parameter in the **RandomListItemParameterSet** parameter set accepts arrays that contain an empty string or `$null`.</span></span> <span data-ttu-id="ed867-220">In eerdere Power shell-versies heeft alleen de **maximum** para meter in de **RandomNumberParameterSet** -parameterset een lege teken reeks geaccepteerd of `$null` .</span><span class="sxs-lookup"><span data-stu-id="ed867-220">In earlier PowerShell versions, only the **Maximum** parameter in the **RandomNumberParameterSet** parameter set accepted an empty string or `$null`.</span></span>

## <span data-ttu-id="ed867-221">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ed867-221">RELATED LINKS</span></span>

