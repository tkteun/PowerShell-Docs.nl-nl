---
title: Visual Studio Code gebruiken voor het ontwikkelen van PowerShell
description: Visual Studio Code gebruiken voor het ontwikkelen van PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 9c06ce72c39d08e75fcb7e5cf9d5f92ae5dd8ed9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225791"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="b06e0-103">Visual Studio Code gebruiken voor het ontwikkelen van PowerShell</span><span class="sxs-lookup"><span data-stu-id="b06e0-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="b06e0-104">Naast de [PowerShell ISE][ise], PowerShell wordt ook goed ondersteund in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b06e0-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="b06e0-105">Bovendien wordt de ISE niet ondersteund met PowerShell Core, terwijl de Visual Studio Code voor PowerShell Core wordt ondersteund op alle platformen (Windows, macOS en Linux)</span><span class="sxs-lookup"><span data-stu-id="b06e0-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="b06e0-106">U kunt Visual Studio Code op Windows met PowerShell versie 5 gebruiken met behulp van Windows 10 of door het installeren van [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) voor downlevel-Windows-OSs (bijvoorbeeld Windows 8.1, enzovoort).</span><span class="sxs-lookup"><span data-stu-id="b06e0-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="b06e0-107">Voordat u begint met het, Controleer of dat PowerShell bestaat op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="b06e0-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="b06e0-108">Zie voor moderne workloads in Windows, macOS en Linux:</span><span class="sxs-lookup"><span data-stu-id="b06e0-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="b06e0-109">[PowerShell Core in Linux installeren][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="b06e0-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="b06e0-110">[PowerShell Core in macOS installeren][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="b06e0-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="b06e0-111">[PowerShell Core in Windows installeren][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="b06e0-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="b06e0-112">Zie voor traditionele Windows PowerShell-workloads, [Windows PowerShell installeren][install-winps].</span><span class="sxs-lookup"><span data-stu-id="b06e0-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="b06e0-113">Bewerken met Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b06e0-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="b06e0-114">1. Visual Studio Code installeren</span><span class="sxs-lookup"><span data-stu-id="b06e0-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="b06e0-115">**Linux**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op Linux](https://code.visualstudio.com/docs/setup/linux) pagina</span><span class="sxs-lookup"><span data-stu-id="b06e0-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="b06e0-116">**macOS**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op macOS](https://code.visualstudio.com/docs/setup/mac) pagina</span><span class="sxs-lookup"><span data-stu-id="b06e0-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="b06e0-117">Op Mac OS, moet u OpenSSL voor de extensie van PowerShell correct te laten werken.</span><span class="sxs-lookup"><span data-stu-id="b06e0-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="b06e0-118">De eenvoudigste manier om dit te doen is voor het installeren van [Homebrew](http://brew.sh/) en voer `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="b06e0-118">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="b06e0-119">VS Code kan nu worden geladen de PowerShell-extensie.</span><span class="sxs-lookup"><span data-stu-id="b06e0-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="b06e0-120">**Windows**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op Windows](https://code.visualstudio.com/docs/setup/windows) pagina</span><span class="sxs-lookup"><span data-stu-id="b06e0-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="b06e0-121">2. PowerShell-extensie installeren</span><span class="sxs-lookup"><span data-stu-id="b06e0-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="b06e0-122">Start Visual Studio Code app door:</span><span class="sxs-lookup"><span data-stu-id="b06e0-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="b06e0-123">**Windows**: typen `code` in uw PowerShell-sessie</span><span class="sxs-lookup"><span data-stu-id="b06e0-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="b06e0-124">**Linux**: typen `code` in uw terminal</span><span class="sxs-lookup"><span data-stu-id="b06e0-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="b06e0-125">**macOS**: typen `code` in uw terminal</span><span class="sxs-lookup"><span data-stu-id="b06e0-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="b06e0-126">Start **snel openen** door te drukken **Ctrl + P** (**Cmd + P** op Mac).</span><span class="sxs-lookup"><span data-stu-id="b06e0-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="b06e0-127">Typ in snel openen `ext install powershell` en klik op **Enter**.</span><span class="sxs-lookup"><span data-stu-id="b06e0-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="b06e0-128">De **extensies** weergave geopend op de zijbalk.</span><span class="sxs-lookup"><span data-stu-id="b06e0-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="b06e0-129">Selecteer de PowerShell-uitbreiding van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b06e0-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="b06e0-130">U zou iets moet zien zoals hieronder:</span><span class="sxs-lookup"><span data-stu-id="b06e0-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="b06e0-132">Klik op de **installeren** knop van de PowerShell-extensie van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b06e0-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="b06e0-133">Na de installatie, ziet u de **installeren** knop verandert in **opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="b06e0-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="b06e0-134">Klik op **opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="b06e0-134">Click on **Reload**.</span></span>
- <span data-ttu-id="b06e0-135">Nadat Visual Studio Code opnieuw laden is, bent u klaar voor het bewerken van.</span><span class="sxs-lookup"><span data-stu-id="b06e0-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="b06e0-136">Bijvoorbeeld, als u wilt een nieuw bestand maken, klikt u op **File -> New**.</span><span class="sxs-lookup"><span data-stu-id="b06e0-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="b06e0-137">Als u wilt opslaan, klikt u op **File -> Opslaan** en geef vervolgens een bestandsnaam op, laten we zeggen `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="b06e0-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="b06e0-138">U sluit het bestand, klikt u op 'x' naast de bestandsnaam van het.</span><span class="sxs-lookup"><span data-stu-id="b06e0-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="b06e0-139">Om af te sluiten van Visual Studio Code, **File -> afsluiten**.</span><span class="sxs-lookup"><span data-stu-id="b06e0-139">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="b06e0-140">Met behulp van een specifieke versie van PowerShell</span><span class="sxs-lookup"><span data-stu-id="b06e0-140">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="b06e0-141">Als u gebruiken van een specifieke installatie van PowerShell met Visual Studio Code wilt, moet u een nieuwe variabele toevoegen aan het bestand met gebruiker instellingen.</span><span class="sxs-lookup"><span data-stu-id="b06e0-141">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="b06e0-142">Klik op **File -> Voorkeuren >-instellingen**</span><span class="sxs-lookup"><span data-stu-id="b06e0-142">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="b06e0-143">Twee deelvensters van de rapporteditor worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="b06e0-143">Two editor panes appear.</span></span>
   <span data-ttu-id="b06e0-144">In het deelvenster uiterst rechts (`settings.json`), invoegen van de instelling van de onderstaande geschikt is voor uw besturingssysteem ergens tussen de twee gekrulde haken (`{` en `}`) en vervang **\<versie\>** met de geïnstalleerde versie van PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b06e0-144">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="b06e0-145">De instelling vervangen door het pad naar de gewenste uitvoerbare PowerShell</span><span class="sxs-lookup"><span data-stu-id="b06e0-145">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="b06e0-146">Het bestand met instellingen opslaan en opnieuw opstarten van Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b06e0-146">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="b06e0-147">Configuratie-instellingen voor Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b06e0-147">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="b06e0-148">U kunt configuratie-instellingen in toevoegen met behulp van de stappen in de vorige alinea `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="b06e0-148">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="b06e0-149">U wordt aangeraden de volgende configuratie-instellingen voor Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="b06e0-149">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="b06e0-150">Fouten opsporen met Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b06e0-150">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="b06e0-151">Geen werkruimte foutopsporing</span><span class="sxs-lookup"><span data-stu-id="b06e0-151">No-workspace debugging</span></span>

<span data-ttu-id="b06e0-152">Vanaf versie van Visual Studio Code 1.9 kunt u PowerShell-scripts fouten opsporen zonder te open de map met het PowerShell-script.</span><span class="sxs-lookup"><span data-stu-id="b06e0-152">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="b06e0-153">Open gewoon de PowerShell-scriptbestand met **File -> bestand openen...** , stel een onderbrekingspunt in op een regel (druk op F9) en druk vervolgens op F5 foutopsporing te starten.</span><span class="sxs-lookup"><span data-stu-id="b06e0-153">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="b06e0-154">U ziet het actiedeelvenster van foutopsporing worden weergegeven waarmee u in het foutopsporingsprogramma, stap, hervatten en stop foutopsporing opsplitsen.</span><span class="sxs-lookup"><span data-stu-id="b06e0-154">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="b06e0-155">Werkruimte-foutopsporing</span><span class="sxs-lookup"><span data-stu-id="b06e0-155">Workspace debugging</span></span>

<span data-ttu-id="b06e0-156">Werkruimte foutopsporing verwijst naar het opsporen van fouten in de context van een map die u hebt geopend in Visual Studio Code met behulp van **map openen...**  uit de **bestand** menu.</span><span class="sxs-lookup"><span data-stu-id="b06e0-156">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="b06e0-157">De map die u opent is meestal de projectmap op PowerShell en/of de hoofdmap van de Git-opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="b06e0-157">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="b06e0-158">Zelfs in deze modus kunt u beginnen met het opsporen van fouten in de momenteel geselecteerde PowerShell-script door op F5 te drukken.</span><span class="sxs-lookup"><span data-stu-id="b06e0-158">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="b06e0-159">Echter, kunt u definiëren configuraties met meerdere foutopsporing dan alleen opsporen van fouten in het geopende bestand werkruimte foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="b06e0-159">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="b06e0-160">U kunt bijvoorbeeld een configuraties die u kunt toevoegen:</span><span class="sxs-lookup"><span data-stu-id="b06e0-160">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="b06e0-161">Pester tests in het foutopsporingsprogramma Start</span><span class="sxs-lookup"><span data-stu-id="b06e0-161">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="b06e0-162">Een specifiek bestand met argumenten in het foutopsporingsprogramma Start</span><span class="sxs-lookup"><span data-stu-id="b06e0-162">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="b06e0-163">Een interactieve sessie in het foutopsporingsprogramma Start</span><span class="sxs-lookup"><span data-stu-id="b06e0-163">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="b06e0-164">Het foutopsporingsprogramma koppelen aan een hostproces van PowerShell</span><span class="sxs-lookup"><span data-stu-id="b06e0-164">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="b06e0-165">Volg deze stappen om uw debug-configuratiebestand te maken:</span><span class="sxs-lookup"><span data-stu-id="b06e0-165">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="b06e0-166">Open de **Debug** weergeven door te drukken **Ctrl + Shift + D** (**Cmd + Shift + D** op Mac).</span><span class="sxs-lookup"><span data-stu-id="b06e0-166">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="b06e0-167">Druk op de **configureren** tandwielpictogram in de werkbalk.</span><span class="sxs-lookup"><span data-stu-id="b06e0-167">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="b06e0-168">U wordt gevraagd om Visual Studio Code **omgeving selecteert**.</span><span class="sxs-lookup"><span data-stu-id="b06e0-168">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="b06e0-169">Kies **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="b06e0-169">Choose **PowerShell**.</span></span>

  <span data-ttu-id="b06e0-170">Als u dit doet, maakt Visual Studio Code een map en een bestand '.vscode\launch.json' in de hoofdmap van de werkruimtemap van uw.</span><span class="sxs-lookup"><span data-stu-id="b06e0-170">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="b06e0-171">Dit is waar uw debug-configuratie is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b06e0-171">This is where your debug configuration is stored.</span></span> <span data-ttu-id="b06e0-172">Als de bestanden zich in een Git-opslagplaats, wilt u meestal het bestand launch.json doorvoeren.</span><span class="sxs-lookup"><span data-stu-id="b06e0-172">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="b06e0-173">De inhoud van het bestand launch.json zijn:</span><span class="sxs-lookup"><span data-stu-id="b06e0-173">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="b06e0-174">Hiermee wordt de algemene scenario's voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="b06e0-174">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="b06e0-175">Echter, als u dit bestand in de editor opent, ziet u een **configuratie toevoegen...**  knop.</span><span class="sxs-lookup"><span data-stu-id="b06e0-175">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="b06e0-176">U drukt op deze knop om toe te voegen meer PowerShell-configuraties voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="b06e0-176">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="b06e0-177">Een handige configuratie toe te voegen is **PowerShell: Script Start**.</span><span class="sxs-lookup"><span data-stu-id="b06e0-177">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="b06e0-178">Met deze configuratie kunt u een specifiek bestand met optionele argumenten die moet worden gestart wanneer u op F5 drukt ongeacht welk bestand is momenteel actief zijn in de editor.</span><span class="sxs-lookup"><span data-stu-id="b06e0-178">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="b06e0-179">Zodra de configuratie van de foutopsporing tot stand is gebracht, kunt u selecteren welke configuratie u gebruiken tijdens een foutopsporingssessie wilt door het selecteren van een van de configuratie van de foutopsporing vervolgkeuzelijst in de **Debug** van weergave-werkbalk.</span><span class="sxs-lookup"><span data-stu-id="b06e0-179">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="b06e0-180">Er zijn een paar blogs die mogelijk nuttig zijn om aan de slag met PowerShell-extensie voor Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="b06e0-180">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="b06e0-181">[Extensie van PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="b06e0-181">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="b06e0-182">[Schrijf en fouten opsporen in PowerShell-scripts in Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="b06e0-182">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="b06e0-183">[Foutopsporing van Visual Studio Code-richtlijnen][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="b06e0-183">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="b06e0-184">[Foutopsporing in PowerShell in Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="b06e0-184">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="b06e0-185">[Aan de slag met PowerShell-ontwikkeling in Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="b06e0-185">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="b06e0-186">[Visual Studio Code bewerken van functies voor het ontwikkelen van PowerShell-deel 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="b06e0-186">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="b06e0-187">[Visual Studio Code bewerken van functies voor het ontwikkelen van PowerShell-deel 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="b06e0-187">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="b06e0-188">[PowerShell-script voor foutopsporing in Visual Studio Code – deel 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="b06e0-188">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="b06e0-189">[PowerShell-script voor foutopsporing in Visual Studio Code – deel 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="b06e0-189">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="b06e0-190">PowerShell-extensie voor Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b06e0-190">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="b06e0-191">De broncode van de PowerShell-extensie kunt u vinden op [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="b06e0-191">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
