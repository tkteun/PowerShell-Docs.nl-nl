---
title: De ISE-ervaring in Visual Studio Code repliceren
description: De ISE-ervaring in Visual Studio Code repliceren
ms.date: 08/06/2018
ms.openlocfilehash: 6b0b8ce054695d6cc0fc578290c554e2dc1472bc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784619"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="6fe85-103">De ISE-ervaring in Visual Studio Code repliceren</span><span class="sxs-lookup"><span data-stu-id="6fe85-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="6fe85-104">Hoewel met de Power shell-extensie voor VS code niet wordt gezocht naar de functie pariteit met de Power shell-ISE, zijn er functies die ervoor zorgen dat de VS code natuurlijk meer natuurlijke is voor gebruikers van de ISE.</span><span class="sxs-lookup"><span data-stu-id="6fe85-104">While the PowerShell extension for VS Code doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VS Code experience more natural for users of the ISE.</span></span>

<span data-ttu-id="6fe85-105">In dit document wordt geprobeerd een lijst te maken met de instellingen die u kunt configureren in VS code, zodat de gebruiker meer vertrouwd is vergeleken met de ISE.</span><span class="sxs-lookup"><span data-stu-id="6fe85-105">This document tries to list settings you can configure in VS Code to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="6fe85-106">ISE-modus</span><span class="sxs-lookup"><span data-stu-id="6fe85-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="6fe85-107">Deze functie is beschikbaar in de Power shell preview-uitbrei ding sinds versie 2019.12.0 en in de Power shell-uitbrei ding sinds versie 2020.3.0.</span><span class="sxs-lookup"><span data-stu-id="6fe85-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="6fe85-108">De eenvoudigste manier om de ISE-ervaring in Visual Studio code te repliceren, is door ' ISE-modus ' in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="6fe85-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="6fe85-109">Hiertoe opent u het opdracht palet (<kbd>F1</kbd> of <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>p</kbd> of <kbd>cmd</kbd> + <kbd>SHIFT</kbd> + <kbd>p</kbd> op macOS) en typt u ' ISE-modus '.</span><span class="sxs-lookup"><span data-stu-id="6fe85-109">To do this, open the command palette (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span> <span data-ttu-id="6fe85-110">Selecteer Power shell: ISE-modus inschakelen in de lijst.</span><span class="sxs-lookup"><span data-stu-id="6fe85-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="6fe85-111">Met deze opdracht worden de instellingen die onder het resultaat worden beschreven, automatisch toegepast op de volgende manier:</span><span class="sxs-lookup"><span data-stu-id="6fe85-111">This command automatically applies the settings described below The result looks like this:</span></span>

![Visual Studio code in de modus ISE](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a><span data-ttu-id="6fe85-113">Configuratie-instellingen voor ISE-modus</span><span class="sxs-lookup"><span data-stu-id="6fe85-113">ISE Mode configuration settings</span></span>

<span data-ttu-id="6fe85-114">Met de ISE-modus worden de volgende wijzigingen aangebracht in VS-code-instellingen.</span><span class="sxs-lookup"><span data-stu-id="6fe85-114">ISE Mode makes the following changes to VS Code settings.</span></span>

- <span data-ttu-id="6fe85-115">Sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="6fe85-115">Key bindings</span></span>

  |               <span data-ttu-id="6fe85-116">Functie</span><span class="sxs-lookup"><span data-stu-id="6fe85-116">Function</span></span>                |         <span data-ttu-id="6fe85-117">ISE-binding</span><span class="sxs-lookup"><span data-stu-id="6fe85-117">ISE Binding</span></span>          |              <span data-ttu-id="6fe85-118">VS-code binding</span><span class="sxs-lookup"><span data-stu-id="6fe85-118">VS Code Binding</span></span>                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | <span data-ttu-id="6fe85-119">Fout opsporing onderbreken en verbreken</span><span class="sxs-lookup"><span data-stu-id="6fe85-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="6fe85-120"><kbd>CTRL</kbd> + <kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="6fe85-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="6fe85-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="6fe85-121"><kbd>F6</kbd></span></span>                               |
  | <span data-ttu-id="6fe85-122">Huidige regel/gemarkeerde tekst uitvoeren</span><span class="sxs-lookup"><span data-stu-id="6fe85-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="6fe85-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="6fe85-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="6fe85-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="6fe85-124"><kbd>F8</kbd></span></span>                               |
  | <span data-ttu-id="6fe85-125">Beschik bare fragmenten weer geven</span><span class="sxs-lookup"><span data-stu-id="6fe85-125">List available snippets</span></span>               | <span data-ttu-id="6fe85-126"><kbd>CTRL</kbd> + <kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="6fe85-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="6fe85-127"><kbd>CTRL</kbd> + <kbd>Alt</kbd> + <kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="6fe85-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

  > [!NOTE]
  > <span data-ttu-id="6fe85-128">U kunt ook [uw eigen sleutel bindingen configureren](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VS code.</span><span class="sxs-lookup"><span data-stu-id="6fe85-128">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VS Code as well.</span></span>

- <span data-ttu-id="6fe85-129">Vereenvoudigde ISE-achtige gebruikers interface</span><span class="sxs-lookup"><span data-stu-id="6fe85-129">Simplified ISE-like UI</span></span>

  <span data-ttu-id="6fe85-130">Als u de gebruikers interface van Visual Studio wilt vereenvoudigen om nauw keuriger te kijken naar de gebruikers interface van de ISE, moet u deze twee instellingen Toep assen:</span><span class="sxs-lookup"><span data-stu-id="6fe85-130">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  <span data-ttu-id="6fe85-131">Deze instellingen verbergen de ' activiteiten balk ' en de sectie ' fout opsporen van zijkant ' in het rode vak hieronder weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="6fe85-131">These settings hide the "Activity Bar" and the "Debug Side Bar" sections shown inside the red box below:</span></span>

  ![De gemarkeerde sectie bevat de activiteiten balk en de fout balk aan de zijkant](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  <span data-ttu-id="6fe85-133">Het eind resultaat ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="6fe85-133">The end result looks like this:</span></span>

  ![Vereenvoudigde weer gave van VS code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- <span data-ttu-id="6fe85-135">Tabblad voltooiing</span><span class="sxs-lookup"><span data-stu-id="6fe85-135">Tab completion</span></span>

  <span data-ttu-id="6fe85-136">Als u meer ISE wilt inschakelen, voegt u deze instelling toe:</span><span class="sxs-lookup"><span data-stu-id="6fe85-136">To enable more ISE-like tab completion, add this setting:</span></span>

  ```json
  "editor.tabCompletion": "on",
  ```

- <span data-ttu-id="6fe85-137">Geen focus op console bij het uitvoeren van</span><span class="sxs-lookup"><span data-stu-id="6fe85-137">No focus on console when executing</span></span>

  <span data-ttu-id="6fe85-138">Als u de focus in de editor wilt houden wanneer u uitvoert met <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="6fe85-138">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  <span data-ttu-id="6fe85-139">De standaard instelling is `true` voor toegankelijkheids doeleinden.</span><span class="sxs-lookup"><span data-stu-id="6fe85-139">The default is `true` for accessibility purposes.</span></span>

- <span data-ttu-id="6fe85-140">Geïntegreerde console niet starten bij opstarten</span><span class="sxs-lookup"><span data-stu-id="6fe85-140">Don't start integrated console on startup</span></span>

  <span data-ttu-id="6fe85-141">Als u de geïntegreerde console tijdens het opstarten wilt stoppen, stelt u het volgende in:</span><span class="sxs-lookup"><span data-stu-id="6fe85-141">To stop the integrated console on startup, set:</span></span>

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > <span data-ttu-id="6fe85-142">Het Power Shell-proces voor de achtergrond begint nog steeds IntelliSense, script analyse, navigatie naar symbolen, enzovoort, maar de console wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6fe85-142">The background PowerShell process still starts to provide IntelliSense, script analysis, symbol navigation, etc., but the console won't be shown.</span></span>

- <span data-ttu-id="6fe85-143">Aannemen dat bestanden standaard Power shell zijn</span><span class="sxs-lookup"><span data-stu-id="6fe85-143">Assume files are PowerShell by default</span></span>

  <span data-ttu-id="6fe85-144">Als u nieuwe/naamloze bestanden wilt maken, moet u zich standaard als Power shell registreren:</span><span class="sxs-lookup"><span data-stu-id="6fe85-144">To make new/untitled files, register as PowerShell by default:</span></span>

  ```json
  "files.defaultLanguage": "powershell",
  ```

- <span data-ttu-id="6fe85-145">Kleurenschema</span><span class="sxs-lookup"><span data-stu-id="6fe85-145">Color scheme</span></span>

  <span data-ttu-id="6fe85-146">Er zijn een aantal ISE-Thema's beschikbaar voor VS code om ervoor te zorgen dat de editor er veel meer uitziet als de ISE.</span><span class="sxs-lookup"><span data-stu-id="6fe85-146">There are a number of ISE themes available for VS Code to make the editor look much more like the ISE.</span></span>

  <span data-ttu-id="6fe85-147">In het [opdracht palet][] typt `theme` u `Preferences: Color Theme` en drukt u op <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="6fe85-147">In the [Command Palette][] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span> <span data-ttu-id="6fe85-148">Selecteer in de vervolg keuzelijst `PowerShell ISE` .</span><span class="sxs-lookup"><span data-stu-id="6fe85-148">In the drop-down list, select `PowerShell ISE`.</span></span>

  <span data-ttu-id="6fe85-149">U kunt dit thema instellen in de instellingen met:</span><span class="sxs-lookup"><span data-stu-id="6fe85-149">You can set this theme in the settings with:</span></span>

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- <span data-ttu-id="6fe85-150">Power shell-opdracht Verkenner</span><span class="sxs-lookup"><span data-stu-id="6fe85-150">PowerShell Command Explorer</span></span>

  <span data-ttu-id="6fe85-151">Dankzij het werk van [@corbob](https://github.com/corbob) is de Power shell-uitbrei ding het begin van een eigen opdracht Verkenner.</span><span class="sxs-lookup"><span data-stu-id="6fe85-151">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

  <span data-ttu-id="6fe85-152">Voer in het [opdracht palet][]Enter `PowerShell Command Explorer` en druk op <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="6fe85-152">In the [Command Palette][], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

- <span data-ttu-id="6fe85-153">Open in de ISE</span><span class="sxs-lookup"><span data-stu-id="6fe85-153">Open in the ISE</span></span>

  <span data-ttu-id="6fe85-154">Als u een bestand in de Windows PowerShell ISE toch wilt openen, opent u het [opdracht palet][], zoekt u naar ' openen in ISE ' en selecteert u vervolgens **Power shell: huidig bestand openen in Power shell ISE**.</span><span class="sxs-lookup"><span data-stu-id="6fe85-154">If you want to open a file in the Windows PowerShell ISE anyway, open the [Command Palette][], search for "open in ise", then select **PowerShell: Open Current File in PowerShell ISE**.</span></span>

## <a name="other-resources"></a><span data-ttu-id="6fe85-155">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="6fe85-155">Other resources</span></span>

- <span data-ttu-id="6fe85-156">4sysops heeft [een geweldig artikel][4sysops] over het configureren van VS code zodat deze meer lijkt op het ISE.</span><span class="sxs-lookup"><span data-stu-id="6fe85-156">4sysops has [a great article][4sysops] on configuring VS Code to be more like the ISE.</span></span>
- <span data-ttu-id="6fe85-157">Mike F Robbins heeft [een geweldig bericht over het][mikefrobbins] instellen van VS code.</span><span class="sxs-lookup"><span data-stu-id="6fe85-157">Mike F Robbins has [a great post][mikefrobbins] on setting up VS Code.</span></span>
<!-- - Learn PowerShell has [an excellent write up][learnpwsh] setup for PowerShell. -->

## <a name="vs-code-tips"></a><span data-ttu-id="6fe85-158">VS-code tips</span><span class="sxs-lookup"><span data-stu-id="6fe85-158">VS Code Tips</span></span>

- <span data-ttu-id="6fe85-159">Opdracht palet</span><span class="sxs-lookup"><span data-stu-id="6fe85-159">Command Palette</span></span>

  <span data-ttu-id="6fe85-160">Het opdracht palet is een handige manier om opdrachten in VS code uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="6fe85-160">The Command Palette is handy way of executing commands in VS Code.</span></span> <span data-ttu-id="6fe85-161">Open het opdracht palet met <kbd>F1</kbd> of <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>p</kbd> of <kbd>cmd</kbd> + <kbd>SHIFT</kbd> + <kbd>p</kbd> in macOS.</span><span class="sxs-lookup"><span data-stu-id="6fe85-161">Open the command palette using <kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS.</span></span>

  <span data-ttu-id="6fe85-162">Raadpleeg [de VS code-documentatie][vsc-docs]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6fe85-162">For more information, see [the VS Code documentation][vsc-docs].</span></span>

- <span data-ttu-id="6fe85-163">De console fout opsporing uitschakelen</span><span class="sxs-lookup"><span data-stu-id="6fe85-163">Disable the Debug Console</span></span>

  <span data-ttu-id="6fe85-164">Als u alleen van plan bent om gebruik te maken van VS code voor Power shell-scripts, kunt u de **console voor fout opsporing** verbergen omdat deze niet wordt gebruikt door de Power shell-extensie.</span><span class="sxs-lookup"><span data-stu-id="6fe85-164">If you only plan on using VS Code for PowerShell scripting, you can hide the **Debug Console** since it is not used by the PowerShell extension.</span></span> <span data-ttu-id="6fe85-165">Hiertoe klikt u met de rechter muisknop op **debug-console** en klikt u vervolgens op het vinkje om het te verbergen.</span><span class="sxs-lookup"><span data-stu-id="6fe85-165">To do so, right click on **Debug Console** then click on the check mark to hide it.</span></span>

## <a name="more-settings"></a><span data-ttu-id="6fe85-166">Meer instellingen</span><span class="sxs-lookup"><span data-stu-id="6fe85-166">More settings</span></span>

<span data-ttu-id="6fe85-167">Als u meer wilt weten over de verschillende manieren om de code van ISE-gebruikers beter te maken, kunt u het beste een bijdrage leveren aan dit document. Als er een compatibiliteits configuratie is die u zoekt, maar u geen manier kunt vinden om deze in te scha kelen, [opent u een probleem][] en vraagt u dit af.</span><span class="sxs-lookup"><span data-stu-id="6fe85-167">If you know of more ways to make VS Code feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue][] and ask away!</span></span>

<span data-ttu-id="6fe85-168">We zijn altijd blij om pull en bijdragen ook te accepteren.</span><span class="sxs-lookup"><span data-stu-id="6fe85-168">We're always happy to accept PRs and contributions as well!</span></span>

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[Opdracht palet]: #vs-code-tips
[Command Palette]: #vs-code-tips
[een probleem openen]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose
[open an issue]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
