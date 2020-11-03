---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 0c8c386ab376afde3d15fcd29b3f653b3f738f63
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2020
ms.locfileid: "93251443"
---
# <span data-ttu-id="368df-103">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="368df-103">Enable-PSRemoting</span></span>

## <span data-ttu-id="368df-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="368df-104">SYNOPSIS</span></span>
<span data-ttu-id="368df-105">Hiermee configureert u de computer voor het ontvangen van externe opdrachten.</span><span class="sxs-lookup"><span data-stu-id="368df-105">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="368df-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="368df-106">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="368df-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="368df-107">DESCRIPTION</span></span>

<span data-ttu-id="368df-108">`Enable-PSRemoting`Met de cmdlet wordt de computer geconfigureerd om externe Power shell-opdrachten te ontvangen die worden verzonden met behulp van de WS-Management technologie.</span><span class="sxs-lookup"><span data-stu-id="368df-108">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span>

<span data-ttu-id="368df-109">Externe communicatie van Power shell is standaard ingeschakeld op Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="368df-109">PowerShell remoting is enabled by default on Windows Server 2012.</span></span> <span data-ttu-id="368df-110">U kunt gebruiken `Enable-PSRemoting` om externe communicatie van Power shell in te scha kelen op andere ondersteunde versies van Windows en externe toegang opnieuw in te scha kelen op Windows Server 2012 als deze functie wordt uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="368df-110">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting on Windows Server 2012 if it becomes disabled.</span></span>

<span data-ttu-id="368df-111">U hoeft deze opdracht slechts één keer uit te voeren op elke computer waarop opdrachten worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="368df-111">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="368df-112">U hoeft deze niet uit te voeren op computers die alleen opdrachten verzenden.</span><span class="sxs-lookup"><span data-stu-id="368df-112">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="368df-113">Omdat de configuratie listeners start, is het voorzichtig om deze alleen uit te voeren als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="368df-113">Because the configuration starts listeners, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="368df-114">Vanaf Power Shell 3,0 kan de `Enable-PSRemoting` cmdlet Power shell-externe toegang inschakelen op client versies van Windows wanneer de computer zich in een openbaar netwerk bevindt.</span><span class="sxs-lookup"><span data-stu-id="368df-114">Beginning in PowerShell 3.0, the `Enable-PSRemoting` cmdlet can enable PowerShell remoting on client versions of Windows when the computer is on a public network.</span></span> <span data-ttu-id="368df-115">Zie de beschrijving van de para meter **SkipNetworkProfileCheck** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="368df-115">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="368df-116">De `Enable-PSRemoting` cmdlet voert de volgende bewerkingen uit:</span><span class="sxs-lookup"><span data-stu-id="368df-116">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="368df-117">Voert de cmdlet [set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) uit, waarmee de volgende taken worden uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="368df-117">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="368df-118">De WinRM-service wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="368df-118">Starts the WinRM service.</span></span>
  - <span data-ttu-id="368df-119">Hiermee stelt u het opstart type van de WinRM-service in op automatisch.</span><span class="sxs-lookup"><span data-stu-id="368df-119">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="368df-120">Hiermee maakt u een listener voor het accepteren van aanvragen op een IP-adres.</span><span class="sxs-lookup"><span data-stu-id="368df-120">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="368df-121">Hiermee schakelt u een firewall-uitzonde ring voor WS-Management-communicatie.</span><span class="sxs-lookup"><span data-stu-id="368df-121">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="368df-122">Registreert de **micro soft. Power shell** en **micro soft. Power shell. werk stroom** sessie configuraties, als deze nog niet zijn geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="368df-122">Registers the **Microsoft.PowerShell** and **Microsoft.PowerShell.Workflow** session configurations, if it they are not already registered.</span></span>
  - <span data-ttu-id="368df-123">Registreert de **micro soft. PowerShell32** -sessie configuratie op 64-bits computers, als deze nog niet is geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="368df-123">Registers the **Microsoft.PowerShell32** session configuration on 64-bit computers, if it is not already registered.</span></span>
  - <span data-ttu-id="368df-124">Hiermee schakelt u alle sessie configuraties in.</span><span class="sxs-lookup"><span data-stu-id="368df-124">Enables all session configurations.</span></span>
  - <span data-ttu-id="368df-125">Hiermee wijzigt u de security descriptor van alle sessie configuraties om externe toegang toe te staan.</span><span class="sxs-lookup"><span data-stu-id="368df-125">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="368df-126">De WinRM-service wordt opnieuw gestart om de voor gaande wijzigingen van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="368df-126">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="368df-127">Als u deze cmdlet wilt uitvoeren op het Windows-platform, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="368df-127">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="368df-128">Dit geldt niet voor Linux-of MacOS-versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="368df-128">This does not apply to Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="368df-129">Gebruik Power Shell 2,0 niet voor het uitvoeren van de cmdlets op systemen met Power Shell 3,0 en Power Shell 2,0 `Enable-PSRemoting` `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="368df-129">On systems that have both PowerShell 3.0 and PowerShell 2.0, do not use PowerShell 2.0 to run the `Enable-PSRemoting` and `Disable-PSRemoting` cmdlets.</span></span> <span data-ttu-id="368df-130">De opdrachten kunnen lijken te slagen, maar externe communicatie is niet juist geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="368df-130">The commands might appear to succeed, but the remoting is not configured correctly.</span></span> <span data-ttu-id="368df-131">Externe opdrachten en latere pogingen om externe toegang in te scha kelen en uit te scha kelen, mislukken waarschijnlijk.</span><span class="sxs-lookup"><span data-stu-id="368df-131">Remote commands and later attempts to enable and disable remoting, are likely to fail.</span></span>

## <span data-ttu-id="368df-132">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="368df-132">EXAMPLES</span></span>

### <span data-ttu-id="368df-133">Voor beeld 1: een computer configureren voor het ontvangen van externe opdrachten</span><span class="sxs-lookup"><span data-stu-id="368df-133">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="368df-134">Met deze opdracht wordt de computer zo geconfigureerd dat externe opdrachten worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="368df-134">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

### <span data-ttu-id="368df-135">Voor beeld 2: een computer configureren voor het ontvangen van externe opdrachten zonder een bevestigings prompt</span><span class="sxs-lookup"><span data-stu-id="368df-135">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="368df-136">Met deze opdracht wordt de computer zo geconfigureerd dat externe opdrachten worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="368df-136">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="368df-137">De para meter **Force** onderdrukt de gebruikers prompts.</span><span class="sxs-lookup"><span data-stu-id="368df-137">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

### <span data-ttu-id="368df-138">Voor beeld 3: externe toegang op clients toestaan</span><span class="sxs-lookup"><span data-stu-id="368df-138">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="368df-139">In dit voor beeld ziet u hoe u externe toegang toestaat vanuit open bare netwerken op client versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="368df-139">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="368df-140">De naam van de firewall regel kan verschillend zijn voor verschillende versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="368df-140">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="368df-141">Gebruiken `Get-NetFirewallRule` om een lijst met regels weer te geven.</span><span class="sxs-lookup"><span data-stu-id="368df-141">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="368df-142">Voordat u de firewall regel inschakelt, bekijkt u de beveiligings instellingen in de regel om te controleren of de configuratie geschikt is voor uw omgeving.</span><span class="sxs-lookup"><span data-stu-id="368df-142">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

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

<span data-ttu-id="368df-143">`Enable-PSRemoting`Maakt standaard netwerk regels die externe toegang vanaf particuliere en domein netwerken toestaan.</span><span class="sxs-lookup"><span data-stu-id="368df-143">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="368df-144">De opdracht gebruikt de para meter **SkipNetworkProfileCheck** om externe toegang vanaf open bare netwerken in hetzelfde lokale subnet toe te staan.</span><span class="sxs-lookup"><span data-stu-id="368df-144">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="368df-145">De opdracht geeft de para meter **Force** om bevestigings berichten te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="368df-145">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="368df-146">De para meter **SkipNetworkProfileCheck** heeft geen invloed op Server versies van het Windows-besturings systeem, waardoor externe toegang vanaf open bare netwerken in hetzelfde lokale subnet standaard is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="368df-146">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="368df-147">De `Set-NetFirewallRule` cmdlet in de module **netsecurity** voegt een firewall regel toe die externe toegang vanaf open bare netwerken vanaf elke externe locatie toestaat.</span><span class="sxs-lookup"><span data-stu-id="368df-147">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="368df-148">Dit omvat locaties in verschillende subnetten.</span><span class="sxs-lookup"><span data-stu-id="368df-148">This includes locations in different subnets.</span></span>

> [!NOTE]
> <span data-ttu-id="368df-149">De naam van de firewall regel kan verschillen, afhankelijk van de versie van Windows.</span><span class="sxs-lookup"><span data-stu-id="368df-149">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="368df-150">Gebruik de `Get-NetFirewallRule` cmdlet om de namen van de regels op uw systeem weer te geven.</span><span class="sxs-lookup"><span data-stu-id="368df-150">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="368df-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="368df-151">PARAMETERS</span></span>

### <span data-ttu-id="368df-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="368df-152">-Confirm</span></span>

<span data-ttu-id="368df-153">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="368df-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="368df-154">-Force</span><span class="sxs-lookup"><span data-stu-id="368df-154">-Force</span></span>

<span data-ttu-id="368df-155">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="368df-155">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="368df-156">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="368df-156">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="368df-157">Geeft aan dat met deze cmdlet externe toegang wordt ingeschakeld op client versies van het Windows-besturings systeem wanneer de computer zich op een openbaar netwerk bevindt.</span><span class="sxs-lookup"><span data-stu-id="368df-157">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="368df-158">Met deze para meter wordt een firewall regel ingeschakeld voor open bare netwerken die alleen externe toegang toestaan vanaf computers in hetzelfde lokale subnet.</span><span class="sxs-lookup"><span data-stu-id="368df-158">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="368df-159">Deze para meter heeft geen invloed op Server versies van het Windows-besturings systeem, die standaard een lokale subnet-firewall regel voor open bare netwerken hebben.</span><span class="sxs-lookup"><span data-stu-id="368df-159">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="368df-160">Als de firewall regel van het lokale subnet is uitgeschakeld op een server versie, `Enable-PSRemoting` schakelt u deze opnieuw in, ongeacht de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="368df-160">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="368df-161">Als u de beperkingen voor lokale subnetten wilt verwijderen en externe toegang vanaf alle locaties op open bare netwerken wilt inschakelen, gebruikt u de `Set-NetFirewallRule` cmdlet in de module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="368df-161">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="368df-162">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="368df-162">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="368df-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="368df-163">-WhatIf</span></span>

<span data-ttu-id="368df-164">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="368df-164">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="368df-165">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="368df-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="368df-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="368df-166">CommonParameters</span></span>

<span data-ttu-id="368df-167">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="368df-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="368df-168">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="368df-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="368df-169">INVOER</span><span class="sxs-lookup"><span data-stu-id="368df-169">INPUTS</span></span>

### <span data-ttu-id="368df-170">Geen</span><span class="sxs-lookup"><span data-stu-id="368df-170">None</span></span>

<span data-ttu-id="368df-171">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="368df-171">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="368df-172">UITVOER</span><span class="sxs-lookup"><span data-stu-id="368df-172">OUTPUTS</span></span>

### <span data-ttu-id="368df-173">System. String</span><span class="sxs-lookup"><span data-stu-id="368df-173">System.String</span></span>

<span data-ttu-id="368df-174">Deze cmdlet retourneert teken reeksen die de resultaten beschrijven.</span><span class="sxs-lookup"><span data-stu-id="368df-174">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="368df-175">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="368df-175">NOTES</span></span>

<span data-ttu-id="368df-176">In Power Shell 3,0 `Enable-PSRemoting` maakt u de volgende firewall-uitzonde ringen voor WS-Management-communicatie.</span><span class="sxs-lookup"><span data-stu-id="368df-176">In PowerShell 3.0, `Enable-PSRemoting` creates the following firewall exceptions for WS-Management communications.</span></span>

<span data-ttu-id="368df-177">Op Server versies van het Windows-besturings systeem `Enable-PSRemoting` maakt u firewall regels voor privé-en domein netwerken die externe toegang toestaan en maakt u een firewall regel voor open bare netwerken die alleen externe toegang vanaf computers in hetzelfde lokale subnet mogelijk maken.</span><span class="sxs-lookup"><span data-stu-id="368df-177">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="368df-178">Op client versies van het Windows-besturings systeem `Enable-PSRemoting` maakt Power shell 3,0 firewall regels voor particuliere en domein netwerken die onbeperkte externe toegang toestaan.</span><span class="sxs-lookup"><span data-stu-id="368df-178">On client versions of the Windows operating system, `Enable-PSRemoting` in PowerShell 3.0 creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="368df-179">Als u een firewall regel wilt maken voor open bare netwerken die externe toegang tot hetzelfde lokale subnet toestaan, gebruikt u de para meter **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="368df-179">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="368df-180">Op client-of server versies van het Windows-besturings systeem, om een firewall regel te maken voor open bare netwerken die de lokale subnet-beperking verwijderen en externe toegang toestaan, gebruikt u de `Set-NetFirewallRule` cmdlet in de module netsecurity om de volgende opdracht uit te voeren: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="368df-180">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="368df-181">In Power Shell 2,0 `Enable-PSRemoting` maakt u de volgende firewall-uitzonde ringen voor WS-Management-communicatie.</span><span class="sxs-lookup"><span data-stu-id="368df-181">In PowerShell 2.0, `Enable-PSRemoting` creates the following firewall exceptions for WS-Management communications.</span></span>

<span data-ttu-id="368df-182">Op Server versies van het Windows-besturings systeem maakt de firewall regels voor alle netwerken die externe toegang toestaan.</span><span class="sxs-lookup"><span data-stu-id="368df-182">On server versions of the Windows operating system, it creates firewall rules for all networks that allow remote access.</span></span>

<span data-ttu-id="368df-183">Op client versies van het Windows-besturings systeem `Enable-PSRemoting` maakt Power shell 2,0 een firewall uitzondering alleen voor locaties van domein en particulier netwerk.</span><span class="sxs-lookup"><span data-stu-id="368df-183">On client versions of the Windows operating system, `Enable-PSRemoting` in PowerShell 2.0 creates a firewall exception only for domain and private network locations.</span></span> <span data-ttu-id="368df-184">Voor het minimaliseren van beveiligings Risico's `Enable-PSRemoting` maakt geen firewall regel voor open bare netwerken op client versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="368df-184">To minimize security risks, `Enable-PSRemoting` does not create a firewall rule for public networks on client versions of Windows.</span></span> <span data-ttu-id="368df-185">Wanneer de huidige netwerk locatie openbaar is, `Enable-PSRemoting` wordt het volgende bericht weer gegeven: kan de status van de firewall niet controleren.</span><span class="sxs-lookup"><span data-stu-id="368df-185">When the current network location is public, `Enable-PSRemoting` returns the following message: Unable to check the status of the firewall.</span></span>

<span data-ttu-id="368df-186">Vanaf Power Shell 3,0 worden `Enable-PSRemoting` alle sessie configuraties ingeschakeld door de waarde van de eigenschap **enabled** van alle sessie configuraties in te stellen op `$True` .</span><span class="sxs-lookup"><span data-stu-id="368df-186">Starting in PowerShell 3.0, `Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="368df-187">In Power Shell 2,0 `Enable-PSRemoting` wordt de instelling **Deny_All** verwijderd uit de security descriptor van de sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="368df-187">In PowerShell 2.0, `Enable-PSRemoting` removes the **Deny_All** setting from the security descriptor of session configurations.</span></span> <span data-ttu-id="368df-188">In Power Shell 3,0 `Enable-PSRemoting` verwijdert u de instellingen **Deny_All** en **Network_Deny_All** .</span><span class="sxs-lookup"><span data-stu-id="368df-188">In PowerShell 3.0, `Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="368df-189">Dit biedt externe toegang tot sessie configuraties die zijn gereserveerd voor lokaal gebruik.</span><span class="sxs-lookup"><span data-stu-id="368df-189">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="368df-190">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="368df-190">RELATED LINKS</span></span>

[<span data-ttu-id="368df-191">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="368df-191">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="368df-192">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="368df-192">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="368df-193">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="368df-193">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="368df-194">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="368df-194">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="368df-195">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="368df-195">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="368df-196">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="368df-196">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="368df-197">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="368df-197">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="368df-198">about_Remote</span><span class="sxs-lookup"><span data-stu-id="368df-198">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="368df-199">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="368df-199">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)
