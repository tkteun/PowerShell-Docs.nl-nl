---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-PackageManagementSource Resource
ms.openlocfilehash: 80d157aff5bf7685a797baaf6a26215f02473096
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="abb52-103">DSC-PackageManagementSource Resource</span><span class="sxs-lookup"><span data-stu-id="abb52-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="abb52-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="abb52-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="abb52-105">De **PackageManagementSource** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme om te registreren of de registratie van gegevensbronnen in een doelknooppunt Package Management.</span><span class="sxs-lookup"><span data-stu-id="abb52-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="abb52-106">**Pakket Management bronnen geregistreerd op deze manier zijn geregistreerd met de systeemcontext, kan worden gebruikt door het systeem-account of door de DSC-engine.**</span><span class="sxs-lookup"><span data-stu-id="abb52-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="abb52-107">Deze resource vereist de **PackageManagement** module beschikbaar is via http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="abb52-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="abb52-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="abb52-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="abb52-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="abb52-109">Properties</span></span>
|  <span data-ttu-id="abb52-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="abb52-110">Property</span></span>  |  <span data-ttu-id="abb52-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="abb52-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="abb52-112">Naam</span><span class="sxs-lookup"><span data-stu-id="abb52-112">Name</span></span>| <span data-ttu-id="abb52-113">Hiermee geeft u de naam van de pakketbron om te worden ingeschreven of niet geregistreerd op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="abb52-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>| 
| <span data-ttu-id="abb52-114">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="abb52-114">Ensure</span></span>| <span data-ttu-id="abb52-115">Hiermee wordt bepaald of de pakketbron worden geregistreerd of de registratie is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="abb52-115">Determines whether the package source is to be registered or unregistered.</span></span>| 
| <span data-ttu-id="abb52-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="abb52-116">InstallationPolicy</span></span>| <span data-ttu-id="abb52-117">Hiermee bepaalt u of u de pakketbron vertrouwt.</span><span class="sxs-lookup"><span data-stu-id="abb52-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="abb52-118">Een van: 'Niet vertrouwd', 'Vertrouwd'.</span><span class="sxs-lookup"><span data-stu-id="abb52-118">One of: "Untrusted", "Trusted".</span></span>| 
| <span data-ttu-id="abb52-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="abb52-119">ProviderName</span></span>| <span data-ttu-id="abb52-120">Hiermee geeft u de naam van de OneGet provider waarmee u interop met de pakketbron kunt.</span><span class="sxs-lookup"><span data-stu-id="abb52-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>| 
| <span data-ttu-id="abb52-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="abb52-121">SourceUri</span></span>| <span data-ttu-id="abb52-122">Hiermee geeft u de URI van de pakketbron.</span><span class="sxs-lookup"><span data-stu-id="abb52-122">Specifies the URI of the package source.</span></span>| 
| <span data-ttu-id="abb52-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="abb52-123">SourceCredential</span></span>| <span data-ttu-id="abb52-124">Biedt toegang tot het pakket op een externe bron.</span><span class="sxs-lookup"><span data-stu-id="abb52-124">Provides access to the package on a remote source.</span></span>| 

## <a name="example"></a><span data-ttu-id="abb52-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="abb52-125">Example</span></span>

<span data-ttu-id="abb52-126">In dit voorbeeld wordt de http://nuget.org pakket bron via de **PackageManagementSource** DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="abb52-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

