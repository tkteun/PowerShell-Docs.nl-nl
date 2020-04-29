---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxService-resource
ms.openlocfilehash: 6bb58796c4deff1153f932f61c328d84f8c4d2ca
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942564"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="6fd95-103">DSC voor Linux nxService-resource</span><span class="sxs-lookup"><span data-stu-id="6fd95-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="6fd95-104">De **nxService** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van services op een Linux-knoop punt.</span><span class="sxs-lookup"><span data-stu-id="6fd95-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6fd95-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6fd95-105">Syntax</span></span>

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="6fd95-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="6fd95-106">Properties</span></span>

|<span data-ttu-id="6fd95-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="6fd95-107">Property</span></span> |<span data-ttu-id="6fd95-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6fd95-108">Description</span></span> |
|---|---|
|<span data-ttu-id="6fd95-109">Naam</span><span class="sxs-lookup"><span data-stu-id="6fd95-109">Name</span></span> |<span data-ttu-id="6fd95-110">De naam van de service/daemon die moet worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="6fd95-110">The name of the service/daemon to configure.</span></span> |
|<span data-ttu-id="6fd95-111">Regelaar</span><span class="sxs-lookup"><span data-stu-id="6fd95-111">Controller</span></span> |<span data-ttu-id="6fd95-112">Het type service controller dat moet worden gebruikt bij het configureren van de service.</span><span class="sxs-lookup"><span data-stu-id="6fd95-112">The type of service controller to use when configuring the service.</span></span> |
|<span data-ttu-id="6fd95-113">Ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="6fd95-113">Enabled</span></span> |<span data-ttu-id="6fd95-114">Hiermee wordt aangegeven of de service wordt gestart bij het opstarten.</span><span class="sxs-lookup"><span data-stu-id="6fd95-114">Indicates whether the service starts on boot.</span></span> |
|<span data-ttu-id="6fd95-115">Status</span><span class="sxs-lookup"><span data-stu-id="6fd95-115">State</span></span> |<span data-ttu-id="6fd95-116">Hiermee wordt aangegeven of de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6fd95-116">Indicates whether the service is running.</span></span> <span data-ttu-id="6fd95-117">Stel deze eigenschap in op **gestopt** om er zeker van te zijn dat de service niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6fd95-117">Set this property to **Stopped** to ensure that the service is not running.</span></span> <span data-ttu-id="6fd95-118">Stel deze in op **wordt uitgevoerd** om ervoor te zorgen dat de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6fd95-118">Set it to **Running** to ensure that the service is running.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="6fd95-119">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="6fd95-119">Common properties</span></span>

|<span data-ttu-id="6fd95-120">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="6fd95-120">Property</span></span> |<span data-ttu-id="6fd95-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6fd95-121">Description</span></span> |
|---|---|
|<span data-ttu-id="6fd95-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6fd95-122">DependsOn</span></span> |<span data-ttu-id="6fd95-123">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="6fd95-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6fd95-124">De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is.</span><span class="sxs-lookup"><span data-stu-id="6fd95-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="6fd95-125">Aanvullende informatie</span><span class="sxs-lookup"><span data-stu-id="6fd95-125">Additional Information</span></span>

<span data-ttu-id="6fd95-126">Met de **nxService** -resource wordt geen service definitie of script voor de service gemaakt als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="6fd95-126">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="6fd95-127">U kunt de Power shell desired state Configuration **nxFile** resource Resource gebruiken om het bestaan of de inhoud van het service definitie bestand of-script te beheren.</span><span class="sxs-lookup"><span data-stu-id="6fd95-127">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="6fd95-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6fd95-128">Example</span></span>

<span data-ttu-id="6fd95-129">In het volgende voor beeld ziet u de configuratie van de ' httpd-service (voor Apache HTTP-server) die is geregistreerd bij de **Gesystemde** service controller.</span><span class="sxs-lookup"><span data-stu-id="6fd95-129">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```