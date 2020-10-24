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
# <a name="changing-computer-state"></a><span data-ttu-id="b1a4d-104">Computerstatus wijzigen</span><span class="sxs-lookup"><span data-stu-id="b1a4d-104">Changing Computer State</span></span>

<span data-ttu-id="b1a4d-105">Als u een computer opnieuw wilt instellen in Power shell, gebruikt u een standaard opdracht regel programma, WMI of een CIM-klasse.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-105">To reset a computer in PowerShell, use either a standard command-line tool, WMI, or a CIM class.</span></span>
<span data-ttu-id="b1a4d-106">Hoewel u Power shell alleen gebruikt om het-hulp programma uit te voeren, leert u hoe u de energie status van een computer kunt wijzigen in Power shell een aantal van de belang rijke informatie over het werken met externe hulpprogram ma's in Power shell.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-106">Although you are using PowerShell only to run the tool, learning how to change a computer's power state in PowerShell illustrates some of the important details about working with external tools in PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="b1a4d-107">Een computer vergren delen</span><span class="sxs-lookup"><span data-stu-id="b1a4d-107">Locking a Computer</span></span>

<span data-ttu-id="b1a4d-108">De enige manier om een computer rechtstreeks te vergren delen met de standaard beschik bare hulpprogram ma's is door de functie **LockWorkStation ()** aan te roepen in **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="b1a4d-108">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```powershell
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="b1a4d-109">Met deze opdracht wordt het werk station onmiddellijk vergrendeld.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-109">This command immediately locks the workstation.</span></span> <span data-ttu-id="b1a4d-110">Er wordt gebruikgemaakt van **rundll32.exe**, dat Windows-dll's uitvoert (en de bibliotheken opslaat voor herhaald gebruik) om uit te voeren `user32.dll` , een bibliotheek met Windows-beheer functies.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-110">It uses **rundll32.exe**, which runs Windows DLLs (and saves their libraries for repeated use) to run `user32.dll`, a library of Windows management functions.</span></span>

<span data-ttu-id="b1a4d-111">Wanneer u een werk station vergrendelt terwijl snelle gebruikers wisseling is ingeschakeld, zoals op Windows XP, wordt in de computer het aanmeldings scherm van de gebruiker weer gegeven in plaats van de scherm beveiliging van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-111">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="b1a4d-112">Als u bepaalde sessies op een Terminal Server wilt afsluiten, gebruikt u het opdracht regel programma **tsshutdn.exe** .</span><span class="sxs-lookup"><span data-stu-id="b1a4d-112">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="b1a4d-113">De huidige sessie afmelden</span><span class="sxs-lookup"><span data-stu-id="b1a4d-113">Logging Off the Current Session</span></span>

<span data-ttu-id="b1a4d-114">U kunt verschillende technieken gebruiken om u af te melden bij een sessie op het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-114">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="b1a4d-115">De eenvoudigste manier is het gebruik van het opdracht regel programma Extern bureaublad/Terminal Services, **logoff.exe** (voor meer informatie, typt u in het Power shell-prompt type `logoff /?` ).</span><span class="sxs-lookup"><span data-stu-id="b1a4d-115">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the PowerShell prompt, type `logoff /?`).</span></span> <span data-ttu-id="b1a4d-116">Als u de huidige actieve sessie wilt afmelden, typt u `logoff` zonder argumenten.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-116">To log off the current active session, type `logoff` with no arguments.</span></span>

<span data-ttu-id="b1a4d-117">U kunt het hulp programma **shutdown.exe** ook gebruiken met de optie voor afmelden:</span><span class="sxs-lookup"><span data-stu-id="b1a4d-117">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```powershell
shutdown.exe -l
```

<span data-ttu-id="b1a4d-118">Een andere optie is om WMI te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-118">Another option is to use WMI.</span></span> <span data-ttu-id="b1a4d-119">De **Win32_OperatingSystem** klasse heeft een **afsluit** methode.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-119">The **Win32_OperatingSystem** class has a **Shutdown** method.</span></span>
<span data-ttu-id="b1a4d-120">Als de methode wordt aangeroepen met de vlag 0, wordt de afmelding gestart:</span><span class="sxs-lookup"><span data-stu-id="b1a4d-120">Invoking the method with the 0 flag initiates logoff:</span></span>

<span data-ttu-id="b1a4d-121">Zie voor meer informatie over de **afsluit** methode de [methode Shutdown van de klasse Win32_OperatingSystem](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span><span class="sxs-lookup"><span data-stu-id="b1a4d-121">For more information about the **Shutdown** method, see [Shutdown method of the Win32_OperatingSystem class](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span></span>

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="b1a4d-122">Afsluiten of opnieuw opstarten van een computer</span><span class="sxs-lookup"><span data-stu-id="b1a4d-122">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="b1a4d-123">Het afsluiten en opnieuw opstarten van computers zijn over het algemeen hetzelfde type taak.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-123">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="b1a4d-124">Hulpprogram ma's die een computer afsluiten, zullen deze doorgaans ook opnieuw starten en vice versa.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-124">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="b1a4d-125">Er zijn twee eenvoudige opties voor het opnieuw opstarten van een computer vanuit Power shell.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-125">There are two straightforward options for restarting a computer from PowerShell.</span></span> <span data-ttu-id="b1a4d-126">Gebruik **tsshutdn.exe** of **shutdown.exe** met de juiste argumenten.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-126">Use either **tsshutdn.exe** or **shutdown.exe** with appropriate arguments.</span></span> <span data-ttu-id="b1a4d-127">U kunt gedetailleerde gebruiks gegevens ophalen van `tsshutdn.exe /?` of `shutdown.exe /?` .</span><span class="sxs-lookup"><span data-stu-id="b1a4d-127">You can get detailed usage information from `tsshutdn.exe /?` or `shutdown.exe /?`.</span></span>

<span data-ttu-id="b1a4d-128">U kunt ook de bewerkingen voor afsluiten en opnieuw opstarten rechtstreeks vanuit Power shell uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-128">You can also perform shutdown and restart operations directly from PowerShell as well.</span></span>

<span data-ttu-id="b1a4d-129">Als u de computer wilt afsluiten, gebruikt u de opdracht Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="b1a4d-129">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="b1a4d-130">Als u het besturings systeem opnieuw wilt starten, gebruikt u de opdracht Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="b1a4d-130">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="b1a4d-131">Als u de computer direct opnieuw wilt opstarten, gebruikt u de para meter-Force.</span><span class="sxs-lookup"><span data-stu-id="b1a4d-131">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
