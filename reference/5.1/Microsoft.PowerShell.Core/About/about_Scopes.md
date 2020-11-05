---
description: Hierin wordt het concept van de scope in Power shell beschreven en wordt getoond hoe u het bereik van elementen kunt instellen en wijzigen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 6a86348bb70afdcbd8ffe00339d1597efd8f88c4
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354572"
---
# <a name="about-scopes"></a><span data-ttu-id="764be-104">Over bereiken</span><span class="sxs-lookup"><span data-stu-id="764be-104">About Scopes</span></span>

## <a name="short-description"></a><span data-ttu-id="764be-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="764be-105">Short description</span></span>
<span data-ttu-id="764be-106">Hierin wordt het concept van de scope in Power shell beschreven en wordt getoond hoe u het bereik van elementen kunt instellen en wijzigen.</span><span class="sxs-lookup"><span data-stu-id="764be-106">Explains the concept of scope in PowerShell and shows how to set and change the scope of elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="764be-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="764be-107">Long description</span></span>

<span data-ttu-id="764be-108">Power shell beveiligt de toegang tot variabelen, aliassen, functies en Power Shell-stations (PSDrives) door te beperken waar ze kunnen worden gelezen en gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="764be-108">PowerShell protects access to variables, aliases, functions, and PowerShell drives (PSDrives) by limiting where they can be read and changed.</span></span> <span data-ttu-id="764be-109">In Power shell worden scope regels gebruikt om ervoor te zorgen dat u niet per ongeluk een item wijzigt dat niet mag worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="764be-109">PowerShell uses scope rules to ensure that you do not inadvertently change an item that should not be changed.</span></span>

<span data-ttu-id="764be-110">Hier volgen de basis regels voor het bereik:</span><span class="sxs-lookup"><span data-stu-id="764be-110">The following are the basic rules of scope:</span></span>

- <span data-ttu-id="764be-111">Bereiken kunnen worden genest.</span><span class="sxs-lookup"><span data-stu-id="764be-111">Scopes may nest.</span></span> <span data-ttu-id="764be-112">Een buitenste bereik wordt een bovenliggend bereik genoemd.</span><span class="sxs-lookup"><span data-stu-id="764be-112">An outer scope is referred to as a parent scope.</span></span> <span data-ttu-id="764be-113">Alle geneste bereiken zijn onderliggende bereiken van het bovenliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-113">Any nested scopes are child scopes of that parent.</span></span>

- <span data-ttu-id="764be-114">Een item is zichtbaar in het bereik waarin het is gemaakt en in een onderliggend bereik, tenzij u het expliciet persoonlijk maakt.</span><span class="sxs-lookup"><span data-stu-id="764be-114">An item is visible in the scope in which it was created and in any child scopes, unless you explicitly make it private.</span></span> <span data-ttu-id="764be-115">U kunt variabelen, aliassen, functies of Power Shell-stations in een of meer scopes plaatsen.</span><span class="sxs-lookup"><span data-stu-id="764be-115">You can place variables, aliases, functions, or PowerShell drives in one or more scopes.</span></span>

- <span data-ttu-id="764be-116">Een item dat u in een bereik hebt gemaakt, kan alleen worden gewijzigd in het bereik waarin het is gemaakt, tenzij u expliciet een ander bereik opgeeft.</span><span class="sxs-lookup"><span data-stu-id="764be-116">An item that you created within a scope can be changed only in the scope in which it was created, unless you explicitly specify a different scope.</span></span>

<span data-ttu-id="764be-117">Als u een item in een bereik maakt en de naam van het item is gedeeld met een item in een ander bereik, wordt het oorspronkelijke item mogelijk verborgen onder het nieuwe item, maar wordt het niet overschreven of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="764be-117">If you create an item in a scope, and the item shares its name with an item in a different scope, the original item might be hidden under the new item, but it is not overridden or changed.</span></span>

## <a name="powershell-scopes"></a><span data-ttu-id="764be-118">Power shell-bereiken</span><span class="sxs-lookup"><span data-stu-id="764be-118">PowerShell Scopes</span></span>

<span data-ttu-id="764be-119">Power shell ondersteunt de volgende bereiken:</span><span class="sxs-lookup"><span data-stu-id="764be-119">PowerShell supports the following scopes:</span></span>

- <span data-ttu-id="764be-120">Global: het bereik dat van toepassing is wanneer Power shell wordt gestart of wanneer u een nieuwe sessie of runs Pace maakt.</span><span class="sxs-lookup"><span data-stu-id="764be-120">Global: The scope that is in effect when PowerShell starts or when you create a new session or runspace.</span></span> <span data-ttu-id="764be-121">Variabelen en functies die aanwezig zijn wanneer Power shell wordt gestart, zijn gemaakt in het globale bereik, zoals automatische variabelen en voorkeurs variabelen.</span><span class="sxs-lookup"><span data-stu-id="764be-121">Variables and functions that are present when PowerShell starts have been created in the global scope, such as automatic variables and preference variables.</span></span> <span data-ttu-id="764be-122">De variabelen, aliassen en functies in uw Power shell-profielen worden ook in het globale bereik gemaakt.</span><span class="sxs-lookup"><span data-stu-id="764be-122">The variables, aliases, and functions in your PowerShell profiles are also created in the global scope.</span></span> <span data-ttu-id="764be-123">Het globale bereik is het bovenliggende hoofd bereik in een sessie.</span><span class="sxs-lookup"><span data-stu-id="764be-123">The global scope is the root parent scope in a session.</span></span>

- <span data-ttu-id="764be-124">Lokaal: het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-124">Local: The current scope.</span></span> <span data-ttu-id="764be-125">Het lokale bereik kan het globale bereik of een ander bereik zijn.</span><span class="sxs-lookup"><span data-stu-id="764be-125">The local scope can be the global scope or any other scope.</span></span>

- <span data-ttu-id="764be-126">Script: het bereik dat is gemaakt tijdens het uitvoeren van een script bestand.</span><span class="sxs-lookup"><span data-stu-id="764be-126">Script: The scope that is created while a script file runs.</span></span> <span data-ttu-id="764be-127">Alleen de opdrachten in het script worden uitgevoerd in het bereik van het script.</span><span class="sxs-lookup"><span data-stu-id="764be-127">Only the commands in the script run in the script scope.</span></span> <span data-ttu-id="764be-128">Met de opdrachten in een script is het bereik van het script het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-128">To the commands in a script, the script scope is the local scope.</span></span>

> [!NOTE]
> <span data-ttu-id="764be-129">**Privé** is geen bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-129">**Private** is not a scope.</span></span> <span data-ttu-id="764be-130">Het is een [optie](#private-option) waarmee de zicht baarheid van een item buiten het bereik waarin het item is gedefinieerd, wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="764be-130">It is an [option](#private-option) that changes the visibility of an item outside of the scope where the item is defined.</span></span>

## <a name="parent-and-child-scopes"></a><span data-ttu-id="764be-131">Bovenliggende en onderliggende bereiken</span><span class="sxs-lookup"><span data-stu-id="764be-131">Parent and Child Scopes</span></span>

<span data-ttu-id="764be-132">U kunt een nieuw onderliggend bereik maken door een script of functie aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="764be-132">You can create a new child scope by calling a script or function.</span></span> <span data-ttu-id="764be-133">Het aanroepende bereik is het bovenliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-133">The calling scope is the parent scope.</span></span> <span data-ttu-id="764be-134">De aangeroepen script of functie is het onderliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-134">The called script or function is the child scope.</span></span>
<span data-ttu-id="764be-135">De functies of scripts die u aanroept, kunnen andere functies aanroepen en een hiërarchie van onderliggende bereiken maken waarvan het hoofd bereik het globale bereik is.</span><span class="sxs-lookup"><span data-stu-id="764be-135">The functions or scripts you call may call other functions, creating a hierarchy of child scopes whose root scope is the global scope.</span></span>

<span data-ttu-id="764be-136">Tenzij u de items expliciet aanmaakt, zijn de items in het bovenliggende bereik beschikbaar voor het onderliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-136">Unless you explicitly make the items private, the items in the parent scope are available to the child scope.</span></span> <span data-ttu-id="764be-137">Items die u in het onderliggende bereik maakt en wijzigt, hebben echter geen invloed op het bovenliggende bereik, tenzij u expliciet het bereik opgeeft wanneer u de items maakt.</span><span class="sxs-lookup"><span data-stu-id="764be-137">However, items that you create and change in the child scope do not affect the parent scope, unless you explicitly specify the scope when you create the items.</span></span>

> [!NOTE]
> <span data-ttu-id="764be-138">Functies van een module kunnen niet worden uitgevoerd in een onderliggend bereik van het aanroepende bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-138">Functions from a module do not run in a child scope of the calling scope.</span></span>
> <span data-ttu-id="764be-139">Modules hebben hun eigen sessie status die is gekoppeld aan het globale bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-139">Modules have their own session state that is linked to the global scope.</span></span>
> <span data-ttu-id="764be-140">Alle module code wordt uitgevoerd in een module-specifieke hiërarchie van bereiken met een eigen hoofd bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-140">All module code runs in a module-specific hierarchy of scopes that has its own root scope.</span></span>

## <a name="inheritance"></a><span data-ttu-id="764be-141">Overname</span><span class="sxs-lookup"><span data-stu-id="764be-141">Inheritance</span></span>

<span data-ttu-id="764be-142">Een onderliggend bereik neemt de variabelen, aliassen en functies niet over van het bovenliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-142">A child scope does not inherit the variables, aliases, and functions from the parent scope.</span></span> <span data-ttu-id="764be-143">Tenzij een item privé is, kan het onderliggende bereik de items in het bovenliggende bereik weer geven.</span><span class="sxs-lookup"><span data-stu-id="764be-143">Unless an item is private, the child scope can view the items in the parent scope.</span></span> <span data-ttu-id="764be-144">En de items kunnen worden gewijzigd door expliciet het bovenliggende bereik op te geven, maar de items maken geen deel uit van het onderliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-144">And, it can change the items by explicitly specifying the parent scope, but the items are not part of the child scope.</span></span>

<span data-ttu-id="764be-145">Een onderliggend bereik wordt echter gemaakt met een set items.</span><span class="sxs-lookup"><span data-stu-id="764be-145">However, a child scope is created with a set of items.</span></span> <span data-ttu-id="764be-146">Normaal gesp roken bevat het alle aliassen met de optie **AllScope** .</span><span class="sxs-lookup"><span data-stu-id="764be-146">Typically, it includes all the aliases that have the **AllScope** option.</span></span> <span data-ttu-id="764be-147">Deze optie wordt verderop in dit artikel besproken.</span><span class="sxs-lookup"><span data-stu-id="764be-147">This option is discussed later in this article.</span></span> <span data-ttu-id="764be-148">Het bevat alle variabelen met de optie **AllScope** , plus enkele automatische variabelen.</span><span class="sxs-lookup"><span data-stu-id="764be-148">It includes all the variables that have the **AllScope** option, plus some automatic variables.</span></span>

<span data-ttu-id="764be-149">Als u de items in een bepaald bereik wilt zoeken, gebruikt u de para meter bereik van `Get-Variable` of `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="764be-149">To find the items in a particular scope, use the Scope parameter of `Get-Variable` or `Get-Alias`.</span></span>

<span data-ttu-id="764be-150">Als u bijvoorbeeld alle variabelen in het lokale bereik wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="764be-150">For example, to get all the variables in the local scope, type:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="764be-151">Als u alle variabelen in het globale bereik wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="764be-151">To get all the variables in the global scope, type:</span></span>

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a><span data-ttu-id="764be-152">Bereik aanpassingen</span><span class="sxs-lookup"><span data-stu-id="764be-152">Scope Modifiers</span></span>

<span data-ttu-id="764be-153">Een variabele-, alias-of functie naam kan een van de volgende optionele Scope-para meters bevatten:</span><span class="sxs-lookup"><span data-stu-id="764be-153">A variable, alias, or function name can include any one of the following optional scope modifiers:</span></span>

- <span data-ttu-id="764be-154">`global:` -Geeft aan dat de naam bestaat in het **globale** bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-154">`global:` - Specifies that the name exists in the **Global** scope.</span></span>
- <span data-ttu-id="764be-155">`local:` -Geeft aan dat de naam bestaat in het **lokale** bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-155">`local:` - Specifies that the name exists in the **Local** scope.</span></span> <span data-ttu-id="764be-156">Het huidige bereik is altijd het **lokale** bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-156">The current scope is always the **Local** scope.</span></span>
- <span data-ttu-id="764be-157">`private:` -Geeft aan dat de naam **privé** is en alleen zichtbaar is voor de huidige scope.</span><span class="sxs-lookup"><span data-stu-id="764be-157">`private:` - Specifies that the name is **Private** and only visible to the current scope.</span></span>
- <span data-ttu-id="764be-158">`script:` -Geeft aan dat de naam in het **script** bereik bestaat.</span><span class="sxs-lookup"><span data-stu-id="764be-158">`script:` - Specifies that the name exists in the **Script** scope.</span></span>
  <span data-ttu-id="764be-159">Het bereik van het **script** is het bereik van het dichtstbijzijnde bovenliggende script bestand of **globaal** als er zich geen dichtstbijgelegen bovenliggend script bestand bevindt.</span><span class="sxs-lookup"><span data-stu-id="764be-159">**Script** scope is the nearest ancestor script file's scope or **Global** if there is no nearest ancestor script file.</span></span>
- <span data-ttu-id="764be-160">`using:` : Wordt gebruikt voor toegang tot variabelen die in een ander bereik zijn gedefinieerd tijdens het uitvoeren van scripts via cmdlets zoals `Start-Job` en `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="764be-160">`using:` - Used to access variables defined in another scope while running scripts via cmdlets like `Start-Job` and `Invoke-Command`.</span></span>
- <span data-ttu-id="764be-161">`workflow:` -Geeft aan dat de naam bestaat in een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="764be-161">`workflow:` - Specifies that the name exists within a workflow.</span></span> <span data-ttu-id="764be-162">Opmerking: werk stromen worden niet ondersteund in Power shell core.</span><span class="sxs-lookup"><span data-stu-id="764be-162">Note: Workflows are not supported in PowerShell Core.</span></span>
- <span data-ttu-id="764be-163">`<variable-namespace>` -Een wijzigings functie die is gemaakt door een Power shell PSDrive-provider.</span><span class="sxs-lookup"><span data-stu-id="764be-163">`<variable-namespace>` - A modifier created by a PowerShell PSDrive provider.</span></span>
  <span data-ttu-id="764be-164">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="764be-164">For example:</span></span>

  |  <span data-ttu-id="764be-165">Naamruimte</span><span class="sxs-lookup"><span data-stu-id="764be-165">Namespace</span></span>  |                    <span data-ttu-id="764be-166">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="764be-166">Description</span></span>                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | <span data-ttu-id="764be-167">Aliassen die in het huidige bereik zijn gedefinieerd</span><span class="sxs-lookup"><span data-stu-id="764be-167">Aliases defined in the current scope</span></span>               |
  | `Env:`      | <span data-ttu-id="764be-168">Omgevings variabelen die zijn gedefinieerd in het huidige bereik</span><span class="sxs-lookup"><span data-stu-id="764be-168">Environment variables defined in the current scope</span></span> |
  | `Function:` | <span data-ttu-id="764be-169">Functies die zijn gedefinieerd in het huidige bereik</span><span class="sxs-lookup"><span data-stu-id="764be-169">Functions defined in the current scope</span></span>             |
  | `Variable:` | <span data-ttu-id="764be-170">Variabelen die zijn gedefinieerd in het huidige bereik</span><span class="sxs-lookup"><span data-stu-id="764be-170">Variables defined in the current scope</span></span>             |

<span data-ttu-id="764be-171">Het standaard bereik voor scripts is het script bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-171">The default scope for scripts is the script scope.</span></span> <span data-ttu-id="764be-172">Het standaard bereik voor functies en aliassen is het lokale bereik, zelfs als ze in een script zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="764be-172">The default scope for functions and aliases is the local scope, even if they are defined in a script.</span></span>

### <a name="using-scope-modifiers"></a><span data-ttu-id="764be-173">Bereik aanpassingen gebruiken</span><span class="sxs-lookup"><span data-stu-id="764be-173">Using scope modifiers</span></span>

<span data-ttu-id="764be-174">Als u het bereik van een nieuwe variabele, alias of functie wilt opgeven, gebruikt u een bereik aanpassing.</span><span class="sxs-lookup"><span data-stu-id="764be-174">To specify the scope of a new variable, alias, or function, use a scope modifier.</span></span>

<span data-ttu-id="764be-175">De syntaxis voor een bereik wijzigings functie in een variabele is:</span><span class="sxs-lookup"><span data-stu-id="764be-175">The syntax for a scope modifier in a variable is:</span></span>

```
$[<scope-modifier>:]<name> = <value>
```

<span data-ttu-id="764be-176">De syntaxis voor een bereik aanpassing in een functie is:</span><span class="sxs-lookup"><span data-stu-id="764be-176">The syntax for a scope modifier in a function is:</span></span>

```
function [<scope-modifier>:]<name> {<function-body>}
```

<span data-ttu-id="764be-177">Met de volgende opdracht, waarbij geen bereik wijziging wordt gebruikt, maakt een variabele in het huidige of **lokale** bereik:</span><span class="sxs-lookup"><span data-stu-id="764be-177">The following command, which does not use a scope modifier, creates a variable in the current or **local** scope:</span></span>

```powershell
$a = "one"
```

<span data-ttu-id="764be-178">Als u dezelfde variabele wilt maken in het **globale** bereik, gebruikt u de `global:` aanpassings functie voor het bereik:</span><span class="sxs-lookup"><span data-stu-id="764be-178">To create the same variable in the **global** scope, use the scope `global:` modifier:</span></span>

```powershell
$global:a = "one"
```

<span data-ttu-id="764be-179">Als u dezelfde variabele in het **script** bereik wilt maken, gebruikt u de `script:` aanpassings functie voor het bereik:</span><span class="sxs-lookup"><span data-stu-id="764be-179">To create the same variable in the **script** scope, use the `script:` scope modifier:</span></span>

```powershell
$script:a = "one"
```

<span data-ttu-id="764be-180">U kunt ook een bereik wijzigings functie met functies gebruiken.</span><span class="sxs-lookup"><span data-stu-id="764be-180">You can also use a scope modifier with functions.</span></span> <span data-ttu-id="764be-181">Met de volgende functie definitie maakt u een functie in het **globale** bereik:</span><span class="sxs-lookup"><span data-stu-id="764be-181">The following function definition creates a function in the **global** scope:</span></span>

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

<span data-ttu-id="764be-182">U kunt ook bereik aanpassingen gebruiken om te verwijzen naar een variabele in een ander bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-182">You can also use scope modifiers to refer to a variable in a different scope.</span></span>
<span data-ttu-id="764be-183">De volgende opdracht verwijst naar de `$test` variabele, eerst in het lokale bereik en vervolgens in het globale bereik:</span><span class="sxs-lookup"><span data-stu-id="764be-183">The following command refers to the `$test` variable, first in the local scope and then in the global scope:</span></span>

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a><span data-ttu-id="764be-184">De `Using:` aanpassing van het bereik</span><span class="sxs-lookup"><span data-stu-id="764be-184">The `Using:` scope modifier</span></span>

<span data-ttu-id="764be-185">Met is een speciale Scope wijzigings functie waarmee een lokale variabele wordt aangeduid in een externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="764be-185">Using is a special scope modifier that identifies a local variable in a remote command.</span></span> <span data-ttu-id="764be-186">Zonder een wijzigings programma verwacht Power shell variabelen in externe opdrachten die in de externe sessie moeten worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="764be-186">Without a modifier, PowerShell expects variables in remote commands to be defined in the remote session.</span></span>

<span data-ttu-id="764be-187">De `Using` aanpassing van het bereik is geïntroduceerd in Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="764be-187">The `Using` scope modifier is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="764be-188">Voor elk script of elke opdracht die uit de sessie wordt uitgevoerd, hebt u de `Using` bereik wijzigings functie nodig om variabele waarden van het aanroepende sessie bereik in te sluiten, zodat out of Session-code er toegang toe heeft.</span><span class="sxs-lookup"><span data-stu-id="764be-188">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="764be-189">De `Using` aanpassing van het bereik wordt ondersteund in de volgende contexten:</span><span class="sxs-lookup"><span data-stu-id="764be-189">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="764be-190">Extern uitgevoerde opdrachten, begonnen met `Invoke-Command` het gebruik van de **computer naam** of de **sessie** parameter (externe sessie)</span><span class="sxs-lookup"><span data-stu-id="764be-190">Remotely executed commands, started with `Invoke-Command` using the **ComputerName** or **Session** parameter (remote session)</span></span>
- <span data-ttu-id="764be-191">Achtergrond taken, begonnen met `Start-Job` (out-of-process-sessie)</span><span class="sxs-lookup"><span data-stu-id="764be-191">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="764be-192">Thread taken, gestart via `Start-ThreadJob` of `ForEach-Object -Parallel` (afzonderlijke thread sessie)</span><span class="sxs-lookup"><span data-stu-id="764be-192">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="764be-193">Afhankelijk van de context, zijn Inge sloten variabelen waarden ofwel onafhankelijke kopieën van de gegevens in het bereik of verwijzingen naar de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="764be-193">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="764be-194">In externe en out-of-process-sessies zijn ze altijd onafhankelijke kopieën.</span><span class="sxs-lookup"><span data-stu-id="764be-194">In remote and out-of-process sessions, they are always independent copies.</span></span>

<span data-ttu-id="764be-195">Zie [about_Remote_Variables](about_Remote_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="764be-195">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

<span data-ttu-id="764be-196">In thread sessies worden ze door gegeven door verwijzing.</span><span class="sxs-lookup"><span data-stu-id="764be-196">In thread sessions, they are passed by reference.</span></span> <span data-ttu-id="764be-197">Dit betekent dat het mogelijk is om de variabelen voor het aanroep bereik te wijzigen in een andere thread.</span><span class="sxs-lookup"><span data-stu-id="764be-197">This means it is possible to modify call scope variables in a different thread.</span></span> <span data-ttu-id="764be-198">Voor het veilig wijzigen van variabelen is thread synchronisatie vereist.</span><span class="sxs-lookup"><span data-stu-id="764be-198">To safely modify variables requires thread synchronization.</span></span>

<span data-ttu-id="764be-199">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="764be-199">For more information see:</span></span>

- [<span data-ttu-id="764be-200">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="764be-200">Start-ThreadJob</span></span>](/powershell/module/ThreadJob/Start-ThreadJob)

#### <a name="serialization-of-variable-values"></a><span data-ttu-id="764be-201">Serialisatie van variabele waarden</span><span class="sxs-lookup"><span data-stu-id="764be-201">Serialization of variable values</span></span>

<span data-ttu-id="764be-202">Extern uitgevoerde opdrachten en achtergrond taken worden out-of-process uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="764be-202">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="764be-203">Out-of-process-sessies gebruiken op XML gebaseerde serialisatie en deserialisatie om de waarden van variabelen beschikbaar te maken voor de grenzen van het proces.</span><span class="sxs-lookup"><span data-stu-id="764be-203">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="764be-204">Het serialization-proces converteert objecten naar een **PSObject** die de eigenschappen van de oorspronkelijke objecten bevat, maar niet de methoden ervan.</span><span class="sxs-lookup"><span data-stu-id="764be-204">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="764be-205">Voor een beperkte set typen worden objecten door deserialisatie opnieuw naar het oorspronkelijke type gehydrateerd.</span><span class="sxs-lookup"><span data-stu-id="764be-205">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="764be-206">Het opnieuw gehydrateerde object is een kopie van het oorspronkelijke object exemplaar.</span><span class="sxs-lookup"><span data-stu-id="764be-206">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="764be-207">Deze bevat de type-eigenschappen en-methoden.</span><span class="sxs-lookup"><span data-stu-id="764be-207">It has the type properties and methods.</span></span> <span data-ttu-id="764be-208">Voor eenvoudige typen, zoals **System. versie** , is de kopie gelijk.</span><span class="sxs-lookup"><span data-stu-id="764be-208">For simple types, such as **System.Version** , the copy is exact.</span></span> <span data-ttu-id="764be-209">Voor complexe typen is de kopie niet perfect.</span><span class="sxs-lookup"><span data-stu-id="764be-209">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="764be-210">Bijvoorbeeld: opnieuw gehydrateerde certificaat objecten bevatten niet de persoonlijke sleutel.</span><span class="sxs-lookup"><span data-stu-id="764be-210">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="764be-211">Exemplaren van alle andere typen zijn **PSObject** -exemplaren.</span><span class="sxs-lookup"><span data-stu-id="764be-211">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="764be-212">De eigenschap **PSTypeNames** bevat de oorspronkelijke type naam, voorafgegaan door een **gedeserialiseerd** , bijvoorbeeld **Deserialized.System. Data. DataTable**</span><span class="sxs-lookup"><span data-stu-id="764be-212">The **PSTypeNames** property contains the original type name prefixed with **Deserialized** , for example, **Deserialized.System.Data.DataTable**</span></span>

### <a name="the-allscope-option"></a><span data-ttu-id="764be-213">De optie AllScope</span><span class="sxs-lookup"><span data-stu-id="764be-213">The AllScope Option</span></span>

<span data-ttu-id="764be-214">Variabelen en aliassen hebben een **optie** -eigenschap die een waarde van **AllScope** kan hebben.</span><span class="sxs-lookup"><span data-stu-id="764be-214">Variables and aliases have an **Option** property that can take a value of **AllScope**.</span></span> <span data-ttu-id="764be-215">Items met de eigenschap **AllScope** worden deel van alle onderliggende bereiken die u maakt, hoewel ze niet met terugwerkende kracht worden overgenomen door bovenliggende bereiken.</span><span class="sxs-lookup"><span data-stu-id="764be-215">Items that have the **AllScope** property become part of any child scopes that you create, although they are not retroactively inherited by parent scopes.</span></span>

<span data-ttu-id="764be-216">Een item met de eigenschap **AllScope** is zichtbaar in het onderliggende bereik en maakt deel uit van dat bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-216">An item that has the **AllScope** property is visible in the child scope, and it is part of that scope.</span></span> <span data-ttu-id="764be-217">Wijzigingen in het item in elk bereik zijn van invloed op alle bereiken waarin de variabele is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="764be-217">Changes to the item in any scope affect all the scopes in which the variable is defined.</span></span>

### <a name="managing-scope"></a><span data-ttu-id="764be-218">Bereik beheren</span><span class="sxs-lookup"><span data-stu-id="764be-218">Managing Scope</span></span>

<span data-ttu-id="764be-219">Verschillende cmdlets hebben een **bereik** parameter waarmee u items in een bepaald bereik kunt ophalen of instellen (maken en wijzigen).</span><span class="sxs-lookup"><span data-stu-id="764be-219">Several cmdlets have a **Scope** parameter that lets you get or set (create and change) items in a particular scope.</span></span> <span data-ttu-id="764be-220">Gebruik de volgende opdracht om te zoeken naar alle cmdlets in uw sessie met een **bereik** parameter:</span><span class="sxs-lookup"><span data-stu-id="764be-220">Use the following command to find all the cmdlets in your session that have a **Scope** parameter:</span></span>

```powershell
Get-Help * -Parameter scope
```

<span data-ttu-id="764be-221">Als u de variabelen wilt vinden die zichtbaar zijn in een bepaald bereik, gebruikt u de `Scope` para meter van `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="764be-221">To find the variables that are visible in a particular scope, use the `Scope` parameter of `Get-Variable`.</span></span> <span data-ttu-id="764be-222">De zicht bare variabelen bevatten globale variabelen, variabelen in het bovenliggende bereik en variabelen in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-222">The visible variables include global variables, variables in the parent scope, and variables in the current scope.</span></span>

<span data-ttu-id="764be-223">Met de volgende opdracht worden bijvoorbeeld de variabelen opgehaald die zichtbaar zijn in het lokale bereik:</span><span class="sxs-lookup"><span data-stu-id="764be-223">For example, the following command gets the variables that are visible in the local scope:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="764be-224">Als u een variabele in een bepaald bereik wilt maken, gebruikt u een bereik wijzigings functie of de **bereik** parameter van `Set-Variable` .</span><span class="sxs-lookup"><span data-stu-id="764be-224">To create a variable in a particular scope, use a scope modifier or the **Scope** parameter of `Set-Variable`.</span></span> <span data-ttu-id="764be-225">Met de volgende opdracht maakt u een variabele in het globale bereik:</span><span class="sxs-lookup"><span data-stu-id="764be-225">The following command creates a variable in the global scope:</span></span>

```powershell
New-Variable -Scope global -Name a -Value "One"
```

<span data-ttu-id="764be-226">U kunt ook de bereik parameter van de `New-Alias` -, `Set-Alias` -of- `Get-Alias` cmdlets gebruiken om het bereik op te geven.</span><span class="sxs-lookup"><span data-stu-id="764be-226">You can also use the Scope parameter of the `New-Alias`, `Set-Alias`, or `Get-Alias` cmdlets to specify the scope.</span></span> <span data-ttu-id="764be-227">Met de volgende opdracht maakt u een alias in het globale bereik:</span><span class="sxs-lookup"><span data-stu-id="764be-227">The following command creates an alias in the global scope:</span></span>

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

<span data-ttu-id="764be-228">Als u de functies in een bepaald bereik wilt ophalen, gebruikt `Get-Item` u de cmdlet als u zich in het bereik bevindt.</span><span class="sxs-lookup"><span data-stu-id="764be-228">To get the functions in a particular scope, use the `Get-Item` cmdlet when you are in the scope.</span></span> <span data-ttu-id="764be-229">De `Get-Item` cmdlet heeft geen **bereik** parameter.</span><span class="sxs-lookup"><span data-stu-id="764be-229">The `Get-Item` cmdlet does not have a **Scope** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="764be-230">Voor de cmdlets die gebruikmaken van de **bereik** parameter, kunt u ook bereiken op aantal.</span><span class="sxs-lookup"><span data-stu-id="764be-230">For the cmdlets that use the **Scope** parameter, you can also refer to scopes by number.</span></span> <span data-ttu-id="764be-231">Met het nummer wordt de relatieve positie van het ene bereik naar het andere bepaald.</span><span class="sxs-lookup"><span data-stu-id="764be-231">The number describes the relative position of one scope to another.</span></span> <span data-ttu-id="764be-232">Scope 0 staat voor het huidige of lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-232">Scope 0 represents the current, or local, scope.</span></span> <span data-ttu-id="764be-233">Scope 1 geeft het directe bovenliggende bereik aan.</span><span class="sxs-lookup"><span data-stu-id="764be-233">Scope 1 indicates the immediate parent scope.</span></span> <span data-ttu-id="764be-234">Scope 2 geeft het bovenliggende bereik aan, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="764be-234">Scope 2 indicates the parent of the parent scope, and so on.</span></span> <span data-ttu-id="764be-235">Genummerde bereiken zijn handig als u veel recursieve bereiken hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="764be-235">Numbered scopes are useful if you have created many recursive scopes.</span></span>

### <a name="using-dot-source-notation-with-scope"></a><span data-ttu-id="764be-236">Punt bron notatie met bereik gebruiken</span><span class="sxs-lookup"><span data-stu-id="764be-236">Using Dot Source Notation with Scope</span></span>

<span data-ttu-id="764be-237">Scripts en functies volgen alle regels van het bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-237">Scripts and functions follow all the rules of scope.</span></span> <span data-ttu-id="764be-238">U maakt ze in een bepaald bereik en zijn alleen van invloed op dat bereik, tenzij u een cmdlet-para meter of een bereik aanpassings functie gebruikt om dat bereik te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="764be-238">You create them in a particular scope, and they affect only that scope unless you use a cmdlet parameter or a scope modifier to change that scope.</span></span>

<span data-ttu-id="764be-239">Maar u kunt een script of functie aan het huidige bereik toevoegen met behulp van de punt-bron notatie.</span><span class="sxs-lookup"><span data-stu-id="764be-239">But, you can add a script or function to the current scope by using dot source notation.</span></span> <span data-ttu-id="764be-240">Wanneer een script wordt uitgevoerd in het huidige bereik, worden alle functies, aliassen en variabelen die het script maakt, beschikbaar in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-240">Then, when a script runs in the current scope, any functions, aliases, and variables that the script creates are available in the current scope.</span></span>

<span data-ttu-id="764be-241">Als u een functie wilt toevoegen aan het huidige bereik, typt u een punt (.) en een spatie vóór het pad en de naam van de functie in de functie aanroep.</span><span class="sxs-lookup"><span data-stu-id="764be-241">To add a function to the current scope, type a dot (.) and a space before the path and name of the function in the function call.</span></span>

<span data-ttu-id="764be-242">Als u bijvoorbeeld het Sample.ps1 script uit de directory C:\Scripts in het script bereik (de standaard waarde voor scripts) wilt uitvoeren, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="764be-242">For example, to run the Sample.ps1 script from the C:\Scripts directory in the script scope (the default for scripts), use the following command:</span></span>

```powershell
c:\scripts\sample.ps1
```

<span data-ttu-id="764be-243">Als u het Sample.ps1 script in het lokale bereik wilt uitvoeren, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="764be-243">To run the Sample.ps1 script in the local scope, use the following command:</span></span>

```powershell
. c:\scripts.sample.ps1
```

<span data-ttu-id="764be-244">Wanneer u de aanroep operator (&) gebruikt om een functie of script uit te voeren, wordt deze niet toegevoegd aan het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-244">When you use the call operator (&) to run a function or script, it is not added to the current scope.</span></span> <span data-ttu-id="764be-245">In het volgende voor beeld wordt de aanroep operator gebruikt:</span><span class="sxs-lookup"><span data-stu-id="764be-245">The following example uses the call operator:</span></span>

```powershell
& c:\scripts.sample.ps1
```

<span data-ttu-id="764be-246">Meer informatie over de aanroep operator vindt u in [about_operators](about_operators.md).</span><span class="sxs-lookup"><span data-stu-id="764be-246">You can read more about the call operator in [about_operators](about_operators.md).</span></span>

<span data-ttu-id="764be-247">Aliassen, functies of variabelen die het Sample.ps1 script maakt, zijn niet beschikbaar in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-247">Any aliases, functions, or variables that the Sample.ps1 script creates are not available in the current scope.</span></span>

## <a name="restricting-without-scope"></a><span data-ttu-id="764be-248">Beperken zonder bereik</span><span class="sxs-lookup"><span data-stu-id="764be-248">Restricting Without Scope</span></span>

<span data-ttu-id="764be-249">Enkele Power shell-concepten zijn vergelijkbaar met de reik wijdte of interactie met het bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-249">A few PowerShell concepts are similar to scope or interact with scope.</span></span> <span data-ttu-id="764be-250">Deze concepten kunnen worden verward met het bereik of het gedrag van het bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-250">These concepts may be confused with scope or the behavior of scope.</span></span>

<span data-ttu-id="764be-251">Sessies, modules en geneste prompts zijn op zichzelf staande omgevingen, maar ze zijn geen onderliggende bereiken van het globale bereik in de sessie.</span><span class="sxs-lookup"><span data-stu-id="764be-251">Sessions, modules, and nested prompts are self-contained environments, but they are not child scopes of the global scope in the session.</span></span>

### <a name="sessions"></a><span data-ttu-id="764be-252">Sessies</span><span class="sxs-lookup"><span data-stu-id="764be-252">Sessions</span></span>

<span data-ttu-id="764be-253">Een sessie is een omgeving waarin Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="764be-253">A session is an environment in which PowerShell runs.</span></span> <span data-ttu-id="764be-254">Wanneer u een sessie op een externe computer maakt, brengt Power shell een permanente verbinding met de externe computer tot stand.</span><span class="sxs-lookup"><span data-stu-id="764be-254">When you create a session on a remote computer, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="764be-255">Met de permanente verbinding kunt u de sessie voor meerdere gerelateerde opdrachten gebruiken.</span><span class="sxs-lookup"><span data-stu-id="764be-255">The persistent connection lets you use the session for multiple related commands.</span></span>

<span data-ttu-id="764be-256">Omdat een sessie een opgenomen omgeving is, heeft deze een eigen bereik, maar een sessie is geen onderliggend bereik van de sessie waarin deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="764be-256">Because a session is a contained environment, it has its own scope, but a session is not a child scope of the session in which it was created.</span></span> <span data-ttu-id="764be-257">De sessie begint met een eigen globaal bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-257">The session starts with its own global scope.</span></span> <span data-ttu-id="764be-258">Deze scope is onafhankelijk van het globale bereik van de sessie.</span><span class="sxs-lookup"><span data-stu-id="764be-258">This scope is independent of the global scope of the session.</span></span> <span data-ttu-id="764be-259">U kunt onderliggende bereiken maken in de sessie.</span><span class="sxs-lookup"><span data-stu-id="764be-259">You can create child scopes in the session.</span></span> <span data-ttu-id="764be-260">U kunt bijvoorbeeld een script uitvoeren om een onderliggend bereik in een sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="764be-260">For example, you can run a script to create a child scope in a session.</span></span>

### <a name="modules"></a><span data-ttu-id="764be-261">Modules</span><span class="sxs-lookup"><span data-stu-id="764be-261">Modules</span></span>

<span data-ttu-id="764be-262">U kunt een Power shell-module gebruiken om Power shell-hulpprogram ma's te delen en te leveren.</span><span class="sxs-lookup"><span data-stu-id="764be-262">You can use a PowerShell module to share and deliver PowerShell tools.</span></span> <span data-ttu-id="764be-263">Een module is een eenheid die cmdlets, scripts, functies, variabelen, aliassen en andere nuttige items kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="764be-263">A module is a unit that can contain cmdlets, scripts, functions, variables, aliases, and other useful items.</span></span> <span data-ttu-id="764be-264">Tenzij expliciet gedefinieerd, zijn de items in een module niet toegankelijk buiten de module.</span><span class="sxs-lookup"><span data-stu-id="764be-264">Unless explicitly defined, the items in a module are not accessible outside the module.</span></span> <span data-ttu-id="764be-265">Daarom kunt u de module toevoegen aan uw sessie en de open bare items gebruiken zonder dat u zich zorgen hoeft te maken dat de andere items de cmdlets, scripts, functies en andere items in uw sessie kunnen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="764be-265">Therefore, you can add the module to your session and use the public items without worrying that the other items might override the cmdlets, scripts, functions, and other items in your session.</span></span>

<span data-ttu-id="764be-266">Standaard worden modules geladen in het hoogste niveau van de huidige _sessie status_ niet van de huidige _Scope_.</span><span class="sxs-lookup"><span data-stu-id="764be-266">By default, modules are loaded into the top-level of the current _session state_ not the current _scope_.</span></span> <span data-ttu-id="764be-267">De huidige sessie status kan een module sessie status of de status van de globale sessie zijn.</span><span class="sxs-lookup"><span data-stu-id="764be-267">The current session state could be a module session state or the global session state.</span></span> <span data-ttu-id="764be-268">Wanneer een module aan een sessie wordt toegevoegd, wordt het bereik niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="764be-268">Adding a module to a session does not change the scope.</span></span> <span data-ttu-id="764be-269">Als u zich in het globale bereik bevindt, worden modules geladen in de globale sessie status.</span><span class="sxs-lookup"><span data-stu-id="764be-269">If you are in the global scope, then modules are loaded into the global session state.</span></span> <span data-ttu-id="764be-270">Eventuele exports worden in de globale tabellen geplaatst.</span><span class="sxs-lookup"><span data-stu-id="764be-270">Any exports are placed into the global tables.</span></span>
<span data-ttu-id="764be-271">Als u Module2 laadt _vanuit Module1,_ wordt Module2 in de sessie status van Module1 geladen en niet de globale sessie status.</span><span class="sxs-lookup"><span data-stu-id="764be-271">If you load module2 from _within_ module1, module2 is loaded into the session state of module1 not the global session state.</span></span> <span data-ttu-id="764be-272">Exports van Module2 worden boven aan de Module1-sessie status geplaatst.</span><span class="sxs-lookup"><span data-stu-id="764be-272">Any exports from module2 are placed at the top of the module1 session state.</span></span> <span data-ttu-id="764be-273">Als u gebruikt `Import-Module -Scope local` , worden de exports in het huidige bereik object geplaatst in plaats van op het hoogste niveau.</span><span class="sxs-lookup"><span data-stu-id="764be-273">If you use `Import-Module -Scope local`, then the exports are placed into the current scope object rather than at the top level.</span></span> <span data-ttu-id="764be-274">Als u zich _in een module_ bevindt en gebruikt `Import-Module -Scope global` (of `Import-Module -Global` ) om een andere module te laden, worden die module en de export bewerkingen geladen in de status van de globale sessie in plaats van de lokale sessie status van de module.</span><span class="sxs-lookup"><span data-stu-id="764be-274">If you are _in a module_ and use `Import-Module -Scope global` (or `Import-Module -Global`) to load another module, that module and it's exports are loaded into the global session state instead of the module's local session state.</span></span> <span data-ttu-id="764be-275">Deze functie is ontworpen voor het schrijven van module voor het bewerken van modules.</span><span class="sxs-lookup"><span data-stu-id="764be-275">This feature was designed for writing module that manipulate modules.</span></span> <span data-ttu-id="764be-276">In de **WindowsCompatibility** -module worden proxy modules in de globale sessie status geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="764be-276">The **WindowsCompatibility** module does this to import proxy modules into the global session state.</span></span>

<span data-ttu-id="764be-277">Binnen de sessie status hebben modules hun eigen bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-277">Within the session state, modules have their own scope.</span></span> <span data-ttu-id="764be-278">Bekijk de volgende module `C:\temp\mod1.psm1` :</span><span class="sxs-lookup"><span data-stu-id="764be-278">Consider the following module `C:\temp\mod1.psm1`:</span></span>

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

<span data-ttu-id="764be-279">Nu maakt u een globale variabele `$a` , geeft u deze een waarde en roept u de functie **Foo** aan.</span><span class="sxs-lookup"><span data-stu-id="764be-279">Now we create a global variable `$a`, give it a value and call the function **foo**.</span></span>

```powershell
$a = "Goodbye"
foo
```

<span data-ttu-id="764be-280">De module declareert de variabele `$a` in het module bereik en de functie **Foo** voert de waarde van de variabele in beide bereiken uit.</span><span class="sxs-lookup"><span data-stu-id="764be-280">The module declares the variable `$a` in the module scope then the function **foo** outputs the value of the variable in both scopes.</span></span>

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a><span data-ttu-id="764be-281">Geneste prompts</span><span class="sxs-lookup"><span data-stu-id="764be-281">Nested Prompts</span></span>

<span data-ttu-id="764be-282">Geneste prompts hebben geen eigen bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-282">Nested prompts do not have their own scope.</span></span> <span data-ttu-id="764be-283">Wanneer u een geneste prompt invoert, is de geneste prompt een subset van de omgeving.</span><span class="sxs-lookup"><span data-stu-id="764be-283">When you enter a nested prompt, the nested prompt is a subset of the environment.</span></span> <span data-ttu-id="764be-284">Maar u blijft binnen het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-284">But, you remain within the local scope.</span></span>

<span data-ttu-id="764be-285">Scripts hebben hun eigen bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-285">Scripts do have their own scope.</span></span> <span data-ttu-id="764be-286">Als u fouten opspoort in een script en u een onderbrekings punt in het script bereikt, voert u het script bereik in.</span><span class="sxs-lookup"><span data-stu-id="764be-286">If you are debugging a script, and you reach a breakpoint in the script, you enter the script scope.</span></span>

### <a name="private-option"></a><span data-ttu-id="764be-287">Privé-optie</span><span class="sxs-lookup"><span data-stu-id="764be-287">Private Option</span></span>

<span data-ttu-id="764be-288">Aliassen en variabelen hebben een **optie** -eigenschap die de waarde **privé** kan uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="764be-288">Aliases and variables have an **Option** property that can take a value of **Private**.</span></span> <span data-ttu-id="764be-289">Items met de optie **privé** kunnen worden weer gegeven en gewijzigd in het bereik waarin ze zijn gemaakt, maar ze kunnen niet worden weer gegeven of gewijzigd buiten dat bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-289">Items that have the **Private** option can be viewed and changed in the scope in which they are created, but they cannot be viewed or changed outside that scope.</span></span>

<span data-ttu-id="764be-290">Als u bijvoorbeeld een variabele maakt met de optie privé in het globale bereik en vervolgens een script uitvoert, wordt `Get-Variable` de persoonlijke variabele niet weer gegeven in opdrachten in het script.</span><span class="sxs-lookup"><span data-stu-id="764be-290">For example, if you create a variable that has a private option in the global scope and then run a script, `Get-Variable` commands in the script do not display the private variable.</span></span> <span data-ttu-id="764be-291">Als u de para meter voor globaal bereik in dit exemplaar gebruikt, wordt de persoonlijke variabele niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="764be-291">Using the global scope modifier in this instance does not display the private variable.</span></span>

<span data-ttu-id="764be-292">U kunt de optie para meter van de `New-Variable` `Set-Variable` `New-Alias` cmdlets,, en gebruiken `Set-Alias` om de waarde van de eigenschap Option in te stellen op persoonlijk.</span><span class="sxs-lookup"><span data-stu-id="764be-292">You can use the Option parameter of the `New-Variable`, `Set-Variable`, `New-Alias`, and `Set-Alias` cmdlets to set the value of the Option property to Private.</span></span>

### <a name="visibility"></a><span data-ttu-id="764be-293">Zicht</span><span class="sxs-lookup"><span data-stu-id="764be-293">Visibility</span></span>

<span data-ttu-id="764be-294">De **zichtbaarheids** eigenschap van een variabele of alias bepaalt of u het item buiten de container kunt zien waarin het is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="764be-294">The **Visibility** property of a variable or alias determines whether you can see the item outside the container, in which it was created.</span></span> <span data-ttu-id="764be-295">Een container kan een module, script of module zijn.</span><span class="sxs-lookup"><span data-stu-id="764be-295">A container could be a module, script, or snap-in.</span></span> <span data-ttu-id="764be-296">Zicht baarheid is ontworpen voor containers op dezelfde manier als de **privé** waarde van de eigenschap **Option** is ontworpen voor scopes.</span><span class="sxs-lookup"><span data-stu-id="764be-296">Visibility is designed for containers in the same way that the **Private** value of the **Option** property is designed for scopes.</span></span>

<span data-ttu-id="764be-297">De **zichtbaarheids** eigenschap heeft de **open bare** en **persoonlijke** waarden.</span><span class="sxs-lookup"><span data-stu-id="764be-297">The **Visibility** property takes the **Public** and **Private** values.</span></span> <span data-ttu-id="764be-298">Items met een persoonlijke zicht baarheid kunnen alleen worden weer gegeven en gewijzigd in de container waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="764be-298">Items that have private visibility can be viewed and changed only in the container in which they were created.</span></span> <span data-ttu-id="764be-299">Als de container wordt toegevoegd of geïmporteerd, kunnen de items met een persoonlijke zicht baarheid niet worden weer gegeven of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="764be-299">If the container is added or imported, the items that have private visibility cannot be viewed or changed.</span></span>

<span data-ttu-id="764be-300">Omdat de zicht baarheid is ontworpen voor containers, werkt deze anders in een bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-300">Because visibility is designed for containers, it works differently in a scope.</span></span>

- <span data-ttu-id="764be-301">Als u een item maakt dat een persoonlijke zicht baarheid heeft in het globale bereik, kunt u het item in geen enkel bereik weer geven of wijzigen.</span><span class="sxs-lookup"><span data-stu-id="764be-301">If you create an item that has private visibility in the global scope, you cannot view or change the item in any scope.</span></span>
- <span data-ttu-id="764be-302">Als u de waarde van een variabele met persoonlijke zicht baarheid probeert weer te geven of te wijzigen, retourneert Power shell een fout bericht.</span><span class="sxs-lookup"><span data-stu-id="764be-302">If you try to view or change the value of a variable that has private visibility, PowerShell returns an error message.</span></span>

<span data-ttu-id="764be-303">U kunt de `New-Variable` `Set-Variable` cmdlets en gebruiken om een variabele met persoonlijke zicht baarheid te maken.</span><span class="sxs-lookup"><span data-stu-id="764be-303">You can use the `New-Variable` and `Set-Variable` cmdlets to create a variable that has private visibility.</span></span>

## <a name="examples"></a><span data-ttu-id="764be-304">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="764be-304">Examples</span></span>

### <a name="example-1-change-a-variable-value-only-in-a-script"></a><span data-ttu-id="764be-305">Voor beeld 1: een variabele waarde alleen in een script wijzigen</span><span class="sxs-lookup"><span data-stu-id="764be-305">Example 1: Change a Variable Value Only in a Script</span></span>

<span data-ttu-id="764be-306">Met de volgende opdracht wordt de waarde van de `$ConfirmPreference` variabele in een script gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="764be-306">The following command changes the value of the `$ConfirmPreference` variable in a script.</span></span> <span data-ttu-id="764be-307">De wijziging heeft geen invloed op het globale bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-307">The change does not affect the global scope.</span></span>

<span data-ttu-id="764be-308">Gebruik eerst de volgende opdracht om de waarde van de `$ConfirmPreference` variabele in het lokale bereik weer te geven:</span><span class="sxs-lookup"><span data-stu-id="764be-308">First, to display the value of the `$ConfirmPreference` variable in the local scope, use the following command:</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="764be-309">Maak een Scope.ps1-script dat de volgende opdrachten bevat:</span><span class="sxs-lookup"><span data-stu-id="764be-309">Create a Scope.ps1 script that contains the following commands:</span></span>

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

<span data-ttu-id="764be-310">Voer het script uit.</span><span class="sxs-lookup"><span data-stu-id="764be-310">Run the script.</span></span> <span data-ttu-id="764be-311">Het script wijzigt de waarde van de `$ConfirmPreference` variabele en rapporteert vervolgens de waarde in het script bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-311">The script changes the value of the `$ConfirmPreference` variable and then reports its value in the script scope.</span></span> <span data-ttu-id="764be-312">De uitvoer moet er ongeveer uitzien als in de volgende uitvoer:</span><span class="sxs-lookup"><span data-stu-id="764be-312">The output should resemble the following output:</span></span>

```output
The value of $ConfirmPreference is Low.
```

<span data-ttu-id="764be-313">Test vervolgens de huidige waarde van de `$ConfirmPreference` variabele in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-313">Next, test the current value of the `$ConfirmPreference` variable in the current scope.</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="764be-314">Dit voor beeld laat zien dat wijzigingen in de waarde van een variabele in het script bereik geen invloed hebben op de waarde van de variabele in het bovenliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-314">This example shows that changes to the value of a variable in the script scope does not affect the variable\`s value in the parent scope.</span></span>

### <a name="example-2-view-a-variable-value-in-different-scopes"></a><span data-ttu-id="764be-315">Voor beeld 2: een variabele waarde in verschillende bereiken weer geven</span><span class="sxs-lookup"><span data-stu-id="764be-315">Example 2: View a Variable Value in Different Scopes</span></span>

<span data-ttu-id="764be-316">U kunt Scope-para meters gebruiken om de waarde van een variabele in het lokale bereik en in een bovenliggend bereik weer te geven.</span><span class="sxs-lookup"><span data-stu-id="764be-316">You can use scope modifiers to view the value of a variable in the local scope and in a parent scope.</span></span>

<span data-ttu-id="764be-317">Definieer eerst een `$test` variabele in het globale bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-317">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="764be-318">Maak vervolgens een Sample.ps1 script waarmee de variabele wordt gedefinieerd `$test` .</span><span class="sxs-lookup"><span data-stu-id="764be-318">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="764be-319">Gebruik in het script een bereik aanpassings functie om te verwijzen naar de globale of lokale versies van de `$test` variabele.</span><span class="sxs-lookup"><span data-stu-id="764be-319">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="764be-320">In Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="764be-320">In Sample.ps1:</span></span>

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

<span data-ttu-id="764be-321">Wanneer u Sample.ps1 uitvoert, moet de uitvoer eruitzien als in de volgende uitvoer:</span><span class="sxs-lookup"><span data-stu-id="764be-321">When you run Sample.ps1, the output should resemble the following output:</span></span>

```output
The local value of $test is Local.
The global value of $test is Global.
```

<span data-ttu-id="764be-322">Wanneer het script is voltooid, wordt alleen de globale waarde van `$test` in de sessie gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="764be-322">When the script is complete, only the global value of `$test` is defined in the session.</span></span>

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a><span data-ttu-id="764be-323">Voor beeld 3: de waarde van een variabele in een bovenliggend bereik wijzigen</span><span class="sxs-lookup"><span data-stu-id="764be-323">Example 3: Change the Value of a Variable in a Parent Scope</span></span>

<span data-ttu-id="764be-324">Tenzij u een item beveiligt met behulp van de optie privé of een andere methode, kunt u de waarde van een variabele in een bovenliggend bereik weer geven en wijzigen.</span><span class="sxs-lookup"><span data-stu-id="764be-324">Unless you protect an item by using the Private option or another method, you can view and change the value of a variable in a parent scope.</span></span>

<span data-ttu-id="764be-325">Definieer eerst een `$test` variabele in het globale bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-325">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="764be-326">Maak vervolgens een Sample.ps1 script waarmee de variabele wordt gedefinieerd `$test` .</span><span class="sxs-lookup"><span data-stu-id="764be-326">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="764be-327">Gebruik in het script een bereik aanpassings functie om te verwijzen naar de globale of lokale versies van de `$test` variabele.</span><span class="sxs-lookup"><span data-stu-id="764be-327">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="764be-328">In Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="764be-328">In Sample.ps1:</span></span>

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

<span data-ttu-id="764be-329">Wanneer het script is voltooid, wordt de algemene waarde van `$test` gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="764be-329">When the script is complete, the global value of `$test` is changed.</span></span>

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a><span data-ttu-id="764be-330">Voor beeld 4: een persoonlijke variabele maken</span><span class="sxs-lookup"><span data-stu-id="764be-330">Example 4: Creating a Private Variable</span></span>

<span data-ttu-id="764be-331">Een persoonlijke variabele is een variabele met een **optie** -eigenschap die de waarde *privé* heeft.</span><span class="sxs-lookup"><span data-stu-id="764be-331">A private variable is a variable that has an **Option** property that has a value of *Private*.</span></span> <span data-ttu-id="764be-332">*Persoonlijke* variabelen worden overgenomen door het onderliggende bereik, maar ze kunnen alleen worden weer gegeven of gewijzigd in het bereik waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="764be-332">*Private* variables are inherited by the child scope, but they can only be viewed or changed in the scope in which they were created.</span></span>

<span data-ttu-id="764be-333">Met de volgende opdracht maakt u een persoonlijke variabele `$ptest` met de naam in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="764be-333">The following command creates a private variable called `$ptest` in the local scope.</span></span>

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

<span data-ttu-id="764be-334">U kunt de waarde van `$ptest` in het lokale bereik weer geven en wijzigen.</span><span class="sxs-lookup"><span data-stu-id="764be-334">You can display and change the value of `$ptest` in the local scope.</span></span>

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

<span data-ttu-id="764be-335">Maak vervolgens een Sample.ps1 script dat de volgende opdrachten bevat.</span><span class="sxs-lookup"><span data-stu-id="764be-335">Next, create a Sample.ps1 script that contains the following commands.</span></span> <span data-ttu-id="764be-336">De opdracht probeert de waarde van weer te geven en te wijzigen `$ptest` .</span><span class="sxs-lookup"><span data-stu-id="764be-336">The command tries to display and change the value of `$ptest`.</span></span>

<span data-ttu-id="764be-337">In Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="764be-337">In Sample.ps1:</span></span>

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

<span data-ttu-id="764be-338">De `$ptest` variabele is niet zichtbaar in het script bereik. de uitvoer is leeg.</span><span class="sxs-lookup"><span data-stu-id="764be-338">The `$ptest` variable is not visible in the script scope, the output is empty.</span></span>

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a><span data-ttu-id="764be-339">Voor beeld 5: een lokale variabele gebruiken in een externe opdracht</span><span class="sxs-lookup"><span data-stu-id="764be-339">Example 5: Using a Local Variable in a Remote Command</span></span>

<span data-ttu-id="764be-340">Voor variabelen in een externe opdracht die in de lokale sessie wordt gemaakt, gebruikt u de `Using` bereik aanpassing.</span><span class="sxs-lookup"><span data-stu-id="764be-340">For variables in a remote command created in the local session, use the `Using` scope modifier.</span></span> <span data-ttu-id="764be-341">In Power shell wordt ervan uitgegaan dat de variabelen in externe opdrachten zijn gemaakt in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="764be-341">PowerShell assumes that the variables in remote commands were created in the remote session.</span></span>

<span data-ttu-id="764be-342">De syntaxis is:</span><span class="sxs-lookup"><span data-stu-id="764be-342">The syntax is:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="764be-343">Met de volgende opdrachten maakt u bijvoorbeeld een `$Cred` variabele in de lokale sessie en gebruikt u vervolgens de `$Cred` variabele in een externe opdracht:</span><span class="sxs-lookup"><span data-stu-id="764be-343">For example, the following commands create a `$Cred` variable in the local session and then use the `$Cred` variable in a remote command:</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

<span data-ttu-id="764be-344">Het gebruik van het bereik is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="764be-344">The Using scope was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="764be-345">In Power Shell 2,0 om aan te geven dat een variabele is gemaakt in de lokale sessie, gebruikt u de volgende opdracht indeling.</span><span class="sxs-lookup"><span data-stu-id="764be-345">In PowerShell 2.0, to indicate that a variable was created in the local session, use the following command format.</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a><span data-ttu-id="764be-346">Zie ook</span><span class="sxs-lookup"><span data-stu-id="764be-346">See also</span></span>

[<span data-ttu-id="764be-347">about_Variables</span><span class="sxs-lookup"><span data-stu-id="764be-347">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="764be-348">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="764be-348">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="764be-349">about_Functions</span><span class="sxs-lookup"><span data-stu-id="764be-349">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="764be-350">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="764be-350">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="764be-351">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="764be-351">Start-ThreadJob</span></span>](/powershell/module/ThreadJob/Start-ThreadJob)
