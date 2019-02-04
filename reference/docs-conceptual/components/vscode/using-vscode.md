---
title: Visual Studio Code gebruiken voor het ontwikkelen van PowerShell
description: Visual Studio Code gebruiken voor het ontwikkelen van PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 03f370d0906790b573ea42290b9ccdec2cf84f2e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686696"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="4e976-103">Visual Studio Code gebruiken voor het ontwikkelen van PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e976-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="4e976-104">Naast de [PowerShell ISE][ise], PowerShell wordt ook goed ondersteund in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4e976-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="4e976-105">Bovendien wordt de ISE niet ondersteund met PowerShell Core, terwijl de Visual Studio Code voor PowerShell Core wordt ondersteund op alle platformen (Windows, macOS en Linux)</span><span class="sxs-lookup"><span data-stu-id="4e976-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="4e976-106">U kunt Visual Studio Code op Windows met PowerShell versie 5 gebruiken met behulp van Windows 10 of door het installeren van [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) voor downlevel-Windows-OSs (bijvoorbeeld Windows 8.1, enzovoort).</span><span class="sxs-lookup"><span data-stu-id="4e976-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="4e976-107">Voordat u begint met het, Controleer of dat PowerShell bestaat op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="4e976-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="4e976-108">Zie voor moderne workloads in Windows, macOS en Linux:</span><span class="sxs-lookup"><span data-stu-id="4e976-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="4e976-109">[PowerShell Core in Linux installeren][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="4e976-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="4e976-110">[PowerShell Core in macOS installeren][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="4e976-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="4e976-111">[PowerShell Core in Windows installeren][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="4e976-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="4e976-112">Zie voor traditionele Windows PowerShell-workloads, [Windows PowerShell installeren][install-winps].</span><span class="sxs-lookup"><span data-stu-id="4e976-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="4e976-113">Bewerken met Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4e976-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="4e976-114">1. Visual Studio Code installeren</span><span class="sxs-lookup"><span data-stu-id="4e976-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="4e976-115">**Linux**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op Linux](https://code.visualstudio.com/docs/setup/linux) pagina</span><span class="sxs-lookup"><span data-stu-id="4e976-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="4e976-116">**macOS**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op macOS](https://code.visualstudio.com/docs/setup/mac) pagina</span><span class="sxs-lookup"><span data-stu-id="4e976-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="4e976-117">Op Mac OS, moet u OpenSSL voor de extensie van PowerShell correct te laten werken.</span><span class="sxs-lookup"><span data-stu-id="4e976-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="4e976-118">De eenvoudigste manier om dit te doen is voor het installeren van [Homebrew](https://brew.sh/) en voer `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="4e976-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="4e976-119">VS Code kan nu worden geladen de PowerShell-extensie.</span><span class="sxs-lookup"><span data-stu-id="4e976-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="4e976-120">**Windows**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op Windows](https://code.visualstudio.com/docs/setup/windows) pagina</span><span class="sxs-lookup"><span data-stu-id="4e976-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="4e976-121">2. PowerShell-extensie installeren</span><span class="sxs-lookup"><span data-stu-id="4e976-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="4e976-122">Start Visual Studio Code app door:</span><span class="sxs-lookup"><span data-stu-id="4e976-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="4e976-123">**Windows**: typen `code` in uw PowerShell-sessie</span><span class="sxs-lookup"><span data-stu-id="4e976-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="4e976-124">**Linux**: typen `code` in uw terminal</span><span class="sxs-lookup"><span data-stu-id="4e976-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="4e976-125">**macOS**: typen `code` in uw terminal</span><span class="sxs-lookup"><span data-stu-id="4e976-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="4e976-126">Start **snel openen** door te drukken **Ctrl + P** (**Cmd + P** op Mac).</span><span class="sxs-lookup"><span data-stu-id="4e976-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="4e976-127">Typ in snel openen `ext install powershell` en klik op **Enter**.</span><span class="sxs-lookup"><span data-stu-id="4e976-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="4e976-128">De **extensies** weergave geopend op de zijbalk.</span><span class="sxs-lookup"><span data-stu-id="4e976-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="4e976-129">Selecteer de PowerShell-uitbreiding van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4e976-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="4e976-130">U zou iets moet zien zoals hieronder:</span><span class="sxs-lookup"><span data-stu-id="4e976-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="4e976-132">Klik op de **installeren** knop van de PowerShell-extensie van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4e976-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="4e976-133">Na de installatie, ziet u de **installeren** knop verandert in **opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="4e976-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="4e976-134">Klik op **opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="4e976-134">Click on **Reload**.</span></span>
- <span data-ttu-id="4e976-135">Nadat Visual Studio Code opnieuw laden is, bent u klaar voor het bewerken van.</span><span class="sxs-lookup"><span data-stu-id="4e976-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="4e976-136">Bijvoorbeeld, als u wilt een nieuw bestand maken, klikt u op **File -> New**.</span><span class="sxs-lookup"><span data-stu-id="4e976-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="4e976-137">Als u wilt opslaan, klikt u op **File -> Opslaan** en geef vervolgens een bestandsnaam op, laten we zeggen `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4e976-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="4e976-138">U sluit het bestand, klikt u op 'x' naast de bestandsnaam van het.</span><span class="sxs-lookup"><span data-stu-id="4e976-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="4e976-139">Om af te sluiten van Visual Studio Code, **File -> afsluiten**.</span><span class="sxs-lookup"><span data-stu-id="4e976-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="4e976-140">Installeren van de PowerShell-extensie op systemen met beperkte toegang</span><span class="sxs-lookup"><span data-stu-id="4e976-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="4e976-141">Sommige systemen zijn ingesteld op een manier die nodig zijn alle code handtekeningen moet worden gecontroleerd en dus nodig PowerShell Editor Services handmatig worden goedgekeurd om te worden uitgevoerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="4e976-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="4e976-142">Als u de extensie van PowerShell hebt geïnstalleerd, maar een foutmelding als zijn bereikt, is een Groepsbeleid-update die uitvoeringsbeleid wijzigen een waarschijnlijke oorzaak:</span><span class="sxs-lookup"><span data-stu-id="4e976-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="4e976-143">Open een PowerShell-prompt en voer voor het handmatig goedkeuren van PowerShell Editor Services en dus de PowerShell-extensie voor VSCode:</span><span class="sxs-lookup"><span data-stu-id="4e976-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="4e976-144">U wordt gevraagd met "Wilt u uitvoeren van software van deze niet-vertrouwde uitgever?"</span><span class="sxs-lookup"><span data-stu-id="4e976-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="4e976-145">Type `R` het bestand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="4e976-145">Type `R` to run the file.</span></span> <span data-ttu-id="4e976-146">Vervolgens opent u Visual Studio Code en controleer of de PowerShell-uitbreiding correct functioneert.</span><span class="sxs-lookup"><span data-stu-id="4e976-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="4e976-147">Als u nog steeds problemen aan de slag hebt, laat het ons weten op [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="4e976-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="4e976-148">Met behulp van een specifieke versie van PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e976-148">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="4e976-149">Als u gebruiken van een specifieke installatie van PowerShell met Visual Studio Code wilt, moet u een nieuwe variabele toevoegen aan het bestand met gebruiker instellingen.</span><span class="sxs-lookup"><span data-stu-id="4e976-149">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="4e976-150">Klik op **File -> Voorkeuren >-instellingen**</span><span class="sxs-lookup"><span data-stu-id="4e976-150">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="4e976-151">Twee deelvensters van de rapporteditor worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="4e976-151">Two editor panes appear.</span></span>
   <span data-ttu-id="4e976-152">In het deelvenster uiterst rechts (`settings.json`), invoegen van de instelling van de onderstaande geschikt is voor uw besturingssysteem ergens tussen de twee gekrulde haken (`{` en `}`) en vervang **\<versie\>** met de geïnstalleerde versie van PowerShell:</span><span class="sxs-lookup"><span data-stu-id="4e976-152">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="4e976-153">De instelling vervangen door het pad naar de gewenste uitvoerbare PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e976-153">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="4e976-154">Het bestand met instellingen opslaan en opnieuw opstarten van Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4e976-154">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="4e976-155">Configuratie-instellingen voor Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4e976-155">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="4e976-156">U kunt configuratie-instellingen in toevoegen met behulp van de stappen in de vorige alinea `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="4e976-156">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="4e976-157">U wordt aangeraden de volgende configuratie-instellingen voor Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="4e976-157">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="4e976-158">Fouten opsporen met Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4e976-158">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="4e976-159">Geen werkruimte foutopsporing</span><span class="sxs-lookup"><span data-stu-id="4e976-159">No-workspace debugging</span></span>

<span data-ttu-id="4e976-160">Vanaf versie van Visual Studio Code 1.9 kunt u PowerShell-scripts fouten opsporen zonder te open de map met het PowerShell-script.</span><span class="sxs-lookup"><span data-stu-id="4e976-160">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="4e976-161">Open gewoon de PowerShell-scriptbestand met **File -> bestand openen...** , stel een onderbrekingspunt in op een regel (druk op F9) en druk vervolgens op F5 foutopsporing te starten.</span><span class="sxs-lookup"><span data-stu-id="4e976-161">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="4e976-162">U ziet het actiedeelvenster van foutopsporing worden weergegeven waarmee u in het foutopsporingsprogramma, stap, hervatten en stop foutopsporing opsplitsen.</span><span class="sxs-lookup"><span data-stu-id="4e976-162">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="4e976-163">Werkruimte-foutopsporing</span><span class="sxs-lookup"><span data-stu-id="4e976-163">Workspace debugging</span></span>

<span data-ttu-id="4e976-164">Werkruimte foutopsporing verwijst naar het opsporen van fouten in de context van een map die u hebt geopend in Visual Studio Code met behulp van **map openen...**  uit de **bestand** menu.</span><span class="sxs-lookup"><span data-stu-id="4e976-164">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="4e976-165">De map die u opent is meestal de projectmap op PowerShell en/of de hoofdmap van de Git-opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="4e976-165">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="4e976-166">Zelfs in deze modus kunt u beginnen met het opsporen van fouten in de momenteel geselecteerde PowerShell-script door op F5 te drukken.</span><span class="sxs-lookup"><span data-stu-id="4e976-166">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="4e976-167">Echter, kunt u definiëren configuraties met meerdere foutopsporing dan alleen opsporen van fouten in het geopende bestand werkruimte foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="4e976-167">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="4e976-168">U kunt bijvoorbeeld een configuraties die u kunt toevoegen:</span><span class="sxs-lookup"><span data-stu-id="4e976-168">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="4e976-169">Pester tests in het foutopsporingsprogramma Start</span><span class="sxs-lookup"><span data-stu-id="4e976-169">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="4e976-170">Een specifiek bestand met argumenten in het foutopsporingsprogramma Start</span><span class="sxs-lookup"><span data-stu-id="4e976-170">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="4e976-171">Een interactieve sessie in het foutopsporingsprogramma Start</span><span class="sxs-lookup"><span data-stu-id="4e976-171">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="4e976-172">Het foutopsporingsprogramma koppelen aan een hostproces van PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e976-172">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="4e976-173">Volg deze stappen om uw debug-configuratiebestand te maken:</span><span class="sxs-lookup"><span data-stu-id="4e976-173">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="4e976-174">Open de **Debug** weergeven door te drukken **Ctrl + Shift + D** (**Cmd + Shift + D** op Mac).</span><span class="sxs-lookup"><span data-stu-id="4e976-174">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="4e976-175">Druk op de **configureren** tandwielpictogram in de werkbalk.</span><span class="sxs-lookup"><span data-stu-id="4e976-175">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="4e976-176">U wordt gevraagd om Visual Studio Code **omgeving selecteert**.</span><span class="sxs-lookup"><span data-stu-id="4e976-176">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="4e976-177">Kies **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="4e976-177">Choose **PowerShell**.</span></span>

  <span data-ttu-id="4e976-178">Als u dit doet, maakt Visual Studio Code een map en een bestand '.vscode\launch.json' in de hoofdmap van de werkruimtemap van uw.</span><span class="sxs-lookup"><span data-stu-id="4e976-178">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="4e976-179">Dit is waar uw debug-configuratie is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="4e976-179">This is where your debug configuration is stored.</span></span> <span data-ttu-id="4e976-180">Als de bestanden zich in een Git-opslagplaats, wilt u meestal het bestand launch.json doorvoeren.</span><span class="sxs-lookup"><span data-stu-id="4e976-180">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="4e976-181">De inhoud van het bestand launch.json zijn:</span><span class="sxs-lookup"><span data-stu-id="4e976-181">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="4e976-182">Hiermee wordt de algemene scenario's voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="4e976-182">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="4e976-183">Echter, als u dit bestand in de editor opent, ziet u een **configuratie toevoegen...**  knop.</span><span class="sxs-lookup"><span data-stu-id="4e976-183">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="4e976-184">U drukt op deze knop om toe te voegen meer PowerShell-configuraties voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="4e976-184">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="4e976-185">Een handige configuratie toe te voegen is **PowerShell: Script Start**.</span><span class="sxs-lookup"><span data-stu-id="4e976-185">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="4e976-186">Met deze configuratie kunt u een specifiek bestand met optionele argumenten die moet worden gestart wanneer u op F5 drukt ongeacht welk bestand is momenteel actief zijn in de editor.</span><span class="sxs-lookup"><span data-stu-id="4e976-186">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="4e976-187">Zodra de configuratie van de foutopsporing tot stand is gebracht, kunt u selecteren welke configuratie u gebruiken tijdens een foutopsporingssessie wilt door het selecteren van een van de configuratie van de foutopsporing vervolgkeuzelijst in de **Debug** van weergave-werkbalk.</span><span class="sxs-lookup"><span data-stu-id="4e976-187">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="4e976-188">Er zijn een paar blogs die mogelijk nuttig zijn om aan de slag met PowerShell-extensie voor Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="4e976-188">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="4e976-189">[Extensie van PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="4e976-189">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="4e976-190">[Schrijf en fouten opsporen in PowerShell-scripts in Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="4e976-190">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="4e976-191">[Foutopsporing van Visual Studio Code-richtlijnen][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="4e976-191">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="4e976-192">[Foutopsporing in PowerShell in Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="4e976-192">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="4e976-193">[Aan de slag met PowerShell-ontwikkeling in Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="4e976-193">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="4e976-194">[Visual Studio Code bewerken van functies voor het ontwikkelen van PowerShell-deel 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="4e976-194">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="4e976-195">[Visual Studio Code bewerken van functies voor het ontwikkelen van PowerShell-deel 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="4e976-195">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="4e976-196">[PowerShell-script voor foutopsporing in Visual Studio Code – deel 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="4e976-196">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="4e976-197">[PowerShell-script voor foutopsporing in Visual Studio Code – deel 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="4e976-197">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="4e976-198">PowerShell-extensie voor Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4e976-198">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="4e976-199">De broncode van de PowerShell-extensie kunt u vinden op [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="4e976-199">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
