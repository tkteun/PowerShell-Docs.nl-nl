---
title: Visual Studio Code gebruiken voor externe bewerking en foutopsporing
description: Visual Studio Code gebruiken voor externe bewerking en foutopsporing
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086664"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Visual Studio Code gebruiken voor externe bewerking en foutopsporing

Bedoeld voor degenen die bekend zijn met de ISE zijn misschien herinnert u zich dat u kunt uitvoeren `psedit file.ps1` rechtstreeks vanuit de geïntegreerde console bestanden - lokale of externe - te openen in de ISE.

Deze functie is ook beschikbaar in de PowerShell-extensie voor VSCode als het blijkt. Deze handleiding wordt beschreven hoe om dit te doen.

## <a name="prerequisites"></a>Vereisten

Deze handleiding wordt ervan uitgegaan dat u hebt:

- een externe bron (bijvoorbeeld: een virtuele machine, een container) dat u toegang tot hebt
- PowerShell die worden uitgevoerd op deze en de hostcomputer
- VSCode en de PowerShell-extensie voor VSCode

Deze functie werkt op Windows PowerShell en PowerShell Core.

Deze functie werkt ook bij het verbinden met een externe computer via WinRM, PowerShell Direct of SSH. Als u wilt gebruiken van SSH, maar met behulp van Windows, bekijk dan de [Win32-versie van SSH](https://github.com/PowerShell/Win32-OpenSSH)!

## <a name="lets-go"></a>We gaan

In deze sectie behandelen ik externe bewerken en foutopsporing van mijn MacBook Pro op een Ubuntu-VM in Azure wordt uitgevoerd. Ik kan niet worden met behulp van Windows, maar **het proces is identiek**.

### <a name="local-file-editing-with-open-editorfile"></a>Lokaal bestand bewerken met Open-EditorFile

Met de PowerShell-extensie voor VSCode gestart en de geïntegreerde PowerShell-Console hebt geopend, kunnen we typen `Open-EditorFile foo.ps1` of `psedit foo.ps1` lokale foo.ps1 bestand rechts in de editor te openen.

![Open-EditorFile foo.ps1 werkt lokaal](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 moet al bestaan.

Van daaruit kunnen we:

onderbrekingspunten toevoegen aan de extra ![onderbrekingspunten rugmarge toevoegen](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

en druk op F5 om op te sporen in het PowerShell-script.
![het lokale PowerShell-script-foutopsporing](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Tijdens het opsporen van fouten, kunt u communiceren met de console voor foutopsporing, bekijk de variabelen in het bereik aan de linkerkant en alle andere standard hulpmiddelen voor foutopsporing.

### <a name="remote-file-editing-with-open-editorfile"></a>Extern bestand bewerken met Open-EditorFile

Nu gaan we krijgen tot externe bestand bewerken en het opsporen van fouten. De stappen zijn vrijwel hetzelfde, wordt er slechts één wat die we moeten eerst doen - opgeven van onze PowerShell-sessie met de externe server.

Er is een cmdlet voor om dit te doen. Dit heet `Enter-PSSession`.

De watered omlaag uitleg van de cmdlet is:

- `Enter-PSSession -ComputerName foo` Hiermee wordt een sessie via WinRM gestart
- `Enter-PSSession -ContainerId foo` en `Enter-PSSession -VmId foo` een sessie via PowerShell Direct starten
- `Enter-PSSession -HostName foo` Hiermee wordt een sessie via SSH gestart

Voor meer informatie over `Enter-PSSession`, bekijk de documenten [hier](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Ik moet gebruikmaken van SSH voor externe toegang omdat ik in Mac OS een Ubuntu-VM in Azure.

Eerst in de geïntegreerde Console, gaan we onze Enter-PSSession uitvoeren. Weet u zeker dat u in de sessie bent omdat `[something]` worden weergegeven aan de linkerkant van de opdrachtprompt.

![De aanroep naar de Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

Van daaruit doen we de exacte stappen als wanneer we bezig was met het bewerken van een lokale script.

1. Voer `Open-EditorFile test.ps1` of `psedit test.ps1` openen van de externe `test.ps1` bestand ![Open-EditorFile het bestand test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Het bestand/set-onderbrekingspunten bewerken ![bewerken en onderbrekingspunten instellen](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Foutopsporing (F5) het externe bestand starten

![foutopsporing van het externe bestand](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

Dat is alles eenvoudig werkt dat.! We hopen dat deze handleiding wissen van vragen over externe foutopsporing en het bewerken van PowerShell in VSCode geholpen.

Als u problemen hebt, kunt u problemen melden [op de GitHub-opslagplaats](http://github.com/powershell/vscode-powershell).
