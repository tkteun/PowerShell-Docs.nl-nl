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
# <a name="apply-get-and-test-configurations-on-a-node"></a>Configuraties voor een knooppunt toepassen, ophalen en testen

In deze hand leiding wordt uitgelegd hoe u kunt werken met configuraties op een doel knooppunt. Deze hand leiding is opgesplitst in de volgende stappen:

## <a name="apply-a-configuration"></a>Een configuratie Toep assen

Om een configuratie toe te passen en te beheren, moeten we een '. MOF-bestand ' genereren. De volgende code geeft een eenvoudige configuratie weer die in deze hand leiding wordt gebruikt.

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

Bij het compileren van deze configuratie worden twee '. MOF-bestanden ' geoogst.

```Output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Gebruik de cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) om een configuratie toe te passen. Met de `-Path` para meter geeft u een map op waarin de MOF-bestanden zich bevinden. Als er geen `-Computername` is opgegeven, `Start-DSCConfiguration` wordt geprobeerd elke configuratie toe te passen op de computer naam die is opgegeven met de naam van het MOF-bestand ( `<computername>.mof` ). Geef op om `-Verbose` `Start-DSCConfiguration` meer uitgebreide uitvoer weer te geven.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Als `-Wait` niet is opgegeven, ziet u dat er één taak is gemaakt. De gemaakte taak heeft één **ChildJob** voor elk bestand '. mof ' dat is verwerkt door `Start-DSCConfiguration` .

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Als een configuratie lange tijd in beslag neemt en u deze wilt stoppen, kunt u [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) gebruiken om de toepassing op het lokale knoop punt te stoppen.

```powershell
Stop-DSCConfiguration -Force
```

Zodra het proces is voltooid, kunt u de status van de taken weer geven via het taak object dat wordt geretourneerd door [Get-job](/powershell/module/microsoft.powershell.core/get-job).

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

Als u de **uitgebreide** uitvoer wilt zien, gebruikt u de volgende opdrachten om de **uitgebreide** stroom voor elke **ChildJob** weer te geven. Zie [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)voor meer informatie over Power shell-taken.

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

Vanaf Power shell 5,0 is de `-UseExisting` para meter toegevoegd aan `Start-DSCConfiguration` . `-UseExisting`Als u opgeeft, geeft u de cmdlet de opdracht om de bestaande toegepaste configuratie te gebruiken in plaats van een opgegeven door de `-Path` para meter.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Een configuratie testen

U kunt een momenteel toegepaste configuratie testen met [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).
`Test-DSCConfiguration` wordt geretourneerd `True` als het knoop punt compatibel is en `False` als dit niet het geval is.

```powershell
Test-DSCConfiguration
```

Vanaf Power shell 5,0 is de `-Detailed` para meter toegevoegd die een object retourneert met verzamelingen voor **ResourcesInDesiredState** en **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

Vanaf Power shell 5,0 kunt u een configuratie testen zonder deze toe te passen. De `-ReferenceConfiguration` para meter accepteert het pad van een '. MOF-bestand om het knoop punt te testen. Er worden geen **set** -acties uitgevoerd op het knoop punt. In Power Shell 4,0 zijn er tijdelijke oplossingen voor het testen van een configuratie zonder deze toe te passen, maar ze worden hier niet besproken.

## <a name="get-configuration-values"></a>Configuratie waarden ophalen

De cmdlet [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) retourneert de huidige waarden voor alle geconfigureerde resources in de momenteel toegepaste configuratie.

```powershell
Get-DSCConfiguration
```

De uitvoer van de voorbeeld configuratie zou er als volgt uitzien als ze zijn toegepast.

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

## <a name="get-configuration-status"></a>Configuratie status ophalen

Vanaf Power shell 5,0 kunt u met de cmdlet [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) de geschiedenis van toegepaste configuraties weer geven in het knoop punt. Power shell DSC houdt de laatste {{N}} configuraties bij die in de **Push** -of **pull** -modus worden toegepast. Dit omvat alle *consistentie* controles die door de LCM worden uitgevoerd. Standaard `Get-DSCConfigurationStatus` wordt alleen de laatste geschiedenis vermelding weer gegeven.

```powershell
Get-DSCConfigurationStatus
```

```Output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Gebruik de `-All` para meter om alle geschiedenis van de configuratie status weer te geven.

> [!NOTE]
> De uitvoer wordt afgekapt voor het boogere.

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

## <a name="manage-configuration-documents"></a>Configuratie documenten beheren

De LCM beheert de configuratie van het knoop punt door te werken met **configuratie documenten** . Deze MOF-bestanden bevinden zich in de `C:\Windows\System32\Configuration` map.

Vanaf Power shell 5,0 kunt u met de [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) de '. MOF-bestanden verwijderen om toekomstige consistentie controles te stoppen of een configuratie met fouten verwijderen als deze wordt toegepast. `-Stage`Met de para meter kunt u opgeven welk MOF-bestand u wilt verwijderen.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> In Power Shell 4,0 kunt u deze '. MOF-bestanden nog steeds rechtstreeks verwijderen met behulp van [Remove-item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Configuraties publiceren

Vanaf Power shell 5,0 is de cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) toegevoegd. Met deze cmdlet kunt u een '. MOF-bestand publiceren naar externe computers, zonder het toe te passen.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Zie ook

- [Ophalen, testen en instellen](../resources/get-test-set.md)
