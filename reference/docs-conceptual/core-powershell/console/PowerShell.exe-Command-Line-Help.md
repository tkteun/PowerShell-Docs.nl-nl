---
ms.date: 08/14/2018
keywords: PowerShell-cmdlet
title: Help voor de PowerShell.exe-opdrachtregel
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133853"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="c1828-103">PowerShell.exe Help voor de opdrachtregel</span><span class="sxs-lookup"><span data-stu-id="c1828-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="c1828-104">U kunt het gebruiken van PowerShell.exe een PowerShell-sessie starten vanaf de opdrachtregel van een ander hulpprogramma, zoals Cmd.exe of op de PowerShell-opdrachtregel gebruiken om een nieuwe sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="c1828-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="c1828-105">Gebruik de parameters voor het aanpassen van de sessie.</span><span class="sxs-lookup"><span data-stu-id="c1828-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="c1828-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c1828-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="c1828-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="c1828-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="c1828-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="c1828-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="c1828-109">Accepteert een base 64 gecodeerde tekenreeks-versie van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="c1828-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="c1828-110">Gebruik deze parameter om te verzenden naar PowerShell-opdrachten die complexe tussen aanhalingstekens worden gezet of accolades vereist.</span><span class="sxs-lookup"><span data-stu-id="c1828-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="c1828-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="c1828-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="c1828-112">Hiermee stelt u het standaardbeleid voor uitvoering voor de huidige sessie en opgeslagen in de $env: PSExecutionPolicyPreference-omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="c1828-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="c1828-113">Deze parameter wijzigen niet van de PowerShell-uitvoeringsbeleid is ingesteld in het register.</span><span class="sxs-lookup"><span data-stu-id="c1828-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="c1828-114">Zie voor meer informatie over de uitvoeringsbeleidsregels PowerShell, waaronder een lijst met geldige waarden [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="c1828-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="c1828-115">-Bestand <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="c1828-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="c1828-116">Voert het opgegeven script in het lokale bereik ('dot-Source'), zodat de functies en variabelen die het script wordt gemaakt, beschikbaar in de huidige sessie zijn.</span><span class="sxs-lookup"><span data-stu-id="c1828-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="c1828-117">Geef het pad naar het script en eventueel parameters.</span><span class="sxs-lookup"><span data-stu-id="c1828-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="c1828-118">**Bestand** moet de laatste parameter in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="c1828-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="c1828-119">Alle waarden zijn ingevoerd na de **-bestand** parameter wordt geïnterpreteerd als het script logbestandspad en -parameters doorgegeven aan het script.</span><span class="sxs-lookup"><span data-stu-id="c1828-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="c1828-120">Parameters doorgegeven aan het script worden doorgegeven als letterlijke tekenreeksen (na interpretatie door de huidige shell).</span><span class="sxs-lookup"><span data-stu-id="c1828-120">Parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span> <span data-ttu-id="c1828-121">Bijvoorbeeld, als u in cmd.exe en wilt een omgevingsvariabele doorgeven, gebruikt u de syntaxis cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` In dit voorbeeld wordt het script de letterlijke tekenreeks ontvangt `$env:windir` en niet de waarde van deze omgevingsvariabele: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="c1828-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` In this example, the script receives the literal string `$env:windir` and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="c1828-122">\-InputFormat {tekst | XML}</span><span class="sxs-lookup"><span data-stu-id="c1828-122">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="c1828-123">Hierin wordt beschreven in de indeling van gegevens die worden verzonden naar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1828-123">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="c1828-124">Geldige waarden zijn 'Tekst' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="c1828-124">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="c1828-125">-Mta</span><span class="sxs-lookup"><span data-stu-id="c1828-125">-Mta</span></span>

<span data-ttu-id="c1828-126">Start PowerShell met behulp van een apartment meerdere threads.</span><span class="sxs-lookup"><span data-stu-id="c1828-126">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="c1828-127">Deze parameter is opgenomen in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c1828-127">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="c1828-128">Single-threaded apartment (STA) is PowerShell 3.0, de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="c1828-128">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="c1828-129">In PowerShell 2.0 is dankzij de multi-threaded apartment (MTA) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="c1828-129">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="c1828-130">-NoExit</span><span class="sxs-lookup"><span data-stu-id="c1828-130">-NoExit</span></span>

<span data-ttu-id="c1828-131">Na het uitvoeren van opstartopdrachten afsluiten niet.</span><span class="sxs-lookup"><span data-stu-id="c1828-131">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="c1828-132">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="c1828-132">-NoLogo</span></span>

<span data-ttu-id="c1828-133">Hiermee verbergt u de copyright banner bij het opstarten.</span><span class="sxs-lookup"><span data-stu-id="c1828-133">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="c1828-134">-Niet-interactieve</span><span class="sxs-lookup"><span data-stu-id="c1828-134">-NonInteractive</span></span>

<span data-ttu-id="c1828-135">Niet aanwezig zijn van een interactieve prompt voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="c1828-135">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="c1828-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="c1828-136">-NoProfile</span></span>

<span data-ttu-id="c1828-137">Het PowerShell-profiel niet worden geladen.</span><span class="sxs-lookup"><span data-stu-id="c1828-137">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="c1828-138">-Uitvoerindeling {tekst | XML}</span><span class="sxs-lookup"><span data-stu-id="c1828-138">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="c1828-139">Bepaalt hoe de uitvoer van PowerShell wordt opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="c1828-139">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="c1828-140">Geldige waarden zijn 'Tekst' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="c1828-140">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="c1828-141">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="c1828-141">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="c1828-142">Laadt het opgegeven bestand van de PowerShell-console.</span><span class="sxs-lookup"><span data-stu-id="c1828-142">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="c1828-143">Geef het pad en de naam van de consolebestand.</span><span class="sxs-lookup"><span data-stu-id="c1828-143">Enter the path and name of the console file.</span></span> <span data-ttu-id="c1828-144">Gebruik voor het maken van een consolebestand de [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1828-144">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="c1828-145">-Sta</span><span class="sxs-lookup"><span data-stu-id="c1828-145">-Sta</span></span>

<span data-ttu-id="c1828-146">Start PowerShell met behulp van een single-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="c1828-146">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="c1828-147">Single-threaded apartment (STA) is PowerShell 3.0, de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="c1828-147">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="c1828-148">In PowerShell 2.0 is dankzij de multi-threaded apartment (MTA) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="c1828-148">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="c1828-149">-Versie <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="c1828-149">-Version <PowerShell Version></span></span>

<span data-ttu-id="c1828-150">Hiermee start u de opgegeven versie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1828-150">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="c1828-151">De versie die u opgeeft moet worden geïnstalleerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="c1828-151">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="c1828-152">Als u PowerShell 3.0 op de computer is geïnstalleerd, wordt de geldige waarden zijn "2.0" en '3.0'.</span><span class="sxs-lookup"><span data-stu-id="c1828-152">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="c1828-153">De standaardwaarde is '3.0'.</span><span class="sxs-lookup"><span data-stu-id="c1828-153">The default value is "3.0".</span></span>

<span data-ttu-id="c1828-154">Als PowerShell 3.0 niet is geïnstalleerd, is de enige geldige waarde '2.0'.</span><span class="sxs-lookup"><span data-stu-id="c1828-154">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="c1828-155">Andere waarden worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="c1828-155">Other values are ignored.</span></span>

<span data-ttu-id="c1828-156">Zie voor meer informatie, [Windows PowerShell installeren](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c1828-156">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="c1828-157">-Vensterstijl <Window style></span><span class="sxs-lookup"><span data-stu-id="c1828-157">-WindowStyle <Window style></span></span>

<span data-ttu-id="c1828-158">Hiermee stelt u de vensterstijl voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="c1828-158">Sets the window style for the session.</span></span> <span data-ttu-id="c1828-159">Geldige waarden zijn normaal, geminimaliseerd, gemaximaliseerd en verborgen.</span><span class="sxs-lookup"><span data-stu-id="c1828-159">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="c1828-160">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="c1828-160">-Command</span></span>

<span data-ttu-id="c1828-161">Hiermee voert u de opgegeven opdrachten (met parameters) alsof ze zijn getypt achter de PowerShell-opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="c1828-161">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span> <span data-ttu-id="c1828-162">Na de uitvoering, PowerShell wordt afgesloten, tenzij de `-NoExit` parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c1828-162">After execution, PowerShell exits unless the `-NoExit` parameter is specified.</span></span>
<span data-ttu-id="c1828-163">Alle tekst na `-Command` als een enkele opdrachtregel wordt verzonden naar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1828-163">Any text after `-Command` is sent as a single command line to PowerShell.</span></span> <span data-ttu-id="c1828-164">Dit wijkt af van hoe u `-File` parameters die worden verzonden naar een script worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="c1828-164">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="c1828-165">De waarde van de opdracht kan niet '-', een tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="c1828-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="c1828-166">of een scriptblok.</span><span class="sxs-lookup"><span data-stu-id="c1828-166">or a script block.</span></span> <span data-ttu-id="c1828-167">Als de waarde van de opdracht '-', de opdrachttekst worden gelezen uit de standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="c1828-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="c1828-168">Scriptblokken moeten tussen accolades ({}).</span><span class="sxs-lookup"><span data-stu-id="c1828-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="c1828-169">U kunt een scriptblok alleen wanneer PowerShell.exe uitgevoerd in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1828-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="c1828-170">De resultaten van het script keert terug naar de bovenliggende shell als gedeserialiseerde XML-objecten die niet live objecten.</span><span class="sxs-lookup"><span data-stu-id="c1828-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="c1828-171">Als de waarde van de opdracht een tekenreeks is, **opdracht** moet de laatste parameter in de opdracht, omdat alle tekens hebt getypt nadat de opdracht als de opdrachtargumenten worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="c1828-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="c1828-172">Gebruik de indeling voor het schrijven van een tekenreeks is die wordt uitgevoerd een PowerShell-opdracht:</span><span class="sxs-lookup"><span data-stu-id="c1828-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="c1828-173">De aanhalingstekens geven een tekenreeks en de invoke-operator (&) zorgt ervoor dat de opdracht moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c1828-173">The quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="c1828-174">-Help-,?, /?</span><span class="sxs-lookup"><span data-stu-id="c1828-174">-Help, -?, /?</span></span>

<span data-ttu-id="c1828-175">Ziet u de syntaxis van de powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="c1828-175">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="c1828-176">Als u een opdracht PowerShell.exe in PowerShell, voegt u vóór de opdrachtparameters met een afbreekstreepje (-), niet een slash (/).</span><span class="sxs-lookup"><span data-stu-id="c1828-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="c1828-177">U kunt een afbreekstreepje of een schuine streep in Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="c1828-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="c1828-178">Opmerking voor probleemoplossing: In PowerShell 2.0, sommige programma's starten in de Windows PowerShell console niet met een LastExitCode van 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="c1828-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="c1828-179">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c1828-179">EXAMPLES</span></span>

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
