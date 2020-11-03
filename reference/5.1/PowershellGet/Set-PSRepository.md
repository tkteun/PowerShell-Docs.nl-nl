---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: 0734bda0a3462e39f799570c853cffa3e267c5db
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250745"
---
# <span data-ttu-id="526e9-103">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="526e9-103">Set-PSRepository</span></span>

## <span data-ttu-id="526e9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="526e9-104">SYNOPSIS</span></span>
<span data-ttu-id="526e9-105">Hiermee stelt u waarden in voor een geregistreerde opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="526e9-105">Sets values for a registered repository.</span></span>

## <span data-ttu-id="526e9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="526e9-106">SYNTAX</span></span>

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## <span data-ttu-id="526e9-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="526e9-107">DESCRIPTION</span></span>

<span data-ttu-id="526e9-108">De `Set-PSRepository` cmdlet stelt waarden in voor een geregistreerde module opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="526e9-108">The `Set-PSRepository` cmdlet sets values for a registered module repository.</span></span> <span data-ttu-id="526e9-109">De instellingen zijn permanent voor de huidige gebruiker en gelden voor alle versies van Power shell die voor die gebruiker zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="526e9-109">The settings are persistent for the current user and apply to all versions of PowerShell installed for that user.</span></span>

## <span data-ttu-id="526e9-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="526e9-110">EXAMPLES</span></span>

### <span data-ttu-id="526e9-111">Voor beeld 1: het installatie beleid voor een opslag plaats instellen</span><span class="sxs-lookup"><span data-stu-id="526e9-111">Example 1: Set the installation policy for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

<span data-ttu-id="526e9-112">Met deze opdracht wordt het installatie beleid voor de **myInternalSource** -opslag plaats ingesteld op **vertrouwd** , zodat u niet wordt gevraagd om de modules van die bron te installeren.</span><span class="sxs-lookup"><span data-stu-id="526e9-112">This command sets the installation policy for the **myInternalSource** repository to **Trusted** , so that you are not prompted before installing modules from that source.</span></span>

### <span data-ttu-id="526e9-113">Voor beeld 2: de bron-en publicatie locaties voor een opslag plaats instellen</span><span class="sxs-lookup"><span data-stu-id="526e9-113">Example 2: Set the source and publish locations for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

<span data-ttu-id="526e9-114">Met deze opdracht worden de bron locatie en publicatie locatie voor **myInternalSource** ingesteld op de opgegeven uri's.</span><span class="sxs-lookup"><span data-stu-id="526e9-114">This command sets the source location and publish location for **myInternalSource** to the specified URIs.</span></span>

## <span data-ttu-id="526e9-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="526e9-115">PARAMETERS</span></span>

### <span data-ttu-id="526e9-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="526e9-116">-Credential</span></span>

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

### <span data-ttu-id="526e9-117">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="526e9-117">-InstallationPolicy</span></span>

<span data-ttu-id="526e9-118">Hiermee geeft u het installatie beleid op.</span><span class="sxs-lookup"><span data-stu-id="526e9-118">Specifies the installation policy.</span></span> <span data-ttu-id="526e9-119">Geldige waarden zijn: **vertrouwd** , **niet vertrouwd**.</span><span class="sxs-lookup"><span data-stu-id="526e9-119">Valid values are: **Trusted** , **Untrusted**.</span></span>

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

### <span data-ttu-id="526e9-120">-Name</span><span class="sxs-lookup"><span data-stu-id="526e9-120">-Name</span></span>

<span data-ttu-id="526e9-121">Hiermee geeft u de naam van de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="526e9-121">Specifies the name of the repository.</span></span>

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

### <span data-ttu-id="526e9-122">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="526e9-122">-PackageManagementProvider</span></span>

<span data-ttu-id="526e9-123">Hiermee geeft u de pakket beheer provider op.</span><span class="sxs-lookup"><span data-stu-id="526e9-123">Specifies the package management provider.</span></span>

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

### <span data-ttu-id="526e9-124">-Proxy</span><span class="sxs-lookup"><span data-stu-id="526e9-124">-Proxy</span></span>

<span data-ttu-id="526e9-125">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="526e9-125">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="526e9-126">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="526e9-126">-ProxyCredential</span></span>

<span data-ttu-id="526e9-127">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="526e9-127">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="526e9-128">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="526e9-128">-PublishLocation</span></span>

<span data-ttu-id="526e9-129">Hiermee wordt de URI van de publicatie locatie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="526e9-129">Specifies the URI of the publish location.</span></span> <span data-ttu-id="526e9-130">Bijvoorbeeld: voor opslag plaatsen op basis van NuGet is de publicatie locatie vergelijkbaar met `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="526e9-130">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="526e9-131">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="526e9-131">-ScriptPublishLocation</span></span>

<span data-ttu-id="526e9-132">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="526e9-132">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="526e9-133">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="526e9-133">-ScriptSourceLocation</span></span>

<span data-ttu-id="526e9-134">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="526e9-134">Specifies the script source location.</span></span>

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

### <span data-ttu-id="526e9-135">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="526e9-135">-SourceLocation</span></span>

<span data-ttu-id="526e9-136">Hiermee geeft u de URI op voor het detecteren en installeren van modules uit deze opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="526e9-136">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="526e9-137">Bijvoorbeeld: voor opslag plaatsen op basis van NuGet is de bron locatie vergelijkbaar met `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="526e9-137">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

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

### <span data-ttu-id="526e9-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="526e9-138">CommonParameters</span></span>

<span data-ttu-id="526e9-139">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="526e9-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="526e9-140">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="526e9-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="526e9-141">INVOER</span><span class="sxs-lookup"><span data-stu-id="526e9-141">INPUTS</span></span>

### <span data-ttu-id="526e9-142">System. String</span><span class="sxs-lookup"><span data-stu-id="526e9-142">System.String</span></span>

### <span data-ttu-id="526e9-143">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="526e9-143">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="526e9-144">System. URI</span><span class="sxs-lookup"><span data-stu-id="526e9-144">System.Uri</span></span>

## <span data-ttu-id="526e9-145">UITVOER</span><span class="sxs-lookup"><span data-stu-id="526e9-145">OUTPUTS</span></span>

### <span data-ttu-id="526e9-146">System. object</span><span class="sxs-lookup"><span data-stu-id="526e9-146">System.Object</span></span>

## <span data-ttu-id="526e9-147">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="526e9-147">NOTES</span></span>

## <span data-ttu-id="526e9-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="526e9-148">RELATED LINKS</span></span>

[<span data-ttu-id="526e9-149">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="526e9-149">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="526e9-150">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="526e9-150">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="526e9-151">Registratie ongedaan maken-PSRepository</span><span class="sxs-lookup"><span data-stu-id="526e9-151">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
