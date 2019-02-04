---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Foutopsporing voor DSC-resources
ms.openlocfilehash: 9b2e7dd9b42332b869c4d7fabb21bd4b5a6b8800
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683952"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="233e0-103">Foutopsporing voor DSC-resources</span><span class="sxs-lookup"><span data-stu-id="233e0-103">Debugging DSC resources</span></span>

> <span data-ttu-id="233e0-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="233e0-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="233e0-105">Een nieuwe functie geïntroduceerd in PowerShell 5.0, in de gewenste status elementen voor configuratie (DSC) waarmee u fouten opsporen in een DSC-resource, zoals een configuratie wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="233e0-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="233e0-106">Foutopsporing voor DSC inschakelen</span><span class="sxs-lookup"><span data-stu-id="233e0-106">Enabling DSC debugging</span></span>
<span data-ttu-id="233e0-107">Voordat u kunt fouten opsporen in een resource, u hebt om in te schakelen door het aanroepen van foutopsporing de [inschakelen DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="233e0-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span></span>
<span data-ttu-id="233e0-108">Deze cmdlet gebruikt een verplichte parameter **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="233e0-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="233e0-109">U kunt controleren of foutopsporing is ingeschakeld door te kijken naar het resultaat van een aanroep naar [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="233e0-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span></span>

<span data-ttu-id="233e0-110">De volgende PowerShell-uitvoer toont het resultaat van foutopsporing inschakelen:</span><span class="sxs-lookup"><span data-stu-id="233e0-110">The following PowerShell output shows the result of enabling debugging:</span></span>


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="233e0-111">Starten van een configuratie met foutopsporing ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="233e0-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="233e0-112">Om op te sporen een DSC-resource, start u een configuratie die die resource aanroept.</span><span class="sxs-lookup"><span data-stu-id="233e0-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="233e0-113">In dit voorbeeld kijken we een eenvoudige configuratie die roept de **WindowsFeature** resource om ervoor te zorgen dat de functie 'WindowsPowerShellWebAccess' is geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="233e0-113">For this example, we'll look at a simple configuration that calls the **WindowsFeature** resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
<span data-ttu-id="233e0-114">Na de configuratie compileren, start de service door het aanroepen van [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="233e0-114">After compiling the configuration, start it by calling [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span></span>
<span data-ttu-id="233e0-115">De configuratie van de abonnementsmeter stopt wanneer de lokale Configuration Manager (LCM) naar de eerste resource in de configuratie aanroepen.</span><span class="sxs-lookup"><span data-stu-id="233e0-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="233e0-116">Als u de `-Verbose` en `-Wait` parameters, de uitvoer worden de regels die u invoeren moet voor het starten van foutopsporing weergegeven.</span><span class="sxs-lookup"><span data-stu-id="233e0-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
<span data-ttu-id="233e0-117">De LCM heeft op dit moment de resource met de naam en het eerste onderbrekingspunt bereikt.</span><span class="sxs-lookup"><span data-stu-id="233e0-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="233e0-118">De laatste drie regels in de uitvoer laten zien hoe koppelen aan het proces en de resource-script voor de foutopsporing starten.</span><span class="sxs-lookup"><span data-stu-id="233e0-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="233e0-119">De resource-script-foutopsporing</span><span class="sxs-lookup"><span data-stu-id="233e0-119">Debugging the resource script</span></span>

<span data-ttu-id="233e0-120">Start een nieuw exemplaar van de PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="233e0-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="233e0-121">Voer in het consolevenster de laatste drie regels van uitvoer van de `Start-DscConfiguration` uitvoer als opdrachten, vervangen `<credentials>` met geldige referenties.</span><span class="sxs-lookup"><span data-stu-id="233e0-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="233e0-122">U ziet nu een prompt die lijkt op:</span><span class="sxs-lookup"><span data-stu-id="233e0-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="233e0-123">De resource-script wordt geopend in het scriptvenster en het foutopsporingsprogramma is gestopt op de eerste regel van de **Test TargetResource** functie (de **Test()** methode van een resource op basis van een klasse).</span><span class="sxs-lookup"><span data-stu-id="233e0-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="233e0-124">Nu kunt u de opdrachten voor foutopsporing in ISE de resource-script kunt doorlopen, bekijk de waarden van variabelen, de aanroepstack, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="233e0-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="233e0-125">Houd er rekening mee dat elke regel in de bron-script (of klasse) is ingesteld als een onderbrekingspunt.</span><span class="sxs-lookup"><span data-stu-id="233e0-125">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="233e0-126">DSC-foutopsporing uitschakelen</span><span class="sxs-lookup"><span data-stu-id="233e0-126">Disabling DSC debugging</span></span>

<span data-ttu-id="233e0-127">Na het aanroepen [inschakelen DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), alle aanroepen naar [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) zal leiden tot de configuratie in het foutopsporingsprogramma te analyseren.</span><span class="sxs-lookup"><span data-stu-id="233e0-127">After calling [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), all calls to [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="233e0-128">Om toe te staan configuraties normaal uitgevoerd, moet u uitschakelen door het aanroepen van foutopsporing de [uitschakelen DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="233e0-128">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span></span>

><span data-ttu-id="233e0-129">**Opmerking:** Opnieuw wordt opgestart, wordt de status van de foutopsporing van de LCM niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="233e0-129">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="233e0-130">Als foutopsporing is ingeschakeld, wordt starten van een configuratie nog steeds opsplitsen in het foutopsporingsprogramma na het opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="233e0-130">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>

## <a name="see-also"></a><span data-ttu-id="233e0-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="233e0-131">See Also</span></span>

- [<span data-ttu-id="233e0-132">Een aangepaste DSC-resource met MOF schrijven</span><span class="sxs-lookup"><span data-stu-id="233e0-132">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="233e0-133">Schrijven van een aangepaste DSC-resource met de PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="233e0-133">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
