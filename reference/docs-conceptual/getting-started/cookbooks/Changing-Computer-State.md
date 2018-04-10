---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Computerstatus wijzigen
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: 3d3983c6d9e9b11db62bd71805da51be83331fdb
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="changing-computer-state"></a>Computerstatus wijzigen

Als u wilt instellen op een computer in Windows PowerShell, een standaard opdrachtregelprogramma of een WMI-klasse te gebruiken. Hoewel u Windows PowerShell werkt alleen voor het hulpprogramma uitvoert, leren van het wijzigen van de energiestatus van een computer in Windows PowerShell ziet u enkele van de belangrijke informatie over het werken met externe hulpprogramma's in Windows PowerShell.

### <a name="locking-a-computer"></a>Vergrendelen van een Computer

De enige manier om het vergrendelen van een computer rechtstreeks met de standaard beschikbare hulpprogramma's om aan te roepen is de **LockWorkstation()** werken in **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Met deze opdracht wordt onmiddellijk vergrendeld voor het werkstation. Hierbij *rundll32.exe*, welke dll's van Windows wordt uitgevoerd (en hun bibliotheken voor herhaalde gebruik slaat) user32.dll, een bibliotheek van Windows-beheerfuncties uitvoeren.

Wanneer u vergrendelen een werkstation terwijl snelle gebruikerswisseling is ingeschakeld, zoals op Windows XP, verschijnt de computer het aanmeldingsscherm van de gebruiker in plaats van de huidige gebruiker de screensaver wordt gestart.

Als u wilt afsluiten bepaalde sessies op een Terminal Server, gebruiken de **tsshutdn.exe** opdrachtregelprogramma.

### <a name="logging-off-the-current-session"></a>De huidige sessie afmelden

U kunt verschillende andere technieken worden afgemeld bij een sessie op het lokale systeem. De eenvoudigste manier is om met het hulpprogramma voor extern bureaublad/Terminal Services **logoff.exe** (Typ voor meer informatie bij de Windows PowerShell-prompt **Afmelden /?**). De huidige actieve sessie afmelden, typ **Afmelden** zonder argumenten.

U kunt ook de **shutdown.exe** hulpprogramma uit met de optie Afmelden:

```
shutdown.exe -l
```

Een derde optie is het gebruik van WMI. De Win32_OperatingSystem-klasse heeft een methode Win32Shutdown. Aanroepen van de methode met de vlag 0 initieert afmelden:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Zie 'Win32Shutdown methode van de Win32_OperatingSystem Class' in MSDN voor meer informatie en om andere onderdelen van de methode Win32Shutdown te vinden.

### <a name="shutting-down-or-restarting-a-computer"></a>Afsluiten of opnieuw opstarten van een Computer

Afgesloten en opnieuw starten van de computers zijn meestal hetzelfde type taak. Hulpprogramma's die een computer afsluiten dan in het algemeen start ook, en vice versa. Er zijn twee eenvoudige opties voor het opnieuw opstarten van een computer uit de Windows PowerShell. Tsshutdn.exe of Shutdown.exe gebruiken met de juiste argumenten. Krijgt u gedetailleerde informatie over het van gebruiksinformatie van **tsshutdn.exe /?** of **shutdown.exe /?**.

U kunt ook afsluiten en opnieuw opstarten van bewerkingen met behulp van **Win32_OperatingSystem** rechtstreeks vanuit Windows PowerShell ook.

Als u wilt de computer afsluiten, gebruikt u de methode Win32Shutdown met de **1** vlag.

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(1)
```

Als u wilt het besturingssysteem opnieuw te starten, gebruikt u de methode Win32Shutdown met de **2** vlag.

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(2)
```