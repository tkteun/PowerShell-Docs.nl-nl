---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Processen beheren met proces-cmdlets
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: d6d7daa810dce2d476566e4d30f03cc95bf730e6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="eb851-103">Processen beheren met proces-cmdlets</span><span class="sxs-lookup"><span data-stu-id="eb851-103">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="eb851-104">U kunt de proces-cmdlets in Windows PowerShell gebruiken voor het beheren van lokale en externe processen in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb851-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="eb851-105">Processen ophalen (Get-Process)</span><span class="sxs-lookup"><span data-stu-id="eb851-105">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="eb851-106">Uitvoeren als u de processen die worden uitgevoerd op de lokale computer, een **Get-Process** zonder parameters.</span><span class="sxs-lookup"><span data-stu-id="eb851-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="eb851-107">U kunt bepaalde processen ophalen door hun procesnamen of proces-id's te geven.</span><span class="sxs-lookup"><span data-stu-id="eb851-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="eb851-108">De volgende opdracht wordt het actieve proces:</span><span class="sxs-lookup"><span data-stu-id="eb851-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="eb851-109">Hoewel het normaal voor cmdlets retourneren geen gegevens in sommige gevallen is wanneer u een proces met de proces-id opgeeft **Get-Process** wordt een fout gegenereerd als het geen overeenkomsten gevonden omdat het gebruikelijke doel voor het ophalen van een bekende proces dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eb851-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="eb851-110">Als er geen proces met die Id, is het waarschijnlijk dat de Id onjuist is of het proces van belang is al afgesloten:</span><span class="sxs-lookup"><span data-stu-id="eb851-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="eb851-111">De parameter Name van de cmdlet Get-Process kunt u een subset van de processen op basis van de procesnaam opgeven.</span><span class="sxs-lookup"><span data-stu-id="eb851-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="eb851-112">De parameter Name kunt meerdere namen in een door komma's gescheiden lijst en daarmee het gebruik van jokertekens, zodat u kunt bestandsnaampatronen typen.</span><span class="sxs-lookup"><span data-stu-id="eb851-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="eb851-113">Bijvoorbeeld de volgende opdracht opgehaald proces waarvan de naam begint met 'ex'.</span><span class="sxs-lookup"><span data-stu-id="eb851-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="eb851-114">Omdat de klasse .NET System.Diagnostics.Process de basis voor Windows PowerShell-processen vormt, volgt een aantal van de overeenkomsten die wordt gebruikt door System.Diagnostics.Process.</span><span class="sxs-lookup"><span data-stu-id="eb851-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="eb851-115">Een van deze conventies is de procesnaam voor een uitvoerbaar bestand bevat nooit de '.exe' aan het einde van het uitvoerbare bestand.</span><span class="sxs-lookup"><span data-stu-id="eb851-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="eb851-116">**Get-Process** ook accepteert meerdere waarden voor de parameter Name.</span><span class="sxs-lookup"><span data-stu-id="eb851-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="eb851-117">U kunt de parameter ComputerName van Get-Process gebruiken om op te halen van processen op externe computers.</span><span class="sxs-lookup"><span data-stu-id="eb851-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="eb851-118">Bijvoorbeeld, opgehaald van de PowerShell-processen op de lokale computer (vertegenwoordigd door 'localhost') in de volgende opdracht en op twee externe computers.</span><span class="sxs-lookup"><span data-stu-id="eb851-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="eb851-119">De computernamen zijn niet duidelijk in deze informatie wilt weergeven, maar ze worden opgeslagen in de eigenschap computernaam van de proces-objecten die Get-Process retourneert.</span><span class="sxs-lookup"><span data-stu-id="eb851-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="eb851-120">De volgende opdracht maakt gebruik van de cmdlet Format-Table de proces-ID, de procesnaam en de computernaam (ComputerName) wilt weergeven van de proces-objecten.</span><span class="sxs-lookup"><span data-stu-id="eb851-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="eb851-121">De eigenschap MachineName deze complexere opdracht toegevoegd aan de standaard Get-Process-weergave.</span><span class="sxs-lookup"><span data-stu-id="eb851-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $() {$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="eb851-122">Stoppen (Stop-proces)-processen</span><span class="sxs-lookup"><span data-stu-id="eb851-122">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="eb851-123">Windows PowerShell biedt flexibiliteit voor processen weergeven, maar hoe zit het stoppen van een proces?</span><span class="sxs-lookup"><span data-stu-id="eb851-123">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="eb851-124">De **Stop-Process** cmdlet heeft een naam of Id om op te geven van een proces dat u wilt stoppen.</span><span class="sxs-lookup"><span data-stu-id="eb851-124">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="eb851-125">De mogelijkheid om te stoppen processen is afhankelijk van uw machtigingen.</span><span class="sxs-lookup"><span data-stu-id="eb851-125">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="eb851-126">Bepaalde processen kunnen niet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="eb851-126">Some processes cannot be stopped.</span></span> <span data-ttu-id="eb851-127">Haal bijvoorbeeld als u probeert om de niet-actieve proces te stoppen, een fout opgetreden:</span><span class="sxs-lookup"><span data-stu-id="eb851-127">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="eb851-128">U kunt ook afdwingen te vragen met de **bevestigen** parameter.</span><span class="sxs-lookup"><span data-stu-id="eb851-128">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="eb851-129">Deze parameter is vooral handig als u een jokerteken gebruiken bij het opgeven van de procesnaam omdat u mogelijk per ongeluk overeenkomt met bepaalde processen die u niet wilt stoppen:</span><span class="sxs-lookup"><span data-stu-id="eb851-129">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

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

<span data-ttu-id="eb851-130">Complex proces manipulatie is mogelijk met behulp van een deel van het object voor het filteren van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="eb851-130">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="eb851-131">Omdat een procesobject een reageren-eigenschap die is ingesteld op true heeft wanneer reageert niet meer, kunt u alle responsieve toepassingen met de volgende opdracht te stoppen:</span><span class="sxs-lookup"><span data-stu-id="eb851-131">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="eb851-132">In andere situaties kunt u dezelfde aanpak.</span><span class="sxs-lookup"><span data-stu-id="eb851-132">You can use the same approach in other situations.</span></span> <span data-ttu-id="eb851-133">Stel bijvoorbeeld dat een toepassing van de gebied secundaire melding wordt automatisch uitgevoerd wanneer gebruikers een andere toepassing starten.</span><span class="sxs-lookup"><span data-stu-id="eb851-133">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="eb851-134">U merkt dat dit niet goed in Terminal Services-sessies werkt, maar u toch wilt behouden blijft in sessies die worden uitgevoerd op de fysieke computer-console.</span><span class="sxs-lookup"><span data-stu-id="eb851-134">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="eb851-135">Sessies altijd verbonden met het bureaublad van de fysieke computer hebben een sessie-ID 0, kunt u alle exemplaren van het proces die zich in andere sessies met stoppen **Where-Object** en het proces **SessionId** :</span><span class="sxs-lookup"><span data-stu-id="eb851-135">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="eb851-136">De cmdlet Stop-Process beschikt niet over een parameter ComputerName.</span><span class="sxs-lookup"><span data-stu-id="eb851-136">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="eb851-137">Daarom een stopopdracht-proces op een externe computer uitgevoerd, moet u de cmdlet Invoke-Command gebruiken.</span><span class="sxs-lookup"><span data-stu-id="eb851-137">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="eb851-138">Bijvoorbeeld, als u wilt stoppen het PowerShell-proces op de externe computer Server01, typt u:</span><span class="sxs-lookup"><span data-stu-id="eb851-138">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="eb851-139">Alle andere Windows PowerShell-sessies te stoppen</span><span class="sxs-lookup"><span data-stu-id="eb851-139">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="eb851-140">Tijd tot tijd mogelijk handig om te voorkomen dat alle actieve Windows PowerShell-sessies dan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eb851-140">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="eb851-141">Als een sessie te veel bronnen of niet toegankelijk is (dit kan worden uitgevoerd op afstand of in een ander bureaublad-sessiehost), mogelijk niet rechtstreeks te stoppen.</span><span class="sxs-lookup"><span data-stu-id="eb851-141">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="eb851-142">Als u probeert alle actieve sessies te stoppen, maar worden de huidige sessie beëindigd in plaats daarvan.</span><span class="sxs-lookup"><span data-stu-id="eb851-142">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="eb851-143">Elke Windows PowerShell-sessie heeft een omgevingsvariabele PID met de Id van de Windows PowerShell-proces.</span><span class="sxs-lookup"><span data-stu-id="eb851-143">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="eb851-144">U kunt de $PID tegen de Id van elke sessie controleren en alleen Windows PowerShell-sessies waarvoor een andere Id. beëindigen De volgende opdracht in de pijplijn wordt dit en retourneert de lijst met beëindigde sessies (vanwege het gebruik van de **PassThru** parameter):</span><span class="sxs-lookup"><span data-stu-id="eb851-144">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

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

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="eb851-145">Starten, foutopsporing en wachten op processen</span><span class="sxs-lookup"><span data-stu-id="eb851-145">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="eb851-146">Windows PowerShell ook wordt geleverd met cmdlets (of opnieuw instellen), een proces voor foutopsporing en wachttijd voor een proces te voltooien voordat een opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="eb851-146">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="eb851-147">Zie het help-onderwerp van de cmdlet voor elke cmdlet voor informatie over deze cdmlets.</span><span class="sxs-lookup"><span data-stu-id="eb851-147">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb851-148">Zie ook</span><span class="sxs-lookup"><span data-stu-id="eb851-148">See Also</span></span>

- <span data-ttu-id="eb851-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span><span class="sxs-lookup"><span data-stu-id="eb851-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span></span>
- <span data-ttu-id="eb851-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span><span class="sxs-lookup"><span data-stu-id="eb851-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span></span>
- [<span data-ttu-id="eb851-151">Start-Process</span><span class="sxs-lookup"><span data-stu-id="eb851-151">Start-Process</span></span>](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [<span data-ttu-id="eb851-152">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="eb851-152">Wait-Process</span></span>](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [<span data-ttu-id="eb851-153">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="eb851-153">Debug-Process</span></span>](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [<span data-ttu-id="eb851-154">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="eb851-154">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)