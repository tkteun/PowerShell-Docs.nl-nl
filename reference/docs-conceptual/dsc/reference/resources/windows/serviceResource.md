---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-Service Resource
ms.openlocfilehash: acd0710fb4b131876e3edece15b07cff8e9a8a9e
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557002"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="1630d-103">DSC-Service Resource</span><span class="sxs-lookup"><span data-stu-id="1630d-103">DSC Service Resource</span></span>

> <span data-ttu-id="1630d-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="1630d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="1630d-105">De **service** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van services op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="1630d-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1630d-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1630d-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="1630d-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="1630d-107">Properties</span></span>

|<span data-ttu-id="1630d-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="1630d-108">Property</span></span> |<span data-ttu-id="1630d-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1630d-109">Description</span></span> |
|---|---|
|<span data-ttu-id="1630d-110">Name</span><span class="sxs-lookup"><span data-stu-id="1630d-110">Name</span></span> |<span data-ttu-id="1630d-111">Hiermee wordt de service naam aangegeven.</span><span class="sxs-lookup"><span data-stu-id="1630d-111">Indicates the service name.</span></span> <span data-ttu-id="1630d-112">Houd er rekening mee dat dit verschilt van de weergave naam.</span><span class="sxs-lookup"><span data-stu-id="1630d-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="1630d-113">U kunt een lijst met de services en de huidige status van de `Get-Service` cmdlet ophalen.</span><span class="sxs-lookup"><span data-stu-id="1630d-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="1630d-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="1630d-114">BuiltInAccount</span></span> |<span data-ttu-id="1630d-115">Hiermee wordt het aanmeldings account aangegeven dat moet worden gebruikt voor de service.</span><span class="sxs-lookup"><span data-stu-id="1630d-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="1630d-116">De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**en **Network Service**.</span><span class="sxs-lookup"><span data-stu-id="1630d-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="1630d-117">Referentie</span><span class="sxs-lookup"><span data-stu-id="1630d-117">Credential</span></span> |<span data-ttu-id="1630d-118">Hiermee geeft u de referenties op voor het account waaronder de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1630d-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="1630d-119">Deze eigenschap en de eigenschap **BuiltinAccount** kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1630d-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="1630d-120">Opstart type</span><span class="sxs-lookup"><span data-stu-id="1630d-120">StartupType</span></span> |<span data-ttu-id="1630d-121">Hiermee geeft u het opstart type voor de service.</span><span class="sxs-lookup"><span data-stu-id="1630d-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="1630d-122">De waarden die zijn toegestaan voor deze eigenschap zijn: **automatisch**, **uitgeschakeld**en **hand matig**.</span><span class="sxs-lookup"><span data-stu-id="1630d-122">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="1630d-123">Staat</span><span class="sxs-lookup"><span data-stu-id="1630d-123">State</span></span> |<span data-ttu-id="1630d-124">Hiermee wordt de status aangegeven die u voor de service wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="1630d-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="1630d-125">De waarden zijn: **actief** of **gestopt**.</span><span class="sxs-lookup"><span data-stu-id="1630d-125">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="1630d-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1630d-126">Description</span></span> |<span data-ttu-id="1630d-127">Hiermee wordt de beschrijving van de doel service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="1630d-127">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="1630d-128">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1630d-128">DisplayName</span></span> |<span data-ttu-id="1630d-129">Hiermee wordt de weergave naam van de doel service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="1630d-129">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="1630d-130">Pad</span><span class="sxs-lookup"><span data-stu-id="1630d-130">Path</span></span> |<span data-ttu-id="1630d-131">Hiermee wordt het pad naar het binaire bestand voor een nieuwe service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="1630d-131">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1630d-132">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="1630d-132">Common properties</span></span>

|<span data-ttu-id="1630d-133">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="1630d-133">Property</span></span> |<span data-ttu-id="1630d-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1630d-134">Description</span></span> |
|---|---|
|<span data-ttu-id="1630d-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1630d-135">DependsOn</span></span> |<span data-ttu-id="1630d-136">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="1630d-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1630d-137">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="1630d-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1630d-138">Zo</span><span class="sxs-lookup"><span data-stu-id="1630d-138">Ensure</span></span> |<span data-ttu-id="1630d-139">Hiermee geeft u op of de doel service op het systeem bestaat.</span><span class="sxs-lookup"><span data-stu-id="1630d-139">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="1630d-140">Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de doel service niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="1630d-140">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="1630d-141">**Als u** deze instelling inschakelt, zorgt u ervoor dat de doel service bestaat.</span><span class="sxs-lookup"><span data-stu-id="1630d-141">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="1630d-142">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="1630d-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="1630d-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1630d-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="1630d-144">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="1630d-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="1630d-145">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="1630d-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="1630d-146">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1630d-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="1630d-147">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="1630d-147">Example</span></span>

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
