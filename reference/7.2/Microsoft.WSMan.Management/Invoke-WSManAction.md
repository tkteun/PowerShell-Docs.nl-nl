---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: e2456e1da866929d60c36cc0e09990399b41614b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704721"
---
# <span data-ttu-id="faf64-102">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="faf64-102">Invoke-WSManAction</span></span>

## <span data-ttu-id="faf64-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="faf64-103">SYNOPSIS</span></span>
<span data-ttu-id="faf64-104">Hiermee wordt een actie aangeroepen voor het object dat is opgegeven door de resource-URI en de selecters.</span><span class="sxs-lookup"><span data-stu-id="faf64-104">Invokes an action on the object that is specified by the Resource URI and by the selectors.</span></span>

## <span data-ttu-id="faf64-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="faf64-105">SYNTAX</span></span>

### <span data-ttu-id="faf64-106">URI (standaard)</span><span class="sxs-lookup"><span data-stu-id="faf64-106">URI (Default)</span></span>

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="faf64-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="faf64-107">ComputerName</span></span>

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="faf64-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="faf64-108">DESCRIPTION</span></span>
<span data-ttu-id="faf64-109">De **invoke-WSManAction** voert een actie uit op het object dat is opgegeven door RESOURCE_URI, waarbij de para meters worden opgegeven door sleutel waardeparen.</span><span class="sxs-lookup"><span data-stu-id="faf64-109">The **Invoke-WSManAction** runs an action on the object that is specified by RESOURCE_URI, where parameters are specified by key value pairs.</span></span>

<span data-ttu-id="faf64-110">Deze cmdlet maakt gebruik van de WSMan-verbinding/transportlaag om de actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="faf64-110">This cmdlet uses the WSMan connection/transport layer to run the action.</span></span>

## <span data-ttu-id="faf64-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="faf64-111">EXAMPLES</span></span>

### <span data-ttu-id="faf64-112">Voor beeld 1: een methode aanroepen</span><span class="sxs-lookup"><span data-stu-id="faf64-112">Example 1: Invoke a method</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="faf64-113">Met deze opdracht wordt de methode **Start service** aangeroepen van de Win32_Service WMI-klasse-instantie die overeenkomt met de Spooler-service.</span><span class="sxs-lookup"><span data-stu-id="faf64-113">This command calls the **StartService** method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>

<span data-ttu-id="faf64-114">De geretourneerde waarde geeft aan of de actie is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="faf64-114">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="faf64-115">In dit geval geeft een geretourneerde waarde van 0 aan dat dit is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="faf64-115">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="faf64-116">Een retour waarde van 5 geeft aan dat de service al is gestart.</span><span class="sxs-lookup"><span data-stu-id="faf64-116">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="faf64-117">Voor beeld 2: een methode aanroepen</span><span class="sxs-lookup"><span data-stu-id="faf64-117">Example 2: Invoke a method</span></span>

```powershell
Invoke-WSManAction -Action stopservice -ResourceURI wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:input.xml -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="faf64-118">Met deze opdracht wordt de **Stop** service-methode voor de spooler aangeroepen met behulp van invoer vanuit een bestand.</span><span class="sxs-lookup"><span data-stu-id="faf64-118">This command calls the **StopService** method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="faf64-119">Het bestand, Input.xml, bevat de volgende inhoud:</span><span class="sxs-lookup"><span data-stu-id="faf64-119">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

### <span data-ttu-id="faf64-120">Voor beeld 3: een methode met opgegeven parameter waarden aanroepen</span><span class="sxs-lookup"><span data-stu-id="faf64-120">Example 3: Invoke a method with specified parameter values</span></span>

```powershell
Invoke-WSManAction -Action create -ResourceURI wmicimv2/win32_process -ValueSet @{commandline="notepad.exe";currentdirectory="C:\"}
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Process
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ProcessId   : 6356
ReturnValue : 0
```

<span data-ttu-id="faf64-121">Met deze opdracht wordt de methode **Create** van de klasse Win32_Process aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="faf64-121">This command calls the **Create** method of the Win32_Process class.</span></span>
<span data-ttu-id="faf64-122">Er worden twee parameter waarden voor de methode, Notepad.exe en C:\., door gegeven</span><span class="sxs-lookup"><span data-stu-id="faf64-122">It passes the method two parameter values, Notepad.exe and C:\.</span></span>
<span data-ttu-id="faf64-123">Als gevolg hiervan wordt een nieuw proces gemaakt voor het uitvoeren van Klad blok en de huidige map van het nieuwe proces is ingesteld op C:\.</span><span class="sxs-lookup"><span data-stu-id="faf64-123">As a result, a new process is created to run Notepad, and the current directory of the new process is set to C:\.</span></span>

### <span data-ttu-id="faf64-124">Voor beeld 4: een methode aanroepen op een externe computer</span><span class="sxs-lookup"><span data-stu-id="faf64-124">Example 4: Invoke a method on a remote computer</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -ComputerName server01 -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="faf64-125">Met deze opdracht wordt de methode **Start service** aangeroepen van de Win32_Service WMI-klasse-instantie die overeenkomt met de Spooler-service.</span><span class="sxs-lookup"><span data-stu-id="faf64-125">This command calls the **StartService** method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>
<span data-ttu-id="faf64-126">Omdat de para meter *ComputerName* is opgegeven, wordt de opdracht uitgevoerd op de externe Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="faf64-126">Because the *ComputerName* parameter is specified, the command runs against the remote server01 computer.</span></span>

## <span data-ttu-id="faf64-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="faf64-127">PARAMETERS</span></span>

### <span data-ttu-id="faf64-128">-Actie</span><span class="sxs-lookup"><span data-stu-id="faf64-128">-Action</span></span>
<span data-ttu-id="faf64-129">Hiermee geeft u de methode op die moet worden uitgevoerd op het beheer object dat is opgegeven door de ResourceURI en selecters.</span><span class="sxs-lookup"><span data-stu-id="faf64-129">Specifies the method to run on the management object specified by the ResourceURI and selectors.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="faf64-130">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="faf64-130">-ApplicationName</span></span>
<span data-ttu-id="faf64-131">Hiermee geeft u de naam van de toepassing in de verbinding.</span><span class="sxs-lookup"><span data-stu-id="faf64-131">Specifies the application name in the connection.</span></span>
<span data-ttu-id="faf64-132">De standaard waarde van de para meter *ApplicationName* is WSMAN.</span><span class="sxs-lookup"><span data-stu-id="faf64-132">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="faf64-133">De volledige id voor het externe eind punt heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="faf64-133">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="faf64-134">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="faf64-134">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="faf64-135">Bijvoorbeeld: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="faf64-135">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="faf64-136">Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="faf64-136">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="faf64-137">Deze standaard instelling van WSMAN is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="faf64-137">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="faf64-138">Deze para meter is ontworpen om te worden gebruikt als veel computers externe verbindingen tot stand brengen met één computer waarop Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="faf64-138">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="faf64-139">In dit geval wordt IIS gehost Web Services for Management (WS-Management) voor efficiëntie.</span><span class="sxs-lookup"><span data-stu-id="faf64-139">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="faf64-140">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="faf64-140">-Authentication</span></span>
<span data-ttu-id="faf64-141">Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server.</span><span class="sxs-lookup"><span data-stu-id="faf64-141">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="faf64-142">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="faf64-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="faf64-143">Hoofd.</span><span class="sxs-lookup"><span data-stu-id="faf64-143">Basic.</span></span>
<span data-ttu-id="faf64-144">Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="faf64-144">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="faf64-145">Standaard.</span><span class="sxs-lookup"><span data-stu-id="faf64-145">Default.</span></span>
<span data-ttu-id="faf64-146">Gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol.</span><span class="sxs-lookup"><span data-stu-id="faf64-146">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="faf64-147">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="faf64-147">This is the default.</span></span>
- <span data-ttu-id="faf64-148">Vatting.</span><span class="sxs-lookup"><span data-stu-id="faf64-148">Digest.</span></span>
<span data-ttu-id="faf64-149">Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.</span><span class="sxs-lookup"><span data-stu-id="faf64-149">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="faf64-150">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="faf64-150">Kerberos.</span></span>
<span data-ttu-id="faf64-151">De client computer en de server worden wederzijds geverifieerd met behulp van Kerberos-certificaten.</span><span class="sxs-lookup"><span data-stu-id="faf64-151">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="faf64-152">Afspraken.</span><span class="sxs-lookup"><span data-stu-id="faf64-152">Negotiate.</span></span>
<span data-ttu-id="faf64-153">Onderhandelen is een vraag/antwoord-schema waarmee wordt onderhandeld over de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="faf64-153">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="faf64-154">Met deze parameter waarde kan bijvoorbeeld worden geonderhandelingd om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="faf64-154">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="faf64-155">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="faf64-155">CredSSP.</span></span>
<span data-ttu-id="faf64-156">Gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren.</span><span class="sxs-lookup"><span data-stu-id="faf64-156">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="faf64-157">Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="faf64-157">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="faf64-158">Let op: CredSSP delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="faf64-158">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="faf64-159">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="faf64-159">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="faf64-160">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="faf64-160">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="faf64-161">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="faf64-161">-CertificateThumbprint</span></span>
<span data-ttu-id="faf64-162">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="faf64-162">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="faf64-163">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="faf64-163">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="faf64-164">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="faf64-164">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="faf64-165">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="faf64-165">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="faf64-166">Als u een certificaat vingerafdruk wilt krijgen, gebruikt u de opdracht Get-Item of Get-ChildItem in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="faf64-166">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="faf64-167">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="faf64-167">-ComputerName</span></span>
<span data-ttu-id="faf64-168">Hiermee geeft u de computer op waarop de beheer bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="faf64-168">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="faf64-169">De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.</span><span class="sxs-lookup"><span data-stu-id="faf64-169">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="faf64-170">Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="faf64-170">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="faf64-171">De lokale computer is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="faf64-171">The local computer is the default.</span></span>
<span data-ttu-id="faf64-172">Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.</span><span class="sxs-lookup"><span data-stu-id="faf64-172">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="faf64-173">U kunt een waarde voor deze para meter door geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="faf64-173">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="faf64-174">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="faf64-174">-ConnectionURI</span></span>
<span data-ttu-id="faf64-175">Hiermee geeft u het eind punt van de verbinding.</span><span class="sxs-lookup"><span data-stu-id="faf64-175">Specifies the connection endpoint.</span></span>
<span data-ttu-id="faf64-176">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="faf64-176">The format of this string is as follows:</span></span>

<span data-ttu-id="faf64-177">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="faf64-177">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="faf64-178">De volgende teken reeks is een correct ingedeelde waarde voor deze para meter:</span><span class="sxs-lookup"><span data-stu-id="faf64-178">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="faf64-179">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="faf64-179">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="faf64-180">-Credential</span><span class="sxs-lookup"><span data-stu-id="faf64-180">-Credential</span></span>
<span data-ttu-id="faf64-181">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="faf64-181">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="faf64-182">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="faf64-182">The default is the current user.</span></span>
<span data-ttu-id="faf64-183">Typ een gebruikers naam, zoals gebruiker01, Domain01\User01 of User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="faf64-183">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="faf64-184">U kunt ook een **PSCredential** -object invoeren, zoals het dat wordt geretourneerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="faf64-184">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="faf64-185">Wanneer u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="faf64-185">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="faf64-186">-FilePath</span><span class="sxs-lookup"><span data-stu-id="faf64-186">-FilePath</span></span>
<span data-ttu-id="faf64-187">Hiermee geeft u het pad op van een bestand dat wordt gebruikt om een beheer bron bij te werken.</span><span class="sxs-lookup"><span data-stu-id="faf64-187">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="faf64-188">U geeft de beheer bron op met behulp van de para meter *ResourceURI* en de para meter *SelectorSet* .</span><span class="sxs-lookup"><span data-stu-id="faf64-188">You specify the management resource by using the *ResourceURI* parameter and the *SelectorSet* parameter.</span></span>
<span data-ttu-id="faf64-189">De volgende opdracht maakt bijvoorbeeld gebruik van de *filepath* -para meter:</span><span class="sxs-lookup"><span data-stu-id="faf64-189">For example, the following command uses the *FilePath* parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

<span data-ttu-id="faf64-190">Met deze opdracht wordt de **Stop** service-methode voor de **spooler** aangeroepen met behulp van invoer vanuit een bestand.</span><span class="sxs-lookup"><span data-stu-id="faf64-190">This command calls the **StopService** method on the **Spooler** service by using input from a file.</span></span>
<span data-ttu-id="faf64-191">Het bestand, Input.xml, bevat de volgende inhoud:</span><span class="sxs-lookup"><span data-stu-id="faf64-191">The file, Input.xml, contains the following content:</span></span>

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

### <span data-ttu-id="faf64-192">-Optieset</span><span class="sxs-lookup"><span data-stu-id="faf64-192">-OptionSet</span></span>
<span data-ttu-id="faf64-193">Hiermee geeft u een set switches naar een service op om de aard van de aanvraag te wijzigen of te verfijnen.</span><span class="sxs-lookup"><span data-stu-id="faf64-193">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="faf64-194">Deze lijken op de Schakel opties die worden gebruikt in opdracht regel shells, omdat deze service-specifiek zijn.</span><span class="sxs-lookup"><span data-stu-id="faf64-194">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="faf64-195">U kunt een wille keurig aantal opties opgeven.</span><span class="sxs-lookup"><span data-stu-id="faf64-195">Any number of options can be specified.</span></span>

<span data-ttu-id="faf64-196">In het volgende voor beeld ziet u de syntaxis waarmee de waarden 1, 2 en 3 worden door gegeven voor de para meters a, b en c:</span><span class="sxs-lookup"><span data-stu-id="faf64-196">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="faf64-197">-Port</span><span class="sxs-lookup"><span data-stu-id="faf64-197">-Port</span></span>
<span data-ttu-id="faf64-198">Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="faf64-198">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="faf64-199">Wanneer het Trans Port HTTP is, is de standaard poort 80.</span><span class="sxs-lookup"><span data-stu-id="faf64-199">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="faf64-200">Wanneer het Trans Port HTTPS is, is de standaard poort 443.</span><span class="sxs-lookup"><span data-stu-id="faf64-200">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="faf64-201">Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter *ComputerName* overeenkomen met de common name (CN) van het server certificaat.</span><span class="sxs-lookup"><span data-stu-id="faf64-201">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="faf64-202">Als de para meter *SkipCNCheck* echter is opgegeven als onderdeel van de *SessionOption* -para meter, moet de algemene naam van het certificaat van de server niet overeenkomen met de hostnaam van de server.</span><span class="sxs-lookup"><span data-stu-id="faf64-202">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="faf64-203">De para meter *SkipCNCheck* moet alleen worden gebruikt voor vertrouwde computers.</span><span class="sxs-lookup"><span data-stu-id="faf64-203">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="faf64-204">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="faf64-204">-ResourceURI</span></span>
<span data-ttu-id="faf64-205">Hiermee geeft u de URI van de resource klasse of het exemplaar.</span><span class="sxs-lookup"><span data-stu-id="faf64-205">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="faf64-206">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="faf64-206">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="faf64-207">Een URI bestaat uit een voor voegsel en een pad van een resource.</span><span class="sxs-lookup"><span data-stu-id="faf64-207">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="faf64-208">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="faf64-208">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="faf64-209">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="faf64-209">-SelectorSet</span></span>
<span data-ttu-id="faf64-210">Hiermee geeft u een set waardeparen op die worden gebruikt om bepaalde beheer resource-instanties te selecteren.</span><span class="sxs-lookup"><span data-stu-id="faf64-210">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="faf64-211">*SelectorSet* wordt gebruikt wanneer er meer dan één exemplaar van de bron bestaat.</span><span class="sxs-lookup"><span data-stu-id="faf64-211">*SelectorSet* is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="faf64-212">De waarde van *SelectorSet* moet een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="faf64-212">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="faf64-213">In het volgende voor beeld ziet u hoe u een waarde voor deze para meter opgeeft:</span><span class="sxs-lookup"><span data-stu-id="faf64-213">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="faf64-214">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="faf64-214">-SessionOption</span></span>
<span data-ttu-id="faf64-215">Hiermee worden uitgebreide opties voor de WS-Management-sessie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="faf64-215">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="faf64-216">Voer een **SessionOption** -object in dat u maakt met behulp van de cmdlet New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="faf64-216">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="faf64-217">Typ voor meer informatie over de beschik bare opties `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="faf64-217">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="faf64-218">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="faf64-218">-UseSSL</span></span>
<span data-ttu-id="faf64-219">Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) wordt gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="faf64-219">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="faf64-220">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="faf64-220">By default, SSL is not used.</span></span>

<span data-ttu-id="faf64-221">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="faf64-221">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="faf64-222">Met de para meter *UseSSL* kunt u de extra beveiliging van https in plaats van http opgeven.</span><span class="sxs-lookup"><span data-stu-id="faf64-222">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="faf64-223">Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="faf64-223">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="faf64-224">-Waardeset</span><span class="sxs-lookup"><span data-stu-id="faf64-224">-ValueSet</span></span>
<span data-ttu-id="faf64-225">Hiermee geeft u een hash-tabel op waarmee u een beheer bron kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="faf64-225">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="faf64-226">U geeft de beheer resource op met behulp van *ResourceURI* en *SelectorSet*.</span><span class="sxs-lookup"><span data-stu-id="faf64-226">You specify the management resource by using *ResourceURI* and *SelectorSet*.</span></span>
<span data-ttu-id="faf64-227">De waarde van de para meter voor de *waardeset* moet een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="faf64-227">The value of the *ValueSet* parameter must be a hash table.</span></span>

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

### <span data-ttu-id="faf64-228">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="faf64-228">CommonParameters</span></span>
<span data-ttu-id="faf64-229">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="faf64-229">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="faf64-230">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="faf64-230">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="faf64-231">INVOER</span><span class="sxs-lookup"><span data-stu-id="faf64-231">INPUTS</span></span>

### <span data-ttu-id="faf64-232">Geen</span><span class="sxs-lookup"><span data-stu-id="faf64-232">None</span></span>
<span data-ttu-id="faf64-233">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="faf64-233">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="faf64-234">UITVOER</span><span class="sxs-lookup"><span data-stu-id="faf64-234">OUTPUTS</span></span>

### <span data-ttu-id="faf64-235">Geen</span><span class="sxs-lookup"><span data-stu-id="faf64-235">None</span></span>
<span data-ttu-id="faf64-236">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="faf64-236">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="faf64-237">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="faf64-237">NOTES</span></span>

## <span data-ttu-id="faf64-238">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="faf64-238">RELATED LINKS</span></span>

[<span data-ttu-id="faf64-239">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="faf64-239">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="faf64-240">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="faf64-240">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="faf64-241">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="faf64-241">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="faf64-242">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="faf64-242">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="faf64-243">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="faf64-243">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="faf64-244">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="faf64-244">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="faf64-245">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="faf64-245">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="faf64-246">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="faf64-246">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="faf64-247">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="faf64-247">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="faf64-248">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="faf64-248">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="faf64-249">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="faf64-249">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="faf64-250">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="faf64-250">Test-WSMan</span></span>](Test-WSMan.md)

