---
ms.date: 08/14/2018
keywords: PowerShell-cmdlet
title: Externe opdrachten uitvoeren
ms.openlocfilehash: d6609deafd8dec4f34a8412439d87dacd20d46f1
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030309"
---
# <a name="running-remote-commands"></a><span data-ttu-id="c961b-103">Externe opdrachten uitvoeren</span><span class="sxs-lookup"><span data-stu-id="c961b-103">Running Remote Commands</span></span>

<span data-ttu-id="c961b-104">U kunt opdrachten uitvoeren op een of honderden computers met slechts één PowerShell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="c961b-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="c961b-105">Windows PowerShell biedt ondersteuning voor externe computing met behulp van verschillende technologieën, zoals WMI, RPC en WS-Management.</span><span class="sxs-lookup"><span data-stu-id="c961b-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="c961b-106">PowerShell Core biedt ondersteuning voor WMI, WS-Management en SSH voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="c961b-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="c961b-107">RPC wordt niet meer ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c961b-107">RPC is no longer supported.</span></span>

<span data-ttu-id="c961b-108">Zie voor meer informatie over externe communicatie in PowerShell Core, de volgende artikelen:</span><span class="sxs-lookup"><span data-stu-id="c961b-108">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="c961b-109">[SSH in PowerShell Core voor externe toegang][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="c961b-109">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="c961b-110">[Externe communicatie van WSMan in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="c961b-110">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="c961b-111">Windows PowerShell voor externe toegang zonder configuratie</span><span class="sxs-lookup"><span data-stu-id="c961b-111">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="c961b-112">Veel Windows PowerShell-cmdlets hebben de parameter ComputerName waarmee u voor het verzamelen van gegevens en instellingen op een of meer externe computers wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c961b-112">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="c961b-113">Deze cmdlets gebruikt verschillende communicatieprotocollen en werkt op alle Windows-besturingssystemen zonder speciale configuratie.</span><span class="sxs-lookup"><span data-stu-id="c961b-113">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="c961b-114">Deze cmdlets zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="c961b-114">These cmdlets include:</span></span>

- [<span data-ttu-id="c961b-115">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="c961b-115">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="c961b-116">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="c961b-116">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="c961b-117">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="c961b-117">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="c961b-118">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="c961b-118">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="c961b-119">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="c961b-119">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="c961b-120">Get-Process</span><span class="sxs-lookup"><span data-stu-id="c961b-120">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="c961b-121">Get-Service</span><span class="sxs-lookup"><span data-stu-id="c961b-121">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="c961b-122">Set-Service</span><span class="sxs-lookup"><span data-stu-id="c961b-122">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="c961b-123">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="c961b-123">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="c961b-124">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="c961b-124">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="c961b-125">Normaal gesproken cmdlets die ondersteuning bieden voor externe toegang zonder speciale configuratie hebt de parameter ComputerName en hoeft de sessie-parameter.</span><span class="sxs-lookup"><span data-stu-id="c961b-125">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="c961b-126">U vindt deze cmdlets in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="c961b-126">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="c961b-127">Windows PowerShell voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="c961b-127">Windows PowerShell Remoting</span></span>

<span data-ttu-id="c961b-128">Windows PowerShell voor externe toegang kunt met behulp van het protocol WS-Management, u een Windows PowerShell-opdracht uitvoeren op een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="c961b-128">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="c961b-129">U kunt permanente verbindingen tot stand brengen, interactieve sessies starten en scripts uitvoeren op externe computers.</span><span class="sxs-lookup"><span data-stu-id="c961b-129">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="c961b-130">Voor het gebruik van Windows PowerShell voor externe toegang, moet de externe computer worden geconfigureerd voor extern beheer.</span><span class="sxs-lookup"><span data-stu-id="c961b-130">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="c961b-131">Zie voor meer informatie, inclusief instructies [over externe vereisten](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="c961b-131">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="c961b-132">Nadat u Windows PowerShell voor externe toegang hebt geconfigureerd, worden veel externe communicatie van strategieën voor u beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="c961b-132">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="c961b-133">Dit artikel worden slechts enkele van deze.</span><span class="sxs-lookup"><span data-stu-id="c961b-133">This article lists just a few of them.</span></span> <span data-ttu-id="c961b-134">Zie voor meer informatie, [over externe](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="c961b-134">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="c961b-135">Start een interactieve sessie</span><span class="sxs-lookup"><span data-stu-id="c961b-135">Start an Interactive Session</span></span>

<span data-ttu-id="c961b-136">Gebruiken om een interactieve sessie starten met een externe computer, de [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c961b-136">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span>
<span data-ttu-id="c961b-137">Bijvoorbeeld, om een interactieve sessie starten met de externe computer Server01, typt u:</span><span class="sxs-lookup"><span data-stu-id="c961b-137">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="c961b-138">De wijzigingen van de opdrachtprompt om weer te geven van de naam van de externe computer.</span><span class="sxs-lookup"><span data-stu-id="c961b-138">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="c961b-139">Alle opdrachten die u typt u bij de opdrachtprompt worden uitgevoerd op de externe computer en de resultaten worden weergegeven op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c961b-139">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="c961b-140">Als u de interactieve sessie beëindigen, typt u:</span><span class="sxs-lookup"><span data-stu-id="c961b-140">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="c961b-141">Zie voor meer informatie over de Enter-PSSession en afsluiten PSSession-cmdlets:</span><span class="sxs-lookup"><span data-stu-id="c961b-141">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="c961b-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="c961b-142">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="c961b-143">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="c961b-143">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="c961b-144">Een externe opdracht uitvoeren</span><span class="sxs-lookup"><span data-stu-id="c961b-144">Run a Remote Command</span></span>

<span data-ttu-id="c961b-145">Als u wilt een opdracht uitvoeren op een of meer computers, gebruiken de [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c961b-145">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="c961b-146">Bijvoorbeeld, om uit te voeren een [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) opdracht op de Server01 en Server02 externe computers, type:</span><span class="sxs-lookup"><span data-stu-id="c961b-146">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="c961b-147">De uitvoer wordt geretourneerd naar de computer.</span><span class="sxs-lookup"><span data-stu-id="c961b-147">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="c961b-148">Een Script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="c961b-148">Run a Script</span></span>

<span data-ttu-id="c961b-149">Als u wilt een script uitvoeren op een of meer externe computers, gebruikt u de parameter van het bestandspad van de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c961b-149">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="c961b-150">Het script moet op of toegankelijk is voor uw lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c961b-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="c961b-151">De resultaten worden geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c961b-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="c961b-152">De volgende opdracht wordt bijvoorbeeld het DiskCollect.ps1-script uitgevoerd op de externe computers, Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="c961b-152">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="c961b-153">Een permanente verbinding tot stand brengen</span><span class="sxs-lookup"><span data-stu-id="c961b-153">Establish a Persistent Connection</span></span>

<span data-ttu-id="c961b-154">Gebruik de `New-PSSession` cmdlet voor het maken van een permanente sessie op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="c961b-154">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="c961b-155">Het volgende voorbeeld wordt een externe sessies op Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="c961b-155">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="c961b-156">De sessieobjecten worden opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="c961b-156">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="c961b-157">Nu dat de sessies tot stand worden gebracht, kunt u een opdracht uitvoeren in deze.</span><span class="sxs-lookup"><span data-stu-id="c961b-157">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="c961b-158">En omdat de sessies persistent zijn, kunt u gegevens verzamelen in één opdracht en deze gebruiken in een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="c961b-158">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="c961b-159">Bijvoorbeeld een Get-HotFix-opdracht in de volgende opdracht wordt uitgevoerd in de sessies in de variabele $s en de resultaten worden opgeslagen in de variabele $h.</span><span class="sxs-lookup"><span data-stu-id="c961b-159">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="c961b-160">De variabele $h in elk van de sessies in $s is gemaakt, maar deze nog niet bestaat in de lokale sessie.</span><span class="sxs-lookup"><span data-stu-id="c961b-160">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="c961b-161">Nu kunt u de gegevens in de `$h` variabele met andere opdrachten in dezelfde sessie.</span><span class="sxs-lookup"><span data-stu-id="c961b-161">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="c961b-162">De resultaten worden weergegeven op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c961b-162">The results are displayed on the local computer.</span></span> <span data-ttu-id="c961b-163">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="c961b-163">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="c961b-164">Geavanceerde voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="c961b-164">Advanced Remoting</span></span>

<span data-ttu-id="c961b-165">Windows PowerShell extern beheer alleen hier begint.</span><span class="sxs-lookup"><span data-stu-id="c961b-165">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="c961b-166">Met behulp van de cmdlets die met Windows PowerShell is geïnstalleerd, kunt u tot stand brengen en externe sessies configureren bij de uiteinden lokale en externe maken van aangepaste en beperkte sessies, kunnen gebruikers opdrachten voor het importeren van een externe sessie die daadwerkelijk wordt uitgevoerd impliciet op de externe sessie, configureert u de beveiliging van een externe sessie en nog veel meer.</span><span class="sxs-lookup"><span data-stu-id="c961b-166">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="c961b-167">Windows PowerShell omvat een WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="c961b-167">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="c961b-168">Hiermee maakt u de provider een `WSMAN:` station waarmee u navigeren door een hiërarchie van configuratie-instellingen op de lokale computer en externe computers.</span><span class="sxs-lookup"><span data-stu-id="c961b-168">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="c961b-169">Zie voor meer informatie over de WSMan-provider [WSMan-Provider](https://technet.microsoft.com/library/dd819476.aspx) en [over WS-Management-Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), of typ in de Windows PowerShell-console `Get-Help wsman`.</span><span class="sxs-lookup"><span data-stu-id="c961b-169">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="c961b-170">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="c961b-170">For more information, see:</span></span>

- [<span data-ttu-id="c961b-171">Over veelgestelde vragen over externe</span><span class="sxs-lookup"><span data-stu-id="c961b-171">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="c961b-172">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c961b-172">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="c961b-173">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="c961b-173">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="c961b-174">Zie voor hulp bij externe communicatie van fouten, [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="c961b-174">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="c961b-175">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c961b-175">See Also</span></span>

- [<span data-ttu-id="c961b-176">about_Remote</span><span class="sxs-lookup"><span data-stu-id="c961b-176">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="c961b-177">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="c961b-177">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="c961b-178">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="c961b-178">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="c961b-179">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="c961b-179">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="c961b-180">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="c961b-180">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="c961b-181">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c961b-181">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="c961b-182">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="c961b-182">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="c961b-183">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="c961b-183">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="c961b-184">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="c961b-184">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="c961b-185">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c961b-185">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="c961b-186">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="c961b-186">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
