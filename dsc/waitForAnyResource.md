---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WaitForAny Resource
ms.openlocfilehash: 39100f0fc52092c54bbecab55e3ef3dfabb4c70e
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226046"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="c0a0f-103">DSC WaitForAny Resource</span><span class="sxs-lookup"><span data-stu-id="c0a0f-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="c0a0f-104">Van toepassing op: Windows PowerShell 5.1 of hoger</span><span class="sxs-lookup"><span data-stu-id="c0a0f-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="c0a0f-105">De **WaitForSome** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](configurations.md) afhankelijkheden opgeven voor configuraties op andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="c0a0f-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="c0a0f-106">Deze resource is geslaagd als de resource die is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status op een doelknooppunten dat is gedefinieerd in de **knooppuntnaam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="c0a0f-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="c0a0f-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c0a0f-107">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="c0a0f-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c0a0f-108">Properties</span></span>

|  <span data-ttu-id="c0a0f-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="c0a0f-109">Property</span></span>  |  <span data-ttu-id="c0a0f-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c0a0f-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="c0a0f-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="c0a0f-111">ResourceName</span></span>| <span data-ttu-id="c0a0f-112">De naam van de resource afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="c0a0f-112">The resource name to depend on.</span></span> <span data-ttu-id="c0a0f-113">Als deze resource tot een andere configuratie behoort, maakt u de naam op als ' [__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="c0a0f-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="c0a0f-114">Knooppuntnaam</span><span class="sxs-lookup"><span data-stu-id="c0a0f-114">NodeName</span></span>| <span data-ttu-id="c0a0f-115">De doelknooppunten van de resource afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="c0a0f-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="c0a0f-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="c0a0f-116">RetryIntervalSec</span></span>| <span data-ttu-id="c0a0f-117">Het aantal seconden alvorens het opnieuw te proberen.</span><span class="sxs-lookup"><span data-stu-id="c0a0f-117">The number of seconds before retrying.</span></span> <span data-ttu-id="c0a0f-118">Minimumwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="c0a0f-118">Minimum is 1.</span></span>|
| <span data-ttu-id="c0a0f-119">retryCount</span><span class="sxs-lookup"><span data-stu-id="c0a0f-119">RetryCount</span></span>| <span data-ttu-id="c0a0f-120">Het maximale aantal nieuwe pogingen.</span><span class="sxs-lookup"><span data-stu-id="c0a0f-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="c0a0f-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="c0a0f-121">ThrottleLimit</span></span>| <span data-ttu-id="c0a0f-122">Het aantal machines tegelijk verbinding kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="c0a0f-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="c0a0f-123">Standaard is de nieuwe-cimsession standaard.</span><span class="sxs-lookup"><span data-stu-id="c0a0f-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="c0a0f-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c0a0f-124">DependsOn</span></span> | <span data-ttu-id="c0a0f-125">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="c0a0f-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c0a0f-126">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c0a0f-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="c0a0f-127">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c0a0f-127">Example</span></span>

<span data-ttu-id="c0a0f-128">Zie voor een voorbeeld van het gebruik van deze resource [afhankelijkheden van meerdere knooppunten opgeven](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="c0a0f-128">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>