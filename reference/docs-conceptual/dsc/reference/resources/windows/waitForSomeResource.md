---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC WaitForSome-resource
ms.openlocfilehash: 91589c84518a2bd0f4816d11aa011dec1d5305e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941262"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="f4ae4-103">DSC WaitForSome-resource</span><span class="sxs-lookup"><span data-stu-id="f4ae4-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="f4ae4-104">Van toepassing op: Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="f4ae4-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="f4ae4-105">De resource van de desired state Configuration (DSC) **WaitForSome** kan worden gebruikt binnen een knooppunt blok in een [DSC-configuratie](../../../configurations/configurations.md) om afhankelijkheden op te geven voor de configuraties op andere knoop punten.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="f4ae4-106">Deze resource slaagt als de resource die is opgegeven door de eigenschap **ResourceName** de gewenste status heeft voor een minimum aantal knoop punten (opgegeven door **NodeCount**) dat is gedefinieerd door de eigenschap **nodenaam** .</span><span class="sxs-lookup"><span data-stu-id="f4ae4-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="f4ae4-107">**WaitForSome** -resource maakt gebruik van Windows Remote Management om de status van andere knoop punten te controleren.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="f4ae4-108">Zie [beveiligings overwegingen voor externe communicatie van Power shell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)voor meer informatie over de vereisten voor de poort en de beveiliging van WinRM.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="f4ae4-109">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f4ae4-109">Syntax</span></span>

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="f4ae4-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="f4ae4-110">Properties</span></span>

|<span data-ttu-id="f4ae4-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="f4ae4-111">Property</span></span> |<span data-ttu-id="f4ae4-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f4ae4-112">Description</span></span> |
|---|---|
|<span data-ttu-id="f4ae4-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="f4ae4-113">NodeCount</span></span> |<span data-ttu-id="f4ae4-114">Het minimum aantal knoop punten dat in de gewenste status voor deze resource moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span> |
|<span data-ttu-id="f4ae4-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="f4ae4-115">NodeName</span></span> |<span data-ttu-id="f4ae4-116">De doel knooppunten van de resource waarvan afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-116">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="f4ae4-117">ResourceName</span><span class="sxs-lookup"><span data-stu-id="f4ae4-117">ResourceName</span></span> |<span data-ttu-id="f4ae4-118">De resource naam waarvan afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-118">The resource name to depend on.</span></span> <span data-ttu-id="f4ae4-119">Als deze resource deel uitmaakt van een andere configuratie, moet u de naam indelen als `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-119">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="f4ae4-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="f4ae4-120">RetryIntervalSec</span></span> |<span data-ttu-id="f4ae4-121">Het aantal seconden voordat een nieuwe poging wordt gedaan.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-121">The number of seconds before retrying.</span></span> <span data-ttu-id="f4ae4-122">De minimum waarde is 1.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-122">Minimum is 1.</span></span> |
|<span data-ttu-id="f4ae4-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="f4ae4-123">RetryCount</span></span> |<span data-ttu-id="f4ae4-124">Het maximum aantal keren dat opnieuw moet worden geprobeerd.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-124">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="f4ae4-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="f4ae4-125">ThrottleLimit</span></span> |<span data-ttu-id="f4ae4-126">Aantal machines om tegelijkertijd verbinding te maken.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="f4ae4-127">De standaard instelling is `New-CimSession` standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-127">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f4ae4-128">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="f4ae4-128">Common properties</span></span>

|<span data-ttu-id="f4ae4-129">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="f4ae4-129">Property</span></span> |<span data-ttu-id="f4ae4-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f4ae4-130">Description</span></span> |
|---|---|
|<span data-ttu-id="f4ae4-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f4ae4-131">DependsOn</span></span> |<span data-ttu-id="f4ae4-132">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f4ae4-133">Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-133">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f4ae4-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f4ae4-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="f4ae4-135">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="f4ae4-136">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f4ae4-137">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="f4ae4-138">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f4ae4-138">Example</span></span>

<span data-ttu-id="f4ae4-139">Zie [afhankelijkheden van meerdere knoop punten opgeven](../../../configurations/crossNodeDependencies.md) voor een voor beeld van het gebruik van deze bron.</span><span class="sxs-lookup"><span data-stu-id="f4ae4-139">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>