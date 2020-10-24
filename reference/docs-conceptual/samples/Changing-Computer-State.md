---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Computerstatus wijzigen
description: Dit voor beeld laat zien hoe u via Power shell externe opdrachten kunt gebruiken om de configuratie van een computer te beheren.
ms.openlocfilehash: 341f29f24d7e4bd341ccc0954b16d4b75880678b
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500671"
---
# <a name="changing-computer-state"></a>Computerstatus wijzigen

Als u een computer opnieuw wilt instellen in Power shell, gebruikt u een standaard opdracht regel programma, WMI of een CIM-klasse.
Hoewel u Power shell alleen gebruikt om het-hulp programma uit te voeren, leert u hoe u de energie status van een computer kunt wijzigen in Power shell een aantal van de belang rijke informatie over het werken met externe hulpprogram ma's in Power shell.

## <a name="locking-a-computer"></a>Een computer vergren delen

De enige manier om een computer rechtstreeks te vergren delen met de standaard beschik bare hulpprogram ma's is door de functie **LockWorkStation ()** aan te roepen in **user32.dll**:

```powershell
rundll32.exe user32.dll,LockWorkStation
```

Met deze opdracht wordt het werk station onmiddellijk vergrendeld. Er wordt gebruikgemaakt van **rundll32.exe**, dat Windows-dll's uitvoert (en de bibliotheken opslaat voor herhaald gebruik) om uit te voeren `user32.dll` , een bibliotheek met Windows-beheer functies.

Wanneer u een werk station vergrendelt terwijl snelle gebruikers wisseling is ingeschakeld, zoals op Windows XP, wordt in de computer het aanmeldings scherm van de gebruiker weer gegeven in plaats van de scherm beveiliging van de huidige gebruiker.

Als u bepaalde sessies op een Terminal Server wilt afsluiten, gebruikt u het opdracht regel programma **tsshutdn.exe** .

## <a name="logging-off-the-current-session"></a>De huidige sessie afmelden

U kunt verschillende technieken gebruiken om u af te melden bij een sessie op het lokale systeem. De eenvoudigste manier is het gebruik van het opdracht regel programma Extern bureaublad/Terminal Services, **logoff.exe** (voor meer informatie, typt u in het Power shell-prompt type `logoff /?` ). Als u de huidige actieve sessie wilt afmelden, typt u `logoff` zonder argumenten.

U kunt het hulp programma **shutdown.exe** ook gebruiken met de optie voor afmelden:

```powershell
shutdown.exe -l
```

Een andere optie is om WMI te gebruiken. De **Win32_OperatingSystem** klasse heeft een **afsluit** methode.
Als de methode wordt aangeroepen met de vlag 0, wordt de afmelding gestart:

Zie voor meer informatie over de **afsluit** methode de [methode Shutdown van de klasse Win32_OperatingSystem](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Afsluiten of opnieuw opstarten van een computer

Het afsluiten en opnieuw opstarten van computers zijn over het algemeen hetzelfde type taak. Hulpprogram ma's die een computer afsluiten, zullen deze doorgaans ook opnieuw starten en vice versa. Er zijn twee eenvoudige opties voor het opnieuw opstarten van een computer vanuit Power shell. Gebruik **tsshutdn.exe** of **shutdown.exe** met de juiste argumenten. U kunt gedetailleerde gebruiks gegevens ophalen van `tsshutdn.exe /?` of `shutdown.exe /?` .

U kunt ook de bewerkingen voor afsluiten en opnieuw opstarten rechtstreeks vanuit Power shell uitvoeren.

Als u de computer wilt afsluiten, gebruikt u de opdracht Stop-Computer

```powershell
Stop-Computer
```

Als u het besturings systeem opnieuw wilt starten, gebruikt u de opdracht Restart-Computer

```powershell
Restart-Computer
```

Als u de computer direct opnieuw wilt opstarten, gebruikt u de para meter-Force.

```powershell
Restart-Computer -Force
```
