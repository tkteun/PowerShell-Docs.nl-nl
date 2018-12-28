---
title: Het repliceren van de ISE-ervaring in Visual Studio Code
description: Het repliceren van de ISE-ervaring in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 0ac38985a842a0dfc6118d0ae7116d12e1579daf
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655508"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="97a19-103">Het repliceren van de ISE-ervaring in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="97a19-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="97a19-104">Terwijl de PowerShell-extensie voor VSCode niet zoeken naar volledige functiepariteit met de PowerShell ISE, zijn er functies om de VSCode-ervaring voor gebruikers van de ISE natuurlijker maken.</span><span class="sxs-lookup"><span data-stu-id="97a19-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="97a19-105">Dit document probeert te lijstinstellingen die u in VSCode configureren kunt zodat de gebruiker iets meer vertrouwd in vergelijking met de ISE-ervaring.</span><span class="sxs-lookup"><span data-stu-id="97a19-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="97a19-106">Sleutel-bindingen</span><span class="sxs-lookup"><span data-stu-id="97a19-106">Key bindings</span></span>

| <span data-ttu-id="97a19-107">Functie</span><span class="sxs-lookup"><span data-stu-id="97a19-107">Function</span></span>                              | <span data-ttu-id="97a19-108">ISE-Binding</span><span class="sxs-lookup"><span data-stu-id="97a19-108">ISE Binding</span></span>                  | <span data-ttu-id="97a19-109">VSCode-Binding</span><span class="sxs-lookup"><span data-stu-id="97a19-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="97a19-110">Onderbreken en foutopsporingsprogramma opsplitsen</span><span class="sxs-lookup"><span data-stu-id="97a19-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="97a19-111"><kbd>CTRL</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="97a19-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="97a19-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="97a19-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="97a19-113">Huidige regel/gemarkeerde tekst uitvoeren</span><span class="sxs-lookup"><span data-stu-id="97a19-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="97a19-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="97a19-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="97a19-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="97a19-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="97a19-116">Lijst met beschikbare fragmenten</span><span class="sxs-lookup"><span data-stu-id="97a19-116">List available snippets</span></span>               | <span data-ttu-id="97a19-117"><kbd>CTRL</kbd>+<kbd>"j"</kbd></span><span class="sxs-lookup"><span data-stu-id="97a19-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="97a19-118"><kbd>CTRL</kbd>+<kbd>Alt</kbd>+<kbd>"j"</kbd></span><span class="sxs-lookup"><span data-stu-id="97a19-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="97a19-119">Aangepaste sleutel-bindingen</span><span class="sxs-lookup"><span data-stu-id="97a19-119">Custom Key bindings</span></span>

<span data-ttu-id="97a19-120">U kunt [configureren van uw eigen sleutelbindingen](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) vscode ook.</span><span class="sxs-lookup"><span data-stu-id="97a19-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="97a19-121">Tab-aanvulling</span><span class="sxs-lookup"><span data-stu-id="97a19-121">Tab completion</span></span>

<span data-ttu-id="97a19-122">Om in te schakelen meer ISE-achtige tab-aanvulling, deze instelling toevoegen:</span><span class="sxs-lookup"><span data-stu-id="97a19-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="97a19-123">Deze instelling is rechtstreeks naar VSCode (in plaats van in de uitbreiding) toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="97a19-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="97a19-124">Het gedrag ervan wordt bepaald door VSCode rechtstreeks en door de extensie kan niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="97a19-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="97a19-125">Er is geen focus op de console bij het uitvoeren van</span><span class="sxs-lookup"><span data-stu-id="97a19-125">No focus on console when executing</span></span>

<span data-ttu-id="97a19-126">De focus in de editor houden wanneer u met <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="97a19-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="97a19-127">De standaardwaarde is `true` voor toegankelijkheid doeleinden.</span><span class="sxs-lookup"><span data-stu-id="97a19-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="97a19-128">Geïntegreerde console bij het opstarten niet starten</span><span class="sxs-lookup"><span data-stu-id="97a19-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="97a19-129">Als u wilt stoppen met de geïntegreerde console bij het opstarten, instellen:</span><span class="sxs-lookup"><span data-stu-id="97a19-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="97a19-130">De achtergrond PowerShell-proces wordt nog steeds beginnen omdat dat intellisense, script-analyse, symbool navigatie, enzovoort biedt. Maar de console niet weergegeven.</span><span class="sxs-lookup"><span data-stu-id="97a19-130">The background PowerShell process will still start since that provides intellisense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="97a19-131">Wordt ervan uitgegaan dat standaard worden bestanden PowerShell</span><span class="sxs-lookup"><span data-stu-id="97a19-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="97a19-132">Als u wilt dat nieuwe/naamloos bestanden, registreren als PowerShell standaard:</span><span class="sxs-lookup"><span data-stu-id="97a19-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="97a19-133">Kleurenschema</span><span class="sxs-lookup"><span data-stu-id="97a19-133">Color scheme</span></span>

<span data-ttu-id="97a19-134">Er zijn een aantal ISE thema's beschikbaar voor VSCode om de er veel meer, zoals de ISE-editor.</span><span class="sxs-lookup"><span data-stu-id="97a19-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="97a19-135">In de [Command Palette] type `theme` om op te halen `Preferences: Color Theme` en druk op <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="97a19-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="97a19-136">Selecteer in de vervolgkeuzelijst `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="97a19-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="97a19-137">U kunt dit thema instellen in de instellingen met:</span><span class="sxs-lookup"><span data-stu-id="97a19-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="97a19-138">PowerShell-opdracht Explorer</span><span class="sxs-lookup"><span data-stu-id="97a19-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="97a19-139">Dankzij het werk van [ @corbob ](https://github.com/corbob), de PowerShell-extensie heeft het begin van een eigen explorer opdracht.</span><span class="sxs-lookup"><span data-stu-id="97a19-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="97a19-140">In de [Command Palette], voer `PowerShell Command Explorer` en druk op <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="97a19-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="97a19-141">Open in de ISE</span><span class="sxs-lookup"><span data-stu-id="97a19-141">Open in the ISE</span></span>

<span data-ttu-id="97a19-142">Als u uiteindelijk willen openen van een bestand in de ISE toch, kunt u <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="97a19-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="97a19-143">Andere bronnen</span><span class="sxs-lookup"><span data-stu-id="97a19-143">Other resources</span></span>

- <span data-ttu-id="97a19-144">4sysops heeft [een geweldige artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) over het configureren van VSCode om meer, zoals de ISE.</span><span class="sxs-lookup"><span data-stu-id="97a19-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="97a19-145">Mike F Robbins heeft [een goede boeken](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) over het instellen van VSCode.</span><span class="sxs-lookup"><span data-stu-id="97a19-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="97a19-146">Informatie over PowerShell heeft [een uitstekende schrijven van](https://www.learnpwsh.com/setup-vs-code-for-powershell/) instellen op het ophalen van VSCode voor PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97a19-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="97a19-147">Meer instellingen</span><span class="sxs-lookup"><span data-stu-id="97a19-147">More settings</span></span>

<span data-ttu-id="97a19-148">Als u meer manieren om te maken van VSCode kunt u meer vertrouwd voor ISE-gebruikers weet, kunt u bijdragen aan dit document. Als er is een compatibiliteitsconfiguratie die u zoekt, maar u geen enkele manier om in te schakelen, vinden [opent u een probleem](https://github.com/PowerShell/vscode-powershell/issues/new/choose) en vragen!</span><span class="sxs-lookup"><span data-stu-id="97a19-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="97a19-149">We zijn altijd blij te accepteren van pull-aanvragen en ook bijdragen!</span><span class="sxs-lookup"><span data-stu-id="97a19-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="97a19-150">Tips voor VSCode</span><span class="sxs-lookup"><span data-stu-id="97a19-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="97a19-151">Command Palette</span><span class="sxs-lookup"><span data-stu-id="97a19-151">Command Palette</span></span>

<span data-ttu-id="97a19-152"><kbd>F1</kbd> of <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> SHIFT</kbd>+<kbd>P</kbd> in macOS)</span><span class="sxs-lookup"><span data-stu-id="97a19-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="97a19-153">Een handige manier voor het uitvoeren van opdrachten vscode.</span><span class="sxs-lookup"><span data-stu-id="97a19-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="97a19-154">Zie voor meer informatie, [de documenten VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="97a19-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Command Palette]: #command-palette
