---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/publish-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-DscConfiguration
ms.openlocfilehash: 139de2bfdb88c443e7bc48d36e37e95644556bf5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250767"
---
# <span data-ttu-id="c80f6-103">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c80f6-103">Publish-DscConfiguration</span></span>

## <span data-ttu-id="c80f6-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c80f6-104">SYNOPSIS</span></span>
<span data-ttu-id="c80f6-105">Publiceert een DSC-configuratie naar een set computers.</span><span class="sxs-lookup"><span data-stu-id="c80f6-105">Publishes a DSC configuration to a set of computers.</span></span>

## <span data-ttu-id="c80f6-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c80f6-106">SYNTAX</span></span>

### <span data-ttu-id="c80f6-107">ComputerNameSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="c80f6-107">ComputerNameSet (Default)</span></span>

```
Publish-DscConfiguration [-Path] <String> [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c80f6-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="c80f6-108">CimSessionSet</span></span>

```
Publish-DscConfiguration [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c80f6-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c80f6-109">DESCRIPTION</span></span>
<span data-ttu-id="c80f6-110">De cmdlet **Publish-DscConfiguration** publiceert een configuratie document van de desired state Configuration (DSC) van Windows Power shell op een set computers.</span><span class="sxs-lookup"><span data-stu-id="c80f6-110">The **Publish-DscConfiguration** cmdlet publishes a Windows PowerShell Desired State Configuration (DSC) configuration document on set of computers.</span></span>
<span data-ttu-id="c80f6-111">Met deze cmdlet wordt de configuratie niet toegepast.</span><span class="sxs-lookup"><span data-stu-id="c80f6-111">This cmdlet does not apply the configuration.</span></span>
<span data-ttu-id="c80f6-112">Configuraties worden toegepast met behulp van de cmdlet Start-DscConfiguration als deze wordt gebruikt met de para meter *UseExisting* of wanneer de DSC-engine de consistentie cyclus uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c80f6-112">Configurations are applied by either the Start-DscConfiguration cmdlet when it is used with the *UseExisting* parameter or when the DSC engine runs its consistency cycle.</span></span>
<span data-ttu-id="c80f6-113">De DSC-engine wordt ook wel de lokale Configuration Manager (LCM) genoemd.</span><span class="sxs-lookup"><span data-stu-id="c80f6-113">The DSC engine is also known as the Local Configuration Manager (LCM).</span></span>

<span data-ttu-id="c80f6-114">Deze cmdlet is vooral handig wanneer er fragmenten van meerdere configuratie documenten worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="c80f6-114">This cmdlet is especially useful when fragments of multiple configuration documents are delivered.</span></span>
<span data-ttu-id="c80f6-115">Wanneer er meerdere fragmenten voor configuratie documenten worden geleverd, overschrijven ze de oudere configuratie document fragmenten.</span><span class="sxs-lookup"><span data-stu-id="c80f6-115">When multiple configuration documents fragments are delivered, they overwrite the older configuration document fragments.</span></span>

## <span data-ttu-id="c80f6-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c80f6-116">EXAMPLES</span></span>

### <span data-ttu-id="c80f6-117">Voor beeld 1: een configuratie naar een externe computer publiceren</span><span class="sxs-lookup"><span data-stu-id="c80f6-117">Example 1: Publish a configuration to a remote computer</span></span>

```
PS C:\> Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

<span data-ttu-id="c80f6-118">Met deze opdracht wordt een configuratie naar een externe computer gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="c80f6-118">This command publishes a configuration to a remote computer.</span></span>
<span data-ttu-id="c80f6-119">De gebruiker die de cmdlet uitvoert, moet beheerder zijn op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="c80f6-119">The user who runs the cmdlet should be administrator on the remote computer.</span></span>

## <span data-ttu-id="c80f6-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c80f6-120">PARAMETERS</span></span>

### <span data-ttu-id="c80f6-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="c80f6-121">-CimSession</span></span>
<span data-ttu-id="c80f6-122">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="c80f6-122">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="c80f6-123">Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="c80f6-123">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="c80f6-124">De standaard waarde is de huidige sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c80f6-124">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c80f6-125">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="c80f6-125">-ComputerName</span></span>
<span data-ttu-id="c80f6-126">Hiermee geeft u een of meer computers waarop deze cmdlet de configuratie publiceert.</span><span class="sxs-lookup"><span data-stu-id="c80f6-126">Specifies one or more computers on which this cmdlet publishes the configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c80f6-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="c80f6-127">-Credential</span></span>
<span data-ttu-id="c80f6-128">Hiermee geeft u de referenties op die worden gebruikt voor toegang tot het doel apparaat.</span><span class="sxs-lookup"><span data-stu-id="c80f6-128">Specifies credentials that are used to access the target device.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c80f6-129">-Force</span><span class="sxs-lookup"><span data-stu-id="c80f6-129">-Force</span></span>
<span data-ttu-id="c80f6-130">Hiermee wordt de cmdlet geforceerd voltooid.</span><span class="sxs-lookup"><span data-stu-id="c80f6-130">Forces the cmdlet to finish.</span></span>
<span data-ttu-id="c80f6-131">Als de modus voor het vernieuwen van lokale Configuration Manager is ingesteld op PULL, wordt het gebruik van deze para meter gewijzigd in PUSH en wordt publicatie van de DSC-configuratie ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="c80f6-131">If the Local Configuration Manager refresh mode is set to PULL, usage of this parameter changes it to PUSH and enables publication of the DSC configuration.</span></span>
<span data-ttu-id="c80f6-132">Als er al een in behandeling zijnde DSC-configuratie bestaat, wordt het gebruik van deze para meter overschreven met een configuratie die in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="c80f6-132">Also, if a pending DSC configuration exists, usage of this parameter overwrites that pending configuration.</span></span>

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

### <span data-ttu-id="c80f6-133">-Path</span><span class="sxs-lookup"><span data-stu-id="c80f6-133">-Path</span></span>
<span data-ttu-id="c80f6-134">Hiermee geeft u een pad op dat configuraties bevat die moeten worden gepubliceerd op doel computers.</span><span class="sxs-lookup"><span data-stu-id="c80f6-134">Specifies a path that contains configurations to publish to target computers.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c80f6-135">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="c80f6-135">-ThrottleLimit</span></span>
<span data-ttu-id="c80f6-136">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c80f6-136">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="c80f6-137">Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c80f6-137">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="c80f6-138">De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="c80f6-138">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="c80f6-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c80f6-139">-Confirm</span></span>
<span data-ttu-id="c80f6-140">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c80f6-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c80f6-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c80f6-141">-WhatIf</span></span>
<span data-ttu-id="c80f6-142">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c80f6-142">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c80f6-143">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c80f6-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c80f6-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c80f6-144">CommonParameters</span></span>
<span data-ttu-id="c80f6-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c80f6-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c80f6-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c80f6-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c80f6-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="c80f6-147">INPUTS</span></span>

## <span data-ttu-id="c80f6-148">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c80f6-148">OUTPUTS</span></span>

## <span data-ttu-id="c80f6-149">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c80f6-149">NOTES</span></span>

## <span data-ttu-id="c80f6-150">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c80f6-150">RELATED LINKS</span></span>

[<span data-ttu-id="c80f6-151">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="c80f6-151">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="c80f6-152">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c80f6-152">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="c80f6-153">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="c80f6-153">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="c80f6-154">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c80f6-154">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="c80f6-155">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c80f6-155">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="c80f6-156">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c80f6-156">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
