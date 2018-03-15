---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-WaitForSome Resource
ms.openlocfilehash: 8b0ad0dbd31816cc673c7f77945927987e90e08b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="de9ef-103">DSC-WaitForSome Resource</span><span class="sxs-lookup"><span data-stu-id="de9ef-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="de9ef-104">Van toepassing op: Windows PowerShell 5.0 en hoger</span><span class="sxs-lookup"><span data-stu-id="de9ef-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="de9ef-105">De **WaitForAny** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](configurations.md) afhankelijkheden opgeven voor de configuraties op andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="de9ef-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="de9ef-106">Deze resource is geslaagd als de resource is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status van een minimum aantal knooppunten (opgegeven door **NodeCount**) gedefinieerd door de **NodeName**  eigenschap.</span><span class="sxs-lookup"><span data-stu-id="de9ef-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="de9ef-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="de9ef-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="de9ef-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="de9ef-108">Properties</span></span>

|  <span data-ttu-id="de9ef-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="de9ef-109">Property</span></span>  |  <span data-ttu-id="de9ef-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="de9ef-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="de9ef-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="de9ef-111">NodeCount</span></span>| <span data-ttu-id="de9ef-112">Het minimale aantal knooppunten dat moet zich in de gewenste status voor deze bron zou lukken.</span><span class="sxs-lookup"><span data-stu-id="de9ef-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="de9ef-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="de9ef-113">NodeName</span></span>| <span data-ttu-id="de9ef-114">De doelknooppunten van afhankelijk zijn van de bron.</span><span class="sxs-lookup"><span data-stu-id="de9ef-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="de9ef-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="de9ef-115">ResourceName</span></span>| <span data-ttu-id="de9ef-116">De naam van de resource afhangen van.</span><span class="sxs-lookup"><span data-stu-id="de9ef-116">The resource name to depend on.</span></span> <span data-ttu-id="de9ef-117">Als deze resource bij een andere configuratie hoort, de naam op als indeling ' [__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="de9ef-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>| 
| <span data-ttu-id="de9ef-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="de9ef-118">RetryIntervalSec</span></span>| <span data-ttu-id="de9ef-119">Het aantal seconden alvorens het opnieuw proberen.</span><span class="sxs-lookup"><span data-stu-id="de9ef-119">The number of seconds before retrying.</span></span> <span data-ttu-id="de9ef-120">Minimumwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="de9ef-120">Minimum is 1.</span></span>| 
| <span data-ttu-id="de9ef-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="de9ef-121">RetryCount</span></span>| <span data-ttu-id="de9ef-122">Het maximale aantal keren opnieuw proberen.</span><span class="sxs-lookup"><span data-stu-id="de9ef-122">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="de9ef-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="de9ef-123">ThrottleLimit</span></span>| <span data-ttu-id="de9ef-124">Het aantal machines tegelijk verbinding maken.</span><span class="sxs-lookup"><span data-stu-id="de9ef-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="de9ef-125">Standaard is de nieuwe-cimsession standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="de9ef-125">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="de9ef-126">dependsOn</span><span class="sxs-lookup"><span data-stu-id="de9ef-126">DependsOn</span></span> | <span data-ttu-id="de9ef-127">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="de9ef-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="de9ef-128">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="de9ef-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="de9ef-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="de9ef-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="de9ef-130">Zie [gebruik van DSC met gebruikersgegevens](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="de9ef-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="de9ef-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="de9ef-131">Example</span></span>

<span data-ttu-id="de9ef-132">Zie voor een voorbeeld van het gebruik van deze resource [cross-knooppunt afhankelijkheden opgeven](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="de9ef-132">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

