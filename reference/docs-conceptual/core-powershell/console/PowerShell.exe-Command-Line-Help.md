---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Help voor de PowerShell.exe-opdrachtregel
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952576"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="6600b-103">Help voor de opdrachtregel PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="6600b-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="6600b-104">U kunt PowerShell.exe gebruiken een PowerShell-sessie starten vanaf de opdrachtregel van een ander hulpprogramma, zoals Cmd.exe of op de PowerShell-opdrachtregel gebruiken om een nieuwe sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="6600b-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="6600b-105">Gebruik de parameters voor het aanpassen van de sessie.</span><span class="sxs-lookup"><span data-stu-id="6600b-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="6600b-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6600b-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="6600b-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="6600b-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="6600b-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="6600b-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="6600b-109">Een base 64 gecodeerde tekenreeksversie van een opdracht accepteert.</span><span class="sxs-lookup"><span data-stu-id="6600b-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="6600b-110">Gebruik deze parameter om opdrachten naar PowerShell waarvoor complexe aanhalingstekens of accolades verzenden.</span><span class="sxs-lookup"><span data-stu-id="6600b-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="6600b-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="6600b-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="6600b-112">Hiermee stelt u het standaarduitvoeringsbeleid voor de huidige sessie en opgeslagen in de $env: PSExecutionPolicyPreference-omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="6600b-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="6600b-113">Deze parameter wordt de PowerShell-uitvoeringsbeleid dat is ingesteld in het register niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="6600b-113">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="6600b-114">Zie voor informatie over de uitvoeringsbeleidsregels PowerShell, waaronder een lijst met geldige waarden [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="6600b-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="6600b-115">-Bestand <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="6600b-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="6600b-116">Voert het opgegeven script in het lokale bereik ('dot-afkomstig'), zodat de functies en variabelen die het script maakt beschikbaar in de huidige sessie zijn.</span><span class="sxs-lookup"><span data-stu-id="6600b-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="6600b-117">Geef het pad naar het script en parameters.</span><span class="sxs-lookup"><span data-stu-id="6600b-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="6600b-118">**Bestand** moet de laatste parameter in de opdracht, omdat alle tekens worden ingevoerd na de **bestand** parameternaam worden geïnterpreteerd als het script bestandspad gevolgd door de scriptparameters en hun waarden.</span><span class="sxs-lookup"><span data-stu-id="6600b-118">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="6600b-119">U kunt de parameters van een script en parameterwaarden, opnemen in de waarde van de **bestand** parameter.</span><span class="sxs-lookup"><span data-stu-id="6600b-119">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="6600b-120">Bijvoorbeeld: `-File .\Get-Script.ps1 -Domain Central` opmerking die parameters doorgegeven aan het script worden doorgegeven als letterlijke tekenreeksen (na interpretatie door de huidige shell).</span><span class="sxs-lookup"><span data-stu-id="6600b-120">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="6600b-121">Bijvoorbeeld, als u in cmd.exe en wilt doorgeven van een omgevingsvariabele, gebruikt u de syntaxis van de cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` als u zou gebruiken van PowerShell-syntaxis, wordt in dit voorbeeld uw script de letterlijke waarde ontvangt ' $env: windir ' en niet de waarde van die omgevingsvariabele: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="6600b-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="6600b-122">Normaal gesproken worden de switch-parameters van een script opgenomen of weggelaten.</span><span class="sxs-lookup"><span data-stu-id="6600b-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="6600b-123">Bijvoorbeeld de volgende opdracht maakt gebruik van de **alle** parameter van het scriptbestand Get-Script.ps1: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="6600b-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="6600b-124">\-InputFormat {tekst | XML}</span><span class="sxs-lookup"><span data-stu-id="6600b-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="6600b-125">Beschrijft de indeling van gegevens die worden verzonden naar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6600b-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="6600b-126">Geldige waarden zijn 'Text' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="6600b-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="6600b-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="6600b-127">-Mta</span></span>

<span data-ttu-id="6600b-128">Start PowerShell met een apartment met meerdere threads.</span><span class="sxs-lookup"><span data-stu-id="6600b-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="6600b-129">Deze parameter is geïntroduceerd in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="6600b-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="6600b-130">PowerShell 3.0 is single thread apartment (STA) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="6600b-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="6600b-131">In PowerShell 2.0 is met meerdere threads MTA (apartment) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="6600b-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="6600b-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="6600b-132">-NoExit</span></span>

<span data-ttu-id="6600b-133">Bestaat niet na het starten van de opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="6600b-133">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="6600b-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="6600b-134">-NoLogo</span></span>

<span data-ttu-id="6600b-135">Hiermee verbergt het vaandel met copyright bij het opstarten.</span><span class="sxs-lookup"><span data-stu-id="6600b-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="6600b-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="6600b-136">-NonInteractive</span></span>

<span data-ttu-id="6600b-137">Biedt een interactieve prompt niet aanwezig voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="6600b-137">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="6600b-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="6600b-138">-NoProfile</span></span>

<span data-ttu-id="6600b-139">Het PowerShell-profiel niet geladen.</span><span class="sxs-lookup"><span data-stu-id="6600b-139">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="6600b-140">-OutputFormat {tekst | XML}</span><span class="sxs-lookup"><span data-stu-id="6600b-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="6600b-141">Hiermee wordt bepaald hoe de uitvoer van PowerShell is geformatteerd.</span><span class="sxs-lookup"><span data-stu-id="6600b-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="6600b-142">Geldige waarden zijn 'Text' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="6600b-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="6600b-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="6600b-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="6600b-144">Laadt het opgegeven bestand van de PowerShell-console.</span><span class="sxs-lookup"><span data-stu-id="6600b-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="6600b-145">Geef het pad en de naam van het consolebestand.</span><span class="sxs-lookup"><span data-stu-id="6600b-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="6600b-146">Gebruik voor het maken van een consolebestand de [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6600b-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="6600b-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="6600b-147">-Sta</span></span>

<span data-ttu-id="6600b-148">Start PowerShell met een apartment met één thread bevindt.</span><span class="sxs-lookup"><span data-stu-id="6600b-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="6600b-149">PowerShell 3.0 is single thread apartment (STA) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="6600b-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="6600b-150">In PowerShell 2.0 is met meerdere threads MTA (apartment) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="6600b-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="6600b-151">-Versie <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="6600b-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="6600b-152">Hiermee start u de opgegeven versie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6600b-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="6600b-153">De versie die u opgeeft moet worden geïnstalleerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="6600b-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="6600b-154">Als PowerShell 3.0 is geïnstalleerd op de computer, wordt de geldige waarden zijn '2.0' en '3.0'.</span><span class="sxs-lookup"><span data-stu-id="6600b-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="6600b-155">De standaardwaarde is '3.0'.</span><span class="sxs-lookup"><span data-stu-id="6600b-155">The default value is "3.0".</span></span>

<span data-ttu-id="6600b-156">Als PowerShell 3.0 niet is geïnstalleerd, is de enige geldige waarde '2.0'.</span><span class="sxs-lookup"><span data-stu-id="6600b-156">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="6600b-157">Andere waarden worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="6600b-157">Other values are ignored.</span></span>

<span data-ttu-id="6600b-158">Zie voor meer informatie '[Windows PowerShell installeren](../../setup/installing-windows-powershell.md)'.</span><span class="sxs-lookup"><span data-stu-id="6600b-158">For more information, see "[Installing Windows PowerShell](../../setup/installing-windows-powershell.md)".</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="6600b-159">-Vensterstijl <Window style></span><span class="sxs-lookup"><span data-stu-id="6600b-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="6600b-160">Hiermee stelt de vensterstijl voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="6600b-160">Sets the window style for the session.</span></span> <span data-ttu-id="6600b-161">Geldige waarden zijn standaard, geminimaliseerd, gemaximaliseerd en verborgen.</span><span class="sxs-lookup"><span data-stu-id="6600b-161">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="6600b-162">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="6600b-162">-Command</span></span>

<span data-ttu-id="6600b-163">Voert de opgegeven opdrachten (en eventuele parameters) alsof ze zijn getypt achter de PowerShell-opdrachtprompt en vervolgens wordt afgesloten, tenzij de parameter NoExit is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6600b-163">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="6600b-164">In wezen elke tekst na `-Command` wordt verzonden als een enkele opdrachtregel naar PowerShell (dit verschilt van het `-File` omgaat met parameters die worden verzonden naar een script).</span><span class="sxs-lookup"><span data-stu-id="6600b-164">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="6600b-165">De waarde van de opdracht kan niet '-', een tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="6600b-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="6600b-166">of een scriptblok is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6600b-166">or a script block.</span></span> <span data-ttu-id="6600b-167">Als de waarde van de opdracht '-', de opdrachttekst is gelezen uit standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="6600b-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="6600b-168">Scriptblokken moeten tussen accolades ({}) worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="6600b-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="6600b-169">U kunt een scriptblok opgeven, alleen wanneer PowerShell.exe uitgevoerd in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6600b-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="6600b-170">De resultaten van het script worden geretourneerd aan de bovenliggende shell als gedeserialiseerde XML-objecten die niet live objecten.</span><span class="sxs-lookup"><span data-stu-id="6600b-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="6600b-171">Als de waarde van de opdracht een tekenreeks is, **opdracht** moet de laatste parameter in de opdracht, omdat alle tekens worden ingevoerd nadat de opdracht als de opdrachtargumenten worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="6600b-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="6600b-172">Gebruik de notatie voor het schrijven van een tekenreeks die wordt uitgevoerd een PowerShell-opdracht:</span><span class="sxs-lookup"><span data-stu-id="6600b-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="6600b-173">waar de aanhalingstekens geven een tekenreeks en de operator invoke (&) zorgt ervoor dat de opdracht om te worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6600b-173">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="6600b-174">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="6600b-174">-Help, -?, /?</span></span>

<span data-ttu-id="6600b-175">Dit bericht bevat.</span><span class="sxs-lookup"><span data-stu-id="6600b-175">Shows this message.</span></span> <span data-ttu-id="6600b-176">Als u een opdracht PowerShell.exe in PowerShell typt, voeg de opdrachtparameters met een afbreekstreepje (-), niet een slash (/).</span><span class="sxs-lookup"><span data-stu-id="6600b-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="6600b-177">U kunt een koppelteken of een slash in Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="6600b-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="6600b-178">Opmerking voor probleemoplossing: In PowerShell 2.0 beginnen enkele programma's in de Windows PowerShell console is mislukt met een LastExitCode van 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="6600b-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="6600b-179">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6600b-179">EXAMPLES</span></span>

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