---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 007f8f2e377af0620d439f5a35be51aace032dc1
ms.sourcegitcommit: fa1a84c81e15f1ffac962110b0b4c850c1b173a0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2021
ms.locfileid: "99496033"
---
# <span data-ttu-id="1e622-102">Get-Random</span><span class="sxs-lookup"><span data-stu-id="1e622-102">Get-Random</span></span>

## <span data-ttu-id="1e622-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1e622-103">SYNOPSIS</span></span>
<span data-ttu-id="1e622-104">Haalt een wille keurig getal op of selecteert objecten wille keurig van een verzameling.</span><span class="sxs-lookup"><span data-stu-id="1e622-104">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="1e622-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1e622-105">SYNTAX</span></span>

### <span data-ttu-id="1e622-106">RandomNumberParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="1e622-106">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="1e622-107">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="1e622-107">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="1e622-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1e622-108">DESCRIPTION</span></span>

<span data-ttu-id="1e622-109">De `Get-Random` cmdlet haalt een wille keurig geselecteerd getal op.</span><span class="sxs-lookup"><span data-stu-id="1e622-109">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="1e622-110">Als u een verzameling objecten indient, worden er `Get-Random` een of meer wille keurig geselecteerde objecten uit de verzameling opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1e622-110">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="1e622-111">Zonder para meters of invoer `Get-Random` retourneert een opdracht een wille keurig geselecteerd 32-bits geheel getal van 0 (nul) en **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).</span><span class="sxs-lookup"><span data-stu-id="1e622-111">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="1e622-112">Standaard wordt `Get-Random` cryptografische, veilige wille keurigheid gegenereerd met behulp van de [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) -klasse.</span><span class="sxs-lookup"><span data-stu-id="1e622-112">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="1e622-113">U kunt de para meters van gebruiken `Get-Random` om de minimum-en maximum waarden op te geven, het aantal objecten dat wordt geretourneerd door een verzameling of een Seed-nummer.</span><span class="sxs-lookup"><span data-stu-id="1e622-113">You can use the parameters of `Get-Random` to specify the minimum and maximum values, the number of objects returned from a collection, or a seed number.</span></span>

> [!CAUTION]
> <span data-ttu-id="1e622-114">Als u de Seed opzettelijk instelt, wordt het niet-wille keurig Herhaal bare gedrag veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="1e622-114">Setting the seed deliberately results in non-random, repeatable behavior.</span></span> <span data-ttu-id="1e622-115">Het mag alleen worden gebruikt bij het reproduceren van gedrag, zoals bij het opsporen van fouten of het analyseren van een script dat `Get-Random` opdrachten bevat.</span><span class="sxs-lookup"><span data-stu-id="1e622-115">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="1e622-116">Deze Seed-waarde wordt gebruikt voor de huidige opdracht en voor alle volgende `Get-Random` opdrachten in de huidige sessie totdat u **SetSeed** opnieuw gebruikt of de sessie sluit.</span><span class="sxs-lookup"><span data-stu-id="1e622-116">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="1e622-117">U kunt de Seed niet opnieuw instellen op de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="1e622-117">You can't reset the seed to its default value.</span></span>

## <span data-ttu-id="1e622-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1e622-118">EXAMPLES</span></span>

### <span data-ttu-id="1e622-119">Voor beeld 1: een wille keurig geheel getal ophalen</span><span class="sxs-lookup"><span data-stu-id="1e622-119">Example 1: Get a random integer</span></span>

<span data-ttu-id="1e622-120">Met deze opdracht wordt een wille keurig geheel getal opgehaald tussen 0 (nul) en **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="1e622-120">This command gets a random integer between 0 (zero) and **Int32.MaxValue**.</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="1e622-121">Voor beeld 2: een wille keurig geheel getal ophalen tussen 0 en 99</span><span class="sxs-lookup"><span data-stu-id="1e622-121">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="1e622-122">Voor beeld 3: een wille keurig geheel getal ophalen tussen-100 en 99</span><span class="sxs-lookup"><span data-stu-id="1e622-122">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="1e622-123">Voor beeld 4: een wille keurig getal met drijvende komma ophalen</span><span class="sxs-lookup"><span data-stu-id="1e622-123">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="1e622-124">Met deze opdracht wordt een wille keurig drijvende-komma nummer opgehaald dat groter is dan of gelijk is aan 10,7 en kleiner is dan 20,92.</span><span class="sxs-lookup"><span data-stu-id="1e622-124">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="1e622-125">Voor beeld 5: een wille keurig geheel getal uit een matrix ophalen</span><span class="sxs-lookup"><span data-stu-id="1e622-125">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="1e622-126">Met deze opdracht wordt een wille keurig geselecteerd getal uit de opgegeven matrix opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1e622-126">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="1e622-127">Voor beeld 6: meerdere wille keurige gehele getallen ophalen uit een matrix</span><span class="sxs-lookup"><span data-stu-id="1e622-127">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="1e622-128">Met deze opdracht worden drie wille keurig geselecteerde getallen in wille keurige volg orde uit een matrix opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1e622-128">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="1e622-129">Voor beeld 7: een hele verzameling wille keurig toekennen</span><span class="sxs-lookup"><span data-stu-id="1e622-129">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="1e622-130">Met deze opdracht wordt de gehele verzameling in wille keurige volg orde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1e622-130">This command returns the entire collection in random order.</span></span>

<span data-ttu-id="1e622-131">De waarde van de para meter **aantal** is de eigenschap **MaxValue** static van integers.</span><span class="sxs-lookup"><span data-stu-id="1e622-131">The value of the **Count** parameter is the **MaxValue** static property of integers.</span></span>

<span data-ttu-id="1e622-132">Als u een volledige verzameling in een wille keurige volg orde wilt retour neren, voert u een getal in dat groter is dan of gelijk is aan het aantal objecten in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="1e622-132">To return an entire collection in random order, enter any number that is greater than or equal to the number of objects in the collection.</span></span>

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

### <span data-ttu-id="1e622-133">Voor beeld 8: een wille keurige, niet-numerieke waarde ophalen</span><span class="sxs-lookup"><span data-stu-id="1e622-133">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="1e622-134">Met deze opdracht wordt een wille keurige waarde uit een niet-numerieke collectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1e622-134">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="1e622-135">Voor beeld 9: de para meter SetSeed gebruiken</span><span class="sxs-lookup"><span data-stu-id="1e622-135">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="1e622-136">In dit voor beeld ziet u het effect van het gebruik van de para meter **SetSeed** .</span><span class="sxs-lookup"><span data-stu-id="1e622-136">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="1e622-137">Omdat **SetSeed** niet-wille keurig gedrag produceert, wordt het doorgaans alleen gebruikt om de resultaten te reproduceren, bijvoorbeeld bij het opsporen van fouten in een script of het analyseren van een-bestand.</span><span class="sxs-lookup"><span data-stu-id="1e622-137">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

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

### <span data-ttu-id="1e622-138">Voor beeld 10: wille keurige bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="1e622-138">Example 10: Get random files</span></span>

<span data-ttu-id="1e622-139">Deze opdrachten krijgen een wille keurig geselecteerd voor beeld van 50 bestanden van het `C:` station van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1e622-139">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="1e622-140">Voor beeld 11: roll-Fair-dobbel stenen</span><span class="sxs-lookup"><span data-stu-id="1e622-140">Example 11: Roll fair dice</span></span>

<span data-ttu-id="1e622-141">In dit voor beeld wordt een billijke dobbel steen van 1200 keer Gerolt en worden de resultaten geteld.</span><span class="sxs-lookup"><span data-stu-id="1e622-141">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="1e622-142">Met de eerste opdracht wordt `ForEach-Object` de aanroep herhaald `Get-Random` van de sluis in getallen (1-6).</span><span class="sxs-lookup"><span data-stu-id="1e622-142">The first command, `ForEach-Object` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="1e622-143">De resultaten worden gegroepeerd op basis van de waarde `Group-Object` en opgemaakt als een tabel met `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="1e622-143">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

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

### <span data-ttu-id="1e622-144">Voor beeld 12: de para meter aantal gebruiken</span><span class="sxs-lookup"><span data-stu-id="1e622-144">Example 12: Use the Count parameter</span></span>

<span data-ttu-id="1e622-145">U kunt nu de para meter **aantal** gebruiken zonder pijpleiding objecten aan `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="1e622-145">You can now use the **Count** parameter without piping objects to `Get-Random`.</span></span>
<span data-ttu-id="1e622-146">In het volgende voor beeld worden drie wille keurige getallen opgehaald die kleiner zijn dan 10.</span><span class="sxs-lookup"><span data-stu-id="1e622-146">The following example gets three random numbers less than 10.</span></span>

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### <span data-ttu-id="1e622-147">Voor beeld 13: gebruik de para meter input object met een lege teken reeks of $null</span><span class="sxs-lookup"><span data-stu-id="1e622-147">Example 13: Use the InputObject parameter with an empty string or $null</span></span>

<span data-ttu-id="1e622-148">In dit voor beeld wordt met de para meter **input object** een matrix opgegeven die een lege teken reeks ( `''` ) en bevat `$null` .</span><span class="sxs-lookup"><span data-stu-id="1e622-148">In this example, the **InputObject** parameter specifies an array that contains an empty string (`''`) and `$null`.</span></span>

```powershell
Get-Random -InputObject @('a','',$null)
```

<span data-ttu-id="1e622-149">`Get-Random` retourneert, een `a` lege teken reeks of `$null` .</span><span class="sxs-lookup"><span data-stu-id="1e622-149">`Get-Random` will return either `a`, empty string, or `$null`.</span></span> <span data-ttu-id="1e622-150">De lege Sting wordt weer gegeven als een lege regel en `$null` keert terug naar een Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="1e622-150">The empty sting displays as a blank line and `$null` returns to a PowerShell prompt.</span></span>

## <span data-ttu-id="1e622-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1e622-151">PARAMETERS</span></span>

### <span data-ttu-id="1e622-152">-Aantal</span><span class="sxs-lookup"><span data-stu-id="1e622-152">-Count</span></span>

<span data-ttu-id="1e622-153">Hiermee geeft u het aantal wille keurige objecten of getallen op dat moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1e622-153">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="1e622-154">De standaardwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="1e622-154">The default is 1.</span></span>

<span data-ttu-id="1e622-155">Als in combi natie met de `InputObject` waarde van **Count** het aantal objecten in de verzameling overschrijdt, `Get-Random` retourneert alle objecten in wille keurige volg orde.</span><span class="sxs-lookup"><span data-stu-id="1e622-155">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e622-156">-Input object</span><span class="sxs-lookup"><span data-stu-id="1e622-156">-InputObject</span></span>

<span data-ttu-id="1e622-157">Hiermee wordt een verzameling objecten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1e622-157">Specifies a collection of objects.</span></span> <span data-ttu-id="1e622-158">`Get-Random` Hiermee worden wille keurig geselecteerde objecten in wille keurige volg orde opgehaald uit de verzameling tot het aantal dat is opgegeven door **Count**.</span><span class="sxs-lookup"><span data-stu-id="1e622-158">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count**.</span></span> <span data-ttu-id="1e622-159">Voer de objecten, een variabele die de objecten bevat of een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1e622-159">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="1e622-160">U kunt ook een verzameling van objecten door sluizen naar `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="1e622-160">You can also pipe a collection of objects to `Get-Random`.</span></span>

<span data-ttu-id="1e622-161">Vanaf Power shell 7 accepteert de para meter **input object** matrices die een lege teken reeks of kunnen bevatten `$null` .</span><span class="sxs-lookup"><span data-stu-id="1e622-161">Beginning in PowerShell 7, the **InputObject** parameter accepts arrays that can contain an empty string or `$null`.</span></span> <span data-ttu-id="1e622-162">De matrix kan worden verzonden door de pijp lijn of als een **input object** parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="1e622-162">The array can be sent down the pipeline or as an **InputObject** parameter value.</span></span>

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

### <span data-ttu-id="1e622-163">-Maximum</span><span class="sxs-lookup"><span data-stu-id="1e622-163">-Maximum</span></span>

<span data-ttu-id="1e622-164">Hiermee geeft u een maximum waarde op voor het wille keurig getal.</span><span class="sxs-lookup"><span data-stu-id="1e622-164">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="1e622-165">`Get-Random` retourneert een waarde die kleiner is dan het maximum (niet gelijk aan).</span><span class="sxs-lookup"><span data-stu-id="1e622-165">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="1e622-166">Voer een geheel getal, een zwevende-komma getal met dubbele precisie of een object in dat kan worden geconverteerd naar een geheel getal of dubbele waarde, zoals een numerieke teken reeks ("100").</span><span class="sxs-lookup"><span data-stu-id="1e622-166">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="1e622-167">De waarde van **maximum** moet groter dan (niet gelijk aan) de waarde van **minimum** zijn.</span><span class="sxs-lookup"><span data-stu-id="1e622-167">The value of **Maximum** must be greater than (not equal to) the value of **Minimum**.</span></span> <span data-ttu-id="1e622-168">Als de waarde van **maximum** of **minimum** een drijvende-komma getal is, `Get-Random` wordt een wille keurig geselecteerd drijvende-komma getal geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1e622-168">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="1e622-169">Als de waarde van **minimum** een 32-bits integer is op een 64-bits computer, is de standaard waarde van **maximum** **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="1e622-169">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue**.</span></span>

<span data-ttu-id="1e622-170">Als de waarde van **minimum** een double is (een getal met een drijvende komma), is de standaard waarde van **maximum** **Double. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="1e622-170">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue**.</span></span> <span data-ttu-id="1e622-171">Anders is de standaard waarde **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="1e622-171">Otherwise, the default value is **Int32.MaxValue**.</span></span>

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

### <span data-ttu-id="1e622-172">-Minimum</span><span class="sxs-lookup"><span data-stu-id="1e622-172">-Minimum</span></span>

<span data-ttu-id="1e622-173">Hiermee geeft u een minimum waarde voor het wille keurig getal op.</span><span class="sxs-lookup"><span data-stu-id="1e622-173">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="1e622-174">Voer een geheel getal, een zwevende-komma getal met dubbele precisie of een object in dat kan worden geconverteerd naar een geheel getal of dubbele waarde, zoals een numerieke teken reeks ("100").</span><span class="sxs-lookup"><span data-stu-id="1e622-174">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="1e622-175">De standaardwaarde is 0 (nul).</span><span class="sxs-lookup"><span data-stu-id="1e622-175">The default value is 0 (zero).</span></span>

<span data-ttu-id="1e622-176">De waarde van **minimum** moet kleiner zijn dan (niet gelijk aan) de waarde van **maximum**.</span><span class="sxs-lookup"><span data-stu-id="1e622-176">The value of **Minimum** must be less than (not equal to) the value of **Maximum**.</span></span> <span data-ttu-id="1e622-177">Als de waarde van **maximum** of **minimum** een drijvende-komma getal is, `Get-Random` wordt een wille keurig geselecteerd drijvende-komma getal geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1e622-177">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

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

### <span data-ttu-id="1e622-178">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="1e622-178">-SetSeed</span></span>

<span data-ttu-id="1e622-179">Hiermee geeft u een Seed-waarde op voor de generator voor wille keurige getallen.</span><span class="sxs-lookup"><span data-stu-id="1e622-179">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="1e622-180">Wanneer u **SetSeed** gebruikt, gebruikt de cmdlet de methode [System. Random](/dotnet/api/system.random) om Pseudorandom-nummers te genereren, die niet cryptografisch veilig zijn.</span><span class="sxs-lookup"><span data-stu-id="1e622-180">When you use **SetSeed**, the cmdlet uses the [System.Random](/dotnet/api/system.random) method to generate pseudorandom numbers, which is not cryptographically secure.</span></span>

> [!CAUTION]
> <span data-ttu-id="1e622-181">De Seed-resultaten worden ingesteld op niet-wille keurig gedrag.</span><span class="sxs-lookup"><span data-stu-id="1e622-181">Setting the seed results in non-random behavior.</span></span> <span data-ttu-id="1e622-182">Het mag alleen worden gebruikt bij het reproduceren van gedrag, zoals bij het opsporen van fouten of het analyseren van een script dat `Get-Random` opdrachten bevat.</span><span class="sxs-lookup"><span data-stu-id="1e622-182">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="1e622-183">Deze Seed-waarde wordt gebruikt voor de huidige opdracht en voor alle volgende `Get-Random` opdrachten in de huidige sessie totdat u **SetSeed** opnieuw gebruikt of de sessie sluit.</span><span class="sxs-lookup"><span data-stu-id="1e622-183">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="1e622-184">U kunt de Seed niet opnieuw instellen op de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="1e622-184">You can't reset the seed to its default value.</span></span>

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

### <span data-ttu-id="1e622-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1e622-185">CommonParameters</span></span>

<span data-ttu-id="1e622-186">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1e622-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1e622-187">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1e622-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1e622-188">INVOER</span><span class="sxs-lookup"><span data-stu-id="1e622-188">INPUTS</span></span>

### <span data-ttu-id="1e622-189">System. object</span><span class="sxs-lookup"><span data-stu-id="1e622-189">System.Object</span></span>

<span data-ttu-id="1e622-190">U kunt een of meer objecten door sluizen.</span><span class="sxs-lookup"><span data-stu-id="1e622-190">You can pipe one or more objects.</span></span> <span data-ttu-id="1e622-191">`Get-Random` selecteert waarden wille keurig van de objecten met pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="1e622-191">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="1e622-192">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1e622-192">OUTPUTS</span></span>

### <span data-ttu-id="1e622-193">System. Int32, System. Int64, systeem. Double</span><span class="sxs-lookup"><span data-stu-id="1e622-193">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="1e622-194">`Get-Random` retourneert een geheel getal of getal met een drijvende komma of een object dat wille keurig uit een ingediende verzameling is geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="1e622-194">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="1e622-195">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1e622-195">NOTES</span></span>

<span data-ttu-id="1e622-196">Standaard wordt `Get-Random` cryptografische, veilige wille keurigheid gegenereerd met behulp van de [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) -klasse.</span><span class="sxs-lookup"><span data-stu-id="1e622-196">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="1e622-197">`Get-Random` retourneert niet altijd hetzelfde gegevens type als de invoer waarde.</span><span class="sxs-lookup"><span data-stu-id="1e622-197">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="1e622-198">In de volgende tabel ziet u het uitvoer type voor elk van de numerieke invoer typen.</span><span class="sxs-lookup"><span data-stu-id="1e622-198">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="1e622-199">Invoertype</span><span class="sxs-lookup"><span data-stu-id="1e622-199">Input Type</span></span> | <span data-ttu-id="1e622-200">Uitvoer type</span><span class="sxs-lookup"><span data-stu-id="1e622-200">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="1e622-201">SByte</span><span class="sxs-lookup"><span data-stu-id="1e622-201">SByte</span></span>    |   <span data-ttu-id="1e622-202">Dubbel</span><span class="sxs-lookup"><span data-stu-id="1e622-202">Double</span></span>    |
|    <span data-ttu-id="1e622-203">Byte</span><span class="sxs-lookup"><span data-stu-id="1e622-203">Byte</span></span>    |   <span data-ttu-id="1e622-204">Dubbel</span><span class="sxs-lookup"><span data-stu-id="1e622-204">Double</span></span>    |
|   <span data-ttu-id="1e622-205">Int16</span><span class="sxs-lookup"><span data-stu-id="1e622-205">Int16</span></span>    |   <span data-ttu-id="1e622-206">Dubbel</span><span class="sxs-lookup"><span data-stu-id="1e622-206">Double</span></span>    |
|   <span data-ttu-id="1e622-207">UInt16</span><span class="sxs-lookup"><span data-stu-id="1e622-207">UInt16</span></span>   |   <span data-ttu-id="1e622-208">Dubbel</span><span class="sxs-lookup"><span data-stu-id="1e622-208">Double</span></span>    |
|   <span data-ttu-id="1e622-209">Int32</span><span class="sxs-lookup"><span data-stu-id="1e622-209">Int32</span></span>    |    <span data-ttu-id="1e622-210">Int32</span><span class="sxs-lookup"><span data-stu-id="1e622-210">Int32</span></span>    |
|   <span data-ttu-id="1e622-211">UInt32</span><span class="sxs-lookup"><span data-stu-id="1e622-211">UInt32</span></span>   |   <span data-ttu-id="1e622-212">Dubbel</span><span class="sxs-lookup"><span data-stu-id="1e622-212">Double</span></span>    |
|   <span data-ttu-id="1e622-213">Int64</span><span class="sxs-lookup"><span data-stu-id="1e622-213">Int64</span></span>    |    <span data-ttu-id="1e622-214">Int64</span><span class="sxs-lookup"><span data-stu-id="1e622-214">Int64</span></span>    |
|   <span data-ttu-id="1e622-215">UInt64</span><span class="sxs-lookup"><span data-stu-id="1e622-215">UInt64</span></span>   |   <span data-ttu-id="1e622-216">Dubbel</span><span class="sxs-lookup"><span data-stu-id="1e622-216">Double</span></span>    |
|   <span data-ttu-id="1e622-217">Dubbel</span><span class="sxs-lookup"><span data-stu-id="1e622-217">Double</span></span>   |   <span data-ttu-id="1e622-218">Dubbel</span><span class="sxs-lookup"><span data-stu-id="1e622-218">Double</span></span>    |
|   <span data-ttu-id="1e622-219">Enkelvoudig</span><span class="sxs-lookup"><span data-stu-id="1e622-219">Single</span></span>   |   <span data-ttu-id="1e622-220">Dubbel</span><span class="sxs-lookup"><span data-stu-id="1e622-220">Double</span></span>    |

<span data-ttu-id="1e622-221">Vanaf Windows Power Shell 3,0 `Get-Random` ondersteunt 64-bits geheel getal.</span><span class="sxs-lookup"><span data-stu-id="1e622-221">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="1e622-222">In Windows Power Shell 2,0 worden alle waarden geconverteerd naar **System. Int32**.</span><span class="sxs-lookup"><span data-stu-id="1e622-222">In Windows PowerShell 2.0, all values are cast to **System.Int32**.</span></span>

<span data-ttu-id="1e622-223">Vanaf Power shell 7 accepteert de para meter **input object** in de para meter set **RandomListItemParameterSet** matrices die een lege teken reeks of bevatten `$null` .</span><span class="sxs-lookup"><span data-stu-id="1e622-223">Beginning in PowerShell 7, the **InputObject** parameter in the **RandomListItemParameterSet** parameter set accepts arrays that contain an empty string or `$null`.</span></span> <span data-ttu-id="1e622-224">In eerdere Power shell-versies heeft alleen de **maximum** para meter in de **RandomNumberParameterSet** -parameterset een lege teken reeks geaccepteerd of `$null` .</span><span class="sxs-lookup"><span data-stu-id="1e622-224">In earlier PowerShell versions, only the **Maximum** parameter in the **RandomNumberParameterSet** parameter set accepted an empty string or `$null`.</span></span>

## <span data-ttu-id="1e622-225">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1e622-225">RELATED LINKS</span></span>

[<span data-ttu-id="1e622-226">System. Security. Cryptography. RandomNumberGenerator ()</span><span class="sxs-lookup"><span data-stu-id="1e622-226">System.Security.Cryptography.RandomNumberGenerator()</span></span>](/dotnet/api/system.security.cryptography.randomnumbergenerator)

[<span data-ttu-id="1e622-227">Systeem. wille keurig</span><span class="sxs-lookup"><span data-stu-id="1e622-227">Sytem.Random</span></span>](/dotnet/api/system.random)
