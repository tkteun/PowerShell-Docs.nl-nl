---
description: Beschrijft de operators die worden ondersteund door PowerShell.
Locale: en-US
ms.date: 04/22/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: 861fdf00e0cde1e5264a326d337a6cb995e8d67d
ms.sourcegitcommit: 96efcc9613740449940b371b34c3baafb675b1ed
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2021
ms.locfileid: "107907364"
---
# <a name="about-operators"></a><span data-ttu-id="cf5dc-103">Over operators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-103">About Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="cf5dc-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="cf5dc-104">Short description</span></span>
<span data-ttu-id="cf5dc-105">Beschrijft de operators die worden ondersteund door PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-105">Describes the operators that are supported by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="cf5dc-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="cf5dc-106">Long description</span></span>

<span data-ttu-id="cf5dc-107">Een operator is een taalelement dat u kunt gebruiken in een opdracht of expressie.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-107">An operator is a language element that you can use in a command or expression.</span></span>
<span data-ttu-id="cf5dc-108">PowerShell ondersteunt verschillende typen operators om waarden te bewerken.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-108">PowerShell supports several types of operators to help you manipulate values.</span></span>

### <a name="arithmetic-operators"></a><span data-ttu-id="cf5dc-109">Rekenkundige operators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-109">Arithmetic Operators</span></span>

<span data-ttu-id="cf5dc-110">Gebruik rekenkundige operators ( , , , , , ) om waarden in een opdracht of expressie `+` `-` te `*` `/` `%` berekenen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-110">Use arithmetic operators (`+`, `-`, `*`, `/`, `%`) to calculate values in a command or expression.</span></span> <span data-ttu-id="cf5dc-111">Met deze operators kunt u waarden toevoegen, aftrekken, vermenigvuldigen of delen en de rest (modulus) van een delingsbewerking berekenen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-111">With these operators, you can add, subtract, multiply, or divide values, and calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="cf5dc-112">Met de optellingsoperator worden elementen samenvoegt.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-112">The addition operator concatenates elements.</span></span> <span data-ttu-id="cf5dc-113">De vermenigvuldigingsoperator retourneert het opgegeven aantal kopieën van elk element.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-113">The multiplication operator returns the specified number of copies of each element.</span></span> <span data-ttu-id="cf5dc-114">U kunt rekenkundige operators gebruiken voor elk .NET-type dat ze implementeert, zoals: `Int` , , , en `String` `DateTime` `Hashtable` Matrices.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-114">You can use arithmetic operators on any .NET type that implements them, such as: `Int`, `String`, `DateTime`, `Hashtable`, and Arrays.</span></span>

<span data-ttu-id="cf5dc-115">Bitsgewijze operators ( `-band` , , , , , , ) bewerken de `-bor` `-bxor` `-bnot` `-shl` `-shr` bitpatronen in waarden.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-115">Bitwise operators (`-band`, `-bor`, `-bxor`, `-bnot`, `-shl`, `-shr`) manipulate the bit patterns in values.</span></span>

<span data-ttu-id="cf5dc-116">Zie voor meer informatie [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-116">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="assignment-operators"></a><span data-ttu-id="cf5dc-117">Toewijzingsoperators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-117">Assignment Operators</span></span>

<span data-ttu-id="cf5dc-118">Gebruik toewijzingsoperators ( , , , , , , ) om waarden toe te wijzen, te wijzigen of toe te wijzen `=` `+=` aan `-=` `*=` `/=` `%=` variabelen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-118">Use assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `%=`) to assign, change, or append values to variables.</span></span> <span data-ttu-id="cf5dc-119">U kunt rekenkundige operators combineren met toewijzing om het resultaat van de rekenkundige bewerking toe te wijzen aan een variabele.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-119">You can combine arithmetic operators with assignment to assign the result of the arithmetic operation to a variable.</span></span>

<span data-ttu-id="cf5dc-120">Zie voor meer informatie [about_Assignment_Operators](about_Assignment_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-120">For more information, see [about_Assignment_Operators](about_Assignment_Operators.md).</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="cf5dc-121">Vergelijkingsoperators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-121">Comparison Operators</span></span>

<span data-ttu-id="cf5dc-122">Gebruik vergelijkingsoperators ( `-eq` , , , , , , ) om waarden en `-ne` `-gt` `-lt` `-le` `-ge` testvoorwaarden te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-122">Use comparison operators (`-eq`, `-ne`, `-gt`, `-lt`, `-le`, `-ge`) to compare values and test conditions.</span></span> <span data-ttu-id="cf5dc-123">U kunt bijvoorbeeld twee tekenreekswaarden vergelijken om te bepalen of ze gelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-123">For example, you can compare two string values to determine whether they are equal.</span></span>

<span data-ttu-id="cf5dc-124">De vergelijkingsoperators bevatten ook operators die patronen in tekst zoeken of vervangen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-124">The comparison operators also include operators that find or replace patterns in text.</span></span> <span data-ttu-id="cf5dc-125">De operators ( `-match` , , ) gebruiken reguliere `-notmatch` `-replace` expressies en ( , ) `-like` gebruiken `-notlike` jokertekens. `*`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-125">The (`-match`, `-notmatch`, `-replace`) operators use regular expressions, and (`-like`, `-notlike`) use wildcards `*`.</span></span>

<span data-ttu-id="cf5dc-126">Vergelijkingsoperators voor insluiting bepalen of een testwaarde wordt weergegeven in een referentieset ( `-in` , , , , `-notin` `-contains` `-notcontains` ).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-126">Containment comparison operators determine whether a test value appears in a reference set (`-in`, `-notin`, `-contains`, `-notcontains`).</span></span>

<span data-ttu-id="cf5dc-127">Typevergelijkingsoperators ( `-is` , ) bepalen of een object van een bepaald type `-isnot` is.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-127">Type comparison operators (`-is`, `-isnot`) determine whether an object is of a given type.</span></span>

<span data-ttu-id="cf5dc-128">Zie voor meer informatie [about_Comparison_Operators](about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-128">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span>

### <a name="logical-operators"></a><span data-ttu-id="cf5dc-129">Logische operators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-129">Logical Operators</span></span>

<span data-ttu-id="cf5dc-130">Gebruik logische operators ( , , , , , ) om voorwaardelijke instructies `-and` te verbinden met één complexe `-or` `-xor` `-not` `!` voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-130">Use logical operators (`-and`, `-or`, `-xor`, `-not`, `!`) to connect conditional statements into a single complex conditional.</span></span> <span data-ttu-id="cf5dc-131">U kunt bijvoorbeeld een logische operator gebruiken om een objectfilter met `-and` twee verschillende voorwaarden te maken.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-131">For example, you can use a logical `-and` operator to create an object filter with two different conditions.</span></span>

<span data-ttu-id="cf5dc-132">Zie voor meer informatie [about_Logical_Operators.](about_logical_operators.md)</span><span class="sxs-lookup"><span data-stu-id="cf5dc-132">For more information, see [about_Logical_Operators](about_logical_operators.md).</span></span>

### <a name="redirection-operators"></a><span data-ttu-id="cf5dc-133">Omleidingsoperators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-133">Redirection Operators</span></span>

<span data-ttu-id="cf5dc-134">Gebruik omleidingsoperators ( , , , , en ) om de uitvoer van een opdracht of expressie naar `>` `>>` een `2>` `2>>` `2>&1` tekstbestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-134">Use redirection operators (`>`, `>>`, `2>`, `2>>`, and `2>&1`) to send the output of a command or expression to a text file.</span></span> <span data-ttu-id="cf5dc-135">De omleidingsoperators werken als de cmdlet (zonder parameters), maar u kunt ook `Out-File` foutuitvoer omleiden naar opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-135">The redirection operators work like the `Out-File` cmdlet (without parameters) but they also let you redirect error output to specified files.</span></span> <span data-ttu-id="cf5dc-136">U kunt ook de `Tee-Object` cmdlet gebruiken om uitvoer om te leiden.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-136">You can also use the `Tee-Object` cmdlet to redirect output.</span></span>

<span data-ttu-id="cf5dc-137">Zie voor meer informatie [about_Redirection](about_Redirection.md)</span><span class="sxs-lookup"><span data-stu-id="cf5dc-137">For more information, see [about_Redirection](about_Redirection.md)</span></span>

### <a name="split-and-join-operators"></a><span data-ttu-id="cf5dc-138">Operators splitsen en lid worden</span><span class="sxs-lookup"><span data-stu-id="cf5dc-138">Split and Join Operators</span></span>

<span data-ttu-id="cf5dc-139">De `-split` operators en delen en combineren `-join` subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-139">The `-split` and `-join` operators divide and combine substrings.</span></span> <span data-ttu-id="cf5dc-140">De `-split` operator splitst een tekenreeks in subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-140">The `-split` operator splits a string into substrings.</span></span> <span data-ttu-id="cf5dc-141">Met `-join` de operator worden meerdere tekenreeksen in één tekenreeks samenvoegd.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-141">The `-join` operator concatenates multiple strings into a single string.</span></span>

<span data-ttu-id="cf5dc-142">Zie voor meer informatie [about_Split](about_Split.md) en [about_Join.](about_Join.md)</span><span class="sxs-lookup"><span data-stu-id="cf5dc-142">For more information, see [about_Split](about_Split.md) and [about_Join](about_Join.md).</span></span>

### <a name="type-operators"></a><span data-ttu-id="cf5dc-143">Typeoperators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-143">Type Operators</span></span>

<span data-ttu-id="cf5dc-144">Gebruik de typeoperators ( , , ) om het type .NET Framework `-is` object te zoeken of te `-isnot` `-as` wijzigen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-144">Use the type operators (`-is`, `-isnot`, `-as`) to find or change the .NET Framework type of an object.</span></span>

<span data-ttu-id="cf5dc-145">Zie voor meer informatie [about_Type_Operators](about_Type_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-145">For more information, see [about_Type_Operators](about_Type_Operators.md).</span></span>

### <a name="unary-operators"></a><span data-ttu-id="cf5dc-146">Unaire operators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-146">Unary Operators</span></span>

<span data-ttu-id="cf5dc-147">Gebruik de unaire `++`  operators en om waarden te verhogen of te `--` degraderen en `-` voor negatie.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-147">Use the unary `++`  and `--` operators to increment or decrement values and `-` for negation.</span></span> <span data-ttu-id="cf5dc-148">Als u bijvoorbeeld de variabele wilt verhogen `$a` van `9` naar , `10` typt u `$a++` .</span><span class="sxs-lookup"><span data-stu-id="cf5dc-148">For example, to increment the variable `$a` from `9` to `10`, you type `$a++`.</span></span>

<span data-ttu-id="cf5dc-149">Zie voor meer informatie [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-149">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="special-operators"></a><span data-ttu-id="cf5dc-150">Speciale operators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-150">Special Operators</span></span>

<span data-ttu-id="cf5dc-151">Speciale operators hebben specifieke gebruiksgevallen die niet in een andere operatorgroep passen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-151">Special operators have specific use-cases that do not fit into any other operator group.</span></span> <span data-ttu-id="cf5dc-152">Met speciale operators kunt u bijvoorbeeld opdrachten uitvoeren, het gegevenstype van een waarde wijzigen of elementen ophalen uit een matrix.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-152">For example, special operators allow you to run commands, change a value's data type, or retrieve elements from an array.</span></span>

#### <a name="grouping-operator--"></a><span data-ttu-id="cf5dc-153">Groeperingsoperator `( )`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-153">Grouping operator `( )`</span></span>

<span data-ttu-id="cf5dc-154">Net als in andere talen dient `(...)` om de prioriteit van operatoren in expressies te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-154">As in other languages, `(...)` serves to override operator precedence in expressions.</span></span> <span data-ttu-id="cf5dc-155">Bijvoorbeeld: `(1 + 2) / 3`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-155">For example: `(1 + 2) / 3`</span></span>

<span data-ttu-id="cf5dc-156">In PowerShell zijn er echter aanvullende gedragingen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-156">However, in PowerShell, there are additional behaviors.</span></span>

- <span data-ttu-id="cf5dc-157">`(...)` met kunt u de uitvoer van een opdracht _laten_ deelnemen aan een expressie.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-157">`(...)` allows you to let output from a _command_ participate in an expression.</span></span> <span data-ttu-id="cf5dc-158">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="cf5dc-158">For example:</span></span>

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- <span data-ttu-id="cf5dc-159">Wanneer een opdracht of expressie tussen haakjes wordt gebruikt als het  eerste segment van een pijplijn, wordt het resultaat van de expressie altijd door een semanier geseed.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-159">When used as the first segment of a pipeline, wrapping a command or expression in parentheses invariably causes _enumeration_ of the expression result.</span></span> <span data-ttu-id="cf5dc-160">Als de haakjes een opdracht _verpakken,_ wordt deze uitgevoerd tot voltooiing met alle uitvoer die _in_ het geheugen is verzameld voordat de resultaten via de pijplijn worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-160">If the parentheses wrap a _command_, it is run to completion with all output _collected in memory_ before the results are sent through the pipeline.</span></span>

#### <a name="subexpression-operator--"></a><span data-ttu-id="cf5dc-161">Subexpressieoperator `$( )`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-161">Subexpression operator `$( )`</span></span>

<span data-ttu-id="cf5dc-162">Retourneert het resultaat van een of meer instructies.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-162">Returns the result of one or more statements.</span></span> <span data-ttu-id="cf5dc-163">Retourneert een scalaire waarde voor één resultaat.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-163">For a single result, returns a scalar.</span></span> <span data-ttu-id="cf5dc-164">Retourneert een matrix voor meerdere resultaten.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-164">For multiple results, returns an array.</span></span> <span data-ttu-id="cf5dc-165">Gebruik dit als u een expressie binnen een andere expressie wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-165">Use this when you want to use an expression within another expression.</span></span> <span data-ttu-id="cf5dc-166">Als u bijvoorbeeld de resultaten van de opdracht wilt insluiten in een tekenreeksexpressie.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-166">For example, to embed the results of command in a string expression.</span></span>

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a><span data-ttu-id="cf5dc-167">Matrixsubexpressieoperator `@( )`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-167">Array subexpression operator `@( )`</span></span>

<span data-ttu-id="cf5dc-168">Retourneert het resultaat van een of meer instructies als een matrix.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-168">Returns the result of one or more statements as an array.</span></span> <span data-ttu-id="cf5dc-169">Als er slechts één item is, heeft de matrix slechts één lid.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-169">If there is only one item, the array has only one member.</span></span>

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="hash-table-literal-syntax-"></a><span data-ttu-id="cf5dc-170">Letterlijke syntaxis van hash-tabel `@{}`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-170">Hash table literal syntax `@{}`</span></span>

<span data-ttu-id="cf5dc-171">Net als bij de subexpressie van de matrix wordt deze syntaxis gebruikt om een hash-tabel te declaren.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-171">Similar to the array subexpression, this syntax is used to declare a hash table.</span></span>
<span data-ttu-id="cf5dc-172">Zie voor meer informatie [about_Hash_Tables](about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-172">For more information, see [about_Hash_Tables](about_Hash_Tables.md).</span></span>

#### <a name="call-operator-"></a><span data-ttu-id="cf5dc-173">Operator voor aanroepen `&`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-173">Call operator `&`</span></span>

<span data-ttu-id="cf5dc-174">Voert een opdracht- of scriptblok uit.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-174">Runs a command, script, or script block.</span></span> <span data-ttu-id="cf5dc-175">Met de aanroepoperator, ook wel de aanroepoperator genoemd, kunt u opdrachten uitvoeren die zijn opgeslagen in variabelen en worden vertegenwoordigd door tekenreeksen of scriptblokken.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-175">The call operator, also known as the "invocation operator", lets you run commands that are stored in variables and represented by strings or script blocks.</span></span> <span data-ttu-id="cf5dc-176">De aanroepoperator wordt uitgevoerd in een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-176">The call operator executes in a child scope.</span></span> <span data-ttu-id="cf5dc-177">Zie voor meer informatie over [about_Scopes.](about_Scopes.md)</span><span class="sxs-lookup"><span data-stu-id="cf5dc-177">For more about scopes, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="cf5dc-178">In dit voorbeeld slaat u een opdracht op in een tekenreeks en voert u deze uit met behulp van de aanroepoperator.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-178">This example stores a command in a string and executes it using the call operator.</span></span>

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

<span data-ttu-id="cf5dc-179">De aanroepoperator parseert geen tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-179">The call operator does not parse strings.</span></span> <span data-ttu-id="cf5dc-180">Dit betekent dat u geen opdrachtparameters binnen een tekenreeks kunt gebruiken wanneer u de aanroepoperator gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-180">This means that you cannot use command parameters within a string when you use the call operator.</span></span>

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
```

<span data-ttu-id="cf5dc-181">De [cmdlet Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) kan code uitvoeren die parseringsfouten veroorzaakt bij het gebruik van de aanroepoperator.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-181">The [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) cmdlet can execute code that causes parsing errors when using the call operator.</span></span>

```
PS> & "1+1"
& : The term '1+1' is not recognized as the name of a cmdlet, function, script
file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:2
+ & "1+1"
+  ~~~~~
    + CategoryInfo          : ObjectNotFound: (1+1:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
PS> Invoke-Expression "1+1"
2
```

<span data-ttu-id="cf5dc-182">U kunt de aanroepoperator gebruiken om scripts uit te voeren met hun bestandsnamen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-182">You can use the call operator to execute scripts using their filenames.</span></span> <span data-ttu-id="cf5dc-183">In het onderstaande voorbeeld ziet u een scriptbestandsnaam die spaties bevat.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-183">The example below shows a script filename that contains spaces.</span></span> <span data-ttu-id="cf5dc-184">Wanneer u het script probeert uit te voeren, geeft PowerShell in plaats daarvan de inhoud weer van de tekenreeks met de bestandsnaam.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-184">When you try to execute the script, PowerShell instead displays the contents of the quoted string containing the filename.</span></span> <span data-ttu-id="cf5dc-185">Met de aanroepoperator kunt u de inhoud van de tekenreeks met de bestandsnaam uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-185">The call operator allows you to execute the contents of the string containing the filename.</span></span>

```
PS C:\Scripts> Get-ChildItem

    Directory: C:\Scripts


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/28/2018   1:36 PM             58 script name with spaces.ps1

PS C:\Scripts> ".\script name with spaces.ps1"
.\script name with spaces.ps1
PS C:\Scripts> & ".\script name with spaces.ps1"
Hello World!
```

<span data-ttu-id="cf5dc-186">Zie voor meer informatie over scriptblokken [about_Script_Blocks](about_Script_Blocks.md).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-186">For more about script blocks, see [about_Script_Blocks](about_Script_Blocks.md).</span></span>

#### <a name="background-operator-"></a><span data-ttu-id="cf5dc-187">Achtergrondoperator `&`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-187">Background operator `&`</span></span>

<span data-ttu-id="cf5dc-188">Voert de pijplijn vóór deze op de achtergrond uit in een PowerShell-taak.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-188">Runs the pipeline before it in the background, in a PowerShell job.</span></span> <span data-ttu-id="cf5dc-189">Deze operator werkt op dezelfde manier als de UNIX-besturingsoperator ampersand ( ), waarmee de opdracht vóór deze asynchroon in subshell als een taak `&` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-189">This operator acts similarly to the UNIX control operator ampersand (`&`), which runs the command before it asynchronously in subshell as a job.</span></span>

<span data-ttu-id="cf5dc-190">Deze operator is functioneel equivalent aan `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="cf5dc-190">This operator is functionally equivalent to `Start-Job`.</span></span> <span data-ttu-id="cf5dc-191">De achtergrondoperator start de taken standaard in de huidige werkmap van de aanroeper die de parallelle taken heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-191">By default, the background operator starts the jobs in the current working directory of the caller that started the parallel tasks.</span></span> <span data-ttu-id="cf5dc-192">In het volgende voorbeeld wordt het basisgebruik van de operator voor achtergrondfuncties gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-192">The following example demonstrates basic usage of the background job operator.</span></span>

```powershell
Get-Process -Name pwsh &
```

<span data-ttu-id="cf5dc-193">Deze opdracht is functioneel equivalent aan het volgende gebruik van `Start-Job` :</span><span class="sxs-lookup"><span data-stu-id="cf5dc-193">That command is functionally equivalent to the following usage of `Start-Job`:</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

<span data-ttu-id="cf5dc-194">Net als `Start-Job` retourneert `&` de achtergrondoperator een `Job` -object.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-194">Just like `Start-Job`, the `&` background operator returns a `Job` object.</span></span> <span data-ttu-id="cf5dc-195">Dit object kan worden gebruikt met en , net alsof u hebt gebruikt `Receive-Job` om de taak te `Remove-Job` `Start-Job` starten.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-195">This object can be used with `Receive-Job` and `Remove-Job`, just as if you had used `Start-Job` to start the job.</span></span>

```powershell
$job = Get-Process -Name pwsh &
Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

```powershell
Remove-Job $job
```

<span data-ttu-id="cf5dc-196">De `&` achtergrondoperator is ook een instructie-eindafding, net als de UNIX-besturingsoperator ampersand ( `&` ).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-196">The `&` background operator is also a statement terminator, just like the UNIX control operator ampersand (`&`).</span></span> <span data-ttu-id="cf5dc-197">Hiermee kunt u aanvullende opdrachten aanroepen na de `&` achtergrondoperator.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-197">This allows you to invoke additional commands after the `&` background operator.</span></span> <span data-ttu-id="cf5dc-198">In het volgende voorbeeld wordt het aanroepen van aanvullende opdrachten na de `&` achtergrondoperator gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-198">The following example demonstrates the invocation of additional commands after the `&` background operator.</span></span>

```powershell
$job = Get-Process -Name pwsh & Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

<span data-ttu-id="cf5dc-199">Dit is gelijk aan het volgende script:</span><span class="sxs-lookup"><span data-stu-id="cf5dc-199">This is equivalent to the following script:</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

<span data-ttu-id="cf5dc-200">Als u meerdere opdrachten wilt uitvoeren, elk in hun eigen achtergrondproces, maar allemaal op één regel, plaats dan tussen en `&` na elk van de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-200">If you want to run multiple commands, each in their own background process but all on one line, simply place `&` between and after each of the commands.</span></span>

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

<span data-ttu-id="cf5dc-201">Zie voor meer informatie over PowerShell-taken [about_Jobs.](about_Jobs.md)</span><span class="sxs-lookup"><span data-stu-id="cf5dc-201">For more information on PowerShell jobs, see [about_Jobs](about_Jobs.md).</span></span>

#### <a name="cast-operator--"></a><span data-ttu-id="cf5dc-202">Cast-operator `[ ]`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-202">Cast operator `[ ]`</span></span>

<span data-ttu-id="cf5dc-203">Converteert of beperkt objecten tot het opgegeven type.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-203">Converts or limits objects to the specified type.</span></span> <span data-ttu-id="cf5dc-204">Als de objecten niet kunnen worden geconverteerd, genereert PowerShell een fout.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-204">If the objects cannot be converted, PowerShell generates an error.</span></span>

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

<span data-ttu-id="cf5dc-205">Een cast-cast kan ook worden uitgevoerd wanneer een variabele wordt toegewezen aan met behulp van [cast-notatie](about_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-205">A cast can also be performed when a variable is assigned to using [cast notation](about_Variables.md).</span></span>

#### <a name="comma-operator-"></a><span data-ttu-id="cf5dc-206">Kommaoperator `,`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-206">Comma operator `,`</span></span>

<span data-ttu-id="cf5dc-207">Als binaire operator maakt de komma een matrix of wordt deze aan de matrix die wordt gemaakt, aan de matrix die wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-207">As a binary operator, the comma creates an array or appends to the array being created.</span></span> <span data-ttu-id="cf5dc-208">In de expressiemodus maakt de komma als unaire operator een matrix met slechts één lid.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-208">In expression mode, as a unary operator, the comma creates an array with just one member.</span></span> <span data-ttu-id="cf5dc-209">Plaats de komma vóór het lid.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-209">Place the comma before the member.</span></span>

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

<span data-ttu-id="cf5dc-210">Omdat `Write-Object` een argument verwacht, moet u de expressie tussen haakjes zetten.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-210">Since `Write-Object` expects an argument, you must put the expression in parentheses.</span></span>

#### <a name="dot-sourcing-operator-"></a><span data-ttu-id="cf5dc-211">Operator voor puntsourcing `.`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-211">Dot sourcing operator `.`</span></span>

<span data-ttu-id="cf5dc-212">Voert een script uit in het huidige bereik, zodat alle functies, aliassen en variabelen die door het script worden gemaakt, worden toegevoegd aan het huidige bereik, waardoor bestaande functies, aliassen en variabelen worden overschrijven.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-212">Runs a script in the current scope so that any functions, aliases, and variables that the script creates are added to the current scope, overriding existing ones.</span></span> <span data-ttu-id="cf5dc-213">Parameters die door het script zijn gedeclareerd, worden variabelen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-213">Parameters declared by the script become variables.</span></span> <span data-ttu-id="cf5dc-214">Parameters waarvoor geen waarde is gegeven, worden variabelen zonder waarde.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-214">Parameters for which no value has been given become variables with no value.</span></span> <span data-ttu-id="cf5dc-215">De automatische variabele `$args` blijft echter behouden.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-215">However, the automatic variable `$args` is preserved.</span></span>

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> <span data-ttu-id="cf5dc-216">De operator voor puntsourcing wordt gevolgd door een spatie.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-216">The dot sourcing operator is followed by a space.</span></span> <span data-ttu-id="cf5dc-217">Gebruik de spatie om de punt te onderscheiden van het punt ( `.` ) symbool dat de huidige map vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-217">Use the space to distinguish the dot from the dot (`.`) symbol that represents the current directory.</span></span>
>
> <span data-ttu-id="cf5dc-218">In het volgende voorbeeld wordt het Sample.ps1 in de huidige map uitgevoerd in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-218">In the following example, the Sample.ps1 script in the current directory is run in the current scope.</span></span>
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a><span data-ttu-id="cf5dc-219">Opmaakoperator `-f`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-219">Format operator `-f`</span></span>

<span data-ttu-id="cf5dc-220">Maakt tekenreeksen op met behulp van de indelingsmethode van tekenreeksobjecten.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-220">Formats strings by using the format method of string objects.</span></span> <span data-ttu-id="cf5dc-221">Voer de notatiereeks in aan de linkerkant van de operator en de objecten die aan de rechterkant van de operator moeten worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-221">Enter the format string on the left side of the operator and the objects to be formatted on the right side of the operator.</span></span>

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

<span data-ttu-id="cf5dc-222">Als u de accolades ( ) in de opgemaakte tekenreeks wilt houden, kunt u deze escapen door de `{}` accolades te verdubbelen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-222">If you need to keep the curly braces (`{}`) in the formatted string, you can escape them by doubling the curly braces.</span></span>

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

<span data-ttu-id="cf5dc-223">Zie de methode [String.Format](/dotnet/api/system.string.format) en Samengestelde opmaak [voor meer informatie.](/dotnet/standard/base-types/composite-formatting)</span><span class="sxs-lookup"><span data-stu-id="cf5dc-223">For more information, see the [String.Format](/dotnet/api/system.string.format) method and [Composite Formatting](/dotnet/standard/base-types/composite-formatting).</span></span>

#### <a name="index-operator--"></a><span data-ttu-id="cf5dc-224">Indexoperator `[ ]`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-224">Index operator `[ ]`</span></span>

<span data-ttu-id="cf5dc-225">Selecteert objecten uit geïndexeerde verzamelingen, zoals matrices en hashtabellen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-225">Selects objects from indexed collections, such as arrays and hash tables.</span></span> <span data-ttu-id="cf5dc-226">Matrixindexen zijn op nul gebaseerd, dus het eerste object wordt geïndexeerd als `[0]` .</span><span class="sxs-lookup"><span data-stu-id="cf5dc-226">Array indexes are zero-based, so the first object is indexed as `[0]`.</span></span> <span data-ttu-id="cf5dc-227">Voor matrices (alleen) kunt u ook negatieve indexen gebruiken om de laatste waarden op te halen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-227">For arrays (only), you can also use negative indexes to get the last values.</span></span> <span data-ttu-id="cf5dc-228">Hashtabellen worden geïndexeerd op sleutelwaarde.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-228">Hash tables are indexed by key value.</span></span>

```
PS> $a = 1, 2, 3
PS> $a[0]
1
PS> $a[-1]
3
```

```powershell
(Get-HotFix | Sort-Object installedOn)[-1]
```

```powershell
$h = @{key="value"; name="PowerShell"; version="2.0"}
$h["name"]
```

```output
PowerShell
```

```powershell
$x = [xml]"<doc><intro>Once upon a time...</intro></doc>"
$x["doc"]
```

```output
intro
-----
Once upon a time...
```

#### <a name="pipeline-operator-"></a><span data-ttu-id="cf5dc-229">Pijplijnoperator `|`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-229">Pipeline operator `|`</span></span>

<span data-ttu-id="cf5dc-230">Verzendt ("pipes") de uitvoer van de opdracht die voorafgaat aan de opdracht die volgt.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-230">Sends ("pipes") the output of the command that precedes it to the command that follows it.</span></span> <span data-ttu-id="cf5dc-231">Wanneer de uitvoer meer dan één object (een 'verzameling') bevat, verzendt de pijplijnoperator de objecten één voor één.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-231">When the output includes more than one object (a "collection"), the pipeline operator sends the objects one at a time.</span></span>

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="pipeline-chain-operators--and-"></a><span data-ttu-id="cf5dc-232">Pijplijnketenoperators `&&` en `||`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-232">Pipeline chain operators `&&` and `||`</span></span>

<span data-ttu-id="cf5dc-233">Voer de pijplijn aan de rechterkant voorwaardelijk uit op basis van het succes van de pijplijn aan de linkerkant.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-233">Conditionally execute the right-hand side pipeline based on the success of the left-hand side pipeline.</span></span>

```powershell
# If Get-Process successfully finds a process called notepad,
# Stop-Process -Name notepad is called
Get-Process notepad && Stop-Process -Name notepad
```

```powershell
# If npm install fails, the node_modules directory is removed
npm install || Remove-Item -Recurse ./node_modules
```

<span data-ttu-id="cf5dc-234">Zie voor meer informatie [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-234">For more information, see [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md).</span></span>

#### <a name="range-operator-"></a><span data-ttu-id="cf5dc-235">Bereikoperator `..`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-235">Range operator `..`</span></span>

<span data-ttu-id="cf5dc-236">Vertegenwoordigt de sequentiële gehele getallen in een matrix met gehele getallen op een boven- en ondergrens.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-236">Represents the sequential integers in an integer array, given an upper, and lower boundary.</span></span>

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

<span data-ttu-id="cf5dc-237">U kunt ook in omgekeerde volgorde reeksen maken.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-237">You can also create ranges in reverse order.</span></span>

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

<span data-ttu-id="cf5dc-238">Vanaf PowerShell 6 werkt de bereikoperator met **tekens** en **gehele getallen.**</span><span class="sxs-lookup"><span data-stu-id="cf5dc-238">Beginning in PowerShell 6, the range operator works with **Characters** as well as **Integers**.</span></span>

<span data-ttu-id="cf5dc-239">Als u een bereik van tekens wilt maken, sluit u de grenstekens tussen aanhalingstekens.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-239">To create a range of characters, enclose the boundary characters in quotes.</span></span>

```powershell
PS> 'a'..'f'
a
b
c
d
e
f
```

```powershell
PS> 'F'..'A'
F
E
D
C
B
A
```

#### <a name="member-access-operator-"></a><span data-ttu-id="cf5dc-240">Operator voor lidtoegang `.`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-240">Member access operator `.`</span></span>

<span data-ttu-id="cf5dc-241">Heeft toegang tot de eigenschappen en methoden van een object.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-241">Accesses the properties and methods of an object.</span></span> <span data-ttu-id="cf5dc-242">De naam van het lid kan een expressie zijn.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-242">The member name may be an expression.</span></span>

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a><span data-ttu-id="cf5dc-243">Statische lidoperator `::`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-243">Static member operator `::`</span></span>

<span data-ttu-id="cf5dc-244">Roept de statische eigenschappen en methoden van een .NET Framework aan.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-244">Calls the static properties and methods of a .NET Framework class.</span></span> <span data-ttu-id="cf5dc-245">Gebruik de statische parameter van de cmdlet om de statische eigenschappen en methoden van een object `Get-Member` te vinden.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-245">To find the static properties and methods of an object, use the Static parameter of the `Get-Member` cmdlet.</span></span>  <span data-ttu-id="cf5dc-246">De naam van het lid kan een expressie zijn.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-246">The member name may be an expression.</span></span>

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

#### <a name="ternary-operator--if-true--if-false"></a><span data-ttu-id="cf5dc-247">Ternaire operator `? <if-true> : <if-false>`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-247">Ternary operator `? <if-true> : <if-false>`</span></span>

<span data-ttu-id="cf5dc-248">U kunt de ternaire operator gebruiken als vervanging voor de `if-else` instructie in eenvoudige voorwaardelijke gevallen.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-248">You can use the ternary operator as a replacement for the `if-else` statement in simple conditional cases.</span></span>

<span data-ttu-id="cf5dc-249">Zie voor meer informatie [about_If](about_If.md).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-249">For more information, see [about_If](about_If.md).</span></span>

#### <a name="null-coalescing-operator-"></a><span data-ttu-id="cf5dc-250">Operator voor null-sameneten `??`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-250">Null-coalescing operator `??`</span></span>

<span data-ttu-id="cf5dc-251">De operator null-coalescing retourneert de waarde van de linkerope `??` operand als deze niet null is.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-251">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span> <span data-ttu-id="cf5dc-252">Anders wordt de rechterope operand geëvalueerd en wordt het resultaat ervan retourneert.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-252">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="cf5dc-253">De `??` operator evalueert de rechterope operand niet als de linkeropeen is geëvalueerd als niet-null.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-253">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
```

```Output
100
```

<span data-ttu-id="cf5dc-254">In het volgende voorbeeld wordt de rechteropeen niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-254">In the following example, the right-hand operand won't be evaluated.</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-coalescing-assignment-operator-"></a><span data-ttu-id="cf5dc-255">Toewijzingsoperator null-samen te sluiten `??=`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-255">Null-coalescing assignment operator `??=`</span></span>

<span data-ttu-id="cf5dc-256">De toewijzingsoperator null-coalescing wijst de waarde van de rechteropend alleen toe aan de linkerope operand als de operand aan de linkerkant als null wordt `??=` geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-256">The null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="cf5dc-257">De `??=` operator evalueert de rechterope operand niet als de linkeropeen is geëvalueerd als niet-null.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-257">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
```

```Output
100
```

<span data-ttu-id="cf5dc-258">In het volgende voorbeeld wordt de rechteropeen niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-258">In the following example, the right-hand operand won't be evaluated.</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-conditional-operators--and-"></a><span data-ttu-id="cf5dc-259">Null-voorwaardelijke operators `?.` en `?[]`</span><span class="sxs-lookup"><span data-stu-id="cf5dc-259">Null-conditional operators `?.` and `?[]`</span></span>

> [!NOTE]
> <span data-ttu-id="cf5dc-260">Deze functie is verplaatst van experimenteel naar standaard in PowerShell 7.1.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-260">This feature was moved from experimental to mainstream in PowerShell 7.1.</span></span>

<span data-ttu-id="cf5dc-261">Een null-voorwaardelijke operator past een bewerking voor lidtoegang, , of elementtoegang, alleen toe op de operand als die operand als niet-null wordt geëvalueerd; anders wordt `?.` `?[]` null geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-261">A null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

<span data-ttu-id="cf5dc-262">Omdat PowerShell deel mag uitmaken van de naam van de variabele, is een formele specificatie van de naam van de variabele `?` vereist voor het gebruik van deze operators.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-262">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="cf5dc-263">Het is dus vereist om te gebruiken `{}` rond de namen van variabelen, zoals of wanneer deel uitmaakt van de `${a}` `?` variabelenaam `${a?}` .</span><span class="sxs-lookup"><span data-stu-id="cf5dc-263">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="cf5dc-264">In het volgende voorbeeld wordt de waarde **van PropName** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-264">In the following example, the value of **PropName** is returned.</span></span>

```powershell
$a = @{ PropName = 100 }
${a}?.PropName
```

```Output
100
```

<span data-ttu-id="cf5dc-265">In het volgende voorbeeld wordt null geretourneerd, zonder toegang te krijgen tot de **lidnaam PropName.**</span><span class="sxs-lookup"><span data-stu-id="cf5dc-265">The following example will return null, without trying to access the member name **PropName**.</span></span>

```powershell
$a = $null
${a}?.PropName
```

<span data-ttu-id="cf5dc-266">Op dezelfde manier wordt de waarde van het element geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-266">Similarly, the value of the element will be returned.</span></span>

```powershell
$a = 1..10
${a}?[0]
```

```Output
1
```

<span data-ttu-id="cf5dc-267">En wanneer de operand null is, wordt het element niet toegankelijk en wordt null geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-267">And when the operand is null, the element isn't accessed and null is returned.</span></span>

```PowerShell
$a = $null
${a}?[0]
```

> [!NOTE]
> <span data-ttu-id="cf5dc-268">Omdat PowerShell deel mag uitmaken van de naam van de variabele, is een formele specificatie van de naam van de variabele `?` vereist voor het gebruik van deze operators.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-268">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="cf5dc-269">Het is dus vereist om te gebruiken rond de namen van variabelen, zoals `{}` of wanneer deel uitmaakt van de `${a}` `?` variabelenaam `${a?}` .</span><span class="sxs-lookup"><span data-stu-id="cf5dc-269">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>
>
> <span data-ttu-id="cf5dc-270">De syntaxis van de `${<name>}` variabelenaam mag niet worden verward met de `$()` operator subexpressie.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-270">The variable name syntax of `${<name>}` should not be confused with the `$()` subexpression operator.</span></span> <span data-ttu-id="cf5dc-271">Zie voor meer informatie de sectie Variabelenaam van [about_Variables](about_Variables.md#variable-names-that-include-special-characters).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-271">For more information, see Variable name section of [about_Variables](about_Variables.md#variable-names-that-include-special-characters).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf5dc-272">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cf5dc-272">See also</span></span>

[<span data-ttu-id="cf5dc-273">about_Arithmetic_Operators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-273">about_Arithmetic_Operators</span></span>](about_Arithmetic_Operators.md)

[<span data-ttu-id="cf5dc-274">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-274">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="cf5dc-275">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-275">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="cf5dc-276">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-276">about_Logical_Operators</span></span>](about_logical_operators.md)

[<span data-ttu-id="cf5dc-277">about_Operator_Precedence</span><span class="sxs-lookup"><span data-stu-id="cf5dc-277">about_Operator_Precedence</span></span>](about_operator_precedence.md)

[<span data-ttu-id="cf5dc-278">about_Type_Operators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-278">about_Type_Operators</span></span>](about_Type_Operators.md)

[<span data-ttu-id="cf5dc-279">about_Pipeline_Chain_Operators</span><span class="sxs-lookup"><span data-stu-id="cf5dc-279">about_Pipeline_Chain_Operators</span></span>](about_Pipeline_Chain_Operators.md)

[<span data-ttu-id="cf5dc-280">about_Split</span><span class="sxs-lookup"><span data-stu-id="cf5dc-280">about_Split</span></span>](about_Split.md)

[<span data-ttu-id="cf5dc-281">about_Join</span><span class="sxs-lookup"><span data-stu-id="cf5dc-281">about_Join</span></span>](about_Join.md)

[<span data-ttu-id="cf5dc-282">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="cf5dc-282">about_Redirection</span></span>](about_Redirection.md)
