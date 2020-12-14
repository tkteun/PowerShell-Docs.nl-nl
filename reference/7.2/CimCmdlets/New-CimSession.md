---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSession
ms.openlocfilehash: 59e70f75ac9d822db00419d84055d92a3882c11d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705401"
---
# <span data-ttu-id="79fec-102">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="79fec-102">New-CimSession</span></span>

## <span data-ttu-id="79fec-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="79fec-103">SYNOPSIS</span></span>

<span data-ttu-id="79fec-104">Hiermee maakt u een CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="79fec-104">Creates a CIM session.</span></span>

## <span data-ttu-id="79fec-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="79fec-105">SYNTAX</span></span>

### <span data-ttu-id="79fec-106">CredentialParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="79fec-106">CredentialParameterSet (Default)</span></span>

```
New-CimSession [-Authentication <PasswordAuthenticationMechanism>] [[-Credential] <PSCredential>]
 [[-ComputerName] <String[]>] [-Name <String>] [-OperationTimeoutSec <UInt32>] [-SkipTestConnection]
 [-Port <UInt32>] [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

### <span data-ttu-id="79fec-107">CertificateParameterSet</span><span class="sxs-lookup"><span data-stu-id="79fec-107">CertificateParameterSet</span></span>

```
New-CimSession [-CertificateThumbprint <String>] [[-ComputerName] <String[]>] [-Name <String>]
 [-OperationTimeoutSec <UInt32>] [-SkipTestConnection] [-Port <UInt32>]
 [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

## <span data-ttu-id="79fec-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="79fec-108">DESCRIPTION</span></span>

<span data-ttu-id="79fec-109">Met de `New-CimSession` cmdlet wordt een CIM-sessie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="79fec-109">The `New-CimSession` cmdlet creates a CIM session.</span></span> <span data-ttu-id="79fec-110">Een CIM-sessie is een client-side-object dat een verbinding met een lokale computer of een externe computer vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="79fec-110">A CIM session is a client-side object representing a connection to a local computer or a remote computer.</span></span> <span data-ttu-id="79fec-111">De CIM-sessie bevat informatie over de verbinding, zoals **ComputerName**, het gebruikte protocol of verschillende id's.</span><span class="sxs-lookup"><span data-stu-id="79fec-111">The CIM session contains information about the connection, such as **ComputerName**, the protocol used, or various identifiers.</span></span>

<span data-ttu-id="79fec-112">Met deze cmdlet wordt een CIM-sessie object geretourneerd dat kan worden gebruikt door alle andere CIM-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="79fec-112">This cmdlet returns a CIM session object that can be used by all other CIM cmdlets.</span></span>

## <span data-ttu-id="79fec-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="79fec-113">EXAMPLES</span></span>

### <span data-ttu-id="79fec-114">Voor beeld 1: een CIM-sessie met standaard opties maken</span><span class="sxs-lookup"><span data-stu-id="79fec-114">Example 1: Create a CIM session with default options</span></span>

<span data-ttu-id="79fec-115">In dit voor beeld wordt een lokale CIM-sessie met standaard opties gemaakt.</span><span class="sxs-lookup"><span data-stu-id="79fec-115">This example creates a local CIM session with default options.</span></span> <span data-ttu-id="79fec-116">Als **ComputerName** niet is opgegeven, `New-CimSession` maakt een DCOM-sessie naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="79fec-116">If **ComputerName** is not specified, `New-CimSession` creates a DCOM session to the local computer.</span></span>

```powershell
New-CimSession
```

### <span data-ttu-id="79fec-117">Voor beeld 2: een CIM-sessie maken op een specifieke computer</span><span class="sxs-lookup"><span data-stu-id="79fec-117">Example 2: Create a CIM session to a specific computer</span></span>

<span data-ttu-id="79fec-118">In dit voor beeld wordt een CIM-sessie gemaakt met de computer die is opgegeven door **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="79fec-118">This example creates a CIM session to the computer specified by **ComputerName**.</span></span>
<span data-ttu-id="79fec-119">`New-CimSession`Maakt standaard een WSMan-sessie wanneer **ComputerName** wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="79fec-119">By default, `New-CimSession` creates a WSMan session when **ComputerName** is specified.</span></span>

```powershell
New-CimSession -ComputerName Server01
```

### <span data-ttu-id="79fec-120">Voor beeld 3: een CIM-sessie maken op meerdere computers</span><span class="sxs-lookup"><span data-stu-id="79fec-120">Example 3: Create a CIM session to multiple computers</span></span>

<span data-ttu-id="79fec-121">In dit voor beeld wordt een CIM-sessie gemaakt voor alle computers die zijn opgegeven door **ComputerName**, in de door komma's gescheiden lijst.</span><span class="sxs-lookup"><span data-stu-id="79fec-121">This example creates a CIM session to each of the computers specified by **ComputerName**, in the comma separated list.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02,Server03
```

### <span data-ttu-id="79fec-122">Voor beeld 4: een CIM-sessie met een beschrijvende naam maken</span><span class="sxs-lookup"><span data-stu-id="79fec-122">Example 4: Create a CIM session with a friendly name</span></span>

<span data-ttu-id="79fec-123">In dit voor beeld wordt een externe CIM-sessie gemaakt op alle computers die zijn opgegeven door **ComputerName**, in de door komma's gescheiden lijst en wordt een beschrijvende naam toegewezen aan de nieuwe sessies door een **naam** op te geven.</span><span class="sxs-lookup"><span data-stu-id="79fec-123">This example creates a remote CIM session to each of the computers specified by **ComputerName**, in the comma separated list, and assigns a friendly name to the new sessions, by specifying **Name**.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02 -Name FileServers
Get-CimSession -Name File*
```

<span data-ttu-id="79fec-124">U kunt de beschrijvende naam van een CIM-sessie gebruiken om te verwijzen naar de sessie in andere CIM-cmdlets, bijvoorbeeld [Get-CimSession](Get-CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="79fec-124">You can use the friendly name of a CIM session to refer to the session in other CIM cmdlets, for example, [Get-CimSession](Get-CimSession.md).</span></span>

### <span data-ttu-id="79fec-125">Voor beeld 5: een CIM-sessie maken op een computer met behulp van een PSCredential-object</span><span class="sxs-lookup"><span data-stu-id="79fec-125">Example 5: Create a CIM session to a computer using a PSCredential object</span></span>

<span data-ttu-id="79fec-126">In dit voor beeld wordt een CIM-sessie gemaakt met de computer die is opgegeven door **ComputerName**, met behulp van het **PSCredential** -object dat is opgegeven door **Credential** en het verificatie type dat wordt opgegeven door de **verificatie**.</span><span class="sxs-lookup"><span data-stu-id="79fec-126">This example creates a CIM session to the computer specified by **ComputerName**, using the **PSCredential** object specified by **Credential**, and the authentication type specified by **Authentication**.</span></span>

```powershell
New-CimSession -ComputerName Server01 -Credential $cred -Authentication Negotiate
```

<span data-ttu-id="79fec-127">U kunt een **PSCredential** -object maken met behulp van de- [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="79fec-127">You can create a **PSCredential** object using the [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.</span></span>

### <span data-ttu-id="79fec-128">Voor beeld 6: een CIM-sessie maken op een computer met behulp van een specifieke poort</span><span class="sxs-lookup"><span data-stu-id="79fec-128">Example 6: Create a CIM session to a computer using a specific port</span></span>

<span data-ttu-id="79fec-129">In dit voor beeld wordt een CIM-sessie gemaakt met de computer die is opgegeven door **computer naam** met behulp van de TCP-poort die is opgegeven door **poort**.</span><span class="sxs-lookup"><span data-stu-id="79fec-129">This example creates a CIM session to the computer specified by **ComputerName** using the TCP port specified by **Port**.</span></span>

```powershell
New-CimSession -ComputerName Server01 -Port 1234
```

### <span data-ttu-id="79fec-130">Voor beeld 7: een CIM-sessie maken met DCOM</span><span class="sxs-lookup"><span data-stu-id="79fec-130">Example 7: Create a CIM session using DCOM</span></span>

<span data-ttu-id="79fec-131">In dit voor beeld wordt een CIM-sessie gemaakt met behulp van het gedistribueerde COM-Protocol (DCOM) in plaats van WSMan.</span><span class="sxs-lookup"><span data-stu-id="79fec-131">This example creates a CIM session using the Distributed COM (DCOM) protocol instead of WSMan.</span></span>

```powershell
$SessionOption = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server1 -SessionOption $SessionOption
```

## <span data-ttu-id="79fec-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="79fec-132">PARAMETERS</span></span>

### <span data-ttu-id="79fec-133">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="79fec-133">-Authentication</span></span>

<span data-ttu-id="79fec-134">Hiermee geeft u het verificatie type op dat wordt gebruikt voor de referenties van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="79fec-134">Specifies the authentication type used for the user's credentials.</span></span> <span data-ttu-id="79fec-135">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="79fec-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="79fec-136">Standaard</span><span class="sxs-lookup"><span data-stu-id="79fec-136">Default</span></span>
- <span data-ttu-id="79fec-137">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="79fec-137">Digest</span></span>
- <span data-ttu-id="79fec-138">Negotiate</span><span class="sxs-lookup"><span data-stu-id="79fec-138">Negotiate</span></span>
- <span data-ttu-id="79fec-139">Basic</span><span class="sxs-lookup"><span data-stu-id="79fec-139">Basic</span></span>
- <span data-ttu-id="79fec-140">Kerberos</span><span class="sxs-lookup"><span data-stu-id="79fec-140">Kerberos</span></span>
- <span data-ttu-id="79fec-141">NtlmDomain</span><span class="sxs-lookup"><span data-stu-id="79fec-141">NtlmDomain</span></span>
- <span data-ttu-id="79fec-142">CredSsp</span><span class="sxs-lookup"><span data-stu-id="79fec-142">CredSsp</span></span>

<span data-ttu-id="79fec-143">U kunt het verificatie type **NtlmDomain** niet gebruiken voor verbinding met de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="79fec-143">You cannot use the **NtlmDomain** authentication type for connection to the local computer.</span></span> <span data-ttu-id="79fec-144">**CredSSP** -verificatie is alleen beschikbaar in Windows Vista, windows server 2008 en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="79fec-144">**CredSSP** authentication is available only in Windows Vista, Windows Server 2008, and later versions of Windows.</span></span>

> [!CAUTION]
> <span data-ttu-id="79fec-145">CredSSP-verificatie (Credential Security service provider) is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="79fec-145">Credential Security Service Provider (CredSSP) authentication is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="79fec-146">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="79fec-146">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="79fec-147">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="79fec-147">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: CredentialParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="79fec-148">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="79fec-148">-CertificateThumbprint</span></span>

<span data-ttu-id="79fec-149">Hiermee geeft u het digitale open bare-sleutel certificaat (X. 509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="79fec-149">Specifies the digital public key certificate (X.509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="79fec-150">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="79fec-150">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="79fec-151">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="79fec-151">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="79fec-152">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="79fec-152">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="79fec-153">Gebruik de [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) cmdlets in de Power shell-certificaat provider om een certificaat vingerafdruk te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="79fec-153">To get a certificate thumbprint, use the [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) or [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) cmdlets in the PowerShell Certificate Provider.</span></span>

<span data-ttu-id="79fec-154">Zie [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="79fec-154">For more information, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

```yaml
Type: System.String
Parameter Sets: CertificateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="79fec-155">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="79fec-155">-ComputerName</span></span>

<span data-ttu-id="79fec-156">Hiermee geeft u de naam op van de computer waarop u de CIM-sessie wilt maken.</span><span class="sxs-lookup"><span data-stu-id="79fec-156">Specifies the name of the computer to which to create the CIM session.</span></span> <span data-ttu-id="79fec-157">Geef een naam op voor één computer of meerdere computer namen gescheiden door een komma.</span><span class="sxs-lookup"><span data-stu-id="79fec-157">Specify either a single computer name, or multiple computer names separated by a comma.</span></span>

<span data-ttu-id="79fec-158">Als **ComputerName** niet is opgegeven, wordt er een CIM-sessie naar de lokale computer gemaakt.</span><span class="sxs-lookup"><span data-stu-id="79fec-158">If **ComputerName** is not specified, a CIM session to the local computer is created.</span></span> <span data-ttu-id="79fec-159">U kunt de waarde voor computer naam opgeven in een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="79fec-159">You can specify the value for computer name in one of the following formats:</span></span>

- <span data-ttu-id="79fec-160">Een of meer NetBIOS-namen</span><span class="sxs-lookup"><span data-stu-id="79fec-160">One or more NetBIOS names</span></span>
- <span data-ttu-id="79fec-161">Een of meer IP-adressen</span><span class="sxs-lookup"><span data-stu-id="79fec-161">One or more IP addresses</span></span>
- <span data-ttu-id="79fec-162">Een of meer volledig gekwalificeerde domein namen.</span><span class="sxs-lookup"><span data-stu-id="79fec-162">One or more fully qualified domain names.</span></span>

<span data-ttu-id="79fec-163">Als de computer zich in een ander domein bevindt dan de gebruiker, moet u de Fully Qualified Domain Name opgeven.</span><span class="sxs-lookup"><span data-stu-id="79fec-163">If the computer is in a different domain than the user, you must specify the fully qualified domain name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="79fec-164">-Credential</span><span class="sxs-lookup"><span data-stu-id="79fec-164">-Credential</span></span>

<span data-ttu-id="79fec-165">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="79fec-165">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="79fec-166">Als er geen **referentie** is opgegeven, wordt het huidige gebruikers account gebruikt.</span><span class="sxs-lookup"><span data-stu-id="79fec-166">If **Credential** is not specified, the current user account is used.</span></span>

<span data-ttu-id="79fec-167">Geef de waarde voor **referenties** op met behulp van een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="79fec-167">Specify the value for **Credential** using one of the following formats:</span></span>

- <span data-ttu-id="79fec-168">Een gebruikers naam: ' gebruiker01 '</span><span class="sxs-lookup"><span data-stu-id="79fec-168">A user name: "User01"</span></span>
- <span data-ttu-id="79fec-169">Een domein naam en een gebruikers naam: ' Domain01\User01 '</span><span class="sxs-lookup"><span data-stu-id="79fec-169">A domain name and a user name: "Domain01\User01"</span></span>
- <span data-ttu-id="79fec-170">Een user principal name: User@Domain.com</span><span class="sxs-lookup"><span data-stu-id="79fec-170">A user principal name: "User@Domain.com"</span></span>
- <span data-ttu-id="79fec-171">Een PSCredential-object, zoals het dat door de [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="79fec-171">A PSCredential object, such as one returned by the [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.</span></span>

<span data-ttu-id="79fec-172">Wanneer u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="79fec-172">When you type a user name, you are prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialParameterSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fec-173">-Name</span><span class="sxs-lookup"><span data-stu-id="79fec-173">-Name</span></span>

<span data-ttu-id="79fec-174">Hiermee geeft u een beschrijvende naam op voor de CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="79fec-174">Specifies a friendly name for the CIM session.</span></span>

<span data-ttu-id="79fec-175">U kunt de naam gebruiken om te verwijzen naar de CIM-sessie wanneer u andere cmdlets gebruikt, zoals de cmdlet [Get-CimSession](Get-CimSession.md) .</span><span class="sxs-lookup"><span data-stu-id="79fec-175">You can use the name to refer to the CIM session when using other cmdlets, such as the [Get-CimSession](Get-CimSession.md) cmdlet.</span></span>
<span data-ttu-id="79fec-176">De naam hoeft niet uniek te zijn voor de computer of de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="79fec-176">The name is not required to be unique to the computer or the current session.</span></span>

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

### <span data-ttu-id="79fec-177">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="79fec-177">-OperationTimeoutSec</span></span>

<span data-ttu-id="79fec-178">De duur waarvoor de cmdlet wacht op een reactie van de server.</span><span class="sxs-lookup"><span data-stu-id="79fec-178">Duration for which the cmdlet waits for a response from the server.</span></span>

<span data-ttu-id="79fec-179">Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.</span><span class="sxs-lookup"><span data-stu-id="79fec-179">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="79fec-180">Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.</span><span class="sxs-lookup"><span data-stu-id="79fec-180">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="79fec-181">-Port</span><span class="sxs-lookup"><span data-stu-id="79fec-181">-Port</span></span>

<span data-ttu-id="79fec-182">Hiermee geeft u de netwerk poort op de externe computer op die voor deze verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="79fec-182">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="79fec-183">Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="79fec-183">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="79fec-184">De standaard poorten zijn 5985 (de WinRM-poort voor HTTP) en 5986 (de WinRM-poort voor HTTPS).</span><span class="sxs-lookup"><span data-stu-id="79fec-184">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span>

<span data-ttu-id="79fec-185">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="79fec-185">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="79fec-186">Gebruik de volgende opdrachten om de listener te configureren:</span><span class="sxs-lookup"><span data-stu-id="79fec-186">Use the following commands to configure the listener:</span></span>

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number>"}`

<span data-ttu-id="79fec-187">Gebruik de para meter **poort** alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="79fec-187">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="79fec-188">De poort instelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="79fec-188">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="79fec-189">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="79fec-189">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="79fec-190">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="79fec-190">-SessionOption</span></span>

<span data-ttu-id="79fec-191">Hiermee stelt u geavanceerde opties in voor de nieuwe CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="79fec-191">Sets advanced options for the new CIM session.</span></span> <span data-ttu-id="79fec-192">Voer de naam in van een **CimSessionOption** -object dat is gemaakt met de [`New-CimSessionOption`](New-CimSessionOption.md) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="79fec-192">Enter the name of a **CimSessionOption** object created using the [`New-CimSessionOption`](New-CimSessionOption.md) cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.CimSessionOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="79fec-193">-SkipTestConnection</span><span class="sxs-lookup"><span data-stu-id="79fec-193">-SkipTestConnection</span></span>

<span data-ttu-id="79fec-194">De cmdlet maakt standaard `New-CimSession` een verbinding met een extern WS-Management-eind punt om twee redenen: om te controleren of de externe server luistert naar het poort nummer dat is opgegeven met de para meter **poort** en om de opgegeven account referenties te controleren.</span><span class="sxs-lookup"><span data-stu-id="79fec-194">By default, the `New-CimSession` cmdlet establishes a connection with a remote WS-Management endpoint for two reasons: to verify that the remote server is listening on the port number that is specified using the **Port** parameter, and to verify the specified account credentials.</span></span> <span data-ttu-id="79fec-195">De verificatie wordt uitgevoerd met behulp van een standaard WS-Identity bewerking.</span><span class="sxs-lookup"><span data-stu-id="79fec-195">The verification is accomplished using a standard WS-Identity operation.</span></span> <span data-ttu-id="79fec-196">U kunt de para meter **SkipTestConnection** toevoegen als het externe WS-Management-eind punt WS-identify niet kan gebruiken, of om een aantal gegevens overdrachts tijd te verminderen.</span><span class="sxs-lookup"><span data-stu-id="79fec-196">You can add the **SkipTestConnection** switch parameter if the remote WS-Management endpoint cannot use WS-Identify, or to reduce some data transmission time.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="79fec-197">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="79fec-197">CommonParameters</span></span>

<span data-ttu-id="79fec-198">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="79fec-198">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="79fec-199">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="79fec-199">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="79fec-200">INVOER</span><span class="sxs-lookup"><span data-stu-id="79fec-200">INPUTS</span></span>

### <span data-ttu-id="79fec-201">Geen</span><span class="sxs-lookup"><span data-stu-id="79fec-201">None</span></span>

<span data-ttu-id="79fec-202">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="79fec-202">This cmdlet accepts no inputs.</span></span>

## <span data-ttu-id="79fec-203">UITVOER</span><span class="sxs-lookup"><span data-stu-id="79fec-203">OUTPUTS</span></span>

### <span data-ttu-id="79fec-204">Micro soft. Management. Infrastructure. CimSession</span><span class="sxs-lookup"><span data-stu-id="79fec-204">Microsoft.Management.Infrastructure.CimSession</span></span>

## <span data-ttu-id="79fec-205">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="79fec-205">NOTES</span></span>

## <span data-ttu-id="79fec-206">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="79fec-206">RELATED LINKS</span></span>

[<span data-ttu-id="79fec-207">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="79fec-207">Get-ChildItem</span></span>](../Microsoft.Powershell.Management/Get-ChildItem.md)

[<span data-ttu-id="79fec-208">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="79fec-208">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="79fec-209">Get-item</span><span class="sxs-lookup"><span data-stu-id="79fec-209">Get-Item</span></span>](../Microsoft.Powershell.Management/Get-Item.md)

[<span data-ttu-id="79fec-210">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="79fec-210">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="79fec-211">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="79fec-211">Remove-CimSession</span></span>](Remove-CimSession.md)

[<span data-ttu-id="79fec-212">New-CimSessionOption</span><span class="sxs-lookup"><span data-stu-id="79fec-212">New-CimSessionOption</span></span>](New-CimSessionOption.md)

[<span data-ttu-id="79fec-213">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="79fec-213">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

