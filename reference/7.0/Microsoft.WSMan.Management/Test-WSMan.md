---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: 602f390aa6474d56e2ac1865dbad20fbb73dc4f1
ms.sourcegitcommit: 87b9b989f261b52969e99159e99ee28ad8d8839a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/21/2020
ms.locfileid: "93251455"
---
# <span data-ttu-id="1435f-103">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="1435f-103">Test-WSMan</span></span>

## <span data-ttu-id="1435f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1435f-104">SYNOPSIS</span></span>
<span data-ttu-id="1435f-105">Test of de WinRM-service wordt uitgevoerd op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="1435f-105">Tests whether the WinRM service is running on a local or remote computer.</span></span>

## <span data-ttu-id="1435f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1435f-106">SYNTAX</span></span>

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="1435f-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1435f-107">DESCRIPTION</span></span>

<span data-ttu-id="1435f-108">Met de cmdlet **test-WSMan** wordt een identificatie aanvraag verzonden waarmee wordt bepaald of de WinRM-service wordt uitgevoerd op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="1435f-108">The **Test-WSMan** cmdlet submits an identification request that determines whether the WinRM service is running on a local or remote computer.</span></span>
<span data-ttu-id="1435f-109">Als de geteste computer de service uitvoert, geeft de cmdlet het WS-Management-identiteits schema, de Protocol versie, de product leverancier en de product versie van de geteste service weer.</span><span class="sxs-lookup"><span data-stu-id="1435f-109">If the tested computer is running the service, the cmdlet displays the WS-Management identity schema, the protocol version, the product vendor, and the product version of the tested service.</span></span>

## <span data-ttu-id="1435f-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1435f-110">EXAMPLES</span></span>

### <span data-ttu-id="1435f-111">Voor beeld 1: de status van de WinRM-service bepalen</span><span class="sxs-lookup"><span data-stu-id="1435f-111">Example 1: Determine the status of the WinRM service</span></span>

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="1435f-112">Met deze opdracht wordt bepaald of de WinRM-service wordt uitgevoerd op de lokale computer of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="1435f-112">This command determines whether the WinRM service is running on the local computer or on a remote computer.</span></span>

### <span data-ttu-id="1435f-113">Voor beeld 2: de status van de WinRM-service op een externe computer bepalen</span><span class="sxs-lookup"><span data-stu-id="1435f-113">Example 2: Determine the status of the WinRM service on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="1435f-114">Met deze opdracht wordt bepaald of de WinRM-service wordt uitgevoerd op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="1435f-114">This command determines whether the WinRM service is running on the server01 computer.</span></span>

### <span data-ttu-id="1435f-115">Voor beeld 3: de status van de WinRM-service en de versie van het besturings systeem bepalen</span><span class="sxs-lookup"><span data-stu-id="1435f-115">Example 3: Determine the status of the WinRM service and the operating system version</span></span>

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

<span data-ttu-id="1435f-116">Met deze opdracht wordt getest of de WS-Management-service (WinRM) wordt uitgevoerd op de lokale computer met behulp van de verificatie parameter.</span><span class="sxs-lookup"><span data-stu-id="1435f-116">This command tests to see whether the WS-Management (WinRM) service is running on the local computer by using the authentication parameter.</span></span>

<span data-ttu-id="1435f-117">Met behulp van de para meter verificatie kan de versie van het besturings systeem door **WSMan** worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1435f-117">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

### <span data-ttu-id="1435f-118">Voor beeld 4: de status van de WinRM-service en de versie van het besturings systeem op een externe computer bepalen</span><span class="sxs-lookup"><span data-stu-id="1435f-118">Example 4: Determine the status of the WinRM service and the operating system version on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="1435f-119">Met deze opdracht wordt getest of de WS-Management-service (WinRM) wordt uitgevoerd op de computer met de naam Server01 met behulp van de verificatie parameter.</span><span class="sxs-lookup"><span data-stu-id="1435f-119">This command tests to see whether the WS-Management (WinRM) service is running on the computer named server01 using the authentication parameter.</span></span>

<span data-ttu-id="1435f-120">Met behulp van de para meter verificatie kan de versie van het besturings systeem door **WSMan** worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1435f-120">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

## <span data-ttu-id="1435f-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1435f-121">PARAMETERS</span></span>

### <span data-ttu-id="1435f-122">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="1435f-122">-ApplicationName</span></span>

<span data-ttu-id="1435f-123">Hiermee geeft u de naam van de toepassing in de verbinding.</span><span class="sxs-lookup"><span data-stu-id="1435f-123">Specifies the application name in the connection.</span></span>
<span data-ttu-id="1435f-124">De standaard waarde van de para meter *ApplicationName* is WSMAN.</span><span class="sxs-lookup"><span data-stu-id="1435f-124">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="1435f-125">De volledige id voor het externe eind punt heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="1435f-125">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="1435f-126">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="1435f-126">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="1435f-127">Bijvoorbeeld: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="1435f-127">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="1435f-128">Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="1435f-128">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="1435f-129">Deze standaard instelling van WSMAN is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="1435f-129">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="1435f-130">Deze para meter is ontworpen om te worden gebruikt als veel computers externe verbindingen tot stand brengen met één computer waarop Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1435f-130">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="1435f-131">In dit geval wordt IIS gehost Web Services for Management (WS-Management) voor efficiëntie.</span><span class="sxs-lookup"><span data-stu-id="1435f-131">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="1435f-132">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="1435f-132">-Authentication</span></span>

<span data-ttu-id="1435f-133">Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server.</span><span class="sxs-lookup"><span data-stu-id="1435f-133">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="1435f-134">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="1435f-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1435f-135">Hoofd.</span><span class="sxs-lookup"><span data-stu-id="1435f-135">Basic.</span></span>
<span data-ttu-id="1435f-136">Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="1435f-136">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="1435f-137">Standaard.</span><span class="sxs-lookup"><span data-stu-id="1435f-137">Default.</span></span>
<span data-ttu-id="1435f-138">Gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol.</span><span class="sxs-lookup"><span data-stu-id="1435f-138">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="1435f-139">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="1435f-139">This is the default.</span></span>
- <span data-ttu-id="1435f-140">Vatting.</span><span class="sxs-lookup"><span data-stu-id="1435f-140">Digest.</span></span>
<span data-ttu-id="1435f-141">Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.</span><span class="sxs-lookup"><span data-stu-id="1435f-141">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="1435f-142">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="1435f-142">Kerberos.</span></span>
<span data-ttu-id="1435f-143">De client computer en de server worden wederzijds geverifieerd met behulp van Kerberos-certificaten.</span><span class="sxs-lookup"><span data-stu-id="1435f-143">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="1435f-144">Afspraken.</span><span class="sxs-lookup"><span data-stu-id="1435f-144">Negotiate.</span></span>
<span data-ttu-id="1435f-145">Onderhandelen is een vraag/antwoord-schema waarmee wordt onderhandeld over de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="1435f-145">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="1435f-146">Met deze parameter waarde kan bijvoorbeeld worden geonderhandelingd om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1435f-146">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="1435f-147">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="1435f-147">CredSSP.</span></span>
<span data-ttu-id="1435f-148">Gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren.</span><span class="sxs-lookup"><span data-stu-id="1435f-148">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="1435f-149">Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1435f-149">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="1435f-150">Let op: CredSSP delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="1435f-150">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="1435f-151">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="1435f-151">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="1435f-152">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="1435f-152">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

<span data-ttu-id="1435f-153">Belang rijk: als u de para meter *authenticatie* niet opgeeft, wordt de aanvraag van de **test-WSMan** anoniem verzonden naar de externe computer, zonder verificatie.</span><span class="sxs-lookup"><span data-stu-id="1435f-153">Important: If you do not specify the *Authentication* parameter,, the **Test-WSMan** request is sent to the remote computer anonymously, without using authentication.</span></span>
<span data-ttu-id="1435f-154">Als de aanvraag anoniem wordt gemaakt, wordt er geen informatie geretourneerd die specifiek is voor de versie van het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="1435f-154">If the request is made anonymously, it returns no information that is specific to the operating-system version.</span></span>
<span data-ttu-id="1435f-155">In plaats daarvan worden met deze cmdlet Null-waarden weer gegeven voor de versie van het besturings systeem en het Service Pack (OS: 0.0.0 SP: 0,0).</span><span class="sxs-lookup"><span data-stu-id="1435f-155">Instead, this cmdlet displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

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

### <span data-ttu-id="1435f-156">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="1435f-156">-CertificateThumbprint</span></span>

<span data-ttu-id="1435f-157">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1435f-157">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="1435f-158">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="1435f-158">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="1435f-159">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="1435f-159">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="1435f-160">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="1435f-160">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="1435f-161">Als u een certificaat vingerafdruk wilt krijgen, gebruikt u de opdracht Get-Item of Get-ChildItem in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="1435f-161">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="1435f-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="1435f-162">-ComputerName</span></span>

<span data-ttu-id="1435f-163">Hiermee geeft u de computer op waarop de beheer bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1435f-163">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="1435f-164">De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.</span><span class="sxs-lookup"><span data-stu-id="1435f-164">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="1435f-165">Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="1435f-165">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="1435f-166">De lokale computer is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="1435f-166">The local computer is the default.</span></span>
<span data-ttu-id="1435f-167">Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1435f-167">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="1435f-168">U kunt een waarde voor deze para meter door geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1435f-168">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="1435f-169">-Credential</span><span class="sxs-lookup"><span data-stu-id="1435f-169">-Credential</span></span>

<span data-ttu-id="1435f-170">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1435f-170">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="1435f-171">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="1435f-171">The default is the current user.</span></span>
<span data-ttu-id="1435f-172">Typ een gebruikers naam, zoals gebruiker01, Domain01\User01 of User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="1435f-172">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="1435f-173">U kunt ook een **PSCredential** -object invoeren, zoals het dat wordt geretourneerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="1435f-173">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="1435f-174">Wanneer u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="1435f-174">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="1435f-175">-Port</span><span class="sxs-lookup"><span data-stu-id="1435f-175">-Port</span></span>

<span data-ttu-id="1435f-176">Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="1435f-176">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="1435f-177">Wanneer het Trans Port HTTP is, is de standaard poort 80.</span><span class="sxs-lookup"><span data-stu-id="1435f-177">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="1435f-178">Wanneer het Trans Port HTTPS is, is de standaard poort 443.</span><span class="sxs-lookup"><span data-stu-id="1435f-178">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="1435f-179">Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter *ComputerName* overeenkomen met de common name (CN) van het server certificaat.</span><span class="sxs-lookup"><span data-stu-id="1435f-179">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>

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

### <span data-ttu-id="1435f-180">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="1435f-180">-UseSSL</span></span>

<span data-ttu-id="1435f-181">Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) wordt gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1435f-181">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="1435f-182">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1435f-182">By default, SSL is not used.</span></span>

<span data-ttu-id="1435f-183">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="1435f-183">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="1435f-184">Met de para meter *UseSSL* kunt u de extra beveiliging van https in plaats van http opgeven.</span><span class="sxs-lookup"><span data-stu-id="1435f-184">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="1435f-185">Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1435f-185">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="1435f-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1435f-186">CommonParameters</span></span>

<span data-ttu-id="1435f-187">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1435f-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1435f-188">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1435f-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1435f-189">INVOER</span><span class="sxs-lookup"><span data-stu-id="1435f-189">INPUTS</span></span>

### <span data-ttu-id="1435f-190">Geen</span><span class="sxs-lookup"><span data-stu-id="1435f-190">None</span></span>

<span data-ttu-id="1435f-191">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="1435f-191">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="1435f-192">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1435f-192">OUTPUTS</span></span>

### <span data-ttu-id="1435f-193">Geen</span><span class="sxs-lookup"><span data-stu-id="1435f-193">None</span></span>

<span data-ttu-id="1435f-194">Met deze cmdlet wordt geen uitvoer object gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1435f-194">This cmdlet does not generate any output object.</span></span>

## <span data-ttu-id="1435f-195">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1435f-195">NOTES</span></span>

* <span data-ttu-id="1435f-196">De cmdlet **test-WSMan** vraagt de WinRM-service standaard aan zonder gebruik te maken van verificatie en er wordt geen informatie geretourneerd die specifiek is voor de versie van het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="1435f-196">By default, the **Test-WSMan** cmdlet queries the WinRM service without using authentication, and it returns no information that is specific to the operating-system version.</span></span> <span data-ttu-id="1435f-197">In plaats daarvan worden Null-waarden weer gegeven voor de versie van het besturings systeem en het Service Pack-niveau (OS: 0.0.0 SP: 0,0).</span><span class="sxs-lookup"><span data-stu-id="1435f-197">Instead, it displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

## <span data-ttu-id="1435f-198">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1435f-198">RELATED LINKS</span></span>

[<span data-ttu-id="1435f-199">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="1435f-199">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="1435f-200">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="1435f-200">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="1435f-201">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="1435f-201">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="1435f-202">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="1435f-202">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="1435f-203">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="1435f-203">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="1435f-204">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="1435f-204">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="1435f-205">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="1435f-205">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="1435f-206">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="1435f-206">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="1435f-207">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="1435f-207">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="1435f-208">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="1435f-208">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="1435f-209">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="1435f-209">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="1435f-210">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="1435f-210">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)
