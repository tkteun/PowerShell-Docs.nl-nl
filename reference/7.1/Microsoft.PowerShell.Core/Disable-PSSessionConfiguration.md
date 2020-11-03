---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: ce8b77d9d3de16e16302fc7846ca8a45852511bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251374"
---
# <span data-ttu-id="d7e6a-103">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7e6a-103">Disable-PSSessionConfiguration</span></span>

## <span data-ttu-id="d7e6a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d7e6a-104">SYNOPSIS</span></span>
<span data-ttu-id="d7e6a-105">Hiermee schakelt u de sessie configuraties op de lokale computer uit.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-105">Disables session configurations on the local computer.</span></span>

## <span data-ttu-id="d7e6a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d7e6a-106">SYNTAX</span></span>

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="d7e6a-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d7e6a-107">DESCRIPTION</span></span>

<span data-ttu-id="d7e6a-108">Met de cmdlet worden de `Disable-PSSessionConfiguration` sessie configuraties op de lokale computer uitgeschakeld, waardoor wordt voor komen dat alle gebruikers de sessie configuraties gebruiken om een door de gebruiker beheerde sessies ( **PSSessions** ) te maken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-108">The `Disable-PSSessionConfiguration` cmdlet disables session configurations on the local computer, which prevents all users from using the session configurations to create a user-managed sessions ( **PSSessions** ) on the local computer.</span></span> <span data-ttu-id="d7e6a-109">Dit is een geavanceerde cmdlet die is ontworpen om te worden gebruikt door systeem beheerders voor het beheren van aangepaste sessie configuraties voor hun gebruikers.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="d7e6a-110">Vanaf Power Shell 3,0 stelt de `Disable-PSSessionConfiguration` cmdlet de **ingeschakelde** instelling van de sessie configuratie ( `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` ) in op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-110">Starting in PowerShell 3.0, the `Disable-PSSessionConfiguration` cmdlet sets the **Enabled** setting of the session configuration (`WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled`) to False.</span></span>

<span data-ttu-id="d7e6a-111">In Power Shell 2,0 `Disable-PSSessionConfiguration` voegt de cmdlet een **Deny_All** vermelding toe aan de security descriptor van een of meer geregistreerde sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-111">In PowerShell 2.0, the `Disable-PSSessionConfiguration` cmdlet adds a **Deny_All** entry to the security descriptor of one or more registered session configurations.</span></span>

<span data-ttu-id="d7e6a-112">Zonder para meters wordt `Disable-PSSessionConfiguration` de configuratie van **micro soft. Power shell** uitgeschakeld, de standaard configuratie die wordt gebruikt voor sessies.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-112">Without parameters, `Disable-PSSessionConfiguration` disables the **Microsoft.PowerShell** configuration, the default configuration used for sessions.</span></span> <span data-ttu-id="d7e6a-113">Tenzij de gebruiker een andere configuratie opgeeft, kunnen lokale en externe gebruikers effectief geen sessies maken die verbinding maken met de computer.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-113">Unless the user specifies a different configuration, both local and remote users are effectively prevented from creating any sessions that connect to the computer.</span></span>

<span data-ttu-id="d7e6a-114">Als u alle sessie configuraties op de computer wilt uitschakelen, gebruikt u `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="d7e6a-114">To disable all session configurations on the computer, use `Disable-PSRemoting`.</span></span>

## <span data-ttu-id="d7e6a-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d7e6a-115">EXAMPLES</span></span>

### <span data-ttu-id="d7e6a-116">Voor beeld 1: de standaard configuratie uitschakelen</span><span class="sxs-lookup"><span data-stu-id="d7e6a-116">Example 1: Disable the default configuration</span></span>

<span data-ttu-id="d7e6a-117">In dit voor beeld wordt de micro soft. Power shell-sessie configuratie uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-117">This example disables the Microsoft.PowerShell session configuration.</span></span>

```powershell
Disable-PSSessionConfiguration
```

### <span data-ttu-id="d7e6a-118">Voor beeld 2: alle geregistreerde sessie configuraties uitschakelen</span><span class="sxs-lookup"><span data-stu-id="d7e6a-118">Example 2: Disable all registered session configurations</span></span>

<span data-ttu-id="d7e6a-119">In dit voor beeld worden alle geregistreerde sessie configuraties op de computer uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-119">This example disables all registered session configurations on the computer.</span></span>

```powershell
Disable-PSSessionConfiguration -Name *
```

### <span data-ttu-id="d7e6a-120">Voor beeld 3: sessie configuraties op naam uitschakelen</span><span class="sxs-lookup"><span data-stu-id="d7e6a-120">Example 3: Disable session configurations by name</span></span>

<span data-ttu-id="d7e6a-121">In dit voor beeld worden alle sessie configuraties uitgeschakeld die namen hebben die beginnen met micro soft.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-121">This example disables all session configurations that have names that begin with Microsoft.</span></span> <span data-ttu-id="d7e6a-122">De **Force** -para meter onderdrukt alle gebruikers prompts van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-122">The **Force** parameter suppresses all user prompts from the cmdlet.</span></span>

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### <span data-ttu-id="d7e6a-123">Voor beeld 4: sessie configuraties uitschakelen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="d7e6a-123">Example 4: Disable session configurations by using the pipeline</span></span>

<span data-ttu-id="d7e6a-124">In dit voor beeld worden de **MaintenanceShell** -en **AdminShell** -sessie configuraties uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-124">This example disables the **MaintenanceShell** and **AdminShell** session configurations.</span></span> <span data-ttu-id="d7e6a-125">Met de pijplijn operator (|) worden de resultaten van een `Get-PSSessionConfiguration` naar verzonden `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="d7e6a-125">The pipeline operator (|) sends the results of a `Get-PSSessionConfiguration` to `Disable-PSSessionConfiguration`.</span></span>

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### <span data-ttu-id="d7e6a-126">Voor beeld 5: gevolgen van het uitschakelen van een sessie configuratie</span><span class="sxs-lookup"><span data-stu-id="d7e6a-126">Example 5: Effects of disabling a session configuration</span></span>

<span data-ttu-id="d7e6a-127">In dit voor beeld ziet u de machtigingen vóór en na `Disable-PSSessionConfiguration` het uitvoeren en het effect van het uitschakelen van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-127">This example shows the permissions before and after running `Disable-PSSessionConfiguration` and the effect of disabling a session configuration.</span></span>

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> <span data-ttu-id="d7e6a-128">Door de configuratie uit te scha kelen, kunt u de configuratie niet wijzigen met de `Set-PSSessionConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-128">Disabling the configuration does not prevent you from changing the configuration using the `Set-PSSessionConfiguration` cmdlet.</span></span> <span data-ttu-id="d7e6a-129">Hiermee wordt alleen het gebruik van de configuratie voor komen.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-129">It only prevents use of the configuration.</span></span>

## <span data-ttu-id="d7e6a-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d7e6a-130">PARAMETERS</span></span>

### <span data-ttu-id="d7e6a-131">-Force</span><span class="sxs-lookup"><span data-stu-id="d7e6a-131">-Force</span></span>

<span data-ttu-id="d7e6a-132">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-132">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="d7e6a-133">-Name</span><span class="sxs-lookup"><span data-stu-id="d7e6a-133">-Name</span></span>

<span data-ttu-id="d7e6a-134">Hiermee geeft u een matrix met namen van sessie configuraties op die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-134">Specifies an array of names of session configurations to disable.</span></span> <span data-ttu-id="d7e6a-135">Voer een of meer configuratie namen in.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-135">Enter one or more configuration names.</span></span> <span data-ttu-id="d7e6a-136">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-136">Wildcard characters are permitted.</span></span> <span data-ttu-id="d7e6a-137">U kunt ook een teken reeks met een configuratie naam of een sessie configuratie object door sluizen naar `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="d7e6a-137">You can also pipe a string that contains a configuration name or a session configuration object to `Disable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="d7e6a-138">Als u deze para meter weglaat, wordt `Disable-PSSessionConfiguration` de micro soft. Power shell-sessie configuratie uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-138">If you omit this parameter, `Disable-PSSessionConfiguration` disables the Microsoft.PowerShell session configuration.</span></span>

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

### <span data-ttu-id="d7e6a-139">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="d7e6a-139">-NoServiceRestart</span></span>

<span data-ttu-id="d7e6a-140">Wordt gebruikt om te voor komen dat de WSMan-service opnieuw wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-140">Used to prevent the restart of the WSMan service.</span></span> <span data-ttu-id="d7e6a-141">Het is niet nodig om de service opnieuw te starten om de configuratie uit te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-141">It is not necessary to restart the service to disable the configuration.</span></span>

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

### <span data-ttu-id="d7e6a-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d7e6a-142">-Confirm</span></span>

<span data-ttu-id="d7e6a-143">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d7e6a-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d7e6a-144">-WhatIf</span></span>

<span data-ttu-id="d7e6a-145">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d7e6a-146">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d7e6a-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d7e6a-147">CommonParameters</span></span>

<span data-ttu-id="d7e6a-148">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d7e6a-149">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d7e6a-150">INVOER</span><span class="sxs-lookup"><span data-stu-id="d7e6a-150">INPUTS</span></span>

### <span data-ttu-id="d7e6a-151">Micro soft. Power shell. commands. PSSessionConfigurationCommands # PSSessionConfiguration, System. String</span><span class="sxs-lookup"><span data-stu-id="d7e6a-151">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="d7e6a-152">U kunt een sessie configuratie object of een teken reeks die de naam van een sessie configuratie bevat, door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-152">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="d7e6a-153">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d7e6a-153">OUTPUTS</span></span>

### <span data-ttu-id="d7e6a-154">Geen</span><span class="sxs-lookup"><span data-stu-id="d7e6a-154">None</span></span>

<span data-ttu-id="d7e6a-155">Met deze cmdlet worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d7e6a-155">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="d7e6a-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d7e6a-156">NOTES</span></span>

<span data-ttu-id="d7e6a-157">Als u deze cmdlet wilt uitvoeren, moet u Power shell starten met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="d7e6a-157">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="d7e6a-158">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d7e6a-158">RELATED LINKS</span></span>

[<span data-ttu-id="d7e6a-159">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7e6a-159">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="d7e6a-160">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7e6a-160">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="d7e6a-161">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="d7e6a-161">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="d7e6a-162">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7e6a-162">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="d7e6a-163">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7e6a-163">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="d7e6a-164">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="d7e6a-164">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="d7e6a-165">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7e6a-165">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="d7e6a-166">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="d7e6a-166">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="d7e6a-167">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="d7e6a-167">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="d7e6a-168">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="d7e6a-168">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)

