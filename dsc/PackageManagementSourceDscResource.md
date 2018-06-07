---
ms.date: 06/20/2018
keywords: DSC, powershell, configuratie, setup
title: DSC-PackageManagementSource Resource
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753767"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="5404a-103">DSC-PackageManagementSource Resource</span><span class="sxs-lookup"><span data-stu-id="5404a-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="5404a-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 van Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5404a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="5404a-105">De **PackageManagementSource** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme om te registreren of de registratie van gegevensbronnen in een doelknooppunt Package Management.</span><span class="sxs-lookup"><span data-stu-id="5404a-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="5404a-106">**Pakket Management bronnen geregistreerd op deze manier zijn geregistreerd met de systeemcontext, kan worden gebruikt door het systeem-account of door de DSC-engine.**</span><span class="sxs-lookup"><span data-stu-id="5404a-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="5404a-107">Deze resource vereist de **PackageManagement** module beschikbaar is via http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="5404a-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5404a-108">De **PackageManagement** module moet ten minste versie 1.1.7.0 voor de volgende eigenschapsinformatie juist te zijn.</span><span class="sxs-lookup"><span data-stu-id="5404a-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="5404a-109">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5404a-109">Syntax</span></span>

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="5404a-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="5404a-110">Properties</span></span>

|  <span data-ttu-id="5404a-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="5404a-111">Property</span></span>  |  <span data-ttu-id="5404a-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5404a-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="5404a-113">Naam</span><span class="sxs-lookup"><span data-stu-id="5404a-113">Name</span></span>| <span data-ttu-id="5404a-114">Hiermee geeft u de naam van de pakketbron om te worden ingeschreven of niet geregistreerd op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="5404a-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="5404a-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="5404a-115">ProviderName</span></span>| <span data-ttu-id="5404a-116">Hiermee geeft u de naam van de OneGet provider waarmee u interop met de pakketbron kunt.</span><span class="sxs-lookup"><span data-stu-id="5404a-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="5404a-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="5404a-117">SourceLocation</span></span>| <span data-ttu-id="5404a-118">Hiermee geeft u de URI van de pakketbron.</span><span class="sxs-lookup"><span data-stu-id="5404a-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="5404a-119">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="5404a-119">Ensure</span></span>| <span data-ttu-id="5404a-120">Hiermee wordt bepaald of de pakketbron worden geregistreerd of de registratie is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5404a-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="5404a-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="5404a-121">InstallationPolicy</span></span>| <span data-ttu-id="5404a-122">Gebruikt door providers zoals de ingebouwde Nuget-Provider.</span><span class="sxs-lookup"><span data-stu-id="5404a-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="5404a-123">Hiermee bepaalt u of u het pakket bron vertrouwt.</span><span class="sxs-lookup"><span data-stu-id="5404a-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="5404a-124">Een van: 'Niet vertrouwd', 'Vertrouwd'.</span><span class="sxs-lookup"><span data-stu-id="5404a-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="5404a-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="5404a-125">SourceCredential</span></span>| <span data-ttu-id="5404a-126">Biedt toegang tot het pakket op een externe bron.</span><span class="sxs-lookup"><span data-stu-id="5404a-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="5404a-127">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5404a-127">Example</span></span>

<span data-ttu-id="5404a-128">In dit voorbeeld wordt de http://nuget.org pakket bron met behulp van de **PackageManagementSource** DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="5404a-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```