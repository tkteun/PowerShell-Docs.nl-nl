---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-WaitForAny Resource
ms.openlocfilehash: ba1873cc0ecfc4596cbad5b61b4a52b61ea4778a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="8cd74-103">DSC-WaitForAny Resource</span><span class="sxs-lookup"><span data-stu-id="8cd74-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="8cd74-104">Van toepassing op: Windows PowerShell 5.1 en hoger</span><span class="sxs-lookup"><span data-stu-id="8cd74-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="8cd74-105">De **WaitForSome** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](configurations.md) afhankelijkheden opgeven voor de configuraties op andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="8cd74-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="8cd74-106">Deze bron slaagt of als de resource is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status op een doel-knooppunt dat is gedefinieerd in de **NodeName** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="8cd74-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="8cd74-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8cd74-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="8cd74-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="8cd74-108">Properties</span></span>

|  <span data-ttu-id="8cd74-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8cd74-109">Property</span></span>  |  <span data-ttu-id="8cd74-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8cd74-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="8cd74-111">resourceName</span><span class="sxs-lookup"><span data-stu-id="8cd74-111">ResourceName</span></span>| <span data-ttu-id="8cd74-112">De naam van de resource afhangen van.</span><span class="sxs-lookup"><span data-stu-id="8cd74-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="8cd74-113">nodeName</span><span class="sxs-lookup"><span data-stu-id="8cd74-113">NodeName</span></span>| <span data-ttu-id="8cd74-114">De doelknooppunten van afhankelijk zijn van de bron.</span><span class="sxs-lookup"><span data-stu-id="8cd74-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="8cd74-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="8cd74-115">RetryIntervalSec</span></span>| <span data-ttu-id="8cd74-116">Het aantal seconden alvorens het opnieuw proberen.</span><span class="sxs-lookup"><span data-stu-id="8cd74-116">The number of seconds before retrying.</span></span> <span data-ttu-id="8cd74-117">Minimumwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="8cd74-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="8cd74-118">retryCount</span><span class="sxs-lookup"><span data-stu-id="8cd74-118">RetryCount</span></span>| <span data-ttu-id="8cd74-119">Het maximale aantal keren opnieuw proberen.</span><span class="sxs-lookup"><span data-stu-id="8cd74-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="8cd74-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="8cd74-120">ThrottleLimit</span></span>| <span data-ttu-id="8cd74-121">Het aantal machines tegelijk verbinding maken.</span><span class="sxs-lookup"><span data-stu-id="8cd74-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="8cd74-122">Standaard is de nieuwe-cimsession standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="8cd74-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="8cd74-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="8cd74-123">DependsOn</span></span> | <span data-ttu-id="8cd74-124">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="8cd74-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8cd74-125">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8cd74-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="8cd74-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="8cd74-126">Example</span></span>

<span data-ttu-id="8cd74-127">Zie voor een voorbeeld van het gebruik van deze resource [cross-knooppunt afhankelijkheden opgeven](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="8cd74-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

