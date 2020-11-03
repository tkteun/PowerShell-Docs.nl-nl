---
description: Hierin wordt het concept van de scope in Power shell beschreven en wordt getoond hoe u het bereik van elementen kunt instellen en wijzigen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 2149a1dec14e4de9c6ff1021e98689ca93307cb8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252083"
---
# <a name="about-scopes"></a><span data-ttu-id="9bdf6-104">Over bereiken</span><span class="sxs-lookup"><span data-stu-id="9bdf6-104">About Scopes</span></span>

## <a name="short-description"></a><span data-ttu-id="9bdf6-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="9bdf6-105">Short description</span></span>
<span data-ttu-id="9bdf6-106">Hierin wordt het concept van de scope in Power shell beschreven en wordt getoond hoe u het bereik van elementen kunt instellen en wijzigen.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-106">Explains the concept of scope in PowerShell and shows how to set and change the scope of elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="9bdf6-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="9bdf6-107">Long description</span></span>

<span data-ttu-id="9bdf6-108">Power shell beveiligt de toegang tot variabelen, aliassen, functies en Power Shell-stations (PSDrives) door te beperken waar ze kunnen worden gelezen en gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-108">PowerShell protects access to variables, aliases, functions, and PowerShell drives (PSDrives) by limiting where they can be read and changed.</span></span> <span data-ttu-id="9bdf6-109">In Power shell worden scope regels gebruikt om ervoor te zorgen dat u niet per ongeluk een item wijzigt dat niet mag worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-109">PowerShell uses scope rules to ensure that you do not inadvertently change an item that should not be changed.</span></span>

<span data-ttu-id="9bdf6-110">Hier volgen de basis regels voor het bereik:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-110">The following are the basic rules of scope:</span></span>

- <span data-ttu-id="9bdf6-111">Bereiken kunnen worden genest.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-111">Scopes may nest.</span></span> <span data-ttu-id="9bdf6-112">Een buitenste bereik wordt een bovenliggend bereik genoemd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-112">An outer scope is referred to as a parent scope.</span></span> <span data-ttu-id="9bdf6-113">Alle geneste bereiken zijn onderliggende bereiken van het bovenliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-113">Any nested scopes are child scopes of that parent.</span></span>

- <span data-ttu-id="9bdf6-114">Een item is zichtbaar in het bereik waarin het is gemaakt en in een onderliggend bereik, tenzij u het expliciet persoonlijk maakt.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-114">An item is visible in the scope in which it was created and in any child scopes, unless you explicitly make it private.</span></span> <span data-ttu-id="9bdf6-115">U kunt variabelen, aliassen, functies of Power Shell-stations in een of meer scopes plaatsen.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-115">You can place variables, aliases, functions, or PowerShell drives in one or more scopes.</span></span>

- <span data-ttu-id="9bdf6-116">Een item dat u in een bereik hebt gemaakt, kan alleen worden gewijzigd in het bereik waarin het is gemaakt, tenzij u expliciet een ander bereik opgeeft.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-116">An item that you created within a scope can be changed only in the scope in which it was created, unless you explicitly specify a different scope.</span></span>

<span data-ttu-id="9bdf6-117">Als u een item in een bereik maakt en de naam van het item is gedeeld met een item in een ander bereik, wordt het oorspronkelijke item mogelijk verborgen onder het nieuwe item, maar wordt het niet overschreven of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-117">If you create an item in a scope, and the item shares its name with an item in a different scope, the original item might be hidden under the new item, but it is not overridden or changed.</span></span>

## <a name="powershell-scopes"></a><span data-ttu-id="9bdf6-118">Power shell-bereiken</span><span class="sxs-lookup"><span data-stu-id="9bdf6-118">PowerShell Scopes</span></span>

<span data-ttu-id="9bdf6-119">Power shell ondersteunt de volgende bereiken:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-119">PowerShell supports the following scopes:</span></span>

- <span data-ttu-id="9bdf6-120">Global: de scope die van toepassing is wanneer Power shell wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-120">Global: The scope that is in effect when PowerShell starts.</span></span> <span data-ttu-id="9bdf6-121">Variabelen en functies die aanwezig zijn wanneer Power shell wordt gestart, zijn gemaakt in het globale bereik, zoals automatische variabelen en voorkeurs variabelen.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-121">Variables and functions that are present when PowerShell starts have been created in the global scope, such as automatic variables and preference variables.</span></span> <span data-ttu-id="9bdf6-122">De variabelen, aliassen en functies in uw Power shell-profielen worden ook in het globale bereik gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-122">The variables, aliases, and functions in your PowerShell profiles are also created in the global scope.</span></span>

- <span data-ttu-id="9bdf6-123">Lokaal: het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-123">Local: The current scope.</span></span> <span data-ttu-id="9bdf6-124">Het lokale bereik kan het globale bereik of een ander bereik zijn.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-124">The local scope can be the global scope or any other scope.</span></span>

- <span data-ttu-id="9bdf6-125">Script: het bereik dat is gemaakt tijdens het uitvoeren van een script bestand.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-125">Script: The scope that is created while a script file runs.</span></span> <span data-ttu-id="9bdf6-126">Alleen de opdrachten in het script worden uitgevoerd in het bereik van het script.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-126">Only the commands in the script run in the script scope.</span></span> <span data-ttu-id="9bdf6-127">Met de opdrachten in een script is het bereik van het script het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-127">To the commands in a script, the script scope is the local scope.</span></span>

> [!NOTE]
> <span data-ttu-id="9bdf6-128">**Privé** is geen bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-128">**Private** is not a scope.</span></span> <span data-ttu-id="9bdf6-129">Het is een [optie](#private-option) waarmee de zicht baarheid van een item buiten het bereik waarin het item is gedefinieerd, wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-129">It is an [option](#private-option) that changes the visibility of an item outside of the scope where the item is defined.</span></span>

## <a name="parent-and-child-scopes"></a><span data-ttu-id="9bdf6-130">Bovenliggende en onderliggende bereiken</span><span class="sxs-lookup"><span data-stu-id="9bdf6-130">Parent and Child Scopes</span></span>

<span data-ttu-id="9bdf6-131">U kunt een nieuwe scope maken door een script of functie uit te voeren door een sessie te maken of door een nieuw exemplaar van Power shell te starten.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-131">You can create a new scope by running a script or function, by creating a session, or by starting a new instance of PowerShell.</span></span> <span data-ttu-id="9bdf6-132">Wanneer u een nieuwe scope maakt, is het resultaat een bovenliggend bereik (het oorspronkelijke bereik) en een onderliggend bereik (het bereik dat u hebt gemaakt).</span><span class="sxs-lookup"><span data-stu-id="9bdf6-132">When you create a new scope, the result is a parent scope (the original scope) and a child scope (the scope that you created).</span></span>

<span data-ttu-id="9bdf6-133">In Power shell zijn alle bereiken onderliggende bereiken van het globale bereik, maar u kunt een groot aantal bereiken maken en veel recursieve bereiken.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-133">In PowerShell, all scopes are child scopes of the global scope, but you can create many scopes and many recursive scopes.</span></span>

<span data-ttu-id="9bdf6-134">Tenzij u de items expliciet aanmaakt, zijn de items in het bovenliggende bereik beschikbaar voor het onderliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-134">Unless you explicitly make the items private, the items in the parent scope are available to the child scope.</span></span> <span data-ttu-id="9bdf6-135">Items die u in het onderliggende bereik maakt en wijzigt, hebben echter geen invloed op het bovenliggende bereik, tenzij u expliciet het bereik opgeeft wanneer u de items maakt.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-135">However, items that you create and change in the child scope do not affect the parent scope, unless you explicitly specify the scope when you create the items.</span></span>

## <a name="inheritance"></a><span data-ttu-id="9bdf6-136">Overname</span><span class="sxs-lookup"><span data-stu-id="9bdf6-136">Inheritance</span></span>

<span data-ttu-id="9bdf6-137">Een onderliggend bereik neemt de variabelen, aliassen en functies niet over van het bovenliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-137">A child scope does not inherit the variables, aliases, and functions from the parent scope.</span></span> <span data-ttu-id="9bdf6-138">Tenzij een item privé is, kan het onderliggende bereik de items in het bovenliggende bereik weer geven.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-138">Unless an item is private, the child scope can view the items in the parent scope.</span></span> <span data-ttu-id="9bdf6-139">En de items kunnen worden gewijzigd door expliciet het bovenliggende bereik op te geven, maar de items maken geen deel uit van het onderliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-139">And, it can change the items by explicitly specifying the parent scope, but the items are not part of the child scope.</span></span>

<span data-ttu-id="9bdf6-140">Een onderliggend bereik wordt echter gemaakt met een set items.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-140">However, a child scope is created with a set of items.</span></span> <span data-ttu-id="9bdf6-141">Normaal gesp roken bevat het alle aliassen met de optie **AllScope** .</span><span class="sxs-lookup"><span data-stu-id="9bdf6-141">Typically, it includes all the aliases that have the **AllScope** option.</span></span> <span data-ttu-id="9bdf6-142">Deze optie wordt verderop in dit artikel besproken.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-142">This option is discussed later in this article.</span></span> <span data-ttu-id="9bdf6-143">Het bevat alle variabelen met de optie **AllScope** , plus enkele automatische variabelen.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-143">It includes all the variables that have the **AllScope** option, plus some automatic variables.</span></span>

<span data-ttu-id="9bdf6-144">Als u de items in een bepaald bereik wilt zoeken, gebruikt u de para meter bereik van `Get-Variable` of `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="9bdf6-144">To find the items in a particular scope, use the Scope parameter of `Get-Variable` or `Get-Alias`.</span></span>

<span data-ttu-id="9bdf6-145">Als u bijvoorbeeld alle variabelen in het lokale bereik wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-145">For example, to get all the variables in the local scope, type:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="9bdf6-146">Als u alle variabelen in het globale bereik wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-146">To get all the variables in the global scope, type:</span></span>

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a><span data-ttu-id="9bdf6-147">Bereik aanpassingen</span><span class="sxs-lookup"><span data-stu-id="9bdf6-147">Scope Modifiers</span></span>

<span data-ttu-id="9bdf6-148">Een variabele-, alias-of functie naam kan een van de volgende optionele Scope-para meters bevatten:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-148">A variable, alias, or function name can include any one of the following optional scope modifiers:</span></span>

- <span data-ttu-id="9bdf6-149">`global:` -Geeft aan dat de naam bestaat in het **globale** bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-149">`global:` - Specifies that the name exists in the **Global** scope.</span></span>
- <span data-ttu-id="9bdf6-150">`local:` -Geeft aan dat de naam bestaat in het **lokale** bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-150">`local:` - Specifies that the name exists in the **Local** scope.</span></span> <span data-ttu-id="9bdf6-151">Het huidige bereik is altijd het **lokale** bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-151">The current scope is always the **Local** scope.</span></span>
- <span data-ttu-id="9bdf6-152">`private:` -Geeft aan dat de naam **privé** is en alleen zichtbaar is voor de huidige scope.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-152">`private:` - Specifies that the name is **Private** and only visible to the current scope.</span></span>
- <span data-ttu-id="9bdf6-153">`script:` -Geeft aan dat de naam in het **script** bereik bestaat.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-153">`script:` - Specifies that the name exists in the **Script** scope.</span></span>
  <span data-ttu-id="9bdf6-154">Het bereik van het **script** is het bereik van het dichtstbijzijnde bovenliggende script bestand of **globaal** als er zich geen dichtstbijgelegen bovenliggend script bestand bevindt.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-154">**Script** scope is the nearest ancestor script file's scope or **Global** if there is no nearest ancestor script file.</span></span>
- <span data-ttu-id="9bdf6-155">`using:` : Wordt gebruikt voor toegang tot variabelen die in een ander bereik zijn gedefinieerd tijdens het uitvoeren van scripts via cmdlets zoals `Start-Job` en `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="9bdf6-155">`using:` - Used to access variables defined in another scope while running scripts via cmdlets like `Start-Job` and `Invoke-Command`.</span></span>
- <span data-ttu-id="9bdf6-156">`workflow:` -Geeft aan dat de naam bestaat in een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-156">`workflow:` - Specifies that the name exists within a workflow.</span></span> <span data-ttu-id="9bdf6-157">Opmerking: werk stromen worden niet ondersteund in Power shell core.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-157">Note: Workflows are not supported in PowerShell Core.</span></span>
- <span data-ttu-id="9bdf6-158">`<variable-namespace>` -Een wijzigings functie die is gemaakt door een Power shell PSDrive-provider.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-158">`<variable-namespace>` - A modifier created by a PowerShell PSDrive provider.</span></span>
  <span data-ttu-id="9bdf6-159">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-159">For example:</span></span>

  |  <span data-ttu-id="9bdf6-160">Naamruimte</span><span class="sxs-lookup"><span data-stu-id="9bdf6-160">Namespace</span></span>  |                    <span data-ttu-id="9bdf6-161">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9bdf6-161">Description</span></span>                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | <span data-ttu-id="9bdf6-162">Aliassen die in het huidige bereik zijn gedefinieerd</span><span class="sxs-lookup"><span data-stu-id="9bdf6-162">Aliases defined in the current scope</span></span>               |
  | `Env:`      | <span data-ttu-id="9bdf6-163">Omgevings variabelen die zijn gedefinieerd in het huidige bereik</span><span class="sxs-lookup"><span data-stu-id="9bdf6-163">Environment variables defined in the current scope</span></span> |
  | `Function:` | <span data-ttu-id="9bdf6-164">Functies die zijn gedefinieerd in het huidige bereik</span><span class="sxs-lookup"><span data-stu-id="9bdf6-164">Functions defined in the current scope</span></span>             |
  | `Variable:` | <span data-ttu-id="9bdf6-165">Variabelen die zijn gedefinieerd in het huidige bereik</span><span class="sxs-lookup"><span data-stu-id="9bdf6-165">Variables defined in the current scope</span></span>             |

<span data-ttu-id="9bdf6-166">Het standaard bereik voor scripts is het script bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-166">The default scope for scripts is the script scope.</span></span> <span data-ttu-id="9bdf6-167">Het standaard bereik voor functies en aliassen is het lokale bereik, zelfs als ze in een script zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-167">The default scope for functions and aliases is the local scope, even if they are defined in a script.</span></span>

### <a name="using-scope-modifiers"></a><span data-ttu-id="9bdf6-168">Bereik aanpassingen gebruiken</span><span class="sxs-lookup"><span data-stu-id="9bdf6-168">Using scope modifiers</span></span>

<span data-ttu-id="9bdf6-169">Als u het bereik van een nieuwe variabele, alias of functie wilt opgeven, gebruikt u een bereik aanpassing.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-169">To specify the scope of a new variable, alias, or function, use a scope modifier.</span></span>

<span data-ttu-id="9bdf6-170">De syntaxis voor een bereik wijzigings functie in een variabele is:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-170">The syntax for a scope modifier in a variable is:</span></span>

```
$[<scope-modifier>:]<name> = <value>
```

<span data-ttu-id="9bdf6-171">De syntaxis voor een bereik aanpassing in een functie is:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-171">The syntax for a scope modifier in a function is:</span></span>

```
function [<scope-modifier>:]<name> {<function-body>}
```

<span data-ttu-id="9bdf6-172">Met de volgende opdracht, waarbij geen bereik wijziging wordt gebruikt, maakt een variabele in het huidige of **lokale** bereik:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-172">The following command, which does not use a scope modifier, creates a variable in the current or **local** scope:</span></span>

```powershell
$a = "one"
```

<span data-ttu-id="9bdf6-173">Als u dezelfde variabele wilt maken in het **globale** bereik, gebruikt u de `global:` aanpassings functie voor het bereik:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-173">To create the same variable in the **global** scope, use the scope `global:` modifier:</span></span>

```powershell
$global:a = "one"
```

<span data-ttu-id="9bdf6-174">Als u dezelfde variabele in het **script** bereik wilt maken, gebruikt u de `script:` aanpassings functie voor het bereik:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-174">To create the same variable in the **script** scope, use the `script:` scope modifier:</span></span>

```powershell
$script:a = "one"
```

<span data-ttu-id="9bdf6-175">U kunt ook een bereik wijzigings functie met functies gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-175">You can also use a scope modifier with functions.</span></span> <span data-ttu-id="9bdf6-176">Met de volgende functie definitie maakt u een functie in het **globale** bereik:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-176">The following function definition creates a function in the **global** scope:</span></span>

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

<span data-ttu-id="9bdf6-177">U kunt ook bereik aanpassingen gebruiken om te verwijzen naar een variabele in een ander bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-177">You can also use scope modifiers to refer to a variable in a different scope.</span></span>
<span data-ttu-id="9bdf6-178">De volgende opdracht verwijst naar de `$test` variabele, eerst in het lokale bereik en vervolgens in het globale bereik:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-178">The following command refers to the `$test` variable, first in the local scope and then in the global scope:</span></span>

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a><span data-ttu-id="9bdf6-179">De `Using:` aanpassing van het bereik</span><span class="sxs-lookup"><span data-stu-id="9bdf6-179">The `Using:` scope modifier</span></span>

<span data-ttu-id="9bdf6-180">Met is een speciale Scope wijzigings functie waarmee een lokale variabele wordt aangeduid in een externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-180">Using is a special scope modifier that identifies a local variable in a remote command.</span></span> <span data-ttu-id="9bdf6-181">Zonder een wijzigings programma verwacht Power shell variabelen in externe opdrachten die in de externe sessie moeten worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-181">Without a modifier, PowerShell expects variables in remote commands to be defined in the remote session.</span></span>

<span data-ttu-id="9bdf6-182">De `Using` aanpassing van het bereik is geïntroduceerd in Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-182">The `Using` scope modifier is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="9bdf6-183">Voor elk script of elke opdracht die uit de sessie wordt uitgevoerd, hebt u de `Using` bereik wijzigings functie nodig om variabele waarden van het aanroepende sessie bereik in te sluiten, zodat out of Session-code er toegang toe heeft.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-183">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="9bdf6-184">De `Using` aanpassing van het bereik wordt ondersteund in de volgende contexten:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-184">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="9bdf6-185">Extern uitgevoerde opdrachten, begonnen met `Invoke-Command` het gebruik van **ComputerName** , **hostname** , **SSHConnection** of **Session** para meters (externe sessie)</span><span class="sxs-lookup"><span data-stu-id="9bdf6-185">Remotely executed commands, started with `Invoke-Command` using the **ComputerName** , **HostName** , **SSHConnection** or **Session** parameters (remote session)</span></span>
- <span data-ttu-id="9bdf6-186">Achtergrond taken, begonnen met `Start-Job` (out-of-process-sessie)</span><span class="sxs-lookup"><span data-stu-id="9bdf6-186">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="9bdf6-187">Thread taken, gestart via `Start-ThreadJob` of `ForEach-Object -Parallel` (afzonderlijke thread sessie)</span><span class="sxs-lookup"><span data-stu-id="9bdf6-187">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="9bdf6-188">Afhankelijk van de context, zijn Inge sloten variabelen waarden ofwel onafhankelijke kopieën van de gegevens in het bereik of verwijzingen naar de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-188">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="9bdf6-189">In externe en out-of-process-sessies zijn ze altijd onafhankelijke kopieën.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-189">In remote and out-of-process sessions, they are always independent copies.</span></span>

<span data-ttu-id="9bdf6-190">Zie [about_Remote_Variables](about_Remote_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-190">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

<span data-ttu-id="9bdf6-191">In thread sessies worden ze door gegeven door verwijzing.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-191">In thread sessions, they are passed by reference.</span></span> <span data-ttu-id="9bdf6-192">Dit betekent dat het mogelijk is om de variabelen voor het aanroep bereik te wijzigen in een andere thread.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-192">This means it is possible to modify call scope variables in a different thread.</span></span> <span data-ttu-id="9bdf6-193">Voor het veilig wijzigen van variabelen is thread synchronisatie vereist.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-193">To safely modify variables requires thread synchronization.</span></span>

<span data-ttu-id="9bdf6-194">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-194">For more information see:</span></span>

- [<span data-ttu-id="9bdf6-195">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="9bdf6-195">Start-ThreadJob</span></span>](xref:ThreadJob.Start-ThreadJob)
- [<span data-ttu-id="9bdf6-196">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="9bdf6-196">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)

#### <a name="serialization-of-variable-values"></a><span data-ttu-id="9bdf6-197">Serialisatie van variabele waarden</span><span class="sxs-lookup"><span data-stu-id="9bdf6-197">Serialization of variable values</span></span>

<span data-ttu-id="9bdf6-198">Extern uitgevoerde opdrachten en achtergrond taken worden out-of-process uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-198">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="9bdf6-199">Out-of-process-sessies gebruiken op XML gebaseerde serialisatie en deserialisatie om de waarden van variabelen beschikbaar te maken voor de grenzen van het proces.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-199">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="9bdf6-200">Het serialization-proces converteert objecten naar een **PSObject** die de eigenschappen van de oorspronkelijke objecten bevat, maar niet de methoden ervan.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-200">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="9bdf6-201">Voor een beperkte set typen worden objecten door deserialisatie opnieuw naar het oorspronkelijke type gehydrateerd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-201">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="9bdf6-202">Het opnieuw gehydrateerde object is een kopie van het oorspronkelijke object exemplaar.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-202">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="9bdf6-203">Deze bevat de type-eigenschappen en-methoden.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-203">It has the type properties and methods.</span></span> <span data-ttu-id="9bdf6-204">Voor eenvoudige typen, zoals **System. versie** , is de kopie gelijk.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-204">For simple types, such as **System.Version** , the copy is exact.</span></span> <span data-ttu-id="9bdf6-205">Voor complexe typen is de kopie niet perfect.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-205">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="9bdf6-206">Bijvoorbeeld: opnieuw gehydrateerde certificaat objecten bevatten niet de persoonlijke sleutel.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-206">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="9bdf6-207">Exemplaren van alle andere typen zijn **PSObject** -exemplaren.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-207">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="9bdf6-208">De eigenschap **PSTypeNames** bevat de oorspronkelijke type naam, voorafgegaan door een **gedeserialiseerd** , bijvoorbeeld **Deserialized.System. Data. DataTable**</span><span class="sxs-lookup"><span data-stu-id="9bdf6-208">The **PSTypeNames** property contains the original type name prefixed with **Deserialized** , for example, **Deserialized.System.Data.DataTable**</span></span>

### <a name="the-allscope-option"></a><span data-ttu-id="9bdf6-209">De optie AllScope</span><span class="sxs-lookup"><span data-stu-id="9bdf6-209">The AllScope Option</span></span>

<span data-ttu-id="9bdf6-210">Variabelen en aliassen hebben een **optie** -eigenschap die een waarde van **AllScope** kan hebben.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-210">Variables and aliases have an **Option** property that can take a value of **AllScope**.</span></span> <span data-ttu-id="9bdf6-211">Items met de eigenschap **AllScope** worden deel van alle onderliggende bereiken die u maakt, hoewel ze niet met terugwerkende kracht worden overgenomen door bovenliggende bereiken.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-211">Items that have the **AllScope** property become part of any child scopes that you create, although they are not retroactively inherited by parent scopes.</span></span>

<span data-ttu-id="9bdf6-212">Een item met de eigenschap **AllScope** is zichtbaar in het onderliggende bereik en maakt deel uit van dat bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-212">An item that has the **AllScope** property is visible in the child scope, and it is part of that scope.</span></span> <span data-ttu-id="9bdf6-213">Wijzigingen in het item in elk bereik zijn van invloed op alle bereiken waarin de variabele is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-213">Changes to the item in any scope affect all the scopes in which the variable is defined.</span></span>

### <a name="managing-scope"></a><span data-ttu-id="9bdf6-214">Bereik beheren</span><span class="sxs-lookup"><span data-stu-id="9bdf6-214">Managing Scope</span></span>

<span data-ttu-id="9bdf6-215">Verschillende cmdlets hebben een **bereik** parameter waarmee u items in een bepaald bereik kunt ophalen of instellen (maken en wijzigen).</span><span class="sxs-lookup"><span data-stu-id="9bdf6-215">Several cmdlets have a **Scope** parameter that lets you get or set (create and change) items in a particular scope.</span></span> <span data-ttu-id="9bdf6-216">Gebruik de volgende opdracht om te zoeken naar alle cmdlets in uw sessie met een **bereik** parameter:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-216">Use the following command to find all the cmdlets in your session that have a **Scope** parameter:</span></span>

```powershell
Get-Help * -Parameter scope
```

<span data-ttu-id="9bdf6-217">Als u de variabelen wilt vinden die zichtbaar zijn in een bepaald bereik, gebruikt u de `Scope` para meter van `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="9bdf6-217">To find the variables that are visible in a particular scope, use the `Scope` parameter of `Get-Variable`.</span></span> <span data-ttu-id="9bdf6-218">De zicht bare variabelen bevatten globale variabelen, variabelen in het bovenliggende bereik en variabelen in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-218">The visible variables include global variables, variables in the parent scope, and variables in the current scope.</span></span>

<span data-ttu-id="9bdf6-219">Met de volgende opdracht worden bijvoorbeeld de variabelen opgehaald die zichtbaar zijn in het lokale bereik:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-219">For example, the following command gets the variables that are visible in the local scope:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="9bdf6-220">Als u een variabele in een bepaald bereik wilt maken, gebruikt u een bereik wijzigings functie of de **bereik** parameter van `Set-Variable` .</span><span class="sxs-lookup"><span data-stu-id="9bdf6-220">To create a variable in a particular scope, use a scope modifier or the **Scope** parameter of `Set-Variable`.</span></span> <span data-ttu-id="9bdf6-221">Met de volgende opdracht maakt u een variabele in het globale bereik:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-221">The following command creates a variable in the global scope:</span></span>

```powershell
New-Variable -Scope global -Name a -Value "One"
```

<span data-ttu-id="9bdf6-222">U kunt ook de bereik parameter van de `New-Alias` -, `Set-Alias` -of- `Get-Alias` cmdlets gebruiken om het bereik op te geven.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-222">You can also use the Scope parameter of the `New-Alias`, `Set-Alias`, or `Get-Alias` cmdlets to specify the scope.</span></span> <span data-ttu-id="9bdf6-223">Met de volgende opdracht maakt u een alias in het globale bereik:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-223">The following command creates an alias in the global scope:</span></span>

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

<span data-ttu-id="9bdf6-224">Als u de functies in een bepaald bereik wilt ophalen, gebruikt `Get-Item` u de cmdlet als u zich in het bereik bevindt.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-224">To get the functions in a particular scope, use the `Get-Item` cmdlet when you are in the scope.</span></span> <span data-ttu-id="9bdf6-225">De `Get-Item` cmdlet heeft geen **bereik** parameter.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-225">The `Get-Item` cmdlet does not have a **Scope** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="9bdf6-226">Voor de cmdlets die gebruikmaken van de **bereik** parameter, kunt u ook bereiken op aantal.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-226">For the cmdlets that use the **Scope** parameter, you can also refer to scopes by number.</span></span> <span data-ttu-id="9bdf6-227">Met het nummer wordt de relatieve positie van het ene bereik naar het andere bepaald.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-227">The number describes the relative position of one scope to another.</span></span> <span data-ttu-id="9bdf6-228">Scope 0 staat voor het huidige of lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-228">Scope 0 represents the current, or local, scope.</span></span> <span data-ttu-id="9bdf6-229">Scope 1 geeft het directe bovenliggende bereik aan.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-229">Scope 1 indicates the immediate parent scope.</span></span> <span data-ttu-id="9bdf6-230">Scope 2 geeft het bovenliggende bereik aan, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-230">Scope 2 indicates the parent of the parent scope, and so on.</span></span> <span data-ttu-id="9bdf6-231">Genummerde bereiken zijn handig als u veel recursieve bereiken hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-231">Numbered scopes are useful if you have created many recursive scopes.</span></span>

### <a name="using-dot-source-notation-with-scope"></a><span data-ttu-id="9bdf6-232">Punt bron notatie met bereik gebruiken</span><span class="sxs-lookup"><span data-stu-id="9bdf6-232">Using Dot Source Notation with Scope</span></span>

<span data-ttu-id="9bdf6-233">Scripts en functies volgen alle regels van het bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-233">Scripts and functions follow all the rules of scope.</span></span> <span data-ttu-id="9bdf6-234">U maakt ze in een bepaald bereik en zijn alleen van invloed op dat bereik, tenzij u een cmdlet-para meter of een bereik aanpassings functie gebruikt om dat bereik te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-234">You create them in a particular scope, and they affect only that scope unless you use a cmdlet parameter or a scope modifier to change that scope.</span></span>

<span data-ttu-id="9bdf6-235">Maar u kunt een script of functie aan het huidige bereik toevoegen met behulp van de punt-bron notatie.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-235">But, you can add a script or function to the current scope by using dot source notation.</span></span> <span data-ttu-id="9bdf6-236">Wanneer een script wordt uitgevoerd in het huidige bereik, worden alle functies, aliassen en variabelen die het script maakt, beschikbaar in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-236">Then, when a script runs in the current scope, any functions, aliases, and variables that the script creates are available in the current scope.</span></span>

<span data-ttu-id="9bdf6-237">Als u een functie wilt toevoegen aan het huidige bereik, typt u een punt (.) en een spatie vóór het pad en de naam van de functie in de functie aanroep.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-237">To add a function to the current scope, type a dot (.) and a space before the path and name of the function in the function call.</span></span>

<span data-ttu-id="9bdf6-238">Als u bijvoorbeeld het Sample.ps1 script uit de directory C:\Scripts in het script bereik (de standaard waarde voor scripts) wilt uitvoeren, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-238">For example, to run the Sample.ps1 script from the C:\Scripts directory in the script scope (the default for scripts), use the following command:</span></span>

```powershell
c:\scripts\sample.ps1
```

<span data-ttu-id="9bdf6-239">Als u het Sample.ps1 script in het lokale bereik wilt uitvoeren, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-239">To run the Sample.ps1 script in the local scope, use the following command:</span></span>

```powershell
. c:\scripts.sample.ps1
```

<span data-ttu-id="9bdf6-240">Wanneer u de aanroep operator (&) gebruikt om een functie of script uit te voeren, wordt deze niet toegevoegd aan het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-240">When you use the call operator (&) to run a function or script, it is not added to the current scope.</span></span> <span data-ttu-id="9bdf6-241">In het volgende voor beeld wordt de aanroep operator gebruikt:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-241">The following example uses the call operator:</span></span>

```powershell
& c:\scripts.sample.ps1
```

<span data-ttu-id="9bdf6-242">Meer informatie over de aanroep operator vindt u in [about_operators](about_operators.md).</span><span class="sxs-lookup"><span data-stu-id="9bdf6-242">You can read more about the call operator in [about_operators](about_operators.md).</span></span>

<span data-ttu-id="9bdf6-243">Aliassen, functies of variabelen die het Sample.ps1 script maakt, zijn niet beschikbaar in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-243">Any aliases, functions, or variables that the Sample.ps1 script creates are not available in the current scope.</span></span>

## <a name="restricting-without-scope"></a><span data-ttu-id="9bdf6-244">Beperken zonder bereik</span><span class="sxs-lookup"><span data-stu-id="9bdf6-244">Restricting Without Scope</span></span>

<span data-ttu-id="9bdf6-245">Enkele Power shell-concepten zijn vergelijkbaar met de reik wijdte of interactie met het bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-245">A few PowerShell concepts are similar to scope or interact with scope.</span></span> <span data-ttu-id="9bdf6-246">Deze concepten kunnen worden verward met het bereik of het gedrag van het bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-246">These concepts may be confused with scope or the behavior of scope.</span></span>

<span data-ttu-id="9bdf6-247">Sessies, modules en geneste prompts zijn op zichzelf staande omgevingen, maar ze zijn geen onderliggende bereiken van het globale bereik in de sessie.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-247">Sessions, modules, and nested prompts are self-contained environments, but they are not child scopes of the global scope in the session.</span></span>

### <a name="sessions"></a><span data-ttu-id="9bdf6-248">Sessies</span><span class="sxs-lookup"><span data-stu-id="9bdf6-248">Sessions</span></span>

<span data-ttu-id="9bdf6-249">Een sessie is een omgeving waarin Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-249">A session is an environment in which PowerShell runs.</span></span> <span data-ttu-id="9bdf6-250">Wanneer u een sessie op een externe computer maakt, brengt Power shell een permanente verbinding met de externe computer tot stand.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-250">When you create a session on a remote computer, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="9bdf6-251">Met de permanente verbinding kunt u de sessie voor meerdere gerelateerde opdrachten gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-251">The persistent connection lets you use the session for multiple related commands.</span></span>

<span data-ttu-id="9bdf6-252">Omdat een sessie een opgenomen omgeving is, heeft deze een eigen bereik, maar een sessie is geen onderliggend bereik van de sessie waarin deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-252">Because a session is a contained environment, it has its own scope, but a session is not a child scope of the session in which it was created.</span></span> <span data-ttu-id="9bdf6-253">De sessie begint met een eigen globaal bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-253">The session starts with its own global scope.</span></span> <span data-ttu-id="9bdf6-254">Deze scope is onafhankelijk van het globale bereik van de sessie.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-254">This scope is independent of the global scope of the session.</span></span> <span data-ttu-id="9bdf6-255">U kunt onderliggende bereiken maken in de sessie.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-255">You can create child scopes in the session.</span></span> <span data-ttu-id="9bdf6-256">U kunt bijvoorbeeld een script uitvoeren om een onderliggend bereik in een sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-256">For example, you can run a script to create a child scope in a session.</span></span>

### <a name="modules"></a><span data-ttu-id="9bdf6-257">Modules</span><span class="sxs-lookup"><span data-stu-id="9bdf6-257">Modules</span></span>

<span data-ttu-id="9bdf6-258">U kunt een Power shell-module gebruiken om Power shell-hulpprogram ma's te delen en te leveren.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-258">You can use a PowerShell module to share and deliver PowerShell tools.</span></span> <span data-ttu-id="9bdf6-259">Een module is een eenheid die cmdlets, scripts, functies, variabelen, aliassen en andere nuttige items kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-259">A module is a unit that can contain cmdlets, scripts, functions, variables, aliases, and other useful items.</span></span> <span data-ttu-id="9bdf6-260">Tenzij expliciet gedefinieerd, zijn de items in een module niet toegankelijk buiten de module.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-260">Unless explicitly defined, the items in a module are not accessible outside the module.</span></span> <span data-ttu-id="9bdf6-261">Daarom kunt u de module toevoegen aan uw sessie en de open bare items gebruiken zonder dat u zich zorgen hoeft te maken dat de andere items de cmdlets, scripts, functies en andere items in uw sessie kunnen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-261">Therefore, you can add the module to your session and use the public items without worrying that the other items might override the cmdlets, scripts, functions, and other items in your session.</span></span>

<span data-ttu-id="9bdf6-262">Standaard worden modules geladen in het hoogste niveau van de huidige _sessie status_ niet van de huidige _Scope_.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-262">By default, modules are loaded into the top-level of the current _session state_ not the current _scope_.</span></span> <span data-ttu-id="9bdf6-263">De huidige sessie status kan een module sessie status of de status van de globale sessie zijn.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-263">The current session state could be a module session state or the global session state.</span></span> <span data-ttu-id="9bdf6-264">Wanneer een module aan een sessie wordt toegevoegd, wordt het bereik niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-264">Adding a module to a session does not change the scope.</span></span> <span data-ttu-id="9bdf6-265">Als u zich in het globale bereik bevindt, worden modules geladen in de globale sessie status.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-265">If you are in the global scope, then modules are loaded into the global session state.</span></span> <span data-ttu-id="9bdf6-266">Eventuele exports worden in de globale tabellen geplaatst.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-266">Any exports are placed into the global tables.</span></span>
<span data-ttu-id="9bdf6-267">Als u Module2 laadt _vanuit Module1,_ wordt Module2 in de sessie status van Module1 geladen en niet de globale sessie status.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-267">If you load module2 from _within_ module1, module2 is loaded into the session state of module1 not the global session state.</span></span> <span data-ttu-id="9bdf6-268">Exports van Module2 worden boven aan de Module1-sessie status geplaatst.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-268">Any exports from module2 are placed at the top of the module1 session state.</span></span> <span data-ttu-id="9bdf6-269">Als u gebruikt `Import-Module -Scope local` , worden de exports in het huidige bereik object geplaatst in plaats van op het hoogste niveau.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-269">If you use `Import-Module -Scope local`, then the exports are placed into the current scope object rather than at the top level.</span></span> <span data-ttu-id="9bdf6-270">Als u zich _in een module_ bevindt en gebruikt `Import-Module -Scope global` (of `Import-Module -Global` ) om een andere module te laden, worden die module en de export bewerkingen geladen in de status van de globale sessie in plaats van de lokale sessie status van de module.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-270">If you are _in a module_ and use `Import-Module -Scope global` (or `Import-Module -Global`) to load another module, that module and it's exports are loaded into the global session state instead of the module's local session state.</span></span> <span data-ttu-id="9bdf6-271">Deze functie is ontworpen voor het schrijven van module voor het bewerken van modules.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-271">This feature was designed for writing module that manipulate modules.</span></span> <span data-ttu-id="9bdf6-272">In de **WindowsCompatibility** -module worden proxy modules in de globale sessie status geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-272">The **WindowsCompatibility** module does this to import proxy modules into the global session state.</span></span>

<span data-ttu-id="9bdf6-273">Binnen de sessie status hebben modules hun eigen bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-273">Within the session state, modules have their own scope.</span></span> <span data-ttu-id="9bdf6-274">Bekijk de volgende module `C:\temp\mod1.psm1` :</span><span class="sxs-lookup"><span data-stu-id="9bdf6-274">Consider the following module `C:\temp\mod1.psm1`:</span></span>

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

<span data-ttu-id="9bdf6-275">Nu maakt u een globale variabele `$a` , geeft u deze een waarde en roept u de functie **Foo** aan.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-275">Now we create a global variable `$a`, give it a value and call the function **foo**.</span></span>

```powershell
$a = "Goodbye"
foo
```

<span data-ttu-id="9bdf6-276">De module declareert de variabele `$a` in het module bereik en de functie **Foo** voert de waarde van de variabele in beide bereiken uit.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-276">The module declares the variable `$a` in the module scope then the function **foo** outputs the value of the variable in both scopes.</span></span>

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a><span data-ttu-id="9bdf6-277">Geneste prompts</span><span class="sxs-lookup"><span data-stu-id="9bdf6-277">Nested Prompts</span></span>

<span data-ttu-id="9bdf6-278">Geneste prompts hebben geen eigen bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-278">Nested prompts do not have their own scope.</span></span> <span data-ttu-id="9bdf6-279">Wanneer u een geneste prompt invoert, is de geneste prompt een subset van de omgeving.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-279">When you enter a nested prompt, the nested prompt is a subset of the environment.</span></span> <span data-ttu-id="9bdf6-280">Maar u blijft binnen het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-280">But, you remain within the local scope.</span></span>

<span data-ttu-id="9bdf6-281">Scripts hebben hun eigen bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-281">Scripts do have their own scope.</span></span> <span data-ttu-id="9bdf6-282">Als u fouten opspoort in een script en u een onderbrekings punt in het script bereikt, voert u het script bereik in.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-282">If you are debugging a script, and you reach a breakpoint in the script, you enter the script scope.</span></span>

### <a name="private-option"></a><span data-ttu-id="9bdf6-283">Privé-optie</span><span class="sxs-lookup"><span data-stu-id="9bdf6-283">Private Option</span></span>

<span data-ttu-id="9bdf6-284">Aliassen en variabelen hebben een **optie** -eigenschap die de waarde **privé** kan uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-284">Aliases and variables have an **Option** property that can take a value of **Private**.</span></span> <span data-ttu-id="9bdf6-285">Items met de optie **privé** kunnen worden weer gegeven en gewijzigd in het bereik waarin ze zijn gemaakt, maar ze kunnen niet worden weer gegeven of gewijzigd buiten dat bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-285">Items that have the **Private** option can be viewed and changed in the scope in which they are created, but they cannot be viewed or changed outside that scope.</span></span>

<span data-ttu-id="9bdf6-286">Als u bijvoorbeeld een variabele maakt met de optie privé in het globale bereik en vervolgens een script uitvoert, wordt `Get-Variable` de persoonlijke variabele niet weer gegeven in opdrachten in het script.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-286">For example, if you create a variable that has a private option in the global scope and then run a script, `Get-Variable` commands in the script do not display the private variable.</span></span> <span data-ttu-id="9bdf6-287">Als u de para meter voor globaal bereik in dit exemplaar gebruikt, wordt de persoonlijke variabele niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-287">Using the global scope modifier in this instance does not display the private variable.</span></span>

<span data-ttu-id="9bdf6-288">U kunt de optie para meter van de `New-Variable` `Set-Variable` `New-Alias` cmdlets,, en gebruiken `Set-Alias` om de waarde van de eigenschap Option in te stellen op persoonlijk.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-288">You can use the Option parameter of the `New-Variable`, `Set-Variable`, `New-Alias`, and `Set-Alias` cmdlets to set the value of the Option property to Private.</span></span>

### <a name="visibility"></a><span data-ttu-id="9bdf6-289">Zicht</span><span class="sxs-lookup"><span data-stu-id="9bdf6-289">Visibility</span></span>

<span data-ttu-id="9bdf6-290">De **zichtbaarheids** eigenschap van een variabele of alias bepaalt of u het item buiten de container kunt zien waarin het is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-290">The **Visibility** property of a variable or alias determines whether you can see the item outside the container, in which it was created.</span></span> <span data-ttu-id="9bdf6-291">Een container kan een module, script of module zijn.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-291">A container could be a module, script, or snap-in.</span></span> <span data-ttu-id="9bdf6-292">Zicht baarheid is ontworpen voor containers op dezelfde manier als de **privé** waarde van de eigenschap **Option** is ontworpen voor scopes.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-292">Visibility is designed for containers in the same way that the **Private** value of the **Option** property is designed for scopes.</span></span>

<span data-ttu-id="9bdf6-293">De **zichtbaarheids** eigenschap heeft de **open bare** en **persoonlijke** waarden.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-293">The **Visibility** property takes the **Public** and **Private** values.</span></span> <span data-ttu-id="9bdf6-294">Items met een persoonlijke zicht baarheid kunnen alleen worden weer gegeven en gewijzigd in de container waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-294">Items that have private visibility can be viewed and changed only in the container in which they were created.</span></span> <span data-ttu-id="9bdf6-295">Als de container wordt toegevoegd of geïmporteerd, kunnen de items met een persoonlijke zicht baarheid niet worden weer gegeven of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-295">If the container is added or imported, the items that have private visibility cannot be viewed or changed.</span></span>

<span data-ttu-id="9bdf6-296">Omdat de zicht baarheid is ontworpen voor containers, werkt deze anders in een bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-296">Because visibility is designed for containers, it works differently in a scope.</span></span>

- <span data-ttu-id="9bdf6-297">Als u een item maakt dat een persoonlijke zicht baarheid heeft in het globale bereik, kunt u het item in geen enkel bereik weer geven of wijzigen.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-297">If you create an item that has private visibility in the global scope, you cannot view or change the item in any scope.</span></span>
- <span data-ttu-id="9bdf6-298">Als u de waarde van een variabele met persoonlijke zicht baarheid probeert weer te geven of te wijzigen, retourneert Power shell een fout bericht.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-298">If you try to view or change the value of a variable that has private visibility, PowerShell returns an error message.</span></span>

<span data-ttu-id="9bdf6-299">U kunt de `New-Variable` `Set-Variable` cmdlets en gebruiken om een variabele met persoonlijke zicht baarheid te maken.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-299">You can use the `New-Variable` and `Set-Variable` cmdlets to create a variable that has private visibility.</span></span>

## <a name="examples"></a><span data-ttu-id="9bdf6-300">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="9bdf6-300">Examples</span></span>

### <a name="example-1-change-a-variable-value-only-in-a-script"></a><span data-ttu-id="9bdf6-301">Voor beeld 1: een variabele waarde alleen in een script wijzigen</span><span class="sxs-lookup"><span data-stu-id="9bdf6-301">Example 1: Change a Variable Value Only in a Script</span></span>

<span data-ttu-id="9bdf6-302">Met de volgende opdracht wordt de waarde van de `$ConfirmPreference` variabele in een script gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-302">The following command changes the value of the `$ConfirmPreference` variable in a script.</span></span> <span data-ttu-id="9bdf6-303">De wijziging heeft geen invloed op het globale bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-303">The change does not affect the global scope.</span></span>

<span data-ttu-id="9bdf6-304">Gebruik eerst de volgende opdracht om de waarde van de `$ConfirmPreference` variabele in het lokale bereik weer te geven:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-304">First, to display the value of the `$ConfirmPreference` variable in the local scope, use the following command:</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="9bdf6-305">Maak een Scope.ps1-script dat de volgende opdrachten bevat:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-305">Create a Scope.ps1 script that contains the following commands:</span></span>

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

<span data-ttu-id="9bdf6-306">Voer het script uit.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-306">Run the script.</span></span> <span data-ttu-id="9bdf6-307">Het script wijzigt de waarde van de `$ConfirmPreference` variabele en rapporteert vervolgens de waarde in het script bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-307">The script changes the value of the `$ConfirmPreference` variable and then reports its value in the script scope.</span></span> <span data-ttu-id="9bdf6-308">De uitvoer moet er ongeveer uitzien als in de volgende uitvoer:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-308">The output should resemble the following output:</span></span>

```output
The value of $ConfirmPreference is Low.
```

<span data-ttu-id="9bdf6-309">Test vervolgens de huidige waarde van de `$ConfirmPreference` variabele in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-309">Next, test the current value of the `$ConfirmPreference` variable in the current scope.</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="9bdf6-310">Dit voor beeld laat zien dat wijzigingen in de waarde van een variabele in het script bereik geen invloed hebben op de waarde van de variabele in het bovenliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-310">This example shows that changes to the value of a variable in the script scope does not affect the variable\`s value in the parent scope.</span></span>

### <a name="example-2-view-a-variable-value-in-different-scopes"></a><span data-ttu-id="9bdf6-311">Voor beeld 2: een variabele waarde in verschillende bereiken weer geven</span><span class="sxs-lookup"><span data-stu-id="9bdf6-311">Example 2: View a Variable Value in Different Scopes</span></span>

<span data-ttu-id="9bdf6-312">U kunt Scope-para meters gebruiken om de waarde van een variabele in het lokale bereik en in een bovenliggend bereik weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-312">You can use scope modifiers to view the value of a variable in the local scope and in a parent scope.</span></span>

<span data-ttu-id="9bdf6-313">Definieer eerst een `$test` variabele in het globale bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-313">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="9bdf6-314">Maak vervolgens een Sample.ps1 script waarmee de variabele wordt gedefinieerd `$test` .</span><span class="sxs-lookup"><span data-stu-id="9bdf6-314">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="9bdf6-315">Gebruik in het script een bereik aanpassings functie om te verwijzen naar de globale of lokale versies van de `$test` variabele.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-315">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="9bdf6-316">In Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-316">In Sample.ps1:</span></span>

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

<span data-ttu-id="9bdf6-317">Wanneer u Sample.ps1 uitvoert, moet de uitvoer eruitzien als in de volgende uitvoer:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-317">When you run Sample.ps1, the output should resemble the following output:</span></span>

```output
The local value of $test is Local.
The global value of $test is Global.
```

<span data-ttu-id="9bdf6-318">Wanneer het script is voltooid, wordt alleen de globale waarde van `$test` in de sessie gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-318">When the script is complete, only the global value of `$test` is defined in the session.</span></span>

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a><span data-ttu-id="9bdf6-319">Voor beeld 3: de waarde van een variabele in een bovenliggend bereik wijzigen</span><span class="sxs-lookup"><span data-stu-id="9bdf6-319">Example 3: Change the Value of a Variable in a Parent Scope</span></span>

<span data-ttu-id="9bdf6-320">Tenzij u een item beveiligt met behulp van de optie privé of een andere methode, kunt u de waarde van een variabele in een bovenliggend bereik weer geven en wijzigen.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-320">Unless you protect an item by using the Private option or another method, you can view and change the value of a variable in a parent scope.</span></span>

<span data-ttu-id="9bdf6-321">Definieer eerst een `$test` variabele in het globale bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-321">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="9bdf6-322">Maak vervolgens een Sample.ps1 script waarmee de variabele wordt gedefinieerd `$test` .</span><span class="sxs-lookup"><span data-stu-id="9bdf6-322">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="9bdf6-323">Gebruik in het script een bereik aanpassings functie om te verwijzen naar de globale of lokale versies van de `$test` variabele.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-323">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="9bdf6-324">In Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-324">In Sample.ps1:</span></span>

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

<span data-ttu-id="9bdf6-325">Wanneer het script is voltooid, wordt de algemene waarde van `$test` gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-325">When the script is complete, the global value of `$test` is changed.</span></span>

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a><span data-ttu-id="9bdf6-326">Voor beeld 4: een persoonlijke variabele maken</span><span class="sxs-lookup"><span data-stu-id="9bdf6-326">Example 4: Creating a Private Variable</span></span>

<span data-ttu-id="9bdf6-327">Een persoonlijke variabele is een variabele met een **optie** -eigenschap die de waarde *privé* heeft.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-327">A private variable is a variable that has an **Option** property that has a value of *Private*.</span></span> <span data-ttu-id="9bdf6-328">*Persoonlijke* variabelen worden overgenomen door het onderliggende bereik, maar ze kunnen alleen worden weer gegeven of gewijzigd in het bereik waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-328">*Private* variables are inherited by the child scope, but they can only be viewed or changed in the scope in which they were created.</span></span>

<span data-ttu-id="9bdf6-329">Met de volgende opdracht maakt u een persoonlijke variabele `$ptest` met de naam in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-329">The following command creates a private variable called `$ptest` in the local scope.</span></span>

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

<span data-ttu-id="9bdf6-330">U kunt de waarde van `$ptest` in het lokale bereik weer geven en wijzigen.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-330">You can display and change the value of `$ptest` in the local scope.</span></span>

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

<span data-ttu-id="9bdf6-331">Maak vervolgens een Sample.ps1 script dat de volgende opdrachten bevat.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-331">Next, create a Sample.ps1 script that contains the following commands.</span></span> <span data-ttu-id="9bdf6-332">De opdracht probeert de waarde van weer te geven en te wijzigen `$ptest` .</span><span class="sxs-lookup"><span data-stu-id="9bdf6-332">The command tries to display and change the value of `$ptest`.</span></span>

<span data-ttu-id="9bdf6-333">In Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-333">In Sample.ps1:</span></span>

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

<span data-ttu-id="9bdf6-334">De `$ptest` variabele is niet zichtbaar in het script bereik. de uitvoer is leeg.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-334">The `$ptest` variable is not visible in the script scope, the output is empty.</span></span>

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a><span data-ttu-id="9bdf6-335">Voor beeld 5: een lokale variabele gebruiken in een externe opdracht</span><span class="sxs-lookup"><span data-stu-id="9bdf6-335">Example 5: Using a Local Variable in a Remote Command</span></span>

<span data-ttu-id="9bdf6-336">Voor variabelen in een externe opdracht die in de lokale sessie wordt gemaakt, gebruikt u de `Using` bereik aanpassing.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-336">For variables in a remote command created in the local session, use the `Using` scope modifier.</span></span> <span data-ttu-id="9bdf6-337">In Power shell wordt ervan uitgegaan dat de variabelen in externe opdrachten zijn gemaakt in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-337">PowerShell assumes that the variables in remote commands were created in the remote session.</span></span>

<span data-ttu-id="9bdf6-338">De syntaxis is:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-338">The syntax is:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="9bdf6-339">Met de volgende opdrachten maakt u bijvoorbeeld een `$Cred` variabele in de lokale sessie en gebruikt u vervolgens de `$Cred` variabele in een externe opdracht:</span><span class="sxs-lookup"><span data-stu-id="9bdf6-339">For example, the following commands create a `$Cred` variable in the local session and then use the `$Cred` variable in a remote command:</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

<span data-ttu-id="9bdf6-340">Het gebruik van het bereik is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-340">The Using scope was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="9bdf6-341">In Power Shell 2,0 om aan te geven dat een variabele is gemaakt in de lokale sessie, gebruikt u de volgende opdracht indeling.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-341">In PowerShell 2.0, to indicate that a variable was created in the local session, use the following command format.</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a><span data-ttu-id="9bdf6-342">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9bdf6-342">See also</span></span>

[<span data-ttu-id="9bdf6-343">about_Variables</span><span class="sxs-lookup"><span data-stu-id="9bdf6-343">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="9bdf6-344">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="9bdf6-344">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="9bdf6-345">about_Functions</span><span class="sxs-lookup"><span data-stu-id="9bdf6-345">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="9bdf6-346">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="9bdf6-346">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="9bdf6-347">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="9bdf6-347">Start-ThreadJob</span></span>](/powershell/module/ThreadJob/Start-ThreadJob)
