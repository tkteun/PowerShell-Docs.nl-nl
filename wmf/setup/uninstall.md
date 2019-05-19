---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verwijderen van WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856187"
---
# <a name="uninstallation-instructions"></a>Verwijderen van de installatie-instructies

## <a name="using-command-prompt"></a>Met behulp van de opdrachtprompt

1. Open **opdrachtprompt.**
2. Voer de [startprogramma voor de zelfstandige versie van de Windows Update](https://support.microsoft.com/en-us/kb/934307) zoals hieronder wordt weergegeven:

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

1. Open **het Configuratiescherm.**
2. Open **programma's**en open vervolgens **een programma verwijderen.**
3. Klik op **geïnstalleerde updates weergeven.**
4. Selecteer **Windows Management Framework 5.0** uit de lijst met geïnstalleerde updates. Dit komt overeen met *KB3134758*, *KB3134759*, of *KB3134760*. Klik op **verwijderen.**
