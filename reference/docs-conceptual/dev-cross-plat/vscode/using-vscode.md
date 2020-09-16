---
title: Visual Studio code for Power Shell Development gebruiken
description: Visual Studio code for Power Shell Development gebruiken
ms.date: 11/07/2019
ms.openlocfilehash: 181746e7d3df2880223d1f15a0c8b99b324f5b98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782528"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="bd9af-103">Visual Studio code for Power Shell Development gebruiken</span><span class="sxs-lookup"><span data-stu-id="bd9af-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="bd9af-104">[Visual Studio code][vscode] is een platformoverschrijdende script editor van micro soft.</span><span class="sxs-lookup"><span data-stu-id="bd9af-104">[Visual Studio Code][vscode] is a cross-platform script editor by Microsoft.</span></span> <span data-ttu-id="bd9af-105">Samen met de [Power shell-uitbrei ding][psext]beschikt u over een uitgebreide en interactieve script bewerkings ervaring, waardoor het eenvoudiger is om betrouw bare Power shell-scripts te schrijven.</span><span class="sxs-lookup"><span data-stu-id="bd9af-105">Together with the [PowerShell extension][psext], it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span> <span data-ttu-id="bd9af-106">Visual Studio code met de Power shell-extensie is de aanbevolen editor voor het schrijven van Power shell-scripts.</span><span class="sxs-lookup"><span data-stu-id="bd9af-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>

<span data-ttu-id="bd9af-107">Het ondersteunt de volgende Power shell-versies:</span><span class="sxs-lookup"><span data-stu-id="bd9af-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="bd9af-108">Power shell 7 en up (Windows, macOS en Linux)</span><span class="sxs-lookup"><span data-stu-id="bd9af-108">PowerShell 7 and up (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="bd9af-109">Power shell Core 6 (Windows, macOS en Linux)</span><span class="sxs-lookup"><span data-stu-id="bd9af-109">PowerShell Core 6 (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="bd9af-110">Windows Power shell 5,1 (alleen Windows)</span><span class="sxs-lookup"><span data-stu-id="bd9af-110">Windows PowerShell 5.1 (Windows-only)</span></span>

> [!NOTE]
> <span data-ttu-id="bd9af-111">Visual Studio code is niet hetzelfde als [Visual Studio][].</span><span class="sxs-lookup"><span data-stu-id="bd9af-111">Visual Studio Code is not the same as [Visual Studio][].</span></span>

## <a name="getting-started"></a><span data-ttu-id="bd9af-112">Aan de slag</span><span class="sxs-lookup"><span data-stu-id="bd9af-112">Getting started</span></span>

<span data-ttu-id="bd9af-113">Controleer voordat u begint of Power shell op het systeem bestaat.</span><span class="sxs-lookup"><span data-stu-id="bd9af-113">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="bd9af-114">Raadpleeg de volgende koppelingen voor moderne werk belastingen op Windows, macOS en Linux:</span><span class="sxs-lookup"><span data-stu-id="bd9af-114">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="bd9af-115">[PowerShell installeren in Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="bd9af-115">[Installing PowerShell on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="bd9af-116">[PowerShell installeren in macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="bd9af-116">[Installing PowerShell on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="bd9af-117">[PowerShell installeren in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="bd9af-117">[Installing PowerShell on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="bd9af-118">Zie [Windows Power Shell installeren][install-winps]voor traditionele workloads van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="bd9af-118">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd9af-119">De [Windows PowerShell ISE][ise] is nog steeds beschikbaar voor Windows.</span><span class="sxs-lookup"><span data-stu-id="bd9af-119">The [Windows PowerShell ISE][ise] is still available for Windows.</span></span> <span data-ttu-id="bd9af-120">Het is echter niet langer in de ontwikkeling van actieve functies.</span><span class="sxs-lookup"><span data-stu-id="bd9af-120">However, it is no longer in active feature development.</span></span> <span data-ttu-id="bd9af-121">De ISE werkt niet met Power shell 6 en hoger.</span><span class="sxs-lookup"><span data-stu-id="bd9af-121">The ISE does not work with PowerShell 6 and higher.</span></span> <span data-ttu-id="bd9af-122">Als onderdeel van Windows blijft het officieel worden ondersteund voor oplossingen voor beveiliging en onderhoud met hoge prioriteit.</span><span class="sxs-lookup"><span data-stu-id="bd9af-122">As a component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="bd9af-123">Er zijn geen plannen om de ISE van Windows te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="bd9af-123">We have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="bd9af-124">Bewerken met Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="bd9af-124">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="bd9af-125">Installeer Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="bd9af-125">Install Visual Studio Code.</span></span> <span data-ttu-id="bd9af-126">Zie voor meer informatie het overzicht instellen [van Visual Studio code][vsc-setup].</span><span class="sxs-lookup"><span data-stu-id="bd9af-126">For more information, see the overview [Setting up Visual Studio Code][vsc-setup].</span></span>

   <span data-ttu-id="bd9af-127">Er zijn installatie-instructies voor elk platform:</span><span class="sxs-lookup"><span data-stu-id="bd9af-127">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="bd9af-128">**Windows**: Volg de installatie-instructies op de pagina [Visual Studio code uitvoeren op Windows][vsc-setup-win] .</span><span class="sxs-lookup"><span data-stu-id="bd9af-128">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows][vsc-setup-win] page.</span></span>
   - <span data-ttu-id="bd9af-129">**macOS**: Volg de installatie-instructies op de pagina [Visual Studio code uitvoeren op MacOS][vsc-setup-macOS] .</span><span class="sxs-lookup"><span data-stu-id="bd9af-129">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS][vsc-setup-macOS] page.</span></span>
   - <span data-ttu-id="bd9af-130">**Linux**: Volg de installatie-instructies op de pagina [Visual Studio code uitvoeren op Linux][vsc-setup-linux] .</span><span class="sxs-lookup"><span data-stu-id="bd9af-130">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux][vsc-setup-linux] page.</span></span>

1. <span data-ttu-id="bd9af-131">Installeer de Power shell-extensie.</span><span class="sxs-lookup"><span data-stu-id="bd9af-131">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="bd9af-132">Start de app Visual Studio code door te typen `code` in een-console of `code-insiders` Als u Visual Studio code insiders hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="bd9af-132">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="bd9af-133">Start **snel openen** in Windows of Linux door op <kbd>CTRL</kbd> + <kbd>P</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="bd9af-133">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="bd9af-134">Druk op macOS op <kbd>cmd</kbd> + <kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd9af-134">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="bd9af-135">Typ in snel openen `ext install powershell` en druk op **Enter**.</span><span class="sxs-lookup"><span data-stu-id="bd9af-135">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="bd9af-136">De weer gave **extensies** wordt weer gegeven op de balk aan de zijkant.</span><span class="sxs-lookup"><span data-stu-id="bd9af-136">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="bd9af-137">Selecteer de Power shell-extensie van micro soft.</span><span class="sxs-lookup"><span data-stu-id="bd9af-137">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="bd9af-138">Er wordt een Visual Studio-code scherm weer gegeven dat vergelijkbaar is met de volgende afbeelding:</span><span class="sxs-lookup"><span data-stu-id="bd9af-138">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio code: weer gave van de Power shell-uitbrei ding](media/using-vscode/vscode.png)

   1. <span data-ttu-id="bd9af-140">Klik op de knop **installeren** in de Power shell-extensie van micro soft.</span><span class="sxs-lookup"><span data-stu-id="bd9af-140">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="bd9af-141">Als u na de installatie de knop **installeren** ziet, klikt u **op opnieuw** **laden**.</span><span class="sxs-lookup"><span data-stu-id="bd9af-141">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="bd9af-142">Nadat Visual Studio code opnieuw is geladen, bent u klaar om te bewerken.</span><span class="sxs-lookup"><span data-stu-id="bd9af-142">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="bd9af-143">Als u bijvoorbeeld een nieuw bestand wilt maken, klikt u op **bestand > nieuw**.</span><span class="sxs-lookup"><span data-stu-id="bd9af-143">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="bd9af-144">Als u deze wilt opslaan, klikt u op **bestand > opslaan** en geeft u een bestands naam op, zoals `HelloWorld.ps1` .</span><span class="sxs-lookup"><span data-stu-id="bd9af-144">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="bd9af-145">Als u het bestand wilt sluiten, klikt u op het `X` volgende bij de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="bd9af-145">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="bd9af-146">Als u Visual Studio code wilt afsluiten, wordt het **bestand > sluiten**.</span><span class="sxs-lookup"><span data-stu-id="bd9af-146">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="bd9af-147">De Power shell-uitbrei ding installeren op beperkte systemen</span><span class="sxs-lookup"><span data-stu-id="bd9af-147">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="bd9af-148">Sommige systemen zijn ingesteld om validatie van alle code handtekeningen te vereisen.</span><span class="sxs-lookup"><span data-stu-id="bd9af-148">Some systems are set up to require validation of all code signatures.</span></span> <span data-ttu-id="bd9af-149">De volgende fout kan optreden:</span><span class="sxs-lookup"><span data-stu-id="bd9af-149">You may receive the following error:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="bd9af-150">Dit probleem kan optreden wanneer het uitvoerings beleid van Power shell is ingesteld door Windows groepsbeleid.</span><span class="sxs-lookup"><span data-stu-id="bd9af-150">This problem can occur when PowerShell's execution policy is set by Windows Group Policy.</span></span> <span data-ttu-id="bd9af-151">Open een Power shell-prompt en voer de volgende opdracht uit om de Power shell editor-Services en de Power shell-extensie voor Visual Studio code hand matig goed te keuren:</span><span class="sxs-lookup"><span data-stu-id="bd9af-151">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="bd9af-152">U wordt gevraagd of **u software van deze niet-vertrouwde uitgever wilt uitvoeren?**</span><span class="sxs-lookup"><span data-stu-id="bd9af-152">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="bd9af-153">Typ `A` om het bestand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="bd9af-153">Type `A` to run the file.</span></span> <span data-ttu-id="bd9af-154">Open vervolgens Visual Studio code en controleer of de Power shell-extensie goed werkt.</span><span class="sxs-lookup"><span data-stu-id="bd9af-154">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="bd9af-155">Als u nog steeds problemen ondervindt, laat het ons dan weten over [github-problemen][].</span><span class="sxs-lookup"><span data-stu-id="bd9af-155">If you still have problems getting started, let us know on [GitHub issues][].</span></span>

> [!NOTE]
> <span data-ttu-id="bd9af-156">De Power shell-extensie voor Visual Studio code biedt geen ondersteuning voor uitvoering in een modus met beperkte taal.</span><span class="sxs-lookup"><span data-stu-id="bd9af-156">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="bd9af-157">Zie [github issue #606][i606]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd9af-157">For more information, see [GitHub issue #606][i606].</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="bd9af-158">Een versie van Power shell kiezen die moet worden gebruikt met de extensie</span><span class="sxs-lookup"><span data-stu-id="bd9af-158">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="bd9af-159">Met Power shell core die naast Windows Power shell wordt geïnstalleerd, is het nu mogelijk om een specifieke versie van Power shell te gebruiken met de Power shell-extensie.</span><span class="sxs-lookup"><span data-stu-id="bd9af-159">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a specific version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="bd9af-160">Deze functie bekijkt enkele bekende paden op verschillende besturings systemen voor het detecteren van installaties van Power shell.</span><span class="sxs-lookup"><span data-stu-id="bd9af-160">This feature looks at a few well-known paths on different operating systems to discover installations of PowerShell.</span></span>

<span data-ttu-id="bd9af-161">Gebruik de volgende stappen om de versie te kiezen:</span><span class="sxs-lookup"><span data-stu-id="bd9af-161">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="bd9af-162">Open het **opdracht palet** in Windows of Linux met <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd9af-162">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="bd9af-163">Gebruik <kbd>cmd</kbd> + <kbd>SHIFT</kbd> + <kbd>P</kbd>in macOS.</span><span class="sxs-lookup"><span data-stu-id="bd9af-163">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="bd9af-164">Zoek naar de **sessie**.</span><span class="sxs-lookup"><span data-stu-id="bd9af-164">Search for **Session**.</span></span>
1. <span data-ttu-id="bd9af-165">Klik op **Power shell: menu sessie weer geven**.</span><span class="sxs-lookup"><span data-stu-id="bd9af-165">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="bd9af-166">Kies de versie van Power shell die u wilt gebruiken in de lijst, bijvoorbeeld: **Power shell core**.</span><span class="sxs-lookup"><span data-stu-id="bd9af-166">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

<span data-ttu-id="bd9af-167">Als u Power shell hebt geïnstalleerd op een niet-typische locatie, wordt deze mogelijk niet eerst weer gegeven in het menu sessie.</span><span class="sxs-lookup"><span data-stu-id="bd9af-167">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="bd9af-168">U kunt het menu sessie uitbreiden door [uw eigen aangepaste paden toe te voegen](#adding-your-own-powershell-paths-to-the-session-menu) , zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="bd9af-168">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

> [!NOTE]
> <span data-ttu-id="bd9af-169">Het menu Power shell-sessie kan ook worden geopend vanuit het groene versie nummer in de rechter benedenhoek van de status balk.</span><span class="sxs-lookup"><span data-stu-id="bd9af-169">The PowerShell session menu can also be accessed from the green version number in the bottom right corner of status bar.</span></span> <span data-ttu-id="bd9af-170">Als u op dit versie nummer klikt, wordt het menu sessie geopend.</span><span class="sxs-lookup"><span data-stu-id="bd9af-170">Clicking this version number opens the session menu.</span></span>

## <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="bd9af-171">Configuratie-instellingen voor Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="bd9af-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="bd9af-172">Als u niet bekend bent met het wijzigen van instellingen in Visual Studio code, raden we u aan [de documentatie van de Visual Studio code-instellingen][vsc-settings] te lezen.</span><span class="sxs-lookup"><span data-stu-id="bd9af-172">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend reading [Visual Studio Code's settings][vsc-settings] documentation.</span></span>

<span data-ttu-id="bd9af-173">Na het lezen van de documentatie kunt u configuratie-instellingen toevoegen in `settings.json` .</span><span class="sxs-lookup"><span data-stu-id="bd9af-173">After reading the documentation, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="bd9af-174">Als u niet wilt dat deze instellingen van invloed zijn op alle bestands typen, kunt u met Visual Studio code ook configuraties per taal instellen.</span><span class="sxs-lookup"><span data-stu-id="bd9af-174">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="bd9af-175">Maak een taalspecifieke instelling door instellingen in een veld in te voeren `[<language-name>]` .</span><span class="sxs-lookup"><span data-stu-id="bd9af-175">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="bd9af-176">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bd9af-176">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="bd9af-177">Zie [informatie over bestands codering][file-encoding]voor meer informatie over het coderen van bestanden in Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="bd9af-177">For more information about file encoding in Visual Studio Code, see [Understanding file encoding][file-encoding].</span></span>
>
> <span data-ttu-id="bd9af-178">Lees ook [hoe u de ISE-ervaring in Visual Studio code repliceert][vsc-ise] voor andere tips over het configureren van Visual Studio code voor het bewerken van Power shell.</span><span class="sxs-lookup"><span data-stu-id="bd9af-178">Also, check out [How to replicate the ISE experience in Visual Studio Code][vsc-ise] for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="bd9af-179">Uw eigen Power shell-paden toevoegen aan het menu sessie</span><span class="sxs-lookup"><span data-stu-id="bd9af-179">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="bd9af-180">U kunt andere uitvoer bare Power shell-paden toevoegen aan het menu sessie met behulp van de [Visual Studio code-instelling](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths` .</span><span class="sxs-lookup"><span data-stu-id="bd9af-180">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="bd9af-181">Voeg een item toe aan de lijst `powershell.powerShellAdditionalExePaths` of maak een lijst als deze niet bestaat in uw `settings.json` :</span><span class="sxs-lookup"><span data-stu-id="bd9af-181">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="bd9af-182">Elk item moet het volgende bevatten:</span><span class="sxs-lookup"><span data-stu-id="bd9af-182">Each item must have:</span></span>

- <span data-ttu-id="bd9af-183">`exePath`: Het pad naar het `pwsh` of het `powershell` uitvoer bare bestand.</span><span class="sxs-lookup"><span data-stu-id="bd9af-183">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="bd9af-184">`versionName`: De tekst die wordt weer gegeven in het menu van de sessie.</span><span class="sxs-lookup"><span data-stu-id="bd9af-184">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="bd9af-185">Als u de standaard-Power shell-versie wilt instellen, stelt u de waarde `powershell.powerShellDefaultVersion` in op de tekst die wordt weer gegeven in het menu sessie (ook wel bekend als de `versionName` ):</span><span class="sxs-lookup"><span data-stu-id="bd9af-185">To set the default PowerShell version, set the value `powershell.powerShellDefaultVersion` to the text displayed in the session menu (also known as the `versionName`):</span></span>

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

<span data-ttu-id="bd9af-186">Nadat u deze instelling hebt geconfigureerd, start u Visual Studio code opnieuw of laadt u het huidige venster Visual Studio-code opnieuw vanuit het **opdracht palet**, typt u **ontwikkelaar: venster opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="bd9af-186">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="bd9af-187">Als u het menu sessie opent, ziet u nu uw extra Power shell-versies!</span><span class="sxs-lookup"><span data-stu-id="bd9af-187">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="bd9af-188">Als u Power shell bouwt vanaf een bron, is dit een fantastische manier om uw lokale build van Power shell te testen.</span><span class="sxs-lookup"><span data-stu-id="bd9af-188">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="bd9af-189">Een oudere versie van de Power shell-uitbrei ding voor Windows Power Shell v3 en v4 gebruiken</span><span class="sxs-lookup"><span data-stu-id="bd9af-189">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="bd9af-190">De huidige Power shell-extensie biedt geen ondersteuning voor [Power Shell v3 en v4][i1310].</span><span class="sxs-lookup"><span data-stu-id="bd9af-190">The current PowerShell extension doesn't support [PowerShell v3 and v4][i1310].</span></span> <span data-ttu-id="bd9af-191">U kunt echter de laatste versie van de uitbrei ding gebruiken die Power Shell v3 en v4 ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="bd9af-191">However, you can use the last version of the extension that supports PowerShell v3 and v4.</span></span>

> [!CAUTION]
> <span data-ttu-id="bd9af-192">Er zijn geen aanvullende oplossingen voor deze oudere versie van de uitbrei ding.</span><span class="sxs-lookup"><span data-stu-id="bd9af-192">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="bd9af-193">Het wordt weer gegeven als IS, maar is beschikbaar voor u als u nog steeds Windows Power Shell v3 en Windows Power shell v4 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bd9af-193">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="bd9af-194">Open eerst het deel venster uitbrei ding en zoek naar `PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="bd9af-194">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="bd9af-195">Klik vervolgens op het vistuig en selecteer **een andere versie installeren...**.</span><span class="sxs-lookup"><span data-stu-id="bd9af-195">Then click the gear and select **Install another version...**.</span></span>

![Menu-item-Installeer een andere versie...](media/using-vscode/install-another-version.png)

<span data-ttu-id="bd9af-197">Selecteer vervolgens de **2020.1.0** -versie.</span><span class="sxs-lookup"><span data-stu-id="bd9af-197">Then select the **2020.1.0** version.</span></span> <span data-ttu-id="bd9af-198">Deze versie van de uitbrei ding is de laatste versie voor de ondersteuning van v3 en v4.</span><span class="sxs-lookup"><span data-stu-id="bd9af-198">This version of the extension was the last version to support v3 and v4.</span></span> <span data-ttu-id="bd9af-199">Zorg ervoor dat u de volgende instelling toevoegt zodat uw extensie versie niet automatisch wordt bijgewerkt:</span><span class="sxs-lookup"><span data-stu-id="bd9af-199">Be sure to add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="bd9af-200">Versie **2020.1.0** werkt voor de nabije toekomst.</span><span class="sxs-lookup"><span data-stu-id="bd9af-200">Version **2020.1.0** will work for the foreseeable future.</span></span> <span data-ttu-id="bd9af-201">Visual Studio code kan echter een wijziging implementeren die deze versie van de uitbrei ding verbreekt.</span><span class="sxs-lookup"><span data-stu-id="bd9af-201">However, Visual Studio Code could implement a change that breaks this version of the extension.</span></span> <span data-ttu-id="bd9af-202">Daarom wordt u aangeraden het volgende te doen en geen ondersteuning te bieden:</span><span class="sxs-lookup"><span data-stu-id="bd9af-202">Because of this, and lack of support, we recommend:</span></span>

- <span data-ttu-id="bd9af-203">Upgraden naar Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="bd9af-203">Upgrading to Windows PowerShell 5.1</span></span>
- <span data-ttu-id="bd9af-204">Power shell 7 installeren, een side-by-side installatie van Windows Power shell en werkt het beste met de Power shell-extensie</span><span class="sxs-lookup"><span data-stu-id="bd9af-204">Install PowerShell 7, which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="bd9af-205">Fout opsporing met Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="bd9af-205">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="bd9af-206">Geen-werk ruimte: fout opsporing</span><span class="sxs-lookup"><span data-stu-id="bd9af-206">No-workspace debugging</span></span>

<span data-ttu-id="bd9af-207">In Visual Studio code versie 1,9 (of hoger) kunt u fouten opsporen in Power shell-scripts zonder de map met het Power shell-script te openen.</span><span class="sxs-lookup"><span data-stu-id="bd9af-207">In Visual Studio Code version 1.9 (or higher), you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span>

1. <span data-ttu-id="bd9af-208">Open het Power shell-script bestand met het **bestand > bestand openen...**</span><span class="sxs-lookup"><span data-stu-id="bd9af-208">Open the PowerShell script file with **File > Open File...**</span></span>
1. <span data-ttu-id="bd9af-209">Een onderbrekings punt instellen: Selecteer een regel en druk vervolgens op <kbd>F9</kbd></span><span class="sxs-lookup"><span data-stu-id="bd9af-209">Set a breakpoint - select a line then press <kbd>F9</kbd></span></span>
1. <span data-ttu-id="bd9af-210">Druk op <kbd>F5</kbd> om de fout opsporing te starten</span><span class="sxs-lookup"><span data-stu-id="bd9af-210">Press <kbd>F5</kbd> to start debugging</span></span>

<span data-ttu-id="bd9af-211">Het deel venster acties voor fout opsporing wordt weer gegeven, waarin u de fout opsporing kunt opdelen, stap, CV en stoppen.</span><span class="sxs-lookup"><span data-stu-id="bd9af-211">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="bd9af-212">Fout opsporing voor werk ruimten</span><span class="sxs-lookup"><span data-stu-id="bd9af-212">Workspace debugging</span></span>

<span data-ttu-id="bd9af-213">Fout opsporing in werk ruimte verwijst naar fout opsporing in de context van een map die u hebt geopend vanuit het menu **bestand** met **open map...**. De map die u opent, is doorgaans uw Power shell-projectmap of de hoofdmap van uw Git-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="bd9af-213">Workspace debugging refers to debugging in the context of a folder that you've opened from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder or the root of your Git repository.</span></span> <span data-ttu-id="bd9af-214">Met fout opsporing voor werk ruimten kunt u meerdere debug-configuraties definiëren, anders dan alleen fouten opsporen in het bestand dat momenteel is geopend.</span><span class="sxs-lookup"><span data-stu-id="bd9af-214">Workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>

<span data-ttu-id="bd9af-215">Voer de volgende stappen uit om een configuratie bestand voor fout opsporing te maken:</span><span class="sxs-lookup"><span data-stu-id="bd9af-215">Follow these steps to create a debug configuration file:</span></span>

1. <span data-ttu-id="bd9af-216">Open de weer gave **fout opsporing** in Windows of Linux door op <kbd>CTRL</kbd> + <kbd>+ SHIFT</kbd> + <kbd>D</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="bd9af-216">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="bd9af-217">Druk op macOS op <kbd>cmd</kbd> + <kbd>SHIFT</kbd> + <kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd9af-217">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
1. <span data-ttu-id="bd9af-218">Klik op de koppeling **een launch.jsmaken op bestand** .</span><span class="sxs-lookup"><span data-stu-id="bd9af-218">Click the **create a launch.json file** link.</span></span>
1. <span data-ttu-id="bd9af-219">Kies **Power shell**in het venster **omgeving selecteren** .</span><span class="sxs-lookup"><span data-stu-id="bd9af-219">From the **Select Environment** prompt, choose **PowerShell**.</span></span>
1. <span data-ttu-id="bd9af-220">Kies het type fout opsporing dat u wilt gebruiken:</span><span class="sxs-lookup"><span data-stu-id="bd9af-220">Choose the type of debugging you'd like to use:</span></span>

   - <span data-ttu-id="bd9af-221">Het **huidige bestand starten** -starten en fouten opsporen in het bestand in het huidige venster van de editor</span><span class="sxs-lookup"><span data-stu-id="bd9af-221">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
   - <span data-ttu-id="bd9af-222">**Script starten** : starten en fouten opsporen in opgegeven bestand of opdracht</span><span class="sxs-lookup"><span data-stu-id="bd9af-222">**Launch Script** - Launch and debug the specified file or command</span></span>
   - <span data-ttu-id="bd9af-223">**Interactieve sessie** -opdrachten voor fout opsporing in de geïntegreerde console</span><span class="sxs-lookup"><span data-stu-id="bd9af-223">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
   - <span data-ttu-id="bd9af-224">Het fout **opsporingsprogramma koppelen aan** een actief Power shell-hostproces</span><span class="sxs-lookup"><span data-stu-id="bd9af-224">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="bd9af-225">Met Visual Studio code maakt u een map en een bestand `.vscode\launch.json` in de hoofdmap van de map werk ruimte voor het opslaan van de configuratie van fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="bd9af-225">Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder to store the debug configuration.</span></span> <span data-ttu-id="bd9af-226">Als uw bestanden zich in een Git-opslag plaats bevinden, wilt u het bestand doorgaans door voeren `launch.json` .</span><span class="sxs-lookup"><span data-stu-id="bd9af-226">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="bd9af-227">De inhoud van het `launch.json` bestand is:</span><span class="sxs-lookup"><span data-stu-id="bd9af-227">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="bd9af-228">Dit bestand vertegenwoordigt de veelvoorkomende scenario's voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="bd9af-228">This file represents the common debug scenarios.</span></span> <span data-ttu-id="bd9af-229">Wanneer u dit bestand in de editor opent, ziet u een knop **Configuratie toevoegen...** .</span><span class="sxs-lookup"><span data-stu-id="bd9af-229">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="bd9af-230">U kunt op deze knop klikken om meer configuratie van Power Shell-fout opsporing toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="bd9af-230">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="bd9af-231">Een van de handig te toevoegen configuratie is **Power shell: script starten**.</span><span class="sxs-lookup"><span data-stu-id="bd9af-231">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="bd9af-232">Met deze configuratie kunt u een bestand opgeven dat optionele argumenten bevat die worden gebruikt wanneer u op <kbd>F5</kbd> drukt, ongeacht welk bestand in de Editor actief is.</span><span class="sxs-lookup"><span data-stu-id="bd9af-232">With this configuration, you can specify a file containing optional arguments that are used whenever you press <kbd>F5</kbd> no matter which file is active in the editor.</span></span>

<span data-ttu-id="bd9af-233">Nadat de configuratie van de fout opsporing is ingesteld, kunt u selecteren welke configuratie u tijdens een foutopsporingssessie wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bd9af-233">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="bd9af-234">Selecteer een configuratie in de vervolg keuzelijst debug Configuration in de werk balk van de weer gave van de **fout opsporing** .</span><span class="sxs-lookup"><span data-stu-id="bd9af-234">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="bd9af-235">Problemen met de Power shell-extensie voor Visual Studio code oplossen</span><span class="sxs-lookup"><span data-stu-id="bd9af-235">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="bd9af-236">Als u problemen ondervindt met het gebruik van Visual Studio code voor het ontwikkelen van Power shell-scripts, raadpleegt u de [gids voor probleem oplossing][troubleshooting] op github.</span><span class="sxs-lookup"><span data-stu-id="bd9af-236">If you experience any issues using Visual Studio Code for PowerShell script development, see the [troubleshooting guide][troubleshooting] on GitHub.</span></span>

## <a name="useful-resources"></a><span data-ttu-id="bd9af-237">Nuttige informatie</span><span class="sxs-lookup"><span data-stu-id="bd9af-237">Useful resources</span></span>

<span data-ttu-id="bd9af-238">Er zijn enkele Video's en blog berichten die handig kunnen zijn om aan de slag te gaan met behulp van de Power shell-extensie voor Visual Studio code:</span><span class="sxs-lookup"><span data-stu-id="bd9af-238">There are a few videos and blog posts that may be helpful to get you started using the PowerShell extension for Visual Studio Code:</span></span>

### <a name="videos"></a><span data-ttu-id="bd9af-239">Video's</span><span class="sxs-lookup"><span data-stu-id="bd9af-239">Videos</span></span>

- [<span data-ttu-id="bd9af-240">Visual Studio code gebruiken als uw standaard Power shell-editor</span><span class="sxs-lookup"><span data-stu-id="bd9af-240">Using Visual Studio Code as Your Default PowerShell Editor</span></span>](https://youtu.be/bGn45vIeAMM)
- [<span data-ttu-id="bd9af-241">Visual Studio code: dieper in fout opsporing voor uw Power shell-scripts</span><span class="sxs-lookup"><span data-stu-id="bd9af-241">Visual Studio Code: deep dive into debugging your PowerShell scripts</span></span>](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a><span data-ttu-id="bd9af-242">Blogberichten</span><span class="sxs-lookup"><span data-stu-id="bd9af-242">Blog posts</span></span>

- <span data-ttu-id="bd9af-243">[Power shell-uitbrei ding][pscdn]</span><span class="sxs-lookup"><span data-stu-id="bd9af-243">[PowerShell Extension][pscdn]</span></span>
- <span data-ttu-id="bd9af-244">[Power shell-scripts schrijven en fouten opsporen in Visual Studio code][debug]</span><span class="sxs-lookup"><span data-stu-id="bd9af-244">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="bd9af-245">[Fout opsporing van Visual Studio code guidance][psdbgblog]</span><span class="sxs-lookup"><span data-stu-id="bd9af-245">[Debugging Visual Studio Code Guidance][psdbgblog]</span></span>
- <span data-ttu-id="bd9af-246">[Fout opsporing in Power shell in Visual Studio code][psdbg-gh]</span><span class="sxs-lookup"><span data-stu-id="bd9af-246">[Debugging PowerShell in Visual Studio Code][psdbg-gh]</span></span>
- <span data-ttu-id="bd9af-247">[Aan de slag met Power shell-ontwikkeling in Visual Studio code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="bd9af-247">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="bd9af-248">[Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="bd9af-248">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="bd9af-249">[Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="bd9af-249">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="bd9af-250">[Fout opsporing voor Power shell-script in Visual Studio code – deel 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="bd9af-250">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="bd9af-251">[Fout opsporing voor Power shell-script in Visual Studio code – deel 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="bd9af-251">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

## <a name="powershell-extension-project-source-code"></a><span data-ttu-id="bd9af-252">Bron code van Power shell-extensie project</span><span class="sxs-lookup"><span data-stu-id="bd9af-252">PowerShell extension project source code</span></span>

<span data-ttu-id="bd9af-253">De bron code van de Power shell-extensie vindt u op [github][psext-src].</span><span class="sxs-lookup"><span data-stu-id="bd9af-253">The PowerShell extension's source code can be found on [GitHub][psext-src].</span></span>

<span data-ttu-id="bd9af-254">Als u geïnteresseerd bent in bijdragen, worden pull-aanvragen aanzienlijk gewaardeerd.</span><span class="sxs-lookup"><span data-stu-id="bd9af-254">If you're interested in contributing, Pull Requests are greatly appreciated.</span></span> <span data-ttu-id="bd9af-255">Volg samen met de [documentatie voor ontwikkel aars][dev-docs] op github om aan de slag te gaan.</span><span class="sxs-lookup"><span data-stu-id="bd9af-255">Follow along with the [developer documentation][dev-docs] on GitHub to get started.</span></span>

<!-- related articles -->
[ise]:                    ../../windows-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:   ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:   ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]:          ../../install/Installing-Windows-PowerShell.md
[file-encoding]:          understanding-file-encoding.md
[vsc-ise]:                How-To-Replicate-the-ISE-Experience-In-VSCode.md

<!-- blogs -->
[debug]:                  https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[debugging-part1]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
[editing-part1]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[getting-started]:        https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[psdbgblog]:              https://johnpapa.net/debugging-with-visual-studio-code/
[psdbg-gh]:               https://github.com/PowerShell/vscode-powershell/tree/master/examples
[pscdn]:                  https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/

<!-- issues -->
[Problemen met GitHub]:          https://github.com/PowerShell/vscode-powershell/issues
[GitHub issues]:          https://github.com/PowerShell/vscode-powershell/issues
[i1310]:                  https://github.com/PowerShell/vscode-powershell/issues/1310
[i606]:                   https://github.com/PowerShell/vscode-powershell/issues/606

<!-- product links -->
[Visual Studio]:          https://visualstudio.microsoft.com/
[vscode]:                 https://code.visualstudio.com/
[psext]:                  https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[vsc-settings]:           https://code.visualstudio.com/docs/getstarted/settings
[vsc-setup]:              https://code.visualstudio.com/Docs/setup/setup-overview
[vsc-setup-win]:          https://code.visualstudio.com/docs/setup/windows
[vsc-setup-macos]:        https://code.visualstudio.com/docs/setup/mac
[vsc-setup-linux]:        https://code.visualstudio.com/docs/setup/linux
[psext-src]:              https://github.com/PowerShell/vscode-powershell
[troubleshooting]:        https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md
[dev-docs]:               https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md
