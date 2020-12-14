---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: 3ada5513343a5d6527cf1b091e1ee85e51f7f8de
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892246"
---
# <span data-ttu-id="2b0ee-103">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="2b0ee-103">Publish-Module</span></span>

## <span data-ttu-id="2b0ee-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2b0ee-104">SYNOPSIS</span></span>
<span data-ttu-id="2b0ee-105">Hiermee publiceert u een opgegeven module van de lokale computer naar een online galerie.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-105">Publishes a specified module from the local computer to an online gallery.</span></span>

## <span data-ttu-id="2b0ee-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2b0ee-106">SYNTAX</span></span>

### <span data-ttu-id="2b0ee-107">ModuleNameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="2b0ee-107">ModuleNameParameterSet (Default)</span></span>

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2b0ee-108">ModulePathParameterSet</span><span class="sxs-lookup"><span data-stu-id="2b0ee-108">ModulePathParameterSet</span></span>

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2b0ee-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2b0ee-109">DESCRIPTION</span></span>

<span data-ttu-id="2b0ee-110">De `Publish-Module` cmdlet publiceert een module naar een online NuGet-galerie met behulp van een API-sleutel, opgeslagen als onderdeel van een gebruikers profiel in de galerie.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-110">The `Publish-Module` cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="2b0ee-111">U kunt opgeven welke module moet worden gepubliceerd door de naam van de module of door het pad naar de map met de module.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-111">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="2b0ee-112">Wanneer u een module op naam opgeeft, wordt `Publish-Module` de eerste module gepubliceerd die zou worden gevonden door uit te voeren `Get-Module -ListAvailable <Name>` .</span><span class="sxs-lookup"><span data-stu-id="2b0ee-112">When you specify a module by name, `Publish-Module` publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="2b0ee-113">Als u een minimum versie van een module opgeeft om te publiceren, `Publish-Module` publiceert de eerste module met een versie die groter is dan of gelijk is aan de minimum versie die u hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-113">If you specify a minimum version of a module to publish, `Publish-Module` publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="2b0ee-114">Voor het publiceren van een module zijn meta gegevens vereist die worden weer gegeven op de galerie pagina voor de module.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-114">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="2b0ee-115">De vereiste meta gegevens bevatten de module naam, versie, beschrijving en auteur.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-115">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="2b0ee-116">Hoewel de meeste meta gegevens worden opgehaald uit het module manifest, moeten sommige meta gegevens worden opgegeven in `Publish-Module` para meters, zoals **tag**, **ReleaseNote**, **IconUri**, **ProjectUri** en **LicenseUri**, omdat deze para meters overeenkomen met velden in een op NuGet gebaseerde galerie.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-116">Although most metadata is taken from the module manifest, some metadata must be specified in `Publish-Module` parameters, such as **Tag**, **ReleaseNote**, **IconUri**, **ProjectUri**, and **LicenseUri**, because these parameters match fields in a NuGet-based gallery.</span></span>

## <span data-ttu-id="2b0ee-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2b0ee-117">EXAMPLES</span></span>

### <span data-ttu-id="2b0ee-118">Voor beeld 1: een module publiceren</span><span class="sxs-lookup"><span data-stu-id="2b0ee-118">Example 1: Publish a module</span></span>

<span data-ttu-id="2b0ee-119">In dit voor beeld wordt MyDscModule in de online galerie gepubliceerd met behulp van de API-sleutel om het online galerie account van de module eigenaar aan te geven.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-119">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's online gallery account.</span></span> <span data-ttu-id="2b0ee-120">Als MyDscModule geen geldige manifest module is die een naam, versie, beschrijving en auteur opgeeft, treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-120">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### <span data-ttu-id="2b0ee-121">Voor beeld 2: een module met de meta gegevens van de galerie publiceren</span><span class="sxs-lookup"><span data-stu-id="2b0ee-121">Example 2: Publish a module with gallery metadata</span></span>

<span data-ttu-id="2b0ee-122">In dit voor beeld wordt MyDscModule in de online galerie gepubliceerd met behulp van de API-sleutel om het Galerie account van de module eigenaar aan te geven.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-122">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's gallery account.</span></span> <span data-ttu-id="2b0ee-123">De aanvullende meta gegevens worden weer gegeven op de webpagina van de module in de galerie.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-123">The additional metadata provided is displayed on the webpage for the module in the gallery.</span></span> <span data-ttu-id="2b0ee-124">De eigenaar voegt twee zoek tags voor de module toe, met betrekking tot Active Directory. Er wordt een korte release opmerking toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-124">The owner adds two search tags for the module, relating it to Active Directory; a brief release note is added.</span></span> <span data-ttu-id="2b0ee-125">Als MyDscModule geen geldige manifest module is die een naam, versie, beschrijving en auteur opgeeft, treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-125">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## <span data-ttu-id="2b0ee-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2b0ee-126">PARAMETERS</span></span>

### <span data-ttu-id="2b0ee-127">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="2b0ee-127">-AllowPrerelease</span></span>

<span data-ttu-id="2b0ee-128">Hiermee kunnen modules die zijn gemarkeerd als Prerelease, worden gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-128">Allows modules marked as prerelease to be published.</span></span>

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

### <span data-ttu-id="2b0ee-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2b0ee-129">-Confirm</span></span>

<span data-ttu-id="2b0ee-130">Vraagt u om bevestiging voordat de wordt uitgevoerd `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="2b0ee-130">Prompts you for confirmation before running the `Publish-Module`.</span></span>

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

### <span data-ttu-id="2b0ee-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="2b0ee-131">-Credential</span></span>

<span data-ttu-id="2b0ee-132">Hiermee geeft u een gebruikers account op dat beschikt over rechten voor het publiceren van een module voor een opgegeven pakket provider of bron.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-132">Specifies a user account that has rights to publish a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="2b0ee-133">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="2b0ee-133">-Exclude</span></span>

<span data-ttu-id="2b0ee-134">Hiermee worden bestanden gedefinieerd die moeten worden uitgesloten van de gepubliceerde module.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-134">Defines files to exclude from the published module.</span></span>

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

### <span data-ttu-id="2b0ee-135">-Force</span><span class="sxs-lookup"><span data-stu-id="2b0ee-135">-Force</span></span>

<span data-ttu-id="2b0ee-136">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-136">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="2b0ee-137">-FormatVersion</span><span class="sxs-lookup"><span data-stu-id="2b0ee-137">-FormatVersion</span></span>

<span data-ttu-id="2b0ee-138">Accepteert alleen geldige waarden die zijn opgegeven met het kenmerk **Validate** .</span><span class="sxs-lookup"><span data-stu-id="2b0ee-138">Accepts only valid values specified by the **ValidateSet** attribute.</span></span>

<span data-ttu-id="2b0ee-139">Zie [Validate-kenmerk declaratie](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) en [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-139">For more information, see [ValidateSet Attribute Declaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) and [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span></span>

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

### <span data-ttu-id="2b0ee-140">-IconUri</span><span class="sxs-lookup"><span data-stu-id="2b0ee-140">-IconUri</span></span>

<span data-ttu-id="2b0ee-141">Hiermee geeft u de URL op van een pictogram voor de module.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-141">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="2b0ee-142">Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor de module.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-142">The specified icon is displayed on the gallery webpage for the module.</span></span>

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

### <span data-ttu-id="2b0ee-143">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="2b0ee-143">-LicenseUri</span></span>

<span data-ttu-id="2b0ee-144">Hiermee geeft u de URL op van de licentie voorwaarden voor de module die u wilt publiceren.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-144">Specifies the URL of licensing terms for the module you want to publish.</span></span>

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

### <span data-ttu-id="2b0ee-145">-Name</span><span class="sxs-lookup"><span data-stu-id="2b0ee-145">-Name</span></span>

<span data-ttu-id="2b0ee-146">Hiermee geeft u de naam van de module die u wilt publiceren.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-146">Specifies the name of the module that you want to publish.</span></span> <span data-ttu-id="2b0ee-147">`Publish-Module` zoekt naar de opgegeven module naam in `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="2b0ee-147">`Publish-Module` searches for the specified module name in `$Env:PSModulePath`.</span></span>

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

### <span data-ttu-id="2b0ee-148">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="2b0ee-148">-NuGetApiKey</span></span>

<span data-ttu-id="2b0ee-149">Hiermee geeft u de API-sleutel op die u wilt gebruiken voor het publiceren van een module naar de online galerie.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-149">Specifies the API key that you want to use to publish a module to the online gallery.</span></span> <span data-ttu-id="2b0ee-150">De API-sleutel maakt deel uit van uw profiel in de online galerie en is te vinden op de pagina met uw gebruikers account in de galerie.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-150">The API key is part of your profile in the online gallery, and can be found on your user account page in the gallery.</span></span> <span data-ttu-id="2b0ee-151">De API-sleutel is NuGet-specifieke functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-151">The API key is NuGet-specific functionality.</span></span>

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

### <span data-ttu-id="2b0ee-152">-Path</span><span class="sxs-lookup"><span data-stu-id="2b0ee-152">-Path</span></span>

<span data-ttu-id="2b0ee-153">Hiermee geeft u het pad op naar de module die u wilt publiceren.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-153">Specifies the path to the module that you want to publish.</span></span> <span data-ttu-id="2b0ee-154">Deze para meter accepteert het pad naar de map waarin de module zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-154">This parameter accepts the path to the folder that contains the module.</span></span>

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

### <span data-ttu-id="2b0ee-155">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="2b0ee-155">-ProjectUri</span></span>

<span data-ttu-id="2b0ee-156">Hiermee geeft u de URL van een webpagina over dit project op.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-156">Specifies the URL of a webpage about this project.</span></span>

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

### <span data-ttu-id="2b0ee-157">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="2b0ee-157">-ReleaseNotes</span></span>

<span data-ttu-id="2b0ee-158">Hiermee geeft u een teken reeks met release opmerkingen of opmerkingen die u beschikbaar wilt maken voor gebruikers van deze versie van de module.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-158">Specifies a string containing release notes or comments that you want to be available to users of this version of the module.</span></span>

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

### <span data-ttu-id="2b0ee-159">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="2b0ee-159">-Repository</span></span>

<span data-ttu-id="2b0ee-160">Hiermee geeft u de beschrijvende naam op van een opslag plaats die is geregistreerd door te worden uitgevoerd `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="2b0ee-160">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="2b0ee-161">De opslag plaats moet een **PublishLocation** hebben. Dit is een geldige NUGET-URI.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-161">The repository must have a **PublishLocation**, which is a valid NuGet URI.</span></span>
<span data-ttu-id="2b0ee-162">De **PublishLocation** kan worden ingesteld door te worden uitgevoerd `Set-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="2b0ee-162">The **PublishLocation** can be set by running `Set-PSRepository`.</span></span>

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

### <span data-ttu-id="2b0ee-163">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="2b0ee-163">-RequiredVersion</span></span>

<span data-ttu-id="2b0ee-164">Hiermee geeft u de exacte versie van één module op die moet worden gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-164">Specifies the exact version of a single module to publish.</span></span>

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

### <span data-ttu-id="2b0ee-165">-SkipAutomaticTags</span><span class="sxs-lookup"><span data-stu-id="2b0ee-165">-SkipAutomaticTags</span></span>

<span data-ttu-id="2b0ee-166">Hiermee verwijdert u opdrachten en resources uit de tags die u wilt opnemen.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-166">Removes commands and resources from being included as tags.</span></span> <span data-ttu-id="2b0ee-167">Hiermee slaat u automatisch tags toe aan een module.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-167">Skips automatically adding tags to a module.</span></span>

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

### <span data-ttu-id="2b0ee-168">-Tags</span><span class="sxs-lookup"><span data-stu-id="2b0ee-168">-Tags</span></span>

<span data-ttu-id="2b0ee-169">Hiermee voegt u een of meer tags toe aan de module die u publiceert.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-169">Adds one or more tags to the module that you are publishing.</span></span> <span data-ttu-id="2b0ee-170">Voor beelden van tags zijn DesiredStateConfiguration, DSC, DSCResourceKit of PSModule.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-170">Example tags include DesiredStateConfiguration, DSC, DSCResourceKit, or PSModule.</span></span> <span data-ttu-id="2b0ee-171">Scheid meerdere labels met komma's.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-171">Separate multiple tags with commas.</span></span>

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

### <span data-ttu-id="2b0ee-172">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2b0ee-172">-WhatIf</span></span>

<span data-ttu-id="2b0ee-173">Laat zien wat er zou gebeuren als de `Publish-Module` uitvoeringen wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-173">Shows what would happen if the `Publish-Module` runs.</span></span> <span data-ttu-id="2b0ee-174">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-174">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2b0ee-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2b0ee-175">CommonParameters</span></span>

<span data-ttu-id="2b0ee-176">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2b0ee-177">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2b0ee-178">INVOER</span><span class="sxs-lookup"><span data-stu-id="2b0ee-178">INPUTS</span></span>

### <span data-ttu-id="2b0ee-179">System. String</span><span class="sxs-lookup"><span data-stu-id="2b0ee-179">System.String</span></span>

### <span data-ttu-id="2b0ee-180">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="2b0ee-180">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="2b0ee-181">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2b0ee-181">OUTPUTS</span></span>

### <span data-ttu-id="2b0ee-182">System. object</span><span class="sxs-lookup"><span data-stu-id="2b0ee-182">System.Object</span></span>

## <span data-ttu-id="2b0ee-183">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2b0ee-183">NOTES</span></span>

<span data-ttu-id="2b0ee-184">`Publish-Module` wordt uitgevoerd op Power Shell 3,0 of latere versies van Power shell, op Windows 7 of Windows 2008 R2 en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-184">`Publish-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b0ee-185">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-185">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="2b0ee-186">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-186">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="2b0ee-187">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="2b0ee-187">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="2b0ee-188">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-188">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="2b0ee-189">Voor het publiceren van een module zijn meta gegevens vereist die worden weer gegeven op de galerie pagina voor de module.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-189">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="2b0ee-190">De vereiste meta gegevens bevatten de module naam, versie, beschrijving en auteur.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-190">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="2b0ee-191">De meeste meta gegevens worden opgehaald uit het module manifest, maar sommige meta gegevens kunnen worden opgegeven in `Publish-Module` para meters, zoals **tag**, **ReleaseNote**, **IconUri**, **ProjectUri** en **LicenseUri**.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-191">Most metadata is taken from the module manifest, but some metadata can be specified in `Publish-Module` parameters, such as **Tag**, **ReleaseNote**, **IconUri**, **ProjectUri**, and **LicenseUri**.</span></span> <span data-ttu-id="2b0ee-192">Zie [pakket manifest waarden die van invloed zijn op de PowerShell Gallery-gebruikers interface](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2b0ee-192">For more information, see [Package manifest values that impact the PowerShell Gallery UI](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span></span>

## <span data-ttu-id="2b0ee-193">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2b0ee-193">RELATED LINKS</span></span>

[<span data-ttu-id="2b0ee-194">Find-Module</span><span class="sxs-lookup"><span data-stu-id="2b0ee-194">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="2b0ee-195">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="2b0ee-195">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="2b0ee-196">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="2b0ee-196">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="2b0ee-197">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="2b0ee-197">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="2b0ee-198">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="2b0ee-198">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="2b0ee-199">Update-Module</span><span class="sxs-lookup"><span data-stu-id="2b0ee-199">Update-Module</span></span>](Update-Module.md)
