---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WaitForSome Resource
ms.openlocfilehash: 906375a8fcf9b87d4b7487e63e6fae3f05b86d0d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048179"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="17053-103">DSC WaitForSome Resource</span><span class="sxs-lookup"><span data-stu-id="17053-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="17053-104">Van toepassing op: Windows PowerShell 5.0 en hoger</span><span class="sxs-lookup"><span data-stu-id="17053-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="17053-105">De **WaitForAny** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](../../../configurations/configurations.md) afhankelijkheden opgeven voor configuraties op andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="17053-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="17053-106">Deze resource is geslaagd als de resource die is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status op een minimum aantal knooppunten (opgegeven door **NodeCount**) gedefinieerd door de **knooppuntnaam**  eigenschap.</span><span class="sxs-lookup"><span data-stu-id="17053-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="17053-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="17053-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="17053-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="17053-108">Properties</span></span>

|  <span data-ttu-id="17053-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="17053-109">Property</span></span>  |  <span data-ttu-id="17053-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="17053-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="17053-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="17053-111">NodeCount</span></span>| <span data-ttu-id="17053-112">Het minimum aantal knooppunten dat in de gewenste status voor deze resource worden moet te voltooien.</span><span class="sxs-lookup"><span data-stu-id="17053-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="17053-113">Knooppuntnaam</span><span class="sxs-lookup"><span data-stu-id="17053-113">NodeName</span></span>| <span data-ttu-id="17053-114">De doelknooppunten van de resource afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="17053-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="17053-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="17053-115">ResourceName</span></span>| <span data-ttu-id="17053-116">De naam van de resource afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="17053-116">The resource name to depend on.</span></span> <span data-ttu-id="17053-117">Als deze resource tot een andere configuratie behoort, maakt u de naam op als ' [__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="17053-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="17053-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="17053-118">RetryIntervalSec</span></span>| <span data-ttu-id="17053-119">Het aantal seconden alvorens het opnieuw te proberen.</span><span class="sxs-lookup"><span data-stu-id="17053-119">The number of seconds before retrying.</span></span> <span data-ttu-id="17053-120">Minimumwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="17053-120">Minimum is 1.</span></span>|
| <span data-ttu-id="17053-121">retryCount</span><span class="sxs-lookup"><span data-stu-id="17053-121">RetryCount</span></span>| <span data-ttu-id="17053-122">Het maximale aantal nieuwe pogingen.</span><span class="sxs-lookup"><span data-stu-id="17053-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="17053-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="17053-123">ThrottleLimit</span></span>| <span data-ttu-id="17053-124">Het aantal machines tegelijk verbinding kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="17053-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="17053-125">Standaard is de nieuwe-cimsession standaard.</span><span class="sxs-lookup"><span data-stu-id="17053-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="17053-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="17053-126">DependsOn</span></span> | <span data-ttu-id="17053-127">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="17053-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="17053-128">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="17053-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="17053-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="17053-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="17053-130">Zie [DSC gebruiken met de referenties van gebruiker](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="17053-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="17053-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="17053-131">Example</span></span>

<span data-ttu-id="17053-132">Zie voor een voorbeeld van het gebruik van deze resource [afhankelijkheden van meerdere knooppunten opgeven](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="17053-132">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
