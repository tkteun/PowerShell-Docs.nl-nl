---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: 1eeeb912ab32ec5334959daba1e352f20fec15b1
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253129"
---
# <span data-ttu-id="a61c3-103">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="a61c3-103">Invoke-WSManAction</span></span>

## <span data-ttu-id="a61c3-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a61c3-104">SYNOPSIS</span></span>
<span data-ttu-id="a61c3-105">Hiermee wordt een actie aangeroepen voor het object dat is opgegeven door de resource-URI en de selecters.</span><span class="sxs-lookup"><span data-stu-id="a61c3-105">Invokes an action on the object that is specified by the Resource URI and by the selectors.</span></span>

## <span data-ttu-id="a61c3-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a61c3-106">SYNTAX</span></span>

### <span data-ttu-id="a61c3-107">URI (standaard)</span><span class="sxs-lookup"><span data-stu-id="a61c3-107">URI (Default)</span></span>

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="a61c3-108">ComputerName</span><span class="sxs-lookup"><span data-stu-id="a61c3-108">ComputerName</span></span>

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="a61c3-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a61c3-109">DESCRIPTION</span></span>

<span data-ttu-id="a61c3-110">De Invoke-WSManAction voert een actie uit op het object dat is opgegeven door RESOURCE_URI, waarbij de para meters worden opgegeven door sleutel waardeparen.</span><span class="sxs-lookup"><span data-stu-id="a61c3-110">The Invoke-WSManAction runs an action on the object that is specified by RESOURCE_URI, where parameters are specified by key value pairs.</span></span>

<span data-ttu-id="a61c3-111">Deze cmdlet maakt gebruik van de WSMan-verbinding/transportlaag om de actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a61c3-111">This cmdlet uses the WSMan connection/transport layer to run the action.</span></span>

## <span data-ttu-id="a61c3-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a61c3-112">EXAMPLES</span></span>

### <span data-ttu-id="a61c3-113">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="a61c3-113">Example 1</span></span>

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

<span data-ttu-id="a61c3-114">Met deze opdracht wordt de methode start service aangeroepen van de Win32_Service WMI-klasse-instantie die overeenkomt met de Spooler-service.</span><span class="sxs-lookup"><span data-stu-id="a61c3-114">This command calls the StartService method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>

<span data-ttu-id="a61c3-115">De geretourneerde waarde geeft aan of de actie is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="a61c3-115">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="a61c3-116">In dit geval geeft een geretourneerde waarde van 0 aan dat dit is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="a61c3-116">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="a61c3-117">Een retour waarde van 5 geeft aan dat de service al is gestart.</span><span class="sxs-lookup"><span data-stu-id="a61c3-117">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="a61c3-118">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="a61c3-118">Example 2</span></span>

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

<span data-ttu-id="a61c3-119">Met deze opdracht wordt de stop service-methode voor de spooler aangeroepen met behulp van invoer vanuit een bestand.</span><span class="sxs-lookup"><span data-stu-id="a61c3-119">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="a61c3-120">Het bestand, Input.xml, bevat de volgende inhoud:</span><span class="sxs-lookup"><span data-stu-id="a61c3-120">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

<span data-ttu-id="a61c3-121">De geretourneerde waarde geeft aan of de actie is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="a61c3-121">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="a61c3-122">In dit geval geeft een geretourneerde waarde van 0 aan dat dit is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="a61c3-122">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="a61c3-123">Een retour waarde van 5 geeft aan dat de service al is gestart.</span><span class="sxs-lookup"><span data-stu-id="a61c3-123">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="a61c3-124">Voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="a61c3-124">Example 3</span></span>

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

<span data-ttu-id="a61c3-125">Met deze opdracht wordt de methode Create van de klasse Win32_Process aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="a61c3-125">This command calls the Create method of the Win32_Process class.</span></span>
<span data-ttu-id="a61c3-126">De methode geeft twee parameter waarden, Notepad.exe en C: \" .</span><span class="sxs-lookup"><span data-stu-id="a61c3-126">It passes the method two parameter values, Notepad.exe and "C:\".</span></span>
<span data-ttu-id="a61c3-127">Als gevolg hiervan wordt een nieuw proces gemaakt voor het uitvoeren van Klad blok en de huidige map van het nieuwe proces is ingesteld op C: \" .</span><span class="sxs-lookup"><span data-stu-id="a61c3-127">As a result, a new process is created to run Notepad, and the current directory of the new process is set to "C:\".</span></span>

### <span data-ttu-id="a61c3-128">Voorbeeld 4</span><span class="sxs-lookup"><span data-stu-id="a61c3-128">Example 4</span></span>

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

<span data-ttu-id="a61c3-129">Met deze opdracht wordt de methode start service aangeroepen van de Win32_Service WMI-klasse-instantie die overeenkomt met de Spooler-service.</span><span class="sxs-lookup"><span data-stu-id="a61c3-129">This command calls the StartService method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>
<span data-ttu-id="a61c3-130">Omdat de para meter ComputerName is opgegeven, wordt de opdracht uitgevoerd op de externe Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="a61c3-130">Because the ComputerName parameter is specified, the command runs against the remote server01 computer.</span></span>

<span data-ttu-id="a61c3-131">De geretourneerde waarde geeft aan of de actie is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="a61c3-131">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="a61c3-132">In dit geval geeft een geretourneerde waarde van 0 aan dat dit is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="a61c3-132">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="a61c3-133">Een retour waarde van 5 geeft aan dat de service al is gestart.</span><span class="sxs-lookup"><span data-stu-id="a61c3-133">A return value of 5 indicates that the service is already started.</span></span>

## <span data-ttu-id="a61c3-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a61c3-134">PARAMETERS</span></span>

### <span data-ttu-id="a61c3-135">-Actie</span><span class="sxs-lookup"><span data-stu-id="a61c3-135">-Action</span></span>

<span data-ttu-id="a61c3-136">Hiermee geeft u de methode op die moet worden uitgevoerd op het beheer object dat is opgegeven door de ResourceURI en selecters.</span><span class="sxs-lookup"><span data-stu-id="a61c3-136">Specifies the method to run on the management object specified by the ResourceURI and selectors.</span></span>

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

### <span data-ttu-id="a61c3-137">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="a61c3-137">-ApplicationName</span></span>

<span data-ttu-id="a61c3-138">Hiermee geeft u de naam van de toepassing in de verbinding.</span><span class="sxs-lookup"><span data-stu-id="a61c3-138">Specifies the application name in the connection.</span></span>
<span data-ttu-id="a61c3-139">De standaard waarde van de para meter ApplicationName is WSMAN.</span><span class="sxs-lookup"><span data-stu-id="a61c3-139">The default value of the ApplicationName parameter is WSMAN.</span></span>
<span data-ttu-id="a61c3-140">De volledige id voor het externe eind punt heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="a61c3-140">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="a61c3-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="a61c3-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="a61c3-142">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a61c3-142">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="a61c3-143">Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="a61c3-143">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="a61c3-144">Deze standaard instelling van ' WSMAN ' is geschikt voor de meeste doel einden.</span><span class="sxs-lookup"><span data-stu-id="a61c3-144">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="a61c3-145">Deze para meter is ontworpen om te worden gebruikt wanneer talloze computers externe verbindingen tot stand brengen met één computer met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="a61c3-145">This parameter is designed to be used when numerous computers establish remote connections to one computer running Windows PowerShell.</span></span>
<span data-ttu-id="a61c3-146">In dit geval wordt IIS gehost Web Services for Management (WS-Management) voor efficiëntie.</span><span class="sxs-lookup"><span data-stu-id="a61c3-146">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="a61c3-147">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="a61c3-147">-Authentication</span></span>

<span data-ttu-id="a61c3-148">Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server.</span><span class="sxs-lookup"><span data-stu-id="a61c3-148">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="a61c3-149">Mogelijke waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="a61c3-149">Possible values are:</span></span>

- <span data-ttu-id="a61c3-150">Basic: Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="a61c3-150">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="a61c3-151">Standaard: gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol.</span><span class="sxs-lookup"><span data-stu-id="a61c3-151">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="a61c3-152">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="a61c3-152">This is the default.</span></span>
- <span data-ttu-id="a61c3-153">Digest: Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.</span><span class="sxs-lookup"><span data-stu-id="a61c3-153">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="a61c3-154">Kerberos: de client computer en de server worden wederzijds geverifieerd met behulp van Kerberos-certificaten.</span><span class="sxs-lookup"><span data-stu-id="a61c3-154">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="a61c3-155">Onderhandelen: onderhandelen is een vraag/antwoord-schema dat onderhandelt met de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="a61c3-155">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="a61c3-156">Deze parameter waarde kan bijvoorbeeld onderhandelen om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a61c3-156">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="a61c3-157">CredSSP: gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren.</span><span class="sxs-lookup"><span data-stu-id="a61c3-157">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="a61c3-158">Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a61c3-158">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="a61c3-159">Let op: CredSSP delegeert de referenties van de gebruiker van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="a61c3-159">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="a61c3-160">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="a61c3-160">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="a61c3-161">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="a61c3-161">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="a61c3-162">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="a61c3-162">-CertificateThumbprint</span></span>

<span data-ttu-id="a61c3-163">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a61c3-163">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="a61c3-164">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="a61c3-164">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="a61c3-165">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="a61c3-165">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="a61c3-166">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="a61c3-166">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="a61c3-167">Als u een certificaat vingerafdruk wilt krijgen, gebruikt u de opdracht Get-Item of Get-ChildItem in het Windows Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="a61c3-167">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the Windows PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="a61c3-168">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a61c3-168">-ComputerName</span></span>

<span data-ttu-id="a61c3-169">Hiermee geeft u de computer op waartegen u de beheer bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="a61c3-169">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="a61c3-170">De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.</span><span class="sxs-lookup"><span data-stu-id="a61c3-170">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="a61c3-171">Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="a61c3-171">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="a61c3-172">De lokale computer is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="a61c3-172">The local computer is the default.</span></span>
<span data-ttu-id="a61c3-173">Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a61c3-173">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="a61c3-174">U kunt een waarde voor deze para meter door geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a61c3-174">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="a61c3-175">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="a61c3-175">-ConnectionURI</span></span>

<span data-ttu-id="a61c3-176">Hiermee geeft u het eind punt van de verbinding.</span><span class="sxs-lookup"><span data-stu-id="a61c3-176">Specifies the connection endpoint.</span></span>
<span data-ttu-id="a61c3-177">De notatie van deze teken reeks is:</span><span class="sxs-lookup"><span data-stu-id="a61c3-177">The format of this string is:</span></span>

<span data-ttu-id="a61c3-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="a61c3-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="a61c3-179">De volgende teken reeks is een correct ingedeelde waarde voor deze para meter:</span><span class="sxs-lookup"><span data-stu-id="a61c3-179">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="a61c3-180">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="a61c3-180">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="a61c3-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="a61c3-181">-Credential</span></span>

<span data-ttu-id="a61c3-182">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a61c3-182">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="a61c3-183">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a61c3-183">The default is the current user.</span></span>
<span data-ttu-id="a61c3-184">Typ een gebruikers naam, zoals "gebruiker01", "Domain01\User01" of User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="a61c3-184">Type a user name, such as "User01", "Domain01\User01", or User@Domain.com.</span></span>
<span data-ttu-id="a61c3-185">U kunt ook een PSCredential-object invoeren, zoals het dat wordt geretourneerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="a61c3-185">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="a61c3-186">Wanneer u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="a61c3-186">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="a61c3-187">-FilePath</span><span class="sxs-lookup"><span data-stu-id="a61c3-187">-FilePath</span></span>

<span data-ttu-id="a61c3-188">Hiermee geeft u het pad op van een bestand dat wordt gebruikt om een beheer bron bij te werken.</span><span class="sxs-lookup"><span data-stu-id="a61c3-188">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="a61c3-189">U geeft de beheer bron op met behulp van de para meter ResourceURI en de para meter SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="a61c3-189">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="a61c3-190">De volgende opdracht maakt bijvoorbeeld gebruik van de FilePath-para meter:</span><span class="sxs-lookup"><span data-stu-id="a61c3-190">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

<span data-ttu-id="a61c3-191">Met deze opdracht wordt de stop service-methode voor de spooler aangeroepen met behulp van invoer vanuit een bestand.</span><span class="sxs-lookup"><span data-stu-id="a61c3-191">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="a61c3-192">Het bestand, Input.xml, bevat de volgende inhoud:</span><span class="sxs-lookup"><span data-stu-id="a61c3-192">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

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

### <span data-ttu-id="a61c3-193">-Optieset</span><span class="sxs-lookup"><span data-stu-id="a61c3-193">-OptionSet</span></span>

<span data-ttu-id="a61c3-194">Hiermee wordt een set switches door gegeven aan een service om de aard van de aanvraag te wijzigen of te verfijnen.</span><span class="sxs-lookup"><span data-stu-id="a61c3-194">Passes a set of switches  to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="a61c3-195">Deze zijn vergelijkbaar met de switches die worden gebruikt in opdracht regel shells, omdat deze service-specifiek zijn.</span><span class="sxs-lookup"><span data-stu-id="a61c3-195">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="a61c3-196">U kunt een wille keurig aantal opties opgeven.</span><span class="sxs-lookup"><span data-stu-id="a61c3-196">Any number of options  can be specified.</span></span>

<span data-ttu-id="a61c3-197">In het volgende voor beeld ziet u de syntaxis waarmee de waarden 1, 2 en 3 worden door gegeven voor de para meters a, b en c:</span><span class="sxs-lookup"><span data-stu-id="a61c3-197">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="a61c3-198">-Port</span><span class="sxs-lookup"><span data-stu-id="a61c3-198">-Port</span></span>

<span data-ttu-id="a61c3-199">Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="a61c3-199">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="a61c3-200">Wanneer het Trans Port HTTP is, is de standaard poort 80.</span><span class="sxs-lookup"><span data-stu-id="a61c3-200">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="a61c3-201">Wanneer het Trans Port HTTPS is, is de standaard poort 443.</span><span class="sxs-lookup"><span data-stu-id="a61c3-201">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="a61c3-202">Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter ComputerName overeenkomen met de common name (CN) van het server certificaat.</span><span class="sxs-lookup"><span data-stu-id="a61c3-202">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="a61c3-203">Als de para meter SkipCNCheck echter is opgegeven als onderdeel van de para meter SessionOption, moet de algemene naam van het certificaat van de server niet overeenkomen met de hostnaam van de server.</span><span class="sxs-lookup"><span data-stu-id="a61c3-203">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="a61c3-204">De para meter SkipCNCheck moet alleen worden gebruikt voor vertrouwde computers.</span><span class="sxs-lookup"><span data-stu-id="a61c3-204">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="a61c3-205">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="a61c3-205">-ResourceURI</span></span>

<span data-ttu-id="a61c3-206">Bevat de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar.</span><span class="sxs-lookup"><span data-stu-id="a61c3-206">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="a61c3-207">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="a61c3-207">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="a61c3-208">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="a61c3-208">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="a61c3-209">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a61c3-209">For example:</span></span>

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

### <span data-ttu-id="a61c3-210">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="a61c3-210">-SelectorSet</span></span>

<span data-ttu-id="a61c3-211">Hiermee geeft u een set waardeparen op die worden gebruikt om bepaalde beheer resource-instanties te selecteren.</span><span class="sxs-lookup"><span data-stu-id="a61c3-211">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="a61c3-212">*SelectorSet* wordt gebruikt wanneer er meer dan één exemplaar van de bron bestaat.</span><span class="sxs-lookup"><span data-stu-id="a61c3-212">*SelectorSet* is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="a61c3-213">De waarde van *SelectorSet* moet een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="a61c3-213">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="a61c3-214">In het volgende voor beeld ziet u hoe u een waarde voor deze para meter opgeeft:</span><span class="sxs-lookup"><span data-stu-id="a61c3-214">The following example shows how to enter a value for this parameter:</span></span>

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

### <span data-ttu-id="a61c3-215">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="a61c3-215">-SessionOption</span></span>

<span data-ttu-id="a61c3-216">Hiermee definieert u een set uitgebreide opties voor de WS-Management sessie.</span><span class="sxs-lookup"><span data-stu-id="a61c3-216">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="a61c3-217">Voer een SessionOption-object in dat u maakt met behulp van de cmdlet New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="a61c3-217">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="a61c3-218">Zie New-WSManSessionOption voor meer informatie over de beschik bare opties.</span><span class="sxs-lookup"><span data-stu-id="a61c3-218">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="a61c3-219">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="a61c3-219">-UseSSL</span></span>

<span data-ttu-id="a61c3-220">Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) wordt gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="a61c3-220">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="a61c3-221">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a61c3-221">By default, SSL is not used.</span></span>

<span data-ttu-id="a61c3-222">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="a61c3-222">WS-Management encrypts all the PowerShell content  that is transmitted over the network.</span></span>
<span data-ttu-id="a61c3-223">Met de para meter UseSSL kunt u de extra beveiliging van HTTPS in plaats van HTTP opgeven.</span><span class="sxs-lookup"><span data-stu-id="a61c3-223">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="a61c3-224">Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="a61c3-224">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="a61c3-225">-Waardeset</span><span class="sxs-lookup"><span data-stu-id="a61c3-225">-ValueSet</span></span>

<span data-ttu-id="a61c3-226">Hiermee geeft u een hash-tabel op waarmee u een beheer bron kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a61c3-226">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="a61c3-227">U geeft de beheer resource op met behulp van de para meters ResourceURI en SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="a61c3-227">You specify the management resource using the ResourceURI and SelectorSet parameters.</span></span>
<span data-ttu-id="a61c3-228">De waarde van de para meter voor de waardeset moet een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="a61c3-228">The value of the ValueSet parameter must be a hash table.</span></span>

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

### <span data-ttu-id="a61c3-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a61c3-229">CommonParameters</span></span>

<span data-ttu-id="a61c3-230">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a61c3-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a61c3-231">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a61c3-231">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a61c3-232">INVOER</span><span class="sxs-lookup"><span data-stu-id="a61c3-232">INPUTS</span></span>

### <span data-ttu-id="a61c3-233">Geen</span><span class="sxs-lookup"><span data-stu-id="a61c3-233">None</span></span>

<span data-ttu-id="a61c3-234">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="a61c3-234">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="a61c3-235">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a61c3-235">OUTPUTS</span></span>

### <span data-ttu-id="a61c3-236">Geen</span><span class="sxs-lookup"><span data-stu-id="a61c3-236">None</span></span>

<span data-ttu-id="a61c3-237">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a61c3-237">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a61c3-238">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a61c3-238">NOTES</span></span>

## <span data-ttu-id="a61c3-239">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a61c3-239">RELATED LINKS</span></span>

[<span data-ttu-id="a61c3-240">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="a61c3-240">Invoke-WmiMethod</span></span>](../Microsoft.PowerShell.Management/Invoke-WmiMethod.md)

[<span data-ttu-id="a61c3-241">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="a61c3-241">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="a61c3-242">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a61c3-242">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="a61c3-243">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="a61c3-243">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="a61c3-244">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a61c3-244">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="a61c3-245">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a61c3-245">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="a61c3-246">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a61c3-246">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="a61c3-247">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a61c3-247">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="a61c3-248">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="a61c3-248">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="a61c3-249">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a61c3-249">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="a61c3-250">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a61c3-250">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="a61c3-251">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="a61c3-251">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="a61c3-252">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="a61c3-252">Test-WSMan</span></span>](Test-WSMan.md)
