---
title: Visual Studio Code gebruiken voor het ontwikkelen van PowerShell
description: Visual Studio Code gebruiken voor het ontwikkelen van PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 0d796460511b273771eacb03d0df4d90e1e9c322
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854394"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="0d4ca-103">Visual Studio Code gebruiken voor het ontwikkelen van PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d4ca-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="0d4ca-104">Naast de [PowerShell ISE][ise], PowerShell wordt ook goed ondersteund in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="0d4ca-105">Bovendien wordt de ISE niet ondersteund met PowerShell Core, terwijl de Visual Studio Code voor PowerShell Core wordt ondersteund op alle platformen (Windows, macOS en Linux)</span><span class="sxs-lookup"><span data-stu-id="0d4ca-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="0d4ca-106">U kunt Visual Studio Code op Windows met PowerShell versie 5 gebruiken met behulp van Windows 10 of door het installeren van [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) voor downlevel-Windows-OSs (bijvoorbeeld Windows 8.1, enzovoort).</span><span class="sxs-lookup"><span data-stu-id="0d4ca-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="0d4ca-107">Voordat u begint met het, Controleer of dat PowerShell bestaat op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="0d4ca-108">Zie voor moderne workloads in Windows, macOS en Linux:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="0d4ca-109">[PowerShell Core in Linux installeren][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="0d4ca-110">[PowerShell Core in macOS installeren][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="0d4ca-111">[PowerShell Core in Windows installeren][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="0d4ca-112">Zie voor traditionele Windows PowerShell-workloads, [Windows PowerShell installeren][install-winps].</span><span class="sxs-lookup"><span data-stu-id="0d4ca-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="0d4ca-113">Bewerken met Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0d4ca-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="0d4ca-114">1. Visual Studio Code installeren</span><span class="sxs-lookup"><span data-stu-id="0d4ca-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="0d4ca-115">**Linux**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op Linux](https://code.visualstudio.com/docs/setup/linux) pagina</span><span class="sxs-lookup"><span data-stu-id="0d4ca-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="0d4ca-116">**macOS**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op macOS](https://code.visualstudio.com/docs/setup/mac) pagina</span><span class="sxs-lookup"><span data-stu-id="0d4ca-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="0d4ca-117">Op Mac OS, moet u OpenSSL voor de extensie van PowerShell correct te laten werken.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="0d4ca-118">De eenvoudigste manier om dit te doen is voor het installeren van [Homebrew](https://brew.sh/) en voer `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="0d4ca-119">VS Code kan nu worden geladen de PowerShell-extensie.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="0d4ca-120">**Windows**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op Windows](https://code.visualstudio.com/docs/setup/windows) pagina</span><span class="sxs-lookup"><span data-stu-id="0d4ca-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="0d4ca-121">2. PowerShell-extensie installeren</span><span class="sxs-lookup"><span data-stu-id="0d4ca-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="0d4ca-122">Start Visual Studio Code app door:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="0d4ca-123">**Windows**: typen `code` in uw PowerShell-sessie</span><span class="sxs-lookup"><span data-stu-id="0d4ca-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="0d4ca-124">**Linux**: typen `code` in uw terminal</span><span class="sxs-lookup"><span data-stu-id="0d4ca-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="0d4ca-125">**macOS**: typen `code` in uw terminal</span><span class="sxs-lookup"><span data-stu-id="0d4ca-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="0d4ca-126">Start **snel openen** door te drukken **Ctrl + P** (**Cmd + P** op Mac).</span><span class="sxs-lookup"><span data-stu-id="0d4ca-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="0d4ca-127">Typ in snel openen `ext install powershell` en klik op **Enter**.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="0d4ca-128">De **extensies** weergave geopend op de zijbalk.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="0d4ca-129">Selecteer de PowerShell-uitbreiding van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="0d4ca-130">U zou iets moet zien zoals hieronder:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="0d4ca-132">Klik op de **installeren** knop van de PowerShell-extensie van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="0d4ca-133">Na de installatie, ziet u de **installeren** knop verandert in **opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="0d4ca-134">Klik op **opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-134">Click on **Reload**.</span></span>
- <span data-ttu-id="0d4ca-135">Nadat Visual Studio Code opnieuw laden is, bent u klaar voor het bewerken van.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="0d4ca-136">Bijvoorbeeld, als u wilt een nieuw bestand maken, klikt u op **File -> New**.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="0d4ca-137">Als u wilt opslaan, klikt u op **File -> Opslaan** en geef vervolgens een bestandsnaam op, laten we zeggen `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="0d4ca-138">U sluit het bestand, klikt u op 'x' naast de bestandsnaam van het.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="0d4ca-139">Om af te sluiten van Visual Studio Code, **File -> afsluiten**.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="0d4ca-140">Installeren van de PowerShell-extensie op systemen met beperkte toegang</span><span class="sxs-lookup"><span data-stu-id="0d4ca-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="0d4ca-141">Sommige systemen zijn ingesteld op een manier die nodig zijn alle code handtekeningen moet worden gecontroleerd en dus nodig PowerShell Editor Services handmatig worden goedgekeurd om te worden uitgevoerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="0d4ca-142">Als u de extensie van PowerShell hebt geïnstalleerd, maar een foutmelding als zijn bereikt, is een Groepsbeleid-update die uitvoeringsbeleid wijzigen een waarschijnlijke oorzaak:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="0d4ca-143">Open een PowerShell-prompt en voer voor het handmatig goedkeuren van PowerShell Editor Services en dus de PowerShell-extensie voor VSCode:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="0d4ca-144">U wordt gevraagd met "Wilt u uitvoeren van software van deze niet-vertrouwde uitgever?"</span><span class="sxs-lookup"><span data-stu-id="0d4ca-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="0d4ca-145">Type `R` het bestand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-145">Type `R` to run the file.</span></span> <span data-ttu-id="0d4ca-146">Vervolgens opent u Visual Studio Code en controleer of de PowerShell-uitbreiding correct functioneert.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="0d4ca-147">Als u nog steeds problemen aan de slag hebt, laat het ons weten op [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="0d4ca-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="0d4ca-148">Een versie van PowerShell gebruiken met de extensie kiezen</span><span class="sxs-lookup"><span data-stu-id="0d4ca-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="0d4ca-149">Met PowerShell Core side-by-side installeren met Windows PowerShell, is het nu mogelijk om een bepaalde versie van PowerShell met de extensie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="0d4ca-150">Gebruik de volgende stappen als u wilt de versie kiezen:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="0d4ca-151">Open het palet opdracht (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> op Windows & Linux, <kbd>Cmd</kbd> + <kbd>Shift</kbd>+<kbd>P</kbd> in macOS).</span><span class="sxs-lookup"><span data-stu-id="0d4ca-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="0d4ca-152">Zoek naar 'Sessie'.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-152">Search for "Session".</span></span>
1. <span data-ttu-id="0d4ca-153">Klik op ' PowerShell: Sessie-Menu weergeven'.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="0d4ca-154">Kies de versie van PowerShell die u wilt gebruiken in de lijst, bijvoorbeeld 'PowerShell Core'.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

>[!IMPORTANT]
> <span data-ttu-id="0d4ca-155">Deze functie kijkt naar enkele bekende paden op verschillende besturingssystemen worden uitgevoerd voor het detecteren van locaties van de installatie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="0d4ca-156">Als u PowerShell hebt geïnstalleerd op een niet-standaard locatie, deze mogelijk niet weergegeven in eerste instantie in het Menu van de sessie.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="0d4ca-157">U kunt de sessie-menu door uitbreiden [toevoegen van uw eigen aangepaste paden](#adding-your-own-powershell-paths-to-the-session-menu) zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="0d4ca-158">Er is een andere manier om te gaan naar het menu van de sessie.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="0d4ca-159">Wanneer een PowerShell-bestand geopend in de editor is, ziet u een groene versienummer in de rechterbenedenhoek.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="0d4ca-160">Dit versienummer op te klikken, gaat u naar het menu van de sessie.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="0d4ca-161">Uw eigen PowerShell-paden toe te voegen aan de sessie-menu</span><span class="sxs-lookup"><span data-stu-id="0d4ca-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="0d4ca-162">U kunt andere uitvoerbare PowerShell-paden toevoegen aan het menu sessie via een instelling voor VS Code.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-162">You can add other PowerShell executable paths to the session menu through a VS Code setting.</span></span>

<span data-ttu-id="0d4ca-163">Een item toevoegen aan de lijst met `powershell.powerShellAdditionalExePaths` of de lijst te maken als deze niet bestaat uw `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-163">Add an item to the list  `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="0d4ca-164">Elk item moet beschikken over:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-164">Each item must have:</span></span>

* <span data-ttu-id="0d4ca-165">`exePath`: Het pad naar de `pwsh` of `powershell` uitvoerbaar bestand.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="0d4ca-166">`versionName`: De tekst die wordt weergegeven in het menu van de sessie.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="0d4ca-167">U kunt instellen dat de standaardversie van PowerShell gebruiken met behulp van de `powershell.powerShellDefaultVersion` instelling door dit aan in de tekst weergegeven in het menu van de sessie (ook wel de `versionName` in de laatste instelling):</span><span class="sxs-lookup"><span data-stu-id="0d4ca-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="0d4ca-168">Als u deze instelling hebt ingesteld, start u Visual Studio Code of gebruik de de "Developer: Venster laden"palet opdrachtactie laden van de huidige vscode-venster.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-168">Once you've set this setting, restart Visual Studio Code or use the the "Developer: Reload Window" command pallet action to reload the current vscode window.</span></span>

<span data-ttu-id="0d4ca-169">Als u het menu sessie opent, ziet u nu de aanvullende versies van PowerShell!</span><span class="sxs-lookup"><span data-stu-id="0d4ca-169">If you open the session menu, you will now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="0d4ca-170">Als u PowerShell van bron bouwt, is dit een uitstekende manier om het testen van uw lokale build van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="0d4ca-171">Configuratie-instellingen voor Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0d4ca-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="0d4ca-172">U kunt configuratie-instellingen in toevoegen met behulp van de stappen in de vorige alinea `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="0d4ca-173">U wordt aangeraden de volgende configuratie-instellingen voor Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-173">We recommend the following configuration settings for Visual Studio Code:</span></span>

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

<span data-ttu-id="0d4ca-174">Als u niet dat deze instellingen wilt beïnvloeden alle bestandstypen, kan VSCode per taal configuraties.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="0d4ca-175">Maken van een bepaalde taal-instelling door te nemen van instellingen een `[<language-name>]` veld.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="0d4ca-176">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="0d4ca-177">Zie voor meer informatie over bestand codering in VS Code [begrijpen bestandscodering](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="0d4ca-177">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="0d4ca-178">Fouten opsporen met Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0d4ca-178">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="0d4ca-179">Geen werkruimte foutopsporing</span><span class="sxs-lookup"><span data-stu-id="0d4ca-179">No-workspace debugging</span></span>

<span data-ttu-id="0d4ca-180">Vanaf versie van Visual Studio Code 1.9 kunt u PowerShell-scripts fouten opsporen zonder te open de map met het PowerShell-script.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-180">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="0d4ca-181">Open de PowerShell-scriptbestand met **File -> bestand openen...** , stel een onderbrekingspunt in op een regel (druk op F9) en druk vervolgens op F5 foutopsporing te starten.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="0d4ca-182">U ziet het actiedeelvenster van foutopsporing worden weergegeven waarmee u in het foutopsporingsprogramma, stap, hervatten en stop foutopsporing opsplitsen.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="0d4ca-183">Werkruimte-foutopsporing</span><span class="sxs-lookup"><span data-stu-id="0d4ca-183">Workspace debugging</span></span>

<span data-ttu-id="0d4ca-184">Werkruimte foutopsporing verwijst naar het opsporen van fouten in de context van een map die u hebt geopend in Visual Studio Code met behulp van **map openen...**  uit de **bestand** menu.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="0d4ca-185">De map die u opent is meestal de projectmap op PowerShell en/of de hoofdmap van de Git-opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="0d4ca-186">Zelfs in deze modus kunt u beginnen met het opsporen van fouten in de momenteel geselecteerde PowerShell-script door op F5 te drukken.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="0d4ca-187">Echter, kunt u definiëren configuraties met meerdere foutopsporing dan alleen opsporen van fouten in het geopende bestand werkruimte foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="0d4ca-188">U kunt bijvoorbeeld een configuraties die u kunt toevoegen:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="0d4ca-189">Pester tests in het foutopsporingsprogramma Start</span><span class="sxs-lookup"><span data-stu-id="0d4ca-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="0d4ca-190">Een specifiek bestand met argumenten in het foutopsporingsprogramma Start</span><span class="sxs-lookup"><span data-stu-id="0d4ca-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="0d4ca-191">Een interactieve sessie in het foutopsporingsprogramma Start</span><span class="sxs-lookup"><span data-stu-id="0d4ca-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="0d4ca-192">Het foutopsporingsprogramma koppelen aan een hostproces van PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d4ca-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="0d4ca-193">Volg deze stappen om uw debug-configuratiebestand te maken:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="0d4ca-194">Open de **Debug** weergeven door te drukken **Ctrl + Shift + D** (**Cmd + Shift + D** op Mac).</span><span class="sxs-lookup"><span data-stu-id="0d4ca-194">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="0d4ca-195">Druk op de **configureren** tandwielpictogram in de werkbalk.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-195">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="0d4ca-196">U wordt gevraagd om Visual Studio Code **omgeving selecteert**.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-196">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="0d4ca-197">Kies **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="0d4ca-198">Als u dit doet, maakt Visual Studio Code een map en een bestand '.vscode\launch.json' in de hoofdmap van de werkruimtemap van uw.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-198">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="0d4ca-199">Dit is waar uw debug-configuratie is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="0d4ca-200">Als de bestanden zich in een Git-opslagplaats, wilt u meestal het bestand launch.json doorvoeren.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="0d4ca-201">De inhoud van het bestand launch.json zijn:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-201">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="0d4ca-202">Hiermee wordt de algemene scenario's voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-202">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="0d4ca-203">Echter, als u dit bestand in de editor opent, ziet u een **configuratie toevoegen...**  knop.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="0d4ca-204">U drukt op deze knop om toe te voegen meer PowerShell-configuraties voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-204">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="0d4ca-205">Een handige configuratie toe te voegen is **PowerShell: Script Start**.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="0d4ca-206">Met deze configuratie kunt u een specifiek bestand met optionele argumenten die moet worden gestart wanneer u op F5 drukt ongeacht welk bestand is momenteel actief zijn in de editor.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="0d4ca-207">Zodra de configuratie van de foutopsporing tot stand is gebracht, kunt u selecteren welke configuratie u gebruiken tijdens een foutopsporingssessie wilt door het selecteren van een van de configuratie van de foutopsporing vervolgkeuzelijst in de **Debug** van weergave-werkbalk.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="0d4ca-208">Er zijn een paar blogs die mogelijk nuttig zijn om aan de slag met PowerShell-extensie voor Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="0d4ca-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="0d4ca-209">[Extensie van PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="0d4ca-210">[Schrijf en fouten opsporen in PowerShell-scripts in Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="0d4ca-211">[Foutopsporing van Visual Studio Code-richtlijnen][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="0d4ca-212">[Foutopsporing in PowerShell in Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="0d4ca-213">[Aan de slag met PowerShell-ontwikkeling in Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="0d4ca-214">[Visual Studio Code bewerken van functies voor het ontwikkelen van PowerShell-deel 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="0d4ca-215">[Visual Studio Code bewerken van functies voor het ontwikkelen van PowerShell-deel 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="0d4ca-216">[PowerShell-script voor foutopsporing in Visual Studio Code – deel 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="0d4ca-217">[PowerShell-script voor foutopsporing in Visual Studio Code – deel 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="0d4ca-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="0d4ca-218">PowerShell-extensie voor Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0d4ca-218">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="0d4ca-219">De broncode van de PowerShell-extensie kunt u vinden op [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="0d4ca-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
