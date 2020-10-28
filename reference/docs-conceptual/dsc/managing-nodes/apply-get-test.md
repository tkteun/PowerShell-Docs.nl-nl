---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Configuraties voor een knooppunt toepassen, ophalen en testen
description: In deze hand leiding wordt uitgelegd hoe u kunt werken met configuraties op een doel knooppunt.
ms.openlocfilehash: 6bc9262bc0e2ce8eea7b85bd46ecc0c0a691276d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651022"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="6310e-104">Configuraties voor een knooppunt toepassen, ophalen en testen</span><span class="sxs-lookup"><span data-stu-id="6310e-104">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="6310e-105">In deze hand leiding wordt uitgelegd hoe u kunt werken met configuraties op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="6310e-105">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="6310e-106">Deze hand leiding is opgesplitst in de volgende stappen:</span><span class="sxs-lookup"><span data-stu-id="6310e-106">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="6310e-107">Een configuratie Toep assen</span><span class="sxs-lookup"><span data-stu-id="6310e-107">Apply a Configuration</span></span>

<span data-ttu-id="6310e-108">Om een configuratie toe te passen en te beheren, moeten we een '. MOF-bestand ' genereren.</span><span class="sxs-lookup"><span data-stu-id="6310e-108">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="6310e-109">De volgende code geeft een eenvoudige configuratie weer die in deze hand leiding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6310e-109">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

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

<span data-ttu-id="6310e-110">Bij het compileren van deze configuratie worden twee '. MOF-bestanden ' geoogst.</span><span class="sxs-lookup"><span data-stu-id="6310e-110">Compiling this configuration will yield two ".mof" files.</span></span>

```Output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="6310e-111">Gebruik de cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) om een configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="6310e-111">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="6310e-112">Met de `-Path` para meter geeft u een map op waarin de MOF-bestanden zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="6310e-112">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="6310e-113">Als er geen `-Computername` is opgegeven, `Start-DSCConfiguration` wordt geprobeerd elke configuratie toe te passen op de computer naam die is opgegeven met de naam van het MOF-bestand ( `<computername>.mof` ).</span><span class="sxs-lookup"><span data-stu-id="6310e-113">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (`<computername>.mof`).</span></span> <span data-ttu-id="6310e-114">Geef op om `-Verbose` `Start-DSCConfiguration` meer uitgebreide uitvoer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6310e-114">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="6310e-115">Als `-Wait` niet is opgegeven, ziet u dat er één taak is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="6310e-115">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="6310e-116">De gemaakte taak heeft één **ChildJob** voor elk bestand '. mof ' dat is verwerkt door `Start-DSCConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="6310e-116">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="6310e-117">Als een configuratie lange tijd in beslag neemt en u deze wilt stoppen, kunt u [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) gebruiken om de toepassing op het lokale knoop punt te stoppen.</span><span class="sxs-lookup"><span data-stu-id="6310e-117">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="6310e-118">Zodra het proces is voltooid, kunt u de status van de taken weer geven via het taak object dat wordt geretourneerd door [Get-job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="6310e-118">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="6310e-119">Als u de **uitgebreide** uitvoer wilt zien, gebruikt u de volgende opdrachten om de **uitgebreide** stroom voor elke **ChildJob** weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6310e-119">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob** .</span></span> <span data-ttu-id="6310e-120">Zie [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)voor meer informatie over Power shell-taken.</span><span class="sxs-lookup"><span data-stu-id="6310e-120">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```Output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,
'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
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

<span data-ttu-id="6310e-121">Vanaf Power shell 5,0 is de `-UseExisting` para meter toegevoegd aan `Start-DSCConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="6310e-121">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="6310e-122">`-UseExisting`Als u opgeeft, geeft u de cmdlet de opdracht om de bestaande toegepaste configuratie te gebruiken in plaats van een opgegeven door de `-Path` para meter.</span><span class="sxs-lookup"><span data-stu-id="6310e-122">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="6310e-123">Een configuratie testen</span><span class="sxs-lookup"><span data-stu-id="6310e-123">Test a Configuration</span></span>

<span data-ttu-id="6310e-124">U kunt een momenteel toegepaste configuratie testen met [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="6310e-124">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>
<span data-ttu-id="6310e-125">`Test-DSCConfiguration` wordt geretourneerd `True` als het knoop punt compatibel is en `False` als dit niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="6310e-125">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="6310e-126">Vanaf Power shell 5,0 is de `-Detailed` para meter toegevoegd die een object retourneert met verzamelingen voor **ResourcesInDesiredState** en **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="6310e-126">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="6310e-127">Vanaf Power shell 5,0 kunt u een configuratie testen zonder deze toe te passen.</span><span class="sxs-lookup"><span data-stu-id="6310e-127">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="6310e-128">De `-ReferenceConfiguration` para meter accepteert het pad van een '. MOF-bestand om het knoop punt te testen.</span><span class="sxs-lookup"><span data-stu-id="6310e-128">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="6310e-129">Er worden geen **set** -acties uitgevoerd op het knoop punt.</span><span class="sxs-lookup"><span data-stu-id="6310e-129">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="6310e-130">In Power Shell 4,0 zijn er tijdelijke oplossingen voor het testen van een configuratie zonder deze toe te passen, maar ze worden hier niet besproken.</span><span class="sxs-lookup"><span data-stu-id="6310e-130">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="6310e-131">Configuratie waarden ophalen</span><span class="sxs-lookup"><span data-stu-id="6310e-131">Get Configuration Values</span></span>

<span data-ttu-id="6310e-132">De cmdlet [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) retourneert de huidige waarden voor alle geconfigureerde resources in de momenteel toegepaste configuratie.</span><span class="sxs-lookup"><span data-stu-id="6310e-132">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="6310e-133">De uitvoer van de voorbeeld configuratie zou er als volgt uitzien als ze zijn toegepast.</span><span class="sxs-lookup"><span data-stu-id="6310e-133">Output from our sample Configuration would look like this if applied successfully.</span></span>

```Output
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

## <a name="get-configuration-status"></a><span data-ttu-id="6310e-134">Configuratie status ophalen</span><span class="sxs-lookup"><span data-stu-id="6310e-134">Get Configuration Status</span></span>

<span data-ttu-id="6310e-135">Vanaf Power shell 5,0 kunt u met de cmdlet [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) de geschiedenis van toegepaste configuraties weer geven in het knoop punt.</span><span class="sxs-lookup"><span data-stu-id="6310e-135">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="6310e-136">Power shell DSC houdt de laatste {{N}} configuraties bij die in de **Push** -of **pull** -modus worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="6310e-136">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="6310e-137">Dit omvat alle *consistentie* controles die door de LCM worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6310e-137">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="6310e-138">Standaard `Get-DSCConfigurationStatus` wordt alleen de laatste geschiedenis vermelding weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6310e-138">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```Output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="6310e-139">Gebruik de `-All` para meter om alle geschiedenis van de configuratie status weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6310e-139">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="6310e-140">De uitvoer wordt afgekapt voor het boogere.</span><span class="sxs-lookup"><span data-stu-id="6310e-140">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```Output
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

## <a name="manage-configuration-documents"></a><span data-ttu-id="6310e-141">Configuratie documenten beheren</span><span class="sxs-lookup"><span data-stu-id="6310e-141">Manage Configuration Documents</span></span>

<span data-ttu-id="6310e-142">De LCM beheert de configuratie van het knoop punt door te werken met **configuratie documenten** .</span><span class="sxs-lookup"><span data-stu-id="6310e-142">The LCM manages the Configuration of the Node by working with **Configuration Documents** .</span></span> <span data-ttu-id="6310e-143">Deze MOF-bestanden bevinden zich in de `C:\Windows\System32\Configuration` map.</span><span class="sxs-lookup"><span data-stu-id="6310e-143">These ".mof" files reside in the `C:\Windows\System32\Configuration` directory.</span></span>

<span data-ttu-id="6310e-144">Vanaf Power shell 5,0 kunt u met de [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) de '. MOF-bestanden verwijderen om toekomstige consistentie controles te stoppen of een configuratie met fouten verwijderen als deze wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="6310e-144">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="6310e-145">`-Stage`Met de para meter kunt u opgeven welk MOF-bestand u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="6310e-145">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="6310e-146">In Power Shell 4,0 kunt u deze '. MOF-bestanden nog steeds rechtstreeks verwijderen met behulp van [Remove-item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="6310e-146">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="6310e-147">Configuraties publiceren</span><span class="sxs-lookup"><span data-stu-id="6310e-147">Publish Configurations</span></span>

<span data-ttu-id="6310e-148">Vanaf Power shell 5,0 is de cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="6310e-148">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="6310e-149">Met deze cmdlet kunt u een '. MOF-bestand publiceren naar externe computers, zonder het toe te passen.</span><span class="sxs-lookup"><span data-stu-id="6310e-149">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="6310e-150">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6310e-150">See also</span></span>

- [<span data-ttu-id="6310e-151">Ophalen, testen en instellen</span><span class="sxs-lookup"><span data-stu-id="6310e-151">Get, Test, and Set</span></span>](../resources/get-test-set.md)
