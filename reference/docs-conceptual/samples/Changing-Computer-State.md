---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Computerstatus wijzigen
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736910"
---
# <a name="changing-computer-state"></a>Computerstatus wijzigen

Als u een computer opnieuw wilt instellen in Power shell, gebruikt u een standaard opdracht regel programma, een WMI-of CIM-klasse.
Hoewel u Power shell alleen gebruikt om het-hulp programma uit te voeren, leert u hoe u de energie status van een computer kunt wijzigen in Power shell een aantal van de belang rijke informatie over het werken met externe hulpprogram ma's in Power shell.

## <a name="locking-a-computer"></a>Een computer vergren delen

De enige manier om een computer rechtstreeks te vergren delen met de standaard beschik bare hulpprogram ma's is het aanroepen van de functie **LockWorkStation ()** in **user32. dll**:

```powershell
rundll32.exe user32.dll,LockWorkStation
```

Met deze opdracht wordt het werk station onmiddellijk vergrendeld. Er wordt gebruik gemaakt van **rundll32. exe**, dat Windows-dll's uitvoert (en de bibliotheken opslaat voor herhaalde gebruik) om uit te voeren `user32.dll`, een bibliotheek met Windows-beheer functies.

Wanneer u een werk station vergrendelt terwijl snelle gebruikers wisseling is ingeschakeld, zoals op Windows XP, wordt in de computer het aanmeldings scherm van de gebruiker weer gegeven in plaats van de scherm beveiliging van de huidige gebruiker.

Als u bepaalde sessies op een Terminal Server wilt afsluiten, gebruikt u het opdracht regel programma **tsshutdn. exe** .

## <a name="logging-off-the-current-session"></a>De huidige sessie afmelden

U kunt verschillende technieken gebruiken om u af te melden bij een sessie op het lokale systeem. De eenvoudigste manier is het gebruik van het opdracht regel programma Extern bureaublad/Terminal Services, **Afmelden. exe** (Typ in het Power shell-prompt type `logoff /?`) voor meer informatie. Als u de huidige actieve sessie wilt afmelden `logoff` , typt u zonder argumenten.

U kunt ook het hulp programma **shutdown. exe** gebruiken met de optie voor afmelden:

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

Het afsluiten en opnieuw opstarten van computers zijn over het algemeen hetzelfde type taak. Hulpprogram ma's die een computer afsluiten, zullen deze doorgaans ook opnieuw starten en vice versa. Er zijn twee eenvoudige opties voor het opnieuw opstarten van een computer vanuit Power shell. Gebruik de juiste argumenten van **tsshutdn. exe** of **shutdown. exe** . U kunt gedetailleerde gebruiks gegevens ophalen van `tsshutdn.exe /?` of `shutdown.exe /?`.

U kunt ook de bewerkingen voor afsluiten en opnieuw opstarten rechtstreeks vanuit Power shell uitvoeren.

Gebruik de opdracht stop-computer om de computer af te sluiten.

```powershell
Stop-Computer
```

Gebruik de opdracht Restart-computer om het besturings systeem opnieuw op te starten

```powershell
Restart-Computer
```

Als u de computer direct opnieuw wilt opstarten, gebruikt u de para meter-Force.

```powershell
Restart-Computer -Force
```
