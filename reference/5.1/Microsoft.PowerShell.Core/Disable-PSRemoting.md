---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 3a281786f99b2a46d0aeb9785480f02b35b2b433
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249977"
---
# <span data-ttu-id="ab69e-103">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="ab69e-103">Disable-PSRemoting</span></span>

## <span data-ttu-id="ab69e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ab69e-104">SYNOPSIS</span></span>
<span data-ttu-id="ab69e-105">Hiermee voor komt u dat Power shell-eind punten externe verbindingen ontvangen.</span><span class="sxs-lookup"><span data-stu-id="ab69e-105">Prevents PowerShell endpoints from receiving remote connections.</span></span>

## <span data-ttu-id="ab69e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ab69e-106">SYNTAX</span></span>

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ab69e-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ab69e-107">DESCRIPTION</span></span>

<span data-ttu-id="ab69e-108">De `Disable-PSRemoting` cmdlet blokkeert externe toegang tot alle configuraties van Windows Power shell-sessie-eind punten op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ab69e-108">The `Disable-PSRemoting` cmdlet blocks remote access to all Windows PowerShell session endpoint configurations on the local computer.</span></span> <span data-ttu-id="ab69e-109">Dit omvat alle eind punten die zijn gemaakt met Power shell 6 of hoger.</span><span class="sxs-lookup"><span data-stu-id="ab69e-109">This includes any endpoints created by PowerShell 6 or higher.</span></span>

<span data-ttu-id="ab69e-110">Als u externe toegang tot alle sessie configuraties opnieuw wilt inschakelen, gebruikt u de `Enable-PSRemoting` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab69e-110">To re-enable remote access to all session configurations, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="ab69e-111">Dit omvat alle eind punten die zijn gemaakt met Power shell 6 of hoger.</span><span class="sxs-lookup"><span data-stu-id="ab69e-111">This includes any endpoints created by PowerShell 6 or higher.</span></span> <span data-ttu-id="ab69e-112">Als u externe toegang tot geselecteerde sessie configuraties wilt inschakelen, gebruikt u de para meter **AccessMode** van de `Set-PSSessionConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab69e-112">To enable remote access to selected session configurations, use the **AccessMode** parameter of the `Set-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="ab69e-113">U kunt ook de `Enable-PSSessionConfiguration` `Disable-PSSessionConfiguration` cmdlets en gebruiken om de sessie configuraties voor alle gebruikers in te scha kelen en uit te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="ab69e-113">You can also use the `Enable-PSSessionConfiguration` and `Disable-PSSessionConfiguration` cmdlets to enable and disable session configurations for all users.</span></span> <span data-ttu-id="ab69e-114">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="ab69e-114">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ab69e-115">Zelfs nadat `Disable-PSRemoting` u hebt uitgevoerd, kunt u nog steeds loop back-verbindingen maken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ab69e-115">Even after running `Disable-PSRemoting` you can still make loopback connections on the local machine.</span></span> <span data-ttu-id="ab69e-116">Een loop back-verbinding is een externe Power shell-sessie die afkomstig is van en die verbinding maakt met dezelfde lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ab69e-116">A loopback connection is a PowerShell remote session that originates from and connects to the same local machine.</span></span> <span data-ttu-id="ab69e-117">Externe sessies van externe bronnen blijven geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="ab69e-117">Remote sessions from external sources remain blocked.</span></span> <span data-ttu-id="ab69e-118">Voor loop back-verbindingen moet u impliciete referenties gebruiken in combi natie met de para meter **EnableNetworkAccess** .</span><span class="sxs-lookup"><span data-stu-id="ab69e-118">For loopback connections you must use implicit credentials along the **EnableNetworkAccess** parameter.</span></span> <span data-ttu-id="ab69e-119">Zie [New-PSSession](New-PSSession.md)voor meer informatie over loop back-verbindingen.</span><span class="sxs-lookup"><span data-stu-id="ab69e-119">For more information about loopback connections, see [New-PSSession](New-PSSession.md).</span></span>

<span data-ttu-id="ab69e-120">Als u deze cmdlet wilt uitvoeren, start u Windows Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="ab69e-120">To run this cmdlet, start Windows PowerShell with the **Run as administrator** option.</span></span>

## <span data-ttu-id="ab69e-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ab69e-121">EXAMPLES</span></span>

### <span data-ttu-id="ab69e-122">Voor beeld 1: externe toegang tot alle sessie configuraties voor komen</span><span class="sxs-lookup"><span data-stu-id="ab69e-122">Example 1: Prevent remote access to all session configurations</span></span>

<span data-ttu-id="ab69e-123">In dit voor beeld wordt voor komen dat externe toegang tot alle configuraties van het Power shell-sessie eindpunt op de computer.</span><span class="sxs-lookup"><span data-stu-id="ab69e-123">This example prevents remote access to all PowerShell session endpoint configurations on the computer.</span></span>

```powershell
Disable-PSRemoting
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="ab69e-124">Voor beeld 2: externe toegang tot alle sessie configuraties verhinderen zonder bevestiging te vragen</span><span class="sxs-lookup"><span data-stu-id="ab69e-124">Example 2: Prevent remote access to all session configurations without confirmation prompt</span></span>

<span data-ttu-id="ab69e-125">In dit voor beeld wordt voor komen dat alle configuratie van het eind punt van een Power shell-sessie op de computer zonder dat dit wordt gevraagd</span><span class="sxs-lookup"><span data-stu-id="ab69e-125">This example prevents remote access all PowerShell session endpoint configurations on the computer without prompting.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="ab69e-126">Voor beeld 3: gevolgen van het uitvoeren van deze cmdlet</span><span class="sxs-lookup"><span data-stu-id="ab69e-126">Example 3: Effects of running this cmdlet</span></span>

<span data-ttu-id="ab69e-127">In dit voor beeld ziet u het effect van het gebruik van de `Disable-PSRemoting` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab69e-127">This example shows the effect of using the `Disable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="ab69e-128">Als u deze opdracht reeks wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="ab69e-128">To run this command sequence, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="ab69e-129">Nadat de sessie configuraties zijn uitgeschakeld, `New-PSSession` probeert de cmdlet een externe sessie te maken naar de lokale computer (ook wel ' loop back ' genoemd).</span><span class="sxs-lookup"><span data-stu-id="ab69e-129">After disabling the sessions configurations, the `New-PSSession` cmdlet attempts to create a remote session to the local computer (also known as a "loopback").</span></span> <span data-ttu-id="ab69e-130">Omdat externe toegang is uitgeschakeld op de lokale computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="ab69e-130">Because remote access is disabled on the local machine, the command fails.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
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

### <span data-ttu-id="ab69e-131">Voor beeld 4: gevolgen van het uitvoeren van deze cmdlet en Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="ab69e-131">Example 4: Effects of running this cmdlet and Enable-PSRemoting</span></span>

<span data-ttu-id="ab69e-132">In dit voor beeld ziet u het effect van de sessie configuraties van met de- `Disable-PSRemoting` en- `Enable-PSRemoting` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ab69e-132">This example shows the effect on the session configurations of using the `Disable-PSRemoting` and `Enable-PSRemoting` cmdlets.</span></span>

<span data-ttu-id="ab69e-133">`Disable-PSRemoting` wordt gebruikt om externe toegang uit te scha kelen voor alle configuraties van de Power shell-sessie-eind punten.</span><span class="sxs-lookup"><span data-stu-id="ab69e-133">`Disable-PSRemoting` is used to disable remote access to all PowerShell session endpoint configurations.</span></span> <span data-ttu-id="ab69e-134">De **Force** -para meter onderdrukt alle gebruikers prompts.</span><span class="sxs-lookup"><span data-stu-id="ab69e-134">The **Force** parameter suppresses all user prompts.</span></span> <span data-ttu-id="ab69e-135">`Get-PSSessionConfiguration`Met de `Format-Table` cmdlets en worden de sessie configuraties op de computer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ab69e-135">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations on the computer.</span></span>

<span data-ttu-id="ab69e-136">In de uitvoer ziet u dat alle externe gebruikers met een netwerk token de toegang tot de eindpunt configuraties hebben geweigerd.</span><span class="sxs-lookup"><span data-stu-id="ab69e-136">The output shows that all remote users with a network token are denied access to the endpoint configurations.</span></span> <span data-ttu-id="ab69e-137">De groep Administrators op de lokale computer is toegang tot de eindpunt configuraties, zolang ze lokaal verbinding maken (ook wel loop back) en impliciete referenties gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ab69e-137">Administrators group on the local computer are allowed access to the endpoint configurations as long as they are connecting locally (also known as loopback) and using implicit credentials.</span></span>

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow BUILTIN\Administrators AccessAllowed
microsoft.powershell32        BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="ab69e-138">`Enable-PSRemoting`Met de cmdlet wordt externe toegang tot alle configuratie van het eind punt van de Power shell-sessie op de computer opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="ab69e-138">The `Enable-PSRemoting` cmdlet re-enables remote access to all PowerShell session endpoint configurations on the computer.</span></span> <span data-ttu-id="ab69e-139">De **Force** -para meter onderdrukt alle gebruikers prompts en start de WinRM-service opnieuw op zonder toestemming te vragen.</span><span class="sxs-lookup"><span data-stu-id="ab69e-139">The **Force** parameter suppresses all user prompts and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="ab69e-140">In de nieuwe uitvoer ziet u dat de security descriptors voor **AccessDenied** zijn verwijderd uit alle sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="ab69e-140">The new output shows that the **AccessDenied** security descriptors have been removed from all session configurations.</span></span>

### <span data-ttu-id="ab69e-141">Voor beeld 5: loop back-verbindingen met uitgeschakelde sessie-eindpunt configuraties</span><span class="sxs-lookup"><span data-stu-id="ab69e-141">Example 5: Loopback connections with disabled session endpoint configurations</span></span>

<span data-ttu-id="ab69e-142">In dit voor beeld ziet u hoe eindpunt configuraties worden uitgeschakeld en hoe u een geslaagde loop back-verbinding kunt maken met een uitgeschakeld eind punt.</span><span class="sxs-lookup"><span data-stu-id="ab69e-142">This example demonstrates how endpoint configurations are disabled, and shows how to make a successful loopback connection to a disabled endpoint.</span></span> <span data-ttu-id="ab69e-143">`Disable-PSRemoting` Hiermee worden alle configuratie van het eind punt van een Power shell-sessie uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="ab69e-143">`Disable-PSRemoting` disables all PowerShell session endpoint configurations.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message : Access is
denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [New-PSSession], PSRemotin
   gTransportException
    + FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed

```

```powershell
New-PSSession -ComputerName localhost -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

<span data-ttu-id="ab69e-144">Het eerste gebruik van `New-PSSession` pogingen om een externe sessie te maken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ab69e-144">The first use of `New-PSSession` attempts to create a remote session to the local machine.</span></span> <span data-ttu-id="ab69e-145">Dit type verbinding loopt via de netwerk stack en is geen loop back.</span><span class="sxs-lookup"><span data-stu-id="ab69e-145">This type of connection goes through the network stack and is not a loopback.</span></span> <span data-ttu-id="ab69e-146">Daarom mislukt de verbindings poging met het uitgeschakelde eind punt met een fout bericht **geweigerd** .</span><span class="sxs-lookup"><span data-stu-id="ab69e-146">Consequently, the connection attempt to the disabled endpoint fails with an **Access is denied** error.</span></span>

<span data-ttu-id="ab69e-147">Het tweede gebruik van `New-PSSession` ook pogingen om een externe sessie te maken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ab69e-147">The second use of `New-PSSession` also attempts to create a remote session to the local machine.</span></span>
<span data-ttu-id="ab69e-148">In dit geval slaagt dit omdat het een loop back-verbinding is die de netwerk stack omzeilt.</span><span class="sxs-lookup"><span data-stu-id="ab69e-148">In this case, it succeeds because it is a loopback connection that bypasses the network stack.</span></span>

<span data-ttu-id="ab69e-149">Er wordt een loop back-verbinding gemaakt wanneer aan de volgende voor waarden wordt voldaan:</span><span class="sxs-lookup"><span data-stu-id="ab69e-149">A loopback connection is created when the following conditions are met:</span></span>

- <span data-ttu-id="ab69e-150">De computer naam waarmee verbinding moet worden gemaakt, is ' localhost '.</span><span class="sxs-lookup"><span data-stu-id="ab69e-150">The computer name to connect to is 'localhost'.</span></span>
- <span data-ttu-id="ab69e-151">Er zijn geen referenties door gegeven in.</span><span class="sxs-lookup"><span data-stu-id="ab69e-151">No credentials are passed in.</span></span> <span data-ttu-id="ab69e-152">De huidige aangemelde gebruiker (impliciete referenties) wordt gebruikt voor de verbinding.</span><span class="sxs-lookup"><span data-stu-id="ab69e-152">Current logged in user (implicit credentials) is used for the connection.</span></span>
- <span data-ttu-id="ab69e-153">De switch parameter **EnableNetworkAccess** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ab69e-153">The **EnableNetworkAccess** switch parameter is used.</span></span>

<span data-ttu-id="ab69e-154">Zie [New-PSSession](New-PSSession.md) document voor meer informatie over loop back-verbindingen.</span><span class="sxs-lookup"><span data-stu-id="ab69e-154">For more information on loopback connections, see [New-PSSession](New-PSSession.md) document.</span></span>

### <span data-ttu-id="ab69e-155">Voor beeld 6: externe toegang tot sessie configuraties met aangepaste Security descriptors voor komen</span><span class="sxs-lookup"><span data-stu-id="ab69e-155">Example 6: Prevent remote access to session configurations that have custom security descriptors</span></span>

<span data-ttu-id="ab69e-156">In dit voor beeld wordt gedemonstreerd dat `Disable-PSRemoting` externe toegang wordt uitgeschakeld voor alle sessie configuraties die sessie configuraties met aangepaste Security descriptors bevatten.</span><span class="sxs-lookup"><span data-stu-id="ab69e-156">This example demonstrates that the `Disable-PSRemoting` cmdlet disables remote access to all session configurations that include session configurations with custom security descriptors.</span></span>

<span data-ttu-id="ab69e-157">`Register-PSSessionConfiguration` Hiermee maakt u de configuratie van de **test** sessie.</span><span class="sxs-lookup"><span data-stu-id="ab69e-157">`Register-PSSessionConfiguration` creates the **Test** session configuration.</span></span> <span data-ttu-id="ab69e-158">De **filepath** para meter geeft een sessie configuratie bestand op waarmee de sessie wordt aangepast.</span><span class="sxs-lookup"><span data-stu-id="ab69e-158">The **FilePath** parameter specifies a session configuration file that customizes the session.</span></span> <span data-ttu-id="ab69e-159">De para meter **ShowSecurityDescriptorUI** geeft een dialoog venster weer waarin machtigingen worden ingesteld voor de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ab69e-159">The **ShowSecurityDescriptorUI** parameter displays a dialog box that sets permissions for the session configuration.</span></span> <span data-ttu-id="ab69e-160">In het dialoog venster machtigingen maken we aangepaste machtigingen voor volledige toegang voor de aangegeven gebruiker.</span><span class="sxs-lookup"><span data-stu-id="ab69e-160">In the Permissions dialog box, we create custom full-access permissions for the indicated user.</span></span>

<span data-ttu-id="ab69e-161">`Get-PSSessionConfiguration`Met de `Format-Table` cmdlets en worden de sessie configuraties en de bijbehorende eigenschappen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ab69e-161">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations and their properties.</span></span> <span data-ttu-id="ab69e-162">In de uitvoer ziet u dat de configuratie van de **test** sessie interactieve toegang en speciale machtigingen voor de aangegeven gebruiker toestaat.</span><span class="sxs-lookup"><span data-stu-id="ab69e-162">The output shows that the **Test** session configuration allows interactive access and special permissions for the indicated user.</span></span>

<span data-ttu-id="ab69e-163">`Disable-PSRemoting` externe toegang tot alle sessie configuraties wordt uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="ab69e-163">`Disable-PSRemoting` disables remote access to all session configurations.</span></span>

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
DOMAIN01\User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\NETWORK AccessDenied, NTAUTHORITY\INTERACTIVE AccessAllowed,
BUILTIN\Administrators AccessAllowed, DOMAIN01\User01 AccessAllowed


[Server01] Connecting to remote server failed with the following error message : Access is denied. For more information, see the about_Rem
ote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

<span data-ttu-id="ab69e-164">Met de `Get-PSSessionConfiguration` `Format-Table` cmdlets en wordt aangegeven dat een **AccessDenied** -security descriptor voor alle netwerk gebruikers wordt toegevoegd aan alle sessie configuraties, met inbegrip van de configuratie van de **test** sessie.</span><span class="sxs-lookup"><span data-stu-id="ab69e-164">Now the `Get-PSSessionConfiguration` and `Format-Table` cmdlets shows that an **AccessDenied** security descriptor for all network users is added to all session configurations, including the **Test** session configuration.</span></span> <span data-ttu-id="ab69e-165">Hoewel de andere security descriptors niet worden gewijzigd, heeft de security descriptor network_deny_all voor rang.</span><span class="sxs-lookup"><span data-stu-id="ab69e-165">Although the other security descriptors are not changed, the "network_deny_all" security descriptor takes precedence.</span></span> <span data-ttu-id="ab69e-166">Dit wordt geïllustreerd door de poging om `New-PSSession` verbinding te maken met de configuratie van de **test** sessie.</span><span class="sxs-lookup"><span data-stu-id="ab69e-166">This is illustrated by the attempt to use `New-PSSession` to connect to the **Test** session configuration.</span></span>

### <span data-ttu-id="ab69e-167">Voor beeld 7: externe toegang tot geselecteerde sessie configuraties opnieuw inschakelen</span><span class="sxs-lookup"><span data-stu-id="ab69e-167">Example 7: Re-enable remote access to selected session configurations</span></span>

<span data-ttu-id="ab69e-168">In dit voor beeld ziet u hoe u externe toegang opnieuw inschakelt voor geselecteerde sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="ab69e-168">This example shows how to re-enable remote access only to selected session configurations.</span></span> <span data-ttu-id="ab69e-169">Nadat alle sessie configuraties zijn uitgeschakeld, wordt een specifieke sessie opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="ab69e-169">After disabling all session configurations, we re-enable a specific session.</span></span>

<span data-ttu-id="ab69e-170">De `Set-PSSessionConfiguration` cmdlet wordt gebruikt om de **micro soft te wijzigen.** Sessie configuratie van Server Manager.</span><span class="sxs-lookup"><span data-stu-id="ab69e-170">The `Set-PSSessionConfiguration` cmdlet is used to change the **microsoft.ServerManager** session configuration.</span></span> <span data-ttu-id="ab69e-171">De **AccessMode** para meter met de waarde **extern** opnieuw inschakelen externe toegang tot de configuratie.</span><span class="sxs-lookup"><span data-stu-id="ab69e-171">The **AccessMode** parameter with a value of **Remote** re-enables remote access to the configuration.</span></span>

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name Microsoft.ServerManager -AccessMode Remote -Force
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

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
```

## <span data-ttu-id="ab69e-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ab69e-172">PARAMETERS</span></span>

### <span data-ttu-id="ab69e-173">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ab69e-173">-Confirm</span></span>

<span data-ttu-id="ab69e-174">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ab69e-174">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ab69e-175">-Force</span><span class="sxs-lookup"><span data-stu-id="ab69e-175">-Force</span></span>
<span data-ttu-id="ab69e-176">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="ab69e-176">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ab69e-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ab69e-177">-WhatIf</span></span>

<span data-ttu-id="ab69e-178">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ab69e-178">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ab69e-179">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ab69e-179">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ab69e-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab69e-180">CommonParameters</span></span>

<span data-ttu-id="ab69e-181">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ab69e-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ab69e-182">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ab69e-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ab69e-183">INVOER</span><span class="sxs-lookup"><span data-stu-id="ab69e-183">INPUTS</span></span>

### <span data-ttu-id="ab69e-184">Geen</span><span class="sxs-lookup"><span data-stu-id="ab69e-184">None</span></span>

<span data-ttu-id="ab69e-185">U kunt geen objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab69e-185">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="ab69e-186">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ab69e-186">OUTPUTS</span></span>

### <span data-ttu-id="ab69e-187">Geen</span><span class="sxs-lookup"><span data-stu-id="ab69e-187">None</span></span>

<span data-ttu-id="ab69e-188">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ab69e-188">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ab69e-189">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ab69e-189">NOTES</span></span>

- <span data-ttu-id="ab69e-190">Door de sessie configuraties uit te scha kelen, worden niet alle wijzigingen ongedaan gemaakt die zijn aangebracht door de- `Enable-PSRemoting` of- `Enable-PSSessionConfiguration` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ab69e-190">Disabling the session configurations does not undo all the changes that were made by the `Enable-PSRemoting` or `Enable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="ab69e-191">Mogelijk moet u de volgende wijzigingen hand matig ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="ab69e-191">You might have to undo the following changes manually.</span></span>

  1. <span data-ttu-id="ab69e-192">Stop de WinRM-service en schakel deze uit.</span><span class="sxs-lookup"><span data-stu-id="ab69e-192">Stop and disable the WinRM service.</span></span>
  2. <span data-ttu-id="ab69e-193">Verwijder de listener die aanvragen op een IP-adres accepteert.</span><span class="sxs-lookup"><span data-stu-id="ab69e-193">Delete the listener that accepts requests on any IP address.</span></span>
  3. <span data-ttu-id="ab69e-194">Schakel de firewall-uitzonde ringen voor de communicatie van WS-Management uit.</span><span class="sxs-lookup"><span data-stu-id="ab69e-194">Disable the firewall exceptions for WS-Management communications.</span></span>
  4. <span data-ttu-id="ab69e-195">Herstel de waarde van LocalAccountTokenFilterPolicy in 0, waardoor externe toegang wordt beperkt tot leden van de groep Administrators op de computer.</span><span class="sxs-lookup"><span data-stu-id="ab69e-195">Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the Administrators group on the computer.</span></span>

  <span data-ttu-id="ab69e-196">Een sessie configuratie is een groep instellingen waarmee de omgeving voor een sessie wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="ab69e-196">A session configuration is a group of settings that define the environment for a session.</span></span> <span data-ttu-id="ab69e-197">Elke sessie die verbinding maakt met de computer, moet een van de sessie configuraties gebruiken die zijn geregistreerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="ab69e-197">Every session that connects to the computer must use one of the session configurations that are registered on the computer.</span></span> <span data-ttu-id="ab69e-198">Door externe toegang tot alle sessie configuraties te weigeren, voor komt u dat externe gebruikers sessies kunnen instellen die verbinding maken met de computer.</span><span class="sxs-lookup"><span data-stu-id="ab69e-198">By denying remote access to all session configurations, you effectively prevent remote users from establishing sessions that connect to the computer.</span></span>

  <span data-ttu-id="ab69e-199">In Windows Power Shell 2,0 `Disable-PSRemoting` voegt een Deny_All vermelding toe aan de security descriptors van alle sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="ab69e-199">In Windows PowerShell 2.0, `Disable-PSRemoting` adds a Deny_All entry to the security descriptors of all session configurations.</span></span> <span data-ttu-id="ab69e-200">Met deze instelling wordt voor komen dat alle gebruikers door gebruikers beheerde sessies op de lokale computer maken.</span><span class="sxs-lookup"><span data-stu-id="ab69e-200">This setting prevents all users from creating user-managed sessions to the local computer.</span></span> <span data-ttu-id="ab69e-201">In Windows Power Shell 3,0 `Disable-PSRemoting` voegt een Network_Deny_All vermelding toe aan de security descriptors van alle sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="ab69e-201">In Windows PowerShell 3.0, `Disable-PSRemoting` adds a Network_Deny_All entry to the security descriptors of all session configurations.</span></span> <span data-ttu-id="ab69e-202">Met deze instelling wordt voor komen dat gebruikers op andere computers door gebruikers beheerde sessies op de lokale computer maken, maar kunnen gebruikers van de lokale computer een loop back-sessie maken die door gebruikers wordt beheerd.</span><span class="sxs-lookup"><span data-stu-id="ab69e-202">This setting prevents users on other computers from creating user-managed sessions on the local computer, but allows users of the local computer to create user-managed loopback sessions.</span></span>

  <span data-ttu-id="ab69e-203">In Windows Power Shell 2,0 `Disable-PSRemoting` is het equivalent van `Disable-PSSessionConfiguration -Name *` .</span><span class="sxs-lookup"><span data-stu-id="ab69e-203">In Windows PowerShell 2.0, `Disable-PSRemoting` is the equivalent of `Disable-PSSessionConfiguration -Name *`.</span></span> <span data-ttu-id="ab69e-204">In Windows Power Shell 3,0 en latere versies `Disable-PSRemoting` is het equivalent van `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`</span><span class="sxs-lookup"><span data-stu-id="ab69e-204">In Windows PowerShell 3.0 and later releases, `Disable-PSRemoting` is the equivalent of `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`</span></span>

## <span data-ttu-id="ab69e-205">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ab69e-205">RELATED LINKS</span></span>

[<span data-ttu-id="ab69e-206">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab69e-206">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="ab69e-207">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="ab69e-207">Enable-PSRemoting</span></span>](Enable-PSRemoting.md)

[<span data-ttu-id="ab69e-208">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab69e-208">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="ab69e-209">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="ab69e-209">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="ab69e-210">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab69e-210">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="ab69e-211">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab69e-211">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="ab69e-212">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab69e-212">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="ab69e-213">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="ab69e-213">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
