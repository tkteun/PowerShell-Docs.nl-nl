---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Computerstatus wijzigen
ms.openlocfilehash: 80692ad7c56aa13e55d4997cfec289ffb3605458
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030277"
---
# <a name="changing-computer-state"></a><span data-ttu-id="060a6-103">Computerstatus wijzigen</span><span class="sxs-lookup"><span data-stu-id="060a6-103">Changing Computer State</span></span>

<span data-ttu-id="060a6-104">Als u wilt herstellen op een computer in Windows PowerShell, een standaard opdrachtregelprogramma of een WMI-klasse te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="060a6-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="060a6-105">Hoewel u Windows PowerShell gebruiken om alleen uit te voeren van het hulpprogramma, leren hoe u kunt de energiestatus van de computer in Windows PowerShell wijzigen ziet u enkele van de belangrijke informatie over het werken met externe hulpprogramma's in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="060a6-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="060a6-106">Vergrendelen van een Computer</span><span class="sxs-lookup"><span data-stu-id="060a6-106">Locking a Computer</span></span>

<span data-ttu-id="060a6-107">De enige manier om het vergrendelen van een computer rechtstreeks met de tools die standaard beschikbaar is om aan te roepen de **LockWorkstation()** werken in **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="060a6-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="060a6-108">Met deze opdracht wordt onmiddellijk vergrendeld voor het werkstation.</span><span class="sxs-lookup"><span data-stu-id="060a6-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="060a6-109">Hierbij *rundll32.exe*, die wordt uitgevoerd Windows dll-bestanden (en slaat de bibliotheken voor herhaalde gebruik) om uit te voeren user32.dll, een bibliotheek met functies voor het beheer van Windows.</span><span class="sxs-lookup"><span data-stu-id="060a6-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="060a6-110">Wanneer u vergrendelen een werkstation snelle gebruikerswisseling is ingeschakeld, zoals op Windows XP, toont de computer het aanmeldingsscherm van de gebruiker in plaats van vanaf de screensaver van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="060a6-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="060a6-111">Als u wilt afsluiten bepaalde sessies op een Terminal Server, gebruikt u de **tsshutdn.exe** opdrachtregel-hulpprogramma.</span><span class="sxs-lookup"><span data-stu-id="060a6-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="060a6-112">De huidige sessie afmelden</span><span class="sxs-lookup"><span data-stu-id="060a6-112">Logging Off the Current Session</span></span>

<span data-ttu-id="060a6-113">U kunt meerdere verschillende technieken worden afgemeld bij een sessie op het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="060a6-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="060a6-114">De eenvoudigste manier is het gebruik van het opdrachtregelprogramma van extern bureaublad/Terminal Services **logoff.exe** (voor meer informatie bij de Windows PowerShell-prompt, typ **Afmelden /?** ).</span><span class="sxs-lookup"><span data-stu-id="060a6-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="060a6-115">De huidige actieve sessie afmelden, typt u **Afmelden** zonder argumenten.</span><span class="sxs-lookup"><span data-stu-id="060a6-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="060a6-116">U kunt ook de **shutdown.exe** hulpprogramma met de optie voor afmelden:</span><span class="sxs-lookup"><span data-stu-id="060a6-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="060a6-117">Een derde optie is het gebruik van WMI.</span><span class="sxs-lookup"><span data-stu-id="060a6-117">A third option is to use WMI.</span></span> <span data-ttu-id="060a6-118">De Win32_OperatingSystem-klasse heeft een methode Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="060a6-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="060a6-119">Aanroepen van de methode met de vlag 0 initieert afmelden:</span><span class="sxs-lookup"><span data-stu-id="060a6-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="060a6-120">Zie "Win32Shutdown methode van de Win32_OperatingSystem Class" in MSDN voor meer informatie en andere functies van de methode Win32Shutdown vinden.</span><span class="sxs-lookup"><span data-stu-id="060a6-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="060a6-121">Afsluiten of opnieuw opstarten van een Computer</span><span class="sxs-lookup"><span data-stu-id="060a6-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="060a6-122">Afgesloten en opnieuw opstarten van computers worden in het algemeen dezelfde gegevenstypen van de taak.</span><span class="sxs-lookup"><span data-stu-id="060a6-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="060a6-123">Hulpprogramma's die een computer afsluiten dan in het algemeen start ook, en vice versa.</span><span class="sxs-lookup"><span data-stu-id="060a6-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="060a6-124">Er zijn twee eenvoudige opties voor opnieuw opstarten van een computer vanuit Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="060a6-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="060a6-125">Tsshutdn.exe of Shutdown.exe gebruiken met de juiste argumenten.</span><span class="sxs-lookup"><span data-stu-id="060a6-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="060a6-126">Krijgt u gedetailleerde gebruiksinformatie van **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="060a6-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="060a6-127">of **shutdown.exe /?** .</span><span class="sxs-lookup"><span data-stu-id="060a6-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="060a6-128">U kunt ook afsluiten en opnieuw starten van bewerkingen rechtstreeks vanuit Windows PowerShell ook.</span><span class="sxs-lookup"><span data-stu-id="060a6-128">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="060a6-129">Als u wilt afsluiten de computer, gebruikt u de opdracht Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="060a6-129">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="060a6-130">Als u wilt het besturingssysteem opnieuw hebt opgestart, gebruikt u de opdracht Computer opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="060a6-130">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="060a6-131">Als u wilt afdwingen dat een onmiddellijk opnieuw opstarten van de computer, gebruikt u de parameter - Force.</span><span class="sxs-lookup"><span data-stu-id="060a6-131">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
