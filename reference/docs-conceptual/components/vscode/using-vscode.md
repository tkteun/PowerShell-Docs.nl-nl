---
title: Visual Studio code for Power Shell Development gebruiken
description: Visual Studio code for Power Shell Development gebruiken
ms.date: 08/06/2018
ms.openlocfilehash: 0e082b74f99d214749f10224fb5aaf41e2ef8951
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325234"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="c80de-103">Visual Studio code for Power Shell Development gebruiken</span><span class="sxs-lookup"><span data-stu-id="c80de-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="c80de-104">Naast [Power shell ISE][ise]is Power shell ook goed ondersteund in Visual Studio code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="c80de-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="c80de-105">Bovendien wordt de ISE niet ondersteund met Power shell core, terwijl VSCode wordt ondersteund voor Power shell Core op alle platformen (Windows, macOS en Linux)</span><span class="sxs-lookup"><span data-stu-id="c80de-105">Furthermore, the ISE is not supported with PowerShell Core, while VSCode is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="c80de-106">U kunt VSCode in Windows met Power shell versie 5 gebruiken met behulp van Windows 10 of door [Windows Management Framework 5,0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) te installeren voor een down level Windows oss (bijvoorbeeld Windows 8,1, enzovoort).</span><span class="sxs-lookup"><span data-stu-id="c80de-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="c80de-107">Controleer voordat u begint of Power shell op uw systeem is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c80de-107">Before starting it, please make sure PowerShell exists on your system.</span></span> <span data-ttu-id="c80de-108">Voor moderne werk belastingen op Windows, macOS en Linux raadpleegt u:</span><span class="sxs-lookup"><span data-stu-id="c80de-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="c80de-109">[Power shell Core installeren in Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="c80de-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="c80de-110">[Power shell core in macOS installeren][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="c80de-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="c80de-111">[Power shell Core installeren in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="c80de-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="c80de-112">Zie [Windows Power Shell installeren][install-winps]voor traditionele workloads van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c80de-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="c80de-113">Bewerken met VSCode</span><span class="sxs-lookup"><span data-stu-id="c80de-113">Editing with VSCode</span></span>

1. [<span data-ttu-id="c80de-114">VSCode installeren</span><span class="sxs-lookup"><span data-stu-id="c80de-114">Installing VSCode</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

   - <span data-ttu-id="c80de-115">**Linux**: Volg de installatie-instructies op de pagina [actieve VSCode op Linux](https://code.visualstudio.com/docs/setup/linux)</span><span class="sxs-lookup"><span data-stu-id="c80de-115">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>
   - <span data-ttu-id="c80de-116">**macOS**: Volg de installatie-instructies op de pagina [actieve VSCode op macOS](https://code.visualstudio.com/docs/setup/mac)</span><span class="sxs-lookup"><span data-stu-id="c80de-116">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="c80de-117">Bij macOS moet u OpenSSL installeren om de Power shell-extensie correct te laten werken.</span><span class="sxs-lookup"><span data-stu-id="c80de-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="c80de-118">De eenvoudigste manier om dit te doen is door [homebrew](https://brew.sh/) te installeren en `brew install openssl`vervolgens uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c80de-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="c80de-119">VSCode kan nu de Power shell-uitbrei ding laden.</span><span class="sxs-lookup"><span data-stu-id="c80de-119">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="c80de-120">**Windows**: Volg de installatie-instructies op de pagina [actieve VSCode op Windows](https://code.visualstudio.com/docs/setup/windows)</span><span class="sxs-lookup"><span data-stu-id="c80de-120">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

2. <span data-ttu-id="c80de-121">Power shell-extensie installeren</span><span class="sxs-lookup"><span data-stu-id="c80de-121">Installing PowerShell Extension</span></span>

   - <span data-ttu-id="c80de-122">Start de VSCode-app op:</span><span class="sxs-lookup"><span data-stu-id="c80de-122">Launch the VSCode app by:</span></span>
     - <span data-ttu-id="c80de-123">**Windows**: typen `code` in uw Power shell-sessie</span><span class="sxs-lookup"><span data-stu-id="c80de-123">**Windows**: typing `code` in your PowerShell session</span></span>
     - <span data-ttu-id="c80de-124">**Linux**: typen `code` in uw Terminal</span><span class="sxs-lookup"><span data-stu-id="c80de-124">**Linux**: typing `code` in your terminal</span></span>
     - <span data-ttu-id="c80de-125">**macOS**: typen `code` in uw Terminal</span><span class="sxs-lookup"><span data-stu-id="c80de-125">**macOS**: typing `code` in your terminal</span></span>
   - <span data-ttu-id="c80de-126">Start **snel openen** door op <kbd>CTRL</kbd>+<kbd>P</kbd> te drukken (<kbd>cmd</kbd>+<kbd>p</kbd> op Mac).</span><span class="sxs-lookup"><span data-stu-id="c80de-126">Launch **Quick Open** by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>P</kbd> on Mac).</span></span>
   - <span data-ttu-id="c80de-127">Typ `ext install powershell` en druk op **Enter**in snel openen.</span><span class="sxs-lookup"><span data-stu-id="c80de-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
   - <span data-ttu-id="c80de-128">De weer gave **extensies** wordt weer gegeven op de balk aan de zijkant.</span><span class="sxs-lookup"><span data-stu-id="c80de-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="c80de-129">Selecteer de Power shell-extensie van micro soft.</span><span class="sxs-lookup"><span data-stu-id="c80de-129">Select the PowerShell extension from Microsoft.</span></span>
     <span data-ttu-id="c80de-130">U ziet nu het volgende:</span><span class="sxs-lookup"><span data-stu-id="c80de-130">You should see something like below:</span></span>

     ![VSCode](../../images/using-vscode/vscode.png)

   - <span data-ttu-id="c80de-132">Klik op de knop **installeren** in de Power shell-extensie van micro soft.</span><span class="sxs-lookup"><span data-stu-id="c80de-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   - <span data-ttu-id="c80de-133">Na de installatie ziet u de knop **installeren** om opnieuw te **laden**.</span><span class="sxs-lookup"><span data-stu-id="c80de-133">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="c80de-134">Klik op **opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="c80de-134">Click on **Reload**.</span></span>
   - <span data-ttu-id="c80de-135">Nadat VSCode opnieuw is geladen, bent u klaar om te bewerken.</span><span class="sxs-lookup"><span data-stu-id="c80de-135">After VSCode has reload, you are ready for editing.</span></span>

<span data-ttu-id="c80de-136">Als u bijvoorbeeld een nieuw bestand wilt maken, klikt u op **bestand-> nieuw**.</span><span class="sxs-lookup"><span data-stu-id="c80de-136">For example, to create a new file, click **File->New**.</span></span> <span data-ttu-id="c80de-137">Als u deze wilt opslaan, klikt u op **bestand-> opslaan** en geeft u een bestands naam `HelloWorld.ps1`op.</span><span class="sxs-lookup"><span data-stu-id="c80de-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span> <span data-ttu-id="c80de-138">Als u het bestand wilt sluiten, klikt u op ' x ' naast de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="c80de-138">To close the file, click on "x" next to the file name.</span></span> <span data-ttu-id="c80de-139">Als u VSCode wilt afsluiten, wordt **het bestand > afgesloten**.</span><span class="sxs-lookup"><span data-stu-id="c80de-139">To exit VSCode, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="c80de-140">De Power shell-uitbrei ding installeren op beperkte systemen</span><span class="sxs-lookup"><span data-stu-id="c80de-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="c80de-141">Sommige systemen zijn zodanig ingesteld dat alle code handtekeningen moeten worden gecontroleerd en daarom moeten Power shell-editor Services hand matig worden goedgekeurd om te worden uitgevoerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="c80de-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="c80de-142">Een groepsbeleid update die het uitvoerings beleid wijzigt, is waarschijnlijk een mogelijke oorzaak als u de Power shell-uitbrei ding hebt geïnstalleerd maar een fout ziet zoals:</span><span class="sxs-lookup"><span data-stu-id="c80de-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="c80de-143">Voor het hand matig goed keuren van Power shell-editor Services en de Power shell-extensie voor VSCode een Power shell-prompt openen en uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="c80de-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="c80de-144">U wordt gevraagd of u software van deze niet-vertrouwde uitgever wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c80de-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span> <span data-ttu-id="c80de-145">Typ `R` om het bestand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c80de-145">Type `R` to run the file.</span></span> <span data-ttu-id="c80de-146">Open vervolgens VSCode en controleer of de Power shell-extensie goed werkt.</span><span class="sxs-lookup"><span data-stu-id="c80de-146">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="c80de-147">Als u nog steeds problemen ondervindt, laat het ons dan weten op [github](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="c80de-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="c80de-148">Een versie van Power shell kiezen die moet worden gebruikt met de extensie</span><span class="sxs-lookup"><span data-stu-id="c80de-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="c80de-149">Met Power shell Core installeren naast Windows Power shell is het nu mogelijk om een bepaalde versie van Power shell te gebruiken met de Power shell-extensie.</span><span class="sxs-lookup"><span data-stu-id="c80de-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="c80de-150">Gebruik de volgende stappen om de versie te kiezen:</span><span class="sxs-lookup"><span data-stu-id="c80de-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="c80de-151">Open de opdracht pallet (<kbd>CTRL</kbd>+<kbd>+ SHIFT</kbd>+<kbd>p</kbd> op Windows & Linux, <kbd>cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>p</kbd> op macOS).</span><span class="sxs-lookup"><span data-stu-id="c80de-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="c80de-152">Zoek naar "Session".</span><span class="sxs-lookup"><span data-stu-id="c80de-152">Search for "Session".</span></span>
1. <span data-ttu-id="c80de-153">Klik op Power shell: Menu sessie weer geven.</span><span class="sxs-lookup"><span data-stu-id="c80de-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="c80de-154">Kies de versie van Power shell die u wilt gebruiken in de lijst, bijvoorbeeld Power shell core.</span><span class="sxs-lookup"><span data-stu-id="c80de-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c80de-155">Deze functie bekijkt enkele bekende paden op verschillende besturings systemen om installatie locaties van Power shell te detecteren.</span><span class="sxs-lookup"><span data-stu-id="c80de-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="c80de-156">Als u Power shell hebt geïnstalleerd op een niet-typische locatie, wordt deze mogelijk niet eerst weer gegeven in het menu sessie.</span><span class="sxs-lookup"><span data-stu-id="c80de-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="c80de-157">U kunt het menu sessie uitbreiden door [uw eigen aangepaste paden toe te voegen](#adding-your-own-powershell-paths-to-the-session-menu) , zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="c80de-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="c80de-158">Er is een andere manier om naar het menu sessie te gaan.</span><span class="sxs-lookup"><span data-stu-id="c80de-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="c80de-159">Wanneer een Power shell-bestand is geopend in uw editor, ziet u een groen versie nummer in de rechter benedenhoek.</span><span class="sxs-lookup"><span data-stu-id="c80de-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="c80de-160">Als u op dit versie nummer klikt, gaat u naar het menu sessie.</span><span class="sxs-lookup"><span data-stu-id="c80de-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="c80de-161">Uw eigen Power shell-paden toevoegen aan het menu sessie</span><span class="sxs-lookup"><span data-stu-id="c80de-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="c80de-162">U kunt andere uitvoer bare Power shell-paden toevoegen aan het menu sessie via een VSCode-instelling.</span><span class="sxs-lookup"><span data-stu-id="c80de-162">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="c80de-163">Voeg een item toe aan de `powershell.powerShellAdditionalExePaths` lijst of maak een lijst als deze niet bestaat in `settings.json`uw:</span><span class="sxs-lookup"><span data-stu-id="c80de-163">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

<span data-ttu-id="c80de-164">Elk item moet het volgende bevatten:</span><span class="sxs-lookup"><span data-stu-id="c80de-164">Each item must have:</span></span>

* <span data-ttu-id="c80de-165">`exePath`: Het pad naar het `pwsh` of `powershell` het uitvoer bare bestand.</span><span class="sxs-lookup"><span data-stu-id="c80de-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="c80de-166">`versionName`: De tekst die wordt weer gegeven in het menu van de sessie.</span><span class="sxs-lookup"><span data-stu-id="c80de-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="c80de-167">U kunt de standaard-Power shell-versie instellen op `powershell.powerShellDefaultVersion` het gebruik van de instelling door dit in te stellen op de tekst die wordt `versionName` weer gegeven in het menu sessie (ook wel de in de laatste instelling):</span><span class="sxs-lookup"><span data-stu-id="c80de-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

<span data-ttu-id="c80de-168">Wanneer u deze instelling hebt ingesteld, start u VSCode opnieuw of gebruikt u de ' ontwikkel aars: Het venster opdracht pallet actie opnieuw laden om het huidige VSCode-venster opnieuw te laden.</span><span class="sxs-lookup"><span data-stu-id="c80de-168">Once you've set this setting, restart VSCode or use the the "Developer: Reload Window" command pallet action to reload the current VSCode window.</span></span>

<span data-ttu-id="c80de-169">Als u het menu sessie opent, ziet u nu uw extra Power shell-versies!</span><span class="sxs-lookup"><span data-stu-id="c80de-169">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="c80de-170">Als u Power shell bouwt vanaf een bron, is dit een fantastische manier om uw lokale build van Power shell te testen.</span><span class="sxs-lookup"><span data-stu-id="c80de-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="c80de-171">Configuratie-instellingen voor VSCode</span><span class="sxs-lookup"><span data-stu-id="c80de-171">Configuration settings for VSCode</span></span>

<span data-ttu-id="c80de-172">Door de stappen in de vorige alinea te gebruiken, kunt u configuratie- `settings.json`instellingen toevoegen in.</span><span class="sxs-lookup"><span data-stu-id="c80de-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="c80de-173">We raden de volgende configuratie-instellingen aan voor VSCode:</span><span class="sxs-lookup"><span data-stu-id="c80de-173">We recommend the following configuration settings for VSCode:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="c80de-174">Als u niet wilt dat deze instellingen van invloed zijn op alle bestands typen, kunt u met VSCode ook configuraties per taal configureren.</span><span class="sxs-lookup"><span data-stu-id="c80de-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="c80de-175">Maak een taalspecifieke instelling door instellingen in een `[<language-name>]` veld in te voeren.</span><span class="sxs-lookup"><span data-stu-id="c80de-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="c80de-176">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="c80de-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="c80de-177">Zie [Wat is bestands codering](understanding-file-encoding.md)? voor meer informatie over bestands codering in VSCode.</span><span class="sxs-lookup"><span data-stu-id="c80de-177">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="c80de-178">Fout opsporing met VSCode</span><span class="sxs-lookup"><span data-stu-id="c80de-178">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="c80de-179">Geen-werk ruimte: fout opsporing</span><span class="sxs-lookup"><span data-stu-id="c80de-179">No-workspace debugging</span></span>

<span data-ttu-id="c80de-180">Vanaf VSCode-versie 1,9 kunt u fouten opsporen in Power shell-scripts zonder dat u de map met het Power shell-script hoeft te openen.</span><span class="sxs-lookup"><span data-stu-id="c80de-180">As of VSCode version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="c80de-181">Open het Power shell-script bestand met **File-> open file...** , stel een onderbrekings punt in op een regel (druk op <kbd>F9</kbd>) en druk vervolgens op <kbd>F5</kbd> om de fout opsporing te starten.</span><span class="sxs-lookup"><span data-stu-id="c80de-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press <kbd>F9</kbd>) and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="c80de-182">Het deel venster acties voor fout opsporing wordt weer gegeven, waarin u de fout opsporing, stap, hervatten en stoppen van het fout opsporingsprogramma kunt onderbreken.</span><span class="sxs-lookup"><span data-stu-id="c80de-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="c80de-183">Fout opsporing voor werk ruimten</span><span class="sxs-lookup"><span data-stu-id="c80de-183">Workspace debugging</span></span>

<span data-ttu-id="c80de-184">Fout opsporing voor werk ruimten verwijst naar fout opsporing in de context van een map die u hebt geopend in Visual Studio code met behulp van **openen map...** in het menu **bestand** .</span><span class="sxs-lookup"><span data-stu-id="c80de-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span> <span data-ttu-id="c80de-185">De map die u opent, is doorgaans uw Power shell-projectmap en/of de hoofdmap van uw Git-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="c80de-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="c80de-186">Zelfs in deze modus kunt u de fout opsporing van het momenteel geselecteerde Power shell-script starten door simpelweg op <kbd>F5</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="c80de-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="c80de-187">Met fout opsporing in werk ruimten kunt u echter meerdere debug-configuraties definiëren, anders dan alleen fouten opsporen in het bestand dat momenteel is geopend.</span><span class="sxs-lookup"><span data-stu-id="c80de-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="c80de-188">U kunt bijvoorbeeld een configuratie toevoegen aan:</span><span class="sxs-lookup"><span data-stu-id="c80de-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="c80de-189">Schadelijke tests starten in het fout opsporingsprogramma</span><span class="sxs-lookup"><span data-stu-id="c80de-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="c80de-190">Een specifiek bestand met argumenten in het fout opsporingsprogramma starten</span><span class="sxs-lookup"><span data-stu-id="c80de-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="c80de-191">Een interactieve sessie starten in het fout opsporingsprogramma</span><span class="sxs-lookup"><span data-stu-id="c80de-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="c80de-192">Het fout opsporingsprogramma koppelen aan een Power shell-hostproces</span><span class="sxs-lookup"><span data-stu-id="c80de-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="c80de-193">Voer de volgende stappen uit om het configuratie bestand voor fout opsporing te maken:</span><span class="sxs-lookup"><span data-stu-id="c80de-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="c80de-194">Open de weer gave **fout opsporing** door op <kbd>CTRL</kbd>+<kbd>+ SHIFT</kbd>+<kbd>d</kbd> te drukken (<kbd>cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>d</kbd> op Mac).</span><span class="sxs-lookup"><span data-stu-id="c80de-194">Open the **Debug** view by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> on Mac).</span></span>
  2. <span data-ttu-id="c80de-195">Klik op het pictogram vistuig **configureren** op de werk balk.</span><span class="sxs-lookup"><span data-stu-id="c80de-195">Click the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="c80de-196">U wordt door VSCode gevraagd om **omgeving te selecteren**.</span><span class="sxs-lookup"><span data-stu-id="c80de-196">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="c80de-197">Kies **Power shell**.</span><span class="sxs-lookup"><span data-stu-id="c80de-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="c80de-198">Wanneer u dit doet, maakt VSCode een map en een bestand '. vscode\launch.json ' in de hoofdmap van uw werkruimte map.</span><span class="sxs-lookup"><span data-stu-id="c80de-198">When you do this, VSCode creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span> <span data-ttu-id="c80de-199">Hier wordt de configuratie van de fout opsporing opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c80de-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="c80de-200">Als uw bestanden zich in een Git-opslag plaats bevinden, wilt u meestal het bestand Launch. json door voeren.</span><span class="sxs-lookup"><span data-stu-id="c80de-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span> <span data-ttu-id="c80de-201">De inhoud van het bestand Launch. json is:</span><span class="sxs-lookup"><span data-stu-id="c80de-201">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="c80de-202">Dit duidt op de veelvoorkomende scenario's voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="c80de-202">This represents the common debug scenarios.</span></span> <span data-ttu-id="c80de-203">Wanneer u dit bestand echter in de editor opent, ziet u een knop **Configuratie toevoegen...** .</span><span class="sxs-lookup"><span data-stu-id="c80de-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="c80de-204">U kunt op deze knop klikken om meer configuratie van Power Shell-fout opsporing toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="c80de-204">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="c80de-205">Power shell is **een handige configuratie om toe te voegen. Script**starten.</span><span class="sxs-lookup"><span data-stu-id="c80de-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="c80de-206">Met deze configuratie kunt u een specifiek bestand opgeven met optionele argumenten die moeten worden gestart wanneer u op <kbd>F5</kbd> drukt, ongeacht welk bestand momenteel actief is in de editor.</span><span class="sxs-lookup"><span data-stu-id="c80de-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="c80de-207">Zodra de configuratie van de fout opsporing is ingesteld, kunt u selecteren welke configuratie u tijdens een foutopsporingssessie wilt gebruiken door er een te selecteren in de vervolg keuzelijst debug-configuratie op de werk balk van de weer gave van de **fout** opsporing.</span><span class="sxs-lookup"><span data-stu-id="c80de-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="c80de-208">Er zijn enkele blogs die handig kunnen zijn om aan de slag te gaan met Power shell-extensie voor Visual Studio code:</span><span class="sxs-lookup"><span data-stu-id="c80de-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="c80de-209">[Power shell-uitbrei ding][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="c80de-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="c80de-210">[Power shell-scripts schrijven en fouten opsporen in Visual Studio code][debug]</span><span class="sxs-lookup"><span data-stu-id="c80de-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="c80de-211">[Fout opsporing van Visual Studio code guidance][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="c80de-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="c80de-212">[Fout opsporing in Power shell in Visual Studio code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="c80de-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="c80de-213">[Aan de slag met Power shell-ontwikkeling in Visual Studio code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="c80de-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="c80de-214">[Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="c80de-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="c80de-215">[Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="c80de-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="c80de-216">[Fout opsporing voor Power shell-script in Visual Studio code – deel 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="c80de-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="c80de-217">[Fout opsporing voor Power shell-script in Visual Studio code – deel 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="c80de-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="c80de-218">Power shell-uitbrei ding voor VSCode</span><span class="sxs-lookup"><span data-stu-id="c80de-218">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="c80de-219">De bron code van de Power shell-extensie vindt u op [github](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="c80de-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
