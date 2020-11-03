---
description: Hierin wordt beschreven hoe u de `Try` -, `Catch` -en- `Finally` blokken gebruikt voor het afhandelen van afsluit fouten.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: 1bb6974e1ba42861a4f411777be237685d2becbc
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252061"
---
# <a name="about-try-catch-finally"></a><span data-ttu-id="f024a-104">Over try catch finally</span><span class="sxs-lookup"><span data-stu-id="f024a-104">About Try Catch Finally</span></span>

## <a name="short-description"></a><span data-ttu-id="f024a-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f024a-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="f024a-106">Hierin wordt beschreven hoe u de `Try` -, `Catch` -en- `Finally` blokken gebruikt voor het afhandelen van afsluit fouten.</span><span class="sxs-lookup"><span data-stu-id="f024a-106">Describes how to use the `Try`, `Catch`, and `Finally` blocks to handle terminating errors.</span></span>

## <a name="long-description"></a><span data-ttu-id="f024a-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f024a-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="f024a-108">Gebruik `Try` , `Catch` , en `Finally` blokkeert om te reageren op afsluit fouten in scripts of af te handelen.</span><span class="sxs-lookup"><span data-stu-id="f024a-108">Use `Try`, `Catch`, and `Finally` blocks to respond to or handle terminating errors in scripts.</span></span> <span data-ttu-id="f024a-109">De `Trap` instructie kan ook worden gebruikt voor het afhandelen van afsluit fouten in scripts.</span><span class="sxs-lookup"><span data-stu-id="f024a-109">The `Trap` statement can also be used to handle terminating errors in scripts.</span></span> <span data-ttu-id="f024a-110">Zie [about_Trap](about_Trap.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f024a-110">For more information, see [about_Trap](about_Trap.md).</span></span>

<span data-ttu-id="f024a-111">Een afsluit fout zorgt ervoor dat een instructie niet kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f024a-111">A terminating error stops a statement from running.</span></span> <span data-ttu-id="f024a-112">Als Power shell geen afsluit fout op een of andere manier verwerkt, stopt Power shell ook met het uitvoeren van de functie of het script met behulp van de huidige pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="f024a-112">If PowerShell does not handle a terminating error in some way, PowerShell also stops running the function or script using the current pipeline.</span></span> <span data-ttu-id="f024a-113">In andere talen, zoals C \# , worden afsluit fouten aangeduid als uitzonde ringen.</span><span class="sxs-lookup"><span data-stu-id="f024a-113">In other languages, such as C\#, terminating errors are referred to as exceptions.</span></span>

<span data-ttu-id="f024a-114">Gebruik het `Try` blok om een sectie te definiëren van een script waarin Power shell op fouten moet worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="f024a-114">Use the `Try` block to define a section of a script in which you want PowerShell to monitor for errors.</span></span> <span data-ttu-id="f024a-115">Als er een fout optreedt in het `Try` blok, wordt de fout eerst opgeslagen in de `$Error` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="f024a-115">When an error occurs within the `Try` block, the error is first saved to the `$Error` automatic variable.</span></span> <span data-ttu-id="f024a-116">Power shell zoekt vervolgens naar een `Catch` blok om de fout af te handelen.</span><span class="sxs-lookup"><span data-stu-id="f024a-116">PowerShell then searches for a `Catch` block to handle the error.</span></span> <span data-ttu-id="f024a-117">Als de `Try` instructie geen overeenkomend blok heeft `Catch` , gaat Power shell door met zoeken naar een geschikt `Catch` blok of een `Trap` instructie in de bovenliggende bereiken.</span><span class="sxs-lookup"><span data-stu-id="f024a-117">If the `Try` statement does not have a matching `Catch` block, PowerShell continues to search for an appropriate `Catch` block or `Trap` statement in the parent scopes.</span></span> <span data-ttu-id="f024a-118">Wanneer een `Catch` blok is voltooid of als er geen geschikt `Catch` blok of een `Trap` instructie wordt gevonden, `Finally` wordt het blok uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f024a-118">After a `Catch` block is completed or if no appropriate `Catch` block or `Trap` statement is found, the `Finally` block is run.</span></span> <span data-ttu-id="f024a-119">Als de fout niet kan worden verwerkt, wordt de fout naar de fout stroom geschreven.</span><span class="sxs-lookup"><span data-stu-id="f024a-119">If the error cannot be handled, the error is written to the error stream.</span></span>

<span data-ttu-id="f024a-120">Een `Catch` blok kan opdrachten bevatten voor het volgen van de fout of voor het herstellen van de verwachte stroom van het script.</span><span class="sxs-lookup"><span data-stu-id="f024a-120">A `Catch` block can include commands for tracking the error or for recovering the expected flow of the script.</span></span> <span data-ttu-id="f024a-121">Een `Catch` blok kan opgeven welke fout typen er worden onderschept.</span><span class="sxs-lookup"><span data-stu-id="f024a-121">A `Catch` block can specify which error types it catches.</span></span> <span data-ttu-id="f024a-122">Een `Try` instructie kan meerdere `Catch` blokken bevatten voor verschillende soorten fouten.</span><span class="sxs-lookup"><span data-stu-id="f024a-122">A `Try` statement can include multiple `Catch` blocks for different kinds of errors.</span></span>

<span data-ttu-id="f024a-123">Een `Finally` blok kan worden gebruikt om resources vrij te maken die niet langer nodig zijn voor uw script.</span><span class="sxs-lookup"><span data-stu-id="f024a-123">A `Finally` block can be used to free any resources that are no longer needed by your script.</span></span>

<span data-ttu-id="f024a-124">`Try`, en `Catch` `Finally` lijken op de `Try` , `Catch` en `Finally` tref woorden die worden gebruikt in de \# programmeer taal C.</span><span class="sxs-lookup"><span data-stu-id="f024a-124">`Try`, `Catch`, and `Finally` resemble the `Try`, `Catch`, and `Finally` keywords used in the C\# programming language.</span></span>

### <a name="syntax"></a><span data-ttu-id="f024a-125">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f024a-125">SYNTAX</span></span>

<span data-ttu-id="f024a-126">Een `Try` instructie bevat een `Try` blok, nul of meer `Catch` blokken en nul of één `Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="f024a-126">A `Try` statement contains a `Try` block, zero or more `Catch` blocks, and zero or one `Finally` block.</span></span> <span data-ttu-id="f024a-127">Een `Try` instructie moet ten minste één `Catch` blok of één `Finally` blok bevatten.</span><span class="sxs-lookup"><span data-stu-id="f024a-127">A `Try` statement must have at least one `Catch` block or one `Finally` block.</span></span>

<span data-ttu-id="f024a-128">Hieronder ziet u de `Try` blok syntaxis:</span><span class="sxs-lookup"><span data-stu-id="f024a-128">The following shows the `Try` block syntax:</span></span>

```powershell
try {<statement list>}
```

<span data-ttu-id="f024a-129">Het `Try` tref woord wordt gevolgd door een lijst met overzichten tussen accolades.</span><span class="sxs-lookup"><span data-stu-id="f024a-129">The `Try` keyword is followed by a statement list in braces.</span></span> <span data-ttu-id="f024a-130">Als er een afsluit fout optreedt terwijl de instructies in de lijst met overzichten worden uitgevoerd, wordt het fout object door het script door gegeven van het `Try` blok naar een geschikt `Catch` blok.</span><span class="sxs-lookup"><span data-stu-id="f024a-130">If a terminating error occurs while the statements in the statement list are being run, the script passes the error object from the `Try` block to an appropriate `Catch` block.</span></span>

<span data-ttu-id="f024a-131">Hieronder ziet u de `Catch` blok syntaxis:</span><span class="sxs-lookup"><span data-stu-id="f024a-131">The following shows the `Catch` block syntax:</span></span>

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

<span data-ttu-id="f024a-132">Fout typen worden tussen haakjes weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f024a-132">Error types appear in brackets.</span></span> <span data-ttu-id="f024a-133">De buitenste haken geven aan dat het element optioneel is.</span><span class="sxs-lookup"><span data-stu-id="f024a-133">The outermost brackets indicate the element is optional.</span></span>

<span data-ttu-id="f024a-134">Het `Catch` sleutel woord wordt gevolgd door een optionele lijst met fout type specificaties en een instructie lijst.</span><span class="sxs-lookup"><span data-stu-id="f024a-134">The `Catch` keyword is followed by an optional list of error type specifications and a statement list.</span></span> <span data-ttu-id="f024a-135">Als er een afsluit fout optreedt in het `Try` blok, zoekt Power shell naar een geschikt `Catch` blok.</span><span class="sxs-lookup"><span data-stu-id="f024a-135">If a terminating error occurs in the `Try` block, PowerShell searches for an appropriate `Catch` block.</span></span> <span data-ttu-id="f024a-136">Als er een wordt gevonden, worden de instructies in het `Catch` blok uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f024a-136">If one is found, the statements in the `Catch` block are executed.</span></span>

<span data-ttu-id="f024a-137">In het `Catch` blok kunnen een of meer fout typen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f024a-137">The `Catch` block can specify one or more error types.</span></span> <span data-ttu-id="f024a-138">Een fout type is een Microsoft .NET Framework-uitzonde ring of een uitzonde ring die is afgeleid van een .NET Framework uitzonde ring.</span><span class="sxs-lookup"><span data-stu-id="f024a-138">An error type is a Microsoft .NET Framework exception or an exception that is derived from a .NET Framework exception.</span></span> <span data-ttu-id="f024a-139">Een `Catch` blok behandelt fouten van de opgegeven uitzonderings klasse .NET Framework of van een klasse die is afgeleid van de opgegeven klasse.</span><span class="sxs-lookup"><span data-stu-id="f024a-139">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span>

<span data-ttu-id="f024a-140">Als in een `Catch` blok een fout type wordt opgegeven, wordt het `Catch` type fout door dat blok afgehandeld.</span><span class="sxs-lookup"><span data-stu-id="f024a-140">If a `Catch` block specifies an error type, that `Catch` block handles that type of error.</span></span> <span data-ttu-id="f024a-141">Als `Catch` voor een blok geen fout type wordt opgegeven, wordt in dat blok een `Catch` fout verwerkt die in het blok is aangetroffen `Try` .</span><span class="sxs-lookup"><span data-stu-id="f024a-141">If a `Catch` block does not specify an error type, that `Catch` block handles any error encountered in the `Try` block.</span></span> <span data-ttu-id="f024a-142">Een `Try` instructie kan meerdere `Catch` blokken bevatten voor de verschillende opgegeven fout typen.</span><span class="sxs-lookup"><span data-stu-id="f024a-142">A `Try` statement can include multiple `Catch` blocks for the different specified error types.</span></span>

<span data-ttu-id="f024a-143">Hieronder ziet u de `Finally` blok syntaxis:</span><span class="sxs-lookup"><span data-stu-id="f024a-143">The following shows the `Finally` block syntax:</span></span>

```powershell
finally {<statement list>}
```

<span data-ttu-id="f024a-144">Het `Finally` sleutel woord wordt gevolgd door een lijst met overzichten die wordt uitgevoerd telkens wanneer het script wordt uitgevoerd, zelfs als de `Try` instructie zonder fouten is uitgevoerd of als er een fout is opgetreden in een `Catch` instructie.</span><span class="sxs-lookup"><span data-stu-id="f024a-144">The `Finally` keyword is followed by a statement list that runs every time the script is run, even if the `Try` statement ran without error or an error was caught in a `Catch` statement.</span></span>

<span data-ttu-id="f024a-145">Houd er rekening mee dat de pijp lijn wordt gestopt door op <kbd>CTRL</kbd> + <kbd>C</kbd> te drukken.</span><span class="sxs-lookup"><span data-stu-id="f024a-145">Note that pressing <kbd>CTRL</kbd>+<kbd>C</kbd> stops the pipeline.</span></span> <span data-ttu-id="f024a-146">Objecten die naar de pijp lijn worden verzonden, worden niet weer gegeven als uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f024a-146">Objects that are sent to the pipeline will not be displayed as output.</span></span> <span data-ttu-id="f024a-147">Als u dus een instructie opneemt die moet worden weer gegeven, zoals ' finally Block is run ', wordt deze niet weer gegeven nadat u op <kbd>CTRL</kbd> + <kbd>C</kbd>hebt gedrukt, zelfs als het `Finally` blok is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f024a-147">Therefore, if you include a statement to be displayed, such as "Finally block has run", it will not be displayed after you press <kbd>CTRL</kbd>+<kbd>C</kbd>, even if the `Finally` block ran.</span></span>

### <a name="catching-errors"></a><span data-ttu-id="f024a-148">OPVANGEN VAN FOUTEN</span><span class="sxs-lookup"><span data-stu-id="f024a-148">CATCHING ERRORS</span></span>

<span data-ttu-id="f024a-149">In het volgende voorbeeld script ziet u een `Try` blok met een `Catch` blok:</span><span class="sxs-lookup"><span data-stu-id="f024a-149">The following sample script shows a `Try` block with a `Catch` block:</span></span>

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

<span data-ttu-id="f024a-150">Het `Catch` tref woord moet direct volgen op het `Try` blok of een ander `Catch` blok.</span><span class="sxs-lookup"><span data-stu-id="f024a-150">The `Catch` keyword must immediately follow the `Try` block or another `Catch` block.</span></span>

<span data-ttu-id="f024a-151">Power shell herkent "NonsenseString" niet als cmdlet of ander item.</span><span class="sxs-lookup"><span data-stu-id="f024a-151">PowerShell does not recognize "NonsenseString" as a cmdlet or other item.</span></span>
<span data-ttu-id="f024a-152">Als u dit script uitvoert, wordt het volgende resultaat geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="f024a-152">Running this script returns the following result:</span></span>

```powershell
An error occurred.
```

<span data-ttu-id="f024a-153">Wanneer het script zich voordoet als ' NonsenseString ', treedt er een afsluit fout op.</span><span class="sxs-lookup"><span data-stu-id="f024a-153">When the script encounters "NonsenseString", it causes a terminating error.</span></span> <span data-ttu-id="f024a-154">De `Catch` blok kering van de fout wordt door de lijst met instructies in het blok uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f024a-154">The `Catch` block handles the error by running the statement list inside the block.</span></span>

### <a name="using-multiple-catch-statements"></a><span data-ttu-id="f024a-155">MEERDERE CATCH-INSTRUCTIES GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="f024a-155">USING MULTIPLE CATCH STATEMENTS</span></span>

<span data-ttu-id="f024a-156">Een `Try` instructie kan een wille keurig aantal `Catch` blokken bevatten.</span><span class="sxs-lookup"><span data-stu-id="f024a-156">A `Try` statement can have any number of `Catch` blocks.</span></span> <span data-ttu-id="f024a-157">Het volgende script heeft bijvoorbeeld een `Try` blok dat wordt gedownload `MyDoc.doc` en bevat twee `Catch` blokken:</span><span class="sxs-lookup"><span data-stu-id="f024a-157">For example, the following script has a `Try` block that downloads `MyDoc.doc`, and it contains two `Catch` blocks:</span></span>

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

<span data-ttu-id="f024a-158">Het eerste `Catch` blok behandelt fouten van het type **System .net. WebException** en **System. io. IOException** .</span><span class="sxs-lookup"><span data-stu-id="f024a-158">The first `Catch` block handles errors of the **System.Net.WebException** and **System.IO.IOException** types.</span></span> <span data-ttu-id="f024a-159">In het tweede `Catch` blok is geen fout type opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f024a-159">The second `Catch` block does not specify an error type.</span></span> <span data-ttu-id="f024a-160">Het tweede `Catch` blok verwerkt alle andere afsluit fouten die optreden.</span><span class="sxs-lookup"><span data-stu-id="f024a-160">The second `Catch` block handles any other terminating errors that occur.</span></span>

<span data-ttu-id="f024a-161">Power shell komt overeen met fout typen op overname.</span><span class="sxs-lookup"><span data-stu-id="f024a-161">PowerShell matches error types by inheritance.</span></span> <span data-ttu-id="f024a-162">Een `Catch` blok behandelt fouten van de opgegeven uitzonderings klasse .NET Framework of van een klasse die is afgeleid van de opgegeven klasse.</span><span class="sxs-lookup"><span data-stu-id="f024a-162">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span> <span data-ttu-id="f024a-163">Het volgende voor beeld bevat een `Catch` blok dat de fout ' opdracht niet gevonden ' onderschept:</span><span class="sxs-lookup"><span data-stu-id="f024a-163">The following example contains a `Catch` block that catches a "Command Not Found" error:</span></span>

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

<span data-ttu-id="f024a-164">Het opgegeven fout type **CommandNotFoundException** , neemt over van het type **System.SystemException** .</span><span class="sxs-lookup"><span data-stu-id="f024a-164">The specified error type, **CommandNotFoundException** , inherits from the **System.SystemException** type.</span></span> <span data-ttu-id="f024a-165">In het volgende voor beeld wordt ook een niet-gevonden opdracht onderschept:</span><span class="sxs-lookup"><span data-stu-id="f024a-165">The following example also catches a Command Not Found error:</span></span>

```powershell
catch [System.SystemException] {"Base Exception" }
```

<span data-ttu-id="f024a-166">Dit `Catch` blok verwerkt de fout ' opdracht niet gevonden ' en andere fouten die van het type **SystemException** overnemen.</span><span class="sxs-lookup"><span data-stu-id="f024a-166">This `Catch` block handles the "Command Not Found" error and other errors that inherit from the **SystemException** type.</span></span>

<span data-ttu-id="f024a-167">Als u een fout klasse en een van de afgeleide klassen opgeeft, plaatst u het `Catch` blok voor de afgeleide klasse vóór het `Catch` blok voor de algemene klasse.</span><span class="sxs-lookup"><span data-stu-id="f024a-167">If you specify an error class and one of its derived classes, place the `Catch` block for the derived class before the `Catch` block for the general class.</span></span>

### <a name="using-traps-in-a-try-catch"></a><span data-ttu-id="f024a-168">Traps gebruiken in een try-catch</span><span class="sxs-lookup"><span data-stu-id="f024a-168">Using Traps in a Try Catch</span></span>

<span data-ttu-id="f024a-169">Als er een afsluit fout optreedt in een `Try` blok met een `Trap` gedefinieerde binnen het `Try` blok, zelfs als er een overeenkomend `Catch` blok is, `Trap` neemt de instructie de controle.</span><span class="sxs-lookup"><span data-stu-id="f024a-169">When a terminating error occurs in a `Try` block with a `Trap` defined within the `Try` block, even if there is a matching `Catch` block, the `Trap` statement takes control.</span></span>

<span data-ttu-id="f024a-170">Als een `Trap` bestaat in een hoger blok dan het `Try` , en er is geen overeenkomend `Catch` blok binnen het huidige bereik, `Trap` wordt de controle uitgevoerd, zelfs als een bovenliggend bereik een overeenkomend `Catch` blok heeft.</span><span class="sxs-lookup"><span data-stu-id="f024a-170">If a `Trap` exists at a higher block than the `Try`, and there is no matching `Catch` block within the current scope, the `Trap` will take control, even if any parent scope has a matching `Catch` block.</span></span>

### <a name="accessing-exception-information"></a><span data-ttu-id="f024a-171">UITZONDERINGS INFORMATIE OPENEN</span><span class="sxs-lookup"><span data-stu-id="f024a-171">ACCESSING EXCEPTION INFORMATION</span></span>

<span data-ttu-id="f024a-172">Binnen een `Catch` blok kan de huidige fout worden geopend met `$_` , ook wel bekend als `$PSItem` .</span><span class="sxs-lookup"><span data-stu-id="f024a-172">Within a `Catch` block, the current error can be accessed using `$_`, which is also known as `$PSItem`.</span></span> <span data-ttu-id="f024a-173">Het object is van het type **ErrorRecord**.</span><span class="sxs-lookup"><span data-stu-id="f024a-173">The object is of type **ErrorRecord**.</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

<span data-ttu-id="f024a-174">Als u dit script uitvoert, wordt het volgende resultaat geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="f024a-174">Running this script returns the following result:</span></span>

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

<span data-ttu-id="f024a-175">Er zijn aanvullende eigenschappen die kunnen worden geopend, zoals **ScriptStackTrace** , **Exception** en **Error Details**.</span><span class="sxs-lookup"><span data-stu-id="f024a-175">There are additional properties that can be accessed, such as **ScriptStackTrace** , **Exception** , and **ErrorDetails**.</span></span>  <span data-ttu-id="f024a-176">Als we het script bijvoorbeeld wijzigen in het volgende:</span><span class="sxs-lookup"><span data-stu-id="f024a-176">For example, if we change the script to the following:</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

<span data-ttu-id="f024a-177">Het resultaat is vergelijkbaar met:</span><span class="sxs-lookup"><span data-stu-id="f024a-177">The result will be similar to:</span></span>

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a><span data-ttu-id="f024a-178">RESOURCES VRIJMAKEN DOOR TEN SLOTTE TE GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="f024a-178">FREEING RESOURCES BY USING FINALLY</span></span>

<span data-ttu-id="f024a-179">Als u resources wilt vrijmaken die door een script worden gebruikt, voegt u een `Finally` blok toe na de `Try` en- `Catch` blokken.</span><span class="sxs-lookup"><span data-stu-id="f024a-179">To free resources used by a script, add a `Finally` block after the `Try` and `Catch` blocks.</span></span> <span data-ttu-id="f024a-180">De `Finally` blok-instructies worden uitgevoerd, ongeacht of er `Try` een afsluit fout is opgetreden in het blok.</span><span class="sxs-lookup"><span data-stu-id="f024a-180">The `Finally` block statements run regardless of whether the `Try` block encounters a terminating error.</span></span> <span data-ttu-id="f024a-181">Power Shell voert het `Finally` blok uit voordat het script wordt beëindigd of voordat het huidige blok buiten het bereik valt.</span><span class="sxs-lookup"><span data-stu-id="f024a-181">PowerShell runs the `Finally` block before the script terminates or before the current block goes out of scope.</span></span>

<span data-ttu-id="f024a-182">Een `Finally` blok wordt zelfs uitgevoerd als u <kbd>CTRL</kbd> + <kbd>C</kbd> gebruikt om het script te stoppen.</span><span class="sxs-lookup"><span data-stu-id="f024a-182">A `Finally` block runs even if you use <kbd>CTRL</kbd>+<kbd>C</kbd> to stop the script.</span></span> <span data-ttu-id="f024a-183">Een `Finally` blok wordt ook uitgevoerd als het sleutel woord exit het script in een `Catch` blok stopt.</span><span class="sxs-lookup"><span data-stu-id="f024a-183">A `Finally` block also runs if an Exit keyword stops the script from within a `Catch` block.</span></span>

### <a name="see-also"></a><span data-ttu-id="f024a-184">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="f024a-184">SEE ALSO</span></span>

[<span data-ttu-id="f024a-185">about_Break</span><span class="sxs-lookup"><span data-stu-id="f024a-185">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="f024a-186">about_Continue</span><span class="sxs-lookup"><span data-stu-id="f024a-186">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="f024a-187">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="f024a-187">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="f024a-188">about_Throw</span><span class="sxs-lookup"><span data-stu-id="f024a-188">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="f024a-189">about_Trap</span><span class="sxs-lookup"><span data-stu-id="f024a-189">about_Trap</span></span>](about_Trap.md)
