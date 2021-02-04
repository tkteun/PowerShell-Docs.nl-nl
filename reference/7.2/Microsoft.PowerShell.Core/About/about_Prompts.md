---
description: Hierin wordt de `Prompt` functie beschreven en wordt gedemonstreerd hoe u een aangepaste `Prompt` functie maakt.
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: 3887df636c3ad486a4dbe72fffdc8acd92d2b3e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705332"
---
# <a name="about-prompts"></a><span data-ttu-id="1c2f9-103">Over prompts</span><span class="sxs-lookup"><span data-stu-id="1c2f9-103">About Prompts</span></span>

## <a name="short-description"></a><span data-ttu-id="1c2f9-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="1c2f9-104">Short description</span></span>
<span data-ttu-id="1c2f9-105">Hierin wordt de `Prompt` functie beschreven en wordt gedemonstreerd hoe u een aangepaste `Prompt` functie maakt.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-105">Describes the `Prompt` function and demonstrates how to create a custom `Prompt` function.</span></span>

## <a name="long-description"></a><span data-ttu-id="1c2f9-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="1c2f9-106">Long description</span></span>

<span data-ttu-id="1c2f9-107">De Power shell-opdracht prompt geeft aan dat Power shell gereed is om een opdracht uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-107">The PowerShell command prompt indicates that PowerShell is ready to run a command:</span></span>

```
PS C:\>
```

<span data-ttu-id="1c2f9-108">De Power shell-prompt wordt bepaald door de ingebouwde `Prompt` functie.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-108">The PowerShell prompt is determined by the built-in `Prompt` function.</span></span> <span data-ttu-id="1c2f9-109">U kunt de prompt aanpassen door uw eigen functie te maken `Prompt` en deze op te slaan in uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-109">You can customize the prompt by creating your own `Prompt` function and saving it in your PowerShell profile.</span></span>

## <a name="about-the-prompt-function"></a><span data-ttu-id="1c2f9-110">Over de functie vragen</span><span class="sxs-lookup"><span data-stu-id="1c2f9-110">About the Prompt function</span></span>

<span data-ttu-id="1c2f9-111">De `Prompt` functie bepaalt het uiterlijk van de Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-111">The `Prompt` function determines the appearance of the PowerShell prompt.</span></span>
<span data-ttu-id="1c2f9-112">Power shell wordt geleverd met een ingebouwde `Prompt` functie, maar u kunt deze vervangen door uw eigen functie te definiëren `Prompt` .</span><span class="sxs-lookup"><span data-stu-id="1c2f9-112">PowerShell comes with a built-in `Prompt` function, but you can override it by defining your own `Prompt` function.</span></span>

<span data-ttu-id="1c2f9-113">De `Prompt` functie heeft de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-113">The `Prompt` function has the following syntax:</span></span>

```powershell
function Prompt { <function-body> }
```

<span data-ttu-id="1c2f9-114">De `Prompt` functie moet een object retour neren.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-114">The `Prompt` function must return an object.</span></span> <span data-ttu-id="1c2f9-115">Als best practice retourneert een teken reeks of een object dat is opgemaakt als een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-115">As a best practice, return a string or an object that is formatted as a string.</span></span> <span data-ttu-id="1c2f9-116">De maximale aanbevolen lengte is 80 tekens.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-116">The maximum recommended length is 80 characters.</span></span>

<span data-ttu-id="1c2f9-117">De volgende `Prompt` functie retourneert bijvoorbeeld een teken reeks ' Hallo, wereld ', gevolgd door een punt haak rechts ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="1c2f9-117">For example, the following `Prompt` function returns a "Hello, World" string followed by a  right angle bracket (`>`).</span></span>

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a><span data-ttu-id="1c2f9-118">De functie voor vragen ophalen</span><span class="sxs-lookup"><span data-stu-id="1c2f9-118">Getting the Prompt function</span></span>

<span data-ttu-id="1c2f9-119">Als u de `Prompt` functie wilt ophalen, gebruikt u de `Get-Command` cmdlet of gebruikt u de `Get-Item` cmdlet in het functie station.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-119">To get the `Prompt` function, use the `Get-Command` cmdlet or use the `Get-Item` cmdlet in the Function drive.</span></span>

<span data-ttu-id="1c2f9-120">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-120">For example:</span></span>

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

<span data-ttu-id="1c2f9-121">Als u het script wilt ophalen waarmee de waarde van de prompt wordt ingesteld, gebruikt u de punt methode om de eigenschap **script Block** van de functie op te halen `Prompt` .</span><span class="sxs-lookup"><span data-stu-id="1c2f9-121">To get the script that sets the value of the prompt, use the dot method to get the **ScriptBlock** property of the `Prompt` function.</span></span>

<span data-ttu-id="1c2f9-122">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-122">For example:</span></span>

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

<span data-ttu-id="1c2f9-123">Net als alle functies `Prompt` wordt de functie in het `Function:` station opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-123">Like all functions, the `Prompt` function is stored in the `Function:` drive.</span></span>
<span data-ttu-id="1c2f9-124">Als u het script wilt weer geven waarmee de huidige functie wordt gemaakt `Prompt` , typt u:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-124">To display the script that creates the current `Prompt` function, type:</span></span>

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a><span data-ttu-id="1c2f9-125">De standaard prompt</span><span class="sxs-lookup"><span data-stu-id="1c2f9-125">The default prompt</span></span>

<span data-ttu-id="1c2f9-126">De standaard prompt wordt alleen weer gegeven als de `Prompt` functie een fout genereert of geen object retourneert.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-126">The default prompt appears only when the `Prompt` function generates an error or does not return an object.</span></span>

<span data-ttu-id="1c2f9-127">De standaard Power shell-prompt is:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-127">The default PowerShell prompt is:</span></span>

```
PS>
```

<span data-ttu-id="1c2f9-128">Met de volgende opdracht wordt bijvoorbeeld de `Prompt` functie ingesteld op `$null` , die ongeldig is.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-128">For example, the following command sets the `Prompt` function to `$null`, which is invalid.</span></span> <span data-ttu-id="1c2f9-129">Als gevolg hiervan wordt de standaard prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-129">As a result, the default prompt appears.</span></span>

```powershell
PS C:\> function prompt {$null}
PS>
```

<span data-ttu-id="1c2f9-130">Omdat Power shell wordt geleverd met een ingebouwde prompt, wordt de standaard prompt doorgaans niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-130">Because PowerShell comes with a built-in prompt, you usually do not see the default prompt.</span></span>

### <a name="built-in-prompt"></a><span data-ttu-id="1c2f9-131">Ingebouwde prompt</span><span class="sxs-lookup"><span data-stu-id="1c2f9-131">Built-in prompt</span></span>

<span data-ttu-id="1c2f9-132">Power shell bevat een ingebouwde `Prompt` functie.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-132">PowerShell includes a built-in `Prompt` function.</span></span>

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

<span data-ttu-id="1c2f9-133">De functie gebruikt de `Test-Path` cmdlet om te bepalen of de `$PSDebugContext` Automatische variabele is gevuld.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-133">The function uses the `Test-Path` cmdlet to determine whether the `$PSDebugContext` automatic variable is populated.</span></span> <span data-ttu-id="1c2f9-134">Als deze `$PSDebugContext` is ingevuld, bevindt u zich in de foutopsporingsmodus en `[DBG]:` wordt u als volgt aan de prompt toegevoegd:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-134">If `$PSDebugContext` is populated, you are in debugging mode, and `[DBG]:` is added to the prompt, as follows:</span></span>

```Output
[DBG]: PS C:\ps-test>
```

<span data-ttu-id="1c2f9-135">Als `$PSDebugContext` niet is ingevuld, wordt de functie toegevoegd `PS` aan de prompt.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-135">If `$PSDebugContext` is not populated, the function adds `PS` to the prompt.</span></span>
<span data-ttu-id="1c2f9-136">En de functie gebruikt de `Get-Location` cmdlet om de huidige locatie van de bestandssysteem Directory op te halen.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-136">And, the function uses the `Get-Location` cmdlet to get the current file system directory location.</span></span> <span data-ttu-id="1c2f9-137">Vervolgens wordt er een rechte haak () toegevoegd `>` .</span><span class="sxs-lookup"><span data-stu-id="1c2f9-137">Then, it adds a right angle bracket (`>`).</span></span>

<span data-ttu-id="1c2f9-138">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-138">For example:</span></span>

```Output
PS C:\ps-test>
```

<span data-ttu-id="1c2f9-139">Als u zich in een geneste prompt bevindt, voegt de functie twee punt haken ( `>>` ) toe aan de prompt.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-139">If you are in a nested prompt, the function adds two angle brackets (`>>`) to the prompt.</span></span> <span data-ttu-id="1c2f9-140">(U bevindt zich in een geneste prompt als de waarde van de `$NestedPromptLevel` Automatische variabele groter is dan 1.)</span><span class="sxs-lookup"><span data-stu-id="1c2f9-140">(You are in a nested prompt if the value of the `$NestedPromptLevel` automatic variable is greater than 1.)</span></span>

<span data-ttu-id="1c2f9-141">Wanneer u bijvoorbeeld fouten opspoort in een geneste prompt, ziet u het volgende bericht:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-141">For example, when you are debugging in a nested prompt, the prompt resembles the following prompt:</span></span>

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a><span data-ttu-id="1c2f9-142">Wijzigingen in de prompt</span><span class="sxs-lookup"><span data-stu-id="1c2f9-142">Changes to the prompt</span></span>

<span data-ttu-id="1c2f9-143">De `Enter-PSSession` cmdlet voegt de naam van de externe computer toe aan de huidige `Prompt` functie.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-143">The `Enter-PSSession` cmdlet prepends the name of the remote computer to the current `Prompt` function.</span></span> <span data-ttu-id="1c2f9-144">Wanneer u de `Enter-PSSession` cmdlet gebruikt om een sessie met een externe computer te starten, wordt de opdracht prompt gewijzigd in de naam van de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-144">When you use the `Enter-PSSession` cmdlet to start a session with a remote computer, the command prompt changes to include the name of the remote computer.</span></span> <span data-ttu-id="1c2f9-145">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-145">For example:</span></span>

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

<span data-ttu-id="1c2f9-146">Andere Power shell-hosttoepassingen en alternatieve shells hebben mogelijk hun eigen opdracht prompts.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-146">Other PowerShell host applications and alternate shells might have their own custom command prompts.</span></span>

<span data-ttu-id="1c2f9-147">Zie about_Automatic_Variables voor meer informatie over de `$PSDebugContext` en `$NestedPromptLevel` automatische variabelen [](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="1c2f9-147">For more information about the `$PSDebugContext` and `$NestedPromptLevel` automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

### <a name="how-to-customize-the-prompt"></a><span data-ttu-id="1c2f9-148">De prompt aanpassen</span><span class="sxs-lookup"><span data-stu-id="1c2f9-148">How to customize the prompt</span></span>

<span data-ttu-id="1c2f9-149">Als u de prompt wilt aanpassen, schrijft u een nieuwe `Prompt` functie.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-149">To customize the prompt, write a new `Prompt` function.</span></span> <span data-ttu-id="1c2f9-150">De functie is niet beveiligd, dus u kunt deze overschrijven.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-150">The function is not protected, so you can overwrite it.</span></span>

<span data-ttu-id="1c2f9-151">Als u een `Prompt` functie wilt schrijven, typt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-151">To write a `Prompt` function, type the following:</span></span>

```powershell
function prompt { }
```

<span data-ttu-id="1c2f9-152">Voer vervolgens tussen de accolades de opdrachten in of de teken reeks waarmee u wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-152">Then, between the braces, enter the commands or the string that creates your prompt.</span></span>

<span data-ttu-id="1c2f9-153">De volgende prompt bevat bijvoorbeeld de naam van uw computer:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-153">For example, the following prompt includes your computer name:</span></span>

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

<span data-ttu-id="1c2f9-154">Op de Server01-computer ziet u het volgende bericht:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-154">On the Server01 computer, the prompt resembles the following prompt:</span></span>

```Output
PS [Server01] >
```

<span data-ttu-id="1c2f9-155">De volgende `Prompt` functie bevat de huidige datum en tijd:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-155">The following `Prompt` function includes the current date and time:</span></span>

```powershell
function prompt {"$(Get-Date)> "}
```

<span data-ttu-id="1c2f9-156">De prompt ziet er ongeveer als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-156">The prompt resembles the following prompt:</span></span>

```Output
03/15/2012 17:49:47>
```

<span data-ttu-id="1c2f9-157">U kunt ook de standaard `Prompt` functie wijzigen:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-157">You can also change the default `Prompt` function:</span></span>

<span data-ttu-id="1c2f9-158">De volgende gewijzigde `Prompt` functie voegt bijvoorbeeld `[ADMIN]:` toe aan de ingebouwde Power shell-prompt wanneer Power shell wordt geopend met de optie **als administrator uitvoeren** :</span><span class="sxs-lookup"><span data-stu-id="1c2f9-158">For example, the following modified `Prompt` function adds `[ADMIN]:` to the built-in PowerShell prompt when PowerShell is opened by using the **Run as administrator** option:</span></span>

```powershell
function prompt {
  $identity = [Security.Principal.WindowsIdentity]::GetCurrent()
  $principal = [Security.Principal.WindowsPrincipal] $identity
  $adminRole = [Security.Principal.WindowsBuiltInRole]::Administrator

  $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
    elseif($principal.IsInRole($adminRole)) { "[ADMIN]: " }
    else { '' }
  ) + 'PS ' + $(Get-Location) +
    $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

<span data-ttu-id="1c2f9-159">Wanneer u Power shell start met behulp van de optie **als administrator uitvoeren** , wordt een prompt weer gegeven die er ongeveer als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="1c2f9-159">When you start PowerShell by using the **Run as administrator** option, a prompt that resembles the following prompt appears:</span></span>

```Output
[ADMIN]: PS C:\ps-test>
```

<span data-ttu-id="1c2f9-160">Met de volgende `Prompt` functie wordt de geschiedenis-id van de volgende opdracht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-160">The following `Prompt` function displays the history ID of the next command.</span></span> <span data-ttu-id="1c2f9-161">Als u de opdracht geschiedenis wilt weer geven, gebruikt u de- `Get-History` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-161">To view the command history, use the `Get-History` cmdlet.</span></span>

```powershell
function prompt {
   # The at sign creates an array in case only one history item exists.
   $history = @(Get-History)
   if($history.Count -gt 0)
   {
      $lastItem = $history[$history.Count - 1]
      $lastId = $lastItem.Id
   }

   $nextCommand = $lastId + 1
   $currentDirectory = Get-Location
   "PS: $nextCommand $currentDirectory >"
}
```

<span data-ttu-id="1c2f9-162">In de volgende prompt worden de- `Write-Host` en- `Get-Random` cmdlets gebruikt om een prompt te maken die wille keurige kleur wijzigt.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-162">The following prompt uses the `Write-Host` and `Get-Random` cmdlets to create a prompt that changes color randomly.</span></span> <span data-ttu-id="1c2f9-163">Omdat `Write-Host` Er wordt geschreven naar de huidige hosttoepassing, maar geen object retourneert, bevat deze functie een `Return` instructie.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-163">Because `Write-Host` writes to the current host application but does not return an object, this function includes a `Return` statement.</span></span> <span data-ttu-id="1c2f9-164">Zonder IT maakt Power shell gebruik van de standaard prompt `PS>` .</span><span class="sxs-lookup"><span data-stu-id="1c2f9-164">Without it, PowerShell uses the default prompt, `PS>`.</span></span>

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a><span data-ttu-id="1c2f9-165">De functie vragen opslaan</span><span class="sxs-lookup"><span data-stu-id="1c2f9-165">Saving the Prompt function</span></span>

<span data-ttu-id="1c2f9-166">Net als elke functie `Prompt` bestaat de functie alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-166">Like any function, the `Prompt` function exists only in the current session.</span></span> <span data-ttu-id="1c2f9-167">Als u de `Prompt` functie voor toekomstige sessies wilt opslaan, voegt u deze toe aan uw Power shell-profielen.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-167">To save the `Prompt` function for future sessions, add it to your PowerShell profiles.</span></span> <span data-ttu-id="1c2f9-168">Zie [about_Profiles](about_Profiles.md)voor meer informatie over profielen.</span><span class="sxs-lookup"><span data-stu-id="1c2f9-168">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c2f9-169">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1c2f9-169">See also</span></span>

[<span data-ttu-id="1c2f9-170">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="1c2f9-170">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)

[<span data-ttu-id="1c2f9-171">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="1c2f9-171">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="1c2f9-172">Get-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="1c2f9-172">Get-History</span></span>](xref:Microsoft.PowerShell.Core.Get-History)

[<span data-ttu-id="1c2f9-173">Ophalen-wille keurig</span><span class="sxs-lookup"><span data-stu-id="1c2f9-173">Get-Random</span></span>](xref:Microsoft.PowerShell.Utility.Get-Random)

[<span data-ttu-id="1c2f9-174">Write-host</span><span class="sxs-lookup"><span data-stu-id="1c2f9-174">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)

[<span data-ttu-id="1c2f9-175">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="1c2f9-175">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="1c2f9-176">about_Functions</span><span class="sxs-lookup"><span data-stu-id="1c2f9-176">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="1c2f9-177">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="1c2f9-177">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="1c2f9-178">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="1c2f9-178">about_Debuggers</span></span>](about_Debuggers.md)

[<span data-ttu-id="1c2f9-179">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="1c2f9-179">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
