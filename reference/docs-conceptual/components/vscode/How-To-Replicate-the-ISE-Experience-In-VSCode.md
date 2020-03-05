---
title: De ISE-ervaring in Visual Studio Code repliceren
description: De ISE-ervaring in Visual Studio Code repliceren
ms.date: 08/06/2018
ms.openlocfilehash: 193243dc2e3e921b22a6ee068370200ae84ce4ac
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279240"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="a1fae-103">De ISE-ervaring in Visual Studio Code repliceren</span><span class="sxs-lookup"><span data-stu-id="a1fae-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="a1fae-104">Hoewel de Power shell-extensie voor VSCode niet de functie pariteit van de Power shell-ISE doorzoekt, zijn er functies aanwezig waarmee de VSCode-ervaring natuurlijker wordt voor gebruikers van de ISE.</span><span class="sxs-lookup"><span data-stu-id="a1fae-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="a1fae-105">In dit document wordt geprobeerd een lijst te maken met de instellingen die u kunt configureren in VSCode, zodat de gebruiker een beetje bekender is vergeleken met de ISE.</span><span class="sxs-lookup"><span data-stu-id="a1fae-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="a1fae-106">ISE-modus</span><span class="sxs-lookup"><span data-stu-id="a1fae-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="a1fae-107">Deze functie is beschikbaar in de Power shell preview-uitbrei ding sinds versie 2019.12.0 en in de Power shell-uitbrei ding sinds versie 2020.3.0.</span><span class="sxs-lookup"><span data-stu-id="a1fae-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="a1fae-108">De eenvoudigste manier om de ISE-ervaring in Visual Studio code te repliceren, is door ' ISE-modus ' in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="a1fae-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="a1fae-109">Hiervoor opent u de opdracht pallet (<kbd>F1</kbd> of <kbd>Ctrl</kbd>+<kbd>shift</kbd>+<kbd>p</kbd> of <kbd>cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>p</kbd> op macOS) en typt u ' ISE-modus '.</span><span class="sxs-lookup"><span data-stu-id="a1fae-109">To do this, open the command pallet (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span>
<span data-ttu-id="a1fae-110">Selecteer Power shell: ISE-modus inschakelen in de lijst.</span><span class="sxs-lookup"><span data-stu-id="a1fae-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="a1fae-111">Met deze opdracht worden automatisch veel instellingen toegepast die in dit document worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="a1fae-111">This command will apply a lot of the settings found in this document automatically.</span></span>
<span data-ttu-id="a1fae-112">Het resultaat ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="a1fae-112">The result looks like this:</span></span>

![ISE-modus](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

<span data-ttu-id="a1fae-114">De rest van dit artikel bevat gedetailleerde informatie over de instellingen in de ISE-modus en enkele aanvullende instellingen.</span><span class="sxs-lookup"><span data-stu-id="a1fae-114">The rest of this article includes more detailed information on settings in ISE Mode and some additional settings.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="a1fae-115">Sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="a1fae-115">Key bindings</span></span>

| <span data-ttu-id="a1fae-116">Function</span><span class="sxs-lookup"><span data-stu-id="a1fae-116">Function</span></span>                              | <span data-ttu-id="a1fae-117">ISE-binding</span><span class="sxs-lookup"><span data-stu-id="a1fae-117">ISE Binding</span></span>                  | <span data-ttu-id="a1fae-118">VSCode-binding</span><span class="sxs-lookup"><span data-stu-id="a1fae-118">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="a1fae-119">Fout opsporing onderbreken en verbreken</span><span class="sxs-lookup"><span data-stu-id="a1fae-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="a1fae-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="a1fae-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="a1fae-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="a1fae-121"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="a1fae-122">Huidige regel/gemarkeerde tekst uitvoeren</span><span class="sxs-lookup"><span data-stu-id="a1fae-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="a1fae-123"><kbd>Drukken</kbd></span><span class="sxs-lookup"><span data-stu-id="a1fae-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="a1fae-124"><kbd>Drukken</kbd></span><span class="sxs-lookup"><span data-stu-id="a1fae-124"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="a1fae-125">Beschik bare fragmenten weer geven</span><span class="sxs-lookup"><span data-stu-id="a1fae-125">List available snippets</span></span>               | <span data-ttu-id="a1fae-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="a1fae-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="a1fae-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="a1fae-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="a1fae-128">Aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="a1fae-128">Custom Key bindings</span></span>

<span data-ttu-id="a1fae-129">U kunt ook [uw eigen sleutel bindingen configureren](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode.</span><span class="sxs-lookup"><span data-stu-id="a1fae-129">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="a1fae-130">Vereenvoudigde ISE-achtige gebruikers interface</span><span class="sxs-lookup"><span data-stu-id="a1fae-130">Simplified ISE-like UI</span></span>

<span data-ttu-id="a1fae-131">Als u de gebruikers interface van Visual Studio wilt vereenvoudigen om nauw keuriger te kijken naar de gebruikers interface van de ISE, moet u deze twee instellingen Toep assen:</span><span class="sxs-lookup"><span data-stu-id="a1fae-131">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

> [!NOTE]
> <span data-ttu-id="a1fae-132">Deze instellingen zijn opgenomen in de [' ISE-modus '](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="a1fae-132">These settings are included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="a1fae-133">Hiermee worden de volgende secties in het vak rood weer gegeven: ' activiteiten balk ' en ' balk voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="a1fae-133">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![de gemarkeerde sectie bevat de activiteiten balk en de fout balk aan de zijkant](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="a1fae-135">Het eind resultaat ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="a1fae-135">The end result looks like this:</span></span>

![Vereenvoudigde weer gave van VS code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="a1fae-137">Tabblad voltooiing</span><span class="sxs-lookup"><span data-stu-id="a1fae-137">Tab completion</span></span>

<span data-ttu-id="a1fae-138">Als u meer ISE wilt inschakelen, voegt u deze instelling toe:</span><span class="sxs-lookup"><span data-stu-id="a1fae-138">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="a1fae-139">Deze instelling is rechtstreeks aan VSCode toegevoegd (in plaats van in de extensie).</span><span class="sxs-lookup"><span data-stu-id="a1fae-139">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="a1fae-140">Het gedrag wordt rechtstreeks door VSCode bepaald en kan niet worden gewijzigd door de extensie.</span><span class="sxs-lookup"><span data-stu-id="a1fae-140">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

> [!NOTE]
> <span data-ttu-id="a1fae-141">Deze instelling is opgenomen in de [ISE-modus](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="a1fae-141">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="a1fae-142">Geen focus op console bij het uitvoeren van</span><span class="sxs-lookup"><span data-stu-id="a1fae-142">No focus on console when executing</span></span>

<span data-ttu-id="a1fae-143">Als u de focus in de editor wilt houden wanneer u uitvoert met <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="a1fae-143">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> <span data-ttu-id="a1fae-144">Deze instelling is opgenomen in de [ISE-modus](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="a1fae-144">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="a1fae-145">De standaard waarde is `true` voor toegankelijkheids doeleinden.</span><span class="sxs-lookup"><span data-stu-id="a1fae-145">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="a1fae-146">Geïntegreerde console niet starten bij opstarten</span><span class="sxs-lookup"><span data-stu-id="a1fae-146">Don't start integrated console on startup</span></span>

<span data-ttu-id="a1fae-147">Als u de geïntegreerde console tijdens het opstarten wilt stoppen, stelt u het volgende in:</span><span class="sxs-lookup"><span data-stu-id="a1fae-147">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="a1fae-148">Het Power Shell-proces op de achtergrond wordt nog steeds gestart, omdat IntelliSense, script analyse, navigatie naar symbolen, enzovoort. Maar de console wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a1fae-148">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="a1fae-149">Aannemen dat bestanden standaard Power shell zijn</span><span class="sxs-lookup"><span data-stu-id="a1fae-149">Assume files are PowerShell by default</span></span>

<span data-ttu-id="a1fae-150">Als u nieuwe/naamloze bestanden wilt maken, moet u zich standaard als Power shell registreren:</span><span class="sxs-lookup"><span data-stu-id="a1fae-150">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

> [!NOTE]
> <span data-ttu-id="a1fae-151">Deze instelling is opgenomen in de [ISE-modus](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="a1fae-151">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="color-scheme"></a><span data-ttu-id="a1fae-152">Kleuren schema</span><span class="sxs-lookup"><span data-stu-id="a1fae-152">Color scheme</span></span>

<span data-ttu-id="a1fae-153">Er zijn een aantal ISE-Thema's beschikbaar voor VSCode, waardoor de editor veel meer lijkt op de ISE.</span><span class="sxs-lookup"><span data-stu-id="a1fae-153">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="a1fae-154">Typ in het [opdracht palet] `theme` om `Preferences: Color Theme` op te halen en druk op <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="a1fae-154">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="a1fae-155">Selecteer `PowerShell ISE`in de vervolg keuzelijst.</span><span class="sxs-lookup"><span data-stu-id="a1fae-155">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="a1fae-156">U kunt dit thema instellen in de instellingen met:</span><span class="sxs-lookup"><span data-stu-id="a1fae-156">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> <span data-ttu-id="a1fae-157">Deze instelling is opgenomen in de [ISE-modus](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="a1fae-157">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="powershell-command-explorer"></a><span data-ttu-id="a1fae-158">Power shell-opdracht Verkenner</span><span class="sxs-lookup"><span data-stu-id="a1fae-158">PowerShell Command Explorer</span></span>

<span data-ttu-id="a1fae-159">Dankzij het werk van [@corbob](https://github.com/corbob)heeft de Power shell-uitbrei ding het begin van een eigen opdracht Verkenner.</span><span class="sxs-lookup"><span data-stu-id="a1fae-159">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="a1fae-160">Voer in het [opdracht palet]`PowerShell Command Explorer` in en druk op <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="a1fae-160">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

> [!NOTE]
> <span data-ttu-id="a1fae-161">Dit wordt automatisch weer gegeven in de [' ISE-modus '](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="a1fae-161">This is shown automatically in ["ISE Mode"](#ise-mode).</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="a1fae-162">Open in de ISE</span><span class="sxs-lookup"><span data-stu-id="a1fae-162">Open in the ISE</span></span>

<span data-ttu-id="a1fae-163">Als u uiteindelijk wilt dat een bestand in de ISE toch opent, kunt u <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a1fae-163">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="a1fae-164">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="a1fae-164">Other resources</span></span>

- <span data-ttu-id="a1fae-165">4sysops heeft [een geweldig artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) over het configureren van VSCode als de ISE.</span><span class="sxs-lookup"><span data-stu-id="a1fae-165">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="a1fae-166">Mike F Robbins heeft [een geweldig bericht over het](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) instellen van VSCode.</span><span class="sxs-lookup"><span data-stu-id="a1fae-166">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="a1fae-167">Meer informatie over Power shell is [een uitstekende schrijf bewerking voor het](https://www.learnpwsh.com/setup-vs-code-for-powershell/) ophalen van VSCode-instellingen voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="a1fae-167">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="a1fae-168">Meer instellingen</span><span class="sxs-lookup"><span data-stu-id="a1fae-168">More settings</span></span>

<span data-ttu-id="a1fae-169">Als u meer wilt weten over het maken van VSCode meer vertrouwd voor ISE-gebruikers, draagt u bij aan dit document. Als er een compatibiliteits configuratie is die u zoekt, maar u geen manier kunt vinden om deze in te scha kelen, [opent u een probleem](https://github.com/PowerShell/vscode-powershell/issues/new/choose) en vraagt u dit af.</span><span class="sxs-lookup"><span data-stu-id="a1fae-169">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="a1fae-170">We zijn altijd blij om pull en bijdragen ook te accepteren.</span><span class="sxs-lookup"><span data-stu-id="a1fae-170">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="a1fae-171">Tips voor VSCode</span><span class="sxs-lookup"><span data-stu-id="a1fae-171">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="a1fae-172">Opdracht palet</span><span class="sxs-lookup"><span data-stu-id="a1fae-172">Command Palette</span></span>

<span data-ttu-id="a1fae-173"><kbd>F1</kbd> OF <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>p</kbd> (<kbd>cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd> op macOS)</span><span class="sxs-lookup"><span data-stu-id="a1fae-173"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="a1fae-174">Een handige manier om opdrachten uit te voeren in VSCode.</span><span class="sxs-lookup"><span data-stu-id="a1fae-174">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="a1fae-175">Zie [de VSCode-documenten](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a1fae-175">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Opdracht palet]: #command-palette
[Command Palette]: #command-palette
