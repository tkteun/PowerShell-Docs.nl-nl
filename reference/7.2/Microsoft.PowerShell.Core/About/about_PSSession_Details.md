---
description: Bevat gedetailleerde informatie over Power shell-sessies en de rol die ze afspelen in externe opdrachten.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssession_details?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSession_Details
ms.openlocfilehash: 79340e5d0ae1fe047f1f37bdfdbb1bebe920d851
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705648"
---
# <a name="about-pssession-details"></a><span data-ttu-id="eb07d-103">Informatie over PSSession</span><span class="sxs-lookup"><span data-stu-id="eb07d-103">About PSSession Details</span></span>

## <a name="short-description"></a><span data-ttu-id="eb07d-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="eb07d-104">Short Description</span></span>
<span data-ttu-id="eb07d-105">Bevat gedetailleerde informatie over Power shell-sessies en de rol die ze afspelen in externe opdrachten.</span><span class="sxs-lookup"><span data-stu-id="eb07d-105">Provides detailed information about PowerShell sessions and the role they play in remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="eb07d-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="eb07d-106">Long Description</span></span>

<span data-ttu-id="eb07d-107">Een sessie is een omgeving waarin Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eb07d-107">A session is an environment in which PowerShell runs.</span></span> <span data-ttu-id="eb07d-108">Telkens wanneer u Power shell start, wordt er een sessie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-108">A session is created for you whenever you start PowerShell.</span></span> <span data-ttu-id="eb07d-109">U kunt op uw computer of op een andere computer extra sessies maken met de naam ' Power shell-sessies ' of ' PSSessions '.</span><span class="sxs-lookup"><span data-stu-id="eb07d-109">You can create additional sessions, called "PowerShell sessions" or "PSSessions" on your computer or another computer.</span></span>

<span data-ttu-id="eb07d-110">In tegens telling tot de sessies die Power shell voor u maakt, kunt u de PSSessions die u hebt gemaakt, regelen en beheren.</span><span class="sxs-lookup"><span data-stu-id="eb07d-110">Unlike the sessions that PowerShell creates for you, you control and manage the PSSessions that you create.</span></span>

<span data-ttu-id="eb07d-111">PSSessions speelt een belang rijke rol bij extern computer gebruik.</span><span class="sxs-lookup"><span data-stu-id="eb07d-111">PSSessions play an important role in remote computing.</span></span> <span data-ttu-id="eb07d-112">Wanneer u een PSSession maakt die is verbonden met een externe computer, brengt Power shell een permanente verbinding met de externe computer tot stand om de PSSession te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="eb07d-112">When you create a PSSession that is connected to a remote computer, PowerShell establishes a persistent connection to the remote computer to support the PSSession.</span></span> <span data-ttu-id="eb07d-113">U kunt de PSSession gebruiken om een reeks opdrachten, functies en scripts uit te voeren die gegevens delen.</span><span class="sxs-lookup"><span data-stu-id="eb07d-113">You can use the PSSession to run a series of commands, functions, and scripts that share data.</span></span>

<span data-ttu-id="eb07d-114">Dit onderwerp bevat gedetailleerde informatie over sessies en PSSessions in Power shell.</span><span class="sxs-lookup"><span data-stu-id="eb07d-114">This topic provides detailed information about sessions and PSSessions in PowerShell.</span></span> <span data-ttu-id="eb07d-115">Zie [about_PSSessions](about_PSSessions.md)voor algemene informatie over de taken die u met sessies kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="eb07d-115">For basic information about the tasks that you can perform with sessions, see [about_PSSessions](about_PSSessions.md).</span></span>

## <a name="about-sessions"></a><span data-ttu-id="eb07d-116">Over sessies</span><span class="sxs-lookup"><span data-stu-id="eb07d-116">About Sessions</span></span>

<span data-ttu-id="eb07d-117">Technisch gezien is een sessie een uitvoerings omgeving waarin Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eb07d-117">Technically, a session is an execution environment in which PowerShell runs.</span></span> <span data-ttu-id="eb07d-118">Elke sessie bevat een exemplaar van System. Management. Automation engine en een hostprogramma waarin Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eb07d-118">Each session includes an instance of the System.Management.Automation engine and a host program in which PowerShell runs.</span></span> <span data-ttu-id="eb07d-119">De host kan de vertrouwde Power shell-console zijn of een ander programma dat opdrachten uitvoert, zoals Cmd.exe, of een programma dat is gebouwd voor het hosten van Power shell, zoals Windows Power shell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="eb07d-119">The host can be the familiar PowerShell console or another program that runs commands, such as Cmd.exe, or a program built to host PowerShell, such as Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="eb07d-120">Vanuit een Windows-perspectief is een sessie een Windows-proces op de doel computer.</span><span class="sxs-lookup"><span data-stu-id="eb07d-120">From a Windows perspective, a session is a Windows process on the target computer.</span></span>

<span data-ttu-id="eb07d-121">Elke sessie is onafhankelijk geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="eb07d-121">Each session is configured independently.</span></span> <span data-ttu-id="eb07d-122">Het bevat eigen eigenschappen, een eigen uitvoerings beleid en de eigen profielen.</span><span class="sxs-lookup"><span data-stu-id="eb07d-122">It includes its own properties, its own execution policy, and its own profiles.</span></span> <span data-ttu-id="eb07d-123">De omgeving die zich voordoet wanneer de sessie wordt gemaakt, blijft in de levens duur, zelfs als u de omgeving op de computer wijzigt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-123">The environment that exists when the session is created persists for its lifetime even if you change the environment on the computer.</span></span> <span data-ttu-id="eb07d-124">Alle sessies worden gemaakt in een globaal bereik, zelfs in sessies die u in een script maakt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-124">All sessions are created in a global scope, even sessions that you create in a script.</span></span>

<span data-ttu-id="eb07d-125">U kunt in een sessie in één keer slechts één opdracht (of opdracht pijplijn) uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="eb07d-125">You can run only one command (or command pipeline) in a session at one time.</span></span> <span data-ttu-id="eb07d-126">Een tweede opdracht die synchroon wordt uitgevoerd (één op een keer), wacht tot vier minuten totdat de eerste opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="eb07d-126">A second command run synchronously (one at a time) waits up to four minutes for the first command to be completed.</span></span> <span data-ttu-id="eb07d-127">Een tweede opdracht die asynchroon (gelijktijdig) wordt uitgevoerd, mislukt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-127">A second command run asynchronously (concurrently) fails.</span></span>

## <a name="about-pssessions"></a><span data-ttu-id="eb07d-128">Over PSSessions</span><span class="sxs-lookup"><span data-stu-id="eb07d-128">About PSSessions</span></span>

<span data-ttu-id="eb07d-129">Telkens wanneer u Power shell start, wordt er een sessie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-129">A session is created each time that you start PowerShell.</span></span> <span data-ttu-id="eb07d-130">En Power Shell maakt tijdelijke sessies voor het uitvoeren van afzonderlijke opdrachten.</span><span class="sxs-lookup"><span data-stu-id="eb07d-130">And, PowerShell creates temporary sessions to run individual commands.</span></span>
<span data-ttu-id="eb07d-131">U kunt echter ook sessies maken (' Power shell-sessies ' of ' PSSessions ' genoemd) die u beheert en beheert.</span><span class="sxs-lookup"><span data-stu-id="eb07d-131">However, you can also create sessions (called "PowerShell sessions" or "PSSessions") that you control and manage.</span></span>

<span data-ttu-id="eb07d-132">PSSessions zijn essentieel voor externe opdrachten.</span><span class="sxs-lookup"><span data-stu-id="eb07d-132">PSSessions are critical to remote commands.</span></span> <span data-ttu-id="eb07d-133">Als u de para meter **ComputerName** van de `Invoke-Command` `Enter-PSSession` cmdlets gebruikt, maakt Power shell een tijdelijke sessie om de opdracht uit te voeren en wordt de sessie gesloten zodra de opdracht of de interactieve sessie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="eb07d-133">If you use the **ComputerName** parameter of the `Invoke-Command` or `Enter-PSSession` cmdlets, PowerShell establishes a temporary session to run the command and then closes the session as soon as the command or the interactive session is complete.</span></span>

<span data-ttu-id="eb07d-134">Als u echter de `New-PSSession` -cmdlet gebruikt om een PSSession te maken, brengt Power shell een permanente sessie tot stand op de externe computer waarin u meerdere opdrachten of interactieve sessies kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="eb07d-134">However, if you use the `New-PSSession` cmdlet to create a PSSession, PowerShell establishes a persistent session on the remote computer in which you can run multiple commands or interactive sessions.</span></span> <span data-ttu-id="eb07d-135">De PSSessions die u maakt, blijven open en beschikbaar voor gebruik totdat u ze verwijdert of totdat u de sessie sluit waarin deze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-135">The PSSessions that you create remain open and available for use until you delete them or until you close the session in which they were created.</span></span>

<span data-ttu-id="eb07d-136">Wanneer u een PSSession op een externe computer maakt, maakt het systeem een Power Shell-proces op de externe computer en wordt er een verbinding tot stand gebracht tussen de lokale computer en het proces op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="eb07d-136">When you create a PSSession on a remote computer, the system creates a PowerShell process on the remote computer and establishes a connection from the local computer to the process on the remote computer.</span></span> <span data-ttu-id="eb07d-137">Wanneer u een PSSession maakt op de lokale computer, worden zowel het nieuwe proces als de verbindingen gemaakt op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="eb07d-137">When you create a PSSession on the local computer, both the new process and the connections are created on the local computer.</span></span>

## <a name="when-do-i-need-a-pssession"></a><span data-ttu-id="eb07d-138">Wanneer heb ik een PSSession nodig?</span><span class="sxs-lookup"><span data-stu-id="eb07d-138">When Do I Need a PSSession?</span></span>

<span data-ttu-id="eb07d-139">De `Invoke-Command` `Enter-PSSession` cmdlets en hebben zowel **ComputerName** als **Session** -para meters.</span><span class="sxs-lookup"><span data-stu-id="eb07d-139">The `Invoke-Command` and `Enter-PSSession` cmdlets have both **ComputerName** and **Session** parameters.</span></span> <span data-ttu-id="eb07d-140">U kunt ofwel gebruiken om een externe opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="eb07d-140">You can use either to run a remote command.</span></span>

<span data-ttu-id="eb07d-141">Gebruik de para meter **ComputerName** om één opdracht uit te voeren of een reeks niet-gerelateerde opdrachten op een of meer computers.</span><span class="sxs-lookup"><span data-stu-id="eb07d-141">Use the **ComputerName** parameter to run a single command or a series of unrelated commands on one or many computers.</span></span>

<span data-ttu-id="eb07d-142">U hebt een permanente verbinding met de externe computer nodig om opdrachten uit te voeren die gegevens delen.</span><span class="sxs-lookup"><span data-stu-id="eb07d-142">To run commands that share data, you need a persistent connection to the remote computer.</span></span> <span data-ttu-id="eb07d-143">In dat geval maakt u een PSSession en gebruikt u vervolgens de **sessie** parameter om opdrachten uit te voeren in de PSSession.</span><span class="sxs-lookup"><span data-stu-id="eb07d-143">In that case, create a PSSession, and then use the **Session** parameter to run commands in the PSSession.</span></span>

<span data-ttu-id="eb07d-144">Veel andere cmdlets die gegevens ophalen van externe computers, zoals `Get-Process` ,, `Get-Service` `Get-EventLog` en `Get-WmiObject` alleen een **ComputerName** -para meter hebben.</span><span class="sxs-lookup"><span data-stu-id="eb07d-144">Many other cmdlets that get data from remote computers, such as `Get-Process`, `Get-Service`, `Get-EventLog`, and `Get-WmiObject` have only a **ComputerName** parameter.</span></span> <span data-ttu-id="eb07d-145">Ze gebruiken andere technologieën dan externe communicatie van Power shell om gegevens op afstand te verzamelen.</span><span class="sxs-lookup"><span data-stu-id="eb07d-145">They use technologies other than PowerShell remoting to gather data remotely.</span></span> <span data-ttu-id="eb07d-146">Deze cmdlets hebben geen **sessie** parameter, maar u kunt de `Invoke-Command` cmdlet gebruiken om deze opdrachten uit te voeren in een PSSession.</span><span class="sxs-lookup"><span data-stu-id="eb07d-146">These cmdlets do not have a **Session** parameter, but you can use the `Invoke-Command` cmdlet to run these commands in a PSSession.</span></span>

## <a name="how-do-i-create-a-pssession"></a><span data-ttu-id="eb07d-147">Hoe maak ik een PSSession?</span><span class="sxs-lookup"><span data-stu-id="eb07d-147">How Do I Create a PSSession?</span></span>

<span data-ttu-id="eb07d-148">Gebruik de cmdlet om een PSSession te maken `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="eb07d-148">To create a PSSession, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="eb07d-149">U kunt gebruiken `New-PSSession` om een PSSession te maken op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="eb07d-149">You can use `New-PSSession` to create a PSSession on a local or remote computer.</span></span>

## <a name="can-i-create-a-pssession-on-any-computer"></a><span data-ttu-id="eb07d-150">Kan ik een PSSession op elke computer maken?</span><span class="sxs-lookup"><span data-stu-id="eb07d-150">Can I Create a PSSession on Any Computer?</span></span>

<span data-ttu-id="eb07d-151">Als u een PSSession wilt maken die is verbonden met een externe computer, moet de computer zijn geconfigureerd voor externe toegang in Power shell.</span><span class="sxs-lookup"><span data-stu-id="eb07d-151">To create a PSSession that is connected to a remote computer, the computer must be configured for remoting in PowerShell.</span></span> <span data-ttu-id="eb07d-152">De huidige gebruiker moet lid zijn van de groep Administrators op de externe computer, of de huidige gebruiker moet de referenties kunnen opgeven van een lid van de groep Administrators.</span><span class="sxs-lookup"><span data-stu-id="eb07d-152">The current user must be a member of the Administrators group on the remote computer, or the current user must be able to supply the credentials of a member of the Administrators group.</span></span> <span data-ttu-id="eb07d-153">Zie [about_Remote_Requirements](about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eb07d-153">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

## <a name="can-i-see-my-pssessions-in-other-sessions"></a><span data-ttu-id="eb07d-154">Kan ik mijn PSSessions in andere sessies zien?</span><span class="sxs-lookup"><span data-stu-id="eb07d-154">Can I See My PSSessions in Other Sessions?</span></span>

<span data-ttu-id="eb07d-155">Vanaf Windows Power Shell 3,0 krijgt de para meter **ComputerName** van de `Get-PSSession` cmdlet PSSessions die u hebt gemaakt op de opgegeven externe computers.</span><span class="sxs-lookup"><span data-stu-id="eb07d-155">Beginning in Windows PowerShell 3.0, the **ComputerName** parameter of the `Get-PSSession` cmdlet gets PSSessions that you created on the specified remote computers.</span></span>

<span data-ttu-id="eb07d-156">Actieve PSSessions worden onderhouden op de externe computer (de ' server-side ' van een verbinding) en u kunt deze vanuit elke sessie op elke computer ophalen.</span><span class="sxs-lookup"><span data-stu-id="eb07d-156">Active PSSessions are maintained on the remote computer (the "server-side" of a connection) and you can get them from any session on any computer.</span></span>

<span data-ttu-id="eb07d-157">Als u bijvoorbeeld een PSSession maakt van de Server01-computer naar de Server02-computer en vervolgens overschakelt naar de Server03-computer, kunt u een opdracht als de volgende gebruiken om de sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="eb07d-157">For example, if you create a PSSession from the Server01 computer to the Server02 computer, and then switch to the Server03 computer, you can use a command like the following one to get the session.</span></span>

```powershell
Get-PSSession -ComputerName Server02
```

<span data-ttu-id="eb07d-158">Zelfs als u de verbinding met de sessie verbreekt, wordt de sessie op de externe computer gehandhaafd totdat u deze verwijdert of er een time-out optreedt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-158">Even if you disconnect from the session, the session is maintained on the remote computer until you delete it or it times out.</span></span>

<span data-ttu-id="eb07d-159">In Windows Power Shell 2,0 kunt u alleen de PSSessions ophalen die u in de huidige sessie hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-159">In Windows PowerShell 2.0, you can get only the PSSessions that you have created in the current session.</span></span> <span data-ttu-id="eb07d-160">U kunt geen PSSessions ophalen die u in andere sessies hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-160">You cannot get PSSessions that you created in other sessions.</span></span>

<span data-ttu-id="eb07d-161">Zie [Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eb07d-161">For more information, see [Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession).</span></span>

## <a name="can-i-see-the-pssessions-that-others-have-created-on-my-computer"></a><span data-ttu-id="eb07d-162">Kan ik de PSSessions zien die anderen op mijn computer hebben gemaakt?</span><span class="sxs-lookup"><span data-stu-id="eb07d-162">Can I See the PSSessions That Others Have Created on My Computer?</span></span>

<span data-ttu-id="eb07d-163">U kunt alleen de PSSessions ophalen en beheren die anderen alleen hebben gemaakt als u de referenties kunt opgeven van de gebruiker die de PSSession heeft gemaakt of de sessie configuratie die de PSSession gebruikt, inclusief runas-referenties.</span><span class="sxs-lookup"><span data-stu-id="eb07d-163">You can get and manage only the PSSessions that others have created only if you can supply the credentials of the user who created the PSSession or the session configuration that the PSSession uses includes RunAs credentials.</span></span> <span data-ttu-id="eb07d-164">Als dat niet het geval is, kunt u alleen de PSSessions die u hebt gemaakt, ophalen, verbinding maken met en beheren.</span><span class="sxs-lookup"><span data-stu-id="eb07d-164">Otherwise, you can get, connect to, use, and manage only the PSSessions that you created.</span></span>

## <a name="can-i-connect-to-a-pssession-from-a-different-computer"></a><span data-ttu-id="eb07d-165">Kan ik verbinding maken met een PSSession vanaf een andere computer?</span><span class="sxs-lookup"><span data-stu-id="eb07d-165">Can I Connect to a PSSession From a Different Computer?</span></span>

<span data-ttu-id="eb07d-166">Vanaf Windows Power Shell 3,0 zijn PSSessions onafhankelijk van de sessies waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-166">Beginning in Windows PowerShell 3.0, PSSessions are independent of the sessions in which they were created.</span></span> <span data-ttu-id="eb07d-167">Actieve PSSessions worden onderhouden op de computer op het externe of aan de server zijde van een verbinding.</span><span class="sxs-lookup"><span data-stu-id="eb07d-167">Active PSSessions are maintained on the computer at the remote or "server-side" of a connection.</span></span>

<span data-ttu-id="eb07d-168">U kunt de `Disconnect-PSSession` cmdlet gebruiken om de verbinding met een PSSession te verbreken.</span><span class="sxs-lookup"><span data-stu-id="eb07d-168">You can use the `Disconnect-PSSession` cmdlet to disconnect from a PSSession.</span></span> <span data-ttu-id="eb07d-169">De PSSession is losgekoppeld van de lokale sessie, maar blijft actief op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="eb07d-169">The PSSession is disconnected from the local session, but is maintained on the remote computer.</span></span>
<span data-ttu-id="eb07d-170">Opdrachten blijven actief in de niet-verbonden PSSession.</span><span class="sxs-lookup"><span data-stu-id="eb07d-170">Commands continue to run in the disconnected PSSession.</span></span> <span data-ttu-id="eb07d-171">U kunt Power shell sluiten en de oorspronkelijke computer afsluiten zonder de PSSession te onderbreken.</span><span class="sxs-lookup"><span data-stu-id="eb07d-171">You can close PowerShell and shut down the originating computer without interrupting the PSSession.</span></span>

<span data-ttu-id="eb07d-172">Vervolgens kunt u, zelfs later, de cmdlet gebruiken `Get-PSSession` om de PSSession en de `Connect-PSSession` cmdlet te verkrijgen om verbinding te maken met de PSSession vanuit een nieuwe sessie op een andere computer.</span><span class="sxs-lookup"><span data-stu-id="eb07d-172">Then, even hours later, you can use the `Get-PSSession` cmdlet to get the PSSession and the `Connect-PSSession` cmdlet to connect to the PSSession from a new session on a different computer.</span></span>

<span data-ttu-id="eb07d-173">Zie [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eb07d-173">For more information, see [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md).</span></span>

## <a name="what-happens-to-my-pssession-if-my-computer-stops"></a><span data-ttu-id="eb07d-174">Wat gebeurt er met mijn PSSession als mijn computer stopt?</span><span class="sxs-lookup"><span data-stu-id="eb07d-174">What Happens to My PSSession if My Computer Stops?</span></span>

<span data-ttu-id="eb07d-175">Niet-verbonden PSSessions zijn onafhankelijk van de sessies waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-175">Disconnected PSSessions are independent of the sessions in which they were created.</span></span> <span data-ttu-id="eb07d-176">Als u een PSSession verbreekt en vervolgens de oorspronkelijke computer sluit, wordt de PSSession op de externe computer onderhouden.</span><span class="sxs-lookup"><span data-stu-id="eb07d-176">If you disconnect a PSSession and then close the originating computer, the PSSession is maintained on the remote computer.</span></span>

<span data-ttu-id="eb07d-177">Daarnaast probeert Power shell actieve PSSessions te herstellen die onbedoeld zijn losgekoppeld, zoals het opnieuw opstarten van een computer, een tijdelijke stroom storing of een onderbreking van het netwerk.</span><span class="sxs-lookup"><span data-stu-id="eb07d-177">In addition, PowerShell attempts to recover active PSSessions that are disconnected unintentionally, such as by a computer reboot, a temporary power outage or network disruption.</span></span> <span data-ttu-id="eb07d-178">Power shell probeert de PSSession bij te houden of te herstellen, als de oorspronkelijke sessie nog steeds beschikbaar is, of de status niet verbonden als dat niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="eb07d-178">PowerShell attempts to maintain or recover the PSSession to an Opened state, if the originating session is still available, or to a disconnected state if it is not.</span></span>

<span data-ttu-id="eb07d-179">Een ' actieve ' PSSession is een met-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="eb07d-179">An "active" PSSession is one that is running commands.</span></span> <span data-ttu-id="eb07d-180">Als een PSSession is verbonden (niet verbroken) en de opdrachten worden uitgevoerd in de PSSession wanneer de verbonden sessie wordt gesloten, probeert Power shell de PSSession op de externe computer te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="eb07d-180">If a PSSession is connected (not disconnected) and commands are running in the PSSession when the connected session closes, PowerShell attempts to maintain the PSSession on the remote computer.</span></span> <span data-ttu-id="eb07d-181">Als er echter geen opdrachten worden uitgevoerd in de PSSession, wordt de PSSession door Power shell gesloten wanneer de verbonden sessie wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="eb07d-181">However, if no commands are running in the PSSession, PowerShell closes the PSSession when the connected session closes.</span></span>

<span data-ttu-id="eb07d-182">Zie [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eb07d-182">For more information, see [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md).</span></span>

## <a name="can-i-run-a-background-job-in-a-pssession"></a><span data-ttu-id="eb07d-183">Kan ik een achtergrond taak uitvoeren in een PSSession?</span><span class="sxs-lookup"><span data-stu-id="eb07d-183">Can I Run a Background Job in a PSSession?</span></span>

<span data-ttu-id="eb07d-184">Ja.</span><span class="sxs-lookup"><span data-stu-id="eb07d-184">Yes.</span></span> <span data-ttu-id="eb07d-185">Een achtergrond taak is een opdracht die asynchroon op de achtergrond wordt uitgevoerd zonder interactie met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eb07d-185">A background job is a command that runs asynchronously in the background without interacting with the current session.</span></span> <span data-ttu-id="eb07d-186">Wanneer u een opdracht verzendt om een taak te starten, retourneert de opdracht een taak object, maar de taak wordt uitgevoerd op de achtergrond totdat deze is voltooid.</span><span class="sxs-lookup"><span data-stu-id="eb07d-186">When you submit a command to start a job, the command returns a job object, but the job continues to run in the background until it is complete.</span></span>

<span data-ttu-id="eb07d-187">Als u een achtergrond taak wilt starten op een lokale computer, gebruikt u de `Start-Job` opdracht.</span><span class="sxs-lookup"><span data-stu-id="eb07d-187">To start a background job on a local computer, use the `Start-Job` command.</span></span>
<span data-ttu-id="eb07d-188">U kunt de achtergrond taak uitvoeren in een tijdelijke verbinding (door de para meter **ComputerName** te gebruiken) of in een PSSession (met behulp van de para meter **Session** ).</span><span class="sxs-lookup"><span data-stu-id="eb07d-188">You can run the background job in a temporary connection (by using the **ComputerName** parameter) or in a PSSession (by using the **Session** parameter).</span></span>

<span data-ttu-id="eb07d-189">Als u een achtergrond taak wilt starten op een externe computer, gebruikt u de `Invoke-Command` cmdlet met de para meter **AsJob** of gebruikt `Invoke-Command` u de cmdlet om een opdracht uit te voeren `Start-Job` op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="eb07d-189">To start a background job on a remote computer, use the `Invoke-Command` cmdlet with its **AsJob** parameter, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span> <span data-ttu-id="eb07d-190">Wanneer u de para meter **AsJob** gebruikt, kunt u de **computer naam** of de **sessie** parameters gebruiken.</span><span class="sxs-lookup"><span data-stu-id="eb07d-190">When using the **AsJob** parameter, you can use the **ComputerName** or **Session** parameters.</span></span>

<span data-ttu-id="eb07d-191">Wanneer `Invoke-Command` u gebruikt om een opdracht uit te voeren `Start-Job` , moet u de opdracht uitvoeren in een PSSession.</span><span class="sxs-lookup"><span data-stu-id="eb07d-191">When using `Invoke-Command` to run a `Start-Job` command, you must run the command in a PSSession.</span></span> <span data-ttu-id="eb07d-192">Als u de para meter **ComputerName** gebruikt, wordt de verbinding door Power Shell beëindigd wanneer het taak object retourneert, en wordt de taak onderbroken.</span><span class="sxs-lookup"><span data-stu-id="eb07d-192">If you use the **ComputerName** parameter, PowerShell ends the connection when the job object returns, and the job is interrupted.</span></span>

<span data-ttu-id="eb07d-193">Zie [About Jobs](about_Jobs.md) (Taken) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eb07d-193">For more information, see [about_Jobs](about_Jobs.md).</span></span>

## <a name="can-i-run-an-interactive-session"></a><span data-ttu-id="eb07d-194">Kan ik een interactieve sessie uitvoeren?</span><span class="sxs-lookup"><span data-stu-id="eb07d-194">Can I Run an Interactive Session?</span></span>

<span data-ttu-id="eb07d-195">Ja.</span><span class="sxs-lookup"><span data-stu-id="eb07d-195">Yes.</span></span> <span data-ttu-id="eb07d-196">Als u een interactieve sessie met een externe computer wilt starten, gebruikt u de `Enter-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb07d-196">To start an interactive session with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="eb07d-197">In een interactieve sessie worden de opdrachten die u typt op de externe computer uitgevoerd, net alsof u ze rechtstreeks op de externe computer hebt getypt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-197">In an interactive session, the commands that you type run on the remote computer, just as if you typed them directly on the remote computer.</span></span>

<span data-ttu-id="eb07d-198">U kunt een interactieve sessie uitvoeren in een tijdelijke sessie (met behulp van de para meter **ComputerName** ) of in een PSSession (met behulp van de para meter **Session** ).</span><span class="sxs-lookup"><span data-stu-id="eb07d-198">You can run an interactive session in a temporary session (by using the **ComputerName** parameter) or in a PSSession (by using the **Session** parameter).</span></span>
<span data-ttu-id="eb07d-199">Als u een PSSession gebruikt, worden de gegevens van de vorige opdrachten door de PSSession bewaard en worden alle gegevens die zijn gegenereerd tijdens de interactieve sessie, bewaard voor gebruik in latere opdrachten.</span><span class="sxs-lookup"><span data-stu-id="eb07d-199">If you use a PSSession, the PSSession retains the data from previous commands, and the PSSession retains any data generated during the interactive session for use in later commands.</span></span>

<span data-ttu-id="eb07d-200">Wanneer u de interactieve sessie beëindigt, blijft de PSSession open en beschikbaar voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="eb07d-200">When you end the interactive session, the PSSession remains open and available for use.</span></span>

<span data-ttu-id="eb07d-201">Zie [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) en [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eb07d-201">For more information, see [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) and [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession).</span></span>

## <a name="must-i-delete-the-pssessions"></a><span data-ttu-id="eb07d-202">Moet ik de PSSessions verwijderen?</span><span class="sxs-lookup"><span data-stu-id="eb07d-202">Must I Delete the PSSessions?</span></span>

<span data-ttu-id="eb07d-203">Ja.</span><span class="sxs-lookup"><span data-stu-id="eb07d-203">Yes.</span></span> <span data-ttu-id="eb07d-204">Een PSSession is een proces. Dit is een op zichzelf staande omgeving waarin geheugen en andere bronnen worden gebruikt, zelfs wanneer u deze niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-204">A PSSession is a process, which is a self-contained environment that uses memory and other resources even when you are not using it.</span></span> <span data-ttu-id="eb07d-205">Wanneer u klaar bent met een PSSession, verwijdert u deze.</span><span class="sxs-lookup"><span data-stu-id="eb07d-205">When you are finished with a PSSession, delete it.</span></span> <span data-ttu-id="eb07d-206">Als u meerdere PSSessions maakt, sluit u de bestanden die u niet gebruikt en behoudt u alleen de items die momenteel in gebruik zijn.</span><span class="sxs-lookup"><span data-stu-id="eb07d-206">If you create multiple PSSessions, close the ones that you are not using, and maintain only the ones currently in use.</span></span>

<span data-ttu-id="eb07d-207">Als u PSSessions wilt verwijderen, gebruikt u de `Remove-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb07d-207">To delete PSSessions, use the `Remove-PSSession` cmdlet.</span></span> <span data-ttu-id="eb07d-208">De PSSessions wordt verwijderd en alle resources die ze gebruiken, worden vrijgegeven.</span><span class="sxs-lookup"><span data-stu-id="eb07d-208">It deletes the PSSessions and releases all of the resources that they were using.</span></span>

<span data-ttu-id="eb07d-209">U kunt ook de para meter **IdleTimeOut** van gebruiken `New-PSSessionOption` om een inactieve PSSession te sluiten na een interval dat u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="eb07d-209">You can also use the **IdleTimeOut** parameter of `New-PSSessionOption` to close an idle PSSession after an interval that you specify.</span></span> <span data-ttu-id="eb07d-210">Zie [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eb07d-210">For more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="eb07d-211">Als u een PSSession-object opslaat in een variabele en vervolgens de PSSession verwijdert of een time-out krijgt, bevat de variabele nog steeds het object PSSession, maar de PSSession is niet actief en kan niet worden gebruikt of gerepareerd.</span><span class="sxs-lookup"><span data-stu-id="eb07d-211">If you save a PSSession object in a variable and then delete the PSSession or let it time out, the variable still contains the PSSession object, but the PSSession is not active and cannot be used or repaired.</span></span>

## <a name="are-all-sessions-and-pssessions-alike"></a><span data-ttu-id="eb07d-212">Zijn alle sessies en PSSessions hetzelfde?</span><span class="sxs-lookup"><span data-stu-id="eb07d-212">Are All Sessions and PSSessions Alike?</span></span>

<span data-ttu-id="eb07d-213">Nee.</span><span class="sxs-lookup"><span data-stu-id="eb07d-213">No.</span></span> <span data-ttu-id="eb07d-214">Ontwikkel aars kunnen aangepaste sessies maken die alleen geselecteerde providers en cmdlets bevatten.</span><span class="sxs-lookup"><span data-stu-id="eb07d-214">Developers can create custom sessions that include only selected providers and cmdlets.</span></span> <span data-ttu-id="eb07d-215">Als een opdracht in één sessie werkt, maar niet in een andere, wordt de sessie mogelijk beperkt.</span><span class="sxs-lookup"><span data-stu-id="eb07d-215">If a command works in one session but not in another, it might be because the session is restricted.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb07d-216">Zie ook</span><span class="sxs-lookup"><span data-stu-id="eb07d-216">See Also</span></span>

[<span data-ttu-id="eb07d-217">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="eb07d-217">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="eb07d-218">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="eb07d-218">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="eb07d-219">about_Remote</span><span class="sxs-lookup"><span data-stu-id="eb07d-219">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="eb07d-220">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="eb07d-220">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="eb07d-221">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="eb07d-221">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="eb07d-222">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="eb07d-222">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="eb07d-223">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="eb07d-223">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="eb07d-224">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="eb07d-224">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[<span data-ttu-id="eb07d-225">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="eb07d-225">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="eb07d-226">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="eb07d-226">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="eb07d-227">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="eb07d-227">Remove-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSession)
