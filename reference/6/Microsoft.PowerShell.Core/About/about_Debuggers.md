---
description: Hierin wordt het Power Shell-fout opsporingsprogramma beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: a200d5612c29cfad63100e0db5686996032f96fa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252356"
---
# <a name="about-debuggers"></a><span data-ttu-id="62981-104">Over fout opsporing</span><span class="sxs-lookup"><span data-stu-id="62981-104">About Debuggers</span></span>

## <a name="short-description"></a><span data-ttu-id="62981-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="62981-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="62981-106">Hierin wordt het Power Shell-fout opsporingsprogramma beschreven.</span><span class="sxs-lookup"><span data-stu-id="62981-106">Describes the PowerShell debugger.</span></span>

## <a name="long-description"></a><span data-ttu-id="62981-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="62981-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="62981-108">Fout opsporing is het proces van het onderzoeken van een script terwijl het wordt uitgevoerd om fouten in de script instructies te identificeren en te corrigeren.</span><span class="sxs-lookup"><span data-stu-id="62981-108">Debugging is the process of examining a script while it is running to identify and correct errors in the script instructions.</span></span> <span data-ttu-id="62981-109">De Power Shell-fout opsporing kan u helpen bij het onderzoeken en identificeren van fouten en inefficiëntie in uw scripts, functies, opdrachten, Power shell desired state Configuration (DSC)-configuraties of-expressies.</span><span class="sxs-lookup"><span data-stu-id="62981-109">The PowerShell debugger can help you examine and identify errors and inefficiencies in your scripts, functions, commands, PowerShell Desired State Configuration (DSC) configurations, or expressions.</span></span>

<span data-ttu-id="62981-110">Vanaf Power shell 5,0 is het Power Shell-fout opsporingsprogramma bijgewerkt voor het opsporen van fouten in scripts, functies, opdrachten, configuraties of expressies die worden uitgevoerd in de-console of Windows PowerShell ISE op externe computers.</span><span class="sxs-lookup"><span data-stu-id="62981-110">Starting in PowerShell 5.0, the PowerShell debugger has been updated to debug scripts, functions, commands, configurations, or expressions that are running in either the console or Windows PowerShell ISE on remote computers.</span></span> <span data-ttu-id="62981-111">U kunt uitvoeren `Enter-PSSession` om een interactieve externe Power shell-sessie te starten waarin u onderbrekings punten en script bestanden en opdrachten voor fout opsporing op de externe computer kunt instellen.</span><span class="sxs-lookup"><span data-stu-id="62981-111">You can run `Enter-PSSession` to start an interactive remote PowerShell session in which you can set breakpoints and debug script files and commands on the remote computer.</span></span> <span data-ttu-id="62981-112">`Enter-PSSession` de functionaliteit is bijgewerkt, waarmee u opnieuw verbinding kunt maken en een niet-verbonden sessie kunt invoeren waarop een script of opdracht op een externe computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="62981-112">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running a script or command on a remote computer.</span></span> <span data-ttu-id="62981-113">Als het script dat wordt uitgevoerd een onderbrekings punt bereikt, wordt het fout opsporingsprogramma automatisch gestart door uw client sessie.</span><span class="sxs-lookup"><span data-stu-id="62981-113">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span> <span data-ttu-id="62981-114">Als de niet-verbonden sessie met een script al een onderbrekings punt heeft bereikt en op het onderbrekings punt wordt gestopt, `Enter-PSSession` wordt het opdracht regel programma voor fout opsporing automatisch gestart nadat u opnieuw verbinding hebt gemaakt met de sessie.</span><span class="sxs-lookup"><span data-stu-id="62981-114">If the disconnected session that is running a script has already hit a breakpoint, and is stopped at the breakpoint, `Enter-PSSession` automatically starts the command-line debugger, after you reconnect to the session.</span></span>

<span data-ttu-id="62981-115">U kunt de functies van de Power Shell-fout opsporing gebruiken om een Power shell-script,-functie,-opdracht of-expressie te onderzoeken terwijl deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="62981-115">You can use the features of the PowerShell debugger to examine a PowerShell script, function, command, or expression while it is running.</span></span> <span data-ttu-id="62981-116">Het Power Shell-fout opsporingsprogramma bevat een set cmdlets waarmee u onderbrekings punten kunt instellen, onderbrekings punten kunt beheren en de aanroep stack weer geven.</span><span class="sxs-lookup"><span data-stu-id="62981-116">The PowerShell debugger includes a set of cmdlets that let you set breakpoints, manage breakpoints, and view the call stack.</span></span>

## <a name="debugger-cmdlets"></a><span data-ttu-id="62981-117">Cmdlets voor fout opsporing</span><span class="sxs-lookup"><span data-stu-id="62981-117">Debugger Cmdlets</span></span>

<span data-ttu-id="62981-118">Het Power Shell-fout opsporingsprogramma bevat de volgende set cmdlets:</span><span class="sxs-lookup"><span data-stu-id="62981-118">The PowerShell debugger includes the following set of cmdlets:</span></span>

- <span data-ttu-id="62981-119">`Set-PSBreakpoint`: Hiermee stelt u onderbrekings punten in voor lijnen, variabelen en opdrachten.</span><span class="sxs-lookup"><span data-stu-id="62981-119">`Set-PSBreakpoint`: Sets breakpoints on lines, variables, and commands.</span></span>
- <span data-ttu-id="62981-120">`Get-PSBreakpoint`: Hiermee worden onderbrekings punten in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="62981-120">`Get-PSBreakpoint`: Gets breakpoints in the current session.</span></span>
- <span data-ttu-id="62981-121">`Disable-PSBreakpoint`: Schakelt onderbrekings punten in de huidige sessie uit.</span><span class="sxs-lookup"><span data-stu-id="62981-121">`Disable-PSBreakpoint`: Turns off breakpoints in the current session.</span></span>
- <span data-ttu-id="62981-122">`Enable-PSBreakpoint`: Hiermee schakelt u onderbrekings punten in de huidige sessie opnieuw in.</span><span class="sxs-lookup"><span data-stu-id="62981-122">`Enable-PSBreakpoint`: Re-enables breakpoints in the current session.</span></span>
- <span data-ttu-id="62981-123">`Remove-PSBreakpoint`: Verwijdert onderbrekings punten uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="62981-123">`Remove-PSBreakpoint`: Deletes breakpoints from the current session.</span></span>
- <span data-ttu-id="62981-124">`Get-PSCallStack`: Hiermee wordt de huidige aanroep stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="62981-124">`Get-PSCallStack`: Displays the current call stack.</span></span>

## <a name="starting-and-stopping-the-debugger"></a><span data-ttu-id="62981-125">Fout opsporing starten en stoppen</span><span class="sxs-lookup"><span data-stu-id="62981-125">Starting and Stopping the Debugger</span></span>

<span data-ttu-id="62981-126">Stel een of meer onderbrekings punten in om de fout opsporing te starten.</span><span class="sxs-lookup"><span data-stu-id="62981-126">To start the debugger, set one or more breakpoints.</span></span> <span data-ttu-id="62981-127">Voer vervolgens het script, de opdracht of de functie uit die u wilt fouten opsporen.</span><span class="sxs-lookup"><span data-stu-id="62981-127">Then, run the script, command, or function that you want to debug.</span></span>

<span data-ttu-id="62981-128">Wanneer u een onderbrekings punt bereikt, wordt de uitvoering gestopt en wordt het besturings element overgezet naar het fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="62981-128">When you reach a breakpoint, execution stops, and control is turned over to the debugger.</span></span>

<span data-ttu-id="62981-129">Als u het fout opsporingsprogramma wilt stoppen, voert u het script, de opdracht of de functie uit totdat dit is voltooid.</span><span class="sxs-lookup"><span data-stu-id="62981-129">To stop the debugger, run the script, command, or function until it is complete.</span></span> <span data-ttu-id="62981-130">Of typ `stop` of `t` .</span><span class="sxs-lookup"><span data-stu-id="62981-130">Or, type `stop` or `t`.</span></span>

### <a name="debugger-commands"></a><span data-ttu-id="62981-131">Opdrachten voor fout opsporing</span><span class="sxs-lookup"><span data-stu-id="62981-131">Debugger Commands</span></span>

<span data-ttu-id="62981-132">Wanneer u het fout opsporingsprogramma gebruikt in de Power shell-console, gebruikt u de volgende opdrachten om de uitvoering te beheren.</span><span class="sxs-lookup"><span data-stu-id="62981-132">When you use the debugger in the PowerShell console, use the following commands to control the execution.</span></span> <span data-ttu-id="62981-133">In Windows PowerShell ISE gebruikt u opdrachten in het menu fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="62981-133">In Windows PowerShell ISE, use commands on the Debug menu.</span></span>

<span data-ttu-id="62981-134">Opmerking: voor meer informatie over het gebruik van het fout opsporingsprogramma in andere hosttoepassingen, raadpleegt u de documentatie van de hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="62981-134">Note: For information about how to use the debugger in other host applications, see the host application documentation.</span></span>

- <span data-ttu-id="62981-135">`s`, `StepInto` : Voert de volgende instructie uit en stopt vervolgens.</span><span class="sxs-lookup"><span data-stu-id="62981-135">`s`, `StepInto`: Executes the next statement and then stops.</span></span>

- <span data-ttu-id="62981-136">`v`, `StepOver` : Voert de volgende instructie uit, maar slaat functies en aanroepen over.</span><span class="sxs-lookup"><span data-stu-id="62981-136">`v`, `StepOver`: Executes the next statement, but skips functions and invocations.</span></span> <span data-ttu-id="62981-137">De overgeslagen instructies worden uitgevoerd, maar niet getrapt via.</span><span class="sxs-lookup"><span data-stu-id="62981-137">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="62981-138">`Ctrl+Break`: (Alles onderbreken in ISE) is in een actief script in de Power shell-console of Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="62981-138">`Ctrl+Break`: (Break All in ISE) Breaks into a running script within either the PowerShell console, or Windows PowerShell ISE.</span></span> <span data-ttu-id="62981-139">Houd er rekening mee dat <kbd>CTRL</kbd> + -<kbd>afbreek</kbd> in Windows Power Shell 2,0, 3,0 en 4,0 het programma sluit.</span><span class="sxs-lookup"><span data-stu-id="62981-139">Note that <kbd>Ctrl</kbd>+<kbd>Break</kbd> in Windows PowerShell 2.0, 3.0, and 4.0 closes the program.</span></span> <span data-ttu-id="62981-140">Alles onderbreken werkt op zowel lokale als externe interactief uitgevoerde scripts.</span><span class="sxs-lookup"><span data-stu-id="62981-140">Break All works on both local and remote interactively-running scripts.</span></span>

- <span data-ttu-id="62981-141">`o`, `StepOut` : Stappen van de huidige functie; Eén niveau omhoog als genest.</span><span class="sxs-lookup"><span data-stu-id="62981-141">`o`, `StepOut`: Steps out of the current function; up one level if nested.</span></span> <span data-ttu-id="62981-142">In de hoofd tekst wordt het einde of het volgende onderbrekings punt voortgezet.</span><span class="sxs-lookup"><span data-stu-id="62981-142">If in the main body, it continues to the end or the next breakpoint.</span></span> <span data-ttu-id="62981-143">De overgeslagen instructies worden uitgevoerd, maar niet getrapt via.</span><span class="sxs-lookup"><span data-stu-id="62981-143">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="62981-144">`c`, `Continue` : Blijft actief totdat het script is voltooid of totdat het volgende onderbrekings punt is bereikt.</span><span class="sxs-lookup"><span data-stu-id="62981-144">`c`, `Continue`: Continues to run until the script is complete or until the next breakpoint is reached.</span></span> <span data-ttu-id="62981-145">De overgeslagen instructies worden uitgevoerd, maar niet getrapt via.</span><span class="sxs-lookup"><span data-stu-id="62981-145">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="62981-146">`l`, `List` : Geeft het deel van het script weer dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="62981-146">`l`, `List`: Displays the part of the script that is executing.</span></span> <span data-ttu-id="62981-147">Standaard worden de huidige regel, vijf vorige regels en tien volgende regels weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="62981-147">By default, it displays the current line, five previous lines, and 10 subsequent lines.</span></span>
  <span data-ttu-id="62981-148">Als u het script wilt blijven aanbieden, drukt u op ENTER.</span><span class="sxs-lookup"><span data-stu-id="62981-148">To continue listing the script, press ENTER.</span></span>

- <span data-ttu-id="62981-149">`l <m>`, `List` : Hiermee worden 16 regels van het script weer gegeven, te beginnen met het regel nummer dat is opgegeven door `<m>` .</span><span class="sxs-lookup"><span data-stu-id="62981-149">`l <m>`, `List`: Displays 16 lines of the script beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="62981-150">`l <m> <n>`, `List` : Hiermee worden de `<n>` regels van het script weer gegeven, te beginnen met het regel nummer dat is opgegeven door `<m>` .</span><span class="sxs-lookup"><span data-stu-id="62981-150">`l <m> <n>`, `List`: Displays `<n>` lines of the script, beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="62981-151">`q`, `Stop` , `Exit` : Stopt met het uitvoeren van het script en sluit het fout opsporingsprogramma af.</span><span class="sxs-lookup"><span data-stu-id="62981-151">`q`, `Stop`, `Exit`: Stops executing the script, and exits the debugger.</span></span> <span data-ttu-id="62981-152">Als u fouten opspoort in een taak door de cmdlet uit te voeren `Debug-Job` , wordt `Exit` het fout opsporingsprogramma door de opdracht losgekoppeld en kan de taak blijven worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="62981-152">If you are debugging a job by running the `Debug-Job` cmdlet, the `Exit` command detaches the debugger, and allows the job to continue running.</span></span>

- <span data-ttu-id="62981-153">`k`, `Get-PsCallStack` : Hiermee wordt de huidige aanroep stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="62981-153">`k`, `Get-PsCallStack`: Displays the current call stack.</span></span>

- <span data-ttu-id="62981-154">`<Enter>`: Herhaalt de laatste opdracht als de stap (s), StepOver (v) of lijst (l).</span><span class="sxs-lookup"><span data-stu-id="62981-154">`<Enter>`: Repeats the last command if it was Step (s), StepOver (v), or List (l).</span></span> <span data-ttu-id="62981-155">Anders vertegenwoordigt een indienings actie.</span><span class="sxs-lookup"><span data-stu-id="62981-155">Otherwise, represents a submit action.</span></span>

- <span data-ttu-id="62981-156">`?`, `h` : Geeft de Help voor de opdracht fout opsporing weer.</span><span class="sxs-lookup"><span data-stu-id="62981-156">`?`, `h`: Displays the debugger command Help.</span></span>

<span data-ttu-id="62981-157">Als u het fout opsporingsprogramma wilt afsluiten, kunt u stoppen (q) gebruiken.</span><span class="sxs-lookup"><span data-stu-id="62981-157">To exit the debugger, you can use Stop (q).</span></span>

<span data-ttu-id="62981-158">Vanaf Power shell 5,0 kunt u de opdracht exit uitvoeren om een geneste foutopsporingssessie te afsluiten die u hebt gestart door ofwel of uit te voeren `Debug-Job` `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="62981-158">Starting in PowerShell 5.0, you can run the Exit command to exit a nested debugging session that you started by running either `Debug-Job` or `Debug-Runspace`.</span></span>

<span data-ttu-id="62981-159">Met behulp van deze opdrachten voor fout opsporing kunt u een script uitvoeren, stoppen op een bepaald punt, de waarden van variabelen en de status van het systeem controleren en door gaan met het uitvoeren van het script totdat u een probleem hebt vastgesteld.</span><span class="sxs-lookup"><span data-stu-id="62981-159">By using these debugger commands, you can run a script, stop on a point of concern, examine the values of variables and the state of the system, and continue running the script until you have identified a problem.</span></span>

<span data-ttu-id="62981-160">Opmerking: als u een instructie Step Into met een omleidings operator, zoals ' > ', worden de Power Shell-fout opsporings stappen voor alle resterende instructies in het script.</span><span class="sxs-lookup"><span data-stu-id="62981-160">NOTE: If you step into a statement with a redirection operator, such as ">", the PowerShell debugger steps over all remaining statements in the script.</span></span>

<span data-ttu-id="62981-161">De waarden van script variabelen weer geven</span><span class="sxs-lookup"><span data-stu-id="62981-161">Displaying the Values of script Variables</span></span>

<span data-ttu-id="62981-162">Terwijl u zich in het fout opsporingsprogramma bevindt, kunt u ook opdrachten invoeren, de waarde van variabelen weer geven, cmdlets gebruiken en scripts uitvoeren op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="62981-162">While you are in the debugger, you can also enter commands, display the value of variables, use cmdlets, and run scripts at the command line.</span></span>

<span data-ttu-id="62981-163">U kunt de huidige waarde van alle variabelen weer geven in het script waarvoor fout opsporing wordt uitgevoerd, met uitzonde ring van de volgende automatische variabelen:</span><span class="sxs-lookup"><span data-stu-id="62981-163">You can display the current value of all variables in the script that is being debugged, except for the following automatic variables:</span></span>

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

<span data-ttu-id="62981-164">Als u probeert de waarde van een van deze variabelen weer te geven, krijgt u de waarde van die variabele voor in een interne pijp lijn die wordt gebruikt door het fout opsporingsprogramma, niet de waarde van de variabele in het script.</span><span class="sxs-lookup"><span data-stu-id="62981-164">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span>

<span data-ttu-id="62981-165">Als u de waarde van deze variabelen wilt weer geven voor het script dat wordt opgespoord, wijst u in het script de waarde van de automatische variabele toe aan een nieuwe variabele.</span><span class="sxs-lookup"><span data-stu-id="62981-165">To display the value these variables for the script that is being debugged, in the script, assign the value of the automatic variable to a new variable.</span></span> <span data-ttu-id="62981-166">Vervolgens kunt u de waarde van de nieuwe variabele weer geven.</span><span class="sxs-lookup"><span data-stu-id="62981-166">Then you can display the value of the new variable.</span></span>

<span data-ttu-id="62981-167">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="62981-167">For example,</span></span>

```powershell
$scriptArgs = $Args
$scriptArgs
```

<span data-ttu-id="62981-168">In het voor beeld in dit onderwerp wordt de waarde van de `$MyInvocation` variabele als volgt opnieuw toegewezen:</span><span class="sxs-lookup"><span data-stu-id="62981-168">In the example in this topic, the value of the `$MyInvocation` variable is reassigned as follows:</span></span>

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a><span data-ttu-id="62981-169">De debugger omgeving</span><span class="sxs-lookup"><span data-stu-id="62981-169">The Debugger Environment</span></span>

<span data-ttu-id="62981-170">Wanneer u een onderbrekings punt bereikt, voert u de omgeving voor fout opsporing in.</span><span class="sxs-lookup"><span data-stu-id="62981-170">When you reach a breakpoint, you enter the debugger environment.</span></span> <span data-ttu-id="62981-171">De opdracht prompt wordt gewijzigd zodat deze begint met "[DBG]:".</span><span class="sxs-lookup"><span data-stu-id="62981-171">The command prompt changes so that it begins with "[DBG]:".</span></span>

<span data-ttu-id="62981-172">Zie [about_Prompts](about_prompts.md)voor meer informatie over het aanpassen van de prompt.</span><span class="sxs-lookup"><span data-stu-id="62981-172">For more information about customizing the prompt, see [about_Prompts](about_prompts.md).</span></span>

<span data-ttu-id="62981-173">Daarnaast wordt in sommige hosttoepassingen, zoals de Power shell-console, (maar niet in Windows Power shell Integrated Scripting Environment [ISE]), een geneste prompt geopend voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="62981-173">Also, in some host applications, such as the PowerShell console, (but not in Windows PowerShell Integrated Scripting Environment [ISE]), a nested prompt opens for debugging.</span></span> <span data-ttu-id="62981-174">U kunt de geneste prompt detecteren door de herhaalde tekens die groter zijn dan (ASCII 62) die worden weer gegeven bij de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="62981-174">You can detect the nested prompt by the repeating greater-than characters (ASCII 62) that appear at the command prompt.</span></span>

<span data-ttu-id="62981-175">Het volgende is bijvoorbeeld de standaard prompt voor fout opsporing in de Power shell-console:</span><span class="sxs-lookup"><span data-stu-id="62981-175">For example, the following is the default debugging prompt in the PowerShell console:</span></span>

```
[DBG]: PS (get-location)>>>
```

<span data-ttu-id="62981-176">U kunt het nest niveau vinden met behulp van de `$NestedPromptLevel` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="62981-176">You can find the nesting level by using the `$NestedPromptLevel` automatic variable.</span></span>

<span data-ttu-id="62981-177">Daarnaast wordt een automatische variabele `$PSDebugContext` gedefinieerd in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="62981-177">Additionally, an automatic variable, `$PSDebugContext`, is defined in the local scope.</span></span> <span data-ttu-id="62981-178">U kunt de aanwezigheid van de `$PsDebugContext` variabele gebruiken om te bepalen of u zich in het fout opsporingsprogramma bevindt.</span><span class="sxs-lookup"><span data-stu-id="62981-178">You can use the presence of the `$PsDebugContext` variable to determine whether you are in the debugger.</span></span>

<span data-ttu-id="62981-179">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="62981-179">For example:</span></span>

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

<span data-ttu-id="62981-180">U kunt de waarde van de `$PSDebugContext` variabele in de fout opsporing gebruiken.</span><span class="sxs-lookup"><span data-stu-id="62981-180">You can use the value of the `$PSDebugContext` variable in your debugging.</span></span>

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a><span data-ttu-id="62981-181">Fout opsporing en bereik</span><span class="sxs-lookup"><span data-stu-id="62981-181">Debugging and Scope</span></span>

<span data-ttu-id="62981-182">Breuk in het fout opsporingsprogramma wijzigt niet het bereik waarin u werkt, maar wanneer u een onderbrekings punt in een script bereikt, gaat u naar het script bereik.</span><span class="sxs-lookup"><span data-stu-id="62981-182">Breaking into the debugger does not change the scope in which you are operating, but when you reach a breakpoint in a script, you move into the script scope.</span></span> <span data-ttu-id="62981-183">Het script bereik is een onderliggend item van het bereik waarin u het fout opsporingsprogramma hebt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="62981-183">The script scope is a child of the scope in which you ran the debugger.</span></span>

<span data-ttu-id="62981-184">Als u de variabelen en aliassen wilt vinden die in het script bereik zijn gedefinieerd, gebruikt u de para meter bereik van de `Get-Alias` `Get-Variable` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="62981-184">To find the variables and aliases that are defined in the script scope, use the Scope parameter of the `Get-Alias` or `Get-Variable` cmdlets.</span></span>

<span data-ttu-id="62981-185">Met de volgende opdracht worden bijvoorbeeld de variabelen in het lokale (script) bereik opgehaald:</span><span class="sxs-lookup"><span data-stu-id="62981-185">For example, the following command gets the variables in the local (script) scope:</span></span>

```powershell
Get-Variable -scope 0
```

<span data-ttu-id="62981-186">U kunt de opdracht als volgt afkorten:</span><span class="sxs-lookup"><span data-stu-id="62981-186">You can abbreviate the command as:</span></span>

```powershell
gv -s 0
```

<span data-ttu-id="62981-187">Dit is een handige manier om alleen de variabelen weer te geven die u in het script hebt gedefinieerd en die u tijdens het opsporen van fouten hebt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="62981-187">This is a useful way to see only the variables that you defined in the script and that you defined while debugging.</span></span>

<span data-ttu-id="62981-188">Fout opsporing op de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="62981-188">Debugging at the Command Line</span></span>

<span data-ttu-id="62981-189">Wanneer u een onderbrekings punt voor een variabele of een opdracht onderbrekings punt instelt, kunt u het onderbrekings punt alleen instellen in een script bestand.</span><span class="sxs-lookup"><span data-stu-id="62981-189">When you set a variable breakpoint or a command breakpoint, you can set the breakpoint only in a script file.</span></span> <span data-ttu-id="62981-190">Het onderbrekings punt wordt echter standaard ingesteld op alles dat wordt uitgevoerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="62981-190">However, by default, the breakpoint is set on anything that runs in the current session.</span></span>

<span data-ttu-id="62981-191">Als u bijvoorbeeld een onderbrekings punt instelt voor de `$name` variabele, wordt het fout opsporingsprogramma afgebroken op een wille keurige `$name` variabele in een script, opdracht, functie, script-cmdlet of expressie die u uitvoert totdat u het onderbrekings punt uitschakelt of verwijdert.</span><span class="sxs-lookup"><span data-stu-id="62981-191">For example, if you set a breakpoint on the `$name` variable, the debugger breaks on any `$name` variable in any script, command, function, script cmdlet or expression that you run until you disable or remove the breakpoint.</span></span>

<span data-ttu-id="62981-192">Zo kunt u fouten opsporen in uw scripts in een realistischere context waarin ze mogelijk worden beïnvloed door functies, variabelen en andere scripts in de sessie en in het profiel van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="62981-192">This allows you to debug your scripts in a more realistic context in which they might be affected by functions, variables, and other scripts in the session and in the user's profile.</span></span>

<span data-ttu-id="62981-193">Regel onderbrekingen zijn specifiek voor script bestanden, zodat ze alleen worden ingesteld in script bestanden.</span><span class="sxs-lookup"><span data-stu-id="62981-193">Line breakpoints are specific to script files, so they are set only in script files.</span></span>

## <a name="debugging-functions"></a><span data-ttu-id="62981-194">Functies voor fout opsporing</span><span class="sxs-lookup"><span data-stu-id="62981-194">Debugging Functions</span></span>

<span data-ttu-id="62981-195">Wanneer u een onderbrekings punt instelt voor een functie die de volgende secties bevat, `Begin` `Process` wordt `End` het fout opsporingsprogramma afgebroken op de eerste regel van elke sectie.</span><span class="sxs-lookup"><span data-stu-id="62981-195">When you set a breakpoint on a function that has `Begin`, `Process`, and `End` sections, the debugger breaks at the first line of each section.</span></span>

<span data-ttu-id="62981-196">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="62981-196">For example:</span></span>

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

## <a name="debugging-remote-scripts"></a><span data-ttu-id="62981-197">Fout opsporing voor externe scripts</span><span class="sxs-lookup"><span data-stu-id="62981-197">Debugging Remote Scripts</span></span>

<span data-ttu-id="62981-198">Vanaf Power shell 5,0 kunt u de Power Shell-fout opsporing uitvoeren in een externe sessie, in de-console of in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="62981-198">Starting in PowerShell 5.0, you can run the PowerShell debugger in a remote session, in either the console, or Windows PowerShell ISE.</span></span>
<span data-ttu-id="62981-199">`Enter-PSSession` de functionaliteit is bijgewerkt, waarmee u opnieuw verbinding kunt maken en een niet-verbonden sessie kunt invoeren die wordt uitgevoerd op een externe computer en die op dit moment een script uitvoert.</span><span class="sxs-lookup"><span data-stu-id="62981-199">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running on a remote computer, and currently running a script.</span></span> <span data-ttu-id="62981-200">Als het script dat wordt uitgevoerd een onderbrekings punt bereikt, wordt het fout opsporingsprogramma automatisch gestart door uw client sessie.</span><span class="sxs-lookup"><span data-stu-id="62981-200">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span>

<span data-ttu-id="62981-201">Hier volgt een voor beeld van hoe dit werkt, waarbij onderbrekings punten in een script worden ingesteld op regels 6, 11, 22 en 25.</span><span class="sxs-lookup"><span data-stu-id="62981-201">The following is an example that shows how this works, with breakpoints set in a script at lines 6, 11, 22, and 25.</span></span> <span data-ttu-id="62981-202">In het voor beeld, wanneer het fout opsporingsprogramma wordt gestart, zijn er twee instructies: de naam van de computer waarop de sessie wordt uitgevoerd en de DBG-prompt waarin u kunt zien dat u zich in de foutopsporingsmodus bevindt.</span><span class="sxs-lookup"><span data-stu-id="62981-202">Note that in the example, when the debugger starts, there are two identifying prompts: the name of the computer on which the session is running, and the DBG prompt that lets you know you are in debugging mode.</span></span>

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

## <a name="examples"></a><span data-ttu-id="62981-203">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="62981-203">Examples</span></span>

<span data-ttu-id="62981-204">Met dit test script wordt de versie van het besturings systeem gedetecteerd en wordt er een systeem bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="62981-204">This test script detects the version of the operating system and displays a system-appropriate message.</span></span> <span data-ttu-id="62981-205">Het bevat een functie, een functie aanroep en een variabele.</span><span class="sxs-lookup"><span data-stu-id="62981-205">It includes a function, a function call, and a variable.</span></span>

<span data-ttu-id="62981-206">De volgende opdracht wordt de inhoud van het test script bestand weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="62981-206">The following command displays the contents of the test script file:</span></span>

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

<span data-ttu-id="62981-207">Als u wilt beginnen, stelt u een onderbrekings punt in dat interessant is in het script, zoals een regel, opdracht, variabele of functie.</span><span class="sxs-lookup"><span data-stu-id="62981-207">To start, set a breakpoint at a point of interest in the script, such as a line, command, variable, or function.</span></span>

<span data-ttu-id="62981-208">Begin door een regel onderbreking te maken op de eerste regel van het Test.ps1 script in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="62981-208">Start by creating a line breakpoint on the first line of the Test.ps1 script in the current directory.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

<span data-ttu-id="62981-209">U kunt deze opdracht afkorten tot:</span><span class="sxs-lookup"><span data-stu-id="62981-209">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

<span data-ttu-id="62981-210">De opdracht retourneert een regel voor het onderbrekings object ( **System. Management. Automation. LineBreakpoint** ).</span><span class="sxs-lookup"><span data-stu-id="62981-210">The command returns a line-breakpoint object ( **System.Management.Automation.LineBreakpoint** ).</span></span>

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

<span data-ttu-id="62981-211">Start nu het script.</span><span class="sxs-lookup"><span data-stu-id="62981-211">Now, start the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
```

<span data-ttu-id="62981-212">Wanneer het script het eerste onderbrekings punt bereikt, geeft het onderbrekings bericht aan dat het fout opsporingsprogramma actief is.</span><span class="sxs-lookup"><span data-stu-id="62981-212">When the script reaches the first breakpoint, the breakpoint message indicates that the debugger is active.</span></span> <span data-ttu-id="62981-213">Hierin wordt het onderbrekings punt beschreven en wordt een voor beeld weer gegeven van de eerste regel van het script. Dit is een functie declaratie.</span><span class="sxs-lookup"><span data-stu-id="62981-213">It describes the breakpoint and previews the first line of the script, which is a function declaration.</span></span> <span data-ttu-id="62981-214">De opdracht prompt wordt ook gewijzigd om aan te geven dat het fout opsporingsprogramma het besturings element heeft.</span><span class="sxs-lookup"><span data-stu-id="62981-214">The command prompt also changes to indicate that the debugger has control.</span></span>

<span data-ttu-id="62981-215">De voorbeeld regel bevat de script naam en het regel nummer van de vooraf bekeken opdracht.</span><span class="sxs-lookup"><span data-stu-id="62981-215">The preview line includes the script name and the line number of the previewed command.</span></span>

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

<span data-ttu-id="62981-216">Gebruik de stap opdracht (en) om de eerste instructie in het script uit te voeren en de volgende instructie te bekijken.</span><span class="sxs-lookup"><span data-stu-id="62981-216">Use the Step command (s) to execute the first statement in the script and to preview the next statement.</span></span> <span data-ttu-id="62981-217">In de volgende instructie wordt de `$MyInvocation` Automatische variabele gebruikt om de waarde van de `$scriptName` variabele in te stellen op het pad en de bestands naam van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="62981-217">The next statement uses the `$MyInvocation` automatic variable to set the value of the `$scriptName` variable to the path and file name of the script file.</span></span>

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

<span data-ttu-id="62981-218">De variabele wordt op dit moment `$scriptName` niet ingevuld, maar u kunt de waarde van de variabele controleren door de waarde ervan weer te geven.</span><span class="sxs-lookup"><span data-stu-id="62981-218">At this point, the `$scriptName` variable is not populated, but you can verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="62981-219">In dit geval is de waarde `$null` .</span><span class="sxs-lookup"><span data-stu-id="62981-219">In this case, the value is `$null`.</span></span>

```powershell
DBG> $scriptname
# DBG>
```

<span data-ttu-id="62981-220">Gebruik een andere stap opdracht (en) om de huidige instructie uit te voeren en de volgende instructie in het script te bekijken.</span><span class="sxs-lookup"><span data-stu-id="62981-220">Use another Step command (s) to execute the current statement and to preview the next statement in the script.</span></span> <span data-ttu-id="62981-221">Met de volgende instructie wordt de functie PsVersion aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="62981-221">The next statement calls the PsVersion function.</span></span>

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="62981-222">Op dit moment wordt de `$scriptName` variabele gevuld, maar u controleert de waarde van de variabele door de waarde ervan weer te geven.</span><span class="sxs-lookup"><span data-stu-id="62981-222">At this point, the `$scriptName` variable is populated, but you verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="62981-223">In dit geval wordt de waarde ingesteld op het pad naar het script.</span><span class="sxs-lookup"><span data-stu-id="62981-223">In this case, the value is set to the script path.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

<span data-ttu-id="62981-224">Gebruik een andere stap opdracht om de functie aanroep uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="62981-224">Use another Step command to execute the function call.</span></span> <span data-ttu-id="62981-225">Druk op ENTER of typ "s" voor stap.</span><span class="sxs-lookup"><span data-stu-id="62981-225">Press ENTER, or type "s" for Step.</span></span>

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

<span data-ttu-id="62981-226">Het debug-bericht bevat een voor beeld van de instructie in de functie.</span><span class="sxs-lookup"><span data-stu-id="62981-226">The debug message includes a preview of the statement in the function.</span></span> <span data-ttu-id="62981-227">Als u deze instructie wilt uitvoeren en de volgende instructie in de functie wilt bekijken, kunt u een `Step` opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="62981-227">To execute this statement and to preview the next statement in the function, you can use a `Step` command.</span></span> <span data-ttu-id="62981-228">Maar in dit geval gebruikt u een StepOut-opdracht (o).</span><span class="sxs-lookup"><span data-stu-id="62981-228">But, in this case, use a StepOut command (o).</span></span> <span data-ttu-id="62981-229">De uitvoering van de functie is voltooid (tenzij deze een onderbrekings punt bereikt) en stappen voor de volgende instructie in het script.</span><span class="sxs-lookup"><span data-stu-id="62981-229">It completes the execution of the function (unless it reaches a breakpoint) and steps to the next statement in the script.</span></span>

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="62981-230">Omdat we de laatste instructie in het script hebben gedaan, hebben de opdrachten stap, StepOut en voortzetten hetzelfde effect.</span><span class="sxs-lookup"><span data-stu-id="62981-230">Because we are on the last statement in the script, the Step, StepOut, and Continue commands have the same effect.</span></span> <span data-ttu-id="62981-231">In dit geval gebruikt u StepOut (o).</span><span class="sxs-lookup"><span data-stu-id="62981-231">In this case, use StepOut (o).</span></span>

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

<span data-ttu-id="62981-232">De opdracht StepOut voert de laatste opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="62981-232">The StepOut command executes the last command.</span></span> <span data-ttu-id="62981-233">De standaard opdracht prompt geeft aan dat het fout opsporingsprogramma is afgesloten en het besturings element heeft geretourneerd aan de opdracht processor.</span><span class="sxs-lookup"><span data-stu-id="62981-233">The standard command prompt indicates that the debugger has exited and returned control to the command processor.</span></span>

<span data-ttu-id="62981-234">Voer het fout opsporingsprogramma nu opnieuw uit.</span><span class="sxs-lookup"><span data-stu-id="62981-234">Now, run the debugger again.</span></span> <span data-ttu-id="62981-235">Gebruik eerst de cmdlets en om het huidige onderbrekings punt te verwijderen `Get-PsBreakpoint` `Remove-PsBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="62981-235">First, to delete the current breakpoint, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span> <span data-ttu-id="62981-236">(Als u denkt dat u het onderbrekings punt zou kunnen hergebruiken, gebruikt u de `Disable-PsBreakpoint` cmdlet in plaats van `Remove-PsBreakpoint` .)</span><span class="sxs-lookup"><span data-stu-id="62981-236">(If you think you might reuse the breakpoint, use the `Disable-PsBreakpoint` cmdlet instead of `Remove-PsBreakpoint`.)</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="62981-237">U kunt deze opdracht afkorten tot:</span><span class="sxs-lookup"><span data-stu-id="62981-237">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> gbp | rbp
```

<span data-ttu-id="62981-238">Of voer de opdracht uit door een functie te schrijven, zoals de volgende functie:</span><span class="sxs-lookup"><span data-stu-id="62981-238">Or, run the command by writing a function, such as the following function:</span></span>

```powershell
function delbr { gbp | rbp }
```

<span data-ttu-id="62981-239">Maak nu een onderbrekings punt voor de `$scriptname` variabele.</span><span class="sxs-lookup"><span data-stu-id="62981-239">Now, create a breakpoint on the `$scriptname` variable.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

<span data-ttu-id="62981-240">U kunt de opdracht als volgt afkorten:</span><span class="sxs-lookup"><span data-stu-id="62981-240">You can abbreviate the command as:</span></span>

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

<span data-ttu-id="62981-241">Start nu het script.</span><span class="sxs-lookup"><span data-stu-id="62981-241">Now, start the script.</span></span> <span data-ttu-id="62981-242">Het script bereikt het onderbrekings punt van de variabele.</span><span class="sxs-lookup"><span data-stu-id="62981-242">The script reaches the variable breakpoint.</span></span> <span data-ttu-id="62981-243">De standaard modus is schrijven, dus de uitvoering stopt net vóór de instructie die de waarde van de variabele wijzigt.</span><span class="sxs-lookup"><span data-stu-id="62981-243">The default mode is Write, so execution stops just before the statement that changes the value of the variable.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

<span data-ttu-id="62981-244">De huidige waarde van de variabele weer geven `$scriptName` `$null` .</span><span class="sxs-lookup"><span data-stu-id="62981-244">Display the current value of the `$scriptName` variable, which is `$null`.</span></span>

```powershell
DBG> $scriptName
# DBG>
```

<span data-ttu-id="62981-245">Gebruik een stap opdracht (en) om de instructie uit te voeren waarmee de variabele wordt gevuld.</span><span class="sxs-lookup"><span data-stu-id="62981-245">Use a Step command (s) to execute the statement that populates the variable.</span></span>
<span data-ttu-id="62981-246">Vervolgens wordt de nieuwe waarde van de variabele weer gegeven `$scriptName` .</span><span class="sxs-lookup"><span data-stu-id="62981-246">Then, display the new value of the `$scriptName` variable.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="62981-247">De volgende instructie is een aanroep van de functie PsVersion.</span><span class="sxs-lookup"><span data-stu-id="62981-247">The next statement is a call to the PsVersion function.</span></span> <span data-ttu-id="62981-248">Als u de functie wilt overs Laan, maar nog steeds wilt uitvoeren, gebruikt u een StepOver-opdracht (v).</span><span class="sxs-lookup"><span data-stu-id="62981-248">To skip the function but still execute it, use a StepOver command (v).</span></span> <span data-ttu-id="62981-249">Als u zich al in de functie bevindt wanneer u StepOver gebruikt, is deze niet effectief.</span><span class="sxs-lookup"><span data-stu-id="62981-249">If you are already in the function when you use StepOver, it is not effective.</span></span> <span data-ttu-id="62981-250">De functie aanroep wordt weer gegeven, maar wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="62981-250">The function call is displayed, but it is not executed.</span></span>

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="62981-251">Met de opdracht StepOver wordt de functie uitgevoerd en wordt een voor beeld weer gegeven van de volgende instructie in het script, die de laatste regel afdrukt.</span><span class="sxs-lookup"><span data-stu-id="62981-251">The StepOver command executes the function, and it previews the next statement in the script, which prints the final line.</span></span>

<span data-ttu-id="62981-252">Gebruik een stop opdracht (t) om het fout opsporingsprogramma af te sluiten.</span><span class="sxs-lookup"><span data-stu-id="62981-252">Use a Stop command (t) to exit the debugger.</span></span> <span data-ttu-id="62981-253">De opdracht prompt wordt teruggezet naar de standaard opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="62981-253">The command prompt reverts to the standard command prompt.</span></span>

```powershell
C:\ps-test>
```

<span data-ttu-id="62981-254">Gebruik de cmdlets en om de onderbrekings punten te verwijderen `Get-PsBreakpoint` `Remove-PsBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="62981-254">To delete the breakpoints, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="62981-255">Maak een nieuwe opdracht onderbrekings punt voor de functie PsVersion.</span><span class="sxs-lookup"><span data-stu-id="62981-255">Create a new command breakpoint on the PsVersion function.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

<span data-ttu-id="62981-256">U kunt deze opdracht afkorten tot:</span><span class="sxs-lookup"><span data-stu-id="62981-256">You can abbreviate this command to:</span></span>

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

<span data-ttu-id="62981-257">Voer nu het script uit.</span><span class="sxs-lookup"><span data-stu-id="62981-257">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

<span data-ttu-id="62981-258">Het script bereikt het onderbrekings punt bij de functie aanroep.</span><span class="sxs-lookup"><span data-stu-id="62981-258">The script reaches the breakpoint at the function call.</span></span> <span data-ttu-id="62981-259">De functie is op dit moment nog niet aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="62981-259">At this point, the function has not yet been called.</span></span> <span data-ttu-id="62981-260">Dit biedt u de mogelijkheid om de actie parameter van te gebruiken om voor waarden in te `Set-PSBreakpoint` stellen voor de uitvoering van het onderbrekings punt of om voorbereidende-of diagnose taken uit te voeren, zoals het starten van een logboek of het aanroepen van een diagnose-of beveiligings script.</span><span class="sxs-lookup"><span data-stu-id="62981-260">This gives you the opportunity to use the Action parameter of `Set-PSBreakpoint` to set conditions for the execution of the breakpoint or to perform preparatory or diagnostic tasks, such as starting a log or invoking a diagnostic or security script.</span></span>

<span data-ttu-id="62981-261">Als u een actie wilt instellen, gebruikt u de opdracht door gaan (c) om het script af te sluiten en een `Remove-PsBreakpoint` opdracht om het huidige onderbrekings punt te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="62981-261">To set an action, use a Continue command (c) to exit the script, and a `Remove-PsBreakpoint` command to delete the current breakpoint.</span></span> <span data-ttu-id="62981-262">(Onderbrekings punten zijn alleen-lezen, dus u kunt geen actie aan het huidige onderbrekings punt toevoegen.)</span><span class="sxs-lookup"><span data-stu-id="62981-262">(Breakpoints are read-only, so you cannot add an action to the current breakpoint.)</span></span>

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

<span data-ttu-id="62981-263">Maak nu een nieuwe opdracht onderbrekings punt met een actie.</span><span class="sxs-lookup"><span data-stu-id="62981-263">Now, create a new command breakpoint with an action.</span></span> <span data-ttu-id="62981-264">Met de volgende opdracht wordt een opdracht onderbrekings punt ingesteld met een actie waarmee de waarde van de `$scriptName` variabele wordt geregistreerd wanneer de functie wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="62981-264">The following command sets a command breakpoint with an action that logs the value of the `$scriptName` variable when the function is called.</span></span> <span data-ttu-id="62981-265">Omdat het sleutel woord einde niet wordt gebruikt in de actie, wordt de uitvoering niet gestopt.</span><span class="sxs-lookup"><span data-stu-id="62981-265">Because the Break keyword is not used in the action, execution does not stop.</span></span> <span data-ttu-id="62981-266">(De apostroffen (') is het regel vervolg teken.)</span><span class="sxs-lookup"><span data-stu-id="62981-266">(The backtick (\`) is the line-continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

<span data-ttu-id="62981-267">U kunt ook acties toevoegen die voor waarden voor het onderbrekings punt instellen.</span><span class="sxs-lookup"><span data-stu-id="62981-267">You can also add actions that set conditions for the breakpoint.</span></span> <span data-ttu-id="62981-268">In de volgende opdracht wordt het onderbrekings punt voor opdrachten alleen uitgevoerd als het uitvoerings beleid is ingesteld op RemoteSigned, het meest beperkende beleid dat nog steeds in staat is om scripts uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="62981-268">In the following command, the command breakpoint is executed only if the execution policy is set to RemoteSigned, the most restrictive policy that still permits you to run scripts.</span></span> <span data-ttu-id="62981-269">(De apostroffen (') is het voortzettings teken.)</span><span class="sxs-lookup"><span data-stu-id="62981-269">(The backtick (\`) is the continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

<span data-ttu-id="62981-270">Met het sleutel woord break in de actie wordt het fout opsporingsprogramma doorgestuurd om het onderbrekings punt uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="62981-270">The Break keyword in the action directs the debugger to execute the breakpoint.</span></span>
<span data-ttu-id="62981-271">U kunt ook het sleutel woord continue gebruiken om het fout opsporingsprogramma te laten uitvoeren zonder te verbreken.</span><span class="sxs-lookup"><span data-stu-id="62981-271">You can also use the Continue keyword to direct the debugger to execute without breaking.</span></span> <span data-ttu-id="62981-272">Omdat het sleutel woord default wordt voortgezet, moet u onderbreken opgeven om de uitvoering te stoppen.</span><span class="sxs-lookup"><span data-stu-id="62981-272">Because the default keyword is Continue, you must specify Break to stop execution.</span></span>

<span data-ttu-id="62981-273">Voer nu het script uit.</span><span class="sxs-lookup"><span data-stu-id="62981-273">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

<span data-ttu-id="62981-274">Omdat het uitvoerings beleid is ingesteld op **RemoteSigned** , wordt de uitvoering gestopt bij de functie aanroep.</span><span class="sxs-lookup"><span data-stu-id="62981-274">Because the execution policy is set to **RemoteSigned** , execution stops at the function call.</span></span>

<span data-ttu-id="62981-275">Op dit moment kunt u de aanroep stack controleren.</span><span class="sxs-lookup"><span data-stu-id="62981-275">At this point, you might want to check the call stack.</span></span> <span data-ttu-id="62981-276">Gebruik de `Get-PsCallStack` cmdlet of de `Get-PsCallStack` debugger opdracht (k).</span><span class="sxs-lookup"><span data-stu-id="62981-276">Use the `Get-PsCallStack` cmdlet or the `Get-PsCallStack` debugger command (k).</span></span> <span data-ttu-id="62981-277">Met de volgende opdracht wordt de huidige aanroep stack opgehaald.</span><span class="sxs-lookup"><span data-stu-id="62981-277">The following command gets the current call stack.</span></span>

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

<span data-ttu-id="62981-278">In dit voor beeld ziet u slechts enkele van de vele manieren waarop u het Power Shell-fout opsporingsprogramma kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="62981-278">This example demonstrates just a few of the many ways to use the PowerShell debugger.</span></span>

<span data-ttu-id="62981-279">Voor meer informatie over de cmdlets voor fout opsporing typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="62981-279">For more information about the debugger cmdlets, type the following command:</span></span>

```powershell
help <cmdlet-name> -full
```

<span data-ttu-id="62981-280">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="62981-280">For example, type:</span></span>

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a><span data-ttu-id="62981-281">Andere functies voor fout opsporing in Power shell</span><span class="sxs-lookup"><span data-stu-id="62981-281">Other Debugging Features in PowerShell</span></span>

<span data-ttu-id="62981-282">Naast de Power Shell-fout opsporing bevat Power shell diverse andere functies die u kunt gebruiken om fouten in scripts en functies op te sporen.</span><span class="sxs-lookup"><span data-stu-id="62981-282">In addition to the PowerShell debugger, PowerShell includes several other features that you can use to debug scripts and functions.</span></span>

- <span data-ttu-id="62981-283">Windows PowerShell ISE bevat een interactief grafisch fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="62981-283">Windows PowerShell ISE includes an interactive graphical debugger.</span></span> <span data-ttu-id="62981-284">Start Windows PowerShell ISE en druk op F1 voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="62981-284">For more information, start Windows PowerShell ISE and press F1.</span></span>

- <span data-ttu-id="62981-285">De `Set-PSDebug` cmdlet biedt zeer eenvoudige script functies voor fout opsporing, waaronder steping en tracering.</span><span class="sxs-lookup"><span data-stu-id="62981-285">The `Set-PSDebug` cmdlet offers very basic script debugging features, including stepping and tracing.</span></span>

- <span data-ttu-id="62981-286">Gebruik de `Set-StrictMode` cmdlet voor het detecteren van verwijzingen naar niet-geïnitialiseerde variabelen, verwijzingen naar niet-bestaande eigenschappen van een object en de syntaxis van de functie die ongeldig is.</span><span class="sxs-lookup"><span data-stu-id="62981-286">Use the `Set-StrictMode` cmdlet to detect references to uninitialized variables, to references to non-existent properties of an object, and to function syntax that is not valid.</span></span>

- <span data-ttu-id="62981-287">Voeg diagnostische instructies toe aan een script, zoals instructies voor het weer geven van de waarde van variabelen, instructies die invoer lezen van de opdracht regel of instructies die de huidige instructie rapporteren.</span><span class="sxs-lookup"><span data-stu-id="62981-287">Add diagnostic statements to a script, such as statements that display the value of variables, statements that read input from the command line, or statements that report the current instruction.</span></span> <span data-ttu-id="62981-288">Gebruik de cmdlets die de schrijf bewerking voor deze taak bevatten, zoals `Write-Host` ,, `Write-Debug` en `Write-Warning` `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="62981-288">Use the cmdlets that contain the Write verb for this task, such as `Write-Host`, `Write-Debug`, `Write-Warning`, and `Write-Verbose`.</span></span>

## <a name="see-also"></a><span data-ttu-id="62981-289">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="62981-289">SEE ALSO</span></span>

- [<span data-ttu-id="62981-290">Disable-PsBreakpoint</span><span class="sxs-lookup"><span data-stu-id="62981-290">Disable-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [<span data-ttu-id="62981-291">Enable-PsBreakpoint</span><span class="sxs-lookup"><span data-stu-id="62981-291">Enable-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [<span data-ttu-id="62981-292">Get-PsBreakpoint</span><span class="sxs-lookup"><span data-stu-id="62981-292">Get-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [<span data-ttu-id="62981-293">Get-PsCallStack</span><span class="sxs-lookup"><span data-stu-id="62981-293">Get-PsCallStack</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [<span data-ttu-id="62981-294">Remove-PsBreakpoint</span><span class="sxs-lookup"><span data-stu-id="62981-294">Remove-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [<span data-ttu-id="62981-295">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="62981-295">Set-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [<span data-ttu-id="62981-296">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="62981-296">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="62981-297">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="62981-297">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
