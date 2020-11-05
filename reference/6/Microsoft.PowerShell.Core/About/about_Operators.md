---
description: Hierin worden de Opera tors beschreven die worden ondersteund door Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: 9668e635b17f8cbe9f6639e8a13b95d4b9387fbb
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/29/2020
ms.locfileid: "93253256"
---
# <a name="about-operators"></a><span data-ttu-id="4b5c4-104">Opera tors</span><span class="sxs-lookup"><span data-stu-id="4b5c4-104">About Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="4b5c4-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="4b5c4-105">Short description</span></span>
<span data-ttu-id="4b5c4-106">Hierin worden de Opera tors beschreven die worden ondersteund door Power shell.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-106">Describes the operators that are supported by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4b5c4-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="4b5c4-107">Long description</span></span>

<span data-ttu-id="4b5c4-108">Een operator is een taal element dat u kunt gebruiken in een opdracht of expressie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-108">An operator is a language element that you can use in a command or expression.</span></span>
<span data-ttu-id="4b5c4-109">Power shell ondersteunt diverse typen Opera tors die u helpen bij het manipuleren van waarden.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-109">PowerShell supports several types of operators to help you manipulate values.</span></span>

### <a name="arithmetic-operators"></a><span data-ttu-id="4b5c4-110">Rekenkundige operators</span><span class="sxs-lookup"><span data-stu-id="4b5c4-110">Arithmetic Operators</span></span>

<span data-ttu-id="4b5c4-111">Reken kundige Opera tors ( `+` ,, `-` `*` , `/` ) gebruiken `%` om waarden in een opdracht of expressie te berekenen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-111">Use arithmetic operators (`+`, `-`, `*`, `/`, `%`) to calculate values in a command or expression.</span></span> <span data-ttu-id="4b5c4-112">Met deze opera tors kunt u waarden toevoegen, aftrekken, vermenigvuldigen of delen, en de rest (modulus) van een delings bewerking berekenen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-112">With these operators, you can add, subtract, multiply, or divide values, and calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="4b5c4-113">De operator voor optellen voegt elementen samen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-113">The addition operator concatenates elements.</span></span> <span data-ttu-id="4b5c4-114">De operator voor vermenigvuldigen retourneert het opgegeven aantal exemplaren van elk element.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-114">The multiplication operator returns the specified number of copies of each element.</span></span> <span data-ttu-id="4b5c4-115">U kunt reken kundige Opera tors gebruiken voor elk .net-type dat deze implementeert, zoals: `Int` ,, `String` `DateTime` , `Hashtable` en arrays.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-115">You can use arithmetic operators on any .NET type that implements them, such as: `Int`, `String`, `DateTime`, `Hashtable`, and Arrays.</span></span>

<span data-ttu-id="4b5c4-116">Bitsgewijze Opera tors ( `-band` , `-bor` ,,, `-bxor` `-bnot` `-shl` , `-shr` ) bewerken de bits patronen in waarden.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-116">Bitwise operators (`-band`, `-bor`, `-bxor`, `-bnot`, `-shl`, `-shr`) manipulate the bit patterns in values.</span></span>

<span data-ttu-id="4b5c4-117">Zie [about_Arithmetic_Operators](about_Arithmetic_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-117">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="assignment-operators"></a><span data-ttu-id="4b5c4-118">Toewijzings operatoren</span><span class="sxs-lookup"><span data-stu-id="4b5c4-118">Assignment Operators</span></span>

<span data-ttu-id="4b5c4-119">Gebruik toewijzings operatoren (,,,, `=` `+=` `-=` `*=` `/=` , `%=` ) om waarden toe te wijzen, te wijzigen of toe te voegen aan variabelen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-119">Use assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `%=`) to assign, change, or append values to variables.</span></span> <span data-ttu-id="4b5c4-120">U kunt reken kundige Opera tors combi neren met toewijzing om het resultaat van de reken kundige bewerking aan een variabele toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-120">You can combine arithmetic operators with assignment to assign the result of the arithmetic operation to a variable.</span></span>

<span data-ttu-id="4b5c4-121">Zie [about_Assignment_Operators](about_Assignment_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-121">For more information, see [about_Assignment_Operators](about_Assignment_Operators.md).</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="4b5c4-122">Vergelijkingsoperators</span><span class="sxs-lookup"><span data-stu-id="4b5c4-122">Comparison Operators</span></span>

<span data-ttu-id="4b5c4-123">Gebruik vergelijkings operatoren ( `-eq` ,, `-ne` `-gt` , `-lt` , `-le` , `-ge` ) om waarden en test voorwaarden te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-123">Use comparison operators (`-eq`, `-ne`, `-gt`, `-lt`, `-le`, `-ge`) to compare values and test conditions.</span></span> <span data-ttu-id="4b5c4-124">U kunt bijvoorbeeld twee teken reeks waarden vergelijken om te bepalen of ze gelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-124">For example, you can compare two string values to determine whether they are equal.</span></span>

<span data-ttu-id="4b5c4-125">De vergelijkings operators omvatten ook Opera tors waarmee patronen in tekst worden gezocht of vervangen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-125">The comparison operators also include operators that find or replace patterns in text.</span></span> <span data-ttu-id="4b5c4-126">De `-match` `-notmatch` Opera tors (,, `-replace` ) gebruiken reguliere expressies en `-like` `-notlike` gebruiken joker tekens `*` .</span><span class="sxs-lookup"><span data-stu-id="4b5c4-126">The (`-match`, `-notmatch`, `-replace`) operators use regular expressions, and (`-like`, `-notlike`) use wildcards `*`.</span></span>

<span data-ttu-id="4b5c4-127">Containment-vergelijkings operatoren bepalen of een test waarde wordt weer gegeven in een referentieset ( `-in` ,, `-notin` `-contains` , `-notcontains` ).</span><span class="sxs-lookup"><span data-stu-id="4b5c4-127">Containment comparison operators determine whether a test value appears in a reference set (`-in`, `-notin`, `-contains`, `-notcontains`).</span></span>

<span data-ttu-id="4b5c4-128">Type vergelijkings operatoren ( `-is` , `-isnot` ) bepalen of een object van een bepaald type is.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-128">Type comparison operators (`-is`, `-isnot`) determine whether an object is of a given type.</span></span>

<span data-ttu-id="4b5c4-129">Zie [about_Comparison_Operators](about_Comparison_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span>

### <a name="logical-operators"></a><span data-ttu-id="4b5c4-130">Logische operators</span><span class="sxs-lookup"><span data-stu-id="4b5c4-130">Logical Operators</span></span>

<span data-ttu-id="4b5c4-131">Gebruik logische Opera tors (,,, `-and` `-or` `-xor` `-not` , `!` ) om voorwaardelijke instructies te verbinden met één complexe voorwaardelijke waarde.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-131">Use logical operators (`-and`, `-or`, `-xor`, `-not`, `!`) to connect conditional statements into a single complex conditional.</span></span> <span data-ttu-id="4b5c4-132">U kunt bijvoorbeeld een logische `-and` operator gebruiken om een object filter te maken met twee verschillende voor waarden.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-132">For example, you can use a logical `-and` operator to create an object filter with two different conditions.</span></span>

<span data-ttu-id="4b5c4-133">Zie [about_Logical_Operators](about_logical_operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-133">For more information, see [about_Logical_Operators](about_logical_operators.md).</span></span>

### <a name="redirection-operators"></a><span data-ttu-id="4b5c4-134">Omleidings operatoren</span><span class="sxs-lookup"><span data-stu-id="4b5c4-134">Redirection Operators</span></span>

<span data-ttu-id="4b5c4-135">Gebruik de omleidings operatoren ( `>` ,, `>>` `2>` , `2>>` en `2>&1` ) om de uitvoer van een opdracht of expressie naar een tekst bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-135">Use redirection operators (`>`, `>>`, `2>`, `2>>`, and `2>&1`) to send the output of a command or expression to a text file.</span></span> <span data-ttu-id="4b5c4-136">De omleidings operatoren werken zoals de `Out-File` cmdlet (zonder para meters), maar u kunt ook de fout uitvoer omleiden naar opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-136">The redirection operators work like the `Out-File` cmdlet (without parameters) but they also let you redirect error output to specified files.</span></span> <span data-ttu-id="4b5c4-137">U kunt ook de- `Tee-Object` cmdlet gebruiken om uitvoer om te leiden.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-137">You can also use the `Tee-Object` cmdlet to redirect output.</span></span>

<span data-ttu-id="4b5c4-138">Zie [about_Redirection](about_Redirection.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-138">For more information, see [about_Redirection](about_Redirection.md)</span></span>

### <a name="split-and-join-operators"></a><span data-ttu-id="4b5c4-139">Opera tors voor splitsen en samen voegen</span><span class="sxs-lookup"><span data-stu-id="4b5c4-139">Split and Join Operators</span></span>

<span data-ttu-id="4b5c4-140">De `-split` `-join` Opera tors en delen subtekenreeksen en combi neren deze.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-140">The `-split` and `-join` operators divide and combine substrings.</span></span> <span data-ttu-id="4b5c4-141">De `-split` operator splitst een teken reeks in subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-141">The `-split` operator splits a string into substrings.</span></span> <span data-ttu-id="4b5c4-142">De `-join` operator voegt meerdere teken reeksen samen tot één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-142">The `-join` operator concatenates multiple strings into a single string.</span></span>

<span data-ttu-id="4b5c4-143">Zie [about_Split](about_Split.md) en [about_Join](about_Join.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-143">For more information, see [about_Split](about_Split.md) and [about_Join](about_Join.md).</span></span>

### <a name="type-operators"></a><span data-ttu-id="4b5c4-144">Type operators</span><span class="sxs-lookup"><span data-stu-id="4b5c4-144">Type Operators</span></span>

<span data-ttu-id="4b5c4-145">Gebruik de type operators ( `-is` , `-isnot` , `-as` ) om het .NET Framework type van een object te zoeken of te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-145">Use the type operators (`-is`, `-isnot`, `-as`) to find or change the .NET Framework type of an object.</span></span>

<span data-ttu-id="4b5c4-146">Zie [about_Type_Operators](about_Type_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-146">For more information, see [about_Type_Operators](about_Type_Operators.md).</span></span>

### <a name="unary-operators"></a><span data-ttu-id="4b5c4-147">Unaire Opera tors</span><span class="sxs-lookup"><span data-stu-id="4b5c4-147">Unary Operators</span></span>

<span data-ttu-id="4b5c4-148">Gebruik unaire Opera tors om variabelen of object eigenschappen te verhogen of verlagen en om integers in te stellen op positieve of negatieve getallen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-148">Use unary operators to increment or decrement variables or object properties and to set integers to positive or negative numbers.</span></span> <span data-ttu-id="4b5c4-149">Als u bijvoorbeeld de variabele wilt verhogen `$a` van `9` naar `10` , typt u `$a++` .</span><span class="sxs-lookup"><span data-stu-id="4b5c4-149">For example, to increment the variable `$a` from `9` to `10`, you type `$a++`.</span></span>

### <a name="special-operators"></a><span data-ttu-id="4b5c4-150">Speciale Opera tors</span><span class="sxs-lookup"><span data-stu-id="4b5c4-150">Special Operators</span></span>

<span data-ttu-id="4b5c4-151">Speciale Opera tors hebben specifieke use-cases die niet in een andere operator groep passen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-151">Special operators have specific use-cases that do not fit into any other operator group.</span></span> <span data-ttu-id="4b5c4-152">Speciale Opera tors maken het bijvoorbeeld mogelijk om opdrachten uit te voeren, het gegevens type van een waarde te wijzigen of elementen uit een matrix op te halen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-152">For example, special operators allow you to run commands, change a value's data type, or retrieve elements from an array.</span></span>

#### <a name="grouping-operator--"></a><span data-ttu-id="4b5c4-153">Operator voor groeperen `( )`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-153">Grouping operator `( )`</span></span>

<span data-ttu-id="4b5c4-154">Net als in andere talen `(...)` moet de operator prioriteit in expressies worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-154">As in other languages, `(...)` serves to override operator precedence in expressions.</span></span> <span data-ttu-id="4b5c4-155">Bijvoorbeeld: `(1 + 2) / 3`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-155">For example: `(1 + 2) / 3`</span></span>

<span data-ttu-id="4b5c4-156">Er zijn echter extra problemen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-156">However, in PowerShell, there are additional behaviors.</span></span>

- <span data-ttu-id="4b5c4-157">`(...)` met kunt u de uitvoer van een _opdracht_ laten deel uitmaken van een expressie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-157">`(...)` allows you to let output from a _command_ participate in an expression.</span></span> <span data-ttu-id="4b5c4-158">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="4b5c4-158">For example:</span></span>

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- <span data-ttu-id="4b5c4-159">Wanneer u gebruikt als het eerste segment van een pijp lijn, verpakt u een opdracht of expressie tussen haakjes invariably resulteert in de _opsomming_ van het resultaat van de expressie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-159">When used as the first segment of a pipeline, wrapping a command or expression in parentheses invariably causes _enumeration_ of the expression result.</span></span> <span data-ttu-id="4b5c4-160">Als de haakjes een _opdracht_ teruglopen, wordt deze uitgevoerd om te volt ooien met alle uitvoer die _in het geheugen is verzameld_ voordat de resultaten via de pijp lijn worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-160">If the parentheses wrap a _command_ , it is run to completion with all output _collected in memory_ before the results are sent through the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="4b5c4-161">Als u een opdracht tussen haakjes typt, wordt de automatische variabele `$?` ingesteld op `$true` , zelfs wanneer de Inge sloten opdracht zelf is ingesteld `$?` op `$false` .</span><span class="sxs-lookup"><span data-stu-id="4b5c4-161">Wrapping a command in parentheses causes the automatic variable `$?` to be set to `$true`, even when the enclosed command itself set `$?` to `$false`.</span></span>
> <span data-ttu-id="4b5c4-162">Zo wordt `(Get-Item /Nosuch); $?` onverwacht resultaat **geretourneerd**.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-162">For example, `(Get-Item /Nosuch); $?` unexpectedly yields **True**.</span></span> <span data-ttu-id="4b5c4-163">Zie about_Automatic_Variables voor meer informatie over `$?` . [about_Automatic_Variables](about_Automatic_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="4b5c4-163">For more information about `$?`, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

#### <a name="subexpression-operator--"></a><span data-ttu-id="4b5c4-164">Operator voor subexpressie `$( )`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-164">Subexpression operator `$( )`</span></span>

<span data-ttu-id="4b5c4-165">Retourneert het resultaat van een of meer instructies.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-165">Returns the result of one or more statements.</span></span> <span data-ttu-id="4b5c4-166">Voor één resultaat retourneert een scalaire waarde.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-166">For a single result, returns a scalar.</span></span> <span data-ttu-id="4b5c4-167">Voor meerdere resultaten wordt een matrix geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-167">For multiple results, returns an array.</span></span> <span data-ttu-id="4b5c4-168">Gebruik deze als u een expressie binnen een andere expressie wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-168">Use this when you want to use an expression within another expression.</span></span> <span data-ttu-id="4b5c4-169">Bijvoorbeeld, om de resultaten van de opdracht in een teken reeks expressie in te sluiten.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-169">For example, to embed the results of command in a string expression.</span></span>

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a><span data-ttu-id="4b5c4-170">Operator voor subexpressie van matrix `@( )`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-170">Array subexpression operator `@( )`</span></span>

<span data-ttu-id="4b5c4-171">Retourneert het resultaat van een of meer instructies als een matrix.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-171">Returns the result of one or more statements as an array.</span></span> <span data-ttu-id="4b5c4-172">Als er slechts één item is, heeft de matrix slechts één lid.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-172">If there is only one item, the array has only one member.</span></span>

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="call-operator-"></a><span data-ttu-id="4b5c4-173">Aanroep operator `&`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-173">Call operator `&`</span></span>

<span data-ttu-id="4b5c4-174">Voert een opdracht, script of script blok uit.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-174">Runs a command, script, or script block.</span></span> <span data-ttu-id="4b5c4-175">Met de oproep operator, ook wel bekend als aanroep operator, kunt u opdrachten uitvoeren die zijn opgeslagen in variabelen en vertegenwoordigd door teken reeksen of script blokken.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-175">The call operator, also known as the "invocation operator", lets you run commands that are stored in variables and represented by strings or script blocks.</span></span> <span data-ttu-id="4b5c4-176">De aanroep operator wordt uitgevoerd in een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-176">The call operator executes in a child scope.</span></span> <span data-ttu-id="4b5c4-177">Zie [about_Scopes](about_Scopes.md)voor meer informatie over bereiken.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-177">For more about scopes, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="4b5c4-178">In dit voor beeld wordt een opdracht in een teken reeks opgeslagen en uitgevoerd met de aanroep operator.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-178">This example stores a command in a string and executes it using the call operator.</span></span>

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

<span data-ttu-id="4b5c4-179">De aanroep operator parseert geen teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-179">The call operator does not parse strings.</span></span> <span data-ttu-id="4b5c4-180">Dit betekent dat u geen opdracht parameters binnen een teken reeks kunt gebruiken wanneer u de aanroep operator gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-180">This means that you cannot use command parameters within a string when you use the call operator.</span></span>

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

<span data-ttu-id="4b5c4-181">Met de cmdlet [invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) kan code worden uitgevoerd die fouten tijdens het parseren van de aanroep operator veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-181">The [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) cmdlet can execute code that causes parsing errors when using the call operator.</span></span>

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

<span data-ttu-id="4b5c4-182">U kunt de aanroep operator gebruiken om scripts uit te voeren met hun bestands namen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-182">You can use the call operator to execute scripts using their filenames.</span></span> <span data-ttu-id="4b5c4-183">In het onderstaande voor beeld ziet u een script bestandsnaam die spaties bevat.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-183">The example below shows a script filename that contains spaces.</span></span> <span data-ttu-id="4b5c4-184">Wanneer u het script probeert uit te voeren, geeft Power shell in plaats daarvan de inhoud weer van de teken reeks met de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-184">When you try to execute the script, PowerShell instead displays the contents of the quoted string containing the filename.</span></span> <span data-ttu-id="4b5c4-185">Met de aanroep operator kunt u de inhoud van de teken reeks met de bestands naam uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-185">The call operator allows you to execute the contents of the string containing the filename.</span></span>

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

<span data-ttu-id="4b5c4-186">Zie [about_Script_Blocks](about_Script_Blocks.md)voor meer informatie over script blokken.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-186">For more about script blocks, see [about_Script_Blocks](about_Script_Blocks.md).</span></span>

#### <a name="background-operator-"></a><span data-ttu-id="4b5c4-187">Operator voor achtergrond `&`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-187">Background operator `&`</span></span>

<span data-ttu-id="4b5c4-188">Voert de pijp lijn voordat deze op de achtergrond wordt uitgevoerd in een Power shell-taak.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-188">Runs the pipeline before it in the background, in a PowerShell job.</span></span> <span data-ttu-id="4b5c4-189">Deze operator werkt op dezelfde manier als de UNIX-besturings operator en-teken ( `&` ), waarbij de opdracht wordt uitgevoerd vóór asynchroon in subshell als een taak.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-189">This operator acts similarly to the UNIX control operator ampersand (`&`), which runs the command before it asynchronously in subshell as a job.</span></span>

<span data-ttu-id="4b5c4-190">Deze operator is functioneel gelijk aan `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="4b5c4-190">This operator is functionally equivalent to `Start-Job`.</span></span> <span data-ttu-id="4b5c4-191">In het volgende voor beeld wordt het basis gebruik van de taak operator achtergrond gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-191">The following example demonstrates basic usage of the background job operator.</span></span>

```powershell
Get-Process -Name pwsh &
```

<span data-ttu-id="4b5c4-192">Deze opdracht is functioneel gelijk aan het volgende gebruik van `Start-Job` :</span><span class="sxs-lookup"><span data-stu-id="4b5c4-192">That command is functionally equivalent to the following usage of `Start-Job`:</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

<span data-ttu-id="4b5c4-193">Net als `Start-Job` : de `&` operator background retourneert een- `Job` object.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-193">Just like `Start-Job`, the `&` background operator returns a `Job` object.</span></span> <span data-ttu-id="4b5c4-194">Dit object kan worden gebruikt met `Receive-Job` en `Remove-Job` , net alsof u hebt gebruikt `Start-Job` om de taak te starten.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-194">This object can be used with `Receive-Job` and `Remove-Job`, just as if you had used `Start-Job` to start the job.</span></span>

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

<span data-ttu-id="4b5c4-195">De `&` operator voor de achtergrond is ook een instructie-eind punt, net als bij de UNIX-besturings operator en-teken ( `&` ).</span><span class="sxs-lookup"><span data-stu-id="4b5c4-195">The `&` background operator is also a statement terminator, just like the UNIX control operator ampersand (`&`).</span></span> <span data-ttu-id="4b5c4-196">Hierdoor kunt u aanvullende opdrachten aanroepen na de `&` operator achtergrond.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-196">This allows you to invoke additional commands after the `&` background operator.</span></span> <span data-ttu-id="4b5c4-197">In het volgende voor beeld ziet u de aanroep van extra opdrachten na de `&` operator achtergrond.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-197">The following example demonstrates the invocation of additional commands after the `&` background operator.</span></span>

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

<span data-ttu-id="4b5c4-198">Dit komt overeen met het volgende script:</span><span class="sxs-lookup"><span data-stu-id="4b5c4-198">This is equivalent to the following script:</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

<span data-ttu-id="4b5c4-199">Als u meerdere opdrachten wilt uitvoeren, elk in een eigen achtergrond proces, maar op één regel, plaatst u gewoon `&` tussen en na elk van de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-199">If you want to run multiple commands, each in their own background process but all on one line, simply place `&` between and after each of the commands.</span></span>

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

<span data-ttu-id="4b5c4-200">Zie [about_Jobs](about_Jobs.md)voor meer informatie over Power shell-taken.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-200">For more information on PowerShell jobs, see [about_Jobs](about_Jobs.md).</span></span>

#### <a name="cast-operator--"></a><span data-ttu-id="4b5c4-201">Conversie operator `[ ]`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-201">Cast operator `[ ]`</span></span>

<span data-ttu-id="4b5c4-202">Hiermee worden objecten geconverteerd of beperkt tot het opgegeven type.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-202">Converts or limits objects to the specified type.</span></span> <span data-ttu-id="4b5c4-203">Als de objecten niet kunnen worden geconverteerd, wordt er door Power shell een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-203">If the objects cannot be converted, PowerShell generates an error.</span></span>

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

<span data-ttu-id="4b5c4-204">Een cast kan ook worden uitgevoerd wanneer een variabele is toegewezen aan met behulp van de [cast-notatie](about_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="4b5c4-204">A cast can also be performed when a variable is assigned to using [cast notation](about_Variables.md).</span></span>

#### <a name="comma-operator-"></a><span data-ttu-id="4b5c4-205">Komma operator `,`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-205">Comma operator `,`</span></span>

<span data-ttu-id="4b5c4-206">Als binaire operator maakt de komma een matrix of voegt deze toe aan de matrix die wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-206">As a binary operator, the comma creates an array or appends to the array being created.</span></span> <span data-ttu-id="4b5c4-207">In de expressie modus, als een unaire operator, maakt de komma een matrix met slechts één lid.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-207">In expression mode, as a unary operator, the comma creates an array with just one member.</span></span> <span data-ttu-id="4b5c4-208">Plaats de komma vóór het lid.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-208">Place the comma before the member.</span></span>

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

<span data-ttu-id="4b5c4-209">Omdat `Write-Object` een argument wordt verwacht, moet u de expressie tussen haakjes plaatsen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-209">Since `Write-Object` expects an argument, you must put the expression in parentheses.</span></span>

#### <a name="dot-sourcing-operator-"></a><span data-ttu-id="4b5c4-210">Operator voor punt sourcing `.`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-210">Dot sourcing operator `.`</span></span>

<span data-ttu-id="4b5c4-211">Voert een script uit in het huidige bereik, zodat alle functies, aliassen en variabelen die het script maakt, worden toegevoegd aan het huidige bereik en bestaande worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-211">Runs a script in the current scope so that any functions, aliases, and variables that the script creates are added to the current scope, overriding existing ones.</span></span> <span data-ttu-id="4b5c4-212">De door het script gedeclareerde para meters worden variabelen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-212">Parameters declared by the script become variables.</span></span> <span data-ttu-id="4b5c4-213">Para meters waarvoor geen waarde is opgegeven, worden variabelen zonder waarde.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-213">Parameters for which no value has been given become variables with no value.</span></span> <span data-ttu-id="4b5c4-214">De automatische variabele blijft echter `$args` behouden.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-214">However, the automatic variable `$args` is preserved.</span></span>

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> <span data-ttu-id="4b5c4-215">De operator stip sourcing wordt gevolgd door een spatie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-215">The dot sourcing operator is followed by a space.</span></span> <span data-ttu-id="4b5c4-216">Gebruik de ruimte om het punt te onderscheiden van het punt ( `.` ) dat staat voor de huidige map.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-216">Use the space to distinguish the dot from the dot (`.`) symbol that represents the current directory.</span></span>
>
> <span data-ttu-id="4b5c4-217">In het volgende voor beeld wordt het Sample.ps1 script in de huidige map uitgevoerd in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-217">In the following example, the Sample.ps1 script in the current directory is run in the current scope.</span></span>
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a><span data-ttu-id="4b5c4-218">Indelings operator `-f`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-218">Format operator `-f`</span></span>

<span data-ttu-id="4b5c4-219">Teken reeksen met de indelings methode van teken reeks objecten.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-219">Formats strings by using the format method of string objects.</span></span> <span data-ttu-id="4b5c4-220">Voer de notatie teken reeks links van de operator in en de objecten die aan de rechter kant van de operator moeten worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-220">Enter the format string on the left side of the operator and the objects to be formatted on the right side of the operator.</span></span>

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

<span data-ttu-id="4b5c4-221">Als u de accolades ( `{}` ) in de opgemaakte teken reeks moet blijven staan, kunt u ze weglaten door de accolades te verdubbelen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-221">If you need to keep the curly braces (`{}`) in the formatted string, you can escape them by doubling the curly braces.</span></span>

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

<span data-ttu-id="4b5c4-222">Zie de methode [String. Format](/dotnet/api/system.string.format) en [samengestelde opmaak](/dotnet/standard/base-types/composite-formatting)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-222">For more information, see the [String.Format](/dotnet/api/system.string.format) method and [Composite Formatting](/dotnet/standard/base-types/composite-formatting).</span></span>

#### <a name="index-operator--"></a><span data-ttu-id="4b5c4-223">Index operator `[ ]`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-223">Index operator `[ ]`</span></span>

<span data-ttu-id="4b5c4-224">Selecteert objecten uit geïndexeerde verzamelingen, zoals matrices en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-224">Selects objects from indexed collections, such as arrays and hash tables.</span></span> <span data-ttu-id="4b5c4-225">Matrix indexen zijn gebaseerd op nul, dus het eerste object wordt geïndexeerd als `[0]` .</span><span class="sxs-lookup"><span data-stu-id="4b5c4-225">Array indexes are zero-based, so the first object is indexed as `[0]`.</span></span> <span data-ttu-id="4b5c4-226">Voor matrices (alleen) kunt u ook negatieve indexen gebruiken om de laatste waarden op te halen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-226">For arrays (only), you can also use negative indexes to get the last values.</span></span> <span data-ttu-id="4b5c4-227">Hash-tabellen worden geïndexeerd op basis van de sleutel waarde.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-227">Hash tables are indexed by key value.</span></span>

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

#### <a name="pipeline-operator-"></a><span data-ttu-id="4b5c4-228">Pijplijn operator `|`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-228">Pipeline operator `|`</span></span>

<span data-ttu-id="4b5c4-229">Verzendt ("sluizen") de uitvoer van de opdracht die voorafgaat aan de opdracht die erop volgt.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-229">Sends ("pipes") the output of the command that precedes it to the command that follows it.</span></span> <span data-ttu-id="4b5c4-230">Wanneer de uitvoer meer dan één object (een ' verzameling ') bevat, verzendt de pijplijn operator een voor een per keer de objecten.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-230">When the output includes more than one object (a "collection"), the pipeline operator sends the objects one at a time.</span></span>

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="range-operator-"></a><span data-ttu-id="4b5c4-231">De operator Range `..`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-231">Range operator `..`</span></span>

<span data-ttu-id="4b5c4-232">Vertegenwoordigt de sequentiële gehele getallen in een matrix met gehele getallen, op basis van een bovenste en onderste grens.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-232">Represents the sequential integers in an integer array, given an upper, and lower boundary.</span></span>

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

<span data-ttu-id="4b5c4-233">U kunt ook bereiken maken in omgekeerde volg orde.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-233">You can also create ranges in reverse order.</span></span>

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

<span data-ttu-id="4b5c4-234">Vanaf Power shell 6 werkt de bereik operator met **tekens** en **gehele getallen**.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-234">Beginning in PowerShell 6, the range operator works with **Characters** as well as **Integers**.</span></span>

<span data-ttu-id="4b5c4-235">Als u een reeks tekens wilt maken, plaatst u de grens tekens in aanhalings teken.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-235">To create a range of characters, enclose the boundary characters in quotes.</span></span>

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

#### <a name="member-access-operator-"></a><span data-ttu-id="4b5c4-236">Operator voor leden toegang `.`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-236">Member access operator `.`</span></span>

<span data-ttu-id="4b5c4-237">Toegang tot de eigenschappen en methoden van een object.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-237">Accesses the properties and methods of an object.</span></span> <span data-ttu-id="4b5c4-238">De lidnaam mag een expressie zijn.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-238">The member name may be an expression.</span></span>

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a><span data-ttu-id="4b5c4-239">Statische lid-operator `::`</span><span class="sxs-lookup"><span data-stu-id="4b5c4-239">Static member operator `::`</span></span>

<span data-ttu-id="4b5c4-240">Hiermee worden de statische eigenschappen en methoden van een .NET Framework klasse aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-240">Calls the static properties and methods of a .NET Framework class.</span></span> <span data-ttu-id="4b5c4-241">Als u de statische eigenschappen en methoden van een object wilt zoeken, gebruikt u de statische para meter van de `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-241">To find the static properties and methods of an object, use the Static parameter of the `Get-Member` cmdlet.</span></span>  <span data-ttu-id="4b5c4-242">De lidnaam mag een expressie zijn.</span><span class="sxs-lookup"><span data-stu-id="4b5c4-242">The member name may be an expression.</span></span>

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

## <a name="see-also"></a><span data-ttu-id="4b5c4-243">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4b5c4-243">See also</span></span>

[<span data-ttu-id="4b5c4-244">about_Arithmetic_Operators</span><span class="sxs-lookup"><span data-stu-id="4b5c4-244">about_Arithmetic_Operators</span></span>](about_Arithmetic_Operators.md)

[<span data-ttu-id="4b5c4-245">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="4b5c4-245">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="4b5c4-246">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="4b5c4-246">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="4b5c4-247">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="4b5c4-247">about_Logical_Operators</span></span>](about_logical_operators.md)

[<span data-ttu-id="4b5c4-248">about_Operator_Precedence</span><span class="sxs-lookup"><span data-stu-id="4b5c4-248">about_Operator_Precedence</span></span>](about_operator_precedence.md)

[<span data-ttu-id="4b5c4-249">about_Type_Operators</span><span class="sxs-lookup"><span data-stu-id="4b5c4-249">about_Type_Operators</span></span>](about_Type_Operators.md)

[<span data-ttu-id="4b5c4-250">about_Split</span><span class="sxs-lookup"><span data-stu-id="4b5c4-250">about_Split</span></span>](about_Split.md)

[<span data-ttu-id="4b5c4-251">about_Join</span><span class="sxs-lookup"><span data-stu-id="4b5c4-251">about_Join</span></span>](about_Join.md)

[<span data-ttu-id="4b5c4-252">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="4b5c4-252">about_Redirection</span></span>](about_Redirection.md)