---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 03/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManInstance
ms.openlocfilehash: dd0343e9b6014e079c322309b699874683bacd6a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704718"
---
# <span data-ttu-id="0eee8-102">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="0eee8-102">New-WSManInstance</span></span>

## <span data-ttu-id="0eee8-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0eee8-103">SYNOPSIS</span></span>
<span data-ttu-id="0eee8-104">Hiermee maakt u een nieuw exemplaar van een beheer bron.</span><span class="sxs-lookup"><span data-stu-id="0eee8-104">Creates a new instance of a management resource.</span></span>

## <span data-ttu-id="0eee8-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0eee8-105">SYNTAX</span></span>

### <span data-ttu-id="0eee8-106">Computer naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="0eee8-106">ComputerName (Default)</span></span>

```
New-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable>
 [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="0eee8-107">URI</span><span class="sxs-lookup"><span data-stu-id="0eee8-107">URI</span></span>

```
New-WSManInstance [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="0eee8-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0eee8-108">DESCRIPTION</span></span>

<span data-ttu-id="0eee8-109">De `New-WSManInstance` cmdlet maakt een nieuw exemplaar van een beheer bron.</span><span class="sxs-lookup"><span data-stu-id="0eee8-109">The `New-WSManInstance` cmdlet creates a new instance of a management resource.</span></span> <span data-ttu-id="0eee8-110">Het maakt gebruik van een resource-URI en een ingestelde waarde of invoer bestand om het nieuwe exemplaar van de beheer bron te maken.</span><span class="sxs-lookup"><span data-stu-id="0eee8-110">It uses a resource URI and a value set or input file to create the new instance of the management resource.</span></span>

<span data-ttu-id="0eee8-111">Deze cmdlet maakt gebruik van de WinRM-verbinding/Trans Port-laag voor het maken van het beheer resource-exemplaar.</span><span class="sxs-lookup"><span data-stu-id="0eee8-111">This cmdlet uses the WinRM connection/transport layer to create the management resource instance.</span></span>

## <span data-ttu-id="0eee8-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0eee8-112">EXAMPLES</span></span>

### <span data-ttu-id="0eee8-113">Voor beeld 1: een HTTPS-listener maken</span><span class="sxs-lookup"><span data-stu-id="0eee8-113">Example 1: Create a HTTPS listener</span></span>

<span data-ttu-id="0eee8-114">Met deze opdracht maakt u een exemplaar van een WS-Management HTTPS-listener op alle IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="0eee8-114">This command creates an instance of a WS-Management HTTPS listener on all IP addresses.</span></span>

```powershell
New-WSManInstance winrm/config/Listener -SelectorSet @{Transport='HTTPS'; Address='*'} -ValueSet @{Hostname="HOST";CertificateThumbprint="XXXXXXXXXX"}
```

## <span data-ttu-id="0eee8-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0eee8-115">PARAMETERS</span></span>

### <span data-ttu-id="0eee8-116">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="0eee8-116">-ApplicationName</span></span>

<span data-ttu-id="0eee8-117">Hiermee geeft u de naam van de toepassing in de verbinding.</span><span class="sxs-lookup"><span data-stu-id="0eee8-117">Specifies the application name in the connection.</span></span> <span data-ttu-id="0eee8-118">De standaard waarde van de para meter **ApplicationName** is **WSMAN**.</span><span class="sxs-lookup"><span data-stu-id="0eee8-118">The default value of the **ApplicationName** parameter is **WSMAN**.</span></span> <span data-ttu-id="0eee8-119">De volledige id voor het externe eind punt heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="0eee8-119">The complete identifier for the remote endpoint is in the following format:</span></span>

`<transport>://<server>:<port>/<ApplicationName>`

<span data-ttu-id="0eee8-120">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="0eee8-120">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="0eee8-121">Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="0eee8-121">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span> <span data-ttu-id="0eee8-122">Deze standaard instelling van **WSMAN** is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="0eee8-122">This default setting of **WSMAN** is appropriate for most uses.</span></span> <span data-ttu-id="0eee8-123">Deze para meter is ontworpen om te worden gebruikt wanneer talloze computers externe verbindingen tot stand brengen met één computer met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="0eee8-123">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span> <span data-ttu-id="0eee8-124">In dit geval wordt IIS gehost Web Services for Management (WS-Management) voor efficiëntie.</span><span class="sxs-lookup"><span data-stu-id="0eee8-124">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: Wsman
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eee8-125">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="0eee8-125">-Authentication</span></span>

<span data-ttu-id="0eee8-126">Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server.</span><span class="sxs-lookup"><span data-stu-id="0eee8-126">Specifies the authentication mechanism to be used at the server.</span></span> <span data-ttu-id="0eee8-127">Mogelijke waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="0eee8-127">Possible values are:</span></span>

- <span data-ttu-id="0eee8-128">Basic: Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="0eee8-128">Basic: Basic is a scheme in which the username and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="0eee8-129">Standaard: gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol.</span><span class="sxs-lookup"><span data-stu-id="0eee8-129">Default: Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="0eee8-130">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="0eee8-130">This is the default.</span></span>
- <span data-ttu-id="0eee8-131">Digest: Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.</span><span class="sxs-lookup"><span data-stu-id="0eee8-131">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="0eee8-132">Kerberos: de client computer en de server worden wederzijds geverifieerd met Kerberos-certificaten.</span><span class="sxs-lookup"><span data-stu-id="0eee8-132">Kerberos: The client computer and the server mutually authenticate using Kerberos certificates.</span></span>
- <span data-ttu-id="0eee8-133">Onderhandelen: onderhandelen is een vraag/antwoord-schema dat onderhandelt met de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="0eee8-133">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="0eee8-134">Deze parameter waarde kan bijvoorbeeld onderhandelen om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0eee8-134">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="0eee8-135">CredSSP: gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren.</span><span class="sxs-lookup"><span data-stu-id="0eee8-135">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="0eee8-136">Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0eee8-136">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

> [!CAUTION]
> <span data-ttu-id="0eee8-137">CredSSP delegeert de referenties van de gebruiker van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="0eee8-137">CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="0eee8-138">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="0eee8-138">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="0eee8-139">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="0eee8-139">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="0eee8-140">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="0eee8-140">-CertificateThumbprint</span></span>

<span data-ttu-id="0eee8-141">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0eee8-141">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="0eee8-142">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="0eee8-142">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="0eee8-143">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="0eee8-143">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="0eee8-144">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="0eee8-144">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="0eee8-145">Als u een certificaat vingerafdruk wilt ophalen, gebruikt u de `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="0eee8-145">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="0eee8-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="0eee8-146">-ComputerName</span></span>

<span data-ttu-id="0eee8-147">Hiermee geeft u de computer op waartegen u de beheer bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0eee8-147">Specifies the computer against which you want to run the management operation.</span></span> <span data-ttu-id="0eee8-148">De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.</span><span class="sxs-lookup"><span data-stu-id="0eee8-148">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="0eee8-149">Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt ( `.` ) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="0eee8-149">Use the local computer name, use localhost, or use a dot (`.`) to specify the local computer.</span></span> <span data-ttu-id="0eee8-150">De lokale computer is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="0eee8-150">The local computer is the default.</span></span> <span data-ttu-id="0eee8-151">Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0eee8-151">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span> <span data-ttu-id="0eee8-152">U kunt een waarde voor deze para meter door geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0eee8-152">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: Localhost
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eee8-153">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="0eee8-153">-ConnectionURI</span></span>

<span data-ttu-id="0eee8-154">Hiermee geeft u het eind punt van de verbinding.</span><span class="sxs-lookup"><span data-stu-id="0eee8-154">Specifies the connection endpoint.</span></span>
<span data-ttu-id="0eee8-155">De notatie van deze teken reeks is:</span><span class="sxs-lookup"><span data-stu-id="0eee8-155">The format of this string is:</span></span>

`<Transport>://<Server>:<Port>/<ApplicationName>`

<span data-ttu-id="0eee8-156">De volgende teken reeks is een correct ingedeelde waarde voor deze para meter:</span><span class="sxs-lookup"><span data-stu-id="0eee8-156">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="0eee8-157">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="0eee8-157">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eee8-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="0eee8-158">-Credential</span></span>

<span data-ttu-id="0eee8-159">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0eee8-159">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="0eee8-160">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0eee8-160">The default is the current user.</span></span> <span data-ttu-id="0eee8-161">Typ een gebruikers naam, zoals "gebruiker01", "Domain01\User01" of " User@Domain.com ".</span><span class="sxs-lookup"><span data-stu-id="0eee8-161">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span> <span data-ttu-id="0eee8-162">U kunt ook een PSCredential-object invoeren, zoals het item dat door de cmdlet wordt geretourneerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="0eee8-162">Or, enter a PSCredential object, such as one returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="0eee8-163">Wanneer u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="0eee8-163">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="0eee8-164">-FilePath</span><span class="sxs-lookup"><span data-stu-id="0eee8-164">-FilePath</span></span>

<span data-ttu-id="0eee8-165">Hiermee geeft u het pad op van een bestand dat wordt gebruikt om een beheer bron te maken.</span><span class="sxs-lookup"><span data-stu-id="0eee8-165">Specifies the path of a file that is used to create a management resource.</span></span> <span data-ttu-id="0eee8-166">U geeft de beheer resource op met behulp van de para meter **ResourceURI** en de para meter **SelectorSet** .</span><span class="sxs-lookup"><span data-stu-id="0eee8-166">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter .</span></span> <span data-ttu-id="0eee8-167">Met de volgende opdracht wordt bijvoorbeeld de **File** -para meter gebruikt:</span><span class="sxs-lookup"><span data-stu-id="0eee8-167">For example, the following command uses the **File** parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmi/cimv2/Win32_Service -SelectorSet @{Name="spooler"} -File c:\input.xml -Authentication Default`

<span data-ttu-id="0eee8-168">Met deze opdracht wordt de **Stop** service-methode voor de spoolerservice aangeroepen met behulp van invoer uit een bestand.</span><span class="sxs-lookup"><span data-stu-id="0eee8-168">This command calls the **StopService** method on the Spooler service using input from a file.</span></span> <span data-ttu-id="0eee8-169">Het bestand, `Input.xml` , bevat de volgende inhoud:</span><span class="sxs-lookup"><span data-stu-id="0eee8-169">The file, `Input.xml`, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eee8-170">-Optieset</span><span class="sxs-lookup"><span data-stu-id="0eee8-170">-OptionSet</span></span>

<span data-ttu-id="0eee8-171">Hiermee wordt een set switches door gegeven aan een service om de aard van de aanvraag te wijzigen of te verfijnen.</span><span class="sxs-lookup"><span data-stu-id="0eee8-171">Passes a set of switches to a service to modify or refine the nature of the request.</span></span> <span data-ttu-id="0eee8-172">Deze zijn vergelijkbaar met de switches die worden gebruikt in opdracht regel shells, omdat deze service-specifiek zijn.</span><span class="sxs-lookup"><span data-stu-id="0eee8-172">These are similar to switches used in command-line shells because they are service specific.</span></span> <span data-ttu-id="0eee8-173">U kunt een wille keurig aantal opties opgeven.</span><span class="sxs-lookup"><span data-stu-id="0eee8-173">Any number of options can be specified.</span></span>

<span data-ttu-id="0eee8-174">In het volgende voor beeld ziet u de syntaxis waarmee de waarden 1, 2 en 3 worden door gegeven voor de para meters a, b en c:</span><span class="sxs-lookup"><span data-stu-id="0eee8-174">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="0eee8-175">-Port</span><span class="sxs-lookup"><span data-stu-id="0eee8-175">-Port</span></span>

<span data-ttu-id="0eee8-176">Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="0eee8-176">Specifies the port to use when the client connects to the WinRM service.</span></span> <span data-ttu-id="0eee8-177">Wanneer het Trans Port HTTP is, is de standaard poort 80.</span><span class="sxs-lookup"><span data-stu-id="0eee8-177">When the transport is HTTP, the default port is 80.</span></span> <span data-ttu-id="0eee8-178">Wanneer het Trans Port HTTPS is, is de standaard poort 443.</span><span class="sxs-lookup"><span data-stu-id="0eee8-178">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="0eee8-179">Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter **ComputerName** overeenkomen met de common name (CN) van het server certificaat.</span><span class="sxs-lookup"><span data-stu-id="0eee8-179">When you use HTTPS as the transport, the value of the **ComputerName** parameter must match the server's certificate common name (CN).</span></span> <span data-ttu-id="0eee8-180">Als de para meter **SkipCNCheck** echter is opgegeven als onderdeel van de **SessionOption** -para meter, moet de algemene naam van het certificaat van de server niet overeenkomen met de hostnaam van de server.</span><span class="sxs-lookup"><span data-stu-id="0eee8-180">However, if the **SkipCNCheck** parameter is specified as part of the **SessionOption** parameter, the certificate common name of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="0eee8-181">De para meter **SkipCNCheck** moet alleen worden gebruikt voor vertrouwde computers.</span><span class="sxs-lookup"><span data-stu-id="0eee8-181">The **SkipCNCheck** parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="0eee8-182">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="0eee8-182">-ResourceURI</span></span>

<span data-ttu-id="0eee8-183">Bevat de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar.</span><span class="sxs-lookup"><span data-stu-id="0eee8-183">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="0eee8-184">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="0eee8-184">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="0eee8-185">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="0eee8-185">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="0eee8-186">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="0eee8-186">For example:</span></span>

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

### <span data-ttu-id="0eee8-187">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="0eee8-187">-SelectorSet</span></span>

<span data-ttu-id="0eee8-188">Hiermee geeft u een set waardeparen op die worden gebruikt om bepaalde beheer resource-instanties te selecteren.</span><span class="sxs-lookup"><span data-stu-id="0eee8-188">Specifies a set of value pairs that are used to select particular management resource instances.</span></span> <span data-ttu-id="0eee8-189">De para meter **SelectorSet** wordt gebruikt wanneer er meer dan één exemplaar van de bron bestaat.</span><span class="sxs-lookup"><span data-stu-id="0eee8-189">The **SelectorSet** parameter is used when more than one instance of the resource exists.</span></span> <span data-ttu-id="0eee8-190">De waarde van de para meter **SelectorSet** moet een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="0eee8-190">The value of the **SelectorSet** parameter must be a hash table.</span></span>

<span data-ttu-id="0eee8-191">In het volgende voor beeld ziet u hoe u een waarde voor deze para meter opgeeft:</span><span class="sxs-lookup"><span data-stu-id="0eee8-191">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0eee8-192">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="0eee8-192">-SessionOption</span></span>

<span data-ttu-id="0eee8-193">Hiermee definieert u een set uitgebreide opties voor de WS-Management sessie.</span><span class="sxs-lookup"><span data-stu-id="0eee8-193">Defines a set of extended options for the WS-Management session.</span></span> <span data-ttu-id="0eee8-194">Voer een **SessionOption** -object in dat u maakt met behulp van de `New-WSManSessionOption` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0eee8-194">Enter a **SessionOption** object that you create using the `New-WSManSessionOption` cmdlet.</span></span> <span data-ttu-id="0eee8-195">Zie voor meer informatie over de beschik bare opties `New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="0eee8-195">For more information about the options that are available, see `New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="0eee8-196">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="0eee8-196">-UseSSL</span></span>

<span data-ttu-id="0eee8-197">Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) moet worden gebruikt om een verbinding met de externe computer tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="0eee8-197">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="0eee8-198">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0eee8-198">By default, SSL is not used.</span></span>

<span data-ttu-id="0eee8-199">WS-Management versleutelt alle Windows Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="0eee8-199">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="0eee8-200">Met de para meter **UseSSL** kunt u de extra beveiliging van https in plaats van http opgeven.</span><span class="sxs-lookup"><span data-stu-id="0eee8-200">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="0eee8-201">Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="0eee8-201">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="0eee8-202">-Waardeset</span><span class="sxs-lookup"><span data-stu-id="0eee8-202">-ValueSet</span></span>

<span data-ttu-id="0eee8-203">Hiermee geeft u een hash-tabel op waarmee u een beheer bron kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="0eee8-203">Specifies a hash table that helps modify a management resource.</span></span> <span data-ttu-id="0eee8-204">U geeft de beheer resource op met behulp van de para meter **ResourceURI** en de para meter **SelectorSet** .</span><span class="sxs-lookup"><span data-stu-id="0eee8-204">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter.</span></span> <span data-ttu-id="0eee8-205">De waarde van de para meter voor de **waardeset** moet een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="0eee8-205">The value of the **ValueSet** parameter must be a hash table.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eee8-206">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0eee8-206">CommonParameters</span></span>

<span data-ttu-id="0eee8-207">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0eee8-207">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0eee8-208">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0eee8-208">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0eee8-209">INVOER</span><span class="sxs-lookup"><span data-stu-id="0eee8-209">INPUTS</span></span>

### <span data-ttu-id="0eee8-210">Geen</span><span class="sxs-lookup"><span data-stu-id="0eee8-210">None</span></span>

<span data-ttu-id="0eee8-211">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="0eee8-211">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="0eee8-212">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0eee8-212">OUTPUTS</span></span>

### <span data-ttu-id="0eee8-213">Geen</span><span class="sxs-lookup"><span data-stu-id="0eee8-213">None</span></span>

<span data-ttu-id="0eee8-214">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="0eee8-214">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0eee8-215">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0eee8-215">NOTES</span></span>

<span data-ttu-id="0eee8-216">De `Set-WmiInstance` cmdlet, een Windows Management Instrumentation-cmdlet (WMI), is vergelijkbaar.</span><span class="sxs-lookup"><span data-stu-id="0eee8-216">The `Set-WmiInstance` cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span>
<span data-ttu-id="0eee8-217">`Set-WmiInstance` maakt gebruik van de DCOM-verbinding/Trans Port-laag voor het maken of bijwerken van WMI-exemplaren.</span><span class="sxs-lookup"><span data-stu-id="0eee8-217">`Set-WmiInstance` uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

## <span data-ttu-id="0eee8-218">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0eee8-218">RELATED LINKS</span></span>

[<span data-ttu-id="0eee8-219">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="0eee8-219">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="0eee8-220">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="0eee8-220">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="0eee8-221">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="0eee8-221">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="0eee8-222">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="0eee8-222">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="0eee8-223">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="0eee8-223">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="0eee8-224">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="0eee8-224">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="0eee8-225">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="0eee8-225">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="0eee8-226">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="0eee8-226">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="0eee8-227">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="0eee8-227">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="0eee8-228">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="0eee8-228">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="0eee8-229">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="0eee8-229">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="0eee8-230">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="0eee8-230">Test-WSMan</span></span>](Test-WSMan.md)
