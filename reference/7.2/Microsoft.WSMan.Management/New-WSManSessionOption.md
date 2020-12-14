---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: e7d7f132eb82dc1a709a88cbdef525aa83d867e4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705684"
---
# <span data-ttu-id="ee919-102">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="ee919-102">New-WSManSessionOption</span></span>

## <span data-ttu-id="ee919-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ee919-103">SYNOPSIS</span></span>
<span data-ttu-id="ee919-104">Maakt een hash-tabel voor sessie-opties die moet worden gebruikt als invoer parameters voor WS-Management-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ee919-104">Creates session option hash table to use as input parameters for WS-Management cmdlets.</span></span>

## <span data-ttu-id="ee919-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ee919-105">SYNTAX</span></span>

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## <span data-ttu-id="ee919-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ee919-106">DESCRIPTION</span></span>
<span data-ttu-id="ee919-107">Met de cmdlet **New-WSManSessionOption** maakt u een hash-tabel voor Wsman-sessie opties die kan worden door gegeven aan WSMan-cmdlets:</span><span class="sxs-lookup"><span data-stu-id="ee919-107">The **New-WSManSessionOption** cmdlet creates a WSMan Session option hash table which can be passed to WSMan cmdlets:</span></span>

- <span data-ttu-id="ee919-108">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ee919-108">Get-WSManInstance</span></span>
- <span data-ttu-id="ee919-109">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ee919-109">Set-WSManInstance</span></span>
- <span data-ttu-id="ee919-110">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="ee919-110">Invoke-WSManAction</span></span>
- <span data-ttu-id="ee919-111">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="ee919-111">Connect-WSMan</span></span>

## <span data-ttu-id="ee919-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ee919-112">EXAMPLES</span></span>

### <span data-ttu-id="ee919-113">Voor beeld 1: een verbinding maken die gebruikmaakt van verbindings opties</span><span class="sxs-lookup"><span data-stu-id="ee919-113">Example 1: Create a connection that uses connection options</span></span>

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

<span data-ttu-id="ee919-114">In dit voor beeld wordt een verbinding met de externe Server01-computer gemaakt met behulp van de verbindings opties die zijn gedefinieerd door **New-WSManSessionOption**.</span><span class="sxs-lookup"><span data-stu-id="ee919-114">This example creates a connection to the remote server01 computer by using the connection options that are defined by **New-WSManSessionOption**.</span></span>

<span data-ttu-id="ee919-115">De eerste opdracht maakt gebruik van **New-WSManSessionOption** voor het opslaan van een set opties voor Verbindings instellingen in de variabele $a.</span><span class="sxs-lookup"><span data-stu-id="ee919-115">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="ee919-116">In dit geval stelt de sessie opties een verbindings tijd in van 30 seconden (30.000 milliseconden).</span><span class="sxs-lookup"><span data-stu-id="ee919-116">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="ee919-117">De tweede opdracht gebruikt de para meter *SessionOption* om de referenties door te geven die zijn opgeslagen in de $a variabele om **verbinding te maken-WSMan**.</span><span class="sxs-lookup"><span data-stu-id="ee919-117">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan**.</span></span>
<span data-ttu-id="ee919-118">**Connect-WSMan** maakt verbinding met de externe Server01-computer met behulp van de opgegeven sessie opties.</span><span class="sxs-lookup"><span data-stu-id="ee919-118">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

<span data-ttu-id="ee919-119">**Connect-WSMan** wordt doorgaans gebruikt in de context van de WSMan-provider om verbinding te maken met een externe computer, in dit geval de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="ee919-119">**Connect-WSMan** is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="ee919-120">U kunt de cmdlet echter gebruiken om verbindingen met externe computers tot stand te brengen voordat u overschakelt naar de WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="ee919-120">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="ee919-121">Deze verbindingen worden weer gegeven in de lijst **computer naam** .</span><span class="sxs-lookup"><span data-stu-id="ee919-121">Those connections appear in the **ComputerName** list.</span></span>

## <span data-ttu-id="ee919-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ee919-122">PARAMETERS</span></span>

### <span data-ttu-id="ee919-123">-Geen versleuteling</span><span class="sxs-lookup"><span data-stu-id="ee919-123">-NoEncryption</span></span>
<span data-ttu-id="ee919-124">Geeft aan dat de verbinding geen versleuteling gebruikt voor externe bewerkingen via HTTP.</span><span class="sxs-lookup"><span data-stu-id="ee919-124">Indicates that the connection does not use encryption for remote operations over HTTP.</span></span>

<span data-ttu-id="ee919-125">Standaard is niet-versleuteld verkeer niet ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="ee919-125">By default, unencrypted traffic is not enabled.</span></span>
<span data-ttu-id="ee919-126">Deze moet worden ingeschakeld in de lokale configuratie.</span><span class="sxs-lookup"><span data-stu-id="ee919-126">It must be enabled in the local configuration.</span></span>

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

### <span data-ttu-id="ee919-127">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="ee919-127">-OperationTimeout</span></span>
<span data-ttu-id="ee919-128">Hiermee geeft u de time-out op, in milliseconden, voor de WS-Management bewerking.</span><span class="sxs-lookup"><span data-stu-id="ee919-128">Specifies the time-out, in milliseconds, for the WS-Management operation.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee919-129">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="ee919-129">-ProxyAccessType</span></span>
<span data-ttu-id="ee919-130">Hiermee geeft u het mechanisme op waarmee de proxy server zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="ee919-130">Specifies the mechanism by which the proxy server is located.</span></span>
<span data-ttu-id="ee919-131">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="ee919-131">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ee919-132">ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="ee919-132">ProxyIEConfig.</span></span>
<span data-ttu-id="ee919-133">Gebruik de proxy configuratie van Internet Explorer voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="ee919-133">Use the Internet Explorer proxy configuration for the current user.</span></span>
- <span data-ttu-id="ee919-134">ProxyWinHttpConfig.</span><span class="sxs-lookup"><span data-stu-id="ee919-134">ProxyWinHttpConfig.</span></span>
<span data-ttu-id="ee919-135">De WSMan-client gebruikt de proxy-instellingen die zijn geconfigureerd voor WinHTTP, met behulp van het ProxyCfg.exe-hulp programma.</span><span class="sxs-lookup"><span data-stu-id="ee919-135">The WSMan client uses the proxy settings configured for WinHTTP, using the ProxyCfg.exe utility.</span></span>
- <span data-ttu-id="ee919-136">ProxyAutoDetect.</span><span class="sxs-lookup"><span data-stu-id="ee919-136">ProxyAutoDetect.</span></span>
<span data-ttu-id="ee919-137">Automatische detectie van een proxy server afdwingen.</span><span class="sxs-lookup"><span data-stu-id="ee919-137">Force auto-detection of a proxy server.</span></span>
- <span data-ttu-id="ee919-138">ProxyNoProxyServer.</span><span class="sxs-lookup"><span data-stu-id="ee919-138">ProxyNoProxyServer.</span></span>
<span data-ttu-id="ee919-139">Gebruik geen proxy server.</span><span class="sxs-lookup"><span data-stu-id="ee919-139">Do not use a proxy server.</span></span>
<span data-ttu-id="ee919-140">Alle hostnamen lokaal oplossen.</span><span class="sxs-lookup"><span data-stu-id="ee919-140">Resolve all host names locally.</span></span>

<span data-ttu-id="ee919-141">De standaard waarde is ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="ee919-141">The default value is ProxyIEConfig.</span></span>

```yaml
Type: Microsoft.WSMan.Management.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: ProxyIEConfig, ProxyWinHttpConfig, ProxyAutoDetect, ProxyNoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee919-142">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="ee919-142">-ProxyAuthentication</span></span>
<span data-ttu-id="ee919-143">Hiermee geeft u de verificatie methode op die moet worden gebruikt bij de proxy.</span><span class="sxs-lookup"><span data-stu-id="ee919-143">Specifies the authentication method to use at the proxy.</span></span>
<span data-ttu-id="ee919-144">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="ee919-144">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ee919-145">Hoofd.</span><span class="sxs-lookup"><span data-stu-id="ee919-145">Basic.</span></span>
<span data-ttu-id="ee919-146">Basic is een schema waarin de gebruikers naam en het wacht woord in ongecodeerde tekst worden verzonden naar de server of proxy.</span><span class="sxs-lookup"><span data-stu-id="ee919-146">Basic is a scheme in which the user name and password are sent in clear-text to the server or proxy.</span></span>
- <span data-ttu-id="ee919-147">Vatting.</span><span class="sxs-lookup"><span data-stu-id="ee919-147">Digest.</span></span>
<span data-ttu-id="ee919-148">Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.</span><span class="sxs-lookup"><span data-stu-id="ee919-148">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="ee919-149">Afspraken.</span><span class="sxs-lookup"><span data-stu-id="ee919-149">Negotiate.</span></span>
<span data-ttu-id="ee919-150">Onderhandelen is een vraag/antwoord-schema waarmee wordt onderhandeld over de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="ee919-150">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine which scheme to use for authentication.</span></span>
<span data-ttu-id="ee919-151">Voor beelden zijn het Kerberos-protocol en NTLM.</span><span class="sxs-lookup"><span data-stu-id="ee919-151">Examples are the Kerberos protocol and NTLM.</span></span>

<span data-ttu-id="ee919-152">De standaard waarde is Negotiate.</span><span class="sxs-lookup"><span data-stu-id="ee919-152">The default value is Negotiate.</span></span>

```yaml
Type: Microsoft.WSMan.Management.ProxyAuthentication
Parameter Sets: (All)
Aliases:
Accepted values: Negotiate, Basic, Digest

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee919-153">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="ee919-153">-ProxyCredential</span></span>
<span data-ttu-id="ee919-154">Hiermee geeft u een gebruikers account op dat gemachtigd is om toegang te krijgen via een tussenliggende webproxy.</span><span class="sxs-lookup"><span data-stu-id="ee919-154">Specifies a user account that has permission to gain access through an intermediate Web proxy.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee919-155">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="ee919-155">-SkipCACheck</span></span>
<span data-ttu-id="ee919-156">Hiermee geeft u op dat, wanneer de verbinding via HTTPS maakt, niet door de client wordt gecontroleerd of het server certificaat is ondertekend door een vertrouwde certificerings instantie (CA).</span><span class="sxs-lookup"><span data-stu-id="ee919-156">Specifies that, when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>
<span data-ttu-id="ee919-157">Gebruik deze optie alleen als de externe computer wordt vertrouwd door een andere methode, bijvoorbeeld als de externe computer deel uitmaakt van een netwerk dat fysiek is beveiligd en geïsoleerd of als de externe computer wordt vermeld als een vertrouwde host in de WS-Management configuratie.</span><span class="sxs-lookup"><span data-stu-id="ee919-157">Use this option only when the remote computer is trusted by another method, for example, if the remote computer is part of a network that is physically secure and isolated or the remote computer is listed as a trusted host in the WS-Management configuration.</span></span>

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

### <span data-ttu-id="ee919-158">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="ee919-158">-SkipCNCheck</span></span>
<span data-ttu-id="ee919-159">Hiermee geeft u op dat de algemene naam (CN) van het certificaat van de server niet overeenkomt met de hostnaam van de server.</span><span class="sxs-lookup"><span data-stu-id="ee919-159">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="ee919-160">Dit wordt alleen gebruikt in externe bewerkingen met behulp van HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ee919-160">This is used only in remote operations using HTTPS.</span></span>
<span data-ttu-id="ee919-161">Deze optie mag alleen worden gebruikt voor vertrouwde computers.</span><span class="sxs-lookup"><span data-stu-id="ee919-161">This option should only be used for trusted computers.</span></span>

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

### <span data-ttu-id="ee919-162">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="ee919-162">-SkipRevocationCheck</span></span>
<span data-ttu-id="ee919-163">Geeft aan dat de verbinding de intrekkings status van het server certificaat niet verifieert.</span><span class="sxs-lookup"><span data-stu-id="ee919-163">Indicates that the connection does not validate the revocation status on the server certificate.</span></span>

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

### <span data-ttu-id="ee919-164">-SPNPort</span><span class="sxs-lookup"><span data-stu-id="ee919-164">-SPNPort</span></span>
<span data-ttu-id="ee919-165">Hiermee geeft u een poort nummer op dat moet worden toegevoegd aan de SPN (Service Principal Name) van de externe server.</span><span class="sxs-lookup"><span data-stu-id="ee919-165">Specifies a port number to append to the connection Service Principal Name (SPN) of the remote server.</span></span>
<span data-ttu-id="ee919-166">Er wordt een SPN gebruikt wanneer het verificatie mechanisme Kerberos of Negotiate is.</span><span class="sxs-lookup"><span data-stu-id="ee919-166">An SPN is used when the authentication mechanism is Kerberos or Negotiate.</span></span>

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

### <span data-ttu-id="ee919-167">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="ee919-167">-UseUTF16</span></span>
<span data-ttu-id="ee919-168">Geeft aan dat de verbinding de aanvraag in een UTF16-indeling versleutelt in plaats van UTF8-indeling.</span><span class="sxs-lookup"><span data-stu-id="ee919-168">Indicates that the connection encodes the request in UTF16 format instead of UTF8 format.</span></span>
<span data-ttu-id="ee919-169">De standaard waarde is UTF8-code ring.</span><span class="sxs-lookup"><span data-stu-id="ee919-169">The default is UTF8 encoding.</span></span>

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

### <span data-ttu-id="ee919-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee919-170">CommonParameters</span></span>
<span data-ttu-id="ee919-171">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee919-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee919-172">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ee919-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ee919-173">INVOER</span><span class="sxs-lookup"><span data-stu-id="ee919-173">INPUTS</span></span>

## <span data-ttu-id="ee919-174">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ee919-174">OUTPUTS</span></span>

### <span data-ttu-id="ee919-175">SessionOption</span><span class="sxs-lookup"><span data-stu-id="ee919-175">SessionOption</span></span>

## <span data-ttu-id="ee919-176">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ee919-176">NOTES</span></span>

## <span data-ttu-id="ee919-177">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ee919-177">RELATED LINKS</span></span>

[<span data-ttu-id="ee919-178">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="ee919-178">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="ee919-179">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ee919-179">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="ee919-180">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="ee919-180">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="ee919-181">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ee919-181">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="ee919-182">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ee919-182">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="ee919-183">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ee919-183">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="ee919-184">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="ee919-184">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="ee919-185">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ee919-185">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="ee919-186">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ee919-186">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="ee919-187">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ee919-187">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="ee919-188">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="ee919-188">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="ee919-189">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="ee919-189">Test-WSMan</span></span>](Test-WSMan.md)

