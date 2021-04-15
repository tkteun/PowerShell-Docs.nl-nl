---
description: Beschrijft hoe u externe opdrachten in PowerShell kunt uitvoeren.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: ad7ccd24c6e9642283e4ea9d1fb04bac40a6b11b
ms.sourcegitcommit: 2b1059dd18ae4ec4f350479185c156748649b4ab
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/14/2021
ms.locfileid: "107390111"
---
# <a name="about-remote"></a><span data-ttu-id="e5c7d-104">Over extern</span><span class="sxs-lookup"><span data-stu-id="e5c7d-104">About Remote</span></span>

## <a name="short-description"></a><span data-ttu-id="e5c7d-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e5c7d-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="e5c7d-106">Beschrijft hoe u externe opdrachten in PowerShell kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-106">Describes how to run remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="e5c7d-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e5c7d-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e5c7d-108">U kunt externe opdrachten uitvoeren op één computer of op meerdere computers met behulp van een tijdelijke of permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-108">You can run remote commands on a single computer or on multiple computers by using a temporary or persistent connection.</span></span> <span data-ttu-id="e5c7d-109">U kunt ook een interactieve sessie starten met één externe computer.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-109">You can also start an interactive session with a single remote computer.</span></span>

<span data-ttu-id="e5c7d-110">In dit onderwerp vindt u een reeks voorbeelden die u laten zien hoe u verschillende typen externe opdrachten kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-110">This topic provides a series of examples to show you how to run different types of remote command.</span></span> <span data-ttu-id="e5c7d-111">Nadat u deze basisopdrachten hebt geprobeerd, leest u de Help-onderwerpen waarin elke cmdlet wordt beschreven die in deze opdrachten wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-111">After you try these basic commands, read the Help topics that describe each cmdlet that is used in these commands.</span></span> <span data-ttu-id="e5c7d-112">In de onderwerpen vindt u de details en wordt uitgelegd hoe u de opdrachten kunt aanpassen aan uw behoeften.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-112">The topics provide the details and explain how you can modify the commands to meet your needs.</span></span>

<span data-ttu-id="e5c7d-113">Opmerking: als u externe toegang van PowerShell wilt gebruiken, moeten de lokale en externe computers zijn geconfigureerd voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-113">Note: To use PowerShell remoting, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="e5c7d-114">Zie voor meer informatie [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5c7d-114">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

## <a name="how-to-start-an-interactive-session-enter-pssession"></a><span data-ttu-id="e5c7d-115">EEN INTERACTIEVE SESSIE STARTEN (ENTER-PSSESSION)</span><span class="sxs-lookup"><span data-stu-id="e5c7d-115">HOW TO START AN INTERACTIVE SESSION (ENTER-PSSESSION)</span></span>

<span data-ttu-id="e5c7d-116">De eenvoudigste manier om externe opdrachten uit te voeren, is door een interactieve sessie te starten met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-116">The easiest way to run remote commands is to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="e5c7d-117">Wanneer de sessie wordt gestart, worden de opdrachten die u typt uitgevoerd op de externe computer, net zoals u ze rechtstreeks op de externe computer hebt getypt.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-117">When the session starts, the commands that you type run on the remote computer, just as though you typed them directly on the remote computer.</span></span> <span data-ttu-id="e5c7d-118">U kunt in elke interactieve sessie verbinding maken met slechts één computer.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-118">You can connect to only one computer in each interactive session.</span></span>

<span data-ttu-id="e5c7d-119">Als u een interactieve sessie wilt starten, gebruikt u Enter-PSSession cmdlet .</span><span class="sxs-lookup"><span data-stu-id="e5c7d-119">To start an interactive session, use the Enter-PSSession cmdlet.</span></span> <span data-ttu-id="e5c7d-120">Met de volgende opdracht start u een interactieve sessie met de computer Server01:</span><span class="sxs-lookup"><span data-stu-id="e5c7d-120">The following command starts an interactive session with the Server01 computer:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="e5c7d-121">De opdrachtprompt wordt gewijzigd om aan te geven dat u bent verbonden met de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-121">The command prompt changes to indicate that you are connected to the Server01 computer.</span></span>

```
Server01\PS>
```

<span data-ttu-id="e5c7d-122">U kunt nu opdrachten typen op de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-122">Now, you can type commands on the Server01 computer.</span></span>

<span data-ttu-id="e5c7d-123">Typ het volgende om de interactieve sessie te beëindigen:</span><span class="sxs-lookup"><span data-stu-id="e5c7d-123">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="e5c7d-124">Zie Enter-PSSession voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-124">For more information, see Enter-PSSession.</span></span>

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a><span data-ttu-id="e5c7d-125">CMDLETS GEBRUIKEN DIE EEN COMPUTERNAME-PARAMETER HEBBEN OM EXTERNE GEGEVENS OP TE HALEN</span><span class="sxs-lookup"><span data-stu-id="e5c7d-125">HOW TO USE CMDLETS THAT HAVE A COMPUTERNAME PARAMETER TO GET REMOTE DATA</span></span>

<span data-ttu-id="e5c7d-126">Verschillende cmdlets hebben een ComputerName parameter waarmee u objecten van externe computers.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-126">Several cmdlets have a ComputerName parameter that lets you get objects from remote computers.</span></span>

<span data-ttu-id="e5c7d-127">Omdat deze cmdlets geen op WS Management gebaseerde PowerShell-remoting gebruiken, kunt u de parameter ComputerName van deze cmdlets gebruiken op elke computer met PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-127">Because these cmdlets do not use WS-Management-based PowerShell remoting, you can use the ComputerName parameter of these cmdlets on any computer that is running PowerShell.</span></span> <span data-ttu-id="e5c7d-128">De computers hoeft niet te worden geconfigureerd voor het op de markt houden van powershell en de computers moeten niet voldoen aan de systeemvereisten voor remoting.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-128">The computers do not have to be configured for PowerShell remoting, and the computers do not have to meet the system requirements for remoting.</span></span>

<span data-ttu-id="e5c7d-129">De volgende cmdlets hebben een ComputerName-parameter:</span><span class="sxs-lookup"><span data-stu-id="e5c7d-129">The following cmdlets have a ComputerName parameter:</span></span>

```
Clear-EventLog    Limit-EventLog
Get-Counter       New-EventLog
Get-EventLog      Remove-EventLog
Get-HotFix        Restart-Computer
Get-Process       Show-EventLog
Get-Service       Stop-Computer
Get-WinEvent      Test-Connection
Get-WmiObject     Write-EventLog
```

<span data-ttu-id="e5c7d-130">Met de volgende opdracht worden bijvoorbeeld de services op de externe server01-computer opgeslagen:</span><span class="sxs-lookup"><span data-stu-id="e5c7d-130">For example, the following command gets the services on the Server01 remote computer:</span></span>

```powershell
Get-Service -ComputerName Server01
```

<span data-ttu-id="e5c7d-131">Cmdlets die ondersteuning bieden voor remoting zonder speciale configuratie hebben doorgaans een **ComputerName-parameter** en hebben geen **sessieparameter.**</span><span class="sxs-lookup"><span data-stu-id="e5c7d-131">Typically, cmdlets that support remoting without special configuration have a **ComputerName** parameter and do not have a **Session** parameter.</span></span> <span data-ttu-id="e5c7d-132">Als u wilt zoeken naar deze cmdlets in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="e5c7d-132">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a><span data-ttu-id="e5c7d-133">EEN EXTERNE OPDRACHT UITVOEREN</span><span class="sxs-lookup"><span data-stu-id="e5c7d-133">HOW TO RUN A REMOTE COMMAND</span></span>

<span data-ttu-id="e5c7d-134">Als u andere opdrachten wilt uitvoeren op externe computers, gebruikt u Invoke-Command cmdlet .</span><span class="sxs-lookup"><span data-stu-id="e5c7d-134">To run other commands on remote computers, use the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="e5c7d-135">Als u één opdracht of een paar niet-gerelateerde opdrachten wilt uitvoeren, gebruikt u de parameter ComputerName van Invoke-Command om de externe computers op te geven.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-135">To run a single command or a few unrelated commands, use the ComputerName parameter of Invoke-Command to specify the remote computers.</span></span> <span data-ttu-id="e5c7d-136">Gebruik de parameter ScriptBlock om de opdracht op te geven.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-136">Use the ScriptBlock parameter to specify the command.</span></span>

<span data-ttu-id="e5c7d-137">Met de volgende opdracht wordt bijvoorbeeld een Get-Culture uitgevoerd op de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-137">For example, the following command runs a Get-Culture command on the Server01 computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="e5c7d-138">De ComputerName parameter is ontworpen voor situaties waarin u één opdracht of een aantal niet-gerelateerde opdrachten op een of meer computers uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-138">The ComputerName parameter is designed for situation in which you run a single command or several unrelated commands on one or many computers.</span></span> <span data-ttu-id="e5c7d-139">Als u een permanente verbinding met een externe computer tot stand wilt brengen, gebruikt u de parameter Sessie.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-139">To establish a persistent connection to a remote computer, use the Session parameter.</span></span>

## <a name="how-to-create-a-persistent-connection-pssession"></a><span data-ttu-id="e5c7d-140">EEN PERMANENTE VERBINDING MAKEN (PSSESSION)</span><span class="sxs-lookup"><span data-stu-id="e5c7d-140">HOW TO CREATE A PERSISTENT CONNECTION (PSSESSION)</span></span>

<span data-ttu-id="e5c7d-141">Wanneer u de parameter ComputerName van de cmdlet Invoke-Command, maakt Windows PowerShell alleen een verbinding voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-141">When you use the ComputerName parameter of the Invoke-Command cmdlet, Windows PowerShell establishes a connection just for the command.</span></span> <span data-ttu-id="e5c7d-142">Vervolgens wordt de verbinding gesloten wanneer de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-142">Then, it closes the connection when the command is complete.</span></span> <span data-ttu-id="e5c7d-143">Variabelen of functies die zijn gedefinieerd in de opdracht gaan verloren.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-143">Any variables or functions that are defined in the command are lost.</span></span>

<span data-ttu-id="e5c7d-144">Als u een permanente verbinding met een externe computer wilt maken, gebruikt u New-PSSession cmdlet .</span><span class="sxs-lookup"><span data-stu-id="e5c7d-144">To create a persistent connection to a remote computer, use the New-PSSession cmdlet.</span></span> <span data-ttu-id="e5c7d-145">Met de volgende opdracht maakt u bijvoorbeeld PSSessions op de computers Server01 en Server02 en slaat u de PSSessions vervolgens op in de $s variabele.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-145">For example, the following command creates PSSessions on the Server01 and Server02 computers and then saves the PSSessions in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="e5c7d-146">OPDRACHTEN UITVOEREN IN EEN PSSESSION</span><span class="sxs-lookup"><span data-stu-id="e5c7d-146">HOW TO RUN COMMANDS IN A PSSESSION</span></span>

<span data-ttu-id="e5c7d-147">Met een PSSession kunt u een reeks externe opdrachten uitvoeren die gegevens delen, zoals functies, aliassen en de waarden van variabelen.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-147">With a PSSession, you can run a series of remote commands that share data, like functions, aliases, and the values of variables.</span></span> <span data-ttu-id="e5c7d-148">Als u opdrachten wilt uitvoeren in een PSSession, gebruikt u de parameter Session van Invoke-Command cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-148">To run commands in a PSSession, use the Session parameter of the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="e5c7d-149">Met de volgende opdracht wordt bijvoorbeeld de cmdlet Invoke-Command gebruikt om een Get-Process-opdracht uit te voeren in de PSSessions op de computers Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-149">For example, the following command uses the Invoke-Command cmdlet to run a Get-Process command in the PSSessions on the Server01 and Server02 computers.</span></span>
<span data-ttu-id="e5c7d-150">De opdracht slaat de processen op in een $p variabele in elke PSSession.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-150">The command saves the processes in a $p variable in each PSSession.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

<span data-ttu-id="e5c7d-151">Omdat de PSSession een permanente verbinding gebruikt, kunt u een andere opdracht uitvoeren in dezelfde PSSession die gebruikmaakt van de $p variabele.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-151">Because the PSSession uses a persistent connection, you can run another command in the same PSSession that uses the $p variable.</span></span> <span data-ttu-id="e5c7d-152">Met de volgende opdracht wordt het aantal processen geteld dat is opgeslagen in $p.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-152">The following command counts the number of processes saved in $p.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a><span data-ttu-id="e5c7d-153">EEN EXTERNE OPDRACHT UITVOEREN OP MEERDERE COMPUTERS</span><span class="sxs-lookup"><span data-stu-id="e5c7d-153">HOW TO RUN A REMOTE COMMAND ON MULTIPLE COMPUTERS</span></span>

<span data-ttu-id="e5c7d-154">Als u een externe opdracht wilt uitvoeren op meerdere computers, typt u alle computernamen in de waarde van de parameter ComputerName van Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-154">To run a remote command on multiple computers, type all of the computer names in the value of the ComputerName parameter of Invoke-Command.</span></span> <span data-ttu-id="e5c7d-155">Scheid de namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-155">Separate the names with commas.</span></span>

<span data-ttu-id="e5c7d-156">Met de volgende opdracht wordt bijvoorbeeld een Get-Culture uitgevoerd op drie computers:</span><span class="sxs-lookup"><span data-stu-id="e5c7d-156">For example, the following command runs a Get-Culture command on three computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="e5c7d-157">U kunt ook een opdracht uitvoeren in meerdere PSSessions.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-157">You can also run a command in multiple PSSessions.</span></span> <span data-ttu-id="e5c7d-158">Met de volgende opdrachten maakt u PSSessions op de computers Server01, Server02 en Server03 en voert u vervolgens een Get-Culture-opdracht uit in elk van de PSSessions.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-158">The following commands create PSSessions on the Server01, Server02, and Server03 computers and then run a Get-Culture command in each of the PSSessions.</span></span>

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="e5c7d-159">Als u de lokale computerlijst met computers wilt opnemen, typt u de naam van de lokale computer, typt u een punt (.) of typt u 'localhost'.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-159">To include the local computer list of computers, type the name of the local computer, type a dot (.), or type  "localhost".</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a><span data-ttu-id="e5c7d-160">EEN SCRIPT UITVOEREN OP EXTERNE COMPUTERS</span><span class="sxs-lookup"><span data-stu-id="e5c7d-160">HOW TO RUN A SCRIPT ON REMOTE COMPUTERS</span></span>

<span data-ttu-id="e5c7d-161">Als u een lokaal script wilt uitvoeren op externe computers, gebruikt u de parameter FilePath van Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-161">To run a local script on remote computers, use the FilePath parameter of Invoke-Command.</span></span>

<span data-ttu-id="e5c7d-162">Met de volgende opdracht wordt bijvoorbeeld het Sample.ps1 uitgevoerd op de S1- en S2-computers:</span><span class="sxs-lookup"><span data-stu-id="e5c7d-162">For example, the following command runs the Sample.ps1 script on the S1 and S2 computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

<span data-ttu-id="e5c7d-163">De resultaten van het script worden geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-163">The results of the script are returned to the local computer.</span></span> <span data-ttu-id="e5c7d-164">U hoeft geen bestanden te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-164">You do not need to copy any files.</span></span>

## <a name="how-to-stop-a-remote-command"></a><span data-ttu-id="e5c7d-165">EEN EXTERNE OPDRACHT STOPPEN</span><span class="sxs-lookup"><span data-stu-id="e5c7d-165">HOW TO STOP A REMOTE COMMAND</span></span>

<span data-ttu-id="e5c7d-166">Als u een opdracht wilt onderbreken, drukt u op CTRL +C.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-166">To interrupt a command, press CTRL+C.</span></span> <span data-ttu-id="e5c7d-167">De interruptaanvraag wordt doorgegeven aan de externe computer waar de externe opdracht wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="e5c7d-167">The interrupt request is passed to the remote computer where it terminates the remote command.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="e5c7d-168">VOOR MEER INFORMATIE</span><span class="sxs-lookup"><span data-stu-id="e5c7d-168">FOR MORE INFORMATION</span></span>

- <span data-ttu-id="e5c7d-169">Zie voor meer informatie over de systeemvereisten voor remoting [about_Remote_Requirements.](about_Remote_Requirements.md)</span><span class="sxs-lookup"><span data-stu-id="e5c7d-169">For information about the system requirements for remoting, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

- <span data-ttu-id="e5c7d-170">Zie voor hulp bij het opmaken van [externe uitvoer about_Remote_Output.](about_Remote_Output.md)</span><span class="sxs-lookup"><span data-stu-id="e5c7d-170">For help in formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

- <span data-ttu-id="e5c7d-171">Zie voor meer informatie over hoe externe toegang werkt, het beheren van externe gegevens, speciale configuraties, beveiligingsproblemen en andere veelgestelde [about_Remote_FAQ.](about_Remote_FAQ.md)</span><span class="sxs-lookup"><span data-stu-id="e5c7d-171">For information about how remoting works, how to manage remote data, special configurations, security issues, and other frequently asked questions, see [about_Remote_FAQ](about_Remote_FAQ.md).</span></span>

- <span data-ttu-id="e5c7d-172">Zie voor hulp bij het oplossen van fouten bij het oplossen [van about_Remote_Troubleshooting.](about_Remote_Troubleshooting.md)</span><span class="sxs-lookup"><span data-stu-id="e5c7d-172">For help in resolving remoting errors, see [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md).</span></span>

- <span data-ttu-id="e5c7d-173">Zie voor meer informatie over PSSessions en permanente verbindingen [about_PSSessions.](about_PSSessions.md)</span><span class="sxs-lookup"><span data-stu-id="e5c7d-173">For information about PSSessions and persistent connections, see [about_PSSessions](about_PSSessions.md).</span></span>

- <span data-ttu-id="e5c7d-174">Zie voor meer informatie over PowerShell-achtergrondtaken [about_Jobs.](about_Jobs.md)</span><span class="sxs-lookup"><span data-stu-id="e5c7d-174">For information about PowerShell background jobs, see [about_Jobs](about_Jobs.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="e5c7d-175">Zoekwoorden</span><span class="sxs-lookup"><span data-stu-id="e5c7d-175">KEYWORDS</span></span>

<span data-ttu-id="e5c7d-176">about_Remoting</span><span class="sxs-lookup"><span data-stu-id="e5c7d-176">about_Remoting</span></span>

## <a name="see-also"></a><span data-ttu-id="e5c7d-177">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="e5c7d-177">SEE ALSO</span></span>

[<span data-ttu-id="e5c7d-178">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="e5c7d-178">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="e5c7d-179">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="e5c7d-179">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="e5c7d-180">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="e5c7d-180">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="e5c7d-181">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="e5c7d-181">about_Remote_FAQ</span></span>](about_Remote_FAQ.md)

[<span data-ttu-id="e5c7d-182">about_Remote_TroubleShooting</span><span class="sxs-lookup"><span data-stu-id="e5c7d-182">about_Remote_TroubleShooting</span></span>](about_Remote_TroubleShooting.md)

[<span data-ttu-id="e5c7d-183">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="e5c7d-183">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="e5c7d-184">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="e5c7d-184">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="e5c7d-185">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="e5c7d-185">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="e5c7d-186">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e5c7d-186">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

