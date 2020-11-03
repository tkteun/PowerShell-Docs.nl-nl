---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 40d9da7d2e7e3233608b893b026c2b89c7155ab1
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/24/2020
ms.locfileid: "93251667"
---
# <span data-ttu-id="6c74f-103">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="6c74f-103">Enter-PSSession</span></span>

## <span data-ttu-id="6c74f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6c74f-104">SYNOPSIS</span></span>
<span data-ttu-id="6c74f-105">Start een interactieve sessie met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-105">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="6c74f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6c74f-106">SYNTAX</span></span>

### <span data-ttu-id="6c74f-107">Computer naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="6c74f-107">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="6c74f-108">Sessie</span><span class="sxs-lookup"><span data-stu-id="6c74f-108">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="6c74f-109">URI</span><span class="sxs-lookup"><span data-stu-id="6c74f-109">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="6c74f-110">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6c74f-110">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="6c74f-111">Id</span><span class="sxs-lookup"><span data-stu-id="6c74f-111">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="6c74f-112">Naam</span><span class="sxs-lookup"><span data-stu-id="6c74f-112">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="6c74f-113">VMId</span><span class="sxs-lookup"><span data-stu-id="6c74f-113">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> -Credential <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="6c74f-114">VMName</span><span class="sxs-lookup"><span data-stu-id="6c74f-114">VMName</span></span>

```
Enter-PSSession [-VMName] <String> -Credential <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="6c74f-115">ContainerId</span><span class="sxs-lookup"><span data-stu-id="6c74f-115">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="6c74f-116">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6c74f-116">DESCRIPTION</span></span>

<span data-ttu-id="6c74f-117">`Enter-PSSession`Met de cmdlet wordt een interactieve sessie met één externe computer gestart.</span><span class="sxs-lookup"><span data-stu-id="6c74f-117">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span> <span data-ttu-id="6c74f-118">Tijdens de sessie worden de opdrachten die u typt op de externe computer uitgevoerd, net alsof u rechtstreeks op de externe computer typt.</span><span class="sxs-lookup"><span data-stu-id="6c74f-118">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="6c74f-119">U kunt slechts één interactieve sessie tegelijk hebben.</span><span class="sxs-lookup"><span data-stu-id="6c74f-119">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="6c74f-120">Normaal gesp roken gebruikt u de para meter **ComputerName** om de naam van de externe computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="6c74f-120">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="6c74f-121">U kunt echter ook een sessie gebruiken die u maakt met behulp van de `New-PSSession` cmdlet voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-121">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="6c74f-122">U kunt echter de-, `Disconnect-PSSession` `Connect-PSSession` -of-cmdlets niet gebruiken om de verbinding met `Receive-PSSession` een interactieve sessie te verbreken of opnieuw te verbinden.</span><span class="sxs-lookup"><span data-stu-id="6c74f-122">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="6c74f-123">Als u de interactieve sessie wilt beëindigen en de verbinding wilt verbreken met de externe computer, gebruikt u de `Exit-PSSession` cmdlet of het type `exit` .</span><span class="sxs-lookup"><span data-stu-id="6c74f-123">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="6c74f-124">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6c74f-124">EXAMPLES</span></span>

### <span data-ttu-id="6c74f-125">Voor beeld 1: een interactieve sessie starten</span><span class="sxs-lookup"><span data-stu-id="6c74f-125">Example 1: Start an interactive session</span></span>

```
PS C:\> Enter-PSSession
[localhost]: PS C:\>
```

<span data-ttu-id="6c74f-126">Met deze opdracht wordt een interactieve sessie gestart op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-126">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="6c74f-127">De opdracht prompt wordt gewijzigd om aan te geven dat u nu opdrachten uitvoert in een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-127">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="6c74f-128">De opdrachten die u invoert, worden uitgevoerd in de nieuwe sessie en de resultaten worden geretourneerd naar de standaard sessie als tekst.</span><span class="sxs-lookup"><span data-stu-id="6c74f-128">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="6c74f-129">Voor beeld 2: werken met een interactieve sessie</span><span class="sxs-lookup"><span data-stu-id="6c74f-129">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="6c74f-130">Met de eerste opdracht wordt de `Enter-PSSession` cmdlet gebruikt voor het starten van een interactieve sessie met Server01, een externe computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-130">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="6c74f-131">Wanneer de sessie wordt gestart, wordt de computer naam in de opdracht prompt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="6c74f-131">When the session starts, the command prompt changes to include the computer name.</span></span>
<span data-ttu-id="6c74f-132">Met de tweede opdracht wordt het Windows Power Shell-proces opgehaald en wordt de uitvoer omgeleid naar het Process.txt-bestand.</span><span class="sxs-lookup"><span data-stu-id="6c74f-132">The second command gets the Windows PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="6c74f-133">De opdracht wordt verzonden naar de externe computer en het bestand wordt opgeslagen op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-133">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>
<span data-ttu-id="6c74f-134">De derde opdracht maakt gebruik van het sleutel woord **Exit** om de interactieve sessie te beëindigen en sluit de verbinding.</span><span class="sxs-lookup"><span data-stu-id="6c74f-134">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="6c74f-135">Met de vierde opdracht wordt bevestigd dat het Process.txt-bestand zich op de externe computer bevindt.</span><span class="sxs-lookup"><span data-stu-id="6c74f-135">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="6c74f-136">Een `Get-ChildItem` ("dir") opdracht op de lokale computer kan het bestand niet vinden.</span><span class="sxs-lookup"><span data-stu-id="6c74f-136">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

<span data-ttu-id="6c74f-137">Met deze opdracht wordt aangegeven hoe u kunt werken in een interactieve sessie met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-137">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="6c74f-138">Voor beeld 3: de sessie parameter gebruiken</span><span class="sxs-lookup"><span data-stu-id="6c74f-138">Example 3: Use the Session parameter</span></span>

```powershell
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
[Server01]: PS C:\>
```

<span data-ttu-id="6c74f-139">Met deze opdrachten wordt de **sessie** parameter van gebruikt `Enter-PSSession` voor het uitvoeren van de interactieve sessie in een bestaande Windows Power shell-sessie ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="6c74f-139">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing Windows PowerShell session ( **PSSession** ).</span></span>

### <span data-ttu-id="6c74f-140">Voor beeld 4: een interactieve sessie starten en de poort en de referentie parameters opgeven</span><span class="sxs-lookup"><span data-stu-id="6c74f-140">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS C:\>
```

<span data-ttu-id="6c74f-141">Met deze opdracht wordt een interactieve sessie gestart met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-141">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="6c74f-142">De para meter **poort** wordt gebruikt om de poort en de **referentie** parameter op te geven om het account op te geven van een gebruiker die gemachtigd is om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-142">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="6c74f-143">Voor beeld 5: een interactieve sessie stoppen</span><span class="sxs-lookup"><span data-stu-id="6c74f-143">Example 5: Stop an interactive session</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\> Exit-PSSession
PS C:\>
```

<span data-ttu-id="6c74f-144">In dit voor beeld ziet u hoe u een interactieve sessie start en stopt.</span><span class="sxs-lookup"><span data-stu-id="6c74f-144">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="6c74f-145">Met de eerste opdracht wordt de `Enter-PSSession` cmdlet gebruikt om een interactieve sessie met de Server01-computer te starten.</span><span class="sxs-lookup"><span data-stu-id="6c74f-145">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="6c74f-146">De tweede opdracht gebruikt de `Exit-PSSession` cmdlet om de sessie te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="6c74f-146">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="6c74f-147">U kunt ook het sleutel woord **Exit** gebruiken om de interactieve sessie te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="6c74f-147">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="6c74f-148">`Exit-PSSession` en **Afsluiten** hebben hetzelfde effect.</span><span class="sxs-lookup"><span data-stu-id="6c74f-148">`Exit-PSSession` and **Exit** have the same effect.</span></span>

## <span data-ttu-id="6c74f-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6c74f-149">PARAMETERS</span></span>

### <span data-ttu-id="6c74f-150">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="6c74f-150">-AllowRedirection</span></span>

<span data-ttu-id="6c74f-151">Hiermee kan de verbinding worden omgeleid naar een alternatieve URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="6c74f-151">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="6c74f-152">Omleiding is standaard niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6c74f-152">By default, redirection is not allowed.</span></span>

<span data-ttu-id="6c74f-153">Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="6c74f-153">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="6c74f-154">Standaard worden verbindingen niet door Windows Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding door te sturen.</span><span class="sxs-lookup"><span data-stu-id="6c74f-154">By default, Windows PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="6c74f-155">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="6c74f-155">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="6c74f-156">Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de `$PSSessionOption` Voorkeurs variabele in.</span><span class="sxs-lookup"><span data-stu-id="6c74f-156">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="6c74f-157">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="6c74f-157">The default value is 5.</span></span>

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

### <span data-ttu-id="6c74f-158">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="6c74f-158">-ApplicationName</span></span>

<span data-ttu-id="6c74f-159">Hiermee geeft u het segment van de toepassings naam van de verbindings-URI op.</span><span class="sxs-lookup"><span data-stu-id="6c74f-159">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="6c74f-160">Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de para meter **ConnectionURI** niet gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="6c74f-160">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="6c74f-161">De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-161">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="6c74f-162">Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN.</span><span class="sxs-lookup"><span data-stu-id="6c74f-162">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="6c74f-163">Deze waarde is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="6c74f-163">This value is appropriate for most uses.</span></span> <span data-ttu-id="6c74f-164">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-164">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="6c74f-165">De **WinRM** -service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="6c74f-165">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="6c74f-166">De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-166">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="6c74f-167">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="6c74f-167">-Authentication</span></span>

<span data-ttu-id="6c74f-168">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="6c74f-168">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="6c74f-169">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="6c74f-169">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6c74f-170">Standaard</span><span class="sxs-lookup"><span data-stu-id="6c74f-170">Default</span></span>
- <span data-ttu-id="6c74f-171">Basic</span><span class="sxs-lookup"><span data-stu-id="6c74f-171">Basic</span></span>
- <span data-ttu-id="6c74f-172">CredSSP</span><span class="sxs-lookup"><span data-stu-id="6c74f-172">Credssp</span></span>
- <span data-ttu-id="6c74f-173">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="6c74f-173">Digest</span></span>
- <span data-ttu-id="6c74f-174">Kerberos</span><span class="sxs-lookup"><span data-stu-id="6c74f-174">Kerberos</span></span>
- <span data-ttu-id="6c74f-175">Negotiate</span><span class="sxs-lookup"><span data-stu-id="6c74f-175">Negotiate</span></span>
- <span data-ttu-id="6c74f-176">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="6c74f-176">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="6c74f-177">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="6c74f-177">The default value is Default.</span></span>

<span data-ttu-id="6c74f-178">CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="6c74f-178">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="6c74f-179">Zie [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="6c74f-179">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="6c74f-180">Let op: de verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="6c74f-180">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="6c74f-181">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="6c74f-181">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="6c74f-182">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="6c74f-182">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="6c74f-183">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="6c74f-183">-CertificateThumbprint</span></span>

<span data-ttu-id="6c74f-184">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="6c74f-184">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="6c74f-185">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="6c74f-185">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="6c74f-186">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="6c74f-186">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="6c74f-187">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="6c74f-187">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="6c74f-188">Als u een certificaat wilt ophalen, gebruikt u de `Get-Item` `Get-ChildItem` opdracht of in het Windows Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="6c74f-188">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the Windows PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="6c74f-189">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="6c74f-189">-ComputerName</span></span>

<span data-ttu-id="6c74f-190">Hiermee geeft u een computer naam op.</span><span class="sxs-lookup"><span data-stu-id="6c74f-190">Specifies a computer name.</span></span> <span data-ttu-id="6c74f-191">Met deze cmdlet wordt een interactieve sessie gestart met de opgegeven externe computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-191">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="6c74f-192">Voer slechts één computer naam in.</span><span class="sxs-lookup"><span data-stu-id="6c74f-192">Enter only one computer name.</span></span> <span data-ttu-id="6c74f-193">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-193">The default is the local computer.</span></span>

<span data-ttu-id="6c74f-194">Typ de NetBIOS-naam, het IP-adres of de Fully Qualified Domain Name van de computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-194">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="6c74f-195">U kunt ook een computer naam door geven aan `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6c74f-195">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="6c74f-196">Als u een IP-adres wilt gebruiken in de waarde van de para meter **ComputerName** , moet de opdracht de para meter **Credential** bevatten.</span><span class="sxs-lookup"><span data-stu-id="6c74f-196">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="6c74f-197">De computer moet ook worden geconfigureerd voor HTTPS-Trans Port of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-197">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="6c74f-198">Zie "een computer toevoegen aan de lijst met vertrouwde hosts" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md)voor instructies voor het toevoegen van een computer naam aan de lijst TrustedHosts.</span><span class="sxs-lookup"><span data-stu-id="6c74f-198">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="6c74f-199">Opmerking: in Windows Vista en latere versies van het Windows-besturings systeem moet u Windows Power shell starten met de optie als administrator uitvoeren om de lokale computer op te geven in de waarde van de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="6c74f-199">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start Windows PowerShell with the Run as administrator option.</span></span>

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

### <span data-ttu-id="6c74f-200">-Configuratiepad</span><span class="sxs-lookup"><span data-stu-id="6c74f-200">-ConfigurationName</span></span>

<span data-ttu-id="6c74f-201">Hiermee geeft u de sessie configuratie op die wordt gebruikt voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-201">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="6c74f-202">Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-202">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="6c74f-203">Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="6c74f-203">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="6c74f-204">De sessie configuratie voor een sessie bevindt zich op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-204">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="6c74f-205">Als de opgegeven sessie configuratie niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="6c74f-205">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="6c74f-206">De standaard waarde is de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-206">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="6c74f-207">Als deze voorkeurs variabele niet is ingesteld, is de standaard instelling micro soft. Power shell.</span><span class="sxs-lookup"><span data-stu-id="6c74f-207">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="6c74f-208">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-208">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="6c74f-209">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="6c74f-209">-ConnectionUri</span></span>

<span data-ttu-id="6c74f-210">Hiermee geeft u een URI op die het verbindings eindpunt voor de sessie definieert.</span><span class="sxs-lookup"><span data-stu-id="6c74f-210">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="6c74f-211">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="6c74f-211">The URI must be fully qualified.</span></span> <span data-ttu-id="6c74f-212">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="6c74f-212">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="6c74f-213">De standaard waarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="6c74f-213">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="6c74f-214">Als u geen **ConnectionURI** opgeeft, kunt u de para meters **UseSSL** , **ComputerName** , **Port** en **ApplicationName** gebruiken om de **ConnectionURI** -waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="6c74f-214">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="6c74f-215">Geldige waarden voor het transport segment van de URI zijn HTTP en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c74f-215">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="6c74f-216">Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met behulp van standaard poorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c74f-216">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="6c74f-217">Als u de standaard poorten voor externe communicatie van Windows Power shell wilt gebruiken, geeft u poort 5985 op voor HTTP of 5986 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c74f-217">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="6c74f-218">Als de doel computer de verbinding omleidt naar een andere URI, verhindert Windows Power shell de omleiding tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6c74f-218">If the destination computer redirects the connection to a different URI, Windows PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="6c74f-219">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="6c74f-219">-ContainerId</span></span>

<span data-ttu-id="6c74f-220">Hiermee geeft u de ID van een container op.</span><span class="sxs-lookup"><span data-stu-id="6c74f-220">Specifies the ID of a container.</span></span>

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

### <span data-ttu-id="6c74f-221">-Credential</span><span class="sxs-lookup"><span data-stu-id="6c74f-221">-Credential</span></span>

<span data-ttu-id="6c74f-222">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="6c74f-222">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="6c74f-223">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="6c74f-223">The default is the current user.</span></span>

<span data-ttu-id="6c74f-224">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="6c74f-224">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="6c74f-225">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="6c74f-225">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="6c74f-226">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="6c74f-226">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="6c74f-227">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="6c74f-227">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="6c74f-228">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="6c74f-228">-EnableNetworkAccess</span></span>

<span data-ttu-id="6c74f-229">Geeft aan dat met deze cmdlet een interactief beveiligings token wordt toegevoegd aan loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="6c74f-229">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="6c74f-230">Met het interactieve token kunt u opdrachten uitvoeren in de loop back-sessie die gegevens van andere computers ophalen.</span><span class="sxs-lookup"><span data-stu-id="6c74f-230">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="6c74f-231">U kunt bijvoorbeeld een opdracht uitvoeren in de sessie waarmee XML-bestanden van een externe computer naar de lokale computer worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="6c74f-231">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="6c74f-232">Een loop back-sessie is een **PSSession** die afkomstig is van en eindigt op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-232">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="6c74f-233">Als u een loop back-sessie wilt maken, laat u de para meter **ComputerName** weg of stelt u de waarde in op.</span><span class="sxs-lookup"><span data-stu-id="6c74f-233">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="6c74f-234">(punt), localhost of de naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-234">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="6c74f-235">Loop Back-sessies worden standaard gemaakt met behulp van een netwerk token, wat mogelijk niet voldoende machtigingen biedt om te verifiëren bij externe computers.</span><span class="sxs-lookup"><span data-stu-id="6c74f-235">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="6c74f-236">De para meter **EnableNetworkAccess** is alleen effectief in loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="6c74f-236">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="6c74f-237">Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, mislukt de opdracht, maar wordt de para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="6c74f-237">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="6c74f-238">U kunt externe toegang ook toestaan in een loop back-sessie met behulp van de **CredSSP** -waarde van de **verificatie** parameter, die de sessie referenties delegeert naar andere computers.</span><span class="sxs-lookup"><span data-stu-id="6c74f-238">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="6c74f-239">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6c74f-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6c74f-240">-Id</span><span class="sxs-lookup"><span data-stu-id="6c74f-240">-Id</span></span>

<span data-ttu-id="6c74f-241">Hiermee geeft u de ID op van een bestaande sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-241">Specifies the ID of an existing session.</span></span> <span data-ttu-id="6c74f-242">`Enter-PSSession` maakt gebruik van de opgegeven sessie voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-242">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="6c74f-243">Gebruik de cmdlet om de ID van een sessie te vinden `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6c74f-243">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="6c74f-244">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6c74f-244">-InstanceId</span></span>

<span data-ttu-id="6c74f-245">Hiermee geeft u de exemplaar-ID van een bestaande sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-245">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="6c74f-246">`Enter-PSSession` maakt gebruik van de opgegeven sessie voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-246">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="6c74f-247">De exemplaar-ID is een GUID.</span><span class="sxs-lookup"><span data-stu-id="6c74f-247">The instance ID is a GUID.</span></span> <span data-ttu-id="6c74f-248">Gebruik de cmdlet om de exemplaar-ID van een sessie te vinden `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6c74f-248">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="6c74f-249">U kunt ook de para meters voor de **sessie** , **naam** of **id** gebruiken om een bestaande sessie op te geven.</span><span class="sxs-lookup"><span data-stu-id="6c74f-249">You can also use the **Session** , **Name** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="6c74f-250">U kunt ook de para meter **ComputerName** gebruiken om een tijdelijke sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="6c74f-250">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

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

### <span data-ttu-id="6c74f-251">-Name</span><span class="sxs-lookup"><span data-stu-id="6c74f-251">-Name</span></span>

<span data-ttu-id="6c74f-252">Hiermee geeft u de beschrijvende naam van een bestaande sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-252">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="6c74f-253">`Enter-PSSession` maakt gebruik van de opgegeven sessie voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-253">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="6c74f-254">Als de naam die u opgeeft, overeenkomt met meer dan één sessie, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="6c74f-254">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="6c74f-255">U kunt ook de para meters **Session** , **InstanceId** of **id** gebruiken om een bestaande sessie op te geven.</span><span class="sxs-lookup"><span data-stu-id="6c74f-255">You can also use the **Session** , **InstanceID** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="6c74f-256">U kunt ook de para meter **ComputerName** gebruiken om een tijdelijke sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="6c74f-256">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="6c74f-257">Als u een beschrijvende naam voor een sessie wilt instellen, gebruikt u de para meter **name** van de `New-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6c74f-257">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="6c74f-258">-Port</span><span class="sxs-lookup"><span data-stu-id="6c74f-258">-Port</span></span>

<span data-ttu-id="6c74f-259">Hiermee geeft u de netwerk poort op de externe computer die wordt gebruikt voor deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="6c74f-259">Specifies the network port on the remote computer that is used for this command.</span></span> <span data-ttu-id="6c74f-260">Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6c74f-260">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="6c74f-261">De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c74f-261">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="6c74f-262">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="6c74f-262">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="6c74f-263">Gebruik de volgende opdrachten om de listener te configureren:</span><span class="sxs-lookup"><span data-stu-id="6c74f-263">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="6c74f-264">Gebruik de para meter **poort** alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="6c74f-264">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="6c74f-265">De poort instelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6c74f-265">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="6c74f-266">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="6c74f-266">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6c74f-267">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="6c74f-267">-RunAsAdministrator</span></span>

<span data-ttu-id="6c74f-268">Geeft aan dat de **PSSession** wordt uitgevoerd als beheerder.</span><span class="sxs-lookup"><span data-stu-id="6c74f-268">Indicates that the **PSSession** runs as administrator.</span></span>

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

### <span data-ttu-id="6c74f-269">-Sessie</span><span class="sxs-lookup"><span data-stu-id="6c74f-269">-Session</span></span>

<span data-ttu-id="6c74f-270">Hiermee geeft u een Windows Power shell-sessie ( **PSSession** ) op die moet worden gebruikt voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-270">Specifies a Windows PowerShell session ( **PSSession** ) to use for the interactive session.</span></span> <span data-ttu-id="6c74f-271">Deze para meter gebruikt een sessie object.</span><span class="sxs-lookup"><span data-stu-id="6c74f-271">This parameter takes a session object.</span></span> <span data-ttu-id="6c74f-272">U kunt ook de para meters **name** , **InstanceId** of **id** gebruiken om een **PSSession** op te geven.</span><span class="sxs-lookup"><span data-stu-id="6c74f-272">You can also use the **Name** , **InstanceID** , or **ID** parameters to specify a **PSSession**.</span></span>

<span data-ttu-id="6c74f-273">Voer een variabele in die een sessie object bevat of een opdracht waarmee een sessie object wordt gemaakt of opgehaald, zoals een `New-PSSession` of- `Get-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="6c74f-273">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="6c74f-274">U kunt ook een sessie object door sluizen naar `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6c74f-274">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="6c74f-275">U kunt slechts één **PSSession** verzenden met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="6c74f-275">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="6c74f-276">Als u een variabele opgeeft die meer dan één **PSSession** bevat, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="6c74f-276">If you enter a variable that contains more than one **PSSession** , the command fails.</span></span>

<span data-ttu-id="6c74f-277">Wanneer u `Exit-PSSession` of het sleutel woord **Exit** gebruikt, wordt de interactieve sessie beëindigd, maar de **PSSession** die u hebt gemaakt, blijft open en beschikbaar voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="6c74f-277">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

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

### <span data-ttu-id="6c74f-278">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="6c74f-278">-SessionOption</span></span>

<span data-ttu-id="6c74f-279">Hiermee stelt u geavanceerde opties in voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-279">Sets advanced options for the session.</span></span> <span data-ttu-id="6c74f-280">Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden voor de waarden van de sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-280">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="6c74f-281">De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="6c74f-281">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="6c74f-282">Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-282">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="6c74f-283">De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-283">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="6c74f-284">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-284">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="6c74f-285">Zie voor een beschrijving van de sessie opties, met inbegrip van de standaard waarden `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="6c74f-285">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="6c74f-286">Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](About/about_Preference_Variables.md)variabele.</span><span class="sxs-lookup"><span data-stu-id="6c74f-286">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="6c74f-287">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="6c74f-287">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="6c74f-288">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="6c74f-288">-UseSSL</span></span>

<span data-ttu-id="6c74f-289">Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-289">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="6c74f-290">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6c74f-290">By default, SSL is not used.</span></span>

<span data-ttu-id="6c74f-291">WS-Management versleutelt alle Windows Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="6c74f-291">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="6c74f-292">De para meter **UseSSL** is een extra beveiliging waarmee de gegevens worden verzonden via een HTTPS-verbinding in plaats van via een http-verbinding.</span><span class="sxs-lookup"><span data-stu-id="6c74f-292">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="6c74f-293">Als u deze para meter gebruikt, maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="6c74f-293">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="6c74f-294">-VMId</span><span class="sxs-lookup"><span data-stu-id="6c74f-294">-VMId</span></span>

<span data-ttu-id="6c74f-295">Hiermee geeft u de ID van een virtuele machine op.</span><span class="sxs-lookup"><span data-stu-id="6c74f-295">Specifies the ID of a virtual machine.</span></span>

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

### <span data-ttu-id="6c74f-296">-VMName</span><span class="sxs-lookup"><span data-stu-id="6c74f-296">-VMName</span></span>

<span data-ttu-id="6c74f-297">Hiermee geeft u de naam van een virtuele machine op.</span><span class="sxs-lookup"><span data-stu-id="6c74f-297">Specifies the name of a virtual machine.</span></span>

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

### <span data-ttu-id="6c74f-298">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6c74f-298">CommonParameters</span></span>

<span data-ttu-id="6c74f-299">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6c74f-299">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6c74f-300">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-300">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6c74f-301">INVOER</span><span class="sxs-lookup"><span data-stu-id="6c74f-301">INPUTS</span></span>

### <span data-ttu-id="6c74f-302">System. String, System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="6c74f-302">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="6c74f-303">U kunt een computer naam, als een teken reeks of een sessie object door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6c74f-303">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="6c74f-304">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6c74f-304">OUTPUTS</span></span>

### <span data-ttu-id="6c74f-305">Geen</span><span class="sxs-lookup"><span data-stu-id="6c74f-305">None</span></span>

<span data-ttu-id="6c74f-306">De cmdlet retourneert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-306">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="6c74f-307">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6c74f-307">NOTES</span></span>

<span data-ttu-id="6c74f-308">Als u verbinding wilt maken met een externe computer, moet u lid zijn van de groep Administrators op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="6c74f-308">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="6c74f-309">Als u een interactieve sessie op de lokale computer wilt starten, moet u Power shell starten met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="6c74f-309">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="6c74f-310">Wanneer u gebruikt `Enter-PSSession` , wordt uw gebruikers profiel op de externe computer gebruikt voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-310">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="6c74f-311">De opdrachten in het profiel voor externe gebruikers, met inbegrip van opdrachten voor het toevoegen van Power shell-modules en het wijzigen van de opdracht prompt, uitvoeren voordat de prompt op afstand wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6c74f-311">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="6c74f-312">`Enter-PSSession` maakt gebruik van de GEBRUIKERSINTERFACE cultuur-instelling op de lokale computer voor de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-312">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="6c74f-313">Gebruik de automatische variabele om de lokale GEBRUIKERSINTERFACE cultuur te vinden `$UICulture` .</span><span class="sxs-lookup"><span data-stu-id="6c74f-313">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="6c74f-314">`Enter-PSSession` vereist de `Get-Command` `Out-Default` `Exit-PSSession` cmdlets, en.</span><span class="sxs-lookup"><span data-stu-id="6c74f-314">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="6c74f-315">Als deze cmdlets niet zijn opgenomen in de sessie configuratie op de externe computer, `Enter-PSSession` mislukt de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="6c74f-315">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="6c74f-316">In tegens telling tot `Invoke-Command` , waarbij de opdrachten worden geparseerd en geïnterpreteerd voordat deze naar de externe computer worden verzonden, `Enter-PSSession` verzendt de opdrachten rechtstreeks naar de externe computer zonder interpretatie.</span><span class="sxs-lookup"><span data-stu-id="6c74f-316">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="6c74f-317">Als de sessie die u wilt invoeren, bezig is met het verwerken van een opdracht, kan er een vertraging optreden voordat Power shell reageert op de `Enter-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="6c74f-317">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="6c74f-318">U bent verbonden zodra de sessie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="6c74f-318">You are connected as soon as the session is available.</span></span> <span data-ttu-id="6c74f-319">U annuleert de `Enter-PSSession` opdracht door op <kbd>CTRL</kbd> + <kbd>C</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="6c74f-319">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

## <span data-ttu-id="6c74f-320">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6c74f-320">RELATED LINKS</span></span>

[<span data-ttu-id="6c74f-321">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="6c74f-321">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="6c74f-322">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="6c74f-322">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="6c74f-323">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="6c74f-323">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="6c74f-324">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="6c74f-324">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="6c74f-325">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="6c74f-325">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="6c74f-326">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="6c74f-326">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="6c74f-327">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="6c74f-327">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="6c74f-328">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="6c74f-328">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="6c74f-329">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="6c74f-329">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="6c74f-330">about_Remote</span><span class="sxs-lookup"><span data-stu-id="6c74f-330">about_Remote</span></span>](About/about_Remote.md)
