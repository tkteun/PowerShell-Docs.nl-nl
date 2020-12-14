---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: 602d160a4cc7fd4e8a806d2c3d2772ee5053535d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889688"
---
# <span data-ttu-id="4c80c-103">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="4c80c-103">Publish-Module</span></span>

## <span data-ttu-id="4c80c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4c80c-104">SYNOPSIS</span></span>
<span data-ttu-id="4c80c-105">Hiermee publiceert u een opgegeven module van de lokale computer naar een online galerie.</span><span class="sxs-lookup"><span data-stu-id="4c80c-105">Publishes a specified module from the local computer to an online gallery.</span></span>

## <span data-ttu-id="4c80c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4c80c-106">SYNTAX</span></span>

### <span data-ttu-id="4c80c-107">ModuleNameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="4c80c-107">ModuleNameParameterSet (Default)</span></span>

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4c80c-108">ModulePathParameterSet</span><span class="sxs-lookup"><span data-stu-id="4c80c-108">ModulePathParameterSet</span></span>

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4c80c-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4c80c-109">DESCRIPTION</span></span>

<span data-ttu-id="4c80c-110">De `Publish-Module` cmdlet publiceert een module naar een online NuGet-galerie met behulp van een API-sleutel, opgeslagen als onderdeel van een gebruikers profiel in de galerie.</span><span class="sxs-lookup"><span data-stu-id="4c80c-110">The `Publish-Module` cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="4c80c-111">U kunt opgeven welke module moet worden gepubliceerd door de naam van de module of door het pad naar de map met de module.</span><span class="sxs-lookup"><span data-stu-id="4c80c-111">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="4c80c-112">Wanneer u een module op naam opgeeft, wordt `Publish-Module` de eerste module gepubliceerd die zou worden gevonden door uit te voeren `Get-Module -ListAvailable <Name>` .</span><span class="sxs-lookup"><span data-stu-id="4c80c-112">When you specify a module by name, `Publish-Module` publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="4c80c-113">Als u een minimum versie van een module opgeeft om te publiceren, `Publish-Module` publiceert de eerste module met een versie die groter is dan of gelijk is aan de minimum versie die u hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="4c80c-113">If you specify a minimum version of a module to publish, `Publish-Module` publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="4c80c-114">Voor het publiceren van een module zijn meta gegevens vereist die worden weer gegeven op de galerie pagina voor de module.</span><span class="sxs-lookup"><span data-stu-id="4c80c-114">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="4c80c-115">De vereiste meta gegevens bevatten de module naam, versie, beschrijving en auteur.</span><span class="sxs-lookup"><span data-stu-id="4c80c-115">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="4c80c-116">Hoewel de meeste meta gegevens worden opgehaald uit het module manifest, moeten sommige meta gegevens worden opgegeven in `Publish-Module` para meters, zoals **tag**, **ReleaseNote**, **IconUri**, **ProjectUri** en **LicenseUri**, omdat deze para meters overeenkomen met velden in een op NuGet gebaseerde galerie.</span><span class="sxs-lookup"><span data-stu-id="4c80c-116">Although most metadata is taken from the module manifest, some metadata must be specified in `Publish-Module` parameters, such as **Tag**, **ReleaseNote**, **IconUri**, **ProjectUri**, and **LicenseUri**, because these parameters match fields in a NuGet-based gallery.</span></span>

## <span data-ttu-id="4c80c-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4c80c-117">EXAMPLES</span></span>

### <span data-ttu-id="4c80c-118">Voor beeld 1: een module publiceren</span><span class="sxs-lookup"><span data-stu-id="4c80c-118">Example 1: Publish a module</span></span>

<span data-ttu-id="4c80c-119">In dit voor beeld wordt MyDscModule in de online galerie gepubliceerd met behulp van de API-sleutel om het online galerie account van de module eigenaar aan te geven.</span><span class="sxs-lookup"><span data-stu-id="4c80c-119">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's online gallery account.</span></span> <span data-ttu-id="4c80c-120">Als MyDscModule geen geldige manifest module is die een naam, versie, beschrijving en auteur opgeeft, treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="4c80c-120">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### <span data-ttu-id="4c80c-121">Voor beeld 2: een module met de meta gegevens van de galerie publiceren</span><span class="sxs-lookup"><span data-stu-id="4c80c-121">Example 2: Publish a module with gallery metadata</span></span>

<span data-ttu-id="4c80c-122">In dit voor beeld wordt MyDscModule in de online galerie gepubliceerd met behulp van de API-sleutel om het Galerie account van de module eigenaar aan te geven.</span><span class="sxs-lookup"><span data-stu-id="4c80c-122">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's gallery account.</span></span> <span data-ttu-id="4c80c-123">De aanvullende meta gegevens worden weer gegeven op de webpagina van de module in de galerie.</span><span class="sxs-lookup"><span data-stu-id="4c80c-123">The additional metadata provided is displayed on the webpage for the module in the gallery.</span></span> <span data-ttu-id="4c80c-124">De eigenaar voegt twee zoek tags voor de module toe, met betrekking tot Active Directory. Er wordt een korte release opmerking toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="4c80c-124">The owner adds two search tags for the module, relating it to Active Directory; a brief release note is added.</span></span> <span data-ttu-id="4c80c-125">Als MyDscModule geen geldige manifest module is die een naam, versie, beschrijving en auteur opgeeft, treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="4c80c-125">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## <span data-ttu-id="4c80c-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4c80c-126">PARAMETERS</span></span>

### <span data-ttu-id="4c80c-127">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="4c80c-127">-AllowPrerelease</span></span>

<span data-ttu-id="4c80c-128">Hiermee kunnen modules die zijn gemarkeerd als Prerelease, worden gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="4c80c-128">Allows modules marked as prerelease to be published.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4c80c-129">-Confirm</span></span>

<span data-ttu-id="4c80c-130">Vraagt u om bevestiging voordat de wordt uitgevoerd `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="4c80c-130">Prompts you for confirmation before running the `Publish-Module`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="4c80c-131">-Credential</span></span>

<span data-ttu-id="4c80c-132">Hiermee geeft u een gebruikers account op dat beschikt over rechten voor het publiceren van een module voor een opgegeven pakket provider of bron.</span><span class="sxs-lookup"><span data-stu-id="4c80c-132">Specifies a user account that has rights to publish a module for a specified package provider or source.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-133">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="4c80c-133">-Exclude</span></span>

<span data-ttu-id="4c80c-134">Hiermee worden bestanden gedefinieerd die moeten worden uitgesloten van de gepubliceerde module.</span><span class="sxs-lookup"><span data-stu-id="4c80c-134">Defines files to exclude from the published module.</span></span> <span data-ttu-id="4c80c-135">Ondersteuning voor **uitsluiting** van para meters is toevoegen in **PowershellGet** -versie 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="4c80c-135">**Exclude** parameter support is add in **PowershellGet** version 2.0.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-136">-Force</span><span class="sxs-lookup"><span data-stu-id="4c80c-136">-Force</span></span>

<span data-ttu-id="4c80c-137">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="4c80c-137">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-138">-FormatVersion</span><span class="sxs-lookup"><span data-stu-id="4c80c-138">-FormatVersion</span></span>

<span data-ttu-id="4c80c-139">Accepteert alleen geldige waarden die zijn opgegeven met het kenmerk **Validate** .</span><span class="sxs-lookup"><span data-stu-id="4c80c-139">Accepts only valid values specified by the **ValidateSet** attribute.</span></span>

<span data-ttu-id="4c80c-140">Zie [Validate-kenmerk declaratie](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) en [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4c80c-140">For more information, see [ValidateSet Attribute Declaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) and [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:
Accepted values: 2.0

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-141">-IconUri</span><span class="sxs-lookup"><span data-stu-id="4c80c-141">-IconUri</span></span>

<span data-ttu-id="4c80c-142">Hiermee geeft u de URL op van een pictogram voor de module.</span><span class="sxs-lookup"><span data-stu-id="4c80c-142">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="4c80c-143">Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor de module.</span><span class="sxs-lookup"><span data-stu-id="4c80c-143">The specified icon is displayed on the gallery webpage for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-144">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="4c80c-144">-LicenseUri</span></span>

<span data-ttu-id="4c80c-145">Hiermee geeft u de URL op van de licentie voorwaarden voor de module die u wilt publiceren.</span><span class="sxs-lookup"><span data-stu-id="4c80c-145">Specifies the URL of licensing terms for the module you want to publish.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-146">-Name</span><span class="sxs-lookup"><span data-stu-id="4c80c-146">-Name</span></span>

<span data-ttu-id="4c80c-147">Hiermee geeft u de naam van de module die u wilt publiceren.</span><span class="sxs-lookup"><span data-stu-id="4c80c-147">Specifies the name of the module that you want to publish.</span></span> <span data-ttu-id="4c80c-148">`Publish-Module` zoekt naar de opgegeven module naam in `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="4c80c-148">`Publish-Module` searches for the specified module name in `$Env:PSModulePath`.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-149">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="4c80c-149">-NuGetApiKey</span></span>

<span data-ttu-id="4c80c-150">Hiermee geeft u de API-sleutel op die u wilt gebruiken voor het publiceren van een module naar de online galerie.</span><span class="sxs-lookup"><span data-stu-id="4c80c-150">Specifies the API key that you want to use to publish a module to the online gallery.</span></span> <span data-ttu-id="4c80c-151">De API-sleutel maakt deel uit van uw profiel in de online galerie en is te vinden op de pagina met uw gebruikers account in de galerie.</span><span class="sxs-lookup"><span data-stu-id="4c80c-151">The API key is part of your profile in the online gallery, and can be found on your user account page in the gallery.</span></span> <span data-ttu-id="4c80c-152">De API-sleutel is NuGet-specifieke functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="4c80c-152">The API key is NuGet-specific functionality.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-153">-Path</span><span class="sxs-lookup"><span data-stu-id="4c80c-153">-Path</span></span>

<span data-ttu-id="4c80c-154">Hiermee geeft u het pad op naar de module die u wilt publiceren.</span><span class="sxs-lookup"><span data-stu-id="4c80c-154">Specifies the path to the module that you want to publish.</span></span> <span data-ttu-id="4c80c-155">Deze para meter accepteert het pad naar de map waarin de module zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="4c80c-155">This parameter accepts the path to the folder that contains the module.</span></span>

```yaml
Type: System.String
Parameter Sets: ModulePathParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-156">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="4c80c-156">-ProjectUri</span></span>

<span data-ttu-id="4c80c-157">Hiermee geeft u de URL van een webpagina over dit project op.</span><span class="sxs-lookup"><span data-stu-id="4c80c-157">Specifies the URL of a webpage about this project.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-158">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="4c80c-158">-ReleaseNotes</span></span>

<span data-ttu-id="4c80c-159">Hiermee geeft u een teken reeks met release opmerkingen of opmerkingen die u beschikbaar wilt maken voor gebruikers van deze versie van de module.</span><span class="sxs-lookup"><span data-stu-id="4c80c-159">Specifies a string containing release notes or comments that you want to be available to users of this version of the module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-160">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="4c80c-160">-Repository</span></span>

<span data-ttu-id="4c80c-161">Hiermee geeft u de beschrijvende naam op van een opslag plaats die is geregistreerd door te worden uitgevoerd `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="4c80c-161">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="4c80c-162">De opslag plaats moet een **PublishLocation** hebben. Dit is een geldige NUGET-URI.</span><span class="sxs-lookup"><span data-stu-id="4c80c-162">The repository must have a **PublishLocation**, which is a valid NuGet URI.</span></span>
<span data-ttu-id="4c80c-163">De **PublishLocation** kan worden ingesteld door te worden uitgevoerd `Set-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="4c80c-163">The **PublishLocation** can be set by running `Set-PSRepository`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="4c80c-164">-RequiredVersion</span></span>

<span data-ttu-id="4c80c-165">Hiermee geeft u de exacte versie van één module op die moet worden gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="4c80c-165">Specifies the exact version of a single module to publish.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-166">-SkipAutomaticTags</span><span class="sxs-lookup"><span data-stu-id="4c80c-166">-SkipAutomaticTags</span></span>

<span data-ttu-id="4c80c-167">Hiermee verwijdert u opdrachten en resources uit de tags die u wilt opnemen.</span><span class="sxs-lookup"><span data-stu-id="4c80c-167">Removes commands and resources from being included as tags.</span></span> <span data-ttu-id="4c80c-168">Hiermee slaat u automatisch tags toe aan een module.</span><span class="sxs-lookup"><span data-stu-id="4c80c-168">Skips automatically adding tags to a module.</span></span> <span data-ttu-id="4c80c-169">Ondersteuning voor **SkipAutomaticTags** -para meters is toegevoegd in de **PowerShellGet** -versie 2.0.0</span><span class="sxs-lookup"><span data-stu-id="4c80c-169">**SkipAutomaticTags** parameter support is added in **PowerShellGet** version 2.0.0</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-170">-Tags</span><span class="sxs-lookup"><span data-stu-id="4c80c-170">-Tags</span></span>

<span data-ttu-id="4c80c-171">Hiermee voegt u een of meer tags toe aan de module die u publiceert.</span><span class="sxs-lookup"><span data-stu-id="4c80c-171">Adds one or more tags to the module that you are publishing.</span></span> <span data-ttu-id="4c80c-172">Voor beelden van tags zijn DesiredStateConfiguration, DSC, DSCResourceKit of PSModule.</span><span class="sxs-lookup"><span data-stu-id="4c80c-172">Example tags include DesiredStateConfiguration, DSC, DSCResourceKit, or PSModule.</span></span> <span data-ttu-id="4c80c-173">Scheid meerdere labels met komma's.</span><span class="sxs-lookup"><span data-stu-id="4c80c-173">Separate multiple tags with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-174">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4c80c-174">-WhatIf</span></span>

<span data-ttu-id="4c80c-175">Laat zien wat er zou gebeuren als de `Publish-Module` uitvoeringen wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c80c-175">Shows what would happen if the `Publish-Module` runs.</span></span> <span data-ttu-id="4c80c-176">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c80c-176">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c80c-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4c80c-177">CommonParameters</span></span>

<span data-ttu-id="4c80c-178">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4c80c-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4c80c-179">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4c80c-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4c80c-180">INVOER</span><span class="sxs-lookup"><span data-stu-id="4c80c-180">INPUTS</span></span>

### <span data-ttu-id="4c80c-181">System. String</span><span class="sxs-lookup"><span data-stu-id="4c80c-181">System.String</span></span>

### <span data-ttu-id="4c80c-182">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="4c80c-182">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="4c80c-183">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4c80c-183">OUTPUTS</span></span>

### <span data-ttu-id="4c80c-184">System. object</span><span class="sxs-lookup"><span data-stu-id="4c80c-184">System.Object</span></span>

## <span data-ttu-id="4c80c-185">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4c80c-185">NOTES</span></span>

<span data-ttu-id="4c80c-186">`Publish-Module` wordt uitgevoerd op Power Shell 3,0 of latere versies van Power shell, op Windows 7 of Windows 2008 R2 en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="4c80c-186">`Publish-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4c80c-187">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="4c80c-187">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="4c80c-188">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="4c80c-188">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="4c80c-189">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="4c80c-189">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="4c80c-190">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4c80c-190">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="4c80c-191">Voor het publiceren van een module zijn meta gegevens vereist die worden weer gegeven op de galerie pagina voor de module.</span><span class="sxs-lookup"><span data-stu-id="4c80c-191">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="4c80c-192">De vereiste meta gegevens bevatten de module naam, versie, beschrijving en auteur.</span><span class="sxs-lookup"><span data-stu-id="4c80c-192">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="4c80c-193">De meeste meta gegevens worden opgehaald uit het module manifest, maar sommige meta gegevens kunnen worden opgegeven in `Publish-Module` para meters, zoals **tag**, **ReleaseNote**, **IconUri**, **ProjectUri** en **LicenseUri**.</span><span class="sxs-lookup"><span data-stu-id="4c80c-193">Most metadata is taken from the module manifest, but some metadata can be specified in `Publish-Module` parameters, such as **Tag**, **ReleaseNote**, **IconUri**, **ProjectUri**, and **LicenseUri**.</span></span> <span data-ttu-id="4c80c-194">Zie [pakket manifest waarden die van invloed zijn op de PowerShell Gallery-gebruikers interface](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4c80c-194">For more information, see [Package manifest values that impact the PowerShell Gallery UI](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span></span>

## <span data-ttu-id="4c80c-195">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4c80c-195">RELATED LINKS</span></span>

[<span data-ttu-id="4c80c-196">Find-Module</span><span class="sxs-lookup"><span data-stu-id="4c80c-196">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="4c80c-197">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="4c80c-197">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="4c80c-198">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="4c80c-198">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="4c80c-199">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="4c80c-199">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="4c80c-200">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="4c80c-200">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="4c80c-201">Update-Module</span><span class="sxs-lookup"><span data-stu-id="4c80c-201">Update-Module</span></span>](Update-Module.md)
