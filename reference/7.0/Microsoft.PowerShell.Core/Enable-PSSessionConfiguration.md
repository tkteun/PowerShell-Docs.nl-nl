---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 6c8c64161ef674e3a9babaa7ad18c33b3f18cbf0
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344436"
---
# <span data-ttu-id="2a325-103">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2a325-103">Enable-PSSessionConfiguration</span></span>

## <span data-ttu-id="2a325-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2a325-104">SYNOPSIS</span></span>
<span data-ttu-id="2a325-105">Hiermee schakelt u de sessie configuraties in op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2a325-105">Enables the session configurations on the local computer.</span></span>

## <span data-ttu-id="2a325-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2a325-106">SYNTAX</span></span>

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2a325-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2a325-107">DESCRIPTION</span></span>

<span data-ttu-id="2a325-108">Met de `Enable-PSSessionConfiguration` cmdlet worden geregistreerde sessie configuraties ingeschakeld die zijn uitgeschakeld, zoals met behulp van de `Disable-PSSessionConfiguration` `Disable-PSRemoting` cmdlets of de **AccessMode** -para meter van `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="2a325-108">The `Enable-PSSessionConfiguration` cmdlet enables registered session configurations that have been disabled, such as by using the `Disable-PSSessionConfiguration` or `Disable-PSRemoting` cmdlets, or the **AccessMode** parameter of `Register-PSSessionConfiguration`.</span></span> <span data-ttu-id="2a325-109">Dit is een geavanceerde cmdlet die is ontworpen om te worden gebruikt door systeem beheerders voor het beheren van aangepaste sessie configuraties voor hun gebruikers.</span><span class="sxs-lookup"><span data-stu-id="2a325-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="2a325-110">Zonder para meters wordt `Enable-PSSessionConfiguration` de configuratie van **micro soft. Power shell** ingeschakeld. Dit is de standaard configuratie die wordt gebruikt voor sessies.</span><span class="sxs-lookup"><span data-stu-id="2a325-110">Without parameters, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** configuration, which is the default configuration that is used for sessions.</span></span>

<span data-ttu-id="2a325-111">`Enable-PSSessionConfiguration` Hiermee wordt de instelling **Deny_All** verwijderd uit de security descriptor van de betrokken sessie configuraties, wordt de listener ingeschakeld die aanvragen op een IP-adres accepteert en wordt de WinRM-service opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="2a325-111">`Enable-PSSessionConfiguration` removes the **Deny_All** setting from the security descriptor of the affected session configurations, turns on the listener that accepts requests on any IP address, and restarts the WinRM service.</span></span> <span data-ttu-id="2a325-112">Vanaf Power Shell 3,0 `Enable-PSSessionConfiguration` wordt ook de waarde van de eigenschap **enabled** van de sessie configuratie ( `WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled` ) ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="2a325-112">Beginning in PowerShell 3.0, `Enable-PSSessionConfiguration` also sets the value of the **Enabled** property of the session configuration (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) to True.</span></span> <span data-ttu-id="2a325-113">`Enable-PSSessionConfiguration`De instelling **Network_Deny_All** (Security descriptor) wordt echter niet verwijderd of gewijzigd, `AccessMode=Local` waardoor alleen gebruikers van de lokale computer kunnen gebruiken voor de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="2a325-113">However, `Enable-PSSessionConfiguration` does not remove or change the **Network_Deny_All** (`AccessMode=Local`) security descriptor setting that allows only users of the local computer to use to the session configuration.</span></span>

## <span data-ttu-id="2a325-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2a325-114">EXAMPLES</span></span>

### <span data-ttu-id="2a325-115">Voor beeld 1: de standaard sessie opnieuw inschakelen</span><span class="sxs-lookup"><span data-stu-id="2a325-115">Example 1: Re-enable the default session</span></span>

<span data-ttu-id="2a325-116">In dit voor beeld wordt de standaard sessie configuratie van **micro soft. Power shell** op de computer opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2a325-116">This example re-enables the **Microsoft.PowerShell** default session configuration on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration
```

### <span data-ttu-id="2a325-117">Voor beeld 2: opgegeven sessies opnieuw inschakelen</span><span class="sxs-lookup"><span data-stu-id="2a325-117">Example 2: Re-enable specified sessions</span></span>

<span data-ttu-id="2a325-118">In dit voor beeld worden de **MaintenanceShell** -en **AdminShell** -sessie configuraties op de computer opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2a325-118">This example re-enables the **MaintenanceShell** and **AdminShell** session configurations on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### <span data-ttu-id="2a325-119">Voor beeld 3: alle sessies opnieuw inschakelen</span><span class="sxs-lookup"><span data-stu-id="2a325-119">Example 3: Re-enable the all sessions</span></span>

<span data-ttu-id="2a325-120">In dit voor beeld worden alle sessie configuraties op de computer opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2a325-120">This example re-enables all session configurations on the computer.</span></span> <span data-ttu-id="2a325-121">Deze opdrachten zijn gelijk.</span><span class="sxs-lookup"><span data-stu-id="2a325-121">These commands are equivalent.</span></span>
<span data-ttu-id="2a325-122">Daarom kunt u beide gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2a325-122">Therefore, you can use either.</span></span>

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

<span data-ttu-id="2a325-123">`Enable-PSSessionConfiguration` Er wordt geen fout gegenereerd als u een sessie configuratie inschakelt die al is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2a325-123">`Enable-PSSessionConfiguration` does not generate an error if you enable a session configuration that is already enabled.</span></span>

### <span data-ttu-id="2a325-124">Voor beeld 4: een sessie opnieuw inschakelen en een nieuwe security descriptor opgeven</span><span class="sxs-lookup"><span data-stu-id="2a325-124">Example 4: Re-enable a session and specify a new security descriptor</span></span>

<span data-ttu-id="2a325-125">In dit voor beeld wordt de configuratie van de **MaintenanceShell** -sessie opnieuw ingeschakeld en wordt een nieuwe security descriptor voor de configuratie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2a325-125">This example re-enables the **MaintenanceShell** session configuration and specifies a new security descriptor for the configuration.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## <span data-ttu-id="2a325-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2a325-126">PARAMETERS</span></span>

### <span data-ttu-id="2a325-127">-Force</span><span class="sxs-lookup"><span data-stu-id="2a325-127">-Force</span></span>

<span data-ttu-id="2a325-128">Geeft aan dat de cmdlet niet vraagt om bevestiging en de WinRM-service opnieuw opstart zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="2a325-128">Indicates that the cmdlet does not prompt you for confirmation, and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="2a325-129">Als de service opnieuw wordt gestart, wordt de configuratie wijziging effectief.</span><span class="sxs-lookup"><span data-stu-id="2a325-129">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="2a325-130">Als u het opnieuw opstarten wilt voor komen en de prompt voor opnieuw opstarten wilt onderdrukken, gebruikt u de para meter **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="2a325-130">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="2a325-131">-Name</span><span class="sxs-lookup"><span data-stu-id="2a325-131">-Name</span></span>

<span data-ttu-id="2a325-132">Hiermee geeft u de namen van de sessie configuraties op die moeten worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2a325-132">Specifies the names of session configurations to enable.</span></span> <span data-ttu-id="2a325-133">Voer een of meer configuratie namen in.</span><span class="sxs-lookup"><span data-stu-id="2a325-133">Enter one or more configuration names.</span></span>
<span data-ttu-id="2a325-134">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2a325-134">Wildcard characters are permitted.</span></span>

<span data-ttu-id="2a325-135">U kunt ook een teken reeks met een configuratie naam of een sessie configuratie object door sluizen naar `Enable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="2a325-135">You can also pipe a string that contains a configuration name or a session configuration object to `Enable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="2a325-136">Als u deze para meter weglaat, wordt `Enable-PSSessionConfiguration` de **micro soft. Power shell** -sessie configuratie ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2a325-136">If you omit this parameter, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** session configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="2a325-137">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="2a325-137">-NoServiceRestart</span></span>

<span data-ttu-id="2a325-138">Geeft aan dat de cmdlet de service niet opnieuw opstart.</span><span class="sxs-lookup"><span data-stu-id="2a325-138">Indicates that the cmdlet does not restart the service.</span></span>

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

### <span data-ttu-id="2a325-139">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="2a325-139">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="2a325-140">Hiermee geeft u een security descriptor op waarmee deze cmdlet de security descriptor in de sessie configuratie vervangt.</span><span class="sxs-lookup"><span data-stu-id="2a325-140">Specifies a security descriptor with which this cmdlet replaces the security descriptor on the session configuration.</span></span>

<span data-ttu-id="2a325-141">Als u deze para meter weglaat, wordt `Enable-PSSessionConfiguration` alleen het item alle items weigeren uit de security descriptor verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2a325-141">If you omit this parameter, `Enable-PSSessionConfiguration` only deletes the deny all item from the security descriptor.</span></span>

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

### <span data-ttu-id="2a325-142">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="2a325-142">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="2a325-143">Geeft aan dat met deze cmdlet de sessie configuratie wordt ingeschakeld wanneer de computer zich op een openbaar netwerk bevindt.</span><span class="sxs-lookup"><span data-stu-id="2a325-143">Indicates that this cmdlet enables the session configuration when the computer is on a public network.</span></span> <span data-ttu-id="2a325-144">Met deze para meter wordt een firewall regel ingeschakeld voor open bare netwerken die alleen externe toegang toestaan vanaf computers in hetzelfde lokale subnet.</span><span class="sxs-lookup"><span data-stu-id="2a325-144">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="2a325-145">Standaard `Enable-PSSessionConfiguration` mislukt op een openbaar netwerk.</span><span class="sxs-lookup"><span data-stu-id="2a325-145">By default, `Enable-PSSessionConfiguration` fails on a public network.</span></span>

<span data-ttu-id="2a325-146">Deze para meter is ontworpen voor client versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="2a325-146">This parameter is designed for client versions of the Windows operating system.</span></span> <span data-ttu-id="2a325-147">Server versies van het Windows-besturings systeem hebben een lokale subnet-firewall regel voor open bare netwerken.</span><span class="sxs-lookup"><span data-stu-id="2a325-147">Server versions of the Windows operating system have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="2a325-148">Als de regel voor de lokale subnet-firewall echter is uitgeschakeld op een server versie van het Windows-besturings systeem, wordt deze door deze para meter opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2a325-148">However, if the local subnet firewall rule is disabled on a server version of the Windows operating system, this parameter re-enables it.</span></span>

<span data-ttu-id="2a325-149">Als u de beperkingen voor lokale subnetten wilt verwijderen en externe toegang vanaf alle locaties op open bare netwerken wilt inschakelen, gebruikt u de `Set-NetFirewallRule` cmdlet in de module netsecurity.</span><span class="sxs-lookup"><span data-stu-id="2a325-149">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="2a325-150">Voor meer informatie raadpleegt u `Enable-PSRemoting`.</span><span class="sxs-lookup"><span data-stu-id="2a325-150">For more information, see `Enable-PSRemoting`.</span></span>

<span data-ttu-id="2a325-151">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2a325-151">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="2a325-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2a325-152">-Confirm</span></span>

<span data-ttu-id="2a325-153">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2a325-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2a325-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2a325-154">-WhatIf</span></span>

<span data-ttu-id="2a325-155">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2a325-155">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2a325-156">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2a325-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2a325-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a325-157">CommonParameters</span></span>

<span data-ttu-id="2a325-158">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2a325-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2a325-159">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2a325-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2a325-160">INVOER</span><span class="sxs-lookup"><span data-stu-id="2a325-160">INPUTS</span></span>

### <span data-ttu-id="2a325-161">Micro soft. Power shell. commands. PSSessionConfigurationCommands # PSSessionConfiguration, System. String</span><span class="sxs-lookup"><span data-stu-id="2a325-161">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="2a325-162">U kunt een sessie configuratie object of een teken reeks die de naam van een sessie configuratie bevat, door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2a325-162">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="2a325-163">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2a325-163">OUTPUTS</span></span>

### <span data-ttu-id="2a325-164">Geen</span><span class="sxs-lookup"><span data-stu-id="2a325-164">None</span></span>

<span data-ttu-id="2a325-165">Met deze cmdlet worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2a325-165">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="2a325-166">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2a325-166">NOTES</span></span>

<span data-ttu-id="2a325-167">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="2a325-167">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="2a325-168">Als u deze cmdlet wilt gebruiken, moet u Power shell starten met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="2a325-168">To use this cmdlet, you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="2a325-169">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2a325-169">RELATED LINKS</span></span>

[<span data-ttu-id="2a325-170">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2a325-170">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="2a325-171">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2a325-171">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="2a325-172">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="2a325-172">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="2a325-173">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="2a325-173">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="2a325-174">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2a325-174">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="2a325-175">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2a325-175">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="2a325-176">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="2a325-176">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="2a325-177">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2a325-177">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="2a325-178">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="2a325-178">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="2a325-179">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="2a325-179">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="2a325-180">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="2a325-180">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
