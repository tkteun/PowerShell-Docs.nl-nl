---
ms.date: 06/12/2017
title: WMF 5.0 verwijderen
description: In dit artikel wordt uitgelegd hoe u WMF van oudere versies van Windows kunt verwijderen.
ms.openlocfilehash: d8078ea918db2c1cf9a7ddd6ea8d1413b593c0ff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660803"
---
# <a name="uninstallation-instructions"></a>Instructies voor verwijderen

## <a name="using-command-prompt"></a>Opdracht prompt gebruiken

1. Open de **opdracht prompt.**
2. Voer de [Windows Update zelfstandige Launcher](https://support.microsoft.com/kb/934307) uit, zoals hieronder wordt weer gegeven:

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
2. Open **Program ma's** en open vervolgens **een programma verwijderen.**
3. Klik op **geïnstalleerde updates weer geven.**
4. Selecteer **Windows Management Framework 5,0** in de lijst met geïnstalleerde updates. Dit komt overeen met *KB3134758* , *KB3134759* of *KB3134760* . Klik op **verwijderen.**
