---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Foutopsporing voor DSC-resources
ms.openlocfilehash: 6a1f4b04a11185c2cfe9be26324bd66ed13ca7dd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="debugging-dsc-resources"></a>Foutopsporing voor DSC-resources

> Van toepassing op: Windows PowerShell 5.0

In PowerShell 5.0 is een nieuwe functie geïntroduceerd in de gewenste status configuratie (DSC) waarmee u fouten opsporen in een DSC-resource als een configuratie wordt toegepast.

## <a name="enabling-dsc-debugging"></a>DSC-foutopsporing inschakelen
Voordat u fouten in een resource opsporen kunt, u moet inschakelen door het aanroepen van foutopsporing de [inschakelen DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.
Deze cmdlet wordt een verplichte parameter **BreakAll**.

U kunt controleren of foutopsporing is ingeschakeld door te kijken naar het resultaat van een aanroep naar [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).

De volgende PowerShell-uitvoer geeft het resultaat van de foutopsporing inschakelen:


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


## <a name="starting-a-configuration-with-debug-enabled"></a>Starten van een configuratie met foutopsporing is ingeschakeld
Voor foutopsporing DSC-resource, start u een configuratie die die resource aanroept.
Bijvoorbeeld, zullen we een eenvoudige configuratie die roept de [WindowsFeature](windowsfeatureResource.md) resource om ervoor te zorgen dat de functie 'WindowsPowerShellWebAccess' is geïnstalleerd:

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
Na het compileren van de configuratie, start u deze door aan te roepen [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).
De configuratie wordt niet meer wanneer de lokale Configuration Manager (LCM) in de eerste resource in de configuratie aanroepen.
Als u de `-Verbose` en `-Wait` parameters, de uitvoer geeft aan de regels die u invoeren moet om foutopsporing starten.

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
De LCM heeft op dit moment de resource genoemd en keert u naar het eerste break-punt.
De laatste drie regels in de uitvoer laten zien hoe koppelen aan het proces en foutopsporing in de resource-scripts te starten.

## <a name="debugging-the-resource-script"></a>Foutopsporing in de resource-scripts

Start een nieuw exemplaar van de PowerShell ISE.
Voer in het consolevenster de laatste drie regels van uitvoer van de `Start-DscConfiguration` uitvoer als opdrachten, vervangen `<credentials>` met geldige gebruikersreferenties.
U ziet nu een prompt die er ongeveer als volgt:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

Het script resource wordt geopend in het scriptvenster en het foutopsporingsprogramma stopt op de eerste regel van de **Test TargetResource** functie (de **Test()** methode van een bron op basis van een klasse).
Nu kunt u de opdrachten voor foutopsporing in de ISE om het script resource te doorlopen, bekijk de waarden van variabelen, de aanroepstack, enzovoort.
Zie voor meer informatie over foutopsporing in de PowerShell ISE [hoe fouten opsporen in Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).
Houd er rekening mee dat elke regel in het resource-script (of de klasse) is ingesteld als een break-punt.

## <a name="disabling-dsc-debugging"></a>DSC-foutopsporing uit te schakelen

Na het aanroepen [inschakelen DscDebug](https://technet.microsoft.com/library/mt517870.aspx), alle aanroepen voor [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) leidt ertoe dat de configuratie in het foutopsporingsprogramma te splitsen. Om toe te staan configuraties normaal uitgevoerd, moet u uitschakelen door het aanroepen van foutopsporing de [uitschakelen DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.

>**Opmerking:** Rebooting verandert de status van de foutopsporing van de LCM niet. Als foutopsporing is ingeschakeld, wordt het starten van een configuratie nog steeds onderbreken met foutopsporing na opnieuw opstarten.


## <a name="see-also"></a>Zie ook
- [Schrijven van een aangepaste DSC-resource met MOF](authoringResourceMOF.md)
- [Schrijven van een aangepaste DSC-resource met PowerShell-klassen](authoringResourceClass.md)