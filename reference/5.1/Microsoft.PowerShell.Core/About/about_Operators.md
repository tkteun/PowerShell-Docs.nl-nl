---
description: Beschrijft de operators die worden ondersteund door PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: fecf8808bb1b92a61359d327b5f87d045f913c09
ms.sourcegitcommit: 96efcc9613740449940b371b34c3baafb675b1ed
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2021
ms.locfileid: "107907359"
---
# <a name="about-operators"></a><span data-ttu-id="2667e-104">Over operators</span><span class="sxs-lookup"><span data-stu-id="2667e-104">About Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="2667e-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="2667e-105">Short description</span></span>
<span data-ttu-id="2667e-106">Beschrijft de operators die worden ondersteund door PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2667e-106">Describes the operators that are supported by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="2667e-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="2667e-107">Long description</span></span>

<span data-ttu-id="2667e-108">Een operator is een taalelement dat u kunt gebruiken in een opdracht of expressie.</span><span class="sxs-lookup"><span data-stu-id="2667e-108">An operator is a language element that you can use in a command or expression.</span></span>
<span data-ttu-id="2667e-109">PowerShell ondersteunt verschillende typen operators om waarden te bewerken.</span><span class="sxs-lookup"><span data-stu-id="2667e-109">PowerShell supports several types of operators to help you manipulate values.</span></span>

### <a name="arithmetic-operators"></a><span data-ttu-id="2667e-110">Rekenkundige operators</span><span class="sxs-lookup"><span data-stu-id="2667e-110">Arithmetic Operators</span></span>

<span data-ttu-id="2667e-111">Gebruik rekenkundige operators ( `+` , , , , , , ) om waarden in een opdracht of expressie te `-` `*` `/` `%` berekenen.</span><span class="sxs-lookup"><span data-stu-id="2667e-111">Use arithmetic operators (`+`, `-`, `*`, `/`, `%`) to calculate values in a command or expression.</span></span> <span data-ttu-id="2667e-112">Met deze operators kunt u waarden toevoegen, aftrekken, vermenigvuldigen of delen en de rest (modulus) van een delingsbewerking berekenen.</span><span class="sxs-lookup"><span data-stu-id="2667e-112">With these operators, you can add, subtract, multiply, or divide values, and calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="2667e-113">Met de optellingsoperator worden elementen samenvoegt.</span><span class="sxs-lookup"><span data-stu-id="2667e-113">The addition operator concatenates elements.</span></span> <span data-ttu-id="2667e-114">De vermenigvuldigingsoperator retourneert het opgegeven aantal kopieën van elk element.</span><span class="sxs-lookup"><span data-stu-id="2667e-114">The multiplication operator returns the specified number of copies of each element.</span></span> <span data-ttu-id="2667e-115">U kunt rekenkundige operators gebruiken voor elk .NET-type dat ze implementeert, zoals: `Int` , , , en `String` `DateTime` `Hashtable` Matrices.</span><span class="sxs-lookup"><span data-stu-id="2667e-115">You can use arithmetic operators on any .NET type that implements them, such as: `Int`, `String`, `DateTime`, `Hashtable`, and Arrays.</span></span>

<span data-ttu-id="2667e-116">Bitsgewijze operators ( `-band` , , , , , , , ) bewerken de `-bor` `-bxor` `-bnot` `-shl` `-shr` bitpatronen in waarden.</span><span class="sxs-lookup"><span data-stu-id="2667e-116">Bitwise operators (`-band`, `-bor`, `-bxor`, `-bnot`, `-shl`, `-shr`) manipulate the bit patterns in values.</span></span>

<span data-ttu-id="2667e-117">Zie voor meer informatie [about_Arithmetic_Operators.](about_Arithmetic_Operators.md)</span><span class="sxs-lookup"><span data-stu-id="2667e-117">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="assignment-operators"></a><span data-ttu-id="2667e-118">Toewijzingsoperators</span><span class="sxs-lookup"><span data-stu-id="2667e-118">Assignment Operators</span></span>

<span data-ttu-id="2667e-119">Gebruik toewijzingsoperators ( , , , , , , ) om waarden toe te wijzen, te wijzigen of toe te wijzen `=` `+=` aan `-=` `*=` `/=` `%=` variabelen.</span><span class="sxs-lookup"><span data-stu-id="2667e-119">Use assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `%=`) to assign, change, or append values to variables.</span></span> <span data-ttu-id="2667e-120">U kunt rekenkundige operators combineren met toewijzing om het resultaat van de rekenkundige bewerking toe te wijzen aan een variabele.</span><span class="sxs-lookup"><span data-stu-id="2667e-120">You can combine arithmetic operators with assignment to assign the result of the arithmetic operation to a variable.</span></span>

<span data-ttu-id="2667e-121">Zie voor meer informatie [about_Assignment_Operators](about_Assignment_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="2667e-121">For more information, see [about_Assignment_Operators](about_Assignment_Operators.md).</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="2667e-122">Vergelijkingsoperators</span><span class="sxs-lookup"><span data-stu-id="2667e-122">Comparison Operators</span></span>

<span data-ttu-id="2667e-123">Gebruik vergelijkingsoperators ( `-eq` , , , , , , ) om waarden en `-ne` `-gt` `-lt` `-le` `-ge` testvoorwaarden te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="2667e-123">Use comparison operators (`-eq`, `-ne`, `-gt`, `-lt`, `-le`, `-ge`) to compare values and test conditions.</span></span> <span data-ttu-id="2667e-124">U kunt bijvoorbeeld twee tekenreekswaarden vergelijken om te bepalen of ze gelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="2667e-124">For example, you can compare two string values to determine whether they are equal.</span></span>

<span data-ttu-id="2667e-125">De vergelijkingsoperators bevatten ook operators die patronen in tekst zoeken of vervangen.</span><span class="sxs-lookup"><span data-stu-id="2667e-125">The comparison operators also include operators that find or replace patterns in text.</span></span> <span data-ttu-id="2667e-126">De operators ( `-match` , , ) gebruiken reguliere `-notmatch` `-replace` expressies en ( , ) `-like` gebruiken `-notlike` jokertekens. `*`</span><span class="sxs-lookup"><span data-stu-id="2667e-126">The (`-match`, `-notmatch`, `-replace`) operators use regular expressions, and (`-like`, `-notlike`) use wildcards `*`.</span></span>

<span data-ttu-id="2667e-127">Vergelijkingsoperators voor insluitingen bepalen of een testwaarde wordt weergegeven in een referentieset ( `-in` `-notin` , , , `-contains` `-notcontains` ).</span><span class="sxs-lookup"><span data-stu-id="2667e-127">Containment comparison operators determine whether a test value appears in a reference set (`-in`, `-notin`, `-contains`, `-notcontains`).</span></span>

<span data-ttu-id="2667e-128">Typevergelijkingsoperators ( `-is` , ) bepalen of een object van een bepaald type `-isnot` is.</span><span class="sxs-lookup"><span data-stu-id="2667e-128">Type comparison operators (`-is`, `-isnot`) determine whether an object is of a given type.</span></span>

<span data-ttu-id="2667e-129">Zie voor meer informatie [about_Comparison_Operators](about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="2667e-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span>

### <a name="logical-operators"></a><span data-ttu-id="2667e-130">Logische operators</span><span class="sxs-lookup"><span data-stu-id="2667e-130">Logical Operators</span></span>

<span data-ttu-id="2667e-131">Gebruik logische operators ( , , , , , ) om voorwaardelijke instructies `-and` te verbinden met één complexe `-or` `-xor` `-not` `!` voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="2667e-131">Use logical operators (`-and`, `-or`, `-xor`, `-not`, `!`) to connect conditional statements into a single complex conditional.</span></span> <span data-ttu-id="2667e-132">U kunt bijvoorbeeld een logische operator gebruiken om een objectfilter met `-and` twee verschillende voorwaarden te maken.</span><span class="sxs-lookup"><span data-stu-id="2667e-132">For example, you can use a logical `-and` operator to create an object filter with two different conditions.</span></span>

<span data-ttu-id="2667e-133">Zie voor meer informatie [about_Logical_Operators](about_logical_operators.md).</span><span class="sxs-lookup"><span data-stu-id="2667e-133">For more information, see [about_Logical_Operators](about_logical_operators.md).</span></span>

### <a name="redirection-operators"></a><span data-ttu-id="2667e-134">Omleidingsoperators</span><span class="sxs-lookup"><span data-stu-id="2667e-134">Redirection Operators</span></span>

<span data-ttu-id="2667e-135">Gebruik omleidingsoperators ( , , , , en ) om de uitvoer van een opdracht of expressie naar `>` `>>` een `2>` `2>>` `2>&1` tekstbestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="2667e-135">Use redirection operators (`>`, `>>`, `2>`, `2>>`, and `2>&1`) to send the output of a command or expression to a text file.</span></span> <span data-ttu-id="2667e-136">De omleidingsoperators werken als de cmdlet (zonder parameters), maar u kunt ook foutuitvoer `Out-File` omleiden naar opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="2667e-136">The redirection operators work like the `Out-File` cmdlet (without parameters) but they also let you redirect error output to specified files.</span></span> <span data-ttu-id="2667e-137">U kunt ook de `Tee-Object` cmdlet gebruiken om de uitvoer om te leiden.</span><span class="sxs-lookup"><span data-stu-id="2667e-137">You can also use the `Tee-Object` cmdlet to redirect output.</span></span>

<span data-ttu-id="2667e-138">Zie voor meer informatie [about_Redirection](about_Redirection.md)</span><span class="sxs-lookup"><span data-stu-id="2667e-138">For more information, see [about_Redirection](about_Redirection.md)</span></span>

### <a name="split-and-join-operators"></a><span data-ttu-id="2667e-139">Operators splitsen en lid worden</span><span class="sxs-lookup"><span data-stu-id="2667e-139">Split and Join Operators</span></span>

<span data-ttu-id="2667e-140">De `-split` operators en delen en combineren `-join` subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="2667e-140">The `-split` and `-join` operators divide and combine substrings.</span></span> <span data-ttu-id="2667e-141">De `-split` operator splitst een tekenreeks in subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="2667e-141">The `-split` operator splits a string into substrings.</span></span> <span data-ttu-id="2667e-142">Met `-join` de operator worden meerdere tekenreeksen in één tekenreeks samenvoegd.</span><span class="sxs-lookup"><span data-stu-id="2667e-142">The `-join` operator concatenates multiple strings into a single string.</span></span>

<span data-ttu-id="2667e-143">Zie voor meer informatie [about_Split](about_Split.md) en [about_Join](about_Join.md).</span><span class="sxs-lookup"><span data-stu-id="2667e-143">For more information, see [about_Split](about_Split.md) and [about_Join](about_Join.md).</span></span>

### <a name="type-operators"></a><span data-ttu-id="2667e-144">Typeoperators</span><span class="sxs-lookup"><span data-stu-id="2667e-144">Type Operators</span></span>

<span data-ttu-id="2667e-145">Gebruik de typeoperators ( , , ) om het type .NET Framework `-is` object te zoeken of te `-isnot` `-as` wijzigen.</span><span class="sxs-lookup"><span data-stu-id="2667e-145">Use the type operators (`-is`, `-isnot`, `-as`) to find or change the .NET Framework type of an object.</span></span>

<span data-ttu-id="2667e-146">Zie voor meer informatie [about_Type_Operators](about_Type_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="2667e-146">For more information, see [about_Type_Operators](about_Type_Operators.md).</span></span>

### <a name="unary-operators"></a><span data-ttu-id="2667e-147">Unaire operators</span><span class="sxs-lookup"><span data-stu-id="2667e-147">Unary Operators</span></span>

<span data-ttu-id="2667e-148">Gebruik de unaire operators en om waarden te verhogen `++` `--` of te degraderen en `-` voor negatie.</span><span class="sxs-lookup"><span data-stu-id="2667e-148">Use the unary `++`  and `--` operators to increment or decrement values and `-` for negation.</span></span> <span data-ttu-id="2667e-149">Als u bijvoorbeeld de variabele wilt verhogen `$a` van `9` naar , `10` typt u `$a++` .</span><span class="sxs-lookup"><span data-stu-id="2667e-149">For example, to increment the variable `$a` from `9` to `10`, you type `$a++`.</span></span>

<span data-ttu-id="2667e-150">Zie voor meer informatie [about_Arithmetic_Operators.](about_Arithmetic_Operators.md)</span><span class="sxs-lookup"><span data-stu-id="2667e-150">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="special-operators"></a><span data-ttu-id="2667e-151">Speciale operators</span><span class="sxs-lookup"><span data-stu-id="2667e-151">Special Operators</span></span>

<span data-ttu-id="2667e-152">Speciale operators hebben specifieke gebruiksgevallen die niet in een andere operatorgroep passen.</span><span class="sxs-lookup"><span data-stu-id="2667e-152">Special operators have specific use-cases that do not fit into any other operator group.</span></span> <span data-ttu-id="2667e-153">Met speciale operators kunt u bijvoorbeeld opdrachten uitvoeren, het gegevenstype van een waarde wijzigen of elementen ophalen uit een matrix.</span><span class="sxs-lookup"><span data-stu-id="2667e-153">For example, special operators allow you to run commands, change a value's data type, or retrieve elements from an array.</span></span>

#### <a name="grouping-operator--"></a><span data-ttu-id="2667e-154">Groeperingsoperator `( )`</span><span class="sxs-lookup"><span data-stu-id="2667e-154">Grouping operator `( )`</span></span>

<span data-ttu-id="2667e-155">Net als in andere talen dient `(...)` om de prioriteit van operatoren in expressies te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="2667e-155">As in other languages, `(...)` serves to override operator precedence in expressions.</span></span> <span data-ttu-id="2667e-156">Bijvoorbeeld: `(1 + 2) / 3`</span><span class="sxs-lookup"><span data-stu-id="2667e-156">For example: `(1 + 2) / 3`</span></span>

<span data-ttu-id="2667e-157">In PowerShell zijn er echter aanvullende gedragingen.</span><span class="sxs-lookup"><span data-stu-id="2667e-157">However, in PowerShell, there are additional behaviors.</span></span>

- <span data-ttu-id="2667e-158">`(...)` met kunt u de uitvoer van een opdracht _laten_ deelnemen aan een expressie.</span><span class="sxs-lookup"><span data-stu-id="2667e-158">`(...)` allows you to let output from a _command_ participate in an expression.</span></span> <span data-ttu-id="2667e-159">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2667e-159">For example:</span></span>

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- <span data-ttu-id="2667e-160">Wanneer een opdracht of expressie tussen haakjes wordt gebruikt als het eerste segment van een pijplijn, leidt dat altijd tot een _enumeratie_ van het resultaat van de expressie.</span><span class="sxs-lookup"><span data-stu-id="2667e-160">When used as the first segment of a pipeline, wrapping a command or expression in parentheses invariably causes _enumeration_ of the expression result.</span></span> <span data-ttu-id="2667e-161">Als de haakjes een opdracht _verpakken,_ wordt deze uitgevoerd tot voltooiing met alle uitvoer die _in_ het geheugen is verzameld voordat de resultaten via de pijplijn worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="2667e-161">If the parentheses wrap a _command_, it is run to completion with all output _collected in memory_ before the results are sent through the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="2667e-162">Wanneer u een opdracht tussen haakjes verpakt, wordt de automatische variabele ingesteld op , zelfs wanneer de ingesloten `$?` opdracht zelf is ingesteld op `$true` `$?` `$false` .</span><span class="sxs-lookup"><span data-stu-id="2667e-162">Wrapping a command in parentheses causes the automatic variable `$?` to be set to `$true`, even when the enclosed command itself set `$?` to `$false`.</span></span>
> <span data-ttu-id="2667e-163">Onverwacht levert `(Get-Item /Nosuch); $?` bijvoorbeeld Waar **op.**</span><span class="sxs-lookup"><span data-stu-id="2667e-163">For example, `(Get-Item /Nosuch); $?` unexpectedly yields **True**.</span></span> <span data-ttu-id="2667e-164">Zie voor meer informatie `$?` [over about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="2667e-164">For more information about `$?`, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

#### <a name="subexpression-operator--"></a><span data-ttu-id="2667e-165">Subexpressieoperator `$( )`</span><span class="sxs-lookup"><span data-stu-id="2667e-165">Subexpression operator `$( )`</span></span>

<span data-ttu-id="2667e-166">Retourneert het resultaat van een of meer instructies.</span><span class="sxs-lookup"><span data-stu-id="2667e-166">Returns the result of one or more statements.</span></span> <span data-ttu-id="2667e-167">Retourneert een scalaire waarde voor één resultaat.</span><span class="sxs-lookup"><span data-stu-id="2667e-167">For a single result, returns a scalar.</span></span> <span data-ttu-id="2667e-168">Retourneert een matrix voor meerdere resultaten.</span><span class="sxs-lookup"><span data-stu-id="2667e-168">For multiple results, returns an array.</span></span> <span data-ttu-id="2667e-169">Gebruik dit als u een expressie binnen een andere expressie wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2667e-169">Use this when you want to use an expression within another expression.</span></span> <span data-ttu-id="2667e-170">Als u bijvoorbeeld de resultaten van de opdracht wilt insluiten in een tekenreeksexpressie.</span><span class="sxs-lookup"><span data-stu-id="2667e-170">For example, to embed the results of command in a string expression.</span></span>

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a><span data-ttu-id="2667e-171">Operator voor matrixsubexpressie `@( )`</span><span class="sxs-lookup"><span data-stu-id="2667e-171">Array subexpression operator `@( )`</span></span>

<span data-ttu-id="2667e-172">Retourneert het resultaat van een of meer instructies als een matrix.</span><span class="sxs-lookup"><span data-stu-id="2667e-172">Returns the result of one or more statements as an array.</span></span> <span data-ttu-id="2667e-173">Als er slechts één item is, heeft de matrix slechts één lid.</span><span class="sxs-lookup"><span data-stu-id="2667e-173">If there is only one item, the array has only one member.</span></span>

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="hash-table-literal-syntax-"></a><span data-ttu-id="2667e-174">Letterlijke syntaxis van hash-tabel `@{}`</span><span class="sxs-lookup"><span data-stu-id="2667e-174">Hash table literal syntax `@{}`</span></span>

<span data-ttu-id="2667e-175">Net als bij de matrixsubexpressie wordt deze syntaxis gebruikt om een hash-tabel te declaren.</span><span class="sxs-lookup"><span data-stu-id="2667e-175">Similar to the array subexpression, this syntax is used to declare a hash table.</span></span>
<span data-ttu-id="2667e-176">Zie voor meer informatie [about_Hash_Tables](about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="2667e-176">For more information, see [about_Hash_Tables](about_Hash_Tables.md).</span></span>

#### <a name="call-operator-"></a><span data-ttu-id="2667e-177">Operator voor aanroepen `&`</span><span class="sxs-lookup"><span data-stu-id="2667e-177">Call operator `&`</span></span>

<span data-ttu-id="2667e-178">Voert een opdracht, script of scriptblok uit.</span><span class="sxs-lookup"><span data-stu-id="2667e-178">Runs a command, script, or script block.</span></span> <span data-ttu-id="2667e-179">Met de aanroepoperator, ook wel de aanroepoperator genoemd, kunt u opdrachten uitvoeren die zijn opgeslagen in variabelen en worden vertegenwoordigd door tekenreeksen of scriptblokken.</span><span class="sxs-lookup"><span data-stu-id="2667e-179">The call operator, also known as the "invocation operator", lets you run commands that are stored in variables and represented by strings or script blocks.</span></span> <span data-ttu-id="2667e-180">De aanroepoperator wordt uitgevoerd in een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="2667e-180">The call operator executes in a child scope.</span></span> <span data-ttu-id="2667e-181">Zie voor meer informatie over [about_Scopes.](about_Scopes.md)</span><span class="sxs-lookup"><span data-stu-id="2667e-181">For more about scopes, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="2667e-182">In dit voorbeeld slaat u een opdracht op in een tekenreeks en voert u deze uit met behulp van de aanroepoperator.</span><span class="sxs-lookup"><span data-stu-id="2667e-182">This example stores a command in a string and executes it using the call operator.</span></span>

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

<span data-ttu-id="2667e-183">De aanroepoperator parseert geen tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="2667e-183">The call operator does not parse strings.</span></span> <span data-ttu-id="2667e-184">Dit betekent dat u geen opdrachtparameters binnen een tekenreeks kunt gebruiken wanneer u de aanroepoperator gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2667e-184">This means that you cannot use command parameters within a string when you use the call operator.</span></span>

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
At line:1 char:2
+ & $c
+  ~~
    + CategoryInfo          : ObjectNotFound: (Get-Service -Name Spooler:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="2667e-185">De [invoke-expression-cmdlet](xref:Microsoft.PowerShell.Utility.Invoke-Expression) kan code uitvoeren die parseringsfouten veroorzaakt bij het gebruik van de aanroepoperator.</span><span class="sxs-lookup"><span data-stu-id="2667e-185">The [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) cmdlet can execute code that causes parsing errors when using the call operator.</span></span>

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

<span data-ttu-id="2667e-186">U kunt de aanroepoperator gebruiken om scripts uit te voeren met hun bestandsnamen.</span><span class="sxs-lookup"><span data-stu-id="2667e-186">You can use the call operator to execute scripts using their filenames.</span></span> <span data-ttu-id="2667e-187">In het onderstaande voorbeeld ziet u een scriptbestandsnaam die spaties bevat.</span><span class="sxs-lookup"><span data-stu-id="2667e-187">The example below shows a script filename that contains spaces.</span></span> <span data-ttu-id="2667e-188">Wanneer u het script probeert uit te voeren, geeft PowerShell in plaats daarvan de inhoud weer van de tekenreeks met de bestandsnaam.</span><span class="sxs-lookup"><span data-stu-id="2667e-188">When you try to execute the script, PowerShell instead displays the contents of the quoted string containing the filename.</span></span> <span data-ttu-id="2667e-189">Met de aanroepoperator kunt u de inhoud van de tekenreeks met de bestandsnaam uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="2667e-189">The call operator allows you to execute the contents of the string containing the filename.</span></span>

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

<span data-ttu-id="2667e-190">Zie voor meer informatie over scriptblokken [about_Script_Blocks.](about_Script_Blocks.md)</span><span class="sxs-lookup"><span data-stu-id="2667e-190">For more about script blocks, see [about_Script_Blocks](about_Script_Blocks.md).</span></span>

#### <a name="cast-operator--"></a><span data-ttu-id="2667e-191">Cast-operator `[ ]`</span><span class="sxs-lookup"><span data-stu-id="2667e-191">Cast operator `[ ]`</span></span>

<span data-ttu-id="2667e-192">Converteert of beperkt objecten naar het opgegeven type.</span><span class="sxs-lookup"><span data-stu-id="2667e-192">Converts or limits objects to the specified type.</span></span> <span data-ttu-id="2667e-193">Als de objecten niet kunnen worden geconverteerd, genereert PowerShell een fout.</span><span class="sxs-lookup"><span data-stu-id="2667e-193">If the objects cannot be converted, PowerShell generates an error.</span></span>

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

<span data-ttu-id="2667e-194">Een cast-cast kan ook worden uitgevoerd wanneer een variabele wordt toegewezen aan met behulp van [cast-notatie](about_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="2667e-194">A cast can also be performed when a variable is assigned to using [cast notation](about_Variables.md).</span></span>

#### <a name="comma-operator-"></a><span data-ttu-id="2667e-195">Kommaoperator `,`</span><span class="sxs-lookup"><span data-stu-id="2667e-195">Comma operator `,`</span></span>

<span data-ttu-id="2667e-196">Als binaire operator maakt de komma een matrix of wordt deze aan de matrix die wordt gemaakt, aan de matrix die wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="2667e-196">As a binary operator, the comma creates an array or appends to the array being created.</span></span> <span data-ttu-id="2667e-197">In de expressiemodus maakt de komma als unaire operator een matrix met slechts één lid.</span><span class="sxs-lookup"><span data-stu-id="2667e-197">In expression mode, as a unary operator, the comma creates an array with just one member.</span></span> <span data-ttu-id="2667e-198">Plaats de komma vóór het lid.</span><span class="sxs-lookup"><span data-stu-id="2667e-198">Place the comma before the member.</span></span>

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

<span data-ttu-id="2667e-199">Omdat `Write-Object` een argument verwacht, moet u de expressie tussen haakjes zetten.</span><span class="sxs-lookup"><span data-stu-id="2667e-199">Since `Write-Object` expects an argument, you must put the expression in parentheses.</span></span>

#### <a name="dot-sourcing-operator-"></a><span data-ttu-id="2667e-200">Operator voor puntsourcing `.`</span><span class="sxs-lookup"><span data-stu-id="2667e-200">Dot sourcing operator `.`</span></span>

<span data-ttu-id="2667e-201">Voert een script uit in het huidige bereik, zodat alle functies, aliassen en variabelen die door het script worden gemaakt, worden toegevoegd aan het huidige bereik, waardoor bestaande functies, aliassen en variabelen worden overschrijven.</span><span class="sxs-lookup"><span data-stu-id="2667e-201">Runs a script in the current scope so that any functions, aliases, and variables that the script creates are added to the current scope, overriding existing ones.</span></span> <span data-ttu-id="2667e-202">Parameters die door het script zijn gedeclareerd, worden variabelen.</span><span class="sxs-lookup"><span data-stu-id="2667e-202">Parameters declared by the script become variables.</span></span> <span data-ttu-id="2667e-203">Parameters waarvoor geen waarde is gegeven, worden variabelen zonder waarde.</span><span class="sxs-lookup"><span data-stu-id="2667e-203">Parameters for which no value has been given become variables with no value.</span></span> <span data-ttu-id="2667e-204">De automatische variabele `$args` blijft echter behouden.</span><span class="sxs-lookup"><span data-stu-id="2667e-204">However, the automatic variable `$args` is preserved.</span></span>

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> <span data-ttu-id="2667e-205">De operator voor puntsourcing wordt gevolgd door een spatie.</span><span class="sxs-lookup"><span data-stu-id="2667e-205">The dot sourcing operator is followed by a space.</span></span> <span data-ttu-id="2667e-206">Gebruik de spatie om de punt te onderscheiden van het punt ( `.` ) symbool dat de huidige map vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="2667e-206">Use the space to distinguish the dot from the dot (`.`) symbol that represents the current directory.</span></span>
>
> <span data-ttu-id="2667e-207">In het volgende voorbeeld wordt het Sample.ps1 script in de huidige map uitgevoerd in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="2667e-207">In the following example, the Sample.ps1 script in the current directory is run in the current scope.</span></span>
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a><span data-ttu-id="2667e-208">Opmaakoperator `-f`</span><span class="sxs-lookup"><span data-stu-id="2667e-208">Format operator `-f`</span></span>

<span data-ttu-id="2667e-209">Maakt tekenreeksen op met behulp van de indelingsmethode van tekenreeksobjecten.</span><span class="sxs-lookup"><span data-stu-id="2667e-209">Formats strings by using the format method of string objects.</span></span> <span data-ttu-id="2667e-210">Voer de notatiereeks aan de linkerkant van de operator en de objecten in die aan de rechterkant van de operator moeten worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="2667e-210">Enter the format string on the left side of the operator and the objects to be formatted on the right side of the operator.</span></span>

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

<span data-ttu-id="2667e-211">Als u de accolades ( ) in de opgemaakte tekenreeks wilt houden, kunt u deze escapen door de `{}` accolades te verdubbelen.</span><span class="sxs-lookup"><span data-stu-id="2667e-211">If you need to keep the curly braces (`{}`) in the formatted string, you can escape them by doubling the curly braces.</span></span>

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

<span data-ttu-id="2667e-212">Zie de methode [String.Format en](/dotnet/api/system.string.format) Samengestelde opmaak [voor meer informatie.](/dotnet/standard/base-types/composite-formatting)</span><span class="sxs-lookup"><span data-stu-id="2667e-212">For more information, see the [String.Format](/dotnet/api/system.string.format) method and [Composite Formatting](/dotnet/standard/base-types/composite-formatting).</span></span>

#### <a name="index-operator--"></a><span data-ttu-id="2667e-213">Indexoperator `[ ]`</span><span class="sxs-lookup"><span data-stu-id="2667e-213">Index operator `[ ]`</span></span>

<span data-ttu-id="2667e-214">Selecteert objecten uit geïndexeerde verzamelingen, zoals matrices en hashtabellen.</span><span class="sxs-lookup"><span data-stu-id="2667e-214">Selects objects from indexed collections, such as arrays and hash tables.</span></span> <span data-ttu-id="2667e-215">Matrixindexen zijn op nul gebaseerd, dus het eerste object wordt geïndexeerd als `[0]` .</span><span class="sxs-lookup"><span data-stu-id="2667e-215">Array indexes are zero-based, so the first object is indexed as `[0]`.</span></span> <span data-ttu-id="2667e-216">Voor matrices (alleen) kunt u ook negatieve indexen gebruiken om de laatste waarden op te halen.</span><span class="sxs-lookup"><span data-stu-id="2667e-216">For arrays (only), you can also use negative indexes to get the last values.</span></span> <span data-ttu-id="2667e-217">Hashtabellen worden geïndexeerd op sleutelwaarde.</span><span class="sxs-lookup"><span data-stu-id="2667e-217">Hash tables are indexed by key value.</span></span>

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

#### <a name="pipeline-operator-"></a><span data-ttu-id="2667e-218">Pijplijnoperator `|`</span><span class="sxs-lookup"><span data-stu-id="2667e-218">Pipeline operator `|`</span></span>

<span data-ttu-id="2667e-219">Verzendt ("pipes") de uitvoer van de opdracht die voorafgaat aan de opdracht die volgt.</span><span class="sxs-lookup"><span data-stu-id="2667e-219">Sends ("pipes") the output of the command that precedes it to the command that follows it.</span></span> <span data-ttu-id="2667e-220">Wanneer de uitvoer meer dan één object (een verzameling) bevat, verzendt de pijplijnoperator de objecten één voor één.</span><span class="sxs-lookup"><span data-stu-id="2667e-220">When the output includes more than one object (a "collection"), the pipeline operator sends the objects one at a time.</span></span>

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="range-operator-"></a><span data-ttu-id="2667e-221">Bereikoperator `..`</span><span class="sxs-lookup"><span data-stu-id="2667e-221">Range operator `..`</span></span>

<span data-ttu-id="2667e-222">Vertegenwoordigt de sequentiële gehele getallen in een matrix met gehele getallen op een boven- en ondergrens.</span><span class="sxs-lookup"><span data-stu-id="2667e-222">Represents the sequential integers in an integer array, given an upper, and lower boundary.</span></span>

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

<span data-ttu-id="2667e-223">U kunt ook in omgekeerde volgorde reeksen maken.</span><span class="sxs-lookup"><span data-stu-id="2667e-223">You can also create ranges in reverse order.</span></span>

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

#### <a name="member-access-operator-"></a><span data-ttu-id="2667e-224">Operator voor lidtoegang `.`</span><span class="sxs-lookup"><span data-stu-id="2667e-224">Member access operator `.`</span></span>

<span data-ttu-id="2667e-225">Heeft toegang tot de eigenschappen en methoden van een object.</span><span class="sxs-lookup"><span data-stu-id="2667e-225">Accesses the properties and methods of an object.</span></span> <span data-ttu-id="2667e-226">De lidnaam kan een expressie zijn.</span><span class="sxs-lookup"><span data-stu-id="2667e-226">The member name may be an expression.</span></span>

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a><span data-ttu-id="2667e-227">Statische lidoperator `::`</span><span class="sxs-lookup"><span data-stu-id="2667e-227">Static member operator `::`</span></span>

<span data-ttu-id="2667e-228">Roept de statische eigenschappen en methoden van een .NET Framework klasse aan.</span><span class="sxs-lookup"><span data-stu-id="2667e-228">Calls the static properties and methods of a .NET Framework class.</span></span> <span data-ttu-id="2667e-229">Als u de statische eigenschappen en methoden van een object wilt vinden, gebruikt u de parameter Statisch van de `Get-Member` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="2667e-229">To find the static properties and methods of an object, use the Static parameter of the `Get-Member` cmdlet.</span></span>  <span data-ttu-id="2667e-230">De naam van het lid kan een expressie zijn.</span><span class="sxs-lookup"><span data-stu-id="2667e-230">The member name may be an expression.</span></span>

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

## <a name="see-also"></a><span data-ttu-id="2667e-231">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2667e-231">See also</span></span>

[<span data-ttu-id="2667e-232">about_Arithmetic_Operators</span><span class="sxs-lookup"><span data-stu-id="2667e-232">about_Arithmetic_Operators</span></span>](about_Arithmetic_Operators.md)

[<span data-ttu-id="2667e-233">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="2667e-233">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="2667e-234">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="2667e-234">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="2667e-235">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="2667e-235">about_Logical_Operators</span></span>](about_logical_operators.md)

[<span data-ttu-id="2667e-236">about_Operator_Precedence</span><span class="sxs-lookup"><span data-stu-id="2667e-236">about_Operator_Precedence</span></span>](about_operator_precedence.md)

[<span data-ttu-id="2667e-237">about_Type_Operators</span><span class="sxs-lookup"><span data-stu-id="2667e-237">about_Type_Operators</span></span>](about_Type_Operators.md)

[<span data-ttu-id="2667e-238">about_Split</span><span class="sxs-lookup"><span data-stu-id="2667e-238">about_Split</span></span>](about_Split.md)

[<span data-ttu-id="2667e-239">about_Join</span><span class="sxs-lookup"><span data-stu-id="2667e-239">about_Join</span></span>](about_Join.md)

[<span data-ttu-id="2667e-240">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="2667e-240">about_Redirection</span></span>](about_Redirection.md)
