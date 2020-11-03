---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 3f4ee9edf6e8dfce21a51ff9c055fe56a0cbef3c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251570"
---
# <span data-ttu-id="3e6b1-103">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e6b1-103">Set-WSManInstance</span></span>

## <span data-ttu-id="3e6b1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3e6b1-104">SYNOPSIS</span></span>
<span data-ttu-id="3e6b1-105">Hiermee wijzigt u de beheer gegevens die zijn gerelateerd aan een resource.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-105">Modifies the management information that is related to a resource.</span></span>

## <span data-ttu-id="3e6b1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3e6b1-106">SYNTAX</span></span>

### <span data-ttu-id="3e6b1-107">Computer naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="3e6b1-107">ComputerName (Default)</span></span>

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="3e6b1-108">URI</span><span class="sxs-lookup"><span data-stu-id="3e6b1-108">URI</span></span>

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="3e6b1-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3e6b1-109">DESCRIPTION</span></span>

<span data-ttu-id="3e6b1-110">Met de cmdlet Set-WSManInstance worden de beheer gegevens van een resource gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-110">The Set-WSManInstance cmdlet modifies the management information that is related to a resource.</span></span>

<span data-ttu-id="3e6b1-111">Deze cmdlet maakt gebruik van de WinRM-verbinding/Trans Port-laag voor het wijzigen van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-111">This cmdlet uses the WinRM connection/transport layer to modify the information.</span></span>

## <span data-ttu-id="3e6b1-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3e6b1-112">EXAMPLES</span></span>

### <span data-ttu-id="3e6b1-113">Voor beeld 1: een listener op de lokale computer uitschakelen</span><span class="sxs-lookup"><span data-stu-id="3e6b1-113">Example 1: Disable a listener on the local computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.171, ::1, 2001:4898:0:fff:0:5efe:172.30.168.171...}
```

<span data-ttu-id="3e6b1-114">Met deze opdracht wordt de https-listener op de lokale computer uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-114">This command disables the https listener on the local computer.</span></span>

<span data-ttu-id="3e6b1-115">Belang rijk: de *waardeset* -para meter is hoofdletter gevoelig bij het vergelijken van de opgegeven eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-115">Important: The *ValueSet* parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="3e6b1-116">In deze opdracht bijvoorbeeld</span><span class="sxs-lookup"><span data-stu-id="3e6b1-116">For example, in this command,</span></span>

<span data-ttu-id="3e6b1-117">Dit mislukt: `-ValueSet @{enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="3e6b1-117">This fails: `-ValueSet @{enabled="False"}`</span></span>

<span data-ttu-id="3e6b1-118">Dit is geslaagd: `-ValueSet @{Enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="3e6b1-118">This succeeds: `-ValueSet @{Enabled="False"}`</span></span>

### <span data-ttu-id="3e6b1-119">Voor beeld 2: de maximale envelop grootte op de lokale computer instellen</span><span class="sxs-lookup"><span data-stu-id="3e6b1-119">Example 2: Set the maximum envelope size on the local computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config -ValueSet @{MaxEnvelopeSizekb = "200"}
```

```Output
cfg                 : http://schemas.microsoft.com/wbem/wsman/1/config
lang                : en-US
MaxEnvelopeSizekb   : 200
MaxTimeoutms        : 60000
MaxBatchItems       : 32000
MaxProviderRequests : 4294967295
Client              : Client
Service             : Service
Winrs               : Winrs
```

<span data-ttu-id="3e6b1-120">Met deze opdracht wordt de waarde voor MaxEnvelopeSizekb ingesteld op 200 op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-120">This command sets the MaxEnvelopeSizekb value to 200 on the local computer.</span></span>

<span data-ttu-id="3e6b1-121">Belang rijk: de waardeset-para meter is hoofdletter gevoelig bij het vergelijken van de opgegeven eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-121">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="3e6b1-122">Gebruik bijvoorbeeld de bovenstaande opdracht.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-122">For example, using the above command.</span></span>

<span data-ttu-id="3e6b1-123">Dit mislukt:-waardeset @ {MaxEnvelopeSizeKB = "200"}</span><span class="sxs-lookup"><span data-stu-id="3e6b1-123">This fails:     -ValueSet @{MaxEnvelopeSizeKB ="200"}</span></span>

<span data-ttu-id="3e6b1-124">Dit is het volgende:-values-waarde @ {MaxEnvelopeSizekb = "200"}</span><span class="sxs-lookup"><span data-stu-id="3e6b1-124">This succeeds:  -ValueSet @{MaxEnvelopeSizekb ="200"}</span></span>

### <span data-ttu-id="3e6b1-125">Voor beeld 3: een listener op een externe computer uitschakelen</span><span class="sxs-lookup"><span data-stu-id="3e6b1-125">Example 3: Disable a listener on a remote computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -ComputerName SERVER02 -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.172, ::1, 2001:4898:0:fff:0:5efe:172.30.168.172...}
```

<span data-ttu-id="3e6b1-126">Met deze opdracht wordt de https-listener op de externe computer SERVER02 uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-126">This command disables the https listener on the remote computer SERVER02.</span></span>

<span data-ttu-id="3e6b1-127">Belang rijk: de waardeset-para meter is hoofdletter gevoelig bij het vergelijken van de opgegeven eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-127">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="3e6b1-128">Gebruik bijvoorbeeld de bovenstaande opdracht.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-128">For example, using the above command.</span></span>

<span data-ttu-id="3e6b1-129">Dit mislukt:-values @ {enabled = "false"}</span><span class="sxs-lookup"><span data-stu-id="3e6b1-129">This fails:     -ValueSet @{enabled="False"}</span></span>

<span data-ttu-id="3e6b1-130">Dit is het volgende:-values-waarde @ {enabled = "false"}</span><span class="sxs-lookup"><span data-stu-id="3e6b1-130">This succeeds:  -ValueSet @{Enabled="False"}</span></span>

## <span data-ttu-id="3e6b1-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3e6b1-131">PARAMETERS</span></span>

### <span data-ttu-id="3e6b1-132">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="3e6b1-132">-ApplicationName</span></span>

<span data-ttu-id="3e6b1-133">Hiermee geeft u de naam van de toepassing in de verbinding.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-133">Specifies the application name in the connection.</span></span>
<span data-ttu-id="3e6b1-134">De standaard waarde van de para meter ApplicationName is WSMAN.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-134">The default value of the ApplicationName parameter is "WSMAN".</span></span>
<span data-ttu-id="3e6b1-135">De volledige id voor het externe eind punt heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="3e6b1-135">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="3e6b1-136">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="3e6b1-136">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="3e6b1-137">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="3e6b1-137">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="3e6b1-138">Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-138">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="3e6b1-139">Deze standaard instelling van ' WSMAN ' is geschikt voor de meeste doel einden.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-139">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="3e6b1-140">Deze para meter is ontworpen om te worden gebruikt wanneer talloze computers externe verbindingen tot stand brengen met één computer met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-140">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span>
<span data-ttu-id="3e6b1-141">In dit geval wordt IIS gehost Web Services for Management (WS-Management) voor efficiëntie.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-141">In this case, IIS hosts Web Services for Management (WS-Management ) for efficiency.</span></span>

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

### <span data-ttu-id="3e6b1-142">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="3e6b1-142">-Authentication</span></span>

<span data-ttu-id="3e6b1-143">Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-143">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="3e6b1-144">Mogelijke waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="3e6b1-144">Possible values are:</span></span>

- <span data-ttu-id="3e6b1-145">Basic: Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-145">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="3e6b1-146">Standaard: gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-146">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="3e6b1-147">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-147">This is the default.</span></span>
- <span data-ttu-id="3e6b1-148">Digest: Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-148">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="3e6b1-149">Kerberos: de client computer en de server worden wederzijds geverifieerd met behulp van Kerberos-certificaten.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-149">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="3e6b1-150">Onderhandelen: onderhandelen is een vraag/antwoord-schema dat onderhandelt met de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-150">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="3e6b1-151">Deze parameter waarde kan bijvoorbeeld onderhandelen om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-151">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="3e6b1-152">CredSSP: gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-152">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="3e6b1-153">Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-153">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="3e6b1-154">Let op: CredSSP delegeert de referenties van de gebruiker van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-154">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="3e6b1-155">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-155">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="3e6b1-156">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-156">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e6b1-157">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="3e6b1-157">-CertificateThumbprint</span></span>

<span data-ttu-id="3e6b1-158">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-158">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="3e6b1-159">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-159">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="3e6b1-160">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-160">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="3e6b1-161">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-161">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="3e6b1-162">Als u een certificaat vingerafdruk wilt krijgen, gebruikt u de opdracht Get-Item of Get-ChildItem in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-162">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="3e6b1-163">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3e6b1-163">-ComputerName</span></span>

<span data-ttu-id="3e6b1-164">Hiermee geeft u de computer op waartegen u de beheer bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-164">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="3e6b1-165">De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-165">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="3e6b1-166">Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-166">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="3e6b1-167">De lokale computer is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-167">The local computer is the default.</span></span>
<span data-ttu-id="3e6b1-168">Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-168">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="3e6b1-169">U kunt een waarde voor deze para meter door geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-169">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="3e6b1-170">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="3e6b1-170">-ConnectionURI</span></span>

<span data-ttu-id="3e6b1-171">Hiermee geeft u het eind punt van de verbinding.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-171">Specifies the connection endpoint.</span></span>
<span data-ttu-id="3e6b1-172">De notatie van deze teken reeks is:</span><span class="sxs-lookup"><span data-stu-id="3e6b1-172">The format of this string is:</span></span>

<span data-ttu-id="3e6b1-173">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="3e6b1-173">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="3e6b1-174">De volgende teken reeks is een correct ingedeelde waarde voor deze para meter:</span><span class="sxs-lookup"><span data-stu-id="3e6b1-174">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="3e6b1-175">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-175">The URI must be fully qualified .</span></span>

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

### <span data-ttu-id="3e6b1-176">-Credential</span><span class="sxs-lookup"><span data-stu-id="3e6b1-176">-Credential</span></span>

<span data-ttu-id="3e6b1-177">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-177">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="3e6b1-178">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-178">The default is the current user.</span></span>
<span data-ttu-id="3e6b1-179">Typ een gebruikers naam, zoals "gebruiker01", "Domain01\User01" of " User@Domain.com ".</span><span class="sxs-lookup"><span data-stu-id="3e6b1-179">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span>
<span data-ttu-id="3e6b1-180">U kunt ook een PSCredential-object invoeren, zoals het dat wordt geretourneerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-180">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="3e6b1-181">Wanneer u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-181">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="3e6b1-182">-Dialect</span><span class="sxs-lookup"><span data-stu-id="3e6b1-182">-Dialect</span></span>

<span data-ttu-id="3e6b1-183">Hiermee geeft u het dialect op dat moet worden gebruikt in het filter predicaat.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-183">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="3e6b1-184">Dit kan elk dialect zijn dat wordt ondersteund door de externe service.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-184">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="3e6b1-185">De volgende aliassen kunnen worden gebruikt voor de dialect-URI:</span><span class="sxs-lookup"><span data-stu-id="3e6b1-185">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="3e6b1-186">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="3e6b1-186">WQL: `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="3e6b1-187">Selector `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="3e6b1-187">Selector: `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="3e6b1-188">Organisatie `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="3e6b1-188">Association: `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: http://schemas.microsoft.com/wbem/wsman/1/WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e6b1-189">-FilePath</span><span class="sxs-lookup"><span data-stu-id="3e6b1-189">-FilePath</span></span>

<span data-ttu-id="3e6b1-190">Hiermee geeft u het pad op van een bestand dat wordt gebruikt om een beheer bron bij te werken.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-190">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="3e6b1-191">U geeft de beheer bron op met behulp van de para meter ResourceURI en de para meter SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-191">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter .</span></span>
<span data-ttu-id="3e6b1-192">De volgende opdracht maakt bijvoorbeeld gebruik van de FilePath-para meter:</span><span class="sxs-lookup"><span data-stu-id="3e6b1-192">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

<span data-ttu-id="3e6b1-193">Met deze opdracht wordt de stop service-methode voor de spooler aangeroepen met behulp van invoer vanuit een bestand.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-193">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="3e6b1-194">Het bestand, Input.xml, bevat de volgende inhoud:</span><span class="sxs-lookup"><span data-stu-id="3e6b1-194">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e6b1-195">-Fragment</span><span class="sxs-lookup"><span data-stu-id="3e6b1-195">-Fragment</span></span>

<span data-ttu-id="3e6b1-196">Hiermee geeft u een sectie in het exemplaar op dat moet worden bijgewerkt of opgehaald voor de opgegeven bewerking.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-196">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="3e6b1-197">Als u bijvoorbeeld de status van een Spooler-service wilt ophalen, geeft u '-fragment status ' op.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-197">For example, to get the status of a spooler service, specify "-Fragment Status".</span></span>

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

### <span data-ttu-id="3e6b1-198">-Optieset</span><span class="sxs-lookup"><span data-stu-id="3e6b1-198">-OptionSet</span></span>

<span data-ttu-id="3e6b1-199">Hiermee wordt een set switches door gegeven aan een service om de aard van de aanvraag te wijzigen of te verfijnen.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-199">Passes a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="3e6b1-200">Deze zijn vergelijkbaar met de switches die worden gebruikt in opdracht regel shells, omdat deze service-specifiek zijn.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-200">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="3e6b1-201">U kunt een wille keurig aantal opties opgeven.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-201">Any number of options can be specified.</span></span>

<span data-ttu-id="3e6b1-202">In het volgende voor beeld ziet u de syntaxis waarmee de waarden 1, 2 en 3 worden door gegeven voor de para meters a, b en c:</span><span class="sxs-lookup"><span data-stu-id="3e6b1-202">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

<span data-ttu-id="3e6b1-203">-Optieset @ {a = 1; b = 2; c = 3}</span><span class="sxs-lookup"><span data-stu-id="3e6b1-203">-OptionSet @{a=1;b=2;c=3}</span></span>

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

### <span data-ttu-id="3e6b1-204">-Port</span><span class="sxs-lookup"><span data-stu-id="3e6b1-204">-Port</span></span>

<span data-ttu-id="3e6b1-205">Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-205">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="3e6b1-206">Wanneer het Trans Port HTTP is, is de standaard poort 80.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-206">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="3e6b1-207">Wanneer het Trans Port HTTPS is, is de standaard poort 443.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-207">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="3e6b1-208">Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter ComputerName overeenkomen met de common name (CN) van het server certificaat.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-208">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="3e6b1-209">Als de para meter SkipCNCheck echter is opgegeven als onderdeel van de para meter SessionOption, moet de algemene naam van het certificaat van de server niet overeenkomen met de hostnaam van de server.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-209">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="3e6b1-210">De para meter SkipCNCheck moet alleen worden gebruikt voor vertrouwde computers.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-210">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="3e6b1-211">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="3e6b1-211">-ResourceURI</span></span>

<span data-ttu-id="3e6b1-212">Bevat de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-212">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="3e6b1-213">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-213">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="3e6b1-214">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-214">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="3e6b1-215">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="3e6b1-215">For example:</span></span>

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

### <span data-ttu-id="3e6b1-216">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="3e6b1-216">-SelectorSet</span></span>

<span data-ttu-id="3e6b1-217">Hiermee geeft u een set waardeparen op die worden gebruikt om bepaalde beheer resource-instanties te selecteren.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-217">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="3e6b1-218">De para meter SelectorSet wordt gebruikt wanneer er meer dan één exemplaar van de bron bestaat.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-218">The SelectorSet parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="3e6b1-219">De waarde van de para meter SelectorSet moet een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-219">The value of the SelectorSet parameter must be a hash table.</span></span>
<span data-ttu-id="3e6b1-220">In het volgende voor beeld ziet u hoe u een waarde voor deze para meter opgeeft:</span><span class="sxs-lookup"><span data-stu-id="3e6b1-220">The following example shows how to enter a value for this parameter:</span></span>

<span data-ttu-id="3e6b1-221">-SelectorSet @ {name = "WinRM"; ID = "yyy"}</span><span class="sxs-lookup"><span data-stu-id="3e6b1-221">-SelectorSet @{Name="WinRM";ID="yyy"}</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3e6b1-222">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="3e6b1-222">-SessionOption</span></span>

<span data-ttu-id="3e6b1-223">Hiermee definieert u een set uitgebreide opties voor de WS-Management sessie.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-223">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="3e6b1-224">Voer een SessionOption-object in dat u maakt met behulp van de cmdlet New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-224">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="3e6b1-225">Zie New-WSManSessionOption voor meer informatie over de beschik bare opties.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-225">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="3e6b1-226">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="3e6b1-226">-UseSSL</span></span>

<span data-ttu-id="3e6b1-227">Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) moet worden gebruikt om een verbinding met de externe computer tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-227">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="3e6b1-228">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-228">By default, SSL is not used.</span></span>

<span data-ttu-id="3e6b1-229">WS-Management versleutelt alle Windows Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-229">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="3e6b1-230">Met de para meter UseSSL kunt u de extra beveiliging van HTTPS in plaats van HTTP opgeven.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-230">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="3e6b1-231">Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-231">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="3e6b1-232">-Waardeset</span><span class="sxs-lookup"><span data-stu-id="3e6b1-232">-ValueSet</span></span>

<span data-ttu-id="3e6b1-233">Hiermee geeft u een hash-tabel op waarmee u een beheer bron kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-233">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="3e6b1-234">U geeft de beheer bron op met behulp van de para meter ResourceURI en de para meter SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-234">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="3e6b1-235">De waarde van de para meter voor de waardeset moet een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-235">The value of the ValueSet parameter must be a hash table.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e6b1-236">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e6b1-236">CommonParameters</span></span>

<span data-ttu-id="3e6b1-237">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-237">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e6b1-238">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-238">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3e6b1-239">INVOER</span><span class="sxs-lookup"><span data-stu-id="3e6b1-239">INPUTS</span></span>

### <span data-ttu-id="3e6b1-240">Geen</span><span class="sxs-lookup"><span data-stu-id="3e6b1-240">None</span></span>

<span data-ttu-id="3e6b1-241">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-241">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="3e6b1-242">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3e6b1-242">OUTPUTS</span></span>

### <span data-ttu-id="3e6b1-243">Geen</span><span class="sxs-lookup"><span data-stu-id="3e6b1-243">None</span></span>

<span data-ttu-id="3e6b1-244">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-244">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3e6b1-245">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3e6b1-245">NOTES</span></span>

## <span data-ttu-id="3e6b1-246">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3e6b1-246">RELATED LINKS</span></span>

[<span data-ttu-id="3e6b1-247">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="3e6b1-247">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="3e6b1-248">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3e6b1-248">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="3e6b1-249">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="3e6b1-249">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="3e6b1-250">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3e6b1-250">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="3e6b1-251">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3e6b1-251">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="3e6b1-252">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e6b1-252">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="3e6b1-253">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="3e6b1-253">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="3e6b1-254">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e6b1-254">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="3e6b1-255">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="3e6b1-255">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="3e6b1-256">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e6b1-256">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="3e6b1-257">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="3e6b1-257">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="3e6b1-258">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="3e6b1-258">Test-WSMan</span></span>](Test-WSMan.md)
