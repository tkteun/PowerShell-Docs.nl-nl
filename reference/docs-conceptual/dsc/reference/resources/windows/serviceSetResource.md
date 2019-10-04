---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC serviceset-resource
ms.openlocfilehash: 97c25f46940d69ed6c696e2692e29131e9a997b0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941297"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="10daf-103">DSC serviceset-resource</span><span class="sxs-lookup"><span data-stu-id="10daf-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="10daf-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="10daf-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="10daf-105">De **serviceset** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van services op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="10daf-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="10daf-106">Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die de [Service Resource](serviceResource.md) aanroept voor elke service die in de eigenschap **name** is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="10daf-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the **Name** property.</span></span>

<span data-ttu-id="10daf-107">Gebruik deze resource als u een aantal services wilt configureren met dezelfde status.</span><span class="sxs-lookup"><span data-stu-id="10daf-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="10daf-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="10daf-108">Syntax</span></span>

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="10daf-109">properties</span><span class="sxs-lookup"><span data-stu-id="10daf-109">Properties</span></span>

|<span data-ttu-id="10daf-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="10daf-110">Property</span></span> |<span data-ttu-id="10daf-111">Description</span><span class="sxs-lookup"><span data-stu-id="10daf-111">Description</span></span> |
|---|---|
|<span data-ttu-id="10daf-112">Name</span><span class="sxs-lookup"><span data-stu-id="10daf-112">Name</span></span> |<span data-ttu-id="10daf-113">Hiermee worden de service namen aangegeven.</span><span class="sxs-lookup"><span data-stu-id="10daf-113">Indicates the service names.</span></span> <span data-ttu-id="10daf-114">Houd er rekening mee dat dit verschilt van de weergave namen.</span><span class="sxs-lookup"><span data-stu-id="10daf-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="10daf-115">U kunt een lijst met de services en de huidige status van de `Get-Service` cmdlet ophalen.</span><span class="sxs-lookup"><span data-stu-id="10daf-115">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="10daf-116">Opstart type</span><span class="sxs-lookup"><span data-stu-id="10daf-116">StartupType</span></span> |<span data-ttu-id="10daf-117">Hiermee wordt het opstart type voor de Services aangegeven.</span><span class="sxs-lookup"><span data-stu-id="10daf-117">Indicates the startup type for the services.</span></span> <span data-ttu-id="10daf-118">De waarden die zijn toegestaan voor deze eigenschap zijn: **Automatisch**, **uitgeschakeld**en **hand matig**.</span><span class="sxs-lookup"><span data-stu-id="10daf-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="10daf-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="10daf-119">BuiltInAccount</span></span> |<span data-ttu-id="10daf-120">Hiermee wordt het aanmeldings account aangegeven dat moet worden gebruikt voor de services.</span><span class="sxs-lookup"><span data-stu-id="10daf-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="10daf-121">De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**en **Network Service**.</span><span class="sxs-lookup"><span data-stu-id="10daf-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="10daf-122">State</span><span class="sxs-lookup"><span data-stu-id="10daf-122">State</span></span> |<span data-ttu-id="10daf-123">Hiermee wordt de status aangegeven die u voor de services wilt waarborgen: **Gestopt** of **actief**.</span><span class="sxs-lookup"><span data-stu-id="10daf-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span> |
|<span data-ttu-id="10daf-124">Referentie</span><span class="sxs-lookup"><span data-stu-id="10daf-124">Credential</span></span> |<span data-ttu-id="10daf-125">Hiermee geeft u de referenties op voor het account dat wordt uitgevoerd door de service bron.</span><span class="sxs-lookup"><span data-stu-id="10daf-125">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="10daf-126">Deze eigenschap en de eigenschap **BuiltinAccount** kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="10daf-126">This property and the **BuiltinAccount** property cannot be used together.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="10daf-127">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="10daf-127">Common properties</span></span>

|<span data-ttu-id="10daf-128">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="10daf-128">Property</span></span> |<span data-ttu-id="10daf-129">Description</span><span class="sxs-lookup"><span data-stu-id="10daf-129">Description</span></span> |
|---|---|
|<span data-ttu-id="10daf-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="10daf-130">DependsOn</span></span> |<span data-ttu-id="10daf-131">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="10daf-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="10daf-132">De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is.</span><span class="sxs-lookup"><span data-stu-id="10daf-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="10daf-133">Zo</span><span class="sxs-lookup"><span data-stu-id="10daf-133">Ensure</span></span> |<span data-ttu-id="10daf-134">Hiermee wordt aangegeven of de services bestaan op het systeem.</span><span class="sxs-lookup"><span data-stu-id="10daf-134">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="10daf-135">Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de services niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="10daf-135">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="10daf-136">Als u deze optie instelt op **presen teren** , zorgt u ervoor dat doel services bestaan.</span><span class="sxs-lookup"><span data-stu-id="10daf-136">Setting it to **Present** ensures that target services exist.</span></span> <span data-ttu-id="10daf-137">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="10daf-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="10daf-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="10daf-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="10daf-139">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="10daf-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="10daf-140">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="10daf-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="10daf-141">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="10daf-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="10daf-142">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="10daf-142">Example</span></span>

<span data-ttu-id="10daf-143">Met de volgende configuratie worden de services Windows Audio en Extern bureaublad-services gestart.</span><span class="sxs-lookup"><span data-stu-id="10daf-143">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

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