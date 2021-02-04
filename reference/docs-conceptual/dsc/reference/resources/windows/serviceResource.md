---
ms.date: 01/06/2021
ms.topic: reference
title: DSC-Service Resource
description: DSC-Service Resource
ms.openlocfilehash: bb151e11475c6e67f1fcb2d73336ff2e34b749b8
ms.sourcegitcommit: afefb3636362857036648c2fe80215bc4e81f5ac
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/07/2021
ms.locfileid: "97957033"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="dfafb-103">DSC-Service Resource</span><span class="sxs-lookup"><span data-stu-id="dfafb-103">DSC Service Resource</span></span>

> <span data-ttu-id="dfafb-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="dfafb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="dfafb-105">De **service** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van services op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="dfafb-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="dfafb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="dfafb-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="dfafb-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="dfafb-107">Properties</span></span>

|<span data-ttu-id="dfafb-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="dfafb-108">Property</span></span> |<span data-ttu-id="dfafb-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dfafb-109">Description</span></span> |
|---|---|
|<span data-ttu-id="dfafb-110">Name</span><span class="sxs-lookup"><span data-stu-id="dfafb-110">Name</span></span> |<span data-ttu-id="dfafb-111">Hiermee wordt de service naam aangegeven.</span><span class="sxs-lookup"><span data-stu-id="dfafb-111">Indicates the service name.</span></span> <span data-ttu-id="dfafb-112">Houd er rekening mee dat dit verschilt van de weergave naam.</span><span class="sxs-lookup"><span data-stu-id="dfafb-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="dfafb-113">U kunt een lijst met de services en de huidige status van de `Get-Service` cmdlet ophalen.</span><span class="sxs-lookup"><span data-stu-id="dfafb-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="dfafb-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="dfafb-114">BuiltInAccount</span></span> |<span data-ttu-id="dfafb-115">Hiermee wordt het aanmeldings account aangegeven dat moet worden gebruikt voor de service.</span><span class="sxs-lookup"><span data-stu-id="dfafb-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="dfafb-116">De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem** en **Network Service**.</span><span class="sxs-lookup"><span data-stu-id="dfafb-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="dfafb-117">Referentie</span><span class="sxs-lookup"><span data-stu-id="dfafb-117">Credential</span></span> |<span data-ttu-id="dfafb-118">Hiermee geeft u de referenties op voor het account waaronder de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="dfafb-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="dfafb-119">Deze eigenschap en de eigenschap **BuiltinAccount** kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dfafb-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="dfafb-120">Opstart type</span><span class="sxs-lookup"><span data-stu-id="dfafb-120">StartupType</span></span> |<span data-ttu-id="dfafb-121">Hiermee geeft u het opstart type voor de service.</span><span class="sxs-lookup"><span data-stu-id="dfafb-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="dfafb-122">De waarden die zijn toegestaan voor deze eigenschap zijn: **automatisch**, **uitgeschakeld** en **hand matig**.</span><span class="sxs-lookup"><span data-stu-id="dfafb-122">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="dfafb-123">Staat</span><span class="sxs-lookup"><span data-stu-id="dfafb-123">State</span></span> |<span data-ttu-id="dfafb-124">Hiermee wordt de status aangegeven die u voor de service wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="dfafb-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="dfafb-125">De waarden zijn: **actief** of **gestopt**.</span><span class="sxs-lookup"><span data-stu-id="dfafb-125">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="dfafb-126">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="dfafb-126">Dependencies</span></span> | <span data-ttu-id="dfafb-127">Een matrix met de namen van de afhankelijkheden die de service moet hebben.</span><span class="sxs-lookup"><span data-stu-id="dfafb-127">An array of the names of the dependencies the service should have.</span></span> |
|<span data-ttu-id="dfafb-128">Description</span><span class="sxs-lookup"><span data-stu-id="dfafb-128">Description</span></span> |<span data-ttu-id="dfafb-129">Hiermee wordt de beschrijving van de doel service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="dfafb-129">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="dfafb-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="dfafb-130">DisplayName</span></span> |<span data-ttu-id="dfafb-131">Hiermee wordt de weergave naam van de doel service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="dfafb-131">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="dfafb-132">Pad</span><span class="sxs-lookup"><span data-stu-id="dfafb-132">Path</span></span> |<span data-ttu-id="dfafb-133">Hiermee wordt het pad naar het binaire bestand voor een nieuwe service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="dfafb-133">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="dfafb-134">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="dfafb-134">Common properties</span></span>

|<span data-ttu-id="dfafb-135">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="dfafb-135">Property</span></span> |<span data-ttu-id="dfafb-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dfafb-136">Description</span></span> |
|---|---|
|<span data-ttu-id="dfafb-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dfafb-137">DependsOn</span></span> |<span data-ttu-id="dfafb-138">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="dfafb-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dfafb-139">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="dfafb-139">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="dfafb-140">Zo</span><span class="sxs-lookup"><span data-stu-id="dfafb-140">Ensure</span></span> |<span data-ttu-id="dfafb-141">Hiermee geeft u op of de doel service op het systeem bestaat.</span><span class="sxs-lookup"><span data-stu-id="dfafb-141">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="dfafb-142">Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de doel service niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="dfafb-142">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="dfafb-143">**Als u** deze instelling inschakelt, zorgt u ervoor dat de doel service bestaat.</span><span class="sxs-lookup"><span data-stu-id="dfafb-143">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="dfafb-144">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="dfafb-144">The default value is **Present**.</span></span> |
|<span data-ttu-id="dfafb-145">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="dfafb-145">PsDscRunAsCredential</span></span> |<span data-ttu-id="dfafb-146">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="dfafb-146">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="dfafb-147">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="dfafb-147">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="dfafb-148">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dfafb-148">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="dfafb-149">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="dfafb-149">Example</span></span>

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
