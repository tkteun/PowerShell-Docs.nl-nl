---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-Service Resource
ms.openlocfilehash: f936f58ffd00f84d8c6d5d41d93378eaa8db5879
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463581"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="10d97-103">DSC-Service Resource</span><span class="sxs-lookup"><span data-stu-id="10d97-103">DSC Service Resource</span></span>

> <span data-ttu-id="10d97-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="10d97-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="10d97-105">De **service** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van services op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="10d97-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="10d97-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="10d97-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupTimeout = [uint32]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Ignore | Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DesktopInteract = [boolean]]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
    [ TerminateTimeout = [uint32] ]
}
```

## <a name="properties"></a><span data-ttu-id="10d97-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="10d97-107">Properties</span></span>

|<span data-ttu-id="10d97-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="10d97-108">Property</span></span> |<span data-ttu-id="10d97-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="10d97-109">Description</span></span> |
|---|---|
|<span data-ttu-id="10d97-110">Naam</span><span class="sxs-lookup"><span data-stu-id="10d97-110">Name</span></span> |<span data-ttu-id="10d97-111">Hiermee wordt de service naam aangegeven.</span><span class="sxs-lookup"><span data-stu-id="10d97-111">Indicates the service name.</span></span> <span data-ttu-id="10d97-112">Houd er rekening mee dat dit verschilt van de weergave naam.</span><span class="sxs-lookup"><span data-stu-id="10d97-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="10d97-113">U kunt een lijst met de services en de huidige status van de `Get-Service` cmdlet ophalen.</span><span class="sxs-lookup"><span data-stu-id="10d97-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="10d97-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="10d97-114">BuiltInAccount</span></span> |<span data-ttu-id="10d97-115">Hiermee wordt het aanmeldings account aangegeven dat moet worden gebruikt voor de service.</span><span class="sxs-lookup"><span data-stu-id="10d97-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="10d97-116">De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**en **Network Service**.</span><span class="sxs-lookup"><span data-stu-id="10d97-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="10d97-117">Referentie</span><span class="sxs-lookup"><span data-stu-id="10d97-117">Credential</span></span> |<span data-ttu-id="10d97-118">Hiermee geeft u de referenties op voor het account waaronder de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="10d97-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="10d97-119">Deze eigenschap en de eigenschap **BuiltinAccount** kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="10d97-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="10d97-120">StartupTimeout</span><span class="sxs-lookup"><span data-stu-id="10d97-120">StartupTimeout</span></span> | <span data-ttu-id="10d97-121">De tijd die moet worden gewacht voordat de service wordt uitgevoerd in milliseconden.</span><span class="sxs-lookup"><span data-stu-id="10d97-121">The time to wait for the service to be running in milliseconds.</span></span>|
|<span data-ttu-id="10d97-122">Opstart type</span><span class="sxs-lookup"><span data-stu-id="10d97-122">StartupType</span></span> |<span data-ttu-id="10d97-123">Hiermee geeft u het opstart type voor de service.</span><span class="sxs-lookup"><span data-stu-id="10d97-123">Indicates the startup type for the service.</span></span> <span data-ttu-id="10d97-124">De waarden die zijn toegestaan voor deze eigenschap zijn: **automatisch**, **uitgeschakeld**en **hand matig**.</span><span class="sxs-lookup"><span data-stu-id="10d97-124">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="10d97-125">Status</span><span class="sxs-lookup"><span data-stu-id="10d97-125">State</span></span> |<span data-ttu-id="10d97-126">Hiermee wordt de status aangegeven die u voor de service wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="10d97-126">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="10d97-127">De waarden zijn: **actief** of **gestopt**.</span><span class="sxs-lookup"><span data-stu-id="10d97-127">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="10d97-128">TerminateTimeout</span><span class="sxs-lookup"><span data-stu-id="10d97-128">TerminateTimeout</span></span> |<span data-ttu-id="10d97-129">De tijd die moet worden gewacht voordat de service wordt gestopt in milliseconden.</span><span class="sxs-lookup"><span data-stu-id="10d97-129">The time to wait for the service to be stopped in milliseconds.</span></span>|
|<span data-ttu-id="10d97-130">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="10d97-130">Dependencies</span></span> | <span data-ttu-id="10d97-131">Een matrix met de namen van de afhankelijkheden die de service moet hebben.</span><span class="sxs-lookup"><span data-stu-id="10d97-131">An array of the names of the dependencies the service should have.</span></span> |
|<span data-ttu-id="10d97-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="10d97-132">Description</span></span> |<span data-ttu-id="10d97-133">Hiermee wordt de beschrijving van de doel service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="10d97-133">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="10d97-134">DesktopInteract</span><span class="sxs-lookup"><span data-stu-id="10d97-134">DesktopInteract</span></span> | <span data-ttu-id="10d97-135">Hiermee wordt aangegeven of de service kan communiceren met een venster op het bureau blad.</span><span class="sxs-lookup"><span data-stu-id="10d97-135">Indicates whether or not the service should be able to communicate with a window on the desktop.</span></span> <span data-ttu-id="10d97-136">Moet onwaar zijn voor services die niet als LocalSystem worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="10d97-136">Must be false for services not running as LocalSystem.</span></span>|
|<span data-ttu-id="10d97-137">DisplayName</span><span class="sxs-lookup"><span data-stu-id="10d97-137">DisplayName</span></span> |<span data-ttu-id="10d97-138">Hiermee wordt de weergave naam van de doel service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="10d97-138">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="10d97-139">Pad</span><span class="sxs-lookup"><span data-stu-id="10d97-139">Path</span></span> |<span data-ttu-id="10d97-140">Hiermee wordt het pad naar het binaire bestand voor een nieuwe service aangegeven.</span><span class="sxs-lookup"><span data-stu-id="10d97-140">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="10d97-141">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="10d97-141">Common properties</span></span>

|<span data-ttu-id="10d97-142">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="10d97-142">Property</span></span> |<span data-ttu-id="10d97-143">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="10d97-143">Description</span></span> |
|---|---|
|<span data-ttu-id="10d97-144">DependsOn</span><span class="sxs-lookup"><span data-stu-id="10d97-144">DependsOn</span></span> |<span data-ttu-id="10d97-145">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="10d97-145">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="10d97-146">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="10d97-146">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="10d97-147">Zo</span><span class="sxs-lookup"><span data-stu-id="10d97-147">Ensure</span></span> |<span data-ttu-id="10d97-148">Hiermee geeft u op of de doel service op het systeem bestaat.</span><span class="sxs-lookup"><span data-stu-id="10d97-148">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="10d97-149">Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de doel service niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="10d97-149">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="10d97-150">**Als u** deze instelling inschakelt, zorgt u ervoor dat de doel service bestaat.</span><span class="sxs-lookup"><span data-stu-id="10d97-150">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="10d97-151">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="10d97-151">The default value is **Present**.</span></span> |
|<span data-ttu-id="10d97-152">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="10d97-152">PsDscRunAsCredential</span></span> |<span data-ttu-id="10d97-153">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="10d97-153">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="10d97-154">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="10d97-154">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="10d97-155">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="10d97-155">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="10d97-156">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="10d97-156">Example</span></span>

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
