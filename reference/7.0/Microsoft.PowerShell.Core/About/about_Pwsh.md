---
description: Hierin wordt uitgelegd hoe u de `pwsh` opdracht regel interface gebruikt. Hiermee worden de opdracht regel parameters weer gegeven en wordt de syntaxis beschreven.
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: 25ccb20a4c19a9519bf9d2a518ef6187c2327323
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692696"
---
# <a name="about-pwsh"></a><span data-ttu-id="84c49-104">Over pwsh</span><span class="sxs-lookup"><span data-stu-id="84c49-104">About pwsh</span></span>

## <a name="short-description"></a><span data-ttu-id="84c49-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="84c49-105">Short Description</span></span>
<span data-ttu-id="84c49-106">Hierin wordt uitgelegd hoe u de `pwsh` opdracht regel interface gebruikt.</span><span class="sxs-lookup"><span data-stu-id="84c49-106">Explains how to use the `pwsh` command-line interface.</span></span> <span data-ttu-id="84c49-107">Hiermee worden de opdracht regel parameters weer gegeven en wordt de syntaxis beschreven.</span><span class="sxs-lookup"><span data-stu-id="84c49-107">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="84c49-108">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="84c49-108">Long Description</span></span>

## <a name="syntax"></a><span data-ttu-id="84c49-109">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="84c49-109">Syntax</span></span>

```
pwsh[.exe]
   [[-File] <filePath> [args]]
   [-Command { - | <script-block> [-args <arg-array>]
                 | <string> [<CommandParameters>] } ]
   [-ConfigurationName <string>]
   [-CustomPipeName <string>]
   [-EncodedCommand <Base64EncodedCommand>]
   [-ExecutionPolicy <ExecutionPolicy>]
   [-InputFormat {Text | XML}]
   [-Interactive]
   [-Login]
   [-MTA]
   [-NoExit]
   [-NoLogo]
   [-NonInteractive]
   [-NoProfile]
   [-OutputFormat {Text | XML}]
   [-SettingsFile <SettingsFilePath>]
   [-SSHServerMode]
   [-STA]
   [-Version]
   [-WindowStyle <style>]
   [-WorkingDirectory <directoryPath>]

pwsh[.exe] -h | -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="84c49-110">Parameters</span><span class="sxs-lookup"><span data-stu-id="84c49-110">Parameters</span></span>

<span data-ttu-id="84c49-111">Alle para meters zijn hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="84c49-111">All parameters are case-insensitive.</span></span>

### <a name="-file---f"></a><span data-ttu-id="84c49-112">-Bestand | -f</span><span class="sxs-lookup"><span data-stu-id="84c49-112">-File | -f</span></span>

<span data-ttu-id="84c49-113">Als de waarde van `File` is `-` , wordt de opdracht tekst gelezen uit de standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="84c49-113">If the value of `File` is `-`, the command text is read from standard input.</span></span>
<span data-ttu-id="84c49-114">Als u `pwsh -File -` zonder omgeleide standaard invoer uitvoert, wordt een reguliere sessie gestart.</span><span class="sxs-lookup"><span data-stu-id="84c49-114">Running `pwsh -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="84c49-115">Dit is hetzelfde als het niet opgeven `File` van de para meter.</span><span class="sxs-lookup"><span data-stu-id="84c49-115">This is the same as not specifying the `File` parameter at all.</span></span>

<span data-ttu-id="84c49-116">Dit is de standaard parameter als er geen para meters aanwezig zijn, maar waarden wel aanwezig zijn in de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="84c49-116">This is the default parameter if no parameters are present but values are present in the command line.</span></span> <span data-ttu-id="84c49-117">Het opgegeven script wordt uitgevoerd in het lokale bereik (' dot-sourced '), zodat de functies en variabelen die het script maakt, beschikbaar zijn in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="84c49-117">The specified script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="84c49-118">Voer het pad naar het script bestand en eventuele para meters in.</span><span class="sxs-lookup"><span data-stu-id="84c49-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="84c49-119">Het bestand moet de laatste para meter in de opdracht zijn, omdat alle tekens die na de naam van de bestands parameter worden getypt, worden geïnterpreteerd als het pad naar het script bestand, gevolgd door de script parameters.</span><span class="sxs-lookup"><span data-stu-id="84c49-119">File must be the last parameter in the command, because all characters typed after the File parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="84c49-120">Normaal gesp roken worden de switch parameters van een script opgenomen of wegge laten.</span><span class="sxs-lookup"><span data-stu-id="84c49-120">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="84c49-121">Met de volgende opdracht wordt bijvoorbeeld de para meter all van het Get-Script.ps1 script bestand gebruikt: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="84c49-121">For example, the following command uses the All parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="84c49-122">In zeldzame gevallen moet u mogelijk een **Booleaanse** waarde voor een switch parameter opgeven.</span><span class="sxs-lookup"><span data-stu-id="84c49-122">In rare cases, you might need to provide a **Boolean** value for a switch parameter.</span></span> <span data-ttu-id="84c49-123">Als u een **Boole** -waarde voor een para meter switch wilt opgeven in de waarde van de **Bestands** parameter, gebruikt u de para meter normaal gesp roken onmiddellijk gevolgd door een dubbele punt en de Booleaanse waarde, zoals de volgende: `-File .\Get-Script.ps1 -All:$False` .</span><span class="sxs-lookup"><span data-stu-id="84c49-123">To provide a **Boolean** value for a switch parameter in the value of the **File** parameter, Use the parameter normally followed immediately by a colon and the boolean value, such as the following: `-File .\Get-Script.ps1 -All:$False`.</span></span>

<span data-ttu-id="84c49-124">Para meters die aan het script worden door gegeven, worden als letterlijke teken reeksen door gegeven na de interpretatie van de huidige shell.</span><span class="sxs-lookup"><span data-stu-id="84c49-124">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="84c49-125">Als u bijvoorbeeld in bent `cmd.exe` en een waarde voor een omgevings variabele wilt door geven, gebruikt u de volgende `cmd.exe` syntaxis: `pwsh -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="84c49-125">For example, if you are in `cmd.exe` and want to pass an environment variable value, you would use the `cmd.exe` syntax: `pwsh -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="84c49-126">In daarentegen wordt `pwsh -File .\test.ps1 -TestParam $env:windir` de `cmd.exe` letterlijke teken reeks ontvangen in resultaten van het script `$env:windir` omdat het geen speciale betekenis heeft voor de huidige `cmd.exe` shell.</span><span class="sxs-lookup"><span data-stu-id="84c49-126">In contrast, running `pwsh -File .\test.ps1 -TestParam $env:windir` in `cmd.exe` results in the script receiving the literal string `$env:windir` because it has no special meaning to the current `cmd.exe` shell.</span></span> <span data-ttu-id="84c49-127">De `$env:windir` stijl van de verwijzing naar een omgevings variabele _kan_ worden gebruikt binnen een **opdracht** parameter, omdat deze wordt geïnterpreteerd als Power shell-code.</span><span class="sxs-lookup"><span data-stu-id="84c49-127">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it is interpreted as PowerShell code.</span></span>

<span data-ttu-id="84c49-128">Als u dezelfde opdracht uit een _batch script_ wilt uitvoeren, gebruikt u `%~dp0` in plaats van `.\` of `$PSScriptRoot` om de huidige uitvoerings Directory te vertegenwoordigen: `pwsh -File %~dp0test.ps1 -TestParam %windir%` .</span><span class="sxs-lookup"><span data-stu-id="84c49-128">Similarly, if you want to execute the same command from a _Batch script_, you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `pwsh -File %~dp0test.ps1 -TestParam %windir%`.</span></span> <span data-ttu-id="84c49-129">Als u in plaats daarvan gebruikt `.\test.ps1` , genereert Power shell een fout omdat het letterlijke pad niet kan worden gevonden `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="84c49-129">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="84c49-130">Wanneer het script bestand met een `exit` opdracht wordt beëindigd, wordt de afsluit code van het proces ingesteld op het numerieke argument dat met de opdracht wordt gebruikt `exit` .</span><span class="sxs-lookup"><span data-stu-id="84c49-130">When the script file terminates with an `exit` command, the process exit code is set to the numeric argument used with the `exit` command.</span></span> <span data-ttu-id="84c49-131">Bij normale beëindiging is de afsluit code altijd `0` .</span><span class="sxs-lookup"><span data-stu-id="84c49-131">With normal termination, the exit code is always `0`.</span></span>

<span data-ttu-id="84c49-132">Net als bij `-Command` het beëindigen van een script wordt de afsluit code ingesteld op `1` .</span><span class="sxs-lookup"><span data-stu-id="84c49-132">Similar to `-Command`, when a script-terminating error occurs, the exit code is set to `1`.</span></span> <span data-ttu-id="84c49-133">Maar in tegens telling tot `-Command` , wanneer de uitvoering wordt onderbroken met <kbd>CTRL</kbd> - <kbd>C</kbd> , is de afsluit code `0` .</span><span class="sxs-lookup"><span data-stu-id="84c49-133">However, unlike with `-Command`, when the execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd> the exit code is `0`.</span></span>

### <a name="-command---c"></a><span data-ttu-id="84c49-134">-Opdracht | -c</span><span class="sxs-lookup"><span data-stu-id="84c49-134">-Command | -c</span></span>

<span data-ttu-id="84c49-135">Hiermee worden de opgegeven opdrachten (en eventuele para meters) uitgevoerd alsof ze zijn getypt bij de Power shell-opdracht prompt en vervolgens afgesloten, tenzij de `NoExit` para meter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="84c49-135">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="84c49-136">De waarde van de **opdracht** kan `-` een script blok of een teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="84c49-136">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="84c49-137">Als de waarde van de **opdracht** is `-` , wordt de opdracht tekst gelezen uit de standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="84c49-137">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="84c49-138">De **opdracht** parameter accepteert alleen een script blok voor uitvoering wanneer het de **waarde die wordt door gegeven, kan** herkennen als een **script Block** -type.</span><span class="sxs-lookup"><span data-stu-id="84c49-138">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="84c49-139">Dit kan _alleen_ worden uitgevoerd `pwsh` vanuit een andere Power shell-host.</span><span class="sxs-lookup"><span data-stu-id="84c49-139">This is _only_ possible when running `pwsh` from another PowerShell host.</span></span> <span data-ttu-id="84c49-140">Het type **script Block** kan worden opgenomen in een bestaande variabele, geretourneerd vanuit een expressie, of door de Power shell-host geparseerd als een letterlijk script blok tussen accolades ( `{}` ) voordat het wordt door gegeven aan `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="84c49-140">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `pwsh`.</span></span>

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="84c49-141">In `cmd.exe` is er geen script blok (of **script Block** -type), dus de waarde die is door gegeven aan de **opdracht** , is _altijd_ een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="84c49-141">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="84c49-142">U kunt een script blok schrijven in de teken reeks, maar in plaats van dat het wordt uitgevoerd, werkt het niet exact alsof u het hebt getypt bij een typische Power shell-prompt, waarbij de inhoud van het script blok wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="84c49-142">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="84c49-143">Een teken reeks die aan de **opdracht** is door gegeven, wordt nog steeds uitgevoerd als Power shell-code, dus de accolades voor het blok keren van een script zijn in de eerste plaats vaak niet vereist tijdens de uitvoering van `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="84c49-143">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="84c49-144">Voor het uitvoeren van een inline-script blok dat in een teken reeks is gedefinieerd, kan de [aanroep operator](about_operators.md#special-operators) `&` worden gebruikt:</span><span class="sxs-lookup"><span data-stu-id="84c49-144">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="84c49-145">Als de waarde van de **opdracht** een teken reeks is, moet de **opdracht** de laatste para meter zijn voor pwsh, omdat alle argumenten die deze bevat, worden geïnterpreteerd als onderdeel van de opdracht die moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="84c49-145">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="84c49-146">Bij het aanroepen vanuit een bestaande Power shell-sessie worden de resultaten geretourneerd naar de bovenliggende shell als gedeserialiseerd XML-objecten, niet live-objecten.</span><span class="sxs-lookup"><span data-stu-id="84c49-146">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="84c49-147">Voor andere shells worden de resultaten geretourneerd als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="84c49-147">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="84c49-148">Als de waarde van de **opdracht** is `-` , wordt de opdracht tekst gelezen uit de standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="84c49-148">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="84c49-149">U moet de standaard invoer omleiden wanneer u de **opdracht** parameter gebruikt met standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="84c49-149">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="84c49-150">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="84c49-150">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="84c49-151">In dit voor beeld wordt de volgende uitvoer gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="84c49-151">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="84c49-152">De afsluit code van het proces wordt bepaald door de status van de laatste (uitgevoerde) opdracht in het-script blok.</span><span class="sxs-lookup"><span data-stu-id="84c49-152">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="84c49-153">De afsluit code is `0` `$?` `$true` of wanneer dat `1` `$?` zo is `$false` .</span><span class="sxs-lookup"><span data-stu-id="84c49-153">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="84c49-154">Als de laatste opdracht een extern programma of een Power shell-script is waarmee expliciet een andere afsluit code dan of wordt ingesteld `0` `1` , wordt die afsluit code geconverteerd naar `1` voor de afsluit code van het proces.</span><span class="sxs-lookup"><span data-stu-id="84c49-154">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="84c49-155">Als u de specifieke afsluit code wilt behouden, voegt `exit $LASTEXITCODE` u toe aan de opdracht reeks of het script blok.</span><span class="sxs-lookup"><span data-stu-id="84c49-155">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="84c49-156">Op dezelfde manier wordt de waarde 1 geretourneerd als er een fout optreedt bij het beëindigen van een script (runs, afgebroken), zoals een `throw` of `-ErrorAction Stop` , wanneer de uitvoering wordt onderbroken door <kbd>CTRL</kbd> - <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="84c49-156">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

### <a name="-configurationname---config"></a><span data-ttu-id="84c49-157">-Configuratiepad | -config</span><span class="sxs-lookup"><span data-stu-id="84c49-157">-ConfigurationName | -config</span></span>

<span data-ttu-id="84c49-158">Hiermee geeft u een configuratie-eind punt waarin Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="84c49-158">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="84c49-159">Dit kan elk eind punt zijn dat is geregistreerd op de lokale computer, met inbegrip van de standaard externe communicatie-eind punten in Power shell of een aangepast eind punt met specifieke mogelijkheden voor de gebruikersrol.</span><span class="sxs-lookup"><span data-stu-id="84c49-159">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

<span data-ttu-id="84c49-160">Voorbeeld: `pwsh -ConfigurationName AdminRoles`</span><span class="sxs-lookup"><span data-stu-id="84c49-160">Example: `pwsh -ConfigurationName AdminRoles`</span></span>

### <a name="-custompipename"></a><span data-ttu-id="84c49-161">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="84c49-161">-CustomPipeName</span></span>

<span data-ttu-id="84c49-162">Hiermee geeft u de naam op die moet worden gebruikt voor een extra IPC-server (named pipe) die wordt gebruikt voor fout opsporing en andere communicatie tussen processen.</span><span class="sxs-lookup"><span data-stu-id="84c49-162">Specifies the name to use for an additional IPC server (named pipe) used for debugging and other cross-process communication.</span></span> <span data-ttu-id="84c49-163">Dit biedt een voorspelbaar mechanisme om verbinding te maken met andere Power shell-exemplaren.</span><span class="sxs-lookup"><span data-stu-id="84c49-163">This offers a predictable mechanism for connecting to other PowerShell instances.</span></span> <span data-ttu-id="84c49-164">Wordt meestal gebruikt met de para meter **CustomPipeName** op `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="84c49-164">Typically used with the **CustomPipeName** parameter on `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="84c49-165">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="84c49-165">This parameter was introduced in PowerShell 6.2.</span></span>

<span data-ttu-id="84c49-166">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="84c49-166">For example:</span></span>

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a><span data-ttu-id="84c49-167">-EncodedCommand | -e | -EG</span><span class="sxs-lookup"><span data-stu-id="84c49-167">-EncodedCommand | -e | -ec</span></span>

<span data-ttu-id="84c49-168">Hiermee wordt een met base64 gecodeerde teken reeks versie van een opdracht geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="84c49-168">Accepts a Base64-encoded string version of a command.</span></span> <span data-ttu-id="84c49-169">Gebruik deze para meter voor het verzenden van opdrachten naar Power shell waarvoor complexe, geneste aanhalings tekens zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="84c49-169">Use this parameter to submit commands to PowerShell that require complex, nested quoting.</span></span> <span data-ttu-id="84c49-170">De base64-weer gave moet een gecodeerde teken reeks met UTF-16LE zijn.</span><span class="sxs-lookup"><span data-stu-id="84c49-170">The Base64 representation must be a UTF-16LE encoded string.</span></span>

<span data-ttu-id="84c49-171">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="84c49-171">For example:</span></span>

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a><span data-ttu-id="84c49-172">-ExecutionPolicy | -ex | -EP</span><span class="sxs-lookup"><span data-stu-id="84c49-172">-ExecutionPolicy | -ex | -ep</span></span>

<span data-ttu-id="84c49-173">Hiermee stelt u het standaard uitvoerings beleid voor de huidige sessie en slaat u deze op in de `$env:PSExecutionPolicyPreference` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="84c49-173">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="84c49-174">Met deze para meter wordt het permanent geconfigureerde uitvoerings beleid niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="84c49-174">This parameter does not change the persistently configured execution policies.</span></span>

<span data-ttu-id="84c49-175">Deze para meter is alleen van toepassing op Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="84c49-175">This parameter only applies to Windows computers.</span></span> <span data-ttu-id="84c49-176">De `$env:PSExecutionPolicyPreference` omgevings variabele bestaat niet op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="84c49-176">The `$env:PSExecutionPolicyPreference` environment variable does not exist on non-Windows platforms.</span></span>

### <a name="-inputformat---inp---if"></a><span data-ttu-id="84c49-177">-InputFormat | -INP | -Als</span><span class="sxs-lookup"><span data-stu-id="84c49-177">-InputFormat | -inp | -if</span></span>

<span data-ttu-id="84c49-178">Beschrijft de indeling van gegevens die naar Power shell worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="84c49-178">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="84c49-179">Geldige waarden zijn ' text ' (tekst reeksen) of ' XML ' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="84c49-179">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-interactive---i"></a><span data-ttu-id="84c49-180">-Interactief | -i</span><span class="sxs-lookup"><span data-stu-id="84c49-180">-Interactive | -i</span></span>

<span data-ttu-id="84c49-181">Presenteer een interactieve prompt aan de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="84c49-181">Present an interactive prompt to the user.</span></span> <span data-ttu-id="84c49-182">Inverse voor niet-interactieve para meter.</span><span class="sxs-lookup"><span data-stu-id="84c49-182">Inverse for NonInteractive parameter.</span></span>

### <a name="-login---l"></a><span data-ttu-id="84c49-183">-Aanmelden | -l</span><span class="sxs-lookup"><span data-stu-id="84c49-183">-Login | -l</span></span>

<span data-ttu-id="84c49-184">In Linux en macOS wordt Power shell gestart als een aanmeldings shell, met behulp van/bin/sh om aanmeldings profielen, zoals/etc/profile en ~/.profile., uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="84c49-184">On Linux and macOS, starts PowerShell as a login shell, using /bin/sh to execute login profiles such as /etc/profile and ~/.profile.</span></span>
<span data-ttu-id="84c49-185">In Windows heeft deze switch niets.</span><span class="sxs-lookup"><span data-stu-id="84c49-185">On Windows, this switch does nothing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84c49-186">Deze para meter moet eerst worden gestart om Power shell als een aanmeldings shell te starten.</span><span class="sxs-lookup"><span data-stu-id="84c49-186">This parameter must come first to start PowerShell as a login shell.</span></span>
> <span data-ttu-id="84c49-187">Als deze para meter op een andere positie wordt door gegeven, wordt dit genegeerd.</span><span class="sxs-lookup"><span data-stu-id="84c49-187">Passing this parameter in another position will be ignored.</span></span>

<span data-ttu-id="84c49-188">Instellen `pwsh` als de aanmeldings shell op UNIX-achtige besturings systemen:</span><span class="sxs-lookup"><span data-stu-id="84c49-188">To set up `pwsh` as the login shell on UNIX-like operating systems:</span></span>

- <span data-ttu-id="84c49-189">Controleer of het volledige absolute pad naar `pwsh` wordt vermeld onder `/etc/shells`</span><span class="sxs-lookup"><span data-stu-id="84c49-189">Verify that the full absolute path to `pwsh` is listed under `/etc/shells`</span></span>
  - <span data-ttu-id="84c49-190">Dit pad is doorgaans iets zoals `/usr/bin/pwsh` in Linux of `/usr/local/bin/pwsh` op macOS</span><span class="sxs-lookup"><span data-stu-id="84c49-190">This path is usually something like `/usr/bin/pwsh` on Linux or `/usr/local/bin/pwsh` on macOS</span></span>
  - <span data-ttu-id="84c49-191">Bij sommige installatie methoden wordt deze vermelding tijdens de installatie automatisch toegevoegd</span><span class="sxs-lookup"><span data-stu-id="84c49-191">With some installation methods, this entry will be added automatically at installation time</span></span>
  - <span data-ttu-id="84c49-192">Als `pwsh` niet aanwezig is in `/etc/shells` , gebruikt u een editor om het pad toe te voegen aan `pwsh` op de laatste regel.</span><span class="sxs-lookup"><span data-stu-id="84c49-192">If `pwsh` is not present in `/etc/shells`, use an editor to append the path to `pwsh` on the last line.</span></span> <span data-ttu-id="84c49-193">Hiervoor zijn verhoogde bevoegdheden vereist om te bewerken.</span><span class="sxs-lookup"><span data-stu-id="84c49-193">This requires elevated privileges to edit.</span></span>
- <span data-ttu-id="84c49-194">Gebruik het hulp programma [chsh](https://linux.die.net/man/1/chsh) om de shell van uw huidige gebruiker in te stellen op `pwsh` :</span><span class="sxs-lookup"><span data-stu-id="84c49-194">Use the [chsh](https://linux.die.net/man/1/chsh) utility to set your current user's shell to `pwsh`:</span></span>

  ```sh
  chsh -s /usr/bin/pwsh
  ```

> [!WARNING]
> <span data-ttu-id="84c49-195">`pwsh`Het instellen van de aanmeldings shell wordt momenteel niet ondersteund op het Windows-subsysteem voor Linux (WSL), en het instellen van `pwsh` de aanmeldings shell kan ertoe leiden dat WSL niet interactief kan worden gestart.</span><span class="sxs-lookup"><span data-stu-id="84c49-195">Setting `pwsh` as the login shell is currently not supported on Windows Subsystem for Linux (WSL), and attempting to set `pwsh` as the login shell there may lead to being unable to start WSL interactively.</span></span>

### <a name="-mta"></a><span data-ttu-id="84c49-196">-MTA</span><span class="sxs-lookup"><span data-stu-id="84c49-196">-MTA</span></span>

<span data-ttu-id="84c49-197">Start Power shell met een Apartment met meerdere threads.</span><span class="sxs-lookup"><span data-stu-id="84c49-197">Start PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="84c49-198">Deze schakel optie is alleen beschikbaar in Windows.</span><span class="sxs-lookup"><span data-stu-id="84c49-198">This switch is only available on Windows.</span></span>

### <a name="-noexit---noe"></a><span data-ttu-id="84c49-199">-Niet afsluiten | -noe</span><span class="sxs-lookup"><span data-stu-id="84c49-199">-NoExit | -noe</span></span>

<span data-ttu-id="84c49-200">Wordt niet afgesloten na het uitvoeren van opstart opdrachten.</span><span class="sxs-lookup"><span data-stu-id="84c49-200">Does not exit after running startup commands.</span></span>

<span data-ttu-id="84c49-201">Voorbeeld: `pwsh -NoExit -Command Get-Date`</span><span class="sxs-lookup"><span data-stu-id="84c49-201">Example: `pwsh -NoExit -Command Get-Date`</span></span>

### <a name="-nologo---nol"></a><span data-ttu-id="84c49-202">-Logo | -nol</span><span class="sxs-lookup"><span data-stu-id="84c49-202">-NoLogo | -nol</span></span>

<span data-ttu-id="84c49-203">Hiermee verbergt u het copyright banner bij het opstarten van interactieve sessies.</span><span class="sxs-lookup"><span data-stu-id="84c49-203">Hides the copyright banner at startup of interactive sessions.</span></span>

### <a name="-noninteractive---noni"></a><span data-ttu-id="84c49-204">-Niet-interactief | -noni</span><span class="sxs-lookup"><span data-stu-id="84c49-204">-NonInteractive | -noni</span></span>

<span data-ttu-id="84c49-205">Er wordt geen interactieve prompt voor de gebruiker weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="84c49-205">Does not present an interactive prompt to the user.</span></span> <span data-ttu-id="84c49-206">Alle pogingen om interactieve functies, zoals `Read-Host` of bevestigings prompts, te gebruiken, resulteren in instructie-Terminate-fouten.</span><span class="sxs-lookup"><span data-stu-id="84c49-206">Any attempts to use interactive features, like `Read-Host` or confirmation prompts, result in statement-terminating errors.</span></span>

### <a name="-noprofile---nop"></a><span data-ttu-id="84c49-207">-Profile | -NOP</span><span class="sxs-lookup"><span data-stu-id="84c49-207">-NoProfile | -nop</span></span>

<span data-ttu-id="84c49-208">Laadt de Power shell-profielen niet.</span><span class="sxs-lookup"><span data-stu-id="84c49-208">Does not load the PowerShell profiles.</span></span>

### <a name="-outputformat---o---of"></a><span data-ttu-id="84c49-209">-Output Format | -o | -van</span><span class="sxs-lookup"><span data-stu-id="84c49-209">-OutputFormat | -o | -of</span></span>

<span data-ttu-id="84c49-210">Hiermee wordt bepaald hoe de uitvoer van Power shell wordt opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="84c49-210">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="84c49-211">Geldige waarden zijn ' text ' (tekst reeksen) of ' XML ' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="84c49-211">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

<span data-ttu-id="84c49-212">Voorbeeld: `pwsh -o XML -c Get-Date`</span><span class="sxs-lookup"><span data-stu-id="84c49-212">Example: `pwsh -o XML -c Get-Date`</span></span>

<span data-ttu-id="84c49-213">Wanneer u een Power shell-sessie aanroept, haalt u objecten op die zijn gedeserialiseerd als uitvoer in plaats van gewone teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="84c49-213">When called withing a PowerShell session, you get deserialized objects as output rather plain strings.</span></span> <span data-ttu-id="84c49-214">Bij het aanroepen van andere shells is de uitvoer teken reeks gegevens die zijn opgemaakt als CLIXML-tekst.</span><span class="sxs-lookup"><span data-stu-id="84c49-214">When called from other shells, the output is string data formatted as CLIXML text.</span></span>

### <a name="-settingsfile---settings"></a><span data-ttu-id="84c49-215">-SettingsFile | -instellingen</span><span class="sxs-lookup"><span data-stu-id="84c49-215">-SettingsFile | -settings</span></span>

<span data-ttu-id="84c49-216">Onderdrukt het `powershell.config.json` instellingen bestand voor het hele systeem voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="84c49-216">Overrides the system-wide `powershell.config.json` settings file for the session.</span></span> <span data-ttu-id="84c49-217">Standaard worden de instellingen voor het hele systeem gelezen van de `powershell.config.json` in de `$PSHOME` map.</span><span class="sxs-lookup"><span data-stu-id="84c49-217">By default, system-wide settings are read from the `powershell.config.json` in the `$PSHOME` directory.</span></span>

<span data-ttu-id="84c49-218">Houd er rekening mee dat deze instellingen niet worden gebruikt door het eind punt dat is opgegeven door het `-ConfigurationName` argument.</span><span class="sxs-lookup"><span data-stu-id="84c49-218">Note that these settings are not used by the endpoint specified by the `-ConfigurationName` argument.</span></span>

<span data-ttu-id="84c49-219">Voorbeeld: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span><span class="sxs-lookup"><span data-stu-id="84c49-219">Example: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span></span>

### <a name="-sshservermode---sshs"></a><span data-ttu-id="84c49-220">-SSHServerMode | -sshs</span><span class="sxs-lookup"><span data-stu-id="84c49-220">-SSHServerMode | -sshs</span></span>

<span data-ttu-id="84c49-221">Wordt gebruikt in sshd_config voor het uitvoeren van Power shell als een SSH-subsysteem.</span><span class="sxs-lookup"><span data-stu-id="84c49-221">Used in sshd_config for running PowerShell as an SSH subsystem.</span></span> <span data-ttu-id="84c49-222">Het is niet bedoeld of wordt niet ondersteund voor andere gebruik.</span><span class="sxs-lookup"><span data-stu-id="84c49-222">It is not intended or supported for any other use.</span></span>

### <a name="-sta"></a><span data-ttu-id="84c49-223">-STA</span><span class="sxs-lookup"><span data-stu-id="84c49-223">-STA</span></span>

<span data-ttu-id="84c49-224">Start Power shell met een Apartment met één thread.</span><span class="sxs-lookup"><span data-stu-id="84c49-224">Start PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="84c49-225">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="84c49-225">This is the default.</span></span> <span data-ttu-id="84c49-226">Deze schakel optie is alleen beschikbaar in Windows.</span><span class="sxs-lookup"><span data-stu-id="84c49-226">This switch is only available on Windows.</span></span>

### <a name="-version---v"></a><span data-ttu-id="84c49-227">-Versie | -v</span><span class="sxs-lookup"><span data-stu-id="84c49-227">-Version | -v</span></span>

<span data-ttu-id="84c49-228">Hiermee wordt de versie van Power shell weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="84c49-228">Displays the version of PowerShell.</span></span> <span data-ttu-id="84c49-229">Aanvullende para meters worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="84c49-229">Additional parameters are ignored.</span></span>

### <a name="-windowstyle---w"></a><span data-ttu-id="84c49-230">-WindowStyle | -w</span><span class="sxs-lookup"><span data-stu-id="84c49-230">-WindowStyle | -w</span></span>

<span data-ttu-id="84c49-231">Hiermee stelt u de venster stijl voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="84c49-231">Sets the window style for the session.</span></span> <span data-ttu-id="84c49-232">Geldige waarden zijn normaal, geminimaliseerd, gemaximaliseerd en verborgen.</span><span class="sxs-lookup"><span data-stu-id="84c49-232">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-workingdirectory---wd"></a><span data-ttu-id="84c49-233">-Variabele workingdirectory | -WD</span><span class="sxs-lookup"><span data-stu-id="84c49-233">-WorkingDirectory | -wd</span></span>

<span data-ttu-id="84c49-234">Hiermee stelt u de oorspronkelijke werkmap in door tijdens het opstarten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="84c49-234">Sets the initial working directory by executing at startup.</span></span> <span data-ttu-id="84c49-235">Een geldig pad naar een Power shell-bestand wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="84c49-235">Any valid PowerShell file path is supported.</span></span>

<span data-ttu-id="84c49-236">Als u Power shell in uw basismap wilt starten, gebruikt u: `pwsh -WorkingDirectory ~`</span><span class="sxs-lookup"><span data-stu-id="84c49-236">To start PowerShell in your home directory, use: `pwsh -WorkingDirectory ~`</span></span>

### <a name="-help---"></a><span data-ttu-id="84c49-237">-Help,-?,/?</span><span class="sxs-lookup"><span data-stu-id="84c49-237">-Help, -?, /?</span></span>

<span data-ttu-id="84c49-238">Geeft Help weer voor `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="84c49-238">Displays help for `pwsh`.</span></span> <span data-ttu-id="84c49-239">Als u een pwsh-opdracht in Power shell typt, laten voorafgaan door u de opdracht parameters met een koppel teken ( `-` ), niet een slash ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="84c49-239">If you are typing a pwsh command in PowerShell, prepend the command parameters with a hyphen (`-`), not a forward slash (`/`).</span></span>
