---
description: Hierin wordt uitgelegd hoe u met een switch meerdere `If` instructies kunt verwerken.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 12a4b8412b0c490372ea73a90855e333b6bbfbf3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252063"
---
# <a name="about-switch"></a><span data-ttu-id="f26db-104">Over Switch</span><span class="sxs-lookup"><span data-stu-id="f26db-104">About Switch</span></span>

## <a name="short-description"></a><span data-ttu-id="f26db-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="f26db-105">Short description</span></span>
<span data-ttu-id="f26db-106">Hierin wordt uitgelegd hoe u met een switch meerdere `If` instructies kunt verwerken.</span><span class="sxs-lookup"><span data-stu-id="f26db-106">Explains how to use a switch to handle multiple `If` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="f26db-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="f26db-107">Long description</span></span>

<span data-ttu-id="f26db-108">Als u een voor waarde in een script of functie wilt controleren, gebruikt u een- `If` instructie.</span><span class="sxs-lookup"><span data-stu-id="f26db-108">To check a condition in a script or function, use an `If` statement.</span></span> <span data-ttu-id="f26db-109">De `If` instructie kan veel soorten voor waarden controleren, met inbegrip van de waarde van variabelen en de eigenschappen van de objecten.</span><span class="sxs-lookup"><span data-stu-id="f26db-109">The `If` statement can check many types of conditions, including the value of variables and the properties of objects.</span></span>

<span data-ttu-id="f26db-110">Als u meerdere voor waarden wilt controleren, gebruikt u een- `Switch` instructie.</span><span class="sxs-lookup"><span data-stu-id="f26db-110">To check multiple conditions, use a `Switch` statement.</span></span> <span data-ttu-id="f26db-111">De `Switch` instructie is gelijk aan een reeks `If` instructies, maar is eenvoudiger.</span><span class="sxs-lookup"><span data-stu-id="f26db-111">The `Switch` statement is equivalent to a series of `If` statements, but it is simpler.</span></span> <span data-ttu-id="f26db-112">De `Switch` instructie vermeldt elke voor waarde en een optionele actie.</span><span class="sxs-lookup"><span data-stu-id="f26db-112">The `Switch` statement lists each condition and an optional action.</span></span> <span data-ttu-id="f26db-113">Als een voor waarde wordt opgehaald, wordt de actie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-113">If a condition obtains, the action is performed.</span></span>

<span data-ttu-id="f26db-114">De- `Switch` instructie kan de `$_` en `$switch` automatische variabelen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f26db-114">The `Switch` statement can use the `$_` and `$switch` automatic variables.</span></span> <span data-ttu-id="f26db-115">Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f26db-115">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="f26db-116">Een Basic- `Switch` instructie heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="f26db-116">A basic `Switch` statement has the following format:</span></span>

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

<span data-ttu-id="f26db-117">De volgende `Switch` instructie vergelijkt bijvoorbeeld de test waarde, 3, op elk van de voor waarden.</span><span class="sxs-lookup"><span data-stu-id="f26db-117">For example, the following `Switch` statement compares the test value, 3, to each of the conditions.</span></span> <span data-ttu-id="f26db-118">Wanneer de test waarde overeenkomt met de voor waarde, wordt de actie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-118">When the test value matches the condition, the action is performed.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
}
```

```Output
It is three.
```

<span data-ttu-id="f26db-119">In dit eenvoudige voor beeld wordt de waarde vergeleken met elke voor waarde in de lijst, zelfs als er een overeenkomst is voor de waarde 3.</span><span class="sxs-lookup"><span data-stu-id="f26db-119">In this simple example, the value is compared to each condition in the list, even though there is a match for the value 3.</span></span> <span data-ttu-id="f26db-120">De volgende `Switch` instructie heeft twee voor waarden voor de waarde 3.</span><span class="sxs-lookup"><span data-stu-id="f26db-120">The following `Switch` statement has two conditions for a value of 3.</span></span> <span data-ttu-id="f26db-121">Er wordt gedemonstreerd dat alle voor waarden standaard worden getest.</span><span class="sxs-lookup"><span data-stu-id="f26db-121">It demonstrates that, by default, all conditions are tested.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
Three again.
```

<span data-ttu-id="f26db-122">`Switch`Gebruik de instructie om de te stoppen om te vergelijken na een overeenkomst `Break` .</span><span class="sxs-lookup"><span data-stu-id="f26db-122">To direct the `Switch` to stop comparing after a match, use the `Break` statement.</span></span> <span data-ttu-id="f26db-123">De instructie `Break` beëindigt de `Switch` instructie.</span><span class="sxs-lookup"><span data-stu-id="f26db-123">The `Break` statement terminates the `Switch` statement.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."; Break}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
```

<span data-ttu-id="f26db-124">Als de test waarde een verzameling is, zoals een matrix, wordt elk item in de verzameling geëvalueerd in de volg orde waarin deze wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f26db-124">If the test value is a collection, such as an array, each item in the collection is evaluated in the order in which it appears.</span></span> <span data-ttu-id="f26db-125">In de volgende voor beelden wordt 4 en vervolgens 2 geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-125">The following examples evaluates 4 and then 2.</span></span>

```powershell
switch (4, 2)
{
    1 {"It is one." }
    2 {"It is two." }
    3 {"It is three." }
    4 {"It is four." }
    3 {"Three again."}
}
```

```Output
It is four.
It is two.
```

<span data-ttu-id="f26db-126">Alle `Break` instructies zijn van toepassing op de verzameling, niet op elke waarde, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="f26db-126">Any `Break` statements apply to the collection, not to each value, as shown in the following example.</span></span> <span data-ttu-id="f26db-127">De `Switch` instructie wordt beëindigd door de `Break` instructie in de voor waarde van de waarde 4.</span><span class="sxs-lookup"><span data-stu-id="f26db-127">The `Switch` statement is terminated by the `Break` statement in the condition of value 4.</span></span>

```powershell
switch (4, 2)
{
    1 {"It is one."; Break}
    2 {"It is two." ; Break }
    3 {"It is three." ; Break }
    4 {"It is four." ; Break }
    3 {"Three again."}
}
```

```Output
It is four.
```

### <a name="syntax"></a><span data-ttu-id="f26db-128">Syntax</span><span class="sxs-lookup"><span data-stu-id="f26db-128">Syntax</span></span>

<span data-ttu-id="f26db-129">De syntaxis van de `Switch` instructie complete is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f26db-129">The complete `Switch` statement syntax is as follows:</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="f26db-130">of</span><span class="sxs-lookup"><span data-stu-id="f26db-130">or</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="f26db-131">Als er geen para meters worden gebruikt, `Switch` werkt hetzelfde als met de **exacte** para meter.</span><span class="sxs-lookup"><span data-stu-id="f26db-131">If no parameters are used, `Switch` behaves the same as using the **Exact** parameter.</span></span> <span data-ttu-id="f26db-132">Er wordt een niet-hoofdletter gevoelige overeenkomst voor de waarde uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-132">It performs a case-insensitive match for the value.</span></span> <span data-ttu-id="f26db-133">Als de waarde een verzameling is, wordt elk element geëvalueerd in de volg orde waarin het wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f26db-133">If the value is a collection, each element is evaluated in the order in which it appears.</span></span>

<span data-ttu-id="f26db-134">De `Switch` instructie moet ten minste één voorwaarde instructie bevatten.</span><span class="sxs-lookup"><span data-stu-id="f26db-134">The `Switch` statement must include at least one condition statement.</span></span>

<span data-ttu-id="f26db-135">De `Default` component wordt geactiveerd wanneer de waarde niet overeenkomt met een van de voor waarden.</span><span class="sxs-lookup"><span data-stu-id="f26db-135">The `Default` clause is triggered when the value does not match any of the conditions.</span></span> <span data-ttu-id="f26db-136">Deze is gelijk aan een- `Else` component in een- `If` instructie.</span><span class="sxs-lookup"><span data-stu-id="f26db-136">It is equivalent to an `Else` clause in an `If` statement.</span></span> <span data-ttu-id="f26db-137">`Default`In elke instructie is slechts één component toegestaan `Switch` .</span><span class="sxs-lookup"><span data-stu-id="f26db-137">Only one `Default` clause is permitted in each `Switch` statement.</span></span>

<span data-ttu-id="f26db-138">`Switch` heeft de volgende para meters:</span><span class="sxs-lookup"><span data-stu-id="f26db-138">`Switch` has the following parameters:</span></span>

- <span data-ttu-id="f26db-139">**Joker** teken: geeft aan dat de voor waarde een Joker teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="f26db-139">**Wildcard** - Indicates that the condition is a wildcard string.</span></span> <span data-ttu-id="f26db-140">Als de match-component geen teken reeks is, wordt de para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-140">If the match clause is not a string, the parameter is ignored.</span></span> <span data-ttu-id="f26db-141">De vergelijking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="f26db-141">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="f26db-142">**Exact** : geeft aan dat de match-component als deze een teken reeks is, exact moet overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="f26db-142">**Exact** - Indicates that the match clause, if it is a string, must match exactly.</span></span> <span data-ttu-id="f26db-143">Als de match-component geen teken reeks is, wordt deze para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-143">If the match clause is not a string, this parameter is ignored.</span></span> <span data-ttu-id="f26db-144">De vergelijking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="f26db-144">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="f26db-145">**CaseSensitive** : Hiermee wordt een hoofdletter gevoelige overeenkomst uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-145">**CaseSensitive** - Performs a case-sensitive match.</span></span> <span data-ttu-id="f26db-146">Als de match-component geen teken reeks is, wordt deze para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-146">If the match clause is not a string, this parameter is ignored.</span></span>
- <span data-ttu-id="f26db-147">**File** -voert invoer uit vanuit een bestand in plaats van een waarde-instructie.</span><span class="sxs-lookup"><span data-stu-id="f26db-147">**File** - Takes input from a file rather than a value statement.</span></span> <span data-ttu-id="f26db-148">Als er meerdere **Bestands** parameters zijn opgenomen, wordt alleen de laatste gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f26db-148">If multiple **File** parameters are included, only the last one is used.</span></span> <span data-ttu-id="f26db-149">Elke regel van het bestand wordt gelezen en geëvalueerd door de `Switch` instructie.</span><span class="sxs-lookup"><span data-stu-id="f26db-149">Each line of the file is read and evaluated by the `Switch` statement.</span></span> <span data-ttu-id="f26db-150">De vergelijking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="f26db-150">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="f26db-151">**Regex** -voert een reguliere expressie die overeenkomt met de waarde aan de voor waarde.</span><span class="sxs-lookup"><span data-stu-id="f26db-151">**Regex** - Performs regular expression matching of the value to the condition.</span></span> <span data-ttu-id="f26db-152">Als de match-component geen teken reeks is, wordt deze para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-152">If the match clause is not a string, this parameter is ignored.</span></span>
  <span data-ttu-id="f26db-153">De vergelijking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="f26db-153">The comparison is case-insensitive.</span></span> <span data-ttu-id="f26db-154">De `$matches` Automatische variabele is beschikbaar voor gebruik binnen het overeenkomende instructie blok.</span><span class="sxs-lookup"><span data-stu-id="f26db-154">The `$matches` automatic variable is available for use within the matching statement block.</span></span>

> [!NOTE]
> <span data-ttu-id="f26db-155">Wanneer er conflicterende waarden worden opgegeven, zoals **regex** en **Joker teken** , heeft de laatste para meter prioriteit en worden alle conflicterende para meters genegeerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-155">When specifying conflicting values, like **Regex** and **Wildcard** , the last parameter specified takes precedence, and all conflicting parameters are ignored.</span></span> <span data-ttu-id="f26db-156">Er zijn ook meerdere exemplaren van para meters toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f26db-156">Multiple instances of parameters are also permitted.</span></span> <span data-ttu-id="f26db-157">Alleen de laatste para meter die wordt gebruikt, is echter effectief.</span><span class="sxs-lookup"><span data-stu-id="f26db-157">However, only the last parameter used is effective.</span></span>

<span data-ttu-id="f26db-158">In dit voor beeld wordt een object dat geen teken reeks of numerieke gegevens is door gegeven aan de `Switch` .</span><span class="sxs-lookup"><span data-stu-id="f26db-158">In this example, an object that's not a string or numerical data is passed to the `Switch`.</span></span> <span data-ttu-id="f26db-159">`Switch`Hiermee wordt een teken reeks afgedwongen voor het object en wordt het resultaat geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-159">The `Switch` performs a string coercion on the object and evaluates the outcome.</span></span>

```powershell
$test = @{
    Test  = 'test'
    Test2 = 'test2'
}

$test.ToString()

switch -Exact ($test)
{
    'System.Collections.Hashtable'
    {
        'Hashtable string coercion'
    }
    'test'
    {
        'Hashtable value'
    }
}
```

```Output
System.Collections.Hashtable
Hashtable string coercion
```

<span data-ttu-id="f26db-160">In dit voor beeld is er geen overeenkomende case, dus er is geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f26db-160">In this example, there is no matching case so there is no output.</span></span>

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
}
```

<span data-ttu-id="f26db-161">Door de component toe te voegen `Default` , kunt u een actie uitvoeren wanneer er geen andere voor waarden slagen.</span><span class="sxs-lookup"><span data-stu-id="f26db-161">By adding the `Default` clause, you can perform an action when no other conditions succeed.</span></span>

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
    Default {
        "No matches"
    }
}
```

```Output
No matches
```

<span data-ttu-id="f26db-162">Als u wilt dat het woord ' veer tien ' overeenkomt met een aanvraag, moet u de `-Wildcard` `-Regex` para meter or gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f26db-162">For the word "fourteen" to match a case you must use the `-Wildcard` or `-Regex` parameter.</span></span>

```powershell
   PS> switch -Wildcard ("fourteen")
       {
           1 {"It is one."; Break}
           2 {"It is two."; Break}
           3 {"It is three."; Break}
           4 {"It is four."; Break}
           "fo*" {"That's too many."}
       }
 ```

```Output
That's too many.
```

<span data-ttu-id="f26db-163">In het volgende voor beeld wordt de `-Regex` para meter gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f26db-163">The following example uses the `-Regex` parameter.</span></span>

```powershell
$target = 'https://bing.com'
switch -Regex ($target)
{
    '^ftp\://.*$' { "$_ is an ftp address"; Break }
    '^\w+@\w+\.com|edu|org$' { "$_ is an email address"; Break }
    '^(http[s]?)\://.*$' { "$_ is a web address that uses $($matches[1])"; Break }
}
```

```Output
https://bing.com is a web address that uses https
```

<span data-ttu-id="f26db-164">De voor waarde van een switch instructie kan bestaan uit:</span><span class="sxs-lookup"><span data-stu-id="f26db-164">A Switch statement condition may be either:</span></span>

- <span data-ttu-id="f26db-165">Een expressie waarvan de waarde wordt vergeleken met de invoer waarde</span><span class="sxs-lookup"><span data-stu-id="f26db-165">An expression whose value is compared to the input value</span></span>
- <span data-ttu-id="f26db-166">Een script blok dat moet worden geretourneerd `$true` als aan een voor waarde wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="f26db-166">A script block which should return `$true` if a condition is met.</span></span>

<span data-ttu-id="f26db-167">De `$_` Automatische variabele bevat de waarde die is door gegeven aan de switch-instructie en is beschikbaar voor evaluatie en gebruik binnen het bereik van de voor waarden-instructies.</span><span class="sxs-lookup"><span data-stu-id="f26db-167">The `$_` automatic variable contains the value passed to the switch statement and is available for evaluation and use within the scope of the condition statements.</span></span>

<span data-ttu-id="f26db-168">De actie voor elke voor waarde is onafhankelijk van de acties in andere omstandigheden.</span><span class="sxs-lookup"><span data-stu-id="f26db-168">The action for each condition is independent of the actions in other conditions.</span></span>

<span data-ttu-id="f26db-169">In het volgende voor beeld wordt het gebruik van script blokken als instructie voorwaarden gedemonstreerd `Switch` .</span><span class="sxs-lookup"><span data-stu-id="f26db-169">The following example demonstrates the use of script blocks as `Switch` statement conditions.</span></span>

```powershell
switch ("Test")
{
    {$_ -is [String]} {
        "Found a string"
    }
    "Test" {
        "This $_ executes as well"
    }
}
```

```Output
Found a string
This Test executes as well
```

<span data-ttu-id="f26db-170">Als de waarde overeenkomt met meerdere voor waarden, wordt de actie voor elke voor waarde uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f26db-170">If the value matches multiple conditions, the action for each condition is executed.</span></span> <span data-ttu-id="f26db-171">Gebruik de `Break` tref woorden of om dit gedrag te wijzigen `Continue` .</span><span class="sxs-lookup"><span data-stu-id="f26db-171">To change this behavior, use the `Break` or `Continue` keywords.</span></span>

<span data-ttu-id="f26db-172">Het `Break` sleutel woord stopt met de verwerking en sluit de `Switch` instructie af.</span><span class="sxs-lookup"><span data-stu-id="f26db-172">The `Break` keyword stops processing and exits the `Switch` statement.</span></span>

<span data-ttu-id="f26db-173">Het `Continue` sleutel woord stopt met het verwerken van de huidige waarde, maar gaat verder met de verwerking van alle volgende waarden.</span><span class="sxs-lookup"><span data-stu-id="f26db-173">The `Continue` keyword stops processing the current value, but continues processing any subsequent values.</span></span>

<span data-ttu-id="f26db-174">In het volgende voor beeld wordt een matrix met getallen verwerkt en wordt weer gegeven als ze oneven of even zijn.</span><span class="sxs-lookup"><span data-stu-id="f26db-174">The following example processes an array of numbers and displays if they are odd or even.</span></span> <span data-ttu-id="f26db-175">Negatieve getallen worden overgeslagen met het `Continue` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="f26db-175">Negative numbers are skipped with the `Continue` keyword.</span></span> <span data-ttu-id="f26db-176">Als er een niet-nummer wordt aangetroffen, wordt de uitvoering beëindigd met het `Break` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="f26db-176">If a non-number is encountered, execution is terminated with the `Break` keyword.</span></span>

```powershell
switch (1,4,-1,3,"Hello",2,1)
{
    {$_ -lt 0} { Continue }
    {$_ -isnot [Int32]} { Break }
    {$_ % 2} {
        "$_ is Odd"
    }
    {-not ($_ % 2)} {
        "$_ is Even"
    }
}
```

```Output
1 is Odd
4 is Even
3 is Odd
```

## <a name="see-also"></a><span data-ttu-id="f26db-177">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f26db-177">See also</span></span>

[<span data-ttu-id="f26db-178">about_Break</span><span class="sxs-lookup"><span data-stu-id="f26db-178">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="f26db-179">about_Continue</span><span class="sxs-lookup"><span data-stu-id="f26db-179">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="f26db-180">about_If</span><span class="sxs-lookup"><span data-stu-id="f26db-180">about_If</span></span>](about_If.md)

[<span data-ttu-id="f26db-181">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="f26db-181">about_Script_Blocks</span></span>](about_Script_Blocks.md)
