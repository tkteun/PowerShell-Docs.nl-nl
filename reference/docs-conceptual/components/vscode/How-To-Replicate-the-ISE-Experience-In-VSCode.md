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
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>De ISE-ervaring in Visual Studio Code repliceren

Hoewel de Power shell-extensie voor VSCode niet de functie pariteit van de Power shell-ISE doorzoekt, zijn er functies aanwezig waarmee de VSCode-ervaring natuurlijker wordt voor gebruikers van de ISE.

In dit document wordt geprobeerd een lijst te maken met de instellingen die u kunt configureren in VSCode, zodat de gebruiker een beetje bekender is vergeleken met de ISE.

## <a name="ise-mode"></a>ISE-modus

> [!NOTE]
> Deze functie is beschikbaar in de Power shell preview-uitbrei ding sinds versie 2019.12.0 en in de Power shell-uitbrei ding sinds versie 2020.3.0.

De eenvoudigste manier om de ISE-ervaring in Visual Studio code te repliceren, is door ' ISE-modus ' in te scha kelen.
Hiervoor opent u de opdracht pallet (<kbd>F1</kbd> of <kbd>Ctrl</kbd>+<kbd>shift</kbd>+<kbd>p</kbd> of <kbd>cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>p</kbd> op macOS) en typt u ' ISE-modus '.
Selecteer Power shell: ISE-modus inschakelen in de lijst.

Met deze opdracht worden automatisch veel instellingen toegepast die in dit document worden gevonden.
Het resultaat ziet er als volgt uit:

![ISE-modus](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

De rest van dit artikel bevat gedetailleerde informatie over de instellingen in de ISE-modus en enkele aanvullende instellingen.

## <a name="key-bindings"></a>Sleutel bindingen

| Function                              | ISE-binding                  | VSCode-binding                              |
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

> [!NOTE]
> Deze instellingen zijn opgenomen in de [' ISE-modus '](#ise-mode).

Hiermee worden de volgende secties in het vak rood weer gegeven: ' activiteiten balk ' en ' balk voor fout opsporing.

![de gemarkeerde sectie bevat de activiteiten balk en de fout balk aan de zijkant](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

Het eind resultaat ziet er als volgt uit:

![Vereenvoudigde weer gave van VS code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>Tabblad voltooiing

Als u meer ISE wilt inschakelen, voegt u deze instelling toe:

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> Deze instelling is rechtstreeks aan VSCode toegevoegd (in plaats van in de extensie). Het gedrag wordt rechtstreeks door VSCode bepaald en kan niet worden gewijzigd door de extensie.

> [!NOTE]
> Deze instelling is opgenomen in de [ISE-modus](#ise-mode).

## <a name="no-focus-on-console-when-executing"></a>Geen focus op console bij het uitvoeren van

Als u de focus in de editor wilt houden wanneer u uitvoert met <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> Deze instelling is opgenomen in de [ISE-modus](#ise-mode).

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

> [!NOTE]
> Deze instelling is opgenomen in de [ISE-modus](#ise-mode).

## <a name="color-scheme"></a>Kleuren schema

Er zijn een aantal ISE-Thema's beschikbaar voor VSCode, waardoor de editor veel meer lijkt op de ISE.

Typ in het [opdracht palet] `theme` om `Preferences: Color Theme` op te halen en druk op <kbd>Enter</kbd>.
Selecteer `PowerShell ISE`in de vervolg keuzelijst.

U kunt dit thema instellen in de instellingen met:

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> Deze instelling is opgenomen in de [ISE-modus](#ise-mode).

## <a name="powershell-command-explorer"></a>Power shell-opdracht Verkenner

Dankzij het werk van [@corbob](https://github.com/corbob)heeft de Power shell-uitbrei ding het begin van een eigen opdracht Verkenner.

Voer in het [opdracht palet]`PowerShell Command Explorer` in en druk op <kbd>Enter</kbd>.

> [!NOTE]
> Dit wordt automatisch weer gegeven in de [' ISE-modus '](#ise-mode).

## <a name="open-in-the-ise"></a>Open in de ISE

Als u uiteindelijk wilt dat een bestand in de ISE toch opent, kunt u <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>gebruiken.

## <a name="other-resources"></a>Meer informatie

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
