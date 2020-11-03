---
description: Beschrijft een tref woord dat een afsluit fout verwerkt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_trap?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Trap
ms.openlocfilehash: 88c16066b96912faf38fd48a3bd2f84572707e4c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252204"
---
# <a name="about-trap"></a><span data-ttu-id="b42a5-104">Over trap</span><span class="sxs-lookup"><span data-stu-id="b42a5-104">About Trap</span></span>

## <a name="short-description"></a><span data-ttu-id="b42a5-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="b42a5-105">Short description</span></span>

<span data-ttu-id="b42a5-106">Beschrijft een tref woord dat een afsluit fout verwerkt.</span><span class="sxs-lookup"><span data-stu-id="b42a5-106">Describes a keyword that handles a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="b42a5-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="b42a5-107">Long description</span></span>

<span data-ttu-id="b42a5-108">Een afsluit fout zorgt ervoor dat een instructie niet kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b42a5-108">A terminating error stops a statement from running.</span></span> <span data-ttu-id="b42a5-109">Als Power shell geen afsluit fout op een of andere manier verwerkt, stopt Power shell ook met het uitvoeren van de functie of het script in de huidige pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b42a5-109">If PowerShell does not handle a terminating error in some way, PowerShell also stops running the function or script in the current pipeline.</span></span> <span data-ttu-id="b42a5-110">In andere talen, zoals C#, worden afsluit fouten ook wel uitzonde ringen genoemd.</span><span class="sxs-lookup"><span data-stu-id="b42a5-110">In other languages, such as C#, terminating errors are known as exceptions.</span></span>

<span data-ttu-id="b42a5-111">Met het `trap` sleutel woord wordt een lijst met instructies opgegeven die moeten worden uitgevoerd wanneer er een afsluit fout optreedt.</span><span class="sxs-lookup"><span data-stu-id="b42a5-111">The `trap` keyword specifies a list of statements to run when a terminating error occurs.</span></span> <span data-ttu-id="b42a5-112">`trap` instructies verwerken de afsluit fouten op de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="b42a5-112">`trap` statements handle the terminating errors in the following ways:</span></span>

- <span data-ttu-id="b42a5-113">De fout weer geven na het verwerken `trap` van het instructie blok en de uitvoering van het script of de functie die de bevat, voortzetten `trap` .</span><span class="sxs-lookup"><span data-stu-id="b42a5-113">Display the error after processing the `trap` statement block and continuing execution of the script or function containing the `trap`.</span></span> <span data-ttu-id="b42a5-114">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="b42a5-114">This is the default behavior.</span></span>

- <span data-ttu-id="b42a5-115">De fout weer geven en de uitvoering van het script of de functie die de `trap` gebruiken `break` in de-instructie bevat afbreken `trap` .</span><span class="sxs-lookup"><span data-stu-id="b42a5-115">Display the error and abort execution of the script or function containing the `trap` using `break` in the `trap` statement.</span></span>

- <span data-ttu-id="b42a5-116">Stilte de fout, maar ga door met het uitvoeren van het script of de functie die de `trap` door gebruikt `continue` in de- `trap` instructie.</span><span class="sxs-lookup"><span data-stu-id="b42a5-116">Silence the error, but continue execution of the script or function containing the `trap` by using `continue` in the `trap` statement.</span></span>

<span data-ttu-id="b42a5-117">De instructie lijst van `trap` kan meerdere voor waarden of functie aanroepen bevatten.</span><span class="sxs-lookup"><span data-stu-id="b42a5-117">The statement list of the `trap` can include multiple conditions or function calls.</span></span> <span data-ttu-id="b42a5-118">Een `trap` kan Logboeken schrijven, test omstandigheden of zelfs een ander programma uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b42a5-118">A `trap` can write logs, test conditions, or even run another program.</span></span>

### <a name="syntax"></a><span data-ttu-id="b42a5-119">Syntax</span><span class="sxs-lookup"><span data-stu-id="b42a5-119">Syntax</span></span>

<span data-ttu-id="b42a5-120">De `trap` instructie heeft de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="b42a5-120">The `trap` statement has the following syntax:</span></span>

```powershell
trap [[<error type>]] {<statement list>}
```

<span data-ttu-id="b42a5-121">De `trap` instructie bevat een lijst met instructies die moeten worden uitgevoerd wanneer er een afsluit fout optreedt.</span><span class="sxs-lookup"><span data-stu-id="b42a5-121">The `trap` statement includes a list of statements to run when a terminating error occurs.</span></span> <span data-ttu-id="b42a5-122">Een `trap` instructie bestaat uit het `trap` tref woord, eventueel gevolgd door een type-expressie, en het instructie blok met de lijst met instructies die moeten worden uitgevoerd wanneer een fout wordt onderschept.</span><span class="sxs-lookup"><span data-stu-id="b42a5-122">A `trap` statement consists of the `trap` keyword, optionally followed by a type expression, and the statement block containing the list of statements to run when an error is trapped.</span></span> <span data-ttu-id="b42a5-123">De type-expressie verfijnt de typen fouten die de `trap` vangsten opleveren.</span><span class="sxs-lookup"><span data-stu-id="b42a5-123">The type expression refines the types of errors the `trap` catches.</span></span>

<span data-ttu-id="b42a5-124">Een script of opdracht kan meerdere `trap` instructies hebben.</span><span class="sxs-lookup"><span data-stu-id="b42a5-124">A script or command can have multiple `trap` statements.</span></span> <span data-ttu-id="b42a5-125">`trap` instructies kunnen ergens in het script of de opdracht worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b42a5-125">`trap` statements can appear anywhere in the script or command.</span></span>

### <a name="trapping-all-terminating-errors"></a><span data-ttu-id="b42a5-126">Alle afsluit fouten worden overgevuld</span><span class="sxs-lookup"><span data-stu-id="b42a5-126">Trapping all terminating errors</span></span>

<span data-ttu-id="b42a5-127">Wanneer er een afsluit fout optreedt die niet op een andere manier wordt verwerkt in een script of opdracht, controleert Power shell op een `trap` instructie die de fout verwerkt.</span><span class="sxs-lookup"><span data-stu-id="b42a5-127">When a terminating error occurs that is not handled in another way in a script or command, PowerShell checks for a `trap` statement that handles the error.</span></span> <span data-ttu-id="b42a5-128">Als er een `trap` instructie aanwezig is, gaat Power shell door met het uitvoeren van het script of de opdracht in de `trap` instructie.</span><span class="sxs-lookup"><span data-stu-id="b42a5-128">If a `trap` statement is present, PowerShell continues running the script or command in the `trap` statement.</span></span>

<span data-ttu-id="b42a5-129">Het volgende voor beeld is een zeer eenvoudige `trap` instructie:</span><span class="sxs-lookup"><span data-stu-id="b42a5-129">The following example is a very simple `trap` statement:</span></span>

```powershell
trap {"Error found."}
```

<span data-ttu-id="b42a5-130">Deze `trap` instructie overlapt elke afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="b42a5-130">This `trap` statement traps any terminating error.</span></span>

<span data-ttu-id="b42a5-131">In het volgende voor beeld bevat de functie een niet-zin teken reeks die een runtime-fout veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="b42a5-131">In the following example, the function includes a nonsense string that causes a runtime error.</span></span>

```powershell
function TrapTest {
    trap {"Error found."}
    nonsenseString
}

TrapTest
```

<span data-ttu-id="b42a5-132">Als u deze functie uitvoert, wordt het volgende geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="b42a5-132">Running this function returns the following:</span></span>

```Output
Error found.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="b42a5-133">Het volgende voor beeld bevat een `trap` instructie waarmee de fout wordt weer gegeven met behulp van de `$_` Automatische variabele:</span><span class="sxs-lookup"><span data-stu-id="b42a5-133">The following example includes a `trap` statement that displays the error by using the `$_` automatic variable:</span></span>

```powershell
function TrapTest {
    trap {"Error found: $_"}
    nonsenseString
}

TrapTest
```

<span data-ttu-id="b42a5-134">Als deze versie van de functie wordt uitgevoerd, wordt het volgende geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="b42a5-134">Running this version of the function returns the following:</span></span>

```Output
Error found: The term 'nonsenseString' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the
name, or if a path was included, verify that the path is correct and try again.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

> [!IMPORTANT]
> <span data-ttu-id="b42a5-135">`trap` instructies kunnen ergens binnen een bepaald bereik worden gedefinieerd, maar altijd gelden voor alle instructies in dat bereik.</span><span class="sxs-lookup"><span data-stu-id="b42a5-135">`trap` statements may be defined anywhere within a given scope, but always apply to all statements in that scope.</span></span> <span data-ttu-id="b42a5-136">Tijdens runtime `trap` worden instructies in een blok gedefinieerd voordat andere instructies worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b42a5-136">At runtime, `trap` statements in a block are defined before any other statements are executed.</span></span> <span data-ttu-id="b42a5-137">In Java script wordt dit ' [hijsing](https://wikipedia.org/wiki/JavaScript_syntax#hoisting)' genoemd.</span><span class="sxs-lookup"><span data-stu-id="b42a5-137">In JavaScript, this is known as [hoisting](https://wikipedia.org/wiki/JavaScript_syntax#hoisting).</span></span> <span data-ttu-id="b42a5-138">Dit betekent dat de `trap` instructies van toepassing zijn op alle-instructies in dat blok, zelfs als de uitvoering niet is gevorderd voorbij het punt waarop ze zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b42a5-138">This means that `trap` statements apply to all statements in that block even if execution has not advanced past the point at which they are defined.</span></span> <span data-ttu-id="b42a5-139">Als u bijvoorbeeld een `trap` aan het einde van een script definieert en er een fout optreedt in de eerste instructie, wordt er nog steeds geactiveerd `trap` .</span><span class="sxs-lookup"><span data-stu-id="b42a5-139">For example, defining a `trap` at the end of a script and throwing an error in the first statement still triggers that `trap`.</span></span>

### <a name="trapping-specific-errors"></a><span data-ttu-id="b42a5-140">Specifieke fouten overvullen</span><span class="sxs-lookup"><span data-stu-id="b42a5-140">Trapping specific errors</span></span>

<span data-ttu-id="b42a5-141">Een script of opdracht kan meerdere `trap` instructies hebben.</span><span class="sxs-lookup"><span data-stu-id="b42a5-141">A script or command can have multiple `trap` statements.</span></span> <span data-ttu-id="b42a5-142">A `trap` kan worden gedefinieerd om specifieke fouten te verwerken.</span><span class="sxs-lookup"><span data-stu-id="b42a5-142">A `trap` can be defined to handle specific errors.</span></span>

<span data-ttu-id="b42a5-143">Het volgende voor beeld is een `trap` instructie waarmee de specifieke fout **CommandNotFoundException** wordt onderschept:</span><span class="sxs-lookup"><span data-stu-id="b42a5-143">The following example is a `trap` statement that traps the specific error **CommandNotFoundException** :</span></span>

```powershell
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
```

<span data-ttu-id="b42a5-144">Wanneer een functie of script een teken reeks aantreft die niet overeenkomt met een bekende opdracht, wordt in deze `trap` instructie de teken reeks "opdracht fout onderschept" weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b42a5-144">When a function or script encounters a string that does not match a known command, this `trap` statement displays the "Command error trapped" string.</span></span>
<span data-ttu-id="b42a5-145">Na het uitvoeren van de `trap` instructie lijst, schrijft Power shell het fout object naar de fout stroom en wordt het script voortgezet.</span><span class="sxs-lookup"><span data-stu-id="b42a5-145">After running the `trap` statement list, PowerShell writes the error object to the error stream and then continues the script.</span></span>

<span data-ttu-id="b42a5-146">Power shell gebruikt .NET-uitzonderings typen.</span><span class="sxs-lookup"><span data-stu-id="b42a5-146">PowerShell uses .NET exception types.</span></span> <span data-ttu-id="b42a5-147">In het volgende voor beeld wordt het **systeem. uitzonderings** fout type opgegeven:</span><span class="sxs-lookup"><span data-stu-id="b42a5-147">The following example specifies the **System.Exception** error type:</span></span>

```powershell
trap [System.Exception] {"An error trapped"}
```

<span data-ttu-id="b42a5-148">Het **CommandNotFoundException** -fout type neemt over van het type **System. Exception** .</span><span class="sxs-lookup"><span data-stu-id="b42a5-148">The **CommandNotFoundException** error type inherits from the **System.Exception** type.</span></span> <span data-ttu-id="b42a5-149">Met deze instructie wordt een fout onderschept die wordt gemaakt door een onbekende opdracht.</span><span class="sxs-lookup"><span data-stu-id="b42a5-149">This statement traps an error that is created by an unknown command.</span></span> <span data-ttu-id="b42a5-150">Ook worden andere fout typen onderschept.</span><span class="sxs-lookup"><span data-stu-id="b42a5-150">It also traps other error types.</span></span>

<span data-ttu-id="b42a5-151">U kunt meer dan één `trap` instructie in een script hebben.</span><span class="sxs-lookup"><span data-stu-id="b42a5-151">You can have more than one `trap` statement in a script.</span></span> <span data-ttu-id="b42a5-152">Elk fout type kan slechts door één instructie worden getrapt `trap` .</span><span class="sxs-lookup"><span data-stu-id="b42a5-152">Each error type can be trapped by only one `trap` statement.</span></span> <span data-ttu-id="b42a5-153">Wanneer er een afsluit fout optreedt, zoekt Power shell naar de `trap` met de meest specifieke overeenkomst, te beginnen met het huidige bereik van de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="b42a5-153">When a terminating error occurs, PowerShell searches for the `trap` with the most specific match, starting in the current scope of execution.</span></span>

<span data-ttu-id="b42a5-154">Het volgende script voorbeeld bevat een fout.</span><span class="sxs-lookup"><span data-stu-id="b42a5-154">The following script example contains an error.</span></span> <span data-ttu-id="b42a5-155">Het script bevat een algemene `trap` instructie waarmee elke afsluit fout wordt onderschept en een specifieke `trap` instructie die het type **CommandNotFoundException** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="b42a5-155">The script includes a general `trap` statement that traps any terminating error and a specific `trap` statement that specifies the **CommandNotFoundException** type.</span></span>

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException] {
  "Command error trapped"
}
nonsenseString
```

<span data-ttu-id="b42a5-156">Als u dit script uitvoert, wordt het volgende resultaat gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="b42a5-156">Running this script produces the following result:</span></span>

```Output
Command error trapped
nonsenseString:
Line |
   5 |  nonsenseString
     |  ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="b42a5-157">Omdat Power shell geen nonsenseString herkent als een cmdlet of een ander item, wordt een **CommandNotFoundException** -fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b42a5-157">Because PowerShell does not recognize "nonsenseString" as a cmdlet or other item, it returns a **CommandNotFoundException** error.</span></span> <span data-ttu-id="b42a5-158">Deze afsluit fout wordt getrapt door de specifieke `trap` instructie.</span><span class="sxs-lookup"><span data-stu-id="b42a5-158">This terminating error is trapped by the specific `trap` statement.</span></span>

<span data-ttu-id="b42a5-159">Het volgende script voorbeeld bevat dezelfde `trap` instructies met een andere fout:</span><span class="sxs-lookup"><span data-stu-id="b42a5-159">The following script example contains the same `trap` statements with a different error:</span></span>

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
1/$null
```

<span data-ttu-id="b42a5-160">Als u dit script uitvoert, wordt het volgende resultaat gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="b42a5-160">Running this script produces the following result:</span></span>

```Output
Other terminating error trapped
RuntimeException:
Line |
   4 |  1/$null
     |  ~~~~~~~
     | Attempted to divide by zero.
```

<span data-ttu-id="b42a5-161">Bij de poging om door nul te delen, wordt er geen **CommandNotFoundException** -fout gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b42a5-161">The attempt to divide by zero does not create a **CommandNotFoundException** error.</span></span> <span data-ttu-id="b42a5-162">In plaats daarvan wordt deze fout overlapt door de andere `trap` instructie, wat een afsluit fout overlapt.</span><span class="sxs-lookup"><span data-stu-id="b42a5-162">Instead, that error is trapped by the other `trap` statement, which traps any terminating error.</span></span>

### <a name="trapping-errors-and-scope"></a><span data-ttu-id="b42a5-163">Trap fouten en bereik</span><span class="sxs-lookup"><span data-stu-id="b42a5-163">Trapping errors and scope</span></span>

<span data-ttu-id="b42a5-164">Als een afsluit fout optreedt in hetzelfde bereik als de `trap` instructie, voert Power shell de lijst met instructies uit die zijn gedefinieerd door `trap` .</span><span class="sxs-lookup"><span data-stu-id="b42a5-164">If a terminating error occurs in the same scope as the `trap` statement, PowerShell runs the list of statements defined by the `trap`.</span></span> <span data-ttu-id="b42a5-165">De uitvoering gaat na de fout verder met de instructie.</span><span class="sxs-lookup"><span data-stu-id="b42a5-165">Execution continues at the statement after the error.</span></span> <span data-ttu-id="b42a5-166">Als de `trap` instructie een andere scope heeft dan de fout, wordt de uitvoering voortgezet bij de volgende instructie die zich in hetzelfde bereik bevindt als de- `trap` instructie.</span><span class="sxs-lookup"><span data-stu-id="b42a5-166">If the `trap` statement is in a different scope from the error, execution continues at the next statement that is in the same scope as the `trap` statement.</span></span>

<span data-ttu-id="b42a5-167">Als er bijvoorbeeld een fout optreedt in een functie en de `trap` instructie zich in de functie bevindt, wordt het script voortgezet bij de volgende instructie.</span><span class="sxs-lookup"><span data-stu-id="b42a5-167">For example, if an error occurs in a function, and the `trap` statement is in the function, the script continues at the next statement.</span></span> <span data-ttu-id="b42a5-168">Het volgende script bevat een fout en een `trap` instructie:</span><span class="sxs-lookup"><span data-stu-id="b42a5-168">The following script contains an error and a `trap` statement:</span></span>

```powershell
function function1 {
    trap { "An error: " }
    NonsenseString
    "function1 was completed"
}

function1
```

<span data-ttu-id="b42a5-169">Als u dit script uitvoert, wordt het volgende resultaat gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="b42a5-169">Running this script produces the following result:</span></span>

```Output
An error:
NonsenseString:
Line |
   3 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
function1 was completed
```

<span data-ttu-id="b42a5-170">De `trap` instructie in de functie overtrapt de fout.</span><span class="sxs-lookup"><span data-stu-id="b42a5-170">The `trap` statement in the function traps the error.</span></span> <span data-ttu-id="b42a5-171">Na het weer geven van het bericht, wordt de uitvoering van de functie hervat met Power shell.</span><span class="sxs-lookup"><span data-stu-id="b42a5-171">After displaying the message, PowerShell resumes running the function.</span></span> <span data-ttu-id="b42a5-172">Opmerking `Function1` is voltooid.</span><span class="sxs-lookup"><span data-stu-id="b42a5-172">Note that `Function1` was completed.</span></span>

<span data-ttu-id="b42a5-173">Vergelijk dit met het volgende voor beeld, dat dezelfde fout en `trap` instructie heeft.</span><span class="sxs-lookup"><span data-stu-id="b42a5-173">Compare this with the following example, which has the same error and `trap` statement.</span></span> <span data-ttu-id="b42a5-174">In dit voor beeld `trap` vindt de instructie plaats buiten de functie:</span><span class="sxs-lookup"><span data-stu-id="b42a5-174">In this example, the `trap` statement occurs outside the function:</span></span>

```powershell
function function2 {
    NonsenseString
    "function2 was completed"
}

trap { "An error: " }

function2
```

<span data-ttu-id="b42a5-175">Het uitvoeren van de `Function2` functie levert het volgende resultaat:</span><span class="sxs-lookup"><span data-stu-id="b42a5-175">Running the `Function2` function produces the following result:</span></span>

```Output
An error:
NonsenseString:
Line |
   2 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="b42a5-176">In dit voor beeld is de opdracht ' function2 is voltooid ' niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b42a5-176">In this example, the "function2 was completed" command was not run.</span></span> <span data-ttu-id="b42a5-177">In beide voor beelden treedt de afsluit fout op in de functie.</span><span class="sxs-lookup"><span data-stu-id="b42a5-177">In both examples, the terminating error occurs within the function.</span></span> <span data-ttu-id="b42a5-178">In dit voor beeld `trap` is de instructie echter buiten de functie.</span><span class="sxs-lookup"><span data-stu-id="b42a5-178">In this example, however, the `trap` statement is outside the function.</span></span> <span data-ttu-id="b42a5-179">Power shell gaat niet terug naar de functie nadat de `trap` instructie is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b42a5-179">PowerShell does not go back into the function after the `trap` statement runs.</span></span>

> [!CAUTION]
> <span data-ttu-id="b42a5-180">Wanneer meerdere traps voor dezelfde fout voorwaarde worden gedefinieerd, wordt de eerste `trap` gedefinieerde lexicale (hoogste in het bereik) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b42a5-180">When multiple traps are defined for the same error condition, the first `trap` defined lexically (highest in the scope) is used.</span></span>

<span data-ttu-id="b42a5-181">In het volgende voor beeld wordt alleen de `trap` met ' Whoops 1 ' uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b42a5-181">In the following example, only the `trap` with "whoops 1" is run.</span></span>

```powershell
Remove-Item -ErrorAction Stop ThisFileDoesNotExist
trap { "whoops 1"; continue }
trap { "whoops 2"; continue }
```

> [!IMPORTANT]
> <span data-ttu-id="b42a5-182">Een trap-instructie ligt binnen het bereik waar deze zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="b42a5-182">A Trap statement is scoped to where it compiles.</span></span> <span data-ttu-id="b42a5-183">Als u een `trap` -instructie in een Function-of dot-script hebt, worden alle-instructies verwijderd wanneer het script van de functie of het punt wordt afgesloten `trap` .</span><span class="sxs-lookup"><span data-stu-id="b42a5-183">If you have a `trap` statement inside a function or dot sourced script, when the function or dot sourced script exits, all `trap` statements inside are removed.</span></span>

### <a name="using-the-break-and-continue-keywords"></a><span data-ttu-id="b42a5-184">De tref woorden voor onderbreken en door lopen gebruiken</span><span class="sxs-lookup"><span data-stu-id="b42a5-184">Using the break and continue keywords</span></span>

<span data-ttu-id="b42a5-185">U kunt de `break` en `continue` tref woorden in een `trap` instructie gebruiken om te bepalen of een script of opdracht wordt uitgevoerd na een afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="b42a5-185">You can use the `break` and `continue` keywords in a `trap` statement to determine whether a script or command continues to run after a terminating error.</span></span>

<span data-ttu-id="b42a5-186">Als u een instructie opneemt `break` in een `trap` instructie lijst, stopt Power shell de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="b42a5-186">If you include a `break` statement in a `trap` statement list, PowerShell stops the function or script.</span></span> <span data-ttu-id="b42a5-187">De volgende voorbeeld functie maakt gebruik `break` van het sleutel woord in een `trap` instructie:</span><span class="sxs-lookup"><span data-stu-id="b42a5-187">The following sample function uses the `break` keyword in a `trap` statement:</span></span>

```powershell
function break_example {
    trap {
        "Error trapped"
        break
    }
    1/$null
    "Function completed."
}

break_example
```

```Output
Error trapped
ParentContainsErrorRecordException:
Line |
   6 |      1/$null
     |      ~~~~~~~
     | Attempted to divide by zero.
```

<span data-ttu-id="b42a5-188">Omdat de `trap` instructie het `break` tref woord bevat, wordt de functie niet verder uitgevoerd en wordt de regel ' functie voltooid ' niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b42a5-188">Because the `trap` statement included the `break` keyword, the function does not continue to run, and the "Function completed" line is not run.</span></span>

<span data-ttu-id="b42a5-189">Als u een `continue` sleutel woord in een instructie opneemt `trap` , wordt Power shell hervat na de instructie die de fout heeft veroorzaakt, net zoals zonder `break` of `continue` .</span><span class="sxs-lookup"><span data-stu-id="b42a5-189">If you include a `continue` keyword in a `trap` statement, PowerShell resumes after the statement that caused the error, just as it would without `break` or `continue`.</span></span> <span data-ttu-id="b42a5-190">Met het `continue` tref woord schrijft Power shell echter geen fout naar de fout stroom.</span><span class="sxs-lookup"><span data-stu-id="b42a5-190">With the `continue` keyword, however, PowerShell does not write an error to the error stream.</span></span>

<span data-ttu-id="b42a5-191">De volgende voorbeeld functie maakt gebruik `continue` van het sleutel woord in een `trap` instructie:</span><span class="sxs-lookup"><span data-stu-id="b42a5-191">The following sample function uses the `continue` keyword in a `trap` statement:</span></span>

```powershell
function continue_example {
    trap {
        "Error trapped"
        continue
    }
    1/$null
    "Function completed."
}

continue_example
```

```Output
Error trapped
Function completed.
```

<span data-ttu-id="b42a5-192">De functie wordt hervat nadat de fout is getrapt en de instructie ' functie voltooid ' wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b42a5-192">The function resumes after the error is trapped, and the "Function completed" statement runs.</span></span> <span data-ttu-id="b42a5-193">Er wordt geen fout naar de fout stroom geschreven.</span><span class="sxs-lookup"><span data-stu-id="b42a5-193">No error is written to the error stream.</span></span>

## <a name="notes"></a><span data-ttu-id="b42a5-194">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b42a5-194">Notes</span></span>

<span data-ttu-id="b42a5-195">`trap` instructies bieden een eenvoudige manier om ervoor te zorgen dat alle afsluit fouten binnen een bereik worden afgehandeld.</span><span class="sxs-lookup"><span data-stu-id="b42a5-195">`trap` statements provide a simple way to broadly ensure all terminating errors within a scope are handled.</span></span> <span data-ttu-id="b42a5-196">Gebruik `try` / `catch` blokken waarin traps worden gedefinieerd met behulp van-instructies voor meer nauw keurige fout afhandeling `catch` .</span><span class="sxs-lookup"><span data-stu-id="b42a5-196">For more finer-grained error handling, use `try`/`catch` blocks where traps are defined using `catch` statements.</span></span> <span data-ttu-id="b42a5-197">De `catch` instructies zijn alleen van toepassing op de code in de bijbehorende `try` instructie.</span><span class="sxs-lookup"><span data-stu-id="b42a5-197">The `catch` statements only apply to the code inside the associated `try` statement.</span></span> <span data-ttu-id="b42a5-198">Zie [about_Try_Catch_Finally](about_Try_Catch_Finally.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b42a5-198">For more information, see [about_Try_Catch_Finally](about_Try_Catch_Finally.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b42a5-199">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b42a5-199">See also</span></span>

[<span data-ttu-id="b42a5-200">about_Break</span><span class="sxs-lookup"><span data-stu-id="b42a5-200">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="b42a5-201">about_Continue</span><span class="sxs-lookup"><span data-stu-id="b42a5-201">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="b42a5-202">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="b42a5-202">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="b42a5-203">about_Throw</span><span class="sxs-lookup"><span data-stu-id="b42a5-203">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="b42a5-204">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="b42a5-204">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
