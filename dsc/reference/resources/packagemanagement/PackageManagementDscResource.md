---
ms.date: 06/20/2018
keywords: DSC, powershell, configuratie en installatie
title: DSC-Package Management-Resource
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077616"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="e7470-103">DSC-Package Management-Resource</span><span class="sxs-lookup"><span data-stu-id="e7470-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="e7470-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e7470-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="e7470-105">De **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om te installeren of verwijderen van Package Management-pakketten op een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="e7470-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="e7470-106">Deze resource is vereist de **PackageManagement** -module, beschikbaar is via [ http://PowerShellGallery.com ](http://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="e7470-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](http://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e7470-107">De **PackageManagement** module moet ten minste versie 1.1.7.0 voor de volgende eigenschapsinformatie juist te zijn.</span><span class="sxs-lookup"><span data-stu-id="e7470-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7470-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e7470-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="e7470-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="e7470-109">Properties</span></span>

| <span data-ttu-id="e7470-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="e7470-110">Property</span></span> | <span data-ttu-id="e7470-111">Description</span><span class="sxs-lookup"><span data-stu-id="e7470-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="e7470-112">Naam</span><span class="sxs-lookup"><span data-stu-id="e7470-112">Name</span></span>| <span data-ttu-id="e7470-113">Hiermee geeft u de naam van het pakket dat moet worden geïnstalleerd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e7470-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="e7470-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="e7470-114">AdditionalParameters</span></span>| <span data-ttu-id="e7470-115">Specifieke hashtabel van de provider van de parameters die worden doorgegeven aan `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="e7470-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="e7470-116">Bijvoorbeeld, kunt u aanvullende parameters, zoals het doelpad doorgeven voor NuGet-provider.</span><span class="sxs-lookup"><span data-stu-id="e7470-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="e7470-117">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="e7470-117">Ensure</span></span>| <span data-ttu-id="e7470-118">Bepaalt of het pakket moet worden geïnstalleerd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e7470-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="e7470-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e7470-119">MaximumVersion</span></span>|<span data-ttu-id="e7470-120">Hiermee geeft u de maximaal toegestane versie van het pakket dat u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="e7470-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="e7470-121">Als u deze parameter niet toevoegt, zoekt de resource is de hoogste versie van het pakket.</span><span class="sxs-lookup"><span data-stu-id="e7470-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="e7470-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e7470-122">MinimumVersion</span></span>|<span data-ttu-id="e7470-123">Hiermee geeft u de minimaal toegestane versie van het pakket dat u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="e7470-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="e7470-124">Als u deze parameter niet toevoegt, de bron zoekt naar de hoogste versie van het pakket dat ook voldoet aan alle maximale opgegeven versie van het opgegeven door de _MaximumVersion_ parameter.</span><span class="sxs-lookup"><span data-stu-id="e7470-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="e7470-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e7470-125">ProviderName</span></span>| <span data-ttu-id="e7470-126">Hiermee geeft u de naam van een pakket provider waarnaar u wilt uw zoekopdracht pakket beperken.</span><span class="sxs-lookup"><span data-stu-id="e7470-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="e7470-127">Krijgt u provider-pakketnamen door het uitvoeren van de `Get-PackageProvider` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e7470-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="e7470-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e7470-128">RequiredVersion</span></span>| <span data-ttu-id="e7470-129">Hiermee geeft u de exacte versie van het pakket dat u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="e7470-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="e7470-130">Als u deze parameter niet opgeeft, deze DSC-resource wordt geïnstalleerd voor de nieuwste beschikbare versie van het pakket dat ook voldoet aan een maximale versie van het opgegeven door de _MaximumVersion_ parameter.</span><span class="sxs-lookup"><span data-stu-id="e7470-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="e7470-131">Bron</span><span class="sxs-lookup"><span data-stu-id="e7470-131">Source</span></span>| <span data-ttu-id="e7470-132">Hiermee geeft u de naam van de pakketbron waar het pakket kan worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="e7470-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="e7470-133">Dit kan een URI of een bron die is geregistreerd bij `Register-PackageSource` of PackageManagementSource DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="e7470-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="e7470-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="e7470-134">SourceCredential</span></span> | <span data-ttu-id="e7470-135">Hiermee geeft u een gebruikersaccount met rechten voor het installeren van een pakket voor een opgegeven pakket-provider of de bron.</span><span class="sxs-lookup"><span data-stu-id="e7470-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="e7470-136">Extra Parameters</span><span class="sxs-lookup"><span data-stu-id="e7470-136">Additional Parameters</span></span>

<span data-ttu-id="e7470-137">De volgende tabel bevat opties voor de eigenschap AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="e7470-137">The following table lists options for the AdditionalParameters property.</span></span>

| <span data-ttu-id="e7470-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="e7470-138">Parameter</span></span> | <span data-ttu-id="e7470-139">Description</span><span class="sxs-lookup"><span data-stu-id="e7470-139">Description</span></span> |
| --- | --- |
| <span data-ttu-id="e7470-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="e7470-140">DestinationPath</span></span>| <span data-ttu-id="e7470-141">Gebruikt door providers, zoals de geïntegreerde Nuget-Provider.</span><span class="sxs-lookup"><span data-stu-id="e7470-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="e7470-142">Hiermee geeft u een locatie waar u het pakket dat moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e7470-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="e7470-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="e7470-143">InstallationPolicy</span></span>| <span data-ttu-id="e7470-144">Gebruikt door providers, zoals de geïntegreerde Nuget-Provider.</span><span class="sxs-lookup"><span data-stu-id="e7470-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="e7470-145">Hiermee bepaalt u of u het pakket met de bron vertrouwt.</span><span class="sxs-lookup"><span data-stu-id="e7470-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="e7470-146">Een van: `Untrusted`, `Trusted`.</span><span class="sxs-lookup"><span data-stu-id="e7470-146">One of: `Untrusted`, `Trusted`.</span></span>|

## <a name="example"></a><span data-ttu-id="e7470-147">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e7470-147">Example</span></span>

<span data-ttu-id="e7470-148">In dit voorbeeld installeert de **JQuery** NuGet-pakket en **GistProvider** PowerShell module met behulp van de **PackageManagement** DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="e7470-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="e7470-149">In dit voorbeeld eerst zorgt ervoor dat de bronnen vereist pakket beschikbaar zijn en vervolgens definieert de verwachte status van de **JQuery** en **GistProvider** pakketten (NuGet en PowerShell, respectievelijk).</span><span class="sxs-lookup"><span data-stu-id="e7470-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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