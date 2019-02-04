---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 22a027ebc97e15075980bc77ce272d8ecdae0b5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686990"
---
# <a name="improvements-in-powershell-script-debugging"></a>Verbeteringen in foutopsporing voor PowerShell-scripts

Een aantal verbeteringen aangebracht in PowerShell 5.0 om de foutopsporing ervaring te verbeteren:

## <a name="break-all"></a>Alle verbreken

De PowerShell-console en de Windows PowerShell ISE nu kunt u in het foutopsporingsprogramma opsplitsen voor het uitvoeren van scripts. Dit werkt in zowel lokale als externe sessies.

In de console, drukt u op **Ctrl + Break**.

In ISE, drukt u op **Ctrl + B**, of gebruik de **Debug -> alle opsplitsen** -opdracht.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Foutopsporing op afstand en extern bestand bewerken in Windows PowerShell ISE

Windows PowerShell ISE kunt u nu bestanden openen en bewerken in een externe sessie met de opdracht PSEdit.
U kunt bijvoorbeeld een bestand vanaf de opdrachtregel bewerken in een externe sessie als volgt openen:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Bovendien kunt u nu bewerken en opslaan van wijzigingen in een extern bestand dat automatisch wordt geopend in Windows PowerShell ISE wanneer u een onderbrekingspunt bereikt.
U kunt nu, fouten opsporen in een scriptbestand wordt uitgevoerd op een externe computer, het bestand te herstellen van een fout en voer het gewijzigde script bewerken.

## <a name="advanced-script-debugging"></a>Geavanceerde Script opsporen van fouten

Er zijn nieuwe, geavanceerde foutopsporing functies waarmee u kunnen koppelen aan een lokale computer-proces dat Windows PowerShell is geladen en fouten opsporen in willekeurige runspaces in het proces.

### <a name="runspace-debugging"></a>Runspace foutopsporing

Er zijn nieuwe cmdlets zijn toegevoegd waarmee u de lijst met huidige runspaces in een proces en de Windows PowerShell-console of ISE foutopsporingsprogramma koppelen aan deze runspace voor foutopsporing voor scripts kunt:

-   Get-Runspace
-   Debug-Runspace
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Koppelen aan het proces voor het hosten van PowerShell

U kunt nu koppelen aan het proces voor elke computer met Windows PowerShell is geladen. U doen dit door te voeren in een interactieve sessie met het proces, vergelijkbaar met hoe u in een interactieve externe sessie invoeren op de Enter-PSSession cmdlet uit te voeren:

-   Enter-PSHostProcess
-   Exit-PSHostProcess
