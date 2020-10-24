---
ms.date: 10/19/2020
keywords: Power shell, cmdlet, debug
title: Visual Studio code gebruiken voor het opsporen van fouten in gecompileerde cmdlets
description: Een bouw taak instellen en configuratie starten voor een PSModule-project in .NET core
ms.openlocfilehash: b51a69110c64b386f5c3ccf2527d1e184ef89257
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501640"
---
# <a name="using-visual-studio-code-to-debug-compiled-cmdlets"></a>Visual Studio code gebruiken voor het opsporen van fouten in gecompileerde cmdlets

In deze hand leiding wordt beschreven hoe u interactief fouten opspoort in C#-bron code voor een gecompileerde Power shell-module met behulp van Visual Studio code (VS code) en de C#-extensie.

Enige kennis van het fout opsporingsprogramma Visual Studio code wordt aangenomen.

- Zie [fout opsporing in Visual Studio code][]voor een algemene inleiding tot de VS code debugger.

- Voor voor beelden van fout opsporing van Power shell-script bestanden en-modules raadpleegt [u Visual Studio code gebruiken voor het extern bewerken en opsporen van fouten][].

In deze hand leiding wordt ervan uitgegaan dat u de instructies in de hand leiding voor het [schrijven van draag bare modules][] hebt gelezen en gevolgd.

## <a name="creating-a-build-task"></a>Een build-taak maken

Bouw uw project automatisch op voordat u een foutopsporingssessie start. Als u het opnieuw bouwt, zorgt u ervoor dat u fouten opspoort in de nieuwste versie van uw code.

Een build-taak configureren:

1. Voer in het **opdracht palet**de opdracht **standaard build-taak configureren** uit.

   ![Taak configureren standaard maken uitvoeren](media/using-vscode-for-debugging-compiled-cmdlets/configure-default-build-task.png)

1. Kies in het dialoog venster **Selecteer een taak die u wilt configureren** **tasks.jsop bestand maken van sjabloon**.

1. Kies in het dialoog venster **een taak sjabloon selecteren** de optie **.net core**.

Er wordt een nieuw `tasks.json` bestand gemaakt als er nog geen bestaat.

Uw build-taak testen:

1. Voer in het **opdracht palet**de opdracht **taak maken** uit.

1. Kies in het dialoog venster **Selecteer de taak die u wilt uitvoeren** op **bouwen**.

### <a name="information-about-dll-files-being-locked"></a>Informatie over DLL-bestanden die worden vergrendeld

Standaard wordt in een geslaagde build geen uitvoer weer gegeven in het deel venster Terminal. Als er geen uitvoer wordt weer geven die het tekst **Project bestand**bevat, moet u het `tasks.json` bestand bewerken. Neem het expliciete pad op naar het C#-project, uitgedrukt als `"${workspaceFolder}/myModule"` . In dit voor beeld `myModule` is de naam van de projectmap. Deze vermelding moet als volgt worden weer gegeven na de `build` vermelding in de `args` lijst:

```json
    {
        "label": "build",
        "command": "dotnet",
        "type": "shell",
        "args": [
            "build",
            "${workspaceFolder}/myModule",
            // Ask dotnet build to generate full paths for file names.
            "/property:GenerateFullPaths=true",
            // Do not generate summary otherwise it leads to duplicate errors in Problems panel
            "/consoleloggerparameters:NoSummary",
        ],
        "group": "build",
        "presentation": {
            "reveal": "silent"
        },
        "problemMatcher": "$msCompile"
    }
```

Bij het opsporen van fouten wordt uw module-DLL geïmporteerd in de Power shell-sessie in de VS code-Terminal. De DLL wordt vergrendeld. Het volgende bericht wordt weer gegeven wanneer u de taak maken uitvoert zonder de terminal sessie te sluiten:

```Output
Could not copy "obj\Debug\netstandard2.0\myModule.dll" to "bin\Debug\netstandard2.0\myModule.dll"`.
```

Terminal sessies moeten worden gesloten voordat u opnieuw bouwt.

## <a name="setting-up-the-debugger"></a>Het fout opsporingsprogramma instellen

Als u fouten wilt opsporen in de Power shell-cmdlet, moet u een aangepaste start configuratie instellen. Deze configuratie wordt gebruikt voor het volgende:

- Uw bron code maken
- Power shell starten met de module geladen
- Power shell geopend laten in het deel venster Terminal

Wanneer u de cmdlet aanroept in de terminal sessie, stopt het fout opsporingsprogramma bij eventuele onderbrekings punten die in de bron code zijn ingesteld.

### <a name="configuring-launchjson-for-powershell-core"></a>launch.jsconfigureren voor Power shell core

1. Installeer de [C# voor Visual Studio code][] extension

1. Voeg in het deel venster fout opsporing een configuratie voor fout opsporing toe

1. Kies in het `Select environment` dialoog venster `.NET Core`

1. Het `launch.json` bestand wordt geopend in de editor. Met de cursor in de `configurations` matrix, ziet u de `configuration` kiezer. Als u deze lijst niet ziet, selecteert u **Configuratie toevoegen**.

1. Als u een standaard configuratie voor fout opsporing wilt maken, selecteert u de **app .net Core-Console starten**:

   ![.NET Core-Console-app starten](media/using-vscode-for-debugging-compiled-cmdlets/add-configuration-dialog.png)

1. Bewerk de `name` `program` velden,, `args` en `console` als volgt:

   ```json
    {
        "name": "PowerShell cmdlets: pwsh",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "pwsh",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

Het `program` veld wordt gebruikt om te starten `pwsh` zodat de cmdlet die wordt opgespoord, kan worden uitgevoerd. Het `-NoExit` argument voor komt dat de Power shell-sessie wordt afgesloten zodra de module wordt geïmporteerd.
Het pad in het `Import-Module` argument is het standaarduitvoer traject voor builds wanneer u de hand leiding voor het [schrijven van draag bare modules][] hebt gevolgd. Als u een module manifest ( `.psd1` bestand) hebt gemaakt, moet u het pad hiervoor gebruiken. Het `/` padscheidingsteken werkt in Windows, Linux en macOS. U moet de geïntegreerde Terminal gebruiken om de Power shell-opdrachten uit te voeren waarvoor u fouten wilt opsporen.

> [!NOTE]
> Als het fout opsporingsprogramma niet stopt bij onderbrekings punten, kijkt u in de Visual Studio code debug console op een regel met de volgende tekst:
>
> ```
> Loaded '/path/to/myModule.dll'. Skipped loading symbols. Module is optimized and the debugger option 'Just My Code' is enabled.
> ```
>
> Als u dit ziet, voegt u toe `"justMyCode": false` aan de start configuratie (op hetzelfde niveau als `"console": "integratedTerminal"` .

### <a name="configuring-launchjson-for-windows-powershell"></a>launch.jsconfigureren voor voor Windows Power shell

Deze start configuratie werkt voor het testen van uw cmdlets in Windows Power shell ( `powershell.exe` ).
Maak een tweede start configuratie met de volgende wijzigingen:

1. `name` moet worden `PowerShell cmdlets: powershell`

1. `type` moet worden `clr`

1. `program` moet worden `powershell`

   Dit ziet er als volgt uit:

   ```json
    {
        "name": "PowerShell cmdlets: powershell",
        "type": "clr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "powershell",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

## <a name="launching-a-debugging-session"></a>Een foutopsporingssessie starten

Alles is nu klaar om te beginnen met de fout opsporing.

- Plaats een onderbrekings punt in de bron code voor de cmdlet waarvoor u fouten wilt opsporen:

  ![Een onderbrekings punt wordt weer gegeven als een rode stip in de rugmarge](media/using-vscode-for-debugging-compiled-cmdlets/set-breakpoint.png)

- Zorg ervoor dat de relevante configuratie van de **Power shell-cmdlets** is geselecteerd in de vervolg keuzelijst configuratie in de weer gave **fout opsporing** :

  ![De start configuratie selecteren](media/using-vscode-for-debugging-compiled-cmdlets/select-launch-configuration.png)

- Druk op <kbd>F5</kbd> of klik op de knop **fout opsporing starten**

- Ga naar het Terminal venster en roep uw cmdlet aan:

  ![De cmdlet aanroepen](media/using-vscode-for-debugging-compiled-cmdlets/invoke-the-cmdlet.png)

- Uitvoering stopt bij het onderbrekings punt:

  ![Uitvoeringen stopt bij onderbrekings punt](media/using-vscode-for-debugging-compiled-cmdlets/stopped-at-breakpoint.png)

U kunt de bron code stapsgewijs door lopen, variabelen inspecteren en de aanroep stack controleren.

Als u de fout opsporing wilt beëindigen, klikt u in de werk balk fout opsporing op **stoppen** of drukt u op <kbd>SHIFT</kbd> - <kbd>F5</kbd>. De shell die wordt gebruikt voor fout opsporing sluit af en geeft de vergren deling van het gecompileerde DLL-bestand vrij.

<!-- reference links -->
[Fout opsporing in Visual Studio code]: https://code.visualstudio.com/docs/editor/debugging
[Visual Studio Code gebruiken voor externe bewerking en foutopsporing]: using-vscode-for-remote-editing-and-debugging.md
[Draag bare modules schrijven]: ../writing-portable-modules.md
[C# voor Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
