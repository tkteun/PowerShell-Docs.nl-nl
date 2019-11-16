---
title: Visual Studio code for Power Shell Development gebruiken
description: Visual Studio code for Power Shell Development gebruiken
ms.date: 11/07/2019
ms.openlocfilehash: 4f197e71d3b79828f466584f5d862415726818b1
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117401"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="e409c-103">Visual Studio code for Power Shell Development gebruiken</span><span class="sxs-lookup"><span data-stu-id="e409c-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="e409c-104">Naast [Power shell ISE][ise]is Power shell ook goed ondersteund in Visual Studio code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="e409c-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="e409c-105">De ISE wordt niet ondersteund met Power shell core, maar VSCode wordt ondersteund voor Power shell Core op alle platforms: Windows, macOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="e409c-105">The ISE isn't supported with PowerShell Core, but VSCode is supported for PowerShell Core on all platforms: Windows, macOS, and Linux.</span></span>

<span data-ttu-id="e409c-106">U kunt VSCode in Windows met Power shell versie 5 gebruiken met behulp van Windows 10 of door Windows Management Framework 5,1 te installeren voor down level Windows OSs, zoals Windows 8,1.</span><span class="sxs-lookup"><span data-stu-id="e409c-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing Windows Management Framework 5.1 for down-level Windows OSs such as Windows 8.1.</span></span> <span data-ttu-id="e409c-107">Zie [WMF 5,1 installeren en configureren](/powershell/scripting/wmf/setup/install-configure)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e409c-107">For more information, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>

<span data-ttu-id="e409c-108">Controleer voordat u begint of Power shell op het systeem bestaat.</span><span class="sxs-lookup"><span data-stu-id="e409c-108">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="e409c-109">Raadpleeg de volgende koppelingen voor moderne werk belastingen op Windows, macOS en Linux:</span><span class="sxs-lookup"><span data-stu-id="e409c-109">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="e409c-110">[Power shell Core installeren in Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="e409c-110">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="e409c-111">[Power shell core in macOS installeren][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="e409c-111">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="e409c-112">[Power shell Core installeren in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="e409c-112">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="e409c-113">Zie [Windows Power Shell installeren][install-winps]voor traditionele workloads van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e409c-113">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="e409c-114">Bewerken met VSCode</span><span class="sxs-lookup"><span data-stu-id="e409c-114">Editing with VSCode</span></span>

1. <span data-ttu-id="e409c-115">Installeer VSCode.</span><span class="sxs-lookup"><span data-stu-id="e409c-115">Install VSCode.</span></span> <span data-ttu-id="e409c-116">Zie voor meer informatie het overzicht instellen [van Visual Studio code](https://code.visualstudio.com/Docs/setup/setup-overview).</span><span class="sxs-lookup"><span data-stu-id="e409c-116">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

   <span data-ttu-id="e409c-117">Er zijn installatie-instructies voor elk platform:</span><span class="sxs-lookup"><span data-stu-id="e409c-117">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="e409c-118">**Linux**: Volg de installatie-instructies op de pagina [actieve VSCode op Linux](https://code.visualstudio.com/docs/setup/linux) .</span><span class="sxs-lookup"><span data-stu-id="e409c-118">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>
   - <span data-ttu-id="e409c-119">**macOS**: Volg de installatie-instructies op de pagina [actieve VSCode op macOS](https://code.visualstudio.com/docs/setup/mac) .</span><span class="sxs-lookup"><span data-stu-id="e409c-119">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="e409c-120">Bij macOS moet u OpenSSL installeren om de Power shell-extensie correct te laten werken.</span><span class="sxs-lookup"><span data-stu-id="e409c-120">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="e409c-121">De eenvoudigste manier om dit te doen is door [homebrew](https://brew.sh/) te installeren en vervolgens `brew install openssl`uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e409c-121">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="e409c-122">VSCode kan nu de Power shell-uitbrei ding laden.</span><span class="sxs-lookup"><span data-stu-id="e409c-122">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="e409c-123">**Windows**: Volg de installatie-instructies op de pagina [actieve VSCode op Windows](https://code.visualstudio.com/docs/setup/windows) .</span><span class="sxs-lookup"><span data-stu-id="e409c-123">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>

1. <span data-ttu-id="e409c-124">Installeer de Power shell-extensie.</span><span class="sxs-lookup"><span data-stu-id="e409c-124">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="e409c-125">Start de VSCode-app op:</span><span class="sxs-lookup"><span data-stu-id="e409c-125">Launch the VSCode app by:</span></span>
      - <span data-ttu-id="e409c-126">**Windows**: `code` in uw Power shell-sessie typen</span><span class="sxs-lookup"><span data-stu-id="e409c-126">**Windows**: typing `code` in your PowerShell session</span></span>
      - <span data-ttu-id="e409c-127">**Linux**: `code` in uw terminal typen</span><span class="sxs-lookup"><span data-stu-id="e409c-127">**Linux**: typing `code` in your terminal</span></span>
      - <span data-ttu-id="e409c-128">**macOS**: `code` in uw terminal typen</span><span class="sxs-lookup"><span data-stu-id="e409c-128">**macOS**: typing `code` in your terminal</span></span>
   1. <span data-ttu-id="e409c-129">Start **snel openen** in Windows of Linux door op <kbd>CTRL</kbd>+<kbd>P</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="e409c-129">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="e409c-130">Druk in macOS op <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e409c-130">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="e409c-131">Typ `ext install powershell` in snel openen en druk op **Enter**.</span><span class="sxs-lookup"><span data-stu-id="e409c-131">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="e409c-132">De weer gave **extensies** wordt weer gegeven op de balk aan de zijkant.</span><span class="sxs-lookup"><span data-stu-id="e409c-132">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="e409c-133">Selecteer de Power shell-extensie van micro soft.</span><span class="sxs-lookup"><span data-stu-id="e409c-133">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="e409c-134">Er wordt een VSCode-scherm weer gegeven dat vergelijkbaar is met de volgende afbeelding:</span><span class="sxs-lookup"><span data-stu-id="e409c-134">You should see a VSCode screen similar to the following image:</span></span>

      ![VSCode](../../images/using-vscode/vscode.png)

   1. <span data-ttu-id="e409c-136">Klik op de knop **installeren** in de Power shell-extensie van micro soft.</span><span class="sxs-lookup"><span data-stu-id="e409c-136">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="e409c-137">Na de installatie ziet u de knop **installeren** om opnieuw te **laden**.</span><span class="sxs-lookup"><span data-stu-id="e409c-137">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="e409c-138">Klik op **opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="e409c-138">Click on **Reload**.</span></span>
   1. <span data-ttu-id="e409c-139">Nadat VSCode opnieuw is geladen, bent u klaar om te bewerken.</span><span class="sxs-lookup"><span data-stu-id="e409c-139">After VSCode has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="e409c-140">Als u bijvoorbeeld een nieuw bestand wilt maken, klikt u op **bestand > nieuw**.</span><span class="sxs-lookup"><span data-stu-id="e409c-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="e409c-141">Als u deze wilt opslaan, klikt u op **bestand > opslaan** en geeft u een bestands naam op, zoals `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="e409c-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="e409c-142">Als u het bestand wilt sluiten, klikt u op de `X` naast de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="e409c-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="e409c-143">**Bestand >** afsluiten om VSCode af te sluiten.</span><span class="sxs-lookup"><span data-stu-id="e409c-143">To exit VSCode, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="e409c-144">De Power shell-uitbrei ding installeren op beperkte systemen</span><span class="sxs-lookup"><span data-stu-id="e409c-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="e409c-145">Sommige systemen zijn zodanig ingesteld dat alle code handtekeningen moeten worden gecontroleerd en hiervoor moeten de services van Power shell-editor hand matig worden goedgekeurd om te worden uitgevoerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="e409c-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="e409c-146">Een groepsbeleid update die het uitvoerings beleid wijzigt, is waarschijnlijk een mogelijke oorzaak als u de Power shell-uitbrei ding hebt geïnstalleerd, maar er wordt een fout bericht ontvangen zoals:</span><span class="sxs-lookup"><span data-stu-id="e409c-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="e409c-147">Open een Power shell-prompt en voer de volgende opdracht uit om Power shell editor-Services en de Power shell-uitbrei ding voor VSCode hand matig goed te keuren:</span><span class="sxs-lookup"><span data-stu-id="e409c-147">To manually approve PowerShell Editor Services and the PowerShell extension for VSCode, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="e409c-148">U wordt gevraagd of **u software van deze niet-vertrouwde uitgever wilt uitvoeren?**</span><span class="sxs-lookup"><span data-stu-id="e409c-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="e409c-149">Typ `A` om het bestand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e409c-149">Type `A` to run the file.</span></span> <span data-ttu-id="e409c-150">Open vervolgens VSCode en controleer of de Power shell-extensie goed werkt.</span><span class="sxs-lookup"><span data-stu-id="e409c-150">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="e409c-151">Als u nog steeds problemen ondervindt, laat het ons dan weten op [github](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="e409c-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="e409c-152">Een versie van Power shell kiezen die moet worden gebruikt met de extensie</span><span class="sxs-lookup"><span data-stu-id="e409c-152">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="e409c-153">Met Power shell core die naast Windows Power shell wordt geïnstalleerd, is het nu mogelijk om een bepaalde versie van Power shell te gebruiken met de Power shell-extensie.</span><span class="sxs-lookup"><span data-stu-id="e409c-153">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="e409c-154">Gebruik de volgende stappen om de versie te kiezen:</span><span class="sxs-lookup"><span data-stu-id="e409c-154">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="e409c-155">Open het **opdracht palet** in Windows of Linux met <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e409c-155">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="e409c-156">In macOS, gebruikt u <kbd>Cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e409c-156">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="e409c-157">Zoek naar de **sessie**.</span><span class="sxs-lookup"><span data-stu-id="e409c-157">Search for **Session**.</span></span>
1. <span data-ttu-id="e409c-158">Klik op **Power shell: menu sessie weer geven**.</span><span class="sxs-lookup"><span data-stu-id="e409c-158">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="e409c-159">Kies de versie van Power shell die u wilt gebruiken in de lijst, bijvoorbeeld: **Power shell core**.</span><span class="sxs-lookup"><span data-stu-id="e409c-159">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e409c-160">Deze functie bekijkt enkele bekende paden op verschillende besturings systemen om installatie locaties van Power shell te detecteren.</span><span class="sxs-lookup"><span data-stu-id="e409c-160">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="e409c-161">Als u Power shell hebt geïnstalleerd op een niet-typische locatie, wordt deze mogelijk niet eerst weer gegeven in het menu sessie.</span><span class="sxs-lookup"><span data-stu-id="e409c-161">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="e409c-162">U kunt het menu sessie uitbreiden door [uw eigen aangepaste paden toe te voegen](#adding-your-own-powershell-paths-to-the-session-menu) , zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="e409c-162">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="e409c-163">Er is een andere manier om naar het menu sessie te gaan.</span><span class="sxs-lookup"><span data-stu-id="e409c-163">There's another way to get to the session menu.</span></span> <span data-ttu-id="e409c-164">Wanneer een Power shell-bestand is geopend in uw editor, ziet u een groen versie nummer in de rechter benedenhoek.</span><span class="sxs-lookup"><span data-stu-id="e409c-164">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="e409c-165">Als u op dit versie nummer klikt, gaat u naar het menu sessie.</span><span class="sxs-lookup"><span data-stu-id="e409c-165">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="e409c-166">Uw eigen Power shell-paden toevoegen aan het menu sessie</span><span class="sxs-lookup"><span data-stu-id="e409c-166">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="e409c-167">U kunt andere uitvoer bare Power shell-paden toevoegen aan het menu sessie via een VSCode-instelling.</span><span class="sxs-lookup"><span data-stu-id="e409c-167">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="e409c-168">Voeg een item toe aan de lijst `powershell.powerShellAdditionalExePaths` of maak een lijst als deze niet bestaat in uw `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="e409c-168">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="e409c-169">Elk item moet het volgende bevatten:</span><span class="sxs-lookup"><span data-stu-id="e409c-169">Each item must have:</span></span>

* <span data-ttu-id="e409c-170">`exePath`: het pad naar de `pwsh` of `powershell` uitvoer bare bestand.</span><span class="sxs-lookup"><span data-stu-id="e409c-170">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="e409c-171">`versionName`: de tekst die wordt weer gegeven in het menu van de sessie.</span><span class="sxs-lookup"><span data-stu-id="e409c-171">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="e409c-172">U kunt de standaard-Power shell-versie instellen op het gebruik van de `powershell.powerShellDefaultVersion` instelling door dit in te stellen op de tekst die wordt weer gegeven in het menu sessie (ook wel bekend als de `versionName` in de laatste instelling):</span><span class="sxs-lookup"><span data-stu-id="e409c-172">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="e409c-173">Nadat u deze instelling hebt geconfigureerd, start u VSCode opnieuw of laadt u het huidige VSCode-venster opnieuw vanuit het **opdracht palet**, typt u **ontwikkelaar: venster opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="e409c-173">After you've configured this setting, restart VSCode or to reload the current VSCode window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="e409c-174">Als u het menu sessie opent, ziet u nu uw extra Power shell-versies!</span><span class="sxs-lookup"><span data-stu-id="e409c-174">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="e409c-175">Als u Power shell bouwt vanaf een bron, is dit een fantastische manier om uw lokale build van Power shell te testen.</span><span class="sxs-lookup"><span data-stu-id="e409c-175">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="e409c-176">Configuratie-instellingen voor VSCode</span><span class="sxs-lookup"><span data-stu-id="e409c-176">Configuration settings for VSCode</span></span>

<span data-ttu-id="e409c-177">U kunt met behulp van de stappen in de vorige alinea configuratie-instellingen toevoegen in `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="e409c-177">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="e409c-178">We raden de volgende configuratie-instellingen aan voor VSCode:</span><span class="sxs-lookup"><span data-stu-id="e409c-178">We recommend the following configuration settings for VSCode:</span></span>

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

<span data-ttu-id="e409c-179">Als u niet wilt dat deze instellingen van invloed zijn op alle bestands typen, kunt u met VSCode ook configuraties per taal configureren.</span><span class="sxs-lookup"><span data-stu-id="e409c-179">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="e409c-180">Maak een taalspecifieke instelling door instellingen in een `[<language-name>]` veld in te voeren.</span><span class="sxs-lookup"><span data-stu-id="e409c-180">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="e409c-181">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e409c-181">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="e409c-182">Zie [Wat is bestands codering](understanding-file-encoding.md)? voor meer informatie over bestands codering in VSCode.</span><span class="sxs-lookup"><span data-stu-id="e409c-182">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="e409c-183">Fout opsporing met VSCode</span><span class="sxs-lookup"><span data-stu-id="e409c-183">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="e409c-184">Geen-werk ruimte: fout opsporing</span><span class="sxs-lookup"><span data-stu-id="e409c-184">No-workspace debugging</span></span>

<span data-ttu-id="e409c-185">Vanaf VSCode-versie 1,9 kunt u fouten opsporen in Power shell-scripts zonder de map met het Power shell-script te openen.</span><span class="sxs-lookup"><span data-stu-id="e409c-185">As of VSCode version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="e409c-186">Open het Power shell-script bestand met het **bestand > bestand openen...** , stel een onderbrekings punt in op een regel, druk op <kbd>F9</kbd>en druk vervolgens op <kbd>F5</kbd> om de fout opsporing te starten.</span><span class="sxs-lookup"><span data-stu-id="e409c-186">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="e409c-187">Het deel venster acties voor fout opsporing wordt weer gegeven, waarin u de fout opsporing kunt opdelen, stap, CV en stoppen.</span><span class="sxs-lookup"><span data-stu-id="e409c-187">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="e409c-188">Fout opsporing voor werk ruimten</span><span class="sxs-lookup"><span data-stu-id="e409c-188">Workspace debugging</span></span>

<span data-ttu-id="e409c-189">Fout opsporing voor werk ruimten verwijst naar fout opsporing in de context van een map die u hebt geopend in Visual Studio code vanuit het menu **bestand** met **open map...** . De map die u opent, is doorgaans uw Power shell-projectmap en/of de hoofdmap van uw Git-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e409c-189">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="e409c-190">Zelfs in deze modus kunt u de fout opsporing van het momenteel geselecteerde Power shell-script starten door op <kbd>F5</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="e409c-190">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="e409c-191">Met fout opsporing in werk ruimten kunt u echter meerdere debug-configuraties definiëren, anders dan alleen fouten opsporen in het bestand dat momenteel is geopend.</span><span class="sxs-lookup"><span data-stu-id="e409c-191">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="e409c-192">U kunt bijvoorbeeld een configuratie toevoegen aan:</span><span class="sxs-lookup"><span data-stu-id="e409c-192">For instance, you can add a configuration to:</span></span>

- <span data-ttu-id="e409c-193">Start de tests van parasieten in het fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="e409c-193">Launch Pester tests in the debugger.</span></span>
- <span data-ttu-id="e409c-194">Start een specifiek bestand met argumenten in het fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="e409c-194">Launch a specific file with arguments in the debugger.</span></span>
- <span data-ttu-id="e409c-195">Start een interactieve sessie in het fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="e409c-195">Launch an interactive session in the debugger.</span></span>
- <span data-ttu-id="e409c-196">Koppel het fout opsporingsprogramma aan een Power shell-hostproces.</span><span class="sxs-lookup"><span data-stu-id="e409c-196">Attach the debugger to a PowerShell host process.</span></span>

<span data-ttu-id="e409c-197">Voer de volgende stappen uit om het configuratie bestand voor fout opsporing te maken:</span><span class="sxs-lookup"><span data-stu-id="e409c-197">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="e409c-198">Open de weer gave **fout opsporing** op Windows of Linux door op <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="e409c-198">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="e409c-199">Druk in macOS op <kbd>Cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e409c-199">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="e409c-200">Klik op het pictogram vistuig **configureren** op de werk balk.</span><span class="sxs-lookup"><span data-stu-id="e409c-200">Click the **Configure** gear icon in the toolbar.</span></span>
  1. <span data-ttu-id="e409c-201">U wordt door VSCode gevraagd om **omgeving te selecteren**.</span><span class="sxs-lookup"><span data-stu-id="e409c-201">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="e409c-202">Kies **Power shell**.</span><span class="sxs-lookup"><span data-stu-id="e409c-202">Choose **PowerShell**.</span></span>

<span data-ttu-id="e409c-203">Het resultaat is dat VSCode een map en een bestand `.vscode\launch.json` maakt in de hoofdmap van de map met de werk ruimte.</span><span class="sxs-lookup"><span data-stu-id="e409c-203">The result is that VSCode creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="e409c-204">Deze locatie is waar de configuratie van de fout opsporing wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e409c-204">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="e409c-205">Als uw bestanden zich in een Git-opslag plaats bevinden, wilt u meestal het `launch.json` bestand door voeren.</span><span class="sxs-lookup"><span data-stu-id="e409c-205">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="e409c-206">De inhoud van het `launch.json` bestand zijn:</span><span class="sxs-lookup"><span data-stu-id="e409c-206">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="e409c-207">Dit bestand vertegenwoordigt de veelvoorkomende scenario's voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e409c-207">This file represents the common debug scenarios.</span></span> <span data-ttu-id="e409c-208">Wanneer u dit bestand in de editor opent, ziet u een knop **Configuratie toevoegen...** .</span><span class="sxs-lookup"><span data-stu-id="e409c-208">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="e409c-209">U kunt op deze knop klikken om meer configuratie van Power Shell-fout opsporing toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="e409c-209">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="e409c-210">Een van de handig te toevoegen configuratie is **Power shell: script starten**.</span><span class="sxs-lookup"><span data-stu-id="e409c-210">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="e409c-211">Met deze configuratie kunt u een bestand opgeven met optionele argumenten die moeten worden gestart wanneer u op <kbd>F5</kbd> drukt, ongeacht welk bestand momenteel actief is in de editor.</span><span class="sxs-lookup"><span data-stu-id="e409c-211">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="e409c-212">Nadat de configuratie van de fout opsporing is ingesteld, kunt u selecteren welke configuratie u tijdens een foutopsporingssessie wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e409c-212">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="e409c-213">Selecteer een configuratie in de vervolg keuzelijst debug Configuration in de werk balk van de weer gave van de **fout opsporing** .</span><span class="sxs-lookup"><span data-stu-id="e409c-213">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="e409c-214">Er zijn enkele blogs die handig kunnen zijn om aan de slag te gaan met Power shell-extensie voor Visual Studio code:</span><span class="sxs-lookup"><span data-stu-id="e409c-214">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="e409c-215">[Power shell-uitbrei ding][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="e409c-215">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="e409c-216">[Power shell-scripts schrijven en fouten opsporen in Visual Studio code][debug]</span><span class="sxs-lookup"><span data-stu-id="e409c-216">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="e409c-217">[Fout opsporing van Visual Studio code guidance][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="e409c-217">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="e409c-218">[Fout opsporing in Power shell in Visual Studio code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="e409c-218">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="e409c-219">[Aan de slag met Power shell-ontwikkeling in Visual Studio code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="e409c-219">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="e409c-220">[Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="e409c-220">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="e409c-221">[Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="e409c-221">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="e409c-222">[Fout opsporing voor Power shell-script in Visual Studio code – deel 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="e409c-222">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="e409c-223">[Fout opsporing voor Power shell-script in Visual Studio code – deel 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="e409c-223">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="e409c-224">Power shell-uitbrei ding voor VSCode</span><span class="sxs-lookup"><span data-stu-id="e409c-224">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="e409c-225">De bron code van de Power shell-extensie vindt u op [github](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="e409c-225">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
