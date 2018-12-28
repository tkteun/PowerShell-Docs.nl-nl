---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Get-Test-Set
ms.openlocfilehash: e46710954679bf20f4536c6efbcbd4dafd9e629e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403984"
---
# <a name="get-test-set"></a>Get-Test-Set

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

![Ophalen, testen, en instellen](/media/get-test-set.png)

PowerShell Desired State Configuration is opgebouwd rond een **ophalen**, **Test**, en **ingesteld** proces. DSC [resources](resources.md) elk bevat methoden voor het voltooien van elk van deze bewerkingen. In een [configuratie](../configurations/configurations.md), definieert u de resource-blokken in te vullen in sleutels die parameters voor een resource worden **ophalen**, **Test**, en **instellen** methoden.

Dit is de syntaxis voor een **Service** resource blokkeren. De **Service** resource configureert Windows-services.

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

De **ophalen**, **Test**, en **ingesteld** methoden van de **Service** resource heeft parameterblokken die deze waarden accepteren.

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
> De taal en de methode die wordt gebruikt voor het definiëren van de resource wordt bepaald hoe de **ophalen**, **Test**, en **ingesteld** methoden worden gedefinieerd.

Omdat de **Service** resource heeft slechts één sleutel (`Name`), een **Service** blok resource kan worden net zo eenvoudig als dit:

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

Wanneer u de bovenstaande configuratie compileren, worden de waarden die u voor een sleutel opgeeft worden opgeslagen in het bestand '.mof' die wordt gegenereerd. Zie voor meer informatie, [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

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

Wanneer toegepast, de [Local Configuration Manager](../managing-nodes/metaConfig.md) wordt de waarde 'Spooler' lezen uit het bestand '.mof' en doorgegeven aan de `-Name` parameter van de **ophalen**, **Test**, en **ingesteld** methoden voor het exemplaar 'MyService' van de **Service** resource.

## <a name="get"></a>Ophalen

De **ophalen** methode van een resource, wordt de status van de resource die is geconfigureerd op de doel-knooppunt. Deze status wordt geretourneerd als een [hashtabel](/powershell/module/microsoft.powershell.core/about/about_hash_tables). De sleutels van de **hashtabel** zal worden de waarden kunnen worden geconfigureerd of de parameters, accepteert de resource.

De **ophalen** methode wijst rechtstreeks naar de [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet. Als u aanroept `Get-DSCConfiguration`, de LCM wordt uitgevoerd de **ophalen** methode van elke resource in de configuratie van dat momenteel wordt toegepast. De LCM maakt gebruik van de sleutelwaarden die zijn opgeslagen in het bestand '.mof' als parameters voor elke bijbehorende resource-instantie.

Dit voorbeeld van uitvoer van is een **Service** resource waarmee de service 'Spooler' worden geconfigureerd.

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
                       this service, you won’t be able to print or see your printers.
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

De uitvoer ziet u de huidige waarde-eigenschappen kunnen worden geconfigureerd door de **Service** resource.

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

## <a name="test"></a>Test

De **Test** methode van een resource wordt bepaald of het doelknooppunt momenteel compatibel zijn met de resource is *desired state*. De **Test** methode retourneert `$True` of `$False` alleen om aan te geven of het knooppunt dat compatibel is.
Als u aanroept [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), aanroepen van de LCM de **Test** methode van elke resource in de configuratie van dat momenteel wordt toegepast. De LCM maakt gebruik van de sleutelwaarden die zijn opgeslagen in het bestand '.mof' als parameters voor elke bijbehorende resource-instantie.

Als het resultaat van een afzonderlijke resource **Test** is `$False`, `Test-DSCConfiguration` retourneert `$False` die aangeeft dat het knooppunt niet compatibel is. Als alle resource **Test** methoden retourneren `$True`, `Test-DSCConfiguration` retourneert `$True` om aan te geven dat het knooppunt compatibel is.

```powershell
Test-DSCConfiguration
```

```output
True
```

PowerShell 5.0, vanaf de `-Detailed` parameter is toegevoegd. Op te geven `-Detailed` zorgt ervoor dat `Test-DSCConfiguration` als resultaat een object met verzamelingen van resultaten voor compatibele en niet-compatibele resources.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Zie voor meer informatie, [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Instellen

De **ingesteld** methode van een resource wordt geprobeerd om af te dwingen van het knooppunt om te voldoen aan de resource *desired state*. De **ingesteld** methode is bedoeld om te worden **idempotent**, dit houdt in dat **ingesteld** kan worden meerdere keren uitvoeren en altijd kunnen genieten van hetzelfde resultaat zonder fouten.  Bij het uitvoeren van [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), de LCM bladeren door elke resource in de configuratie van dat momenteel wordt toegepast. De LCM sleutelwaarden voor het huidige exemplaar van de resource opgehaald uit het bestand '.mof' en deze gebruikt als parameters voor de **Test** methode. Als de **Test** methode retourneert `$True`, het knooppunt is compatibel zijn met de huidige resource en de **ingesteld** methode is overgeslagen. Als de **Test** retourneert `$False`, het knooppunt is niet-compatibel.  De LCM geeft de bron van de instantie sleutelwaarden als parameters aan van de resource **ingesteld** methode, het knooppunt voor de naleving te herstellen.

Door op te geven de `-Verbose` en `-Wait` parameters, u kunt controleren of de voortgang van de `Start-DSCConfiguration` cmdlet. In dit voorbeeld is het knooppunt al conform. De `Verbose` uitvoer geeft aan dat de **ingesteld** methode is overgeslagen.

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

- [Overzicht van Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Instellen van een SMB-pull-server](../pull-server/pullServerSMB.md)
- [Een pull-client configureren](../pull-server/pullClientConfigID.md)
