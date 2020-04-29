---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-Service Resource
ms.openlocfilehash: 0bef6aa6d3526c9d8d92187c1e738d5c46b5665a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941311"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="be740-103">DSC-Service Resource</span><span class="sxs-lookup"><span data-stu-id="be740-103">DSC Service Resource</span></span>

> <span data-ttu-id="be740-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="be740-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="be740-105">De **service** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van services op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="be740-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="be740-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="be740-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="be740-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="be740-107">Properties</span></span>

|<span data-ttu-id="be740-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="be740-108">Property</span></span> |<span data-ttu-id="be740-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="be740-109">Description</span></span> |
|---|---|
|<span data-ttu-id="be740-110">Naam</span><span class="sxs-lookup"><span data-stu-id="be740-110">Name</span></span> |<span data-ttu-id="be740-111">Hiermee wordt de service naam aangegeven.</span><span class="sxs-lookup"><span data-stu-id="be740-111">Indicates the service name.</span></span> <span data-ttu-id="be740-112">Houd er rekening mee dat dit verschilt van de weergave naam.</span><span class="sxs-lookup"><span data-stu-id="be740-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="be740-113">U kunt een lijst met de services en de huidige status van de `Get-Service` cmdlet ophalen.</span><span class="sxs-lookup"><span data-stu-id="be740-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="be740-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="be740-114">BuiltInAccount</span></span> |<span data-ttu-id="be740-115">Hiermee wordt het aanmeldings account aangegeven dat moet worden gebruikt voor de service.</span><span class="sxs-lookup"><span data-stu-id="be740-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="be740-116">De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**en **Network Service**.</span><span class="sxs-lookup"><span data-stu-id="be740-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="be740-117">Referentie</span><span class="sxs-lookup"><span data-stu-id="be740-117">Credential</span></span> |<span data-ttu-id="be740-118">Hiermee geeft u de referenties op voor het account waaronder de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be740-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="be740-119">Deze eigenschap en de eigenschap **BuiltinAccount** kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="be740-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="be740-120">Opstart type</span><span class="sxs-lookup"><span data-stu-id="be740-120">StartupType</span></span> |<span data-ttu-id="be740-121">Hiermee geeft u het opstart type voor de service.</span><span class="sxs-lookup"><span data-stu-id="be740-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="be740-122">De waarden die zijn toegestaan voor deze eigenschap zijn: **automatisch**, **uitgeschakeld**en **hand matig**.</span><span class="sxs-lookup"><span data-stu-id="be740-122">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="be740-123">Status</span><span class="sxs-lookup"><span data-stu-id="be740-123">State</span></span> |<span data-ttu-id="be740-124">Hiermee wordt de status aangegeven die u voor de service wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="be740-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="be740-125">De waarden zijn: **actief** of **gestopt**.</span><span class="sxs-lookup"><span data-stu-id="be740-125">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="be740-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="be740-126">Description</span></span> |<span data-ttu-id="be740-127">Hiermee wordt de beschrijving van de doel service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="be740-127">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="be740-128">DisplayName</span><span class="sxs-lookup"><span data-stu-id="be740-128">DisplayName</span></span> |<span data-ttu-id="be740-129">Hiermee wordt de weergave naam van de doel service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="be740-129">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="be740-130">Pad</span><span class="sxs-lookup"><span data-stu-id="be740-130">Path</span></span> |<span data-ttu-id="be740-131">Hiermee wordt het pad naar het binaire bestand voor een nieuwe service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="be740-131">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="be740-132">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="be740-132">Common properties</span></span>

|<span data-ttu-id="be740-133">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="be740-133">Property</span></span> |<span data-ttu-id="be740-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="be740-134">Description</span></span> |
|---|---|
|<span data-ttu-id="be740-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="be740-135">DependsOn</span></span> |<span data-ttu-id="be740-136">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="be740-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="be740-137">De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is.</span><span class="sxs-lookup"><span data-stu-id="be740-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="be740-138">Zo</span><span class="sxs-lookup"><span data-stu-id="be740-138">Ensure</span></span> |<span data-ttu-id="be740-139">Hiermee geeft u op of de doel service op het systeem bestaat.</span><span class="sxs-lookup"><span data-stu-id="be740-139">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="be740-140">Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de doel service niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="be740-140">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="be740-141">**Als u** deze instelling inschakelt, zorgt u ervoor dat de doel service bestaat.</span><span class="sxs-lookup"><span data-stu-id="be740-141">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="be740-142">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="be740-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="be740-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="be740-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="be740-144">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="be740-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="be740-145">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="be740-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="be740-146">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be740-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="be740-147">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="be740-147">Example</span></span>

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