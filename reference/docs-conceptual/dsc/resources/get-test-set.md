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
# <a name="get-test-set"></a><span data-ttu-id="f2dac-103">Get-test-set</span><span class="sxs-lookup"><span data-stu-id="f2dac-103">Get-Test-Set</span></span>

><span data-ttu-id="f2dac-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="f2dac-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f2dac-105">De gewenste status configuratie van Power shell is geconstrueerd rond een **Get**-, **test**-en **set** -proces.</span><span class="sxs-lookup"><span data-stu-id="f2dac-105">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="f2dac-106">DSC- [resources](resources.md) bevatten elk methoden voor het volt ooien van elk van deze bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="f2dac-106">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span>
<span data-ttu-id="f2dac-107">In een [configuratie](../configurations/configurations.md)definieert u resource blokken om sleutels in te vullen die para meters voor de **Get**-, **test**-en **set** -methoden van een resource worden.</span><span class="sxs-lookup"><span data-stu-id="f2dac-107">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="f2dac-108">Dit is de syntaxis voor een **service** bron blok.</span><span class="sxs-lookup"><span data-stu-id="f2dac-108">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="f2dac-109">De **service** resource configureert Windows-Services.</span><span class="sxs-lookup"><span data-stu-id="f2dac-109">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="f2dac-110">De methoden **Get**, **test**en **set** van de **service** Resource hebben parameter blokken die deze waarden accepteren.</span><span class="sxs-lookup"><span data-stu-id="f2dac-110">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="f2dac-111">De taal en methode waarmee de resource is gedefinieerd, bepalen hoe de methoden **ophalen**, **testen**en **instellen** worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="f2dac-111">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="f2dac-112">Omdat de **service** bron slechts één vereiste sleutel ( `Name` ) heeft, kan een **service** blok bron zo eenvoudig zijn als:</span><span class="sxs-lookup"><span data-stu-id="f2dac-112">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="f2dac-113">Wanneer u de configuratie hierboven compileert, worden de waarden die u opgeeft voor een sleutel opgeslagen in het `.mof` bestand dat wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f2dac-113">When you compile the Configuration above, the values you specify for a key are stored in the `.mof` file that is generated.</span></span> <span data-ttu-id="f2dac-114">Zie voor meer informatie [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="f2dac-114">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="f2dac-115">Als de [lokale Configuration Manager](../managing-nodes/metaConfig.md) (LCM) wordt toegepast, wordt de waarde ' spooler ' in het `.mof` bestand gelezen en door gegeven aan de para meter **name** van de methoden **Get**, **test**en **set** voor het exemplaar ' MyService ' van de **service** resource.</span><span class="sxs-lookup"><span data-stu-id="f2dac-115">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the `.mof` file, and pass it to the **Name** parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="f2dac-116">Ophalen</span><span class="sxs-lookup"><span data-stu-id="f2dac-116">Get</span></span>

<span data-ttu-id="f2dac-117">De **Get** -methode van een resource haalt de status van de resource op zoals deze is geconfigureerd op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="f2dac-117">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="f2dac-118">Deze status wordt geretourneerd als [hash](/powershell/module/microsoft.powershell.core/about/about_hash_tables)-tabel.</span><span class="sxs-lookup"><span data-stu-id="f2dac-118">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>
<span data-ttu-id="f2dac-119">De sleutels van de **hashtabel** zijn de Configureer bare waarden, of para meters, die door de resource worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="f2dac-119">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="f2dac-120">De **Get** -methode wijst rechtstreeks toe aan de cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="f2dac-120">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="f2dac-121">Wanneer u aanroept `Get-DSCConfiguration` , wordt de **Get** -methode van elke bron uitgevoerd in de huidige toegepaste configuratie.</span><span class="sxs-lookup"><span data-stu-id="f2dac-121">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="f2dac-122">De LCM gebruikt de sleutel waarden die zijn opgeslagen in het `.mof` bestand als para meters voor elk bijbehorend bron exemplaar.</span><span class="sxs-lookup"><span data-stu-id="f2dac-122">The LCM uses the key values stored in the `.mof` file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="f2dac-123">Dit is een voor beeld van uitvoer van een **service** resource waarmee de Spooler-service wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="f2dac-123">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="f2dac-124">In de uitvoer ziet u de eigenschappen van de huidige waarde die kunnen worden geconfigureerd door de **service** resource.</span><span class="sxs-lookup"><span data-stu-id="f2dac-124">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="f2dac-125">Testen</span><span class="sxs-lookup"><span data-stu-id="f2dac-125">Test</span></span>

<span data-ttu-id="f2dac-126">De **test** methode van een bron bepaalt of het doel knooppunt momenteel compatibel is met de _gewenste status_van de resource.</span><span class="sxs-lookup"><span data-stu-id="f2dac-126">The **Test** method of a resource determines if the target node is currently compliant with the resource's _desired state_.</span></span> <span data-ttu-id="f2dac-127">De **test** methode retourneert `$true` of `$false` alleen om aan te geven of het knoop punt compatibel is.</span><span class="sxs-lookup"><span data-stu-id="f2dac-127">The **Test** method returns `$true` or `$false` only to indicate whether the Node is compliant.</span></span> <span data-ttu-id="f2dac-128">Wanneer u [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)aanroept, roept de LCM de **test** methode van elke bron in de huidige toegepaste configuratie aan.</span><span class="sxs-lookup"><span data-stu-id="f2dac-128">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="f2dac-129">De LCM gebruikt de sleutel waarden die zijn opgeslagen in het MOF-bestand als para meters voor elk bijbehorend bron exemplaar.</span><span class="sxs-lookup"><span data-stu-id="f2dac-129">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="f2dac-130">Als het resultaat van de **test** van een afzonderlijke resource is `$false` , wordt `Test-DSCConfiguration` Hiermee `$false` aangegeven dat het knoop punt niet aan het beleid voldoet.</span><span class="sxs-lookup"><span data-stu-id="f2dac-130">If the result of any individual resource's **Test** is `$false`, `Test-DSCConfiguration` returns `$false` indicating that the Node is not compliant.</span></span> <span data-ttu-id="f2dac-131">Als de **test** methode van alle resources retourneert `$true` , `Test-DSCConfiguration` wordt geretourneerd `$true` om aan te geven dat het knoop punt compatibel is.</span><span class="sxs-lookup"><span data-stu-id="f2dac-131">If all resource's **Test** methods return `$true`, `Test-DSCConfiguration` returns `$true` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="f2dac-132">Vanaf Power shell 5,0 is de **gedetailleerde** para meter toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f2dac-132">Beginning in PowerShell 5.0, the **Detailed** parameter was added.</span></span> <span data-ttu-id="f2dac-133">Het opgeven van **gedetailleerde** oorzaken voor `Test-DSCConfiguration` het retour neren van een object met verzamelingen resultaten voor compatibele en niet-compatibele resources.</span><span class="sxs-lookup"><span data-stu-id="f2dac-133">Specifying **Detailed** causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="f2dac-134">Zie [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f2dac-134">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="f2dac-135">Instellen</span><span class="sxs-lookup"><span data-stu-id="f2dac-135">Set</span></span>

<span data-ttu-id="f2dac-136">De methode **set** van een resource probeert het knoop punt af te dwingen te voldoen aan de *gewenste status*van de resource.</span><span class="sxs-lookup"><span data-stu-id="f2dac-136">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="f2dac-137">De **set** -methode is bedoeld om te worden **idempotent**. Dit betekent dat de **set** kan worden uitgevoerd meerdere keren en dat altijd hetzelfde resultaat oplevert zonder fouten.</span><span class="sxs-lookup"><span data-stu-id="f2dac-137">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span> <span data-ttu-id="f2dac-138">Wanneer u [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration)uitvoert, wordt door de LCM elke bron in de huidige toegepaste configuratie door lopen.</span><span class="sxs-lookup"><span data-stu-id="f2dac-138">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="f2dac-139">De LCM haalt sleutel waarden voor het huidige bron exemplaar op uit het MOF-bestand en gebruikt deze als para meters voor de **test** methode.</span><span class="sxs-lookup"><span data-stu-id="f2dac-139">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="f2dac-140">Als de **test** methode retourneert `$true` , is het knoop punt compatibel met de huidige resource en wordt de methode **set** overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f2dac-140">If the **Test** method returns `$true`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="f2dac-141">Als de **test** retourneert `$false` , is het knoop punt niet compatibel.</span><span class="sxs-lookup"><span data-stu-id="f2dac-141">If the **Test** returns `$false`, the Node is non-compliant.</span></span> <span data-ttu-id="f2dac-142">De LCM geeft de sleutel waarden van het resource-exemplaar als para meters door aan de **ingestelde** methode van de resource. het knoop punt wordt teruggezet op naleving.</span><span class="sxs-lookup"><span data-stu-id="f2dac-142">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="f2dac-143">Door de para meters **uitgebreid** en **wachten** op te geven, kunt u de voortgang van de `Start-DSCConfiguration` cmdlet bekijken.</span><span class="sxs-lookup"><span data-stu-id="f2dac-143">By specifying the **Verbose** and **Wait** parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="f2dac-144">In dit voor beeld is het knoop punt al compatibel.</span><span class="sxs-lookup"><span data-stu-id="f2dac-144">In this example, the Node is already compliant.</span></span> <span data-ttu-id="f2dac-145">De `Verbose` uitvoer geeft aan dat de **ingestelde** methode is overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f2dac-145">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f2dac-146">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f2dac-146">See also</span></span>

- [<span data-ttu-id="f2dac-147">Overzicht van Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="f2dac-147">Azure Automation DSC Overview</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="f2dac-148">Een SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="f2dac-148">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="f2dac-149">Een pull-client configureren</span><span class="sxs-lookup"><span data-stu-id="f2dac-149">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
