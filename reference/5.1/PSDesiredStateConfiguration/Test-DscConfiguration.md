---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-DscConfiguration
ms.openlocfilehash: 25c8bc61976ce3940e0b9bd949fa3ee60728450d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250341"
---
# <span data-ttu-id="08b4a-103">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="08b4a-103">Test-DscConfiguration</span></span>

## <span data-ttu-id="08b4a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="08b4a-104">SYNOPSIS</span></span>
<span data-ttu-id="08b4a-105">Test of de werkelijke configuratie van de knoop punten overeenkomt met de gewenste configuratie.</span><span class="sxs-lookup"><span data-stu-id="08b4a-105">Tests whether the actual configuration on the nodes matches the desired configuration.</span></span>

## <span data-ttu-id="08b4a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="08b4a-106">SYNTAX</span></span>

### <span data-ttu-id="08b4a-107">ComputerNameSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="08b4a-107">ComputerNameSet (Default)</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Detailed] [<CommonParameters>]
```

### <span data-ttu-id="08b4a-108">ComputerNameAndPathSet</span><span class="sxs-lookup"><span data-stu-id="08b4a-108">ComputerNameAndPathSet</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="08b4a-109">ComputerNameAndReferenceConfigurationSet</span><span class="sxs-lookup"><span data-stu-id="08b4a-109">ComputerNameAndReferenceConfigurationSet</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] -ReferenceConfiguration <String> [<CommonParameters>]
```

### <span data-ttu-id="08b4a-110">CimSessionAndPathSet</span><span class="sxs-lookup"><span data-stu-id="08b4a-110">CimSessionAndPathSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Path] <String>
 [<CommonParameters>]
```

### <span data-ttu-id="08b4a-111">CimSessionAndReferenceConfigurationSet</span><span class="sxs-lookup"><span data-stu-id="08b4a-111">CimSessionAndReferenceConfigurationSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob]
 -ReferenceConfiguration <String> [<CommonParameters>]
```

### <span data-ttu-id="08b4a-112">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="08b4a-112">CimSessionSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Detailed]
 [<CommonParameters>]
```

## <span data-ttu-id="08b4a-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="08b4a-113">DESCRIPTION</span></span>
<span data-ttu-id="08b4a-114">Met de cmdlet **test-DscConfiguration** wordt getest of de werkelijke configuratie van de knoop punten overeenkomt met de gewenste configuratie.</span><span class="sxs-lookup"><span data-stu-id="08b4a-114">The **Test-DscConfiguration** cmdlet tests whether the actual configuration on the nodes matches the desired configuration.</span></span>
<span data-ttu-id="08b4a-115">Geef op welke computers u wilt testen configuraties met behulp van computer namen of Common Information Model (CIM)-sessies.</span><span class="sxs-lookup"><span data-stu-id="08b4a-115">Specify which computers for which you want to test configurations by using computer names or Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="08b4a-116">Als u geen doel computer opgeeft, test de cmdlet de configuratie van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="08b4a-116">If you do not specify a target computer, the cmdlet tests configuration of the local computer.</span></span>

<span data-ttu-id="08b4a-117">Als de gewenste en werkelijke configuraties overeenkomen, retourneert de cmdlet de teken reeks waarde ' True '.</span><span class="sxs-lookup"><span data-stu-id="08b4a-117">If the desired and actual configurations match, the cmdlet returns a string value of 'True'.</span></span>
<span data-ttu-id="08b4a-118">Anders wordt de teken reeks waarde ' false ' geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="08b4a-118">Otherwise, it returns a string value of 'False'.</span></span>

## <span data-ttu-id="08b4a-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="08b4a-119">EXAMPLES</span></span>

### <span data-ttu-id="08b4a-120">Voor beeld 1: configuratie testen voor de lokale computer</span><span class="sxs-lookup"><span data-stu-id="08b4a-120">Example 1: Test configuration for the local computer</span></span>

```
PS C:\> Test-DscConfiguration
```

<span data-ttu-id="08b4a-121">Met deze opdracht wordt de configuratie voor de lokale computer getest.</span><span class="sxs-lookup"><span data-stu-id="08b4a-121">This command tests configuration for the local computer.</span></span>

### <span data-ttu-id="08b4a-122">Voor beeld 2: configuratie testen voor een opgegeven computer</span><span class="sxs-lookup"><span data-stu-id="08b4a-122">Example 2: Test configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Test-DscConfiguration -CimSession $Session
```

<span data-ttu-id="08b4a-123">Dit voor beeld test configuratie van een computer die is opgegeven door een CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="08b4a-123">This example test configuration from a computer specified by a CIM session.</span></span>
<span data-ttu-id="08b4a-124">In het voor beeld wordt een CIM-sessie voor een computer met de naam Server01 gemaakt voor gebruik met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="08b4a-124">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="08b4a-125">U kunt ook een matrix met CIM-sessies maken om de cmdlet op meerdere opgegeven computers toe te passen.</span><span class="sxs-lookup"><span data-stu-id="08b4a-125">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="08b4a-126">Met de eerste opdracht maakt u een CIM-sessie met behulp van de cmdlet **New-CimSession** en slaat u het **CimSession** -object op in de variabele $Session.</span><span class="sxs-lookup"><span data-stu-id="08b4a-126">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="08b4a-127">De opdracht vraagt u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="08b4a-127">The command prompts you for a password.</span></span>
<span data-ttu-id="08b4a-128">Typ `Get-Help New-CimSession` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="08b4a-128">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="08b4a-129">Met de tweede opdracht wordt de configuratie getest voor de computers die worden geïdentificeerd door de **CimSession** -objecten die zijn opgeslagen in de variabele $Session, in dit geval de computer met de naam Server01.</span><span class="sxs-lookup"><span data-stu-id="08b4a-129">The second command tests configuration for the computers identified by the **CimSession** objects stored in the $Session variable, in this case, the computer named Server01.</span></span>

### <span data-ttu-id="08b4a-130">Voor beeld 3: test configuraties met gedetailleerde resultaten</span><span class="sxs-lookup"><span data-stu-id="08b4a-130">Example 3: Test configurations with detailed results</span></span>

```
PS C:\> Test-DscConfiguration -ComputerName "Server01", "Server02", "Server03" -Detailed
```

<span data-ttu-id="08b4a-131">Met deze opdracht worden configuraties getest voor een set computers die is opgegeven door de para meter *ComputerName* en wordt gedetailleerde informatie geretourneerd die de algehele status bevat, resources die de gewenste status hebben, resources die niet de gewenste status en computer naam hebben.</span><span class="sxs-lookup"><span data-stu-id="08b4a-131">This command tests configurations for a set of computers specified by the *ComputerName* parameter and returns detailed information that includes the overall state, resources that are in the desired state, resources that are not in the desired state and computer name.</span></span>

### <span data-ttu-id="08b4a-132">Voor beeld 4: test configuraties die zijn opgegeven in een map</span><span class="sxs-lookup"><span data-stu-id="08b4a-132">Example 4: Test configurations specified in a folder</span></span>

```
PS C:\> Test-DscConfiguration -Path "C:\Dsc\Configurations"
```

<span data-ttu-id="08b4a-133">Met deze opdracht worden configuraties getest die zijn gedefinieerd in een map die is opgegeven door de para meter *Path* .</span><span class="sxs-lookup"><span data-stu-id="08b4a-133">This command tests configurations that are defined in a folder specified by the *Path* parameter.</span></span>
<span data-ttu-id="08b4a-134">De configuraties worden getest op basis van een set computers, die elk worden geïdentificeerd door de bestands naam van het configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="08b4a-134">The configurations are tested against a set of computers, each identified by the file name of the configuration file.</span></span>

### <span data-ttu-id="08b4a-135">Voor beeld 5: test configuraties die zijn opgegeven in een bestand</span><span class="sxs-lookup"><span data-stu-id="08b4a-135">Example 5: Test configurations specified in a file</span></span>

```
PS C:\> Test-DscConfiguration -ReferenceConfiguration "C:\Dsc\Configurations\WebServer.mof" -ComputerName "Server01", "Server02", "Server03"
```

<span data-ttu-id="08b4a-136">Met deze opdracht test u een configuratie die is gedefinieerd in een bestand op basis van een set computers die is opgegeven door de para meter *ComputerName* .</span><span class="sxs-lookup"><span data-stu-id="08b4a-136">This command tests a configuration defined in a file against a set of computers specified by the *ComputerName* parameter.</span></span>

## <span data-ttu-id="08b4a-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="08b4a-137">PARAMETERS</span></span>

### <span data-ttu-id="08b4a-138">-AsJob</span><span class="sxs-lookup"><span data-stu-id="08b4a-138">-AsJob</span></span>
<span data-ttu-id="08b4a-139">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="08b4a-139">Indicates that this cmdlet runs the command as a background job.</span></span>

<span data-ttu-id="08b4a-140">Als u de para meter *AsJob* opgeeft, retourneert de opdracht een object dat de taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="08b4a-140">If you specify the *AsJob* parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span>
<span data-ttu-id="08b4a-141">U kunt in de sessie blijven werken totdat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="08b4a-141">You can continue to work in the session until the job finishes.</span></span>
<span data-ttu-id="08b4a-142">De taak wordt gemaakt op de lokale computer en de resultaten van externe computers worden automatisch geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="08b4a-142">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="08b4a-143">Gebruik de taak-cmdlets om de taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="08b4a-143">To manage the job, use the Job cmdlets.</span></span>
<span data-ttu-id="08b4a-144">Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="08b4a-144">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="08b4a-145">Als u deze para meter wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang en op Windows Vista en latere versies van het Windows-besturings systeem, moet u Windows Power shell openen met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="08b4a-145">To use this parameter, the local and remote computers must be configured for remoting, and on Windows Vista and later versions of the Windows operating system, you must open Windows PowerShell with the Run as administrator option.</span></span>
<span data-ttu-id="08b4a-146">Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="08b4a-146">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="08b4a-147">Zie [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)voor meer informatie over Windows Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="08b4a-147">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="08b4a-148">-CimSession</span><span class="sxs-lookup"><span data-stu-id="08b4a-148">-CimSession</span></span>
<span data-ttu-id="08b4a-149">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="08b4a-149">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="08b4a-150">Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="08b4a-150">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="08b4a-151">De standaard waarde is de huidige sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="08b4a-151">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndReferenceConfigurationSet, CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="08b4a-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="08b4a-152">-ComputerName</span></span>
<span data-ttu-id="08b4a-153">Hiermee geeft u een matrix met computer namen op waarop met deze cmdlet de configuratie wordt getest.</span><span class="sxs-lookup"><span data-stu-id="08b4a-153">Specifies an array of computer names on which this cmdlet tests the configuration.</span></span>
<span data-ttu-id="08b4a-154">De cmdlet test het configuratie document op de locatie die is opgegeven door de para meter *Path* naar deze computers.</span><span class="sxs-lookup"><span data-stu-id="08b4a-154">The cmdlet tests the configuration document in the location specified by the *Path* parameter to these computers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="08b4a-155">-Credential</span><span class="sxs-lookup"><span data-stu-id="08b4a-155">-Credential</span></span>
<span data-ttu-id="08b4a-156">Hiermee geeft u een gebruikers naam en wacht woord op als een **PSCredential** -object voor de doel computer.</span><span class="sxs-lookup"><span data-stu-id="08b4a-156">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="08b4a-157">Als u een **PSCredential** -object wilt ophalen, gebruikt u de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="08b4a-157">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="08b4a-158">Typ `Get-Help Get-Credential` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="08b4a-158">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="08b4a-159">-Gedetailleerd</span><span class="sxs-lookup"><span data-stu-id="08b4a-159">-Detailed</span></span>
<span data-ttu-id="08b4a-160">Geeft aan dat deze cmdlet een gedetailleerd resultaat retourneert van het vergelijken van het configuratie document met de gewenste status van de knoop punten.</span><span class="sxs-lookup"><span data-stu-id="08b4a-160">Indicates that this cmdlet returns a detailed result of comparing the configuration document with the desired state of the nodes.</span></span>
<span data-ttu-id="08b4a-161">Het resultaat bevat informatie zoals de algemene status, resources met de gewenste status, resources die niet de gewenste status hebben en de computer naam.</span><span class="sxs-lookup"><span data-stu-id="08b4a-161">The result includes information such as overall state, resources that are in the desired state, resources that are not in desired state, and computer name.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameSet, CimSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="08b4a-162">-Path</span><span class="sxs-lookup"><span data-stu-id="08b4a-162">-Path</span></span>
<span data-ttu-id="08b4a-163">Hiermee geeft u het pad op van een map die configuratie document bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="08b4a-163">Specifies the path of a folder that contains configuration document files.</span></span>
<span data-ttu-id="08b4a-164">De cmdlet test de configuratie op basis van de gewenste status van de computers die zijn opgegeven door de para meter *ComputerName* of *CimSession* .</span><span class="sxs-lookup"><span data-stu-id="08b4a-164">The cmdlet tests the configuration against the desired state of computers specified by the *ComputerName* or *CimSession* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="08b4a-165">-ReferenceConfiguration</span><span class="sxs-lookup"><span data-stu-id="08b4a-165">-ReferenceConfiguration</span></span>
<span data-ttu-id="08b4a-166">Hiermee geeft u het pad van het configuratie document bestand.</span><span class="sxs-lookup"><span data-stu-id="08b4a-166">Specifies the path of the configuration document file.</span></span>
<span data-ttu-id="08b4a-167">Met deze cmdlet wordt de configuratie getest op basis van de werkelijke status van de computers die zijn opgegeven door de para meter *ComputerName* of *CimSession* .</span><span class="sxs-lookup"><span data-stu-id="08b4a-167">This cmdlet tests the configuration against the actual state of computers specified by the *ComputerName* or *CimSession* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndReferenceConfigurationSet, CimSessionAndReferenceConfigurationSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="08b4a-168">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="08b4a-168">-ThrottleLimit</span></span>
<span data-ttu-id="08b4a-169">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="08b4a-169">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="08b4a-170">Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="08b4a-170">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="08b4a-171">De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="08b4a-171">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="08b4a-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="08b4a-172">CommonParameters</span></span>
<span data-ttu-id="08b4a-173">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="08b4a-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="08b4a-174">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="08b4a-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="08b4a-175">INVOER</span><span class="sxs-lookup"><span data-stu-id="08b4a-175">INPUTS</span></span>

## <span data-ttu-id="08b4a-176">UITVOER</span><span class="sxs-lookup"><span data-stu-id="08b4a-176">OUTPUTS</span></span>

## <span data-ttu-id="08b4a-177">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="08b4a-177">NOTES</span></span>

## <span data-ttu-id="08b4a-178">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="08b4a-178">RELATED LINKS</span></span>

[<span data-ttu-id="08b4a-179">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="08b4a-179">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="08b4a-180">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="08b4a-180">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="08b4a-181">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="08b4a-181">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="08b4a-182">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="08b4a-182">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="08b4a-183">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="08b4a-183">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)
