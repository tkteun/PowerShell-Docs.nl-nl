---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/set-packagesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PackageSource
ms.openlocfilehash: ad5384f7d708cc708991d4150bf883139007ae1b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250884"
---
# <span data-ttu-id="519ac-103">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="519ac-103">Set-PackageSource</span></span>

## <span data-ttu-id="519ac-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="519ac-104">SYNOPSIS</span></span>
<span data-ttu-id="519ac-105">Vervangt een pakket bron voor een opgegeven pakket provider.</span><span class="sxs-lookup"><span data-stu-id="519ac-105">Replaces a package source for a specified package provider.</span></span>

## <span data-ttu-id="519ac-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="519ac-106">SYNTAX</span></span>

### <span data-ttu-id="519ac-107">SourceBySearch (standaard)</span><span class="sxs-lookup"><span data-stu-id="519ac-107">SourceBySearch (Default)</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [[-Name] <String>] [-Location <String>] [-NewLocation <String>] [-NewName <String>] [-Trusted]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="519ac-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="519ac-108">SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] -InputObject <PackageSource> [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="519ac-109">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="519ac-109">NuGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="519ac-110">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="519ac-110">NuGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="519ac-111">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="519ac-111">PowerShellGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="519ac-112">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="519ac-112">PowerShellGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="519ac-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="519ac-113">DESCRIPTION</span></span>

<span data-ttu-id="519ac-114">De `Set-PackageSource` vervangt een pakket bron voor een opgegeven pakket provider.</span><span class="sxs-lookup"><span data-stu-id="519ac-114">The `Set-PackageSource` replaces a package source for a specified package provider.</span></span> <span data-ttu-id="519ac-115">Pakket bronnen worden altijd beheerd door een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="519ac-115">Package sources are always managed by a package provider.</span></span>

## <span data-ttu-id="519ac-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="519ac-116">EXAMPLES</span></span>

### <span data-ttu-id="519ac-117">Voor beeld 1: een pakket bron wijzigen</span><span class="sxs-lookup"><span data-stu-id="519ac-117">Example 1: Change a package source</span></span>

<span data-ttu-id="519ac-118">Met deze opdracht wordt de bestaande naam van een pakket bron gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="519ac-118">This command changes the existing name of a package source.</span></span> <span data-ttu-id="519ac-119">De bron is ingesteld op **vertrouwd** , waardoor prompts worden voor komen om de bron te controleren wanneer pakketten zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="519ac-119">The source is set to **Trusted** , which eliminates prompts to verify the source when packages are installed.</span></span>

```
PS C:\> Set-PackageSource -Name MyNuget -NewName NewNuGet -Trusted -ProviderName NuGet
```

## <span data-ttu-id="519ac-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="519ac-120">PARAMETERS</span></span>

### <span data-ttu-id="519ac-121">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="519ac-121">-ConfigFile</span></span>

<span data-ttu-id="519ac-122">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="519ac-122">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="519ac-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="519ac-123">-Credential</span></span>

<span data-ttu-id="519ac-124">Hiermee geeft u een gebruikers account op dat is gemachtigd om pakket providers te installeren.</span><span class="sxs-lookup"><span data-stu-id="519ac-124">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="519ac-125">-Force</span><span class="sxs-lookup"><span data-stu-id="519ac-125">-Force</span></span>

<span data-ttu-id="519ac-126">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="519ac-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="519ac-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="519ac-127">-ForceBootstrap</span></span>

<span data-ttu-id="519ac-128">Geeft aan `Set-PackageSource` dat **Package Management** automatisch de pakket provider installeert.</span><span class="sxs-lookup"><span data-stu-id="519ac-128">Indicates that `Set-PackageSource` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="519ac-129">-Input object</span><span class="sxs-lookup"><span data-stu-id="519ac-129">-InputObject</span></span>

<span data-ttu-id="519ac-130">Hiermee geeft u een pakket bron-ID-object op dat staat voor het pakket dat u wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="519ac-130">Specifies a package source ID object that represents the package that you want to change.</span></span> <span data-ttu-id="519ac-131">Pakket bron-Id's maken deel uit van de resultaten van de `Get-PackageSource` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="519ac-131">Package source IDs are part of the results of the `Get-PackageSource` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="519ac-132">-Locatie</span><span class="sxs-lookup"><span data-stu-id="519ac-132">-Location</span></span>

<span data-ttu-id="519ac-133">Hiermee geeft u de huidige pakket bron locatie.</span><span class="sxs-lookup"><span data-stu-id="519ac-133">Specifies the current package source location.</span></span> <span data-ttu-id="519ac-134">De waarde kan een URI, een bestandspad of een andere bestemmings indeling zijn die wordt ondersteund door de pakket provider.</span><span class="sxs-lookup"><span data-stu-id="519ac-134">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="519ac-135">-Name</span><span class="sxs-lookup"><span data-stu-id="519ac-135">-Name</span></span>

<span data-ttu-id="519ac-136">Hiermee geeft u de naam van de pakket bron.</span><span class="sxs-lookup"><span data-stu-id="519ac-136">Specifies a package source's name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: SourceName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="519ac-137">-NewLocation</span><span class="sxs-lookup"><span data-stu-id="519ac-137">-NewLocation</span></span>

<span data-ttu-id="519ac-138">Hiermee geeft u de nieuwe locatie voor een pakket bron op.</span><span class="sxs-lookup"><span data-stu-id="519ac-138">Specifies the new location for a package source.</span></span> <span data-ttu-id="519ac-139">De waarde kan een URI, een bestandspad of een andere bestemmings indeling zijn die wordt ondersteund door de pakket provider.</span><span class="sxs-lookup"><span data-stu-id="519ac-139">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="519ac-140">-NewName</span><span class="sxs-lookup"><span data-stu-id="519ac-140">-NewName</span></span>

<span data-ttu-id="519ac-141">Hiermee geeft u de nieuwe naam op die u toewijst aan een pakket bron.</span><span class="sxs-lookup"><span data-stu-id="519ac-141">Specifies the new name you assign to a package source.</span></span>

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

### <span data-ttu-id="519ac-142">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="519ac-142">-PackageManagementProvider</span></span>

<span data-ttu-id="519ac-143">Hiermee geeft u een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="519ac-143">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="519ac-144">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="519ac-144">-ProviderName</span></span>

<span data-ttu-id="519ac-145">Hiermee geeft u de naam van een provider.</span><span class="sxs-lookup"><span data-stu-id="519ac-145">Specifies a provider name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="519ac-146">-Proxy</span><span class="sxs-lookup"><span data-stu-id="519ac-146">-Proxy</span></span>

<span data-ttu-id="519ac-147">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="519ac-147">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="519ac-148">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="519ac-148">-ProxyCredential</span></span>

<span data-ttu-id="519ac-149">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="519ac-149">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="519ac-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="519ac-150">-PublishLocation</span></span>

<span data-ttu-id="519ac-151">Hiermee geeft u de publicatie locatie op.</span><span class="sxs-lookup"><span data-stu-id="519ac-151">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="519ac-152">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="519ac-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="519ac-153">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="519ac-153">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="519ac-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="519ac-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="519ac-155">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="519ac-155">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="519ac-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="519ac-156">-SkipValidate</span></span>

<span data-ttu-id="519ac-157">Switch waarmee de validatie van de referenties van een pakket bron wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="519ac-157">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="519ac-158">-Vertrouwd</span><span class="sxs-lookup"><span data-stu-id="519ac-158">-Trusted</span></span>

<span data-ttu-id="519ac-159">Geeft aan dat de bron een vertrouwde pakket provider is.</span><span class="sxs-lookup"><span data-stu-id="519ac-159">Indicates that the source is a trusted package provider.</span></span> <span data-ttu-id="519ac-160">Voor vertrouwde bronnen wordt niet om verificatie gevraagd om pakketten te installeren.</span><span class="sxs-lookup"><span data-stu-id="519ac-160">Trusted sources don't prompt for verification to install packages.</span></span>

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

### <span data-ttu-id="519ac-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="519ac-161">-Confirm</span></span>

<span data-ttu-id="519ac-162">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="519ac-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="519ac-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="519ac-163">-WhatIf</span></span>

<span data-ttu-id="519ac-164">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="519ac-164">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="519ac-165">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="519ac-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="519ac-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="519ac-166">CommonParameters</span></span>

<span data-ttu-id="519ac-167">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="519ac-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="519ac-168">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="519ac-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="519ac-169">INVOER</span><span class="sxs-lookup"><span data-stu-id="519ac-169">INPUTS</span></span>

### <span data-ttu-id="519ac-170">`Set-PackageSource` accepteert geen pijplijn invoer.</span><span class="sxs-lookup"><span data-stu-id="519ac-170">`Set-PackageSource` doesn't accept pipeline input.</span></span>

## <span data-ttu-id="519ac-171">UITVOER</span><span class="sxs-lookup"><span data-stu-id="519ac-171">OUTPUTS</span></span>

### <span data-ttu-id="519ac-172">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="519ac-172">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="519ac-173">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="519ac-173">NOTES</span></span>

## <span data-ttu-id="519ac-174">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="519ac-174">RELATED LINKS</span></span>

[<span data-ttu-id="519ac-175">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="519ac-175">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="519ac-176">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="519ac-176">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="519ac-177">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="519ac-177">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="519ac-178">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="519ac-178">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

