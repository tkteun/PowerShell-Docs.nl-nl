---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057510"
---
# <a name="uninstallation-instructions"></a>Verwijderen van de installatie-instructies

## <a name="using-command-prompt"></a>Met behulp van de opdrachtprompt
1.  Open **opdrachtprompt.**
2.  Voer de [startprogramma voor de zelfstandige versie van de Windows Update](https://support.microsoft.com/en-us/kb/934307) zoals hieronder wordt weergegeven:

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
2.  Open **programma's**en open vervolgens **een programma verwijderen.**
3.  Klik op **geïnstalleerde updates weergeven.**
4.  Selecteer **Windows Management Framework 5.0** uit de lijst met geïnstalleerde updates. Dit komt overeen met *KB3134758*, *KB3134759*, of *KB3134760*. Klik op **verwijderen.**
