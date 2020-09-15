---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Get-test-set
ms.openlocfilehash: f7b7e947a85832365a783e40c25a25bfaa9fff8d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771512"
---
# <a name="get-test-set"></a>Get-test-set

>Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

De gewenste status configuratie van Power shell is geconstrueerd rond een **Get**-, **test**-en **set** -proces. DSC- [resources](resources.md) bevatten elk methoden voor het volt ooien van elk van deze bewerkingen.
In een [configuratie](../configurations/configurations.md)definieert u resource blokken om sleutels in te vullen die para meters voor de **Get**-, **test**-en **set** -methoden van een resource worden.

Dit is de syntaxis voor een **service** bron blok. De **service** resource configureert Windows-Services.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

De methoden **Get**, **test**en **set** van de **service** Resource hebben parameter blokken die deze waarden accepteren.

```powershell
param
(
    [parameter(Mandatory = $true)]
    [ValidateNotNullOrEmpty()]
    [System.String]
    $Name,

    [System.String]
    [ValidateSet("Automatic", "Manual", "Disabled")]
    $StartupType,

    [System.String]
    [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
    $BuiltInAccount,

    [System.Management.Automation.PSCredential]
    [ValidateNotNull()]
    $Credential,

    [System.String]
    [ValidateSet("Running", "Stopped")]
    $State="Running",

    [System.String]
    [ValidateNotNullOrEmpty()]
    $DisplayName,

    [System.String]
    [ValidateNotNullOrEmpty()]
    $Description,

    [System.String]
    [ValidateNotNullOrEmpty()]
    $Path,

    [System.String[]]
    [ValidateNotNullOrEmpty()]
    $Dependencies,

    [System.String]
    [ValidateSet("Present", "Absent")]
    $Ensure="Present"
)
```

> [!NOTE]
> De taal en methode waarmee de resource is gedefinieerd, bepalen hoe de methoden **ophalen**, **testen**en **instellen** worden gedefinieerd.

Omdat de **service** bron slechts één vereiste sleutel ( `Name` ) heeft, kan een **service** blok bron zo eenvoudig zijn als:

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

Wanneer u de configuratie hierboven compileert, worden de waarden die u opgeeft voor een sleutel opgeslagen in het `.mof` bestand dat wordt gegenereerd. Zie voor meer informatie [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

Als de [lokale Configuration Manager](../managing-nodes/metaConfig.md) (LCM) wordt toegepast, wordt de waarde ' spooler ' in het `.mof` bestand gelezen en door gegeven aan de para meter **name** van de methoden **Get**, **test**en **set** voor het exemplaar ' MyService ' van de **service** resource.

## <a name="get"></a>Ophalen

De **Get** -methode van een resource haalt de status van de resource op zoals deze is geconfigureerd op het doel knooppunt. Deze status wordt geretourneerd als [hash](/powershell/module/microsoft.powershell.core/about/about_hash_tables)-tabel.
De sleutels van de **hashtabel** zijn de Configureer bare waarden, of para meters, die door de resource worden geaccepteerd.

De **Get** -methode wijst rechtstreeks toe aan de cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) . Wanneer u aanroept `Get-DSCConfiguration` , wordt de **Get** -methode van elke bron uitgevoerd in de huidige toegepaste configuratie. De LCM gebruikt de sleutel waarden die zijn opgeslagen in het `.mof` bestand als para meters voor elk bijbehorend bron exemplaar.

Dit is een voor beeld van uitvoer van een **service** resource waarmee de Spooler-service wordt geconfigureerd.

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won't be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

In de uitvoer ziet u de eigenschappen van de huidige waarde die kunnen worden geconfigureerd door de **service** resource.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a>Testen

De **test** methode van een bron bepaalt of het doel knooppunt momenteel compatibel is met de _gewenste status_van de resource. De **test** methode retourneert `$true` of `$false` alleen om aan te geven of het knoop punt compatibel is. Wanneer u [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)aanroept, roept de LCM de **test** methode van elke bron in de huidige toegepaste configuratie aan. De LCM gebruikt de sleutel waarden die zijn opgeslagen in het MOF-bestand als para meters voor elk bijbehorend bron exemplaar.

Als het resultaat van de **test** van een afzonderlijke resource is `$false` , wordt `Test-DSCConfiguration` Hiermee `$false` aangegeven dat het knoop punt niet aan het beleid voldoet. Als de **test** methode van alle resources retourneert `$true` , `Test-DSCConfiguration` wordt geretourneerd `$true` om aan te geven dat het knoop punt compatibel is.

```powershell
Test-DSCConfiguration
```

```output
True
```

Vanaf Power shell 5,0 is de **gedetailleerde** para meter toegevoegd. Het opgeven van **gedetailleerde** oorzaken voor `Test-DSCConfiguration` het retour neren van een object met verzamelingen resultaten voor compatibele en niet-compatibele resources.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Zie [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) voor meer informatie.

## <a name="set"></a>Instellen

De methode **set** van een resource probeert het knoop punt af te dwingen te voldoen aan de *gewenste status*van de resource. De **set** -methode is bedoeld om te worden **idempotent**. Dit betekent dat de **set** kan worden uitgevoerd meerdere keren en dat altijd hetzelfde resultaat oplevert zonder fouten. Wanneer u [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration)uitvoert, wordt door de LCM elke bron in de huidige toegepaste configuratie door lopen. De LCM haalt sleutel waarden voor het huidige bron exemplaar op uit het MOF-bestand en gebruikt deze als para meters voor de **test** methode. Als de **test** methode retourneert `$true` , is het knoop punt compatibel met de huidige resource en wordt de methode **set** overgeslagen. Als de **test** retourneert `$false` , is het knoop punt niet compatibel. De LCM geeft de sleutel waarden van het resource-exemplaar als para meters door aan de **ingestelde** methode van de resource. het knoop punt wordt teruggezet op naleving.

Door de para meters **uitgebreid** en **wachten** op te geven, kunt u de voortgang van de `Start-DSCConfiguration` cmdlet bekijken. In dit voor beeld is het knoop punt al compatibel. De `Verbose` uitvoer geeft aan dat de **ingestelde** methode is overgeslagen.

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a>Zie ook

- [Overzicht van Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Een SMB-pull-server instellen](../pull-server/pullServerSMB.md)
- [Een pull-client configureren](../pull-server/pullClientConfigID.md)
