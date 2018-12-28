---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Van toepassing, Get, en Test configuraties op een knooppunt
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404374"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="98244-103">Van toepassing, Get, en Test configuraties op een knooppunt</span><span class="sxs-lookup"><span data-stu-id="98244-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="98244-104">Deze handleiding wordt beschreven hoe om te werken met configuraties op een doel-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="98244-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="98244-105">Deze handleiding wordt opgedeeld in de volgende stappen uit:</span><span class="sxs-lookup"><span data-stu-id="98244-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="98244-106">Een configuratie toepassen</span><span class="sxs-lookup"><span data-stu-id="98244-106">Apply a Configuration</span></span>

<span data-ttu-id="98244-107">Als u wilt toepassen en beheren van een configuratie, moeten we een '.mof'-bestand genereren.</span><span class="sxs-lookup"><span data-stu-id="98244-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="98244-108">De volgende code staat voor een eenvoudige configuratie die wordt gebruikt in deze handleiding.</span><span class="sxs-lookup"><span data-stu-id="98244-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

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

<span data-ttu-id="98244-109">Deze configuratie compileren tot "twee MOF-bestanden.</span><span class="sxs-lookup"><span data-stu-id="98244-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="98244-110">Als u wilt een configuratie toepassen, gebruikt u de [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="98244-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="98244-111">De `-Path` parameter geeft u een map waar MOF-bestanden zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="98244-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="98244-112">Als er geen `-Computername` is opgegeven, `Start-DSCConfiguration` probeert toe te passen van elke configuratie op de computernaam die is opgegeven door de naam van het bestand '.mof' (\<computername\>.mof).</span><span class="sxs-lookup"><span data-stu-id="98244-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="98244-113">Geef `-Verbose` naar `Start-DSCConfiguration` om meer uitgebreide uitvoer te bekijken.</span><span class="sxs-lookup"><span data-stu-id="98244-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="98244-114">Als `-Wait` niet is opgegeven, ziet u een taak gemaakt.</span><span class="sxs-lookup"><span data-stu-id="98244-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="98244-115">De taak hebt gemaakt heeft een **ChildJob** voor elk bestand ".mof" verwerkt door `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="98244-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="98244-116">Als een configuratie duurt lang duren en u wilt stoppen, kunt u [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) Stop de toepassing op het lokale knooppunt.</span><span class="sxs-lookup"><span data-stu-id="98244-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="98244-117">Als u klaar bent, vindt u de status van de taken via het taakobject dat is geretourneerd door [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="98244-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

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

<span data-ttu-id="98244-118">Om te zien de **uitgebreid** uitvoer, gebruikt u de volgende opdrachten om weer te geven de **uitgebreid** stream voor elk **ChildJob**.</span><span class="sxs-lookup"><span data-stu-id="98244-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="98244-119">Zie voor meer informatie over PowerShell-taken, [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="98244-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

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

<span data-ttu-id="98244-120">PowerShell 5.0, vanaf de `-UseExisting` parameter is toegevoegd aan de `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="98244-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="98244-121">Door op te geven `-UseExisting`, u de cmdlet voor het gebruik van de bestaande configuratie van de toegepaste in plaats van een opgegeven door de opdracht geven de `-Path` parameter.</span><span class="sxs-lookup"><span data-stu-id="98244-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="98244-122">Een configuratie testen</span><span class="sxs-lookup"><span data-stu-id="98244-122">Test a Configuration</span></span>

<span data-ttu-id="98244-123">U kunt testen een dat momenteel wordt toegepast met configuratie [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="98244-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="98244-124">`Test-DSCConfiguration` retourneert `True` als compatibel is, is het knooppunt en `False` als deze niet.</span><span class="sxs-lookup"><span data-stu-id="98244-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="98244-125">PowerShell 5.0, vanaf de `-Detailed` parameter is toegevoegd die resulteert in een object met verzamelingen voor **ResourcesInDesiredState** en **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="98244-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="98244-126">Vanaf PowerShell 5.0 u kunt een configuratie testen zonder toe te passen.</span><span class="sxs-lookup"><span data-stu-id="98244-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="98244-127">De `-ReferenceConfiguration` parameter accepteert u het pad van een bestand '.mof' voor het testen van het knooppunt op.</span><span class="sxs-lookup"><span data-stu-id="98244-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="98244-128">Geen **ingesteld** acties worden uitgevoerd op basis van het knooppunt.</span><span class="sxs-lookup"><span data-stu-id="98244-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="98244-129">Er zijn oplossingen voor het testen van een configuratie zonder toe te passen in PowerShell 4.0, maar ze niet hier worden besproken.</span><span class="sxs-lookup"><span data-stu-id="98244-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="98244-130">Configuratiewaarden ophalen</span><span class="sxs-lookup"><span data-stu-id="98244-130">Get Configuration Values</span></span>

<span data-ttu-id="98244-131">De [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet retourneert de huidige waarden voor alle geconfigureerde resources in de configuratie van de dat momenteel wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="98244-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="98244-132">Uitvoer van de configuratie van ons voorbeeld zou er als volgt als is toegepast.</span><span class="sxs-lookup"><span data-stu-id="98244-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

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

## <a name="get-configuration-status"></a><span data-ttu-id="98244-133">Configuratiestatus van de ophalen</span><span class="sxs-lookup"><span data-stu-id="98244-133">Get Configuration Status</span></span>

<span data-ttu-id="98244-134">PowerShell 5.0 vanaf de [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet kunt u zien van de geschiedenis van toegepaste configuraties naar het knooppunt.</span><span class="sxs-lookup"><span data-stu-id="98244-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="98244-135">PowerShell DSC houdt van de laatste {{N}}-configuraties in toegepast **Push** of **Pull** modus.</span><span class="sxs-lookup"><span data-stu-id="98244-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="98244-136">Dit omvat een *consistentie* controles uitgevoerd door de LCM.</span><span class="sxs-lookup"><span data-stu-id="98244-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="98244-137">Standaard `Get-DSCConfigurationStatus` ziet u alleen de laatste geschiedenisitem.</span><span class="sxs-lookup"><span data-stu-id="98244-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="98244-138">Gebruik de `-All` parameter om te zien van alle configuratie-statusgeschiedenis.</span><span class="sxs-lookup"><span data-stu-id="98244-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="98244-139">Uitvoer is afgekapt voor kort te houden.</span><span class="sxs-lookup"><span data-stu-id="98244-139">Output is truncated for brevity.</span></span>

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

## <a name="manage-configuration-documents"></a><span data-ttu-id="98244-140">Van configuratiedocumenten beheren</span><span class="sxs-lookup"><span data-stu-id="98244-140">Manage Configuration Documents</span></span>

<span data-ttu-id="98244-141">De LCM beheert de configuratie van het knooppunt door te werken met **configuratiedocumenten**.</span><span class="sxs-lookup"><span data-stu-id="98244-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="98244-142">"Deze MOF-bestanden bevinden zich in de map 'C:\Windows\System32\Configuration'.</span><span class="sxs-lookup"><span data-stu-id="98244-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="98244-143">PowerShell 5.0 vanaf de [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) Hiermee kunt u de bestanden ".mof" consistentiecontroles van de toekomstige stoppen of verwijderen van een configuratie met fouten bij het toegepast verwijderen.</span><span class="sxs-lookup"><span data-stu-id="98244-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="98244-144">De `-Stage` parameter kunt u opgeven welk '.mof'-bestand dat u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="98244-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="98244-145">In PowerShell 4.0, kunt u nog steeds deze ' MOF-bestanden rechtstreeks met behulp van verwijderen [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="98244-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="98244-146">Publiceren van configuraties</span><span class="sxs-lookup"><span data-stu-id="98244-146">Publish Configurations</span></span>

<span data-ttu-id="98244-147">PowerShell 5.0, vanaf de [publiceren-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="98244-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="98244-148">Deze cmdlet kunt u een bestand '.mof' publiceren naar externe computers, zonder toe te passen.</span><span class="sxs-lookup"><span data-stu-id="98244-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="98244-149">Zie ook</span><span class="sxs-lookup"><span data-stu-id="98244-149">See also</span></span>

- [<span data-ttu-id="98244-150">Ophalen, testen, en instellen</span><span class="sxs-lookup"><span data-stu-id="98244-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
