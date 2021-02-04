---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: 4ac7605ada0fdb682e9df31c2422d368d6e64f57
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705496"
---
# <span data-ttu-id="d9dcc-102">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9dcc-102">Unregister-PSSessionConfiguration</span></span>

## <span data-ttu-id="d9dcc-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d9dcc-103">SYNOPSIS</span></span>
<span data-ttu-id="d9dcc-104">Hiermee verwijdert u geregistreerde sessie configuraties van de computer.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-104">Deletes registered session configurations from the computer.</span></span>

## <span data-ttu-id="d9dcc-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d9dcc-105">SYNTAX</span></span>

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="d9dcc-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d9dcc-106">DESCRIPTION</span></span>

<span data-ttu-id="d9dcc-107">`Unregister-PSSessionConfiguration`Met de cmdlet worden geregistreerde sessie configuraties van de computer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-107">The `Unregister-PSSessionConfiguration` cmdlet deletes registered session configurations from the computer.</span></span> <span data-ttu-id="d9dcc-108">Deze cmdlet is ontworpen voor systeem beheerders voor het beheren van aangepaste sessie configuraties voor gebruikers.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-108">This cmdlet is designed for system administrators to manage customized session configurations for users.</span></span>

<span data-ttu-id="d9dcc-109">`Unregister-PSSessionConfiguration`Start de **WinRM** -service opnieuw om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-109">To make the change effective, `Unregister-PSSessionConfiguration` restarts the **WinRM** service.</span></span> <span data-ttu-id="d9dcc-110">Geef de para meter **NoServiceRestart** op om het opnieuw opstarten te voor komen.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-110">To prevent the restart, specify the **NoServiceRestart** parameter.</span></span>

<span data-ttu-id="d9dcc-111">Als u per ongeluk de standaard **micro soft. Power shell** -of **micro soft. PowerShell32** -sessie configuraties verwijdert, gebruikt u de `Enable-PSRemoting` cmdlet om ze te herstellen.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-111">If you accidentally delete the default **Microsoft.PowerShell** or **Microsoft.PowerShell32** session configurations, use the `Enable-PSRemoting` cmdlet to restore them.</span></span> <span data-ttu-id="d9dcc-112">Zie [about_Session_Configurations](About/about_Session_Configurations.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-112">For more information, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="d9dcc-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d9dcc-113">EXAMPLES</span></span>

### <span data-ttu-id="d9dcc-114">Voor beeld 1: een sessie configuratie verwijderen</span><span class="sxs-lookup"><span data-stu-id="d9dcc-114">Example 1: Delete a session configuration</span></span>

<span data-ttu-id="d9dcc-115">In dit voor beeld wordt de **MaintenanceShell** -sessie configuratie van de computer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-115">This example deletes the **MaintenanceShell** session configuration from the computer.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### <span data-ttu-id="d9dcc-116">Voor beeld 2: een sessie configuratie verwijderen en de WinRM-service opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="d9dcc-116">Example 2: Delete a session configuration and restart the WinRM service</span></span>

<span data-ttu-id="d9dcc-117">In dit voor beeld wordt de **MaintenanceShell** -configuratie verwijderd en wordt de WinRM-service opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-117">In this example, we delete the **MaintenanceShell** configuration and restart the WinRM service.</span></span> <span data-ttu-id="d9dcc-118">De **Force** -para meter onderdrukt alle gebruikers berichten om de **WinRM** -service opnieuw te starten zonder dat dit wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-118">The **Force** parameter suppresses all user messages to restart the **WinRM** service without prompting.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### <span data-ttu-id="d9dcc-119">Voor beeld 3: alle sessie configuraties verwijderen</span><span class="sxs-lookup"><span data-stu-id="d9dcc-119">Example 3: Delete all session configurations</span></span>

<span data-ttu-id="d9dcc-120">In deze voor beelden ziet u twee manieren om alle sessie configuraties op de computer te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-120">This examples show two ways to delete all the session configurations on the computer.</span></span> <span data-ttu-id="d9dcc-121">Beide opdrachten hebben hetzelfde effect en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-121">Both commands have the same effect and can be used interchangeably.</span></span>

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### <span data-ttu-id="d9dcc-122">Voor beeld 4: de registratie ongedaan maken zonder opnieuw op te starten</span><span class="sxs-lookup"><span data-stu-id="d9dcc-122">Example 4: Unregister without a restart</span></span>

<span data-ttu-id="d9dcc-123">In dit voor beeld ziet u het effect van het gebruik van de para meter **NoServiceRestart** om te voor komen dat een service opnieuw wordt gestart, waardoor sessies op de computer worden verstoord.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-123">This example shows the effect of using the **NoServiceRestart** parameter to prevent a service restart that would disrupt any sessions on the computer.</span></span>

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

<span data-ttu-id="d9dcc-124">`Unregister-PSSessionConfiguration`Hiermee verwijdert u de **MaintenanceShell** -sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-124">The `Unregister-PSSessionConfiguration` deletes the **MaintenanceShell** session configuration.</span></span>
<span data-ttu-id="d9dcc-125">Omdat de opdracht echter de para meter **NoServiceRestart** gebruikt, wordt de **WinRM** -service niet opnieuw gestart en is de wijziging nog niet volledig effectief.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-125">However, because the command uses the **NoServiceRestart** parameter, the **WinRM** service is not restarted and the change is not yet completely effective.</span></span>

<span data-ttu-id="d9dcc-126">Vervolgens wordt `Get-PSSessionConfiguration` geprobeerd de **MaintenanceShell** -sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-126">Next, the `Get-PSSessionConfiguration` tries to get the **MaintenanceShell** session.</span></span> <span data-ttu-id="d9dcc-127">Omdat de sessie is verwijderd uit de resource tabel van WS-Management, `Get-PSSessionConfiguration` kan deze niet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-127">Because the session has been removed from the WS-Management resource table, `Get-PSSessionConfiguration` cannot return it.</span></span>

<span data-ttu-id="d9dcc-128">`New-PSSession`Met de cmdlet wordt een sessie gemaakt met behulp van de **MaintenanceShell** -configuratie.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-128">The `New-PSSession` cmdlet creates a session using the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="d9dcc-129">De opdracht is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-129">The command succeeds.</span></span> <span data-ttu-id="d9dcc-130">Vervolgens wordt de **WinRM** -service opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-130">Next, we restart the **WinRM** service.</span></span>

<span data-ttu-id="d9dcc-131">Ten slotte `New-PSSession` probeert de cmdlet een sessie te maken die gebruikmaakt van de **MaintenanceShell** -configuratie.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-131">Finally, the `New-PSSession` cmdlet tries to create a session that uses the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="d9dcc-132">Deze keer mislukt de sessie omdat de **MaintenanceShell** -configuratie is verwijderd toen de WinRM-service opnieuw werd gestart.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-132">This time, the session fails because the **MaintenanceShell** configuration was deleted when the WinRM service restarted.</span></span>

## <span data-ttu-id="d9dcc-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d9dcc-133">PARAMETERS</span></span>

### <span data-ttu-id="d9dcc-134">-Force</span><span class="sxs-lookup"><span data-stu-id="d9dcc-134">-Force</span></span>

<span data-ttu-id="d9dcc-135">Geeft aan dat de cmdlet niet vraagt om bevestiging en de **WinRM** -service opnieuw opstart zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-135">Indicates that the cmdlet does not prompt you for confirmation, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="d9dcc-136">Als de service opnieuw wordt gestart, wordt de configuratie wijziging effectief.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-136">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="d9dcc-137">Als u het opnieuw opstarten wilt voor komen en de prompt voor opnieuw opstarten wilt onderdrukken, gebruikt u de para meter **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="d9dcc-137">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="d9dcc-138">-Name</span><span class="sxs-lookup"><span data-stu-id="d9dcc-138">-Name</span></span>

<span data-ttu-id="d9dcc-139">Hiermee geeft u de namen van de sessie configuraties die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-139">Specifies the names of the session configurations to delete.</span></span> <span data-ttu-id="d9dcc-140">Voer één sessie configuratie naam of een configuratie naam patroon in.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-140">Enter one session configuration name or a configuration name pattern.</span></span> <span data-ttu-id="d9dcc-141">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-141">Wildcard characters are permitted.</span></span> <span data-ttu-id="d9dcc-142">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-142">This parameter is required.</span></span>

<span data-ttu-id="d9dcc-143">U kunt ook een sessie configuratie door sluizen naar `Unregister-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="d9dcc-143">You can also pipe a session configurations to `Unregister-PSSessionConfiguration`.</span></span>

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

### <span data-ttu-id="d9dcc-144">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="d9dcc-144">-NoServiceRestart</span></span>

<span data-ttu-id="d9dcc-145">Geeft aan dat met deze cmdlet de **WinRM** -service niet opnieuw wordt gestart en wordt de prompt voor het opnieuw starten van de service onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-145">Indicates that this cmdlet does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="d9dcc-146">Wanneer u een `Unregister-PSSessionConfiguration` opdracht uitvoert, wordt u standaard gevraagd de **WinRM** -service opnieuw op te starten om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-146">By default, when you run an `Unregister-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the change effective.</span></span> <span data-ttu-id="d9dcc-147">Zolang de **WinRM** -service opnieuw is gestart, kunnen gebruikers nog steeds de niet-geregistreerde sessie configuratie gebruiken, zelfs `Get-PSSessionConfiguration` niet.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-147">Until the **WinRM** service is restarted, users can still use the unregistered session configuration, even though `Get-PSSessionConfiguration` does not find it.</span></span>

<span data-ttu-id="d9dcc-148">Als u de **WinRM** -service opnieuw wilt starten zonder te vragen, geeft u de para meter **Force** op.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-148">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="d9dcc-149">Gebruik de cmdlet om de **WinRM** -service hand matig opnieuw te starten `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="d9dcc-149">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="d9dcc-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d9dcc-150">-Confirm</span></span>

<span data-ttu-id="d9dcc-151">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d9dcc-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d9dcc-152">-WhatIf</span></span>

<span data-ttu-id="d9dcc-153">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d9dcc-154">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d9dcc-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d9dcc-155">CommonParameters</span></span>

<span data-ttu-id="d9dcc-156">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d9dcc-157">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d9dcc-158">INVOER</span><span class="sxs-lookup"><span data-stu-id="d9dcc-158">INPUTS</span></span>

### <span data-ttu-id="d9dcc-159">Micro soft. Power shell. commands. PSSessionConfigurationCommands # PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9dcc-159">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

<span data-ttu-id="d9dcc-160">U kunt een sessie configuratie object door sluizen van `Get-PSSessionConfiguration` naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-160">You can pipe a session configuration object from `Get-PSSessionConfiguration` to this cmdlet.</span></span>

## <span data-ttu-id="d9dcc-161">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d9dcc-161">OUTPUTS</span></span>

### <span data-ttu-id="d9dcc-162">Geen</span><span class="sxs-lookup"><span data-stu-id="d9dcc-162">None</span></span>

<span data-ttu-id="d9dcc-163">Met deze cmdlet worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-163">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="d9dcc-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d9dcc-164">NOTES</span></span>

<span data-ttu-id="d9dcc-165">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="d9dcc-165">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="d9dcc-166">Als u deze cmdlet wilt uitvoeren, moet u Power shell starten met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="d9dcc-166">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="d9dcc-167">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d9dcc-167">RELATED LINKS</span></span>

[<span data-ttu-id="d9dcc-168">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9dcc-168">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="d9dcc-169">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9dcc-169">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="d9dcc-170">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9dcc-170">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="d9dcc-171">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="d9dcc-171">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="d9dcc-172">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="d9dcc-172">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="d9dcc-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9dcc-173">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="d9dcc-174">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9dcc-174">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="d9dcc-175">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="d9dcc-175">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="d9dcc-176">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9dcc-176">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="d9dcc-177">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="d9dcc-177">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="d9dcc-178">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="d9dcc-178">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="d9dcc-179">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="d9dcc-179">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)