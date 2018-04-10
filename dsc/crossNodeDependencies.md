---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Afhankelijkheden van meerdere knooppunten opgeven
ms.openlocfilehash: c563563118c4df8aeee442d3b30b79f7b7700fc7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="71a61-103">Afhankelijkheden van meerdere knooppunten opgeven</span><span class="sxs-lookup"><span data-stu-id="71a61-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="71a61-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="71a61-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="71a61-105">DSC biedt speciale bronnen **WaitForAll**, **WaitForAny**, en **WaitForSome** die kunnen worden gebruikt in configuraties afhankelijkheden op configuraties op andere opgeven knooppunten.</span><span class="sxs-lookup"><span data-stu-id="71a61-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="71a61-106">Het gedrag van deze resources is als volgt:</span><span class="sxs-lookup"><span data-stu-id="71a61-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="71a61-107">**WaitForAll**: is geslaagd als de opgegeven bron in de gewenste status op alle doelknooppunten gedefinieerd is in de **NodeName** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="71a61-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="71a61-108">**WaitForAny**: is geslaagd als de opgegeven bron in de gewenste status op ten minste één van de doelknooppunten gedefinieerd is in de **NodeName** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="71a61-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="71a61-109">**WaitForSome**: Hiermee geeft u een **NodeCount** eigenschap naast een **NodeName** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="71a61-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="71a61-110">De resource is geslaagd als de bron in de gewenste status van een minimum aantal knooppunten is (opgegeven door **NodeCount**) gedefinieerd door de **NodeName** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="71a61-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="71a61-111">WaitForXXXX-bronnen</span><span class="sxs-lookup"><span data-stu-id="71a61-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="71a61-112">Gebruik de **WaitForXXXX** resources, hebt u een resource-blok van dat resourcetype waarmee de DSC-resource en de knooppunten te wachten.</span><span class="sxs-lookup"><span data-stu-id="71a61-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="71a61-113">Vervolgens gebruikt u de **DependsOn** eigenschap in een andere bron gegevensblokken die zich in de configuratie moet worden gewacht op de voorwaarden van de **WaitForXXXX** knooppunt om te slagen.</span><span class="sxs-lookup"><span data-stu-id="71a61-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="71a61-114">Bijvoorbeeld, in de volgende configuratie het doelknooppunt wacht tot de **xADDomain** resource moet worden voltooid op de **Eigendc** knooppunt met 30 maximumaantal nieuwe pogingen, met intervallen van 15 seconden, voordat de doelknooppunt kunt deelnemen aan het domein.</span><span class="sxs-lookup"><span data-stu-id="71a61-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

><span data-ttu-id="71a61-115">**Opmerking:** standaard de WaitForXXX resources één keer te proberen en voert vervolgens failover uit.</span><span class="sxs-lookup"><span data-stu-id="71a61-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="71a61-116">Hoewel dit niet vereist is, wilt u waarschijnlijk een interval voor opnieuw proberen en de telling opgeven.</span><span class="sxs-lookup"><span data-stu-id="71a61-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="71a61-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="71a61-117">See Also</span></span>
* [<span data-ttu-id="71a61-118">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="71a61-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="71a61-119">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="71a61-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="71a61-120">De lokale Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="71a61-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)