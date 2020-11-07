---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: 0ee32b680aee940df36d3219e4b24ab594e79284
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345813"
---
# <span data-ttu-id="ce800-103">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce800-103">Unregister-PSSessionConfiguration</span></span>

## <span data-ttu-id="ce800-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ce800-104">SYNOPSIS</span></span>
<span data-ttu-id="ce800-105">Hiermee verwijdert u geregistreerde sessie configuraties van de computer.</span><span class="sxs-lookup"><span data-stu-id="ce800-105">Deletes registered session configurations from the computer.</span></span>

## <span data-ttu-id="ce800-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ce800-106">SYNTAX</span></span>

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="ce800-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ce800-107">DESCRIPTION</span></span>

<span data-ttu-id="ce800-108">`Unregister-PSSessionConfiguration`Met de cmdlet worden geregistreerde sessie configuraties van de computer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ce800-108">The `Unregister-PSSessionConfiguration` cmdlet deletes registered session configurations from the computer.</span></span> <span data-ttu-id="ce800-109">Deze cmdlet is ontworpen voor systeem beheerders voor het beheren van aangepaste sessie configuraties voor gebruikers.</span><span class="sxs-lookup"><span data-stu-id="ce800-109">This cmdlet is designed for system administrators to manage customized session configurations for users.</span></span>

<span data-ttu-id="ce800-110">`Unregister-PSSessionConfiguration`Start de **WinRM** -service opnieuw om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="ce800-110">To make the change effective, `Unregister-PSSessionConfiguration` restarts the **WinRM** service.</span></span> <span data-ttu-id="ce800-111">Geef de para meter **NoServiceRestart** op om het opnieuw opstarten te voor komen.</span><span class="sxs-lookup"><span data-stu-id="ce800-111">To prevent the restart, specify the **NoServiceRestart** parameter.</span></span>

<span data-ttu-id="ce800-112">Als u per ongeluk de standaard **micro soft. Power shell** -of **micro soft. PowerShell32** -sessie configuraties verwijdert, gebruikt u de `Enable-PSRemoting` cmdlet om ze te herstellen.</span><span class="sxs-lookup"><span data-stu-id="ce800-112">If you accidentally delete the default **Microsoft.PowerShell** or **Microsoft.PowerShell32** session configurations, use the `Enable-PSRemoting` cmdlet to restore them.</span></span> <span data-ttu-id="ce800-113">Zie [about_Session_Configurations](About/about_Session_Configurations.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ce800-113">For more information, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="ce800-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ce800-114">EXAMPLES</span></span>

### <span data-ttu-id="ce800-115">Voor beeld 1: een sessie configuratie verwijderen</span><span class="sxs-lookup"><span data-stu-id="ce800-115">Example 1: Delete a session configuration</span></span>

<span data-ttu-id="ce800-116">In dit voor beeld wordt de **MaintenanceShell** -sessie configuratie van de computer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ce800-116">This example deletes the **MaintenanceShell** session configuration from the computer.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### <span data-ttu-id="ce800-117">Voor beeld 2: een sessie configuratie verwijderen en de WinRM-service opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="ce800-117">Example 2: Delete a session configuration and restart the WinRM service</span></span>

<span data-ttu-id="ce800-118">In dit voor beeld wordt de **MaintenanceShell** -configuratie verwijderd en wordt de WinRM-service opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="ce800-118">In this example, we delete the **MaintenanceShell** configuration and restart the WinRM service.</span></span> <span data-ttu-id="ce800-119">De **Force** -para meter onderdrukt alle gebruikers berichten om de **WinRM** -service opnieuw te starten zonder dat dit wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="ce800-119">The **Force** parameter suppresses all user messages to restart the **WinRM** service without prompting.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### <span data-ttu-id="ce800-120">Voor beeld 3: alle sessie configuraties verwijderen</span><span class="sxs-lookup"><span data-stu-id="ce800-120">Example 3: Delete all session configurations</span></span>

<span data-ttu-id="ce800-121">In deze voor beelden ziet u twee manieren om alle sessie configuraties op de computer te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ce800-121">This examples show two ways to delete all the session configurations on the computer.</span></span> <span data-ttu-id="ce800-122">Beide opdrachten hebben hetzelfde effect en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ce800-122">Both commands have the same effect and can be used interchangeably.</span></span>

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### <span data-ttu-id="ce800-123">Voor beeld 4: de registratie ongedaan maken zonder opnieuw op te starten</span><span class="sxs-lookup"><span data-stu-id="ce800-123">Example 4: Unregister without a restart</span></span>

<span data-ttu-id="ce800-124">In dit voor beeld ziet u het effect van het gebruik van de para meter **NoServiceRestart** om te voor komen dat een service opnieuw wordt gestart, waardoor sessies op de computer worden verstoord.</span><span class="sxs-lookup"><span data-stu-id="ce800-124">This example shows the effect of using the **NoServiceRestart** parameter to prevent a service restart that would disrupt any sessions on the computer.</span></span>

```
PS> Unregister-PSSessionConfiguration -Name "MaintenanceShell" -NoServiceRestart
PS> Get-PSSessionConfiguration -Name "MaintenanceShell"

Get-PSSessionConfiguration -Name MaintenanceShell : No Session Configuration matches criteria "MaintenanceShell".
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

PS> New-PSSession -ConfigurationName "MaintenanceShell"

Id Name      ComputerName    State    Configuration         Availability
-- ----      ------------    -----    -------------         ------------
1 Session1  localhost       Opened   MaintenanceShell      Available

PS> Restart-Service winrm
PS> New-PSSession -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message :
 The WS-Management service cannot process the request.
 The resource URI (http://schemas.microsoft.com/powershell/MaintenanceShell) was not found in the WS-Management catalog.
 The catalog contains the metadata that describes resources, or logical endpoints.
 For more information, see the about_Remote_Troubleshooting Help topic.
 + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
 + FullyQualifiedErrorId : PSSessionOpenFailed
```

<span data-ttu-id="ce800-125">`Unregister-PSSessionConfiguration`Hiermee verwijdert u de **MaintenanceShell** -sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ce800-125">The `Unregister-PSSessionConfiguration` deletes the **MaintenanceShell** session configuration.</span></span>
<span data-ttu-id="ce800-126">Omdat de opdracht echter de para meter **NoServiceRestart** gebruikt, wordt de **WinRM** -service niet opnieuw gestart en is de wijziging nog niet volledig effectief.</span><span class="sxs-lookup"><span data-stu-id="ce800-126">However, because the command uses the **NoServiceRestart** parameter, the **WinRM** service is not restarted and the change is not yet completely effective.</span></span>

<span data-ttu-id="ce800-127">Vervolgens wordt `Get-PSSessionConfiguration` geprobeerd de **MaintenanceShell** -sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="ce800-127">Next, the `Get-PSSessionConfiguration` tries to get the **MaintenanceShell** session.</span></span> <span data-ttu-id="ce800-128">Omdat de sessie is verwijderd uit de resource tabel van WS-Management, `Get-PSSessionConfiguration` kan deze niet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ce800-128">Because the session has been removed from the WS-Management resource table, `Get-PSSessionConfiguration` cannot return it.</span></span>

<span data-ttu-id="ce800-129">`New-PSSession`Met de cmdlet wordt een sessie gemaakt met behulp van de **MaintenanceShell** -configuratie.</span><span class="sxs-lookup"><span data-stu-id="ce800-129">The `New-PSSession` cmdlet creates a session using the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="ce800-130">De opdracht is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="ce800-130">The command succeeds.</span></span> <span data-ttu-id="ce800-131">Vervolgens wordt de **WinRM** -service opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="ce800-131">Next, we restart the **WinRM** service.</span></span>

<span data-ttu-id="ce800-132">Ten slotte `New-PSSession` probeert de cmdlet een sessie te maken die gebruikmaakt van de **MaintenanceShell** -configuratie.</span><span class="sxs-lookup"><span data-stu-id="ce800-132">Finally, the `New-PSSession` cmdlet tries to create a session that uses the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="ce800-133">Deze keer mislukt de sessie omdat de **MaintenanceShell** -configuratie is verwijderd toen de WinRM-service opnieuw werd gestart.</span><span class="sxs-lookup"><span data-stu-id="ce800-133">This time, the session fails because the **MaintenanceShell** configuration was deleted when the WinRM service restarted.</span></span>

## <span data-ttu-id="ce800-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ce800-134">PARAMETERS</span></span>

### <span data-ttu-id="ce800-135">-Force</span><span class="sxs-lookup"><span data-stu-id="ce800-135">-Force</span></span>

<span data-ttu-id="ce800-136">Geeft aan dat de cmdlet niet vraagt om bevestiging en de **WinRM** -service opnieuw opstart zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="ce800-136">Indicates that the cmdlet does not prompt you for confirmation, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="ce800-137">Als de service opnieuw wordt gestart, wordt de configuratie wijziging effectief.</span><span class="sxs-lookup"><span data-stu-id="ce800-137">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="ce800-138">Als u het opnieuw opstarten wilt voor komen en de prompt voor opnieuw opstarten wilt onderdrukken, gebruikt u de para meter **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="ce800-138">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="ce800-139">-Name</span><span class="sxs-lookup"><span data-stu-id="ce800-139">-Name</span></span>

<span data-ttu-id="ce800-140">Hiermee geeft u de namen van de sessie configuraties die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ce800-140">Specifies the names of the session configurations to delete.</span></span> <span data-ttu-id="ce800-141">Voer één sessie configuratie naam of een configuratie naam patroon in.</span><span class="sxs-lookup"><span data-stu-id="ce800-141">Enter one session configuration name or a configuration name pattern.</span></span> <span data-ttu-id="ce800-142">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="ce800-142">Wildcard characters are permitted.</span></span> <span data-ttu-id="ce800-143">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="ce800-143">This parameter is required.</span></span>

<span data-ttu-id="ce800-144">U kunt ook een sessie configuratie door sluizen naar `Unregister-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="ce800-144">You can also pipe a session configurations to `Unregister-PSSessionConfiguration`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ce800-145">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="ce800-145">-NoServiceRestart</span></span>

<span data-ttu-id="ce800-146">Geeft aan dat met deze cmdlet de **WinRM** -service niet opnieuw wordt gestart en wordt de prompt voor het opnieuw starten van de service onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="ce800-146">Indicates that this cmdlet does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="ce800-147">Wanneer u een `Unregister-PSSessionConfiguration` opdracht uitvoert, wordt u standaard gevraagd de **WinRM** -service opnieuw op te starten om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="ce800-147">By default, when you run an `Unregister-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the change effective.</span></span> <span data-ttu-id="ce800-148">Zolang de **WinRM** -service opnieuw is gestart, kunnen gebruikers nog steeds de niet-geregistreerde sessie configuratie gebruiken, zelfs `Get-PSSessionConfiguration` niet.</span><span class="sxs-lookup"><span data-stu-id="ce800-148">Until the **WinRM** service is restarted, users can still use the unregistered session configuration, even though `Get-PSSessionConfiguration` does not find it.</span></span>

<span data-ttu-id="ce800-149">Als u de **WinRM** -service opnieuw wilt starten zonder te vragen, geeft u de para meter **Force** op.</span><span class="sxs-lookup"><span data-stu-id="ce800-149">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="ce800-150">Gebruik de cmdlet om de **WinRM** -service hand matig opnieuw te starten `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="ce800-150">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="ce800-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ce800-151">-Confirm</span></span>

<span data-ttu-id="ce800-152">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ce800-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ce800-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ce800-153">-WhatIf</span></span>

<span data-ttu-id="ce800-154">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ce800-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ce800-155">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ce800-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ce800-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ce800-156">CommonParameters</span></span>

<span data-ttu-id="ce800-157">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ce800-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ce800-158">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ce800-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ce800-159">INVOER</span><span class="sxs-lookup"><span data-stu-id="ce800-159">INPUTS</span></span>

### <span data-ttu-id="ce800-160">Micro soft. Power shell. commands. PSSessionConfigurationCommands # PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce800-160">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

<span data-ttu-id="ce800-161">U kunt een sessie configuratie object door sluizen van `Get-PSSessionConfiguration` naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ce800-161">You can pipe a session configuration object from `Get-PSSessionConfiguration` to this cmdlet.</span></span>

## <span data-ttu-id="ce800-162">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ce800-162">OUTPUTS</span></span>

### <span data-ttu-id="ce800-163">Geen</span><span class="sxs-lookup"><span data-stu-id="ce800-163">None</span></span>

<span data-ttu-id="ce800-164">Met deze cmdlet worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ce800-164">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="ce800-165">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ce800-165">NOTES</span></span>

<span data-ttu-id="ce800-166">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="ce800-166">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="ce800-167">Als u deze cmdlet wilt uitvoeren, moet u Power shell starten met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="ce800-167">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="ce800-168">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ce800-168">RELATED LINKS</span></span>

[<span data-ttu-id="ce800-169">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce800-169">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="ce800-170">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce800-170">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="ce800-171">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce800-171">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="ce800-172">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="ce800-172">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="ce800-173">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="ce800-173">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="ce800-174">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce800-174">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="ce800-175">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce800-175">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="ce800-176">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="ce800-176">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="ce800-177">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce800-177">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="ce800-178">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="ce800-178">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="ce800-179">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="ce800-179">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="ce800-180">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="ce800-180">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
