---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: be7ffa38a0409fa7ef0d01649b863a32732e34de
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249730"
---
# <span data-ttu-id="dc275-103">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="dc275-103">Register-PSRepository</span></span>

## <span data-ttu-id="dc275-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="dc275-104">SYNOPSIS</span></span>
<span data-ttu-id="dc275-105">Registreert een Power shell-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="dc275-105">Registers a PowerShell repository.</span></span>

## <span data-ttu-id="dc275-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="dc275-106">SYNTAX</span></span>

### <span data-ttu-id="dc275-107">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="dc275-107">NameParameterSet (Default)</span></span>

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### <span data-ttu-id="dc275-108">PSGalleryParameterSet</span><span class="sxs-lookup"><span data-stu-id="dc275-108">PSGalleryParameterSet</span></span>

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="dc275-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="dc275-109">DESCRIPTION</span></span>

<span data-ttu-id="dc275-110">De `Register-PSRepository` cmdlet registreert de standaard opslagplaats voor Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="dc275-110">The `Register-PSRepository` cmdlet registers the default repository for PowerShell modules.</span></span> <span data-ttu-id="dc275-111">Nadat een opslag plaats is geregistreerd, kunt u ernaar verwijzen vanuit `Find-Module` de `Install-Module` `Publish-Module` cmdlets, en.</span><span class="sxs-lookup"><span data-stu-id="dc275-111">After a repository is registered, you can reference it from the `Find-Module`, `Install-Module`, and `Publish-Module` cmdlets.</span></span> <span data-ttu-id="dc275-112">De geregistreerde opslag plaats wordt de standaard opslagplaats in `Find-Module` en `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="dc275-112">The registered repository becomes the default repository in `Find-Module` and `Install-Module`.</span></span>

<span data-ttu-id="dc275-113">Geregistreerde opslag plaatsen zijn gebruikersspecifieke.</span><span class="sxs-lookup"><span data-stu-id="dc275-113">Registered repositories are user-specific.</span></span> <span data-ttu-id="dc275-114">Ze worden niet geregistreerd in een context voor het hele systeem.</span><span class="sxs-lookup"><span data-stu-id="dc275-114">They are not registered in a system-wide context.</span></span>

<span data-ttu-id="dc275-115">Elke geregistreerde opslag plaats is gekoppeld aan een OneGet-pakket provider, die wordt opgegeven met de para meter **PackageManagementProvider** .</span><span class="sxs-lookup"><span data-stu-id="dc275-115">Each registered repository is associated with a OneGet package provider, which is specified with the **PackageManagementProvider** parameter.</span></span> <span data-ttu-id="dc275-116">Elke OneGet-provider is ontworpen om te communiceren met een specifiek type opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="dc275-116">Each OneGet provider is designed to interact with a specific type of repository.</span></span> <span data-ttu-id="dc275-117">De NuGet-provider is bijvoorbeeld ontworpen om te communiceren met op NuGet gebaseerde opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="dc275-117">For example, the NuGet provider is designed to interact with NuGet-based repositories.</span></span> <span data-ttu-id="dc275-118">Als tijdens de registratie geen OneGet-provider is opgegeven, probeert PowerShellGet een OneGet-provider te vinden die de opgegeven bron locatie kan verwerken.</span><span class="sxs-lookup"><span data-stu-id="dc275-118">If a OneGet provider is not specified during registration, PowerShellGet attempts to find a OneGet provider that can handle the specified source location.</span></span>

## <span data-ttu-id="dc275-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="dc275-119">EXAMPLES</span></span>

### <span data-ttu-id="dc275-120">Voor beeld 1: een opslag plaats registreren</span><span class="sxs-lookup"><span data-stu-id="dc275-120">Example 1: Register a repository</span></span>

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

<span data-ttu-id="dc275-121">De eerste opdracht wordt geregistreerd `https://www.myget.org/F/powershellgetdemo/` als een opslag plaats voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="dc275-121">The first command registers `https://www.myget.org/F/powershellgetdemo/` as a repository for the current user.</span></span> <span data-ttu-id="dc275-122">Nadat myNuGetSource is geregistreerd, kunt u er expliciet naar verwijzen tijdens het zoeken, installeren en publiceren van modules.</span><span class="sxs-lookup"><span data-stu-id="dc275-122">After myNuGetSource is registered, you can explicitly reference it when searching for, installing, and publishing modules.</span></span> <span data-ttu-id="dc275-123">Omdat de para meter **PackageManagementProvider** niet is opgegeven, is de opslag plaats niet expliciet gekoppeld aan een OneGet-pakket provider, dus PowerShellGet polls beschik bare pakket providers en koppelt deze aan de NuGet-provider.</span><span class="sxs-lookup"><span data-stu-id="dc275-123">Because the **PackageManagementProvider** parameter isn't specified, the repository is not explicitly associated with a OneGet package provider, so PowerShellGet polls available package providers and associates it with the NuGet provider.</span></span>

<span data-ttu-id="dc275-124">Met de tweede opdracht worden de geregistreerde opslag plaatsen opgehaald en worden de resultaten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="dc275-124">The second command gets registered repositories and displays the results.</span></span>

## <span data-ttu-id="dc275-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dc275-125">PARAMETERS</span></span>

### <span data-ttu-id="dc275-126">-Credential</span><span class="sxs-lookup"><span data-stu-id="dc275-126">-Credential</span></span>

<span data-ttu-id="dc275-127">Hiermee geeft u de referenties op van een account met rechten voor het registreren van een opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="dc275-127">Specifies credentials of an account that has rights to register a repository.</span></span>

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

### <span data-ttu-id="dc275-128">-Default</span><span class="sxs-lookup"><span data-stu-id="dc275-128">-Default</span></span>

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

### <span data-ttu-id="dc275-129">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="dc275-129">-InstallationPolicy</span></span>

<span data-ttu-id="dc275-130">Hiermee geeft u het installatie beleid op.</span><span class="sxs-lookup"><span data-stu-id="dc275-130">Specifies the installation policy.</span></span> <span data-ttu-id="dc275-131">Geldige waarden zijn: vertrouwd, niet vertrouwd.</span><span class="sxs-lookup"><span data-stu-id="dc275-131">Valid values are: Trusted, UnTrusted.</span></span> <span data-ttu-id="dc275-132">De standaard waarde is niet vertrouwd.</span><span class="sxs-lookup"><span data-stu-id="dc275-132">The default value is UnTrusted.</span></span>

<span data-ttu-id="dc275-133">Het installatie beleid van een opslag plaats specificeert Power shell-gedrag bij het installeren vanuit die opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="dc275-133">A repository's installation policy specifies PowerShell behavior when installing from that repository.</span></span> <span data-ttu-id="dc275-134">Wanneer er modules worden geïnstalleerd vanuit een niet-vertrouwde opslag plaats, wordt de gebruiker gevraagd om bevestiging.</span><span class="sxs-lookup"><span data-stu-id="dc275-134">When installing modules from an UnTrusted repository, the user is prompted for confirmation.</span></span>

<span data-ttu-id="dc275-135">U kunt de **InstallationPolicy** instellen met de `Set-PSRepository` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dc275-135">You can set the **InstallationPolicy** with the `Set-PSRepository` cmdlet.</span></span>

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

### <span data-ttu-id="dc275-136">-Name</span><span class="sxs-lookup"><span data-stu-id="dc275-136">-Name</span></span>

<span data-ttu-id="dc275-137">Hiermee geeft u de naam op van de opslag plaats die u wilt registreren.</span><span class="sxs-lookup"><span data-stu-id="dc275-137">Specifies the name of the repository to register.</span></span> <span data-ttu-id="dc275-138">U kunt deze naam gebruiken om de opslag plaats in cmdlets zoals en te specificeren `Find-Module` `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="dc275-138">You can use this name to specify the repository in cmdlets such as `Find-Module` and `Install-Module`.</span></span>

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

### <span data-ttu-id="dc275-139">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="dc275-139">-PackageManagementProvider</span></span>

<span data-ttu-id="dc275-140">Hiermee geeft u een OneGet-pakket provider op.</span><span class="sxs-lookup"><span data-stu-id="dc275-140">Specifies a OneGet package provider.</span></span> <span data-ttu-id="dc275-141">Als u geen waarde opgeeft voor deze para meter, PowerShellGet polls beschik bare pakket providers en koppelt deze opslag plaats aan de eerste pakket provider waarmee wordt aangegeven dat de opslag plaats kan worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="dc275-141">If you don't specify a value for this parameter, PowerShellGet polls available package providers and associates this repository with the first package provider that indicates it can handle the repository.</span></span>

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

### <span data-ttu-id="dc275-142">-Proxy</span><span class="sxs-lookup"><span data-stu-id="dc275-142">-Proxy</span></span>

<span data-ttu-id="dc275-143">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="dc275-143">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="dc275-144">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="dc275-144">-ProxyCredential</span></span>

<span data-ttu-id="dc275-145">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="dc275-145">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="dc275-146">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="dc275-146">-PublishLocation</span></span>

<span data-ttu-id="dc275-147">Hiermee wordt de URI van de publicatie locatie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="dc275-147">Specifies the URI of the publish location.</span></span> <span data-ttu-id="dc275-148">Bijvoorbeeld: voor opslag plaatsen op basis van NuGet is de publicatie locatie vergelijkbaar met `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="dc275-148">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="dc275-149">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="dc275-149">-ScriptPublishLocation</span></span>

<span data-ttu-id="dc275-150">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="dc275-150">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="dc275-151">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="dc275-151">-ScriptSourceLocation</span></span>

<span data-ttu-id="dc275-152">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="dc275-152">Specifies the script source location.</span></span>

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

### <span data-ttu-id="dc275-153">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="dc275-153">-SourceLocation</span></span>

<span data-ttu-id="dc275-154">Hiermee geeft u de URI op voor het detecteren en installeren van modules uit deze opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="dc275-154">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="dc275-155">Een URI kan een NuGet zijn (de meest voorkomende situatie), de HTTP-, HTTPS-, FTP-of file-locatie.</span><span class="sxs-lookup"><span data-stu-id="dc275-155">A URI can be a NuGet server feed (most common situation), HTTP, HTTPS, FTP or file location.</span></span>

<span data-ttu-id="dc275-156">Bijvoorbeeld: voor opslag plaatsen op basis van NuGet is de bron locatie vergelijkbaar met `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="dc275-156">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

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

### <span data-ttu-id="dc275-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dc275-157">CommonParameters</span></span>

<span data-ttu-id="dc275-158">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dc275-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dc275-159">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc275-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dc275-160">INVOER</span><span class="sxs-lookup"><span data-stu-id="dc275-160">INPUTS</span></span>

### <span data-ttu-id="dc275-161">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="dc275-161">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="dc275-162">System. URI</span><span class="sxs-lookup"><span data-stu-id="dc275-162">System.Uri</span></span>

## <span data-ttu-id="dc275-163">UITVOER</span><span class="sxs-lookup"><span data-stu-id="dc275-163">OUTPUTS</span></span>

### <span data-ttu-id="dc275-164">System. object</span><span class="sxs-lookup"><span data-stu-id="dc275-164">System.Object</span></span>

## <span data-ttu-id="dc275-165">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="dc275-165">NOTES</span></span>

## <span data-ttu-id="dc275-166">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="dc275-166">RELATED LINKS</span></span>

[<span data-ttu-id="dc275-167">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="dc275-167">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="dc275-168">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="dc275-168">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="dc275-169">Registratie ongedaan maken-PSRepository</span><span class="sxs-lookup"><span data-stu-id="dc275-169">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
