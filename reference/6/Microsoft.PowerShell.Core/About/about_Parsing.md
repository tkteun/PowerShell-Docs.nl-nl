---
description: Hierin wordt beschreven hoe Power shell opdrachten parseert.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: 200a3aa7aac6477a2b2d3660167621132514c333
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252277"
---
# <a name="about-parsing"></a><span data-ttu-id="947f4-104">Over het parseren</span><span class="sxs-lookup"><span data-stu-id="947f4-104">About Parsing</span></span>

## <a name="short-description"></a><span data-ttu-id="947f4-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="947f4-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="947f4-106">Hierin wordt beschreven hoe Power shell opdrachten parseert.</span><span class="sxs-lookup"><span data-stu-id="947f4-106">Describes how PowerShell parses commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="947f4-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="947f4-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="947f4-108">Wanneer u een opdracht bij de opdracht prompt invoert, wordt de opdracht tekst door Power shell in een reeks segmenten met de naam _tokens_ genoemd en wordt vervolgens bepaald hoe elk token moet worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="947f4-108">When you enter a command at the command prompt, PowerShell breaks the command text into a series of segments called _tokens_ and then determines how to interpret each token.</span></span>

<span data-ttu-id="947f4-109">Als u bijvoorbeeld het volgende typt:</span><span class="sxs-lookup"><span data-stu-id="947f4-109">For example, if you type:</span></span>

```powershell
Write-Host book
```

<span data-ttu-id="947f4-110">Power shell verbreekt de opdracht in twee tokens `Write-Host` en `book` interpreteert elk token onafhankelijk van een van de twee primaire parserings modi: expressie modus en argument modus.</span><span class="sxs-lookup"><span data-stu-id="947f4-110">PowerShell breaks the command into two tokens, `Write-Host` and `book`, and interprets each token independently using one of two major parsing modes: expression mode and argument mode.</span></span>

> [!NOTE]
> <span data-ttu-id="947f4-111">Tijdens het parseren van de opdracht invoer in Power shell wordt geprobeerd de opdracht namen om te zetten in cmdlets of native uitvoer bare bestanden.</span><span class="sxs-lookup"><span data-stu-id="947f4-111">As PowerShell parses command input it tries to resolve the command names to cmdlets or native executables.</span></span> <span data-ttu-id="947f4-112">Als een opdracht naam niet exact overeenkomt, voegt Power shell `Get-` toe aan de opdracht als een standaard term.</span><span class="sxs-lookup"><span data-stu-id="947f4-112">If a command name does not have an exact match, PowerShell prepends `Get-` to the command as a default verb.</span></span> <span data-ttu-id="947f4-113">Power shell wordt bijvoorbeeld geparseerd `Process` als `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="947f4-113">For example, PowerShell parses `Process` as `Get-Process`.</span></span> <span data-ttu-id="947f4-114">Het wordt niet aanbevolen om deze functie te gebruiken om de volgende redenen:</span><span class="sxs-lookup"><span data-stu-id="947f4-114">It's not recommended to use this feature for the following reasons:</span></span>
>
> - <span data-ttu-id="947f4-115">Het is inefficiënt.</span><span class="sxs-lookup"><span data-stu-id="947f4-115">It's inefficient.</span></span> <span data-ttu-id="947f4-116">Dit leidt ertoe dat Power shell meerdere keren zoekt.</span><span class="sxs-lookup"><span data-stu-id="947f4-116">This causes PowerShell to search multiple times.</span></span>
> - <span data-ttu-id="947f4-117">Externe Program ma's met dezelfde naam worden eerst opgelost, dus u kunt de beoogde cmdlet niet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="947f4-117">External programs with the same name are resolved first, so you may not execute intended cmdlet.</span></span>
> - <span data-ttu-id="947f4-118">`Get-Help` en `Get-Command` herkennen niet-korte namen van woorden.</span><span class="sxs-lookup"><span data-stu-id="947f4-118">`Get-Help` and `Get-Command` don't recognize verb-less names.</span></span>

### <a name="expression-mode"></a><span data-ttu-id="947f4-119">Expressie modus</span><span class="sxs-lookup"><span data-stu-id="947f4-119">Expression mode</span></span>

<span data-ttu-id="947f4-120">De expressie modus is bedoeld voor het combi neren van expressies, die vereist zijn voor het bewerken van waarden in een script taal.</span><span class="sxs-lookup"><span data-stu-id="947f4-120">Expression mode is intended for combining expressions, required for value manipulation in a scripting language.</span></span> <span data-ttu-id="947f4-121">Expressies zijn representaties van waarden in de Power shell-syntaxis en kunnen eenvoudig of samengesteld zijn, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="947f4-121">Expressions are representations of values in PowerShell syntax, and can be simple or composite, for example:</span></span>

<span data-ttu-id="947f4-122">Letterlijke expressies zijn directe representaties van hun waarden:</span><span class="sxs-lookup"><span data-stu-id="947f4-122">Literal expressions are direct representations of their values:</span></span> 

```powershell
'hello', 32
```

<span data-ttu-id="947f4-123">Variabelen expressies bevatten de waarde van de variabele waarnaar wordt verwezen:</span><span class="sxs-lookup"><span data-stu-id="947f4-123">Variable expressions carry the value of the variable they reference:</span></span> 

```powershell
$x, $script:path
```
<span data-ttu-id="947f4-124">Opera tors combi neren andere expressies voor evaluatie:</span><span class="sxs-lookup"><span data-stu-id="947f4-124">Operators combine other expressions for evaluation:</span></span> 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- <span data-ttu-id="947f4-125">_Letterlijke teken reeks_ moet tussen aanhalings tekens staan.</span><span class="sxs-lookup"><span data-stu-id="947f4-125">_Character string literals_ must be contained in quotation marks.</span></span>
- <span data-ttu-id="947f4-126">_Getallen_ worden beschouwd als numerieke waarden in plaats van als een reeks tekens (tenzij escaped).</span><span class="sxs-lookup"><span data-stu-id="947f4-126">_Numbers_ are treated as numerical values rather than as a series of characters (unless escaped).</span></span>
- <span data-ttu-id="947f4-127">_Opera tors_ , waaronder unaire Opera tors als `-` en `-not` binaire Opera tors zoals en `+` `-gt` , worden geïnterpreteerd als Opera tors en voeren hun respectieve bewerkingen uit op hun argumenten (operands).</span><span class="sxs-lookup"><span data-stu-id="947f4-127">_Operators_ , including unary operators like `-` and `-not` and binary operators like `+` and `-gt`, are interpreted as operators and apply their respective operations on their arguments (operands).</span></span>
- <span data-ttu-id="947f4-128">_Kenmerk-en conversie-expressies_ worden geparseerd als expressies en toegepast op onderliggende expressies, bijvoorbeeld `[int] '7'` .</span><span class="sxs-lookup"><span data-stu-id="947f4-128">_Attribute and conversion expressions_ are parsed as expressions and applied to subordinate expressions, e.g. `[int] '7'`.</span></span>
- <span data-ttu-id="947f4-129">_Verwijzingen naar variabelen_ worden geëvalueerd op hun waarden, maar _splatting_ (d.w.z. het plakken van vooraf gevulde parameter sets) is verboden en veroorzaakt een parserfout.</span><span class="sxs-lookup"><span data-stu-id="947f4-129">_Variable references_ are evaluated to their values but _splatting_ (i.e. pasting prefilled parameter sets) is forbidden and causes a parser error.</span></span>
- <span data-ttu-id="947f4-130">Alle andere worden behandeld als een opdracht die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="947f4-130">Anything else will be treated as a command to be invoked.</span></span>

### <a name="argument-mode"></a><span data-ttu-id="947f4-131">Argument modus</span><span class="sxs-lookup"><span data-stu-id="947f4-131">Argument mode</span></span>

<span data-ttu-id="947f4-132">Bij het parseren van Power shell lijkt het om invoer te interpreteren als een expressie.</span><span class="sxs-lookup"><span data-stu-id="947f4-132">When parsing, PowerShell first looks to interpret input as an expression.</span></span> <span data-ttu-id="947f4-133">Maar wanneer een opdracht aanroep wordt aangetroffen, wordt het parseren voortgezet in de argument modus.</span><span class="sxs-lookup"><span data-stu-id="947f4-133">But when a command invocation is encountered, parsing continues in argument mode.</span></span>

<span data-ttu-id="947f4-134">De argument modus is ontworpen voor het parseren van argumenten en para meters voor opdrachten in een shell-omgeving.</span><span class="sxs-lookup"><span data-stu-id="947f4-134">Argument mode is designed for parsing arguments and parameters for commands in a shell environment.</span></span> <span data-ttu-id="947f4-135">Alle invoer wordt beschouwd als een uitbreid bare teken reeks, tenzij deze gebruikmaakt van een van de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="947f4-135">All input is treated as an expandable string unless it uses one of the following syntaxes:</span></span>

- <span data-ttu-id="947f4-136">Dollar teken ( `$` ) begint een verwijzing naar een variabele (alleen als deze wordt gevolgd door een geldige variabelenaam, anders wordt de waarde geïnterpreteerd als onderdeel van de uitbreid bare teken reeks).</span><span class="sxs-lookup"><span data-stu-id="947f4-136">Dollar sign (`$`) begins a variable reference (only if it is followed by a valid variable name, otherwise it is interpreted as part of the expandable string).</span></span>
- <span data-ttu-id="947f4-137">Aanhalings tekens ( `'` en `"` ) begin teken reeks waarden</span><span class="sxs-lookup"><span data-stu-id="947f4-137">Quotation marks (`'` and `"`) begin string values</span></span>
- <span data-ttu-id="947f4-138">Tussen haakjes ( `(` en `)` ) worden nieuwe expressies afgebakend.</span><span class="sxs-lookup"><span data-stu-id="947f4-138">Parentheses (`(` and `)`) demarcate new expressions.</span></span>
- <span data-ttu-id="947f4-139">De operator voor subexpressie ( `$(` ... `)` ) afbakent Inge sloten expressies.</span><span class="sxs-lookup"><span data-stu-id="947f4-139">Subexpression operator (`$(`…`)`) demarcates embedded expressions.</span></span>
- <span data-ttu-id="947f4-140">Accolades ( `{` en `}` ) afbakenen nieuwe script blokken.</span><span class="sxs-lookup"><span data-stu-id="947f4-140">Braces (`{` and `}`) demarcate new script blocks.</span></span>
- <span data-ttu-id="947f4-141">Bij het eerste at `@` -teken () begint de syntaxis van de expressie, zoals splatting ( `@args` ), arrays ( `@(1,2,3)` ) en Hash Tables ( `@{a=1;b=2}` ).</span><span class="sxs-lookup"><span data-stu-id="947f4-141">Initial at sign (`@`) begins expression syntaxes such as splatting (`@args`), arrays (`@(1,2,3)`) and hash tables (`@{a=1;b=2}`).</span></span>
- <span data-ttu-id="947f4-142">Komma's ( `,` ) introduceren lijsten die worden door gegeven als matrices, behalve wanneer de opdracht die moet worden aangeroepen, een systeem eigen toepassing is, in dat geval worden ze geïnterpreteerd als onderdeel van de uitbreid bare teken reeks.</span><span class="sxs-lookup"><span data-stu-id="947f4-142">Commas (`,`) introduce lists passed as arrays, except when the command to be called is a native application, in which case they are interpreted as part of the expandable string.</span></span> <span data-ttu-id="947f4-143">Initiële, opeenvolgende of afsluitende komma's worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="947f4-143">Initial, consecutive or trailing commas are not supported.</span></span>

<span data-ttu-id="947f4-144">Waarden van Inge sloten expressies worden geconverteerd naar teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="947f4-144">Values of embedded expressions are converted to strings.</span></span>

<span data-ttu-id="947f4-145">De volgende tabel bevat een aantal voor beelden van waarden die worden verwerkt in de expressie modus en de argument modus en de evaluatie van die waarden.</span><span class="sxs-lookup"><span data-stu-id="947f4-145">The following table provides several examples of values processed in expression mode and argument mode and the evaluation of those values.</span></span> <span data-ttu-id="947f4-146">We gaan ervan uit dat de waarde van de variabele `a` is `4` .</span><span class="sxs-lookup"><span data-stu-id="947f4-146">We assume that the value of the variable `a` is `4`.</span></span>

|       <span data-ttu-id="947f4-147">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="947f4-147">Example</span></span>        |    <span data-ttu-id="947f4-148">Modus</span><span class="sxs-lookup"><span data-stu-id="947f4-148">Mode</span></span>    |      <span data-ttu-id="947f4-149">Resultaat</span><span class="sxs-lookup"><span data-stu-id="947f4-149">Result</span></span>       |
| -------------------- | ---------- | ----------------- |
| `2`                  | <span data-ttu-id="947f4-150">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-150">Expression</span></span> | <span data-ttu-id="947f4-151">2 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="947f4-151">2 (integer)</span></span>       |
| `` `2``              | <span data-ttu-id="947f4-152">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-152">Expression</span></span> | <span data-ttu-id="947f4-153">"2" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="947f4-153">"2" (command)</span></span>     |
| `echo 2`             | <span data-ttu-id="947f4-154">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-154">Expression</span></span> | <span data-ttu-id="947f4-155">2 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="947f4-155">2 (integer)</span></span>       |
| `2+2`                | <span data-ttu-id="947f4-156">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-156">Expression</span></span> | <span data-ttu-id="947f4-157">4 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="947f4-157">4 (integer)</span></span>       |
| `echo 2+2`           | <span data-ttu-id="947f4-158">Argument</span><span class="sxs-lookup"><span data-stu-id="947f4-158">Argument</span></span>   | <span data-ttu-id="947f4-159">"2 + 2" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="947f4-159">"2+2" (string)</span></span>    |
| `echo(2+2)`          | <span data-ttu-id="947f4-160">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-160">Expression</span></span> | <span data-ttu-id="947f4-161">4 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="947f4-161">4 (integer)</span></span>       |
| `$a`                 | <span data-ttu-id="947f4-162">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-162">Expression</span></span> | <span data-ttu-id="947f4-163">4 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="947f4-163">4 (integer)</span></span>       |
| `echo $a`            | <span data-ttu-id="947f4-164">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-164">Expression</span></span> | <span data-ttu-id="947f4-165">4 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="947f4-165">4 (integer)</span></span>       |
| `$a+2`               | <span data-ttu-id="947f4-166">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-166">Expression</span></span> | <span data-ttu-id="947f4-167">6 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="947f4-167">6 (integer)</span></span>       |
| `echo $a+2`          | <span data-ttu-id="947f4-168">Argument</span><span class="sxs-lookup"><span data-stu-id="947f4-168">Argument</span></span>   | <span data-ttu-id="947f4-169">4 + 2 (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="947f4-169">4+2 (string)</span></span>      |
| `$-`                 | <span data-ttu-id="947f4-170">Argument</span><span class="sxs-lookup"><span data-stu-id="947f4-170">Argument</span></span>   | <span data-ttu-id="947f4-171">"$-" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="947f4-171">"$-" (command)</span></span>    |
| `echo $-`            | <span data-ttu-id="947f4-172">Argument</span><span class="sxs-lookup"><span data-stu-id="947f4-172">Argument</span></span>   | <span data-ttu-id="947f4-173">"$-" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="947f4-173">"$-" (string)</span></span>     |
| `a$a`                | <span data-ttu-id="947f4-174">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-174">Expression</span></span> | <span data-ttu-id="947f4-175">"a $ a" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="947f4-175">"a$a" (command)</span></span>   |
| `echo a$a`           | <span data-ttu-id="947f4-176">Argument</span><span class="sxs-lookup"><span data-stu-id="947f4-176">Argument</span></span>   | <span data-ttu-id="947f4-177">"A4" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="947f4-177">"a4" (string)</span></span>     |
| `a'$a'`              | <span data-ttu-id="947f4-178">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-178">Expression</span></span> | <span data-ttu-id="947f4-179">"a $ a" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="947f4-179">"a$a" (command)</span></span>   |
| `echo a'$a'`         | <span data-ttu-id="947f4-180">Argument</span><span class="sxs-lookup"><span data-stu-id="947f4-180">Argument</span></span>   | <span data-ttu-id="947f4-181">"a $ a" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="947f4-181">"a$a" (string)</span></span>    |
| `a"$a"`              | <span data-ttu-id="947f4-182">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-182">Expression</span></span> | <span data-ttu-id="947f4-183">"a $ a" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="947f4-183">"a$a" (command)</span></span>   |
| `echo a"$a"`         | <span data-ttu-id="947f4-184">Argument</span><span class="sxs-lookup"><span data-stu-id="947f4-184">Argument</span></span>   | <span data-ttu-id="947f4-185">"A4" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="947f4-185">"a4" (string)</span></span>     |
| `a$(2)`              | <span data-ttu-id="947f4-186">Expression</span><span class="sxs-lookup"><span data-stu-id="947f4-186">Expression</span></span> | <span data-ttu-id="947f4-187">"a $ (2)" (opdracht)</span><span class="sxs-lookup"><span data-stu-id="947f4-187">"a$(2)" (command)</span></span> |
| `echo a$(2)`         | <span data-ttu-id="947f4-188">Argument</span><span class="sxs-lookup"><span data-stu-id="947f4-188">Argument</span></span>   | <span data-ttu-id="947f4-189">"a2" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="947f4-189">"a2" (string)</span></span>     |

<span data-ttu-id="947f4-190">Elk token kan worden geïnterpreteerd als een soort object type, zoals Boole of teken reeks.</span><span class="sxs-lookup"><span data-stu-id="947f4-190">Every token can be interpreted as some kind of object type, such as Boolean or string.</span></span> <span data-ttu-id="947f4-191">Power shell probeert het object type te bepalen op basis van de expressie.</span><span class="sxs-lookup"><span data-stu-id="947f4-191">PowerShell attempts to determine the object type from the expression.</span></span>
<span data-ttu-id="947f4-192">Het object type is afhankelijk van het type para meter dat een opdracht verwacht en of Power shell weet hoe het argument moet worden geconverteerd naar het juiste type.</span><span class="sxs-lookup"><span data-stu-id="947f4-192">The object type depends on the type of parameter a command expects and on whether PowerShell knows how to convert the argument to the correct type.</span></span> <span data-ttu-id="947f4-193">In de volgende tabel ziet u een aantal voor beelden van de typen die zijn toegewezen aan waarden die door de expressies worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="947f4-193">The following table shows several examples of the types assigned to values returned by the expressions.</span></span>

|       <span data-ttu-id="947f4-194">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="947f4-194">Example</span></span>          |    <span data-ttu-id="947f4-195">Modus</span><span class="sxs-lookup"><span data-stu-id="947f4-195">Mode</span></span>    |     <span data-ttu-id="947f4-196">Resultaat</span><span class="sxs-lookup"><span data-stu-id="947f4-196">Result</span></span>      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | <span data-ttu-id="947f4-197">Argument voor </span><span class="sxs-lookup"><span data-stu-id="947f4-197">argument</span></span>   | <span data-ttu-id="947f4-198">"! 1" (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="947f4-198">"!1" (string)</span></span>   |
| `Write-Output (!1)`    | <span data-ttu-id="947f4-199">expression</span><span class="sxs-lookup"><span data-stu-id="947f4-199">expression</span></span> | <span data-ttu-id="947f4-200">False (Boole-waarde)</span><span class="sxs-lookup"><span data-stu-id="947f4-200">False (Boolean)</span></span> |
| `Write-Output (2)`     | <span data-ttu-id="947f4-201">expression</span><span class="sxs-lookup"><span data-stu-id="947f4-201">expression</span></span> | <span data-ttu-id="947f4-202">2 (geheel getal)</span><span class="sxs-lookup"><span data-stu-id="947f4-202">2 (integer)</span></span>     |
| `Set-Variable AB A,B`  | <span data-ttu-id="947f4-203">Argument voor </span><span class="sxs-lookup"><span data-stu-id="947f4-203">argument</span></span>   | <span data-ttu-id="947f4-204">' A ', ' B ' (matrix)</span><span class="sxs-lookup"><span data-stu-id="947f4-204">'A','B' (array)</span></span> |
| `CMD /CECHO A,B`       | <span data-ttu-id="947f4-205">Argument voor </span><span class="sxs-lookup"><span data-stu-id="947f4-205">argument</span></span>   | <span data-ttu-id="947f4-206">A, B (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="947f4-206">'A,B' (string)</span></span>  |
| `CMD /CECHO $AB`       | <span data-ttu-id="947f4-207">expression</span><span class="sxs-lookup"><span data-stu-id="947f4-207">expression</span></span> | <span data-ttu-id="947f4-208">' A ', ' B ' (matrix)</span><span class="sxs-lookup"><span data-stu-id="947f4-208">'A','B' (array)</span></span> |
| `CMD /CECHO :$AB`      | <span data-ttu-id="947f4-209">Argument voor </span><span class="sxs-lookup"><span data-stu-id="947f4-209">argument</span></span>   | <span data-ttu-id="947f4-210">': A B ' (teken reeks)</span><span class="sxs-lookup"><span data-stu-id="947f4-210">':A B' (string)</span></span> |

<span data-ttu-id="947f4-211">Het symbool voor het stoppen van parseren ( `--%` ), geïntroduceerd in Power shell 3,0, stuurt Power shell uit om te voor komen dat invoer als Power shell-opdrachten of-expressies wordt geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="947f4-211">The stop-parsing symbol (`--%`), introduced in PowerShell 3.0, directs PowerShell to refrain from interpreting input as PowerShell commands or expressions.</span></span>

<span data-ttu-id="947f4-212">Wanneer u een uitvoerbaar programma aanroept in Power shell, plaatst u het symbool voor het stoppen van parseren voor de programma argumenten.</span><span class="sxs-lookup"><span data-stu-id="947f4-212">When calling an executable program in PowerShell, place the stop-parsing symbol before the program arguments.</span></span> <span data-ttu-id="947f4-213">Deze techniek is veel eenvoudiger dan het gebruik van escape tekens om te voor komen dat er geen misinterpretatie is.</span><span class="sxs-lookup"><span data-stu-id="947f4-213">This technique is much easier than using escape characters to prevent misinterpretation.</span></span>

<span data-ttu-id="947f4-214">Wanneer er een symbool voor het stoppen van het parseren wordt aangetroffen, behandelt Power shell de resterende tekens in de regel als een letterlijke waarde.</span><span class="sxs-lookup"><span data-stu-id="947f4-214">When it encounters a stop-parsing symbol, PowerShell treats the remaining characters in the line as a literal.</span></span> <span data-ttu-id="947f4-215">De enige interpretatie die wordt uitgevoerd, is het vervangen van waarden voor omgevings variabelen die gebruikmaken van de standaard Windows-notatie, zoals `%USERPROFILE%` .</span><span class="sxs-lookup"><span data-stu-id="947f4-215">The only interpretation it performs is to substitute values for environment variables that use standard Windows notation, such as `%USERPROFILE%`.</span></span>

<span data-ttu-id="947f4-216">Het stop-parserings symbool is alleen geldig tot de volgende nieuwe regel of een volgend pijp lijn teken.</span><span class="sxs-lookup"><span data-stu-id="947f4-216">The stop-parsing symbol is effective only until the next newline or pipeline character.</span></span> <span data-ttu-id="947f4-217">U kunt geen voortzettings teken ( `` ` `` ) gebruiken om het effect ervan uit te breiden of een opdracht scheidings teken ( `;` ) te gebruiken om het effect te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="947f4-217">You cannot use a continuation character (`` ` ``) to extend its effect or use a command delimiter (`;`) to terminate its effect.</span></span>

<span data-ttu-id="947f4-218">Met de volgende opdracht wordt bijvoorbeeld het programma **icacls** aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="947f4-218">For example, the following command calls the **Icacls** program.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="947f4-219">Als u deze opdracht wilt uitvoeren in Power Shell 2,0, moet u escape tekens gebruiken om te voor komen dat Power shell de haakjes interpreteert.</span><span class="sxs-lookup"><span data-stu-id="947f4-219">To run this command in PowerShell 2.0, you must use escape characters to prevent PowerShell from misinterpreting the parentheses.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

<span data-ttu-id="947f4-220">Vanaf Power Shell 3,0 kunt u het symbool voor stoppen en parseren gebruiken.</span><span class="sxs-lookup"><span data-stu-id="947f4-220">Beginning in PowerShell 3.0, you can use the stop-parsing symbol.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="947f4-221">Power shell verzendt de volgende opdracht reeks naar het **icacls** -programma:</span><span class="sxs-lookup"><span data-stu-id="947f4-221">PowerShell sends the following command string to the **Icacls** program:</span></span>

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> <span data-ttu-id="947f4-222">Het symbool voor stoppen-parseren is alleen bedoeld voor gebruik op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="947f4-222">The stop-parsing symbol only intended for use on Windows platforms.</span></span>

## <a name="see-also"></a><span data-ttu-id="947f4-223">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="947f4-223">SEE ALSO</span></span>

[<span data-ttu-id="947f4-224">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="947f4-224">about_Command_Syntax</span></span>](about_Command_Syntax.md)
