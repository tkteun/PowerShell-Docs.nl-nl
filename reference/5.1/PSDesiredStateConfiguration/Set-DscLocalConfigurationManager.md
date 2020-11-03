---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 04/29/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/set-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-DscLocalConfigurationManager
ms.openlocfilehash: 0d35aa56a52f0e6c17abd0e7b2707869e780324c
ms.sourcegitcommit: 0d4d3e47f6979876550591f62061096e7a568f7e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/11/2020
ms.locfileid: "93251437"
---
# <span data-ttu-id="83ee2-103">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="83ee2-103">Set-DscLocalConfigurationManager</span></span>

## <span data-ttu-id="83ee2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="83ee2-104">SYNOPSIS</span></span>

<span data-ttu-id="83ee2-105">Hiermee worden lokale Configuration Manager (LCM)-instellingen toegepast op knoop punten.</span><span class="sxs-lookup"><span data-stu-id="83ee2-105">Applies Local Configuration Manager (LCM) settings to nodes.</span></span>

## <span data-ttu-id="83ee2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="83ee2-106">SYNTAX</span></span>

### <span data-ttu-id="83ee2-107">ComputerNameSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="83ee2-107">ComputerNameSet (Default)</span></span>

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="83ee2-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="83ee2-108">CimSessionSet</span></span>

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="83ee2-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="83ee2-109">DESCRIPTION</span></span>

<span data-ttu-id="83ee2-110">`Set-DscLocalConfigurationManager`Met de cmdlet worden de instellingen van de LCM of meta configuratie toegepast op knoop punten.</span><span class="sxs-lookup"><span data-stu-id="83ee2-110">The `Set-DscLocalConfigurationManager` cmdlet applies LCM settings, or meta-configuration, to nodes.</span></span> <span data-ttu-id="83ee2-111">Geef computers op door computer namen op te geven of door Common Information Model (CIM)-sessies te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="83ee2-111">Specify computers by specifying computer names or by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="83ee2-112">Als u geen doel computer opgeeft, past de cmdlet instellingen toe op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="83ee2-112">If you do not specify a target computer, the cmdlet applies settings to the local computer.</span></span>

## <span data-ttu-id="83ee2-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="83ee2-113">EXAMPLES</span></span>

### <span data-ttu-id="83ee2-114">Voor beeld 1: instellingen voor de LCM Toep assen</span><span class="sxs-lookup"><span data-stu-id="83ee2-114">Example 1: Apply LCM settings</span></span>

```
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="83ee2-115">Met deze opdracht worden de instellingen van de ICM van `C:\DSC\Configurations\` op de doel knooppunten toegepast.</span><span class="sxs-lookup"><span data-stu-id="83ee2-115">This command applies the LCM settings from `C:\DSC\Configurations\` to the targeted nodes.</span></span> <span data-ttu-id="83ee2-116">Nadat de instellingen zijn ontvangen, worden ze door de LCM verwerkt.</span><span class="sxs-lookup"><span data-stu-id="83ee2-116">After receiving the settings, LCM processes them.</span></span>

> [!WARNING]
> <span data-ttu-id="83ee2-117">Als er meerdere META mof's zijn voor dezelfde computer die is opgeslagen in de opgegeven map, wordt alleen de eerste meta MOF toegepast.</span><span class="sxs-lookup"><span data-stu-id="83ee2-117">If there are multiple meta mofs for the same computer stored in the specified folder, only the first meta mof will be applied.</span></span>

### <span data-ttu-id="83ee2-118">Voor beeld 2: instellingen voor de LCM Toep assen met behulp van een CIM-sessie</span><span class="sxs-lookup"><span data-stu-id="83ee2-118">Example 2: Apply LCM settings by using a CIM session</span></span>

```
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\" -CimSession $Session
```

<span data-ttu-id="83ee2-119">In dit voor beeld worden de instellingen van de LCM toegepast op een computer en worden de instellingen toegepast.</span><span class="sxs-lookup"><span data-stu-id="83ee2-119">This example applies LCM settings to a computer and applies the settings.</span></span> <span data-ttu-id="83ee2-120">In het voor beeld wordt een CIM-sessie voor een computer met de naam Server01 gemaakt voor gebruik met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="83ee2-120">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span> <span data-ttu-id="83ee2-121">U kunt ook een matrix met CIM-sessies maken om de cmdlet op meerdere opgegeven computers toe te passen.</span><span class="sxs-lookup"><span data-stu-id="83ee2-121">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="83ee2-122">Met de eerste opdracht maakt u een CIM-sessie met behulp van de `New-CimSession` cmdlet en slaat u vervolgens het **CimSession** -object op in de `$Session` variabele.</span><span class="sxs-lookup"><span data-stu-id="83ee2-122">The first command creates a CIM session by using the `New-CimSession` cmdlet, and then stores the **CimSession** object in the `$Session` variable.</span></span> <span data-ttu-id="83ee2-123">De opdracht vraagt u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="83ee2-123">The command prompts you for a password.</span></span> <span data-ttu-id="83ee2-124">Typ `Get-Help New-CimSession` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="83ee2-124">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="83ee2-125">Met de tweede opdracht worden de instellingen voor de LCM van het doel knooppunt toegepast `C:\DSC\Configurations\` op de computer die wordt geïdentificeerd door de **CimSession** -objecten die zijn opgeslagen in de `$Session` variabele.</span><span class="sxs-lookup"><span data-stu-id="83ee2-125">The second command applies LCM settings for the targeted node from `C:\DSC\Configurations\` to the computer identified by the **CimSession** objects stored in the `$Session` variable.</span></span> <span data-ttu-id="83ee2-126">In dit voor beeld `$Session` bevat de variabele alleen een CIM-sessie voor de computer met de naam Server01.</span><span class="sxs-lookup"><span data-stu-id="83ee2-126">In this example, the `$Session` variable contains a CIM session only for the computer named Server01.</span></span> <span data-ttu-id="83ee2-127">Met de opdracht worden de instellingen toegepast.</span><span class="sxs-lookup"><span data-stu-id="83ee2-127">The command applies the settings.</span></span> <span data-ttu-id="83ee2-128">Nadat de instellingen zijn ontvangen, worden ze door de LCM verwerkt.</span><span class="sxs-lookup"><span data-stu-id="83ee2-128">After receiving the settings, LCM processes them.</span></span>

## <span data-ttu-id="83ee2-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="83ee2-129">PARAMETERS</span></span>

### <span data-ttu-id="83ee2-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="83ee2-130">-CimSession</span></span>

<span data-ttu-id="83ee2-131">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="83ee2-131">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="83ee2-132">Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) of [Get-CimSession](/powershell/module/CimCmdlets/Get-CimSession) .</span><span class="sxs-lookup"><span data-stu-id="83ee2-132">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) or [Get-CimSession](/powershell/module/CimCmdlets/Get-CimSession) cmdlet.</span></span>
<span data-ttu-id="83ee2-133">De standaard waarde is de huidige sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="83ee2-133">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="83ee2-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="83ee2-134">-ComputerName</span></span>

<span data-ttu-id="83ee2-135">Hiermee geeft u een matrix van computer namen op.</span><span class="sxs-lookup"><span data-stu-id="83ee2-135">Specifies an array of computer names.</span></span> <span data-ttu-id="83ee2-136">Deze para meter beperkt de computers die meta-configuratie documenten hebben in de para meter **Path** tot die in de matrix zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="83ee2-136">This parameter restricts the computers that have meta-configuration documents in the **Path** parameter to those specified in the array.</span></span>

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

### <span data-ttu-id="83ee2-137">-Credential</span><span class="sxs-lookup"><span data-stu-id="83ee2-137">-Credential</span></span>

<span data-ttu-id="83ee2-138">Hiermee geeft u een gebruikers naam en wacht woord op als een **PSCredential** -object voor de doel computer.</span><span class="sxs-lookup"><span data-stu-id="83ee2-138">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span> <span data-ttu-id="83ee2-139">Als u een **PSCredential** -object wilt ophalen, gebruikt u de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="83ee2-139">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span> <span data-ttu-id="83ee2-140">Typ `Get-Help Get-Credential` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="83ee2-140">For more information, type `Get-Help Get-Credential`.</span></span>

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

### <span data-ttu-id="83ee2-141">-Force</span><span class="sxs-lookup"><span data-stu-id="83ee2-141">-Force</span></span>

<span data-ttu-id="83ee2-142">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="83ee2-142">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="83ee2-143">-Path</span><span class="sxs-lookup"><span data-stu-id="83ee2-143">-Path</span></span>

<span data-ttu-id="83ee2-144">Hiermee geeft u een bestandspad van een map met bestanden met configuratie-instellingen.</span><span class="sxs-lookup"><span data-stu-id="83ee2-144">Specifies a file path of a folder that contains configuration settings files.</span></span> <span data-ttu-id="83ee2-145">De cmdlet publiceert en past deze instellingen van de ICM toe op computers met instellingen bestanden in het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="83ee2-145">The cmdlet publishes and applies these LCM settings to computers that have settings files in the specified path.</span></span> <span data-ttu-id="83ee2-146">Elk doel knooppunt moet een instellingen bestand hebben met de volgende indeling: `NetBIOS Name.meta.mof` .</span><span class="sxs-lookup"><span data-stu-id="83ee2-146">Each target node must have a settings file of the following format: `NetBIOS Name.meta.mof`.</span></span>

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

### <span data-ttu-id="83ee2-147">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="83ee2-147">-ThrottleLimit</span></span>

<span data-ttu-id="83ee2-148">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="83ee2-148">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span> <span data-ttu-id="83ee2-149">Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="83ee2-149">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span> <span data-ttu-id="83ee2-150">De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="83ee2-150">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="83ee2-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="83ee2-151">-Confirm</span></span>

<span data-ttu-id="83ee2-152">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="83ee2-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="83ee2-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="83ee2-153">-WhatIf</span></span>

<span data-ttu-id="83ee2-154">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="83ee2-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="83ee2-155">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="83ee2-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="83ee2-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="83ee2-156">CommonParameters</span></span>

<span data-ttu-id="83ee2-157">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="83ee2-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="83ee2-158">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="83ee2-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="83ee2-159">INVOER</span><span class="sxs-lookup"><span data-stu-id="83ee2-159">INPUTS</span></span>

## <span data-ttu-id="83ee2-160">UITVOER</span><span class="sxs-lookup"><span data-stu-id="83ee2-160">OUTPUTS</span></span>

## <span data-ttu-id="83ee2-161">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="83ee2-161">NOTES</span></span>

## <span data-ttu-id="83ee2-162">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="83ee2-162">RELATED LINKS</span></span>

[<span data-ttu-id="83ee2-163">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="83ee2-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="83ee2-164">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="83ee2-164">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)
