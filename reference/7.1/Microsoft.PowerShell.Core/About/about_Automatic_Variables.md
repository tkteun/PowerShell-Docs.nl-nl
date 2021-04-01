---
description: Beschrijft variabelen waarin status informatie voor Power shell wordt opgeslagen. Deze variabelen worden gemaakt en onderhouden door Power shell.
Locale: en-US
ms.date: 03/29/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: a439ba5e678c68dcd25b79ea898ed7a157c851b5
ms.sourcegitcommit: bdd0fedaf9ba534645b2f7eb1fe1241481f58715
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/30/2021
ms.locfileid: "105936652"
---
# <a name="about-automatic-variables"></a><span data-ttu-id="7f7f6-104">Over automatische variabelen</span><span class="sxs-lookup"><span data-stu-id="7f7f6-104">About Automatic Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="7f7f6-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="7f7f6-105">Short description</span></span>

<span data-ttu-id="7f7f6-106">Beschrijft variabelen waarin status informatie voor Power shell wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-106">Describes variables that store state information for PowerShell.</span></span> <span data-ttu-id="7f7f6-107">Deze variabelen worden gemaakt en onderhouden door Power shell.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-107">These variables are created and maintained by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="7f7f6-108">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="7f7f6-108">Long description</span></span>

<span data-ttu-id="7f7f6-109">Deze variabelen worden conceptueel gezien als alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-109">Conceptually, these variables are considered to be read-only.</span></span> <span data-ttu-id="7f7f6-110">Hoewel ze **kunnen** worden geschreven naar, voor achterwaartse compatibiliteit, **moeten** ze daar niet naar worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-110">Even though they **can** be written to, for backward compatibility they **should not** be written to.</span></span>

<span data-ttu-id="7f7f6-111">Hier volgt een lijst met de automatische variabelen in Power shell:</span><span class="sxs-lookup"><span data-stu-id="7f7f6-111">Here is a list of the automatic variables in PowerShell:</span></span>

### <a name=""></a>$$

<span data-ttu-id="7f7f6-112">Bevat het laatste token in de laatste door de sessie ontvangen regel.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-112">Contains the last token in the last line received by the session.</span></span>

### <a name=""></a><span data-ttu-id="7f7f6-113">$?</span><span class="sxs-lookup"><span data-stu-id="7f7f6-113">$?</span></span>

<span data-ttu-id="7f7f6-114">Bevat de uitvoerings status van de laatste opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-114">Contains the execution status of the last command.</span></span> <span data-ttu-id="7f7f6-115">Het bevat **waar** als de laatste opdracht is geslaagd en **Onwaar** als deze is mislukt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-115">It contains **True** if the last command succeeded and **False** if it failed.</span></span>

<span data-ttu-id="7f7f6-116">Voor cmdlets en geavanceerde functies die in meerdere fasen in een pijp lijn worden uitgevoerd, bijvoorbeeld in zowel `process` -als `end` -blokken, `this.WriteError()` wordt het aanroepen van of `$PSCmdlet.WriteError()` respectievelijk op elk punt ingesteld `$?` op **False**, zoals `this.ThrowTerminatingError()` en `$PSCmdlet.ThrowTerminatingError()` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-116">For cmdlets and advanced functions that are run at multiple stages in a pipeline, for example in both `process` and `end` blocks, calling `this.WriteError()` or `$PSCmdlet.WriteError()` respectively at any point will set `$?` to **False**, as will `this.ThrowTerminatingError()` and `$PSCmdlet.ThrowTerminatingError()`.</span></span>

<span data-ttu-id="7f7f6-117">De `Write-Error` cmdlet wordt altijd ingesteld `$?` op **False** direct nadat deze is uitgevoerd, maar is niet ingesteld `$?` op **False** voor een functie die deze aanroept:</span><span class="sxs-lookup"><span data-stu-id="7f7f6-117">The `Write-Error` cmdlet always sets `$?` to **False** immediately after it is executed, but will not set `$?` to **False** for a function calling it:</span></span>

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

<span data-ttu-id="7f7f6-118">Voor dit laatste doel `$PSCmdlet.WriteError()` moet in plaats daarvan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-118">For the latter purpose, `$PSCmdlet.WriteError()` should be used instead.</span></span>

<span data-ttu-id="7f7f6-119">Voor systeem eigen opdrachten (uitvoer bare bestanden) `$?` is ingesteld op **True** wanneer `$LASTEXITCODE` 0 is en is ingesteld op **False** wanneer `$LASTEXITCODE` een andere waarde is.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-119">For native commands (executables), `$?` is set to **True** when `$LASTEXITCODE` is 0, and set to **False** when `$LASTEXITCODE` is any other value.</span></span>

> [!NOTE]
> <span data-ttu-id="7f7f6-120">Tot Power shell 7, met een instructie tussen haakjes, wordt de syntaxis van de `(...)` subexpressie `$(...)` of matrix expressie `@(...)` altijd opnieuw ingesteld `$?` op **True**, zodat deze `(Write-Error)` wordt weer gegeven `$?` als **waar**.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-120">Until PowerShell 7, containing a statement within parentheses `(...)`, subexpression syntax `$(...)` or array expression `@(...)` always reset `$?` to **True**, so that `(Write-Error)` shows `$?` as **True**.</span></span>
> <span data-ttu-id="7f7f6-121">Dit is gewijzigd in Power shell 7, zodat `$?` altijd het werkelijke succes van de laatste opdracht wordt uitgevoerd in deze expressies.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-121">This has been changed in PowerShell 7, so that `$?` will always reflect the actual success of the last command run in these expressions.</span></span>

### <a name=""></a>$^

<span data-ttu-id="7f7f6-122">Bevat het eerste token in de laatste regel die door de sessie is ontvangen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-122">Contains the first token in the last line received by the session.</span></span>

### <a name="_"></a><span data-ttu-id="7f7f6-123">$_</span><span class="sxs-lookup"><span data-stu-id="7f7f6-123">$_</span></span>

<span data-ttu-id="7f7f6-124">Hetzelfde als `$PSItem` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-124">Same as `$PSItem`.</span></span> <span data-ttu-id="7f7f6-125">Bevat het huidige object in het pijplijn object.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-125">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="7f7f6-126">U kunt deze variabele gebruiken in opdrachten voor het uitvoeren van een actie op elk object of op geselecteerde objecten in een pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-126">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="args"></a><span data-ttu-id="7f7f6-127">$args</span><span class="sxs-lookup"><span data-stu-id="7f7f6-127">$args</span></span>

<span data-ttu-id="7f7f6-128">Bevat een matrix met waarden voor niet-gedeclareerde para meters die worden door gegeven aan een functie, script of script blok.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-128">Contains an array of values for undeclared parameters that are passed to a function, script, or script block.</span></span> <span data-ttu-id="7f7f6-129">Wanneer u een functie maakt, kunt u de para meters declareren met behulp van het `param` sleutel woord of door een door komma's gescheiden lijst met para meters toe te voegen tussen haakjes achter de functie naam.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-129">When you create a function, you can declare the parameters by using the `param` keyword or by adding a comma-separated list of parameters in parentheses after the function name.</span></span>

<span data-ttu-id="7f7f6-130">In een gebeurtenis actie bevat de `$args` variabele objecten die de gebeurtenis argumenten vertegenwoordigen van de gebeurtenis die wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-130">In an event action, the `$args` variable contains objects that represent the event arguments of the event that is being processed.</span></span> <span data-ttu-id="7f7f6-131">Deze variabele wordt alleen ingevuld in de `Action` blok kering van een gebeurtenis registratie opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-131">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="7f7f6-132">De waarde van deze variabele kan ook worden gevonden in de eigenschap **SourceArgs** van het **PSEventArgs** -object dat `Get-Event` retourneert.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-132">The value of this variable can also be found in the **SourceArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="consolefilename"></a><span data-ttu-id="7f7f6-133">$ConsoleFileName</span><span class="sxs-lookup"><span data-stu-id="7f7f6-133">$ConsoleFileName</span></span>

<span data-ttu-id="7f7f6-134">Bevat het pad naar het console bestand ( `.psc1` ) dat het meest recent is gebruikt in de sessie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-134">Contains the path of the console file (`.psc1`) that was most recently used in the session.</span></span> <span data-ttu-id="7f7f6-135">Deze variabele wordt ingevuld wanneer u Power shell start met de para meter **PSConsoleFile** of wanneer u de `Export-Console` cmdlet gebruikt om module namen te exporteren naar een-console bestand.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-135">This variable is populated when you start PowerShell with the **PSConsoleFile** parameter or when you use the `Export-Console` cmdlet to export snap-in names to a console file.</span></span>

<span data-ttu-id="7f7f6-136">Wanneer u de `Export-Console` cmdlet zonder para meters gebruikt, wordt automatisch het console bestand bijgewerkt dat het meest recent is gebruikt in de sessie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-136">When you use the `Export-Console` cmdlet without parameters, it automatically updates the console file that was most recently used in the session.</span></span> <span data-ttu-id="7f7f6-137">U kunt deze automatische variabele gebruiken om te bepalen welk bestand moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-137">You can use this automatic variable to determine which file will be updated.</span></span>

### <a name="error"></a><span data-ttu-id="7f7f6-138">$Error</span><span class="sxs-lookup"><span data-stu-id="7f7f6-138">$Error</span></span>

<span data-ttu-id="7f7f6-139">Bevat een matrix met fout objecten die de meest recente fouten vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-139">Contains an array of error objects that represent the most recent errors.</span></span>
<span data-ttu-id="7f7f6-140">De meest recente fout is het eerste fout object in de matrix `$Error[0]` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-140">The most recent error is the first error object in the array `$Error[0]`.</span></span>

<span data-ttu-id="7f7f6-141">`$Error`Gebruik de para meter **Error Action** common met de waarde **Ignore** om te voor komen dat er een fout wordt toegevoegd aan de matrix.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-141">To prevent an error from being added to the `$Error` array, use the **ErrorAction** common parameter with a value of **Ignore**.</span></span> <span data-ttu-id="7f7f6-142">Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-142">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="event"></a><span data-ttu-id="7f7f6-143">$Event</span><span class="sxs-lookup"><span data-stu-id="7f7f6-143">$Event</span></span>

<span data-ttu-id="7f7f6-144">Bevat een **PSEventArgs** -object dat de gebeurtenis vertegenwoordigt die wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-144">Contains a **PSEventArgs** object that represents the event that is being processed.</span></span> <span data-ttu-id="7f7f6-145">Deze variabele wordt alleen ingevuld binnen het `Action` blok van een gebeurtenis registratie opdracht, zoals `Register-ObjectEvent` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-145">This variable is populated only within the `Action` block of an event registration command, such as `Register-ObjectEvent`.</span></span> <span data-ttu-id="7f7f6-146">De waarde van deze variabele is hetzelfde object dat door de `Get-Event` cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-146">The value of this variable is the same object that the `Get-Event` cmdlet returns.</span></span> <span data-ttu-id="7f7f6-147">Daarom kunt u de eigenschappen van de variabele gebruiken `Event` , zoals `$Event.TimeGenerated` in een- `Action` script blok.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-147">Therefore, you can use the properties of the `Event` variable, such as `$Event.TimeGenerated`, in an `Action` script block.</span></span>

### <a name="eventargs"></a><span data-ttu-id="7f7f6-148">$EventArgs</span><span class="sxs-lookup"><span data-stu-id="7f7f6-148">$EventArgs</span></span>

<span data-ttu-id="7f7f6-149">Bevat een object dat het eerste gebeurtenis argument vertegenwoordigt dat is afgeleid van **EventArgs** van de gebeurtenis die wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-149">Contains an object that represents the first event argument that derives from **EventArgs** of the event that is being processed.</span></span> <span data-ttu-id="7f7f6-150">Deze variabele wordt alleen ingevuld in de `Action` blok kering van een gebeurtenis registratie opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-150">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="7f7f6-151">De waarde van deze variabele kan ook worden gevonden in de eigenschap **SourceEventArgs** van het **PSEventArgs** -object dat `Get-Event` retourneert.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-151">The value of this variable can also be found in the **SourceEventArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="eventsubscriber"></a><span data-ttu-id="7f7f6-152">$EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="7f7f6-152">$EventSubscriber</span></span>

<span data-ttu-id="7f7f6-153">Bevat een **PSEventSubscriber** -object dat de gebeurtenis abonnee vertegenwoordigt van de gebeurtenis die wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-153">Contains a **PSEventSubscriber** object that represents the event subscriber of the event that is being processed.</span></span> <span data-ttu-id="7f7f6-154">Deze variabele wordt alleen ingevuld in de `Action` blok kering van een gebeurtenis registratie opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-154">This variable is populated only within the `Action` block of an event registration command.</span></span> <span data-ttu-id="7f7f6-155">De waarde van deze variabele is hetzelfde object dat door de `Get-EventSubscriber` cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-155">The value of this variable is the same object that the `Get-EventSubscriber` cmdlet returns.</span></span>

### <a name="executioncontext"></a><span data-ttu-id="7f7f6-156">$ExecutionContext</span><span class="sxs-lookup"><span data-stu-id="7f7f6-156">$ExecutionContext</span></span>

<span data-ttu-id="7f7f6-157">Bevat een **EngineIntrinsics** -object dat de uitvoerings context van de Power shell-host vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-157">Contains an **EngineIntrinsics** object that represents the execution context of the PowerShell host.</span></span> <span data-ttu-id="7f7f6-158">U kunt deze variabele gebruiken om de uitvoerings objecten te vinden die beschikbaar zijn voor cmdlets.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-158">You can use this variable to find the execution objects that are available to cmdlets.</span></span>

### <a name="false"></a><span data-ttu-id="7f7f6-159">$false</span><span class="sxs-lookup"><span data-stu-id="7f7f6-159">$false</span></span>

<span data-ttu-id="7f7f6-160">Bevat **Onwaar**.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-160">Contains **False**.</span></span> <span data-ttu-id="7f7f6-161">U kunt deze variabele gebruiken om **Onwaar** in opdrachten en scripts weer te geven in plaats van de teken reeks "false" te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-161">You can use this variable to represent **False** in commands and scripts instead of using the string "false".</span></span> <span data-ttu-id="7f7f6-162">De teken reeks kan worden geïnterpreteerd als **True** als deze is geconverteerd naar een niet-lege teken reeks of een niet-nul-geheel getal.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-162">The string can be interpreted as **True** if it's converted to a non-empty string or to a non-zero integer.</span></span>

### <a name="foreach"></a><span data-ttu-id="7f7f6-163">$foreach</span><span class="sxs-lookup"><span data-stu-id="7f7f6-163">$foreach</span></span>

<span data-ttu-id="7f7f6-164">Bevat de enumerator (niet de resulterende waarden) van een [foreach](about_ForEach.md) -lus.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-164">Contains the enumerator (not the resulting values) of a [ForEach](about_ForEach.md) loop.</span></span> <span data-ttu-id="7f7f6-165">De `$ForEach` variabele bestaat alleen wanneer de `ForEach` lus wordt uitgevoerd; deze wordt verwijderd nadat de lus is voltooid.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-165">The `$ForEach` variable exists only while the `ForEach` loop is running; it's deleted after the loop is completed.</span></span>

<span data-ttu-id="7f7f6-166">Opsommingen bevatten eigenschappen en methoden die u kunt gebruiken om loop waarden op te halen en de huidige loop-iteratie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-166">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="7f7f6-167">Zie [using enumeraties](#using-enumerators)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-167">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="home"></a><span data-ttu-id="7f7f6-168">$HOME</span><span class="sxs-lookup"><span data-stu-id="7f7f6-168">$HOME</span></span>

<span data-ttu-id="7f7f6-169">Bevat het volledige pad naar de basismap van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-169">Contains the full path of the user's home directory.</span></span> <span data-ttu-id="7f7f6-170">Deze variabele is het equivalent van de `"$env:homedrive$env:homepath"` Windows-omgevings variabelen `C:\Users\<UserName>` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-170">This variable is the equivalent of the `"$env:homedrive$env:homepath"` Windows environment variables, typically `C:\Users\<UserName>`.</span></span>

### <a name="host"></a><span data-ttu-id="7f7f6-171">$Host</span><span class="sxs-lookup"><span data-stu-id="7f7f6-171">$Host</span></span>

<span data-ttu-id="7f7f6-172">Bevat een-object dat de huidige hosttoepassing voor Power shell vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-172">Contains an object that represents the current host application for PowerShell.</span></span> <span data-ttu-id="7f7f6-173">U kunt deze variabele gebruiken om de huidige host in opdrachten aan te geven of om de eigenschappen van de host, zoals of of, weer te geven of te wijzigen `$Host.version` `$Host.CurrentCulture` `$host.ui.rawui.setbackgroundcolor("Red")` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-173">You can use this variable to represent the current host in commands or to display or change the properties of the host, such as `$Host.version` or `$Host.CurrentCulture`, or `$host.ui.rawui.setbackgroundcolor("Red")`.</span></span>

### <a name="input"></a><span data-ttu-id="7f7f6-174">$input</span><span class="sxs-lookup"><span data-stu-id="7f7f6-174">$input</span></span>

<span data-ttu-id="7f7f6-175">Bevat een enumerator die alle invoer inventariseert die wordt door gegeven aan een functie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-175">Contains an enumerator that enumerates all input that is passed to a function.</span></span> <span data-ttu-id="7f7f6-176">De `$input` variabele is alleen beschikbaar voor functies en script blokken (die functies zijn die geen naam zijn).</span><span class="sxs-lookup"><span data-stu-id="7f7f6-176">The `$input` variable is available only to functions and script blocks (which are unnamed functions).</span></span>

- <span data-ttu-id="7f7f6-177">In een functie zonder een `Begin` , `Process` , of `End` blok keert de `$input` variabele de verzameling van alle invoer naar de functie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-177">In a function without a `Begin`, `Process`, or `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

- <span data-ttu-id="7f7f6-178">In het `Begin` blok bevat de `$input` variabele geen gegevens.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-178">In the `Begin` block, the `$input` variable contains no data.</span></span>

- <span data-ttu-id="7f7f6-179">In het `Process` blok bevat de `$input` variabele het object dat zich momenteel in de pijp lijn bevindt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-179">In the `Process` block, the `$input` variable contains the object that is currently in the pipeline.</span></span>

- <span data-ttu-id="7f7f6-180">In het `End` blok wordt met de `$input` variabele de verzameling van alle invoer in de functie opgesomd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-180">In the `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

  > [!NOTE]
  > <span data-ttu-id="7f7f6-181">U kunt de variabele niet in `$input` zowel het proces blok als het eind blok in dezelfde functie of hetzelfde script blok gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-181">You cannot use the `$input` variable inside both the Process block and the End block in the same function or script block.</span></span>

<span data-ttu-id="7f7f6-182">Omdat `$input` een enumerator is, heeft toegang tot de eigenschappen van het bestand `$input` niet langer beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-182">Since `$input` is an enumerator, accessing any of it's properties causes `$input` to no longer be available.</span></span> <span data-ttu-id="7f7f6-183">U kunt `$input` in een andere variabele opslaan om de eigenschappen opnieuw te gebruiken `$input` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-183">You can store `$input` in another variable to reuse the `$input` properties.</span></span>

<span data-ttu-id="7f7f6-184">Opsommingen bevatten eigenschappen en methoden die u kunt gebruiken om loop waarden op te halen en de huidige loop-iteratie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-184">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="7f7f6-185">Zie [using enumeraties](#using-enumerators)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-185">For more information, see [Using Enumerators](#using-enumerators).</span></span>

<span data-ttu-id="7f7f6-186">De `$input` variabele is ook beschikbaar voor de opdracht die is opgegeven door de `-Command` para meter van `pwsh` wanneer deze wordt aangeroepen vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-186">The `$input` variable is also available to the command specified by the `-Command` parameter of `pwsh` when invoked from the command line.</span></span> <span data-ttu-id="7f7f6-187">Het volgende voor beeld wordt uitgevoerd vanuit de Windows-opdracht shell.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-187">The following example is run from the Windows Command shell.</span></span>

```CMD
echo Hello | pwsh -Command """$input World!"""
```

### <a name="iscoreclr"></a><span data-ttu-id="7f7f6-188">$IsCoreCLR</span><span class="sxs-lookup"><span data-stu-id="7f7f6-188">$IsCoreCLR</span></span>

<span data-ttu-id="7f7f6-189">Bevat `$True` als de huidige sessie wordt uitgevoerd op .net core runtime (CoreCLR).</span><span class="sxs-lookup"><span data-stu-id="7f7f6-189">Contains `$True` if the current session is running on the .NET Core Runtime (CoreCLR).</span></span> <span data-ttu-id="7f7f6-190">Anders bevat `$False` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-190">Otherwise contains `$False`.</span></span>

### <a name="islinux"></a><span data-ttu-id="7f7f6-191">$IsLinux</span><span class="sxs-lookup"><span data-stu-id="7f7f6-191">$IsLinux</span></span>

<span data-ttu-id="7f7f6-192">Bevat `$True` als de huidige sessie wordt uitgevoerd op een Linux-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-192">Contains `$True` if the current session is running on a Linux operating system.</span></span>
<span data-ttu-id="7f7f6-193">Anders bevat `$False` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-193">Otherwise contains `$False`.</span></span>

### <a name="ismacos"></a><span data-ttu-id="7f7f6-194">$IsMacOS</span><span class="sxs-lookup"><span data-stu-id="7f7f6-194">$IsMacOS</span></span>

<span data-ttu-id="7f7f6-195">Bevat `$True` als de huidige sessie wordt uitgevoerd op een MacOS-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-195">Contains `$True` if the current session is running on a MacOS operating system.</span></span>
<span data-ttu-id="7f7f6-196">Anders bevat `$False` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-196">Otherwise contains `$False`.</span></span>

### <a name="iswindows"></a><span data-ttu-id="7f7f6-197">$IsWindows</span><span class="sxs-lookup"><span data-stu-id="7f7f6-197">$IsWindows</span></span>

<span data-ttu-id="7f7f6-198">Bevat `$TRUE` als de huidige sessie wordt uitgevoerd op een Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-198">Contains `$TRUE` if the current session is running on a Windows operating system.</span></span> <span data-ttu-id="7f7f6-199">Anders bevat `$FALSE` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-199">Otherwise contains `$FALSE`.</span></span>

### <a name="lastexitcode"></a><span data-ttu-id="7f7f6-200">$LastExitCode</span><span class="sxs-lookup"><span data-stu-id="7f7f6-200">$LastExitCode</span></span>

<span data-ttu-id="7f7f6-201">Bevat de afsluit code van het laatste op Windows gebaseerde programma dat is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-201">Contains the exit code of the last Windows-based program that was run.</span></span>

### <a name="matches"></a><span data-ttu-id="7f7f6-202">$Matches</span><span class="sxs-lookup"><span data-stu-id="7f7f6-202">$Matches</span></span>

<span data-ttu-id="7f7f6-203">De `Matches` variabele werkt met de `-match` `-notmatch` Opera tors en.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-203">The `Matches` variable works with the `-match` and `-notmatch` operators.</span></span>
<span data-ttu-id="7f7f6-204">Wanneer u scalaire invoer verzendt naar `-match` de `-notmatch` operator OR en één overeenkomst detecteert, wordt een Booleaanse waarde geretourneerd en wordt de `$Matches` Automatische variabele gevuld met een hash-tabel van de teken reeks waarden die overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-204">When you submit scalar input to the `-match` or `-notmatch` operator, and either one detects a match, they return a Boolean value and populate the `$Matches` automatic variable with a hash table of any string values that were matched.</span></span> <span data-ttu-id="7f7f6-205">De `$Matches` hash-tabel kan ook worden gevuld met opnamen wanneer u reguliere expressies met de operator gebruikt `-match` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-205">The `$Matches` hash table can also be populated with captures when you use regular expressions with the `-match` operator.</span></span>

<span data-ttu-id="7f7f6-206">Zie about_Comparison_Operators voor meer informatie over de `-match` - [](about_comparison_operators.md)operator.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-206">For more information about the `-match` operator, see [about_Comparison_Operators](about_comparison_operators.md).</span></span> <span data-ttu-id="7f7f6-207">Zie [about_Regular_Expressions](about_Regular_Expressions.md)voor meer informatie over reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-207">For more information on regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

<span data-ttu-id="7f7f6-208">De `$Matches` variabele werkt ook in een `switch` instructie met de `-Regex` para meter.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-208">The `$Matches` variable also works in a `switch` statement with the `-Regex` parameter.</span></span> <span data-ttu-id="7f7f6-209">Het is op dezelfde manier gevuld als de `-match` `-notmatch` Opera tors en.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-209">It's populated the same way as the `-match` and `-notmatch` operators.</span></span>
<span data-ttu-id="7f7f6-210">Zie about_Switch voor meer informatie over de `switch` - [](about_Switch.md)instructie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-210">For more information about the `switch` statement, see [about_Switch](about_Switch.md).</span></span>

### <a name="myinvocation"></a><span data-ttu-id="7f7f6-211">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="7f7f6-211">$MyInvocation</span></span>

<span data-ttu-id="7f7f6-212">Bevat informatie over de huidige opdracht, zoals de naam, para meters, parameter waarden en informatie over de manier waarop de opdracht is gestart, aangeroepen of aangeroepen, zoals de naam van het script dat de huidige opdracht heet.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-212">Contains information about the current command, such as the name, parameters, parameter values, and information about how the command was started, called, or invoked, such as the name of the script that called the current command.</span></span>

<span data-ttu-id="7f7f6-213">`$MyInvocation` wordt alleen ingevuld voor scripts, functies en script blokken.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-213">`$MyInvocation` is populated only for scripts, function, and script blocks.</span></span> <span data-ttu-id="7f7f6-214">U kunt de informatie in het object **System. Management. Automation. InvocationInfo** gebruiken dat `$MyInvocation` in het huidige script retourneert, zoals het pad en de bestands naam van het script ( `$MyInvocation.MyCommand.Path` ) of de naam van een functie ( `$MyInvocation.MyCommand.Name` ) om de huidige opdracht te identificeren.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-214">You can use the information in the **System.Management.Automation.InvocationInfo** object that `$MyInvocation` returns in the current script, such as the path and file name of the script (`$MyInvocation.MyCommand.Path`) or the name of a function (`$MyInvocation.MyCommand.Name`) to identify the current command.</span></span> <span data-ttu-id="7f7f6-215">Dit is vooral handig om de naam van het huidige script te vinden.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-215">This is particularly useful for finding the name of the current script.</span></span>

<span data-ttu-id="7f7f6-216">Vanaf Power Shell 3,0 `MyInvocation` heeft de volgende nieuwe eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-216">Beginning in PowerShell 3.0, `MyInvocation` has the following new properties.</span></span>

| <span data-ttu-id="7f7f6-217">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="7f7f6-217">Property</span></span>      | <span data-ttu-id="7f7f6-218">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7f7f6-218">Description</span></span>                                         |
| ------------- | --------------------------------------------------- |
| <span data-ttu-id="7f7f6-219">**PSScriptRoot**</span><span class="sxs-lookup"><span data-stu-id="7f7f6-219">**PSScriptRoot**</span></span>  | <span data-ttu-id="7f7f6-220">Bevat het volledige pad naar het script dat is aangeroepen</span><span class="sxs-lookup"><span data-stu-id="7f7f6-220">Contains the full path to the script that invoked</span></span>   |
|               | <span data-ttu-id="7f7f6-221">de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-221">the current command.</span></span> <span data-ttu-id="7f7f6-222">De waarde van deze eigenschap is</span><span class="sxs-lookup"><span data-stu-id="7f7f6-222">The value of this property is</span></span>  |
|               | <span data-ttu-id="7f7f6-223">wordt alleen ingevuld wanneer de aanroeper een script is.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-223">populated only when the caller is a script.</span></span>         |
| <span data-ttu-id="7f7f6-224">**PSCommandPath**</span><span class="sxs-lookup"><span data-stu-id="7f7f6-224">**PSCommandPath**</span></span> | <span data-ttu-id="7f7f6-225">Bevat het volledige pad en de bestands naam van het script</span><span class="sxs-lookup"><span data-stu-id="7f7f6-225">Contains the full path and file name of the script</span></span>  |
|               | <span data-ttu-id="7f7f6-226">die de huidige opdracht heeft aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-226">that invoked the current command.</span></span> <span data-ttu-id="7f7f6-227">De waarde van deze</span><span class="sxs-lookup"><span data-stu-id="7f7f6-227">The value of this</span></span> |
|               | <span data-ttu-id="7f7f6-228">de eigenschap wordt alleen ingevuld wanneer de aanroeper een</span><span class="sxs-lookup"><span data-stu-id="7f7f6-228">property is populated only when the caller is a</span></span>     |
|               | <span data-ttu-id="7f7f6-229">uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-229">script.</span></span>                                             |

<span data-ttu-id="7f7f6-230">In tegens telling tot de `$PSScriptRoot` en `$PSCommandPath` automatische variabelen bevatten de eigenschappen **PSScriptRoot** en **PSCommandPath** van de `$MyInvocation` Automatische variabele informatie over de aanroeper of aanroepende script, niet het huidige script.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-230">Unlike the `$PSScriptRoot` and `$PSCommandPath` automatic variables, the **PSScriptRoot** and **PSCommandPath** properties of the `$MyInvocation` automatic variable contain information about the invoker or calling script, not the current script.</span></span>

### <a name="nestedpromptlevel"></a><span data-ttu-id="7f7f6-231">$NestedPromptLevel</span><span class="sxs-lookup"><span data-stu-id="7f7f6-231">$NestedPromptLevel</span></span>

<span data-ttu-id="7f7f6-232">Bevat het huidige prompt niveau.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-232">Contains the current prompt level.</span></span> <span data-ttu-id="7f7f6-233">Een waarde van 0 geeft aan dat het oorspronkelijke prompt niveau is.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-233">A value of 0 indicates the original prompt level.</span></span> <span data-ttu-id="7f7f6-234">De waarde wordt verhoogd wanneer u een genest niveau invoert en afneemt wanneer u het afsluit.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-234">The value is incremented when you enter a nested level and decremented when you exit it.</span></span>

<span data-ttu-id="7f7f6-235">Power shell presenteert bijvoorbeeld een genest opdracht prompt wanneer u de- `$Host.EnterNestedPrompt` methode gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-235">For example, PowerShell presents a nested command prompt when you use the `$Host.EnterNestedPrompt` method.</span></span> <span data-ttu-id="7f7f6-236">Power shell presenteert ook een geneste opdracht prompt wanneer u een onderbrekings punt in het Power Shell-fout opsporingsprogramma bereikt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-236">PowerShell also presents a nested command prompt when you reach a breakpoint in the PowerShell debugger.</span></span>

<span data-ttu-id="7f7f6-237">Wanneer u een geneste prompt invoert, wordt de huidige opdracht door Power shell onderbroken, wordt de uitvoerings context opgeslagen en wordt de waarde van de `$NestedPromptLevel` variabele verhoogd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-237">When you enter a nested prompt, PowerShell pauses the current command, saves the execution context, and increments the value of the `$NestedPromptLevel` variable.</span></span> <span data-ttu-id="7f7f6-238">Als u extra geneste opdracht prompts wilt maken (Maxi maal 128 niveaus) of als u wilt terugkeren naar de oorspronkelijke opdracht prompt, voltooit u de opdracht of typt u `exit` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-238">To create additional nested command prompts (up to 128 levels) or to return to the original command prompt, complete the command, or type `exit`.</span></span>

<span data-ttu-id="7f7f6-239">De `$NestedPromptLevel` variabele helpt u bij het volgen van het prompt niveau.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-239">The `$NestedPromptLevel` variable helps you track the prompt level.</span></span> <span data-ttu-id="7f7f6-240">U kunt een alternatieve Power shell-opdracht prompt met daarin deze waarde maken zodat deze altijd zichtbaar is.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-240">You can create an alternative PowerShell command prompt that includes this value so that it's always visible.</span></span>

### <a name="null"></a><span data-ttu-id="7f7f6-241">$null</span><span class="sxs-lookup"><span data-stu-id="7f7f6-241">$null</span></span>

<span data-ttu-id="7f7f6-242">`$null` is een automatische variabele die een **Null** of lege waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-242">`$null` is an automatic variable that contains a **null** or empty value.</span></span> <span data-ttu-id="7f7f6-243">U kunt deze variabele gebruiken om een ontbrekende of niet-gedefinieerde waarde te vertegenwoordigen in opdrachten en scripts.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-243">You can use this variable to represent an absent or undefined value in commands and scripts.</span></span>

<span data-ttu-id="7f7f6-244">Power shell behandelt `$null` als een object met een waarde, dat wil zeggen, als een expliciete tijdelijke aanduiding, zodat u kunt gebruiken `$null` om een lege waarde in een reeks waarden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-244">PowerShell treats `$null` as an object with a value, that is, as an explicit placeholder, so you can use `$null` to represent an empty value in a series of values.</span></span>

<span data-ttu-id="7f7f6-245">Als bijvoorbeeld `$null` is opgenomen in een verzameling, wordt deze geteld als een van de objecten.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-245">For example, when `$null` is included in a collection, it's counted as one of the objects.</span></span>

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

<span data-ttu-id="7f7f6-246">Als u de `$null` variabele naar de cmdlet pipet `ForEach-Object` , wordt er een waarde voor gegenereerd `$null` , net zoals voor de andere objecten</span><span class="sxs-lookup"><span data-stu-id="7f7f6-246">If you pipe the `$null` variable to the `ForEach-Object` cmdlet, it generates a value for `$null`, just as it does for the other objects</span></span>

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

<span data-ttu-id="7f7f6-247">Als gevolg hiervan kunt u `$null` **geen parameter waarde** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-247">As a result, you can't use `$null` to mean **no parameter value**.</span></span> <span data-ttu-id="7f7f6-248">Een parameter waarde van `$null` overschrijft de standaard parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-248">A parameter value of `$null` overrides the default parameter value.</span></span>

<span data-ttu-id="7f7f6-249">Omdat Power shell de `$null` variabele echter als tijdelijke aanduiding beschouwt, kunt u deze gebruiken in scripts zoals de volgende, wat niet zou kunnen werken als ze worden `$null` genegeerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-249">However, because PowerShell treats the `$null` variable as a placeholder, you can use it in scripts like the following one, which wouldn't work if `$null` were ignored.</span></span>

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

### <a name="pid"></a><span data-ttu-id="7f7f6-250">$PID</span><span class="sxs-lookup"><span data-stu-id="7f7f6-250">$PID</span></span>

<span data-ttu-id="7f7f6-251">Bevat de proces-id (PID) van het proces dat als host fungeert voor de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-251">Contains the process identifier (PID) of the process that is hosting the current PowerShell session.</span></span>

### <a name="profile"></a><span data-ttu-id="7f7f6-252">$PROFILE</span><span class="sxs-lookup"><span data-stu-id="7f7f6-252">$PROFILE</span></span>

<span data-ttu-id="7f7f6-253">Bevat het volledige pad van het Power shell-profiel voor de huidige gebruiker en de huidige host-toepassing.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-253">Contains the full path of the PowerShell profile for the current user and the current host application.</span></span> <span data-ttu-id="7f7f6-254">U kunt deze variabele gebruiken om het profiel in opdrachten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-254">You can use this variable to represent the profile in commands.</span></span> <span data-ttu-id="7f7f6-255">U kunt deze bijvoorbeeld in een opdracht gebruiken om te bepalen of er een profiel is gemaakt:</span><span class="sxs-lookup"><span data-stu-id="7f7f6-255">For example, you can use it in a command to determine whether a profile has been created:</span></span>

```powershell
Test-Path $PROFILE
```

<span data-ttu-id="7f7f6-256">Of u kunt deze gebruiken in een opdracht voor het maken van een profiel:</span><span class="sxs-lookup"><span data-stu-id="7f7f6-256">Or, you can use it in a command to create a profile:</span></span>

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

<span data-ttu-id="7f7f6-257">U kunt dit in een opdracht gebruiken om het profiel in **notepad.exe** te openen:</span><span class="sxs-lookup"><span data-stu-id="7f7f6-257">You can use it in a command to open the profile in **notepad.exe**:</span></span>

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a><span data-ttu-id="7f7f6-258">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="7f7f6-258">$PSBoundParameters</span></span>

<span data-ttu-id="7f7f6-259">Bevat een woorden lijst van de para meters die worden door gegeven aan een script of functie en de huidige waarden.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-259">Contains a dictionary of the parameters that are passed to a script or function and their current values.</span></span> <span data-ttu-id="7f7f6-260">Deze variabele heeft alleen een waarde in een bereik waarvoor para meters zijn gedeclareerd, zoals een script of functie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-260">This variable has a value only in a scope where parameters are declared, such as a script or function.</span></span> <span data-ttu-id="7f7f6-261">U kunt deze gebruiken om de huidige waarden van para meters weer te geven of te wijzigen of om parameter waarden door te geven aan een ander script of een functie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-261">You can use it to display or change the current values of parameters or to pass parameter values to another script or function.</span></span>

<span data-ttu-id="7f7f6-262">In dit voor beeld wordt de functie **Test2** door gegeven `$PSBoundParameters` aan de functie **test1** .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-262">In this example, the **Test2** function passes the `$PSBoundParameters` to the **Test1** function.</span></span> <span data-ttu-id="7f7f6-263">De `$PSBoundParameters` worden weer gegeven in de indeling **sleutel** en **waarde**.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-263">The `$PSBoundParameters` are displayed in the format of **Key** and **Value**.</span></span>

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

### <a name="pscmdlet"></a><span data-ttu-id="7f7f6-264">$PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="7f7f6-264">$PSCmdlet</span></span>

<span data-ttu-id="7f7f6-265">Bevat een-object dat de cmdlet of geavanceerde functie vertegenwoordigt die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-265">Contains an object that represents the cmdlet or advanced function that's being run.</span></span>

<span data-ttu-id="7f7f6-266">U kunt de eigenschappen en methoden van het object in uw cmdlet of functie code gebruiken om te reageren op de gebruiks voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-266">You can use the properties and methods of the object in your cmdlet or function code to respond to the conditions of use.</span></span> <span data-ttu-id="7f7f6-267">De eigenschap **ParameterSetName** bevat bijvoorbeeld de naam van de para meter die wordt gebruikt en de methode **ShouldProcess** voegt de **WhatIf** en **de para** meters voor de cmdlet dynamisch toe.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-267">For example, the **ParameterSetName** property contains the name of the parameter set that's being used, and the **ShouldProcess** method adds the **WhatIf** and **Confirm** parameters to the cmdlet dynamically.</span></span>

<span data-ttu-id="7f7f6-268">`$PSCmdlet`Zie [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) en [about_Functions_Advanced](about_Functions_Advanced.md)voor meer informatie over de automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-268">For more information about the `$PSCmdlet` automatic variable, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

### <a name="pscommandpath"></a><span data-ttu-id="7f7f6-269">$PSCommandPath</span><span class="sxs-lookup"><span data-stu-id="7f7f6-269">$PSCommandPath</span></span>

<span data-ttu-id="7f7f6-270">Bevat het volledige pad en de bestands naam van het script dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-270">Contains the full path and file name of the script that's being run.</span></span> <span data-ttu-id="7f7f6-271">Deze variabele is in alle scripts geldig.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-271">This variable is valid in all scripts.</span></span>

### <a name="psculture"></a><span data-ttu-id="7f7f6-272">$PSCulture</span><span class="sxs-lookup"><span data-stu-id="7f7f6-272">$PSCulture</span></span>

<span data-ttu-id="7f7f6-273">Vanaf Power shell 7 `$PSCulture` weerspiegelt de cultuur van de huidige Power shell-runs Pace (sessie).</span><span class="sxs-lookup"><span data-stu-id="7f7f6-273">Beginning in PowerShell 7, `$PSCulture` reflects the culture of the current PowerShell runspace (session).</span></span> <span data-ttu-id="7f7f6-274">Als de cultuur wordt gewijzigd in een Power shell-runs Pace, `$PSCulture` wordt de waarde voor die runs Pace bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-274">If the culture is changed in a PowerShell runspace, the `$PSCulture` value for that runspace is updated.</span></span>

<span data-ttu-id="7f7f6-275">De cultuur bepaalt de weergave notatie van items, zoals getallen, valuta's en datums, en wordt opgeslagen in een object **System. Globalization. Culture info** .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-275">The culture determines the display format of items such as numbers, currency, and dates, and is stored in a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="7f7f6-276">Gebruiken `Get-Culture` om de cultuur van de computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-276">Use `Get-Culture` to display the computer's culture.</span></span> <span data-ttu-id="7f7f6-277">`$PSCulture` bevat de waarde van de eigenschap **naam** .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-277">`$PSCulture` contains the **Name** property's value.</span></span>

### <a name="psdebugcontext"></a><span data-ttu-id="7f7f6-278">$PSDebugContext</span><span class="sxs-lookup"><span data-stu-id="7f7f6-278">$PSDebugContext</span></span>

<span data-ttu-id="7f7f6-279">Bij het opsporen van fouten bevat deze variabele informatie over de fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-279">While debugging, this variable contains information about the debugging environment.</span></span> <span data-ttu-id="7f7f6-280">Anders bevat het een **Null** -waarde.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-280">Otherwise, it contains a **null** value.</span></span> <span data-ttu-id="7f7f6-281">Als gevolg hiervan kunt u deze gebruiken om aan te geven of het fout opsporingsprogramma controle heeft.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-281">As a result, you can use it to indicate whether the debugger has control.</span></span> <span data-ttu-id="7f7f6-282">Bij het invullen bevat deze een **PsDebugContext** -object met **onderbrekings punten** en eigenschappen **InvocationInfo** .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-282">When populated, it contains a **PsDebugContext** object that has **Breakpoints** and **InvocationInfo** properties.</span></span> <span data-ttu-id="7f7f6-283">De eigenschap **InvocationInfo** heeft verschillende nuttige eigenschappen, waaronder de **locatie** -eigenschap.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-283">The **InvocationInfo** property has several useful properties, including the **Location** property.</span></span> <span data-ttu-id="7f7f6-284">De eigenschap **Location** geeft het pad van het script aan waarvoor fouten worden opgespoord.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-284">The **Location** property indicates the path of the script that is being debugged.</span></span>

### <a name="pshome"></a><span data-ttu-id="7f7f6-285">$PSHOME</span><span class="sxs-lookup"><span data-stu-id="7f7f6-285">$PSHOME</span></span>

<span data-ttu-id="7f7f6-286">Bevat het volledige pad van de installatie directory voor Power shell, meestal `$env:windir\System32\PowerShell\v1.0` in Windows-systemen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-286">Contains the full path of the installation directory for PowerShell, typically, `$env:windir\System32\PowerShell\v1.0` in Windows systems.</span></span> <span data-ttu-id="7f7f6-287">U kunt deze variabele gebruiken in de paden van Power Shell-bestanden.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-287">You can use this variable in the paths of PowerShell files.</span></span> <span data-ttu-id="7f7f6-288">De volgende opdracht zoekt bijvoorbeeld naar de conceptuele Help-onderwerpen voor de **variabele** woord:</span><span class="sxs-lookup"><span data-stu-id="7f7f6-288">For example, the following command searches the conceptual Help topics for the word **variable**:</span></span>

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a><span data-ttu-id="7f7f6-289">$PSItem</span><span class="sxs-lookup"><span data-stu-id="7f7f6-289">$PSItem</span></span>

<span data-ttu-id="7f7f6-290">Hetzelfde als `$_` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-290">Same as `$_`.</span></span> <span data-ttu-id="7f7f6-291">Bevat het huidige object in het pijplijn object.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-291">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="7f7f6-292">U kunt deze variabele gebruiken in opdrachten voor het uitvoeren van een actie op elk object of op geselecteerde objecten in een pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-292">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="psscriptroot"></a><span data-ttu-id="7f7f6-293">$PSScriptRoot</span><span class="sxs-lookup"><span data-stu-id="7f7f6-293">$PSScriptRoot</span></span>

<span data-ttu-id="7f7f6-294">Bevat de map van waaruit een script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-294">Contains the directory from which a script is being run.</span></span>

<span data-ttu-id="7f7f6-295">In Power Shell 2,0 is deze variabele alleen geldig in script modules ( `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="7f7f6-295">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
<span data-ttu-id="7f7f6-296">Vanaf Power Shell 3,0 is het in alle scripts geldig.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-296">Beginning in PowerShell 3.0, it's valid in all scripts.</span></span>

### <a name="pssenderinfo"></a><span data-ttu-id="7f7f6-297">$PSSenderInfo</span><span class="sxs-lookup"><span data-stu-id="7f7f6-297">$PSSenderInfo</span></span>

<span data-ttu-id="7f7f6-298">Bevat informatie over de gebruiker die de PSSession heeft gestart, met inbegrip van de gebruikers-id en de tijd zone van de oorspronkelijke computer.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-298">Contains information about the user who started the PSSession, including the user identity and the time zone of the originating computer.</span></span> <span data-ttu-id="7f7f6-299">Deze variabele is alleen beschikbaar in PSSessions.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-299">This variable is available only in PSSessions.</span></span>

<span data-ttu-id="7f7f6-300">De `$PSSenderInfo` variabele bevat een door de gebruiker Configureer bare eigenschap, **ApplicationArguments**, die standaard alleen de `$PSVersionTable` van de oorspronkelijke sessie bevat.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-300">The `$PSSenderInfo` variable includes a user-configurable property, **ApplicationArguments**, that by default, contains only the `$PSVersionTable` from the originating session.</span></span> <span data-ttu-id="7f7f6-301">Als u gegevens wilt toevoegen aan de eigenschap **ApplicationArguments** , gebruikt u de para meter **ApplicationArguments** van de `New-PSSessionOption` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-301">To add data to the **ApplicationArguments** property, use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet.</span></span>

### <a name="psuiculture"></a><span data-ttu-id="7f7f6-302">$PSUICulture</span><span class="sxs-lookup"><span data-stu-id="7f7f6-302">$PSUICulture</span></span>

<span data-ttu-id="7f7f6-303">Bevat de naam van de cultuur van de gebruikers interface die momenteel wordt gebruikt in het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-303">Contains the name of the user interface (UI) culture that's currently in use in the operating system.</span></span> <span data-ttu-id="7f7f6-304">De GEBRUIKERSINTERFACE cultuur bepaalt welke teken reeksen worden gebruikt voor elementen van de gebruikers interface, zoals menu's en berichten.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-304">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span> <span data-ttu-id="7f7f6-305">Dit is de waarde van de eigenschap **System.Globalization.CultureInfo.CurrentUICulture.name** van het systeem.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-305">This is the value of the **System.Globalization.CultureInfo.CurrentUICulture.Name** property of the system.</span></span> <span data-ttu-id="7f7f6-306">Gebruik de cmdlet om het object **System. Globalization. Culture info** voor het systeem op te halen `Get-UICulture` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-306">To get the **System.Globalization.CultureInfo** object for the system, use the `Get-UICulture` cmdlet.</span></span>

### <a name="psversiontable"></a><span data-ttu-id="7f7f6-307">$PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="7f7f6-307">$PSVersionTable</span></span>

<span data-ttu-id="7f7f6-308">Bevat een alleen-lezen hash-tabel waarin details worden weer gegeven over de versie van Power shell die in de huidige sessie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-308">Contains a read-only hash table that displays details about the version of PowerShell that is running in the current session.</span></span> <span data-ttu-id="7f7f6-309">De tabel bevat de volgende items:</span><span class="sxs-lookup"><span data-stu-id="7f7f6-309">The table includes the following items:</span></span>

| <span data-ttu-id="7f7f6-310">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="7f7f6-310">Property</span></span>                  | <span data-ttu-id="7f7f6-311">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7f7f6-311">Description</span></span>                                   |
| ------------------------- | --------------------------------------------- |
| <span data-ttu-id="7f7f6-312">**PSVersion**</span><span class="sxs-lookup"><span data-stu-id="7f7f6-312">**PSVersion**</span></span>             | <span data-ttu-id="7f7f6-313">Het Power shell-versie nummer</span><span class="sxs-lookup"><span data-stu-id="7f7f6-313">The PowerShell version number</span></span>                 |
| <span data-ttu-id="7f7f6-314">**PSEdition**</span><span class="sxs-lookup"><span data-stu-id="7f7f6-314">**PSEdition**</span></span>             | <span data-ttu-id="7f7f6-315">Deze eigenschap heeft de waarde ' Desktop ' voor</span><span class="sxs-lookup"><span data-stu-id="7f7f6-315">This property has the value of 'Desktop' for</span></span>  |
|                           | <span data-ttu-id="7f7f6-316">Power Shell 4 en lager, evenals Power shell</span><span class="sxs-lookup"><span data-stu-id="7f7f6-316">PowerShell 4 and below as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="7f7f6-317">5,1 op volledig uitgeruste Windows-edities.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-317">5.1 on full-featured Windows editions.</span></span>        |
|                           | <span data-ttu-id="7f7f6-318">Deze eigenschap heeft de waarde ' core ' voor</span><span class="sxs-lookup"><span data-stu-id="7f7f6-318">This property has the value of 'Core' for</span></span>     |
|                           | <span data-ttu-id="7f7f6-319">Power shell 6 en hoger, evenals Power shell</span><span class="sxs-lookup"><span data-stu-id="7f7f6-319">PowerShell 6 and above as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="7f7f6-320">Power shell 5,1 voor edities met verminderde footprint</span><span class="sxs-lookup"><span data-stu-id="7f7f6-320">PowerShell 5.1 on reduced-footprint editions</span></span>  |
|                           | <span data-ttu-id="7f7f6-321">net als Windows nano server of Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-321">like Windows Nano Server or Windows IoT.</span></span>      |
| <span data-ttu-id="7f7f6-322">**GitCommitId**</span><span class="sxs-lookup"><span data-stu-id="7f7f6-322">**GitCommitId**</span></span>           | <span data-ttu-id="7f7f6-323">De door Voer-id van de bron bestanden, in GitHub,</span><span class="sxs-lookup"><span data-stu-id="7f7f6-323">The commit Id of the source files, in GitHub,</span></span> |
| <span data-ttu-id="7f7f6-324">**Besturingssysteem**</span><span class="sxs-lookup"><span data-stu-id="7f7f6-324">**OS**</span></span>                    | <span data-ttu-id="7f7f6-325">Beschrijving van het besturings systeem dat</span><span class="sxs-lookup"><span data-stu-id="7f7f6-325">Description of the operating system that</span></span>      |
|                           | <span data-ttu-id="7f7f6-326">Power shell wordt uitgevoerd op.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-326">PowerShell is running on.</span></span>                     |
| <span data-ttu-id="7f7f6-327">**Platform**</span><span class="sxs-lookup"><span data-stu-id="7f7f6-327">**Platform**</span></span>              | <span data-ttu-id="7f7f6-328">Platform waarop het besturings systeem wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="7f7f6-328">Platform that the operating system is running</span></span> |
|                           | <span data-ttu-id="7f7f6-329">waarop.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-329">on.</span></span> <span data-ttu-id="7f7f6-330">De waarde op Linux en macOS is **UNIX**.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-330">The value on Linux and macOS is **Unix**.</span></span> |
|                           | <span data-ttu-id="7f7f6-331">Zie `$IsMacOs` en `$IsLinux` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-331">See `$IsMacOs` and `$IsLinux`.</span></span>                |
| <span data-ttu-id="7f7f6-332">**PSCompatibleVersions**</span><span class="sxs-lookup"><span data-stu-id="7f7f6-332">**PSCompatibleVersions**</span></span>  | <span data-ttu-id="7f7f6-333">Versies van Power shell die compatibel zijn</span><span class="sxs-lookup"><span data-stu-id="7f7f6-333">Versions of PowerShell that are compatible</span></span>    |
|                           | <span data-ttu-id="7f7f6-334">met de huidige versie</span><span class="sxs-lookup"><span data-stu-id="7f7f6-334">with the current version</span></span>                      |
| <span data-ttu-id="7f7f6-335">**PSRemotingProtocolVersion**</span><span class="sxs-lookup"><span data-stu-id="7f7f6-335">**PSRemotingProtocolVersion**</span></span> | <span data-ttu-id="7f7f6-336">De versie van de Power shell Remote</span><span class="sxs-lookup"><span data-stu-id="7f7f6-336">The version of the PowerShell remote</span></span>      |
|                           | <span data-ttu-id="7f7f6-337">beheer protocol.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-337">management protocol.</span></span>                          |
| <span data-ttu-id="7f7f6-338">**SerializationVersion**</span><span class="sxs-lookup"><span data-stu-id="7f7f6-338">**SerializationVersion**</span></span>  | <span data-ttu-id="7f7f6-339">De versie van de serialisatie-methode</span><span class="sxs-lookup"><span data-stu-id="7f7f6-339">The version of the serialization method</span></span>       |
| <span data-ttu-id="7f7f6-340">**WSManStackVersion**</span><span class="sxs-lookup"><span data-stu-id="7f7f6-340">**WSManStackVersion**</span></span>     | <span data-ttu-id="7f7f6-341">Het versie nummer van de WS-Management stack</span><span class="sxs-lookup"><span data-stu-id="7f7f6-341">The version number of the WS-Management stack</span></span> |

### <a name="pwd"></a><span data-ttu-id="7f7f6-342">$PWD</span><span class="sxs-lookup"><span data-stu-id="7f7f6-342">$PWD</span></span>

<span data-ttu-id="7f7f6-343">Bevat een Path-object dat het volledige pad vertegenwoordigt van de huidige maplocatie voor de huidige Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-343">Contains a path object that represents the full path of the current directory location for the current PowerShell runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="7f7f6-344">Power shell ondersteunt meerdere runspaces per proces.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-344">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="7f7f6-345">Elke runs Pace heeft zijn eigen _huidige map_.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-345">Each runspace has its own _current directory_.</span></span> <span data-ttu-id="7f7f6-346">Dit is niet hetzelfde als de huidige map van het proces: `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-346">This is not the same as the current directory of the process: `[System.Environment]::CurrentDirectory`.</span></span>

### <a name="sender"></a><span data-ttu-id="7f7f6-347">$Sender</span><span class="sxs-lookup"><span data-stu-id="7f7f6-347">$Sender</span></span>

<span data-ttu-id="7f7f6-348">Bevat het object dat deze gebeurtenis heeft gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-348">Contains the object that generated this event.</span></span> <span data-ttu-id="7f7f6-349">Deze variabele wordt alleen ingevuld binnen het actie blok van een gebeurtenis registratie opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-349">This variable is populated only within the Action block of an event registration command.</span></span> <span data-ttu-id="7f7f6-350">De waarde van deze variabele kan ook worden gevonden in de eigenschap Sender van het **PSEventArgs** -object dat `Get-Event` retourneert.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-350">The value of this variable can also be found in the Sender property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="shellid"></a><span data-ttu-id="7f7f6-351">$ShellId</span><span class="sxs-lookup"><span data-stu-id="7f7f6-351">$ShellId</span></span>

<span data-ttu-id="7f7f6-352">Bevat de id van de huidige shell.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-352">Contains the identifier of the current shell.</span></span>

### <a name="stacktrace"></a><span data-ttu-id="7f7f6-353">$StackTrace</span><span class="sxs-lookup"><span data-stu-id="7f7f6-353">$StackTrace</span></span>

<span data-ttu-id="7f7f6-354">Bevat een stack tracering voor de meest recente fout.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-354">Contains a stack trace for the most recent error.</span></span>

### <a name="switch"></a><span data-ttu-id="7f7f6-355">$switch</span><span class="sxs-lookup"><span data-stu-id="7f7f6-355">$switch</span></span>

<span data-ttu-id="7f7f6-356">Bevat de enumerator niet de resulterende waarden van een `Switch` instructie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-356">Contains the enumerator not the resulting values of a `Switch` statement.</span></span> <span data-ttu-id="7f7f6-357">De `$switch` variabele bestaat alleen als de `Switch` instructie wordt uitgevoerd en wordt verwijderd wanneer de instructie wordt uitgevoerd `switch` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-357">The `$switch` variable exists only while the `Switch` statement is running; it's deleted when the `switch` statement completes execution.</span></span> <span data-ttu-id="7f7f6-358">Zie [about_Switch](about_Switch.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-358">For more information, see [about_Switch](about_Switch.md).</span></span>

<span data-ttu-id="7f7f6-359">Opsommingen bevatten eigenschappen en methoden die u kunt gebruiken om loop waarden op te halen en de huidige loop-iteratie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-359">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="7f7f6-360">Zie [using enumeraties](#using-enumerators)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-360">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="this"></a><span data-ttu-id="7f7f6-361">$this</span><span class="sxs-lookup"><span data-stu-id="7f7f6-361">$this</span></span>

<span data-ttu-id="7f7f6-362">In een script blok dat een script eigenschap of script methode definieert, `$this` verwijst de variabele naar het object dat wordt uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-362">In a script block that defines a script property or script method, the `$this` variable refers to the object that is being extended.</span></span>

<span data-ttu-id="7f7f6-363">In een aangepaste klasse verwijst de `$this` variabele naar het klassen object zelf, waardoor toegang wordt toegestaan tot eigenschappen en methoden die zijn gedefinieerd in de klasse.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-363">In a custom class, the `$this` variable refers to the class object itself allowing access to properties and methods defined in the class.</span></span>

### <a name="true"></a><span data-ttu-id="7f7f6-364">$true</span><span class="sxs-lookup"><span data-stu-id="7f7f6-364">$true</span></span>

<span data-ttu-id="7f7f6-365">Bevat **waar**.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-365">Contains **True**.</span></span> <span data-ttu-id="7f7f6-366">U kunt deze variabele gebruiken om **waar** in opdrachten en scripts weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-366">You can use this variable to represent **True** in commands and scripts.</span></span>

## <a name="using-enumerators"></a><span data-ttu-id="7f7f6-367">Opsommingen gebruiken</span><span class="sxs-lookup"><span data-stu-id="7f7f6-367">Using Enumerators</span></span>

<span data-ttu-id="7f7f6-368">De `$input` `$foreach` variabelen, en `$switch` zijn alle inventarisaties die worden gebruikt om de waarden te herhalen die worden verwerkt door hun insluitende code blok.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-368">The `$input`, `$foreach`, and `$switch` variables are all enumerators used to iterate through the values processed by their containing code block.</span></span>

<span data-ttu-id="7f7f6-369">Een enumerator bevat eigenschappen en methoden die u kunt gebruiken om herhaling te herstellen of opnieuw in te stellen, of om iteratie waarden op te halen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-369">An enumerator contains properties and methods you can use to advance or reset iteration, or retrieve iteration values.</span></span> <span data-ttu-id="7f7f6-370">Het rechtstreeks bewerken van opsommings wordt niet beschouwd als best practice.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-370">Directly manipulating enumerators isn't considered best practice.</span></span>

- <span data-ttu-id="7f7f6-371">Binnen lussen moeten [de tref woorden](about_Break.md) voor stroom beheer en [door gaan](about_Continue.md) worden voor keur.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-371">Within loops, flow control keywords [break](about_Break.md) and [continue](about_Continue.md) should be preferred.</span></span>
- <span data-ttu-id="7f7f6-372">Binnen functies die pijplijn invoer accepteren, is het best practice om para meters met de kenmerken **ValueFromPipeline** of **ValueFromPipelineByPropertyName** te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-372">Within functions that accept pipeline input, it's best practice to use Parameters with the **ValueFromPipeline** or **ValueFromPipelineByPropertyName** attributes.</span></span>

  <span data-ttu-id="7f7f6-373">Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-373">For more information, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="movenext"></a><span data-ttu-id="7f7f6-374">Aangeroepen</span><span class="sxs-lookup"><span data-stu-id="7f7f6-374">MoveNext</span></span>

<span data-ttu-id="7f7f6-375">De methode [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) gaat de enumerator door naar het volgende element van de verzameling.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-375">The [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) method advances the enumerator to the next element of the collection.</span></span> <span data-ttu-id="7f7f6-376">**MoveNext** retourneert **True** als de enumerator is uitgebreid, **False** als de enumerator het einde van de verzameling heeft door gegeven.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-376">**MoveNext** returns **True** if the enumerator was successfully advanced, **False** if the enumerator has passed the end of the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="7f7f6-377">De **Booleaanse** waarde die mijn **MoveNext** retourneert, wordt verzonden naar de uitvoer stroom.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-377">The **Boolean** value returned my **MoveNext** is sent to the output stream.</span></span>
> <span data-ttu-id="7f7f6-378">U kunt de uitvoer onderdrukken door deze te typecasting `[void]` of deze uit te sluizen naar [out-null](xref:Microsoft.PowerShell.Core.Out-Null).</span><span class="sxs-lookup"><span data-stu-id="7f7f6-378">You can suppress the output by typecasting it to `[void]` or piping it to [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null).</span></span>
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a><span data-ttu-id="7f7f6-379">Opnieuw instellen</span><span class="sxs-lookup"><span data-stu-id="7f7f6-379">Reset</span></span>

<span data-ttu-id="7f7f6-380">Met de methode [Reset](/dotnet/api/system.collections.ienumerator.reset) wordt de enumerator ingesteld op de oorspronkelijke positie, die **vóór** het eerste element in de verzameling ligt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-380">The [Reset](/dotnet/api/system.collections.ienumerator.reset) method sets the enumerator to its initial position, which is **before** the first element in the collection.</span></span>

### <a name="current"></a><span data-ttu-id="7f7f6-381">Huidig</span><span class="sxs-lookup"><span data-stu-id="7f7f6-381">Current</span></span>

<span data-ttu-id="7f7f6-382">Met de [huidige](/dotnet/api/system.collections.ienumerator.current) eigenschap wordt het element in de verzameling, of de pijp lijn, op de huidige positie van de enumerator opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-382">The [Current](/dotnet/api/system.collections.ienumerator.current) property gets the element in the collection, or pipeline, at the current position of the enumerator.</span></span>

<span data-ttu-id="7f7f6-383">De **huidige** eigenschap blijft dezelfde eigenschap retour neren totdat **MoveNext** is aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-383">The **Current** property continues to return the same property until **MoveNext** is called.</span></span>

## <a name="examples"></a><span data-ttu-id="7f7f6-384">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="7f7f6-384">Examples</span></span>

### <a name="example-1-using-the-input-variable"></a><span data-ttu-id="7f7f6-385">Voor beeld 1: de variabele $input gebruiken</span><span class="sxs-lookup"><span data-stu-id="7f7f6-385">Example 1: Using the $input variable</span></span>

<span data-ttu-id="7f7f6-386">In het volgende voor beeld wordt met de `$input` variabele de variabele gewist tot de volgende keer dat het proces blok wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-386">In the following example, accessing the `$input` variable clears the variable until the next time the process block executes.</span></span> <span data-ttu-id="7f7f6-387">Als u de methode **Reset** gebruikt, wordt de variabele opnieuw ingesteld `$input` op de huidige pijplijn waarde.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-387">Using the **Reset** method resets the `$input` variable to the current pipeline value.</span></span>

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

<span data-ttu-id="7f7f6-388">De variabele wordt door het proces blok automatisch `$input` door berekend, zelfs als u geen toegang hebt.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-388">The process block automatically advances the `$input` variable even if you don't access it.</span></span>

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

### <a name="example-2-using-input-outside-the-process-block"></a><span data-ttu-id="7f7f6-389">Voor beeld 2: $input buiten het proces blok gebruiken</span><span class="sxs-lookup"><span data-stu-id="7f7f6-389">Example 2: Using $input outside the process block</span></span>

<span data-ttu-id="7f7f6-390">Buiten het proces blok bevindt de `$input` variabele alle waarden die in de functie zijn ondergebracht.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-390">Outside of the process block the `$input` variable represents all the values piped into the function.</span></span>

- <span data-ttu-id="7f7f6-391">Als u de variabele opent, worden `$input` alle waarden gewist.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-391">Accessing the `$input` variable clears all values.</span></span>
- <span data-ttu-id="7f7f6-392">De methode **Reset** herstelt de volledige verzameling.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-392">The **Reset** method resets the entire collection.</span></span>
- <span data-ttu-id="7f7f6-393">De **huidige** eigenschap wordt nooit ingevuld.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-393">The **Current** property is never populated.</span></span>
- <span data-ttu-id="7f7f6-394">De methode **MoveNext** retourneert False omdat de verzameling niet kan worden uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-394">The **MoveNext** method returns false because the collection can't be advanced.</span></span>
  - <span data-ttu-id="7f7f6-395">Door **MoveNext** aan te roepen, wordt de `$input` variabele gewist.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-395">Calling **MoveNext** clears out the `$input` variable.</span></span>

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

### <a name="example-3-using-the-inputcurrent-property"></a><span data-ttu-id="7f7f6-396">Voor beeld 3: het $input gebruiken. Huidige eigenschap</span><span class="sxs-lookup"><span data-stu-id="7f7f6-396">Example 3: Using the $input.Current property</span></span>

<span data-ttu-id="7f7f6-397">Met de **huidige** eigenschap kan de huidige pijplijn waarde meerdere keren worden gebruikt zonder gebruik te maken van de methode **Reset** .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-397">By using the **Current** property, the current pipeline value can be accessed multiple times without using the **Reset** method.</span></span> <span data-ttu-id="7f7f6-398">De methode **MoveNext** wordt niet automatisch aangeroepen door het proces blok.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-398">The process block doesn't automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="7f7f6-399">De **huidige** eigenschap wordt nooit gevuld tenzij u **MoveNext** expliciet aanroept.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-399">The **Current** property will never be populated unless you explicitly call **MoveNext**.</span></span> <span data-ttu-id="7f7f6-400">De **huidige** eigenschap kan meermaals worden gebruikt binnen het proces blok zonder dat de waarde ervan wordt gewist.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-400">The **Current** property can be accessed multiple times inside the process block without clearing its value.</span></span>

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

### <a name="example-4-using-the-foreach-variable"></a><span data-ttu-id="7f7f6-401">Voor beeld 4: de variabele $foreach gebruiken</span><span class="sxs-lookup"><span data-stu-id="7f7f6-401">Example 4: Using the $foreach variable</span></span>

<span data-ttu-id="7f7f6-402">In tegens telling tot de `$input` variabele `$foreach` vertegenwoordigt de variabele altijd alle items in de verzameling wanneer deze rechtstreeks worden geopend.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-402">Unlike the `$input` variable, the `$foreach` variable always represents all items in the collection when accessed directly.</span></span> <span data-ttu-id="7f7f6-403">Gebruik de eigenschap **Current** om toegang te krijgen tot het huidige verzamelings element en de methoden **Reset** en **MoveNext** om de waarde ervan te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-403">Use the **Current** property to access the current collection element, and the **Reset** and **MoveNext** methods to change its value.</span></span>

> [!NOTE]
> <span data-ttu-id="7f7f6-404">Bij elke herhaling van de `foreach` lus wordt de methode **MoveNext** automatisch aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-404">Each iteration of the `foreach` loop will automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="7f7f6-405">De volgende lus wordt alleen twee keer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-405">The following loop only executes twice.</span></span> <span data-ttu-id="7f7f6-406">In de tweede iteratie wordt de verzameling verplaatst naar het derde element voordat de herhaling is voltooid.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-406">In the second iteration, the collection is moved to the third element before the iteration is complete.</span></span> <span data-ttu-id="7f7f6-407">Na de tweede iteratie zijn er nu geen waarden meer om te herhalen en wordt de lus afgebroken.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-407">After the second iteration, there are now no more values to iterate, and the loop terminates.</span></span>

<span data-ttu-id="7f7f6-408">De eigenschap **MoveNext** heeft geen invloed op de variabele die is gekozen om de verzameling () door te lopen `$Num` .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-408">The **MoveNext** property doesn't affect the variable chosen to iterate through the collection (`$Num`).</span></span>

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

<span data-ttu-id="7f7f6-409">Als u de methode **Reset** gebruikt, wordt het huidige element in de verzameling opnieuw ingesteld.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-409">Using the **Reset** method resets the current element in the collection.</span></span> <span data-ttu-id="7f7f6-410">In het volgende voor beeld worden de eerste twee elementen **twee keer** door lopen, omdat de methode **Reset** is aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-410">The following example loops through the first two elements **twice** because the **Reset** method is called.</span></span> <span data-ttu-id="7f7f6-411">Na de eerste twee lussen `if` mislukt de instructie en doorloopt de lus alle drie de elementen normaal.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-411">After the first two loops, the `if` statement fails and the loop iterates through all three elements normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f7f6-412">Dit kan leiden tot een oneindige lus.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-412">This could result in an infinite loop.</span></span>

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

### <a name="example-5-using-the-switch-variable"></a><span data-ttu-id="7f7f6-413">Voor beeld 5: de variabele $switch gebruiken</span><span class="sxs-lookup"><span data-stu-id="7f7f6-413">Example 5: Using the $switch variable</span></span>

<span data-ttu-id="7f7f6-414">De `$switch` variabele heeft precies dezelfde regels als de `$foreach` variabele.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-414">The `$switch` variable has the exact same rules as the `$foreach` variable.</span></span>
<span data-ttu-id="7f7f6-415">In het volgende voor beeld worden alle enumerator-concepten gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="7f7f6-415">The following example demonstrates all the enumerator concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="7f7f6-416">U ziet dat de **NotEvaluated** -Case nooit wordt uitgevoerd, ook al is er geen `break` instructie na de methode **MoveNext** .</span><span class="sxs-lookup"><span data-stu-id="7f7f6-416">Note how the **NotEvaluated** case is never executed, even though there's no `break` statement after the **MoveNext** method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7f7f6-417">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7f7f6-417">See also</span></span>

[<span data-ttu-id="7f7f6-418">about_Functions</span><span class="sxs-lookup"><span data-stu-id="7f7f6-418">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="7f7f6-419">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="7f7f6-419">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="7f7f6-420">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="7f7f6-420">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="7f7f6-421">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="7f7f6-421">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="7f7f6-422">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="7f7f6-422">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="7f7f6-423">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="7f7f6-423">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="7f7f6-424">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="7f7f6-424">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="7f7f6-425">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="7f7f6-425">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="7f7f6-426">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="7f7f6-426">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="7f7f6-427">about_Variables</span><span class="sxs-lookup"><span data-stu-id="7f7f6-427">about_Variables</span></span>](about_Variables.md)

