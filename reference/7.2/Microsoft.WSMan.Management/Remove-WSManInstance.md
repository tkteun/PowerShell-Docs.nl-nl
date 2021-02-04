---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/remove-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WSManInstance
ms.openlocfilehash: 4d1273fe1ed643f8d45b627db9863b75212b6b24
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705685"
---
# <span data-ttu-id="b1f6f-102">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b1f6f-102">Remove-WSManInstance</span></span>

## <span data-ttu-id="b1f6f-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b1f6f-103">SYNOPSIS</span></span>
<span data-ttu-id="b1f6f-104">Hiermee verwijdert u een beheer resource-exemplaar.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-104">Deletes a management resource instance.</span></span>

## <span data-ttu-id="b1f6f-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b1f6f-105">SYNTAX</span></span>

### <span data-ttu-id="b1f6f-106">Computer naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="b1f6f-106">ComputerName (Default)</span></span>

```
Remove-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-UseSSL]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="b1f6f-107">URI</span><span class="sxs-lookup"><span data-stu-id="b1f6f-107">URI</span></span>

```
Remove-WSManInstance [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="b1f6f-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b1f6f-108">DESCRIPTION</span></span>

<span data-ttu-id="b1f6f-109">De cmdlet **Remove-WSManInstance** verwijdert een exemplaar van een beheer bron die is opgegeven in de para meters *ResourceURI* en *SelectorSet* .</span><span class="sxs-lookup"><span data-stu-id="b1f6f-109">The **Remove-WSManInstance** cmdlet deletes an instance of a management resource that is specified in the *ResourceURI* and *SelectorSet* parameters.</span></span>

<span data-ttu-id="b1f6f-110">Deze cmdlet maakt gebruik van de WinRM-verbinding/Trans Port-laag voor het verwijderen van het beheer resource-exemplaar.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-110">This cmdlet uses the WinRM connection/transport layer to delete the management resource instance.</span></span>

## <span data-ttu-id="b1f6f-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b1f6f-111">EXAMPLES</span></span>

### <span data-ttu-id="b1f6f-112">Voor beeld 1: een listener verwijderen</span><span class="sxs-lookup"><span data-stu-id="b1f6f-112">Example 1: Delete a listener</span></span>

```
PS C:\> Remove-WSManInstance -ResourceUri winrm/config/Listener -SelectorSet Address=test.fabrikam.com;Transport=http
```

<span data-ttu-id="b1f6f-113">Met deze opdracht wordt de HTTP-listener van WS-Management op een computer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-113">This command deletes the WS-Management HTTP listener on a computer.</span></span>

## <span data-ttu-id="b1f6f-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b1f6f-114">PARAMETERS</span></span>

### <span data-ttu-id="b1f6f-115">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="b1f6f-115">-ApplicationName</span></span>

<span data-ttu-id="b1f6f-116">Hiermee geeft u de naam van de toepassing in de verbinding.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-116">Specifies the application name in the connection.</span></span>
<span data-ttu-id="b1f6f-117">De standaard waarde van de para meter *ApplicationName* is WSMAN.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-117">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="b1f6f-118">De volledige id voor het externe eind punt heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="b1f6f-118">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="b1f6f-119">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="b1f6f-119">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="b1f6f-120">Bijvoorbeeld: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="b1f6f-120">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="b1f6f-121">Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-121">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="b1f6f-122">Deze standaard instelling van WSMAN is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-122">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="b1f6f-123">Deze para meter is ontworpen om te worden gebruikt als veel computers externe verbindingen tot stand brengen met één computer waarop Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-123">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="b1f6f-124">In dit geval wordt IIS gehost Web Services for Management (WS-Management) voor efficiëntie.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-124">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1f6f-125">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="b1f6f-125">-Authentication</span></span>

<span data-ttu-id="b1f6f-126">Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-126">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="b1f6f-127">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="b1f6f-127">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b1f6f-128">Hoofd.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-128">Basic.</span></span>
<span data-ttu-id="b1f6f-129">Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-129">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="b1f6f-130">Standaard.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-130">Default.</span></span>
<span data-ttu-id="b1f6f-131">Gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-131">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="b1f6f-132">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-132">This is the default.</span></span>
- <span data-ttu-id="b1f6f-133">Vatting.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-133">Digest.</span></span>
<span data-ttu-id="b1f6f-134">Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-134">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="b1f6f-135">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-135">Kerberos.</span></span>
<span data-ttu-id="b1f6f-136">De client computer en de server worden wederzijds geverifieerd met behulp van Kerberos-certificaten.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-136">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="b1f6f-137">Afspraken.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-137">Negotiate.</span></span>
<span data-ttu-id="b1f6f-138">Onderhandelen is een vraag/antwoord-schema waarmee wordt onderhandeld over de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-138">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="b1f6f-139">Met deze parameter waarde kan bijvoorbeeld worden geonderhandelingd om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-139">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="b1f6f-140">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-140">CredSSP.</span></span>
<span data-ttu-id="b1f6f-141">Gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-141">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="b1f6f-142">Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-142">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="b1f6f-143">Let op: CredSSP delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-143">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="b1f6f-144">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-144">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="b1f6f-145">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-145">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1f6f-146">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="b1f6f-146">-CertificateThumbprint</span></span>

<span data-ttu-id="b1f6f-147">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-147">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="b1f6f-148">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-148">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="b1f6f-149">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-149">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="b1f6f-150">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-150">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="b1f6f-151">Als u een certificaat vingerafdruk wilt krijgen, gebruikt u de opdracht Get-Item of Get-ChildItem in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-151">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="b1f6f-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b1f6f-152">-ComputerName</span></span>

<span data-ttu-id="b1f6f-153">Hiermee geeft u de computer op waarop de beheer bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-153">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="b1f6f-154">De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-154">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="b1f6f-155">Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-155">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="b1f6f-156">De lokale computer is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-156">The local computer is the default.</span></span>
<span data-ttu-id="b1f6f-157">Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-157">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="b1f6f-158">U kunt een waarde voor deze para meter door geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-158">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1f6f-159">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="b1f6f-159">-ConnectionURI</span></span>

<span data-ttu-id="b1f6f-160">Hiermee geeft u het eind punt van de verbinding.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-160">Specifies the connection endpoint.</span></span>
<span data-ttu-id="b1f6f-161">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="b1f6f-161">The format of this string is as follows:</span></span>

<span data-ttu-id="b1f6f-162">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="b1f6f-162">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="b1f6f-163">De volgende teken reeks is een correct ingedeelde waarde voor deze para meter:</span><span class="sxs-lookup"><span data-stu-id="b1f6f-163">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="b1f6f-164">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-164">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1f6f-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="b1f6f-165">-Credential</span></span>

<span data-ttu-id="b1f6f-166">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-166">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="b1f6f-167">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-167">The default is the current user.</span></span>
<span data-ttu-id="b1f6f-168">Typ een gebruikers naam, zoals gebruiker01, Domain01\User01 of User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="b1f6f-168">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="b1f6f-169">U kunt ook een **PSCredential** -object invoeren, zoals het dat wordt geretourneerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-169">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="b1f6f-170">Wanneer u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-170">When you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b1f6f-171">-Optieset</span><span class="sxs-lookup"><span data-stu-id="b1f6f-171">-OptionSet</span></span>

<span data-ttu-id="b1f6f-172">Hiermee geeft u een set switches naar een service op om de aard van de aanvraag te wijzigen of te verfijnen.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-172">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="b1f6f-173">Deze lijken op de Schakel opties die worden gebruikt in opdracht regel shells, omdat deze service-specifiek zijn.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-173">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="b1f6f-174">U kunt een wille keurig aantal opties opgeven.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-174">Any number of options can be specified.</span></span>

<span data-ttu-id="b1f6f-175">In het volgende voor beeld ziet u de syntaxis waarmee de waarden 1, 2 en 3 worden door gegeven voor de para meters a, b en c:</span><span class="sxs-lookup"><span data-stu-id="b1f6f-175">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1f6f-176">-Port</span><span class="sxs-lookup"><span data-stu-id="b1f6f-176">-Port</span></span>

<span data-ttu-id="b1f6f-177">Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-177">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="b1f6f-178">Wanneer het Trans Port HTTP is, is de standaard poort 80.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-178">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="b1f6f-179">Wanneer het Trans Port HTTPS is, is de standaard poort 443.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-179">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="b1f6f-180">Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter *ComputerName* overeenkomen met de common name (CN) van het server certificaat.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-180">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="b1f6f-181">Als de para meter *SkipCNCheck* echter is opgegeven als onderdeel van de *SessionOption* -para meter, moet de algemene naam van het certificaat van de server niet overeenkomen met de hostnaam van de server.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-181">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="b1f6f-182">De para meter *SkipCNCheck* moet alleen worden gebruikt voor vertrouwde computers.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-182">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="b1f6f-183">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="b1f6f-183">-ResourceURI</span></span>

<span data-ttu-id="b1f6f-184">Hiermee geeft u de URI van de resource klasse of het exemplaar.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-184">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="b1f6f-185">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-185">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="b1f6f-186">Een URI bestaat uit een voor voegsel en een pad van een resource.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-186">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="b1f6f-187">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b1f6f-187">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1f6f-188">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="b1f6f-188">-SelectorSet</span></span>

<span data-ttu-id="b1f6f-189">Hiermee geeft u een set waardeparen op die worden gebruikt om bepaalde beheer resource-instanties te selecteren.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-189">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="b1f6f-190">De para meter *SelectorSet* wordt gebruikt wanneer er meer dan één exemplaar van de bron bestaat.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-190">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="b1f6f-191">De waarde van *SelectorSet* moet een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-191">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="b1f6f-192">In het volgende voor beeld ziet u hoe u een waarde voor deze para meter opgeeft:</span><span class="sxs-lookup"><span data-stu-id="b1f6f-192">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b1f6f-193">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="b1f6f-193">-SessionOption</span></span>

<span data-ttu-id="b1f6f-194">Hiermee worden uitgebreide opties voor de WS-Management-sessie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-194">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="b1f6f-195">Voer een **SessionOption** -object in dat u maakt met behulp van de cmdlet New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-195">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="b1f6f-196">Typ voor meer informatie over de beschik bare opties `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="b1f6f-196">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: so

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1f6f-197">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="b1f6f-197">-UseSSL</span></span>

<span data-ttu-id="b1f6f-198">Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) wordt gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-198">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="b1f6f-199">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-199">By default, SSL is not used.</span></span>

<span data-ttu-id="b1f6f-200">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-200">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="b1f6f-201">Met de para meter *UseSSL* kunt u de extra beveiliging van https in plaats van http opgeven.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-201">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="b1f6f-202">Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-202">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases: ssl

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1f6f-203">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b1f6f-203">CommonParameters</span></span>

<span data-ttu-id="b1f6f-204">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-204">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b1f6f-205">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-205">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b1f6f-206">INVOER</span><span class="sxs-lookup"><span data-stu-id="b1f6f-206">INPUTS</span></span>

### <span data-ttu-id="b1f6f-207">Geen</span><span class="sxs-lookup"><span data-stu-id="b1f6f-207">None</span></span>

<span data-ttu-id="b1f6f-208">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-208">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="b1f6f-209">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b1f6f-209">OUTPUTS</span></span>

### <span data-ttu-id="b1f6f-210">Geen</span><span class="sxs-lookup"><span data-stu-id="b1f6f-210">None</span></span>

<span data-ttu-id="b1f6f-211">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-211">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b1f6f-212">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b1f6f-212">NOTES</span></span>

* <span data-ttu-id="b1f6f-213">De cmdlet Remove-WmiObject, een Windows Management Instrumentation-cmdlet (WMI), is vergelijkbaar.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-213">The Remove-WmiObject cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span> <span data-ttu-id="b1f6f-214">**Remove-WmiObject** gebruikt de DCOM-verbinding/Trans Port-laag voor het maken of bijwerken van WMI-exemplaren.</span><span class="sxs-lookup"><span data-stu-id="b1f6f-214">**Remove-WmiObject** uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

*

## <span data-ttu-id="b1f6f-215">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b1f6f-215">RELATED LINKS</span></span>

[<span data-ttu-id="b1f6f-216">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b1f6f-216">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="b1f6f-217">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b1f6f-217">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="b1f6f-218">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="b1f6f-218">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="b1f6f-219">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b1f6f-219">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="b1f6f-220">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b1f6f-220">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="b1f6f-221">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b1f6f-221">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="b1f6f-222">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="b1f6f-222">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="b1f6f-223">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b1f6f-223">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="b1f6f-224">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="b1f6f-224">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="b1f6f-225">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b1f6f-225">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="b1f6f-226">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="b1f6f-226">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="b1f6f-227">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="b1f6f-227">Test-WSMan</span></span>](Test-WSMan.md)
