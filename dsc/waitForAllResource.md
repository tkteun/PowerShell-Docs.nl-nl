---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC-WaitForAll Resource
ms.openlocfilehash: 4413220bb0b5eeef5fd1599f794cd551f15a2925
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221779"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="d2f68-103">DSC-WaitForAll Resource</span><span class="sxs-lookup"><span data-stu-id="d2f68-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="d2f68-104">Van toepassing op: Windows PowerShell 5.0 en hoger</span><span class="sxs-lookup"><span data-stu-id="d2f68-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="d2f68-105">De **WaitForAll** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](configurations.md) afhankelijkheden opgeven voor de configuraties op andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="d2f68-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="d2f68-106">Deze bron slaagt of als de resource is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status op alle doelknooppunten gedefinieerd in de **NodeName** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="d2f68-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="d2f68-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d2f68-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="d2f68-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="d2f68-108">Properties</span></span>

|  <span data-ttu-id="d2f68-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="d2f68-109">Property</span></span>  |  <span data-ttu-id="d2f68-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d2f68-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="d2f68-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="d2f68-111">ResourceName</span></span>| <span data-ttu-id="d2f68-112">De naam van de resource afhangen van.</span><span class="sxs-lookup"><span data-stu-id="d2f68-112">The resource name to depend on.</span></span> <span data-ttu-id="d2f68-113">Als deze resource bij een andere configuratie hoort, de naam op als indeling ' [__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="d2f68-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="d2f68-114">nodeName</span><span class="sxs-lookup"><span data-stu-id="d2f68-114">NodeName</span></span>| <span data-ttu-id="d2f68-115">De doelknooppunten van afhankelijk zijn van de bron.</span><span class="sxs-lookup"><span data-stu-id="d2f68-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="d2f68-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="d2f68-116">RetryIntervalSec</span></span>| <span data-ttu-id="d2f68-117">Het aantal seconden alvorens het opnieuw proberen.</span><span class="sxs-lookup"><span data-stu-id="d2f68-117">The number of seconds before retrying.</span></span> <span data-ttu-id="d2f68-118">Minimumwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="d2f68-118">Minimum is 1.</span></span>|
| <span data-ttu-id="d2f68-119">retryCount</span><span class="sxs-lookup"><span data-stu-id="d2f68-119">RetryCount</span></span>| <span data-ttu-id="d2f68-120">Het maximale aantal keren opnieuw proberen.</span><span class="sxs-lookup"><span data-stu-id="d2f68-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="d2f68-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="d2f68-121">ThrottleLimit</span></span>| <span data-ttu-id="d2f68-122">Het aantal machines tegelijk verbinding maken.</span><span class="sxs-lookup"><span data-stu-id="d2f68-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="d2f68-123">Standaard is de nieuwe-cimsession standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="d2f68-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="d2f68-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="d2f68-124">DependsOn</span></span> | <span data-ttu-id="d2f68-125">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="d2f68-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d2f68-126">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d2f68-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="d2f68-127">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d2f68-127">Example</span></span>

<span data-ttu-id="d2f68-128">Zie voor een voorbeeld van het gebruik van deze resource [cross-knooppunt afhankelijkheden opgeven](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="d2f68-128">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>