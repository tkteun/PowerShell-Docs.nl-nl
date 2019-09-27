---
title: Visual Studio code for Power Shell Development gebruiken
description: Visual Studio code for Power Shell Development gebruiken
ms.date: 08/06/2018
ms.openlocfilehash: 0e082b74f99d214749f10224fb5aaf41e2ef8951
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325234"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Visual Studio code for Power Shell Development gebruiken

Naast [Power shell ISE][ise]is Power shell ook goed ondersteund in Visual Studio code (VSCode). Bovendien wordt de ISE niet ondersteund met Power shell core, terwijl VSCode wordt ondersteund voor Power shell Core op alle platformen (Windows, macOS en Linux)

U kunt VSCode in Windows met Power shell versie 5 gebruiken met behulp van Windows 10 of door [Windows Management Framework 5,0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) te installeren voor een down level Windows oss (bijvoorbeeld Windows 8,1, enzovoort).

Controleer voordat u begint of Power shell op uw systeem is geïnstalleerd. Voor moderne werk belastingen op Windows, macOS en Linux raadpleegt u:

- [Power shell Core installeren in Linux][install-pscore-linux]
- [Power shell core in macOS installeren][install-pscore-macos]
- [Power shell Core installeren in Windows][install-pscore-windows]

Zie [Windows Power Shell installeren][install-winps]voor traditionele workloads van Windows Power shell.

## <a name="editing-with-vscode"></a>Bewerken met VSCode

1. [VSCode installeren](https://code.visualstudio.com/Docs/setup/setup-overview)

   - **Linux**: Volg de installatie-instructies op de pagina [actieve VSCode op Linux](https://code.visualstudio.com/docs/setup/linux)
   - **macOS**: Volg de installatie-instructies op de pagina [actieve VSCode op macOS](https://code.visualstudio.com/docs/setup/mac)

     > [!IMPORTANT]
     > Bij macOS moet u OpenSSL installeren om de Power shell-extensie correct te laten werken. De eenvoudigste manier om dit te doen is door [homebrew](https://brew.sh/) te installeren en `brew install openssl`vervolgens uit te voeren. VSCode kan nu de Power shell-uitbrei ding laden.

   - **Windows**: Volg de installatie-instructies op de pagina [actieve VSCode op Windows](https://code.visualstudio.com/docs/setup/windows)

2. Power shell-extensie installeren

   - Start de VSCode-app op:
     - **Windows**: typen `code` in uw Power shell-sessie
     - **Linux**: typen `code` in uw Terminal
     - **macOS**: typen `code` in uw Terminal
   - Start **snel openen** door op <kbd>CTRL</kbd>+<kbd>P</kbd> te drukken (<kbd>cmd</kbd>+<kbd>p</kbd> op Mac).
   - Typ `ext install powershell` en druk op **Enter**in snel openen.
   - De weer gave **extensies** wordt weer gegeven op de balk aan de zijkant. Selecteer de Power shell-extensie van micro soft.
     U ziet nu het volgende:

     ![VSCode](../../images/using-vscode/vscode.png)

   - Klik op de knop **installeren** in de Power shell-extensie van micro soft.
   - Na de installatie ziet u de knop **installeren** om opnieuw te **laden**. Klik op **opnieuw laden**.
   - Nadat VSCode opnieuw is geladen, bent u klaar om te bewerken.

Als u bijvoorbeeld een nieuw bestand wilt maken, klikt u op **bestand-> nieuw**. Als u deze wilt opslaan, klikt u op **bestand-> opslaan** en geeft u een bestands naam `HelloWorld.ps1`op. Als u het bestand wilt sluiten, klikt u op ' x ' naast de bestands naam. Als u VSCode wilt afsluiten, wordt **het bestand > afgesloten**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>De Power shell-uitbrei ding installeren op beperkte systemen

Sommige systemen zijn zodanig ingesteld dat alle code handtekeningen moeten worden gecontroleerd en daarom moeten Power shell-editor Services hand matig worden goedgekeurd om te worden uitgevoerd op het systeem. Een groepsbeleid update die het uitvoerings beleid wijzigt, is waarschijnlijk een mogelijke oorzaak als u de Power shell-uitbrei ding hebt geïnstalleerd maar een fout ziet zoals:

```
Language server startup failed.
```

Voor het hand matig goed keuren van Power shell-editor Services en de Power shell-extensie voor VSCode een Power shell-prompt openen en uitvoeren:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

U wordt gevraagd of u software van deze niet-vertrouwde uitgever wilt uitvoeren. Typ `R` om het bestand uit te voeren. Open vervolgens VSCode en controleer of de Power shell-extensie goed werkt. Als u nog steeds problemen ondervindt, laat het ons dan weten op [github](https://github.com/PowerShell/vscode-powershell/issues).

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Een versie van Power shell kiezen die moet worden gebruikt met de extensie

Met Power shell Core installeren naast Windows Power shell is het nu mogelijk om een bepaalde versie van Power shell te gebruiken met de Power shell-extensie. Gebruik de volgende stappen om de versie te kiezen:

1. Open de opdracht pallet (<kbd>CTRL</kbd>+<kbd>+ SHIFT</kbd>+<kbd>p</kbd> op Windows & Linux, <kbd>cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>p</kbd> op macOS).
1. Zoek naar "Session".
1. Klik op Power shell: Menu sessie weer geven.
1. Kies de versie van Power shell die u wilt gebruiken in de lijst, bijvoorbeeld Power shell core.

> [!IMPORTANT]
> Deze functie bekijkt enkele bekende paden op verschillende besturings systemen om installatie locaties van Power shell te detecteren. Als u Power shell hebt geïnstalleerd op een niet-typische locatie, wordt deze mogelijk niet eerst weer gegeven in het menu sessie. U kunt het menu sessie uitbreiden door [uw eigen aangepaste paden toe te voegen](#adding-your-own-powershell-paths-to-the-session-menu) , zoals hieronder wordt beschreven.

>[!NOTE]
> Er is een andere manier om naar het menu sessie te gaan. Wanneer een Power shell-bestand is geopend in uw editor, ziet u een groen versie nummer in de rechter benedenhoek. Als u op dit versie nummer klikt, gaat u naar het menu sessie.

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Uw eigen Power shell-paden toevoegen aan het menu sessie

U kunt andere uitvoer bare Power shell-paden toevoegen aan het menu sessie via een VSCode-instelling.

Voeg een item toe aan de `powershell.powerShellAdditionalExePaths` lijst of maak een lijst als deze niet bestaat in `settings.json`uw:

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

* `exePath`: Het pad naar het `pwsh` of `powershell` het uitvoer bare bestand.
* `versionName`: De tekst die wordt weer gegeven in het menu van de sessie.

U kunt de standaard-Power shell-versie instellen op `powershell.powerShellDefaultVersion` het gebruik van de instelling door dit in te stellen op de tekst die wordt `versionName` weer gegeven in het menu sessie (ook wel de in de laatste instelling):

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

Wanneer u deze instelling hebt ingesteld, start u VSCode opnieuw of gebruikt u de ' ontwikkel aars: Het venster opdracht pallet actie opnieuw laden om het huidige VSCode-venster opnieuw te laden.

Als u het menu sessie opent, ziet u nu uw extra Power shell-versies!

> [!NOTE]
> Als u Power shell bouwt vanaf een bron, is dit een fantastische manier om uw lokale build van Power shell te testen.

#### <a name="configuration-settings-for-vscode"></a>Configuratie-instellingen voor VSCode

Door de stappen in de vorige alinea te gebruiken, kunt u configuratie- `settings.json`instellingen toevoegen in.

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

Vanaf VSCode-versie 1,9 kunt u fouten opsporen in Power shell-scripts zonder dat u de map met het Power shell-script hoeft te openen. Open het Power shell-script bestand met **File-> open file...** , stel een onderbrekings punt in op een regel (druk op <kbd>F9</kbd>) en druk vervolgens op <kbd>F5</kbd> om de fout opsporing te starten. Het deel venster acties voor fout opsporing wordt weer gegeven, waarin u de fout opsporing, stap, hervatten en stoppen van het fout opsporingsprogramma kunt onderbreken.

### <a name="workspace-debugging"></a>Fout opsporing voor werk ruimten

Fout opsporing voor werk ruimten verwijst naar fout opsporing in de context van een map die u hebt geopend in Visual Studio code met behulp van **openen map...** in het menu **bestand** . De map die u opent, is doorgaans uw Power shell-projectmap en/of de hoofdmap van uw Git-opslag plaats.

Zelfs in deze modus kunt u de fout opsporing van het momenteel geselecteerde Power shell-script starten door simpelweg op <kbd>F5</kbd>te drukken. Met fout opsporing in werk ruimten kunt u echter meerdere debug-configuraties definiëren, anders dan alleen fouten opsporen in het bestand dat momenteel is geopend. U kunt bijvoorbeeld een configuratie toevoegen aan:

- Schadelijke tests starten in het fout opsporingsprogramma
- Een specifiek bestand met argumenten in het fout opsporingsprogramma starten
- Een interactieve sessie starten in het fout opsporingsprogramma
- Het fout opsporingsprogramma koppelen aan een Power shell-hostproces

Voer de volgende stappen uit om het configuratie bestand voor fout opsporing te maken:

  1. Open de weer gave **fout opsporing** door op <kbd>CTRL</kbd>+<kbd>+ SHIFT</kbd>+<kbd>d</kbd> te drukken (<kbd>cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>d</kbd> op Mac).
  2. Klik op het pictogram vistuig **configureren** op de werk balk.
  3. U wordt door VSCode gevraagd om **omgeving te selecteren**. Kies **Power shell**.

  Wanneer u dit doet, maakt VSCode een map en een bestand '. vscode\launch.json ' in de hoofdmap van uw werkruimte map. Hier wordt de configuratie van de fout opsporing opgeslagen. Als uw bestanden zich in een Git-opslag plaats bevinden, wilt u meestal het bestand Launch. json door voeren. De inhoud van het bestand Launch. json is:

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

  Dit duidt op de veelvoorkomende scenario's voor fout opsporing. Wanneer u dit bestand echter in de editor opent, ziet u een knop **Configuratie toevoegen...** . U kunt op deze knop klikken om meer configuratie van Power Shell-fout opsporing toe te voegen. Power shell is **een handige configuratie om toe te voegen. Script**starten. Met deze configuratie kunt u een specifiek bestand opgeven met optionele argumenten die moeten worden gestart wanneer u op <kbd>F5</kbd> drukt, ongeacht welk bestand momenteel actief is in de editor.

  Zodra de configuratie van de fout opsporing is ingesteld, kunt u selecteren welke configuratie u tijdens een foutopsporingssessie wilt gebruiken door er een te selecteren in de vervolg keuzelijst debug-configuratie op de werk balk van de weer gave van de **fout** opsporing.

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

## <a name="powershell-extension-for-vscode"></a>Power shell-uitbrei ding voor VSCode

De bron code van de Power shell-extensie vindt u op [github](https://github.com/PowerShell/vscode-powershell).
