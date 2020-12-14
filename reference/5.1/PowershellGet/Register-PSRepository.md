---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: 07f70f4fad6057ad689befaafd1d41f819a4538c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892760"
---
# <span data-ttu-id="e61ce-103">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="e61ce-103">Register-PSRepository</span></span>

## <span data-ttu-id="e61ce-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e61ce-104">SYNOPSIS</span></span>
<span data-ttu-id="e61ce-105">Registreert een Power shell-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e61ce-105">Registers a PowerShell repository.</span></span>

## <span data-ttu-id="e61ce-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e61ce-106">SYNTAX</span></span>

### <span data-ttu-id="e61ce-107">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="e61ce-107">NameParameterSet (Default)</span></span>

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### <span data-ttu-id="e61ce-108">PSGalleryParameterSet</span><span class="sxs-lookup"><span data-stu-id="e61ce-108">PSGalleryParameterSet</span></span>

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="e61ce-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e61ce-109">DESCRIPTION</span></span>

<span data-ttu-id="e61ce-110">De `Register-PSRepository` cmdlet registreert de standaard opslagplaats voor Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="e61ce-110">The `Register-PSRepository` cmdlet registers the default repository for PowerShell modules.</span></span> <span data-ttu-id="e61ce-111">Nadat een opslag plaats is geregistreerd, kunt u ernaar verwijzen vanuit `Find-Module` de `Install-Module` `Publish-Module` cmdlets, en.</span><span class="sxs-lookup"><span data-stu-id="e61ce-111">After a repository is registered, you can reference it from the `Find-Module`, `Install-Module`, and `Publish-Module` cmdlets.</span></span> <span data-ttu-id="e61ce-112">De geregistreerde opslag plaats wordt de standaard opslagplaats in `Find-Module` en `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="e61ce-112">The registered repository becomes the default repository in `Find-Module` and `Install-Module`.</span></span>

<span data-ttu-id="e61ce-113">Geregistreerde opslag plaatsen zijn gebruikersspecifieke.</span><span class="sxs-lookup"><span data-stu-id="e61ce-113">Registered repositories are user-specific.</span></span> <span data-ttu-id="e61ce-114">Ze worden niet geregistreerd in een context voor het hele systeem.</span><span class="sxs-lookup"><span data-stu-id="e61ce-114">They are not registered in a system-wide context.</span></span>

<span data-ttu-id="e61ce-115">Elke geregistreerde opslag plaats is gekoppeld aan een OneGet-pakket provider, die wordt opgegeven met de para meter **PackageManagementProvider** .</span><span class="sxs-lookup"><span data-stu-id="e61ce-115">Each registered repository is associated with a OneGet package provider, which is specified with the **PackageManagementProvider** parameter.</span></span> <span data-ttu-id="e61ce-116">Elke OneGet-provider is ontworpen om te communiceren met een specifiek type opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e61ce-116">Each OneGet provider is designed to interact with a specific type of repository.</span></span> <span data-ttu-id="e61ce-117">De NuGet-provider is bijvoorbeeld ontworpen om te communiceren met op NuGet gebaseerde opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="e61ce-117">For example, the NuGet provider is designed to interact with NuGet-based repositories.</span></span> <span data-ttu-id="e61ce-118">Als tijdens de registratie geen OneGet-provider is opgegeven, probeert PowerShellGet een OneGet-provider te vinden die de opgegeven bron locatie kan verwerken.</span><span class="sxs-lookup"><span data-stu-id="e61ce-118">If a OneGet provider is not specified during registration, PowerShellGet attempts to find a OneGet provider that can handle the specified source location.</span></span>

## <span data-ttu-id="e61ce-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e61ce-119">EXAMPLES</span></span>

### <span data-ttu-id="e61ce-120">Voor beeld 1: een opslag plaats registreren</span><span class="sxs-lookup"><span data-stu-id="e61ce-120">Example 1: Register a repository</span></span>

```powershell
$parameters = @{
  Name = "myNuGetSource"
  SourceLocation = "https://www.myget.org/F/powershellgetdemo/api/v2"
  PublishLocation = "https://www.myget.org/F/powershellgetdemo/api/v2/Packages"
  InstallationPolicy = 'Trusted'
}
Register-PSRepository @parameters
Get-PSRepository
```

```Output
Name                SourceLocation          OneGetProvider       InstallationPolicy
----                --------------          --------------       ------------------
PSGallery           http://go.micro...      NuGet                Untrusted
myNuGetSource       https://myget.c...      NuGet                Trusted
```

<span data-ttu-id="e61ce-121">De eerste opdracht wordt geregistreerd `https://www.myget.org/F/powershellgetdemo/` als een opslag plaats voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e61ce-121">The first command registers `https://www.myget.org/F/powershellgetdemo/` as a repository for the current user.</span></span> <span data-ttu-id="e61ce-122">Nadat myNuGetSource is geregistreerd, kunt u er expliciet naar verwijzen tijdens het zoeken, installeren en publiceren van modules.</span><span class="sxs-lookup"><span data-stu-id="e61ce-122">After myNuGetSource is registered, you can explicitly reference it when searching for, installing, and publishing modules.</span></span> <span data-ttu-id="e61ce-123">Omdat de para meter **PackageManagementProvider** niet is opgegeven, is de opslag plaats niet expliciet gekoppeld aan een OneGet-pakket provider, dus PowerShellGet polls beschik bare pakket providers en koppelt deze aan de NuGet-provider.</span><span class="sxs-lookup"><span data-stu-id="e61ce-123">Because the **PackageManagementProvider** parameter isn't specified, the repository is not explicitly associated with a OneGet package provider, so PowerShellGet polls available package providers and associates it with the NuGet provider.</span></span>

<span data-ttu-id="e61ce-124">Met de tweede opdracht worden de geregistreerde opslag plaatsen opgehaald en worden de resultaten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e61ce-124">The second command gets registered repositories and displays the results.</span></span>

## <span data-ttu-id="e61ce-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e61ce-125">PARAMETERS</span></span>

### <span data-ttu-id="e61ce-126">-Credential</span><span class="sxs-lookup"><span data-stu-id="e61ce-126">-Credential</span></span>

<span data-ttu-id="e61ce-127">Hiermee geeft u de referenties op van een account met rechten voor het registreren van een opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e61ce-127">Specifies credentials of an account that has rights to register a repository.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e61ce-128">-Default</span><span class="sxs-lookup"><span data-stu-id="e61ce-128">-Default</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PSGalleryParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e61ce-129">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="e61ce-129">-InstallationPolicy</span></span>

<span data-ttu-id="e61ce-130">Hiermee geeft u het installatie beleid op.</span><span class="sxs-lookup"><span data-stu-id="e61ce-130">Specifies the installation policy.</span></span> <span data-ttu-id="e61ce-131">Geldige waarden zijn: vertrouwd, niet vertrouwd.</span><span class="sxs-lookup"><span data-stu-id="e61ce-131">Valid values are: Trusted, UnTrusted.</span></span> <span data-ttu-id="e61ce-132">De standaard waarde is niet vertrouwd.</span><span class="sxs-lookup"><span data-stu-id="e61ce-132">The default value is UnTrusted.</span></span>

<span data-ttu-id="e61ce-133">Het installatie beleid van een opslag plaats specificeert Power shell-gedrag bij het installeren vanuit die opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e61ce-133">A repository's installation policy specifies PowerShell behavior when installing from that repository.</span></span> <span data-ttu-id="e61ce-134">Wanneer er modules worden geïnstalleerd vanuit een niet-vertrouwde opslag plaats, wordt de gebruiker gevraagd om bevestiging.</span><span class="sxs-lookup"><span data-stu-id="e61ce-134">When installing modules from an UnTrusted repository, the user is prompted for confirmation.</span></span>

<span data-ttu-id="e61ce-135">U kunt de **InstallationPolicy** instellen met de `Set-PSRepository` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e61ce-135">You can set the **InstallationPolicy** with the `Set-PSRepository` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Trusted, Untrusted

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e61ce-136">-Name</span><span class="sxs-lookup"><span data-stu-id="e61ce-136">-Name</span></span>

<span data-ttu-id="e61ce-137">Hiermee geeft u de naam op van de opslag plaats die u wilt registreren.</span><span class="sxs-lookup"><span data-stu-id="e61ce-137">Specifies the name of the repository to register.</span></span> <span data-ttu-id="e61ce-138">U kunt deze naam gebruiken om de opslag plaats in cmdlets zoals en te specificeren `Find-Module` `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="e61ce-138">You can use this name to specify the repository in cmdlets such as `Find-Module` and `Install-Module`.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e61ce-139">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="e61ce-139">-PackageManagementProvider</span></span>

<span data-ttu-id="e61ce-140">Hiermee geeft u een OneGet-pakket provider op.</span><span class="sxs-lookup"><span data-stu-id="e61ce-140">Specifies a OneGet package provider.</span></span> <span data-ttu-id="e61ce-141">Als u geen waarde opgeeft voor deze para meter, PowerShellGet polls beschik bare pakket providers en koppelt deze opslag plaats aan de eerste pakket provider waarmee wordt aangegeven dat de opslag plaats kan worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="e61ce-141">If you don't specify a value for this parameter, PowerShellGet polls available package providers and associates this repository with the first package provider that indicates it can handle the repository.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e61ce-142">-Proxy</span><span class="sxs-lookup"><span data-stu-id="e61ce-142">-Proxy</span></span>

<span data-ttu-id="e61ce-143">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="e61ce-143">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e61ce-144">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="e61ce-144">-ProxyCredential</span></span>

<span data-ttu-id="e61ce-145">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="e61ce-145">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="e61ce-146">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="e61ce-146">-PublishLocation</span></span>

<span data-ttu-id="e61ce-147">Hiermee wordt de URI van de publicatie locatie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e61ce-147">Specifies the URI of the publish location.</span></span> <span data-ttu-id="e61ce-148">Bijvoorbeeld: voor opslag plaatsen op basis van NuGet is de publicatie locatie vergelijkbaar met `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="e61ce-148">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e61ce-149">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="e61ce-149">-ScriptPublishLocation</span></span>

<span data-ttu-id="e61ce-150">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="e61ce-150">Specifies the script publish location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e61ce-151">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="e61ce-151">-ScriptSourceLocation</span></span>

<span data-ttu-id="e61ce-152">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="e61ce-152">Specifies the script source location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e61ce-153">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="e61ce-153">-SourceLocation</span></span>

<span data-ttu-id="e61ce-154">Hiermee geeft u de URI op voor het detecteren en installeren van modules uit deze opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e61ce-154">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="e61ce-155">Een URI kan een NuGet zijn (de meest voorkomende situatie), de HTTP-, HTTPS-, FTP-of file-locatie.</span><span class="sxs-lookup"><span data-stu-id="e61ce-155">A URI can be a NuGet server feed (most common situation), HTTP, HTTPS, FTP or file location.</span></span>

<span data-ttu-id="e61ce-156">Bijvoorbeeld: voor opslag plaatsen op basis van NuGet is de bron locatie vergelijkbaar met `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="e61ce-156">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e61ce-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e61ce-157">CommonParameters</span></span>

<span data-ttu-id="e61ce-158">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e61ce-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e61ce-159">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e61ce-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e61ce-160">INVOER</span><span class="sxs-lookup"><span data-stu-id="e61ce-160">INPUTS</span></span>

### <span data-ttu-id="e61ce-161">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="e61ce-161">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="e61ce-162">System. URI</span><span class="sxs-lookup"><span data-stu-id="e61ce-162">System.Uri</span></span>

## <span data-ttu-id="e61ce-163">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e61ce-163">OUTPUTS</span></span>

### <span data-ttu-id="e61ce-164">System. object</span><span class="sxs-lookup"><span data-stu-id="e61ce-164">System.Object</span></span>

## <span data-ttu-id="e61ce-165">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e61ce-165">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e61ce-166">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="e61ce-166">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="e61ce-167">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e61ce-167">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="e61ce-168">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="e61ce-168">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="e61ce-169">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e61ce-169">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="e61ce-170">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e61ce-170">RELATED LINKS</span></span>

[<span data-ttu-id="e61ce-171">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="e61ce-171">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="e61ce-172">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="e61ce-172">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="e61ce-173">Registratie ongedaan maken-PSRepository</span><span class="sxs-lookup"><span data-stu-id="e61ce-173">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
