---
description: Hierin wordt uitgelegd hoe u de `powershell.exe` opdracht regel interface gebruikt. Hiermee worden de opdracht regel parameters weer gegeven en wordt de syntaxis beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_exe
ms.openlocfilehash: ef03558a6b58868b98c9da488934b0bfbbce9fe7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252762"
---
# <a name="about-powershellexe"></a><span data-ttu-id="25b95-105">Over PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="25b95-105">About PowerShell.exe</span></span>

## <a name="short-description"></a><span data-ttu-id="25b95-106">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="25b95-106">Short Description</span></span>
<span data-ttu-id="25b95-107">Hierin wordt uitgelegd hoe u de `powershell.exe` opdracht regel interface gebruikt.</span><span class="sxs-lookup"><span data-stu-id="25b95-107">Explains how to use the `powershell.exe` command-line interface.</span></span> <span data-ttu-id="25b95-108">Hiermee worden de opdracht regel parameters weer gegeven en wordt de syntaxis beschreven.</span><span class="sxs-lookup"><span data-stu-id="25b95-108">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="25b95-109">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="25b95-109">Long Description</span></span>

### <a name="syntax"></a><span data-ttu-id="25b95-110">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="25b95-110">SYNTAX</span></span>

```
PowerShell[.exe]
    [-PSConsoleFile <file> | -Version <version>]
    [-NoLogo]
    [-NoExit]
    [-Sta]
    [-Mta]
    [-NoProfile]
    [-NonInteractive]
    [-InputFormat {Text | XML}]
    [-OutputFormat {Text | XML}]
    [-WindowStyle <style>]
    [-EncodedCommand <Base64EncodedCommand>]
    [-ConfigurationName <string>]
    [-File - | <filePath> <args>]
    [-ExecutionPolicy <ExecutionPolicy>]
    [-Command - | { <script-block> [-args <arg-array>] }
                | { <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

### <a name="parameters"></a><span data-ttu-id="25b95-111">Parameters</span><span class="sxs-lookup"><span data-stu-id="25b95-111">Parameters</span></span>

#### <a name="-psconsolefile-filepath"></a><span data-ttu-id="25b95-112">-PSConsoleFile \<FilePath\></span><span class="sxs-lookup"><span data-stu-id="25b95-112">-PSConsoleFile \<FilePath\></span></span>

<span data-ttu-id="25b95-113">Hiermee wordt het opgegeven Power shell-console bestand geladen.</span><span class="sxs-lookup"><span data-stu-id="25b95-113">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="25b95-114">Voer het pad en de naam van het console bestand in.</span><span class="sxs-lookup"><span data-stu-id="25b95-114">Enter the path and name of the console file.</span></span> <span data-ttu-id="25b95-115">Gebruik de cmdlet Export-Console in Power shell om een console bestand te maken.</span><span class="sxs-lookup"><span data-stu-id="25b95-115">To create a console file, use the Export-Console cmdlet in PowerShell.</span></span>

#### <a name="-version-powershell-version"></a><span data-ttu-id="25b95-116">-Versie \<PowerShell Version\></span><span class="sxs-lookup"><span data-stu-id="25b95-116">-Version \<PowerShell Version\></span></span>

<span data-ttu-id="25b95-117">Hiermee wordt de opgegeven versie van Power shell gestart.</span><span class="sxs-lookup"><span data-stu-id="25b95-117">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="25b95-118">Geldige waarden zijn 2,0 en 3,0.</span><span class="sxs-lookup"><span data-stu-id="25b95-118">Valid values are 2.0 and 3.0.</span></span> <span data-ttu-id="25b95-119">De versie die u opgeeft, moet op het systeem zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="25b95-119">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="25b95-120">Als Windows Power Shell 3,0 is geïnstalleerd op de computer, is "3,0" de standaard versie.</span><span class="sxs-lookup"><span data-stu-id="25b95-120">If Windows PowerShell 3.0 is installed on the computer, "3.0" is the default version.</span></span>
<span data-ttu-id="25b95-121">Anders is ' 2,0 ' de standaard versie.</span><span class="sxs-lookup"><span data-stu-id="25b95-121">Otherwise, "2.0" is the default version.</span></span> <span data-ttu-id="25b95-122">Zie [Power Shell installeren](/powershell/scripting/install/installing-windows-powershell)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="25b95-122">For more information, see [Installing PowerShell](/powershell/scripting/install/installing-windows-powershell).</span></span>

#### <a name="-nologo"></a><span data-ttu-id="25b95-123">-Logo</span><span class="sxs-lookup"><span data-stu-id="25b95-123">-NoLogo</span></span>

<span data-ttu-id="25b95-124">Hiermee verbergt u het copyright banner bij het opstarten.</span><span class="sxs-lookup"><span data-stu-id="25b95-124">Hides the copyright banner at startup.</span></span>

#### <a name="-noexit"></a><span data-ttu-id="25b95-125">-Outexit</span><span class="sxs-lookup"><span data-stu-id="25b95-125">-NoExit</span></span>

<span data-ttu-id="25b95-126">Wordt niet afgesloten na het uitvoeren van opstart opdrachten.</span><span class="sxs-lookup"><span data-stu-id="25b95-126">Does not exit after running startup commands.</span></span>

#### <a name="-sta"></a><span data-ttu-id="25b95-127">-Sta</span><span class="sxs-lookup"><span data-stu-id="25b95-127">-Sta</span></span>

<span data-ttu-id="25b95-128">Power shell wordt gestart met een Apartment met één thread.</span><span class="sxs-lookup"><span data-stu-id="25b95-128">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="25b95-129">In Windows Power Shell 2,0 is multi-threaded apartment (MTA) de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="25b95-129">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span> <span data-ttu-id="25b95-130">In Windows Power Shell 3,0 is single-threaded apartment (STA) de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="25b95-130">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span>

#### <a name="-mta"></a><span data-ttu-id="25b95-131">-MTA</span><span class="sxs-lookup"><span data-stu-id="25b95-131">-Mta</span></span>

<span data-ttu-id="25b95-132">Power shell wordt gestart met een Apartment met meerdere threads.</span><span class="sxs-lookup"><span data-stu-id="25b95-132">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="25b95-133">Deze para meter wordt geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="25b95-133">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="25b95-134">In Power Shell 2,0 is multi-threaded apartment (MTA) de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="25b95-134">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span> <span data-ttu-id="25b95-135">In Power Shell 3,0 is single-threaded apartment (STA) de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="25b95-135">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span>

#### <a name="-noprofile"></a><span data-ttu-id="25b95-136">-Geen profiel</span><span class="sxs-lookup"><span data-stu-id="25b95-136">-NoProfile</span></span>

<span data-ttu-id="25b95-137">Laadt het Power shell-profiel niet.</span><span class="sxs-lookup"><span data-stu-id="25b95-137">Does not load the PowerShell profile.</span></span>

#### <a name="-noninteractive"></a><span data-ttu-id="25b95-138">-Niet-interactief</span><span class="sxs-lookup"><span data-stu-id="25b95-138">-NonInteractive</span></span>

<span data-ttu-id="25b95-139">Er wordt geen interactieve prompt voor de gebruiker weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="25b95-139">Does not present an interactive prompt to the user.</span></span>

#### <a name="-inputformat-text--xml"></a><span data-ttu-id="25b95-140">-InputFormat {text | INDELING</span><span class="sxs-lookup"><span data-stu-id="25b95-140">-InputFormat {Text | XML}</span></span>

<span data-ttu-id="25b95-141">Beschrijft de indeling van gegevens die naar Power shell worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="25b95-141">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="25b95-142">Geldige waarden zijn ' text ' (tekst reeksen) of ' XML ' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="25b95-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

#### <a name="-outputformat-text--xml"></a><span data-ttu-id="25b95-143">-Output Format {Text | INDELING</span><span class="sxs-lookup"><span data-stu-id="25b95-143">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="25b95-144">Hiermee wordt bepaald hoe de uitvoer van Power shell wordt opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="25b95-144">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="25b95-145">Geldige waarden zijn ' text ' (tekst reeksen) of ' XML ' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="25b95-145">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

#### <a name="-windowstyle-window-style"></a><span data-ttu-id="25b95-146">-WindowStyle \<Window style\></span><span class="sxs-lookup"><span data-stu-id="25b95-146">-WindowStyle \<Window style\></span></span>

<span data-ttu-id="25b95-147">Hiermee stelt u de venster stijl voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="25b95-147">Sets the window style for the session.</span></span> <span data-ttu-id="25b95-148">Geldige waarden zijn normaal, geminimaliseerd, gemaximaliseerd en verborgen.</span><span class="sxs-lookup"><span data-stu-id="25b95-148">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

#### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="25b95-149">-EncodedCommand \<Base64EncodedCommand\></span><span class="sxs-lookup"><span data-stu-id="25b95-149">-EncodedCommand \<Base64EncodedCommand\></span></span>

<span data-ttu-id="25b95-150">Hiermee wordt een teken reeks versie met basis-64-code ring geaccepteerd van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="25b95-150">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="25b95-151">Gebruik deze para meter om opdrachten naar Power shell te verzenden waarvoor complexe aanhalings tekens of accolades zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="25b95-151">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span> <span data-ttu-id="25b95-152">De teken reeks moet worden opgemaakt met de UTF-16LE-teken codering.</span><span class="sxs-lookup"><span data-stu-id="25b95-152">The string must be formatted using UTF-16LE character encoding.</span></span>

#### <a name="-configurationname-string"></a><span data-ttu-id="25b95-153">-Configuratiepad \<string\></span><span class="sxs-lookup"><span data-stu-id="25b95-153">-ConfigurationName \<string\></span></span>

<span data-ttu-id="25b95-154">Hiermee geeft u een configuratie-eind punt waarin Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="25b95-154">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="25b95-155">Dit kan elk eind punt zijn dat is geregistreerd op de lokale computer, met inbegrip van de standaard externe communicatie-eind punten in Power shell of een aangepast eind punt met specifieke mogelijkheden voor de gebruikersrol.</span><span class="sxs-lookup"><span data-stu-id="25b95-155">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

#### <a name="-file----filepath-args"></a><span data-ttu-id="25b95-156">-Bestand-| \<filePath\>\<args\></span><span class="sxs-lookup"><span data-stu-id="25b95-156">-File - | \<filePath\> \<args\></span></span>

<span data-ttu-id="25b95-157">Als de waarde van het **bestand** is, wordt de opdracht tekst gelezen uit de standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="25b95-157">If the value of **File** is "-", the command text is read from standard input.</span></span>
<span data-ttu-id="25b95-158">Als u `powershell -File -` zonder omgeleide standaard invoer uitvoert, wordt een reguliere sessie gestart.</span><span class="sxs-lookup"><span data-stu-id="25b95-158">Running `powershell -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="25b95-159">Dit is hetzelfde als de **Bestands** parameter helemaal niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="25b95-159">This is the same as not specifying the **File** parameter at all.</span></span>

<span data-ttu-id="25b95-160">Als de waarde van het **bestand** een bestandspad is, wordt het script uitgevoerd in het lokale bereik (' dot-brond '), zodat de functies en variabelen die het script maakt, beschikbaar zijn in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="25b95-160">If the value of **File** is a file path, the script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="25b95-161">Voer het pad naar het script bestand en eventuele para meters in.</span><span class="sxs-lookup"><span data-stu-id="25b95-161">Enter the script file path and any parameters.</span></span> <span data-ttu-id="25b95-162">Het **bestand** moet de laatste para meter in de opdracht zijn.</span><span class="sxs-lookup"><span data-stu-id="25b95-162">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="25b95-163">Alle waarden die na de **Bestands** parameter worden getypt, worden geïnterpreteerd als het pad naar het script bestand en de para meters die aan het script worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="25b95-163">All values typed after the **File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="25b95-164">Para meters die aan het script worden door gegeven, worden als letterlijke teken reeksen door gegeven na de interpretatie van de huidige shell.</span><span class="sxs-lookup"><span data-stu-id="25b95-164">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="25b95-165">Als u bijvoorbeeld in **cmd.exe** bent en u een omgevings variabele waarde wilt door geven, gebruikt u de **cmd.exe** syntaxis: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="25b95-165">For example, if you are in **cmd.exe** and want to pass an environment variable value, you would use the **cmd.exe** syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="25b95-166">Als u daarentegen `powershell.exe -File .\test.ps1 -TestParam $env:windir` in **cmd.exe** resulteert, wordt de letterlijke teken reeks door het script ontvangen `$env:windir` omdat het geen speciale betekenis heeft voor de huidige **cmd.exe** shell.</span><span class="sxs-lookup"><span data-stu-id="25b95-166">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in **cmd.exe** results in the script receiving the literal string `$env:windir` because it has no special meaning to the current **cmd.exe** shell.</span></span> <span data-ttu-id="25b95-167">De `$env:windir` stijl van de verwijzing naar een omgevings variabele _kan_ worden gebruikt binnen een **opdracht** parameter, omdat deze wordt geïnterpreteerd als Power shell-code.</span><span class="sxs-lookup"><span data-stu-id="25b95-167">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it will be interpreted as PowerShell code.</span></span>

<span data-ttu-id="25b95-168">Als u dezelfde opdracht uit een **batch script** wilt uitvoeren, gebruikt u `%~dp0` in plaats van `.\` of `$PSScriptRoot` om de huidige uitvoerings Directory te vertegenwoordigen: `powershell.exe -File %~dp0test.ps1 -TestParam %windir%` .</span><span class="sxs-lookup"><span data-stu-id="25b95-168">Similarly, if you want to execute the same command from a **Batch script** , you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `powershell.exe -File %~dp0test.ps1 -TestParam %windir%`.</span></span>
<span data-ttu-id="25b95-169">Als u in plaats daarvan gebruikt `.\test.ps1` , genereert Power shell een fout omdat het letterlijke pad niet kan worden gevonden `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="25b95-169">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="25b95-170">Wanneer de **waarde van het bestand een** bestandspad is, **File** _moet_ het bestand de laatste para meter zijn in de opdracht omdat de tekens die na de naam van de **Bestands** parameter worden getypt, worden geïnterpreteerd als het pad naar het script bestand gevolgd door de script parameters.</span><span class="sxs-lookup"><span data-stu-id="25b95-170">When the value of **File** is a file path, **File** _must_ be the last parameter in the command because any characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="25b95-171">U kunt de script parameters en waarden in de waarde van de **Bestands** parameter toevoegen.</span><span class="sxs-lookup"><span data-stu-id="25b95-171">You can include the script parameters and values in the value of the **File** parameter.</span></span> <span data-ttu-id="25b95-172">Bijvoorbeeld: `-File .\Get-Script.ps1 -Domain Central`</span><span class="sxs-lookup"><span data-stu-id="25b95-172">For example: `-File .\Get-Script.ps1 -Domain Central`</span></span>

<span data-ttu-id="25b95-173">Normaal gesp roken worden de switch parameters van een script opgenomen of wegge laten.</span><span class="sxs-lookup"><span data-stu-id="25b95-173">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="25b95-174">Met de volgende opdracht wordt bijvoorbeeld de para meter **all** van het `Get-Script.ps1` script bestand gebruikt: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="25b95-174">For example, the following command uses the **All** parameter of the `Get-Script.ps1` script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="25b95-175">In zeldzame gevallen moet u mogelijk een **Booleaanse** waarde voor een para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="25b95-175">In rare cases, you might need to provide a **Boolean** value for a parameter.</span></span>
<span data-ttu-id="25b95-176">Het is niet mogelijk om een expliciete Booleaanse waarde door te geven voor een switch parameter wanneer u een script op deze manier uitvoert.</span><span class="sxs-lookup"><span data-stu-id="25b95-176">It is not possible to pass an explicit boolean value for a switch parameter when running a script in this way.</span></span> <span data-ttu-id="25b95-177">Deze beperking is verwijderd in Power shell 6 ( `pwsh.exe` ).</span><span class="sxs-lookup"><span data-stu-id="25b95-177">This limitation was removed in PowerShell 6 (`pwsh.exe`).</span></span>

#### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="25b95-178">-ExecutionPolicy \<ExecutionPolicy\></span><span class="sxs-lookup"><span data-stu-id="25b95-178">-ExecutionPolicy \<ExecutionPolicy\></span></span>

<span data-ttu-id="25b95-179">Hiermee stelt u het standaard uitvoerings beleid voor de huidige sessie en slaat u deze op in de `$env:PSExecutionPolicyPreference` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="25b95-179">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="25b95-180">Met deze para meter wordt het Power shell-uitvoerings beleid dat in het REGI ster is ingesteld, niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="25b95-180">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="25b95-181">Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie over het uitvoeren van Power shell-uitvoerings beleid, met inbegrip van een lijst met geldige waarden.</span><span class="sxs-lookup"><span data-stu-id="25b95-181">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

#### <a name="-command"></a><span data-ttu-id="25b95-182">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="25b95-182">-Command</span></span>

<span data-ttu-id="25b95-183">Hiermee worden de opgegeven opdrachten (en eventuele para meters) uitgevoerd alsof ze zijn getypt bij de Power shell-opdracht prompt en vervolgens afgesloten, tenzij de `NoExit` para meter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="25b95-183">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="25b95-184">De waarde van de **opdracht** kan `-` een script blok of een teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="25b95-184">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="25b95-185">Als de waarde van de **opdracht** is `-` , wordt de opdracht tekst gelezen uit de standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="25b95-185">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="25b95-186">De **opdracht** parameter accepteert alleen een script blok voor uitvoering wanneer het de **waarde die wordt door gegeven, kan** herkennen als een **script Block** -type.</span><span class="sxs-lookup"><span data-stu-id="25b95-186">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="25b95-187">Dit kan _alleen_ worden uitgevoerd `powershell.exe` vanuit een andere Power shell-host.</span><span class="sxs-lookup"><span data-stu-id="25b95-187">This is _only_ possible when running `powershell.exe` from another PowerShell host.</span></span> <span data-ttu-id="25b95-188">Het type **script Block** kan worden opgenomen in een bestaande variabele, geretourneerd vanuit een expressie, of door de Power shell-host geparseerd als een letterlijk script blok tussen accolades ( `{}` ) voordat het wordt door gegeven aan `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="25b95-188">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `powershell.exe`.</span></span>

```powershell
powershell -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="25b95-189">In `cmd.exe` is er geen script blok (of **script Block** -type), dus de waarde die is door gegeven aan de **opdracht** , is _altijd_ een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="25b95-189">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="25b95-190">U kunt een script blok schrijven in de teken reeks, maar in plaats van dat het wordt uitgevoerd, werkt het niet exact alsof u het hebt getypt bij een typische Power shell-prompt, waarbij de inhoud van het script blok wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="25b95-190">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="25b95-191">Een teken reeks die aan de **opdracht** is door gegeven, wordt nog steeds uitgevoerd als Power shell-code, dus de accolades voor het blok keren van een script zijn in de eerste plaats vaak niet vereist tijdens de uitvoering van `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="25b95-191">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="25b95-192">Voor het uitvoeren van een inline-script blok dat in een teken reeks is gedefinieerd, kan de [aanroep operator](about_operators.md#special-operators) `&` worden gebruikt:</span><span class="sxs-lookup"><span data-stu-id="25b95-192">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```cmd
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="25b95-193">Als de waarde van de **opdracht** een teken reeks is, moet de **opdracht** de laatste para meter zijn voor pwsh, omdat alle argumenten die deze bevat, worden geïnterpreteerd als onderdeel van de opdracht die moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="25b95-193">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="25b95-194">Bij het aanroepen vanuit een bestaande Power shell-sessie worden de resultaten geretourneerd naar de bovenliggende shell als gedeserialiseerd XML-objecten, niet live-objecten.</span><span class="sxs-lookup"><span data-stu-id="25b95-194">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="25b95-195">Voor andere shells worden de resultaten geretourneerd als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="25b95-195">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="25b95-196">Als de waarde van de **opdracht** is `-` , wordt de opdracht tekst gelezen uit de standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="25b95-196">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="25b95-197">U moet de standaard invoer omleiden wanneer u de **opdracht** parameter gebruikt met standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="25b95-197">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="25b95-198">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="25b95-198">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="25b95-199">In dit voor beeld wordt de volgende uitvoer gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="25b95-199">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="25b95-200">De afsluit code van het proces wordt bepaald door de status van de laatste (uitgevoerde) opdracht in het-script blok.</span><span class="sxs-lookup"><span data-stu-id="25b95-200">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="25b95-201">De afsluit code is `0` `$?` `$true` of wanneer dat `1` `$?` zo is `$false` .</span><span class="sxs-lookup"><span data-stu-id="25b95-201">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="25b95-202">Als de laatste opdracht een extern programma of een Power shell-script is waarmee expliciet een andere afsluit code dan of wordt ingesteld `0` `1` , wordt die afsluit code geconverteerd naar `1` voor de afsluit code van het proces.</span><span class="sxs-lookup"><span data-stu-id="25b95-202">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="25b95-203">Als u de specifieke afsluit code wilt behouden, voegt `exit $LASTEXITCODE` u toe aan de opdracht reeks of het script blok.</span><span class="sxs-lookup"><span data-stu-id="25b95-203">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="25b95-204">Op dezelfde manier wordt de waarde 1 geretourneerd als er een fout optreedt bij het beëindigen van een script (runs, afgebroken), zoals een `throw` of `-ErrorAction Stop` , wanneer de uitvoering wordt onderbroken door <kbd>CTRL</kbd> - <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="25b95-204">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

<span data-ttu-id="25b95-205">_alleen_ mogelijk wanneer **PowerShell.exe** van een andere Power shell-host wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="25b95-205">_only_ possible when running **PowerShell.exe** from another PowerShell host.</span></span>
<span data-ttu-id="25b95-206">Het type **script Block** kan worden opgenomen in een bestaande variabele, geretourneerd vanuit een expressie, of door de Power shell-host geparseerd als een letterlijk script blok tussen accolades `{}` voordat het wordt door gegeven aan **PowerShell.exe**.</span><span class="sxs-lookup"><span data-stu-id="25b95-206">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to **PowerShell.exe**.</span></span>

<span data-ttu-id="25b95-207">In **cmd.exe** is er geen script blok (of **script Block** -type), dus de waarde die wordt door gegeven aan de **opdracht** , is _altijd_ een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="25b95-207">In **cmd.exe** , there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="25b95-208">U kunt een script blok schrijven in de teken reeks, maar in plaats van dat het wordt uitgevoerd, werkt het niet exact alsof u het hebt getypt bij een typische Power shell-prompt, waarbij de inhoud van het script blok wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="25b95-208">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="25b95-209">Een teken reeks die is door gegeven aan de **opdracht** , wordt nog steeds uitgevoerd als Power shell, zodat de accolades voor het blok keren van een script in de eerste plaats vaak niet vereist zijn wanneer ze vanuit **cmd.exe** worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="25b95-209">A string passed to **Command** will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from **cmd.exe**.</span></span> <span data-ttu-id="25b95-210">Voor het uitvoeren van een inline-script blok dat in een teken reeks is gedefinieerd, kan de [aanroep operator](about_operators.md#special-operators) 
 `&` worden gebruikt:</span><span class="sxs-lookup"><span data-stu-id="25b95-210">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators)
`&` can be used:</span></span>

```console
"& {<command>}"
```

#### <a name="-help---"></a><span data-ttu-id="25b95-211">-Help,-?,/?</span><span class="sxs-lookup"><span data-stu-id="25b95-211">-Help, -?, /?</span></span>

<span data-ttu-id="25b95-212">Geeft Help weer voor **PowerShell.exe**.</span><span class="sxs-lookup"><span data-stu-id="25b95-212">Displays help for **PowerShell.exe**.</span></span> <span data-ttu-id="25b95-213">Als u een **PowerShell.exe** -opdracht in een Power shell-sessie typt, laten voorafgaan door u de opdracht parameters met een koppel teken (-), niet een slash (/).</span><span class="sxs-lookup"><span data-stu-id="25b95-213">If you are typing a **PowerShell.exe** command in a PowerShell session, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="25b95-214">U kunt een koppel teken of slash gebruiken in **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="25b95-214">You can use either a hyphen or forward slash in **cmd.exe**.</span></span>

### <a name="remarks"></a><span data-ttu-id="25b95-215">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="25b95-215">REMARKS</span></span>

<span data-ttu-id="25b95-216">Problemen met de probleem oplossing: in Power Shell 2,0 kunnen sommige Program ma's van de Power shell-console niet worden gestart met een **LastExitCode** van 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="25b95-216">Troubleshooting note: In PowerShell 2.0, starting some programs from the PowerShell console fails with a **LastExitCode** of 0xc0000142.</span></span>

### <a name="examples"></a><span data-ttu-id="25b95-217">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="25b95-217">EXAMPLES</span></span>

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
