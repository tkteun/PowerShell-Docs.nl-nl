---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC ServiceSet-Resource
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076824"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="390e5-103">DSC ServiceSet-Resource</span><span class="sxs-lookup"><span data-stu-id="390e5-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="390e5-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="390e5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="390e5-105">De **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van services op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="390e5-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="390e5-106">Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die roept de [Service resource](serviceResource.md) voor elke service die is opgegeven in de `Name` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="390e5-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="390e5-107">Gebruik deze resource als u wilt configureren van een aantal services naar dezelfde toestand.</span><span class="sxs-lookup"><span data-stu-id="390e5-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="390e5-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="390e5-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="390e5-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="390e5-109">Properties</span></span>

|  <span data-ttu-id="390e5-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="390e5-110">Property</span></span>  |  <span data-ttu-id="390e5-111">Description</span><span class="sxs-lookup"><span data-stu-id="390e5-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="390e5-112">Naam</span><span class="sxs-lookup"><span data-stu-id="390e5-112">Name</span></span>| <span data-ttu-id="390e5-113">Geeft aan dat de servicenamen van de.</span><span class="sxs-lookup"><span data-stu-id="390e5-113">Indicates the service names.</span></span> <span data-ttu-id="390e5-114">Houd er rekening mee dat soms dit af van de weergavenamen wijkt.</span><span class="sxs-lookup"><span data-stu-id="390e5-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="390e5-115">U krijgt een overzicht van de services en de huidige status hiervan met de [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="390e5-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="390e5-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="390e5-116">StartupType</span></span>| <span data-ttu-id="390e5-117">Geeft aan dat het opstarttype voor de service.</span><span class="sxs-lookup"><span data-stu-id="390e5-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="390e5-118">De waarden die zijn toegestaan voor deze eigenschap zijn: **Automatische**, **uitgeschakelde**, en **handmatig**</span><span class="sxs-lookup"><span data-stu-id="390e5-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="390e5-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="390e5-119">BuiltInAccount</span></span>| <span data-ttu-id="390e5-120">Geeft aan dat de aanmeldingsaccount gebruiken voor de services.</span><span class="sxs-lookup"><span data-stu-id="390e5-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="390e5-121">De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**, en **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="390e5-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="390e5-122">Status</span><span class="sxs-lookup"><span data-stu-id="390e5-122">State</span></span>| <span data-ttu-id="390e5-123">Hiermee geeft u de status die u wilt om ervoor te zorgen voor de services: **Gestopt** of **met**.</span><span class="sxs-lookup"><span data-stu-id="390e5-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="390e5-124">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="390e5-124">Ensure</span></span>| <span data-ttu-id="390e5-125">Geeft aan of de services op het systeem zijn.</span><span class="sxs-lookup"><span data-stu-id="390e5-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="390e5-126">Deze eigenschap instellen op **afwezig** om ervoor te zorgen dat de services niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="390e5-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="390e5-127">Instellen op **aanwezig** (de standaardwaarde) zorgt ervoor dat de doelservices bestaan.</span><span class="sxs-lookup"><span data-stu-id="390e5-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="390e5-128">Referentie</span><span class="sxs-lookup"><span data-stu-id="390e5-128">Credential</span></span>| <span data-ttu-id="390e5-129">Geeft aan dat de referenties voor het account dat de bron van de service wordt uitgevoerd onder.</span><span class="sxs-lookup"><span data-stu-id="390e5-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="390e5-130">Deze eigenschap en de **BuiltinAccount** eigenschap samen kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="390e5-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="390e5-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="390e5-131">DependsOn</span></span>| <span data-ttu-id="390e5-132">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="390e5-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="390e5-133">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is *ResourceName* en het type *ResourceType*, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="390e5-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="390e5-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="390e5-134">Example</span></span>

<span data-ttu-id="390e5-135">De volgende configuratie start de services 'Windows Audio' en 'Extern bureaublad-Services'.</span><span class="sxs-lookup"><span data-stu-id="390e5-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

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
