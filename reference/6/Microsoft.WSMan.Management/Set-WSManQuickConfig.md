---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e8bc5bc248eafe479f366397aa947845e94e190c
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/01/2020
ms.locfileid: "93251891"
---
# <span data-ttu-id="9166f-103">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="9166f-103">Set-WSManQuickConfig</span></span>

## <span data-ttu-id="9166f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9166f-104">SYNOPSIS</span></span>
<span data-ttu-id="9166f-105">Hiermee configureert u de lokale computer voor extern beheer.</span><span class="sxs-lookup"><span data-stu-id="9166f-105">Configures the local computer for remote management.</span></span>

## <span data-ttu-id="9166f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9166f-106">SYNTAX</span></span>

### <span data-ttu-id="9166f-107">Alles</span><span class="sxs-lookup"><span data-stu-id="9166f-107">All</span></span>

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## <span data-ttu-id="9166f-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9166f-108">DESCRIPTION</span></span>

<span data-ttu-id="9166f-109">`Set-WSManQuickConfig`Met de cmdlet wordt de computer geconfigureerd om externe Power shell-opdrachten te ontvangen die worden verzonden met behulp van de technologie van webservices voor beheer (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="9166f-109">The `Set-WSManQuickConfig` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the Web Services for Management (WS-Management) technology.</span></span>

<span data-ttu-id="9166f-110">`Set-WSManQuickConfig` voert de volgende acties uit:</span><span class="sxs-lookup"><span data-stu-id="9166f-110">`Set-WSManQuickConfig` performs the following actions:</span></span>

- <span data-ttu-id="9166f-111">Controleert of de WinRM-service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9166f-111">Checks whether the WinRM service is running.</span></span> <span data-ttu-id="9166f-112">Als de WinRM-service niet wordt uitgevoerd, wordt de service gestart.</span><span class="sxs-lookup"><span data-stu-id="9166f-112">If the WinRM service isn't running, the service is started.</span></span>
- <span data-ttu-id="9166f-113">Hiermee stelt u het opstart type voor de WinRM-service in op automatisch.</span><span class="sxs-lookup"><span data-stu-id="9166f-113">Sets the WinRM service startup type to automatic.</span></span>
- <span data-ttu-id="9166f-114">Hiermee maakt u een listener voor het accepteren van aanvragen op een IP-adres.</span><span class="sxs-lookup"><span data-stu-id="9166f-114">Creates a listener to accept requests on any IP address.</span></span> <span data-ttu-id="9166f-115">Het standaard transport is **http**.</span><span class="sxs-lookup"><span data-stu-id="9166f-115">The default transport is **HTTP**.</span></span>
- <span data-ttu-id="9166f-116">Hiermee schakelt u een firewall-uitzonde ring voor WinRM-verkeer.</span><span class="sxs-lookup"><span data-stu-id="9166f-116">Enables a firewall exception for WinRM traffic.</span></span>

<span data-ttu-id="9166f-117">`Set-WSManQuickConfig`Start Power shell met de optie **als administrator uitvoeren** om het programma uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9166f-117">To run `Set-WSManQuickConfig`, start PowerShell with the **Run as Administrator** option.</span></span>

## <span data-ttu-id="9166f-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9166f-118">EXAMPLES</span></span>

### <span data-ttu-id="9166f-119">Voor beeld 1: extern beheer van de lokale computer via HTTP inschakelen</span><span class="sxs-lookup"><span data-stu-id="9166f-119">Example 1: Enable remote management of the local computer over HTTP</span></span>

<span data-ttu-id="9166f-120">In dit voor beeld wordt de vereiste configuratie ingesteld om extern beheer van de lokale computer in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="9166f-120">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="9166f-121">Met deze opdracht maakt u standaard een WS-Management listener op **http**.</span><span class="sxs-lookup"><span data-stu-id="9166f-121">By default, this command creates a WS-Management listener on **HTTP**.</span></span>

```powershell
Set-WSManQuickConfig
```

### <span data-ttu-id="9166f-122">Voor beeld 2: extern beheer van de lokale computer via HTTPS inschakelen</span><span class="sxs-lookup"><span data-stu-id="9166f-122">Example 2: Enable remote management of the local computer over HTTPS</span></span>

<span data-ttu-id="9166f-123">In dit voor beeld wordt de vereiste configuratie ingesteld om extern beheer van de lokale computer in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="9166f-123">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="9166f-124">De para meter **UseSSL** geeft aan dat **https** wordt gebruikt om te communiceren met de computer.</span><span class="sxs-lookup"><span data-stu-id="9166f-124">The **UseSSL** parameter specifies that **HTTPS** is used to communicate with the computer.</span></span>

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> <span data-ttu-id="9166f-125">**Https** vereist hand matige configuratie.</span><span class="sxs-lookup"><span data-stu-id="9166f-125">**HTTPS** requires manual configuration.</span></span> <span data-ttu-id="9166f-126">Zie de beschrijving van de para meter **UseSSL** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9166f-126">For more information, see the **UseSSL** parameter's description.</span></span>

## <span data-ttu-id="9166f-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9166f-127">PARAMETERS</span></span>

### <span data-ttu-id="9166f-128">-Force</span><span class="sxs-lookup"><span data-stu-id="9166f-128">-Force</span></span>

<span data-ttu-id="9166f-129">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="9166f-129">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9166f-130">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="9166f-130">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="9166f-131">Hiermee configureert u Windows-client versies voor externe toegang wanneer de computer zich op een openbaar netwerk bevindt.</span><span class="sxs-lookup"><span data-stu-id="9166f-131">Configures Windows client versions for remoting when the computer is on a public network.</span></span> <span data-ttu-id="9166f-132">Met deze para meter wordt een firewall regel ingeschakeld voor open bare netwerken die alleen externe toegang toestaan vanaf computers in hetzelfde lokale subnet.</span><span class="sxs-lookup"><span data-stu-id="9166f-132">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="9166f-133">Deze para meter heeft geen invloed op Server versies van Windows, die standaard een lokale subnet-firewall regel voor open bare netwerken hebben.</span><span class="sxs-lookup"><span data-stu-id="9166f-133">This parameter has no effect on server versions of Windows, that by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="9166f-134">Als de firewall regel van het lokale subnet is uitgeschakeld op de server versie van Windows, `Enable-PSRemoting` schakelt u deze opnieuw in, ongeacht de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="9166f-134">If the local subnet firewall rule is disabled on the server version of Windows, `Enable-PSRemoting` re-enables it, regardless of this parameter's value.</span></span>

<span data-ttu-id="9166f-135">Als u de beperkingen voor lokale subnetten wilt verwijderen en externe toegang vanaf alle locaties op open bare netwerken wilt inschakelen, gebruikt u de `Set-NetFirewallRule` cmdlet in de module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="9166f-135">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="9166f-136">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9166f-136">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9166f-137">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="9166f-137">-UseSSL</span></span>

<span data-ttu-id="9166f-138">Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) wordt gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="9166f-138">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span> <span data-ttu-id="9166f-139">SSL wordt standaard niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9166f-139">By default, SSL isn't used.</span></span>

<span data-ttu-id="9166f-140">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="9166f-140">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="9166f-141">Met de para meter **UseSSL** kunt u de extra beveiliging van https in plaats van http opgeven.</span><span class="sxs-lookup"><span data-stu-id="9166f-141">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="9166f-142">Als u deze para meter gebruikt en SSL niet beschikbaar is op de poort die wordt gebruikt voor de verbinding, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="9166f-142">If you use this parameter and SSL isn't available on the port that's used for the connection, the command fails.</span></span>

<span data-ttu-id="9166f-143">**Https** vereist hand matige configuratie van WinRM-en firewall regels.</span><span class="sxs-lookup"><span data-stu-id="9166f-143">**HTTPS** requires manual configuration of WinRM and firewall rules.</span></span> <span data-ttu-id="9166f-144">Zie [How to: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9166f-144">For more information, see [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9166f-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9166f-145">CommonParameters</span></span>

<span data-ttu-id="9166f-146">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9166f-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9166f-147">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9166f-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9166f-148">INVOER</span><span class="sxs-lookup"><span data-stu-id="9166f-148">INPUTS</span></span>

### <span data-ttu-id="9166f-149">Geen</span><span class="sxs-lookup"><span data-stu-id="9166f-149">None</span></span>

<span data-ttu-id="9166f-150">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="9166f-150">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="9166f-151">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9166f-151">OUTPUTS</span></span>

### <span data-ttu-id="9166f-152">Geen</span><span class="sxs-lookup"><span data-stu-id="9166f-152">None</span></span>

<span data-ttu-id="9166f-153">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9166f-153">This cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="9166f-154">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9166f-154">NOTES</span></span>

## <span data-ttu-id="9166f-155">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9166f-155">RELATED LINKS</span></span>

[<span data-ttu-id="9166f-156">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="9166f-156">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="9166f-157">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="9166f-157">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="9166f-158">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="9166f-158">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="9166f-159">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="9166f-159">Enable-PSRemoting</span></span>](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[<span data-ttu-id="9166f-160">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="9166f-160">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="9166f-161">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="9166f-161">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="9166f-162">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="9166f-162">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="9166f-163">Procedure: WINRM configureren voor HTTPS</span><span class="sxs-lookup"><span data-stu-id="9166f-163">How To: Configure WINRM for HTTPS</span></span>](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[<span data-ttu-id="9166f-164">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="9166f-164">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="9166f-165">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="9166f-165">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="9166f-166">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="9166f-166">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="9166f-167">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="9166f-167">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="9166f-168">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="9166f-168">Test-WSMan</span></span>](Test-WSMan.md)