---
description: Bevat vragen en antwoorden over het uitvoeren van externe opdrachten in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_FAQ
ms.openlocfilehash: da70a3a563031a04aeffd1ead692d9a605f14042
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252753"
---
# <a name="about-remote-faq"></a><span data-ttu-id="d9dec-104">Over externe Veelgestelde vragen</span><span class="sxs-lookup"><span data-stu-id="d9dec-104">About Remote FAQ</span></span>

## <a name="short-description"></a><span data-ttu-id="d9dec-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="d9dec-105">Short description</span></span>
<span data-ttu-id="d9dec-106">Bevat vragen en antwoorden over het uitvoeren van externe opdrachten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="d9dec-106">Contains questions and answers about running remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="d9dec-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="d9dec-107">Long description</span></span>

<span data-ttu-id="d9dec-108">Wanneer u op afstand werkt, typt u opdrachten in Power shell op één computer (ook wel ' lokale computer ' genoemd), maar de opdrachten worden uitgevoerd op een andere computer (ook wel ' externe computer ' genoemd).</span><span class="sxs-lookup"><span data-stu-id="d9dec-108">When you work remotely, you type commands in PowerShell on one computer (known as the "local computer"), but the commands run on another computer (known as the "remote computer").</span></span> <span data-ttu-id="d9dec-109">De ervaring van het werken op afstand moet zo veel mogelijk rechtstreeks op de externe computer werken.</span><span class="sxs-lookup"><span data-stu-id="d9dec-109">The experience of working remotely should be as much like working directly at the remote computer as possible.</span></span>

<span data-ttu-id="d9dec-110">Opmerking: als u externe communicatie met Power shell wilt gebruiken, moet u de Remote computer configureren voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="d9dec-110">Note: To use PowerShell remoting, the remote computer must be configured for remoting.</span></span> <span data-ttu-id="d9dec-111">Zie [about_Remote_Requirements](about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d9dec-111">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

### <a name="must-both-computers-have-powershell-installed"></a><span data-ttu-id="d9dec-112">Moeten op beide computers Power shell zijn geïnstalleerd?</span><span class="sxs-lookup"><span data-stu-id="d9dec-112">Must both computers have PowerShell installed?</span></span>

<span data-ttu-id="d9dec-113">Ja.</span><span class="sxs-lookup"><span data-stu-id="d9dec-113">Yes.</span></span> <span data-ttu-id="d9dec-114">Om op afstand te kunnen werken, moeten de lokale en externe computers Power shell, het Microsoft .NET Framework en het protocol Web Services for Management (WS-Management) hebben.</span><span class="sxs-lookup"><span data-stu-id="d9dec-114">To work remotely, the local and remote computers must have PowerShell, the Microsoft .NET Framework, and the Web Services for Management (WS-Management) protocol.</span></span> <span data-ttu-id="d9dec-115">Alle bestanden en andere bronnen die nodig zijn voor het uitvoeren van een bepaalde opdracht, moeten zich op de externe computer bevinden.</span><span class="sxs-lookup"><span data-stu-id="d9dec-115">Any files and other resources that are needed to execute a particular command must be on the remote computer.</span></span>

<span data-ttu-id="d9dec-116">Computers met Windows Power Shell 3,0 en computers met Windows Power Shell 2,0 kunnen extern verbinding maken met elkaar en externe opdrachten uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="d9dec-116">Computers running Windows PowerShell 3.0 and computers running Windows PowerShell 2.0 can connect to each other remotely and run remote commands.</span></span>
<span data-ttu-id="d9dec-117">Sommige functies, zoals de mogelijkheid om de verbinding met een sessie te verbreken en opnieuw verbinding te maken, werken echter alleen als Windows Power Shell 3,0 wordt uitgevoerd op beide computers.</span><span class="sxs-lookup"><span data-stu-id="d9dec-117">However, some features, such as the ability to disconnect from a session and reconnect to it, work only when both computers are running Windows PowerShell 3.0.</span></span>

<span data-ttu-id="d9dec-118">U moet gemachtigd zijn om verbinding te maken met de externe computer, om Power shell uit te voeren en om toegang te krijgen tot gegevens archieven (zoals bestanden en mappen) en het REGI ster op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-118">You must have permission to connect to the remote computer, permission to run PowerShell, and permission to access data stores (such as files and folders), and the registry on the remote computer.</span></span>

<span data-ttu-id="d9dec-119">Zie [about_Remote_Requirements](about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d9dec-119">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

### <a name="how-does-remoting-work"></a><span data-ttu-id="d9dec-120">Hoe werkt externe communicatie?</span><span class="sxs-lookup"><span data-stu-id="d9dec-120">How does remoting work?</span></span>

<span data-ttu-id="d9dec-121">Wanneer u een externe opdracht verzendt, wordt de opdracht via het netwerk verzonden naar de Power shell-engine op de externe computer en wordt deze uitgevoerd in de Power shell-client op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-121">When you submit a remote command, the command is transmitted across the network to the PowerShell engine on the remote computer, and it runs in the PowerShell client on the remote computer.</span></span> <span data-ttu-id="d9dec-122">De resultaten van de opdracht worden teruggestuurd naar de lokale computer en worden weer gegeven in de Power shell-sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-122">The command results are sent back to the local computer and appear in the PowerShell session on the local computer.</span></span>

<span data-ttu-id="d9dec-123">Als u de opdrachten wilt verzenden en de uitvoer wilt ontvangen, gebruikt Power shell het WS-Management protocol.</span><span class="sxs-lookup"><span data-stu-id="d9dec-123">To transmit the commands and receive the output, PowerShell uses the WS-Management protocol.</span></span> <span data-ttu-id="d9dec-124">Zie het [WS-Management-Protocol](/windows/win32/winrm/ws-management-protocol) in de Windows-documentatie voor meer informatie over het WS-Management-protocol.</span><span class="sxs-lookup"><span data-stu-id="d9dec-124">For information about the WS-Management protocol, see [WS-Management Protocol](/windows/win32/winrm/ws-management-protocol) in the Windows documentation.</span></span>

<span data-ttu-id="d9dec-125">Vanaf Windows Power Shell 3,0 worden externe sessies opgeslagen op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-125">Beginning in Windows PowerShell 3.0, remote sessions are stored on the remote computer.</span></span> <span data-ttu-id="d9dec-126">Zo kunt u de verbinding met de sessie verbreken en opnieuw verbinding maken met een andere sessie of een andere computer zonder de opdrachten te onderbreken of de status verlies te verliezen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-126">This enables you to disconnect from the session and reconnect from a different session or a different computer without interrupting the commands or losing state.</span></span>

### <a name="is-powershell-remoting-secure"></a><span data-ttu-id="d9dec-127">Is externe communicatie van Power shell veilig?</span><span class="sxs-lookup"><span data-stu-id="d9dec-127">Is PowerShell remoting secure?</span></span>

<span data-ttu-id="d9dec-128">Wanneer u verbinding maakt met een externe computer, gebruikt het systeem de gebruikers naam en het wacht woord op de lokale computer of de referenties die u opgeeft in de opdracht om u aan te melden bij de externe computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-128">When you connect to a remote computer, the system uses the username and password credentials on the local computer or the credentials that you supply in the command to log you in to the remote computer.</span></span> <span data-ttu-id="d9dec-129">De referenties en de rest van de overdracht worden versleuteld.</span><span class="sxs-lookup"><span data-stu-id="d9dec-129">The credentials and the rest of the transmission are encrypted.</span></span>

<span data-ttu-id="d9dec-130">Om extra beveiliging toe te voegen, kunt u de externe computer configureren voor het gebruik van Secure Sockets Layer (SSL) in plaats van HTTP om te Luis teren naar aanvragen van Windows Remote Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="d9dec-130">To add additional protection, you can configure the remote computer to use Secure Sockets Layer (SSL) instead of HTTP to listen for Windows Remote Management (WinRM) requests.</span></span> <span data-ttu-id="d9dec-131">Vervolgens kunnen gebruikers de para meter **UseSSL** van de `Invoke-Command` `New-PSSession` cmdlets, en gebruiken `Enter-PSSession` bij het tot stand brengen van een verbinding.</span><span class="sxs-lookup"><span data-stu-id="d9dec-131">Then, users can use the **UseSSL** parameter of the `Invoke-Command`, `New-PSSession`, and `Enter-PSSession` cmdlets when establishing a connection.</span></span> <span data-ttu-id="d9dec-132">Deze optie maakt gebruik van het veiligere HTTPS-kanaal in plaats van HTTP.</span><span class="sxs-lookup"><span data-stu-id="d9dec-132">This option uses the more secure HTTPS channel instead of HTTP.</span></span>

### <a name="do-all-remote-commands-require-powershell-remoting"></a><span data-ttu-id="d9dec-133">Zijn voor alle externe opdrachten Power shell Remoting vereist?</span><span class="sxs-lookup"><span data-stu-id="d9dec-133">Do all remote commands require PowerShell remoting?</span></span>

<span data-ttu-id="d9dec-134">Nee.</span><span class="sxs-lookup"><span data-stu-id="d9dec-134">No.</span></span> <span data-ttu-id="d9dec-135">Verschillende cmdlets hebben de para meter **ComputerName** waarmee u objecten van de externe computer kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-135">Several cmdlets have a **ComputerName** parameter that lets you get objects from the remote computer.</span></span>

<span data-ttu-id="d9dec-136">Deze cmdlets maken geen gebruik van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="d9dec-136">These cmdlets do not use PowerShell remoting.</span></span> <span data-ttu-id="d9dec-137">U kunt ze dus op elke computer met Power shell gebruiken, zelfs als de computer niet is geconfigureerd voor externe communicatie met Power shell of als de computer niet voldoet aan de vereisten voor externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="d9dec-137">So, you can use them on any computer that is running PowerShell, even if the computer is not configured for PowerShell remoting or if the computer does not meet the requirements for PowerShell remoting.</span></span>

<span data-ttu-id="d9dec-138">Dit zijn onder andere de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="d9dec-138">These cmdlets include the following:</span></span>

- `Get-Process`
- `Get-Service`
- `Get-WinEvent`
- `Get-EventLog`
- `Test-Connection`

<span data-ttu-id="d9dec-139">Als u alle cmdlets wilt zoeken met de para meter **ComputerName** , typt u:</span><span class="sxs-lookup"><span data-stu-id="d9dec-139">To find all the cmdlets with a **ComputerName** parameter, type:</span></span>

```powershell
Get-Help * -Parameter ComputerName
# or
Get-Command -ParameterName ComputerName
```

<span data-ttu-id="d9dec-140">Als u wilt weten of de para meter **ComputerName** van een bepaalde cmdlet Power shell Remoting vereist, raadpleegt u de parameter beschrijving.</span><span class="sxs-lookup"><span data-stu-id="d9dec-140">To determine whether the **ComputerName** parameter of a particular cmdlet requires PowerShell remoting, see the parameter description.</span></span> <span data-ttu-id="d9dec-141">Als u de parameter beschrijving wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="d9dec-141">To display the parameter description, type:</span></span>

```powershell
Get-Help <cmdlet-name> -Parameter ComputerName
```

<span data-ttu-id="d9dec-142">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d9dec-142">For example:</span></span>

```powershell
Get-Help Get-Process -Parameter ComputerName
```

<span data-ttu-id="d9dec-143">Voor alle andere opdrachten, gebruikt u de- `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9dec-143">For all other commands, use the `Invoke-Command` cmdlet.</span></span>

### <a name="how-do-i-run-a-command-on-a-remote-computer"></a><span data-ttu-id="d9dec-144">Hoe kan ik een opdracht op een externe computer uit te voeren?</span><span class="sxs-lookup"><span data-stu-id="d9dec-144">How do I run a command on a remote computer?</span></span>

<span data-ttu-id="d9dec-145">Als u een opdracht wilt uitvoeren op een externe computer, gebruikt u de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9dec-145">To run a command on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="d9dec-146">Plaats de opdracht in accolades ( `{}` ) om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="d9dec-146">Enclose your command in braces (`{}`) to make it a script block.</span></span> <span data-ttu-id="d9dec-147">Gebruik de para meter **script Block** van `Invoke-Command` om de opdracht op te geven.</span><span class="sxs-lookup"><span data-stu-id="d9dec-147">Use the **ScriptBlock** parameter of `Invoke-Command` to specify the command.</span></span>

<span data-ttu-id="d9dec-148">U kunt de para meter **ComputerName** van gebruiken `Invoke-Command` om een externe computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="d9dec-148">You can use the **ComputerName** parameter of `Invoke-Command` to specify a remote computer.</span></span> <span data-ttu-id="d9dec-149">U kunt ook een permanente verbinding met een externe computer (een sessie) maken en vervolgens de **sessie** parameter van gebruiken `Invoke-Command` om de opdracht uit te voeren in de sessie.</span><span class="sxs-lookup"><span data-stu-id="d9dec-149">Or, you can create a persistent connection to a remote computer (a session) and then use the **Session** parameter of `Invoke-Command` to run the command in the session.</span></span>

<span data-ttu-id="d9dec-150">Met de volgende opdrachten wordt `Get-Process` op afstand een opdracht uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d9dec-150">For example, the following commands run a `Get-Process` command remotely.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-Process}

#  - OR -

Invoke-Command -Session $s -ScriptBlock {Get-Process}
```

<span data-ttu-id="d9dec-151">Als u een externe opdracht wilt onderbreken, typt u <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d9dec-151">To interrupt a remote command, type <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="d9dec-152">De aanvraag voor de onderbreking wordt door gegeven aan de externe computer, waar de externe opdracht wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="d9dec-152">The interruption request is passed to the remote computer, where it terminates the remote command.</span></span>

<span data-ttu-id="d9dec-153">Zie about_Remote en de Help-onderwerpen voor de cmdlets die ondersteuning bieden voor externe toegang voor meer informatie over externe opdrachten.</span><span class="sxs-lookup"><span data-stu-id="d9dec-153">For more information about remote commands, see about_Remote and the Help topics for the cmdlets that support remoting.</span></span>

### <a name="can-i-just-telnet-into-a-remote-computer"></a><span data-ttu-id="d9dec-154">Kan ik gewoon Telnet op een externe computer?</span><span class="sxs-lookup"><span data-stu-id="d9dec-154">Can I just telnet into a remote computer?</span></span>

<span data-ttu-id="d9dec-155">U kunt de `Enter-PSSession` cmdlet gebruiken om een interactieve sessie met een externe computer te starten.</span><span class="sxs-lookup"><span data-stu-id="d9dec-155">You can use the `Enter-PSSession` cmdlet to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="d9dec-156">Typ het volgende bij de Power shell-prompt:</span><span class="sxs-lookup"><span data-stu-id="d9dec-156">At the PowerShell prompt, type:</span></span>

```powershell
Enter-PSSession <ComputerName>
```

<span data-ttu-id="d9dec-157">De opdracht prompt wordt weer gegeven om aan te geven dat u verbinding hebt met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-157">The command prompt changes to show that you are connected to the remote computer.</span></span>

```
<ComputerName>\C:>
```

<span data-ttu-id="d9dec-158">Nu worden de opdrachten die u typt op de externe computer uitgevoerd, net zoals u ze rechtstreeks op de externe computer hebt getypt.</span><span class="sxs-lookup"><span data-stu-id="d9dec-158">Now, the commands that you type run on the remote computer just as though you typed them directly on the remote computer.</span></span>

<span data-ttu-id="d9dec-159">Als u de interactieve sessie wilt beëindigen, typt u:</span><span class="sxs-lookup"><span data-stu-id="d9dec-159">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="d9dec-160">Een interactieve sessie is een permanente sessie die gebruikmaakt van het WS-Management-protocol.</span><span class="sxs-lookup"><span data-stu-id="d9dec-160">An interactive session is a persistent session that uses the WS-Management protocol.</span></span> <span data-ttu-id="d9dec-161">Het is niet hetzelfde als het gebruik van Telnet, maar het biedt een vergelijk bare ervaring.</span><span class="sxs-lookup"><span data-stu-id="d9dec-161">It is not the same as using Telnet, but it provides a similar experience.</span></span>

<span data-ttu-id="d9dec-162">Voor meer informatie raadpleegt u `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="d9dec-162">For more information, see `Enter-PSSession`.</span></span>

### <a name="can-i-create-a-persistent-connection"></a><span data-ttu-id="d9dec-163">Kan ik een permanente verbinding maken?</span><span class="sxs-lookup"><span data-stu-id="d9dec-163">Can I create a persistent connection?</span></span>

<span data-ttu-id="d9dec-164">Ja.</span><span class="sxs-lookup"><span data-stu-id="d9dec-164">Yes.</span></span> <span data-ttu-id="d9dec-165">U kunt externe opdrachten uitvoeren door de naam van de externe computer, de NetBIOS-naam of het IP-adres op te geven.</span><span class="sxs-lookup"><span data-stu-id="d9dec-165">You can run remote commands by specifying the name of the remote computer, its NetBIOS name, or its IP address.</span></span> <span data-ttu-id="d9dec-166">U kunt ook externe opdrachten uitvoeren door een Power shell-sessie (PSSession) op te geven die is verbonden met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-166">Or, you can run remote commands by specifying a PowerShell session (PSSession) that is connected to the remote computer.</span></span>

<span data-ttu-id="d9dec-167">Wanneer u de para meter **ComputerName** van `Invoke-Command` of gebruikt `Enter-PSSession` , brengt Power shell een tijdelijke verbinding tot stand.</span><span class="sxs-lookup"><span data-stu-id="d9dec-167">When you use the **ComputerName** parameter of `Invoke-Command` or `Enter-PSSession`, PowerShell establishes a temporary connection.</span></span> <span data-ttu-id="d9dec-168">Power shell gebruikt de verbinding om alleen de huidige opdracht uit te voeren, waarna de verbinding wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="d9dec-168">PowerShell uses the connection to run only the current command, and then it closes the connection.</span></span> <span data-ttu-id="d9dec-169">Dit is een zeer efficiënte methode voor het uitvoeren van één opdracht of meerdere niet-gerelateerde opdrachten, zelfs op veel externe computers.</span><span class="sxs-lookup"><span data-stu-id="d9dec-169">This is a very efficient method for running a single command or several unrelated commands, even on many remote computers.</span></span>

<span data-ttu-id="d9dec-170">Wanneer u de `New-PSSession` -cmdlet gebruikt om een PSSession te maken, brengt Power shell een permanente verbinding tot stand voor de PSSession.</span><span class="sxs-lookup"><span data-stu-id="d9dec-170">When you use the `New-PSSession` cmdlet to create a PSSession, PowerShell establishes a persistent connection for the PSSession.</span></span> <span data-ttu-id="d9dec-171">Vervolgens kunt u meerdere opdrachten uitvoeren in de PSSession, waaronder opdrachten voor het delen van gegevens.</span><span class="sxs-lookup"><span data-stu-id="d9dec-171">Then, you can run multiple commands in the PSSession, including commands that share data.</span></span>

<span data-ttu-id="d9dec-172">Normaal gesp roken maakt u een PSSession om een reeks gerelateerde opdrachten uit te voeren die gegevens delen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-172">Typically, you create a PSSession to run a series of related commands that share data.</span></span> <span data-ttu-id="d9dec-173">Anders is de tijdelijke verbinding die is gemaakt door de para meter **ComputerName** voldoende voor de meeste opdrachten.</span><span class="sxs-lookup"><span data-stu-id="d9dec-173">Otherwise, the temporary connection created by the **ComputerName** parameter is sufficient for most commands.</span></span>

<span data-ttu-id="d9dec-174">Zie about_PSSessions voor meer informatie over sessies.</span><span class="sxs-lookup"><span data-stu-id="d9dec-174">For more information about sessions, see about_PSSessions.</span></span>

### <a name="can-i-run-commands-on-more-than-one-computer-at-a-time"></a><span data-ttu-id="d9dec-175">Kan ik opdrachten op meer dan één computer tegelijk uitvoeren?</span><span class="sxs-lookup"><span data-stu-id="d9dec-175">Can I run commands on more than one computer at a time?</span></span>

<span data-ttu-id="d9dec-176">Ja.</span><span class="sxs-lookup"><span data-stu-id="d9dec-176">Yes.</span></span> <span data-ttu-id="d9dec-177">De para meter **ComputerName** van de `Invoke-Command` cmdlet accepteert meerdere computer namen en de **sessie** parameter accepteert meerdere PSSessions.</span><span class="sxs-lookup"><span data-stu-id="d9dec-177">The **ComputerName** parameter of the `Invoke-Command` cmdlet accepts multiple computer names, and the **Session** parameter accepts multiple PSSessions.</span></span>

<span data-ttu-id="d9dec-178">Wanneer u een `Invoke-Command` opdracht uitvoert, voert Power shell de opdrachten uit op alle opgegeven computers of in alle opgegeven PSSessions.</span><span class="sxs-lookup"><span data-stu-id="d9dec-178">When you run an `Invoke-Command` command, PowerShell runs the commands on all of the specified computers or in all of the specified PSSessions.</span></span>

<span data-ttu-id="d9dec-179">In Power shell kunnen honderden gelijktijdige externe verbindingen worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="d9dec-179">PowerShell can manage hundreds of concurrent remote connections.</span></span> <span data-ttu-id="d9dec-180">Het aantal externe opdrachten dat u kunt verzenden, kan echter worden beperkt door de bronnen van uw computer en de capaciteit om meerdere netwerk verbindingen tot stand te brengen en te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="d9dec-180">However, the number of remote commands that you can send might be limited by the resources of your computer and its capacity to establish and maintain multiple network connections.</span></span>

<span data-ttu-id="d9dec-181">Zie het voor beeld in het Help-onderwerp voor meer informatie `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="d9dec-181">For more information, see the example in the `Invoke-Command` Help topic.</span></span>

### <a name="where-are-my-profiles"></a><span data-ttu-id="d9dec-182">Waar bevinden zich mijn profielen?</span><span class="sxs-lookup"><span data-stu-id="d9dec-182">Where are my profiles?</span></span>

<span data-ttu-id="d9dec-183">Power shell-profielen worden niet automatisch uitgevoerd in externe sessies, zodat de opdrachten die het profiel toevoegt, niet aanwezig zijn in de sessie.</span><span class="sxs-lookup"><span data-stu-id="d9dec-183">PowerShell profiles are not run automatically in remote sessions, so the commands that the profile adds are not present in the session.</span></span> <span data-ttu-id="d9dec-184">Daarnaast `$profile` wordt de automatische variabele niet ingevuld in externe sessies.</span><span class="sxs-lookup"><span data-stu-id="d9dec-184">In addition, the `$profile` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="d9dec-185">Als u een profiel in een sessie wilt uitvoeren, gebruikt u de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9dec-185">To run a profile in a session, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="d9dec-186">Met de volgende opdracht wordt bijvoorbeeld het CurrentUserCurrentHost-profiel uitgevoerd van de lokale computer in de sessie in `$s` .</span><span class="sxs-lookup"><span data-stu-id="d9dec-186">For example, the following command runs the CurrentUserCurrentHost profile from the local computer in the session in `$s`.</span></span>

```
Invoke-Command -Session $s -FilePath $profile
```

<span data-ttu-id="d9dec-187">Met de volgende opdracht wordt het CurrentUserCurrentHost-profiel uitgevoerd vanaf de externe computer in de sessie in `$s` .</span><span class="sxs-lookup"><span data-stu-id="d9dec-187">The following command runs the CurrentUserCurrentHost profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="d9dec-188">Omdat de `$profile` variabele niet is ingevuld, gebruikt de opdracht het expliciete pad naar het profiel.</span><span class="sxs-lookup"><span data-stu-id="d9dec-188">Because the `$profile` variable is not populated, the command uses the explicit path to the profile.</span></span>

```powershell
Invoke-Command -Session $s {
  . "$home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="d9dec-189">Nadat u deze opdracht hebt uitgevoerd, zijn de opdrachten die door het profiel aan de sessie worden toegevoegd, beschikbaar in `$s` .</span><span class="sxs-lookup"><span data-stu-id="d9dec-189">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

<span data-ttu-id="d9dec-190">U kunt ook een opstart script in een sessie configuratie gebruiken om een profiel uit te voeren in elke externe sessie die gebruikmaakt van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="d9dec-190">You can also use a startup script in a session configuration to run a profile in every remote session that uses the session configuration.</span></span>

<span data-ttu-id="d9dec-191">Zie about_Profiles voor meer informatie over Power shell-profielen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-191">For more information about PowerShell profiles, see about_Profiles.</span></span>
<span data-ttu-id="d9dec-192">Zie voor meer informatie over sessie configuraties `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="d9dec-192">For more information about session configurations, see `Register-PSSessionConfiguration`.</span></span>

### <a name="how-does-throttling-work-on-remote-commands"></a><span data-ttu-id="d9dec-193">Hoe werkt het beperken op externe opdrachten?</span><span class="sxs-lookup"><span data-stu-id="d9dec-193">How does throttling work on remote commands?</span></span>

<span data-ttu-id="d9dec-194">Om u te helpen bij het beheren van de resources op uw lokale computer, bevat Power shell een functie beperking per opdracht waarmee u het aantal gelijktijdige externe verbindingen kunt beperken dat voor elke opdracht tot stand wordt gebracht.</span><span class="sxs-lookup"><span data-stu-id="d9dec-194">To help you manage the resources on your local computer, PowerShell includes a per-command throttling feature that lets you limit the number of concurrent remote connections that are established for each command.</span></span>

<span data-ttu-id="d9dec-195">De standaard instelling is 32 gelijktijdige verbindingen, maar u kunt de para meter **ThrottleLimit** van de cmdlets gebruiken om een aangepaste beperkings limiet voor bepaalde opdrachten in te stellen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-195">The default is 32 concurrent connections, but you can use the **ThrottleLimit** parameter of the cmdlets to set a custom throttle limit for particular commands.</span></span>

<span data-ttu-id="d9dec-196">Wanneer u de beperkings functie gebruikt, moet u er rekening mee houden dat deze wordt toegepast op elke opdracht, niet op de hele sessie of op de computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-196">When you use the throttling feature, remember that it is applied to each command, not to the entire session or to the computer.</span></span> <span data-ttu-id="d9dec-197">Als u opdrachten gelijktijdig uitvoert in verschillende sessies of PSSessions, is het aantal gelijktijdige verbindingen de som van de gelijktijdige verbindingen in alle sessies.</span><span class="sxs-lookup"><span data-stu-id="d9dec-197">If you are running commands concurrently in several sessions or PSSessions, the number of concurrent connections is the sum of the concurrent connections in all the sessions.</span></span>

<span data-ttu-id="d9dec-198">Als u cmdlets wilt zoeken met een **ThrottleLimit** -para meter, typt u:</span><span class="sxs-lookup"><span data-stu-id="d9dec-198">To find cmdlets with a **ThrottleLimit** parameter, type:</span></span>

```
Get-Help * -Parameter ThrottleLimit
-or-
Get-Command -ParameterName ThrottleLimit
```

### <a name="is-the-output-of-remote-commands-different-from-local-output"></a><span data-ttu-id="d9dec-199">Is de uitvoer van externe opdrachten afwijkend van de lokale uitvoer?</span><span class="sxs-lookup"><span data-stu-id="d9dec-199">Is the output of remote commands different from local output?</span></span>

<span data-ttu-id="d9dec-200">Wanneer u Power shell lokaal gebruikt, verzendt en ontvangt u ' live ' .NET Framework objecten; ' live ' objecten zijn objecten die zijn gekoppeld aan de werkelijke Program ma's of systeem onderdelen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-200">When you use PowerShell locally, you send and receive "live" .NET Framework objects; "live" objects are objects that are associated with actual programs or system components.</span></span> <span data-ttu-id="d9dec-201">Wanneer u de methoden aanroept of de eigenschappen van live objecten wijzigt, zijn de wijzigingen van invloed op het werkelijke programma of onderdeel.</span><span class="sxs-lookup"><span data-stu-id="d9dec-201">When you invoke the methods or change the properties of live objects, the changes affect the actual program or component.</span></span> <span data-ttu-id="d9dec-202">En wanneer de eigenschappen van een programma of onderdeel worden gewijzigd, worden de eigenschappen van het object die ze vertegenwoordigen ook gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="d9dec-202">And, when the properties of a program or component change, the properties of the object that represent them also change.</span></span>

<span data-ttu-id="d9dec-203">Omdat de meeste live objecten echter niet via het netwerk kunnen worden verzonden, worden de meeste objecten die worden verzonden in externe opdrachten, dat wil zeggen, geconverteerd naar een reeks XML-gegevens elementen (beperkings taal in XML [CLiXML]) voor verzen ding.</span><span class="sxs-lookup"><span data-stu-id="d9dec-203">However, because most live objects cannot be transmitted over the network, PowerShell "serializes" most of the objects sent in remote commands, that is, it converts each object into a series of XML (Constraint Language in XML [CLiXML]) data elements for transmission.</span></span>

<span data-ttu-id="d9dec-204">Wanneer Power shell een geserialiseerd object ontvangt, wordt de XML geconverteerd naar een gedeserialiseerd object type.</span><span class="sxs-lookup"><span data-stu-id="d9dec-204">When PowerShell receives a serialized object, it converts the XML into a deserialized object type.</span></span> <span data-ttu-id="d9dec-205">Het gedeserialiseerd object is een nauw keurige record van de eigenschappen van het programma of onderdeel op een eerder tijdstip, maar het is niet langer ' live ', dat wil zeggen dat het niet langer rechtstreeks aan het onderdeel is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="d9dec-205">The deserialized object is an accurate record of the properties of the program or component at a previous time, but it is no longer "live", that is, it is no longer directly associated with the component.</span></span> <span data-ttu-id="d9dec-206">De methoden worden verwijderd, omdat ze niet langer effectief zijn.</span><span class="sxs-lookup"><span data-stu-id="d9dec-206">And, the methods are removed because they are no longer effective.</span></span>

<span data-ttu-id="d9dec-207">Normaal gesp roken kunt u ongeserialiseerde objecten gebruiken, net zoals u live objecten zou gebruiken, maar u moet op de hoogte zijn van de beperkingen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-207">Typically, you can use deserialized objects just as you would use live objects, but you must be aware of their limitations.</span></span> <span data-ttu-id="d9dec-208">Daarnaast hebben de objecten die worden geretourneerd door de `Invoke-Command` cmdlet extra eigenschappen die u helpen de oorsprong van de opdracht te bepalen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-208">Also, the objects that are returned by the `Invoke-Command` cmdlet have additional properties that help you to determine the origin of the command.</span></span>

<span data-ttu-id="d9dec-209">Sommige object typen, zoals DirectoryInfo-objecten en GUID'S, worden weer omgezet in live-objecten wanneer ze worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-209">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="d9dec-210">Voor deze objecten is geen speciale verwerking of opmaak vereist.</span><span class="sxs-lookup"><span data-stu-id="d9dec-210">These objects do not need any special handling or formatting.</span></span>

<span data-ttu-id="d9dec-211">Zie [about_Remote_Output](about_Remote_Output.md)voor meer informatie over het interpreteren en Format teren van externe uitvoer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-211">For information about interpreting and formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

### <a name="can-i-run-background-jobs-remotely"></a><span data-ttu-id="d9dec-212">Kan ik achtergrond taken op afstand uitvoeren?</span><span class="sxs-lookup"><span data-stu-id="d9dec-212">Can I run background jobs remotely?</span></span>

<span data-ttu-id="d9dec-213">Ja.</span><span class="sxs-lookup"><span data-stu-id="d9dec-213">Yes.</span></span> <span data-ttu-id="d9dec-214">Een Power shell-achtergrond taak is een Power shell-opdracht die asynchroon wordt uitgevoerd zonder interactie met de sessie.</span><span class="sxs-lookup"><span data-stu-id="d9dec-214">A PowerShell background job is a PowerShell command that runs asynchronously without interacting with the session.</span></span> <span data-ttu-id="d9dec-215">Wanneer u een achtergrond taak start, wordt de opdracht regel onmiddellijk geretourneerd en kunt u in de sessie blijven werken terwijl de taak wordt uitgevoerd, zelfs als deze gedurende een lange periode wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d9dec-215">When you start a background job, the command prompt returns immediately, and you can continue to work in the session while the job runs even if it runs for an extended period of time.</span></span>

<span data-ttu-id="d9dec-216">U kunt ook een achtergrond taak starten terwijl andere opdrachten worden uitgevoerd, omdat de achtergrond taken in een tijdelijke sessie altijd asynchroon worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d9dec-216">You can start a background job even while other commands are running because background jobs always run asynchronously in a temporary session.</span></span>

<span data-ttu-id="d9dec-217">U kunt achtergrond taken uitvoeren op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-217">You can run background jobs on a local or remote computer.</span></span> <span data-ttu-id="d9dec-218">Standaard wordt een achtergrond taak uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-218">By default, a background job runs on the local computer.</span></span> <span data-ttu-id="d9dec-219">U kunt echter de para meter **AsJob** van de `Invoke-Command` cmdlet gebruiken om een externe opdracht als achtergrond taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d9dec-219">However, you can use the **AsJob** parameter of the `Invoke-Command` cmdlet to run any remote command as a background job.</span></span> <span data-ttu-id="d9dec-220">En u kunt gebruiken `Invoke-Command` om een `Start-Job` opdracht op afstand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d9dec-220">And, you can use `Invoke-Command` to run a `Start-Job` command remotely.</span></span>

<span data-ttu-id="d9dec-221">Zie [about_Jobs (about_Jobs. MD)] en [about_Remote_Jobs (about_Remote_Jobs. MD)] voor meer informatie over achtergrond taken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="d9dec-221">For more information about background jobs in PowerShell , see [about_Jobs(about_Jobs.md)] and [about_Remote_Jobs(about_Remote_Jobs.md)].</span></span>

### <a name="can-i-run-windows-programs-on-a-remote-computer"></a><span data-ttu-id="d9dec-222">Kan ik Windows-Program ma's uitvoeren op een externe computer?</span><span class="sxs-lookup"><span data-stu-id="d9dec-222">Can I run windows programs on a remote computer?</span></span>

<span data-ttu-id="d9dec-223">U kunt externe Power shell-opdrachten gebruiken voor het uitvoeren van Windows-Program ma's op externe computers.</span><span class="sxs-lookup"><span data-stu-id="d9dec-223">You can use PowerShell remote commands to run Windows-based programs on remote computers.</span></span> <span data-ttu-id="d9dec-224">U kunt bijvoorbeeld uitvoeren `Shutdown.exe` of `Ipconfig.exe` op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-224">For example, you can run `Shutdown.exe` or `Ipconfig.exe` on a remote computer.</span></span>

<span data-ttu-id="d9dec-225">U kunt echter geen Power shell-opdrachten gebruiken om de gebruikers interface voor elk programma op een externe computer te openen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-225">However, you cannot use PowerShell commands to open the user interface for any program on a remote computer.</span></span>

<span data-ttu-id="d9dec-226">Wanneer u een Windows-programma op een externe computer start, wordt de opdracht niet voltooid en de Power shell-opdracht prompt wordt niet geretourneerd totdat het programma is voltooid of totdat u op <kbd>CTRL</kbd> + <kbd>C</kbd> drukt om de opdracht te onderbreken.</span><span class="sxs-lookup"><span data-stu-id="d9dec-226">When you start a Windows program on a remote computer, the command is not completed, and the PowerShell command prompt does not return, until the program is finished or until you press <kbd>CTRL</kbd>+<kbd>C</kbd> to interrupt the command.</span></span> <span data-ttu-id="d9dec-227">Als u bijvoorbeeld het `Ipconfig.exe` programma op een externe computer uitvoert, wordt de opdracht prompt pas geretourneerd nadat het `Ipconfig.exe` is voltooid.</span><span class="sxs-lookup"><span data-stu-id="d9dec-227">For example, if you run the `Ipconfig.exe` program on a remote computer, the command prompt does not return until `Ipconfig.exe` is completed.</span></span>

<span data-ttu-id="d9dec-228">Als u externe opdrachten gebruikt om een programma met een gebruikers interface te starten, wordt het programma gestart, maar de gebruikers interface wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d9dec-228">If you use remote commands to start a program that has a user interface, the program process starts, but the user interface does not appear.</span></span> <span data-ttu-id="d9dec-229">De Power shell-opdracht is niet voltooid en de opdracht prompt wordt pas weer gegeven nadat u het programma proces hebt gestopt of totdat u op <kbd>CTRL</kbd> + <kbd>C</kbd>drukt, waardoor de opdracht wordt onderbroken en het proces wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="d9dec-229">The PowerShell command is not completed, and the command prompt does not return until you stop the program process or until you press <kbd>CTRL</kbd>+<kbd>C</kbd>, which interrupts the command and stops the process.</span></span>

<span data-ttu-id="d9dec-230">Als u bijvoorbeeld een Power shell-opdracht gebruikt om uit te voeren `Notepad` op een externe computer, wordt het klad blok-proces op de externe computer gestart, maar de gebruikers interface van Klad blok wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d9dec-230">For example, if you use a PowerShell command to run `Notepad` on a remote computer, the Notepad process starts on the remote computer, but the Notepad user interface does not appear.</span></span> <span data-ttu-id="d9dec-231">Als u de opdracht wilt onderbreken en de opdracht prompt wilt herstellen, drukt u op <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d9dec-231">To interrupt the command and restore the command prompt, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

### <a name="can-i-limit-the-commands-that-users-can-run-remotely-on-my-computer"></a><span data-ttu-id="d9dec-232">Kan ik de opdrachten beperken die gebruikers op afstand kunnen uitvoeren op mijn computer?</span><span class="sxs-lookup"><span data-stu-id="d9dec-232">Can I limit the commands that users can run remotely on my computer?</span></span>

<span data-ttu-id="d9dec-233">Ja.</span><span class="sxs-lookup"><span data-stu-id="d9dec-233">Yes.</span></span> <span data-ttu-id="d9dec-234">Elke externe sessie moet een van de sessie configuraties op de externe computer gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d9dec-234">Every remote session must use one of the session configurations on the remote computer.</span></span> <span data-ttu-id="d9dec-235">U kunt de sessie configuraties op uw computer (en de machtigingen voor die sessie configuraties) beheren om te bepalen wie opdrachten op afstand kan uitvoeren op uw computer en welke opdrachten ze kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="d9dec-235">You can manage the session configurations on your computer (and the permissions to those session configurations) to determine who can run commands remotely on your computer and which commands they can run.</span></span>

<span data-ttu-id="d9dec-236">Met een sessie configuratie configureert u de omgeving voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="d9dec-236">A session configuration configures the environment for the session.</span></span> <span data-ttu-id="d9dec-237">U kunt de configuratie definiëren met behulp van een assembly die een nieuwe configuratie klasse implementeert of met behulp van een script dat in de sessie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d9dec-237">You can define the configuration by using an assembly that implements a new configuration class or by using a script that runs in the session.</span></span> <span data-ttu-id="d9dec-238">De configuratie kan bepalen welke opdrachten beschikbaar zijn in de sessie.</span><span class="sxs-lookup"><span data-stu-id="d9dec-238">The configuration can determine the commands that are available in the session.</span></span>
<span data-ttu-id="d9dec-239">En de configuratie kan instellingen bevatten voor het beveiligen van de computer, zoals instellingen die de hoeveelheid gegevens beperken die de sessie op afstand kan ontvangen in één object of opdracht.</span><span class="sxs-lookup"><span data-stu-id="d9dec-239">And, the configuration can include settings that protect the computer, such as settings that limit the amount of data that the session can receive remotely in a single object or command.</span></span> <span data-ttu-id="d9dec-240">U kunt ook een security descriptor opgeven die de benodigde machtigingen voor het gebruik van de configuratie bepaalt.</span><span class="sxs-lookup"><span data-stu-id="d9dec-240">You can also specify a security descriptor that determines the permissions that are required to use the configuration.</span></span>

<span data-ttu-id="d9dec-241">De `Enable-PSRemoting` cmdlet maakt de standaard sessie configuraties op uw computer: micro soft. Power shell, micro soft. Power shell. workflow en micro soft. PowerShell32 (alleen 64-bits besturings systemen).</span><span class="sxs-lookup"><span data-stu-id="d9dec-241">The `Enable-PSRemoting` cmdlet creates the default session configurations on your computer: Microsoft.PowerShell, Microsoft.PowerShell.Workflow, and Microsoft.PowerShell32 (64-bit operating systems only).</span></span> <span data-ttu-id="d9dec-242">`Enable-PSRemoting` Hiermee stelt u de security descriptor in voor de configuratie zodat alleen leden van de groep Administrators op uw computer deze kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d9dec-242">`Enable-PSRemoting` sets the security descriptor for the configuration to allow only members of the Administrators group on your computer to use them.</span></span>

<span data-ttu-id="d9dec-243">U kunt de-cmdlets voor sessie configuratie gebruiken om de standaard sessie configuraties te bewerken, nieuwe sessie configuraties te maken en de security descriptors van alle sessie configuraties te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-243">You can use the session configuration cmdlets to edit the default session configurations, to create new session configurations, and to change the security descriptors of all the session configurations.</span></span>

<span data-ttu-id="d9dec-244">Met ingang van Windows Power Shell 3,0 `New-PSSessionConfigurationFile` kunt u met de cmdlet aangepaste sessie configuraties maken met behulp van een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="d9dec-244">Beginning in Windows PowerShell 3.0, the `New-PSSessionConfigurationFile` cmdlet lets you create custom session configurations by using a text file.</span></span> <span data-ttu-id="d9dec-245">Het bestand bevat opties voor het instellen van de taal modus en voor het opgeven van de cmdlets en modules die beschikbaar zijn in sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="d9dec-245">The file includes options for setting the language mode and for specifying the cmdlets and modules that are available in sessions that use the session configuration.</span></span>

<span data-ttu-id="d9dec-246">Wanneer gebruikers de `Invoke-Command` -, `New-PSSession` -of- `Enter-PSSession` cmdlets gebruiken, kunnen ze de para meter **configuratiepad** gebruiken om de sessie configuratie aan te geven die wordt gebruikt voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="d9dec-246">When users use the `Invoke-Command`, `New-PSSession`, or `Enter-PSSession` cmdlets, they can use the **ConfigurationName** parameter to indicate the session configuration that is used for the session.</span></span> <span data-ttu-id="d9dec-247">En ze kunnen de standaard configuratie wijzigen die hun sessies gebruiken door de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele in de sessie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-247">And, they can change the default configuration that their sessions use by changing the value of the `$PSSessionConfigurationName` preference variable in the session.</span></span>

<span data-ttu-id="d9dec-248">Zie de Help bij de cmdlets voor sessie configuratie voor meer informatie over sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="d9dec-248">For more information about session configurations, see the Help for the session configuration cmdlets.</span></span> <span data-ttu-id="d9dec-249">Als u de cmdlets voor de sessie configuratie wilt vinden, typt u:</span><span class="sxs-lookup"><span data-stu-id="d9dec-249">To find the session configuration cmdlets, type:</span></span>

```powershell
Get-Command *PSSessionConfiguration
```

### <a name="what-are-fan-in-and-fan-out-configurations"></a><span data-ttu-id="d9dec-250">Wat zijn ventilatoren in en uitwaaieren van configuraties?</span><span class="sxs-lookup"><span data-stu-id="d9dec-250">What are fan in and fan out configurations?</span></span>

<span data-ttu-id="d9dec-251">Het meest voorkomende scenario voor externe communicatie van Power shell met meerdere computers is de een-op-veel-configuratie, waarbij een lokale computer (de computer van de beheerder) Power shell-opdrachten op talloze externe computers uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d9dec-251">The most common PowerShell remoting scenario involving multiple computers is the one-to-many configuration, in which one local computer (the administrator's computer) runs PowerShell commands on numerous remote computers.</span></span> <span data-ttu-id="d9dec-252">Dit wordt het scenario ' uitwaaieren ' genoemd.</span><span class="sxs-lookup"><span data-stu-id="d9dec-252">This is known as the "fan-out" scenario.</span></span>

<span data-ttu-id="d9dec-253">In sommige ondernemingen is de configuratie echter veel-op-één, waarbij veel client computers verbinding maken met één externe computer met Power shell, zoals een bestands server of een kiosk.</span><span class="sxs-lookup"><span data-stu-id="d9dec-253">However, in some enterprises, the configuration is many-to-one, where many client computers connect to a single remote computer that is running PowerShell, such as a file server or a kiosk.</span></span> <span data-ttu-id="d9dec-254">Dit wordt ook wel de ' ventilator in ' configuratie genoemd.</span><span class="sxs-lookup"><span data-stu-id="d9dec-254">This is known as the "fan-in" configuration.</span></span>

<span data-ttu-id="d9dec-255">Externe communicatie van Power shell ondersteunt zowel uitwaaier-als ventilator configuraties.</span><span class="sxs-lookup"><span data-stu-id="d9dec-255">PowerShell remoting supports both fan-out and fan-in configurations.</span></span>

<span data-ttu-id="d9dec-256">Voor de uitwaaiers configuratie gebruikt Power shell het protocol Web Services for Management (WS-Management) en de WinRM-service die ondersteuning biedt voor de micro soft-implementatie van WS-Management.</span><span class="sxs-lookup"><span data-stu-id="d9dec-256">For the fan-out configuration, PowerShell uses the Web Services for Management (WS-Management) protocol and the WinRM service that supports the Microsoft implementation of WS-Management.</span></span> <span data-ttu-id="d9dec-257">Wanneer een lokale computer verbinding maakt met een externe computer, WS-Management een verbinding tot stand brengt en een invoeg toepassing voor Power shell gebruikt om het Power shell-hostproces (Wsmprovhost.exe) op de externe computer te starten.</span><span class="sxs-lookup"><span data-stu-id="d9dec-257">When a local computer connects to a remote computer, WS-Management establishes a connection and uses a plug-in for PowerShell to start the PowerShell host process (Wsmprovhost.exe) on the remote computer.</span></span> <span data-ttu-id="d9dec-258">De gebruiker kan een alternatieve poort opgeven, een alternatieve sessie configuratie en andere functies om de externe verbinding aan te passen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-258">The user can specify an alternate port, an alternate session configuration, and other features to customize the remote connection.</span></span>

<span data-ttu-id="d9dec-259">Power shell gebruikt IIS (Internet Information Services) voor het hosten van WS-Management om de Power shell-invoeg toepassing te laden en Power shell te starten om de configuratie van ' ventilator in ' te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="d9dec-259">To support the "fan-in" configuration, PowerShell uses internet Information Services (IIS) to host WS-Management, to load the PowerShell plug-in, and to start PowerShell.</span></span> <span data-ttu-id="d9dec-260">In dit scenario, in plaats van elke Power shell-sessie in een afzonderlijk proces te starten, worden alle Power shell-sessies uitgevoerd in hetzelfde hostproces.</span><span class="sxs-lookup"><span data-stu-id="d9dec-260">In this scenario, instead of starting each PowerShell session in a separate process, all PowerShell sessions run in the same host process.</span></span>

<span data-ttu-id="d9dec-261">IIS-hosting en-ventilator in extern beheer wordt niet ondersteund in Windows XP of in Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="d9dec-261">IIS hosting and fan-in remote management is not supported in Windows XP or in Windows Server 2003.</span></span>

<span data-ttu-id="d9dec-262">In een configuratie van een ventilator kan de gebruiker een verbindings-URI en een HTTP-eind punt opgeven, met inbegrip van het Trans Port, de computer naam, de poort en de toepassings naam.</span><span class="sxs-lookup"><span data-stu-id="d9dec-262">In a fan-in configuration, the user can specify a connection URI and an HTTP endpoint, including the transport, computer name, port, and application name.</span></span>
<span data-ttu-id="d9dec-263">Alle aanvragen met een opgegeven toepassings naam worden door IIS doorgestuurd naar de toepassing.</span><span class="sxs-lookup"><span data-stu-id="d9dec-263">IIS forwards all the requests with a specified application name to the application.</span></span> <span data-ttu-id="d9dec-264">De standaard waarde is WS-Management, die Power shell kan hosten.</span><span class="sxs-lookup"><span data-stu-id="d9dec-264">The default is WS-Management, which can host PowerShell.</span></span>

<span data-ttu-id="d9dec-265">U kunt ook een verificatie mechanisme opgeven en omleiding van HTTP-en HTTPS-eind punten verbieden of toestaan.</span><span class="sxs-lookup"><span data-stu-id="d9dec-265">You can also specify an authentication mechanism and prohibit or allow redirection from HTTP and HTTPS endpoints.</span></span>

### <a name="can-i-test-remoting-on-a-single-computer-not-in-a-domain"></a><span data-ttu-id="d9dec-266">Kan ik externe toegang testen op één computer die zich niet in een domein bevindt?</span><span class="sxs-lookup"><span data-stu-id="d9dec-266">Can I test remoting on a single computer not in a domain?</span></span>

<span data-ttu-id="d9dec-267">Ja.</span><span class="sxs-lookup"><span data-stu-id="d9dec-267">Yes.</span></span> <span data-ttu-id="d9dec-268">Externe communicatie met Power shell is ook beschikbaar wanneer de lokale computer zich niet in een domein bevindt.</span><span class="sxs-lookup"><span data-stu-id="d9dec-268">PowerShell remoting is available even when the local computer is not in a domain.</span></span> <span data-ttu-id="d9dec-269">U kunt de externe functies gebruiken om verbinding te maken met sessies en om sessies op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-269">You can use the remoting features to connect to sessions and to create sessions on the same computer.</span></span> <span data-ttu-id="d9dec-270">De functies werken hetzelfde als wanneer u verbinding maakt met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-270">The features work the same as they do when you connect to a remote computer.</span></span>

<span data-ttu-id="d9dec-271">Als u externe opdrachten op een computer in een werk groep wilt uitvoeren, wijzigt u de volgende Windows-instellingen op de computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-271">To run remote commands on a computer in a workgroup, change the following Windows settings on the computer.</span></span>

<span data-ttu-id="d9dec-272">Let op: deze instellingen zijn van invloed op alle gebruikers op het systeem en ze kunnen het systeem kwetsbaarder maken voor een kwaadwillende aanval.</span><span class="sxs-lookup"><span data-stu-id="d9dec-272">Caution: These settings affect all users on the system and they can make the system more vulnerable to a malicious attack.</span></span> <span data-ttu-id="d9dec-273">Wees voorzichtig wanneer u deze wijzigingen aanbrengt.</span><span class="sxs-lookup"><span data-stu-id="d9dec-273">Use caution when making these changes.</span></span>

- <span data-ttu-id="d9dec-274">Windows Vista, Windows 7, Windows 8:</span><span class="sxs-lookup"><span data-stu-id="d9dec-274">Windows Vista, Windows 7, Windows 8:</span></span>

  <span data-ttu-id="d9dec-275">Maak de volgende register vermelding en stel de waarde in op 1: LocalAccountTokenFilterPolicy in ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`</span><span class="sxs-lookup"><span data-stu-id="d9dec-275">Create the following registry entry, and then set its value to 1: LocalAccountTokenFilterPolicy in ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`</span></span>

  <span data-ttu-id="d9dec-276">U kunt de volgende Power shell-opdracht gebruiken om deze vermelding toe te voegen:</span><span class="sxs-lookup"><span data-stu-id="d9dec-276">You can use the following PowerShell command to add this entry:</span></span>

    ```powershell
    $parameters = @{
      Path='HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System'
      Name='LocalAccountTokenFilterPolicy'
      propertyType='DWord'
      Value=1
    }
    New-ItemProperty @parameters
    ```

- <span data-ttu-id="d9dec-277">Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2:</span><span class="sxs-lookup"><span data-stu-id="d9dec-277">Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2:</span></span>

  <span data-ttu-id="d9dec-278">Er zijn geen wijzigingen nodig omdat de standaard instelling van het beleid ' netwerk toegang: delen en beveiligings model voor lokale accounts ' ' klassiek ' is.</span><span class="sxs-lookup"><span data-stu-id="d9dec-278">No changes are needed because the default setting of the "Network Access: Sharing and security model for local accounts" policy is "Classic".</span></span> <span data-ttu-id="d9dec-279">Controleer de instelling als deze is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="d9dec-279">Verify the setting in case it has changed.</span></span>

### <a name="can-i-run-remote-commands-on-a-computer-in-another-domain"></a><span data-ttu-id="d9dec-280">Kan ik externe opdrachten uitvoeren op een computer in een ander domein?</span><span class="sxs-lookup"><span data-stu-id="d9dec-280">Can I run remote commands on a computer in another domain?</span></span>

<span data-ttu-id="d9dec-281">Ja.</span><span class="sxs-lookup"><span data-stu-id="d9dec-281">Yes.</span></span> <span data-ttu-id="d9dec-282">Normaal gesp roken worden de opdrachten zonder fouten uitgevoerd, maar u moet mogelijk de para meter **Credential** van `Invoke-Command` de `New-PSSession` cmdlets, of gebruiken `Enter-PSSession` om de referenties op te geven van een lid van de groep Administrators op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="d9dec-282">Typically, the commands run without error, although you might need to use the **Credential** parameter of the `Invoke-Command`, `New-PSSession`, or `Enter-PSSession` cmdlets to provide the credentials of a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="d9dec-283">Dit is soms ook vereist, zelfs wanneer de huidige gebruiker lid is van de groep Administrators op de lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="d9dec-283">This is sometimes required even when the current user is a member of the Administrators group on the local and remote computers.</span></span>

<span data-ttu-id="d9dec-284">Als de externe computer echter zich niet in een domein bevindt dat de lokale computer vertrouwt, kan de externe computer de referenties van de gebruiker mogelijk niet verifiëren.</span><span class="sxs-lookup"><span data-stu-id="d9dec-284">However, if the remote computer is not in a domain that the local computer trusts, the remote computer might not be able to authenticate the user's credentials.</span></span>

<span data-ttu-id="d9dec-285">Als u verificatie wilt inschakelen, gebruikt u de volgende opdracht om de externe computer toe te voegen aan de lijst met vertrouwde hosts voor de lokale computer in WinRM.</span><span class="sxs-lookup"><span data-stu-id="d9dec-285">To enable authentication, use the following command to add the remote computer to the list of trusted hosts for the local computer in WinRM.</span></span> <span data-ttu-id="d9dec-286">Typ de opdracht achter de Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="d9dec-286">Type the command at the PowerShell prompt.</span></span>

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value <Remote-computer-name>
```

<span data-ttu-id="d9dec-287">Als u bijvoorbeeld de Server01-computer wilt toevoegen aan de lijst met vertrouwde hosts op de lokale computer, typt u de volgende opdracht achter de Power shell-prompt:</span><span class="sxs-lookup"><span data-stu-id="d9dec-287">For example, to add the Server01 computer to the list of trusted hosts on the local computer, type the following command at the PowerShell prompt:</span></span>

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value Server01
```


## <a name="see-also"></a><span data-ttu-id="d9dec-288">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d9dec-288">See also</span></span>

[<span data-ttu-id="d9dec-289">about_Remote</span><span class="sxs-lookup"><span data-stu-id="d9dec-289">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="d9dec-290">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="d9dec-290">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="d9dec-291">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="d9dec-291">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="d9dec-292">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="d9dec-292">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)

[<span data-ttu-id="d9dec-293">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="d9dec-293">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="d9dec-294">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="d9dec-294">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="d9dec-295">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="d9dec-295">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
