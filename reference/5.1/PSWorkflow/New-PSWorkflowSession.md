---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowSession
ms.openlocfilehash: 995dd8a6df3ac8ebd7a204d2aefef3fa6aa71e14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250288"
---
# <span data-ttu-id="96ef4-103">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="96ef4-103">New-PSWorkflowSession</span></span>

## <span data-ttu-id="96ef4-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="96ef4-104">SYNOPSIS</span></span>
<span data-ttu-id="96ef4-105">Hiermee maakt u een werk stroom sessie.</span><span class="sxs-lookup"><span data-stu-id="96ef4-105">Creates a workflow session.</span></span>

## <span data-ttu-id="96ef4-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="96ef4-106">SYNTAX</span></span>

```
New-PSWorkflowSession [[-ComputerName] <String[]>] [-Credential <Object>] [-Name <String[]>] [-Port <Int32>]
 [-UseSSL] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-EnableNetworkAccess]
 [<CommonParameters>]
```

## <span data-ttu-id="96ef4-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="96ef4-107">DESCRIPTION</span></span>

<span data-ttu-id="96ef4-108">Met de `New-PSWorkflowSession` cmdlet maakt u een door de gebruiker beheerde sessie ( **PSSession** ) die is bedoeld voor het uitvoeren van Windows Power shell-werk stromen.</span><span class="sxs-lookup"><span data-stu-id="96ef4-108">The `New-PSWorkflowSession` cmdlet creates a user-managed session ( **PSSession** ) that is especially designed for running Windows PowerShell workflows.</span></span> <span data-ttu-id="96ef4-109">Hierbij wordt gebruikgemaakt van de configuratie van de micro soft. Power shell. werk stroom sessie, die scripts bevat, typen en Format teren van bestanden en opties die vereist zijn voor werk stromen.</span><span class="sxs-lookup"><span data-stu-id="96ef4-109">It uses the Microsoft.PowerShell.Workflow session configuration, which includes scripts, type and formatting files, and options that are required for workflows.</span></span>

<span data-ttu-id="96ef4-110">U kunt `New-PSWorkflowSession` de alias gebruiken `nwsn` .</span><span class="sxs-lookup"><span data-stu-id="96ef4-110">You can use `New-PSWorkflowSession` or its alias, `nwsn`.</span></span>

<span data-ttu-id="96ef4-111">U kunt ook algemene werk stroom parameters toevoegen aan deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="96ef4-111">You can also add workflow common parameters to this command.</span></span> <span data-ttu-id="96ef4-112">Zie [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md) voor meer informatie over algemene werk stroom parameters</span><span class="sxs-lookup"><span data-stu-id="96ef4-112">For more information about workflow common parameters, see [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)</span></span>

<span data-ttu-id="96ef4-113">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="96ef4-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="96ef4-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="96ef4-114">EXAMPLES</span></span>

### <span data-ttu-id="96ef4-115">Voor beeld 1: een werk stroom sessie op een externe computer maken</span><span class="sxs-lookup"><span data-stu-id="96ef4-115">Example 1: Create a workflow session on a remote computer</span></span>

<span data-ttu-id="96ef4-116">In dit voor beeld wordt de **WorkflowTests** -sessie gemaakt op de externe computer met ServerNode01.</span><span class="sxs-lookup"><span data-stu-id="96ef4-116">This example creates the **WorkflowTests** session on the ServerNode01 remote computer.</span></span>

```powershell
$params = @{
    ComputerName = "ServerNode01"
    Name = "WorkflowTests"
    SessionOption = (New-PSSessionOption -OutputBufferingMode Drop)
}
New-PSWorkflowSession @params
```

<span data-ttu-id="96ef4-117">De waarde van de para meter **SessionOption** is een `New-PSSessionOption` opdracht waarmee de uitvoer buffer modus in de te **verwijderen** sessie wordt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="96ef4-117">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that sets the output buffering mode in the session to **Drop**.</span></span>

### <span data-ttu-id="96ef4-118">Voor beeld 2: werk stroom sessies op meerdere externe computers maken</span><span class="sxs-lookup"><span data-stu-id="96ef4-118">Example 2: Create workflow sessions on multiple remote computers</span></span>

<span data-ttu-id="96ef4-119">In dit voor beeld worden werk stroom sessies op de ServerNode01-en Server12-computers gemaakt.</span><span class="sxs-lookup"><span data-stu-id="96ef4-119">This example creates workflow sessions on the ServerNode01 and Server12 computers.</span></span> <span data-ttu-id="96ef4-120">De opdracht gebruikt de para meter **Credential** om uit te voeren met de machtigingen van de domein beheerder.</span><span class="sxs-lookup"><span data-stu-id="96ef4-120">The command uses the **Credential** parameter to run with the permissions of the domain administrator.</span></span>

```powershell
"ServerNode01", "Server12" |
    New-PSWorkflowSession -Name WorkflowSession -Credential Domain01\Admin01 -ThrottleLimit 150
```

<span data-ttu-id="96ef4-121">De opdracht gebruikt de para meter **ThrottleLimit** om de beperking per opdracht te verhogen tot 150.</span><span class="sxs-lookup"><span data-stu-id="96ef4-121">The command uses the **ThrottleLimit** parameter to increase the per-command throttle limit to 150.</span></span>
<span data-ttu-id="96ef4-122">Deze waarde heeft voor rang op de standaard beperkings limiet van 100 die is ingesteld in de **micro soft. Power shell. workflow** -sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="96ef4-122">This value takes precedence over the default throttle limit of 100 that is set in the **Microsoft.PowerShell.Workflow** session configuration.</span></span>

## <span data-ttu-id="96ef4-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="96ef4-123">PARAMETERS</span></span>

### <span data-ttu-id="96ef4-124">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="96ef4-124">-ApplicationName</span></span>

<span data-ttu-id="96ef4-125">Hiermee geeft u het segment van de toepassings naam van de verbindings-URI op.</span><span class="sxs-lookup"><span data-stu-id="96ef4-125">Specifies the application name segment of the connection URI.</span></span>

<span data-ttu-id="96ef4-126">De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="96ef4-126">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="96ef4-127">Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN.</span><span class="sxs-lookup"><span data-stu-id="96ef4-127">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="96ef4-128">Deze waarde is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="96ef4-128">This value is appropriate for most uses.</span></span> <span data-ttu-id="96ef4-129">Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="96ef4-129">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="96ef4-130">De WinRM-service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="96ef4-130">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="96ef4-131">De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="96ef4-131">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="96ef4-132">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="96ef4-132">-Authentication</span></span>

<span data-ttu-id="96ef4-133">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="96ef4-133">Specifies the mechanism that is used to authenticate the user credentials.</span></span>
<span data-ttu-id="96ef4-134">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="96ef4-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="96ef4-135">Standaard</span><span class="sxs-lookup"><span data-stu-id="96ef4-135">Default</span></span>
- <span data-ttu-id="96ef4-136">Basic</span><span class="sxs-lookup"><span data-stu-id="96ef4-136">Basic</span></span>
- <span data-ttu-id="96ef4-137">CredSSP</span><span class="sxs-lookup"><span data-stu-id="96ef4-137">Credssp</span></span>
- <span data-ttu-id="96ef4-138">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="96ef4-138">Digest</span></span>
- <span data-ttu-id="96ef4-139">Kerberos</span><span class="sxs-lookup"><span data-stu-id="96ef4-139">Kerberos</span></span>
- <span data-ttu-id="96ef4-140">Negotiate</span><span class="sxs-lookup"><span data-stu-id="96ef4-140">Negotiate</span></span>
- <span data-ttu-id="96ef4-141">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="96ef4-141">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="96ef4-142">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="96ef4-142">The default value is Default.</span></span>

<span data-ttu-id="96ef4-143">CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="96ef4-143">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="96ef4-144">Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="96ef4-144">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="96ef4-145">CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="96ef4-145">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="96ef4-146">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="96ef4-146">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="96ef4-147">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="96ef4-147">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96ef4-148">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="96ef4-148">-CertificateThumbprint</span></span>

<span data-ttu-id="96ef4-149">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="96ef4-149">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="96ef4-150">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="96ef4-150">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="96ef4-151">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="96ef4-151">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="96ef4-152">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="96ef4-152">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="96ef4-153">Als u een certificaat vingerafdruk wilt ophalen, gebruikt u de `Get-Item` cmdlet of de `Get-ChildItem` cmdlet in het Windows Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="96ef4-153">To get a certificate thumbprint, use the `Get-Item` cmdlet or the `Get-ChildItem` cmdlet in the Windows PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96ef4-154">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="96ef4-154">-ComputerName</span></span>

<span data-ttu-id="96ef4-155">Hiermee maakt u een permanente verbinding ( **PSSession** ) met de opgegeven computer.</span><span class="sxs-lookup"><span data-stu-id="96ef4-155">Creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="96ef4-156">Als u meerdere computer namen opgeeft, maakt Windows Power shell meerdere **PSSessions** , één voor elke computer.</span><span class="sxs-lookup"><span data-stu-id="96ef4-156">If you enter multiple computer names, Windows PowerShell creates multiple **PSSessions** , one for each computer.</span></span> <span data-ttu-id="96ef4-157">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="96ef4-157">The default is the local computer.</span></span>

<span data-ttu-id="96ef4-158">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="96ef4-158">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="96ef4-159">Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="96ef4-159">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="96ef4-160">Wanneer de computer zich in een ander domein bevindt dan de gebruiker, is de Fully Qualified Domain Name vereist.</span><span class="sxs-lookup"><span data-stu-id="96ef4-160">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="96ef4-161">U kunt ook een computer naam door geven tussen aanhalings tekens naar `New-PSWorkflowSession` .</span><span class="sxs-lookup"><span data-stu-id="96ef4-161">You can also pipe a computer name, in quotation marks to `New-PSWorkflowSession`.</span></span>

<span data-ttu-id="96ef4-162">Als u een IP-adres wilt gebruiken in de waarde van de para meter **ComputerName** , moet de opdracht de para meter **Credential** bevatten.</span><span class="sxs-lookup"><span data-stu-id="96ef4-162">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="96ef4-163">De computer moet ook worden geconfigureerd voor HTTPS-Trans Port of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="96ef4-163">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="96ef4-164">Zie "een computer toevoegen aan de lijst met vertrouwde hosts" in [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)voor instructies voor het toevoegen van een computer naam aan de lijst TrustedHosts.</span><span class="sxs-lookup"><span data-stu-id="96ef4-164">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="96ef4-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="96ef4-165">-Credential</span></span>

<span data-ttu-id="96ef4-166">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="96ef4-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="96ef4-167">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="96ef4-167">The default is the current user.</span></span> <span data-ttu-id="96ef4-168">Typ een gebruikers naam, zoals gebruiker01, Domain01\User01 of User@Domain.com , of voer een **PSCredential** -object in, zoals het item dat door de `Get-Credential` cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="96ef4-168">Type a user name, such as User01, Domain01\User01, or User@Domain.com, or enter a **PSCredential** object, such as one returned by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="96ef4-169">Wanneer u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="96ef4-169">When you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="96ef4-170">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="96ef4-170">-EnableNetworkAccess</span></span>

<span data-ttu-id="96ef4-171">Geeft aan dat met deze cmdlet een interactief beveiligings token wordt toegevoegd aan loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="96ef4-171">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="96ef4-172">Met het interactieve token kunt u opdrachten uitvoeren in de loop back-sessie die gegevens van andere computers ophalen.</span><span class="sxs-lookup"><span data-stu-id="96ef4-172">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="96ef4-173">U kunt bijvoorbeeld een opdracht uitvoeren in de sessie waarmee XML-bestanden van een externe computer naar de lokale computer worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="96ef4-173">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="96ef4-174">Een loop back-sessie is een **PSSession** die afkomstig is van en eindigt op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="96ef4-174">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="96ef4-175">Als u een loop back-sessie wilt maken, geeft u de para meter **ComputerName** niet op of stelt u de waarde in op punt, localhost of de naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="96ef4-175">To create a loopback session, do not specify the **ComputerName** parameter or set its value to dot, localhost, or the name of the local computer.</span></span>

<span data-ttu-id="96ef4-176">Loop Back-sessies worden standaard gemaakt met een netwerk token, wat mogelijk niet voldoende machtigingen biedt om te verifiëren bij externe computers.</span><span class="sxs-lookup"><span data-stu-id="96ef4-176">By default, loopback sessions are created that have a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="96ef4-177">De para meter **EnableNetworkAccess** is alleen effectief in loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="96ef4-177">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="96ef4-178">Als u de para meter **EnableNetworkAccess** opgeeft wanneer u een sessie op een externe computer maakt, mislukt de opdracht, maar wordt de para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="96ef4-178">If you specify the **EnableNetworkAccess** parameter when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="96ef4-179">U kunt externe toegang ook toestaan in een loop back-sessie met behulp van de **CredSSP** -waarde van de **verificatie** parameter, die de sessie referenties delegeert naar andere computers.</span><span class="sxs-lookup"><span data-stu-id="96ef4-179">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="96ef4-180">Om de computer te beschermen tegen kwaad aardige toegang, niet-verbonden loop Back-sessies met interactieve tokens, die zijn gemaakt met behulp van de para meter **EnableNetworkAccess** , kunnen alleen opnieuw worden verbonden vanaf de computer waarop de sessie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="96ef4-180">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="96ef4-181">Verbroken sessies die gebruikmaken van CredSSP-verificatie, kunnen opnieuw worden aangesloten op andere computers.</span><span class="sxs-lookup"><span data-stu-id="96ef4-181">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="96ef4-182">Zie de cmdlet voor meer informatie `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="96ef4-182">For more information, see the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="96ef4-183">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="96ef4-183">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96ef4-184">-Name</span><span class="sxs-lookup"><span data-stu-id="96ef4-184">-Name</span></span>

<span data-ttu-id="96ef4-185">Hiermee geeft u een beschrijvende naam op voor de werk stroom sessie.</span><span class="sxs-lookup"><span data-stu-id="96ef4-185">Specifies a friendly name for the workflow session.</span></span> <span data-ttu-id="96ef4-186">U kunt de naam gebruiken met andere cmdlets, zoals `Get-PSSession` en `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="96ef4-186">You can use the name with other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="96ef4-187">De naam hoeft niet uniek te zijn voor de computer of de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="96ef4-187">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Session#
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96ef4-188">-Port</span><span class="sxs-lookup"><span data-stu-id="96ef4-188">-Port</span></span>

<span data-ttu-id="96ef4-189">Hiermee geeft u de netwerk poort op de externe computer op die voor deze verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="96ef4-189">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="96ef4-190">Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="96ef4-190">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="96ef4-191">De standaard poorten zijn 5985 (WinRM-poort voor HTTP) en 5986 (WinRM-poort voor HTTPS).</span><span class="sxs-lookup"><span data-stu-id="96ef4-191">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="96ef4-192">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="96ef4-192">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="96ef4-193">Gebruik de volgende opdrachten om de listener te configureren:</span><span class="sxs-lookup"><span data-stu-id="96ef4-193">Use the following commands to configure the listener:</span></span>

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="96ef4-194">Gebruik de para meter **poort** alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="96ef4-194">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="96ef4-195">De poort instelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="96ef4-195">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="96ef4-196">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="96ef4-196">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96ef4-197">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="96ef4-197">-SessionOption</span></span>

<span data-ttu-id="96ef4-198">Hiermee geeft u geavanceerde opties voor de sessie op.</span><span class="sxs-lookup"><span data-stu-id="96ef4-198">Specifies advanced options for the session.</span></span> <span data-ttu-id="96ef4-199">Voer een **SessionOption** -object in, zoals een, dat u maakt met behulp van de- `New-PSSessionOption` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="96ef4-199">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet.</span></span>

<span data-ttu-id="96ef4-200">De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="96ef4-200">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="96ef4-201">Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="96ef4-201">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="96ef4-202">De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="96ef4-202">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="96ef4-203">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="96ef4-203">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="96ef4-204">Zie [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="96ef4-204">For more information about session configurations, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="96ef4-205">Zie voor een beschrijving van de sessie opties, met inbegrip van de standaard waarden `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="96ef4-205">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="96ef4-206">Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)variabele.</span><span class="sxs-lookup"><span data-stu-id="96ef4-206">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96ef4-207">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="96ef4-207">-ThrottleLimit</span></span>

<span data-ttu-id="96ef4-208">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="96ef4-208">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="96ef4-209">Als u deze para meter weglaat of een waarde van 0 (nul) opgeeft, wordt de standaard waarde voor de **micro soft. PowerShellWorkflow** -sessie configuratie, 100, gebruikt.</span><span class="sxs-lookup"><span data-stu-id="96ef4-209">If you omit this parameter or enter a value of 0 (zero), the default value for the **Microsoft.PowerShellWorkflow** session configuration, 100, is used.</span></span>

<span data-ttu-id="96ef4-210">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="96ef4-210">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96ef4-211">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="96ef4-211">-UseSSL</span></span>

<span data-ttu-id="96ef4-212">Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="96ef4-212">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="96ef4-213">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="96ef4-213">By default, SSL is not used.</span></span>

<span data-ttu-id="96ef4-214">WS-Management versleutelt alle Windows Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="96ef4-214">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="96ef4-215">De para meter **UseSSL** is een extra beveiliging waarmee de gegevens worden verzonden via een HTTPS-verbinding in plaats van via een http-verbinding.</span><span class="sxs-lookup"><span data-stu-id="96ef4-215">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="96ef4-216">Als u deze para meter opgeeft, maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="96ef4-216">If you specify this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96ef4-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="96ef4-217">CommonParameters</span></span>

<span data-ttu-id="96ef4-218">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="96ef4-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="96ef4-219">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="96ef4-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="96ef4-220">INVOER</span><span class="sxs-lookup"><span data-stu-id="96ef4-220">INPUTS</span></span>

### <span data-ttu-id="96ef4-221">System. Management. Automation. Runspaces. PSSession [], System. String</span><span class="sxs-lookup"><span data-stu-id="96ef4-221">System.Management.Automation.Runspaces.PSSession[], System.String</span></span>

<span data-ttu-id="96ef4-222">U kunt een sessie of een computer naam door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="96ef4-222">You can pipe a session or a computer name to this cmdlet.</span></span>

## <span data-ttu-id="96ef4-223">UITVOER</span><span class="sxs-lookup"><span data-stu-id="96ef4-223">OUTPUTS</span></span>

### <span data-ttu-id="96ef4-224">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="96ef4-224">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="96ef4-225">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="96ef4-225">NOTES</span></span>

<span data-ttu-id="96ef4-226">Een `New-PSWorkflowSession` opdracht is gelijk aan de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="96ef4-226">A `New-PSWorkflowSession` command is equivalent to the following command:</span></span>

`New-PSSession -ConfigurationName Microsoft.PowerShell.Workflow`

## <span data-ttu-id="96ef4-227">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="96ef4-227">RELATED LINKS</span></span>

[<span data-ttu-id="96ef4-228">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="96ef4-228">Disconnect-PSSession</span></span>](../Microsoft.PowerShell.Core/Disconnect-PSSession.md)

[<span data-ttu-id="96ef4-229">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="96ef4-229">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="96ef4-230">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="96ef4-230">New-PSTransportOption</span></span>](../Microsoft.PowerShell.Core/New-PSTransportOption.md)

[<span data-ttu-id="96ef4-231">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="96ef4-231">Register-PSSessionConfiguration</span></span>](../Microsoft.PowerShell.Core/Register-PSSessionConfiguration.md)

[<span data-ttu-id="96ef4-232">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="96ef4-232">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="96ef4-233">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="96ef4-233">about_Session_Configurations</span></span>](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)

[<span data-ttu-id="96ef4-234">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="96ef4-234">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="96ef4-235">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="96ef4-235">about_WorkflowCommonParameters</span></span>](About/about_WorkflowCommonParameters.md)
