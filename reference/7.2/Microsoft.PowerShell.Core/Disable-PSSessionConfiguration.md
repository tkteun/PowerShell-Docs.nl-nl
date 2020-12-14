---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: c2f88431c0a09a2d4093c6523467a812812c10bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705763"
---
# <span data-ttu-id="9cdec-102">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9cdec-102">Disable-PSSessionConfiguration</span></span>

## <span data-ttu-id="9cdec-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9cdec-103">SYNOPSIS</span></span>
<span data-ttu-id="9cdec-104">Hiermee schakelt u de sessie configuraties op de lokale computer uit.</span><span class="sxs-lookup"><span data-stu-id="9cdec-104">Disables session configurations on the local computer.</span></span>

## <span data-ttu-id="9cdec-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9cdec-105">SYNTAX</span></span>

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="9cdec-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9cdec-106">DESCRIPTION</span></span>

<span data-ttu-id="9cdec-107">Met de cmdlet worden de `Disable-PSSessionConfiguration` sessie configuraties op de lokale computer uitgeschakeld, waardoor wordt voor komen dat alle gebruikers de sessie configuraties gebruiken om een door de gebruiker beheerde sessies (**PSSessions**) te maken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9cdec-107">The `Disable-PSSessionConfiguration` cmdlet disables session configurations on the local computer, which prevents all users from using the session configurations to create a user-managed sessions (**PSSessions**) on the local computer.</span></span> <span data-ttu-id="9cdec-108">Dit is een geavanceerde cmdlet die is ontworpen om te worden gebruikt door systeem beheerders voor het beheren van aangepaste sessie configuraties voor hun gebruikers.</span><span class="sxs-lookup"><span data-stu-id="9cdec-108">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="9cdec-109">Vanaf Power Shell 3,0 stelt de `Disable-PSSessionConfiguration` cmdlet de **ingeschakelde** instelling van de sessie configuratie ( `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` ) in op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="9cdec-109">Starting in PowerShell 3.0, the `Disable-PSSessionConfiguration` cmdlet sets the **Enabled** setting of the session configuration (`WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled`) to False.</span></span>

<span data-ttu-id="9cdec-110">In Power Shell 2,0 `Disable-PSSessionConfiguration` voegt de cmdlet een **Deny_All** vermelding toe aan de security descriptor van een of meer geregistreerde sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="9cdec-110">In PowerShell 2.0, the `Disable-PSSessionConfiguration` cmdlet adds a **Deny_All** entry to the security descriptor of one or more registered session configurations.</span></span>

<span data-ttu-id="9cdec-111">Zonder para meters wordt `Disable-PSSessionConfiguration` de configuratie van **micro soft. Power shell** uitgeschakeld, de standaard configuratie die wordt gebruikt voor sessies.</span><span class="sxs-lookup"><span data-stu-id="9cdec-111">Without parameters, `Disable-PSSessionConfiguration` disables the **Microsoft.PowerShell** configuration, the default configuration used for sessions.</span></span> <span data-ttu-id="9cdec-112">Tenzij de gebruiker een andere configuratie opgeeft, kunnen lokale en externe gebruikers effectief geen sessies maken die verbinding maken met de computer.</span><span class="sxs-lookup"><span data-stu-id="9cdec-112">Unless the user specifies a different configuration, both local and remote users are effectively prevented from creating any sessions that connect to the computer.</span></span>

<span data-ttu-id="9cdec-113">Als u alle sessie configuraties op de computer wilt uitschakelen, gebruikt u `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="9cdec-113">To disable all session configurations on the computer, use `Disable-PSRemoting`.</span></span>

## <span data-ttu-id="9cdec-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9cdec-114">EXAMPLES</span></span>

### <span data-ttu-id="9cdec-115">Voor beeld 1: de standaard configuratie uitschakelen</span><span class="sxs-lookup"><span data-stu-id="9cdec-115">Example 1: Disable the default configuration</span></span>

<span data-ttu-id="9cdec-116">In dit voor beeld wordt de micro soft. Power shell-sessie configuratie uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cdec-116">This example disables the Microsoft.PowerShell session configuration.</span></span>

```powershell
Disable-PSSessionConfiguration
```

### <span data-ttu-id="9cdec-117">Voor beeld 2: alle geregistreerde sessie configuraties uitschakelen</span><span class="sxs-lookup"><span data-stu-id="9cdec-117">Example 2: Disable all registered session configurations</span></span>

<span data-ttu-id="9cdec-118">In dit voor beeld worden alle geregistreerde sessie configuraties op de computer uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cdec-118">This example disables all registered session configurations on the computer.</span></span>

```powershell
Disable-PSSessionConfiguration -Name *
```

### <span data-ttu-id="9cdec-119">Voor beeld 3: sessie configuraties op naam uitschakelen</span><span class="sxs-lookup"><span data-stu-id="9cdec-119">Example 3: Disable session configurations by name</span></span>

<span data-ttu-id="9cdec-120">In dit voor beeld worden alle sessie configuraties uitgeschakeld die namen hebben die beginnen met micro soft.</span><span class="sxs-lookup"><span data-stu-id="9cdec-120">This example disables all session configurations that have names that begin with Microsoft.</span></span> <span data-ttu-id="9cdec-121">De **Force** -para meter onderdrukt alle gebruikers prompts van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cdec-121">The **Force** parameter suppresses all user prompts from the cmdlet.</span></span>

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### <span data-ttu-id="9cdec-122">Voor beeld 4: sessie configuraties uitschakelen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="9cdec-122">Example 4: Disable session configurations by using the pipeline</span></span>

<span data-ttu-id="9cdec-123">In dit voor beeld worden de **MaintenanceShell** -en **AdminShell** -sessie configuraties uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cdec-123">This example disables the **MaintenanceShell** and **AdminShell** session configurations.</span></span> <span data-ttu-id="9cdec-124">Met de pijplijn operator (|) worden de resultaten van een `Get-PSSessionConfiguration` naar verzonden `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="9cdec-124">The pipeline operator (|) sends the results of a `Get-PSSessionConfiguration` to `Disable-PSSessionConfiguration`.</span></span>

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### <span data-ttu-id="9cdec-125">Voor beeld 5: gevolgen van het uitschakelen van een sessie configuratie</span><span class="sxs-lookup"><span data-stu-id="9cdec-125">Example 5: Effects of disabling a session configuration</span></span>

<span data-ttu-id="9cdec-126">In dit voor beeld ziet u de machtigingen vóór en na `Disable-PSSessionConfiguration` het uitvoeren en het effect van het uitschakelen van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="9cdec-126">This example shows the permissions before and after running `Disable-PSSessionConfiguration` and the effect of disabling a session configuration.</span></span>

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
> <span data-ttu-id="9cdec-127">Door de configuratie uit te scha kelen, kunt u de configuratie niet wijzigen met de `Set-PSSessionConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cdec-127">Disabling the configuration does not prevent you from changing the configuration using the `Set-PSSessionConfiguration` cmdlet.</span></span> <span data-ttu-id="9cdec-128">Hiermee wordt alleen het gebruik van de configuratie voor komen.</span><span class="sxs-lookup"><span data-stu-id="9cdec-128">It only prevents use of the configuration.</span></span>

## <span data-ttu-id="9cdec-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9cdec-129">PARAMETERS</span></span>

### <span data-ttu-id="9cdec-130">-Force</span><span class="sxs-lookup"><span data-stu-id="9cdec-130">-Force</span></span>

<span data-ttu-id="9cdec-131">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="9cdec-131">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="9cdec-132">-Name</span><span class="sxs-lookup"><span data-stu-id="9cdec-132">-Name</span></span>

<span data-ttu-id="9cdec-133">Hiermee geeft u een matrix met namen van sessie configuraties op die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cdec-133">Specifies an array of names of session configurations to disable.</span></span> <span data-ttu-id="9cdec-134">Voer een of meer configuratie namen in.</span><span class="sxs-lookup"><span data-stu-id="9cdec-134">Enter one or more configuration names.</span></span> <span data-ttu-id="9cdec-135">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="9cdec-135">Wildcard characters are permitted.</span></span> <span data-ttu-id="9cdec-136">U kunt ook een teken reeks met een configuratie naam of een sessie configuratie object door sluizen naar `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="9cdec-136">You can also pipe a string that contains a configuration name or a session configuration object to `Disable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="9cdec-137">Als u deze para meter weglaat, wordt `Disable-PSSessionConfiguration` de micro soft. Power shell-sessie configuratie uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cdec-137">If you omit this parameter, `Disable-PSSessionConfiguration` disables the Microsoft.PowerShell session configuration.</span></span>

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

### <span data-ttu-id="9cdec-138">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="9cdec-138">-NoServiceRestart</span></span>

<span data-ttu-id="9cdec-139">Wordt gebruikt om te voor komen dat de WSMan-service opnieuw wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="9cdec-139">Used to prevent the restart of the WSMan service.</span></span> <span data-ttu-id="9cdec-140">Het is niet nodig om de service opnieuw te starten om de configuratie uit te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="9cdec-140">It is not necessary to restart the service to disable the configuration.</span></span>

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

### <span data-ttu-id="9cdec-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9cdec-141">-Confirm</span></span>

<span data-ttu-id="9cdec-142">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9cdec-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9cdec-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9cdec-143">-WhatIf</span></span>

<span data-ttu-id="9cdec-144">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9cdec-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9cdec-145">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9cdec-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9cdec-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9cdec-146">CommonParameters</span></span>

<span data-ttu-id="9cdec-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9cdec-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9cdec-148">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cdec-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9cdec-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="9cdec-149">INPUTS</span></span>

### <span data-ttu-id="9cdec-150">Micro soft. Power shell. commands. PSSessionConfigurationCommands # PSSessionConfiguration, System. String</span><span class="sxs-lookup"><span data-stu-id="9cdec-150">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="9cdec-151">U kunt een sessie configuratie object of een teken reeks die de naam van een sessie configuratie bevat, door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cdec-151">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="9cdec-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9cdec-152">OUTPUTS</span></span>

### <span data-ttu-id="9cdec-153">Geen</span><span class="sxs-lookup"><span data-stu-id="9cdec-153">None</span></span>

<span data-ttu-id="9cdec-154">Met deze cmdlet worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9cdec-154">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="9cdec-155">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9cdec-155">NOTES</span></span>

<span data-ttu-id="9cdec-156">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="9cdec-156">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="9cdec-157">Als u deze cmdlet wilt uitvoeren, moet u Power shell starten met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="9cdec-157">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="9cdec-158">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9cdec-158">RELATED LINKS</span></span>

[<span data-ttu-id="9cdec-159">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9cdec-159">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="9cdec-160">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9cdec-160">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="9cdec-161">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="9cdec-161">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="9cdec-162">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9cdec-162">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="9cdec-163">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9cdec-163">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="9cdec-164">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="9cdec-164">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="9cdec-165">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9cdec-165">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="9cdec-166">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="9cdec-166">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="9cdec-167">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="9cdec-167">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="9cdec-168">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="9cdec-168">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
