---
ms.date: 08/21/2020
keywords: powershell,cmdlet
title: Externe opdrachten uitvoeren
description: Hierin worden de methoden beschreven voor het uitvoeren van opdrachten op externe systemen met behulp van Power shell.
ms.openlocfilehash: cff18a4f51c3ed8e3ed2c1f35862a88911e7ceb5
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391405"
---
# <a name="running-remote-commands"></a><span data-ttu-id="bb4f4-104">Externe opdrachten uitvoeren</span><span class="sxs-lookup"><span data-stu-id="bb4f4-104">Running Remote Commands</span></span>

<span data-ttu-id="bb4f4-105">U kunt opdrachten uitvoeren op een of honderden computers met één Power shell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-105">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="bb4f4-106">Windows Power shell ondersteunt extern computer gebruik met behulp van verschillende technologieën, waaronder WMI, RPC en WS-Management.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-106">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="bb4f4-107">Power shell core ondersteunt WMI, WS-beheer en externe SSH-communicatie.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-107">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="bb4f4-108">In Power shell 6 wordt RPC niet meer ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-108">In PowerShell 6, RPC is no longer supported.</span></span> <span data-ttu-id="bb4f4-109">In Power shell 7 en hoger wordt RPC alleen ondersteund in Windows.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-109">In PowerShell 7 and above, RPC is supported only in Windows.</span></span>

<span data-ttu-id="bb4f4-110">Raadpleeg de volgende artikelen voor meer informatie over externe communicatie in Power shell core:</span><span class="sxs-lookup"><span data-stu-id="bb4f4-110">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="bb4f4-111">[Externe SSH-communicatie in Power shell core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="bb4f4-111">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="bb4f4-112">[Externe WSMan-communicatie in Power shell core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="bb4f4-112">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="bb4f4-113">Externe toegang tot Windows Power shell zonder configuratie</span><span class="sxs-lookup"><span data-stu-id="bb4f4-113">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="bb4f4-114">Veel Windows Power shell-cmdlets hebben de para meter ComputerName waarmee u gegevens kunt verzamelen en instellingen op een of meer externe computers wijzigt.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-114">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="bb4f4-115">Deze cmdlets gebruiken verschillende communicatie protocollen en werken zonder speciale configuratie op alle Windows-besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-115">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="bb4f4-116">Deze cmdlets zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="bb4f4-116">These cmdlets include:</span></span>

- [<span data-ttu-id="bb4f4-117">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="bb4f4-117">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="bb4f4-118">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="bb4f4-118">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="bb4f4-119">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="bb4f4-119">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="bb4f4-120">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="bb4f4-120">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="bb4f4-121">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="bb4f4-121">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="bb4f4-122">Get-Process</span><span class="sxs-lookup"><span data-stu-id="bb4f4-122">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="bb4f4-123">Get-Service</span><span class="sxs-lookup"><span data-stu-id="bb4f4-123">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="bb4f4-124">Set-Service</span><span class="sxs-lookup"><span data-stu-id="bb4f4-124">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="bb4f4-125">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="bb4f4-125">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="bb4f4-126">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="bb4f4-126">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="bb4f4-127">Doorgaans hebben cmdlets die ondersteuning bieden voor externe toegang zonder speciale configuratie, de para meter ComputerName en hebben de sessie parameter niet.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-127">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="bb4f4-128">Als u deze cmdlets wilt vinden in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="bb4f4-128">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="bb4f4-129">Externe toegang voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="bb4f4-129">Windows PowerShell Remoting</span></span>

<span data-ttu-id="bb4f4-130">Met behulp van het WS-Management-protocol kunt u met Windows Power shell voor externe toegang een Windows Power shell-opdracht op een of meer externe computers uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-130">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="bb4f4-131">U kunt permanente verbindingen tot stand brengen, interactieve sessies starten en scripts uitvoeren op externe computers.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-131">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="bb4f4-132">Als u externe toegang tot Windows Power shell wilt gebruiken, moet u de computer configureren voor extern beheer.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-132">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="bb4f4-133">Zie [over externe vereisten](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)voor meer informatie, waaronder instructies.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-133">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="bb4f4-134">Wanneer u Windows Power shell Remoting hebt geconfigureerd, zijn veel externe strategieën voor u beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-134">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="bb4f4-135">In dit artikel worden slechts enkele hiervan vermeld.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-135">This article lists just a few of them.</span></span> <span data-ttu-id="bb4f4-136">Zie [over extern](/powershell/module/microsoft.powershell.core/about/about_remote)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-136">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="bb4f4-137">Een interactieve sessie starten</span><span class="sxs-lookup"><span data-stu-id="bb4f4-137">Start an Interactive Session</span></span>

<span data-ttu-id="bb4f4-138">Als u een interactieve sessie met één externe computer wilt starten, gebruikt u de cmdlet [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .</span><span class="sxs-lookup"><span data-stu-id="bb4f4-138">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span> <span data-ttu-id="bb4f4-139">Als u bijvoorbeeld een interactieve sessie met de externe computer Server01 wilt starten, typt u:</span><span class="sxs-lookup"><span data-stu-id="bb4f4-139">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="bb4f4-140">De opdracht prompt wordt gewijzigd om de naam van de externe computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-140">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="bb4f4-141">Alle opdrachten die u typt bij de prompt die worden uitgevoerd op de externe computer en de resultaten worden weer gegeven op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-141">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="bb4f4-142">Als u de interactieve sessie wilt beëindigen, typt u:</span><span class="sxs-lookup"><span data-stu-id="bb4f4-142">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="bb4f4-143">Zie voor meer informatie over de Enter-PSSession en Exit-PSSession-cmdlets:</span><span class="sxs-lookup"><span data-stu-id="bb4f4-143">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="bb4f4-144">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb4f4-144">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="bb4f4-145">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb4f4-145">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="bb4f4-146">Een externe opdracht uitvoeren</span><span class="sxs-lookup"><span data-stu-id="bb4f4-146">Run a Remote Command</span></span>

<span data-ttu-id="bb4f4-147">Als u een opdracht op een of meer computers wilt uitvoeren, gebruikt u de cmdlet [invoke-opdracht](/powershell/module/microsoft.powershell.core/invoke-command) .</span><span class="sxs-lookup"><span data-stu-id="bb4f4-147">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="bb4f4-148">Als u bijvoorbeeld de opdracht [Get-uiCulture](/powershell/module/microsoft.powershell.utility/get-uiculture) wilt uitvoeren op de externe computers Server01 en Server02, typt u:</span><span class="sxs-lookup"><span data-stu-id="bb4f4-148">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="bb4f4-149">De uitvoer wordt teruggestuurd naar uw computer.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-149">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="bb4f4-150">Een script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="bb4f4-150">Run a Script</span></span>

<span data-ttu-id="bb4f4-151">Als u een script wilt uitvoeren op een of meer externe computers, gebruikt u de para meter FilePath van de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-151">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="bb4f4-152">Het script moet op of toegankelijk zijn voor uw lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-152">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="bb4f4-153">De resultaten worden teruggestuurd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-153">The results are returned to your local computer.</span></span>

<span data-ttu-id="bb4f4-154">Met de volgende opdracht wordt bijvoorbeeld het DiskCollect.ps1 script uitgevoerd op de externe computers, Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-154">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="bb4f4-155">Een permanente verbinding tot stand brengen</span><span class="sxs-lookup"><span data-stu-id="bb4f4-155">Establish a Persistent Connection</span></span>

<span data-ttu-id="bb4f4-156">Gebruik de `New-PSSession` cmdlet om een permanente sessie te maken op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-156">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="bb4f4-157">In het volgende voor beeld worden externe sessies gemaakt op Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-157">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="bb4f4-158">De sessie objecten worden opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-158">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="bb4f4-159">Nu u de sessies tot stand hebt gebracht, kunt u elke opdracht in ze uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="bb4f4-160">En omdat de sessies permanent zijn, kunt u gegevens verzamelen van de ene opdracht en deze gebruiken in een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-160">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="bb4f4-161">Met de volgende opdracht wordt bijvoorbeeld een Get-HotFix-opdracht uitgevoerd in de sessies in de $s variabele en worden de resultaten opgeslagen in de $h variabele.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="bb4f4-162">De variabele $h wordt gemaakt in elk van de sessies in $s, maar deze komt niet voor in de lokale sessie.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-162">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="bb4f4-163">Nu kunt u de gegevens in de `$h` variabele gebruiken met andere opdrachten in dezelfde sessie.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-163">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="bb4f4-164">De resultaten worden weer gegeven op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-164">The results are displayed on the local computer.</span></span> <span data-ttu-id="bb4f4-165">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bb4f4-165">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="bb4f4-166">Geavanceerde externe communicatie</span><span class="sxs-lookup"><span data-stu-id="bb4f4-166">Advanced Remoting</span></span>

<span data-ttu-id="bb4f4-167">Windows Power shell Remote Management begint hier gewoon.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-167">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="bb4f4-168">Door gebruik te maken van de cmdlets die zijn geïnstalleerd met Windows Power shell, kunt u externe sessies instellen en configureren op basis van de lokale en externe eind punten, aangepaste en beperkte sessies opstellen, gebruikers opdrachten laten importeren uit een externe sessie die daad werkelijk impliciet is uitgevoerd op de externe sessie, de beveiliging van een externe sessie configureren, en nog veel meer.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-168">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="bb4f4-169">Windows Power shell bevat een WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-169">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="bb4f4-170">De provider maakt een `WSMAN:` station waarmee u kunt navigeren door een hiërarchie van configuratie-instellingen op de lokale computer en externe computers.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-170">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="bb4f4-171">Zie voor meer informatie over de WSMan-provider [wsman-provider](/powershell/module/microsoft.wsman.management/about/about_wsman_provider) en [over WS-Management-cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets), of typ in de Windows Power shell-console `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="bb4f4-171">For more information about the WSMan provider, see [WSMan Provider](/powershell/module/microsoft.wsman.management/about/about_wsman_provider) and [About WS-Management Cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="bb4f4-172">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="bb4f4-172">For more information, see:</span></span>

- [<span data-ttu-id="bb4f4-173">Over externe Veelgestelde vragen</span><span class="sxs-lookup"><span data-stu-id="bb4f4-173">About Remote FAQ</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="bb4f4-174">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb4f4-174">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [<span data-ttu-id="bb4f4-175">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb4f4-175">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

<span data-ttu-id="bb4f4-176">Zie [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting)voor hulp bij externe fouten.</span><span class="sxs-lookup"><span data-stu-id="bb4f4-176">For help with remoting errors, see [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb4f4-177">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bb4f4-177">See Also</span></span>

- [<span data-ttu-id="bb4f4-178">about_Remote</span><span class="sxs-lookup"><span data-stu-id="bb4f4-178">about_Remote</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="bb4f4-179">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="bb4f4-179">about_Remote_FAQ</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="bb4f4-180">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="bb4f4-180">about_Remote_Requirements</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
- [<span data-ttu-id="bb4f4-181">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="bb4f4-181">about_Remote_Troubleshooting</span></span>](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting)
- [<span data-ttu-id="bb4f4-182">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="bb4f4-182">about_PSSessions</span></span>](/powershell/module/microsoft.powershell.core/about/about_PSSessions)
- [<span data-ttu-id="bb4f4-183">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="bb4f4-183">about_WS-Management_Cmdlets</span></span>](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets)
- [<span data-ttu-id="bb4f4-184">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="bb4f4-184">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="bb4f4-185">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb4f4-185">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)
- [<span data-ttu-id="bb4f4-186">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb4f4-186">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="bb4f4-187">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb4f4-187">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [<span data-ttu-id="bb4f4-188">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="bb4f4-188">WSMan Provider</span></span>](/powershell/module/microsoft.wsman.management/about/about_wsman_provider)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
