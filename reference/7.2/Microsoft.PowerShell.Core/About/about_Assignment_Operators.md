---
description: Hierin wordt beschreven hoe u Opera tors kunt gebruiken om waarden toe te wijzen aan variabelen.
ms.date: 04/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_assignment_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Assignment_Operators
ms.openlocfilehash: 4e21c9d0f2b0a47cd4db10ee515ceb07548eb971
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706128"
---
# <a name="about-assignment-operators"></a><span data-ttu-id="ea1ab-103">Over toewijzings operatoren</span><span class="sxs-lookup"><span data-stu-id="ea1ab-103">About Assignment Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="ea1ab-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="ea1ab-104">Short description</span></span>
<span data-ttu-id="ea1ab-105">Hierin wordt beschreven hoe u Opera tors kunt gebruiken om waarden toe te wijzen aan variabelen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-105">Describes how to use operators to assign values to variables.</span></span>

## <a name="long-description"></a><span data-ttu-id="ea1ab-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="ea1ab-106">Long description</span></span>

<span data-ttu-id="ea1ab-107">Toewijzings operatoren wijzen een of meer waarden toe aan een variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-107">Assignment operators assign one or more values to a variable.</span></span> <span data-ttu-id="ea1ab-108">Ze kunnen numerieke bewerkingen uitvoeren op de waarden vóór de toewijzing.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-108">They can perform numeric operations on the values before the assignment.</span></span>

<span data-ttu-id="ea1ab-109">Power shell ondersteunt de volgende toewijzings operatoren.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-109">PowerShell supports the following assignment operators.</span></span>

|<span data-ttu-id="ea1ab-110">Operator</span><span class="sxs-lookup"><span data-stu-id="ea1ab-110">Operator</span></span>|<span data-ttu-id="ea1ab-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ea1ab-111">Description</span></span>                                                  |
|--------|-------------------------------------------------------------|
|=       |<span data-ttu-id="ea1ab-112">Hiermee stelt u de waarde van een variabele in op de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-112">Sets the value of a variable to the specified value.</span></span>         |
|+=      |<span data-ttu-id="ea1ab-113">Verhoogt de waarde van een variabele met de opgegeven waarde, of</span><span class="sxs-lookup"><span data-stu-id="ea1ab-113">Increases the value of a variable by the specified value, or</span></span> |
|        |<span data-ttu-id="ea1ab-114">Hiermee wordt de opgegeven waarde aan de bestaande waarde toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-114">appends the specified value to the existing value.</span></span>           |
|-=      |<span data-ttu-id="ea1ab-115">Hiermee verkleint u de waarde van een variabele met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-115">Decreases the value of a variable by the specified value.</span></span>    |
|*=      |<span data-ttu-id="ea1ab-116">Vermenigvuldigt de waarde van een variabele met de opgegeven waarde, of</span><span class="sxs-lookup"><span data-stu-id="ea1ab-116">Multiplies the value of a variable by the specified value, or</span></span>|
|        |<span data-ttu-id="ea1ab-117">Hiermee wordt de opgegeven waarde aan de bestaande waarde toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-117">appends the specified value to the existing value.</span></span>           |
|/=      |<span data-ttu-id="ea1ab-118">Hiermee wordt de waarde van een variabele opgedeeld op basis van de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-118">Divides the value of a variable by the specified value.</span></span>      |
|%=      |<span data-ttu-id="ea1ab-119">Hiermee wordt de waarde van een variabele opgedeeld op basis van de opgegeven waarde en</span><span class="sxs-lookup"><span data-stu-id="ea1ab-119">Divides the value of a variable by the specified value and</span></span>   |
|        |<span data-ttu-id="ea1ab-120">wijst vervolgens de rest (modulus) toe aan de variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-120">then assigns the remainder (modulus) to the variable.</span></span>        |
|++      |<span data-ttu-id="ea1ab-121">Verhoogt de waarde van een variabele, toewijs bare eigenschap of</span><span class="sxs-lookup"><span data-stu-id="ea1ab-121">Increases the value of a variable, assignable property, or</span></span>   |
|        |<span data-ttu-id="ea1ab-122">matrix element door 1.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-122">array element by 1.</span></span>                                          |
|--      |<span data-ttu-id="ea1ab-123">Hiermee verkleint u de waarde van een variabele, toewijs bare eigenschap of</span><span class="sxs-lookup"><span data-stu-id="ea1ab-123">Decreases the value of a variable, assignable property, or</span></span>   |
|        |<span data-ttu-id="ea1ab-124">matrix element door 1.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-124">array element by 1.</span></span>                                          |

## <a name="syntax"></a><span data-ttu-id="ea1ab-125">Syntax</span><span class="sxs-lookup"><span data-stu-id="ea1ab-125">Syntax</span></span>

<span data-ttu-id="ea1ab-126">De syntaxis van de toewijzings operators is als volgt:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-126">The syntax of the assignment operators is as follows:</span></span>

<span data-ttu-id="ea1ab-127">`<assignable-expression>` `<assignment-operator>` `<value>`</span><span class="sxs-lookup"><span data-stu-id="ea1ab-127">`<assignable-expression>` `<assignment-operator>` `<value>`</span></span>

<span data-ttu-id="ea1ab-128">Toewijs bare expressies bevatten variabelen en eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-128">Assignable expressions include variables and properties.</span></span> <span data-ttu-id="ea1ab-129">De waarde kan één waarde, een matrix met waarden of een opdracht, expressie of instructie zijn.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-129">The value can be a single value, an array of values, or a command, expression, or statement.</span></span>

<span data-ttu-id="ea1ab-130">De Opera tors voor verhogen en verlagen zijn unaire Opera tors.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-130">The increment and decrement operators are unary operators.</span></span> <span data-ttu-id="ea1ab-131">Elk heeft een voor voegsel-en achtervoegsel-versie.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-131">Each has prefix and postfix versions.</span></span>

`<assignable-expression><operator>`
`<operator><assignable-expression>`

<span data-ttu-id="ea1ab-132">De toewijs bare expressie moet een getal zijn of moet worden geconverteerd naar een getal.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-132">The assignable expression must be a number or it must be convertible to a number.</span></span>

## <a name="assigning-values"></a><span data-ttu-id="ea1ab-133">Waarden toewijzen</span><span class="sxs-lookup"><span data-stu-id="ea1ab-133">Assigning values</span></span>

<span data-ttu-id="ea1ab-134">Variabelen hebben de naam geheugen ruimten die waarden opslaan.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-134">Variables are named memory spaces that store values.</span></span> <span data-ttu-id="ea1ab-135">U slaat de waarden in variabelen op met behulp van de toewijzings operator `=` .</span><span class="sxs-lookup"><span data-stu-id="ea1ab-135">You store the values in variables by using the assignment operator `=`.</span></span> <span data-ttu-id="ea1ab-136">De nieuwe waarde kan de bestaande waarde van de variabele vervangen, of u kunt een nieuwe waarde toevoegen aan de bestaande waarde.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-136">The new value can replace the existing value of the variable, or you can append a new value to the existing value.</span></span>

<span data-ttu-id="ea1ab-137">De operator basis toewijzing is het gelijkteken `=` `(ASCII 61)` .</span><span class="sxs-lookup"><span data-stu-id="ea1ab-137">The basic assignment operator is the equal sign `=` `(ASCII 61)`.</span></span> <span data-ttu-id="ea1ab-138">Met de volgende instructie wordt de waarde Power shell bijvoorbeeld toegewezen aan de `$MyShell` variabele:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-138">For example, the following statement assigns the value PowerShell to the `$MyShell` variable:</span></span>

```powershell
$MyShell = "PowerShell"
```

<span data-ttu-id="ea1ab-139">Wanneer u een waarde aan een variabele toewijst in Power shell, wordt de variabele gemaakt als deze nog niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-139">When you assign a value to a variable in PowerShell, the variable is created if it did not already exist.</span></span> <span data-ttu-id="ea1ab-140">De eerste van de volgende twee toewijzings instructies maakt bijvoorbeeld de `$a` variabele en wijst de waarde 6 toe aan `$a` .</span><span class="sxs-lookup"><span data-stu-id="ea1ab-140">For example, the first of the following two assignment statements creates the `$a` variable and assigns a value of 6 to `$a`.</span></span> <span data-ttu-id="ea1ab-141">De tweede toewijzings instructie wijst een waarde van 12 toe aan `$a` .</span><span class="sxs-lookup"><span data-stu-id="ea1ab-141">The second assignment statement assigns a value of 12 to `$a`.</span></span> <span data-ttu-id="ea1ab-142">Met de eerste instructie maakt u een nieuwe variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-142">The first statement creates a new variable.</span></span> <span data-ttu-id="ea1ab-143">De tweede instructie wijzigt alleen de waarde:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-143">The second statement changes only its value:</span></span>

```powershell
$a = 6
$a = 12
```

<span data-ttu-id="ea1ab-144">Variabelen in Power Shell hebben geen specifiek gegevens type tenzij u ze cast.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-144">Variables in PowerShell do not have a specific data type unless you cast them.</span></span>
<span data-ttu-id="ea1ab-145">Wanneer een variabele slechts één object bevat, neemt de variabele het gegevens type van dat object.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-145">When a variable contains only one object, the variable takes the data type of that object.</span></span> <span data-ttu-id="ea1ab-146">Wanneer een variabele een verzameling objecten bevat, heeft de variabele het gegevens type System. object.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-146">When a variable contains a collection of objects, the variable has the System.Object data type.</span></span> <span data-ttu-id="ea1ab-147">Daarom kunt u elk type object toewijzen aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-147">Therefore, you can assign any type of object to the collection.</span></span> <span data-ttu-id="ea1ab-148">In het volgende voor beeld ziet u dat u proces objecten, service objecten, teken reeksen en gehele getallen kunt toevoegen aan een variabele zonder een fout te genereren:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-148">The following example shows that you can add process objects, service objects, strings, and integers to a variable without generating an error:</span></span>

```powershell
$a = Get-Process
$a += Get-Service
$a += "string"
$a += 12
```

<span data-ttu-id="ea1ab-149">Omdat de toewijzings operator `=` een lagere prioriteit heeft dan de pijplijn operator `|` , zijn haakjes niet vereist om het resultaat van een opdracht pijplijn aan een variabele toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-149">Because the assignment operator `=` has a lower precedence than the pipeline operator `|`, parentheses are not required to assign the result of a command pipeline to a variable.</span></span> <span data-ttu-id="ea1ab-150">Met de volgende opdracht worden bijvoorbeeld de services op de computer gesorteerd en vervolgens de gesorteerde services toegewezen aan de `$a` variabele:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-150">For example, the following command sorts the services on the computer and then assigns the sorted services to the `$a` variable:</span></span>

```powershell
$a = Get-Service | Sort-Object -Property name
```

<span data-ttu-id="ea1ab-151">U kunt de waarde die is gemaakt door een instructie ook toewijzen aan een variabele, zoals in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-151">You can also assign the value created by a statement to a variable, as in the following example:</span></span>

```powershell
$a = if ($b -lt 0) { 0 } else { $b }
```

<span data-ttu-id="ea1ab-152">In dit voor beeld wordt nul toegewezen aan de `$a` variabele als de waarde van `$b` kleiner dan nul is.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-152">This example assigns zero to the `$a` variable if the value of `$b` is less than zero.</span></span> <span data-ttu-id="ea1ab-153">De waarde van `$b` wordt toegewezen aan `$a` als de waarde van `$b` is niet kleiner dan nul.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-153">It assigns the value of `$b` to `$a` if the value of `$b` is not less than zero.</span></span>

### <a name="the-assignment-operator"></a><span data-ttu-id="ea1ab-154">De toewijzings operator</span><span class="sxs-lookup"><span data-stu-id="ea1ab-154">The assignment operator</span></span>

<span data-ttu-id="ea1ab-155">De toewijzings operator `=` wijst waarden toe aan variabelen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-155">The assignment operator `=` assigns values to variables.</span></span> <span data-ttu-id="ea1ab-156">Als de variabele al een waarde heeft, vervangt de toewijzings operator `=` de waarde zonder waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-156">If the variable already has a value, the assignment operator `=` replaces the value without warning.</span></span>

<span data-ttu-id="ea1ab-157">Met de volgende instructie wordt de waarde 6 van het gehele getal toegewezen aan de `$a` variabele:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-157">The following statement assigns the integer value 6 to the `$a` variable:</span></span>

```powershell
$a = 6
```

<span data-ttu-id="ea1ab-158">Als u een teken reeks waarde wilt toewijzen aan een variabele, plaatst u de teken reeks waarde tussen aanhalings tekens, als volgt:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-158">To assign a string value to a variable, enclose the string value in quotation marks, as follows:</span></span>

```powershell
$a = "baseball"
```

<span data-ttu-id="ea1ab-159">Als u een matrix (meerdere waarden) wilt toewijzen aan een variabele, scheidt u de waarden met komma's, als volgt:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-159">To assign an array (multiple values) to a variable, separate the values with commas, as follows:</span></span>

```powershell
$a = "apple", "orange", "lemon", "grape"
```

<span data-ttu-id="ea1ab-160">Als u een hash-tabel aan een variabele wilt toewijzen, gebruikt u de standaard hash-tabel notatie in Power shell.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-160">To assign a hash table to a variable, use the standard hash table notation in PowerShell.</span></span> <span data-ttu-id="ea1ab-161">Typ een at `@` -teken gevolgd door sleutel-waardeparen, gescheiden door punt komma's `;` en tussen accolades `{ }` .</span><span class="sxs-lookup"><span data-stu-id="ea1ab-161">Type an at sign `@` followed by key/value pairs that are separated by semicolons `;` and enclosed in braces `{ }`.</span></span> <span data-ttu-id="ea1ab-162">Als u bijvoorbeeld een hash-tabel aan de variabele wilt toewijzen `$a` , typt u:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-162">For example, to assign a hash table to the `$a` variable, type:</span></span>

```powershell
$a = @{one=1; two=2; three=3}
```

<span data-ttu-id="ea1ab-163">Voor het toewijzen van hexadecimale waarden aan een variabele, wordt de waarde voorafgegaan door `0x` .</span><span class="sxs-lookup"><span data-stu-id="ea1ab-163">To assign hexadecimal values to a variable, precede the value with `0x`.</span></span>
<span data-ttu-id="ea1ab-164">Power shell converteert de hexadecimale waarde (0x10) naar een decimale waarde (in dit geval 16) en wijst die waarde toe aan de `$a` variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-164">PowerShell converts the hexadecimal value (0x10) to a decimal value (in this case, 16) and assigns that value to the `$a` variable.</span></span> <span data-ttu-id="ea1ab-165">Als u bijvoorbeeld een waarde van 0x10 wilt toewijzen aan de `$a` variabele, typt u:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-165">For example, to assign a value of 0x10 to the `$a` variable, type:</span></span>

```powershell
$a = 0x10
```

<span data-ttu-id="ea1ab-166">Als u een exponentiële waarde aan een variabele wilt toewijzen, typt u het hoofd nummer, de letter `e` en een getal dat een meervoud van 10 vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-166">To assign an exponential value to a variable, type the root number, the letter `e`, and a number that represents a multiple of 10.</span></span> <span data-ttu-id="ea1ab-167">Als u bijvoorbeeld een waarde van 3,1415 wilt toewijzen aan de kracht van 1.000 `$a` , typt u:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-167">For example, to assign a value of 3.1415 to the power of 1,000 to the `$a` variable, type:</span></span>

```powershell
$a = 3.1415e3
```

<span data-ttu-id="ea1ab-168">In Power shell kunnen KB `KB` , mega bytes en gigabytes ook worden geconverteerd `MB` `GB` naar bytes.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-168">PowerShell can also convert kilobytes `KB`, megabytes `MB`, and gigabytes `GB` into bytes.</span></span> <span data-ttu-id="ea1ab-169">Als u bijvoorbeeld een waarde van 10 kilo bytes wilt toewijzen aan de `$a` variabele, typt u:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-169">For example, to assign a value of 10 kilobytes to the `$a` variable, type:</span></span>

```powershell
$a = 10kb
```

### <a name="the-assignment-by-addition-operator"></a><span data-ttu-id="ea1ab-170">De operator Assignment by plus</span><span class="sxs-lookup"><span data-stu-id="ea1ab-170">The assignment by addition operator</span></span>

<span data-ttu-id="ea1ab-171">De operator Assignment by plus `+=` verhoogt de waarde van een variabele of voegt de opgegeven waarde toe aan de bestaande waarde.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-171">The assignment by addition operator `+=` either increments the value of a variable or appends the specified value to the existing value.</span></span> <span data-ttu-id="ea1ab-172">De actie is afhankelijk van het feit of de variabele een numeriek of een teken reeks type heeft en of de variabele een enkele waarde (scalair) of meerdere waarden (een verzameling) bevat.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-172">The action depends on whether the variable has a numeric or string type and whether the variable contains a single value (a scalar) or multiple values (a collection).</span></span>

<span data-ttu-id="ea1ab-173">De `+=` operator combineert twee bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-173">The `+=` operator combines two operations.</span></span> <span data-ttu-id="ea1ab-174">Eerst wordt toegevoegd en vervolgens toegewezen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-174">First, it adds, and then it assigns.</span></span>
<span data-ttu-id="ea1ab-175">Daarom zijn de volgende instructies gelijkwaardig:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-175">Therefore, the following statements are equivalent:</span></span>

```powershell
$a += 2
$a = ($a + 2)
```

<span data-ttu-id="ea1ab-176">Wanneer de variabele één numerieke waarde bevat, wordt de `+=` huidige waarde verhoogd met de hoeveelheid aan de rechter kant van de operator.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-176">When the variable contains a single numeric value, the `+=` operator increments the existing value by the amount on the right side of the operator.</span></span> <span data-ttu-id="ea1ab-177">Vervolgens wijst de operator de resulterende waarde toe aan de variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-177">Then, the operator assigns the resulting value to the variable.</span></span> <span data-ttu-id="ea1ab-178">In het volgende voor beeld ziet u hoe u de operator kunt gebruiken `+=` om de waarde van een variabele te verhogen:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-178">The following example shows how to use the `+=` operator to increase the value of a variable:</span></span>

```powershell
$a = 4
$a += 2
$a
```

```
6
```

<span data-ttu-id="ea1ab-179">Wanneer de waarde van de variabele een teken reeks is, wordt de waarde aan de rechter kant van de operator toegevoegd aan de teken reeks, als volgt:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-179">When the value of the variable is a string, the value on the right side of the operator is appended to the string, as follows:</span></span>

```powershell
$a = "Windows"
$a += " PowerShell"
$a
```

```
Windows PowerShell
```

<span data-ttu-id="ea1ab-180">Wanneer de waarde van de variabele een matrix is, `+=` voegt de operator de waarden aan de rechter kant van de operator toe aan de matrix.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-180">When the value of the variable is an array, the `+=` operator appends the values on the right side of the operator to the array.</span></span> <span data-ttu-id="ea1ab-181">Tenzij de matrix expliciet wordt getypeerd door cast, kunt u als volgt een wille keurig type waarde aan de matrix toevoegen:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-181">Unless the array is explicitly typed by casting, you can append any type of value to the array, as follows:</span></span>

```powershell
$a = 1,2,3
$a += 2
$a
```

```
1
2
3
2
```

<span data-ttu-id="ea1ab-182">en</span><span class="sxs-lookup"><span data-stu-id="ea1ab-182">and</span></span>

```powershell
$a += "String"
$a
```

```
1
2
3
2
String
```

<span data-ttu-id="ea1ab-183">Wanneer de waarde van een variabele een hash-tabel is, `+=` voegt de operator de waarde aan de rechter kant van de operator toe aan de hashtabel.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-183">When the value of a variable is a hash table, the `+=` operator appends the value on the right side of the operator to the hash table.</span></span> <span data-ttu-id="ea1ab-184">Omdat het enige type dat u aan een hashtabel kunt toevoegen, echter een andere hash-tabel is, mislukken alle andere toewijzingen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-184">However, because the only type that you can add to a hash table is another hash table, all other assignments fail.</span></span>

<span data-ttu-id="ea1ab-185">Met de volgende opdracht wordt bijvoorbeeld een hash-tabel aan de `$a` variabele toegewezen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-185">For example, the following command assigns a hash table to the `$a` variable.</span></span>
<span data-ttu-id="ea1ab-186">Vervolgens wordt de operator gebruikt `+=` om een andere hash-tabel toe te voegen aan de bestaande hash-tabel, waardoor een nieuwe sleutel/waarde-paar in feite wordt toegevoegd aan de bestaande hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-186">Then, it uses the `+=` operator to append another hash table to the existing hash table, effectively adding a new key/value pair to the existing hash table.</span></span>
<span data-ttu-id="ea1ab-187">Deze opdracht is geslaagd, zoals wordt weer gegeven in de uitvoer:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-187">This command succeeds, as shown in the output:</span></span>

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += @{mode = "write"}
$a
```

```
Name                           Value
----                           -----
a                              1
b                              2
mode                           write
c                              3
```

<span data-ttu-id="ea1ab-188">Met de volgende opdracht wordt geprobeerd een geheel getal ' 1 ' toe te voegen aan de hash-tabel in de `$a` variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-188">The following command attempts to append an integer "1" to the hash table in the `$a` variable.</span></span> <span data-ttu-id="ea1ab-189">Deze opdracht mislukt:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-189">This command fails:</span></span>

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += 1
```

```
You can add another hash table only to a hash table.
At line:1 char:6
+ $a += <<<<  1
```

### <a name="the-assignment-by-subtraction-operator"></a><span data-ttu-id="ea1ab-190">De operator Assignment door aftrekken</span><span class="sxs-lookup"><span data-stu-id="ea1ab-190">The assignment by subtraction operator</span></span>

<span data-ttu-id="ea1ab-191">De operator Assignment door aftrekken `-=` verlaagt de waarde van een variabele met de waarde die aan de rechter kant van de operator is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-191">The assignment by subtraction operator `-=` decrements the value of a variable by the value that is specified on the right side of the operator.</span></span> <span data-ttu-id="ea1ab-192">Deze operator kan niet worden gebruikt met teken reeks variabelen en kan niet worden gebruikt om een element uit een verzameling te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-192">This operator cannot be used with string variables, and it cannot be used to remove an element from a collection.</span></span>

<span data-ttu-id="ea1ab-193">De `-=` operator combineert twee bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-193">The `-=` operator combines two operations.</span></span> <span data-ttu-id="ea1ab-194">Eerst wordt de waarde afgetrokken en vervolgens toegewezen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-194">First, it subtracts, and then it assigns.</span></span> <span data-ttu-id="ea1ab-195">Daarom zijn de volgende instructies gelijkwaardig:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-195">Therefore, the following statements are equivalent:</span></span>

```powershell
$a -= 2
$a = ($a - 2)
```

<span data-ttu-id="ea1ab-196">In het volgende voor beeld ziet u hoe u de operator kunt gebruiken `-=` om de waarde van een variabele te verlagen:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-196">The following example shows how to use of the `-=` operator to decrease the value of a variable:</span></span>

```powershell
$a = 8
$a -= 2
$a
```

```
6
```

<span data-ttu-id="ea1ab-197">U kunt ook de `-=` toewijzings operator gebruiken om de waarde van een lid van een numerieke matrix te verlagen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-197">You can also use the `-=` assignment operator to decrease the value of a member of a numeric array.</span></span> <span data-ttu-id="ea1ab-198">U doet dit door de index op te geven van het matrix element dat u wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-198">To do this, specify the index of the array element that you want to change.</span></span> <span data-ttu-id="ea1ab-199">In het volgende voor beeld wordt de waarde van het derde element van een matrix (element 2) verlaagd met 1:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-199">In the following example, the value of the third element of an array (element 2) is decreased by 1:</span></span>

```powershell
$a = 1,2,3
$a[2] -= 1
$a
```

```
1
2
2
```

<span data-ttu-id="ea1ab-200">U kunt de operator niet gebruiken `-=` om de waarden van een variabele te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-200">You cannot use the `-=` operator to delete the values of a variable.</span></span> <span data-ttu-id="ea1ab-201">Als u alle waarden wilt verwijderen die aan een variabele zijn toegewezen, gebruikt u de cmdlets [Clear-item](xref:Microsoft.PowerShell.Management.Clear-Item) of [Clear-variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) om een waarde van `$null` of `""` toe te wijzen aan de variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-201">To delete all the values that are assigned to a variable, use the [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item) or [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) cmdlets to assign a value of `$null` or `""` to the variable.</span></span>

```powershell
$a = $null
```

<span data-ttu-id="ea1ab-202">Als u een bepaalde waarde uit een matrix wilt verwijderen, gebruikt u matrix notatie om een waarde `$null` toe te wijzen aan een bepaald item.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-202">To delete a particular value from an array, use array notation to assign a value of `$null` to the particular item.</span></span> <span data-ttu-id="ea1ab-203">Met de volgende instructie wordt bijvoorbeeld de tweede waarde (index positie 1) uit een matrix verwijderd:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-203">For example, the following statement deletes the second value (index position 1) from an array:</span></span>

```powershell
$a = 1,2,3
$a
```

```
1
2
3
```

```powershell
$a[1] = $null
$a
```

```
1
3
```

<span data-ttu-id="ea1ab-204">Als u een variabele wilt verwijderen, gebruikt u de cmdlet [Remove-variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) .</span><span class="sxs-lookup"><span data-stu-id="ea1ab-204">To delete a variable, use the [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) cmdlet.</span></span> <span data-ttu-id="ea1ab-205">Deze methode is handig wanneer de variabele expliciet wordt geconverteerd naar een bepaald gegevens type en u een variabele zonder type wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-205">This method is useful when the variable is explicitly cast to a particular data type, and you want an untyped variable.</span></span> <span data-ttu-id="ea1ab-206">Met de volgende opdracht wordt de `$a` variabele verwijderd:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-206">The following command deletes the `$a` variable:</span></span>

```powershell
Remove-Variable -Name a
```

### <a name="the-assignment-by-multiplication-operator"></a><span data-ttu-id="ea1ab-207">De operator Assignment door vermenigvuldigen</span><span class="sxs-lookup"><span data-stu-id="ea1ab-207">The assignment by multiplication operator</span></span>

<span data-ttu-id="ea1ab-208">De operator Assignment door vermenigvuldigen `*=` vermenigvuldigt een numerieke waarde of voegt het opgegeven aantal kopieën van de teken reeks waarde van een variabele toe.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-208">The assignment by multiplication operator `*=` multiplies a numeric value or appends the specified number of copies of the string value of a variable.</span></span>

<span data-ttu-id="ea1ab-209">Wanneer een variabele één numerieke waarde bevat, wordt die waarde vermenigvuldigd met de waarde aan de rechter kant van de operator.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-209">When a variable contains a single numeric value, that value is multiplied by the value on the right side of the operator.</span></span> <span data-ttu-id="ea1ab-210">In het volgende voor beeld ziet u bijvoorbeeld hoe u de `*=` operator kunt gebruiken om de waarde van een variabele te vermenigvuldigen:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-210">For example, the following example shows how to use the `*=` operator to multiply the value of a variable:</span></span>

```powershell
$a = 3
$a *= 4
$a
```

```
12
```

<span data-ttu-id="ea1ab-211">In dit geval combineert de `*=` operator twee bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-211">In this case, the `*=` operator combines two operations.</span></span> <span data-ttu-id="ea1ab-212">Eerst wordt de waarde vermenigvuldigd en vervolgens toegewezen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-212">First, it multiplies, and then it assigns.</span></span> <span data-ttu-id="ea1ab-213">Daarom zijn de volgende instructies gelijkwaardig:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-213">Therefore, the following statements are equivalent:</span></span>

```powershell
$a *= 2
$a = ($a * 2)
```

<span data-ttu-id="ea1ab-214">Wanneer een variabele een teken reeks waarde bevat, voegt Power shell het opgegeven aantal teken reeksen toe aan de waarde, als volgt:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-214">When a variable contains a string value, PowerShell appends the specified number of strings to the value, as follows:</span></span>

```powershell
$a = "file"
$a *= 4
$a
```

```
filefilefilefile
```

<span data-ttu-id="ea1ab-215">Als u een element van een matrix wilt vermenigvuldigen, gebruikt u een index om het element te identificeren dat u wilt vermenigvuldigen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-215">To multiply an element of an array, use an index to identify the element that you want to multiply.</span></span> <span data-ttu-id="ea1ab-216">De volgende opdracht vermenigvuldigt bijvoorbeeld het eerste element in de matrix (index positie 0) door 2:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-216">For example, the following command multiplies the first element in the array (index position 0) by 2:</span></span>

```powershell
$a[0] *= 2
```

### <a name="the-assignment-by-division-operator"></a><span data-ttu-id="ea1ab-217">De operator Assignment per divisie</span><span class="sxs-lookup"><span data-stu-id="ea1ab-217">The assignment by division operator</span></span>

<span data-ttu-id="ea1ab-218">De operator Assignment per divisie `/=` deelt een numerieke waarde door de waarde die aan de rechter kant van de operator is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-218">The assignment by division operator `/=` divides a numeric value by the value that is specified on the right side of the operator.</span></span> <span data-ttu-id="ea1ab-219">De operator kan niet worden gebruikt met teken reeks variabelen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-219">The operator cannot be used with string variables.</span></span>

<span data-ttu-id="ea1ab-220">De `/=` operator combineert twee bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-220">The `/=` operator combines two operations.</span></span> <span data-ttu-id="ea1ab-221">Eerst wordt de waarde gedeeld en vervolgens toegewezen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-221">First, it divides, and then it assigns.</span></span> <span data-ttu-id="ea1ab-222">Daarom zijn de volgende twee instructies gelijkwaardig:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-222">Therefore, the following two statements are equivalent:</span></span>

```powershell
$a /= 2
$a = ($a / 2)
```

<span data-ttu-id="ea1ab-223">Met de volgende opdracht wordt bijvoorbeeld de `/=` operator gebruikt om de waarde van een variabele te verdelen:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-223">For example, the following command uses the `/=` operator to divide the value of a variable:</span></span>

```powershell
$a = 8
$a /=2
$a
```

```
4
```

<span data-ttu-id="ea1ab-224">Als u een element van een matrix wilt delen, gebruikt u een index om het element te identificeren dat u wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-224">To divide an element of an array, use an index to identify the element that you want to change.</span></span> <span data-ttu-id="ea1ab-225">De volgende opdracht deelt bijvoorbeeld het tweede element in de matrix (index positie 1) door 2:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-225">For example, the following command divides the second element in the array (index position 1) by 2:</span></span>

```powershell
$a[1] /= 2
```

### <a name="the-assignment-by-modulus-operator"></a><span data-ttu-id="ea1ab-226">De operator Assignment door modulus</span><span class="sxs-lookup"><span data-stu-id="ea1ab-226">The assignment by modulus operator</span></span>

<span data-ttu-id="ea1ab-227">De operator Assignment door modulus `%=` verdeelt de waarde van een variabele met de waarde aan de rechter kant van de operator.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-227">The assignment by modulus operator `%=` divides the value of a variable by the value on the right side of the operator.</span></span> <span data-ttu-id="ea1ab-228">Vervolgens wijst de `%=` operator de rest (ook wel de modulus) toe aan de variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-228">Then, the `%=` operator assigns the remainder (known as the modulus) to the variable.</span></span> <span data-ttu-id="ea1ab-229">U kunt deze operator alleen gebruiken wanneer een variabele een enkele numerieke waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-229">You can use this operator only when a variable contains a single numeric value.</span></span> <span data-ttu-id="ea1ab-230">U kunt deze operator niet gebruiken wanneer een variabele een teken reeks variabele of een matrix bevat.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-230">You cannot use this operator when a variable contains a string variable or an array.</span></span>

<span data-ttu-id="ea1ab-231">De `%=` operator combineert twee bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-231">The `%=` operator combines two operations.</span></span> <span data-ttu-id="ea1ab-232">Eerst wordt het restant gesplitst en bepaald en vervolgens wordt de rest aan de variabele toegewezen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-232">First, it divides and determines the remainder, and then it assigns the remainder to the variable.</span></span> <span data-ttu-id="ea1ab-233">Daarom zijn de volgende instructies gelijkwaardig:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-233">Therefore, the following statements are equivalent:</span></span>

```powershell
$a %= 2
$a = ($a % 2)
```

<span data-ttu-id="ea1ab-234">In het volgende voor beeld ziet u hoe u de operator kunt gebruiken `%=` om de modulus van een quotiënt op te slaan:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-234">The following example shows how to use the `%=` operator to save the modulus of a quotient:</span></span>

```powershell
$a = 7
$a %= 4
$a
```

```
3
```

## <a name="the-increment-and-decrement-operators"></a><span data-ttu-id="ea1ab-235">De Opera tors voor verhogen en verlagen</span><span class="sxs-lookup"><span data-stu-id="ea1ab-235">The increment and decrement operators</span></span>

<span data-ttu-id="ea1ab-236">De operator voor oplopen `++` verhoogt de waarde van een variabele met 1.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-236">The increment operator `++` increases the value of a variable by 1.</span></span> <span data-ttu-id="ea1ab-237">Wanneer u de operator voor verhogen in een eenvoudige instructie gebruikt, wordt er geen waarde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-237">When you use the increment operator in a simple statement, no value is returned.</span></span> <span data-ttu-id="ea1ab-238">Als u het resultaat wilt weer geven, geeft u de waarde van de variabele als volgt weer:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-238">To view the result, display the value of the variable, as follows:</span></span>

```powershell
$a = 7
++$a
$a
```

```
8
```

<span data-ttu-id="ea1ab-239">Als u wilt afdwingen dat een waarde wordt geretourneerd, plaatst u de variabele en de operator tussen haakjes, als volgt:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-239">To force a value to be returned, enclose the variable and the operator in parentheses, as follows:</span></span>

```powershell
$a = 7
(++$a)
```

```
8
```

<span data-ttu-id="ea1ab-240">De operator voor oplopen kan vóór (voor voegsel) of na (achtervoegsel) een variabele worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-240">The increment operator can be placed before (prefix) or after (postfix) a variable.</span></span> <span data-ttu-id="ea1ab-241">De voorvoegsel versie van de operator verhoogt een variabele voordat de waarde ervan in de instructie wordt gebruikt, als volgt:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-241">The prefix version of the operator increments a variable before its value is used in the statement, as follows:</span></span>

```powershell
$a = 7
$c = ++$a
$a
```

```
8
```

```powershell
$c
```

```
8
```

<span data-ttu-id="ea1ab-242">De achtervoegsel-versie van de operator verhoogt een variabele nadat de waarde ervan wordt gebruikt in de instructie.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-242">The postfix version of the operator increments a variable after its value is used in the statement.</span></span> <span data-ttu-id="ea1ab-243">In het volgende voor beeld `$c` hebben de `$a` variabelen en verschillende waarden, omdat de waarde wordt toegewezen aan `$c` vóór `$a` wijzigingen:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-243">In the following example, the `$c` and `$a` variables have different values because the value is assigned to `$c` before `$a` changes:</span></span>

```powershell
$a = 7
$c = $a++
$a
```

```
8
```

```powershell
$c
```

```
7
```

<span data-ttu-id="ea1ab-244">De operator `--` voor verlagen vermindert de waarde van een variabele met 1.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-244">The decrement operator `--` decreases the value of a variable by 1.</span></span> <span data-ttu-id="ea1ab-245">Net als bij de operator voor verhogen, wordt er geen waarde geretourneerd wanneer u de operator in een eenvoudige instructie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-245">As with the increment operator, no value is returned when you use the operator in a simple statement.</span></span> <span data-ttu-id="ea1ab-246">Gebruik haakjes om een waarde te retour neren, als volgt:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-246">Use parentheses to return a value, as follows:</span></span>

```powershell
$a = 7
--$a
$a
```

```
6
```

```powershell
(--$a)
```

```
5
```

<span data-ttu-id="ea1ab-247">De voorvoegsel versie van de operator vermindert een variabele voordat de waarde ervan in de instructie wordt gebruikt, als volgt:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-247">The prefix version of the operator decrements a variable before its value is used in the statement, as follows:</span></span>

```powershell
$a = 7
$c = --$a
$a
```

```
6
```

```powershell
$c
```

```
6
```

<span data-ttu-id="ea1ab-248">De achtervoegsel-versie van de operator verlaagt een variabele nadat de waarde ervan is gebruikt in de instructie.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-248">The postfix version of the operator decrements a variable after its value is used in the statement.</span></span> <span data-ttu-id="ea1ab-249">In het volgende voor beeld `$d` hebben de `$a` variabelen en verschillende waarden, omdat de waarde wordt toegewezen aan `$d` vóór `$a` wijzigingen:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-249">In the following example, the `$d` and `$a` variables have different values because the value is assigned to `$d` before `$a` changes:</span></span>

```powershell
$a = 7
$d = $a--
$a
```

```
6
```

```powershell
$d
```

```
7
```

## <a name="microsoft-net-framework-types"></a><span data-ttu-id="ea1ab-250">Microsoft .NET Framework-typen</span><span class="sxs-lookup"><span data-stu-id="ea1ab-250">Microsoft .NET Framework types</span></span>

<span data-ttu-id="ea1ab-251">Wanneer een variabele slechts één waarde heeft, bepaalt de waarde die is toegewezen aan de variabele standaard het gegevens type van de variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-251">By default, when a variable has only one value, the value that is assigned to the variable determines the data type of the variable.</span></span> <span data-ttu-id="ea1ab-252">Met de volgende opdracht maakt u bijvoorbeeld een variabele met het type geheel getal (System. Int32):</span><span class="sxs-lookup"><span data-stu-id="ea1ab-252">For example, the following command creates a variable that has the "Integer" (System.Int32) type:</span></span>

```powershell
$a = 6
```

<span data-ttu-id="ea1ab-253">Als u wilt zoeken naar het .NET Framework type van een variabele, gebruikt u de methode **gettype** en de eigenschap **FullName** als volgt.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-253">To find the .NET Framework type of a variable, use the **GetType** method and its **FullName** property, as follows.</span></span> <span data-ttu-id="ea1ab-254">Zorg ervoor dat u de haakjes achter de **gettype** -methode naam opgeeft, zelfs als de aanroep van de methode geen argumenten heeft:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-254">Be sure to include the parentheses after the **GetType** method name, even though the method call has no arguments:</span></span>

```powershell
$a = 6
$a.GetType().FullName
```

```
System.Int32
```

<span data-ttu-id="ea1ab-255">Als u een variabele wilt maken die een teken reeks bevat, wijst u een teken reeks waarde toe aan de variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-255">To create a variable that contains a string, assign a string value to the variable.</span></span> <span data-ttu-id="ea1ab-256">Om aan te geven dat de waarde een teken reeks is, plaatst u deze tussen aanhalings tekens als volgt:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-256">To indicate that the value is a string, enclose it in quotation marks, as follows:</span></span>

```powershell
$a = "6"
$a.GetType().FullName
```

```
System.String
```

<span data-ttu-id="ea1ab-257">Als de eerste waarde die is toegewezen aan de variabele een teken reeks is, behandelt Power shell alle bewerkingen als teken reeks bewerkingen en worden nieuwe waarden naar teken reeksen gecast.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-257">If the first value that is assigned to the variable is a string, PowerShell treats all operations as string operations and casts new values to strings.</span></span>
<span data-ttu-id="ea1ab-258">Dit doet zich voor in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-258">This occurs in the following example:</span></span>

```powershell
$a = "file"
$a += 3
$a
```

```
file3
```

<span data-ttu-id="ea1ab-259">Als de eerste waarde een geheel getal is, behandelt Power shell alle bewerkingen als gehele getallen en worden nieuwe waarden gecast naar gehele getallen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-259">If the first value is an integer, PowerShell treats all operations as integer operations and casts new values to integers.</span></span> <span data-ttu-id="ea1ab-260">Dit doet zich voor in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-260">This occurs in the following example:</span></span>

```powershell
$a = 6
$a += "3"
$a
```

```
9
```

<span data-ttu-id="ea1ab-261">U kunt een nieuwe scalaire variabele als .NET Framework type casten door de type naam tussen vier Kante haken te plaatsen die voorafgaat aan de naam van de variabele of de eerste toewijzings waarde.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-261">You can cast a new scalar variable as any .NET Framework type by placing the type name in brackets that precede either the variable name or the first assignment value.</span></span> <span data-ttu-id="ea1ab-262">Wanneer u een variabele casteert, kunt u bepalen welke typen gegevens in de variabele kunnen worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-262">When you cast a variable, you can determine the types of data that can be stored in the variable.</span></span> <span data-ttu-id="ea1ab-263">En u kunt bepalen hoe de variabele zich gedraagt wanneer u deze bewerkt.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-263">And, you can determine how the variable behaves when you manipulate it.</span></span>

<span data-ttu-id="ea1ab-264">Met de volgende opdracht wordt de variabele bijvoorbeeld gecast als een teken reeks type:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-264">For example, the following command casts the variable as a string type:</span></span>

```powershell
[string]$a = 27
$a += 3
$a
```

```
273
```

<span data-ttu-id="ea1ab-265">In het volgende voor beeld wordt de eerste waarde geconverteerd, in plaats van de variabele te casten:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-265">The following example casts the first value, instead of casting the variable:</span></span>

```powershell
$a = [string]27
```

<span data-ttu-id="ea1ab-266">Wanneer u een variabele naar een specifiek type casteert, is de gemeen schappelijke Conventie om de variabele te casten, niet de waarde.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-266">When you cast a variable to a specific type, the common convention is to cast the variable, not the value.</span></span> <span data-ttu-id="ea1ab-267">U kunt het gegevens type van een bestaande variabele echter niet opnieuw converteren als de waarde ervan niet kan worden geconverteerd naar het nieuwe gegevens type.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-267">However, you cannot recast the data type of an existing variable if its value cannot be converted to the new data type.</span></span> <span data-ttu-id="ea1ab-268">Als u het gegevens type wilt wijzigen, moet u de waarde als volgt vervangen:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-268">To change the data type, you must replace its value, as follows:</span></span>

```powershell
$a = "string"
[int]$a
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input string was
not in a correct format." At line:1 char:8 + [int]$a <<<<
```

```powershell
[int]$a = 3
```

<span data-ttu-id="ea1ab-269">Wanneer u de naam van een variabele voorafgaat aan een gegevens type, wordt het type van die variabele bovendien vergrendeld, tenzij u het type expliciet overschrijft door een ander gegevens type op te geven.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-269">In addition, when you precede a variable name with a data type, the type of that variable is locked unless you explicitly override the type by specifying another data type.</span></span> <span data-ttu-id="ea1ab-270">Als u probeert een waarde toe te wijzen die niet compatibel is met het bestaande type en u het type niet expliciet overschrijft, wordt een fout weer gegeven, zoals in het volgende voor beeld wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-270">If you try to assign a value that is incompatible with the existing type, and you do not explicitly override the type, PowerShell displays an error, as shown in the following example:</span></span>

```powershell
$a = 3
$a = "string"
[int]$a = 3
$a = "string"
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input
string was not in a correct format."
At line:1 char:3
+ $a <<<<  = "string"
```

```powershell
[string]$a = "string"
```

<span data-ttu-id="ea1ab-271">In Power shell worden de gegevens typen van variabelen die meerdere items in een matrix bevatten, anders afgehandeld dan de gegevens typen van variabelen die één item bevatten.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-271">In PowerShell, the data types of variables that contain multiple items in an array are handled differently from the data types of variables that contain a single item.</span></span> <span data-ttu-id="ea1ab-272">Tenzij een gegevens type specifiek wordt toegewezen aan een matrix variabele, is het gegevens type altijd `System.Object []` .</span><span class="sxs-lookup"><span data-stu-id="ea1ab-272">Unless a data type is specifically assigned to an array variable, the data type is always `System.Object []`.</span></span> <span data-ttu-id="ea1ab-273">Dit gegevens type is specifiek voor matrices.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-273">This data type is specific to arrays.</span></span>

<span data-ttu-id="ea1ab-274">Soms kunt u het standaard type overschrijven door een ander type op te geven.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-274">Sometimes, you can override the default type by specifying another type.</span></span> <span data-ttu-id="ea1ab-275">Met de volgende opdracht wordt de variabele bijvoorbeeld gecast als een `string []` matrix type:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-275">For example, the following command casts the variable as a `string []` array type:</span></span>

```powershell
[string []] $a = "one", "two", "three"
```

<span data-ttu-id="ea1ab-276">Power shell-variabelen kunnen elk .NET Framework gegevens type zijn.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-276">PowerShell variables can be any .NET Framework data type.</span></span> <span data-ttu-id="ea1ab-277">Daarnaast kunt u een volledig gekwalificeerd .NET Framework gegevens type toewijzen dat in het huidige proces beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-277">In addition, you can assign any fully qualified .NET Framework data type that is available in the current process.</span></span> <span data-ttu-id="ea1ab-278">Met de volgende opdracht wordt bijvoorbeeld een `System.DateTime` gegevens type opgegeven:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-278">For example, the following command specifies a `System.DateTime` data type:</span></span>

```powershell
[System.DateTime]$a = "5/31/2005"
```

<span data-ttu-id="ea1ab-279">Aan de variabele wordt een waarde toegewezen die voldoet aan het `System.DateTime` gegevens type.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-279">The variable will be assigned a value that conforms to the `System.DateTime` data type.</span></span> <span data-ttu-id="ea1ab-280">De waarde van de `$a` variabele zou het volgende zijn:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-280">The value of the `$a` variable would be the following:</span></span>

```
Tuesday, May 31, 2005 12:00:00 AM
```

## <a name="assigning-multiple-variables"></a><span data-ttu-id="ea1ab-281">Meerdere variabelen toewijzen</span><span class="sxs-lookup"><span data-stu-id="ea1ab-281">Assigning multiple variables</span></span>

<span data-ttu-id="ea1ab-282">In Power shell kunt u waarden toewijzen aan meerdere variabelen met behulp van één opdracht.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-282">In PowerShell, you can assign values to multiple variables by using a single command.</span></span> <span data-ttu-id="ea1ab-283">Het eerste element van de toewijzings waarde wordt toegewezen aan de eerste variabele, het tweede element wordt toegewezen aan de tweede variabele, het derde element aan de derde variabele, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-283">The first element of the assignment value is assigned to the first variable, the second element is assigned to the second variable, the third element to the third variable, and so on.</span></span> <span data-ttu-id="ea1ab-284">Met de volgende opdracht wordt bijvoorbeeld de waarde 1 toegewezen aan de `$a` variabele, de waarde 2 aan de `$b` variabele en de waarde 3 aan de `$c` variabele:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-284">For example, the following command assigns the value 1 to the `$a` variable, the value 2 to the `$b` variable, and the value 3 to the `$c` variable:</span></span>

```powershell
$a, $b, $c = 1, 2, 3
```

<span data-ttu-id="ea1ab-285">Als de toewijzings waarde meer elementen dan variabelen bevat, worden alle resterende waarden toegewezen aan de laatste variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-285">If the assignment value contains more elements than variables, all the remaining values are assigned to the last variable.</span></span> <span data-ttu-id="ea1ab-286">De volgende opdracht bevat bijvoorbeeld drie variabelen en vijf waarden:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-286">For example, the following command contains three variables and five values:</span></span>

```powershell
$a, $b, $c = 1, 2, 3, 4, 5
```

<span data-ttu-id="ea1ab-287">Daarom wijst Power shell de waarde 1 toe aan de `$a` variabele en de waarde 2 aan de `$b` variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-287">Therefore, PowerShell assigns the value 1 to the `$a` variable and the value 2 to the `$b` variable.</span></span> <span data-ttu-id="ea1ab-288">De waarden 3, 4 en 5 worden toegewezen aan de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-288">It assigns the values 3, 4, and 5 to the `$c` variable.</span></span>
<span data-ttu-id="ea1ab-289">Als u de waarden in de `$c` variabele aan drie andere variabelen wilt toewijzen, gebruikt u de volgende notatie:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-289">To assign the values in the `$c` variable to three other variables, use the following format:</span></span>

```powershell
$d, $e, $f = $c
```

<span data-ttu-id="ea1ab-290">Met deze opdracht wordt de waarde 3 toegewezen aan de `$d` variabele, de waarde 4 voor de `$e` variabele en de waarde 5 voor de `$f` variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-290">This command assigns the value 3 to the `$d` variable, the value 4 to the `$e` variable, and the value 5 to the `$f` variable.</span></span>

<span data-ttu-id="ea1ab-291">Als de toewijzings waarde minder elementen dan variabelen bevat, worden aan alle resterende variabelen aan het einde geen waarden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-291">If the assignment value contains less elements than variables, all the remaining variables at the end are not assigned any values.</span></span> <span data-ttu-id="ea1ab-292">De volgende opdracht bevat bijvoorbeeld drie variabelen en twee waarden:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-292">For example, the following command contains three variables and two values:</span></span>

```powershell
$a, $b, $c = 1, 2
```

<span data-ttu-id="ea1ab-293">Daarom wijst Power shell de waarde 1 toe aan de `$a` variabele en de waarde 2 aan de `$b` variabele.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-293">Therefore, PowerShell assigns the value 1 to the `$a` variable and the value 2 to the `$b` variable.</span></span> <span data-ttu-id="ea1ab-294">Er wordt geen waarde aan de variabele toegewezen `$c` .</span><span class="sxs-lookup"><span data-stu-id="ea1ab-294">It will not assign any value to the `$c` variable.</span></span>

<span data-ttu-id="ea1ab-295">U kunt ook een enkele waarde aan meerdere variabelen toewijzen door de variabelen te koppelen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-295">You can also assign a single value to multiple variables by chaining the variables.</span></span> <span data-ttu-id="ea1ab-296">Met de volgende opdracht wordt bijvoorbeeld de waarde ' drie ' toegewezen aan alle vier de variabelen:</span><span class="sxs-lookup"><span data-stu-id="ea1ab-296">For example, the following command assigns a value of "three" to all four variables:</span></span>

```powershell
$a = $b = $c = $d = "three"
```

## <a name="variable-related-cmdlets"></a><span data-ttu-id="ea1ab-297">Met variabele gerelateerde cmdlets</span><span class="sxs-lookup"><span data-stu-id="ea1ab-297">Variable-related cmdlets</span></span>

<span data-ttu-id="ea1ab-298">Naast het gebruik van een toewijzings bewerking om een variabele waarde in te stellen, kunt u ook de cmdlet [set-variable](xref:Microsoft.PowerShell.Utility.Set-Variable) gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-298">In addition to using an assignment operation to set a variable value, you can also use the [Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable) cmdlet.</span></span> <span data-ttu-id="ea1ab-299">Met de volgende opdracht wordt bijvoorbeeld `Set-Variable` een matrix van 1, 2, 3 aan de `$a` variabele toegewezen.</span><span class="sxs-lookup"><span data-stu-id="ea1ab-299">For example, the following command uses `Set-Variable` to assign an array of 1, 2, 3 to the `$a` variable.</span></span>

```powershell
Set-Variable -Name a -Value 1, 2, 3
```

## <a name="see-also"></a><span data-ttu-id="ea1ab-300">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ea1ab-300">See also</span></span>

[<span data-ttu-id="ea1ab-301">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="ea1ab-301">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="ea1ab-302">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="ea1ab-302">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="ea1ab-303">about_Variables</span><span class="sxs-lookup"><span data-stu-id="ea1ab-303">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="ea1ab-304">Clear-variabele</span><span class="sxs-lookup"><span data-stu-id="ea1ab-304">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

[<span data-ttu-id="ea1ab-305">Remove-variabele</span><span class="sxs-lookup"><span data-stu-id="ea1ab-305">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)

[<span data-ttu-id="ea1ab-306">Set-variabele</span><span class="sxs-lookup"><span data-stu-id="ea1ab-306">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)

