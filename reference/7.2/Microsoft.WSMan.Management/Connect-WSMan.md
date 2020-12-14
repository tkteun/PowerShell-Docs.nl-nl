---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/connect-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-WSMan
ms.openlocfilehash: 5dfd0b355a3589bf45ea92b92ae8778023132bcd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706030"
---
# <span data-ttu-id="359c3-102">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="359c3-102">Connect-WSMan</span></span>

## <span data-ttu-id="359c3-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="359c3-103">SYNOPSIS</span></span>
<span data-ttu-id="359c3-104">Maakt verbinding met de WinRM-service op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="359c3-104">Connects to the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="359c3-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="359c3-105">SYNTAX</span></span>

### <span data-ttu-id="359c3-106">Computer naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="359c3-106">ComputerName (Default)</span></span>

```
Connect-WSMan [-ApplicationName <String>] [[-ComputerName] <String>] [-OptionSet <Hashtable>] [-Port <Int32>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="359c3-107">URI</span><span class="sxs-lookup"><span data-stu-id="359c3-107">URI</span></span>

```
Connect-WSMan [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-Port <Int32>] [-SessionOption <SessionOption>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="359c3-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="359c3-108">DESCRIPTION</span></span>
<span data-ttu-id="359c3-109">De cmdlet **Connect-WSMan** maakt verbinding met de WinRM-service op een externe computer en brengt een permanente verbinding met de externe computer tot stand.</span><span class="sxs-lookup"><span data-stu-id="359c3-109">The **Connect-WSMan** cmdlet connects to the WinRM service on a remote computer, and it establishes a persistent connection to the remote computer.</span></span>
<span data-ttu-id="359c3-110">U kunt deze cmdlet in de context van de WSMan-provider gebruiken om verbinding te maken met de WinRM-service op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="359c3-110">You can use this cmdlet in the context of the WSMan provider to connect to the WinRM service on a remote computer.</span></span>
<span data-ttu-id="359c3-111">U kunt deze cmdlet echter ook gebruiken om verbinding te maken met de WinRM-service op een externe computer voordat u overschakelt naar de WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="359c3-111">However, you can also use this cmdlet to connect to the WinRM service on a remote computer before you change to the WSMan provider.</span></span>
<span data-ttu-id="359c3-112">De externe computer wordt weer gegeven in de hoofdmap van de WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="359c3-112">The remote computer appears in the root directory of the WSMan provider.</span></span>

<span data-ttu-id="359c3-113">Expliciete referenties zijn vereist wanneer de client-en Server computers zich in verschillende domeinen of werk groepen bevinden.</span><span class="sxs-lookup"><span data-stu-id="359c3-113">Explicit credentials are required when the client and server computers are in different domains or workgroups.</span></span>

<span data-ttu-id="359c3-114">Voor informatie over het verbreken van de verbinding met de WinRM-service op een externe computer, raadpleegt u de Disconnect-WSMan-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="359c3-114">For information about how to disconnect from the WinRM service on a remote computer, see the Disconnect-WSMan cmdlet.</span></span>

## <span data-ttu-id="359c3-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="359c3-115">EXAMPLES</span></span>

### <span data-ttu-id="359c3-116">Voor beeld 1: verbinding maken met een externe computer</span><span class="sxs-lookup"><span data-stu-id="359c3-116">Example 1: Connect to a remote computer</span></span>

```
PS C:\> Connect-WSMan -ComputerName "server01"
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="359c3-117">Met deze opdracht maakt u een verbinding met de externe Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="359c3-117">This command creates a connection to the remote server01 computer.</span></span>

<span data-ttu-id="359c3-118">De cmdlet **Connect-wsman** wordt doorgaans gebruikt in de context van de wsman-provider om verbinding te maken met een externe computer, in dit geval de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="359c3-118">The **Connect-WSMan** cmdlet is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="359c3-119">U kunt de cmdlet echter gebruiken om verbindingen met externe computers tot stand te brengen voordat u overschakelt naar de WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="359c3-119">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="359c3-120">Deze verbindingen worden weer gegeven in de lijst **computer naam** .</span><span class="sxs-lookup"><span data-stu-id="359c3-120">Those connections appear in the **ComputerName** list.</span></span>

### <span data-ttu-id="359c3-121">Voor beeld 2: verbinding maken met een externe computer met behulp van beheerders referenties</span><span class="sxs-lookup"><span data-stu-id="359c3-121">Example 2: Connect to a remote computer by using Administrator credentials</span></span>

```
PS C:\> $cred = Get-Credential Administrator
PS C:\> Connect-WSMan -ComputerName "server01" -Credential $cred
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="359c3-122">Met deze opdracht maakt u een verbinding met de Server01 van het externe systeem met behulp van de referenties van het beheerders account.</span><span class="sxs-lookup"><span data-stu-id="359c3-122">This command creates a connection to the remote system server01 using the Administrator account credentials.</span></span>

<span data-ttu-id="359c3-123">De eerste opdracht gebruikt de cmdlet Get-Credential om de beheerders referenties op te halen en deze vervolgens op te slaan in de $cred variabele.</span><span class="sxs-lookup"><span data-stu-id="359c3-123">The first command uses the Get-Credential cmdlet to get the Administrator credentials and then stores them in the $cred variable.</span></span>
<span data-ttu-id="359c3-124">**Get-Credential** vraagt u om een wacht woord van gebruikers naam en wacht woord via een dialoog venster of via de opdracht regel, afhankelijk van de instellingen van het systeem register.</span><span class="sxs-lookup"><span data-stu-id="359c3-124">**Get-Credential** prompts you for a password of username and password through a dialog box or at the command line, depending on system registry settings.</span></span>

<span data-ttu-id="359c3-125">Met de tweede opdracht wordt de *referentie* parameter gebruikt voor het door geven van de referenties die zijn opgeslagen in $cred om **verbinding te maken-WSMan**.</span><span class="sxs-lookup"><span data-stu-id="359c3-125">The second command uses the *Credential* parameter to pass the credentials stored in $cred to **Connect-WSMan**.</span></span>
<span data-ttu-id="359c3-126">**Connect: WSMan** maakt vervolgens verbinding met de Server01 van het externe systeem met behulp van de referenties van de beheerder.</span><span class="sxs-lookup"><span data-stu-id="359c3-126">**Connect-WSMan** then connects to the remote system server01 by using the Administrator credentials.</span></span>

### <span data-ttu-id="359c3-127">Voor beeld 3: verbinding maken met een externe computer via een opgegeven poort</span><span class="sxs-lookup"><span data-stu-id="359c3-127">Example 3: Connect to a remote computer over a specified port</span></span>

```
PS C:\> Connect-WSMan -ComputerName "server01" -Port 80
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="359c3-128">Met deze opdracht maakt u een verbinding met de externe Server01-computer via poort 80.</span><span class="sxs-lookup"><span data-stu-id="359c3-128">This command creates a connection to the remote server01 computer over port 80.</span></span>

### <span data-ttu-id="359c3-129">Voor beeld 4: verbinding maken met een externe computer via verbindings opties</span><span class="sxs-lookup"><span data-stu-id="359c3-129">Example 4: Connect to a remote computer by using connection options</span></span>

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="359c3-130">In dit voor beeld wordt een verbinding met de externe Server01-computer gemaakt met behulp van de verbindings opties die zijn gedefinieerd in de opdracht **New-WSManSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="359c3-130">This example creates a connection to the remote server01 computer by using the connection options that are defined in the **New-WSManSessionOption** command.</span></span>

<span data-ttu-id="359c3-131">De eerste opdracht maakt gebruik van **New-WSManSessionOption** voor het opslaan van een set opties voor Verbindings instellingen in de variabele $a.</span><span class="sxs-lookup"><span data-stu-id="359c3-131">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="359c3-132">In dit geval stelt de sessie opties een verbindings tijd in van 30 seconden (30.000 milliseconden).</span><span class="sxs-lookup"><span data-stu-id="359c3-132">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="359c3-133">De tweede opdracht gebruikt de para meter *SessionOption* om de referenties door te geven die zijn opgeslagen in de $a variabele om **verbinding te maken-WSMan**.</span><span class="sxs-lookup"><span data-stu-id="359c3-133">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan**.</span></span>
<span data-ttu-id="359c3-134">**Connect-WSMan** maakt verbinding met de externe Server01-computer met behulp van de opgegeven sessie opties.</span><span class="sxs-lookup"><span data-stu-id="359c3-134">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

## <span data-ttu-id="359c3-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="359c3-135">PARAMETERS</span></span>

### <span data-ttu-id="359c3-136">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="359c3-136">-ApplicationName</span></span>
<span data-ttu-id="359c3-137">Hiermee geeft u de naam van de toepassing in de verbinding.</span><span class="sxs-lookup"><span data-stu-id="359c3-137">Specifies the application name in the connection.</span></span>
<span data-ttu-id="359c3-138">De standaard waarde van de para meter *ApplicationName* is WSMAN.</span><span class="sxs-lookup"><span data-stu-id="359c3-138">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="359c3-139">De volledige id voor het externe eind punt heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="359c3-139">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="359c3-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="359c3-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="359c3-141">Bijvoorbeeld: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="359c3-141">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="359c3-142">Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="359c3-142">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="359c3-143">Deze standaard instelling van WSMAN is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="359c3-143">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="359c3-144">Deze para meter is ontworpen om te worden gebruikt als veel computers externe verbindingen tot stand brengen met één computer waarop Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="359c3-144">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="359c3-145">In dit geval wordt IIS gehost Web Services for Management (WS-Management) voor efficiëntie.</span><span class="sxs-lookup"><span data-stu-id="359c3-145">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="359c3-146">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="359c3-146">-Authentication</span></span>
<span data-ttu-id="359c3-147">Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server.</span><span class="sxs-lookup"><span data-stu-id="359c3-147">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="359c3-148">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="359c3-148">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="359c3-149">Hoofd.</span><span class="sxs-lookup"><span data-stu-id="359c3-149">Basic.</span></span>
<span data-ttu-id="359c3-150">Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="359c3-150">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="359c3-151">Standaard.</span><span class="sxs-lookup"><span data-stu-id="359c3-151">Default.</span></span>
<span data-ttu-id="359c3-152">Gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol.</span><span class="sxs-lookup"><span data-stu-id="359c3-152">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="359c3-153">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="359c3-153">This is the default.</span></span>
- <span data-ttu-id="359c3-154">Vatting.</span><span class="sxs-lookup"><span data-stu-id="359c3-154">Digest.</span></span>
<span data-ttu-id="359c3-155">Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.</span><span class="sxs-lookup"><span data-stu-id="359c3-155">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="359c3-156">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="359c3-156">Kerberos.</span></span>
<span data-ttu-id="359c3-157">De client computer en de server worden wederzijds geverifieerd met behulp van Kerberos-certificaten.</span><span class="sxs-lookup"><span data-stu-id="359c3-157">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="359c3-158">Afspraken.</span><span class="sxs-lookup"><span data-stu-id="359c3-158">Negotiate.</span></span>
<span data-ttu-id="359c3-159">Onderhandelen is een vraag/antwoord-schema waarmee wordt onderhandeld over de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="359c3-159">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="359c3-160">Met deze parameter waarde kan bijvoorbeeld worden geonderhandelingd om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="359c3-160">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="359c3-161">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="359c3-161">CredSSP.</span></span>
<span data-ttu-id="359c3-162">Gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren.</span><span class="sxs-lookup"><span data-stu-id="359c3-162">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="359c3-163">Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="359c3-163">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="359c3-164">Let op: CredSSP delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="359c3-164">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="359c3-165">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="359c3-165">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="359c3-166">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="359c3-166">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="359c3-167">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="359c3-167">-CertificateThumbprint</span></span>
<span data-ttu-id="359c3-168">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="359c3-168">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="359c3-169">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="359c3-169">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="359c3-170">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="359c3-170">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="359c3-171">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="359c3-171">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="359c3-172">Als u een certificaat vingerafdruk wilt krijgen, gebruikt u de opdracht Get-Item of Get-ChildItem in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="359c3-172">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="359c3-173">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="359c3-173">-ComputerName</span></span>
<span data-ttu-id="359c3-174">Hiermee geeft u de computer op waarop de beheer bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="359c3-174">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="359c3-175">De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.</span><span class="sxs-lookup"><span data-stu-id="359c3-175">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="359c3-176">Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="359c3-176">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="359c3-177">De lokale computer is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="359c3-177">The local computer is the default.</span></span>
<span data-ttu-id="359c3-178">Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.</span><span class="sxs-lookup"><span data-stu-id="359c3-178">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="359c3-179">U kunt een waarde voor deze para meter door geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="359c3-179">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="359c3-180">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="359c3-180">-ConnectionURI</span></span>
<span data-ttu-id="359c3-181">Hiermee geeft u het eind punt van de verbinding.</span><span class="sxs-lookup"><span data-stu-id="359c3-181">Specifies the connection endpoint.</span></span>
<span data-ttu-id="359c3-182">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="359c3-182">The format of this string is as follows:</span></span>

<span data-ttu-id="359c3-183">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="359c3-183">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="359c3-184">De volgende teken reeks is een correct ingedeelde waarde voor deze para meter:</span><span class="sxs-lookup"><span data-stu-id="359c3-184">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="359c3-185">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="359c3-185">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="359c3-186">-Credential</span><span class="sxs-lookup"><span data-stu-id="359c3-186">-Credential</span></span>
<span data-ttu-id="359c3-187">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="359c3-187">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="359c3-188">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="359c3-188">The default is the current user.</span></span>
<span data-ttu-id="359c3-189">Typ een gebruikers naam, zoals gebruiker01, Domain01\User01 of User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="359c3-189">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="359c3-190">U kunt ook een **PSCredential** -object invoeren, zoals het dat wordt geretourneerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="359c3-190">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="359c3-191">Wanneer u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="359c3-191">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="359c3-192">-Optieset</span><span class="sxs-lookup"><span data-stu-id="359c3-192">-OptionSet</span></span>
<span data-ttu-id="359c3-193">Hiermee geeft u een set switches naar een service op om de aard van de aanvraag te wijzigen of te verfijnen.</span><span class="sxs-lookup"><span data-stu-id="359c3-193">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="359c3-194">Deze lijken op de Schakel opties die worden gebruikt in opdracht regel shells, omdat deze service-specifiek zijn.</span><span class="sxs-lookup"><span data-stu-id="359c3-194">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="359c3-195">U kunt een wille keurig aantal opties opgeven.</span><span class="sxs-lookup"><span data-stu-id="359c3-195">Any number of options can be specified.</span></span>

<span data-ttu-id="359c3-196">In het volgende voor beeld ziet u de syntaxis waarmee de waarden 1, 2 en 3 worden door gegeven voor de para meters a, b en c:</span><span class="sxs-lookup"><span data-stu-id="359c3-196">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="359c3-197">-Port</span><span class="sxs-lookup"><span data-stu-id="359c3-197">-Port</span></span>
<span data-ttu-id="359c3-198">Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="359c3-198">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="359c3-199">Wanneer het Trans Port HTTP is, is de standaard poort 80.</span><span class="sxs-lookup"><span data-stu-id="359c3-199">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="359c3-200">Wanneer het Trans Port HTTPS is, is de standaard poort 443.</span><span class="sxs-lookup"><span data-stu-id="359c3-200">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="359c3-201">Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter *ComputerName* overeenkomen met de common name (CN) van het server certificaat.</span><span class="sxs-lookup"><span data-stu-id="359c3-201">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="359c3-202">Als de para meter *SkipCNCheck* echter is opgegeven als onderdeel van de *SessionOption* -para meter, moet de algemene naam van het certificaat van de server niet overeenkomen met de hostnaam van de server.</span><span class="sxs-lookup"><span data-stu-id="359c3-202">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="359c3-203">De para meter *SkipCNCheck* moet alleen worden gebruikt voor vertrouwde computers.</span><span class="sxs-lookup"><span data-stu-id="359c3-203">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="359c3-204">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="359c3-204">-SessionOption</span></span>
<span data-ttu-id="359c3-205">Hiermee worden uitgebreide opties voor de WS-Management-sessie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="359c3-205">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="359c3-206">Voer een **SessionOption** -object in dat u maakt met behulp van de cmdlet New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="359c3-206">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="359c3-207">Typ voor meer informatie over de beschik bare opties `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="359c3-207">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="359c3-208">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="359c3-208">-UseSSL</span></span>
<span data-ttu-id="359c3-209">Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) wordt gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="359c3-209">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="359c3-210">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="359c3-210">By default, SSL is not used.</span></span>

<span data-ttu-id="359c3-211">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="359c3-211">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="359c3-212">Met de para meter *UseSSL* kunt u de extra beveiliging van https in plaats van http opgeven.</span><span class="sxs-lookup"><span data-stu-id="359c3-212">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="359c3-213">Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="359c3-213">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="359c3-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="359c3-214">CommonParameters</span></span>
<span data-ttu-id="359c3-215">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="359c3-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="359c3-216">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="359c3-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="359c3-217">INVOER</span><span class="sxs-lookup"><span data-stu-id="359c3-217">INPUTS</span></span>

### <span data-ttu-id="359c3-218">Geen</span><span class="sxs-lookup"><span data-stu-id="359c3-218">None</span></span>
<span data-ttu-id="359c3-219">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="359c3-219">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="359c3-220">UITVOER</span><span class="sxs-lookup"><span data-stu-id="359c3-220">OUTPUTS</span></span>

### <span data-ttu-id="359c3-221">Geen</span><span class="sxs-lookup"><span data-stu-id="359c3-221">None</span></span>
<span data-ttu-id="359c3-222">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="359c3-222">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="359c3-223">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="359c3-223">NOTES</span></span>

* <span data-ttu-id="359c3-224">U kunt beheer opdrachten of query beheer gegevens uitvoeren op een externe computer zonder een WS-Management sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="359c3-224">You can run management commands or query management data on a remote computer without creating a WS-Management session.</span></span> <span data-ttu-id="359c3-225">U kunt dit doen met behulp van de para meters van de *computer naam* van Invoke-WSManAction en Get-WSManInstance.</span><span class="sxs-lookup"><span data-stu-id="359c3-225">You can do this by using the *ComputerName* parameters of Invoke-WSManAction and Get-WSManInstance.</span></span> <span data-ttu-id="359c3-226">Wanneer u de para meter *ComputerName* gebruikt, maakt Power shell een tijdelijke verbinding die wordt gebruikt voor de afzonderlijke opdracht.</span><span class="sxs-lookup"><span data-stu-id="359c3-226">When you use the *ComputerName* parameter, PowerShell creates a temporary connection that is used for the single command.</span></span> <span data-ttu-id="359c3-227">Nadat de opdracht is uitgevoerd, wordt de verbinding gesloten.</span><span class="sxs-lookup"><span data-stu-id="359c3-227">After the command runs, the connection is closed.</span></span>

*

## <span data-ttu-id="359c3-228">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="359c3-228">RELATED LINKS</span></span>

[<span data-ttu-id="359c3-229">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="359c3-229">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="359c3-230">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="359c3-230">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="359c3-231">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="359c3-231">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="359c3-232">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="359c3-232">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="359c3-233">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="359c3-233">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="359c3-234">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="359c3-234">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="359c3-235">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="359c3-235">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="359c3-236">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="359c3-236">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="359c3-237">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="359c3-237">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="359c3-238">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="359c3-238">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="359c3-239">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="359c3-239">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="359c3-240">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="359c3-240">Test-WSMan</span></span>](Test-WSMan.md)

