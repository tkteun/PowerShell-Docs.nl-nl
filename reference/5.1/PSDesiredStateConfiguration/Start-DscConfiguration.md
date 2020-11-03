---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/start-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-DscConfiguration
ms.openlocfilehash: c34754aeb7fce99030cf4ddb235e3e7e8161f3eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250763"
---
# <span data-ttu-id="2db31-103">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2db31-103">Start-DscConfiguration</span></span>

## <span data-ttu-id="2db31-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2db31-104">SYNOPSIS</span></span>
<span data-ttu-id="2db31-105">Hiermee wordt configuratie op knoop punten toegepast.</span><span class="sxs-lookup"><span data-stu-id="2db31-105">Applies configuration to nodes.</span></span>

## <span data-ttu-id="2db31-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2db31-106">SYNTAX</span></span>

### <span data-ttu-id="2db31-107">ComputerNameAndPathSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="2db31-107">ComputerNameAndPathSet (Default)</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="2db31-108">CimSessionAndPathSet</span><span class="sxs-lookup"><span data-stu-id="2db31-108">CimSessionAndPathSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] -CimSession <CimSession[]> [-ThrottleLimit <Int32>]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2db31-109">ComputerNameAndUseExistingSet</span><span class="sxs-lookup"><span data-stu-id="2db31-109">ComputerNameAndUseExistingSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-UseExisting] [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2db31-110">CimSessionAndUseExistingSet</span><span class="sxs-lookup"><span data-stu-id="2db31-110">CimSessionAndUseExistingSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] -CimSession <CimSession[]> [-ThrottleLimit <Int32>] [-UseExisting]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2db31-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2db31-111">DESCRIPTION</span></span>
<span data-ttu-id="2db31-112">De cmdlet **Start-DscConfiguration** past configuratie toe op knoop punten.</span><span class="sxs-lookup"><span data-stu-id="2db31-112">The **Start-DscConfiguration** cmdlet applies configuration to nodes.</span></span>
<span data-ttu-id="2db31-113">Bij gebruik met de para meter *UseExisting* wordt de bestaande configuratie op de doel computer toegepast.</span><span class="sxs-lookup"><span data-stu-id="2db31-113">When used with the *UseExisting* parameter, the existing configuration on the target computer is applied.</span></span>
<span data-ttu-id="2db31-114">Geef op op welke computers u de configuratie wilt Toep assen door computer namen op te geven of door Common Information Model (CIM)-sessies te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2db31-114">Specify which computers that you want to apply configuration to by specifying computer names or by using Common Information Model (CIM) sessions.</span></span>

<span data-ttu-id="2db31-115">Deze cmdlet maakt standaard een taak en retourneert een **taak** object.</span><span class="sxs-lookup"><span data-stu-id="2db31-115">By default, this cmdlet creates a job and returns a **Job** object.</span></span>
<span data-ttu-id="2db31-116">Typ voor meer informatie over achtergrond taken `Get-Help about_Jobs` .</span><span class="sxs-lookup"><span data-stu-id="2db31-116">For more information about background jobs, type `Get-Help about_Jobs`.</span></span>
<span data-ttu-id="2db31-117">Als u deze cmdlet interactief wilt gebruiken, geeft u de *wait* -para meter op.</span><span class="sxs-lookup"><span data-stu-id="2db31-117">To use this cmdlet interactively, specify the *Wait* parameter.</span></span>

<span data-ttu-id="2db31-118">Geef de para meter *uitgebreid* op om details weer te geven van wat de cmdlet doet wanneer configuratie-instellingen worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="2db31-118">Specify the *Verbose* parameter to see details of what the cmdlet does when it applies configuration settings.</span></span>

## <span data-ttu-id="2db31-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2db31-119">EXAMPLES</span></span>

### <span data-ttu-id="2db31-120">Voor beeld 1: configuratie-instellingen Toep assen</span><span class="sxs-lookup"><span data-stu-id="2db31-120">Example 1: Apply configuration settings</span></span>

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="2db31-121">Met deze opdracht worden de configuratie-instellingen van C:\DSC\Configurations\ toegepast op elke computer met instellingen in die map.</span><span class="sxs-lookup"><span data-stu-id="2db31-121">This command applies the configuration settings from C:\DSC\Configurations\ to the every computer that has settings in that folder.</span></span>
<span data-ttu-id="2db31-122">Met de opdracht worden **taak** objecten geretourneerd voor elk doel knooppunt dat is geïmplementeerd op.</span><span class="sxs-lookup"><span data-stu-id="2db31-122">The command returns **Job** objects for each target node deployed to.</span></span>

### <span data-ttu-id="2db31-123">Voor beeld 2: configuratie-instellingen Toep assen en wachten tot de configuratie is voltooid</span><span class="sxs-lookup"><span data-stu-id="2db31-123">Example 2: Apply configuration settings and wait for configuration to complete</span></span>

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -Wait -Verbose
```

<span data-ttu-id="2db31-124">Met deze opdracht wordt de configuratie van C:\DSC\Configurations\ toegepast op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2db31-124">This command applies the configuration from C:\DSC\Configurations\ to the local computer.</span></span>
<span data-ttu-id="2db31-125">De opdracht retourneert **taak** objecten voor elk doel knooppunt dat is geïmplementeerd op, in dit geval alleen de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2db31-125">The command returns **Job** objects for each target node deployed to, in this case, just the local computer.</span></span>
<span data-ttu-id="2db31-126">In dit voor beeld wordt de *uitgebreide* para meter opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2db31-126">This example specifies the *Verbose* parameter.</span></span>
<span data-ttu-id="2db31-127">Daarom verzendt de opdracht berichten naar de console als deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2db31-127">Therefore, the command sends messages to the console as it proceeds.</span></span>
<span data-ttu-id="2db31-128">De opdracht bevat de *wait* -para meter.</span><span class="sxs-lookup"><span data-stu-id="2db31-128">The command includes the *Wait* parameter.</span></span>
<span data-ttu-id="2db31-129">Daarom kunt u de-console pas gebruiken als de opdracht alle configuratie taken heeft voltooid.</span><span class="sxs-lookup"><span data-stu-id="2db31-129">Therefore, you cannot use the console until the command finishes all configuration tasks.</span></span>

### <span data-ttu-id="2db31-130">Voor beeld 3: configuratie-instellingen Toep assen met behulp van een CIM-sessie</span><span class="sxs-lookup"><span data-stu-id="2db31-130">Example 3: Apply configuration settings by using a CIM session</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -CimSession $Session
```

<span data-ttu-id="2db31-131">In dit voor beeld worden configuratie-instellingen toegepast op een opgegeven computer.</span><span class="sxs-lookup"><span data-stu-id="2db31-131">This example applies configuration settings to a specified computer.</span></span>
<span data-ttu-id="2db31-132">In het voor beeld wordt een CIM-sessie voor een computer met de naam Server01 gemaakt voor gebruik met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2db31-132">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="2db31-133">U kunt ook een matrix met CIM-sessies maken om de cmdlet op meerdere opgegeven computers toe te passen.</span><span class="sxs-lookup"><span data-stu-id="2db31-133">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="2db31-134">Met de eerste opdracht maakt u een CIM-sessie met behulp van de cmdlet **New-CimSession** en slaat u het **CimSession** -object op in de variabele $Session.</span><span class="sxs-lookup"><span data-stu-id="2db31-134">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="2db31-135">De opdracht vraagt u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="2db31-135">The command prompts you for a password.</span></span>
<span data-ttu-id="2db31-136">Typ `Get-Help NewCimSession` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2db31-136">For more information, type `Get-Help NewCimSession`.</span></span>

<span data-ttu-id="2db31-137">Met de tweede opdracht worden de configuratie-instellingen van C:\DSC\Configurations\ toegepast op de computers die worden geïdentificeerd door de **CimSession** -objecten die zijn opgeslagen in de variabele $Session.</span><span class="sxs-lookup"><span data-stu-id="2db31-137">The second command applies the configuration settings from C:\DSC\Configurations\ to the computers identified by the **CimSession** objects stored in the $Session variable.</span></span>
<span data-ttu-id="2db31-138">In dit voor beeld bevat de variabele $Session alleen een CIM-sessie voor de computer met de naam Server01.</span><span class="sxs-lookup"><span data-stu-id="2db31-138">In this example, the $Session variable contains a CIM session only for the computer named Server01.</span></span>
<span data-ttu-id="2db31-139">De opdracht past de configuratie toe.</span><span class="sxs-lookup"><span data-stu-id="2db31-139">The command applies the configuration.</span></span>
<span data-ttu-id="2db31-140">De opdracht maakt **taak** objecten voor elke geconfigureerde computer.</span><span class="sxs-lookup"><span data-stu-id="2db31-140">The command creates **Job** objects for each configured computer.</span></span>

## <span data-ttu-id="2db31-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2db31-141">PARAMETERS</span></span>

### <span data-ttu-id="2db31-142">-CimSession</span><span class="sxs-lookup"><span data-stu-id="2db31-142">-CimSession</span></span>
<span data-ttu-id="2db31-143">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="2db31-143">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="2db31-144">Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="2db31-144">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="2db31-145">De standaard waarde is de huidige sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2db31-145">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2db31-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="2db31-146">-ComputerName</span></span>
<span data-ttu-id="2db31-147">Hiermee geeft u een matrix van computer namen op.</span><span class="sxs-lookup"><span data-stu-id="2db31-147">Specifies an array of computer names.</span></span>
<span data-ttu-id="2db31-148">Deze para meter beperkt de computers die configuratie documenten hebben in de para meter *Path* naar die zijn opgegeven in de matrix.</span><span class="sxs-lookup"><span data-stu-id="2db31-148">This parameter restricts the computers that have configuration documents in the *Path* parameter to those specified in the array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2db31-149">-Credential</span><span class="sxs-lookup"><span data-stu-id="2db31-149">-Credential</span></span>
<span data-ttu-id="2db31-150">Hiermee geeft u een gebruikers naam en wacht woord op als een **PSCredential** -object voor de doel computer.</span><span class="sxs-lookup"><span data-stu-id="2db31-150">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="2db31-151">Als u een **PSCredential** -object wilt ophalen, gebruikt u de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="2db31-151">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="2db31-152">Typ `Get-Help Get-Credential` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2db31-152">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2db31-153">-Force</span><span class="sxs-lookup"><span data-stu-id="2db31-153">-Force</span></span>
<span data-ttu-id="2db31-154">Hiermee wordt de configuratie bewerking gestopt die momenteel wordt uitgevoerd op de doel computer en wordt de nieuwe Start-Configuration bewerking gestart.</span><span class="sxs-lookup"><span data-stu-id="2db31-154">Stops the configuration operation currently running on the target computer and begins the new Start-Configuration operation.</span></span>
<span data-ttu-id="2db31-155">Als de eigenschap **RefreshMode** van de lokale Configuration Manager is ingesteld op **pull** , en als u deze para meter opgeeft, wordt deze gewijzigd in **Push**.</span><span class="sxs-lookup"><span data-stu-id="2db31-155">If the **RefreshMode** property of the Local Configuration Manager is set to **Pull** , specifying this parameter changes it to **Push**.</span></span>

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

### <span data-ttu-id="2db31-156">-JobName</span><span class="sxs-lookup"><span data-stu-id="2db31-156">-JobName</span></span>
<span data-ttu-id="2db31-157">Hiermee geeft u een beschrijvende naam voor een taak op.</span><span class="sxs-lookup"><span data-stu-id="2db31-157">Specifies a friendly name for a job.</span></span>
<span data-ttu-id="2db31-158">Als u deze para meter opgeeft, wordt de cmdlet uitgevoerd als een taak en wordt een **taak** object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2db31-158">If you specify this parameter, the cmdlet runs as a job, and it returns a **Job** object.</span></span>

<span data-ttu-id="2db31-159">Windows Power shell wijst standaard de naam JobN toe, waarbij N een geheel getal is.</span><span class="sxs-lookup"><span data-stu-id="2db31-159">By default, Windows PowerShell assigns the name JobN where N is an integer.</span></span>

<span data-ttu-id="2db31-160">Als u de *wait* -para meter opgeeft, moet u deze para meter niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="2db31-160">If you specify the *Wait* parameter, do not specify this parameter.</span></span>

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

### <span data-ttu-id="2db31-161">-Path</span><span class="sxs-lookup"><span data-stu-id="2db31-161">-Path</span></span>
<span data-ttu-id="2db31-162">Hiermee geeft u een bestandspad van een map met bestanden met configuratie-instellingen.</span><span class="sxs-lookup"><span data-stu-id="2db31-162">Specifies a file path of a folder that contains configuration settings files.</span></span>
<span data-ttu-id="2db31-163">Met deze cmdlet worden deze configuratie-instellingen gepubliceerd en toegepast op computers met instellingen bestanden in het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="2db31-163">This cmdlet publishes and applies these configuration settings to computers that have settings files in the specified path.</span></span>
<span data-ttu-id="2db31-164">Elk doel knooppunt moet een instellingen bestand hebben met de volgende indeling: NetBIOS name. mof.</span><span class="sxs-lookup"><span data-stu-id="2db31-164">Each target node must have a settings file of the following format: NetBIOS Name.mof.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2db31-165">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2db31-165">-ThrottleLimit</span></span>
<span data-ttu-id="2db31-166">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2db31-166">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="2db31-167">Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2db31-167">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="2db31-168">De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="2db31-168">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="2db31-169">-UseExisting</span><span class="sxs-lookup"><span data-stu-id="2db31-169">-UseExisting</span></span>
<span data-ttu-id="2db31-170">Geeft aan dat met deze cmdlet de bestaande configuratie wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="2db31-170">Indicates that this cmdlet applies the existing configuration.</span></span>
<span data-ttu-id="2db31-171">De configuratie kan bestaan op de doel computer met behulp van de cmdlet **Start-DscConfiguration** of op basis van de Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2db31-171">The configuration can exist on the target computer by enactment using **Start-DscConfiguration** or by publication using the Publish-DscConfiguration cmdlet.</span></span>

<span data-ttu-id="2db31-172">Lees de informatie in [What's New in Windows Power shell 5,0](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50) voordat u deze para meter voor deze cmdlet opgeeft.</span><span class="sxs-lookup"><span data-stu-id="2db31-172">Before you specify this parameter for this cmdlet, review the information in [What's New in Windows PowerShell 5.0](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50)</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameAndUseExistingSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2db31-173">-Wachten</span><span class="sxs-lookup"><span data-stu-id="2db31-173">-Wait</span></span>
<span data-ttu-id="2db31-174">Geeft aan dat de cmdlet de console blokkeert totdat alle configuratie taken zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="2db31-174">Indicates that the cmdlet blocks the console until it finishes all configuration tasks.</span></span>

<span data-ttu-id="2db31-175">Als u deze para meter opgeeft, moet u de para meter *JobName* niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="2db31-175">If you specify this parameter, do not specify the *JobName* parameter.</span></span>

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

### <span data-ttu-id="2db31-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2db31-176">-Confirm</span></span>
<span data-ttu-id="2db31-177">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2db31-177">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2db31-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2db31-178">-WhatIf</span></span>
<span data-ttu-id="2db31-179">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2db31-179">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2db31-180">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2db31-180">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2db31-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2db31-181">CommonParameters</span></span>
<span data-ttu-id="2db31-182">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2db31-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2db31-183">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2db31-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2db31-184">INVOER</span><span class="sxs-lookup"><span data-stu-id="2db31-184">INPUTS</span></span>

## <span data-ttu-id="2db31-185">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2db31-185">OUTPUTS</span></span>

## <span data-ttu-id="2db31-186">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2db31-186">NOTES</span></span>

## <span data-ttu-id="2db31-187">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2db31-187">RELATED LINKS</span></span>

[<span data-ttu-id="2db31-188">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="2db31-188">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="2db31-189">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2db31-189">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="2db31-190">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="2db31-190">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="2db31-191">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2db31-191">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="2db31-192">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2db31-192">Stop-DscConfiguration</span></span>](Stop-DscConfiguration.md)

[<span data-ttu-id="2db31-193">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2db31-193">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

[<span data-ttu-id="2db31-194">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2db31-194">Update-DscConfiguration</span></span>](Update-DscConfiguration.md)
