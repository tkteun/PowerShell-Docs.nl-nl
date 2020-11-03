---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: a1b87830e1a9f330b10fb3e283fa990ccff66d36
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/24/2020
ms.locfileid: "93251674"
---
# <span data-ttu-id="5a6c2-103">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="5a6c2-103">Enter-PSSession</span></span>

## <span data-ttu-id="5a6c2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5a6c2-104">SYNOPSIS</span></span>
<span data-ttu-id="5a6c2-105">Start een interactieve sessie met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-105">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="5a6c2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5a6c2-106">SYNTAX</span></span>

### <span data-ttu-id="5a6c2-107">Computer naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="5a6c2-107">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="5a6c2-108">SSHHost</span><span class="sxs-lookup"><span data-stu-id="5a6c2-108">SSHHost</span></span>

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [<CommonParameters>]
```

### <span data-ttu-id="5a6c2-109">Sessie</span><span class="sxs-lookup"><span data-stu-id="5a6c2-109">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="5a6c2-110">URI</span><span class="sxs-lookup"><span data-stu-id="5a6c2-110">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="5a6c2-111">InstanceId</span><span class="sxs-lookup"><span data-stu-id="5a6c2-111">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="5a6c2-112">Id</span><span class="sxs-lookup"><span data-stu-id="5a6c2-112">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="5a6c2-113">Naam</span><span class="sxs-lookup"><span data-stu-id="5a6c2-113">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="5a6c2-114">VMId</span><span class="sxs-lookup"><span data-stu-id="5a6c2-114">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="5a6c2-115">VMName</span><span class="sxs-lookup"><span data-stu-id="5a6c2-115">VMName</span></span>

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="5a6c2-116">ContainerId</span><span class="sxs-lookup"><span data-stu-id="5a6c2-116">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="5a6c2-117">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5a6c2-117">DESCRIPTION</span></span>

<span data-ttu-id="5a6c2-118">`Enter-PSSession`Met de cmdlet wordt een interactieve sessie met één externe computer gestart.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-118">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span>
<span data-ttu-id="5a6c2-119">Tijdens de sessie worden de opdrachten die u typt op de externe computer uitgevoerd, net alsof u rechtstreeks op de externe computer typt.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-119">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="5a6c2-120">U kunt slechts één interactieve sessie tegelijk hebben.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-120">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="5a6c2-121">Normaal gesp roken gebruikt u de para meter **ComputerName** om de naam van de externe computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-121">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="5a6c2-122">U kunt echter ook een sessie gebruiken die u maakt met behulp van de `New-PSSession` cmdlet voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-122">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="5a6c2-123">U kunt echter de-, `Disconnect-PSSession` `Connect-PSSession` -of-cmdlets niet gebruiken om de verbinding met `Receive-PSSession` een interactieve sessie te verbreken of opnieuw te verbinden.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-123">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="5a6c2-124">Vanaf Power shell 6,0 kunt u Secure Shell (SSH) gebruiken om een verbinding met een externe computer tot stand te brengen, als SSH beschikbaar is op de lokale computer en de externe computer is geconfigureerd met een Power shell-SSH-eind punt.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-124">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="5a6c2-125">Het voor deel van een op SSH gebaseerde Power shell-externe sessie is dat deze werkt op meerdere platformen (Windows, Linux, macOS).</span><span class="sxs-lookup"><span data-stu-id="5a6c2-125">The benefit an SSH based PowerShell remote session is that it works across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="5a6c2-126">Voor op SSH gebaseerde externe communicatie gebruikt u de para meter **hostname** om de externe computer en de relevante verbindings gegevens op te geven.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-126">For SSH based remoting you use the **HostName** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="5a6c2-127">Zie voor meer informatie over het instellen van externe toegang tot Power shell [via SSH Power shell](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="5a6c2-127">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="5a6c2-128">Als u de interactieve sessie wilt beëindigen en de verbinding wilt verbreken met de externe computer, gebruikt u de `Exit-PSSession` cmdlet of het type `exit` .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-128">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="5a6c2-129">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5a6c2-129">EXAMPLES</span></span>

### <span data-ttu-id="5a6c2-130">Voor beeld 1: een interactieve sessie starten</span><span class="sxs-lookup"><span data-stu-id="5a6c2-130">Example 1: Start an interactive session</span></span>

```
PS> Enter-PSSession
[localhost]: PS>
```

<span data-ttu-id="5a6c2-131">Met deze opdracht wordt een interactieve sessie gestart op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-131">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="5a6c2-132">De opdracht prompt wordt gewijzigd om aan te geven dat u nu opdrachten uitvoert in een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-132">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="5a6c2-133">De opdrachten die u invoert, worden uitgevoerd in de nieuwe sessie en de resultaten worden geretourneerd naar de standaard sessie als tekst.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-133">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="5a6c2-134">Voor beeld 2: werken met een interactieve sessie</span><span class="sxs-lookup"><span data-stu-id="5a6c2-134">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="5a6c2-135">Met de eerste opdracht wordt de `Enter-PSSession` cmdlet gebruikt voor het starten van een interactieve sessie met Server01, een externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-135">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="5a6c2-136">Wanneer de sessie wordt gestart, wordt de computer naam in de opdracht prompt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-136">When the session starts, the command prompt changes to include the computer name.</span></span>

<span data-ttu-id="5a6c2-137">Met de tweede opdracht wordt het Power Shell-proces opgehaald en wordt de uitvoer omgeleid naar het Process.txt-bestand.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-137">The second command gets the PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="5a6c2-138">De opdracht wordt verzonden naar de externe computer en het bestand wordt opgeslagen op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-138">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>

<span data-ttu-id="5a6c2-139">De derde opdracht maakt gebruik van het sleutel woord **Exit** om de interactieve sessie te beëindigen en sluit de verbinding.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-139">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="5a6c2-140">Met de vierde opdracht wordt bevestigd dat het Process.txt-bestand zich op de externe computer bevindt.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-140">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="5a6c2-141">Een `Get-ChildItem` ("dir") opdracht op de lokale computer kan het bestand niet vinden.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-141">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

<span data-ttu-id="5a6c2-142">Met deze opdracht wordt aangegeven hoe u kunt werken in een interactieve sessie met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-142">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="5a6c2-143">Voor beeld 3: de sessie parameter gebruiken</span><span class="sxs-lookup"><span data-stu-id="5a6c2-143">Example 3: Use the Session parameter</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

<span data-ttu-id="5a6c2-144">Met deze opdrachten wordt de **sessie** parameter van gebruikt `Enter-PSSession` voor het uitvoeren van de interactieve sessie in een bestaande Power shell-sessie ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="5a6c2-144">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing PowerShell session ( **PSSession** ).</span></span>

### <span data-ttu-id="5a6c2-145">Voor beeld 4: een interactieve sessie starten en de poort en de referentie parameters opgeven</span><span class="sxs-lookup"><span data-stu-id="5a6c2-145">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

<span data-ttu-id="5a6c2-146">Met deze opdracht wordt een interactieve sessie gestart met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-146">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="5a6c2-147">De para meter **poort** wordt gebruikt om de poort en de **referentie** parameter op te geven om het account op te geven van een gebruiker die gemachtigd is om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-147">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="5a6c2-148">Voor beeld 5: een interactieve sessie stoppen</span><span class="sxs-lookup"><span data-stu-id="5a6c2-148">Example 5: Stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

<span data-ttu-id="5a6c2-149">In dit voor beeld ziet u hoe u een interactieve sessie start en stopt.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-149">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="5a6c2-150">Met de eerste opdracht wordt de `Enter-PSSession` cmdlet gebruikt om een interactieve sessie met de Server01-computer te starten.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-150">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="5a6c2-151">De tweede opdracht gebruikt de `Exit-PSSession` cmdlet om de sessie te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-151">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="5a6c2-152">U kunt ook het sleutel woord **Exit** gebruiken om de interactieve sessie te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-152">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="5a6c2-153">`Exit-PSSession` en **Afsluiten** hebben hetzelfde effect.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-153">`Exit-PSSession` and **Exit** have the same effect.</span></span>

### <span data-ttu-id="5a6c2-154">Voor beeld 6: een interactieve sessie starten met SSH</span><span class="sxs-lookup"><span data-stu-id="5a6c2-154">Example 6: Start an interactive session using SSH</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="5a6c2-155">In dit voor beeld ziet u hoe u een interactieve sessie start met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="5a6c2-155">This example shows how to start an interactive session using Secure Shell (SSH).</span></span> <span data-ttu-id="5a6c2-156">Als SSH op de externe computer is geconfigureerd om te vragen om wacht woorden, wordt u gevraagd om een wacht woord op te geven.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-156">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span>
<span data-ttu-id="5a6c2-157">Anders moet u gebruikmaken van SSH-sleutel op basis van gebruikers verificatie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-157">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="5a6c2-158">Voor beeld 7: een interactieve sessie starten met SSH en de poort en gebruikers verificatie sleutel opgeven</span><span class="sxs-lookup"><span data-stu-id="5a6c2-158">Example 7: Start an interactive session using SSH and specify the Port and user authentication key</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="5a6c2-159">In dit voor beeld ziet u hoe u een interactieve sessie start met SSH.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-159">This example shows how to start an interactive session using SSH.</span></span> <span data-ttu-id="5a6c2-160">De para meter **poort** wordt gebruikt om de te gebruiken poort op te geven **en de para** meter voor het sleutelpad om een RSA-sleutel op te geven die wordt gebruikt om de gebruiker te verifiëren op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-160">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to authenticate the user on the remote computer.</span></span>

## <span data-ttu-id="5a6c2-161">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5a6c2-161">PARAMETERS</span></span>

### <span data-ttu-id="5a6c2-162">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="5a6c2-162">-AllowRedirection</span></span>

<span data-ttu-id="5a6c2-163">Hiermee kan de verbinding worden omgeleid naar een alternatieve URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="5a6c2-163">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="5a6c2-164">Omleiding is standaard niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-164">By default, redirection is not allowed.</span></span>

<span data-ttu-id="5a6c2-165">Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-165">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="5a6c2-166">Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding te omleiden.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-166">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="5a6c2-167">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-167">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="5a6c2-168">Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de `$PSSessionOption` Voorkeurs variabele in.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-168">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="5a6c2-169">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-169">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-170">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="5a6c2-170">-ApplicationName</span></span>

<span data-ttu-id="5a6c2-171">Hiermee geeft u het segment van de toepassings naam van de verbindings-URI op.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-171">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="5a6c2-172">Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de para meter **ConnectionURI** niet gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-172">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="5a6c2-173">De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-173">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="5a6c2-174">Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-174">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="5a6c2-175">Deze waarde is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-175">This value is appropriate for most uses.</span></span> <span data-ttu-id="5a6c2-176">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-176">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="5a6c2-177">De **WinRM** -service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-177">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="5a6c2-178">De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-178">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-179">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="5a6c2-179">-Authentication</span></span>

<span data-ttu-id="5a6c2-180">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-180">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="5a6c2-181">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="5a6c2-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5a6c2-182">Standaard</span><span class="sxs-lookup"><span data-stu-id="5a6c2-182">Default</span></span>
- <span data-ttu-id="5a6c2-183">Basic</span><span class="sxs-lookup"><span data-stu-id="5a6c2-183">Basic</span></span>
- <span data-ttu-id="5a6c2-184">CredSSP</span><span class="sxs-lookup"><span data-stu-id="5a6c2-184">Credssp</span></span>
- <span data-ttu-id="5a6c2-185">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="5a6c2-185">Digest</span></span>
- <span data-ttu-id="5a6c2-186">Kerberos</span><span class="sxs-lookup"><span data-stu-id="5a6c2-186">Kerberos</span></span>
- <span data-ttu-id="5a6c2-187">Negotiate</span><span class="sxs-lookup"><span data-stu-id="5a6c2-187">Negotiate</span></span>
- <span data-ttu-id="5a6c2-188">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="5a6c2-188">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="5a6c2-189">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-189">The default value is Default.</span></span>

<span data-ttu-id="5a6c2-190">CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-190">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="5a6c2-191">Zie [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-191">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="5a6c2-192">Let op: de verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-192">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="5a6c2-193">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-193">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="5a6c2-194">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-194">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-195">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="5a6c2-195">-CertificateThumbprint</span></span>

<span data-ttu-id="5a6c2-196">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-196">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="5a6c2-197">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-197">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="5a6c2-198">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-198">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="5a6c2-199">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-199">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="5a6c2-200">Als u een certificaat wilt ophalen, gebruikt u de `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-200">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="5a6c2-201">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="5a6c2-201">-ComputerName</span></span>

<span data-ttu-id="5a6c2-202">Hiermee geeft u een computer naam op.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-202">Specifies a computer name.</span></span> <span data-ttu-id="5a6c2-203">Met deze cmdlet wordt een interactieve sessie gestart met de opgegeven externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-203">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="5a6c2-204">Voer slechts één computer naam in.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-204">Enter only one computer name.</span></span> <span data-ttu-id="5a6c2-205">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-205">The default is the local computer.</span></span>

<span data-ttu-id="5a6c2-206">Typ de NetBIOS-naam, het IP-adres of de Fully Qualified Domain Name van de computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-206">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="5a6c2-207">U kunt ook een computer naam door geven aan `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-207">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="5a6c2-208">Als u een IP-adres wilt gebruiken in de waarde van de para meter **ComputerName** , moet de opdracht de para meter **Credential** bevatten.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-208">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="5a6c2-209">De computer moet ook worden geconfigureerd voor HTTPS-Trans Port of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-209">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="5a6c2-210">Zie "een computer toevoegen aan de lijst met vertrouwde hosts" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md)voor instructies voor het toevoegen van een computer naam aan de lijst TrustedHosts.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-210">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="5a6c2-211">Opmerking: in Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell starten met de optie als administrator uitvoeren om de lokale computer op te geven in de waarde van de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-211">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start PowerShell with the Run as administrator option.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-212">-Configuratiepad</span><span class="sxs-lookup"><span data-stu-id="5a6c2-212">-ConfigurationName</span></span>

<span data-ttu-id="5a6c2-213">Hiermee geeft u de sessie configuratie op die wordt gebruikt voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-213">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="5a6c2-214">Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-214">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="5a6c2-215">Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-215">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="5a6c2-216">Bij gebruik in combi natie met SSH geeft dit het subsysteem op dat op het doel moet worden gebruikt, zoals gedefinieerd in sshd_config.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-216">When used with SSH, this specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="5a6c2-217">De standaard waarde voor SSH is het `powershell` subsysteem.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-217">The default value for SSH is the `powershell` subsystem.</span></span>

<span data-ttu-id="5a6c2-218">De sessie configuratie voor een sessie bevindt zich op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-218">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="5a6c2-219">Als de opgegeven sessie configuratie niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-219">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="5a6c2-220">De standaard waarde is de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-220">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="5a6c2-221">Als deze voorkeurs variabele niet is ingesteld, is de standaard instelling micro soft. Power shell.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-221">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="5a6c2-222">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-222">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-223">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="5a6c2-223">-ConnectionUri</span></span>

<span data-ttu-id="5a6c2-224">Hiermee geeft u een URI op die het verbindings eindpunt voor de sessie definieert.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-224">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="5a6c2-225">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-225">The URI must be fully qualified.</span></span> <span data-ttu-id="5a6c2-226">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="5a6c2-226">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="5a6c2-227">De standaard waarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="5a6c2-227">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="5a6c2-228">Als u geen **ConnectionURI** opgeeft, kunt u de para meters **UseSSL** , **ComputerName** , **Port** en **ApplicationName** gebruiken om de **ConnectionURI** -waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-228">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="5a6c2-229">Geldige waarden voor het transport segment van de URI zijn HTTP en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-229">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="5a6c2-230">Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met behulp van standaard poorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-230">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="5a6c2-231">Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-231">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="5a6c2-232">Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-232">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-233">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="5a6c2-233">-ContainerId</span></span>

<span data-ttu-id="5a6c2-234">Hiermee geeft u de ID van een container op.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-234">Specifies the ID of a container.</span></span>

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-235">-Credential</span><span class="sxs-lookup"><span data-stu-id="5a6c2-235">-Credential</span></span>

<span data-ttu-id="5a6c2-236">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-236">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="5a6c2-237">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-237">The default is the current user.</span></span>

<span data-ttu-id="5a6c2-238">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-238">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="5a6c2-239">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-239">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="5a6c2-240">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="5a6c2-240">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="5a6c2-241">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-241">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-242">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="5a6c2-242">-EnableNetworkAccess</span></span>

<span data-ttu-id="5a6c2-243">Geeft aan dat met deze cmdlet een interactief beveiligings token wordt toegevoegd aan loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-243">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="5a6c2-244">Met het interactieve token kunt u opdrachten uitvoeren in de loop back-sessie die gegevens van andere computers ophalen.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-244">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="5a6c2-245">U kunt bijvoorbeeld een opdracht uitvoeren in de sessie waarmee XML-bestanden van een externe computer naar de lokale computer worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-245">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="5a6c2-246">Een loop back-sessie is een **PSSession** die afkomstig is van en eindigt op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-246">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="5a6c2-247">Als u een loop back-sessie wilt maken, laat u de para meter **ComputerName** weg of stelt u de waarde in op.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-247">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="5a6c2-248">(punt), localhost of de naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-248">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="5a6c2-249">Loop Back-sessies worden standaard gemaakt met behulp van een netwerk token, wat mogelijk niet voldoende machtigingen biedt om te verifiëren bij externe computers.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-249">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="5a6c2-250">De para meter **EnableNetworkAccess** is alleen effectief in loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-250">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="5a6c2-251">Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, mislukt de opdracht, maar wordt de para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-251">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="5a6c2-252">U kunt externe toegang ook toestaan in een loop back-sessie met behulp van de **CredSSP** -waarde van de **verificatie** parameter, die de sessie referenties delegeert naar andere computers.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-252">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="5a6c2-253">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-254">-Hostnaam</span><span class="sxs-lookup"><span data-stu-id="5a6c2-254">-HostName</span></span>

<span data-ttu-id="5a6c2-255">Hiermee geeft u een computer naam voor een verbinding op basis van SSH (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="5a6c2-255">Specifies a computer name for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="5a6c2-256">Dit is vergelijkbaar met de para meter **ComputerName** , behalve dat de verbinding met de externe computer wordt gemaakt met behulp van SSH in plaats van Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-256">This is similar to the **ComputerName** parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span> <span data-ttu-id="5a6c2-257">Met deze para meter kunt u de gebruikers naam en/of poort opgeven als onderdeel van de waarde van de para meter voor de naam van de hostnaam met behulp van het formulier `user@hostname:port` .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-257">This parameter supports specifying the user name and/or port as part of the host name parameter value using the form `user@hostname:port`.</span></span> <span data-ttu-id="5a6c2-258">De gebruikers naam en/of poort die is opgegeven als onderdeel van de hostnaam, hebben voor rang op de `-UserName` `-Port` para meters en, indien opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-258">The user name and/or port specified as part of the host name takes precedence over the `-UserName` and `-Port` parameters, if specified.</span></span> <span data-ttu-id="5a6c2-259">Hierdoor kunnen meerdere computer namen worden door gegeven aan deze para meter, waarbij sommige specifieke gebruikers namen en/of poorten worden gebruikt, terwijl anderen de gebruikers naam en/of poort van de `-UserName` `-Port` para meters en gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-259">This allows passing multiple computer names to this parameter where some have specific user names and/or ports, while others use the user name and/or port from the `-UserName` and `-Port` parameters.</span></span>

<span data-ttu-id="5a6c2-260">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-260">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-261">-Id</span><span class="sxs-lookup"><span data-stu-id="5a6c2-261">-Id</span></span>

<span data-ttu-id="5a6c2-262">Hiermee geeft u de ID op van een bestaande sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-262">Specifies the ID of an existing session.</span></span> <span data-ttu-id="5a6c2-263">`Enter-PSSession` maakt gebruik van de opgegeven sessie voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-263">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="5a6c2-264">Gebruik de cmdlet om de ID van een sessie te vinden `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-264">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-265">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="5a6c2-265">-InstanceId</span></span>

<span data-ttu-id="5a6c2-266">Hiermee geeft u de exemplaar-ID van een bestaande sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-266">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="5a6c2-267">`Enter-PSSession` maakt gebruik van de opgegeven sessie voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-267">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="5a6c2-268">De exemplaar-ID is een GUID.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-268">The instance ID is a GUID.</span></span> <span data-ttu-id="5a6c2-269">Gebruik de cmdlet om de exemplaar-ID van een sessie te vinden `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-269">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="5a6c2-270">U kunt ook de para meters voor de **sessie** , **naam** of **id** gebruiken om een bestaande sessie op te geven.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-270">You can also use the **Session** , **Name** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="5a6c2-271">U kunt ook de para meter **ComputerName** gebruiken om een tijdelijke sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-271">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-272">-Bestandspad</span><span class="sxs-lookup"><span data-stu-id="5a6c2-272">-KeyFilePath</span></span>

<span data-ttu-id="5a6c2-273">Hiermee geeft u een pad naar een sleutel bestand dat door een Secure Shell (SSH) wordt gebruikt om een gebruiker op een externe computer te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-273">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="5a6c2-274">Met SSH kan gebruikers verificatie worden uitgevoerd via persoonlijke/open bare sleutels als alternatief voor de basis wachtwoord verificatie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-274">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="5a6c2-275">Als de externe computer is geconfigureerd voor sleutel verificatie, kan deze para meter worden gebruikt om de sleutel op te geven waarmee de gebruiker wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-275">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="5a6c2-276">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-276">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-277">-Name</span><span class="sxs-lookup"><span data-stu-id="5a6c2-277">-Name</span></span>

<span data-ttu-id="5a6c2-278">Hiermee geeft u de beschrijvende naam van een bestaande sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-278">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="5a6c2-279">`Enter-PSSession` maakt gebruik van de opgegeven sessie voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-279">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="5a6c2-280">Als de naam die u opgeeft, overeenkomt met meer dan één sessie, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-280">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="5a6c2-281">U kunt ook de para meters **Session** , **InstanceId** of **id** gebruiken om een bestaande sessie op te geven.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-281">You can also use the **Session** , **InstanceID** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="5a6c2-282">U kunt ook de para meter **ComputerName** gebruiken om een tijdelijke sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-282">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="5a6c2-283">Als u een beschrijvende naam voor een sessie wilt instellen, gebruikt u de para meter **name** van de `New-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-283">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-284">-Port</span><span class="sxs-lookup"><span data-stu-id="5a6c2-284">-Port</span></span>

<span data-ttu-id="5a6c2-285">Hiermee geeft u de netwerk poort op de externe computer die wordt gebruikt voor deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-285">Specifies the network port on the remote computer that is used for this command.</span></span>

<span data-ttu-id="5a6c2-286">In Power shell 6,0 is deze para meter Inlcuded in de para meter **hostname** die ondersteuning biedt voor ssh-verbindingen (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="5a6c2-286">In PowerShell 6.0 this parameter was inlcuded in the **HostName** parameter set which supports Secure Shell (SSH) connections.</span></span>

<span data-ttu-id="5a6c2-287">**WinRM (ComputerName para meter set)**</span><span class="sxs-lookup"><span data-stu-id="5a6c2-287">**WinRM (ComputerName parameter set)**</span></span>

<span data-ttu-id="5a6c2-288">Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-288">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="5a6c2-289">De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-289">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="5a6c2-290">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-290">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="5a6c2-291">Gebruik de volgende opdrachten om de listener te configureren:</span><span class="sxs-lookup"><span data-stu-id="5a6c2-291">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="5a6c2-292">Gebruik de para meter **poort** alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-292">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="5a6c2-293">De poort instelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-293">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="5a6c2-294">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-294">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="5a6c2-295">**SSH (HostName para meter set)**</span><span class="sxs-lookup"><span data-stu-id="5a6c2-295">**SSH (HostName parameter set)**</span></span>

<span data-ttu-id="5a6c2-296">Als u verbinding wilt maken met een externe computer, moet de externe computer zijn geconfigureerd met de SSH-service (SSHD) en moet u Luis teren op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-296">To connect to a remote computer, the remote computer must be configured with the SSH service (SSHD) and must be listening on the port that the connection uses.</span></span> <span data-ttu-id="5a6c2-297">De standaard poort voor SSH is 22.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-297">The default port for SSH is 22.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-298">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="5a6c2-298">-RunAsAdministrator</span></span>

<span data-ttu-id="5a6c2-299">Geeft aan dat de **PSSession** wordt uitgevoerd als beheerder.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-299">Indicates that the **PSSession** runs as administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-300">-Sessie</span><span class="sxs-lookup"><span data-stu-id="5a6c2-300">-Session</span></span>

<span data-ttu-id="5a6c2-301">Hiermee geeft u een Power shell-sessie ( **PSSession** ) op die moet worden gebruikt voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-301">Specifies a PowerShell session ( **PSSession** ) to use for the interactive session.</span></span> <span data-ttu-id="5a6c2-302">Deze para meter gebruikt een sessie object.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-302">This parameter takes a session object.</span></span> <span data-ttu-id="5a6c2-303">U kunt ook de para meters **name** , **InstanceId** of **id** gebruiken om een **PSSession** op te geven.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-303">You can also use the **Name** , **InstanceID** , or **ID** parameters to specify a **PSSession**.</span></span>

<span data-ttu-id="5a6c2-304">Voer een variabele in die een sessie object bevat of een opdracht waarmee een sessie object wordt gemaakt of opgehaald, zoals een `New-PSSession` of- `Get-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-304">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="5a6c2-305">U kunt ook een sessie object door sluizen naar `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-305">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="5a6c2-306">U kunt slechts één **PSSession** verzenden met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-306">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="5a6c2-307">Als u een variabele opgeeft die meer dan één **PSSession** bevat, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-307">If you enter a variable that contains more than one **PSSession** , the command fails.</span></span>

<span data-ttu-id="5a6c2-308">Wanneer u `Exit-PSSession` of het sleutel woord **Exit** gebruikt, wordt de interactieve sessie beëindigd, maar de **PSSession** die u hebt gemaakt, blijft open en beschikbaar voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-308">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-309">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="5a6c2-309">-SessionOption</span></span>

<span data-ttu-id="5a6c2-310">Hiermee stelt u geavanceerde opties in voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-310">Sets advanced options for the session.</span></span> <span data-ttu-id="5a6c2-311">Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden voor de waarden van de sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-311">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="5a6c2-312">De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-312">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="5a6c2-313">Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-313">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="5a6c2-314">De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-314">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="5a6c2-315">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-315">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="5a6c2-316">Zie voor een beschrijving van de sessie opties, met inbegrip van de standaard waarden `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-316">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="5a6c2-317">Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](About/about_Preference_Variables.md)variabele.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-317">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="5a6c2-318">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-318">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-319">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="5a6c2-319">-SSHTransport</span></span>

<span data-ttu-id="5a6c2-320">Geeft aan dat de externe verbinding tot stand is gebracht met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="5a6c2-320">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="5a6c2-321">Power Shell maakt standaard gebruik van Windows WinRM om verbinding te maken met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-321">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="5a6c2-322">Met deze switch wordt Power shell gedwongen de para meter HostName te gebruiken die is ingesteld voor het maken van een externe SSH-verbinding.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-322">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="5a6c2-323">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-323">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-324">-Subsysteem</span><span class="sxs-lookup"><span data-stu-id="5a6c2-324">-Subsystem</span></span>

<span data-ttu-id="5a6c2-325">Hiermee geeft u het SSH-subsysteem op dat wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-325">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="5a6c2-326">Hiermee geeft u het subsysteem op dat moet worden gebruikt op het doel zoals gedefinieerd in sshd_config.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-326">This specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="5a6c2-327">Het subsysteem start een specifieke versie van Power shell met vooraf gedefinieerde para meters.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-327">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span> <span data-ttu-id="5a6c2-328">Als het opgegeven subsysteem niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-328">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="5a6c2-329">Als deze para meter niet wordt gebruikt, is de standaard het subsysteem Power shell.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-329">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

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

### <span data-ttu-id="5a6c2-330">-GebruikersNaam</span><span class="sxs-lookup"><span data-stu-id="5a6c2-330">-UserName</span></span>

<span data-ttu-id="5a6c2-331">Hiermee geeft u de gebruikers naam op voor het account dat wordt gebruikt om een sessie te maken op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-331">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="5a6c2-332">De verificatie methode voor de gebruiker is afhankelijk van hoe Secure Shell (SSH) is geconfigureerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-332">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="5a6c2-333">Als SSH is geconfigureerd voor basis wachtwoord verificatie, wordt u gevraagd om het wacht woord van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-333">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="5a6c2-334">Als SSH is geconfigureerd voor sleutel op basis van gebruikers verificatie, kan een pad naar een sleutel bestand worden opgegeven **via de para** meter voor het sleutelpad en er wordt geen wachtwoord prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-334">If SSH is configured for key based user authentication then a key file path can be provided via the **KeyFilePath** parameter and no password prompt will occur.</span></span> <span data-ttu-id="5a6c2-335">Houd er rekening mee dat als het sleutel bestand van de client gebruiker zich bevindt op een bekende SSH-locatie, de para meter voor het **bestandspad** niet nodig is voor op sleutels gebaseerde verificatie en de gebruikers verificatie automatisch wordt uitgevoerd op basis van de gebruikers naam.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-335">Note that if the client user key file is located in an SSH known location then the **KeyFilePath** parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="5a6c2-336">Raadpleeg SSH-documentatie over op sleutels gebaseerde gebruikers verificatie voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-336">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="5a6c2-337">Dit is geen vereiste para meter.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-337">This is not a required parameter.</span></span> <span data-ttu-id="5a6c2-338">Als er geen **username** -para meter is opgegeven, wordt de naam van de huidige aanmeldings gebruiker gebruikt voor de verbinding.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-338">If no **UserName** parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="5a6c2-339">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-339">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-340">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="5a6c2-340">-UseSSL</span></span>

<span data-ttu-id="5a6c2-341">Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-341">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="5a6c2-342">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-342">By default, SSL is not used.</span></span>

<span data-ttu-id="5a6c2-343">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-343">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="5a6c2-344">De para meter **UseSSL** is een extra beveiliging waarmee de gegevens worden verzonden via een HTTPS-verbinding in plaats van via een http-verbinding.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-344">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="5a6c2-345">Als u deze para meter gebruikt, maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-345">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-346">-VMId</span><span class="sxs-lookup"><span data-stu-id="5a6c2-346">-VMId</span></span>

<span data-ttu-id="5a6c2-347">Hiermee geeft u de ID van een virtuele machine op.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-347">Specifies the ID of a virtual machine.</span></span>

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-348">-VMName</span><span class="sxs-lookup"><span data-stu-id="5a6c2-348">-VMName</span></span>

<span data-ttu-id="5a6c2-349">Hiermee geeft u de naam van een virtuele machine op.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-349">Specifies the name of a virtual machine.</span></span>

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5a6c2-350">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a6c2-350">CommonParameters</span></span>

<span data-ttu-id="5a6c2-351">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-351">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5a6c2-352">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-352">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5a6c2-353">INVOER</span><span class="sxs-lookup"><span data-stu-id="5a6c2-353">INPUTS</span></span>

### <span data-ttu-id="5a6c2-354">System. String, System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="5a6c2-354">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="5a6c2-355">U kunt een computer naam, als een teken reeks of een sessie object door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-355">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="5a6c2-356">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5a6c2-356">OUTPUTS</span></span>

### <span data-ttu-id="5a6c2-357">Geen</span><span class="sxs-lookup"><span data-stu-id="5a6c2-357">None</span></span>

<span data-ttu-id="5a6c2-358">De cmdlet retourneert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-358">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="5a6c2-359">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5a6c2-359">NOTES</span></span>

<span data-ttu-id="5a6c2-360">Als u verbinding wilt maken met een externe computer, moet u lid zijn van de groep Administrators op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-360">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="5a6c2-361">Als u een interactieve sessie op de lokale computer wilt starten, moet u Power shell starten met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-361">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="5a6c2-362">Wanneer u gebruikt `Enter-PSSession` , wordt uw gebruikers profiel op de externe computer gebruikt voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-362">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="5a6c2-363">De opdrachten in het profiel voor externe gebruikers, met inbegrip van opdrachten voor het toevoegen van Power shell-modules en het wijzigen van de opdracht prompt, uitvoeren voordat de prompt op afstand wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-363">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="5a6c2-364">`Enter-PSSession` maakt gebruik van de GEBRUIKERSINTERFACE cultuur-instelling op de lokale computer voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-364">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="5a6c2-365">Gebruik de automatische variabele om de lokale GEBRUIKERSINTERFACE cultuur te vinden `$UICulture` .</span><span class="sxs-lookup"><span data-stu-id="5a6c2-365">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="5a6c2-366">`Enter-PSSession` vereist de `Get-Command` `Out-Default` `Exit-PSSession` cmdlets, en.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-366">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="5a6c2-367">Als deze cmdlets niet zijn opgenomen in de sessie configuratie op de externe computer, `Enter-PSSession` mislukt de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-367">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="5a6c2-368">In tegens telling tot `Invoke-Command` , waarbij de opdrachten worden geparseerd en geïnterpreteerd voordat deze naar de externe computer worden verzonden, `Enter-PSSession` verzendt de opdrachten rechtstreeks naar de externe computer zonder interpretatie.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-368">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="5a6c2-369">Als de sessie die u wilt invoeren, bezig is met het verwerken van een opdracht, kan er een vertraging optreden voordat Power shell reageert op de `Enter-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-369">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="5a6c2-370">U bent verbonden zodra de sessie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-370">You are connected as soon as the session is available.</span></span> <span data-ttu-id="5a6c2-371">U annuleert de `Enter-PSSession` opdracht door op <kbd>CTRL</kbd> + <kbd>C</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-371">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="5a6c2-372">De para meter **hostname** is opgenomen vanaf power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-372">The **HostName** parameter set was included starting with PowerShell 6.0.</span></span> <span data-ttu-id="5a6c2-373">Het is toegevoegd om externe communicatie van Power shell op te geven op basis van de Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="5a6c2-373">It was added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="5a6c2-374">SSH en Power shell worden ondersteund op meerdere platformen (Windows, Linux, macOS) en externe communicatie met Power shell werkt op deze platforms waarin Power shell en SSH zijn geïnstalleerd en geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-374">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="5a6c2-375">Dit is gescheiden van de vorige Windows-functie voor externe toegang die is gebaseerd op WinRM en veel van de specifieke WinRM-functies en-beperkingen zijn niet van toepassing.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-375">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="5a6c2-376">Zo worden op WinRM gebaseerde quota's, sessie opties, aangepaste eindpunt configuratie en functies voor ontkoppelen en opnieuw verbinden op dit moment niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-376">For example, WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="5a6c2-377">Zie voor meer informatie over het instellen van externe toegang tot Power shell [via SSH Power shell](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="5a6c2-377">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="5a6c2-378">Voorafgaand aan Power shell 7,1 heeft externe toegang via SSH geen ondersteuning voor externe sessies van de tweede hop.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-378">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="5a6c2-379">Deze mogelijkheid is beperkt tot sessies met WinRM.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-379">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="5a6c2-380">Met Power shell 7,1 kunt `Enter-PSSession` `Enter-PSHostProcess` u binnen elke interactieve externe sessie werken.</span><span class="sxs-lookup"><span data-stu-id="5a6c2-380">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="5a6c2-381">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5a6c2-381">RELATED LINKS</span></span>

[<span data-ttu-id="5a6c2-382">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="5a6c2-382">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="5a6c2-383">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="5a6c2-383">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="5a6c2-384">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="5a6c2-384">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="5a6c2-385">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="5a6c2-385">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="5a6c2-386">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="5a6c2-386">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="5a6c2-387">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="5a6c2-387">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="5a6c2-388">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="5a6c2-388">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="5a6c2-389">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="5a6c2-389">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="5a6c2-390">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="5a6c2-390">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="5a6c2-391">about_Remote</span><span class="sxs-lookup"><span data-stu-id="5a6c2-391">about_Remote</span></span>](About/about_Remote.md)
