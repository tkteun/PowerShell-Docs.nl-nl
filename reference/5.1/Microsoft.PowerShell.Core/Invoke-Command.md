---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-opdracht
ms.openlocfilehash: 652ff321ea1c6507915be9748715604166207200
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251492"
---
# <span data-ttu-id="1707b-103">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="1707b-103">Invoke-Command</span></span>

## <span data-ttu-id="1707b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1707b-104">SYNOPSIS</span></span>
<span data-ttu-id="1707b-105">Voert opdrachten uit op lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="1707b-105">Runs commands on local and remote computers.</span></span>

## <span data-ttu-id="1707b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1707b-106">SYNTAX</span></span>

### <span data-ttu-id="1707b-107">Inproces (standaard)</span><span class="sxs-lookup"><span data-stu-id="1707b-107">InProcess (Default)</span></span>

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="1707b-108">Sessie</span><span class="sxs-lookup"><span data-stu-id="1707b-108">Session</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="1707b-109">FilePathRunspace</span><span class="sxs-lookup"><span data-stu-id="1707b-109">FilePathRunspace</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="1707b-110">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="1707b-110">FilePathComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="1707b-111">ComputerName</span><span class="sxs-lookup"><span data-stu-id="1707b-111">ComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="1707b-112">URI</span><span class="sxs-lookup"><span data-stu-id="1707b-112">Uri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="1707b-113">FilePathUri</span><span class="sxs-lookup"><span data-stu-id="1707b-113">FilePathUri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="1707b-114">VMId</span><span class="sxs-lookup"><span data-stu-id="1707b-114">VMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="1707b-115">VMName</span><span class="sxs-lookup"><span data-stu-id="1707b-115">VMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="1707b-116">FilePathVMId</span><span class="sxs-lookup"><span data-stu-id="1707b-116">FilePathVMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="1707b-117">FilePathVMName</span><span class="sxs-lookup"><span data-stu-id="1707b-117">FilePathVMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="1707b-118">ContainerId</span><span class="sxs-lookup"><span data-stu-id="1707b-118">ContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="1707b-119">FilePathContainerId</span><span class="sxs-lookup"><span data-stu-id="1707b-119">FilePathContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

## <span data-ttu-id="1707b-120">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1707b-120">DESCRIPTION</span></span>

<span data-ttu-id="1707b-121">De `Invoke-Command` cmdlet voert opdrachten uit op een lokale of externe computer en retourneert alle uitvoer van de opdrachten, met inbegrip van fouten.</span><span class="sxs-lookup"><span data-stu-id="1707b-121">The `Invoke-Command` cmdlet runs commands on a local or remote computer and returns all output from the commands, including errors.</span></span> <span data-ttu-id="1707b-122">Met één `Invoke-Command` opdracht kunt u opdrachten uitvoeren op meerdere computers.</span><span class="sxs-lookup"><span data-stu-id="1707b-122">Using a single `Invoke-Command` command, you can run commands on multiple computers.</span></span>

<span data-ttu-id="1707b-123">Als u één opdracht wilt uitvoeren op een externe computer, gebruikt u de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="1707b-123">To run a single command on a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="1707b-124">Als u een reeks gerelateerde opdrachten wilt uitvoeren die gegevens delen, gebruikt u de `New-PSSession` cmdlet om een **PSSession** (een permanente verbinding) te maken op de externe computer en gebruikt u vervolgens de **sessie** parameter van `Invoke-Command` om de opdracht uit te voeren in de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="1707b-124">To run a series of related commands that share data, use the `New-PSSession` cmdlet to create a **PSSession** (a persistent connection) on the remote computer, and then use the **Session** parameter of `Invoke-Command` to run the command in the **PSSession**.</span></span> <span data-ttu-id="1707b-125">Als u een opdracht wilt uitvoeren in een sessie zonder verbinding, gebruikt u de para meter **InDisconnectedSession** .</span><span class="sxs-lookup"><span data-stu-id="1707b-125">To run a command in a disconnected session, use the **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="1707b-126">Als u een opdracht in een achtergrond taak wilt uitvoeren, gebruikt u de para meter **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="1707b-126">To run a command in a background job, use the **AsJob** parameter.</span></span>

<span data-ttu-id="1707b-127">U kunt ook `Invoke-Command` op een lokale computer met een script blok als een opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-127">You can also use `Invoke-Command` on a local computer to a script block as a command.</span></span> <span data-ttu-id="1707b-128">Power Shell voert het script blok onmiddellijk uit in een onderliggend bereik van de huidige scope.</span><span class="sxs-lookup"><span data-stu-id="1707b-128">PowerShell runs the script block immediately in a child scope of the current scope.</span></span>

<span data-ttu-id="1707b-129">`Invoke-Command`Lees [about_Remote](./About/about_Remote.md)voordat u opdrachten uitvoert op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-129">Before using `Invoke-Command` to run commands on a remote computer, read [about_Remote](./About/about_Remote.md).</span></span>

<span data-ttu-id="1707b-130">Sommige code voorbeelden gebruiken splatting om de lengte van de lijn te verkleinen.</span><span class="sxs-lookup"><span data-stu-id="1707b-130">Some code samples use splatting to reduce the line length.</span></span> <span data-ttu-id="1707b-131">Zie [about_Splatting](./About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1707b-131">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="1707b-132">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1707b-132">EXAMPLES</span></span>

### <span data-ttu-id="1707b-133">Voor beeld 1: een script uitvoeren op een server</span><span class="sxs-lookup"><span data-stu-id="1707b-133">Example 1: Run a script on a server</span></span>

<span data-ttu-id="1707b-134">In dit voor beeld wordt het `Test.ps1` script op de Server01-computer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-134">This example runs the `Test.ps1` script on the Server01 computer.</span></span>

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

<span data-ttu-id="1707b-135">De **filepath** para meter geeft u een script op dat zich op de lokale computer bevindt.</span><span class="sxs-lookup"><span data-stu-id="1707b-135">The **FilePath** parameter specifies a script that is located on the local computer.</span></span> <span data-ttu-id="1707b-136">Het script wordt uitgevoerd op de externe computer en de resultaten worden geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-136">The script runs on the remote computer and the results are returned to the local computer.</span></span>

### <span data-ttu-id="1707b-137">Voor beeld 2: een opdracht uitvoeren op een externe server</span><span class="sxs-lookup"><span data-stu-id="1707b-137">Example 2: Run a command on a remote server</span></span>

<span data-ttu-id="1707b-138">In dit voor beeld wordt een `Get-Culture` opdracht uitgevoerd op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="1707b-138">This example runs a `Get-Culture` command on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

<span data-ttu-id="1707b-139">De **ComputerName** para meter geeft de naam van de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-139">The **ComputerName** parameter specifies the name of the remote computer.</span></span> <span data-ttu-id="1707b-140">De para meter **Credential** wordt gebruikt om de opdracht uit te voeren in de beveiligings context van Domain01\User01, een gebruiker die gemachtigd is om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-140">The **Credential** parameter is used to run the command in the security context of Domain01\User01, a user who has permission to run commands.</span></span> <span data-ttu-id="1707b-141">De **script Block** para meter geeft u de opdracht op die moet worden uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-141">The **ScriptBlock** parameter specifies the command to be run on the remote computer.</span></span>

<span data-ttu-id="1707b-142">Als antwoord Power shell vraagt het wacht woord en een verificatie methode voor het gebruiker01-account.</span><span class="sxs-lookup"><span data-stu-id="1707b-142">In response, PowerShell requests the password and an authentication method for the User01 account.</span></span>
<span data-ttu-id="1707b-143">Vervolgens wordt de opdracht op de computer Server01 uitgevoerd en wordt het resultaat geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-143">It then runs the command on the Server01 computer and returns the result.</span></span>

### <span data-ttu-id="1707b-144">Voor beeld 3: een opdracht uitvoeren in een permanente verbinding</span><span class="sxs-lookup"><span data-stu-id="1707b-144">Example 3: Run a command in a persistent connection</span></span>

<span data-ttu-id="1707b-145">In dit voor beeld wordt dezelfde `Get-Culture` opdracht uitgevoerd in een sessie, met behulp van een permanente verbinding op de externe computer met de naam Server02.</span><span class="sxs-lookup"><span data-stu-id="1707b-145">This example runs the same `Get-Culture` command in a session, using a persistent connection, on the remote computer named Server02.</span></span>

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="1707b-146">`New-PSSession`Met de cmdlet wordt een sessie gemaakt op de externe computer Server02 en opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-146">The `New-PSSession` cmdlet creates a session on the Server02 remote computer and saves it in the `$s` variable.</span></span> <span data-ttu-id="1707b-147">Normaal gesp roken maakt u alleen een sessie wanneer u een reeks opdrachten op de externe computer uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1707b-147">Typically, you create a session only when you run a series of commands on the remote computer.</span></span>

<span data-ttu-id="1707b-148">`Invoke-Command`Met de cmdlet wordt de `Get-Culture` opdracht uitgevoerd op Server02.</span><span class="sxs-lookup"><span data-stu-id="1707b-148">The `Invoke-Command` cmdlet runs the `Get-Culture` command on Server02.</span></span> <span data-ttu-id="1707b-149">Met de **sessie** parameter wordt de sessie opgegeven die is opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-149">The **Session** parameter specifies the session saved in the `$s` variable.</span></span>

<span data-ttu-id="1707b-150">Als antwoord Power Shell voert de opdracht uit in de sessie op de Server02-computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-150">In response, PowerShell runs the command in the session on the Server02 computer.</span></span>

### <span data-ttu-id="1707b-151">Voor beeld 4: een sessie gebruiken om een reeks opdrachten uit te voeren die gegevens delen</span><span class="sxs-lookup"><span data-stu-id="1707b-151">Example 4: Use a session to run a series of commands that share data</span></span>

<span data-ttu-id="1707b-152">In dit voor beeld worden de gevolgen van **computer naam** en **sessie** parameters van gebruikt `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="1707b-152">This example compares the effects of using **ComputerName** and **Session** parameters of `Invoke-Command`.</span></span> <span data-ttu-id="1707b-153">U ziet hoe u een sessie gebruikt om een reeks opdrachten uit te voeren die dezelfde gegevens delen.</span><span class="sxs-lookup"><span data-stu-id="1707b-153">It shows how to use a session to run a series of commands that share the same data.</span></span>

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

<span data-ttu-id="1707b-154">De eerste twee opdrachten gebruiken de para meter **ComputerName** van `Invoke-Command` om opdrachten uit te voeren op de externe computer Server02.</span><span class="sxs-lookup"><span data-stu-id="1707b-154">The first two commands use the **ComputerName** parameter of `Invoke-Command` to run commands on the Server02 remote computer.</span></span> <span data-ttu-id="1707b-155">De eerste opdracht gebruikt de `Get-Process` cmdlet om het Power Shell-proces op de externe computer op te halen en om het in de variabele op te slaan `$p` .</span><span class="sxs-lookup"><span data-stu-id="1707b-155">The first command uses the `Get-Process` cmdlet to get the PowerShell process on the remote computer and to save it in the `$p` variable.</span></span> <span data-ttu-id="1707b-156">Met de tweede opdracht wordt de waarde van de eigenschap **VirtualMemorySize** van het Power Shell-proces opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1707b-156">The second command gets the value of the **VirtualMemorySize** property of the PowerShell process.</span></span>

<span data-ttu-id="1707b-157">Wanneer u de para meter **ComputerName** gebruikt, maakt Power shell een nieuwe sessie om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-157">When you use the **ComputerName** parameter, PowerShell creates a new session to run the command.</span></span>
<span data-ttu-id="1707b-158">De sessie wordt gesloten wanneer de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="1707b-158">The session is closed when the command completes.</span></span> <span data-ttu-id="1707b-159">De `$p` variabele is gemaakt in één verbinding, maar bestaat niet in de verbinding die is gemaakt voor de tweede opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-159">The `$p` variable was created in one connection, but it doesn't exist in the connection created for the second command.</span></span>

<span data-ttu-id="1707b-160">Het probleem wordt opgelost door een permanente sessie te maken op de externe computer en vervolgens beide opdrachten in dezelfde sessie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-160">The problem is solved by creating a persistent session on the remote computer, then running both of the commands in the same session.</span></span>

<span data-ttu-id="1707b-161">Met de `New-PSSession` cmdlet wordt een permanente sessie gemaakt op de computer Server02 en wordt de sessie opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-161">The `New-PSSession` cmdlet creates a persistent session on the computer Server02 and saves the session in the `$s` variable.</span></span> <span data-ttu-id="1707b-162">`Invoke-Command`Op de regels die volgen, wordt de para meter **Session** gebruikt om beide opdrachten in dezelfde sessie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-162">The `Invoke-Command` lines that follow use the **Session** parameter to run both of the commands in the same session.</span></span> <span data-ttu-id="1707b-163">Omdat beide opdrachten in dezelfde sessie worden uitgevoerd, `$p` blijft de waarde actief.</span><span class="sxs-lookup"><span data-stu-id="1707b-163">Since both commands run in the same session, the `$p` value remains active.</span></span>

### <span data-ttu-id="1707b-164">Voor beeld 5: Voer een opdracht in die is opgeslagen in een lokale variabele</span><span class="sxs-lookup"><span data-stu-id="1707b-164">Example 5: Enter a command stored in a local variable</span></span>

<span data-ttu-id="1707b-165">In dit voor beeld ziet u hoe u een opdracht maakt die is opgeslagen als een script blok in een lokale variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-165">This example shows how to create a command that is stored as a script block in a local variable.</span></span>
<span data-ttu-id="1707b-166">Wanneer het script blok wordt opgeslagen in een lokale variabele, kunt u de variabele opgeven als de waarde van de para meter **script Block** .</span><span class="sxs-lookup"><span data-stu-id="1707b-166">When the script block is saved in a local variable, you can specify the variable as the value of the **ScriptBlock** parameter.</span></span>

```powershell
$command = { Get-EventLog -LogName "Windows PowerShell" |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

<span data-ttu-id="1707b-167">De `$command` variabele slaat de `Get-EventLog` opdracht op die is opgemaakt als een script blok.</span><span class="sxs-lookup"><span data-stu-id="1707b-167">The `$command` variable stores the `Get-EventLog` command that's formatted as a script block.</span></span> <span data-ttu-id="1707b-168">Hiermee `Invoke-Command` wordt de opdracht uitgevoerd die is opgeslagen in `$command` op de externe computers S1 en S2.</span><span class="sxs-lookup"><span data-stu-id="1707b-168">The `Invoke-Command` runs the command stored in `$command` on the S1 and S2 remote computers.</span></span>

### <span data-ttu-id="1707b-169">Voor beeld 6: één opdracht op meerdere computers uitvoeren</span><span class="sxs-lookup"><span data-stu-id="1707b-169">Example 6: Run a single command on several computers</span></span>

<span data-ttu-id="1707b-170">In dit voor beeld ziet u hoe u kunt gebruiken `Invoke-Command` om één opdracht op meerdere computers uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-170">This example demonstrates how to use `Invoke-Command` to run a single command on multiple computers.</span></span>

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-EventLog "Windows PowerShell" }
}
Invoke-Command @parameters
```

<span data-ttu-id="1707b-171">De para meter **ComputerName** bevat een door komma's gescheiden lijst met computer namen.</span><span class="sxs-lookup"><span data-stu-id="1707b-171">The **ComputerName** parameter specifies a comma-separated list of computer names.</span></span> <span data-ttu-id="1707b-172">De lijst met computers bevat de localhost-waarde, die de lokale computer vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1707b-172">The list of computers includes the localhost value, which represents the local computer.</span></span> <span data-ttu-id="1707b-173">Met de para meter **configuratiepad** wordt een alternatieve sessie configuratie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1707b-173">The **ConfigurationName** parameter specifies an alternate session configuration.</span></span> <span data-ttu-id="1707b-174">De para meter **script Block** wordt uitgevoerd `Get-EventLog` om de Windows Power shell-gebeurtenis logboeken van elke computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="1707b-174">The **ScriptBlock** parameter runs `Get-EventLog` to get the Windows PowerShell event logs from each computer.</span></span>

### <span data-ttu-id="1707b-175">Voor beeld 7: de versie van het hostprogramma op meerdere computers ophalen</span><span class="sxs-lookup"><span data-stu-id="1707b-175">Example 7: Get the version of the host program on multiple computers</span></span>

<span data-ttu-id="1707b-176">In dit voor beeld wordt de versie van het Power shell-host-programma uitgevoerd op 200 externe computers.</span><span class="sxs-lookup"><span data-stu-id="1707b-176">This example gets the version of the PowerShell host program running on 200 remote computers.</span></span>

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

<span data-ttu-id="1707b-177">Omdat er slechts één opdracht wordt uitgevoerd, hoeft u geen permanente verbindingen te maken met elk van de computers.</span><span class="sxs-lookup"><span data-stu-id="1707b-177">Because only one command is run, you don't have to create persistent connections to each of the computers.</span></span> <span data-ttu-id="1707b-178">In plaats daarvan gebruikt de opdracht de para meter **ComputerName** om de computers aan te geven.</span><span class="sxs-lookup"><span data-stu-id="1707b-178">Instead, the command uses the **ComputerName** parameter to indicate the computers.</span></span> <span data-ttu-id="1707b-179">Als u de computers wilt opgeven, wordt de `Get-Content` cmdlet gebruikt om de inhoud van het Machine.txt bestand, een bestand met computer namen, op te halen.</span><span class="sxs-lookup"><span data-stu-id="1707b-179">To specify the computers, it uses the `Get-Content` cmdlet to get the contents of the Machine.txt file, a file of computer names.</span></span>

<span data-ttu-id="1707b-180">`Invoke-Command`Met de cmdlet wordt een `Get-Host` opdracht op de externe computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-180">The `Invoke-Command` cmdlet runs a `Get-Host` command on the remote computers.</span></span> <span data-ttu-id="1707b-181">De teken punt notatie wordt gebruikt om de eigenschap **Version** van de Power shell-host op te halen.</span><span class="sxs-lookup"><span data-stu-id="1707b-181">It uses dot notation to get the **Version** property of the PowerShell host.</span></span>

<span data-ttu-id="1707b-182">Deze opdrachten worden een voor een uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-182">These commands run one at a time.</span></span> <span data-ttu-id="1707b-183">Wanneer de opdrachten zijn voltooid, wordt de uitvoer van de opdrachten van alle computers in de variabele opgeslagen `$version` .</span><span class="sxs-lookup"><span data-stu-id="1707b-183">When the commands complete, the output of the commands from all of the computers is saved in the `$version` variable.</span></span> <span data-ttu-id="1707b-184">De uitvoer bevat de naam van de computer waarvan de gegevens afkomstig zijn.</span><span class="sxs-lookup"><span data-stu-id="1707b-184">The output includes the name of the computer from which the data originated.</span></span>

### <span data-ttu-id="1707b-185">Voor beeld 8: een achtergrond taak op meerdere externe computers uitvoeren</span><span class="sxs-lookup"><span data-stu-id="1707b-185">Example 8: Run a background job on several remote computers</span></span>

<span data-ttu-id="1707b-186">In dit voor beeld wordt een opdracht op twee externe computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-186">This example runs a command on two remote computers.</span></span> <span data-ttu-id="1707b-187">De `Invoke-Command` opdracht maakt gebruik van de para meter **AsJob** , zodat de opdracht als achtergrond taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-187">The `Invoke-Command` command uses the **AsJob** parameter so that the command runs as a background job.</span></span> <span data-ttu-id="1707b-188">De opdrachten worden uitgevoerd op de externe computers, maar de taak bestaat op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-188">The commands run on the remote computers, but the job exists on the local computer.</span></span> <span data-ttu-id="1707b-189">De resultaten worden verzonden naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-189">The results are transmitted to the local computer.</span></span>

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

<span data-ttu-id="1707b-190">De `New-PSSession` cmdlet maakt sessies op de externe computers Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="1707b-190">The `New-PSSession` cmdlet creates sessions on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="1707b-191">De `Invoke-Command` cmdlet voert een achtergrond taak in elk van de sessies uit.</span><span class="sxs-lookup"><span data-stu-id="1707b-191">The `Invoke-Command` cmdlet runs a background job in each of the sessions.</span></span> <span data-ttu-id="1707b-192">De opdracht gebruikt de para meter **AsJob** om de opdracht als achtergrond taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-192">The command uses the **AsJob** parameter to run the command as a background job.</span></span> <span data-ttu-id="1707b-193">Met deze opdracht wordt een taak object geretourneerd dat twee onderliggende taak objecten bevat, één voor elk van de taken die op de twee externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-193">This command returns a job object that contains two child job objects, one for each of the jobs run on the two remote computers.</span></span>

<span data-ttu-id="1707b-194">De `Get-Job` opdracht slaat het taak object op in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-194">The `Get-Job` command saves the job object in the `$j` variable.</span></span> <span data-ttu-id="1707b-195">De `$j` variabele wordt vervolgens naar de cmdlet geleid `Format-List` om alle eigenschappen van het taak object in een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1707b-195">The `$j` variable is then piped to the `Format-List` cmdlet to display all properties of the job object in a list.</span></span> <span data-ttu-id="1707b-196">Met de laatste opdracht worden de resultaten van de taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1707b-196">The last command gets the results of the jobs.</span></span> <span data-ttu-id="1707b-197">Hiermee wordt het taak object in `$j` naar de `Receive-Job` cmdlet sluizen en worden de resultaten opgeslagen in de `$results` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-197">It pipes the job object in `$j` to the `Receive-Job` cmdlet and stores the results in the `$results` variable.</span></span>

### <span data-ttu-id="1707b-198">Voor beeld 9: lokale variabelen insluiten in een opdracht die wordt uitgevoerd op een externe computer</span><span class="sxs-lookup"><span data-stu-id="1707b-198">Example 9: Include local variables in a command run on a remote computer</span></span>

<span data-ttu-id="1707b-199">In dit voor beeld ziet u hoe u de waarden van lokale variabelen opneemt in een opdracht die wordt uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-199">This example shows how to include the values of local variables in a command run on a remote computer.</span></span> <span data-ttu-id="1707b-200">De opdracht gebruikt de `Using` aanpassings functie van het bereik om een lokale variabele in een externe opdracht te identificeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-200">The command uses the `Using` scope modifier to identify a local variable in a remote command.</span></span> <span data-ttu-id="1707b-201">Standaard worden alle variabelen geacht te zijn gedefinieerd in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="1707b-201">By default, all variables are assumed to be defined in the remote session.</span></span> <span data-ttu-id="1707b-202">De `Using` aanpassing van het bereik is geïntroduceerd in Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1707b-202">The `Using` scope modifier was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="1707b-203">`Using`Zie [about_Remote_Variables](./About/about_Remote_Variables.md) en [about_Scopes](./about/about_scopes.md)voor meer informatie over de aanpassing van het bereik.</span><span class="sxs-lookup"><span data-stu-id="1707b-203">For more information about the `Using` scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md) and [about_Scopes](./about/about_scopes.md).</span></span>

```powershell
$Log = "Windows PowerShell"
Invoke-Command -ComputerName Server01 -ScriptBlock { Get-EventLog -LogName $Using:Log -Newest 10 }
```

<span data-ttu-id="1707b-204">De `$Log` variabele bevat de naam van het gebeurtenis logboek, Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="1707b-204">The `$Log` variable stores the name of the event log, Windows PowerShell.</span></span> <span data-ttu-id="1707b-205">De `Invoke-Command` cmdlet wordt uitgevoerd `Get-EventLog` op Server01 om de tien nieuwste gebeurtenissen uit het gebeurtenis logboek op te halen.</span><span class="sxs-lookup"><span data-stu-id="1707b-205">The `Invoke-Command` cmdlet runs `Get-EventLog` on Server01 to get the ten newest events from the event log.</span></span> <span data-ttu-id="1707b-206">De waarde van de para meter **LogName** is de `$Log` variabele, die wordt voorafgegaan door de `Using` wijzigings functie van het bereik om aan te geven dat deze is gemaakt in de lokale sessie, niet in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="1707b-206">The value of the **LogName** parameter is the `$Log` variable, which is prefixed by the `Using` scope modifier to indicate that it was created in the local session, not in the remote session.</span></span>

### <span data-ttu-id="1707b-207">Voor beeld 10: de computer naam verbergen</span><span class="sxs-lookup"><span data-stu-id="1707b-207">Example 10: Hide the computer name</span></span>

<span data-ttu-id="1707b-208">In dit voor beeld ziet u het effect van het gebruik van de para meter **HideComputerName** van `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="1707b-208">This example shows the effect of using the **HideComputerName** parameter of `Invoke-Command`.</span></span>
<span data-ttu-id="1707b-209">**HideComputerName** heeft geen invloed op het object dat met deze cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-209">**HideComputerName** doesn't change the object that this cmdlet returns.</span></span> <span data-ttu-id="1707b-210">Alleen de weer gave wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="1707b-210">It changes only the display.</span></span> <span data-ttu-id="1707b-211">U kunt nog steeds de **Format** -cmdlets gebruiken om de eigenschap **PsComputerName** van de betrokken objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1707b-211">You can still use the **Format** cmdlets to display the **PsComputerName** property of any of the affected objects.</span></span>

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

<span data-ttu-id="1707b-212">De eerste twee opdrachten gebruiken `Invoke-Command` om een `Get-Process` opdracht voor het Power Shell-proces uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-212">The first two commands use `Invoke-Command` to run a `Get-Process` command for the PowerShell process.</span></span> <span data-ttu-id="1707b-213">De uitvoer van de eerste opdracht bevat de eigenschap **PsComputerName** , die de naam bevat van de computer waarop de opdracht is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-213">The output of the first command includes the **PsComputerName** property, which contains the name of the computer on which the command ran.</span></span> <span data-ttu-id="1707b-214">De uitvoer van de tweede opdracht, die gebruikmaakt van **HideComputerName** , bevat niet de kolom **PsComputerName** .</span><span class="sxs-lookup"><span data-stu-id="1707b-214">The output of the second command, which uses **HideComputerName** , doesn't include the **PsComputerName** column.</span></span>

### <span data-ttu-id="1707b-215">Voor beeld 11: het sleutel woord param in een script blok gebruiken</span><span class="sxs-lookup"><span data-stu-id="1707b-215">Example 11: Use the Param keyword in a script block</span></span>

<span data-ttu-id="1707b-216">Het `Param` sleutel woord en de para meter **argument List** worden gebruikt om variabele waarden door te geven aan benoemde para meters in een-script blok.</span><span class="sxs-lookup"><span data-stu-id="1707b-216">The `Param` keyword and the **ArgumentList** parameter are used to pass variable values to named parameters in a script block.</span></span> <span data-ttu-id="1707b-217">In dit voor beeld worden bestands namen weer gegeven die beginnen met de letter `a` en de `.pdf` uitbrei ding hebben.</span><span class="sxs-lookup"><span data-stu-id="1707b-217">This example displays filenames that begin with the letter `a` and have the `.pdf` extension.</span></span>

<span data-ttu-id="1707b-218">Zie about_Language_Keywords voor meer informatie over het `Param` tref [about_Language_Keywords](./about/about_language_keywords.md#param)woord.</span><span class="sxs-lookup"><span data-stu-id="1707b-218">For more information about the `Param` keyword, see [about_Language_Keywords](./about/about_language_keywords.md#param).</span></span>

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

<span data-ttu-id="1707b-219">`Invoke-Command` maakt gebruik van de para meter **script Block** die twee variabelen definieert, `$param1` en `$param2` .</span><span class="sxs-lookup"><span data-stu-id="1707b-219">`Invoke-Command` uses the **ScriptBlock** parameter that defines two variables, `$param1` and `$param2`.</span></span> <span data-ttu-id="1707b-220">`Get-ChildItem` maakt gebruik van de benoemde para meters, **naam** en **bevatten** met de namen van variabelen.</span><span class="sxs-lookup"><span data-stu-id="1707b-220">`Get-ChildItem` uses the named parameters, **Name** and **Include** with the variable names.</span></span> <span data-ttu-id="1707b-221">De **argument List** geeft de waarden door aan de variabelen.</span><span class="sxs-lookup"><span data-stu-id="1707b-221">The **ArgumentList** passes the values to the variables.</span></span>

### <span data-ttu-id="1707b-222">Voor beeld 12: de $args automatische variabele in een script blok gebruiken</span><span class="sxs-lookup"><span data-stu-id="1707b-222">Example 12: Use the $args automatic variable in a script block</span></span>

<span data-ttu-id="1707b-223">De `$args` Automatische variabele en de para meter **argument List** worden gebruikt om matrix waarden door te geven aan parameter posities in een-script blok.</span><span class="sxs-lookup"><span data-stu-id="1707b-223">The `$args` automatic variable and the **ArgumentList** parameter are used to pass array values to parameter positions in a script block.</span></span> <span data-ttu-id="1707b-224">In dit voor beeld wordt de mapinhoud van de server weer gegeven `.txt` .</span><span class="sxs-lookup"><span data-stu-id="1707b-224">This example displays a server's directory contents of `.txt` files.</span></span> <span data-ttu-id="1707b-225">De `Get-ChildItem` para meter **Path** is positie 0 en de **filter** parameter is positie</span><span class="sxs-lookup"><span data-stu-id="1707b-225">The `Get-ChildItem` **Path** parameter is position 0 and the **Filter** parameter is position</span></span>
1.

<span data-ttu-id="1707b-226">Zie about_Automatic_Variables voor meer informatie over de `$args` variabele [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span><span class="sxs-lookup"><span data-stu-id="1707b-226">For more information about the `$args` variable, see [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span></span>

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

<span data-ttu-id="1707b-227">`Invoke-Command` Hiermee wordt een **script Block** -para meter gebruikt en worden `Get-ChildItem` de-en- `$args[0]` `$args[1]` matrix waarden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1707b-227">`Invoke-Command` uses a **ScriptBlock** parameter and `Get-ChildItem` specifies the `$args[0]` and `$args[1]` array values.</span></span> <span data-ttu-id="1707b-228">De **argument List** geeft de `$args` matrix waarden door aan de `Get-ChildItem` parameter posities voor **Path** en **filter**.</span><span class="sxs-lookup"><span data-stu-id="1707b-228">The **ArgumentList** passes the `$args` array values to the `Get-ChildItem` parameter positions for **Path** and **Filter**.</span></span>

### <span data-ttu-id="1707b-229">Voor beeld 13: een script uitvoeren op alle computers die worden vermeld in een tekst bestand</span><span class="sxs-lookup"><span data-stu-id="1707b-229">Example 13: Run a script on all the computers listed in a text file</span></span>

<span data-ttu-id="1707b-230">In dit voor beeld wordt de `Invoke-Command` cmdlet gebruikt om het script uit te voeren `Sample.ps1` op alle computers die worden vermeld in het `Servers.txt` bestand.</span><span class="sxs-lookup"><span data-stu-id="1707b-230">This example uses the `Invoke-Command` cmdlet to run the `Sample.ps1` script on all the computers listed in the `Servers.txt` file.</span></span> <span data-ttu-id="1707b-231">De opdracht gebruikt de **filepath** -para meter om het script bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="1707b-231">The command uses the **FilePath** parameter to specify the script file.</span></span> <span data-ttu-id="1707b-232">Met deze opdracht kunt u het script uitvoeren op de externe computers, zelfs als het script bestand niet toegankelijk is voor de externe computers.</span><span class="sxs-lookup"><span data-stu-id="1707b-232">This command lets you run the script on the remote computers, even if the script file isn't accessible to the remote computers.</span></span>

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

<span data-ttu-id="1707b-233">Wanneer u de opdracht verzendt, wordt de inhoud van het `Sample.ps1` bestand gekopieerd naar een script blok en wordt het script blok op elke externe computer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-233">When you submit the command, the content of the `Sample.ps1` file is copied into a script block and the script block is run on each of the remote computers.</span></span> <span data-ttu-id="1707b-234">Deze procedure is gelijk aan het gebruik van de para meter **script Block** om de inhoud van het script te verzenden.</span><span class="sxs-lookup"><span data-stu-id="1707b-234">This procedure is equivalent to using the **ScriptBlock** parameter to submit the contents of the script.</span></span>

### <span data-ttu-id="1707b-235">Voor beeld 14: een opdracht uitvoeren op een externe computer met behulp van een URI</span><span class="sxs-lookup"><span data-stu-id="1707b-235">Example 14: Run a command on a remote computer using a URI</span></span>

<span data-ttu-id="1707b-236">In dit voor beeld ziet u hoe u een opdracht uitvoert op een externe computer die wordt geïdentificeerd door een URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="1707b-236">This example shows how to run a command on a remote computer that's identified by a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="1707b-237">In dit voor beeld wordt een `Set-Mailbox` opdracht uitgevoerd op een externe Exchange-Server.</span><span class="sxs-lookup"><span data-stu-id="1707b-237">This particular example runs a `Set-Mailbox` command on a remote Exchange server.</span></span>

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

<span data-ttu-id="1707b-238">De eerste regel gebruikt de `Get-Credential` cmdlet voor het opslaan van Windows Live ID-referenties in de `$LiveCred` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-238">The first line uses the `Get-Credential` cmdlet to store Windows Live ID credentials in the `$LiveCred` variable.</span></span> <span data-ttu-id="1707b-239">Power shell vraagt de gebruiker om Windows Live ID-referenties in te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-239">PowerShell prompts the user to enter Windows Live ID credentials.</span></span>

<span data-ttu-id="1707b-240">De `$parameters` variabele is een hash-tabel met de para meters die moeten worden door gegeven aan de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1707b-240">The `$parameters` variable is a hash table containing the parameters to be passed to the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="1707b-241">`Invoke-Command`Met de cmdlet wordt een `Set-Mailbox` opdracht uitgevoerd met behulp van de **micro soft. Exchange** -sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="1707b-241">The `Invoke-Command` cmdlet runs a `Set-Mailbox` command using the **Microsoft.Exchange** session configuration.</span></span> <span data-ttu-id="1707b-242">De **ConnectionURI** para meter geeft u de URL van het Exchange Server-eind punt.</span><span class="sxs-lookup"><span data-stu-id="1707b-242">The **ConnectionURI** parameter specifies the URL of the Exchange server endpoint.</span></span> <span data-ttu-id="1707b-243">De **referentie** parameter bevat de referenties die zijn opgeslagen in de `$LiveCred` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-243">The **Credential** parameter specifies the credentials stored in the `$LiveCred` variable.</span></span> <span data-ttu-id="1707b-244">De para meter **AuthenticationMechanism** bepaalt het gebruik van basis verificatie.</span><span class="sxs-lookup"><span data-stu-id="1707b-244">The **AuthenticationMechanism** parameter specifies the use of basic authentication.</span></span> <span data-ttu-id="1707b-245">De para meter **script Block** geeft een script blok dat de opdracht bevat.</span><span class="sxs-lookup"><span data-stu-id="1707b-245">The **ScriptBlock** parameter specifies a script block that contains the command.</span></span>

### <span data-ttu-id="1707b-246">Voor beeld 15: een sessie optie gebruiken</span><span class="sxs-lookup"><span data-stu-id="1707b-246">Example 15: Use a session option</span></span>

<span data-ttu-id="1707b-247">In dit voor beeld ziet u hoe u een **SessionOption** -para meter maakt en gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1707b-247">This example shows how to create and use a **SessionOption** parameter.</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

<span data-ttu-id="1707b-248">De `New-PSSessionOption` cmdlet maakt een sessie optie object dat ervoor zorgt dat het externe einde de certificerings instantie, canonieke naam en intrekkings lijsten niet verifieert tijdens het evalueren van de binnenkomende https-verbinding.</span><span class="sxs-lookup"><span data-stu-id="1707b-248">The `New-PSSessionOption` cmdlet creates a session option object that causes the remote end not to verify the Certificate Authority, Canonical Name, and Revocation Lists while evaluating the incoming HTTPS connection.</span></span> <span data-ttu-id="1707b-249">Het **SessionOption** -object wordt opgeslagen in de `$so` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-249">The **SessionOption** object is saved in the `$so` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="1707b-250">Het uitschakelen van deze controles is handig voor het oplossen van problemen, maar is uiteraard niet veilig.</span><span class="sxs-lookup"><span data-stu-id="1707b-250">Disabling these checks is convenient for troubleshooting, but obviously not secure.</span></span>

<span data-ttu-id="1707b-251">Met de `Invoke-Command` cmdlet wordt `Get-HotFix` op afstand een opdracht uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-251">The `Invoke-Command` cmdlet runs a `Get-HotFix` command remotely.</span></span> <span data-ttu-id="1707b-252">De **SessionOption** -para meter krijgt de `$so` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-252">The **SessionOption** parameter is given the `$so` variable.</span></span>

### <span data-ttu-id="1707b-253">Voor beeld 16: URI-omleiding beheren in een externe opdracht</span><span class="sxs-lookup"><span data-stu-id="1707b-253">Example 16: Manage URI redirection in a remote command</span></span>

<span data-ttu-id="1707b-254">In dit voor beeld ziet u hoe u de para meters **AllowRedirection** en **SessionOption** gebruikt voor het beheren van URI-omleiding in een externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-254">This example shows how to use the **AllowRedirection** and **SessionOption** parameters to manage URI redirection in a remote command.</span></span>

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

<span data-ttu-id="1707b-255">`New-PSSessionOption`Met de cmdlet maakt u een **PSSessionOption** -object dat is opgeslagen in de `$max` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-255">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object that is saved in the `$max` variable.</span></span> <span data-ttu-id="1707b-256">De opdracht gebruikt de para meter **MaximumRedirection** om de eigenschap **MaximumConnectionRedirectionCount** van het object **PSSessionOption** in te stellen op 1.</span><span class="sxs-lookup"><span data-stu-id="1707b-256">The command uses the **MaximumRedirection** parameter to set the **MaximumConnectionRedirectionCount** property of the **PSSessionOption** object to 1.</span></span>

<span data-ttu-id="1707b-257">`Invoke-Command`Met de cmdlet wordt een `Get-Mailbox` opdracht uitgevoerd op een externe micro soft Exchange-Server.</span><span class="sxs-lookup"><span data-stu-id="1707b-257">The `Invoke-Command` cmdlet runs a `Get-Mailbox` command on a remote Microsoft Exchange Server.</span></span> <span data-ttu-id="1707b-258">De para meter **AllowRedirection** biedt expliciete machtigingen voor het omleiden van de verbinding met een ander eind punt.</span><span class="sxs-lookup"><span data-stu-id="1707b-258">The **AllowRedirection** parameter provides explicit permission to redirect the connection to an alternate endpoint.</span></span> <span data-ttu-id="1707b-259">De para meter **SessionOption** maakt gebruik van het sessie object dat is opgeslagen in de `$max` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-259">The **SessionOption** parameter uses the session object stored in the `$max` variable.</span></span>

<span data-ttu-id="1707b-260">Als de externe computer die wordt opgegeven door **ConnectionURI** een omleidings bericht retourneert, wordt de verbinding door Power shell omgeleid, maar als de nieuwe bestemming een andere omleidings bericht retourneert, wordt de waarde van het aantal omleidingen van 1 overschreden en `Invoke-Command` wordt een niet-afsluit fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-260">As a result, if the remote computer specified by **ConnectionURI** returns a redirection message, PowerShell redirects the connection, but if the new destination returns another redirection message, the redirection count value of 1 is exceeded, and `Invoke-Command` returns a non-terminating error.</span></span>

### <span data-ttu-id="1707b-261">Voor beeld 17: toegang tot een netwerk share in een externe sessie</span><span class="sxs-lookup"><span data-stu-id="1707b-261">Example 17: Access a network share in a remote session</span></span>

<span data-ttu-id="1707b-262">In dit voor beeld ziet u hoe u een netwerk share opent vanuit een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="1707b-262">This example shows how to access a network share from a remote session.</span></span> <span data-ttu-id="1707b-263">Er worden drie computers gebruikt om het voor beeld te demonstreren.</span><span class="sxs-lookup"><span data-stu-id="1707b-263">Three computers are used to demonstrate the example.</span></span> <span data-ttu-id="1707b-264">Server01 is de lokale computer, Server02 is de externe computer en Net03 bevat de netwerk share.</span><span class="sxs-lookup"><span data-stu-id="1707b-264">Server01 is the local computer, Server02 is the remote computer, and Net03 contains the network share.</span></span> <span data-ttu-id="1707b-265">Server01 maakt verbinding met Server02 en vervolgens wordt Server02 een tweede hop naar Net03 om toegang te krijgen tot de netwerk share.</span><span class="sxs-lookup"><span data-stu-id="1707b-265">Server01 connects to Server02, and then Server02 does a second hop to Net03 to access the network share.</span></span> <span data-ttu-id="1707b-266">Zie [de tweede hop in Power shell Remoting maken](/powershell/scripting/learn/remoting/ps-remoting-second-hop)voor meer informatie over de manier waarop externe communicatie tussen computers door Power shell wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="1707b-266">For more information about how PowerShell Remoting supports hops between computers, see [Making the second hop in PowerShell Remoting](/powershell/scripting/learn/remoting/ps-remoting-second-hop).</span></span>

<span data-ttu-id="1707b-267">De vereiste CredSSP-overdracht (Credential Security Support Provider) is ingeschakeld in de client instellingen op de lokale computer en in de service-instellingen op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-267">The required Credential Security Support Provider (CredSSP) delegation is enabled in the client settings on the local computer, and in the service settings on the remote computer.</span></span> <span data-ttu-id="1707b-268">Als u de opdrachten in dit voor beeld wilt uitvoeren, moet u lid zijn van de groep **Administrators** op de lokale computer en de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-268">To run the commands in this example, you must be a member of the **Administrators** group on the local computer and the remote computer.</span></span>

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

<span data-ttu-id="1707b-269">`Enable-WSManCredSSP`Met de cmdlet wordt CredSSP delegering van de lokale Server01-computer naar de externe computer van Server02 ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="1707b-269">The `Enable-WSManCredSSP` cmdlet enables CredSSP delegation from the Server01 local computer to the Server02 remote computer.</span></span> <span data-ttu-id="1707b-270">De para meter **Role** specificeert de **client** voor het configureren van de CredSSP client-instelling op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-270">The **Role** parameter specifies **Client** to configure the CredSSP client setting on the local computer.</span></span>

<span data-ttu-id="1707b-271">`New-PSSession` Hiermee maakt u een **PSSession** -object voor Server02 en slaat u het object op in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-271">`New-PSSession` creates a **PSSession** object for Server02 and stores the object in the `$s` variable.</span></span>

<span data-ttu-id="1707b-272">De `Invoke-Command` cmdlet gebruikt de `$s` variabele om verbinding te maken met de externe computer, Server02.</span><span class="sxs-lookup"><span data-stu-id="1707b-272">The `Invoke-Command` cmdlet uses the `$s` variable to connect to the remote computer, Server02.</span></span> <span data-ttu-id="1707b-273">De para meter **script Block** wordt uitgevoerd `Enable-WSManCredSSP` op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-273">The **ScriptBlock** parameter runs `Enable-WSManCredSSP` on the remote computer.</span></span> <span data-ttu-id="1707b-274">De para meter **Role** specificeert de **Server** voor het configureren van de CredSSP-server instelling op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-274">The **Role** parameter specifies **Server** to configure the CredSSP server setting on the remote computer.</span></span>

<span data-ttu-id="1707b-275">De `$parameters` variabele bevat de parameter waarden om verbinding te maken met de netwerk share.</span><span class="sxs-lookup"><span data-stu-id="1707b-275">The `$parameters` variable contains the parameter values to connect to the network share.</span></span> <span data-ttu-id="1707b-276">De `Invoke-Command` cmdlet voert een `Get-Item` opdracht in de sessie in uit `$s` .</span><span class="sxs-lookup"><span data-stu-id="1707b-276">The `Invoke-Command` cmdlet runs a `Get-Item` command in the session in `$s`.</span></span> <span data-ttu-id="1707b-277">Met deze opdracht wordt een script opgehaald van de `\\Net03\Scripts` netwerk share.</span><span class="sxs-lookup"><span data-stu-id="1707b-277">This command gets a script from the `\\Net03\Scripts` network share.</span></span> <span data-ttu-id="1707b-278">De opdracht gebruikt de **verificatie** parameter met de waarde **CredSSP** en de para meter **Credential** met de waarde **Domain01\Admin01**.</span><span class="sxs-lookup"><span data-stu-id="1707b-278">The command uses the **Authentication** parameter with a value of **CredSSP** and the **Credential** parameter with a value of **Domain01\Admin01**.</span></span>

### <span data-ttu-id="1707b-279">Voor beeld 18: scripts op veel externe computers starten</span><span class="sxs-lookup"><span data-stu-id="1707b-279">Example 18: Start scripts on many remote computers</span></span>

<span data-ttu-id="1707b-280">In dit voor beeld wordt een script uitgevoerd op meer dan honderd computers.</span><span class="sxs-lookup"><span data-stu-id="1707b-280">This example runs a script on more than a hundred computers.</span></span> <span data-ttu-id="1707b-281">Om de impact op de lokale computer tot een minimum te beperken, wordt er verbinding gemaakt met elke computer, wordt het script gestart en wordt de verbinding met elke computer verbroken.</span><span class="sxs-lookup"><span data-stu-id="1707b-281">To minimize the impact on the local computer, it connects to each computer, starts the script, and then disconnects from each computer.</span></span>
<span data-ttu-id="1707b-282">Het script wordt nog steeds uitgevoerd in de verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="1707b-282">The script continues to run in the disconnected sessions.</span></span>

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

<span data-ttu-id="1707b-283">De opdracht wordt gebruikt `Invoke-Command` om het script uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-283">The command uses `Invoke-Command` to run the script.</span></span> <span data-ttu-id="1707b-284">De waarde van de para meter **ComputerName** is een `Get-Content` opdracht waarmee de namen van de externe computers uit een tekst bestand worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1707b-284">The value of the **ComputerName** parameter is a `Get-Content` command that gets the names of the remote computers from a text file.</span></span> <span data-ttu-id="1707b-285">De **InDisconnectedSession** para meter verbreekt de verbinding van de sessies zodra de opdracht wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="1707b-285">The **InDisconnectedSession** parameter disconnects the sessions as soon as it starts the command.</span></span> <span data-ttu-id="1707b-286">De waarde van de **filepath** para meter is het script dat `Invoke-Command` op elke computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-286">The value of the **FilePath** parameter is the script that `Invoke-Command` runs on each computer.</span></span>

<span data-ttu-id="1707b-287">De waarde van **SessionOption** is een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="1707b-287">The value of **SessionOption** is a hash table.</span></span> <span data-ttu-id="1707b-288">De **OutputBufferingMode** -waarde is ingesteld op **Drop** en de waarde **IdleTimeout** is ingesteld op **43200000** milliseconden (12 uur).</span><span class="sxs-lookup"><span data-stu-id="1707b-288">The **OutputBufferingMode** value is set to **Drop** and the **IdleTimeout** value is set to **43200000** milliseconds (12 hours).</span></span>

<span data-ttu-id="1707b-289">Gebruik de cmdlet om de resultaten op te halen van opdrachten en scripts die worden uitgevoerd in verbroken sessies `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1707b-289">To get the results of commands and scripts that run in disconnected sessions, use the `Receive-PSSession` cmdlet.</span></span>

## <span data-ttu-id="1707b-290">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1707b-290">PARAMETERS</span></span>

### <span data-ttu-id="1707b-291">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="1707b-291">-AllowRedirection</span></span>

<span data-ttu-id="1707b-292">Hiermee kan de verbinding worden omgeleid naar een alternatieve URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="1707b-292">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="1707b-293">Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="1707b-293">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="1707b-294">Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding door te sturen.</span><span class="sxs-lookup"><span data-stu-id="1707b-294">By default, PowerShell doesn't redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="1707b-295">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="1707b-295">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="1707b-296">Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de `$PSSessionOption` Voorkeurs variabele in.</span><span class="sxs-lookup"><span data-stu-id="1707b-296">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="1707b-297">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="1707b-297">The default value is 5.</span></span>

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

### <span data-ttu-id="1707b-298">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="1707b-298">-ApplicationName</span></span>

<span data-ttu-id="1707b-299">Hiermee geeft u het segment van de toepassings naam van de verbindings-URI op.</span><span class="sxs-lookup"><span data-stu-id="1707b-299">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="1707b-300">Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de para meter **ConnectionURI** niet in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1707b-300">Use this parameter to specify the application name when you aren't using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="1707b-301">De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-301">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="1707b-302">Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN.</span><span class="sxs-lookup"><span data-stu-id="1707b-302">If this preference variable isn't defined, the default value is WSMAN.</span></span> <span data-ttu-id="1707b-303">Deze waarde is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="1707b-303">This value is appropriate for most uses.</span></span> <span data-ttu-id="1707b-304">Zie [about_Preference_Variables](./About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1707b-304">For more information, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="1707b-305">De WinRM-service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="1707b-305">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="1707b-306">De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-306">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-307">-Argument List</span><span class="sxs-lookup"><span data-stu-id="1707b-307">-ArgumentList</span></span>

<span data-ttu-id="1707b-308">Levert de waarden van lokale variabelen in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-308">Supplies the values of local variables in the command.</span></span> <span data-ttu-id="1707b-309">De variabelen in de opdracht worden vervangen door deze waarden voordat de opdracht wordt uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-309">The variables in the command are replaced by these values before the command is run on the remote computer.</span></span> <span data-ttu-id="1707b-310">Voer de waarden in een door komma's gescheiden lijst in.</span><span class="sxs-lookup"><span data-stu-id="1707b-310">Enter the values in a comma-separated list.</span></span> <span data-ttu-id="1707b-311">Waarden worden aan variabelen gekoppeld in de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1707b-311">Values are associated with variables in the order that they're listed.</span></span> <span data-ttu-id="1707b-312">De alias voor **argument List** is args.</span><span class="sxs-lookup"><span data-stu-id="1707b-312">The alias for **ArgumentList** is Args.</span></span>

<span data-ttu-id="1707b-313">De waarden in de para meter **argument List** kunnen werkelijke waarden zijn, zoals 1024, of ze kunnen verwijzingen zijn naar lokale variabelen, zoals `$max` .</span><span class="sxs-lookup"><span data-stu-id="1707b-313">The values in the **ArgumentList** parameter can be actual values, such as 1024, or they can be references to local variables, such as `$max`.</span></span>

<span data-ttu-id="1707b-314">Als u lokale variabelen wilt gebruiken in een opdracht, gebruikt u de volgende opdracht indeling:</span><span class="sxs-lookup"><span data-stu-id="1707b-314">To use local variables in a command, use the following command format:</span></span>

<span data-ttu-id="1707b-315">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` of `<local-variable>`</span><span class="sxs-lookup"><span data-stu-id="1707b-315">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` -or- `<local-variable>`</span></span>

<span data-ttu-id="1707b-316">Het sleutel woord **param** bevat de lokale variabelen die worden gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-316">The **param** keyword lists the local variables that are used in the command.</span></span> <span data-ttu-id="1707b-317">**Argument List** levert de waarden van de variabelen in de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1707b-317">**ArgumentList** supplies the values of the variables, in the order that they're listed.</span></span> <span data-ttu-id="1707b-318">Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="1707b-318">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="1707b-319">-AsJob</span><span class="sxs-lookup"><span data-stu-id="1707b-319">-AsJob</span></span>

<span data-ttu-id="1707b-320">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-320">Indicates that this cmdlet runs the command as a background job on a remote computer.</span></span> <span data-ttu-id="1707b-321">Gebruik deze para meter om opdrachten uit te voeren die veel tijd in beslag nemen.</span><span class="sxs-lookup"><span data-stu-id="1707b-321">Use this parameter to run commands that take an extensive time to finish.</span></span>

<span data-ttu-id="1707b-322">Wanneer u de para meter **AsJob** gebruikt, retourneert de opdracht een object dat de taak vertegenwoordigt, waarna de opdracht prompt wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1707b-322">When you use the **AsJob** parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span> <span data-ttu-id="1707b-323">U kunt in de sessie blijven werken terwijl de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="1707b-323">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="1707b-324">Als u de taak wilt beheren, gebruikt u de- `*-Job` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="1707b-324">To manage the job, use the `*-Job` cmdlets.</span></span> <span data-ttu-id="1707b-325">Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="1707b-325">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="1707b-326">De para meter **AsJob** lijkt op het gebruik van de `Invoke-Command` cmdlet om een `Start-Job` cmdlet op afstand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-326">The **AsJob** parameter resembles using the `Invoke-Command` cmdlet to run a `Start-Job` cmdlet remotely.</span></span> <span data-ttu-id="1707b-327">Met **AsJob** wordt de taak echter gemaakt op de lokale computer, zelfs als de taak wordt uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-327">However, with **AsJob** , the job is created on the local computer, even though the job runs on a remote computer.</span></span> <span data-ttu-id="1707b-328">De resultaten van de externe taak worden automatisch geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-328">The results of the remote job are automatically returned to the local computer.</span></span>

<span data-ttu-id="1707b-329">Zie [about_Jobs](About/about_Jobs.md) en [about_Remote_Jobs](About/about_Remote_Jobs.md)voor meer informatie over Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="1707b-329">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-330">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="1707b-330">-Authentication</span></span>

<span data-ttu-id="1707b-331">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="1707b-331">Specifies the mechanism that's used to authenticate the user's credentials.</span></span> <span data-ttu-id="1707b-332">CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="1707b-332">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="1707b-333">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="1707b-333">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1707b-334">Standaard</span><span class="sxs-lookup"><span data-stu-id="1707b-334">Default</span></span>
- <span data-ttu-id="1707b-335">Basic</span><span class="sxs-lookup"><span data-stu-id="1707b-335">Basic</span></span>
- <span data-ttu-id="1707b-336">CredSSP</span><span class="sxs-lookup"><span data-stu-id="1707b-336">Credssp</span></span>
- <span data-ttu-id="1707b-337">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="1707b-337">Digest</span></span>
- <span data-ttu-id="1707b-338">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1707b-338">Kerberos</span></span>
- <span data-ttu-id="1707b-339">Negotiate</span><span class="sxs-lookup"><span data-stu-id="1707b-339">Negotiate</span></span>
- <span data-ttu-id="1707b-340">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="1707b-340">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="1707b-341">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="1707b-341">The default value is Default.</span></span>

<span data-ttu-id="1707b-342">Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="1707b-342">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="1707b-343">De verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="1707b-343">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="1707b-344">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="1707b-344">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="1707b-345">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="1707b-345">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span> <span data-ttu-id="1707b-346">Zie [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1707b-346">For more information, see [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-347">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="1707b-347">-CertificateThumbprint</span></span>

<span data-ttu-id="1707b-348">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="1707b-348">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="1707b-349">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="1707b-349">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="1707b-350">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="1707b-350">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="1707b-351">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts en ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="1707b-351">They can be mapped only to local user accounts and they don't work with domain accounts.</span></span>

<span data-ttu-id="1707b-352">Als u een certificaat vingerafdruk wilt ophalen, gebruikt u een `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="1707b-352">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="1707b-353">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="1707b-353">-ComputerName</span></span>

<span data-ttu-id="1707b-354">Hiermee geeft u de computers waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-354">Specifies the computers on which the command runs.</span></span> <span data-ttu-id="1707b-355">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-355">The default is the local computer.</span></span>

<span data-ttu-id="1707b-356">Wanneer u de para meter **ComputerName** gebruikt, maakt Power shell een tijdelijke verbinding die alleen wordt gebruikt om de opgegeven opdracht uit te voeren en vervolgens gesloten.</span><span class="sxs-lookup"><span data-stu-id="1707b-356">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that's used only to run the specified command and is then closed.</span></span> <span data-ttu-id="1707b-357">Als u een permanente verbinding nodig hebt, gebruikt u de para meter **Session** .</span><span class="sxs-lookup"><span data-stu-id="1707b-357">If you need a persistent connection, use the **Session** parameter.</span></span>

<span data-ttu-id="1707b-358">Typ de NETBIOS-naam, het IP-adres of de Fully Qualified Domain Name van een of meer computers in een lijst met door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="1707b-358">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="1707b-359">Typ de computer naam, localhost of een punt () om de lokale computer op te geven `.` .</span><span class="sxs-lookup"><span data-stu-id="1707b-359">To specify the local computer, type the computer name, localhost, or a dot (`.`).</span></span>

<span data-ttu-id="1707b-360">Als u een IP-adres in de waarde **computer naam** wilt gebruiken, moet de opdracht de para meter **Credential** bevatten.</span><span class="sxs-lookup"><span data-stu-id="1707b-360">To use an IP address in the value of **ComputerName** , the command must include the **Credential** parameter.</span></span> <span data-ttu-id="1707b-361">De computer moet zijn geconfigureerd voor het HTTPS-Trans Port of het IP-adres van de externe computer moet zijn opgenomen in de lijst met WinRM **TrustedHosts** van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-361">The computer must be configured for the HTTPS transport or the IP address of the remote computer must be included in the local computer's WinRM **TrustedHosts** list.</span></span> <span data-ttu-id="1707b-362">Zie [een computer toevoegen aan de lijst met vertrouwde hosts](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list)voor instructies om een computer naam toe te voegen aan de lijst met **TrustedHosts** .</span><span class="sxs-lookup"><span data-stu-id="1707b-362">For instructions to add a computer name to the **TrustedHosts** list, see [How to Add a Computer to the Trusted Host List](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list).</span></span>

<span data-ttu-id="1707b-363">In Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell uitvoeren met de optie **als administrator uitvoeren** om de lokale computer op te vragen met de waarde **computer naam**.</span><span class="sxs-lookup"><span data-stu-id="1707b-363">On Windows Vista and later versions of the Windows operating system, to include the local computer in the value of **ComputerName** , you must run PowerShell using the **Run as administrator** option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FilePathComputerName, ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-364">-Configuratiepad</span><span class="sxs-lookup"><span data-stu-id="1707b-364">-ConfigurationName</span></span>

<span data-ttu-id="1707b-365">Hiermee geeft u de sessie configuratie op die wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="1707b-365">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="1707b-366">Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="1707b-366">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="1707b-367">Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="1707b-367">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="1707b-368">De sessie configuratie voor een sessie bevindt zich op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-368">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="1707b-369">Als de opgegeven sessie configuratie niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-369">If the specified session configuration doesn't exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="1707b-370">De standaard waarde is de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-370">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="1707b-371">Als deze voorkeurs variabele niet is ingesteld, is de standaard instelling **micro soft. Power shell**.</span><span class="sxs-lookup"><span data-stu-id="1707b-371">If this preference variable isn't set, the default is **Microsoft.PowerShell**.</span></span> <span data-ttu-id="1707b-372">Zie [about_Preference_Variables](about/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1707b-372">For more information, see [about_Preference_Variables](about/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-373">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="1707b-373">-ConnectionUri</span></span>

<span data-ttu-id="1707b-374">Hiermee geeft u een URI (Uniform Resource Identifier) op die het verbindings eindpunt van de sessie definieert.</span><span class="sxs-lookup"><span data-stu-id="1707b-374">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint of the session.</span></span>
<span data-ttu-id="1707b-375">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="1707b-375">The URI must be fully qualified.</span></span>

<span data-ttu-id="1707b-376">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="1707b-376">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="1707b-377">De standaard waarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="1707b-377">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="1707b-378">Als u geen verbindings-URI opgeeft, kunt u de para meters **UseSSL** en **Port** gebruiken om de verbindings-URI-waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="1707b-378">If you don't specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="1707b-379">Geldige waarden voor het **transport** segment van de URI zijn http en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1707b-379">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="1707b-380">Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met de standaard poorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1707b-380">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with the standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="1707b-381">Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1707b-381">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="1707b-382">Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1707b-382">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="1707b-383">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="1707b-383">-ContainerId</span></span>

<span data-ttu-id="1707b-384">Hiermee geeft u een matrix met container-Id's op.</span><span class="sxs-lookup"><span data-stu-id="1707b-384">Specifies an array of container IDs.</span></span>

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

### <span data-ttu-id="1707b-385">-Credential</span><span class="sxs-lookup"><span data-stu-id="1707b-385">-Credential</span></span>

<span data-ttu-id="1707b-386">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-386">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="1707b-387">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="1707b-387">The default is the current user.</span></span>

<span data-ttu-id="1707b-388">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="1707b-388">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1707b-389">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-389">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="1707b-390">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="1707b-390">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="1707b-391">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="1707b-391">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="1707b-392">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="1707b-392">-EnableNetworkAccess</span></span>

<span data-ttu-id="1707b-393">Geeft aan dat met deze cmdlet een interactief beveiligings token wordt toegevoegd aan loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="1707b-393">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="1707b-394">Met het interactieve token kunt u opdrachten uitvoeren in de loop back-sessie die gegevens van andere computers ophalen.</span><span class="sxs-lookup"><span data-stu-id="1707b-394">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="1707b-395">U kunt bijvoorbeeld een opdracht uitvoeren in de sessie waarmee XML-bestanden van een externe computer naar de lokale computer worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-395">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="1707b-396">Een loop back-sessie is een **PSSession** die afkomstig is van en eindigt op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-396">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="1707b-397">Als u een loop back-sessie wilt maken, laat u de para meter **ComputerName** weg of stelt u de waarde in op punt ( `.` ), localhost of de naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-397">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (`.`), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="1707b-398">Loop Back-sessies worden standaard gemaakt met behulp van een netwerk token, wat mogelijk niet voldoende machtigingen biedt om te verifiëren bij externe computers.</span><span class="sxs-lookup"><span data-stu-id="1707b-398">By default, loopback sessions are created using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="1707b-399">De para meter **EnableNetworkAccess** is alleen effectief in loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="1707b-399">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="1707b-400">Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, mislukt de opdracht, maar wordt de para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-400">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="1707b-401">U kunt externe toegang toestaan in een loop back-sessie met behulp van de **CredSSP** -waarde van de **verificatie** parameter, waarmee de sessie referenties worden gedelegeerd aan andere computers.</span><span class="sxs-lookup"><span data-stu-id="1707b-401">You can allow remote access in a loopback session using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="1707b-402">Om de computer te beschermen tegen kwaadwillende toegang, kunnen niet-verbonden loop Back-sessies met interactieve tokens, die zijn gemaakt met behulp van **EnableNetworkAccess** , alleen opnieuw verbinding maken vanaf de computer waarop de sessie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="1707b-402">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created using **EnableNetworkAccess** , can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="1707b-403">Verbroken sessies die gebruikmaken van CredSSP-verificatie, kunnen opnieuw worden aangesloten op andere computers.</span><span class="sxs-lookup"><span data-stu-id="1707b-403">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="1707b-404">Voor meer informatie raadpleegt u `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="1707b-404">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="1707b-405">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1707b-405">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-406">-FilePath</span><span class="sxs-lookup"><span data-stu-id="1707b-406">-FilePath</span></span>

<span data-ttu-id="1707b-407">Hiermee geeft u een lokaal script op dat met deze cmdlet wordt uitgevoerd op een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="1707b-407">Specifies a local script that this cmdlet runs on one or more remote computers.</span></span> <span data-ttu-id="1707b-408">Voer het pad en de bestands naam van het script in of pipet een scriptpad naar `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="1707b-408">Enter the path and filename of the script, or pipe a script path to `Invoke-Command`.</span></span> <span data-ttu-id="1707b-409">Het script moet bestaan op de lokale computer of in een map waartoe de lokale computer toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="1707b-409">The script must exist on the local computer or in a directory that the local computer can access.</span></span> <span data-ttu-id="1707b-410">Gebruik **argument List** om de waarden van para meters in het script op te geven.</span><span class="sxs-lookup"><span data-stu-id="1707b-410">Use **ArgumentList** to specify the values of parameters in the script.</span></span>

<span data-ttu-id="1707b-411">Wanneer u deze para meter gebruikt, wordt de inhoud van het opgegeven script bestand door Power shell naar een script blok geconverteerd, wordt het script blok verzonden naar de externe computer en uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-411">When you use this parameter, PowerShell converts the contents of the specified script file to a script block, transmits the script block to the remote computer, and runs it on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-412">-HideComputerName</span><span class="sxs-lookup"><span data-stu-id="1707b-412">-HideComputerName</span></span>

<span data-ttu-id="1707b-413">Geeft aan dat met deze cmdlet de computer naam van elk object uit de uitvoer weergave wordt wegge laten.</span><span class="sxs-lookup"><span data-stu-id="1707b-413">Indicates that this cmdlet omits the computer name of each object from the output display.</span></span> <span data-ttu-id="1707b-414">De naam van de computer die het object heeft gegenereerd, wordt standaard weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="1707b-414">By default, the name of the computer that generated the object appears in the display.</span></span>

<span data-ttu-id="1707b-415">Deze para meter is alleen van invloed op de uitvoer weergave.</span><span class="sxs-lookup"><span data-stu-id="1707b-415">This parameter affects only the output display.</span></span> <span data-ttu-id="1707b-416">Het object wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="1707b-416">It doesn't change the object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases: HCN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-417">-InDisconnectedSession</span><span class="sxs-lookup"><span data-stu-id="1707b-417">-InDisconnectedSession</span></span>

<span data-ttu-id="1707b-418">Geeft aan dat met deze cmdlet een opdracht of script wordt uitgevoerd in een sessie waarbij de verbinding is verbroken.</span><span class="sxs-lookup"><span data-stu-id="1707b-418">Indicates that this cmdlet runs a command or script in a disconnected session.</span></span>

<span data-ttu-id="1707b-419">Wanneer u de para meter **InDisconnectedSession** gebruikt, `Invoke-Command` wordt op elke externe computer een permanente sessie gemaakt, wordt de opdracht gestart die is opgegeven door de para meter **script Block** of **filepath** en wordt de verbinding met de sessie verbroken.</span><span class="sxs-lookup"><span data-stu-id="1707b-419">When you use the **InDisconnectedSession** parameter, `Invoke-Command` creates a persistent session on each remote computer, starts the command specified by the **ScriptBlock** or **FilePath** parameter, and then disconnects from the session.</span></span> <span data-ttu-id="1707b-420">De opdrachten blijven worden uitgevoerd in de verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="1707b-420">The commands continue to run in the disconnected sessions.</span></span> <span data-ttu-id="1707b-421">Met **InDisconnectedSession** kunt u opdrachten uitvoeren zonder een verbinding met de externe sessies te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="1707b-421">**InDisconnectedSession** enables you to run commands without maintaining a connection to the remote sessions.</span></span> <span data-ttu-id="1707b-422">En omdat de verbinding van de sessie wordt verbroken voordat er resultaten worden geretourneerd, zorgt **InDisconnectedSession** ervoor dat alle opdracht resultaten worden geretourneerd naar de opnieuw verbonden sessie, in plaats van te worden gesplitst tussen sessies.</span><span class="sxs-lookup"><span data-stu-id="1707b-422">And, because the session is disconnected before any results are returned, **InDisconnectedSession** makes sure that all command results are returned to the reconnected session, instead of being split between sessions.</span></span>

<span data-ttu-id="1707b-423">U kunt **InDisconnectedSession** niet gebruiken met de para meter **Session** of de para meter **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="1707b-423">You can't use **InDisconnectedSession** with the **Session** parameter or the **AsJob** parameter.</span></span>

<span data-ttu-id="1707b-424">Opdrachten die gebruikmaken van **InDisconnectedSession** retour neren een **PSSession** -object dat de niet-verbonden sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1707b-424">Commands that use **InDisconnectedSession** return a **PSSession** object that represents the disconnected session.</span></span> <span data-ttu-id="1707b-425">Ze retour neren niet de uitvoer van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-425">They don't return the command output.</span></span> <span data-ttu-id="1707b-426">Gebruik de cmdlets of om verbinding te maken met de verbroken sessie `Connect-PSSession` `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1707b-426">To connect to the disconnected session, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span> <span data-ttu-id="1707b-427">Gebruik de cmdlet om de resultaten op te halen van de opdrachten die in de sessie worden uitgevoerd `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1707b-427">To get the results of commands that ran in the session, use the `Receive-PSSession` cmdlet.</span></span> <span data-ttu-id="1707b-428">Om opdrachten uit te voeren die uitvoer genereren in een verbroken sessie, stelt u de waarde van de **OutputBufferingMode** -sessie optie in op **Drop**.</span><span class="sxs-lookup"><span data-stu-id="1707b-428">To run commands that generate output in a disconnected session, set the value of the **OutputBufferingMode** session option to **Drop**.</span></span> <span data-ttu-id="1707b-429">Als u van plan bent om verbinding te maken met de verbroken sessie, stelt u de time-out voor inactiviteit in de sessie zo in dat u voldoende tijd hebt om verbinding te maken voordat u de sessie verwijdert.</span><span class="sxs-lookup"><span data-stu-id="1707b-429">If you intend to connect to the disconnected session, set the idle time-out in the session so that it provides sufficient time for you to connect before deleting the session.</span></span>

<span data-ttu-id="1707b-430">U kunt de uitvoer buffer modus en time-out voor inactiviteit instellen in de para meter **SessionOption** of in de `$PSSessionOption` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-430">You can set the output buffering mode and idle time-out in the **SessionOption** parameter or in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="1707b-431">Zie en about_Preference_Variables voor meer informatie over sessie `New-PSSessionOption` opties [about_Preference_Variables](./about/about_preference_variables.md).</span><span class="sxs-lookup"><span data-stu-id="1707b-431">For more information about session options, see `New-PSSessionOption` and [about_Preference_Variables](./about/about_preference_variables.md).</span></span>

<span data-ttu-id="1707b-432">Zie [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)voor meer informatie over de functie voor verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="1707b-432">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="1707b-433">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1707b-433">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-434">-Input object</span><span class="sxs-lookup"><span data-stu-id="1707b-434">-InputObject</span></span>

<span data-ttu-id="1707b-435">Hiermee geeft u de invoer aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-435">Specifies input to the command.</span></span> <span data-ttu-id="1707b-436">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1707b-436">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="1707b-437">Gebruik bij het gebruik van de para meter **input object** de `$Input` Automatische variabele in de waarde van de para meter **script Block** om de invoer objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1707b-437">When using the **InputObject** parameter, use the `$Input` automatic variable in the value of the **ScriptBlock** parameter to represent the input objects.</span></span>

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

### <span data-ttu-id="1707b-438">-JobName</span><span class="sxs-lookup"><span data-stu-id="1707b-438">-JobName</span></span>

<span data-ttu-id="1707b-439">Hiermee geeft u een beschrijvende naam op voor de achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="1707b-439">Specifies a friendly name for the background job.</span></span> <span data-ttu-id="1707b-440">Taken worden standaard benoemd `Job<n>` , waarbij `<n>` een rang nummer is.</span><span class="sxs-lookup"><span data-stu-id="1707b-440">By default, jobs are named `Job<n>`, where `<n>` is an ordinal number.</span></span>

<span data-ttu-id="1707b-441">Als u de para meter **JobName** in een opdracht gebruikt, wordt de opdracht uitgevoerd als een taak en `Invoke-Command` wordt een taak object geretourneerd, zelfs als u geen **AsJob** in de opdracht opneemt.</span><span class="sxs-lookup"><span data-stu-id="1707b-441">If you use the **JobName** parameter in a command, the command is run as a job, and `Invoke-Command` returns a job object, even if you don't include **AsJob** in the command.</span></span>

<span data-ttu-id="1707b-442">Zie [about_Jobs](./About/about_Jobs.md)voor meer informatie over Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="1707b-442">For more information about PowerShell background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

```yaml
Type: System.String
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-443">-NoNewScope</span><span class="sxs-lookup"><span data-stu-id="1707b-443">-NoNewScope</span></span>

<span data-ttu-id="1707b-444">Geeft aan dat met deze cmdlet de opgegeven opdracht wordt uitgevoerd in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="1707b-444">Indicates that this cmdlet runs the specified command in the current scope.</span></span> <span data-ttu-id="1707b-445">`Invoke-Command`Voert standaard opdrachten uit in hun eigen bereik.</span><span class="sxs-lookup"><span data-stu-id="1707b-445">By default, `Invoke-Command` runs commands in their own scope.</span></span>

<span data-ttu-id="1707b-446">Deze para meter is alleen geldig in opdrachten die worden uitgevoerd in de huidige sessie, dat wil zeggen opdrachten die de **computer naam** en de **sessie** parameters weglaten.</span><span class="sxs-lookup"><span data-stu-id="1707b-446">This parameter is valid only in commands that are run in the current session, that is, commands that omit both the **ComputerName** and **Session** parameters.</span></span>

<span data-ttu-id="1707b-447">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1707b-447">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1707b-448">-Port</span><span class="sxs-lookup"><span data-stu-id="1707b-448">-Port</span></span>

<span data-ttu-id="1707b-449">Hiermee geeft u de netwerk poort op de externe computer die wordt gebruikt voor deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-449">Specifies the network port on the remote computer that is used for this command.</span></span> <span data-ttu-id="1707b-450">Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1707b-450">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="1707b-451">De standaard poorten zijn 5985 (WinRM-poort voor HTTP) en 5986 (WinRM-poort voor HTTPS).</span><span class="sxs-lookup"><span data-stu-id="1707b-451">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="1707b-452">Voordat u een andere poort gebruikt, configureert u de WinRM-listener op de externe computer om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="1707b-452">Before using an alternate port, configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="1707b-453">Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de Power shell-prompt:</span><span class="sxs-lookup"><span data-stu-id="1707b-453">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="1707b-454">Gebruik de para meter **poort** alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="1707b-454">Don't use the **Port** parameter unless you must.</span></span> <span data-ttu-id="1707b-455">De poort die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-455">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="1707b-456">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="1707b-456">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-457">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="1707b-457">-RunAsAdministrator</span></span>

<span data-ttu-id="1707b-458">Geeft aan dat deze cmdlet een opdracht aanroept als beheerder.</span><span class="sxs-lookup"><span data-stu-id="1707b-458">Indicates that this cmdlet invokes a command as an Administrator.</span></span>

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

### <span data-ttu-id="1707b-459">-Script Block</span><span class="sxs-lookup"><span data-stu-id="1707b-459">-ScriptBlock</span></span>

<span data-ttu-id="1707b-460">Hiermee geeft u de opdrachten op die moeten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-460">Specifies the commands to run.</span></span> <span data-ttu-id="1707b-461">Plaats de opdrachten tussen accolades `{ }` om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="1707b-461">Enclose the commands in curly braces `{ }` to create a script block.</span></span>
<span data-ttu-id="1707b-462">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="1707b-462">This parameter is required.</span></span>

<span data-ttu-id="1707b-463">Standaard worden alle variabelen in de opdracht geëvalueerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-463">By default, any variables in the command are evaluated on the remote computer.</span></span> <span data-ttu-id="1707b-464">Als u lokale variabelen wilt toevoegen aan de opdracht, gebruikt u **argument List**.</span><span class="sxs-lookup"><span data-stu-id="1707b-464">To include local variables in the command, use **ArgumentList**.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, ContainerId
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-465">-Sessie</span><span class="sxs-lookup"><span data-stu-id="1707b-465">-Session</span></span>

<span data-ttu-id="1707b-466">Hiermee geeft u een matrix met sessies waarin met deze cmdlet de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-466">Specifies an array of sessions in which this cmdlet runs the command.</span></span> <span data-ttu-id="1707b-467">Voer een variabele in die **PSSession** -objecten bevat of een opdracht waarmee de **PSSession** -objecten, zoals een of-opdracht, worden gemaakt of opgehaald `New-PSSession` `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1707b-467">Enter a variable that contains **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="1707b-468">Wanneer u een **PSSession** maakt, brengt Power shell een permanente verbinding met de externe computer tot stand.</span><span class="sxs-lookup"><span data-stu-id="1707b-468">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="1707b-469">Gebruik een **PSSession** om een reeks gerelateerde opdrachten uit te voeren die gegevens delen.</span><span class="sxs-lookup"><span data-stu-id="1707b-469">Use a **PSSession** to run a series of related commands that share data.</span></span> <span data-ttu-id="1707b-470">Als u één opdracht of een reeks niet-gerelateerde opdrachten wilt uitvoeren, gebruikt u de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="1707b-470">To run a single command or a series of unrelated commands, use the **ComputerName** parameter.</span></span> <span data-ttu-id="1707b-471">Zie [about_PSSessions](./About/about_PSSessions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1707b-471">For more information, see [about_PSSessions](./About/about_PSSessions.md).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session, FilePathRunspace
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-472">-Sessie naam</span><span class="sxs-lookup"><span data-stu-id="1707b-472">-SessionName</span></span>

<span data-ttu-id="1707b-473">Hiermee geeft u een beschrijvende naam op voor een niet-verbonden sessie.</span><span class="sxs-lookup"><span data-stu-id="1707b-473">Specifies a friendly name for a disconnected session.</span></span> <span data-ttu-id="1707b-474">U kunt de naam gebruiken om te verwijzen naar de sessie in volgende opdrachten, zoals een `Get-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-474">You can use the name to refer to the session in subsequent commands, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="1707b-475">Deze para meter is alleen geldig voor de para meter **InDisconnectedSession** .</span><span class="sxs-lookup"><span data-stu-id="1707b-475">This parameter is valid only with the **InDisconnectedSession** parameter.</span></span>

<span data-ttu-id="1707b-476">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1707b-476">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-477">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="1707b-477">-SessionOption</span></span>

<span data-ttu-id="1707b-478">Hiermee geeft u geavanceerde opties voor de sessie op.</span><span class="sxs-lookup"><span data-stu-id="1707b-478">Specifies advanced options for the session.</span></span> <span data-ttu-id="1707b-479">Voer een **SessionOption** -object in, zoals het account dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de namen van sessie opties zijn en de waarden zijn waarden voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="1707b-479">Enter a **SessionOption** object, such as one that you create using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="1707b-480">De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="1707b-480">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="1707b-481">Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="1707b-481">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="1707b-482">De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="1707b-482">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="1707b-483">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="1707b-483">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="1707b-484">Zie voor een beschrijving van de sessie opties die de standaard waarden bevatten `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="1707b-484">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="1707b-485">Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](About/about_Preference_Variables.md)variabele.</span><span class="sxs-lookup"><span data-stu-id="1707b-485">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="1707b-486">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="1707b-486">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-487">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="1707b-487">-ThrottleLimit</span></span>

<span data-ttu-id="1707b-488">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1707b-488">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="1707b-489">Als u deze para meter weglaat of een waarde van 0 invoert, wordt de standaard waarde 32 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1707b-489">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="1707b-490">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-490">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-491">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="1707b-491">-UseSSL</span></span>

<span data-ttu-id="1707b-492">Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-492">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="1707b-493">SSL wordt standaard niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1707b-493">By default, SSL isn't used.</span></span>

<span data-ttu-id="1707b-494">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="1707b-494">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="1707b-495">De para meter **UseSSL** is een extra beveiliging waarbij de gegevens worden verzonden via een HTTPS, in plaats van via http.</span><span class="sxs-lookup"><span data-stu-id="1707b-495">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span>

<span data-ttu-id="1707b-496">Als u deze para meter gebruikt, maar SSL niet beschikbaar is op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-496">If you use this parameter, but SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1707b-497">-VMId</span><span class="sxs-lookup"><span data-stu-id="1707b-497">-VMId</span></span>

<span data-ttu-id="1707b-498">Hiermee geeft u een matrix met Id's van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="1707b-498">Specifies an array of IDs of virtual machines.</span></span>

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

### <span data-ttu-id="1707b-499">-VMName</span><span class="sxs-lookup"><span data-stu-id="1707b-499">-VMName</span></span>

<span data-ttu-id="1707b-500">Hiermee geeft u een matrix met namen van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="1707b-500">Specifies an array of names of virtual machines.</span></span>

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

### <span data-ttu-id="1707b-501">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1707b-501">CommonParameters</span></span>

<span data-ttu-id="1707b-502">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1707b-502">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1707b-503">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1707b-503">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1707b-504">INVOER</span><span class="sxs-lookup"><span data-stu-id="1707b-504">INPUTS</span></span>

### <span data-ttu-id="1707b-505">System. Management. Automation. script Block</span><span class="sxs-lookup"><span data-stu-id="1707b-505">System.Management.Automation.ScriptBlock</span></span>

<span data-ttu-id="1707b-506">U kunt een opdracht in een script blok door sluizen naar `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="1707b-506">You can pipe a command in a script block to `Invoke-Command`.</span></span> <span data-ttu-id="1707b-507">Gebruik de `$Input` Automatische variabele om de invoer objecten in de opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1707b-507">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="1707b-508">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1707b-508">OUTPUTS</span></span>

### <span data-ttu-id="1707b-509">System. Management. Automation. PSRemotingJob, System. Management. Automation. Runspaces. PSSession, of de uitvoer van de aangeroepen opdracht</span><span class="sxs-lookup"><span data-stu-id="1707b-509">System.Management.Automation.PSRemotingJob, System.Management.Automation.Runspaces.PSSession, or the output of the invoked command</span></span>

<span data-ttu-id="1707b-510">Met deze cmdlet wordt een taak object geretourneerd als u de para meter **AsJob** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1707b-510">This cmdlet returns a job object, if you use the **AsJob** parameter.</span></span> <span data-ttu-id="1707b-511">Als u de para meter **InDisconnectedSession** opgeeft, `Invoke-Command` wordt een **PSSession** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-511">If you specify the **InDisconnectedSession** parameter, `Invoke-Command` returns a **PSSession** object.</span></span> <span data-ttu-id="1707b-512">Anders wordt de uitvoer van de aangeroepen opdracht geretourneerd. Dit is de waarde van de para meter **script Block** .</span><span class="sxs-lookup"><span data-stu-id="1707b-512">Otherwise, it returns the output of the invoked command, which is the value of the **ScriptBlock** parameter.</span></span>

## <span data-ttu-id="1707b-513">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1707b-513">NOTES</span></span>

<span data-ttu-id="1707b-514">In Windows Vista en latere versies van het Windows-besturings systeem **ComputerName** `Invoke-Command` moet u Power shell uitvoeren met de optie **als administrator uitvoeren** om de para meter ComputerName van te gebruiken voor het uitvoeren van een opdracht op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-514">On Windows Vista, and later versions of the Windows operating system, to use the **ComputerName** parameter of `Invoke-Command` to run a command on the local computer, you must run PowerShell using the **Run as administrator** option.</span></span>

<span data-ttu-id="1707b-515">Wanneer u opdrachten op meerdere computers uitvoert, maakt Power shell verbinding met de computers in de volg orde waarin ze worden weer gegeven in de lijst.</span><span class="sxs-lookup"><span data-stu-id="1707b-515">When you run commands on multiple computers, PowerShell connects to the computers in the order in which they appear in the list.</span></span> <span data-ttu-id="1707b-516">De uitvoer van de opdracht wordt echter weer gegeven in de volg orde waarin deze worden ontvangen van de externe computers. Dit kan anders zijn.</span><span class="sxs-lookup"><span data-stu-id="1707b-516">However, the command output is displayed in the order that it's received from the remote computers, which might be different.</span></span>

<span data-ttu-id="1707b-517">Fouten die het resultaat zijn van de opdracht die `Invoke-Command` wordt uitgevoerd, worden opgenomen in de opdracht resultaten.</span><span class="sxs-lookup"><span data-stu-id="1707b-517">Errors that result from the command that `Invoke-Command` runs are included in the command results.</span></span>
<span data-ttu-id="1707b-518">Fouten waarvoor fouten in een lokale opdracht zouden worden beëindigd, worden beschouwd als niet-afsluit fouten in een externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="1707b-518">Errors that would be terminating errors in a local command are treated as non-terminating errors in a remote command.</span></span> <span data-ttu-id="1707b-519">Deze strategie zorgt ervoor dat het beëindigen van fouten op één computer de opdracht niet sluit op alle computers waarop deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1707b-519">This strategy makes sure that terminating errors on one computer don't close the command on all computers on which it's run.</span></span> <span data-ttu-id="1707b-520">Deze procedure wordt ook gebruikt wanneer een externe opdracht wordt uitgevoerd op één computer.</span><span class="sxs-lookup"><span data-stu-id="1707b-520">This practice is used even when a remote command is run on a single computer.</span></span>

<span data-ttu-id="1707b-521">Als de externe computer zich niet in een domein bevindt dat de lokale computer vertrouwt, is de computer mogelijk niet in staat om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="1707b-521">If the remote computer isn't in a domain that the local computer trusts, the computer might not be able to authenticate the user's credentials.</span></span> <span data-ttu-id="1707b-522">Als u de externe computer wilt toevoegen aan de lijst met vertrouwde hosts in WS-Management, gebruikt u de volgende opdracht in de `WSMAN` provider, waarbij `<Remote-Computer-Name>` de naam is van de externe computer:</span><span class="sxs-lookup"><span data-stu-id="1707b-522">To add the remote computer to the list of trusted hosts in WS-Management, use the following command in the `WSMAN` provider, where `<Remote-Computer-Name>` is the name of the remote computer:</span></span>

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

<span data-ttu-id="1707b-523">Wanneer u een **PSSession** verbreekt met de para meter **InDisconnectedSession** , wordt de sessie status **losgekoppeld** en is de beschik baarheid **geen**.</span><span class="sxs-lookup"><span data-stu-id="1707b-523">When you disconnect a **PSSession** using the **InDisconnectedSession** parameter, the session state is **Disconnected** and the availability is **None**.</span></span> <span data-ttu-id="1707b-524">De waarde van de eigenschap **State** is relatief ten opzichte van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="1707b-524">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="1707b-525">Als de waarde voor de **verbinding is verbroken** , betekent dit dat de **PSSession** niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="1707b-525">A value of **Disconnected** means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="1707b-526">Dit betekent echter niet dat de **PSSession** van de verbinding met alle sessies is verbroken.</span><span class="sxs-lookup"><span data-stu-id="1707b-526">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="1707b-527">Deze is mogelijk verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="1707b-527">It might be connected to a different session.</span></span> <span data-ttu-id="1707b-528">Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de sessie of er opnieuw verbinding mee wilt maken.</span><span class="sxs-lookup"><span data-stu-id="1707b-528">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

<span data-ttu-id="1707b-529">Een **beschikbaarheids** waarde van **geen** geeft aan dat u verbinding kunt maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="1707b-529">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="1707b-530">De waarde **bezet** geeft aan dat u geen verbinding kunt maken met de **PSSession** , omdat deze is verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="1707b-530">A value of **Busy** indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span> <span data-ttu-id="1707b-531">Zie [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)voor meer informatie over de waarden van de eigenschap **State** van sessies.</span><span class="sxs-lookup"><span data-stu-id="1707b-531">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span> <span data-ttu-id="1707b-532">Zie [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de eigenschap **Beschik baarheid** van sessies.</span><span class="sxs-lookup"><span data-stu-id="1707b-532">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="1707b-533">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1707b-533">RELATED LINKS</span></span>

[<span data-ttu-id="1707b-534">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="1707b-534">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="1707b-535">about_Remote</span><span class="sxs-lookup"><span data-stu-id="1707b-535">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="1707b-536">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="1707b-536">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="1707b-537">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="1707b-537">about_Remote_Troubleshooting</span></span>](./About/about_remote_troubleshooting.md)

[<span data-ttu-id="1707b-538">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="1707b-538">about_Remote_Variables</span></span>](./About/about_Remote_Variables.md)

[<span data-ttu-id="1707b-539">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="1707b-539">about_Scopes</span></span>](./About/about_scopes.md)

[<span data-ttu-id="1707b-540">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="1707b-540">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="1707b-541">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="1707b-541">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="1707b-542">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="1707b-542">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="1707b-543">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="1707b-543">Invoke-Item</span></span>](../Microsoft.PowerShell.Management/Invoke-Item.md)

[<span data-ttu-id="1707b-544">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="1707b-544">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="1707b-545">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="1707b-545">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="1707b-546">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="1707b-546">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
