# <a name="using-visual-studio-code-for-powershell-development"></a>Met behulp van Visual Studio Code voor het ontwikkelen van PowerShell

Naast de [PowerShell ISE][ise], PowerShell wordt ook goed ondersteund in Visual Studio Code.
Bovendien wordt de ISE niet ondersteund met PowerShell-kern wanneer Visual Studio Code wordt ondersteund voor PowerShell Core op alle platforms (Windows, Mac OS en Linux)

U kunt Visual Studio Code in Windows met PowerShell versie 5 met behulp van Windows 10 of door het installeren van [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) voor eerdere Windows-besturingssystemen (bijvoorbeeld Windows 8.1, enzovoort).

Voordat u begint het, Controleer of dat PowerShell bestaat op uw systeem.
Zie voor moderne werkbelastingen op Windows-, Mac OS- en Linux:

- [PowerShell Core installeert op Mac OS- en Linux][install-pscore-linux]
- [PowerShell Core installeren in Windows][install-pscore-windows]

Zie voor traditionele Windows PowerShell-werkbelastingen, [Windows PowerShell installeren][install-winps].

## <a name="editing-with-visual-studio-code"></a>Bewerken met Visual Studio Code

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Visual Studio Code installeren](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: Volg de instructies voor installatie op de [uitgevoerd tegenover Code op Linux](https://code.visualstudio.com/docs/setup/linux) pagina

- **Mac OS**: Volg de instructies voor installatie op de [uitgevoerd tegenover Code op Mac OS](https://code.visualstudio.com/docs/setup/mac) pagina

> [!IMPORTANT]
> Op Mac OS, moet u OpenSSL voor de PowerShell-uitbreiding correct te laten werken.
> De eenvoudigste manier om dit te bereiken is voor het installeren van [Homebrew](http://brew.sh/) en voer vervolgens `brew install openssl`.
> De PowerShell-extensie is nu mogelijk zijn geladen.

- **Windows**: Volg de instructies voor installatie op de [tegenover Code uitgevoerd op Windows](https://code.visualstudio.com/docs/setup/windows) pagina

### <a name="2-installing-powershell-extension"></a>2. Installeren van PowerShell-extensie

- Start de Visual Studio Code app door:
    - **Windows**: typen `code` in uw PowerShell-sessie
    - **Linux**: typen `code` in uw terminal
    - **Mac OS**: typen `code` in uw terminal

- Start **snelle Open** door te drukken **Ctrl + P** (**Cmd + P** op Mac).
- Typ in het vak snel openen `ext install powershell` en treffers **Enter**.
- De **extensies** weergave wilt openen op de zijmarge. Selecteer de PowerShell-uitbreiding van Microsoft.
  U ziet, zoals hieronder:

  ![VSCode](../../images/vscode.png)

- Klik op de **installeren** knop van de PowerShell-extensie van Microsoft.
- Na de installatie ziet u de **installeren** knop verandert in **opnieuw laden**.
  Klik op **opnieuw laden**.
- Nadat Visual Studio Code opnieuw laden heeft, bent u klaar om te bewerken.

Bijvoorbeeld voor het maken van een nieuw bestand, klikt u op **File -> nieuw**.
Als u wilt opslaan, klikt u op **File -> Opslaan** en geef vervolgens een bestandsnaam, gaan we spreek `HelloWorld.ps1`.
U sluit het bestand, klik op 'x' naast de bestandsnaam.
Om af te sluiten van Visual Studio Code **File -> afsluiten**.

#### <a name="using-a-specific-installed-version-of-powershell"></a>Een specifieke geïnstalleerde versie van PowerShell

Als u een specifieke installatie van PowerShell gebruiken met Visual Studio Code wilt, moet u een nieuwe variabele toevoegen aan het bestand van de gebruiker-instellingen.

1. Klik op **File-Voorkeuren > Instellingen ->**
1. Twee deelvensters van de editor wordt weergegeven.
   In het deelvenster van de meest rechtse (`settings.json`), voeg de onderstaande instelling geschikt is voor uw besturingssysteem ergens tussen de twee accolades (`{` en `}`) en vervang  *<version>*  met de geïnstalleerde PowerShell-versie:

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. Vervangt de instelling met het pad naar het gewenste uitvoerbare PowerShell
1. Sla het instellingenbestand en Visual Studio Code opnieuw starten

#### <a name="configuration-settings-for-visual-studio-code"></a>Configuratie-instellingen voor Visual Studio Code

U kunt configuratie-instellingen in toevoegen met behulp van de stappen in de vorige alinea `settings.json`.

U wordt aangeraden de volgende configuratieinstellingen voor Visual Studio Code:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>Foutopsporing met Visual Studio Code

### <a name="no-workspace-debugging"></a>Er is geen werkruimte foutopsporing

Vanaf versie van Visual Studio Code 1,9 kunt u PowerShell-scripts zonder te openen van de map met het PowerShell-script voor foutopsporing.
Gewoon openen met de PowerShell-scriptbestand **File -> bestand openen...** , stel een onderbrekingspunt in op een regel (druk op F9) en druk op F5 foutopsporing te starten.
Hier ziet u het actiedeelvenster voor foutopsporing worden weergegeven waarmee u in het foutopsporingsprogramma, stap, hervatten en stop foutopsporing te verdelen.

### <a name="workspace-debugging"></a>Werkruimte foutopsporing

Werkruimte foutopsporing verwijst naar het opsporen van fouten in de context van een map die u hebt geopend in met behulp van Visual Studio Code **map openen...**  van de **bestand** menu.
De map die u opent is meestal de projectmap PowerShell en/of de hoofdmap van de Git-opslagplaats.

U kunt zelfs in deze modus starten foutopsporing van het momenteel geselecteerde PowerShell-script door op F5 te drukken.
Echter, kunt u voor het definiëren van configuraties met meerdere foutopsporing dan alleen het geopende bestand foutopsporing werkruimte foutopsporing.
U kunt bijvoorbeeld een configuraties toevoegen:

- Pester tests in de foutopsporing starten
- Een specifiek bestand met argumenten in het foutopsporingsprogramma starten
- Een interactieve sessie in de foutopsporing starten
- Het foutopsporingsprogramma koppelen aan een hostproces van PowerShell

Volg deze stappen om uw configuratiebestand foutopsporing te maken:

1. Open de **Debug** weergeven door te drukken **Ctrl + Shift + D** (**Cmd + Shift + D** op Mac).
1. Druk op de **configureren** tandwielpictogram-pictogram op de werkbalk.
1. Visual Studio Code wordt u gevraagd te **omgeving Selecteer**.
   Kies **PowerShell**.

   Als u dit doet, Visual Studio Code een map en een bestand '.vscode\launch.json' gemaakt in de hoofdmap van uw werkruimtemap.
   Hier wordt de configuratie van de foutopsporing is opgeslagen. Als de bestanden zich in een Git-opslagplaats, wilt u waarschijnlijk het bestand launch.json doorvoeren.
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
Echter, wanneer u dit bestand in de editor opent, ziet u een **configuratie toevoegen...**  knop.
U kunt drukt u op deze knop om meer PowerShell foutopsporing configuraties toevoegt. Een handige configuratie om toe te voegen is **PowerShell: Script starten**.
Met deze configuratie kunt u een specifiek bestand met optionele argumenten die moet worden gestart telkens wanneer u op F5 drukken ongeacht welk bestand is momenteel actief zijn in de editor.

Wanneer de configuratie van de foutopsporing is gemaakt, kunt u selecteren welke configuratie u gebruiken tijdens een foutopsporingssessie voor wilt door een te selecteren in de configuratie van de foutopsporing vervolgkeuzelijst in de **Debug** van weergave-werkbalk.

Er zijn enkele blogs die mogelijk nuttig om aan de slag met PowerShell-extensie voor Visual Studio Code te gaan

- Visual Studio Code: [PowerShell-uitbreiding][ps-extension]
- [Schrijven en foutopsporing van PowerShell-scripts in Visual Studio Code][debug]
- [Foutopsporing van Visual Studio Code richtlijnen][vscode-guide]
- [Foutopsporing van PowerShell in Visual Studio Code][ps-vscode]
- [Aan de slag met PowerShell-ontwikkeling in Visual Studio Code][getting-started]
- [Visual Studio Code bewerkingsfuncties voor PowerShell-ontwikkeling: deel 1][editing-part1]
- [Visual Studio Code bewerkingsfuncties voor PowerShell ontwikkeling – deel 2][editing-part2]
- [PowerShell-script voor foutopsporing in Visual Studio Code – deel 1][debugging-part1]
- [PowerShell-script voor foutopsporing in Visual Studio Code – deel 2][debugging-part2]

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-macOS-and-Linux.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>PowerShell-extensie voor Visual Studio Code

Broncode van de PowerShell-uitbreiding kunt u vinden op [GitHub](https://github.com/PowerShell/vscode-powershell).
