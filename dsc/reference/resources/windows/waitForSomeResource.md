---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WaitForSome Resource
ms.openlocfilehash: 888da1810f0a9233579bad5eef8d5dd556947c61
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059453"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="04a4d-103">DSC WaitForSome Resource</span><span class="sxs-lookup"><span data-stu-id="04a4d-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="04a4d-104">Van toepassing op: Windows PowerShell 5.0 en hoger</span><span class="sxs-lookup"><span data-stu-id="04a4d-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="04a4d-105">De **WaitForSome** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](../../../configurations/configurations.md) afhankelijkheden opgeven voor configuraties op andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="04a4d-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="04a4d-106">Deze resource is geslaagd als de resource die is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status op een minimum aantal knooppunten (opgegeven door **NodeCount**) gedefinieerd door de **knooppuntnaam**  eigenschap.</span><span class="sxs-lookup"><span data-stu-id="04a4d-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="04a4d-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="04a4d-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="04a4d-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="04a4d-108">Properties</span></span>

|  <span data-ttu-id="04a4d-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="04a4d-109">Property</span></span>  |  <span data-ttu-id="04a4d-110">Description</span><span class="sxs-lookup"><span data-stu-id="04a4d-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="04a4d-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="04a4d-111">NodeCount</span></span>| <span data-ttu-id="04a4d-112">Het minimum aantal knooppunten dat in de gewenste status voor deze resource worden moet te voltooien.</span><span class="sxs-lookup"><span data-stu-id="04a4d-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="04a4d-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="04a4d-113">NodeName</span></span>| <span data-ttu-id="04a4d-114">De doelknooppunten van de resource afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="04a4d-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="04a4d-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="04a4d-115">ResourceName</span></span>| <span data-ttu-id="04a4d-116">De naam van de resource afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="04a4d-116">The resource name to depend on.</span></span> <span data-ttu-id="04a4d-117">Als deze resource tot een andere configuratie behoort, maakt u de naam op als ' [__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="04a4d-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="04a4d-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="04a4d-118">RetryIntervalSec</span></span>| <span data-ttu-id="04a4d-119">Het aantal seconden alvorens het opnieuw te proberen.</span><span class="sxs-lookup"><span data-stu-id="04a4d-119">The number of seconds before retrying.</span></span> <span data-ttu-id="04a4d-120">Minimumwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="04a4d-120">Minimum is 1.</span></span>|
| <span data-ttu-id="04a4d-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="04a4d-121">RetryCount</span></span>| <span data-ttu-id="04a4d-122">Het maximale aantal nieuwe pogingen.</span><span class="sxs-lookup"><span data-stu-id="04a4d-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="04a4d-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="04a4d-123">ThrottleLimit</span></span>| <span data-ttu-id="04a4d-124">Het aantal machines tegelijk verbinding kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="04a4d-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="04a4d-125">Standaard is de nieuwe-cimsession standaard.</span><span class="sxs-lookup"><span data-stu-id="04a4d-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="04a4d-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="04a4d-126">DependsOn</span></span> | <span data-ttu-id="04a4d-127">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="04a4d-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="04a4d-128">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="04a4d-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="04a4d-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="04a4d-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="04a4d-130">Zie [DSC gebruiken met de referenties van gebruiker](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="04a4d-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="04a4d-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="04a4d-131">Example</span></span>

<span data-ttu-id="04a4d-132">Zie voor een voorbeeld van het gebruik van deze resource [afhankelijkheden van meerdere knooppunten opgeven](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="04a4d-132">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
