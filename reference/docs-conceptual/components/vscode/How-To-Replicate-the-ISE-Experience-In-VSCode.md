---
title: De ISE-ervaring in Visual Studio Code repliceren
description: De ISE-ervaring in Visual Studio Code repliceren
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687375"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>De ISE-ervaring in Visual Studio Code repliceren

Terwijl de PowerShell-extensie voor VSCode niet zoeken naar volledige functiepariteit met de PowerShell ISE, zijn er functies om de VSCode-ervaring voor gebruikers van de ISE natuurlijker maken.

Dit document probeert te lijstinstellingen die u in VSCode configureren kunt zodat de gebruiker iets meer vertrouwd in vergelijking met de ISE-ervaring.

## <a name="key-bindings"></a>Sleutel-bindingen

| Functie                              | ISE-Binding                  | VSCode-Binding                              |
| ----------------                      | -----------                  | --------------                              |
| Onderbreken en foutopsporingsprogramma opsplitsen          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Huidige regel/gemarkeerde tekst uitvoeren | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Lijst met beschikbare fragmenten               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Aangepaste sleutel-bindingen

U kunt [configureren van uw eigen sleutelbindingen](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) vscode ook.

## <a name="tab-completion"></a>Tab-aanvulling

Om in te schakelen meer ISE-achtige tab-aanvulling, deze instelling toevoegen:

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> Deze instelling is rechtstreeks naar VSCode (in plaats van in de uitbreiding) toegevoegd. Het gedrag ervan wordt bepaald door VSCode rechtstreeks en door de extensie kan niet worden gewijzigd.

## <a name="no-focus-on-console-when-executing"></a>Er is geen focus op de console bij het uitvoeren van

De focus in de editor houden wanneer u met <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

De standaardwaarde is `true` voor toegankelijkheid doeleinden.

## <a name="dont-start-integrated-console-on-startup"></a>Geïntegreerde console bij het opstarten niet starten

Als u wilt stoppen met de geïntegreerde console bij het opstarten, instellen:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> De achtergrond PowerShell-proces wordt nog steeds beginnen omdat die zorgt voor IntelliSense, script-analyse, symbool navigatie, enzovoort. Maar de console niet weergegeven.

## <a name="assume-files-are-powershell-by-default"></a>Wordt ervan uitgegaan dat standaard worden bestanden PowerShell

Als u wilt dat nieuwe/naamloos bestanden, registreren als PowerShell standaard:

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>Kleurenschema

Er zijn een aantal ISE thema's beschikbaar voor VSCode om de er veel meer, zoals de ISE-editor.

In de [Command Palette] type `theme` om op te halen `Preferences: Color Theme` en druk op <kbd>Enter</kbd>.
Selecteer in de vervolgkeuzelijst `PowerShell ISE`.

U kunt dit thema instellen in de instellingen met:

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>PowerShell-opdracht Explorer

Dankzij het werk van [ @corbob ](https://github.com/corbob), de PowerShell-extensie heeft het begin van een eigen explorer opdracht.

In de [Command Palette], voer `PowerShell Command Explorer` en druk op <kbd>Enter</kbd>.

## <a name="open-in-the-ise"></a>Open in de ISE

Als u uiteindelijk willen openen van een bestand in de ISE toch, kunt u <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Andere bronnen

- 4sysops heeft [een geweldige artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) over het configureren van VSCode om meer, zoals de ISE.
- Mike F Robbins heeft [een goede boeken](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) over het instellen van VSCode.
- Informatie over PowerShell heeft [een uitstekende schrijven van](https://www.learnpwsh.com/setup-vs-code-for-powershell/) instellen op het ophalen van VSCode voor PowerShell.

## <a name="more-settings"></a>Meer instellingen

Als u meer manieren om te maken van VSCode kunt u meer vertrouwd voor ISE-gebruikers weet, kunt u bijdragen aan dit document. Als er is een compatibiliteitsconfiguratie die u zoekt, maar u geen enkele manier om in te schakelen, vinden [opent u een probleem](https://github.com/PowerShell/vscode-powershell/issues/new/choose) en vragen!

We zijn altijd blij te accepteren van pull-aanvragen en ook bijdragen!

## <a name="vscode-tips"></a>VSCode Tips

### <a name="command-palette"></a>Command Palette

<kbd>F1</kbd> of <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> SHIFT</kbd>+<kbd>P</kbd> in macOS)

Een handige manier voor het uitvoeren van opdrachten vscode.
Zie voor meer informatie, [de documenten VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Command Palette]: #command-palette
