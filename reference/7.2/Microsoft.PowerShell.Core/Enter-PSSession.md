---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 0fac823666277621c3bed0f961ae2ce22d8d8408
ms.sourcegitcommit: b10731301412afd4111743b85da95e8c25583533
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/20/2021
ms.locfileid: "107756236"
---
# <span data-ttu-id="7f5d0-102">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f5d0-102">Enter-PSSession</span></span>

## <span data-ttu-id="7f5d0-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="7f5d0-103">Synopsis</span></span>
<span data-ttu-id="7f5d0-104">Start een interactieve sessie met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-104">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="7f5d0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f5d0-105">Syntax</span></span>

### <span data-ttu-id="7f5d0-106">ComputerName (standaard)</span><span class="sxs-lookup"><span data-stu-id="7f5d0-106">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="7f5d0-107">SSHHost</span><span class="sxs-lookup"><span data-stu-id="7f5d0-107">SSHHost</span></span>

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [-ConnectingTimeout <int>] [<CommonParameters>]
```

### <span data-ttu-id="7f5d0-108">Sessie</span><span class="sxs-lookup"><span data-stu-id="7f5d0-108">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="7f5d0-109">Uri</span><span class="sxs-lookup"><span data-stu-id="7f5d0-109">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="7f5d0-110">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7f5d0-110">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="7f5d0-111">Id</span><span class="sxs-lookup"><span data-stu-id="7f5d0-111">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="7f5d0-112">Name</span><span class="sxs-lookup"><span data-stu-id="7f5d0-112">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="7f5d0-113">VMId</span><span class="sxs-lookup"><span data-stu-id="7f5d0-113">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="7f5d0-114">VMName</span><span class="sxs-lookup"><span data-stu-id="7f5d0-114">VMName</span></span>

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="7f5d0-115">ContainerId</span><span class="sxs-lookup"><span data-stu-id="7f5d0-115">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="7f5d0-116">Description</span><span class="sxs-lookup"><span data-stu-id="7f5d0-116">Description</span></span>

<span data-ttu-id="7f5d0-117">De `Enter-PSSession` cmdlet start een interactieve sessie met één externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-117">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span>
<span data-ttu-id="7f5d0-118">Tijdens de sessie worden de opdrachten die u typt, uitgevoerd op de externe computer, net alsof u rechtstreeks op de externe computer typt.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-118">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="7f5d0-119">U kunt slechts één interactieve sessie tegelijk hebben.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-119">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="7f5d0-120">Normaal gesproken gebruikt u de **ComputerName** parameter opgeven voor de naam van de externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-120">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="7f5d0-121">U kunt echter ook een sessie gebruiken die u maakt met behulp van de `New-PSSession` cmdlet voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-121">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="7f5d0-122">U kunt de cmdlets , of echter niet gebruiken om de verbinding met een interactieve sessie te verbreken of opnieuw verbinding `Disconnect-PSSession` `Connect-PSSession` te `Receive-PSSession` maken.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-122">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="7f5d0-123">Vanaf PowerShell 6.0 kunt u Secure Shell (SSH) gebruiken om verbinding te maken met een externe computer, als SSH beschikbaar is op de lokale computer en de externe computer is geconfigureerd met een PowerShell SSH-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-123">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="7f5d0-124">Het voordeel van een externe PowerShell-sessie op basis van SSH is dat deze op meerdere platforms (Windows, Linux, macOS) werkt.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-124">The benefit an SSH based PowerShell remote session is that it works across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="7f5d0-125">Voor externe toegang op basis van SSH gebruikt u de **parameterset HostName** om de externe computer en relevante verbindingsgegevens op te geven.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-125">For SSH based remoting you use the **HostName** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="7f5d0-126">Zie Voor meer informatie over het instellen van SSH-remoting voor [PowerShell Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="7f5d0-126">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="7f5d0-127">Als u de interactieve sessie wilt beëindigen en de verbinding met de externe computer wilt verbreken, gebruikt u `Exit-PSSession` de cmdlet of typt u `exit` .</span><span class="sxs-lookup"><span data-stu-id="7f5d0-127">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="7f5d0-128">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="7f5d0-128">Examples</span></span>

### <span data-ttu-id="7f5d0-129">Voorbeeld 1: Een interactieve sessie starten</span><span class="sxs-lookup"><span data-stu-id="7f5d0-129">Example 1: Start an interactive session</span></span>

```
PS> Enter-PSSession
[localhost]: PS>
```

<span data-ttu-id="7f5d0-130">Met deze opdracht start u een interactieve sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-130">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="7f5d0-131">De opdrachtprompt wordt gewijzigd om aan te geven dat u nu opdrachten in een andere sessie uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-131">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="7f5d0-132">De opdrachten die u op te geven, worden uitgevoerd in de nieuwe sessie en de resultaten worden als tekst geretourneerd naar de standaardsessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-132">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="7f5d0-133">Voorbeeld 2: Werken met een interactieve sessie</span><span class="sxs-lookup"><span data-stu-id="7f5d0-133">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="7f5d0-134">De eerste opdracht gebruikt de `Enter-PSSession` cmdlet voor het starten van een interactieve sessie met Server01, een externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-134">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="7f5d0-135">Wanneer de sessie wordt gestart, wordt de opdrachtprompt gewijzigd om de computernaam op te nemen.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-135">When the session starts, the command prompt changes to include the computer name.</span></span>

<span data-ttu-id="7f5d0-136">Met de tweede opdracht wordt het PowerShell-proces opgeslagen en wordt de uitvoer omgeleid naar Process.txt bestand.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-136">The second command gets the PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="7f5d0-137">De opdracht wordt verzonden naar de externe computer en het bestand wordt opgeslagen op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-137">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>

<span data-ttu-id="7f5d0-138">De derde opdracht maakt gebruik van **het trefwoord Afsluiten** om de interactieve sessie te beëindigen en de verbinding te sluiten.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-138">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="7f5d0-139">De vierde opdracht bevestigt dat het Process.txt bestand zich op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-139">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="7f5d0-140">Een `Get-ChildItem` opdracht ("dir") op de lokale computer kan het bestand niet vinden.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-140">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

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

<span data-ttu-id="7f5d0-141">Deze opdracht laat zien hoe u in een interactieve sessie met een externe computer werkt.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-141">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="7f5d0-142">Voorbeeld 3: De sessieparameter gebruiken</span><span class="sxs-lookup"><span data-stu-id="7f5d0-142">Example 3: Use the Session parameter</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

<span data-ttu-id="7f5d0-143">Deze opdrachten gebruiken de **sessieparameter** van om de interactieve sessie `Enter-PSSession` uit te voeren in een bestaande PowerShell-sessie **(PSSession).**</span><span class="sxs-lookup"><span data-stu-id="7f5d0-143">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing PowerShell session (**PSSession**).</span></span>

### <span data-ttu-id="7f5d0-144">Voorbeeld 4: Een interactieve sessie starten en de parameters Port en Credential opgeven</span><span class="sxs-lookup"><span data-stu-id="7f5d0-144">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

<span data-ttu-id="7f5d0-145">Met deze opdracht start u een interactieve sessie met de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-145">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="7f5d0-146">Hierbij de **poort** parameter opgeven voor de poort en de **referentie** parameter opgeven voor het account van een gebruiker die is machtigingen om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-146">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="7f5d0-147">Voorbeeld 5: Een interactieve sessie stoppen</span><span class="sxs-lookup"><span data-stu-id="7f5d0-147">Example 5: Stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

<span data-ttu-id="7f5d0-148">In dit voorbeeld ziet u hoe u een interactieve sessie start en stopt.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-148">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="7f5d0-149">De eerste opdracht gebruikt de `Enter-PSSession` cmdlet om een interactieve sessie met de computer Server01 te starten.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-149">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="7f5d0-150">De tweede opdracht gebruikt de `Exit-PSSession` cmdlet om de sessie te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-150">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="7f5d0-151">U kunt ook het **trefwoord Afsluiten** gebruiken om de interactieve sessie te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-151">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="7f5d0-152">`Exit-PSSession` en **Afsluiten** hebben hetzelfde effect.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-152">`Exit-PSSession` and **Exit** have the same effect.</span></span>

### <span data-ttu-id="7f5d0-153">Voorbeeld 6: Een interactieve sessie starten met SSH</span><span class="sxs-lookup"><span data-stu-id="7f5d0-153">Example 6: Start an interactive session using SSH</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="7f5d0-154">In dit voorbeeld ziet u hoe u een interactieve sessie start met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="7f5d0-154">This example shows how to start an interactive session using Secure Shell (SSH).</span></span> <span data-ttu-id="7f5d0-155">Als SSH is geconfigureerd op de externe computer om te vragen om wachtwoorden, krijgt u een wachtwoordprompt.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-155">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span>
<span data-ttu-id="7f5d0-156">Anders moet u gebruikersverificatie op basis van een SSH-sleutel gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-156">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="7f5d0-157">Voorbeeld 7: Een interactieve sessie starten met SSH en de sleutel voor poort- en gebruikersverificatie opgeven</span><span class="sxs-lookup"><span data-stu-id="7f5d0-157">Example 7: Start an interactive session using SSH and specify the Port and user authentication key</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="7f5d0-158">In dit voorbeeld ziet u hoe u een interactieve sessie start met behulp van SSH.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-158">This example shows how to start an interactive session using SSH.</span></span> <span data-ttu-id="7f5d0-159">De parameter **Port wordt** gebruikt om de poort op te geven die moet worden gebruikt en de parameter **KeyFilePath** om een RSA-sleutel op te geven die wordt gebruikt om de gebruiker op de externe computer te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-159">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to authenticate the user on the remote computer.</span></span>

## <span data-ttu-id="7f5d0-160">Parameters</span><span class="sxs-lookup"><span data-stu-id="7f5d0-160">Parameters</span></span>

### <span data-ttu-id="7f5d0-161">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="7f5d0-161">-AllowRedirection</span></span>

<span data-ttu-id="7f5d0-162">Staat omleiding van deze verbinding naar een alternatieve Uniform Resource Identifier (URI) toe.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-162">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="7f5d0-163">Omleiding is standaard niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-163">By default, redirection is not allowed.</span></span>

<span data-ttu-id="7f5d0-164">Wanneer u de **parameter ConnectionURI** gebruikt, kan de externe bestemming een instructie retourneren om om te leiden naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-164">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="7f5d0-165">PowerShell leidt verbindingen standaard niet om, maar u kunt deze parameter gebruiken om de verbinding om te leiden.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-165">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="7f5d0-166">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de **optiewaarde maximumConnectionRedirectionCount-sessie** te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-166">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="7f5d0-167">Gebruik de **parameter MaximumRedirection** van de cmdlet of stel de eigenschap `New-PSSessionOption` **MaximumConnectionRedirectionCount** van de `$PSSessionOption` voorkeursvariabele in.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-167">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="7f5d0-168">De standaardwaarde is 5.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-168">The default value is 5.</span></span>

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

### <span data-ttu-id="7f5d0-169">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="7f5d0-169">-ApplicationName</span></span>

<span data-ttu-id="7f5d0-170">Hiermee geeft u het toepassingsnaamsegment van de verbindings-URI op.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-170">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="7f5d0-171">Gebruik deze parameter om de naam van de toepassing op te geven wanneer u de **parameter ConnectionURI** niet gebruikt in de opdracht .</span><span class="sxs-lookup"><span data-stu-id="7f5d0-171">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="7f5d0-172">De standaardwaarde is de waarde van de `$PSSessionApplicationName` voorkeursvariabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-172">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="7f5d0-173">Als deze voorkeursvariabele niet is gedefinieerd, is de standaardwaarde WSMAN.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-173">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="7f5d0-174">Deze waarde is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-174">This value is appropriate for most uses.</span></span> <span data-ttu-id="7f5d0-175">Zie voor meer informatie [about_Preference_Variables.](About/about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="7f5d0-175">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="7f5d0-176">De **WinRM-service** gebruikt de toepassingsnaam om een listener te selecteren om de verbindingsaanvraag te verwerken.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-176">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="7f5d0-177">De waarde van deze parameter moet overeenkomen met de waarde van de **eigenschap URLPrefix** van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-177">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="7f5d0-178">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="7f5d0-178">-Authentication</span></span>

<span data-ttu-id="7f5d0-179">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-179">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="7f5d0-180">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="7f5d0-180">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7f5d0-181">Standaard</span><span class="sxs-lookup"><span data-stu-id="7f5d0-181">Default</span></span>
- <span data-ttu-id="7f5d0-182">Basic</span><span class="sxs-lookup"><span data-stu-id="7f5d0-182">Basic</span></span>
- <span data-ttu-id="7f5d0-183">Credssp</span><span class="sxs-lookup"><span data-stu-id="7f5d0-183">Credssp</span></span>
- <span data-ttu-id="7f5d0-184">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="7f5d0-184">Digest</span></span>
- <span data-ttu-id="7f5d0-185">Kerberos</span><span class="sxs-lookup"><span data-stu-id="7f5d0-185">Kerberos</span></span>
- <span data-ttu-id="7f5d0-186">Negotiate</span><span class="sxs-lookup"><span data-stu-id="7f5d0-186">Negotiate</span></span>
- <span data-ttu-id="7f5d0-187">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="7f5d0-187">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="7f5d0-188">De standaardwaarde is Standaard.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-188">The default value is Default.</span></span>

<span data-ttu-id="7f5d0-189">CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-189">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="7f5d0-190">Zie [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze parameter.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-190">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="7f5d0-191">Let op: CredSSP-verificatie (Credential Security Support Provider), waarbij de referenties van de gebruiker worden doorgegeven aan een externe computer om te worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie op meer dan één resource is vereist, zoals toegang tot een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-191">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="7f5d0-192">Dit mechanisme verhoogt het beveiligingsrisico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-192">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="7f5d0-193">Als de externe computer is gecompromitteerd, kunnen de referenties die worden doorgegeven aan de computer worden gebruikt voor het beheer van de netwerksessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-193">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="7f5d0-194">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="7f5d0-194">-CertificateThumbprint</span></span>

<span data-ttu-id="7f5d0-195">Hiermee geeft u het digitale openbare-sleutelcertificaat (X509) op van een gebruikersaccount dat is machtigingen heeft om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-195">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="7f5d0-196">Voer de vingerafdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-196">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="7f5d0-197">Certificaten worden gebruikt bij verificatie op basis van clientcertificaten.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-197">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="7f5d0-198">Ze kunnen alleen worden toe te wijs aan lokale gebruikersaccounts; ze werken niet met domeinaccounts.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-198">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="7f5d0-199">Als u een certificaat wilt verkrijgen, gebruikt u `Get-Item` de opdracht of in het `Get-ChildItem` PowerShell-station Certificaat: .</span><span class="sxs-lookup"><span data-stu-id="7f5d0-199">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="7f5d0-200">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7f5d0-200">-ComputerName</span></span>

<span data-ttu-id="7f5d0-201">Hiermee geeft u een computernaam.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-201">Specifies a computer name.</span></span> <span data-ttu-id="7f5d0-202">Deze cmdlet start een interactieve sessie met de opgegeven externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-202">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="7f5d0-203">Voer slechts één computernaam in.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-203">Enter only one computer name.</span></span> <span data-ttu-id="7f5d0-204">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-204">The default is the local computer.</span></span>

<span data-ttu-id="7f5d0-205">Typ de NetBIOS-naam, het IP-adres of de fully qualified domain name van de computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-205">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="7f5d0-206">U kunt ook een computernaam doorspijpen naar `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7f5d0-206">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="7f5d0-207">Als u een IP-adres wilt gebruiken in de waarde van de parameter **ComputerName,** moet de opdracht de parameter **Credential** bevatten.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-207">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="7f5d0-208">De computer moet ook worden geconfigureerd voor HTTPS-transport of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-208">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="7f5d0-209">Zie 'How to Add a Computer to the Trusted Host List' in about_Remote_Troubleshooting voor instructies voor het toevoegen van een computernaam [aan de](About/about_Remote_Troubleshooting.md)lijst met TrustedHosts.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-209">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="7f5d0-210">Opmerking: in Windows Vista en latere versies van het Windows-besturingssysteem moet u PowerShell starten met de optie Als administrator uitvoeren om de lokale computer op te nemen in de waarde van de parameter **ComputerName.**</span><span class="sxs-lookup"><span data-stu-id="7f5d0-210">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start PowerShell with the Run as administrator option.</span></span>

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

### <span data-ttu-id="7f5d0-211">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="7f5d0-211">-ConfigurationName</span></span>

<span data-ttu-id="7f5d0-212">Hiermee geeft u de sessieconfiguratie die wordt gebruikt voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-212">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="7f5d0-213">Voer een configuratienaam of de volledig gekwalificeerde resource-URI in voor een sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-213">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="7f5d0-214">Als u alleen de configuratienaam opgeeft, wordt de volgende schema-URI toegevoegd: `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="7f5d0-214">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="7f5d0-215">Bij gebruik met SSH geeft u hiermee het subsysteem op dat moet worden gebruikt op het doel, zoals gedefinieerd in sshd_config.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-215">When used with SSH, this specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="7f5d0-216">De standaardwaarde voor SSH is het `powershell` subsysteem.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-216">The default value for SSH is the `powershell` subsystem.</span></span>

<span data-ttu-id="7f5d0-217">De sessieconfiguratie voor een sessie bevindt zich op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-217">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="7f5d0-218">Als de opgegeven sessieconfiguratie niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-218">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="7f5d0-219">De standaardwaarde is de waarde van de `$PSSessionConfigurationName` voorkeursvariabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-219">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="7f5d0-220">Als deze voorkeursvariabele niet is ingesteld, is de standaardwaarde Microsoft.PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-220">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="7f5d0-221">Zie voor meer informatie [about_Preference_Variables.](About/about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="7f5d0-221">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="7f5d0-222">-ConnectingTimeout</span><span class="sxs-lookup"><span data-stu-id="7f5d0-222">-ConnectingTimeout</span></span>

<span data-ttu-id="7f5d0-223">Hiermee geeft u de hoeveelheid tijd in milliseconden op die is toegestaan voor het voltooien van de eerste SSH-verbinding.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-223">Specifies the amount of time in milliseconds allowed for the initial SSH connection to complete.</span></span> <span data-ttu-id="7f5d0-224">Als de verbinding niet binnen de opgegeven tijd wordt voltooid, wordt er een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-224">If the connection doesn't complete within the specified time, an error is returned.</span></span>

<span data-ttu-id="7f5d0-225">Deze parameter is geïntroduceerd in PowerShell 7.2</span><span class="sxs-lookup"><span data-stu-id="7f5d0-225">This parameter was introduced in PowerShell 7.2</span></span>

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

### <span data-ttu-id="7f5d0-226">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="7f5d0-226">-ConnectionUri</span></span>

<span data-ttu-id="7f5d0-227">Hiermee geeft u een URI op die het verbindings-eindpunt voor de sessie definieert.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-227">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="7f5d0-228">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-228">The URI must be fully qualified.</span></span> <span data-ttu-id="7f5d0-229">De indeling van deze tekenreeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7f5d0-229">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="7f5d0-230">De standaardwaarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7f5d0-230">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="7f5d0-231">Als u geen **ConnectionURI** opgeeft, kunt u de parameters **UseSSL,** **ComputerName,** **Port** en **ApplicationName** gebruiken om de **ConnectionURI-waarden op te** geven.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-231">If you do not specify a **ConnectionURI**, you can use the **UseSSL**, **ComputerName**, **Port**, and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="7f5d0-232">Geldige waarden voor het segment Transport van de URI zijn HTTP en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-232">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="7f5d0-233">Als u een verbindings-URI opgeeft met een Transport-segment, maar geen poort opgeeft, wordt de sessie gemaakt met behulp van standaardenpoorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-233">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="7f5d0-234">Als u de standaardpoorten wilt gebruiken voor remoting van PowerShell, geeft u poort 5985 voor HTTP of 5986 voor HTTPS op.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-234">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="7f5d0-235">Als de doelcomputer de verbinding omleiden naar een andere URI, PowerShell voorkomt de omleiding, tenzij u de **parameter AllowRedirection** in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-235">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="7f5d0-236">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="7f5d0-236">-ContainerId</span></span>

<span data-ttu-id="7f5d0-237">Hiermee geeft u de id van een container op.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-237">Specifies the ID of a container.</span></span>

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

### <span data-ttu-id="7f5d0-238">-Credential</span><span class="sxs-lookup"><span data-stu-id="7f5d0-238">-Credential</span></span>

<span data-ttu-id="7f5d0-239">Hiermee geeft u een gebruikersaccount op dat is machtigingen heeft om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-239">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="7f5d0-240">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-240">The default is the current user.</span></span>

<span data-ttu-id="7f5d0-241">Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een **PSCredential-object** in dat is gegenereerd door de `Get-Credential` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="7f5d0-241">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="7f5d0-242">Als u een gebruikersnaam typt, wordt u gevraagd het wachtwoord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-242">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="7f5d0-243">Referenties worden opgeslagen in een [PSCredential-object](/dotnet/api/system.management.automation.pscredential) en het wachtwoord wordt opgeslagen als een [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="7f5d0-243">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="7f5d0-244">Zie How secure is SecureString? (Hoe veilig [is SecureString?) voor meer informatie over SecureString-gegevensbeveiliging.](/dotnet/api/system.security.securestring#how-secure-is-securestring) </span><span class="sxs-lookup"><span data-stu-id="7f5d0-244">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="7f5d0-245">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="7f5d0-245">-EnableNetworkAccess</span></span>

<span data-ttu-id="7f5d0-246">Geeft aan dat deze cmdlet een interactief beveiliging token toevoegt aan loopback-sessies.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-246">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="7f5d0-247">Met het interactieve token kunt u opdrachten uitvoeren in de loopback-sessie die gegevens van andere computers op halen.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-247">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="7f5d0-248">U kunt bijvoorbeeld een opdracht uitvoeren in de sessie die XML-bestanden kopieert van een externe computer naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-248">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="7f5d0-249">Een loopback-sessie is **een PSSession** die afkomstig is van en eindigt op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-249">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="7f5d0-250">Als u een loopback-sessie wilt maken, laat u de parameter **ComputerName** weg of stelt u de waarde ervan in op .</span><span class="sxs-lookup"><span data-stu-id="7f5d0-250">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="7f5d0-251">(punt), localhost of de naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-251">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="7f5d0-252">Loopback-sessies worden standaard gemaakt met behulp van een netwerk-token, dat mogelijk onvoldoende machtigingen biedt voor verificatie bij externe computers.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-252">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="7f5d0-253">De **parameter EnableNetworkAccess** is alleen effectief in loopback-sessies.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-253">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="7f5d0-254">Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, slaagt de opdracht, maar de parameter wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-254">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="7f5d0-255">U kunt ook externe toegang toestaan in een loopback-sessie  met behulp van de **CredSSP-waarde** van de verificatieparameter, die de sessiereferenties delegeert naar andere computers.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-255">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="7f5d0-256">Deze parameter is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-256">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="7f5d0-257">-HostName</span><span class="sxs-lookup"><span data-stu-id="7f5d0-257">-HostName</span></span>

<span data-ttu-id="7f5d0-258">Hiermee geeft u een computernaam op voor een SSH-verbinding (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="7f5d0-258">Specifies a computer name for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="7f5d0-259">Dit is vergelijkbaar met de **ComputerName** parameter behalve dat de verbinding met de externe computer wordt gemaakt met behulp van SSH in plaats van Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-259">This is similar to the **ComputerName** parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span> <span data-ttu-id="7f5d0-260">Deze parameter ondersteunt het opgeven van de gebruikersnaam en/of poort als onderdeel van de parameterwaarde van de hostnaam met behulp van het formulier `user@hostname:port` .</span><span class="sxs-lookup"><span data-stu-id="7f5d0-260">This parameter supports specifying the user name and/or port as part of the host name parameter value using the form `user@hostname:port`.</span></span> <span data-ttu-id="7f5d0-261">De gebruikersnaam en/of poort die zijn opgegeven als onderdeel van de hostnaam heeft voorrang op de `-UserName` `-Port` parameters en, indien opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-261">The user name and/or port specified as part of the host name takes precedence over the `-UserName` and `-Port` parameters, if specified.</span></span> <span data-ttu-id="7f5d0-262">Hierdoor kunnen meerdere computernamen worden doorgegeven aan deze parameter, waarbij sommige specifieke gebruikersnamen en/of poorten hebben, terwijl andere de gebruikersnaam en/of poort van de `-UserName` `-Port` parameters en gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-262">This allows passing multiple computer names to this parameter where some have specific user names and/or ports, while others use the user name and/or port from the `-UserName` and `-Port` parameters.</span></span>

<span data-ttu-id="7f5d0-263">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-263">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="7f5d0-264">-Id</span><span class="sxs-lookup"><span data-stu-id="7f5d0-264">-Id</span></span>

<span data-ttu-id="7f5d0-265">Hiermee geeft u de id van een bestaande sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-265">Specifies the ID of an existing session.</span></span> <span data-ttu-id="7f5d0-266">`Enter-PSSession` gebruikt de opgegeven sessie voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-266">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="7f5d0-267">Gebruik de cmdlet om de id van een `Get-PSSession` sessie te vinden.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-267">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="7f5d0-268">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="7f5d0-268">-InstanceId</span></span>

<span data-ttu-id="7f5d0-269">Hiermee geeft u de exemplaar-id van een bestaande sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-269">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="7f5d0-270">`Enter-PSSession` gebruikt de opgegeven sessie voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-270">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="7f5d0-271">De exemplaar-id is een GUID.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-271">The instance ID is a GUID.</span></span> <span data-ttu-id="7f5d0-272">Gebruik de cmdlet om de exemplaar-id van een `Get-PSSession` sessie te vinden.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-272">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="7f5d0-273">U kunt ook de parameters **Sessie,** **Naam** of **Id** gebruiken om een bestaande sessie op te geven.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-273">You can also use the **Session**, **Name**, or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="7f5d0-274">U kunt ook de **parameter ComputerName gebruiken** om een tijdelijke sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-274">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

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

### <span data-ttu-id="7f5d0-275">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="7f5d0-275">-KeyFilePath</span></span>

<span data-ttu-id="7f5d0-276">Hiermee geeft u een sleutelbestandspad op dat door Secure Shell (SSH) wordt gebruikt om een gebruiker op een externe computer te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-276">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="7f5d0-277">Met SSH kan gebruikersverificatie worden uitgevoerd via persoonlijke/openbare sleutels als alternatief voor basiswachtwoordverificatie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-277">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="7f5d0-278">Als de externe computer is geconfigureerd voor sleutelverificatie, kan deze parameter worden gebruikt om de sleutel op te geven waarmee de gebruiker wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-278">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="7f5d0-279">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-279">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="7f5d0-280">-Name</span><span class="sxs-lookup"><span data-stu-id="7f5d0-280">-Name</span></span>

<span data-ttu-id="7f5d0-281">Hiermee geeft u de naam van een bestaande sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-281">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="7f5d0-282">`Enter-PSSession` gebruikt de opgegeven sessie voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-282">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="7f5d0-283">Als de naam die u opgeeft overeenkomt met meer dan één sessie, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-283">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="7f5d0-284">U kunt ook de parameters **Session,** **InstanceID** of **ID** gebruiken om een bestaande sessie op te geven.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-284">You can also use the **Session**, **InstanceID**, or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="7f5d0-285">U kunt ook de **parameter ComputerName gebruiken** om een tijdelijke sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-285">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="7f5d0-286">Als u een gebruiksvriendelijke naam voor een sessie wilt maken, gebruikt u de parameter **Name** van de `New-PSSession` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="7f5d0-286">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="7f5d0-287">-Port</span><span class="sxs-lookup"><span data-stu-id="7f5d0-287">-Port</span></span>

<span data-ttu-id="7f5d0-288">Hiermee geeft u de netwerkpoort op de externe computer die wordt gebruikt voor deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-288">Specifies the network port on the remote computer that is used for this command.</span></span>

<span data-ttu-id="7f5d0-289">In PowerShell 6.0 is deze parameter in de **parameterset HostName** gebruikt die ondersteuning biedt voor SSH-verbindingen (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="7f5d0-289">In PowerShell 6.0 this parameter was inlcuded in the **HostName** parameter set which supports Secure Shell (SSH) connections.</span></span>

<span data-ttu-id="7f5d0-290">**WinRM (parameterset ComputerName)**</span><span class="sxs-lookup"><span data-stu-id="7f5d0-290">**WinRM (ComputerName parameter set)**</span></span>

<span data-ttu-id="7f5d0-291">Als u verbinding wilt maken met een externe computer, moet de externe computer luisteren op de poort die de verbinding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-291">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="7f5d0-292">De standaardpoorten zijn 5985, de WinRM-poort voor HTTP, en 5986, de WinRM-poort voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-292">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="7f5d0-293">Voordat u een alternatieve poort gebruikt, moet u de WinRM-listener op de externe computer configureren om naar die poort te luisteren.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-293">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="7f5d0-294">Gebruik de volgende opdrachten om de listener te configureren:</span><span class="sxs-lookup"><span data-stu-id="7f5d0-294">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="7f5d0-295">Gebruik de parameter **Port alleen** als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-295">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="7f5d0-296">De poortinstelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-296">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="7f5d0-297">Een alternatieve poortinstelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-297">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="7f5d0-298">**SSH (set hostnaamparameters)**</span><span class="sxs-lookup"><span data-stu-id="7f5d0-298">**SSH (HostName parameter set)**</span></span>

<span data-ttu-id="7f5d0-299">Als u verbinding wilt maken met een externe computer, moet de externe computer zijn geconfigureerd met de SSH-service (SSHD) en moet deze luisteren op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-299">To connect to a remote computer, the remote computer must be configured with the SSH service (SSHD) and must be listening on the port that the connection uses.</span></span> <span data-ttu-id="7f5d0-300">De standaardpoort voor SSH is 22.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-300">The default port for SSH is 22.</span></span>

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

### <span data-ttu-id="7f5d0-301">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="7f5d0-301">-RunAsAdministrator</span></span>

<span data-ttu-id="7f5d0-302">Geeft aan dat **pssession wordt uitgevoerd** als beheerder.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-302">Indicates that the **PSSession** runs as administrator.</span></span>

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

### <span data-ttu-id="7f5d0-303">-Sessie</span><span class="sxs-lookup"><span data-stu-id="7f5d0-303">-Session</span></span>

<span data-ttu-id="7f5d0-304">Hiermee geeft u een PowerShell-sessie **(PSSession**) op die moet worden gebruikt voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-304">Specifies a PowerShell session (**PSSession**) to use for the interactive session.</span></span> <span data-ttu-id="7f5d0-305">Deze parameter gebruikt een sessieobject.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-305">This parameter takes a session object.</span></span> <span data-ttu-id="7f5d0-306">U kunt ook de parameters **Name,** **InstanceID** of **ID** gebruiken om een **PSSession op te geven.**</span><span class="sxs-lookup"><span data-stu-id="7f5d0-306">You can also use the **Name**, **InstanceID**, or **ID** parameters to specify a **PSSession**.</span></span>

<span data-ttu-id="7f5d0-307">Voer een variabele in die een sessieobject bevat of een opdracht die een sessieobject maakt of op haalt, zoals een `New-PSSession` - of `Get-PSSession` -opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-307">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="7f5d0-308">U kunt ook een sessieobject doorspijpen naar `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7f5d0-308">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="7f5d0-309">U kunt slechts één **PSSession verzenden met** behulp van deze parameter.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-309">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="7f5d0-310">Als u een variabele met meer dan één **PSSession opgeeft,** mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-310">If you enter a variable that contains more than one **PSSession**, the command fails.</span></span>

<span data-ttu-id="7f5d0-311">Wanneer u of `Exit-PSSession` het **trefwoord EXIT** gebruikt, wordt de interactieve sessie beëindigd, maar de **PSSession** die u hebt gemaakt, blijft geopend en beschikbaar voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-311">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

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

### <span data-ttu-id="7f5d0-312">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="7f5d0-312">-SessionOption</span></span>

<span data-ttu-id="7f5d0-313">Hiermee stelt u geavanceerde opties voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-313">Sets advanced options for the session.</span></span> <span data-ttu-id="7f5d0-314">Voer een **SessionOption-object** in, zoals een object dat u maakt met behulp van de cmdlet of een hash-tabel waarin de sleutels sessieoptienamen zijn en de waarden `New-PSSessionOption` sessieoptiewaarden zijn.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-314">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="7f5d0-315">De standaardwaarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` voorkeursvariabele als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-315">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="7f5d0-316">Anders worden de standaardwaarden ingesteld door opties die zijn ingesteld in de sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-316">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="7f5d0-317">De waarden van de sessieoptie hebben voorrang op de standaardwaarden voor sessies die zijn ingesteld in de `$PSSessionOption` voorkeursvariabele en in de sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-317">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="7f5d0-318">Ze hebben echter geen voorrang op maximumwaarden, quota of limieten die zijn ingesteld in de sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-318">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="7f5d0-319">Zie voor een beschrijving van de sessieopties, met inbegrip van de `New-PSSessionOption` standaardwaarden.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-319">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="7f5d0-320">Zie voor meer informatie `$PSSessionOption` over de voorkeursvariabele [about_Preference_Variables.](About/about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="7f5d0-320">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="7f5d0-321">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-321">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="7f5d0-322">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="7f5d0-322">-SSHTransport</span></span>

<span data-ttu-id="7f5d0-323">Geeft aan dat de externe verbinding tot stand is gebracht met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="7f5d0-323">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="7f5d0-324">PowerShell maakt standaard gebruik van Windows WinRM om verbinding te maken met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-324">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="7f5d0-325">Deze schakelknop dwingt PowerShell om de parameterset HostName te gebruiken voor het tot stand brengen van een externe SSH-verbinding.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-325">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="7f5d0-326">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-326">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="7f5d0-327">-Subsysteem</span><span class="sxs-lookup"><span data-stu-id="7f5d0-327">-Subsystem</span></span>

<span data-ttu-id="7f5d0-328">Hiermee geeft u het SSH-subsysteem op dat wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-328">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="7f5d0-329">Hiermee geeft u het subsysteem op dat moet worden gebruikt op het doel, zoals gedefinieerd in sshd_config.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-329">This specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="7f5d0-330">Het subsysteem start een specifieke versie van PowerShell met vooraf gedefinieerde parameters.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-330">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span> <span data-ttu-id="7f5d0-331">Als het opgegeven subsysteem niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-331">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="7f5d0-332">Als deze parameter niet wordt gebruikt, is de standaardwaarde het subsysteem 'powershell'.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-332">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

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

### <span data-ttu-id="7f5d0-333">-GebruikersNaam</span><span class="sxs-lookup"><span data-stu-id="7f5d0-333">-UserName</span></span>

<span data-ttu-id="7f5d0-334">Hiermee geeft u de gebruikersnaam voor het account dat wordt gebruikt voor het maken van een sessie op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-334">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="7f5d0-335">De verificatiemethode voor gebruikers is afhankelijk van hoe Secure Shell (SSH) is geconfigureerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-335">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="7f5d0-336">Als SSH is geconfigureerd voor basisverificatie van wachtwoorden, wordt u gevraagd om het gebruikerswachtwoord.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-336">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="7f5d0-337">Als SSH is geconfigureerd voor gebruikersverificatie op basis van sleutels, kan er een pad naar een sleutelbestand worden opgegeven via de parameter **KeyFilePath** en wordt er geen wachtwoordprompt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-337">If SSH is configured for key based user authentication then a key file path can be provided via the **KeyFilePath** parameter and no password prompt will occur.</span></span> <span data-ttu-id="7f5d0-338">Houd er rekening mee dat als het clientgebruikerssleutelbestand zich op een bekende SSH-locatie bevindt, de parameter **KeyFilePath** niet nodig is voor verificatie op basis van sleutels en dat gebruikersverificatie automatisch wordt uitgevoerd op basis van de gebruikersnaam.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-338">Note that if the client user key file is located in an SSH known location then the **KeyFilePath** parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="7f5d0-339">Zie SSH-documentatie over op sleutels gebaseerde gebruikersverificatie voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-339">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="7f5d0-340">Dit is geen vereiste parameter.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-340">This is not a required parameter.</span></span> <span data-ttu-id="7f5d0-341">Als er **geen userName** parameter is opgegeven, wordt de huidige gebruikersnaam voor aanmelden gebruikt voor de verbinding.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-341">If no **UserName** parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="7f5d0-342">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-342">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="7f5d0-343">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="7f5d0-343">-UseSSL</span></span>

<span data-ttu-id="7f5d0-344">Geeft aan dat deze cmdlet het SSL-protocol (Secure Sockets Layer) gebruikt om een verbinding met de externe computer tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-344">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="7f5d0-345">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-345">By default, SSL is not used.</span></span>

<span data-ttu-id="7f5d0-346">WS-Management versleutelt alle PowerShell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-346">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="7f5d0-347">De **parameter UseSSL** is een extra beveiliging die de gegevens via een HTTPS-verbinding verzendt in plaats van een HTTP-verbinding.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-347">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="7f5d0-348">Als u deze parameter gebruikt, maar SSL niet beschikbaar is op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-348">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="7f5d0-349">-VMId</span><span class="sxs-lookup"><span data-stu-id="7f5d0-349">-VMId</span></span>

<span data-ttu-id="7f5d0-350">Hiermee geeft u de id van een virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-350">Specifies the ID of a virtual machine.</span></span>

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

### <span data-ttu-id="7f5d0-351">-VMName</span><span class="sxs-lookup"><span data-stu-id="7f5d0-351">-VMName</span></span>

<span data-ttu-id="7f5d0-352">Hiermee geeft u de naam van een virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-352">Specifies the name of a virtual machine.</span></span>

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

### <span data-ttu-id="7f5d0-353">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7f5d0-353">CommonParameters</span></span>

<span data-ttu-id="7f5d0-354">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-354">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7f5d0-355">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7f5d0-355">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7f5d0-356">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="7f5d0-356">Inputs</span></span>

### <span data-ttu-id="7f5d0-357">System.String, System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="7f5d0-357">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="7f5d0-358">U kunt een computernaam, als een tekenreeks of een sessieobject doorseen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-358">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="7f5d0-359">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="7f5d0-359">Outputs</span></span>

### <span data-ttu-id="7f5d0-360">Geen</span><span class="sxs-lookup"><span data-stu-id="7f5d0-360">None</span></span>

<span data-ttu-id="7f5d0-361">De cmdlet retourneerde geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-361">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="7f5d0-362">Notities</span><span class="sxs-lookup"><span data-stu-id="7f5d0-362">Notes</span></span>

<span data-ttu-id="7f5d0-363">Als u verbinding wilt maken met een externe computer, moet u lid zijn van de groep Administrators op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-363">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="7f5d0-364">Als u een interactieve sessie op de lokale computer wilt starten, moet u PowerShell starten met de **optie Als administrator** uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-364">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="7f5d0-365">Wanneer u `Enter-PSSession` gebruikt, wordt uw gebruikersprofiel op de externe computer gebruikt voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-365">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="7f5d0-366">De opdrachten in het profiel van de externe gebruiker, inclusief opdrachten voor het toevoegen van PowerShell-modules en om de opdrachtprompt te wijzigen, voert u uit voordat de externe prompt wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-366">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="7f5d0-367">`Enter-PSSession` gebruikt de cultuurinstelling ui op de lokale computer voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-367">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="7f5d0-368">Gebruik de automatische variabele om de lokale UI-cultuur `$UICulture` te vinden.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-368">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="7f5d0-369">`Enter-PSSession` vereist `Get-Command` de `Out-Default` `Exit-PSSession` cmdlets , en .</span><span class="sxs-lookup"><span data-stu-id="7f5d0-369">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="7f5d0-370">Als deze cmdlets niet zijn opgenomen in de sessieconfiguratie op de externe computer, mislukt `Enter-PSSession` de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-370">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="7f5d0-371">In tegenstelling tot , die de opdrachten parseert en interpreteert voordat deze naar de externe computer worden verzendt, verzendt de opdrachten rechtstreeks naar de externe `Invoke-Command` `Enter-PSSession` computer zonder interpretatie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-371">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="7f5d0-372">Als de sessie die u wilt invoeren bezig is met het verwerken van een opdracht, kan er een vertraging zijn voordat PowerShell op de opdracht `Enter-PSSession` reageert.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-372">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="7f5d0-373">U bent verbonden zodra de sessie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-373">You are connected as soon as the session is available.</span></span> <span data-ttu-id="7f5d0-374">Druk op `Enter-PSSession` <kbd>CTRL C</kbd>om de opdracht + <kbd>te annuleren.</kbd></span><span class="sxs-lookup"><span data-stu-id="7f5d0-374">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="7f5d0-375">De **parameterset HostName** is opgenomen vanaf PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-375">The **HostName** parameter set was included starting with PowerShell 6.0.</span></span> <span data-ttu-id="7f5d0-376">Het is toegevoegd om Toegang tot PowerShell te bieden op basis van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="7f5d0-376">It was added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="7f5d0-377">Zowel SSH als PowerShell worden ondersteund op meerdere platforms (Windows, Linux, macOS) en voor het voor mobiele gebruik van PowerShell worden deze platformen gebruikt waarop PowerShell en SSH zijn geïnstalleerd en geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-377">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="7f5d0-378">Dit staat los van de vorige windows-remoting die is gebaseerd op WinRM en veel van de specifieke WinRM-functies en -beperkingen zijn niet van toepassing.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-378">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="7f5d0-379">Op WinRM gebaseerde quota, sessieopties, aangepaste eindpuntconfiguratie en functies voor verbreken/opnieuw verbinden worden momenteel bijvoorbeeld niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-379">For example, WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="7f5d0-380">Zie Voor meer informatie over het instellen van SSH-remoting voor [PowerShell Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="7f5d0-380">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="7f5d0-381">Vóór PowerShell 7.1 biedt externe externe sessies geen ondersteuning voor externe sessies via externe toegang via SSH.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-381">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="7f5d0-382">Deze mogelijkheid was beperkt tot sessies met WinRM.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-382">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="7f5d0-383">Met PowerShell 7.1 kunnen `Enter-PSSession` en werken vanuit elke interactieve externe `Enter-PSHostProcess` sessie.</span><span class="sxs-lookup"><span data-stu-id="7f5d0-383">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="7f5d0-384">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="7f5d0-384">Related Links</span></span>

[<span data-ttu-id="7f5d0-385">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f5d0-385">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="7f5d0-386">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f5d0-386">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="7f5d0-387">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="7f5d0-387">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="7f5d0-388">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f5d0-388">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="7f5d0-389">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f5d0-389">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="7f5d0-390">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f5d0-390">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="7f5d0-391">Verbinding verbreken met PSSession</span><span class="sxs-lookup"><span data-stu-id="7f5d0-391">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="7f5d0-392">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f5d0-392">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="7f5d0-393">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="7f5d0-393">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="7f5d0-394">about_Remote</span><span class="sxs-lookup"><span data-stu-id="7f5d0-394">about_Remote</span></span>](About/about_Remote.md)
