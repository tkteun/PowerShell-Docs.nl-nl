---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Foutopsporing voor DSC-resources
ms.openlocfilehash: 30d49768fc2301b5306d0001e157d60e2e991883
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="971d1-103">Foutopsporing voor DSC-resources</span><span class="sxs-lookup"><span data-stu-id="971d1-103">Debugging DSC resources</span></span>

> <span data-ttu-id="971d1-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="971d1-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="971d1-105">In PowerShell 5.0 is een nieuwe functie geïntroduceerd in de gewenste status configuratie (DSC) waarmee u fouten opsporen in een DSC-resource als een configuratie wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="971d1-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="971d1-106">DSC-foutopsporing inschakelen</span><span class="sxs-lookup"><span data-stu-id="971d1-106">Enabling DSC debugging</span></span>
<span data-ttu-id="971d1-107">Voordat u fouten in een resource opsporen kunt, u moet inschakelen door het aanroepen van foutopsporing de [inschakelen DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="971d1-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.</span></span>
<span data-ttu-id="971d1-108">Deze cmdlet wordt een verplichte parameter **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="971d1-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="971d1-109">U kunt controleren of foutopsporing is ingeschakeld door te kijken naar het resultaat van een aanroep naar [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span><span class="sxs-lookup"><span data-stu-id="971d1-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span></span>

<span data-ttu-id="971d1-110">De volgende PowerShell-uitvoer geeft het resultaat van de foutopsporing inschakelen:</span><span class="sxs-lookup"><span data-stu-id="971d1-110">The following PowerShell output shows the result of enabling debugging:</span></span>


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


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="971d1-111">Starten van een configuratie met foutopsporing is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="971d1-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="971d1-112">Voor foutopsporing DSC-resource, start u een configuratie die die resource aanroept.</span><span class="sxs-lookup"><span data-stu-id="971d1-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="971d1-113">Bijvoorbeeld, zullen we een eenvoudige configuratie die roept de [WindowsFeature](windowsfeatureResource.md) resource om ervoor te zorgen dat de functie 'WindowsPowerShellWebAccess' is geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="971d1-113">For this example, we'll look at a simple configuration that calls the [WindowsFeature](windowsfeatureResource.md) resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

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
<span data-ttu-id="971d1-114">Na het compileren van de configuratie, start u deze door aan te roepen [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="971d1-114">After compiling the configuration, start it by calling [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span></span>
<span data-ttu-id="971d1-115">De configuratie wordt niet meer wanneer de lokale Configuration Manager (LCM) in de eerste resource in de configuratie aanroepen.</span><span class="sxs-lookup"><span data-stu-id="971d1-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="971d1-116">Als u de `-Verbose` en `-Wait` parameters, de uitvoer geeft aan de regels die u invoeren moet om foutopsporing starten.</span><span class="sxs-lookup"><span data-stu-id="971d1-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

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
<span data-ttu-id="971d1-117">De LCM heeft op dit moment de resource genoemd en keert u naar het eerste break-punt.</span><span class="sxs-lookup"><span data-stu-id="971d1-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="971d1-118">De laatste drie regels in de uitvoer laten zien hoe koppelen aan het proces en foutopsporing in de resource-scripts te starten.</span><span class="sxs-lookup"><span data-stu-id="971d1-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="971d1-119">Foutopsporing in de resource-scripts</span><span class="sxs-lookup"><span data-stu-id="971d1-119">Debugging the resource script</span></span>

<span data-ttu-id="971d1-120">Start een nieuw exemplaar van de PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="971d1-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="971d1-121">Voer in het consolevenster de laatste drie regels van uitvoer van de `Start-DscConfiguration` uitvoer als opdrachten, vervangen `<credentials>` met geldige gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="971d1-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="971d1-122">U ziet nu een prompt die er ongeveer als volgt:</span><span class="sxs-lookup"><span data-stu-id="971d1-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="971d1-123">Het script resource wordt geopend in het scriptvenster en het foutopsporingsprogramma stopt op de eerste regel van de **Test TargetResource** functie (de **Test()** methode van een bron op basis van een klasse).</span><span class="sxs-lookup"><span data-stu-id="971d1-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="971d1-124">Nu kunt u de opdrachten voor foutopsporing in de ISE om het script resource te doorlopen, bekijk de waarden van variabelen, de aanroepstack, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="971d1-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span>
<span data-ttu-id="971d1-125">Zie voor meer informatie over foutopsporing in de PowerShell ISE [hoe fouten opsporen in Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span><span class="sxs-lookup"><span data-stu-id="971d1-125">For information about debugging in the PowerShell ISE, see [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span></span>
<span data-ttu-id="971d1-126">Houd er rekening mee dat elke regel in het resource-script (of de klasse) is ingesteld als een break-punt.</span><span class="sxs-lookup"><span data-stu-id="971d1-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="971d1-127">DSC-foutopsporing uit te schakelen</span><span class="sxs-lookup"><span data-stu-id="971d1-127">Disabling DSC debugging</span></span>

<span data-ttu-id="971d1-128">Na het aanroepen [inschakelen DscDebug](https://technet.microsoft.com/library/mt517870.aspx), alle aanroepen voor [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) leidt ertoe dat de configuratie in het foutopsporingsprogramma te splitsen.</span><span class="sxs-lookup"><span data-stu-id="971d1-128">After calling [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx), all calls to [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="971d1-129">Om toe te staan configuraties normaal uitgevoerd, moet u uitschakelen door het aanroepen van foutopsporing de [uitschakelen DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="971d1-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span></span>

><span data-ttu-id="971d1-130">**Opmerking:** Rebooting verandert de status van de foutopsporing van de LCM niet.</span><span class="sxs-lookup"><span data-stu-id="971d1-130">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="971d1-131">Als foutopsporing is ingeschakeld, wordt het starten van een configuratie nog steeds onderbreken met foutopsporing na opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="971d1-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>


## <a name="see-also"></a><span data-ttu-id="971d1-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="971d1-132">See Also</span></span>
- [<span data-ttu-id="971d1-133">Schrijven van een aangepaste DSC-resource met MOF</span><span class="sxs-lookup"><span data-stu-id="971d1-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="971d1-134">Schrijven van een aangepaste DSC-resource met PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="971d1-134">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)