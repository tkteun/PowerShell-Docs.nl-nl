---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="uninstallation-instructions"></a>Instructies voor het verwijderen

## <a name="using-command-prompt"></a>Vanaf een opdrachtprompt
1.  Open **opdrachtprompt.**
2.  Voer de [Windows Update zelfstandige Launcher](https://support.microsoft.com/en-us/kb/934307) zoals hieronder wordt weergegeven:

Op Windows Server 2012 R2 en Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
On Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
Op Windows Server 2008 R2 SP1 en Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a>Via het Configuratiescherm
1.  Open **het Configuratiescherm.**
2.  Open **programma's**, open vervolgens **een programma verwijderen.**
3.  Klik op **geïnstalleerde updates weergeven.**
4.  Selecteer **Windows Management Framework 5.0** uit de lijst met geïnstalleerde updates. Dit komt overeen met *KB3134758*, *KB3134759*, of *KB3134760*. Klik op **verwijderen.**
