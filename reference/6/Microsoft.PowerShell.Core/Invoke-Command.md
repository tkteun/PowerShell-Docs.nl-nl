---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-opdracht
ms.openlocfilehash: b1c1396d8a29e390ca83d1c42ee43b43442ee83f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251544"
---
# <span data-ttu-id="690f3-103">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="690f3-103">Invoke-Command</span></span>

## <span data-ttu-id="690f3-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="690f3-104">SYNOPSIS</span></span>
<span data-ttu-id="690f3-105">Voert opdrachten uit op lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="690f3-105">Runs commands on local and remote computers.</span></span>

## <span data-ttu-id="690f3-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="690f3-106">SYNTAX</span></span>

### <span data-ttu-id="690f3-107">Inproces (standaard)</span><span class="sxs-lookup"><span data-stu-id="690f3-107">InProcess (Default)</span></span>

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="690f3-108">FilePathRunspace</span><span class="sxs-lookup"><span data-stu-id="690f3-108">FilePathRunspace</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="690f3-109">Sessie</span><span class="sxs-lookup"><span data-stu-id="690f3-109">Session</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="690f3-110">ComputerName</span><span class="sxs-lookup"><span data-stu-id="690f3-110">ComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="690f3-111">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="690f3-111">FilePathComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="690f3-112">URI</span><span class="sxs-lookup"><span data-stu-id="690f3-112">Uri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="690f3-113">FilePathUri</span><span class="sxs-lookup"><span data-stu-id="690f3-113">FilePathUri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="690f3-114">VMId</span><span class="sxs-lookup"><span data-stu-id="690f3-114">VMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="690f3-115">VMName</span><span class="sxs-lookup"><span data-stu-id="690f3-115">VMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="690f3-116">FilePathVMId</span><span class="sxs-lookup"><span data-stu-id="690f3-116">FilePathVMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="690f3-117">FilePathVMName</span><span class="sxs-lookup"><span data-stu-id="690f3-117">FilePathVMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="690f3-118">SSHHost</span><span class="sxs-lookup"><span data-stu-id="690f3-118">SSHHost</span></span>

```
Invoke-Command [-Port <Int32>] [-AsJob] [-HideComputerName] -ScriptBlock <ScriptBlock>
 -HostName <String[]> [-UserName <String>] [-KeyFilePath <String>] [-SSHTransport] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-Subsystem <String>] [<CommonParameters>]
```

### <span data-ttu-id="690f3-119">ContainerId</span><span class="sxs-lookup"><span data-stu-id="690f3-119">ContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="690f3-120">FilePathContainerId</span><span class="sxs-lookup"><span data-stu-id="690f3-120">FilePathContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="690f3-121">SSHHostHashParam</span><span class="sxs-lookup"><span data-stu-id="690f3-121">SSHHostHashParam</span></span>

```
Invoke-Command [-AsJob] [-HideComputerName] -ScriptBlock <ScriptBlock> -SSHConnection <Hashtable[]>
 [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="690f3-122">FilePathSSHHost</span><span class="sxs-lookup"><span data-stu-id="690f3-122">FilePathSSHHost</span></span>

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -HostName <String[]>
 [-UserName <String>] [-KeyFilePath <String>] [-SSHTransport] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="690f3-123">FilePathSSHHostHash</span><span class="sxs-lookup"><span data-stu-id="690f3-123">FilePathSSHHostHash</span></span>

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -SSHConnection <Hashtable[]>
 [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="690f3-124">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="690f3-124">DESCRIPTION</span></span>

<span data-ttu-id="690f3-125">De `Invoke-Command` cmdlet voert opdrachten uit op een lokale of externe computer en retourneert alle uitvoer van de opdrachten, met inbegrip van fouten.</span><span class="sxs-lookup"><span data-stu-id="690f3-125">The `Invoke-Command` cmdlet runs commands on a local or remote computer and returns all output from the commands, including errors.</span></span> <span data-ttu-id="690f3-126">Met één `Invoke-Command` opdracht kunt u opdrachten uitvoeren op meerdere computers.</span><span class="sxs-lookup"><span data-stu-id="690f3-126">Using a single `Invoke-Command` command, you can run commands on multiple computers.</span></span>

<span data-ttu-id="690f3-127">Als u één opdracht wilt uitvoeren op een externe computer, gebruikt u de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="690f3-127">To run a single command on a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="690f3-128">Als u een reeks gerelateerde opdrachten wilt uitvoeren die gegevens delen, gebruikt u de `New-PSSession` cmdlet om een **PSSession** (een permanente verbinding) te maken op de externe computer en gebruikt u vervolgens de **sessie** parameter van `Invoke-Command` om de opdracht uit te voeren in de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="690f3-128">To run a series of related commands that share data, use the `New-PSSession` cmdlet to create a **PSSession** (a persistent connection) on the remote computer, and then use the **Session** parameter of `Invoke-Command` to run the command in the **PSSession**.</span></span> <span data-ttu-id="690f3-129">Als u een opdracht wilt uitvoeren in een sessie zonder verbinding, gebruikt u de para meter **InDisconnectedSession** .</span><span class="sxs-lookup"><span data-stu-id="690f3-129">To run a command in a disconnected session, use the **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="690f3-130">Als u een opdracht in een achtergrond taak wilt uitvoeren, gebruikt u de para meter **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="690f3-130">To run a command in a background job, use the **AsJob** parameter.</span></span>

<span data-ttu-id="690f3-131">U kunt ook `Invoke-Command` op een lokale computer met een script blok als een opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-131">You can also use `Invoke-Command` on a local computer to a script block as a command.</span></span> <span data-ttu-id="690f3-132">Power Shell voert het script blok onmiddellijk uit in een onderliggend bereik van de huidige scope.</span><span class="sxs-lookup"><span data-stu-id="690f3-132">PowerShell runs the script block immediately in a child scope of the current scope.</span></span>

<span data-ttu-id="690f3-133">`Invoke-Command`Lees [about_Remote](./About/about_Remote.md)voordat u opdrachten uitvoert op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-133">Before using `Invoke-Command` to run commands on a remote computer, read [about_Remote](./About/about_Remote.md).</span></span>

<span data-ttu-id="690f3-134">Vanaf Power shell 6,0 kunt u Secure Shell (SSH) gebruiken om een verbinding te maken met en opdrachten op externe computers aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="690f3-134">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to and invoke commands on remote computers.</span></span> <span data-ttu-id="690f3-135">SSH moet worden geïnstalleerd op de lokale computer en de externe computer moet worden geconfigureerd met een Power shell-SSH-eind punt.</span><span class="sxs-lookup"><span data-stu-id="690f3-135">SSH must be installed on the local computer and the remote computer must be configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="690f3-136">Het voor deel van een op SSH gebaseerde Power shell-externe sessie is dat deze werkt op meerdere platformen (Windows, Linux, macOS).</span><span class="sxs-lookup"><span data-stu-id="690f3-136">The benefit of an SSH based PowerShell remote session is that it works across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="690f3-137">Voor SSH-sessie gebruikt u de para meter **hostname** of **SSHConnection** om de externe computer en de relevante verbindings gegevens op te geven.</span><span class="sxs-lookup"><span data-stu-id="690f3-137">For SSH based session you use the **HostName** or **SSHConnection** parameters to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="690f3-138">Zie voor meer informatie over het instellen van externe toegang tot Power shell [via SSH Power shell](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="690f3-138">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="690f3-139">Sommige code voorbeelden gebruiken splatting om de lengte van de lijn te verkleinen.</span><span class="sxs-lookup"><span data-stu-id="690f3-139">Some code samples use splatting to reduce the line length.</span></span> <span data-ttu-id="690f3-140">Zie [about_Splatting](./About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="690f3-140">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="690f3-141">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="690f3-141">EXAMPLES</span></span>

### <span data-ttu-id="690f3-142">Voor beeld 1: een script uitvoeren op een server</span><span class="sxs-lookup"><span data-stu-id="690f3-142">Example 1: Run a script on a server</span></span>

<span data-ttu-id="690f3-143">In dit voor beeld wordt het `Test.ps1` script op de Server01-computer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-143">This example runs the `Test.ps1` script on the Server01 computer.</span></span>

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

<span data-ttu-id="690f3-144">De **filepath** para meter geeft u een script op dat zich op de lokale computer bevindt.</span><span class="sxs-lookup"><span data-stu-id="690f3-144">The **FilePath** parameter specifies a script that is located on the local computer.</span></span> <span data-ttu-id="690f3-145">Het script wordt uitgevoerd op de externe computer en de resultaten worden geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-145">The script runs on the remote computer and the results are returned to the local computer.</span></span>

### <span data-ttu-id="690f3-146">Voor beeld 2: een opdracht uitvoeren op een externe server</span><span class="sxs-lookup"><span data-stu-id="690f3-146">Example 2: Run a command on a remote server</span></span>

<span data-ttu-id="690f3-147">In dit voor beeld wordt een `Get-Culture` opdracht uitgevoerd op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="690f3-147">This example runs a `Get-Culture` command on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

<span data-ttu-id="690f3-148">De **ComputerName** para meter geeft de naam van de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-148">The **ComputerName** parameter specifies the name of the remote computer.</span></span> <span data-ttu-id="690f3-149">De para meter **Credential** wordt gebruikt om de opdracht uit te voeren in de beveiligings context van Domain01\User01, een gebruiker die gemachtigd is om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-149">The **Credential** parameter is used to run the command in the security context of Domain01\User01, a user who has permission to run commands.</span></span> <span data-ttu-id="690f3-150">De **script Block** para meter geeft u de opdracht op die moet worden uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-150">The **ScriptBlock** parameter specifies the command to be run on the remote computer.</span></span>

<span data-ttu-id="690f3-151">Als antwoord Power shell vraagt het wacht woord en een verificatie methode voor het gebruiker01-account.</span><span class="sxs-lookup"><span data-stu-id="690f3-151">In response, PowerShell requests the password and an authentication method for the User01 account.</span></span>
<span data-ttu-id="690f3-152">Vervolgens wordt de opdracht op de computer Server01 uitgevoerd en wordt het resultaat geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-152">It then runs the command on the Server01 computer and returns the result.</span></span>

### <span data-ttu-id="690f3-153">Voor beeld 3: een opdracht uitvoeren in een permanente verbinding</span><span class="sxs-lookup"><span data-stu-id="690f3-153">Example 3: Run a command in a persistent connection</span></span>

<span data-ttu-id="690f3-154">In dit voor beeld wordt dezelfde `Get-Culture` opdracht uitgevoerd in een sessie, met behulp van een permanente verbinding op de externe computer met de naam Server02.</span><span class="sxs-lookup"><span data-stu-id="690f3-154">This example runs the same `Get-Culture` command in a session, using a persistent connection, on the remote computer named Server02.</span></span>

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="690f3-155">`New-PSSession`Met de cmdlet wordt een sessie gemaakt op de externe computer Server02 en opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-155">The `New-PSSession` cmdlet creates a session on the Server02 remote computer and saves it in the `$s` variable.</span></span> <span data-ttu-id="690f3-156">Normaal gesp roken maakt u alleen een sessie wanneer u een reeks opdrachten op de externe computer uitvoert.</span><span class="sxs-lookup"><span data-stu-id="690f3-156">Typically, you create a session only when you run a series of commands on the remote computer.</span></span>

<span data-ttu-id="690f3-157">`Invoke-Command`Met de cmdlet wordt de `Get-Culture` opdracht uitgevoerd op Server02.</span><span class="sxs-lookup"><span data-stu-id="690f3-157">The `Invoke-Command` cmdlet runs the `Get-Culture` command on Server02.</span></span> <span data-ttu-id="690f3-158">Met de **sessie** parameter wordt de sessie opgegeven die is opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-158">The **Session** parameter specifies the session saved in the `$s` variable.</span></span>

<span data-ttu-id="690f3-159">Als antwoord Power Shell voert de opdracht uit in de sessie op de Server02-computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-159">In response, PowerShell runs the command in the session on the Server02 computer.</span></span>

### <span data-ttu-id="690f3-160">Voor beeld 4: een sessie gebruiken om een reeks opdrachten uit te voeren die gegevens delen</span><span class="sxs-lookup"><span data-stu-id="690f3-160">Example 4: Use a session to run a series of commands that share data</span></span>

<span data-ttu-id="690f3-161">In dit voor beeld worden de gevolgen van **computer naam** en **sessie** parameters van gebruikt `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="690f3-161">This example compares the effects of using **ComputerName** and **Session** parameters of `Invoke-Command`.</span></span> <span data-ttu-id="690f3-162">U ziet hoe u een sessie gebruikt om een reeks opdrachten uit te voeren die dezelfde gegevens delen.</span><span class="sxs-lookup"><span data-stu-id="690f3-162">It shows how to use a session to run a series of commands that share the same data.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -ComputerName Server02 -ScriptBlock {$p.VirtualMemorySize}
$s = New-PSSession -ComputerName Server02
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -Session $s -ScriptBlock {$p.VirtualMemorySize}
```

```Output
17930240
```

<span data-ttu-id="690f3-163">De eerste twee opdrachten gebruiken de para meter **ComputerName** van `Invoke-Command` om opdrachten uit te voeren op de externe computer Server02.</span><span class="sxs-lookup"><span data-stu-id="690f3-163">The first two commands use the **ComputerName** parameter of `Invoke-Command` to run commands on the Server02 remote computer.</span></span> <span data-ttu-id="690f3-164">De eerste opdracht gebruikt de `Get-Process` cmdlet om het Power Shell-proces op de externe computer op te halen en om het in de variabele op te slaan `$p` .</span><span class="sxs-lookup"><span data-stu-id="690f3-164">The first command uses the `Get-Process` cmdlet to get the PowerShell process on the remote computer and to save it in the `$p` variable.</span></span> <span data-ttu-id="690f3-165">Met de tweede opdracht wordt de waarde van de eigenschap **VirtualMemorySize** van het Power Shell-proces opgehaald.</span><span class="sxs-lookup"><span data-stu-id="690f3-165">The second command gets the value of the **VirtualMemorySize** property of the PowerShell process.</span></span>

<span data-ttu-id="690f3-166">Wanneer u de para meter **ComputerName** gebruikt, maakt Power shell een nieuwe sessie om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-166">When you use the **ComputerName** parameter, PowerShell creates a new session to run the command.</span></span>
<span data-ttu-id="690f3-167">De sessie wordt gesloten wanneer de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="690f3-167">The session is closed when the command completes.</span></span> <span data-ttu-id="690f3-168">De `$p` variabele is gemaakt in één verbinding, maar bestaat niet in de verbinding die is gemaakt voor de tweede opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-168">The `$p` variable was created in one connection, but it doesn't exist in the connection created for the second command.</span></span>

<span data-ttu-id="690f3-169">Het probleem wordt opgelost door een permanente sessie te maken op de externe computer en vervolgens beide opdrachten in dezelfde sessie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-169">The problem is solved by creating a persistent session on the remote computer, then running both of the commands in the same session.</span></span>

<span data-ttu-id="690f3-170">Met de `New-PSSession` cmdlet wordt een permanente sessie gemaakt op de computer Server02 en wordt de sessie opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-170">The `New-PSSession` cmdlet creates a persistent session on the computer Server02 and saves the session in the `$s` variable.</span></span> <span data-ttu-id="690f3-171">`Invoke-Command`Op de regels die volgen, wordt de para meter **Session** gebruikt om beide opdrachten in dezelfde sessie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-171">The `Invoke-Command` lines that follow use the **Session** parameter to run both of the commands in the same session.</span></span> <span data-ttu-id="690f3-172">Omdat beide opdrachten in dezelfde sessie worden uitgevoerd, `$p` blijft de waarde actief.</span><span class="sxs-lookup"><span data-stu-id="690f3-172">Since both commands run in the same session, the `$p` value remains active.</span></span>

### <span data-ttu-id="690f3-173">Voor beeld 5: Voer een opdracht in die is opgeslagen in een lokale variabele</span><span class="sxs-lookup"><span data-stu-id="690f3-173">Example 5: Enter a command stored in a local variable</span></span>

<span data-ttu-id="690f3-174">In dit voor beeld ziet u hoe u een opdracht maakt die is opgeslagen als een script blok in een lokale variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-174">This example shows how to create a command that is stored as a script block in a local variable.</span></span>
<span data-ttu-id="690f3-175">Wanneer het script blok wordt opgeslagen in een lokale variabele, kunt u de variabele opgeven als de waarde van de para meter **script Block** .</span><span class="sxs-lookup"><span data-stu-id="690f3-175">When the script block is saved in a local variable, you can specify the variable as the value of the **ScriptBlock** parameter.</span></span>

```powershell
$command = { Get-WinEvent -LogName PowerShellCore/Operational |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

<span data-ttu-id="690f3-176">De `$command` variabele slaat de `Get-WinEvent` opdracht op die is opgemaakt als een script blok.</span><span class="sxs-lookup"><span data-stu-id="690f3-176">The `$command` variable stores the `Get-WinEvent` command that's formatted as a script block.</span></span> <span data-ttu-id="690f3-177">Hiermee `Invoke-Command` wordt de opdracht uitgevoerd die is opgeslagen in `$command` op de externe computers S1 en S2.</span><span class="sxs-lookup"><span data-stu-id="690f3-177">The `Invoke-Command` runs the command stored in `$command` on the S1 and S2 remote computers.</span></span>

### <span data-ttu-id="690f3-178">Voor beeld 6: één opdracht op meerdere computers uitvoeren</span><span class="sxs-lookup"><span data-stu-id="690f3-178">Example 6: Run a single command on several computers</span></span>

<span data-ttu-id="690f3-179">In dit voor beeld ziet u hoe u kunt gebruiken `Invoke-Command` om één opdracht op meerdere computers uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-179">This example demonstrates how to use `Invoke-Command` to run a single command on multiple computers.</span></span>

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-WinEvent -LogName PowerShellCore/Operational }
}
Invoke-Command @parameters
```

<span data-ttu-id="690f3-180">De para meter **ComputerName** bevat een door komma's gescheiden lijst met computer namen.</span><span class="sxs-lookup"><span data-stu-id="690f3-180">The **ComputerName** parameter specifies a comma-separated list of computer names.</span></span> <span data-ttu-id="690f3-181">De lijst met computers bevat de localhost-waarde, die de lokale computer vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="690f3-181">The list of computers includes the localhost value, which represents the local computer.</span></span> <span data-ttu-id="690f3-182">Met de para meter **configuratiepad** wordt een alternatieve sessie configuratie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="690f3-182">The **ConfigurationName** parameter specifies an alternate session configuration.</span></span> <span data-ttu-id="690f3-183">De para meter **script Block** wordt uitgevoerd `Get-WinEvent` om de PowerShellCore/operationele gebeurtenis logboeken van elke computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="690f3-183">The **ScriptBlock** parameter runs `Get-WinEvent` to get the PowerShellCore/Operational event logs from each computer.</span></span>

### <span data-ttu-id="690f3-184">Voor beeld 7: de versie van het hostprogramma op meerdere computers ophalen</span><span class="sxs-lookup"><span data-stu-id="690f3-184">Example 7: Get the version of the host program on multiple computers</span></span>

<span data-ttu-id="690f3-185">In dit voor beeld wordt de versie van het Power shell-host-programma uitgevoerd op 200 externe computers.</span><span class="sxs-lookup"><span data-stu-id="690f3-185">This example gets the version of the PowerShell host program running on 200 remote computers.</span></span>

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

<span data-ttu-id="690f3-186">Omdat er slechts één opdracht wordt uitgevoerd, hoeft u geen permanente verbindingen te maken met elk van de computers.</span><span class="sxs-lookup"><span data-stu-id="690f3-186">Because only one command is run, you don't have to create persistent connections to each of the computers.</span></span> <span data-ttu-id="690f3-187">In plaats daarvan gebruikt de opdracht de para meter **ComputerName** om de computers aan te geven.</span><span class="sxs-lookup"><span data-stu-id="690f3-187">Instead, the command uses the **ComputerName** parameter to indicate the computers.</span></span> <span data-ttu-id="690f3-188">Als u de computers wilt opgeven, wordt de `Get-Content` cmdlet gebruikt om de inhoud van het Machine.txt bestand, een bestand met computer namen, op te halen.</span><span class="sxs-lookup"><span data-stu-id="690f3-188">To specify the computers, it uses the `Get-Content` cmdlet to get the contents of the Machine.txt file, a file of computer names.</span></span>

<span data-ttu-id="690f3-189">`Invoke-Command`Met de cmdlet wordt een `Get-Host` opdracht op de externe computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-189">The `Invoke-Command` cmdlet runs a `Get-Host` command on the remote computers.</span></span> <span data-ttu-id="690f3-190">De teken punt notatie wordt gebruikt om de eigenschap **Version** van de Power shell-host op te halen.</span><span class="sxs-lookup"><span data-stu-id="690f3-190">It uses dot notation to get the **Version** property of the PowerShell host.</span></span>

<span data-ttu-id="690f3-191">Deze opdrachten worden een voor een uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-191">These commands run one at a time.</span></span> <span data-ttu-id="690f3-192">Wanneer de opdrachten zijn voltooid, wordt de uitvoer van de opdrachten van alle computers in de variabele opgeslagen `$version` .</span><span class="sxs-lookup"><span data-stu-id="690f3-192">When the commands complete, the output of the commands from all of the computers is saved in the `$version` variable.</span></span> <span data-ttu-id="690f3-193">De uitvoer bevat de naam van de computer waarvan de gegevens afkomstig zijn.</span><span class="sxs-lookup"><span data-stu-id="690f3-193">The output includes the name of the computer from which the data originated.</span></span>

### <span data-ttu-id="690f3-194">Voor beeld 8: een achtergrond taak op meerdere externe computers uitvoeren</span><span class="sxs-lookup"><span data-stu-id="690f3-194">Example 8: Run a background job on several remote computers</span></span>

<span data-ttu-id="690f3-195">In dit voor beeld wordt een opdracht op twee externe computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-195">This example runs a command on two remote computers.</span></span> <span data-ttu-id="690f3-196">De `Invoke-Command` opdracht maakt gebruik van de para meter **AsJob** , zodat de opdracht als achtergrond taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-196">The `Invoke-Command` command uses the **AsJob** parameter so that the command runs as a background job.</span></span> <span data-ttu-id="690f3-197">De opdrachten worden uitgevoerd op de externe computers, maar de taak bestaat op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-197">The commands run on the remote computers, but the job exists on the local computer.</span></span> <span data-ttu-id="690f3-198">De resultaten worden verzonden naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-198">The results are transmitted to the local computer.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
Invoke-Command -Session $s -ScriptBlock {Get-EventLog system} -AsJob
```

```Output
Id   Name    State      HasMoreData   Location           Command
---  ----    -----      -----         -----------        ---------------
1    Job1    Running    True          Server01,Server02  Get-EventLog system
```

```powershell
$j = Get-Job
$j | Format-List -Property *
```

```Output
HasMoreData   : True
StatusMessage :
Location      : Server01,Server02
Command       : Get-EventLog system
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : e124bb59-8cb2-498b-a0d2-2e07d4e030ca
Id            : 1
Name          : Job1
ChildJobs     : {Job2, Job3}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
$results = $j | Receive-Job
```

<span data-ttu-id="690f3-199">De `New-PSSession` cmdlet maakt sessies op de externe computers Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="690f3-199">The `New-PSSession` cmdlet creates sessions on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="690f3-200">De `Invoke-Command` cmdlet voert een achtergrond taak in elk van de sessies uit.</span><span class="sxs-lookup"><span data-stu-id="690f3-200">The `Invoke-Command` cmdlet runs a background job in each of the sessions.</span></span> <span data-ttu-id="690f3-201">De opdracht gebruikt de para meter **AsJob** om de opdracht als achtergrond taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-201">The command uses the **AsJob** parameter to run the command as a background job.</span></span> <span data-ttu-id="690f3-202">Met deze opdracht wordt een taak object geretourneerd dat twee onderliggende taak objecten bevat, één voor elk van de taken die op de twee externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-202">This command returns a job object that contains two child job objects, one for each of the jobs run on the two remote computers.</span></span>

<span data-ttu-id="690f3-203">De `Get-Job` opdracht slaat het taak object op in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-203">The `Get-Job` command saves the job object in the `$j` variable.</span></span> <span data-ttu-id="690f3-204">De `$j` variabele wordt vervolgens naar de cmdlet geleid `Format-List` om alle eigenschappen van het taak object in een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="690f3-204">The `$j` variable is then piped to the `Format-List` cmdlet to display all properties of the job object in a list.</span></span> <span data-ttu-id="690f3-205">Met de laatste opdracht worden de resultaten van de taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="690f3-205">The last command gets the results of the jobs.</span></span> <span data-ttu-id="690f3-206">Hiermee wordt het taak object in `$j` naar de `Receive-Job` cmdlet sluizen en worden de resultaten opgeslagen in de `$results` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-206">It pipes the job object in `$j` to the `Receive-Job` cmdlet and stores the results in the `$results` variable.</span></span>

### <span data-ttu-id="690f3-207">Voor beeld 9: lokale variabelen insluiten in een opdracht die wordt uitgevoerd op een externe computer</span><span class="sxs-lookup"><span data-stu-id="690f3-207">Example 9: Include local variables in a command run on a remote computer</span></span>

<span data-ttu-id="690f3-208">In dit voor beeld ziet u hoe u de waarden van lokale variabelen opneemt in een opdracht die wordt uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-208">This example shows how to include the values of local variables in a command run on a remote computer.</span></span> <span data-ttu-id="690f3-209">De opdracht gebruikt de `Using` aanpassings functie van het bereik om een lokale variabele in een externe opdracht te identificeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-209">The command uses the `Using` scope modifier to identify a local variable in a remote command.</span></span> <span data-ttu-id="690f3-210">Standaard worden alle variabelen geacht te zijn gedefinieerd in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="690f3-210">By default, all variables are assumed to be defined in the remote session.</span></span> <span data-ttu-id="690f3-211">De `Using` aanpassing van het bereik is geïntroduceerd in Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="690f3-211">The `Using` scope modifier was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="690f3-212">`Using`Zie [about_Remote_Variables](./About/about_Remote_Variables.md) en [about_Scopes](./about/about_scopes.md)voor meer informatie over de aanpassing van het bereik.</span><span class="sxs-lookup"><span data-stu-id="690f3-212">For more information about the `Using` scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md) and [about_Scopes](./about/about_scopes.md).</span></span>

```powershell
$Log = "PowerShellCore/Operational"
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-WinEvent -LogName $Using:Log -MaxEvents 10}
```

<span data-ttu-id="690f3-213">De `$Log` variabele bevat de naam van het gebeurtenis logboek, PowerShellCore/Operation.</span><span class="sxs-lookup"><span data-stu-id="690f3-213">The `$Log` variable stores the name of the event log, PowerShellCore/Operational.</span></span> <span data-ttu-id="690f3-214">De `Invoke-Command` cmdlet wordt uitgevoerd `Get-WinEvent` op Server01 om de tien nieuwste gebeurtenissen uit het gebeurtenis logboek op te halen.</span><span class="sxs-lookup"><span data-stu-id="690f3-214">The `Invoke-Command` cmdlet runs `Get-WinEvent` on Server01 to get the ten newest events from the event log.</span></span> <span data-ttu-id="690f3-215">De waarde van de para meter **LogName** is de `$Log` variabele die wordt voorafgegaan door de `Using` wijzigings functie van het bereik om aan te geven dat deze is gemaakt in de lokale sessie, niet in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="690f3-215">The value of the **LogName** parameter is the `$Log` variable that is prefixed by the `Using` scope modifier to indicate that it was created in the local session, not in the remote session.</span></span>

### <span data-ttu-id="690f3-216">Voor beeld 10: de computer naam verbergen</span><span class="sxs-lookup"><span data-stu-id="690f3-216">Example 10: Hide the computer name</span></span>

<span data-ttu-id="690f3-217">In dit voor beeld ziet u het effect van het gebruik van de para meter **HideComputerName** van `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="690f3-217">This example shows the effect of using the **HideComputerName** parameter of `Invoke-Command`.</span></span>
<span data-ttu-id="690f3-218">**HideComputerName** heeft geen invloed op het object dat met deze cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-218">**HideComputerName** doesn't change the object that this cmdlet returns.</span></span> <span data-ttu-id="690f3-219">Alleen de weer gave wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="690f3-219">It changes only the display.</span></span> <span data-ttu-id="690f3-220">U kunt nog steeds de **Format** -cmdlets gebruiken om de eigenschap **PsComputerName** van de betrokken objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="690f3-220">You can still use the **Format** cmdlets to display the **PsComputerName** property of any of the affected objects.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell}
```

```Output
PSComputerName    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
--------------    -------  ------    -----      ----- -----   ------     --   -----------
S1                575      15        45100      40988   200     4.68     1392 PowerShell
S2                777      14        35100      30988   150     3.68     67   PowerShell
```

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell} -HideComputerName
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
575      15        45100      40988   200     4.68     1392 PowerShell
777      14        35100      30988   150     3.68     67   PowerShell
```

<span data-ttu-id="690f3-221">De eerste twee opdrachten gebruiken `Invoke-Command` om een `Get-Process` opdracht voor het Power Shell-proces uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-221">The first two commands use `Invoke-Command` to run a `Get-Process` command for the PowerShell process.</span></span> <span data-ttu-id="690f3-222">De uitvoer van de eerste opdracht bevat de eigenschap **PsComputerName** , die de naam bevat van de computer waarop de opdracht is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-222">The output of the first command includes the **PsComputerName** property, which contains the name of the computer on which the command ran.</span></span> <span data-ttu-id="690f3-223">De uitvoer van de tweede opdracht, die gebruikmaakt van **HideComputerName** , bevat niet de kolom **PsComputerName** .</span><span class="sxs-lookup"><span data-stu-id="690f3-223">The output of the second command, which uses **HideComputerName** , doesn't include the **PsComputerName** column.</span></span>

### <span data-ttu-id="690f3-224">Voor beeld 11: het sleutel woord param in een script blok gebruiken</span><span class="sxs-lookup"><span data-stu-id="690f3-224">Example 11: Use the Param keyword in a script block</span></span>

<span data-ttu-id="690f3-225">Het `Param` sleutel woord en de para meter **argument List** worden gebruikt om variabele waarden door te geven aan benoemde para meters in een-script blok.</span><span class="sxs-lookup"><span data-stu-id="690f3-225">The `Param` keyword and the **ArgumentList** parameter are used to pass variable values to named parameters in a script block.</span></span> <span data-ttu-id="690f3-226">In dit voor beeld worden bestands namen weer gegeven die beginnen met de letter `a` en de `.pdf` uitbrei ding hebben.</span><span class="sxs-lookup"><span data-stu-id="690f3-226">This example displays filenames that begin with the letter `a` and have the `.pdf` extension.</span></span>

<span data-ttu-id="690f3-227">Zie about_Language_Keywords voor meer informatie over het `Param` tref [about_Language_Keywords](./about/about_language_keywords.md#param)woord.</span><span class="sxs-lookup"><span data-stu-id="690f3-227">For more information about the `Param` keyword, see [about_Language_Keywords](./about/about_language_keywords.md#param).</span></span>

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Param ($param1,$param2) Get-ChildItem -Name $param1 -Include $param2 }
    ArgumentList = "a*", "*.pdf"
}
Invoke-Command @parameters
```

```Output
aa.pdf
ab.pdf
ac.pdf
az.pdf
```

<span data-ttu-id="690f3-228">`Invoke-Command` maakt gebruik van de para meter **script Block** die twee variabelen definieert, `$param1` en `$param2` .</span><span class="sxs-lookup"><span data-stu-id="690f3-228">`Invoke-Command` uses the **ScriptBlock** parameter that defines two variables, `$param1` and `$param2`.</span></span> <span data-ttu-id="690f3-229">`Get-ChildItem` maakt gebruik van de benoemde para meters, **naam** en **bevatten** met de namen van variabelen.</span><span class="sxs-lookup"><span data-stu-id="690f3-229">`Get-ChildItem` uses the named parameters, **Name** and **Include** with the variable names.</span></span> <span data-ttu-id="690f3-230">De **argument List** geeft de waarden door aan de variabelen.</span><span class="sxs-lookup"><span data-stu-id="690f3-230">The **ArgumentList** passes the values to the variables.</span></span>

### <span data-ttu-id="690f3-231">Voor beeld 12: de $args automatische variabele in een script blok gebruiken</span><span class="sxs-lookup"><span data-stu-id="690f3-231">Example 12: Use the $args automatic variable in a script block</span></span>

<span data-ttu-id="690f3-232">De `$args` Automatische variabele en de para meter **argument List** worden gebruikt om matrix waarden door te geven aan parameter posities in een-script blok.</span><span class="sxs-lookup"><span data-stu-id="690f3-232">The `$args` automatic variable and the **ArgumentList** parameter are used to pass array values to parameter positions in a script block.</span></span> <span data-ttu-id="690f3-233">In dit voor beeld wordt de mapinhoud van de server weer gegeven `.txt` .</span><span class="sxs-lookup"><span data-stu-id="690f3-233">This example displays a server's directory contents of `.txt` files.</span></span> <span data-ttu-id="690f3-234">De `Get-ChildItem` para meter **Path** is positie 0 en de **filter** parameter is positie</span><span class="sxs-lookup"><span data-stu-id="690f3-234">The `Get-ChildItem` **Path** parameter is position 0 and the **Filter** parameter is position</span></span>
1.

<span data-ttu-id="690f3-235">Zie about_Automatic_Variables voor meer informatie over de `$args` variabele [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span><span class="sxs-lookup"><span data-stu-id="690f3-235">For more information about the `$args` variable, see [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span></span>

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Get-ChildItem $args[0] $args[1] }
    ArgumentList = "C:\Test", "*.txt*"
}
Invoke-Command @parameters
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/12/2019    15:15            128 alog.txt
-a---           7/27/2019    15:16            256 blog.txt
-a---           9/28/2019    17:10             64 zlog.txt
```

<span data-ttu-id="690f3-236">`Invoke-Command` Hiermee wordt een **script Block** -para meter gebruikt en worden `Get-ChildItem` de-en- `$args[0]` `$args[1]` matrix waarden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="690f3-236">`Invoke-Command` uses a **ScriptBlock** parameter and `Get-ChildItem` specifies the `$args[0]` and `$args[1]` array values.</span></span> <span data-ttu-id="690f3-237">De **argument List** geeft de `$args` matrix waarden door aan de `Get-ChildItem` parameter posities voor **Path** en **filter**.</span><span class="sxs-lookup"><span data-stu-id="690f3-237">The **ArgumentList** passes the `$args` array values to the `Get-ChildItem` parameter positions for **Path** and **Filter**.</span></span>

### <span data-ttu-id="690f3-238">Voor beeld 13: een script uitvoeren op alle computers die worden vermeld in een tekst bestand</span><span class="sxs-lookup"><span data-stu-id="690f3-238">Example 13: Run a script on all the computers listed in a text file</span></span>

<span data-ttu-id="690f3-239">In dit voor beeld wordt de `Invoke-Command` cmdlet gebruikt om het script uit te voeren `Sample.ps1` op alle computers die worden vermeld in het `Servers.txt` bestand.</span><span class="sxs-lookup"><span data-stu-id="690f3-239">This example uses the `Invoke-Command` cmdlet to run the `Sample.ps1` script on all the computers listed in the `Servers.txt` file.</span></span> <span data-ttu-id="690f3-240">De opdracht gebruikt de **filepath** -para meter om het script bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="690f3-240">The command uses the **FilePath** parameter to specify the script file.</span></span> <span data-ttu-id="690f3-241">Met deze opdracht kunt u het script uitvoeren op de externe computers, zelfs als het script bestand niet toegankelijk is voor de externe computers.</span><span class="sxs-lookup"><span data-stu-id="690f3-241">This command lets you run the script on the remote computers, even if the script file isn't accessible to the remote computers.</span></span>

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

<span data-ttu-id="690f3-242">Wanneer u de opdracht verzendt, wordt de inhoud van het `Sample.ps1` bestand gekopieerd naar een script blok en wordt het script blok op elke externe computer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-242">When you submit the command, the content of the `Sample.ps1` file is copied into a script block and the script block is run on each of the remote computers.</span></span> <span data-ttu-id="690f3-243">Deze procedure is gelijk aan het gebruik van de para meter **script Block** om de inhoud van het script te verzenden.</span><span class="sxs-lookup"><span data-stu-id="690f3-243">This procedure is equivalent to using the **ScriptBlock** parameter to submit the contents of the script.</span></span>

### <span data-ttu-id="690f3-244">Voor beeld 14: een opdracht uitvoeren op een externe computer met behulp van een URI</span><span class="sxs-lookup"><span data-stu-id="690f3-244">Example 14: Run a command on a remote computer using a URI</span></span>

<span data-ttu-id="690f3-245">In dit voor beeld ziet u hoe u een opdracht uitvoert op een externe computer die wordt geïdentificeerd door een URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="690f3-245">This example shows how to run a command on a remote computer that's identified by a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="690f3-246">In dit voor beeld wordt een `Set-Mailbox` opdracht uitgevoerd op een externe Exchange-Server.</span><span class="sxs-lookup"><span data-stu-id="690f3-246">This particular example runs a `Set-Mailbox` command on a remote Exchange server.</span></span>

```powershell
$LiveCred = Get-Credential
$parameters = @{
  ConfigurationName = 'Microsoft.Exchange'
  ConnectionUri = 'https://ps.exchangelabs.com/PowerShell'
  Credential = $LiveCred
  Authentication = 'Basic'
  ScriptBlock = {Set-Mailbox Dan -DisplayName "Dan Park"}
}
Invoke-Command @parameters
```

<span data-ttu-id="690f3-247">De eerste regel gebruikt de `Get-Credential` cmdlet voor het opslaan van Windows Live ID-referenties in de `$LiveCred` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-247">The first line uses the `Get-Credential` cmdlet to store Windows Live ID credentials in the `$LiveCred` variable.</span></span> <span data-ttu-id="690f3-248">Power shell vraagt de gebruiker om Windows Live ID-referenties in te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-248">PowerShell prompts the user to enter Windows Live ID credentials.</span></span>

<span data-ttu-id="690f3-249">De `$parameters` variabele is een hash-tabel met de para meters die moeten worden door gegeven aan de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="690f3-249">The `$parameters` variable is a hash table containing the parameters to be passed to the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="690f3-250">`Invoke-Command`Met de cmdlet wordt een `Set-Mailbox` opdracht uitgevoerd met behulp van de **micro soft. Exchange** -sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="690f3-250">The `Invoke-Command` cmdlet runs a `Set-Mailbox` command using the **Microsoft.Exchange** session configuration.</span></span> <span data-ttu-id="690f3-251">De **ConnectionURI** para meter geeft u de URL van het Exchange Server-eind punt.</span><span class="sxs-lookup"><span data-stu-id="690f3-251">The **ConnectionURI** parameter specifies the URL of the Exchange server endpoint.</span></span> <span data-ttu-id="690f3-252">De **referentie** parameter bevat de referenties die zijn opgeslagen in de `$LiveCred` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-252">The **Credential** parameter specifies the credentials stored in the `$LiveCred` variable.</span></span> <span data-ttu-id="690f3-253">De para meter **AuthenticationMechanism** bepaalt het gebruik van basis verificatie.</span><span class="sxs-lookup"><span data-stu-id="690f3-253">The **AuthenticationMechanism** parameter specifies the use of basic authentication.</span></span> <span data-ttu-id="690f3-254">De para meter **script Block** geeft een script blok dat de opdracht bevat.</span><span class="sxs-lookup"><span data-stu-id="690f3-254">The **ScriptBlock** parameter specifies a script block that contains the command.</span></span>

### <span data-ttu-id="690f3-255">Voor beeld 15: een sessie optie gebruiken</span><span class="sxs-lookup"><span data-stu-id="690f3-255">Example 15: Use a session option</span></span>

<span data-ttu-id="690f3-256">In dit voor beeld ziet u hoe u een **SessionOption** -para meter maakt en gebruikt.</span><span class="sxs-lookup"><span data-stu-id="690f3-256">This example shows how to create and use a **SessionOption** parameter.</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

<span data-ttu-id="690f3-257">De `New-PSSessionOption` cmdlet maakt een sessie optie object dat ervoor zorgt dat het externe einde de certificerings instantie, canonieke naam en intrekkings lijsten niet verifieert tijdens het evalueren van de binnenkomende https-verbinding.</span><span class="sxs-lookup"><span data-stu-id="690f3-257">The `New-PSSessionOption` cmdlet creates a session option object that causes the remote end not to verify the Certificate Authority, Canonical Name, and Revocation Lists while evaluating the incoming HTTPS connection.</span></span> <span data-ttu-id="690f3-258">Het **SessionOption** -object wordt opgeslagen in de `$so` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-258">The **SessionOption** object is saved in the `$so` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="690f3-259">Het uitschakelen van deze controles is handig voor het oplossen van problemen, maar is uiteraard niet veilig.</span><span class="sxs-lookup"><span data-stu-id="690f3-259">Disabling these checks is convenient for troubleshooting, but obviously not secure.</span></span>

<span data-ttu-id="690f3-260">Met de `Invoke-Command` cmdlet wordt `Get-HotFix` op afstand een opdracht uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-260">The `Invoke-Command` cmdlet runs a `Get-HotFix` command remotely.</span></span> <span data-ttu-id="690f3-261">De **SessionOption** -para meter krijgt de `$so` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-261">The **SessionOption** parameter is given the `$so` variable.</span></span>

### <span data-ttu-id="690f3-262">Voor beeld 16: URI-omleiding beheren in een externe opdracht</span><span class="sxs-lookup"><span data-stu-id="690f3-262">Example 16: Manage URI redirection in a remote command</span></span>

<span data-ttu-id="690f3-263">In dit voor beeld ziet u hoe u de para meters **AllowRedirection** en **SessionOption** gebruikt voor het beheren van URI-omleiding in een externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-263">This example shows how to use the **AllowRedirection** and **SessionOption** parameters to manage URI redirection in a remote command.</span></span>

```powershell
$max = New-PSSessionOption -MaximumRedirection 1
$parameters = @{
  ConnectionUri = "https://ps.exchangelabs.com/PowerShell"
  ScriptBlock = { Get-Mailbox dan }
  AllowRedirection = $true
  SessionOption = $max
}
Invoke-Command @parameters
```

<span data-ttu-id="690f3-264">`New-PSSessionOption`Met de cmdlet maakt u een **PSSessionOption** -object dat is opgeslagen in de `$max` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-264">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object that is saved in the `$max` variable.</span></span> <span data-ttu-id="690f3-265">De opdracht gebruikt de para meter **MaximumRedirection** om de eigenschap **MaximumConnectionRedirectionCount** van het object **PSSessionOption** in te stellen op 1.</span><span class="sxs-lookup"><span data-stu-id="690f3-265">The command uses the **MaximumRedirection** parameter to set the **MaximumConnectionRedirectionCount** property of the **PSSessionOption** object to 1.</span></span>

<span data-ttu-id="690f3-266">`Invoke-Command`Met de cmdlet wordt een `Get-Mailbox` opdracht uitgevoerd op een externe micro soft Exchange-Server.</span><span class="sxs-lookup"><span data-stu-id="690f3-266">The `Invoke-Command` cmdlet runs a `Get-Mailbox` command on a remote Microsoft Exchange Server.</span></span> <span data-ttu-id="690f3-267">De para meter **AllowRedirection** biedt expliciete machtigingen voor het omleiden van de verbinding met een ander eind punt.</span><span class="sxs-lookup"><span data-stu-id="690f3-267">The **AllowRedirection** parameter provides explicit permission to redirect the connection to an alternate endpoint.</span></span> <span data-ttu-id="690f3-268">De para meter **SessionOption** maakt gebruik van het sessie object dat is opgeslagen in de `$max` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-268">The **SessionOption** parameter uses the session object stored in the `$max` variable.</span></span>

<span data-ttu-id="690f3-269">Als de externe computer die wordt opgegeven door **ConnectionURI** een omleidings bericht retourneert, wordt de verbinding door Power shell omgeleid, maar als de nieuwe bestemming een andere omleidings bericht retourneert, wordt de waarde van het aantal omleidingen van 1 overschreden en `Invoke-Command` wordt een niet-afsluit fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-269">As a result, if the remote computer specified by **ConnectionURI** returns a redirection message, PowerShell redirects the connection, but if the new destination returns another redirection message, the redirection count value of 1 is exceeded, and `Invoke-Command` returns a non-terminating error.</span></span>

### <span data-ttu-id="690f3-270">Voor beeld 17: toegang tot een netwerk share in een externe sessie</span><span class="sxs-lookup"><span data-stu-id="690f3-270">Example 17: Access a network share in a remote session</span></span>

<span data-ttu-id="690f3-271">In dit voor beeld ziet u hoe u een netwerk share opent vanuit een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="690f3-271">This example shows how to access a network share from a remote session.</span></span> <span data-ttu-id="690f3-272">Er worden drie computers gebruikt om het voor beeld te demonstreren.</span><span class="sxs-lookup"><span data-stu-id="690f3-272">Three computers are used to demonstrate the example.</span></span> <span data-ttu-id="690f3-273">Server01 is de lokale computer, Server02 is de externe computer en Net03 bevat de netwerk share.</span><span class="sxs-lookup"><span data-stu-id="690f3-273">Server01 is the local computer, Server02 is the remote computer, and Net03 contains the network share.</span></span> <span data-ttu-id="690f3-274">Server01 maakt verbinding met Server02 en vervolgens wordt Server02 een tweede hop naar Net03 om toegang te krijgen tot de netwerk share.</span><span class="sxs-lookup"><span data-stu-id="690f3-274">Server01 connects to Server02, and then Server02 does a second hop to Net03 to access the network share.</span></span> <span data-ttu-id="690f3-275">Zie [de tweede hop in Power shell Remoting maken](/powershell/scripting/learn/remoting/ps-remoting-second-hop)voor meer informatie over de manier waarop externe communicatie tussen computers door Power shell wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="690f3-275">For more information about how PowerShell Remoting supports hops between computers, see [Making the second hop in PowerShell Remoting](/powershell/scripting/learn/remoting/ps-remoting-second-hop).</span></span>

<span data-ttu-id="690f3-276">De vereiste CredSSP-overdracht (Credential Security Support Provider) is ingeschakeld in de client instellingen op de lokale computer en in de service-instellingen op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-276">The required Credential Security Support Provider (CredSSP) delegation is enabled in the client settings on the local computer, and in the service settings on the remote computer.</span></span> <span data-ttu-id="690f3-277">Als u de opdrachten in dit voor beeld wilt uitvoeren, moet u lid zijn van de groep **Administrators** op de lokale computer en de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-277">To run the commands in this example, you must be a member of the **Administrators** group on the local computer and the remote computer.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer Server02
$s = New-PSSession Server02
Invoke-Command -Session $s -ScriptBlock {Enable-WSManCredSSP -Role Server -Force}
$parameters = @{
  Session = $s
  ScriptBlock = { Get-Item \\Net03\Scripts\LogFiles.ps1 }
  Authentication = "CredSSP"
  Credential = "Domain01\Admin01"
}
Invoke-Command @parameters
```

<span data-ttu-id="690f3-278">`Enable-WSManCredSSP`Met de cmdlet wordt CredSSP delegering van de lokale Server01-computer naar de externe computer van Server02 ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="690f3-278">The `Enable-WSManCredSSP` cmdlet enables CredSSP delegation from the Server01 local computer to the Server02 remote computer.</span></span> <span data-ttu-id="690f3-279">De para meter **Role** specificeert de **client** voor het configureren van de CredSSP client-instelling op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-279">The **Role** parameter specifies **Client** to configure the CredSSP client setting on the local computer.</span></span>

<span data-ttu-id="690f3-280">`New-PSSession` Hiermee maakt u een **PSSession** -object voor Server02 en slaat u het object op in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-280">`New-PSSession` creates a **PSSession** object for Server02 and stores the object in the `$s` variable.</span></span>

<span data-ttu-id="690f3-281">De `Invoke-Command` cmdlet gebruikt de `$s` variabele om verbinding te maken met de externe computer, Server02.</span><span class="sxs-lookup"><span data-stu-id="690f3-281">The `Invoke-Command` cmdlet uses the `$s` variable to connect to the remote computer, Server02.</span></span> <span data-ttu-id="690f3-282">De para meter **script Block** wordt uitgevoerd `Enable-WSManCredSSP` op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-282">The **ScriptBlock** parameter runs `Enable-WSManCredSSP` on the remote computer.</span></span> <span data-ttu-id="690f3-283">De para meter **Role** specificeert de **Server** voor het configureren van de CredSSP-server instelling op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-283">The **Role** parameter specifies **Server** to configure the CredSSP server setting on the remote computer.</span></span>

<span data-ttu-id="690f3-284">De `$parameters` variabele bevat de parameter waarden om verbinding te maken met de netwerk share.</span><span class="sxs-lookup"><span data-stu-id="690f3-284">The `$parameters` variable contains the parameter values to connect to the network share.</span></span> <span data-ttu-id="690f3-285">De `Invoke-Command` cmdlet voert een `Get-Item` opdracht in de sessie in uit `$s` .</span><span class="sxs-lookup"><span data-stu-id="690f3-285">The `Invoke-Command` cmdlet runs a `Get-Item` command in the session in `$s`.</span></span> <span data-ttu-id="690f3-286">Met deze opdracht wordt een script opgehaald van de `\\Net03\Scripts` netwerk share.</span><span class="sxs-lookup"><span data-stu-id="690f3-286">This command gets a script from the `\\Net03\Scripts` network share.</span></span> <span data-ttu-id="690f3-287">De opdracht gebruikt de **verificatie** parameter met de waarde **CredSSP** en de para meter **Credential** met de waarde **Domain01\Admin01**.</span><span class="sxs-lookup"><span data-stu-id="690f3-287">The command uses the **Authentication** parameter with a value of **CredSSP** and the **Credential** parameter with a value of **Domain01\Admin01**.</span></span>

### <span data-ttu-id="690f3-288">Voor beeld 18: scripts op veel externe computers starten</span><span class="sxs-lookup"><span data-stu-id="690f3-288">Example 18: Start scripts on many remote computers</span></span>

<span data-ttu-id="690f3-289">In dit voor beeld wordt een script uitgevoerd op meer dan honderd computers.</span><span class="sxs-lookup"><span data-stu-id="690f3-289">This example runs a script on more than a hundred computers.</span></span> <span data-ttu-id="690f3-290">Om de impact op de lokale computer tot een minimum te beperken, wordt er verbinding gemaakt met elke computer, wordt het script gestart en wordt de verbinding met elke computer verbroken.</span><span class="sxs-lookup"><span data-stu-id="690f3-290">To minimize the impact on the local computer, it connects to each computer, starts the script, and then disconnects from each computer.</span></span>
<span data-ttu-id="690f3-291">Het script wordt nog steeds uitgevoerd in de verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="690f3-291">The script continues to run in the disconnected sessions.</span></span>

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

<span data-ttu-id="690f3-292">De opdracht wordt gebruikt `Invoke-Command` om het script uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-292">The command uses `Invoke-Command` to run the script.</span></span> <span data-ttu-id="690f3-293">De waarde van de para meter **ComputerName** is een `Get-Content` opdracht waarmee de namen van de externe computers uit een tekst bestand worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="690f3-293">The value of the **ComputerName** parameter is a `Get-Content` command that gets the names of the remote computers from a text file.</span></span> <span data-ttu-id="690f3-294">De **InDisconnectedSession** para meter verbreekt de verbinding van de sessies zodra de opdracht wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="690f3-294">The **InDisconnectedSession** parameter disconnects the sessions as soon as it starts the command.</span></span> <span data-ttu-id="690f3-295">De waarde van de **filepath** para meter is het script dat `Invoke-Command` op elke computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-295">The value of the **FilePath** parameter is the script that `Invoke-Command` runs on each computer.</span></span>

<span data-ttu-id="690f3-296">De waarde van **SessionOption** is een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="690f3-296">The value of **SessionOption** is a hash table.</span></span> <span data-ttu-id="690f3-297">De **OutputBufferingMode** -waarde is ingesteld op **Drop** en de waarde **IdleTimeout** is ingesteld op **43200000** milliseconden (12 uur).</span><span class="sxs-lookup"><span data-stu-id="690f3-297">The **OutputBufferingMode** value is set to **Drop** and the **IdleTimeout** value is set to **43200000** milliseconds (12 hours).</span></span>

<span data-ttu-id="690f3-298">Gebruik de cmdlet om de resultaten op te halen van opdrachten en scripts die worden uitgevoerd in verbroken sessies `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="690f3-298">To get the results of commands and scripts that run in disconnected sessions, use the `Receive-PSSession` cmdlet.</span></span>

### <span data-ttu-id="690f3-299">Voor beeld 19: een opdracht uitvoeren op een externe computer via SSH</span><span class="sxs-lookup"><span data-stu-id="690f3-299">Example 19: Run a command on a remote computer using SSH</span></span>

<span data-ttu-id="690f3-300">In dit voor beeld ziet u hoe u een opdracht op een externe computer uitvoert met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="690f3-300">This example shows how to run a command on a remote computer using Secure Shell (SSH).</span></span> <span data-ttu-id="690f3-301">Als SSH op de externe computer is geconfigureerd om te vragen om wacht woorden, wordt u gevraagd een wacht woord op te geven.</span><span class="sxs-lookup"><span data-stu-id="690f3-301">If SSH is configured on the remote computer to prompt for passwords, then you'll get a password prompt.</span></span>
<span data-ttu-id="690f3-302">Anders moet u op SSH-sleutel gebaseerde gebruikers verificatie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="690f3-302">Otherwise, you'll have to use SSH key-based user authentication.</span></span>

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * }
```

### <span data-ttu-id="690f3-303">Voor beeld 20: een opdracht uitvoeren op een externe computer met SSH en een gebruikers verificatie sleutel opgeven</span><span class="sxs-lookup"><span data-stu-id="690f3-303">Example 20: Run a command on a remote computer using SSH and specify a user authentication key</span></span>

<span data-ttu-id="690f3-304">In dit voor beeld ziet u hoe u een opdracht op een externe computer uitvoert met SSH en een sleutel bestand opgeeft voor gebruikers verificatie.</span><span class="sxs-lookup"><span data-stu-id="690f3-304">This example shows how to run a command on a remote computer using SSH and specifying a key file for user authentication.</span></span> <span data-ttu-id="690f3-305">U wordt niet gevraagd om een wacht woord tenzij de sleutel verificatie mislukt en de externe computer zo is geconfigureerd dat basis wachtwoord verificatie is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="690f3-305">You won't be prompted for a password unless the key authentication fails and the remote computer is configured to allow basic password authentication.</span></span>

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * } -KeyFilePath /UserA/UserAKey_rsa
```

### <span data-ttu-id="690f3-306">Voor beeld 21: een script bestand op meerdere externe computers uitvoeren met SSH als een taak</span><span class="sxs-lookup"><span data-stu-id="690f3-306">Example 21: Run a script file on multiple remote computers using SSH as a job</span></span>

<span data-ttu-id="690f3-307">In dit voor beeld ziet u hoe u een script bestand op meerdere externe computers kunt uitvoeren met behulp van SSH en de para meter **SSHConnection** .</span><span class="sxs-lookup"><span data-stu-id="690f3-307">This example shows how to run a script file on multiple remote computers using SSH and the **SSHConnection** parameter set.</span></span> <span data-ttu-id="690f3-308">De para meter **SSHConnection** gebruikt een matrix van hash-tabellen die verbindings gegevens voor elke computer bevatten.</span><span class="sxs-lookup"><span data-stu-id="690f3-308">The **SSHConnection** parameter takes an array of hash tables that contain connection information for each computer.</span></span> <span data-ttu-id="690f3-309">Dit voor beeld vereist dat de doel-externe computers SSH hebben geconfigureerd ter ondersteuning van de verificatie op basis van sleutel-gebruikers.</span><span class="sxs-lookup"><span data-stu-id="690f3-309">This example requires that the target remote computers have SSH configured to support key-based user authentication.</span></span>

```powershell
$sshConnections =
@{ HostName="WinServer1"; UserName="Domain\UserA"; KeyFilePath="C:\Users\UserA\id_rsa" },
@{ HostName="UserB@LinuxServer5"; KeyFilePath="/Users/UserB/id_rsa" }
$results = Invoke-Command -FilePath c:\Scripts\CollectEvents.ps1 -SSHConnection $sshConnections
```

## <span data-ttu-id="690f3-310">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="690f3-310">PARAMETERS</span></span>

### <span data-ttu-id="690f3-311">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="690f3-311">-AllowRedirection</span></span>

<span data-ttu-id="690f3-312">Hiermee kan de verbinding worden omgeleid naar een alternatieve URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="690f3-312">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="690f3-313">Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="690f3-313">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="690f3-314">Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding door te sturen.</span><span class="sxs-lookup"><span data-stu-id="690f3-314">By default, PowerShell doesn't redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="690f3-315">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="690f3-315">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="690f3-316">Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de `$PSSessionOption` Voorkeurs variabele in.</span><span class="sxs-lookup"><span data-stu-id="690f3-316">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="690f3-317">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="690f3-317">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-318">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="690f3-318">-ApplicationName</span></span>

<span data-ttu-id="690f3-319">Hiermee geeft u het segment van de toepassings naam van de verbindings-URI op.</span><span class="sxs-lookup"><span data-stu-id="690f3-319">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="690f3-320">Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de para meter **ConnectionURI** niet in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="690f3-320">Use this parameter to specify the application name when you aren't using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="690f3-321">De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-321">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="690f3-322">Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN.</span><span class="sxs-lookup"><span data-stu-id="690f3-322">If this preference variable isn't defined, the default value is WSMAN.</span></span> <span data-ttu-id="690f3-323">Deze waarde is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="690f3-323">This value is appropriate for most uses.</span></span> <span data-ttu-id="690f3-324">Zie [about_Preference_Variables](./About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="690f3-324">For more information, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="690f3-325">De WinRM-service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="690f3-325">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="690f3-326">De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-326">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-327">-Argument List</span><span class="sxs-lookup"><span data-stu-id="690f3-327">-ArgumentList</span></span>

<span data-ttu-id="690f3-328">Levert de waarden van lokale variabelen in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-328">Supplies the values of local variables in the command.</span></span> <span data-ttu-id="690f3-329">De variabelen in de opdracht worden vervangen door deze waarden voordat de opdracht wordt uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-329">The variables in the command are replaced by these values before the command is run on the remote computer.</span></span> <span data-ttu-id="690f3-330">Voer de waarden in een door komma's gescheiden lijst in.</span><span class="sxs-lookup"><span data-stu-id="690f3-330">Enter the values in a comma-separated list.</span></span> <span data-ttu-id="690f3-331">Waarden worden aan variabelen gekoppeld in de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="690f3-331">Values are associated with variables in the order that they're listed.</span></span> <span data-ttu-id="690f3-332">De alias voor **argument List** is args.</span><span class="sxs-lookup"><span data-stu-id="690f3-332">The alias for **ArgumentList** is Args.</span></span>

<span data-ttu-id="690f3-333">De waarden in de para meter **argument List** kunnen werkelijke waarden zijn, zoals 1024, of ze kunnen verwijzingen zijn naar lokale variabelen, zoals `$max` .</span><span class="sxs-lookup"><span data-stu-id="690f3-333">The values in the **ArgumentList** parameter can be actual values, such as 1024, or they can be references to local variables, such as `$max`.</span></span>

<span data-ttu-id="690f3-334">Als u lokale variabelen wilt gebruiken in een opdracht, gebruikt u de volgende opdracht indeling:</span><span class="sxs-lookup"><span data-stu-id="690f3-334">To use local variables in a command, use the following command format:</span></span>

<span data-ttu-id="690f3-335">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` of `<local-variable>`</span><span class="sxs-lookup"><span data-stu-id="690f3-335">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` -or- `<local-variable>`</span></span>

<span data-ttu-id="690f3-336">Het sleutel woord **param** bevat de lokale variabelen die worden gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-336">The **param** keyword lists the local variables that are used in the command.</span></span> <span data-ttu-id="690f3-337">**Argument List** levert de waarden van de variabelen in de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="690f3-337">**ArgumentList** supplies the values of the variables, in the order that they're listed.</span></span> <span data-ttu-id="690f3-338">Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="690f3-338">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-339">-AsJob</span><span class="sxs-lookup"><span data-stu-id="690f3-339">-AsJob</span></span>

<span data-ttu-id="690f3-340">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-340">Indicates that this cmdlet runs the command as a background job on a remote computer.</span></span> <span data-ttu-id="690f3-341">Gebruik deze para meter om opdrachten uit te voeren die veel tijd in beslag nemen.</span><span class="sxs-lookup"><span data-stu-id="690f3-341">Use this parameter to run commands that take an extensive time to finish.</span></span>

<span data-ttu-id="690f3-342">Wanneer u de para meter **AsJob** gebruikt, retourneert de opdracht een object dat de taak vertegenwoordigt, waarna de opdracht prompt wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="690f3-342">When you use the **AsJob** parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span> <span data-ttu-id="690f3-343">U kunt in de sessie blijven werken terwijl de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="690f3-343">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="690f3-344">Als u de taak wilt beheren, gebruikt u de- `*-Job` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="690f3-344">To manage the job, use the `*-Job` cmdlets.</span></span> <span data-ttu-id="690f3-345">Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="690f3-345">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="690f3-346">De para meter **AsJob** lijkt op het gebruik van de `Invoke-Command` cmdlet om een `Start-Job` cmdlet op afstand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-346">The **AsJob** parameter resembles using the `Invoke-Command` cmdlet to run a `Start-Job` cmdlet remotely.</span></span> <span data-ttu-id="690f3-347">Met **AsJob** wordt de taak echter gemaakt op de lokale computer, zelfs als de taak wordt uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-347">However, with **AsJob** , the job is created on the local computer, even though the job runs on a remote computer.</span></span> <span data-ttu-id="690f3-348">De resultaten van de externe taak worden automatisch geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-348">The results of the remote job are automatically returned to the local computer.</span></span>

<span data-ttu-id="690f3-349">Zie [about_Jobs](About/about_Jobs.md) en [about_Remote_Jobs](About/about_Remote_Jobs.md)voor meer informatie over Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="690f3-349">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-350">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="690f3-350">-Authentication</span></span>

<span data-ttu-id="690f3-351">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="690f3-351">Specifies the mechanism that's used to authenticate the user's credentials.</span></span> <span data-ttu-id="690f3-352">CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="690f3-352">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="690f3-353">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="690f3-353">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="690f3-354">Standaard</span><span class="sxs-lookup"><span data-stu-id="690f3-354">Default</span></span>
- <span data-ttu-id="690f3-355">Basic</span><span class="sxs-lookup"><span data-stu-id="690f3-355">Basic</span></span>
- <span data-ttu-id="690f3-356">CredSSP</span><span class="sxs-lookup"><span data-stu-id="690f3-356">Credssp</span></span>
- <span data-ttu-id="690f3-357">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="690f3-357">Digest</span></span>
- <span data-ttu-id="690f3-358">Kerberos</span><span class="sxs-lookup"><span data-stu-id="690f3-358">Kerberos</span></span>
- <span data-ttu-id="690f3-359">Negotiate</span><span class="sxs-lookup"><span data-stu-id="690f3-359">Negotiate</span></span>
- <span data-ttu-id="690f3-360">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="690f3-360">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="690f3-361">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="690f3-361">The default value is Default.</span></span>

<span data-ttu-id="690f3-362">Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="690f3-362">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="690f3-363">De verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="690f3-363">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="690f3-364">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="690f3-364">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="690f3-365">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="690f3-365">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span> <span data-ttu-id="690f3-366">Zie [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="690f3-366">For more information, see [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:
Accepted values: Basic, Default, Credssp, Digest, Kerberos, Negotiate, NegotiateWithImplicitCredential

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-367">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="690f3-367">-CertificateThumbprint</span></span>

<span data-ttu-id="690f3-368">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="690f3-368">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="690f3-369">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="690f3-369">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="690f3-370">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="690f3-370">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="690f3-371">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts en ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="690f3-371">They can be mapped only to local user accounts and they don't work with domain accounts.</span></span>

<span data-ttu-id="690f3-372">Als u een certificaat vingerafdruk wilt ophalen, gebruikt u een `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="690f3-372">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-373">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="690f3-373">-ComputerName</span></span>

<span data-ttu-id="690f3-374">Hiermee geeft u de computers waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-374">Specifies the computers on which the command runs.</span></span> <span data-ttu-id="690f3-375">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-375">The default is the local computer.</span></span>

<span data-ttu-id="690f3-376">Wanneer u de para meter **ComputerName** gebruikt, maakt Power shell een tijdelijke verbinding die alleen wordt gebruikt om de opgegeven opdracht uit te voeren en vervolgens gesloten.</span><span class="sxs-lookup"><span data-stu-id="690f3-376">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that's used only to run the specified command and is then closed.</span></span> <span data-ttu-id="690f3-377">Als u een permanente verbinding nodig hebt, gebruikt u de para meter **Session** .</span><span class="sxs-lookup"><span data-stu-id="690f3-377">If you need a persistent connection, use the **Session** parameter.</span></span>

<span data-ttu-id="690f3-378">Typ de NETBIOS-naam, het IP-adres of de Fully Qualified Domain Name van een of meer computers in een lijst met door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="690f3-378">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="690f3-379">Typ de computer naam, localhost of een punt () om de lokale computer op te geven `.` .</span><span class="sxs-lookup"><span data-stu-id="690f3-379">To specify the local computer, type the computer name, localhost, or a dot (`.`).</span></span>

<span data-ttu-id="690f3-380">Als u een IP-adres in de waarde **computer naam** wilt gebruiken, moet de opdracht de para meter **Credential** bevatten.</span><span class="sxs-lookup"><span data-stu-id="690f3-380">To use an IP address in the value of **ComputerName** , the command must include the **Credential** parameter.</span></span> <span data-ttu-id="690f3-381">De computer moet zijn geconfigureerd voor het HTTPS-Trans Port of het IP-adres van de externe computer moet zijn opgenomen in de lijst met WinRM **TrustedHosts** van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-381">The computer must be configured for the HTTPS transport or the IP address of the remote computer must be included in the local computer's WinRM **TrustedHosts** list.</span></span> <span data-ttu-id="690f3-382">Zie [een computer toevoegen aan de lijst met vertrouwde hosts](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list)voor instructies om een computer naam toe te voegen aan de lijst met **TrustedHosts** .</span><span class="sxs-lookup"><span data-stu-id="690f3-382">For instructions to add a computer name to the **TrustedHosts** list, see [How to Add a Computer to the Trusted Host List](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list).</span></span>

<span data-ttu-id="690f3-383">In Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell uitvoeren met de optie **als administrator uitvoeren** om de lokale computer op te vragen met de waarde **computer naam**.</span><span class="sxs-lookup"><span data-stu-id="690f3-383">On Windows Vista and later versions of the Windows operating system, to include the local computer in the value of **ComputerName** , you must run PowerShell using the **Run as administrator** option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-384">-Configuratiepad</span><span class="sxs-lookup"><span data-stu-id="690f3-384">-ConfigurationName</span></span>

<span data-ttu-id="690f3-385">Hiermee geeft u de sessie configuratie op die wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="690f3-385">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="690f3-386">Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="690f3-386">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="690f3-387">Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="690f3-387">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="690f3-388">Als deze para meter wordt gebruikt in combi natie met SSH, geeft u het subsysteem op dat moet worden gebruikt voor het doel zoals gedefinieerd in `sshd_config` .</span><span class="sxs-lookup"><span data-stu-id="690f3-388">When used with SSH, this parameter specifies the subsystem to use on the target as defined in `sshd_config`.</span></span> <span data-ttu-id="690f3-389">De standaard waarde voor SSH is het `powershell` subsysteem.</span><span class="sxs-lookup"><span data-stu-id="690f3-389">The default value for SSH is the `powershell` subsystem.</span></span>

<span data-ttu-id="690f3-390">De sessie configuratie voor een sessie bevindt zich op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-390">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="690f3-391">Als de opgegeven sessie configuratie niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-391">If the specified session configuration doesn't exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="690f3-392">De standaard waarde is de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-392">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="690f3-393">Als deze voorkeurs variabele niet is ingesteld, is de standaard instelling **micro soft. Power shell**.</span><span class="sxs-lookup"><span data-stu-id="690f3-393">If this preference variable isn't set, the default is **Microsoft.PowerShell**.</span></span> <span data-ttu-id="690f3-394">Zie [about_Preference_Variables](about/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="690f3-394">For more information, see [about_Preference_Variables](about/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-395">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="690f3-395">-ConnectionUri</span></span>

<span data-ttu-id="690f3-396">Hiermee geeft u een URI (Uniform Resource Identifier) op die het verbindings eindpunt van de sessie definieert.</span><span class="sxs-lookup"><span data-stu-id="690f3-396">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint of the session.</span></span>
<span data-ttu-id="690f3-397">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="690f3-397">The URI must be fully qualified.</span></span>

<span data-ttu-id="690f3-398">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="690f3-398">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="690f3-399">De standaard waarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="690f3-399">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="690f3-400">Als u geen verbindings-URI opgeeft, kunt u de para meters **UseSSL** en **Port** gebruiken om de verbindings-URI-waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="690f3-400">If you don't specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="690f3-401">Geldige waarden voor het **transport** segment van de URI zijn http en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="690f3-401">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="690f3-402">Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met de standaard poorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="690f3-402">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with the standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="690f3-403">Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="690f3-403">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="690f3-404">Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="690f3-404">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: Uri, FilePathUri
Aliases: URI, CU

Required: False
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-405">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="690f3-405">-ContainerId</span></span>

<span data-ttu-id="690f3-406">Hiermee geeft u een matrix met container-Id's op.</span><span class="sxs-lookup"><span data-stu-id="690f3-406">Specifies an array of container IDs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-407">-Credential</span><span class="sxs-lookup"><span data-stu-id="690f3-407">-Credential</span></span>

<span data-ttu-id="690f3-408">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-408">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="690f3-409">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="690f3-409">The default is the current user.</span></span>

<span data-ttu-id="690f3-410">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="690f3-410">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="690f3-411">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-411">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="690f3-412">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="690f3-412">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="690f3-413">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="690f3-413">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName
Aliases:

Required: True (VMId, VMName, FilePathVMId, FilePathVMName), False (ComputerName, FilePathComputerName, Uri, FilePathUri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-414">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="690f3-414">-EnableNetworkAccess</span></span>

<span data-ttu-id="690f3-415">Geeft aan dat met deze cmdlet een interactief beveiligings token wordt toegevoegd aan loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="690f3-415">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="690f3-416">Met het interactieve token kunt u opdrachten uitvoeren in de loop back-sessie die gegevens van andere computers ophalen.</span><span class="sxs-lookup"><span data-stu-id="690f3-416">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="690f3-417">U kunt bijvoorbeeld een opdracht uitvoeren in de sessie waarmee XML-bestanden van een externe computer naar de lokale computer worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-417">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="690f3-418">Een loop back-sessie is een **PSSession** die afkomstig is van en eindigt op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-418">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="690f3-419">Als u een loop back-sessie wilt maken, laat u de para meter **ComputerName** weg of stelt u de waarde in op punt ( `.` ), localhost of de naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-419">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (`.`), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="690f3-420">Loop Back-sessies worden standaard gemaakt met behulp van een netwerk token, wat mogelijk niet voldoende machtigingen biedt om te verifiëren bij externe computers.</span><span class="sxs-lookup"><span data-stu-id="690f3-420">By default, loopback sessions are created using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="690f3-421">De para meter **EnableNetworkAccess** is alleen effectief in loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="690f3-421">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="690f3-422">Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, mislukt de opdracht, maar wordt de para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-422">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="690f3-423">U kunt externe toegang toestaan in een loop back-sessie met behulp van de **CredSSP** -waarde van de **verificatie** parameter, waarmee de sessie referenties worden gedelegeerd aan andere computers.</span><span class="sxs-lookup"><span data-stu-id="690f3-423">You can allow remote access in a loopback session using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="690f3-424">Om de computer te beschermen tegen kwaadwillende toegang, kunnen niet-verbonden loop Back-sessies met interactieve tokens, die zijn gemaakt met behulp van **EnableNetworkAccess** , alleen opnieuw verbinding maken vanaf de computer waarop de sessie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="690f3-424">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created using **EnableNetworkAccess** , can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="690f3-425">Verbroken sessies die gebruikmaken van CredSSP-verificatie, kunnen opnieuw worden aangesloten op andere computers.</span><span class="sxs-lookup"><span data-stu-id="690f3-425">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="690f3-426">Voor meer informatie raadpleegt u `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="690f3-426">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="690f3-427">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="690f3-427">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-428">-FilePath</span><span class="sxs-lookup"><span data-stu-id="690f3-428">-FilePath</span></span>

<span data-ttu-id="690f3-429">Hiermee geeft u een lokaal script op dat met deze cmdlet wordt uitgevoerd op een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="690f3-429">Specifies a local script that this cmdlet runs on one or more remote computers.</span></span> <span data-ttu-id="690f3-430">Voer het pad en de bestands naam van het script in of pipet een scriptpad naar `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="690f3-430">Enter the path and filename of the script, or pipe a script path to `Invoke-Command`.</span></span> <span data-ttu-id="690f3-431">Het script moet bestaan op de lokale computer of in een map waartoe de lokale computer toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="690f3-431">The script must exist on the local computer or in a directory that the local computer can access.</span></span> <span data-ttu-id="690f3-432">Gebruik **argument List** om de waarden van para meters in het script op te geven.</span><span class="sxs-lookup"><span data-stu-id="690f3-432">Use **ArgumentList** to specify the values of parameters in the script.</span></span>

<span data-ttu-id="690f3-433">Wanneer u deze para meter gebruikt, wordt de inhoud van het opgegeven script bestand door Power shell naar een script blok geconverteerd, wordt het script blok verzonden naar de externe computer en uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-433">When you use this parameter, PowerShell converts the contents of the specified script file to a script block, transmits the script block to the remote computer, and runs it on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId, FilePathSSHHost, FilePathSSHHostHash
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-434">-HideComputerName</span><span class="sxs-lookup"><span data-stu-id="690f3-434">-HideComputerName</span></span>

<span data-ttu-id="690f3-435">Geeft aan dat met deze cmdlet de computer naam van elk object uit de uitvoer weergave wordt wegge laten.</span><span class="sxs-lookup"><span data-stu-id="690f3-435">Indicates that this cmdlet omits the computer name of each object from the output display.</span></span> <span data-ttu-id="690f3-436">De naam van de computer die het object heeft gegenereerd, wordt standaard weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="690f3-436">By default, the name of the computer that generated the object appears in the display.</span></span>

<span data-ttu-id="690f3-437">Deze para meter is alleen van invloed op de uitvoer weergave.</span><span class="sxs-lookup"><span data-stu-id="690f3-437">This parameter affects only the output display.</span></span> <span data-ttu-id="690f3-438">Het object wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="690f3-438">It doesn't change the object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases: HCN

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-439">-Hostnaam</span><span class="sxs-lookup"><span data-stu-id="690f3-439">-HostName</span></span>

<span data-ttu-id="690f3-440">Hiermee geeft u een matrix van computer namen voor een verbinding op basis van SSH (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="690f3-440">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="690f3-441">Dit is vergelijkbaar met de para meter **ComputerName** , behalve dat de verbinding met de externe computer wordt gemaakt met behulp van SSH in plaats van Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="690f3-441">This is similar to the **ComputerName** parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>

<span data-ttu-id="690f3-442">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="690f3-442">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-443">-InDisconnectedSession</span><span class="sxs-lookup"><span data-stu-id="690f3-443">-InDisconnectedSession</span></span>

<span data-ttu-id="690f3-444">Geeft aan dat met deze cmdlet een opdracht of script wordt uitgevoerd in een sessie waarbij de verbinding is verbroken.</span><span class="sxs-lookup"><span data-stu-id="690f3-444">Indicates that this cmdlet runs a command or script in a disconnected session.</span></span>

<span data-ttu-id="690f3-445">Wanneer u de para meter **InDisconnectedSession** gebruikt, `Invoke-Command` wordt op elke externe computer een permanente sessie gemaakt, wordt de opdracht gestart die is opgegeven door de para meter **script Block** of **filepath** en wordt de verbinding met de sessie verbroken.</span><span class="sxs-lookup"><span data-stu-id="690f3-445">When you use the **InDisconnectedSession** parameter, `Invoke-Command` creates a persistent session on each remote computer, starts the command specified by the **ScriptBlock** or **FilePath** parameter, and then disconnects from the session.</span></span> <span data-ttu-id="690f3-446">De opdrachten blijven worden uitgevoerd in de verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="690f3-446">The commands continue to run in the disconnected sessions.</span></span> <span data-ttu-id="690f3-447">Met **InDisconnectedSession** kunt u opdrachten uitvoeren zonder een verbinding met de externe sessies te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="690f3-447">**InDisconnectedSession** enables you to run commands without maintaining a connection to the remote sessions.</span></span> <span data-ttu-id="690f3-448">En omdat de verbinding van de sessie wordt verbroken voordat er resultaten worden geretourneerd, zorgt **InDisconnectedSession** ervoor dat alle opdracht resultaten worden geretourneerd naar de opnieuw verbonden sessie, in plaats van te worden gesplitst tussen sessies.</span><span class="sxs-lookup"><span data-stu-id="690f3-448">And, because the session is disconnected before any results are returned, **InDisconnectedSession** makes sure that all command results are returned to the reconnected session, instead of being split between sessions.</span></span>

<span data-ttu-id="690f3-449">U kunt **InDisconnectedSession** niet gebruiken met de para meter **Session** of de para meter **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="690f3-449">You can't use **InDisconnectedSession** with the **Session** parameter or the **AsJob** parameter.</span></span>

<span data-ttu-id="690f3-450">Opdrachten die gebruikmaken van **InDisconnectedSession** retour neren een **PSSession** -object dat de niet-verbonden sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="690f3-450">Commands that use **InDisconnectedSession** return a **PSSession** object that represents the disconnected session.</span></span> <span data-ttu-id="690f3-451">Ze retour neren niet de uitvoer van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-451">They don't return the command output.</span></span> <span data-ttu-id="690f3-452">Gebruik de cmdlets of om verbinding te maken met de verbroken sessie `Connect-PSSession` `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="690f3-452">To connect to the disconnected session, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span> <span data-ttu-id="690f3-453">Gebruik de cmdlet om de resultaten op te halen van de opdrachten die in de sessie worden uitgevoerd `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="690f3-453">To get the results of commands that ran in the session, use the `Receive-PSSession` cmdlet.</span></span> <span data-ttu-id="690f3-454">Om opdrachten uit te voeren die uitvoer genereren in een verbroken sessie, stelt u de waarde van de **OutputBufferingMode** -sessie optie in op **Drop**.</span><span class="sxs-lookup"><span data-stu-id="690f3-454">To run commands that generate output in a disconnected session, set the value of the **OutputBufferingMode** session option to **Drop**.</span></span> <span data-ttu-id="690f3-455">Als u van plan bent om verbinding te maken met de verbroken sessie, stelt u de time-out voor inactiviteit in de sessie zo in dat u voldoende tijd hebt om verbinding te maken voordat u de sessie verwijdert.</span><span class="sxs-lookup"><span data-stu-id="690f3-455">If you intend to connect to the disconnected session, set the idle time-out in the session so that it provides sufficient time for you to connect before deleting the session.</span></span>

<span data-ttu-id="690f3-456">U kunt de uitvoer buffer modus en time-out voor inactiviteit instellen in de para meter **SessionOption** of in de `$PSSessionOption` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-456">You can set the output buffering mode and idle time-out in the **SessionOption** parameter or in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="690f3-457">Zie en about_Preference_Variables voor meer informatie over sessie `New-PSSessionOption` opties [about_Preference_Variables](./about/about_preference_variables.md).</span><span class="sxs-lookup"><span data-stu-id="690f3-457">For more information about session options, see `New-PSSessionOption` and [about_Preference_Variables](./about/about_preference_variables.md).</span></span>

<span data-ttu-id="690f3-458">Zie [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)voor meer informatie over de functie voor verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="690f3-458">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="690f3-459">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="690f3-459">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-460">-Input object</span><span class="sxs-lookup"><span data-stu-id="690f3-460">-InputObject</span></span>

<span data-ttu-id="690f3-461">Hiermee geeft u de invoer aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-461">Specifies input to the command.</span></span> <span data-ttu-id="690f3-462">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="690f3-462">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="690f3-463">Gebruik bij het gebruik van de para meter **input object** de `$Input` Automatische variabele in de waarde van de para meter **script Block** om de invoer objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="690f3-463">When using the **InputObject** parameter, use the `$Input` automatic variable in the value of the **ScriptBlock** parameter to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-464">-JobName</span><span class="sxs-lookup"><span data-stu-id="690f3-464">-JobName</span></span>

<span data-ttu-id="690f3-465">Hiermee geeft u een beschrijvende naam op voor de achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="690f3-465">Specifies a friendly name for the background job.</span></span> <span data-ttu-id="690f3-466">Taken worden standaard benoemd `Job<n>` , waarbij `<n>` een rang nummer is.</span><span class="sxs-lookup"><span data-stu-id="690f3-466">By default, jobs are named `Job<n>`, where `<n>` is an ordinal number.</span></span>

<span data-ttu-id="690f3-467">Als u de para meter **JobName** in een opdracht gebruikt, wordt de opdracht uitgevoerd als een taak en `Invoke-Command` wordt een taak object geretourneerd, zelfs als u geen **AsJob** in de opdracht opneemt.</span><span class="sxs-lookup"><span data-stu-id="690f3-467">If you use the **JobName** parameter in a command, the command is run as a job, and `Invoke-Command` returns a job object, even if you don't include **AsJob** in the command.</span></span>

<span data-ttu-id="690f3-468">Zie [about_Jobs](./About/about_Jobs.md)voor meer informatie over Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="690f3-468">For more information about PowerShell background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-469">-Bestandspad</span><span class="sxs-lookup"><span data-stu-id="690f3-469">-KeyFilePath</span></span>

<span data-ttu-id="690f3-470">Hiermee geeft u een pad naar een sleutel bestand dat door een Secure Shell (SSH) wordt gebruikt om een gebruiker op een externe computer te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="690f3-470">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="690f3-471">Met SSH kan gebruikers verificatie worden uitgevoerd via persoonlijke en open bare sleutels als alternatief voor de basis wachtwoord verificatie.</span><span class="sxs-lookup"><span data-stu-id="690f3-471">SSH allows user authentication to be performed via private and public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="690f3-472">Als de externe computer is geconfigureerd voor sleutel verificatie, kan deze para meter worden gebruikt om de sleutel op te geven waarmee de gebruiker wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-472">If the remote computer is configured for key authentication, then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="690f3-473">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="690f3-473">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-474">-NoNewScope</span><span class="sxs-lookup"><span data-stu-id="690f3-474">-NoNewScope</span></span>

<span data-ttu-id="690f3-475">Geeft aan dat met deze cmdlet de opgegeven opdracht wordt uitgevoerd in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="690f3-475">Indicates that this cmdlet runs the specified command in the current scope.</span></span> <span data-ttu-id="690f3-476">`Invoke-Command`Voert standaard opdrachten uit in hun eigen bereik.</span><span class="sxs-lookup"><span data-stu-id="690f3-476">By default, `Invoke-Command` runs commands in their own scope.</span></span>

<span data-ttu-id="690f3-477">Deze para meter is alleen geldig in opdrachten die worden uitgevoerd in de huidige sessie, dat wil zeggen opdrachten die de **computer naam** en de **sessie** parameters weglaten.</span><span class="sxs-lookup"><span data-stu-id="690f3-477">This parameter is valid only in commands that are run in the current session, that is, commands that omit both the **ComputerName** and **Session** parameters.</span></span>

<span data-ttu-id="690f3-478">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="690f3-478">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InProcess
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-479">-Port</span><span class="sxs-lookup"><span data-stu-id="690f3-479">-Port</span></span>

<span data-ttu-id="690f3-480">Hiermee geeft u de netwerk poort op de externe computer die wordt gebruikt voor deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-480">Specifies the network port on the remote computer that is used for this command.</span></span> <span data-ttu-id="690f3-481">Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="690f3-481">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="690f3-482">De standaard poorten zijn 5985 (WinRM-poort voor HTTP) en 5986 (WinRM-poort voor HTTPS).</span><span class="sxs-lookup"><span data-stu-id="690f3-482">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="690f3-483">Voordat u een andere poort gebruikt, configureert u de WinRM-listener op de externe computer om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="690f3-483">Before using an alternate port, configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="690f3-484">Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de Power shell-prompt:</span><span class="sxs-lookup"><span data-stu-id="690f3-484">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="690f3-485">Gebruik de para meter **poort** alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="690f3-485">Don't use the **Port** parameter unless you must.</span></span> <span data-ttu-id="690f3-486">De poort die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-486">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="690f3-487">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="690f3-487">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, FilePathComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-488">-RemoteDebug</span><span class="sxs-lookup"><span data-stu-id="690f3-488">-RemoteDebug</span></span>

<span data-ttu-id="690f3-489">Wordt gebruikt om de aangeroepen opdracht in de foutopsporingsmodus in de externe Power shell-sessie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-489">Used to run the invoked command in debug mode in the remote PowerShell session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-490">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="690f3-490">-RunAsAdministrator</span></span>

<span data-ttu-id="690f3-491">Geeft aan dat deze cmdlet een opdracht aanroept als beheerder.</span><span class="sxs-lookup"><span data-stu-id="690f3-491">Indicates that this cmdlet invokes a command as an Administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-492">-Script Block</span><span class="sxs-lookup"><span data-stu-id="690f3-492">-ScriptBlock</span></span>

<span data-ttu-id="690f3-493">Hiermee geeft u de opdrachten op die moeten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-493">Specifies the commands to run.</span></span> <span data-ttu-id="690f3-494">Plaats de opdrachten tussen accolades `{ }` om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="690f3-494">Enclose the commands in curly braces `{ }` to create a script block.</span></span>
<span data-ttu-id="690f3-495">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="690f3-495">This parameter is required.</span></span>

<span data-ttu-id="690f3-496">Standaard worden alle variabelen in de opdracht geëvalueerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-496">By default, any variables in the command are evaluated on the remote computer.</span></span> <span data-ttu-id="690f3-497">Als u lokale variabelen wilt toevoegen aan de opdracht, gebruikt u **argument List**.</span><span class="sxs-lookup"><span data-stu-id="690f3-497">To include local variables in the command, use **ArgumentList**.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, SSHHost, ContainerId, SSHHostHashParam
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-498">-Sessie</span><span class="sxs-lookup"><span data-stu-id="690f3-498">-Session</span></span>

<span data-ttu-id="690f3-499">Hiermee geeft u een matrix met sessies waarin met deze cmdlet de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-499">Specifies an array of sessions in which this cmdlet runs the command.</span></span> <span data-ttu-id="690f3-500">Voer een variabele in die **PSSession** -objecten bevat of een opdracht waarmee de **PSSession** -objecten, zoals een of-opdracht, worden gemaakt of opgehaald `New-PSSession` `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="690f3-500">Enter a variable that contains **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="690f3-501">Wanneer u een **PSSession** maakt, brengt Power shell een permanente verbinding met de externe computer tot stand.</span><span class="sxs-lookup"><span data-stu-id="690f3-501">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="690f3-502">Gebruik een **PSSession** om een reeks gerelateerde opdrachten uit te voeren die gegevens delen.</span><span class="sxs-lookup"><span data-stu-id="690f3-502">Use a **PSSession** to run a series of related commands that share data.</span></span> <span data-ttu-id="690f3-503">Als u één opdracht of een reeks niet-gerelateerde opdrachten wilt uitvoeren, gebruikt u de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="690f3-503">To run a single command or a series of unrelated commands, use the **ComputerName** parameter.</span></span> <span data-ttu-id="690f3-504">Zie [about_PSSessions](./About/about_PSSessions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="690f3-504">For more information, see [about_PSSessions](./About/about_PSSessions.md).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: FilePathRunspace, Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-505">-Sessie naam</span><span class="sxs-lookup"><span data-stu-id="690f3-505">-SessionName</span></span>

<span data-ttu-id="690f3-506">Hiermee geeft u een beschrijvende naam op voor een niet-verbonden sessie.</span><span class="sxs-lookup"><span data-stu-id="690f3-506">Specifies a friendly name for a disconnected session.</span></span> <span data-ttu-id="690f3-507">U kunt de naam gebruiken om te verwijzen naar de sessie in volgende opdrachten, zoals een `Get-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-507">You can use the name to refer to the session in subsequent commands, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="690f3-508">Deze para meter is alleen geldig voor de para meter **InDisconnectedSession** .</span><span class="sxs-lookup"><span data-stu-id="690f3-508">This parameter is valid only with the **InDisconnectedSession** parameter.</span></span>

<span data-ttu-id="690f3-509">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="690f3-509">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-510">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="690f3-510">-SessionOption</span></span>

<span data-ttu-id="690f3-511">Hiermee geeft u geavanceerde opties voor de sessie op.</span><span class="sxs-lookup"><span data-stu-id="690f3-511">Specifies advanced options for the session.</span></span> <span data-ttu-id="690f3-512">Voer een **SessionOption** -object in, zoals het account dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de namen van sessie opties zijn en de waarden zijn waarden voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="690f3-512">Enter a **SessionOption** object, such as one that you create using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="690f3-513">De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="690f3-513">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="690f3-514">Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="690f3-514">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="690f3-515">De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="690f3-515">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="690f3-516">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="690f3-516">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="690f3-517">Zie voor een beschrijving van de sessie opties die de standaard waarden bevatten `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="690f3-517">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="690f3-518">Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](About/about_Preference_Variables.md)variabele.</span><span class="sxs-lookup"><span data-stu-id="690f3-518">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="690f3-519">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="690f3-519">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-520">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="690f3-520">-SSHConnection</span></span>

<span data-ttu-id="690f3-521">Deze para meter gebruikt een matrix van hash-tabellen waarbij elke hash-tabel een of meer verbindings parameters bevat die nodig zijn om een SSH-verbinding (Secure Shell) tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="690f3-521">This parameter takes an array of hash tables where each hash table contains one or more connection parameters needed to establish a Secure Shell (SSH) connection.</span></span> <span data-ttu-id="690f3-522">De **SSHConnection** -para meter is handig voor het maken van meerdere sessies waarbij voor elke sessie verschillende verbindings gegevens zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="690f3-522">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

<span data-ttu-id="690f3-523">De hashtabel bevat de volgende leden:</span><span class="sxs-lookup"><span data-stu-id="690f3-523">The hashtable has the following members:</span></span>

- <span data-ttu-id="690f3-524">**ComputerName** (of **hostnaam** )</span><span class="sxs-lookup"><span data-stu-id="690f3-524">**ComputerName** (or **HostName** )</span></span>
- <span data-ttu-id="690f3-525">**Poort**</span><span class="sxs-lookup"><span data-stu-id="690f3-525">**Port**</span></span>
- <span data-ttu-id="690f3-526">**Gebruikers**</span><span class="sxs-lookup"><span data-stu-id="690f3-526">**UserName**</span></span>
- <span data-ttu-id="690f3-527">Het **bestandspad** (of **IdentityFilePath** )</span><span class="sxs-lookup"><span data-stu-id="690f3-527">**KeyFilePath** (or **IdentityFilePath** )</span></span>

<span data-ttu-id="690f3-528">**ComputerName** (of **hostnaam** ) is het enige sleutel-waardepaar dat vereist is.</span><span class="sxs-lookup"><span data-stu-id="690f3-528">**ComputerName** (or **HostName** ) is the only key-value pair that is required.</span></span>

<span data-ttu-id="690f3-529">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="690f3-529">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam, FilePathSSHHostHash
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-530">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="690f3-530">-SSHTransport</span></span>

<span data-ttu-id="690f3-531">Geeft aan dat de externe verbinding tot stand is gebracht met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="690f3-531">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="690f3-532">Power Shell maakt standaard gebruik van Windows WinRM om verbinding te maken met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-532">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="690f3-533">Met deze switch wordt Power shell gedwongen de para meter **hostname** te gebruiken om een externe verbinding op basis van SSH tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="690f3-533">This switch forces PowerShell to use the **HostName** parameter for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="690f3-534">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="690f3-534">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-535">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="690f3-535">-ThrottleLimit</span></span>

<span data-ttu-id="690f3-536">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="690f3-536">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="690f3-537">Als u deze para meter weglaat of een waarde van 0 invoert, wordt de standaard waarde 32 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="690f3-537">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="690f3-538">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-538">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-539">-GebruikersNaam</span><span class="sxs-lookup"><span data-stu-id="690f3-539">-UserName</span></span>

<span data-ttu-id="690f3-540">Hiermee geeft u de gebruikers naam op voor het account dat wordt gebruikt om een opdracht uit te voeren op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-540">Specifies the username for the account used to run a command on the remote computer.</span></span> <span data-ttu-id="690f3-541">De verificatie methode voor de gebruiker is afhankelijk van hoe Secure Shell (SSH) is geconfigureerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-541">The user authentication method depends on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="690f3-542">Als SSH is geconfigureerd voor basis wachtwoord verificatie, wordt u gevraagd om het wacht woord van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="690f3-542">If SSH is configured for basic password authentication, then you'll be prompted for the user password.</span></span>

<span data-ttu-id="690f3-543">Als SSH is geconfigureerd voor gebruikers authenticatie op basis van sleutels, kan een pad naar een sleutel bestand worden opgegeven **via de para** meter voor het sleutelpad en wordt er geen wachtwoord prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="690f3-543">If SSH is configured for key-based user authentication then a key file path can be provided via the **KeyFilePath** parameter and no password prompt occurs.</span></span> <span data-ttu-id="690f3-544">Als het sleutel bestand van de client gebruiker zich in een bekende SSH-locatie bevindt, is de para meter voor het sleutelpad niet nodig voor verificatie op basis van een sleutel en **wordt de gebruikers** verificatie automatisch uitgevoerd op basis van de gebruikers naam.</span><span class="sxs-lookup"><span data-stu-id="690f3-544">If the client user key file is located in an SSH known location, then the **KeyFilePath** parameter isn't needed for key-based authentication, and user authentication occurs automatically based on the username.</span></span> <span data-ttu-id="690f3-545">Zie de SSH-documentatie van uw platform over gebruikers verificatie op basis van een sleutel voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="690f3-545">For more information, see your platform's SSH documentation about key-based user authentication.</span></span>

<span data-ttu-id="690f3-546">Dit is geen vereiste para meter.</span><span class="sxs-lookup"><span data-stu-id="690f3-546">This isn't a required parameter.</span></span> <span data-ttu-id="690f3-547">Als de para meter **username** niet is opgegeven, wordt de huidige aangemelde gebruikers naam gebruikt voor de verbinding.</span><span class="sxs-lookup"><span data-stu-id="690f3-547">If the **UserName** parameter isn't specified, then the current logged on username is used for the connection.</span></span>

<span data-ttu-id="690f3-548">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="690f3-548">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-549">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="690f3-549">-UseSSL</span></span>

<span data-ttu-id="690f3-550">Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-550">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="690f3-551">SSL wordt standaard niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="690f3-551">By default, SSL isn't used.</span></span>

<span data-ttu-id="690f3-552">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="690f3-552">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="690f3-553">De para meter **UseSSL** is een extra beveiliging waarbij de gegevens worden verzonden via een HTTPS, in plaats van via http.</span><span class="sxs-lookup"><span data-stu-id="690f3-553">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span>

<span data-ttu-id="690f3-554">Als u deze para meter gebruikt, maar SSL niet beschikbaar is op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-554">If you use this parameter, but SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-555">-VMId</span><span class="sxs-lookup"><span data-stu-id="690f3-555">-VMId</span></span>

<span data-ttu-id="690f3-556">Hiermee geeft u een matrix met Id's van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="690f3-556">Specifies an array of IDs of virtual machines.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: VMId, FilePathVMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-557">-VMName</span><span class="sxs-lookup"><span data-stu-id="690f3-557">-VMName</span></span>

<span data-ttu-id="690f3-558">Hiermee geeft u een matrix met namen van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="690f3-558">Specifies an array of names of virtual machines.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName, FilePathVMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-559">-Subsysteem</span><span class="sxs-lookup"><span data-stu-id="690f3-559">-Subsystem</span></span>

<span data-ttu-id="690f3-560">Hiermee geeft u het SSH-subsysteem op dat wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="690f3-560">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="690f3-561">Hiermee geeft u het subsysteem op dat moet worden gebruikt op het doel zoals gedefinieerd in sshd_config.</span><span class="sxs-lookup"><span data-stu-id="690f3-561">This specifies the subsystem to use on the target as defined in sshd_config.</span></span>
<span data-ttu-id="690f3-562">Het subsysteem start een specifieke versie van Power shell met vooraf gedefinieerde para meters.</span><span class="sxs-lookup"><span data-stu-id="690f3-562">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span>
<span data-ttu-id="690f3-563">Als het opgegeven subsysteem niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-563">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="690f3-564">Als deze para meter niet wordt gebruikt, is de standaard het subsysteem Power shell.</span><span class="sxs-lookup"><span data-stu-id="690f3-564">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="690f3-565">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="690f3-565">CommonParameters</span></span>

<span data-ttu-id="690f3-566">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="690f3-566">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="690f3-567">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="690f3-567">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="690f3-568">INVOER</span><span class="sxs-lookup"><span data-stu-id="690f3-568">INPUTS</span></span>

### <span data-ttu-id="690f3-569">System. Management. Automation. script Block</span><span class="sxs-lookup"><span data-stu-id="690f3-569">System.Management.Automation.ScriptBlock</span></span>

<span data-ttu-id="690f3-570">U kunt een opdracht in een script blok door sluizen naar `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="690f3-570">You can pipe a command in a script block to `Invoke-Command`.</span></span> <span data-ttu-id="690f3-571">Gebruik de `$Input` Automatische variabele om de invoer objecten in de opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="690f3-571">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="690f3-572">UITVOER</span><span class="sxs-lookup"><span data-stu-id="690f3-572">OUTPUTS</span></span>

### <span data-ttu-id="690f3-573">System. Management. Automation. PSRemotingJob, System. Management. Automation. Runspaces. PSSession, of de uitvoer van de aangeroepen opdracht</span><span class="sxs-lookup"><span data-stu-id="690f3-573">System.Management.Automation.PSRemotingJob, System.Management.Automation.Runspaces.PSSession, or the output of the invoked command</span></span>

<span data-ttu-id="690f3-574">Met deze cmdlet wordt een taak object geretourneerd als u de para meter **AsJob** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="690f3-574">This cmdlet returns a job object, if you use the **AsJob** parameter.</span></span> <span data-ttu-id="690f3-575">Als u de para meter **InDisconnectedSession** opgeeft, `Invoke-Command` wordt een **PSSession** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-575">If you specify the **InDisconnectedSession** parameter, `Invoke-Command` returns a **PSSession** object.</span></span> <span data-ttu-id="690f3-576">Anders wordt de uitvoer van de aangeroepen opdracht geretourneerd. Dit is de waarde van de para meter **script Block** .</span><span class="sxs-lookup"><span data-stu-id="690f3-576">Otherwise, it returns the output of the invoked command, which is the value of the **ScriptBlock** parameter.</span></span>

## <span data-ttu-id="690f3-577">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="690f3-577">NOTES</span></span>

<span data-ttu-id="690f3-578">In Windows Vista en latere versies van het Windows-besturings systeem **ComputerName** `Invoke-Command` moet u Power shell uitvoeren met de optie **als administrator uitvoeren** om de para meter ComputerName van te gebruiken voor het uitvoeren van een opdracht op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-578">On Windows Vista, and later versions of the Windows operating system, to use the **ComputerName** parameter of `Invoke-Command` to run a command on the local computer, you must run PowerShell using the **Run as administrator** option.</span></span>

<span data-ttu-id="690f3-579">Wanneer u opdrachten op meerdere computers uitvoert, maakt Power shell verbinding met de computers in de volg orde waarin ze worden weer gegeven in de lijst.</span><span class="sxs-lookup"><span data-stu-id="690f3-579">When you run commands on multiple computers, PowerShell connects to the computers in the order in which they appear in the list.</span></span> <span data-ttu-id="690f3-580">De uitvoer van de opdracht wordt echter weer gegeven in de volg orde waarin deze worden ontvangen van de externe computers. Dit kan anders zijn.</span><span class="sxs-lookup"><span data-stu-id="690f3-580">However, the command output is displayed in the order that it's received from the remote computers, which might be different.</span></span>

<span data-ttu-id="690f3-581">Fouten die het resultaat zijn van de opdracht die `Invoke-Command` wordt uitgevoerd, worden opgenomen in de opdracht resultaten.</span><span class="sxs-lookup"><span data-stu-id="690f3-581">Errors that result from the command that `Invoke-Command` runs are included in the command results.</span></span>
<span data-ttu-id="690f3-582">Fouten waarvoor fouten in een lokale opdracht zouden worden beëindigd, worden beschouwd als niet-afsluit fouten in een externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="690f3-582">Errors that would be terminating errors in a local command are treated as non-terminating errors in a remote command.</span></span> <span data-ttu-id="690f3-583">Deze strategie zorgt ervoor dat het beëindigen van fouten op één computer de opdracht niet sluit op alle computers waarop deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-583">This strategy makes sure that terminating errors on one computer don't close the command on all computers on which it's run.</span></span> <span data-ttu-id="690f3-584">Deze procedure wordt ook gebruikt wanneer een externe opdracht wordt uitgevoerd op één computer.</span><span class="sxs-lookup"><span data-stu-id="690f3-584">This practice is used even when a remote command is run on a single computer.</span></span>

<span data-ttu-id="690f3-585">Als de externe computer zich niet in een domein bevindt dat de lokale computer vertrouwt, is de computer mogelijk niet in staat om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="690f3-585">If the remote computer isn't in a domain that the local computer trusts, the computer might not be able to authenticate the user's credentials.</span></span> <span data-ttu-id="690f3-586">Als u de externe computer wilt toevoegen aan de lijst met vertrouwde hosts in WS-Management, gebruikt u de volgende opdracht in de `WSMAN` provider, waarbij `<Remote-Computer-Name>` de naam is van de externe computer:</span><span class="sxs-lookup"><span data-stu-id="690f3-586">To add the remote computer to the list of trusted hosts in WS-Management, use the following command in the `WSMAN` provider, where `<Remote-Computer-Name>` is the name of the remote computer:</span></span>

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

<span data-ttu-id="690f3-587">Wanneer u een **PSSession** verbreekt met de para meter **InDisconnectedSession** , wordt de sessie status **losgekoppeld** en is de beschik baarheid **geen**.</span><span class="sxs-lookup"><span data-stu-id="690f3-587">When you disconnect a **PSSession** using the **InDisconnectedSession** parameter, the session state is **Disconnected** and the availability is **None**.</span></span> <span data-ttu-id="690f3-588">De waarde van de eigenschap **State** is relatief ten opzichte van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="690f3-588">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="690f3-589">Als de waarde voor de **verbinding is verbroken** , betekent dit dat de **PSSession** niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="690f3-589">A value of **Disconnected** means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="690f3-590">Dit betekent echter niet dat de **PSSession** van de verbinding met alle sessies is verbroken.</span><span class="sxs-lookup"><span data-stu-id="690f3-590">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="690f3-591">Deze is mogelijk verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="690f3-591">It might be connected to a different session.</span></span> <span data-ttu-id="690f3-592">Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de sessie of er opnieuw verbinding mee wilt maken.</span><span class="sxs-lookup"><span data-stu-id="690f3-592">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

<span data-ttu-id="690f3-593">Een **beschikbaarheids** waarde van **geen** geeft aan dat u verbinding kunt maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="690f3-593">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="690f3-594">De waarde **bezet** geeft aan dat u geen verbinding kunt maken met de **PSSession** , omdat deze is verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="690f3-594">A value of **Busy** indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span> <span data-ttu-id="690f3-595">Zie [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)voor meer informatie over de waarden van de eigenschap **State** van sessies.</span><span class="sxs-lookup"><span data-stu-id="690f3-595">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span> <span data-ttu-id="690f3-596">Zie [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de eigenschap **Beschik baarheid** van sessies.</span><span class="sxs-lookup"><span data-stu-id="690f3-596">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

<span data-ttu-id="690f3-597">De para meters **hostname** en **SSHConnection** zijn opgenomen vanaf Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="690f3-597">The **HostName** and **SSHConnection** parameters were included starting with PowerShell 6.0.</span></span> <span data-ttu-id="690f3-598">Ze zijn toegevoegd om Power shell Remoting te bieden op basis van de Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="690f3-598">They were added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="690f3-599">Power shell en SSH worden ondersteund op meerdere platformen (Windows, Linux, macOS) en externe communicatie van Power shell werkt op deze platforms waarin Power shell en SSH zijn geïnstalleerd en geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="690f3-599">PowerShell and SSH are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting works over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="690f3-600">Dit is gescheiden van de vorige Windows-functie voor externe toegang die is gebaseerd op WinRM en veel van de specifieke WinRM-functies en-beperkingen zijn niet van toepassing.</span><span class="sxs-lookup"><span data-stu-id="690f3-600">This is separate from the previous Windows only remoting that is based on WinRM and many of the WinRM specific features and limitations don't apply.</span></span> <span data-ttu-id="690f3-601">Bijvoorbeeld: op WinRM gebaseerde quota's, sessie opties, aangepaste eindpunt configuratie en functies voor ontkoppelen/opnieuw verbinden worden op dit moment niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="690f3-601">For example WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="690f3-602">Zie voor meer informatie over het instellen van externe toegang tot Power shell [via SSH Power shell](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="690f3-602">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <span data-ttu-id="690f3-603">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="690f3-603">RELATED LINKS</span></span>

[<span data-ttu-id="690f3-604">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="690f3-604">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="690f3-605">about_Remote</span><span class="sxs-lookup"><span data-stu-id="690f3-605">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="690f3-606">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="690f3-606">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="690f3-607">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="690f3-607">about_Remote_Troubleshooting</span></span>](./About/about_remote_troubleshooting.md)

[<span data-ttu-id="690f3-608">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="690f3-608">about_Remote_Variables</span></span>](./About/about_Remote_Variables.md)

[<span data-ttu-id="690f3-609">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="690f3-609">about_Scopes</span></span>](./About/about_scopes.md)

[<span data-ttu-id="690f3-610">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="690f3-610">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="690f3-611">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="690f3-611">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="690f3-612">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="690f3-612">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="690f3-613">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="690f3-613">Invoke-Item</span></span>](../Microsoft.PowerShell.Management/Invoke-Item.md)

[<span data-ttu-id="690f3-614">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="690f3-614">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="690f3-615">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="690f3-615">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="690f3-616">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="690f3-616">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
