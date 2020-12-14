---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: 2b23a121249c5cc9037e0440dfaed17a1a9f76e9
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891554"
---
# <span data-ttu-id="744be-103">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="744be-103">Set-PSRepository</span></span>

## <span data-ttu-id="744be-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="744be-104">SYNOPSIS</span></span>
<span data-ttu-id="744be-105">Hiermee stelt u waarden in voor een geregistreerde opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="744be-105">Sets values for a registered repository.</span></span>

## <span data-ttu-id="744be-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="744be-106">SYNTAX</span></span>

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## <span data-ttu-id="744be-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="744be-107">DESCRIPTION</span></span>

<span data-ttu-id="744be-108">De `Set-PSRepository` cmdlet stelt waarden in voor een geregistreerde module opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="744be-108">The `Set-PSRepository` cmdlet sets values for a registered module repository.</span></span> <span data-ttu-id="744be-109">De instellingen zijn permanent voor de huidige gebruiker en gelden voor alle versies van Power shell die voor die gebruiker zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="744be-109">The settings are persistent for the current user and apply to all versions of PowerShell installed for that user.</span></span>

## <span data-ttu-id="744be-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="744be-110">EXAMPLES</span></span>

### <span data-ttu-id="744be-111">Voor beeld 1: het installatie beleid voor een opslag plaats instellen</span><span class="sxs-lookup"><span data-stu-id="744be-111">Example 1: Set the installation policy for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

<span data-ttu-id="744be-112">Met deze opdracht wordt het installatie beleid voor de **myInternalSource** -opslag plaats ingesteld op **vertrouwd**, zodat u niet wordt gevraagd om de modules van die bron te installeren.</span><span class="sxs-lookup"><span data-stu-id="744be-112">This command sets the installation policy for the **myInternalSource** repository to **Trusted**, so that you are not prompted before installing modules from that source.</span></span>

### <span data-ttu-id="744be-113">Voor beeld 2: de bron-en publicatie locaties voor een opslag plaats instellen</span><span class="sxs-lookup"><span data-stu-id="744be-113">Example 2: Set the source and publish locations for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

<span data-ttu-id="744be-114">Met deze opdracht worden de bron locatie en publicatie locatie voor **myInternalSource** ingesteld op de opgegeven uri's.</span><span class="sxs-lookup"><span data-stu-id="744be-114">This command sets the source location and publish location for **myInternalSource** to the specified URIs.</span></span>

## <span data-ttu-id="744be-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="744be-115">PARAMETERS</span></span>

### <span data-ttu-id="744be-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="744be-116">-Credential</span></span>

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

### <span data-ttu-id="744be-117">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="744be-117">-InstallationPolicy</span></span>

<span data-ttu-id="744be-118">Hiermee geeft u het installatie beleid op.</span><span class="sxs-lookup"><span data-stu-id="744be-118">Specifies the installation policy.</span></span> <span data-ttu-id="744be-119">Geldige waarden zijn: **vertrouwd**, **niet vertrouwd**.</span><span class="sxs-lookup"><span data-stu-id="744be-119">Valid values are: **Trusted**, **Untrusted**.</span></span>

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

### <span data-ttu-id="744be-120">-Name</span><span class="sxs-lookup"><span data-stu-id="744be-120">-Name</span></span>

<span data-ttu-id="744be-121">Hiermee geeft u de naam van de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="744be-121">Specifies the name of the repository.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="744be-122">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="744be-122">-PackageManagementProvider</span></span>

<span data-ttu-id="744be-123">Hiermee geeft u de pakket beheer provider op.</span><span class="sxs-lookup"><span data-stu-id="744be-123">Specifies the package management provider.</span></span>

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

### <span data-ttu-id="744be-124">-Proxy</span><span class="sxs-lookup"><span data-stu-id="744be-124">-Proxy</span></span>

<span data-ttu-id="744be-125">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="744be-125">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="744be-126">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="744be-126">-ProxyCredential</span></span>

<span data-ttu-id="744be-127">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="744be-127">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="744be-128">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="744be-128">-PublishLocation</span></span>

<span data-ttu-id="744be-129">Hiermee wordt de URI van de publicatie locatie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="744be-129">Specifies the URI of the publish location.</span></span> <span data-ttu-id="744be-130">Bijvoorbeeld: voor opslag plaatsen op basis van NuGet is de publicatie locatie vergelijkbaar met `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="744be-130">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="744be-131">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="744be-131">-ScriptPublishLocation</span></span>

<span data-ttu-id="744be-132">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="744be-132">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="744be-133">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="744be-133">-ScriptSourceLocation</span></span>

<span data-ttu-id="744be-134">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="744be-134">Specifies the script source location.</span></span>

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

### <span data-ttu-id="744be-135">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="744be-135">-SourceLocation</span></span>

<span data-ttu-id="744be-136">Hiermee geeft u de URI op voor het detecteren en installeren van modules uit deze opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="744be-136">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="744be-137">Bijvoorbeeld: voor opslag plaatsen op basis van NuGet is de bron locatie vergelijkbaar met `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="744be-137">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="744be-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="744be-138">CommonParameters</span></span>

<span data-ttu-id="744be-139">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="744be-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="744be-140">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="744be-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="744be-141">INVOER</span><span class="sxs-lookup"><span data-stu-id="744be-141">INPUTS</span></span>

### <span data-ttu-id="744be-142">System. String</span><span class="sxs-lookup"><span data-stu-id="744be-142">System.String</span></span>

### <span data-ttu-id="744be-143">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="744be-143">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="744be-144">System. URI</span><span class="sxs-lookup"><span data-stu-id="744be-144">System.Uri</span></span>

## <span data-ttu-id="744be-145">UITVOER</span><span class="sxs-lookup"><span data-stu-id="744be-145">OUTPUTS</span></span>

### <span data-ttu-id="744be-146">System. object</span><span class="sxs-lookup"><span data-stu-id="744be-146">System.Object</span></span>

## <span data-ttu-id="744be-147">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="744be-147">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="744be-148">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="744be-148">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="744be-149">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="744be-149">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="744be-150">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="744be-150">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="744be-151">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="744be-151">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="744be-152">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="744be-152">RELATED LINKS</span></span>

[<span data-ttu-id="744be-153">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="744be-153">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="744be-154">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="744be-154">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="744be-155">Registratie ongedaan maken-PSRepository</span><span class="sxs-lookup"><span data-stu-id="744be-155">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
