---
title: De ISE-ervaring in Visual Studio Code repliceren
description: De ISE-ervaring in Visual Studio Code repliceren
ms.date: 08/06/2018
ms.openlocfilehash: 899e1c393fd49b0659631b88d610e80ec885e69e
ms.sourcegitcommit: bda70d2163eef5a158441cb1c38ac422d704535d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/10/2020
ms.locfileid: "81005598"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>De ISE-ervaring in Visual Studio Code repliceren

Hoewel met de Power shell-extensie voor VS code niet wordt gezocht naar de functie pariteit met de Power shell-ISE, zijn er functies die ervoor zorgen dat de VS code natuurlijk meer natuurlijke is voor gebruikers van de ISE.

In dit document wordt geprobeerd een lijst te maken met de instellingen die u kunt configureren in VS code, zodat de gebruiker meer vertrouwd is vergeleken met de ISE.

## <a name="ise-mode"></a>ISE-modus

> [!NOTE]
> Deze functie is beschikbaar in de Power shell preview-uitbrei ding sinds versie 2019.12.0 en in de Power shell-uitbrei ding sinds versie 2020.3.0.

De eenvoudigste manier om de ISE-ervaring in Visual Studio code te repliceren, is door ' ISE-modus ' in te scha kelen.
Hiertoe opent u het opdracht palet (<kbd>F1</kbd> of <kbd>Ctrl</kbd>+<kbd>shift</kbd>+<kbd>p</kbd> of <kbd>cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>p</kbd> op macOS) en typt u ' ISE-modus '. Selecteer Power shell: ISE-modus inschakelen in de lijst.

Met deze opdracht worden de instellingen die onder het resultaat worden beschreven, automatisch toegepast op de volgende manier:

![ISE-modus](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a>Configuratie-instellingen voor ISE-modus

Met de ISE-modus worden de volgende wijzigingen aangebracht in VS-code-instellingen.

- Sleutel bindingen

  |               Functie                |         ISE-binding          |              VS-code binding                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | Fout opsporing onderbreken en verbreken          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
  | Huidige regel/gemarkeerde tekst uitvoeren | <kbd>Drukken</kbd>                | <kbd>Drukken</kbd>                               |
  | Beschik bare fragmenten weer geven               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

  > [!NOTE]
  > U kunt ook [uw eigen sleutel bindingen configureren](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VS code.

- Vereenvoudigde ISE-achtige gebruikers interface

  Als u de gebruikers interface van Visual Studio wilt vereenvoudigen om nauw keuriger te kijken naar de gebruikers interface van de ISE, moet u deze twee instellingen Toep assen:

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  Deze instellingen verbergen de ' activiteiten balk ' en de sectie ' fout opsporen van zijkant ' in het rode vak hieronder weer gegeven:

  ![de gemarkeerde sectie bevat de activiteiten balk en de fout balk aan de zijkant](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  Het eind resultaat ziet er als volgt uit:

  ![Vereenvoudigde weer gave van VS code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- Tabblad voltooiing

  Als u meer ISE wilt inschakelen, voegt u deze instelling toe:

  ```json
  "editor.tabCompletion": "on",
  ```

- Geen focus op console bij het uitvoeren van

  Als u de focus in de editor wilt houden wanneer u uitvoert met <kbd>F8</kbd>:

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  De standaard waarde is `true` voor toegankelijkheids doeleinden.

- Geïntegreerde console niet starten bij opstarten

  Als u de geïntegreerde console tijdens het opstarten wilt stoppen, stelt u het volgende in:

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > Het Power Shell-proces voor de achtergrond begint nog steeds IntelliSense, script analyse, navigatie naar symbolen, enzovoort, maar de console wordt niet weer gegeven.

- Aannemen dat bestanden standaard Power shell zijn

  Als u nieuwe/naamloze bestanden wilt maken, moet u zich standaard als Power shell registreren:

  ```json
  "files.defaultLanguage": "powershell",
  ```

- Kleuren schema

  Er zijn een aantal ISE-Thema's beschikbaar voor VS code om ervoor te zorgen dat de editor er veel meer uitziet als de ISE.

  Typ in het [opdracht palet][] `theme` om `Preferences: Color Theme` op te halen en druk op <kbd>Enter</kbd>. Selecteer `PowerShell ISE`in de vervolg keuzelijst.

  U kunt dit thema instellen in de instellingen met:

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- Power shell-opdracht Verkenner

  Dankzij het werk van [@corbob](https://github.com/corbob)heeft de Power shell-uitbrei ding het begin van een eigen opdracht Verkenner.

  Voer in het [opdracht palet][]`PowerShell Command Explorer` in en druk op <kbd>Enter</kbd>.

- Open in de ISE

  Als u een bestand in de Windows PowerShell ISE toch wilt openen, opent u het [opdracht palet][], zoekt u naar ' openen in ISE ' en selecteert u vervolgens **Power shell: huidig bestand openen in Power shell ISE**.

## <a name="other-resources"></a>Meer informatie

- 4sysops heeft [een geweldig artikel][4sysops] over het configureren van VS code zodat deze meer lijkt op het ISE.
- Mike F Robbins heeft [een geweldig bericht over het][mikefrobbins] instellen van VS code.
- Meer informatie over Power shell vindt [u in een uitstekende][learnpwsh] installatie voor schrijven voor Power shell.

## <a name="vs-code-tips"></a>VS-code tips

- Opdracht palet

  Het opdracht palet is een handige manier om opdrachten in VS code uit te voeren. Open het opdracht palet met <kbd>F1</kbd> of <kbd>Ctrl</kbd>+<kbd>shift</kbd>+<kbd>p</kbd> of <kbd>cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>p</kbd> op macOS.

  Raadpleeg [de VS code-documentatie][vsc-docs]voor meer informatie.

- De console fout opsporing uitschakelen

  Als u alleen van plan bent om gebruik te maken van VS code voor Power shell-scripts, kunt u de **console voor fout opsporing** verbergen omdat deze niet wordt gebruikt door de Power shell-extensie. Hiertoe klikt u met de rechter muisknop op **debug-console** en klikt u vervolgens op het vinkje om het te verbergen.

## <a name="more-settings"></a>Meer instellingen

Als u meer wilt weten over de verschillende manieren om de code van ISE-gebruikers beter te maken, kunt u het beste een bijdrage leveren aan dit document. Als er een compatibiliteits configuratie is die u zoekt, maar u geen manier kunt vinden om deze in te scha kelen, [opent u een probleem][] en vraagt u dit af.

We zijn altijd blij om pull en bijdragen ook te accepteren.

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[Opdracht palet]: #vs-code-tips
[opent u een probleem]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
