---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: a3d9506a0fd2adbb9cc093fb24f99e922dc8a938
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705896"
---
# <span data-ttu-id="22c00-102">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="22c00-102">Enable-PSRemoting</span></span>

## <span data-ttu-id="22c00-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="22c00-103">SYNOPSIS</span></span>
<span data-ttu-id="22c00-104">Hiermee configureert u de computer voor het ontvangen van externe opdrachten.</span><span class="sxs-lookup"><span data-stu-id="22c00-104">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="22c00-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="22c00-105">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="22c00-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="22c00-106">DESCRIPTION</span></span>

<span data-ttu-id="22c00-107">`Enable-PSRemoting`Met de cmdlet wordt de computer geconfigureerd om externe Power shell-opdrachten te ontvangen die worden verzonden met behulp van de WS-Management technologie.</span><span class="sxs-lookup"><span data-stu-id="22c00-107">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span> <span data-ttu-id="22c00-108">Externe communicatie van Power shell op basis van WS-Management wordt momenteel alleen ondersteund op het Windows-platform.</span><span class="sxs-lookup"><span data-stu-id="22c00-108">WS-Management based PowerShell remoting is currently supported only on Windows platform.</span></span>

<span data-ttu-id="22c00-109">Externe communicatie van Power shell is standaard ingeschakeld op Windows Server-platforms.</span><span class="sxs-lookup"><span data-stu-id="22c00-109">PowerShell remoting is enabled by default on Windows Server platforms.</span></span> <span data-ttu-id="22c00-110">U kunt gebruiken `Enable-PSRemoting` om externe communicatie van Power shell in te scha kelen op andere ondersteunde versies van Windows en externe toegang opnieuw in te scha kelen als deze wordt uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="22c00-110">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting if it becomes disabled.</span></span>

<span data-ttu-id="22c00-111">U hoeft deze opdracht slechts één keer uit te voeren op elke computer waarop opdrachten worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="22c00-111">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="22c00-112">U hoeft deze niet uit te voeren op computers die alleen opdrachten verzenden.</span><span class="sxs-lookup"><span data-stu-id="22c00-112">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="22c00-113">Omdat de configuratie listeners worden gestart om externe verbindingen te accepteren, is het verstandig om deze alleen uit te voeren als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="22c00-113">Because the configuration starts listeners to accept remote connections, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="22c00-114">Externe communicatie van Power shell inschakelen op client versies van Windows als de computer zich op een openbaar netwerk bevindt, wordt normaal gesp roken niet toegestaan, maar u kunt deze beperking overs laan met behulp van de para meter **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="22c00-114">Enabling PowerShell remoting on client versions of Windows when the computer is on a public network is normally disallowed, but you can skip this restriction by using the **SkipNetworkProfileCheck** parameter.</span></span> <span data-ttu-id="22c00-115">Zie de beschrijving van de para meter **SkipNetworkProfileCheck** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="22c00-115">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="22c00-116">Meerdere Power shell-installaties kunnen naast elkaar bestaan op één computer.</span><span class="sxs-lookup"><span data-stu-id="22c00-116">Multiple PowerShell installations can exist side-by-side on a single computer.</span></span> <span data-ttu-id="22c00-117">Als `Enable-PSRemoting` u uitvoert, wordt een extern eind punt geconfigureerd voor de specifieke installatie versie waarop u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="22c00-117">Running `Enable-PSRemoting` will configure a remoting endpoint for the specific installation version that you are running the cmdlet in.</span></span> <span data-ttu-id="22c00-118">Dus als u uitvoert `Enable-PSRemoting` tijdens het uitvoeren van Power shell 6,2, wordt een extern eind punt geconfigureerd dat Power shell 6,2 uitvoert.</span><span class="sxs-lookup"><span data-stu-id="22c00-118">So if you run `Enable-PSRemoting` while running PowerShell 6.2, a remoting endpoint will be configured that runs PowerShell 6.2.</span></span> <span data-ttu-id="22c00-119">Als u uitvoert `Enable-PSRemoting` tijdens het uitvoeren van Power shell 7-Preview, wordt een extern eind punt geconfigureerd dat Power shell 7-Preview uitvoert.</span><span class="sxs-lookup"><span data-stu-id="22c00-119">If you run `Enable-PSRemoting` while running PowerShell 7-preview, a remoting endpoint will be configured that runs PowerShell 7-preview.</span></span>

<span data-ttu-id="22c00-120">`Enable-PSRemoting` maakt twee externe eindpunt configuraties waar nodig.</span><span class="sxs-lookup"><span data-stu-id="22c00-120">`Enable-PSRemoting` creates two remoting endpoint configurations as needed.</span></span> <span data-ttu-id="22c00-121">Als de eindpunt configuraties al bestaan, kunnen ze gewoon worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="22c00-121">If the endpoint configurations already exist, then they are simply ensured to be enabled.</span></span> <span data-ttu-id="22c00-122">De gemaakte configuraties zijn identiek, maar hebben verschillende namen.</span><span class="sxs-lookup"><span data-stu-id="22c00-122">The created configurations are identical but have different names.</span></span> <span data-ttu-id="22c00-123">Een voor waarde is een eenvoudige naam die overeenkomt met de Power shell-versie die als host fungeert voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="22c00-123">One will have a simple name corresponding to the PowerShell version that hosts the session.</span></span> <span data-ttu-id="22c00-124">De andere configuratie naam bevat gedetailleerde informatie over de Power shell-versie die als host fungeert voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="22c00-124">The other configuration name contains more detailed information about the PowerShell version which hosts the session.</span></span> <span data-ttu-id="22c00-125">Bij uitvoering `Enable-PSRemoting` in Power shell 6,2 krijgt u bijvoorbeeld twee geconfigureerde eind punten met de naam **Power shell. 6**, **Power shell. 6.2.2**.</span><span class="sxs-lookup"><span data-stu-id="22c00-125">For example, when running `Enable-PSRemoting` in PowerShell 6.2, you will get two configured endpoints named **PowerShell.6**, **PowerShell.6.2.2**.</span></span>
<span data-ttu-id="22c00-126">Hierdoor kunt u een verbinding met de nieuwste versie van Power shell 6-host maken met behulp van de eenvoudige naam **Power shell. 6**.</span><span class="sxs-lookup"><span data-stu-id="22c00-126">This allows you to create a connection to the latest PowerShell 6 host version by using the simple name **PowerShell.6**.</span></span> <span data-ttu-id="22c00-127">U kunt ook verbinding maken met een specifieke versie van de Power shell-host met behulp van de meer naam **Power shell. 6.2.2**.</span><span class="sxs-lookup"><span data-stu-id="22c00-127">Or you can connect to a specific PowerShell host version by using the longer name **PowerShell.6.2.2**.</span></span>

<span data-ttu-id="22c00-128">Als u de nieuw ingeschakelde externe eind punten wilt gebruiken, moet u deze opgeven met de naam met de para meter **configuratiepad** bij het maken van een externe verbinding met behulp van de `Invoke-Command` `New-PSSession` `Enter-PSSession` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="22c00-128">To use the newly enabled remoting endpoints, you must specify them by name with the **ConfigurationName** parameter when creating a remote connection using the `Invoke-Command`,`New-PSSession`,`Enter-PSSession` cmdlets.</span></span> <span data-ttu-id="22c00-129">Zie voor beeld 4 voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="22c00-129">For more information, see Example 4.</span></span>

<span data-ttu-id="22c00-130">De `Enable-PSRemoting` cmdlet voert de volgende bewerkingen uit:</span><span class="sxs-lookup"><span data-stu-id="22c00-130">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="22c00-131">Voert de cmdlet [set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) uit, waarmee de volgende taken worden uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="22c00-131">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="22c00-132">De WinRM-service wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="22c00-132">Starts the WinRM service.</span></span>
  - <span data-ttu-id="22c00-133">Hiermee stelt u het opstart type van de WinRM-service in op automatisch.</span><span class="sxs-lookup"><span data-stu-id="22c00-133">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="22c00-134">Hiermee maakt u een listener voor het accepteren van aanvragen op een IP-adres.</span><span class="sxs-lookup"><span data-stu-id="22c00-134">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="22c00-135">Hiermee schakelt u een firewall-uitzonde ring voor WS-Management-communicatie.</span><span class="sxs-lookup"><span data-stu-id="22c00-135">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="22c00-136">Maakt zo nodig de eenvoudige en lange naam van de sessie-eindpunt configuraties.</span><span class="sxs-lookup"><span data-stu-id="22c00-136">Creates the simple and long name session endpoint configurations if needed.</span></span>
  - <span data-ttu-id="22c00-137">Hiermee schakelt u alle sessie configuraties in.</span><span class="sxs-lookup"><span data-stu-id="22c00-137">Enables all session configurations.</span></span>
  - <span data-ttu-id="22c00-138">Hiermee wijzigt u de security descriptor van alle sessie configuraties om externe toegang toe te staan.</span><span class="sxs-lookup"><span data-stu-id="22c00-138">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="22c00-139">De WinRM-service wordt opnieuw gestart om de voor gaande wijzigingen van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="22c00-139">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="22c00-140">Als u deze cmdlet wilt uitvoeren op het Windows-platform, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="22c00-140">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="22c00-141">Deze cmdlet is niet beschikbaar in Linux-of MacOS-versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="22c00-141">This cmdlet is not available on Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="22c00-142">Deze cmdlet heeft geen invloed op externe eindpunt configuraties die zijn gemaakt door Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="22c00-142">This cmdlet does not affect remote endpoint configurations created by Windows PowerShell.</span></span>
> <span data-ttu-id="22c00-143">Dit geldt alleen voor eind punten die zijn gemaakt met Power shell versie 6 en hoger.</span><span class="sxs-lookup"><span data-stu-id="22c00-143">It only affects endpoints created with PowerShell version 6 and greater.</span></span> <span data-ttu-id="22c00-144">Als u externe Power shell-eind punten die worden gehost door Windows Power shell wilt in-en uitschakelen, voert u de `Enable-PSRemoting` cmdlet uit vanuit een Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="22c00-144">To enable and disable PowerShell remoting endpoints that are hosted by Windows PowerShell, run the `Enable-PSRemoting` cmdlet from within a Windows PowerShell session.</span></span>

## <span data-ttu-id="22c00-145">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="22c00-145">EXAMPLES</span></span>

### <span data-ttu-id="22c00-146">Voor beeld 1: een computer configureren voor het ontvangen van externe opdrachten</span><span class="sxs-lookup"><span data-stu-id="22c00-146">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="22c00-147">Met deze opdracht wordt de computer zo geconfigureerd dat externe opdrachten worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="22c00-147">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="22c00-148">Voor beeld 2: een computer configureren voor het ontvangen van externe opdrachten zonder een bevestigings prompt</span><span class="sxs-lookup"><span data-stu-id="22c00-148">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="22c00-149">Met deze opdracht wordt de computer zo geconfigureerd dat externe opdrachten worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="22c00-149">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="22c00-150">De para meter **Force** onderdrukt de gebruikers prompts.</span><span class="sxs-lookup"><span data-stu-id="22c00-150">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="22c00-151">Voor beeld 3: externe toegang op clients toestaan</span><span class="sxs-lookup"><span data-stu-id="22c00-151">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="22c00-152">In dit voor beeld ziet u hoe u externe toegang toestaat vanuit open bare netwerken op client versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="22c00-152">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="22c00-153">De naam van de firewall regel kan verschillend zijn voor verschillende versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="22c00-153">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="22c00-154">Gebruiken `Get-NetFirewallRule` om een lijst met regels weer te geven.</span><span class="sxs-lookup"><span data-stu-id="22c00-154">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="22c00-155">Voordat u de firewall regel inschakelt, bekijkt u de beveiligings instellingen in de regel om te controleren of de configuratie geschikt is voor uw omgeving.</span><span class="sxs-lookup"><span data-stu-id="22c00-155">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

<span data-ttu-id="22c00-156">`Enable-PSRemoting`Maakt standaard netwerk regels die externe toegang vanaf particuliere en domein netwerken toestaan.</span><span class="sxs-lookup"><span data-stu-id="22c00-156">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="22c00-157">De opdracht gebruikt de para meter **SkipNetworkProfileCheck** om externe toegang vanaf open bare netwerken in hetzelfde lokale subnet toe te staan.</span><span class="sxs-lookup"><span data-stu-id="22c00-157">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="22c00-158">De opdracht geeft de para meter **Force** om bevestigings berichten te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="22c00-158">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="22c00-159">De para meter **SkipNetworkProfileCheck** heeft geen invloed op Server versies van het Windows-besturings systeem, waardoor externe toegang vanaf open bare netwerken in hetzelfde lokale subnet standaard is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="22c00-159">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="22c00-160">De `Set-NetFirewallRule` cmdlet in de module **netsecurity** voegt een firewall regel toe die externe toegang vanaf open bare netwerken vanaf elke externe locatie toestaat.</span><span class="sxs-lookup"><span data-stu-id="22c00-160">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="22c00-161">Dit omvat locaties in verschillende subnetten.</span><span class="sxs-lookup"><span data-stu-id="22c00-161">This includes locations in different subnets.</span></span>

### <span data-ttu-id="22c00-162">Voor beeld 4: een externe sessie maken naar de nieuwe ingeschakelde eindpunt configuratie</span><span class="sxs-lookup"><span data-stu-id="22c00-162">Example 4: Create a remote session to the newly enabled endpoint configuration</span></span>

<span data-ttu-id="22c00-163">In dit voor beeld ziet u hoe u externe communicatie van Power shell op een computer inschakelt, de geconfigureerde eindpunt namen zoekt en een externe sessie maakt naar een van de eind punten.</span><span class="sxs-lookup"><span data-stu-id="22c00-163">This example shows how to enable PowerShell remoting on a computer, find the configured endpoint names, and create a remote session to one of the endpoints.</span></span>

<span data-ttu-id="22c00-164">Met de eerste opdracht wordt externe communicatie met Power shell op de computer ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="22c00-164">The first command enables PowerShell remoting on the computer.</span></span>

<span data-ttu-id="22c00-165">Met de tweede opdracht worden de eindpunt configuraties weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="22c00-165">The second command lists the endpoint configurations.</span></span>

<span data-ttu-id="22c00-166">Met de derde opdracht maakt u een externe Power shell-sessie op dezelfde computer, waarbij u de **Power shell. 6** -eind punt op naam opgeeft.</span><span class="sxs-lookup"><span data-stu-id="22c00-166">The third command creates a remote PowerShell session to the same machine, specifying the **PowerShell.6** endpoint by name.</span></span> <span data-ttu-id="22c00-167">De externe sessie wordt gehost met de nieuwste versie van Power shell 6 (6.2.2).</span><span class="sxs-lookup"><span data-stu-id="22c00-167">The remote session will be hosted with the latest PowerShell 6 version (6.2.2).</span></span>

<span data-ttu-id="22c00-168">Met de laatste opdracht wordt de `$PSVersionTable` variabele in de externe sessie geopend om de Power shell-versie weer te geven die als host fungeert voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="22c00-168">The last command accesses the `$PSVersionTable` variable in the remote session to display the PowerShell version that is hosting the session.</span></span>

```powershell
Enable-PSRemoting -Force

Get-PSSessionConfiguration

$session = New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6

Invoke-Command -Session $session -ScriptBlock { $PSVersionTable }
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name                           Value
----                           -----
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
PSEdition                      Core
PSRemotingProtocolVersion      2.3
Platform                       Win32NT
SerializationVersion           1.1.0.1
GitCommitId                    6.2.2
WSManStackVersion              3.0
PSVersion                      6.2.2
OS                             Microsoft Windows 10.0.18363
```

> [!NOTE]
> <span data-ttu-id="22c00-169">De naam van de firewall regel kan verschillen, afhankelijk van de versie van Windows.</span><span class="sxs-lookup"><span data-stu-id="22c00-169">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="22c00-170">Gebruik de `Get-NetFirewallRule` cmdlet om de namen van de regels op uw systeem weer te geven.</span><span class="sxs-lookup"><span data-stu-id="22c00-170">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="22c00-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="22c00-171">PARAMETERS</span></span>

### <span data-ttu-id="22c00-172">-Confirm</span><span class="sxs-lookup"><span data-stu-id="22c00-172">-Confirm</span></span>

<span data-ttu-id="22c00-173">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="22c00-173">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="22c00-174">-Force</span><span class="sxs-lookup"><span data-stu-id="22c00-174">-Force</span></span>

<span data-ttu-id="22c00-175">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="22c00-175">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="22c00-176">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="22c00-176">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="22c00-177">Geeft aan dat met deze cmdlet externe toegang wordt ingeschakeld op client versies van het Windows-besturings systeem wanneer de computer zich op een openbaar netwerk bevindt.</span><span class="sxs-lookup"><span data-stu-id="22c00-177">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="22c00-178">Met deze para meter wordt een firewall regel ingeschakeld voor open bare netwerken die alleen externe toegang toestaan vanaf computers in hetzelfde lokale subnet.</span><span class="sxs-lookup"><span data-stu-id="22c00-178">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="22c00-179">Deze para meter heeft geen invloed op Server versies van het Windows-besturings systeem, die standaard een lokale subnet-firewall regel voor open bare netwerken hebben.</span><span class="sxs-lookup"><span data-stu-id="22c00-179">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="22c00-180">Als de firewall regel van het lokale subnet is uitgeschakeld op een server versie, `Enable-PSRemoting` schakelt u deze opnieuw in, ongeacht de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="22c00-180">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="22c00-181">Als u de beperkingen voor lokale subnetten wilt verwijderen en externe toegang vanaf alle locaties op open bare netwerken wilt inschakelen, gebruikt u de `Set-NetFirewallRule` cmdlet in de module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="22c00-181">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="22c00-182">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="22c00-182">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="22c00-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="22c00-183">-WhatIf</span></span>

<span data-ttu-id="22c00-184">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="22c00-184">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="22c00-185">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="22c00-185">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="22c00-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="22c00-186">CommonParameters</span></span>

<span data-ttu-id="22c00-187">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="22c00-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="22c00-188">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="22c00-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="22c00-189">INVOER</span><span class="sxs-lookup"><span data-stu-id="22c00-189">INPUTS</span></span>

### <span data-ttu-id="22c00-190">Geen</span><span class="sxs-lookup"><span data-stu-id="22c00-190">None</span></span>

<span data-ttu-id="22c00-191">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22c00-191">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="22c00-192">UITVOER</span><span class="sxs-lookup"><span data-stu-id="22c00-192">OUTPUTS</span></span>

### <span data-ttu-id="22c00-193">System. String</span><span class="sxs-lookup"><span data-stu-id="22c00-193">System.String</span></span>

<span data-ttu-id="22c00-194">Deze cmdlet retourneert teken reeksen die de resultaten beschrijven.</span><span class="sxs-lookup"><span data-stu-id="22c00-194">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="22c00-195">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="22c00-195">NOTES</span></span>

<span data-ttu-id="22c00-196">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="22c00-196">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="22c00-197">Op Server versies van het Windows-besturings systeem `Enable-PSRemoting` maakt u firewall regels voor privé-en domein netwerken die externe toegang toestaan en maakt u een firewall regel voor open bare netwerken die alleen externe toegang vanaf computers in hetzelfde lokale subnet mogelijk maken.</span><span class="sxs-lookup"><span data-stu-id="22c00-197">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="22c00-198">Op client versies van het Windows-besturings systeem `Enable-PSRemoting` maakt firewall regels voor particuliere en domein netwerken die onbeperkte externe toegang toestaan.</span><span class="sxs-lookup"><span data-stu-id="22c00-198">On client versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="22c00-199">Als u een firewall regel wilt maken voor open bare netwerken die externe toegang tot hetzelfde lokale subnet toestaan, gebruikt u de para meter **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="22c00-199">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="22c00-200">Op client-of server versies van het Windows-besturings systeem, om een firewall regel te maken voor open bare netwerken die de lokale subnet-beperking verwijderen en externe toegang toestaan, gebruikt u de `Set-NetFirewallRule` cmdlet in de module netsecurity om de volgende opdracht uit te voeren: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="22c00-200">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="22c00-201">`Enable-PSRemoting` Hiermee schakelt u alle sessie configuraties in door de waarde van de eigenschap **ingeschakeld** van alle sessie configuraties in te stellen op `$True` .</span><span class="sxs-lookup"><span data-stu-id="22c00-201">`Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="22c00-202">`Enable-PSRemoting` Hiermee verwijdert u de instellingen voor **Deny_All** en **Network_Deny_All** .</span><span class="sxs-lookup"><span data-stu-id="22c00-202">`Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="22c00-203">Dit biedt externe toegang tot sessie configuraties die zijn gereserveerd voor lokaal gebruik.</span><span class="sxs-lookup"><span data-stu-id="22c00-203">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="22c00-204">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="22c00-204">RELATED LINKS</span></span>

[<span data-ttu-id="22c00-205">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="22c00-205">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="22c00-206">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="22c00-206">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="22c00-207">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="22c00-207">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="22c00-208">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="22c00-208">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="22c00-209">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="22c00-209">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="22c00-210">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="22c00-210">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="22c00-211">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="22c00-211">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="22c00-212">about_Remote</span><span class="sxs-lookup"><span data-stu-id="22c00-212">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="22c00-213">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="22c00-213">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)
