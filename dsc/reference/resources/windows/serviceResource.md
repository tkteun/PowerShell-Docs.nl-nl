---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Bron van het DSC-Service
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688299"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="0abb1-103">Bron van het DSC-Service</span><span class="sxs-lookup"><span data-stu-id="0abb1-103">DSC Service Resource</span></span>

> <span data-ttu-id="0abb1-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0abb1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="0abb1-105">De **Service** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van services op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="0abb1-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0abb1-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0abb1-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="0abb1-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="0abb1-107">Properties</span></span>

|  <span data-ttu-id="0abb1-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="0abb1-108">Property</span></span>  |  <span data-ttu-id="0abb1-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0abb1-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="0abb1-110">Naam</span><span class="sxs-lookup"><span data-stu-id="0abb1-110">Name</span></span>| <span data-ttu-id="0abb1-111">Geeft de servicenaam.</span><span class="sxs-lookup"><span data-stu-id="0abb1-111">Indicates the service name.</span></span> <span data-ttu-id="0abb1-112">Houd er rekening mee dat soms dit af van de weergavenaam wijkt.</span><span class="sxs-lookup"><span data-stu-id="0abb1-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="0abb1-113">U krijgt een overzicht van de services en de huidige status hiervan met de cmdlet Get-Service.</span><span class="sxs-lookup"><span data-stu-id="0abb1-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="0abb1-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="0abb1-114">BuiltInAccount</span></span>| <span data-ttu-id="0abb1-115">Geeft aan dat de aanmeldingsaccount gebruiken voor de service.</span><span class="sxs-lookup"><span data-stu-id="0abb1-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="0abb1-116">De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**, en **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="0abb1-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="0abb1-117">Referentie</span><span class="sxs-lookup"><span data-stu-id="0abb1-117">Credential</span></span>| <span data-ttu-id="0abb1-118">Geeft aan dat referenties voor het account waaronder de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0abb1-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="0abb1-119">Deze eigenschap en de __BuiltinAccount__ eigenschap samen kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0abb1-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="0abb1-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0abb1-120">DependsOn</span></span>| <span data-ttu-id="0abb1-121">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="0abb1-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0abb1-122">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0abb1-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="0abb1-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="0abb1-123">StartupType</span></span>| <span data-ttu-id="0abb1-124">Geeft aan dat het opstarttype voor de service.</span><span class="sxs-lookup"><span data-stu-id="0abb1-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="0abb1-125">De waarden die zijn toegestaan voor deze eigenschap zijn: **Automatische**, **uitgeschakelde**, en **handmatig**</span><span class="sxs-lookup"><span data-stu-id="0abb1-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="0abb1-126">Status</span><span class="sxs-lookup"><span data-stu-id="0abb1-126">State</span></span>| <span data-ttu-id="0abb1-127">Geeft de status die u wilt om ervoor te zorgen voor de service.</span><span class="sxs-lookup"><span data-stu-id="0abb1-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="0abb1-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0abb1-128">Description</span></span> | <span data-ttu-id="0abb1-129">Geeft aan dat de beschrijving van de doelservice.</span><span class="sxs-lookup"><span data-stu-id="0abb1-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="0abb1-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0abb1-130">DisplayName</span></span> | <span data-ttu-id="0abb1-131">Geeft de naam van de doelservice.</span><span class="sxs-lookup"><span data-stu-id="0abb1-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="0abb1-132">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="0abb1-132">Ensure</span></span> | <span data-ttu-id="0abb1-133">Geeft aan of de doelservice op het systeem bestaat.</span><span class="sxs-lookup"><span data-stu-id="0abb1-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="0abb1-134">Deze eigenschap instellen op **afwezig** om ervoor te zorgen dat de doelservice niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="0abb1-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="0abb1-135">Instellen op **aanwezig** (de standaardwaarde) zorgt ervoor dat de doelservice bestaat.</span><span class="sxs-lookup"><span data-stu-id="0abb1-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="0abb1-136">Pad</span><span class="sxs-lookup"><span data-stu-id="0abb1-136">Path</span></span> | <span data-ttu-id="0abb1-137">Geeft het pad naar het binaire bestand voor een nieuwe service.</span><span class="sxs-lookup"><span data-stu-id="0abb1-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="0abb1-138">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0abb1-138">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```