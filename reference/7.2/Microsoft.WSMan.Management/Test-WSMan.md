---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: a29a9ef1e35f0c0f802952b99d853c617614a97b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704719"
---
# <span data-ttu-id="5fcad-102">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="5fcad-102">Test-WSMan</span></span>

## <span data-ttu-id="5fcad-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5fcad-103">SYNOPSIS</span></span>
<span data-ttu-id="5fcad-104">Test of de WinRM-service wordt uitgevoerd op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="5fcad-104">Tests whether the WinRM service is running on a local or remote computer.</span></span>

## <span data-ttu-id="5fcad-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5fcad-105">SYNTAX</span></span>

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="5fcad-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5fcad-106">DESCRIPTION</span></span>

<span data-ttu-id="5fcad-107">Met de cmdlet **test-WSMan** wordt een identificatie aanvraag verzonden waarmee wordt bepaald of de WinRM-service wordt uitgevoerd op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="5fcad-107">The **Test-WSMan** cmdlet submits an identification request that determines whether the WinRM service is running on a local or remote computer.</span></span>
<span data-ttu-id="5fcad-108">Als de geteste computer de service uitvoert, geeft de cmdlet het WS-Management-identiteits schema, de Protocol versie, de product leverancier en de product versie van de geteste service weer.</span><span class="sxs-lookup"><span data-stu-id="5fcad-108">If the tested computer is running the service, the cmdlet displays the WS-Management identity schema, the protocol version, the product vendor, and the product version of the tested service.</span></span>

## <span data-ttu-id="5fcad-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5fcad-109">EXAMPLES</span></span>

### <span data-ttu-id="5fcad-110">Voor beeld 1: de status van de WinRM-service bepalen</span><span class="sxs-lookup"><span data-stu-id="5fcad-110">Example 1: Determine the status of the WinRM service</span></span>

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="5fcad-111">Met deze opdracht wordt bepaald of de WinRM-service wordt uitgevoerd op de lokale computer of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="5fcad-111">This command determines whether the WinRM service is running on the local computer or on a remote computer.</span></span>

### <span data-ttu-id="5fcad-112">Voor beeld 2: de status van de WinRM-service op een externe computer bepalen</span><span class="sxs-lookup"><span data-stu-id="5fcad-112">Example 2: Determine the status of the WinRM service on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="5fcad-113">Met deze opdracht wordt bepaald of de WinRM-service wordt uitgevoerd op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="5fcad-113">This command determines whether the WinRM service is running on the server01 computer.</span></span>

### <span data-ttu-id="5fcad-114">Voor beeld 3: de status van de WinRM-service en de versie van het besturings systeem bepalen</span><span class="sxs-lookup"><span data-stu-id="5fcad-114">Example 3: Determine the status of the WinRM service and the operating system version</span></span>

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

<span data-ttu-id="5fcad-115">Met deze opdracht wordt getest of de WS-Management-service (WinRM) wordt uitgevoerd op de lokale computer met behulp van de verificatie parameter.</span><span class="sxs-lookup"><span data-stu-id="5fcad-115">This command tests to see whether the WS-Management (WinRM) service is running on the local computer by using the authentication parameter.</span></span>

<span data-ttu-id="5fcad-116">Met behulp van de para meter verificatie kan de versie van het besturings systeem door **WSMan** worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5fcad-116">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

### <span data-ttu-id="5fcad-117">Voor beeld 4: de status van de WinRM-service en de versie van het besturings systeem op een externe computer bepalen</span><span class="sxs-lookup"><span data-stu-id="5fcad-117">Example 4: Determine the status of the WinRM service and the operating system version on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="5fcad-118">Met deze opdracht wordt getest of de WS-Management-service (WinRM) wordt uitgevoerd op de computer met de naam Server01 met behulp van de verificatie parameter.</span><span class="sxs-lookup"><span data-stu-id="5fcad-118">This command tests to see whether the WS-Management (WinRM) service is running on the computer named server01 using the authentication parameter.</span></span>

<span data-ttu-id="5fcad-119">Met behulp van de para meter verificatie kan de versie van het besturings systeem door **WSMan** worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5fcad-119">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

## <span data-ttu-id="5fcad-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5fcad-120">PARAMETERS</span></span>

### <span data-ttu-id="5fcad-121">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="5fcad-121">-ApplicationName</span></span>

<span data-ttu-id="5fcad-122">Hiermee geeft u de naam van de toepassing in de verbinding.</span><span class="sxs-lookup"><span data-stu-id="5fcad-122">Specifies the application name in the connection.</span></span>
<span data-ttu-id="5fcad-123">De standaard waarde van de para meter *ApplicationName* is WSMAN.</span><span class="sxs-lookup"><span data-stu-id="5fcad-123">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="5fcad-124">De volledige id voor het externe eind punt heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="5fcad-124">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="5fcad-125">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="5fcad-125">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="5fcad-126">Bijvoorbeeld: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="5fcad-126">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="5fcad-127">Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="5fcad-127">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="5fcad-128">Deze standaard instelling van WSMAN is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="5fcad-128">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="5fcad-129">Deze para meter is ontworpen om te worden gebruikt als veel computers externe verbindingen tot stand brengen met één computer waarop Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5fcad-129">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="5fcad-130">In dit geval wordt IIS gehost Web Services for Management (WS-Management) voor efficiëntie.</span><span class="sxs-lookup"><span data-stu-id="5fcad-130">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="5fcad-131">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="5fcad-131">-Authentication</span></span>

<span data-ttu-id="5fcad-132">Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server.</span><span class="sxs-lookup"><span data-stu-id="5fcad-132">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="5fcad-133">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="5fcad-133">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5fcad-134">Hoofd.</span><span class="sxs-lookup"><span data-stu-id="5fcad-134">Basic.</span></span>
<span data-ttu-id="5fcad-135">Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="5fcad-135">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="5fcad-136">Standaard.</span><span class="sxs-lookup"><span data-stu-id="5fcad-136">Default.</span></span>
<span data-ttu-id="5fcad-137">Gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol.</span><span class="sxs-lookup"><span data-stu-id="5fcad-137">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="5fcad-138">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="5fcad-138">This is the default.</span></span>
- <span data-ttu-id="5fcad-139">Vatting.</span><span class="sxs-lookup"><span data-stu-id="5fcad-139">Digest.</span></span>
<span data-ttu-id="5fcad-140">Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.</span><span class="sxs-lookup"><span data-stu-id="5fcad-140">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="5fcad-141">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="5fcad-141">Kerberos.</span></span>
<span data-ttu-id="5fcad-142">De client computer en de server worden wederzijds geverifieerd met behulp van Kerberos-certificaten.</span><span class="sxs-lookup"><span data-stu-id="5fcad-142">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="5fcad-143">Afspraken.</span><span class="sxs-lookup"><span data-stu-id="5fcad-143">Negotiate.</span></span>
<span data-ttu-id="5fcad-144">Onderhandelen is een vraag/antwoord-schema waarmee wordt onderhandeld over de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="5fcad-144">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="5fcad-145">Met deze parameter waarde kan bijvoorbeeld worden geonderhandelingd om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5fcad-145">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="5fcad-146">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="5fcad-146">CredSSP.</span></span>
<span data-ttu-id="5fcad-147">Gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren.</span><span class="sxs-lookup"><span data-stu-id="5fcad-147">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="5fcad-148">Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5fcad-148">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="5fcad-149">Let op: CredSSP delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="5fcad-149">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="5fcad-150">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="5fcad-150">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="5fcad-151">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="5fcad-151">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

<span data-ttu-id="5fcad-152">Belang rijk: als u de para meter *authenticatie* niet opgeeft, wordt de aanvraag van de **test-WSMan** anoniem verzonden naar de externe computer, zonder verificatie.</span><span class="sxs-lookup"><span data-stu-id="5fcad-152">Important: If you do not specify the *Authentication* parameter,, the **Test-WSMan** request is sent to the remote computer anonymously, without using authentication.</span></span>
<span data-ttu-id="5fcad-153">Als de aanvraag anoniem wordt gemaakt, wordt er geen informatie geretourneerd die specifiek is voor de versie van het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="5fcad-153">If the request is made anonymously, it returns no information that is specific to the operating-system version.</span></span>
<span data-ttu-id="5fcad-154">In plaats daarvan worden met deze cmdlet Null-waarden weer gegeven voor de versie van het besturings systeem en het Service Pack (OS: 0.0.0 SP: 0,0).</span><span class="sxs-lookup"><span data-stu-id="5fcad-154">Instead, this cmdlet displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

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

### <span data-ttu-id="5fcad-155">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="5fcad-155">-CertificateThumbprint</span></span>

<span data-ttu-id="5fcad-156">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5fcad-156">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="5fcad-157">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="5fcad-157">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="5fcad-158">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="5fcad-158">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="5fcad-159">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="5fcad-159">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="5fcad-160">Als u een certificaat vingerafdruk wilt krijgen, gebruikt u de opdracht Get-Item of Get-ChildItem in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="5fcad-160">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="5fcad-161">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="5fcad-161">-ComputerName</span></span>

<span data-ttu-id="5fcad-162">Hiermee geeft u de computer op waarop de beheer bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5fcad-162">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="5fcad-163">De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.</span><span class="sxs-lookup"><span data-stu-id="5fcad-163">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="5fcad-164">Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="5fcad-164">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="5fcad-165">De lokale computer is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="5fcad-165">The local computer is the default.</span></span>
<span data-ttu-id="5fcad-166">Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5fcad-166">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="5fcad-167">U kunt een waarde voor deze para meter door geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fcad-167">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5fcad-168">-Credential</span><span class="sxs-lookup"><span data-stu-id="5fcad-168">-Credential</span></span>

<span data-ttu-id="5fcad-169">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5fcad-169">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="5fcad-170">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="5fcad-170">The default is the current user.</span></span>
<span data-ttu-id="5fcad-171">Typ een gebruikers naam, zoals gebruiker01, Domain01\User01 of User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="5fcad-171">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="5fcad-172">U kunt ook een **PSCredential** -object invoeren, zoals het dat wordt geretourneerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="5fcad-172">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="5fcad-173">Wanneer u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="5fcad-173">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="5fcad-174">-Port</span><span class="sxs-lookup"><span data-stu-id="5fcad-174">-Port</span></span>

<span data-ttu-id="5fcad-175">Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="5fcad-175">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="5fcad-176">Wanneer het Trans Port HTTP is, is de standaard poort 80.</span><span class="sxs-lookup"><span data-stu-id="5fcad-176">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="5fcad-177">Wanneer het Trans Port HTTPS is, is de standaard poort 443.</span><span class="sxs-lookup"><span data-stu-id="5fcad-177">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="5fcad-178">Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter *ComputerName* overeenkomen met de common name (CN) van het server certificaat.</span><span class="sxs-lookup"><span data-stu-id="5fcad-178">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>

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

### <span data-ttu-id="5fcad-179">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="5fcad-179">-UseSSL</span></span>

<span data-ttu-id="5fcad-180">Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) wordt gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5fcad-180">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="5fcad-181">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5fcad-181">By default, SSL is not used.</span></span>

<span data-ttu-id="5fcad-182">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="5fcad-182">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="5fcad-183">Met de para meter *UseSSL* kunt u de extra beveiliging van https in plaats van http opgeven.</span><span class="sxs-lookup"><span data-stu-id="5fcad-183">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="5fcad-184">Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="5fcad-184">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="5fcad-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5fcad-185">CommonParameters</span></span>

<span data-ttu-id="5fcad-186">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5fcad-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5fcad-187">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5fcad-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5fcad-188">INVOER</span><span class="sxs-lookup"><span data-stu-id="5fcad-188">INPUTS</span></span>

### <span data-ttu-id="5fcad-189">Geen</span><span class="sxs-lookup"><span data-stu-id="5fcad-189">None</span></span>

<span data-ttu-id="5fcad-190">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="5fcad-190">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="5fcad-191">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5fcad-191">OUTPUTS</span></span>

### <span data-ttu-id="5fcad-192">Geen</span><span class="sxs-lookup"><span data-stu-id="5fcad-192">None</span></span>

<span data-ttu-id="5fcad-193">Met deze cmdlet wordt geen uitvoer object gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="5fcad-193">This cmdlet does not generate any output object.</span></span>

## <span data-ttu-id="5fcad-194">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5fcad-194">NOTES</span></span>

* <span data-ttu-id="5fcad-195">De cmdlet **test-WSMan** vraagt de WinRM-service standaard aan zonder gebruik te maken van verificatie en er wordt geen informatie geretourneerd die specifiek is voor de versie van het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="5fcad-195">By default, the **Test-WSMan** cmdlet queries the WinRM service without using authentication, and it returns no information that is specific to the operating-system version.</span></span> <span data-ttu-id="5fcad-196">In plaats daarvan worden Null-waarden weer gegeven voor de versie van het besturings systeem en het Service Pack-niveau (OS: 0.0.0 SP: 0,0).</span><span class="sxs-lookup"><span data-stu-id="5fcad-196">Instead, it displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

*

## <span data-ttu-id="5fcad-197">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5fcad-197">RELATED LINKS</span></span>

[<span data-ttu-id="5fcad-198">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="5fcad-198">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="5fcad-199">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="5fcad-199">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="5fcad-200">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="5fcad-200">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="5fcad-201">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="5fcad-201">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="5fcad-202">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="5fcad-202">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="5fcad-203">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5fcad-203">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="5fcad-204">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="5fcad-204">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="5fcad-205">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5fcad-205">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="5fcad-206">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="5fcad-206">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="5fcad-207">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5fcad-207">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="5fcad-208">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5fcad-208">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="5fcad-209">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="5fcad-209">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

