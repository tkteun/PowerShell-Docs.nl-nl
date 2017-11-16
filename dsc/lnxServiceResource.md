---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxService Resource
ms.openlocfilehash: be9f1f090eacc38bcdb77e53020d559bab72c156
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="8b944-103">DSC voor Linux nxService Resource</span><span class="sxs-lookup"><span data-stu-id="8b944-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="8b944-104">De **nxService** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van services op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="8b944-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8b944-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8b944-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="8b944-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="8b944-106">Properties</span></span>
|  <span data-ttu-id="8b944-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8b944-107">Property</span></span> |  <span data-ttu-id="8b944-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8b944-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="8b944-109">Naam</span><span class="sxs-lookup"><span data-stu-id="8b944-109">Name</span></span>| <span data-ttu-id="8b944-110">De naam van de service /-daemon te configureren.</span><span class="sxs-lookup"><span data-stu-id="8b944-110">The name of the service/daemon to configure.</span></span>| 
| <span data-ttu-id="8b944-111">Domeincontroller</span><span class="sxs-lookup"><span data-stu-id="8b944-111">Controller</span></span>| <span data-ttu-id="8b944-112">Het type servicecontroller moet worden gebruikt bij het configureren van de service.</span><span class="sxs-lookup"><span data-stu-id="8b944-112">The type of service controller to use when configuring the service.</span></span>| 
| <span data-ttu-id="8b944-113">Ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="8b944-113">Enabled</span></span>| <span data-ttu-id="8b944-114">Hiermee wordt aangegeven of de service wordt gestart bij het opstarten.</span><span class="sxs-lookup"><span data-stu-id="8b944-114">Indicates whether the service starts on boot.</span></span>| 
| <span data-ttu-id="8b944-115">Status</span><span class="sxs-lookup"><span data-stu-id="8b944-115">State</span></span>| <span data-ttu-id="8b944-116">Hiermee wordt aangegeven of de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8b944-116">Indicates whether the service is running.</span></span> <span data-ttu-id="8b944-117">Stel deze eigenschap op 'Gestopt' om ervoor te zorgen dat de service niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8b944-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="8b944-118">Stel deze in op 'Uitvoeren' om ervoor te zorgen dat de service niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8b944-118">Set it to "Running" to ensure that the service is not running.</span></span>| 
| <span data-ttu-id="8b944-119">dependsOn</span><span class="sxs-lookup"><span data-stu-id="8b944-119">DependsOn</span></span> | <span data-ttu-id="8b944-120">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="8b944-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8b944-121">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8b944-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 


## <a name="additional-information"></a><span data-ttu-id="8b944-122">Als u meer informatie</span><span class="sxs-lookup"><span data-stu-id="8b944-122">Additional Information</span></span>

<span data-ttu-id="8b944-123">De **nxService** resource niet maakt een servicedefinitie of het script voor de service als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="8b944-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="8b944-124">Kunt u PowerShell Desired State Configuration **nxFile** Resource resource voor het beheren van de aanwezigheid of de inhoud van het servicedefinitiebestand of script.</span><span class="sxs-lookup"><span data-stu-id="8b944-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="8b944-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="8b944-125">Example</span></span>

<span data-ttu-id="8b944-126">Het volgende voorbeeld ziet u configuratie van de service 'httpd' (voor Apache HTTP-Server), geregistreerd bij de **SystemD** service-controller.</span><span class="sxs-lookup"><span data-stu-id="8b944-126">The following example shows configuration of the “httpd” service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```

