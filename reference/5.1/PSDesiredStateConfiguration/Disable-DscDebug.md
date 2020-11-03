---
external help file: Disable-DscDebug.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/disable-dscdebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-DscDebug
ms.openlocfilehash: fdaba8358772f559a33117c796a923d774b009cb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250779"
---
# <span data-ttu-id="04bfe-103">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="04bfe-103">Disable-DscDebug</span></span>

## <span data-ttu-id="04bfe-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="04bfe-104">SYNOPSIS</span></span>
<span data-ttu-id="04bfe-105">Hiermee stopt u fout opsporing van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="04bfe-105">Stops debugging of DSC resources.</span></span>

## <span data-ttu-id="04bfe-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="04bfe-106">SYNTAX</span></span>

```
Disable-DscDebug [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="04bfe-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="04bfe-107">DESCRIPTION</span></span>
<span data-ttu-id="04bfe-108">De cmdlet **Disable-DscDebug** vraagt of de Windows Power shell-engine voor desired state Configuration (DSC) fout opsporing van DSC-resources stopt.</span><span class="sxs-lookup"><span data-stu-id="04bfe-108">The **Disable-DscDebug** cmdlet requests that the Windows PowerShell Desired State Configuration (DSC) engine stop debugging of DSC resources.</span></span>
<span data-ttu-id="04bfe-109">Deze cmdlet heeft geen effect als de DSC-engine zich momenteel niet in de foutopsporingsmodus bevindt.</span><span class="sxs-lookup"><span data-stu-id="04bfe-109">This cmdlet has no effect if the DSC engine is not currently in debugging mode.</span></span>

## <span data-ttu-id="04bfe-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="04bfe-110">EXAMPLES</span></span>

### <span data-ttu-id="04bfe-111">Voor beeld 1: fout opsporing van bronnen stoppen</span><span class="sxs-lookup"><span data-stu-id="04bfe-111">Example 1: Stop resource debugging</span></span>

```
PS C:\> Disable-DscDebug
```

<span data-ttu-id="04bfe-112">Met deze opdracht wordt de DSC-engine op de lokale Configuration Manager (LCM) aangegeven om fout opsporing van resources te stoppen.</span><span class="sxs-lookup"><span data-stu-id="04bfe-112">This command indicates to the DSC engine on the Local Configuration Manager (LCM) to stop resource debugging.</span></span>

### <span data-ttu-id="04bfe-113">Voor beeld 2: de status van de engine controleren en de fout opsporing stoppen</span><span class="sxs-lookup"><span data-stu-id="04bfe-113">Example 2: Check the engine state and stop debugging</span></span>

```
PS C:\> if((Get-DscLocalConfigurationManager).DebugMode -like '*Break*'){Disable-DscDebug}
```

<span data-ttu-id="04bfe-114">Met deze opdracht wordt de status van de DSC-engine gecontroleerd en wordt de fout opsporing van bronnen alleen gestopt als deze zich al in de foutopsporingsmodus bevindt</span><span class="sxs-lookup"><span data-stu-id="04bfe-114">This command checks the DSC engine state, and stops resource debugging only if it is already in debugging mode</span></span>

## <span data-ttu-id="04bfe-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="04bfe-115">PARAMETERS</span></span>

### <span data-ttu-id="04bfe-116">-AsJob</span><span class="sxs-lookup"><span data-stu-id="04bfe-116">-AsJob</span></span>
<span data-ttu-id="04bfe-117">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="04bfe-117">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="04bfe-118">-CimSession</span><span class="sxs-lookup"><span data-stu-id="04bfe-118">-CimSession</span></span>
<span data-ttu-id="04bfe-119">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="04bfe-119">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="04bfe-120">Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="04bfe-120">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="04bfe-121">De standaard waarde is de huidige sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="04bfe-121">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="04bfe-122">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="04bfe-122">-ThrottleLimit</span></span>
<span data-ttu-id="04bfe-123">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="04bfe-123">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="04bfe-124">Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="04bfe-124">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="04bfe-125">De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="04bfe-125">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="04bfe-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="04bfe-126">-Confirm</span></span>
<span data-ttu-id="04bfe-127">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="04bfe-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="04bfe-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="04bfe-128">-WhatIf</span></span>
<span data-ttu-id="04bfe-129">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="04bfe-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="04bfe-130">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="04bfe-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="04bfe-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="04bfe-131">CommonParameters</span></span>
<span data-ttu-id="04bfe-132">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="04bfe-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="04bfe-133">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="04bfe-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="04bfe-134">INVOER</span><span class="sxs-lookup"><span data-stu-id="04bfe-134">INPUTS</span></span>

## <span data-ttu-id="04bfe-135">UITVOER</span><span class="sxs-lookup"><span data-stu-id="04bfe-135">OUTPUTS</span></span>

## <span data-ttu-id="04bfe-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="04bfe-136">NOTES</span></span>

## <span data-ttu-id="04bfe-137">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="04bfe-137">RELATED LINKS</span></span>

[<span data-ttu-id="04bfe-138">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="04bfe-138">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="04bfe-139">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="04bfe-139">Enable-DscDebug</span></span>](Enable-DscDebug.md)

[<span data-ttu-id="04bfe-140">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="04bfe-140">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="04bfe-141">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="04bfe-141">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

[<span data-ttu-id="04bfe-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="04bfe-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="04bfe-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="04bfe-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="04bfe-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="04bfe-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
