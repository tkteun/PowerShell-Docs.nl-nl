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
# <a name="changing-computer-state"></a><span data-ttu-id="cc83f-103">Computerstatus wijzigen</span><span class="sxs-lookup"><span data-stu-id="cc83f-103">Changing Computer State</span></span>

<span data-ttu-id="cc83f-104">Als u wilt instellen op een computer in Windows PowerShell, een standaard opdrachtregelprogramma of een WMI-klasse te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cc83f-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="cc83f-105">Hoewel u Windows PowerShell werkt alleen voor het hulpprogramma uitvoert, leren van het wijzigen van de energiestatus van een computer in Windows PowerShell ziet u enkele van de belangrijke informatie over het werken met externe hulpprogramma's in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc83f-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

### <a name="locking-a-computer"></a><span data-ttu-id="cc83f-106">Vergrendelen van een Computer</span><span class="sxs-lookup"><span data-stu-id="cc83f-106">Locking a Computer</span></span>

<span data-ttu-id="cc83f-107">De enige manier om het vergrendelen van een computer rechtstreeks met de standaard beschikbare hulpprogramma's om aan te roepen is de **LockWorkstation()** werken in **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="cc83f-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="cc83f-108">Met deze opdracht wordt onmiddellijk vergrendeld voor het werkstation.</span><span class="sxs-lookup"><span data-stu-id="cc83f-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="cc83f-109">Hierbij *rundll32.exe*, welke dll's van Windows wordt uitgevoerd (en hun bibliotheken voor herhaalde gebruik slaat) user32.dll, een bibliotheek van Windows-beheerfuncties uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="cc83f-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="cc83f-110">Wanneer u vergrendelen een werkstation terwijl snelle gebruikerswisseling is ingeschakeld, zoals op Windows XP, verschijnt de computer het aanmeldingsscherm van de gebruiker in plaats van de huidige gebruiker de screensaver wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="cc83f-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="cc83f-111">Als u wilt afsluiten bepaalde sessies op een Terminal Server, gebruiken de **tsshutdn.exe** opdrachtregelprogramma.</span><span class="sxs-lookup"><span data-stu-id="cc83f-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

### <a name="logging-off-the-current-session"></a><span data-ttu-id="cc83f-112">De huidige sessie afmelden</span><span class="sxs-lookup"><span data-stu-id="cc83f-112">Logging Off the Current Session</span></span>

<span data-ttu-id="cc83f-113">U kunt verschillende andere technieken worden afgemeld bij een sessie op het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="cc83f-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="cc83f-114">De eenvoudigste manier is om met het hulpprogramma voor extern bureaublad/Terminal Services **logoff.exe** (Typ voor meer informatie bij de Windows PowerShell-prompt **Afmelden /?**).</span><span class="sxs-lookup"><span data-stu-id="cc83f-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="cc83f-115">De huidige actieve sessie afmelden, typ **Afmelden** zonder argumenten.</span><span class="sxs-lookup"><span data-stu-id="cc83f-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="cc83f-116">U kunt ook de **shutdown.exe** hulpprogramma uit met de optie Afmelden:</span><span class="sxs-lookup"><span data-stu-id="cc83f-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="cc83f-117">Een derde optie is het gebruik van WMI.</span><span class="sxs-lookup"><span data-stu-id="cc83f-117">A third option is to use WMI.</span></span> <span data-ttu-id="cc83f-118">De Win32_OperatingSystem-klasse heeft een methode Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="cc83f-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="cc83f-119">Aanroepen van de methode met de vlag 0 initieert afmelden:</span><span class="sxs-lookup"><span data-stu-id="cc83f-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="cc83f-120">Zie 'Win32Shutdown methode van de Win32_OperatingSystem Class' in MSDN voor meer informatie en om andere onderdelen van de methode Win32Shutdown te vinden.</span><span class="sxs-lookup"><span data-stu-id="cc83f-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

### <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="cc83f-121">Afsluiten of opnieuw opstarten van een Computer</span><span class="sxs-lookup"><span data-stu-id="cc83f-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="cc83f-122">Afgesloten en opnieuw starten van de computers zijn meestal hetzelfde type taak.</span><span class="sxs-lookup"><span data-stu-id="cc83f-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="cc83f-123">Hulpprogramma's die een computer afsluiten dan in het algemeen start ook, en vice versa.</span><span class="sxs-lookup"><span data-stu-id="cc83f-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="cc83f-124">Er zijn twee eenvoudige opties voor het opnieuw opstarten van een computer uit de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc83f-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="cc83f-125">Tsshutdn.exe of Shutdown.exe gebruiken met de juiste argumenten.</span><span class="sxs-lookup"><span data-stu-id="cc83f-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="cc83f-126">Krijgt u gedetailleerde informatie over het van gebruiksinformatie van **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="cc83f-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="cc83f-127">of **shutdown.exe /?**.</span><span class="sxs-lookup"><span data-stu-id="cc83f-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="cc83f-128">U kunt ook afsluiten en opnieuw opstarten van bewerkingen met behulp van **Win32_OperatingSystem** rechtstreeks vanuit Windows PowerShell ook.</span><span class="sxs-lookup"><span data-stu-id="cc83f-128">You can also perform shutdown and restart operations by using **Win32_OperatingSystem** directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="cc83f-129">Als u wilt de computer afsluiten, gebruikt u de methode Win32Shutdown met de **1** vlag.</span><span class="sxs-lookup"><span data-stu-id="cc83f-129">To shut down the computer, use the Win32Shutdown method with the **1** flag.</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(1)
```

<span data-ttu-id="cc83f-130">Als u wilt het besturingssysteem opnieuw te starten, gebruikt u de methode Win32Shutdown met de **2** vlag.</span><span class="sxs-lookup"><span data-stu-id="cc83f-130">To restart the operating system, use the Win32Shutdown method with the **2** flag.</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(2)
```