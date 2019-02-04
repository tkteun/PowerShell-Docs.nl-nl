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
# <a name="debugging-dsc-resources"></a>Foutopsporing voor DSC-resources

> Van toepassing op: Windows PowerShell 5.0

Een nieuwe functie geïntroduceerd in PowerShell 5.0, in de gewenste status elementen voor configuratie (DSC) waarmee u fouten opsporen in een DSC-resource, zoals een configuratie wordt toegepast.

## <a name="enabling-dsc-debugging"></a>Foutopsporing voor DSC inschakelen
Voordat u kunt fouten opsporen in een resource, u hebt om in te schakelen door het aanroepen van foutopsporing de [inschakelen DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.
Deze cmdlet gebruikt een verplichte parameter **BreakAll**.

U kunt controleren of foutopsporing is ingeschakeld door te kijken naar het resultaat van een aanroep naar [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

De volgende PowerShell-uitvoer toont het resultaat van foutopsporing inschakelen:


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


## <a name="starting-a-configuration-with-debug-enabled"></a>Starten van een configuratie met foutopsporing ingeschakeld
Om op te sporen een DSC-resource, start u een configuratie die die resource aanroept.
In dit voorbeeld kijken we een eenvoudige configuratie die roept de **WindowsFeature** resource om ervoor te zorgen dat de functie 'WindowsPowerShellWebAccess' is geïnstalleerd:

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
Na de configuratie compileren, start de service door het aanroepen van [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).
De configuratie van de abonnementsmeter stopt wanneer de lokale Configuration Manager (LCM) naar de eerste resource in de configuratie aanroepen.
Als u de `-Verbose` en `-Wait` parameters, de uitvoer worden de regels die u invoeren moet voor het starten van foutopsporing weergegeven.

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
De LCM heeft op dit moment de resource met de naam en het eerste onderbrekingspunt bereikt.
De laatste drie regels in de uitvoer laten zien hoe koppelen aan het proces en de resource-script voor de foutopsporing starten.

## <a name="debugging-the-resource-script"></a>De resource-script-foutopsporing

Start een nieuw exemplaar van de PowerShell ISE.
Voer in het consolevenster de laatste drie regels van uitvoer van de `Start-DscConfiguration` uitvoer als opdrachten, vervangen `<credentials>` met geldige referenties.
U ziet nu een prompt die lijkt op:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

De resource-script wordt geopend in het scriptvenster en het foutopsporingsprogramma is gestopt op de eerste regel van de **Test TargetResource** functie (de **Test()** methode van een resource op basis van een klasse).
Nu kunt u de opdrachten voor foutopsporing in ISE de resource-script kunt doorlopen, bekijk de waarden van variabelen, de aanroepstack, enzovoort. Houd er rekening mee dat elke regel in de bron-script (of klasse) is ingesteld als een onderbrekingspunt.

## <a name="disabling-dsc-debugging"></a>DSC-foutopsporing uitschakelen

Na het aanroepen [inschakelen DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), alle aanroepen naar [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) zal leiden tot de configuratie in het foutopsporingsprogramma te analyseren. Om toe te staan configuraties normaal uitgevoerd, moet u uitschakelen door het aanroepen van foutopsporing de [uitschakelen DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.

>**Opmerking:** Opnieuw wordt opgestart, wordt de status van de foutopsporing van de LCM niet gewijzigd. Als foutopsporing is ingeschakeld, wordt starten van een configuratie nog steeds opsplitsen in het foutopsporingsprogramma na het opnieuw opstarten.

## <a name="see-also"></a>Zie ook

- [Een aangepaste DSC-resource met MOF schrijven](../resources/authoringResourceMOF.md)
- [Schrijven van een aangepaste DSC-resource met de PowerShell-klassen](../resources/authoringResourceClass.md)
