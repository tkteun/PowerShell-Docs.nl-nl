---
external help file: Remove-DscConfigurationDocument.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-DscConfigurationDocument
ms.openlocfilehash: d3e9b15dfeea94921503247adc08b291eed9d7d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250766"
---
# <span data-ttu-id="ec9f2-103">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="ec9f2-103">Remove-DscConfigurationDocument</span></span>

## <span data-ttu-id="ec9f2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ec9f2-104">SYNOPSIS</span></span>
<span data-ttu-id="ec9f2-105">Hiermee verwijdert u een configuratie document uit de DSC-configuratie opslag.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-105">Removes a configuration document from the DSC configuration store.</span></span>

## <span data-ttu-id="ec9f2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ec9f2-106">SYNTAX</span></span>

```
Remove-DscConfigurationDocument -Stage <Stage> [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>]
 [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ec9f2-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ec9f2-107">DESCRIPTION</span></span>
<span data-ttu-id="ec9f2-108">De `Remove-DscConfigurationDocument` cmdlet verwijdert een configuratie document (. MOF-bestand) uit het configuratie archief Windows Power shell desired state Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="ec9f2-108">The `Remove-DscConfigurationDocument` cmdlet removes a configuration document (.mof file) from the Windows PowerShell Desired State Configuration (DSC) configuration store.</span></span>
<span data-ttu-id="ec9f2-109">Tijdens de configuratie `Start-DscConfiguration` kopieert de cmdlet een. MOF-bestand naar een map op de doel computer.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-109">During configuration, the `Start-DscConfiguration` cmdlet copies a .mof file to a folder on the target computer.</span></span>
<span data-ttu-id="ec9f2-110">Met deze cmdlet wordt dat configuratie document verwijderd en wordt er extra opgeruimd.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-110">This cmdlet removes that configuration document and does additional cleanup.</span></span>

<span data-ttu-id="ec9f2-111">Deze cmdlet is alleen beschikbaar als onderdeel van het [Update pakket van November 2014 voor Windows RT 8,1, Windows 8,1 en Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) uit de Microsoft ondersteuning-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-111">This cmdlet is available only as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span>

## <span data-ttu-id="ec9f2-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ec9f2-112">EXAMPLES</span></span>

### <span data-ttu-id="ec9f2-113">Voor beeld 1: het huidige configuratie document verwijderen</span><span class="sxs-lookup"><span data-stu-id="ec9f2-113">Example 1: Remove the current configuration document</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Remove-DscConfigurationDocument -Stage Current -CimSession $Session
```

<span data-ttu-id="ec9f2-114">Met de eerste opdracht maakt u een CIM-sessie met behulp van de cmdlet **New-CimSession** en slaat u het **CimSession** -object op in de variabele $Session.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-114">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="ec9f2-115">De opdracht vraagt u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-115">The command prompts you for a password.</span></span>
<span data-ttu-id="ec9f2-116">Typ `Get-Help New-CimSession` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-116">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="ec9f2-117">Met de tweede opdracht wordt het huidige configuratie document verwijderd voor de computer die is opgegeven in de **CimSession** die zijn opgeslagen in $Session.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-117">The second command removes the current configuration document for the computer specified in the **CimSession** stored in $Session.</span></span>

## <span data-ttu-id="ec9f2-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ec9f2-118">PARAMETERS</span></span>

### <span data-ttu-id="ec9f2-119">-AsJob</span><span class="sxs-lookup"><span data-stu-id="ec9f2-119">-AsJob</span></span>
<span data-ttu-id="ec9f2-120">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-120">Indicates that this cmdlet runs the command as a background job.</span></span>

<span data-ttu-id="ec9f2-121">Als u de para meter *AsJob* opgeeft, retourneert de opdracht een object dat de taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-121">If you specify the *AsJob* parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span>
<span data-ttu-id="ec9f2-122">U kunt in de sessie blijven werken totdat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-122">You can continue to work in the session until the job finishes.</span></span>
<span data-ttu-id="ec9f2-123">De taak wordt gemaakt op de lokale computer en de resultaten van externe computers worden automatisch geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-123">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="ec9f2-124">Gebruik de taak-cmdlets om de taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-124">To manage the job, use the Job cmdlets.</span></span>
<span data-ttu-id="ec9f2-125">Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-125">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="ec9f2-126">Als u deze para meter wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang en op Windows Vista en latere versies van het Windows-besturings systeem, moet u Windows Power shell openen met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-126">To use this parameter, the local and remote computers must be configured for remoting, and on Windows Vista and later versions of the Windows operating system, you must open Windows PowerShell with the Run as administrator option.</span></span>
<span data-ttu-id="ec9f2-127">Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-127">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="ec9f2-128">Zie [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)voor meer informatie over Windows Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-128">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="ec9f2-129">-CimSession</span><span class="sxs-lookup"><span data-stu-id="ec9f2-129">-CimSession</span></span>
<span data-ttu-id="ec9f2-130">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-130">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="ec9f2-131">Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet **New-CimSession** of **Get-CimSession** .</span><span class="sxs-lookup"><span data-stu-id="ec9f2-131">Enter a computer name or a session object, such as the output of a **New-CimSession** or **Get-CimSession** cmdlet.</span></span>

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

### <span data-ttu-id="ec9f2-132">-Force</span><span class="sxs-lookup"><span data-stu-id="ec9f2-132">-Force</span></span>
<span data-ttu-id="ec9f2-133">Geeft aan dat deze cmdlet de actieve configuratie taak stopt voordat het configuratie document wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-133">Indicates that this cmdlet stops the running configuration job before it removes the configuration document.</span></span>
<span data-ttu-id="ec9f2-134">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ec9f2-135">-Fase</span><span class="sxs-lookup"><span data-stu-id="ec9f2-135">-Stage</span></span>
<span data-ttu-id="ec9f2-136">Hiermee geeft u op welk configuratie document moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-136">Specifies which configuration document to remove.</span></span>
<span data-ttu-id="ec9f2-137">U kunt meerdere documenten opgeven.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-137">You can specify multiple documents.</span></span>
<span data-ttu-id="ec9f2-138">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="ec9f2-138">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ec9f2-139">VLOTT.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-139">Current.</span></span>
<span data-ttu-id="ec9f2-140">Verwijder het configuratie document waarin de huidige status van het systeem wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-140">Remove the configuration document that describes the current state of the system.</span></span>
- <span data-ttu-id="ec9f2-141">Status.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-141">Pending.</span></span>
<span data-ttu-id="ec9f2-142">Verwijder het configuratie document met een beschrijving van de status van het systeem in behandeling.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-142">Remove the configuration document that describes the pending state of the system.</span></span>
- <span data-ttu-id="ec9f2-143">Bestaande.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-143">Previous.</span></span>
<span data-ttu-id="ec9f2-144">Verwijder het configuratie document waarin de vorige status van het systeem wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-144">Remove the configuration document that describes the previous state of the system.</span></span>

```yaml
Type: Microsoft.PowerShell.Cmdletization.GeneratedTypes.RemoveDscConfigurationDocument.Stage
Parameter Sets: (All)
Aliases:
Accepted values: Current, Pending, Previous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ec9f2-145">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="ec9f2-145">-ThrottleLimit</span></span>
<span data-ttu-id="ec9f2-146">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-146">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="ec9f2-147">Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-147">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="ec9f2-148">De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-148">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="ec9f2-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ec9f2-149">-Confirm</span></span>
<span data-ttu-id="ec9f2-150">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ec9f2-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ec9f2-151">-WhatIf</span></span>
<span data-ttu-id="ec9f2-152">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ec9f2-153">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ec9f2-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ec9f2-154">CommonParameters</span></span>
<span data-ttu-id="ec9f2-155">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ec9f2-156">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ec9f2-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ec9f2-157">INVOER</span><span class="sxs-lookup"><span data-stu-id="ec9f2-157">INPUTS</span></span>

### <span data-ttu-id="ec9f2-158">Geen</span><span class="sxs-lookup"><span data-stu-id="ec9f2-158">None</span></span>

## <span data-ttu-id="ec9f2-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ec9f2-159">OUTPUTS</span></span>

### <span data-ttu-id="ec9f2-160">Geen</span><span class="sxs-lookup"><span data-stu-id="ec9f2-160">None</span></span>

## <span data-ttu-id="ec9f2-161">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ec9f2-161">NOTES</span></span>

## <span data-ttu-id="ec9f2-162">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ec9f2-162">RELATED LINKS</span></span>

[<span data-ttu-id="ec9f2-163">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="ec9f2-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="ec9f2-164">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="ec9f2-164">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="ec9f2-165">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="ec9f2-165">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)
