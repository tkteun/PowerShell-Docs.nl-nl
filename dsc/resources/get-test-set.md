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
# <a name="get-test-set"></a><span data-ttu-id="fa412-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="fa412-103">Get-Test-Set</span></span>

><span data-ttu-id="fa412-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fa412-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Ophalen, testen, en instellen](/media/get-test-set.png)

<span data-ttu-id="fa412-106">PowerShell Desired State Configuration is opgebouwd rond een **ophalen**, **Test**, en **ingesteld** proces.</span><span class="sxs-lookup"><span data-stu-id="fa412-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="fa412-107">DSC [resources](resources.md) elk bevat methoden voor het voltooien van elk van deze bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="fa412-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="fa412-108">In een [configuratie](../configurations/configurations.md), definieert u de resource-blokken in te vullen in sleutels die parameters voor een resource worden **ophalen**, **Test**, en **instellen** methoden.</span><span class="sxs-lookup"><span data-stu-id="fa412-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="fa412-109">Dit is de syntaxis voor een **Service** resource blokkeren.</span><span class="sxs-lookup"><span data-stu-id="fa412-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="fa412-110">De **Service** resource configureert Windows-services.</span><span class="sxs-lookup"><span data-stu-id="fa412-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="fa412-111">De **ophalen**, **Test**, en **ingesteld** methoden van de **Service** resource heeft parameterblokken die deze waarden accepteren.</span><span class="sxs-lookup"><span data-stu-id="fa412-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="fa412-112">De taal en de methode die wordt gebruikt voor het definiëren van de resource wordt bepaald hoe de **ophalen**, **Test**, en **ingesteld** methoden worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="fa412-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="fa412-113">Omdat de **Service** resource heeft slechts één sleutel (`Name`), een **Service** blok resource kan worden net zo eenvoudig als dit:</span><span class="sxs-lookup"><span data-stu-id="fa412-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="fa412-114">Wanneer u de bovenstaande configuratie compileren, worden de waarden die u voor een sleutel opgeeft worden opgeslagen in het bestand '.mof' die wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="fa412-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="fa412-115">Zie voor meer informatie, [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="fa412-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="fa412-116">Wanneer toegepast, de [Local Configuration Manager](../managing-nodes/metaConfig.md) wordt de waarde 'Spooler' lezen uit het bestand '.mof' en doorgegeven aan de `-Name` parameter van de **ophalen**, **Test**, en **ingesteld** methoden voor het exemplaar 'MyService' van de **Service** resource.</span><span class="sxs-lookup"><span data-stu-id="fa412-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="fa412-117">Ophalen</span><span class="sxs-lookup"><span data-stu-id="fa412-117">Get</span></span>

<span data-ttu-id="fa412-118">De **ophalen** methode van een resource, wordt de status van de resource die is geconfigureerd op de doel-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="fa412-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="fa412-119">Deze status wordt geretourneerd als een [hashtabel](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="fa412-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="fa412-120">De sleutels van de **hashtabel** zal worden de waarden kunnen worden geconfigureerd of de parameters, accepteert de resource.</span><span class="sxs-lookup"><span data-stu-id="fa412-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="fa412-121">De **ophalen** methode wijst rechtstreeks naar de [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa412-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="fa412-122">Als u aanroept `Get-DSCConfiguration`, de LCM wordt uitgevoerd de **ophalen** methode van elke resource in de configuratie van dat momenteel wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="fa412-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="fa412-123">De LCM maakt gebruik van de sleutelwaarden die zijn opgeslagen in het bestand '.mof' als parameters voor elke bijbehorende resource-instantie.</span><span class="sxs-lookup"><span data-stu-id="fa412-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="fa412-124">Dit voorbeeld van uitvoer van is een **Service** resource waarmee de service 'Spooler' worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="fa412-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="fa412-125">De uitvoer ziet u de huidige waarde-eigenschappen kunnen worden geconfigureerd door de **Service** resource.</span><span class="sxs-lookup"><span data-stu-id="fa412-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="fa412-126">Test</span><span class="sxs-lookup"><span data-stu-id="fa412-126">Test</span></span>

<span data-ttu-id="fa412-127">De **Test** methode van een resource wordt bepaald of het doelknooppunt momenteel compatibel zijn met de resource is *desired state*.</span><span class="sxs-lookup"><span data-stu-id="fa412-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="fa412-128">De **Test** methode retourneert `$True` of `$False` alleen om aan te geven of het knooppunt dat compatibel is.</span><span class="sxs-lookup"><span data-stu-id="fa412-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="fa412-129">Als u aanroept [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), aanroepen van de LCM de **Test** methode van elke resource in de configuratie van dat momenteel wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="fa412-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="fa412-130">De LCM maakt gebruik van de sleutelwaarden die zijn opgeslagen in het bestand '.mof' als parameters voor elke bijbehorende resource-instantie.</span><span class="sxs-lookup"><span data-stu-id="fa412-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="fa412-131">Als het resultaat van een afzonderlijke resource **Test** is `$False`, `Test-DSCConfiguration` retourneert `$False` die aangeeft dat het knooppunt niet compatibel is.</span><span class="sxs-lookup"><span data-stu-id="fa412-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="fa412-132">Als alle resource **Test** methoden retourneren `$True`, `Test-DSCConfiguration` retourneert `$True` om aan te geven dat het knooppunt compatibel is.</span><span class="sxs-lookup"><span data-stu-id="fa412-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="fa412-133">PowerShell 5.0, vanaf de `-Detailed` parameter is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="fa412-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="fa412-134">Op te geven `-Detailed` zorgt ervoor dat `Test-DSCConfiguration` als resultaat een object met verzamelingen van resultaten voor compatibele en niet-compatibele resources.</span><span class="sxs-lookup"><span data-stu-id="fa412-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="fa412-135">Zie voor meer informatie, [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="fa412-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="fa412-136">Instellen</span><span class="sxs-lookup"><span data-stu-id="fa412-136">Set</span></span>

<span data-ttu-id="fa412-137">De **ingesteld** methode van een resource wordt geprobeerd om af te dwingen van het knooppunt om te voldoen aan de resource *desired state*.</span><span class="sxs-lookup"><span data-stu-id="fa412-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="fa412-138">De **ingesteld** methode is bedoeld om te worden **idempotent**, dit houdt in dat **ingesteld** kan worden meerdere keren uitvoeren en altijd kunnen genieten van hetzelfde resultaat zonder fouten.</span><span class="sxs-lookup"><span data-stu-id="fa412-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="fa412-139">Bij het uitvoeren van [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), de LCM bladeren door elke resource in de configuratie van dat momenteel wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="fa412-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="fa412-140">De LCM sleutelwaarden voor het huidige exemplaar van de resource opgehaald uit het bestand '.mof' en deze gebruikt als parameters voor de **Test** methode.</span><span class="sxs-lookup"><span data-stu-id="fa412-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="fa412-141">Als de **Test** methode retourneert `$True`, het knooppunt is compatibel zijn met de huidige resource en de **ingesteld** methode is overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="fa412-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="fa412-142">Als de **Test** retourneert `$False`, het knooppunt is niet-compatibel.</span><span class="sxs-lookup"><span data-stu-id="fa412-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="fa412-143">De LCM geeft de bron van de instantie sleutelwaarden als parameters aan van de resource **ingesteld** methode, het knooppunt voor de naleving te herstellen.</span><span class="sxs-lookup"><span data-stu-id="fa412-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="fa412-144">Door op te geven de `-Verbose` en `-Wait` parameters, u kunt controleren of de voortgang van de `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa412-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="fa412-145">In dit voorbeeld is het knooppunt al conform.</span><span class="sxs-lookup"><span data-stu-id="fa412-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="fa412-146">De `Verbose` uitvoer geeft aan dat de **ingesteld** methode is overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="fa412-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fa412-147">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fa412-147">See also</span></span>

- [<span data-ttu-id="fa412-148">Overzicht van Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="fa412-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="fa412-149">Instellen van een SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="fa412-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="fa412-150">Een pull-client configureren</span><span class="sxs-lookup"><span data-stu-id="fa412-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
