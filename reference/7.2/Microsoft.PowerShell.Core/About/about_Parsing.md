---
description: Hierin wordt beschreven hoe Power shell opdrachten parseert.
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: a5ce30b2ad9aff7dd8b54e7a62937013a61cd278
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706228"
---
# <a name="about-parsing"></a><span data-ttu-id="31c9c-103">Over het parseren</span><span class="sxs-lookup"><span data-stu-id="31c9c-103">About Parsing</span></span>

## <a name="short-description"></a><span data-ttu-id="31c9c-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="31c9c-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="31c9c-105">Hierin wordt beschreven hoe Power shell opdrachten parseert.</span><span class="sxs-lookup"><span data-stu-id="31c9c-105">Describes how PowerShell parses commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="31c9c-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="31c9c-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="31c9c-107">Wanneer u een opdracht bij de opdracht prompt invoert, wordt de opdracht tekst door Power shell in een reeks segmenten met de naam _tokens_ genoemd en wordt vervolgens bepaald hoe elk token moet worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="31c9c-107">When you enter a command at the command prompt, PowerShell breaks the command text into a series of segments called _tokens_ and then determines how to interpret each token.</span></span>

<span data-ttu-id="31c9c-108">Als u bijvoorbeeld het volgende typt:</span><span class="sxs-lookup"><span data-stu-id="31c9c-108">For example, if you type:</span></span>

```powershell
Write-Host book
```

<span data-ttu-id="31c9c-109">Power shell verbreekt de opdracht in twee tokens `Write-Host` en `book` interpreteert elk token onafhankelijk van een van de twee primaire parserings modi: expressie modus en argument modus.</span><span class="sxs-lookup"><span data-stu-id="31c9c-109">PowerShell breaks the command into two tokens, `Write-Host` and `book`, and interprets each token independently using one of two major parsing modes: expression mode and argument mode.</span></span>

> [!NOTE]
> <span data-ttu-id="31c9c-110">Tijdens het parseren van de opdracht invoer in Power shell wordt geprobeerd de opdracht namen om te zetten in cmdlets of native uitvoer bare bestanden.</span><span class="sxs-lookup"><span data-stu-id="31c9c-110">As PowerShell parses command input it tries to resolve the command names to cmdlets or native executables.</span></span> <span data-ttu-id="31c9c-111">Als een opdracht naam niet exact overeenkomt, voegt Power shell `Get-` toe aan de opdracht als een standaard term.</span><span class="sxs-lookup"><span data-stu-id="31c9c-111">If a command name does not have an exact match, PowerShell prepends `Get-` to the command as a default verb.</span></span> <span data-ttu-id="31c9c-112">Power shell wordt bijvoorbeeld geparseerd `Process` als `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="31c9c-112">For example, PowerShell parses `Process` as `Get-Process`.</span></span> <span data-ttu-id="31c9c-113">Het wordt niet aanbevolen om deze functie te gebruiken om de volgende redenen:</span><span class="sxs-lookup"><span data-stu-id="31c9c-113">It's not recommended to use this feature for the following reasons:</span></span>
>
> - <span data-ttu-id="31c9c-114">Het is inefficiënt.</span><span class="sxs-lookup"><span data-stu-id="31c9c-114">It's inefficient.</span></span> <span data-ttu-id="31c9c-115">Dit leidt ertoe dat Power shell meerdere keren zoekt.</span><span class="sxs-lookup"><span data-stu-id="31c9c-115">This causes PowerShell to search multiple times.</span></span>
> - <span data-ttu-id="31c9c-116">Externe Program ma's met dezelfde naam worden eerst opgelost, dus u kunt de beoogde cmdlet niet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="31c9c-116">External programs with the same name are resolved first, so you may not execute intended cmdlet.</span></span>
> - <span data-ttu-id="31c9c-117">`Get-Help` en `Get-Command` herkennen niet-korte namen van woorden.</span><span class="sxs-lookup"><span data-stu-id="31c9c-117">`Get-Help` and `Get-Command` don't recognize verb-less names.</span></span>

### <a name="expression-mode"></a><span data-ttu-id="31c9c-118">Expressie modus</span><span class="sxs-lookup"><span data-stu-id="31c9c-118">Expression mode</span></span>

<span data-ttu-id="31c9c-119">De expressie modus is bedoeld voor het combi neren van expressies, die vereist zijn voor het bewerken van waarden in een script taal.</span><span class="sxs-lookup"><span data-stu-id="31c9c-119">Expression mode is intended for combining expressions, required for value manipulation in a scripting language.</span></span> <span data-ttu-id="31c9c-120">Expressies zijn representaties van waarden in de Power shell-syntaxis en kunnen eenvoudig of samengesteld zijn, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="31c9c-120">Expressions are representations of values in PowerShell syntax, and can be simple or composite, for example:</span></span>

<span data-ttu-id="31c9c-121">Letterlijke expressies zijn directe representaties van hun waarden:</span><span class="sxs-lookup"><span data-stu-id="31c9c-121">Literal expressions are direct representations of their values:</span></span> 

```powershell
'hello', 32
```

<span data-ttu-id="31c9c-122">Variabelen expressies bevatten de waarde van de variabele waarnaar wordt verwezen:</span><span class="sxs-lookup"><span data-stu-id="31c9c-122">Variable expressions carry the value of the variable they reference:</span></span> 

```powershell
$x, $script:path
```
<span data-ttu-id="31c9c-123">Opera tors combi neren andere expressies voor evaluatie:</span><span class="sxs-lookup"><span data-stu-id="31c9c-123">Operators combine other expressions for evaluation:</span></span> 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- <span data-ttu-id="31c9c-124">_Letterlijke teken reeks_ moet tussen aanhalings tekens staan.</span><span class="sxs-lookup"><span data-stu-id="31c9c-124">_Character string literals_ must be contained in quotation marks.</span></span>
- <span data-ttu-id="31c9c-125">_Getallen_ worden beschouwd als numerieke waarden in plaats van als een reeks tekens (tenzij escaped).</span><span class="sxs-lookup"><span data-stu-id="31c9c-125">_Numbers_ are treated as numerical values rather than as a series of characters (unless escaped).</span></span>
- <span data-ttu-id="31c9c-126">_Opera tors_, waaronder unaire Opera tors als `-` en `-not` binaire Opera tors zoals en `+` `-gt` , worden geïnterpreteerd als Opera tors en voeren hun respectieve bewerkingen uit op hun argumenten (operands).</span><span class="sxs-lookup"><span data-stu-id="31c9c-126">_Operators_, including unary operators like `-` and `-not` and binary operators like `+` and `-gt`, are interpreted as operators and apply their respective operations on their arguments (operands).</span></span>
- <span data-ttu-id="31c9c-127">_Kenmerk-en conversie-expressies_ worden geparseerd als expressies en toegepast op onderliggende expressies, bijvoorbeeld `[int] '7'` .</span><span class="sxs-lookup"><span data-stu-id="31c9c-127">_Attribute and conversion expressions_ are parsed as expressions and applied to subordinate expressions, e.g. `[int] '7'`.</span></span>
- <span data-ttu-id="31c9c-128">_Verwijzingen naar variabelen_ worden geëvalueerd op hun waarden, maar _splatting_ (d.w.z. het plakken van vooraf gevulde parameter sets) is verboden en veroorzaakt een parserfout.</span><span class="sxs-lookup"><span data-stu-id="31c9c-128">_Variable references_ are evaluated to their values but _splatting_ (i.e. pasting prefilled parameter sets) is forbidden and causes a parser error.</span></span>
- <span data-ttu-id="31c9c-129">Alle andere worden behandeld als een opdracht die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="31c9c-129">Anything else will be treated as a command to be invoked.</span></span>

### <a name="argument-mode"></a><span data-ttu-id="31c9c-130">Argument modus</span><span class="sxs-lookup"><span data-stu-id="31c9c-130">Argument mode</span></span>

<span data-ttu-id="31c9c-131">Bij het parseren van Power shell lijkt het om invoer te interpreteren als een expressie.</span><span class="sxs-lookup"><span data-stu-id="31c9c-131">When parsing, PowerShell first looks to interpret input as an expression.</span></span> <span data-ttu-id="31c9c-132">Maar wanneer een opdracht aanroep wordt aangetroffen, wordt het parseren voortgezet in de argument modus.</span><span class="sxs-lookup"><span data-stu-id="31c9c-132">But when a command invocation is encountered, parsing continues in argument mode.</span></span>

<span data-ttu-id="31c9c-133">De argument modus is ontworpen voor het parseren van argumenten en para meters voor opdrachten in een shell-omgeving.</span><span class="sxs-lookup"><span data-stu-id="31c9c-133">Argument mode is designed for parsing arguments and parameters for commands in a shell environment.</span></span> <span data-ttu-id="31c9c-134">Alle invoer wordt beschouwd als een uitbreid bare teken reeks, tenzij deze gebruikmaakt van een van de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="31c9c-134">All input is treated as an expandable string unless it uses one of the following syntaxes:</span></span>

- <span data-ttu-id="31c9c-135">Dollar teken ( `$` ) begint een verwijzing naar een variabele (alleen als deze wordt gevolgd door een geldige variabelenaam, anders wordt de waarde geïnterpreteerd als onderdeel van de uitbreid bare teken reeks).</span><span class="sxs-lookup"><span data-stu-id="31c9c-135">Dollar sign (`$`) begins a variable reference (only if it is followed by a valid variable name, otherwise it is interpreted as part of the expandable string).</span></span>
- <span data-ttu-id="31c9c-136">Aanhalings tekens ( `'` en `"` ) begin teken reeks waarden</span><span class="sxs-lookup"><span data-stu-id="31c9c-136">Quotation marks (`'` and `"`) begin string values</span></span>
- <span data-ttu-id="31c9c-137">Tussen haakjes ( `(` en `)` ) worden nieuwe expressies afgebakend.</span><span class="sxs-lookup"><span data-stu-id="31c9c-137">Parentheses (`(` and `)`) demarcate new expressions.</span></span>
- <span data-ttu-id="31c9c-138">De operator voor subexpressie ( `$(` ... `)` ) afbakent Inge sloten expressies.</span><span class="sxs-lookup"><span data-stu-id="31c9c-138">Subexpression operator (`$(`…`)`) demarcates embedded expressions.</span></span>
- <span data-ttu-id="31c9c-139">Accolades ( `{` en `}` ) afbakenen nieuwe script blokken.</span><span class="sxs-lookup"><span data-stu-id="31c9c-139">Braces (`{` and `}`) demarcate new script blocks.</span></span>
- <span data-ttu-id="31c9c-140">Bij het eerste at `@` -teken () begint de syntaxis van de expressie, zoals splatting ( `@args` ), arrays ( `@(1,2,3)` ) en Hash Tables ( `@{a=1;b=2}` ).</span><span class="sxs-lookup"><span data-stu-id="31c9c-140">Initial at sign (`@`) begins expression syntaxes such as splatting (`@args`), arrays (`@(1,2,3)`) and hash tables (`@{a=1;b=2}`).</span></span>
- <span data-ttu-id="31c9c-141">Komma's ( `,` ) introduceren lijsten die worden door gegeven als matrices, behalve wanneer de opdracht die moet worden aangeroepen, een systeem eigen toepassing is, in dat geval worden ze geïnterpreteerd als onderdeel van de uitbreid bare teken reeks.</span><span class="sxs-lookup"><span data-stu-id="31c9c-141">Commas (`,`) introduce lists passed as arrays, except when the command to be called is a native application, in which case they are interpreted as part of the expandable string.</span></span> <span data-ttu-id="31c9c-142">Initiële, opeenvolgende of afsluitende komma's worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="31c9c-142">Initial, consecutive or trailing commas are not supported.</span></span>

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
<span data-ttu-id="31c9c-143">Waarden van Inge sloten expressies worden geconverteerd naar teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="31c9c-143">Values of embedded expressions are converted to strings.</span></span>

<span data-ttu-id="31c9c-144">De volgende tabel bevat een aantal voor beelden van waarden die worden verwerkt in de expressie modus en de argument modus en de evaluatie van die waarden.</span><span class="sxs-lookup"><span data-stu-id="31c9c-144">The following table provides several examples of values processed in expression mode and argument mode and the evaluation of those values.</span></span> <span data-ttu-id="31c9c-145">We gaan ervan uit dat de waarde van de variabele `a` is `4` .</span><span class="sxs-lookup"><span data-stu-id="31c9c-145">We assume that the value of the variable `a` is `4`.</span></span>

|       <span data-ttu-id="31c9c-146">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="31c9c-146">Example</span></span>        |    <span data-ttu-id="31c9c-147">Modus</span><span class="sxs-lookup"><span data-stu-id="31c9c-147">Mode</span></span>    |      <span data-ttu-id="31c9c-148">Resultaat</span><span class="sxs-lookup"><span data-stu-id="31c9c-148">Result</span></span>       |
| -------------------- | ---------- | ----------------- |
| `2`                  | <span data-ttu-id="31c9c-149">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-149">Expression</span></span> | <span data-ttu-id="31c9c-150">2 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="31c9c-150">2 (integer)</span></span>       |
| `` `2``              | <span data-ttu-id="31c9c-151">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-151">Expression</span></span> | <span data-ttu-id="31c9c-152">"2" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="31c9c-152">"2" (command)</span></span>     |
| `echo 2`             | <span data-ttu-id="31c9c-153">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-153">Expression</span></span> | <span data-ttu-id="31c9c-154">2 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="31c9c-154">2 (integer)</span></span>       |
| `2+2`                | <span data-ttu-id="31c9c-155">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-155">Expression</span></span> | <span data-ttu-id="31c9c-156">4 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="31c9c-156">4 (integer)</span></span>       |
| `echo 2+2`           | <span data-ttu-id="31c9c-157">Argument</span><span class="sxs-lookup"><span data-stu-id="31c9c-157">Argument</span></span>   | <span data-ttu-id="31c9c-158">"2 + 2" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="31c9c-158">"2+2" (string)</span></span>    |
| `echo(2+2)`          | <span data-ttu-id="31c9c-159">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-159">Expression</span></span> | <span data-ttu-id="31c9c-160">4 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="31c9c-160">4 (integer)</span></span>       |
| `$a`                 | <span data-ttu-id="31c9c-161">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-161">Expression</span></span> | <span data-ttu-id="31c9c-162">4 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="31c9c-162">4 (integer)</span></span>       |
| `echo $a`            | <span data-ttu-id="31c9c-163">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-163">Expression</span></span> | <span data-ttu-id="31c9c-164">4 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="31c9c-164">4 (integer)</span></span>       |
| `$a+2`               | <span data-ttu-id="31c9c-165">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-165">Expression</span></span> | <span data-ttu-id="31c9c-166">6 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="31c9c-166">6 (integer)</span></span>       |
| `echo $a+2`          | <span data-ttu-id="31c9c-167">Argument</span><span class="sxs-lookup"><span data-stu-id="31c9c-167">Argument</span></span>   | <span data-ttu-id="31c9c-168">4 + 2 (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="31c9c-168">4+2 (string)</span></span>      |
| `$-`                 | <span data-ttu-id="31c9c-169">Argument</span><span class="sxs-lookup"><span data-stu-id="31c9c-169">Argument</span></span>   | <span data-ttu-id="31c9c-170">"$-" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="31c9c-170">"$-" (command)</span></span>    |
| `echo $-`            | <span data-ttu-id="31c9c-171">Argument</span><span class="sxs-lookup"><span data-stu-id="31c9c-171">Argument</span></span>   | <span data-ttu-id="31c9c-172">"$-" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="31c9c-172">"$-" (string)</span></span>     |
| `a$a`                | <span data-ttu-id="31c9c-173">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-173">Expression</span></span> | <span data-ttu-id="31c9c-174">"a $ a" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="31c9c-174">"a$a" (command)</span></span>   |
| `echo a$a`           | <span data-ttu-id="31c9c-175">Argument</span><span class="sxs-lookup"><span data-stu-id="31c9c-175">Argument</span></span>   | <span data-ttu-id="31c9c-176">"A4" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="31c9c-176">"a4" (string)</span></span>     |
| `a'$a'`              | <span data-ttu-id="31c9c-177">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-177">Expression</span></span> | <span data-ttu-id="31c9c-178">"a $ a" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="31c9c-178">"a$a" (command)</span></span>   |
| `echo a'$a'`         | <span data-ttu-id="31c9c-179">Argument</span><span class="sxs-lookup"><span data-stu-id="31c9c-179">Argument</span></span>   | <span data-ttu-id="31c9c-180">"a $ a" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="31c9c-180">"a$a" (string)</span></span>    |
| `a"$a"`              | <span data-ttu-id="31c9c-181">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-181">Expression</span></span> | <span data-ttu-id="31c9c-182">"a $ a" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="31c9c-182">"a$a" (command)</span></span>   |
| `echo a"$a"`         | <span data-ttu-id="31c9c-183">Argument</span><span class="sxs-lookup"><span data-stu-id="31c9c-183">Argument</span></span>   | <span data-ttu-id="31c9c-184">"A4" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="31c9c-184">"a4" (string)</span></span>     |
| `a$(2)`              | <span data-ttu-id="31c9c-185">Expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-185">Expression</span></span> | <span data-ttu-id="31c9c-186">"a $ (2)" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="31c9c-186">"a$(2)" (command)</span></span> |
| `echo a$(2)`         | <span data-ttu-id="31c9c-187">Argument</span><span class="sxs-lookup"><span data-stu-id="31c9c-187">Argument</span></span>   | <span data-ttu-id="31c9c-188">"a2" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="31c9c-188">"a2" (string)</span></span>     |

<span data-ttu-id="31c9c-189">Elk token kan worden geïnterpreteerd als een soort object type, zoals Boole of teken reeks.</span><span class="sxs-lookup"><span data-stu-id="31c9c-189">Every token can be interpreted as some kind of object type, such as Boolean or string.</span></span> <span data-ttu-id="31c9c-190">Power shell probeert het object type te bepalen op basis van de expressie.</span><span class="sxs-lookup"><span data-stu-id="31c9c-190">PowerShell attempts to determine the object type from the expression.</span></span>
<span data-ttu-id="31c9c-191">Het object type is afhankelijk van het type para meter dat een opdracht verwacht en of Power shell weet hoe het argument moet worden geconverteerd naar het juiste type.</span><span class="sxs-lookup"><span data-stu-id="31c9c-191">The object type depends on the type of parameter a command expects and on whether PowerShell knows how to convert the argument to the correct type.</span></span> <span data-ttu-id="31c9c-192">In de volgende tabel ziet u een aantal voor beelden van de typen die zijn toegewezen aan waarden die door de expressies worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="31c9c-192">The following table shows several examples of the types assigned to values returned by the expressions.</span></span>

|       <span data-ttu-id="31c9c-193">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="31c9c-193">Example</span></span>          |    <span data-ttu-id="31c9c-194">Modus</span><span class="sxs-lookup"><span data-stu-id="31c9c-194">Mode</span></span>    |     <span data-ttu-id="31c9c-195">Resultaat</span><span class="sxs-lookup"><span data-stu-id="31c9c-195">Result</span></span>      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | <span data-ttu-id="31c9c-196">Argument voor </span><span class="sxs-lookup"><span data-stu-id="31c9c-196">argument</span></span>   | <span data-ttu-id="31c9c-197">"! 1" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="31c9c-197">"!1" (string)</span></span>   |
| `Write-Output (!1)`    | <span data-ttu-id="31c9c-198">expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-198">expression</span></span> | <span data-ttu-id="31c9c-199">False (Boole-waarde)</span><span class="sxs-lookup"><span data-stu-id="31c9c-199">False (Boolean)</span></span> |
| `Write-Output (2)`     | <span data-ttu-id="31c9c-200">expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-200">expression</span></span> | <span data-ttu-id="31c9c-201">2 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="31c9c-201">2 (integer)</span></span>     |
| `Set-Variable AB A,B`  | <span data-ttu-id="31c9c-202">Argument voor </span><span class="sxs-lookup"><span data-stu-id="31c9c-202">argument</span></span>   | <span data-ttu-id="31c9c-203">' A ', ' B ' (matrix)</span><span class="sxs-lookup"><span data-stu-id="31c9c-203">'A','B' (array)</span></span> |
| `CMD /CECHO A,B`       | <span data-ttu-id="31c9c-204">Argument voor </span><span class="sxs-lookup"><span data-stu-id="31c9c-204">argument</span></span>   | <span data-ttu-id="31c9c-205">A, B (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="31c9c-205">'A,B' (string)</span></span>  |
| `CMD /CECHO $AB`       | <span data-ttu-id="31c9c-206">expression</span><span class="sxs-lookup"><span data-stu-id="31c9c-206">expression</span></span> | <span data-ttu-id="31c9c-207">' A ', ' B ' (matrix)</span><span class="sxs-lookup"><span data-stu-id="31c9c-207">'A','B' (array)</span></span> |
| `CMD /CECHO :$AB`      | <span data-ttu-id="31c9c-208">Argument voor </span><span class="sxs-lookup"><span data-stu-id="31c9c-208">argument</span></span>   | <span data-ttu-id="31c9c-209">': A B ' (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="31c9c-209">':A B' (string)</span></span> |

<span data-ttu-id="31c9c-210">Het symbool voor het stoppen van parseren ( `--%` ), geïntroduceerd in Power shell 3,0, stuurt Power shell uit om te voor komen dat invoer als Power shell-opdrachten of-expressies wordt geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="31c9c-210">The stop-parsing symbol (`--%`), introduced in PowerShell 3.0, directs PowerShell to refrain from interpreting input as PowerShell commands or expressions.</span></span>

<span data-ttu-id="31c9c-211">Wanneer u een uitvoerbaar programma aanroept in Power shell, plaatst u het symbool voor het stoppen van parseren voor de programma argumenten.</span><span class="sxs-lookup"><span data-stu-id="31c9c-211">When calling an executable program in PowerShell, place the stop-parsing symbol before the program arguments.</span></span> <span data-ttu-id="31c9c-212">Deze techniek is veel eenvoudiger dan het gebruik van escape tekens om te voor komen dat er geen misinterpretatie is.</span><span class="sxs-lookup"><span data-stu-id="31c9c-212">This technique is much easier than using escape characters to prevent misinterpretation.</span></span>

<span data-ttu-id="31c9c-213">Wanneer er een symbool voor het stoppen van het parseren wordt aangetroffen, behandelt Power shell de resterende tekens in de regel als een letterlijke waarde.</span><span class="sxs-lookup"><span data-stu-id="31c9c-213">When it encounters a stop-parsing symbol, PowerShell treats the remaining characters in the line as a literal.</span></span> <span data-ttu-id="31c9c-214">De enige interpretatie die wordt uitgevoerd, is het vervangen van waarden voor omgevings variabelen die gebruikmaken van de standaard Windows-notatie, zoals `%USERPROFILE%` .</span><span class="sxs-lookup"><span data-stu-id="31c9c-214">The only interpretation it performs is to substitute values for environment variables that use standard Windows notation, such as `%USERPROFILE%`.</span></span>

<span data-ttu-id="31c9c-215">Het stop-parserings symbool is alleen geldig tot de volgende nieuwe regel of een volgend pijp lijn teken.</span><span class="sxs-lookup"><span data-stu-id="31c9c-215">The stop-parsing symbol is effective only until the next newline or pipeline character.</span></span> <span data-ttu-id="31c9c-216">U kunt geen voortzettings teken ( `` ` `` ) gebruiken om het effect ervan uit te breiden of een opdracht scheidings teken ( `;` ) te gebruiken om het effect te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="31c9c-216">You cannot use a continuation character (`` ` ``) to extend its effect or use a command delimiter (`;`) to terminate its effect.</span></span>

<span data-ttu-id="31c9c-217">Met de volgende opdracht wordt bijvoorbeeld het programma **icacls** aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="31c9c-217">For example, the following command calls the **Icacls** program.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="31c9c-218">Als u deze opdracht wilt uitvoeren in Power Shell 2,0, moet u escape tekens gebruiken om te voor komen dat Power shell de haakjes interpreteert.</span><span class="sxs-lookup"><span data-stu-id="31c9c-218">To run this command in PowerShell 2.0, you must use escape characters to prevent PowerShell from misinterpreting the parentheses.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

<span data-ttu-id="31c9c-219">Vanaf Power Shell 3,0 kunt u het symbool voor stoppen en parseren gebruiken.</span><span class="sxs-lookup"><span data-stu-id="31c9c-219">Beginning in PowerShell 3.0, you can use the stop-parsing symbol.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="31c9c-220">Power shell verzendt de volgende opdracht reeks naar het **icacls** -programma:</span><span class="sxs-lookup"><span data-stu-id="31c9c-220">PowerShell sends the following command string to the **Icacls** program:</span></span>

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> <span data-ttu-id="31c9c-221">Het symbool voor stoppen-parseren is alleen bedoeld voor gebruik op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="31c9c-221">The stop-parsing symbol only intended for use on Windows platforms.</span></span>

## <a name="see-also"></a><span data-ttu-id="31c9c-222">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="31c9c-222">SEE ALSO</span></span>

[<span data-ttu-id="31c9c-223">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="31c9c-223">about_Command_Syntax</span></span>](about_Command_Syntax.md)
