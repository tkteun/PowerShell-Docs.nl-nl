---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-WaitForSome Resource
ms.openlocfilehash: cbe16c543f0eeb62dbe1fb439af2f9147f1bc210
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="ae2bb-103">DSC-WaitForSome Resource</span><span class="sxs-lookup"><span data-stu-id="ae2bb-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="ae2bb-104">Van toepassing op: Windows PowerShell 5.0 en hoger</span><span class="sxs-lookup"><span data-stu-id="ae2bb-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="ae2bb-105">De **WaitForAny** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](configurations.md) afhankelijkheden opgeven voor de configuraties op andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="ae2bb-106">Deze resource is geslaagd als de resource is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status van een minimum aantal knooppunten (opgegeven door **NodeCount**) gedefinieerd door de **NodeName**  eigenschap.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="ae2bb-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ae2bb-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="ae2bb-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="ae2bb-108">Properties</span></span>

|  <span data-ttu-id="ae2bb-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="ae2bb-109">Property</span></span>  |  <span data-ttu-id="ae2bb-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ae2bb-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="ae2bb-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="ae2bb-111">NodeCount</span></span>| <span data-ttu-id="ae2bb-112">Het minimale aantal knooppunten dat moet zich in de gewenste status voor deze bron zou lukken.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="ae2bb-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="ae2bb-113">NodeName</span></span>| <span data-ttu-id="ae2bb-114">De doelknooppunten van afhankelijk zijn van de bron.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="ae2bb-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="ae2bb-115">ResourceName</span></span>| <span data-ttu-id="ae2bb-116">De naam van de resource afhangen van.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-116">The resource name to depend on.</span></span>| 
| <span data-ttu-id="ae2bb-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="ae2bb-117">RetryIntervalSec</span></span>| <span data-ttu-id="ae2bb-118">Het aantal seconden alvorens het opnieuw proberen.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-118">The number of seconds before retrying.</span></span> <span data-ttu-id="ae2bb-119">Minimumwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="ae2bb-120">RetryCount</span><span class="sxs-lookup"><span data-stu-id="ae2bb-120">RetryCount</span></span>| <span data-ttu-id="ae2bb-121">Het maximale aantal keren opnieuw proberen.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="ae2bb-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="ae2bb-122">ThrottleLimit</span></span>| <span data-ttu-id="ae2bb-123">Het aantal machines tegelijk verbinding maken.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="ae2bb-124">Standaard is de nieuwe-cimsession standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="ae2bb-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="ae2bb-125">DependsOn</span></span> | <span data-ttu-id="ae2bb-126">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ae2bb-127">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ae2bb-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="ae2bb-128">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ae2bb-128">PsDscRunAsCredential</span></span> | <span data-ttu-id="ae2bb-129">Zie [gebruik van DSC met gebruikersgegevens](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="ae2bb-129">See [Using DSC with User Credentials](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="ae2bb-130">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ae2bb-130">Example</span></span>

<span data-ttu-id="ae2bb-131">Zie voor een voorbeeld van het gebruik van deze resource [cross-knooppunt afhankelijkheden opgeven](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="ae2bb-131">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

