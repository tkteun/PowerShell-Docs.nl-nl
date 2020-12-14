---
description: Hierin wordt uitgelegd hoe u met een switch meerdere `If` instructies kunt verwerken.
Locale: en-US
ms.date: 05/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 5ca12fe1d5052c1589c5dfecca8cf08cf68901e8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706072"
---
# <a name="about-switch"></a><span data-ttu-id="aeeed-103">Over Switch</span><span class="sxs-lookup"><span data-stu-id="aeeed-103">About Switch</span></span>

## <a name="short-description"></a><span data-ttu-id="aeeed-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="aeeed-104">Short description</span></span>
<span data-ttu-id="aeeed-105">Hierin wordt uitgelegd hoe u met een switch meerdere `If` instructies kunt verwerken.</span><span class="sxs-lookup"><span data-stu-id="aeeed-105">Explains how to use a switch to handle multiple `If` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="aeeed-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="aeeed-106">Long description</span></span>

<span data-ttu-id="aeeed-107">Als u een voor waarde in een script of functie wilt controleren, gebruikt u een- `If` instructie.</span><span class="sxs-lookup"><span data-stu-id="aeeed-107">To check a condition in a script or function, use an `If` statement.</span></span> <span data-ttu-id="aeeed-108">De `If` instructie kan veel soorten voor waarden controleren, met inbegrip van de waarde van variabelen en de eigenschappen van de objecten.</span><span class="sxs-lookup"><span data-stu-id="aeeed-108">The `If` statement can check many types of conditions, including the value of variables and the properties of objects.</span></span>

<span data-ttu-id="aeeed-109">Als u meerdere voor waarden wilt controleren, gebruikt u een- `Switch` instructie.</span><span class="sxs-lookup"><span data-stu-id="aeeed-109">To check multiple conditions, use a `Switch` statement.</span></span> <span data-ttu-id="aeeed-110">De `Switch` instructie is gelijk aan een reeks `If` instructies, maar is eenvoudiger.</span><span class="sxs-lookup"><span data-stu-id="aeeed-110">The `Switch` statement is equivalent to a series of `If` statements, but it is simpler.</span></span> <span data-ttu-id="aeeed-111">De `Switch` instructie vermeldt elke voor waarde en een optionele actie.</span><span class="sxs-lookup"><span data-stu-id="aeeed-111">The `Switch` statement lists each condition and an optional action.</span></span> <span data-ttu-id="aeeed-112">Als een voor waarde wordt opgehaald, wordt de actie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-112">If a condition obtains, the action is performed.</span></span>

<span data-ttu-id="aeeed-113">De- `Switch` instructie kan de `$_` en `$switch` automatische variabelen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="aeeed-113">The `Switch` statement can use the `$_` and `$switch` automatic variables.</span></span> <span data-ttu-id="aeeed-114">Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aeeed-114">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="aeeed-115">Een Basic- `Switch` instructie heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="aeeed-115">A basic `Switch` statement has the following format:</span></span>

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

<span data-ttu-id="aeeed-116">De volgende `Switch` instructie vergelijkt bijvoorbeeld de test waarde, 3, op elk van de voor waarden.</span><span class="sxs-lookup"><span data-stu-id="aeeed-116">For example, the following `Switch` statement compares the test value, 3, to each of the conditions.</span></span> <span data-ttu-id="aeeed-117">Wanneer de test waarde overeenkomt met de voor waarde, wordt de actie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-117">When the test value matches the condition, the action is performed.</span></span>

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

<span data-ttu-id="aeeed-118">In dit eenvoudige voor beeld wordt de waarde vergeleken met elke voor waarde in de lijst, zelfs als er een overeenkomst is voor de waarde 3.</span><span class="sxs-lookup"><span data-stu-id="aeeed-118">In this simple example, the value is compared to each condition in the list, even though there is a match for the value 3.</span></span> <span data-ttu-id="aeeed-119">De volgende `Switch` instructie heeft twee voor waarden voor de waarde 3.</span><span class="sxs-lookup"><span data-stu-id="aeeed-119">The following `Switch` statement has two conditions for a value of 3.</span></span> <span data-ttu-id="aeeed-120">Er wordt gedemonstreerd dat alle voor waarden standaard worden getest.</span><span class="sxs-lookup"><span data-stu-id="aeeed-120">It demonstrates that, by default, all conditions are tested.</span></span>

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

<span data-ttu-id="aeeed-121">`Switch`Gebruik de instructie om de te stoppen om te vergelijken na een overeenkomst `Break` .</span><span class="sxs-lookup"><span data-stu-id="aeeed-121">To direct the `Switch` to stop comparing after a match, use the `Break` statement.</span></span> <span data-ttu-id="aeeed-122">De instructie `Break` beëindigt de `Switch` instructie.</span><span class="sxs-lookup"><span data-stu-id="aeeed-122">The `Break` statement terminates the `Switch` statement.</span></span>

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

<span data-ttu-id="aeeed-123">Als de test waarde een verzameling is, zoals een matrix, wordt elk item in de verzameling geëvalueerd in de volg orde waarin deze wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aeeed-123">If the test value is a collection, such as an array, each item in the collection is evaluated in the order in which it appears.</span></span> <span data-ttu-id="aeeed-124">In de volgende voor beelden wordt 4 en vervolgens 2 geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-124">The following examples evaluates 4 and then 2.</span></span>

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

<span data-ttu-id="aeeed-125">Alle `Break` instructies zijn van toepassing op de verzameling, niet op elke waarde, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="aeeed-125">Any `Break` statements apply to the collection, not to each value, as shown in the following example.</span></span> <span data-ttu-id="aeeed-126">De `Switch` instructie wordt beëindigd door de `Break` instructie in de voor waarde van de waarde 4.</span><span class="sxs-lookup"><span data-stu-id="aeeed-126">The `Switch` statement is terminated by the `Break` statement in the condition of value 4.</span></span>

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

### <a name="syntax"></a><span data-ttu-id="aeeed-127">Syntax</span><span class="sxs-lookup"><span data-stu-id="aeeed-127">Syntax</span></span>

<span data-ttu-id="aeeed-128">De syntaxis van de `Switch` instructie complete is als volgt:</span><span class="sxs-lookup"><span data-stu-id="aeeed-128">The complete `Switch` statement syntax is as follows:</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="aeeed-129">of</span><span class="sxs-lookup"><span data-stu-id="aeeed-129">or</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="aeeed-130">Als er geen para meters worden gebruikt, `Switch` werkt hetzelfde als met de **exacte** para meter.</span><span class="sxs-lookup"><span data-stu-id="aeeed-130">If no parameters are used, `Switch` behaves the same as using the **Exact** parameter.</span></span> <span data-ttu-id="aeeed-131">Er wordt een niet-hoofdletter gevoelige overeenkomst voor de waarde uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-131">It performs a case-insensitive match for the value.</span></span> <span data-ttu-id="aeeed-132">Als de waarde een verzameling is, wordt elk element geëvalueerd in de volg orde waarin het wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aeeed-132">If the value is a collection, each element is evaluated in the order in which it appears.</span></span>

<span data-ttu-id="aeeed-133">De `Switch` instructie moet ten minste één voorwaarde instructie bevatten.</span><span class="sxs-lookup"><span data-stu-id="aeeed-133">The `Switch` statement must include at least one condition statement.</span></span>

<span data-ttu-id="aeeed-134">De `Default` component wordt geactiveerd wanneer de waarde niet overeenkomt met een van de voor waarden.</span><span class="sxs-lookup"><span data-stu-id="aeeed-134">The `Default` clause is triggered when the value does not match any of the conditions.</span></span> <span data-ttu-id="aeeed-135">Deze is gelijk aan een- `Else` component in een- `If` instructie.</span><span class="sxs-lookup"><span data-stu-id="aeeed-135">It is equivalent to an `Else` clause in an `If` statement.</span></span> <span data-ttu-id="aeeed-136">`Default`In elke instructie is slechts één component toegestaan `Switch` .</span><span class="sxs-lookup"><span data-stu-id="aeeed-136">Only one `Default` clause is permitted in each `Switch` statement.</span></span>

<span data-ttu-id="aeeed-137">`Switch` heeft de volgende para meters:</span><span class="sxs-lookup"><span data-stu-id="aeeed-137">`Switch` has the following parameters:</span></span>

- <span data-ttu-id="aeeed-138">**Joker** teken: geeft aan dat de voor waarde een Joker teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="aeeed-138">**Wildcard** - Indicates that the condition is a wildcard string.</span></span> <span data-ttu-id="aeeed-139">Als de match-component geen teken reeks is, wordt de para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-139">If the match clause is not a string, the parameter is ignored.</span></span> <span data-ttu-id="aeeed-140">De vergelijking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="aeeed-140">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="aeeed-141">**Exact** : geeft aan dat de match-component als deze een teken reeks is, exact moet overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="aeeed-141">**Exact** - Indicates that the match clause, if it is a string, must match exactly.</span></span> <span data-ttu-id="aeeed-142">Als de match-component geen teken reeks is, wordt deze para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-142">If the match clause is not a string, this parameter is ignored.</span></span> <span data-ttu-id="aeeed-143">De vergelijking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="aeeed-143">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="aeeed-144">**CaseSensitive** : Hiermee wordt een hoofdletter gevoelige overeenkomst uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-144">**CaseSensitive** - Performs a case-sensitive match.</span></span> <span data-ttu-id="aeeed-145">Als de match-component geen teken reeks is, wordt deze para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-145">If the match clause is not a string, this parameter is ignored.</span></span>
- <span data-ttu-id="aeeed-146">**File**-voert invoer uit vanuit een bestand in plaats van een waarde-instructie.</span><span class="sxs-lookup"><span data-stu-id="aeeed-146">**File**- Takes input from a file rather than a value statement.</span></span> <span data-ttu-id="aeeed-147">Als er meerdere **Bestands** parameters zijn opgenomen, wordt alleen de laatste gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aeeed-147">If multiple **File** parameters are included, only the last one is used.</span></span> <span data-ttu-id="aeeed-148">Elke regel van het bestand wordt gelezen en geëvalueerd door de `Switch` instructie.</span><span class="sxs-lookup"><span data-stu-id="aeeed-148">Each line of the file is read and evaluated by the `Switch` statement.</span></span> <span data-ttu-id="aeeed-149">De vergelijking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="aeeed-149">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="aeeed-150">**Regex** -voert een reguliere expressie die overeenkomt met de waarde aan de voor waarde.</span><span class="sxs-lookup"><span data-stu-id="aeeed-150">**Regex** - Performs regular expression matching of the value to the condition.</span></span> <span data-ttu-id="aeeed-151">Als de match-component geen teken reeks is, wordt deze para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-151">If the match clause is not a string, this parameter is ignored.</span></span>
  <span data-ttu-id="aeeed-152">De vergelijking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="aeeed-152">The comparison is case-insensitive.</span></span> <span data-ttu-id="aeeed-153">De `$matches` Automatische variabele is beschikbaar voor gebruik binnen het overeenkomende instructie blok.</span><span class="sxs-lookup"><span data-stu-id="aeeed-153">The `$matches` automatic variable is available for use within the matching statement block.</span></span>

> [!NOTE]
> <span data-ttu-id="aeeed-154">Wanneer er conflicterende waarden worden opgegeven, zoals **regex** en **Joker teken**, heeft de laatste para meter prioriteit en worden alle conflicterende para meters genegeerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-154">When specifying conflicting values, like **Regex** and **Wildcard**, the last parameter specified takes precedence, and all conflicting parameters are ignored.</span></span> <span data-ttu-id="aeeed-155">Er zijn ook meerdere exemplaren van para meters toegestaan.</span><span class="sxs-lookup"><span data-stu-id="aeeed-155">Multiple instances of parameters are also permitted.</span></span> <span data-ttu-id="aeeed-156">Alleen de laatste para meter die wordt gebruikt, is echter effectief.</span><span class="sxs-lookup"><span data-stu-id="aeeed-156">However, only the last parameter used is effective.</span></span>

<span data-ttu-id="aeeed-157">In dit voor beeld wordt een object dat geen teken reeks of numerieke gegevens is door gegeven aan de `Switch` .</span><span class="sxs-lookup"><span data-stu-id="aeeed-157">In this example, an object that's not a string or numerical data is passed to the `Switch`.</span></span> <span data-ttu-id="aeeed-158">`Switch`Hiermee wordt een teken reeks afgedwongen voor het object en wordt het resultaat geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-158">The `Switch` performs a string coercion on the object and evaluates the outcome.</span></span>

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

<span data-ttu-id="aeeed-159">In dit voor beeld is er geen overeenkomende case, dus er is geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="aeeed-159">In this example, there is no matching case so there is no output.</span></span>

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

<span data-ttu-id="aeeed-160">Door de component toe te voegen `Default` , kunt u een actie uitvoeren wanneer er geen andere voor waarden slagen.</span><span class="sxs-lookup"><span data-stu-id="aeeed-160">By adding the `Default` clause, you can perform an action when no other conditions succeed.</span></span>

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

<span data-ttu-id="aeeed-161">Als u wilt dat het woord ' veer tien ' overeenkomt met een aanvraag, moet u de `-Wildcard` `-Regex` para meter or gebruiken.</span><span class="sxs-lookup"><span data-stu-id="aeeed-161">For the word "fourteen" to match a case you must use the `-Wildcard` or `-Regex` parameter.</span></span>

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

<span data-ttu-id="aeeed-162">In het volgende voor beeld wordt de `-Regex` para meter gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aeeed-162">The following example uses the `-Regex` parameter.</span></span>

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

<span data-ttu-id="aeeed-163">De voor waarde van een switch instructie kan bestaan uit:</span><span class="sxs-lookup"><span data-stu-id="aeeed-163">A Switch statement condition may be either:</span></span>

- <span data-ttu-id="aeeed-164">Een expressie waarvan de waarde wordt vergeleken met de invoer waarde</span><span class="sxs-lookup"><span data-stu-id="aeeed-164">An expression whose value is compared to the input value</span></span>
- <span data-ttu-id="aeeed-165">Een script blok dat moet worden geretourneerd `$true` als aan een voor waarde wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="aeeed-165">A script block which should return `$true` if a condition is met.</span></span>

<span data-ttu-id="aeeed-166">De `$_` Automatische variabele bevat de waarde die is door gegeven aan de switch-instructie en is beschikbaar voor evaluatie en gebruik binnen het bereik van de voor waarden-instructies.</span><span class="sxs-lookup"><span data-stu-id="aeeed-166">The `$_` automatic variable contains the value passed to the switch statement and is available for evaluation and use within the scope of the condition statements.</span></span>

<span data-ttu-id="aeeed-167">De actie voor elke voor waarde is onafhankelijk van de acties in andere omstandigheden.</span><span class="sxs-lookup"><span data-stu-id="aeeed-167">The action for each condition is independent of the actions in other conditions.</span></span>

<span data-ttu-id="aeeed-168">In het volgende voor beeld wordt het gebruik van script blokken als instructie voorwaarden gedemonstreerd `Switch` .</span><span class="sxs-lookup"><span data-stu-id="aeeed-168">The following example demonstrates the use of script blocks as `Switch` statement conditions.</span></span>

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

<span data-ttu-id="aeeed-169">Als de waarde overeenkomt met meerdere voor waarden, wordt de actie voor elke voor waarde uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aeeed-169">If the value matches multiple conditions, the action for each condition is executed.</span></span> <span data-ttu-id="aeeed-170">Gebruik de `Break` tref woorden of om dit gedrag te wijzigen `Continue` .</span><span class="sxs-lookup"><span data-stu-id="aeeed-170">To change this behavior, use the `Break` or `Continue` keywords.</span></span>

<span data-ttu-id="aeeed-171">Het `Break` sleutel woord stopt met de verwerking en sluit de `Switch` instructie af.</span><span class="sxs-lookup"><span data-stu-id="aeeed-171">The `Break` keyword stops processing and exits the `Switch` statement.</span></span>

<span data-ttu-id="aeeed-172">Het `Continue` sleutel woord stopt met het verwerken van de huidige waarde, maar gaat verder met de verwerking van alle volgende waarden.</span><span class="sxs-lookup"><span data-stu-id="aeeed-172">The `Continue` keyword stops processing the current value, but continues processing any subsequent values.</span></span>

<span data-ttu-id="aeeed-173">In het volgende voor beeld wordt een matrix met getallen verwerkt en wordt weer gegeven als ze oneven of even zijn.</span><span class="sxs-lookup"><span data-stu-id="aeeed-173">The following example processes an array of numbers and displays if they are odd or even.</span></span> <span data-ttu-id="aeeed-174">Negatieve getallen worden overgeslagen met het `Continue` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="aeeed-174">Negative numbers are skipped with the `Continue` keyword.</span></span> <span data-ttu-id="aeeed-175">Als er een niet-nummer wordt aangetroffen, wordt de uitvoering beëindigd met het `Break` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="aeeed-175">If a non-number is encountered, execution is terminated with the `Break` keyword.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="aeeed-176">Zie ook</span><span class="sxs-lookup"><span data-stu-id="aeeed-176">See also</span></span>

[<span data-ttu-id="aeeed-177">about_Break</span><span class="sxs-lookup"><span data-stu-id="aeeed-177">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="aeeed-178">about_Continue</span><span class="sxs-lookup"><span data-stu-id="aeeed-178">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="aeeed-179">about_If</span><span class="sxs-lookup"><span data-stu-id="aeeed-179">about_If</span></span>](about_If.md)

[<span data-ttu-id="aeeed-180">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="aeeed-180">about_Script_Blocks</span></span>](about_Script_Blocks.md)
