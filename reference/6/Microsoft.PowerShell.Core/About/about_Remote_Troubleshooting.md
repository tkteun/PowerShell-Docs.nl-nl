---
description: Hierin wordt beschreven hoe u problemen met externe bewerkingen oplost in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Troubleshooting
ms.openlocfilehash: b78f3004e316b6d4de1082b914970d3c8b56f955
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/29/2020
ms.locfileid: "93253254"
---
# <a name="about-remote-troubleshooting"></a><span data-ttu-id="1e9dc-104">Over externe probleem oplossing</span><span class="sxs-lookup"><span data-stu-id="1e9dc-104">About Remote Troubleshooting</span></span>

## <a name="short-description"></a><span data-ttu-id="1e9dc-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="1e9dc-105">Short description</span></span>
<span data-ttu-id="1e9dc-106">Hierin wordt beschreven hoe u problemen met externe bewerkingen oplost in Power shell.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-106">Describes how to troubleshoot remote operations in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="1e9dc-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="1e9dc-107">Long description</span></span>

<span data-ttu-id="1e9dc-108">In deze sectie worden enkele van de problemen beschreven die kunnen optreden bij het gebruik van de externe functies van Power shell die zijn gebaseerd op WS-Management technologie en worden oplossingen voor deze problemen voorgesteld.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-108">This section describes some of the problems that you might encounter when using the remoting features of PowerShell that are based on WS-Management technology and it suggests solutions to these problems.</span></span>

<span data-ttu-id="1e9dc-109">Zie [about_Remote](about_remote.md) en [about_Remote_Requirements](about_Remote_Requirements.md) voor meer informatie over de configuratie en het basis gebruik voordat u externe communicatie van Power shell kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-109">Before using PowerShell remoting, see [about_Remote](about_remote.md) and [about_Remote_Requirements](about_Remote_Requirements.md) for guidance on configuration and basic use.</span></span> <span data-ttu-id="1e9dc-110">Daarnaast bevat de Help-onderwerpen voor elk van de externe cmdlets, met name de parameter beschrijvingen, nuttige informatie die is ontworpen om u te helpen bij het voor komen van problemen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-110">Also, the Help topics for each of the remoting cmdlets, particularly the parameter descriptions, have useful information that is designed to help you avoid problems.</span></span>

> [!NOTE]
> <span data-ttu-id="1e9dc-111">Als u de instellingen voor de lokale computer in het WSMan:-station wilt bekijken of wijzigen, inclusief wijzigingen in de sessie configuraties, vertrouwde hosts, poorten of listeners, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="1e9dc-111">To view or change settings for the local computer in the WSMan: drive, including changes to the session configurations, trusted hosts, ports, or listeners, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="troubleshooting-permission-and-authentication-issues"></a><span data-ttu-id="1e9dc-112">Problemen met machtigingen en verificatie oplossen</span><span class="sxs-lookup"><span data-stu-id="1e9dc-112">Troubleshooting permission and authentication issues</span></span>

<span data-ttu-id="1e9dc-113">In deze sectie worden externe problemen besproken die betrekking hebben op gebruikers-en computer machtigingen en externe vereisten.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-113">This section discusses remoting problems that are related to user and computer permissions and remoting requirements.</span></span>

### <a name="how-to-run-as-administrator"></a><span data-ttu-id="1e9dc-114">Als administrator uitvoeren</span><span class="sxs-lookup"><span data-stu-id="1e9dc-114">How to run as administrator</span></span>

```
ERROR: Access is denied. You need to run this cmdlet from an elevated
process.
```

<span data-ttu-id="1e9dc-115">Windows Power shell starten met de optie **als administrator uitvoeren** om een externe sessie op de lokale computer te starten of instellingen te bekijken of te wijzigen voor de lokale computer in het WSMan:-station, inclusief wijzigingen in de sessie configuraties, vertrouwde hosts, poorten of listeners.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-115">To start a remote session on the local computer, or to view or change settings for the local computer in the WSMan: drive, including changes to the session configurations, trusted hosts, ports, or listeners, start Windows PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="1e9dc-116">Windows Power shell starten met de optie **als administrator uitvoeren** :</span><span class="sxs-lookup"><span data-stu-id="1e9dc-116">To start Windows PowerShell with the **Run as administrator** option:</span></span>

- <span data-ttu-id="1e9dc-117">Klik met de rechter muisknop op een Windows Power shell-pictogram (of Windows PowerShell ISE) en klik vervolgens op **als administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-117">Right-click a Windows PowerShell (or Windows PowerShell ISE) icon and then click **Run as administrator**.</span></span>

  <span data-ttu-id="1e9dc-118">Windows Power shell starten met de optie **als administrator uitvoeren** in Windows 7 en windows server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-118">To start Windows PowerShell with the **Run as administrator** option in Windows 7 and Windows Server 2008 R2.</span></span>

- <span data-ttu-id="1e9dc-119">Klik in de Windows-taak balk met de rechter muisknop op het Windows Power shell-pictogram en klik vervolgens op **als administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-119">In the Windows taskbar, right-click the Windows PowerShell icon, and then click **Run as administrator**.</span></span>

  <span data-ttu-id="1e9dc-120">In Windows Server 2008 R2 wordt het Windows Power shell-pictogram standaard vastgemaakt aan de taak balk.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-120">In Windows Server 2008 R2, the Windows PowerShell icon is pinned to the taskbar by default.</span></span>

### <a name="how-to-enable-remoting"></a><span data-ttu-id="1e9dc-121">Externe toegang inschakelen</span><span class="sxs-lookup"><span data-stu-id="1e9dc-121">How to enable remoting</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to
listen for requests on the correct port and HTTP URL.
```

<span data-ttu-id="1e9dc-122">Er is geen configuratie vereist om een computer in staat te stellen externe opdrachten te verzenden.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-122">No configuration is required to enable a computer to send remote commands.</span></span>
<span data-ttu-id="1e9dc-123">Als u externe opdrachten wilt ontvangen, moet externe communicatie van Power shell op de computer zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-123">However, to receive remote commands, PowerShell remoting must be enabled on the computer.</span></span> <span data-ttu-id="1e9dc-124">U kunt onder andere het starten van de WinRM-service, het opstart type voor de WinRM-service instellen op automatisch, listeners maken voor HTTP-en HTTPS-verbindingen en standaard sessie configuraties maken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-124">Enabling includes starting the WinRM service, setting the startup type for the WinRM service to Automatic, creating listeners for HTTP and HTTPS connections, and creating default session configurations.</span></span>

<span data-ttu-id="1e9dc-125">Windows Power shell Remoting is standaard ingeschakeld op Windows Server 2012 en nieuwere versies van Windows Server.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-125">Windows PowerShell remoting is enabled on Windows Server 2012 and newer releases of Windows Server by default.</span></span> <span data-ttu-id="1e9dc-126">Op alle andere systemen voert u de `Enable-PSRemoting` cmdlet uit om externe toegang in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-126">On all other systems, run the `Enable-PSRemoting` cmdlet to enable remoting.</span></span> <span data-ttu-id="1e9dc-127">U kunt ook de `Enable-PSRemoting` cmdlet uitvoeren om externe toegang tot Windows server 2012 en nieuwere releases van Windows Server opnieuw in te scha kelen als externe toegang is uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-127">You can also run the `Enable-PSRemoting` cmdlet to re-enable remoting on Windows Server 2012 and newer releases of Windows Server if remoting is disabled.</span></span>

<span data-ttu-id="1e9dc-128">Als u een computer wilt configureren voor het ontvangen van externe opdrachten, gebruikt u de `Enable-PSRemoting` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-128">To configure a computer to receive remote commands, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="1e9dc-129">Met de volgende opdracht worden alle vereiste externe instellingen ingeschakeld, worden de sessie configuraties ingeschakeld en wordt de WinRM-service opnieuw gestart om de wijzigingen van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-129">The following command enables all required remote settings, enables the session configurations, and restarts the WinRM service to make the changes effective.</span></span>

`Enable-PSRemoting`

<span data-ttu-id="1e9dc-130">Als u alle gebruikers prompts wilt onderdrukken, typt u:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-130">To suppress all user prompts, type:</span></span>

`Enable-PSRemoting -Force`

<span data-ttu-id="1e9dc-131">Zie [Enable-PSRemoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-131">For more information, see [Enable-PSRemoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting).</span></span>

### <a name="how-to-enable-remoting-in-an-enterprise"></a><span data-ttu-id="1e9dc-132">Externe toegang inschakelen in een onderneming</span><span class="sxs-lookup"><span data-stu-id="1e9dc-132">How to enable remoting in an enterprise</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="1e9dc-133">Gebruik de cmdlet om één computer in staat te stellen externe Power shell-opdrachten te ontvangen en verbindingen te accepteren `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="1e9dc-133">To enable a single computer to receive remote PowerShell commands and accept connections, use the `Enable-PSRemoting` cmdlet.</span></span>

<span data-ttu-id="1e9dc-134">Als u externe toegang wilt inschakelen voor meerdere computers in een onderneming, kunt u de volgende schaal bare opties gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-134">To enable remoting for multiple computers in an enterprise, you can use the following scaled options.</span></span>

- <span data-ttu-id="1e9dc-135">Als u listeners voor externe toegang wilt configureren, schakelt u het groeps beleid **automatische configuratie van listeners toestaan** in.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-135">To configure listeners for remoting, enable the **Allow automatic configuration of listeners** group policy.</span></span>

- <span data-ttu-id="1e9dc-136">Als u het opstart type van Windows Remote Management (WinRM) wilt instellen op automatisch op meerdere computers, gebruikt u de `Set-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-136">To set the startup type of the Windows Remote Management (WinRM) to Automatic on multiple computers, use the `Set-Service` cmdlet.</span></span>

- <span data-ttu-id="1e9dc-137">Als u een firewall uitzondering wilt inschakelen, gebruikt u de Windows Firewall: groeps beleid voor **lokale poort uitzonderingen toestaan** .</span><span class="sxs-lookup"><span data-stu-id="1e9dc-137">To enable a firewall exception, use the **Windows Firewall: Allow Local Port Exceptions** group policy.</span></span>

### <a name="how-to-enable-listeners-by-using-a-group-policy"></a><span data-ttu-id="1e9dc-138">Listeners inschakelen met behulp van een groeps beleid</span><span class="sxs-lookup"><span data-stu-id="1e9dc-138">How to enable listeners by using a group policy</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="1e9dc-139">Als u de listeners voor alle computers in een domein wilt configureren, schakelt u het beleid **automatische configuratie van listeners toestaan** in het volgende groepsbeleid pad:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-139">To configure the listeners for all computers in a domain, enable the **Allow automatic configuration of listeners** policy in the following Group Policy path:</span></span>

```
Computer Configuration\Administrative Templates\Windows Components
    \Windows Remote Management (WinRM)\WinRM service
```

<span data-ttu-id="1e9dc-140">Schakel het beleid in en geef de IPv4-en IPv6-filters op.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-140">Enable the policy and specify the IPv4 and IPv6 filters.</span></span> <span data-ttu-id="1e9dc-141">Joker tekens ( `*` ) zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-141">Wildcards (`*`) are permitted.</span></span>

### <a name="how-to-enable-remoting-on-public-networks"></a><span data-ttu-id="1e9dc-142">Externe toegang inschakelen op open bare netwerken</span><span class="sxs-lookup"><span data-stu-id="1e9dc-142">How to enable remoting on public networks</span></span>

```
ERROR:  Unable to check the status of the firewall
```

<span data-ttu-id="1e9dc-143">De `Enable-PSRemoting` cmdlet retourneert deze fout wanneer het lokale netwerk openbaar is en de para meter **SkipNetworkProfileCheck** niet in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-143">The `Enable-PSRemoting` cmdlet returns this error when the local network is public and the **SkipNetworkProfileCheck** parameter is not used in the command.</span></span>

<span data-ttu-id="1e9dc-144">Op Server versies van Windows is `Enable-PSRemoting` geslaagd op alle typen netwerk locaties.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-144">On server versions of Windows, `Enable-PSRemoting` succeeds on all network location types.</span></span> <span data-ttu-id="1e9dc-145">Er worden firewall regels gemaakt waarmee externe toegang tot privé-en domein netwerken (Home-en work) mogelijk wordt.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-145">It creates firewall rules that allow remote access to private and domain ("Home" and "Work") networks.</span></span> <span data-ttu-id="1e9dc-146">Voor open bare netwerken maakt firewall regels die externe toegang vanaf hetzelfde lokale subnet toestaan.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-146">For public networks, it creates firewall rules that allows remote access from the same local subnet.</span></span>

<span data-ttu-id="1e9dc-147">Op client versies van Windows `Enable-PSRemoting` slaagt op particuliere en domein netwerken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-147">On client versions of Windows, `Enable-PSRemoting` succeeds on private and domain networks.</span></span> <span data-ttu-id="1e9dc-148">Standaard mislukt het op open bare netwerken, maar als u de para meter **SkipNetworkProfileCheck** gebruikt, `Enable-PSRemoting` slaagt en maakt een firewall regel die verkeer van hetzelfde lokale subnet toestaat.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-148">By default, it fails on public networks, but if you use the **SkipNetworkProfileCheck** parameter, `Enable-PSRemoting` succeeds and creates a firewall rule that allows traffic from the same local subnet.</span></span>

<span data-ttu-id="1e9dc-149">Voer de volgende opdracht uit om de beperking van het lokale subnet op open bare netwerken te verwijderen en externe toegang vanaf elke locatie toe te staan:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-149">To remove the local subnet restriction on public networks and allow remote access from any location, run the following command:</span></span>

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

<span data-ttu-id="1e9dc-150">De `Set-NetFirewallRule` cmdlet wordt geëxporteerd door de module netsecurity.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-150">The `Set-NetFirewallRule` cmdlet is exported by the NetSecurity module.</span></span>

> [!NOTE]
> <span data-ttu-id="1e9dc-151">In Windows Power Shell 2,0 worden op computers met server versies van Windows `Enable-PSRemoting` firewall regels gemaakt waarmee externe toegang wordt toegestaan op particuliere, domein en open bare netwerken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-151">In Windows PowerShell 2.0, on computers running server versions of Windows, `Enable-PSRemoting` creates firewall rules that allow remote access on private, domain and public networks.</span></span> <span data-ttu-id="1e9dc-152">Op computers met client versies van Windows `Enable-PSRemoting` maakt firewall regels die alleen externe toegang toestaan op particuliere en domein netwerken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-152">On computers running client versions of Windows, `Enable-PSRemoting` creates firewall rules that allow remote access only on private and domain networks.</span></span>

### <a name="how-to-enable-a-firewall-exception-by-using-a-group-policy"></a><span data-ttu-id="1e9dc-153">Een firewall uitzondering inschakelen met behulp van een groeps beleid</span><span class="sxs-lookup"><span data-stu-id="1e9dc-153">How to enable a firewall exception by using a group policy</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="1e9dc-154">Als u een firewall-uitzonde ring voor alle computers in een domein wilt inschakelen, schakelt u het **Windows Firewall: beleid voor lokale poort uitzonderingen toestaan** in het volgende groepsbeleid pad:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-154">To enable a firewall exception for in all computers in a domain, enable the **Windows Firewall: Allow local port exceptions** policy in the following Group Policy path:</span></span>

```
Computer Configuration\Administrative Templates\Network
    \Network Connections\Windows Firewall\Domain Profile
```

<span data-ttu-id="1e9dc-155">Met dit beleid kunnen leden van de groep Administrators op de computer **Windows Firewall** in **configuratie scherm** gebruiken om een firewall uitzondering te maken voor de Windows Remote Management-service.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-155">This policy allows members of the Administrators group on the computer to use **Windows Firewall** in **Control Panel** to create a firewall exception for the Windows Remote Management service.</span></span>

<span data-ttu-id="1e9dc-156">Als de configuratie van het beleid onjuist is, wordt mogelijk de volgende fout weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-156">If the policy configuration is incorrect you may receive the following error:</span></span>

```
The client cannot connect to the destination specified in the request. Verify
that the service on the destination is running and is accepting requests.
```

<span data-ttu-id="1e9dc-157">Een configuratie fout in het beleid resulteert in een lege waarde voor de eigenschap **ListeningOn** .</span><span class="sxs-lookup"><span data-stu-id="1e9dc-157">A configuration error in the policy results in an empty value for the **ListeningOn** property.</span></span> <span data-ttu-id="1e9dc-158">Gebruik de volgende opdracht om de waarde te controleren.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-158">Use the following command to check the value.</span></span>

```powershell
PS> Get-WSManInstance winrm/config/listener -Enumerate

cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
Source                : GPO
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 5985
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {}
```

### <a name="how-to-set-the-startup-type-of-the-winrm-service"></a><span data-ttu-id="1e9dc-159">Het opstart type van de WinRM-service instellen</span><span class="sxs-lookup"><span data-stu-id="1e9dc-159">How to set the startup type of the WinRM service</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="1e9dc-160">Externe communicatie van Power shell is afhankelijk van de WinRM-service (Windows Remote Management).</span><span class="sxs-lookup"><span data-stu-id="1e9dc-160">PowerShell remoting depends upon the Windows Remote Management (WinRM) service.</span></span>
<span data-ttu-id="1e9dc-161">De service moet worden uitgevoerd om externe opdrachten te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-161">The service must be running to support remote commands.</span></span>

<span data-ttu-id="1e9dc-162">In Server versies van Windows wordt het opstart type van de WinRM-service (Windows Remote Management) automatisch.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-162">On server versions of Windows, the startup type of the Windows Remote Management (WinRM) service is Automatic.</span></span>

<span data-ttu-id="1e9dc-163">Op client versies van Windows is de WinRM-service echter standaard uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-163">However, on client versions of Windows, the WinRM service is disabled by default.</span></span>

<span data-ttu-id="1e9dc-164">Als u het opstart type van een service op een externe computer wilt instellen, gebruikt u de `Set-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-164">To set the startup type of a service on a remote computer, use the `Set-Service` cmdlet.</span></span>

<span data-ttu-id="1e9dc-165">Als u de opdracht op meerdere computers wilt uitvoeren, kunt u een tekst bestand of CSV-bestand van de computer namen maken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-165">To run the command on multiple computers, you can create a text file or CSV file of the computer names.</span></span>

<span data-ttu-id="1e9dc-166">Met de volgende opdrachten wordt bijvoorbeeld een lijst met computer namen uit het `Servers.txt` bestand opgehaald en wordt vervolgens het opstart type van de WinRM-service op alle computers ingesteld op **automatisch**.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-166">For example, the following commands get a list of computer names from the `Servers.txt` file and then sets the startup type of the WinRM service on all of the computers to **Automatic**.</span></span>

```powershell
$servers = Get-Content servers.txt
Set-Service WinRM -ComputerName $servers -startuptype Automatic
```

<span data-ttu-id="1e9dc-167">Als u de resultaten wilt weer geven, gebruikt u de `Get-WMIObject` cmdlet met het **Win32_Service** -object.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-167">To see the results use the `Get-WMIObject` cmdlet with the **Win32_Service** object.</span></span> <span data-ttu-id="1e9dc-168">Zie [set-service](xref:Microsoft.PowerShell.Management.Set-Service)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-168">For more information, see [Set-Service](xref:Microsoft.PowerShell.Management.Set-Service).</span></span>

### <a name="how-to-recreate-the-default-session-configurations"></a><span data-ttu-id="1e9dc-169">De standaard sessie configuraties opnieuw maken</span><span class="sxs-lookup"><span data-stu-id="1e9dc-169">How to recreate the default session configurations</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="1e9dc-170">Om verbinding te maken met de lokale computer en opdrachten op afstand uit te voeren, moet de lokale computer sessie configuraties voor externe opdrachten bevatten.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-170">To connect to the local computer and run commands remotely, the local computer must include session configurations for remote commands.</span></span>

<span data-ttu-id="1e9dc-171">Wanneer u gebruikt `Enable-PSRemoting` , worden standaard sessie configuraties gemaakt op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-171">When you use `Enable-PSRemoting`, it creates default session configurations on the local computer.</span></span> <span data-ttu-id="1e9dc-172">Externe gebruikers gebruiken deze sessie configuraties wanneer een externe opdracht de para meter **configuratiepad** niet bevat.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-172">Remote users use these session configurations whenever a remote command does not include the **ConfigurationName** parameter.</span></span>

<span data-ttu-id="1e9dc-173">Als de standaard configuraties op een computer niet zijn geregistreerd of verwijderd, gebruikt `Enable-PSRemoting` u de cmdlet om ze opnieuw te maken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-173">If the default configurations on a computer are unregistered or deleted, use the `Enable-PSRemoting` cmdlet to recreate them.</span></span> <span data-ttu-id="1e9dc-174">U kunt deze cmdlet herhaaldelijk gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-174">You can use this cmdlet repeatedly.</span></span> <span data-ttu-id="1e9dc-175">Er worden geen fouten gegenereerd als een functie al is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-175">It does not generate errors if a feature is already configured.</span></span>

<span data-ttu-id="1e9dc-176">Als u de standaard sessie configuraties wijzigt en de oorspronkelijke standaard sessie configuraties wilt herstellen, gebruikt u de `Unregister-PSSessionConfiguration` cmdlet om de gewijzigde sessie configuraties te verwijderen en gebruikt u vervolgens de `Enable-PSRemoting` cmdlet om ze te herstellen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-176">If you change the default session configurations and want to restore the original default session configurations, use the `Unregister-PSSessionConfiguration` cmdlet to delete the changed session configurations and then use the `Enable-PSRemoting` cmdlet to restore them.</span></span>
<span data-ttu-id="1e9dc-177">`Enable-PSRemoting` de bestaande sessie configuraties worden niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-177">`Enable-PSRemoting` does not change existing session configurations.</span></span>

> [!NOTE]
> <span data-ttu-id="1e9dc-178">Wanneer `Enable-PSRemoting` de standaard sessie configuratie herstelt, worden er geen expliciete Security descriptors gemaakt voor de configuraties.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-178">When `Enable-PSRemoting` restores the default session configuration, it does not create explicit security descriptors for the configurations.</span></span> <span data-ttu-id="1e9dc-179">In plaats daarvan nemen de configuraties de security descriptor van de RootSDDL over, die standaard veilig is.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-179">Instead, the configurations inherit the security descriptor of the RootSDDL, which is secure by default.</span></span>

<span data-ttu-id="1e9dc-180">Als u de RootSDDL-security descriptor wilt zien, typt u:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-180">To see the RootSDDL security descriptor, type:</span></span>

```powershell
Get-Item wsman:\localhost\Service\RootSDDL
```

<span data-ttu-id="1e9dc-181">Als u de RootSDDL wilt wijzigen, gebruikt u de `Set-Item` cmdlet in het station WSMan:.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-181">To change the RootSDDL, use the `Set-Item` cmdlet in the WSMan: drive.</span></span> <span data-ttu-id="1e9dc-182">Als u de security descriptor van een sessie configuratie wilt wijzigen, gebruikt u de `Set-PSSessionConfiguration` cmdlet met de para meters **SecurityDescriptorSDDL** of **ShowSecurityDescriptorUI** .</span><span class="sxs-lookup"><span data-stu-id="1e9dc-182">To change the security descriptor of a session configuration, use the `Set-PSSessionConfiguration` cmdlet with the **SecurityDescriptorSDDL** or **ShowSecurityDescriptorUI** parameters.</span></span>

<span data-ttu-id="1e9dc-183">Zie het Help-onderwerp voor de WSMan-provider (' Get-Help WSMan ') voor meer informatie over WSMan: drive.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-183">For more information about the WSMan: drive, see the Help topic for the WSMan provider ("Get-Help wsman").</span></span>

### <a name="how-to-provide-administrator-credentials"></a><span data-ttu-id="1e9dc-184">Beheerders referenties opgeven</span><span class="sxs-lookup"><span data-stu-id="1e9dc-184">How to provide administrator credentials</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="1e9dc-185">Als u een PSSession wilt maken of opdrachten wilt uitvoeren op een externe computer, moet de huidige gebruiker standaard lid zijn van de groep Administrators op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-185">To create a PSSession or run commands on a remote computer, by default, the current user must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="1e9dc-186">Referenties zijn soms vereist, zelfs wanneer de huidige gebruiker is aangemeld met een account dat lid is van de groep Administrators.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-186">Credentials are sometimes required even when the current user is logged on to an account that is a member of the Administrators group.</span></span>

<span data-ttu-id="1e9dc-187">Als de huidige gebruiker lid is van de groep Administrators op de externe computer of u de referenties van een lid van de groep Administrators kunt opgeven, gebruikt u de para meter **Credential** van de `New-PSSession` - `Enter-PSSession` of- `Invoke-Command` cmdlets om extern verbinding te maken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-187">If the current user is a member of the Administrators group on the remote computer, or can provide the credentials of a member of the Administrators group, use the **Credential** parameter of the `New-PSSession`, `Enter-PSSession` or `Invoke-Command` cmdlets to connect remotely.</span></span>

<span data-ttu-id="1e9dc-188">De volgende opdracht geeft bijvoorbeeld de referenties van een beheerder.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-188">For example, the following command provides the credentials of an Administrator.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\Admin01
```

<span data-ttu-id="1e9dc-189">Zie [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) of [invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)voor meer informatie over de para meter **Credential** .</span><span class="sxs-lookup"><span data-stu-id="1e9dc-189">For more information about the **Credential** parameter, see [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) or [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command).</span></span>

### <a name="how-to-enable-remoting-for-non-administrative-users"></a><span data-ttu-id="1e9dc-190">Externe toegang inschakelen voor gebruikers die geen beheerder zijn</span><span class="sxs-lookup"><span data-stu-id="1e9dc-190">How to enable remoting for non-administrative users</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="1e9dc-191">Om een PSSession te maken of een opdracht uit te voeren op een externe computer, moet de gebruiker gemachtigd zijn om de sessie configuraties te gebruiken op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-191">To establish a PSSession or run a command on a remote computer, the user must have permission to use the session configurations on the remote computer.</span></span>

<span data-ttu-id="1e9dc-192">Standaard zijn alleen leden van de groep Administrators op een computer gemachtigd om de standaard sessie configuraties te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-192">By default, only members of the Administrators group on a computer have permission to use the default session configurations.</span></span> <span data-ttu-id="1e9dc-193">Daarom kunnen alleen leden van de groep Administrators op afstand verbinding maken met de computer.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-193">Therefore, only members of the Administrators group can connect to the computer remotely.</span></span>

<span data-ttu-id="1e9dc-194">Om andere gebruikers toe te staan verbinding te maken met de lokale computer, geeft u de gebruiker de bevoegdheid om de standaard sessie configuraties op de lokale computer uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-194">To allow other users to connect to the local computer, give the user Execute permissions to the default session configurations on the local computer.</span></span>

<span data-ttu-id="1e9dc-195">Met de volgende opdracht wordt een eigenschappen venster geopend waarmee u de security descriptor van de standaard configuratie van de micro soft. Power shell-sessie op de lokale computer kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-195">The following command opens a property sheet that lets you change the security descriptor of the default Microsoft.PowerShell session configuration on the local computer.</span></span>

```powershell
Set-PSSessionConfiguration Microsoft.PowerShell -ShowSecurityDescriptorUI
```

<span data-ttu-id="1e9dc-196">Zie [about_Session_Configurations](about_Session_Configurations.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-196">For more information, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

### <a name="how-to-enable-remoting-for-administrators-in-other-domains"></a><span data-ttu-id="1e9dc-197">Externe toegang inschakelen voor beheerders in andere domeinen</span><span class="sxs-lookup"><span data-stu-id="1e9dc-197">How to enable remoting for administrators in other domains</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="1e9dc-198">Wanneer een gebruiker in een ander domein lid is van de groep Administrators op de lokale computer, kan de gebruiker niet extern verbinding maken met de lokale computer met Administrator bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-198">When a user in another domain is a member of the Administrators group on the local computer, the user cannot connect to the local computer remotely with Administrator privileges.</span></span> <span data-ttu-id="1e9dc-199">Externe verbindingen van andere domeinen worden standaard alleen uitgevoerd met standaard gebruikers privilege-tokens.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-199">By default, remote connections from other domains run with only standard user privilege tokens.</span></span>

<span data-ttu-id="1e9dc-200">U kunt echter de register vermelding **LocalAccountTokenFilterPolicy** gebruiken om het standaard gedrag te wijzigen en externe gebruikers die lid zijn van de groep Administrators toe te staan om met beheerders bevoegdheden uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-200">However, you can use the **LocalAccountTokenFilterPolicy** registry entry to change the default behavior and allow remote users who are members of the Administrators group to run with Administrator privileges.</span></span>

> [!CAUTION]
> <span data-ttu-id="1e9dc-201">Met de **LocalAccountTokenFilterPolicy** -vermelding worden externe beperkingen van Gebruikersaccountbeheer (UAC) uitgeschakeld voor alle gebruikers van alle betrokken computers.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-201">The **LocalAccountTokenFilterPolicy** entry disables user account control (UAC) remote restrictions for all users of all affected computers.</span></span> <span data-ttu-id="1e9dc-202">Houd rekening met de implicaties van deze instelling zorgvuldig voordat u het beleid wijzigt.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-202">Consider the implications of this setting carefully before changing the policy.</span></span>

<span data-ttu-id="1e9dc-203">Als u het beleid wilt wijzigen, gebruikt u de volgende opdracht om de waarde van de register vermelding **LocalAccountTokenFilterPolicy** in te stellen op 1.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-203">To change the policy, use the following command to set the value of the **LocalAccountTokenFilterPolicy** registry entry to 1.</span></span>

```powershell
New-ItemProperty -Name LocalAccountTokenFilterPolicy `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System `
  -PropertyType DWord -Value 1
```

### <a name="how-to-use-an-ip-address-in-a-remote-command"></a><span data-ttu-id="1e9dc-204">Een IP-adres gebruiken in een externe opdracht</span><span class="sxs-lookup"><span data-stu-id="1e9dc-204">How to use an ip address in a remote command</span></span>

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

<span data-ttu-id="1e9dc-205">De para meter **ComputerName** van de `New-PSSession` - `Enter-PSSession` en `Invoke-Command` -cmdlets accepteert een IP-adres als een geldige waarde.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-205">The **ComputerName** parameter of the `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets accepts an IP address as a valid value.</span></span> <span data-ttu-id="1e9dc-206">Omdat Kerberos-verificatie echter geen ondersteuning biedt voor IP-adressen, wordt NTLM-verificatie standaard gebruikt wanneer u een IP-adres opgeeft.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-206">However, because Kerberos authentication does not support IP addresses, NTLM authentication is used by default whenever you specify an IP address.</span></span>

<span data-ttu-id="1e9dc-207">Als NTLM-verificatie wordt gebruikt, is de volgende procedure vereist voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-207">When using NTLM authentication, the following procedure is required for remoting.</span></span>

1. <span data-ttu-id="1e9dc-208">Configureer de computer voor HTTPS-Trans Port of Voeg de IP-adressen van de externe computers toe aan de lijst TrustedHosts op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-208">Configure the computer for HTTPS transport or add the IP addresses of the remote computers to the TrustedHosts list on the local computer.</span></span>

1. <span data-ttu-id="1e9dc-209">Gebruik de para meter **Credential** in alle externe opdrachten.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-209">Use the **Credential** parameter in all remote commands.</span></span>

   <span data-ttu-id="1e9dc-210">Dit is ook vereist wanneer u de referenties van de huidige gebruiker verzendt.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-210">This is required even when you are submitting the credentials of the current user.</span></span>

### <a name="how-to-connect-remotely-from-a-workgroup-based-computer"></a><span data-ttu-id="1e9dc-211">Extern verbinding maken vanaf een computer op basis van een werk groep</span><span class="sxs-lookup"><span data-stu-id="1e9dc-211">How to connect remotely from a workgroup-based computer</span></span>

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

<span data-ttu-id="1e9dc-212">Als de lokale computer zich niet in een domein bevindt, is de volgende procedure vereist voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-212">When the local computer is not in a domain, the following procedure is required for remoting.</span></span>

1. <span data-ttu-id="1e9dc-213">Configureer de computer voor HTTPS-Trans Port of Voeg de namen van de externe computers toe aan de lijst TrustedHosts op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-213">Configure the computer for HTTPS transport or add the names of the remote computers to the TrustedHosts list on the local computer.</span></span>

1. <span data-ttu-id="1e9dc-214">Controleer of er een wacht woord is ingesteld op de computer die is gebaseerd op werk groep.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-214">Verify that a password is set on the workgroup-based computer.</span></span> <span data-ttu-id="1e9dc-215">Als er geen wacht woord is ingesteld of als de wachtwoord waarde leeg is, kunt u geen externe opdrachten uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-215">If a password is not set or the password value is empty, you cannot run remote commands.</span></span>

   <span data-ttu-id="1e9dc-216">Als u wacht woord voor uw gebruikers account wilt instellen, gebruikt u gebruikers accounts in het configuratie scherm.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-216">To set password for your user account, use User Accounts in Control Panel.</span></span>

1. <span data-ttu-id="1e9dc-217">Gebruik de para meter **Credential** in alle externe opdrachten.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-217">Use the **Credential** parameter in all remote commands.</span></span>

   <span data-ttu-id="1e9dc-218">Dit is ook vereist wanneer u de referenties van de huidige gebruiker verzendt.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-218">This is required even when you are submitting the credentials of the current user.</span></span>

### <a name="how-to-add-a-computer-to-the-trusted-hosts-list"></a><span data-ttu-id="1e9dc-219">Een computer toevoegen aan de lijst met vertrouwde hosts</span><span class="sxs-lookup"><span data-stu-id="1e9dc-219">How to add a computer to the trusted hosts list</span></span>

<span data-ttu-id="1e9dc-220">Het TrustedHosts-item kan een door komma's gescheiden lijst met computer namen, IP-adressen en volledig gekwalificeerde domein namen bevatten.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-220">The TrustedHosts item can contain a comma-separated list of computer names, IP addresses, and fully-qualified domain names.</span></span> <span data-ttu-id="1e9dc-221">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-221">Wildcards are permitted.</span></span>

<span data-ttu-id="1e9dc-222">Als u de lijst met vertrouwde hosts wilt weer geven of wijzigen, gebruikt u het station WSMan:.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-222">To view or change the trusted host list, use the WSMan: drive.</span></span> <span data-ttu-id="1e9dc-223">Het TrustedHost-item bevindt zich in het `WSMan:\localhost\Client` knoop punt.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-223">The TrustedHost item is in the `WSMan:\localhost\Client` node.</span></span>

<span data-ttu-id="1e9dc-224">Alleen leden van de groep Administrators op de computer zijn gemachtigd om de lijst met vertrouwde hosts op de computer te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-224">Only members of the Administrators group on the computer have permission to change the list of trusted hosts on the computer.</span></span>

<span data-ttu-id="1e9dc-225">Let op: de waarde die u voor het TrustedHosts-item instelt, is van invloed op alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-225">Caution: The value that you set for the TrustedHosts item affects all users of the computer.</span></span>

<span data-ttu-id="1e9dc-226">Als u de lijst met vertrouwde hosts wilt weer geven, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-226">To view the list of trusted hosts, use the following command:</span></span>

```powershell
Get-Item wsman:\localhost\Client\TrustedHosts
```

<span data-ttu-id="1e9dc-227">U kunt ook de `Set-Location` cmdlet (alias = cd) gebruiken om te navigeren naar de locatie WSMan: station.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-227">You can also use the `Set-Location` cmdlet (alias = cd) to navigate though the WSMan: drive to the location.</span></span> <span data-ttu-id="1e9dc-228">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-228">For example:</span></span>

```powershell
cd WSMan:\localhost\Client; dir
```

<span data-ttu-id="1e9dc-229">Als u alle computers aan de lijst met vertrouwde hosts wilt toevoegen, gebruikt u de volgende opdracht, waarmee de waarde \* (alle) wordt geplaatst in de computer naam</span><span class="sxs-lookup"><span data-stu-id="1e9dc-229">To add all computers to the list of trusted hosts, use the following command, which places a value of \* (all) in the ComputerName</span></span>

```powershell
Set-Item wsman:localhost\client\trustedhosts -Value *
```

<span data-ttu-id="1e9dc-230">U kunt ook een Joker teken ( `*` ) gebruiken om alle computers in een bepaald domein toe te voegen aan de lijst met vertrouwde hosts.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-230">You can also use a wildcard character (`*`) to add all computers in a particular domain to the list of trusted hosts.</span></span> <span data-ttu-id="1e9dc-231">Met de volgende opdracht worden alle computers in het fabrikam-domein bijvoorbeeld toegevoegd aan de lijst met vertrouwde hosts.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-231">For example, the following command adds all of the computers in the Fabrikam domain to the list of trusted hosts.</span></span>

```powershell
Set-Item wsman:localhost\client\trustedhosts *.fabrikam.com
```

<span data-ttu-id="1e9dc-232">Gebruik de volgende opdracht indeling om de namen van bepaalde computers toe te voegen aan de lijst met vertrouwde hosts:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-232">To add the names of particular computers to the list of trusted hosts, use the following command format:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <ComputerName>
```

<span data-ttu-id="1e9dc-233">waarbij elke waarde `<ComputerName>` de volgende notatie moet hebben:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-233">where each value `<ComputerName>` must have the following format:</span></span>

```
<Computer>.<Domain>.<Company>.<top-level-domain>
```

<span data-ttu-id="1e9dc-234">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-234">For example:</span></span>

```powershell
$server = 'Server01.Domain01.Fabrikam.com'
Set-Item wsman:\localhost\Client\TrustedHosts -Value $server
```

<span data-ttu-id="1e9dc-235">Als u een computer naam wilt toevoegen aan een bestaande lijst met vertrouwde hosts, slaat u eerst de huidige waarde op in een variabele en stelt u de waarde in op een door komma's gescheiden lijst met de huidige en nieuwe waarden.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-235">To add a computer name to an existing list of trusted hosts, first save the current value in a variable, and then set the value to a comma-separated list that includes the current and new values.</span></span>

<span data-ttu-id="1e9dc-236">Als u bijvoorbeeld de Server01-computer aan een bestaande lijst met vertrouwde hosts wilt toevoegen, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-236">For example, to add the Server01 computer to an existing list of trusted hosts, use the following command</span></span>

```powershell
$curValue = (Get-Item wsman:\localhost\Client\TrustedHosts).value

Set-Item wsman:\localhost\Client\TrustedHosts -Value `
  "$curValue, Server01.Domain01.Fabrikam.com"
```

<span data-ttu-id="1e9dc-237">Als u de IP-adressen van bepaalde computers wilt toevoegen aan de lijst met vertrouwde hosts, gebruikt u de volgende opdracht indeling:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-237">To add the IP addresses of particular computers to the list of trusted hosts, use the following command format:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <IP Address>
```

<span data-ttu-id="1e9dc-238">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-238">For example:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value 172.16.0.0
```

<span data-ttu-id="1e9dc-239">Als u een computer wilt toevoegen aan de lijst TrustedHosts van een externe computer, gebruikt u de `Connect-WSMan` cmdlet om een knoop punt voor de externe computer toe te voegen aan het WSMan:-station op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-239">To add a computer to the TrustedHosts list of a remote computer, use the `Connect-WSMan` cmdlet to add a node for the remote computer to the WSMan: drive on the local computer.</span></span> <span data-ttu-id="1e9dc-240">Gebruik vervolgens een `Set-Item` opdracht om de computer toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-240">Then use a `Set-Item` command to add the computer.</span></span>

<span data-ttu-id="1e9dc-241">`Connect-WSMan`Zie [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)voor meer informatie over de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-241">For more information about the `Connect-WSMan` cmdlet, see [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span>

## <a name="troubleshooting-computer-configuration-issues"></a><span data-ttu-id="1e9dc-242">Problemen met computer configuratie oplossen</span><span class="sxs-lookup"><span data-stu-id="1e9dc-242">Troubleshooting computer configuration issues</span></span>

<span data-ttu-id="1e9dc-243">In deze sectie worden externe problemen besproken die betrekking hebben op bepaalde configuraties van een computer, domein of onderneming.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-243">This section discusses remoting problems that are related to particular configurations of a computer, domain, or enterprise.</span></span>

### <a name="how-to-configure-remoting-on-alternate-ports"></a><span data-ttu-id="1e9dc-244">Externe toegang configureren op alternatieve poorten</span><span class="sxs-lookup"><span data-stu-id="1e9dc-244">How to configure remoting on alternate ports</span></span>

```
ERROR: The connection to the specified remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="1e9dc-245">Externe communicatie van Power shell gebruikt poort 80 voor HTTP-Trans Port.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-245">PowerShell remoting uses port 80 for HTTP transport by default.</span></span> <span data-ttu-id="1e9dc-246">De standaard poort wordt gebruikt wanneer de gebruiker niet de para meters **ConnectionURI** of **poort** opgeeft in een externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-246">The default port is used whenever the user does not specify the **ConnectionURI** or **Port** parameters in a remote command.</span></span>

<span data-ttu-id="1e9dc-247">Als u de standaard poort die Power shell gebruikt, wilt wijzigen, gebruikt u `Set-Item` cmdlet in het station WSMan: om de poort waarde in het knoop punt listener te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-247">To change the default port that PowerShell uses, use `Set-Item` cmdlet in the WSMan: drive to change the Port value in the listener leaf node.</span></span>

<span data-ttu-id="1e9dc-248">Met de volgende opdracht wordt bijvoorbeeld de standaard poort gewijzigd in 8080.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-248">For example, the following command changes the default port to 8080.</span></span>

```powershell
Set-Item wsman:\localhost\listener\listener*\port -Value 8080
```

### <a name="how-to-configure-remoting-with-a-proxy-server"></a><span data-ttu-id="1e9dc-249">Externe toegang configureren met een proxy server</span><span class="sxs-lookup"><span data-stu-id="1e9dc-249">How to configure remoting with a proxy server</span></span>

```
ERROR: The client cannot connect to the destination specified in the request.
Verify that the service on the destination is running and is accepting
requests.
```

<span data-ttu-id="1e9dc-250">Omdat externe communicatie van Power shell gebruikmaakt van het HTTP-protocol, is dit van invloed op de HTTP-proxy-instellingen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-250">Because PowerShell remoting uses the HTTP protocol, it is affected by HTTP proxy settings.</span></span> <span data-ttu-id="1e9dc-251">In ondernemingen met proxy servers hebben gebruikers geen rechtstreekse toegang tot een externe Power shell-computer.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-251">In enterprises that have proxy servers, users cannot access a PowerShell remote computer directly.</span></span>

<span data-ttu-id="1e9dc-252">U kunt dit probleem oplossen met behulp van opties voor proxy-instellingen in uw externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-252">To resolve this problem, use proxy setting options in your remote command.</span></span> <span data-ttu-id="1e9dc-253">De volgende instellingen zijn beschikbaar:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-253">The following settings are available:</span></span>

- <span data-ttu-id="1e9dc-254">ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="1e9dc-254">ProxyAccessType</span></span>
- <span data-ttu-id="1e9dc-255">ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="1e9dc-255">ProxyAuthentication</span></span>
- <span data-ttu-id="1e9dc-256">ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="1e9dc-256">ProxyCredential</span></span>

<span data-ttu-id="1e9dc-257">Als u deze opties voor een bepaalde opdracht wilt instellen, gebruikt u de volgende procedure:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-257">To set these options for a particular command, use the following procedure:</span></span>

1. <span data-ttu-id="1e9dc-258">Gebruik de para meters **ProxyAccessType** , **ProxyAuthentication** en **ProxyCredential** van de `New-PSSessionOption` cmdlet om een sessie optie object te maken met de proxy-instellingen voor uw onderneming.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-258">Use the **ProxyAccessType** , **ProxyAuthentication** , and **ProxyCredential** parameters of the `New-PSSessionOption` cmdlet to create a session option object with the proxy settings for your enterprise.</span></span> <span data-ttu-id="1e9dc-259">Sla het optie object op als variabele.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-259">Save the option object is a variable.</span></span>

1. <span data-ttu-id="1e9dc-260">Gebruik de variabele die het optie object bevat als waarde voor de para meter **SessionOption** van een `New-PSSession` , `Enter-PSSession` , of `Invoke-Command` opdracht.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-260">Use the variable that contains the option object as the value of the **SessionOption** parameter of a `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` command.</span></span>

<span data-ttu-id="1e9dc-261">Met de volgende opdracht wordt bijvoorbeeld een sessie optie object gemaakt met proxy sessie opties en wordt het object vervolgens gebruikt om een externe sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-261">For example, the following command creates a session option object with proxy session options and then uses the object to create a remote session.</span></span>

```powershell
$SessionOption = New-PSSessionOption -ProxyAccessType IEConfig `
-ProxyAuthentication Negotiate -ProxyCredential Domain01\User01

New-PSSession -ConnectionURI https://www.fabrikam.com
```

<span data-ttu-id="1e9dc-262">`New-PSSessionOption`Zie [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor meer informatie over de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-262">For more information about the `New-PSSessionOption` cmdlet, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="1e9dc-263">Als u deze opties wilt instellen voor alle externe opdrachten in de huidige sessie, gebruikt u het optie object dat `New-PSSessionOption` maakt in de waarde van de `$PSSessionOption` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-263">To set these options for all remote commands in the current session, use the option object that `New-PSSessionOption` creates in the value of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="1e9dc-264">Zie [about_Preference_Variables](about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-264">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="1e9dc-265">Als u deze opties wilt instellen voor alle externe opdrachten alle Power shell-sessies op de lokale computer, voegt `$PSSessionOption` u de voorkeurs variabele toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-265">To set these options for all remote commands all PowerShell sessions on the local computer, add the `$PSSessionOption` preference variable to your PowerShell profile.</span></span> <span data-ttu-id="1e9dc-266">Zie [about_Profiles](about_Profiles.md)voor meer informatie over Power shell-profielen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-266">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="how-to-detect-a-32-bit-session-on-a-64-bit-computer"></a><span data-ttu-id="1e9dc-267">Een 32-bits sessie op een 64-bits computer detecteren</span><span class="sxs-lookup"><span data-stu-id="1e9dc-267">How to detect a 32-bit session on a 64-bit computer</span></span>

```
ERROR: The term "<tool-Name>" is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="1e9dc-268">Als op de externe computer een 64-bits versie van Windows wordt uitgevoerd en de externe opdracht een 32-bits sessie configuratie gebruikt, zoals micro soft. PowerShell32, laadt Windows Remote Management (WinRM) een WOW64-proces en worden alle verwijzingen naar de Directory automatisch door Windows omgeleid naar `$env:Windir\System32` de `$env:Windir\SysWOW64` map.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-268">If the remote computer is running a 64-bit version of Windows, and the remote command is using a 32-bit session configuration, such as Microsoft.PowerShell32, Windows Remote Management (WinRM) loads a WOW64 process and Windows automatically redirects all references to the `$env:Windir\System32` directory to the `$env:Windir\SysWOW64` directory.</span></span>

<span data-ttu-id="1e9dc-269">Als u probeert hulpprogram ma's in de map System32 te gebruiken die geen tegen Hangers hebben in de map SysWow64, zoals `Defrag.exe` , kunnen de hulpprogram ma's niet worden gevonden in de map.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-269">As a result, if you try to use tools in the System32 directory that do not have counterparts in the SysWow64 directory, such as `Defrag.exe`, the tools cannot be found in the directory.</span></span>

<span data-ttu-id="1e9dc-270">Als u de processor architectuur wilt vinden die in de sessie wordt gebruikt, gebruikt u de waarde van de omgevings variabele **PROCESSOR_ARCHITECTURE** .</span><span class="sxs-lookup"><span data-stu-id="1e9dc-270">To find the processor architecture that is being used in the session, use the value of the **PROCESSOR_ARCHITECTURE** environment variable.</span></span> <span data-ttu-id="1e9dc-271">Met de volgende opdracht wordt de processor architectuur van de sessie in de `$s` variabele gevonden.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-271">The following command finds the processor architecture of the session in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -ConfigurationName CustomShell
Invoke-Command -Session $s {$env:PROCESSOR_ARCHITECTURE}
```

```Output
x86
```

<span data-ttu-id="1e9dc-272">Zie [about_Session_Configurations](about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-272">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

## <a name="troubleshooting-policy-and-preference-issues"></a><span data-ttu-id="1e9dc-273">Problemen met beleid en voor keuren oplossen</span><span class="sxs-lookup"><span data-stu-id="1e9dc-273">Troubleshooting policy and preference issues</span></span>

<span data-ttu-id="1e9dc-274">In deze sectie worden externe problemen besproken die betrekking hebben op beleids regels en voor keuren die zijn ingesteld op de lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-274">This section discusses remoting problems that are related to policies and preferences set on the local and remote computers.</span></span>

### <a name="how-to-change-the-execution-policy-for-import-pssession-and-import-module"></a><span data-ttu-id="1e9dc-275">Het uitvoerings beleid voor Import-PSSession en Import-Module wijzigen</span><span class="sxs-lookup"><span data-stu-id="1e9dc-275">How to change the execution policy for Import-PSSession and Import-Module</span></span>

```
ERROR: Import-Module: File <filename> cannot be loaded because the
execution of scripts is disabled on this system.
```

<span data-ttu-id="1e9dc-276">De `Import-PSSession` `Export-PSSession` cmdlets en maken modules met niet-ondertekende script bestanden en indelings bestanden.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-276">The `Import-PSSession` and `Export-PSSession` cmdlets create modules that contains unsigned script files and formatting files.</span></span>

<span data-ttu-id="1e9dc-277">Als u de modules wilt importeren die zijn gemaakt met deze cmdlets, `Import-PSSession` kunt u `Import-Module` het uitvoerings beleid in de huidige sessie niet beperken of alles ondertekend.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-277">To import the modules that are created by these cmdlets, either by using `Import-PSSession` or `Import-Module`, the execution policy in the current session cannot be Restricted or AllSigned.</span></span> <span data-ttu-id="1e9dc-278">Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie over het uitvoeren van Power shell-uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-278">For information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="1e9dc-279">Als u de modules wilt importeren zonder het uitvoerings beleid voor de lokale computer die is ingesteld in het REGI ster te wijzigen, gebruikt u de para meter **bereik** van `Set-ExecutionPolicy` om een minder beperkend uitvoerings beleid in te stellen voor één proces.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-279">To import the modules without changing the execution policy for the local computer that is set in the registry, use the **Scope** parameter of `Set-ExecutionPolicy` to set a less restrictive execution policy for a single process.</span></span>

<span data-ttu-id="1e9dc-280">Met de volgende opdracht wordt bijvoorbeeld een proces met het `RemoteSigned` uitvoerings beleid gestart.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-280">For example, the following command starts a process with the `RemoteSigned` execution policy.</span></span> <span data-ttu-id="1e9dc-281">De wijziging van het uitvoerings beleid is alleen van invloed op het huidige proces en wijzigt de Power shell **ExecutionPolicy** -register instelling niet.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-281">The execution policy change affects only the current process and does not change the PowerShell **ExecutionPolicy** registry setting.</span></span>

```powershell
Set-ExecutionPolicy -Scope process -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="1e9dc-282">U kunt ook de para meter **ExecutionPolicy** van gebruiken `PowerShell.exe` om één sessie met een minder beperkend uitvoerings beleid te starten.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-282">You can also use the **ExecutionPolicy** parameter of `PowerShell.exe` to start a single session with a less restrictive execution policy.</span></span>

```powershell
PowerShell.exe -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="1e9dc-283">Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie over uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-283">For more information about execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span> <span data-ttu-id="1e9dc-284">Typ `PowerShell.exe -?` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-284">For more information, type `PowerShell.exe -?`.</span></span>

### <a name="how-to-set-and-change-quotas"></a><span data-ttu-id="1e9dc-285">Quota's instellen en wijzigen</span><span class="sxs-lookup"><span data-stu-id="1e9dc-285">How to set and change quotas</span></span>

```
ERROR: The total data received from the remote client exceeded allowed
maximum.
```

<span data-ttu-id="1e9dc-286">U kunt quota's gebruiken om de lokale computer en de externe computer te beschermen tegen overmatig gebruik van bronnen, zowel per ongeluk als kwaad aardigheid.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-286">You can use quotas to protect the local computer and the remote computer from excessive resource use, both accidental and malicious.</span></span>

<span data-ttu-id="1e9dc-287">De volgende quota's zijn beschikbaar in de basis configuratie.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-287">The following quotas are available in the basic configuration.</span></span>

- <span data-ttu-id="1e9dc-288">De WSMan-provider (WSMan:) biedt verschillende quota-instellingen, zoals de instellingen **MaxEnvelopeSizeKB** en **MaxProviderRequests** in het `WSMan:<ComputerName>` knoop punt en de instellingen **MaxConcurrentOperations** , **MaxConcurrentOperationsPerUser** en **MaxConnections** in het `WSMan:<ComputerName>\Service` knoop punt.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-288">The WSMan provider (WSMan:) provides several quota settings, such as the **MaxEnvelopeSizeKB** and **MaxProviderRequests** settings in the `WSMan:<ComputerName>` node and the **MaxConcurrentOperations** , **MaxConcurrentOperationsPerUser** , and **MaxConnections** settings in the `WSMan:<ComputerName>\Service` node.</span></span>

- <span data-ttu-id="1e9dc-289">U kunt de lokale computer beveiligen met behulp van de **MaximumReceivedDataSizePerCommand** -en **MaximumReceivedObjectSize** -para meters van de `New-PSSessionOption` cmdlet en de `$PSSessionOption` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-289">You can protect the local computer by using the **MaximumReceivedDataSizePerCommand** and **MaximumReceivedObjectSize** parameters of the `New-PSSessionOption` cmdlet and the `$PSSessionOption` preference variable.</span></span>

- <span data-ttu-id="1e9dc-290">U kunt de externe computer beveiligen door beperkingen toe te voegen aan de sessie configuraties, zoals met behulp van de para meters **MaximumReceivedDataSizePerCommandMB** en **MaximumReceivedObjectSizeMB** van de `Register-PSSessionConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-290">You can protect the remote computer by adding restrictions to the session configurations, such as by using the **MaximumReceivedDataSizePerCommandMB** and **MaximumReceivedObjectSizeMB** parameters of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="1e9dc-291">Wanneer quota conflicteren met een opdracht, genereert Power shell een fout.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-291">When quotas conflict with a command, PowerShell generates an error.</span></span>

<span data-ttu-id="1e9dc-292">Wijzig de externe opdracht om te voldoen aan het quotum om de fout op te lossen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-292">To resolve the error, change the remote command to comply with the quota.</span></span> <span data-ttu-id="1e9dc-293">U kunt ook de bron van het quotum bepalen en vervolgens het quotum verhogen zodat de opdracht kan worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-293">Or, determine the source of the quota, and then increase the quota to allow the command to complete.</span></span>

<span data-ttu-id="1e9dc-294">Met de volgende opdracht wordt bijvoorbeeld het quotum voor de object grootte in de micro soft. Power shell-sessie configuratie op de externe computer verhoogd van 10 MB (de standaard waarde) tot 11 MB.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-294">For example, the following command increases the object size quota in the Microsoft.PowerShell session configuration on the remote computer from 10 MB (the default value) to 11 MB.</span></span>

```powershell
Set-PSSessionConfiguration -Name microsoft.PowerShell `
  -MaximumReceivedObjectSizeMB 11 -Force
```

<span data-ttu-id="1e9dc-295">Zie voor meer informatie over de `New-PSSessionOption` cmdlet `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="1e9dc-295">For more information about the `New-PSSessionOption` cmdlet, see `New-PSSessionOption`.</span></span>

<span data-ttu-id="1e9dc-296">Zie [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)voor meer informatie over de WS-Management quota's.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-296">For more information about the WS-Management quotas, see [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md).</span></span>

### <a name="how-to-resolve-timeout-errors"></a><span data-ttu-id="1e9dc-297">Time-outfouten oplossen</span><span class="sxs-lookup"><span data-stu-id="1e9dc-297">How to resolve timeout errors</span></span>

```
ERROR: The WS-Management service cannot complete the operation within
the time specified in OperationTimeout.
```

<span data-ttu-id="1e9dc-298">U kunt time-outs gebruiken om de lokale computer en de externe computer te beschermen tegen overmatig gebruik van bronnen, zowel per ongeluk als kwaad aardig.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-298">You can use timeouts to protect the local computer and the remote computer from excessive resource use, both accidental and malicious.</span></span> <span data-ttu-id="1e9dc-299">Wanneer time-outs zijn ingesteld op zowel de lokale als de externe computer, gebruikt Power shell de kortste time-outinstellingen.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-299">When timeouts are set on both the local and remote computer, PowerShell uses the shortest timeout settings.</span></span>

<span data-ttu-id="1e9dc-300">De volgende time-outs zijn beschikbaar in de basis configuratie.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-300">The following timeouts are available in the basic configuration.</span></span>

- <span data-ttu-id="1e9dc-301">De WSMan-provider (WSMan:) voorziet in verschillende time-outinstellingen aan de client zijde en aan de service zijde, zoals de instelling **MaxTimeoutms** in het `WSMan:<ComputerName>` knoop punt en de **EnumerationTimeoutms** -en **MaxPacketRetrievalTimeSeconds** -instellingen in het `WSMan:<ComputerName>\Service` knoop punt.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-301">The WSMan provider (WSMan:) provides several client-side and service-side timeout settings, such as the **MaxTimeoutms** setting in the `WSMan:<ComputerName>` node and the **EnumerationTimeoutms** and **MaxPacketRetrievalTimeSeconds** settings in the `WSMan:<ComputerName>\Service` node.</span></span>

- <span data-ttu-id="1e9dc-302">U kunt de lokale computer beveiligen door gebruik te maken van de para meters **CancelTimeout** , **IdleTimeout** , **opentime out** en **OperationTimeout** van de `New-PSSessionOption` cmdlet en de `$PSSessionOption` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-302">You can protect the local computer by using the **CancelTimeout** , **IdleTimeout** , **OpenTimeout** , and **OperationTimeout** parameters of the `New-PSSessionOption` cmdlet and the `$PSSessionOption` preference variable.</span></span>

- <span data-ttu-id="1e9dc-303">U kunt de externe computer ook beveiligen door time-outwaarden programmatisch in te stellen in de sessie configuratie voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-303">You can also protect the remote computer by setting timeout values programmatically in the session configuration for the session.</span></span>

<span data-ttu-id="1e9dc-304">Als een time-outwaarde een bewerking niet kan worden voltooid, wordt de bewerking door Power Shell beëindigd en wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-304">When a timeout value does not permit a operation to complete, PowerShell terminates the operation and generates an error.</span></span>

<span data-ttu-id="1e9dc-305">Om de fout op te lossen, wijzigt u de opdracht in volt ooien binnen de time-outinterval of bepaalt u de bron van de time-outlimiet en verhoogt u de time-outinterval zodat de opdracht kan worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-305">To resolve the error, change the command to complete within the timeout interval or determine the source of the timeout limit and increase the timeout interval to allow the command to complete.</span></span>

<span data-ttu-id="1e9dc-306">De volgende opdrachten gebruiken bijvoorbeeld de `New-PSSessionOption` cmdlet om een sessie optie object te maken met een **OperationTimeout** -waarde van 4 minuten (in MS) en vervolgens het object Session Option gebruiken om een externe sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-306">For example, the following commands use the `New-PSSessionOption` cmdlet to create a session option object with an **OperationTimeout** value of 4 minutes (in MS) and then use the session option object to create a remote session.</span></span>

```powershell
$pso = New-PSSessionoption -OperationTimeout 240000

New-PSSession -ComputerName Server01 -sessionOption $pso
```

<span data-ttu-id="1e9dc-307">Zie het Help-onderwerp voor de WSMan-provider (type) voor meer informatie over de WS-Management-time-outs `Get-Help WSMan` .</span><span class="sxs-lookup"><span data-stu-id="1e9dc-307">For more information about the WS-Management timeouts, see the Help topic for the WSMan provider (type `Get-Help WSMan`).</span></span>

<span data-ttu-id="1e9dc-308">`New-PSSessionOption`Zie [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor meer informatie over de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-308">For more information about the `New-PSSessionOption` cmdlet, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

## <a name="troubleshooting-unresponsive-behavior"></a><span data-ttu-id="1e9dc-309">Oplossen van problemen met niet-reagerende gedrag</span><span class="sxs-lookup"><span data-stu-id="1e9dc-309">Troubleshooting unresponsive behavior</span></span>

<span data-ttu-id="1e9dc-310">In deze sectie worden externe problemen beschreven die voor komen dat een opdracht wordt voltooid en de retour nering van de Power shell-prompt wordt voor komen of vertraagd.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-310">This section discusses remoting problems that prevent a command from completing and prevent or delay the return of the PowerShell prompt.</span></span>

### <a name="how-to-interrupt-a-command"></a><span data-ttu-id="1e9dc-311">Een opdracht onderbreken</span><span class="sxs-lookup"><span data-stu-id="1e9dc-311">How to interrupt a command</span></span>

<span data-ttu-id="1e9dc-312">Sommige systeem eigen Windows-Program ma's, zoals Program ma's met een gebruikers interface, console toepassingen die invoer vragen en console toepassingen die gebruikmaken van de Win32-console-API, werken niet goed in de externe Power shell-host.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-312">Some native Windows programs, such as programs with a user interface, console applications that prompt for input, and console applications that use the Win32 console API, do not work correctly in the PowerShell remote host.</span></span>

<span data-ttu-id="1e9dc-313">Wanneer u deze Program ma's gebruikt, ziet u mogelijk onverwacht gedrag, zoals geen uitvoer, gedeeltelijke uitvoer of een externe opdracht die niet is voltooid.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-313">When you use these programs, you might see unexpected behavior, such as no output, partial output, or a remote command that does not complete.</span></span>

<span data-ttu-id="1e9dc-314">Als u een programma wilt beëindigen dat niet meer reageert, typt u <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-314">To end an unresponsive program, type <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="1e9dc-315">Als u fouten wilt weer geven die mogelijk zijn gerapporteerd, typt u `$error` de lokale host en de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-315">To view any errors that might have been reported, type `$error` in the local host and the remote session.</span></span>

## <a name="how-to-recover-from-an-operation-failure"></a><span data-ttu-id="1e9dc-316">Herstellen na een mislukte bewerking</span><span class="sxs-lookup"><span data-stu-id="1e9dc-316">How to recover from an operation failure</span></span>

```
ERROR: The I/O operation has been aborted because of either a thread exit
or an  application request.
```

<span data-ttu-id="1e9dc-317">Deze fout wordt geretourneerd wanneer een bewerking wordt beëindigd voordat deze is voltooid.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-317">This error is returned when an operation is terminated before it completes.</span></span>
<span data-ttu-id="1e9dc-318">Normaal gesp roken treedt er een fout op wanneer de WinRM-service wordt gestopt of opnieuw wordt gestart terwijl andere WinRM-bewerkingen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-318">Typically, it occurs when the WinRM service stops or restarts while other WinRM operations are in progress.</span></span>

<span data-ttu-id="1e9dc-319">Om dit probleem op te lossen, controleert u of de WinRM-service wordt uitgevoerd en voert u de opdracht opnieuw uit.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-319">To resolve this issue, verify that the WinRM service is running and try the command again.</span></span>

1. <span data-ttu-id="1e9dc-320">Start Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="1e9dc-320">Start PowerShell with the **Run as administrator** option.</span></span>
1. <span data-ttu-id="1e9dc-321">Voer de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="1e9dc-321">Run the following command:</span></span>

   `Start-Service WinRM`

1. <span data-ttu-id="1e9dc-322">Voer de opdracht die de fout heeft gegenereerd opnieuw uit.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-322">Re-run the command that generated the error.</span></span>

## <a name="linux-and-macos-limitations"></a><span data-ttu-id="1e9dc-323">Beperkingen voor Linux en macOS</span><span class="sxs-lookup"><span data-stu-id="1e9dc-323">Linux and macOS limitations</span></span>

### <a name="authentication"></a><span data-ttu-id="1e9dc-324">Verificatie</span><span class="sxs-lookup"><span data-stu-id="1e9dc-324">Authentication</span></span>

<span data-ttu-id="1e9dc-325">Alleen basis verificatie werkt in macOS en poging tot het gebruik van andere verificatie schema's kan leiden tot een storing in het proces.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-325">Only basic authentication works on macOS and attempting to use other authentication schemes may result in the process crashing.</span></span>

<span data-ttu-id="1e9dc-326">Raadpleeg de [Omi-verificatie](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) -instructies.</span><span class="sxs-lookup"><span data-stu-id="1e9dc-326">Please see the [OMI authentication](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) instructions.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e9dc-327">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="1e9dc-327">SEE ALSO</span></span>

[<span data-ttu-id="1e9dc-328">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="1e9dc-328">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

[<span data-ttu-id="1e9dc-329">Exporteren-PSSession</span><span class="sxs-lookup"><span data-stu-id="1e9dc-329">Export-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Export-PSSession)

[<span data-ttu-id="1e9dc-330">Import-module</span><span class="sxs-lookup"><span data-stu-id="1e9dc-330">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

[<span data-ttu-id="1e9dc-331">about_Remote</span><span class="sxs-lookup"><span data-stu-id="1e9dc-331">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="1e9dc-332">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="1e9dc-332">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="1e9dc-333">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="1e9dc-333">about_Remote_Variables</span></span>](about_Remote_Variables.md)
