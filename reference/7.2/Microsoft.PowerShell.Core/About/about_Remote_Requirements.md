---
description: Hierin worden de systeem vereisten en configuratie vereisten beschreven voor het uitvoeren van externe opdrachten in Power shell.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Requirements
ms.openlocfilehash: 4a994ded51195e5932af7bb4af0b2e6fb3a67857
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705301"
---
# <a name="about-remote-requirements"></a><span data-ttu-id="0a580-103">Over externe vereisten</span><span class="sxs-lookup"><span data-stu-id="0a580-103">About Remote Requirements</span></span>

## <a name="short-description"></a><span data-ttu-id="0a580-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0a580-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="0a580-105">Hierin worden de systeem vereisten en configuratie vereisten beschreven voor het uitvoeren van externe opdrachten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="0a580-105">Describes the system requirements and configuration requirements for running remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="0a580-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0a580-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="0a580-107">In dit onderwerp worden de systeem vereisten, de gebruikers vereisten en de resource vereisten beschreven voor het tot stand brengen van externe verbindingen en het uitvoeren van externe opdrachten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="0a580-107">This topic describes the system requirements, user requirements, and resource requirements for establishing remote connections and running remote commands in PowerShell.</span></span> <span data-ttu-id="0a580-108">Het bevat ook instructies voor het configureren van externe bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="0a580-108">It also provides instructions for configuring remote operations.</span></span>

<span data-ttu-id="0a580-109">Opmerking: veel cmdlets (inclusief de cmdlets Get-service, Get-process, Get-WMIObject, Get-EventLog en Get-WinEvent) krijgen objecten van externe computers met behulp van Microsoft .NET Framework-methoden om de objecten op te halen.</span><span class="sxs-lookup"><span data-stu-id="0a580-109">Note: Many cmdlets (including the Get-Service, Get-Process, Get-WMIObject, Get-EventLog, and Get-WinEvent cmdlets) get objects from remote computers by using Microsoft .NET Framework methods to retrieve the objects.</span></span> <span data-ttu-id="0a580-110">Ze maken geen gebruik van de infra structuur voor externe communicatie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="0a580-110">They do not use the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="0a580-111">De vereisten in dit document zijn niet van toepassing op deze cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0a580-111">The requirements in this document do not apply to these cmdlets.</span></span>

<span data-ttu-id="0a580-112">Lees de beschrijving van de para meter ComputerName van de cmdlets om de cmdlets te vinden die de para meter ComputerName hebben maar geen externe communicatie van Power shell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0a580-112">To find the cmdlets that have a ComputerName parameter but do not use PowerShell remoting, read the description of the ComputerName parameter of the cmdlets.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="0a580-113">SYSTEEM VEREISTEN</span><span class="sxs-lookup"><span data-stu-id="0a580-113">SYSTEM REQUIREMENTS</span></span>

<span data-ttu-id="0a580-114">Als u externe sessies wilt uitvoeren op Windows Power Shell 3,0, moeten de lokale en externe computers het volgende hebben:</span><span class="sxs-lookup"><span data-stu-id="0a580-114">To run remote sessions on Windows PowerShell 3.0, the local and remote computers must have the following:</span></span>

- <span data-ttu-id="0a580-115">Windows Power Shell 3,0 of hoger</span><span class="sxs-lookup"><span data-stu-id="0a580-115">Windows PowerShell 3.0 or later</span></span>
- <span data-ttu-id="0a580-116">Het Microsoft .NET Framework 4 of hoger</span><span class="sxs-lookup"><span data-stu-id="0a580-116">The Microsoft .NET Framework 4 or later</span></span>
- <span data-ttu-id="0a580-117">Windows Remote Management 3,0</span><span class="sxs-lookup"><span data-stu-id="0a580-117">Windows Remote Management 3.0</span></span>

<span data-ttu-id="0a580-118">Als u externe sessies wilt uitvoeren op Windows Power Shell 2,0, moeten de lokale en externe computers het volgende hebben:</span><span class="sxs-lookup"><span data-stu-id="0a580-118">To run remote sessions on Windows PowerShell 2.0, the local and remote computers must have the following:</span></span>

- <span data-ttu-id="0a580-119">Windows Power Shell 2,0 of hoger</span><span class="sxs-lookup"><span data-stu-id="0a580-119">Windows PowerShell 2.0 or later</span></span>
- <span data-ttu-id="0a580-120">Het Microsoft .NET Framework 2,0 of hoger</span><span class="sxs-lookup"><span data-stu-id="0a580-120">The Microsoft .NET Framework 2.0 or later</span></span>
- <span data-ttu-id="0a580-121">Windows Remote Management 2,0</span><span class="sxs-lookup"><span data-stu-id="0a580-121">Windows Remote Management 2.0</span></span>

<span data-ttu-id="0a580-122">U kunt externe sessies maken tussen computers met Windows Power Shell 2,0 en Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0a580-122">You can create remote sessions between computers running Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span> <span data-ttu-id="0a580-123">Functies die alleen worden uitgevoerd op Windows Power Shell 3,0, zoals de mogelijkheid om de verbinding met sessies te verbreken en opnieuw te verbinden, zijn alleen beschikbaar als op beide computers Windows Power Shell 3,0 wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0a580-123">However, features that run only on Windows PowerShell 3.0, such as the ability to disconnect and reconnect to sessions, are available only when both computers are running Windows PowerShell 3.0.</span></span>

<span data-ttu-id="0a580-124">Als u het versie nummer van een geïnstalleerde versie van Power shell wilt weten, gebruikt u de $PSVersionTable automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="0a580-124">To find the version number of an installed version of PowerShell, use the $PSVersionTable automatic variable.</span></span>

<span data-ttu-id="0a580-125">Windows Remote Management (WinRM) 3,0 en Microsoft .NET Framework 4 zijn opgenomen in Windows 8, Windows Server 2012 en nieuwere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="0a580-125">Windows Remote Management (WinRM) 3.0 and Microsoft .NET Framework 4 are included in Windows 8, Windows Server 2012, and newer releases of the Windows operating system.</span></span> <span data-ttu-id="0a580-126">WinRM 3,0 is opgenomen in Windows Management Framework 3,0 voor oudere besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="0a580-126">WinRM 3.0 is included in Windows Management Framework 3.0 for older operating systems.</span></span> <span data-ttu-id="0a580-127">Als de computer niet beschikt over de vereiste versie van WinRM of het Microsoft .NET Framework, mislukt de installatie.</span><span class="sxs-lookup"><span data-stu-id="0a580-127">If the computer does not have the required version of WinRM or the Microsoft .NET Framework, the installation fails.</span></span>

## <a name="user-permissions"></a><span data-ttu-id="0a580-128">GEBRUIKERSMACHTIGINGEN</span><span class="sxs-lookup"><span data-stu-id="0a580-128">USER PERMISSIONS</span></span>

<span data-ttu-id="0a580-129">Om externe sessies te maken en externe opdrachten uit te voeren, moet de huidige gebruiker lid zijn van de groep Administrators op de externe computer of moeten de referenties van een beheerder worden verstrekt.</span><span class="sxs-lookup"><span data-stu-id="0a580-129">To create remote sessions and run remote commands, by default, the current user must be a member of the Administrators group on the remote computer or provide the credentials of an administrator.</span></span> <span data-ttu-id="0a580-130">Anders mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="0a580-130">Otherwise, the command fails.</span></span>

<span data-ttu-id="0a580-131">De vereiste machtigingen voor het maken van sessies en het uitvoeren van opdrachten op een externe computer (of in een externe sessie op de lokale computer) worden vastgesteld door de sessie configuratie (ook wel ' eind punt ' genoemd) op de externe computer waarmee de sessie verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="0a580-131">The permissions required to create sessions and run commands on a remote computer (or in a remote session on the local computer) are established by the session configuration (also known as an "endpoint") on the remote computer to which the session connects.</span></span> <span data-ttu-id="0a580-132">Met name de security descriptor in de sessie configuratie bepaalt wie toegang heeft tot de sessie configuratie en wie deze kan gebruiken om verbinding te maken.</span><span class="sxs-lookup"><span data-stu-id="0a580-132">Specifically, the security descriptor on the session configuration determines who has access to the session configuration and who can use it to connect.</span></span>

<span data-ttu-id="0a580-133">De security descriptors voor de standaard sessie configuraties, micro soft. Power shell, micro soft. PowerShell32 en micro soft. Power shell. workflow, geven alleen toegang tot leden van de groep Administrators.</span><span class="sxs-lookup"><span data-stu-id="0a580-133">The security descriptors on the default session configurations, Microsoft.PowerShell, Microsoft.PowerShell32, and Microsoft.PowerShell.Workflow, allow access only to members of the Administrators group.</span></span>

<span data-ttu-id="0a580-134">Als de huidige gebruiker geen machtiging heeft voor het gebruik van de sessie configuratie, de opdracht voor het uitvoeren van een opdracht (die gebruikmaakt van een tijdelijke sessie) of het maken van een permanente sessie op de externe computer mislukt.</span><span class="sxs-lookup"><span data-stu-id="0a580-134">If the current user doesn't have permission to use the session configuration, the command to run a command (which uses a temporary session) or create a persistent session on the remote computer fails.</span></span> <span data-ttu-id="0a580-135">De gebruiker kan de para meter configuratiepad van cmdlets gebruiken waarmee sessies worden gemaakt voor het selecteren van een andere sessie configuratie, als er een beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="0a580-135">The user can use the ConfigurationName parameter of cmdlets that create sessions to select a different session configuration, if one is available.</span></span>

<span data-ttu-id="0a580-136">Leden van de groep Administrators op een computer kunnen bepalen wie toestemming heeft om op afstand verbinding te maken met de computer door de security descriptors te wijzigen op de standaard sessie configuraties en door nieuwe sessie configuraties te maken met verschillende security descriptors.</span><span class="sxs-lookup"><span data-stu-id="0a580-136">Members of the Administrators group on a computer can determine who has permission to connect to the computer remotely by changing the security descriptors on the default session configurations and by creating new session configurations with different security descriptors.</span></span>

<span data-ttu-id="0a580-137">Zie [about_Session_Configurations](about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="0a580-137">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

## <a name="windows-network-locations"></a><span data-ttu-id="0a580-138">WINDOWS-NETWERK LOCATIES</span><span class="sxs-lookup"><span data-stu-id="0a580-138">WINDOWS NETWORK LOCATIONS</span></span>

<span data-ttu-id="0a580-139">Met ingang van Windows Power Shell 3,0 kan de cmdlet Enable-PSRemoting externe communicatie mogelijk maken op client-en server versies van Windows op particuliere, domein-en open bare netwerken.</span><span class="sxs-lookup"><span data-stu-id="0a580-139">Beginning in Windows PowerShell 3.0, the Enable-PSRemoting cmdlet can enable remoting on client and server versions of Windows on private, domain, and public networks.</span></span>

<span data-ttu-id="0a580-140">Op Server versies van Windows met particuliere en domein netwerken maakt de Enable-PSRemoting-cmdlet firewall regels die onbeperkte externe toegang toestaan.</span><span class="sxs-lookup"><span data-stu-id="0a580-140">On server versions of Windows with private and domain networks, the Enable-PSRemoting cmdlet creates firewall rules that allow unrestricted remote access.</span></span> <span data-ttu-id="0a580-141">Er wordt ook een firewall regel gemaakt voor open bare netwerken die alleen externe toegang vanaf computers in hetzelfde lokale subnet toestaan.</span><span class="sxs-lookup"><span data-stu-id="0a580-141">It also creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="0a580-142">Deze regel voor het lokale subnet firewall is standaard ingeschakeld op Server versies van Windows op open bare netwerken, maar Enable-PSRemoting past de regel opnieuw toe als deze is gewijzigd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0a580-142">This local subnet firewall rule is enabled by default on server versions of Windows on public networks, but Enable-PSRemoting reapplies the rule in case it was changed or deleted.</span></span>

<span data-ttu-id="0a580-143">Op client versies van Windows met particuliere en domein netwerken maakt de Enable-PSRemoting-cmdlet standaard firewall regels waarmee onbeperkte externe toegang is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="0a580-143">On client versions of Windows with private and domain networks, by default, the Enable-PSRemoting cmdlet creates firewall rules that allow unrestricted remote access.</span></span>

<span data-ttu-id="0a580-144">Als u externe toegang wilt inschakelen op client versies van Windows met open bare netwerken, gebruikt u de para meter SkipNetworkProfileCheck van de cmdlet Enable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="0a580-144">To enable remoting on client versions of Windows with public networks, use the SkipNetworkProfileCheck parameter of the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="0a580-145">Er wordt een firewall regel gemaakt die alleen externe toegang toestaat vanaf computers in hetzelfde lokale subnet.</span><span class="sxs-lookup"><span data-stu-id="0a580-145">It creates a firewall rule that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="0a580-146">Als u de lokale subnet-beperking voor open bare netwerken wilt verwijderen en externe toegang vanaf alle locaties op client-en server versies van Windows wilt toestaan, gebruikt u de Set-NetFirewallRule cmdlet in de module netsecurity.</span><span class="sxs-lookup"><span data-stu-id="0a580-146">To remove the local subnet restriction on public networks and allow remote access from all locations on client and server versions of Windows, use the Set-NetFirewallRule cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="0a580-147">Voer de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="0a580-147">Run the following command:</span></span>

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

<span data-ttu-id="0a580-148">In Windows Power Shell 2,0, op Server versies van Windows, maakt Enable-PSRemoting firewall regels die externe toegang op alle netwerken toestaan.</span><span class="sxs-lookup"><span data-stu-id="0a580-148">In Windows PowerShell 2.0, on server versions of Windows, Enable-PSRemoting creates firewall rules that permit remote access on all networks.</span></span>

<span data-ttu-id="0a580-149">In Windows Power Shell 2,0, op client versies van Windows, maakt Enable-PSRemoting firewall regels alleen op particuliere en domein netwerken.</span><span class="sxs-lookup"><span data-stu-id="0a580-149">In Windows PowerShell 2.0, on client versions of Windows, Enable-PSRemoting creates firewall rules only on private and domain networks.</span></span> <span data-ttu-id="0a580-150">Als de netwerk locatie openbaar is, mislukt Enable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="0a580-150">If the network location is public, Enable-PSRemoting fails.</span></span>

## <a name="run-as-administrator"></a><span data-ttu-id="0a580-151">ALS ADMINISTRATOR UITVOEREN</span><span class="sxs-lookup"><span data-stu-id="0a580-151">RUN AS ADMINISTRATOR</span></span>

<span data-ttu-id="0a580-152">Beheerders bevoegdheden zijn vereist voor de volgende externe bewerkingen:</span><span class="sxs-lookup"><span data-stu-id="0a580-152">Administrator privileges are required for the following remoting operations:</span></span>

- <span data-ttu-id="0a580-153">Een externe verbinding met de lokale computer tot stand brengen.</span><span class="sxs-lookup"><span data-stu-id="0a580-153">Establishing a remote connection to the local computer.</span></span> <span data-ttu-id="0a580-154">Dit wordt meestal een ' loop back-scenario ' genoemd.</span><span class="sxs-lookup"><span data-stu-id="0a580-154">This is commonly known as a "loopback" scenario.</span></span>

- <span data-ttu-id="0a580-155">De sessie configuraties op de lokale computer beheren.</span><span class="sxs-lookup"><span data-stu-id="0a580-155">Managing session configurations on the local computer.</span></span>

- <span data-ttu-id="0a580-156">WS-Management instellingen op de lokale computer weer geven en wijzigen.</span><span class="sxs-lookup"><span data-stu-id="0a580-156">Viewing and changing WS-Management settings on the local computer.</span></span> <span data-ttu-id="0a580-157">Dit zijn de instellingen in het LocalHost-knoop punt van het WSMAN:-station.</span><span class="sxs-lookup"><span data-stu-id="0a580-157">These are the settings in the LocalHost node of the WSMAN: drive.</span></span>

<span data-ttu-id="0a580-158">Als u deze taken wilt uitvoeren, moet u Power shell starten met de optie als administrator uitvoeren, zelfs als u lid bent van de groep Administrators op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="0a580-158">To perform these tasks, you must start PowerShell with the "Run as administrator" option even if you are a member of the Administrators group on the local computer.</span></span>

<span data-ttu-id="0a580-159">In Windows 7 en in Windows Server 2008 R2 start u Windows Power shell met de optie als administrator uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="0a580-159">In Windows 7 and in Windows Server 2008 R2, to start Windows PowerShell with the "Run as administrator" option:</span></span>

1. <span data-ttu-id="0a580-160">Klik op Start, klik op alle Program Ma's, klik op accessoires en klik vervolgens op de map Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="0a580-160">Click Start, click All Programs, click Accessories, and then click the Windows PowerShell folder.</span></span>
2. <span data-ttu-id="0a580-161">Klik met de rechter muisknop op Windows Power shell en klik vervolgens op als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0a580-161">Right-click Windows PowerShell, and then click "Run as administrator".</span></span>

<span data-ttu-id="0a580-162">Windows Power shell starten met de optie als administrator uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="0a580-162">To start Windows PowerShell with the "Run as administrator" option:</span></span>

1. <span data-ttu-id="0a580-163">Klik op Start, klik op alle Program Ma's en klik vervolgens op de map Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="0a580-163">Click Start, click All Programs, and then click the Windows PowerShell folder.</span></span>
2. <span data-ttu-id="0a580-164">Klik met de rechter muisknop op Windows Power shell en klik vervolgens op als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0a580-164">Right-click Windows PowerShell, and then click "Run as administrator".</span></span>

<span data-ttu-id="0a580-165">De optie als administrator uitvoeren is ook beschikbaar in andere Windows Verkenner-vermeldingen voor Windows Power shell, inclusief snelkoppelingen.</span><span class="sxs-lookup"><span data-stu-id="0a580-165">The "Run as administrator" option is also available in other Windows Explorer entries for Windows PowerShell, including shortcuts.</span></span> <span data-ttu-id="0a580-166">Klik met de rechter muisknop op het item en klik vervolgens op als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0a580-166">Just right-click the item, and then click "Run as administrator".</span></span>

<span data-ttu-id="0a580-167">Wanneer u Windows Power shell start vanuit een ander programma, zoals Cmd.exe, gebruikt u de optie als administrator uitvoeren om het programma te starten.</span><span class="sxs-lookup"><span data-stu-id="0a580-167">When you start Windows PowerShell from another program such as Cmd.exe, use the "Run as administrator" option to start the program.</span></span>

## <a name="how-to-configure-your-computer-for-remoting"></a><span data-ttu-id="0a580-168">UW COMPUTER CONFIGUREREN VOOR EXTERNE COMMUNICATIE</span><span class="sxs-lookup"><span data-stu-id="0a580-168">HOW TO CONFIGURE YOUR COMPUTER FOR REMOTING</span></span>

<span data-ttu-id="0a580-169">Computers met alle ondersteunde versies van Windows kunnen externe verbindingen tot stand brengen met en externe opdrachten uitvoeren in Power shell zonder enige configuratie.</span><span class="sxs-lookup"><span data-stu-id="0a580-169">Computers running all supported versions of Windows can establish remote connections to and run remote commands in PowerShell without any configuration.</span></span> <span data-ttu-id="0a580-170">Als u echter verbindingen wilt ontvangen en gebruikers wilt toestaan lokale en externe door de gebruiker beheerde Power shell-sessies ("PSSessions") te maken en opdrachten op de lokale computer uit te voeren, moet u externe communicatie van Power shell op de computer inschakelen.</span><span class="sxs-lookup"><span data-stu-id="0a580-170">However, to receive connections, and allow users to create local and remote user-managed PowerShell sessions ("PSSessions") and run commands on the local computer, you must enable PowerShell remoting on the computer.</span></span>

<span data-ttu-id="0a580-171">Windows Server 2012 en nieuwere versies van Windows Server zijn standaard ingeschakeld voor externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="0a580-171">Windows Server 2012 and newer releases of Windows Server are enabled for PowerShell remoting by default.</span></span> <span data-ttu-id="0a580-172">Als de instellingen zijn gewijzigd, kunt u de standaard instellingen herstellen door de cmdlet Enable-PSRemoting uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0a580-172">If the settings are changed, you can restore the default settings by running the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="0a580-173">In alle andere ondersteunde versies van Windows moet u de Enable-PSRemoting-cmdlet uitvoeren om externe communicatie van Power shell in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="0a580-173">On all other supported versions of Windows, you need to run the Enable-PSRemoting cmdlet to enable PowerShell remoting.</span></span>

<span data-ttu-id="0a580-174">De externe functies van Power shell worden ondersteund door de WinRM-service. Dit is de micro soft-implementatie van het protocol Web Services for Management (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="0a580-174">The remoting features of PowerShell are supported by the WinRM service, which is the Microsoft implementation of the Web Services for Management (WS-Management) protocol.</span></span> <span data-ttu-id="0a580-175">Wanneer u externe communicatie van Power shell inschakelt, wijzigt u de standaard configuratie van WS-Management en voegt u systeem configuratie toe waarmee gebruikers verbinding kunnen maken met WS-Management.</span><span class="sxs-lookup"><span data-stu-id="0a580-175">When you enable PowerShell remoting, you change the default configuration of WS-Management and add system configuration that allow users to connect to WS-Management.</span></span>

<span data-ttu-id="0a580-176">Power shell configureren voor het ontvangen van externe opdrachten:</span><span class="sxs-lookup"><span data-stu-id="0a580-176">To configure PowerShell to receive remote commands:</span></span>

1. <span data-ttu-id="0a580-177">Start Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0a580-177">Start PowerShell with the "Run as administrator" option.</span></span>
2. <span data-ttu-id="0a580-178">Typ bij de opdrachtprompt: `Enable-PSRemoting`</span><span class="sxs-lookup"><span data-stu-id="0a580-178">At the command prompt, type: `Enable-PSRemoting`</span></span>

<span data-ttu-id="0a580-179">Als u wilt controleren of externe toegang juist is geconfigureerd, voert u een test opdracht uit, zoals de volgende opdracht, waarmee een externe sessie op de lokale computer wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="0a580-179">To verify that remoting is configured correctly, run a test command such as the following command, which creates a remote session on the local computer.</span></span>

```powershell
New-PSSession
```

<span data-ttu-id="0a580-180">Als externe toegang op de juiste wijze is geconfigureerd, wordt door de opdracht een sessie op de lokale computer gemaakt en wordt een object geretourneerd dat de sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="0a580-180">If remoting is configured correctly, the command will create a session on the local computer and return an object that represents the session.</span></span> <span data-ttu-id="0a580-181">De uitvoer moet er ongeveer uitzien als in de volgende voorbeeld uitvoer:</span><span class="sxs-lookup"><span data-stu-id="0a580-181">The output should resemble the following sample output:</span></span>

```output
Id Name        ComputerName    State    ConfigurationName
-- ----        ------------    -----    -----
1  Session1    localhost       Opened   Microsoft.PowerShell
```

<span data-ttu-id="0a580-182">Als de opdracht mislukt, raadpleegt u [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md)voor hulp.</span><span class="sxs-lookup"><span data-stu-id="0a580-182">If the command fails, for assistance, see [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md).</span></span>

## <a name="understand-policies"></a><span data-ttu-id="0a580-183">BELEID BEGRIJPEN</span><span class="sxs-lookup"><span data-stu-id="0a580-183">UNDERSTAND POLICIES</span></span>

<span data-ttu-id="0a580-184">Wanneer u op afstand werkt, gebruikt u twee instanties van Power shell, een op de lokale computer en een op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="0a580-184">When you work remotely, you use two instances of PowerShell, one on the local computer and one on the remote computer.</span></span> <span data-ttu-id="0a580-185">Als gevolg hiervan wordt uw werk beïnvloed door het Windows-beleid en de Power shell-beleids regels op de lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="0a580-185">As a result, your work is affected by the Windows policies and the PowerShell policies on the local and remote computers.</span></span>

<span data-ttu-id="0a580-186">In het algemeen is het beleid op de lokale computer van kracht voordat u verbinding maakt en wanneer u de verbinding tot stand brengt.</span><span class="sxs-lookup"><span data-stu-id="0a580-186">In general, before you connect and as you are establishing the connection, the policies on the local computer are in effect.</span></span> <span data-ttu-id="0a580-187">Wanneer u de verbinding gebruikt, zijn de beleids regels op de externe computer van kracht.</span><span class="sxs-lookup"><span data-stu-id="0a580-187">When you are using the connection, the policies on the remote computer are in effect.</span></span>

## <a name="basic-authentication-limitations-on-linux-and-macos"></a><span data-ttu-id="0a580-188">Elementaire verificatie beperkingen voor Linux en macOS</span><span class="sxs-lookup"><span data-stu-id="0a580-188">Basic Authentication Limitations on Linux and macOS</span></span>

<span data-ttu-id="0a580-189">Wanneer u verbinding maakt vanaf een Linux-of macOS-systeem naar Windows, wordt basis verificatie via HTTP niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0a580-189">When connecting from a Linux or macOS system to Windows, Basic Authentication over HTTP is not supported.</span></span> <span data-ttu-id="0a580-190">Basis verificatie kan worden gebruikt via HTTPS door een certificaat te installeren op de doel server.</span><span class="sxs-lookup"><span data-stu-id="0a580-190">Basic Authentication can be used over HTTPS by installing a certificate on the target server.</span></span> <span data-ttu-id="0a580-191">Het certificaat moet een CN-naam hebben die overeenkomt met de hostnaam, is niet verlopen of ingetrokken.</span><span class="sxs-lookup"><span data-stu-id="0a580-191">The certificate must have a CN name that matches the hostname, is not expired or revoked.</span></span> <span data-ttu-id="0a580-192">Een zelfondertekend certificaat kan worden gebruikt voor test doeleinden.</span><span class="sxs-lookup"><span data-stu-id="0a580-192">A self-signed certificate may be used for testing purposes.</span></span>

<span data-ttu-id="0a580-193">Zie [procedure: WINRM voor HTTPS configureren](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0a580-193">See [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) for additional details.</span></span>

<span data-ttu-id="0a580-194">De volgende opdracht wordt uitgevoerd vanaf een opdracht prompt met verhoogde bevoegdheid en configureert de HTTPS-listener in Windows met het geïnstalleerde certificaat.</span><span class="sxs-lookup"><span data-stu-id="0a580-194">The following command, run from an elevated command prompt, will configure the HTTPS listener on Windows with the installed certificate.</span></span>

```powershell
$hostinfo = '@{Hostname="<DNS_NAME>"; CertificateThumbprint="<THUMBPRINT>"}'
winrm create winrm/config/Listener?Address=*+Transport=HTTPS $hostinfo
```

<span data-ttu-id="0a580-195">Selecteer op de Linux-of macOS-zijde Basic voor verificatie en-UseSSl.</span><span class="sxs-lookup"><span data-stu-id="0a580-195">On the Linux or macOS side, select Basic for authentication and -UseSSl.</span></span>

> <span data-ttu-id="0a580-196">Opmerking: basis verificatie kan niet worden gebruikt met domein accounts. Er is een lokaal account vereist en het account moet zich in de groep Administrators bevindt.</span><span class="sxs-lookup"><span data-stu-id="0a580-196">NOTE: Basic authentication cannot be used with domain accounts; a local account is required and the account must be in the Administrators group.</span></span>

```powershell
# The specified local user must have administrator rights on the target machine.
# Specify the unqualified username.
$cred = Get-Credential username
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Basic -UseSSL
```

<span data-ttu-id="0a580-197">Een alternatief voor basis verificatie via HTTPS is onderhandeld.</span><span class="sxs-lookup"><span data-stu-id="0a580-197">An alternative to Basic Authentication over HTTPS is Negotiate.</span></span> <span data-ttu-id="0a580-198">Dit resulteert in NTLM-verificatie tussen de client en de server en de payload wordt versleuteld via HTTP.</span><span class="sxs-lookup"><span data-stu-id="0a580-198">This results in NTLM authentication between the client and server and payload is encrypted over HTTP.</span></span>

<span data-ttu-id="0a580-199">Het volgende illustreert het gebruik van onderhandelen met New-PSSession:</span><span class="sxs-lookup"><span data-stu-id="0a580-199">The following illustrates using Negotiate with New-PSSession:</span></span>

```powershell
# The specified user must have administrator rights on the target machine.
$cred = Get-Credential username@hostname
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Negotiate
```

> [!NOTE]
> <span data-ttu-id="0a580-200">Voor Windows Server is een extra register instelling vereist om beheerders, behalve de ingebouwde Administrator, in te scha kelen om verbinding te maken met behulp van NTLM.</span><span class="sxs-lookup"><span data-stu-id="0a580-200">Windows Server requires an additional registry setting to enable administrators, other than the built in administrator, to connect using NTLM.</span></span>
> <span data-ttu-id="0a580-201">Raadpleeg de register instelling LocalAccountTokenFilterPolicy onder Negotiate-verificatie in [authenticatie voor externe verbindingen](/windows/win32/winrm/authentication-for-remote-connections)</span><span class="sxs-lookup"><span data-stu-id="0a580-201">Refer to the LocalAccountTokenFilterPolicy registry setting under Negotiate Authentication in [Authentication for Remote Connections](/windows/win32/winrm/authentication-for-remote-connections)</span></span>

## <a name="see-also"></a><span data-ttu-id="0a580-202">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="0a580-202">SEE ALSO</span></span>

[<span data-ttu-id="0a580-203">about_Remote</span><span class="sxs-lookup"><span data-stu-id="0a580-203">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="0a580-204">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="0a580-204">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="0a580-205">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="0a580-205">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="0a580-206">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="0a580-206">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="0a580-207">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="0a580-207">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="0a580-208">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="0a580-208">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

