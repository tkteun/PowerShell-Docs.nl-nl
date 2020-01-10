---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Computerstatus wijzigen
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736910"
---
# <a name="changing-computer-state"></a><span data-ttu-id="8ef05-103">Computerstatus wijzigen</span><span class="sxs-lookup"><span data-stu-id="8ef05-103">Changing Computer State</span></span>

<span data-ttu-id="8ef05-104">Als u een computer opnieuw wilt instellen in Power shell, gebruikt u een standaard opdracht regel programma, een WMI-of CIM-klasse.</span><span class="sxs-lookup"><span data-stu-id="8ef05-104">To reset a computer in PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span>
<span data-ttu-id="8ef05-105">Hoewel u Power shell alleen gebruikt om het-hulp programma uit te voeren, leert u hoe u de energie status van een computer kunt wijzigen in Power shell een aantal van de belang rijke informatie over het werken met externe hulpprogram ma's in Power shell.</span><span class="sxs-lookup"><span data-stu-id="8ef05-105">Although you are using PowerShell only to run the tool, learning how to change a computer's power state in PowerShell illustrates some of the important details about working with external tools in PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="8ef05-106">Een computer vergren delen</span><span class="sxs-lookup"><span data-stu-id="8ef05-106">Locking a Computer</span></span>

<span data-ttu-id="8ef05-107">De enige manier om een computer rechtstreeks te vergren delen met de standaard beschik bare hulpprogram ma's is het aanroepen van de functie **LockWorkStation ()** in **user32. dll**:</span><span class="sxs-lookup"><span data-stu-id="8ef05-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```powershell
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="8ef05-108">Met deze opdracht wordt het werk station onmiddellijk vergrendeld.</span><span class="sxs-lookup"><span data-stu-id="8ef05-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="8ef05-109">Er wordt gebruik gemaakt van **rundll32. exe**, dat Windows-dll's uitvoert (en de bibliotheken opslaat voor herhaalde gebruik) om `user32.dll`uit te voeren, een bibliotheek met Windows-beheer functies.</span><span class="sxs-lookup"><span data-stu-id="8ef05-109">It uses **rundll32.exe**, which runs Windows DLLs (and saves their libraries for repeated use) to run `user32.dll`, a library of Windows management functions.</span></span>

<span data-ttu-id="8ef05-110">Wanneer u een werk station vergrendelt terwijl snelle gebruikers wisseling is ingeschakeld, zoals op Windows XP, wordt in de computer het aanmeldings scherm van de gebruiker weer gegeven in plaats van de scherm beveiliging van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="8ef05-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="8ef05-111">Als u bepaalde sessies op een Terminal Server wilt afsluiten, gebruikt u het opdracht regel programma **tsshutdn. exe** .</span><span class="sxs-lookup"><span data-stu-id="8ef05-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="8ef05-112">De huidige sessie afmelden</span><span class="sxs-lookup"><span data-stu-id="8ef05-112">Logging Off the Current Session</span></span>

<span data-ttu-id="8ef05-113">U kunt verschillende technieken gebruiken om u af te melden bij een sessie op het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="8ef05-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="8ef05-114">De eenvoudigste manier is het gebruik van het opdracht regel programma Extern bureaublad/Terminal Services, **Logoff. exe** (Typ `logoff /?`in het Power shell-venster voor meer informatie).</span><span class="sxs-lookup"><span data-stu-id="8ef05-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the PowerShell prompt, type `logoff /?`).</span></span> <span data-ttu-id="8ef05-115">Als u de huidige actieve sessie wilt afmelden, typt u `logoff` zonder argumenten.</span><span class="sxs-lookup"><span data-stu-id="8ef05-115">To log off the current active session, type `logoff` with no arguments.</span></span>

<span data-ttu-id="8ef05-116">U kunt ook het hulp programma **shutdown. exe** gebruiken met de optie voor afmelden:</span><span class="sxs-lookup"><span data-stu-id="8ef05-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```powershell
shutdown.exe -l
```

<span data-ttu-id="8ef05-117">Een andere optie is om WMI te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8ef05-117">Another option is to use WMI.</span></span> <span data-ttu-id="8ef05-118">De **Win32_OperatingSystem** klasse heeft een **afsluit** methode.</span><span class="sxs-lookup"><span data-stu-id="8ef05-118">The **Win32_OperatingSystem** class has a **Shutdown** method.</span></span>
<span data-ttu-id="8ef05-119">Als de methode wordt aangeroepen met de vlag 0, wordt de afmelding gestart:</span><span class="sxs-lookup"><span data-stu-id="8ef05-119">Invoking the method with the 0 flag initiates logoff:</span></span>

<span data-ttu-id="8ef05-120">Zie voor meer informatie over de **afsluit** methode de [methode Shutdown van de klasse Win32_OperatingSystem](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span><span class="sxs-lookup"><span data-stu-id="8ef05-120">For more information about the **Shutdown** method, see [Shutdown method of the Win32_OperatingSystem class](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span></span>

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="8ef05-121">Afsluiten of opnieuw opstarten van een computer</span><span class="sxs-lookup"><span data-stu-id="8ef05-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="8ef05-122">Het afsluiten en opnieuw opstarten van computers zijn over het algemeen hetzelfde type taak.</span><span class="sxs-lookup"><span data-stu-id="8ef05-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="8ef05-123">Hulpprogram ma's die een computer afsluiten, zullen deze doorgaans ook opnieuw starten en vice versa.</span><span class="sxs-lookup"><span data-stu-id="8ef05-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="8ef05-124">Er zijn twee eenvoudige opties voor het opnieuw opstarten van een computer vanuit Power shell.</span><span class="sxs-lookup"><span data-stu-id="8ef05-124">There are two straightforward options for restarting a computer from PowerShell.</span></span> <span data-ttu-id="8ef05-125">Gebruik de juiste argumenten van **tsshutdn. exe** of **shutdown. exe** .</span><span class="sxs-lookup"><span data-stu-id="8ef05-125">Use either **tsshutdn.exe** or **shutdown.exe** with appropriate arguments.</span></span> <span data-ttu-id="8ef05-126">U kunt gedetailleerde gebruiks gegevens verkrijgen van `tsshutdn.exe /?` of `shutdown.exe /?`.</span><span class="sxs-lookup"><span data-stu-id="8ef05-126">You can get detailed usage information from `tsshutdn.exe /?` or `shutdown.exe /?`.</span></span>

<span data-ttu-id="8ef05-127">U kunt ook de bewerkingen voor afsluiten en opnieuw opstarten rechtstreeks vanuit Power shell uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="8ef05-127">You can also perform shutdown and restart operations directly from PowerShell as well.</span></span>

<span data-ttu-id="8ef05-128">Gebruik de opdracht stop-computer om de computer af te sluiten.</span><span class="sxs-lookup"><span data-stu-id="8ef05-128">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="8ef05-129">Gebruik de opdracht Restart-computer om het besturings systeem opnieuw op te starten</span><span class="sxs-lookup"><span data-stu-id="8ef05-129">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="8ef05-130">Als u de computer direct opnieuw wilt opstarten, gebruikt u de para meter-Force.</span><span class="sxs-lookup"><span data-stu-id="8ef05-130">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
