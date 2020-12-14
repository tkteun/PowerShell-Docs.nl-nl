---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/register-packagesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PackageSource
ms.openlocfilehash: dfaccf285b8a53c1701919016509fd49eeee5da7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891046"
---
# <span data-ttu-id="72f04-103">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="72f04-103">Register-PackageSource</span></span>

## <span data-ttu-id="72f04-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="72f04-104">SYNOPSIS</span></span>
<span data-ttu-id="72f04-105">Hiermee voegt u een pakket bron voor een opgegeven pakket provider toe.</span><span class="sxs-lookup"><span data-stu-id="72f04-105">Adds a package source for a specified package provider.</span></span>

## <span data-ttu-id="72f04-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="72f04-106">SYNTAX</span></span>

### <span data-ttu-id="72f04-107">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="72f04-107">SourceBySearch</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="72f04-108">NuGet</span><span class="sxs-lookup"><span data-stu-id="72f04-108">NuGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="72f04-109">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="72f04-109">PowerShellGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="72f04-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="72f04-110">DESCRIPTION</span></span>

<span data-ttu-id="72f04-111">De `Register-PackageSource` cmdlet voegt een pakket bron voor een opgegeven pakket provider toe.</span><span class="sxs-lookup"><span data-stu-id="72f04-111">The `Register-PackageSource` cmdlet adds a package source for a specified package provider.</span></span> <span data-ttu-id="72f04-112">Pakket bronnen worden altijd beheerd door een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="72f04-112">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="72f04-113">Als de pakket provider een pakket bron niet kan toevoegen of vervangen, genereert de provider een fout bericht.</span><span class="sxs-lookup"><span data-stu-id="72f04-113">If the package provider cannot add or replace a package source, the provider generates an error message.</span></span>

## <span data-ttu-id="72f04-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="72f04-114">EXAMPLES</span></span>

### <span data-ttu-id="72f04-115">Voor beeld 1: een pakket bron registreren voor de NuGet-provider</span><span class="sxs-lookup"><span data-stu-id="72f04-115">Example 1: Register a package source for the NuGet provider</span></span>

<span data-ttu-id="72f04-116">Met deze opdracht wordt een pakket bron, een weblocatie voor de **NuGet** -provider geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="72f04-116">This command registers a package source, a web-based location for the **NuGet** provider.</span></span> <span data-ttu-id="72f04-117">Standaard worden bronnen niet vertrouwd.</span><span class="sxs-lookup"><span data-stu-id="72f04-117">By default, sources aren't trusted.</span></span> <span data-ttu-id="72f04-118">U wordt gevraagd om te bevestigen dat de bron wordt vertrouwd voordat pakketten zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="72f04-118">You are prompted to confirm the source is trusted before packages are installed.</span></span> <span data-ttu-id="72f04-119">Als u de standaard waarde wilt overschrijven, gebruikt u de `-Trusted` para meter.</span><span class="sxs-lookup"><span data-stu-id="72f04-119">To override the default, use the `-Trusted` parameter.</span></span>

```powershell
Register-PackageSource -Name MyNuGet -Location https://www.nuget.org/api/v2 -ProviderName NuGet
```

```Output
Name          ProviderName     IsTrusted  Location
----          ------------     ---------  --------
MyNuGet       NuGet            False      https://www.nuget.org/api/v2
```

## <span data-ttu-id="72f04-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="72f04-120">PARAMETERS</span></span>

### <span data-ttu-id="72f04-121">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="72f04-121">-ConfigFile</span></span>

<span data-ttu-id="72f04-122">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="72f04-122">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72f04-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="72f04-123">-Credential</span></span>

<span data-ttu-id="72f04-124">Hiermee geeft u een gebruikers account op dat gemachtigd is om toegang te krijgen tot de geauthenticeerde locatie.</span><span class="sxs-lookup"><span data-stu-id="72f04-124">Specifies a user account that has permission to access the authenticated location.</span></span>

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

### <span data-ttu-id="72f04-125">-Force</span><span class="sxs-lookup"><span data-stu-id="72f04-125">-Force</span></span>

<span data-ttu-id="72f04-126">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="72f04-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="72f04-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="72f04-127">-ForceBootstrap</span></span>

<span data-ttu-id="72f04-128">Geeft aan dat met deze cmdlet automatisch de pakket provider wordt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="72f04-128">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="72f04-129">-Locatie</span><span class="sxs-lookup"><span data-stu-id="72f04-129">-Location</span></span>

<span data-ttu-id="72f04-130">Hiermee geeft u de bron locatie van het pakket op.</span><span class="sxs-lookup"><span data-stu-id="72f04-130">Specifies the package source location.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72f04-131">-Name</span><span class="sxs-lookup"><span data-stu-id="72f04-131">-Name</span></span>

<span data-ttu-id="72f04-132">Hiermee geeft u de naam op van de pakket bron die u wilt registreren.</span><span class="sxs-lookup"><span data-stu-id="72f04-132">Specifies the name of the package source to register.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72f04-133">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="72f04-133">-PackageManagementProvider</span></span>

<span data-ttu-id="72f04-134">Hiermee geeft u de pakket beheer provider op.</span><span class="sxs-lookup"><span data-stu-id="72f04-134">Specifies the Package Management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72f04-135">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="72f04-135">-ProviderName</span></span>

<span data-ttu-id="72f04-136">Hiermee geeft u de naam van de pakket provider op.</span><span class="sxs-lookup"><span data-stu-id="72f04-136">Specifies the package provider's name.</span></span>

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

### <span data-ttu-id="72f04-137">-Proxy</span><span class="sxs-lookup"><span data-stu-id="72f04-137">-Proxy</span></span>

<span data-ttu-id="72f04-138">Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="72f04-138">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="72f04-139">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="72f04-139">-ProxyCredential</span></span>

<span data-ttu-id="72f04-140">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="72f04-140">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="72f04-141">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="72f04-141">-PublishLocation</span></span>

<span data-ttu-id="72f04-142">Hiermee geeft u de publicatie locatie op.</span><span class="sxs-lookup"><span data-stu-id="72f04-142">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72f04-143">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="72f04-143">-ScriptPublishLocation</span></span>

<span data-ttu-id="72f04-144">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="72f04-144">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72f04-145">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="72f04-145">-ScriptSourceLocation</span></span>

<span data-ttu-id="72f04-146">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="72f04-146">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72f04-147">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="72f04-147">-SkipValidate</span></span>

<span data-ttu-id="72f04-148">Switch waarmee de validatie van de referenties van een pakket bron wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="72f04-148">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72f04-149">-Vertrouwd</span><span class="sxs-lookup"><span data-stu-id="72f04-149">-Trusted</span></span>

<span data-ttu-id="72f04-150">Geeft aan dat de pakket bron wordt vertrouwd.</span><span class="sxs-lookup"><span data-stu-id="72f04-150">Indicates that the package source is trusted.</span></span>

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

### <span data-ttu-id="72f04-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="72f04-151">-Confirm</span></span>

<span data-ttu-id="72f04-152">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="72f04-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="72f04-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="72f04-153">-WhatIf</span></span>

<span data-ttu-id="72f04-154">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="72f04-154">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="72f04-155">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="72f04-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="72f04-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="72f04-156">CommonParameters</span></span>

<span data-ttu-id="72f04-157">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="72f04-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="72f04-158">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="72f04-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="72f04-159">INVOER</span><span class="sxs-lookup"><span data-stu-id="72f04-159">INPUTS</span></span>

## <span data-ttu-id="72f04-160">UITVOER</span><span class="sxs-lookup"><span data-stu-id="72f04-160">OUTPUTS</span></span>

## <span data-ttu-id="72f04-161">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="72f04-161">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="72f04-162">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="72f04-162">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="72f04-163">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="72f04-163">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="72f04-164">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="72f04-164">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="72f04-165">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="72f04-165">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="72f04-166">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="72f04-166">RELATED LINKS</span></span>

[<span data-ttu-id="72f04-167">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="72f04-167">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="72f04-168">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="72f04-168">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="72f04-169">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="72f04-169">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="72f04-170">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="72f04-170">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
