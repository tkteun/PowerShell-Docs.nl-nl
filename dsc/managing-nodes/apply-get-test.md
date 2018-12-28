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
# <a name="apply-get-and-test-configurations-on-a-node"></a>Van toepassing, Get, en Test configuraties op een knooppunt

Deze handleiding wordt beschreven hoe om te werken met configuraties op een doel-knooppunt. Deze handleiding wordt opgedeeld in de volgende stappen uit:

## <a name="apply-a-configuration"></a>Een configuratie toepassen

Als u wilt toepassen en beheren van een configuratie, moeten we een '.mof'-bestand genereren. De volgende code staat voor een eenvoudige configuratie die wordt gebruikt in deze handleiding.

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

Deze configuratie compileren tot "twee MOF-bestanden.

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Als u wilt een configuratie toepassen, gebruikt u de [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. De `-Path` parameter geeft u een map waar MOF-bestanden zich bevinden. Als er geen `-Computername` is opgegeven, `Start-DSCConfiguration` probeert toe te passen van elke configuratie op de computernaam die is opgegeven door de naam van het bestand '.mof' (\<computername\>.mof). Geef `-Verbose` naar `Start-DSCConfiguration` om meer uitgebreide uitvoer te bekijken.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Als `-Wait` niet is opgegeven, ziet u een taak gemaakt. De taak hebt gemaakt heeft een **ChildJob** voor elk bestand ".mof" verwerkt door `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Als een configuratie duurt lang duren en u wilt stoppen, kunt u [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) Stop de toepassing op het lokale knooppunt.

```powershell
Stop-DSCConfiguration -Force
```

Als u klaar bent, vindt u de status van de taken via het taakobject dat is geretourneerd door [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

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

Om te zien de **uitgebreid** uitvoer, gebruikt u de volgende opdrachten om weer te geven de **uitgebreid** stream voor elk **ChildJob**. Zie voor meer informatie over PowerShell-taken, [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

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

PowerShell 5.0, vanaf de `-UseExisting` parameter is toegevoegd aan de `Start-DSCConfiguration`. Door op te geven `-UseExisting`, u de cmdlet voor het gebruik van de bestaande configuratie van de toegepaste in plaats van een opgegeven door de opdracht geven de `-Path` parameter.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Een configuratie testen

U kunt testen een dat momenteel wordt toegepast met configuratie [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` retourneert `True` als compatibel is, is het knooppunt en `False` als deze niet.

```powershell
Test-DSCConfiguration
```

PowerShell 5.0, vanaf de `-Detailed` parameter is toegevoegd die resulteert in een object met verzamelingen voor **ResourcesInDesiredState** en **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

Vanaf PowerShell 5.0 u kunt een configuratie testen zonder toe te passen. De `-ReferenceConfiguration` parameter accepteert u het pad van een bestand '.mof' voor het testen van het knooppunt op. Geen **ingesteld** acties worden uitgevoerd op basis van het knooppunt. Er zijn oplossingen voor het testen van een configuratie zonder toe te passen in PowerShell 4.0, maar ze niet hier worden besproken.

## <a name="get-configuration-values"></a>Configuratiewaarden ophalen

De [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet retourneert de huidige waarden voor alle geconfigureerde resources in de configuratie van de dat momenteel wordt toegepast.

```powershell
Get-DSCConfiguration
```

Uitvoer van de configuratie van ons voorbeeld zou er als volgt als is toegepast.

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

## <a name="get-configuration-status"></a>Configuratiestatus van de ophalen

PowerShell 5.0 vanaf de [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet kunt u zien van de geschiedenis van toegepaste configuraties naar het knooppunt. PowerShell DSC houdt van de laatste {{N}}-configuraties in toegepast **Push** of **Pull** modus. Dit omvat een *consistentie* controles uitgevoerd door de LCM. Standaard `Get-DSCConfigurationStatus` ziet u alleen de laatste geschiedenisitem.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Gebruik de `-All` parameter om te zien van alle configuratie-statusgeschiedenis.

> [!NOTE]
> Uitvoer is afgekapt voor kort te houden.

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

## <a name="manage-configuration-documents"></a>Van configuratiedocumenten beheren

De LCM beheert de configuratie van het knooppunt door te werken met **configuratiedocumenten**. "Deze MOF-bestanden bevinden zich in de map 'C:\Windows\System32\Configuration'.

PowerShell 5.0 vanaf de [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) Hiermee kunt u de bestanden ".mof" consistentiecontroles van de toekomstige stoppen of verwijderen van een configuratie met fouten bij het toegepast verwijderen. De `-Stage` parameter kunt u opgeven welk '.mof'-bestand dat u wilt verwijderen.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> In PowerShell 4.0, kunt u nog steeds deze ' MOF-bestanden rechtstreeks met behulp van verwijderen [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Publiceren van configuraties

PowerShell 5.0, vanaf de [publiceren-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet is toegevoegd. Deze cmdlet kunt u een bestand '.mof' publiceren naar externe computers, zonder toe te passen.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Zie ook

- [Ophalen, testen, en instellen](../resources/get-test-set.md)
