---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/set-packagesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PackageSource
ms.openlocfilehash: 4d534ebf97f7d7f37115e23f12cbd4d725e2212b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889950"
---
# <span data-ttu-id="0dcb9-103">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0dcb9-103">Set-PackageSource</span></span>

## <span data-ttu-id="0dcb9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0dcb9-104">SYNOPSIS</span></span>
<span data-ttu-id="0dcb9-105">Vervangt een pakket bron voor een opgegeven pakket provider.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-105">Replaces a package source for a specified package provider.</span></span>

## <span data-ttu-id="0dcb9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0dcb9-106">SYNTAX</span></span>

### <span data-ttu-id="0dcb9-107">SourceBySearch (standaard)</span><span class="sxs-lookup"><span data-stu-id="0dcb9-107">SourceBySearch (Default)</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [[-Name] <String>] [-Location <String>] [-NewLocation <String>] [-NewName <String>] [-Trusted]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="0dcb9-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="0dcb9-108">SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] -InputObject <PackageSource> [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0dcb9-109">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="0dcb9-109">NuGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="0dcb9-110">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="0dcb9-110">NuGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="0dcb9-111">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="0dcb9-111">PowerShellGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="0dcb9-112">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="0dcb9-112">PowerShellGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="0dcb9-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0dcb9-113">DESCRIPTION</span></span>

<span data-ttu-id="0dcb9-114">De `Set-PackageSource` vervangt een pakket bron voor een opgegeven pakket provider.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-114">The `Set-PackageSource` replaces a package source for a specified package provider.</span></span> <span data-ttu-id="0dcb9-115">Pakket bronnen worden altijd beheerd door een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-115">Package sources are always managed by a package provider.</span></span>

## <span data-ttu-id="0dcb9-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0dcb9-116">EXAMPLES</span></span>

### <span data-ttu-id="0dcb9-117">Voor beeld 1: een pakket bron wijzigen</span><span class="sxs-lookup"><span data-stu-id="0dcb9-117">Example 1: Change a package source</span></span>

<span data-ttu-id="0dcb9-118">Met deze opdracht wordt de bestaande naam van een pakket bron gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-118">This command changes the existing name of a package source.</span></span> <span data-ttu-id="0dcb9-119">De bron is ingesteld op **vertrouwd**, waardoor prompts worden voor komen om de bron te controleren wanneer pakketten zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-119">The source is set to **Trusted**, which eliminates prompts to verify the source when packages are installed.</span></span>

```
PS C:\> Set-PackageSource -Name MyNuget -NewName NewNuGet -Trusted -ProviderName NuGet
```

## <span data-ttu-id="0dcb9-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0dcb9-120">PARAMETERS</span></span>

### <span data-ttu-id="0dcb9-121">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="0dcb9-121">-ConfigFile</span></span>

<span data-ttu-id="0dcb9-122">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-122">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="0dcb9-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="0dcb9-123">-Credential</span></span>

<span data-ttu-id="0dcb9-124">Hiermee geeft u een gebruikers account op dat is gemachtigd om pakket providers te installeren.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-124">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="0dcb9-125">-Force</span><span class="sxs-lookup"><span data-stu-id="0dcb9-125">-Force</span></span>

<span data-ttu-id="0dcb9-126">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0dcb9-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="0dcb9-127">-ForceBootstrap</span></span>

<span data-ttu-id="0dcb9-128">Geeft aan `Set-PackageSource` dat **Package Management** automatisch de pakket provider installeert.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-128">Indicates that `Set-PackageSource` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="0dcb9-129">-Input object</span><span class="sxs-lookup"><span data-stu-id="0dcb9-129">-InputObject</span></span>

<span data-ttu-id="0dcb9-130">Hiermee geeft u een pakket bron-ID-object op dat staat voor het pakket dat u wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-130">Specifies a package source ID object that represents the package that you want to change.</span></span> <span data-ttu-id="0dcb9-131">Pakket bron-Id's maken deel uit van de resultaten van de `Get-PackageSource` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-131">Package source IDs are part of the results of the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="0dcb9-132">-Locatie</span><span class="sxs-lookup"><span data-stu-id="0dcb9-132">-Location</span></span>

<span data-ttu-id="0dcb9-133">Hiermee geeft u de huidige pakket bron locatie.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-133">Specifies the current package source location.</span></span> <span data-ttu-id="0dcb9-134">De waarde kan een URI, een bestandspad of een andere bestemmings indeling zijn die wordt ondersteund door de pakket provider.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-134">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="0dcb9-135">-Name</span><span class="sxs-lookup"><span data-stu-id="0dcb9-135">-Name</span></span>

<span data-ttu-id="0dcb9-136">Hiermee geeft u de naam van de pakket bron.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-136">Specifies a package source's name.</span></span>

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

### <span data-ttu-id="0dcb9-137">-NewLocation</span><span class="sxs-lookup"><span data-stu-id="0dcb9-137">-NewLocation</span></span>

<span data-ttu-id="0dcb9-138">Hiermee geeft u de nieuwe locatie voor een pakket bron op.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-138">Specifies the new location for a package source.</span></span> <span data-ttu-id="0dcb9-139">De waarde kan een URI, een bestandspad of een andere bestemmings indeling zijn die wordt ondersteund door de pakket provider.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-139">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="0dcb9-140">-NewName</span><span class="sxs-lookup"><span data-stu-id="0dcb9-140">-NewName</span></span>

<span data-ttu-id="0dcb9-141">Hiermee geeft u de nieuwe naam op die u toewijst aan een pakket bron.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-141">Specifies the new name you assign to a package source.</span></span>

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

### <span data-ttu-id="0dcb9-142">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="0dcb9-142">-PackageManagementProvider</span></span>

<span data-ttu-id="0dcb9-143">Hiermee geeft u een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-143">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="0dcb9-144">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="0dcb9-144">-ProviderName</span></span>

<span data-ttu-id="0dcb9-145">Hiermee geeft u de naam van een provider.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-145">Specifies a provider name.</span></span>

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

### <span data-ttu-id="0dcb9-146">-Proxy</span><span class="sxs-lookup"><span data-stu-id="0dcb9-146">-Proxy</span></span>

<span data-ttu-id="0dcb9-147">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-147">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="0dcb9-148">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="0dcb9-148">-ProxyCredential</span></span>

<span data-ttu-id="0dcb9-149">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="0dcb9-149">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="0dcb9-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="0dcb9-150">-PublishLocation</span></span>

<span data-ttu-id="0dcb9-151">Hiermee geeft u de publicatie locatie op.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-151">Specifies the publish location.</span></span>

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

### <span data-ttu-id="0dcb9-152">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="0dcb9-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="0dcb9-153">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-153">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="0dcb9-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="0dcb9-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="0dcb9-155">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-155">Specifies the script source location.</span></span>

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

### <span data-ttu-id="0dcb9-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="0dcb9-156">-SkipValidate</span></span>

<span data-ttu-id="0dcb9-157">Switch waarmee de validatie van de referenties van een pakket bron wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-157">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="0dcb9-158">-Vertrouwd</span><span class="sxs-lookup"><span data-stu-id="0dcb9-158">-Trusted</span></span>

<span data-ttu-id="0dcb9-159">Geeft aan dat de bron een vertrouwde pakket provider is.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-159">Indicates that the source is a trusted package provider.</span></span> <span data-ttu-id="0dcb9-160">Voor vertrouwde bronnen wordt niet om verificatie gevraagd om pakketten te installeren.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-160">Trusted sources don't prompt for verification to install packages.</span></span>

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

### <span data-ttu-id="0dcb9-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0dcb9-161">-Confirm</span></span>

<span data-ttu-id="0dcb9-162">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0dcb9-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0dcb9-163">-WhatIf</span></span>

<span data-ttu-id="0dcb9-164">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-164">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0dcb9-165">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0dcb9-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0dcb9-166">CommonParameters</span></span>

<span data-ttu-id="0dcb9-167">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0dcb9-168">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0dcb9-169">INVOER</span><span class="sxs-lookup"><span data-stu-id="0dcb9-169">INPUTS</span></span>

### <span data-ttu-id="0dcb9-170">`Set-PackageSource` accepteert geen pijplijn invoer.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-170">`Set-PackageSource` doesn't accept pipeline input.</span></span>

## <span data-ttu-id="0dcb9-171">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0dcb9-171">OUTPUTS</span></span>

### <span data-ttu-id="0dcb9-172">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-172">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0dcb9-173">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0dcb9-173">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0dcb9-174">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-174">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="0dcb9-175">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-175">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="0dcb9-176">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="0dcb9-176">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="0dcb9-177">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0dcb9-177">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="0dcb9-178">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0dcb9-178">RELATED LINKS</span></span>

[<span data-ttu-id="0dcb9-179">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="0dcb9-179">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="0dcb9-180">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0dcb9-180">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="0dcb9-181">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0dcb9-181">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="0dcb9-182">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0dcb9-182">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
