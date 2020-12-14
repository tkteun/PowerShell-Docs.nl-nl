---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/set-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PackageSource
ms.openlocfilehash: 9f258c3b02064aafdaf272141f2613ff5cbaf5b5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889279"
---
# <span data-ttu-id="36fbb-102">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="36fbb-102">Set-PackageSource</span></span>

## <span data-ttu-id="36fbb-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="36fbb-103">SYNOPSIS</span></span>
<span data-ttu-id="36fbb-104">Vervangt een pakket bron voor een opgegeven pakket provider.</span><span class="sxs-lookup"><span data-stu-id="36fbb-104">Replaces a package source for a specified package provider.</span></span>

## <span data-ttu-id="36fbb-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="36fbb-105">SYNTAX</span></span>

### <span data-ttu-id="36fbb-106">SourceBySearch (standaard)</span><span class="sxs-lookup"><span data-stu-id="36fbb-106">SourceBySearch (Default)</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [[-Name] <String>] [-Location <String>] [-NewLocation <String>] [-NewName <String>] [-Trusted]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="36fbb-107">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="36fbb-107">SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] -InputObject <PackageSource> [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="36fbb-108">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="36fbb-108">NuGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="36fbb-109">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="36fbb-109">NuGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="36fbb-110">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="36fbb-110">PowerShellGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="36fbb-111">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="36fbb-111">PowerShellGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="36fbb-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="36fbb-112">DESCRIPTION</span></span>

<span data-ttu-id="36fbb-113">De `Set-PackageSource` vervangt een pakket bron voor een opgegeven pakket provider.</span><span class="sxs-lookup"><span data-stu-id="36fbb-113">The `Set-PackageSource` replaces a package source for a specified package provider.</span></span> <span data-ttu-id="36fbb-114">Pakket bronnen worden altijd beheerd door een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="36fbb-114">Package sources are always managed by a package provider.</span></span>

## <span data-ttu-id="36fbb-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="36fbb-115">EXAMPLES</span></span>

### <span data-ttu-id="36fbb-116">Voor beeld 1: een pakket bron wijzigen</span><span class="sxs-lookup"><span data-stu-id="36fbb-116">Example 1: Change a package source</span></span>

<span data-ttu-id="36fbb-117">Met deze opdracht wordt de bestaande naam van een pakket bron gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="36fbb-117">This command changes the existing name of a package source.</span></span> <span data-ttu-id="36fbb-118">De bron is ingesteld op **vertrouwd**, waardoor prompts worden voor komen om de bron te controleren wanneer pakketten zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="36fbb-118">The source is set to **Trusted**, which eliminates prompts to verify the source when packages are installed.</span></span>

```
PS C:\> Set-PackageSource -Name MyNuget -NewName NewNuGet -Trusted -ProviderName NuGet
```

## <span data-ttu-id="36fbb-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36fbb-119">PARAMETERS</span></span>

### <span data-ttu-id="36fbb-120">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="36fbb-120">-ConfigFile</span></span>

<span data-ttu-id="36fbb-121">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="36fbb-121">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="36fbb-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="36fbb-122">-Credential</span></span>

<span data-ttu-id="36fbb-123">Hiermee geeft u een gebruikers account op dat is gemachtigd om pakket providers te installeren.</span><span class="sxs-lookup"><span data-stu-id="36fbb-123">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="36fbb-124">-Force</span><span class="sxs-lookup"><span data-stu-id="36fbb-124">-Force</span></span>

<span data-ttu-id="36fbb-125">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="36fbb-125">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="36fbb-126">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="36fbb-126">-ForceBootstrap</span></span>

<span data-ttu-id="36fbb-127">Geeft aan `Set-PackageSource` dat **Package Management** automatisch de pakket provider installeert.</span><span class="sxs-lookup"><span data-stu-id="36fbb-127">Indicates that `Set-PackageSource` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="36fbb-128">-Input object</span><span class="sxs-lookup"><span data-stu-id="36fbb-128">-InputObject</span></span>

<span data-ttu-id="36fbb-129">Hiermee geeft u een pakket bron-ID-object op dat staat voor het pakket dat u wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="36fbb-129">Specifies a package source ID object that represents the package that you want to change.</span></span> <span data-ttu-id="36fbb-130">Pakket bron-Id's maken deel uit van de resultaten van de `Get-PackageSource` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36fbb-130">Package source IDs are part of the results of the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="36fbb-131">-Locatie</span><span class="sxs-lookup"><span data-stu-id="36fbb-131">-Location</span></span>

<span data-ttu-id="36fbb-132">Hiermee geeft u de huidige pakket bron locatie.</span><span class="sxs-lookup"><span data-stu-id="36fbb-132">Specifies the current package source location.</span></span> <span data-ttu-id="36fbb-133">De waarde kan een URI, een bestandspad of een andere bestemmings indeling zijn die wordt ondersteund door de pakket provider.</span><span class="sxs-lookup"><span data-stu-id="36fbb-133">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="36fbb-134">-Name</span><span class="sxs-lookup"><span data-stu-id="36fbb-134">-Name</span></span>

<span data-ttu-id="36fbb-135">Hiermee geeft u de naam van de pakket bron.</span><span class="sxs-lookup"><span data-stu-id="36fbb-135">Specifies a package source's name.</span></span>

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

### <span data-ttu-id="36fbb-136">-NewLocation</span><span class="sxs-lookup"><span data-stu-id="36fbb-136">-NewLocation</span></span>

<span data-ttu-id="36fbb-137">Hiermee geeft u de nieuwe locatie voor een pakket bron op.</span><span class="sxs-lookup"><span data-stu-id="36fbb-137">Specifies the new location for a package source.</span></span> <span data-ttu-id="36fbb-138">De waarde kan een URI, een bestandspad of een andere bestemmings indeling zijn die wordt ondersteund door de pakket provider.</span><span class="sxs-lookup"><span data-stu-id="36fbb-138">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="36fbb-139">-NewName</span><span class="sxs-lookup"><span data-stu-id="36fbb-139">-NewName</span></span>

<span data-ttu-id="36fbb-140">Hiermee geeft u de nieuwe naam op die u toewijst aan een pakket bron.</span><span class="sxs-lookup"><span data-stu-id="36fbb-140">Specifies the new name you assign to a package source.</span></span>

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

### <span data-ttu-id="36fbb-141">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="36fbb-141">-PackageManagementProvider</span></span>

<span data-ttu-id="36fbb-142">Hiermee geeft u een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="36fbb-142">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="36fbb-143">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="36fbb-143">-ProviderName</span></span>

<span data-ttu-id="36fbb-144">Hiermee geeft u de naam van een provider.</span><span class="sxs-lookup"><span data-stu-id="36fbb-144">Specifies a provider name.</span></span>

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

### <span data-ttu-id="36fbb-145">-Proxy</span><span class="sxs-lookup"><span data-stu-id="36fbb-145">-Proxy</span></span>

<span data-ttu-id="36fbb-146">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="36fbb-146">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="36fbb-147">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="36fbb-147">-ProxyCredential</span></span>

<span data-ttu-id="36fbb-148">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="36fbb-148">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="36fbb-149">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="36fbb-149">-PublishLocation</span></span>

<span data-ttu-id="36fbb-150">Hiermee geeft u de publicatie locatie op.</span><span class="sxs-lookup"><span data-stu-id="36fbb-150">Specifies the publish location.</span></span>

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

### <span data-ttu-id="36fbb-151">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="36fbb-151">-ScriptPublishLocation</span></span>

<span data-ttu-id="36fbb-152">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="36fbb-152">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="36fbb-153">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="36fbb-153">-ScriptSourceLocation</span></span>

<span data-ttu-id="36fbb-154">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="36fbb-154">Specifies the script source location.</span></span>

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

### <span data-ttu-id="36fbb-155">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="36fbb-155">-SkipValidate</span></span>

<span data-ttu-id="36fbb-156">Switch waarmee de validatie van de referenties van een pakket bron wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="36fbb-156">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="36fbb-157">-Vertrouwd</span><span class="sxs-lookup"><span data-stu-id="36fbb-157">-Trusted</span></span>

<span data-ttu-id="36fbb-158">Geeft aan dat de bron een vertrouwde pakket provider is.</span><span class="sxs-lookup"><span data-stu-id="36fbb-158">Indicates that the source is a trusted package provider.</span></span> <span data-ttu-id="36fbb-159">Voor vertrouwde bronnen wordt niet om verificatie gevraagd om pakketten te installeren.</span><span class="sxs-lookup"><span data-stu-id="36fbb-159">Trusted sources don't prompt for verification to install packages.</span></span>

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

### <span data-ttu-id="36fbb-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="36fbb-160">-Confirm</span></span>

<span data-ttu-id="36fbb-161">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="36fbb-161">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="36fbb-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="36fbb-162">-WhatIf</span></span>

<span data-ttu-id="36fbb-163">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="36fbb-163">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="36fbb-164">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="36fbb-164">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="36fbb-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36fbb-165">CommonParameters</span></span>

<span data-ttu-id="36fbb-166">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36fbb-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36fbb-167">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36fbb-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36fbb-168">INVOER</span><span class="sxs-lookup"><span data-stu-id="36fbb-168">INPUTS</span></span>

### <span data-ttu-id="36fbb-169">`Set-PackageSource` accepteert geen pijplijn invoer.</span><span class="sxs-lookup"><span data-stu-id="36fbb-169">`Set-PackageSource` doesn't accept pipeline input.</span></span>

## <span data-ttu-id="36fbb-170">UITVOER</span><span class="sxs-lookup"><span data-stu-id="36fbb-170">OUTPUTS</span></span>

### <span data-ttu-id="36fbb-171">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="36fbb-171">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="36fbb-172">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="36fbb-172">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36fbb-173">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="36fbb-173">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="36fbb-174">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="36fbb-174">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="36fbb-175">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="36fbb-175">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="36fbb-176">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36fbb-176">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="36fbb-177">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="36fbb-177">RELATED LINKS</span></span>

[<span data-ttu-id="36fbb-178">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="36fbb-178">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="36fbb-179">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="36fbb-179">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="36fbb-180">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="36fbb-180">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="36fbb-181">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="36fbb-181">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
