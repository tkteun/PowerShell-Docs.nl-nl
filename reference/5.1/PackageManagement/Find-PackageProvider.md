---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: dc4450e1c9f8b9506ee57948e4cec2d0541c181d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250284"
---
# <span data-ttu-id="2f33a-103">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="2f33a-103">Find-PackageProvider</span></span>

## <span data-ttu-id="2f33a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2f33a-104">SYNOPSIS</span></span>
<span data-ttu-id="2f33a-105">Retourneert een lijst met pakket beheer pakket providers die beschikbaar zijn voor installatie.</span><span class="sxs-lookup"><span data-stu-id="2f33a-105">Returns a list of Package Management package providers available for installation.</span></span>

## <span data-ttu-id="2f33a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2f33a-106">SYNTAX</span></span>

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="2f33a-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2f33a-107">DESCRIPTION</span></span>

<span data-ttu-id="2f33a-108">Met de cmdlet **find-package provider** vindt u overeenkomende Package Management-providers die beschikbaar zijn in pakket bronnen die zijn geregistreerd bij PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="2f33a-108">The **Find-PackageProvider** cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span>
<span data-ttu-id="2f33a-109">Dit zijn pakket providers die beschikbaar zijn voor installatie met de cmdlet Install-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="2f33a-109">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span>
<span data-ttu-id="2f33a-110">Dit omvat standaard modules die beschikbaar zijn in de PowerShell Gallery met de labels **Package Management** en **provider** .</span><span class="sxs-lookup"><span data-stu-id="2f33a-110">By default, this includes modules available in the PowerShell Gallery with the **PackageManagement** and **Provider** tags.</span></span>

<span data-ttu-id="2f33a-111">Met **find-package provider** vindt u ook overeenkomende pakket beheer providers die beschikbaar zijn in de Azure Blob Store van het pakket beheer.</span><span class="sxs-lookup"><span data-stu-id="2f33a-111">**Find-PackageProvider** also finds matching Package Management providers that are available in the Package Management Azure Blob store.</span></span>
<span data-ttu-id="2f33a-112">Gebruik de Boots Trapper-provider om ze te zoeken en te installeren.</span><span class="sxs-lookup"><span data-stu-id="2f33a-112">Use the bootstrapper provider to find and install them.</span></span>

## <span data-ttu-id="2f33a-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2f33a-113">EXAMPLES</span></span>

### <span data-ttu-id="2f33a-114">Voor beeld 1: alle beschik bare pakket providers zoeken</span><span class="sxs-lookup"><span data-stu-id="2f33a-114">Example 1: Find all available package providers</span></span>

```
PS C:\> Find-PackageProvider
```

<span data-ttu-id="2f33a-115">Met deze opdracht wordt een lijst van alle pakket providers opgehaald die beschikbaar zijn op de opslag plaatsen die worden ondersteund door Package Management.</span><span class="sxs-lookup"><span data-stu-id="2f33a-115">This command gets a list of all package providers that are available on the repositories supported by Package Management.</span></span>
<span data-ttu-id="2f33a-116">Deze pakket providers zijn standaard beschikbaar op het PowerShell Gallery en met behulp van de toepassing voor het Boots trappen van het pakket beheer.</span><span class="sxs-lookup"><span data-stu-id="2f33a-116">By default, those package providers are available on the PowerShell Gallery and by using the Package Management bootstrapping application.</span></span>

### <span data-ttu-id="2f33a-117">Voor beeld 2: alle versies van een provider zoeken</span><span class="sxs-lookup"><span data-stu-id="2f33a-117">Example 2: Find all versions of a provider</span></span>

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

<span data-ttu-id="2f33a-118">Met deze opdracht vindt u alle versies van de pakket provider met de naam Nuget.</span><span class="sxs-lookup"><span data-stu-id="2f33a-118">This command finds all versions of the package provider named Nuget.</span></span>

### <span data-ttu-id="2f33a-119">Voor beeld 3: een provider uit een opgegeven bron zoeken</span><span class="sxs-lookup"><span data-stu-id="2f33a-119">Example 3: Find a provider from a specified source</span></span>

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

<span data-ttu-id="2f33a-120">Met deze opdracht wordt een pakket provider gevonden die beschikbaar is via een opgegeven pakket bron.</span><span class="sxs-lookup"><span data-stu-id="2f33a-120">This command finds a package provider available by using a specified package source.</span></span>

## <span data-ttu-id="2f33a-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2f33a-121">PARAMETERS</span></span>

### <span data-ttu-id="2f33a-122">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="2f33a-122">-AllVersions</span></span>

<span data-ttu-id="2f33a-123">Geeft aan dat met deze cmdlet alle beschik bare versies van de pakket provider worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2f33a-123">Indicates that this cmdlet returns all available versions of the package provider.</span></span>
<span data-ttu-id="2f33a-124">**Zoek-package provider** retourneert standaard alleen de nieuwste beschik bare versie.</span><span class="sxs-lookup"><span data-stu-id="2f33a-124">By default, **Find-PackageProvider** only returns the newest available version.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f33a-125">-Credential</span><span class="sxs-lookup"><span data-stu-id="2f33a-125">-Credential</span></span>

<span data-ttu-id="2f33a-126">Hiermee geeft u een gebruikers account op dat is gemachtigd om te zoeken naar pakket providers.</span><span class="sxs-lookup"><span data-stu-id="2f33a-126">Specifies a user account that has permission to search for package providers.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f33a-127">-Force</span><span class="sxs-lookup"><span data-stu-id="2f33a-127">-Force</span></span>

<span data-ttu-id="2f33a-128">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="2f33a-128">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="2f33a-129">Op dit moment is dit gelijk aan de para meter *ForceBootstrap* .</span><span class="sxs-lookup"><span data-stu-id="2f33a-129">Currently, this is equivalent to the *ForceBootstrap* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f33a-130">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="2f33a-130">-ForceBootstrap</span></span>

<span data-ttu-id="2f33a-131">Geeft aan dat deze cmdlet pakket beheer afdwingt om de pakket provider automatisch te installeren.</span><span class="sxs-lookup"><span data-stu-id="2f33a-131">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f33a-132">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="2f33a-132">-IncludeDependencies</span></span>

<span data-ttu-id="2f33a-133">Geeft aan dat deze cmdlet afhankelijkheden bevat.</span><span class="sxs-lookup"><span data-stu-id="2f33a-133">Indicates that this cmdlet includes dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f33a-134">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="2f33a-134">-MaximumVersion</span></span>

<span data-ttu-id="2f33a-135">Hiermee geeft u de Maxi maal toegestane versie van de pakket provider die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="2f33a-135">Specifies the maximum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="2f33a-136">Als u deze para meter niet toevoegt, zoekt **package provider** de hoogste beschik bare versie van de provider.</span><span class="sxs-lookup"><span data-stu-id="2f33a-136">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider.</span></span>

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

### <span data-ttu-id="2f33a-137">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="2f33a-137">-MinimumVersion</span></span>

<span data-ttu-id="2f33a-138">Hiermee geeft u de mini maal toegestane versie van de pakket provider die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="2f33a-138">Specifies the minimum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="2f33a-139">Als u deze para meter niet toevoegt, zoekt **find-package provider** de hoogste beschik bare versie van het pakket dat ook voldoet aan de maximum opgegeven versie die is opgegeven door de para meter *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="2f33a-139">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the package that also satisfies any maximum specified version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="2f33a-140">-Name</span><span class="sxs-lookup"><span data-stu-id="2f33a-140">-Name</span></span>

<span data-ttu-id="2f33a-141">Hiermee geeft u een of meer module namen van pakket providers, of provider namen met Joker tekens.</span><span class="sxs-lookup"><span data-stu-id="2f33a-141">Specifies one or more package provider module names, or provider names with wildcard characters.</span></span>
<span data-ttu-id="2f33a-142">Scheid meerdere pakket namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="2f33a-142">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="2f33a-143">-Proxy</span><span class="sxs-lookup"><span data-stu-id="2f33a-143">-Proxy</span></span>

<span data-ttu-id="2f33a-144">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="2f33a-144">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="2f33a-145">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="2f33a-145">-ProxyCredential</span></span>

<span data-ttu-id="2f33a-146">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="2f33a-146">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f33a-147">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="2f33a-147">-RequiredVersion</span></span>

<span data-ttu-id="2f33a-148">Hiermee geeft u de exacte toegestane versie van de pakket provider die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="2f33a-148">Specifies the exact allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="2f33a-149">Als u deze para meter niet toevoegt, zoekt **find-package provider** de hoogste beschik bare versie van de provider die ook voldoet aan de maximum versie die is opgegeven door de para meter *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="2f33a-149">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="2f33a-150">-Source</span><span class="sxs-lookup"><span data-stu-id="2f33a-150">-Source</span></span>

<span data-ttu-id="2f33a-151">Hiermee geeft u een of meer pakket bronnen op.</span><span class="sxs-lookup"><span data-stu-id="2f33a-151">Specifies one or more package sources.</span></span>
<span data-ttu-id="2f33a-152">U kunt een lijst met beschik bare pakket bronnen ophalen met behulp van de cmdlet Get-PackageSource.</span><span class="sxs-lookup"><span data-stu-id="2f33a-152">You can get a list of available package sources by using the Get-PackageSource cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f33a-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f33a-153">CommonParameters</span></span>

<span data-ttu-id="2f33a-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2f33a-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2f33a-155">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f33a-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2f33a-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="2f33a-156">INPUTS</span></span>

## <span data-ttu-id="2f33a-157">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2f33a-157">OUTPUTS</span></span>

### <span data-ttu-id="2f33a-158">Micro soft. package management. verpakking. SoftwareIdentity</span><span class="sxs-lookup"><span data-stu-id="2f33a-158">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="2f33a-159">Met deze cmdlet wordt een **SoftwareIdentity** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2f33a-159">This cmdlet returns a **SoftwareIdentity** object.</span></span>
<span data-ttu-id="2f33a-160">Een **SoftwareIdentity** -object kan worden gepiped in **install-package provider** om de resultaten van **zoeken-package provider** te installeren.</span><span class="sxs-lookup"><span data-stu-id="2f33a-160">A **SoftwareIdentity** object can be piped into **Install-PackageProvider** to install the results of **Find-PackageProvider**.</span></span>

## <span data-ttu-id="2f33a-161">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2f33a-161">NOTES</span></span>

## <span data-ttu-id="2f33a-162">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2f33a-162">RELATED LINKS</span></span>

[<span data-ttu-id="2f33a-163">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="2f33a-163">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="2f33a-164">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2f33a-164">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="2f33a-165">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2f33a-165">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="2f33a-166">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2f33a-166">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="2f33a-167">Install-package provider</span><span class="sxs-lookup"><span data-stu-id="2f33a-167">Install-PackageProvider</span></span>](Install-PackageProvider.md)
