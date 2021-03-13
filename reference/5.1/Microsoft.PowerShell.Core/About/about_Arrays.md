---
description: Hierin worden matrices beschreven. Dit zijn gegevens structuren die zijn ontworpen om verzamelingen van items op te slaan.
Locale: en-US
ms.date: 08/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arrays
ms.openlocfilehash: d50bcaca53939c3fee2ee9f1e179c139e1145810
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412898"
---
# <a name="about-arrays"></a><span data-ttu-id="1ecc6-103">Over matrices</span><span class="sxs-lookup"><span data-stu-id="1ecc6-103">About Arrays</span></span>

## <a name="short-description"></a><span data-ttu-id="1ecc6-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="1ecc6-104">Short Description</span></span>
<span data-ttu-id="1ecc6-105">Hierin worden matrices beschreven. Dit zijn gegevens structuren die zijn ontworpen om verzamelingen van items op te slaan.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-105">Describes arrays, which are data structures designed to store collections of items.</span></span>

## <a name="long-description"></a><span data-ttu-id="1ecc6-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="1ecc6-106">Long Description</span></span>

<span data-ttu-id="1ecc6-107">Een matrix is een gegevens structuur die is ontworpen voor het opslaan van een verzameling items.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-107">An array is a data structure that is designed to store a collection of items.</span></span>
<span data-ttu-id="1ecc6-108">De items kunnen van hetzelfde type of van verschillende typen zijn.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-108">The items can be the same type or different types.</span></span>

<span data-ttu-id="1ecc6-109">Vanaf Windows Power Shell 3,0 heeft een verzameling van nul of één object enkele eigenschappen van matrices.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-109">Beginning in Windows PowerShell 3.0, a collection of zero or one object has some properties of arrays.</span></span>

## <a name="creating-and-initializing-an-array"></a><span data-ttu-id="1ecc6-110">Een matrix maken en initialiseren</span><span class="sxs-lookup"><span data-stu-id="1ecc6-110">Creating and initializing an array</span></span>

<span data-ttu-id="1ecc6-111">Als u een matrix wilt maken en initialiseren, moet u meerdere waarden toewijzen aan een variabele.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-111">To create and initialize an array, assign multiple values to a variable.</span></span> <span data-ttu-id="1ecc6-112">De waarden die zijn opgeslagen in de matrix, worden gescheiden door een komma en gescheiden door de toewijzings operator () van de naam van de variabele `=` .</span><span class="sxs-lookup"><span data-stu-id="1ecc6-112">The values stored in the array are delimited with a comma and separated from the variable name by the assignment operator (`=`).</span></span>

<span data-ttu-id="1ecc6-113">Als u bijvoorbeeld een matrix wilt maken `$A` met de naam die de zeven numerieke waarden (int) van 22, 5, 10, 8, 12, 9 en 80 bevat, typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-113">For example, to create an array named `$A` that contains the seven numeric (int) values of 22, 5, 10, 8, 12, 9, and 80, type:</span></span>

```powershell
$A = 22,5,10,8,12,9,80
```

<span data-ttu-id="1ecc6-114">De komma kan ook worden gebruikt voor het initialiseren van een enkele item matrix door de komma vóór het afzonderlijke item te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-114">The comma can also be used to initialize a single item array by placing the comma before the single item.</span></span>

<span data-ttu-id="1ecc6-115">Als u bijvoorbeeld een enkele item matrix wilt maken met `$B` de naam met de waarde 7, typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-115">For example, to create a single item array named `$B` containing the single value of 7, type:</span></span>

```powershell
$B = ,7
```

<span data-ttu-id="1ecc6-116">U kunt ook een matrix maken en initialiseren met behulp van de operator Range ( `..` ).</span><span class="sxs-lookup"><span data-stu-id="1ecc6-116">You can also create and initialize an array by using the range operator (`..`).</span></span>
<span data-ttu-id="1ecc6-117">In het volgende voor beeld wordt een matrix gemaakt met de waarden 5 tot en met 8.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-117">The following example creates an array containing the values 5 through 8.</span></span>

```powershell
$C = 5..8
```

<span data-ttu-id="1ecc6-118">Als gevolg hiervan `$C` bevat vier waarden: 5, 6, 7 en 8.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-118">As a result, `$C` contains four values: 5, 6, 7, and 8.</span></span>

<span data-ttu-id="1ecc6-119">Als er geen gegevens type is opgegeven, maakt Power shell elke matrix als een object Matrix (**System. object []**).</span><span class="sxs-lookup"><span data-stu-id="1ecc6-119">When no data type is specified, PowerShell creates each array as an object array (**System.Object[]**).</span></span> <span data-ttu-id="1ecc6-120">Gebruik de methode **gettype ()** om het gegevens type van een matrix te bepalen.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-120">To determine the data type of an array, use the **GetType()** method.</span></span> <span data-ttu-id="1ecc6-121">Als u bijvoorbeeld het gegevens type van de matrix wilt bepalen `$A` , typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-121">For example, to determine the data type of the `$A` array, type:</span></span>

```powershell
$A.GetType()
```

<span data-ttu-id="1ecc6-122">Als u een sterk getypeerde matrix wilt maken, dat wil zeggen een matrix die alleen waarden van een bepaald type kan bevatten, kunt u de variabele als een matrix type casten, zoals **String []**, **Long []** of **Int32 []**.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-122">To create a strongly typed array, that is, an array that can contain only values of a particular type, cast the variable as an array type, such as **string[]**, **long[]**, or **int32[]**.</span></span> <span data-ttu-id="1ecc6-123">Als u een matrix wilt casten, moet u vóór de naam van de variabele een matrix type opgeven tussen vier Kante haken.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-123">To cast an array, precede the variable name with an array type enclosed in brackets.</span></span> <span data-ttu-id="1ecc6-124">Als u bijvoorbeeld een matrix van 32-bits geheel getal met de naam `$ia` vier gehele getallen (1500, 2230, 3350 en 4000) wilt maken, typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-124">For example, to create a 32-bit integer array named `$ia` containing four integers (1500, 2230, 3350, and 4000), type:</span></span>

```powershell
[int32[]]$ia = 1500,2230,3350,4000
```

<span data-ttu-id="1ecc6-125">Als gevolg hiervan kan de `$ia` matrix alleen gehele getallen bevatten.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-125">As a result, the `$ia` array can contain only integers.</span></span>

<span data-ttu-id="1ecc6-126">U kunt matrices maken die worden geconverteerd naar een ondersteund type in het Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-126">You can create arrays that are cast to any supported type in the Microsoft .NET Framework.</span></span> <span data-ttu-id="1ecc6-127">De objecten die `Get-Process` worden opgehaald om processen te vertegenwoordigen, zijn bijvoorbeeld van het type **System. Diagnostics. process** .</span><span class="sxs-lookup"><span data-stu-id="1ecc6-127">For example, the objects that `Get-Process` retrieves to represent processes are of the **System.Diagnostics.Process** type.</span></span> <span data-ttu-id="1ecc6-128">Als u een sterk getypeerde matrix met proces objecten wilt maken, voert u de volgende opdracht in:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-128">To create a strongly typed array of process objects, enter the following command:</span></span>

```powershell
[Diagnostics.Process[]]$zz = Get-Process
```

## <a name="the-array-sub-expression-operator"></a><span data-ttu-id="1ecc6-129">De subexpression-operator van de matrix</span><span class="sxs-lookup"><span data-stu-id="1ecc6-129">The array sub-expression operator</span></span>

<span data-ttu-id="1ecc6-130">De operator subexpression van matrix maakt een matrix van de instructies hierin.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-130">The array sub-expression operator creates an array from the statements inside it.</span></span> <span data-ttu-id="1ecc6-131">Ongeacht het resultaat van de instructie in de operator, plaatst de operator deze in een matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-131">Whatever the statement inside the operator produces, the operator will place it in an array.</span></span> <span data-ttu-id="1ecc6-132">Zelfs als er geen of een object is.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-132">Even if there is zero or one object.</span></span>

<span data-ttu-id="1ecc6-133">De syntaxis van de matrix operator is als volgt:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-133">The syntax of the array operator is as follows:</span></span>

```syntax
@( ... )
```

<span data-ttu-id="1ecc6-134">U kunt de operator matrix gebruiken om een matrix van nul of één object te maken.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-134">You can use the array operator to create an array of zero or one object.</span></span> <span data-ttu-id="1ecc6-135">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-135">For example:</span></span>

```powershell
$a = @("Hello World")
$a.Count
```

```Output
1
```

```powershell
$b = @()
$b.Count
```

```Output
0
```

<span data-ttu-id="1ecc6-136">De matrix operator is handig in scripts wanneer u objecten ophaalt, maar niet weet hoeveel objecten u krijgt.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-136">The array operator is useful in scripts when you are getting objects, but do not know how many objects you get.</span></span> <span data-ttu-id="1ecc6-137">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-137">For example:</span></span>

```powershell
$p = @(Get-Process Notepad)
```

<span data-ttu-id="1ecc6-138">Zie [about_Operators](about_Operators.md)voor meer informatie over de subexpression-operator van de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-138">For more information about the array sub-expression operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="accessing-and-using-array-elements"></a><span data-ttu-id="1ecc6-139">Matrix elementen openen en gebruiken</span><span class="sxs-lookup"><span data-stu-id="1ecc6-139">Accessing and using array elements</span></span>

### <a name="reading-an-array"></a><span data-ttu-id="1ecc6-140">Een matrix lezen</span><span class="sxs-lookup"><span data-stu-id="1ecc6-140">Reading an array</span></span>

<span data-ttu-id="1ecc6-141">U kunt naar een matrix verwijzen met behulp van de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-141">You can refer to an array by using its variable name.</span></span> <span data-ttu-id="1ecc6-142">Als u alle elementen in de matrix wilt weer geven, typt u de naam van de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-142">To display all the elements in the array, type the array name.</span></span> <span data-ttu-id="1ecc6-143">`$a`Als er bijvoorbeeld een matrix is met gehele getallen 0, 1, 2, tot 9; typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-143">For example, assuming `$a` is an array containing integers 0, 1, 2, until 9; typing:</span></span>

```powershell
$a
```

```Output
0
1
2
3
4
5
6
7
8
9
```

<span data-ttu-id="1ecc6-144">U kunt naar de elementen in een matrix verwijzen met behulp van een index, te beginnen bij positie 0.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-144">You can refer to the elements in an array by using an index, beginning at position 0.</span></span> <span data-ttu-id="1ecc6-145">Plaats het index nummer tussen haakjes.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-145">Enclose the index number in brackets.</span></span> <span data-ttu-id="1ecc6-146">Als u bijvoorbeeld het eerste element in de matrix wilt weer geven `$a` , typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-146">For example, to display the first element in the `$a` array, type:</span></span>

```powershell
$a[0]
```

```Output
0
```

<span data-ttu-id="1ecc6-147">Als u het derde element wilt weer geven in de `$a` matrix, typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-147">To display the third element in the `$a` array, type:</span></span>

```powershell
$a[2]
```

```Output
2
```

<span data-ttu-id="1ecc6-148">U kunt een deel van de matrix ophalen met behulp van een bereik operator voor de index.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-148">You can retrieve part of the array using a range operator for the index.</span></span> <span data-ttu-id="1ecc6-149">Als u bijvoorbeeld de tweede tot vijfde elementen van de matrix wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-149">For example, to retrieve the second to fifth elements of the array, you would type:</span></span>

```powershell
$a[1..4]
```

```Output
1
2
3
4
```

<span data-ttu-id="1ecc6-150">Het aantal negatieve getallen vanaf het einde van de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-150">Negative numbers count from the end of the array.</span></span> <span data-ttu-id="1ecc6-151">Bijvoorbeeld: '-1 ' verwijst naar het laatste element van de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-151">For example, "-1" refers to the last element of the array.</span></span> <span data-ttu-id="1ecc6-152">Als u de laatste drie elementen van de matrix wilt weer geven, typt u in oplopende volg orde index:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-152">To display the last three elements of the array, in index ascending order, type:</span></span>

```powershell
$a = 0 .. 9
$a[-3..-1]
```

```Output
7
8
9
```

<span data-ttu-id="1ecc6-153">Als u negatieve indexen in aflopende volg orde typt, verandert de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-153">If you type negative indexes in descending order, your output changes.</span></span>

```powershell
$a = 0 .. 9
$a[-1..-3]
```

```Output
9
8
7
```

<span data-ttu-id="1ecc6-154">Wees echter voorzichtig bij het gebruik van deze notatie.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-154">However, be cautious when using this notation.</span></span> <span data-ttu-id="1ecc6-155">De notatie loopt van de eind grens naar het begin van de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-155">The notation cycles from the end boundary to the beginning of the array.</span></span>

```powershell
$a = 0 .. 9
$a[2..-2]
```

```Output
2
1
0
9
8
```

<span data-ttu-id="1ecc6-156">Daarnaast moet u er ook `$a[0..-2]` voor kiezen om te verwijzen naar alle elementen van de matrix, met uitzonde ring van de laatste.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-156">Also, one common mistake is to assume `$a[0..-2]` refers to all the elements of the array, except for the last one.</span></span> <span data-ttu-id="1ecc6-157">Deze verwijst naar de elementen First, last en Second naar laatste in de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-157">It refers to the first, last, and second-to-last elements in the array.</span></span>

<span data-ttu-id="1ecc6-158">U kunt de plus operator ( `+` ) gebruiken om een bereik te combi neren met een lijst met elementen in een matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-158">You can use the plus operator (`+`) to combine a ranges with a list of elements in an array.</span></span> <span data-ttu-id="1ecc6-159">Als u bijvoorbeeld de elementen op index posities 0, 2 en 4 tot en met 6 wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-159">For example, to display the elements at index positions 0, 2, and 4 through 6, type:</span></span>

```powershell
$a = 0 .. 9
$a[0,2+4..6]
```

```Output
0
2
4
5
6
```

<span data-ttu-id="1ecc6-160">Als u meerdere bereiken en afzonderlijke elementen wilt weer geven, kunt u ook de operator plus gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-160">Also, to list multiple ranges and individual elements you can use the plus operator.</span></span> <span data-ttu-id="1ecc6-161">Als u bijvoorbeeld elementen wilt weer geven van nul tot twee, vier tot zes en het element met het achtste positie type:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-161">For example, to list elements zero to two, four to six, and the element at eighth positional type:</span></span>

```powershell
$a = 0..9
$a[+0..2+4..6+8]
```

```Output
0
1
2
4
5
6
8
```

### <a name="iterations-over-array-elements"></a><span data-ttu-id="1ecc6-162">Herhalingen over matrix elementen</span><span class="sxs-lookup"><span data-stu-id="1ecc6-162">Iterations over array elements</span></span>

<span data-ttu-id="1ecc6-163">U kunt ook herhalings constructies, zoals ForEach, voor en tijdens lussen, gebruiken om te verwijzen naar de elementen in een matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-163">You can also use looping constructs, such as ForEach, For, and While loops, to refer to the elements in an array.</span></span> <span data-ttu-id="1ecc6-164">Als u bijvoorbeeld een ForEach-lus wilt gebruiken om de elementen in de matrix weer te geven `$a` , typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-164">For example, to use a ForEach loop to display the elements in the `$a` array, type:</span></span>

```powershell
$a = 0..9
foreach ($element in $a) {
  $element
}
```

```Output
0
1
2
3
4
5
6
7
8
9
```

<span data-ttu-id="1ecc6-165">De foreach-lus doorloopt de matrix en retourneert elke waarde in de matrix totdat het einde van de matrix wordt bereikt.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-165">The Foreach loop iterates through the array and returns each value in the array until reaching the end of the array.</span></span>

<span data-ttu-id="1ecc6-166">De for-lus is handig wanneer u prestatie meter items verhoogt tijdens het onderzoeken van de elementen in een matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-166">The For loop is useful when you are incrementing counters while examining the elements in an array.</span></span> <span data-ttu-id="1ecc6-167">Als u bijvoorbeeld een for-lus wilt gebruiken om elke andere waarde in een matrix te retour neren, typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-167">For example, to use a For loop to return every other value in an array, type:</span></span>

```powershell
$a = 0..9
for ($i = 0; $i -le ($a.length - 1); $i += 2) {
  $a[$i]
}
```

```Output
0
2
4
6
8
```

<span data-ttu-id="1ecc6-168">U kunt een while-lus gebruiken om de elementen in een matrix weer te geven totdat een gedefinieerde voor waarde niet meer waar is.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-168">You can use a While loop to display the elements in an array until a defined condition is no longer true.</span></span> <span data-ttu-id="1ecc6-169">Als u bijvoorbeeld de elementen in de matrix wilt weer geven `$a` terwijl de index van de matrix kleiner is dan 4, typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-169">For example, to display the elements in the `$a` array while the array index is less than 4, type:</span></span>

```powershell
$a = 0..9
$i=0
while($i -lt 4) {
  $a[$i];
  $i++
}
```

```Output
0
1
2
3
```

## <a name="properties-of-arrays"></a><span data-ttu-id="1ecc6-170">Eigenschappen van matrices</span><span class="sxs-lookup"><span data-stu-id="1ecc6-170">Properties of arrays</span></span>

### <a name="count-or-length-or-longlength"></a><span data-ttu-id="1ecc6-171">Aantal of lengte of LongLength</span><span class="sxs-lookup"><span data-stu-id="1ecc6-171">Count or Length or LongLength</span></span>

<span data-ttu-id="1ecc6-172">Gebruik de `Length` eigenschap of de alias om te bepalen hoeveel items zich in een matrix bevinden `Count` .</span><span class="sxs-lookup"><span data-stu-id="1ecc6-172">To determine how many items are in an array, use the `Length` property or its `Count` alias.</span></span> <span data-ttu-id="1ecc6-173">`Longlength` is handig als de matrix meer dan 2.147.483.647 elementen bevat.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-173">`Longlength` is useful if the array contains more than 2,147,483,647 elements.</span></span>

```powershell
$a = 0..9
$a.Count
$a.Length
```

```Output
10
10
```

### <a name="rank"></a><span data-ttu-id="1ecc6-174">Positie</span><span class="sxs-lookup"><span data-stu-id="1ecc6-174">Rank</span></span>

<span data-ttu-id="1ecc6-175">Retourneert het aantal dimensies in de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-175">Returns the number of dimensions in the array.</span></span> <span data-ttu-id="1ecc6-176">De meeste matrices in Power Shell hebben één dimensie.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-176">Most arrays in PowerShell have one dimension, only.</span></span> <span data-ttu-id="1ecc6-177">Zelfs wanneer u denkt dat u een multidimensionale matrix bouwt zoals in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-177">Even when you think you are building a multidimensional array like the following example:</span></span>

```powershell
$a = @(
  @(0,1),
  @("b", "c"),
  @(Get-Process)
)

"`$a rank: $($a.Rank)"
"`$a length: $($a.Length)"
"`$a length: $($a.Length)"
"Process `$a[2][1]: $($a[2][1].ProcessName)"
```

<span data-ttu-id="1ecc6-178">In dit voor beeld maakt u een eendimensionale matrix die andere matrices bevat.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-178">In this example, you are creating a single-dimensional array that contains other arrays.</span></span> <span data-ttu-id="1ecc6-179">Dit wordt ook wel een _gekartelde matrix_ genoemd.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-179">This is also known as a _jagged array_.</span></span> <span data-ttu-id="1ecc6-180">De eigenschap **Rank** heeft aangetoond dat dit eendimensionale is.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-180">The **Rank** property proved that this is single-dimensional.</span></span> <span data-ttu-id="1ecc6-181">Voor toegang tot items in een gekartelde matrix moeten de indexen tussen vier Kante haken ( `[]` ) staan.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-181">To access items in a jagged array, the indexes must be in separate brackets (`[]`).</span></span>

```Output
$a rank: 1
$a length: 3
$a[2] length: 348
Process $a[2][1]: AcroRd32
```

<span data-ttu-id="1ecc6-182">Multidimensionale matrices worden opgeslagen in de [volg orde row-major](https://wikipedia.org/wiki/Row-_and_column-major_order).</span><span class="sxs-lookup"><span data-stu-id="1ecc6-182">Multidimensional arrays are stored in [row-major order](https://wikipedia.org/wiki/Row-_and_column-major_order).</span></span> <span data-ttu-id="1ecc6-183">In het volgende voor beeld ziet u hoe u een echte multidimensionale matrix maakt.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-183">The following example shows how to create a truly multidimensional array.</span></span>

```powershell
[string[,]]$rank2 = [string[,]]::New(3,2)
$rank2.rank
$rank2.Length
$rank2[0,0] = 'a'
$rank2[0,1] = 'b'
$rank2[1,0] = 'c'
$rank2[1,1] = 'd'
$rank2[2,0] = 'e'
$rank2[2,1] = 'f'
$rank2[1,1]
```

```Output
2
6
d
```

<span data-ttu-id="1ecc6-184">Als u toegang wilt krijgen tot items in een multidimensionale matrix, scheidt u de indexen met een komma ( `,` ) binnen één set haken ( `[]` ).</span><span class="sxs-lookup"><span data-stu-id="1ecc6-184">To access items in a multidimensional array, separate the indexes using a comma (`,`) within a single set of brackets (`[]`).</span></span>

<span data-ttu-id="1ecc6-185">Bij sommige bewerkingen op een multidimensionale matrix, zoals replicatie en samen voegen, moet de matrix worden afgevlakt.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-185">Some operations on a multidimensional array, such as replication and concatenation, require that array to be flattened.</span></span> <span data-ttu-id="1ecc6-186">Met afvlakking wordt de matrix omgezet in een eendimensionale matrix van het type unperked.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-186">Flattening turns the array into a 1-dimensional array of unconstrained type.</span></span> <span data-ttu-id="1ecc6-187">De resulterende matrix neemt alle elementen in de volg orde van de rij-groot op.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-187">The resulting array takes on all the elements in row-major order.</span></span> <span data-ttu-id="1ecc6-188">Kijk eens naar het volgende voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-188">Consider the following example:</span></span>

```powershell
$a = "red",$true
$b = (New-Object 'int[,]' 2,2)
$b[0,0] = 10
$b[0,1] = 20
$b[1,0] = 30
$b[1,1] = 40
$c = $a + $b
$a.GetType().Name
$b.GetType().Name
$c.GetType().Name
$c
```

<span data-ttu-id="1ecc6-189">In de uitvoer ziet u `$c` een eendimensionale matrix met daarin de items van `$a` en in de `$b` volg orde van de rij-Major.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-189">The output shows that `$c` is a 1-dimensional array containing the items from `$a` and `$b` in row-major order.</span></span>

```output
Object[]
Int32[,]
Object[]
red
True
10
20
30
40
```

## <a name="methods-of-arrays"></a><span data-ttu-id="1ecc6-190">Methoden van matrices</span><span class="sxs-lookup"><span data-stu-id="1ecc6-190">Methods of arrays</span></span>

### <a name="clear"></a><span data-ttu-id="1ecc6-191">Veilig</span><span class="sxs-lookup"><span data-stu-id="1ecc6-191">Clear</span></span>

<span data-ttu-id="1ecc6-192">Hiermee stelt u alle element waarden in op de _standaard waarde_ van het element type van de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-192">Sets all element values to the _default value_ of the array's element type.</span></span>
<span data-ttu-id="1ecc6-193">De methode Clear () stelt de grootte van de matrix niet opnieuw in.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-193">The Clear() method does not reset the size of the array.</span></span>

<span data-ttu-id="1ecc6-194">In het volgende voor beeld `$a` is een matrix met objecten.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-194">In the following example `$a` is an array of objects.</span></span>

```powershell
$a = 1, 2, 3
$a.Clear()
$a | % { $null -eq $_ }
```

```Output
True
True
True
```

<span data-ttu-id="1ecc6-195">In dit voor beeld `$intA` wordt expliciet getypt om gehele getallen te bevatten.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-195">In this example, `$intA` is explicitly typed to contain integers.</span></span>

```powershell
[int[]] $intA = 1, 2, 3
$intA.Clear()
$intA
```

```Output
0
0
0
```

### <a name="foreach"></a><span data-ttu-id="1ecc6-196">ForEach</span><span class="sxs-lookup"><span data-stu-id="1ecc6-196">ForEach</span></span>

<span data-ttu-id="1ecc6-197">Hiermee kunt u alle elementen in de matrix herhalen en een bepaalde bewerking uitvoeren voor elk element van de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-197">Allows to iterate over all elements in the array and perform a given operation for each element of the array.</span></span>

<span data-ttu-id="1ecc6-198">De ForEach-methode heeft verschillende Overloads die verschillende bewerkingen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-198">The ForEach method has several overloads that perform different operations.</span></span>

```
ForEach(scriptblock expression)
ForEach(scriptblock expression, object[] arguments)
ForEach(type convertToType)
ForEach(string propertyName)
ForEach(string propertyName, object[] newValue)
ForEach(string methodName)
ForEach(string methodName, object[] arguments)
```

#### <a name="foreachscriptblock-expression"></a><span data-ttu-id="1ecc6-199">ForEach (script Block-expressie)</span><span class="sxs-lookup"><span data-stu-id="1ecc6-199">ForEach(scriptblock expression)</span></span>

#### <a name="foreachscriptblock-expression-object-arguments"></a><span data-ttu-id="1ecc6-200">ForEach (script Block-expressie, object [] argumenten)</span><span class="sxs-lookup"><span data-stu-id="1ecc6-200">ForEach(scriptblock expression, object[] arguments)</span></span>

<span data-ttu-id="1ecc6-201">Deze methode is toegevoegd in Power shell v4.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-201">This method was added in PowerShell v4.</span></span>

> [!NOTE]
> <span data-ttu-id="1ecc6-202">De syntaxis vereist het gebruik van een script blok.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-202">The syntax requires the usage of a script block.</span></span> <span data-ttu-id="1ecc6-203">Haakjes zijn optioneel als de script Block de enige para meter is.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-203">Parentheses are optional if the scriptblock is the only parameter.</span></span> <span data-ttu-id="1ecc6-204">Er mag ook geen spatie tussen de methode en het haakje openen of de accolade worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-204">Also, there must not be a space between the method and the opening parenthesis or brace.</span></span>

<span data-ttu-id="1ecc6-205">In het volgende voor beeld ziet u hoe u de methode foreach gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-205">The following example shows how use the foreach method.</span></span> <span data-ttu-id="1ecc6-206">In dit geval is de bedoeling de vier Kante waarde van de elementen in de matrix te genereren.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-206">In this case the intent is to generate the square value of the elements in the array.</span></span>

```powershell
$a = @(0 .. 3)
$a.ForEach({ $_ * $_})
```

```Output
0
1
4
9
```

<span data-ttu-id="1ecc6-207">Net als de `-ArgumentList` para meter van `ForEach-Object` `arguments` kan de para meter een matrix met argumenten door geven aan een script blok dat is geconfigureerd om deze te accepteren.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-207">Just like the `-ArgumentList` parameter of `ForEach-Object`, the `arguments` parameter allows the passing of an array of arguments to a script block configured to accept them.</span></span>

<span data-ttu-id="1ecc6-208">Zie [about_Splatting](about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-208">For more information about the behavior of **ArgumentList**, see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

#### <a name="foreachtype-converttotype"></a><span data-ttu-id="1ecc6-209">ForEach (type convertToType)</span><span class="sxs-lookup"><span data-stu-id="1ecc6-209">ForEach(type convertToType)</span></span>

<span data-ttu-id="1ecc6-210">De `ForEach` methode kan worden gebruikt om de elementen snel te casten naar een ander type. in het volgende voor beeld ziet u hoe u een lijst met teken reeks datums converteert naar een `[DateTime]` type.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-210">The `ForEach` method can be used to swiftly cast the elements to a different type; the following example shows how to convert a list of string dates to `[DateTime]` type.</span></span>

```powershell
@("1/1/2017", "2/1/2017", "3/1/2017").ForEach([datetime])
```

```Output

Sunday, January 1, 2017 12:00:00 AM
Wednesday, February 1, 2017 12:00:00 AM
Wednesday, March 1, 2017 12:00:00 AM
```

#### <a name="foreachstring-propertyname"></a><span data-ttu-id="1ecc6-211">ForEach (String PropertyName)</span><span class="sxs-lookup"><span data-stu-id="1ecc6-211">ForEach(string propertyName)</span></span>

#### <a name="foreachstring-propertyname-object-newvalue"></a><span data-ttu-id="1ecc6-212">ForEach (String PropertyName, object [] newValue)</span><span class="sxs-lookup"><span data-stu-id="1ecc6-212">ForEach(string propertyName, object[] newValue)</span></span>

<span data-ttu-id="1ecc6-213">De `ForEach` methode kan ook worden gebruikt om snel eigenschaps waarden op te halen of in te stellen voor elk item in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-213">The `ForEach` method can also be used to quickly retrieve, or set property values for every item in the collection.</span></span>

```powershell
# Set all LastAccessTime properties of files to the current date.
(dir 'C:\Temp').ForEach('LastAccessTime', (Get-Date))
# View the newly set LastAccessTime of all items, and find Unique entries.
(dir 'C:\Temp').ForEach('LastAccessTime') | Get-Unique
```

```Output
Wednesday, June 20, 2018 9:21:57 AM
```

#### <a name="foreachstring-methodname"></a><span data-ttu-id="1ecc6-214">ForEach (String methode)</span><span class="sxs-lookup"><span data-stu-id="1ecc6-214">ForEach(string methodName)</span></span>

#### <a name="foreachstring-methodname-object-arguments"></a><span data-ttu-id="1ecc6-215">ForEach (String Method methode, object [] argumenten)</span><span class="sxs-lookup"><span data-stu-id="1ecc6-215">ForEach(string methodName, object[] arguments)</span></span>

<span data-ttu-id="1ecc6-216">Ten slotte `ForEach` kunnen methoden worden gebruikt om een methode uit te voeren voor elk item in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-216">Lastly, `ForEach` methods can be used to execute a method on every item in the collection.</span></span>

```powershell
("one", "two", "three").ForEach("ToUpper")
```

```Output
ONE
TWO
THREE
```

<span data-ttu-id="1ecc6-217">Net als de `-ArgumentList` para meter van `ForEach-Object` `arguments` kan de para meter een matrix met argumenten door geven aan een script blok dat is geconfigureerd om deze te accepteren.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-217">Just like the `-ArgumentList` parameter of `ForEach-Object`, the `arguments` parameter allows the passing of an array of arguments to a script block configured to accept them.</span></span>

> [!NOTE]
> <span data-ttu-id="1ecc6-218">Starten in Windows Power Shell 3,0 het ophalen van eigenschappen en het uitvoeren van methoden voor elk item in een verzameling kan ook worden uitgevoerd met behulp van methoden van scalaire objecten en verzamelingen. hier vindt u meer informatie over deze [about_methods](about_methods.md).</span><span class="sxs-lookup"><span data-stu-id="1ecc6-218">Starting in Windows PowerShell 3.0 retrieving properties and executing methods for each item in a collection can also be accomplished using "Methods of scalar objects and collections" You can read more about that here [about_methods](about_methods.md).</span></span>

### <a name="where"></a><span data-ttu-id="1ecc6-219">Waar</span><span class="sxs-lookup"><span data-stu-id="1ecc6-219">Where</span></span>

<span data-ttu-id="1ecc6-220">Hiermee kunt u de elementen van de matrix filteren of selecteren.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-220">Allows to filter or select the elements of the array.</span></span> <span data-ttu-id="1ecc6-221">Het script moet resulteren in iets anders dan: nul (0), lege teken reeks `$false` of `$null` voor het element dat moet worden weer gegeven na de `Where`</span><span class="sxs-lookup"><span data-stu-id="1ecc6-221">The script must evaluate to anything different than: zero (0), empty string, `$false` or `$null` for the element to show after the `Where`</span></span>

<span data-ttu-id="1ecc6-222">Er is één definitie voor de `Where` methode.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-222">There is one definition for the `Where` method.</span></span>

```
Where(scriptblock expression[, WhereOperatorSelectionMode mode
                            [, int numberToReturn]])
```

> [!NOTE]
> <span data-ttu-id="1ecc6-223">De syntaxis vereist het gebruik van een script blok.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-223">The syntax requires the usage of a script block.</span></span> <span data-ttu-id="1ecc6-224">Haakjes zijn optioneel als de script Block de enige para meter is.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-224">Parentheses are optional if the scriptblock is the only parameter.</span></span> <span data-ttu-id="1ecc6-225">Er mag ook geen spatie tussen de methode en het haakje openen of de accolade worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-225">Also, there must not be a space between the method and the opening parenthesis or brace.</span></span>

<span data-ttu-id="1ecc6-226">De `Expression` script Block is vereist voor het filteren, het `mode` optionele argument biedt aanvullende selectie mogelijkheden en `numberToReturn` met het optionele argument kunt u het aantal items dat door het filter wordt geretourneerd, beperken.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-226">The `Expression` is scriptblock that is required for filtering, the `mode` optional argument allows additional selection capabilities, and the `numberToReturn` optional argument allows the ability to limit how many items are returned from the filter.</span></span>

<span data-ttu-id="1ecc6-227">De acceptabele waarden voor `mode` zijn:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-227">The acceptable values for `mode` are:</span></span>

- <span data-ttu-id="1ecc6-228">Standaard (0)-alle items retour neren</span><span class="sxs-lookup"><span data-stu-id="1ecc6-228">Default (0) - Return all items</span></span>
- <span data-ttu-id="1ecc6-229">Eerste (1)-retourneert het eerste item</span><span class="sxs-lookup"><span data-stu-id="1ecc6-229">First (1) - Return the first item</span></span>
- <span data-ttu-id="1ecc6-230">Last (2)-het laatste item retour neren</span><span class="sxs-lookup"><span data-stu-id="1ecc6-230">Last (2) - Return the last item</span></span>
- <span data-ttu-id="1ecc6-231">SkipUntil (3)-items overs Laan tot voor waarde is ingesteld op ' True ', de resterende items retour neren</span><span class="sxs-lookup"><span data-stu-id="1ecc6-231">SkipUntil (3) - Skip items until condition is true, the return the remaining items</span></span>
- <span data-ttu-id="1ecc6-232">Tot (4): alle items retour neren totdat de voor waarde waar is</span><span class="sxs-lookup"><span data-stu-id="1ecc6-232">Until (4) - Return all items until condition is true</span></span>
- <span data-ttu-id="1ecc6-233">Splitsen (5)-een matrix van twee elementen retour neren</span><span class="sxs-lookup"><span data-stu-id="1ecc6-233">Split (5) - Return an array of two elements</span></span>
  - <span data-ttu-id="1ecc6-234">Het eerste element bevat overeenkomende items</span><span class="sxs-lookup"><span data-stu-id="1ecc6-234">The first element contains matching items</span></span>
  - <span data-ttu-id="1ecc6-235">Het tweede element bevat de resterende items</span><span class="sxs-lookup"><span data-stu-id="1ecc6-235">The second element contains the remaining items</span></span>

<span data-ttu-id="1ecc6-236">In het volgende voor beeld ziet u hoe u alle oneven getallen uit de matrix selecteert.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-236">The following example shows how to select all odd numbers from the array.</span></span>

```powershell
(0..9).Where{ $_ % 2 }
```

```Output
1
3
5
7
9
```

<span data-ttu-id="1ecc6-237">In dit voor beeld ziet u hoe u de teken reeksen selecteert die niet leeg zijn.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-237">This example show how to select the strings that are not empty.</span></span>

```powershell
('hi', '', 'there').Where({$_.Length})
```

```Output
hi
there
```

#### <a name="default"></a><span data-ttu-id="1ecc6-238">Standaard</span><span class="sxs-lookup"><span data-stu-id="1ecc6-238">Default</span></span>

<span data-ttu-id="1ecc6-239">`Default`In de modus worden items gefilterd met behulp van de `Expression` script Block.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-239">The `Default` mode filters items using the `Expression` scriptblock.</span></span>

<span data-ttu-id="1ecc6-240">Als er een `numberToReturn` is opgegeven, wordt hiermee het maximum aantal items opgegeven dat moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-240">If a `numberToReturn` is provided, it specifies the maximum number of items to return.</span></span>

```powershell
# Get the zip files in the current users profile, sorted by LastAccessTime.
$Zips = dir $env:userprofile -Recurse '*.zip' | Sort-Object LastAccessTime
# Get the least accessed file over 100MB
$Zips.Where({$_.Length -gt 100MB}, 'Default', 1)
```

> [!NOTE]
> <span data-ttu-id="1ecc6-241">Zowel de `Default` modus als de `First` modus retour neren de eerste ( `numberToReturn` ) items en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-241">Both the `Default` mode and `First` mode return the first (`numberToReturn`) items, and can be used interchangeably.</span></span>

#### <a name="last"></a><span data-ttu-id="1ecc6-242">Laatste</span><span class="sxs-lookup"><span data-stu-id="1ecc6-242">Last</span></span>

```powershell
$h = (Get-Date).AddHours(-1)
$logs = dir 'C:\' -Recurse '*.log' | Sort-Object CreationTime
# Find the last 5 log files created in the past hour.
$logs.Where({$_.CreationTime -gt $h}, 'Last', 5)
```

#### <a name="skipuntil"></a><span data-ttu-id="1ecc6-243">SkipUntil</span><span class="sxs-lookup"><span data-stu-id="1ecc6-243">SkipUntil</span></span>

<span data-ttu-id="1ecc6-244">`SkipUntil`In de modus worden alle objecten in een verzameling overgeslagen totdat een object het filter voor script blok expressies door gegeven.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-244">The `SkipUntil` mode skips all objects in a collection until an object passes the script block expression filter.</span></span> <span data-ttu-id="1ecc6-245">Vervolgens worden **alle** resterende verzamelings items geretourneerd zonder ze te testen.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-245">It then returns **ALL** remaining collection items without testing them.</span></span> <span data-ttu-id="1ecc6-246">_Er wordt slechts één door gegeven item getest_.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-246">_Only one passing item is tested_.</span></span>

<span data-ttu-id="1ecc6-247">Dit betekent dat de geretourneerde verzameling zowel _door gegeven_ als _niet-door gegeven_ items bevat die niet zijn getest.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-247">This means the returned collection contains both _passing_ and _non-passing_ items that have NOT been tested.</span></span>

<span data-ttu-id="1ecc6-248">Het aantal geretourneerde items kan worden beperkt door een waarde door te geven aan het `numberToReturn` argument.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-248">The number of items returned can be limited by passing a value to the `numberToReturn` argument.</span></span>

```powershell
$computers = "Server01", "Server02", "Server03", "localhost", "Server04"
# Find the first available online server.
$computers.Where({ Test-Connection $_ }, 'SkipUntil', 1)
```

```Output
localhost
```

#### <a name="until"></a><span data-ttu-id="1ecc6-249">Totdat</span><span class="sxs-lookup"><span data-stu-id="1ecc6-249">Until</span></span>

<span data-ttu-id="1ecc6-250">De modus `Until` keert de `SkipUntil` modus om.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-250">The `Until` mode inverts the `SkipUntil` mode.</span></span>  <span data-ttu-id="1ecc6-251">**Alle** items in een verzameling worden geretourneerd totdat een item de script blok expressie door gegeven.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-251">It returns **ALL** items in a collection until an item passes the script block expression.</span></span> <span data-ttu-id="1ecc6-252">Zodra een item de script Block-expressie heeft _door gegeven_ , stopt de methode met het `Where` verwerken van items.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-252">Once an item _passes_ the scriptblock expression, the `Where` method stops processing items.</span></span>

<span data-ttu-id="1ecc6-253">Dit betekent dat u de eerste set van _niet-door gegeven_ items van de `Where` methode ontvangt.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-253">This means that you receive the first set of _non-passing_ items from the `Where` method.</span></span> <span data-ttu-id="1ecc6-254">_Nadat_ één item is door gegeven, wordt de rest niet getest of geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-254">_After_ one item passes, the rest are NOT tested or returned.</span></span>

<span data-ttu-id="1ecc6-255">Het aantal geretourneerde items kan worden beperkt door een waarde door te geven aan het `numberToReturn` argument.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-255">The number of items returned can be limited by passing a value to the `numberToReturn` argument.</span></span>

```powershell
# Retrieve the first set of numbers less than or equal to 10.
(1..50).Where({$_ -gt 10}, 'Until')
# This would perform the same operation.
(1..50).Where({$_ -le 10})
```

```Output
1
2
3
4
5
6
7
8
9
10
```

> [!NOTE]
> <span data-ttu-id="1ecc6-256">`Until`Met en `SkipUntil` zonder een batch met items te testen.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-256">Both `Until` and `SkipUntil` operate under the premise of NOT testing a batch of items.</span></span>
>
> <span data-ttu-id="1ecc6-257">`Until` retourneert de items **vóór** de eerste _fase_.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-257">`Until` returns the items **BEFORE** the first _pass_.</span></span>
>
> <span data-ttu-id="1ecc6-258">`SkipUntil` retourneert alle items **na** de eerste _fase_, inclusief het eerste door gegeven item.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-258">`SkipUntil` returns all the items **AFTER** the first _pass_, including the first passing item.</span></span>

#### <a name="split"></a><span data-ttu-id="1ecc6-259">Splitsen</span><span class="sxs-lookup"><span data-stu-id="1ecc6-259">Split</span></span>

<span data-ttu-id="1ecc6-260">De `Split` modus splitst of groepeert items in twee afzonderlijke verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-260">The `Split` mode splits, or groups collection items into two separate collections.</span></span> <span data-ttu-id="1ecc6-261">Gebruikers die de script Block-expressie door geven, en de expressies die dat niet doen.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-261">Those that pass the scriptblock expression, and those that do not.</span></span>

<span data-ttu-id="1ecc6-262">Als er een `numberToReturn` is opgegeven, bevat de eerste verzameling de _door gegeven_ items, niet om de opgegeven waarde te overschrijden.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-262">If a `numberToReturn` is specified, the first collection, contains the _passing_ items, not to exceed the value specified.</span></span>

<span data-ttu-id="1ecc6-263">De resterende objecten, zelfs degene die het expressie filter **door geven** , worden geretourneerd in de tweede verzameling.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-263">The remaining objects, even those that **PASS** the expression filter, are returned in the second collection.</span></span>

```powershell
$running, $stopped = (Get-Service).Where({$_.Status -eq 'Running'}, 'Split')
$running
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
...
```

```powershell
$stopped
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
...
```

## <a name="get-the-members-of-an-array"></a><span data-ttu-id="1ecc6-264">De leden van een matrix ophalen</span><span class="sxs-lookup"><span data-stu-id="1ecc6-264">Get the members of an array</span></span>

<span data-ttu-id="1ecc6-265">Gebruik de para meter **input object** van de cmdlet om de eigenschappen en methoden van een matrix op te halen, zoals de eigenschap length en de methode **WaardeInstellen** `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="1ecc6-265">To get the properties and methods of an array, such as the Length property and the **SetValue** method, use the **InputObject** parameter of the `Get-Member` cmdlet.</span></span>

<span data-ttu-id="1ecc6-266">Wanneer u een matrix naar verplaatst `Get-Member` , verzendt Power shell de items per keer en `Get-Member` retourneert het type van elk item in de matrix (dubbele waarden worden genegeerd).</span><span class="sxs-lookup"><span data-stu-id="1ecc6-266">When you pipe an array to `Get-Member`, PowerShell sends the items one at a time and `Get-Member` returns the type of each item in the array (ignoring duplicates).</span></span>

<span data-ttu-id="1ecc6-267">Wanneer u de para meter **input object** gebruikt, `Get-Member` retourneert de leden van de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-267">When you use the **InputObject** parameter, `Get-Member` returns the members of the array.</span></span>

<span data-ttu-id="1ecc6-268">Met de volgende opdracht worden bijvoorbeeld de leden van de `$a` matrix variabele opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-268">For example, the following command gets the members of the `$a` array variable.</span></span>

```powershell
Get-Member -InputObject $a
```

<span data-ttu-id="1ecc6-269">U kunt ook de leden van een matrix ophalen door een komma (,) te typen vóór de waarde die is gesluisd met de `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-269">You can also get the members of an array by typing a comma (,) before the value that is piped to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="1ecc6-270">De komma maakt de matrix het tweede item in een matrix met matrices.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-270">The comma makes the array the second item in an array of arrays.</span></span> <span data-ttu-id="1ecc6-271">Power shell Pipet de matrix per keer en `Get-Member` retourneert de leden van de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-271">PowerShell pipes the arrays one at a time and `Get-Member` returns the members of the array.</span></span> <span data-ttu-id="1ecc6-272">Net als de volgende twee voor beelden.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-272">Like the next two examples.</span></span>

```powershell
,$a | Get-Member

,(1,2,3) | Get-Member
```

## <a name="manipulating-an-array"></a><span data-ttu-id="1ecc6-273">Een matrix bewerken</span><span class="sxs-lookup"><span data-stu-id="1ecc6-273">Manipulating an array</span></span>

<span data-ttu-id="1ecc6-274">U kunt de elementen in een matrix wijzigen, een element aan een matrix toevoegen en de waarden van twee matrices combi neren in een derde matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-274">You can change the elements in an array, add an element to an array, and combine the values from two arrays into a third array.</span></span>

<span data-ttu-id="1ecc6-275">Als u de waarde van een bepaald element in een matrix wilt wijzigen, geeft u de naam van de matrix en de index op van het element dat u wilt wijzigen, en gebruikt u vervolgens de toewijzings operator ( `=` ) om een nieuwe waarde voor het element op te geven.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-275">To change the value of a particular element in an array, specify the array name and the index of the element that you want to change, and then use the assignment operator (`=`) to specify a new value for the element.</span></span> <span data-ttu-id="1ecc6-276">Als u bijvoorbeeld de waarde van het tweede item in de `$a` matrix (index positie 1) op 10 wilt wijzigen, typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-276">For example, to change the value of the second item in the `$a` array (index position 1) to 10, type:</span></span>

```powershell
$a[1] = 10
```

<span data-ttu-id="1ecc6-277">U kunt ook de **WaardeInstellen** -methode van een matrix gebruiken om een waarde te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-277">You can also use the **SetValue** method of an array to change a value.</span></span> <span data-ttu-id="1ecc6-278">In het volgende voor beeld wordt de tweede waarde (index positie 1) van de `$a` matrix gewijzigd in 500:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-278">The following example changes the second value (index position 1) of the `$a` array to 500:</span></span>

```powershell
$a.SetValue(500,1)
```

<span data-ttu-id="1ecc6-279">U kunt de `+=` operator gebruiken om een element aan een matrix toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-279">You can use the `+=` operator to add an element to an array.</span></span> <span data-ttu-id="1ecc6-280">In het volgende voor beeld ziet u hoe u een element aan de matrix kunt toevoegen `$a` .</span><span class="sxs-lookup"><span data-stu-id="1ecc6-280">The following example shows how to add an element to the `$a` array.</span></span>

```powershell
$a = @(0..4)
$a += 5
```

> [!NOTE]
> <span data-ttu-id="1ecc6-281">Wanneer u de `+=` operator gebruikt, maakt Power shell in feite een nieuwe matrix met de waarden van de oorspronkelijke matrix en de toegevoegde waarde.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-281">When you use the `+=` operator, PowerShell actually creates a new array with the values of the original array and the added value.</span></span> <span data-ttu-id="1ecc6-282">Dit kan leiden tot prestatie problemen als de bewerking meerdere keren wordt herhaald of de grootte van de matrix te groot is.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-282">This might cause performance issues if the operation is repeated several times or the size of the array is too big.</span></span>

<span data-ttu-id="1ecc6-283">Het is niet eenvoudig om elementen uit een matrix te verwijderen, maar u kunt wel een nieuwe matrix maken die alleen geselecteerde elementen van een bestaande matrix bevat.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-283">It is not easy to delete elements from an array, but you can create a new array that contains only selected elements of an existing array.</span></span> <span data-ttu-id="1ecc6-284">Als u bijvoorbeeld de `$t` matrix met alle elementen in de matrix wilt maken, met `$a` uitzonde ring van de waarde op index positie 2, typt u:</span><span class="sxs-lookup"><span data-stu-id="1ecc6-284">For example, to create the `$t` array with all the elements in the `$a` array except for the value at index position 2, type:</span></span>

```powershell
$t = $a[0,1 + 3..($a.length - 1)]
```

<span data-ttu-id="1ecc6-285">Als u twee matrices wilt combi neren tot één matrix, gebruikt u de plus operator ( `+` ).</span><span class="sxs-lookup"><span data-stu-id="1ecc6-285">To combine two arrays into a single array, use the plus operator (`+`).</span></span> <span data-ttu-id="1ecc6-286">In het volgende voor beeld worden twee matrices gemaakt, gecombineerd en wordt de resulterende gecombineerde matrix weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-286">The following example creates two arrays, combines them, and then displays the resulting combined array.</span></span>

```powershell
$x = 1,3
$y = 5,9
$z = $x + $y
```

<span data-ttu-id="1ecc6-287">Als gevolg hiervan bevat de `$z` matrix 1, 3, 5 en 9.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-287">As a result, the `$z` array contains 1, 3, 5, and 9.</span></span>

<span data-ttu-id="1ecc6-288">Als u een matrix wilt verwijderen, wijst u een waarde `$null` toe aan de matrix.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-288">To delete an array, assign a value of `$null` to the array.</span></span> <span data-ttu-id="1ecc6-289">Met de volgende opdracht wordt de matrix in de `$a` variabele verwijderd.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-289">The following command deletes the array in the `$a` variable.</span></span>

`$a = $null`

<span data-ttu-id="1ecc6-290">U kunt de cmdlet ook gebruiken `Remove-Item` , maar een waarde van `$null` is sneller, vooral voor grote matrices.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-290">You can also use the `Remove-Item` cmdlet, but assigning a value of `$null` is faster, especially for large arrays.</span></span>

## <a name="arrays-of-zero-or-one"></a><span data-ttu-id="1ecc6-291">Matrices van nul of één</span><span class="sxs-lookup"><span data-stu-id="1ecc6-291">Arrays of zero or one</span></span>

<span data-ttu-id="1ecc6-292">Vanaf Windows Power Shell 3,0 heeft een verzameling van nul of één object de eigenschap Count en length.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-292">Beginning in Windows PowerShell 3.0, a collection of zero or one object has the Count and Length property.</span></span> <span data-ttu-id="1ecc6-293">U kunt ook indexeren naar een matrix van één object.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-293">Also, you can index into an array of one object.</span></span> <span data-ttu-id="1ecc6-294">Deze functie helpt u bij het voor komen van script fouten die optreden wanneer een opdracht die een verzameling verwacht minder dan twee items ontvangt.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-294">This feature helps you to avoid scripting errors that occur when a command that expects a collection gets fewer than two items.</span></span>

<span data-ttu-id="1ecc6-295">In de volgende voor beelden wordt deze functie gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="1ecc6-295">The following examples demonstrate this feature.</span></span>

### <a name="zero-objects"></a><span data-ttu-id="1ecc6-296">Nul objecten</span><span class="sxs-lookup"><span data-stu-id="1ecc6-296">Zero objects</span></span>

```powershell
$a = $null
$a.Count
$a.Length
```

```Output
0
0
```

### <a name="one-object"></a><span data-ttu-id="1ecc6-297">Eén object</span><span class="sxs-lookup"><span data-stu-id="1ecc6-297">One object</span></span>

```powershell
$a = 4
$a.Count
$a.Length
$a[0]
$a[-1]
```

```Output
1
1
4
4
```

## <a name="see-also"></a><span data-ttu-id="1ecc6-298">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1ecc6-298">See also</span></span>

- [<span data-ttu-id="1ecc6-299">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="1ecc6-299">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="1ecc6-300">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="1ecc6-300">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="1ecc6-301">about_Operators</span><span class="sxs-lookup"><span data-stu-id="1ecc6-301">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="1ecc6-302">about_For</span><span class="sxs-lookup"><span data-stu-id="1ecc6-302">about_For</span></span>](about_For.md)
- [<span data-ttu-id="1ecc6-303">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="1ecc6-303">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="1ecc6-304">about_While</span><span class="sxs-lookup"><span data-stu-id="1ecc6-304">about_While</span></span>](about_While.md)
