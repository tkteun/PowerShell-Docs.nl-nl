---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC ServiceSet-Resource
ms.openlocfilehash: 1f879d2eafeb11e69968252a11f0c550c9b103f3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188962"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="c21b0-103">DSC ServiceSet-Resource</span><span class="sxs-lookup"><span data-stu-id="c21b0-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="c21b0-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c21b0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="c21b0-105">De **ServiceSet** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van services in het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="c21b0-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="c21b0-106">Deze bron is een [samengestelde bron](authoringResourceComposite.md) die roept de [Service resource](serviceResource.md) voor elke service die is opgegeven in de `Name` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="c21b0-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="c21b0-107">Gebruik deze bron als u wilt configureren, een aantal services naar dezelfde toestand.</span><span class="sxs-lookup"><span data-stu-id="c21b0-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="c21b0-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c21b0-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="c21b0-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c21b0-109">Properties</span></span>

|  <span data-ttu-id="c21b0-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="c21b0-110">Property</span></span>  |  <span data-ttu-id="c21b0-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c21b0-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="c21b0-112">Naam</span><span class="sxs-lookup"><span data-stu-id="c21b0-112">Name</span></span>| <span data-ttu-id="c21b0-113">Hiermee geeft u de servicenamen van de.</span><span class="sxs-lookup"><span data-stu-id="c21b0-113">Indicates the service names.</span></span> <span data-ttu-id="c21b0-114">Houd er rekening mee dat soms dit van de weergavenamen verschilt.</span><span class="sxs-lookup"><span data-stu-id="c21b0-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="c21b0-115">U krijgt een lijst van de services en de huidige staat met de [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c21b0-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="c21b0-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="c21b0-116">StartupType</span></span>| <span data-ttu-id="c21b0-117">Hiermee geeft het opstarttype voor de service.</span><span class="sxs-lookup"><span data-stu-id="c21b0-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="c21b0-118">De waarden die zijn toegestaan voor deze eigenschap zijn: **automatische**, **uitgeschakelde**, en **handmatig**</span><span class="sxs-lookup"><span data-stu-id="c21b0-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="c21b0-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="c21b0-119">BuiltInAccount</span></span>| <span data-ttu-id="c21b0-120">Hiermee geeft u het aanmeldingsaccount voor de services.</span><span class="sxs-lookup"><span data-stu-id="c21b0-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="c21b0-121">De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**, en **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="c21b0-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="c21b0-122">Status</span><span class="sxs-lookup"><span data-stu-id="c21b0-122">State</span></span>| <span data-ttu-id="c21b0-123">Geeft de status die u wilt zorgen voor de services: **gestopt** of **met**.</span><span class="sxs-lookup"><span data-stu-id="c21b0-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="c21b0-124">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="c21b0-124">Ensure</span></span>| <span data-ttu-id="c21b0-125">Geeft aan of de services op het systeem zijn.</span><span class="sxs-lookup"><span data-stu-id="c21b0-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="c21b0-126">Deze eigenschap instellen op **afwezig** om ervoor te zorgen dat de services niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="c21b0-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="c21b0-127">Instellen op **aanwezig** (de standaardwaarde) zorgt ervoor dat de doelservices bestaat.</span><span class="sxs-lookup"><span data-stu-id="c21b0-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="c21b0-128">referentie</span><span class="sxs-lookup"><span data-stu-id="c21b0-128">Credential</span></span>| <span data-ttu-id="c21b0-129">Hiermee geeft u referenties voor het account waaronder resource voor de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c21b0-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="c21b0-130">Deze eigenschap en de **BuiltinAccount** eigenschap kan niet samen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c21b0-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="c21b0-131">dependsOn</span><span class="sxs-lookup"><span data-stu-id="c21b0-131">DependsOn</span></span>| <span data-ttu-id="c21b0-132">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="c21b0-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c21b0-133">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is *ResourceName* en het type *ResourceType*, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c21b0-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="c21b0-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c21b0-134">Example</span></span>

<span data-ttu-id="c21b0-135">De volgende configuratie start de services 'Windows Audio' en 'Extern bureaublad-Services'.</span><span class="sxs-lookup"><span data-stu-id="c21b0-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

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