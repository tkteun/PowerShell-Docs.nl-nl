---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WaitForAll-resource
description: DSC WaitForAll-resource
ms.openlocfilehash: a477584cf97a56815bda9973cb2befc9b71d14d1
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143106"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="e129a-103">DSC WaitForAll-resource</span><span class="sxs-lookup"><span data-stu-id="e129a-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="e129a-104">Van toepassing op: Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="e129a-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="e129a-105">De resource van de desired state Configuration (DSC) **WaitForAll** kan worden gebruikt binnen een knooppunt blok in een [DSC-configuratie](../../../configurations/configurations.md) om afhankelijkheden op te geven voor de configuraties op andere knoop punten.</span><span class="sxs-lookup"><span data-stu-id="e129a-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

<span data-ttu-id="e129a-106">Deze resource slaagt als de resource die is opgegeven door de eigenschap **ResourceName** de gewenste status heeft voor alle doel knooppunten die zijn gedefinieerd in de eigenschap **nodenaam** .</span><span class="sxs-lookup"><span data-stu-id="e129a-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="e129a-107">**WaitForAll** -resource maakt gebruik van Windows Remote Management om de status van andere knoop punten te controleren.</span><span class="sxs-lookup"><span data-stu-id="e129a-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="e129a-108">Zie [beveiligings overwegingen voor externe communicatie van Power shell](/powershell/scripting/learn/remoting/winrmsecurity)voor meer informatie over de vereisten voor de poort en de beveiliging van WinRM.</span><span class="sxs-lookup"><span data-stu-id="e129a-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

## <a name="syntax"></a><span data-ttu-id="e129a-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="e129a-109">Syntax</span></span>

```Syntax
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="e129a-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="e129a-110">Properties</span></span>

|<span data-ttu-id="e129a-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="e129a-111">Property</span></span> |<span data-ttu-id="e129a-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e129a-112">Description</span></span> |
|---|---|
|<span data-ttu-id="e129a-113">ResourceName</span><span class="sxs-lookup"><span data-stu-id="e129a-113">ResourceName</span></span> |<span data-ttu-id="e129a-114">De resource naam waarvan afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="e129a-114">The resource name to depend on.</span></span> <span data-ttu-id="e129a-115">Als deze resource deel uitmaakt van een andere configuratie, moet u de naam indelen als `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]` .</span><span class="sxs-lookup"><span data-stu-id="e129a-115">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="e129a-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="e129a-116">NodeName</span></span> |<span data-ttu-id="e129a-117">De doel knooppunten van de resource waarvan afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="e129a-117">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="e129a-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="e129a-118">RetryIntervalSec</span></span> |<span data-ttu-id="e129a-119">Het aantal seconden voordat een nieuwe poging wordt gedaan.</span><span class="sxs-lookup"><span data-stu-id="e129a-119">The number of seconds before retrying.</span></span> <span data-ttu-id="e129a-120">De minimum waarde is 1.</span><span class="sxs-lookup"><span data-stu-id="e129a-120">Minimum is 1.</span></span> |
|<span data-ttu-id="e129a-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="e129a-121">RetryCount</span></span> |<span data-ttu-id="e129a-122">Het maximum aantal keren dat opnieuw moet worden geprobeerd.</span><span class="sxs-lookup"><span data-stu-id="e129a-122">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="e129a-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="e129a-123">ThrottleLimit</span></span> |<span data-ttu-id="e129a-124">Aantal machines om tegelijkertijd verbinding te maken.</span><span class="sxs-lookup"><span data-stu-id="e129a-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="e129a-125">Standaard instelling is `New-CimSession` standaard.</span><span class="sxs-lookup"><span data-stu-id="e129a-125">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="e129a-126">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="e129a-126">Common properties</span></span>

|<span data-ttu-id="e129a-127">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="e129a-127">Property</span></span> |<span data-ttu-id="e129a-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e129a-128">Description</span></span> |
|---|---|
|<span data-ttu-id="e129a-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e129a-129">DependsOn</span></span> |<span data-ttu-id="e129a-130">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="e129a-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e129a-131">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="e129a-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="e129a-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="e129a-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="e129a-133">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="e129a-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="e129a-134">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="e129a-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="e129a-135">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e129a-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="e129a-136">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e129a-136">Example</span></span>

<span data-ttu-id="e129a-137">Zie [afhankelijkheden van meerdere knoop punten opgeven](../../../configurations/crossNodeDependencies.md) voor een voor beeld van het gebruik van deze bron.</span><span class="sxs-lookup"><span data-stu-id="e129a-137">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
