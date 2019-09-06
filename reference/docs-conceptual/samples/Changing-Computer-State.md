---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Computerstatus wijzigen
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386287"
---
# <a name="changing-computer-state"></a><span data-ttu-id="0bd51-103">Computerstatus wijzigen</span><span class="sxs-lookup"><span data-stu-id="0bd51-103">Changing Computer State</span></span>

<span data-ttu-id="0bd51-104">Als u een computer opnieuw wilt instellen in Windows Power shell, gebruikt u een standaard opdracht regel programma, WMI of CIM-klasse.</span><span class="sxs-lookup"><span data-stu-id="0bd51-104">To reset a computer in Windows PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span> <span data-ttu-id="0bd51-105">Hoewel u Windows Power shell alleen gebruikt om het-hulp programma uit te voeren, leert u hoe u de energie status van een computer in Windows Power shell kunt wijzigen om een deel van de belang rijke informatie te zien over het werken met externe hulpprogram ma's in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="0bd51-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="0bd51-106">Een computer vergren delen</span><span class="sxs-lookup"><span data-stu-id="0bd51-106">Locking a Computer</span></span>

<span data-ttu-id="0bd51-107">De enige manier om een computer rechtstreeks te vergren delen met de standaard beschik bare hulpprogram ma's is het aanroepen van de functie **LockWorkStation ()** in **user32. dll**:</span><span class="sxs-lookup"><span data-stu-id="0bd51-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="0bd51-108">Met deze opdracht wordt het werk station onmiddellijk vergrendeld.</span><span class="sxs-lookup"><span data-stu-id="0bd51-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="0bd51-109">Er wordt gebruik gemaakt van *rundll32. exe*, dat Windows-dll's uitvoert (en de bibliotheken opslaat voor herhaalde gebruik) om user32. dll uit te voeren, een bibliotheek met Windows-beheer functies.</span><span class="sxs-lookup"><span data-stu-id="0bd51-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="0bd51-110">Wanneer u een werk station vergrendelt terwijl snelle gebruikers wisseling is ingeschakeld, zoals op Windows XP, wordt in de computer het aanmeldings scherm van de gebruiker weer gegeven in plaats van de scherm beveiliging van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0bd51-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="0bd51-111">Als u bepaalde sessies op een Terminal Server wilt afsluiten, gebruikt u het opdracht regel programma **tsshutdn. exe** .</span><span class="sxs-lookup"><span data-stu-id="0bd51-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="0bd51-112">De huidige sessie afmelden</span><span class="sxs-lookup"><span data-stu-id="0bd51-112">Logging Off the Current Session</span></span>

<span data-ttu-id="0bd51-113">U kunt verschillende technieken gebruiken om u af te melden bij een sessie op het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="0bd51-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="0bd51-114">De eenvoudigste manier is het gebruik van het opdracht regel programma Extern bureaublad/Terminal Services, **Afmelden. exe** (voor meer informatie, typt u bij de Windows Power shell-prompt **Afmelden/?** ).</span><span class="sxs-lookup"><span data-stu-id="0bd51-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="0bd51-115">Als u de huidige actieve sessie wilt afmelden, typt u **Afmelden** zonder argumenten.</span><span class="sxs-lookup"><span data-stu-id="0bd51-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="0bd51-116">U kunt ook het hulp programma **shutdown. exe** gebruiken met de optie voor afmelden:</span><span class="sxs-lookup"><span data-stu-id="0bd51-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="0bd51-117">Een andere optie is om WMI te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0bd51-117">Another option is to use WMI.</span></span> <span data-ttu-id="0bd51-118">De Win32_OperatingSystem-klasse heeft een Win32Shutdown-methode.</span><span class="sxs-lookup"><span data-stu-id="0bd51-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="0bd51-119">Als de methode wordt aangeroepen met de vlag 0, wordt de afmelding gestart:</span><span class="sxs-lookup"><span data-stu-id="0bd51-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="0bd51-120">Zie ' methode Win32Shutdown van de Win32_OperatingSystem-klasse ' in MSDN voor meer informatie en om andere functies van de Win32Shutdown-methode te vinden.</span><span class="sxs-lookup"><span data-stu-id="0bd51-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

<span data-ttu-id="0bd51-121">Ten slotte kunt u CIM gebruiken met dezelfde Win32_OperatingSystem-klasse als hierboven beschreven in de WMI-methode.</span><span class="sxs-lookup"><span data-stu-id="0bd51-121">Finally you can use CIM with the same Win32_OperatingSystem class as described above in the WMI method.</span></span>

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="0bd51-122">Afsluiten of opnieuw opstarten van een computer</span><span class="sxs-lookup"><span data-stu-id="0bd51-122">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="0bd51-123">Het afsluiten en opnieuw opstarten van computers zijn over het algemeen hetzelfde type taak.</span><span class="sxs-lookup"><span data-stu-id="0bd51-123">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="0bd51-124">Hulpprogram ma's die een computer afsluiten, zullen deze doorgaans ook opnieuw starten en vice versa.</span><span class="sxs-lookup"><span data-stu-id="0bd51-124">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="0bd51-125">Er zijn twee eenvoudige opties voor het opnieuw opstarten van een computer vanuit Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="0bd51-125">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="0bd51-126">Gebruik de juiste argumenten van tsshutdn. exe of Shutdown. exe.</span><span class="sxs-lookup"><span data-stu-id="0bd51-126">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="0bd51-127">U kunt gedetailleerde gebruiks gegevens verkrijgen van **tsshutdn. exe/?**</span><span class="sxs-lookup"><span data-stu-id="0bd51-127">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="0bd51-128">of **shutdown. exe/?** .</span><span class="sxs-lookup"><span data-stu-id="0bd51-128">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="0bd51-129">U kunt ook de bewerkingen voor afsluiten en opnieuw opstarten rechtstreeks vanuit Windows Power shell uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0bd51-129">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="0bd51-130">Gebruik de opdracht stop-computer om de computer af te sluiten.</span><span class="sxs-lookup"><span data-stu-id="0bd51-130">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="0bd51-131">Gebruik de opdracht Restart-computer om het besturings systeem opnieuw op te starten</span><span class="sxs-lookup"><span data-stu-id="0bd51-131">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="0bd51-132">Als u de computer direct opnieuw wilt opstarten, gebruikt u de para meter-Force.</span><span class="sxs-lookup"><span data-stu-id="0bd51-132">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
