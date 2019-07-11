---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Afhankelijkheden van meerdere knooppunten opgeven
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734685"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="1bc2f-103">Afhankelijkheden van meerdere knooppunten opgeven</span><span class="sxs-lookup"><span data-stu-id="1bc2f-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="1bc2f-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1bc2f-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1bc2f-105">DSC biedt speciale resources **WaitForAll**, **WaitForAny**, en **WaitForSome** die kunnen worden gebruikt in configuraties met afhankelijkheden opgeven voor configuraties op andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="1bc2f-106">Het gedrag van deze resources is als volgt:</span><span class="sxs-lookup"><span data-stu-id="1bc2f-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="1bc2f-107">**WaitForAll**: Is geslaagd als de opgegeven resource in de gewenste status van alle doelknooppunten gedefinieerd is in de **knooppuntnaam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="1bc2f-108">**WaitForAny**: Is geslaagd als de opgegeven resource in de gewenste status op ten minste één van de doelknooppunten gedefinieerd is in de **knooppuntnaam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="1bc2f-109">**WaitForSome**: Hiermee geeft u een **NodeCount** eigenschap naast een **knooppuntnaam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="1bc2f-110">De resource is geslaagd als de resource in de gewenste status op een minimum aantal knooppunten is (opgegeven door **NodeCount**) gedefinieerd door de **knooppuntnaam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="1bc2f-111">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1bc2f-111">Syntax</span></span>

<span data-ttu-id="1bc2f-112">De **WaitForAll** en **WaitForAny** resources delen dezelfde syntaxis.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="1bc2f-113">Vervang \<ResourceType\> in het onderstaande voorbeeld met ofwel **WaitForAny** of **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="1bc2f-114">Net als de **DependsOn** trefwoord, moet u de naam als 'ResourceName [ResourceType]'.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="1bc2f-115">Als de resource deel uitmaakt van een afzonderlijke [configuratie](configurations.md), bevatten de **ConfigurationName** in de opgemaakte tekenreeks "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName] '.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="1bc2f-116">De **knooppuntnaam** is de computer, of het knooppunt waarop de huidige bron moet wachten.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="1bc2f-117">De **WaitForSome** resource heeft een vergelijkbare syntaxis in het bovenstaande voorbeeld, maar voegt de **NodeCount** sleutel.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="1bc2f-118">De **NodeCount** geeft aan hoeveel knooppunten die de huidige bron moet worden gewacht op.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="1bc2f-119">Alle **WaitForXXXX** delen van de volgende syntaxis van de sleutels.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="1bc2f-120">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="1bc2f-120">Property</span></span>|  <span data-ttu-id="1bc2f-121">Description</span><span class="sxs-lookup"><span data-stu-id="1bc2f-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="1bc2f-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="1bc2f-122">RetryIntervalSec</span></span>| <span data-ttu-id="1bc2f-123">Het aantal seconden alvorens het opnieuw te proberen.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-123">The number of seconds before retrying.</span></span> <span data-ttu-id="1bc2f-124">Minimumwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-124">Minimum is 1.</span></span>|
| <span data-ttu-id="1bc2f-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="1bc2f-125">RetryCount</span></span>| <span data-ttu-id="1bc2f-126">Het maximale aantal nieuwe pogingen.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="1bc2f-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="1bc2f-127">ThrottleLimit</span></span>| <span data-ttu-id="1bc2f-128">Het aantal machines tegelijk verbinding kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="1bc2f-129">De standaardwaarde is `New-CimSession` standaard.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="1bc2f-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1bc2f-130">DependsOn</span></span> | <span data-ttu-id="1bc2f-131">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1bc2f-132">Zie voor meer informatie, [DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="1bc2f-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="1bc2f-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1bc2f-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="1bc2f-134">Zie [DSC gebruiken met de referenties van gebruiker](./runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="1bc2f-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="1bc2f-135">Met behulp van WaitForXXXX bronnen</span><span class="sxs-lookup"><span data-stu-id="1bc2f-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="1bc2f-136">Elke **WaitForXXXX** resource wacht tot de opgegeven bronnen voor het opgegeven knooppunt.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="1bc2f-137">Andere resources in dezelfde configuratie kunnen vervolgens *afhankelijk zijn van* de **WaitForXXXX** resource met behulp van de **DependsOn** sleutel.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="1bc2f-138">Bijvoorbeeld, in de volgende configuratie, het doelknooppunt wordt gewacht tot de **xADDomain** resource moet worden voltooid op de **Eigendc** knooppunt met een maximum van 30 nieuwe pogingen, met intervallen van 15 seconden, voordat de doelknooppunt kan deelnemen aan het domein.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="1bc2f-139">Standaard de **WaitForXXX** resources één keer proberen en voert vervolgens failover uit.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="1bc2f-140">Hoewel het niet vereist is, zult u doorgaans om op te geven een **RetryCount** en **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

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

<span data-ttu-id="1bc2f-141">Wanneer u de configuratie compileren, worden "twee MOF-bestanden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="1bc2f-142">Beide ".mof" bestanden van toepassing op de doelknooppunten met behulp van de [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span><span class="sxs-lookup"><span data-stu-id="1bc2f-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="1bc2f-143">**WaitForXXX** resources Windows Remote Management gebruiken om te controleren of de status van andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="1bc2f-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="1bc2f-144">Zie voor meer informatie over de poort en beveiligingsvereisten voor WinRM [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="1bc2f-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="1bc2f-145">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1bc2f-145">See Also</span></span>

- [<span data-ttu-id="1bc2f-146">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="1bc2f-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="1bc2f-147">Resource-afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="1bc2f-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="1bc2f-148">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="1bc2f-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="1bc2f-149">De Local Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="1bc2f-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
