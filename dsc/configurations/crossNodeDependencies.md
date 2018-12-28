---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Afhankelijkheden van meerdere knooppunten opgeven
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403890"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="8841b-103">Afhankelijkheden van meerdere knooppunten opgeven</span><span class="sxs-lookup"><span data-stu-id="8841b-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="8841b-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8841b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8841b-105">DSC biedt speciale resources **WaitForAll**, **WaitForAny**, en **WaitForSome** die kunnen worden gebruikt in configuraties met afhankelijkheden opgeven voor configuraties op andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="8841b-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="8841b-106">Het gedrag van deze resources is als volgt:</span><span class="sxs-lookup"><span data-stu-id="8841b-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="8841b-107">**WaitForAll**: Is geslaagd als de opgegeven resource in de gewenste status van alle doelknooppunten gedefinieerd is in de **knooppuntnaam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="8841b-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="8841b-108">**WaitForAny**: Is geslaagd als de opgegeven resource in de gewenste status op ten minste één van de doelknooppunten gedefinieerd is in de **knooppuntnaam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="8841b-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="8841b-109">**WaitForSome**: Hiermee geeft u een **NodeCount** eigenschap naast een **knooppuntnaam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="8841b-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="8841b-110">De resource is geslaagd als de resource in de gewenste status op een minimum aantal knooppunten is (opgegeven door **NodeCount**) gedefinieerd door de **knooppuntnaam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="8841b-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="8841b-111">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8841b-111">Syntax</span></span>

<span data-ttu-id="8841b-112">De **WaitForAll** en **WaitForAny** resources delen dezelfde syntaxis.</span><span class="sxs-lookup"><span data-stu-id="8841b-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="8841b-113">Vervang \<ResourceType\> in het onderstaande voorbeeld met ofwel **WaitForAny** of **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="8841b-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="8841b-114">Net als de **DependsOn** trefwoord, moet u de naam als 'ResourceName [ResourceType]'.</span><span class="sxs-lookup"><span data-stu-id="8841b-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="8841b-115">Als de resource deel uitmaakt van een afzonderlijke [configuratie](configurations.md), bevatten de **ConfigurationName** in de opgemaakte tekenreeks "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName] '.</span><span class="sxs-lookup"><span data-stu-id="8841b-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="8841b-116">De **knooppuntnaam** is de computer, of het knooppunt waarop de huidige bron moet wachten.</span><span class="sxs-lookup"><span data-stu-id="8841b-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

<span data-ttu-id="8841b-117">De **WaitForSome** resource heeft een vergelijkbare syntaxis in het bovenstaande voorbeeld, maar voegt de **NodeCount** sleutel.</span><span class="sxs-lookup"><span data-stu-id="8841b-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="8841b-118">De **NodeCount** geeft aan hoeveel knooppunten die de huidige bron moet worden gewacht op.</span><span class="sxs-lookup"><span data-stu-id="8841b-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

<span data-ttu-id="8841b-119">Alle **WaitForXXXX** delen van de volgende syntaxis van de sleutels.</span><span class="sxs-lookup"><span data-stu-id="8841b-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="8841b-120">|  De eigenschap |  Beschrijving || RetryIntervalSec | Het aantal seconden alvorens het opnieuw te proberen.</span><span class="sxs-lookup"><span data-stu-id="8841b-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="8841b-121">Minimumwaarde is 1. | | RetryCount | Het maximum aantal nieuwe pogingen. | | ThrottleLimit | Het aantal machines tegelijk verbinding kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="8841b-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="8841b-122">De standaardwaarde is `New-CimSession` standaard. | | DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="8841b-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8841b-123">Zie voor meer informatie, [DependsOn](resource-depends-on.md)|| PsDscRunAsCredential | Zie [DSC gebruiken met de referenties van gebruiker](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="8841b-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="8841b-124">Met behulp van WaitForXXXX bronnen</span><span class="sxs-lookup"><span data-stu-id="8841b-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="8841b-125">Elke **WaitForXXXX** resource wacht tot de opgegeven bronnen voor het opgegeven knooppunt.</span><span class="sxs-lookup"><span data-stu-id="8841b-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="8841b-126">Andere resources in dezelfde configuratie kunnen vervolgens *afhankelijk zijn van* de **WaitForXXXX** resource met behulp van de **DependsOn** sleutel.</span><span class="sxs-lookup"><span data-stu-id="8841b-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="8841b-127">Bijvoorbeeld, in de volgende configuratie, het doelknooppunt wordt gewacht tot de **xADDomain** resource moet worden voltooid op de **Eigendc** knooppunt met een maximum van 30 nieuwe pogingen, met intervallen van 15 seconden, voordat de doelknooppunt kan deelnemen aan het domein.</span><span class="sxs-lookup"><span data-stu-id="8841b-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

<span data-ttu-id="8841b-128">Wanneer u de configuratie compileren, worden "twee MOF-bestanden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="8841b-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="8841b-129">Beide ".mof" bestanden van toepassing op de doelknooppunten met behulp van de [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span><span class="sxs-lookup"><span data-stu-id="8841b-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="8841b-130">**Opmerking:** Standaard de WaitForXXX resources één keer proberen en voert vervolgens failover uit.</span><span class="sxs-lookup"><span data-stu-id="8841b-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="8841b-131">Hoewel het niet vereist is, zult u doorgaans om op te geven een **RetryCount** en **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="8841b-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="8841b-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8841b-132">See Also</span></span>

- [<span data-ttu-id="8841b-133">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="8841b-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="8841b-134">Resource-afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="8841b-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="8841b-135">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="8841b-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="8841b-136">De Local Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="8841b-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
