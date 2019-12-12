---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Configuraties voor een knooppunt toepassen, ophalen en testen
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941864"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="22524-103">Configuraties voor een knooppunt toepassen, ophalen en testen</span><span class="sxs-lookup"><span data-stu-id="22524-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="22524-104">In deze hand leiding wordt uitgelegd hoe u kunt werken met configuraties op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="22524-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="22524-105">Deze hand leiding is opgesplitst in de volgende stappen:</span><span class="sxs-lookup"><span data-stu-id="22524-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="22524-106">Een configuratie Toep assen</span><span class="sxs-lookup"><span data-stu-id="22524-106">Apply a Configuration</span></span>

<span data-ttu-id="22524-107">Om een configuratie toe te passen en te beheren, moeten we een '. MOF-bestand ' genereren.</span><span class="sxs-lookup"><span data-stu-id="22524-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="22524-108">De volgende code geeft een eenvoudige configuratie weer die in deze hand leiding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="22524-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

<span data-ttu-id="22524-109">Bij het compileren van deze configuratie worden twee '. MOF-bestanden ' geoogst.</span><span class="sxs-lookup"><span data-stu-id="22524-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="22524-110">Gebruik de cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) om een configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="22524-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="22524-111">Met de para meter `-Path` geeft u een map op waarin de MOF-bestanden zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="22524-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="22524-112">Als er geen `-Computername` is opgegeven, probeert `Start-DSCConfiguration` elke configuratie toe te passen op de computer naam die is opgegeven met de naam van het MOF-bestand (\<ComputerName\>. MOF).</span><span class="sxs-lookup"><span data-stu-id="22524-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="22524-113">Geef `-Verbose` op `Start-DSCConfiguration` om meer uitgebreide uitvoer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="22524-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="22524-114">Als `-Wait` niet is opgegeven, ziet u een taak die is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="22524-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="22524-115">De gemaakte taak heeft één **ChildJob** voor elk bestand met de naam. MOF dat is verwerkt door `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="22524-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="22524-116">Als een configuratie lange tijd in beslag neemt en u deze wilt stoppen, kunt u [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) gebruiken om de toepassing op het lokale knoop punt te stoppen.</span><span class="sxs-lookup"><span data-stu-id="22524-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="22524-117">Zodra het proces is voltooid, kunt u de status van de taken weer geven via het taak object dat wordt geretourneerd door [Get-job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="22524-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="22524-118">Als u de **uitgebreide** uitvoer wilt zien, gebruikt u de volgende opdrachten om de **uitgebreide** stroom voor elke **ChildJob**weer te geven.</span><span class="sxs-lookup"><span data-stu-id="22524-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="22524-119">Zie [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)voor meer informatie over Power shell-taken.</span><span class="sxs-lookup"><span data-stu-id="22524-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="22524-120">Vanaf Power shell 5,0 is de `-UseExisting` para meter toegevoegd aan `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="22524-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="22524-121">Als u `-UseExisting`opgeeft, geeft u de cmdlet de opdracht om de bestaande toegepaste configuratie te gebruiken in plaats van een opgegeven door de para meter `-Path`.</span><span class="sxs-lookup"><span data-stu-id="22524-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="22524-122">Een configuratie testen</span><span class="sxs-lookup"><span data-stu-id="22524-122">Test a Configuration</span></span>

<span data-ttu-id="22524-123">U kunt een momenteel toegepaste configuratie testen met [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="22524-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="22524-124">`Test-DSCConfiguration` wordt `True` geretourneerd als het knoop punt compatibel is en `False` als dat niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="22524-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="22524-125">Vanaf Power shell 5,0 is de para meter `-Detailed` toegevoegd waarmee een object wordt geretourneerd met verzamelingen voor **ResourcesInDesiredState** en **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="22524-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="22524-126">Vanaf Power shell 5,0 kunt u een configuratie testen zonder deze toe te passen.</span><span class="sxs-lookup"><span data-stu-id="22524-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="22524-127">De para meter `-ReferenceConfiguration` accepteert het pad van een '. MOF-bestand om het knoop punt te testen.</span><span class="sxs-lookup"><span data-stu-id="22524-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="22524-128">Er worden geen **set** -acties uitgevoerd op het knoop punt.</span><span class="sxs-lookup"><span data-stu-id="22524-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="22524-129">In Power Shell 4,0 zijn er tijdelijke oplossingen voor het testen van een configuratie zonder deze toe te passen, maar ze worden hier niet besproken.</span><span class="sxs-lookup"><span data-stu-id="22524-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="22524-130">Configuratie waarden ophalen</span><span class="sxs-lookup"><span data-stu-id="22524-130">Get Configuration Values</span></span>

<span data-ttu-id="22524-131">De cmdlet [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) retourneert de huidige waarden voor alle geconfigureerde resources in de momenteel toegepaste configuratie.</span><span class="sxs-lookup"><span data-stu-id="22524-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="22524-132">De uitvoer van de voorbeeld configuratie zou er als volgt uitzien als ze zijn toegepast.</span><span class="sxs-lookup"><span data-stu-id="22524-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a><span data-ttu-id="22524-133">Configuratie status ophalen</span><span class="sxs-lookup"><span data-stu-id="22524-133">Get Configuration Status</span></span>

<span data-ttu-id="22524-134">Vanaf Power shell 5,0 kunt u met de cmdlet [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) de geschiedenis van toegepaste configuraties weer geven in het knoop punt.</span><span class="sxs-lookup"><span data-stu-id="22524-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="22524-135">Power shell DSC houdt de laatste {{N}} configuraties bij die in de **Push** -of **pull** -modus worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="22524-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="22524-136">Dit omvat alle *consistentie* controles die door de LCM worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="22524-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="22524-137">`Get-DSCConfigurationStatus` wordt standaard alleen de laatste geschiedenis vermelding weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="22524-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="22524-138">Gebruik de para meter `-All` om alle geschiedenis van de configuratie status weer te geven.</span><span class="sxs-lookup"><span data-stu-id="22524-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="22524-139">De uitvoer wordt afgekapt voor het boogere.</span><span class="sxs-lookup"><span data-stu-id="22524-139">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a><span data-ttu-id="22524-140">Configuratie documenten beheren</span><span class="sxs-lookup"><span data-stu-id="22524-140">Manage Configuration Documents</span></span>

<span data-ttu-id="22524-141">De LCM beheert de configuratie van het knoop punt door te werken met **configuratie documenten**.</span><span class="sxs-lookup"><span data-stu-id="22524-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="22524-142">Deze MOF-bestanden bevinden zich in de map ' C:\Windows\System32\Configuration '.</span><span class="sxs-lookup"><span data-stu-id="22524-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="22524-143">Vanaf Power shell 5,0 kunt u met de [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) de '. MOF-bestanden verwijderen om toekomstige consistentie controles te stoppen of een configuratie met fouten verwijderen als deze wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="22524-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="22524-144">Met de para meter `-Stage` kunt u opgeven welk. MOF-bestand u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="22524-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="22524-145">In Power Shell 4,0 kunt u deze '. MOF-bestanden nog steeds rechtstreeks verwijderen met behulp van [Remove-item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="22524-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="22524-146">Configuraties publiceren</span><span class="sxs-lookup"><span data-stu-id="22524-146">Publish Configurations</span></span>

<span data-ttu-id="22524-147">Vanaf Power shell 5,0 is de cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="22524-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="22524-148">Met deze cmdlet kunt u een '. MOF-bestand publiceren naar externe computers, zonder het toe te passen.</span><span class="sxs-lookup"><span data-stu-id="22524-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="22524-149">Zie ook</span><span class="sxs-lookup"><span data-stu-id="22524-149">See also</span></span>

- [<span data-ttu-id="22524-150">Ophalen, testen en instellen</span><span class="sxs-lookup"><span data-stu-id="22524-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
