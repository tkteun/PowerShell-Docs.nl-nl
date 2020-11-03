---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/update-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-DscConfiguration
ms.openlocfilehash: 13365902ab317a3daa41b9a951d5e2fa6e4f1b37
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250340"
---
# <span data-ttu-id="b2910-103">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2910-103">Update-DscConfiguration</span></span>

## <span data-ttu-id="b2910-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b2910-104">SYNOPSIS</span></span>
<span data-ttu-id="b2910-105">Controleert de pull-server op een bijgewerkte configuratie en past deze toe.</span><span class="sxs-lookup"><span data-stu-id="b2910-105">Checks the pull server for an updated configuration and applies it.</span></span>

## <span data-ttu-id="b2910-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b2910-106">SYNTAX</span></span>

### <span data-ttu-id="b2910-107">ComputerNameSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="b2910-107">ComputerNameSet (Default)</span></span>

```
Update-DscConfiguration [-Wait] [-JobName <String>] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b2910-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="b2910-108">CimSessionSet</span></span>

```
Update-DscConfiguration [-Wait] [-JobName <String>] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b2910-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b2910-109">DESCRIPTION</span></span>
<span data-ttu-id="b2910-110">De `Update-DscConfiguration` cmdlet maakt verbinding met een pull-server, downloadt de configuratie als deze afwijkt van wat er op het knoop punt staat en past de configuratie vervolgens toe op de computer.</span><span class="sxs-lookup"><span data-stu-id="b2910-110">The `Update-DscConfiguration` cmdlet connects to a pull server, downloads the configuration if it differs from what is current on the node, and then applies the configuration to the computer.</span></span>

<span data-ttu-id="b2910-111">Deze cmdlet is alleen beschikbaar als onderdeel van het [Update pakket van November 2014 voor Windows RT 8,1, Windows 8,1 en Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) uit de Microsoft ondersteuning-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="b2910-111">This cmdlet is available only as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span>

## <span data-ttu-id="b2910-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b2910-112">EXAMPLES</span></span>

### <span data-ttu-id="b2910-113">Voor beeld 1: een configuratie bijwerken</span><span class="sxs-lookup"><span data-stu-id="b2910-113">Example 1: Update a configuration</span></span>

```
PS C:\> Update-DscConfiguration -Wait -Verbose
```

<span data-ttu-id="b2910-114">Nadat u deze opdracht hebt uitgevoerd, maakt de server verbinding met de geregistreerde pull-service, downloadt de meest recente toegewezen configuratie en past deze vervolgens toe.</span><span class="sxs-lookup"><span data-stu-id="b2910-114">After running this command, the server will connect to the registered pull service, download the latest assigned configuration, and then apply it.</span></span>
<span data-ttu-id="b2910-115">De para meters-wait en-verbose zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="b2910-115">The -Wait and -Verbose parameters are optional.</span></span>
<span data-ttu-id="b2910-116">Wanneer u interactief werkt, kunt u met deze para meters realtime feedback geven over de voortgang en het slagen of mislukken bij het Toep assen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="b2910-116">When working interactively, these parameters combined enable real-time feedback about progress and success or failure when applying the configuration.</span></span>

### <span data-ttu-id="b2910-117">Voor beeld 2: een configuratie bijwerken door verbinding te maken via een CIM-sessie</span><span class="sxs-lookup"><span data-stu-id="b2910-117">Example 2: Update a configuration by connecting over a CIM session</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Update-DscConfiguration -CimSession $Session -Wait
```

<span data-ttu-id="b2910-118">Met de eerste opdracht maakt u een CIM-sessie met behulp van de cmdlet **New-CimSession** en slaat u het **CimSession** -object op in de variabele $Session.</span><span class="sxs-lookup"><span data-stu-id="b2910-118">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="b2910-119">De opdracht vraagt u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="b2910-119">The command prompts you for a password.</span></span>
<span data-ttu-id="b2910-120">Typ `Get-Help New-CimSession` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b2910-120">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="b2910-121">Met de tweede opdracht wordt de computer die is opgegeven in de **CimSession** die is opgeslagen in $Session, bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="b2910-121">The second command updates the computer specified in the **CimSession** stored in $Session.</span></span>
<span data-ttu-id="b2910-122">Met de opdracht wordt de *wait* -para meter opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b2910-122">The command specifies the *Wait* parameter.</span></span>
<span data-ttu-id="b2910-123">De console accepteert geen aanvullende opdrachten totdat de huidige opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="b2910-123">The console does not accept additional commands until the current command finishes.</span></span>

## <span data-ttu-id="b2910-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b2910-124">PARAMETERS</span></span>

### <span data-ttu-id="b2910-125">-CimSession</span><span class="sxs-lookup"><span data-stu-id="b2910-125">-CimSession</span></span>
<span data-ttu-id="b2910-126">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="b2910-126">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="b2910-127">Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="b2910-127">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="b2910-128">De standaard waarde is de huidige sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b2910-128">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="b2910-129">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b2910-129">-ComputerName</span></span>
<span data-ttu-id="b2910-130">Hiermee geeft u een matrix van computer namen op.</span><span class="sxs-lookup"><span data-stu-id="b2910-130">Specifies an array of computer names.</span></span>
<span data-ttu-id="b2910-131">Met de cmdlet worden de configuratie-instellingen toegepast op de computers die door deze para meter worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b2910-131">The cmdlet applies the configuration settings to the computers that this parameter specifies.</span></span>

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

### <span data-ttu-id="b2910-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="b2910-132">-Credential</span></span>
<span data-ttu-id="b2910-133">Hiermee geeft u een gebruikers naam en wacht woord op als een **PSCredential** -object voor de doel computer.</span><span class="sxs-lookup"><span data-stu-id="b2910-133">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="b2910-134">Als u een **PSCredential** -object wilt ophalen, gebruikt u de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="b2910-134">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="b2910-135">Typ `Get-Help Get-Credential` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b2910-135">For more information, type `Get-Help Get-Credential`.</span></span>

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

### <span data-ttu-id="b2910-136">-JobName</span><span class="sxs-lookup"><span data-stu-id="b2910-136">-JobName</span></span>
<span data-ttu-id="b2910-137">Hiermee geeft u een beschrijvende naam voor een taak op.</span><span class="sxs-lookup"><span data-stu-id="b2910-137">Specifies a friendly name for a job.</span></span>
<span data-ttu-id="b2910-138">Als u deze para meter opgeeft, wordt de cmdlet uitgevoerd als een taak en wordt een **taak** object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b2910-138">If you specify this parameter, the cmdlet runs as a job, and it returns a **Job** object.</span></span>

<span data-ttu-id="b2910-139">Windows Power shell wijst standaard de naam JobN toe, waarbij N een geheel getal is.</span><span class="sxs-lookup"><span data-stu-id="b2910-139">By default, Windows PowerShell assigns the name JobN where N is an integer.</span></span>

<span data-ttu-id="b2910-140">Als u de *wait* -para meter opgeeft, moet u deze para meter niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="b2910-140">If you specify the *Wait* parameter, do not specify this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2910-141">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b2910-141">-ThrottleLimit</span></span>
<span data-ttu-id="b2910-142">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2910-142">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="b2910-143">Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b2910-143">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="b2910-144">De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="b2910-144">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="b2910-145">-Wachten</span><span class="sxs-lookup"><span data-stu-id="b2910-145">-Wait</span></span>
<span data-ttu-id="b2910-146">Geeft aan dat de cmdlet de console blokkeert totdat alle configuratie taken zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="b2910-146">Indicates that the cmdlet blocks the console until it finishes all configuration tasks.</span></span>

<span data-ttu-id="b2910-147">Als u deze para meter opgeeft, moet u de para meter *JobName* niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="b2910-147">If you specify this parameter, do not specify the *JobName* parameter.</span></span>

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

### <span data-ttu-id="b2910-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b2910-148">-Confirm</span></span>
<span data-ttu-id="b2910-149">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b2910-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b2910-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b2910-150">-WhatIf</span></span>
<span data-ttu-id="b2910-151">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b2910-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b2910-152">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b2910-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b2910-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2910-153">CommonParameters</span></span>
<span data-ttu-id="b2910-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b2910-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b2910-155">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b2910-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b2910-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="b2910-156">INPUTS</span></span>

## <span data-ttu-id="b2910-157">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b2910-157">OUTPUTS</span></span>

## <span data-ttu-id="b2910-158">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b2910-158">NOTES</span></span>

## <span data-ttu-id="b2910-159">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b2910-159">RELATED LINKS</span></span>

[<span data-ttu-id="b2910-160">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="b2910-160">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="b2910-161">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2910-161">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="b2910-162">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="b2910-162">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="b2910-163">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2910-163">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="b2910-164">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2910-164">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="b2910-165">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2910-165">Stop-DscConfiguration</span></span>](Stop-DscConfiguration.md)

[<span data-ttu-id="b2910-166">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2910-166">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
