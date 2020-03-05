---
title: Visual Studio code for Power Shell Development gebruiken
description: Visual Studio code for Power Shell Development gebruiken
ms.date: 11/07/2019
ms.openlocfilehash: 16ae228c0d169261b783366a730fd2d5d77d32d6
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279062"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Visual Studio code for Power Shell Development gebruiken

Naast [Power shell ISE][ise]is Power shell ook goed ondersteund in Visual Studio code (VSCode). De ISE wordt niet ondersteund met Power shell core, maar VSCode wordt ondersteund voor Power shell Core op alle platforms: Windows, macOS en Linux.

U kunt VSCode in Windows met Power shell versie 5 gebruiken met behulp van Windows 10 of door Windows Management Framework 5,1 te installeren voor down level Windows OSs, zoals Windows 8,1. Zie [WMF 5,1 installeren en configureren](/powershell/scripting/wmf/setup/install-configure)voor meer informatie.

Controleer voordat u begint of Power shell op het systeem bestaat. Raadpleeg de volgende koppelingen voor moderne werk belastingen op Windows, macOS en Linux:

- [Installing PowerShell Core on Linux][install-pscore-linux] (PowerShell Core installeren in Linux)
- [Installing PowerShell Core on macOS][install-pscore-macos] (PowerShell Core installeren in macOS)
- [Power shell Core installeren in Windows][install-pscore-windows]

Zie [Windows Power Shell installeren][install-winps]voor traditionele workloads van Windows Power shell.

## <a name="editing-with-vscode"></a>Bewerken met VSCode

1. Installeer VSCode. Zie voor meer informatie het overzicht instellen [van Visual Studio code](https://code.visualstudio.com/Docs/setup/setup-overview).

   Er zijn installatie-instructies voor elk platform:

   - **Linux**: Volg de installatie-instructies op de pagina [actieve VSCode op Linux](https://code.visualstudio.com/docs/setup/linux) .
   - **macOS**: Volg de installatie-instructies op de pagina [actieve VSCode op macOS](https://code.visualstudio.com/docs/setup/mac) .

     > [!IMPORTANT]
     > Bij macOS moet u OpenSSL installeren om de Power shell-extensie correct te laten werken. De eenvoudigste manier om dit te doen is door [homebrew](https://brew.sh/) te installeren en vervolgens `brew install openssl`uit te voeren. VSCode kan nu de Power shell-uitbrei ding laden.

   - **Windows**: Volg de installatie-instructies op de pagina [actieve VSCode op Windows](https://code.visualstudio.com/docs/setup/windows) .

1. Installeer de Power shell-extensie.

   1. Start de VSCode-app op:
      - **Windows**: `code` in uw Power shell-sessie typen
      - **Linux**: `code` in uw terminal typen
      - **macOS**: `code` in uw terminal typen
   1. Start **snel openen** in Windows of Linux door op <kbd>CTRL</kbd>+<kbd>P</kbd>te drukken. Druk in macOS op <kbd>Cmd</kbd>+<kbd>P</kbd>.
   1. Typ `ext install powershell` in snel openen en druk op **Enter**.
   1. De weer gave **extensies** wordt weer gegeven op de balk aan de zijkant. Selecteer de Power shell-extensie van micro soft.
      Er wordt een VSCode-scherm weer gegeven dat vergelijkbaar is met de volgende afbeelding:

      ![VSCode](media/using-vscode/vscode.png)

   1. Klik op de knop **installeren** in de Power shell-extensie van micro soft.
   1. Na de installatie ziet u de knop **installeren** om opnieuw te **laden**. Klik op **opnieuw laden**.
   1. Nadat VSCode opnieuw is geladen, bent u klaar om te bewerken.

Als u bijvoorbeeld een nieuw bestand wilt maken, klikt u op **bestand > nieuw**. Als u deze wilt opslaan, klikt u op **bestand > opslaan** en geeft u een bestands naam op, zoals `HelloWorld.ps1`. Als u het bestand wilt sluiten, klikt u op de `X` naast de bestands naam. **Bestand >** afsluiten om VSCode af te sluiten.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>De Power shell-uitbrei ding installeren op beperkte systemen

Sommige systemen zijn zodanig ingesteld dat alle code handtekeningen moeten worden gecontroleerd en hiervoor moeten de services van Power shell-editor hand matig worden goedgekeurd om te worden uitgevoerd op het systeem. Een groepsbeleid update die het uitvoerings beleid wijzigt, is waarschijnlijk een mogelijke oorzaak als u de Power shell-uitbrei ding hebt geïnstalleerd, maar er wordt een fout bericht ontvangen zoals:

```
Language server startup failed.
```

Open een Power shell-prompt en voer de volgende opdracht uit om Power shell editor-Services en de Power shell-uitbrei ding voor VSCode hand matig goed te keuren:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

U wordt gevraagd of **u software van deze niet-vertrouwde uitgever wilt uitvoeren?** Typ `A` om het bestand uit te voeren. Open vervolgens VSCode en controleer of de Power shell-extensie goed werkt. Als u nog steeds problemen ondervindt, laat het ons dan weten op [github](https://github.com/PowerShell/vscode-powershell/issues).

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Een versie van Power shell kiezen die moet worden gebruikt met de extensie

Met Power shell core die naast Windows Power shell wordt geïnstalleerd, is het nu mogelijk om een bepaalde versie van Power shell te gebruiken met de Power shell-extensie. Gebruik de volgende stappen om de versie te kiezen:

1. Open het **opdracht palet** in Windows of Linux met <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>. In macOS, gebruikt u <kbd>Cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>.
1. Zoek naar de **sessie**.
1. Klik op **Power shell: menu sessie weer geven**.
1. Kies de versie van Power shell die u wilt gebruiken in de lijst, bijvoorbeeld: **Power shell core**.

> [!IMPORTANT]
> Deze functie bekijkt enkele bekende paden op verschillende besturings systemen om installatie locaties van Power shell te detecteren. Als u Power shell hebt geïnstalleerd op een niet-typische locatie, wordt deze mogelijk niet eerst weer gegeven in het menu sessie. U kunt het menu sessie uitbreiden door [uw eigen aangepaste paden toe te voegen](#adding-your-own-powershell-paths-to-the-session-menu) , zoals hieronder wordt beschreven.

>[!NOTE]
> Er is een andere manier om naar het menu sessie te gaan. Wanneer een Power shell-bestand is geopend in uw editor, ziet u een groen versie nummer in de rechter benedenhoek. Als u op dit versie nummer klikt, gaat u naar het menu sessie.

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Uw eigen Power shell-paden toevoegen aan het menu sessie

U kunt andere uitvoer bare Power shell-paden toevoegen aan het menu sessie via een VSCode-instelling.

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

* `exePath`: het pad naar de `pwsh` of `powershell` uitvoer bare bestand.
* `versionName`: de tekst die wordt weer gegeven in het menu van de sessie.

U kunt de standaard-Power shell-versie instellen op het gebruik van de `powershell.powerShellDefaultVersion` instelling door dit in te stellen op de tekst die wordt weer gegeven in het menu sessie (ook wel bekend als de `versionName` in de laatste instelling):

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

Nadat u deze instelling hebt geconfigureerd, start u VSCode opnieuw of laadt u het huidige VSCode-venster opnieuw vanuit het **opdracht palet**, typt u **ontwikkelaar: venster opnieuw laden**.

Als u het menu sessie opent, ziet u nu uw extra Power shell-versies!

> [!NOTE]
> Als u Power shell bouwt vanaf een bron, is dit een fantastische manier om uw lokale build van Power shell te testen.

### <a name="configuration-settings-for-vscode"></a>Configuratie-instellingen voor VSCode

U kunt met behulp van de stappen in de vorige alinea configuratie-instellingen toevoegen in `settings.json`.

We raden de volgende configuratie-instellingen aan voor VSCode:

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

Als u niet wilt dat deze instellingen van invloed zijn op alle bestands typen, kunt u met VSCode ook configuraties per taal configureren. Maak een taalspecifieke instelling door instellingen in een `[<language-name>]` veld in te voeren. Bijvoorbeeld:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Zie [Wat is bestands codering](understanding-file-encoding.md)? voor meer informatie over bestands codering in VSCode.

## <a name="debugging-with-vscode"></a>Fout opsporing met VSCode

### <a name="no-workspace-debugging"></a>Geen-werk ruimte: fout opsporing

Vanaf VSCode-versie 1,9 kunt u fouten opsporen in Power shell-scripts zonder de map met het Power shell-script te openen. Open het Power shell-script bestand met het **bestand > bestand openen...** , stel een onderbrekings punt in op een regel, druk op <kbd>F9</kbd>en druk vervolgens op <kbd>F5</kbd> om de fout opsporing te starten. Het deel venster acties voor fout opsporing wordt weer gegeven, waarin u de fout opsporing kunt opdelen, stap, CV en stoppen.

### <a name="workspace-debugging"></a>Fout opsporing voor werk ruimten

Fout opsporing voor werk ruimten verwijst naar fout opsporing in de context van een map die u hebt geopend in Visual Studio code vanuit het menu **bestand** met **open map...** . De map die u opent, is doorgaans uw Power shell-projectmap en/of de hoofdmap van uw Git-opslag plaats.

Zelfs in deze modus kunt u de fout opsporing van het momenteel geselecteerde Power shell-script starten door op <kbd>F5</kbd>te drukken. Met fout opsporing in werk ruimten kunt u echter meerdere debug-configuraties definiëren, anders dan alleen fouten opsporen in het bestand dat momenteel is geopend. U kunt bijvoorbeeld een configuratie toevoegen aan:

- Start de tests van parasieten in het fout opsporingsprogramma.
- Start een specifiek bestand met argumenten in het fout opsporingsprogramma.
- Start een interactieve sessie in het fout opsporingsprogramma.
- Koppel het fout opsporingsprogramma aan een Power shell-hostproces.

Voer de volgende stappen uit om het configuratie bestand voor fout opsporing te maken:

  1. Open de weer gave **fout opsporing** op Windows of Linux door op <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>te drukken. Druk in macOS op <kbd>Cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>.
  1. Klik op het pictogram vistuig **configureren** op de werk balk.
  1. U wordt door VSCode gevraagd om **omgeving te selecteren**. Kies **Power shell**.

Het resultaat is dat VSCode een map en een bestand `.vscode\launch.json` maakt in de hoofdmap van de map met de werk ruimte. Deze locatie is waar de configuratie van de fout opsporing wordt opgeslagen. Als uw bestanden zich in een Git-opslag plaats bevinden, wilt u meestal het `launch.json` bestand door voeren. De inhoud van het `launch.json` bestand zijn:

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

Dit bestand vertegenwoordigt de veelvoorkomende scenario's voor fout opsporing. Wanneer u dit bestand in de editor opent, ziet u een knop **Configuratie toevoegen...** . U kunt op deze knop klikken om meer configuratie van Power Shell-fout opsporing toe te voegen. Een van de handig te toevoegen configuratie is **Power shell: script starten**. Met deze configuratie kunt u een bestand opgeven met optionele argumenten die moeten worden gestart wanneer u op <kbd>F5</kbd> drukt, ongeacht welk bestand momenteel actief is in de editor.

Nadat de configuratie van de fout opsporing is ingesteld, kunt u selecteren welke configuratie u tijdens een foutopsporingssessie wilt gebruiken. Selecteer een configuratie in de vervolg keuzelijst debug Configuration in de werk balk van de weer gave van de **fout opsporing** .

Er zijn enkele blogs die handig kunnen zijn om aan de slag te gaan met Power shell-extensie voor Visual Studio code:

- [Power shell-uitbrei ding][ps-extension]
- [Power shell-scripts schrijven en fouten opsporen in Visual Studio code][debug]
- [Fout opsporing van Visual Studio code guidance][vscode-guide]
- [Fout opsporing in Power shell in Visual Studio code][ps-vscode]
- [Aan de slag met Power shell-ontwikkeling in Visual Studio code][getting-started]
- [Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 1][editing-part1]
- [Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 2][editing-part2]
- [Fout opsporing voor Power shell-script in Visual Studio code – deel 1][debugging-part1]
- [Fout opsporing voor Power shell-script in Visual Studio code – deel 2][debugging-part2]

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a>Power shell-uitbrei ding voor VSCode

De bron code van de Power shell-extensie vindt u op [github](https://github.com/PowerShell/vscode-powershell).
