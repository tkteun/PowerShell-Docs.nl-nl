---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: PowerShell.exe opdrachtregel Help
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 262c21e44e509746314ed44d91bb3de16a4b854b
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="a29f7-103">Help voor de opdrachtregel PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="a29f7-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="a29f7-104">een Windows PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="a29f7-104">a Windows PowerShell session.</span></span> <span data-ttu-id="a29f7-105">U kunt PowerShell.exe gebruiken een PowerShell-sessie starten vanaf de opdrachtregel van een ander hulpprogramma, zoals Cmd.exe of op de PowerShell-opdrachtregel gebruiken om een nieuwe sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="a29f7-105">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="a29f7-106">Gebruik de parameters voor het aanpassen van de sessie.</span><span class="sxs-lookup"><span data-stu-id="a29f7-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="a29f7-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a29f7-107">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}] 
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive] 
       [-NoProfile] 
       [-OutputFormat {Text | XML}] 
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
        

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="a29f7-108">Parameters</span><span class="sxs-lookup"><span data-stu-id="a29f7-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="a29f7-109">-EncodedCommand<Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="a29f7-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="a29f7-110">Een base 64 gecodeerde tekenreeksversie van een opdracht accepteert.</span><span class="sxs-lookup"><span data-stu-id="a29f7-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="a29f7-111">Gebruik deze parameter om opdrachten naar PowerShell waarvoor complexe aanhalingstekens of accolades verzenden.</span><span class="sxs-lookup"><span data-stu-id="a29f7-111">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="a29f7-112">-ExecutionPolicy<ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="a29f7-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="a29f7-113">Hiermee stelt u het standaarduitvoeringsbeleid voor de huidige sessie en opgeslagen in de $env: PSExecutionPolicyPreference-omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="a29f7-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="a29f7-114">Deze parameter wordt de PowerShell-uitvoeringsbeleid dat is ingesteld in het register niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a29f7-114">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="a29f7-115">Zie voor meer informatie over de uitvoeringsbeleidsregels PowerShell, waaronder een lijst met geldige waarden about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span><span class="sxs-lookup"><span data-stu-id="a29f7-115">For information about PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="a29f7-116">-Bestand <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="a29f7-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="a29f7-117">Voert het opgegeven script in het lokale bereik ('dot-afkomstig'), zodat de functies en variabelen die het script maakt beschikbaar in de huidige sessie zijn.</span><span class="sxs-lookup"><span data-stu-id="a29f7-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="a29f7-118">Geef het pad naar het script en parameters.</span><span class="sxs-lookup"><span data-stu-id="a29f7-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="a29f7-119">**Bestand** moet de laatste parameter in de opdracht, omdat alle tekens worden ingevoerd na de **bestand** parameternaam worden geïnterpreteerd als het script bestandspad gevolgd door de scriptparameters en hun waarden.</span><span class="sxs-lookup"><span data-stu-id="a29f7-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="a29f7-120">U kunt de parameters van een script en parameterwaarden, opnemen in de waarde van de **bestand** parameter.</span><span class="sxs-lookup"><span data-stu-id="a29f7-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="a29f7-121">Bijvoorbeeld: `-File .\Get-Script.ps1 -Domain Central` opmerking die parameters doorgegeven aan het script worden doorgegeven als letterlijke tekenreeksen (na interpretatie door de huidige shell).</span><span class="sxs-lookup"><span data-stu-id="a29f7-121">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="a29f7-122">Bijvoorbeeld, als u in cmd.exe en wilt doorgeven van een omgevingsvariabele, gebruikt u de syntaxis van de cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` als u zou gebruiken van PowerShell-syntaxis, wordt in dit voorbeeld uw script de letterlijke waarde ontvangt ' $env: windir ' en niet de waarde van die omgevingsvariabele:`powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="a29f7-122">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="a29f7-123">Normaal gesproken worden de switch-parameters van een script opgenomen of weggelaten.</span><span class="sxs-lookup"><span data-stu-id="a29f7-123">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="a29f7-124">Bijvoorbeeld de volgende opdracht maakt gebruik van de **alle** parameter van het scriptbestand Get-Script.ps1:`-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="a29f7-124">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="a29f7-125">\-InputFormat {tekst | XML}</span><span class="sxs-lookup"><span data-stu-id="a29f7-125">\-InputFormat {Text | XML}</span></span>
<span data-ttu-id="a29f7-126">Beschrijft de indeling van gegevens die worden verzonden naar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a29f7-126">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="a29f7-127">Geldige waarden zijn 'Text' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="a29f7-127">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="a29f7-128">-Mta</span><span class="sxs-lookup"><span data-stu-id="a29f7-128">-Mta</span></span>
<span data-ttu-id="a29f7-129">Start PowerShell met een apartment met meerdere threads.</span><span class="sxs-lookup"><span data-stu-id="a29f7-129">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="a29f7-130">Deze parameter is geïntroduceerd in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="a29f7-130">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="a29f7-131">PowerShell 3.0 is single thread apartment (STA) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="a29f7-131">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="a29f7-132">In PowerShell 2.0 is met meerdere threads MTA (apartment) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="a29f7-132">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="a29f7-133">-NoExit</span><span class="sxs-lookup"><span data-stu-id="a29f7-133">-NoExit</span></span>
<span data-ttu-id="a29f7-134">Bestaat niet na het starten van de opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a29f7-134">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="a29f7-135">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="a29f7-135">-NoLogo</span></span>
<span data-ttu-id="a29f7-136">Hiermee verbergt het vaandel met copyright bij het opstarten.</span><span class="sxs-lookup"><span data-stu-id="a29f7-136">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="a29f7-137">-Niet-interactieve</span><span class="sxs-lookup"><span data-stu-id="a29f7-137">-NonInteractive</span></span>
<span data-ttu-id="a29f7-138">Biedt een interactieve prompt niet aanwezig voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a29f7-138">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="a29f7-139">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="a29f7-139">-NoProfile</span></span>
<span data-ttu-id="a29f7-140">Het PowerShell-profiel niet geladen.</span><span class="sxs-lookup"><span data-stu-id="a29f7-140">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="a29f7-141">-OutputFormat {tekst | XML}</span><span class="sxs-lookup"><span data-stu-id="a29f7-141">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="a29f7-142">Hiermee wordt bepaald hoe de uitvoer van PowerShell is geformatteerd.</span><span class="sxs-lookup"><span data-stu-id="a29f7-142">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="a29f7-143">Geldige waarden zijn 'Text' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="a29f7-143">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="a29f7-144">-PSConsoleFile<FilePath></span><span class="sxs-lookup"><span data-stu-id="a29f7-144">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="a29f7-145">Laadt het opgegeven bestand van de PowerShell-console.</span><span class="sxs-lookup"><span data-stu-id="a29f7-145">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="a29f7-146">Geef het pad en de naam van het consolebestand.</span><span class="sxs-lookup"><span data-stu-id="a29f7-146">Enter the path and name of the console file.</span></span> <span data-ttu-id="a29f7-147">Gebruik voor het maken van een consolebestand de [Export Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a29f7-147">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="a29f7-148">-Sta</span><span class="sxs-lookup"><span data-stu-id="a29f7-148">-Sta</span></span>
<span data-ttu-id="a29f7-149">Start PowerShell met een apartment met één thread bevindt.</span><span class="sxs-lookup"><span data-stu-id="a29f7-149">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="a29f7-150">PowerShell 3.0 is single thread apartment (STA) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="a29f7-150">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="a29f7-151">In PowerShell 2.0 is met meerdere threads MTA (apartment) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="a29f7-151">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="a29f7-152">-Versie<PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="a29f7-152">-Version <PowerShell Version></span></span>
<span data-ttu-id="a29f7-153">Hiermee start u de opgegeven versie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a29f7-153">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="a29f7-154">De versie die u opgeeft moet worden geïnstalleerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="a29f7-154">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="a29f7-155">Als PowerShell 3.0 is geïnstalleerd op de computer, wordt de geldige waarden zijn '2.0' en '3.0'.</span><span class="sxs-lookup"><span data-stu-id="a29f7-155">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="a29f7-156">De standaardwaarde is '3.0'.</span><span class="sxs-lookup"><span data-stu-id="a29f7-156">The default value is "3.0".</span></span>

<span data-ttu-id="a29f7-157">Als PowerShell 3.0 niet is geïnstalleerd, is de enige geldige waarde '2.0'.</span><span class="sxs-lookup"><span data-stu-id="a29f7-157">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="a29f7-158">Andere waarden worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="a29f7-158">Other values are ignored.</span></span>

<span data-ttu-id="a29f7-159">Zie voor meer informatie "PowerShell installeren" in de [aan de slag met PowerShell [oude MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="a29f7-159">For more information, see "Installing PowerShell" in the [Getting Started with PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="a29f7-160">-Vensterstijl<Window style></span><span class="sxs-lookup"><span data-stu-id="a29f7-160">-WindowStyle <Window style></span></span>
<span data-ttu-id="a29f7-161">Hiermee stelt de vensterstijl voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="a29f7-161">Sets the window style for the session.</span></span> <span data-ttu-id="a29f7-162">Geldige waarden zijn standaard, geminimaliseerd, gemaximaliseerd en verborgen.</span><span class="sxs-lookup"><span data-stu-id="a29f7-162">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="a29f7-163">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="a29f7-163">-Command</span></span>
<span data-ttu-id="a29f7-164">Voert de opgegeven opdrachten (en eventuele parameters) alsof ze zijn getypt achter de PowerShell-opdrachtprompt en vervolgens wordt afgesloten, tenzij de parameter NoExit is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a29f7-164">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="a29f7-165">In wezen elke tekst na `-Command` wordt verzonden als een enkele opdrachtregel naar PowerShell (dit verschilt van het `-File` omgaat met parameters die worden verzonden naar een script).</span><span class="sxs-lookup"><span data-stu-id="a29f7-165">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="a29f7-166">De waarde van de opdracht kan niet '-', een tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="a29f7-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="a29f7-167">of een scriptblok is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a29f7-167">or a script block.</span></span> <span data-ttu-id="a29f7-168">Als de waarde van de opdracht '-', de opdrachttekst is gelezen uit standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="a29f7-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="a29f7-169">Scriptblokken moeten tussen accolades ({}) worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="a29f7-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="a29f7-170">U kunt een scriptblok opgeven, alleen wanneer PowerShell.exe uitgevoerd in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a29f7-170">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="a29f7-171">De resultaten van het script worden geretourneerd aan de bovenliggende shell als gedeserialiseerde XML-objecten die niet live objecten.</span><span class="sxs-lookup"><span data-stu-id="a29f7-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="a29f7-172">Als de waarde van de opdracht een tekenreeks is, **opdracht** moet de laatste parameter in de opdracht, omdat alle tekens worden ingevoerd nadat de opdracht als de opdrachtargumenten worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="a29f7-172">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="a29f7-173">Gebruik de notatie voor het schrijven van een tekenreeks die wordt uitgevoerd een PowerShell-opdracht:</span><span class="sxs-lookup"><span data-stu-id="a29f7-173">To write a string that runs a PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="a29f7-174">waar de aanhalingstekens geven een tekenreeks en de operator invoke (&) zorgt ervoor dat de opdracht om te worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a29f7-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="a29f7-175">-Help-,?, /?</span><span class="sxs-lookup"><span data-stu-id="a29f7-175">-Help, -?, /?</span></span>
<span data-ttu-id="a29f7-176">Dit bericht bevat.</span><span class="sxs-lookup"><span data-stu-id="a29f7-176">Shows this message.</span></span> <span data-ttu-id="a29f7-177">Als u een opdracht PowerShell.exe in PowerShell typt, voeg de opdrachtparameters met een afbreekstreepje (-), niet een slash (/).</span><span class="sxs-lookup"><span data-stu-id="a29f7-177">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="a29f7-178">U kunt een koppelteken of een slash in Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="a29f7-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="a29f7-179">Opmerking voor probleemoplossing: In PowerShell 2.0 beginnen enkele programma's in de Windows PowerShell console is mislukt met een LastExitCode van 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="a29f7-179">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="a29f7-180">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a29f7-180">EXAMPLES</span></span>

```
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a Powerhell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate wayh to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

