---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC ServiceSet-Resource
ms.openlocfilehash: 92fa4a442eb42e89195162b7831f1a96d40b84f5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="2dc2a-103">DSC ServiceSet-Resource</span><span class="sxs-lookup"><span data-stu-id="2dc2a-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="2dc2a-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2dc2a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="2dc2a-105">De **ServiceSet** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van services in het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="2dc2a-106">Deze bron is een [samengestelde bron](authoringResourceComposite.md) die roept de [Service resource](serviceResource.md) voor elke service die is opgegeven in de `Name` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="2dc2a-107">Gebruik deze bron als u wilt configureren, een aantal services naar dezelfde toestand.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="2dc2a-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2dc2a-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="2dc2a-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="2dc2a-109">Properties</span></span>

|  <span data-ttu-id="2dc2a-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="2dc2a-110">Property</span></span>  |  <span data-ttu-id="2dc2a-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2dc2a-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="2dc2a-112">Naam</span><span class="sxs-lookup"><span data-stu-id="2dc2a-112">Name</span></span>| <span data-ttu-id="2dc2a-113">Hiermee geeft u de servicenamen van de.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-113">Indicates the service names.</span></span> <span data-ttu-id="2dc2a-114">Houd er rekening mee dat soms dit van de weergavenamen verschilt.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="2dc2a-115">U krijgt een lijst van de services en de huidige staat met de [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="2dc2a-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="2dc2a-116">StartupType</span></span>| <span data-ttu-id="2dc2a-117">Hiermee geeft het opstarttype voor de service.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="2dc2a-118">De waarden die zijn toegestaan voor deze eigenschap zijn: **automatische**, **uitgeschakelde**, en **handmatig**</span><span class="sxs-lookup"><span data-stu-id="2dc2a-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|  
| <span data-ttu-id="2dc2a-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="2dc2a-119">BuiltInAccount</span></span>| <span data-ttu-id="2dc2a-120">Hiermee geeft u het aanmeldingsaccount voor de services.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="2dc2a-121">De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**, en **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>| 
| <span data-ttu-id="2dc2a-122">Status</span><span class="sxs-lookup"><span data-stu-id="2dc2a-122">State</span></span>| <span data-ttu-id="2dc2a-123">Geeft de status die u wilt zorgen voor de services: **gestopt** of **met**.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>| 
| <span data-ttu-id="2dc2a-124">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="2dc2a-124">Ensure</span></span>| <span data-ttu-id="2dc2a-125">Geeft aan of de services op het systeem zijn.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="2dc2a-126">Deze eigenschap instellen op **afwezig** om ervoor te zorgen dat de services niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="2dc2a-127">Instellen op **aanwezig** (de standaardwaarde) zorgt ervoor dat de doelservices bestaat.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="2dc2a-128">referentie</span><span class="sxs-lookup"><span data-stu-id="2dc2a-128">Credential</span></span>| <span data-ttu-id="2dc2a-129">Hiermee geeft u referenties voor het account waaronder resource voor de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="2dc2a-130">Deze eigenschap en de **BuiltinAccount** eigenschap kan niet samen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>| 
| <span data-ttu-id="2dc2a-131">dependsOn</span><span class="sxs-lookup"><span data-stu-id="2dc2a-131">DependsOn</span></span>| <span data-ttu-id="2dc2a-132">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2dc2a-133">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is *ResourceName* en het type *ResourceType*, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 



## <a name="example"></a><span data-ttu-id="2dc2a-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2dc2a-134">Example</span></span>

<span data-ttu-id="2dc2a-135">De volgende configuratie start de services 'Windows Audio' en 'Extern bureaublad-Services'.</span><span class="sxs-lookup"><span data-stu-id="2dc2a-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

