---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Processen beheren met proces-cmdlets
description: Power shell biedt verschillende cmdlets waarmee processen op lokale en externe computers kunnen worden beheerd.
ms.openlocfilehash: 977a3459eeac22536341753ccd59357d718745f2
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500433"
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="36aca-104">Processen beheren met proces-cmdlets</span><span class="sxs-lookup"><span data-stu-id="36aca-104">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="36aca-105">U kunt de proces-cmdlets in Windows Power shell gebruiken voor het beheren van lokale en externe processen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="36aca-105">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="36aca-106">Processen ophalen (Get-proces)</span><span class="sxs-lookup"><span data-stu-id="36aca-106">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="36aca-107">Als u de processen wilt ophalen die worden uitgevoerd op de lokale computer, voert u een **Get-process** zonder para meters uit.</span><span class="sxs-lookup"><span data-stu-id="36aca-107">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="36aca-108">U kunt bepaalde processen verkrijgen door hun proces namen of proces-Id's op te geven.</span><span class="sxs-lookup"><span data-stu-id="36aca-108">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="36aca-109">Met de volgende opdracht wordt het inactief proces opgehaald:</span><span class="sxs-lookup"><span data-stu-id="36aca-109">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="36aca-110">Hoewel het normaal is voor cmdlets om geen gegevens in bepaalde situaties te retour neren, wordt bij het opgeven van een proces door de proces **-** process een fout gegenereerd als er geen overeenkomsten worden gevonden, omdat het gebruikelijk is om een bekend actief proces op te halen.</span><span class="sxs-lookup"><span data-stu-id="36aca-110">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="36aca-111">Als er geen proces met die id is, is het waarschijnlijk dat de id onjuist is of dat het proces van belang al is afgesloten:</span><span class="sxs-lookup"><span data-stu-id="36aca-111">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="36aca-112">U kunt de para meter name van de cmdlet Get-Process gebruiken om een subset van processen op te geven op basis van de proces naam.</span><span class="sxs-lookup"><span data-stu-id="36aca-112">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="36aca-113">De para meter name kan meerdere namen in een lijst met door komma's gescheiden waarden hebben en ondersteunt het gebruik van joker tekens, zodat u naam patronen kunt typen.</span><span class="sxs-lookup"><span data-stu-id="36aca-113">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="36aca-114">Met de volgende opdracht wordt bijvoorbeeld proces uitgevoerd waarvan de naam begint met ' ex '.</span><span class="sxs-lookup"><span data-stu-id="36aca-114">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="36aca-115">Omdat de klasse .NET System. Diagnostics. process de basis is voor Windows Power shell-processen, worden enkele van de conventies gevolgd door System. Diagnostics. process.</span><span class="sxs-lookup"><span data-stu-id="36aca-115">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="36aca-116">Een van deze conventies is dat de proces naam voor een uitvoerbaar bestand nooit de '. exe ' bevat aan het einde van de naam van het uitvoer bare bestand.</span><span class="sxs-lookup"><span data-stu-id="36aca-116">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="36aca-117">**Get-process** accepteert ook meerdere waarden voor de para meter name.</span><span class="sxs-lookup"><span data-stu-id="36aca-117">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="36aca-118">U kunt de para meter ComputerName van Get-Process gebruiken om processen op externe computers op te halen.</span><span class="sxs-lookup"><span data-stu-id="36aca-118">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="36aca-119">Met de volgende opdracht worden bijvoorbeeld de Power shell-processen op de lokale computer (aangeduid door ' localhost ') en op twee externe computers.</span><span class="sxs-lookup"><span data-stu-id="36aca-119">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="36aca-120">De computer namen zijn niet duidelijk in deze weer gave, maar ze worden opgeslagen in de eigenschap MachineName van de proces objecten die Get-Process retourneert.</span><span class="sxs-lookup"><span data-stu-id="36aca-120">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="36aca-121">De volgende opdracht maakt gebruik van de cmdlet Format-Table om de eigenschappen proces-ID, naam van de proces naam en MachineName (ComputerName) van de proces objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="36aca-121">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 |
  Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="36aca-122">Met deze complexere opdracht wordt de eigenschap MachineName aan de standaard Get-Process weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36aca-122">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="36aca-123">Processen stoppen (Stop proces)</span><span class="sxs-lookup"><span data-stu-id="36aca-123">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="36aca-124">Windows Power shell biedt u flexibiliteit voor het weer geven van processen, maar over het stoppen van een proces?</span><span class="sxs-lookup"><span data-stu-id="36aca-124">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="36aca-125">Voor de cmdlet **Stop-process** wordt een naam of id gebruikt om een proces op te geven dat u wilt stoppen.</span><span class="sxs-lookup"><span data-stu-id="36aca-125">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="36aca-126">De mogelijkheid om processen te stoppen, is afhankelijk van uw machtigingen.</span><span class="sxs-lookup"><span data-stu-id="36aca-126">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="36aca-127">Sommige processen kunnen niet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="36aca-127">Some processes cannot be stopped.</span></span> <span data-ttu-id="36aca-128">Als u bijvoorbeeld probeert het inactieve proces te stoppen, krijgt u een fout melding:</span><span class="sxs-lookup"><span data-stu-id="36aca-128">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="36aca-129">U kunt er ook voor zorgen dat u wordt gevraagd om te vragen met de para meter **confirm** .</span><span class="sxs-lookup"><span data-stu-id="36aca-129">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="36aca-130">Deze para meter is met name handig als u een Joker teken gebruikt voor het opgeven van de naam van het proces, omdat u per ongeluk een aantal processen wilt afleiden die u niet wilt stoppen:</span><span class="sxs-lookup"><span data-stu-id="36aca-130">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

<span data-ttu-id="36aca-131">Het maken van complexe processen is mogelijk met enkele van de object Filter-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="36aca-131">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="36aca-132">Omdat een proces object een reagerende eigenschap heeft die waar is wanneer deze niet meer reageert, kunt u alle niet-reagerende toepassingen stoppen met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="36aca-132">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="36aca-133">U kunt dezelfde benadering gebruiken in andere situaties.</span><span class="sxs-lookup"><span data-stu-id="36aca-133">You can use the same approach in other situations.</span></span> <span data-ttu-id="36aca-134">Stel bijvoorbeeld dat een tweede toepassing voor het systeemvak automatisch wordt uitgevoerd wanneer gebruikers een andere toepassing starten.</span><span class="sxs-lookup"><span data-stu-id="36aca-134">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="36aca-135">Het kan voor komen dat dit niet goed werkt in Terminal Services sessies, maar dat u deze nog steeds wilt behouden in sessies die worden uitgevoerd op de fysieke computer console.</span><span class="sxs-lookup"><span data-stu-id="36aca-135">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="36aca-136">Sessies die zijn verbonden met het bureau blad van de fysieke computer hebben altijd een sessie-ID van 0, zodat u alle exemplaren van het proces dat zich in andere sessies bevindt, kunt stoppen met behulp van **where-object** en het proces, **SessionId**:</span><span class="sxs-lookup"><span data-stu-id="36aca-136">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="36aca-137">De cmdlet Stop-Process heeft geen ComputerName-para meter.</span><span class="sxs-lookup"><span data-stu-id="36aca-137">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="36aca-138">Daarom moet u de cmdlet Invoke-Command gebruiken om een opdracht stop proces uit te voeren op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="36aca-138">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="36aca-139">Als u bijvoorbeeld het Power Shell-proces op de externe computer Server01 wilt stoppen, typt u:</span><span class="sxs-lookup"><span data-stu-id="36aca-139">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="36aca-140">Alle andere Windows Power shell-sessies stoppen</span><span class="sxs-lookup"><span data-stu-id="36aca-140">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="36aca-141">Het kan af en toe handig zijn om alle actieve Windows Power shell-sessies te stoppen, behalve de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="36aca-141">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="36aca-142">Als een sessie te veel bronnen gebruikt of niet toegankelijk is (mogelijk op afstand of in een andere bureaublad sessie), is het mogelijk dat u deze niet rechtstreeks kunt stoppen.</span><span class="sxs-lookup"><span data-stu-id="36aca-142">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="36aca-143">Als u probeert alle actieve sessies te stoppen, kan de huidige sessie echter worden beëindigd.</span><span class="sxs-lookup"><span data-stu-id="36aca-143">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="36aca-144">Elke Windows Power shell-sessie heeft een omgevings variabele die de id van het Windows Power Shell-proces bevat.</span><span class="sxs-lookup"><span data-stu-id="36aca-144">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="36aca-145">U kunt de $PID controleren op basis van de id van elke sessie en alleen Windows Power shell-sessies met een andere id beëindigen. De volgende opdracht pijp lijn doet dit en retourneert de lijst met beëindigde sessies (vanwege het gebruik van de para meter **PassThru** ):</span><span class="sxs-lookup"><span data-stu-id="36aca-145">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="36aca-146">Starten, fouten opsporen en wachten op processen</span><span class="sxs-lookup"><span data-stu-id="36aca-146">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="36aca-147">Windows Power shell wordt ook geleverd met cmdlets om een proces te starten (of opnieuw te starten), fouten op te sporen en te wachten totdat een proces is voltooid voordat een opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="36aca-147">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="36aca-148">Zie het Help-onderwerp voor cmdlets voor elke cmdlet voor meer informatie over deze cmdlets.</span><span class="sxs-lookup"><span data-stu-id="36aca-148">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="36aca-149">Zie ook</span><span class="sxs-lookup"><span data-stu-id="36aca-149">See Also</span></span>

- [<span data-ttu-id="36aca-150">Get-Process</span><span class="sxs-lookup"><span data-stu-id="36aca-150">Get-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Process)
- [<span data-ttu-id="36aca-151">Stoppen-proces</span><span class="sxs-lookup"><span data-stu-id="36aca-151">Stop-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Stop-Process)
- [<span data-ttu-id="36aca-152">Start-process</span><span class="sxs-lookup"><span data-stu-id="36aca-152">Start-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Start-Process)
- [<span data-ttu-id="36aca-153">Wacht proces</span><span class="sxs-lookup"><span data-stu-id="36aca-153">Wait-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Wait-Process)
- [<span data-ttu-id="36aca-154">Debug-proces</span><span class="sxs-lookup"><span data-stu-id="36aca-154">Debug-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Debug-Process)
- [<span data-ttu-id="36aca-155">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="36aca-155">Invoke-Command</span></span>](/powershell/module/Microsoft.PowerShell.Core/Invoke-Command)
