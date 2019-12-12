---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Computerstatus wijzigen
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "70386287"
---
# <a name="changing-computer-state"></a>Computerstatus wijzigen

Als u een computer opnieuw wilt instellen in Windows Power shell, gebruikt u een standaard opdracht regel programma, WMI of CIM-klasse. Hoewel u Windows Power shell alleen gebruikt om het-hulp programma uit te voeren, leert u hoe u de energie status van een computer in Windows Power shell kunt wijzigen om een deel van de belang rijke informatie te zien over het werken met externe hulpprogram ma's in Windows Power shell.

## <a name="locking-a-computer"></a>Een computer vergren delen

De enige manier om een computer rechtstreeks te vergren delen met de standaard beschik bare hulpprogram ma's is het aanroepen van de functie **LockWorkStation ()** in **user32. dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Met deze opdracht wordt het werk station onmiddellijk vergrendeld. Er wordt gebruik gemaakt van *rundll32. exe*, dat Windows-dll's uitvoert (en de bibliotheken opslaat voor herhaalde gebruik) om user32. dll uit te voeren, een bibliotheek met Windows-beheer functies.

Wanneer u een werk station vergrendelt terwijl snelle gebruikers wisseling is ingeschakeld, zoals op Windows XP, wordt in de computer het aanmeldings scherm van de gebruiker weer gegeven in plaats van de scherm beveiliging van de huidige gebruiker.

Als u bepaalde sessies op een Terminal Server wilt afsluiten, gebruikt u het opdracht regel programma **tsshutdn. exe** .

## <a name="logging-off-the-current-session"></a>De huidige sessie afmelden

U kunt verschillende technieken gebruiken om u af te melden bij een sessie op het lokale systeem. De eenvoudigste manier is het gebruik van het opdracht regel programma Extern bureaublad/Terminal Services, **Afmelden. exe** (voor meer informatie, typt u bij de Windows Power shell-prompt **Afmelden/?** ). Als u de huidige actieve sessie wilt afmelden, typt u **Afmelden** zonder argumenten.

U kunt ook het hulp programma **shutdown. exe** gebruiken met de optie voor afmelden:

```
shutdown.exe -l
```

Een andere optie is om WMI te gebruiken. De klasse Win32_OperatingSystem heeft een Win32Shutdown-methode. Als de methode wordt aangeroepen met de vlag 0, wordt de afmelding gestart:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Voor meer informatie en om andere functies van de methode Win32Shutdown te vinden, raadpleegt u de methode Win32Shutdown van de klasse Win32_OperatingSystem in MSDN.

Ten slotte kunt u CIM gebruiken met dezelfde Win32_OperatingSystem-klasse zoals hierboven wordt beschreven in de WMI-methode.

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Afsluiten of opnieuw opstarten van een computer

Het afsluiten en opnieuw opstarten van computers zijn over het algemeen hetzelfde type taak. Hulpprogram ma's die een computer afsluiten, zullen deze doorgaans ook opnieuw starten en vice versa. Er zijn twee eenvoudige opties voor het opnieuw opstarten van een computer vanuit Windows Power shell. Gebruik de juiste argumenten van tsshutdn. exe of Shutdown. exe. U kunt gedetailleerde gebruiks gegevens verkrijgen van **tsshutdn. exe/?** of **shutdown. exe/?** .

U kunt ook de bewerkingen voor afsluiten en opnieuw opstarten rechtstreeks vanuit Windows Power shell uitvoeren.

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
