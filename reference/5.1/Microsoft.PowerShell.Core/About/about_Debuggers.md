---
description: Hierin wordt het Power Shell-fout opsporingsprogramma beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: d3353a9c684091b17f496e15f1553c860d26e973
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252814"
---
# <a name="about-debuggers"></a><span data-ttu-id="64009-104">Over fout opsporing</span><span class="sxs-lookup"><span data-stu-id="64009-104">About Debuggers</span></span>

## <a name="short-description"></a><span data-ttu-id="64009-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="64009-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="64009-106">Hierin wordt het Power Shell-fout opsporingsprogramma beschreven.</span><span class="sxs-lookup"><span data-stu-id="64009-106">Describes the PowerShell debugger.</span></span>

## <a name="long-description"></a><span data-ttu-id="64009-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="64009-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="64009-108">Fout opsporing is het proces van het onderzoeken van een script terwijl het wordt uitgevoerd om fouten in de script instructies te identificeren en te corrigeren.</span><span class="sxs-lookup"><span data-stu-id="64009-108">Debugging is the process of examining a script while it is running to identify and correct errors in the script instructions.</span></span> <span data-ttu-id="64009-109">De Power Shell-fout opsporing kan u helpen bij het onderzoeken en identificeren van fouten en inefficiëntie in uw scripts, functies, opdrachten, Power shell-werk stromen, configuratie van desired state Configuration (DSC) of expressies.</span><span class="sxs-lookup"><span data-stu-id="64009-109">The PowerShell debugger can help you examine and identify errors and inefficiencies in your scripts, functions, commands, PowerShell workflows, PowerShell Desired State Configuration (DSC) configurations, or expressions.</span></span>

<span data-ttu-id="64009-110">Vanaf Power shell 5,0 is het Power Shell-fout opsporingsprogramma bijgewerkt voor het opsporen van fouten in scripts, functies, werk stromen, opdrachten, configuraties of expressies die worden uitgevoerd in de-console of Windows PowerShell ISE op externe computers.</span><span class="sxs-lookup"><span data-stu-id="64009-110">Starting in PowerShell 5.0, the PowerShell debugger has been updated to debug scripts, functions, workflows, commands, configurations, or expressions that are running in either the console or Windows PowerShell ISE on remote computers.</span></span> <span data-ttu-id="64009-111">U kunt uitvoeren `Enter-PSSession` om een interactieve externe Power shell-sessie te starten waarin u onderbrekings punten en script bestanden en opdrachten voor fout opsporing op de externe computer kunt instellen.</span><span class="sxs-lookup"><span data-stu-id="64009-111">You can run `Enter-PSSession` to start an interactive remote PowerShell session in which you can set breakpoints and debug script files and commands on the remote computer.</span></span> <span data-ttu-id="64009-112">`Enter-PSSession` de functionaliteit is bijgewerkt, waarmee u opnieuw verbinding kunt maken en een niet-verbonden sessie kunt invoeren waarop een script of opdracht op een externe computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="64009-112">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running a script or command on a remote computer.</span></span> <span data-ttu-id="64009-113">Als het script dat wordt uitgevoerd een onderbrekings punt bereikt, wordt het fout opsporingsprogramma automatisch gestart door uw client sessie.</span><span class="sxs-lookup"><span data-stu-id="64009-113">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span> <span data-ttu-id="64009-114">Als de niet-verbonden sessie met een script al een onderbrekings punt heeft bereikt en op het onderbrekings punt wordt gestopt, `Enter-PSSession` wordt het opdracht regel programma voor fout opsporing automatisch gestart nadat u opnieuw verbinding hebt gemaakt met de sessie.</span><span class="sxs-lookup"><span data-stu-id="64009-114">If the disconnected session that is running a script has already hit a breakpoint, and is stopped at the breakpoint, `Enter-PSSession` automatically starts the command-line debugger, after you reconnect to the session.</span></span>

<span data-ttu-id="64009-115">De Power Shell-fout opsporing kan ook worden gebruikt voor het opsporen van fouten in Power shell-werk stromen, in de Power shell-console of in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="64009-115">The PowerShell debugger can also be used to debug PowerShell workflows, in either the PowerShell console, or in Windows PowerShell ISE.</span></span> <span data-ttu-id="64009-116">Vanaf Power shell 5,0 kunt u fouten opsporen in actieve taken of processen, hetzij lokaal of extern.</span><span class="sxs-lookup"><span data-stu-id="64009-116">Starting in PowerShell 5.0, you can debug within running jobs or processes, either locally or remotely.</span></span>

<span data-ttu-id="64009-117">U kunt de functies van de Power Shell-fout opsporing gebruiken om een Power shell-script,-functie,-opdracht,-werk stroom of-expressie te onderzoeken terwijl deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="64009-117">You can use the features of the PowerShell debugger to examine a PowerShell script, function, command, workflow, or expression while it is running.</span></span> <span data-ttu-id="64009-118">Het Power Shell-fout opsporingsprogramma bevat een set cmdlets waarmee u onderbrekings punten kunt instellen, onderbrekings punten kunt beheren en de aanroep stack weer geven.</span><span class="sxs-lookup"><span data-stu-id="64009-118">The PowerShell debugger includes a set of cmdlets that let you set breakpoints, manage breakpoints, and view the call stack.</span></span>

## <a name="debugger-cmdlets"></a><span data-ttu-id="64009-119">Cmdlets voor fout opsporing</span><span class="sxs-lookup"><span data-stu-id="64009-119">Debugger Cmdlets</span></span>

<span data-ttu-id="64009-120">Het Power Shell-fout opsporingsprogramma bevat de volgende set cmdlets:</span><span class="sxs-lookup"><span data-stu-id="64009-120">The PowerShell debugger includes the following set of cmdlets:</span></span>

- <span data-ttu-id="64009-121">`Set-PSBreakpoint`: Hiermee stelt u onderbrekings punten in voor lijnen, variabelen en opdrachten.</span><span class="sxs-lookup"><span data-stu-id="64009-121">`Set-PSBreakpoint`: Sets breakpoints on lines, variables, and commands.</span></span>
- <span data-ttu-id="64009-122">`Get-PSBreakpoint`: Hiermee worden onderbrekings punten in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="64009-122">`Get-PSBreakpoint`: Gets breakpoints in the current session.</span></span>
- <span data-ttu-id="64009-123">`Disable-PSBreakpoint`: Schakelt onderbrekings punten in de huidige sessie uit.</span><span class="sxs-lookup"><span data-stu-id="64009-123">`Disable-PSBreakpoint`: Turns off breakpoints in the current session.</span></span>
- <span data-ttu-id="64009-124">`Enable-PSBreakpoint`: Hiermee schakelt u onderbrekings punten in de huidige sessie opnieuw in.</span><span class="sxs-lookup"><span data-stu-id="64009-124">`Enable-PSBreakpoint`: Re-enables breakpoints in the current session.</span></span>
- <span data-ttu-id="64009-125">`Remove-PSBreakpoint`: Verwijdert onderbrekings punten uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="64009-125">`Remove-PSBreakpoint`: Deletes breakpoints from the current session.</span></span>
- <span data-ttu-id="64009-126">`Get-PSCallStack`: Hiermee wordt de huidige aanroep stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="64009-126">`Get-PSCallStack`: Displays the current call stack.</span></span>

## <a name="starting-and-stopping-the-debugger"></a><span data-ttu-id="64009-127">Fout opsporing starten en stoppen</span><span class="sxs-lookup"><span data-stu-id="64009-127">Starting and Stopping the Debugger</span></span>

<span data-ttu-id="64009-128">Stel een of meer onderbrekings punten in om de fout opsporing te starten.</span><span class="sxs-lookup"><span data-stu-id="64009-128">To start the debugger, set one or more breakpoints.</span></span> <span data-ttu-id="64009-129">Voer vervolgens het script, de opdracht of de functie uit die u wilt fouten opsporen.</span><span class="sxs-lookup"><span data-stu-id="64009-129">Then, run the script, command, or function that you want to debug.</span></span>

<span data-ttu-id="64009-130">Wanneer u een onderbrekings punt bereikt, wordt de uitvoering gestopt en wordt het besturings element overgezet naar het fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="64009-130">When you reach a breakpoint, execution stops, and control is turned over to the debugger.</span></span>

<span data-ttu-id="64009-131">Als u het fout opsporingsprogramma wilt stoppen, voert u het script, de opdracht of de functie uit totdat dit is voltooid.</span><span class="sxs-lookup"><span data-stu-id="64009-131">To stop the debugger, run the script, command, or function until it is complete.</span></span> <span data-ttu-id="64009-132">Of typ `stop` of `t` .</span><span class="sxs-lookup"><span data-stu-id="64009-132">Or, type `stop` or `t`.</span></span>

### <a name="debugger-commands"></a><span data-ttu-id="64009-133">Opdrachten voor fout opsporing</span><span class="sxs-lookup"><span data-stu-id="64009-133">Debugger Commands</span></span>

<span data-ttu-id="64009-134">Wanneer u het fout opsporingsprogramma gebruikt in de Power shell-console, gebruikt u de volgende opdrachten om de uitvoering te beheren.</span><span class="sxs-lookup"><span data-stu-id="64009-134">When you use the debugger in the PowerShell console, use the following commands to control the execution.</span></span> <span data-ttu-id="64009-135">In Windows PowerShell ISE gebruikt u opdrachten in het menu fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="64009-135">In Windows PowerShell ISE, use commands on the Debug menu.</span></span>

<span data-ttu-id="64009-136">Opmerking: voor meer informatie over het gebruik van het fout opsporingsprogramma in andere hosttoepassingen, raadpleegt u de documentatie van de hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="64009-136">Note: For information about how to use the debugger in other host applications, see the host application documentation.</span></span>

- <span data-ttu-id="64009-137">`s`, `StepInto` : Voert de volgende instructie uit en stopt vervolgens.</span><span class="sxs-lookup"><span data-stu-id="64009-137">`s`, `StepInto`: Executes the next statement and then stops.</span></span>

- <span data-ttu-id="64009-138">`v`, `StepOver` : Voert de volgende instructie uit, maar slaat functies en aanroepen over.</span><span class="sxs-lookup"><span data-stu-id="64009-138">`v`, `StepOver`: Executes the next statement, but skips functions and invocations.</span></span> <span data-ttu-id="64009-139">De overgeslagen instructies worden uitgevoerd, maar niet getrapt via.</span><span class="sxs-lookup"><span data-stu-id="64009-139">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="64009-140">`Ctrl+Break`: (Alles onderbreken in ISE) is in een actief script in de Power shell-console of Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="64009-140">`Ctrl+Break`: (Break All in ISE) Breaks into a running script within either the PowerShell console, or Windows PowerShell ISE.</span></span> <span data-ttu-id="64009-141">Houd er rekening mee dat <kbd>CTRL</kbd> + -<kbd>afbreek</kbd> in Windows Power Shell 2,0, 3,0 en 4,0 het programma sluit.</span><span class="sxs-lookup"><span data-stu-id="64009-141">Note that <kbd>Ctrl</kbd>+<kbd>Break</kbd> in Windows PowerShell 2.0, 3.0, and 4.0 closes the program.</span></span> <span data-ttu-id="64009-142">Alles onderbreken werkt op zowel lokale als externe interactief uitgevoerde scripts.</span><span class="sxs-lookup"><span data-stu-id="64009-142">Break All works on both local and remote interactively-running scripts.</span></span>

- <span data-ttu-id="64009-143">`o`, `StepOut` : Stappen van de huidige functie; Eén niveau omhoog als genest.</span><span class="sxs-lookup"><span data-stu-id="64009-143">`o`, `StepOut`: Steps out of the current function; up one level if nested.</span></span> <span data-ttu-id="64009-144">In de hoofd tekst wordt het einde of het volgende onderbrekings punt voortgezet.</span><span class="sxs-lookup"><span data-stu-id="64009-144">If in the main body, it continues to the end or the next breakpoint.</span></span> <span data-ttu-id="64009-145">De overgeslagen instructies worden uitgevoerd, maar niet getrapt via.</span><span class="sxs-lookup"><span data-stu-id="64009-145">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="64009-146">`c`, `Continue` : Blijft actief totdat het script is voltooid of totdat het volgende onderbrekings punt is bereikt.</span><span class="sxs-lookup"><span data-stu-id="64009-146">`c`, `Continue`: Continues to run until the script is complete or until the next breakpoint is reached.</span></span> <span data-ttu-id="64009-147">De overgeslagen instructies worden uitgevoerd, maar niet getrapt via.</span><span class="sxs-lookup"><span data-stu-id="64009-147">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="64009-148">`l`, `List` : Geeft het deel van het script weer dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="64009-148">`l`, `List`: Displays the part of the script that is executing.</span></span> <span data-ttu-id="64009-149">Standaard worden de huidige regel, vijf vorige regels en tien volgende regels weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="64009-149">By default, it displays the current line, five previous lines, and 10 subsequent lines.</span></span>
  <span data-ttu-id="64009-150">Als u het script wilt blijven aanbieden, drukt u op ENTER.</span><span class="sxs-lookup"><span data-stu-id="64009-150">To continue listing the script, press ENTER.</span></span>

- <span data-ttu-id="64009-151">`l <m>`, `List` : Hiermee worden 16 regels van het script weer gegeven, te beginnen met het regel nummer dat is opgegeven door `<m>` .</span><span class="sxs-lookup"><span data-stu-id="64009-151">`l <m>`, `List`: Displays 16 lines of the script beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="64009-152">`l <m> <n>`, `List` : Hiermee worden de `<n>` regels van het script weer gegeven, te beginnen met het regel nummer dat is opgegeven door `<m>` .</span><span class="sxs-lookup"><span data-stu-id="64009-152">`l <m> <n>`, `List`: Displays `<n>` lines of the script, beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="64009-153">`q`, `Stop` , `Exit` : Stopt met het uitvoeren van het script en sluit het fout opsporingsprogramma af.</span><span class="sxs-lookup"><span data-stu-id="64009-153">`q`, `Stop`, `Exit`: Stops executing the script, and exits the debugger.</span></span> <span data-ttu-id="64009-154">Als u fouten opspoort in een taak door de cmdlet uit te voeren `Debug-Job` , wordt `Exit` het fout opsporingsprogramma door de opdracht losgekoppeld en kan de taak blijven worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="64009-154">If you are debugging a job by running the `Debug-Job` cmdlet, the `Exit` command detaches the debugger, and allows the job to continue running.</span></span>

- <span data-ttu-id="64009-155">`k`, `Get-PsCallStack` : Hiermee wordt de huidige aanroep stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="64009-155">`k`, `Get-PsCallStack`: Displays the current call stack.</span></span>

- <span data-ttu-id="64009-156">`<Enter>`: Herhaalt de laatste opdracht als de stap (s), StepOver (v) of lijst (l).</span><span class="sxs-lookup"><span data-stu-id="64009-156">`<Enter>`: Repeats the last command if it was Step (s), StepOver (v), or List (l).</span></span> <span data-ttu-id="64009-157">Anders vertegenwoordigt een indienings actie.</span><span class="sxs-lookup"><span data-stu-id="64009-157">Otherwise, represents a submit action.</span></span>

- <span data-ttu-id="64009-158">`?`, `h` : Geeft de Help voor de opdracht fout opsporing weer.</span><span class="sxs-lookup"><span data-stu-id="64009-158">`?`, `h`: Displays the debugger command Help.</span></span>

<span data-ttu-id="64009-159">Als u het fout opsporingsprogramma wilt afsluiten, kunt u stoppen (q) gebruiken.</span><span class="sxs-lookup"><span data-stu-id="64009-159">To exit the debugger, you can use Stop (q).</span></span>

<span data-ttu-id="64009-160">Vanaf Power shell 5,0 kunt u de opdracht exit uitvoeren om een geneste foutopsporingssessie te afsluiten die u hebt gestart door ofwel of uit te voeren `Debug-Job` `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="64009-160">Starting in PowerShell 5.0, you can run the Exit command to exit a nested debugging session that you started by running either `Debug-Job` or `Debug-Runspace`.</span></span>

<span data-ttu-id="64009-161">Met behulp van deze opdrachten voor fout opsporing kunt u een script uitvoeren, stoppen op een bepaald punt, de waarden van variabelen en de status van het systeem controleren en door gaan met het uitvoeren van het script totdat u een probleem hebt vastgesteld.</span><span class="sxs-lookup"><span data-stu-id="64009-161">By using these debugger commands, you can run a script, stop on a point of concern, examine the values of variables and the state of the system, and continue running the script until you have identified a problem.</span></span>

<span data-ttu-id="64009-162">Opmerking: als u een instructie Step Into met een omleidings operator, zoals ' > ', worden de Power Shell-fout opsporings stappen voor alle resterende instructies in het script.</span><span class="sxs-lookup"><span data-stu-id="64009-162">NOTE: If you step into a statement with a redirection operator, such as ">", the PowerShell debugger steps over all remaining statements in the script.</span></span>

<span data-ttu-id="64009-163">De waarden van script variabelen weer geven</span><span class="sxs-lookup"><span data-stu-id="64009-163">Displaying the Values of script Variables</span></span>

<span data-ttu-id="64009-164">Terwijl u zich in het fout opsporingsprogramma bevindt, kunt u ook opdrachten invoeren, de waarde van variabelen weer geven, cmdlets gebruiken en scripts uitvoeren op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="64009-164">While you are in the debugger, you can also enter commands, display the value of variables, use cmdlets, and run scripts at the command line.</span></span>

<span data-ttu-id="64009-165">U kunt de huidige waarde van alle variabelen weer geven in het script waarvoor fout opsporing wordt uitgevoerd, met uitzonde ring van de volgende automatische variabelen:</span><span class="sxs-lookup"><span data-stu-id="64009-165">You can display the current value of all variables in the script that is being debugged, except for the following automatic variables:</span></span>

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

<span data-ttu-id="64009-166">Als u probeert de waarde van een van deze variabelen weer te geven, krijgt u de waarde van die variabele voor in een interne pijp lijn die wordt gebruikt door het fout opsporingsprogramma, niet de waarde van de variabele in het script.</span><span class="sxs-lookup"><span data-stu-id="64009-166">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span>

<span data-ttu-id="64009-167">Als u de waarde van deze variabelen wilt weer geven voor het script dat wordt opgespoord, wijst u in het script de waarde van de automatische variabele toe aan een nieuwe variabele.</span><span class="sxs-lookup"><span data-stu-id="64009-167">To display the value these variables for the script that is being debugged, in the script, assign the value of the automatic variable to a new variable.</span></span> <span data-ttu-id="64009-168">Vervolgens kunt u de waarde van de nieuwe variabele weer geven.</span><span class="sxs-lookup"><span data-stu-id="64009-168">Then you can display the value of the new variable.</span></span>

<span data-ttu-id="64009-169">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="64009-169">For example,</span></span>

```powershell
$scriptArgs = $Args
$scriptArgs
```

<span data-ttu-id="64009-170">In het voor beeld in dit onderwerp wordt de waarde van de `$MyInvocation` variabele als volgt opnieuw toegewezen:</span><span class="sxs-lookup"><span data-stu-id="64009-170">In the example in this topic, the value of the `$MyInvocation` variable is reassigned as follows:</span></span>

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a><span data-ttu-id="64009-171">De debugger omgeving</span><span class="sxs-lookup"><span data-stu-id="64009-171">The Debugger Environment</span></span>

<span data-ttu-id="64009-172">Wanneer u een onderbrekings punt bereikt, voert u de omgeving voor fout opsporing in.</span><span class="sxs-lookup"><span data-stu-id="64009-172">When you reach a breakpoint, you enter the debugger environment.</span></span> <span data-ttu-id="64009-173">De opdracht prompt wordt gewijzigd zodat deze begint met "[DBG]:".</span><span class="sxs-lookup"><span data-stu-id="64009-173">The command prompt changes so that it begins with "[DBG]:".</span></span> <span data-ttu-id="64009-174">Als u fouten opspoort voor een werk stroom, is de prompt ' [WFDBG] '.</span><span class="sxs-lookup"><span data-stu-id="64009-174">If you are debugging a workflow, the prompt is "[WFDBG]".</span></span> <span data-ttu-id="64009-175">U kunt de prompt aanpassen.</span><span class="sxs-lookup"><span data-stu-id="64009-175">You can customize the prompt.</span></span>

<span data-ttu-id="64009-176">Zie [about_Prompts](about_prompts.md)voor meer informatie over het aanpassen van de prompt.</span><span class="sxs-lookup"><span data-stu-id="64009-176">For more information about customizing the prompt, see [about_Prompts](about_prompts.md).</span></span>

<span data-ttu-id="64009-177">Daarnaast wordt in sommige hosttoepassingen, zoals de Power shell-console, (maar niet in Windows Power shell Integrated Scripting Environment [ISE]), een geneste prompt geopend voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="64009-177">Also, in some host applications, such as the PowerShell console, (but not in Windows PowerShell Integrated Scripting Environment [ISE]), a nested prompt opens for debugging.</span></span> <span data-ttu-id="64009-178">U kunt de geneste prompt detecteren door de herhaalde tekens die groter zijn dan (ASCII 62) die worden weer gegeven bij de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="64009-178">You can detect the nested prompt by the repeating greater-than characters (ASCII 62) that appear at the command prompt.</span></span>

<span data-ttu-id="64009-179">Het volgende is bijvoorbeeld de standaard prompt voor fout opsporing in de Power shell-console:</span><span class="sxs-lookup"><span data-stu-id="64009-179">For example, the following is the default debugging prompt in the PowerShell console:</span></span>

```
[DBG]: PS (get-location)>>>
```

<span data-ttu-id="64009-180">U kunt het nest niveau vinden met behulp van de `$NestedPromptLevel` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="64009-180">You can find the nesting level by using the `$NestedPromptLevel` automatic variable.</span></span>

<span data-ttu-id="64009-181">Daarnaast wordt een automatische variabele `$PSDebugContext` gedefinieerd in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="64009-181">Additionally, an automatic variable, `$PSDebugContext`, is defined in the local scope.</span></span> <span data-ttu-id="64009-182">U kunt de aanwezigheid van de `$PsDebugContext` variabele gebruiken om te bepalen of u zich in het fout opsporingsprogramma bevindt.</span><span class="sxs-lookup"><span data-stu-id="64009-182">You can use the presence of the `$PsDebugContext` variable to determine whether you are in the debugger.</span></span>

<span data-ttu-id="64009-183">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="64009-183">For example:</span></span>

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

<span data-ttu-id="64009-184">U kunt de waarde van de `$PSDebugContext` variabele in de fout opsporing gebruiken.</span><span class="sxs-lookup"><span data-stu-id="64009-184">You can use the value of the `$PSDebugContext` variable in your debugging.</span></span>

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a><span data-ttu-id="64009-185">Fout opsporing en bereik</span><span class="sxs-lookup"><span data-stu-id="64009-185">Debugging and Scope</span></span>

<span data-ttu-id="64009-186">Breuk in het fout opsporingsprogramma wijzigt niet het bereik waarin u werkt, maar wanneer u een onderbrekings punt in een script bereikt, gaat u naar het script bereik.</span><span class="sxs-lookup"><span data-stu-id="64009-186">Breaking into the debugger does not change the scope in which you are operating, but when you reach a breakpoint in a script, you move into the script scope.</span></span> <span data-ttu-id="64009-187">Het script bereik is een onderliggend item van het bereik waarin u het fout opsporingsprogramma hebt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="64009-187">The script scope is a child of the scope in which you ran the debugger.</span></span>

<span data-ttu-id="64009-188">Als u de variabelen en aliassen wilt vinden die in het script bereik zijn gedefinieerd, gebruikt u de para meter bereik van de `Get-Alias` `Get-Variable` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="64009-188">To find the variables and aliases that are defined in the script scope, use the Scope parameter of the `Get-Alias` or `Get-Variable` cmdlets.</span></span>

<span data-ttu-id="64009-189">Met de volgende opdracht worden bijvoorbeeld de variabelen in het lokale (script) bereik opgehaald:</span><span class="sxs-lookup"><span data-stu-id="64009-189">For example, the following command gets the variables in the local (script) scope:</span></span>

```powershell
Get-Variable -scope 0
```

<span data-ttu-id="64009-190">U kunt de opdracht als volgt afkorten:</span><span class="sxs-lookup"><span data-stu-id="64009-190">You can abbreviate the command as:</span></span>

```powershell
gv -s 0
```

<span data-ttu-id="64009-191">Dit is een handige manier om alleen de variabelen weer te geven die u in het script hebt gedefinieerd en die u tijdens het opsporen van fouten hebt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="64009-191">This is a useful way to see only the variables that you defined in the script and that you defined while debugging.</span></span>

<span data-ttu-id="64009-192">Fout opsporing op de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="64009-192">Debugging at the Command Line</span></span>

<span data-ttu-id="64009-193">Wanneer u een onderbrekings punt voor een variabele of een opdracht onderbrekings punt instelt, kunt u het onderbrekings punt alleen instellen in een script bestand.</span><span class="sxs-lookup"><span data-stu-id="64009-193">When you set a variable breakpoint or a command breakpoint, you can set the breakpoint only in a script file.</span></span> <span data-ttu-id="64009-194">Het onderbrekings punt wordt echter standaard ingesteld op alles dat wordt uitgevoerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="64009-194">However, by default, the breakpoint is set on anything that runs in the current session.</span></span>

<span data-ttu-id="64009-195">Als u bijvoorbeeld een onderbrekings punt instelt voor de `$name` variabele, wordt het fout opsporingsprogramma afgebroken op een wille keurige `$name` variabele in een script, opdracht, functie, script-cmdlet of expressie die u uitvoert totdat u het onderbrekings punt uitschakelt of verwijdert.</span><span class="sxs-lookup"><span data-stu-id="64009-195">For example, if you set a breakpoint on the `$name` variable, the debugger breaks on any `$name` variable in any script, command, function, script cmdlet or expression that you run until you disable or remove the breakpoint.</span></span>

<span data-ttu-id="64009-196">Zo kunt u fouten opsporen in uw scripts in een realistischere context waarin ze mogelijk worden beïnvloed door functies, variabelen en andere scripts in de sessie en in het profiel van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="64009-196">This allows you to debug your scripts in a more realistic context in which they might be affected by functions, variables, and other scripts in the session and in the user's profile.</span></span>

<span data-ttu-id="64009-197">Regel onderbrekingen zijn specifiek voor script bestanden, zodat ze alleen worden ingesteld in script bestanden.</span><span class="sxs-lookup"><span data-stu-id="64009-197">Line breakpoints are specific to script files, so they are set only in script files.</span></span>

## <a name="debugging-workflows"></a><span data-ttu-id="64009-198">Werk stromen voor fout opsporing</span><span class="sxs-lookup"><span data-stu-id="64009-198">Debugging Workflows</span></span>

<span data-ttu-id="64009-199">Het fout opsporingsprogramma Power Shell 4,0 kan worden gebruikt voor het opsporen van fouten in Power shell-werk stromen, hetzij in de Power shell-console, hetzij in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="64009-199">The PowerShell 4.0 debugger can be used to debug PowerShell workflows, either in the PowerShell console, or in Windows PowerShell ISE.</span></span> <span data-ttu-id="64009-200">Er zijn enkele beperkingen bij het gebruik van de Power Shell-fout opsporing voor het opsporen van werk stromen.</span><span class="sxs-lookup"><span data-stu-id="64009-200">There are some limitations with using the PowerShell debugger to debug workflows.</span></span>

- <span data-ttu-id="64009-201">U kunt werk stroom variabelen weer geven terwijl u zich in het fout opsporingsprogramma bevindt, maar het instellen van werk stroom variabelen vanuit het fout opsporingsprogramma wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="64009-201">You can view workflow variables while you are in the debugger, but setting workflow variables from within the debugger is not supported.</span></span>
- <span data-ttu-id="64009-202">Het volt ooien van het tabblad in het fout opsporingsprogramma voor de werk stroom is niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="64009-202">Tab completion when stopped in the workflow debugger is not available.</span></span>
- <span data-ttu-id="64009-203">Fout opsporing werk stroom werkt alleen met synchrone uitvoering van werk stromen vanuit een Power shell-script.</span><span class="sxs-lookup"><span data-stu-id="64009-203">Workflow debugging works only with synchronous running of workflows from a PowerShell script.</span></span> <span data-ttu-id="64009-204">U kunt geen werk stromen opsporen als deze worden uitgevoerd als een taak (met de para meter **AsJob** ).</span><span class="sxs-lookup"><span data-stu-id="64009-204">You cannot debug workflows if they are running as a job (with the **AsJob** parameter).</span></span>
- <span data-ttu-id="64009-205">Andere geneste scenario's voor fout opsporing, zoals een werk stroom die een andere werk stroom aanroept of een werk stroom die een script aanroept, worden niet geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="64009-205">Other nested debugging scenarios, such as a workflow calling another workflow or a workflow calling a script, are not implemented.</span></span>

<span data-ttu-id="64009-206">In het volgende voor beeld ziet u fout opsporing van een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="64009-206">The following example demonstrates debugging a workflow.</span></span> <span data-ttu-id="64009-207">Wanneer de fout opsporings stappen in de werk stroom functie worden uitgevoerd, wordt de debugger prompt gewijzigd in ' [WFDBG] '.</span><span class="sxs-lookup"><span data-stu-id="64009-207">When the debugger steps into the workflow function, the debugger prompt changes to "[WFDBG]".</span></span>

```powershell
PS C:> Set-PSBreakpoint -Script C:\TestWFDemo1.ps1 -Line 8

ID Script           Line Command    Variable     Action
-- ------           ---- -------    --------     ------
0 TestWFDemo1.ps1   8

PS C:> C:\TestWFDemo1.ps1
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\TestWFDemo1.ps1:8'

At C:\TestWFDemo1.ps1:8 char:5
+     Write-Output -InputObject "Now writing output:"
# +!INCLUDE[]~~~~~

[WFDBG:localhost]: PS C:>> list

# 3:

4:  workflow SampleWorkflowTest
5:  {
6:      param ($MyOutput)
# 7:

8:*     Write-Output -InputObject "Now writing output:"
9:      Write-Output -Input $MyOutput
# 10:

11:      Write-Output -InputObject "Get PowerShell process:"
12:      Get-Process -Name powershell
# 13:

14:      Write-Output -InputObject "Workflow function complete."
15:  }
# 16:

17:  # Call workflow function
18:  SampleWorkflowTest -MyOutput "Hello"

[WFDBG:localhost]: PS C:>> $MyOutput
Hello
[WFDBG:localhost]: PS C:>> stepOver
Now writing output:
At C:\TestWFDemo1.ps1:9 char:5
+     Write-Output -Input $MyOutput
# +!INCLUDE[]~

[WFDBG:localhost]: PS C:>> list

4:  workflow SampleWorkflowTest
5:  {
6:      param ($MyOutput)
# 7:

8:      Write-Output -InputObject "Now writing output:"
9:*     Write-Output -Input $MyOutput
# 10:

11:      Write-Output -InputObject "Get PowerShell process:"
12:      Get-Process -Name powershell
# 13:

14:      Write-Output -InputObject "Workflow function complete."
15:  }
# 16:

17:  # Call workflow function
18:  SampleWorkflowTest -MyOutput "Hello"
# 19:


[WFDBG:localhost]: PS C:>> stepOver
Hello
At C:\TestWFDemo1.ps1:11 char:5
+     Write-Output -InputObject "Get PowerShell process:"
# +!INCLUDE[]~~~~~~~~~

[WFDBG:localhost]: PS C:>> stepOut
Get PowerShell process:

Handles  NPM(K)    PM(K)    WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----    ----- -----   ------     -- -----------
    433      35   106688   128392   726     2.67   7124 powershell
    499      44   134244   172096   787     2.79   7452 powershell

Workflow function complete.
```

## <a name="debugging-functions"></a><span data-ttu-id="64009-208">Functies voor fout opsporing</span><span class="sxs-lookup"><span data-stu-id="64009-208">Debugging Functions</span></span>

<span data-ttu-id="64009-209">Wanneer u een onderbrekings punt instelt voor een functie die de volgende secties bevat, `Begin` `Process` wordt `End` het fout opsporingsprogramma afgebroken op de eerste regel van elke sectie.</span><span class="sxs-lookup"><span data-stu-id="64009-209">When you set a breakpoint on a function that has `Begin`, `Process`, and `End` sections, the debugger breaks at the first line of each section.</span></span>

<span data-ttu-id="64009-210">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="64009-210">For example:</span></span>

```powershell
function test-cmdlet {
    begin {
        write-output "Begin"
    }
    process {
        write-output "Process"
    }
    end {
        write-output "End"
    }
}

C:\PS> Set-PSBreakpoint -command test-cmdlet

C:\PS> test-cmdlet

Begin
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
Process
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
End
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

# [DBG]: C:\PS>
```

## <a name="debugging-remote-scripts"></a><span data-ttu-id="64009-211">Fout opsporing voor externe scripts</span><span class="sxs-lookup"><span data-stu-id="64009-211">Debugging Remote Scripts</span></span>

<span data-ttu-id="64009-212">Vanaf Power shell 5,0 kunt u de Power Shell-fout opsporing uitvoeren in een externe sessie, in de-console of in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="64009-212">Starting in PowerShell 5.0, you can run the PowerShell debugger in a remote session, in either the console, or Windows PowerShell ISE.</span></span>
<span data-ttu-id="64009-213">`Enter-PSSession` de functionaliteit is bijgewerkt, waarmee u opnieuw verbinding kunt maken en een niet-verbonden sessie kunt invoeren die wordt uitgevoerd op een externe computer en die op dit moment een script uitvoert.</span><span class="sxs-lookup"><span data-stu-id="64009-213">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running on a remote computer, and currently running a script.</span></span> <span data-ttu-id="64009-214">Als het script dat wordt uitgevoerd een onderbrekings punt bereikt, wordt het fout opsporingsprogramma automatisch gestart door uw client sessie.</span><span class="sxs-lookup"><span data-stu-id="64009-214">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span>

<span data-ttu-id="64009-215">Hier volgt een voor beeld van hoe dit werkt, waarbij onderbrekings punten in een script worden ingesteld op regels 6, 11, 22 en 25.</span><span class="sxs-lookup"><span data-stu-id="64009-215">The following is an example that shows how this works, with breakpoints set in a script at lines 6, 11, 22, and 25.</span></span> <span data-ttu-id="64009-216">In het voor beeld, wanneer het fout opsporingsprogramma wordt gestart, zijn er twee instructies: de naam van de computer waarop de sessie wordt uitgevoerd en de DBG-prompt waarin u kunt zien dat u zich in de foutopsporingsmodus bevindt.</span><span class="sxs-lookup"><span data-stu-id="64009-216">Note that in the example, when the debugger starts, there are two identifying prompts: the name of the computer on which the session is running, and the DBG prompt that lets you know you are in debugging mode.</span></span>

```powershell
Enter-Pssession -Cn localhost
[localhost]: PS C:\psscripts> Set-PSBreakpoint .\ttest19.ps1 6,11,22,25

ID Script          Line     Command          Variable          Action
-- ------          ----     -------          --------          ------
0 ttest19.ps1          6
1 ttest19.ps1          11
2 ttest19.ps1          22
3 ttest19.ps1          25

[localhost]: PS C:\psscripts> .\ttest19.ps1
Hit Line breakpoint on 'C:\psscripts\ttest19.ps1:11'

At C:\psscripts\ttest19.ps1:11 char:1
+ $winRMName = "WinRM"
# + ~

[localhost]: [DBG]: PS C:\psscripts>> list

6:      1..5 | foreach { sleep 1; Write-Output "hello2day $_" }
7:  }
# 8:

9:  $count = 10
10:  $psName = "PowerShell"
11:* $winRMName = "WinRM"
12:  $myVar = 102
# 13:

14:  for ($i=0; $i -lt $count; $i++)
15:  {
16:      sleep 1
17:      Write-Output "Loop iteration is: $i"
18:      Write-Output "MyVar is $myVar"
# 19:

20:      hello2day
# 21:


[localhost]: [DBG]: PS C:\psscripts>> stepover
At C:\psscripts\ttest19.ps1:12 char:1
+ $myVar = 102
# + ~

[localhost]: [DBG]: PS C:\psscripts>> quit
[localhost]: PS C:\psscripts> Exit-PSSession
PS C:\psscripts>
```

## <a name="examples"></a><span data-ttu-id="64009-217">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="64009-217">Examples</span></span>

<span data-ttu-id="64009-218">Met dit test script wordt de versie van het besturings systeem gedetecteerd en wordt er een systeem bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="64009-218">This test script detects the version of the operating system and displays a system-appropriate message.</span></span> <span data-ttu-id="64009-219">Het bevat een functie, een functie aanroep en een variabele.</span><span class="sxs-lookup"><span data-stu-id="64009-219">It includes a function, a function call, and a variable.</span></span>

<span data-ttu-id="64009-220">De volgende opdracht wordt de inhoud van het test script bestand weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="64009-220">The following command displays the contents of the test script file:</span></span>

```powershell
PS C:\PS-test>  Get-Content test.ps1

function psversion {
  "PowerShell " + $PSVersionTable.PSVersion
  if ($PSVersionTable.PSVersion.Major -lt 6) {
    "Upgrade to PowerShell 6.0!"
  }
  else {
    "Have you run a background job today (start-job)?"
  }
}

$scriptName = $MyInvocation.MyCommand.Path
psversion
"Done $scriptName."
```

<span data-ttu-id="64009-221">Als u wilt beginnen, stelt u een onderbrekings punt in dat interessant is in het script, zoals een regel, opdracht, variabele of functie.</span><span class="sxs-lookup"><span data-stu-id="64009-221">To start, set a breakpoint at a point of interest in the script, such as a line, command, variable, or function.</span></span>

<span data-ttu-id="64009-222">Begin door een regel onderbreking te maken op de eerste regel van het Test.ps1 script in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="64009-222">Start by creating a line breakpoint on the first line of the Test.ps1 script in the current directory.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

<span data-ttu-id="64009-223">U kunt deze opdracht afkorten tot:</span><span class="sxs-lookup"><span data-stu-id="64009-223">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

<span data-ttu-id="64009-224">De opdracht retourneert een regel voor het onderbrekings object ( **System. Management. Automation. LineBreakpoint** ).</span><span class="sxs-lookup"><span data-stu-id="64009-224">The command returns a line-breakpoint object ( **System.Management.Automation.LineBreakpoint** ).</span></span>

```
Column     : 0
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\test.ps1
ScriptName : C:\ps-test\test.ps1
```

<span data-ttu-id="64009-225">Start nu het script.</span><span class="sxs-lookup"><span data-stu-id="64009-225">Now, start the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
```

<span data-ttu-id="64009-226">Wanneer het script het eerste onderbrekings punt bereikt, geeft het onderbrekings bericht aan dat het fout opsporingsprogramma actief is.</span><span class="sxs-lookup"><span data-stu-id="64009-226">When the script reaches the first breakpoint, the breakpoint message indicates that the debugger is active.</span></span> <span data-ttu-id="64009-227">Hierin wordt het onderbrekings punt beschreven en wordt een voor beeld weer gegeven van de eerste regel van het script. Dit is een functie declaratie.</span><span class="sxs-lookup"><span data-stu-id="64009-227">It describes the breakpoint and previews the first line of the script, which is a function declaration.</span></span> <span data-ttu-id="64009-228">De opdracht prompt wordt ook gewijzigd om aan te geven dat het fout opsporingsprogramma het besturings element heeft.</span><span class="sxs-lookup"><span data-stu-id="64009-228">The command prompt also changes to indicate that the debugger has control.</span></span>

<span data-ttu-id="64009-229">De voorbeeld regel bevat de script naam en het regel nummer van de vooraf bekeken opdracht.</span><span class="sxs-lookup"><span data-stu-id="64009-229">The preview line includes the script name and the line number of the previewed command.</span></span>

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

<span data-ttu-id="64009-230">Gebruik de stap opdracht (en) om de eerste instructie in het script uit te voeren en de volgende instructie te bekijken.</span><span class="sxs-lookup"><span data-stu-id="64009-230">Use the Step command (s) to execute the first statement in the script and to preview the next statement.</span></span> <span data-ttu-id="64009-231">In de volgende instructie wordt de `$MyInvocation` Automatische variabele gebruikt om de waarde van de `$scriptName` variabele in te stellen op het pad en de bestands naam van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="64009-231">The next statement uses the `$MyInvocation` automatic variable to set the value of the `$scriptName` variable to the path and file name of the script file.</span></span>

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

<span data-ttu-id="64009-232">De variabele wordt op dit moment `$scriptName` niet ingevuld, maar u kunt de waarde van de variabele controleren door de waarde ervan weer te geven.</span><span class="sxs-lookup"><span data-stu-id="64009-232">At this point, the `$scriptName` variable is not populated, but you can verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="64009-233">In dit geval is de waarde `$null` .</span><span class="sxs-lookup"><span data-stu-id="64009-233">In this case, the value is `$null`.</span></span>

```powershell
DBG> $scriptname
# DBG>
```

<span data-ttu-id="64009-234">Gebruik een andere stap opdracht (en) om de huidige instructie uit te voeren en de volgende instructie in het script te bekijken.</span><span class="sxs-lookup"><span data-stu-id="64009-234">Use another Step command (s) to execute the current statement and to preview the next statement in the script.</span></span> <span data-ttu-id="64009-235">Met de volgende instructie wordt de functie PsVersion aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="64009-235">The next statement calls the PsVersion function.</span></span>

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="64009-236">Op dit moment wordt de `$scriptName` variabele gevuld, maar u controleert de waarde van de variabele door de waarde ervan weer te geven.</span><span class="sxs-lookup"><span data-stu-id="64009-236">At this point, the `$scriptName` variable is populated, but you verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="64009-237">In dit geval wordt de waarde ingesteld op het pad naar het script.</span><span class="sxs-lookup"><span data-stu-id="64009-237">In this case, the value is set to the script path.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

<span data-ttu-id="64009-238">Gebruik een andere stap opdracht om de functie aanroep uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="64009-238">Use another Step command to execute the function call.</span></span> <span data-ttu-id="64009-239">Druk op ENTER of typ "s" voor stap.</span><span class="sxs-lookup"><span data-stu-id="64009-239">Press ENTER, or type "s" for Step.</span></span>

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

<span data-ttu-id="64009-240">Het debug-bericht bevat een voor beeld van de instructie in de functie.</span><span class="sxs-lookup"><span data-stu-id="64009-240">The debug message includes a preview of the statement in the function.</span></span> <span data-ttu-id="64009-241">Als u deze instructie wilt uitvoeren en de volgende instructie in de functie wilt bekijken, kunt u een `Step` opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="64009-241">To execute this statement and to preview the next statement in the function, you can use a `Step` command.</span></span> <span data-ttu-id="64009-242">Maar in dit geval gebruikt u een StepOut-opdracht (o).</span><span class="sxs-lookup"><span data-stu-id="64009-242">But, in this case, use a StepOut command (o).</span></span> <span data-ttu-id="64009-243">De uitvoering van de functie is voltooid (tenzij deze een onderbrekings punt bereikt) en stappen voor de volgende instructie in het script.</span><span class="sxs-lookup"><span data-stu-id="64009-243">It completes the execution of the function (unless it reaches a breakpoint) and steps to the next statement in the script.</span></span>

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="64009-244">Omdat we de laatste instructie in het script hebben gedaan, hebben de opdrachten stap, StepOut en voortzetten hetzelfde effect.</span><span class="sxs-lookup"><span data-stu-id="64009-244">Because we are on the last statement in the script, the Step, StepOut, and Continue commands have the same effect.</span></span> <span data-ttu-id="64009-245">In dit geval gebruikt u StepOut (o).</span><span class="sxs-lookup"><span data-stu-id="64009-245">In this case, use StepOut (o).</span></span>

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

<span data-ttu-id="64009-246">De opdracht StepOut voert de laatste opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="64009-246">The StepOut command executes the last command.</span></span> <span data-ttu-id="64009-247">De standaard opdracht prompt geeft aan dat het fout opsporingsprogramma is afgesloten en het besturings element heeft geretourneerd aan de opdracht processor.</span><span class="sxs-lookup"><span data-stu-id="64009-247">The standard command prompt indicates that the debugger has exited and returned control to the command processor.</span></span>

<span data-ttu-id="64009-248">Voer het fout opsporingsprogramma nu opnieuw uit.</span><span class="sxs-lookup"><span data-stu-id="64009-248">Now, run the debugger again.</span></span> <span data-ttu-id="64009-249">Gebruik eerst de cmdlets en om het huidige onderbrekings punt te verwijderen `Get-PsBreakpoint` `Remove-PsBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="64009-249">First, to delete the current breakpoint, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span> <span data-ttu-id="64009-250">(Als u denkt dat u het onderbrekings punt zou kunnen hergebruiken, gebruikt u de `Disable-PsBreakpoint` cmdlet in plaats van `Remove-PsBreakpoint` .)</span><span class="sxs-lookup"><span data-stu-id="64009-250">(If you think you might reuse the breakpoint, use the `Disable-PsBreakpoint` cmdlet instead of `Remove-PsBreakpoint`.)</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="64009-251">U kunt deze opdracht afkorten tot:</span><span class="sxs-lookup"><span data-stu-id="64009-251">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> gbp | rbp
```

<span data-ttu-id="64009-252">Of voer de opdracht uit door een functie te schrijven, zoals de volgende functie:</span><span class="sxs-lookup"><span data-stu-id="64009-252">Or, run the command by writing a function, such as the following function:</span></span>

```powershell
function delbr { gbp | rbp }
```

<span data-ttu-id="64009-253">Maak nu een onderbrekings punt voor de `$scriptname` variabele.</span><span class="sxs-lookup"><span data-stu-id="64009-253">Now, create a breakpoint on the `$scriptname` variable.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

<span data-ttu-id="64009-254">U kunt de opdracht als volgt afkorten:</span><span class="sxs-lookup"><span data-stu-id="64009-254">You can abbreviate the command as:</span></span>

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

<span data-ttu-id="64009-255">Start nu het script.</span><span class="sxs-lookup"><span data-stu-id="64009-255">Now, start the script.</span></span> <span data-ttu-id="64009-256">Het script bereikt het onderbrekings punt van de variabele.</span><span class="sxs-lookup"><span data-stu-id="64009-256">The script reaches the variable breakpoint.</span></span> <span data-ttu-id="64009-257">De standaard modus is schrijven, dus de uitvoering stopt net vóór de instructie die de waarde van de variabele wijzigt.</span><span class="sxs-lookup"><span data-stu-id="64009-257">The default mode is Write, so execution stops just before the statement that changes the value of the variable.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

<span data-ttu-id="64009-258">De huidige waarde van de variabele weer geven `$scriptName` `$null` .</span><span class="sxs-lookup"><span data-stu-id="64009-258">Display the current value of the `$scriptName` variable, which is `$null`.</span></span>

```powershell
DBG> $scriptName
# DBG>
```

<span data-ttu-id="64009-259">Gebruik een stap opdracht (en) om de instructie uit te voeren waarmee de variabele wordt gevuld.</span><span class="sxs-lookup"><span data-stu-id="64009-259">Use a Step command (s) to execute the statement that populates the variable.</span></span>
<span data-ttu-id="64009-260">Vervolgens wordt de nieuwe waarde van de variabele weer gegeven `$scriptName` .</span><span class="sxs-lookup"><span data-stu-id="64009-260">Then, display the new value of the `$scriptName` variable.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="64009-261">De volgende instructie is een aanroep van de functie PsVersion.</span><span class="sxs-lookup"><span data-stu-id="64009-261">The next statement is a call to the PsVersion function.</span></span> <span data-ttu-id="64009-262">Als u de functie wilt overs Laan, maar nog steeds wilt uitvoeren, gebruikt u een StepOver-opdracht (v).</span><span class="sxs-lookup"><span data-stu-id="64009-262">To skip the function but still execute it, use a StepOver command (v).</span></span> <span data-ttu-id="64009-263">Als u zich al in de functie bevindt wanneer u StepOver gebruikt, is deze niet effectief.</span><span class="sxs-lookup"><span data-stu-id="64009-263">If you are already in the function when you use StepOver, it is not effective.</span></span> <span data-ttu-id="64009-264">De functie aanroep wordt weer gegeven, maar wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="64009-264">The function call is displayed, but it is not executed.</span></span>

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="64009-265">Met de opdracht StepOver wordt de functie uitgevoerd en wordt een voor beeld weer gegeven van de volgende instructie in het script, die de laatste regel afdrukt.</span><span class="sxs-lookup"><span data-stu-id="64009-265">The StepOver command executes the function, and it previews the next statement in the script, which prints the final line.</span></span>

<span data-ttu-id="64009-266">Gebruik een stop opdracht (t) om het fout opsporingsprogramma af te sluiten.</span><span class="sxs-lookup"><span data-stu-id="64009-266">Use a Stop command (t) to exit the debugger.</span></span> <span data-ttu-id="64009-267">De opdracht prompt wordt teruggezet naar de standaard opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="64009-267">The command prompt reverts to the standard command prompt.</span></span>

```powershell
C:\ps-test>
```

<span data-ttu-id="64009-268">Gebruik de cmdlets en om de onderbrekings punten te verwijderen `Get-PsBreakpoint` `Remove-PsBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="64009-268">To delete the breakpoints, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="64009-269">Maak een nieuwe opdracht onderbrekings punt voor de functie PsVersion.</span><span class="sxs-lookup"><span data-stu-id="64009-269">Create a new command breakpoint on the PsVersion function.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

<span data-ttu-id="64009-270">U kunt deze opdracht afkorten tot:</span><span class="sxs-lookup"><span data-stu-id="64009-270">You can abbreviate this command to:</span></span>

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

<span data-ttu-id="64009-271">Voer nu het script uit.</span><span class="sxs-lookup"><span data-stu-id="64009-271">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

<span data-ttu-id="64009-272">Het script bereikt het onderbrekings punt bij de functie aanroep.</span><span class="sxs-lookup"><span data-stu-id="64009-272">The script reaches the breakpoint at the function call.</span></span> <span data-ttu-id="64009-273">De functie is op dit moment nog niet aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="64009-273">At this point, the function has not yet been called.</span></span> <span data-ttu-id="64009-274">Dit biedt u de mogelijkheid om de actie parameter van te gebruiken om voor waarden in te `Set-PSBreakpoint` stellen voor de uitvoering van het onderbrekings punt of om voorbereidende-of diagnose taken uit te voeren, zoals het starten van een logboek of het aanroepen van een diagnose-of beveiligings script.</span><span class="sxs-lookup"><span data-stu-id="64009-274">This gives you the opportunity to use the Action parameter of `Set-PSBreakpoint` to set conditions for the execution of the breakpoint or to perform preparatory or diagnostic tasks, such as starting a log or invoking a diagnostic or security script.</span></span>

<span data-ttu-id="64009-275">Als u een actie wilt instellen, gebruikt u de opdracht door gaan (c) om het script af te sluiten en een `Remove-PsBreakpoint` opdracht om het huidige onderbrekings punt te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="64009-275">To set an action, use a Continue command (c) to exit the script, and a `Remove-PsBreakpoint` command to delete the current breakpoint.</span></span> <span data-ttu-id="64009-276">(Onderbrekings punten zijn alleen-lezen, dus u kunt geen actie aan het huidige onderbrekings punt toevoegen.)</span><span class="sxs-lookup"><span data-stu-id="64009-276">(Breakpoints are read-only, so you cannot add an action to the current breakpoint.)</span></span>

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

<span data-ttu-id="64009-277">Maak nu een nieuwe opdracht onderbrekings punt met een actie.</span><span class="sxs-lookup"><span data-stu-id="64009-277">Now, create a new command breakpoint with an action.</span></span> <span data-ttu-id="64009-278">Met de volgende opdracht wordt een opdracht onderbrekings punt ingesteld met een actie waarmee de waarde van de `$scriptName` variabele wordt geregistreerd wanneer de functie wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="64009-278">The following command sets a command breakpoint with an action that logs the value of the `$scriptName` variable when the function is called.</span></span> <span data-ttu-id="64009-279">Omdat het sleutel woord einde niet wordt gebruikt in de actie, wordt de uitvoering niet gestopt.</span><span class="sxs-lookup"><span data-stu-id="64009-279">Because the Break keyword is not used in the action, execution does not stop.</span></span> <span data-ttu-id="64009-280">(De apostroffen (') is het regel vervolg teken.)</span><span class="sxs-lookup"><span data-stu-id="64009-280">(The backtick (\`) is the line-continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

<span data-ttu-id="64009-281">U kunt ook acties toevoegen die voor waarden voor het onderbrekings punt instellen.</span><span class="sxs-lookup"><span data-stu-id="64009-281">You can also add actions that set conditions for the breakpoint.</span></span> <span data-ttu-id="64009-282">In de volgende opdracht wordt het onderbrekings punt voor opdrachten alleen uitgevoerd als het uitvoerings beleid is ingesteld op RemoteSigned, het meest beperkende beleid dat nog steeds in staat is om scripts uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="64009-282">In the following command, the command breakpoint is executed only if the execution policy is set to RemoteSigned, the most restrictive policy that still permits you to run scripts.</span></span> <span data-ttu-id="64009-283">(De apostroffen (') is het voortzettings teken.)</span><span class="sxs-lookup"><span data-stu-id="64009-283">(The backtick (\`) is the continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

<span data-ttu-id="64009-284">Met het sleutel woord break in de actie wordt het fout opsporingsprogramma doorgestuurd om het onderbrekings punt uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="64009-284">The Break keyword in the action directs the debugger to execute the breakpoint.</span></span>
<span data-ttu-id="64009-285">U kunt ook het sleutel woord continue gebruiken om het fout opsporingsprogramma te laten uitvoeren zonder te verbreken.</span><span class="sxs-lookup"><span data-stu-id="64009-285">You can also use the Continue keyword to direct the debugger to execute without breaking.</span></span> <span data-ttu-id="64009-286">Omdat het sleutel woord default wordt voortgezet, moet u onderbreken opgeven om de uitvoering te stoppen.</span><span class="sxs-lookup"><span data-stu-id="64009-286">Because the default keyword is Continue, you must specify Break to stop execution.</span></span>

<span data-ttu-id="64009-287">Voer nu het script uit.</span><span class="sxs-lookup"><span data-stu-id="64009-287">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

<span data-ttu-id="64009-288">Omdat het uitvoerings beleid is ingesteld op **RemoteSigned** , wordt de uitvoering gestopt bij de functie aanroep.</span><span class="sxs-lookup"><span data-stu-id="64009-288">Because the execution policy is set to **RemoteSigned** , execution stops at the function call.</span></span>

<span data-ttu-id="64009-289">Op dit moment kunt u de aanroep stack controleren.</span><span class="sxs-lookup"><span data-stu-id="64009-289">At this point, you might want to check the call stack.</span></span> <span data-ttu-id="64009-290">Gebruik de `Get-PsCallStack` cmdlet of de `Get-PsCallStack` debugger opdracht (k).</span><span class="sxs-lookup"><span data-stu-id="64009-290">Use the `Get-PsCallStack` cmdlet or the `Get-PsCallStack` debugger command (k).</span></span> <span data-ttu-id="64009-291">Met de volgende opdracht wordt de huidige aanroep stack opgehaald.</span><span class="sxs-lookup"><span data-stu-id="64009-291">The following command gets the current call stack.</span></span>

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

<span data-ttu-id="64009-292">In dit voor beeld ziet u slechts enkele van de vele manieren waarop u het Power Shell-fout opsporingsprogramma kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="64009-292">This example demonstrates just a few of the many ways to use the PowerShell debugger.</span></span>

<span data-ttu-id="64009-293">Voor meer informatie over de cmdlets voor fout opsporing typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="64009-293">For more information about the debugger cmdlets, type the following command:</span></span>

```powershell
help <cmdlet-name> -full
```

<span data-ttu-id="64009-294">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="64009-294">For example, type:</span></span>

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a><span data-ttu-id="64009-295">Andere functies voor fout opsporing in Power shell</span><span class="sxs-lookup"><span data-stu-id="64009-295">Other Debugging Features in PowerShell</span></span>

<span data-ttu-id="64009-296">Naast de Power Shell-fout opsporing bevat Power shell diverse andere functies die u kunt gebruiken om fouten in scripts en functies op te sporen.</span><span class="sxs-lookup"><span data-stu-id="64009-296">In addition to the PowerShell debugger, PowerShell includes several other features that you can use to debug scripts and functions.</span></span>

- <span data-ttu-id="64009-297">Windows PowerShell ISE bevat een interactief grafisch fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="64009-297">Windows PowerShell ISE includes an interactive graphical debugger.</span></span> <span data-ttu-id="64009-298">Start Windows PowerShell ISE en druk op F1 voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="64009-298">For more information, start Windows PowerShell ISE and press F1.</span></span>

- <span data-ttu-id="64009-299">De `Set-PSDebug` cmdlet biedt zeer eenvoudige script functies voor fout opsporing, waaronder steping en tracering.</span><span class="sxs-lookup"><span data-stu-id="64009-299">The `Set-PSDebug` cmdlet offers very basic script debugging features, including stepping and tracing.</span></span>

- <span data-ttu-id="64009-300">Gebruik de `Set-StrictMode` cmdlet voor het detecteren van verwijzingen naar niet-geïnitialiseerde variabelen, verwijzingen naar niet-bestaande eigenschappen van een object en de syntaxis van de functie die ongeldig is.</span><span class="sxs-lookup"><span data-stu-id="64009-300">Use the `Set-StrictMode` cmdlet to detect references to uninitialized variables, to references to non-existent properties of an object, and to function syntax that is not valid.</span></span>

- <span data-ttu-id="64009-301">Voeg diagnostische instructies toe aan een script, zoals instructies voor het weer geven van de waarde van variabelen, instructies die invoer lezen van de opdracht regel of instructies die de huidige instructie rapporteren.</span><span class="sxs-lookup"><span data-stu-id="64009-301">Add diagnostic statements to a script, such as statements that display the value of variables, statements that read input from the command line, or statements that report the current instruction.</span></span> <span data-ttu-id="64009-302">Gebruik de cmdlets die de schrijf bewerking voor deze taak bevatten, zoals `Write-Host` ,, `Write-Debug` en `Write-Warning` `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="64009-302">Use the cmdlets that contain the Write verb for this task, such as `Write-Host`, `Write-Debug`, `Write-Warning`, and `Write-Verbose`.</span></span>

## <a name="see-also"></a><span data-ttu-id="64009-303">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="64009-303">SEE ALSO</span></span>

- [<span data-ttu-id="64009-304">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="64009-304">Disable-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [<span data-ttu-id="64009-305">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="64009-305">Enable-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [<span data-ttu-id="64009-306">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="64009-306">Get-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [<span data-ttu-id="64009-307">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="64009-307">Get-PSCallStack</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [<span data-ttu-id="64009-308">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="64009-308">Remove-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [<span data-ttu-id="64009-309">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="64009-309">Set-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [<span data-ttu-id="64009-310">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="64009-310">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="64009-311">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="64009-311">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
