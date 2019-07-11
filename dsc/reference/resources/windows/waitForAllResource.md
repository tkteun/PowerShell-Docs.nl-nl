---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WaitForAll Resource
ms.openlocfilehash: c1125b7c5b68b9b520ed052800b6a2abf4e53b85
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726876"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="479e8-103">DSC WaitForAll Resource</span><span class="sxs-lookup"><span data-stu-id="479e8-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="479e8-104">Van toepassing op: Windows PowerShell 5.0 en hoger</span><span class="sxs-lookup"><span data-stu-id="479e8-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="479e8-105">De **WaitForAll** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](../../../configurations/configurations.md) afhankelijkheden opgeven voor configuraties op andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="479e8-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="479e8-106">Deze resource is geslaagd als de resource die is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status van alle doelknooppunten gedefinieerd in de **knooppuntnaam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="479e8-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="479e8-107">**WaitForAll** resource maakt gebruik van Windows Remote Management om te controleren of de status van andere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="479e8-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="479e8-108">Zie voor meer informatie over de poort en beveiligingsvereisten voor WinRM [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="479e8-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="479e8-109">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="479e8-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="479e8-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="479e8-110">Properties</span></span>

|  <span data-ttu-id="479e8-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="479e8-111">Property</span></span>  |  <span data-ttu-id="479e8-112">Description</span><span class="sxs-lookup"><span data-stu-id="479e8-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="479e8-113">ResourceName</span><span class="sxs-lookup"><span data-stu-id="479e8-113">ResourceName</span></span>| <span data-ttu-id="479e8-114">De naam van de resource afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="479e8-114">The resource name to depend on.</span></span> <span data-ttu-id="479e8-115">Als deze resource tot een andere configuratie behoort, maakt u de naam op als ' [__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="479e8-115">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="479e8-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="479e8-116">NodeName</span></span>| <span data-ttu-id="479e8-117">De doelknooppunten van de resource afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="479e8-117">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="479e8-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="479e8-118">RetryIntervalSec</span></span>| <span data-ttu-id="479e8-119">Het aantal seconden alvorens het opnieuw te proberen.</span><span class="sxs-lookup"><span data-stu-id="479e8-119">The number of seconds before retrying.</span></span> <span data-ttu-id="479e8-120">Minimumwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="479e8-120">Minimum is 1.</span></span>|
| <span data-ttu-id="479e8-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="479e8-121">RetryCount</span></span>| <span data-ttu-id="479e8-122">Het maximale aantal nieuwe pogingen.</span><span class="sxs-lookup"><span data-stu-id="479e8-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="479e8-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="479e8-123">ThrottleLimit</span></span>| <span data-ttu-id="479e8-124">Het aantal machines tegelijk verbinding kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="479e8-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="479e8-125">Standaard is de nieuwe-cimsession standaard.</span><span class="sxs-lookup"><span data-stu-id="479e8-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="479e8-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="479e8-126">DependsOn</span></span> | <span data-ttu-id="479e8-127">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="479e8-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="479e8-128">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="479e8-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="479e8-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="479e8-129">Example</span></span>

<span data-ttu-id="479e8-130">Zie voor een voorbeeld van het gebruik van deze resource [afhankelijkheden van meerdere knooppunten opgeven](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="479e8-130">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
