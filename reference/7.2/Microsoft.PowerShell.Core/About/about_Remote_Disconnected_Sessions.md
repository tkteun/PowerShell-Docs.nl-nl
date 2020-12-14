---
description: Hierin wordt uitgelegd hoe u de verbinding verbreekt en opnieuw maakt met een Power shell-sessie (PSSession).
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: 0756e110b1058915f6280e2ea59ee915bedb2c75
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705313"
---
# <a name="about-remote-disconnected-sessions"></a><span data-ttu-id="792c2-103">Over externe verbroken sessies</span><span class="sxs-lookup"><span data-stu-id="792c2-103">About Remote Disconnected Sessions</span></span>

## <a name="short-description"></a><span data-ttu-id="792c2-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="792c2-104">Short description</span></span>

<span data-ttu-id="792c2-105">Hierin wordt uitgelegd hoe u de verbinding verbreekt en opnieuw maakt met een Power shell-sessie (PSSession).</span><span class="sxs-lookup"><span data-stu-id="792c2-105">Explains how to disconnect and reconnect to a PowerShell Session (PSSession).</span></span>

## <a name="long-description"></a><span data-ttu-id="792c2-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="792c2-106">Long description</span></span>

<span data-ttu-id="792c2-107">Vanaf Power Shell 3,0 kunt u de verbinding met een PSSession verbreken en opnieuw verbinding maken met de PSSession op dezelfde computer of een andere computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-107">Beginning in PowerShell 3.0, you can disconnect from a PSSession and reconnect to the PSSession on the same computer or a different computer.</span></span> <span data-ttu-id="792c2-108">De sessie status wordt gehandhaafd en opdrachten in de PSSession blijven actief wanneer de sessie wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-108">The session state is maintained and commands in the PSSession continue to run while the session is disconnected.</span></span>

<span data-ttu-id="792c2-109">De functie voor verbroken sessies is alleen beschikbaar als op de externe computer Power Shell 3,0 of een latere versie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="792c2-109">The Disconnected Sessions feature is only available when the remote computer is running PowerShell 3.0 or a later version.</span></span>

<span data-ttu-id="792c2-110">Met de functie voor verbroken sessies kunt u de sessie sluiten waarin een PSSession is gemaakt, en zelfs Power shell sluiten en de computer afsluiten, zonder dat de opdrachten die in de PSSession worden uitgevoerd, worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-110">The Disconnected Sessions feature allows you to close the session in which a PSSession was created, and even close PowerShell, and shut down the computer, without disrupting commands running in the PSSession.</span></span> <span data-ttu-id="792c2-111">Verbroken sessies zijn handig voor het uitvoeren van opdrachten die lange tijd in beslag nemen en biedt de tijd en de flexibiliteit van apparaten die IT-professionals nodig hebben.</span><span class="sxs-lookup"><span data-stu-id="792c2-111">Disconnected sessions are useful for running commands that take an extended time to complete, and provides the time and device flexibility that IT professionals require.</span></span>

<span data-ttu-id="792c2-112">U kunt de verbinding met een interactieve sessie die is gestart met behulp van de cmdlet, niet verbreken `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="792c2-112">You can't disconnect from an interactive session that is started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="792c2-113">U kunt niet-verbonden sessies gebruiken om PSSessions te beheren die onbedoeld zijn losgekoppeld als gevolg van een computer of netwerk storing.</span><span class="sxs-lookup"><span data-stu-id="792c2-113">You can use disconnected sessions to manage PSSessions that were disconnected unintentionally as the result of a computer or network outage.</span></span>

<span data-ttu-id="792c2-114">In Real-World-gebruik kunt u met de functie voor verbroken sessies beginnen met het oplossen van een probleem, een probleem met een hogere prioriteit maken en vervolgens het werk aan de oplossing hervatten, zelfs op een andere computer op een andere locatie.</span><span class="sxs-lookup"><span data-stu-id="792c2-114">In real-world use, the Disconnected Sessions feature allows you to begin solving a problem, turn your attention to a higher priority issue, and then resume work on the solution, even on a different computer in a different location.</span></span>

## <a name="disconnected-session-cmdlets"></a><span data-ttu-id="792c2-115">Verbroken sessie-cmdlets</span><span class="sxs-lookup"><span data-stu-id="792c2-115">Disconnected session cmdlets</span></span>

<span data-ttu-id="792c2-116">De volgende cmdlets bieden ondersteuning voor de functie voor verbroken sessies:</span><span class="sxs-lookup"><span data-stu-id="792c2-116">The following cmdlets support the Disconnected Sessions feature:</span></span>

- <span data-ttu-id="792c2-117">`Connect-PSSession`: Maakt verbinding met een niet-verbonden PSSession.</span><span class="sxs-lookup"><span data-stu-id="792c2-117">`Connect-PSSession`: Connects to a disconnected PSSession.</span></span>
- <span data-ttu-id="792c2-118">`Disconnect-PSSession`: Verbreekt de verbinding met een PSSession.</span><span class="sxs-lookup"><span data-stu-id="792c2-118">`Disconnect-PSSession`: Disconnects a PSSession.</span></span>
- <span data-ttu-id="792c2-119">`Get-PSSession`: Hiermee wordt PSSessions opgehaald op de lokale computer of op externe computers.</span><span class="sxs-lookup"><span data-stu-id="792c2-119">`Get-PSSession`: Gets PSSessions on the local computer or on remote computers.</span></span>
- <span data-ttu-id="792c2-120">`Receive-PSSession`: Hiermee worden de resultaten opgehaald van opdrachten die zijn uitgevoerd in sessies zonder verbinding.</span><span class="sxs-lookup"><span data-stu-id="792c2-120">`Receive-PSSession`: Gets the results of commands that ran in disconnected sessions.</span></span>
- <span data-ttu-id="792c2-121">`Invoke-Command`: Met de para meter **InDisconnectedSession** wordt direct een PSSession gemaakt en wordt de verbinding verbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-121">`Invoke-Command`: **InDisconnectedSession** parameter creates a PSSession and disconnects immediately.</span></span>

## <a name="how-the-disconnected-sessions-feature-works"></a><span data-ttu-id="792c2-122">De werking van de functie voor verbroken sessies</span><span class="sxs-lookup"><span data-stu-id="792c2-122">How the Disconnected Sessions feature works</span></span>

<span data-ttu-id="792c2-123">Vanaf Power Shell 3,0 zijn PSSessions onafhankelijk van de sessies waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="792c2-123">Beginning in PowerShell 3.0, PSSessions are independent of the sessions in which they're created.</span></span> <span data-ttu-id="792c2-124">Actieve PSSessions worden onderhouden op de externe computer of aan de **server zijde** van de verbinding, zelfs als de sessie waarin de PSSession is gemaakt gesloten is en de oorspronkelijke computer wordt afgesloten of de verbinding met het netwerk is verbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-124">Active PSSessions are maintained on the remote computer or **server-side** of the connection, even if the session in which the PSSession was created is closed and the originating computer is shut down or disconnected from the network.</span></span>

<span data-ttu-id="792c2-125">In Power Shell 2,0 wordt de PSSession verwijderd van de externe computer wanneer deze wordt losgekoppeld van de oorspronkelijke sessie of de sessie waarin deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="792c2-125">In PowerShell 2.0, the PSSession is deleted from the remote computer when it's disconnected from the originating session or the session in which it was created ends.</span></span>

<span data-ttu-id="792c2-126">Wanneer u een PSSession verbreekt, blijft de PSSession actief en wordt deze op de externe computer onderhouden.</span><span class="sxs-lookup"><span data-stu-id="792c2-126">When you disconnect a PSSession, the PSSession remains active and is maintained on the remote computer.</span></span> <span data-ttu-id="792c2-127">De sessie status wordt gewijzigd van **actief** in **losgekoppeld**.</span><span class="sxs-lookup"><span data-stu-id="792c2-127">The session state changes from **Running** to **Disconnected**.</span></span> <span data-ttu-id="792c2-128">U kunt opnieuw verbinding maken met een niet-verbonden PSSession van de huidige sessie of van een andere sessie op dezelfde computer of vanaf een andere computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-128">You can reconnect to a disconnected PSSession from the current session or from a different session on the same computer, or from a different computer.</span></span> <span data-ttu-id="792c2-129">De externe computer die de sessie onderhoudt, moet actief zijn en verbonden zijn met het netwerk.</span><span class="sxs-lookup"><span data-stu-id="792c2-129">The remote computer that maintains the session must be running and be connected to the network.</span></span>

<span data-ttu-id="792c2-130">Opdrachten in een PSSession zonder verbinding blijven worden uitgevoerd op de externe computer totdat de opdracht is voltooid of de uitvoer buffer vol is.</span><span class="sxs-lookup"><span data-stu-id="792c2-130">Commands in a disconnected PSSession continue to run uninterrupted on the remote computer until the command completes or the output buffer fills.</span></span> <span data-ttu-id="792c2-131">Als u wilt voor komen dat een volledige uitvoer buffer een opdracht onderbreekt, gebruikt u de para meter **OutputBufferingMode** van de `Disconnect-PSSession` -, `New-PSSessionOption` -of- `New-PSTransportOption` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="792c2-131">To prevent a full output buffer from suspending a command, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="792c2-132">Verbroken sessies worden onderhouden met de status niet verbonden op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-132">Disconnected sessions are maintained in the disconnected state on the remote computer.</span></span> <span data-ttu-id="792c2-133">Ze zijn beschikbaar zodat u opnieuw verbinding kunt maken, totdat u de PSSession verwijdert, zoals met de `Remove-PSSession` cmdlet of totdat de time-out voor inactiviteit van de PSSession verloopt.</span><span class="sxs-lookup"><span data-stu-id="792c2-133">They're available for you to reconnect, until you delete the PSSession, such as by using the `Remove-PSSession` cmdlet, or until the idle timeout of the PSSession expires.</span></span> <span data-ttu-id="792c2-134">U kunt de time-out voor inactiviteit van een PSSession aanpassen met behulp van de **IdleTimeoutSec** -of **IdleTimeout** -para meters van de `Disconnect-PSSession` -, `New-PSSessionOption` -of- `New-PSTransportOption` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="792c2-134">You can adjust the idle timeout of a PSSession by using the **IdleTimeoutSec** or **IdleTimeout** parameters of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="792c2-135">Een andere gebruiker kan verbinding maken met PSSessions die u hebt gemaakt, maar alleen als ze de referenties kunnen opgeven die zijn gebruikt voor het maken van de sessie, of de `RunAs` referenties van de sessie configuratie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="792c2-135">Another user can connect to PSSessions that you created, but only if they can provide the credentials that were used to create the session, or use the `RunAs` credentials of the session configuration.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="792c2-136">PSSessions ophalen</span><span class="sxs-lookup"><span data-stu-id="792c2-136">How to get PSSessions</span></span>

<span data-ttu-id="792c2-137">Vanaf Power Shell 3,0 krijgt de `Get-PSSession` cmdlet PSSessions op de lokale computer en externe computers.</span><span class="sxs-lookup"><span data-stu-id="792c2-137">Beginning in PowerShell 3.0, the `Get-PSSession` cmdlet gets PSSessions on the local computer and remote computers.</span></span> <span data-ttu-id="792c2-138">Er kunnen ook PSSessions worden opgehaald die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="792c2-138">It can also get PSSessions that were created in the current session.</span></span>

<span data-ttu-id="792c2-139">Als u PSSessions op de lokale computer of externe computers wilt ophalen, gebruikt u de para meter **ComputerName** of **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="792c2-139">To get PSSessions on the local computer or remote computers, use the **ComputerName** or **ConnectionUri** parameters.</span></span> <span data-ttu-id="792c2-140">Zonder para meters worden `Get-PSSession` PSSession opgehaald die zijn gemaakt in de lokale sessie, ongeacht waar ze worden beëindigd.</span><span class="sxs-lookup"><span data-stu-id="792c2-140">Without parameters, `Get-PSSession` gets PSSession that were created in the local session, regardless of where they terminate.</span></span>

<span data-ttu-id="792c2-141">Vergeet niet om PSSessions te zoeken naar de computer waarop deze worden onderhouden, dat wil zeggen, de externe computer of de **Server** .</span><span class="sxs-lookup"><span data-stu-id="792c2-141">When getting PSSessions, remember to look for them on the computer on which they're maintained, that is, the remote or **server-side** computer.</span></span>

<span data-ttu-id="792c2-142">Als u bijvoorbeeld een PSSession maakt op de Server01-computer, kunt u de sessie ophalen van de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-142">For example, if you create a PSSession to the Server01 computer, get the session from the Server01 computer.</span></span> <span data-ttu-id="792c2-143">Als u een PSSession van een andere computer op de lokale computer maakt, haalt u de sessie vanaf de lokale computer op.</span><span class="sxs-lookup"><span data-stu-id="792c2-143">If you create a PSSession from another computer to the local computer, get the session from the local computer.</span></span>

<span data-ttu-id="792c2-144">In de volgende opdracht volgorde ziet u hoe `Get-PSSession` werkt.</span><span class="sxs-lookup"><span data-stu-id="792c2-144">The following command sequence shows how `Get-PSSession` works.</span></span>

<span data-ttu-id="792c2-145">Met de eerste opdracht maakt u een sessie op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-145">The first command creates a session to the Server01 computer.</span></span> <span data-ttu-id="792c2-146">De sessie bevindt zich op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-146">The session resides on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="792c2-147">Als u de sessie wilt downloaden, gebruikt u de para meter **ComputerName** van `Get-PSSession` met de waarde Server01.</span><span class="sxs-lookup"><span data-stu-id="792c2-147">To get the session, use the **ComputerName** parameter of `Get-PSSession` with a value of Server01.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="792c2-148">Als de waarde van de para meter **ComputerName** van `Get-PSSession` is localhost, `Get-PSSession` worden er PSSessions opgehaald die eindigen op en worden onderhouden op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-148">If the value of the **ComputerName** parameter of `Get-PSSession` is localhost, `Get-PSSession` gets PSSessions that terminate at and are maintained on the local computer.</span></span> <span data-ttu-id="792c2-149">Er wordt geen PSSessions op de Server01-computer opgehaald, zelfs als deze zijn gestart op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-149">It doesn't get PSSessions on the Server01 computer, even if they were started on the local computer.</span></span>

```powershell
Get-PSSession -ComputerName localhost
```

<span data-ttu-id="792c2-150">Als u sessies wilt ophalen die in de huidige sessie zijn gemaakt, gebruikt u de `Get-PSSession` cmdlet zonder para meters.</span><span class="sxs-lookup"><span data-stu-id="792c2-150">To get sessions that were created in the current session, use the `Get-PSSession` cmdlet without parameters.</span></span> <span data-ttu-id="792c2-151">In dit voor beeld `Get-PSSession` wordt de PSSession opgehaald die in de huidige sessie is gemaakt en wordt er verbinding gemaakt met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-151">In this example, `Get-PSSession` gets the PSSession that was created in the current session and connects to the Server01 computer.</span></span>

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a><span data-ttu-id="792c2-152">Sessies verbreken</span><span class="sxs-lookup"><span data-stu-id="792c2-152">How to disconnect sessions</span></span>

<span data-ttu-id="792c2-153">Gebruik de cmdlet om de verbinding met een PSSession te verbreken `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="792c2-153">To disconnect a PSSession, use the `Disconnect-PSSession` cmdlet.</span></span> <span data-ttu-id="792c2-154">Als u de PSSession wilt identificeren, gebruikt u de para meter **Session** of pijplijnt u een PSSession van de `New-PSSession` `Get-PSSession` cmdlets `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="792c2-154">To identify the PSSession, use the **Session** parameter, or pipeline a PSSession from the `New-PSSession` or `Get-PSSession` cmdlets to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="792c2-155">Met de volgende opdracht wordt de verbinding tussen de PSSession en de Server01-computer verbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-155">The following command disconnects the PSSession to the Server01 computer.</span></span>
<span data-ttu-id="792c2-156">U ziet dat de waarde van de eigenschap **State** is **losgekoppeld** en dat de **Beschik baarheid** **geen** is.</span><span class="sxs-lookup"><span data-stu-id="792c2-156">Notice that the value of the **State** property is **Disconnected** and the **Availability** is **None**.</span></span>

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="792c2-157">Als u een verbroken sessie wilt maken, gebruikt u de para meter **InDisconnectedSession** van de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="792c2-157">To create a disconnected session, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="792c2-158">Er wordt een sessie gemaakt, de opdracht wordt gestart en onmiddellijk wordt de verbinding verbroken, voordat de opdracht uitvoer kan retour neren.</span><span class="sxs-lookup"><span data-stu-id="792c2-158">It creates a session, starts the command, and disconnects immediately, before the command can return any output.</span></span>

<span data-ttu-id="792c2-159">Met de volgende opdracht wordt een `Get-WinEvent` opdracht uitgevoerd in een verbroken sessie op de externe computer Server02.</span><span class="sxs-lookup"><span data-stu-id="792c2-159">The following command runs a `Get-WinEvent` command in a disconnected session on the Server02 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a><span data-ttu-id="792c2-160">Verbinding maken met sessies zonder verbinding</span><span class="sxs-lookup"><span data-stu-id="792c2-160">How to connect to disconnected sessions</span></span>

<span data-ttu-id="792c2-161">U kunt verbinding maken met elke beschik bare losgekoppelde PSSession van de sessie waarin u de PSSession hebt gemaakt of van andere sessies op de lokale computer of andere computers.</span><span class="sxs-lookup"><span data-stu-id="792c2-161">You can connect to any available disconnected PSSession from the session in which you created the PSSession or from other sessions on the local computer or other computers.</span></span>

<span data-ttu-id="792c2-162">U kunt een PSSession maken, opdrachten uitvoeren in de PSSession, de verbinding verbreken met de PSSession, de Power shell sluiten en de computer afsluiten.</span><span class="sxs-lookup"><span data-stu-id="792c2-162">You can create a PSSession, run commands in the PSSession, disconnect from the PSSession, close PowerShell, and shut down the computer.</span></span> <span data-ttu-id="792c2-163">Uur later kunt u een andere computer openen, de PSSession ophalen, er verbinding mee maken en de resultaten ophalen van opdrachten die in de PSSession werden uitgevoerd terwijl de verbinding werd verbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-163">Hours later, you can open a different computer, get the PSSession, connect to it, and get the results of commands that ran in the PSSession while it was disconnected.</span></span> <span data-ttu-id="792c2-164">Vervolgens kunt u meer opdrachten in de sessie uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="792c2-164">Then you can run more commands in the session.</span></span>

<span data-ttu-id="792c2-165">Gebruik de cmdlet om verbinding te maken met een PSSession waarvan de verbinding is verbroken `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="792c2-165">To connect a disconnected PSSession, use the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="792c2-166">Gebruik de para meters **ComputerName** of **ConnectionUri** om de PSSession te identificeren of om een PSSession van `Get-PSSession` aan te geven `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="792c2-166">Use the **ComputerName** or **ConnectionUri** parameters to identify the PSSession, or pipeline a PSSession from `Get-PSSession` to `Connect-PSSession`.</span></span>

<span data-ttu-id="792c2-167">Met de volgende opdracht worden de sessies op de Server02-computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="792c2-167">The following command gets the sessions on the Server02 computer.</span></span> <span data-ttu-id="792c2-168">De uitvoer bevat twee niet-verbonden sessies, beide beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="792c2-168">The output includes two disconnected sessions, both of which are available.</span></span>

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="792c2-169">Met de volgende opdracht maakt u verbinding met Session2.</span><span class="sxs-lookup"><span data-stu-id="792c2-169">The following command connects to Session2.</span></span> <span data-ttu-id="792c2-170">De PSSession is nu geopend en beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="792c2-170">The PSSession is now open and available.</span></span>

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a><span data-ttu-id="792c2-171">De resultaten ophalen</span><span class="sxs-lookup"><span data-stu-id="792c2-171">How to get the results</span></span>

<span data-ttu-id="792c2-172">Gebruik de cmdlet om de resultaten op te halen van opdrachten die zijn uitgevoerd in een PSSession zonder verbinding `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="792c2-172">To get the results of commands that ran in a disconnected PSSession, use the `Receive-PSSession` cmdlet.</span></span>

<span data-ttu-id="792c2-173">U kunt gebruiken `Receive-PSSession` in plaats van de `Connect-PSSession` cmdlet te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="792c2-173">You can use `Receive-PSSession` rather than using the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="792c2-174">Als de sessie al opnieuw is verbonden, worden `Receive-PSSession` de resultaten opgehaald van opdrachten die zijn uitgevoerd toen de verbinding van de sessie werd verbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-174">If the session is already reconnected, `Receive-PSSession` gets the results of commands that ran when the session was disconnected.</span></span> <span data-ttu-id="792c2-175">Als de PSSession nog steeds is verbroken, wordt `Receive-PSSession` er verbinding mee gemaakt en worden de resultaten weer gegeven van opdrachten die zijn uitgevoerd toen de verbinding werd verbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-175">If the PSSession is still disconnected, `Receive-PSSession` connects to it and then gets the results of commands that ran while it was disconnected.</span></span>

<span data-ttu-id="792c2-176">`Receive-PSSession` kan de resultaten in een taak (asynchroon) of aan het host-programma (synchroon) retour neren.</span><span class="sxs-lookup"><span data-stu-id="792c2-176">`Receive-PSSession` can return the results in a job (asynchronously) or to the host program (synchronously).</span></span> <span data-ttu-id="792c2-177">Gebruik de para meter **outtarget** om **taak** of **host** te selecteren.</span><span class="sxs-lookup"><span data-stu-id="792c2-177">Use the **OutTarget** parameter to select **Job** or **Host**.</span></span> <span data-ttu-id="792c2-178">De standaard waarde is **host**.</span><span class="sxs-lookup"><span data-stu-id="792c2-178">The default value is **Host**.</span></span> <span data-ttu-id="792c2-179">Als de opdracht die wordt ontvangen, echter is gestart in de huidige sessie als een **taak**, wordt deze standaard als een **taak** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="792c2-179">However, if the command that's being received was started in the current session as a **Job**, it's returned as a **Job** by default.</span></span>

<span data-ttu-id="792c2-180">Met de volgende opdracht wordt de `Receive-PSSession` cmdlet gebruikt om verbinding te maken met de PSSession op de Server02-computer en worden de resultaten opgehaald van de `Get-WinEvent` opdracht die in de Session3-sessie is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="792c2-180">The following command uses the `Receive-PSSession` cmdlet to connect to the PSSession on the Server02 computer and get the results of the `Get-WinEvent` command that ran in the Session3 session.</span></span> <span data-ttu-id="792c2-181">De opdracht maakt gebruik van de **Outtarget** -para meter om de resultaten in een **taak** op te halen.</span><span class="sxs-lookup"><span data-stu-id="792c2-181">The command uses the **OutTarget** parameter to get the results in a **Job**.</span></span>

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

<span data-ttu-id="792c2-182">Gebruik de cmdlet om de resultaten van de taak te verkrijgen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="792c2-182">To get the job's results, use the `Receive-Job` cmdlet.</span></span>

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a><span data-ttu-id="792c2-183">Eigenschappen van status en beschik baarheid</span><span class="sxs-lookup"><span data-stu-id="792c2-183">State and Availability properties</span></span>

<span data-ttu-id="792c2-184">Met de eigenschappen **status** en **Beschik baarheid** van een niet-verbonden PSSession weet u of de sessie voor u beschikbaar is om opnieuw verbinding te maken.</span><span class="sxs-lookup"><span data-stu-id="792c2-184">The **State** and **Availability** properties of a disconnected PSSession tell you whether the session is available for you to reconnect to it.</span></span>

<span data-ttu-id="792c2-185">Wanneer een PSSession is verbonden met de huidige sessie, wordt de status ervan **geopend** en is de beschik baarheid **beschikbaar**.</span><span class="sxs-lookup"><span data-stu-id="792c2-185">When a PSSession is connected to the current session, its state is **Opened** and its availability is **Available**.</span></span> <span data-ttu-id="792c2-186">Wanneer u de verbinding met de PSSession verbreekt, wordt de status van de PSSession- **verbinding verbroken** en is de beschik baarheid **geen**.</span><span class="sxs-lookup"><span data-stu-id="792c2-186">When you disconnect from the PSSession, the PSSession state is **Disconnected** and its availability is **None**.</span></span>

<span data-ttu-id="792c2-187">De waarde van de eigenschap **State** is relatief ten opzichte van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="792c2-187">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="792c2-188">Als de waarde voor de **verbinding is verbroken** , betekent dit dat de PSSession niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="792c2-188">A value of **Disconnected** means that the PSSession isn't connected to the current session.</span></span> <span data-ttu-id="792c2-189">Maar dit betekent niet dat de PSSession-verbinding met alle sessies is verbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-189">But, it doesn't mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="792c2-190">Deze is mogelijk verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="792c2-190">It might be connected to a different session.</span></span>

<span data-ttu-id="792c2-191">Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken of opnieuw verbinding wilt maken met de PSSession.</span><span class="sxs-lookup"><span data-stu-id="792c2-191">To determine whether you can connect or reconnect to the PSSession, use the **Availability** property.</span></span> <span data-ttu-id="792c2-192">De waarde **geen** geeft aan dat u verbinding kunt maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="792c2-192">A value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="792c2-193">De waarde **bezet** geeft aan dat u geen verbinding kunt maken met de PSSession, omdat deze is verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="792c2-193">A value of **Busy** indicates that you can't connect to the PSSession because it's connected to another session.</span></span>

<span data-ttu-id="792c2-194">Het volgende voor beeld wordt uitgevoerd in twee Power shell-sessies op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-194">The following example is run in two PowerShell sessions on the same computer.</span></span>
<span data-ttu-id="792c2-195">Let op de wijzigings waarden van de **status** -en **beschikbaarheids** eigenschappen in elke sessie, omdat de PSSession is losgekoppeld en opnieuw verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="792c2-195">Note the changing values of the **State** and **Availability** properties in each session as the PSSession is disconnected and reconnected.</span></span>

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

<span data-ttu-id="792c2-196">Verbroken sessies worden op de externe computer gehandhaafd totdat u ze verwijdert, bijvoorbeeld door de cmdlet te gebruiken `Remove-PSSession` of als er een time-out optreedt. De eigenschap **IdleTimeout** van een PSSession bepaalt hoe lang een verbroken sessie wordt behouden voordat deze wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="792c2-196">Disconnected sessions are maintained on the remote computer until you delete them, such as by using the `Remove-PSSession` cmdlet, or they time out. The **IdleTimeout** property of a PSSession determines how long a disconnected session is maintained before it's deleted.</span></span>

<span data-ttu-id="792c2-197">PSSessions zijn niet actief wanneer de **heartbeat-thread** geen antwoord ontvangt.</span><span class="sxs-lookup"><span data-stu-id="792c2-197">PSSessions are idle when the **heartbeat thread** receives no response.</span></span>
<span data-ttu-id="792c2-198">Als u een sessie verbreekt, wordt deze niet-actief en wordt de **IdleTimeout** -klok gestart, zelfs als opdrachten nog steeds worden uitgevoerd in de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="792c2-198">Disconnecting a session makes it idle and starts the **IdleTimeout** clock, even if commands are still running in the disconnected session.</span></span> <span data-ttu-id="792c2-199">Power shell beschouwt beëindigde sessies als actief, maar niet-actief.</span><span class="sxs-lookup"><span data-stu-id="792c2-199">PowerShell considers disconnected sessions to be active, but idle.</span></span>

<span data-ttu-id="792c2-200">Wanneer u sessies maakt en verbreekt, controleert u of de time-out voor inactiviteit in de PSSession lang genoeg is om de sessie voor uw behoeften te onderhouden, maar niet zo lang dat er overbodige resources op de externe computer worden verbruikt.</span><span class="sxs-lookup"><span data-stu-id="792c2-200">When creating and disconnecting sessions, verify that the idle timeout in the PSSession is long enough to maintain the session for your needs, but not so long that it consumes unnecessary resources on the remote computer.</span></span>

<span data-ttu-id="792c2-201">De eigenschap **IdleTimeoutMs** van de sessie configuratie bepaalt de standaard time-out voor inactiviteit van sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="792c2-201">The **IdleTimeoutMs** property of the session configuration determines the default idle timeout of sessions that use the session configuration.</span></span> <span data-ttu-id="792c2-202">U kunt de standaard waarde overschrijven, maar de waarde die u gebruikt, kan niet groter zijn dan de eigenschap **MaxIdleTimeoutMs** van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="792c2-202">You can override the default value, but the value that you use can't exceed the **MaxIdleTimeoutMs** property of the session configuration.</span></span>

<span data-ttu-id="792c2-203">Als u de waarde van de waarden **IdleTimeoutMs** en **MaxIdleTimeoutMs** van een sessie configuratie wilt zoeken, gebruikt u de volgende opdracht indeling.</span><span class="sxs-lookup"><span data-stu-id="792c2-203">To find the value of the **IdleTimeoutMs** and **MaxIdleTimeoutMs** values of a session configuration, use the following command format.</span></span>

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

<span data-ttu-id="792c2-204">U kunt de standaard waarde in de sessie configuratie overschrijven en de time-out voor inactiviteit van een PSSession instellen wanneer u een PSSession maakt en wanneer u de verbinding verbreekt.</span><span class="sxs-lookup"><span data-stu-id="792c2-204">You can override the default value in the session configuration and set the idle timeout of a PSSession when you create a PSSession and when you disconnect.</span></span>

<span data-ttu-id="792c2-205">Als u lid bent van de groep Administrators op de externe computer, kunt u de eigenschappen **IdleTimeoutMs** en **MaxIdleTimeoutMs** van sessie configuraties maken en wijzigen.</span><span class="sxs-lookup"><span data-stu-id="792c2-205">If you're a member of the Administrators group on the remote computer, you can create and change the **IdleTimeoutMs** and **MaxIdleTimeoutMs** properties of session configurations.</span></span>

## <a name="idle-timeout-values"></a><span data-ttu-id="792c2-206">Time-outwaarden</span><span class="sxs-lookup"><span data-stu-id="792c2-206">Idle timeout values</span></span>

<span data-ttu-id="792c2-207">De waarde voor time-out voor inactiviteit van sessie configuraties en sessie opties is in milliseconden.</span><span class="sxs-lookup"><span data-stu-id="792c2-207">The idle timeout value of session configurations and session options is in milliseconds.</span></span> <span data-ttu-id="792c2-208">De waarde voor time-out voor inactiviteit van sessies en sessie configuratie opties is in enkele seconden.</span><span class="sxs-lookup"><span data-stu-id="792c2-208">The idle timeout value of sessions and session configuration options is in seconds.</span></span>

<span data-ttu-id="792c2-209">U kunt de time-out voor inactiviteit van een PSSession instellen wanneer u de PSSession ( `New-PSSession` , `Invoke-Command` ) maakt en wanneer u de verbinding met deze server verbreekt ( `Disconnect-PSSession` ).</span><span class="sxs-lookup"><span data-stu-id="792c2-209">You can set the idle timeout of a PSSession when you create the PSSession (`New-PSSession`, `Invoke-Command`) and when you disconnect from it (`Disconnect-PSSession`).</span></span> <span data-ttu-id="792c2-210">U kunt de waarde voor **IdleTimeout** echter niet wijzigen wanneer u verbinding maakt met de PSSession ( `Connect-PSSession` ) of resultaten ophalen ( `Receive-PSSession` ).</span><span class="sxs-lookup"><span data-stu-id="792c2-210">However, you can't change the **IdleTimeout** value when you connect to the PSSession (`Connect-PSSession`) or get results (`Receive-PSSession`).</span></span>

<span data-ttu-id="792c2-211">De `Connect-PSSession` `Receive-PSSession` cmdlets en hebben een **SessionOption** -para meter die een **SessionOption** -object gebruikt, zoals het resultaat dat door de cmdlet wordt geretourneerd `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="792c2-211">The `Connect-PSSession` and `Receive-PSSession` cmdlets have a **SessionOption** parameter that takes a **SessionOption** object, such as one returned by the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="792c2-212">De waarde voor **IdleTimeout** in **SessionOption** -object en de waarde voor **IdleTimeout** in de `$PSSessionOption` Voorkeurs variabele wijzigen niet de  waarde van de PSSession in een `Connect-PSSession` of- `Receive-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="792c2-212">The **IdleTimeout** value in **SessionOption** object and the **IdleTimeout** value in the `$PSSessionOption` preference variable don't change the value of the **IdleTimeout** of the PSSession in a `Connect-PSSession` or `Receive-PSSession` command.</span></span>

<span data-ttu-id="792c2-213">Als u een PSSession met een bepaalde time-outwaarde wilt maken, maakt u een `$PSSessionOption` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="792c2-213">To create a PSSession with a particular idle timeout value, create a `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="792c2-214">Stel de waarde van de eigenschap **IdleTimeout** in op de gewenste waarde (in milliseconden).</span><span class="sxs-lookup"><span data-stu-id="792c2-214">Set the value of the **IdleTimeout** property to the desired value (in milliseconds).</span></span>

<span data-ttu-id="792c2-215">Wanneer u PSSessions maakt, hebben de waarden in `$PSSessionOption` de variabele voor rang op de waarden in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="792c2-215">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="792c2-216">Met de volgende opdracht wordt bijvoorbeeld een time-out voor inactiviteit van 48 uur ingesteld:</span><span class="sxs-lookup"><span data-stu-id="792c2-216">For example, the following command sets an idle timeout of 48 hours:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

<span data-ttu-id="792c2-217">Als u een PSSession met een bepaalde time-outwaarde wilt maken, gebruikt u de para meter **IdleTimeoutMSec** van de `New-PSSessionOption` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="792c2-217">To create a PSSession with a particular idle timeout value, use the **IdleTimeoutMSec** parameter of the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="792c2-218">Gebruik vervolgens de optie sessie in de waarde van de para meter **SessionOption** van de- `New-PSSession` of- `Invoke-Command` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="792c2-218">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="792c2-219">De waarden die zijn ingesteld bij het maken van de sessie, hebben voor rang op de waarden die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="792c2-219">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="792c2-220">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="792c2-220">For example:</span></span>

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

<span data-ttu-id="792c2-221">Als u de time-out voor inactiviteit van een PSSession wilt wijzigen tijdens het verbreken van de verbinding, gebruikt u de para meter **IdleTimeoutSec** van de `Disconnect-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="792c2-221">To change the idle timeout of a PSSession when disconnecting, use the **IdleTimeoutSec** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="792c2-222">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="792c2-222">For example:</span></span>

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

<span data-ttu-id="792c2-223">Gebruik de para meters **IdleTimeoutSec** en **MaxIdleTimeoutSec** van de cmdlet om een sessie configuratie te maken met een bepaalde time-out voor inactiviteit en een maximale inactieve time-out `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="792c2-223">To create a session configuration with a particular idle timeout and maximum idle timeout, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="792c2-224">Gebruik vervolgens de transport optie in de waarde van de para meter **TransportOption** van `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="792c2-224">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="792c2-225">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="792c2-225">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="792c2-226">Als u de standaard time-out voor inactiviteit en de maximale time-out voor inactiviteit van een sessie configuratie wilt wijzigen, gebruikt u de para meters **IdleTimeoutSec** en **MaxIdleTimeoutSec** van de `New-PSTransportOption` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="792c2-226">To change the default idle timeout and maximum idle timeout of a session configuration, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="792c2-227">Gebruik vervolgens de transport optie in de waarde van de para meter **TransportOption** van `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="792c2-227">Then, use the transport option in the value of the **TransportOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="792c2-228">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="792c2-228">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a><span data-ttu-id="792c2-229">Modus voor uitvoer buffer</span><span class="sxs-lookup"><span data-stu-id="792c2-229">Output buffering mode</span></span>

<span data-ttu-id="792c2-230">De uitvoer buffer modus van een PSSession bepaalt hoe de uitvoer van de opdracht wordt beheerd wanneer de uitvoer buffer van de PSSession vol is.</span><span class="sxs-lookup"><span data-stu-id="792c2-230">The output buffering mode of a PSSession determines how command output is managed when the output buffer of the PSSession is full.</span></span>

<span data-ttu-id="792c2-231">In een verbroken sessie bepaalt de uitvoer buffer modus effectief of de opdracht wordt uitgevoerd terwijl de sessie wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-231">In a disconnected session, the output buffering mode effectively determines whether the command continues to run while the session is disconnected.</span></span>

<span data-ttu-id="792c2-232">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="792c2-232">The valid values as follows:</span></span>

- <span data-ttu-id="792c2-233">**Blok keren**.</span><span class="sxs-lookup"><span data-stu-id="792c2-233">**Block**.</span></span> <span data-ttu-id="792c2-234">Wanneer de uitvoer buffer vol is, wordt de uitvoering onderbroken totdat de buffer leeg is.</span><span class="sxs-lookup"><span data-stu-id="792c2-234">When the output buffer is full, execution is suspended until the buffer is clear.</span></span> <span data-ttu-id="792c2-235">De standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="792c2-235">The default value.</span></span>
- <span data-ttu-id="792c2-236">**Neerzetten**.</span><span class="sxs-lookup"><span data-stu-id="792c2-236">**Drop**.</span></span> <span data-ttu-id="792c2-237">Wanneer de uitvoer buffer vol is, wordt de uitvoering voortgezet.</span><span class="sxs-lookup"><span data-stu-id="792c2-237">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="792c2-238">Wanneer er een nieuwe uitvoer wordt gegenereerd, wordt de oudste uitvoer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="792c2-238">As new output is generated, the oldest output is discarded.</span></span>

<span data-ttu-id="792c2-239">Met **blok keren** worden gegevens bewaard, maar kan de opdracht worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-239">**Block** preserves data, but might interrupt the command.</span></span> <span data-ttu-id="792c2-240">Met de waarde **Drop** kan de opdracht worden voltooid, hoewel gegevens verloren kunnen gaan.</span><span class="sxs-lookup"><span data-stu-id="792c2-240">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="792c2-241">Wanneer u de waarde voor **neerzetten** gebruikt, moet u de uitvoer van de opdracht omleiden naar een bestand op schijf.</span><span class="sxs-lookup"><span data-stu-id="792c2-241">When using the **Drop** value, redirect the command output to a file on disk.</span></span> <span data-ttu-id="792c2-242">Deze waarde wordt aanbevolen voor verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="792c2-242">This value is recommended for disconnected sessions.</span></span>

<span data-ttu-id="792c2-243">De eigenschap **OutputBufferingMode** van de sessie configuratie bepaalt de standaard modus voor uitvoer buffering van sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="792c2-243">The **OutputBufferingMode** property of the session configuration determines the default output buffering mode of sessions that use the session configuration.</span></span>

<span data-ttu-id="792c2-244">U kunt een van de volgende opdracht indelingen gebruiken om de waarde van de **OutputBufferingMode** van de sessie configuratie te vinden:</span><span class="sxs-lookup"><span data-stu-id="792c2-244">To find a session configuration's value of the **OutputBufferingMode**, you can use either of the following command formats:</span></span>

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

<span data-ttu-id="792c2-245">U kunt de standaard waarde in de sessie configuratie overschrijven en de uitvoer buffer modus van een PSSession instellen wanneer u een PSSession maakt, wanneer u de verbinding verbreekt en wanneer u opnieuw verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="792c2-245">You can override the default value in the session configuration and set the output buffering mode of a PSSession when you create a PSSession, when you disconnect, and when you reconnect.</span></span>

<span data-ttu-id="792c2-246">Als u lid bent van de groep Administrators op de externe computer, kunt u de uitvoer buffer modus van sessie configuraties maken en wijzigen.</span><span class="sxs-lookup"><span data-stu-id="792c2-246">If you're a member of the Administrators group on the remote computer, you can create and change the output buffering mode of session configurations.</span></span>

<span data-ttu-id="792c2-247">Als u een PSSession wilt maken met een uitvoer buffer methode **Drop**, maakt u een `$PSSessionOption` Voorkeurs variabele waarin de waarde van de eigenschap **OutputBufferingMode** wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="792c2-247">To create a PSSession with an output buffering mode of **Drop**, create a `$PSSessionOption` preference variable in which the value of the **OutputBufferingMode** property is **Drop**.</span></span>

<span data-ttu-id="792c2-248">Wanneer u PSSessions maakt, hebben de waarden in `$PSSessionOption` de variabele voor rang op de waarden in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="792c2-248">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="792c2-249">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="792c2-249">For example:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

<span data-ttu-id="792c2-250">Als u een PSSession wilt maken met een uitvoer buffer methode **Drop**, gebruikt u de para meter **OutputBufferingMode** van de `New-PSSessionOption` cmdlet om een sessie optie met de waarde **Drop** te maken.</span><span class="sxs-lookup"><span data-stu-id="792c2-250">To create a PSSession with an output buffering mode of **Drop**, use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop**.</span></span> <span data-ttu-id="792c2-251">Gebruik vervolgens de optie sessie in de waarde van de para meter **SessionOption** van de- `New-PSSession` of- `Invoke-Command` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="792c2-251">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="792c2-252">De waarden die zijn ingesteld bij het maken van de sessie, hebben voor rang op de waarden die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="792c2-252">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="792c2-253">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="792c2-253">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

<span data-ttu-id="792c2-254">Als u de modus voor uitvoer buffering van een PSSession wilt wijzigen wanneer de verbinding wordt verbroken, gebruikt u de para meter **OutputBufferingMode** van de `Disconnect-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="792c2-254">To change the output buffering mode of a PSSession when disconnecting, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="792c2-255">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="792c2-255">For example:</span></span>

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

<span data-ttu-id="792c2-256">Als u de modus voor uitvoer buffering van een PSSession wilt wijzigen wanneer u opnieuw verbinding maakt, gebruikt u de para meter **OutputBufferingMode** van de `New-PSSessionOption` cmdlet om een sessie optie met de waarde **Drop** te maken.</span><span class="sxs-lookup"><span data-stu-id="792c2-256">To change the output buffering mode of a PSSession when reconnecting, use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop**.</span></span> <span data-ttu-id="792c2-257">Gebruik vervolgens de optie sessie in de waarde van de para meter **SessionOption** van `Connect-PSSession` of `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="792c2-257">Then, use the session option in the value of the **SessionOption** parameter of `Connect-PSSession` or `Receive-PSSession`.</span></span>

<span data-ttu-id="792c2-258">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="792c2-258">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

<span data-ttu-id="792c2-259">Als u een sessie configuratie met een standaard uitvoer buffer modus wilt maken **, gebruikt** u de para meter **OutputBufferingMode** van de `New-PSTransportOption` cmdlet om een transport optie object te maken met de waarde **Drop**.</span><span class="sxs-lookup"><span data-stu-id="792c2-259">To create a session configuration with a default output buffering mode of **Drop**, use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option object with a value of **Drop**.</span></span> <span data-ttu-id="792c2-260">Gebruik vervolgens de transport optie in de waarde van de para meter **TransportOption** van `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="792c2-260">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="792c2-261">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="792c2-261">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="792c2-262">Als u de standaard modus voor uitvoer buffering van een sessie configuratie wilt wijzigen, gebruikt u de para meter **OutputBufferingMode** van de `New-PSTransportOption` cmdlet om een transport optie te maken met de waarde **Drop**.</span><span class="sxs-lookup"><span data-stu-id="792c2-262">To change the default output buffering mode of a session configuration, use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option with a value of **Drop**.</span></span> <span data-ttu-id="792c2-263">Gebruik vervolgens de transport optie in de waarde van de para meter **SessionOption** van `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="792c2-263">Then, use the Transport option in the value of the **SessionOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="792c2-264">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="792c2-264">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a><span data-ttu-id="792c2-265">Loop Back-sessies verbreken</span><span class="sxs-lookup"><span data-stu-id="792c2-265">Disconnecting loopback sessions</span></span>

<span data-ttu-id="792c2-266">Loop Back-sessies of lokale sessies zijn PSSessions die afkomstig zijn van en eindigen op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-266">Loopback sessions, or local sessions, are PSSessions that originate and terminate on the same computer.</span></span> <span data-ttu-id="792c2-267">Net als bij andere PSSessions worden actieve loop Back-sessies op de computer op het externe einde van de verbinding (de lokale computer) bewaard, zodat u de verbinding met loop Back-sessies kunt verbreken en opnieuw verbinding moet maken.</span><span class="sxs-lookup"><span data-stu-id="792c2-267">Like other PSSessions, active loopback sessions are maintained on the computer on the remote end of the connection (the local computer), so you can disconnect from and reconnect to loopback sessions.</span></span>

<span data-ttu-id="792c2-268">Loop Back-sessies worden standaard gemaakt met een netwerk beveiligings token dat geen opdrachten toestaat die in de sessie worden uitgevoerd om toegang te krijgen tot andere computers.</span><span class="sxs-lookup"><span data-stu-id="792c2-268">By default, loopback sessions are created with a network security token that doesn't permit commands run in the session to access other computers.</span></span> <span data-ttu-id="792c2-269">U kunt opnieuw verbinding maken met loop Back-sessies met een netwerk beveiligings token van een wille keurige sessie op de lokale computer of een externe computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-269">You can reconnect to loopback sessions that have a network security token from any session on the local computer or a remote computer.</span></span>

<span data-ttu-id="792c2-270">Als u echter de para meter **EnableNetworkAccess** van de `New-PSSession` cmdlet, `Enter-PSSession` of gebruikt `Invoke-Command` , wordt de loop back-sessie gemaakt met een interactief beveiligings token.</span><span class="sxs-lookup"><span data-stu-id="792c2-270">However, if you use the **EnableNetworkAccess** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlet, the loopback session is created with an interactive security token.</span></span> <span data-ttu-id="792c2-271">Met het interactieve token kunnen opdrachten die worden uitgevoerd in de loop back-sessie gegevens van andere computers ophalen.</span><span class="sxs-lookup"><span data-stu-id="792c2-271">The interactive token enables commands that run in the loopback session to get data from other computers.</span></span>

<span data-ttu-id="792c2-272">U kunt de loop Back-sessies met interactieve tokens verbreken en vervolgens opnieuw verbinding maken met de-sessie of een andere sessie op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-272">You can disconnect loopback sessions with interactive tokens and then reconnect to them from the same session or a different session on the same computer.</span></span>
<span data-ttu-id="792c2-273">Om bijvoorbeeld kwaad aardige toegang te voor komen, kunt u opnieuw verbinding maken met loop Back-sessies met interactieve tokens van de computer waarop deze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="792c2-273">However, to prevent malicious access, you can reconnect to loopback sessions with interactive tokens only from the computer on which they were created.</span></span>

## <a name="waiting-for-jobs-in-disconnected-sessions"></a><span data-ttu-id="792c2-274">Wachten op taken in sessies zonder verbinding</span><span class="sxs-lookup"><span data-stu-id="792c2-274">Waiting for jobs in disconnected sessions</span></span>

<span data-ttu-id="792c2-275">De `Wait-Job` cmdlet wacht tot een taak is voltooid en keert vervolgens terug naar de opdracht prompt of de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="792c2-275">The `Wait-Job` cmdlet waits until a job completes and then returns to the command prompt or the next command.</span></span> <span data-ttu-id="792c2-276">`Wait-Job`Retourneert standaard als de sessie waarin een taak wordt uitgevoerd, niet is verbonden.</span><span class="sxs-lookup"><span data-stu-id="792c2-276">By default, `Wait-Job` returns if the session in which a job is running is disconnected.</span></span> <span data-ttu-id="792c2-277">Als u de `Wait-Job` cmdlet wilt wachten totdat de sessie opnieuw is verbonden, gebruikt u de para meter **Forces** in de status **geopend** .</span><span class="sxs-lookup"><span data-stu-id="792c2-277">To direct the `Wait-Job` cmdlet to wait until the session is reconnected, in the **Opened** state, use the **Force** parameter.</span></span> <span data-ttu-id="792c2-278">Zie [wait-job](xref:Microsoft.PowerShell.Core.Wait-Job)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="792c2-278">For more information, see [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).</span></span>

## <a name="robust-sessions-and-unintentional-disconnection"></a><span data-ttu-id="792c2-279">Robuuste sessies en onbedoelde verbreken van de verbinding</span><span class="sxs-lookup"><span data-stu-id="792c2-279">Robust sessions and unintentional disconnection</span></span>

<span data-ttu-id="792c2-280">Een PSSession kan per ongeluk worden verbroken vanwege een storing in de computer of netwerk storingen.</span><span class="sxs-lookup"><span data-stu-id="792c2-280">A PSSession might be unintentionally disconnected because of a computer failure or network outage.</span></span> <span data-ttu-id="792c2-281">Power shell probeert de PSSession te herstellen, maar het succes ervan is afhankelijk van de ernst en de duur van de oorzaak.</span><span class="sxs-lookup"><span data-stu-id="792c2-281">PowerShell attempts to recover the PSSession, but its success depends upon the severity and duration of the cause.</span></span>

<span data-ttu-id="792c2-282">De status van een onbedoelde ontkoppelde PSSession kan worden **verbroken** of **gesloten**, maar kan ook worden **losgekoppeld**.</span><span class="sxs-lookup"><span data-stu-id="792c2-282">The state of an unintentionally disconnected PSSession might be **Broken** or **Closed**, but it might also be **Disconnected**.</span></span> <span data-ttu-id="792c2-283">Als de waarde van **status** is **verbroken**, kunt u dezelfde technieken gebruiken om de PSSession te beheren zoals u zou doen als de verbinding met de sessie opzettelijk is verbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-283">If the value of **State** is **Disconnected**, you can use the same techniques to manage the PSSession as you would if the session were disconnected intentionally.</span></span> <span data-ttu-id="792c2-284">U kunt bijvoorbeeld de-cmdlet gebruiken `Connect-PSSession` om opnieuw verbinding te maken met de sessie en de `Receive-PSSession` cmdlet om de resultaten op te halen van opdrachten die zijn uitgevoerd terwijl de verbinding met de sessie werd verbroken.</span><span class="sxs-lookup"><span data-stu-id="792c2-284">For example, you can use the `Connect-PSSession` cmdlet to reconnect to the session and the `Receive-PSSession` cmdlet to get results of commands that ran while the session was disconnected.</span></span>

<span data-ttu-id="792c2-285">Als u sluit (afsluit) de sessie waarin een PSSession is gemaakt terwijl opdrachten worden uitgevoerd in de PSSession, onderhoudt Power shell de PSSession in de niet- **verbonden** status op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="792c2-285">If you close (exit) the session in which a PSSession was created while commands are running in the PSSession, PowerShell maintains the PSSession in the **Disconnected** state on the remote computer.</span></span> <span data-ttu-id="792c2-286">Als u de sessie sluit waarin een PSSession is gemaakt, maar er geen opdrachten worden uitgevoerd in de PSSession, probeert Power shell de PSSession niet te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="792c2-286">If you close (exit) the session in which a PSSession was created, but no commands are running in the PSSession, PowerShell doesn't attempt to maintain the PSSession.</span></span>

## <a name="see-also"></a><span data-ttu-id="792c2-287">Zie ook</span><span class="sxs-lookup"><span data-stu-id="792c2-287">See also</span></span>

[<span data-ttu-id="792c2-288">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="792c2-288">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="792c2-289">about_Remote</span><span class="sxs-lookup"><span data-stu-id="792c2-289">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="792c2-290">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="792c2-290">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="792c2-291">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="792c2-291">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="792c2-292">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="792c2-292">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="792c2-293">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="792c2-293">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="792c2-294">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="792c2-294">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="792c2-295">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="792c2-295">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="792c2-296">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="792c2-296">Receive-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[<span data-ttu-id="792c2-297">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="792c2-297">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

