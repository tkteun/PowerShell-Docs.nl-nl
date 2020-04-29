---
ms.date: 08/14/2018
keywords: Power shell, cmdlet
title: Externe opdrachten uitvoeren
ms.openlocfilehash: d6609deafd8dec4f34a8412439d87dacd20d46f1
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030309"
---
# <a name="running-remote-commands"></a><span data-ttu-id="96cea-103">Externe opdrachten uitvoeren</span><span class="sxs-lookup"><span data-stu-id="96cea-103">Running Remote Commands</span></span>

<span data-ttu-id="96cea-104">U kunt opdrachten uitvoeren op een of honderden computers met één Power shell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="96cea-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="96cea-105">Windows Power shell ondersteunt extern computer gebruik met behulp van verschillende technologieën, waaronder WMI, RPC en WS-Management.</span><span class="sxs-lookup"><span data-stu-id="96cea-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="96cea-106">Power shell core ondersteunt WMI, WS-beheer en externe SSH-communicatie.</span><span class="sxs-lookup"><span data-stu-id="96cea-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="96cea-107">RPC wordt niet meer ondersteund.</span><span class="sxs-lookup"><span data-stu-id="96cea-107">RPC is no longer supported.</span></span>

<span data-ttu-id="96cea-108">Raadpleeg de volgende artikelen voor meer informatie over externe communicatie in Power shell core:</span><span class="sxs-lookup"><span data-stu-id="96cea-108">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="96cea-109">[Externe SSH-communicatie in Power shell core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="96cea-109">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="96cea-110">[Externe WSMan-communicatie in Power shell core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="96cea-110">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="96cea-111">Externe toegang tot Windows Power shell zonder configuratie</span><span class="sxs-lookup"><span data-stu-id="96cea-111">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="96cea-112">Veel Windows Power shell-cmdlets hebben de para meter ComputerName waarmee u gegevens kunt verzamelen en instellingen op een of meer externe computers wijzigt.</span><span class="sxs-lookup"><span data-stu-id="96cea-112">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="96cea-113">Deze cmdlets gebruiken verschillende communicatie protocollen en werken zonder speciale configuratie op alle Windows-besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="96cea-113">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="96cea-114">Deze cmdlets zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="96cea-114">These cmdlets include:</span></span>

- [<span data-ttu-id="96cea-115">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="96cea-115">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="96cea-116">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="96cea-116">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="96cea-117">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="96cea-117">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="96cea-118">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="96cea-118">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="96cea-119">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="96cea-119">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="96cea-120">Get-Process</span><span class="sxs-lookup"><span data-stu-id="96cea-120">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="96cea-121">Get-Service</span><span class="sxs-lookup"><span data-stu-id="96cea-121">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="96cea-122">Set-Service</span><span class="sxs-lookup"><span data-stu-id="96cea-122">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="96cea-123">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="96cea-123">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="96cea-124">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="96cea-124">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="96cea-125">Doorgaans hebben cmdlets die ondersteuning bieden voor externe toegang zonder speciale configuratie, de para meter ComputerName en hebben de sessie parameter niet.</span><span class="sxs-lookup"><span data-stu-id="96cea-125">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="96cea-126">Als u deze cmdlets wilt vinden in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="96cea-126">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="96cea-127">Externe toegang voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="96cea-127">Windows PowerShell Remoting</span></span>

<span data-ttu-id="96cea-128">Met het protocol WS-Management kunt u met Windows Power shell voor externe toegang een Windows Power shell-opdracht uitvoeren op een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="96cea-128">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="96cea-129">U kunt permanente verbindingen tot stand brengen, interactieve sessies starten en scripts uitvoeren op externe computers.</span><span class="sxs-lookup"><span data-stu-id="96cea-129">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="96cea-130">Als u externe toegang tot Windows Power shell wilt gebruiken, moet u de computer configureren voor extern beheer.</span><span class="sxs-lookup"><span data-stu-id="96cea-130">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="96cea-131">Zie [over externe vereisten](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)voor meer informatie, waaronder instructies.</span><span class="sxs-lookup"><span data-stu-id="96cea-131">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="96cea-132">Wanneer u Windows Power shell Remoting hebt geconfigureerd, zijn veel externe strategieën voor u beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="96cea-132">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="96cea-133">In dit artikel worden slechts enkele hiervan vermeld.</span><span class="sxs-lookup"><span data-stu-id="96cea-133">This article lists just a few of them.</span></span> <span data-ttu-id="96cea-134">Zie [over extern](/powershell/module/microsoft.powershell.core/about/about_remote)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="96cea-134">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="96cea-135">Een interactieve sessie starten</span><span class="sxs-lookup"><span data-stu-id="96cea-135">Start an Interactive Session</span></span>

<span data-ttu-id="96cea-136">Als u een interactieve sessie met één externe computer wilt starten, gebruikt u de cmdlet [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .</span><span class="sxs-lookup"><span data-stu-id="96cea-136">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span>
<span data-ttu-id="96cea-137">Als u bijvoorbeeld een interactieve sessie met de externe computer Server01 wilt starten, typt u:</span><span class="sxs-lookup"><span data-stu-id="96cea-137">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="96cea-138">De opdracht prompt wordt gewijzigd om de naam van de externe computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="96cea-138">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="96cea-139">Alle opdrachten die u typt bij de prompt die worden uitgevoerd op de externe computer en de resultaten worden weer gegeven op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="96cea-139">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="96cea-140">Als u de interactieve sessie wilt beëindigen, typt u:</span><span class="sxs-lookup"><span data-stu-id="96cea-140">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="96cea-141">Zie voor meer informatie over de cmdlets Enter-PSSession en Exit-PSSession:</span><span class="sxs-lookup"><span data-stu-id="96cea-141">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="96cea-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="96cea-142">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="96cea-143">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="96cea-143">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="96cea-144">Een externe opdracht uitvoeren</span><span class="sxs-lookup"><span data-stu-id="96cea-144">Run a Remote Command</span></span>

<span data-ttu-id="96cea-145">Als u een opdracht op een of meer computers wilt uitvoeren, gebruikt u de cmdlet [invoke-opdracht](/powershell/module/microsoft.powershell.core/invoke-command) .</span><span class="sxs-lookup"><span data-stu-id="96cea-145">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="96cea-146">Als u bijvoorbeeld de opdracht [Get-uiCulture](/powershell/module/microsoft.powershell.utility/get-uiculture) wilt uitvoeren op de externe computers Server01 en Server02, typt u:</span><span class="sxs-lookup"><span data-stu-id="96cea-146">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="96cea-147">De uitvoer wordt teruggestuurd naar uw computer.</span><span class="sxs-lookup"><span data-stu-id="96cea-147">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="96cea-148">Een script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="96cea-148">Run a Script</span></span>

<span data-ttu-id="96cea-149">Als u een script wilt uitvoeren op een of meer externe computers, gebruikt u de para `Invoke-Command` meter filepath van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="96cea-149">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="96cea-150">Het script moet op of toegankelijk zijn voor uw lokale computer.</span><span class="sxs-lookup"><span data-stu-id="96cea-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="96cea-151">De resultaten worden teruggestuurd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="96cea-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="96cea-152">Met de volgende opdracht wordt bijvoorbeeld het script DiskCollect. ps1 uitgevoerd op de externe computers, Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="96cea-152">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="96cea-153">Een permanente verbinding tot stand brengen</span><span class="sxs-lookup"><span data-stu-id="96cea-153">Establish a Persistent Connection</span></span>

<span data-ttu-id="96cea-154">Gebruik de `New-PSSession` cmdlet om een permanente sessie te maken op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="96cea-154">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="96cea-155">In het volgende voor beeld worden externe sessies gemaakt op Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="96cea-155">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="96cea-156">De sessie objecten worden opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="96cea-156">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="96cea-157">Nu u de sessies tot stand hebt gebracht, kunt u elke opdracht in ze uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="96cea-157">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="96cea-158">En omdat de sessies permanent zijn, kunt u gegevens verzamelen van de ene opdracht en deze gebruiken in een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="96cea-158">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="96cea-159">Met de volgende opdracht wordt bijvoorbeeld een Get-HotFix-opdracht uitgevoerd in de sessies in de variabele $s en worden de resultaten opgeslagen in de $h-variabele.</span><span class="sxs-lookup"><span data-stu-id="96cea-159">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="96cea-160">De variabele $h wordt gemaakt in elk van de sessies in $s, maar deze komt niet voor in de lokale sessie.</span><span class="sxs-lookup"><span data-stu-id="96cea-160">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="96cea-161">Nu kunt u de gegevens in de `$h` variabele gebruiken met andere opdrachten in dezelfde sessie.</span><span class="sxs-lookup"><span data-stu-id="96cea-161">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="96cea-162">De resultaten worden weer gegeven op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="96cea-162">The results are displayed on the local computer.</span></span> <span data-ttu-id="96cea-163">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="96cea-163">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="96cea-164">Geavanceerde externe communicatie</span><span class="sxs-lookup"><span data-stu-id="96cea-164">Advanced Remoting</span></span>

<span data-ttu-id="96cea-165">Windows Power shell Remote Management begint hier gewoon.</span><span class="sxs-lookup"><span data-stu-id="96cea-165">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="96cea-166">Door gebruik te maken van de cmdlets die zijn geïnstalleerd met Windows Power shell, kunt u externe sessies instellen en configureren op basis van de lokale en externe eind punten, aangepaste en beperkte sessies opstellen, gebruikers opdrachten laten importeren uit een externe sessie die daad werkelijk impliciet is uitgevoerd op de externe sessie, de beveiliging van een externe sessie configureren, en nog veel meer.</span><span class="sxs-lookup"><span data-stu-id="96cea-166">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="96cea-167">Windows Power shell bevat een WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="96cea-167">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="96cea-168">De provider maakt een `WSMAN:` station waarmee u kunt navigeren door een hiërarchie van configuratie-instellingen op de lokale computer en externe computers.</span><span class="sxs-lookup"><span data-stu-id="96cea-168">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="96cea-169">Zie voor meer informatie over de WSMan-provider [wsman-provider](https://technet.microsoft.com/library/dd819476.aspx) en [over WS-Management-cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), of typ `Get-Help wsman`in de Windows Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="96cea-169">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="96cea-170">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="96cea-170">For more information, see:</span></span>

- [<span data-ttu-id="96cea-171">Over externe Veelgestelde vragen</span><span class="sxs-lookup"><span data-stu-id="96cea-171">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="96cea-172">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="96cea-172">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="96cea-173">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="96cea-173">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="96cea-174">Zie [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx)voor hulp bij externe fouten.</span><span class="sxs-lookup"><span data-stu-id="96cea-174">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="96cea-175">Zie ook</span><span class="sxs-lookup"><span data-stu-id="96cea-175">See Also</span></span>

- [<span data-ttu-id="96cea-176">about_Remote</span><span class="sxs-lookup"><span data-stu-id="96cea-176">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="96cea-177">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="96cea-177">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="96cea-178">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="96cea-178">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="96cea-179">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="96cea-179">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="96cea-180">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="96cea-180">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="96cea-181">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="96cea-181">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="96cea-182">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="96cea-182">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="96cea-183">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="96cea-183">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="96cea-184">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="96cea-184">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="96cea-185">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="96cea-185">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="96cea-186">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="96cea-186">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
