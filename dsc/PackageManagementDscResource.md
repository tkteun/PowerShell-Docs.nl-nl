---
ms.date: 06/20/2018
keywords: DSC, powershell, configuratie, setup
title: DSC-PackageManagement Resource
ms.openlocfilehash: 3d52934b130d59acee4d7f8a92da2c743c1eb305
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753784"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="5d228-103">DSC-PackageManagement Resource</span><span class="sxs-lookup"><span data-stu-id="5d228-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="5d228-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 van Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d228-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="5d228-105">De **PackageManagement** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme om te installeren of verwijderen van pakketten in een doelknooppunt Package Management.</span><span class="sxs-lookup"><span data-stu-id="5d228-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="5d228-106">Deze resource vereist de **PackageManagement** module beschikbaar is via http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="5d228-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d228-107">De **PackageManagement** module moet ten minste versie 1.1.7.0 voor de volgende eigenschapsinformatie juist te zijn.</span><span class="sxs-lookup"><span data-stu-id="5d228-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d228-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5d228-108">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="5d228-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="5d228-109">Properties</span></span>

|  <span data-ttu-id="5d228-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="5d228-110">Property</span></span>  |  <span data-ttu-id="5d228-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5d228-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="5d228-112">Naam</span><span class="sxs-lookup"><span data-stu-id="5d228-112">Name</span></span>| <span data-ttu-id="5d228-113">Hiermee geeft u de naam van het pakket dat moet worden geïnstalleerd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5d228-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="5d228-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="5d228-114">AdditionalParameters</span></span>| <span data-ttu-id="5d228-115">Specifieke hashtabel van de provider van de parameters die worden doorgegeven aan `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="5d228-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="5d228-116">U kunt bijvoorbeeld aanvullende parameters zoals doelpad doorgeven voor NuGet-provider.</span><span class="sxs-lookup"><span data-stu-id="5d228-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="5d228-117">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="5d228-117">Ensure</span></span>| <span data-ttu-id="5d228-118">Bepaalt of het pakket moet worden geïnstalleerd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5d228-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="5d228-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="5d228-119">MaximumVersion</span></span>|<span data-ttu-id="5d228-120">Hiermee geeft u de maximaal toegestane versie van het pakket dat u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="5d228-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="5d228-121">Als u deze parameter niet toevoegt, wordt de hoogste versie van het pakket gevonden in de resource.</span><span class="sxs-lookup"><span data-stu-id="5d228-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="5d228-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="5d228-122">MinimumVersion</span></span>|<span data-ttu-id="5d228-123">Hiermee geeft u de minimaal toegestane versie van het pakket dat u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="5d228-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="5d228-124">Als u deze parameter niet toevoegt, de bron zoekt de hoogste versie van het pakket dat ook voldoet aan alle opgegeven maximumversie opgegeven door de _MaximumVersion_ parameter.</span><span class="sxs-lookup"><span data-stu-id="5d228-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="5d228-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="5d228-125">ProviderName</span></span>| <span data-ttu-id="5d228-126">Hiermee geeft u een providernaam pakket waarnaar als bereik voor uw zoekopdracht pakket.</span><span class="sxs-lookup"><span data-stu-id="5d228-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="5d228-127">U kunt providernamen pakket ophalen door het uitvoeren van de `Get-PackageProvider` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5d228-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="5d228-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5d228-128">RequiredVersion</span></span>| <span data-ttu-id="5d228-129">Hiermee geeft u de exacte versie van het pakket dat u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="5d228-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="5d228-130">Als u deze parameter niet opgeeft, deze DSC-resource worden geïnstalleerd voor de nieuwste versie van het pakket dat ook voldoet aan alle maximale versie van het opgegeven door de _MaximumVersion_ parameter.</span><span class="sxs-lookup"><span data-stu-id="5d228-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="5d228-131">Bron</span><span class="sxs-lookup"><span data-stu-id="5d228-131">Source</span></span>| <span data-ttu-id="5d228-132">Hiermee geeft u de naam van de pakketbron waar het pakket kan worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="5d228-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="5d228-133">Dit kan een URI of een bron die is geregistreerd bij `Register-PackageSource` of PackageManagementSource DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="5d228-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="5d228-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="5d228-134">SourceCredential</span></span> | <span data-ttu-id="5d228-135">Hiermee geeft u een gebruikersaccount met rechten voor het installeren van een pakket voor een opgegeven pakket-provider of de bron.</span><span class="sxs-lookup"><span data-stu-id="5d228-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="5d228-136">Extra Parameters</span><span class="sxs-lookup"><span data-stu-id="5d228-136">Additional Parameters</span></span>

<span data-ttu-id="5d228-137">De volgende tabel geeft een lijst met opties voor de eigenschap AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="5d228-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="5d228-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="5d228-138">Parameter</span></span>  | <span data-ttu-id="5d228-139">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5d228-139">Description</span></span>   |
|---|---|
| <span data-ttu-id="5d228-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="5d228-140">DestinationPath</span></span>| <span data-ttu-id="5d228-141">Gebruikt door providers zoals de ingebouwde Nuget-Provider.</span><span class="sxs-lookup"><span data-stu-id="5d228-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="5d228-142">Hiermee geeft u een locatie waar u het pakket worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="5d228-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="5d228-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="5d228-143">InstallationPolicy</span></span>| <span data-ttu-id="5d228-144">Gebruikt door providers zoals de ingebouwde Nuget-Provider.</span><span class="sxs-lookup"><span data-stu-id="5d228-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="5d228-145">Hiermee bepaalt u of u het pakket bron vertrouwt.</span><span class="sxs-lookup"><span data-stu-id="5d228-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="5d228-146">Een van: 'Niet vertrouwd', 'Vertrouwd'.</span><span class="sxs-lookup"><span data-stu-id="5d228-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="5d228-147">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5d228-147">Example</span></span>

<span data-ttu-id="5d228-148">Dit voorbeeld installeert de **JQuery** NuGet-pakket en **GistProvider** PowerShell module met behulp van de **PackageManagement** DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="5d228-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="5d228-149">In dit voorbeeld eerst zorgt ervoor dat de vereiste pakket bronnen beschikbaar zijn en vervolgens definieert de verwachte status van de **JQuery** en **GistProvider** pakketten (NuGet en PowerShell, respectievelijk).</span><span class="sxs-lookup"><span data-stu-id="5d228-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```