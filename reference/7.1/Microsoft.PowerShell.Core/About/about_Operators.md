---
description: Hierin worden de Opera tors beschreven die worden ondersteund door Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: a917afc1499af96f834496c22e5634826c5aeb73
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/29/2020
ms.locfileid: "93253252"
---
# <a name="about-operators"></a><span data-ttu-id="c5317-104">Opera tors</span><span class="sxs-lookup"><span data-stu-id="c5317-104">About Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="c5317-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="c5317-105">Short description</span></span>
<span data-ttu-id="c5317-106">Hierin worden de Opera tors beschreven die worden ondersteund door Power shell.</span><span class="sxs-lookup"><span data-stu-id="c5317-106">Describes the operators that are supported by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="c5317-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="c5317-107">Long description</span></span>

<span data-ttu-id="c5317-108">Een operator is een taal element dat u kunt gebruiken in een opdracht of expressie.</span><span class="sxs-lookup"><span data-stu-id="c5317-108">An operator is a language element that you can use in a command or expression.</span></span>
<span data-ttu-id="c5317-109">Power shell ondersteunt diverse typen Opera tors die u helpen bij het manipuleren van waarden.</span><span class="sxs-lookup"><span data-stu-id="c5317-109">PowerShell supports several types of operators to help you manipulate values.</span></span>

### <a name="arithmetic-operators"></a><span data-ttu-id="c5317-110">Rekenkundige operators</span><span class="sxs-lookup"><span data-stu-id="c5317-110">Arithmetic Operators</span></span>

<span data-ttu-id="c5317-111">Reken kundige Opera tors ( `+` ,, `-` `*` , `/` ) gebruiken `%` om waarden in een opdracht of expressie te berekenen.</span><span class="sxs-lookup"><span data-stu-id="c5317-111">Use arithmetic operators (`+`, `-`, `*`, `/`, `%`) to calculate values in a command or expression.</span></span> <span data-ttu-id="c5317-112">Met deze opera tors kunt u waarden toevoegen, aftrekken, vermenigvuldigen of delen, en de rest (modulus) van een delings bewerking berekenen.</span><span class="sxs-lookup"><span data-stu-id="c5317-112">With these operators, you can add, subtract, multiply, or divide values, and calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="c5317-113">De operator voor optellen voegt elementen samen.</span><span class="sxs-lookup"><span data-stu-id="c5317-113">The addition operator concatenates elements.</span></span> <span data-ttu-id="c5317-114">De operator voor vermenigvuldigen retourneert het opgegeven aantal exemplaren van elk element.</span><span class="sxs-lookup"><span data-stu-id="c5317-114">The multiplication operator returns the specified number of copies of each element.</span></span> <span data-ttu-id="c5317-115">U kunt reken kundige Opera tors gebruiken voor elk .net-type dat deze implementeert, zoals: `Int` ,, `String` `DateTime` , `Hashtable` en arrays.</span><span class="sxs-lookup"><span data-stu-id="c5317-115">You can use arithmetic operators on any .NET type that implements them, such as: `Int`, `String`, `DateTime`, `Hashtable`, and Arrays.</span></span>

<span data-ttu-id="c5317-116">Bitsgewijze Opera tors ( `-band` , `-bor` ,,, `-bxor` `-bnot` `-shl` , `-shr` ) bewerken de bits patronen in waarden.</span><span class="sxs-lookup"><span data-stu-id="c5317-116">Bitwise operators (`-band`, `-bor`, `-bxor`, `-bnot`, `-shl`, `-shr`) manipulate the bit patterns in values.</span></span>

<span data-ttu-id="c5317-117">Zie [about_Arithmetic_Operators](about_Arithmetic_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5317-117">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="assignment-operators"></a><span data-ttu-id="c5317-118">Toewijzings operatoren</span><span class="sxs-lookup"><span data-stu-id="c5317-118">Assignment Operators</span></span>

<span data-ttu-id="c5317-119">Gebruik toewijzings operatoren (,,,, `=` `+=` `-=` `*=` `/=` , `%=` ) om waarden toe te wijzen, te wijzigen of toe te voegen aan variabelen.</span><span class="sxs-lookup"><span data-stu-id="c5317-119">Use assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `%=`) to assign, change, or append values to variables.</span></span> <span data-ttu-id="c5317-120">U kunt reken kundige Opera tors combi neren met toewijzing om het resultaat van de reken kundige bewerking aan een variabele toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="c5317-120">You can combine arithmetic operators with assignment to assign the result of the arithmetic operation to a variable.</span></span>

<span data-ttu-id="c5317-121">Zie [about_Assignment_Operators](about_Assignment_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5317-121">For more information, see [about_Assignment_Operators](about_Assignment_Operators.md).</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="c5317-122">Vergelijkingsoperators</span><span class="sxs-lookup"><span data-stu-id="c5317-122">Comparison Operators</span></span>

<span data-ttu-id="c5317-123">Gebruik vergelijkings operatoren ( `-eq` ,, `-ne` `-gt` , `-lt` , `-le` , `-ge` ) om waarden en test voorwaarden te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="c5317-123">Use comparison operators (`-eq`, `-ne`, `-gt`, `-lt`, `-le`, `-ge`) to compare values and test conditions.</span></span> <span data-ttu-id="c5317-124">U kunt bijvoorbeeld twee teken reeks waarden vergelijken om te bepalen of ze gelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="c5317-124">For example, you can compare two string values to determine whether they are equal.</span></span>

<span data-ttu-id="c5317-125">De vergelijkings operators omvatten ook Opera tors waarmee patronen in tekst worden gezocht of vervangen.</span><span class="sxs-lookup"><span data-stu-id="c5317-125">The comparison operators also include operators that find or replace patterns in text.</span></span> <span data-ttu-id="c5317-126">De `-match` `-notmatch` Opera tors (,, `-replace` ) gebruiken reguliere expressies en `-like` `-notlike` gebruiken joker tekens `*` .</span><span class="sxs-lookup"><span data-stu-id="c5317-126">The (`-match`, `-notmatch`, `-replace`) operators use regular expressions, and (`-like`, `-notlike`) use wildcards `*`.</span></span>

<span data-ttu-id="c5317-127">Containment-vergelijkings operatoren bepalen of een test waarde wordt weer gegeven in een referentieset ( `-in` ,, `-notin` `-contains` , `-notcontains` ).</span><span class="sxs-lookup"><span data-stu-id="c5317-127">Containment comparison operators determine whether a test value appears in a reference set (`-in`, `-notin`, `-contains`, `-notcontains`).</span></span>

<span data-ttu-id="c5317-128">Type vergelijkings operatoren ( `-is` , `-isnot` ) bepalen of een object van een bepaald type is.</span><span class="sxs-lookup"><span data-stu-id="c5317-128">Type comparison operators (`-is`, `-isnot`) determine whether an object is of a given type.</span></span>

<span data-ttu-id="c5317-129">Zie [about_Comparison_Operators](about_Comparison_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5317-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span>

### <a name="logical-operators"></a><span data-ttu-id="c5317-130">Logische operators</span><span class="sxs-lookup"><span data-stu-id="c5317-130">Logical Operators</span></span>

<span data-ttu-id="c5317-131">Gebruik logische Opera tors (,,, `-and` `-or` `-xor` `-not` , `!` ) om voorwaardelijke instructies te verbinden met één complexe voorwaardelijke waarde.</span><span class="sxs-lookup"><span data-stu-id="c5317-131">Use logical operators (`-and`, `-or`, `-xor`, `-not`, `!`) to connect conditional statements into a single complex conditional.</span></span> <span data-ttu-id="c5317-132">U kunt bijvoorbeeld een logische `-and` operator gebruiken om een object filter te maken met twee verschillende voor waarden.</span><span class="sxs-lookup"><span data-stu-id="c5317-132">For example, you can use a logical `-and` operator to create an object filter with two different conditions.</span></span>

<span data-ttu-id="c5317-133">Zie [about_Logical_Operators](about_logical_operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5317-133">For more information, see [about_Logical_Operators](about_logical_operators.md).</span></span>

### <a name="redirection-operators"></a><span data-ttu-id="c5317-134">Omleidings operatoren</span><span class="sxs-lookup"><span data-stu-id="c5317-134">Redirection Operators</span></span>

<span data-ttu-id="c5317-135">Gebruik de omleidings operatoren ( `>` ,, `>>` `2>` , `2>>` en `2>&1` ) om de uitvoer van een opdracht of expressie naar een tekst bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="c5317-135">Use redirection operators (`>`, `>>`, `2>`, `2>>`, and `2>&1`) to send the output of a command or expression to a text file.</span></span> <span data-ttu-id="c5317-136">De omleidings operatoren werken zoals de `Out-File` cmdlet (zonder para meters), maar u kunt ook de fout uitvoer omleiden naar opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="c5317-136">The redirection operators work like the `Out-File` cmdlet (without parameters) but they also let you redirect error output to specified files.</span></span> <span data-ttu-id="c5317-137">U kunt ook de- `Tee-Object` cmdlet gebruiken om uitvoer om te leiden.</span><span class="sxs-lookup"><span data-stu-id="c5317-137">You can also use the `Tee-Object` cmdlet to redirect output.</span></span>

<span data-ttu-id="c5317-138">Zie [about_Redirection](about_Redirection.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5317-138">For more information, see [about_Redirection](about_Redirection.md)</span></span>

### <a name="split-and-join-operators"></a><span data-ttu-id="c5317-139">Opera tors voor splitsen en samen voegen</span><span class="sxs-lookup"><span data-stu-id="c5317-139">Split and Join Operators</span></span>

<span data-ttu-id="c5317-140">De `-split` `-join` Opera tors en delen subtekenreeksen en combi neren deze.</span><span class="sxs-lookup"><span data-stu-id="c5317-140">The `-split` and `-join` operators divide and combine substrings.</span></span> <span data-ttu-id="c5317-141">De `-split` operator splitst een teken reeks in subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="c5317-141">The `-split` operator splits a string into substrings.</span></span> <span data-ttu-id="c5317-142">De `-join` operator voegt meerdere teken reeksen samen tot één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c5317-142">The `-join` operator concatenates multiple strings into a single string.</span></span>

<span data-ttu-id="c5317-143">Zie [about_Split](about_Split.md) en [about_Join](about_Join.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5317-143">For more information, see [about_Split](about_Split.md) and [about_Join](about_Join.md).</span></span>

### <a name="type-operators"></a><span data-ttu-id="c5317-144">Type operators</span><span class="sxs-lookup"><span data-stu-id="c5317-144">Type Operators</span></span>

<span data-ttu-id="c5317-145">Gebruik de type operators ( `-is` , `-isnot` , `-as` ) om het .NET Framework type van een object te zoeken of te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c5317-145">Use the type operators (`-is`, `-isnot`, `-as`) to find or change the .NET Framework type of an object.</span></span>

<span data-ttu-id="c5317-146">Zie [about_Type_Operators](about_Type_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5317-146">For more information, see [about_Type_Operators](about_Type_Operators.md).</span></span>

### <a name="unary-operators"></a><span data-ttu-id="c5317-147">Unaire Opera tors</span><span class="sxs-lookup"><span data-stu-id="c5317-147">Unary Operators</span></span>

<span data-ttu-id="c5317-148">Gebruik unaire Opera tors om variabelen of object eigenschappen te verhogen of verlagen en om integers in te stellen op positieve of negatieve getallen.</span><span class="sxs-lookup"><span data-stu-id="c5317-148">Use unary operators to increment or decrement variables or object properties and to set integers to positive or negative numbers.</span></span> <span data-ttu-id="c5317-149">Als u bijvoorbeeld de variabele wilt verhogen `$a` van `9` naar `10` , typt u `$a++` .</span><span class="sxs-lookup"><span data-stu-id="c5317-149">For example, to increment the variable `$a` from `9` to `10`, you type `$a++`.</span></span>

### <a name="special-operators"></a><span data-ttu-id="c5317-150">Speciale Opera tors</span><span class="sxs-lookup"><span data-stu-id="c5317-150">Special Operators</span></span>

<span data-ttu-id="c5317-151">Speciale Opera tors hebben specifieke use-cases die niet in een andere operator groep passen.</span><span class="sxs-lookup"><span data-stu-id="c5317-151">Special operators have specific use-cases that do not fit into any other operator group.</span></span> <span data-ttu-id="c5317-152">Speciale Opera tors maken het bijvoorbeeld mogelijk om opdrachten uit te voeren, het gegevens type van een waarde te wijzigen of elementen uit een matrix op te halen.</span><span class="sxs-lookup"><span data-stu-id="c5317-152">For example, special operators allow you to run commands, change a value's data type, or retrieve elements from an array.</span></span>

#### <a name="grouping-operator--"></a><span data-ttu-id="c5317-153">Operator voor groeperen `( )`</span><span class="sxs-lookup"><span data-stu-id="c5317-153">Grouping operator `( )`</span></span>

<span data-ttu-id="c5317-154">Net als in andere talen `(...)` moet de operator prioriteit in expressies worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="c5317-154">As in other languages, `(...)` serves to override operator precedence in expressions.</span></span> <span data-ttu-id="c5317-155">Bijvoorbeeld: `(1 + 2) / 3`</span><span class="sxs-lookup"><span data-stu-id="c5317-155">For example: `(1 + 2) / 3`</span></span>

<span data-ttu-id="c5317-156">Er zijn echter extra problemen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="c5317-156">However, in PowerShell, there are additional behaviors.</span></span>

- <span data-ttu-id="c5317-157">`(...)` met kunt u de uitvoer van een _opdracht_ laten deel uitmaken van een expressie.</span><span class="sxs-lookup"><span data-stu-id="c5317-157">`(...)` allows you to let output from a _command_ participate in an expression.</span></span> <span data-ttu-id="c5317-158">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="c5317-158">For example:</span></span>

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- <span data-ttu-id="c5317-159">Wanneer u gebruikt als het eerste segment van een pijp lijn, verpakt u een opdracht of expressie tussen haakjes invariably resulteert in de _opsomming_ van het resultaat van de expressie.</span><span class="sxs-lookup"><span data-stu-id="c5317-159">When used as the first segment of a pipeline, wrapping a command or expression in parentheses invariably causes _enumeration_ of the expression result.</span></span> <span data-ttu-id="c5317-160">Als de haakjes een _opdracht_ teruglopen, wordt deze uitgevoerd om te volt ooien met alle uitvoer die _in het geheugen is verzameld_ voordat de resultaten via de pijp lijn worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="c5317-160">If the parentheses wrap a _command_ , it is run to completion with all output _collected in memory_ before the results are sent through the pipeline.</span></span>

#### <a name="subexpression-operator--"></a><span data-ttu-id="c5317-161">Operator voor subexpressie `$( )`</span><span class="sxs-lookup"><span data-stu-id="c5317-161">Subexpression operator `$( )`</span></span>

<span data-ttu-id="c5317-162">Retourneert het resultaat van een of meer instructies.</span><span class="sxs-lookup"><span data-stu-id="c5317-162">Returns the result of one or more statements.</span></span> <span data-ttu-id="c5317-163">Voor één resultaat retourneert een scalaire waarde.</span><span class="sxs-lookup"><span data-stu-id="c5317-163">For a single result, returns a scalar.</span></span> <span data-ttu-id="c5317-164">Voor meerdere resultaten wordt een matrix geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c5317-164">For multiple results, returns an array.</span></span> <span data-ttu-id="c5317-165">Gebruik deze als u een expressie binnen een andere expressie wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c5317-165">Use this when you want to use an expression within another expression.</span></span> <span data-ttu-id="c5317-166">Bijvoorbeeld, om de resultaten van de opdracht in een teken reeks expressie in te sluiten.</span><span class="sxs-lookup"><span data-stu-id="c5317-166">For example, to embed the results of command in a string expression.</span></span>

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a><span data-ttu-id="c5317-167">Operator voor subexpressie van matrix `@( )`</span><span class="sxs-lookup"><span data-stu-id="c5317-167">Array subexpression operator `@( )`</span></span>

<span data-ttu-id="c5317-168">Retourneert het resultaat van een of meer instructies als een matrix.</span><span class="sxs-lookup"><span data-stu-id="c5317-168">Returns the result of one or more statements as an array.</span></span> <span data-ttu-id="c5317-169">Als er slechts één item is, heeft de matrix slechts één lid.</span><span class="sxs-lookup"><span data-stu-id="c5317-169">If there is only one item, the array has only one member.</span></span>

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="call-operator-"></a><span data-ttu-id="c5317-170">Aanroep operator `&`</span><span class="sxs-lookup"><span data-stu-id="c5317-170">Call operator `&`</span></span>

<span data-ttu-id="c5317-171">Voert een opdracht, script of script blok uit.</span><span class="sxs-lookup"><span data-stu-id="c5317-171">Runs a command, script, or script block.</span></span> <span data-ttu-id="c5317-172">Met de oproep operator, ook wel bekend als aanroep operator, kunt u opdrachten uitvoeren die zijn opgeslagen in variabelen en vertegenwoordigd door teken reeksen of script blokken.</span><span class="sxs-lookup"><span data-stu-id="c5317-172">The call operator, also known as the "invocation operator", lets you run commands that are stored in variables and represented by strings or script blocks.</span></span> <span data-ttu-id="c5317-173">De aanroep operator wordt uitgevoerd in een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="c5317-173">The call operator executes in a child scope.</span></span> <span data-ttu-id="c5317-174">Zie [about_Scopes](about_Scopes.md)voor meer informatie over bereiken.</span><span class="sxs-lookup"><span data-stu-id="c5317-174">For more about scopes, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="c5317-175">In dit voor beeld wordt een opdracht in een teken reeks opgeslagen en uitgevoerd met de aanroep operator.</span><span class="sxs-lookup"><span data-stu-id="c5317-175">This example stores a command in a string and executes it using the call operator.</span></span>

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

<span data-ttu-id="c5317-176">De aanroep operator parseert geen teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="c5317-176">The call operator does not parse strings.</span></span> <span data-ttu-id="c5317-177">Dit betekent dat u geen opdracht parameters binnen een teken reeks kunt gebruiken wanneer u de aanroep operator gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c5317-177">This means that you cannot use command parameters within a string when you use the call operator.</span></span>

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

<span data-ttu-id="c5317-178">Met de cmdlet [invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) kan code worden uitgevoerd die fouten tijdens het parseren van de aanroep operator veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="c5317-178">The [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) cmdlet can execute code that causes parsing errors when using the call operator.</span></span>

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

<span data-ttu-id="c5317-179">U kunt de aanroep operator gebruiken om scripts uit te voeren met hun bestands namen.</span><span class="sxs-lookup"><span data-stu-id="c5317-179">You can use the call operator to execute scripts using their filenames.</span></span> <span data-ttu-id="c5317-180">In het onderstaande voor beeld ziet u een script bestandsnaam die spaties bevat.</span><span class="sxs-lookup"><span data-stu-id="c5317-180">The example below shows a script filename that contains spaces.</span></span> <span data-ttu-id="c5317-181">Wanneer u het script probeert uit te voeren, geeft Power shell in plaats daarvan de inhoud weer van de teken reeks met de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="c5317-181">When you try to execute the script, PowerShell instead displays the contents of the quoted string containing the filename.</span></span> <span data-ttu-id="c5317-182">Met de aanroep operator kunt u de inhoud van de teken reeks met de bestands naam uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c5317-182">The call operator allows you to execute the contents of the string containing the filename.</span></span>

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

<span data-ttu-id="c5317-183">Zie [about_Script_Blocks](about_Script_Blocks.md)voor meer informatie over script blokken.</span><span class="sxs-lookup"><span data-stu-id="c5317-183">For more about script blocks, see [about_Script_Blocks](about_Script_Blocks.md).</span></span>

#### <a name="background-operator-"></a><span data-ttu-id="c5317-184">Operator voor achtergrond `&`</span><span class="sxs-lookup"><span data-stu-id="c5317-184">Background operator `&`</span></span>

<span data-ttu-id="c5317-185">Voert de pijp lijn voordat deze op de achtergrond wordt uitgevoerd in een Power shell-taak.</span><span class="sxs-lookup"><span data-stu-id="c5317-185">Runs the pipeline before it in the background, in a PowerShell job.</span></span> <span data-ttu-id="c5317-186">Deze operator werkt op dezelfde manier als de UNIX-besturings operator en-teken ( `&` ), waarbij de opdracht wordt uitgevoerd vóór asynchroon in subshell als een taak.</span><span class="sxs-lookup"><span data-stu-id="c5317-186">This operator acts similarly to the UNIX control operator ampersand (`&`), which runs the command before it asynchronously in subshell as a job.</span></span>

<span data-ttu-id="c5317-187">Deze operator is functioneel gelijk aan `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="c5317-187">This operator is functionally equivalent to `Start-Job`.</span></span> <span data-ttu-id="c5317-188">Standaard start de operator achtergrond de taken in de huidige werkmap van de aanroeper die de parallelle taken heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="c5317-188">By default, the background operator starts the jobs in the current working directory of the caller that started the parallel tasks.</span></span> <span data-ttu-id="c5317-189">In het volgende voor beeld wordt het basis gebruik van de taak operator achtergrond gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="c5317-189">The following example demonstrates basic usage of the background job operator.</span></span>

```powershell
Get-Process -Name pwsh &
```

<span data-ttu-id="c5317-190">Deze opdracht is functioneel gelijk aan het volgende gebruik van `Start-Job` :</span><span class="sxs-lookup"><span data-stu-id="c5317-190">That command is functionally equivalent to the following usage of `Start-Job`:</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

<span data-ttu-id="c5317-191">Net als `Start-Job` : de `&` operator background retourneert een- `Job` object.</span><span class="sxs-lookup"><span data-stu-id="c5317-191">Just like `Start-Job`, the `&` background operator returns a `Job` object.</span></span> <span data-ttu-id="c5317-192">Dit object kan worden gebruikt met `Receive-Job` en `Remove-Job` , net alsof u hebt gebruikt `Start-Job` om de taak te starten.</span><span class="sxs-lookup"><span data-stu-id="c5317-192">This object can be used with `Receive-Job` and `Remove-Job`, just as if you had used `Start-Job` to start the job.</span></span>

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

<span data-ttu-id="c5317-193">De `&` operator voor de achtergrond is ook een instructie-eind punt, net als bij de UNIX-besturings operator en-teken ( `&` ).</span><span class="sxs-lookup"><span data-stu-id="c5317-193">The `&` background operator is also a statement terminator, just like the UNIX control operator ampersand (`&`).</span></span> <span data-ttu-id="c5317-194">Hierdoor kunt u aanvullende opdrachten aanroepen na de `&` operator achtergrond.</span><span class="sxs-lookup"><span data-stu-id="c5317-194">This allows you to invoke additional commands after the `&` background operator.</span></span> <span data-ttu-id="c5317-195">In het volgende voor beeld ziet u de aanroep van extra opdrachten na de `&` operator achtergrond.</span><span class="sxs-lookup"><span data-stu-id="c5317-195">The following example demonstrates the invocation of additional commands after the `&` background operator.</span></span>

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

<span data-ttu-id="c5317-196">Dit komt overeen met het volgende script:</span><span class="sxs-lookup"><span data-stu-id="c5317-196">This is equivalent to the following script:</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

<span data-ttu-id="c5317-197">Als u meerdere opdrachten wilt uitvoeren, elk in een eigen achtergrond proces, maar op één regel, plaatst u gewoon `&` tussen en na elk van de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="c5317-197">If you want to run multiple commands, each in their own background process but all on one line, simply place `&` between and after each of the commands.</span></span>

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

<span data-ttu-id="c5317-198">Zie [about_Jobs](about_Jobs.md)voor meer informatie over Power shell-taken.</span><span class="sxs-lookup"><span data-stu-id="c5317-198">For more information on PowerShell jobs, see [about_Jobs](about_Jobs.md).</span></span>

#### <a name="cast-operator--"></a><span data-ttu-id="c5317-199">Conversie operator `[ ]`</span><span class="sxs-lookup"><span data-stu-id="c5317-199">Cast operator `[ ]`</span></span>

<span data-ttu-id="c5317-200">Hiermee worden objecten geconverteerd of beperkt tot het opgegeven type.</span><span class="sxs-lookup"><span data-stu-id="c5317-200">Converts or limits objects to the specified type.</span></span> <span data-ttu-id="c5317-201">Als de objecten niet kunnen worden geconverteerd, wordt er door Power shell een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c5317-201">If the objects cannot be converted, PowerShell generates an error.</span></span>

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

<span data-ttu-id="c5317-202">Een cast kan ook worden uitgevoerd wanneer een variabele is toegewezen aan met behulp van de [cast-notatie](about_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="c5317-202">A cast can also be performed when a variable is assigned to using [cast notation](about_Variables.md).</span></span>

#### <a name="comma-operator-"></a><span data-ttu-id="c5317-203">Komma operator `,`</span><span class="sxs-lookup"><span data-stu-id="c5317-203">Comma operator `,`</span></span>

<span data-ttu-id="c5317-204">Als binaire operator maakt de komma een matrix of voegt deze toe aan de matrix die wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c5317-204">As a binary operator, the comma creates an array or appends to the array being created.</span></span> <span data-ttu-id="c5317-205">In de expressie modus, als een unaire operator, maakt de komma een matrix met slechts één lid.</span><span class="sxs-lookup"><span data-stu-id="c5317-205">In expression mode, as a unary operator, the comma creates an array with just one member.</span></span> <span data-ttu-id="c5317-206">Plaats de komma vóór het lid.</span><span class="sxs-lookup"><span data-stu-id="c5317-206">Place the comma before the member.</span></span>

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

<span data-ttu-id="c5317-207">Omdat `Write-Object` een argument wordt verwacht, moet u de expressie tussen haakjes plaatsen.</span><span class="sxs-lookup"><span data-stu-id="c5317-207">Since `Write-Object` expects an argument, you must put the expression in parentheses.</span></span>

#### <a name="dot-sourcing-operator-"></a><span data-ttu-id="c5317-208">Operator voor punt sourcing `.`</span><span class="sxs-lookup"><span data-stu-id="c5317-208">Dot sourcing operator `.`</span></span>

<span data-ttu-id="c5317-209">Voert een script uit in het huidige bereik, zodat alle functies, aliassen en variabelen die het script maakt, worden toegevoegd aan het huidige bereik en bestaande worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="c5317-209">Runs a script in the current scope so that any functions, aliases, and variables that the script creates are added to the current scope, overriding existing ones.</span></span> <span data-ttu-id="c5317-210">De door het script gedeclareerde para meters worden variabelen.</span><span class="sxs-lookup"><span data-stu-id="c5317-210">Parameters declared by the script become variables.</span></span> <span data-ttu-id="c5317-211">Para meters waarvoor geen waarde is opgegeven, worden variabelen zonder waarde.</span><span class="sxs-lookup"><span data-stu-id="c5317-211">Parameters for which no value has been given become variables with no value.</span></span> <span data-ttu-id="c5317-212">De automatische variabele blijft echter `$args` behouden.</span><span class="sxs-lookup"><span data-stu-id="c5317-212">However, the automatic variable `$args` is preserved.</span></span>

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> <span data-ttu-id="c5317-213">De operator stip sourcing wordt gevolgd door een spatie.</span><span class="sxs-lookup"><span data-stu-id="c5317-213">The dot sourcing operator is followed by a space.</span></span> <span data-ttu-id="c5317-214">Gebruik de ruimte om het punt te onderscheiden van het punt ( `.` ) dat staat voor de huidige map.</span><span class="sxs-lookup"><span data-stu-id="c5317-214">Use the space to distinguish the dot from the dot (`.`) symbol that represents the current directory.</span></span>
>
> <span data-ttu-id="c5317-215">In het volgende voor beeld wordt het Sample.ps1 script in de huidige map uitgevoerd in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="c5317-215">In the following example, the Sample.ps1 script in the current directory is run in the current scope.</span></span>
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a><span data-ttu-id="c5317-216">Indelings operator `-f`</span><span class="sxs-lookup"><span data-stu-id="c5317-216">Format operator `-f`</span></span>

<span data-ttu-id="c5317-217">Teken reeksen met de indelings methode van teken reeks objecten.</span><span class="sxs-lookup"><span data-stu-id="c5317-217">Formats strings by using the format method of string objects.</span></span> <span data-ttu-id="c5317-218">Voer de notatie teken reeks links van de operator in en de objecten die aan de rechter kant van de operator moeten worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="c5317-218">Enter the format string on the left side of the operator and the objects to be formatted on the right side of the operator.</span></span>

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

<span data-ttu-id="c5317-219">Als u de accolades ( `{}` ) in de opgemaakte teken reeks moet blijven staan, kunt u ze weglaten door de accolades te verdubbelen.</span><span class="sxs-lookup"><span data-stu-id="c5317-219">If you need to keep the curly braces (`{}`) in the formatted string, you can escape them by doubling the curly braces.</span></span>

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

<span data-ttu-id="c5317-220">Zie de methode [String. Format](/dotnet/api/system.string.format) en [samengestelde opmaak](/dotnet/standard/base-types/composite-formatting)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5317-220">For more information, see the [String.Format](/dotnet/api/system.string.format) method and [Composite Formatting](/dotnet/standard/base-types/composite-formatting).</span></span>

#### <a name="index-operator--"></a><span data-ttu-id="c5317-221">Index operator `[ ]`</span><span class="sxs-lookup"><span data-stu-id="c5317-221">Index operator `[ ]`</span></span>

<span data-ttu-id="c5317-222">Selecteert objecten uit geïndexeerde verzamelingen, zoals matrices en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="c5317-222">Selects objects from indexed collections, such as arrays and hash tables.</span></span> <span data-ttu-id="c5317-223">Matrix indexen zijn gebaseerd op nul, dus het eerste object wordt geïndexeerd als `[0]` .</span><span class="sxs-lookup"><span data-stu-id="c5317-223">Array indexes are zero-based, so the first object is indexed as `[0]`.</span></span> <span data-ttu-id="c5317-224">Voor matrices (alleen) kunt u ook negatieve indexen gebruiken om de laatste waarden op te halen.</span><span class="sxs-lookup"><span data-stu-id="c5317-224">For arrays (only), you can also use negative indexes to get the last values.</span></span> <span data-ttu-id="c5317-225">Hash-tabellen worden geïndexeerd op basis van de sleutel waarde.</span><span class="sxs-lookup"><span data-stu-id="c5317-225">Hash tables are indexed by key value.</span></span>

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

#### <a name="pipeline-operator-"></a><span data-ttu-id="c5317-226">Pijplijn operator `|`</span><span class="sxs-lookup"><span data-stu-id="c5317-226">Pipeline operator `|`</span></span>

<span data-ttu-id="c5317-227">Verzendt ("sluizen") de uitvoer van de opdracht die voorafgaat aan de opdracht die erop volgt.</span><span class="sxs-lookup"><span data-stu-id="c5317-227">Sends ("pipes") the output of the command that precedes it to the command that follows it.</span></span> <span data-ttu-id="c5317-228">Wanneer de uitvoer meer dan één object (een ' verzameling ') bevat, verzendt de pijplijn operator een voor een per keer de objecten.</span><span class="sxs-lookup"><span data-stu-id="c5317-228">When the output includes more than one object (a "collection"), the pipeline operator sends the objects one at a time.</span></span>

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="pipeline-chain-operators--and-"></a><span data-ttu-id="c5317-229">Pijplijn keten operators `&&` en `||`</span><span class="sxs-lookup"><span data-stu-id="c5317-229">Pipeline chain operators `&&` and `||`</span></span>

<span data-ttu-id="c5317-230">Voer voorwaardelijk de rechter pijplijn uit op basis van het succes van de pijp lijn aan de linkerkant.</span><span class="sxs-lookup"><span data-stu-id="c5317-230">Conditionally execute the right-hand side pipeline based on the success of the left-hand side pipeline.</span></span>

```powershell
# If Get-Process successfully finds a process called notepad,
# Stop-Process -Name notepad is called
Get-Process notepad && Stop-Process -Name notepad
```

```powershell
# If npm install fails, the node_modules directory is removed
npm install || Remove-Item -Recurse ./node_modules
```

<span data-ttu-id="c5317-231">Zie [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5317-231">For more information, see [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md).</span></span>

#### <a name="range-operator-"></a><span data-ttu-id="c5317-232">De operator Range `..`</span><span class="sxs-lookup"><span data-stu-id="c5317-232">Range operator `..`</span></span>

<span data-ttu-id="c5317-233">Vertegenwoordigt de sequentiële gehele getallen in een matrix met gehele getallen, op basis van een bovenste en onderste grens.</span><span class="sxs-lookup"><span data-stu-id="c5317-233">Represents the sequential integers in an integer array, given an upper, and lower boundary.</span></span>

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

<span data-ttu-id="c5317-234">U kunt ook bereiken maken in omgekeerde volg orde.</span><span class="sxs-lookup"><span data-stu-id="c5317-234">You can also create ranges in reverse order.</span></span>

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

<span data-ttu-id="c5317-235">Vanaf Power shell 6 werkt de bereik operator met **tekens** en **gehele getallen**.</span><span class="sxs-lookup"><span data-stu-id="c5317-235">Beginning in PowerShell 6, the range operator works with **Characters** as well as **Integers**.</span></span>

<span data-ttu-id="c5317-236">Als u een reeks tekens wilt maken, plaatst u de grens tekens in aanhalings teken.</span><span class="sxs-lookup"><span data-stu-id="c5317-236">To create a range of characters, enclose the boundary characters in quotes.</span></span>

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

#### <a name="member-access-operator-"></a><span data-ttu-id="c5317-237">Operator voor leden toegang `.`</span><span class="sxs-lookup"><span data-stu-id="c5317-237">Member access operator `.`</span></span>

<span data-ttu-id="c5317-238">Toegang tot de eigenschappen en methoden van een object.</span><span class="sxs-lookup"><span data-stu-id="c5317-238">Accesses the properties and methods of an object.</span></span> <span data-ttu-id="c5317-239">De lidnaam mag een expressie zijn.</span><span class="sxs-lookup"><span data-stu-id="c5317-239">The member name may be an expression.</span></span>

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a><span data-ttu-id="c5317-240">Statische lid-operator `::`</span><span class="sxs-lookup"><span data-stu-id="c5317-240">Static member operator `::`</span></span>

<span data-ttu-id="c5317-241">Hiermee worden de statische eigenschappen en methoden van een .NET Framework klasse aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="c5317-241">Calls the static properties and methods of a .NET Framework class.</span></span> <span data-ttu-id="c5317-242">Als u de statische eigenschappen en methoden van een object wilt zoeken, gebruikt u de statische para meter van de `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5317-242">To find the static properties and methods of an object, use the Static parameter of the `Get-Member` cmdlet.</span></span>  <span data-ttu-id="c5317-243">De lidnaam mag een expressie zijn.</span><span class="sxs-lookup"><span data-stu-id="c5317-243">The member name may be an expression.</span></span>

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

#### <a name="ternary-operator--if-true--if-false"></a><span data-ttu-id="c5317-244">Ternaire operator `? <if-true> : <if-false>`</span><span class="sxs-lookup"><span data-stu-id="c5317-244">Ternary operator `? <if-true> : <if-false>`</span></span>

<span data-ttu-id="c5317-245">U kunt de ternaire operator als vervanging voor de instructie gebruiken `if-else` in eenvoudige voorwaardelijke cases.</span><span class="sxs-lookup"><span data-stu-id="c5317-245">You can use the ternary operator as a replacement for the `if-else` statement in simple conditional cases.</span></span>

<span data-ttu-id="c5317-246">Zie [about_If](about_If.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5317-246">For more information, see [about_If](about_If.md).</span></span>

#### <a name="null-coalescing-operator-"></a><span data-ttu-id="c5317-247">Null-samenvoegings operator `??`</span><span class="sxs-lookup"><span data-stu-id="c5317-247">Null-coalescing operator `??`</span></span>

<span data-ttu-id="c5317-248">De operator null-samenvoeging `??` retourneert de waarde van de linkeroperand als deze niet null is.</span><span class="sxs-lookup"><span data-stu-id="c5317-248">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span> <span data-ttu-id="c5317-249">Anders wordt de rechter operand geëvalueerd en wordt het resultaat geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c5317-249">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="c5317-250">De `??` operator evalueert de rechter operand niet als de linkeroperand wordt geëvalueerd als niet-null.</span><span class="sxs-lookup"><span data-stu-id="c5317-250">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
```

```Output
100
```

<span data-ttu-id="c5317-251">In het volgende voor beeld wordt de rechter operand niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="c5317-251">In the following example, the right-hand operand won't be evaluated.</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-coalescing-assignment-operator-"></a><span data-ttu-id="c5317-252">De toewijzings operator null-samen voegen `??=`</span><span class="sxs-lookup"><span data-stu-id="c5317-252">Null-coalescing assignment operator `??=`</span></span>

<span data-ttu-id="c5317-253">De operator voor het samen voegen van Null-samen voegen `??=` wijst de waarde van de rechter operand alleen aan de linkeroperand toe als de linkeroperand wordt geëvalueerd als null.</span><span class="sxs-lookup"><span data-stu-id="c5317-253">The null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="c5317-254">De `??=` operator evalueert de rechter operand niet als de linkeroperand wordt geëvalueerd als niet-null.</span><span class="sxs-lookup"><span data-stu-id="c5317-254">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
```

```Output
100
```

<span data-ttu-id="c5317-255">In het volgende voor beeld wordt de rechter operand niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="c5317-255">In the following example, the right-hand operand won't be evaluated.</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-conditional-operators--and-"></a><span data-ttu-id="c5317-256">Null-voorwaardelijke Opera tors `?.` en `?[]`</span><span class="sxs-lookup"><span data-stu-id="c5317-256">Null-conditional operators `?.` and `?[]`</span></span>

> [!NOTE]
> <span data-ttu-id="c5317-257">Deze functie is verplaatst van experimentele naar mainstream in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="c5317-257">This feature was moved from experimental to mainstream in PowerShell 7.1.</span></span>

<span data-ttu-id="c5317-258">Een null-voorwaardelijke operator past een leden toegang, `?.` , of element toegang, `?[]` alleen aan de operand toe als die operand resulteert in niet-null; anders wordt Null geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c5317-258">A null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

<span data-ttu-id="c5317-259">Aangezien Power shell `?` een deel van de naam van de variabele toestaat, is formele specificatie van de naam van de variabele vereist voor het gebruik van deze opera tors.</span><span class="sxs-lookup"><span data-stu-id="c5317-259">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="c5317-260">Het is dus nood zakelijk om `{}` de namen van variabelen te gebruiken, zoals `${a}` of wanneer `?` het een deel van de naam van de variabele is `${a?}` .</span><span class="sxs-lookup"><span data-stu-id="c5317-260">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="c5317-261">In het volgende voor beeld wordt de waarde van **propnaam** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c5317-261">In the following example, the value of **PropName** is returned.</span></span>

```powershell
$a = @{ PropName = 100 }
${a}?.PropName
```

```Output
100
```

<span data-ttu-id="c5317-262">In het volgende voor beeld wordt Null geretourneerd zonder dat u toegang probeert te krijgen tot **de naam van de lidnaam.**</span><span class="sxs-lookup"><span data-stu-id="c5317-262">The following example will return null, without trying to access the member name **PropName**.</span></span>

```powershell
$a = $null
${a}?.PropName
```

<span data-ttu-id="c5317-263">Op dezelfde manier wordt de waarde van het element geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c5317-263">Similarly, the value of the element will be returned.</span></span>

```powershell
$a = 1..10
${a}?[0]
```

```Output
1
```

<span data-ttu-id="c5317-264">En als de operand null is, wordt het element niet geopend en wordt Null geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c5317-264">And when the operand is null, the element isn't accessed and null is returned.</span></span>

```PowerShell
$a = $null
${a}?[0]
```

## <a name="see-also"></a><span data-ttu-id="c5317-265">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c5317-265">See also</span></span>

[<span data-ttu-id="c5317-266">about_Arithmetic_Operators</span><span class="sxs-lookup"><span data-stu-id="c5317-266">about_Arithmetic_Operators</span></span>](about_Arithmetic_Operators.md)

[<span data-ttu-id="c5317-267">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="c5317-267">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="c5317-268">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="c5317-268">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="c5317-269">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="c5317-269">about_Logical_Operators</span></span>](about_logical_operators.md)

[<span data-ttu-id="c5317-270">about_Operator_Precedence</span><span class="sxs-lookup"><span data-stu-id="c5317-270">about_Operator_Precedence</span></span>](about_operator_precedence.md)

[<span data-ttu-id="c5317-271">about_Type_Operators</span><span class="sxs-lookup"><span data-stu-id="c5317-271">about_Type_Operators</span></span>](about_Type_Operators.md)

[<span data-ttu-id="c5317-272">about_Pipeline_Chain_Operators</span><span class="sxs-lookup"><span data-stu-id="c5317-272">about_Pipeline_Chain_Operators</span></span>](about_Pipeline_Chain_Operators.md)

[<span data-ttu-id="c5317-273">about_Split</span><span class="sxs-lookup"><span data-stu-id="c5317-273">about_Split</span></span>](about_Split.md)

[<span data-ttu-id="c5317-274">about_Join</span><span class="sxs-lookup"><span data-stu-id="c5317-274">about_Join</span></span>](about_Join.md)

[<span data-ttu-id="c5317-275">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="c5317-275">about_Redirection</span></span>](about_Redirection.md)