---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e5d50af0551a183b8e9e1995fbd722c331a48486
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704722"
---
# <span data-ttu-id="d9aa6-102">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="d9aa6-102">Set-WSManQuickConfig</span></span>

## <span data-ttu-id="d9aa6-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d9aa6-103">SYNOPSIS</span></span>
<span data-ttu-id="d9aa6-104">Hiermee configureert u de lokale computer voor extern beheer.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-104">Configures the local computer for remote management.</span></span>

## <span data-ttu-id="d9aa6-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d9aa6-105">SYNTAX</span></span>

### <span data-ttu-id="d9aa6-106">Alles</span><span class="sxs-lookup"><span data-stu-id="d9aa6-106">All</span></span>

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## <span data-ttu-id="d9aa6-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d9aa6-107">DESCRIPTION</span></span>

<span data-ttu-id="d9aa6-108">`Set-WSManQuickConfig`Met de cmdlet wordt de computer geconfigureerd om externe Power shell-opdrachten te ontvangen die worden verzonden met behulp van de technologie van webservices voor beheer (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="d9aa6-108">The `Set-WSManQuickConfig` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the Web Services for Management (WS-Management) technology.</span></span>

<span data-ttu-id="d9aa6-109">`Set-WSManQuickConfig` voert de volgende acties uit:</span><span class="sxs-lookup"><span data-stu-id="d9aa6-109">`Set-WSManQuickConfig` performs the following actions:</span></span>

- <span data-ttu-id="d9aa6-110">Controleert of de WinRM-service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-110">Checks whether the WinRM service is running.</span></span> <span data-ttu-id="d9aa6-111">Als de WinRM-service niet wordt uitgevoerd, wordt de service gestart.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-111">If the WinRM service isn't running, the service is started.</span></span>
- <span data-ttu-id="d9aa6-112">Hiermee stelt u het opstart type voor de WinRM-service in op automatisch.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-112">Sets the WinRM service startup type to automatic.</span></span>
- <span data-ttu-id="d9aa6-113">Hiermee maakt u een listener voor het accepteren van aanvragen op een IP-adres.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-113">Creates a listener to accept requests on any IP address.</span></span> <span data-ttu-id="d9aa6-114">Het standaard transport is **http**.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-114">The default transport is **HTTP**.</span></span>
- <span data-ttu-id="d9aa6-115">Hiermee schakelt u een firewall-uitzonde ring voor WinRM-verkeer.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-115">Enables a firewall exception for WinRM traffic.</span></span>

<span data-ttu-id="d9aa6-116">`Set-WSManQuickConfig`Start Power shell met de optie **als administrator uitvoeren** om het programma uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-116">To run `Set-WSManQuickConfig`, start PowerShell with the **Run as Administrator** option.</span></span>

## <span data-ttu-id="d9aa6-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d9aa6-117">EXAMPLES</span></span>

### <span data-ttu-id="d9aa6-118">Voor beeld 1: extern beheer van de lokale computer via HTTP inschakelen</span><span class="sxs-lookup"><span data-stu-id="d9aa6-118">Example 1: Enable remote management of the local computer over HTTP</span></span>

<span data-ttu-id="d9aa6-119">In dit voor beeld wordt de vereiste configuratie ingesteld om extern beheer van de lokale computer in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-119">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="d9aa6-120">Met deze opdracht maakt u standaard een WS-Management listener op **http**.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-120">By default, this command creates a WS-Management listener on **HTTP**.</span></span>

```powershell
Set-WSManQuickConfig
```

### <span data-ttu-id="d9aa6-121">Voor beeld 2: extern beheer van de lokale computer via HTTPS inschakelen</span><span class="sxs-lookup"><span data-stu-id="d9aa6-121">Example 2: Enable remote management of the local computer over HTTPS</span></span>

<span data-ttu-id="d9aa6-122">In dit voor beeld wordt de vereiste configuratie ingesteld om extern beheer van de lokale computer in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-122">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="d9aa6-123">De para meter **UseSSL** geeft aan dat **https** wordt gebruikt om te communiceren met de computer.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-123">The **UseSSL** parameter specifies that **HTTPS** is used to communicate with the computer.</span></span>

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> <span data-ttu-id="d9aa6-124">**Https** vereist hand matige configuratie.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-124">**HTTPS** requires manual configuration.</span></span> <span data-ttu-id="d9aa6-125">Zie de beschrijving van de para meter **UseSSL** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-125">For more information, see the **UseSSL** parameter's description.</span></span>

## <span data-ttu-id="d9aa6-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d9aa6-126">PARAMETERS</span></span>

### <span data-ttu-id="d9aa6-127">-Force</span><span class="sxs-lookup"><span data-stu-id="d9aa6-127">-Force</span></span>

<span data-ttu-id="d9aa6-128">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-128">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="d9aa6-129">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="d9aa6-129">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="d9aa6-130">Hiermee configureert u Windows-client versies voor externe toegang wanneer de computer zich op een openbaar netwerk bevindt.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-130">Configures Windows client versions for remoting when the computer is on a public network.</span></span> <span data-ttu-id="d9aa6-131">Met deze para meter wordt een firewall regel ingeschakeld voor open bare netwerken die alleen externe toegang toestaan vanaf computers in hetzelfde lokale subnet.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-131">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="d9aa6-132">Deze para meter heeft geen invloed op Server versies van Windows, die standaard een lokale subnet-firewall regel voor open bare netwerken hebben.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-132">This parameter has no effect on server versions of Windows, that by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="d9aa6-133">Als de firewall regel van het lokale subnet is uitgeschakeld op de server versie van Windows, `Enable-PSRemoting` schakelt u deze opnieuw in, ongeacht de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-133">If the local subnet firewall rule is disabled on the server version of Windows, `Enable-PSRemoting` re-enables it, regardless of this parameter's value.</span></span>

<span data-ttu-id="d9aa6-134">Als u de beperkingen voor lokale subnetten wilt verwijderen en externe toegang vanaf alle locaties op open bare netwerken wilt inschakelen, gebruikt u de `Set-NetFirewallRule` cmdlet in de module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="d9aa6-134">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="d9aa6-135">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-135">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="d9aa6-136">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="d9aa6-136">-UseSSL</span></span>

<span data-ttu-id="d9aa6-137">Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) wordt gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-137">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span> <span data-ttu-id="d9aa6-138">SSL wordt standaard niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-138">By default, SSL isn't used.</span></span>

<span data-ttu-id="d9aa6-139">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-139">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="d9aa6-140">Met de para meter **UseSSL** kunt u de extra beveiliging van https in plaats van http opgeven.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-140">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="d9aa6-141">Als u deze para meter gebruikt en SSL niet beschikbaar is op de poort die wordt gebruikt voor de verbinding, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-141">If you use this parameter and SSL isn't available on the port that's used for the connection, the command fails.</span></span>

<span data-ttu-id="d9aa6-142">**Https** vereist hand matige configuratie van WinRM-en firewall regels.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-142">**HTTPS** requires manual configuration of WinRM and firewall rules.</span></span> <span data-ttu-id="d9aa6-143">Zie [How to: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-143">For more information, see [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span></span>

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

### <span data-ttu-id="d9aa6-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d9aa6-144">CommonParameters</span></span>

<span data-ttu-id="d9aa6-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d9aa6-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d9aa6-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="d9aa6-147">INPUTS</span></span>

### <span data-ttu-id="d9aa6-148">Geen</span><span class="sxs-lookup"><span data-stu-id="d9aa6-148">None</span></span>

<span data-ttu-id="d9aa6-149">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-149">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="d9aa6-150">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d9aa6-150">OUTPUTS</span></span>

### <span data-ttu-id="d9aa6-151">Geen</span><span class="sxs-lookup"><span data-stu-id="d9aa6-151">None</span></span>

<span data-ttu-id="d9aa6-152">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="d9aa6-152">This cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="d9aa6-153">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d9aa6-153">NOTES</span></span>

## <span data-ttu-id="d9aa6-154">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d9aa6-154">RELATED LINKS</span></span>

[<span data-ttu-id="d9aa6-155">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="d9aa6-155">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="d9aa6-156">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="d9aa6-156">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="d9aa6-157">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="d9aa6-157">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="d9aa6-158">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="d9aa6-158">Enable-PSRemoting</span></span>](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[<span data-ttu-id="d9aa6-159">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="d9aa6-159">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="d9aa6-160">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="d9aa6-160">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="d9aa6-161">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="d9aa6-161">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="d9aa6-162">Procedure: WINRM configureren voor HTTPS</span><span class="sxs-lookup"><span data-stu-id="d9aa6-162">How To: Configure WINRM for HTTPS</span></span>](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[<span data-ttu-id="d9aa6-163">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="d9aa6-163">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="d9aa6-164">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="d9aa6-164">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="d9aa6-165">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="d9aa6-165">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="d9aa6-166">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="d9aa6-166">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="d9aa6-167">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="d9aa6-167">Test-WSMan</span></span>](Test-WSMan.md)

