---
ms.date: 07/15/2020
ms.topic: reference
title: DSC PackageManagementSource-resource
description: DSC PackageManagementSource-resource
ms.openlocfilehash: 495b6548ef86f639e93b914ec8bd8ea7818ff8dd
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142851"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="dad6a-103">DSC PackageManagementSource-resource</span><span class="sxs-lookup"><span data-stu-id="dad6a-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="dad6a-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="dad6a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="dad6a-105">De **PackageManagementSource** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het registreren of ongedaan maken van de registratie van pakket beheer bronnen op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="dad6a-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span>
<span data-ttu-id="dad6a-106">**Pakket beheer bronnen die op deze manier zijn geregistreerd, worden geregistreerd in de systeem context, die bruikbaar is voor het systeem account of de DSC-engine.**</span><span class="sxs-lookup"><span data-stu-id="dad6a-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="dad6a-107">Deze bron vereist de module **Package Management** , die beschikbaar is via de [PowerShell Gallery](https://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="dad6a-107">This resource requires the **PackageManagement** module, available from the [PowerShell Gallery](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dad6a-108">De **Package Management** -module moet ten minste versie 1.1.7.0 zijn voor de volgende eigenschaps gegevens die u wilt corrigeren.</span><span class="sxs-lookup"><span data-stu-id="dad6a-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="dad6a-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="dad6a-109">Syntax</span></span>

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="dad6a-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="dad6a-110">Properties</span></span>

|<span data-ttu-id="dad6a-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="dad6a-111">Property</span></span> |<span data-ttu-id="dad6a-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dad6a-112">Description</span></span> |
|---|---|
|<span data-ttu-id="dad6a-113">Naam</span><span class="sxs-lookup"><span data-stu-id="dad6a-113">Name</span></span> |<span data-ttu-id="dad6a-114">Hiermee geeft u de naam van de pakket bron moet worden geregistreerd of niet geregistreerd op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="dad6a-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span> |
|<span data-ttu-id="dad6a-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="dad6a-115">ProviderName</span></span> |<span data-ttu-id="dad6a-116">Hiermee geeft u de naam van de OneGet-provider op waarmee u interop met de pakket bron kunt doen.</span><span class="sxs-lookup"><span data-stu-id="dad6a-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span> |
|<span data-ttu-id="dad6a-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="dad6a-117">SourceLocation</span></span> |<span data-ttu-id="dad6a-118">Hiermee geeft u de URI van de pakket bron.</span><span class="sxs-lookup"><span data-stu-id="dad6a-118">Specifies the URI of the package source.</span></span> |
|<span data-ttu-id="dad6a-119">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="dad6a-119">InstallationPolicy</span></span> |<span data-ttu-id="dad6a-120">Wordt gebruikt door providers zoals de ingebouwde Nuget-provider.</span><span class="sxs-lookup"><span data-stu-id="dad6a-120">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="dad6a-121">Hiermee wordt bepaald of u de bron van het pakket vertrouwt.</span><span class="sxs-lookup"><span data-stu-id="dad6a-121">Determines whether you trust the package's source.</span></span> <span data-ttu-id="dad6a-122">Een van: **niet-vertrouwd** of **vertrouwd** .</span><span class="sxs-lookup"><span data-stu-id="dad6a-122">One of: **Untrusted** or **Trusted** .</span></span> |
|<span data-ttu-id="dad6a-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="dad6a-123">SourceCredential</span></span> |<span data-ttu-id="dad6a-124">Biedt toegang tot het pakket op een externe bron.</span><span class="sxs-lookup"><span data-stu-id="dad6a-124">Provides access to the package on a remote source.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="dad6a-125">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="dad6a-125">Common properties</span></span>

|<span data-ttu-id="dad6a-126">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="dad6a-126">Property</span></span> |<span data-ttu-id="dad6a-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dad6a-127">Description</span></span> |
|---|---|
|<span data-ttu-id="dad6a-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dad6a-128">DependsOn</span></span> |<span data-ttu-id="dad6a-129">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="dad6a-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dad6a-130">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="dad6a-130">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="dad6a-131">Zo</span><span class="sxs-lookup"><span data-stu-id="dad6a-131">Ensure</span></span> |<span data-ttu-id="dad6a-132">Hiermee wordt bepaald of de bron van het pakket moet worden geregistreerd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="dad6a-132">Determines whether the package source is to be registered or unregistered.</span></span> <span data-ttu-id="dad6a-133">De standaard waarde is **aanwezig** .</span><span class="sxs-lookup"><span data-stu-id="dad6a-133">The default value is **Present** .</span></span> |
|<span data-ttu-id="dad6a-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="dad6a-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="dad6a-135">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="dad6a-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="dad6a-136">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="dad6a-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="dad6a-137">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dad6a-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="dad6a-138">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="dad6a-138">Example</span></span>

<span data-ttu-id="dad6a-139">In dit voor beeld wordt de `https://nuget.org` pakket bron geregistreerd met behulp van de DSC-resource **PackageManagementSource** .</span><span class="sxs-lookup"><span data-stu-id="dad6a-139">This example registers the `https://nuget.org` package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```
