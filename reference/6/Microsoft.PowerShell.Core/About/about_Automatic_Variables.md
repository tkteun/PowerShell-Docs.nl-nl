---
description: Beschrijft variabelen waarin status informatie voor Power shell wordt opgeslagen. Deze variabelen worden gemaakt en onderhouden door Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: 863cd6cf864a40427a92f5a2eee7725eb5a73110
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252376"
---
# <a name="about-automatic-variables"></a><span data-ttu-id="44a44-105">Over automatische variabelen</span><span class="sxs-lookup"><span data-stu-id="44a44-105">About Automatic Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="44a44-106">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="44a44-106">Short description</span></span>

<span data-ttu-id="44a44-107">Beschrijft variabelen waarin status informatie voor Power shell wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="44a44-107">Describes variables that store state information for PowerShell.</span></span> <span data-ttu-id="44a44-108">Deze variabelen worden gemaakt en onderhouden door Power shell.</span><span class="sxs-lookup"><span data-stu-id="44a44-108">These variables are created and maintained by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="44a44-109">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="44a44-109">Long description</span></span>

<span data-ttu-id="44a44-110">Deze variabelen worden conceptueel gezien als alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="44a44-110">Conceptually, these variables are considered to be read-only.</span></span> <span data-ttu-id="44a44-111">Hoewel ze **kunnen** worden geschreven naar, voor achterwaartse compatibiliteit, **moeten** ze daar niet naar worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="44a44-111">Even though they **can** be written to, for backward compatibility they **should not** be written to.</span></span>

<span data-ttu-id="44a44-112">Hier volgt een lijst met de automatische variabelen in Power shell:</span><span class="sxs-lookup"><span data-stu-id="44a44-112">Here is a list of the automatic variables in PowerShell:</span></span>

### <a name=""></a>$$

<span data-ttu-id="44a44-113">Bevat het laatste token in de laatste door de sessie ontvangen regel.</span><span class="sxs-lookup"><span data-stu-id="44a44-113">Contains the last token in the last line received by the session.</span></span>

### <a name=""></a><span data-ttu-id="44a44-114">$?</span><span class="sxs-lookup"><span data-stu-id="44a44-114">$?</span></span>

<span data-ttu-id="44a44-115">Bevat de uitvoerings status van de laatste opdracht.</span><span class="sxs-lookup"><span data-stu-id="44a44-115">Contains the execution status of the last command.</span></span> <span data-ttu-id="44a44-116">Het bevat **waar** als de laatste opdracht is geslaagd en **Onwaar** als deze is mislukt.</span><span class="sxs-lookup"><span data-stu-id="44a44-116">It contains **True** if the last command succeeded and **False** if it failed.</span></span>

<span data-ttu-id="44a44-117">Voor cmdlets en geavanceerde functies die in meerdere fasen in een pijp lijn worden uitgevoerd, bijvoorbeeld in zowel `process` -als `end` -blokken, `this.WriteError()` wordt het aanroepen van of `$PSCmdlet.WriteError()` respectievelijk op elk punt ingesteld `$?` op **False** , zoals `this.ThrowTerminatingError()` en `$PSCmdlet.ThrowTerminatingError()` .</span><span class="sxs-lookup"><span data-stu-id="44a44-117">For cmdlets and advanced functions that are run at multiple stages in a pipeline, for example in both `process` and `end` blocks, calling `this.WriteError()` or `$PSCmdlet.WriteError()` respectively at any point will set `$?` to **False** , as will `this.ThrowTerminatingError()` and `$PSCmdlet.ThrowTerminatingError()`.</span></span>

<span data-ttu-id="44a44-118">De `Write-Error` cmdlet wordt altijd ingesteld `$?` op **False** direct nadat deze is uitgevoerd, maar is niet ingesteld `$?` op **False** voor een functie die deze aanroept:</span><span class="sxs-lookup"><span data-stu-id="44a44-118">The `Write-Error` cmdlet always sets `$?` to **False** immediately after it is executed, but will not set `$?` to **False** for a function calling it:</span></span>

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

<span data-ttu-id="44a44-119">Voor dit laatste doel `$PSCmdlet.WriteError()` moet in plaats daarvan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="44a44-119">For the latter purpose, `$PSCmdlet.WriteError()` should be used instead.</span></span>

<span data-ttu-id="44a44-120">Voor systeem eigen opdrachten (uitvoer bare bestanden) `$?` is ingesteld op **True** wanneer `$LASTEXITCODE` 0 is en is ingesteld op **False** wanneer `$LASTEXITCODE` een andere waarde is.</span><span class="sxs-lookup"><span data-stu-id="44a44-120">For native commands (executables), `$?` is set to **True** when `$LASTEXITCODE` is 0, and set to **False** when `$LASTEXITCODE` is any other value.</span></span>

> [!NOTE]
> <span data-ttu-id="44a44-121">Tot Power shell 7, met een instructie tussen haakjes, wordt de syntaxis van de `(...)` subexpressie `$(...)` of matrix expressie `@(...)` altijd opnieuw ingesteld `$?` op **True** , zodat deze `(Write-Error)` wordt weer gegeven `$?` als **waar**.</span><span class="sxs-lookup"><span data-stu-id="44a44-121">Until PowerShell 7, containing a statement within parentheses `(...)`, subexpression syntax `$(...)` or array expression `@(...)` always reset `$?` to **True** , so that `(Write-Error)` shows `$?` as **True**.</span></span>
> <span data-ttu-id="44a44-122">Dit is gewijzigd in Power shell 7, zodat `$?` altijd het werkelijke succes van de laatste opdracht wordt uitgevoerd in deze expressies.</span><span class="sxs-lookup"><span data-stu-id="44a44-122">This has been changed in PowerShell 7, so that `$?` will always reflect the actual success of the last command run in these expressions.</span></span>

### <a name=""></a>$^

<span data-ttu-id="44a44-123">Bevat het eerste token in de laatste regel die door de sessie is ontvangen.</span><span class="sxs-lookup"><span data-stu-id="44a44-123">Contains the first token in the last line received by the session.</span></span>

### <a name="_"></a><span data-ttu-id="44a44-124">$_</span><span class="sxs-lookup"><span data-stu-id="44a44-124">$_</span></span>

<span data-ttu-id="44a44-125">Hetzelfde als `$PSItem` .</span><span class="sxs-lookup"><span data-stu-id="44a44-125">Same as `$PSItem`.</span></span> <span data-ttu-id="44a44-126">Bevat het huidige object in het pijplijn object.</span><span class="sxs-lookup"><span data-stu-id="44a44-126">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="44a44-127">U kunt deze variabele gebruiken in opdrachten voor het uitvoeren van een actie op elk object of op geselecteerde objecten in een pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="44a44-127">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="args"></a><span data-ttu-id="44a44-128">$args</span><span class="sxs-lookup"><span data-stu-id="44a44-128">$args</span></span>

<span data-ttu-id="44a44-129">Bevat een matrix met waarden voor niet-gedeclareerde para meters die worden door gegeven aan een functie, script of script blok.</span><span class="sxs-lookup"><span data-stu-id="44a44-129">Contains an array of values for undeclared parameters that are passed to a function, script, or script block.</span></span> <span data-ttu-id="44a44-130">Wanneer u een functie maakt, kunt u de para meters declareren met behulp van het `param` sleutel woord of door een door komma's gescheiden lijst met para meters toe te voegen tussen haakjes achter de functie naam.</span><span class="sxs-lookup"><span data-stu-id="44a44-130">When you create a function, you can declare the parameters by using the `param` keyword or by adding a comma-separated list of parameters in parentheses after the function name.</span></span>

<span data-ttu-id="44a44-131">In een gebeurtenis actie bevat de `$Args` variabele objecten die de gebeurtenis argumenten vertegenwoordigen van de gebeurtenis die wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="44a44-131">In an event action, the `$Args` variable contains objects that represent the event arguments of the event that is being processed.</span></span> <span data-ttu-id="44a44-132">Deze variabele wordt alleen ingevuld in de `Action` blok kering van een gebeurtenis registratie opdracht.</span><span class="sxs-lookup"><span data-stu-id="44a44-132">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="44a44-133">De waarde van deze variabele kan ook worden gevonden in de eigenschap **SourceArgs** van het **PSEventArgs** -object dat `Get-Event` retourneert.</span><span class="sxs-lookup"><span data-stu-id="44a44-133">The value of this variable can also be found in the **SourceArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="consolefilename"></a><span data-ttu-id="44a44-134">$ConsoleFileName</span><span class="sxs-lookup"><span data-stu-id="44a44-134">$ConsoleFileName</span></span>

<span data-ttu-id="44a44-135">Bevat het pad naar het console bestand ( `.psc1` ) dat het meest recent is gebruikt in de sessie.</span><span class="sxs-lookup"><span data-stu-id="44a44-135">Contains the path of the console file (`.psc1`) that was most recently used in the session.</span></span> <span data-ttu-id="44a44-136">Deze variabele wordt ingevuld wanneer u Power shell start met de para meter **PSConsoleFile** of wanneer u de `Export-Console` cmdlet gebruikt om module namen te exporteren naar een-console bestand.</span><span class="sxs-lookup"><span data-stu-id="44a44-136">This variable is populated when you start PowerShell with the **PSConsoleFile** parameter or when you use the `Export-Console` cmdlet to export snap-in names to a console file.</span></span>

<span data-ttu-id="44a44-137">Wanneer u de `Export-Console` cmdlet zonder para meters gebruikt, wordt automatisch het console bestand bijgewerkt dat het meest recent is gebruikt in de sessie.</span><span class="sxs-lookup"><span data-stu-id="44a44-137">When you use the `Export-Console` cmdlet without parameters, it automatically updates the console file that was most recently used in the session.</span></span> <span data-ttu-id="44a44-138">U kunt deze automatische variabele gebruiken om te bepalen welk bestand moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="44a44-138">You can use this automatic variable to determine which file will be updated.</span></span>

### <a name="error"></a><span data-ttu-id="44a44-139">$Error</span><span class="sxs-lookup"><span data-stu-id="44a44-139">$Error</span></span>

<span data-ttu-id="44a44-140">Bevat een matrix met fout objecten die de meest recente fouten vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="44a44-140">Contains an array of error objects that represent the most recent errors.</span></span>
<span data-ttu-id="44a44-141">De meest recente fout is het eerste fout object in de matrix `$Error[0]` .</span><span class="sxs-lookup"><span data-stu-id="44a44-141">The most recent error is the first error object in the array `$Error[0]`.</span></span>

<span data-ttu-id="44a44-142">`$Error`Gebruik de para meter **Error Action** common met de waarde **Ignore** om te voor komen dat er een fout wordt toegevoegd aan de matrix.</span><span class="sxs-lookup"><span data-stu-id="44a44-142">To prevent an error from being added to the `$Error` array, use the **ErrorAction** common parameter with a value of **Ignore**.</span></span> <span data-ttu-id="44a44-143">Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="44a44-143">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="event"></a><span data-ttu-id="44a44-144">$Event</span><span class="sxs-lookup"><span data-stu-id="44a44-144">$Event</span></span>

<span data-ttu-id="44a44-145">Bevat een **PSEventArgs** -object dat de gebeurtenis vertegenwoordigt die wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="44a44-145">Contains a **PSEventArgs** object that represents the event that is being processed.</span></span> <span data-ttu-id="44a44-146">Deze variabele wordt alleen ingevuld binnen het `Action` blok van een gebeurtenis registratie opdracht, zoals `Register-ObjectEvent` .</span><span class="sxs-lookup"><span data-stu-id="44a44-146">This variable is populated only within the `Action` block of an event registration command, such as `Register-ObjectEvent`.</span></span> <span data-ttu-id="44a44-147">De waarde van deze variabele is hetzelfde object dat door de `Get-Event` cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-147">The value of this variable is the same object that the `Get-Event` cmdlet returns.</span></span> <span data-ttu-id="44a44-148">Daarom kunt u de eigenschappen van de variabele gebruiken `Event` , zoals `$Event.TimeGenerated` in een- `Action` script blok.</span><span class="sxs-lookup"><span data-stu-id="44a44-148">Therefore, you can use the properties of the `Event` variable, such as `$Event.TimeGenerated`, in an `Action` script block.</span></span>

### <a name="eventargs"></a><span data-ttu-id="44a44-149">$EventArgs</span><span class="sxs-lookup"><span data-stu-id="44a44-149">$EventArgs</span></span>

<span data-ttu-id="44a44-150">Bevat een object dat het eerste gebeurtenis argument vertegenwoordigt dat is afgeleid van **EventArgs** van de gebeurtenis die wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="44a44-150">Contains an object that represents the first event argument that derives from **EventArgs** of the event that is being processed.</span></span> <span data-ttu-id="44a44-151">Deze variabele wordt alleen ingevuld in de `Action` blok kering van een gebeurtenis registratie opdracht.</span><span class="sxs-lookup"><span data-stu-id="44a44-151">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="44a44-152">De waarde van deze variabele kan ook worden gevonden in de eigenschap **SourceEventArgs** van het **PSEventArgs** -object dat `Get-Event` retourneert.</span><span class="sxs-lookup"><span data-stu-id="44a44-152">The value of this variable can also be found in the **SourceEventArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="eventsubscriber"></a><span data-ttu-id="44a44-153">$EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="44a44-153">$EventSubscriber</span></span>

<span data-ttu-id="44a44-154">Bevat een **PSEventSubscriber** -object dat de gebeurtenis abonnee vertegenwoordigt van de gebeurtenis die wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="44a44-154">Contains a **PSEventSubscriber** object that represents the event subscriber of the event that is being processed.</span></span> <span data-ttu-id="44a44-155">Deze variabele wordt alleen ingevuld in de `Action` blok kering van een gebeurtenis registratie opdracht.</span><span class="sxs-lookup"><span data-stu-id="44a44-155">This variable is populated only within the `Action` block of an event registration command.</span></span> <span data-ttu-id="44a44-156">De waarde van deze variabele is hetzelfde object dat door de `Get-EventSubscriber` cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-156">The value of this variable is the same object that the `Get-EventSubscriber` cmdlet returns.</span></span>

### <a name="executioncontext"></a><span data-ttu-id="44a44-157">$ExecutionContext</span><span class="sxs-lookup"><span data-stu-id="44a44-157">$ExecutionContext</span></span>

<span data-ttu-id="44a44-158">Bevat een **EngineIntrinsics** -object dat de uitvoerings context van de Power shell-host vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="44a44-158">Contains an **EngineIntrinsics** object that represents the execution context of the PowerShell host.</span></span> <span data-ttu-id="44a44-159">U kunt deze variabele gebruiken om de uitvoerings objecten te vinden die beschikbaar zijn voor cmdlets.</span><span class="sxs-lookup"><span data-stu-id="44a44-159">You can use this variable to find the execution objects that are available to cmdlets.</span></span>

### <a name="false"></a><span data-ttu-id="44a44-160">$false</span><span class="sxs-lookup"><span data-stu-id="44a44-160">$false</span></span>

<span data-ttu-id="44a44-161">Bevat **Onwaar**.</span><span class="sxs-lookup"><span data-stu-id="44a44-161">Contains **False**.</span></span> <span data-ttu-id="44a44-162">U kunt deze variabele gebruiken om **Onwaar** in opdrachten en scripts weer te geven in plaats van de teken reeks "false" te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="44a44-162">You can use this variable to represent **False** in commands and scripts instead of using the string "false".</span></span> <span data-ttu-id="44a44-163">De teken reeks kan worden geïnterpreteerd als **True** als deze is geconverteerd naar een niet-lege teken reeks of een niet-nul-geheel getal.</span><span class="sxs-lookup"><span data-stu-id="44a44-163">The string can be interpreted as **True** if it's converted to a non-empty string or to a non-zero integer.</span></span>

### <a name="foreach"></a><span data-ttu-id="44a44-164">$foreach</span><span class="sxs-lookup"><span data-stu-id="44a44-164">$foreach</span></span>

<span data-ttu-id="44a44-165">Bevat de enumerator (niet de resulterende waarden) van een [foreach](about_ForEach.md) -lus.</span><span class="sxs-lookup"><span data-stu-id="44a44-165">Contains the enumerator (not the resulting values) of a [ForEach](about_ForEach.md) loop.</span></span> <span data-ttu-id="44a44-166">De `$ForEach` variabele bestaat alleen wanneer de `ForEach` lus wordt uitgevoerd; deze wordt verwijderd nadat de lus is voltooid.</span><span class="sxs-lookup"><span data-stu-id="44a44-166">The `$ForEach` variable exists only while the `ForEach` loop is running; it's deleted after the loop is completed.</span></span>

<span data-ttu-id="44a44-167">Opsommingen bevatten eigenschappen en methoden die u kunt gebruiken om loop waarden op te halen en de huidige loop-iteratie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="44a44-167">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="44a44-168">Zie [using enumeraties](#using-enumerators)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="44a44-168">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="home"></a><span data-ttu-id="44a44-169">$HOME</span><span class="sxs-lookup"><span data-stu-id="44a44-169">$HOME</span></span>

<span data-ttu-id="44a44-170">Bevat het volledige pad naar de basismap van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="44a44-170">Contains the full path of the user's home directory.</span></span> <span data-ttu-id="44a44-171">Deze variabele is het equivalent van de `"$env:homedrive$env:homepath"` Windows-omgevings variabelen `C:\Users\<UserName>` .</span><span class="sxs-lookup"><span data-stu-id="44a44-171">This variable is the equivalent of the `"$env:homedrive$env:homepath"` Windows environment variables, typically `C:\Users\<UserName>`.</span></span>

### <a name="host"></a><span data-ttu-id="44a44-172">$Host</span><span class="sxs-lookup"><span data-stu-id="44a44-172">$Host</span></span>

<span data-ttu-id="44a44-173">Bevat een-object dat de huidige hosttoepassing voor Power shell vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="44a44-173">Contains an object that represents the current host application for PowerShell.</span></span> <span data-ttu-id="44a44-174">U kunt deze variabele gebruiken om de huidige host in opdrachten aan te geven of om de eigenschappen van de host, zoals of of, weer te geven of te wijzigen `$Host.version` `$Host.CurrentCulture` `$host.ui.rawui.setbackgroundcolor("Red")` .</span><span class="sxs-lookup"><span data-stu-id="44a44-174">You can use this variable to represent the current host in commands or to display or change the properties of the host, such as `$Host.version` or `$Host.CurrentCulture`, or `$host.ui.rawui.setbackgroundcolor("Red")`.</span></span>

### <a name="input"></a><span data-ttu-id="44a44-175">$input</span><span class="sxs-lookup"><span data-stu-id="44a44-175">$input</span></span>

<span data-ttu-id="44a44-176">Bevat een enumerator die alle invoer inventariseert die wordt door gegeven aan een functie.</span><span class="sxs-lookup"><span data-stu-id="44a44-176">Contains an enumerator that enumerates all input that is passed to a function.</span></span> <span data-ttu-id="44a44-177">De `$input` variabele is alleen beschikbaar voor functies en script blokken (die functies zijn die geen naam zijn).</span><span class="sxs-lookup"><span data-stu-id="44a44-177">The `$input` variable is available only to functions and script blocks (which are unnamed functions).</span></span>

- <span data-ttu-id="44a44-178">In een functie zonder een `Begin` , `Process` , of `End` blok keert de `$input` variabele de verzameling van alle invoer naar de functie.</span><span class="sxs-lookup"><span data-stu-id="44a44-178">In a function without a `Begin`, `Process`, or `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

- <span data-ttu-id="44a44-179">In het `Begin` blok bevat de `$input` variabele geen gegevens.</span><span class="sxs-lookup"><span data-stu-id="44a44-179">In the `Begin` block, the `$input` variable contains no data.</span></span>

- <span data-ttu-id="44a44-180">In het `Process` blok bevat de `$input` variabele het object dat zich momenteel in de pijp lijn bevindt.</span><span class="sxs-lookup"><span data-stu-id="44a44-180">In the `Process` block, the `$input` variable contains the object that is currently in the pipeline.</span></span>

- <span data-ttu-id="44a44-181">In het `End` blok wordt met de `$input` variabele de verzameling van alle invoer in de functie opgesomd.</span><span class="sxs-lookup"><span data-stu-id="44a44-181">In the `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

  > [!NOTE]
  > <span data-ttu-id="44a44-182">U kunt de variabele niet in `$input` zowel het proces blok als het eind blok in dezelfde functie of hetzelfde script blok gebruiken.</span><span class="sxs-lookup"><span data-stu-id="44a44-182">You cannot use the `$input` variable inside both the Process block and the End block in the same function or script block.</span></span>

<span data-ttu-id="44a44-183">Omdat `$input` een enumerator is, heeft toegang tot de eigenschappen van het bestand `$input` niet langer beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="44a44-183">Since `$input` is an enumerator, accessing any of it's properties causes `$input` to no longer be available.</span></span> <span data-ttu-id="44a44-184">U kunt `$input` in een andere variabele opslaan om de eigenschappen opnieuw te gebruiken `$input` .</span><span class="sxs-lookup"><span data-stu-id="44a44-184">You can store `$input` in another variable to reuse the `$input` properties.</span></span>

<span data-ttu-id="44a44-185">Opsommingen bevatten eigenschappen en methoden die u kunt gebruiken om loop waarden op te halen en de huidige loop-iteratie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="44a44-185">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="44a44-186">Zie [using enumeraties](#using-enumerators)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="44a44-186">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="iscoreclr"></a><span data-ttu-id="44a44-187">$IsCoreCLR</span><span class="sxs-lookup"><span data-stu-id="44a44-187">$IsCoreCLR</span></span>

<span data-ttu-id="44a44-188">Bevat `$True` als de huidige sessie wordt uitgevoerd op .net core runtime (CoreCLR).</span><span class="sxs-lookup"><span data-stu-id="44a44-188">Contains `$True` if the current session is running on the .NET Core Runtime (CoreCLR).</span></span> <span data-ttu-id="44a44-189">Anders bevat `$False` .</span><span class="sxs-lookup"><span data-stu-id="44a44-189">Otherwise contains `$False`.</span></span>

### <a name="islinux"></a><span data-ttu-id="44a44-190">$IsLinux</span><span class="sxs-lookup"><span data-stu-id="44a44-190">$IsLinux</span></span>

<span data-ttu-id="44a44-191">Bevat `$True` als de huidige sessie wordt uitgevoerd op een Linux-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="44a44-191">Contains `$True` if the current session is running on a Linux operating system.</span></span>
<span data-ttu-id="44a44-192">Anders bevat `$False` .</span><span class="sxs-lookup"><span data-stu-id="44a44-192">Otherwise contains `$False`.</span></span>

### <a name="ismacos"></a><span data-ttu-id="44a44-193">$IsMacOS</span><span class="sxs-lookup"><span data-stu-id="44a44-193">$IsMacOS</span></span>

<span data-ttu-id="44a44-194">Bevat `$True` als de huidige sessie wordt uitgevoerd op een MacOS-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="44a44-194">Contains `$True` if the current session is running on a MacOS operating system.</span></span>
<span data-ttu-id="44a44-195">Anders bevat `$False` .</span><span class="sxs-lookup"><span data-stu-id="44a44-195">Otherwise contains `$False`.</span></span>

### <a name="iswindows"></a><span data-ttu-id="44a44-196">$IsWindows</span><span class="sxs-lookup"><span data-stu-id="44a44-196">$IsWindows</span></span>

<span data-ttu-id="44a44-197">Bevat `$TRUE` als de huidige sessie wordt uitgevoerd op een Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="44a44-197">Contains `$TRUE` if the current session is running on a Windows operating system.</span></span> <span data-ttu-id="44a44-198">Anders bevat `$FALSE` .</span><span class="sxs-lookup"><span data-stu-id="44a44-198">Otherwise contains `$FALSE`.</span></span>

### <a name="lastexitcode"></a><span data-ttu-id="44a44-199">$LastExitCode</span><span class="sxs-lookup"><span data-stu-id="44a44-199">$LastExitCode</span></span>

<span data-ttu-id="44a44-200">Bevat de afsluit code van het laatste op Windows gebaseerde programma dat is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-200">Contains the exit code of the last Windows-based program that was run.</span></span>

### <a name="matches"></a><span data-ttu-id="44a44-201">$Matches</span><span class="sxs-lookup"><span data-stu-id="44a44-201">$Matches</span></span>

<span data-ttu-id="44a44-202">De `Matches` variabele werkt met de `-match` `-notmatch` Opera tors en.</span><span class="sxs-lookup"><span data-stu-id="44a44-202">The `Matches` variable works with the `-match` and `-notmatch` operators.</span></span>
<span data-ttu-id="44a44-203">Wanneer u scalaire invoer verzendt naar `-match` de `-notmatch` operator OR en één overeenkomst detecteert, wordt een Booleaanse waarde geretourneerd en wordt de `$Matches` Automatische variabele gevuld met een hash-tabel van de teken reeks waarden die overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="44a44-203">When you submit scalar input to the `-match` or `-notmatch` operator, and either one detects a match, they return a Boolean value and populate the `$Matches` automatic variable with a hash table of any string values that were matched.</span></span> <span data-ttu-id="44a44-204">De `$Matches` hash-tabel kan ook worden gevuld met opnamen wanneer u reguliere expressies met de operator gebruikt `-match` .</span><span class="sxs-lookup"><span data-stu-id="44a44-204">The `$Matches` hash table can also be populated with captures when you use regular expressions with the `-match` operator.</span></span>

<span data-ttu-id="44a44-205">Zie about_Comparison_Operators voor meer informatie over de `-match` - [about_Comparison_Operators](about_comparison_operators.md)operator.</span><span class="sxs-lookup"><span data-stu-id="44a44-205">For more information about the `-match` operator, see [about_Comparison_Operators](about_comparison_operators.md).</span></span> <span data-ttu-id="44a44-206">Zie [about_Regular_Expressions](about_Regular_Expressions.md)voor meer informatie over reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="44a44-206">For more information on regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

### <a name="myinvocation"></a><span data-ttu-id="44a44-207">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="44a44-207">$MyInvocation</span></span>

<span data-ttu-id="44a44-208">Bevat informatie over de huidige opdracht, zoals de naam, para meters, parameter waarden en informatie over de manier waarop de opdracht is gestart, aangeroepen of aangeroepen, zoals de naam van het script dat de huidige opdracht heet.</span><span class="sxs-lookup"><span data-stu-id="44a44-208">Contains information about the current command, such as the name, parameters, parameter values, and information about how the command was started, called, or invoked, such as the name of the script that called the current command.</span></span>

<span data-ttu-id="44a44-209">`$MyInvocation` wordt alleen ingevuld voor scripts, functies en script blokken.</span><span class="sxs-lookup"><span data-stu-id="44a44-209">`$MyInvocation` is populated only for scripts, function, and script blocks.</span></span> <span data-ttu-id="44a44-210">U kunt de informatie in het object **System. Management. Automation. InvocationInfo** gebruiken dat `$MyInvocation` in het huidige script retourneert, zoals het pad en de bestands naam van het script ( `$MyInvocation.MyCommand.Path` ) of de naam van een functie ( `$MyInvocation.MyCommand.Name` ) om de huidige opdracht te identificeren.</span><span class="sxs-lookup"><span data-stu-id="44a44-210">You can use the information in the **System.Management.Automation.InvocationInfo** object that `$MyInvocation` returns in the current script, such as the path and file name of the script (`$MyInvocation.MyCommand.Path`) or the name of a function (`$MyInvocation.MyCommand.Name`) to identify the current command.</span></span> <span data-ttu-id="44a44-211">Dit is vooral handig om de naam van het huidige script te vinden.</span><span class="sxs-lookup"><span data-stu-id="44a44-211">This is particularly useful for finding the name of the current script.</span></span>

<span data-ttu-id="44a44-212">Vanaf Power Shell 3,0 `MyInvocation` heeft de volgende nieuwe eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="44a44-212">Beginning in PowerShell 3.0, `MyInvocation` has the following new properties.</span></span>

| <span data-ttu-id="44a44-213">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="44a44-213">Property</span></span>      | <span data-ttu-id="44a44-214">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="44a44-214">Description</span></span>                                         |
| ------------- | --------------------------------------------------- |
| <span data-ttu-id="44a44-215">**PSScriptRoot**</span><span class="sxs-lookup"><span data-stu-id="44a44-215">**PSScriptRoot**</span></span>  | <span data-ttu-id="44a44-216">Bevat het volledige pad naar het script dat is aangeroepen</span><span class="sxs-lookup"><span data-stu-id="44a44-216">Contains the full path to the script that invoked</span></span>   |
|               | <span data-ttu-id="44a44-217">de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="44a44-217">the current command.</span></span> <span data-ttu-id="44a44-218">De waarde van deze eigenschap is</span><span class="sxs-lookup"><span data-stu-id="44a44-218">The value of this property is</span></span>  |
|               | <span data-ttu-id="44a44-219">wordt alleen ingevuld wanneer de aanroeper een script is.</span><span class="sxs-lookup"><span data-stu-id="44a44-219">populated only when the caller is a script.</span></span>         |
| <span data-ttu-id="44a44-220">**PSCommandPath**</span><span class="sxs-lookup"><span data-stu-id="44a44-220">**PSCommandPath**</span></span> | <span data-ttu-id="44a44-221">Bevat het volledige pad en de bestands naam van het script</span><span class="sxs-lookup"><span data-stu-id="44a44-221">Contains the full path and file name of the script</span></span>  |
|               | <span data-ttu-id="44a44-222">die de huidige opdracht heeft aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="44a44-222">that invoked the current command.</span></span> <span data-ttu-id="44a44-223">De waarde van deze</span><span class="sxs-lookup"><span data-stu-id="44a44-223">The value of this</span></span> |
|               | <span data-ttu-id="44a44-224">de eigenschap wordt alleen ingevuld wanneer de aanroeper een</span><span class="sxs-lookup"><span data-stu-id="44a44-224">property is populated only when the caller is a</span></span>     |
|               | <span data-ttu-id="44a44-225">uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="44a44-225">script.</span></span>                                             |

<span data-ttu-id="44a44-226">In tegens telling tot de `$PSScriptRoot` en `$PSCommandPath` automatische variabelen bevatten de eigenschappen **PSScriptRoot** en **PSCommandPath** van de `$MyInvocation` Automatische variabele informatie over de aanroeper of aanroepende script, niet het huidige script.</span><span class="sxs-lookup"><span data-stu-id="44a44-226">Unlike the `$PSScriptRoot` and `$PSCommandPath` automatic variables, the **PSScriptRoot** and **PSCommandPath** properties of the `$MyInvocation` automatic variable contain information about the invoker or calling script, not the current script.</span></span>

### <a name="nestedpromptlevel"></a><span data-ttu-id="44a44-227">$NestedPromptLevel</span><span class="sxs-lookup"><span data-stu-id="44a44-227">$NestedPromptLevel</span></span>

<span data-ttu-id="44a44-228">Bevat het huidige prompt niveau.</span><span class="sxs-lookup"><span data-stu-id="44a44-228">Contains the current prompt level.</span></span> <span data-ttu-id="44a44-229">Een waarde van 0 geeft aan dat het oorspronkelijke prompt niveau is.</span><span class="sxs-lookup"><span data-stu-id="44a44-229">A value of 0 indicates the original prompt level.</span></span> <span data-ttu-id="44a44-230">De waarde wordt verhoogd wanneer u een genest niveau invoert en afneemt wanneer u het afsluit.</span><span class="sxs-lookup"><span data-stu-id="44a44-230">The value is incremented when you enter a nested level and decremented when you exit it.</span></span>

<span data-ttu-id="44a44-231">Power shell presenteert bijvoorbeeld een genest opdracht prompt wanneer u de- `$Host.EnterNestedPrompt` methode gebruikt.</span><span class="sxs-lookup"><span data-stu-id="44a44-231">For example, PowerShell presents a nested command prompt when you use the `$Host.EnterNestedPrompt` method.</span></span> <span data-ttu-id="44a44-232">Power shell presenteert ook een geneste opdracht prompt wanneer u een onderbrekings punt in het Power Shell-fout opsporingsprogramma bereikt.</span><span class="sxs-lookup"><span data-stu-id="44a44-232">PowerShell also presents a nested command prompt when you reach a breakpoint in the PowerShell debugger.</span></span>

<span data-ttu-id="44a44-233">Wanneer u een geneste prompt invoert, wordt de huidige opdracht door Power shell onderbroken, wordt de uitvoerings context opgeslagen en wordt de waarde van de `$NestedPromptLevel` variabele verhoogd.</span><span class="sxs-lookup"><span data-stu-id="44a44-233">When you enter a nested prompt, PowerShell pauses the current command, saves the execution context, and increments the value of the `$NestedPromptLevel` variable.</span></span> <span data-ttu-id="44a44-234">Als u extra geneste opdracht prompts wilt maken (Maxi maal 128 niveaus) of als u wilt terugkeren naar de oorspronkelijke opdracht prompt, voltooit u de opdracht of typt u `exit` .</span><span class="sxs-lookup"><span data-stu-id="44a44-234">To create additional nested command prompts (up to 128 levels) or to return to the original command prompt, complete the command, or type `exit`.</span></span>

<span data-ttu-id="44a44-235">De `$NestedPromptLevel` variabele helpt u bij het volgen van het prompt niveau.</span><span class="sxs-lookup"><span data-stu-id="44a44-235">The `$NestedPromptLevel` variable helps you track the prompt level.</span></span> <span data-ttu-id="44a44-236">U kunt een alternatieve Power shell-opdracht prompt met daarin deze waarde maken zodat deze altijd zichtbaar is.</span><span class="sxs-lookup"><span data-stu-id="44a44-236">You can create an alternative PowerShell command prompt that includes this value so that it's always visible.</span></span>

### <a name="null"></a><span data-ttu-id="44a44-237">$null</span><span class="sxs-lookup"><span data-stu-id="44a44-237">$null</span></span>

<span data-ttu-id="44a44-238">`$null` is een automatische variabele die een **Null** of lege waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="44a44-238">`$null` is an automatic variable that contains a **null** or empty value.</span></span> <span data-ttu-id="44a44-239">U kunt deze variabele gebruiken om een ontbrekende of niet-gedefinieerde waarde te vertegenwoordigen in opdrachten en scripts.</span><span class="sxs-lookup"><span data-stu-id="44a44-239">You can use this variable to represent an absent or undefined value in commands and scripts.</span></span>

<span data-ttu-id="44a44-240">Power shell behandelt `$null` als een object met een waarde, dat wil zeggen, als een expliciete tijdelijke aanduiding, zodat u kunt gebruiken `$null` om een lege waarde in een reeks waarden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="44a44-240">PowerShell treats `$null` as an object with a value, that is, as an explicit placeholder, so you can use `$null` to represent an empty value in a series of values.</span></span>

<span data-ttu-id="44a44-241">Als bijvoorbeeld `$null` is opgenomen in een verzameling, wordt deze geteld als een van de objecten.</span><span class="sxs-lookup"><span data-stu-id="44a44-241">For example, when `$null` is included in a collection, it's counted as one of the objects.</span></span>

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

<span data-ttu-id="44a44-242">Als u de `$null` variabele naar de cmdlet pipet `ForEach-Object` , wordt er een waarde voor gegenereerd `$null` , net zoals voor de andere objecten</span><span class="sxs-lookup"><span data-stu-id="44a44-242">If you pipe the `$null` variable to the `ForEach-Object` cmdlet, it generates a value for `$null`, just as it does for the other objects</span></span>

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

<span data-ttu-id="44a44-243">Als gevolg hiervan kunt u `$null` **geen parameter waarde** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="44a44-243">As a result, you can't use `$null` to mean **no parameter value**.</span></span> <span data-ttu-id="44a44-244">Een parameter waarde van `$null` overschrijft de standaard parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="44a44-244">A parameter value of `$null` overrides the default parameter value.</span></span>

<span data-ttu-id="44a44-245">Omdat Power shell de `$null` variabele echter als tijdelijke aanduiding beschouwt, kunt u deze gebruiken in scripts zoals de volgende, wat niet zou kunnen werken als ze worden `$null` genegeerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-245">However, because PowerShell treats the `$null` variable as a placeholder, you can use it in scripts like the following one, which wouldn't work if `$null` were ignored.</span></span>

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a><span data-ttu-id="44a44-246">$PID</span><span class="sxs-lookup"><span data-stu-id="44a44-246">$PID</span></span>

<span data-ttu-id="44a44-247">Bevat de proces-id (PID) van het proces dat als host fungeert voor de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="44a44-247">Contains the process identifier (PID) of the process that is hosting the current PowerShell session.</span></span>

### <a name="profile"></a><span data-ttu-id="44a44-248">$PROFILE</span><span class="sxs-lookup"><span data-stu-id="44a44-248">$PROFILE</span></span>

<span data-ttu-id="44a44-249">Bevat het volledige pad van het Power shell-profiel voor de huidige gebruiker en de huidige host-toepassing.</span><span class="sxs-lookup"><span data-stu-id="44a44-249">Contains the full path of the PowerShell profile for the current user and the current host application.</span></span> <span data-ttu-id="44a44-250">U kunt deze variabele gebruiken om het profiel in opdrachten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="44a44-250">You can use this variable to represent the profile in commands.</span></span> <span data-ttu-id="44a44-251">U kunt deze bijvoorbeeld in een opdracht gebruiken om te bepalen of er een profiel is gemaakt:</span><span class="sxs-lookup"><span data-stu-id="44a44-251">For example, you can use it in a command to determine whether a profile has been created:</span></span>

```powershell
Test-Path $PROFILE
```

<span data-ttu-id="44a44-252">Of u kunt deze gebruiken in een opdracht voor het maken van een profiel:</span><span class="sxs-lookup"><span data-stu-id="44a44-252">Or, you can use it in a command to create a profile:</span></span>

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

<span data-ttu-id="44a44-253">U kunt dit in een opdracht gebruiken om het profiel in **notepad.exe** te openen:</span><span class="sxs-lookup"><span data-stu-id="44a44-253">You can use it in a command to open the profile in **notepad.exe** :</span></span>

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a><span data-ttu-id="44a44-254">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="44a44-254">$PSBoundParameters</span></span>

<span data-ttu-id="44a44-255">Bevat een woorden lijst van de para meters die worden door gegeven aan een script of functie en de huidige waarden.</span><span class="sxs-lookup"><span data-stu-id="44a44-255">Contains a dictionary of the parameters that are passed to a script or function and their current values.</span></span> <span data-ttu-id="44a44-256">Deze variabele heeft alleen een waarde in een bereik waarvoor para meters zijn gedeclareerd, zoals een script of functie.</span><span class="sxs-lookup"><span data-stu-id="44a44-256">This variable has a value only in a scope where parameters are declared, such as a script or function.</span></span> <span data-ttu-id="44a44-257">U kunt deze gebruiken om de huidige waarden van para meters weer te geven of te wijzigen of om parameter waarden door te geven aan een ander script of een functie.</span><span class="sxs-lookup"><span data-stu-id="44a44-257">You can use it to display or change the current values of parameters or to pass parameter values to another script or function.</span></span>

<span data-ttu-id="44a44-258">In dit voor beeld wordt de functie **Test2** door gegeven `$PSBoundParameters` aan de functie **test1** .</span><span class="sxs-lookup"><span data-stu-id="44a44-258">In this example, the **Test2** function passes the `$PSBoundParameters` to the **Test1** function.</span></span> <span data-ttu-id="44a44-259">De `$PSBoundParameters` worden weer gegeven in de indeling **sleutel** en **waarde**.</span><span class="sxs-lookup"><span data-stu-id="44a44-259">The `$PSBoundParameters` are displayed in the format of **Key** and **Value**.</span></span>

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a><span data-ttu-id="44a44-260">$PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="44a44-260">$PSCmdlet</span></span>

<span data-ttu-id="44a44-261">Bevat een-object dat de cmdlet of geavanceerde functie vertegenwoordigt die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-261">Contains an object that represents the cmdlet or advanced function that's being run.</span></span>

<span data-ttu-id="44a44-262">U kunt de eigenschappen en methoden van het object in uw cmdlet of functie code gebruiken om te reageren op de gebruiks voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="44a44-262">You can use the properties and methods of the object in your cmdlet or function code to respond to the conditions of use.</span></span> <span data-ttu-id="44a44-263">De eigenschap **ParameterSetName** bevat bijvoorbeeld de naam van de para meter die wordt gebruikt en de methode **ShouldProcess** voegt de **WhatIf** en **de para** meters voor de cmdlet dynamisch toe.</span><span class="sxs-lookup"><span data-stu-id="44a44-263">For example, the **ParameterSetName** property contains the name of the parameter set that's being used, and the **ShouldProcess** method adds the **WhatIf** and **Confirm** parameters to the cmdlet dynamically.</span></span>

<span data-ttu-id="44a44-264">`$PSCmdlet`Zie [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) en [about_Functions_Advanced](about_Functions_Advanced.md)voor meer informatie over de automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="44a44-264">For more information about the `$PSCmdlet` automatic variable, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

### <a name="pscommandpath"></a><span data-ttu-id="44a44-265">$PSCommandPath</span><span class="sxs-lookup"><span data-stu-id="44a44-265">$PSCommandPath</span></span>

<span data-ttu-id="44a44-266">Bevat het volledige pad en de bestands naam van het script dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-266">Contains the full path and file name of the script that's being run.</span></span> <span data-ttu-id="44a44-267">Deze variabele is in alle scripts geldig.</span><span class="sxs-lookup"><span data-stu-id="44a44-267">This variable is valid in all scripts.</span></span>

### <a name="psculture"></a><span data-ttu-id="44a44-268">$PSCulture</span><span class="sxs-lookup"><span data-stu-id="44a44-268">$PSCulture</span></span>

<span data-ttu-id="44a44-269">Bevat de naam van de cultuur die momenteel wordt gebruikt in het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="44a44-269">Contains the name of the culture currently in use in the operating system.</span></span> <span data-ttu-id="44a44-270">De cultuur bepaalt de weergave notatie van items, zoals getallen, valuta's en datums, en wordt opgeslagen in een object **System. Globalization. Culture info** .</span><span class="sxs-lookup"><span data-stu-id="44a44-270">The culture determines the display format of items such as numbers, currency, and dates, and is stored in a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="44a44-271">Gebruiken `Get-Culture` om de cultuur van de computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="44a44-271">Use `Get-Culture` to display the computer's culture.</span></span> <span data-ttu-id="44a44-272">`$PSCulture` bevat de waarde van de eigenschap **naam** .</span><span class="sxs-lookup"><span data-stu-id="44a44-272">`$PSCulture` contains the **Name** property's value.</span></span>

### <a name="psdebugcontext"></a><span data-ttu-id="44a44-273">$PSDebugContext</span><span class="sxs-lookup"><span data-stu-id="44a44-273">$PSDebugContext</span></span>

<span data-ttu-id="44a44-274">Bij het opsporen van fouten bevat deze variabele informatie over de fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="44a44-274">While debugging, this variable contains information about the debugging environment.</span></span> <span data-ttu-id="44a44-275">Anders bevat het een **Null** -waarde.</span><span class="sxs-lookup"><span data-stu-id="44a44-275">Otherwise, it contains a **null** value.</span></span> <span data-ttu-id="44a44-276">Als gevolg hiervan kunt u deze gebruiken om aan te geven of het fout opsporingsprogramma controle heeft.</span><span class="sxs-lookup"><span data-stu-id="44a44-276">As a result, you can use it to indicate whether the debugger has control.</span></span> <span data-ttu-id="44a44-277">Bij het invullen bevat deze een **PsDebugContext** -object met **onderbrekings punten** en eigenschappen **InvocationInfo** .</span><span class="sxs-lookup"><span data-stu-id="44a44-277">When populated, it contains a **PsDebugContext** object that has **Breakpoints** and **InvocationInfo** properties.</span></span> <span data-ttu-id="44a44-278">De eigenschap **InvocationInfo** heeft verschillende nuttige eigenschappen, waaronder de **locatie** -eigenschap.</span><span class="sxs-lookup"><span data-stu-id="44a44-278">The **InvocationInfo** property has several useful properties, including the **Location** property.</span></span> <span data-ttu-id="44a44-279">De eigenschap **Location** geeft het pad van het script aan waarvoor fouten worden opgespoord.</span><span class="sxs-lookup"><span data-stu-id="44a44-279">The **Location** property indicates the path of the script that is being debugged.</span></span>

### <a name="pshome"></a><span data-ttu-id="44a44-280">$PSHOME</span><span class="sxs-lookup"><span data-stu-id="44a44-280">$PSHOME</span></span>

<span data-ttu-id="44a44-281">Bevat het volledige pad van de installatie directory voor Power shell, meestal `$env:windir\System32\PowerShell\v1.0` in Windows-systemen.</span><span class="sxs-lookup"><span data-stu-id="44a44-281">Contains the full path of the installation directory for PowerShell, typically, `$env:windir\System32\PowerShell\v1.0` in Windows systems.</span></span> <span data-ttu-id="44a44-282">U kunt deze variabele gebruiken in de paden van Power Shell-bestanden.</span><span class="sxs-lookup"><span data-stu-id="44a44-282">You can use this variable in the paths of PowerShell files.</span></span> <span data-ttu-id="44a44-283">De volgende opdracht zoekt bijvoorbeeld naar de conceptuele Help-onderwerpen voor de **variabele** woord:</span><span class="sxs-lookup"><span data-stu-id="44a44-283">For example, the following command searches the conceptual Help topics for the word **variable** :</span></span>

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a><span data-ttu-id="44a44-284">$PSItem</span><span class="sxs-lookup"><span data-stu-id="44a44-284">$PSItem</span></span>

<span data-ttu-id="44a44-285">Hetzelfde als `$_` .</span><span class="sxs-lookup"><span data-stu-id="44a44-285">Same as `$_`.</span></span> <span data-ttu-id="44a44-286">Bevat het huidige object in het pijplijn object.</span><span class="sxs-lookup"><span data-stu-id="44a44-286">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="44a44-287">U kunt deze variabele gebruiken in opdrachten voor het uitvoeren van een actie op elk object of op geselecteerde objecten in een pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="44a44-287">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="psscriptroot"></a><span data-ttu-id="44a44-288">$PSScriptRoot</span><span class="sxs-lookup"><span data-stu-id="44a44-288">$PSScriptRoot</span></span>

<span data-ttu-id="44a44-289">Bevat de map van waaruit een script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-289">Contains the directory from which a script is being run.</span></span>

<span data-ttu-id="44a44-290">In Power Shell 2,0 is deze variabele alleen geldig in script modules ( `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="44a44-290">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
<span data-ttu-id="44a44-291">Vanaf Power Shell 3,0 is het in alle scripts geldig.</span><span class="sxs-lookup"><span data-stu-id="44a44-291">Beginning in PowerShell 3.0, it's valid in all scripts.</span></span>

### <a name="pssenderinfo"></a><span data-ttu-id="44a44-292">$PSSenderInfo</span><span class="sxs-lookup"><span data-stu-id="44a44-292">$PSSenderInfo</span></span>

<span data-ttu-id="44a44-293">Bevat informatie over de gebruiker die de PSSession heeft gestart, met inbegrip van de gebruikers-id en de tijd zone van de oorspronkelijke computer.</span><span class="sxs-lookup"><span data-stu-id="44a44-293">Contains information about the user who started the PSSession, including the user identity and the time zone of the originating computer.</span></span> <span data-ttu-id="44a44-294">Deze variabele is alleen beschikbaar in PSSessions.</span><span class="sxs-lookup"><span data-stu-id="44a44-294">This variable is available only in PSSessions.</span></span>

<span data-ttu-id="44a44-295">De `$PSSenderInfo` variabele bevat een door de gebruiker Configureer bare eigenschap, **ApplicationArguments** , die standaard alleen de `$PSVersionTable` van de oorspronkelijke sessie bevat.</span><span class="sxs-lookup"><span data-stu-id="44a44-295">The `$PSSenderInfo` variable includes a user-configurable property, **ApplicationArguments** , that by default, contains only the `$PSVersionTable` from the originating session.</span></span> <span data-ttu-id="44a44-296">Als u gegevens wilt toevoegen aan de eigenschap **ApplicationArguments** , gebruikt u de para meter **ApplicationArguments** van de `New-PSSessionOption` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="44a44-296">To add data to the **ApplicationArguments** property, use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet.</span></span>

### <a name="psuiculture"></a><span data-ttu-id="44a44-297">$PSUICulture</span><span class="sxs-lookup"><span data-stu-id="44a44-297">$PSUICulture</span></span>

<span data-ttu-id="44a44-298">Bevat de naam van de cultuur van de gebruikers interface die momenteel wordt gebruikt in het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="44a44-298">Contains the name of the user interface (UI) culture that's currently in use in the operating system.</span></span> <span data-ttu-id="44a44-299">De GEBRUIKERSINTERFACE cultuur bepaalt welke teken reeksen worden gebruikt voor elementen van de gebruikers interface, zoals menu's en berichten.</span><span class="sxs-lookup"><span data-stu-id="44a44-299">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span> <span data-ttu-id="44a44-300">Dit is de waarde van de eigenschap **System.Globalization.CultureInfo.CurrentUICulture.name** van het systeem.</span><span class="sxs-lookup"><span data-stu-id="44a44-300">This is the value of the **System.Globalization.CultureInfo.CurrentUICulture.Name** property of the system.</span></span> <span data-ttu-id="44a44-301">Gebruik de cmdlet om het object **System. Globalization. Culture info** voor het systeem op te halen `Get-UICulture` .</span><span class="sxs-lookup"><span data-stu-id="44a44-301">To get the **System.Globalization.CultureInfo** object for the system, use the `Get-UICulture` cmdlet.</span></span>

### <a name="psversiontable"></a><span data-ttu-id="44a44-302">$PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="44a44-302">$PSVersionTable</span></span>

<span data-ttu-id="44a44-303">Bevat een alleen-lezen hash-tabel waarin details worden weer gegeven over de versie van Power shell die in de huidige sessie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-303">Contains a read-only hash table that displays details about the version of PowerShell that is running in the current session.</span></span> <span data-ttu-id="44a44-304">De tabel bevat de volgende items:</span><span class="sxs-lookup"><span data-stu-id="44a44-304">The table includes the following items:</span></span>

| <span data-ttu-id="44a44-305">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="44a44-305">Property</span></span>                  | <span data-ttu-id="44a44-306">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="44a44-306">Description</span></span>                                   |
| ------------------------- | --------------------------------------------- |
| <span data-ttu-id="44a44-307">**PSVersion**</span><span class="sxs-lookup"><span data-stu-id="44a44-307">**PSVersion**</span></span>             | <span data-ttu-id="44a44-308">Het Power shell-versie nummer</span><span class="sxs-lookup"><span data-stu-id="44a44-308">The PowerShell version number</span></span>                 |
| <span data-ttu-id="44a44-309">**PSEdition**</span><span class="sxs-lookup"><span data-stu-id="44a44-309">**PSEdition**</span></span>             | <span data-ttu-id="44a44-310">Deze eigenschap heeft de waarde ' Desktop ' voor</span><span class="sxs-lookup"><span data-stu-id="44a44-310">This property has the value of 'Desktop' for</span></span>  |
|                           | <span data-ttu-id="44a44-311">Power Shell 4 en lager, evenals Power shell</span><span class="sxs-lookup"><span data-stu-id="44a44-311">PowerShell 4 and below as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="44a44-312">5,1 op volledig uitgeruste Windows-edities.</span><span class="sxs-lookup"><span data-stu-id="44a44-312">5.1 on full-featured Windows editions.</span></span>        |
|                           | <span data-ttu-id="44a44-313">Deze eigenschap heeft de waarde ' core ' voor</span><span class="sxs-lookup"><span data-stu-id="44a44-313">This property has the value of 'Core' for</span></span>     |
|                           | <span data-ttu-id="44a44-314">Power shell 6 en hoger, evenals Power shell</span><span class="sxs-lookup"><span data-stu-id="44a44-314">PowerShell 6 and above as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="44a44-315">Power shell 5,1 voor edities met verminderde footprint</span><span class="sxs-lookup"><span data-stu-id="44a44-315">PowerShell 5.1 on reduced-footprint editions</span></span>  |
|                           | <span data-ttu-id="44a44-316">net als Windows nano server of Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="44a44-316">like Windows Nano Server or Windows IoT.</span></span>      |
| <span data-ttu-id="44a44-317">**GitCommitId**</span><span class="sxs-lookup"><span data-stu-id="44a44-317">**GitCommitId**</span></span>           | <span data-ttu-id="44a44-318">De door Voer-id van de bron bestanden, in GitHub,</span><span class="sxs-lookup"><span data-stu-id="44a44-318">The commit Id of the source files, in GitHub,</span></span> |
| <span data-ttu-id="44a44-319">**Besturingssysteem**</span><span class="sxs-lookup"><span data-stu-id="44a44-319">**OS**</span></span>                    | <span data-ttu-id="44a44-320">Beschrijving van het besturings systeem dat</span><span class="sxs-lookup"><span data-stu-id="44a44-320">Description of the operating system that</span></span>      |
|                           | <span data-ttu-id="44a44-321">Power shell wordt uitgevoerd op.</span><span class="sxs-lookup"><span data-stu-id="44a44-321">PowerShell is running on.</span></span>                     |
| <span data-ttu-id="44a44-322">**Platform**</span><span class="sxs-lookup"><span data-stu-id="44a44-322">**Platform**</span></span>              | <span data-ttu-id="44a44-323">Platform waarop het besturings systeem wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="44a44-323">Platform that the operating system is running</span></span> |
|                           | <span data-ttu-id="44a44-324">waarop.</span><span class="sxs-lookup"><span data-stu-id="44a44-324">on.</span></span> <span data-ttu-id="44a44-325">De waarde op Linux en macOS is **UNIX**.</span><span class="sxs-lookup"><span data-stu-id="44a44-325">The value on Linux and macOS is **Unix**.</span></span> |
|                           | <span data-ttu-id="44a44-326">Zie `$IsMacOs` en `$IsLinux` .</span><span class="sxs-lookup"><span data-stu-id="44a44-326">See `$IsMacOs` and `$IsLinux`.</span></span>                |
| <span data-ttu-id="44a44-327">**PSCompatibleVersions**</span><span class="sxs-lookup"><span data-stu-id="44a44-327">**PSCompatibleVersions**</span></span>  | <span data-ttu-id="44a44-328">Versies van Power shell die compatibel zijn</span><span class="sxs-lookup"><span data-stu-id="44a44-328">Versions of PowerShell that are compatible</span></span>    |
|                           | <span data-ttu-id="44a44-329">met de huidige versie</span><span class="sxs-lookup"><span data-stu-id="44a44-329">with the current version</span></span>                      |
| <span data-ttu-id="44a44-330">**PSRemotingProtocolVersion**</span><span class="sxs-lookup"><span data-stu-id="44a44-330">**PSRemotingProtocolVersion**</span></span> | <span data-ttu-id="44a44-331">De versie van de Power shell Remote</span><span class="sxs-lookup"><span data-stu-id="44a44-331">The version of the PowerShell remote</span></span>      |
|                           | <span data-ttu-id="44a44-332">beheer protocol.</span><span class="sxs-lookup"><span data-stu-id="44a44-332">management protocol.</span></span>                          |
| <span data-ttu-id="44a44-333">**SerializationVersion**</span><span class="sxs-lookup"><span data-stu-id="44a44-333">**SerializationVersion**</span></span>  | <span data-ttu-id="44a44-334">De versie van de serialisatie-methode</span><span class="sxs-lookup"><span data-stu-id="44a44-334">The version of the serialization method</span></span>       |
| <span data-ttu-id="44a44-335">**WSManStackVersion**</span><span class="sxs-lookup"><span data-stu-id="44a44-335">**WSManStackVersion**</span></span>     | <span data-ttu-id="44a44-336">Het versie nummer van de WS-Management stack</span><span class="sxs-lookup"><span data-stu-id="44a44-336">The version number of the WS-Management stack</span></span> |

### <a name="pwd"></a><span data-ttu-id="44a44-337">$PWD</span><span class="sxs-lookup"><span data-stu-id="44a44-337">$PWD</span></span>

<span data-ttu-id="44a44-338">Bevat een Path-object dat staat voor het volledige pad van de huidige map.</span><span class="sxs-lookup"><span data-stu-id="44a44-338">Contains a path object that represents the full path of the current directory.</span></span>

### <a name="sender"></a><span data-ttu-id="44a44-339">$Sender</span><span class="sxs-lookup"><span data-stu-id="44a44-339">$Sender</span></span>

<span data-ttu-id="44a44-340">Bevat het object dat deze gebeurtenis heeft gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-340">Contains the object that generated this event.</span></span> <span data-ttu-id="44a44-341">Deze variabele wordt alleen ingevuld binnen het actie blok van een gebeurtenis registratie opdracht.</span><span class="sxs-lookup"><span data-stu-id="44a44-341">This variable is populated only within the Action block of an event registration command.</span></span> <span data-ttu-id="44a44-342">De waarde van deze variabele kan ook worden gevonden in de eigenschap Sender van het **PSEventArgs** -object dat `Get-Event` retourneert.</span><span class="sxs-lookup"><span data-stu-id="44a44-342">The value of this variable can also be found in the Sender property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="shellid"></a><span data-ttu-id="44a44-343">$ShellId</span><span class="sxs-lookup"><span data-stu-id="44a44-343">$ShellId</span></span>

<span data-ttu-id="44a44-344">Bevat de id van de huidige shell.</span><span class="sxs-lookup"><span data-stu-id="44a44-344">Contains the identifier of the current shell.</span></span>

### <a name="stacktrace"></a><span data-ttu-id="44a44-345">$StackTrace</span><span class="sxs-lookup"><span data-stu-id="44a44-345">$StackTrace</span></span>

<span data-ttu-id="44a44-346">Bevat een stack tracering voor de meest recente fout.</span><span class="sxs-lookup"><span data-stu-id="44a44-346">Contains a stack trace for the most recent error.</span></span>

### <a name="switch"></a><span data-ttu-id="44a44-347">$switch</span><span class="sxs-lookup"><span data-stu-id="44a44-347">$switch</span></span>

<span data-ttu-id="44a44-348">Bevat de enumerator niet de resulterende waarden van een `Switch` instructie.</span><span class="sxs-lookup"><span data-stu-id="44a44-348">Contains the enumerator not the resulting values of a `Switch` statement.</span></span> <span data-ttu-id="44a44-349">De `$switch` variabele bestaat alleen als de `Switch` instructie wordt uitgevoerd en wordt verwijderd wanneer de instructie wordt uitgevoerd `switch` .</span><span class="sxs-lookup"><span data-stu-id="44a44-349">The `$switch` variable exists only while the `Switch` statement is running; it's deleted when the `switch` statement completes execution.</span></span> <span data-ttu-id="44a44-350">Zie [about_Switch](about_Switch.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="44a44-350">For more information, see [about_Switch](about_Switch.md).</span></span>

<span data-ttu-id="44a44-351">Opsommingen bevatten eigenschappen en methoden die u kunt gebruiken om loop waarden op te halen en de huidige loop-iteratie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="44a44-351">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="44a44-352">Zie [using enumeraties](#using-enumerators)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="44a44-352">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="this"></a><span data-ttu-id="44a44-353">$this</span><span class="sxs-lookup"><span data-stu-id="44a44-353">$this</span></span>

<span data-ttu-id="44a44-354">In een script blok dat een script eigenschap of script methode definieert, `$this` verwijst de variabele naar het object dat wordt uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="44a44-354">In a script block that defines a script property or script method, the `$this` variable refers to the object that is being extended.</span></span>

<span data-ttu-id="44a44-355">In een aangepaste klasse verwijst de `$this` variabele naar het klassen object zelf, waardoor toegang wordt toegestaan tot eigenschappen en methoden die zijn gedefinieerd in de klasse.</span><span class="sxs-lookup"><span data-stu-id="44a44-355">In a custom class, the `$this` variable refers to the class object itself allowing access to properties and methods defined in the class.</span></span>

### <a name="true"></a><span data-ttu-id="44a44-356">$true</span><span class="sxs-lookup"><span data-stu-id="44a44-356">$true</span></span>

<span data-ttu-id="44a44-357">Bevat **waar**.</span><span class="sxs-lookup"><span data-stu-id="44a44-357">Contains **True**.</span></span> <span data-ttu-id="44a44-358">U kunt deze variabele gebruiken om **waar** in opdrachten en scripts weer te geven.</span><span class="sxs-lookup"><span data-stu-id="44a44-358">You can use this variable to represent **True** in commands and scripts.</span></span>

## <a name="using-enumerators"></a><span data-ttu-id="44a44-359">Opsommingen gebruiken</span><span class="sxs-lookup"><span data-stu-id="44a44-359">Using Enumerators</span></span>

<span data-ttu-id="44a44-360">De `$input` `$foreach` variabelen, en `$switch` zijn alle inventarisaties die worden gebruikt om de waarden te herhalen die worden verwerkt door hun insluitende code blok.</span><span class="sxs-lookup"><span data-stu-id="44a44-360">The `$input`, `$foreach`, and `$switch` variables are all enumerators used to iterate through the values processed by their containing code block.</span></span>

<span data-ttu-id="44a44-361">Een enumerator bevat eigenschappen en methoden die u kunt gebruiken om herhaling te herstellen of opnieuw in te stellen, of om iteratie waarden op te halen.</span><span class="sxs-lookup"><span data-stu-id="44a44-361">An enumerator contains properties and methods you can use to advance or reset iteration, or retrieve iteration values.</span></span> <span data-ttu-id="44a44-362">Het rechtstreeks bewerken van opsommings wordt niet beschouwd als best practice.</span><span class="sxs-lookup"><span data-stu-id="44a44-362">Directly manipulating enumerators isn't considered best practice.</span></span>

- <span data-ttu-id="44a44-363">Binnen lussen moeten [de tref woorden](about_Break.md) voor stroom beheer en [door gaan](about_Continue.md) worden voor keur.</span><span class="sxs-lookup"><span data-stu-id="44a44-363">Within loops, flow control keywords [break](about_Break.md) and [continue](about_Continue.md) should be preferred.</span></span>
- <span data-ttu-id="44a44-364">Binnen functies die pijplijn invoer accepteren, is het best practice om para meters met de kenmerken **ValueFromPipeline** of **ValueFromPipelineByPropertyName** te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="44a44-364">Within functions that accept pipeline input, it's best practice to use Parameters with the **ValueFromPipeline** or **ValueFromPipelineByPropertyName** attributes.</span></span>

  <span data-ttu-id="44a44-365">Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="44a44-365">For more information, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="movenext"></a><span data-ttu-id="44a44-366">Aangeroepen</span><span class="sxs-lookup"><span data-stu-id="44a44-366">MoveNext</span></span>

<span data-ttu-id="44a44-367">De methode [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) gaat de enumerator door naar het volgende element van de verzameling.</span><span class="sxs-lookup"><span data-stu-id="44a44-367">The [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) method advances the enumerator to the next element of the collection.</span></span> <span data-ttu-id="44a44-368">**MoveNext** retourneert **True** als de enumerator is uitgebreid, **False** als de enumerator het einde van de verzameling heeft door gegeven.</span><span class="sxs-lookup"><span data-stu-id="44a44-368">**MoveNext** returns **True** if the enumerator was successfully advanced, **False** if the enumerator has passed the end of the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="44a44-369">De **Booleaanse** waarde die mijn **MoveNext** retourneert, wordt verzonden naar de uitvoer stroom.</span><span class="sxs-lookup"><span data-stu-id="44a44-369">The **Boolean** value returned my **MoveNext** is sent to the output stream.</span></span>
> <span data-ttu-id="44a44-370">U kunt de uitvoer onderdrukken door deze te typecasting `[void]` of deze uit te sluizen naar [out-null](xref:Microsoft.PowerShell.Core.Out-Null).</span><span class="sxs-lookup"><span data-stu-id="44a44-370">You can suppress the output by typecasting it to `[void]` or piping it to [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null).</span></span>
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a><span data-ttu-id="44a44-371">Opnieuw instellen</span><span class="sxs-lookup"><span data-stu-id="44a44-371">Reset</span></span>

<span data-ttu-id="44a44-372">Met de methode [Reset](/dotnet/api/system.collections.ienumerator.reset) wordt de enumerator ingesteld op de oorspronkelijke positie, die **vóór** het eerste element in de verzameling ligt.</span><span class="sxs-lookup"><span data-stu-id="44a44-372">The [Reset](/dotnet/api/system.collections.ienumerator.reset) method sets the enumerator to its initial position, which is **before** the first element in the collection.</span></span>

### <a name="current"></a><span data-ttu-id="44a44-373">Huidig</span><span class="sxs-lookup"><span data-stu-id="44a44-373">Current</span></span>

<span data-ttu-id="44a44-374">Met de [huidige](/dotnet/api/system.collections.ienumerator.current) eigenschap wordt het element in de verzameling, of de pijp lijn, op de huidige positie van de enumerator opgehaald.</span><span class="sxs-lookup"><span data-stu-id="44a44-374">The [Current](/dotnet/api/system.collections.ienumerator.current) property gets the element in the collection, or pipeline, at the current position of the enumerator.</span></span>

<span data-ttu-id="44a44-375">De **huidige** eigenschap blijft dezelfde eigenschap retour neren totdat **MoveNext** is aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="44a44-375">The **Current** property continues to return the same property until **MoveNext** is called.</span></span>

## <a name="examples"></a><span data-ttu-id="44a44-376">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="44a44-376">Examples</span></span>

### <a name="example-1-using-the-input-variable"></a><span data-ttu-id="44a44-377">Voor beeld 1: de variabele $input gebruiken</span><span class="sxs-lookup"><span data-stu-id="44a44-377">Example 1: Using the $input variable</span></span>

<span data-ttu-id="44a44-378">In het volgende voor beeld wordt met de `$input` variabele de variabele gewist tot de volgende keer dat het proces blok wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-378">In the following example, accessing the `$input` variable clears the variable until the next time the process block executes.</span></span> <span data-ttu-id="44a44-379">Als u de methode **Reset** gebruikt, wordt de variabele opnieuw ingesteld `$input` op de huidige pijplijn waarde.</span><span class="sxs-lookup"><span data-stu-id="44a44-379">Using the **Reset** method resets the `$input` variable to the current pipeline value.</span></span>

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

<span data-ttu-id="44a44-380">De variabele wordt door het proces blok automatisch `$input` door berekend, zelfs als u geen toegang hebt.</span><span class="sxs-lookup"><span data-stu-id="44a44-380">The process block automatically advances the `$input` variable even if you don't access it.</span></span>

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a><span data-ttu-id="44a44-381">Voor beeld 2: $input buiten het proces blok gebruiken</span><span class="sxs-lookup"><span data-stu-id="44a44-381">Example 2: Using $input outside the process block</span></span>

<span data-ttu-id="44a44-382">Buiten het proces blok bevindt de `$input` variabele alle waarden die in de functie zijn ondergebracht.</span><span class="sxs-lookup"><span data-stu-id="44a44-382">Outside of the process block the `$input` variable represents all the values piped into the function.</span></span>

- <span data-ttu-id="44a44-383">Als u de variabele opent, worden `$input` alle waarden gewist.</span><span class="sxs-lookup"><span data-stu-id="44a44-383">Accessing the `$input` variable clears all values.</span></span>
- <span data-ttu-id="44a44-384">De methode **Reset** herstelt de volledige verzameling.</span><span class="sxs-lookup"><span data-stu-id="44a44-384">The **Reset** method resets the entire collection.</span></span>
- <span data-ttu-id="44a44-385">De **huidige** eigenschap wordt nooit ingevuld.</span><span class="sxs-lookup"><span data-stu-id="44a44-385">The **Current** property is never populated.</span></span>
- <span data-ttu-id="44a44-386">De methode **MoveNext** retourneert False omdat de verzameling niet kan worden uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="44a44-386">The **MoveNext** method returns false because the collection can't be advanced.</span></span>
  - <span data-ttu-id="44a44-387">Door **MoveNext** aan te roepen, wordt de `$input` variabele gewist.</span><span class="sxs-lookup"><span data-stu-id="44a44-387">Calling **MoveNext** clears out the `$input` variable.</span></span>

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a><span data-ttu-id="44a44-388">Voor beeld 3: het $input gebruiken. Huidige eigenschap</span><span class="sxs-lookup"><span data-stu-id="44a44-388">Example 3: Using the $input.Current property</span></span>

<span data-ttu-id="44a44-389">Met de **huidige** eigenschap kan de huidige pijplijn waarde meerdere keren worden gebruikt zonder gebruik te maken van de methode **Reset** .</span><span class="sxs-lookup"><span data-stu-id="44a44-389">By using the **Current** property, the current pipeline value can be accessed multiple times without using the **Reset** method.</span></span> <span data-ttu-id="44a44-390">De methode **MoveNext** wordt niet automatisch aangeroepen door het proces blok.</span><span class="sxs-lookup"><span data-stu-id="44a44-390">The process block doesn't automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="44a44-391">De **huidige** eigenschap wordt nooit gevuld tenzij u **MoveNext** expliciet aanroept.</span><span class="sxs-lookup"><span data-stu-id="44a44-391">The **Current** property will never be populated unless you explicitly call **MoveNext**.</span></span> <span data-ttu-id="44a44-392">De **huidige** eigenschap kan meermaals worden gebruikt binnen het proces blok zonder dat de waarde ervan wordt gewist.</span><span class="sxs-lookup"><span data-stu-id="44a44-392">The **Current** property can be accessed multiple times inside the process block without clearing its value.</span></span>

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a><span data-ttu-id="44a44-393">Voor beeld 4: de variabele $foreach gebruiken</span><span class="sxs-lookup"><span data-stu-id="44a44-393">Example 4: Using the $foreach variable</span></span>

<span data-ttu-id="44a44-394">In tegens telling tot de `$input` variabele `$foreach` vertegenwoordigt de variabele altijd alle items in de verzameling wanneer deze rechtstreeks worden geopend.</span><span class="sxs-lookup"><span data-stu-id="44a44-394">Unlike the `$input` variable, the `$foreach` variable always represents all items in the collection when accessed directly.</span></span> <span data-ttu-id="44a44-395">Gebruik de eigenschap **Current** om toegang te krijgen tot het huidige verzamelings element en de methoden **Reset** en **MoveNext** om de waarde ervan te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="44a44-395">Use the **Current** property to access the current collection element, and the **Reset** and **MoveNext** methods to change its value.</span></span>

> [!NOTE]
> <span data-ttu-id="44a44-396">Bij elke herhaling van de `foreach` lus wordt de methode **MoveNext** automatisch aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="44a44-396">Each iteration of the `foreach` loop will automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="44a44-397">De volgende lus wordt alleen twee keer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-397">The following loop only executes twice.</span></span> <span data-ttu-id="44a44-398">In de tweede iteratie wordt de verzameling verplaatst naar het derde element voordat de herhaling is voltooid.</span><span class="sxs-lookup"><span data-stu-id="44a44-398">In the second iteration, the collection is moved to the third element before the iteration is complete.</span></span> <span data-ttu-id="44a44-399">Na de tweede iteratie zijn er nu geen waarden meer om te herhalen en wordt de lus afgebroken.</span><span class="sxs-lookup"><span data-stu-id="44a44-399">After the second iteration, there are now no more values to iterate, and the loop terminates.</span></span>

<span data-ttu-id="44a44-400">De eigenschap **MoveNext** heeft geen invloed op de variabele die is gekozen om de verzameling () door te lopen `$Num` .</span><span class="sxs-lookup"><span data-stu-id="44a44-400">The **MoveNext** property doesn't affect the variable chosen to iterate through the collection (`$Num`).</span></span>

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

<span data-ttu-id="44a44-401">Als u de methode **Reset** gebruikt, wordt het huidige element in de verzameling opnieuw ingesteld.</span><span class="sxs-lookup"><span data-stu-id="44a44-401">Using the **Reset** method resets the current element in the collection.</span></span> <span data-ttu-id="44a44-402">In het volgende voor beeld worden de eerste twee elementen **twee keer** door lopen, omdat de methode **Reset** is aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="44a44-402">The following example loops through the first two elements **twice** because the **Reset** method is called.</span></span> <span data-ttu-id="44a44-403">Na de eerste twee lussen `if` mislukt de instructie en doorloopt de lus alle drie de elementen normaal.</span><span class="sxs-lookup"><span data-stu-id="44a44-403">After the first two loops, the `if` statement fails and the loop iterates through all three elements normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44a44-404">Dit kan leiden tot een oneindige lus.</span><span class="sxs-lookup"><span data-stu-id="44a44-404">This could result in an infinite loop.</span></span>

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a><span data-ttu-id="44a44-405">Voor beeld 5: de variabele $switch gebruiken</span><span class="sxs-lookup"><span data-stu-id="44a44-405">Example 5: Using the $switch variable</span></span>

<span data-ttu-id="44a44-406">De `$switch` variabele heeft precies dezelfde regels als de `$foreach` variabele.</span><span class="sxs-lookup"><span data-stu-id="44a44-406">The `$switch` variable has the exact same rules as the `$foreach` variable.</span></span>
<span data-ttu-id="44a44-407">In het volgende voor beeld worden alle enumerator-concepten gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="44a44-407">The following example demonstrates all the enumerator concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="44a44-408">U ziet dat de **NotEvaluated** -Case nooit wordt uitgevoerd, ook al is er geen `break` instructie na de methode **MoveNext** .</span><span class="sxs-lookup"><span data-stu-id="44a44-408">Note how the **NotEvaluated** case is never executed, even though there's no `break` statement after the **MoveNext** method.</span></span>

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a><span data-ttu-id="44a44-409">Zie ook</span><span class="sxs-lookup"><span data-stu-id="44a44-409">See also</span></span>

[<span data-ttu-id="44a44-410">about_Functions</span><span class="sxs-lookup"><span data-stu-id="44a44-410">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="44a44-411">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="44a44-411">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="44a44-412">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="44a44-412">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="44a44-413">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="44a44-413">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="44a44-414">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="44a44-414">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="44a44-415">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="44a44-415">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="44a44-416">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="44a44-416">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="44a44-417">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="44a44-417">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="44a44-418">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="44a44-418">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="44a44-419">about_Variables</span><span class="sxs-lookup"><span data-stu-id="44a44-419">about_Variables</span></span>](about_Variables.md)