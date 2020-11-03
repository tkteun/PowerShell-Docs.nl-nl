---
external help file: Enable-DscDebug.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/enable-dscdebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-DscDebug
ms.openlocfilehash: 136481c5a1945c3d5cbd1ca7fc8ce5f580c39b0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250781"
---
# <span data-ttu-id="c94b3-103">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="c94b3-103">Enable-DscDebug</span></span>

## <span data-ttu-id="c94b3-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c94b3-104">SYNOPSIS</span></span>
<span data-ttu-id="c94b3-105">Start de fout opsporing van alle DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="c94b3-105">Starts debugging of all DSC resources.</span></span>

## <span data-ttu-id="c94b3-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c94b3-106">SYNTAX</span></span>

```
Enable-DscDebug [-BreakAll] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="c94b3-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c94b3-107">DESCRIPTION</span></span>
<span data-ttu-id="c94b3-108">Met de cmdlet **Enable-DscDebug** wordt fout opsporing van Windows Power shell desired state Configuration (DSC) door de DSC-engine ingeschakeld, ook wel de lokale Configuration Manager (LCM) genoemd.</span><span class="sxs-lookup"><span data-stu-id="c94b3-108">The **Enable-DscDebug** cmdlet enables Windows PowerShell Desired State Configuration (DSC) resource debugging by the DSC engine, which is also known as the Local Configuration Manager (LCM).</span></span>
<span data-ttu-id="c94b3-109">Standaard worden alle bron exemplaren onderbroken in het fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="c94b3-109">By default, all resource instances break into the debugger.</span></span>

## <span data-ttu-id="c94b3-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c94b3-110">EXAMPLES</span></span>

### <span data-ttu-id="c94b3-111">Voor beeld 1: fout opsporing starten</span><span class="sxs-lookup"><span data-stu-id="c94b3-111">Example 1: Start debugging</span></span>

```
PS C:\> Enable-DscDebug -BreakAll
```

<span data-ttu-id="c94b3-112">Met deze opdracht wordt aangegeven dat de DSC-Engine of de LCM de fout opsporing voor bronnen kan starten.</span><span class="sxs-lookup"><span data-stu-id="c94b3-112">This command indicates to the DSC engine or LCM to start resource debugging.</span></span>
<span data-ttu-id="c94b3-113">De volgende keer dat de configuratie wordt uitgevoerd, wordt het fout opsporingsprogramma geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c94b3-113">The next time the configuration is run, the process enters the debugger.</span></span>

### <span data-ttu-id="c94b3-114">Voor beeld 2: externe fout opsporing starten</span><span class="sxs-lookup"><span data-stu-id="c94b3-114">Example 2: Start remote debugging</span></span>

```
PS C:\> Enable-DscDebug -BreakAll -CimSession DeploymentServer
```

<span data-ttu-id="c94b3-115">Met deze opdracht wordt aangegeven dat de DSC-engine van de externe computer de fout opsporing voor bronnen kan starten.</span><span class="sxs-lookup"><span data-stu-id="c94b3-115">This command indicates to the DSC engine of the remote computer to start resource debugging.</span></span>

## <span data-ttu-id="c94b3-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c94b3-116">PARAMETERS</span></span>

### <span data-ttu-id="c94b3-117">-AsJob</span><span class="sxs-lookup"><span data-stu-id="c94b3-117">-AsJob</span></span>
<span data-ttu-id="c94b3-118">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="c94b3-118">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="c94b3-119">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="c94b3-119">-BreakAll</span></span>
<span data-ttu-id="c94b3-120">Geeft aan dat alle resources het fout opsporingsprogramma invoeren wanneer een configuratie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c94b3-120">Indicates that all resources enter the debugger when a configuration runs.</span></span>

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

### <span data-ttu-id="c94b3-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="c94b3-121">-CimSession</span></span>
<span data-ttu-id="c94b3-122">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="c94b3-122">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="c94b3-123">Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="c94b3-123">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="c94b3-124">De standaard waarde is de huidige sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c94b3-124">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="c94b3-125">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="c94b3-125">-ThrottleLimit</span></span>
<span data-ttu-id="c94b3-126">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c94b3-126">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="c94b3-127">Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c94b3-127">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="c94b3-128">De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="c94b3-128">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="c94b3-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c94b3-129">-Confirm</span></span>
<span data-ttu-id="c94b3-130">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c94b3-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c94b3-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c94b3-131">-WhatIf</span></span>
<span data-ttu-id="c94b3-132">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c94b3-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c94b3-133">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c94b3-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c94b3-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c94b3-134">CommonParameters</span></span>
<span data-ttu-id="c94b3-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c94b3-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c94b3-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c94b3-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c94b3-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="c94b3-137">INPUTS</span></span>

## <span data-ttu-id="c94b3-138">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c94b3-138">OUTPUTS</span></span>

## <span data-ttu-id="c94b3-139">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c94b3-139">NOTES</span></span>

## <span data-ttu-id="c94b3-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c94b3-140">RELATED LINKS</span></span>

[<span data-ttu-id="c94b3-141">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="c94b3-141">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="c94b3-142">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="c94b3-142">Disable-DscDebug</span></span>](Disable-DscDebug.md)

[<span data-ttu-id="c94b3-143">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c94b3-143">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="c94b3-144">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="c94b3-144">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="c94b3-145">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c94b3-145">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="c94b3-146">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c94b3-146">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="c94b3-147">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c94b3-147">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
