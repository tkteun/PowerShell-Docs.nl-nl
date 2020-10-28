---
ms.date: 07/15/2020
ms.topic: reference
title: DSC Package Management-resource
description: DSC Package Management-resource
ms.openlocfilehash: b6676860acea094e04479e38f29ee7c72430851b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667365"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="5eb12-103">DSC Package Management-resource</span><span class="sxs-lookup"><span data-stu-id="5eb12-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="5eb12-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0, Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="5eb12-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="5eb12-105">De **Package Management** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het installeren of verwijderen van pakket beheer pakketten op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5eb12-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="5eb12-106">Deze bron vereist de module **Package Management** , die beschikbaar is via [https://PowerShellGallery.com](https://PowerShellGallery.com) .</span><span class="sxs-lookup"><span data-stu-id="5eb12-106">This resource requires the **PackageManagement** module, available from [https://PowerShellGallery.com](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5eb12-107">De **Package Management** -module moet ten minste versie 1.1.7.0 zijn voor de volgende eigenschaps gegevens die u wilt corrigeren.</span><span class="sxs-lookup"><span data-stu-id="5eb12-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="5eb12-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="5eb12-108">Syntax</span></span>

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ PsDscRunAsCredential = [PSCredential] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="5eb12-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="5eb12-109">Properties</span></span>

|<span data-ttu-id="5eb12-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="5eb12-110">Property</span></span> |<span data-ttu-id="5eb12-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5eb12-111">Description</span></span> |
|---|---|
|<span data-ttu-id="5eb12-112">Naam</span><span class="sxs-lookup"><span data-stu-id="5eb12-112">Name</span></span> |<span data-ttu-id="5eb12-113">Hiermee geeft u de naam op van het pakket dat moet worden geïnstalleerd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5eb12-113">Specifies the name of the Package to be installed or uninstalled.</span></span> |
|<span data-ttu-id="5eb12-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="5eb12-114">AdditionalParameters</span></span> |<span data-ttu-id="5eb12-115">Providerspecifieke hashtabel van para meters die worden door gegeven aan `Get-Package -AdditionalArguments` .</span><span class="sxs-lookup"><span data-stu-id="5eb12-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="5eb12-116">U kunt bijvoorbeeld voor NuGet-provider aanvullende para meters door geven zoals doelpad.</span><span class="sxs-lookup"><span data-stu-id="5eb12-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span> |
|<span data-ttu-id="5eb12-117">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="5eb12-117">MaximumVersion</span></span> |<span data-ttu-id="5eb12-118">Hiermee geeft u de Maxi maal toegestane versie van het pakket dat u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="5eb12-118">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="5eb12-119">Als u deze para meter niet toevoegt, vindt de resource de hoogste beschik bare versie van het pakket.</span><span class="sxs-lookup"><span data-stu-id="5eb12-119">If you do not add this parameter, the resource finds the highest available version of the package.</span></span> |
|<span data-ttu-id="5eb12-120">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="5eb12-120">MinimumVersion</span></span> |<span data-ttu-id="5eb12-121">Hiermee geeft u de mini maal toegestane versie van het pakket dat u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="5eb12-121">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="5eb12-122">Als u deze para meter niet toevoegt, zoekt de resource de hoogste beschik bare versie van het pakket die ook voldoet aan de maximum opgegeven versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="5eb12-122">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="5eb12-123">ProviderName</span><span class="sxs-lookup"><span data-stu-id="5eb12-123">ProviderName</span></span> |<span data-ttu-id="5eb12-124">Hiermee geeft u de naam van een pakket provider op waarmee u de pakket zoekopdracht wilt bereiken.</span><span class="sxs-lookup"><span data-stu-id="5eb12-124">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="5eb12-125">U kunt pakket provider namen ophalen door de cmdlet uit te voeren `Get-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="5eb12-125">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span> |
|<span data-ttu-id="5eb12-126">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5eb12-126">RequiredVersion</span></span> |<span data-ttu-id="5eb12-127">Hiermee geeft u de exacte versie van het pakket op dat u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="5eb12-127">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="5eb12-128">Als u deze para meter niet opgeeft, installeert deze DSC-resource de nieuwste beschik bare versie van het pakket die ook voldoet aan de maximum versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="5eb12-128">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="5eb12-129">Bron</span><span class="sxs-lookup"><span data-stu-id="5eb12-129">Source</span></span> |<span data-ttu-id="5eb12-130">Hiermee geeft u de naam van de pakket bron op waarin het pakket kan worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="5eb12-130">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="5eb12-131">Dit kan een URI zijn of een bron die is geregistreerd bij `Register-PackageSource` of PACKAGEMANAGEMENTSOURCE DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="5eb12-131">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span> |
|<span data-ttu-id="5eb12-132">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="5eb12-132">SourceCredential</span></span> |<span data-ttu-id="5eb12-133">Hiermee geeft u een gebruikers account op dat rechten heeft om een pakket te installeren voor een opgegeven pakket provider of bron.</span><span class="sxs-lookup"><span data-stu-id="5eb12-133">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span> |

## <a name="additional-parameters"></a><span data-ttu-id="5eb12-134">Aanvullende para meters</span><span class="sxs-lookup"><span data-stu-id="5eb12-134">Additional Parameters</span></span>

<span data-ttu-id="5eb12-135">De volgende tabel bevat de opties voor de eigenschap AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="5eb12-135">The following table lists options for the AdditionalParameters property.</span></span>

|<span data-ttu-id="5eb12-136">Parameter</span><span class="sxs-lookup"><span data-stu-id="5eb12-136">Parameter</span></span> |<span data-ttu-id="5eb12-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5eb12-137">Description</span></span> |
|---|---|
|<span data-ttu-id="5eb12-138">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="5eb12-138">DestinationPath</span></span> |<span data-ttu-id="5eb12-139">Wordt gebruikt door providers zoals de ingebouwde Nuget-provider.</span><span class="sxs-lookup"><span data-stu-id="5eb12-139">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="5eb12-140">Hiermee geeft u een bestands locatie op waar het pakket moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="5eb12-140">Specifies a file location where you want the package to be installed.</span></span> |
|<span data-ttu-id="5eb12-141">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="5eb12-141">InstallationPolicy</span></span> |<span data-ttu-id="5eb12-142">Wordt gebruikt door providers zoals de ingebouwde Nuget-provider.</span><span class="sxs-lookup"><span data-stu-id="5eb12-142">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="5eb12-143">Hiermee wordt bepaald of u de bron van het pakket vertrouwt.</span><span class="sxs-lookup"><span data-stu-id="5eb12-143">Determines whether you trust the package's source.</span></span> <span data-ttu-id="5eb12-144">Een van: **niet-vertrouwd** of **vertrouwd** .</span><span class="sxs-lookup"><span data-stu-id="5eb12-144">One of: **Untrusted** or **Trusted** .</span></span> |

## <a name="common-properties"></a><span data-ttu-id="5eb12-145">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="5eb12-145">Common properties</span></span>

|<span data-ttu-id="5eb12-146">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="5eb12-146">Property</span></span> |<span data-ttu-id="5eb12-147">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5eb12-147">Description</span></span> |
|---|---|
|<span data-ttu-id="5eb12-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5eb12-148">DependsOn</span></span> |<span data-ttu-id="5eb12-149">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="5eb12-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5eb12-150">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="5eb12-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="5eb12-151">Zo</span><span class="sxs-lookup"><span data-stu-id="5eb12-151">Ensure</span></span> |<span data-ttu-id="5eb12-152">Hiermee wordt bepaald of het pakket moet worden geïnstalleerd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5eb12-152">Determines whether the package is to be installed or uninstalled.</span></span> <span data-ttu-id="5eb12-153">De standaard waarde is **aanwezig** .</span><span class="sxs-lookup"><span data-stu-id="5eb12-153">The default value is **Present** .</span></span> |
|<span data-ttu-id="5eb12-154">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="5eb12-154">PsDscRunAsCredential</span></span> |<span data-ttu-id="5eb12-155">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="5eb12-155">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="5eb12-156">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="5eb12-156">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="5eb12-157">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5eb12-157">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="5eb12-158">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5eb12-158">Example</span></span>

<span data-ttu-id="5eb12-159">In dit voor beeld wordt het **jQuery** NuGet-pakket en de **GistProvider** Power shell-module geïnstalleerd met behulp van de **Package Management** DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="5eb12-159">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="5eb12-160">In dit voor beeld wordt eerst gegarandeerd dat de vereiste pakket bronnen beschikbaar zijn en definieert vervolgens de verwachte status van de **jQuery** -en **GistProvider** -pakketten (respectievelijk NuGet en Power shell).</span><span class="sxs-lookup"><span data-stu-id="5eb12-160">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
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
