---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Afhankelijkheden van meerdere knooppunten opgeven
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942053"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="264c6-103">Afhankelijkheden van meerdere knooppunten opgeven</span><span class="sxs-lookup"><span data-stu-id="264c6-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="264c6-104">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="264c6-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="264c6-105">DSC biedt speciale resources, **WaitForAll**, **WaitForAny**en **WaitForSome** die in configuraties kunnen worden gebruikt om afhankelijkheden op te geven voor configuraties op andere knoop punten.</span><span class="sxs-lookup"><span data-stu-id="264c6-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="264c6-106">Het gedrag van deze resources is als volgt:</span><span class="sxs-lookup"><span data-stu-id="264c6-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="264c6-107">**WaitForAll**: slaagt als de opgegeven resource de gewenste status heeft op alle doel knooppunten die zijn gedefinieerd in de eigenschap **nodenaam** .</span><span class="sxs-lookup"><span data-stu-id="264c6-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="264c6-108">**WaitForAny**: slaagt als de opgegeven resource de gewenste status heeft op ten minste één van de doel knooppunten die zijn gedefinieerd in de eigenschap **nodenaam** .</span><span class="sxs-lookup"><span data-stu-id="264c6-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="264c6-109">**WaitForSome**: Hiermee geeft u een eigenschap **NodeCount** op in aanvulling op de eigenschap **nodenaam** .</span><span class="sxs-lookup"><span data-stu-id="264c6-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="264c6-110">De resource slaagt als de resource de gewenste status heeft voor een minimum aantal knoop punten (opgegeven door **NodeCount**) dat is gedefinieerd door de eigenschap **nodenaam** .</span><span class="sxs-lookup"><span data-stu-id="264c6-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="264c6-111">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="264c6-111">Syntax</span></span>

<span data-ttu-id="264c6-112">De **WaitForAll** -en **WaitForAny** -resources delen dezelfde syntaxis.</span><span class="sxs-lookup"><span data-stu-id="264c6-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="264c6-113">Vervang \<resource type\> in het onderstaande voor beeld met een **WaitForAny** of **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="264c6-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="264c6-114">Net als het sleutel woord **DependsOn** moet u de naam als ' [resource type] ResourceName ' Format teren.</span><span class="sxs-lookup"><span data-stu-id="264c6-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="264c6-115">Als de resource deel uitmaakt van een afzonderlijke [configuratie](configurations.md), neemt u de **configuratiepad** op in de opgemaakte teken reeks ' [resource type] ResourceName:: [configuratiepad]:: [configuratiepad] '.</span><span class="sxs-lookup"><span data-stu-id="264c6-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="264c6-116">De **knooppunt** naam is de computer of het knoop punt waarop de huidige resource moet wachten.</span><span class="sxs-lookup"><span data-stu-id="264c6-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="264c6-117">De **WaitForSome** -resource heeft een vergelijk bare syntaxis voor het bovenstaande voor beeld, maar voegt de **NodeCount** -sleutel toe.</span><span class="sxs-lookup"><span data-stu-id="264c6-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="264c6-118">De **NodeCount** geeft aan hoeveel knoop punten de huidige resource moet wachten.</span><span class="sxs-lookup"><span data-stu-id="264c6-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="264c6-119">Alle **WaitForXXXX** delen de volgende syntaxis sleutels.</span><span class="sxs-lookup"><span data-stu-id="264c6-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="264c6-120">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="264c6-120">Property</span></span>|  <span data-ttu-id="264c6-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="264c6-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="264c6-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="264c6-122">RetryIntervalSec</span></span>| <span data-ttu-id="264c6-123">Het aantal seconden voordat een nieuwe poging wordt gedaan.</span><span class="sxs-lookup"><span data-stu-id="264c6-123">The number of seconds before retrying.</span></span> <span data-ttu-id="264c6-124">De minimum waarde is 1.</span><span class="sxs-lookup"><span data-stu-id="264c6-124">Minimum is 1.</span></span>|
| <span data-ttu-id="264c6-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="264c6-125">RetryCount</span></span>| <span data-ttu-id="264c6-126">Het maximum aantal keren dat opnieuw moet worden geprobeerd.</span><span class="sxs-lookup"><span data-stu-id="264c6-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="264c6-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="264c6-127">ThrottleLimit</span></span>| <span data-ttu-id="264c6-128">Aantal machines om tegelijkertijd verbinding te maken.</span><span class="sxs-lookup"><span data-stu-id="264c6-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="264c6-129">De standaard instelling is `New-CimSession` standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="264c6-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="264c6-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="264c6-130">DependsOn</span></span> | <span data-ttu-id="264c6-131">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="264c6-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="264c6-132">Zie [DependsOn](resource-depends-on.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="264c6-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="264c6-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="264c6-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="264c6-134">Zie [DSC gebruiken met gebruikers referenties](./runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="264c6-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="264c6-135">WaitForXXXX-resources gebruiken</span><span class="sxs-lookup"><span data-stu-id="264c6-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="264c6-136">Elke **WaitForXXXX** -resource wacht totdat de opgegeven resources zijn voltooid op het opgegeven knoop punt.</span><span class="sxs-lookup"><span data-stu-id="264c6-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="264c6-137">Andere resources in dezelfde configuratie kunnen vervolgens *afhankelijk zijn* van de **WaitForXXXX** -bron met behulp van de **DependsOn** -sleutel.</span><span class="sxs-lookup"><span data-stu-id="264c6-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="264c6-138">In de volgende configuratie kan het doel knooppunt bijvoorbeeld wachten tot de **xADDomain** -resource op het **eigendc** -knoop punt is voltooid met een maximum aantal van 30 nieuwe pogingen, met een interval van 15 seconden voordat het doel knooppunt kan worden toegevoegd aan het domein.</span><span class="sxs-lookup"><span data-stu-id="264c6-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="264c6-139">De **WaitForXXX** -resources proberen standaard één keer en vervolgens mislukt.</span><span class="sxs-lookup"><span data-stu-id="264c6-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="264c6-140">Hoewel dit niet vereist is, wilt u meestal een **RetryCount** en **RetryIntervalSec**opgeven.</span><span class="sxs-lookup"><span data-stu-id="264c6-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

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

<span data-ttu-id="264c6-141">Wanneer u de configuratie compileert, worden er twee. MOF-bestanden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="264c6-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="264c6-142">Beide '. mof '-bestanden Toep assen op de doel knooppunten met behulp van de cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)</span><span class="sxs-lookup"><span data-stu-id="264c6-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="264c6-143">**WaitForXXX** -bronnen gebruiken Windows Remote Management om de status van andere knoop punten te controleren.</span><span class="sxs-lookup"><span data-stu-id="264c6-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="264c6-144">Zie [beveiligings overwegingen voor externe communicatie van Power shell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)voor meer informatie over de vereisten voor de poort en de beveiliging van WinRM.</span><span class="sxs-lookup"><span data-stu-id="264c6-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="264c6-145">Zie ook</span><span class="sxs-lookup"><span data-stu-id="264c6-145">See Also</span></span>

- [<span data-ttu-id="264c6-146">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="264c6-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="264c6-147">Resource afhankelijkheden gebruiken</span><span class="sxs-lookup"><span data-stu-id="264c6-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="264c6-148">DSC-resources</span><span class="sxs-lookup"><span data-stu-id="264c6-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="264c6-149">De lokale Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="264c6-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
