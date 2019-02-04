---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: f30f43265d9daa47383e42f0f8abf4844365ea6d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687690"
---
# <a name="set-dsclocalconfigurationmanager-cmdlet-supports--force-parameter"></a><span data-ttu-id="15667-102">Cmdlet Set-DscLocalConfigurationManager biedt ondersteuning - parameter force</span><span class="sxs-lookup"><span data-stu-id="15667-102">Set-DscLocalConfigurationManager cmdlet supports -force parameter</span></span>

<span data-ttu-id="15667-103">We hebben een ondersteuning voor nieuwe parameter toegevoegd aan de cmdlet Set-DscLocalConfigurationManager.</span><span class="sxs-lookup"><span data-stu-id="15667-103">We have added a support for new parameter to Set-DscLocalConfigurationManager cmdlet.</span></span> <span data-ttu-id="15667-104">Hierdoor wordt de gebruiker meta-configuratie op de machine deterministische wijze opnieuw instellen als andere bewerkingen zoals het consistentiecontrole uit in de achtergrond worden uitgevoerd omdat alle actieve bewerkingen moet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="15667-104">This will allow the user to reset meta configuration on machine deterministically when other operations like consistency check are running in background as it will cause all running operations to be stopped.</span></span>

<span data-ttu-id="15667-105">De ervaring ziet eruit als dit bij een poging om in te stellen meta-configuratie zonder – Force-parameter.</span><span class="sxs-lookup"><span data-stu-id="15667-105">The experience looks like this when trying to set meta configuration without –Force parameter.</span></span>
```powershell
PS C:\\Configs&gt; Set-DscLocalConfigurationManager -Path .\\MetaTest1\\ -Verbose
VERBOSE: Performing the operation "Start-DscConfiguration: SendMetaConfigurationApply" on target "MSFT\_DSCLocalConfigurationManager".
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendMetaConfigurationApply,'className' = MSFT\_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer DEV-10586-465 with user sid S-1-5-21-2127521184-1604012920-1887927527-5557045.
Cannot invoke the Set-DscLocalConfigurationManager cmdlet. The Consistency Check or Pull cmdlet is in progress and must return before
Set-DscLocalConfigurationManager can be invoked. Use -Force option if that is available to cancel the current operation.
+ CategoryInfo : NotSpecified: (root/Microsoft/...gurationManager:String) \[\], CimException
+ FullyQualifiedErrorId : MI RESULT 1
+ PSComputerName : localhost
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Set-DscLocalConfigurationManager finished in 0.046 seconds.
```

<span data-ttu-id="15667-106">Als we gebruiken – geforceerd is werkt u de configuratie van de metagegevens op systeem door het annuleren van de huidige actieve bewerking op de machine.</span><span class="sxs-lookup"><span data-stu-id="15667-106">When we use –force it successfully updates the meta configuration on system by canceling the current running operation on the machine.</span></span>
```powershell
PS C:\\Configs&gt; Set-DscLocalConfigurationManager -Path .\\MetaTest1\\ -Verbose -Force
VERBOSE: Performing the operation "Start-DscConfiguration: SendMetaConfigurationApply" on target "MSFT\_DSCLocalConfigurationManager".
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendMetaConfigurationApply,'className' = MSFT\_DSCLocalConfigurationManager,'n
amespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer DEV-10586-465 with user sid S-1-5-21-2127521184-1604012920-1887927527-5557045.
VERBOSE: The -Force option was specified with the Stop operation. The current configuration has been successfully cancelled.
VERBOSE: An LCM method call arrived from computer DEV-10586-465 with user sid S-1-5-21-2127521184-1604012920-1887927527-5557045.
VERBOSE: \[DEV-10586-465\]: LCM: \[ Start Set \]
VERBOSE: \[DEV-10586-465\]: LCM: \[ Start Resource \] \[MSFT\_DSCMetaConfiguration\]
VERBOSE: \[DEV-10586-465\]: LCM: \[ Start Set \] \[MSFT\_DSCMetaConfiguration\]
VERBOSE: \[DEV-10586-465\]: LCM: \[ End Set \] \[MSFT\_DSCMetaConfiguration\] in 0.0310 seconds.
VERBOSE: \[DEV-10586-465\]: LCM: \[ End Resource \] \[MSFT\_DSCMetaConfiguration\]
VERBOSE: \[DEV-10586-465\]: LCM: \[ End Set \]
VERBOSE: \[DEV-10586-465\]: LCM: \[ End Set \] in 0.1410 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Set-DscLocalConfigurationManager finished in 0.421 seconds.
```
