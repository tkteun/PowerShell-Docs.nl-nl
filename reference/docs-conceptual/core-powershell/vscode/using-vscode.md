# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="69b39-101">Met behulp van Visual Studio Code voor het ontwikkelen van PowerShell</span><span class="sxs-lookup"><span data-stu-id="69b39-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="69b39-102">Naast de [PowerShell ISE][ise], PowerShell wordt ook goed ondersteund in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="69b39-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="69b39-103">Bovendien wordt de ISE niet ondersteund met PowerShell-kern wanneer Visual Studio Code wordt ondersteund voor PowerShell Core op alle platforms (Windows, Mac OS en Linux)</span><span class="sxs-lookup"><span data-stu-id="69b39-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="69b39-104">U kunt Visual Studio Code in Windows met PowerShell versie 5 met behulp van Windows 10 of door het installeren van [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) voor eerdere Windows-besturingssystemen (bijvoorbeeld Windows 8.1, enzovoort).</span><span class="sxs-lookup"><span data-stu-id="69b39-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="69b39-105">Voordat u begint het, Controleer of dat PowerShell bestaat op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="69b39-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="69b39-106">Zie voor moderne werkbelastingen op Windows-, Mac OS- en Linux:</span><span class="sxs-lookup"><span data-stu-id="69b39-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="69b39-107">[PowerShell Core installeren op Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="69b39-107">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="69b39-108">[PowerShell Core installeert op Mac OS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="69b39-108">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="69b39-109">[PowerShell Core installeren in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="69b39-109">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="69b39-110">Zie voor traditionele Windows PowerShell-werkbelastingen, [Windows PowerShell installeren][install-winps].</span><span class="sxs-lookup"><span data-stu-id="69b39-110">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="69b39-111">Bewerken met Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69b39-111">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="69b39-112">1. Visual Studio Code installeren</span><span class="sxs-lookup"><span data-stu-id="69b39-112">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="69b39-113">**Linux**: Volg de instructies voor installatie op de [uitgevoerd tegenover Code op Linux](https://code.visualstudio.com/docs/setup/linux) pagina</span><span class="sxs-lookup"><span data-stu-id="69b39-113">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="69b39-114">**Mac OS**: Volg de instructies voor installatie op de [uitgevoerd tegenover Code op Mac OS](https://code.visualstudio.com/docs/setup/mac) pagina</span><span class="sxs-lookup"><span data-stu-id="69b39-114">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69b39-115">Op Mac OS, moet u OpenSSL voor de PowerShell-uitbreiding correct te laten werken.</span><span class="sxs-lookup"><span data-stu-id="69b39-115">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
> <span data-ttu-id="69b39-116">De eenvoudigste manier om dit te bereiken is voor het installeren van [Homebrew](http://brew.sh/) en voer vervolgens `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="69b39-116">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
> <span data-ttu-id="69b39-117">De PowerShell-extensie is nu mogelijk zijn geladen.</span><span class="sxs-lookup"><span data-stu-id="69b39-117">The PowerShell extension will now be able to load successfully.</span></span>

- <span data-ttu-id="69b39-118">**Windows**: Volg de instructies voor installatie op de [tegenover Code uitgevoerd op Windows](https://code.visualstudio.com/docs/setup/windows) pagina</span><span class="sxs-lookup"><span data-stu-id="69b39-118">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="69b39-119">2. Installeren van PowerShell-extensie</span><span class="sxs-lookup"><span data-stu-id="69b39-119">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="69b39-120">Start de Visual Studio Code app door:</span><span class="sxs-lookup"><span data-stu-id="69b39-120">Launch the Visual Studio Code app by:</span></span>
    - <span data-ttu-id="69b39-121">**Windows**: typen `code` in uw PowerShell-sessie</span><span class="sxs-lookup"><span data-stu-id="69b39-121">**Windows**: typing `code` in your PowerShell session</span></span>
    - <span data-ttu-id="69b39-122">**Linux**: typen `code` in uw terminal</span><span class="sxs-lookup"><span data-stu-id="69b39-122">**Linux**: typing `code` in your terminal</span></span>
    - <span data-ttu-id="69b39-123">**Mac OS**: typen `code` in uw terminal</span><span class="sxs-lookup"><span data-stu-id="69b39-123">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="69b39-124">Start **snelle Open** door te drukken **Ctrl + P** (**Cmd + P** op Mac).</span><span class="sxs-lookup"><span data-stu-id="69b39-124">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="69b39-125">Typ in het vak snel openen `ext install powershell` en treffers **Enter**.</span><span class="sxs-lookup"><span data-stu-id="69b39-125">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="69b39-126">De **extensies** weergave wilt openen op de zijmarge.</span><span class="sxs-lookup"><span data-stu-id="69b39-126">The **Extensions** view will open on the Side Bar.</span></span> <span data-ttu-id="69b39-127">Selecteer de PowerShell-uitbreiding van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="69b39-127">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="69b39-128">U ziet, zoals hieronder:</span><span class="sxs-lookup"><span data-stu-id="69b39-128">You will see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="69b39-130">Klik op de **installeren** knop van de PowerShell-extensie van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="69b39-130">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="69b39-131">Na de installatie ziet u de **installeren** knop verandert in **opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="69b39-131">After the install, you will see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="69b39-132">Klik op **opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="69b39-132">Click on **Reload**.</span></span>
- <span data-ttu-id="69b39-133">Nadat Visual Studio Code opnieuw laden heeft, bent u klaar om te bewerken.</span><span class="sxs-lookup"><span data-stu-id="69b39-133">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="69b39-134">Bijvoorbeeld voor het maken van een nieuw bestand, klikt u op **File -> nieuw**.</span><span class="sxs-lookup"><span data-stu-id="69b39-134">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="69b39-135">Als u wilt opslaan, klikt u op **File -> Opslaan** en geef vervolgens een bestandsnaam, gaan we spreek `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="69b39-135">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="69b39-136">U sluit het bestand, klik op 'x' naast de bestandsnaam.</span><span class="sxs-lookup"><span data-stu-id="69b39-136">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="69b39-137">Om af te sluiten van Visual Studio Code **File -> afsluiten**.</span><span class="sxs-lookup"><span data-stu-id="69b39-137">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="69b39-138">Een specifieke geïnstalleerde versie van PowerShell</span><span class="sxs-lookup"><span data-stu-id="69b39-138">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="69b39-139">Als u een specifieke installatie van PowerShell gebruiken met Visual Studio Code wilt, moet u een nieuwe variabele toevoegen aan het bestand van de gebruiker-instellingen.</span><span class="sxs-lookup"><span data-stu-id="69b39-139">If you wish to use a specific installation of PowerShell with Visual Studio Code, you will need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="69b39-140">Klik op **File-Voorkeuren > Instellingen ->**</span><span class="sxs-lookup"><span data-stu-id="69b39-140">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="69b39-141">Twee deelvensters van de editor wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="69b39-141">Two editor panes will appear.</span></span>
   <span data-ttu-id="69b39-142">In het deelvenster van de meest rechtse (`settings.json`), voeg de onderstaande instelling geschikt is voor uw besturingssysteem ergens tussen de twee accolades (`{` en `}`) en vervang *<version>* met de geïnstalleerde PowerShell-versie:</span><span class="sxs-lookup"><span data-stu-id="69b39-142">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. <span data-ttu-id="69b39-143">Vervangt de instelling met het pad naar het gewenste uitvoerbare PowerShell</span><span class="sxs-lookup"><span data-stu-id="69b39-143">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="69b39-144">Sla het instellingenbestand en Visual Studio Code opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="69b39-144">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="69b39-145">Configuratie-instellingen voor Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69b39-145">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="69b39-146">U kunt configuratie-instellingen in toevoegen met behulp van de stappen in de vorige alinea `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="69b39-146">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="69b39-147">U wordt aangeraden de volgende configuratieinstellingen voor Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="69b39-147">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="69b39-148">Foutopsporing met Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69b39-148">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="69b39-149">Er is geen werkruimte foutopsporing</span><span class="sxs-lookup"><span data-stu-id="69b39-149">No-workspace debugging</span></span>

<span data-ttu-id="69b39-150">Vanaf versie van Visual Studio Code 1,9 kunt u PowerShell-scripts zonder te openen van de map met het PowerShell-script voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="69b39-150">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="69b39-151">Gewoon openen met de PowerShell-scriptbestand **File -> bestand openen...** , stel een onderbrekingspunt in op een regel (druk op F9) en druk op F5 foutopsporing te starten.</span><span class="sxs-lookup"><span data-stu-id="69b39-151">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="69b39-152">Hier ziet u het actiedeelvenster voor foutopsporing worden weergegeven waarmee u in het foutopsporingsprogramma, stap, hervatten en stop foutopsporing te verdelen.</span><span class="sxs-lookup"><span data-stu-id="69b39-152">You will see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="69b39-153">Werkruimte foutopsporing</span><span class="sxs-lookup"><span data-stu-id="69b39-153">Workspace debugging</span></span>

<span data-ttu-id="69b39-154">Werkruimte foutopsporing verwijst naar het opsporen van fouten in de context van een map die u hebt geopend in met behulp van Visual Studio Code **map openen...**  van de **bestand** menu.</span><span class="sxs-lookup"><span data-stu-id="69b39-154">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="69b39-155">De map die u opent is meestal de projectmap PowerShell en/of de hoofdmap van de Git-opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="69b39-155">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="69b39-156">U kunt zelfs in deze modus starten foutopsporing van het momenteel geselecteerde PowerShell-script door op F5 te drukken.</span><span class="sxs-lookup"><span data-stu-id="69b39-156">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="69b39-157">Echter, kunt u voor het definiëren van configuraties met meerdere foutopsporing dan alleen het geopende bestand foutopsporing werkruimte foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="69b39-157">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="69b39-158">U kunt bijvoorbeeld een configuraties toevoegen:</span><span class="sxs-lookup"><span data-stu-id="69b39-158">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="69b39-159">Pester tests in de foutopsporing starten</span><span class="sxs-lookup"><span data-stu-id="69b39-159">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="69b39-160">Een specifiek bestand met argumenten in het foutopsporingsprogramma starten</span><span class="sxs-lookup"><span data-stu-id="69b39-160">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="69b39-161">Een interactieve sessie in de foutopsporing starten</span><span class="sxs-lookup"><span data-stu-id="69b39-161">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="69b39-162">Het foutopsporingsprogramma koppelen aan een hostproces van PowerShell</span><span class="sxs-lookup"><span data-stu-id="69b39-162">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="69b39-163">Volg deze stappen om uw configuratiebestand foutopsporing te maken:</span><span class="sxs-lookup"><span data-stu-id="69b39-163">Follow these steps to create your debug configuration file:</span></span>

1. <span data-ttu-id="69b39-164">Open de **Debug** weergeven door te drukken **Ctrl + Shift + D** (**Cmd + Shift + D** op Mac).</span><span class="sxs-lookup"><span data-stu-id="69b39-164">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
1. <span data-ttu-id="69b39-165">Druk op de **configureren** tandwielpictogram-pictogram op de werkbalk.</span><span class="sxs-lookup"><span data-stu-id="69b39-165">Press the **Configure** gear icon in the toolbar.</span></span>
1. <span data-ttu-id="69b39-166">Visual Studio Code wordt u gevraagd te **omgeving Selecteer**.</span><span class="sxs-lookup"><span data-stu-id="69b39-166">Visual Studio Code will prompt you to **Select Environment**.</span></span>
   <span data-ttu-id="69b39-167">Kies **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="69b39-167">Choose **PowerShell**.</span></span>

   <span data-ttu-id="69b39-168">Als u dit doet, Visual Studio Code een map en een bestand '.vscode\launch.json' gemaakt in de hoofdmap van uw werkruimtemap.</span><span class="sxs-lookup"><span data-stu-id="69b39-168">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
   <span data-ttu-id="69b39-169">Hier wordt de configuratie van de foutopsporing is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="69b39-169">This is where your debug configuration is stored.</span></span> <span data-ttu-id="69b39-170">Als de bestanden zich in een Git-opslagplaats, wilt u waarschijnlijk het bestand launch.json doorvoeren.</span><span class="sxs-lookup"><span data-stu-id="69b39-170">If your files are in a Git repository, you will typically want to commit the launch.json file.</span></span>
   <span data-ttu-id="69b39-171">De inhoud van het bestand launch.json zijn:</span><span class="sxs-lookup"><span data-stu-id="69b39-171">The contents of the launch.json file are:</span></span>

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
}
```

<span data-ttu-id="69b39-172">Hiermee wordt de algemene scenario's voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="69b39-172">This represents the common debug scenarios.</span></span>
<span data-ttu-id="69b39-173">Echter, wanneer u dit bestand in de editor opent, ziet u een **configuratie toevoegen...**  knop.</span><span class="sxs-lookup"><span data-stu-id="69b39-173">However, when you open this file in the editor, you will see an **Add Configuration...** button.</span></span>
<span data-ttu-id="69b39-174">U kunt drukt u op deze knop om meer PowerShell foutopsporing configuraties toevoegt.</span><span class="sxs-lookup"><span data-stu-id="69b39-174">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="69b39-175">Een handige configuratie om toe te voegen is **PowerShell: Script starten**.</span><span class="sxs-lookup"><span data-stu-id="69b39-175">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
<span data-ttu-id="69b39-176">Met deze configuratie kunt u een specifiek bestand met optionele argumenten die moet worden gestart telkens wanneer u op F5 drukken ongeacht welk bestand is momenteel actief zijn in de editor.</span><span class="sxs-lookup"><span data-stu-id="69b39-176">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="69b39-177">Wanneer de configuratie van de foutopsporing is gemaakt, kunt u selecteren welke configuratie u gebruiken tijdens een foutopsporingssessie voor wilt door een te selecteren in de configuratie van de foutopsporing vervolgkeuzelijst in de **Debug** van weergave-werkbalk.</span><span class="sxs-lookup"><span data-stu-id="69b39-177">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="69b39-178">Er zijn enkele blogs die mogelijk nuttig om aan de slag met PowerShell-extensie voor Visual Studio Code te gaan</span><span class="sxs-lookup"><span data-stu-id="69b39-178">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

- <span data-ttu-id="69b39-179">Visual Studio Code: [PowerShell-uitbreiding][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="69b39-179">Visual Studio Code: [PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="69b39-180">[Schrijven en foutopsporing van PowerShell-scripts in Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="69b39-180">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="69b39-181">[Foutopsporing van Visual Studio Code richtlijnen][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="69b39-181">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="69b39-182">[Foutopsporing van PowerShell in Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="69b39-182">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="69b39-183">[Aan de slag met PowerShell-ontwikkeling in Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="69b39-183">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="69b39-184">[Visual Studio Code bewerkingsfuncties voor PowerShell-ontwikkeling: deel 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="69b39-184">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="69b39-185">[Visual Studio Code bewerkingsfuncties voor PowerShell ontwikkeling – deel 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="69b39-185">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="69b39-186">[PowerShell-script voor foutopsporing in Visual Studio Code – deel 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="69b39-186">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="69b39-187">[PowerShell-script voor foutopsporing in Visual Studio Code – deel 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="69b39-187">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="69b39-188">PowerShell-extensie voor Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69b39-188">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="69b39-189">Broncode van de PowerShell-uitbreiding kunt u vinden op [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="69b39-189">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>