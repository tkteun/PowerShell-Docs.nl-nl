---
ms.date: 08/14/2018
keywords: PowerShell-cmdlet
title: Help voor de PowerShell.exe-opdrachtregel
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 03c7672ee72698fe88a73e99702ceaadf87e702f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51691827"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="d83d1-103">PowerShell.exe Help voor de opdrachtregel</span><span class="sxs-lookup"><span data-stu-id="d83d1-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="d83d1-104">U kunt het gebruiken van PowerShell.exe een PowerShell-sessie starten vanaf de opdrachtregel van een ander hulpprogramma, zoals Cmd.exe of op de PowerShell-opdrachtregel gebruiken om een nieuwe sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="d83d1-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="d83d1-105">Gebruik de parameters voor het aanpassen van de sessie.</span><span class="sxs-lookup"><span data-stu-id="d83d1-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="d83d1-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d83d1-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="d83d1-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="d83d1-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="d83d1-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="d83d1-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="d83d1-109">Accepteert een base 64 gecodeerde tekenreeks-versie van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="d83d1-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="d83d1-110">Gebruik deze parameter om te verzenden naar PowerShell-opdrachten die complexe tussen aanhalingstekens worden gezet of accolades vereist.</span><span class="sxs-lookup"><span data-stu-id="d83d1-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="d83d1-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="d83d1-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="d83d1-112">Hiermee stelt u het standaardbeleid voor uitvoering voor de huidige sessie en opgeslagen in de $env: PSExecutionPolicyPreference-omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="d83d1-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="d83d1-113">Deze parameter wijzigen niet van de PowerShell-uitvoeringsbeleid is ingesteld in het register.</span><span class="sxs-lookup"><span data-stu-id="d83d1-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="d83d1-114">Zie voor meer informatie over de uitvoeringsbeleidsregels PowerShell, waaronder een lijst met geldige waarden [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="d83d1-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="d83d1-115">-Bestand <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="d83d1-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="d83d1-116">Voert het opgegeven script in het lokale bereik ('dot-Source'), zodat de functies en variabelen die het script wordt gemaakt, beschikbaar in de huidige sessie zijn.</span><span class="sxs-lookup"><span data-stu-id="d83d1-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="d83d1-117">Geef het pad naar het script en eventueel parameters.</span><span class="sxs-lookup"><span data-stu-id="d83d1-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="d83d1-118">**Bestand** moet de laatste parameter in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="d83d1-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="d83d1-119">Alle waarden zijn ingevoerd na de **-bestand** parameter wordt geïnterpreteerd als het script logbestandspad en -parameters doorgegeven aan het script.</span><span class="sxs-lookup"><span data-stu-id="d83d1-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="d83d1-120">Parameters doorgegeven aan het script worden doorgegeven als letterlijke tekenreeksen, na de interpretatie van de huidige shell.</span><span class="sxs-lookup"><span data-stu-id="d83d1-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="d83d1-121">Bijvoorbeeld, als u zich in cmd.exe en wilt een omgevingsvariabele doorgeven, zou u de syntaxis cmd.exe gebruiken: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="d83d1-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="d83d1-122">Daarentegen uitgevoerd `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe resultaten in het script ontvangen van de letterlijke tekenreeks `$env:windir` omdat er geen speciale betekenis voor de huidige cmd.exe-shell.</span><span class="sxs-lookup"><span data-stu-id="d83d1-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="d83d1-123">De `$env:windir` stijl van de variabele omgevingsverwijzing _kunt_ worden gebruikt binnen een `-Command` parameter, omdat er deze wordt geïnterpreteerd als PowerShell-code.</span><span class="sxs-lookup"><span data-stu-id="d83d1-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="d83d1-124">\-InputFormat {tekst | XML}</span><span class="sxs-lookup"><span data-stu-id="d83d1-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="d83d1-125">Hierin wordt beschreven in de indeling van gegevens die worden verzonden naar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d83d1-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="d83d1-126">Geldige waarden zijn 'Tekst' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="d83d1-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="d83d1-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="d83d1-127">-Mta</span></span>

<span data-ttu-id="d83d1-128">Start PowerShell met behulp van een apartment meerdere threads.</span><span class="sxs-lookup"><span data-stu-id="d83d1-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="d83d1-129">Deze parameter is opgenomen in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d83d1-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="d83d1-130">Single-threaded apartment (STA) is PowerShell 3.0, de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="d83d1-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="d83d1-131">In PowerShell 2.0 is dankzij de multi-threaded apartment (MTA) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="d83d1-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="d83d1-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="d83d1-132">-NoExit</span></span>

<span data-ttu-id="d83d1-133">Na het uitvoeren van opstartopdrachten afsluiten niet.</span><span class="sxs-lookup"><span data-stu-id="d83d1-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="d83d1-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="d83d1-134">-NoLogo</span></span>

<span data-ttu-id="d83d1-135">Hiermee verbergt u de copyright banner bij het opstarten.</span><span class="sxs-lookup"><span data-stu-id="d83d1-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="d83d1-136">-Niet-interactieve</span><span class="sxs-lookup"><span data-stu-id="d83d1-136">-NonInteractive</span></span>

<span data-ttu-id="d83d1-137">Niet aanwezig zijn van een interactieve prompt voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d83d1-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="d83d1-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="d83d1-138">-NoProfile</span></span>

<span data-ttu-id="d83d1-139">Het PowerShell-profiel niet worden geladen.</span><span class="sxs-lookup"><span data-stu-id="d83d1-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="d83d1-140">-Uitvoerindeling {tekst | XML}</span><span class="sxs-lookup"><span data-stu-id="d83d1-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="d83d1-141">Bepaalt hoe de uitvoer van PowerShell wordt opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="d83d1-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="d83d1-142">Geldige waarden zijn 'Tekst' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).</span><span class="sxs-lookup"><span data-stu-id="d83d1-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="d83d1-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="d83d1-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="d83d1-144">Laadt het opgegeven bestand van de PowerShell-console.</span><span class="sxs-lookup"><span data-stu-id="d83d1-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="d83d1-145">Geef het pad en de naam van de consolebestand.</span><span class="sxs-lookup"><span data-stu-id="d83d1-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="d83d1-146">Gebruik voor het maken van een consolebestand de [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d83d1-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="d83d1-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="d83d1-147">-Sta</span></span>

<span data-ttu-id="d83d1-148">Start PowerShell met behulp van een single-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="d83d1-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="d83d1-149">Single-threaded apartment (STA) is PowerShell 3.0, de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="d83d1-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="d83d1-150">In PowerShell 2.0 is dankzij de multi-threaded apartment (MTA) de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="d83d1-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="d83d1-151">-Versie <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="d83d1-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="d83d1-152">Hiermee start u de opgegeven versie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d83d1-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="d83d1-153">De versie die u opgeeft moet worden geïnstalleerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="d83d1-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="d83d1-154">Als u PowerShell 3.0 op de computer is geïnstalleerd, wordt de geldige waarden zijn "2.0" en '3.0'.</span><span class="sxs-lookup"><span data-stu-id="d83d1-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="d83d1-155">De standaardwaarde is '3.0'.</span><span class="sxs-lookup"><span data-stu-id="d83d1-155">The default value is "3.0".</span></span>

<span data-ttu-id="d83d1-156">Als PowerShell 3.0 niet is geïnstalleerd, is de enige geldige waarde '2.0'.</span><span class="sxs-lookup"><span data-stu-id="d83d1-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="d83d1-157">Andere waarden worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="d83d1-157">Other values are ignored.</span></span>

<span data-ttu-id="d83d1-158">Zie voor meer informatie, [Windows PowerShell installeren](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d83d1-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="d83d1-159">-Vensterstijl <Window style></span><span class="sxs-lookup"><span data-stu-id="d83d1-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="d83d1-160">Hiermee stelt u de vensterstijl voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="d83d1-160">Sets the window style for the session.</span></span> <span data-ttu-id="d83d1-161">Geldige waarden zijn normaal, geminimaliseerd, gemaximaliseerd en verborgen.</span><span class="sxs-lookup"><span data-stu-id="d83d1-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="d83d1-162">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="d83d1-162">-Command</span></span>

<span data-ttu-id="d83d1-163">Hiermee voert u de opgegeven opdrachten (met parameters) alsof ze zijn getypt achter de PowerShell-opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="d83d1-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="d83d1-164">Na de uitvoering, PowerShell wordt afgesloten, tenzij de **NoExit** parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d83d1-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="d83d1-165">Alle tekst na `-Command` als een enkele opdrachtregel wordt verzonden naar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d83d1-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="d83d1-166">Dit wijkt af van hoe u `-File` parameters die worden verzonden naar een script worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="d83d1-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="d83d1-167">De waarde van `-Command` kan '-', een tekenreeks of een scriptblok.</span><span class="sxs-lookup"><span data-stu-id="d83d1-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="d83d1-168">De resultaten van de opdracht keert terug naar de bovenliggende shell als gedeserialiseerde XML-objecten die niet live objecten.</span><span class="sxs-lookup"><span data-stu-id="d83d1-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="d83d1-169">Als de waarde van `-Command` is '-', de opdrachttekst worden gelezen uit de standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="d83d1-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="d83d1-170">Wanneer de waarde van `-Command` is een tekenreeks, **opdracht** _moet_ worden de laatste parameter zijn opgegeven, omdat alle tekens hebt getypt nadat de opdracht als de opdrachtargumenten worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="d83d1-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="d83d1-171">De **opdracht** parameter accepteert alleen een scriptblok voor uitvoering op wanneer de waarde die is doorgegeven aan kan worden herkend `-Command` als ScriptBlock-type.</span><span class="sxs-lookup"><span data-stu-id="d83d1-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="d83d1-172">Dit is _alleen_ mogelijk bij het uitvoeren van PowerShell.exe uit een andere PowerShell-host.</span><span class="sxs-lookup"><span data-stu-id="d83d1-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="d83d1-173">Het type kan zich bevinden in een bestaande variabele, geretourneerd door een expressie of geparseerd door de PowerShell ScriptBlock hosten als een letterlijke scriptblok tussen accolades `{}`voordat wordt doorgegeven aan PowerShell.exe.</span><span class="sxs-lookup"><span data-stu-id="d83d1-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="d83d1-174">In cmd.exe, er is niet goed als een scriptblok (of ScriptBlock type), zodat de waarde die is doorgegeven aan **opdracht** wordt _altijd_ een tekenreeks zijn.</span><span class="sxs-lookup"><span data-stu-id="d83d1-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="d83d1-175">U kunt een scriptblok binnen de tekenreeks schrijven, maar in plaats van wordt uitgevoerd het gedragen precies alsof u de gegevens hebt ingevoerd bij een typische PowerShell-prompt, de inhoud van het script afdrukken blokkeren weer uit voor u.</span><span class="sxs-lookup"><span data-stu-id="d83d1-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="d83d1-176">Een tekenreeks doorgegeven aan `-Command` nog steeds worden uitgevoerd als PowerShell, zodat het script blok tussen accolades vaak niet vereist in de eerste plaats zijn bij het uitvoeren van cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="d83d1-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="d83d1-177">Voor het uitvoeren van een inline-scriptblok zoals gedefinieerd in een tekenreeks, de [aanroep-operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` kan worden gebruikt:</span><span class="sxs-lookup"><span data-stu-id="d83d1-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="d83d1-178">-Help-,?, /?</span><span class="sxs-lookup"><span data-stu-id="d83d1-178">-Help, -?, /?</span></span>

<span data-ttu-id="d83d1-179">Ziet u de syntaxis van de powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="d83d1-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="d83d1-180">Als u een opdracht PowerShell.exe in PowerShell, voegt u vóór de opdrachtparameters met een afbreekstreepje (-), niet een slash (/).</span><span class="sxs-lookup"><span data-stu-id="d83d1-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="d83d1-181">U kunt een afbreekstreepje of een schuine streep in Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="d83d1-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="d83d1-182">Opmerking voor probleemoplossing: In PowerShell 2.0, sommige programma's starten in de Windows PowerShell console niet met een LastExitCode van 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="d83d1-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="d83d1-183">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d83d1-183">EXAMPLES</span></span>

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
