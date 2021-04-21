---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-opdracht
ms.openlocfilehash: bd34c20843720b5900e3a6d594939934624d1b13
ms.sourcegitcommit: b10731301412afd4111743b85da95e8c25583533
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/20/2021
ms.locfileid: "107756321"
---
# <span data-ttu-id="f900c-102">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="f900c-102">Invoke-Command</span></span>

## <span data-ttu-id="f900c-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="f900c-103">Synopsis</span></span>
<span data-ttu-id="f900c-104">Opdrachten worden uitgevoerd op lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-104">Runs commands on local and remote computers.</span></span>

## <span data-ttu-id="f900c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f900c-105">Syntax</span></span>

### <span data-ttu-id="f900c-106">InProcess (standaard)</span><span class="sxs-lookup"><span data-stu-id="f900c-106">InProcess (Default)</span></span>

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="f900c-107">FilePathRunspace</span><span class="sxs-lookup"><span data-stu-id="f900c-107">FilePathRunspace</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="f900c-108">Sessie</span><span class="sxs-lookup"><span data-stu-id="f900c-108">Session</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="f900c-109">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="f900c-109">FilePathComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="f900c-110">ComputerName</span><span class="sxs-lookup"><span data-stu-id="f900c-110">ComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="f900c-111">Uri</span><span class="sxs-lookup"><span data-stu-id="f900c-111">Uri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="f900c-112">FilePathUri</span><span class="sxs-lookup"><span data-stu-id="f900c-112">FilePathUri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="f900c-113">VMId</span><span class="sxs-lookup"><span data-stu-id="f900c-113">VMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="f900c-114">VMName</span><span class="sxs-lookup"><span data-stu-id="f900c-114">VMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="f900c-115">FilePathVMId</span><span class="sxs-lookup"><span data-stu-id="f900c-115">FilePathVMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="f900c-116">FilePathVMName</span><span class="sxs-lookup"><span data-stu-id="f900c-116">FilePathVMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="f900c-117">SSHHost</span><span class="sxs-lookup"><span data-stu-id="f900c-117">SSHHost</span></span>

```
Invoke-Command [-Port <Int32>] [-AsJob] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> -HostName <String[]> [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-Subsystem <String>] [-ConnectingTimeout <int>] [<CommonParameters>]
```

### <span data-ttu-id="f900c-118">ContainerId</span><span class="sxs-lookup"><span data-stu-id="f900c-118">ContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="f900c-119">FilePathContainerId</span><span class="sxs-lookup"><span data-stu-id="f900c-119">FilePathContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="f900c-120">SSHHostHashParam</span><span class="sxs-lookup"><span data-stu-id="f900c-120">SSHHostHashParam</span></span>

```
Invoke-Command [-AsJob] [-HideComputerName] [-JobName <String>] [-ScriptBlock] <ScriptBlock>
 -SSHConnection <Hashtable[]> [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="f900c-121">FilePathSSHHost</span><span class="sxs-lookup"><span data-stu-id="f900c-121">FilePathSSHHost</span></span>

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -HostName <String[]>
 [-UserName <String>] [-KeyFilePath <String>] [-SSHTransport] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="f900c-122">FilePathSSHHostHash</span><span class="sxs-lookup"><span data-stu-id="f900c-122">FilePathSSHHostHash</span></span>

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -SSHConnection <Hashtable[]>
 [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="f900c-123">Description</span><span class="sxs-lookup"><span data-stu-id="f900c-123">Description</span></span>

<span data-ttu-id="f900c-124">De cmdlet voert opdrachten uit op een lokale of externe computer en retourneert alle uitvoer van de `Invoke-Command` opdrachten, inclusief fouten.</span><span class="sxs-lookup"><span data-stu-id="f900c-124">The `Invoke-Command` cmdlet runs commands on a local or remote computer and returns all output from the commands, including errors.</span></span> <span data-ttu-id="f900c-125">Met één opdracht `Invoke-Command` kunt u opdrachten uitvoeren op meerdere computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-125">Using a single `Invoke-Command` command, you can run commands on multiple computers.</span></span>

<span data-ttu-id="f900c-126">Als u één opdracht wilt uitvoeren op een externe computer, gebruikt u de parameter **ComputerName.**</span><span class="sxs-lookup"><span data-stu-id="f900c-126">To run a single command on a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="f900c-127">Als u een reeks gerelateerde opdrachten wilt uitvoeren die gegevens delen, gebruikt u de cmdlet om een `New-PSSession` **PSSession** (een permanente verbinding) te maken op de externe computer en gebruikt u vervolgens de parameter **Session** van om de opdracht uit te voeren `Invoke-Command` in de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="f900c-127">To run a series of related commands that share data, use the `New-PSSession` cmdlet to create a **PSSession** (a persistent connection) on the remote computer, and then use the **Session** parameter of `Invoke-Command` to run the command in the **PSSession**.</span></span> <span data-ttu-id="f900c-128">Als u een opdracht wilt uitvoeren in een sessie zonder verbinding, gebruikt u de parameter **InDisconnectedSession.**</span><span class="sxs-lookup"><span data-stu-id="f900c-128">To run a command in a disconnected session, use the **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="f900c-129">Als u een opdracht wilt uitvoeren in een achtergrondjob, gebruikt u de parameter **AsJob.**</span><span class="sxs-lookup"><span data-stu-id="f900c-129">To run a command in a background job, use the **AsJob** parameter.</span></span>

<span data-ttu-id="f900c-130">U kunt ook op `Invoke-Command` een lokale computer gebruiken om een blok script als een opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-130">You can also use `Invoke-Command` on a local computer to a script block as a command.</span></span> <span data-ttu-id="f900c-131">PowerShell voert het scriptblok onmiddellijk uit in een onderliggend bereik van het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="f900c-131">PowerShell runs the script block immediately in a child scope of the current scope.</span></span>

<span data-ttu-id="f900c-132">Lees voordat u gebruikt om opdrachten uit te voeren op een `Invoke-Command` externe computer [about_Remote.](./About/about_Remote.md)</span><span class="sxs-lookup"><span data-stu-id="f900c-132">Before using `Invoke-Command` to run commands on a remote computer, read [about_Remote](./About/about_Remote.md).</span></span>

<span data-ttu-id="f900c-133">Vanaf PowerShell 6.0 kunt u Secure Shell (SSH) gebruiken om verbinding te maken met en opdrachten aan te roepen op externe computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-133">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to and invoke commands on remote computers.</span></span> <span data-ttu-id="f900c-134">SSH moet worden geïnstalleerd op de lokale computer en de externe computer moet worden geconfigureerd met een PowerShell SSH-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="f900c-134">SSH must be installed on the local computer and the remote computer must be configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="f900c-135">Het voordeel van een externe PowerShell-sessie op basis van SSH is dat deze op meerdere platforms werkt (Windows, Linux, macOS).</span><span class="sxs-lookup"><span data-stu-id="f900c-135">The benefit of an SSH based PowerShell remote session is that it works across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="f900c-136">Voor een SSH-sessie gebruikt u de parameters **HostName** of **SSHConnection** om de externe computer en relevante verbindingsgegevens op te geven.</span><span class="sxs-lookup"><span data-stu-id="f900c-136">For SSH based session you use the **HostName** or **SSHConnection** parameters to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="f900c-137">Zie Voor meer informatie over het instellen van remoting via PowerShell SSH [Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="f900c-137">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="f900c-138">Sommige codevoorbeelden gebruiken splatting om de regellengte te verminderen.</span><span class="sxs-lookup"><span data-stu-id="f900c-138">Some code samples use splatting to reduce the line length.</span></span> <span data-ttu-id="f900c-139">Zie voor meer informatie [about_Splatting](./About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="f900c-139">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="f900c-140">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f900c-140">Examples</span></span>

### <span data-ttu-id="f900c-141">Voorbeeld 1: een script uitvoeren op een server</span><span class="sxs-lookup"><span data-stu-id="f900c-141">Example 1: Run a script on a server</span></span>

<span data-ttu-id="f900c-142">In dit voorbeeld wordt het `Test.ps1` script uitgevoerd op de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="f900c-142">This example runs the `Test.ps1` script on the Server01 computer.</span></span>

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

<span data-ttu-id="f900c-143">De **FilePath** parameter geeft u een script dat zich op de lokale computer bevindt.</span><span class="sxs-lookup"><span data-stu-id="f900c-143">The **FilePath** parameter specifies a script that is located on the local computer.</span></span> <span data-ttu-id="f900c-144">Het script wordt uitgevoerd op de externe computer en de resultaten worden geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-144">The script runs on the remote computer and the results are returned to the local computer.</span></span>

### <span data-ttu-id="f900c-145">Voorbeeld 2: een opdracht uitvoeren op een externe server</span><span class="sxs-lookup"><span data-stu-id="f900c-145">Example 2: Run a command on a remote server</span></span>

<span data-ttu-id="f900c-146">In dit voorbeeld wordt een `Get-Culture` opdracht uitgevoerd op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="f900c-146">This example runs a `Get-Culture` command on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

<span data-ttu-id="f900c-147">De **ComputerName** parameter geeft u de naam van de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-147">The **ComputerName** parameter specifies the name of the remote computer.</span></span> <span data-ttu-id="f900c-148">De **referentie** parameter wordt gebruikt voor het uitvoeren van de opdracht in de beveiligingscontext van Domain01\User01, een gebruiker die is machtigingen voor het uitvoeren van opdrachten.</span><span class="sxs-lookup"><span data-stu-id="f900c-148">The **Credential** parameter is used to run the command in the security context of Domain01\User01, a user who has permission to run commands.</span></span> <span data-ttu-id="f900c-149">De **ScriptBlock** parameter geeft u de opdracht moet worden uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-149">The **ScriptBlock** parameter specifies the command to be run on the remote computer.</span></span>

<span data-ttu-id="f900c-150">Als antwoord vraagt PowerShell het wachtwoord en een verificatiemethode voor het account User01 aan.</span><span class="sxs-lookup"><span data-stu-id="f900c-150">In response, PowerShell requests the password and an authentication method for the User01 account.</span></span>
<span data-ttu-id="f900c-151">Vervolgens wordt de opdracht uitgevoerd op de computer Server01 en wordt het resultaat retourneert.</span><span class="sxs-lookup"><span data-stu-id="f900c-151">It then runs the command on the Server01 computer and returns the result.</span></span>

### <span data-ttu-id="f900c-152">Voorbeeld 3: Een opdracht uitvoeren in een permanente verbinding</span><span class="sxs-lookup"><span data-stu-id="f900c-152">Example 3: Run a command in a persistent connection</span></span>

<span data-ttu-id="f900c-153">In dit voorbeeld wordt dezelfde opdracht uitgevoerd in een sessie, met behulp van `Get-Culture` een permanente verbinding, op de externe computer met de naam Server02.</span><span class="sxs-lookup"><span data-stu-id="f900c-153">This example runs the same `Get-Culture` command in a session, using a persistent connection, on the remote computer named Server02.</span></span>

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="f900c-154">De `New-PSSession` cmdlet maakt een sessie op de externe computer Server02 en slaat deze op in de `$s` variabele .</span><span class="sxs-lookup"><span data-stu-id="f900c-154">The `New-PSSession` cmdlet creates a session on the Server02 remote computer and saves it in the `$s` variable.</span></span> <span data-ttu-id="f900c-155">Normaal gesproken maakt u een sessie alleen wanneer u een reeks opdrachten op de externe computer uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="f900c-155">Typically, you create a session only when you run a series of commands on the remote computer.</span></span>

<span data-ttu-id="f900c-156">De `Invoke-Command` cmdlet voert de `Get-Culture` opdracht uit op Server02.</span><span class="sxs-lookup"><span data-stu-id="f900c-156">The `Invoke-Command` cmdlet runs the `Get-Culture` command on Server02.</span></span> <span data-ttu-id="f900c-157">De **sessie** parameter geeft u de sessie opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="f900c-157">The **Session** parameter specifies the session saved in the `$s` variable.</span></span>

<span data-ttu-id="f900c-158">Als antwoord voert PowerShell de opdracht uit in de sessie op de server02-computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-158">In response, PowerShell runs the command in the session on the Server02 computer.</span></span>

### <span data-ttu-id="f900c-159">Voorbeeld 4: Een sessie gebruiken om een reeks opdrachten uit te voeren die gegevens delen</span><span class="sxs-lookup"><span data-stu-id="f900c-159">Example 4: Use a session to run a series of commands that share data</span></span>

<span data-ttu-id="f900c-160">In dit voorbeeld worden de effecten van het gebruik van **de parameters ComputerName** en **Session** van `Invoke-Command` vergeleken.</span><span class="sxs-lookup"><span data-stu-id="f900c-160">This example compares the effects of using **ComputerName** and **Session** parameters of `Invoke-Command`.</span></span> <span data-ttu-id="f900c-161">U ziet hoe u een sessie gebruikt om een reeks opdrachten uit te voeren die dezelfde gegevens delen.</span><span class="sxs-lookup"><span data-stu-id="f900c-161">It shows how to use a session to run a series of commands that share the same data.</span></span>

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

<span data-ttu-id="f900c-162">De eerste twee opdrachten gebruiken de **ComputerName** parameter van `Invoke-Command` om opdrachten uit te voeren op de externe computer Server02.</span><span class="sxs-lookup"><span data-stu-id="f900c-162">The first two commands use the **ComputerName** parameter of `Invoke-Command` to run commands on the Server02 remote computer.</span></span> <span data-ttu-id="f900c-163">De eerste opdracht gebruikt de `Get-Process` cmdlet om het PowerShell-proces op de externe computer op te halen en op te slaan in de `$p` variabele .</span><span class="sxs-lookup"><span data-stu-id="f900c-163">The first command uses the `Get-Process` cmdlet to get the PowerShell process on the remote computer and to save it in the `$p` variable.</span></span> <span data-ttu-id="f900c-164">Met de tweede opdracht wordt de waarde van de eigenschap **VirtualMemorySize van** het PowerShell-proces opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f900c-164">The second command gets the value of the **VirtualMemorySize** property of the PowerShell process.</span></span>

<span data-ttu-id="f900c-165">Wanneer u de **parameter ComputerName gebruikt,** maakt PowerShell een nieuwe sessie om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f900c-165">When you use the **ComputerName** parameter, PowerShell creates a new session to run the command.</span></span>
<span data-ttu-id="f900c-166">De sessie wordt gesloten wanneer de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="f900c-166">The session is closed when the command completes.</span></span> <span data-ttu-id="f900c-167">De variabele is gemaakt in één verbinding, maar deze bestaat niet in de verbinding die is gemaakt `$p` voor de tweede opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-167">The `$p` variable was created in one connection, but it doesn't exist in the connection created for the second command.</span></span>

<span data-ttu-id="f900c-168">Het probleem wordt opgelost door een permanente sessie te maken op de externe computer en vervolgens beide opdrachten in dezelfde sessie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f900c-168">The problem is solved by creating a persistent session on the remote computer, then running both of the commands in the same session.</span></span>

<span data-ttu-id="f900c-169">De `New-PSSession` cmdlet maakt een permanente sessie op de computer Server02 en slaat de sessie op in de `$s` variabele .</span><span class="sxs-lookup"><span data-stu-id="f900c-169">The `New-PSSession` cmdlet creates a persistent session on the computer Server02 and saves the session in the `$s` variable.</span></span> <span data-ttu-id="f900c-170">De `Invoke-Command` volgende regels gebruiken de **sessieparameter** om beide opdrachten in dezelfde sessie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f900c-170">The `Invoke-Command` lines that follow use the **Session** parameter to run both of the commands in the same session.</span></span> <span data-ttu-id="f900c-171">Omdat beide opdrachten in dezelfde sessie worden uitgevoerd, blijft `$p` de waarde actief.</span><span class="sxs-lookup"><span data-stu-id="f900c-171">Since both commands run in the same session, the `$p` value remains active.</span></span>

### <span data-ttu-id="f900c-172">Voorbeeld 5: Voer een opdracht in die is opgeslagen in een lokale variabele</span><span class="sxs-lookup"><span data-stu-id="f900c-172">Example 5: Enter a command stored in a local variable</span></span>

<span data-ttu-id="f900c-173">In dit voorbeeld ziet u hoe u een opdracht maakt die is opgeslagen als een scriptblok in een lokale variabele.</span><span class="sxs-lookup"><span data-stu-id="f900c-173">This example shows how to create a command that is stored as a script block in a local variable.</span></span>
<span data-ttu-id="f900c-174">Wanneer het scriptblok wordt opgeslagen in een lokale variabele, kunt u de variabele opgeven als de waarde van de parameter **ScriptBlock.**</span><span class="sxs-lookup"><span data-stu-id="f900c-174">When the script block is saved in a local variable, you can specify the variable as the value of the **ScriptBlock** parameter.</span></span>

```powershell
$command = { Get-WinEvent -LogName PowerShellCore/Operational |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

<span data-ttu-id="f900c-175">De `$command` variabele slaat de opdracht op die is opgemaakt als een `Get-WinEvent` scriptblok.</span><span class="sxs-lookup"><span data-stu-id="f900c-175">The `$command` variable stores the `Get-WinEvent` command that's formatted as a script block.</span></span> <span data-ttu-id="f900c-176">De `Invoke-Command` voert de opdracht uit die is opgeslagen in op de externe computers `$command` S1 en S2.</span><span class="sxs-lookup"><span data-stu-id="f900c-176">The `Invoke-Command` runs the command stored in `$command` on the S1 and S2 remote computers.</span></span>

### <span data-ttu-id="f900c-177">Voorbeeld 6: Een enkele opdracht uitvoeren op verschillende computers</span><span class="sxs-lookup"><span data-stu-id="f900c-177">Example 6: Run a single command on several computers</span></span>

<span data-ttu-id="f900c-178">In dit voorbeeld wordt gedemonstreerd hoe `Invoke-Command` u gebruikt om één opdracht uit te voeren op meerdere computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-178">This example demonstrates how to use `Invoke-Command` to run a single command on multiple computers.</span></span>

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-WinEvent -LogName PowerShellCore/Operational }
}
Invoke-Command @parameters
```

<span data-ttu-id="f900c-179">De **ComputerName** parameter geeft u een door komma's gescheiden lijst met computernamen.</span><span class="sxs-lookup"><span data-stu-id="f900c-179">The **ComputerName** parameter specifies a comma-separated list of computer names.</span></span> <span data-ttu-id="f900c-180">De lijst met computers bevat de localhost-waarde, die de lokale computer vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f900c-180">The list of computers includes the localhost value, which represents the local computer.</span></span> <span data-ttu-id="f900c-181">De **ConfigurationName** parameter geeft u een alternatieve sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="f900c-181">The **ConfigurationName** parameter specifies an alternate session configuration.</span></span> <span data-ttu-id="f900c-182">De **parameter ScriptBlock** wordt uitgevoerd `Get-WinEvent` om de gebeurtenislogboeken van PowerShellCore/Operational op te halen van elke computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-182">The **ScriptBlock** parameter runs `Get-WinEvent` to get the PowerShellCore/Operational event logs from each computer.</span></span>

### <span data-ttu-id="f900c-183">Voorbeeld 7: de versie van het hostprogramma op meerdere computers op halen</span><span class="sxs-lookup"><span data-stu-id="f900c-183">Example 7: Get the version of the host program on multiple computers</span></span>

<span data-ttu-id="f900c-184">In dit voorbeeld wordt de versie van het PowerShell-hostprogramma op 200 externe computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-184">This example gets the version of the PowerShell host program running on 200 remote computers.</span></span>

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

<span data-ttu-id="f900c-185">Omdat er slechts één opdracht wordt uitgevoerd, hoeft u geen permanente verbindingen met elk van de computers te maken.</span><span class="sxs-lookup"><span data-stu-id="f900c-185">Because only one command is run, you don't have to create persistent connections to each of the computers.</span></span> <span data-ttu-id="f900c-186">In plaats daarvan gebruikt de opdracht de **Parameter ComputerName** om de computers aan te geven.</span><span class="sxs-lookup"><span data-stu-id="f900c-186">Instead, the command uses the **ComputerName** parameter to indicate the computers.</span></span> <span data-ttu-id="f900c-187">Als u de computers wilt opgeven, wordt de cmdlet gebruikt om de inhoud van het Machine.txt op te halen, een bestand `Get-Content` met computernamen.</span><span class="sxs-lookup"><span data-stu-id="f900c-187">To specify the computers, it uses the `Get-Content` cmdlet to get the contents of the Machine.txt file, a file of computer names.</span></span>

<span data-ttu-id="f900c-188">De `Invoke-Command` cmdlet voert een `Get-Host` opdracht uit op de externe computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-188">The `Invoke-Command` cmdlet runs a `Get-Host` command on the remote computers.</span></span> <span data-ttu-id="f900c-189">Er wordt een punt-notatie gebruikt om de **eigenschap Version van** de PowerShell-host op te halen.</span><span class="sxs-lookup"><span data-stu-id="f900c-189">It uses dot notation to get the **Version** property of the PowerShell host.</span></span>

<span data-ttu-id="f900c-190">Deze opdrachten worden één voor één uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-190">These commands run one at a time.</span></span> <span data-ttu-id="f900c-191">Wanneer de opdrachten zijn voltooid, wordt de uitvoer van de opdrachten van alle computers opgeslagen in de `$version` variabele .</span><span class="sxs-lookup"><span data-stu-id="f900c-191">When the commands complete, the output of the commands from all of the computers is saved in the `$version` variable.</span></span> <span data-ttu-id="f900c-192">De uitvoer bevat de naam van de computer van waaruit de gegevens afkomstig zijn.</span><span class="sxs-lookup"><span data-stu-id="f900c-192">The output includes the name of the computer from which the data originated.</span></span>

### <span data-ttu-id="f900c-193">Voorbeeld 8: een achtergrond taak uitvoeren op verschillende externe computers</span><span class="sxs-lookup"><span data-stu-id="f900c-193">Example 8: Run a background job on several remote computers</span></span>

<span data-ttu-id="f900c-194">In dit voorbeeld wordt een opdracht uitgevoerd op twee externe computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-194">This example runs a command on two remote computers.</span></span> <span data-ttu-id="f900c-195">De `Invoke-Command` opdracht maakt gebruik van de Parameter **AsJob** zodat de opdracht wordt uitgevoerd als een achtergrond job.</span><span class="sxs-lookup"><span data-stu-id="f900c-195">The `Invoke-Command` command uses the **AsJob** parameter so that the command runs as a background job.</span></span> <span data-ttu-id="f900c-196">De opdrachten worden uitgevoerd op de externe computers, maar de taak bestaat op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-196">The commands run on the remote computers, but the job exists on the local computer.</span></span> <span data-ttu-id="f900c-197">De resultaten worden verzonden naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-197">The results are transmitted to the local computer.</span></span>

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

<span data-ttu-id="f900c-198">De `New-PSSession` cmdlet maakt sessies op de externe computers Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="f900c-198">The `New-PSSession` cmdlet creates sessions on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="f900c-199">De `Invoke-Command` cmdlet voert in elk van de sessies een achtergrond job uit.</span><span class="sxs-lookup"><span data-stu-id="f900c-199">The `Invoke-Command` cmdlet runs a background job in each of the sessions.</span></span> <span data-ttu-id="f900c-200">De opdracht gebruikt de **parameter AsJob** om de opdracht uit te voeren als achtergrondjob.</span><span class="sxs-lookup"><span data-stu-id="f900c-200">The command uses the **AsJob** parameter to run the command as a background job.</span></span> <span data-ttu-id="f900c-201">Deze opdracht retourneert een taakobject dat twee onderliggende taakobjecten bevat, één voor elk van de taken die op de twee externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-201">This command returns a job object that contains two child job objects, one for each of the jobs run on the two remote computers.</span></span>

<span data-ttu-id="f900c-202">De `Get-Job` opdracht slaat het taakobject op in de variabele `$j` .</span><span class="sxs-lookup"><span data-stu-id="f900c-202">The `Get-Job` command saves the job object in the `$j` variable.</span></span> <span data-ttu-id="f900c-203">De `$j` variabele wordt vervolgens doorspijpt naar de cmdlet om alle eigenschappen van het `Format-List` taakobject in een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f900c-203">The `$j` variable is then piped to the `Format-List` cmdlet to display all properties of the job object in a list.</span></span> <span data-ttu-id="f900c-204">De laatste opdracht haalt de resultaten van de taken op.</span><span class="sxs-lookup"><span data-stu-id="f900c-204">The last command gets the results of the jobs.</span></span> <span data-ttu-id="f900c-205">Het taakobject wordt naar de `$j` `Receive-Job` cmdlet doorgespijpt en de resultaten worden opgeslagen in de `$results` variabele .</span><span class="sxs-lookup"><span data-stu-id="f900c-205">It pipes the job object in `$j` to the `Receive-Job` cmdlet and stores the results in the `$results` variable.</span></span>

### <span data-ttu-id="f900c-206">Voorbeeld 9: lokale variabelen opnemen in een opdracht die wordt uitgevoerd op een externe computer</span><span class="sxs-lookup"><span data-stu-id="f900c-206">Example 9: Include local variables in a command run on a remote computer</span></span>

<span data-ttu-id="f900c-207">In dit voorbeeld ziet u hoe u de waarden van lokale variabelen op te nemen in een opdracht die wordt uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-207">This example shows how to include the values of local variables in a command run on a remote computer.</span></span> <span data-ttu-id="f900c-208">De opdracht maakt gebruik van `Using` de scope-modifier om een lokale variabele in een externe opdracht te identificeren.</span><span class="sxs-lookup"><span data-stu-id="f900c-208">The command uses the `Using` scope modifier to identify a local variable in a remote command.</span></span> <span data-ttu-id="f900c-209">Standaard wordt aangenomen dat alle variabelen worden gedefinieerd in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-209">By default, all variables are assumed to be defined in the remote session.</span></span> <span data-ttu-id="f900c-210">De `Using` scope-modifier is geïntroduceerd in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f900c-210">The `Using` scope modifier was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="f900c-211">Zie voor meer informatie over `Using` de scope-modifier [about_Remote_Variables](./About/about_Remote_Variables.md) en [about_Scopes.](./about/about_scopes.md)</span><span class="sxs-lookup"><span data-stu-id="f900c-211">For more information about the `Using` scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md) and [about_Scopes](./about/about_scopes.md).</span></span>

```powershell
$Log = "PowerShellCore/Operational"
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-WinEvent -LogName $Using:Log -MaxEvents 10}
```

<span data-ttu-id="f900c-212">De `$Log` variabele slaat de naam op van het gebeurtenislogboek, PowerShellCore/Operational.</span><span class="sxs-lookup"><span data-stu-id="f900c-212">The `$Log` variable stores the name of the event log, PowerShellCore/Operational.</span></span> <span data-ttu-id="f900c-213">De `Invoke-Command` cmdlet wordt uitgevoerd op Server01 om de tien nieuwste gebeurtenissen uit `Get-WinEvent` het gebeurtenislogboek op te halen.</span><span class="sxs-lookup"><span data-stu-id="f900c-213">The `Invoke-Command` cmdlet runs `Get-WinEvent` on Server01 to get the ten newest events from the event log.</span></span> <span data-ttu-id="f900c-214">De waarde van de **LogName** parameter is de variabele die wordt voorafgemaakt door de bereik modifier om aan te geven dat deze is gemaakt in de lokale sessie, niet in de `$Log` `Using` externe sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-214">The value of the **LogName** parameter is the `$Log` variable that is prefixed by the `Using` scope modifier to indicate that it was created in the local session, not in the remote session.</span></span>

### <span data-ttu-id="f900c-215">Voorbeeld 10: de computernaam verbergen</span><span class="sxs-lookup"><span data-stu-id="f900c-215">Example 10: Hide the computer name</span></span>

<span data-ttu-id="f900c-216">In dit voorbeeld ziet u het effect van het gebruik van de parameter **HideComputerName** van `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="f900c-216">This example shows the effect of using the **HideComputerName** parameter of `Invoke-Command`.</span></span>
<span data-ttu-id="f900c-217">**HideComputerName** wijzigt het object dat deze cmdlet retourneert niet.</span><span class="sxs-lookup"><span data-stu-id="f900c-217">**HideComputerName** doesn't change the object that this cmdlet returns.</span></span> <span data-ttu-id="f900c-218">Alleen de weergave wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f900c-218">It changes only the display.</span></span> <span data-ttu-id="f900c-219">U kunt nog  steeds de Opmaak-cmdlets gebruiken om de eigenschap **PsComputerName** van een van de betrokken objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f900c-219">You can still use the **Format** cmdlets to display the **PsComputerName** property of any of the affected objects.</span></span>

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

<span data-ttu-id="f900c-220">De eerste twee opdrachten gebruiken om `Invoke-Command` een opdracht uit te voeren voor het `Get-Process` PowerShell-proces.</span><span class="sxs-lookup"><span data-stu-id="f900c-220">The first two commands use `Invoke-Command` to run a `Get-Process` command for the PowerShell process.</span></span> <span data-ttu-id="f900c-221">De uitvoer van de eerste opdracht bevat de eigenschap **PsComputerName,** die de naam bevat van de computer waarop de opdracht is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-221">The output of the first command includes the **PsComputerName** property, which contains the name of the computer on which the command ran.</span></span> <span data-ttu-id="f900c-222">De uitvoer van de tweede opdracht, die **gebruikmaakt van HideComputerName,** bevat niet de **kolom PsComputerName.**</span><span class="sxs-lookup"><span data-stu-id="f900c-222">The output of the second command, which uses **HideComputerName**, doesn't include the **PsComputerName** column.</span></span>

### <span data-ttu-id="f900c-223">Voorbeeld 11: Het sleutelwoord Param gebruiken in een scriptblok</span><span class="sxs-lookup"><span data-stu-id="f900c-223">Example 11: Use the Param keyword in a script block</span></span>

<span data-ttu-id="f900c-224">Het `Param` trefwoord en de **parameter ArgumentList** worden gebruikt om variabele waarden door te geven aan benoemde parameters in een scriptblok.</span><span class="sxs-lookup"><span data-stu-id="f900c-224">The `Param` keyword and the **ArgumentList** parameter are used to pass variable values to named parameters in a script block.</span></span> <span data-ttu-id="f900c-225">In dit voorbeeld worden bestandsnamen weergegeven die beginnen met de letter `a` en de extensie `.pdf` hebben.</span><span class="sxs-lookup"><span data-stu-id="f900c-225">This example displays filenames that begin with the letter `a` and have the `.pdf` extension.</span></span>

<span data-ttu-id="f900c-226">Zie voor meer informatie over `Param` het [trefwoord about_Language_Keywords](./about/about_language_keywords.md#param).</span><span class="sxs-lookup"><span data-stu-id="f900c-226">For more information about the `Param` keyword, see [about_Language_Keywords](./about/about_language_keywords.md#param).</span></span>

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

<span data-ttu-id="f900c-227">`Invoke-Command` gebruikt de **parameter ScriptBlock** die twee variabelen definieert, `$param1` en `$param2` .</span><span class="sxs-lookup"><span data-stu-id="f900c-227">`Invoke-Command` uses the **ScriptBlock** parameter that defines two variables, `$param1` and `$param2`.</span></span> <span data-ttu-id="f900c-228">`Get-ChildItem` maakt gebruik van de benoemde **parameters, Naam** **en Opnemen** met de namen van variabelen.</span><span class="sxs-lookup"><span data-stu-id="f900c-228">`Get-ChildItem` uses the named parameters, **Name** and **Include** with the variable names.</span></span> <span data-ttu-id="f900c-229">De **ArgumentList** geeft de waarden door aan de variabelen.</span><span class="sxs-lookup"><span data-stu-id="f900c-229">The **ArgumentList** passes the values to the variables.</span></span>

### <span data-ttu-id="f900c-230">Voorbeeld 12: De automatische $args in een scriptblok gebruiken</span><span class="sxs-lookup"><span data-stu-id="f900c-230">Example 12: Use the $args automatic variable in a script block</span></span>

<span data-ttu-id="f900c-231">De automatische variabele en de parameter ArgumentList worden gebruikt om matrixwaarden door te geven aan `$args` parameterposities  in een scriptblok.</span><span class="sxs-lookup"><span data-stu-id="f900c-231">The `$args` automatic variable and the **ArgumentList** parameter are used to pass array values to parameter positions in a script block.</span></span> <span data-ttu-id="f900c-232">In dit voorbeeld wordt de mapinhoud van bestanden van een `.txt` server weergegeven.</span><span class="sxs-lookup"><span data-stu-id="f900c-232">This example displays a server's directory contents of `.txt` files.</span></span> <span data-ttu-id="f900c-233">De `Get-ChildItem` **parameter Path** is positie 0 en de **filterparameter** is positie</span><span class="sxs-lookup"><span data-stu-id="f900c-233">The `Get-ChildItem` **Path** parameter is position 0 and the **Filter** parameter is position</span></span>
1.

<span data-ttu-id="f900c-234">Zie voor meer informatie `$args` over de [variabele about_Automatic_Variables](./about/about_automatic_variables.md#args)</span><span class="sxs-lookup"><span data-stu-id="f900c-234">For more information about the `$args` variable, see [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span></span>

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

<span data-ttu-id="f900c-235">`Invoke-Command` gebruikt een **ScriptBlock-parameter** en `Get-ChildItem` geeft de `$args[0]` matrixwaarden en `$args[1]` op.</span><span class="sxs-lookup"><span data-stu-id="f900c-235">`Invoke-Command` uses a **ScriptBlock** parameter and `Get-ChildItem` specifies the `$args[0]` and `$args[1]` array values.</span></span> <span data-ttu-id="f900c-236">De **ArgumentList geeft** de `$args` matrixwaarden door aan de `Get-ChildItem` parameterposities **voor Pad** en **Filter.**</span><span class="sxs-lookup"><span data-stu-id="f900c-236">The **ArgumentList** passes the `$args` array values to the `Get-ChildItem` parameter positions for **Path** and **Filter**.</span></span>

### <span data-ttu-id="f900c-237">Voorbeeld 13: Een script uitvoeren op alle computers die worden vermeld in een tekstbestand</span><span class="sxs-lookup"><span data-stu-id="f900c-237">Example 13: Run a script on all the computers listed in a text file</span></span>

<span data-ttu-id="f900c-238">In dit voorbeeld wordt de `Invoke-Command` cmdlet gebruikt om het `Sample.ps1` script uit te voeren op alle computers die in het bestand worden `Servers.txt` vermeld.</span><span class="sxs-lookup"><span data-stu-id="f900c-238">This example uses the `Invoke-Command` cmdlet to run the `Sample.ps1` script on all the computers listed in the `Servers.txt` file.</span></span> <span data-ttu-id="f900c-239">De opdracht gebruikt de **parameter FilePath** om het scriptbestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="f900c-239">The command uses the **FilePath** parameter to specify the script file.</span></span> <span data-ttu-id="f900c-240">Met deze opdracht kunt u het script uitvoeren op de externe computers, zelfs als het scriptbestand niet toegankelijk is voor de externe computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-240">This command lets you run the script on the remote computers, even if the script file isn't accessible to the remote computers.</span></span>

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

<span data-ttu-id="f900c-241">Wanneer u de opdracht indient, wordt de inhoud van het bestand gekopieerd naar een scriptblok en wordt het `Sample.ps1` scriptblok uitgevoerd op elk van de externe computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-241">When you submit the command, the content of the `Sample.ps1` file is copied into a script block and the script block is run on each of the remote computers.</span></span> <span data-ttu-id="f900c-242">Deze procedure is gelijk aan het gebruik van de parameter **ScriptBlock** om de inhoud van het script in te dienen.</span><span class="sxs-lookup"><span data-stu-id="f900c-242">This procedure is equivalent to using the **ScriptBlock** parameter to submit the contents of the script.</span></span>

### <span data-ttu-id="f900c-243">Voorbeeld 14: Een opdracht uitvoeren op een externe computer met behulp van een URI</span><span class="sxs-lookup"><span data-stu-id="f900c-243">Example 14: Run a command on a remote computer using a URI</span></span>

<span data-ttu-id="f900c-244">In dit voorbeeld ziet u hoe u een opdracht kunt uitvoeren op een externe computer die wordt geïdentificeerd door een Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="f900c-244">This example shows how to run a command on a remote computer that's identified by a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="f900c-245">In dit specifieke voorbeeld wordt een `Set-Mailbox` opdracht uitgevoerd op een externe Exchange-server.</span><span class="sxs-lookup"><span data-stu-id="f900c-245">This particular example runs a `Set-Mailbox` command on a remote Exchange server.</span></span>

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

<span data-ttu-id="f900c-246">De eerste regel maakt gebruik van `Get-Credential` de cmdlet voor het opslaan van Windows Live ID-referenties in de `$LiveCred` variabele .</span><span class="sxs-lookup"><span data-stu-id="f900c-246">The first line uses the `Get-Credential` cmdlet to store Windows Live ID credentials in the `$LiveCred` variable.</span></span> <span data-ttu-id="f900c-247">PowerShell vraagt de gebruiker om Windows Live ID-referenties in te voeren.</span><span class="sxs-lookup"><span data-stu-id="f900c-247">PowerShell prompts the user to enter Windows Live ID credentials.</span></span>

<span data-ttu-id="f900c-248">De `$parameters` variabele is een hashtabel met de parameters die moeten worden doorgegeven aan de `Invoke-Command` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="f900c-248">The `$parameters` variable is a hash table containing the parameters to be passed to the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="f900c-249">De `Invoke-Command` cmdlet voert een opdracht `Set-Mailbox` uit met behulp van de **sessieconfiguratie Microsoft.Exchange.**</span><span class="sxs-lookup"><span data-stu-id="f900c-249">The `Invoke-Command` cmdlet runs a `Set-Mailbox` command using the **Microsoft.Exchange** session configuration.</span></span> <span data-ttu-id="f900c-250">Met **de parameter ConnectionURI** wordt de URL van het Exchange-server-eindpunt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f900c-250">The **ConnectionURI** parameter specifies the URL of the Exchange server endpoint.</span></span> <span data-ttu-id="f900c-251">De **referentie** parameter geeft u de referenties die zijn opgeslagen in de `$LiveCred` variabele.</span><span class="sxs-lookup"><span data-stu-id="f900c-251">The **Credential** parameter specifies the credentials stored in the `$LiveCred` variable.</span></span> <span data-ttu-id="f900c-252">De **AuthenticationMechanism** parameter geeft u het gebruik van basisverificatie.</span><span class="sxs-lookup"><span data-stu-id="f900c-252">The **AuthenticationMechanism** parameter specifies the use of basic authentication.</span></span> <span data-ttu-id="f900c-253">Met de parameter **ScriptBlock** geeft u een scriptblok op dat de opdracht bevat.</span><span class="sxs-lookup"><span data-stu-id="f900c-253">The **ScriptBlock** parameter specifies a script block that contains the command.</span></span>

### <span data-ttu-id="f900c-254">Voorbeeld 15: Een sessieoptie gebruiken</span><span class="sxs-lookup"><span data-stu-id="f900c-254">Example 15: Use a session option</span></span>

<span data-ttu-id="f900c-255">In dit voorbeeld ziet u hoe u een **SessionOption-parameter maakt en** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f900c-255">This example shows how to create and use a **SessionOption** parameter.</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

<span data-ttu-id="f900c-256">De cmdlet maakt een sessieoptieobject dat ervoor zorgt dat de externe end de certificeringsinstantie, canonieke naam en intrekkingslijsten niet verifieert tijdens het evalueren van de binnenkomende `New-PSSessionOption` HTTPS-verbinding.</span><span class="sxs-lookup"><span data-stu-id="f900c-256">The `New-PSSessionOption` cmdlet creates a session option object that causes the remote end not to verify the Certificate Authority, Canonical Name, and Revocation Lists while evaluating the incoming HTTPS connection.</span></span> <span data-ttu-id="f900c-257">Het **object SessionOption** wordt opgeslagen in de `$so` variabele .</span><span class="sxs-lookup"><span data-stu-id="f900c-257">The **SessionOption** object is saved in the `$so` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="f900c-258">Het uitschakelen van deze controles is handig voor het oplossen van problemen, maar is natuurlijk niet veilig.</span><span class="sxs-lookup"><span data-stu-id="f900c-258">Disabling these checks is convenient for troubleshooting, but obviously not secure.</span></span>

<span data-ttu-id="f900c-259">De `Invoke-Command` cmdlet voert een `Get-HotFix` opdracht op afstand uit.</span><span class="sxs-lookup"><span data-stu-id="f900c-259">The `Invoke-Command` cmdlet runs a `Get-HotFix` command remotely.</span></span> <span data-ttu-id="f900c-260">De **parameter SessionOption** krijgt de `$so` variabele .</span><span class="sxs-lookup"><span data-stu-id="f900c-260">The **SessionOption** parameter is given the `$so` variable.</span></span>

### <span data-ttu-id="f900c-261">Voorbeeld 16: URI-omleiding beheren in een externe opdracht</span><span class="sxs-lookup"><span data-stu-id="f900c-261">Example 16: Manage URI redirection in a remote command</span></span>

<span data-ttu-id="f900c-262">In dit voorbeeld ziet u hoe u de **parameters AllowRedirection** en **SessionOption** gebruikt voor het beheren van URI-omleiding in een externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-262">This example shows how to use the **AllowRedirection** and **SessionOption** parameters to manage URI redirection in a remote command.</span></span>

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

<span data-ttu-id="f900c-263">De `New-PSSessionOption` cmdlet maakt een **PSSessionOption-object** dat wordt opgeslagen in de `$max` variabele .</span><span class="sxs-lookup"><span data-stu-id="f900c-263">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object that is saved in the `$max` variable.</span></span> <span data-ttu-id="f900c-264">De opdracht gebruikt de **parameter MaximumRedirection** om de eigenschap **MaximumConnectionRedirectionCount** van het **PSSessionOption-object** in te stellen op 1.</span><span class="sxs-lookup"><span data-stu-id="f900c-264">The command uses the **MaximumRedirection** parameter to set the **MaximumConnectionRedirectionCount** property of the **PSSessionOption** object to 1.</span></span>

<span data-ttu-id="f900c-265">De `Invoke-Command` cmdlet voert een `Get-Mailbox` opdracht uit op een externe Microsoft Exchange-server.</span><span class="sxs-lookup"><span data-stu-id="f900c-265">The `Invoke-Command` cmdlet runs a `Get-Mailbox` command on a remote Microsoft Exchange Server.</span></span> <span data-ttu-id="f900c-266">De **parameter AllowRedirection** biedt expliciete machtigingen om de verbinding om te leiden naar een alternatief eindpunt.</span><span class="sxs-lookup"><span data-stu-id="f900c-266">The **AllowRedirection** parameter provides explicit permission to redirect the connection to an alternate endpoint.</span></span> <span data-ttu-id="f900c-267">De **parameter SessionOption** maakt gebruik van het sessieobject dat is opgeslagen in de `$max` variabele .</span><span class="sxs-lookup"><span data-stu-id="f900c-267">The **SessionOption** parameter uses the session object stored in the `$max` variable.</span></span>

<span data-ttu-id="f900c-268">Als gevolg hiervan, als de externe computer die is opgegeven door **ConnectionURI** een omleidingsbericht retourneert, wordt de verbinding door PowerShell omgeleid, maar als de nieuwe bestemming een ander omleidingsbericht retourneert, wordt de waarde van het aantal omleidingen van 1 overschreden en wordt een `Invoke-Command` niet-beëindigingsfout retourneert.</span><span class="sxs-lookup"><span data-stu-id="f900c-268">As a result, if the remote computer specified by **ConnectionURI** returns a redirection message, PowerShell redirects the connection, but if the new destination returns another redirection message, the redirection count value of 1 is exceeded, and `Invoke-Command` returns a non-terminating error.</span></span>

### <span data-ttu-id="f900c-269">Voorbeeld 17: Toegang tot een netwerk share in een externe sessie</span><span class="sxs-lookup"><span data-stu-id="f900c-269">Example 17: Access a network share in a remote session</span></span>

<span data-ttu-id="f900c-270">In dit voorbeeld ziet u hoe u toegang krijgt tot een netwerk share vanuit een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-270">This example shows how to access a network share from a remote session.</span></span> <span data-ttu-id="f900c-271">Er worden drie computers gebruikt om het voorbeeld te demonstreren.</span><span class="sxs-lookup"><span data-stu-id="f900c-271">Three computers are used to demonstrate the example.</span></span> <span data-ttu-id="f900c-272">Server01 is de lokale computer, Server02 is de externe computer en Net03 bevat de netwerk share.</span><span class="sxs-lookup"><span data-stu-id="f900c-272">Server01 is the local computer, Server02 is the remote computer, and Net03 contains the network share.</span></span> <span data-ttu-id="f900c-273">Server01 maakt verbinding met Server02 en server02 maakt vervolgens een tweede hop naar Net03 om toegang te krijgen tot de netwerk share.</span><span class="sxs-lookup"><span data-stu-id="f900c-273">Server01 connects to Server02, and then Server02 does a second hop to Net03 to access the network share.</span></span> <span data-ttu-id="f900c-274">Zie Making the second hop in PowerShell Remoting (De tweede [hop maken in Remoting van PowerShell) voor meer](/powershell/scripting/learn/remoting/ps-remoting-second-hop)informatie over hoe remoting van PowerShell hops tussen computers ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="f900c-274">For more information about how PowerShell Remoting supports hops between computers, see [Making the second hop in PowerShell Remoting](/powershell/scripting/learn/remoting/ps-remoting-second-hop).</span></span>

<span data-ttu-id="f900c-275">De vereiste credSSP-delegering (Credential Security Support Provider) wordt ingeschakeld in de clientinstellingen op de lokale computer en in de service-instellingen op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-275">The required Credential Security Support Provider (CredSSP) delegation is enabled in the client settings on the local computer, and in the service settings on the remote computer.</span></span> <span data-ttu-id="f900c-276">Als u de opdrachten in dit voorbeeld wilt uitvoeren, moet u lid zijn van de groep **Administrators** op de lokale computer en de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-276">To run the commands in this example, you must be a member of the **Administrators** group on the local computer and the remote computer.</span></span>

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

<span data-ttu-id="f900c-277">De `Enable-WSManCredSSP` cmdlet schakelt CredSSP-overdracht van de lokale computer Server01 naar de externe computer Server02.</span><span class="sxs-lookup"><span data-stu-id="f900c-277">The `Enable-WSManCredSSP` cmdlet enables CredSSP delegation from the Server01 local computer to the Server02 remote computer.</span></span> <span data-ttu-id="f900c-278">De **rol** parameter geeft u **client voor** het configureren van de CredSSP-clientinstelling op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-278">The **Role** parameter specifies **Client** to configure the CredSSP client setting on the local computer.</span></span>

<span data-ttu-id="f900c-279">`New-PSSession` maakt een **PSSession-object** voor Server02 en slaat het object op in de `$s` variabele .</span><span class="sxs-lookup"><span data-stu-id="f900c-279">`New-PSSession` creates a **PSSession** object for Server02 and stores the object in the `$s` variable.</span></span>

<span data-ttu-id="f900c-280">De `Invoke-Command` cmdlet gebruikt de `$s` variabele om verbinding te maken met de externe computer Server02.</span><span class="sxs-lookup"><span data-stu-id="f900c-280">The `Invoke-Command` cmdlet uses the `$s` variable to connect to the remote computer, Server02.</span></span> <span data-ttu-id="f900c-281">De **ScriptBlock** parameter wordt `Enable-WSManCredSSP` uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-281">The **ScriptBlock** parameter runs `Enable-WSManCredSSP` on the remote computer.</span></span> <span data-ttu-id="f900c-282">De **rol** parameter geeft u **Server** voor het configureren van de CredSSP-serverinstelling op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-282">The **Role** parameter specifies **Server** to configure the CredSSP server setting on the remote computer.</span></span>

<span data-ttu-id="f900c-283">De `$parameters` variabele bevat de parameterwaarden om verbinding te maken met de netwerk share.</span><span class="sxs-lookup"><span data-stu-id="f900c-283">The `$parameters` variable contains the parameter values to connect to the network share.</span></span> <span data-ttu-id="f900c-284">De `Invoke-Command` cmdlet voert een `Get-Item` opdracht uit in de sessie in `$s` .</span><span class="sxs-lookup"><span data-stu-id="f900c-284">The `Invoke-Command` cmdlet runs a `Get-Item` command in the session in `$s`.</span></span> <span data-ttu-id="f900c-285">Met deze opdracht haalt u een script op uit de `\\Net03\Scripts` netwerk share.</span><span class="sxs-lookup"><span data-stu-id="f900c-285">This command gets a script from the `\\Net03\Scripts` network share.</span></span> <span data-ttu-id="f900c-286">De opdracht gebruikt de **verificatie** parameter met de waarde van **CredSSP en** de **referentie** parameter met de waarde **van Domain01\Admin01.**</span><span class="sxs-lookup"><span data-stu-id="f900c-286">The command uses the **Authentication** parameter with a value of **CredSSP** and the **Credential** parameter with a value of **Domain01\Admin01**.</span></span>

### <span data-ttu-id="f900c-287">Voorbeeld 18: Scripts starten op veel externe computers</span><span class="sxs-lookup"><span data-stu-id="f900c-287">Example 18: Start scripts on many remote computers</span></span>

<span data-ttu-id="f900c-288">In dit voorbeeld wordt een script uitgevoerd op meer dan honderd computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-288">This example runs a script on more than a hundred computers.</span></span> <span data-ttu-id="f900c-289">Om de impact op de lokale computer te minimaliseren, maakt deze verbinding met elke computer, start het script en wordt vervolgens de verbinding met elke computer verbroken.</span><span class="sxs-lookup"><span data-stu-id="f900c-289">To minimize the impact on the local computer, it connects to each computer, starts the script, and then disconnects from each computer.</span></span>
<span data-ttu-id="f900c-290">Het script blijft worden uitgevoerd in de niet-verbonden sessies.</span><span class="sxs-lookup"><span data-stu-id="f900c-290">The script continues to run in the disconnected sessions.</span></span>

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

<span data-ttu-id="f900c-291">De opdracht gebruikt om `Invoke-Command` het script uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f900c-291">The command uses `Invoke-Command` to run the script.</span></span> <span data-ttu-id="f900c-292">De waarde van de **ComputerName** parameter is een opdracht die de namen van de externe `Get-Content` computers uit een tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="f900c-292">The value of the **ComputerName** parameter is a `Get-Content` command that gets the names of the remote computers from a text file.</span></span> <span data-ttu-id="f900c-293">Met de parameter **InDisconnectedSession** worden de sessies verbroken zodra de opdracht wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="f900c-293">The **InDisconnectedSession** parameter disconnects the sessions as soon as it starts the command.</span></span> <span data-ttu-id="f900c-294">De waarde van de **FilePath** parameter is het script dat `Invoke-Command` wordt uitgevoerd op elke computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-294">The value of the **FilePath** parameter is the script that `Invoke-Command` runs on each computer.</span></span>

<span data-ttu-id="f900c-295">De waarde van **SessionOption** is een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="f900c-295">The value of **SessionOption** is a hash table.</span></span> <span data-ttu-id="f900c-296">De **waarde OutputBufferingMode** is ingesteld op **Drop** en de **waarde IdleTimeout** op **43200000** milliseconden (12 uur).</span><span class="sxs-lookup"><span data-stu-id="f900c-296">The **OutputBufferingMode** value is set to **Drop** and the **IdleTimeout** value is set to **43200000** milliseconds (12 hours).</span></span>

<span data-ttu-id="f900c-297">Gebruik de cmdlet om de resultaten op te halen van opdrachten en scripts die worden uitgevoerd in niet-verbonden `Receive-PSSession` sessies.</span><span class="sxs-lookup"><span data-stu-id="f900c-297">To get the results of commands and scripts that run in disconnected sessions, use the `Receive-PSSession` cmdlet.</span></span>

### <span data-ttu-id="f900c-298">Voorbeeld 19: een opdracht uitvoeren op een externe computer met behulp van SSH</span><span class="sxs-lookup"><span data-stu-id="f900c-298">Example 19: Run a command on a remote computer using SSH</span></span>

<span data-ttu-id="f900c-299">In dit voorbeeld ziet u hoe u een opdracht kunt uitvoeren op een externe computer met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="f900c-299">This example shows how to run a command on a remote computer using Secure Shell (SSH).</span></span> <span data-ttu-id="f900c-300">Als SSH is geconfigureerd op de externe computer om te vragen om wachtwoorden, krijgt u een wachtwoordprompt.</span><span class="sxs-lookup"><span data-stu-id="f900c-300">If SSH is configured on the remote computer to prompt for passwords, then you'll get a password prompt.</span></span>
<span data-ttu-id="f900c-301">Anders moet u gebruikersverificatie op basis van een SSH-sleutel gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f900c-301">Otherwise, you'll have to use SSH key-based user authentication.</span></span>

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * }
```

### <span data-ttu-id="f900c-302">Voorbeeld 20: een opdracht uitvoeren op een externe computer met behulp van SSH en een sleutel voor gebruikersverificatie opgeven</span><span class="sxs-lookup"><span data-stu-id="f900c-302">Example 20: Run a command on a remote computer using SSH and specify a user authentication key</span></span>

<span data-ttu-id="f900c-303">In dit voorbeeld ziet u hoe u een opdracht op een externe computer kunt uitvoeren met behulp van SSH en een sleutelbestand voor gebruikersverificatie kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="f900c-303">This example shows how to run a command on a remote computer using SSH and specifying a key file for user authentication.</span></span> <span data-ttu-id="f900c-304">U wordt niet om een wachtwoord gevraagd, tenzij de sleutelverificatie mislukt en de externe computer is geconfigureerd om eenvoudige wachtwoordverificatie toe te staan.</span><span class="sxs-lookup"><span data-stu-id="f900c-304">You won't be prompted for a password unless the key authentication fails and the remote computer is configured to allow basic password authentication.</span></span>

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * } -KeyFilePath /UserA/UserAKey_rsa
```

### <span data-ttu-id="f900c-305">Voorbeeld 21: Een scriptbestand uitvoeren op meerdere externe computers met SSH als taak</span><span class="sxs-lookup"><span data-stu-id="f900c-305">Example 21: Run a script file on multiple remote computers using SSH as a job</span></span>

<span data-ttu-id="f900c-306">In dit voorbeeld ziet u hoe u een scriptbestand op meerdere externe computers kunt uitvoeren met behulp van SSH en de **parameterset SSHConnection.**</span><span class="sxs-lookup"><span data-stu-id="f900c-306">This example shows how to run a script file on multiple remote computers using SSH and the **SSHConnection** parameter set.</span></span> <span data-ttu-id="f900c-307">De **parameter SSHConnection** maakt gebruik van een matrix met hashtabellen die verbindingsgegevens voor elke computer bevatten.</span><span class="sxs-lookup"><span data-stu-id="f900c-307">The **SSHConnection** parameter takes an array of hash tables that contain connection information for each computer.</span></span> <span data-ttu-id="f900c-308">Voor dit voorbeeld is vereist dat op de externe doelcomputers SSH is geconfigureerd ter ondersteuning van op sleutels gebaseerde gebruikersverificatie.</span><span class="sxs-lookup"><span data-stu-id="f900c-308">This example requires that the target remote computers have SSH configured to support key-based user authentication.</span></span>

```powershell
$sshConnections =
@{ HostName="WinServer1"; UserName="Domain\UserA"; KeyFilePath="C:\Users\UserA\id_rsa" },
@{ HostName="UserB@LinuxServer5"; KeyFilePath="/Users/UserB/id_rsa" }
$results = Invoke-Command -FilePath c:\Scripts\CollectEvents.ps1 -SSHConnection $sshConnections
```

## <span data-ttu-id="f900c-309">Parameters</span><span class="sxs-lookup"><span data-stu-id="f900c-309">Parameters</span></span>

### <span data-ttu-id="f900c-310">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="f900c-310">-AllowRedirection</span></span>

<span data-ttu-id="f900c-311">Staat omleiding van deze verbinding naar een alternatieve Uniform Resource Identifier (URI) toe.</span><span class="sxs-lookup"><span data-stu-id="f900c-311">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="f900c-312">Wanneer u de **parameter ConnectionURI** gebruikt, kan de externe bestemming een instructie retourneren om om te leiden naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="f900c-312">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="f900c-313">PowerShell leidt verbindingen standaard niet om, maar u kunt deze parameter gebruiken om de verbinding om te leiden.</span><span class="sxs-lookup"><span data-stu-id="f900c-313">By default, PowerShell doesn't redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="f900c-314">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de **optiewaarde maximumConnectionRedirectionCount-sessie** te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f900c-314">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="f900c-315">Gebruik de **parameter MaximumRedirection** van de cmdlet of stel de eigenschap `New-PSSessionOption` **MaximumConnectionRedirectionCount** van de `$PSSessionOption` voorkeursvariabele in.</span><span class="sxs-lookup"><span data-stu-id="f900c-315">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="f900c-316">De standaardwaarde is 5.</span><span class="sxs-lookup"><span data-stu-id="f900c-316">The default value is 5.</span></span>

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

### <span data-ttu-id="f900c-317">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="f900c-317">-ApplicationName</span></span>

<span data-ttu-id="f900c-318">Hiermee geeft u het toepassingsnaamsegment van de verbindings-URI op.</span><span class="sxs-lookup"><span data-stu-id="f900c-318">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="f900c-319">Gebruik deze parameter om de naam van de toepassing op te geven wanneer u de **parameter ConnectionURI** niet gebruikt in de opdracht .</span><span class="sxs-lookup"><span data-stu-id="f900c-319">Use this parameter to specify the application name when you aren't using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="f900c-320">De standaardwaarde is de waarde van de `$PSSessionApplicationName` voorkeursvariabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-320">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="f900c-321">Als deze voorkeursvariabele niet is gedefinieerd, is de standaardwaarde WSMAN.</span><span class="sxs-lookup"><span data-stu-id="f900c-321">If this preference variable isn't defined, the default value is WSMAN.</span></span> <span data-ttu-id="f900c-322">Deze waarde is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="f900c-322">This value is appropriate for most uses.</span></span> <span data-ttu-id="f900c-323">Zie voor meer informatie [about_Preference_Variables](./About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="f900c-323">For more information, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="f900c-324">De WinRM-service gebruikt de toepassingsnaam om een listener te selecteren om de verbindingsaanvraag te verwerken.</span><span class="sxs-lookup"><span data-stu-id="f900c-324">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="f900c-325">De waarde van deze parameter moet overeenkomen met de waarde van de **eigenschap URLPrefix** van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-325">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="f900c-326">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="f900c-326">-ArgumentList</span></span>

<span data-ttu-id="f900c-327">Levert de waarden van lokale variabelen in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-327">Supplies the values of local variables in the command.</span></span> <span data-ttu-id="f900c-328">De variabelen in de opdracht worden vervangen door deze waarden voordat de opdracht wordt uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-328">The variables in the command are replaced by these values before the command is run on the remote computer.</span></span> <span data-ttu-id="f900c-329">Voer de waarden in een door komma's gescheiden lijst in.</span><span class="sxs-lookup"><span data-stu-id="f900c-329">Enter the values in a comma-separated list.</span></span> <span data-ttu-id="f900c-330">Waarden zijn gekoppeld aan variabelen in de volgorde waarin ze worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="f900c-330">Values are associated with variables in the order that they're listed.</span></span> <span data-ttu-id="f900c-331">De alias voor **ArgumentList** is Args.</span><span class="sxs-lookup"><span data-stu-id="f900c-331">The alias for **ArgumentList** is Args.</span></span>

<span data-ttu-id="f900c-332">De waarden in de parameter **ArgumentList** kunnen werkelijke waarden zijn, zoals 1024, of ze kunnen verwijzingen zijn naar lokale variabelen, zoals `$max` .</span><span class="sxs-lookup"><span data-stu-id="f900c-332">The values in the **ArgumentList** parameter can be actual values, such as 1024, or they can be references to local variables, such as `$max`.</span></span>

<span data-ttu-id="f900c-333">Als u lokale variabelen in een opdracht wilt gebruiken, gebruikt u de volgende opdrachtindeling:</span><span class="sxs-lookup"><span data-stu-id="f900c-333">To use local variables in a command, use the following command format:</span></span>

<span data-ttu-id="f900c-334">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` -or- `<local-variable>`</span><span class="sxs-lookup"><span data-stu-id="f900c-334">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` -or- `<local-variable>`</span></span>

<span data-ttu-id="f900c-335">Het **sleutelwoord param** bevat de lokale variabelen die worden gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-335">The **param** keyword lists the local variables that are used in the command.</span></span> <span data-ttu-id="f900c-336">**ArgumentList** levert de waarden van de variabelen in de volgorde waarin ze worden vermeld.</span><span class="sxs-lookup"><span data-stu-id="f900c-336">**ArgumentList** supplies the values of the variables, in the order that they're listed.</span></span> <span data-ttu-id="f900c-337">Zie voor meer informatie over het gedrag van **ArgumentList** [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="f900c-337">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="f900c-338">-AsJob</span><span class="sxs-lookup"><span data-stu-id="f900c-338">-AsJob</span></span>

<span data-ttu-id="f900c-339">Geeft aan dat deze cmdlet wordt uitgevoerd de opdracht als achtergrond taak op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-339">Indicates that this cmdlet runs the command as a background job on a remote computer.</span></span> <span data-ttu-id="f900c-340">Gebruik deze parameter om opdrachten uit te voeren die lang duren.</span><span class="sxs-lookup"><span data-stu-id="f900c-340">Use this parameter to run commands that take an extensive time to finish.</span></span>

<span data-ttu-id="f900c-341">Wanneer u de **Parameter AsJob** gebruikt, retourneert de opdracht een -object dat de taak vertegenwoordigt en geeft vervolgens de opdrachtprompt weer.</span><span class="sxs-lookup"><span data-stu-id="f900c-341">When you use the **AsJob** parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span> <span data-ttu-id="f900c-342">U kunt in de sessie blijven werken terwijl de taak is voltooien.</span><span class="sxs-lookup"><span data-stu-id="f900c-342">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="f900c-343">Gebruik de cmdlets om de `*-Job` taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="f900c-343">To manage the job, use the `*-Job` cmdlets.</span></span> <span data-ttu-id="f900c-344">Gebruik de cmdlet om de `Receive-Job` taakresultaten op te halen.</span><span class="sxs-lookup"><span data-stu-id="f900c-344">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="f900c-345">De **Parameter AsJob** lijkt op het gebruik van `Invoke-Command` de cmdlet om een `Start-Job` cmdlet op afstand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f900c-345">The **AsJob** parameter resembles using the `Invoke-Command` cmdlet to run a `Start-Job` cmdlet remotely.</span></span> <span data-ttu-id="f900c-346">Met **AsJob wordt de** taak echter gemaakt op de lokale computer, ook al wordt de taak uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-346">However, with **AsJob**, the job is created on the local computer, even though the job runs on a remote computer.</span></span> <span data-ttu-id="f900c-347">De resultaten van de externe taak worden automatisch geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-347">The results of the remote job are automatically returned to the local computer.</span></span>

<span data-ttu-id="f900c-348">Zie PowerShell-achtergrondtaken voor meer [informatie about_Jobs](About/about_Jobs.md) en [about_Remote_Jobs.](About/about_Remote_Jobs.md)</span><span class="sxs-lookup"><span data-stu-id="f900c-348">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="f900c-349">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="f900c-349">-Authentication</span></span>

<span data-ttu-id="f900c-350">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="f900c-350">Specifies the mechanism that's used to authenticate the user's credentials.</span></span> <span data-ttu-id="f900c-351">CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="f900c-351">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="f900c-352">De acceptabele waarden voor deze parameter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="f900c-352">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f900c-353">Standaard</span><span class="sxs-lookup"><span data-stu-id="f900c-353">Default</span></span>
- <span data-ttu-id="f900c-354">Basic</span><span class="sxs-lookup"><span data-stu-id="f900c-354">Basic</span></span>
- <span data-ttu-id="f900c-355">Credssp</span><span class="sxs-lookup"><span data-stu-id="f900c-355">Credssp</span></span>
- <span data-ttu-id="f900c-356">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="f900c-356">Digest</span></span>
- <span data-ttu-id="f900c-357">Kerberos</span><span class="sxs-lookup"><span data-stu-id="f900c-357">Kerberos</span></span>
- <span data-ttu-id="f900c-358">Negotiate</span><span class="sxs-lookup"><span data-stu-id="f900c-358">Negotiate</span></span>
- <span data-ttu-id="f900c-359">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="f900c-359">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="f900c-360">De standaardwaarde is Standaard.</span><span class="sxs-lookup"><span data-stu-id="f900c-360">The default value is Default.</span></span>

<span data-ttu-id="f900c-361">Zie [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze parameter.</span><span class="sxs-lookup"><span data-stu-id="f900c-361">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="f900c-362">CredSSP-verificatie (Credential Security Support Provider), waarbij de referenties van de gebruiker worden doorgegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie op meer dan één resource is vereist, zoals toegang tot een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="f900c-362">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="f900c-363">Dit mechanisme verhoogt het beveiligingsrisico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="f900c-363">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="f900c-364">Als de externe computer is aangetast, kunnen de referenties die worden doorgegeven aan deze worden gebruikt voor het beheer van de netwerksessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-364">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span> <span data-ttu-id="f900c-365">Zie Credential [Security Support Provider (Referentiebeveiligingsondersteuningsprovider) voor meer informatie.](/windows/win32/secauthn/credential-security-support-provider)</span><span class="sxs-lookup"><span data-stu-id="f900c-365">For more information, see [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider).</span></span>

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

### <span data-ttu-id="f900c-366">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="f900c-366">-CertificateThumbprint</span></span>

<span data-ttu-id="f900c-367">Hiermee geeft u het digitale openbare-sleutelcertificaat (X509) op van een gebruikersaccount dat is machtigingen heeft om verbinding te maken met de niet-verbonden sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-367">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="f900c-368">Voer de vingerafdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="f900c-368">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="f900c-369">Certificaten worden gebruikt bij verificatie op basis van clientcertificaten.</span><span class="sxs-lookup"><span data-stu-id="f900c-369">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="f900c-370">Ze kunnen alleen worden toe te staan aan lokale gebruikersaccounts en ze werken niet met domeinaccounts.</span><span class="sxs-lookup"><span data-stu-id="f900c-370">They can be mapped only to local user accounts and they don't work with domain accounts.</span></span>

<span data-ttu-id="f900c-371">Gebruik een - of -opdracht in het PowerShell-certificaatstation om een vingerafdruk van het `Get-Item` `Get-ChildItem` certificaat op te halen.</span><span class="sxs-lookup"><span data-stu-id="f900c-371">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="f900c-372">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f900c-372">-ComputerName</span></span>

<span data-ttu-id="f900c-373">Hiermee geeft u de computers waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-373">Specifies the computers on which the command runs.</span></span> <span data-ttu-id="f900c-374">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-374">The default is the local computer.</span></span>

<span data-ttu-id="f900c-375">Wanneer u de **parameter ComputerName** gebruikt, maakt PowerShell een tijdelijke verbinding die alleen wordt gebruikt om de opgegeven opdracht uit te voeren en vervolgens wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="f900c-375">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that's used only to run the specified command and is then closed.</span></span> <span data-ttu-id="f900c-376">Als u een permanente verbinding nodig hebt, gebruikt u de parameter **Sessie.**</span><span class="sxs-lookup"><span data-stu-id="f900c-376">If you need a persistent connection, use the **Session** parameter.</span></span>

<span data-ttu-id="f900c-377">Typ de NETBIOS-naam, het IP-adres of de Fully Qualified Domain Name van een of meer computers in een door komma's gescheiden lijst.</span><span class="sxs-lookup"><span data-stu-id="f900c-377">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="f900c-378">Als u de lokale computer wilt opgeven, typt u de computernaam, localhost of een punt ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="f900c-378">To specify the local computer, type the computer name, localhost, or a dot (`.`).</span></span>

<span data-ttu-id="f900c-379">Als u een IP-adres in de waarde **computernaam** wilt gebruiken, moet de opdracht de parameter **Credential** bevatten.</span><span class="sxs-lookup"><span data-stu-id="f900c-379">To use an IP address in the value of **ComputerName**, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="f900c-380">De computer moet worden geconfigureerd voor het HTTPS-transport of het IP-adres van de externe computer moet worden opgenomen in de WinRM **TrustedHosts-lijst van de** lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-380">The computer must be configured for the HTTPS transport or the IP address of the remote computer must be included in the local computer's WinRM **TrustedHosts** list.</span></span> <span data-ttu-id="f900c-381">Zie How to Add a Computer to the Trusted Host List (Een computer toevoegen aan de lijst met vertrouwde [host)](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list)voor instructies voor het toevoegen van een computernaam aan de **lijst met TrustedHosts.**</span><span class="sxs-lookup"><span data-stu-id="f900c-381">For instructions to add a computer name to the **TrustedHosts** list, see [How to Add a Computer to the Trusted Host List](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list).</span></span>

<span data-ttu-id="f900c-382">In Windows Vista en latere versies van het Windows-besturingssysteem moet u PowerShell uitvoeren met  de optie Als administrator uitvoeren om de lokale computer op te nemen in de waarde **computernaam.**</span><span class="sxs-lookup"><span data-stu-id="f900c-382">On Windows Vista and later versions of the Windows operating system, to include the local computer in the value of **ComputerName**, you must run PowerShell using the **Run as administrator** option.</span></span>

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

### <span data-ttu-id="f900c-383">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="f900c-383">-ConfigurationName</span></span>

<span data-ttu-id="f900c-384">Hiermee geeft u de sessieconfiguratie op die wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="f900c-384">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="f900c-385">Voer een configuratienaam of de volledig gekwalificeerde resource-URI in voor een sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="f900c-385">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="f900c-386">Als u alleen de configuratienaam opgeeft, wordt de volgende schema-URI toegevoegd: `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="f900c-386">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="f900c-387">Wanneer u deze parameter gebruikt met SSH, geeft u het subsysteem op dat moet worden gebruikt op het doel, zoals gedefinieerd in `sshd_config` .</span><span class="sxs-lookup"><span data-stu-id="f900c-387">When used with SSH, this parameter specifies the subsystem to use on the target as defined in `sshd_config`.</span></span> <span data-ttu-id="f900c-388">De standaardwaarde voor SSH is het `powershell` subsysteem.</span><span class="sxs-lookup"><span data-stu-id="f900c-388">The default value for SSH is the `powershell` subsystem.</span></span>

<span data-ttu-id="f900c-389">De sessieconfiguratie voor een sessie bevindt zich op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-389">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="f900c-390">Als de opgegeven sessieconfiguratie niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-390">If the specified session configuration doesn't exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="f900c-391">De standaardwaarde is de waarde van de `$PSSessionConfigurationName` voorkeursvariabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-391">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="f900c-392">Als deze voorkeursvariabele niet is ingesteld, is de **standaardwaarde Microsoft.PowerShell.**</span><span class="sxs-lookup"><span data-stu-id="f900c-392">If this preference variable isn't set, the default is **Microsoft.PowerShell**.</span></span> <span data-ttu-id="f900c-393">Zie voor meer informatie [about_Preference_Variables.](about/about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="f900c-393">For more information, see [about_Preference_Variables](about/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="f900c-394">-ConnectingTimeout</span><span class="sxs-lookup"><span data-stu-id="f900c-394">-ConnectingTimeout</span></span>

<span data-ttu-id="f900c-395">Hiermee geeft u de hoeveelheid tijd in milliseconden op die is toegestaan voor het voltooien van de eerste SSH-verbinding.</span><span class="sxs-lookup"><span data-stu-id="f900c-395">Specifies the amount of time in milliseconds allowed for the initial SSH connection to complete.</span></span> <span data-ttu-id="f900c-396">Als de verbinding niet binnen de opgegeven tijd is voltooid, wordt er een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-396">If the connection doesn't complete within the specified time, an error is returned.</span></span>

<span data-ttu-id="f900c-397">Deze parameter is geïntroduceerd in PowerShell 7.2</span><span class="sxs-lookup"><span data-stu-id="f900c-397">This parameter was introduced in PowerShell 7.2</span></span>

```yaml
Type: System.Int32
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: unlimited
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f900c-398">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="f900c-398">-ConnectionUri</span></span>

<span data-ttu-id="f900c-399">Hiermee geeft u een Uniform Resource Identifier (URI) op die het verbindings-eindpunt van de sessie definieert.</span><span class="sxs-lookup"><span data-stu-id="f900c-399">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint of the session.</span></span>
<span data-ttu-id="f900c-400">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="f900c-400">The URI must be fully qualified.</span></span>

<span data-ttu-id="f900c-401">De indeling van deze tekenreeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f900c-401">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="f900c-402">De standaardwaarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f900c-402">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="f900c-403">Als u geen verbindings-URI opgeeft, kunt u de parameters **UseSSL** en **Port** gebruiken om de waarden voor de verbindings-URI op te geven.</span><span class="sxs-lookup"><span data-stu-id="f900c-403">If you don't specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="f900c-404">Geldige waarden voor het **segment Transport** van de URI zijn HTTP en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f900c-404">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="f900c-405">Als u een verbindings-URI opgeeft met een Transport-segment, maar geen poort opgeeft, wordt de sessie gemaakt met de standaardpoorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f900c-405">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with the standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="f900c-406">Geef poort 5985 voor HTTP of 5986 voor HTTPS op als u de standaardpoorten wilt gebruiken voor het op andere locatie gebruiken van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f900c-406">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="f900c-407">Als de doelcomputer de verbinding omleiden naar een andere URI, PowerShell voorkomt de omleiding, tenzij u de **allowRedirection** parameter in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-407">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="f900c-408">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="f900c-408">-ContainerId</span></span>

<span data-ttu-id="f900c-409">Hiermee geeft u een matrix met container-ID's op.</span><span class="sxs-lookup"><span data-stu-id="f900c-409">Specifies an array of container IDs.</span></span>

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

### <span data-ttu-id="f900c-410">-Credential</span><span class="sxs-lookup"><span data-stu-id="f900c-410">-Credential</span></span>

<span data-ttu-id="f900c-411">Hiermee geeft u een gebruikersaccount op dat is machtigingen heeft om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f900c-411">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="f900c-412">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f900c-412">The default is the current user.</span></span>

<span data-ttu-id="f900c-413">Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een **PSCredential-object** in dat door de `Get-Credential` cmdlet is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-413">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f900c-414">Als u een gebruikersnaam typt, wordt u gevraagd het wachtwoord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="f900c-414">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="f900c-415">Referenties worden opgeslagen in een [PSCredential-object](/dotnet/api/system.management.automation.pscredential) en het wachtwoord wordt opgeslagen als een [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="f900c-415">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f900c-416">Zie How secure is **SecureString?** (Hoe veilig is SecureString?) voor meer informatie over [SecureString-gegevensbeveiliging.](/dotnet/api/system.security.securestring#how-secure-is-securestring)</span><span class="sxs-lookup"><span data-stu-id="f900c-416">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="f900c-417">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="f900c-417">-EnableNetworkAccess</span></span>

<span data-ttu-id="f900c-418">Geeft aan dat deze cmdlet een interactief beveiliging token toevoegt aan loopback-sessies.</span><span class="sxs-lookup"><span data-stu-id="f900c-418">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="f900c-419">Met het interactieve token kunt u opdrachten uitvoeren in de loopback-sessie die gegevens van andere computers op halen.</span><span class="sxs-lookup"><span data-stu-id="f900c-419">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="f900c-420">U kunt bijvoorbeeld een opdracht uitvoeren in de sessie die XML-bestanden kopieert van een externe computer naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-420">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="f900c-421">Een loopback-sessie is **een PSSession** die afkomstig is van en eindigt op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-421">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="f900c-422">Als u een loopback-sessie wilt maken, laat u de parameter **ComputerName** weg of stelt u de waarde ervan in op dot ( ), localhost of de `.` naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-422">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (`.`), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="f900c-423">Loopback-sessies worden standaard gemaakt met behulp van een netwerk-token, dat mogelijk onvoldoende machtigingen biedt voor verificatie bij externe computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-423">By default, loopback sessions are created using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="f900c-424">De **parameter EnableNetworkAccess** is alleen van kracht in loopback-sessies.</span><span class="sxs-lookup"><span data-stu-id="f900c-424">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="f900c-425">Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, slaagt de opdracht, maar de parameter wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-425">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="f900c-426">U kunt externe toegang toestaan in een loopback-sessie  met behulp van de **CredSSP-waarde** van de verificatieparameter, die de sessiereferenties delegeert naar andere computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-426">You can allow remote access in a loopback session using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="f900c-427">Om de computer te beschermen tegen schadelijke toegang, kunnen losgekoppelde loopback-sessies met interactieve tokens, die zijn gemaakt met **EnableNetworkAccess,** alleen opnieuw worden verbonden vanaf de computer waarop de sessie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f900c-427">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created using **EnableNetworkAccess**, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="f900c-428">Niet-verbonden sessies die gebruikmaken van CredSSP-verificatie kunnen opnieuw worden verbonden vanaf andere computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-428">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="f900c-429">Voor meer informatie raadpleegt u `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="f900c-429">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="f900c-430">Deze parameter is geïntroduceerd in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f900c-430">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f900c-431">-FilePath</span><span class="sxs-lookup"><span data-stu-id="f900c-431">-FilePath</span></span>

<span data-ttu-id="f900c-432">Hiermee geeft u een lokaal script dat deze cmdlet wordt uitgevoerd op een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-432">Specifies a local script that this cmdlet runs on one or more remote computers.</span></span> <span data-ttu-id="f900c-433">Voer het pad en de bestandsnaam van het script in of geef een scriptpad door naar `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="f900c-433">Enter the path and filename of the script, or pipe a script path to `Invoke-Command`.</span></span> <span data-ttu-id="f900c-434">Het script moet bestaan op de lokale computer of in een map waar de lokale computer toegang toe heeft.</span><span class="sxs-lookup"><span data-stu-id="f900c-434">The script must exist on the local computer or in a directory that the local computer can access.</span></span> <span data-ttu-id="f900c-435">Gebruik **ArgumentList om** de waarden van parameters in het script op te geven.</span><span class="sxs-lookup"><span data-stu-id="f900c-435">Use **ArgumentList** to specify the values of parameters in the script.</span></span>

<span data-ttu-id="f900c-436">Wanneer u deze parameter gebruikt, converteert PowerShell de inhoud van het opgegeven scriptbestand naar een scriptblok, verzendt het scriptblok naar de externe computer en voert het uit op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-436">When you use this parameter, PowerShell converts the contents of the specified script file to a script block, transmits the script block to the remote computer, and runs it on the remote computer.</span></span>

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

### <span data-ttu-id="f900c-437">-HideComputerName</span><span class="sxs-lookup"><span data-stu-id="f900c-437">-HideComputerName</span></span>

<span data-ttu-id="f900c-438">Geeft aan dat deze cmdlet de computernaam van elk object weglaat uit de uitvoerweergave.</span><span class="sxs-lookup"><span data-stu-id="f900c-438">Indicates that this cmdlet omits the computer name of each object from the output display.</span></span> <span data-ttu-id="f900c-439">De naam van de computer die het object heeft gegenereerd, wordt standaard weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="f900c-439">By default, the name of the computer that generated the object appears in the display.</span></span>

<span data-ttu-id="f900c-440">Deze parameter is alleen van invloed op de uitvoerweergave.</span><span class="sxs-lookup"><span data-stu-id="f900c-440">This parameter affects only the output display.</span></span> <span data-ttu-id="f900c-441">Het object wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f900c-441">It doesn't change the object.</span></span>

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

### <span data-ttu-id="f900c-442">-HostName</span><span class="sxs-lookup"><span data-stu-id="f900c-442">-HostName</span></span>

<span data-ttu-id="f900c-443">Hiermee geeft u een matrix met computernamen op voor een SSH-verbinding (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="f900c-443">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="f900c-444">Dit is vergelijkbaar met de **ComputerName** parameter behalve dat de verbinding met de externe computer wordt gemaakt met behulp van SSH in plaats van Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="f900c-444">This is similar to the **ComputerName** parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>

<span data-ttu-id="f900c-445">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="f900c-445">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="f900c-446">-InDisconnectedSession</span><span class="sxs-lookup"><span data-stu-id="f900c-446">-InDisconnectedSession</span></span>

<span data-ttu-id="f900c-447">Geeft aan dat deze cmdlet een opdracht of script in een niet-verbonden sessie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-447">Indicates that this cmdlet runs a command or script in a disconnected session.</span></span>

<span data-ttu-id="f900c-448">Wanneer u de **parameter InDisconnectedSession** gebruikt, maakt een permanente sessie op elke externe computer, start u de opdracht die is opgegeven door de parameter ScriptBlock of FilePath en wordt de verbinding met de sessie `Invoke-Command` verbroken.  </span><span class="sxs-lookup"><span data-stu-id="f900c-448">When you use the **InDisconnectedSession** parameter, `Invoke-Command` creates a persistent session on each remote computer, starts the command specified by the **ScriptBlock** or **FilePath** parameter, and then disconnects from the session.</span></span> <span data-ttu-id="f900c-449">De opdrachten blijven worden uitgevoerd in de niet-verbonden sessies.</span><span class="sxs-lookup"><span data-stu-id="f900c-449">The commands continue to run in the disconnected sessions.</span></span> <span data-ttu-id="f900c-450">**Met InDisconnectedSession kunt** u opdrachten uitvoeren zonder een verbinding met de externe sessies te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="f900c-450">**InDisconnectedSession** enables you to run commands without maintaining a connection to the remote sessions.</span></span> <span data-ttu-id="f900c-451">En omdat de sessie wordt verbroken voordat er resultaten worden geretourneerd, zorgt **InDisconnectedSession** ervoor dat alle opdrachtresultaten worden geretourneerd naar de opnieuw verbonden sessie, in plaats van te worden gesplitst tussen sessies.</span><span class="sxs-lookup"><span data-stu-id="f900c-451">And, because the session is disconnected before any results are returned, **InDisconnectedSession** makes sure that all command results are returned to the reconnected session, instead of being split between sessions.</span></span>

<span data-ttu-id="f900c-452">U kunt **InDisconnectedSession** niet gebruiken met de parameter **Session** of **de parameter AsJob.**</span><span class="sxs-lookup"><span data-stu-id="f900c-452">You can't use **InDisconnectedSession** with the **Session** parameter or the **AsJob** parameter.</span></span>

<span data-ttu-id="f900c-453">Opdrachten die **gebruikmaken van InDisconnectedSession retourneren** een **PSSession-object** dat de niet-verbonden sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f900c-453">Commands that use **InDisconnectedSession** return a **PSSession** object that represents the disconnected session.</span></span> <span data-ttu-id="f900c-454">Ze retourneren de opdrachtuitvoer niet.</span><span class="sxs-lookup"><span data-stu-id="f900c-454">They don't return the command output.</span></span> <span data-ttu-id="f900c-455">Gebruik de cmdlets of om verbinding te maken met de sessie zonder `Connect-PSSession` `Receive-PSSession` verbinding.</span><span class="sxs-lookup"><span data-stu-id="f900c-455">To connect to the disconnected session, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span> <span data-ttu-id="f900c-456">Gebruik de cmdlet om de resultaten op te halen van opdrachten die in de `Receive-PSSession` sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f900c-456">To get the results of commands that ran in the session, use the `Receive-PSSession` cmdlet.</span></span> <span data-ttu-id="f900c-457">Als u opdrachten wilt uitvoeren die uitvoer genereren in een niet-verbonden sessie, stelt u de waarde van de **sessieoptie OutputBufferingMode** in op **Drop**.</span><span class="sxs-lookup"><span data-stu-id="f900c-457">To run commands that generate output in a disconnected session, set the value of the **OutputBufferingMode** session option to **Drop**.</span></span> <span data-ttu-id="f900c-458">Als u verbinding wilt maken met de niet-verbonden sessie, stelt u de time-out voor inactiefheid in de sessie in, zodat u voldoende tijd hebt om verbinding te maken voordat u de sessie kunt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="f900c-458">If you intend to connect to the disconnected session, set the idle time-out in the session so that it provides sufficient time for you to connect before deleting the session.</span></span>

<span data-ttu-id="f900c-459">U kunt de uitvoerbuffermodus en niet-actieve time-out instellen in de parameter **SessionOption** of in de `$PSSessionOption` voorkeursvariabele.</span><span class="sxs-lookup"><span data-stu-id="f900c-459">You can set the output buffering mode and idle time-out in the **SessionOption** parameter or in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="f900c-460">Zie en about_Preference_Variables voor `New-PSSessionOption` [meer informatie over sessieopties.](./about/about_preference_variables.md)</span><span class="sxs-lookup"><span data-stu-id="f900c-460">For more information about session options, see `New-PSSessionOption` and [about_Preference_Variables](./about/about_preference_variables.md).</span></span>

<span data-ttu-id="f900c-461">Zie voor meer informatie over de functie Niet-verbonden [sessies about_Remote_Disconnected_Sessions.](about/about_Remote_Disconnected_Sessions.md)</span><span class="sxs-lookup"><span data-stu-id="f900c-461">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="f900c-462">Deze parameter is geïntroduceerd in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f900c-462">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f900c-463">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f900c-463">-InputObject</span></span>

<span data-ttu-id="f900c-464">Hiermee geeft u invoer voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-464">Specifies input to the command.</span></span> <span data-ttu-id="f900c-465">Voer een variabele in die de objecten bevat of typ een opdracht of expressie die de objecten op haalt.</span><span class="sxs-lookup"><span data-stu-id="f900c-465">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="f900c-466">Wanneer u de **parameter InputObject** gebruikt, gebruikt u de automatische variabele in de waarde van de `$Input` parameter **ScriptBlock** om de invoerobjecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f900c-466">When using the **InputObject** parameter, use the `$Input` automatic variable in the value of the **ScriptBlock** parameter to represent the input objects.</span></span>

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

### <span data-ttu-id="f900c-467">-JobName</span><span class="sxs-lookup"><span data-stu-id="f900c-467">-JobName</span></span>

<span data-ttu-id="f900c-468">Hiermee geeft u een gebruiksvriendelijke naam voor de achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="f900c-468">Specifies a friendly name for the background job.</span></span> <span data-ttu-id="f900c-469">Taken hebben standaard de naam `Job<n>` , waarbij `<n>` een rangnummer is.</span><span class="sxs-lookup"><span data-stu-id="f900c-469">By default, jobs are named `Job<n>`, where `<n>` is an ordinal number.</span></span>

<span data-ttu-id="f900c-470">Als u de parameter **JobName** in een opdracht gebruikt, wordt de opdracht uitgevoerd als een taak en wordt een taakobject retourneert, zelfs als u AsJob niet in de opdracht `Invoke-Command` opgeeft. </span><span class="sxs-lookup"><span data-stu-id="f900c-470">If you use the **JobName** parameter in a command, the command is run as a job, and `Invoke-Command` returns a job object, even if you don't include **AsJob** in the command.</span></span>

<span data-ttu-id="f900c-471">Zie voor meer informatie over PowerShell-achtergrondtaken [about_Jobs.](./About/about_Jobs.md)</span><span class="sxs-lookup"><span data-stu-id="f900c-471">For more information about PowerShell background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f900c-472">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="f900c-472">-KeyFilePath</span></span>

<span data-ttu-id="f900c-473">Hiermee geeft u een sleutelbestandspad op dat door Secure Shell (SSH) wordt gebruikt om een gebruiker op een externe computer te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="f900c-473">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="f900c-474">Met SSH kan gebruikersverificatie worden uitgevoerd via persoonlijke en openbare sleutels als alternatief voor basiswachtwoordverificatie.</span><span class="sxs-lookup"><span data-stu-id="f900c-474">SSH allows user authentication to be performed via private and public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="f900c-475">Als de externe computer is geconfigureerd voor sleutelverificatie, kan deze parameter worden gebruikt om de sleutel op te geven waarmee de gebruiker wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-475">If the remote computer is configured for key authentication, then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="f900c-476">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="f900c-476">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="f900c-477">-NoNewScope</span><span class="sxs-lookup"><span data-stu-id="f900c-477">-NoNewScope</span></span>

<span data-ttu-id="f900c-478">Geeft aan dat deze cmdlet de opgegeven opdracht in het huidige bereik wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-478">Indicates that this cmdlet runs the specified command in the current scope.</span></span> <span data-ttu-id="f900c-479">Opdrachten worden `Invoke-Command` standaard uitgevoerd in hun eigen bereik.</span><span class="sxs-lookup"><span data-stu-id="f900c-479">By default, `Invoke-Command` runs commands in their own scope.</span></span>

<span data-ttu-id="f900c-480">Deze parameter is alleen geldig in opdrachten die worden uitgevoerd in de huidige sessie, dat wil zeggen opdrachten die weglaten zowel de **ComputerName** en **sessie** parameters.</span><span class="sxs-lookup"><span data-stu-id="f900c-480">This parameter is valid only in commands that are run in the current session, that is, commands that omit both the **ComputerName** and **Session** parameters.</span></span>

<span data-ttu-id="f900c-481">Deze parameter is geïntroduceerd in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f900c-481">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f900c-482">-Port</span><span class="sxs-lookup"><span data-stu-id="f900c-482">-Port</span></span>

<span data-ttu-id="f900c-483">Hiermee geeft u de netwerkpoort op de externe computer die wordt gebruikt voor deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-483">Specifies the network port on the remote computer that is used for this command.</span></span> <span data-ttu-id="f900c-484">Als u verbinding wilt maken met een externe computer, moet de externe computer luisteren op de poort die de verbinding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f900c-484">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="f900c-485">De standaardpoorten zijn 5985 (WinRM-poort voor HTTP) en 5986 (WinRM-poort voor HTTPS).</span><span class="sxs-lookup"><span data-stu-id="f900c-485">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="f900c-486">Voordat u een alternatieve poort gebruikt, configureert u de WinRM-listener op de externe computer om naar die poort te luisteren.</span><span class="sxs-lookup"><span data-stu-id="f900c-486">Before using an alternate port, configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="f900c-487">Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de PowerShell-prompt:</span><span class="sxs-lookup"><span data-stu-id="f900c-487">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="f900c-488">Gebruik de parameter **Port niet,** tenzij dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="f900c-488">Don't use the **Port** parameter unless you must.</span></span> <span data-ttu-id="f900c-489">De poort die is ingesteld in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-489">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="f900c-490">Een alternatieve poortinstelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="f900c-490">An alternate port setting might prevent the command from running on all computers.</span></span>

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

### <span data-ttu-id="f900c-491">-RemoteDebug</span><span class="sxs-lookup"><span data-stu-id="f900c-491">-RemoteDebug</span></span>

<span data-ttu-id="f900c-492">Wordt gebruikt om de aangeroepen opdracht uit te voeren in de foutopsporingsmodus in de externe PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-492">Used to run the invoked command in debug mode in the remote PowerShell session.</span></span>

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

### <span data-ttu-id="f900c-493">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="f900c-493">-RunAsAdministrator</span></span>

<span data-ttu-id="f900c-494">Geeft aan dat deze cmdlet een opdracht aanroept als beheerder.</span><span class="sxs-lookup"><span data-stu-id="f900c-494">Indicates that this cmdlet invokes a command as an Administrator.</span></span>

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

### <span data-ttu-id="f900c-495">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="f900c-495">-ScriptBlock</span></span>

<span data-ttu-id="f900c-496">Hiermee geeft u de opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f900c-496">Specifies the commands to run.</span></span> <span data-ttu-id="f900c-497">Sluit de opdrachten tussen accolades om `{ }` een scriptblok te maken.</span><span class="sxs-lookup"><span data-stu-id="f900c-497">Enclose the commands in curly braces `{ }` to create a script block.</span></span>
<span data-ttu-id="f900c-498">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="f900c-498">This parameter is required.</span></span>

<span data-ttu-id="f900c-499">Standaard worden variabelen in de opdracht geëvalueerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-499">By default, any variables in the command are evaluated on the remote computer.</span></span> <span data-ttu-id="f900c-500">Gebruik **ArgumentList** om lokale variabelen op te nemen in de opdracht .</span><span class="sxs-lookup"><span data-stu-id="f900c-500">To include local variables in the command, use **ArgumentList**.</span></span>

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

### <span data-ttu-id="f900c-501">-Sessie</span><span class="sxs-lookup"><span data-stu-id="f900c-501">-Session</span></span>

<span data-ttu-id="f900c-502">Hiermee geeft u een matrix van sessies waarin deze cmdlet de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-502">Specifies an array of sessions in which this cmdlet runs the command.</span></span> <span data-ttu-id="f900c-503">Voer een variabele in die **PSSession-objecten** bevat of een opdracht die de **PSSession-objecten** maakt of op haalt, zoals een `New-PSSession` - of `Get-PSSession` -opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-503">Enter a variable that contains **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="f900c-504">Wanneer u een **PSSession maakt,** maakt PowerShell een permanente verbinding met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-504">When you create a **PSSession**, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="f900c-505">Gebruik een **PSSession om** een reeks gerelateerde opdrachten uit te voeren die gegevens delen.</span><span class="sxs-lookup"><span data-stu-id="f900c-505">Use a **PSSession** to run a series of related commands that share data.</span></span> <span data-ttu-id="f900c-506">Als u één opdracht of een reeks niet-gerelateerde opdrachten wilt uitvoeren, gebruikt u de parameter **ComputerName.**</span><span class="sxs-lookup"><span data-stu-id="f900c-506">To run a single command or a series of unrelated commands, use the **ComputerName** parameter.</span></span> <span data-ttu-id="f900c-507">Zie voor meer informatie [about_PSSessions](./About/about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="f900c-507">For more information, see [about_PSSessions](./About/about_PSSessions.md).</span></span>

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

### <span data-ttu-id="f900c-508">-SessionName</span><span class="sxs-lookup"><span data-stu-id="f900c-508">-SessionName</span></span>

<span data-ttu-id="f900c-509">Hiermee geeft u een gebruiksvriendelijke naam op voor een niet-verbonden sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-509">Specifies a friendly name for a disconnected session.</span></span> <span data-ttu-id="f900c-510">U kunt de naam gebruiken om te verwijzen naar de sessie in volgende opdrachten, zoals een `Get-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-510">You can use the name to refer to the session in subsequent commands, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="f900c-511">Deze parameter is alleen geldig met **de parameter InDisconnectedSession.**</span><span class="sxs-lookup"><span data-stu-id="f900c-511">This parameter is valid only with the **InDisconnectedSession** parameter.</span></span>

<span data-ttu-id="f900c-512">Deze parameter is geïntroduceerd in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f900c-512">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f900c-513">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="f900c-513">-SessionOption</span></span>

<span data-ttu-id="f900c-514">Hiermee geeft u geavanceerde opties voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-514">Specifies advanced options for the session.</span></span> <span data-ttu-id="f900c-515">Voer een **SessionOption-object** in, zoals een object dat u maakt met behulp van de cmdlet of een hash-tabel waarin de sleutels sessieoptienamen zijn en de waarden `New-PSSessionOption` sessieoptiewaarden zijn.</span><span class="sxs-lookup"><span data-stu-id="f900c-515">Enter a **SessionOption** object, such as one that you create using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="f900c-516">De standaardwaarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` voorkeursvariabele als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="f900c-516">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="f900c-517">Anders worden de standaardwaarden ingesteld door opties die zijn ingesteld in de sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="f900c-517">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="f900c-518">De waarden van de sessieoptie hebben voorrang op standaardwaarden voor sessies die zijn ingesteld in de `$PSSessionOption` voorkeursvariabele en in de sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="f900c-518">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="f900c-519">Ze hebben echter geen voorrang op maximumwaarden, quota of limieten die zijn ingesteld in de sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="f900c-519">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="f900c-520">Zie voor een beschrijving van de sessieopties die de standaardwaarden `New-PSSessionOption` bevatten.</span><span class="sxs-lookup"><span data-stu-id="f900c-520">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="f900c-521">Zie voor meer informatie `$PSSessionOption` over de voorkeursvariabele [about_Preference_Variables.](About/about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="f900c-521">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="f900c-522">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="f900c-522">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="f900c-523">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="f900c-523">-SSHConnection</span></span>

<span data-ttu-id="f900c-524">Deze parameter maakt gebruik van een matrix met hashtabellen waarbij elke hash-tabel een of meer verbindingsparameters bevat die nodig zijn om een SSH-verbinding (Secure Shell) tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="f900c-524">This parameter takes an array of hash tables where each hash table contains one or more connection parameters needed to establish a Secure Shell (SSH) connection.</span></span> <span data-ttu-id="f900c-525">De **parameter SSHConnection** is handig voor het maken van meerdere sessies waarbij elke sessie andere verbindingsgegevens vereist.</span><span class="sxs-lookup"><span data-stu-id="f900c-525">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

<span data-ttu-id="f900c-526">De hashtabel heeft de volgende leden:</span><span class="sxs-lookup"><span data-stu-id="f900c-526">The hashtable has the following members:</span></span>

- <span data-ttu-id="f900c-527">**ComputerName** (of **HostName**)</span><span class="sxs-lookup"><span data-stu-id="f900c-527">**ComputerName** (or **HostName**)</span></span>
- <span data-ttu-id="f900c-528">**Poort**</span><span class="sxs-lookup"><span data-stu-id="f900c-528">**Port**</span></span>
- <span data-ttu-id="f900c-529">**Gebruikersnaam**</span><span class="sxs-lookup"><span data-stu-id="f900c-529">**UserName**</span></span>
- <span data-ttu-id="f900c-530">**KeyFilePath** (of **IdentityFilePath**)</span><span class="sxs-lookup"><span data-stu-id="f900c-530">**KeyFilePath** (or **IdentityFilePath**)</span></span>

<span data-ttu-id="f900c-531">**ComputerName** (of **HostName)** is het enige sleutel-waardepaar dat vereist is.</span><span class="sxs-lookup"><span data-stu-id="f900c-531">**ComputerName** (or **HostName**) is the only key-value pair that is required.</span></span>

<span data-ttu-id="f900c-532">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="f900c-532">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="f900c-533">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="f900c-533">-SSHTransport</span></span>

<span data-ttu-id="f900c-534">Geeft aan dat de externe verbinding tot stand is gebracht met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="f900c-534">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="f900c-535">PowerShell maakt standaard gebruik van Windows WinRM om verbinding te maken met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-535">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="f900c-536">Deze schakelknop dwingt PowerShell om de **parameter HostName** te gebruiken voor het tot stand brengen van een externe SSH-verbinding.</span><span class="sxs-lookup"><span data-stu-id="f900c-536">This switch forces PowerShell to use the **HostName** parameter for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="f900c-537">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="f900c-537">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="f900c-538">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="f900c-538">-ThrottleLimit</span></span>

<span data-ttu-id="f900c-539">Hiermee geeft u het maximum aantal gelijktijdige verbindingen die kunnen worden ingesteld voor het uitvoeren van deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-539">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="f900c-540">Als u deze parameter weglaten of een waarde van 0, de standaardwaarde, 32, wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f900c-540">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="f900c-541">De beperkingslimiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-541">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="f900c-542">-GebruikersNaam</span><span class="sxs-lookup"><span data-stu-id="f900c-542">-UserName</span></span>

<span data-ttu-id="f900c-543">Hiermee geeft u de gebruikersnaam voor het account dat wordt gebruikt voor het uitvoeren van een opdracht op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-543">Specifies the username for the account used to run a command on the remote computer.</span></span> <span data-ttu-id="f900c-544">De gebruikersverificatiemethode is afhankelijk van hoe Secure Shell (SSH) is geconfigureerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-544">The user authentication method depends on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="f900c-545">Als SSH is geconfigureerd voor basiswachtwoordverificatie, wordt u gevraagd om het gebruikerswachtwoord.</span><span class="sxs-lookup"><span data-stu-id="f900c-545">If SSH is configured for basic password authentication, then you'll be prompted for the user password.</span></span>

<span data-ttu-id="f900c-546">Als SSH is geconfigureerd voor op sleutels gebaseerde gebruikersverificatie, kan een sleutelbestandspad worden opgegeven via de parameter **KeyFilePath** en wordt er geen wachtwoordprompt gegeven.</span><span class="sxs-lookup"><span data-stu-id="f900c-546">If SSH is configured for key-based user authentication then a key file path can be provided via the **KeyFilePath** parameter and no password prompt occurs.</span></span> <span data-ttu-id="f900c-547">Als het clientgebruikerssleutelbestand zich op een bekende SSH-locatie bevindt, is de parameter **KeyFilePath** niet nodig voor verificatie op basis van een sleutel en vindt gebruikersverificatie automatisch plaats op basis van de gebruikersnaam.</span><span class="sxs-lookup"><span data-stu-id="f900c-547">If the client user key file is located in an SSH known location, then the **KeyFilePath** parameter isn't needed for key-based authentication, and user authentication occurs automatically based on the username.</span></span> <span data-ttu-id="f900c-548">Zie de SSH-documentatie van uw platform over op sleutels gebaseerde gebruikersverificatie voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f900c-548">For more information, see your platform's SSH documentation about key-based user authentication.</span></span>

<span data-ttu-id="f900c-549">Dit is geen vereiste parameter.</span><span class="sxs-lookup"><span data-stu-id="f900c-549">This isn't a required parameter.</span></span> <span data-ttu-id="f900c-550">Als de **gebruikersnaam** parameter niet is opgegeven, wordt de huidige aangemelde gebruikersnaam gebruikt voor de verbinding.</span><span class="sxs-lookup"><span data-stu-id="f900c-550">If the **UserName** parameter isn't specified, then the current logged on username is used for the connection.</span></span>

<span data-ttu-id="f900c-551">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="f900c-551">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="f900c-552">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="f900c-552">-UseSSL</span></span>

<span data-ttu-id="f900c-553">Geeft aan dat deze cmdlet het SSL-protocol (Secure Sockets Layer) gebruikt om een verbinding met de externe computer tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="f900c-553">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="f900c-554">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f900c-554">By default, SSL isn't used.</span></span>

<span data-ttu-id="f900c-555">WS-Management versleutelt alle PowerShell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="f900c-555">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="f900c-556">De **parameter UseSSL** is een extra beveiliging die de gegevens via een HTTPS verzendt in plaats van HTTP.</span><span class="sxs-lookup"><span data-stu-id="f900c-556">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span>

<span data-ttu-id="f900c-557">Als u deze parameter gebruikt, maar SSL niet beschikbaar is op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-557">If you use this parameter, but SSL isn't available on the port that's used for the command, the command fails.</span></span>

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

### <span data-ttu-id="f900c-558">-VMId</span><span class="sxs-lookup"><span data-stu-id="f900c-558">-VMId</span></span>

<span data-ttu-id="f900c-559">Hiermee geeft u een matrix van de ID's van virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="f900c-559">Specifies an array of IDs of virtual machines.</span></span>

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

### <span data-ttu-id="f900c-560">-VMName</span><span class="sxs-lookup"><span data-stu-id="f900c-560">-VMName</span></span>

<span data-ttu-id="f900c-561">Hiermee geeft u een matrix met namen van virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="f900c-561">Specifies an array of names of virtual machines.</span></span>

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

### <span data-ttu-id="f900c-562">-Subsysteem</span><span class="sxs-lookup"><span data-stu-id="f900c-562">-Subsystem</span></span>

<span data-ttu-id="f900c-563">Hiermee geeft u het SSH-subsysteem op dat wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="f900c-563">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="f900c-564">Hiermee geeft u het subsysteem op dat moet worden gebruikt op het doel, zoals gedefinieerd in sshd_config.</span><span class="sxs-lookup"><span data-stu-id="f900c-564">This specifies the subsystem to use on the target as defined in sshd_config.</span></span>
<span data-ttu-id="f900c-565">Het subsysteem start een specifieke versie van PowerShell met vooraf gedefinieerde parameters.</span><span class="sxs-lookup"><span data-stu-id="f900c-565">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span>
<span data-ttu-id="f900c-566">Als het opgegeven subsysteem niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f900c-566">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="f900c-567">Als deze parameter niet wordt gebruikt, is de standaardwaarde het subsysteem 'powershell'.</span><span class="sxs-lookup"><span data-stu-id="f900c-567">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

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

### <span data-ttu-id="f900c-568">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f900c-568">CommonParameters</span></span>

<span data-ttu-id="f900c-569">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f900c-569">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f900c-570">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f900c-570">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f900c-571">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="f900c-571">Inputs</span></span>

### <span data-ttu-id="f900c-572">System.Management.Automation.ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="f900c-572">System.Management.Automation.ScriptBlock</span></span>

<span data-ttu-id="f900c-573">U kunt een opdracht in een scriptblok doorseen naar `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="f900c-573">You can pipe a command in a script block to `Invoke-Command`.</span></span> <span data-ttu-id="f900c-574">Gebruik de `$Input` automatische variabele om de invoerobjecten in de opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f900c-574">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="f900c-575">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="f900c-575">Outputs</span></span>

### <span data-ttu-id="f900c-576">System.Management.Automation.PSRemotingJob, System.Management.Automation.Runspaces.PSSession of de uitvoer van de aangeroepen opdracht</span><span class="sxs-lookup"><span data-stu-id="f900c-576">System.Management.Automation.PSRemotingJob, System.Management.Automation.Runspaces.PSSession, or the output of the invoked command</span></span>

<span data-ttu-id="f900c-577">Deze cmdlet retourneert een taakobject als u de **parameter AsJob** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f900c-577">This cmdlet returns a job object, if you use the **AsJob** parameter.</span></span> <span data-ttu-id="f900c-578">Als u de **parameter InDisconnectedSession opgeeft,** `Invoke-Command` retourneert een **PSSession-object.**</span><span class="sxs-lookup"><span data-stu-id="f900c-578">If you specify the **InDisconnectedSession** parameter, `Invoke-Command` returns a **PSSession** object.</span></span> <span data-ttu-id="f900c-579">Anders wordt de uitvoer van de aangeroepen opdracht, de waarde van de **parameter ScriptBlock,** retourneert.</span><span class="sxs-lookup"><span data-stu-id="f900c-579">Otherwise, it returns the output of the invoked command, which is the value of the **ScriptBlock** parameter.</span></span>

## <span data-ttu-id="f900c-580">Notities</span><span class="sxs-lookup"><span data-stu-id="f900c-580">Notes</span></span>

<span data-ttu-id="f900c-581">Op Windows Vista, en latere versies van het Windows-besturingssysteem, moet u PowerShell uitvoeren met de optie Als administrator uitvoeren om de parameter **ComputerName** van te gebruiken om een opdracht uit te voeren op de lokale `Invoke-Command` computer. </span><span class="sxs-lookup"><span data-stu-id="f900c-581">On Windows Vista, and later versions of the Windows operating system, to use the **ComputerName** parameter of `Invoke-Command` to run a command on the local computer, you must run PowerShell using the **Run as administrator** option.</span></span>

<span data-ttu-id="f900c-582">Wanneer u opdrachten op meerdere computers uitvoeren, maakt PowerShell verbinding met de computers in de volgorde waarin ze worden weergegeven in de lijst.</span><span class="sxs-lookup"><span data-stu-id="f900c-582">When you run commands on multiple computers, PowerShell connects to the computers in the order in which they appear in the list.</span></span> <span data-ttu-id="f900c-583">De uitvoer van de opdracht wordt echter weergegeven in de volgorde waarin deze wordt ontvangen van de externe computers, wat mogelijk anders is.</span><span class="sxs-lookup"><span data-stu-id="f900c-583">However, the command output is displayed in the order that it's received from the remote computers, which might be different.</span></span>

<span data-ttu-id="f900c-584">Fouten die het resultaat zijn van de opdracht `Invoke-Command` die wordt uitgevoerd, zijn opgenomen in de opdrachtresultaten.</span><span class="sxs-lookup"><span data-stu-id="f900c-584">Errors that result from the command that `Invoke-Command` runs are included in the command results.</span></span>
<span data-ttu-id="f900c-585">Fouten die fouten in een lokale opdracht zouden beëindigen, worden in een externe opdracht behandeld als niet-beëindigingsfouten.</span><span class="sxs-lookup"><span data-stu-id="f900c-585">Errors that would be terminating errors in a local command are treated as non-terminating errors in a remote command.</span></span> <span data-ttu-id="f900c-586">Deze strategie zorgt ervoor dat het beëindigen van fouten op één computer de opdracht niet sluit op alle computers waarop deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-586">This strategy makes sure that terminating errors on one computer don't close the command on all computers on which it's run.</span></span> <span data-ttu-id="f900c-587">Deze oefening wordt zelfs gebruikt wanneer een externe opdracht wordt uitgevoerd op één computer.</span><span class="sxs-lookup"><span data-stu-id="f900c-587">This practice is used even when a remote command is run on a single computer.</span></span>

<span data-ttu-id="f900c-588">Als de externe computer zich niet in een domein dat de lokale computer vertrouwt, kan de computer mogelijk niet de referenties van de gebruiker verifiëren.</span><span class="sxs-lookup"><span data-stu-id="f900c-588">If the remote computer isn't in a domain that the local computer trusts, the computer might not be able to authenticate the user's credentials.</span></span> <span data-ttu-id="f900c-589">Als u de externe computer wilt toevoegen aan de lijst met vertrouwde hosts in WS-Management, gebruikt u de volgende opdracht in de provider, waarbij de naam `WSMAN` van de externe computer `<Remote-Computer-Name>` is:</span><span class="sxs-lookup"><span data-stu-id="f900c-589">To add the remote computer to the list of trusted hosts in WS-Management, use the following command in the `WSMAN` provider, where `<Remote-Computer-Name>` is the name of the remote computer:</span></span>

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

<span data-ttu-id="f900c-590">Wanneer u de verbinding met **een PSSession** verbreekt met behulp van de parameter **InDisconnectedSession,** wordt de sessietoestand **Verbroken** en is de beschikbaarheid **Geen.**</span><span class="sxs-lookup"><span data-stu-id="f900c-590">When you disconnect a **PSSession** using the **InDisconnectedSession** parameter, the session state is **Disconnected** and the availability is **None**.</span></span> <span data-ttu-id="f900c-591">De waarde van de **eigenschap State** is relatief ten opzichte van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-591">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="f900c-592">De waarde **Verbroken** betekent dat **de PSSession** niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-592">A value of **Disconnected** means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="f900c-593">Dit betekent echter niet dat de **PSSession** is losgekoppeld van alle sessies.</span><span class="sxs-lookup"><span data-stu-id="f900c-593">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="f900c-594">Deze kan zijn verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-594">It might be connected to a different session.</span></span> <span data-ttu-id="f900c-595">Gebruik de eigenschap Beschikbaarheid om te bepalen of u verbinding kunt maken of opnieuw verbinding kunt maken met **de** sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-595">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

<span data-ttu-id="f900c-596">De **waarde** Beschikbaarheid **van Geen** geeft aan dat u verbinding kunt maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-596">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="f900c-597">De waarde **Bezet geeft** aan dat u geen verbinding kunt maken met de **PSSession** omdat deze is verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="f900c-597">A value of **Busy** indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span> <span data-ttu-id="f900c-598">Zie [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)voor meer informatie over de waarden van de **eigenschap Status** van sessies.</span><span class="sxs-lookup"><span data-stu-id="f900c-598">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span> <span data-ttu-id="f900c-599">Zie [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de **eigenschap Beschikbaarheid** van sessies.</span><span class="sxs-lookup"><span data-stu-id="f900c-599">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

<span data-ttu-id="f900c-600">De **parameters HostName** en **SSHConnection** zijn vanaf PowerShell 6.0 opgenomen.</span><span class="sxs-lookup"><span data-stu-id="f900c-600">The **HostName** and **SSHConnection** parameters were included starting with PowerShell 6.0.</span></span> <span data-ttu-id="f900c-601">Ze zijn toegevoegd om powershell voor remoting te bieden op basis van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="f900c-601">They were added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="f900c-602">PowerShell en SSH worden ondersteund op meerdere platformen (Windows, Linux, macOS) en voor remoting van PowerShell werkt via deze platformen waarop PowerShell en SSH zijn geïnstalleerd en geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="f900c-602">PowerShell and SSH are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting works over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="f900c-603">Dit staat los van de vorige windows-remoting die is gebaseerd op WinRM en veel specifieke WinRM-functies en -beperkingen zijn niet van toepassing.</span><span class="sxs-lookup"><span data-stu-id="f900c-603">This is separate from the previous Windows only remoting that is based on WinRM and many of the WinRM specific features and limitations don't apply.</span></span> <span data-ttu-id="f900c-604">Bijvoorbeeld quota op basis van WinRM, sessieopties, aangepaste eindpuntconfiguratie en functies voor verbreken/opnieuw verbinden worden momenteel niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="f900c-604">For example WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="f900c-605">Zie Voor meer informatie over het instellen van SSH-remoting voor [PowerShell Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="f900c-605">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <span data-ttu-id="f900c-606">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="f900c-606">Related Links</span></span>

[<span data-ttu-id="f900c-607">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="f900c-607">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="f900c-608">about_Remote</span><span class="sxs-lookup"><span data-stu-id="f900c-608">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="f900c-609">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="f900c-609">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="f900c-610">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="f900c-610">about_Remote_Troubleshooting</span></span>](./About/about_remote_troubleshooting.md)

[<span data-ttu-id="f900c-611">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="f900c-611">about_Remote_Variables</span></span>](./About/about_Remote_Variables.md)

[<span data-ttu-id="f900c-612">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="f900c-612">about_Scopes</span></span>](./About/about_scopes.md)

[<span data-ttu-id="f900c-613">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="f900c-613">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="f900c-614">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="f900c-614">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="f900c-615">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="f900c-615">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="f900c-616">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="f900c-616">Invoke-Item</span></span>](../Microsoft.PowerShell.Management/Invoke-Item.md)

[<span data-ttu-id="f900c-617">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="f900c-617">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="f900c-618">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="f900c-618">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="f900c-619">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="f900c-619">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
