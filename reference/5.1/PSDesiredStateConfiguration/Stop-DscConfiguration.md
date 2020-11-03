---
external help file: Stop-DscConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/19/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/stop-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-DscConfiguration
ms.openlocfilehash: 93c8585ae948dfa360a2ae8e2563670de8fd6e93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250347"
---
# <span data-ttu-id="6a6fe-103">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a6fe-103">Stop-DscConfiguration</span></span>

## <span data-ttu-id="6a6fe-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6a6fe-104">SYNOPSIS</span></span>
<span data-ttu-id="6a6fe-105">Hiermee stopt u een configuratie taak die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-105">Stops a configuration job that is running.</span></span>

## <span data-ttu-id="6a6fe-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6a6fe-106">SYNTAX</span></span>

### <span data-ttu-id="6a6fe-107">Alles</span><span class="sxs-lookup"><span data-stu-id="6a6fe-107">All</span></span>

```
Stop-DscConfiguration [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6a6fe-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6a6fe-108">DESCRIPTION</span></span>

<span data-ttu-id="6a6fe-109">De `Stop-DscConfiguration` cmdlet stopt een configuratie taak die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-109">The `Stop-DscConfiguration` cmdlet stops a configuration job that is running.</span></span> <span data-ttu-id="6a6fe-110">Geef op op welke computers deze cmdlet van toepassing is met behulp van Common Information Model (CIM)-sessies.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-110">Specify which computers this cmdlet applies to by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="6a6fe-111">Als er geen configuratie taak wordt uitgevoerd, wordt met deze cmdlet een waarschuwings bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-111">If there's no configuration job running, this cmdlet returns a warning message.</span></span>

<span data-ttu-id="6a6fe-112">`Stop-DscConfiguration` is alleen beschikbaar als onderdeel van het [Update pakket van November 2014 voor Windows RT 8,1, windows 8,1 en Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) van de Microsoft ondersteuning-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-112">`Stop-DscConfiguration` is only available as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span> <span data-ttu-id="6a6fe-113">Voordat u deze cmdlet gebruikt, raadpleegt u de informatie in [What's New in Windows Power shell 5,0](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)</span><span class="sxs-lookup"><span data-stu-id="6a6fe-113">Before you use this cmdlet, review the information in [What's New in Windows PowerShell 5.0](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)</span></span>

## <span data-ttu-id="6a6fe-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6a6fe-114">EXAMPLES</span></span>

### <span data-ttu-id="6a6fe-115">Voor beeld 1: een configuratie taak stoppen</span><span class="sxs-lookup"><span data-stu-id="6a6fe-115">Example 1: Stop a configuration job</span></span>

<span data-ttu-id="6a6fe-116">In dit voor beeld wordt een CIM-sessie gemaakt met behulp van de `New-CimSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-116">In this example, a CIM session is created using the `New-CimSession` cmdlet.</span></span> <span data-ttu-id="6a6fe-117">Het **CimSession** -object wordt gebruikt om een actieve configuratie taak te stoppen.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-117">The **CimSession** object is used to stop a running configuration job.</span></span>

```powershell
$Session = New-CimSession -ComputerName Server01 -Credential ACCOUNTS\User01
Stop-DscConfiguration -CimSession $Session
```

<span data-ttu-id="6a6fe-118">`New-CimSession` maakt gebruik van de para meter **ComputerName** om de Server01-computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-118">`New-CimSession` uses the **ComputerName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="6a6fe-119">De **referentie** parameter geeft u het gebruikers account op.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-119">The **Credential** parameter specifies the user account.</span></span> <span data-ttu-id="6a6fe-120">Het **CimSession** -object wordt opgeslagen in de `$Session` variabele.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-120">The **CimSession** object is stored in the `$Session` variable.</span></span> <span data-ttu-id="6a6fe-121">Wanneer de opdracht wordt uitgevoerd, wordt u gevraagd het wacht woord van het gebruikers account op te vragen.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-121">When the command is run, you're prompted for the user account's password.</span></span>

<span data-ttu-id="6a6fe-122">`Stop-DscConfiguration` maakt gebruik van de para meter **CimSession** en het object dat is opgeslagen in `$Session` om de configuratie taak te stoppen.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-122">`Stop-DscConfiguration` uses the **CimSession** parameter and the object stored in `$Session` to stop the configuration job.</span></span>

## <span data-ttu-id="6a6fe-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6a6fe-123">PARAMETERS</span></span>

### <span data-ttu-id="6a6fe-124">-AsJob</span><span class="sxs-lookup"><span data-stu-id="6a6fe-124">-AsJob</span></span>

<span data-ttu-id="6a6fe-125">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-125">Indicates that this cmdlet runs the command as a background job.</span></span> <span data-ttu-id="6a6fe-126">Zie [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)voor meer informatie over Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-126">For more information about PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="6a6fe-127">Als u de para meter **AsJob** wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-127">To use the **AsJob** parameter, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="6a6fe-128">In Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell openen met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="6a6fe-128">On Windows Vista and later versions of the Windows operating system, you must open PowerShell with the **Run as administrator** option.</span></span> <span data-ttu-id="6a6fe-129">Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-129">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

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

### <span data-ttu-id="6a6fe-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="6a6fe-130">-CimSession</span></span>

<span data-ttu-id="6a6fe-131">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-131">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="6a6fe-132">Voer een computer naam of een sessie object in, zoals de uitvoer van `New-CimSession` of `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="6a6fe-132">Enter a computer name or a session object, such as the output from `New-CimSession` or `Get-CimSession`.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a6fe-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6a6fe-133">-Confirm</span></span>

<span data-ttu-id="6a6fe-134">`Stop-DscConfiguration` biedt geen ondersteuning voor de **confirm** -para meter.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-134">`Stop-DscConfiguration` doesn't support the **Confirm** parameter.</span></span> <span data-ttu-id="6a6fe-135">Als de para meter **confirm** wordt gebruikt, wordt er een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-135">If the **Confirm** parameter is used, an error is displayed.</span></span>

<span data-ttu-id="6a6fe-136">Voor Power shell-cmdlets die ondersteuning bieden voor het **bevestigen** , wordt u door de para meter gevraagd om verificatie voordat een opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-136">For PowerShell cmdlets that support **Confirm** , using the parameter prompts you for verification before a command is run.</span></span>

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

### <span data-ttu-id="6a6fe-137">-Force</span><span class="sxs-lookup"><span data-stu-id="6a6fe-137">-Force</span></span>

<span data-ttu-id="6a6fe-138">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-138">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="6a6fe-139">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6a6fe-139">-ThrottleLimit</span></span>

<span data-ttu-id="6a6fe-140">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-140">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

<span data-ttu-id="6a6fe-141">Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, berekent Power shell een optimale bandbreedte limiet op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-141">If this parameter is omitted or a value of `0` is entered, PowerShell calculates an optimum throttle limit based on the number of CIM cmdlets that are running on the computer.</span></span> <span data-ttu-id="6a6fe-142">De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-142">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a6fe-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6a6fe-143">-WhatIf</span></span>

<span data-ttu-id="6a6fe-144">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6a6fe-145">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="6a6fe-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a6fe-146">CommonParameters</span></span>

<span data-ttu-id="6a6fe-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a6fe-148">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6a6fe-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a6fe-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="6a6fe-149">INPUTS</span></span>

### <span data-ttu-id="6a6fe-150">Geen</span><span class="sxs-lookup"><span data-stu-id="6a6fe-150">None</span></span>

## <span data-ttu-id="6a6fe-151">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6a6fe-151">OUTPUTS</span></span>

### <span data-ttu-id="6a6fe-152">Geen</span><span class="sxs-lookup"><span data-stu-id="6a6fe-152">None</span></span>

## <span data-ttu-id="6a6fe-153">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6a6fe-153">NOTES</span></span>

## <span data-ttu-id="6a6fe-154">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6a6fe-154">RELATED LINKS</span></span>

[<span data-ttu-id="6a6fe-155">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="6a6fe-155">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="6a6fe-156">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a6fe-156">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="6a6fe-157">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="6a6fe-157">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="6a6fe-158">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="6a6fe-158">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="6a6fe-159">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a6fe-159">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="6a6fe-160">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a6fe-160">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="6a6fe-161">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a6fe-161">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

[<span data-ttu-id="6a6fe-162">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a6fe-162">Update-DscConfiguration</span></span>](Update-DscConfiguration.md)

[<span data-ttu-id="6a6fe-163">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="6a6fe-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)
