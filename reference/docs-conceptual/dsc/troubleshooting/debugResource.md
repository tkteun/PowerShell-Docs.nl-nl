---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Foutopsporing voor DSC-resources
description: In dit artikel wordt beschreven hoe u fout opsporing voor DSC-configuraties inschakelt.
ms.openlocfilehash: 5dda217e8dc9cc4b8699c82153c1a588d405d99e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654126"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="c716c-104">Foutopsporing voor DSC-resources</span><span class="sxs-lookup"><span data-stu-id="c716c-104">Debugging DSC resources</span></span>

> <span data-ttu-id="c716c-105">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="c716c-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c716c-106">In Power shell 5,0 is een nieuwe functie geïntroduceerd in desired state Configuration (DSC) waarmee u fouten kunt opsporen in een DSC-resource als er een configuratie wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="c716c-106">In PowerShell 5.0, a new feature was introduced in Desired State Configuration (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="c716c-107">DSC-fout opsporing inschakelen</span><span class="sxs-lookup"><span data-stu-id="c716c-107">Enabling DSC debugging</span></span>

<span data-ttu-id="c716c-108">Voordat u fouten kunt opsporen in een resource, moet u fout opsporing inschakelen door de cmdlet [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c716c-108">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span></span> <span data-ttu-id="c716c-109">Deze cmdlet gebruikt een verplichte para meter, **BreakAll** .</span><span class="sxs-lookup"><span data-stu-id="c716c-109">This cmdlet takes a mandatory parameter, **BreakAll** .</span></span>

<span data-ttu-id="c716c-110">U kunt controleren of de fout opsporing is ingeschakeld door te kijken naar het resultaat van een aanroep naar [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="c716c-110">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span></span>

<span data-ttu-id="c716c-111">De volgende Power shell-uitvoer toont het resultaat van het inschakelen van fout opsporing:</span><span class="sxs-lookup"><span data-stu-id="c716c-111">The following PowerShell output shows the result of enabling debugging:</span></span>

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

## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="c716c-112">Een configuratie starten met fout opsporing ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="c716c-112">Starting a configuration with debug enabled</span></span>

<span data-ttu-id="c716c-113">Als u fouten wilt opsporen in een DSC-resource, start u een configuratie die deze bron aanroept.</span><span class="sxs-lookup"><span data-stu-id="c716c-113">To debug a DSC resource, you start a configuration that calls that resource.</span></span> <span data-ttu-id="c716c-114">In dit voor beeld bekijken we een eenvoudige configuratie die de resource van de **WindowsFeature** oproept om ervoor te zorgen dat de functie ' WindowsPowerShellWebAccess ' is geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="c716c-114">For this example, we'll look at a simple configuration that calls the **WindowsFeature** resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

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

<span data-ttu-id="c716c-115">Nadat u de configuratie hebt gecompileerd, start u deze door [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c716c-115">After compiling the configuration, start it by calling [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span></span> <span data-ttu-id="c716c-116">De configuratie wordt gestopt wanneer de lokale Configuration Manager (LCM) aanroept in de eerste bron in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="c716c-116">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span> <span data-ttu-id="c716c-117">Als u de `-Verbose` `-Wait` para meters en gebruikt, worden de regels weer gegeven die u moet invoeren om de fout opsporing te starten.</span><span class="sxs-lookup"><span data-stu-id="c716c-117">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

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

<span data-ttu-id="c716c-118">De LCM heeft nu de resource genoemd en komt tot het eerste afbreek punt.</span><span class="sxs-lookup"><span data-stu-id="c716c-118">At this point, the LCM has called the resource, and come to the first break point.</span></span> <span data-ttu-id="c716c-119">In de laatste drie regels in de uitvoer ziet u hoe u aan het proces kunt koppelen en de fout opsporing van het resource script start.</span><span class="sxs-lookup"><span data-stu-id="c716c-119">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="c716c-120">Fout opsporing van het resource script</span><span class="sxs-lookup"><span data-stu-id="c716c-120">Debugging the resource script</span></span>

<span data-ttu-id="c716c-121">Start een nieuw exemplaar van de Power shell-ISE.</span><span class="sxs-lookup"><span data-stu-id="c716c-121">Start a new instance of the PowerShell ISE.</span></span> <span data-ttu-id="c716c-122">Voer in het console venster de laatste drie regels uitvoer van de uitvoer in `Start-DscConfiguration` als opdrachten, vervangen `<credentials>` door geldige gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="c716c-122">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span> <span data-ttu-id="c716c-123">Er wordt nu een prompt weer gegeven die er ongeveer als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="c716c-123">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="c716c-124">Het bron script wordt in het Script-venster geopend en de fout opsporing wordt gestopt op de eerste regel van de functie **test-TargetResource** (de methode **test ()** van een op een klasse gebaseerde bron).</span><span class="sxs-lookup"><span data-stu-id="c716c-124">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span> <span data-ttu-id="c716c-125">Nu kunt u de opdrachten voor fout opsporing in de ISE gebruiken om het resource script te door lopen, variabelen waarden bekijken, de aanroep stack bekijken, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="c716c-125">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="c716c-126">Houd er rekening mee dat elke regel in het resource script (of de klasse) is ingesteld als een breek punt.</span><span class="sxs-lookup"><span data-stu-id="c716c-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="c716c-127">DSC-fout opsporing uitschakelen</span><span class="sxs-lookup"><span data-stu-id="c716c-127">Disabling DSC debugging</span></span>

<span data-ttu-id="c716c-128">Nadat u [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)hebt aangeroepen, worden alle aanroepen naar [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) tot de configuratie van de fout opsporing geleid.</span><span class="sxs-lookup"><span data-stu-id="c716c-128">After calling [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), all calls to [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="c716c-129">Als u wilt toestaan dat configuraties normaal worden uitgevoerd, moet u fout opsporing uitschakelen door de cmdlet [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c716c-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c716c-130">Het opnieuw opstarten van de LCM heeft geen invloed op de status van de fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="c716c-130">Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="c716c-131">Als fout opsporing is ingeschakeld, wordt het starten van een configuratie na het opnieuw opstarten nog steeds verbroken in het fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="c716c-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>

## <a name="see-also"></a><span data-ttu-id="c716c-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c716c-132">See Also</span></span>

- [<span data-ttu-id="c716c-133">Een aangepaste DSC-resource schrijven met MOF</span><span class="sxs-lookup"><span data-stu-id="c716c-133">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="c716c-134">Een aangepaste DSC-resource schrijven met Power shell-klassen</span><span class="sxs-lookup"><span data-stu-id="c716c-134">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
