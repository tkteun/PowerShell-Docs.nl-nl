---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Externe opdrachten uit te voeren
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 5cf9690b8fe4549a99186f172cb6f0de156a4dea
ms.sourcegitcommit: c5251755c4442487f99ff74fadf7e37bbf039089
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/18/2017
---
# <a name="running-remote-commands"></a><span data-ttu-id="28808-103">Externe opdrachten uit te voeren</span><span class="sxs-lookup"><span data-stu-id="28808-103">Running Remote Commands</span></span>
<span data-ttu-id="28808-104">U kunt de opdrachten uitvoeren op een of honderden computers met een enkele Windows PowerShell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="28808-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="28808-105">Windows PowerShell biedt ondersteuning voor externe verwerking met behulp van verschillende technologieën, zoals WMI, RPC en WS-Management.</span><span class="sxs-lookup"><span data-stu-id="28808-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="28808-106">Externe toegang zonder configuratie</span><span class="sxs-lookup"><span data-stu-id="28808-106">Remoting Without Configuration</span></span>
<span data-ttu-id="28808-107">Veel Windows PowerShell-cmdlets hebben de parameter ComputerName waarmee u kunt het verzamelen van gegevens en instellingen op een of meer externe computers wijzigen.</span><span class="sxs-lookup"><span data-stu-id="28808-107">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="28808-108">Ze verschillende technologieën voor communicatie en veel werk op alle Windows-besturingssystemen die ondersteuning biedt zonder speciale configuratie voor Windows PowerShell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="28808-108">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="28808-109">Deze cmdlets zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="28808-109">These cmdlets include:</span></span>
* [<span data-ttu-id="28808-110">Computer opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="28808-110">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="28808-111">Verbinding testen</span><span class="sxs-lookup"><span data-stu-id="28808-111">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="28808-112">Schakel EventLog</span><span class="sxs-lookup"><span data-stu-id="28808-112">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="28808-113">Get-gebeurtenislogboek</span><span class="sxs-lookup"><span data-stu-id="28808-113">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="28808-114">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="28808-114">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
  - [<span data-ttu-id="28808-115">Get-Process</span><span class="sxs-lookup"><span data-stu-id="28808-115">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="28808-116">Get-Service</span><span class="sxs-lookup"><span data-stu-id="28808-116">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="28808-117">Set-Service</span><span class="sxs-lookup"><span data-stu-id="28808-117">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="28808-118">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="28808-118">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="28808-119">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="28808-119">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="28808-120">Normaal gesproken cmdlets die ondersteuning bieden voor externe toegang zonder speciale configuratie hebt de parameter ComputerName en hoeft niet de sessie-parameter.</span><span class="sxs-lookup"><span data-stu-id="28808-120">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="28808-121">Om deze cmdlets in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="28808-121">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="28808-122">Windows PowerShell voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="28808-122">Windows PowerShell Remoting</span></span>
<span data-ttu-id="28808-123">Windows PowerShell op afstand, die gebruikmaakt van het protocol WS-Management, kunt u een Windows PowerShell-opdracht uitvoeren op een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="28808-123">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="28808-124">Hiermee kunt u permanente verbindingen tot stand brengen, 1:1 interactieve sessies starten en scripts uitvoeren op meerdere computers.</span><span class="sxs-lookup"><span data-stu-id="28808-124">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="28808-125">Voor het gebruik van Windows PowerShell op afstand, moet de externe computer worden geconfigureerd voor extern beheer.</span><span class="sxs-lookup"><span data-stu-id="28808-125">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="28808-126">Zie voor meer informatie, waaronder instructies [over vereisten voor externe](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="28808-126">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="28808-127">Nadat u Windows PowerShell voor externe toegang hebt geconfigureerd, worden veel remoting strategieën voor u beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="28808-127">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="28808-128">De rest van dit document vindt u enkele van deze.</span><span class="sxs-lookup"><span data-stu-id="28808-128">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="28808-129">Zie voor meer informatie [over externe](https://technet.microsoft.com/en-us/library/dd347744.aspx) en [over veelgestelde vragen over extern](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="28808-129">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="28808-130">Een interactieve sessie starten</span><span class="sxs-lookup"><span data-stu-id="28808-130">Start an Interactive Session</span></span>
<span data-ttu-id="28808-131">Gebruikt u een interactieve sessie starten met een externe computer, de [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="28808-131">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="28808-132">Bijvoorbeeld, u een interactieve sessie starten met de externe computer Server01, typt u:</span><span class="sxs-lookup"><span data-stu-id="28808-132">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="28808-133">De wijzigingen in de opdrachtprompt om weer te geven van de naam van de computer waarop u bent verbonden.</span><span class="sxs-lookup"><span data-stu-id="28808-133">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="28808-134">Daarna alle opdrachten die u typt u bij de opdrachtprompt op de externe computer uitvoeren en de resultaten worden weergegeven op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="28808-134">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="28808-135">Als u wilt de interactieve sessie beëindigen, typt u:</span><span class="sxs-lookup"><span data-stu-id="28808-135">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="28808-136">Zie voor meer informatie over de cmdlets Enter-PSSession en afsluiten-PSSession [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) en [afsluiten-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="28808-136">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="28808-137">Een externe opdracht wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="28808-137">Run a Remote Command</span></span>
<span data-ttu-id="28808-138">Wilt willekeurige opdracht uitvoeren op een of meer externe computers, gebruikt de [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="28808-138">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="28808-139">Bijvoorbeeld, om uit te voeren een [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) opdracht op de Server01 en Server02 externe computers, type:</span><span class="sxs-lookup"><span data-stu-id="28808-139">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="28808-140">De uitvoer wordt geretourneerd naar de computer.</span><span class="sxs-lookup"><span data-stu-id="28808-140">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
<span data-ttu-id="28808-141">Zie voor meer informatie over de cmdlet Invoke-Command [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="28808-141">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="28808-142">Een Script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="28808-142">Run a Script</span></span>
<span data-ttu-id="28808-143">U kunt een script uitvoeren op een of meer externe computers door de parameter bestandspad van de cmdlet Invoke-Command te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="28808-143">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="28808-144">Het script moet op of toegankelijk is voor uw lokale computer.</span><span class="sxs-lookup"><span data-stu-id="28808-144">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="28808-145">De resultaten worden geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="28808-145">The results are returned to your local computer.</span></span>

<span data-ttu-id="28808-146">De volgende opdracht wordt het script DiskCollect.ps1 uitgevoerd op de externe computers Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="28808-146">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="28808-147">Zie voor meer informatie over de cmdlet Invoke-Command [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="28808-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="28808-148">Een permanente verbinding tot stand brengen</span><span class="sxs-lookup"><span data-stu-id="28808-148">Establish a Persistent Connection</span></span>
<span data-ttu-id="28808-149">Voor het uitvoeren van een reeks van verwante opdrachten die gegevens delen, sessie op de externe computer maken en gebruik vervolgens de cmdlet Invoke-Command opdrachten kunt uitvoeren in de sessie die u maakt.</span><span class="sxs-lookup"><span data-stu-id="28808-149">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="28808-150">Gebruik de cmdlet New-PSSession voor het maken van een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="28808-150">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="28808-151">De volgende opdracht maakt bijvoorbeeld een externe sessie op de computer Server01 en een andere externe sessie op de computer Server02.</span><span class="sxs-lookup"><span data-stu-id="28808-151">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="28808-152">De sessieobjecten worden opgeslagen in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="28808-152">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="28808-153">Nu dat de sessies tot stand gebracht worden, kunt u elke opdracht uitvoeren in ze.</span><span class="sxs-lookup"><span data-stu-id="28808-153">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="28808-154">En omdat de sessies persistent zijn, kunt u worden verzameld in één opdracht en deze in de volgende opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="28808-154">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="28808-155">Bijvoorbeeld de volgende opdracht wordt een opdracht Get-HotFix uitgevoerd in de sessies in de variabele $s en de resultaten worden opgeslagen in de variabele $h.</span><span class="sxs-lookup"><span data-stu-id="28808-155">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="28808-156">De variabele $h in elk van de sessies in $s is gemaakt, maar deze niet bestaat in de lokale sessie.</span><span class="sxs-lookup"><span data-stu-id="28808-156">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="28808-157">Nu kunt u de gegevens in de variabele $h in de volgende opdrachten, zoals de volgende.</span><span class="sxs-lookup"><span data-stu-id="28808-157">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="28808-158">De resultaten worden weergegeven op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="28808-158">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="28808-159">Geavanceerde voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="28808-159">Advanced Remoting</span></span>
<span data-ttu-id="28808-160">Windows PowerShell extern beheer begint alleen hier.</span><span class="sxs-lookup"><span data-stu-id="28808-160">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="28808-161">Met behulp van de geïnstalleerd met Windows PowerShell-cmdlets, kunt u tot stand brengen en externe sessies configureren van de lokale en externe is afgelopen, maken van aangepaste en beperkte sessies, kunnen gebruikers opdrachten voor het importeren vanuit een externe sessie die daadwerkelijk worden uitgevoerd impliciet op de externe sessie, configureert u de beveiliging van een externe sessie en nog veel meer.</span><span class="sxs-lookup"><span data-stu-id="28808-161">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="28808-162">Windows PowerShell omvat te vergemakkelijken externe configuratie, een WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="28808-162">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="28808-163">De WSMAN: station dat de provider maakt, kunt u navigeren door een hiërarchie van configuratie-instellingen op de lokale computer en externe computers.</span><span class="sxs-lookup"><span data-stu-id="28808-163">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="28808-164">Zie voor meer informatie over de WSMan-provider [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) en [over WS-Management-Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), of typ 'Get-Help wsman' in de Windows PowerShell-console.</span><span class="sxs-lookup"><span data-stu-id="28808-164">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="28808-165">Zie voor meer informatie</span><span class="sxs-lookup"><span data-stu-id="28808-165">For more information, see:</span></span>
- [<span data-ttu-id="28808-166">Over externe Veelgestelde vragen</span><span class="sxs-lookup"><span data-stu-id="28808-166">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="28808-167">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="28808-167">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="28808-168">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="28808-168">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="28808-169">Zie voor meer informatie over fouten voor externe toegang, [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="28808-169">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="28808-170">Zie ook</span><span class="sxs-lookup"><span data-stu-id="28808-170">See Also</span></span>
- [<span data-ttu-id="28808-171">about_Remote</span><span class="sxs-lookup"><span data-stu-id="28808-171">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="28808-172">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="28808-172">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="28808-173">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="28808-173">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="28808-174">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="28808-174">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="28808-175">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="28808-175">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="28808-176">about_WS Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="28808-176">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="28808-177">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="28808-177">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="28808-178">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="28808-178">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="28808-179">Nieuwe-PSSession</span><span class="sxs-lookup"><span data-stu-id="28808-179">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="28808-180">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="28808-180">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="28808-181">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="28808-181">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)
