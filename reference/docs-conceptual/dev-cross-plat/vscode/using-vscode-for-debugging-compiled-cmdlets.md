---
ms.date: 10/19/2020
keywords: Power shell, cmdlet, debug
title: Visual Studio code gebruiken voor het opsporen van fouten in gecompileerde cmdlets
description: Een bouw taak instellen en configuratie starten voor een PSModule-project in .NET core
ms.openlocfilehash: ffae03b1edaf9d5ffa5da6381e301f829c8bc8f7
ms.sourcegitcommit: 57c3527ec6c3124cb9cdab7b07ebb92ed159cb64
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92374201"
---
# <a name="using-visual-studio-code-to-debug-compiled-cmdlets"></a><span data-ttu-id="65b39-104">Visual Studio code gebruiken voor het opsporen van fouten in gecompileerde cmdlets</span><span class="sxs-lookup"><span data-stu-id="65b39-104">Using Visual Studio Code to debug compiled cmdlets</span></span>

<span data-ttu-id="65b39-105">In deze hand leiding wordt beschreven hoe u interactief fouten opspoort in C#-bron code voor een gecompileerde Power shell-module met behulp van Visual Studio code (VS code) en de C#-extensie.</span><span class="sxs-lookup"><span data-stu-id="65b39-105">This guide shows you how to interactively debug C# source code for a compiled PowerShell module using Visual Studio Code (VS Code) and the C# extension.</span></span>

<span data-ttu-id="65b39-106">Enige kennis van het fout opsporingsprogramma Visual Studio code wordt aangenomen.</span><span class="sxs-lookup"><span data-stu-id="65b39-106">Some familiarity with the Visual Studio Code debugger is assumed.</span></span>

- <span data-ttu-id="65b39-107">Zie [fout opsporing in Visual Studio code][]voor een algemene inleiding tot de VS code debugger.</span><span class="sxs-lookup"><span data-stu-id="65b39-107">For a general introduction to the VS Code debugger, see [Debugging in Visual Studio Code][].</span></span>

- <span data-ttu-id="65b39-108">Voor voor beelden van fout opsporing van Power shell-script bestanden en-modules raadpleegt [u Visual Studio code gebruiken voor het extern bewerken en opsporen van fouten][].</span><span class="sxs-lookup"><span data-stu-id="65b39-108">For examples of debugging PowerShell script files and modules, see [Using Visual Studio Code for remote editing and debugging][].</span></span>

<span data-ttu-id="65b39-109">In deze hand leiding wordt ervan uitgegaan dat u de instructies in de hand leiding voor het [schrijven van draag bare modules][] hebt gelezen en gevolgd.</span><span class="sxs-lookup"><span data-stu-id="65b39-109">This guide assumes you have read and followed the instructions in the [Writing Portable Modules][] guide.</span></span>

## <a name="creating-a-build-task"></a><span data-ttu-id="65b39-110">Een build-taak maken</span><span class="sxs-lookup"><span data-stu-id="65b39-110">Creating a build task</span></span>

<span data-ttu-id="65b39-111">Bouw uw project automatisch op voordat u een foutopsporingssessie start.</span><span class="sxs-lookup"><span data-stu-id="65b39-111">Build your project automatically before launching a debugging session.</span></span> <span data-ttu-id="65b39-112">Als u het opnieuw bouwt, zorgt u ervoor dat u fouten opspoort in de nieuwste versie van uw code.</span><span class="sxs-lookup"><span data-stu-id="65b39-112">Rebuilding ensures that you debug the latest version of your code.</span></span>

<span data-ttu-id="65b39-113">Een build-taak configureren:</span><span class="sxs-lookup"><span data-stu-id="65b39-113">Configure a build task:</span></span>

1. <span data-ttu-id="65b39-114">Voer in het **opdracht palet**de opdracht **standaard build-taak configureren** uit.</span><span class="sxs-lookup"><span data-stu-id="65b39-114">In the **Command Palette**, run the **Configure Default Build Task** command.</span></span>

   ![Taak configureren standaard maken uitvoeren](media/using-vscode-for-debugging-compiled-cmdlets/configure-default-build-task.png)

1. <span data-ttu-id="65b39-116">Kies in het dialoog venster **Selecteer een taak die u wilt configureren** **tasks.jsop bestand maken van sjabloon**.</span><span class="sxs-lookup"><span data-stu-id="65b39-116">In the **Select a task to configure** dialog, choose **Create tasks.json file from template**.</span></span>

1. <span data-ttu-id="65b39-117">Kies in het dialoog venster **een taak sjabloon selecteren** de optie **.net core**.</span><span class="sxs-lookup"><span data-stu-id="65b39-117">In the **Select a Task Template** dialog, choose **.NET Core**.</span></span>

<span data-ttu-id="65b39-118">Er wordt een nieuw `tasks.json` bestand gemaakt als er nog geen bestaat.</span><span class="sxs-lookup"><span data-stu-id="65b39-118">A new `tasks.json` file is created if one doesn't exist yet.</span></span>

<span data-ttu-id="65b39-119">Uw build-taak testen:</span><span class="sxs-lookup"><span data-stu-id="65b39-119">To test your build task:</span></span>

1. <span data-ttu-id="65b39-120">Voer in het **opdracht palet**de opdracht **taak maken** uit.</span><span class="sxs-lookup"><span data-stu-id="65b39-120">In the **Command Palette**, run the **Run Build Task** command.</span></span>

1. <span data-ttu-id="65b39-121">Kies in het dialoog venster **Selecteer de taak die u wilt uitvoeren** op **bouwen**.</span><span class="sxs-lookup"><span data-stu-id="65b39-121">In the **Select the build task to run** dialog, choose **build**.</span></span>

### <a name="information-about-dll-files-being-locked"></a><span data-ttu-id="65b39-122">Informatie over DLL-bestanden die worden vergrendeld</span><span class="sxs-lookup"><span data-stu-id="65b39-122">Information about DLL files being locked</span></span>

<span data-ttu-id="65b39-123">Standaard wordt in een geslaagde build geen uitvoer weer gegeven in het deel venster Terminal.</span><span class="sxs-lookup"><span data-stu-id="65b39-123">By default, a successful build doesn't show output in the terminal pane.</span></span> <span data-ttu-id="65b39-124">Als er geen uitvoer wordt weer geven die het tekst **Project bestand**bevat, moet u het `tasks.json` bestand bewerken.</span><span class="sxs-lookup"><span data-stu-id="65b39-124">If you see output that contains the text **Project file doesn't exist**, you should edit the `tasks.json` file.</span></span> <span data-ttu-id="65b39-125">Neem het expliciete pad op naar het C#-project, uitgedrukt als `"${workspaceFolder}/myModule"` .</span><span class="sxs-lookup"><span data-stu-id="65b39-125">Include the explicit path to the C# project expressed as `"${workspaceFolder}/myModule"`.</span></span> <span data-ttu-id="65b39-126">In dit voor beeld `myModule` is de naam van de projectmap.</span><span class="sxs-lookup"><span data-stu-id="65b39-126">In this example, `myModule` is the name of the project folder.</span></span> <span data-ttu-id="65b39-127">Deze vermelding moet als volgt worden weer gegeven na de `build` vermelding in de `args` lijst:</span><span class="sxs-lookup"><span data-stu-id="65b39-127">This entry must go after the `build` entry in the `args` list as follows:</span></span>

```json
    {
        "label": "build",
        "command": "dotnet",
        "type": "shell",
        "args": [
            "build",
            "${workspaceFolder}/myModule",
            // Ask dotnet build to generate full paths for file names.
            "/property:GenerateFullPaths=true",
            // Do not generate summary otherwise it leads to duplicate errors in Problems panel
            "/consoleloggerparameters:NoSummary",
        ],
        "group": "build",
        "presentation": {
            "reveal": "silent"
        },
        "problemMatcher": "$msCompile"
    }
```

<span data-ttu-id="65b39-128">Bij het opsporen van fouten wordt uw module-DLL geïmporteerd in de Power shell-sessie in de VS code-Terminal.</span><span class="sxs-lookup"><span data-stu-id="65b39-128">When debugging, your module DLL is imported into the PowerShell session in the VS Code terminal.</span></span> <span data-ttu-id="65b39-129">De DLL wordt vergrendeld.</span><span class="sxs-lookup"><span data-stu-id="65b39-129">The DLL becomes locked.</span></span> <span data-ttu-id="65b39-130">Het volgende bericht wordt weer gegeven wanneer u de taak maken uitvoert zonder de terminal sessie te sluiten:</span><span class="sxs-lookup"><span data-stu-id="65b39-130">The following message is displayed when you run the build task without closing the terminal session:</span></span>

```Output
Could not copy "obj\Debug\netstandard2.0\myModule.dll" to "bin\Debug\netstandard2.0\myModule.dll"`.
```

<span data-ttu-id="65b39-131">Terminal sessies moeten worden gesloten voordat u opnieuw bouwt.</span><span class="sxs-lookup"><span data-stu-id="65b39-131">Terminal sessions must be closed before you rebuild.</span></span>

## <a name="setting-up-the-debugger"></a><span data-ttu-id="65b39-132">Het fout opsporingsprogramma instellen</span><span class="sxs-lookup"><span data-stu-id="65b39-132">Setting up the debugger</span></span>

<span data-ttu-id="65b39-133">Als u fouten wilt opsporen in de Power shell-cmdlet, moet u een aangepaste start configuratie instellen.</span><span class="sxs-lookup"><span data-stu-id="65b39-133">To debug the PowerShell cmdlet, you need to set up a custom launch configuration.</span></span> <span data-ttu-id="65b39-134">Deze configuratie wordt gebruikt voor het volgende:</span><span class="sxs-lookup"><span data-stu-id="65b39-134">This configuration is used to:</span></span>

- <span data-ttu-id="65b39-135">Uw bron code maken</span><span class="sxs-lookup"><span data-stu-id="65b39-135">Build your source code</span></span>
- <span data-ttu-id="65b39-136">Power shell starten met de module geladen</span><span class="sxs-lookup"><span data-stu-id="65b39-136">Start PowerShell with your module loaded</span></span>
- <span data-ttu-id="65b39-137">Power shell geopend laten in het deel venster Terminal</span><span class="sxs-lookup"><span data-stu-id="65b39-137">Leave PowerShell open in the terminal pane</span></span>

<span data-ttu-id="65b39-138">Wanneer u de cmdlet aanroept in de terminal sessie, stopt het fout opsporingsprogramma bij eventuele onderbrekings punten die in de bron code zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="65b39-138">When you invoke your cmdlet in the terminal session, the debugger stops at any breakpoints set in your source code.</span></span>

### <a name="configuring-launchjson-for-powershell-core"></a><span data-ttu-id="65b39-139">launch.jsconfigureren voor Power shell core</span><span class="sxs-lookup"><span data-stu-id="65b39-139">Configuring launch.json for PowerShell Core</span></span>

1. <span data-ttu-id="65b39-140">Installeer de [C# voor Visual Studio code][] extension</span><span class="sxs-lookup"><span data-stu-id="65b39-140">Install the [C# for Visual Studio Code][] extension</span></span>

1. <span data-ttu-id="65b39-141">Voeg in het deel venster fout opsporing een configuratie voor fout opsporing toe</span><span class="sxs-lookup"><span data-stu-id="65b39-141">In the Debug pane, add a debug configuration</span></span>

1. <span data-ttu-id="65b39-142">Kies in het `Select environment` dialoog venster `.NET Core`</span><span class="sxs-lookup"><span data-stu-id="65b39-142">In the `Select environment` dialog, choose `.NET Core`</span></span>

1. <span data-ttu-id="65b39-143">Het `launch.json` bestand wordt geopend in de editor.</span><span class="sxs-lookup"><span data-stu-id="65b39-143">The `launch.json` file is opened in the editor.</span></span> <span data-ttu-id="65b39-144">Met de cursor in de `configurations` matrix, ziet u de `configuration` kiezer.</span><span class="sxs-lookup"><span data-stu-id="65b39-144">With your cursor inside the `configurations` array, you see the `configuration` picker.</span></span> <span data-ttu-id="65b39-145">Als u deze lijst niet ziet, selecteert u **Configuratie toevoegen**.</span><span class="sxs-lookup"><span data-stu-id="65b39-145">If you don't see this list, select **Add Configuration**.</span></span>

1. <span data-ttu-id="65b39-146">Als u een standaard configuratie voor fout opsporing wilt maken, selecteert u de **app .net Core-Console starten**:</span><span class="sxs-lookup"><span data-stu-id="65b39-146">To create a default debug configuration, select **Launch .NET Core Console App**:</span></span>

   ![.NET Core-Console-app starten](media/using-vscode-for-debugging-compiled-cmdlets/add-configuration-dialog.png)

1. <span data-ttu-id="65b39-148">Bewerk de `name` `program` velden,, `args` en `console` als volgt:</span><span class="sxs-lookup"><span data-stu-id="65b39-148">Edit the `name`, `program`, `args`, and `console` fields as follows:</span></span>

   ```json
    {
        "name": "PowerShell cmdlets: pwsh",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "pwsh",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

<span data-ttu-id="65b39-149">Het `program` veld wordt gebruikt om te starten `pwsh` zodat de cmdlet die wordt opgespoord, kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="65b39-149">The `program` field is used to launch `pwsh` so that the cmdlet being debugged can be run.</span></span> <span data-ttu-id="65b39-150">Het `-NoExit` argument voor komt dat de Power shell-sessie wordt afgesloten zodra de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="65b39-150">The `-NoExit` argument prevents the PowerShell session from exiting as soon as the module is imported.</span></span>
<span data-ttu-id="65b39-151">Het pad in het `Import-Module` argument is het standaarduitvoer traject voor builds wanneer u de hand leiding voor het [schrijven van draag bare modules][] hebt gevolgd.</span><span class="sxs-lookup"><span data-stu-id="65b39-151">The path in the `Import-Module` argument is the default build output path when you've followed the [Writing Portable Modules][] guide.</span></span> <span data-ttu-id="65b39-152">Als u een module manifest ( `.psd1` bestand) hebt gemaakt, moet u het pad hiervoor gebruiken.</span><span class="sxs-lookup"><span data-stu-id="65b39-152">If you've created a module manifest (`.psd1` file), you should use the path to that instead.</span></span> <span data-ttu-id="65b39-153">Het `/` padscheidingsteken werkt in Windows, Linux en macOS.</span><span class="sxs-lookup"><span data-stu-id="65b39-153">The `/` path separator works on Windows, Linux, and macOS.</span></span> <span data-ttu-id="65b39-154">U moet de geïntegreerde Terminal gebruiken om de Power shell-opdrachten uit te voeren waarvoor u fouten wilt opsporen.</span><span class="sxs-lookup"><span data-stu-id="65b39-154">You must use the integrated terminal to run the PowerShell commands you want to debug.</span></span>

### <a name="configuring-launchjson-for-windows-powershell"></a><span data-ttu-id="65b39-155">launch.jsconfigureren voor voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="65b39-155">Configuring launch.json for Windows PowerShell</span></span>

<span data-ttu-id="65b39-156">Deze start configuratie werkt voor het testen van uw cmdlets in Windows Power shell ( `powershell.exe` ).</span><span class="sxs-lookup"><span data-stu-id="65b39-156">This launch configuration works for testing your cmdlets in Windows PowerShell (`powershell.exe`).</span></span>
<span data-ttu-id="65b39-157">Maak een tweede start configuratie met de volgende wijzigingen:</span><span class="sxs-lookup"><span data-stu-id="65b39-157">Create a second launch configuration with the following changes:</span></span>

1. <span data-ttu-id="65b39-158">`name` moet worden `PowerShell cmdlets: powershell`</span><span class="sxs-lookup"><span data-stu-id="65b39-158">`name` should be `PowerShell cmdlets: powershell`</span></span>

1. <span data-ttu-id="65b39-159">`type` moet worden `clr`</span><span class="sxs-lookup"><span data-stu-id="65b39-159">`type` should be `clr`</span></span>

1. <span data-ttu-id="65b39-160">`program` moet worden `powershell`</span><span class="sxs-lookup"><span data-stu-id="65b39-160">`program` should be `powershell`</span></span>

   <span data-ttu-id="65b39-161">Dit ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="65b39-161">It should look like this:</span></span>

   ```json
    {
        "name": "PowerShell cmdlets: powershell",
        "type": "clr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "powershell",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

## <a name="launching-a-debugging-session"></a><span data-ttu-id="65b39-162">Een foutopsporingssessie starten</span><span class="sxs-lookup"><span data-stu-id="65b39-162">Launching a debugging session</span></span>

<span data-ttu-id="65b39-163">Alles is nu klaar om te beginnen met de fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="65b39-163">Now everything is ready to begin debugging.</span></span>

- <span data-ttu-id="65b39-164">Plaats een onderbrekings punt in de bron code voor de cmdlet waarvoor u fouten wilt opsporen:</span><span class="sxs-lookup"><span data-stu-id="65b39-164">Place a breakpoint in the source code for the cmdlet you want to debug:</span></span>

  ![Een onderbrekings punt wordt weer gegeven als een rode stip in de rugmarge](media/using-vscode-for-debugging-compiled-cmdlets/set-breakpoint.png)

- <span data-ttu-id="65b39-166">Zorg ervoor dat de relevante configuratie van de **Power shell-cmdlets** is geselecteerd in de vervolg keuzelijst configuratie in de weer gave **fout opsporing** :</span><span class="sxs-lookup"><span data-stu-id="65b39-166">Ensure that the relevant **PowerShell cmdlets** configuration is selected in the configuration drop-down menu in the **Debug** view:</span></span>

  ![De start configuratie selecteren](media/using-vscode-for-debugging-compiled-cmdlets/select-launch-configuration.png)

- <span data-ttu-id="65b39-168">Druk op <kbd>F5</kbd> of klik op de knop **fout opsporing starten**</span><span class="sxs-lookup"><span data-stu-id="65b39-168">Press <kbd>F5</kbd> or click on the **Start Debugging** button</span></span>

- <span data-ttu-id="65b39-169">Ga naar het Terminal venster en roep uw cmdlet aan:</span><span class="sxs-lookup"><span data-stu-id="65b39-169">Switch to the terminal pane and invoke your cmdlet:</span></span>

  ![De cmdlet aanroepen](media/using-vscode-for-debugging-compiled-cmdlets/invoke-the-cmdlet.png)

- <span data-ttu-id="65b39-171">Uitvoering stopt bij het onderbrekings punt:</span><span class="sxs-lookup"><span data-stu-id="65b39-171">Execution stops at the breakpoint:</span></span>

  ![Uitvoeringen stopt bij onderbrekings punt](media/using-vscode-for-debugging-compiled-cmdlets/stopped-at-breakpoint.png)

<span data-ttu-id="65b39-173">U kunt de bron code stapsgewijs door lopen, variabelen inspecteren en de aanroep stack controleren.</span><span class="sxs-lookup"><span data-stu-id="65b39-173">You can step through the source code, inspect variables, and inspect the call stack.</span></span>

<span data-ttu-id="65b39-174">Als u de fout opsporing wilt beëindigen, klikt u in de werk balk fout opsporing op **stoppen** of drukt u op <kbd>SHIFT</kbd> - <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="65b39-174">To end debugging, click **Stop** in the debug toolbar or press <kbd>Shift</kbd>-<kbd>F5</kbd>.</span></span> <span data-ttu-id="65b39-175">De shell die wordt gebruikt voor fout opsporing sluit af en geeft de vergren deling van het gecompileerde DLL-bestand vrij.</span><span class="sxs-lookup"><span data-stu-id="65b39-175">The shell used for debugging exits and releases the lock on the compiled DLL file.</span></span>

<!-- reference links -->
[Fout opsporing in Visual Studio code]: https://code.visualstudio.com/docs/editor/debugging
[Debugging in Visual Studio Code]: https://code.visualstudio.com/docs/editor/debugging
[Visual Studio Code gebruiken voor externe bewerking en foutopsporing]: using-vscode-for-remote-editing-and-debugging.md
[Using Visual Studio Code for remote editing and debugging]: using-vscode-for-remote-editing-and-debugging.md
[Draag bare modules schrijven]: ../writing-portable-modules.md
[Writing Portable Modules]: ../writing-portable-modules.md
[C# voor Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
[C# for Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
