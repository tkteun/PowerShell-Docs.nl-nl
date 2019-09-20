---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: WMF 5.0 verwijderen
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145213"
---
# <a name="uninstallation-instructions"></a>Instructies voor verwijderen

## <a name="using-command-prompt"></a>Opdracht prompt gebruiken

1. Open de **opdracht prompt.**
2. Voer de [Windows Update zelfstandige Launcher](https://support.microsoft.com/en-us/kb/934307) uit, zoals hieronder wordt weer gegeven:

In Windows Server 2012 R2 en Windows 8,1:

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

## <a name="using-control-panel"></a>Configuratie scherm gebruiken

1. Open **het configuratie scherm.**
2. Open **Program ma's**en open vervolgens **een programma verwijderen.**
3. Klik op **geïnstalleerde updates weer geven.**
4. Selecteer **Windows Management Framework 5,0** in de lijst met geïnstalleerde updates. Dit komt overeen met *KB3134758*, *KB3134759*of *KB3134760*. Klik op **verwijderen.**
