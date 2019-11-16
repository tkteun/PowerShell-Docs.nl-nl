---
title: De ISE-ervaring in Visual Studio Code repliceren
description: De ISE-ervaring in Visual Studio Code repliceren
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117474"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>De ISE-ervaring in Visual Studio Code repliceren

Hoewel de Power shell-extensie voor VSCode niet de functie pariteit van de Power shell-ISE doorzoekt, zijn er functies aanwezig waarmee de VSCode-ervaring natuurlijker wordt voor gebruikers van de ISE.

In dit document wordt geprobeerd een lijst te maken met de instellingen die u kunt configureren in VSCode, zodat de gebruiker een beetje bekender is vergeleken met de ISE.

## <a name="key-bindings"></a>Sleutel bindingen

| Functie                              | ISE-binding                  | VSCode-binding                              |
| ----------------                      | -----------                  | --------------                              |
| Fout opsporing onderbreken en verbreken          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Huidige regel/gemarkeerde tekst uitvoeren | <kbd>Drukken</kbd>                | <kbd>Drukken</kbd>                               |
| Beschik bare fragmenten weer geven               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Aangepaste sleutel bindingen

U kunt ook [uw eigen sleutel bindingen configureren](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode.

## <a name="simplified-ise-like-ui"></a>Vereenvoudigde ISE-achtige gebruikers interface

Als u de gebruikers interface van Visual Studio wilt vereenvoudigen om nauw keuriger te kijken naar de gebruikers interface van de ISE, moet u deze twee instellingen Toep assen:

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

Hiermee worden de volgende secties in het vak rood weer gegeven: ' activiteiten balk ' en ' balk voor fout opsporing.

![de gemarkeerde sectie bevat de activiteiten balk en de fout balk aan de zijkant](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

Het eind resultaat ziet er als volgt uit:

![Vereenvoudigde weer gave van VS code](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>Tabblad voltooiing

Als u meer ISE wilt inschakelen, voegt u deze instelling toe:

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> Deze instelling is rechtstreeks aan VSCode toegevoegd (in plaats van in de extensie). Het gedrag wordt rechtstreeks door VSCode bepaald en kan niet worden gewijzigd door de extensie.

## <a name="no-focus-on-console-when-executing"></a>Geen focus op console bij het uitvoeren van

Als u de focus in de editor wilt houden wanneer u uitvoert met <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

De standaard waarde is `true` voor toegankelijkheids doeleinden.

## <a name="dont-start-integrated-console-on-startup"></a>Geïntegreerde console niet starten bij opstarten

Als u de geïntegreerde console tijdens het opstarten wilt stoppen, stelt u het volgende in:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> Het Power Shell-proces op de achtergrond wordt nog steeds gestart, omdat IntelliSense, script analyse, navigatie naar symbolen, enzovoort. Maar de console wordt niet weer gegeven.

## <a name="assume-files-are-powershell-by-default"></a>Aannemen dat bestanden standaard Power shell zijn

Als u nieuwe/naamloze bestanden wilt maken, moet u zich standaard als Power shell registreren:

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a>Kleuren schema

Er zijn een aantal ISE-Thema's beschikbaar voor VSCode, waardoor de editor veel meer lijkt op de ISE.

Typ in het [opdracht palet] `theme` om `Preferences: Color Theme` op te halen en druk op <kbd>Enter</kbd>.
Selecteer `PowerShell ISE`in de vervolg keuzelijst.

U kunt dit thema instellen in de instellingen met:

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a>Power shell-opdracht Verkenner

Dankzij het werk van [@corbob](https://github.com/corbob)heeft de Power shell-uitbrei ding het begin van een eigen opdracht Verkenner.

Voer in het [opdracht palet]`PowerShell Command Explorer` in en druk op <kbd>Enter</kbd>.

## <a name="open-in-the-ise"></a>Open in de ISE

Als u uiteindelijk wilt dat een bestand in de ISE toch opent, kunt u <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>gebruiken.

## <a name="other-resources"></a>Andere resources

- 4sysops heeft [een geweldig artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) over het configureren van VSCode als de ISE.
- Mike F Robbins heeft [een geweldig bericht over het](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) instellen van VSCode.
- Meer informatie over Power shell is [een uitstekende schrijf bewerking voor het](https://www.learnpwsh.com/setup-vs-code-for-powershell/) ophalen van VSCode-instellingen voor Power shell.

## <a name="more-settings"></a>Meer instellingen

Als u meer wilt weten over het maken van VSCode meer vertrouwd voor ISE-gebruikers, draagt u bij aan dit document. Als er een compatibiliteits configuratie is die u zoekt, maar u geen manier kunt vinden om deze in te scha kelen, [opent u een probleem](https://github.com/PowerShell/vscode-powershell/issues/new/choose) en vraagt u dit af.

We zijn altijd blij om pull en bijdragen ook te accepteren.

## <a name="vscode-tips"></a>Tips voor VSCode

### <a name="command-palette"></a>Opdracht palet

<kbd>F1</kbd> OF <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>p</kbd> (<kbd>cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd> op macOS)

Een handige manier om opdrachten uit te voeren in VSCode.
Zie [de VSCode-documenten](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)voor meer informatie.

[Opdracht palet]: #command-palette
