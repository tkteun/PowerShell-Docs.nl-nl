---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 82db14f6819a003f4f51a35844a9fcce7a146f03
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251376"
---
# <span data-ttu-id="fe837-103">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="fe837-103">Disable-PSRemoting</span></span>

## <span data-ttu-id="fe837-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fe837-104">SYNOPSIS</span></span>
<span data-ttu-id="fe837-105">Hiermee voor komt u dat Power shell-eind punten externe verbindingen ontvangen.</span><span class="sxs-lookup"><span data-stu-id="fe837-105">Prevents PowerShell endpoints from receiving remote connections.</span></span>

## <span data-ttu-id="fe837-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fe837-106">SYNTAX</span></span>

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fe837-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fe837-107">DESCRIPTION</span></span>

<span data-ttu-id="fe837-108">De `Disable-PSRemoting` cmdlet blokkeert externe toegang tot alle configuraties van de sessie-eindpunt versie 6 en groter op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="fe837-108">The `Disable-PSRemoting` cmdlet blocks remote access to all PowerShell version 6 and greater session endpoint configurations on the local computer.</span></span> <span data-ttu-id="fe837-109">Dit heeft geen invloed op Windows Power shell-eindpunt configuraties.</span><span class="sxs-lookup"><span data-stu-id="fe837-109">It does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="fe837-110">Als u configuraties van Windows Power shell-sessie-eind punten wilt uitschakelen, voert u `Disable-PSRemoting` de opdracht uit vanuit een Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="fe837-110">To disable Windows PowerShell session endpoint configurations, run `Disable-PSRemoting` command from within a Windows PowerShell session.</span></span>

<span data-ttu-id="fe837-111">Gebruik de cmdlet om externe toegang opnieuw in te scha kelen voor alle configuraties van Power shell versie 6 en de grotere sessie-eind punten `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="fe837-111">To re-enable remote access to all PowerShell version 6 and greater session endpoint configurations, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="fe837-112">Als u externe toegang tot alle Windows Power shell-sessie-eindpunt configuraties opnieuw wilt inschakelen, voert u `Enable-PSRemoting` uit vanuit een Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="fe837-112">To re-enable remote access to all Windows PowerShell session endpoint configurations, run `Enable-PSRemoting` from within a Windows PowerShell session.</span></span>

> [!NOTE]
> <span data-ttu-id="fe837-113">Als u alle Power shell-externe toegang wilt uitschakelen voor een lokale Windows-computer, moet u deze opdracht uitvoeren vanaf een van de Power shell-versie 6 of hoger en vanuit een Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="fe837-113">If you want to disable all PowerShell remote access to a local Windows machine, you must run this command both from a within PowerShell version 6 or greater session and from within a Windows PowerShell session.</span></span> <span data-ttu-id="fe837-114">Windows Power shell is standaard geïnstalleerd op alle Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="fe837-114">Windows PowerShell is installed on all Windows machines by default.</span></span>

<span data-ttu-id="fe837-115">Gebruik de cmdlets en om externe toegang tot specifieke configuraties voor sessie-eind punten uit te scha kelen en opnieuw in te scha kelen `Enable-PSSessionConfiguration` `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="fe837-115">To disable and re-enable remote access to specific session endpoint configurations, use the `Enable-PSSessionConfiguration` and `Disable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="fe837-116">Als u specifieke toegangs configuraties van afzonderlijke eind punten wilt instellen, gebruikt u de `Set-PSSessionConfiguration` cmdlet in combi natie met de para meter **AccessMode** .</span><span class="sxs-lookup"><span data-stu-id="fe837-116">To set specific access configurations of individual endpoints, use the `Set-PSSessionConfiguration` cmdlet along with the **AccessMode** parameter.</span></span> <span data-ttu-id="fe837-117">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="fe837-117">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="fe837-118">Zelfs nadat `Disable-PSRemoting` u hebt uitgevoerd, kunt u nog steeds loop back-verbindingen maken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="fe837-118">Even after running `Disable-PSRemoting` you can still make loopback connections on the local machine.</span></span> <span data-ttu-id="fe837-119">Een loop back-verbinding is een externe Power shell-sessie die afkomstig is van en die verbinding maakt met dezelfde lokale computer.</span><span class="sxs-lookup"><span data-stu-id="fe837-119">A loopback connection is a PowerShell remote session that originates from and connects to the same local machine.</span></span> <span data-ttu-id="fe837-120">Externe sessies van externe bronnen blijven geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="fe837-120">Remote sessions from external sources remain blocked.</span></span> <span data-ttu-id="fe837-121">Voor loop back-verbindingen moet u impliciete referenties gebruiken in combi natie met de para meter **EnableNetworkAccess** .</span><span class="sxs-lookup"><span data-stu-id="fe837-121">For loopback connections you must use implicit credentials along the **EnableNetworkAccess** parameter.</span></span> <span data-ttu-id="fe837-122">Zie [New-PSSession](New-PSSession.md)voor meer informatie over loop back-verbindingen.</span><span class="sxs-lookup"><span data-stu-id="fe837-122">For more information about loopback connections, see [New-PSSession](New-PSSession.md).</span></span>

<span data-ttu-id="fe837-123">Deze cmdlet is alleen beschikbaar op het Windows-platform.</span><span class="sxs-lookup"><span data-stu-id="fe837-123">This cmdlet is only available on the Windows platform.</span></span> <span data-ttu-id="fe837-124">Het is niet beschikbaar in Linux-of macOS-versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="fe837-124">It is not available on Linux or macOS versions of PowerShell.</span></span> <span data-ttu-id="fe837-125">Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="fe837-125">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

## <span data-ttu-id="fe837-126">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fe837-126">EXAMPLES</span></span>

### <span data-ttu-id="fe837-127">Voor beeld 1: externe toegang tot alle Power shell-sessie configuraties voor komen</span><span class="sxs-lookup"><span data-stu-id="fe837-127">Example 1: Prevent remote access to all PowerShell session configurations</span></span>

<span data-ttu-id="fe837-128">In dit voor beeld wordt voor komen dat externe toegang tot alle configuraties van het Power shell-sessie eindpunt op de computer.</span><span class="sxs-lookup"><span data-stu-id="fe837-128">This example prevents remote access to all PowerShell session endpoint configurations on the computer.</span></span>

```powershell
Disable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="fe837-129">Voor beeld 2: externe toegang tot alle Power shell-sessie configuraties zonder bevestigings prompt voor komen</span><span class="sxs-lookup"><span data-stu-id="fe837-129">Example 2: Prevent remote access to all PowerShell session configurations without confirmation prompt</span></span>

<span data-ttu-id="fe837-130">In dit voor beeld wordt voor komen dat alle configuratie van het eind punt van een Power shell-sessie op de computer zonder dat dit wordt gevraagd</span><span class="sxs-lookup"><span data-stu-id="fe837-130">This example prevents remote access all PowerShell session endpoint configurations on the computer without prompting.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="fe837-131">Voor beeld 3: gevolgen van het uitvoeren van deze cmdlet</span><span class="sxs-lookup"><span data-stu-id="fe837-131">Example 3: Effects of running this cmdlet</span></span>

<span data-ttu-id="fe837-132">In dit voor beeld ziet u het effect van het gebruik van de `Disable-PSRemoting` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe837-132">This example shows the effect of using the `Disable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="fe837-133">Als u deze opdracht reeks wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="fe837-133">To run this command sequence, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="fe837-134">Nadat de sessie configuraties zijn uitgeschakeld, `New-PSSession` probeert de cmdlet een externe sessie te maken naar de lokale computer (ook wel ' loop back ' genoemd).</span><span class="sxs-lookup"><span data-stu-id="fe837-134">After disabling the sessions configurations, the `New-PSSession` cmdlet attempts to create a remote session to the local computer (also known as a "loopback").</span></span> <span data-ttu-id="fe837-135">Omdat externe toegang is uitgeschakeld op de lokale computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="fe837-135">Because remote access is disabled on the local machine, the command fails.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### <span data-ttu-id="fe837-136">Voor beeld 4: gevolgen van het uitvoeren van deze cmdlet en Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="fe837-136">Example 4: Effects of running this cmdlet and Enable-PSRemoting</span></span>

<span data-ttu-id="fe837-137">In dit voor beeld ziet u het effect van de sessie configuraties van met de- `Disable-PSRemoting` en- `Enable-PSRemoting` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fe837-137">This example shows the effect on the session configurations of using the `Disable-PSRemoting` and `Enable-PSRemoting` cmdlets.</span></span>

<span data-ttu-id="fe837-138">`Disable-PSRemoting` wordt gebruikt om externe toegang uit te scha kelen voor alle configuraties van de Power shell-sessie-eind punten.</span><span class="sxs-lookup"><span data-stu-id="fe837-138">`Disable-PSRemoting` is used to disable remote access to all PowerShell session endpoint configurations.</span></span> <span data-ttu-id="fe837-139">De **Force** -para meter onderdrukt alle gebruikers prompts.</span><span class="sxs-lookup"><span data-stu-id="fe837-139">The **Force** parameter suppresses all user prompts.</span></span> <span data-ttu-id="fe837-140">`Get-PSSessionConfiguration`Met de `Format-Table` cmdlets en worden de sessie configuraties op de computer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fe837-140">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations on the computer.</span></span>

<span data-ttu-id="fe837-141">In de uitvoer ziet u dat alle externe gebruikers met een netwerk token de toegang tot de eindpunt configuraties hebben geweigerd.</span><span class="sxs-lookup"><span data-stu-id="fe837-141">The output shows that all remote users with a network token are denied access to the endpoint configurations.</span></span> <span data-ttu-id="fe837-142">De groep Administrators op de lokale computer is toegang tot de eindpunt configuraties, zolang ze lokaal verbinding maken (ook wel loop back) en impliciete referenties gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fe837-142">Administrators group on the local computer are allowed access to the endpoint configurations as long as they are connecting locally (also known as loopback) and using implicit credentials.</span></span>

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
```

<span data-ttu-id="fe837-143">`Enable-PSRemoting`Met de cmdlet wordt externe toegang tot alle configuratie van het eind punt van de Power shell-sessie op de computer opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fe837-143">The `Enable-PSRemoting` cmdlet re-enables remote access to all PowerShell session endpoint configurations on the computer.</span></span> <span data-ttu-id="fe837-144">De **Force** -para meter onderdrukt alle gebruikers prompts en start de WinRM-service opnieuw op zonder toestemming te vragen.</span><span class="sxs-lookup"><span data-stu-id="fe837-144">The **Force** parameter suppresses all user prompts and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="fe837-145">In de nieuwe uitvoer ziet u dat de security descriptors voor **AccessDenied** zijn verwijderd uit alle sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="fe837-145">The new output shows that the **AccessDenied** security descriptors have been removed from all session configurations.</span></span>

### <span data-ttu-id="fe837-146">Voor beeld 5: loop back-verbindingen met uitgeschakelde sessie-eindpunt configuraties</span><span class="sxs-lookup"><span data-stu-id="fe837-146">Example 5: Loopback connections with disabled session endpoint configurations</span></span>

<span data-ttu-id="fe837-147">In dit voor beeld ziet u hoe eindpunt configuraties worden uitgeschakeld en hoe u een geslaagde loop back-verbinding kunt maken met een uitgeschakeld eind punt.</span><span class="sxs-lookup"><span data-stu-id="fe837-147">This example demonstrates how endpoint configurations are disabled, and shows how to make a successful loopback connection to a disabled endpoint.</span></span> <span data-ttu-id="fe837-148">`Disable-PSRemoting` Hiermee worden alle configuratie van het eind punt van een Power shell-sessie uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fe837-148">`Disable-PSRemoting` disables all PowerShell session endpoint configurations.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -Credential (Get-Credential)
```

```Output
PowerShell credential request
Enter your credentials.
User: UserName
Password for user UserName: ************

New-PSSession: [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

<span data-ttu-id="fe837-149">Het eerste gebruik van `New-PSSession` pogingen om een externe sessie te maken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="fe837-149">The first use of `New-PSSession` attempts to create a remote session to the local machine.</span></span> <span data-ttu-id="fe837-150">De para meter **configuratiepad** wordt gebruikt om een uitgeschakeld Power shell-eind punt op te geven.</span><span class="sxs-lookup"><span data-stu-id="fe837-150">The **ConfigurationName** parameter is used to specify a disabled PowerShell endpoint.</span></span> <span data-ttu-id="fe837-151">Referenties worden expliciet door gegeven aan de opdracht via de para meter **Credential** .</span><span class="sxs-lookup"><span data-stu-id="fe837-151">Credentials are explicitly passed to the command through the **Credential** parameter.</span></span> <span data-ttu-id="fe837-152">Dit type verbinding loopt via de netwerk stack en is geen loop back.</span><span class="sxs-lookup"><span data-stu-id="fe837-152">This type of connection goes through the network stack and is not a loopback.</span></span> <span data-ttu-id="fe837-153">Daarom mislukt de verbindings poging met het uitgeschakelde eind punt met een fout bericht **geweigerd** .</span><span class="sxs-lookup"><span data-stu-id="fe837-153">Consequently, the connection attempt to the disabled endpoint fails with an **Access is denied** error.</span></span>

<span data-ttu-id="fe837-154">Het tweede gebruik van `New-PSSession` ook pogingen om een externe sessie te maken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="fe837-154">The second use of `New-PSSession` also attempts to create a remote session to the local machine.</span></span>
<span data-ttu-id="fe837-155">In dit geval slaagt dit omdat het een loop back-verbinding is die de netwerk stack omzeilt.</span><span class="sxs-lookup"><span data-stu-id="fe837-155">In this case, it succeeds because it is a loopback connection that bypasses the network stack.</span></span>

<span data-ttu-id="fe837-156">Er wordt een loop back-verbinding gemaakt wanneer aan de volgende voor waarden wordt voldaan:</span><span class="sxs-lookup"><span data-stu-id="fe837-156">A loopback connection is created when the following conditions are met:</span></span>

- <span data-ttu-id="fe837-157">De computer naam waarmee verbinding moet worden gemaakt, is ' localhost '.</span><span class="sxs-lookup"><span data-stu-id="fe837-157">The computer name to connect to is 'localhost'.</span></span>
- <span data-ttu-id="fe837-158">Er zijn geen referenties door gegeven in.</span><span class="sxs-lookup"><span data-stu-id="fe837-158">No credentials are passed in.</span></span> <span data-ttu-id="fe837-159">De huidige aangemelde gebruiker (impliciete referenties) wordt gebruikt voor de verbinding.</span><span class="sxs-lookup"><span data-stu-id="fe837-159">Current logged in user (implicit credentials) is used for the connection.</span></span>
- <span data-ttu-id="fe837-160">De switch parameter **EnableNetworkAccess** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fe837-160">The **EnableNetworkAccess** switch parameter is used.</span></span>

<span data-ttu-id="fe837-161">Zie [New-PSSession](New-PSSession.md) document voor meer informatie over loop back-verbindingen.</span><span class="sxs-lookup"><span data-stu-id="fe837-161">For more information on loopback connections, see [New-PSSession](New-PSSession.md) document.</span></span>

### <span data-ttu-id="fe837-162">Voor beeld 6: alle Power shell-configuraties voor externe eind punten uitschakelen</span><span class="sxs-lookup"><span data-stu-id="fe837-162">Example 6: Disabling all PowerShell remoting endpoint configurations</span></span>

<span data-ttu-id="fe837-163">Dit voor beeld laat zien hoe het uitvoeren van de `Disable-PSRemoting` opdracht niet van invloed is op Windows Power shell-eindpunt configuraties.</span><span class="sxs-lookup"><span data-stu-id="fe837-163">This example demonstrates how running the `Disable-PSRemoting` command does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="fe837-164">`Get-PSSessionConfiguration` uitvoeren in Windows Power shell toont alle eindpunt configuraties.</span><span class="sxs-lookup"><span data-stu-id="fe837-164">`Get-PSSessionConfiguration` run within Windows PowerShell shows all endpoint configurations.</span></span> <span data-ttu-id="fe837-165">We zien dat de configuratie van Windows Power shell-eind punten niet is uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fe837-165">We see that the Windows PowerShell endpoint configurations are not disabled.</span></span>

```powershell
Disable-PSRemoting -Force
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

```powershell
powershell.exe -command 'Disable-PSRemoting -Force'
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting or
Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the
Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management
                Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

<span data-ttu-id="fe837-166">Als u deze eindpunt configuraties wilt uitschakelen, moet u de `Disable-PSRemoting` opdracht uitvoeren vanuit een Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="fe837-166">To disable these endpoint configurations, the `Disable-PSRemoting` command must be run from within a Windows PowerShell session.</span></span> <span data-ttu-id="fe837-167">Vanaf nu `Get-PSSessionConfiguration` voert u uit vanuit Windows Power shell om aan te geven dat alle eindpunt configuraties zijn uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fe837-167">Now, `Get-PSSessionConfiguration` run from within Windows PowerShell shows that all endpoint configurations are disabled.</span></span>

### <span data-ttu-id="fe837-168">Voor beeld 7: externe toegang tot sessie configuraties met aangepaste Security descriptors voor komen</span><span class="sxs-lookup"><span data-stu-id="fe837-168">Example 7: Prevent remote access to session configurations that have custom security descriptors</span></span>

<span data-ttu-id="fe837-169">In dit voor beeld wordt gedemonstreerd dat `Disable-PSRemoting` externe toegang wordt uitgeschakeld voor alle sessie configuraties die sessie configuraties met aangepaste Security descriptors bevatten.</span><span class="sxs-lookup"><span data-stu-id="fe837-169">This example demonstrates that the `Disable-PSRemoting` cmdlet disables remote access to all session configurations that include session configurations with custom security descriptors.</span></span>

<span data-ttu-id="fe837-170">`Register-PSSessionConfiguration` Hiermee maakt u de configuratie van de **test** sessie.</span><span class="sxs-lookup"><span data-stu-id="fe837-170">`Register-PSSessionConfiguration` creates the **Test** session configuration.</span></span> <span data-ttu-id="fe837-171">De **filepath** para meter geeft een sessie configuratie bestand op waarmee de sessie wordt aangepast.</span><span class="sxs-lookup"><span data-stu-id="fe837-171">The **FilePath** parameter specifies a session configuration file that customizes the session.</span></span> <span data-ttu-id="fe837-172">De para meter **ShowSecurityDescriptorUI** geeft een dialoog venster weer waarin machtigingen worden ingesteld voor de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="fe837-172">The **ShowSecurityDescriptorUI** parameter displays a dialog box that sets permissions for the session configuration.</span></span> <span data-ttu-id="fe837-173">In het dialoog venster machtigingen maken we aangepaste machtigingen voor volledige toegang voor de aangegeven gebruiker.</span><span class="sxs-lookup"><span data-stu-id="fe837-173">In the Permissions dialog box, we create custom full-access permissions for the indicated user.</span></span>

<span data-ttu-id="fe837-174">`Get-PSSessionConfiguration`Met de `Format-Table` cmdlets en worden de sessie configuraties en de bijbehorende eigenschappen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fe837-174">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations and their properties.</span></span> <span data-ttu-id="fe837-175">In de uitvoer ziet u dat de configuratie van de **test** sessie interactieve toegang en speciale machtigingen voor de aangegeven gebruiker toestaat.</span><span class="sxs-lookup"><span data-stu-id="fe837-175">The output shows that the **Test** session configuration allows interactive access and special permissions for the indicated user.</span></span>

<span data-ttu-id="fe837-176">`Disable-PSRemoting` externe toegang tot alle sessie configuraties wordt uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fe837-176">`Disable-PSRemoting` disables remote access to all session configurations.</span></span>

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, User01 AccessAllowed

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName Test
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

<span data-ttu-id="fe837-177">Met de `Get-PSSessionConfiguration` `Format-Table` cmdlets en wordt aangegeven dat een **AccessDenied** -security descriptor voor alle netwerk gebruikers wordt toegevoegd aan alle sessie configuraties, met inbegrip van de configuratie van de **test** sessie.</span><span class="sxs-lookup"><span data-stu-id="fe837-177">Now the `Get-PSSessionConfiguration` and `Format-Table` cmdlets shows that an **AccessDenied** security descriptor for all network users is added to all session configurations, including the **Test** session configuration.</span></span> <span data-ttu-id="fe837-178">Hoewel de andere security descriptors niet worden gewijzigd, heeft de security descriptor network_deny_all voor rang.</span><span class="sxs-lookup"><span data-stu-id="fe837-178">Although the other security descriptors are not changed, the "network_deny_all" security descriptor takes precedence.</span></span> <span data-ttu-id="fe837-179">Dit wordt geïllustreerd door de poging om `New-PSSession` verbinding te maken met de configuratie van de **test** sessie.</span><span class="sxs-lookup"><span data-stu-id="fe837-179">This is illustrated by the attempt to use `New-PSSession` to connect to the **Test** session configuration.</span></span>

### <span data-ttu-id="fe837-180">Voor beeld 8: externe toegang tot geselecteerde sessie configuraties opnieuw inschakelen</span><span class="sxs-lookup"><span data-stu-id="fe837-180">Example 8: Re-enable remote access to selected session configurations</span></span>

<span data-ttu-id="fe837-181">In dit voor beeld ziet u hoe u externe toegang opnieuw inschakelt voor geselecteerde sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="fe837-181">This example shows how to re-enable remote access only to selected session configurations.</span></span> <span data-ttu-id="fe837-182">Nadat alle sessie configuraties zijn uitgeschakeld, wordt een specifieke sessie opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fe837-182">After disabling all session configurations, we re-enable a specific session.</span></span>

<span data-ttu-id="fe837-183">De `Set-PSSessionConfiguration` cmdlet wordt gebruikt om de configuratie van de **Power shell. 6** -sessie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="fe837-183">The `Set-PSSessionConfiguration` cmdlet is used to change the **PowerShell.6** session configuration.</span></span> <span data-ttu-id="fe837-184">De **AccessMode** para meter met de waarde **extern** opnieuw inschakelen externe toegang tot de configuratie.</span><span class="sxs-lookup"><span data-stu-id="fe837-184">The **AccessMode** parameter with a value of **Remote** re-enables remote access to the configuration.</span></span>

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name PowerShell.6 -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\ ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
```

## <span data-ttu-id="fe837-185">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fe837-185">PARAMETERS</span></span>

### <span data-ttu-id="fe837-186">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fe837-186">-Confirm</span></span>

<span data-ttu-id="fe837-187">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fe837-187">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe837-188">-Force</span><span class="sxs-lookup"><span data-stu-id="fe837-188">-Force</span></span>

<span data-ttu-id="fe837-189">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="fe837-189">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="fe837-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fe837-190">-WhatIf</span></span>

<span data-ttu-id="fe837-191">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fe837-191">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="fe837-192">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fe837-192">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe837-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fe837-193">CommonParameters</span></span>

<span data-ttu-id="fe837-194">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fe837-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fe837-195">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fe837-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fe837-196">INVOER</span><span class="sxs-lookup"><span data-stu-id="fe837-196">INPUTS</span></span>

### <span data-ttu-id="fe837-197">Geen</span><span class="sxs-lookup"><span data-stu-id="fe837-197">None</span></span>

<span data-ttu-id="fe837-198">U kunt geen objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe837-198">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="fe837-199">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fe837-199">OUTPUTS</span></span>

### <span data-ttu-id="fe837-200">Geen</span><span class="sxs-lookup"><span data-stu-id="fe837-200">None</span></span>

<span data-ttu-id="fe837-201">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="fe837-201">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fe837-202">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fe837-202">NOTES</span></span>

- <span data-ttu-id="fe837-203">Door de sessie configuraties uit te scha kelen, worden niet alle wijzigingen ongedaan gemaakt die zijn aangebracht door de- `Enable-PSRemoting` of- `Enable-PSSessionConfiguration` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fe837-203">Disabling the session configurations does not undo all the changes that were made by the `Enable-PSRemoting` or `Enable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="fe837-204">Mogelijk moet u de volgende wijzigingen hand matig ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="fe837-204">You might have to undo the following changes manually.</span></span>

  1. <span data-ttu-id="fe837-205">Stop de WinRM-service en schakel deze uit.</span><span class="sxs-lookup"><span data-stu-id="fe837-205">Stop and disable the WinRM service.</span></span>
  2. <span data-ttu-id="fe837-206">Verwijder de listener die aanvragen op een IP-adres accepteert.</span><span class="sxs-lookup"><span data-stu-id="fe837-206">Delete the listener that accepts requests on any IP address.</span></span>
  3. <span data-ttu-id="fe837-207">Schakel de firewall-uitzonde ringen voor de communicatie van WS-Management uit.</span><span class="sxs-lookup"><span data-stu-id="fe837-207">Disable the firewall exceptions for WS-Management communications.</span></span>
  4. <span data-ttu-id="fe837-208">Herstel de waarde van LocalAccountTokenFilterPolicy in 0, waardoor externe toegang wordt beperkt tot leden van de groep Administrators op de computer.</span><span class="sxs-lookup"><span data-stu-id="fe837-208">Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the Administrators group on the computer.</span></span>

- <span data-ttu-id="fe837-209">Een configuratie van het eind punt van een sessie is een groep instellingen waarmee de omgeving voor een sessie wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="fe837-209">A session endpoint configuration is a group of settings that define the environment for a session.</span></span>
  <span data-ttu-id="fe837-210">Elke sessie die verbinding maakt met de computer, moet een van de sessie-eindpunt configuraties gebruiken die zijn geregistreerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="fe837-210">Every session that connects to the computer must use one of the session endpoint configurations that are registered on the computer.</span></span> <span data-ttu-id="fe837-211">Door externe toegang tot alle sessie-eindpunt configuraties te weigeren, voor komt u dat externe gebruikers sessies kunnen instellen die verbinding maken met de computer.</span><span class="sxs-lookup"><span data-stu-id="fe837-211">By denying remote access to all session endpoint configurations, you effectively prevent remote users from establishing sessions that connect to the computer.</span></span>

## <span data-ttu-id="fe837-212">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fe837-212">RELATED LINKS</span></span>

[<span data-ttu-id="fe837-213">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="fe837-213">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="fe837-214">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="fe837-214">Enable-PSRemoting</span></span>](Enable-PSRemoting.md)

[<span data-ttu-id="fe837-215">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="fe837-215">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="fe837-216">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="fe837-216">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="fe837-217">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="fe837-217">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="fe837-218">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="fe837-218">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="fe837-219">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="fe837-219">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="fe837-220">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="fe837-220">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

