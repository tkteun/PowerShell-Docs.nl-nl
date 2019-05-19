---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen in foutopsporing voor PowerShell-scripts
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856173"
---
# <a name="improvements-in-powershell-script-debugging"></a>Verbeteringen in foutopsporing voor PowerShell-scripts

PowerShell 5.0 bevat verschillende verbeteringen die het opsporen van fouten.

## <a name="break-all"></a>Alle verbreken

De PowerShell-console en de PowerShell ISE nu kunt u in het foutopsporingsprogramma opsplitsen voor het uitvoeren van scripts. Dit werkt in zowel lokale als externe sessies.

In de console, drukt u op <kbd>Ctrl</kbd>+<kbd>verbreken</kbd>.

In ISE, drukt u op <kbd>Ctrl</kbd>+<kbd>B</kbd>, of gebruik de **Debug -> alle opsplitsen** -opdracht.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>Foutopsporing op afstand en extern bestand bewerken in PowerShell ISE

PowerShell ISE kunt u nu bestanden openen en bewerken in een externe sessie met de opdracht PSEdit.
U kunt bijvoorbeeld een bestand vanaf de opdrachtregel bewerken in een externe sessie als volgt openen:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Bovendien kunt u nu bewerken en opslaan van wijzigingen in een extern bestand dat automatisch wordt geopend in PowerShell ISE wanneer u een onderbrekingspunt bereikt. U kunt nu, fouten opsporen in een scriptbestand wordt uitgevoerd op een externe computer, het bestand te herstellen van een fout en voer het gewijzigde script bewerken.

## <a name="advanced-script-debugging"></a>Geavanceerde Script opsporen van fouten

Er zijn nieuwe, geavanceerde foutopsporing functies waarmee u kunnen koppelen aan een lokale computer-proces dat PowerShell is geladen en fouten opsporen in willekeurige runspaces in het proces.

### <a name="runspace-debugging"></a>Runspace foutopsporing

Er zijn nieuwe cmdlets zijn toegevoegd waarmee u de lijst met huidige runspaces in een proces en de PowerShell-console of de PowerShell ISE foutopsporingsprogramma koppelen aan deze runspace voor foutopsporing voor scripts kunt:

- Get-Runspace
- Debug-Runspace
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Koppelen aan het proces voor het hosten van PowerShell

U kunt nu koppelen aan het proces voor elke computer met PowerShell geladen. U doen dit door te voeren in een interactieve sessie met het hostproces. Zie voor meer informatie

- [Enter-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Exit-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
