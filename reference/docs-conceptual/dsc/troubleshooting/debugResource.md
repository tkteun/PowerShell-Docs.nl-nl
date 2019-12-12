---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Foutopsporing voor DSC-resources
ms.openlocfilehash: c088e13a25ba31ceebaf52b2d24b5d32b96ae2fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942158"
---
# <a name="debugging-dsc-resources"></a>Foutopsporing voor DSC-resources

> Van toepassing op: Windows Power shell 5,0

In Power shell 5,0 is een nieuwe functie geïntroduceerd in desired state Configuration (DSC) waarmee u fouten kunt opsporen in een DSC-resource als er een configuratie wordt toegepast.

## <a name="enabling-dsc-debugging"></a>DSC-fout opsporing inschakelen
Voordat u fouten kunt opsporen in een resource, moet u fout opsporing inschakelen door de cmdlet [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) aan te roepen.
Deze cmdlet gebruikt een verplichte para meter, **BreakAll**.

U kunt controleren of de fout opsporing is ingeschakeld door te kijken naar het resultaat van een aanroep naar [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

De volgende Power shell-uitvoer toont het resultaat van het inschakelen van fout opsporing:


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


## <a name="starting-a-configuration-with-debug-enabled"></a>Een configuratie starten met fout opsporing ingeschakeld
Als u fouten wilt opsporen in een DSC-resource, start u een configuratie die deze bron aanroept.
In dit voor beeld bekijken we een eenvoudige configuratie die de resource van de **WindowsFeature** oproept om ervoor te zorgen dat de functie ' WindowsPowerShellWebAccess ' is geïnstalleerd:

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
Nadat u de configuratie hebt gecompileerd, start u deze door [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)aan te roepen.
De configuratie wordt gestopt wanneer de lokale Configuration Manager (LCM) aanroept in de eerste bron in de configuratie.
Als u de para meters `-Verbose` en `-Wait` gebruikt, worden in de uitvoer de regels weer gegeven die u moet invoeren om de fout opsporing te starten.

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
De LCM heeft nu de resource genoemd en komt tot het eerste afbreek punt.
In de laatste drie regels in de uitvoer ziet u hoe u aan het proces kunt koppelen en de fout opsporing van het resource script start.

## <a name="debugging-the-resource-script"></a>Fout opsporing van het resource script

Start een nieuw exemplaar van de Power shell-ISE.
Voer in het console venster de laatste drie regels uitvoer van de `Start-DscConfiguration` uitvoer als opdrachten in, waarbij `<credentials>` wordt vervangen door geldige gebruikers referenties.
Er wordt nu een prompt weer gegeven die er ongeveer als volgt uitziet:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

Het bron script wordt in het Script-venster geopend en de fout opsporing wordt gestopt op de eerste regel van de functie **test-TargetResource** (de methode **test ()** van een op een klasse gebaseerde bron).
Nu kunt u de opdrachten voor fout opsporing in de ISE gebruiken om het resource script te door lopen, variabelen waarden bekijken, de aanroep stack bekijken, enzovoort. Houd er rekening mee dat elke regel in het resource script (of de klasse) is ingesteld als een breek punt.

## <a name="disabling-dsc-debugging"></a>DSC-fout opsporing uitschakelen

Nadat u [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)hebt aangeroepen, worden alle aanroepen naar [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) tot de configuratie van de fout opsporing geleid. Als u wilt toestaan dat configuraties normaal worden uitgevoerd, moet u fout opsporing uitschakelen door de cmdlet [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) aan te roepen.

>**Opmerking:** Het opnieuw opstarten van de LCM heeft geen invloed op de status van de fout opsporing. Als fout opsporing is ingeschakeld, wordt het starten van een configuratie na het opnieuw opstarten nog steeds verbroken in het fout opsporingsprogramma.

## <a name="see-also"></a>Zie ook

- [Een aangepaste DSC-resource schrijven met MOF](../resources/authoringResourceMOF.md)
- [Een aangepaste DSC-resource schrijven met Power shell-klassen](../resources/authoringResourceClass.md)
