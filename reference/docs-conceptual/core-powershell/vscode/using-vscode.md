---
title: Visual Studio Code gebruiken voor het ontwikkelen van PowerShell
description: Visual Studio Code gebruiken voor het ontwikkelen van PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 6433a875c233283f94d70c7acd7d394c73029b6d
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320445"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Visual Studio Code gebruiken voor het ontwikkelen van PowerShell

Naast de [PowerShell ISE][ise], PowerShell wordt ook goed ondersteund in Visual Studio Code.
Bovendien wordt de ISE niet ondersteund met PowerShell Core, terwijl de Visual Studio Code voor PowerShell Core wordt ondersteund op alle platformen (Windows, macOS en Linux)

U kunt Visual Studio Code op Windows met PowerShell versie 5 gebruiken met behulp van Windows 10 of door het installeren van [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) voor downlevel-Windows-OSs (bijvoorbeeld Windows 8.1, enzovoort).

Voordat u begint met het, Controleer of dat PowerShell bestaat op uw systeem.
Zie voor moderne workloads in Windows, macOS en Linux:

- [PowerShell Core in Linux installeren][install-pscore-linux]
- [PowerShell Core in macOS installeren][install-pscore-macos]
- [PowerShell Core in Windows installeren][install-pscore-windows]

Zie voor traditionele Windows PowerShell-workloads, [Windows PowerShell installeren][install-winps].

## <a name="editing-with-visual-studio-code"></a>Bewerken met Visual Studio Code

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Visual Studio Code installeren](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op Linux](https://code.visualstudio.com/docs/setup/linux) pagina

- **macOS**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op macOS](https://code.visualstudio.com/docs/setup/mac) pagina

  > [!IMPORTANT]
  > Op Mac OS, moet u OpenSSL voor de extensie van PowerShell correct te laten werken.
  > De eenvoudigste manier om dit te doen is voor het installeren van [Homebrew](https://brew.sh/) en voer `brew install openssl`.
  > VS Code kan nu worden geladen de PowerShell-extensie.

- **Windows**: Volg de instructies voor installatie op de [VS-Code wordt uitgevoerd op Windows](https://code.visualstudio.com/docs/setup/windows) pagina

### <a name="2-installing-powershell-extension"></a>2. PowerShell-extensie installeren

- Start Visual Studio Code app door:
  - **Windows**: typen `code` in uw PowerShell-sessie
  - **Linux**: typen `code` in uw terminal
  - **macOS**: typen `code` in uw terminal

- Start **snel openen** door te drukken **Ctrl + P** (**Cmd + P** op Mac).
- Typ in snel openen `ext install powershell` en klik op **Enter**.
- De **extensies** weergave geopend op de zijbalk. Selecteer de PowerShell-uitbreiding van Microsoft.
  U zou iets moet zien zoals hieronder:

  ![VSCode](../../images/vscode.png)

- Klik op de **installeren** knop van de PowerShell-extensie van Microsoft.
- Na de installatie, ziet u de **installeren** knop verandert in **opnieuw laden**.
  Klik op **opnieuw laden**.
- Nadat Visual Studio Code opnieuw laden is, bent u klaar voor het bewerken van.

Bijvoorbeeld, als u wilt een nieuw bestand maken, klikt u op **File -> New**.
Als u wilt opslaan, klikt u op **File -> Opslaan** en geef vervolgens een bestandsnaam op, laten we zeggen `HelloWorld.ps1`.
U sluit het bestand, klikt u op 'x' naast de bestandsnaam van het.
Om af te sluiten van Visual Studio Code, **File -> afsluiten**.

#### <a name="using-a-specific-installed-version-of-powershell"></a>Met behulp van een specifieke versie van PowerShell

Als u gebruiken van een specifieke installatie van PowerShell met Visual Studio Code wilt, moet u een nieuwe variabele toevoegen aan het bestand met gebruiker instellingen.

1. Klik op **File -> Voorkeuren >-instellingen**
1. Twee deelvensters van de rapporteditor worden weergegeven.
   In het deelvenster uiterst rechts (`settings.json`), invoegen van de instelling van de onderstaande geschikt is voor uw besturingssysteem ergens tussen de twee gekrulde haken (`{` en `}`) en vervang **\<versie\>** met de geïnstalleerde versie van PowerShell:

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. De instelling vervangen door het pad naar de gewenste uitvoerbare PowerShell
1. Het bestand met instellingen opslaan en opnieuw opstarten van Visual Studio Code

#### <a name="configuration-settings-for-visual-studio-code"></a>Configuratie-instellingen voor Visual Studio Code

U kunt configuratie-instellingen in toevoegen met behulp van de stappen in de vorige alinea `settings.json`.

U wordt aangeraden de volgende configuratie-instellingen voor Visual Studio Code:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>Fouten opsporen met Visual Studio Code

### <a name="no-workspace-debugging"></a>Geen werkruimte foutopsporing

Vanaf versie van Visual Studio Code 1.9 kunt u PowerShell-scripts fouten opsporen zonder te open de map met het PowerShell-script.
Open gewoon de PowerShell-scriptbestand met **File -> bestand openen...** , stel een onderbrekingspunt in op een regel (druk op F9) en druk vervolgens op F5 foutopsporing te starten.
U ziet het actiedeelvenster van foutopsporing worden weergegeven waarmee u in het foutopsporingsprogramma, stap, hervatten en stop foutopsporing opsplitsen.

### <a name="workspace-debugging"></a>Werkruimte-foutopsporing

Werkruimte foutopsporing verwijst naar het opsporen van fouten in de context van een map die u hebt geopend in Visual Studio Code met behulp van **map openen...**  uit de **bestand** menu.
De map die u opent is meestal de projectmap op PowerShell en/of de hoofdmap van de Git-opslagplaats.

Zelfs in deze modus kunt u beginnen met het opsporen van fouten in de momenteel geselecteerde PowerShell-script door op F5 te drukken.
Echter, kunt u definiëren configuraties met meerdere foutopsporing dan alleen opsporen van fouten in het geopende bestand werkruimte foutopsporing.
U kunt bijvoorbeeld een configuraties die u kunt toevoegen:

- Pester tests in het foutopsporingsprogramma Start
- Een specifiek bestand met argumenten in het foutopsporingsprogramma Start
- Een interactieve sessie in het foutopsporingsprogramma Start
- Het foutopsporingsprogramma koppelen aan een hostproces van PowerShell

Volg deze stappen om uw debug-configuratiebestand te maken:

  1. Open de **Debug** weergeven door te drukken **Ctrl + Shift + D** (**Cmd + Shift + D** op Mac).
  2. Druk op de **configureren** tandwielpictogram in de werkbalk.
  3. U wordt gevraagd om Visual Studio Code **omgeving selecteert**. Kies **PowerShell**.

  Als u dit doet, maakt Visual Studio Code een map en een bestand '.vscode\launch.json' in de hoofdmap van de werkruimtemap van uw.
  Dit is waar uw debug-configuratie is opgeslagen. Als de bestanden zich in een Git-opslagplaats, wilt u meestal het bestand launch.json doorvoeren.
  De inhoud van het bestand launch.json zijn:

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

  Hiermee wordt de algemene scenario's voor foutopsporing.
  Echter, als u dit bestand in de editor opent, ziet u een **configuratie toevoegen...**  knop.
  U drukt op deze knop om toe te voegen meer PowerShell-configuraties voor foutopsporing. Een handige configuratie toe te voegen is **PowerShell: Script Start**.
  Met deze configuratie kunt u een specifiek bestand met optionele argumenten die moet worden gestart wanneer u op F5 drukt ongeacht welk bestand is momenteel actief zijn in de editor.

  Zodra de configuratie van de foutopsporing tot stand is gebracht, kunt u selecteren welke configuratie u gebruiken tijdens een foutopsporingssessie wilt door het selecteren van een van de configuratie van de foutopsporing vervolgkeuzelijst in de **Debug** van weergave-werkbalk.

Er zijn een paar blogs die mogelijk nuttig zijn om aan de slag met PowerShell-extensie voor Visual Studio Code:

- [Extensie van PowerShell][ps-extension]
- [Schrijf en fouten opsporen in PowerShell-scripts in Visual Studio Code][debug]
- [Foutopsporing van Visual Studio Code-richtlijnen][vscode-guide]
- [Foutopsporing in PowerShell in Visual Studio Code][ps-vscode]
- [Aan de slag met PowerShell-ontwikkeling in Visual Studio Code][getting-started]
- [Visual Studio Code bewerken van functies voor het ontwikkelen van PowerShell-deel 1][editing-part1]
- [Visual Studio Code bewerken van functies voor het ontwikkelen van PowerShell-deel 2][editing-part2]
- [PowerShell-script voor foutopsporing in Visual Studio Code – deel 1][debugging-part1]
- [PowerShell-script voor foutopsporing in Visual Studio Code – deel 2][debugging-part2]

[ise]: ../ise-guide.md
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

## <a name="powershell-extension-for-visual-studio-code"></a>PowerShell-extensie voor Visual Studio Code

De broncode van de PowerShell-extensie kunt u vinden op [GitHub](https://github.com/PowerShell/vscode-powershell).
