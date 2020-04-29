---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen in foutopsporing voor PowerShell-scripts
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71145178"
---
# <a name="improvements-in-powershell-script-debugging"></a>Verbeteringen in foutopsporing voor PowerShell-scripts

Power shell 5,0 bevat verschillende verbeteringen voor het verbeteren van de fout opsporing.

## <a name="break-all"></a>Alles onderbreken

Met de Power shell-console en Power shell ISE kunt u nu opdelen in het fout opsporingsprogramma voor het uitvoeren van scripts. Dit werkt in zowel lokale als externe sessies.

Druk op <kbd>CTRL</kbd>+-<kbd>afbreek</kbd>punt in de-console.

Druk in ISE op <kbd>CTRL</kbd>+<kbd>B</kbd>, of gebruik de opdracht **debug-> Restore all** menu.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>Externe fout opsporing en externe bestands bewerking in Power shell ISE

Met Power shell ISE kunt u nu bestanden in een externe sessie openen en bewerken door de opdracht PSEdit uit te voeren.
U kunt bijvoorbeeld een bestand openen voor bewerking vanaf de opdracht regel in een externe sessie als volgt:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Daarnaast kunt u nu wijzigingen bewerken en opslaan in een extern bestand dat automatisch wordt geopend in Power shell ISE wanneer u een onderbrekings punt bereikt. U kunt nu fouten opsporen in een script bestand dat wordt uitgevoerd op een externe computer, het bestand bewerken om een fout op te lossen en vervolgens het gewijzigde script opnieuw uitvoeren.

## <a name="advanced-script-debugging"></a>Geavanceerde script fout opsporing

Er zijn nieuwe geavanceerde functies voor fout opsporing waarmee u kunt koppelen aan elk lokaal computer proces dat Power Shell heeft geladen en waarmee wille keurige runspaces in dat proces worden opgespoord.

### <a name="runspace-debugging"></a>Fout opsporing runs Pace

Er zijn nieuwe cmdlets toegevoegd waarmee u de huidige runspaces in een proces kunt weer geven en de Power shell-console of Power shell ISE-fout opsporingsprogramma kunt koppelen aan die runs Pace voor fout opsporing in scripts:

- Get-runs Pace
- Fout opsporing-runs Pace
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Koppelen aan proces hosting-Power shell

U kunt nu koppelen aan elk computer proces dat Power Shell heeft geladen. U doet dit door in te voeren in een interactieve sessie met het hostproces. Zie voor meer informatie:

- [Enter-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Afsluiten-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
