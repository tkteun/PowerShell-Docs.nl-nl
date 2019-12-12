---
title: Visual Studio Code gebruiken voor externe bewerking en foutopsporing
description: Visual Studio Code gebruiken voor externe bewerking en foutopsporing
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67264025"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Visual Studio Code gebruiken voor externe bewerking en foutopsporing

Voor degenen die bekend zijn met de ISE, kunt u intrekken dat u `psedit file.ps1` kunt uitvoeren vanuit de geïntegreerde console om bestanden te openen-lokaal of extern-rechts in de ISE.

Deze functie is ook beschikbaar in de Power shell-uitbrei ding voor VSCode. In deze hand leiding wordt uitgelegd hoe u dit kunt doen.

## <a name="prerequisites"></a>Vereisten

In deze hand leiding wordt ervan uitgegaan dat u het volgende hebt:

- Een externe bron (bijvoorbeeld: een VM, een container) waartoe u toegang hebt
- Power shell wordt uitgevoerd op deze computer en de hostmachine
- VSCode en de Power shell-extensie voor VSCode

Deze functie werkt in Windows Power shell en Power shell core.

Deze functie werkt ook wanneer u verbinding maakt met een externe computer via WinRM, Power shell direct of SSH. Als u SSH wilt gebruiken, maar Windows gebruikt, raadpleegt u de [Win32-versie van SSH](https://github.com/PowerShell/Win32-OpenSSH)!

> [!IMPORTANT]
> De opdrachten `Open-EditorFile` en `psedit` werken alleen in de **Power shell-geïntegreerde console** die is gemaakt met de Power shell-uitbrei ding voor VSCode.

## <a name="usage-examples"></a>Gebruiks voorbeelden

In deze voor beelden ziet u het op afstand bewerken en fout opsporing van een MacBook Pro naar een Ubuntu VM die in azure wordt uitgevoerd. Het proces is identiek in Windows.

### <a name="local-file-editing-with-open-editorfile"></a>Lokaal bestand bewerken met open-EditorFile

Met de Power shell-extensie voor VSCode gestart en de Power shell-geïntegreerde console geopend, kunnen we `Open-EditorFile foo.ps1`-of `psedit foo.ps1` om het lokale bestand foo. ps1 rechtstreeks in de editor te openen.

![Open-EditorFile foo. ps1 werkt lokaal](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> De bestands `foo.ps1` moet al bestaan.

Vanaf daar kunnen we het volgende doen:

- Onderbrekings punten toevoegen aan de rugmarge

  ![onderbrekings punt toevoegen aan rugmarge](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- Druk op F5 om fouten op te sporen in het Power shell-script.

  ![fout opsporing van het lokale Power shell-script](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

Tijdens het opsporen van fouten kunt u communiceren met de console fout opsporing, de variabelen in het bereik aan de linkerkant bekijken en alle andere standaardfout opsporingsprogramma's.

### <a name="remote-file-editing-with-open-editorfile"></a>Externe bestands bewerking met open-EditorFile

Nu gaan we externe bestanden bewerken en fouten opsporen. De stappen zijn bijna hetzelfde, maar u moet eerst onze Power shell-sessie uitvoeren op de externe server.

Er is een cmdlet voor om dit te doen. Het wordt `Enter-PSSession`genoemd.

De niet-bevochtigde uitleg van de cmdlet is:

- `Enter-PSSession -ComputerName foo` start een sessie via WinRM
- een sessie `Enter-PSSession -ContainerId foo` en `Enter-PSSession -VmId foo` via Power shell direct
- `Enter-PSSession -HostName foo` start een sessie via SSH

Zie de documentatie voor [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)voor meer informatie.

Omdat we vanuit macOS naar een Ubuntu-VM in azure gaan, gebruiken we SSH voor externe communicatie.

Voer eerst in de geïntegreerde console het `Enter-PSSession`uit. U bent verbonden met de externe sessie wanneer `[<hostname>]` links van uw prompt wordt weer gegeven.

![Het aanroepen van ENTER-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

Nu kunnen we dezelfde stappen uitvoeren als voor het bewerken van een lokaal script.

1. Voer `Open-EditorFile test.ps1` of `psedit test.ps1` uit om het externe `test.ps1`-bestand te openen

  ![Open-EditorFile het bestand test. ps1](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. Het bestand of de set onderbrekings punten bewerken

   ![onderbrekings punten bewerken en instellen](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. Fout opsporing starten (F5) het externe bestand

   ![fout opsporing van het externe bestand](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

Als u problemen hebt, kunt u problemen openen in de [github-opslag plaats](https://github.com/powershell/vscode-powershell).
