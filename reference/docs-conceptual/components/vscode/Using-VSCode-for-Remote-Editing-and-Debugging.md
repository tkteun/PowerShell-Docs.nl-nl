---
title: Visual Studio Code gebruiken voor externe bewerking en foutopsporing
description: Visual Studio Code gebruiken voor externe bewerking en foutopsporing
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/19/2019
ms.locfileid: "67264025"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Visual Studio Code gebruiken voor externe bewerking en foutopsporing

Bedoeld voor degenen die bekend met de ISE zijn misschien herinnert u zich dat u kunt uitvoeren `psedit file.ps1` rechtstreeks vanuit de geïntegreerde console bestanden - lokale of externe - te openen in de ISE.

Deze functie is ook beschikbaar in de PowerShell-extensie voor VSCode. Deze handleiding wordt beschreven hoe u dit doet.

## <a name="prerequisites"></a>Vereisten

Deze handleiding wordt ervan uitgegaan dat u hebt:

- een externe bron (bijvoorbeeld: een virtuele machine, een container) dat u toegang tot hebt
- PowerShell die worden uitgevoerd op deze en de hostcomputer
- VSCode en de PowerShell-extensie voor VSCode

Deze functie werkt op Windows PowerShell en PowerShell Core.

Deze functie werkt ook bij het verbinden met een externe computer via WinRM, PowerShell Direct of SSH. Als u wilt gebruiken van SSH, maar met behulp van Windows, bekijk dan de [Win32-versie van SSH](https://github.com/PowerShell/Win32-OpenSSH)!

> [!IMPORTANT]
> De `Open-EditorFile` en `psedit` opdrachten alleen werken in de **PowerShell geïntegreerde Console** gemaakt door de PowerShell-extensie voor VSCode.

## <a name="usage-examples"></a>Voorbeelden van het gebruik

Deze voorbeelden tonen externe bewerken en foutopsporing via een MacBook Pro op een Ubuntu-VM die wordt uitgevoerd in Azure. Het proces is vrijwel identiek in Windows.

### <a name="local-file-editing-with-open-editorfile"></a>Lokaal bestand bewerken met Open-EditorFile

Met de PowerShell-extensie voor VSCode gestart en de geïntegreerde PowerShell-Console hebt geopend, kunnen we typen `Open-EditorFile foo.ps1` of `psedit foo.ps1` lokale foo.ps1 bestand rechts in de editor te openen.

![Open-EditorFile foo.ps1 werkt lokaal](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> Het bestand `foo.ps1` moet al bestaan.

Van daaruit kunnen we:

- Onderbrekingspunten toevoegen aan de tussenruimte

  ![onderbrekingspunt naar rugmarge toevoegen](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- Druk op F5 om op te sporen in het PowerShell-script.

  ![het lokale PowerShell-script-foutopsporing](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

Tijdens het opsporen van fouten, kunt u communiceren met de console voor foutopsporing, bekijk de variabelen in het bereik aan de linkerkant en alle andere standard hulpmiddelen voor foutopsporing.

### <a name="remote-file-editing-with-open-editorfile"></a>Extern bestand bewerken met Open-EditorFile

Nu gaan we krijgen tot externe bestand bewerken en het opsporen van fouten. De stappen zijn vrijwel hetzelfde, wordt er slechts één wat die we moeten eerst doen - opgeven van onze PowerShell-sessie met de externe server.

Er is een cmdlet voor om dit te doen. Dit heet `Enter-PSSession`.

De watered omlaag uitleg van de cmdlet is:

- `Enter-PSSession -ComputerName foo` Hiermee wordt een sessie via WinRM gestart
- `Enter-PSSession -ContainerId foo` en `Enter-PSSession -VmId foo` een sessie via PowerShell Direct starten
- `Enter-PSSession -HostName foo` Hiermee wordt een sessie via SSH gestart

Zie voor meer informatie de documentatie voor [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

Daar gaan we in Mac OS een Ubuntu-VM in Azure, we SSH gebruiken voor externe toegang.

Voer eerst in de geïntegreerde Console `Enter-PSSession`. U bent verbonden met de externe sessie wanneer `[<hostname>]` geeft tot aan de linkerkant van de opdrachtprompt.

![De aanroep naar de Enter-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

We kunnen nu dezelfde stappen doen als we een lokale-script bewerkt.

1. Voer `Open-EditorFile test.ps1` of `psedit test.ps1` openen van de externe `test.ps1` bestand

  ![Het bestand test.ps1 Open-EditorFile](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. Het bestand/set-onderbrekingspunten bewerken

   ![bewerken en onderbrekingspunten instellen](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. Foutopsporing (F5) het externe bestand starten

   ![foutopsporing van het externe bestand](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

Als u problemen hebt, kunt u problemen in openen de [GitHub-opslagplaats](https://github.com/powershell/vscode-powershell).
