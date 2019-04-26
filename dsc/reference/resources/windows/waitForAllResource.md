---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WaitForAll Resource
ms.openlocfilehash: 1e891f1aecbdbe641973669f71f22664ad8ea16c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076919"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="76739-103">DSC WaitForAll Resource</span><span class="sxs-lookup"><span data-stu-id="76739-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="76739-104">Van toepassing op: Windows PowerShell 5.0 en hoger</span><span class="sxs-lookup"><span data-stu-id="76739-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="76739-105">De **WaitForAll** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](../../../configurations/configurations.md) afhankelijkheden opgeven voor configuraties op andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="76739-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="76739-106">Deze resource is geslaagd als de resource die is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status van alle doelknooppunten gedefinieerd in de **knooppuntnaam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="76739-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="76739-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="76739-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="76739-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="76739-108">Properties</span></span>

|  <span data-ttu-id="76739-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="76739-109">Property</span></span>  |  <span data-ttu-id="76739-110">Description</span><span class="sxs-lookup"><span data-stu-id="76739-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="76739-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="76739-111">ResourceName</span></span>| <span data-ttu-id="76739-112">De naam van de resource afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="76739-112">The resource name to depend on.</span></span> <span data-ttu-id="76739-113">Als deze resource tot een andere configuratie behoort, maakt u de naam op als ' [__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="76739-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="76739-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="76739-114">NodeName</span></span>| <span data-ttu-id="76739-115">De doelknooppunten van de resource afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="76739-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="76739-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="76739-116">RetryIntervalSec</span></span>| <span data-ttu-id="76739-117">Het aantal seconden alvorens het opnieuw te proberen.</span><span class="sxs-lookup"><span data-stu-id="76739-117">The number of seconds before retrying.</span></span> <span data-ttu-id="76739-118">Minimumwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="76739-118">Minimum is 1.</span></span>|
| <span data-ttu-id="76739-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="76739-119">RetryCount</span></span>| <span data-ttu-id="76739-120">Het maximale aantal nieuwe pogingen.</span><span class="sxs-lookup"><span data-stu-id="76739-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="76739-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="76739-121">ThrottleLimit</span></span>| <span data-ttu-id="76739-122">Het aantal machines tegelijk verbinding kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="76739-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="76739-123">Standaard is de nieuwe-cimsession standaard.</span><span class="sxs-lookup"><span data-stu-id="76739-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="76739-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="76739-124">DependsOn</span></span> | <span data-ttu-id="76739-125">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="76739-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="76739-126">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="76739-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="76739-127">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="76739-127">Example</span></span>

<span data-ttu-id="76739-128">Zie voor een voorbeeld van het gebruik van deze resource [afhankelijkheden van meerdere knooppunten opgeven](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="76739-128">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
