---
title: Visual Studio code for Power Shell Development gebruiken
description: Visual Studio code for Power Shell Development gebruiken
ms.date: 11/07/2019
ms.openlocfilehash: 5251094388f6abc7da7f2cc706537eade78df7c9
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978692"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Visual Studio code for Power Shell Development gebruiken

[Visual Studio code][vscode] is een platformoverschrijdende script editor van micro soft. Samen met de [Power shell-uitbrei ding][psext]beschikt u over een uitgebreide en interactieve script bewerkings ervaring, waardoor het eenvoudiger is om betrouw bare Power shell-scripts te schrijven. Visual Studio code met de Power shell-extensie is de aanbevolen editor voor het schrijven van Power shell-scripts.

Het ondersteunt de volgende Power shell-versies:

- Power shell 7 en up (Windows, macOS en Linux)
- Power shell Core 6 (Windows, macOS en Linux)
- Windows Power shell 5,1 (alleen Windows)

> [!NOTE]
> Visual Studio code is niet hetzelfde als [Visual Studio][].

## <a name="getting-started"></a>Aan de slag

Controleer voordat u begint of Power shell op het systeem bestaat. Raadpleeg de volgende koppelingen voor moderne werk belastingen op Windows, macOS en Linux:

- [Power Shell installeren in Linux][install-pscore-linux]
- [Power shell in macOS installeren][install-pscore-macos]
- [Power shell in Windows installeren][install-pscore-windows]

Zie [Windows Power Shell installeren][install-winps]voor traditionele workloads van Windows Power shell.

> [!IMPORTANT]
> De [Windows PowerShell ISE][ise] is nog steeds beschikbaar voor Windows. Het is echter niet langer in de ontwikkeling van actieve functies. De ISE werkt niet met Power shell 6 en hoger. Als onderdeel van Windows blijft het officieel worden ondersteund voor oplossingen voor beveiliging en onderhoud met hoge prioriteit.
> Er zijn geen plannen om de ISE van Windows te verwijderen.

## <a name="editing-with-visual-studio-code"></a>Bewerken met Visual Studio code

1. Installeer Visual Studio code. Zie voor meer informatie het overzicht instellen [van Visual Studio code][vsc-setup].

   Er zijn installatie-instructies voor elk platform:

   - **Windows**: Volg de installatie-instructies op de pagina [Visual Studio code uitvoeren op Windows][vsc-setup-win] .
   - **macOS**: Volg de installatie-instructies op de pagina [Visual Studio code uitvoeren op MacOS][vsc-setup-macOS] .
   - **Linux**: Volg de installatie-instructies op de pagina [Visual Studio code uitvoeren op Linux][vsc-setup-linux] .

1. Installeer de Power shell-extensie.

   1. Start de app Visual Studio code door `code` te typen in een-console of `code-insiders` als u Visual Studio code insiders hebt geïnstalleerd.
   1. Start **snel openen** in Windows of Linux door op <kbd>CTRL</kbd>+<kbd>P</kbd>te drukken. Druk in macOS op <kbd>Cmd</kbd>+<kbd>P</kbd>.
   1. Typ `ext install powershell` in snel openen en druk op **Enter**.
   1. De weer gave **extensies** wordt weer gegeven op de balk aan de zijkant. Selecteer de Power shell-extensie van micro soft.
      Er wordt een Visual Studio-code scherm weer gegeven dat vergelijkbaar is met de volgende afbeelding:

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. Klik op de knop **installeren** in de Power shell-extensie van micro soft.
   1. Als u na de installatie de knop **installeren** ziet, klikt u **op opnieuw** **laden**.
   1. Nadat Visual Studio code opnieuw is geladen, bent u klaar om te bewerken.

Als u bijvoorbeeld een nieuw bestand wilt maken, klikt u op **bestand > nieuw**. Als u deze wilt opslaan, klikt u op **bestand > opslaan** en geeft u een bestands naam op, zoals `HelloWorld.ps1`. Als u het bestand wilt sluiten, klikt u op de `X` naast de bestands naam. Als u Visual Studio code wilt afsluiten, wordt het **bestand > sluiten**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>De Power shell-uitbrei ding installeren op beperkte systemen

Sommige systemen zijn ingesteld om validatie van alle code handtekeningen te vereisen. De volgende fout kan optreden:

```
Language server startup failed.
```

Dit probleem kan optreden wanneer het uitvoerings beleid van Power shell is ingesteld door Windows groepsbeleid. Open een Power shell-prompt en voer de volgende opdracht uit om de Power shell editor-Services en de Power shell-extensie voor Visual Studio code hand matig goed te keuren:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

U wordt gevraagd of **u software van deze niet-vertrouwde uitgever wilt uitvoeren?** Typ `A` om het bestand uit te voeren. Open vervolgens Visual Studio code en controleer of de Power shell-extensie goed werkt. Als u nog steeds problemen ondervindt, laat het ons dan weten over [Problemen met GitHub][].

> [!NOTE]
> De Power shell-extensie voor Visual Studio code biedt geen ondersteuning voor uitvoering in een modus met beperkte taal. Zie [github issue #606][i606]voor meer informatie.

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Een versie van Power shell kiezen die moet worden gebruikt met de extensie

Met Power shell core die naast Windows Power shell wordt geïnstalleerd, is het nu mogelijk om een specifieke versie van Power shell te gebruiken met de Power shell-extensie. Deze functie bekijkt enkele bekende paden op verschillende besturings systemen voor het detecteren van installaties van Power shell.

Gebruik de volgende stappen om de versie te kiezen:

1. Open het **opdracht palet** in Windows of Linux met <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>. In macOS, gebruikt u <kbd>Cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>.
1. Zoek naar de **sessie**.
1. Klik op **Power shell: menu sessie weer geven**.
1. Kies de versie van Power shell die u wilt gebruiken in de lijst, bijvoorbeeld: **Power shell core**.

Als u Power shell hebt geïnstalleerd op een niet-typische locatie, wordt deze mogelijk niet eerst weer gegeven in het menu sessie. U kunt het menu sessie uitbreiden door [uw eigen aangepaste paden toe te voegen](#adding-your-own-powershell-paths-to-the-session-menu) , zoals hieronder wordt beschreven.

> [!NOTE]
> Het menu Power shell-sessie kan ook worden geopend vanuit het groene versie nummer in de rechter benedenhoek van de status balk. Als u op dit versie nummer klikt, wordt het menu sessie geopend.

## <a name="configuration-settings-for-visual-studio-code"></a>Configuratie-instellingen voor Visual Studio code

Als u niet bekend bent met het wijzigen van instellingen in Visual Studio code, raden we u aan [de documentatie van de Visual Studio code-instellingen][vsc-settings] te lezen.

Nadat u de documentatie hebt gelezen, kunt u configuratie-instellingen toevoegen in `settings.json`.

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Als u niet wilt dat deze instellingen van invloed zijn op alle bestands typen, kunt u met Visual Studio code ook configuraties per taal instellen. Maak een taalspecifieke instelling door instellingen in een `[<language-name>]` veld in te voeren. Bijvoorbeeld:

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> Zie [informatie over bestands codering][file-encoding]voor meer informatie over het coderen van bestanden in Visual Studio code.
>
> Lees ook [hoe u de ISE-ervaring in Visual Studio code repliceert][vsc-ise] voor andere tips over het configureren van Visual Studio code voor het bewerken van Power shell.

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Uw eigen Power shell-paden toevoegen aan het menu sessie

U kunt andere uitvoer bare Power shell-paden toevoegen aan het menu sessie via de [code-instelling van Visual Studio](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.

Voeg een item toe aan de lijst `powershell.powerShellAdditionalExePaths` of maak een lijst als deze niet bestaat in uw `settings.json`:

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

Elk item moet het volgende bevatten:

- `exePath`: het pad naar de `pwsh` of `powershell` uitvoer bare bestand.
- `versionName`: de tekst die wordt weer gegeven in het menu van de sessie.

Als u de standaard versie van Power shell wilt instellen, stelt u de waarde `powershell.powerShellDefaultVersion` in op de tekst die wordt weer gegeven in het menu sessie (ook wel bekend als de `versionName`):

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

Nadat u deze instelling hebt geconfigureerd, start u Visual Studio code opnieuw of laadt u het huidige venster Visual Studio-code opnieuw vanuit het **opdracht palet**, typt u **ontwikkelaar: venster opnieuw laden**.

Als u het menu sessie opent, ziet u nu uw extra Power shell-versies!

> [!NOTE]
> Als u Power shell bouwt vanaf een bron, is dit een fantastische manier om uw lokale build van Power shell te testen.

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a>Een oudere versie van de Power shell-uitbrei ding voor Windows Power Shell v3 en v4 gebruiken

De huidige Power shell-extensie biedt geen ondersteuning voor [Power Shell v3 en v4][i1310]. U kunt echter de laatste versie van de uitbrei ding gebruiken die Power Shell v3 en v4 ondersteunt.

> [!CAUTION]
> Er zijn geen aanvullende oplossingen voor deze oudere versie van de uitbrei ding. Het wordt weer gegeven als IS, maar is beschikbaar voor u als u nog steeds Windows Power Shell v3 en Windows Power shell v4 gebruikt.

Open eerst het deel venster uitbrei ding en zoek naar `PowerShell`. Klik vervolgens op het vistuig en selecteer **een andere versie installeren...** .

![Een andere versie installeren...](media/using-vscode/install-another-version.png)

Selecteer vervolgens de **2020.1.0** -versie. Deze versie van de uitbrei ding is de laatste versie voor de ondersteuning van v3 en v4. Zorg ervoor dat u de volgende instelling toevoegt zodat uw extensie versie niet automatisch wordt bijgewerkt:

```json
{
    "extensions.autoUpdate": false
}
```

Versie **2020.1.0** werkt voor de nabije toekomst. Visual Studio code kan echter een wijziging implementeren die deze versie van de uitbrei ding verbreekt. Daarom wordt u aangeraden het volgende te doen en geen ondersteuning te bieden:

- Upgraden naar Windows Power shell 5,1
- Power shell 7 installeren, een side-by-side installatie van Windows Power shell en werkt het beste met de Power shell-extensie

## <a name="debugging-with-visual-studio-code"></a>Fout opsporing met Visual Studio code

### <a name="no-workspace-debugging"></a>Geen-werk ruimte: fout opsporing

In Visual Studio code versie 1,9 (of hoger) kunt u fouten opsporen in Power shell-scripts zonder de map met het Power shell-script te openen.

1. Open het Power shell-script bestand met het **bestand > bestand openen...**
1. Een onderbrekings punt instellen: Selecteer een regel en druk vervolgens op <kbd>F9</kbd>
1. Druk op <kbd>F5</kbd> om de fout opsporing te starten

Het deel venster acties voor fout opsporing wordt weer gegeven, waarin u de fout opsporing kunt opdelen, stap, CV en stoppen.

### <a name="workspace-debugging"></a>Fout opsporing voor werk ruimten

Fout opsporing in werk ruimte verwijst naar fout opsporing in de context van een map die u hebt geopend vanuit het menu **bestand** met **open map...** . De map die u opent, is doorgaans uw Power shell-projectmap of de hoofdmap van uw Git-opslag plaats. Met fout opsporing voor werk ruimten kunt u meerdere debug-configuraties definiëren, anders dan alleen fouten opsporen in het bestand dat momenteel is geopend.

Voer de volgende stappen uit om een configuratie bestand voor fout opsporing te maken:

1. Open de weer gave **fout opsporing** op Windows of Linux door op <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>te drukken. Druk in macOS op <kbd>Cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>.
1. Klik op de koppeling **een launch. JSON-bestand maken** .
1. Kies **Power shell**in het venster **omgeving selecteren** .
1. Kies het type fout opsporing dat u wilt gebruiken:

   - Het **huidige bestand starten** -starten en fouten opsporen in het bestand in het huidige venster van de editor
   - **Script starten** : starten en fouten opsporen in opgegeven bestand of opdracht
   - **Interactieve sessie** -opdrachten voor fout opsporing in de geïntegreerde console
   - Het fout **opsporingsprogramma koppelen aan** een actief Power shell-hostproces

Met Visual Studio code maakt u een map en een bestand `.vscode\launch.json` in de hoofdmap van de map werk ruimte om de configuratie van fout opsporing op te slaan. Als uw bestanden zich in een Git-opslag plaats bevinden, wilt u meestal het `launch.json` bestand door voeren. De inhoud van het `launch.json` bestand zijn:

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

Dit bestand vertegenwoordigt de veelvoorkomende scenario's voor fout opsporing. Wanneer u dit bestand in de editor opent, ziet u een knop **Configuratie toevoegen...** . U kunt op deze knop klikken om meer configuratie van Power Shell-fout opsporing toe te voegen. Een van de handig te toevoegen configuratie is **Power shell: script starten**. Met deze configuratie kunt u een bestand opgeven dat optionele argumenten bevat die worden gebruikt wanneer u op <kbd>F5</kbd> drukt, ongeacht welk bestand in de Editor actief is.

Nadat de configuratie van de fout opsporing is ingesteld, kunt u selecteren welke configuratie u tijdens een foutopsporingssessie wilt gebruiken. Selecteer een configuratie in de vervolg keuzelijst debug Configuration in de werk balk van de weer gave van de **fout opsporing** .

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a>Problemen met de Power shell-extensie voor Visual Studio code oplossen

Als u problemen ondervindt met het gebruik van Visual Studio code voor het ontwikkelen van Power shell-scripts, raadpleegt u de [gids voor probleem oplossing][troubleshooting] op github.

## <a name="useful-resources"></a>Nuttige informatie

Er zijn enkele Video's en blog berichten die handig kunnen zijn om aan de slag te gaan met behulp van de Power shell-extensie voor Visual Studio code:

### <a name="videos"></a>Video's

- [Visual Studio code gebruiken als uw standaard Power shell-editor](https://youtu.be/bGn45vIeAMM)
- [Visual Studio code: dieper in fout opsporing voor uw Power shell-scripts](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a>Blogberichten

- [Power shell-uitbrei ding][pscdn]
- [Power shell-scripts schrijven en fouten opsporen in Visual Studio code][debug]
- [Fout opsporing van Visual Studio code guidance][psdbgblog]
- [Fout opsporing in Power shell in Visual Studio code][psdbg-gh]
- [Aan de slag met Power shell-ontwikkeling in Visual Studio code][getting-started]
- [Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 1][editing-part1]
- [Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 2][editing-part2]
- [Fout opsporing voor Power shell-script in Visual Studio code – deel 1][debugging-part1]
- [Fout opsporing voor Power shell-script in Visual Studio code – deel 2][debugging-part2]

## <a name="powershell-extension-project-source-code"></a>Bron code van Power shell-extensie project

De bron code van de Power shell-extensie vindt u op [github][psext-src].

Als u geïnteresseerd bent in bijdragen, worden pull-aanvragen aanzienlijk gewaardeerd. Volg samen met de [documentatie voor ontwikkel aars][dev-docs] op github om aan de slag te gaan.

<!-- related articles -->
[ise]:                    ../ise/Introducing-the-Windows-PowerShell-ISE.md
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
